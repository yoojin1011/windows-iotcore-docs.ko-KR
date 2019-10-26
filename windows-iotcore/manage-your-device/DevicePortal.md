---
title: Windows Device Portal
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: Windows 장치 포털을 사용 하 여 장치를 원격으로 구성 하 고 관리 하는 방법에 대해 알아봅니다.
keywords: windows iot, Windows 장치 포털, 원격, 장치 포털
ms.openlocfilehash: d7e5285b7a29a61f15a5272cc822832230e56f75
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72917440"
---
# <a name="windows-device-portal"></a>Windows Device Portal
   Windows 장치 포털 (WDP)을 사용 하 여 로컬 네트워크를 통해 원격으로 장치를 구성 하 고 관리할 수 있습니다.
주요 기능은 [Windows 장치 포털 개요 페이지](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal) 에 설명 되어 있습니다.

![장치 포털 홈](../media/deviceportal/deviceportal.png)

> [!IMPORTANT]
> 상용화에 제조사 이미지를 사용하지 마세요. 디바이스를 상용화하려는 경우 최적의 보안을 위해 사용자 지정 FFU를 사용해야 합니다. [여기](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)에서 자세한 내용을 알아보세요.

> [!WARNING]
> 라이브 커널 디버그가 현재 ARM 장치에 대해 실패 합니다. 이 문제를 해결 하기 위해 노력 하 고 있습니다.

> [!IMPORTANT]
> 최종 사용자가 최종 구성을 수행 하 고 고객에 게 [WDP에 대 한 인증서를 얻어야 하는 고객을 문서화 하는 "특정/제한 된 설치" (즉, 공장 또는 소매점)에 대해 상용 배포를 위한 오픈 정품 장치를 구축 하는 경우 그리고 WDP에 설치 하 고 브라우저와 암호를 연결 하면 WDP에서](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-ssl)WDP를 사용할 수 있습니다. 이 시나리오에서 소매점 이미지는 여전히 IOT_TOOLKIT를 포함 *하지* 않지만 IOT_WEBBEXTN 패키지를 사용 하 여 WDP로 가져와야 합니다. 

## <a name="shared-documentation"></a>공유 설명서
WDP는 모든 Windows 10 장치에서 공유 되는 개발자 도구입니다. 각 제품에는 고유한 기능이 있지만 핵심 기능은 동일 합니다.
주요 기능에 대 한 설명서는 [Windows 장치 포털 개요 페이지](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal)에 있습니다. 아래 설명서의 나머지 부분은 IoT 관련 됩니다.

## <a name="set-up"></a>설정

Windows 장치 포털을 시작 하 고 실행 하는 방법에는 두 가지가 있습니다.

### <a name="1-windows-10-iot-dashboard"></a>1. Windows 10 IoT 대시보드

