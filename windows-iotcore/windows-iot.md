---
title: Windows 10 IoT 개요
author: saraclay
ms.author: saclayt
ms.date: 01/30/2018
ms.topic: article
description: Windows 10 IoT 란 무엇 이며이 사용 하 여 수행할 수 있는 작업에 대해 알아봅니다.
keywords: Windows 10 IoT Enterprise, Windows 10 IoT Core 헤드리스, 음성, 기능, 이진 버전, 버전
ms.openlocfilehash: f1ff68d1efe967eee0472eec54b5354d47c9447a
ms.sourcegitcommit: 1f6afcfee0cb5557dc21c7b15e199bc557d8eedb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65171343"
---
# <a name="an-overview-of-windows-10-iot"></a>Windows 10 IoT 개요 

> [!NOTE]
> 만 Windows 10 컨테이너 Microsoft Azure IoT Edge를 활용 하는 상업용 배포에 대 한 Windows IoT Core 및 Windows IoT Enterprise를 사용 하 여 사용할 수 있습니다.

## <a name="what-is-windows-10-iot"></a>Windows 10 IoT 란?
Windows 10 IoT Internet of Things에 엔터프라이즈급 성능, 보안 및 관리 효율성을 제공 하는 Windows 10 제품군의 멤버 임  Windows의 포함 된 환경, 에코 시스템 및 클라우드 연결을 신속 하 게 프로 비전, 쉽게 관리 및 전체 클라우드 전략을 원활 하 게 연결할 수 있는 보안 장치를 사용 하 여 해당 Internet of Things을 만들려는 조직 허용을 활용 합니다.  

## <a name="windows-10-iot-editions"></a>Windows 10 IoT Editions
Windows 10 IoT는 두 가지 버전에서 제공 됩니다.  Windows 10 IoT Core Windows 10 운영 체제 제품군의 가장 작은 멤버입니다.  만 단일 앱을 실행 하는 동안 아직 관리 효율성 및 보안 Windows 10에서 필요 합니다.  반면, Windows 10 IoT Enterprise는 특정 응용 프로그램 및 주변 장치 집합이 잠기는 전용된 장치를 만드는 특수 기능을 사용 하 여 Windows 10의 전체 버전. 

## <a name="differences-between-windows-10-iot-core-and-windows-10-iot-enterprise"></a>Windows 10 IoT Core 및 Windows 10 IoT Enterprise의 차이점

Windows 10 IoT Core 및 Windows 10 IoT Enterprise를 이름에 유사한 가지 지 원하는 뿐만 아니라 제품 항목에 차이점이 있습니다. 버전 차이 강조 표시 하는 기능 목록은 다음과 같습니다.

