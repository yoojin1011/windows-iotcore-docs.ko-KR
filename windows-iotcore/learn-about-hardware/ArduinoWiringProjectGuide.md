---
title: Arduino 배선 프로젝트 가이드
ms.date: 08/28/2017
ms.topic: article
description: Windows IoT Core를 사용 하 여 Arduino 배선 프로젝트를 만들고, 설치 하 고, 배포 하는 방법에 대해 알아봅니다.
keywords: windows iot, Arduino, Arduino 배선, 라이트닝 성능, Visual Studio
ms.openlocfilehash: 17dc35174cc6aca7074183875e69202fc36dd9bc
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918114"
---
# <a name="arduino-wiring-project-guide"></a><span data-ttu-id="628ed-104">Arduino 배선 프로젝트 가이드</span><span class="sxs-lookup"><span data-stu-id="628ed-104">Arduino Wiring Project Guide</span></span>

> [!IMPORTANT]
> <span data-ttu-id="628ed-105">Windows 10 IoT 팀은 더 이상 Arduino를 적극적으로 유지 관리 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="628ed-105">The Windows 10 IoT team is no longer actively maintaining Arduino.</span></span>

<span data-ttu-id="628ed-106">이 가이드는 Windows IoT Core를 사용 하 여 Arduino 배선 프로젝트를 만들고, 설치 하 고, 배포 하는 과정을 안내 합니다.</span><span class="sxs-lookup"><span data-stu-id="628ed-106">This guide will walk through the creation, setup, and deployment of an Arduino Wiring project using Windows IoT Core.</span></span>

<span data-ttu-id="628ed-107">Arduino 배선 프로젝트는 친숙 하 고 사용 하기 쉬운 Arduino 배선 API를 사용 하 여 Windows IoT 번개 드라이버: 직접 메모리 매핑을 사용 하는 드라이버로 상당한 [성능 속도](../develop-your-app/LightningPerformance.md)를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="628ed-107">Arduino Wiring projects utilize the familiar, easy to use Arduino Wiring API with Windows IoT Lightning DMAP driver: a driver using direct memory mapping to provide significant [performance speeds](../develop-your-app/LightningPerformance.md).</span></span> <span data-ttu-id="628ed-108">Arduino 스케치 및 라이브러리를 복사 하 & IoT Core Arduino 배선 프로젝트에 붙여 넣고 Raspberry Pi2, 3 및 Minnowboard Max를 비롯 한 지원 되는 IoT Core 장치에서 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="628ed-108">You can copy & paste Arduino sketches and libraries into your IoT Core Arduino Wiring projects and run them on supported IoT Core devices, including Raspberry Pi2, 3 and Minnowboard Max!</span></span> <span data-ttu-id="628ed-109">자세한 내용은이 페이지의 개발 섹션을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="628ed-109">See the develop section of this page for more information.</span></span>

## <a name="install-the-microsoft-iot-templates"></a><span data-ttu-id="628ed-110">Microsoft IoT 템플릿 설치</span><span class="sxs-lookup"><span data-stu-id="628ed-110">Install the Microsoft IoT Templates</span></span>

> [!NOTE]
> <span data-ttu-id="628ed-111">VS 2015를 다운로드 하 여 Arduino 배선 템플릿에 액세스-이 템플릿은 VS 2017 이상에서 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="628ed-111">Download VS 2015 to access Arduino Wiring templates - these templates are no loner supported on VS 2017 and beyond.</span></span>

<span data-ttu-id="628ed-112">Arduino 배선 프로젝트 뿐만 아니라 다른 Microsoft IoT 프로젝트 형식에 대 한 VS 템플릿을 자동으로 설치 하는 Visual Studio 확장을 제공 했습니다.</span><span class="sxs-lookup"><span data-stu-id="628ed-112">We've provided a Visual Studio extension which will automatically install a VS template for the Arduino Wiring projects as well as other Microsoft IoT project types.</span></span> 

