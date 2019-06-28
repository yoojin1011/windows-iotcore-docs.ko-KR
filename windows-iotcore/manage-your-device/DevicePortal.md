---
title: Windows Device Portal
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: Windows Device Portal 사용 하 여 구성 하 고 장치를 원격으로 관리 하는 방법에 알아봅니다.
keywords: windows iot, Windows Device Portal, 원격 장치 포털
ms.openlocfilehash: 8e430365ea09509f5638d86ac77b151226df488f
ms.sourcegitcommit: 8932969dc50805113c330bc2ba6ec9003d067b3c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67412157"
---
# <a name="windows-device-portal"></a>Windows Device Portal
   Windows Device Portal (WDP)를 사용 하 여 구성 하 고 로컬 네트워크를 통해 장치를 원격으로 관리할 수 있습니다.
주요 기능에 설명 되어는 [Windows Device Portal 개요 페이지](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal)

![장치 포털 홈](../media/deviceportal/deviceportal.png)

> [!IMPORTANT]
> 상용화에 제조사 이미지를 사용하지 마세요. 디바이스를 상용화하려는 경우 최적의 보안을 위해 사용자 지정 FFU를 사용해야 합니다. [여기](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)에서 자세한 내용을 알아보세요.

> [!WARNING]
> 현재 라이브 커널 디버그 ARM 장치에 대 한 실패 합니다. 고정이 노력 합니다.

> [!IMPORTANT]
> "특정/제한 installation"에 상용 배포에 대 한 열기 소매용 장치를 빌드하는 경우 (예:: factory 또는 소매 저장소)는 최종 사용자가 최종 구성을 수행 하 고 시켜야 하는 고객을 문서 [가져올를 WDP 변경 되 WDP 및 연결 브라우저와 암호에 WDP 및 설치에 대 한 인증서](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-ssl), WDP를 사용 하 여 좁은 상용 인스턴스에서이 허용 됩니다. 이 시나리오에서는 일반 정품 이미지는 여전히 *되지* IOT_TOOLKIT를 포함 하지만 IOT_WEBBEXTN 패키지 WDP에서 끌어오기를 사용 해야 합니다. 

## <a name="shared-documentation"></a>공유 설명서
WDP는 모든 Windows 10 장치 간에 공유 하는 개발자 도구입니다. 각 제품에는 자체 고유 기능이 있지만 핵심 기능은 동일 합니다.
주요 기능에 대 한 설명서에서 검색 되는 [Windows Device Portal 개요 페이지](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal)합니다. 아래 설명서의 나머지 부분에는 특정 IoT 됩니다.

## <a name="set-up"></a>설정

Windows Device Portal 시작 및 실행을 이동 하는 방법은 두 가지입니다.

### <a name="1-windows-10-iot-dashboard"></a>1. Windows 10 IoT 대시보드

