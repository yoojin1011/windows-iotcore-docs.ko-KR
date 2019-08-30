---
title: Arduino 용 Windows 가상 실드 개요
author: saraclay
ms.author: saclayt
ms.date: 09/13/17
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: Arduino에 대 한 Windows 가상 실드를 설정 하 고 첫 번째 Windows 10 IoT Core 앱을 빌드하는 방법을 알아봅니다.
keywords: windows iot, WVSA, Windows 가상 실드, Arduino, 앱
ms.openlocfilehash: bd1dccd59fbc99de9076260f6e21b0ac1403660a
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "60169001"
---
> [!NOTE]
> <span data-ttu-id="17573-104">보관 된 설명서를 보고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17573-104">You are viewing archived documentation.</span></span> <span data-ttu-id="17573-105">AllJoyn는 Windows 10 IoT에서 더 이상 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="17573-105">AllJoyn is no longer supported by Windows 10 IoT.</span></span> <span data-ttu-id="17573-106">질문이 있는 경우 GitHub에서 문제를 열거나 아래 설명에 의견을 남겨 주세요.</span><span class="sxs-lookup"><span data-stu-id="17573-106">For questions, please open an issue on GitHub or leave us feedback in the comments below.</span></span>

# <a name="set-up-windows-virtual-shields-for-arduino"></a><span data-ttu-id="17573-107">Arduino에 대 한 Windows 가상 실드 설정</span><span class="sxs-lookup"><span data-stu-id="17573-107">Set up Windows Virtual Shields for Arduino</span></span>

