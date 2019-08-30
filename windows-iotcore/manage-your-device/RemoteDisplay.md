---
title: 원격 표시
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Windows 10 IoT Core UWP 응용 프로그램을 원격으로 확인 하 고 제어 하는 방법을 알아봅니다.
keywords: windows iot, UWP, 원격 디스플레이, 원격, UWP 응용 프로그램
ms.openlocfilehash: 6f46ddbc5738f377ce3ebd15a49785e27c6a40bf
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "60170711"
---
# <a name="remote-display"></a><span data-ttu-id="1d107-104">원격 표시</span><span class="sxs-lookup"><span data-stu-id="1d107-104">Remote display</span></span>
<span data-ttu-id="1d107-105">Windows 10 desktop PC, 태블릿 또는 휴대폰에서 원격으로 Windows 10 IoT Core UWP 응용 프로그램 보기 및 제어</span><span class="sxs-lookup"><span data-stu-id="1d107-105">View and control your Windows 10 IoT Core UWP applications remotely, from a Windows 10 desktop PC, tablet, or phone</span></span>

> [!WARNING]
> <span data-ttu-id="1d107-106">Windows IoT 원격 클라이언트는 개발자 전용 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="1d107-106">Windows IoT Remote Client is a developer only feature.</span></span> <span data-ttu-id="1d107-107">프로덕션 장치에 적합 하지 않거나 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1d107-107">It is not intended or supported for production devices.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1d107-108">Windows IoT 원격 클라이언트가 Raspberry Pi와 함께 작동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1d107-108">The Windows IoT Remote client does not work for Raspberry Pi.</span></span> <span data-ttu-id="1d107-109">Minnowboard Max 또는 Dragonboard처럼 가속 그래픽을 사용하는 보드를 사용하거나 로컬 표시용 모니터를 연결하세요.</span><span class="sxs-lookup"><span data-stu-id="1d107-109">Use a board with accelerated graphics such as Minnowboard Max or Dragonboard or attach a monitor for local display.</span></span>

## <a name="overview"></a><span data-ttu-id="1d107-110">개요</span><span class="sxs-lookup"><span data-stu-id="1d107-110">Overview</span></span>
___
<span data-ttu-id="1d107-111">원격 표시 환경은 Windows 10 IoT Core 장치에서 실행 되는 UWP 응용 프로그램을 원격으로 제어 하는 데 사용 되는 개발자 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="1d107-111">The remote display experience is a developer tool used to remotely control UWP applications running on a Windows 10 IoT Core device.</span></span>   

