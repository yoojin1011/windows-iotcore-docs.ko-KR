---
title: 기본 앱 설정
author: bfjelds
ms.author: bfjelds
ms.date: 09/05/17
ms.topic: article
description: Windows Device Portal 이나 셸을 사용 하 여 기본 앱을 설정 하는 방법에 알아봅니다.
keywords: windows iot, 기본 앱, PowerShell, iot
ms.openlocfilehash: f3f7a5194491250a8a0b49e81e073282c8f5660b
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513325"
---
# <a name="setup-a-default-app"></a>기본 앱 설정
여기에 기본 응용 프로그램으로 응용 프로그램을 설정 하는 방법을 배웁니다. 기본 응용 프로그램 시스템을 부팅할 때 실행 되는 것입니다.  

> [!NOTE]
> Visual Studio는 RS5를 배포 하는 경우 암호화 오류가 생성 됩니다 (또는 RS4 OpenSSH 사용 하 여 사용 하도록 설정) IoT 이미지에서 RS4 이상 SDK는 Visual Studio에 액세스할 수 있도록 설치 되어 있지 않으면입니다.

## <a name="runtime-options"></a>런타임 옵션

개발 중 / 실험적 단계로 다음과 같은 방법으로 기본 앱을 변경할 수 있습니다.

### <a name="using-windows-device-portal"></a>Windows Device Portal 사용 하 여

클릭할 수 있습니다 **시작** 앱에 해당 하는 열입니다.
![SetupDefaultAppWDP](../media/SetupDefaultApp/DefaultAppWDP.png)

### <a name="using-the-shell"></a>셸 사용

셸을 사용 하 여 기본 앱을 설정 하는 단계 

1. 통해 장치를 연결할 [Powershell](../connect-your-device/PowerShell.md)

2. 사용 하 여 설치할 응용 프로그램 나열 `iotstartup list`

3. 기본적으로 확인 하 여 설정 하려는 응용 프로그램에 대 한 appid 참고 `iotstartup add headed <appid>`합니다. 헤드리스 앱에 대 한 사용할지 `iotstartup add headless <appid>`합니다.


## <a name="build-time-option"></a>빌드 시간 옵션

대규모 배포를 수행 하면 프로 비전 패키지를 사용 하 여

프로 비전 패키지를 만드는 동안 StartupApp/기본 설정 된 WCD에서 지정할 수 있습니다.
![SetupDefaultAppICD](../media/SetupDefaultApp/DefaultAppICD.png)

참조 [Appx.IoTCoreDefaultApp](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Packages/Appx.IoTCoreDefaultApp/customizations.xml) 예입니다. 응용 프로그램 사용자 모델 ID ()의 AUMID를 사용 하 여 appx를 가져올 수 있습니다 [GetAppxInfo 도구](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools/GetAppxInfo.exe)합니다.

## <a name="how-to-configure-home-key"></a>"홈" 키를 구성 하는 방법

Windows 10 IoT 1 주년 업데이트 (1607) 다른 응용 프로그램에서 현재 실행 중인 경우 기본 응용 프로그램 창을 전경으로 가져오는 셸 지원을 제공 합니다.

를 "홈" 키를 사용 하는 방법을 보려면 알아보려면 우리의 [IoT 셸 페이지](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoreshell#switching-between-apps-with-hid-injection-keys)
