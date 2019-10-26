---
title: Windows 10 IoT Core 장치에서 WiFi 사용
ms.date: 08/28/2017
ms.topic: article
description: Windows 10 IoT Core 장치에서 wifi를 사용, 설정 및 구성 하는 방법에 대해 알아봅니다.
keywords: windows iot, wifi, 설정, 장치
ms.openlocfilehash: b8fa691da0560a741c0078d0030f10ae4ceb6c17
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918295"
---
# <a name="using-wifi-on-your-windows-10-iot-core-device"></a>Windows 10 IoT Core 장치에서 WiFi 사용

WiFi는 USB WiFi 어댑터를 사용 하 여 Windows 10 IoT Core 장치에서 지원 됩니다. WiFi를 사용 하면 [SSH](../connect-your-device/SSH.md), [Powershell](../connect-your-device/PowerShell.md), [Windows 장치 포털](../manage-your-device/DevicePortal.md), 응용 프로그램 디버깅 및 배포를 포함 하 여 유선 연결의 모든 기능을 제공 합니다.

> [!NOTE]
> 유선 이더넷 케이블을 꽂으면 기본 네트워크 인터페이스로 WiFi가 재정의 됩니다.

### <a name="supported-adapters"></a>지원 되는 어댑터
Windows 10 IoT Core에서 테스트 된 WiFi 어댑터의 목록은 [지원 되는 하드웨어](../learn-about-hardware/HardwareCompatList.md) 페이지에서 찾을 수 있습니다.

### <a name="configuring-wifi"></a>WiFi 구성
WiFi를 사용 하려면 WiFi 네트워크 자격 증명을 사용 하 여 Windows 10 IoT core를 제공 해야 합니다. 도우미 앱 및 WPS 사용자 지정 솔루션을 빌드하는 방법에 대 한 설명서 외에도 아래에 나열 된 몇 가지 다른 옵션이 있습니다.

## <a name="custom-companion-app--wps-wi-fi-onboarding-samples"></a>사용자 지정 도우미 앱 & WPS Wi-fi 온 보 딩 샘플

현재는 개발자가 자신의 장치에 대 한 사용자 지정 wifi 온 보 딩 솔루션을 빌드하는 다양 한 방법을 제공 합니다. 

