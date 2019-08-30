---
title: UEFI 요구 사항
author: parameshbabu
ms.author: pabab
ms.date: 08/28/2017
ms.topic: article
description: Windows 10 IoT Core OS에 대 한 UEFI 요구 사항을 알아봅니다.
keywords: windows iot, 이미지 만들기, 이미지 사용자 지정, OEM 사용자 지정, UEFI
ms.openlocfilehash: efd8f104d61667b443d48e1722e26789a490196b
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "60170411"
---
# <a name="uefi-requirements"></a>UEFI 요구 사항

IoT Core의 UEFI 요구 사항은 데스크톱과 같은 다른 windows 버전과 비슷합니다. 자세한 내용은 [windows의 uefi](https://docs.microsoft.com/windows-hardware/drivers/bringup/uefi-in-windows) 를 참조 하 고, [SoC 플랫폼의 windows 버전에 대 한 uefi 요구 사항은](https://docs.microsoft.com/windows-hardware/drivers/bringup/uefi-requirements-that-apply-to-all-windows-platforms)특히 참조 하세요. 

## <a name="acpi-design"></a>ACPI 디자인

IoT Core의 ACPI 요구 사항에 대 한 자세한 내용은 [SoC 플랫폼용 WINDOWS acpi 디자인 가이드](https://docs.microsoft.com/windows-hardware/drivers/bringup/windows-acpi-design-guide-for-soc-platforms) 를 참조 하세요.

## <a name="replacing-windows-boot-logo"></a>Windows 부팅 로고 바꾸기

BIOS 또는 UEFI에 표시 되는 부팅 로고를 교체 하는 방법에는 여러 가지가 있습니다.

* 한 가지 방법은 UEFI를 사용 하도록 설정 하거나,이를 위해 보드 제조업체 공급 업체에 지불 하 고, UEFI 소스 코드를 직접 변경 하는 것입니다.
* 또는 UEFI 구현이 서명 된 로드 가능한 UEFI 드라이버를 지 원하는 장치에서 부팅 로고를 대체 하는 드라이버를 작성 하 고 Windows 부팅 프로세스에서 로고를 벗어나면 BGRT 테이블을 bootmgr에 제공 하는 방법을 보여 주는 샘플은 [여기](https://github.com/Microsoft/MS_UEFI/tree/share/MsIoTSamples) 에 있습니다. Windows 로고로 교체 하는 대신 부팅 중에 적용 됩니다.

## <a name="smbios-settings"></a>SMBIOS 설정

필요한 최소 SMBIOS 설정은 [OEM 라이선스 요구 사항](OEMLicenseRequirements.md)에 설명 되어 있습니다.

## <a name="io-bus-access"></a>I/o 버스 액세스

Windows IoT Core 및 IoT Enterprise를 사용 하면 사용자 응용 프로그램이 시스템 i/o 핀과 상호 연결할 수 있습니다. 이를 사용 하도록 설정 하려면 ASL 테이블에 특정 구성이 필요 합니다. 자세한 내용은 [Windows 10 IoT Core에서 사용자 모드 액세스 사용](https://docs.microsoft.com/windows/uwp/devices-sensors/enable-usermode-access) 을 참조 하세요.

## <a name="recovery-trigger"></a>복구 트리거

[Windows 10 IoT Core 복구 옵션](Recovery.md) 을 검토 하 고 하드웨어 트리거를 복구 모드로 전환 해야 하는 경우 UEFI 앱에서이를 구현 하 고 Windows 부팅 전에 필요한 bootsequence를 설정 하 여 복구를 호출 해야 할 수 있습니다.

복구 OS로 부팅 하는 데 필요한 bootsequence는 아래에 제공 되어 있습니다.

```
bcdedit /set {bootmgr} bootsequence {a5935ff2-32ba-4617-bf36-5ac314b3f9bf}
```
