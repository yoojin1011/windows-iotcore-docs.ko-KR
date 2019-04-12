---
title: 원격 표시
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 보기 및 Windows 10 IoT Core UWP 응용 프로그램을 원격으로 제어 하는 방법에 알아봅니다.
keywords: windows iot, UWP, 표시 되는 원격 원격 UWP 응용 프로그램
ms.openlocfilehash: 6f46ddbc5738f377ce3ebd15a49785e27c6a40bf
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513373"
---
# <a name="remote-display"></a><span data-ttu-id="2accd-104">원격 표시</span><span class="sxs-lookup"><span data-stu-id="2accd-104">Remote display</span></span>
<span data-ttu-id="2accd-105">보기 및 Windows 10 데스크톱 PC, 태블릿 또는 휴대폰에서 Windows 10 IoT Core UWP 응용 프로그램을 원격으로 제어</span><span class="sxs-lookup"><span data-stu-id="2accd-105">View and control your Windows 10 IoT Core UWP applications remotely, from a Windows 10 desktop PC, tablet, or phone</span></span>

> [!WARNING]
> <span data-ttu-id="2accd-106">Windows IoT 원격 클라이언트 개발자 유일한 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="2accd-106">Windows IoT Remote Client is a developer only feature.</span></span> <span data-ttu-id="2accd-107">사용 하거나 프로덕션 장치에 대 한 지원 되 는지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2accd-107">It is not intended or supported for production devices.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2accd-108">Raspberry Pi에 대 한 Windows IoT 원격 클라이언트 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2accd-108">The Windows IoT Remote client does not work for Raspberry Pi.</span></span> <span data-ttu-id="2accd-109">보드를 사용 하 여 가속된 그래픽 Minnowboard 최대 Dragonboard 등을 사용 하 여 또는 로컬 표시에 대 한 모니터를 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="2accd-109">Use a board with accelerated graphics such as Minnowboard Max or Dragonboard or attach a monitor for local display.</span></span>

## <a name="overview"></a><span data-ttu-id="2accd-110">개요</span><span class="sxs-lookup"><span data-stu-id="2accd-110">Overview</span></span>
___
<span data-ttu-id="2accd-111">표시 하는 원격 환경에는 Windows 10 IoT Core 장치에서 실행 하는 UWP 응용 프로그램을 원격으로 제어 하는 데 개발자 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="2accd-111">The remote display experience is a developer tool used to remotely control UWP applications running on a Windows 10 IoT Core device.</span></span>   

