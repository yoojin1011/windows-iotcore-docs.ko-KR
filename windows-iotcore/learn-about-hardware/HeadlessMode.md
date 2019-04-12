---
title: 헤드 및 헤드리스 장치
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Windows IoT Core 장치에 대 한 헤드 또는 헤드리스 모드로 구성 하는 방법에 알아봅니다.
keywords: windows iot, 화면, 양방향, 헤드리스 시스템인 UI
ms.openlocfilehash: 8ac0d7e06477836aa080af1b7556b054957d0cac
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513301"
---
# <a name="headed-and-headless-devices"></a><span data-ttu-id="c1689-104">헤드 및 헤드리스 장치</span><span class="sxs-lookup"><span data-stu-id="c1689-104">Headed and Headless devices</span></span>

<span data-ttu-id="c1689-105">Windows 10 IoT Core 대해 구성할 수 있습니다 *양방향* 하거나 *헤드리스* 모드입니다.</span><span class="sxs-lookup"><span data-stu-id="c1689-105">Windows 10 IoT Core can be configured for either *headed* or *headless* mode.</span></span> 

## <a name="headed-mode"></a><span data-ttu-id="c1689-106">헤드 모드만</span><span class="sxs-lookup"><span data-stu-id="c1689-106">Headed mode</span></span>
<span data-ttu-id="c1689-107">헤드 모드만 UI의 존재로 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1689-107">Headed mode is defined by the presence of UI.</span></span> <span data-ttu-id="c1689-108">*양방향* 모드는 단일 UI 앱 시스템 부팅 시 시작 됩니다 및 또한 수 있는 0 개 이상 "백그라운드 앱 일" (StartupTasks).</span><span class="sxs-lookup"><span data-stu-id="c1689-108">In *headed* mode a single UI app will be launched at system boot and there can additionally be 0 or more "Background Apps" (StartupTasks).</span></span> 

## <a name="headless-mode"></a><span data-ttu-id="c1689-109">헤드리스 모드</span><span class="sxs-lookup"><span data-stu-id="c1689-109">Headless mode</span></span>
<span data-ttu-id="c1689-110">헤드리스 모드로 UI에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1689-110">Headless mode has no UI.</span></span>  <span data-ttu-id="c1689-111">UI 기능을 사용 하지 않는 장치 설정할 수 있습니다 *헤드리스* 모드입니다.</span><span class="sxs-lookup"><span data-stu-id="c1689-111">Devices that don't need UI functionality can be set to *headless* mode.</span></span> <span data-ttu-id="c1689-112">UI 스택을 사용 하지 않도록 설정 하 고 UI 앱이 시작 되지.</span><span class="sxs-lookup"><span data-stu-id="c1689-112">The UI stack is disabled and UI apps will not launch.</span></span> <span data-ttu-id="c1689-113">이 사용 된 시스템 리소스의 양을 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="c1689-113">This reduces the amount of system resources used.</span></span> <span data-ttu-id="c1689-114">모니터 장치에 연결 하는 경우에 화면 black 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1689-114">If you attach a monitor to your device, the screen will be black.</span></span>

> [!NOTE]
> <span data-ttu-id="c1689-115">헤드리스 모드로 장치를 배치 하면 해당 IP 주소를 찾으려면 아래에 설명 된 Windows 10 IoT Core 대시보드 응용 프로그램을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1689-115">If you put your device into headless mode, then you can use the Windows 10 IoT Core Dashboard application, described below, to find its IP address.</span></span>

## <a name="changing-the-mode"></a><span data-ttu-id="c1689-116">모드 변경</span><span class="sxs-lookup"><span data-stu-id="c1689-116">Changing the mode</span></span>
<span data-ttu-id="c1689-117">Windows PowerShell 세션 또는 SSH 세션에서 장치의 지 향하는 방향/헤드리스 상태를 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1689-117">You can modify the headed/headless state of your device from a Windows PowerShell session or an SSH session.</span></span> <span data-ttu-id="c1689-118">PowerShell에 대 한 자세한 내용은 참조는 [IoT Core에 대 한 PowerShell](../connect-your-device/PowerShell.md) 페이지입니다.</span><span class="sxs-lookup"><span data-stu-id="c1689-118">To learn more about PowerShell, see the [PowerShell for IoT Core](../connect-your-device/PowerShell.md) page.</span></span> <span data-ttu-id="c1689-119">SSH에 대 한 자세한 내용은 참조는 [IoT Core에 대 한 SSH](../connect-your-device/SSH.md) 페이지입니다.</span><span class="sxs-lookup"><span data-stu-id="c1689-119">To learn more about SSH, see the [SSH for IoT Core](../connect-your-device/SSH.md) page.</span></span>

* <span data-ttu-id="c1689-120">장치의 현재 상태를 표시 하려면 사용 된 `setbootoption` 유틸리티.</span><span class="sxs-lookup"><span data-stu-id="c1689-120">To display the current state of your device, use the `setbootoption` utility:</span></span>

~~~
    [192.168.0.243]: PS C:\> setbootoption.exe
~~~

* <span data-ttu-id="c1689-121">헤드리스 모드를 사용 하도록 설정 하는 장치의 상태를 수정 하려면 사용 합니다 `setbootoption` 유틸리티를 `headless` arg:</span><span class="sxs-lookup"><span data-stu-id="c1689-121">To modify the state of your device to enable headless mode, use the `setbootoption` utility with the `headless` arg:</span></span>

~~~
    [192.168.0.243]: PS C:\> setbootoption.exe headless
    [192.168.0.243]: PS C:\> shutdown /r /t 0
~~~

* <span data-ttu-id="c1689-122">모드도 사용 하는 장치의 상태를 수정 하려면 사용 합니다 `setbootoption` 유틸리티를 `headed` arg:</span><span class="sxs-lookup"><span data-stu-id="c1689-122">To modify the state of your device to enable headed mode, use the `setbootoption` utility with the `headed` arg:</span></span>

~~~
    [192.168.0.243]: PS C:\> setbootoption.exe headed
    [192.168.0.243]: PS C:\> shutdown /r /t 0
~~~

## <a name="finding-your-headless-device"></a><span data-ttu-id="c1689-123">헤드리스 장치 찾기</span><span class="sxs-lookup"><span data-stu-id="c1689-123">Finding your headless device</span></span>

<span data-ttu-id="c1689-124">헤드리스 모드에 있는 IoT Core 장치를 사용 하 여 검색할 수는 **Windows 10 IoT Core 대시보드** 응용 프로그램입니다.</span><span class="sxs-lookup"><span data-stu-id="c1689-124">An IoT Core device that is in headless mode can be discovered using the **Windows 10 IoT Core Dashboard** application.</span></span>  <span data-ttu-id="c1689-125">IoT 대시보드를 다운로드 하려면 참조는 [다운로드](http://go.microsoft.com/fwlink/?LinkID=708576) 페이지입니다.</span><span class="sxs-lookup"><span data-stu-id="c1689-125">To download the IoT Dashboard, see the [Downloads](http://go.microsoft.com/fwlink/?LinkID=708576) page.</span></span>
<span data-ttu-id="c1689-126">를 실행 하는 경우 응용 프로그램에서 로컬 네트워크에 있는 모든 IoT Core 장치 ping에 대 한 수신 대기 하 고 이름, IP 주소 등과 같은 장치 정보를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1689-126">When running, the application listens for pings from any IoT Core devices on the local network and displays device information such as the name, IP address, and more.</span></span>

![Windows 10 IoT Core 대시보드](../media/HeadlessMode/selectDevice.png)
