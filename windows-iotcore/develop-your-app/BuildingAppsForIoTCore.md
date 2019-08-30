---
title: 포그라운드 응용 프로그램 개발
author: msalehmsft
ms.author: msaleh
ms.date: 08/28/2017
ms.topic: article
description: IoT Core에서 지 원하는 언어 및 앱 유형에 대해 알아봅니다.
keywords: windows iot, 언어, 앱 유형, UWP, 지원 됨
ms.openlocfilehash: e0eb046ba874e8433e7632d3f88a63a90b88fa2b
ms.sourcegitcommit: 8a197111b5b7814b924d77dfea5f9d38760d4288
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/08/2019
ms.locfileid: "67627398"
---
# <a name="developing-foreground-applications"></a><span data-ttu-id="562ba-104">포그라운드 응용 프로그램 개발</span><span class="sxs-lookup"><span data-stu-id="562ba-104">Developing foreground applications</span></span>
<span data-ttu-id="562ba-105">Windows 10 IoT Core에서 지원 되는 언어와 IoT Core에서 지원 되는 UWP 및 비 UWP 앱 형식에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="562ba-105">Learn about the languages that are supported on Windows 10 IoT Core as well as the UWP and non-UWP app types that are supported on IoT Core.</span></span>


> [!NOTE]
> <span data-ttu-id="562ba-106">Visual Studio에서 액세스할 수 있는 RS4 이상의 SDK를 설치하지 않으면 RS5(또는 OpenSSH를 사용하는 RS4) IoT 이미지에 배포할 때 Visual Studio가 암호화 오류를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="562ba-106">Visual Studio will generate a cryptic error when deploying to a RS5 (or RS4 with OpenSSH enabled) IoT image unless a SDK from RS4 or greater is installed that Visual Studio can access.</span></span>

## <a name="application-types"></a><span data-ttu-id="562ba-107">응용 프로그램 종류</span><span class="sxs-lookup"><span data-stu-id="562ba-107">Application Types</span></span>
___

### <a name="universal-windows-platform-uwp-apps"></a><span data-ttu-id="562ba-108">UWP (유니버설 Windows 플랫폼) 앱</span><span class="sxs-lookup"><span data-stu-id="562ba-108">Universal Windows Platform (UWP) Apps</span></span>
<span data-ttu-id="562ba-109">IoT Core는 UWP 중심 OS 이며 UWP 앱은 기본 앱 유형입니다.</span><span class="sxs-lookup"><span data-stu-id="562ba-109">IoT Core is a UWP centric OS and UWP apps are its primary app type.</span></span>

<span data-ttu-id="562ba-110">UWP (유니버설 Windows 플랫폼)는 Windows 10 IoT Core를 포함 하 여 모든 버전의 Windows 10에서 일반적인 앱 플랫폼입니다.</span><span class="sxs-lookup"><span data-stu-id="562ba-110">Universal Windows Platform (UWP) is a common app platform across all version of Windows 10, including Windows 10 IoT Core.</span></span>  <span data-ttu-id="562ba-111">UWP는 WinRT (Windows 런타임)의 진화입니다.</span><span class="sxs-lookup"><span data-stu-id="562ba-111">UWP is an evolution of Windows Runtime (WinRT).</span></span> <span data-ttu-id="562ba-112">[여기](https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide)에서 UWP에 대 한 자세한 내용 및 개요를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="562ba-112">You can find more information and an overview to UWP [here](https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide).</span></span>

