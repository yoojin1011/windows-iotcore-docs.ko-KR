---
title: 백그라운드 응용 프로그램
ms.date: 08/28/2017
ms.topic: article
description: IoT 장치용 백그라운드 응용 프로그램을 개발 하는 방법을 알아봅니다.
keywords: windows iot, 백그라운드 응용 프로그램
ms.openlocfilehash: ab9e4f66f3829c9758cbc40abfcde50df597a2d3
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918267"
---
# <a name="developing-background-applications"></a>백그라운드 응용 프로그램 개발

> [!NOTE]
> Visual Studio에서 액세스할 수 있는 RS4 이상의 SDK를 설치하지 않으면 RS5(또는 OpenSSH를 사용하는 RS4) IoT 이미지에 배포할 때 Visual Studio가 암호화 오류를 생성합니다.

백그라운드 응용 프로그램은 직접 UI가 없는 응용 프로그램입니다. 배포 및 구성 되 면 이러한 응용 프로그램은 컴퓨터 시작 시 시작 되 고 프로세스 수명 관리 리소스 사용 제한 없이 계속 실행 됩니다. 충돌이 발생 하거나 종료 되 면 시스템은 자동으로 다시 시작 됩니다.
이러한 백그라운드 응용 프로그램은 매우 간단한 실행 모델을 포함 합니다. 템플릿은 "IBackgroundTask" 인터페이스를 구현 하 고 빈 "Run" 메서드를 생성 하는 클래스를 만듭니다. 이 "실행" 메서드는 응용 프로그램에 대 한 진입점입니다.

![백그라운드 작업](../media/BackgroundApplications/backgroundTaskScreenshot.png)

한 가지 중요 한 점이 있습니다. 기본적으로 실행 메서드가 완료 되 면 응용 프로그램이 종료 됩니다. 즉, 입력을 기다리는 서버 또는 타이머를 실행 하는 일반적인 IoT 패턴을 따르는 앱은 앱 종료를 중간에 찾습니다. 이러한 상황이 발생 하지 않도록 하려면 "GetDeferral" 메서드를 호출 하 여 응용 프로그램을 종료 하지 않도록 해야 합니다. 지연 패턴에 대 한 자세한 내용은 [여기](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Background.BackgroundTaskDeferral)에서 찾을 수 있습니다.

## <a name="where-can-background-applications-be-installed-from"></a>백그라운드 응용 프로그램은 어디에서 설치할 수 있나요? 

