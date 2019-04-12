---
title: Windows 가상 Shields Arduino 개요
author: saraclay
ms.author: saclayt
ms.date: 09/13/17
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: Arduino에 대 한 Windows 가상 Shields 설정 하 여 첫 번째 Windows 10 IoT Core 앱을 구축 하는 방법을 알아봅니다.
keywords: windows iot, WVSA, Windows 가상 방패, Arduino, 앱
ms.openlocfilehash: bd1dccd59fbc99de9076260f6e21b0ac1403660a
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513174"
---
> [!NOTE]
> <span data-ttu-id="838ae-104">보관 된 설명서가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="838ae-104">You are viewing archived documentation.</span></span> <span data-ttu-id="838ae-105">Windows 10 IoT에서 더 이상 AllJoyn 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="838ae-105">AllJoyn is no longer supported by Windows 10 IoT.</span></span> <span data-ttu-id="838ae-106">질문에 대 한 GitHub에서 문제를 제기 하거나 아래 설명에 의견을 남길 하세요.</span><span class="sxs-lookup"><span data-stu-id="838ae-106">For questions, please open an issue on GitHub or leave us feedback in the comments below.</span></span>

# <a name="set-up-windows-virtual-shields-for-arduino"></a><span data-ttu-id="838ae-107">Windows 가상 Shields Arduino에 대 한 설정</span><span class="sxs-lookup"><span data-stu-id="838ae-107">Set up Windows Virtual Shields for Arduino</span></span>