다운로드 하려는 먼저 합니다 [Windows 10 IoT 대시보드](https://docs.microsoft.com/en-us/windows/iot-core/connect-your-device/iotdashboard), 새 장치를 쉽게 설치할 수 있도록 하는 개발자 도구입니다. 대시보드에서 장치를 Windows 10 IoT Core 이미지를 사용한 후 장치 "내 장치"에서 표시 되는지 확인 합니다. 

여기에서 "작업" 아래에 있는 줄임표를 사용 "에서 장치 포털 열기"를 선택 합니다. 여기에서 있습니다 이동 장치 포털 인증 페이지를 처음에 자격 증명을 변경 하지 않는 한 기본 자격 증명이 있는: 

    Username: `Administrator`<br/>
    Password: `p@ssw0rd`
 
 ### <a name="2-browser"></a>2. 브라우저
대시보드에서 장치를 찾을 수 없거나 대시보드를 사용 하 여 표시 하지 않으려면 선호를 열 수도 있습니다는 장치 포털 더하기 장치의 IP 주소를 입력 하 여 `:8080` 끝에 있습니다. 올바르게 수행 하는 경우 다음과 같이 표시 됩니다.


   ![장치 IoTDashboard 보기](../media/deviceportal/Dashboard-Action.gif)

    
## <a name="iot-specific-features"></a>IoT 특정 기능

### <a name="device-settings"></a>장치 설정

IoT Core를 사용 하도록 설정 하거나 사용 하지 않도록 설정 하 라는 확인란이 추가 된 [화상 키보드](../develop-your-app/OnScreenKeyboard.md)
> [!NOTE]
> 이 확인란을 선택 되지 않은 확인 여기서 "깜박입니다"에서 알려진된 버그를 있습니다. 확인란을 원하는 상태를 표시 하 고 있는지 확인을 클릭 한 후 f5 키를 눌러 페이지를 새로 고치십시오.

### <a name="apps"></a>앱
AppX 패키지 및 장치에는 번들에 대 한 설치/제거 기능을 제공합니다.
![앱 목록](../media/DevicePortal/AppList.png)

IoT Core는 한 번에 실행할 하나의 전경 앱만 허용 하는 고유 합니다. 앱 목록의 경우 인지 확인 하도록 수정 됩니다. 아래는 **시작** 열 있습니다 기본적으로 시작 하는 만큼 백그라운드 응용 프로그램을 선택할 수 있지만 하나의 포그라운드 응용 프로그램에만 설정할 수 있습니다.  

### <a name="app-file-explorer"></a>앱 파일 탐색기

앱 파일 탐색기를 앱에 액세스할 수 있도록 디렉터리를 보여 줍니다.

* CameraRoll가 모든 앱 공유
* 모든 앱에서 문서 공유
* LocalAppData 각 앱에 특정 폴더를 포함합니다. 이 폴더의 이름은 앱 되며 다른 앱에 액세스할 수 없습니다.

### <a name="debugging"></a>디버깅

#### <a name="kernel-dumps"></a>커널 덤프
![커널 덤프를 사용 하 여 디버깅](../media/DevicePortal/Debug1.png)

기록 되 고 웹 관리 도구를 통해 볼 수 있습니다에 자동으로 모든 시스템 작동 중지 됩니다.  그런 다음 커널 덤프를 다운로드 하 고 진행 상황을 파악 하려고 수 있습니다.

#### <a name="process-dumps"></a>프로세스 덤프
![프로세스 덤프를 사용 하 여 디버깅](../media/DevicePortal/Debug2.png)

와 유사 하지만 사용자 모드 프로세스에 대 한 라이브 커널 덤프 합니다. 클릭 하 여 **다운로드** 단추 '미니 덤프', 하는 프로세스의 전체 상태 다운로드 됩니다. 중지 프로세스를 디버깅할 때 적합 합니다.

#### <a name="kernel-crash-settings"></a>커널 작동 중단 설정
![커널 작동 중단 설정](../media/DevicePortal/Debug3.png)

### <a name="bluetooth"></a>Bluetooth
이 페이지에는 모든 페어링된 bluetooth 장치와 검색할 수 있는 모든 장치가 표시 됩니다. 다른 Bluetooth 장치 연결, 장치 쌍 모드로 전환 하 고 사용 가능한 장치 목록에 표시 되도록 기다립니다.  
![Bluetooth 장치 목록](../media/DevicePortal/Bluetooth.png)

클릭할 **쌍 링크** 장치를 연결 합니다. 장치 쌍에서 PIN을 요구 하는 경우 팝업 메시지 상자를 PIN 표시 됩니다. 장치 쌍을 이루 면 쌍으로 연결 된 장치 목록에 나타납니다. 클릭 하 여 취소 쌍 장치 수 **제거**합니다. 

Bluetooth 페이지로 이동 하면 장치의 다른 장치에서 검색 됩니다. 또한 PC/휴대폰에서 찾을 수 있으며 여기에서 쌍으로 연결.

Bluetooth에 대 한 자세한 내용은에서 확인할 수 있습니다 합니다 [bluetooth 페이지](https://go.microsoft.com/fwlink/?linkid=823223)합니다.

### <a name="iot-onboarding"></a>IoT 온 보 딩

온 보 딩 IoT는 IoT 장치에서 Wi-fi 연결 옵션을 구성 하는 것에 대 한 지원을 제공 합니다.

**인터넷 연결 공유 (ICS)** Wi-fi SoftAP을 통해 장치에 연결 하는 다른 장치를 사용 하 여 장치에 대 한 인터넷 액세스를 공유할 수 있도록 인터넷 연결 공유 합니다.
이 기능을 사용 하려면 Windows 10 IoT 장치 (예: LAN 통해 유선) 인터넷에 액세스할 수 있도록 해야 합니다.  ' 연결 온 보 딩->-> SoftAP 설정 클릭 'enable' 및 SSID 이름 및 암호를 설정 합니다.  그런 다음 '연결-> 인터넷 연결 공유' '공유 네트워크 어댑터' 및 '액세스 지점 어댑터' 선택 "Microsoft WI-FI Direct 가상 어댑터 2"에서 유선된 이더넷 어댑터를 선택 합니다.  마지막으로, '공유 액세스를 시작 합니다.'를 클릭합니다  시작 되 면 Windows 10 IoT 장치의 SoftAP 별도 Wi-fi 사용 장치를 연결 합니다.  연결이 설정 되 면 별도 Wi-fi 사용 장치를 Windows 10 IoT 장치를 통해 인터넷에 연결할 수 됩니다.

> [!NOTE]
> Wi-fi 프로필을 장치에 있는 ICS 비활성화 됩니다. 예를 들어 Wi-fi 액세스 지점에 연결 하 고 "만들기 프로필 (자동 다시 연결)"를 확인 하는 경우 ICS 비활성화 됩니다.

**SoftAP 설정을** SoftAP 설정 장치의 SoftAP 사용 하도록 설정할지 여부를 제어할 수 있습니다.  또한 수단 제공 SoftAP의 구성에 대 한 SSID 및 WPA2-PSK 키 되는 SoftAP 다른 장치에서 연결 하는 데 필요한 합니다.

**AllJoyn 온 보 딩 설정** The AllJoyn 온 보 딩 설정을 사용 하면 장치에서 Wi-fi 연결 수 여부를 제어 하려면 장치의 AllJoyn 온 보 딩 생산자를 통해 구성 합니다.  때 응용 프로그램에 Windows 10 IoT SoftAP 연결할 AllJoyn 온 보 딩 소비자를를 실행 하는 별도 장치를 AllJoyn 온 보 딩 소비자 응용 프로그램에서 IoT 장치의 Wi-fi 어댑터를 구성 하려면 사용할 수 있습니다.  사용 하도록 설정 하면 AllJoyn 온 보 딩 생산자 앱 (IoTOnboarding) ECDHE_NULL 인증 메서드를 사용 합니다. 

> [!NOTE]
> AllJoyn 사용 하려면 Windows 10 IoT를 사용 하 여 온 보 딩 10.0.14393 빌드 또는 이전 버전을 업데이트 해야 합니다 <strong>IotOnboarding</strong> 일 수 있는 샘플 [에서 다운로드할](https://github.com/ms-iot/samples)합니다.

![AllJoyn에 온 보 딩](../media/DevicePortal/OnboardingAllJoyn.png)
![ICS에 온 보 딩](../media/DevicePortal/OnboardingICS.png)

> [!NOTE]
> 액세스 지점 어댑터는 WiFi 어댑터 (일반적으로 있기 192.168.137.1과 같은 IP 주소)가 WiFi 액세스 지점입니다.
> 공유 네트워크 어댑터는 인터넷에 연결 하는 어댑터 (예: 이더넷 어댑터)입니다.

![소프트 AP에 온 보 딩](../media/DevicePortal/OnboardingSoftAP.png)

> [!NOTE]
> SoftAP SSID가 자동으로 붙일 수 "AJ_" AllJoyn 온 보 딩을 활성화 하 고 Wifi 어댑터의 MAC 주소를 사용 하 여 후 위 하는 경우. SoftAP 암호는 8 자에서 63 ASCII 자 사이 여야 합니다.


### <a name="tpm-configuration"></a>TPM 구성
모듈 TPM (Trusted Platform)는 난수 생성, 암호화 키의 보안 생성 및 사용의 제한 사항에 대 한 기능을 포함 하는 암호화 프로세서입니다. 또한 원격 증명 및 봉인 된 저장소와 같은 기능을 포함 합니다. TPM 및 보안 IoT Core에 대 한 자세한 내용은 참조는 [보안 장치를 구축](../secure-your-device/BuildingSecureDevices.md) 페이지와 [TPM](../secure-your-device/TPM.md) 페이지.

> [!IMPORTANT]
> Windows IoT Core의 일부가 되려면 Limpet.exe 사용 합니다. 2018 년 10 월부터,이 제품은 현재에 오픈 소스 프로젝트가 [ https://github.com/ms-iot/azure-dm-client ](https://github.com/ms-iot/azure-dm-client)합니다.

테스트를 보다 쉽게 확인, 서명 되지 않은 미리 작성 된 버전을 사용할 수 있는 Limpet.exe 하 고 WDP에서 바로 다운로드할 수 있습니다. ' TPM 구성 ' 탭 이동 하 여 최신 설치 ' 단추를 클릭 하기만 하면 됩니다. 

> [!NOTE]
> 이 버전의 Limpet.exe 최종 제품을 사용 하 여 제공 되지 해야 합니다. 대신, 오픈 소스 프로젝트를 빌드하고, 서명, 이미지를 사용 하 여 패키지를 해야 합니다.

### <a name="azure-clients-configuration"></a>Azure 클라이언트 구성

클라우드 서비스를 통해 IoT 장치를 원격으로 관리할 수 있습니다. Azure는 이러한 시나리오를 사용 하는 서비스는 매우 다양 한 집합을 제공 합니다. 도 노출 하는 몇 가지 Windows 관리 효율성 기능 및 Windows 플랫폼에서 Azure의 장치 프로 비전 서비스 (DPS) 및 Azure의 IoT Hub 서비스를 보완 하는 장치 관리 클라이언트를 만들었습니다.

클라이언트는 오픈 소스 프로젝트로 제공 됩니다. 이러한 테스트를 쉽게 미리 작성된 된 이진 파일 제공할 예정입니다. ' Azure 클라이언트 ' 탭을 사용할 수 있습니다 이러한 테스트 이진 파일에서 WDP 설치 하 고 실행 합니다.

> [!NOTE]
> 최종 제품을 사용 하 여이 버전의 도구를 배송 하지 해야 합니다. 대신, 오픈 소스 프로젝트를 빌드하고, 서명, 이미지를 사용 하 여 패키지를 해야 합니다.

오픈 소스 프로젝트에 사용할 수 있으면이 설명서를 업데이트 됩니다.

### <a name="remote"></a>리모컨
Windows IoT 원격 서버를 사용 하면 키보드에 실제 모니터를 연결 하지 않고 표시 하는 장치는 알 수 있습니다.


## <a name="additional-information"></a>추가 정보 

### <a name="changing-the-default-port"></a>기본 포트를 변경합니다.
 
1. Powershell을 시작 하 고 [장치에 연결 합니다.](../connect-your-device/PowerShell.md)
2. 다운로드 [TakeRegistryOwnership](https://github.com/ms-iot/iot-utilities/tree/master/TakeRegistryOwnership) 도구를 빌드하고 장치에 복사 합니다. 
3. 실행 하 여 서비스에 대 한 레지스트리 키의 소유권 가져오기

        .\TakeRegistryOwnership.exe MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\webmanagement\service

4. 레지스트리 설정을 수정 하 여 원하는 포트를 설정 합니다. 

        reg add HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\webmanagement\service /v HttpPort /t REG_DWORD /d <your port number>
        
5. WebManagement 서비스를 실행 하 여 다음 또는 장치를 다시 시작 하 여 다시 시작

        net stop webmanagement ; net start webmanagement

### <a name="using-https"></a>HTTPS를 사용 하 여 

HTTPS를 사용 하려는 경우 먼저 이전 섹션에 설명 된 대로 레지스트리 키의 소유권을 수행 및 아래와 같이 HttpsPort 및 EncryptionMode 레지스트리 키를 설정 하 고 webmanagement 서비스를 다시 시작

        reg add HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\webmanagement\service /v EncryptionMode /t REG_DWORD /d 0x3 /f
        reg add HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\webmanagement\service /v HttpsPort /t REG_DWORD /d <your port number> /f
        net stop webmanagement ; net start webmanagement

### <a name="provisoning-device-portal-with-a-custom-ssl-certificate"></a>사용자 지정 SSL 인증서를 사용 하 여 프로 비전 장치 포털

Windows 10 크리에이터 업데이트 Windows Device Portal HTTPS 통신에 사용 하기 위해 사용자 지정 인증서를 설치 하려면 장치 관리자를 추가 합니다.

자세한 내용은 [Windows Device Portal 문서에 있는 설명서를 읽을](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-ssl)합니다. 

### <a name="crash-dump-settings-for-capturing-memory-dump"></a>덤프 설정은 메모리 덤프 캡처에 대 한 충돌 합니다.

전체 메모리 덤프를 캡처하려면 다음을 수행 합니다.

1. WDP 통해 IoT 장치에 연결 합니다.

2. 디버그에서 설정-> 디버그-> 커널 크래시 설정-크래시 덤프 유형 >입니다. 

3. 선택: 사용 하 여 메모리의 메모리 덤프를 완료 합니다.
    장치 설정을 적용 하려면 다시 부팅 해야 합니다. 
    
4. 확인 `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\CrashControl\CrashDumpEnabled` 0x1로 설정 됩니다.

5. 업데이트 `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\CrashControl\DumpFileSize` 0x0을 합니다.

6. 이 덤프 생성에 대 한 장치에 충분 한 공간이 있는지 확인 합니다. 여기에서 변경 된 덤프 파일 위치를 구성할 수 있습니다. `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\CrashControl\DumpFile`


## <a name="additional-resources"></a>추가 리소스
___ 

1. [Windows Device Portal 개요 페이지](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal)
