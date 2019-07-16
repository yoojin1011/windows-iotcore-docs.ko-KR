---
title: 크리에이터 스 업데이트-빌드 15063
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 읽기 및 크리에이터 업데이트의 새로운 기능에 대해 알아봅니다.
keywords: windows iot, 크리에이터 업데이트 릴리스 정보
ms.openlocfilehash: a8b8fc93d8c079b1b57bbe18f48ea0bc7082dcbe
ms.sourcegitcommit: 38de3aad11845248dac393ffc51b18c5596af4c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68155400"
---
# <a name="creators-update-release-notes-for-windows-10-iot-core"></a>크리에이터 업데이트는 Windows 10 IoT Core 대 한 릴리스 정보
빌드 15063 번호입니다. 2017년 4월

Windows 10 IoT Core 장치 포함 또는 전용 용도의 개발 하며 Oem 및 소형 장치에 대 한 Windows 솔루션을 빌드하는 개발자에 대 한 선택입니다.

이 문서는 다른 콘텐츠 및 Windows 10 IoT Core이 릴리스에 대 한 설명서를 보완 하는 정보를 제공 합니다.

이 릴리스 내의 패키지 도구 및 Intel Atom 프로세서에 따라 Minnowboard 최대 플랫폼 ARM Cortex A7 및 Dragonboard 410 c Qualcomm Snapdragon 400 계열을 기반으로 기반으로 하는 Raspberry Pi 2에 Windows 10 IoT Core 설치 하는 데 필요한 구성 요소를 포함 합니다. 프로세서입니다.   

[기타 플랫폼 및 프로세서](../../learn-about-hardware/SoCsAndCustomBoards.md) 파트너에서 사용할 수 있습니다.

## <a name="privacy-statement"></a>개인정보취급방침

