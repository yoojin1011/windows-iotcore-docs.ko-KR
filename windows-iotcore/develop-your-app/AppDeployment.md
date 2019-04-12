---
title: Visual Studio 사용 하 여 앱 배포
author: bfjelds
ms.author: bfjelds
ms.date: 08/28/2017
ms.topic: article
description: Visual Studio 원격 디버깅 기능을 사용 하 여 앱을 배포 하는 방법에 알아봅니다.
keywords: windows iot, visual studio, 앱 배포, 원격 디버깅
ms.openlocfilehash: 218cbf43a1b63a517091b80315f327954b3eae5a
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513238"
---
# <a name="deploying-an-app-with-visual-studio"></a>Visual Studio 사용 하 여 앱 배포

배포 및 응용 프로그램 디버깅에 Visual Studio를 사용 하 여 간단 합니다. 사용 된 **원격 디버깅** 로컬로 연결 된 Windows 10 IoT Core 장치에 앱을 배포 하는 기능입니다. 

> [!NOTE]
> Visual Studio는 RS5를 배포 하는 경우 암호화 오류가 생성 됩니다 (또는 RS4 OpenSSH 사용 하 여 사용 하도록 설정) IoT 이미지에서 RS4 이상 SDK는 Visual Studio에 액세스할 수 있도록 설치 되어 있지 않으면입니다.

> [!NOTE]
> 원격 디버깅을 사용 하려면 먼저 개발 PC와 같은 로컬 네트워크에 대 IoT Core 장치 연결 되어야 합니다.  
>참조를 [장치로 연결](../connect-your-device/SetupWiFi.md) 지침입니다.

## <a name="deploy-a-c-app-to-your-windows-10-iot-core-device"></a>배포는 C# Windows 10 IoT Core 장치에 앱 
___

1. Visual Studio에서 응용 프로그램을 열고 도구 모음 드롭다운 목록에서 아키텍처를 설정 합니다. Minnowboard 최대 만든다면 선택 `x86`합니다. Raspberry Pi 2, Raspberry Pi 3에는 Dragonboard 만든다면 선택 `ARM`합니다.

2. 다음으로 Visual Studio 도구 모음에서 클릭 합니다 `Local Machine` 드롭다운에서 선택한 `Remote Machine`합니다.

![원격 컴퓨터에서 Visual Studio](../media/AppDeployment/cs-remote-machine-debugging.png)

3. Visual Studio가 제공 하는 시점에서 **원격 연결** 대화 합니다. 이전에 사용한 [PowerShell](../connect-your-device/PowerShell.md) 장치에 대 한 고유 이름을 설정 하려면 사용자가 입력할 수 여기 (이 예제에서는 사용 중인 것 **내 장치**). 그렇지 않은 경우 Windows IoT Core 장치 IP 주소를 사용 합니다.

4. 장치 이름/i P를 입력 한 후 선택 `Universal (Unencrypted Protocol)` 인증 모드, 클릭 **선택**합니다. 

![유니버설 인증 모드](../media/AppDeployment/cs-remote-connections.png)

확인 하거나 프로젝트 속성으로 이동 하 여 이러한 값을 수정할 수 있습니다 (선택 **속성** 솔루션 탐색기에서)를 선택 하 고는 `Debug` 왼쪽 탭:

![디버그 탭](../media/AppDeployment/cs-debug-project-properties.png)

5. 이제 배포할 준비가 되었습니다. 간단히 F5 키를 눌러 (디버그 선택 또는 \| 디버깅 시작) 앱 디버깅을 시작 합니다. 장치의 화면에 표시 하는 앱이 표시 됩니다.

6. 을 배포한 후에 중단점, 참조 변수 값을 설정할 수 있습니다. 앱 키를 눌러 ' 디버깅 중지 ' 단추를 중지 하려면 (디버그 선택 또는 \| 디버깅 중지) 합니다.

7. 성공적으로 배포 하 고 UWP 응용 프로그램 디버깅 만든 릴리스 버전-Visual Studio 도구 모음 구성 드롭다운 목록에서 변경할 `Debug` 에 `Release`입니다.  이제 빌드 및 빌드를 선택 하 여 장치에 앱을 배포할 수 있습니다 \| 솔루션 다시 빌드 및 빌드 \| 솔루션 배포 합니다.

## <a name="deploy-a-c-app-to-your-windows-10-iot-core-device"></a>배포는 C++ Windows 10 IoT Core 장치에 앱

1. Visual Studio에서 응용 프로그램을 열고 도구 모음 드롭다운 목록에서 아키텍처를 설정 합니다. Minnowboard 최대 만든다면 선택 `86`합니다. Raspberry Pi 2 또는 3을 빌드하는 경우 선택 `ARM`합니다.

2. 다음으로 Visual Studio 도구 모음에서 클릭 된 `Local Machine` 드롭다운 선택 `Remote Machine`

![로컬 컴퓨터에서 Visual Studio](../media/AppDeployment/cpp-remote-machine-debugging.png)

3. 프로젝트를 마우스 오른쪽 단추로 클릭 다음에 **솔루션 탐색기** 창입니다. **속성**을 선택합니다. 

![Visual Studio에서 속성](../media/AppDeployment/cpp-project-properties.png)

4. 아래 **구성 속성-> 디버깅**, 다음 필드를 수정 합니다.

    * **컴퓨터 이름을**: 이전에 사용한 [PowerShell](../connect-your-device/PowerShell.md) 장치에 대 한 고유 이름을 설정 하려면 사용자가 입력할 수 여기 (이 예제에서는 사용 중인 것 **내 장치**). 그렇지 않은 경우 Windows IoT Core 장치 IP 주소를 사용 합니다.
    * **인증 모드**: 로 **유니버설 (암호화 되지 않은 프로토콜)**
    
![유니버설 인증 모드](../media/AppDeployment/cpp-debug-project-properties.png)

5. 이제 배포할 준비가 되었습니다. 간단히 F5 키를 눌러 (디버그 선택 또는 \| 디버깅 시작) 앱 디버깅을 시작 합니다. Windows IoT Core 장치 화면에서 앱이 표시 됩니다.

6. 을 배포한 후에 중단점, 참조 변수 값을 설정할 수 있습니다. 앱을 중지 하려면 ' 디버깅 중지 ' 단추를 누릅니다 (디버그 선택 또는 \| 디버깅 중지) 합니다.

7. 성공적으로 배포 하 고 UWP 응용 프로그램을 디버깅 하지 릴리스 버전 만들기-Visual Studio 도구 모음 구성 드롭다운 목록에서 변경할 `Debug` 에 `Release`입니다.  이제 빌드 및 빌드를 선택 하 여 장치에 앱을 배포할 수 있습니다 \| 솔루션 다시 빌드 및 빌드 \| 솔루션 배포 합니다.

