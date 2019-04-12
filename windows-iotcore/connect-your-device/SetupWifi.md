---
title: Windows 10 IoT Core 장치에서 WiFi를 사용 하 여
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 사용, 설치 및 Windows 10 IoT Core 장치에서 wifi를 구성 하는 방법에 알아봅니다.
keywords: windows iot, wifi, 설치, 장치
ms.openlocfilehash: 20f61114323baa60c8052038df68a8c172ce1c95
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513398"
---
# <a name="using-wifi-on-your-windows-10-iot-core-device"></a>Windows 10 IoT Core 장치에서 WiFi를 사용 하 여

WiFi는 WiFi USB 어댑터를 사용 하 여 Windows 10 IoT Core 장치에서 지원 됩니다. WiFi를 사용 하 여 유선된 된 연결의 모든 기능을 제공 등 [SSH](../connect-your-device/SSH.md)를 [Powershell](../connect-your-device/PowerShell.md)를 [Windows Device Portal](../manage-your-device/DevicePortal.md), 응용 프로그램 디버깅 및 배포 합니다.

> [!NOTE]
> 유선된 이더넷 케이블을 연결의 기본 네트워크 인터페이스로 WiFi를 재정의 합니다.

### <a name="supported-adapters"></a>지원 되는 어댑터
Windows 10 IoT Core 테스트 된 WiFi 어댑터 목록을 복지부 우리의 [지원 되는 하드웨어](../learn-about-hardware/HardwareCompatList.md) 페이지.

### <a name="configuring-wifi"></a>WiFi 구성
WiFi를 사용 하려면 Windows 10 IoT core WiFi 네트워크 자격 증명을 제공 해야 합니다. 도우미 앱 및 WPS 사용자 지정 솔루션을 빌드하는 방법에 대 한 설명서, 외에도 따라서 아래에 나열 된 수행 하기 위한 몇 가지 옵션이 있습니다.

## <a name="custom-companion-app--wps-wi-fi-onboarding-samples"></a>사용자 지정 도우미 앱 및 WPS Wi-fi 온 보 딩 샘플

현재 다양 한 장치에 대 한 사용자 지정 wifi 온 보 딩 솔루션을 구축 하는 개발자를 위한 방법 제공 합니다. 