이 Windows 운영 체제 버전의 개인정보처리방침은 [여기](http://go.microsoft.com/fwlink/?LinkId=506737)서 볼 수 있습니다.

## <a name="whats-new"></a>새로운 기능
* Windows 10 IoT Core 공개 릴리스입니다. 
   * Azure 장치 관리 지원-Oem Azure IoT hub 연결 된 장치에 장치 관리 기능을 추가할 Windows IoT Azure DM 클라이언트 라이브러리를 사용할 수 있습니다.
   * 추가 실리콘 지원
      * Intel 줄, Intel Pentium N4200, Intel Celeron N3350 예정 된 Atom x5 E39xx 프로세서 (이전의 Apollo Lake)에서 Windows 10 IoT Core 대 한 지원을 확인 하 고 Raspberry Pi 3 Som 합니다.
      * Allwinner가 Allwinner A64 SoC.를 사용 하 여 소나무 64, Banana Pi 장치에 대 한 지원을 사용 하도록 설정 
   * Microsoft 계정으로 로그인 하는 장치를 검색 하는 데 필요한 특별 한 소프트웨어가 없어도 원격 장치를 검색 합니다.
   * 새 UWP Api 및 컨트롤을 진동, 밝기, 최신 연결 된 대기 모드, 전원 관리, 배터리 충전량 및 NFC (HCE)가 있습니다. 
   * 새로운 버스 및 USB 함수 모드, Wi-Fi Direct 및 API를 계산 하는 GPIO 인터럽트 ARM PCIe 기능입니다. 
   * 새 포함 된 기능 재설정/복구, SOC에서 PWM 및 USB 자동 프로 비전 
   * 향상 된 도구-VS Code에서 새로운 Windows Device Portal 및 IoT 대시보드 기능, VS 2017을 지원 합니다.
   * Windows IoT Core-에서 Cortana Cortana는 이제 Windows 10 IoT Core 사용할 수 있습니다. Cortana가 질문을 입력 합니다.
   * IoT 대시보드 개선 사항-새로운 기능 및 안정성 버그 수정
      * Raspberry Pi 및 Minnowboard Windows Insider Preview 빌드 
      * Windows IoT 원격 클라이언트를 사용 하 여 장치를 연결 합니다. 
      * 장치 검색의 Ipv6 주소 
      * 사용자 의견을 제출 하는 동안 장치 로그 업로드
   *  새 높은 정밀도 GPIO Api-pulse 너비 GPIO를 사용 하 여 정확 하 고 효율적인 측정을 위한 새로운 Api (Windows.Devices.Gpio.GpioInterruptBuffer) 중단 합니다.  GPIO 공급자 회전식 인코더 및 장치를 측정 하는 거리와 같은 응용 프로그램에 대 한 타이밍 고정밀 인터럽트 수 있도록 새 인터럽트 버퍼 인터페이스를 포함 합니다.
   * IoT-장치를 완전히 잠글 이제 작성기 수에 대 한 device Guard는 IoT 장치를 아래쪽 및 알 수 없는 새 맬웨어 변형에 대 한 맬웨어 보호를 고급 얻습니다.  이 허용 가능한 응용 프로그램 및 알 수 없거나 신뢰할 수 없는 코드의 실행을 허용 하는 동안 장치에서 실행 되는 드라이버에 대 한 서명 기관을 지정 하 여 수행할 수 있습니다.  이 맬웨어 및 0 일 공격에 대 한 향상 된 보안을 의미합니다. 
   * 기타 업데이트는 다음과 같습니다. 
      * 향상 된 업데이트 지원 
      * Azure 게이트웨이 SDK 지원 
      * USB 드라이브를 기반으로 자동 프로 비전 
      * 장치 포털 재설계 
      * 64 비트 이미지에는 이제 16,384 MB 메모리의 최대 지원 
      * WinRT 진동 Api 
      * 향상 된 언어 지원 
   * 기타  
      * 장치의 복구 모드가 없는 경우 복구 모드로 부팅 하는 것을 방지 하도록 기본 BCD 설정이 된 변경이 수행 되었습니다. 
      * IOT_POWER_SETTINGS 기능에는 이제 powercfg.exe 포함 됩니다. 모든 아키텍처 (ARM32, x86 및 x64)에 대해 제공 됩니다. 
      * 내용이 변경 Applyupdate.exe blockrebooton/blockrebootoff 플래그를 추가 하려면 
      * 하드웨어 알림 (hwnclx) 및 USB 함수 (usbfnclx)에 대 한 클래스 확장에 추가 된 기본 IoT Core 이미지

## <a name="known-issues"></a>알려진 문제

### <a name="raspberry-pi"></a>Raspberry Pi  

#### <a name="raspberry-pi-display-resolution-if-monitor-is-disconnected"></a>모니터 연결이 끊어진 경우 Raspberry Pi 디스플레이 해상도 
모니터 연결이 끊어진 경우 Raspberry Pi가 디스플레이 해상도를 유지하지 않을 수 있습니다. 모니터의 EDID가 연결 된 경우 시스템의 해상도 설정 하는 데 사용 됩니다.  
연결이 끊어지면 Raspberry Pi 펌웨어는 SD 카드의 루트에 있는 config.txt를 기본값으로 사용합니다. 

#### <a name="raspberry-pi-video-performance"></a>Raspberry Pi 비디오 성능 
Raspberry Pi 플랫폼에서 비디오 재생 성능이 최적화 되지 않았습니다.  XAML 기반 드롭다운 메뉴를 비롯한 애니메이션 사용자 요소가 최적화된 성능을 발휘하지 못할 수 있습니다. 

#### <a name="raspberry-pi-camera-support"></a>Raspberry Pi 카메라 지원 
Raspberry Pi 장치를 사용 하 여 주변 장치 카메라에 대 한 Windows 10 IoT Core 지원은 제한 됩니다. PiCam 장치 내장 카메라 버스에 직접 연결 된 현재 지원 되지 않습니다, DirectX 드라이버 구현 되지 않은 경우 Raspberry Pi에서 현재 사용할 수 없는 GPU 서비스 필요 하므로 합니다. 최신 USB 웹캠 매우 까다로운 USB 호스트 컨트롤러에는 데이터 스트림을 생성 합니다.  저해상도 설정으로 사용하더라도 웹캠에서 USB를 미세 조정해야 하며 특수한 제어 논리가 필요합니다.  

#### <a name="raspberry-pi-3-bluetooth-support"></a>Raspberry Pi 3 Bluetooth 지원 
Raspberry Pi3 기본 제공 Bluetooth 드라이버 저대역폭 장치만 지원  

#### <a name="serial-port-usage-and-access-on-raspberry-pi-2"></a>Raspberry Pi 2에 대 한 액세스 및 직렬 포트 사용 
Raspberry Pi 2는 PL011 UART을 통해 통신에 대한 직렬 전송을 지원합니다.  이는 커널 디버깅 시나리오에서 기본적으로 설정됩니다.  응용 프로그램 또는 장치 드라이버를 PL011 UART를 사용 하 여 다음 명령을 사용 하 여 디버거를 끄면 PL011 장치 드라이버를 사용 하 여 데이터를 주고받을 수 있습니다.   
`bcedit /set debug off` 
 
### <a name="dragon-board"></a>Dragon 보드 

#### <a name="dragonboard-410c-shutdown"></a>Dragonboard 410c 종료 
DragonBoard에서 종료 명령을 실행해도 보드 전원이 꺼지지 않습니다. 시스템이 다시 시작됩니다. 전원을 차단하여 보드를 끄세요. 

#### <a name="dragon-board-headset--microphone-jack"></a>DragonBoard 헤드셋 및 마이크 잭  
Dragonboard BSP에는 헤드셋 잭과 마이크 잭의 드라이버가 있지만, 둘 중 어느 잭도 보드에 통합되어 있지 않습니다.  

#### <a name="dragonboard-spi-runs-at-lock-speed"></a>Dragonboard SPI 잠금 속도로 실행 됩니다.  
에 Dragonboard SPI 요청된 속도 무시 하 고 항상 미리 구성 된 속도로 실행 됩니다.  

#### <a name="dragonboard-connected-standby"></a>Dragonboard 연결된 대기 상태 
연결된 대기 상태는 Qualcomm Dragonboard에서 기본적으로 사용되지 않습니다.  DragonBoard에 연결 된 대기 상태를 사용 하도록 설정 하려면 다음 레지스트리 키 "1"로 설정 해야 
<br>
`HKLM\System\Controlset001\Control\Power\CsEnabled=DWORD:1`
<br>
모든 플랫폼에 대 한 지원이 CS, 다른 플랫폼에서 작동 하지 않을 수 있습니다이 있으므로 참고 합니다.    

#### <a name="vibration-api-may-not-function-on-some-qualcomm-platforms"></a>진동 API Qualcomm 플랫폼 일부에서 작동 하지 않을 수 있습니다. 
제안 된 해결 방법은 다음과 같습니다. 다음 레지스트리 키 추가 
<br>
`[HKEY_LOCAL_MACHINE\SYSTEM\controlset001\services\hwnhaptics]` 
<br>
`"EnableOemSecurity"=dword:00000001 `
<br>
확인에 대 한 기존 이미지에서 확인을 SSH 또는 PowerShell을 사용 하 여 연결 하 고 다음 명령을 실행 합니다. 
<br>
`reg add HKEY_LOCAL_MACHINE\SYSTEM\controlset001\services\hwnhaptics /t REG_DWORD /v EnableOemSecurity /d 1 `

### <a name="minnowboard"></a>MinnowBoard  

#### <a name="minnowboard-max-firmware-update"></a>Minnowboard 최대 펌웨어 업데이트 
펌웨어 버전.092 아닌 MinnowBoard 최대 부팅 되지 것입니다 이상.  
MinnowBoard 최대 MBM () 펌웨어 버전이 0.93 네트워크 연결 오류 수 있습니다.   이 문제는 펌웨어 버전 0.94에서에서 해결 됩니다.)  최소 권장 되는 펌웨어 버전이 "MinnowBoard 최대 32 비트 0.94"입니다. 펌웨어 업데이트를 다운로드할 수 있습니다 [여기](http://go.microsoft.com/fwlink/?LinkId=708613)합니다.
  
 
### <a name="all-platforms"></a>모든 플랫폼 

#### <a name="mouse-pointer-disappears-while-debugging"></a>디버깅하는 동안 사라지는 마우스 포인터 
일부 경우에 배포 하거나 Visual Studio를 사용 하 여 앱을 디버깅 한 후 마우스 포인터를 보이지 않으면, 키보드 (탭)를 사용 하 여 포커스를 변경 하는 경우 마우스 포인터를 다시 표시 해야  

#### <a name="server-applications-with-softap"></a>SoftAP를 사용하는 서버 애플리케이션  
클라이언트 UAP 앱에 의해 노출 되는 콘텐츠에 액세스할 수 없게 됩니다 SoftAP을 사용할 때  
SoftAP 통해 UAP 응용 프로그램을 노출 하는 다음 변경 해야 장치 콘솔에서:  
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
제공된 FFU의 센서 드라이버가 충돌합니다. 원격 센서 프레임워크는 나침반, 자력계, 가속도계 및 자이로스코프의 드라이버를 설치합니다. 애플리케이션에서 이러한 도구에 액세스하는 데 사용되는 UWP API는 1개만 설치된 것으로 가정합니다. 물리적으로 연결 된 장치 드라이버를 개발 하는 경우 microsoft 원격 드라이버 FFUs 충돌을 제공 합니다.  
해결 방법: SSH 또는 PowerShell을 통해 장치에 연결 하 고 도구 devcon.exe를 사용 하 여 입력 하 여 원격 센서 드라이버를 제거 하 여 충돌 하는 드라이버를 제거할 수 있습니다 "devcon.exe 제거 @" ROOT\REMOTESENSORDRIVER * "입니다. 원격 센서 드라이버는 OEM에서 만든 FFU에 영향을 주지 않습니다. 
 
#### <a name="default-administrator-user-name-and-password"></a>기본 관리자 사용자 이름 및 암호 
기본 관리자 사용자 이름 및 암호는 Windows 10 IoT Core 이미지에 하드 코딩됩니다. 이는 디바이스의 보안에 위험 요소로 작동하며, 암호가 변경되기 전에는 열린 인터넷 연결에 노출되면 안 됩니다. 
 
#### <a name="volume-controls"></a>볼륨 컨트롤 
Windows 시스템을 사용하여 시스템 볼륨을 변경하는 USB 마이크 및 스피커의 시스템 볼륨 컨트롤은 현재 Windows 10 IoT Core에서 지원되지 않습니다. 
 
#### <a name="usb-keyboards"></a>USB 키보드  
일부 USB 키보드 및 마우스는 IoT Core에서 작동하지 않을 수 있습니다. 다른 키보드 또는 마우스를 사용하세요. 유효성이 검사 된 주변 장치 목록을 찾을 수 있습니다 [여기](../../learn-about-hardware/HardwareCompatList.md)합니다.  
 
#### <a name="screen-orientation"></a>화면 회전 
"Portrait" 방향을 설정 수 적용 되지 않습니다 유니버설 앱에서 
 
#### <a name="referencing-adapters-with-alljoyn-templates"></a>AllJoyn 템플릿을 사용하여 어댑터 참조 
특정 SDK 버전을 사용하는 경우 AllJoyn 어댑터 프로젝트에 대한 참조를 추가하려고 하면 오류가 발생할 수 있습니다.  이 오류를 해결하려면 Visual Studio의 대상 플랫폼을 현재 SDK 버전에 맞게 변경한 다음, 프로젝트를 다시 로드합니다. 

#### <a name="non-default-drive-mode"></a>기본이 아닌 드라이브 모드  
Raspberry Pi 및 Dragonboard에서, 기본이 아닌 드라이브 모드에서 기본이 아닌 다른 드라이브 모드로 전환하면 GPIO 핀에서 문제가 발생할 수 있습니다. 해결 방법: 애플리케이션을 시작할 때 드라이브 모드를 한 번 설정합니다. 
 
#### <a name="application-already-running"></a>이미 실행 중인 애플리케이션  
기본 시작 앱 역시 Visual Studio에서 배포하면 자체 앱과 충돌할 수 있습니다. 해결 방법: 기본 시작 앱을 배포하려는 앱이 아닌 다른 애플리케이션으로 변경합니다. 
 
#### <a name="backgroundmediaplayermessagereceivedfromforeground-may-crash"></a>BackgroundMediaPlayer.MessageReceivedFromForeground가 충돌할 수 있음  
다음 코드 줄에서 중단 될 수 있습니다: `BackgroundMediaPlayer.MessageReceivedFromForeground += OnMessageReceivedFromForeground;`합니다.
<br>
먼저 실행 되도록 크래시를 방지 하려면이 코드를 추가 `var player = BackgroundMediaPlayer.Current;` 
 
#### <a name="azure-active-directory-authentication-support"></a>Azure Active Directory 인증 지원  
Azure Active Directory 인증 라이브러리는 Windows 10 IoT Core에서 작동하지 않습니다.  
 
#### <a name="shell-management-of-application-crashes"></a>애플리케이션 충돌의 셸 관리 
IoT Core의 셸 인프라는 디바이스에서 실행되는 APPX 형식 애플리케이션의 충돌을 모니터링하다가 충돌이 발생하면 해당 애플리케이션을 다시 시작합니다.  다시 시작된 응용 프로그램에 계속 셸에서 __failfast – 버그 검사를 발생 시키는 중요 한 시스템 프로세스를 적용할를 복구 하기 위해 다시 부팅 합니다.  헤드 구성의 백그라운드 작업과 포그라운드 애플리케이션에 비슷한 논리와 처리 방법이 사용됩니다.   

충돌 처리 및 재시도 논리는 아래에 캡처되어 있습니다. 

Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\CBTConfig (또는 지 향하는 방향에 대 한 ForegroundAppConfig) 
* Qword: "FailureResetIntervalMs" – 앱의 길이 0으로 표시 하는 오류를 다시 설정 하려면 성공적으로 실행 합니다. – 기본값은 0x00000000000493E0 5 분 = =. 
* Qword: "BaseRetryDelayMs"-대기 시간 계수입니다.  기본값은 0xa입니다.
* Dword: "MaxFailureCount"입니다. 기본값은 10입니다.
* DWord: "FallbackExponentNumerator" 기본값은 31입니다.
* Dword: "FallbackExponentDenominator" 기본값은 20입니다.
 
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
 
* 디바이스의 명령줄(예: SSH, PowerShell)  w32tm /config /syncfromflags:manual /manualpeerlist:"0.windows.time.com 1.pool.ntp.org 2. 다른 무언가..." 
* 부팅 스크립트를 통해 레지스트리에 이러한 추가 기능을 만들 수 있습니다 하거나 필요한 경우 이미지 만들기 프로세스의 일부분으로 사용자 지정 런타임을 구성 패키지를 포함 합니다. 
자세한 내용은 다음 항목을 참조하세요. 
* [이미지 파일 및 레지스트리 설정을 추가합니다](https://msdn.microsoft.com/library/windows/hardware/mt670641(v=vs.85).aspx)
* [Windows 10 IoT Core 이미지 만들기](https://blogs.msdn.microsoft.com/iot/2015/12/14/windows-10-iot-core-image-creation/)

#### <a name="starting-the-ftp-server"></a>FTP 서버 시작 
FTP 서버가 더 이상 실행 되는 기본적으로 시작 시 
<br>
한 번만 실행 합니다. 
`Login with SSH\PS` FTP를 시작 하려면이 명령을 실행 합니다.  
`start ftpd.exe`    
모든 부팅 시 실행 하려면 사용자가 스케줄러 작업을 만들어야 합니다. 

    Login with SSH\PS and create a scheduler task:       
    schtasks /create /tn "IoTFTPD" /tr ftpd.exe /ru system /sc onstart 
    schtasks /run /tn “IoTFTPD” 

## <a name="copyright-information"></a>저작권 정보 

© Microsoft입니다. All rights reserved. 
 
이 설명서는 "있는 그대로" 제공됩니다.  정보 및 견해 URL 및 기타 인터넷 웹 사이트 참조를 포함 하 여이 문서의 예 고 없이 변경 될 수 있습니다. 

여기에서 설명하는 일부 예는 설명 목적으로만 제공되는 가상의 예이며,  어떠한 실제 사례와도 연관시킬 의도가 없으며 그렇게 유추해서도 안 됩니다.  

이 문서는 Microsoft 제품의 지적 재산권에 대 한 법적 권한을 제공 하지 않습니다.  이 문서는 내부 참조에 사용할 수 있습니다 목적으로 합니다. 
  
Microsoft는 어떠한 명시적 또는 묵시적 보증도 하지 않습니다.  

상표 제품 목록은 Microsoft 상표를 참조 하십시오. 

다른 모든 상표는 해당 소유자의 자산입니다.  

UPnP™은 UPnP™ Implementers Corporation의 인증 표시입니다. 

Bluetooth®는 Bluetooth SIG, Inc. 소유 상표 미국 고 Microsoft Corporation 라이선스가 부여 됩니다. 

Intel는 Intel Corporation의 등록된 상표입니다. 

Itanium은 Intel Corporation의 등록된 상표입니다.
 
본이 소프트웨어의 일부 MCSA 시스템에 따라, National Center Urbana Champaign에 University of Illinois 슈퍼 컴퓨팅 응용 프로그램에 대 한 개발한, Spyglass, inc. 라이선스 계약에 따라 배포 

이 제품에 RSA Data Security, Inc.에서 라이선스가 부여 된 보안 소프트웨어 