## <a name="overview"></a><span data-ttu-id="17573-108">개요</span><span class="sxs-lookup"><span data-stu-id="17573-108">Overview</span></span>
<span data-ttu-id="17573-109">[Arduino](https://www.arduino.cc)를 사용 하는 경우 방패 개념에 대해 잘 알고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17573-109">If you’ve used an [Arduino](https://www.arduino.cc), you’re familiar with the concept of a shield.</span></span> <span data-ttu-id="17573-110">각 방패는 특별 한 용도 (예: 온도 쉴드,가 속도계 방패)를 가지 며 여러 실드를 사용 하 여 장치를 빌드하는 것은 복잡 하 고, 비용이 많이 들고, 공간이 비효율적입니다.</span><span class="sxs-lookup"><span data-stu-id="17573-110">Each shield has a specialized purpose (e.g. a temperature shield, an accelerometer shield), and building a device with multiple shields can be complex, costly, and space-inefficient.</span></span> <span data-ttu-id="17573-111">이제 저비용의 Windows Lumia Phone을 압축 된 실드 집합으로 사용할 수 있다고 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="17573-111">Now imagine that you can use a low-cost Windows Lumia Phone as a compact set of shields.</span></span> <span data-ttu-id="17573-112">Arduino 스케치는 사용 하기 쉬운 라이브러리 호출을 통해 Windows Phone에서 수많은 센서 및 기능에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17573-112">Your Arduino sketch would be able to access hundreds of dollars worth of sensors and capabilities in your Windows Phone through easy-to-use library calls.</span></span>

<span data-ttu-id="17573-113">이는 개발자를 위해 Windows 가상 실드 for Arduino 라이브러리를 사용 하는 것과 정확히 일치 합니다.</span><span class="sxs-lookup"><span data-stu-id="17573-113">This is exactly what the Windows Virtual Shields for Arduino library enables for developers.</span></span> <span data-ttu-id="17573-114">가장 좋은 부분은 아닙니다 .이 기술은 모든 Windows 10 장치에서 작동 하므로 PC 또는 표면의 센서와 기능을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17573-114">And that’s not the best part - this technology works on all Windows 10 devices, so you can use the sensors and capabilities on your PC or Surface as well.</span></span> <span data-ttu-id="17573-115">또한 Arduino는 음성 인식 및 웹 구문 분석과 같은 계산 부담이 큰 작업을 Windows 10 자매 장치로 오프 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17573-115">Also, the Arduino can offload computationally expensive tasks like speech recognition and web parsing to the Windows 10 companion device!</span></span>

<span data-ttu-id="17573-116">Arduino 용 Windows 가상 실드를 사용 하도록 하드웨어 및 소프트웨어를 설정 하는 방법에 대해 알아보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="17573-116">Let's learn how to setup hardware and software to work with Windows Virtual Shields for Arduino.</span></span>


## <a name="1-get-your-windows-10-device-ready-for-developing-projects-using-windows-virtual-shields-for-arduino"></a><span data-ttu-id="17573-117">1. Windows 가상 실드 for Arduino를 사용 하 여 프로젝트를 개발할 준비가 된 Windows 10 장치를 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="17573-117">1. Get your Windows 10 device ready for developing projects using Windows Virtual Shields for Arduino.</span></span>

<span data-ttu-id="17573-118">자습서의이 섹션에서는 Windows 가상 실드 for Arduino 응용 프로그램을 사용 하 여 로드 하 여 원하는 Windows 10 장치를 준비 합니다 .이 유니버설 Windows 응용 프로그램을 사용 하면 Arduino 보드에 대 한 "가상 실드"로 장치를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17573-118">In this section of the tutorial, you'll prepare a Windows 10 device of your choice by loading it with the Windows Virtual Shields for Arduino application - this Universal Windows Application allows you to use your device as a "virtual shield" for an Arduino board.</span></span>  <span data-ttu-id="17573-119">이로 인해 작성자가 음성 인식, 터치 스크린, 상대적으로 Windows의 계산 능력을 활용할 수 있는 몇 가지 강력한 가능성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17573-119">This results in some powerful possibilities for Makers, allowing them to utilize voice recognition, touch screens, and the computational power of Windows with relative ease.</span></span>

### <a name="hardware"></a><span data-ttu-id="17573-120">하드웨어</span><span class="sxs-lookup"><span data-stu-id="17573-120">Hardware</span></span>
<span data-ttu-id="17573-121">Windows 가상 실드 for Arduino 응용 프로그램은 모든 Windows 10 장치에서 실행할 수 있지만이 자습서에서는 Windows Phone를 사용 하는 설정을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="17573-121">The Windows Virtual Shields for Arduino application can run on any Windows 10 device, but this tutorial will explain setup with a Windows Phone.</span></span>

<span data-ttu-id="17573-122">*필요한 항목* Windows 10을 실행 하는 Windows Phone- [Lumia 520](http://www.microsoft.com/en-us/mobile/phone/lumia520) 또는 [Lumia 635](http://www.microsoft.com/en-us/mobile/phone/lumia635)를 권장 합니다.</span><span class="sxs-lookup"><span data-stu-id="17573-122">*What you need* Windows Phone running Windows 10 - we recommend the [Lumia 520](http://www.microsoft.com/en-us/mobile/phone/lumia520) or [Lumia 635](http://www.microsoft.com/en-us/mobile/phone/lumia635).</span></span>

<span data-ttu-id="17573-123">*Windows Phone 설정*</span><span class="sxs-lookup"><span data-stu-id="17573-123">*Set up your Windows Phone*</span></span>

<span data-ttu-id="17573-124">휴대폰에 아직 Windows 10이 실행 되 고 있지 않은 경우 소프트웨어의 미리 보기 버전을 설치 하는 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17573-124">If your phone is not already running Windows 10, there are options to install preview versions of the software.</span></span>  <span data-ttu-id="17573-125">Windows Phone 8 사용자가 Microsoft Store 앱으로 이동 하 여 "Windows 참가자" 응용 프로그램을 다운로드할 수 있습니다 .이 앱을 통해 사용자는 Windows 10 Technical preview를 업데이트로 받도록 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17573-125">Windows Phone 8 users can go to the Microsoft Store app to download the "Windows Insider" application - this app allows the user to opt into receiving Windows 10 Technical Previews as updates.</span></span>  <span data-ttu-id="17573-126">앱을 열 때 표시 되는 메시지 및 지침에 따라 휴대폰에서 Windows 10이 성공적으로 실행 되 면 계속 합니다.</span><span class="sxs-lookup"><span data-stu-id="17573-126">Follow the prompts and instructions upon opening the app, and continue once your phone is successfully running Windows 10.</span></span>

### <a name="software"></a><span data-ttu-id="17573-127">소프트웨어</span><span class="sxs-lookup"><span data-stu-id="17573-127">Software</span></span>

<span data-ttu-id="17573-128">Windows Phone에 Windows 가상 실드 for Arduino UWP 앱을 설치 하는 두 가지 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17573-128">There are two options for installing the Windows Virtual Shields for Arduino UWP app on your Windows Phone.</span></span>  <span data-ttu-id="17573-129">앱을 다운로드 하는 것이 더 간단 합니다.</span><span class="sxs-lookup"><span data-stu-id="17573-129">Downloading the app is the easier, quicker choice.</span></span>

* <span data-ttu-id="17573-130">Microsoft Store에서 앱 다운로드</span><span class="sxs-lookup"><span data-stu-id="17573-130">Download the app from the Microsoft Store</span></span>
* <span data-ttu-id="17573-131">PC 및 Visual Studio를 사용 하 여 앱 테스트용으로 로드</span><span class="sxs-lookup"><span data-stu-id="17573-131">Sideload the app using a PC and Visual Studio</span></span>

<span data-ttu-id="17573-132">*옵션 1: Microsoft Store에서 앱 다운로드*</span><span class="sxs-lookup"><span data-stu-id="17573-132">*Option 1: Download the app from the Microsoft Store*</span></span>

<span data-ttu-id="17573-133">Arduino에 대 한 Windows 가상 실드의 Microsoft Store 페이지에 대 한 [링크](https://www.microsoft.com/store/apps/9nblgggz0mld) 를 따라 응용 프로그램을 다운로드 한 다음를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="17573-133">Follow this [link](https://www.microsoft.com/store/apps/9nblgggz0mld) to the Microsoft Store page for Windows Virtual Shields for Arduino, download the application, and then install.</span></span> <span data-ttu-id="17573-134">그런 다음 응용 프로그램이 제대로 실행 되는지 확인 하기 위해 응용 프로그램을 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17573-134">You can then open the application to ensure it runs properly.</span></span>  <span data-ttu-id="17573-135">이제 장치가 Arduino에 대 한 "가상 실드"로 사용 되도록 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="17573-135">Your device is now setup to be used as a "virtual shield" for an Arduino!</span></span>  <span data-ttu-id="17573-136">다음 페이지로 진행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17573-136">You can proceed to the next page.</span></span>

<span data-ttu-id="17573-137">*옵션 2: PC 및 Visual Studio*
를 사용 하 여 앱 테스트용으로 로드_필요한 항목_</span><span class="sxs-lookup"><span data-stu-id="17573-137">*Option 2: Sideload the app using a PC and Visual Studio*
_What you need_</span></span>
* <span data-ttu-id="17573-138">Visual Studio 2017는 Arduino 용 Windows 가상 실드 앱을 개발자가 잠근 휴대폰으로 테스트용으로 로드.</span><span class="sxs-lookup"><span data-stu-id="17573-138">Visual Studio 2017 to sideload the Windows Virtual Shields for Arduino app onto a developer-unlocked phone.</span></span>
* <span data-ttu-id="17573-139">Arduino 용 Windows 가상 실드 응용 프로그램에 대 한 코드를 포함 하는이 [리포지토리입니다](https://github.com/ms-iot/virtual-shields-universal) .</span><span class="sxs-lookup"><span data-stu-id="17573-139">This [repository](https://github.com/ms-iot/virtual-shields-universal) containing the code for the Windows Virtual Shields for Arduino application.</span></span>  <span data-ttu-id="17573-140">리포지토리를 복제 하거나 로컬 디스크에서 ZIP으로 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="17573-140">Either clone the repository or download it as a ZIP on your local disk.</span></span>  <span data-ttu-id="17573-141">Git에 익숙하지 않은 경우 적절 한 복제본을 사용 하려면 [여기](https://help.github.com/articles/cloning-a-repository)에 있는 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="17573-141">If you're not familiar with git and want to do a proper clone, follow the instructions [here](https://help.github.com/articles/cloning-a-repository).</span></span>

<span data-ttu-id="17573-142">_Visual Studio 2017 설정_</span><span class="sxs-lookup"><span data-stu-id="17573-142">_Set up Visual Studio 2017_</span></span>
1. <span data-ttu-id="17573-143">[Dev.windows.com](https://developer.microsoft.com/en-us/windows/downloads)의 Windows 10 Developer Preview 도구를 사용 하 여 Visual Studio 2017을 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="17573-143">Install Visual Studio 2017 with the Windows 10 Developer Preview tools from [dev.windows.com](https://developer.microsoft.com/en-us/windows/downloads).</span></span>  <span data-ttu-id="17573-144">Visual Studio의 무료 Community 버전을 사용 하는 것이 좋지만 Enterprise와 Professional은 모두 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="17573-144">We recommend the free Community Version of Visual Studio, but both Enterprise and Professional will work as well.</span></span>  <span data-ttu-id="17573-145">Visual Studio가 이미 설치 되어 있는 경우 다음 단계로 건너뜁니다.</span><span class="sxs-lookup"><span data-stu-id="17573-145">If you already have Visual Studio installed, skip to the next step.</span></span>
2. <span data-ttu-id="17573-146">Visual Studio에서 위의 "필요한 항목" 섹션에 다운로드 한 리포지토리에서 실드를 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="17573-146">In Visual Studio, load the Shield.sln from the repository downloaded in the "What you need" section above.</span></span>
3. <span data-ttu-id="17573-147">Windows 10 장치 (이 경우 Windows Phone)가 개발자 잠금 해제 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="17573-147">Ensure your Windows 10 device (in this case a Windows Phone) is developer-unlocked.</span></span> <span data-ttu-id="17573-148">[이 페이지](https://msdn.microsoft.com/library/windows/apps/dn614128.aspx) 에서는 Windows Phone 8.1, 8 및 7.1의 잠금을 해제 하는 방법을 설명 합니다. 그러나 Windows 10 phone의 단계는 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="17573-148">[This page](https://msdn.microsoft.com/library/windows/apps/dn614128.aspx) explains how to unlock Windows Phone 8.1, 8, and 7.1; however, the steps are the same for Windows 10 phones.</span></span>
4. <span data-ttu-id="17573-149">Windows 10 장치를 컴퓨터에 연결 하 고 실드 .sln 프로그램을 장치에 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="17573-149">Plug your Windows 10 device into your computer and deploy the Shield.sln program to your device.</span></span>  <span data-ttu-id="17573-150">이렇게 하려면 "로컬 컴퓨터"에 배포 하 고 장치의 아키텍처를 "ARM"으로 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="17573-150">To do this, deploy to a "Local Machine", and be sure to set the architecture of the device as "ARM".</span></span>
5. <span data-ttu-id="17573-151">휴대폰에서 새로 설치 된 Arduino 용 Windows 가상 실드 응용 프로그램을 실행 하 여 배포가 성공적으로 완료 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="17573-151">Run the newly-installed Windows Virtual Shields for Arduino application on your phone to ensure the deploy was successful.</span></span>  <span data-ttu-id="17573-152">이제 Windows 10 장치가 가상 실드로 사용 되도록 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="17573-152">Your Windows 10 device is now setup to be used as a virtual shield!</span></span>

## <a name="2-set-up-your-arduino-to-use-the-windows-virtual-shields-for-arduino-library"></a><span data-ttu-id="17573-153">2. Arduino 라이브러리에 Windows 가상 실드를 사용 하도록 Arduino 설정</span><span class="sxs-lookup"><span data-stu-id="17573-153">2. Set up your Arduino to use the Windows Virtual Shields for Arduino library</span></span> 
<span data-ttu-id="17573-154">Windows 10 자매 장치를 제대로 설정 하면 Arduino 라이브러리에 Windows 가상 실드를 사용할 수 있도록 준비 Arduino.</span><span class="sxs-lookup"><span data-stu-id="17573-154">With our Windows 10 companion device properly set up, let's get our Arduino ready to use the Windows Virtual Shields for Arduino library.</span></span> <span data-ttu-id="17573-155">USB, Bluetooth 또는 Wi-fi를 통해 Arduino와 Windows 10 "가상 실드" 간에 연결을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17573-155">You can establish a connection between your Arduino and your Windows 10 "virtual shield" over USB, Bluetooth, or Wi-Fi.</span></span> <span data-ttu-id="17573-156">이 특정 자습서에서는 Bluetooth 연결을 사용 하 여 설치를 완료 하는 방법을 설명 하지만 다른 옵션을 사용해 보세요.</span><span class="sxs-lookup"><span data-stu-id="17573-156">This particular tutorial will explain how to complete setup using a Bluetooth connection, but feel free to experiment with the other options.</span></span>

### <a name="hardware"></a><span data-ttu-id="17573-157">하드웨어</span><span class="sxs-lookup"><span data-stu-id="17573-157">Hardware</span></span>
<span data-ttu-id="17573-158">*필요한 항목*</span><span class="sxs-lookup"><span data-stu-id="17573-158">*What you need*</span></span>
* <span data-ttu-id="17573-159">Arduino Uno 또는 호환 장치</span><span class="sxs-lookup"><span data-stu-id="17573-159">Arduino Uno or compatible device</span></span>
* <span data-ttu-id="17573-160">와이어 연결</span><span class="sxs-lookup"><span data-stu-id="17573-160">Connecting wires</span></span>
* <span data-ttu-id="17573-161">Arduino 스케치를 업로드 하는 데 사용 되는 PC</span><span class="sxs-lookup"><span data-stu-id="17573-161">A PC used to upload your Arduino sketches</span></span>
* <span data-ttu-id="17573-162">표준 A ~ 표준 B USB-Arduino 장치에 대 한 스케치를 업로드 하는 데 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="17573-162">Standard A to Standard B USB - needed to upload sketches to your Arduino device</span></span>
* <span data-ttu-id="17573-163">선택 사항: Bluetooth 모듈-Bluetooth에서 연결 하도록 선택한 경우에만 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="17573-163">Optional: Bluetooth module - only needed if you choose to connect by Bluetooth.</span></span>
* <span data-ttu-id="17573-164">선택 사항: Wi-fi 모듈-wi-fi로 연결 하도록 선택한 경우에만 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="17573-164">Optional: Wi-fi module - only needed if you choose to connect by wi-fi.</span></span>

* <span data-ttu-id="17573-165">Arduino 설정</span><span class="sxs-lookup"><span data-stu-id="17573-165">Set up your Arduino</span></span>
* <span data-ttu-id="17573-166">필요한 경우 Bluetooth 모듈을 준비 합니다 (Bluetooth 모듈에 헤더를 납땜 해야 할 수 있음).</span><span class="sxs-lookup"><span data-stu-id="17573-166">Prepare the Bluetooth module if necessary (the Bluetooth module may need to have headers soldered onto it).</span></span>
* <span data-ttu-id="17573-167">아래에 설명 된 것과 다른 하나를 제외 하 고, [배선 다이어그램](https://learn.sparkfun.com/tutorials/using-the-bluesmirf/hardware-hookup)에 따라 Bluetooth 모듈을 Arduino에 연결 했습니다.</span><span class="sxs-lookup"><span data-stu-id="17573-167">Except for the one different noted below, connected the Bluetooth module to the Arduino per [the wiring diagram](https://learn.sparkfun.com/tutorials/using-the-bluesmirf/hardware-hookup).</span></span>

  * <span data-ttu-id="17573-168">뺀 2 및 3 대신 pin 0과 1을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="17573-168">Difference: Use pins 0 and 1 instead of 2 and 3:</span></span>
    * <span data-ttu-id="17573-169">Bluetooth TX는 핀 0 (Arduino RX 또는 RX0)에 연결 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="17573-169">The Bluetooth TX should connect to pin 0 (Arduino RX or RX0).</span></span>
    * <span data-ttu-id="17573-170">Bluetooth RX는 pin 1 (Arduino TX 또는 TX1)에 연결 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="17573-170">The Bluetooth RX should connect to pin 1 (Arduino TX or TX1).</span></span>

### <a name="software"></a><span data-ttu-id="17573-171">소프트웨어</span><span class="sxs-lookup"><span data-stu-id="17573-171">Software</span></span>
<span data-ttu-id="17573-172">*필요한 항목*</span><span class="sxs-lookup"><span data-stu-id="17573-172">*What you need*</span></span>
* <span data-ttu-id="17573-173">Arduino IDE 1.6 이상</span><span class="sxs-lookup"><span data-stu-id="17573-173">Arduino IDE 1.6 or better</span></span>
* <span data-ttu-id="17573-174">ArduinoJSON 라이브러리</span><span class="sxs-lookup"><span data-stu-id="17573-174">ArduinoJSON library</span></span>
* <span data-ttu-id="17573-175">[이 리포지토리](https://github.com/ms-iot/virtual-shields-arduino)는 Arduino에서 실행 되는 예제 스케치를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="17573-175">[This repository](https://github.com/ms-iot/virtual-shields-arduino), which contains the example sketch which will run on the Arduino.</span></span>

<span data-ttu-id="17573-176">*Arduino IDE 설정*</span><span class="sxs-lookup"><span data-stu-id="17573-176">*Set up your Arduino IDE*</span></span>
* <span data-ttu-id="17573-177">Arduino IDE를 다운로드 하 여 설치한 후 프로그램을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="17573-177">Download and install the Arduino IDE, then launch the program.</span></span>
* <span data-ttu-id="17573-178">*도구 > 보드*에서 올바른 Arduino board가 선택 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="17573-178">Verify that you have the correct Arduino board selected under *Tools > Board*.</span></span>
* <span data-ttu-id="17573-179">*도구 > 포트*에서 올바른 COM 포트가 선택 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="17573-179">Verify that you have the correct COM Port selected under *Tools > Port*.</span></span> <span data-ttu-id="17573-180">보드의 이름은 각 옵션 옆에 표시 되므로 올바른 옵션을 훨씬 쉽게 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17573-180">The name of the board should appear next to each option, making it much easier to choose the correct option.</span></span>

<span data-ttu-id="17573-181">*ArduinoJSON 라이브러리 설정*</span><span class="sxs-lookup"><span data-stu-id="17573-181">*Set up the ArduinoJSON library*</span></span>
* <span data-ttu-id="17573-182">[ArduinoJson 리포지토리에서](https://github.com/bblanchon/ArduinoJson)리포지토리를 복제 하거나 zip을 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="17573-182">From the [ArduinoJson repository](https://github.com/bblanchon/ArduinoJson), clone the repository or download the zip.</span></span>
* <span data-ttu-id="17573-183">라이브러리 폴더에 전체 리포지토리를 저장 합니다 (예: `Documents\Arduino\libraries\ArduinoJson\`).</span><span class="sxs-lookup"><span data-stu-id="17573-183">Place the whole repository into your libraries folder (i.e. `Documents\Arduino\libraries\ArduinoJson\`).</span></span>

<span data-ttu-id="17573-184">*Arduino 라이브러리에 대 한 Windows 가상 실드 설정*</span><span class="sxs-lookup"><span data-stu-id="17573-184">*Set up the Windows Virtual Shields for Arduino Library*</span></span>
* <span data-ttu-id="17573-185">[이 리포지토리](https://github.com/ms-iot/virtual-shields-arduino) 를 복제 하거나 ZIP을 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="17573-185">Clone [this repository](https://github.com/ms-iot/virtual-shields-arduino) or download the ZIP.</span></span> <span data-ttu-id="17573-186">Git에 익숙하지 않은 경우 적절 한 복제본을 사용 하려면 [여기](https://help.github.com/articles/cloning-a-repository/)에 있는 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="17573-186">If you're not familiar with git and want to do a proper clone, follow the instructions [here](https://help.github.com/articles/cloning-a-repository/).</span></span>
* <span data-ttu-id="17573-187">방금 다운로드 한 리포지토리의 "Arduino\Libraries" 폴더에 있는 "VirtualShield" 폴더를 Arduino library 폴더 (예: `Documents\Arduino\libraries\VirtualShield\`)에 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="17573-187">Copy the "VirtualShield" folder, found in the "Arduino\Libraries" folder of the repository you just downloaded, to your Arduino library folder (i.e. `Documents\Arduino\libraries\VirtualShield\`).</span></span>

<span data-ttu-id="17573-188">*설치 테스트*</span><span class="sxs-lookup"><span data-stu-id="17573-188">*Test your setup*</span></span>
* <span data-ttu-id="17573-189">Arduino IDE에서 메뉴 항목 *파일-> 예제 > 가상 실드 > HelloWorld-음성 이벤트*로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="17573-189">From the Arduino IDE, go to the menu item *File -> Examples -> Virtual Shield -> HelloWorld-Speech-Eventing*.</span></span> <span data-ttu-id="17573-190">이렇게 하면이 자습서에 사용 하는 Hello World을 기반으로 음성 인식을 로드 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="17573-190">This should load the speech-recognition based Hello World example we're using for this tutorial.</span></span>
* <span data-ttu-id="17573-191">Arduino에 스케치를 업로드 하기 전에 Arduino에서 Bluetooth TX 및 RX 와이어를 일시적으로 제거 합니다 (USB와 Bluetooth 간에는 하나의 직렬 포트만 공유 됨). Bluetooth는 업로드를 방해 합니다.</span><span class="sxs-lookup"><span data-stu-id="17573-191">Before uploading the sketch to your Arduino, temporarily remove the Bluetooth TX and RX wires from the Arduino (there is only one serial port shared between the USB and Bluetooth - the Bluetooth interferes with the upload).</span></span>
* <span data-ttu-id="17573-192">IDE에서 "업로드" 단추를 눌러 스케치를 업로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="17573-192">Upload the sketch by pressing the "Upload" button in the IDE.</span></span>
* <span data-ttu-id="17573-193">Bluetooth TX 및 RX 와이어를 Arduino 핀 (Bluetooth TX에서 Arduino RX (또는 RX0)으로, Bluetooth RX에서 Arduino TX 또는 (TX1))으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="17573-193">Replace the Bluetooth TX and RX wires into the Arduino pins (Bluetooth TX to Arduino RX (or RX0) and Bluetooth RX to Arduino TX or (TX1)).</span></span>
* <span data-ttu-id="17573-194">이전 페이지에서 준비한 휴대폰 (또는 기타 Windows 장치)에서 Bluetooth 설정의 Arduino Bluetooth 장치에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="17573-194">On the phone (or other Windows device) you prepared on the previous page, pair to the Bluetooth device on your Arduino in the Bluetooth settings.</span></span> <span data-ttu-id="17573-195">BlueSMiRF를 사용 하는 경우 기본 pin 코드는 1234입니다.</span><span class="sxs-lookup"><span data-stu-id="17573-195">If you're using the BlueSMiRF, the default pin code is 1234.</span></span> 

> [!NOTE]
> <span data-ttu-id="17573-196">BlueSMiRF에 깜박이는 빨간색 빛은 성공적으로 페어링 된 후 계속 빨간색으로 깜박입니다.</span><span class="sxs-lookup"><span data-stu-id="17573-196">The red blinking light on the BlueSMiRF continues to blink red after a successful pairing.</span></span> <span data-ttu-id="17573-197">이는 예정된 동작입니다.</span><span class="sxs-lookup"><span data-stu-id="17573-197">This is expected.</span></span> <span data-ttu-id="17573-198">Arduino 용 Windows 가상 실드 응용 프로그램을 연결한 후에만 녹색으로 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="17573-198">It only turns green after a connecting with the Windows Virtual Shields for Arduino application.</span></span>


## <a name="3-write-your-first-app-hello-blinky"></a><span data-ttu-id="17573-199">3. 첫 번째 앱 작성: 안녕하세요.</span><span class="sxs-lookup"><span data-stu-id="17573-199">3. Write your first app: Hello, Blinky!</span></span> 

### <a name="hello-world-speech-enabled-led-example"></a><span data-ttu-id="17573-200">Hello World 음성 사용 LED 예제</span><span class="sxs-lookup"><span data-stu-id="17573-200">Hello World speech-enabled LED example</span></span>
<span data-ttu-id="17573-201">이 자습서의 이전 단계에 자세히 설명 된 대로 Windows Phone (또는 잠재적으로 Windows 10 장치!)를 사용 하 고 Arduino 준비 되었으므로 이제 샘플을 사용해 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17573-201">With your Windows Phone (or potentially any Windows 10 device!) and your Arduino prepared as detailed in the previous steps of this tutorial, you're now ready to try our sample.</span></span>

1. <span data-ttu-id="17573-202">저항기가 있는 LED를 핀 8에 연결 하 여 Arduino 보드를 준비 합니다.</span><span class="sxs-lookup"><span data-stu-id="17573-202">Prepare your Arduino board by hooking up an LED with a resistor to pin 8.</span></span>
2. <span data-ttu-id="17573-203">Arduino이 아직 HelloWorld-음성 이벤트 샘플로 업로드 되었는지 확인 한 다음 Arduino를 전원 공급 장치에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="17573-203">Make sure that your Arduino is still uploaded with the HelloWorld-Speech-Eventing sample, and then plug the Arduino into a power supply.</span></span>
3. <span data-ttu-id="17573-204">이전에 준비한 Windows Phone에서 Arduino 용 Windows 가상 실드 앱을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="17573-204">Run the Windows Virtual Shields for Arduino app on the Windows Phone you prepared previously.</span></span>
4. <span data-ttu-id="17573-205">모든 것이 제대로 설정 된 경우 휴대폰은 Arduino 스케치에 연결 하 여 오디오 신호를 시작 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="17573-205">If everything has been setup properly, your phone should connect to your Arduino sketch and welcome you with an audio cue.</span></span> <span data-ttu-id="17573-206">이제 Windows 10 장치에 대 한 ' 켜기 ' 또는 ' 끄기 '를 통해 Arduino의 LED를 설정 하 고 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17573-206">You can now say 'on' or 'off' to your Windows 10 device to switch the LED on your Arduino between on and off!</span></span>

### <a name="arduino-wiring-sketch-hello-world-example"></a><span data-ttu-id="17573-207">Arduino 배선 스케치: Hello World 예제</span><span class="sxs-lookup"><span data-stu-id="17573-207">Arduino Wiring Sketch: Hello World example</span></span>

```C++
#include <ArduinoJson.h>

#include <VirtualShield.h>
#include <Text.h>
#include <Speech.h>
#include <Recognition.h>

VirtualShield shield;             // identify the shield
Text screen = Text(shield);       // connect the screen
Speech speech = Speech(shield);   // connect text to speech
Recognition recognition = Recognition(shield);    // connect speech to text

int LED_PIN = 8;

void recognitionEvent(ShieldEvent* event)
{
  if (event->resultId > 0) {
    digitalWrite(LED_PIN, recognition.recognizedIndex == 1 ? HIGH : LOW);
    screen.printAt(4, "Heard " + String(recognition.recognizedIndex == 1 ? "on" : "off"));
    recognition.listenFor("on,off", false);     // reset up the recognition after each event
  }
}

// when Bluetooth connects, or the 'Refresh' button is pressed
void refresh(ShieldEvent* event)
{
  String message = "Hello Virtual Shields. Say the word 'on' or 'off' to affect the LED";

  screen.clear();
  screen.print(message);
  speech.speak(message);

  recognition.listenFor("on,off", false);   // NON-blocking instruction to recognize speech
}

void setup()
{
  pinMode(LED_PIN, OUTPUT);
  pinMode(LED_PIN, LOW);

  recognition.setOnEvent(recognitionEvent); // set up a function to handle recognition events (turns auto-blocking off)
  shield.setOnRefresh(refresh);

  // begin() communication - you may specify a baud rate here, default is 115200
  shield.begin();
}

void loop()
{
  shield.checkSensors();            // handles Virtual Shield events.
}
```


