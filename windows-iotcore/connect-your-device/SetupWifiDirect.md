---
title: Windows 10 Iot Core 장치에서 WiFi Direct를 사용 하 여
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 설치, 테스트 및 활성화 된 USB 어댑터를 사용 하 여 장치에서 wifi direct를 사용 하는 방법에 알아봅니다.
keywords: windows iot "," wifi 직접 "," 설치 "," wifi "," 장치
ms.openlocfilehash: 04ecf1820356c59fecea81be47f69617ab42ab36
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513405"
---
# <a name="using-wifi-direct-on-your-windows-10-iot-core-device"></a>Windows 10 IoT Core 장치에서 WiFi Direct를 사용 하 여

WiFi 직접 지원 되는 WiFi 직접 사용 하 여 장치에서 Windows 10 IoT Core USB 어댑터를 사용 합니다. WiFi 직접 두 가지 작업을 사용 하도록 설정된 되었는지 확인 하려면 true 여야 합니다.
* USB 어댑터의 하드웨어를 WiFi Direct를 지원 해야 합니다.
* USB 어댑터의 해당 하는 드라이버는 WiFi Direct를 지원 해야 합니다. 

WiFi 직접 연결을 설정 하거나 무선 액세스 지점 (무선 AP)에 대 한 필요 없이 WiFi 장치-장치 연결에 대 한 솔루션을 제공 합니다. 사용 가능한 UWP Api를 살펴보세요를 [Windows.Devices.WiFiDirect 네임 스페이스](https://msdn.microsoft.com/library/windows/apps/windows.devices.wifidirect.aspx) WiFiDirect를 사용 하 여 수행할 수 있는 작업을 확인 합니다.

## <a name="supported-adapters"></a>지원 되는 어댑터

Windows 10 IoT Core 테스트 된 WiFi 어댑터 목록을 복지부 우리의 [지원 되는 하드웨어](../learn-about-hardware/HardwareCompatList.md) 페이지. 

## <a name="basic-sample-for-wifi-direct"></a>WiFi Direct에 대 한 기본 샘플

WiFi 직접 UWP를 사용 하 여 WiFi 직접 기능을 쉽게 테스트할 수 있습니다 [샘플](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WiFiDirect)합니다. 사용 하 여는 C# 버전 및 두 개의 장치의 샘플을 실행 합니다.

### <a name="set-up-the-two-devices"></a>두 개의 장치 설정
* MinnowBoardMax MBM () Windows 10 IoT Core 실행 (여기의 지침 참조), CanaKit WiFi 동글을 사용 하 여
* 모니터, 키보드 및 마우스를 MBM 연결
* 최신 Windows 10 1 주년 업데이트를 실행 하는 Windows 10 PC. PC (또는 랩톱) 해야 합니다 (예: Microsoft Surface) 지원 되는 WiFi 직접
* Windows 10 PC에서 Visual Studio 2017 설치
* 복제 또는 다운로드 WiFi 직접 UWP [샘플](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WiFiDirect)(GitHub 리포지토리의 루트가 [여기](https://github.com/Microsoft/Windows-universal-samples)).
* 부하는 C# 버전의 Visual Studio 2017에서 WiFi 직접 UWP 샘플

#### <a name="run-the-sample-on-the-two-devices"></a>두 장치에서 샘플을 실행 합니다.
* 샘플 컴파일 및 배포/실행 하는 MBM에서:

    * "솔루션 플랫폼" combobox "x86"으로 설정 합니다.
    * "실행" 드롭다운 목록에서 "원격 컴퓨터"를 선택 합니다.
    * (Ctrl-F5 키를 눌러 또는 "디버그" 메뉴에서 "디버깅 하지 않고 시작"을 선택 하 여) 디버깅 하지 않고는 MBM에서 샘플 시작
    * MBM 연결 모니터에서 실행 되는 WiFi 직접 샘플을 표시
* 샘플 컴파일 및 배포/실행 하는 Windows 10 PC에서:
    * "솔루션 플랫폼" combobox "x86"으로 설정 합니다.
    * "실행" 드롭다운에서 "Local" 선택
    * (F5 또는 ctrl+f5) 샘플 시작
    * Windows 10 PC에서 실행 되는 WiFi 직접 샘플을 표시

### <a name="set-up-advertiser-and-connector"></a>광고 및 커넥터 설정
* MBM에서 (1) "광고"를 선택 하 고 "광고 시작" 단추

    * 자체 WiFi 직접 채널에서 광고를 MBM 시작

        ![광고 구성 화면](../media/SetupWiFiDirect/Advertiser01.png)

        앱의 맨 아래에 "보급 알림 상태" 배너를 확인 합니다.
    
* Windows 10 PC에서 (2) "커넥터"를 선택 하 고 "감시자 시작" 단추 

    * Windows 10 PC는 사용 가능한 WiFi 직접 연결에 대 한 검색을 시작합니다
    * 검색이 완료 되 면 "검색 된 장치" 목록의 MBM 프로그램의 이름을 표시 됩니다.

        ![커넥터 구성 화면](../media/SetupWiFiDirect/Connector01.png)

        나열 된 두 개의 장치를 볼 수 있습니다 (에 관심이 "ale mbm01"), 및 "DeviceWatcher 열거형 완료" 메시지입니다.

### <a name="pair-the-devices"></a>장치 쌍
* Windows 10 PC에서 "검색 된 장치" 목록의 MBM ("ale-mbm01" 예제의)를 선택 하 고 "연결" 단추를 눌러
* Windows 10 PC에 연결 하는 프로세스를 시작 하려면 "예" 키를 누릅니다.

    ![커넥터 시작 페어링](../media/SetupWiFiDirect/Connector02.png)

* PIN 사용 하 여 메시지를 수행 해야 MBM 모니터

    ![광고 PIN 대화 상자](../media/SetupWiFiDirect/Advertiser02.png)

* Windows 10 PC에서 하는 대화 상자가 표시 됩니다 PIN을 입력 해야 하는

    ![커넥터 핀 대화 상자](../media/SetupWiFiDirect/Connector03.png)

### <a name="talk-on-the-channel"></a>채널에서 통신 합니다.
* 두 개의 장치를 연결 되어야 합니다. 임의로 생성 된 장치 id (이 예제의 경우 "hqffpzhz.ggg") "연결 된 장치" 목록의 양쪽 화면에 표시 됩니다.

    ![광고 연결 된 장치](../media/SetupWiFiDirect/Advertiser03.png)

    ![커넥터 연결 된 장치](../media/SetupWiFiDirect/Connector04.png)

* 이제는 전체 이중 채널 (또는 소켓) 설정

    * MBM, 장치 ("hqffpzhz.ggg") "연결 된 장치" 목록에서 선택
    * "메시지를 입력 합니다." 텍스트 상자에 메시지를 입력 합니다.
    * "보내기" 단추를 클릭
    * Windows 10 PC에서 수신 되는 메시지가 표시 됩니다.
    * Windows 10 PC에서 MBM는 메시지를 보내기 시도
