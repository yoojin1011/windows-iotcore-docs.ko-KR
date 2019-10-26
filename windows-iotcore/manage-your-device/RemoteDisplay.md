---
title: 원격 표시
ms.date: 08/28/2017
ms.topic: article
description: Windows 10 IoT Core UWP 응용 프로그램을 원격으로 확인 하 고 제어 하는 방법을 알아봅니다.
keywords: windows iot, UWP, 원격 디스플레이, 원격, UWP 응용 프로그램
ms.openlocfilehash: c0e082284e5bceb6f1a7a87723e883ad6e552c4e
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72917401"
---
# <a name="remote-display"></a>원격 표시
Windows 10 desktop PC, 태블릿 또는 휴대폰에서 원격으로 Windows 10 IoT Core UWP 응용 프로그램 보기 및 제어

> [!WARNING]
> Windows IoT 원격 클라이언트는 개발자 전용 기능입니다. 프로덕션 장치에 적합 하지 않거나 지원 되지 않습니다.

> [!IMPORTANT]
> Windows IoT 원격 클라이언트가 Raspberry Pi와 함께 작동하지 않습니다. Minnowboard Max 또는 Dragonboard처럼 가속 그래픽을 사용하는 보드를 사용하거나 로컬 표시용 모니터를 연결하세요.

## <a name="overview"></a>개요
___
원격 표시 환경은 Windows 10 IoT Core 장치에서 실행 되는 UWP 응용 프로그램을 원격으로 제어 하는 데 사용 되는 개발자 도구입니다.   

## <a name="setup"></a>설정
___
시작 하려면 Windows 10의 최신 빌드를 사용 하 여 Windows 10 IoT Core 장치를 설정 해야 합니다. [시작](https://developer.microsoft.com/en-us/windows/iot/getstarted) 페이지를 방문 하 여 보드를 설정 합니다.

설치는 빠르고 간단 합니다. 원격 디스플레이 기술을 사용 하려면 아래의 세 단계를 따르세요.

1. IoT Core 장치 및 개발 컴퓨터가 동일한 네트워크 및 n 보안 환경에 있는지 확인 합니다.

    한 가지 방법은 자동 교차를 지 원하는 USB 이더넷 어댑터를 사용 하 여 장치를 노트북에 직접 연결 하는 것입니다.

1. Windows 10 IoT Core 장치에서 원격 표시 기능을 켭니다.
  
    장치를 인터넷에 연결 하 고 Windows 장치 포털에 연결 합니다.
  
    왼쪽의 옵션에서 "원격" 페이지를 선택 하 고 "Window IoT 원격 서버 사용" 이라는 확인란을 선택 합니다.  이제 장치가 원격 디스플레이 환경에서 사용 하도록 설정 되었습니다.
    원격 표시 환경을 사용 하도록 설정 ![](../media/RemoteDisplay/enable-remote.png)

1. Windows IoT 원격 클라이언트를 부록 Windows 10 장치에 설치 합니다.
  
    Windows 10 장치를 Windows 10 IoT Core 장치에 연결할 수 있도록 하려면 스토어 응용 프로그램을 설치 해야 합니다.  Windows IoT 원격 클라이언트 앱은 현재 링크만 사용할 수 있으며 [여기](https://www.microsoft.com/en-us/store/apps/iot-remote-client/9nblggh5mnxz)에서 찾을 수 있습니다.
    
    ![클라이언트 앱 설치](../media/RemoteDisplay/store-app.png)


1. 설치 된 응용 프로그램을 통해 Windows 10 IoT Core 장치에 연결 합니다.
  
    Windows 10 자매 장치에서 Windows IoT 원격 클라이언트 응용 프로그램을 실행 합니다.  연결 화면에서 장치의 IP 주소를 입력 합니다. 두 장치는 연결 하 고, Windows 10 IoT Core 장치의 UI 환경을 도우미 장치에 원격으로 연결 해야 합니다.
    
    이제 연결 되었습니다! 이 시점부터 터치 하 고 Windows 10 장치에서 입력을 클릭 하면 Windows 10 IoT Core UWP 응용 프로그램을 제어 하는 데 사용할 수 있습니다.  
    ![장치 연결](../media/RemoteDisplay/connect-device.png)
      

## <a name="compatibility-and-scope"></a>호환성 및 범위
___
IoT 원격 클라이언트를 사용 하려면 대상 장치 및 스토어의 최신 클라이언트 응용 프로그램에서 Windows 10 IoT Core의 최신 빌드를 실행 해야 합니다. 
    
  
## <a name="troubleshooting"></a>문제 해결
___
원격 표시 기술을 사용 하는 것은 쉽고 간단 하지만 사용자에 게 발생할 수 있는 몇 가지 문제가 있습니다.  위의 설정 지침을 면밀 하 게 확인 하세요. 문제가 지속 되 면 아래를 확인 하세요.

### <a name="when-i-try-to-connect-the-client-app-goes-to-a-white-screen"></a>연결 하려고 하면 클라이언트 앱이 흰색 화면으로 이동 합니다.
실패 한 연결은 여러 가지 문제로 인해 발생할 수 있지만 몇 가지 일반적인 문제가 있습니다.

1. 최신 참가자 버전의 Windows 10 IoT Core 및 IoT 원격 클라이언트 응용 프로그램을 실행 중인지 확인 합니다.
1. 먼저 IoT 장치가 사용자의 도우미 장치와 동일한 네트워크에 있는지 확인 합니다.
    Windows IoT 원격 서버를 사용 하도록 설정 하 여 Windows 10 IoT Core의 최신 Insider build를 실행 하 고 있는지 확인 합니다.
1. 이 문제가 발생 하지 않는 경우, 위의 설정 섹션 1 단계에 있는 지침에 따라 장치의 웹 서버를 탐색 하는 것이 좋습니다.  왼쪽의 메뉴에서 "원격"을 선택 하는 대신 "홈" 페이지를 그대로 유지 하 고 아래로 스크롤하여 해상도를 확인 합니다.  800x600.
1. 그래도 문제가 해결 되지 않으면 장치를 외부 디스플레이에 연결 하지 않는 문제가 발생할 수 있습니다.
    이로 인해 장치는 완전히 헤드리스로 간주 됩니다.  이 문제를 해결하려면:
    * 마이크로 Sd 카드를 꺼내고 컴퓨터에 배치 합니다.
    * `<MicroSD card drive>:\config.txt` 편집
    * 다음 줄을 추가 합니다.
 
```
  hdmi_force_hotplug=1
  hdmi_group=2
  hdmi_mode=9
```
