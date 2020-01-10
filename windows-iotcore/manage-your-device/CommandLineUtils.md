---
title: Windows 10 IoT Core 명령줄 유틸리티
author: bfjelds
ms.author: bfjelds
ms.date: 08/28/2017
ms.topic: article
description: 장치에 연결한 후 PowreShell와 함께 사용할 명령줄 유틸리티에 대해 알아봅니다.
keywords: windows iot, 명령줄, 명령줄 유틸리티, PowerShell
ms.openlocfilehash: 9e654e59f3019522f209107acd1b1ed64155d446
ms.sourcegitcommit: ea060254f9c4c25afcd0245c897b9e1425321859
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75721611"
---
# <a name="windows-10-iot-core-command-line-utils"></a>Windows 10 IoT Core 명령줄 유틸리티

장치에서 일부 설정을 구성 하 고 싶으십니까? 아래 도구를 사용할 수 있습니다. [장치에 연결한](../connect-your-device/PowerShell.md)후 PowerShell을 사용 하 여 이러한 명령을 실행 합니다.

> [!NOTE]
> 이러한 도구는 미리 로드 되지 않습니다. 이미지에서 이러한 도구를 얻으려면 적절 한 기능 Id를 포함 해야 합니다.

## <a name="iot-core-specific-command-line-utils"></a>IoT 코어 관련 명령줄 유틸리티

### <a name="setting-startup-app"></a>**시작 앱 설정:**
시작 편집기를 사용 하 여 Windows IoT Core 장치에서 시작 앱을 구성 합니다. 다음 옵션 중 하나를 사용 하 여 `IotStartup`를 실행 합니다.

* 설치 된 응용 프로그램 목록 `IotStartup list`
* 설치 된 응용 프로그램을 나열 하는 `IotStartup list headed`
* 설치 된 헤드리스 응용 프로그램 목록 `IotStartup list headless`
* 패턴과 일치 하는 설치 된 응용 프로그램을 나열 `IotStartup list [MyApp]` `MyApp`
* `IotStartup add` 및 헤드리스 응용 프로그램을 추가 합니다.
* `IotStartup add headed [MyApp]` 패턴 `MyApp`와 일치 하는 응용 프로그램을 추가 합니다.  패턴은 하나의 응용 프로그램에만 일치 해야 합니다.
* 패턴에 일치 하는 헤드리스 응용 프로그램을 추가 `IotStartup add headless [Task1]` `Task1`
* `IotStartup remove` 및 헤드리스 응용 프로그램 제거
* `IotStartup remove headed [MyApp]` 패턴과 일치 하는 응용 프로그램을 제거 `MyApp`
* `IotStartup remove headless [Task1]`는 패턴과 일치 하는 헤드리스 응용 프로그램을 제거 `Task1`
* 시작을 위해 등록 된 i 및 헤드리스 응용 프로그램을 나열 `IotStartup startup`
* `IotStartup startup [MyApp]`는 시작에 대해 패턴과 일치 하는 항목과 헤드리스 응용 프로그램 등록을 나열 `MyApp`
* 시작을 위해 등록 된 응용 프로그램을 나열 하는 `IotStartup startup headed [MyApp]` `MyApp`
* `IotStartup startup headless [Task1]`는 시작에 대해 등록 된 헤드리스 응용 프로그램을 일치 하는 항목을 나열 `Task1`
* `MyApp`로 식별 된 앱 시작 `IotStartup run [MyApp]`
* `MyApp`로 식별 된 앱 중지 `IotStartup stop [MyApp]`
* 자세한 도움말을 보려면 `IotStartup help` 하세요.

### <a name="change-settings-for-region-and-user-or-speech-language"></a>**지역 및 사용자 또는 음성 언어 설정 변경:**

`IoTSettings` 도구는 지역, 사용자 언어 또는 음성 언어를 변경 합니다. 이는 ProcessLauncher API를 사용 하 여 응용 프로그램에서 호출할 수 있는 명령줄 도구입니다. 이러한 명령은 관리자가 아닌 기본 계정으로 실행 해야 합니다.