> | 샘플 | 설명 | 이점  |  단점  |
> |-------------|----------|---------|---------|
> | [도우미 앱](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/CompanionApp) | 장치의 Wi-fi를 구성할 수 있는 간단한 Xamarin 앱을 만듭니다. |  간단 하 게 지정 해야 합니다. 헤드 또는 IoT Core;에 대 한 헤드리스 클라이언트는 플랫폼 간 작동합니다. | 개발자가 자신의 프로토콜; 만드는 보안을 구현 하는 개발자 |
> | [Bluetooth RFCOMM를 사용 하 여 IoT 온 보 딩](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/IoTOnboarding_RFCOMM) | 헤드리스 IoT 장치에서 Wi-fi를 사용 하 여 연결을 구성 하는 솔루션을 만들 Bluetooth RFCOMM를 사용 하 여 합니다.  | 헤드 또는 헤드리스 장치에서 관련 친숙 한 기술 및 개념을 사용 하 여 IoT 장치 SoftAP;를 시작 하지 않아도 방화벽 설정을 조정할 필요가 없습니다. | 클라이언트 및 서버 장치에 대 한 Bluetooth 지원이 필요 샘플은 Windows 10에 대 한 클라이언트 앱 제공 서버 앱 사전-defines/하드 코드 클라이언트 장치의 이름입니다. |
> | [AllJoyn 사용 하 여 IoT 온 보 딩](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/IoTOnboarding) | 홈 Wi-fi 네트워크를 사용 하 여 헤드리스 IoT 장치를 원격으로 조인 합니다. | AllJoyn 사용 | AllJoyn에 대 한 지원이 사용 되지 않음 |
> | -Fi 보호 설정 (WPS) 장치에 대 한 Api | 네트워크에서 지 원하는 WPS 메서드 쿼리 WPS 검색을 수행 합니다. | 단순히 활용 합니다 [WiFiAdapter.GetWpsConfigurationAsync (WiFiAvailableNetwork](https://docs.microsoft.com/uwp/api/windows.devices.wifi.wifiadapter.getwpsconfigurationasync) 및 [WiFiAdapter.ConnectAsync](https://docs.microsoft.com/uwp/api/windows.devices.wifi.wifiadapter.connectasync) wi-fi 장치 특정 네트워크에 연결 하는 방법입니다. | 활용 하려면 이러한 Api를 사용 하 여 파악 해야 합니다.; WPS 사용 라우터를 사용 하 여 호환 될 뿐|

## <a name="headed-options"></a>헤드 옵션:

### <a name="option-1-startup-configuration"></a>옵션 1: 시작 구성
**필수 구성 요소:** Windows 10 IoT core 장치 마우스, 키보드, 표시 하며 USB 어댑터 연결

첫 번째 Windows 10 IoT Core 지원 되는 WiFi USB 어댑터를 사용 하 여 부팅 구성 화면이 표시 됩니다.
구성 화면에서 연결 하 고 암호를 입력 하려는 WiFi 네트워크를 선택 합니다. 클릭 **연결** 의 연결을 시작 합니다.

![시작 WiFi 구성 화면](../media/SetupWiFi/WiFiStartupConfig.png)

### <a name="option-2-default-app-configuration"></a>옵션 2: 기본 앱 구성
**필수 구성 요소:** Windows 10 IoT core 장치 마우스, 키보드, 표시 하며 USB 어댑터 연결

WiFi를 구성 하는 다른 방법은 기본 앱을 사용 하는 것입니다. 이 설정을 구성 하거나 수정할 WiFi 장치가 부팅 한 후에 사용할 수 있습니다.

1. 홈 페이지에서 기어 모양의 설정 아이콘 클릭
2. 선택 **네트워크 및 Wi-fi** 왼쪽된 창에서
3. 에 연결 하려는 WiFi 네트워크를 클릭 합니다. 메시지가 표시 되 면 암호를 입력 하 고 클릭 **연결**

![기본 앱 WiFi 구성](../media/SetupWiFi/DefaultAppWiFiConfig.png)

## <a name="headless-options"></a>헤드리스 옵션:




### <a name="option-1-web-based-configuration"></a>옵션 1: 웹 기반 구성
**필수 구성 요소:** 장치에 이미 이더넷을 통해 로컬 네트워크에 연결 해야 하 고 해야 WiFi USB 어댑터를 연결한 없는

장치가 있는 경우는 UI, 표시 또는 입력된 장치를 사용 하 여 구성할 수 있습니다 통해 합니다 [Windows Device Portal](../manage-your-device/DevicePortal.md)합니다.
**Windows 10 IoT Core 대시보드**를 *클릭* 에 **장치 포털에서 열기** 장치에 대 한 아이콘입니다.

<!-- This content is replicated at en-US/Docs/KitSetupRPI.md -->

1. 입력 **관리자** 사용자 이름에 대 한 사용자 암호를 입력 하 고 (p@ssw0rd 기본적으로)
2. 클릭할 **네트워크** 왼쪽 창에서
3. 아래 **사용 가능한 네트워크**선택, 네트워크에 연결 하 고 연결 자격 증명을 제공 합니다. 클릭 **Connect** 연결 시작 하려면

![웹 기반 WiFi 구성](../media/SetupWiFi/WebBWiFiConfig.png)

<!-- End of Replicated Content -->


### <a name="option-2-connect-using-wifi-profiles"></a>옵션 2: Wi-fi 프로필을 사용 하 여 연결

**필수 구성 요소:** 장치에 이미 이더넷을 통해 로컬 네트워크에 연결 해야 하 고 해야 WiFi USB 어댑터를 연결한 없는 합니다. WiFi 기능을 사용 하 여 Windows PC를 해야합니다.

무선 프로필을 사용 하 여 WiFi 설정는 Windows 10 IoT Core 지원 됩니다. 참조 [MSDN](https://msdn.microsoft.com/library/windows/desktop/aa369853) 세부 정보 및 예제입니다.

1. Windows PC를 원하는 무선 네트워크에 연결 하 고 이러한 명령을 사용 하 여 WiFi 프로필 XML 파일을 만듭니다.

    * `netsh wlan show profiles` -> 방금 추가한 프로필의 이름 찾기

    * `netsh wlan export profile name=<your profilename>`. 프로필을 XML 파일로 내보냅니다.

2. 엽니다는 **파일 탐색기** 창에 주소 표시줄 유형 `\\<TARGET_DEVICE>\C$\` 및 입력 한 다음 키를 누릅니다.  이 특정 예제의 `<TARGET_DEVICE>` 이름 또는 Windows 10 IoT Core 장치 IP 주소 중 하나:

    ![파일 탐색기를 사용 하 여 SMB](../media/SetupWifi/smb1.png)

    사용자 이름 및 암호에 대 한 메시지가 표시 되 면 다음 자격 증명을 사용 합니다.

        User Name: <TARGET_DEVICE>\Administrator
        Password:  p@ssw0rd

    ![파일 탐색기를 사용 하 여 SMB](../media/SetupWifi/cred1.png)

> [!NOTE]
> 것 **좋습니다** 관리자 계정에 대 한 기본 암호를 업데이트 하는 합니다.  지침을 따르세요 [여기](../connect-your-device/PowerShell.md)합니다.

3. Windows 10 IoT Core 장치에 Windows PC에서 내보낸된 WiFi 프로필 XML 파일을 복사

4. 사용 하 여 장치에 연결할 [PowerShell](../connect-your-device/PowerShell.md) 하 고 다음 명령을 실행 하 여 장치에 새 Wi-fi 프로필 추가

    * `netsh wlan add profile filename=<copied XML path>`

    * `netsh wlan show profiles`

5. Windows 10 IoT Core 장치 netsh 통해 무선 네트워크에 연결

    * `netsh wlan connect name=<profile name>`

6. 장치의 무선 네트워크에 연결 되어 및 인터넷에 연결할 수 있는지를 확인 합니다.

    * `netsh wlan show interfaces`

    * `ipconfig /all`

    * `ping /S <your WiFi adapter ip address> bing.com`


#### <a name="connecting-to-wpa2-psk-personal-networks"></a>WPA2-PSK 개인 네트워크에 연결

WPA2-PSK 개인 WiFi 네트워크에 연결 해야 하는 경우 위의 지침을 먼저 수행 하지만 XML 파일에 다음과 같이 변경 합니다. 유일한 차이점은 Windows PC XML을 내보낼 때 암호화 암호입니다.

> [!WARNING] 
> 이렇게 하면 연결이 안전 하지 않은 합니다.

Windows PC에서 내보낸 되는 XML 프로필:

    <sharedKey>
        <keyType>passPhrase</keyType>
        <protected>true</protected>
        <keyMaterial><Your Encrypted password></keyMaterial>
    </sharedKey>


Windows 10 IoT Core 작동 하는 데 필요한 변경 내용:

    <sharedKey>
        <keyType>passPhrase</keyType>
        <protected>false</protected>
        <keyMaterial><Your Unencrypted password></keyMaterial>
    </sharedKey>
