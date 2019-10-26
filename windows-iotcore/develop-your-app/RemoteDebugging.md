---
title: 원격 콘솔 앱 디버깅을 사용 하 여 앱 디버그
author: bfjelds
ms.author: bfjelds
ms.date: 09/12/2017
ms.topic: article
description: Visual Studio에서 원격으로 IoT Core 콘솔 응용 프로그램을 디버그 하는 방법을 알아봅니다.
keywords: windows iot, visual studio, 앱 배포, 원격 디버깅
ms.openlocfilehash: b18af69009b43df5d5d6f3d64a45d9d468017642
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918212"
---
# <a name="debug-your-app-using-remote-console-app-debugging"></a>원격 콘솔 앱 디버깅을 사용 하 여 앱 디버그

다음은 Visual Studio에서 원격으로 IoT Core 콘솔 응용 프로그램을 디버그 하는 방법입니다.

* 먼저 Windows IoT Core 장치에서 원격 디버거를 설정 해야 합니다. 먼저 [여기](AppDeployment.md) 의 단계에 따라 장치에 다른 유니버설 Windows 응용 프로그램을 배포 합니다 (HelloWorld 프로젝트 사용해 보세요). 그러면 필요한 모든 이진 파일이 장치에 복사 됩니다. 

* 장치에서 원격 디버거를 시작 하려면 PC에서 웹 브라우저를 열고 `http://<device name/IP address>:8080` 하 여 [Windows 장치 포털](../manage-your-device/DevicePortal.md)을 시작 합니다. 자격 증명 대화 상자에서 기본 사용자 이름 및 암호 `Administrator``p@ssw0rd`를 사용 합니다. Windows 장치 관리를 시작 하 고 웹 관리 홈 화면을 표시 합니다.

* 이제 Windows 장치 포털의 디버그 설정 섹션으로 이동 하 여 시작 Visual Studio 원격 디버거 아래에서 시작 단추를 클릭 합니다. 

    ![WindowsDevicePortalDebugSettings 원격 디버거 시작](../media/Console/device_portal_start_debugger.png)

* 메시지 상자가 표시 되 고 연결 정보를 제공 합니다. 

*  Visual Studio에서 프로젝트의 속성을 편집 하 여 대상을 구성할 수 있습니다. 강조 표시 된 모든 변경 내용을 보드의 이름 또는 IP 주소에 맞게 설정 해야 합니다.

    ![ConsoleApplication 원격 컴퓨터 프로젝트 설정](../media/Console/console_project_settings.png)
    
> [!NOTE]
> 위의 이미지가 표시 되지 않는 경우 상황에 맞는 메뉴에서 "솔루션 탐색기"으로 이동 하 여 "프로젝트 속성"으로 이동 합니다. 프로젝트 속성에 대 한 자세한 내용은 [여기](https://docs.microsoft.com/visualstudio/ide/managing-project-and-solution-properties?view=vs-2017)에서 찾을 수 있습니다.

> [!TIP]
> Windows IoT 핵심 장치 이름 대신 IP 주소를 사용할 수 있습니다.

* 배포를 사용 하도록 설정 하려면 프로젝트 구성을 수정 해야 합니다.  이렇게 하려면 도구 모음의 솔루션 구성 드롭다운 메뉴에서 구성 관리자를 선택 하 여 Configuration Manager을 엽니다.

    ![ConsoleApplication SolutionConfiguration](../media/Console/configuration_management.png)

    Configuration Manager에서 프로젝트 구성에 대해 배포 확인란을 선택 했는지 확인 합니다 .이 옵션을 사용 하지 않도록 설정 하면 배포 옵션이 프로젝트 속성의 디버깅 탭에 완전히 입력 되지 않았을 수 있습니다.

    ![ConsoleApplication 원격 컴퓨터 프로젝트 설정](../media/Console/deploy_checkbox.png)

* 이제 원격 Windows IoT Core 장치에 배포할 준비가 되었습니다. F5 키를 누르거나 디버그 \| 디버깅 시작을 선택 하 여 앱 디버깅을 시작 하면 됩니다. 빌드 \| 솔루션 배포를 사용 하 여 디버그 세션을 시작 하지 않고 간단히 응용 프로그램을 배포할 수도 있습니다.

> [!NOTE]
> Visual Studio에서 실행 하는 경우 출력은 아무 곳에도 표시 되지 않지만 중단점을 설정 하 고 변수 값 등을 볼 수 있습니다.

* 앱을 중지 하려면 ' 디버깅 중지 ' 단추를 누르거나 디버그 \| 디버깅 중지를 선택 합니다.

* 이제 응용 프로그램을 실행할 수 있습니다.  PowerShell/SSH 연결 ( [powershell에 대](../connect-your-device/PowerShell.md) 한 자세한 [내용은 여기에 있음)을](../connect-your-device/SSH.md)열고 위에서 지정한 원격 명령을 입력 하면 됩니다.

    ![ConsoleApplication 출력](../media/Console/console_output.png)

* 응용 프로그램 디버깅을 마친 후에는 Windows IoT Core 장치에서 원격 디버거를 중지 해야 합니다. 이렇게 하려면 Windows 장치 포털의 디버그 설정 섹션으로 이동한 후 원격 디버거 중지 단추를 클릭 합니다.

    ![WindowsDevicePortalDebugSettings 원격 디버거 중지](../media/Console/device_portal_stop_debugger.PNG)

