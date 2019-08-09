---
title: Windows 10 IoT 개요
author: saraclay
ms.author: saclayt
ms.date: 01/30/2018
ms.topic: article
description: Windows 10 IoT와 이를 통해 수행할 수 있는 작업을 알아봅니다.
keywords: Windows 10 IoT Enterprise, Windows 10 IoT Core, 헤드리스, 음성, 기능, 이진 버전, 버전
ms.openlocfilehash: 1c99541f3b52891d2510fa3fa05df68fac7ced14
ms.sourcegitcommit: c5552007f5456e57512307f51b146406a23fa723
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/02/2019
ms.locfileid: "68739801"
---
# <a name="an-overview-of-windows-10-iot"></a>Windows 10 IoT 개요 

> [!NOTE]
> Windows 컨테이너는 Windows Server, Windows IoT Server, Windows IoT Enterprise 및 Windows IoT Core에서 상업용으로 배포할 수 있습니다.  Windows 10월 업데이트 2018(빌드 17763)부터 Windows 컨테이너는 Windows Enterprise 및 Professional에서 개발/테스트 용도로만 사용할 수 있습니다.

## <a name="what-is-windows-10-iot"></a>Windows 10 IoT란?
Windows 10 IoT는 사물 인터넷에 엔터프라이즈급 성능, 보안 및 관리 효율성을 제공하는 Windows 10 계열 제품입니다.  Windows의 포함된 환경, 에코시스템 및 클라우드 연결을 활용하여 조직에서 신속하게 프로비저닝되고, 쉽게 관리되며 전체 클라우드 전략에 원활하게 연결할 수 있는 보안 디바이스를 사용하여 해당 사물 인터넷을 만들 수 있도록 합니다.  

## <a name="windows-10-iot-editions"></a>Windows 10 IoT 버전
Windows 10 IoT는 두 가지 버전으로 제공됩니다.  Windows 10 IoT Core는 Windows 10 운영 체제 제품군의 가장 작은 멤버입니다.  단일 앱을 실행하는 동안에도 Windows 10에서 기대되는 관리 효율성 및 보안을 여전히 갖습니다.  반면 Windows 10 IoT Enterprise는 특정 애플리케이션 및 주변 기기의 세트에 고정된 전용 디바이스를 만드는 특수 기능이 있는 Windows 10의 정품 버전입니다. 

## <a name="differences-between-windows-10-iot-core-and-windows-10-iot-enterprise"></a>Windows 10 IoT Core와 Windows 10 IoT Enterprise의 차이점

Windows 10 IoT Core 및 Windows 10 IoT Enterprise는 이름이 유사하지만 제공하는 것과 지원하는 것에 차이점이 있습니다. 다음은 버전 차이를 강조 표시하는 기능 목록입니다.

