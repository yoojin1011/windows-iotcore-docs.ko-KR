---
title: 원격 표시
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 보기 및 Windows 10 IoT Core UWP 응용 프로그램을 원격으로 제어 하는 방법에 알아봅니다.
keywords: windows iot, UWP, 표시 되는 원격 원격 UWP 응용 프로그램
ms.openlocfilehash: 6f46ddbc5738f377ce3ebd15a49785e27c6a40bf
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513373"
---
# <a name="remote-display"></a>원격 표시
보기 및 Windows 10 데스크톱 PC, 태블릿 또는 휴대폰에서 Windows 10 IoT Core UWP 응용 프로그램을 원격으로 제어

> [!WARNING]
> Windows IoT 원격 클라이언트 개발자 유일한 기능입니다. 사용 하거나 프로덕션 장치에 대 한 지원 되 는지 않습니다.

> [!IMPORTANT]
> Raspberry Pi에 대 한 Windows IoT 원격 클라이언트 작동 하지 않습니다. 보드를 사용 하 여 가속된 그래픽 Minnowboard 최대 Dragonboard 등을 사용 하 여 또는 로컬 표시에 대 한 모니터를 연결 합니다.

## <a name="overview"></a>개요
___
표시 하는 원격 환경에는 Windows 10 IoT Core 장치에서 실행 하는 UWP 응용 프로그램을 원격으로 제어 하는 데 개발자 도구입니다.   

## <a name="setup"></a>설치 프로그램
___
Windows 10의 최신 빌드를 사용 하 여 Windows 10 IoT Core 장치를 설정 하려면 방문 해야 시작 하는 [시작](https://developer.microsoft.com/en-us/windows/iot/getstarted) 보드를 설정 하는 페이지입니다.

설치 프로그램을 쉽고 빠르게-표시 하는 원격 기술을 사용 하 여 다음 세 가지 단계를 수행 합니다.

1. IoT Core 장치 및 개발 컴퓨터는 보안 환경에 동일한 네트워크에 n을 확인 합니다.

    한 가지 방법은 자동 교차를 지 원하는 USB 이더넷 어댑터를 사용 하 여 랩톱에 직접 장치를 연결 하는 것입니다.

1. Windows 10 IoT Core 장치에 표시 하는 원격 기능을 켭니다.
  
    장치를 인터넷에 연결 하 고 Windows Device Portal 연결 합니다.
  
    왼쪽의 옵션에서 "원격" 페이지를 선택 하 고 "창 IoT 원격 서버 사용" 라는 레이블이 있는 확인란을 표시 합니다.  장치는 이제 표시 하는 원격 환경을 사용 하도록 설정 됩니다.
    ![표시 하는 원격 환경을 사용 하도록 설정](../media/RemoteDisplay/enable-remote.png)

1. 관련 Windows 10 장치에서 Windows IoT 원격 클라이언트를 설치 합니다.
  
    Windows 10 IoT Core 장치에 연결 하는 Windows 10 장치를 사용 하려면 저장소 응용 프로그램을 설치 해야 합니다.  Windows IoT 원격 클라이언트 앱은 현재 링크로 사용할 수 하 고 확인할 수 있습니다 [여기](https://www.microsoft.com/en-us/store/apps/iot-remote-client/9nblggh5mnxz)합니다.
    
    ![클라이언트 앱 설치](../media/RemoteDisplay/store-app.png)


1. 설치 된 응용 프로그램을 통해 Windows 10 IoT Core 장치에 연결 합니다.
  
    Windows 10 관련 장치에서 Windows IoT 원격 클라이언트 응용 프로그램을 실행 합니다.  연결 화면에 장치의 IP 주소를 입력 합니다. 두 개의 장치 연결 해야, 원격 포함 장치는 Windows 10 IoT Core 장치의 UI 경험 합니다.
    
    지금 연결! 이 지점에서 전달, 터치 하 고 제공 된 Windows 10 장치를 사용 하 여 Windows 10 IoT Core UWP 응용 프로그램을 제어할 수에서 입력을 클릭 합니다.  
    ![장치 연결](../media/RemoteDisplay/connect-device.png)
      

## <a name="compatibility-and-scope"></a>호환성 및 범위
___
IoT 원격 클라이언트를 사용 하기 위해 실행 해야 Windows 10 IoT Core 최신 빌드 대상 장치에 최신 클라이언트 응용 프로그램 스토어에서. 
    
  
## <a name="troubleshooting"></a>문제 해결
___
표시 하는 원격 기술을 사용 하는 빠르고 쉬우며 있지만 여전히 사용자가 겪을 수 있는 몇 가지 문제가 있습니다.  위의 지침-밀접 하 게 문제가 지속 되 면 확인 아래 설치를 수행 해야 합니다.

### <a name="when-i-try-to-connect-the-client-app-goes-to-a-white-screen"></a>연결 하려고 할 때 클라이언트 앱 흰색 화면으로 이동 합니다.
실패 한 연결은 다양 한 문제를 발생할 수 있습니다 하지만 몇 가지 일반적인 문제를를 실행 했습니다.

1. Windows 10 IoT Core 버전 및 IoT 원격 클라이언트 응용 프로그램이 최신 참가자를 실행 하는 것을 확인 합니다.
1. 먼저, 부록 장치와 같은 네트워크에는 IoT 장치 해야 합니다.
    Windows 10 IoT Core 최신 참가자 빌드를 사용 하도록 설정 하 여 Windows IoT 원격 서버를 사용 하 여 실행 중인지 확인 합니다.
1. 문제가 없으면 장치를 지원 하도록 보장할 것의 해상도 장치의 웹 서버로 이동할 위의 설치 섹션의 1 단계에서 지침에 따라를 변경해 보세요.  왼쪽 메뉴에서 "Remote"를 선택 하는 대신 "홈" 페이지에 머무는 및 해상도 찾으려면 아래로 스크롤합니다.  800 x 600을 시도 합니다.
1. 여전히이 문제가 해결 되지 않으면, 되지 외장 디스플레이에 장치를 연결에서 발생 하는 문제를 할 수 있습니다.
    이렇게 하면 순수 하 게 헤드리스으로 자체 생각 하면 장치.  이 문제를 해결하려면:
    * MicroSD 카드를 배출 하 고 컴퓨터에 배치
    * 편집 된 `<MicroSD card drive>:\config.txt`
    * 다음 줄을 추가 합니다.
 
```
  hdmi_force_hotplug=1
  hdmi_group=2
  hdmi_mode=9
```
