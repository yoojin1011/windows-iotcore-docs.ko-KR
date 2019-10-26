---
title: Windows 10 Iot Core 장치에서 WiFi Direct 사용
ms.date: 08/28/2017
ms.topic: article
description: USB wifi 어댑터를 사용 하는 장치에서 wifi direct를 설정, 테스트 및 사용 하는 방법을 알아봅니다.
keywords: windows iot, wifi direct, 설정, wifi, 장치
ms.openlocfilehash: 7355d5d0879b2a0f31f5fa89eb00e71eb0fa4e4f
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918284"
---
# <a name="using-wifi-direct-on-your-windows-10-iot-core-device"></a>Windows 10 IoT Core 장치에서 WiFi Direct 사용

Wifi direct는 WiFi Direct가 설정 된 USB WiFi 어댑터를 사용 하 여 Windows 10 IoT Core 장치에서 지원 됩니다. WiFi Direct가 사용 하도록 설정 되었는지 확인 하려면 다음 두 가지를 충족 해야 합니다.
* USB WiFi 어댑터의 하드웨어는 WiFi Direct를 지원 해야 합니다.
* USB WiFi 어댑터의 해당 드라이버는 WiFi Direct를 지원 해야 합니다. 

WiFi Direct는 무선 AP (무선 액세스 지점)를 사용 하 여 연결을 설정할 필요 없이 WiFi 장치-장치 연결에 대 한 솔루션을 제공 합니다. WiFiDirect로 수행할 수 있는 작업을 확인 하려면 [WiFiDirect 네임 스페이스](https://msdn.microsoft.com/library/windows/apps/windows.devices.wifidirect.aspx) 에서 제공 하는 UWP api를 살펴보세요.

## <a name="supported-adapters"></a>지원 되는 어댑터

Windows 10 IoT Core에서 테스트 된 WiFi 어댑터의 목록은 [지원 되는 하드웨어](../learn-about-hardware/HardwareCompatList.md) 페이지에서 찾을 수 있습니다. 

## <a name="basic-sample-for-wifi-direct"></a>WiFi Direct 용 기본 샘플

Wifi Direct UWP [샘플](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WiFiDirect)을 사용 하 여 wifi direct 기능을 쉽게 테스트할 수 있습니다. C# 버전을 사용 하 고 두 개의 장치에 대 한 샘플을 실행 합니다.

### <a name="set-up-the-two-devices"></a>두 장치 설정
* MinnowBoardMax (MBM) Windows 10 IoT Core를 실행 하 고 있습니다 (지침 참조), CanaKit WiFi 동글을 사용
* 모니터, 키보드 및 마우스를 MBM에 연결
* 최신 Windows 10 기념일 업데이트를 실행 하는 Windows 10 PC입니다. PC (또는 랩톱)에는 WiFi Direct 지원이 있어야 합니다 (예: Microsoft Surface).
* Windows 10 PC에 Visual Studio 2017 설치
* WiFi Direct UWP [샘플](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WiFiDirect)(GitHub 리포지토리의 루트는 [여기](https://github.com/Microsoft/Windows-universal-samples)에 있습니다)을 복제 하거나 다운로드 합니다.
* Visual Studio C# 2017에서 WIFI Direct UWP 샘플의 버전을 로드 합니다.

#### <a name="run-the-sample-on-the-two-devices"></a>두 장치에서 샘플 실행
* 샘플을 컴파일하고 MBM에서 배포/실행 합니다.

    * "솔루션 플랫폼" combobox를 "x86"으로 설정 합니다.
    * "실행" 드롭다운에서 "원격 컴퓨터"를 선택 합니다.
    * Ctrl + F5 키를 누르거나 "디버그" 메뉴에서 "디버깅 하지 않고 시작"을 선택 하 여, 디버깅 하지 않고 MBM에서 샘플을 시작 합니다.
    * MBM에 연결 된 모니터에서 실행 중인 WiFi Direct 샘플이 표시 됩니다.
* 샘플을 컴파일하고 Windows 10 PC에서 배포/실행 합니다.
    * "솔루션 플랫폼" combobox를 "x86"으로 설정 합니다.
    * "실행" 드롭다운에서 "로컬"을 선택 합니다.
    * 샘플 (F5 또는 Ctrl + F5)을 시작 합니다.
    * Windows 10 PC에서 실행 되는 WiFi Direct 샘플이 표시 됩니다.

### <a name="set-up-advertiser-and-connector"></a>광고주 및 커넥터 설정
* MBM에서 (1) "광고주"를 선택 하 고 "보급 알림 시작" 단추를 누릅니다.

    * MBM이 WiFi Direct 채널에서 자체 보급을 시작 합니다.

        ![광고주 구성 화면](../media/SetupWiFiDirect/Advertiser01.png)

        앱 아래쪽의 "보급 알림 상태" 배너를 확인 합니다.
    
* Windows 10 PC에서 (2) "커넥터"를 선택 하 고 "감시자 시작" 단추를 누릅니다. 

    * 사용 가능한 WiFi 직접 연결에 대 한 검색을 시작 하는 Windows 10 PC
    * 검색이 완료 되 면 "검색 된 장치" 목록에 MBM 이름이 표시 됩니다.

        ![커넥터 구성 화면](../media/SetupWiFiDirect/Connector01.png)

        표시 되는 두 개의 장치 ("mbm01"에 관심 있음)와 "DeviceWatcher 열거 완료" 메시지가 표시 됩니다.

### <a name="pair-the-devices"></a>장치 페어링
* Windows 10 PC의 "검색 된 장치" 목록에서 MBM (이 예제에서는 "ale-mbm01")을 선택 하 고 "연결" 단추를 누릅니다.
* Windows 10 PC에서 "예"를 눌러 페어링 프로세스를 시작 합니다.

    ![커넥터 시작 페어링](../media/SetupWiFiDirect/Connector02.png)

* MBM 모니터에서 PIN을 포함 하는 메시지가 표시 됩니다.

    ![광고주 고정 대화 상자](../media/SetupWiFiDirect/Advertiser02.png)

* Windows 10 PC에서 PIN을 입력 해야 하는 대화 상자가 표시 됩니다.

    ![커넥터 고정 대화 상자](../media/SetupWiFiDirect/Connector03.png)

### <a name="talk-on-the-channel"></a>채널에 대 한 대화
* 두 장치를 연결 해야 합니다. "연결 된 장치" 목록의 두 화면에 임의로 생성 된 장치 id (이 예제에서는 "hqffggg")가 표시 됩니다.

    ![광고주 연결 장치](../media/SetupWiFiDirect/Advertiser03.png)

    ![커넥터 연결 장치](../media/SetupWiFiDirect/Connector04.png)

* 이제 전체 이중 채널 (또는 소켓)이 설정 되었습니다.

    * MBM의 "연결 된 장치" 목록에서 장치 ("hqffggg")를 선택 합니다.
    * "메시지 입력" 텍스트 상자에 메시지를 입력 합니다.
    * "보내기" 단추를 누릅니다.
    * Windows 10 PC에서 메시지가 수신 되는 것을 볼 수 있습니다.
    * Windows 10 PC에서 MBM으로 메시지를 전송 해 보세요.
