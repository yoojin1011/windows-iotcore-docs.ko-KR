---
title: 백그라운드 응용 프로그램
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: IoT 장치에 대 한 백그라운드 응용 프로그램을 개발 하는 방법에 알아봅니다.
keywords: windows iot, 백그라운드 응용 프로그램
ms.openlocfilehash: 1b3fd831a4cdf3ebb8bc2d80c544344b13115617
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512917"
---
# <a name="developing-background-applications"></a>백그라운드 응용 프로그램 개발

> [!NOTE]
> Visual Studio는 RS5를 배포 하는 경우 암호화 오류가 생성 됩니다 (또는 RS4 OpenSSH 사용 하 여 사용 하도록 설정) IoT 이미지에서 RS4 이상 SDK는 Visual Studio에 액세스할 수 있도록 설치 되어 있지 않으면입니다.

백그라운드 응용 프로그램은 UI가 없는 직접 응용 프로그램. 배포 후 구성 된 이러한 응용 프로그램 컴퓨터 시작 시 시작 하 고 모든 프로세스 수명 관리 리소스 사용 제한 없이 계속 실행 합니다. 충돌 하거나 종료 시스템은 자동으로 다시 시작 합니다.
이러한 백그라운드 응용 프로그램에는 매우 간단한 실행 모델이 있습니다. 템플릿을 "IBackgroundTask" 인터페이스를 구현 하 고 빈 "Run" 메서드를 생성 하는 클래스를 만듭니다. 이 "실행" 메서드는 응용 프로그램 진입점입니다.

![백그라운드 작업](../media/BackgroundApplications/backgroundTaskScreenshot.png)

점이 하나 위험 지점이: 기본적으로 응용 프로그램 종료 실행된 메서드를 완료 합니다. 이 입력 또는 타이머 대기 서버를 실행 하는 일반적인 IoT 패턴을 따르는 앱 중간 앱 종료를 찾을 수는 것을 의미 합니다. 이를 방지 하려면 응용 프로그램 종료를 방지 하기 위해 "GetDeferral" 메서드를 호출 해야 합니다. 지연 패턴에 대 한 자세한 정보를 찾을 수 있습니다 [여기](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Background.BackgroundTaskDeferral)합니다.

## <a name="where-can-background-applications-be-installed-from"></a>여기서 백그라운드 응용 프로그램에서 설치할 수 있습니까? 

