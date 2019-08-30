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
# <a name="developing-foreground-applications"></a>포그라운드 응용 프로그램 개발
Windows 10 IoT Core에서 지원 되는 언어와 IoT Core에서 지원 되는 UWP 및 비 UWP 앱 형식에 대해 알아봅니다.


> [!NOTE]
> Visual Studio에서 액세스할 수 있는 RS4 이상의 SDK를 설치하지 않으면 RS5(또는 OpenSSH를 사용하는 RS4) IoT 이미지에 배포할 때 Visual Studio가 암호화 오류를 생성합니다.

## <a name="application-types"></a>응용 프로그램 종류
___

### <a name="universal-windows-platform-uwp-apps"></a>UWP (유니버설 Windows 플랫폼) 앱
IoT Core는 UWP 중심 OS 이며 UWP 앱은 기본 앱 유형입니다.

UWP (유니버설 Windows 플랫폼)는 Windows 10 IoT Core를 포함 하 여 모든 버전의 Windows 10에서 일반적인 앱 플랫폼입니다.  UWP는 WinRT (Windows 런타임)의 진화입니다. [여기](https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide)에서 UWP에 대 한 자세한 내용 및 개요를 확인할 수 있습니다.

Visual Studio는 IoT Core 용 UWP 앱을 작성 하 고 일반적으로 사용할 수 있는 기본 도구입니다. Visual Studio에 대 한 호환성 요구 사항에 대 한 자세한 목록은 [여기](https://docs.microsoft.com/visualstudio/productinfo/vs2017-compatibility-vs)에서 찾을 수 있습니다.


### <a name="traditional-uwp-apps"></a>기존 UWP 앱
UWP 앱은 다른 Windows 10 버전과 마찬가지로 IoT Core에서 작동 합니다. Visual Studio의 간단한 빈 Xaml 앱은 휴대폰 또는 Windows 10 PC에서와 마찬가지로 IoT Core 장치에 제대로 배포 됩니다. 모든 표준 UWP 언어 및 프로젝트 템플릿은 IoT Core에서 완벽 하 게 지원 됩니다.

IoT 시나리오를 지원 하기 위해 기존 UWP 앱 모델에 몇 가지 추가 사항이 있으며이를 활용 하는 모든 UWP 앱에는 매니페스트에 추가 된 해당 정보가 필요 합니다. 특히 "iot" 네임 스페이스를 이러한 표준 UWP 앱의 매니페스트에 추가 해야 합니다. 

<Package> 매니페스트의 특성 내에서 iot xmlns를 정의 하 고 IgnorableNamespaces 목록에 추가 해야 합니다. 최종 xml은 다음과 같습니다. 

```
<Package
  xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
  xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
  xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
  xmlns:iot="http://schemas.microsoft.com/appx/manifest/iot/windows10"
  IgnorableNamespaces="uap mp iot">
```

### <a name="background-apps"></a>배경 앱
기존 UI 앱 외에도 IoT Core에는 "백그라운드 응용 프로그램" 이라는 새로운 UWP 앱 유형이 추가 되었습니다. 이러한 응용 프로그램에는 UI 구성 요소가 없지만 대신 "IBackgroundTask" 인터페이스를 구현 하는 클래스가 있습니다. 그런 다음 해당 클래스를 시스템 부팅 시 실행할 "StartupTask"로 등록 합니다. 이러한 앱은 여전히 UWP 앱 이므로 동일한 Api 집합에 액세스할 수 있으며 동일한 언어로 지원 됩니다. 유일한 차이점은 UI 진입점이 없다는 점입니다.

각 유형의 IBackgroundTask는 자체 리소스 정책을 가져옵니다. 일반적으로 이러한 백그라운드 앱이 포그라운드 UI 앱의 보조 구성 요소인 장치에서 배터리 수명 및 컴퓨터 리소스를 개선 하는 것이 제한적입니다. IoT 장치에서 백그라운드 앱은 종종 장치의 기본 기능 이므로 이러한 StartupTasks는 다른 장치에서 포그라운드 UI 앱을 미러링 하는 리소스 정책을 받게 됩니다.

다음 샘플에서는 LED를 깜박이는 C# 백그라운드 앱을 빌드하는 데 필요한 코드를 보여 줍니다.

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

백그라운드 앱에 대 한 자세한 정보는 [여기](https://docs.microsoft.com/windows/iot-core/develop-your-app/backgroundapplications)에서 확인할 수 있습니다.

### <a name="non-uwp-apps"></a>비 UWP 앱
IoT Core는 Win32 콘솔 앱 및 NT 서비스와 같은 특정 기존 Win32 앱 유형을 지원 합니다. 이러한 앱은 Windows 10 Desktop과 동일한 방식으로 빌드되고 실행 됩니다. 또한 Visual Studio를 사용 하 여 C++ 이러한 앱을 쉽게 빌드할 수 있도록 하는 IoT Core 콘솔 프로젝트 템플릿이 있습니다.

이러한 비 UWP 응용 프로그램에는 두 가지 주요 제한 사항이 있습니다.
1. *레거시 Win32 UI 지원 안 함:* IoT Core에는 클래식 (HWND) 창을 만들기 위한 Api가 포함 되어 있지 않습니다. CreateWindow () 및 CreateWindowEx ()와 같은 레거시 메서드 또는 Windows 핸들 (Hwnd)을 처리 하는 다른 메서드는 사용할 수 없습니다. 이후에 MFC, Windows Forms 및 WPF를 포함 하 여 이러한 Api에 의존 하는 프레임 워크는 IoT Core에서 지원 되지 않습니다.
2. *C++앱에만 해당:* 현재는 IoT C++ Core에서 Win32 앱을 개발 하는 데만 지원 됩니다.

## <a name="programming-languages"></a>프로그래밍 언어
___

IoT Core는 다양 한 프로그래밍 언어를 지원 합니다.

### <a name="in-box-languages"></a>기본 언어
기존 UWP 언어는 기본적으로 Visual Studio에 대 한 지원과 함께 제공 됩니다. 모든 기본 제공 언어는 UI 및 백그라운드 응용 프로그램을 모두 지원 합니다.
 
* 언어
  * C#
  * C++
  * Javascript
  * Visual Basic

### <a name="arduino-wiring"></a>Arduino 배선
 Arduino 와이어링을 사용 하려면 Visual Studio **도구-> 확장 및 업데이트** 관리자에서 "Windows IoT Core 프로젝트 템플릿"을 다운로드 해야 합니다.  Arduino 유선은 백그라운드 응용 프로그램만 지원 합니다. , 또는 Visual Basic를 C++사용 하 여 C# *Windows 런타임 구성 요소* 를 빌드한 다음 다른 언어에서 해당 라이브러리를 참조할 수도 있습니다.

### <a name="c-and-visual-basic-vb"></a>C#및 Visual Basic (VB)
C#및 VB는 모두 UWP 앱으로 지원 되며 UWP 응용 프로그램에서 사용할 수 있는 .Net Framework 부분에 액세스할 수 있습니다. 백그라운드 앱 뿐만 아니라 Xaml로 빌드된 UI 앱도 지원 합니다. 다른 지원 되는 언어에서 사용할 수 있는 *Windows 런타임 구성 요소* 를 작성할 수도 있습니다.

표본의


* [C#Blinky 헤드리스](https://github.com/microsoft/Windows-iotcore-samples/tree/develop/Samples/HelloBlinkyBackground/CS)
* [VB Blinky 헤드리스](https://github.com/microsoft/Windows-iotcore-samples/tree/develop/Samples/HelloBlinkyBackground/VB)
* [C#Blinky UI 앱](https://github.com/microsoft/Windows-iotcore-samples/tree/develop/Samples/HelloBlinky/CS)


### <a name="javascript"></a>Javascript
Javascript를 사용 하 여 UI 및 백그라운드 앱을 빌드할 수 있습니다. UI 앱은 모든 UWP 버전에서 수행 하는 것과 동일한 방식으로 작동 합니다. 백그라운드 앱은 IoT Core의 새로운 새 것 이지만 매우 간단 합니다. 다음 샘플 코드는 *JS 새 프로젝트 템플릿의*출력을 보여 줍니다.

```javascript
// The Background Application template is documented at http://go.microsoft.com/fwlink/?LinkID=533884&clcid=0x409
(function () {
    "use strict";

    // TODO: Insert code here for the startup task

})();
```

### <a name="c"></a>C++
를 C++ 사용 하 여 Xaml 또는 DirectX UI 앱 뿐만 아니라 UWP 배경 프로젝트 및 *비 UI* Win32 앱을 빌드할 수 있습니다.

표본의

* [Blinky 헤드리스](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/HelloBlinkyBackground/CPP)
* [Blinky 화살표](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/HelloBlinky/Cpp)
* [콘솔 앱](https://github.com/microsoft/Windows-iotcore-samples/tree/develop/Samples/MemoryStatus/CPP)

> [!NOTE]
> 에서 C++해당 앱을 작성할 계획인 경우 다운로드할 때 UWP C++ 확인란을 선택 해야 합니다.

![C++Visual Studio의 경우](../media/BuildingAppsForIoTCore/VS-CPP.jpg)


### <a name="arduino-wiring"></a>Arduino 배선
Arduino 배선 지원을 통해 IoT 에코 시스템에서 널리 사용 되는 다양 한 구성 요소 및 주변 장치에 대 한 Arduino 와이어링으로 앱을 빌드할 수 있습니다.

[Arduino 배선 프로젝트 가이드](../learn-about-hardware/ArduinoWiringProjectGuide.md) 에서는 이러한 앱을 빌드하기 위해 설정 하는 방법에 대 한 자세한 지침을 제공 합니다. 아래에서 복사 하 여 링크 한 샘플을 통해 직접 빌드를 시작할 수 있습니다.  다른 언어에서 사용할 수 있는 [Arduino에서 WinRT 구성 요소를 빌드할](https://github.com/ms-iot/samples/tree/develop/ArduinoLibraryBlinky) 수도 있습니다. 

*Blinky 샘플 코드* 전체 [샘플 코드와 문서](https://github.com/ms-iot/samples/tree/develop/ArduinoLibraryBlinky) 는 샘플 페이지에서 사용할 수 있으며 아래 전체 코드를 찾을 수 있습니다.

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