[여기](https://go.microsoft.com/fwlink/?linkid=847472)에서 Visual Studio 갤러리의 배경 응용 프로그램을 사용 하도록 설정 하는 IoT 템플릿을 다운로드 하 고 설치할 수 있습니다.  또는 [Visual Studio 갤러리](https://visualstudiogallery.msdn.microsoft.com/) 에서 `Windows IoT Core Project Templates`을 검색 하거나 확장 및 업데이트 대화 상자의 visual studio에서 직접 검색 (도구 > 확장 및 업데이트 > 온라인) 하 여 템플릿을 찾을 수 있습니다.

## <a name="what-languages-are-available"></a>사용할 수 있는 언어는 무엇 인가요?

**IoT (백그라운드 응용 프로그램)** 템플릿은 다음에 대해 찾을 수 있습니다.

* **C++** `File > New > Project > Installed > Visual C++ > Windows > Windows IoT Core`
* **C#** `File > New > Project > Installed > Visual C# > Windows > Windows IoT Core`
* **Visual Basic** `File > New > Project > Installed > Visual Basic > Windows > Windows IoT Core`
* **JavaScript** `File > New > Project > Installed > JavaScript > Windows > Windows IoT Core`

## <a name="how-are-background-applications-used"></a>백그라운드 응용 프로그램 사용 방법 

백그라운드 응용 프로그램을 만드는 것은 백그라운드 작업을 만드는 것과 매우 비슷합니다.  백그라운드 응용 프로그램이 시작 되 면 Run 메서드를 호출 합니다.

```csharp
public void Run(IBackgroundTaskInstance taskInstance)
{
}
```

지연 개체를 만들지 않는 한 실행 메서드가 종료 되 면 백그라운드 응용 프로그램이 종료 됩니다. 비동기 프로그래밍에 대 한 일반적인 방법은 다음과 같이 지연 되는 것입니다.

```csharp
private BackgroundTaskDeferral deferral;
public void Run(IBackgroundTaskInstance taskInstance)
{
    deferral = taskInstance.GetDeferral();
    
    //
    // TODO: Insert code to start one or more asynchronous methods
    //
}
```

지연이 발생 하면 지연 개체의 Complete 메서드가 호출 될 때까지 백그라운드 응용 프로그램은 계속 됩니다.

```csharp
deferral.Complete();
```

## <a name="how-do-background-applications-start"></a>백그라운드 응용 프로그램을 시작 하는 방법

이 질문은 배포 및 호출로 나눌 수 있습니다.  

백그라운드 응용 프로그램을 배포 하려면 다음 중 하나를 수행 합니다.

* Visual Studio의 F5 키 (빌드, 배포 및 호출)를 사용 합니다.  자세한 내용은 Visual Studio에서 배포 및 시작 하는 방법을 설명 하는 [Hello World 샘플](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/HelloWorld) 을 참조 하세요.

> [!NOTE]
> 그러면 장치가 부팅 될 때 백그라운드 응용 프로그램이 시작 되도록 구성 되지 않습니다.

* 프로젝트 > 스토어 > 앱 패키지 만들기를 선택 하 여 Visual Studio에서 AppX를 만듭니다.  AppX를 만든 후 [Windows 장치 포털](../manage-your-device/DevicePortal.md) 을 사용 하 여 Windows 10 IoT Core 장치에 배포할 수 있습니다.

백그라운드 응용 프로그램을 호출 하기 위해 다음 중 하나를 수행할 수 있습니다.

* 위에서 설명한 것 처럼 Visual Studio의 F5 기능을 통해 백그라운드 응용 프로그램을 배포 하 고 즉시 시작할 수 있습니다.

> [!NOTE]
> 그러면 장치가 부팅 될 때 백그라운드 응용 프로그램이 시작 되도록 구성 되지 않습니다.

* IoT 장치에 배포 된 백그라운드 응용 프로그램의 경우, i이상 시작 .exe 유틸리티를 사용 하 여 장치가 부팅 될 때 백그라운드 응용 프로그램이 시작 되도록 구성할 수 있습니다.  백그라운드 응용 프로그램을 시작 앱으로 지정 하려면 다음 지침을 따릅니다 (아래 `BackgroundApplication1`에 대 한**앱 이름으로 대체** ).

1. [여기](../connect-your-device/PowerShell.md)에 설명 된 대로 Windows IoT Core 장치로 POWERSHELL (PS) 세션을 시작 합니다.

2. PS 세션에서 다음을 입력 합니다.
            
`[<your IP address>]: PS C:\> iotstartup list BackgroundApplication1`

3. 백그라운드 응용 프로그램의 전체 이름이 표시 됩니다. 예를 들면 다음과 같습니다.

`Headed   : BackgroundApplication1-uwp_cqewk5knvpvee!App
Headless : BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpvee`

4. 이 유틸리티는 백그라운드 응용 프로그램이 ' 헤드리스 ' 응용 프로그램 인지 확인 하 고 올바르게 설치 되었는지 확인 합니다.  배경 응용 프로그램의 경우에도 항목을 볼 수 있지만 무시 해도 됩니다.

5. 이제이 앱을 ' 시작 앱 '으로 쉽게 설정할 수 있습니다. 다음 명령을 입력 하면 됩니다.

`[<your IP address>]: PS C:\> iotstartup add headless BackgroundApplication1`

6. 이 유틸리티는 배경 응용 프로그램이 헤드리스 ' 시작 앱 ' 목록에 추가 되었는지 확인 합니다.

`Added Headless: BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpveeplication1`

7. 계속 진행 하 여 Windows IoT Core 장치를 다시 시작 합니다. PS 세션에서 shutdown 명령을 실행할 수 있습니다.

`[<your IP address>]: PS C:\> shutdown /r /t 0`

8. 장치가 다시 시작 되 면 백그라운드 응용 프로그램이 자동으로 시작 되 고 Windows 10 IoT Core는 중지 될 때마다 다시 시작 되도록 합니다.  

> [!NOTE]
> 백그라운드 앱이 자동으로 실행 되도록 등록 되 면 앱이 종료 되거나 충돌 하는 경우 자동으로 다시 시작 됩니다.  앱은 시작 되거나 다시 시작 되는 이유를 알 수 없으므로, 다시 시작 시 특별 한 작업을 수행 하려는 경우 앱에서 앱 상태를 추적 해야 합니다.

9. 다음 명령을 입력 하 여 헤드리스 시작 앱 목록에서 백그라운드 응용 프로그램을 제거할 수 있습니다.

`[<your IP address>]: PS C:\> iotstartup remove headless BackgroundApplication1`

10. 이 유틸리티는 배경 응용 프로그램이 헤드리스 ' 시작 앱 ' 목록에서 제거 되었는지 확인 합니다.

`Removed headless: BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpvee`

## <a name="see-also"></a>참고 항목
사용자 지정 이미지를 빌드할 때 백그라운드 앱을 추가 하려면 [Appx 패키지 만들기](../build-your-image/createinstallpackage.md) 를 참조 하세요.
