---
title: Visual Studio를 사용 하 여 앱 배포
author: bfjelds
ms.author: bfjelds
ms.date: 08/28/2017
ms.topic: article
description: Visual Studio 원격 디버깅 기능을 사용 하 여 앱을 배포 하는 방법을 알아봅니다.
keywords: windows iot, visual studio, 앱 배포, 원격 디버깅
ms.openlocfilehash: ea0d95fc3702e1cec7f6bda35450c5da495cd837
ms.sourcegitcommit: 77b86eee2bba3844e87f9d3dbef816761ddf0dd9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/11/2019
ms.locfileid: "65533370"
---
# <a name="deploying-an-app-with-visual-studio"></a>Visual Studio를 사용 하 여 앱 배포

Visual Studio를 사용 하면 응용 프로그램을 간편 하 게 배포 하 고 디버그할 수 있습니다. **원격 디버깅** 기능을 사용 하 여 로컬에 연결 된 Windows 10 IoT Core 장치에 앱을 배포 합니다. 

> [!NOTE]
> Visual Studio에서 액세스할 수 있는 RS4 이상의 SDK를 설치하지 않으면 RS5(또는 OpenSSH를 사용하는 RS4) IoT 이미지에 배포할 때 Visual Studio가 암호화 오류를 생성합니다.

> [!NOTE]
> 원격 디버깅을 사용 하려면 먼저 IoT Core 장치를 개발 PC와 동일한 로컬 네트워크에 연결 해야 하 고 UDP/TCP 통신이 네트워크에서 허용 되어야 합니다. 확실 하지 않은 경우 네트워크 트래픽이 허용 되는지 확인 합니다. 지침은 [장치에 연결](../connect-your-device/SetupWiFi.md) 을 참조 하세요.

## <a name="deploy-apps-to-your-windows-10-iot-core-device"></a>Windows 10 IoT Core 장치에 앱 배포

1. Visual Studio에서 응용 프로그램을 열고 도구 모음 드롭다운에서 아키텍처를 설정 합니다. Minnowboard Max에 대해 빌드하는 경우를 선택 `x86`합니다. Raspberry Pi 2, Raspberry Pi 3 또는 Dragonboard에 대해 빌드하는 경우를 선택 `ARM`합니다.

2. 그런 다음 Visual Studio 도구 모음에서 `Local Machine` 드롭다운을 클릭 하 고를 선택 `Remote Machine`합니다.

![Visual Studio의 원격 컴퓨터](../media/AppDeployment/remote-vs.png)

3. 이 시점에서 Visual Studio는 **원격 연결** 대화 상자를 표시 합니다. 이전에 [PowerShell](../connect-your-device/PowerShell.md) 을 사용 하 여 장치에 대 한 고유한 이름을 설정한 경우 여기에 입력할 수 있습니다 (이 예제에서는 **내 장치**를 사용 하 고 있음). 그렇지 않으면 Windows IoT 핵심 장치의 IP 주소를 사용 합니다.

4. 장치 이름/i p를 입력 한 `Universal (Unencrypted Protocol)` 후 인증 모드를 선택 하 고 **선택**을 클릭 합니다. 

![유니버설 인증 모드](../media/AppDeployment/remote-connections.png)

프로젝트 속성 (솔루션 탐색기에서 **속성** 선택)으로 이동 하 고 왼쪽의 `Debug` 탭을 선택 하 여 이러한 값을 확인 하거나 수정할 수 있습니다.

![디버그 탭](../media/AppDeployment/debug-tab.png)

5. 이제 배포할 준비가 되었습니다. F5 키를 누르면 됩니다 (또는 디버그 | 선택 디버깅 시작)을 시작 하 여 응용 프로그램 디버깅을 시작 합니다. 앱이 장치 화면에 표시 됩니다.

6. 일단 배포 되 면 중단점을 설정 하 고 변수 값 등을 볼 수 있습니다. 앱을 중지 하려면 ' 디버깅 중지 ' 단추를 누르거나 [디버그]를 선택 합니다. 디버깅 중지).

7. UWP 응용 프로그램을 성공적으로 배포 하 고 디버깅 한 후 릴리스 버전을 만듭니다.-Visual Studio 도구 모음 `Debug` 구성 `Release`드롭다운을에서로 변경 합니다.  이제 빌드를 선택 하 여 장치에 앱을 빌드하고 배포할 수 있습니다. 솔루션 다시 빌드 및 빌드 | 솔루션 배포.
