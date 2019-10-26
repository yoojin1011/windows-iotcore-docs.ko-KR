---
title: 기본 앱 설정
author: bfjelds
ms.author: bfjelds
ms.date: 09/05/2017
ms.topic: article
description: Windows 장치 포털 또는 셸을 사용 하 여 기본 앱을 설정 하는 방법을 알아봅니다.
keywords: windows iot, 기본 앱, PowerShell, iot
ms.openlocfilehash: b7165331daba3b8bc953535ecc2d5b51cfda782c
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918211"
---
# <a name="setup-a-default-app"></a>기본 앱 설정
여기서는 응용 프로그램을 기본 응용 프로그램으로 설정 하는 방법을 알아봅니다. 기본 응용 프로그램은 시스템이 부팅 될 때 실행 되는 응용 프로그램입니다.  

> [!NOTE]
> Visual Studio에서 액세스할 수 있는 RS4 이상의 SDK를 설치하지 않으면 RS5(또는 OpenSSH를 사용하는 RS4) IoT 이미지에 배포할 때 Visual Studio가 암호화 오류를 생성합니다.

## <a name="runtime-options"></a>런타임 옵션

개발/실험적 단계 중에 다음 방법으로 기본 앱을 변경할 수 있습니다.

### <a name="using-windows-device-portal"></a>Windows 장치 포털 사용

앱에 해당 하는 **시작** 열을 클릭할 수 있습니다.
![SetupDefaultAppWDP](../media/SetupDefaultApp/DefaultAppWDP.png)

### <a name="using-the-shell"></a>Shell 사용

셸을 사용 하 여 기본 앱을 설정 하는 단계 

1. [Powershell](../connect-your-device/PowerShell.md) 을 통해 장치에 연결

2. `iotstartup list`를 사용 하 여 설치 된 응용 프로그램 나열

3. 기본값으로 지정할 응용 프로그램의 appid를 확인 하 고 `iotstartup add headed <appid>`를 사용 하 여 설정 합니다. 헤드리스 응용 프로그램의 경우 `iotstartup add headless <appid>`를 사용 해야 합니다.


## <a name="build-time-option"></a>빌드 시간 옵션

대량 배포의 경우 프로 비전 패키지를 사용 하 여이를 달성할 수 있습니다.

프로 비전 패키지를 만드는 동안 WCD에서 StartupApp/Default 설정을 지정할 수 있습니다.
![SetupDefaultAppICD](../media/SetupDefaultApp/DefaultAppICD.png)

예를 들어 [IoTCoreDefaultApp](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Packages/Appx.IoTCoreDefaultApp/customizations.xml) 를 참조 하세요. [GetAppxInfo 도구](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools/GetAppxInfo.exe)를 사용 하 여 Appx의 응용 프로그램 사용자 모델 ID (AUMID)를 가져올 수 있습니다.

## <a name="how-to-configure-home-key"></a>"홈" 키를 구성 하는 방법

Windows 10 IoT 기념일 업데이트 (1607)는 다른 응용 프로그램이 현재 실행 중일 때 기본 응용 프로그램 창을 포그라운드로 가져오기 위한 셸을 지원 합니다.

"홈" 키를 사용 하도록 설정 하는 방법을 보려면 [IoT Shell 페이지](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoreshell#switching-between-apps-with-hid-injection-keys) 를 방문 하세요.