다운로드 하 고 Visual Studio 갤러리의 백그라운드 응용 프로그램을 사용 하도록 설정 하려면 IoT 템플릿을 설치할 수 있습니다 [여기](https://go.microsoft.com/fwlink/?linkid=847472)합니다.  또는 검색 하 여 템플릿을 찾을 수 있습니다 `Windows IoT Core Project Templates` 에 [Visual Studio 갤러리](https://visualstudiogallery.msdn.microsoft.com/) 또는 확장 및 업데이트 대화 상자에서 Visual Studio에서 직접 (도구 > 확장 및 업데이트 > 온라인).

## <a name="what-languages-are-available"></a>어떤 언어로 제공 되나요?

**응용 프로그램 (IoT) 백그라운드** 에 대 한 템플릿을 찾을 수 있습니다.

* **C++** `File > New > Project > Installed > Visual C++ > Windows > Windows IoT Core`
* **C#** `File > New > Project > Installed > Visual C# > Windows > Windows IoT Core`
* **Visual Basic** `File > New > Project > Installed > Visual Basic > Windows > Windows IoT Core`
* **JavaScript** `File > New > Project > Installed > JavaScript > Windows > Windows IoT Core`

## <a name="how-are-background-applications-used"></a>백그라운드 응용 프로그램을 사용 하는 방법 

백그라운드 응용 프로그램 만들기를 백그라운드 작업을 만드는 매우 비슷합니다.  백그라운드 응용 프로그램이 시작 되 면 Run 메서드가 호출 됩니다.

```csharp
public void Run(IBackgroundTaskInstance taskInstance)
{
}
```

Run 메서드가 종료 지연 개체를 만들지 않으면 백그라운드 응용 프로그램이 종료 됩니다. 비동기 프로그래밍에 대 한 일반적으로, 다음과 같습니다. 이와 같은 지연 수행

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

지연은 수행 되지 않고 백그라운드 응용 프로그램이 deferral 개체의 Complete 메서드를 호출할 때까지 계속 됩니다.

```csharp
deferral.Complete();
```

## <a name="how-do-background-applications-start"></a>백그라운드 응용 프로그램을 시작 하려면 어떻게?

이 질문은 배포 및 호출으로 분류할 수 있습니다.  

백그라운드 응용 프로그램을 배포 하려면 다음 하거나 수행할 수 있습니다.

* Visual Studio F5 (하는 빌드, 배포 호출)를 사용 합니다.  자세한 내용은 참조 하세요. 당사의 [헬로 월드 샘플](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/HelloWorld) 배포 하 고 Visual Studio에서 시작 하는 방법을 설명 하는 합니다.

> [!NOTE]
> 이 장치를 부팅할 때도 시작 하도록 백그라운드 응용 프로그램을 구성 하지 않을 예정입니다.

* Visual Studio에서 프로젝트를 선택 하 여 AppX를 만들기 > 저장소 > 앱 패키지 만들기.  AppX를 만든 후 사용할 수 있습니다 [Windows Device Portal](../manage-your-device/DevicePortal.md) Windows 10 IoT Core 장치에 배포할 수 있습니다.

백그라운드 응용 프로그램을 호출 하기 위해 제출할 수 있습니다.

* 위에서 설명한 대로 Visual Studio F5 기능 배포를 업데이트 하 고 백그라운드 응용 프로그램을 즉시 시작 됩니다.

> [!NOTE]
> 이 장치를 부팅할 때도 시작 하도록 백그라운드 응용 프로그램을 구성 하지 않을 예정입니다.

* IoT 장치에 배포 된 백그라운드 응용 프로그램을 시작할 장치를 부팅할 때 백그라운드 응용 프로그램을 구성 하려면 iotstartup.exe 유틸리티를 사용할 수 있습니다.  백그라운드 응용 프로그램에 앱을 시작으로 지정 하려면 다음이 지침을 따릅니다 (**앱의 이름으로 대체** 에 대 한 `BackgroundApplication1` 아래).

1. 설명 된 대로 Windows IoT Core 장치를 사용 하 여 PS (PowerShell) 세션을 시작 [여기](../connect-your-device/PowerShell.md)합니다.

2. PS 세션에서 다음을 입력 합니다.
            
`[<your IP address>]: PS C:\> iotstartup list BackgroundApplication1`

3. 즉, 같은 백그라운드 응용 프로그램의 전체 이름을 표시 됩니다.

`Headed   : BackgroundApplication1-uwp_cqewk5knvpvee!App
Headless : BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpvee`

4. 유틸리티는 백그라운드 응용 프로그램 '헤드리스' 응용 프로그램은 하 고이 올바르게 설치 되어 있는지 확인 됩니다.  표시 될 가능성이 높습니다 Headed 항목을도 백그라운드 응용 프로그램에 대 한 있지만이 무시할 수 있습니다.

5. 이제 ' 시작 ' 앱으로이 앱을 설정 하기 쉽습니다. 명령을 입력 합니다.

`[<your IP address>]: PS C:\> iotstartup add headless BackgroundApplication1`

6. 유틸리티는 백그라운드 응용 프로그램에 헤드리스 ' 시작 앱 ' 목록에 추가 되었는지 확인 됩니다.

`Added Headless: BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpveeplication1`

7. 계속 해 서 Windows IoT Core 장치 다시 시작 합니다. PS 세션에서를 종료 명령을 실행할 수 있습니다.

`[<your IP address>]: PS C:\> shutdown /r /t 0`

8. 장치를 다시 시작한 후 백그라운드 응용 프로그램은 자동으로 시작 하 고 Windows 10 IoT Core 중지 언제 든 지 다시 가져옵니다 있는지 확인 합니다.  

> [!NOTE]
> 앱 종료 또는 충돌 하는 경우 자동으로 실행 하는 백그라운드 앱 등록 되 면 자동으로 시작할 수 있습니다.  앱이 시작 되 고 또는 앱에서 앱 상태를 추적 해야 다시 시작 시 특수 한 작업을 수행 하려는 경우에이 다시 시작 이유 내용 알림이 표시 되지 않습니다.

9. 헤드리스 시작 앱 목록에서 명령을 입력 하 여 백그라운드 응용 프로그램을 제거할 수 있습니다.

`[<your IP address>]: PS C:\> iotstartup remove headless BackgroundApplication1`

10. 유틸리티는 백그라운드 응용 프로그램가 제거 된 앱 목록에서 헤드리스 ' 시작 ' 확인:

`Removed headless: BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpvee`

# <a name="see-also"></a>관련 항목
백그라운드 앱을 사용자 지정 이미지 참조를 빌드할 때 추가할 [Appx 패키지 만들기](../build-your-image/createinstallpackage.md)