## <a name="setup"></a><span data-ttu-id="2accd-112">설치 프로그램</span><span class="sxs-lookup"><span data-stu-id="2accd-112">Setup</span></span>
___
<span data-ttu-id="2accd-113">Windows 10의 최신 빌드를 사용 하 여 Windows 10 IoT Core 장치를 설정 하려면 방문 해야 시작 하는 [시작](https://developer.microsoft.com/en-us/windows/iot/getstarted) 보드를 설정 하는 페이지입니다.</span><span class="sxs-lookup"><span data-stu-id="2accd-113">To get started, you'll need to set up a Windows 10 IoT Core device with the latest build of Windows 10 - visit the [Get Started](https://developer.microsoft.com/en-us/windows/iot/getstarted) page to set up your board.</span></span>

<span data-ttu-id="2accd-114">설치 프로그램을 쉽고 빠르게-표시 하는 원격 기술을 사용 하 여 다음 세 가지 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="2accd-114">Setup is quick and easy - follow the three steps below to use the remote display technology.</span></span>

1. <span data-ttu-id="2accd-115">IoT Core 장치 및 개발 컴퓨터는 보안 환경에 동일한 네트워크에 n을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="2accd-115">Ensure that your IoT Core device and development computer are on the same network and n a secure environment.</span></span>

    <span data-ttu-id="2accd-116">한 가지 방법은 자동 교차를 지 원하는 USB 이더넷 어댑터를 사용 하 여 랩톱에 직접 장치를 연결 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="2accd-116">One method is to connect your device directly to your laptop using a USB Ethernet adapter which supports automatic crossover.</span></span>

1. <span data-ttu-id="2accd-117">Windows 10 IoT Core 장치에 표시 하는 원격 기능을 켭니다.</span><span class="sxs-lookup"><span data-stu-id="2accd-117">Turn on the remote display functionality on your Windows 10 IoT Core device.</span></span>
  
    <span data-ttu-id="2accd-118">장치를 인터넷에 연결 하 고 Windows Device Portal 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="2accd-118">Connect your device to the Internet and connect to Windows Device Portal.</span></span>
  
    <span data-ttu-id="2accd-119">왼쪽의 옵션에서 "원격" 페이지를 선택 하 고 "창 IoT 원격 서버 사용" 라는 레이블이 있는 확인란을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="2accd-119">Choose the page "Remote" from the options on the left, and mark the check box labeled "Enable Window IoT Remote Server".</span></span>  <span data-ttu-id="2accd-120">장치는 이제 표시 하는 원격 환경을 사용 하도록 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2accd-120">Your device is now enabled for remote display experience.</span></span>
    ![표시 하는 원격 환경을 사용 하도록 설정](../media/RemoteDisplay/enable-remote.png)

1. <span data-ttu-id="2accd-122">관련 Windows 10 장치에서 Windows IoT 원격 클라이언트를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="2accd-122">Install the Windows IoT Remote Client on your companion Windows 10 device.</span></span>
  
    <span data-ttu-id="2accd-123">Windows 10 IoT Core 장치에 연결 하는 Windows 10 장치를 사용 하려면 저장소 응용 프로그램을 설치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2accd-123">To enable a Windows 10 device to connect to your Windows 10 IoT Core device, you need to install our Store application.</span></span>  <span data-ttu-id="2accd-124">Windows IoT 원격 클라이언트 앱은 현재 링크로 사용할 수 하 고 확인할 수 있습니다 [여기](https://www.microsoft.com/en-us/store/apps/iot-remote-client/9nblggh5mnxz)합니다.</span><span class="sxs-lookup"><span data-stu-id="2accd-124">The Windows IoT Remote Client app is currently available by link only and can be found [here](https://www.microsoft.com/en-us/store/apps/iot-remote-client/9nblggh5mnxz).</span></span>
    
    ![클라이언트 앱 설치](../media/RemoteDisplay/store-app.png)


1. <span data-ttu-id="2accd-126">설치 된 응용 프로그램을 통해 Windows 10 IoT Core 장치에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="2accd-126">Connect to your Windows 10 IoT Core device through the installed application.</span></span>
  
    <span data-ttu-id="2accd-127">Windows 10 관련 장치에서 Windows IoT 원격 클라이언트 응용 프로그램을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="2accd-127">Run the Windows IoT Remote Client application on your Windows 10 companion device.</span></span>  <span data-ttu-id="2accd-128">연결 화면에 장치의 IP 주소를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="2accd-128">At the Connect screen, enter the IP address of your device.</span></span> <span data-ttu-id="2accd-129">두 개의 장치 연결 해야, 원격 포함 장치는 Windows 10 IoT Core 장치의 UI 경험 합니다.</span><span class="sxs-lookup"><span data-stu-id="2accd-129">The two devices should connect, remoting the UI experience of the Windows 10 IoT Core device to the companion device.</span></span>
    
    <span data-ttu-id="2accd-130">지금 연결!</span><span class="sxs-lookup"><span data-stu-id="2accd-130">You're now connected!</span></span> <span data-ttu-id="2accd-131">이 지점에서 전달, 터치 하 고 제공 된 Windows 10 장치를 사용 하 여 Windows 10 IoT Core UWP 응용 프로그램을 제어할 수에서 입력을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="2accd-131">From this point forward, touch and click input on the companion Windows 10 device can be used to control the Windows 10 IoT Core UWP application.</span></span>  
    ![장치 연결](../media/RemoteDisplay/connect-device.png)
      

## <a name="compatibility-and-scope"></a><span data-ttu-id="2accd-133">호환성 및 범위</span><span class="sxs-lookup"><span data-stu-id="2accd-133">Compatibility and scope</span></span>
___
<span data-ttu-id="2accd-134">IoT 원격 클라이언트를 사용 하기 위해 실행 해야 Windows 10 IoT Core 최신 빌드 대상 장치에 최신 클라이언트 응용 프로그램 스토어에서.</span><span class="sxs-lookup"><span data-stu-id="2accd-134">In order to use the IoT Remote Client, you must be running the latest build of Windows 10 IoT Core on the target device and the latest client application from the store.</span></span> 
    
  
## <a name="troubleshooting"></a><span data-ttu-id="2accd-135">문제 해결</span><span class="sxs-lookup"><span data-stu-id="2accd-135">Troubleshooting</span></span>
___
<span data-ttu-id="2accd-136">표시 하는 원격 기술을 사용 하는 빠르고 쉬우며 있지만 여전히 사용자가 겪을 수 있는 몇 가지 문제가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2accd-136">Using the remote display technology is quick and easy, but there are still some issues that users may experience.</span></span>  <span data-ttu-id="2accd-137">위의 지침-밀접 하 게 문제가 지속 되 면 확인 아래 설치를 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2accd-137">Make sure to follow the Setup instructions above closely - if problems persist, check below.</span></span>

### <a name="when-i-try-to-connect-the-client-app-goes-to-a-white-screen"></a><span data-ttu-id="2accd-138">연결 하려고 할 때 클라이언트 앱 흰색 화면으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="2accd-138">When I try to connect, the client app goes to a white screen.</span></span>
<span data-ttu-id="2accd-139">실패 한 연결은 다양 한 문제를 발생할 수 있습니다 하지만 몇 가지 일반적인 문제를를 실행 했습니다.</span><span class="sxs-lookup"><span data-stu-id="2accd-139">Failed connections can be caused by a number of issues, but we've run into a couple more common problems:</span></span>

1. <span data-ttu-id="2accd-140">Windows 10 IoT Core 버전 및 IoT 원격 클라이언트 응용 프로그램이 최신 참가자를 실행 하는 것을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="2accd-140">Ensure that you are running the latest insider version of Windows 10 IoT Core and the IoT Remote Client application.</span></span>
1. <span data-ttu-id="2accd-141">먼저, 부록 장치와 같은 네트워크에는 IoT 장치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2accd-141">First, make sure your IoT device is on the same network as your companion device.</span></span>
    <span data-ttu-id="2accd-142">Windows 10 IoT Core 최신 참가자 빌드를 사용 하도록 설정 하 여 Windows IoT 원격 서버를 사용 하 여 실행 중인지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="2accd-142">Check that you're running the latest Insider build of Windows 10 IoT Core with the Windows IoT Remote Server enabled.</span></span>
1. <span data-ttu-id="2accd-143">문제가 없으면 장치를 지원 하도록 보장할 것의 해상도 장치의 웹 서버로 이동할 위의 설치 섹션의 1 단계에서 지침에 따라를 변경해 보세요.</span><span class="sxs-lookup"><span data-stu-id="2accd-143">If this isn't the issue, try changing the resolution of your device to something we're guaranteed to support Follow the instructions in step 1 of the Setup section above to navigate to your device's web server.</span></span>  <span data-ttu-id="2accd-144">왼쪽 메뉴에서 "Remote"를 선택 하는 대신 "홈" 페이지에 머무는 및 해상도 찾으려면 아래로 스크롤합니다.</span><span class="sxs-lookup"><span data-stu-id="2accd-144">Instead of selecting "Remote" from the menu on the left, stay on the "Home" page and scroll down to find resolution.</span></span>  <span data-ttu-id="2accd-145">800 x 600을 시도 합니다.</span><span class="sxs-lookup"><span data-stu-id="2accd-145">Try 800x600.</span></span>
1. <span data-ttu-id="2accd-146">여전히이 문제가 해결 되지 않으면, 되지 외장 디스플레이에 장치를 연결에서 발생 하는 문제를 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2accd-146">If this still doesn't fix your issue, you may have an issue that stems from never connecting your device to an external display.</span></span>
    <span data-ttu-id="2accd-147">이렇게 하면 순수 하 게 헤드리스으로 자체 생각 하면 장치.</span><span class="sxs-lookup"><span data-stu-id="2accd-147">This will cause the device to think of itself as purely headless.</span></span>  <span data-ttu-id="2accd-148">이 문제를 해결하려면:</span><span class="sxs-lookup"><span data-stu-id="2accd-148">To fix this:</span></span>
    * <span data-ttu-id="2accd-149">MicroSD 카드를 배출 하 고 컴퓨터에 배치</span><span class="sxs-lookup"><span data-stu-id="2accd-149">Eject the MicroSD Card, and put into your computer</span></span>
    * <span data-ttu-id="2accd-150">편집 된</span><span class="sxs-lookup"><span data-stu-id="2accd-150">Edit the</span></span> `<MicroSD card drive>:\config.txt`
    * <span data-ttu-id="2accd-151">다음 줄을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="2accd-151">Add the following lines:</span></span>
 
```
  hdmi_force_hotplug=1
  hdmi_group=2
  hdmi_mode=9
```
