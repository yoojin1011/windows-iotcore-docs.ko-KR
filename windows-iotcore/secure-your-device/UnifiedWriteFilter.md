---
title: 통합 쓰기 필터 사용
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 통합 쓰기 필터를 사용 하 여 데이터 쓰기에서 실제 저장소 미디어를 보호 하는 방법에 대해 알아봅니다.
keywords: windows iot, 통합 쓰기 필터, 보안, 메모리, 저장소 미디어
ms.openlocfilehash: d1d6927fe19b5888ef0393d0b101065096cd9f63
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "60167560"
---
# <a name="using-the-unified-write-filter-uwf-on-windows-10-iot-core"></a>Windows 10 IoT Core에서 UWF (통합 쓰기 필터) 사용

> [!WARNING]
> UWF에는 동적 디스크가 지원 되지 않습니다.

UWF (통합 쓰기 필터)는 데이터 쓰기에서 실제 저장소 미디어를 보호 하는 기능입니다. UWF는 보호 볼륨에 대한 모든 쓰기 시도를 가로채서 가상 오버레이로 리디렉션합니다. 따라서 장치의 신뢰성과 안정성을 높이고 플래시 메모리 미디어(예: SSD) 같은 민감한 미디어에서 마모를 줄일 수 있습니다.

자세한 내용은 [통합 쓰기 필터](https://docs.microsoft.com/windows-hardware/customize/enterprise/unified-write-filter) 에 대 한 설명서를 참조 하세요.

## <a name="how-to-install-uwf-on-a-device-running-windows-10-iot-core"></a>Windows 10 IoT Core를 실행 하는 장치에 UWF를 설치 하는 방법

* 최신 버전의 Windows 10 IoT Core 키트가 아직 없는 경우 [windows 10 Iot Core 패키지](https://www.microsoft.com/en-us/software-download/windows10iotcore)를 다운로드 하 여 설치 합니다.
* 장치 아키텍처에 따라 PC ( `Microsoft-IoTUAP-UnifiedWriteFilter-Package.cab` `C:\Program Files (x86)\Windows Kits\10\MSPackages\Retail\<arch>\fre\`)에서 장치 (예 `Microsoft-IoTUAP-UnifiedWriteFilter-Package_Lang_en-us.cab` : [Windows 파일 공유](../manage-your-device/WindowsFileSharing.md))로 UWF 패키지 (및)를 복사 합니다.
* [SSH](../connect-your-device/SSH.md) 또는 [Powershell](../connect-your-device/PowerShell.md) 을 시작 하 고 Windows 10 IoT Core를 실행 하는 장치에 액세스 합니다.
* SSH 또는 Powershell에서 다음을 수행 합니다.
  * 파일을 복사한 디렉터리로 변경 합니다.
    * `cd C:\<dir>`
  * 다음 명령을 실행 하 여 IoT 장치 시스템 이미지에 패키지를 설치 합니다.
    * `applyupdate –stage .\Microsoft-IoTUAP-UnifiedWriteFilter-Package.cab`
    * `applyupdate –stage .\Microsoft-IoTUAP-UnifiedWriteFilter-Package_Lang_en-us.cab`
    * `applyupdate –commit`
* 장치가 업데이트 OS로 부팅 되 고, UWF 기능을 설치 하 고, MainOS로 다시 부팅 합니다.
* 장치가 MainOS로 돌아오면 UWF 기능이 준비 되어 사용할 수 있습니다. Powershell 또는 SSH 창에 입력 ```uwfmgr.exe``` 하 여이를 확인할 수 있습니다.

  ![Windows 10 IoT Core의 uwfmgr](../media/UnifiedWriteFilter/uwfmgr.png)


## <a name="how-to-include-uwf-in-your-custom-ffu"></a>사용자 지정 FFU에 UWF를 포함 하는 방법 

* OEM 입력 파일에 **IOT_UNIFIED_WRITE_FILTER** 기능 id 추가 
* Image\FFU.를 만듭니다. 지침은 [기본 이미지 만들기](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image) 를 참조 하세요.


## <a name="how-to-use-uwf"></a>UWF를 사용 하는 방법

UWF는 Powershell 또는 SSH 세션을 통해 uwfmgr 도구를 사용 하 여 구성할 수 있습니다.
IoT Core에서 지원 되지 않는 아래 나열 된 일부 명령을 제외 하 고 사용 가능한 옵션에 대 한 읽기 [ `uwfmgr.exe` 도구](https://docs.microsoft.com/windows-hardware/customize/enterprise/uwfmgrexe) 입니다.
오버레이 구성의 기본 설정을 검토 하 고 요구 사항에 따라 조정 합니다.

[통합 쓰기 필터 CSP](https://docs.microsoft.com/windows/client-management/mdm/unifiedwritefilter-csp)를 사용 하 여 MDM 채널을 통해 UWF를 구성할 수도 있습니다.


* 예를 들어 다음 명령 조합을 사용 하 여 C 드라이브를 보호 하도록 uwfmgr 및를 구성할 수 있습니다.

  `uwfmgr.exe filter enable`쓰기 필터를 사용 하도록 설정 합니다.
  <br>
  `uwfmgr.exe volume protect c:`볼륨 C를 보호 합니다.
  <br>
  `shutdown /r /t 0`장치를 다시 시작 하 여 쓰기 필터 설정을 적용 합니다.

모든 uwfmgr 설정을 적용 하려면 *다시 부팅* 해야 합니다. 


## <a name="protecting-a-data-volume"></a>데이터 볼륨 보호

IoT Core의 데이터 볼륨은 볼륨의 GUID를 사용 하 여 보호할 수 있습니다. 사용 가능한 볼륨의 GUID는 다음 명령을 통해 찾을 수 있습니다.

  `dir /AL`
  <br>
  `uwfmgr.exe volume protect \\?\Volume {GUID}`


  ![Windows 10 IoT Core에서 볼륨 보호](../media/UnifiedWriteFilter/uwfmgr_protect.png)

### <a name="recommended-exclusions"></a>권장 제외
데이터 볼륨을 보호 하는 경우 Windows OS 서비스에서 액세스 하는 서비스 및 로깅 폴더에 대 한 예외를 추가 하는 것이 좋습니다.

```
C:\Data\Users\System\AppData\Local\UpdateStagingRoot
C:\Data\SharedData\DuShared
C:\Data\SystemData\temp
C:\Data\users\defaultaccount\appdata\local\temp
C:\Data\Programdata\softwaredistribution
C:\Data\systemdata\nonetwlogs
```

제외를 추가 하려면:`uwfmgr.exe file Add-Exclusion <file/folder name>`



## <a name="servicing-uwf-protected-devices"></a>UWF로 보호 된 장치 서비스

> [!Note]
> Windows 10 IoT Core 릴리스 1709, 버전 16299부터 주 OS 볼륨 (C:\) 은 UWF로 보호할 수 있으며 특별 한 단계 없이 *자동으로* 서비스를 제공 합니다.

보호 된 데이터 볼륨을 사용 하 여 UWF로 보호 된 장치를 서비스 하려면 다음 단계가 필요 합니다.

* `uwfmgr.exe filter disable`UWF 사용 안 함
* `shutdown /r /t 0`장치를 다시 부팅 하 여 UWF 사용 안 함
* 서비스를 사용 하도록 설정 (프로 비전 패키지 또는 MDM을 사용 하 여 업데이트 정책 설정)
   * 서비스 업데이트를 수행 하기 위해 장치가 자동으로 다시 부팅 됩니다.
* `uwfmgr.exe filter enable`UWF 사용
* `shutdown /r /t 0`장치를 다시 부팅 하 여 UWF 사용

## <a name="unsupported-uwfmgrexe-commands"></a>지원 되지 않는 uwfmgr 명령

**UWF 서비스 모드** 는 IoT Core에서 지원 되지 않습니다.

`uwfmgr.exe`Windows 10 IoT Core는 아래 나열 된 명령을 지원 하지 않습니다.

```
Filter 
    Shutdown 
    Restart 
Servicing 
    Enable 
    Disable 
    Update-Windows
```
