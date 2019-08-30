---
title: Wake on Touch
author: jordanrh1
ms.author: jordanrh
ms.date: 09/17/2018
ms.topic: article
description: 장치를 켜 켜 켜 지도록 구성
keywords: windows iot, 화면, 절전 모드, 절전 모드 해제, 터치, 대기, 전원
ms.custom: RS5
ms.openlocfilehash: 7c0fc9613f1b1ed45fb8d69a18d82b034eb366fb
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "60167641"
---
# <a name="configure-your-device-to-wake-on-touch"></a><span data-ttu-id="712fd-104">장치를 켜 켜 켜 지도록 구성</span><span class="sxs-lookup"><span data-stu-id="712fd-104">Configure your device to wake on touch</span></span>

<span data-ttu-id="712fd-105">일부 시나리오에서는 사용자가 터치 스크린을 터치 하는 동안 사용 하지 않는 동안 장치의 화면을 끄고 신속 하 게 설정 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="712fd-105">In some scenarios, you want your device's screen to turn off while not in use and to turn on quickly when a user touches the touchscreen.</span></span> <span data-ttu-id="712fd-106">이 문서에서는이 시나리오를 달성할 수 있도록 장치를 구성 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="712fd-106">This document describes how to configure your device to achieve this scenario.</span></span>

## <a name="setting-a-video-idle-timeout"></a><span data-ttu-id="712fd-107">비디오 유휴 시간 제한 설정</span><span class="sxs-lookup"><span data-stu-id="712fd-107">Setting a video idle timeout</span></span>

<span data-ttu-id="712fd-108">비디오 유휴 시간 제한을 설정 하 여 비활성 기간 후에 화면을 해제 하도록 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="712fd-108">You can configure the screen to turn off after a period of inactivity by setting a video idle timeout.</span></span> <span data-ttu-id="712fd-109">사용자가 지정 된 시간 동안 장치와 상호 작용 하지 않으면 화면이 꺼집니다.</span><span class="sxs-lookup"><span data-stu-id="712fd-109">When the user has not interacted with the device for a specified length of time, the screen will turn off.</span></span> <span data-ttu-id="712fd-110">이렇게 하면 디스플레이와 관련 된 구성 요소의 전원을 켜는 방식으로 장치에서 절전 모드로 전환 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="712fd-110">This will enable the device to enter a low power state by powering down components related to the display.</span></span>

```
    powercfg.exe /setacvalueindex SCHEME_CURRENT SUB_VIDEO VIDEOIDLE 10
    powercfg.exe /setdcvalueindex SCHEME_CURRENT SUB_VIDEO VIDEOIDLE 10
    powercfg.exe /setactive SCHEME_CURRENT
```

<span data-ttu-id="712fd-111">자세한 내용은 [유휴 시간 제한](/windows-hardware/customize/power-settings/display-settings-display-idle-timeout) 및 [디스플레이, 절전 모드 및 최대 절전 모드 타이머](/windows-hardware/design/device-experiences/display--sleep--and-hibernate-idle-timers)표시를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="712fd-111">For more information, see [Display Idle Timeout](/windows-hardware/customize/power-settings/display-settings-display-idle-timeout) and [Display, sleep, and hibernate idle timers](/windows-hardware/design/device-experiences/display--sleep--and-hibernate-idle-timers).</span></span>

## <a name="disabling-modern-standby"></a><span data-ttu-id="712fd-112">최신 대기를 사용 하지 않도록 설정</span><span class="sxs-lookup"><span data-stu-id="712fd-112">Disabling modern standby</span></span>

<span data-ttu-id="712fd-113">AoAC 시스템 (모든 ARM 시스템 포함)에서는 디스플레이가 꺼진 경우 시스템이 자동으로 [최신 대기 모드로](/windows-hardware/design/device-experiences/modern-standby) 전환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="712fd-113">On AoAC systems (which includes all ARM systems), the system will automatically enter [modern standby](/windows-hardware/design/device-experiences/modern-standby) when the display goes off.</span></span> <span data-ttu-id="712fd-114">시스템이 최신 대기 상태 이면 특정 입력에 의해서만 해제 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="712fd-114">When a system is in modern standby, it can only be woken by certain inputs.</span></span> <span data-ttu-id="712fd-115">이 목록은 완전 한 목록이 아니지만 이러한 입력에는 전원 단추를 누르거나 랩톱에서 덮개를 열거나 마우스를 클릭 하는 작업이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="712fd-115">This is not an exhaustive list, but these inputs include pressing the power button, opening the lid on a laptop, or clicking the mouse.</span></span> <span data-ttu-id="712fd-116">화면 터치는 최신 대기에서 장치를 절전 모드에서 해제 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="712fd-116">Touching the screen will not wake up the device from modern standby.</span></span> <span data-ttu-id="712fd-117">장치를 터치 하 여 절전 모드를 해제 하려면 최신 대기 모드로 들어가지 않도록 장치를 구성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="712fd-117">If you want your device to wake up by touch, you have to configure the device not to enter modern standby.</span></span> <span data-ttu-id="712fd-118">최신 대기를 사용 하지 않도록 설정 하려면 다음 레지스트리 키를 설정 하 고 다시 부팅 합니다.</span><span class="sxs-lookup"><span data-stu-id="712fd-118">To disable modern standby, set the following registry key and reboot.</span></span>

```
    reg add HKLM\System\CurrentControlSet\Control\Power /v PlatformAoAcOverride /t REG_DWORD /d 0
```
    
<span data-ttu-id="712fd-119">최신 대기를 사용 하지 않도록 설정 하면 시스템이 유휴 상태일 때 전력 소비에 영향을 줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="712fd-119">Disabling modern standby can impact power consumption when the system is idle.</span></span> <span data-ttu-id="712fd-120">최신 대기를 사용 하지 않도록 설정 하기 전에 최신 대기를 사용 하도록 설정 하 고 사용 하지 않도록 설정 하 여 시스템의 전력 소비량을 측정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="712fd-120">You should measure your system's power consumption with modern standby enabled and disabled before making the decision to disable modern standby.</span></span>

<span data-ttu-id="712fd-121">최신 대기는 가능한 한 시스템 작업을 자동으로 시도 하 여 하드웨어를 저전력 상태로 전환할 수 있도록 하는 소프트웨어 메커니즘입니다.</span><span class="sxs-lookup"><span data-stu-id="712fd-121">Modern standby is a software mechanism that attempts to quiet system activity as much as possible, thereby allowing hardware to enter a low power state.</span></span> <span data-ttu-id="712fd-122">이론적으로 최신 대기를 사용 하지 않도록 설정 된 충분 한 자동 장치는 최신 대기 상태의 장치와 동일한 저전력 소비를 달성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="712fd-122">In theory, a sufficiently quiet device with modern standby disabled can achieve the same low power consumption as a device in modern standby.</span></span> <span data-ttu-id="712fd-123">최신 대기를 사용 하지 않는 경우 소프트웨어 타이머 및 정기 작업을 포함 하 여 백그라운드 작업을 최소화 하는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="712fd-123">It is important to minimize background activity including software timers and periodic tasks if modern standby is disabled.</span></span>
