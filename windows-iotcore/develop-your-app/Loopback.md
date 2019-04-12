---
title: Localhost를 사용 하 여 통신
author: paulmon
ms.author: paulmon
ms.date: 08/28/2017
ms.topic: article
description: 로컬 호스트 루프백을 사용 하 여 두 프로세스를 사용 하 여 TCP/IP 연결을 만드는 방법에 알아봅니다.
keywords: windows iot, localhost, 루프백, UWP, visual studio
ms.openlocfilehash: 498db8321babad890606e9e4589c9a6407f3ea6e
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512293"
---
# <a name="communicating-with-localhost-loopback"></a>Localhost (루프백)를 사용 하 여 통신

동일한 장치에서 실행 중인 2 프로세스 간의 TCP/IP 연결을 만들려는 경우 그 중 하나는 UWP 앱을 Windows IoT Core에 로컬 호스트 루프백을 활성화 해야 합니다.

## <a name="loopback-and-the-debugger"></a>루프백 및 디버거 
기본적으로 Visual Studio 디버거에서 실행 사용 하면 아웃 바운드 루프백 자동으로 해당 디버그 세션에 적용 됩니다.  루프백 확인란이 선택 되어 시작 프로젝트에 대 한 디버거 설정으로 모든 작업을 수행 하는 것이 없어야 합니다.  소켓 수신기를 구현 하려는 경우 로컬 호스트 루프백 인바운드 연결 (아래 참조)를 사용 하도록 설정 해야 있습니다.
 
## <a name="enabling-the-inbound-loopback-policy"></a>인바운드 루프백 정책 사용
로컬 호스트 루프백 정책에 대 한 인바운드 **Windows IoT Core** 서버를 구현 하는 UWP 앱에 대 한 사용 하도록 설정 해야 합니다.  이 정책은 다음 레지스트리 키에 의해 제어 됩니다.

        [HKEY_LOCAL_MACHINE\system\currentcontrolset\services\mpssvc\parameters]
            "IoTInboundLoopbackPolicy"=dword:00000001

IoTInboundLoopbackPolicy 레지스트리 키 값이 사용 하도록 설정 하려면 dword:00000001에 설정 되어야 합니다. IoTInboundLoopbackPolicy 레지스트리 값을 변경한 경우 변경 내용을 적용 하려면 다시 부팅 해야 합니다.  로컬 호스트 루프백 정책에서 기본적으로 사용할 수 있어야 **Windows IoT Core**

집합에서 다음 명령을 실행 값이 인지 확인 합니다 **Windows IoT Core** 장치:

        reg query hklm\system\currentcontrolset\services\mpssvc\parameters /v IoTInboundLoopbackPolicy

사용 하도록 설정 하려면 정책에서 다음 명령을 실행 합니다 **Windows IoT Core** 장치:

        reg add hklm\system\currentcontrolset\services\mpssvc\parameters /v IoTInboundLoopbackPolicy /t REG_DWORD /d 1
 

## <a name="enabling-loopback-for-a-uwp-application"></a>UWP 응용 프로그램에 대 한 루프백을 사용 하도록 설정
응용 프로그램에 대 한 루프백 수 있도록 하려면 패키지 패밀리 이름을 해야 합니다.  실행 하 여 설치 된 응용 프로그램에 대 한 패키지 패밀리 이름을 찾을 수 있습니다 **iotstartup 목록**합니다.  경우는 **iotstartup 목록** 응용 프로그램에 대 한 항목은 IoTCoreDefaultApp\_1w720vyc4ccym! 앱 패키지 제품군 이름을 다음이 IoTCoreDefaultApp\_1w720vyc4ccym

클라이언트 연결 사용에 대 한 루프백을 사용 하도록 설정 하려면 `CheckNetIsolation.exe LoopbackExempt -a -n=<AppContainer or Package Family>`합니다.  CheckNetIsolation.exe 응용 프로그램 및 종료에 대 한 루프백을 구성 됩니다. 이렇게 하면 응용 프로그램 서버에 대 한 아웃 바운드 연결을 확인 합니다.

예: `CheckNetIsolation.exe LoopbackExempt -a -n=IoTCoreDefaultApp_1w720vyc4ccym`

인바운드 연결을 수신 하도록 서버 응용 프로그램을 사용 하도록 설정 하려면 `CheckNetIsolation.exe LoopbackExempt -is -n=<AppContainer or Package Family>`합니다. 아웃 바운드 연결 구성에 달리 인바운드 연결 CheckNetIsolation.exe 서버 응용 프로그램은 연결을 수신 하는 동안에 지속적으로 실행 하려면 필요 합니다.  10.0.14393 이전의 최신 OS 빌드는 필요합니다.

예: `CheckNetIsolation.exe LoopbackExempt -is -n=IoTCoreDefaultApp_1w720vyc4ccym`

시작 시 CheckNetIsolation.exe를 자동으로 실행 하는 가장 좋은 방법은 schtasks.exe를 사용 하는 것입니다. `schtasks /create /tn MyTask /f /sc onstart /ru system /tr "checknetisolation LoopbackExempt -is -n=IoTCoreDefaultApp_1w720vyc4ccym"`

다시 부팅 시 해당 checknetisolation.exe tlist.exe를 사용 하 여 실행 중인지 확인할 수 있어야 하거나 [Windows Device Portal](https://developer.microsoft.com/en-us/windows/iot/docs/deviceportal)
