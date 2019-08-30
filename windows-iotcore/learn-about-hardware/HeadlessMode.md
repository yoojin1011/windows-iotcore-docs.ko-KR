---
title: headed 및 headless 디바이스
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 장치에 대해 Windows IoT Core를 구성 하는 방법에 대해 알아봅니다.
keywords: windows iot, 화면, 양방향, 헤드리스, UI
ms.openlocfilehash: 8ac0d7e06477836aa080af1b7556b054957d0cac
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "60169443"
---
# <a name="headed-and-headless-devices"></a><span data-ttu-id="72182-104">양방향 및 헤드리스 장치</span><span class="sxs-lookup"><span data-stu-id="72182-104">Headed and Headless devices</span></span>

<span data-ttu-id="72182-105">Windows 10 IoT Core는 *양방향* 또는 *헤드리스* 모드로 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72182-105">Windows 10 IoT Core can be configured for either *headed* or *headless* mode.</span></span> 

## <a name="headed-mode"></a><span data-ttu-id="72182-106">양방향 모드</span><span class="sxs-lookup"><span data-stu-id="72182-106">Headed mode</span></span>
<span data-ttu-id="72182-107">화살표는 UI가 있는지 여부에 따라 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="72182-107">Headed mode is defined by the presence of UI.</span></span> <span data-ttu-id="72182-108">또한 시스템 부팅 시 단일 UI 앱이 시작 되 고 0 개 이상의 "백그라운드 앱" (startuptasks)이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72182-108">In *headed* mode a single UI app will be launched at system boot and there can additionally be 0 or more "Background Apps" (StartupTasks).</span></span> 

## <a name="headless-mode"></a><span data-ttu-id="72182-109">헤드리스 모드</span><span class="sxs-lookup"><span data-stu-id="72182-109">Headless mode</span></span>
<span data-ttu-id="72182-110">헤드리스 모드에는 UI가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="72182-110">Headless mode has no UI.</span></span>  <span data-ttu-id="72182-111">UI 기능이 필요 하지 않은 장치는 *헤드리스* 모드로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72182-111">Devices that don't need UI functionality can be set to *headless* mode.</span></span> <span data-ttu-id="72182-112">UI 스택이 사용 하지 않도록 설정 되 고 UI 앱이 시작 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="72182-112">The UI stack is disabled and UI apps will not launch.</span></span> <span data-ttu-id="72182-113">이렇게 하면 사용 되는 시스템 리소스의 양이 줄어듭니다.</span><span class="sxs-lookup"><span data-stu-id="72182-113">This reduces the amount of system resources used.</span></span> <span data-ttu-id="72182-114">장치에 모니터를 연결 하면 화면이 검게 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="72182-114">If you attach a monitor to your device, the screen will be black.</span></span>

> [!NOTE]
> <span data-ttu-id="72182-115">장치를 헤드리스 모드로 전환 하는 경우 아래에 설명 된 Windows 10 IoT Core 대시보드 응용 프로그램을 사용 하 여 해당 IP 주소를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72182-115">If you put your device into headless mode, then you can use the Windows 10 IoT Core Dashboard application, described below, to find its IP address.</span></span>

## <a name="changing-the-mode"></a><span data-ttu-id="72182-116">모드 변경</span><span class="sxs-lookup"><span data-stu-id="72182-116">Changing the mode</span></span>
<span data-ttu-id="72182-117">Windows PowerShell 세션 또는 SSH 세션에서 장치의 양방향/헤드리스 상태를 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72182-117">You can modify the headed/headless state of your device from a Windows PowerShell session or an SSH session.</span></span> <span data-ttu-id="72182-118">PowerShell에 대해 자세히 알아보려면 [IoT Core 용 PowerShell](../connect-your-device/PowerShell.md) 페이지를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="72182-118">To learn more about PowerShell, see the [PowerShell for IoT Core](../connect-your-device/PowerShell.md) page.</span></span> <span data-ttu-id="72182-119">SSH에 대 한 자세한 내용은 [IoT Core 용 SSH](../connect-your-device/SSH.md) 페이지를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="72182-119">To learn more about SSH, see the [SSH for IoT Core](../connect-your-device/SSH.md) page.</span></span>

* <span data-ttu-id="72182-120">장치의 현재 상태를 표시 하려면 `setbootoption` 유틸리티를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="72182-120">To display the current state of your device, use the `setbootoption` utility:</span></span>

~~~
    [192.168.0.243]: PS C:\> setbootoption.exe
~~~

* <span data-ttu-id="72182-121">헤드리스 모드를 사용 하도록 장치 상태를 수정 하려면 다음 `setbootoption` `headless` 인수를 사용 하 여 유틸리티를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="72182-121">To modify the state of your device to enable headless mode, use the `setbootoption` utility with the `headless` arg:</span></span>

~~~
    [192.168.0.243]: PS C:\> setbootoption.exe headless
    [192.168.0.243]: PS C:\> shutdown /r /t 0
~~~

* <span data-ttu-id="72182-122">모드를 사용 하도록 장치 상태를 수정 하려면 다음 `setbootoption` `headed` 인수를 사용 하 여 유틸리티를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="72182-122">To modify the state of your device to enable headed mode, use the `setbootoption` utility with the `headed` arg:</span></span>

~~~
    [192.168.0.243]: PS C:\> setbootoption.exe headed
    [192.168.0.243]: PS C:\> shutdown /r /t 0
~~~

## <a name="finding-your-headless-device"></a><span data-ttu-id="72182-123">헤드리스 장치 찾기</span><span class="sxs-lookup"><span data-stu-id="72182-123">Finding your headless device</span></span>

<span data-ttu-id="72182-124">헤드리스 모드에 있는 IoT Core 장치는 **Windows 10 Iot Core 대시보드** 응용 프로그램을 사용 하 여 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72182-124">An IoT Core device that is in headless mode can be discovered using the **Windows 10 IoT Core Dashboard** application.</span></span>  <span data-ttu-id="72182-125">IoT 대시보드를 다운로드 하려면 [다운로드](http://go.microsoft.com/fwlink/?LinkID=708576) 페이지를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="72182-125">To download the IoT Dashboard, see the [Downloads](http://go.microsoft.com/fwlink/?LinkID=708576) page.</span></span>
<span data-ttu-id="72182-126">응용 프로그램을 실행 하면 로컬 네트워크의 모든 IoT Core 장치에서 ping을 수신 대기 하 고 이름, IP 주소 등의 장치 정보를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="72182-126">When running, the application listens for pings from any IoT Core devices on the local network and displays device information such as the name, IP address, and more.</span></span>

![Windows 10 IoT Core 대시보드](../media/HeadlessMode/selectDevice.png)
