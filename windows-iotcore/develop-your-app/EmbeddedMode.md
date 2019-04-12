---
title: 포함 된 모드
author: lilyhou
ms.author: lihou
ms.date: 11/10/2017
ms.topic: article
description: 백그라운드 응용 프로그램 및 기타 기능을 사용 하도록 설정 하는 포함 된 모드를 허용 하도록 Windows를 구성 하는 방법에 알아봅니다.
keywords: windows iot, 포함 된 모드, 백그라운드 응용 프로그램
ms.openlocfilehash: 1944cec09400cff4d895bb9e55b89b3b19a3f5f5
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512318"
---
# <a name="embedded-mode"></a>포함 된 모드

Windows IoT Core 및 Windows IoT Enterprise에 포함 된 모드는 지원 됩니다. 포함 된 모드를 사용 하면:

* [백그라운드 응용 프로그램 (자세히)](https://docs.microsoft.com/windows/iot-core/develop-your-app/backgroundapplications)
* LowLevelDevice 기능 사용
* SystemManagement 기능 사용

포함 된 모드 창 IoT Core에 항상 사용 됩니다.
Windows IoT Enterprise에서 아래 단계에 따라 포함된 모드를 사용할 수 있어야 합니다.

## <a name="background-applications"></a>백그라운드 응용 프로그램

백그라운드 응용 프로그램은 백그라운드 응용 프로그램 (IoT) 템플릿을 사용 하 여 Visual Studio에서 생성 됩니다.
만들기에 대해 자세히 알아보세요 [백그라운드 응용 프로그램](https://docs.microsoft.com/windows/iot-core/develop-your-app/backgroundapplications)합니다.

백그라운드 응용 프로그램 중지 하지 않고 리소스에 제한 없이 실행합니다. 또한 백그라운드 응용 프로그램이 어떤 이유로 중지 하 고 포함 하는 경우 모드가 설정 된 시스템에 의해 백그라운드 응용 프로그램을 다시 시작 해야 합니다.

시스템 자동 백그라운드 응용 프로그램으로 시작 하는 동안 사용자가 중지 하거나 백그라운드 응용 프로그램의 작업을 방해 하지 못하도록 시스템 잠금 기능을 활성화 되어야 합니다.

## <a name="lowleveldevice-capability"></a>lowLevelDevice 기능

기능 lowLevelDevice I2C, SPI, GPIO 같은 하위 수준의 하드웨어 인터페이스에 액세스할 수 있습니다.

* [쳐다 Sample(GPIO)](https://developer.microsoft.com/en-us/windows/iot/samples/helloblinky)
* [가속도계 샘플](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/Accelerometer)

## <a name="systemmanagment-capability"></a>systemManagment 기능

응용 프로그램에 대 한 systemManagment 기능을 사용 하도록 설정 하면 잠금 해제 됩니다 하는 api 집합입니다.  

* [Windows.System.ProcessLauncher](https://msdn.microsoft.com/library/windows/apps/windows.system.processlauncher.aspx)
* [Windows.System.TimeZoneSettings](https://msdn.microsoft.com/library/windows/apps/windows.system.timezonesettings.aspx)
* [Windows.System.ShutdownManager](https://msdn.microsoft.com/library/windows/apps/windows.system.shutdownmanager.aspx)
* [Windows.Globalization.Language.TrySetInputMethodLanguageTag](https://msdn.microsoft.com/library/windows/apps/windows.globalization.language.trysetinputmethodlanguagetag.aspx)

## <a name="debugging-background-applications"></a>백그라운드 응용 프로그램 디버깅

Windows IoT Core를 실행 하지 않는 장치에서 디버깅 하는 경우 다음 오류 메시지 중 하나가 표시 AllowEmbeddedMode 장치에서 사용 하 고 포함 된 모드 서비스가 실행 되 고 있는지 확인 해야 합니다.

* 끝점 매퍼에서 사용할 수 있는 끝점이 더 이상 있습니다.
* 이 프로그램은 그룹 정책에 의해 차단 됩니다. 자세한 내용은 시스템 관리자에 게 문의 합니다.

## <a name="changing-the-mode"></a>모드 변경
이미징 및 구성 디자이너 (ICD) AllowEmbeddedMode 설정으로 프로 비전 패키지를 만들 해야 포함된 모드를 사용 하도록 설정 하려면 = 1입니다.  ICD를 설치 하려면 다운로드 하 고 Windows 10 용 Windows ADK를 설치 해야 합니다.

* [Windows 10 용 Windows ADK 다운로드](http://go.microsoft.com/fwlink/p/?LinkId=526740)
* [Windows 10 용 Windows ADK의에서 새로운 기능 알아보기](https://msdn.microsoft.com/library/windows/hardware/dn927348(v=vs.85).aspx)

1. ADK를 설치할 때 선택 **이미징 및 구성 디자이너 (ICD)**
2. 설치가 완료 된 후 Windows 이미징 및 구성 디자이너 (WICD)를 실행 합니다.

    ![WICD 아이콘](../media/EmbeddedMode/WICD_Icon.png)

3. **Advanced provisioning**(고급 프로비전)을 클릭합니다.  프로젝트 이름을 **AllowEmbeddedMode** 누릅니다 **다음**합니다.
    ![3 단계](../media/EmbeddedMode/Step3.png)

4. 선택할 **모든 Windows 버전에 공통적으로 적용** 한 다음 **다음**합니다.
    ![4 단계](../media/EmbeddedMode/Step4.png)

5. **마침**을 클릭합니다.

    ![5 단계](../media/EmbeddedMode/Step5.png)

6. 검색 상자에 입력 **EmbeddedMode** 를 클릭 하 고 **AllowEmbeddedMode**합니다.

    ![6 단계](../media/EmbeddedMode/Step6.png)

7. 창 가운데에 값을 설정 **AllowEmbeddedMode** 하 **예** ![Step7](../media/EmbeddedMode/Step7.png)

8. 내보내기를 클릭 > 패키지를 프로 비전

    ![Step8](../media/EmbeddedMode/Step8.png)

9. 다음을 클릭합니다.

    ![Step9](../media/EmbeddedMode/Step9.png)

10. 다음을 클릭합니다.

    ![Step10](../media/EmbeddedMode/Step10.png)

11. 다음을 클릭합니다.

    ![Step11](../media/EmbeddedMode/Step11.png)

12. 빌드를 클릭 합니다.

    ![Step12](../media/EmbeddedMode/Step12.png)

13. 포함 된 모드를 설치 합니다. Windows IoT enterprise PPKG 두 번 클릭 합니다. PPKG 합니다.

14. 클릭 **예, 추가**합니다.
    LUA 대화 상자, 표시 되는 경우 예를 클릭 하 고 클릭 **예, 추가** 아래에 표시 된 대화 상자에서.
    ![Step14Standard](../media/EmbeddedMode/Step14Standard.png)


## <a name="configuring-a-background-application-to-run-automatically"></a>자동으로 실행 하는 백그라운드 응용 프로그램 구성
1. 지침에 따라 자동으로 실행 하는 백그라운드 응용 프로그램을 구성 하려면이 필요 [MinnowBoardMax SD 카드를 만듭니다](https://developer.microsoft.com/en-us/windows/iot/getstarted) 복사 `D:\windows\system32\iotstartup.exe` (d:가 SD 카드).

2. 설치 된 백그라운드 응용 프로그램 유형 목록을 가져오려면:

        C:\> iotstartup list BackgroundApplication1

3. 출력은 다음과 같이 표시 됩니다는 각 설치 된 백그라운드 응용 프로그램에서의 전체 이름을 포함 되어야 합니다.

        Headless : BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpvee

5. 부팅 유형에 실행 되도록이 앱을 구성 합니다.

        C:\> iotstartup add headless BackgroundApplication1

6. 백그라운드 응용 프로그램이 성공적으로 시작 목록에 추가 된 경우이 표시 됩니다.

        Added Headless: BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpveeplication1

7. 포함 된 모드 장치를 다시 시작 합니다.

8. 장치를 다시 시작한 후 백그라운드 응용 프로그램에 자동으로 시작 됩니다.  백그라운드 응용 프로그램을 관리 하는 포함 된 모드를 시작 하려면 몇 분 정도 걸릴 수 있습니다.  포함된 모드를 시작 프로그램 목록에서 백그라운드 응용 프로그램을 모니터링 하 고는 중지 되 면 다시 시작 가져오기 있는지 확인 됩니다.  짧은 기간에 여러 번 백그라운드 응용 프로그램을 중지 하는 경우 더 이상 시작할 수 없습니다.

9. 시작 목록 형식에서 백그라운드 응용 프로그램을 제거:

        C:\> iotstartup remove headless BackgroundApplication1

10. 백그라운드 응용 프로그램 구동 목록에서 제거 되 면 다음과 같은 출력이 표시 됩니다.

        Removed headless: BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpvee
