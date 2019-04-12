---
title: 통합된 쓰기 필터를 사용 하 여
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 기록 된 데이터에서에서 실제 저장소 미디어를 보호 하기 위해 통합 쓰기 필터를 사용 하는 방법에 알아봅니다.
keywords: windows iot, 통합 쓰기 필터, 보안, 메모리, 저장소 미디어
ms.openlocfilehash: d1d6927fe19b5888ef0393d0b101065096cd9f63
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59515260"
---
# <a name="using-the-unified-write-filter-uwf-on-windows-10-iot-core"></a>통합된 쓰기 필터 (UWF)를 사용 하 여 Windows 10 IoT Core

> [!WARNING]
> 동적 디스크는 UWF에 대해 지원 되지 않습니다.

쓰기 필터 (UWF (통합)에 기록 된 데이터에서에서 실제 저장소 미디어를 보호 하는 기능입니다. UWF는 보호 볼륨에 대한 모든 쓰기 시도를 가로채서 가상 오버레이로 리디렉션합니다. 따라서 장치의 신뢰성과 안정성을 높이고 플래시 메모리 미디어(예: SSD) 같은 민감한 미디어에서 마모를 줄일 수 있습니다.

설명서를 읽기를 [통합 쓰기 필터](https://docs.microsoft.com/windows-hardware/customize/enterprise/unified-write-filter) 자세한 내용은 합니다.

## <a name="how-to-install-uwf-on-a-device-running-windows-10-iot-core"></a>Windows 10 IoT Core 실행 하는 장치에서 UWF 설치 하는 방법

* 하지 않은 경우 현재 버전의 Windows 10 IoT Core 키트 아직, 다운로드 및 설치 합니다 [Windows 10 IoT Core 패키지](https://www.microsoft.com/en-us/software-download/windows10iotcore)합니다.
* UWF 패키지를 복사 하 여 장치 아키텍처에 따라 ( `Microsoft-IoTUAP-UnifiedWriteFilter-Package.cab` 하 고 `Microsoft-IoTUAP-UnifiedWriteFilter-Package_Lang_en-us.cab` ) PC에서 (`C:\Program Files (x86)\Windows Kits\10\MSPackages\Retail\<arch>\fre\`) 장치 (예를 들어 [Windows 파일 공유](../manage-your-device/WindowsFileSharing.md)).
* 시작 [SSH](../connect-your-device/SSH.md) 하거나 [Powershell](../connect-your-device/PowerShell.md) 및 Windows 10 IoT Core 실행 하는 장치에 액세스 합니다.
* SSH 또는 Powershell에서 다음을 수행 합니다.
  * 파일을 복사한 디렉터리로 변경 합니다.
    * `cd C:\<dir>`
  * IoT 장치 시스템 이미지에 패키지를 설치 하려면 다음이 명령을 실행 합니다.
    * `applyupdate –stage .\Microsoft-IoTUAP-UnifiedWriteFilter-Package.cab`
    * `applyupdate –stage .\Microsoft-IoTUAP-UnifiedWriteFilter-Package_Lang_en-us.cab`
    * `applyupdate –commit`
* 장치는 업데이트 OS로 부팅, UWF 기능을 설치 및는 MainOS 하려면 다시 부팅 됩니다.
* 장치는 MainOS 돌아갑니다, 면 UWF 기능은 준비 하 고 사용할 수 있습니다. 입력 하 여 확인할 수 있습니다 ```uwfmgr.exe``` Powershell 또는 SSH 창에 있습니다.

  ![Windows 10 IoT Core uwfmgr.exe](../media/UnifiedWriteFilter/uwfmgr.png)


## <a name="how-to-include-uwf-in-your-custom-ffu"></a>UWF Your Custom FFU 포함 하는 방법 

* 추가 **IOT_UNIFIED_WRITE_FILTER** OEM 입력 파일에 기능 id 
* image\FFU를 만듭니다. 읽기 [기본 이미지를 만드는](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image) 지침에 대 한 합니다.


## <a name="how-to-use-uwf"></a>UWF를 사용 하는 방법

UWF는 Powershell 또는 SSH 세션을 통해 uwfmgr.exe 도구를 사용 하 여 구성할 수 있습니다.
읽기 [ `uwfmgr.exe` 도구](https://docs.microsoft.com/windows-hardware/customize/enterprise/uwfmgrexe) IoT Core에서 지원 되지 않는 일부 명령 아래에 나열 된 예외와 함께 사용할 수 있는 옵션에 대 한 합니다.
오버레이 구성의 기본 설정을 검토 하 고 요구 사항에 따라 적용 됩니다.

UWF 사용 하 여 MDM 채널을 통해 구성할 수도 있습니다 [통합 쓰기 필터 CSP](https://docs.microsoft.com/windows/client-management/mdm/unifiedwritefilter-csp)합니다.


* 명령의 다음 조합 uwfmgr를 사용 하도록 설정 하 고 C 드라이브를 보호 하기 위해 구성 하는 예를 들어,

  `uwfmgr.exe filter enable`      쓰기 필터를 사용 하도록 설정
  <br>
  `uwfmgr.exe volume protect c:`  C 볼륨을 보호
  <br>
  `shutdown /r /t 0`              쓰기 필터 설정을 적용 하기 위해 장치를 다시 시작

*다시 부팅* 모든 uwfmgr 설정을 적용 하기 위해 필요 합니다. 


## <a name="protecting-a-data-volume"></a>데이터 볼륨을 보호

볼륨 GUID를 사용 하 여 IoT Core에서 데이터 볼륨을 보호할 수 있습니다. 다음 명령을 통해 사용 가능한 볼륨에 대 한 GUID는 찾을 수 있습니다.

  `dir /AL`
  <br>
  `uwfmgr.exe volume protect \\?\Volume {GUID}`


  ![Windows 10 IoT Core 볼륨을 보호](../media/UnifiedWriteFilter/uwfmgr_protect.png)

### <a name="recommended-exclusions"></a>권장 되는 예외
데이터 볼륨을 보호 하는 경우에 서비스 및 Windows OS 서비스에서 액세스할 수 있는 로깅 폴더에 대 한 예외를 추가 하는 것이 좋습니다.

```
C:\Data\Users\System\AppData\Local\UpdateStagingRoot
C:\Data\SharedData\DuShared
C:\Data\SystemData\temp
C:\Data\users\defaultaccount\appdata\local\temp
C:\Data\Programdata\softwaredistribution
C:\Data\systemdata\nonetwlogs
```

제외를 추가 합니다. `uwfmgr.exe file Add-Exclusion <file/folder name>`



## <a name="servicing-uwf-protected-devices"></a>장치를 보호 UWF 서비스

> [!Note]
> Windows 10 IoT Core 릴리스 1709 버전 16299, 기본 OS 볼륨을 시작 (c:\) UWF로 보호할 수 있고 서비스 *자동으로* 특별 단계 없이 합니다.

다음 단계는 보호 된 데이터 볼륨을 사용 하 여 서비스 UWF 보호 장치에 필요 합니다.

* `uwfmgr.exe filter disable` UWF를 사용 하지 않도록 설정
* `shutdown /r /t 0` UWF를 사용 하지 않도록 설정 하는 장치를 다시 부팅
* (사용 하 여 프로 비전 패키지 또는 MDM 업데이트 정책 설정) 서비스를 사용 하도록 설정
   * 장치를 서비스 하는 데 자동으로 다시 부팅 하는 업데이트
* `uwfmgr.exe filter enable` UWF를 사용 하도록 설정
* `shutdown /r /t 0` UWF를 사용 하도록 설정 하려면 장치를 다시 부팅

## <a name="unsupported-uwfmgrexe-commands"></a>지원 되지 않는 uwfmgr.exe 명령

**UWF 서비스 모드** IoT Core에서 지원 되지 않습니다.

`uwfmgr.exe` Windows 10 IoT Core 아래 나열 된 명령을 지원 하지 않습니다.

```
Filter 
    Shutdown 
    Restart 
Servicing 
    Enable 
    Disable 
    Update-Windows
```
