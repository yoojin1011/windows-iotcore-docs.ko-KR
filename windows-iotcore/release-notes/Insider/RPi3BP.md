---
title: Raspberry Pi 3B+ 릴리스 정보
ms.date: 05/16/2018
ms.topic: article
description: Raspberry Pi 3B+ 빌드의 새로운 기능을 참조하여 자세히 알아봅니다.
keywords: Windows IoT, Windows Insider, 릴리스 정보, Raspberry Pi 3B+
ms.openlocfilehash: d321676758f7ff438540720098e6a6ecb1ba457f
ms.sourcegitcommit: 34928850d3b1b2fe22a92ebd1d75c01b3d4bf0aa
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/24/2020
ms.locfileid: "75721018"
---
# <a name="release-notes-for-raspberry-pi-3b"></a>Raspberry Pi 3B+ 릴리스 정보

&copy; 2018 Microsoft Corporation. All rights reserved.

> [!NOTE]
> 이번 Raspberry Pi 3B용 릴리스에서는 기술 미리 보기를 지원하지 않습니다. 유효성 검사 및 활성화가 제한적으로 완료되었습니다. 현재 릴리스는 [여기](https://www.microsoft.com/en-us/software-download/windowsiot)서 찾을 수 있습니다. 보다 나은 평가 환경은 물론, 상용 제품을 위해 Raspberry Pi 3B 또는 Intel, Qualcomm 또는 NXP SoC가 지원되는 기타 디바이스를 사용해 주세요. Raspberry Pi 3B+ 관련 문제 해결의 경우 문제 해결 가이드([여기](https://docs.microsoft.com/windows/iot-core/troubleshooting?branch=master#raspberry-pi-3b-booting-issues))를 참조해 주세요. 

## <a name="whats-new-in-this-build"></a>이 빌드의 새로운 기능 
* 일반 버그 수정

## <a name="known-issues-in-this-build"></a>이 빌드의 알려진 이슈:
* 이 이미지는 RPi3B+ 전용이며, RPi2에서는 부팅되지 않습니다. 
* Visual Studio에서 배포하는 F5 드라이버는 IoT Core에서 작동하지 않습니다. 
* 온보드 WIFI 및 Bluetooth는 RPI3B+에서 작동하지 않습니다. 
* Ft5406 터치 스크린 드라이버는 RPi3B+에서 사용할 수 없습니다. 
* SD 카드 활동 LED를 사용할 수 없습니다. 


### <a name="display-resolution-is-monitor-is-disconnected"></a>모니터 연결이 끊어진 경우 디스플레이 해상도
모니터 연결이 끊어지면 Pi 3B+에서 디스플레이 해상도를 유지 관리하지 못할 수 있습니다. 모니터의 EDID는 모니터가 연결될 때 시스템의 해상도를 설정하는 데 사용됩니다. 연결이 끊어지면 펌웨어가 기본적으로 SD 카드의 루트에 있는 config.txt의 값으로 설정됩니다. 


### <a name="video-performance"></a>비디오 성능
플랫폼의 비디오 재생 성능이 최적화되지 않았습니다.  XAML 기반 드롭다운 메뉴를 비롯한 애니메이션 사용자 요소가 최적화된 성능을 발휘하지 못할 수 있습니다.  

### <a name="camera-support"></a>카메라 지원
카메라 주변 기기 지원이 제한됩니다. D3D 최신 USB 웹캠이 USB 호스트 컨트롤러의 매우 까다로운 데이터 스트림을 생성하도록 지원하기 위해 플랫폼이 제한되므로 온보드 카메라 버스에 직접 연결되는 PiCam 디바이스는 지원되지 않습니다.  저해상도 설정으로 사용하더라도 웹캠에서 USB를 미세 조정해야 하며 특수한 제어 논리가 필요합니다.  


### <a name="mouse-pointer-disappears-while-debugging"></a>디버그하는 동안 사라지는 마우스 포인터
경우에 따라 Visual Studio를 사용하여 앱을 배포하거나 디버그한 후에 마우스 포인터가 표시되지 않을 때 키보드(탭 키)를 사용하여 포커스를 변경하면 마우스 포인터가 다시 나타납니다(8038595).

### <a name="server-applications-with-softap"></a>SoftAP를 사용하는 서버 애플리케이션
SoftAP를 사용하면 클라이언트가 UAP 앱에 의해 노출되는 콘텐츠에 액세스할 수 없습니다. SoftAP를 통해 UAP 애플리케이션을 공개하려면 디바이스의 콘솔에서 다음과 같이 변경해야 합니다(8111807).  

```
reg add hklm\system\currentcontrolset\services\mpssvc\parameters /v IoTInboundLoopbackPolicy /t REG_DWORD /d 1 
checknetisolation loopbackexempt -a -n=<AppID for SoftAP App> 
checknetisolation loopbackexempt -a -n=<AppID for Additional App>  
For example:  checknetisolation loopbackexempt -a -n=IoTOnboardingTask-uwp_1w720vyc4ccym 
```

다시 부팅하세요.

### <a name="sensor-driver-conflict-in-pre-built-ffus"></a>미리 빌드된 FFU의 센서 드라이버 충돌 
제공된 FFU의 센서 드라이버가 충돌합니다. 원격 센서 프레임워크는 나침반, 자력계, 가속도계 및 자이로스코프의 드라이버를 설치합니다. 애플리케이션에서 이러한 디바이스에 액세스하는 UWP API에서는 하나만 설치되어 있다고 가정합니다. 물리적으로 연결되는 디바이스의 드라이버를 개발하는 경우 Microsoft에서 제공한 FFU의 원격 드라이버가 충돌합니다.  

이 문제를 해결하려면 SSH 또는 Powershell을 통해 디바이스에 연결하고 devcon.exe 도구에서 다음을 입력하여 원격 센서 드라이버를 제거함으로써 충돌하는 드라이버를 제거할 수 있습니다. 

```
"devcon.exe remove @"ROOT\REMOTESENSORDRIVER*"
```

원격 센서 드라이버는 OEM에서 만든 FFU에 영향을 주지 않습니다. 


### <a name="default-administrator-user-name-and-password"></a>기본 관리자 사용자 이름 및 암호
기본 관리자 사용자 이름 및 암호는 Windows 10 IoT Core 이미지에 하드 코딩됩니다. 이는 디바이스의 보안에 위험 요소로 작동하며, 암호가 변경되기 전에는 열린 인터넷 연결에 노출되면 안 됩니다. 

### <a name="volume-controls"></a>볼륨 컨트롤
Windows 시스템을 사용하여 시스템 볼륨을 변경하는 USB 마이크 및 스피커의 시스템 볼륨 컨트롤은 현재 Windows 10 IoT Core에서 지원되지 않습니다. 

### <a name="usb-keyboards"></a>USB 키보드
일부 USB 키보드 및 마우스는 IoT Core에서 작동하지 않을 수 있습니다. 다른 키보드 또는 마우스를 사용하세요. 유효성이 검사된 주변 장치의 목록은 [여기](https://go.microsoft.com/fwlink/?LinkId=619428)의 설명서에서 확인할 수 있습니다.
 
### <a name="screen-orientation"></a>화면 방향
방향을 "세로"로 설정하는 기능이 유니버설 앱에서는 작동하지 않을 수 있습니다.

### <a name="referencing-adapters-with-alljoyn-templates"></a>AllJoyn 템플릿을 사용하여 어댑터 참조
특정 SDK 버전을 사용하는 경우 AllJoyn 어댑터 프로젝트에 대한 참조를 추가하려고 하면 오류가 발생할 수 있습니다.  이 오류를 해결하려면 Visual Studio의 대상 플랫폼을 현재 SDK 버전에 맞게 변경한 다음, 프로젝트를 다시 로드합니다.  

### <a name="wifi-direct-limitations-on-windows-10-iot-core"></a>Windows 10 IoT Core의 WiFi Direct 제한 사항
1. Windows 10 IoT Core 디바이스는 연결 디바이스여야 합니다. 이 디바이스는 연결을 시작하는 다른 디바이스가 있는 광고 디바이스로 작동하지 않습니다.   
2. 고급 페어링을 사용해야 합니다.  샘플 앱은 디바이스를 연결하기 전에 고급 페어링 API를 사용하여 페어링하는 방법을 보여줍니다. 
3. 모든 무선 어댑터가 WiFi Direct를 지원하는 것은 아닙니다. "Realtek RTL8188EU Wireless Lan 802.11n USB 2.0 네트워크 어댑터"가 작동하는지 테스트하고 유효성을 검사했지만, 다른 어댑터가 지원되지 않을 수 있습니다. 

### <a name="non-default-drive-mode-3890679"></a>기본이 아닌 드라이브 모드(3890679) 
Raspberry Pi 및 Dragonboard에서, 기본이 아닌 드라이브 모드에서 기본이 아닌 다른 드라이브 모드로 전환하면 GPIO 핀에서 문제가 발생할 수 있습니다. 이 문제를 해결하려면 애플리케이션을 시작할 때 드라이브 모드를 한 번 설정합니다. 

### <a name="application-already-running-1244550"></a>이미 실행 중인 애플리케이션(1244550) 
기본 시작 앱 역시 Visual Studio에서 배포하면 자체 앱과 충돌할 수 있습니다. 해결 방법: 기본 시작 앱을 배포하려는 앱이 아닌 다른 애플리케이션으로 변경합니다. 

### <a name="backgroundmediaplayermessagereceivedfromforeground-may-crash-2199869"></a>BackgroundMediaPlayer.MessageReceivedFromForeground의 작동이 중단될 수 있음(2199869) 
다음 코드 줄이 충돌할 수 있습니다. 
```
BackgroundMediaPlayer.MessageReceivedFromForeground += OnMessageReceivedFromForeground
```

작동 중단을 방지하려면 먼저 실행되도록 다음 코드를 추가합니다.
```
var player = BackgroundMediaPlayer.Current;
```

### <a name="azure-active-directory-authentication-support-4266261"></a>Azure Active Directory 인증 지원(4266261) 
Azure Active Directory 인증 라이브러리는 Windows 10 IoT Core에서 작동하지 않습니다.  

### <a name="shell-management-of-application-crashes"></a>애플리케이션 충돌의 셸 관리
IoT Core의 셸 인프라는 디바이스에서 실행되는 APPX 형식 애플리케이션의 충돌을 모니터링하다가 충돌이 발생하면 해당 애플리케이션을 다시 시작합니다.  다시 시작된 애플리케이션의 작동이 여전히 중단되면 셸에서 failfast를 사용합니다. 이는 복구를 위해 버그를 검사하고 다시 부팅하는 중요한 시스템 프로세스입니다.  헤드 구성의 백그라운드 작업과 포그라운드 애플리케이션에 비슷한 논리와 처리 방법이 사용됩니다.   캡처된 작동 중단 처리 및 다시 시도 논리는 다음과 같습니다.

```
Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\CBTConfig  (or ForegroundAppConfig for headed) 
  Qword:"FailureResetIntervalMs" – length of time app has to run successfully to reset failures seen to 0. – default is 0x00000000000493E0 == 5 minutes 
  Qword:"BaseRetryDelayMs"  -- wait time coefficient.  Default is 0xa. 
  Dword:"MaxFailureCount". Default is 10 
  DWord:"FallbackExponentNumerator", default is 31. 
  Dword:"FallbackExponentDenominator", default is 20 
  
  
Fallback_exponent = FallbackExponentNumerator / FallbackExponentDenominator; // default is 1.55 
When app crash is detected: 
    if time_since_last_crash > failureresetinterval then crashes_seen = 1 
    else ++crashes_seen; 
  
if crashes_seen > MaxFailureCount then __failfast; 
  
else  
  
delay = (dword) ((float)BaseRetryDelayMs * (crashes_seen ** Fallback_exponent)) 
```

지연되는 동안 기다린 후에 앱을 다시 시작하세요.

#### <a name="dragonboard-spi-runs-at-48mhz"></a>4\.8Mhz로 실행되는 Dragonboard SPI
Dragonboard의 SPI는 요청된 속도를 무시하고 항상 4.8Mhz로 실행됩니다.  

#### <a name="dragonboard-connected-standby"></a>Dragonboard 연결된 대기 상태 
연결된 대기 상태는 Qualcomm Dragonboard에서 기본적으로 사용되지 않습니다.  DragonBoard에서 연결된 대기 상태를 사용하도록 설정하려면 다음 레지스트리 키를 "1"로 설정해야 합니다.


### <a name="time-synchronization"></a>시간 동기화
시간 동기화가 실패하거나 시간이 초과되면 시간 서버가 멀리 떨어져 있거나 연결할 수 없는 것이 원인일 수 있습니다. 다음을 수행하여 추가 또는 로컬 시간 서버를 추가할 수 있습니다. 
 
1. 디바이스의 명령줄(예: SSH, Powershell)에서 다음을 실행합니다.
   ```
   w32tm /config /syncfromflags:manual /manualpeerlist:"0.windows.time.com 1.pool.ntp.org 2.something else, ..."
   ```
2. 필요한 경우 부팅 스크립트 또는 이미지 만들기 프로세스 도중에 포함된 사용자 지정 런타임 구성 패키지를 레지스트리에 추가할 수도 있습니다. 

### <a name="starting-the-ftp-server"></a>FTP 서버 시작 
* 한 번만 실행하려면 SSH\PS를 사용하여 로그인하고 다음 명령을 실행하여 FTP를 시작합니다.  

```
start ftpd.exe 
```

* 모든 부팅에서 실행하려면 사용자가 스케줄러 작업을 만들어야 합니다. SSH\PS를 사용하여 로그인하고 스케줄러 작업을 만듭니다.

```
schtasks /create /tn "IoTFTPD" /tr ftpd.exe /ru system /sc onstart 
Schtasks /run /tn “IoTFTPD” 
```

### <a name="partition-size-requirements-for-update"></a>업데이트에 대한 파티션 크기 요구 사항 
데이터 파티션에서 업데이트 기능에 충분한 공간을 유지하는지 확인합니다.  전체 업데이트 기능에는 1GB를 무료로 사용하는 것이 좋습니다.  데이터 파티션의 공간이 부족하면 설치 단계에서 업데이트가 실패합니다. 

### <a name="powershell-log-generation-on-iot-core"></a>IoT Core에서 PowerShell 로그 생성 
Iot Core의 PowerShell은 기본적으로 파일 시스템의 공간을 차지하여 로그 파일을 생성할 수 있습니다. 로그 파일 크기는 제한되어 있지만 잠재적으로 공간을 차지하여 디스크 공간이 부족하게 되므로 업데이트가 실패할 수 있습니다. .evtx 이벤트 로그 파일의 경우 미리 정의된 최대 크기는 각각 20MB입니다. 서로 다른 최대 크기를 유지하도록 레지스트리를 통해 파일을 개별적으로 제한할 수 있습니다. 예를 들어 security.evtx를 최대 10MB 크기로 유지하려면 다음을 수행합니다. 
```
regd add HKLM\SYSTEM\CurrentControlSet\Services\EventLog\Security /v MaxSize /t REG_DWORD /d 0xa00000 /f 
```

### <a name="schtasks-limitation"></a>schtasks 제한  
schtasks는 /xml 스위치를 사용할 수 없습니다. 예를 들어 다음과 같은 가치를 제공해야 합니다. 
```
schtasks /create /xml <xmlfile> /TN <taskname>
```
IoT Core에서는 이 작업이 실패합니다. 이 명령을 실행하면 "오류: 지정된 프로시저를 찾을 수 없습니다."라는 오류가 생성됩니다. 