> | 샘플 | 설명 | 장점  |  단점  |
> |-------------|----------|---------|---------|
> | [도우미 앱](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/CompanionApp) | 장치의 Wi-fi를 구성할 수 있는 간단한 Xamarin 앱을 만듭니다. |  간단히 사용할 수 있습니다. IoT Core 용으로 또는 헤드리스 클라이언트가 플랫폼 간 작동 | 개발자가 자체 프로토콜을 만들고 있습니다. 개발자가 보안을 구현 하도록 요구 |
> | [Bluetooth RFCOMM를 사용 하 여 IoT 온 보 딩](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/IoTOnboarding_RFCOMM) | Bluetooth RFCOMM를 사용 하 여 Wi-fi에 연결 하도록 헤드리스 IoT 장치를 구성 하는 솔루션을 만듭니다.  | I 또는 헤드리스 장치에서 관련 익숙한 기술 및 개념을 사용 합니다. IoT 장치가 SoftAP을 시작할 필요가 없습니다. 방화벽 설정을 조정할 필요가 없습니다. | 클라이언트 및 서버 장치에 대 한 Bluetooth 지원이 필요 합니다. 샘플은 Windows 10 용 클라이언트 앱만 제공 합니다. 서버 앱은 클라이언트 장치 이름을 미리 정의 하거나 하드 코드 합니다. |
> | [AllJoyn를 사용 하 여 IoT 온 보 딩](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/IoTOnboarding) | 사용자의 헤드리스 IoT 장치를 홈 Wi-fi 네트워크와 원격으로 연결 합니다. | AllJoyn에서 작동 | 일부 AllJoyn 지원은 사용 되지 않습니다. |
> | 장치용 wi-fi 보호 설치 (WPS) Api | WPS 검색을 수행 하 여 네트워크에서 지원 되는 WPS 메서드를 쿼리 합니다. | [WiFiAdapter GetWpsConfigurationAsync (WiFiAvailableNetwork](https://docs.microsoft.com/uwp/api/windows.devices.wifi.wifiadapter.getwpsconfigurationasync) 및 [WiFiAdapter](https://docs.microsoft.com/uwp/api/windows.devices.wifi.wifiadapter.connectasync) 메서드를 활용 하 여 wi-fi 장치를 특정 네트워크에 연결 하기만 하면 됩니다. | 이러한 Api를 활용 하려면 이러한 Api에 대해 잘 알고 있어야 합니다. WPS 사용 라우터와만 호환 됩니다.|

## <a name="headed-options"></a>옵션:

### <a name="option-1-startup-configuration"></a>옵션 1: 시작 구성
**필수 구성 요소:** Windows 10 IoT core 장치에는 연결 된 마우스, 키보드, 디스플레이 및 USB WiFi 어댑터가 필요 합니다.

지원 되는 USB WiFi 어댑터를 사용 하 여 Windows 10 IoT Core를 처음 부팅할 때 구성 화면이 표시 됩니다.
구성 화면에서 연결할 WiFi 네트워크를 선택 하 고 암호를 제공 합니다. 연결 **을 클릭 하** 여 연결을 시작 합니다.

![시작 WiFi 구성 화면](../media/SetupWiFi/WiFiStartupConfig.png)

### <a name="option-2-default-app-configuration"></a>옵션 2: 기본 앱 구성
**필수 구성 요소:** Windows 10 IoT core 장치에는 연결 된 마우스, 키보드, 디스플레이 및 USB WiFi 어댑터가 필요 합니다.

WiFi를 구성 하는 다른 방법은 기본 앱을 사용 하는 것입니다. 장치가 부팅 된 후이를 사용 하 여 WiFi 설정을 구성 하거나 수정할 수 있습니다.

1. 홈페이지에서 기어 모양의 설정 아이콘을 클릭 합니다.
2. 왼쪽 창에서 **네트워크 & wi-fi** 를 선택 합니다.
3. 연결 하려는 WiFi 네트워크를 클릭 합니다. 메시지가 표시 되 면 암호를 입력 하 고 **연결** 을 클릭 합니다.

![기본 앱 WiFi 구성](../media/SetupWiFi/DefaultAppWiFiConfig.png)

## <a name="headless-options"></a>헤드리스 옵션:




### <a name="option-1-web-based-configuration"></a>옵션 1: 웹 기반 구성
**필수 구성 요소:** 장치는 이미 이더넷을 통해 로컬 네트워크에 연결 되어 있어야 하며 USB WiFi 어댑터가 연결 되어 있어야 합니다.

UI, 디스플레이 또는 입력 장치가 없는 장치 a를 사용 하는 경우에도 [Windows 장치 포털](../manage-your-device/DevicePortal.md)을 통해 장치를 구성할 수 있습니다.
**Windows 10 IoT Core 대시보드**에서 장치에 대 한 **장치 포털에서 열기** 아이콘을 *클릭* 합니다.

<!-- This content is replicated at en-US/Docs/KitSetupRPI.md -->

1. 사용자 이름에 **관리자** 를 입력 하 고 암호를 입력 합니다 (기본적으로p@ssw0rd).
2. 왼쪽 창에서 **네트워크** 를 클릭 합니다.
3. **사용 가능한 네트워크**에서 연결 하려는 네트워크를 선택 하 고 연결 자격 증명을 제공 합니다. 연결 **을 클릭 하** 여 연결을 시작 합니다.

![웹 기반 WiFi 구성](../media/SetupWiFi/WebBWiFiConfig.png)

<!-- End of Replicated Content -->


### <a name="option-2-connect-using-wifi-profiles"></a>옵션 2: WiFi 프로필을 사용 하 여 연결

**필수 구성 요소:** 장치는 이미 이더넷을 통해 로컬 네트워크에 연결 되어 있어야 하며 USB WiFi 어댑터가 연결 되어 있어야 합니다. 또한 WiFi 기능이 포함 된 Windows PC가 필요 합니다.

무선 프로필을 사용 하 여 WiFi를 설정 하는 것은 Windows 10 IoT Core에서 지원 됩니다. 자세한 내용과 예제는 [MSDN](https://msdn.microsoft.com/library/windows/desktop/aa369853) 을 참조 하세요.

1. Windows PC를 원하는 무선 네트워크에 연결 하 고 다음 명령을 사용 하 여 WiFi 프로필 XML 파일을 만듭니다.

    * `netsh wlan show profiles` > 방금 추가한 프로필의 이름을 찾습니다.

    * `netsh wlan export profile name=<your profilename>`을 참조하십시오. 그러면 프로필이 XML 파일로 내보냅니다.

2. **파일 탐색기** 창을 열고 주소 표시줄에 `\\<TARGET_DEVICE>\C$\`를 입력 한 다음 enter 키를 누릅니다.  이 특정 경우에 `<TARGET_DEVICE>`은 Windows 10 IoT Core 장치의 이름 또는 IP 주소입니다.

    ![파일 탐색기를 사용 하는 SMB](../media/SetupWifi/smb1.png)

    사용자 이름 및 암호를 입력 하 라는 메시지가 표시 되 면 다음 자격 증명을 사용 합니다.

        User Name: <TARGET_DEVICE>\Administrator
        Password:  p@ssw0rd

    ![파일 탐색기를 사용 하는 SMB](../media/SetupWifi/cred1.png)

> [!NOTE]
> 관리자 계정에 대 한 기본 암호를 업데이트 하는 것이 **좋습니다** .  [여기](../connect-your-device/PowerShell.md)에 있는 지침을 따르세요.

3. Windows PC에서 Windows 10 IoT Core 장치로 내보낸 WiFi 프로필 XML 파일을 복사 합니다.

4. [PowerShell](../connect-your-device/PowerShell.md) 을 사용 하 여 장치에 연결 하 고 다음 명령을 실행 하 여 장치에 새 WiFi 프로필을 추가 합니다.

    * `netsh wlan add profile filename=<copied XML path>`

    * `netsh wlan show profiles`

5. Netsh를 통해 Windows 10 IoT Core 장치를 무선 네트워크에 연결

    * `netsh wlan connect name=<profile name>`

6. 장치가 무선 네트워크에 연결 되어 있고 인터넷에 연결할 수 있는지 확인 합니다.

    * `netsh wlan show interfaces`

    * `ipconfig /all`

    * `ping /S <your WiFi adapter ip address> bing.com`


#### <a name="connecting-to-wpa2-psk-personal-networks"></a>WPA2-PSK 개인 네트워크에 연결

WPA2-PSK 개인 WiFi 네트워크에 연결 해야 하는 경우 먼저 위의 지침을 따르고 XML 파일을 다음과 같이 변경 합니다. 유일한 차이점은 Windows PC에서 XML을 내보낼 때 암호를 암호화 한다는 것입니다.

> [!WARNING] 
> 이렇게 하면 연결이 안전 하지 않게 됩니다.

Windows PC에서 내보낸 프로필 XML:

    <sharedKey>
        <keyType>passPhrase</keyType>
        <protected>true</protected>
        <keyMaterial><Your Encrypted password></keyMaterial>
    </sharedKey>


Windows 10 IoT Core에서 작업을 수행 하는 데 필요한 변경 사항:

    <sharedKey>
        <keyType>passPhrase</keyType>
        <protected>false</protected>
        <keyMaterial><Your Unencrypted password></keyMaterial>
    </sharedKey>