> |             | Windows 10 IoT Core K  |  Windows 10 IoT Enterprise  |
> |-------------|----------|---------|
> | 사용자 환경 | 포그라운드 내 UWP 앱 하나(회당, 앱 BackStack 처리는 [IoT 셸 설명서](https://docs.microsoft.com/en-us/windows/iot-core/develop-your-app/iotcoreshell) 참조). 지원 백그라운드 앱 및 서비스 포함 | 고급 잠금 기능이 있는 기존 Windows 셸 |
> | 헤드리스 지원 | 예 | 예 |
> | 앱 아키텍처 지원 | UWP UI 전용 | 전체 Windows UI 지원(예: UWP, WinForms 등) |
> | Cortana | [*Cortana SDK*](https://developer.microsoft.com/en-us/cortana/devices) | 예 |
> | 도메인 가입 | AAD 전용 | AAD 및 기존 도메인 |
> | Management | MDM | MDM |
> | 디바이스 보안 기술 | [TPM](https://docs.microsoft.com/windows/iot-core/secure-your-device/tpm), [보안 부팅, BitLocker, Device Guard](https://docs.microsoft.com/windows/iot-core/secure-your-device/securebootandbitlocker) 및 디바이스 상태 증명 | [TPM](https://docs.microsoft.com/windows/iot-core/secure-your-device/tpm), [보안 부팅, BitLocker, Device Guard](https://docs.microsoft.com/windows/iot-core/secure-your-device/securebootandbitlocker) 및 디바이스 상태 증명 |
> | CPU 아키텍처 지원 | x86, x64 및 ARM | x86 및 x64 |
> | 라이선싱 | 온라인 라이선싱 계약 및 포함된 OEM 계약, 로열티 없음 | 직접 및 간접 포함된 OEM 계약 |
> | 사용 시나리오 | [디지털 사이니지](https://www.microsoft.com/en-us/windowsforbusiness/digital-signage), 스마트 빌딩, IoT 게이트웨이, HMI, 스마트 홈, 착용식 장치 | 업계 태블릿, 소매 서비스 지점, 키오스크, [디지털 사이니지](https://www.microsoft.com/en-us/windowsforbusiness/digital-signage), ATM, 의료 디바이스, 제조 디바이스, 씬 클라이언트 |

최소 요구 사항 세부 정보는 [Windows 하드웨어 사이트](https://docs.microsoft.com/windows-hardware/design/minimum/minimum-hardware-requirements-overview)를 방문하세요.

서비스 지점에 대해 더 자세히 알고 싶은 경우 [이 항목의 UWP 문서](https://aka.ms/pointofservice)를 방문하세요.

## <a name="differences-between-windows-10-desktop-and-windows-10-iot-core"></a>Windows 10 Desktop과 Windows 10 IoT Core의 차이점

### <a name="different-features-available-on-desktop-and-iot-core"></a>데스크톱 및 IoT Core에서 사용할 수 있는 다양한 기능

* 받은 편지함 Cortana는 버전 1809(17763) 이후 Windows 10 IoT Core에서 더 이상 사용할 수 없습니다. 음성 사용 디바이스를 빠르게 출시하려는 경우 [Cortana 디바이스 SDK의 미리 보기](https://developer.microsoft.com/en-us/cortana/devices)를 사용하여 Cortana 지원을 디바이스에 통합할 수 있습니다.
* [FileOpenPicker API](https://docs.microsoft.com/en-us/uwp/api/windows.storage.pickers.fileopenpicker)는 Windows 10 IoT Core에서 지원되지 않습니다. 로컬 드라이브 또는 이동식 스토리지에 액세스하려면 이를 자신의 애플리케이션에서 구현합니다.
* Windows 10 IoT Core 디바이스가 데스크톱과 같은 PC 대신 [기본 앱](https://docs.microsoft.com/en-us/windows/iot-core/develop-your-app/iotcoredefaultapp)으로 부팅됩니다. 이 애플리케이션의 목적은 최초 부팅 시 상호 작용할 수 있는 친숙한 셸을 제공할 뿐만 아니라, 이 애플리케이션에 대해 [오픈 소스 코드](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/IoTCoreDefaultApp)를 사용할 수 있도록 함으로써 이러한 기능을 사용하여 고유한 사용자 지정 애플리케이션을 플러그 앤 플레이할 수 있습니다.

### <a name="differences-in-driver-supported-areas"></a>드라이버 지원 영역의 차이점

* Windows 10 Desktop에는 Windows 10 IoT Core보다 지원 드라이버가 많습니다. Windows 10 IoT Core에서 테스크톱에서와 동일한 디바이스를 작동시키려면 Windows 10 IoT Core 디바이스용 원본에서 드라이버를 빌드하거나, 특히 ARM 아키텍처에 대한 다른 해결 방법을 찾아야 합니다.
* Windows 10 IoT Core(ARM)용 libusb에 대한 기본 제공 드라이버가 없습니다. ARM 아키텍처를 대상으로 하는 원본에서 빌드해야 합니다.

### <a name="differences-in-available-registry-set"></a>사용 가능한 레지스트리 세트의 차이점

* 데스크톱에서는 "Windows의 스크롤 막대를 자동으로 숨기기" 옵션을 off로 설정할 수 있습니다. 다음 레지스트리 항목에 의해 제어됩니다. 

```
HKEY_CURRENTUSER\Control Panel\Accessibility
```

* 기본적으로 Windows 10 IoT Core 디바이스에는 이러한 레지스트리가 없습니다. 원하는 경우 "동적 스크롤 막대" 레지스터를 추가해야 합니다.
* UWP 애플리케이션에서 자동으로 스크롤 막대 숨기기를 활성화하려면 "DynamicScrollbars"를 추가하고 다음과 같이 값을 "1"로 설정합니다.

```
REG ADD "HKCU\Control Panel\Accessibility" /v DynamicScrollbars /t REG_DWORD \d "1"
```

* 레지스트리 키는 기본 계정에서 설정해야 합니다. ScrollViewer의 XAML 설정이 "Visible"인 경우 레지스트리 설정 0은 UI에 스크롤을 표시하기에 충분한 콘텐츠가 있는지 여부와 상관없이 스크롤 막대를 표시합니다. 레지스트리 설정 1은 충분한 콘텐츠가 있을 때까지 스크롤 막대가 숨겨집니다.

```
<TextBox Height="200" Width="100" IsEnabled="True" FontSize="50" TextWrapping="Wrap" ScrollViewer.VerticalScrollBarVisibility="Visible" Text="..."/>
```

* 마지막으로, ScrollViewer XAML의 설정이 "Auto"인 경우 레지스트리 설정 0은 스크롤 막대를 표시할 수 있는 충분한 콘텐츠가 있을 때에만 전체 스크롤 막대를 표시합니다. 레지스트리 설정이 1이면 콘텐츠가 충분하거나 콘텐츠가 없으면 숨겨진 스크롤 막대가 표시됩니다.

```
<TextBox Height="200" Width="100" IsEnabled="True" FontSize="50" TextWrapping="Wrap" ScrollViewer.VerticalScrollBarVisibility="Auto" Text="..."/>
```

### <a name="different-commands-supported"></a>지원되는 다른 명령

* PowerShell Remove-AppxPackage 명령은 데스크톱에서 작동하지만 Windows 10 IoT Core에서는 작동하지 않습니다.
* 유니버설 Windows 앱에서는 디바이스의 모든 폴더에 액세스할 수 있는 것은 아닙니다. Windows 10 IoT Core에서는 FolderPermissions 도구를 사용하여 UWP 앱에서 액세스할 수 있는 폴더를 만들 수 있습니다. 예를 들어 FolderPermissions c:\test -e를 실행하여 UWP 앱에 c:\test 폴더에 대한 액세스 권한을 부여합니다. 그러나 데스크톱에서는 가능하지 않습니다.

이 게시물에 표시된 명령은 Windows 10 IoT Core가 계속 업데이트되므로 시간이 지남에 따라 변경될 수 있습니다.

## <a name="iot-edge-support-for-windows-10-iot"></a>Windows 10 IoT에 대한 IoT Edge 지원
Windows 10 IoT에 대한 IoT Edge 지원에 대해 알아보려면 Azure IoT Edge 문서 [여기](https://docs.microsoft.com/en-us/azure/iot-edge/support#operating-systems)에서 "운영 체제"에 대해 자세히 알아보세요.


## <a name="helpful-resources"></a>유용한 리소스
* [Windows 10 IoT Enterprise](windows-iot-enterprise.md)
* [Windows 10 IoT Core](windows-iot-core.md)