> |             | Windows 10 IoT Core K  |  Windows 10 IoT Enterprise  |
> |-------------|----------|---------|
> | 사용자 환경 | 포그라운드에서 한 번에 하나의 UWP 앱 (참조 [IoT 셸 설명서](https://docs.microsoft.com/en-us/windows/iot-core/develop-your-app/iotcoreshell) 앱 backstack 처리에 대 한) 백그라운드 앱 및 서비스를 지원 합니다. | 고급 보안 잠금 기능을 사용 하 여 기존 Windows 셸 |
> | 헤드리스 지원 | 예 | 예 |
> | 지원 되는 앱 아키텍처 | UWP UI만 | 전체 Windows UI 지원 (예:: UWP, WinForms, 등) |
> | Cortana | [*Cortana SDK*](https://developer.microsoft.com/en-us/cortana/devices) | 예 |
> | 도메인 가입 | AAD만 | AAD 및 기존의 도메인 |
> | 관리 | MDM | MDM |
> | 장치 보안 기술 | [TPM](https://docs.microsoft.com/windows/iot-core/secure-your-device/tpm)하십시오 [부팅, BitLocker, Device Guard Secure](https://docs.microsoft.com/windows/iot-core/secure-your-device/securebootandbitlocker), 및 장치 상태 증명 | [TPM](https://docs.microsoft.com/windows/iot-core/secure-your-device/tpm)하십시오 [부팅, BitLocker, Device Guard Secure](https://docs.microsoft.com/windows/iot-core/secure-your-device/securebootandbitlocker) 및 장치 상태 증명 |
> | CPU 아키텍처 지원 | x86, x64 및 ARM | x86 및 x64 |
> | 라이선싱 | 온라인 라이선스 규약 및 포함 된 OEM 계약 무료 | 직접 및 간접 Embedded OEM 계약 |
> | 사용 시나리오 | [디지털 간판](https://www.microsoft.com/en-us/windowsforbusiness/digital-signage), Smart Building, IoT 게이트웨이, HMI, 스마트 홈, 착용 식 장치 | 업계 태블릿, 키오스크, POS [디지털 간판](https://www.microsoft.com/en-us/windowsforbusiness/digital-signage), ATM, 의료 장치, 제조 장치를 씬 클라이언트 |

최소 요구 사항 세부 정보를 참조 하세요 [Windows 하드웨어 사이트](https://docs.microsoft.com/windows-hardware/design/minimum/minimum-hardware-requirements-overview)합니다.

## <a name="differences-between-windows-10-desktop-and-windows-10-iot-core"></a>Windows 10 Desktop 및 Windows 10 IoT Core 차이점

### <a name="different-features-available-on-desktop-and-iot-core"></a>데스크톱 및 IoT Core에서 사용할 수 있는 다양 한 기능

* 받은 편지함 Cortana를 더 이상 1809 (17763) 버전부터 Windows 10 IoT Core 사용할 수 없습니다. 빠르게 시장에 음성 기능을 사용할 장치를 찾으려는 경우 Cortana 지원을 사용 하 여 장치에 통합할 수 있습니다 합니다 [Cortana 디바이스 SDK의 미리 보기](https://developer.microsoft.com/en-us/cortana/devices)합니다.
* 합니다 [FileOpenPicker API](https://docs.microsoft.com/en-us/uwp/api/windows.storage.pickers.fileopenpicker) Windows 10 IoT Core 지원 되지 않습니다. 로컬 드라이브 또는 이동식 저장소에 액세스 하려면 사용자 고유의 응용 프로그램에서이 구현할 수 있습니다.
* Windows 10 IoT Core 장치로 부팅 합니다 [기본 앱](https://docs.microsoft.com/en-us/windows/iot-core/develop-your-app/iotcoredefaultapp) 같은 데스크톱 PC 대신 합니다. 이 응용 프로그램의 목적은 최초 부팅 시 상호 작용할 수 있지만 사용할 수 있도록 하는 친숙 한 셸을 제공 합니다 [오픈 소스 코드](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/IoTCoreDefaultApp) 이 응용 프로그램에 대 한 플러그 앤 플레이에 이러한 기능을 사용할 수 있도록 사용자 고유의 사용자 지정 응용 프로그램입니다.

### <a name="differences-in-driver-supported-areas"></a>드라이버에서 지 원하는 영역의 차이점

* Windows 10 Desktop에는 Windows 10 IoT Core 보다 드라이버 지원 더 합니다. 바탕 화면에서 Windows 10 IoT Core 장치에 대 한 원본에서 드라이버를 빌드 또는 ARM 아키텍처에 대 한 특히 다른 문제를 해결 하려면 찾을 해야 할 수 있습니다를 동일 하 게 하려면 Windows 10 IoT Core 장치 작동 합니다.
* Windows 10 IoT Core (ARM)에 대 한 libusb에 대 한 기본 제공 드라이버가 없는-ARM 아키텍처를 대상으로 하는 원본에서 작성 해야 합니다.

### <a name="differences-in-available-registry-set"></a>사용 가능한 레지스트리 설정의 차이점

* 바탕 화면에서 "자동 숨기기 스크롤 막대의 Windows" off로 설정할 수 있는 하는 옵션이 있습니다. 다음 레지스트리 항목에 의해 제어 됩니다. 

```
HKEY_CURRENTUSER\Control Panel\Accessibility
```

* 기본적으로 Windows 10 IoT Core 장치에 이러한 레지스트리 하지 않습니다. 원하는 경우 "동적 스크롤 막대" 등록을 추가 해야 합니다.
* UWP 응용 프로그램에서 자동 숨기기 스크롤 막대를 사용 하려면 등록 하 고 값이 같은 "1"을 설정 하는 "DynamicScrollbars"를 추가할 수 있습니다.

```
REG ADD "HKCU\Control Panel\Accessibility" /v DynamicScrollbars /t REG_DWORD \d "1"
```

* 기본 계정에서 레지스트리 키를 설정 해야 합니다. ScrollViewer의 XAML 설정이 "Visible" 인 경우 0 nthe 레지스트리 설정을 스크롤 막대 표시 여부 regardlss를 강제로 스크롤 UI에 표시 하도록 충분 한 콘텐츠가 있습니다. 레지스트리 설정을 1은 충분 한 콘텐츠가 있을 때까지 숨겨진 스크롤 막대를 유지 합니다.

```
<TextBox Height="200" Width="100" IsEnabled="True" FontSize="50" TextWrapping="Wrap" ScrollViewer.VerticalScrollBarVisibility="Visible" Text="..."/>
```

* 마지막으로, ScrollViewer XAML의 설정이 "Auto" 경우 다음 레지스트리 설정을 0만 표시 됩니다 전체 스크롤 막대를 충분 한 콘텐츠가 스크롤 막대를 표시 하는 경우. 레지스트리 설정을 1 이면 내용이 없을 때 콘텐츠 또는 숨겨진 경우에 충분 한 후 스크롤 막대에 표시 됩니다.

```
<TextBox Height="200" Width="100" IsEnabled="True" FontSize="50" TextWrapping="Wrap" ScrollViewer.VerticalScrollBarVisibility="Auto" Text="..."/>
```

### <a name="different-commands-supported"></a>지원 되는 다른 명령

* 제거-AppxPackage PowerShell 명령에는 Windows 10 IoT Core는 없지만 데스크톱에서 작동합니다.
* 장치에서 일부 폴더 유니버설 Windows 앱에서 액세스할 수 있습니다. Windows 10 IoT Core는 폴더에 UWP 앱에 액세스할 수 있도록 FolderPermissions 도구를 사용할 수 있습니다. 예를 들어 c:\test 폴더에 UWP 앱 액세스 권한을 부여 하려면 FolderPermissions c:\test-e를 실행 합니다. 그러나, 바탕 화면에서 가능 하지 않습니다.

Windows 10 IoT Core 유지 되므로 시간이 지남에 따라이 게시물에 표시 된 모든 차이 사라질 수를 업데이트 합니다.

## <a name="iot-edge-support-for-windows-10-iot"></a>Windows 10 IoT에 대 한 IoT Edge 지원
Azure IoT Edge 문서에 Windows 10 IoT를 위한 하세요 "운영 체제"에 대 한 자세한 내용은 지원 IoT Edge에 대 한 자세한 내용을 알아보려면 [여기](https://docs.microsoft.com/en-us/azure/iot-edge/support#operating-systems)합니다.


## <a name="helpful-resources"></a>유용한 리소스
* [Windows 10 IoT Enterprise](windows-iot-enterprise.md)
* [Windows 10 IoT Core](windows-iot-core.md)