먼저 새 장치를 쉽게 설정할 수 있도록 하는 개발자 도구인 [Windows 10 IoT 대시보드](https://docs.microsoft.com/en-us/windows/iot-core/connect-your-device/iotdashboard)를 다운로드 하는 것이 좋습니다. 대시보드를 사용 하 여 Windows 10 IoT Core 이미지를 장치에 플래시 한 후 장치가 "내 장치" 아래에 표시 되는지 확인 합니다. 

여기에서 "작업" 아래에 있는 줄임표를 사용 하 여 "장치 포털에서 열기"를 선택 합니다. 여기서는 처음에 자격 증명을 변경 하지 않은 경우 기본 자격 증명을 사용 하 여 장치 포털 인증 페이지로 이동 합니다. 

    Username: `Administrator`<br/>
    Password: `p@ssw0rd`
 
 ### <a name="2-browser"></a>2. 브라우저
대시보드에서 장치를 찾을 수 없거나 대시보드 사용을 건너뛰도록 선호 하는 경우 장치의 IP 주소를 입력 하 고 끝에 `:8080` 하 여 장치 포털을 열 수도 있습니다. 올바르게 수행 되 면 다음과 같이 표시 됩니다.


   ![I이상 대시보드 보기 장치](../media/deviceportal/Dashboard-Action.gif)

    
## <a name="iot-specific-features"></a>IoT 관련 기능

### <a name="device-settings"></a>장치 설정

IoT Core는 [화상 키보드](../develop-your-app/OnScreenKeyboard.md) 를 사용 하거나 사용 하지 않도록 확인란을 추가 합니다.
> [!NOTE]
> 이 확인란은 선택 된 상태에서 선택 되지 않은 것으로 "flash"가 되는 알려진 버그를 포함 합니다. 확인란이 원하는 상태를 표시 하는지 확인 하려면 클릭 한 후 페이지를 새로 고칩니다.

### <a name="apps"></a>앱을 선택하고
장치에서 AppX 패키지 및 번들에 대 한 설치/제거 기능을 제공 합니다.
앱 목록 ![](../media/DevicePortal/AppList.png)

IoT Core는 한 번에 하나의 포그라운드 앱만 실행할 수 있다는 면에서 고유 합니다. 이 경우 앱 목록이 수정 되어이를 확인 합니다. **시작** 열에서 기본적으로 시작할 백그라운드 응용 프로그램 수를 선택할 수 있지만 전경 응용 프로그램은 하나만 설정할 수 있습니다.  

### <a name="app-file-explorer"></a>앱 파일 탐색기

앱 파일 탐색기에는 앱이 액세스할 수 있는 디렉터리가 표시 됩니다.

* CameraRoll는 모든 앱에서 공유 됩니다.
* 문서는 모든 앱에서 공유 됩니다.
* LocalAppData에는 각 앱에 해당 하는 폴더가 포함 됩니다. 이 폴더는 앱과 이름이 같으며 다른 앱은 액세스할 수 없습니다.

### <a name="debugging"></a>디버깅

#### <a name="kernel-dumps"></a>커널 덤프
![커널 덤프를 사용 하 여 디버깅](../media/DevicePortal/Debug1.png)

모든 시스템 크래시는 자동으로 기록 되 고 웹 관리 도구를 통해 볼 수 있습니다.  그런 다음 커널 덤프를 다운로드 하 고 진행 상황을 파악할 수 있습니다.

#### <a name="process-dumps"></a>덤프 처리
![프로세스 덤프를 사용 하 여 디버깅](../media/DevicePortal/Debug2.png)

이는 라이브 커널 덤프와 유사 하지만 사용자 모드 프로세스의 경우입니다. **다운로드** 단추를 클릭 하면 ' 미니 덤프 '가 발생 하 고 해당 프로세스의 전체 상태가 다운로드 됩니다. 이는 분기 프로세스를 디버깅 하는 데 유용 합니다.

#### <a name="kernel-crash-settings"></a>커널 충돌 설정
![커널 충돌 설정](../media/DevicePortal/Debug3.png)

### <a name="bluetooth"></a>Bluetooth
이 페이지에는 모든 bluetooth 페어링 장치와 검색 가능한 모든 장치가 표시 됩니다. 다른 Bluetooth 장치와 페어링 하려면 장치를 페어링 모드로 전환 하 고 사용 가능한 장치 목록에 표시 될 때까지 기다립니다.  
![Bluetooth 장치 목록](../media/DevicePortal/Bluetooth.png)

**페어링 링크** 를 클릭 하 여 장치를 페어링 합니다. 장치에서 페어링을 위해 PIN을 요구 하는 경우 PIN을 표시 하는 메시지 상자가 표시 됩니다. 장치가 페어링된 후 페어링 된 장치 목록에 표시 됩니다. **제거**를 클릭 하 여 장치 쌍을 해제할 수 있습니다. 

Bluetooth 페이지로 이동 하면 다른 장치에서 장치를 검색할 수 있습니다. 또한 PC/휴대폰에서 해당 파일을 찾아 쌍으로 연결할 수 있습니다.

Bluetooth에 대 한 자세한 내용은 [bluetooth 페이지](https://go.microsoft.com/fwlink/?linkid=823223)에서 찾을 수 있습니다.

### <a name="iot-onboarding"></a>IoT 온 보 딩

IoT 온 보 딩은 IoT 장치의 Wi-fi 연결 옵션을 구성 하는 기능을 제공 합니다.

**ICS (인터넷 연결 공유)** 인터넷 연결 공유를 사용 하면 Wi-fi SoftAP에서 장치에 연결 된 다른 장치와 장치의 인터넷 액세스를 공유할 수 있습니다.
이 기능을 사용 하려면 Windows 10 IoT 장치에서 인터넷에 액세스할 수 있어야 합니다 (예: 유선 LAN 연결을 통해).  ' 연결-> 온 보 딩-> SoftAP 설정 '에서 ' 사용 '을 클릭 하 고 SSID 이름과 암호를 설정 합니다.  그런 다음 ' 연결-> 인터넷 연결 공유 '에서 ' 액세스 지점 어댑터 '를 선택 하 고, ' Microsoft Wi-fi 직접 가상 어댑터 #2 "를 선택 하 고, ' 공유 네트워크 어댑터 '에서 유선 이더넷 어댑터를 선택 합니다.  마지막으로 ' 공유 액세스 시작 '을 클릭 합니다.  시작 되 면 별도의 Wi-fi 사용 장치를 Windows 10 IoT 장치의 SoftAP에 연결 합니다.  연결이 설정 되 면 별도의 Wi-fi 사용 장치에서 Windows 10 IoT 장치를 통해 인터넷에 연결할 수 있습니다.

> [!NOTE]
> Wi-fi 프로필이 장치에 있는 경우 ICS를 사용할 수 없습니다. 예를 들어 Wi-fi 액세스 지점에 연결 하 고 "프로필 만들기 (자동 다시 연결)"를 선택 하는 경우 ICS를 사용 하지 않도록 설정 됩니다.

**SoftAP 설정** SoftAP 설정을 사용 하 여 장치의 SoftAP 사용 여부를 제어할 수 있습니다.  또한 다른 장치에서 SoftAP를 연결 하는 데 필요한 SoftAP의 SSID와 WPA2-PSK 키를 구성 하는 수단을 제공 합니다.

**AllJoyn 온 보 딩 설정** AllJoyn 온 보 딩 설정을 사용 하 여 장치의 AllJoyn 등록 생산자를 통해 장치의 Wi-fi 연결을 구성할 수 있는지 여부를 제어할 수 있습니다.  AllJoyn 온 보 딩 소비자 응용 프로그램을 실행 하는 별도 장치에서 Windows 10 IoT SoftAP에 연결 하는 경우 AllJoyn 온 보 딩 소비자 응용 프로그램을 사용 하 여 IoT 장치의 Wi-fi 어댑터를 구성할 수 있습니다.  이 기능을 사용 하도록 설정 하면 ECDHE_NULL 인증 방법을 사용 하는 AllJoyn 온 보 딩 생산자 앱 

> [!NOTE]
> Windows 10 IoT 빌드에서 10.0.14393 또는 이전 버전을 사용 하려면 [여기에서 다운로드할](https://github.com/ms-iot/samples)수 있는 <strong>iotonboarding 보 딩</strong> 샘플에 대 한 업데이트가 필요 합니다.

](../media/DevicePortal/OnboardingAllJoyn.png)
![를 통해 ![에 온 보 딩에 온 보 딩](../media/DevicePortal/OnboardingICS.png)

> [!NOTE]
> 액세스 지점 어댑터는 WiFi 액세스 지점 역할을 하는 WiFi 어댑터 이며 일반적으로 192.168.137.1와 같은 IP 주소가 있습니다.
> 공유 네트워크 어댑터는 인터넷 (예: 이더넷 어댑터)에 연결 되는 어댑터입니다.

![소프트 AP로 등록](../media/DevicePortal/OnboardingSoftAP.png)

> [!NOTE]
> SoftAP SSID는 AllJoyn 등록을 사용 하도록 설정 하 고, Wifi 어댑터의 MAC 주소를 사용 하 여 되도록 후 위를 사용 하는 경우 "AJ_"로 자동 접두사가 붙습니다. SoftAP 암호는 8 ~ 007e; 63 ASCII 문자 여야 합니다.


### <a name="tpm-configuration"></a>TPM 구성
TPM (신뢰할 수 있는 플랫폼 모듈)은 난수 생성, 암호화 키의 보안 생성 및 사용 제한에 대 한 기능을 포함 하는 암호화 보조 기능입니다. 또한 원격 증명 및 봉인 된 저장소와 같은 기능을 포함 합니다. IoT Core의 TPM 및 보안에 대 한 자세한 내용은 [보안 장치 구축](../secure-your-device/BuildingSecureDevices.md) 페이지 및 [tpm](../secure-your-device/TPM.md) 페이지를 참조 하세요.

> [!IMPORTANT]
> Limpet는 Windows IoT Core의 일부로 사용 됩니다. 2018 년 10 월부터 이제 [https://github.com/ms-iot/azure-dm-client](https://github.com/ms-iot/azure-dm-client)에서 오픈 소스로 사용할 수 있습니다.

테스트를 용이 하 게 하기 위해 Limpet의 서명 되지 않은 미리 작성 된 버전을 사용할 수 있으며 WDP에서 바로 다운로드할 수 있습니다. ' TPM 구성 ' 탭으로 이동 하 여 ' 최신 버전 설치 ' 단추를 클릭 하기만 하면 됩니다. 

> [!NOTE]
> 이 버전의 Limpet를 최종 제품과 함께 제공 해서는 안 됩니다. 대신 오픈 소스 프로젝트를 빌드하고, 서명 하 고, 이미지를 사용 하 여 패키지 해야 합니다.

### <a name="azure-clients-configuration"></a>Azure 클라이언트 구성

IoT 장치는 클라우드 서비스를 통해 원격으로 관리할 수 있습니다. Azure는 이러한 시나리오를 가능 하 게 해 주는 매우 다양 한 서비스 집합을 제공 합니다. Microsoft는 Windows 플랫폼에서 Azure의 DPS (장치 프로 비전 서비스)와 Azure의 IoT Hub 서비스를 보완 하 고 몇 가지 Windows 관리 효율성 기능을 노출 하는 장치 관리 클라이언트를 만들었습니다.

클라이언트는 오픈 소스 프로젝트로 제공 됩니다. 테스트를 더 쉽게 수행 하기 위해 미리 작성 된 이진 파일을 제공할 예정입니다. WDP에서 ' Azure 클라이언트 ' 탭을 사용 하 여 해당 테스트 바이너리를 설치 하 고 실행할 수 있습니다.

> [!NOTE]
> 이 버전의 도구를 최종 제품과 함께 제공 해서는 안 됩니다. 대신 오픈 소스 프로젝트를 빌드하고, 서명 하 고, 이미지를 사용 하 여 패키지 해야 합니다.

오픈 소스 프로젝트를 사용할 수 있게 되 면이 설명서를 업데이트할 예정입니다.

### <a name="remote"></a>리모컨
사용자는 Windows IoT 원격 서버를 사용 하 여 실제 모니터를 키보드에 연결 하지 않고도 장치에 표시 되는 항목을 확인할 수 있습니다.


## <a name="additional-information"></a>추가 정보 

### <a name="changing-the-default-port"></a>기본 포트 변경
 
1. Powershell을 시작 하 고 [장치에 연결 합니다.](../connect-your-device/PowerShell.md)
2. [TakeRegistryOwnership](https://github.com/ms-iot/iot-utilities/tree/master/TakeRegistryOwnership) 도구를 다운로드 하 고 빌드하고 장치에 복사 합니다. 
3. 을 실행 하 여 서비스에 대 한 레지스트리 키의 소유권 가져오기

        .\TakeRegistryOwnership.exe MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\webmanagement\service

4. 레지스트리 설정을 수정 하 여 원하는 포트를 설정 합니다. 

        reg add HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\webmanagement\service /v HttpPort /t REG_DWORD /d <your port number>
        
5. 다음을 실행 하거나 장치를 다시 시작 하 여 WebManagement 서비스를 다시 시작 합니다.

        net stop webmanagement ; net start webmanagement

### <a name="using-https"></a>HTTPS 사용 

HTTPS를 사용 하려면 먼저 이전 섹션에 설명 된 대로 레지스트리 키의 소유권을 가져오고 아래와 같이 HttpsPort 및 \stststststststststh 키를 설정한 후 webmanagement 서비스를 다시 시작 합니다.

        reg add HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\webmanagement\service /v EncryptionMode /t REG_DWORD /d 0x3 /f
        reg add HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\webmanagement\service /v HttpsPort /t REG_DWORD /d <your port number> /f
        net stop webmanagement ; net start webmanagement

### <a name="provisoning-device-portal-with-a-custom-ssl-certificate"></a>사용자 지정 SSL 인증서를 사용 하 여 장치 포털 프로 비전

Windows 10 크리에이터 업데이트에서 Windows 장치 포털은 장치 관리자가 HTTPS 통신에 사용할 사용자 지정 인증서를 설치할 수 있는 방법을 추가 했습니다.

자세히 알아보려면 [Windows 장치 포털 문서에서 설명서를 참조](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-ssl)하세요. 

### <a name="crash-dump-settings-for-capturing-memory-dump"></a>메모리 덤프 캡처에 대 한 크래시 덤프 설정:

전체 메모리 덤프를 캡처하려면 다음을 수행 합니다.

1. WDP를 통해 IoT 장치에 연결 합니다.

2. 디버그 > 디버그 설정-> 커널 충돌 설정-> 크래시 덤프 유형입니다. 

3. : 메모리 덤프 완료 (사용 중인 메모리)를 선택 합니다.
    설정을 적용 하려면 장치를 다시 부팅 해야 합니다. 
    
4. `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\CrashControl\CrashDumpEnabled`가 0x1로 설정 되었는지 확인 합니다.

5. `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\CrashControl\DumpFileSize`를 0x0으로 업데이트 합니다.

6. 이 덤프를 생성 하기에 충분 한 공간이 장치에 있는지 확인 합니다. 덤프 파일 위치를 변경 하는 작업은 다음 위치에서 구성할 수 있습니다. `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\CrashControl\DumpFile`


## <a name="additional-resources"></a>추가 리소스
___ 

1. [Windows 장치 포털 개요 페이지](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal)
