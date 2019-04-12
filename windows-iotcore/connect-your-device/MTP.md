---
title: 미디어 전송 프로토콜
author: PawelWMS
ms.author: pawelwi
ms.date: 12/06/2017
ms.topic: article
description: USB 통해 장치에서 파일을 전송할 선택적 프로토콜 MTP (미디어 전송) 기능을 사용 하는 방법을 알아봅니다.
keywords: windows iot, MTP, 미디어 전송 프로토콜, 파일 전송 장치
ms.openlocfilehash: 72856617c8d49a1b06eadd13ab5fb085340d2ed4
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512325"
---
# <a name="media-transfer-protocol"></a>미디어 전송 프로토콜
(MTP (미디어 전송 프로토콜)를 사용 하면 USB 통해 Windows 10 IoT Core 장치에서 파일을 전송할 수 있습니다. 있는 경우 장치의 내부 저장소를 SD 카드에 대 한 액세스를 허용 합니다.

기능을 다운로드 하 고에서 설치할 수 있는 IoT Core 키트의 일부인 합니다 [Windows 10 IoT Core 패키지](https://www.microsoft.com/en-us/download/details.aspx?id=55031)합니다.

## <a name="how-to-install-the-mtp-feature-on-a-device-running-windows-10-iot-core"></a>MTP 기능을 Windows 10 IoT Core 실행 하는 장치에 설치 하는 방법

### <a name="provisioning-the-device-with-required-packages"></a>필요한 패키지를 사용 하 여 장치를 프로 비전

1. 시작 [Powershell](../connect-your-device/PowerShell.md) 하거나 [SSH](../connect-your-device/SSH.md) 및 Windows 10 IoT Core 실행 하는 장치에 액세스 합니다.
2. Powershell 또는 SSH에서 다음을 수행 합니다.
    1. 대상 컴퓨터의 임시 폴더를 만듭니다 (예: `C:\MTPTemp`).
    2. PC에서 다음 패키지를 복사 장치의 아키텍처에 따라 (`C:\Program Files (x86)\Windows Kits\10\MSPackages\Retail\<arch>\fre`)를 `C:\MTPTemp`:
        * `Microsoft-OneCoreUAP-Mtp-UserService-Package.cab`
        * `Microsoft-OneCoreUAP-Mtp-UserService-Package_Lang_en-US.cab`
        * `Microsoft-WindowsStorSvc-API-Schema-Extension-Package.cab`
        * `Microsoft-WindowsStorSvc-API-Schema-Extension-Package_Lang_en-US.cab`
    3. 다음이 명령을 실행 `C:\MTPTemp` IoT 장치의 시스템 이미지에 패키지를 설치 하려면:
        * `ApplyUpdate.exe -stage Microsoft-OneCoreUAP-Mtp-UserService-Package.cab`
        * `ApplyUpdate.exe -stage Microsoft-OneCoreUAP-Mtp-UserService-Package_Lang_en-US.cab`
        * `ApplyUpdate.exe -stage Microsoft-WindowsStorSvc-API-Schema-Extension-Package.cab`
        * `ApplyUpdate.exe -stage Microsoft-WindowsStorSvc-API-Schema-Extension-Package_Lang_en-US.cab`
        * `ApplyUpdate.exe -commit`
3. 장치는 업데이트 OS로 부팅, MTP 기능을 설치 및는 MainOS 하려면 다시 부팅 됩니다.

### <a name="enabling-the-mtp-usb-interface"></a>MTP USB 인터페이스를 사용 하도록 설정

면 장치는 MainOS 돌아갑니다, USBFN 구성을 계속 해야 MTP를 포함 하도록 업데이트 합니다. 이 작업을 수행 하기 위해 MTP USBFN 열거 하는 인터페이스에 추가 해야 합니다.
합니다 [USB 레지스트리 설정을](https://docs.microsoft.com/windows-hardware/drivers/usbcon/usb-registry-settings-for-a-function-controller-driver) 문서 USB의 구성 정보에 설명 합니다.

사용할 수 있는 기본 USBFN 구성을 수정할 수 있는 반면는 `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN\Configurations\Default` 키, 것이 좋습니다 정의 사용자 고유의 시스템 업데이트로 덮어씁니다 가져오기 되지 됩니다.

#### <a name="creating-a-new-usbfn-configuration-with-the-mtp-interface"></a>MTP 인터페이스를 사용 하 여 새 USBFN 구성 만들기

MTP 사용 하 여 새 구성을 추가 하려면 다음이 단계를 수행 합니다.
1. 새 키를 추가 `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN\Configurations`합니다. 예: `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN\Configurations\MyConfiguration`.
2. 새 키 만들기를 `REG_MULTI_SZ` 값 `InterfaceList` 같음 `MTP`합니다.
3. 동일한 키에서 만들기를 `REG_BINARY` 값 `MSOSCompatIdDescriptor` 같음 `2800000000010400010000000000000000014D545000000000000000000000000000000000000000`합니다.
4. 아래 `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN` 새 `REG_SZ` 값 `CurrentConfiguration` 새로 만든된 키의 이름으로 같은 합니다. 이 경우 것 `MyConfiguration`입니다.
5. [**선택 사항**] 아래에서 `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN` 새 `REG_DWORD` 값 `IncludeDefaultCfg` 1과 같습니다. MTP와 함께 기본 인터페이스를 열거 하는 USB 드라이버를 확인 합니다.

> [!NOTE]
> 사용자 지정 구성을 사용 하는 이미를 사용 하는 경우에 새로 만드는 대신 수정 합니다.

#### <a name="adding-the-mtp-interface-to-an-existing-configuration"></a>MTP 인터페이스는 기존 구성 추가

MTP 기존 USBFN 구성에 추가 하려면 다음이 단계를 수행 합니다.
1. 현재 구성을 확인 하 여 찾을 합니다 `CurrentConfiguration` 값 `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN`합니다. 값이 있는 경우 현재 구성에서 찾을 수 있습니다 `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN\Configurations\[CurrentConfiguration]`합니다. 아래에 있는 것이 고, 그렇지 `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN\Configurations\Default`합니다.
2. 현재 구성 키 추가 `\0MTP` 의 값으로 `InterfaceList`입니다. 합니다 ***\0*** 파트 유형으로 사용 됩니다 `InterfaceList` 는 `REG_MULTI_SZ` 값 사이이 구분 기호를 필요로 합니다.
3. 수정 된 `MSOSCompatIdDescriptor` MTP의 설명자를 포함 하는 값입니다. 아래에 있는 현재 모든 인터페이스를 포함 하는 유효한 설명자를 만들기 위해 합니다 `InterfaceList` 값을 맨 아래에 제공 되는 지침 설명서를 따르세요 [이 페이지](https://msdn.microsoft.com/windows/hardware/gg463179.aspx)합니다. *OS_Desc_CompatID.doc* 설명자의 형식 및 설명자에서 여러 인터페이스를 포함 하는 예를 제공 합니다. MTP의 및 부분 호환 Id도 동일한 페이지에 사용할 수 있습니다 하 고 예제 중 하나에서 사용 됩니다.

## <a name="how-to-include-mtp-in-your-custom-ffu"></a>MTP Your Custom FFU 포함 하는 방법

1. 추가 **IOT_MTP** OEM 입력 파일에 기능 ID입니다. 단계를 다음 중 해당 하는이 "[**필요한 패키지를 사용 하 여 장치를 프로 비전**](#provisioning-the-device-with-required-packages)" 섹션.
2. 설명한 것 처럼 동일한 레지스트리 변경 내용을 적용 해야 합니다 "[**MTP 인터페이스를 사용 하 여 새 USBFN 구성을 만드는**](#creating-a-new-usbfn-configuration-with-the-mtp-interface)" 섹션. 따릅니다 [이러한 지침](https://docs.microsoft.com/windows-hardware/manufacture/iot/add-a-registry-setting-to-an-image) 는 FFU 레지스트리 변경 내용을 적용 하는 방법입니다.
3. image\FFU를 만듭니다. 읽기 [이 문서에서는](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image) 지침에 대 한 합니다.

> [!WARNING]
> 기본 구성을 수정 FFU 사용자 지정을 통해 시도 하지 마십시오. 항목 시스템에 정의 된 시스템 업데이트를 새로 고칠/변경할 수 있습니다 하 고 사용자 지정 설정이 손실 됩니다.

## <a name="how-to-setup-the-mtp-sd-card-filter"></a>MTP SD 카드 필터를 설정 하는 방법

기본적으로 MTP는 열거를 SD 카드에 있는 내용의 모든 장치에 있는 경우. 그러나, 특정 하위 폴더에이 열거형을 제한 하는 것이 가능입니다. 이렇게 하려면 레지스트리 값을 추가 해야 합니다 `MTPSDFolderFilter` 레지스트리 키 아래 `HKEY_LOCAL_MACHINE\Software\Microsoft\MTP`합니다.
형식의 값은 `REG_SZ` MTP를 열거 하 고 싶은 폴더에 상대 경로 포함 해야 합니다. 폴더가 아직 존재 하지 않는 경우 자동으로 생성 됩니다.

샘플 경로:
- \FirstLevelDirectory;
- FirstLevelDirectory;
- \FirstLevelDirectory\SecondLevelDirectory;
- Never\Before\Created\Directory 합니다.

> [!WARNING]
> 같은 드라이브 문자를 포함 하는 절대 경로 사용 하지 마십시오 `C:\Some\Folder\Path` -열거 되 고에서 SD 카드 못할 수도 있습니다.

참조 [이 링크](https://docs.microsoft.com/windows-hardware/manufacture/iot/add-a-registry-setting-to-an-image) 특정 레지스트리 항목을 사용 하 여 이미지를 사용자 지정 하는 방법에 대 한 세부 정보에 대 한 합니다.