## <a name="overview"></a><span data-ttu-id="838ae-108">개요</span><span class="sxs-lookup"><span data-stu-id="838ae-108">Overview</span></span>
<span data-ttu-id="838ae-109">사용한 경우는 [Arduino](https://www.arduino.cc), 방어막의 개념에 익숙할 것입니다.</span><span class="sxs-lookup"><span data-stu-id="838ae-109">If you’ve used an [Arduino](https://www.arduino.cc), you’re familiar with the concept of a shield.</span></span> <span data-ttu-id="838ae-110">각 보호 특수 용도 (예:는 온도 shield는가 속도계 방패), 있으며 복잡 하 고, 비용이 많이 들며, 공간 비효율적인 수 여러 방패 표시를 사용 하 여 장치를 구축 합니다.</span><span class="sxs-lookup"><span data-stu-id="838ae-110">Each shield has a specialized purpose (e.g. a temperature shield, an accelerometer shield), and building a device with multiple shields can be complex, costly, and space-inefficient.</span></span> <span data-ttu-id="838ae-111">이제 사용할 수 있는 저렴 한 비용 Windows Lumia 휴대폰 shields의 간단한 집합으로 가정해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="838ae-111">Now imagine that you can use a low-cost Windows Lumia Phone as a compact set of shields.</span></span> <span data-ttu-id="838ae-112">사용자가 Arduino 스케치에 수백 달러 가치가 센서에 Windows Phone 기능을 사용 하기 쉬운 라이브러리 호출을 통해 액세스할 수 있게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="838ae-112">Your Arduino sketch would be able to access hundreds of dollars worth of sensors and capabilities in your Windows Phone through easy-to-use library calls.</span></span>

<span data-ttu-id="838ae-113">이것이 개발자를 위한 덕분에 Arduino 라이브러리에 대 한 Windows 가상 Shields입니다.</span><span class="sxs-lookup"><span data-stu-id="838ae-113">This is exactly what the Windows Virtual Shields for Arduino library enables for developers.</span></span> <span data-ttu-id="838ae-114">가장 중요 한 부분 없는-고이 기술이 작동 하는 모든 Windows 10 장치에서 사용할 수 있도록 기능과 센서 PC 또는 Surface도 합니다.</span><span class="sxs-lookup"><span data-stu-id="838ae-114">And that’s not the best part - this technology works on all Windows 10 devices, so you can use the sensors and capabilities on your PC or Surface as well.</span></span> <span data-ttu-id="838ae-115">또한에서 Arduino 음성 인식 및 Windows 10 포함 장치를 구문 분석 하는 웹과 같은 계산 비용이 많이 드는 작업을 오프 로드할 수 있습니다!</span><span class="sxs-lookup"><span data-stu-id="838ae-115">Also, the Arduino can offload computationally expensive tasks like speech recognition and web parsing to the Windows 10 companion device!</span></span>

<span data-ttu-id="838ae-116">하드웨어 및 소프트웨어를 Windows 가상 Shields Arduino에 대 한 작업을 설정 하는 방법을 알아보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="838ae-116">Let's learn how to setup hardware and software to work with Windows Virtual Shields for Arduino.</span></span>


## <a name="1-get-your-windows-10-device-ready-for-developing-projects-using-windows-virtual-shields-for-arduino"></a><span data-ttu-id="838ae-117">1. Windows 가상 Shields를 사용 하 여 Arduino에 대 한 프로젝트를 개발 하기 위한 준비 된 Windows 10 장치를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="838ae-117">1. Get your Windows 10 device ready for developing projects using Windows Virtual Shields for Arduino.</span></span>

<span data-ttu-id="838ae-118">자습서의이 섹션에서는 Arduino 응용 프로그램에 대 한 Windows 가상 Shields를 사용 하 여 로드 하 여 원하는 Windows 10 장치 준비-이 유니버설 Windows 응용 프로그램을 Arduino 보드에 대 한 "가상 방패"으로 장치를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="838ae-118">In this section of the tutorial, you'll prepare a Windows 10 device of your choice by loading it with the Windows Virtual Shields for Arduino application - this Universal Windows Application allows you to use your device as a "virtual shield" for an Arduino board.</span></span>  <span data-ttu-id="838ae-119">이 인해 결정권자 음성 인식 기능을 활용할 수 있도록 몇 가지 강력한 가능성에 상대적인 편의성에 화면 및 Windows의 계산 능력을 터치 합니다.</span><span class="sxs-lookup"><span data-stu-id="838ae-119">This results in some powerful possibilities for Makers, allowing them to utilize voice recognition, touch screens, and the computational power of Windows with relative ease.</span></span>

### <a name="hardware"></a><span data-ttu-id="838ae-120">하드웨어</span><span class="sxs-lookup"><span data-stu-id="838ae-120">Hardware</span></span>
<span data-ttu-id="838ae-121">Arduino 응용 프로그램에 대 한 Windows 가상 Shields는 모든 Windows 10 장치에서 실행할 수는 있지만이 자습서에서는 Windows Phone 사용 하 여 설치에 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="838ae-121">The Windows Virtual Shields for Arduino application can run on any Windows 10 device, but this tutorial will explain setup with a Windows Phone.</span></span>

<span data-ttu-id="838ae-122">*필요한* Windows Phone 좋습니다-Windows 10을 실행 합니다 [Lumia 520](http://www.microsoft.com/en-us/mobile/phone/lumia520) 또는 [Lumia 635](http://www.microsoft.com/en-us/mobile/phone/lumia635)합니다.</span><span class="sxs-lookup"><span data-stu-id="838ae-122">*What you need* Windows Phone running Windows 10 - we recommend the [Lumia 520](http://www.microsoft.com/en-us/mobile/phone/lumia520) or [Lumia 635](http://www.microsoft.com/en-us/mobile/phone/lumia635).</span></span>

*<span data-ttu-id="838ae-123">에 Windows Phone 설정</span><span class="sxs-lookup"><span data-stu-id="838ae-123">Set up your Windows Phone</span></span>*

<span data-ttu-id="838ae-124">휴대폰 이미 Windows 10를 실행 하지 않는 경우 미리 보기 버전의 소프트웨어를 설치 하는 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="838ae-124">If your phone is not already running Windows 10, there are options to install preview versions of the software.</span></span>  <span data-ttu-id="838ae-125">Windows Phone 8 사용자가 "Windows Insider" 응용 프로그램을 다운로드 하려면 Microsoft Store 앱을 이동할 수-이 앱이 Windows 10 Technical Preview로 업데이트 수신을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="838ae-125">Windows Phone 8 users can go to the Microsoft Store app to download the "Windows Insider" application - this app allows the user to opt into receiving Windows 10 Technical Previews as updates.</span></span>  <span data-ttu-id="838ae-126">프롬프트 및 앱을 열 때 지침을 따르고 휴대폰 성공적으로 Windows 10을 실행 한 후 계속 합니다.</span><span class="sxs-lookup"><span data-stu-id="838ae-126">Follow the prompts and instructions upon opening the app, and continue once your phone is successfully running Windows 10.</span></span>

### <a name="software"></a><span data-ttu-id="838ae-127">소프트웨어</span><span class="sxs-lookup"><span data-stu-id="838ae-127">Software</span></span>

<span data-ttu-id="838ae-128">Windows Phone Arduino UWP 앱에 대 한 Windows 가상 Shields 설치에 대 한 두 가지 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="838ae-128">There are two options for installing the Windows Virtual Shields for Arduino UWP app on your Windows Phone.</span></span>  <span data-ttu-id="838ae-129">앱을 다운로드 하는 보다 쉽게, 더 빠른 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="838ae-129">Downloading the app is the easier, quicker choice.</span></span>

* <span data-ttu-id="838ae-130">Microsoft Store 앱을 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="838ae-130">Download the app from the Microsoft Store</span></span>
* <span data-ttu-id="838ae-131">PC 및 Visual Studio를 사용 하 여 앱을 테스트용으로 로드</span><span class="sxs-lookup"><span data-stu-id="838ae-131">Sideload the app using a PC and Visual Studio</span></span>

*<span data-ttu-id="838ae-132">옵션 1: Microsoft Store 앱을 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="838ae-132">Option 1: Download the app from the Microsoft Store</span></span>*

<span data-ttu-id="838ae-133">이 따라 [링크](https://www.microsoft.com/store/apps/9nblgggz0mld) Arduino에 대 한 가상 Shields Windows에 대 한 Microsoft Store 페이지로 응용 프로그램을 다운로드 및 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="838ae-133">Follow this [link](https://www.microsoft.com/store/apps/9nblgggz0mld) to the Microsoft Store page for Windows Virtual Shields for Arduino, download the application, and then install.</span></span> <span data-ttu-id="838ae-134">응용 프로그램이 제대로 실행 되도록 응용 프로그램을 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="838ae-134">You can then open the application to ensure it runs properly.</span></span>  <span data-ttu-id="838ae-135">장치의는 Arduino에 대 한 "가상 방패"로 사용할 설치 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="838ae-135">Your device is now setup to be used as a "virtual shield" for an Arduino!</span></span>  <span data-ttu-id="838ae-136">다음 페이지로 진행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="838ae-136">You can proceed to the next page.</span></span>

<span data-ttu-id="838ae-137">*옵션 2: PC 및 Visual Studio를 사용 하 여 앱을 테스트용으로 로드*
_해야 하는 작업_</span><span class="sxs-lookup"><span data-stu-id="838ae-137">*Option 2: Sideload the app using a PC and Visual Studio*
_What you need_</span></span>
* <span data-ttu-id="838ae-138">개발자 잠금 해제 된 휴대폰으로 Arduino 앱에 대 한 Windows 가상 Shields 테스트용으로 로드 하려면 visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="838ae-138">Visual Studio 2017 to sideload the Windows Virtual Shields for Arduino app onto a developer-unlocked phone.</span></span>
* <span data-ttu-id="838ae-139">이렇게 [리포지토리](https://github.com/ms-iot/virtual-shields-universal) Arduino 응용 프로그램에 대 한 Windows 가상 Shields에 대 한 코드를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="838ae-139">This [repository](https://github.com/ms-iot/virtual-shields-universal) containing the code for the Windows Virtual Shields for Arduino application.</span></span>  <span data-ttu-id="838ae-140">리포지토리 복제 또는 로컬 디스크에 ZIP으로 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="838ae-140">Either clone the repository or download it as a ZIP on your local disk.</span></span>  <span data-ttu-id="838ae-141">적절 한 복제 작업을 수행 하 고 git를 사용 하 여 잘 모르는 경우 지침을 따릅니다 [여기](https://help.github.com/articles/cloning-a-repository)합니다.</span><span class="sxs-lookup"><span data-stu-id="838ae-141">If you're not familiar with git and want to do a proper clone, follow the instructions [here](https://help.github.com/articles/cloning-a-repository).</span></span>

_<span data-ttu-id="838ae-142">Visual Studio 2017 설정</span><span class="sxs-lookup"><span data-stu-id="838ae-142">Set up Visual Studio 2017</span></span>_
1. <span data-ttu-id="838ae-143">Windows 10 개발자 미리 보기 도구를 사용 하 여 Visual Studio 2017 설치 [dev.windows.com](https://developer.microsoft.com/en-us/windows/downloads)합니다.</span><span class="sxs-lookup"><span data-stu-id="838ae-143">Install Visual Studio 2017 with the Windows 10 Developer Preview tools from [dev.windows.com](https://developer.microsoft.com/en-us/windows/downloads).</span></span>  <span data-ttu-id="838ae-144">무료 커뮤니티 버전의 Visual Studio에서 권장 되지만 Enterprise 및 Professional도 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="838ae-144">We recommend the free Community Version of Visual Studio, but both Enterprise and Professional will work as well.</span></span>  <span data-ttu-id="838ae-145">설치 된 Visual Studio에 이미 있는 경우 다음 단계를 건너뜁니다.</span><span class="sxs-lookup"><span data-stu-id="838ae-145">If you already have Visual Studio installed, skip to the next step.</span></span>
2. <span data-ttu-id="838ae-146">Visual Studio에서 부하 리포지토리에서 Shield.sln에는 "필요한"에서 다운로드 하는 한 위 섹션입니다.</span><span class="sxs-lookup"><span data-stu-id="838ae-146">In Visual Studio, load the Shield.sln from the repository downloaded in the "What you need" section above.</span></span>
3. <span data-ttu-id="838ae-147">(이 경우에는 Windows Phone)에서 Windows 10 장치는 개발자 잠금 해제를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="838ae-147">Ensure your Windows 10 device (in this case a Windows Phone) is developer-unlocked.</span></span> <span data-ttu-id="838ae-148">[하지만이 페이지](https://msdn.microsoft.com/library/windows/apps/dn614128.aspx) Windows Phone 8.1, 8 및 7.1; 잠금을 해제 하는 방법에 설명 단계는 동일한 Windows 10 phone 용입니다.</span><span class="sxs-lookup"><span data-stu-id="838ae-148">[This page](https://msdn.microsoft.com/library/windows/apps/dn614128.aspx) explains how to unlock Windows Phone 8.1, 8, and 7.1; however, the steps are the same for Windows 10 phones.</span></span>
4. <span data-ttu-id="838ae-149">Windows 10 장치를 컴퓨터에 연결 하 고 장치의 Shield.sln 프로그램을 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="838ae-149">Plug your Windows 10 device into your computer and deploy the Shield.sln program to your device.</span></span>  <span data-ttu-id="838ae-150">이 위해 "로컬 컴퓨터"에 배포 하 고 장치 "ARM"로 아키텍처를 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="838ae-150">To do this, deploy to a "Local Machine", and be sure to set the architecture of the device as "ARM".</span></span>
5. <span data-ttu-id="838ae-151">Windows 배포 되도록 휴대폰 Arduino 응용 프로그램에 대 한 가상 Shields는 새로 설치 된 실행 성공 했습니다.</span><span class="sxs-lookup"><span data-stu-id="838ae-151">Run the newly-installed Windows Virtual Shields for Arduino application on your phone to ensure the deploy was successful.</span></span>  <span data-ttu-id="838ae-152">Windows 10 장치의 가상 방어막으로 사용 하도록 설정 되었습니다!</span><span class="sxs-lookup"><span data-stu-id="838ae-152">Your Windows 10 device is now setup to be used as a virtual shield!</span></span>

## <a name="2-set-up-your-arduino-to-use-the-windows-virtual-shields-for-arduino-library"></a><span data-ttu-id="838ae-153">2. Arduino 라이브러리에 대 한 Windows 가상 방패 표시를 사용 하 여 Arduino 설정</span><span class="sxs-lookup"><span data-stu-id="838ae-153">2. Set up your Arduino to use the Windows Virtual Shields for Arduino library</span></span> 
<span data-ttu-id="838ae-154">Windows 10 관련 장치를 사용 하 여 제대로 설정, Arduino 라이브러리에 대 한 Windows 가상 방패 표시를 사용 하 여 Arduino 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="838ae-154">With our Windows 10 companion device properly set up, let's get our Arduino ready to use the Windows Virtual Shields for Arduino library.</span></span> <span data-ttu-id="838ae-155">USB, Bluetooth 또는 Wi-fi에 Arduino 및 Windows 10 "가상 방패" 간의 연결을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="838ae-155">You can establish a connection between your Arduino and your Windows 10 "virtual shield" over USB, Bluetooth, or Wi-Fi.</span></span> <span data-ttu-id="838ae-156">이 특정 자습서 Bluetooth 연결을 사용 하 여 설치를 완료 하는 방법에 설명 하지만 다른 옵션을 사용해 자유롭게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="838ae-156">This particular tutorial will explain how to complete setup using a Bluetooth connection, but feel free to experiment with the other options.</span></span>

### <a name="hardware"></a><span data-ttu-id="838ae-157">하드웨어</span><span class="sxs-lookup"><span data-stu-id="838ae-157">Hardware</span></span>
*<span data-ttu-id="838ae-158">필요한 것</span><span class="sxs-lookup"><span data-stu-id="838ae-158">What you need</span></span>*
* <span data-ttu-id="838ae-159">Arduino Uno 또는 호환 되는 장치</span><span class="sxs-lookup"><span data-stu-id="838ae-159">Arduino Uno or compatible device</span></span>
* <span data-ttu-id="838ae-160">와이어를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="838ae-160">Connecting wires</span></span>
* <span data-ttu-id="838ae-161">PC에 Arduino 스케치를 업로드 하는 데 사용</span><span class="sxs-lookup"><span data-stu-id="838ae-161">A PC used to upload your Arduino sketches</span></span>
* <span data-ttu-id="838ae-162">표준 장치의 Arduino 스케치를 업로드 하는 데 필요한 표준 B USB-A</span><span class="sxs-lookup"><span data-stu-id="838ae-162">Standard A to Standard B USB - needed to upload sketches to your Arduino device</span></span>
* <span data-ttu-id="838ae-163">선택 사항: Bluetooth 모듈-Bluetooth 하 여 연결 하려는 경우에 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="838ae-163">Optional: Bluetooth module - only needed if you choose to connect by Bluetooth.</span></span>
* <span data-ttu-id="838ae-164">선택 사항: -Fi 모듈--fi 하 여 연결 하려는 경우에 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="838ae-164">Optional: Wi-fi module - only needed if you choose to connect by wi-fi.</span></span>

* <span data-ttu-id="838ae-165">에 Arduino 설정</span><span class="sxs-lookup"><span data-stu-id="838ae-165">Set up your Arduino</span></span>
* <span data-ttu-id="838ae-166">(Bluetooth 모듈 야 할 수도 납땜 헤더) 필요한 경우 Bluetooth 모듈을 준비 합니다.</span><span class="sxs-lookup"><span data-stu-id="838ae-166">Prepare the Bluetooth module if necessary (the Bluetooth module may need to have headers soldered onto it).</span></span>
* <span data-ttu-id="838ae-167">제외 하 고 다른 아래 나와 있는, Bluetooth 모듈 당 Arduino에 연결 [배선 다이어그램이](https://learn.sparkfun.com/tutorials/using-the-bluesmirf/hardware-hookup)합니다.</span><span class="sxs-lookup"><span data-stu-id="838ae-167">Except for the one different noted below, connected the Bluetooth module to the Arduino per [the wiring diagram](https://learn.sparkfun.com/tutorials/using-the-bluesmirf/hardware-hookup).</span></span>

  * <span data-ttu-id="838ae-168">차이점: 대신 2 및 3 핀 0과 1을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="838ae-168">Difference: Use pins 0 and 1 instead of 2 and 3:</span></span>
    * <span data-ttu-id="838ae-169">Bluetooth TX 핀 0 (Arduino RX 또는 RX0)에 연결 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="838ae-169">The Bluetooth TX should connect to pin 0 (Arduino RX or RX0).</span></span>
    * <span data-ttu-id="838ae-170">Bluetooth RX (Arduino TX 또는 TX1) 1 핀에 연결 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="838ae-170">The Bluetooth RX should connect to pin 1 (Arduino TX or TX1).</span></span>

### <a name="software"></a><span data-ttu-id="838ae-171">소프트웨어</span><span class="sxs-lookup"><span data-stu-id="838ae-171">Software</span></span>
*<span data-ttu-id="838ae-172">필요한 것</span><span class="sxs-lookup"><span data-stu-id="838ae-172">What you need</span></span>*
* <span data-ttu-id="838ae-173">Arduino IDE 버전 1.6 이상</span><span class="sxs-lookup"><span data-stu-id="838ae-173">Arduino IDE 1.6 or better</span></span>
* <span data-ttu-id="838ae-174">ArduinoJSON 라이브러리</span><span class="sxs-lookup"><span data-stu-id="838ae-174">ArduinoJSON library</span></span>
* <span data-ttu-id="838ae-175">[이 리포지토리에](https://github.com/ms-iot/virtual-shields-arduino),이 Arduino에서 실행 하는 예제 스케치를 포함 하는 합니다.</span><span class="sxs-lookup"><span data-stu-id="838ae-175">[This repository](https://github.com/ms-iot/virtual-shields-arduino), which contains the example sketch which will run on the Arduino.</span></span>

*<span data-ttu-id="838ae-176">Arduino IDE 설정</span><span class="sxs-lookup"><span data-stu-id="838ae-176">Set up your Arduino IDE</span></span>*
* <span data-ttu-id="838ae-177">다운로드 하 고 Arduino IDE 설치 프로그램을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="838ae-177">Download and install the Arduino IDE, then launch the program.</span></span>
* <span data-ttu-id="838ae-178">올바른 Arduino 보드에서 선택 했는지 확인 하십시오 *도구 > 보드*합니다.</span><span class="sxs-lookup"><span data-stu-id="838ae-178">Verify that you have the correct Arduino board selected under *Tools > Board*.</span></span>
* <span data-ttu-id="838ae-179">아래에서 선택 되는 올바른 COM 포트가 있는지 확인 하십시오 *도구 > 포트*합니다.</span><span class="sxs-lookup"><span data-stu-id="838ae-179">Verify that you have the correct COM Port selected under *Tools > Port*.</span></span> <span data-ttu-id="838ae-180">보드의 이름을 쉽게 올바른 옵션을 선택 하는 각 옵션에 옆에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="838ae-180">The name of the board should appear next to each option, making it much easier to choose the correct option.</span></span>

*<span data-ttu-id="838ae-181">ArduinoJSON 라이브러리 설정</span><span class="sxs-lookup"><span data-stu-id="838ae-181">Set up the ArduinoJSON library</span></span>*
* <span data-ttu-id="838ae-182">[ArduinoJson 리포지토리](https://github.com/bblanchon/ArduinoJson), 리포지토리를 복제 하거나 zip을 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="838ae-182">From the [ArduinoJson repository](https://github.com/bblanchon/ArduinoJson), clone the repository or download the zip.</span></span>
* <span data-ttu-id="838ae-183">전체 저장소 라이브러리 폴더에 배치 (즉, `Documents\Arduino\libraries\ArduinoJson\`).</span><span class="sxs-lookup"><span data-stu-id="838ae-183">Place the whole repository into your libraries folder (i.e. `Documents\Arduino\libraries\ArduinoJson\`).</span></span>

*<span data-ttu-id="838ae-184">Windows 가상 Shields Arduino 라이브러리에 대 한 설정</span><span class="sxs-lookup"><span data-stu-id="838ae-184">Set up the Windows Virtual Shields for Arduino Library</span></span>*
* <span data-ttu-id="838ae-185">클론 [이 리포지토리](https://github.com/ms-iot/virtual-shields-arduino) 또는 ZIP을 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="838ae-185">Clone [this repository](https://github.com/ms-iot/virtual-shields-arduino) or download the ZIP.</span></span> <span data-ttu-id="838ae-186">적절 한 복제 작업을 수행 하 고 git를 사용 하 여 잘 모르는 경우 지침을 따릅니다 [여기](https://help.github.com/articles/cloning-a-repository/)합니다.</span><span class="sxs-lookup"><span data-stu-id="838ae-186">If you're not familiar with git and want to do a proper clone, follow the instructions [here](https://help.github.com/articles/cloning-a-repository/).</span></span>
* <span data-ttu-id="838ae-187">"VirtualShield" 폴더를 복사, Arduino 라이브러리 폴더에 방금 다운로드 한 리포지토리의 "Arduino\Libraries" 폴더에 있는 (즉, `Documents\Arduino\libraries\VirtualShield\`).</span><span class="sxs-lookup"><span data-stu-id="838ae-187">Copy the "VirtualShield" folder, found in the "Arduino\Libraries" folder of the repository you just downloaded, to your Arduino library folder (i.e. `Documents\Arduino\libraries\VirtualShield\`).</span></span>

*<span data-ttu-id="838ae-188">설정 테스트</span><span class="sxs-lookup"><span data-stu-id="838ae-188">Test your setup</span></span>*
* <span data-ttu-id="838ae-189">Arduino IDE에서 메뉴 항목으로 이동 *파일에는 예제-> 가상 방패-> HelloWorld-음성-이벤트->* 합니다.</span><span class="sxs-lookup"><span data-stu-id="838ae-189">From the Arduino IDE, go to the menu item *File -> Examples -> Virtual Shield -> HelloWorld-Speech-Eventing*.</span></span> <span data-ttu-id="838ae-190">이이 자습서에서는 기반 음성 인식 Hello World 예제를 로드 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="838ae-190">This should load the speech-recognition based Hello World example we're using for this tutorial.</span></span>
* <span data-ttu-id="838ae-191">하 여 Arduino 스케치를 업로드 하기 전에 일시적으로 (하나씩만 있기 USB 및 Bluetooth-Bluetooth 간에 공유 되는 직렬 포트 업로드 방해) Arduino에서 Bluetooth TX 및 RX 와이어를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="838ae-191">Before uploading the sketch to your Arduino, temporarily remove the Bluetooth TX and RX wires from the Arduino (there is only one serial port shared between the USB and Bluetooth - the Bluetooth interferes with the upload).</span></span>
* <span data-ttu-id="838ae-192">IDE의 "업로드" 단추를 눌러 스케치를 업로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="838ae-192">Upload the sketch by pressing the "Upload" button in the IDE.</span></span>
* <span data-ttu-id="838ae-193">Bluetooth TX 및 RX 와이어 Arduino pin으로 바꿉니다 (Arduino RX (또는 RX0) TX Bluetooth 및 Bluetooth Arduino tx RX 또는 (TX1)).</span><span class="sxs-lookup"><span data-stu-id="838ae-193">Replace the Bluetooth TX and RX wires into the Arduino pins (Bluetooth TX to Arduino RX (or RX0) and Bluetooth RX to Arduino TX or (TX1)).</span></span>
* <span data-ttu-id="838ae-194">휴대폰 (또는 다른 Windows 장치) 쌍 Bluetooth 장치에서 Bluetooth 설정 프로그램 Arduino에 이전 페이지에서 준비 합니다.</span><span class="sxs-lookup"><span data-stu-id="838ae-194">On the phone (or other Windows device) you prepared on the previous page, pair to the Bluetooth device on your Arduino in the Bluetooth settings.</span></span> <span data-ttu-id="838ae-195">기본 pin 코드를 BlueSMiRF를 사용 하는 경우 1234입니다.</span><span class="sxs-lookup"><span data-stu-id="838ae-195">If you're using the BlueSMiRF, the default pin code is 1234.</span></span> 

> [!NOTE]
> <span data-ttu-id="838ae-196">깜박이 빨간색 표시등은 BlueSMiRF 빨간색으로 성공한 연결 후 깜박임 계속 합니다.</span><span class="sxs-lookup"><span data-stu-id="838ae-196">The red blinking light on the BlueSMiRF continues to blink red after a successful pairing.</span></span> <span data-ttu-id="838ae-197">이는 예정된 동작입니다.</span><span class="sxs-lookup"><span data-stu-id="838ae-197">This is expected.</span></span> <span data-ttu-id="838ae-198">만 하면 녹색으로 Arduino 응용 프로그램에 대 한 Windows 가상 Shields를 사용 하 여 연결한 후 합니다.</span><span class="sxs-lookup"><span data-stu-id="838ae-198">It only turns green after a connecting with the Windows Virtual Shields for Arduino application.</span></span>


## <a name="3-write-your-first-app-hello-blinky"></a><span data-ttu-id="838ae-199">3. 첫 번째 앱을 작성 합니다. Hello, 쳐다!</span><span class="sxs-lookup"><span data-stu-id="838ae-199">3. Write your first app: Hello, Blinky!</span></span> 

### <a name="hello-world-speech-enabled-led-example"></a><span data-ttu-id="838ae-200">Hello World 음성 지원 LED 예제</span><span class="sxs-lookup"><span data-stu-id="838ae-200">Hello World speech-enabled LED example</span></span>
<span data-ttu-id="838ae-201">Windows Phone 사용자 (또는 잠재적으로 모든 Windows 10 장치!)를 사용 하 여이 자습서의 이전 단계에서 설명한 대로 준비 하 여 Arduino, 이제 샘플을 시도 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="838ae-201">With your Windows Phone (or potentially any Windows 10 device!) and your Arduino prepared as detailed in the previous steps of this tutorial, you're now ready to try our sample.</span></span>

1. <span data-ttu-id="838ae-202">핀 8 저항기를 사용 하 여 LED를 연결 하 여 Arduino 보드를 준비 합니다.</span><span class="sxs-lookup"><span data-stu-id="838ae-202">Prepare your Arduino board by hooking up an LED with a resistor to pin 8.</span></span>
2. <span data-ttu-id="838ae-203">에 Arduino 이벤트-음성-HelloWorld 샘플을 계속 업로드 되는 있는지 확인 하 고는 Arduino 전원 공급 장치를 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="838ae-203">Make sure that your Arduino is still uploaded with the HelloWorld-Speech-Eventing sample, and then plug the Arduino into a power supply.</span></span>
3. <span data-ttu-id="838ae-204">이전에 준비한 Windows Phone Arduino 앱에 대 한 Windows 가상 Shields를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="838ae-204">Run the Windows Virtual Shields for Arduino app on the Windows Phone you prepared previously.</span></span>
4. <span data-ttu-id="838ae-205">모든 설치 되었으면 제대로, 휴대폰 사용자가 Arduino 스케치를 연결할를 업데이트 하 고 있습니다에서 오디오 큐를 사용 하 여 시작 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="838ae-205">If everything has been setup properly, your phone should connect to your Arduino sketch and welcome you with an audio cue.</span></span> <span data-ttu-id="838ae-206">간을 전환 하 여 Arduino의 LED 켜고 Windows 10 장치에 'on' 또는 'f'를 말할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="838ae-206">You can now say 'on' or 'off' to your Windows 10 device to switch the LED on your Arduino between on and off!</span></span>

### <a name="arduino-wiring-sketch-hello-world-example"></a><span data-ttu-id="838ae-207">Arduino 스케치를 연결 합니다. Hello World 예제</span><span class="sxs-lookup"><span data-stu-id="838ae-207">Arduino Wiring Sketch: Hello World example</span></span>

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


