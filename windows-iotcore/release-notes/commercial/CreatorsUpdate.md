---
title: 크리에이터스 업데이트 - 빌드 15063
ms.date: 08/28/2017
ms.topic: article
description: 크리에이터스 업데이트의 새로운 기능을 참조하여 자세히 알아봅니다.
keywords: Windows IoT, 크리에이터스 업데이트, 릴리스 정보
ms.openlocfilehash: 09157cb634de971bfe57f549c3c87354f814f9e9
ms.sourcegitcommit: 9fb86fb605d6a8feb5c226a391045b908117a90a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80080556"
---
# <a name="creators-update-release-notes-for-windows-10-iot-core"></a>Windows 10 IoT용 크리에이터스 업데이트 릴리스 정보
빌드 번호 15063. 2017년 4월

Windows 10 IoT Core는 임베디드 또는 전용 디바이스를 개발할 수 있도록 하며, 소형 디바이스용 Windows 솔루션을 빌드하는 OEM 및 개발자에게 적합합니다.

이 문서에서는 이 Windows 10 IoT Core 릴리스에 대한 다른 내용과 설명서를 보충하는 정보를 제공합니다.

이 릴리스의 패키지에는 Intel Atom 프로세서 기반 Minnowboard Max 플랫폼, ARM Cortex A7 기반 Raspberry Pi 2 및 Qualcomm Snapdragon 400 시리즈 프로세서 기반 Dragonboard 410c에 Windows 10 IoT Core를 설치하는 데 필요한 도구와 구성 요소가 포함되어 있습니다.   

[다른 플랫폼 및 프로세서](../../learn-about-hardware/SoCsAndCustomBoards.md)는 파트너에서 사용할 수 있습니다.

## <a name="privacy-statement"></a>개인 정보 취급 방침