## <a name="setup"></a><span data-ttu-id="1d107-112">설정</span><span class="sxs-lookup"><span data-stu-id="1d107-112">Setup</span></span>
___
<span data-ttu-id="1d107-113">시작 하려면 Windows 10의 최신 빌드를 사용 하 여 Windows 10 IoT Core 장치를 설정 해야 합니다. [시작](https://developer.microsoft.com/en-us/windows/iot/getstarted) 페이지를 방문 하 여 보드를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d107-113">To get started, you'll need to set up a Windows 10 IoT Core device with the latest build of Windows 10 - visit the [Get Started](https://developer.microsoft.com/en-us/windows/iot/getstarted) page to set up your board.</span></span>

<span data-ttu-id="1d107-114">설치는 빠르고 간단 합니다. 원격 디스플레이 기술을 사용 하려면 아래의 세 단계를 따르세요.</span><span class="sxs-lookup"><span data-stu-id="1d107-114">Setup is quick and easy - follow the three steps below to use the remote display technology.</span></span>

1. <span data-ttu-id="1d107-115">IoT Core 장치 및 개발 컴퓨터가 동일한 네트워크 및 n 보안 환경에 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d107-115">Ensure that your IoT Core device and development computer are on the same network and n a secure environment.</span></span>

    <span data-ttu-id="1d107-116">한 가지 방법은 자동 교차를 지 원하는 USB 이더넷 어댑터를 사용 하 여 장치를 노트북에 직접 연결 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="1d107-116">One method is to connect your device directly to your laptop using a USB Ethernet adapter which supports automatic crossover.</span></span>

1. <span data-ttu-id="1d107-117">Windows 10 IoT Core 장치에서 원격 표시 기능을 켭니다.</span><span class="sxs-lookup"><span data-stu-id="1d107-117">Turn on the remote display functionality on your Windows 10 IoT Core device.</span></span>
  
    <span data-ttu-id="1d107-118">장치를 인터넷에 연결 하 고 Windows 장치 포털에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d107-118">Connect your device to the Internet and connect to Windows Device Portal.</span></span>
  
    <span data-ttu-id="1d107-119">왼쪽의 옵션에서 "원격" 페이지를 선택 하 고 "Window IoT 원격 서버 사용" 이라는 확인란을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d107-119">Choose the page "Remote" from the options on the left, and mark the check box labeled "Enable Window IoT Remote Server".</span></span>  <span data-ttu-id="1d107-120">이제 장치가 원격 디스플레이 환경에서 사용 하도록 설정 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1d107-120">Your device is now enabled for remote display experience.</span></span>
    <span data-ttu-id="1d107-121">![원격 디스플레이 환경 사용](../media/RemoteDisplay/enable-remote.png)</span><span class="sxs-lookup"><span data-stu-id="1d107-121">![Enable remote display experience](../media/RemoteDisplay/enable-remote.png)</span></span>

1. <span data-ttu-id="1d107-122">Windows IoT 원격 클라이언트를 부록 Windows 10 장치에 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d107-122">Install the Windows IoT Remote Client on your companion Windows 10 device.</span></span>
  
    <span data-ttu-id="1d107-123">Windows 10 장치를 Windows 10 IoT Core 장치에 연결할 수 있도록 하려면 스토어 응용 프로그램을 설치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d107-123">To enable a Windows 10 device to connect to your Windows 10 IoT Core device, you need to install our Store application.</span></span>  <span data-ttu-id="1d107-124">Windows IoT 원격 클라이언트 앱은 현재 링크만 사용할 수 있으며 [여기](https://www.microsoft.com/en-us/store/apps/iot-remote-client/9nblggh5mnxz)에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1d107-124">The Windows IoT Remote Client app is currently available by link only and can be found [here](https://www.microsoft.com/en-us/store/apps/iot-remote-client/9nblggh5mnxz).</span></span>
    
    ![클라이언트 앱 설치](../media/RemoteDisplay/store-app.png)


1. <span data-ttu-id="1d107-126">설치 된 응용 프로그램을 통해 Windows 10 IoT Core 장치에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d107-126">Connect to your Windows 10 IoT Core device through the installed application.</span></span>
  
    <span data-ttu-id="1d107-127">Windows 10 자매 장치에서 Windows IoT 원격 클라이언트 응용 프로그램을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d107-127">Run the Windows IoT Remote Client application on your Windows 10 companion device.</span></span>  <span data-ttu-id="1d107-128">연결 화면에서 장치의 IP 주소를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d107-128">At the Connect screen, enter the IP address of your device.</span></span> <span data-ttu-id="1d107-129">두 장치는 연결 하 고, Windows 10 IoT Core 장치의 UI 환경을 도우미 장치에 원격으로 연결 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d107-129">The two devices should connect, remoting the UI experience of the Windows 10 IoT Core device to the companion device.</span></span>
    
    <span data-ttu-id="1d107-130">이제 연결 되었습니다!</span><span class="sxs-lookup"><span data-stu-id="1d107-130">You're now connected!</span></span> <span data-ttu-id="1d107-131">이 시점부터 터치 하 고 Windows 10 장치에서 입력을 클릭 하면 Windows 10 IoT Core UWP 응용 프로그램을 제어 하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1d107-131">From this point forward, touch and click input on the companion Windows 10 device can be used to control the Windows 10 IoT Core UWP application.</span></span>  
    ![장치 연결](../media/RemoteDisplay/connect-device.png)
      

## <a name="compatibility-and-scope"></a><span data-ttu-id="1d107-133">호환성 및 범위</span><span class="sxs-lookup"><span data-stu-id="1d107-133">Compatibility and scope</span></span>
___
<span data-ttu-id="1d107-134">IoT 원격 클라이언트를 사용 하려면 대상 장치 및 스토어의 최신 클라이언트 응용 프로그램에서 Windows 10 IoT Core의 최신 빌드를 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d107-134">In order to use the IoT Remote Client, you must be running the latest build of Windows 10 IoT Core on the target device and the latest client application from the store.</span></span> 
    
  
## <a name="troubleshooting"></a><span data-ttu-id="1d107-135">문제 해결</span><span class="sxs-lookup"><span data-stu-id="1d107-135">Troubleshooting</span></span>
___
<span data-ttu-id="1d107-136">원격 표시 기술을 사용 하는 것은 쉽고 간단 하지만 사용자에 게 발생할 수 있는 몇 가지 문제가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1d107-136">Using the remote display technology is quick and easy, but there are still some issues that users may experience.</span></span>  <span data-ttu-id="1d107-137">위의 설정 지침을 면밀 하 게 확인 하세요. 문제가 지속 되 면 아래를 확인 하세요.</span><span class="sxs-lookup"><span data-stu-id="1d107-137">Make sure to follow the Setup instructions above closely - if problems persist, check below.</span></span>

### <a name="when-i-try-to-connect-the-client-app-goes-to-a-white-screen"></a><span data-ttu-id="1d107-138">연결 하려고 하면 클라이언트 앱이 흰색 화면으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d107-138">When I try to connect, the client app goes to a white screen.</span></span>
<span data-ttu-id="1d107-139">실패 한 연결은 여러 가지 문제로 인해 발생할 수 있지만 몇 가지 일반적인 문제가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1d107-139">Failed connections can be caused by a number of issues, but we've run into a couple more common problems:</span></span>

1. <span data-ttu-id="1d107-140">최신 참가자 버전의 Windows 10 IoT Core 및 IoT 원격 클라이언트 응용 프로그램을 실행 중인지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d107-140">Ensure that you are running the latest insider version of Windows 10 IoT Core and the IoT Remote Client application.</span></span>
1. <span data-ttu-id="1d107-141">먼저 IoT 장치가 사용자의 도우미 장치와 동일한 네트워크에 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d107-141">First, make sure your IoT device is on the same network as your companion device.</span></span>
    <span data-ttu-id="1d107-142">Windows IoT 원격 서버를 사용 하도록 설정 하 여 Windows 10 IoT Core의 최신 Insider build를 실행 하 고 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d107-142">Check that you're running the latest Insider build of Windows 10 IoT Core with the Windows IoT Remote Server enabled.</span></span>
1. <span data-ttu-id="1d107-143">이 문제가 발생 하지 않는 경우, 위의 설정 섹션 1 단계에 있는 지침에 따라 장치의 웹 서버를 탐색 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="1d107-143">If this isn't the issue, try changing the resolution of your device to something we're guaranteed to support Follow the instructions in step 1 of the Setup section above to navigate to your device's web server.</span></span>  <span data-ttu-id="1d107-144">왼쪽의 메뉴에서 "원격"을 선택 하는 대신 "홈" 페이지를 그대로 유지 하 고 아래로 스크롤하여 해상도를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d107-144">Instead of selecting "Remote" from the menu on the left, stay on the "Home" page and scroll down to find resolution.</span></span>  <span data-ttu-id="1d107-145">800x600.</span><span class="sxs-lookup"><span data-stu-id="1d107-145">Try 800x600.</span></span>
1. <span data-ttu-id="1d107-146">그래도 문제가 해결 되지 않으면 장치를 외부 디스플레이에 연결 하지 않는 문제가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1d107-146">If this still doesn't fix your issue, you may have an issue that stems from never connecting your device to an external display.</span></span>
    <span data-ttu-id="1d107-147">이로 인해 장치는 완전히 헤드리스로 간주 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1d107-147">This will cause the device to think of itself as purely headless.</span></span>  <span data-ttu-id="1d107-148">이 문제를 해결하려면:</span><span class="sxs-lookup"><span data-stu-id="1d107-148">To fix this:</span></span>
    * <span data-ttu-id="1d107-149">마이크로 Sd 카드를 꺼내고 컴퓨터에 배치 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d107-149">Eject the MicroSD Card, and put into your computer</span></span>
    * <span data-ttu-id="1d107-150">편집`<MicroSD card drive>:\config.txt`</span><span class="sxs-lookup"><span data-stu-id="1d107-150">Edit the `<MicroSD card drive>:\config.txt`</span></span>
    * <span data-ttu-id="1d107-151">다음 줄을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d107-151">Add the following lines:</span></span>
 
```
  hdmi_force_hotplug=1
  hdmi_group=2
  hdmi_mode=9
```
