---
title: Localhost와 통신
author: paulmon
ms.author: paulmon
ms.date: 08/28/2017
ms.topic: article
description: Localhost 루프백을 사용 하도록 설정 하 여 두 프로세스로 TCP/IP 연결을 만드는 방법에 대해 알아봅니다.
keywords: windows iot, localhost, 루프백, UWP, visual studio
ms.openlocfilehash: 498db8321babad890606e9e4589c9a6407f3ea6e
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "60170671"
---
# <a name="communicating-with-localhost-loopback"></a>Localhost (루프백)와 통신

Windows IoT Core에서 동일한 장치에서 실행 되는 두 프로세스 사이에 TCP/IP 연결을 만들고 그 중 하나가 UWP 앱 인 경우 localhost 루프백을 사용 하도록 설정 해야 합니다.

## <a name="loopback-and-the-debugger"></a>루프백 및 디버거 
기본적으로 Visual Studio 디버거에서 실행 되는 경우 해당 디버그 세션에 대해서만 자동으로 아웃 바운드 루프백을 사용 합니다.  시작 프로젝트에 대 한 디버거 설정에서 루프백 확인란을 선택 하는 동안에는 아무것도 수행할 필요가 없습니다.  소켓 수신기를 구현 하려면 인바운드 연결에 대해 localhost 루프백을 사용 하도록 설정 해야 합니다 (아래 참조).
 
## <a name="enabling-the-inbound-loopback-policy"></a>인바운드 루프백 정책 사용
서버를 구현 하는 UWP 앱에 대해 **Windows IoT Core** 에 대 한 localhost 인바운드 루프백 정책을 사용 하도록 설정 해야 합니다.  이 정책은 다음 레지스트리 키를 통해 제어 됩니다.

        [HKEY_LOCAL_MACHINE\system\currentcontrolset\services\mpssvc\parameters]
            "IoTInboundLoopbackPolicy"=dword:00000001

이 IoTInboundLoopbackPolicy 레지스트리 키 값을 dword: 00000001로 설정 해야 사용할 수 있습니다. IoTInboundLoopbackPolicy 레지스트리 값을 변경 하는 경우 변경 내용을 적용 하려면 다시 부팅 해야 합니다.  Localhost 루프백 정책은 **Windows IoT Core** 에서 기본적으로 사용 하도록 설정 해야 합니다.

값이 설정 되어 있는지 확인 하려면 **Windows IoT Core** 장치에서 다음 명령을 실행 합니다.

        reg query hklm\system\currentcontrolset\services\mpssvc\parameters /v IoTInboundLoopbackPolicy

정책을 사용 하도록 설정 하려면 **Windows IoT Core** 장치에서 다음 명령을 실행 합니다.

        reg add hklm\system\currentcontrolset\services\mpssvc\parameters /v IoTInboundLoopbackPolicy /t REG_DWORD /d 1
 

## <a name="enabling-loopback-for-a-uwp-application"></a>UWP 응용 프로그램에 대해 루프백 사용
응용 프로그램에 대해 루프백을 사용 하도록 설정 하려면 패키지 제품군 이름이 필요 합니다.  **Iotstartup 목록을**실행 하 여 설치 된 응용 프로그램에 대 한 패키지 제품군 이름을 찾을 수 있습니다.  응용 프로그램에 대 한 **iotstartup 목록** 항목이 IoTCoreDefaultApp\_1w720vyc4ccym! 인 경우 앱에서 패키지 제품군 이름은 IoTCoreDefaultApp\_1w720vyc4ccym입니다.

클라이언트 연결에 대해 루프백을 사용 `CheckNetIsolation.exe LoopbackExempt -a -n=<AppContainer or Package Family>`하도록 설정 하려면를 사용 합니다.  CheckNetIsolation는 응용 프로그램에 대해 루프백을 구성 하 고 종료 합니다. 이렇게 하면 응용 프로그램이 서버에 대 한 아웃 바운드 연결을 설정할 수 있습니다.

예: `CheckNetIsolation.exe LoopbackExempt -a -n=IoTCoreDefaultApp_1w720vyc4ccym`

서버 응용 프로그램에서 인바운드 연결을 받도록 설정 하려면 `CheckNetIsolation.exe LoopbackExempt -is -n=<AppContainer or Package Family>`를 사용 합니다. 아웃 바운드 연결 구성과 달리 인바운드 연결은 서버 응용 프로그램이 연결을 수신 하는 동안 CheckNetIsolation를 계속 실행 해야 합니다.  이를 위해서는 10.0.14393 보다 최신 OS 빌드가 필요 합니다.

예: `CheckNetIsolation.exe LoopbackExempt -is -n=IoTCoreDefaultApp_1w720vyc4ccym`

시작할 때 CheckNetIsolation를 자동으로 실행 하는 가장 좋은 방법은 schtasks.exe를 사용 하는 것입니다.`schtasks /create /tn MyTask /f /sc onstart /ru system /tr "checknetisolation LoopbackExempt -is -n=IoTCoreDefaultApp_1w720vyc4ccym"`

재부팅 시 tlist.exe 또는 [Windows 장치 포털](https://developer.microsoft.com/en-us/windows/iot/docs/deviceportal) 을 사용 하 여 checknetisolation가 실행 되 고 있는지 확인할 수 있어야 합니다.
