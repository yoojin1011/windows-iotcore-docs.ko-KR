---
title: 터치에서 절전 모드 해제
author: jordanrh1
ms.author: jordanrh
ms.date: 09/17/2018
ms.topic: article
description: 터치에서 절전 모드를 해제 하기 위해 장치를 구성 합니다.
keywords: windows iot, 화면, 절전 모드, 절전 모드 해제, 터치, 대기, 전원
ms.custom: RS5
ms.openlocfilehash: 7c0fc9613f1b1ed45fb8d69a18d82b034eb366fb
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513022"
---
# <a name="configure-your-device-to-wake-on-touch"></a><span data-ttu-id="c57c8-104">터치에서 절전 모드를 해제 하기 위해 장치를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="c57c8-104">Configure your device to wake on touch</span></span>

<span data-ttu-id="c57c8-105">일부 시나리오에서는 장치의 화면을 사용 하는 동안 사용 중이 아님 해제 하려면 사용자는 터치 스크린에 닿을 때 신속 하 게 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c57c8-105">In some scenarios, you want your device's screen to turn off while not in use and to turn on quickly when a user touches the touchscreen.</span></span> <span data-ttu-id="c57c8-106">이 문서에서는이 시나리오를 달성 하기 위해 장치를 구성 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="c57c8-106">This document describes how to configure your device to achieve this scenario.</span></span>

## <a name="setting-a-video-idle-timeout"></a><span data-ttu-id="c57c8-107">비디오 유휴 시간 제한 설정</span><span class="sxs-lookup"><span data-stu-id="c57c8-107">Setting a video idle timeout</span></span>

<span data-ttu-id="c57c8-108">비디오 유휴 시간 제한을 설정 하 여 일정 한 비활성 기간 후 해제 하는 화면을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c57c8-108">You can configure the screen to turn off after a period of inactivity by setting a video idle timeout.</span></span> <span data-ttu-id="c57c8-109">사용자가 지정 된 기간 동안 장치가 상호 작용 하지, 화면 기능을 해제 합니다.</span><span class="sxs-lookup"><span data-stu-id="c57c8-109">When the user has not interacted with the device for a specified length of time, the screen will turn off.</span></span> <span data-ttu-id="c57c8-110">장치 디스플레이에 관련 된 구성 요소를 끄는 여 절전 모드를 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c57c8-110">This will enable the device to enter a low power state by powering down components related to the display.</span></span>

```
    powercfg.exe /setacvalueindex SCHEME_CURRENT SUB_VIDEO VIDEOIDLE 10
    powercfg.exe /setdcvalueindex SCHEME_CURRENT SUB_VIDEO VIDEOIDLE 10
    powercfg.exe /setactive SCHEME_CURRENT
```

<span data-ttu-id="c57c8-111">자세한 내용은 [표시 유휴 시간 제한](/windows-hardware/customize/power-settings/display-settings-display-idle-timeout) 하 고 [표시 되는 절전 유휴 타이머를 최대 절전 모드 및](/windows-hardware/design/device-experiences/display--sleep--and-hibernate-idle-timers).</span><span class="sxs-lookup"><span data-stu-id="c57c8-111">For more information, see [Display Idle Timeout](/windows-hardware/customize/power-settings/display-settings-display-idle-timeout) and [Display, sleep, and hibernate idle timers](/windows-hardware/design/device-experiences/display--sleep--and-hibernate-idle-timers).</span></span>

## <a name="disabling-modern-standby"></a><span data-ttu-id="c57c8-112">현대 대기 모드를 사용 하지 않도록 설정</span><span class="sxs-lookup"><span data-stu-id="c57c8-112">Disabling modern standby</span></span>

<span data-ttu-id="c57c8-113">를 포함 하는 모든 ARM 시스템 AoAC 시스템에서는 시스템에서 자동으로 입력 됩니다 [현대 대기](/windows-hardware/design/device-experiences/modern-standby) 표시 되는 경우.</span><span class="sxs-lookup"><span data-stu-id="c57c8-113">On AoAC systems (which includes all ARM systems), the system will automatically enter [modern standby](/windows-hardware/design/device-experiences/modern-standby) when the display goes off.</span></span> <span data-ttu-id="c57c8-114">시스템을 최신 대기에서 경우 특정 입력으로 절전만 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c57c8-114">When a system is in modern standby, it can only be woken by certain inputs.</span></span> <span data-ttu-id="c57c8-115">목록은 아닙니다. 하지만 이러한 입력에서 전원 단추를 랩톱에서 커버를 열거나 마우스 클릭을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="c57c8-115">This is not an exhaustive list, but these inputs include pressing the power button, opening the lid on a laptop, or clicking the mouse.</span></span> <span data-ttu-id="c57c8-116">현대 대기 모드에서 장치 등록 화면을 터치를 작동할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c57c8-116">Touching the screen will not wake up the device from modern standby.</span></span> <span data-ttu-id="c57c8-117">장치를 터치 하 여 절전 모드를 사용 하도록 하려는 경우 최신 대기 상태가 필요가 장치를 구성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c57c8-117">If you want your device to wake up by touch, you have to configure the device not to enter modern standby.</span></span> <span data-ttu-id="c57c8-118">현대 대기 모드를 해제 하려면 다음 레지스트리 키 및 다시 부팅을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c57c8-118">To disable modern standby, set the following registry key and reboot.</span></span>

```
    reg add HKLM\System\CurrentControlSet\Control\Power /v PlatformAoAcOverride /t REG_DWORD /d 0
```
    
<span data-ttu-id="c57c8-119">시스템이 유휴 상태일 때 최신 대기 모드 해제가 전력 소비 하는 영향을 줄 수입니다.</span><span class="sxs-lookup"><span data-stu-id="c57c8-119">Disabling modern standby can impact power consumption when the system is idle.</span></span> <span data-ttu-id="c57c8-120">사용 하도록 설정 하 고 최신 대기 모드를 사용 하지 않도록 설정 하도록 결정 하기 전에 사용 하지 않도록 설정 하는 최신 standby를 사용 하 여 시스템의 전력 소비를 측정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c57c8-120">You should measure your system's power consumption with modern standby enabled and disabled before making the decision to disable modern standby.</span></span>

<span data-ttu-id="c57c8-121">현대 대기에 최대한 많이, 절전 상태로 전환 되려고 할 하드웨어 있기 때문에 자동 시스템 작업 하려고 하는 소프트웨어 메커니즘입니다.</span><span class="sxs-lookup"><span data-stu-id="c57c8-121">Modern standby is a software mechanism that attempts to quiet system activity as much as possible, thereby allowing hardware to enter a low power state.</span></span> <span data-ttu-id="c57c8-122">이론적으로 현대 대기 비활성화를 사용 하 여 충분히 자동 장치 최신 대기에서 장치로 같은 낮은 전력 소비량을 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c57c8-122">In theory, a sufficiently quiet device with modern standby disabled can achieve the same low power consumption as a device in modern standby.</span></span> <span data-ttu-id="c57c8-123">현대 대기 하지 않으면 소프트웨어 타이머 및 정기 작업을 포함 하 여 백그라운드 작업을 최소화 하는 것이 반드시 합니다.</span><span class="sxs-lookup"><span data-stu-id="c57c8-123">It is important to minimize background activity including software timers and periodic tasks if modern standby is disabled.</span></span>