이 Windows 운영 체제 버전의 개인정보처리방침은 [여기](https://go.microsoft.com/fwlink/?LinkId=506737)서 볼 수 있습니다.

## <a name="whats-new"></a>새로운 기능
* Windows 10 IoT Core 퍼블릭 릴리스 
   * Azure 디바이스 관리 지원 - OEM에서 Windows IoT Azure DM 클라이언트 라이브러리를 사용하여 디바이스 관리 기능을 Azure IoT 허브에 연결된 디바이스에 추가할 수 있습니다.
   * 추가 실리콘 지원
      * Intel Joule, Intel Pentium N4200, Intel Celeron N3350, 예정된 Atom x5-E39xx 프로세서(이전의 Apollo Lake) 및 Raspberry Pi 3 SOM에 대한 Windows 10 IoT Core 지원이 확인되었습니다.
      * Allwinner는 Allwinner A64 SoC를 사용하여 Pine 64 및 Banana Pi 디바이스를 지원할 수 있습니다. 
   * 원격 디바이스 검색 - Microsoft 계정으로 로그인한 디바이스를 검색하는 데 특별한 소프트웨어가 필요하지 않습니다.
   * 진동, 밝기, 최신 연결된 대기 상태, 전원 관리, 배터리 충전 및 NFC(HCE 없음)에 대한 UWP API 및 컨트롤이 새로 추가되었습니다. 
   * ARM PCIe, USB 기능 모드, Wi-Fi Direct 및 GPIO 인터럽트 계산 API에 대한 버스와 기능이 새로 추가되었습니다. 
   * 다시 설정/복구, On-SOC PWM 및 자동 USB 프로비저닝에 대한 포함 기능이 새로 추가되었습니다. 
   * 향상된 도구 - VS Code, 새 Windows 디바이스 포털 및 IoT 대시보드 기능, VS 2017 지원
   * Windows IoT Core의 Cortana - Cortana는 이제 Windows 10 IoT Core에서 사용할 수 있습니다. Cortana에 문의하세요.
   * 향상된 IoT 대시보드 - 새로운 기능 및 안정성 버그 수정
      * Windows Insider Preview 빌드(Raspberry Pi 및 Minnowboard용) 
      * Windows IoT 원격 클라이언트를 사용하여 디바이스 연결 
      * 디바이스 검색의 Ipv6 주소 
      * 피드백을 제출하는 동안 디바이스 로그 업로드
   *  새 고정밀 GPIO API - GPIO 인터럽트를 사용하여 펄스 너비를 정확하고 효율적으로 측정하는 새 API(Windows.Devices.Gpio.GpioInterruptBuffer)입니다.  GPIO 공급자에는 회전식 인코더 및 거리 측정 디바이스와 같이 높은 고정밀 인터럽트 타이밍을 애플리케이션에 허용하는 새 인터럽트 버퍼 인터페이스가 포함되어 있습니다.
   * IoT용 Device Guard - 디바이스 작성기는 이제 IoT 디바이스를 완전히 잠그고 새롭거나 알 수 없는 맬웨어 변형으로부터 고급 맬웨어를 보호할 수 있습니다.  이 작업은 알 수 없거나 신뢰할 수 없는 코드를 실행하도록 허용하지 않으면서 디바이스에서 실행되는 허용 가능한 애플리케이션 및 드라이버에 대한 서명 권한을 지정하여 수행할 수 있습니다.  즉, 맬웨어 및 제로 데이 공격에 대한 보안이 향상되었습니다. 
   * 기타 업데이트는 다음과 같습니다. 
      * 향상된 업데이트 지원 
      * Azure 게이트웨이 SDK 지원 
      * USB 드라이브 기반 자동 프로비저닝 
      * 디바이스 포털 재설계 
      * 64비트 이미지 - 이제 최대 16,384MB 메모리를 지원함 
      * WinRT 진동 API 
      * 향상된 언어 지원 
   * 기타  
      * 복구 모드가 없는 경우 디바이스에서 복구 모드로 부팅하지 못하도록 기본 BCD 설정이 변경되었습니다. 
      * 이제 powercfg.exe가 IOT_POWER_SETTINGS 기능에 포함됩니다. 이는 모든 아키텍처(ARM32, x86 및 x64)에서 사용할 수 있습니다. 
      * blockrebooton/blockrebootoff 플래그를 추가하도록 Applyupdate.exe가 변경되었습니다. 
      * 하드웨어 알림(hwnclx) 및 USB 함수(usbfnclx)에 대한 클래스 확장이 기본 IoT Core 이미지에 추가되었습니다.

## <a name="known-issues"></a>알려진 문제

### <a name="raspberry-pi"></a>Raspberry Pi  

#### <a name="raspberry-pi-display-resolution-if-monitor-is-disconnected"></a>모니터 연결이 끊어진 경우 Raspberry Pi 디스플레이 해상도 
모니터 연결이 끊어진 경우 Raspberry Pi가 디스플레이 해상도를 유지하지 않을 수 있습니다. 시스템이 연결되는 경우 모니터의 EDID를 사용하여 시스템의 해상도를 설정합니다.  
연결이 끊어지면 Raspberry Pi 펌웨어는 SD 카드의 루트에 있는 config.txt를 기본값으로 사용합니다. 

#### <a name="raspberry-pi-video-performance"></a>Raspberry Pi 비디오 성능 
Raspberry Pi 플랫폼의 비디오 재생 성능이 최적화되지 않았습니다.  XAML 기반 드롭다운 메뉴를 비롯한 애니메이션 사용자 요소가 최적화된 성능을 발휘하지 못할 수 있습니다. 

#### <a name="raspberry-pi-camera-support"></a>Raspberry Pi 카메라 지원 
Raspberry Pi 디바이스가 있는 카메라 주변 장치에 대한 Windows 10 IoT Core 지원이 제한됩니다. DirectX 드라이버가 구현되지 않아 현재 Raspberry Pi에서 사용할 수 없는 GPU 서비스가 필요하므로 온보드 카메라 버스에 직접 연결된 PiCam 디바이스는 현재 지원되지 않습니다. 최신 USB 웹캠은 USB 호스트 컨트롤러에서 매우 까다로운 데이터 스트림을 생성합니다.  저해상도 설정으로 사용하더라도 웹캠에서 USB를 미세 조정해야 하며 특수한 제어 논리가 필요합니다.  

#### <a name="raspberry-pi-3-bluetooth-support"></a>Raspberry Pi 3 Bluetooth 지원 
Raspberry Pi3 기본 제공 Bluetooth 드라이버는 낮은 대역폭 디바이스만 지원합니다.  

#### <a name="serial-port-usage-and-access-on-raspberry-pi-2"></a>Raspberry Pi 2의 직렬 포트 사용 및 액세스 
Raspberry Pi 2는 PL011 UART을 통해 통신에 대한 직렬 전송을 지원합니다.  이는 커널 디버깅 시나리오에서 기본적으로 설정됩니다.  애플리케이션 또는 디바이스 드라이버는 PL011 UART를 사용하여 다음 명령으로 디버거를 끄는 PL011 디바이스 드라이버와 데이터를 보내고 받을 수 있습니다.   
`bcedit /set debug off` 
 
### <a name="dragon-board"></a>DragonBoard 

#### <a name="dragonboard-410c-shutdown"></a>Dragonboard 410c 종료 
DragonBoard에서 종료 명령을 실행해도 보드 전원이 꺼지지 않습니다. 시스템이 다시 시작됩니다. 전원을 차단하여 보드를 끄세요. 

#### <a name="dragon-board-headset--microphone-jack"></a>DragonBoard 헤드셋 및 마이크 잭  
Dragonboard BSP에는 헤드셋 잭과 마이크 잭의 드라이버가 있지만, 둘 중 어느 잭도 보드에 통합되어 있지 않습니다.  

#### <a name="dragonboard-spi-runs-at-lock-speed"></a>잠금 속도로 실행되는 Dragonboard SPI  
Dragonboard의 SPI는 요청된 속도를 무시하고 항상 미리 구성된 속도로 실행됩니다.  

#### <a name="dragonboard-connected-standby"></a>Dragonboard 연결된 대기 상태 
연결된 대기 상태는 Qualcomm Dragonboard에서 기본적으로 사용되지 않습니다.  DragonBoard에서 연결된 대기 상태를 사용하도록 설정하려면 다음 레지스트리 키를 "1"로 설정해야 합니다. 
<br>
`HKLM\System\Controlset001\Control\Power\CsEnabled=DWORD:1`
<br>
모든 플랫폼에서 CS를 지원하는 것은 아니므로 다른 플랫폼에서는 작동하지 않을 수 있습니다.    

#### <a name="vibration-api-may-not-function-on-some-qualcomm-platforms"></a>일부 Qualcomm 플랫폼에서 진동 API가 작동하지 않을 수 있음 
제안되는 해결 방법은 다음 레지스트리 키를 추가하는 것입니다. 
<br>
`[HKEY_LOCAL_MACHINE\SYSTEM\controlset001\services\hwnhaptics]` 
<br>
`"EnableOemSecurity"=dword:00000001 `
<br>
기존 이미지를 확인/증명하기 위해 SSH 또는 PowerShell에 연결하고 다음 명령을 실행합니다. 
<br>
`reg add HKEY_LOCAL_MACHINE\SYSTEM\controlset001\services\hwnhaptics /t REG_DWORD /v EnableOemSecurity /d 1 `

### <a name="minnowboard"></a>MinnowBoard  

#### <a name="minnowboard-max-firmware-update"></a>Minnowboard Max 펌웨어 업데이트 
펌웨어 버전이 0.92 이상인 경우에만 MinnowBoard Max가 부팅됩니다.  
MBM(MinnowBoard Max) 펌웨어 버전 0.93에는 네트워크 연결 오류가 있을 수 있습니다.   이 문제는 펌웨어 버전 0.94에서 해결되었습니다.  추천되는 최소 펌웨어 버전은 "MinnowBoard MAX 0.94 32비트"입니다. 펌웨어 업데이트는  [여기](https://go.microsoft.com/fwlink/?LinkId=708613)서 다운로드할 수 있습니다.
  
 
### <a name="all-platforms"></a>모든 플랫폼 

#### <a name="mouse-pointer-disappears-while-debugging"></a>디버깅하는 동안 사라지는 마우스 포인터 
경우에 따라 Visual Studio를 사용하여 앱을 배포하거나 디버그한 후에 마우스 포인터가 표시되지 않을 때 키보드(탭 키)를 사용하여 포커스를 변경하면 마우스 포인터가 다시 나타납니다.  

#### <a name="server-applications-with-softap"></a>SoftAP를 사용하는 서버 애플리케이션  
SoftAP를 사용하면 클라이언트가 UAP 앱에서 공개하는 콘텐츠에 액세스할 수 없습니다.  
SoftAP를 통해 UAP 애플리케이션을 공개하려면 디바이스의 콘솔에서 다음과 같이 변경해야 합니다.  
<br>
`reg add hklm\system\currentcontrolset\services\mpssvc\parameters /v IoTInboundLoopbackPolicy /t REG_DWORD /d 1 `
<br>
`checknetisolation loopbackexempt -a -n=<AppID for SoftAP App>`
<br>
`checknetisolation loopbackexempt -a -n=<AppID for Additional App> `
<br>
`For example:  checknetisolation loopbackexempt -a -n=IoTOnboardingTask-uwp_1w720vyc4ccym`
<br>
`Reboot`

#### <a name="sensor-driver-conflict-in-pre-built-ffus"></a>미리 빌드된 FFU의 센서 드라이버 충돌 
제공된 FFU의 센서 드라이버가 충돌합니다. 원격 센서 프레임워크는 나침반, 자력계, 가속도계 및 자이로스코프의 드라이버를 설치합니다. 애플리케이션에서 이러한 도구에 액세스하는 데 사용되는 UWP API는 1개만 설치된 것으로 가정합니다. 물리적으로 연결되는 디바이스의 드라이버를 개발하는 경우 Microsoft에서 제공한 FFU의 원격 드라이버가 충돌합니다.  
해상도: SSH 또는 PowerShell을 통해 디바이스에 연결하고 devcon.exe 도구에서 "devcon.exe remove @"ROOT\REMOTESENSORDRIVER*"를 입력하여 원격 센서 드라이버를 제거함으로써 충돌하는 드라이버를 제거할 수 있습니다. 원격 센서 드라이버는 OEM에서 만든 FFU에 영향을 주지 않습니다. 
 
#### <a name="default-administrator-user-name-and-password"></a>기본 관리자 사용자 이름 및 암호 
기본 관리자 사용자 이름 및 암호는 Windows 10 IoT Core 이미지에 하드 코딩됩니다. 이는 디바이스의 보안에 위험 요소로 작동하며, 암호가 변경되기 전에는 열린 인터넷 연결에 노출되면 안 됩니다. 
 
#### <a name="volume-controls"></a>볼륨 컨트롤 
Windows 시스템을 사용하여 시스템 볼륨을 변경하는 USB 마이크 및 스피커의 시스템 볼륨 컨트롤은 현재 Windows 10 IoT Core에서 지원되지 않습니다. 
 
#### <a name="usb-keyboards"></a>USB 키보드  
일부 USB 키보드 및 마우스는 IoT Core에서 작동하지 않을 수 있습니다. 다른 키보드 또는 마우스를 사용하세요. 유효성이 검사된 주변 장치의 목록은 [여기](../../learn-about-hardware/HardwareCompatList.md)서 확인할 수 있습니다.  
 
#### <a name="screen-orientation"></a>화면 회전 
방향을 "세로"로 설정하는 것은 유니버설 앱에서 허용되지 않을 수 있습니다. 
 
#### <a name="referencing-adapters-with-alljoyn-templates"></a>AllJoyn 템플릿을 사용하여 어댑터 참조 
특정 SDK 버전을 사용하는 경우 AllJoyn 어댑터 프로젝트에 대한 참조를 추가하려고 하면 오류가 발생할 수 있습니다.  이 오류를 해결하려면 Visual Studio의 대상 플랫폼을 현재 SDK 버전에 맞게 변경한 다음, 프로젝트를 다시 로드합니다. 

#### <a name="non-default-drive-mode"></a>기본이 아닌 드라이브 모드  
Raspberry Pi 및 Dragonboard에서, 기본이 아닌 드라이브 모드에서 기본이 아닌 다른 드라이브 모드로 전환하면 GPIO 핀에서 문제가 발생할 수 있습니다. 해결 방법: 애플리케이션을 시작할 때 드라이브 모드를 한 번 설정합니다. 
 
#### <a name="application-already-running"></a>이미 실행 중인 애플리케이션  
기본 시작 앱 역시 Visual Studio에서 배포하면 자체 앱과 충돌할 수 있습니다. 해결 방법: 기본 시작 앱을 배포하려는 앱이 아닌 다른 애플리케이션으로 변경합니다. 
 
#### <a name="backgroundmediaplayermessagereceivedfromforeground-may-crash"></a>BackgroundMediaPlayer.MessageReceivedFromForeground가 충돌할 수 있음  
다음 코드 줄의 작동이 중단될 수 있습니다.`BackgroundMediaPlayer.MessageReceivedFromForeground += OnMessageReceivedFromForeground;`
<br>
작동 중단을 방지하려면 먼저 실행되도록 다음 코드를 추가합니다.`var player = BackgroundMediaPlayer.Current;` 
 
#### <a name="azure-active-directory-authentication-support"></a>Azure Active Directory 인증 지원  
Azure Active Directory 인증 라이브러리는 Windows 10 IoT Core에서 작동하지 않습니다.  
 
#### <a name="shell-management-of-application-crashes"></a>애플리케이션 충돌의 셸 관리 
IoT Core의 셸 인프라는 디바이스에서 실행되는 APPX 형식 애플리케이션의 충돌을 모니터링하다가 충돌이 발생하면 해당 애플리케이션을 다시 시작합니다.  다시 시작된 애플리케이션의 작동이 여전히 중단되면 셸에서 __failfast를 사용합니다. 이는 복구를 위해 버그를 검사하고 다시 부팅하는 중요한 시스템 프로세스입니다.  헤드 구성의 백그라운드 작업과 포그라운드 애플리케이션에 비슷한 논리와 처리 방법이 사용됩니다.   

충돌 처리 및 재시도 논리는 아래에 캡처되어 있습니다. 

Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\CBTConfig(또는 헤드 구성의 경우 ForegroundAppConfig) 
* Qword:"FailureResetIntervalMs" – 앱을 성공적으로 실행하여 0으로 표시되는 오류를 다시 설정해야 하는 기간입니다. – 기본값은 0x00000000000493E0 == 5분입니다. 
* Qword:"BaseRetryDelayMs"  -- 대기 시간 계수입니다.  기본값은 0xa입니다.
* Dword:"MaxFailureCount". 기본값은 10입니다.
* DWord:"FallbackExponentNumerator", 기본값은 31입니다.
* Dword:"FallbackExponentDenominator", 기본값은 20입니다.
 
```C#
Fallback_exponent = FallbackExponentNumerator / FallbackExponentDenominator;
// default is 1.55
When app crash is detected:
    if time_since_last_crash > failureresetinterval then crashes_seen = 1
    else ++crashes_seen;

if crashes_seen > MaxFailureCount then __failfast;

else

delay = (dword) ((float)BaseRetryDelayMs * (crashes_seen ** Fallback_exponent))
// wait for delay and relaunch app
```
 
#### <a name="time-synchronization"></a>시간 동기화  
시간 동기화가 실패하거나 시간이 초과되면 시간 서버가 멀리 떨어져 있거나 연결할 수 없는 것이 원인일 수 있습니다. 다음을 수행하여 추가 또는 로컬 시간 서버를 추가할 수 있습니다. 
 
* 디바이스의 명령줄(예: SSH, PowerShell)에서 다음을 실행합니다.  w32tm /config /syncfromflags:manual /manualpeerlist:"0.windows.time.com 1.pool.ntp.org 2.something else, ..." 
* 필요한 경우 이미지 만들기 프로세스의 일부로 포함된 부팅 스크립트 또는 사용자 지정 런타임 구성 패키지를 통해 이러한 추가 작업을 레지스트리에 수행할 수도 있습니다. 
자세한 내용은 다음 항목을 참조하세요. 
* [이미지에 파일 및 레지스트리 설정 추가](https://msdn.microsoft.com/library/windows/hardware/mt670641(v=vs.85).aspx)
* [Windows 10 IoT Core 이미지 만들기](https://blogs.msdn.microsoft.com/iot/2015/12/14/windows-10-iot-core-image-creation/)

#### <a name="starting-the-ftp-server"></a>FTP 서버 시작 
시작 시 FTP 서버가 더 이상 기본적으로 실행되지 않음 
<br>
한 번만 실행하려면 
`Login with SSH\PS`를 수행합니다. 다음 명령을 실행하여 FTP를 시작합니다.  
`start ftpd.exe`    
부팅할 때마다 실행하려면 사용자가 스케줄러 작업을 만들어야 합니다. 

    Login with SSH\PS and create a scheduler task:       
    schtasks /create /tn "IoTFTPD" /tr ftpd.exe /ru system /sc onstart 
    schtasks /run /tn “IoTFTPD” 

## <a name="copyright-information"></a>저작권 정보 

© Microsoft. All rights reserved. 
 
이 설명서는 “있는 그대로” 제공됩니다.  URL 및 기타 인터넷 웹 사이트 참조를 포함하여 이 문서에 표현된 정보와 보기는 예고 없이 변경될 수 있습니다. 

여기에서 설명한 일부 예시는 설명을 위한 것이며 실제가 아닙니다.  실제 연관이나 관련성을 나타낼 의도가 없으며 그렇게 유추해서도 안됩니다.  

이 문서는 Microsoft 제품의 지적 재산권에 대한 어떠한 법적 권한도 제공하지 않습니다.  이 문서는 내부 참조용으로 사용할 수 있습니다. 
  
Microsoft는 어떠한 명시적 또는 묵시적 보증도 하지 않습니다.  

상표권이 있는 제품의 목록은 Microsoft 상표를 참조하세요. 

다른 모든 상표는 해당 소유자의 자산입니다.  

UPnP™은 UPnP™ Implementers Corporation의 인증 표시입니다. 

Bluetooth®는 Bluetooth SIG, Inc. 소유의 상표입니다. 미국 및 Microsoft Corporation에 사용이 허가되었습니다. 

Intel은 Intel Corporation의 등록 상표입니다. 

Itanium은 Intel Corporation의 등록 상표입니다.
 
이 소프트웨어의 일부는 University of Illinois의 Urbana-Champaign 소재의 National Center for Supercomputing Applications에서 개발하고 Spyglass, Inc.와의 사용권 계약 하에 배포되는 MCSA Mosaic를 기반으로 합니다. 

이 제품에는 RSA Data Security, Inc.에서 사용권을 부여한 보안 소프트웨어가 포함되어 있습니다. 