<span data-ttu-id="562ba-113">Visual Studio는 IoT Core 용 UWP 앱을 작성 하 고 일반적으로 사용할 수 있는 기본 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="562ba-113">Visual Studio is the primary tool for writing UWP apps for IoT Core and in general.</span></span> <span data-ttu-id="562ba-114">Visual Studio에 대 한 호환성 요구 사항에 대 한 자세한 목록은 [여기](https://docs.microsoft.com/visualstudio/productinfo/vs2017-compatibility-vs)에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="562ba-114">You can find a detailed listing of the compatibility requirements for Visual Studio [here](https://docs.microsoft.com/visualstudio/productinfo/vs2017-compatibility-vs).</span></span>


### <a name="traditional-uwp-apps"></a><span data-ttu-id="562ba-115">기존 UWP 앱</span><span class="sxs-lookup"><span data-stu-id="562ba-115">Traditional UWP Apps</span></span>
<span data-ttu-id="562ba-116">UWP 앱은 다른 Windows 10 버전과 마찬가지로 IoT Core에서 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="562ba-116">UWP apps just work on IoT Core, just as they do on other Windows 10 editions.</span></span> <span data-ttu-id="562ba-117">Visual Studio의 간단한 빈 Xaml 앱은 휴대폰 또는 Windows 10 PC에서와 마찬가지로 IoT Core 장치에 제대로 배포 됩니다.</span><span class="sxs-lookup"><span data-stu-id="562ba-117">A simple, blank Xaml app in Visual Studio will properly deploy to your IoT Core device just as it would on a phone or Windows 10 PC.</span></span> <span data-ttu-id="562ba-118">모든 표준 UWP 언어 및 프로젝트 템플릿은 IoT Core에서 완벽 하 게 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="562ba-118">All of the standard UWP languages and project templates are fully supported on IoT Core.</span></span>

<span data-ttu-id="562ba-119">IoT 시나리오를 지원 하기 위해 기존 UWP 앱 모델에 몇 가지 추가 사항이 있으며이를 활용 하는 모든 UWP 앱에는 매니페스트에 추가 된 해당 정보가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="562ba-119">There are a few additions to the traditional UWP app-model to support IoT scenarios and any UWP app that takes advantage of them will need the corresponding information added to their manifest.</span></span> <span data-ttu-id="562ba-120">특히 "iot" 네임 스페이스를 이러한 표준 UWP 앱의 매니페스트에 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="562ba-120">In particular the "iot" namespace needs to be added to the manifest of these standard UWP apps.</span></span> 

<span data-ttu-id="562ba-121"><Package> 매니페스트의 특성 내에서 iot xmlns를 정의 하 고 IgnorableNamespaces 목록에 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="562ba-121">Inside the <Package> attribute of the manifest, you need to define the iot xmlns and add it to the IgnorableNamespaces list.</span></span> <span data-ttu-id="562ba-122">최종 xml은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="562ba-122">The final xml should look like this:</span></span> 

```
<Package
  xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
  xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
  xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
  xmlns:iot="http://schemas.microsoft.com/appx/manifest/iot/windows10"
  IgnorableNamespaces="uap mp iot">
```

### <a name="background-apps"></a><span data-ttu-id="562ba-123">배경 앱</span><span class="sxs-lookup"><span data-stu-id="562ba-123">Background Apps</span></span>
<span data-ttu-id="562ba-124">기존 UI 앱 외에도 IoT Core에는 "백그라운드 응용 프로그램" 이라는 새로운 UWP 앱 유형이 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="562ba-124">In addition to the traditional UI apps, IoT Core has added a new UWP app type called "Background Applications".</span></span> <span data-ttu-id="562ba-125">이러한 응용 프로그램에는 UI 구성 요소가 없지만 대신 "IBackgroundTask" 인터페이스를 구현 하는 클래스가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="562ba-125">These applications do not have a UI component, but instead have a class that implements the "IBackgroundTask" interface.</span></span> <span data-ttu-id="562ba-126">그런 다음 해당 클래스를 시스템 부팅 시 실행할 "StartupTask"로 등록 합니다.</span><span class="sxs-lookup"><span data-stu-id="562ba-126">They then register that class as a "StartupTask" to run at system boot.</span></span> <span data-ttu-id="562ba-127">이러한 앱은 여전히 UWP 앱 이므로 동일한 Api 집합에 액세스할 수 있으며 동일한 언어로 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="562ba-127">Since they are still UWP apps, they have access to the same set of APIs and are supported from the same language.</span></span> <span data-ttu-id="562ba-128">유일한 차이점은 UI 진입점이 없다는 점입니다.</span><span class="sxs-lookup"><span data-stu-id="562ba-128">The only difference is that there is no UI entry point.</span></span>

<span data-ttu-id="562ba-129">각 유형의 IBackgroundTask는 자체 리소스 정책을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="562ba-129">Each type of IBackgroundTask gets its own resource policy.</span></span> <span data-ttu-id="562ba-130">일반적으로 이러한 백그라운드 앱이 포그라운드 UI 앱의 보조 구성 요소인 장치에서 배터리 수명 및 컴퓨터 리소스를 개선 하는 것이 제한적입니다.</span><span class="sxs-lookup"><span data-stu-id="562ba-130">This is usually restrictive to improve battery life and machine resources on devices where these background apps are secondary components of foreground UI apps.</span></span> <span data-ttu-id="562ba-131">IoT 장치에서 백그라운드 앱은 종종 장치의 기본 기능 이므로 이러한 StartupTasks는 다른 장치에서 포그라운드 UI 앱을 미러링 하는 리소스 정책을 받게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="562ba-131">On IoT devices, Background Apps are often the primary function of the device and so these StartupTasks get a resource policy that mirrors foreground UI apps on other devices.</span></span>

<span data-ttu-id="562ba-132">다음 샘플에서는 LED를 깜박이는 C# 백그라운드 앱을 빌드하는 데 필요한 코드를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="562ba-132">The following sample shows the code necessary to build a C# Background App that blinks an LED:</span></span>

```C#
namespace BlinkyHeadlessCS
{
    public sealed class StartupTask : IBackgroundTask
    {
        BackgroundTaskDeferral deferral;
        private GpioPinValue value = GpioPinValue.High;
        private const int LED_PIN = 5;
        private GpioPin pin;
        private ThreadPoolTimer timer;

        public void Run(IBackgroundTaskInstance taskInstance)        {
            deferral = taskInstance.GetDeferral();
            InitGPIO();
            timer = ThreadPoolTimer.CreatePeriodicTimer(Timer_Tick, TimeSpan.FromMilliseconds(500));

        }
        private void InitGPIO()
        {
            pin = GpioController.GetDefault().OpenPin(LED_PIN);
            pin.Write(GpioPinValue.High);
            pin.SetDriveMode(GpioPinDriveMode.Output);
        }

        private void Timer_Tick(ThreadPoolTimer timer)
        {
            value = (value == GpioPinValue.High) ? GpioPinValue.Low : GpioPinValue.High;
            pin.Write(value);
        }
    }
}
```

<span data-ttu-id="562ba-133">백그라운드 앱에 대 한 자세한 정보는 [여기](https://docs.microsoft.com/windows/iot-core/develop-your-app/backgroundapplications)에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="562ba-133">You can find in-depth information on Background apps [here](https://docs.microsoft.com/windows/iot-core/develop-your-app/backgroundapplications).</span></span>

### <a name="non-uwp-apps"></a><span data-ttu-id="562ba-134">비 UWP 앱</span><span class="sxs-lookup"><span data-stu-id="562ba-134">Non-UWP Apps</span></span>
<span data-ttu-id="562ba-135">IoT Core는 Win32 콘솔 앱 및 NT 서비스와 같은 특정 기존 Win32 앱 유형을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="562ba-135">IoT Core supports certain traditional Win32 app types such as Win32 Console Apps and NT Services.</span></span> <span data-ttu-id="562ba-136">이러한 앱은 Windows 10 Desktop과 동일한 방식으로 빌드되고 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="562ba-136">These apps are built and run the same way as on Windows 10 Desktop.</span></span> <span data-ttu-id="562ba-137">또한 Visual Studio를 사용 하 여 C++ 이러한 앱을 쉽게 빌드할 수 있도록 하는 IoT Core 콘솔 프로젝트 템플릿이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="562ba-137">Additionally, there is an IoT Core C++ Console project template to make it easy to build such apps using Visual Studio.</span></span>

<span data-ttu-id="562ba-138">이러한 비 UWP 응용 프로그램에는 두 가지 주요 제한 사항이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="562ba-138">There are two main limitations on these non-UWP applications:</span></span>
1. <span data-ttu-id="562ba-139">*레거시 Win32 UI 지원 안 함:* IoT Core에는 클래식 (HWND) 창을 만들기 위한 Api가 포함 되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="562ba-139">*No legacy Win32 UI support:* IoT Core does not contain APIs to create classic (HWND) Windows.</span></span> <span data-ttu-id="562ba-140">CreateWindow () 및 CreateWindowEx ()와 같은 레거시 메서드 또는 Windows 핸들 (Hwnd)을 처리 하는 다른 메서드는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="562ba-140">Legacy methods such as CreateWindow() and CreateWindowEx() or any other methods that deal with Windows handles (HWNDs) are not available.</span></span> <span data-ttu-id="562ba-141">이후에 MFC, Windows Forms 및 WPF를 포함 하 여 이러한 Api에 의존 하는 프레임 워크는 IoT Core에서 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="562ba-141">Subsequently, frameworks that depend on such APIs including MFC, Windows Forms and WPF, are not supported on IoT Core</span></span>
2. <span data-ttu-id="562ba-142">*C++앱에만 해당:* 현재는 IoT C++ Core에서 Win32 앱을 개발 하는 데만 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="562ba-142">*C++ Apps Only:* Currently, only C++ is supported for developing Win32 apps on IoT Core.</span></span>

## <a name="programming-languages"></a><span data-ttu-id="562ba-143">프로그래밍 언어</span><span class="sxs-lookup"><span data-stu-id="562ba-143">Programming Languages</span></span>
___

<span data-ttu-id="562ba-144">IoT Core는 다양 한 프로그래밍 언어를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="562ba-144">IoT Core supports a wide range of programming languages.</span></span>

### <a name="in-box-languages"></a><span data-ttu-id="562ba-145">기본 언어</span><span class="sxs-lookup"><span data-stu-id="562ba-145">In-Box languages</span></span>
<span data-ttu-id="562ba-146">기존 UWP 언어는 기본적으로 Visual Studio에 대 한 지원과 함께 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="562ba-146">Traditional UWP languages ship with support in Visual Studio by default.</span></span> <span data-ttu-id="562ba-147">모든 기본 제공 언어는 UI 및 백그라운드 응용 프로그램을 모두 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="562ba-147">All of the In-Box languages support both UI and Background Applications</span></span>
 
* <span data-ttu-id="562ba-148">언어</span><span class="sxs-lookup"><span data-stu-id="562ba-148">Languages</span></span>
  * <span data-ttu-id="562ba-149">C#</span><span class="sxs-lookup"><span data-stu-id="562ba-149">C#</span></span>
  * <span data-ttu-id="562ba-150">C++</span><span class="sxs-lookup"><span data-stu-id="562ba-150">C++</span></span>
  * <span data-ttu-id="562ba-151">Javascript</span><span class="sxs-lookup"><span data-stu-id="562ba-151">Javascript</span></span>
  * <span data-ttu-id="562ba-152">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="562ba-152">Visual Basic</span></span>

### <a name="arduino-wiring"></a><span data-ttu-id="562ba-153">Arduino 배선</span><span class="sxs-lookup"><span data-stu-id="562ba-153">Arduino Wiring</span></span>
 <span data-ttu-id="562ba-154">Arduino 와이어링을 사용 하려면 Visual Studio **도구-> 확장 및 업데이트** 관리자에서 "Windows IoT Core 프로젝트 템플릿"을 다운로드 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="562ba-154">Arduino Wiring requires the download of the "Windows IoT Core Project Templates" from the Visual Studio **Tools->Extensions and Updates** manager.</span></span>  <span data-ttu-id="562ba-155">Arduino 유선은 백그라운드 응용 프로그램만 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="562ba-155">Arduino Wiring supports only Background Applications.</span></span> <span data-ttu-id="562ba-156">, 또는 Visual Basic를 C++사용 하 여 C# *Windows 런타임 구성 요소* 를 빌드한 다음 다른 언어에서 해당 라이브러리를 참조할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="562ba-156">You can also build *Windows Runtime Components* using C#, C++, or Visual Basic and then reference those libraries from any other language.</span></span>

### <a name="c-and-visual-basic-vb"></a><span data-ttu-id="562ba-157">C#및 Visual Basic (VB)</span><span class="sxs-lookup"><span data-stu-id="562ba-157">C# and Visual Basic (VB)</span></span>
<span data-ttu-id="562ba-158">C#및 VB는 모두 UWP 앱으로 지원 되며 UWP 응용 프로그램에서 사용할 수 있는 .Net Framework 부분에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="562ba-158">C# and VB are both supported as UWP apps and have access to the portion of the .Net Framework available to UWP applications.</span></span> <span data-ttu-id="562ba-159">백그라운드 앱 뿐만 아니라 Xaml로 빌드된 UI 앱도 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="562ba-159">They support UI apps built with Xaml as well as Background Apps.</span></span> <span data-ttu-id="562ba-160">다른 지원 되는 언어에서 사용할 수 있는 *Windows 런타임 구성 요소* 를 작성할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="562ba-160">You can also build *Windows Runtime Components* that can be used from other supported languages.</span></span>

<span data-ttu-id="562ba-161">표본의</span><span class="sxs-lookup"><span data-stu-id="562ba-161">Samples:</span></span>


* [<span data-ttu-id="562ba-162">C#Blinky 헤드리스</span><span class="sxs-lookup"><span data-stu-id="562ba-162">C# Blinky Headless</span></span>](https://github.com/microsoft/Windows-iotcore-samples/tree/develop/Samples/HelloBlinkyBackground/CS)
* [<span data-ttu-id="562ba-163">VB Blinky 헤드리스</span><span class="sxs-lookup"><span data-stu-id="562ba-163">VB Blinky Headless</span></span>](https://github.com/microsoft/Windows-iotcore-samples/tree/develop/Samples/HelloBlinkyBackground/VB)
* [<span data-ttu-id="562ba-164">C#Blinky UI 앱</span><span class="sxs-lookup"><span data-stu-id="562ba-164">C# Blinky UI App</span></span>](https://github.com/microsoft/Windows-iotcore-samples/tree/develop/Samples/HelloBlinky/CS)


### <a name="javascript"></a><span data-ttu-id="562ba-165">Javascript</span><span class="sxs-lookup"><span data-stu-id="562ba-165">Javascript</span></span>
<span data-ttu-id="562ba-166">Javascript를 사용 하 여 UI 및 백그라운드 앱을 빌드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="562ba-166">You can use Javascript to build both UI and Background Apps.</span></span> <span data-ttu-id="562ba-167">UI 앱은 모든 UWP 버전에서 수행 하는 것과 동일한 방식으로 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="562ba-167">The UI apps work the same way they do on all UWP editions.</span></span> <span data-ttu-id="562ba-168">백그라운드 앱은 IoT Core의 새로운 새 것 이지만 매우 간단 합니다.</span><span class="sxs-lookup"><span data-stu-id="562ba-168">The Background Apps are new for IoT Core but are very simple.</span></span> <span data-ttu-id="562ba-169">다음 샘플 코드는 *JS 새 프로젝트 템플릿의*출력을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="562ba-169">The following sample code shows the output of a the *JS New Project Template*:</span></span>

```javascript
// The Background Application template is documented at http://go.microsoft.com/fwlink/?LinkID=533884&clcid=0x409
(function () {
    "use strict";

    // TODO: Insert code here for the startup task

})();
```

### <a name="c"></a><span data-ttu-id="562ba-170">C++</span><span class="sxs-lookup"><span data-stu-id="562ba-170">C++</span></span>
<span data-ttu-id="562ba-171">를 C++ 사용 하 여 Xaml 또는 DirectX UI 앱 뿐만 아니라 UWP 배경 프로젝트 및 *비 UI* Win32 앱을 빌드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="562ba-171">With C++ you can build Xaml or DirectX UI apps, as well as UWP Background projects and *non-UI* Win32 apps.</span></span>

<span data-ttu-id="562ba-172">표본의</span><span class="sxs-lookup"><span data-stu-id="562ba-172">Samples:</span></span>

* [<span data-ttu-id="562ba-173">Blinky 헤드리스</span><span class="sxs-lookup"><span data-stu-id="562ba-173">Blinky Headless</span></span>](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/HelloBlinkyBackground/CPP)
* [<span data-ttu-id="562ba-174">Blinky 화살표</span><span class="sxs-lookup"><span data-stu-id="562ba-174">Blinky Headed</span></span>](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/HelloBlinky/Cpp)
* [<span data-ttu-id="562ba-175">콘솔 앱</span><span class="sxs-lookup"><span data-stu-id="562ba-175">Console App</span></span>](https://github.com/microsoft/Windows-iotcore-samples/tree/develop/Samples/MemoryStatus/CPP)

> [!NOTE]
> <span data-ttu-id="562ba-176">에서 C++해당 앱을 작성할 계획인 경우 다운로드할 때 UWP C++ 확인란을 선택 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="562ba-176">For those who are planning to write their app in C++, you'll need to check the UWP C++ checkbox upon downloading.</span></span>

![C++Visual Studio의 경우](../media/BuildingAppsForIoTCore/VS-CPP.jpg)


### <a name="arduino-wiring"></a><span data-ttu-id="562ba-178">Arduino 배선</span><span class="sxs-lookup"><span data-stu-id="562ba-178">Arduino Wiring</span></span>
<span data-ttu-id="562ba-179">Arduino 배선 지원을 통해 IoT 에코 시스템에서 널리 사용 되는 다양 한 구성 요소 및 주변 장치에 대 한 Arduino 와이어링으로 앱을 빌드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="562ba-179">With Arduino Wiring support you can build apps in Arduino Wiring for many popular components and peripherals in the IoT ecosystem.</span></span>

<span data-ttu-id="562ba-180">[Arduino 배선 프로젝트 가이드](../learn-about-hardware/ArduinoWiringProjectGuide.md) 에서는 이러한 앱을 빌드하기 위해 설정 하는 방법에 대 한 자세한 지침을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="562ba-180">Our [Arduino Wiring Project Guide](../learn-about-hardware/ArduinoWiringProjectGuide.md) provides full instructions on how to get set up to build these apps.</span></span> <span data-ttu-id="562ba-181">아래에서 복사 하 여 링크 한 샘플을 통해 직접 빌드를 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="562ba-181">The samples copied and linked below will help you get started building your own.</span></span>  <span data-ttu-id="562ba-182">다른 언어에서 사용할 수 있는 [Arduino에서 WinRT 구성 요소를 빌드할](https://github.com/ms-iot/samples/tree/develop/ArduinoLibraryBlinky) 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="562ba-182">You can even [build WinRT components in Arduino](https://github.com/ms-iot/samples/tree/develop/ArduinoLibraryBlinky) that can then be used from other languages.</span></span> 

<span data-ttu-id="562ba-183">*Blinky 샘플 코드* 전체 [샘플 코드와 문서](https://github.com/ms-iot/samples/tree/develop/ArduinoLibraryBlinky) 는 샘플 페이지에서 사용할 수 있으며 아래 전체 코드를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="562ba-183">*Blinky Sample Code* The full [sample code and docs](https://github.com/ms-iot/samples/tree/develop/ArduinoLibraryBlinky) are available on our samples page and you can find the full code below:</span></span>

```C++
void setup()
{
    // put your setup code here, to run once:

    pinMode(GPIO5, OUTPUT);
}

void loop()
{
    // put your main code here, to run repeatedly:

    digitalWrite(GPIO5, LOW);
    delay(500);
    digitalWrite(GPIO5, HIGH);
    delay(500);
}
```