- <span data-ttu-id="628ed-113">[Windows IoT Core 프로젝트 템플릿 확장 페이지로](https://go.microsoft.com/fwlink/?linkid=847472) 이동 하 여 Visual Studio 갤러리에서 확장을 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="628ed-113">Head over to [Windows IoT Core Project Templates extension page](https://go.microsoft.com/fwlink/?linkid=847472) to download the extension from the Visual Studio Gallery!</span></span>
- <span data-ttu-id="628ed-114">확장을 설치 하 고 Visual Studio가 이미 열려 있는 경우 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="628ed-114">Install the extension and restart Visual Studio if it was already open</span></span>

## <a name="change-the-default-controller-driver"></a><span data-ttu-id="628ed-115">기본 컨트롤러 드라이버 변경</span><span class="sxs-lookup"><span data-stu-id="628ed-115">Change the Default Controller Driver</span></span>

<span data-ttu-id="628ed-116">Arduino 배선 솔루션을 쓰려면 직접 메모리 매핑된 드라이버를 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="628ed-116">You will need to be running the Direct Memory Mapped Driver to write Arduino Wiring solutions!</span></span> <span data-ttu-id="628ed-117">지침은 [번개 설정 가이드](../develop-your-app/LightningSetup.md) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="628ed-117">Refer to the [Lightning Setup Guide](../develop-your-app/LightningSetup.md) for instructions!</span></span>

## <a name="develop"></a><span data-ttu-id="628ed-118">개발</span><span class="sxs-lookup"><span data-stu-id="628ed-118">Develop</span></span>
<span data-ttu-id="628ed-119">[샘플 페이지](https://developer.microsoft.com/en-us/windows/iot/samples)의 "배선" 샘플 중 하나를 완료 하거나 고유한 프로젝트를 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="628ed-119">Complete one of the "Wiring" samples on the [Samples Page](https://developer.microsoft.com/en-us/windows/iot/samples), or build your own project!</span></span> <span data-ttu-id="628ed-120">Arduino 배선을 사용 하 여 작성 된 모든 샘플은 다음과 같이 표시 됩니다. [Blinky (배선)](https://developer.microsoft.com/en-us/windows/iot/samples/helloblinkybackgroundwiring).</span><span class="sxs-lookup"><span data-stu-id="628ed-120">Any of the samples we've created that are written using Arduino Wiring will be listed like so: [Blinky (Wiring)](https://developer.microsoft.com/en-us/windows/iot/samples/helloblinkybackgroundwiring).</span></span> <span data-ttu-id="628ed-121">Blinky, IoT 프로젝트용 cononical "Hello World" 프로젝트는 첫 번째 프로젝트를 시작할 수 있는 좋은 장소입니다.</span><span class="sxs-lookup"><span data-stu-id="628ed-121">Blinky, the cononical "Hello World" project for IoT projects, is a great place to start for your first project!</span></span>

### <a name="create-a-new-project"></a><span data-ttu-id="628ed-122">새 프로젝트 만들기</span><span class="sxs-lookup"><span data-stu-id="628ed-122">Create a new Project</span></span>
1. <span data-ttu-id="628ed-123">Visual Studio를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="628ed-123">Open Visual Studio.</span></span>

2. <span data-ttu-id="628ed-124">파일-> 새로 만들기-> 프로젝트 ...를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="628ed-124">Select File -> New -> Project...</span></span>

3. <span data-ttu-id="628ed-125">표시 되는 대화 상자에서 다음을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="628ed-125">From the dialogue that appears, choose:</span></span>  
<span data-ttu-id="628ed-126">Visual C++ > windows-Windows iot core > Windows iot core 용 > Arduino 배선 응용 프로그램</span><span class="sxs-lookup"><span data-stu-id="628ed-126">Visual C++ -> Windows -> Windows IoT Core -> Arduino Wiring Application for Windows IoT Core</span></span>  
<span data-ttu-id="628ed-127">(대신에 표시 될 수 있음)</span><span class="sxs-lookup"><span data-stu-id="628ed-127">(might appear instead as)</span></span>  
<span data-ttu-id="628ed-128">Visual C++ > Windows iot Core-Windows iot core 용 > Arduino 배선 응용 프로그램</span><span class="sxs-lookup"><span data-stu-id="628ed-128">Visual C++ -> Windows IoT Core -> Arduino Wiring Application for Windows IoT Core</span></span> 


![앱 만들기](../media/ArduinoWiring/appcreate.png)

### <a name="porting"></a><span data-ttu-id="628ed-130">포팅</span><span class="sxs-lookup"><span data-stu-id="628ed-130">Porting</span></span>

<span data-ttu-id="628ed-131">Arduino 배선 API는 라이브러리 및 스케치를 Arduino 배선 프로젝트에 복사 하 여 붙여 넣을 수 있도록 신중 하 게 구현 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="628ed-131">The Arduino Wiring API has been carefully implemented to make it possible to copy/paste your libraries and sketches into an Arduino Wiring project.</span></span> <span data-ttu-id="628ed-132">그럼에도 불구 하 고 일부 경우에는 스케치 또는 라이브러리에 대해 약간의 수정이 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="628ed-132">Nevertheless there are, in some circumstances, slight modifications you may have to make to your sketches or libraries.</span></span> <span data-ttu-id="628ed-133">이러한 잠재적인 문제를 다루기 위해 [Arduino 배선 포팅 가이드](ArduinoWiringPortingGuide.md) 를 쉽게 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="628ed-133">We've created an easy to follow [Arduino Wiring Porting Guide](ArduinoWiringPortingGuide.md) to cover these potential issues.</span></span>

## <a name="build-and-deploy"></a><span data-ttu-id="628ed-134">빌드 및 배포</span><span class="sxs-lookup"><span data-stu-id="628ed-134">Build and Deploy</span></span>

- <span data-ttu-id="628ed-135">Visual Studio에서 "원격 컴퓨터"가 배포 대상으로 선택 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="628ed-135">In Visual Studio, make sure "Remote Machine" is selected as your deployment target.</span></span>
- <span data-ttu-id="628ed-136">또한 프로젝트를 실행 하는 보드와 일치 하도록 아키텍처가 설정 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="628ed-136">Also, make sure the  architecture is set to match the board you're running your project on.</span></span> <span data-ttu-id="628ed-137">Raspberry Pi 2 또는 3의 경우 "ARM"을 선택 하 고 Minnowboard Max의 경우 "x86"을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="628ed-137">For Raspberry Pi 2 or 3 choose "ARM" and for Minnowboard Max, choose "x86".</span></span>

![원격 컴퓨터](../media/ArduinoWiring/wiringapp_remotemachine.png)

- <span data-ttu-id="628ed-139">Visual Studio의 디버그 상황에 맞는 메뉴에 있는 솔루션 속성을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="628ed-139">Open the solution properties found on the Debug context menu in Visual Studio.</span></span>

![솔루션 속성](../media/ArduinoWiring/wiringapp_properties.png)

- <span data-ttu-id="628ed-141">장치의 IP 주소 또는 컴퓨터 이름을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="628ed-141">locate the IP address or machine name of your device.</span></span> <span data-ttu-id="628ed-142">Windows 10 IoT Core 대시보드 응용 프로그램을 사용 하거나 장치를 모니터에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="628ed-142">Either use the Windows 10 IoT Core Dashboard application or hook up your device to a monitor.</span></span>
- <span data-ttu-id="628ed-143">컴퓨터 이름 (기본적으로 minwinpc) 또는 원격 컴퓨터의 IP 주소를 ' 컴퓨터 이름 ' 필드에 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="628ed-143">Type the machine name (minwinpc by default) or the IP address of the remote machine into the 'machine name' field.</span></span> <span data-ttu-id="628ed-144">' Minwinpc ' 이외의 이름으로 장치 이름을 변경한 경우 대신 로그인 상자에서 해당 이름을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="628ed-144">If you have renamed your device to something besides 'minwinpc' use that name in the login box instead.</span></span>
- <span data-ttu-id="628ed-145">Authentican 형식이 유니버설 (암호화 되지 않은 프로토콜) 인지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="628ed-145">Ensure the Authentican Type is: Universal (Unencrypted Protocol)</span></span>

![솔루션 속성](../media/ArduinoWiring/wiringapp_properties2.png)

- <span data-ttu-id="628ed-147">F5 키를 눌러 프로젝트를 빌드하고 장치에 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="628ed-147">Press F5 to build and deploy your project on your device.</span></span>