* `IotSettings del account {all | username}` 시스템 또는 특정 계정에서 모든 MSA 또는 AAD 계정을 삭제 합니다.  특정 계정은 형식을 사용 username@provider.com
* `IotSettings del diagnostics` 현재 장치에 대해 클라우드의 진단 정보를 삭제 합니다.  그러면 호출 시간까지 기록이 제거 됩니다.  새 진단 정보는 계속 기록 됩니다.
* `IotSettings list account` 장치에 로그인 된 모든 MSA 또는 AAD 계정을 나열 합니다.
* `IotSettings list uilanguage` 모든 UI 언어를 나열 합니다.
* `IotSettings list speechlanguage` 모든 음성 언어를 나열 합니다.
* `IotSettings get uilanguage` 현재 UI 언어를 표시 합니다.
* `IotSettings get speechlanguage` 현재 음성 언어를 표시 합니다.
* `IotSettings get region` 현재 영역을 표시 합니다.
* `IotSettings set uilanguage language\_tag - (e.g. fr-CA)` 설정 하는 기본 UI 언어 프랑스어 (캐나다)
* `IotSettings set speechlanguage language\_tag - (e.g. fr-CA)`에서 음성 언어 프랑스어 (캐나다)를 설정 합니다.
* `IotSettings set region region\_code - (e.g. CA)` 기본 지역을 캐나다로 설정)
* `IotSettings set bluetoothpref {sink | source}` IOT_BLUETOOTH_A2DP_SOURCE 및 IOT_BLUETOOTH_A2DP_SINK 기능을 모두 사용 하 여 빌드된 장치가 두 역할을 모두 지 원하는 다른 장치에 연결 되는 경우 선택할 Bluetooth 역할 기본 설정을 지정 합니다.
* `IotSettings get bluetoothpref` IOT_BLUETOOTH_A2DP_SOURCE 및 IOT_BLUETOOTH_A2DP_SINK를 사용 하 여 빌드된 장치에 대 한 현재 Bluetooth 역할 기본 설정을 반환 합니다.  기본값은 원본입니다.

> [!TIP]
> `IoTSettings -list uiLanguage`은 지원 되는 UI 언어 목록 (실행 된 Windows IoT core 이미지 버전)을 다시 제공 합니다.
    
### <a name="change-default-audio-device-and-volume"></a>**기본 오디오 장치 및 볼륨 변경:**

`IoTCoreAudioControlTool` 도구는 기본 캡처 및 재생 장치를 설정 하 고 볼륨을 변경 하는 것과 같은 오디오 관련 옵션을 제어 합니다. 매개 변수의 전체 목록을 보려면 `IoTCoreAudioControlTool h`를 실행 합니다.

