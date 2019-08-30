---
title: Embedded(포함) 모드
author: lilyhou
ms.author: lihou
ms.date: 11/10/2017
ms.topic: article
description: Windows에서 포함 모드를 허용 하도록 구성 하 여 백그라운드 응용 프로그램 및 기타 기능을 사용 하도록 구성 하는 방법을 알아봅니다.
keywords: windows iot, 포함 모드, 백그라운드 응용 프로그램
ms.openlocfilehash: ca8124d97a9161a1539eff92c55cf3630cf0a049
ms.sourcegitcommit: b719e66699372e1339c2316cab45df2a474d09a0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/28/2019
ms.locfileid: "66252173"
---
# <a name="embedded-mode"></a>Embedded(포함) 모드

임베디드 모드는 Windows IoT Core 및 Windows IoT Enterprise에서 지원 됩니다. 포함 모드를 사용 합니다.

* [백그라운드 응용 프로그램 (자세히 읽기)](https://docs.microsoft.com/windows/iot-core/develop-your-app/backgroundapplications)
* LowLevelDevice 기능 사용
* SystemManagement 기능 사용

임베디드 모드는 Windows IoT Core에서 항상 사용 하도록 설정 됩니다.
Windows IoT Enterprise에서 아래 단계를 수행 하 여 포함 모드를 사용 하도록 설정 해야 합니다.

## <a name="background-applications"></a>백그라운드 응용 프로그램

백그라운드 응용 프로그램은 Visual Studio의 IoT (배경 응용 프로그램) 템플릿을 사용 하 여 만듭니다.
자세한 내용은 [백그라운드 응용 프로그램](https://docs.microsoft.com/windows/iot-core/develop-your-app/backgroundapplications)만들기를 참조 하세요.

백그라운드 응용 프로그램은 리소스 제한 없이 중지 하지 않고 실행 됩니다. 또한 백그라운드 응용 프로그램이 어떤 이유로 중지 되 고 포함 모드를 사용 하는 경우 시스템에서 백그라운드 응용 프로그램을 다시 시작 합니다.

시스템이 백그라운드 응용 프로그램을 자동으로 다시 시작 하는 동안 사용자가 백그라운드 응용 프로그램의 작업을 중지 하거나 방해 하지 않도록 시스템 잠금 기능을 사용 하도록 설정 해야 합니다.

## <a name="lowlevel-device-capability-and-lowleveldevice-capability"></a>lowLevel 장치 기능 및 lowLevelDevice 기능

**Lowlevel** 장치 기능을 사용 하면 GPIO, SPI 및 I2C와 같은 하위 수준 하드웨어 인터페이스에 액세스할 수 있습니다.

* [Blinky 샘플 (GPIO)](https://developer.microsoft.com/en-us/windows/iot/samples/helloblinky)
* [가 속도계 샘플](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/Accelerometer)

**Lowleveldevices** 기능을 통해 많은 추가 요구 사항이 충족 되 면 앱에서 사용자 지정 장치에 액세스할 수 있습니다. 이 기능은 GPIO, I2C, SPI 및 PWM) 장치에 대 한 액세스를 허용 하는 lowLevel 장치 기능과 혼동 해서는 안 됩니다.

자세한 내용은 [앱 기능 선언](https://docs.microsoft.com/en-us/windows/uwp/packaging/app-capability-declarations) 을 참조 하세요.

## <a name="systemmanagment-capability"></a>systemManagment 기능

응용 프로그램에 대 한 systemManagment 기능을 사용 하도록 설정 하는 경우 잠금 해제 된 Api 집합은 다음과 같습니다.  

* [Windows. System.object](https://msdn.microsoft.com/library/windows/apps/windows.system.processlauncher.aspx)
* [TimeZoneSettings](https://msdn.microsoft.com/library/windows/apps/windows.system.timezonesettings.aspx)
* [ShutdownManager](https://msdn.microsoft.com/library/windows/apps/windows.system.shutdownmanager.aspx)
* [TrySetInputMethodLanguageTag.](https://msdn.microsoft.com/library/windows/apps/windows.globalization.language.trysetinputmethodlanguagetag.aspx)

## <a name="debugging-background-applications"></a>백그라운드 응용 프로그램 디버깅

Windows IoT Core를 실행 하지 않는 장치에서 디버깅 하는 경우 다음 오류 메시지 중 하나가 표시 되 면 장치에서 AllowEmbeddedMode을 사용 하도록 설정 하 고 포함 된 모드 서비스가 실행 중인지 확인 해야 합니다.

* 끝점 매퍼에서 사용할 수 있는 끝점이 더 이상 없습니다.
* 이 프로그램은 그룹 정책에 의해 차단 됩니다. 자세한 내용은 시스템 관리자에 게 문의 하십시오.

## <a name="changing-the-mode"></a>모드 변경
포함 모드를 사용 하도록 설정 하려면 AllowEmbeddedMode = 1을 설정 하는 ICD (이미징 및 구성 디자이너)에서 프로 비전 패키지를 만들어야 합니다.  ICD를 설치 하려면 Windows 10 용 Windows ADK를 다운로드 하 여 설치 해야 합니다.

* [Windows 10 용 Windows ADK 다운로드](http://go.microsoft.com/fwlink/p/?LinkId=526740)
* [Windows 10 용 Windows ADK의 새로운 기능에 대해 알아봅니다.](https://msdn.microsoft.com/library/windows/hardware/dn927348(v=vs.85).aspx)

1. ADK를 설치할 때 **ICD (이미징 및 구성 디자이너)** 를 선택 합니다.
2. 설치가 완료 되 면 Windows 이미징 및 구성 디자이너 (WICD)를 실행 합니다.

    ![WICD 아이콘](../media/EmbeddedMode/WICD_Icon.png)

3. **Advanced provisioning**(고급 프로비전)을 클릭합니다.  프로젝트 이름을 **AllowEmbeddedMode** 로, **다음**을 클릭 합니다.
    ![3 단계](../media/EmbeddedMode/Step3.png)

4. **모든 Windows 버전에 공통을 선택 하** 고 **다음**을 선택 합니다.
    ![4 단계](../media/EmbeddedMode/Step4.png)

5. **마침**을 클릭합니다.

    ![5 단계](../media/EmbeddedMode/Step5.png)

6. 검색 상자에 **EmbeddedMode** 를 입력 한 다음 **AllowEmbeddedMode**를 클릭 합니다.

    ![6 단계](../media/EmbeddedMode/Step6.png)

7. 가운데 창에서 **AllowEmbeddedMode** 값을 **예** ![Step7로 설정 합니다.](../media/EmbeddedMode/Step7.png)

8. 내보내기 > 프로 비전 패키지를 클릭 합니다.

    ![Step8](../media/EmbeddedMode/Step8.png)

9. 다음을 클릭합니다.

    ![Step9](../media/EmbeddedMode/Step9.png)

10. 다음을 클릭합니다.

    ![Step10](../media/EmbeddedMode/Step10.png)

11. 다음을 클릭합니다.

    ![Step11](../media/EmbeddedMode/Step11.png)

12. 빌드를 클릭 합니다.

    ![Step12](../media/EmbeddedMode/Step12.png)

13. 포함 모드를 설치 합니다. PPKG Windows IoT Enterprise에서을 두 번 클릭 합니다. PPKG.

14. **예, 추가를**클릭 합니다.
    LUA 대화 상자가 나타나면 예를 클릭 하 고 **예를** 클릭 하 여 아래에 표시 된 대화 상자에 추가 합니다.
    ![Step14Standard](../media/EmbeddedMode/Step14Standard.png)


## <a name="configuring-a-background-application-to-run-automatically"></a>백그라운드 응용 프로그램이 자동으로 실행 되도록 구성
1. 백그라운드 응용 프로그램을 자동으로 실행 하도록 구성 하려면 지침에 따라 [MinnowBoardMax SD 카드를 만들고](https://developer.microsoft.com/en-us/windows/iot/getstarted) 복사 `D:\windows\system32\iotstartup.exe` 합니다. 여기서 D:는 SD 카드입니다.

2. 설치 된 백그라운드 응용 프로그램의 목록을 가져오려면 다음을 입력 합니다.

        C:\> iotstartup list BackgroundApplication1

3. 출력에는 설치 된 각 백그라운드 응용 프로그램의 전체 이름이 포함 되어야 하며,이는 다음과 같습니다.

        Headless : BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpvee

5. 부팅 형식에서 실행 되도록이 앱을 구성 하려면:

        C:\> iotstartup add headless BackgroundApplication1

6. 백그라운드 응용 프로그램이 시작 목록에 성공적으로 추가 되 면 다음이 표시 됩니다.

        Added Headless: BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpveeplication1

7. 포함 된 모드 장치를 다시 시작 합니다.

8. 장치가 다시 시작 되 면 백그라운드 응용 프로그램이 자동으로 시작 됩니다.  백그라운드 응용 프로그램을 관리 하는 포함 모드 서비스를 시작 하는 데 몇 분 정도 걸릴 수 있습니다.  포함 모드 서비스는 시작 목록에서 백그라운드 응용 프로그램을 모니터링 하 고 중지 시 다시 시작 되는지 확인 합니다.  백그라운드 응용 프로그램이 짧은 시간 동안 여러 번 중지 하는 경우 더 이상 다시 시작 되지 않습니다.

9. 시작 목록에서 백그라운드 응용 프로그램을 제거 하려면 다음을 입력 합니다.

        C:\> iotstartup remove headless BackgroundApplication1

10. 백그라운드 응용 프로그램이 시작 목록에서 제거 되 면 출력은 다음과 같이 표시 됩니다.

        Removed headless: BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpvee
