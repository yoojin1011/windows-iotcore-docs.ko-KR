---
title: 미디어 전송 프로토콜
author: PawelWMS
ms.author: pawelwi
ms.date: 12/06/2017
ms.topic: article
description: USB를 통해 장치 간에 파일을 전송 하는 선택적 MTP (미디어 전송 프로토콜) 기능을 사용 하도록 설정 하는 방법에 대해 알아봅니다.
keywords: windows iot, MTP, 미디어 전송 프로토콜, 파일 전송, 장치
ms.openlocfilehash: 72856617c8d49a1b06eadd13ab5fb085340d2ed4
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "60168041"
---
# <a name="media-transfer-protocol"></a>미디어 전송 프로토콜
MTP (미디어 전송 프로토콜)를 사용 하면 USB를 통해 Windows 10 IoT Core 장치 간에 파일을 전송할 수 있습니다. 장치의 내부 저장소 및 SD 카드 (있는 경우)에 대 한 액세스를 허용 합니다.

이 기능은 [Windows 10 Iot Core 패키지](https://www.microsoft.com/en-us/download/details.aspx?id=55031)에서 다운로드 하 여 설치할 수 있는 Iot core 키트의 일부입니다.

## <a name="how-to-install-the-mtp-feature-on-a-device-running-windows-10-iot-core"></a>Windows 10 IoT Core를 실행 하는 장치에 MTP 기능을 설치 하는 방법

### <a name="provisioning-the-device-with-required-packages"></a>필수 패키지를 사용 하 여 장치 프로 비전

1. [Powershell](../connect-your-device/PowerShell.md) 또는 [SSH](../connect-your-device/SSH.md) 를 시작 하 고 Windows 10 IoT Core를 실행 하는 장치에 액세스 합니다.
2. Powershell 또는 SSH에서 다음을 수행 합니다.
    1. 대상 컴퓨터에 임시 폴더를 만듭니다 (예: `C:\MTPTemp`).
    2. 장치의 아키텍처에 따라 PC (`C:\Program Files (x86)\Windows Kits\10\MSPackages\Retail\<arch>\fre`)에서 다음 패키지를로 `C:\MTPTemp`복사 합니다.
        * `Microsoft-OneCoreUAP-Mtp-UserService-Package.cab`
        * `Microsoft-OneCoreUAP-Mtp-UserService-Package_Lang_en-US.cab`
        * `Microsoft-WindowsStorSvc-API-Schema-Extension-Package.cab`
        * `Microsoft-WindowsStorSvc-API-Schema-Extension-Package_Lang_en-US.cab`
    3. 에서 `C:\MTPTemp` 다음 명령을 실행 하 여 IoT 장치의 시스템 이미지에 패키지를 설치 합니다.
        * `ApplyUpdate.exe -stage Microsoft-OneCoreUAP-Mtp-UserService-Package.cab`
        * `ApplyUpdate.exe -stage Microsoft-OneCoreUAP-Mtp-UserService-Package_Lang_en-US.cab`
        * `ApplyUpdate.exe -stage Microsoft-WindowsStorSvc-API-Schema-Extension-Package.cab`
        * `ApplyUpdate.exe -stage Microsoft-WindowsStorSvc-API-Schema-Extension-Package_Lang_en-US.cab`
        * `ApplyUpdate.exe -commit`
3. 장치가 업데이트 OS로 부팅 되 고, MTP 기능을 설치 하 고, MainOS로 다시 부팅 합니다.

### <a name="enabling-the-mtp-usb-interface"></a>MTP USB 인터페이스 사용

장치에서 MainOS로 돌아오면, MTP를 포함 하도록 업그레이드 해야 합니다. 이 작업을 수행 하려면 추가 작업을 수행 하는 데 필요 합니다.
Usb [레지스트리 설정](https://docs.microsoft.com/windows-hardware/drivers/usbcon/usb-registry-settings-for-a-function-controller-driver) 문서에서는 usb 구성에 대해 자세히 설명 합니다.

`HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN\Configurations\Default` 키를 사용 하 여 사용할 수 있는 기본 사용 안 함 구성을 수정할 수 있지만 시스템 업데이트에 의해 덮어쓰여지지 않으므로 자체를 정의 하는 것이 좋습니다.

#### <a name="creating-a-new-usbfn-configuration-with-the-mtp-interface"></a>MTP 인터페이스를 사용 하 여 새로 구성 된 새 구성 만들기

MTP를 사용 하 여 새 구성을 추가 하려면 다음 단계를 수행 합니다.
1. 아래 `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN\Configurations`에 새 키를 추가 합니다. 예를 들어, `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN\Configurations\MyConfiguration` 같은 형식입니다.
2. 새 키 아래에서와 같은 `REG_MULTI_SZ` `MTP`값 `InterfaceList` 을 만듭니다.
3. 동일한 키에서와 같은 `REG_BINARY` `2800000000010400010000000000000000014D545000000000000000000000000000000000000000`값 `MSOSCompatIdDescriptor` 을 만듭니다.
4. 새로 만든 키의 `REG_SZ` 이름과 `CurrentConfiguration` 같은 새 값을 추가합니다.`HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN` 이 경우에는 `MyConfiguration`입니다.
5. [**선택 사항**] 1과 같은 새 `REG_DWORD` 값 `IncludeDefaultCfg` 을 추가합니다.`HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN` 그러면 USB 드라이버가 MTP와 함께 기본 인터페이스를 열거 합니다.

> [!NOTE]
> 사용자 지정 구성을 이미 사용 하 고 있는 경우 새로 만드는 대신 수정 해야 합니다.

#### <a name="adding-the-mtp-interface-to-an-existing-configuration"></a>기존 구성에 MTP 인터페이스 추가

다음 단계를 수행 하 여 기존로 구성 된 작업에 MTP를 추가 합니다.
1. `CurrentConfiguration` 아래`HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN`값을 확인 하 여 현재 구성을 찾습니다. 값이 있는 경우 현재 구성은에서 `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN\Configurations\[CurrentConfiguration]`찾을 수 있습니다. 그렇지 않으면이 고 `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN\Configurations\Default`, 그렇지 않으면입니다.
2. 현재 구성 키 아래에 `\0MTP` `InterfaceList`값을 추가 합니다. ***\ 0*** 부분은의 `InterfaceList` `REG_MULTI_SZ` 형식으로 사용 되며 값 사이에이 구분 기호가 필요 합니다.
3. MTP 설명자를 포함 하도록 값을수정합니다.`MSOSCompatIdDescriptor` 현재 `InterfaceList` 값 아래에 있는 모든 인터페이스를 포함 하는 유효한 설명자를 만들려면 [이 페이지](https://msdn.microsoft.com/windows/hardware/gg463179.aspx)의 맨 아래에 있는 지침 설명서를 따르세요. *OS_Desc_CompatID* 설명자의 형식에 대 한 설명과 설명자에 여러 인터페이스를 포함 하는 예제를 제공 합니다. MTP의 호환 및 하위 호환 Id는 동일한 페이지 에서도 사용할 수 있으며 예제 중 하나에서 사용 됩니다.

## <a name="how-to-include-mtp-in-your-custom-ffu"></a>사용자 지정 FFU에 MTP를 포함 하는 방법

1. OEM 입력 파일에 **IOT_MTP** 기능 ID를 추가 합니다. 이는 "[**필수 패키지를 사용 하 여 장치 프로 비전**](#provisioning-the-device-with-required-packages)" 섹션의 단계와 동일 합니다.
2. "[**MTP 인터페이스를 사용 하 여 새 작업 fn 구성 만들기**](#creating-a-new-usbfn-configuration-with-the-mtp-interface)" 섹션에서 설명한 대로 동일한 레지스트리 변경 내용을 적용 해야 합니다. [다음 지침](https://docs.microsoft.com/windows-hardware/manufacture/iot/add-a-registry-setting-to-an-image) 에 따라 ffu에 레지스트리 변경 내용을 적용 하는 방법을 알아봅니다.
3. Image\FFU.를 만듭니다. 자세한 내용은 [이 문서](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image) 를 참조 하세요.

> [!WARNING]
> 기본 구성을 수정 하는 것은 FFU 사용자 지정을 통해 시도 해서는 안 됩니다. 시스템 정의 항목은 시스템 업데이트로 새로 고치거 나 변경 될 수 있으며 사용자 지정 설정은 모두 손실 됩니다.

## <a name="how-to-setup-the-mtp-sd-card-filter"></a>MTP SD 카드 필터를 설정 하는 방법

기본적으로 MTP는 장치에 있는 경우 SD 카드의 모든 콘텐츠를 열거 합니다. 그러나이 열거를 특정 하위 폴더로 제한할 수 있습니다. 이렇게 하려면 레지스트리 키 `MTPSDFolderFilter` `HKEY_LOCAL_MACHINE\Software\Microsoft\MTP`아래에 레지스트리 값을 추가 해야 합니다.
값은 형식이 `REG_SZ` 며 MTP에서 열거할 폴더에 대 한 상대 경로를 포함 해야 합니다. 폴더가 아직 없는 경우 자동으로 만들어집니다.

샘플 경로:
- \FirstLevelDirectory;
- FirstLevelDirectory;
- \FirstLevelDirectory\SecondLevelDirectory;
- Never\Before\Created\Directory.

> [!WARNING]
> 과 같은 `C:\Some\Folder\Path` 드라이브 문자를 포함 하는 절대 경로를 사용 하지 마세요. SD 카드를 열거 하지 못할 수 있습니다.

특정 레지스트리 항목으로 이미지를 사용자 지정 하는 방법에 대 한 자세한 내용은 [이 링크](https://docs.microsoft.com/windows-hardware/manufacture/iot/add-a-registry-setting-to-an-image) 를 참조 하세요.