### <a name="manually-installing-appx-files"></a>**수동으로 설치 APPX 파일:**
DeployAppx는에서 설치 및 제거를 사용 하도록 설정 합니다. 배포 시나리오의 APPX 패키지.  를 설치 하기 위한 올바른 방법입니다. 프로덕션 이미지의 APPX 패키지는 [앱 설치](https://docs.microsoft.com/windows/iot-core/develop-your-app/appinstaller#using-provisioning-package-from-wcd) 제목에 설명 된 대로 프로 비전 패키지를 사용 하는 것입니다.  DeployAppx는 쿼리도 지원 합니다. APPX 패키지 정보입니다.

*  `DeployAppx install MyApp.appx`를 설치 합니다. APPX 및 동일한 이름의 인증서 (있는 경우)
* `DeployAppx install force MyApp.appx`는 현재 설치 된를 강제로 제거 합니다. 새을 (를) 설치 하기 전에 패키지 이름이 같은 APPX를 찾았습니다. APPX.  이는를 설치 하는 데 유용 합니다. 현재 설치 된 버전 번호가 같거나 낮은 버전의 APPX입니다. APPX.
* `DeployAppx install retry MyApp.appx` 설치를 다시 시도 합니다. 초당 2 초 지연 시간 동안 APPX를 10 번 실패 합니다.
* `DeployAppx uninstall App_1.0.1.0_x86__publisherid123` 일치 하는 패키지 전체 이름으로 .appx를 제거 합니다.
*  설치 된 `DeployAppx uninstall MyApp.appx` 제거 합니다. 패키지 제품군 이름이 일치 하는 APPX입니다.
* `DeployAppx getpackages` 설치 된 패키지 전체 이름을 나열 합니다.
* `DeployAppx getpackageid IotCoreDefaultApp.appx` 패키지 이름, 패키지 패밀리 이름 및의 패키지 전체 이름을 출력 합니다. APPX.
```cmd
DeployAppx getpackageid IotCoreDefaultApp.appx
         Package Name: 16454Windows10IOTCore.IOTCoreDefaultApplication
  Package Family Name: 16454Windows10IOTCore.IOTCoreDefaultApplication_rz84sjny4rf58
    Package Full Name: 16454Windows10IOTCore.IOTCoreDefaultApplication_2.0.8.0_arm__rz84sjny4rf58
```
* `DeployAppx register appxmanifest.xml` 지원 되지 않음


## <a name="general-command-line-utils"></a>일반 명령줄 유틸리티

### <a name="update-account-password"></a>**계정 암호 업데이트:**

관리자 계정에 대 한 기본 암호를 업데이트 하는 것이 좋습니다. 이렇게 하려면 다음 명령을 실행할 수 있습니다 `net user Administrator [new password]`. 여기서 `[new password]`는 선택한 강력한 암호를 나타냅니다.

### <a name="create-local-user-accounts"></a>**로컬 사용자 계정 만들기:**

다른 사용자에 게 Windows IoT Core 장치에 대 한 액세스 권한을 부여 하려는 경우 `net user [username] [password] /add`를 입력 하 여 PS를 사용 하 여 추가 로컬 사용자 계정을 만들 수 있습니다. 관리자 그룹과 같은 다른 그룹에이 사용자를 추가 하려는 경우 `net localgroup Administrators [username] /add`를 사용 합니다.

### <a name="set-password"></a>**암호 설정:**

장치의 계정에 대 한 암호를 변경 하려면 `net user [account-username] [new-password]`를 실행 하 여 계정 암호를 변경 합니다.

### <a name="query-and-set-device-name"></a>**쿼리 및 설정 장치 이름:**

현재 장치 이름을 식별 하려면 `hostname`을 입력 하면 됩니다. Windows IoT Core 장치 이름을 변경 하려면 `SetComputerName [new machinename]`을 입력 합니다. 이름 변경을 적용 하려면 장치를 다시 시작 해야 할 수 있습니다.

### <a name="basic-network-configuration"></a>**기본 네트워크 구성:**

이미 친숙 한 기본 네트워크 구성 유틸리티 대부분은 `ping.exe`, `netstat.exe`, `netsh.exe`, `ipconfig.exe`, `tracert.exe`, `arp.exe`등의 명령을 포함 하 여 Windows IoT Core에서 사용할 수 있습니다.

### <a name="copy-utilities"></a>**복사 유틸리티:**

Microsoft는 `sfpcopy.exe` 뿐만 아니라 `xcopy.exe`를 비롯 한 친숙 한 도구를 제공 합니다.

### <a name="process-management"></a>**프로세스 관리:**

현재 실행 중인 프로세스를 보려면 `get-process` 또는 `tlist.exe`를 시도해 볼 수 있습니다. 실행 중인 프로세스를 중지 하려면 `kill.exe [pid or process name]`을 입력 합니다.


### <a name="set-boot-option-headless-vs-headed-boot"></a>**설정 부팅 옵션 (헤드리스 및 boot):**

Windows IoT Core 장치는 (표시 기능이 필요한 경우) 또는 헤드리스 (디스플레이가 필요 하지 않거나 사용할 수 있는 경우) 장치 모드로 설정할 수 있습니다. 이 설정을 변경 하려면 `setbootoption.exe [headed | headless]`을 사용 합니다.

> [!NOTE]
> 이 설정을 변경 하면 변경 내용을 적용 하려면 다시 부팅 해야 합니다.

### <a name="task-scheduler"></a>**작업 scheduler:**

예약 된 작업의 현재 목록을 보려면 `schtasks.exe` 명령을 사용 합니다. `/create` 스위치를 사용 하 여 새 작업을 만들거나 `/run` 스위치를 사용 하 여 요청 시 작업을 실행할 수 있습니다. 지원 되는 매개 변수의 전체 목록을 보려면 `schtasks.exe /?`를 사용 하십시오.

### <a name="device-drivers"></a>**장치 드라이버:**

장치 콘솔 유틸리티는 설치 된 장치 및 드라이버를 식별 하 고 관리 하는 데 유용 합니다. 매개 변수의 전체 목록을 보려면 `devcon.exe /?`를 사용 하십시오.

### <a name="registry-access"></a>**레지스트리 액세스:**

설정을 보거나 수정 하기 위해 레지스트리에 액세스 해야 하는 경우 지원 되는 매개 변수의 전체 목록은 `reg.exe /?` 명령을 사용 합니다.

### <a name="services"></a>**서비스:**

Windows 서비스 관리는 `net.exe` 명령을 통해 수행할 수 있습니다. 실행 중인 서비스 목록을 보려면 `net start`를 입력 합니다. 특정 서비스를 시작 하거나 중지 하려면 `net [start | stop] [service name]`을 입력 합니다. 또는 `sc.exe` 명령을 통해 서비스 제어 관리자를 사용할 수도 있습니다.

### <a name="boot-configuration"></a>**부팅 구성:**

`bcdedit.exe`를 사용 하 여 Windows IoT Core 장치의 부팅 구성을 변경할 수 있습니다. 예를 들어 `bcdedit –set testsigning on` 명령을 사용 하 여 testsigning 사용을 설정할 수 있습니다.

### <a name="shutdownrestart-device"></a>**장치 종료/다시 시작:**

장치를 종료 하려면 `shutdown /s /t 0`를 입력 합니다. 장치를 다시 시작 하려면 명령 `shutdown /r /t 0`대신 `/r` 스위치를 사용 합니다.

### <a name="viewing-and-changing-display-settings"></a>**표시 설정 보기 및 변경**
SetDisplayResolution 도구를 사용 하 여 현재 표시 설정을 나열 하 고 지원 되는 값의 목록을 표시할 수 있습니다.  표시의 해상도, 새로 고침 빈도 및/또는 방향을 플랫폼에서 지원 되는 값으로 조정 하는 데 사용할 수 있습니다.  유틸리티는 다음 명령줄 인수를 허용 합니다.

* `SetDisplayResolution` 현재 표시 resoltuion를 나열 합니다.
* `SetDisplayResolution -list` 지원 되는 디스플레이 해상도를 나열 합니다.
* 표시 방향을 변경 `SetDisplayResolution -orientation:[n]` 합니다. 여기서 n = 0, 90180 또는 270입니다.
* 너비와 높이를 픽셀 단위로 변경 `SetDisplayResolution [width] [height]` 
* 너비, 높이 및 새로 고침 빈도 변경 `SetDisplayResolution [width] [height] [refreshrate]` 너비 및 높이는 픽셀 단위로, Hz는 refreshrate입니다. 
* 너비와 높이를 픽셀 단위로 하는 너비, 높이, refreshrate 및 화면 방향을 변경 하는 `SetDisplayResolution [width] [height] [refreshrate] [orientation]` Hz 및 방향 refreshrate 0, 90, 180 또는 270 중 하나입니다.

### <a name="take-screenshot"></a>**스크린샷을 찍습니다.**

`ScreenCapture.exe`를 사용 하 여 Windows I이상 코어 장치의 스크린샷을 사용할 수 있습니다. 예를 들어 `ScreenCapture c:\folder\screencap.jpg`를 실행 하면 스크린샷을 가져와 screencap .jpg 파일에 저장 합니다.

### <a name="get-information-about-network-adapters"></a>**네트워크 어댑터에 대 한 정보 가져오기:**

사용 가능한 모든 네트워크 어댑터 목록을 보려면 `GetAdapterInfo` 도구를 실행 합니다.

### <a name="set-folder-permissions-for-uwp-apps"></a>**UWP 앱에 대 한 폴더 권한 설정:**

유니버설 Windows 앱에서 장치에 있는 모든 폴더를 액세스할 수 하는 것은 아닙니다. UWP 앱에 액세스할 수 폴더를 만들려면 `FolderPermissions` 도구를 사용할 수 있습니다. 예를 들어 `FolderPermissions c:\test -e`를 실행 하 여 UWP 앱에 `c:\test` 폴더에 대 한 액세스를 제공 합니다. 참고로,이 작업은 네이티브 Win32 api (예:) 에서만 작동 합니다. CreateFile2 및 StorageFolder, StorageFile 등과 같은 WinRT api를 사용 하지 않습니다.

### <a name="work-with-serial-ports"></a>**직렬 포트 작업:**
[Mincomm](https://github.com/ms-iot/samples/tree/develop/MinComm) 을 사용 하면 명령줄에서 직렬 포트로 작업할 수 있습니다. 이 샘플은 ms iot 샘플 리포지토리에서 샘플 프로젝트로 제공 됩니다. 

``` 
Usage: MinComm.exe [-list] device_path [baud=<B>] [parity=<P>] [data=<D>] [stop=<S>] [xon={on|off}] [odsr={on|off}] [octs={on|off}] [dtr={on|off|hs}] [rts={on|off|hs|tg}] [idsr={on|off}]

  -list                List all available serial ports on the system and exit.
  device_path          Device path or COM port to open (e.g. COM1)
  baud=<B>             Specifies the transmission rate in bits per second.
  parity={n|e|o|m|s}   Specifies how the system uses the parity bit to check
                       for transmission errors. The abbreviations stand for
                       none, even, odd, mark, and space.
  data={5|6|7|8}       Specifies the number of data bits in a character.
  stop={1|1.5|2}       Specifies the number of stop bits that define the end of
                       a character.
  xon={on|off}         Specifies whether the xon or xoff protocol for data-flow
                       control is on or off.
  odsr={on|off}        Specifies whether output handshaking that uses the
                       Data Set Ready (DSR) circuit is on or off.
  octs={on|off}        Specifies whether output handshaking that uses the
                       Clear To Send (CTS) circuit is on or off.
  dtr={on|off|hs}      Specifies whether the Data Terminal Ready (DTR) circuit
                       is on or off or set to handshake.
  rts={on|off|hs|tg}   Specifies whether the Request To Send (RTS) circuit is
                       set to on, off, handshake, or toggle.
  idsr={on|off}        Specifies whether the DSR circuit sensitivity is on
                       or off.

Parameters that are not specified will default to the port's current
configuration. For more information on the connection parameters, see the
Technet documentation for the Mode command:
  https://technet.microsoft.com/library/cc732236.aspx

Examples:
  Connect to the first serial port found in the port's current configuration:
    MinComm.exe

  List all serial ports on the system:
    MinComm.exe -list

  Open COM1 in 115200 8N1 configuration:
    MinComm.exe COM1 baud=115200 parity=n data=8 stop=1

  Open COM1 in 115200 8N1 configuration:
    MinComm.exe \\.\COM1 baud=115200 parity=n data=8 stop=1

  Open device interface in 115200 8N1 configuration:
    MinComm.exe \\?\USB#VID_FFFF&PID_0005#{86e0d1e0-8089-11d0-9ce4-08003e301f73} baud=115200 parity=n data=8 stop=1```


