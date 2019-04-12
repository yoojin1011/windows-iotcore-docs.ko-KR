---
title: Arduino 배선 프로젝트 가이드
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 만들기, 설정 및 Windows IoT Core를 사용 하 여 Arduino 연결 프로젝트의 배포에 알아봅니다.
keywords: windows iot에 Arduino, Arduino 연결, 번개 성능, Visual Studio
ms.openlocfilehash: baa904d1d5f23db15fd1dacd05c749449dc91213
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512870"
---
# <a name="arduino-wiring-project-guide"></a><span data-ttu-id="655a7-104">Arduino 배선 프로젝트 가이드</span><span class="sxs-lookup"><span data-stu-id="655a7-104">Arduino Wiring Project Guide</span></span>

<span data-ttu-id="655a7-105">이 가이드는 만들기, 설정 및 Windows IoT Core를 사용 하 여 Arduino 연결 프로젝트의 배포를 단계별로 안내 합니다.</span><span class="sxs-lookup"><span data-stu-id="655a7-105">This guide will walk through the creation, setup, and deployment of an Arduino Wiring project using Windows IoT Core.</span></span>

<span data-ttu-id="655a7-106">프로젝트 Arduino 연결, 친숙 하 고 사용 하기 쉬운 Arduino 연결 API 활용 Windows IoT 번개 DMAP 드라이버로: 중요 한 있도록 직접 메모리 매핑을 사용 하 여 드라이버 [성능 속도](../develop-your-app/LightningPerformance.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="655a7-106">Arduino Wiring projects utilize the familiar, easy to use Arduino Wiring API with Windows IoT Lightning DMAP driver: a driver using direct memory mapping to provide significant [performance speeds](../develop-your-app/LightningPerformance.md).</span></span> <span data-ttu-id="655a7-107">복사 하 & IoT Core Arduino 연결 프로젝트로 Arduino 스케치 및 라이브러리를 붙여, 3 및 Minnowboard Max Raspberry Pi2를 비롯 한 장치를 지원 되는 IoT Core에서 실행할 수 있습니다!</span><span class="sxs-lookup"><span data-stu-id="655a7-107">You can copy & paste Arduino sketches and libraries into your IoT Core Arduino Wiring projects and run them on supported IoT Core devices, including Raspberry Pi2, 3 and Minnowboard Max!</span></span> <span data-ttu-id="655a7-108">자세한 내용은이 페이지의 개발 섹션을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="655a7-108">See the develop section of this page for more information.</span></span>

## <a name="install-the-microsoft-iot-templates"></a><span data-ttu-id="655a7-109">Microsoft IoT 템플릿 설치</span><span class="sxs-lookup"><span data-stu-id="655a7-109">Install the Microsoft IoT Templates</span></span>

<span data-ttu-id="655a7-110">Arduino 연결 프로젝트 뿐만 아니라 다른 Microsoft IoT 프로젝트 형식에 대 한 VS 템플릿을 자동으로 설치 하는 Visual Studio 확장을 제공 했습니다.</span><span class="sxs-lookup"><span data-stu-id="655a7-110">We've provided a Visual Studio extension which will automatically install a VS template for the Arduino Wiring projects as well as other Microsoft IoT project types.</span></span> 

- <span data-ttu-id="655a7-111">로 이동 [Windows IoT Core 프로젝트 템플릿에 확장 페이지](https://go.microsoft.com/fwlink/?linkid=847472) Visual Studio 갤러리에서 확장을 다운로드 하려면!</span><span class="sxs-lookup"><span data-stu-id="655a7-111">Head over to [Windows IoT Core Project Templates extension page](https://go.microsoft.com/fwlink/?linkid=847472) to download the extension from the Visual Studio Gallery!</span></span>
- <span data-ttu-id="655a7-112">확장을 설치 하 고 이미 열려 있으면 Visual Studio를 다시 시작</span><span class="sxs-lookup"><span data-stu-id="655a7-112">Install the extension and restart Visual Studio if it was already open</span></span>

## <a name="change-the-default-controller-driver"></a><span data-ttu-id="655a7-113">기본 컨트롤러 드라이버 변경</span><span class="sxs-lookup"><span data-stu-id="655a7-113">Change the Default Controller Driver</span></span>

<span data-ttu-id="655a7-114">Arduino 연결 솔루션을 작성 하려면 직접 메모리 매핑된 드라이버가 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="655a7-114">You will need to be running the Direct Memory Mapped Driver to write Arduino Wiring solutions!</span></span> <span data-ttu-id="655a7-115">참조 된 [번개 설치 가이드](../develop-your-app/LightningSetup.md) 지침은!</span><span class="sxs-lookup"><span data-stu-id="655a7-115">Refer to the [Lightning Setup Guide](../develop-your-app/LightningSetup.md) for instructions!</span></span>

## <a name="develop"></a><span data-ttu-id="655a7-116">개발</span><span class="sxs-lookup"><span data-stu-id="655a7-116">Develop</span></span>
<span data-ttu-id="655a7-117">"연결" 샘플 중 하나를 완료 합니다 [샘플 페이지](https://developer.microsoft.com/en-us/windows/iot/samples), 고유한 프로젝트를 빌드하거나!</span><span class="sxs-lookup"><span data-stu-id="655a7-117">Complete one of the "Wiring" samples on the [Samples Page](https://developer.microsoft.com/en-us/windows/iot/samples), or build your own project!</span></span> <span data-ttu-id="655a7-118">나열 될 Arduino 연결을 사용 하 여 작성 된 샘플 만들었습니다 다음과 같이 합니다. [쳐다 (연결)](https://developer.microsoft.com/en-us/windows/iot/samples/helloblinkybackgroundwiring)합니다.</span><span class="sxs-lookup"><span data-stu-id="655a7-118">Any of the samples we've created that are written using Arduino Wiring will be listed like so: [Blinky (Wiring)](https://developer.microsoft.com/en-us/windows/iot/samples/helloblinkybackgroundwiring).</span></span> <span data-ttu-id="655a7-119">쳐다, IoT 프로젝트용 cononical "Hello World" 프로젝트가 되었습니다. 첫 번째 프로젝트에 대 한 시작 하기에 적합</span><span class="sxs-lookup"><span data-stu-id="655a7-119">Blinky, the cononical "Hello World" project for IoT projects, is a great place to start for your first project!</span></span>

### <a name="create-a-new-project"></a><span data-ttu-id="655a7-120">새 프로젝트 만들기</span><span class="sxs-lookup"><span data-stu-id="655a7-120">Create a new Project</span></span>
1. <span data-ttu-id="655a7-121">Visual Studio를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="655a7-121">Open Visual Studio.</span></span>

2. <span data-ttu-id="655a7-122">파일 선택-> 새로 만들기-> 프로젝트...</span><span class="sxs-lookup"><span data-stu-id="655a7-122">Select File -> New -> Project...</span></span>

3. <span data-ttu-id="655a7-123">나타나는 대화 상자에서 다음을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="655a7-123">From the dialogue that appears, choose:</span></span>  
<span data-ttu-id="655a7-124">Visual C++ -> Windows-Windows > IoT Core에 Windows IoT Core에 대 한 응용 프로그램을 연결 하는 Arduino-></span><span class="sxs-lookup"><span data-stu-id="655a7-124">Visual C++ -> Windows -> Windows IoT Core -> Arduino Wiring Application for Windows IoT Core</span></span>  
<span data-ttu-id="655a7-125">(대신 나타날으로)</span><span class="sxs-lookup"><span data-stu-id="655a7-125">(might appear instead as)</span></span>  
<span data-ttu-id="655a7-126">Visual C++ Windows-> IoT Core에 Windows IoT Core에 대 한 응용 프로그램을 연결 하는 Arduino-></span><span class="sxs-lookup"><span data-stu-id="655a7-126">Visual C++ -> Windows IoT Core -> Arduino Wiring Application for Windows IoT Core</span></span> 


![앱 만들기](../media/ArduinoWiring/appcreate.png)

### <a name="porting"></a><span data-ttu-id="655a7-128">포팅</span><span class="sxs-lookup"><span data-stu-id="655a7-128">Porting</span></span>

<span data-ttu-id="655a7-129">Arduino 연결 API로 복사/붙여넣기 라이브러리 및 스케치를 Arduino 연결 프로젝트로 수 있도록 신중 하 게 구현 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="655a7-129">The Arduino Wiring API has been carefully implemented to make it possible to copy/paste your libraries and sketches into an Arduino Wiring project.</span></span> <span data-ttu-id="655a7-130">그럼에도 불구 하 고,에 경우에 따라 약간의 수정을 스케치 나 라이브러리 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="655a7-130">Nevertheless there are, in some circumstances, slight modifications you may have to make to your sketches or libraries.</span></span> <span data-ttu-id="655a7-131">따라 하기 쉬운 만들었습니다 [Arduino 연결 포팅 가이드](ArduinoWiringPortingGuide.md) 이러한 잠재적인 문제를 처리 하기 위해.</span><span class="sxs-lookup"><span data-stu-id="655a7-131">We've created an easy to follow [Arduino Wiring Porting Guide](ArduinoWiringPortingGuide.md) to cover these potential issues.</span></span>

## <a name="build-and-deploy"></a><span data-ttu-id="655a7-132">빌드 및 배포</span><span class="sxs-lookup"><span data-stu-id="655a7-132">Build and Deploy</span></span>

- <span data-ttu-id="655a7-133">Visual Studio에서 "원격 컴퓨터가" 배포 대상으로 선택 되어 있는지를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="655a7-133">In Visual Studio, make sure "Remote Machine" is selected as your deployment target.</span></span>
- <span data-ttu-id="655a7-134">또한 아키텍처에서 프로젝트를 실행 하는 보드를 일치 하도록 설정 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="655a7-134">Also, make sure the  architecture is set to match the board you're running your project on.</span></span> <span data-ttu-id="655a7-135">Raspberry Pi 2 또는 3에 대 한 "ARM"를 선택 하 고 Minnowboard 최대 "x86"를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="655a7-135">For Raspberry Pi 2 or 3 choose "ARM" and for Minnowboard Max, choose "x86".</span></span>

![원격 컴퓨터](../media/ArduinoWiring/wiringapp_remotemachine.png)

- <span data-ttu-id="655a7-137">Visual Studio에서 디버그 상황에 맞는 메뉴에 있는 솔루션 속성을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="655a7-137">Open the solution properties found on the Debug context menu in Visual Studio.</span></span>

![솔루션 속성](../media/ArduinoWiring/wiringapp_properties.png)

- <span data-ttu-id="655a7-139">장치의 IP 주소 또는 컴퓨터 이름을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="655a7-139">locate the IP address or machine name of your device.</span></span> <span data-ttu-id="655a7-140">Windows 10 IoT Core 대시보드 응용 프로그램을 사용 하거나 모니터를 장치에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="655a7-140">Either use the Windows 10 IoT Core Dashboard application or hook up your device to a monitor.</span></span>
- <span data-ttu-id="655a7-141">'Machine name' 필드에 컴퓨터 이름 (기본적으로 minwinpc) 또는 원격 컴퓨터의 IP 주소를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="655a7-141">Type the machine name (minwinpc by default) or the IP address of the remote machine into the 'machine name' field.</span></span> <span data-ttu-id="655a7-142">변경한 경우 장치를 'minwinpc' 대신 해당 이름을 로그인 상자 외에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="655a7-142">If you have renamed your device to something besides 'minwinpc' use that name in the login box instead.</span></span>
- <span data-ttu-id="655a7-143">Authentican 형식이 확인 합니다. 유니버설 (암호화 되지 않은 프로토콜)</span><span class="sxs-lookup"><span data-stu-id="655a7-143">Ensure the Authentican Type is: Universal (Unencrypted Protocol)</span></span>

![솔루션 속성](../media/ArduinoWiring/wiringapp_properties2.png)

- <span data-ttu-id="655a7-145">F5 키를 눌러를 장치에서 프로젝트를 빌드하여 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="655a7-145">Press F5 to build and deploy your project on your device.</span></span>
