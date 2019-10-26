---
title: Windows 10 IoT Core의 USB 지원 및 이중 역할에 대 한 개요
ms.date: 10/11/2017
ms.topic: article
description: Windows 10 IoT Core 장치에 대해 사용자 지정 하는 방법 뿐만 아니라 USB 지원 및 이중 역할에 대해 알아봅니다.
keywords: windows iot, USB 지원, 이중 역할, USB
ms.openlocfilehash: 11b359d096aedf44e0dac8f87d343caa5db3f57f
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72917326"
---
# <a name="overview-of-usb-support-and-dual-role"></a>USB 지원 및 이중 역할 개요

USB (범용 직렬 버스)는 키보드, 마우스, 조이스틱, 프린터, 스캐너, 저장 장치, 모뎀 및 비디오와 같은 주변 장치에 대 한 표준 저렴 한 연결을 보장 하는 확장 가능한 핫 플러그형 플러그 앤 플레이 직렬 인터페이스를 제공 합니다. 회의 카메라.  
USB 장치에 대해 설명할 때 USB 함수 스택은 플러그 앤 플레이 Manager에서 열거 하 고 로드 하는 드라이버 그룹을 나타내며, 복합 USB 장치는 단일 구성에서 여러 인터페이스를 지원할 수 있습니다. 이 문서에서 설명 하는 대부분의 기능은 usb 2.0에 대 한 이중 역할, 일반적으로 usb (usb) 또는 USB (usb)와 관련 된 것으로, usb 3.0 및 usb 2.0와 어떻게 다른 지에 대해 알고 있는 것도 유용 합니다. USB OTG는 장치에 대 한 두 가지 역할을 정의 합니다. 즉, OTG는 장치 및 OTG B-장치 이며,이를 통해 연결에 전원을 공급 하는 측면과 초기에 호스트를 지정 합니다. 모든 OTG 컨트롤러는 두 역할을 모두 지원 하므로 "OTG 컨트롤러"가 아닌 "이중 역할" 컨트롤러 라고도 합니다. 반면에 USB 3.0는 호스트 또는 주변 장치로 장치를 만들 수 있습니다. 일부 장치는 다른 쪽에서 검색 된 종류에 따라 두 역할을 모두 수행할 수 있습니다. 이러한 유형의 포트를 DRD (이중 역할 데이터) 라고 합니다. 이러한 두 장치가 연결 되 면 역할은 임의로 할당 되지만 한 쪽에서 교환이 가능 합니다. 

## <a name="architecture-of-usb-function-in-windows-10-iot-core"></a>Windows 10 IoT Core의 USB 기능 아키텍처

Windows 10 IoT 플랫폼은 USB 장치 역할을 하는 경우 여러 구성 중 하나를 사용 합니다. 각 구성에는 하나 이상의 USB 인터페이스가 있습니다. Windows 10 IoT에서 USB OTG를 올바르게 지원 하려면 몇 가지 작업을 수행 해야 합니다.  

## <a name="components-oems-have-to-supply"></a>Oem에서 제공 해야 하는 구성 요소

Oem은 usb 장치 측 및 USB 호스트 쪽의 구성 요소를 모두 제공 해야 합니다.  

![OEM이 제공 하는 구성 요소](../media/USB-Support/OEM-Components.png)

### <a name="oems-support-for-both-sides"></a>양쪽 모두에 대 한 Oem 지원

모든 USB 장치에는이를 식별 하는 고유한 VID 및 PID가 있습니다. Windows IoT 기반 USB 장치의 제조업체 인 OEM은 이러한 기능을 제공 해야 합니다.  Oem은 USB 컨소시엄에 적용 하 고 회사 VID (아직 없는 경우)를 가져온 다음 해당 제품에 대해 고유 하 게 사용할 PID를 선택할 수 있습니다. C #의 Windows 10 IoT 기능이 PC에 연결 된 경우 해당 "VID_nnn" 및 "PID_NNN"를 사용 하 여 USB 장치 (My에 설정 된 대로 선택할 수 있는 모든 기능)의 역할을 합니다. 그런 다음 호스트 PC에서이 VID 및 PID 조합을 사용 하 여 로드할 적절 한 드라이버 (myUSB .sys)를 찾습니다. 

![USB 기능을 함께 제공 하는 방법](../media/USB-Support/OEM-supplies.png)

### <a name="supporting-from-the-device-side"></a>장치 쪽에서 지원

_AFN을 사용 하도록 설정 된 이미지 생성을 위해 FFU에 포함할 기능_
* IoT 이미지에는 필요한 패키지 (즉, ufx01000 및 usbfnclx)가 있어야 합니다. 둘 다 다음 패키지 `Microsoft-IoTUAP-USBFN-Class-Extension-Package.cab`와 함께 제공 됩니다. Oem은 FFU에 포함 된 모든 기능을 나열 하는 XML 파일에서 적절 한 "기능" 태그를 사용 해야 합니다. 예를 들어 BoardTestOEMInput 파일의 <Feature>IOT_USBFN_CLASS_EXTENSION</Feature> 섹션에는 다음과 같은 항목이 <Microsoft> 포함 됩니다. 

_USB 역할 전환 드라이버_
* USB OTG의 경우 Oem은 USB 역할 전환 드라이버와 드라이버 자체 (* myURS)에 대 한 올바른 ACPI 테이블 항목 (*myOTGacpi*)을 제공 해야 합니다.

_USB 기능 컨트롤러 드라이버_
* 이는 Oem에서 사용 하는 하드웨어에 따라 달라 집니다. Microsoft는 널리 사용 되는 두 개의 USB 인 Synopsys 및 ChipIdea에 대 한 USB 기능 컨트롤러 드라이버를 제공 합니다.
* OEM에서 다른 USB OTG 칩셋을 사용 하도록 선택 하는 경우 OEM은 고유한 USB 함수 컨트롤러 하드웨어 (*myfunctioncontroller. sys*)를 제공 해야 합니다.

_USB 함수 클래스 드라이버_
* 하나 이상의 USB 함수 클래스 드라이버를 제공 해야 합니다.
* 이 드라이버는 특정 USB 장치 기능을 구현 합니다. 호스트 쪽에 표시 되는 장치 및 수행할 작업을 결정 합니다.
예를 들어, 직렬 통신 장치 또는 대용량 저장 장치 또는 완전히 사용자 지정 유형 장치 (*myc*o n s. m s)로 표시 될 수 있습니다.

_USB 기능 장치 구성_
* IoT 플랫폼이 USB 장치 모드인 경우 하나 이상의 구성에서 작동할 수 있습니다. 사용 중인 각 구성을 추가 하 고 해당 속성을 지정 해야 합니다.

_공용 속성_
* IoT 플랫폼의 모든 USB 기능 구성에 대 한 공용 속성이 있습니다. 궁극적으로는 VID, PID, DeviceClass, DeviceProtocol, Manufacturerer string, 일련 번호 등과 같은 표준 USB 설명자 항목을 지정 하는 것이 OEM에 게 달려 있습니다.
* 이러한 공용 속성은 레지스트리의 다음 위치에 설정 됩니다. `HKLM\System\ControlSet001\Control\USBFN\default`

```
BcdDevice=0x1 
bDeviceClass=0x0 
bDeviceProtocol=0x0 
bDeviceSubClass= 0x0 
idProduct= 0xc0c0 
idVendor=0x045e 
iManufacturer=1 
iSerialNumber=3 
ManufacturerString=OEMname 
ProductString="Windows IOT" 
SerialNumberString=0x123 
```
> [!IMPORTANT]
> 위의 값은 데모용 으로만 사용 되며 모든 제품에서 사용할 수 없습니다. OEM은 위의 각 항목에서 이러한 자리 표시자 필드를 *실제 값* 으로 바꾸어야 합니다.

_구성 당 속성_

구성은 다음 키의 레지스트리에 저장 됩니다. `HKLM\SYSTEM\ControlSet001\Control\USBFN\Configurations`

기본적으로에는 다음과 같이 FFU에 포함 된 빈 기본 USB 함수 구성이 있습니다 `HKLM\SYSTEM\ControlSet001\Control\USBFN\Configurations\default`

이 빈 기본 구성으로 인해 IoT 플랫폼이 설치 된 호스트 쪽에 드라이버가 없는 Windows IoT 장치로 나타납니다.

![에 대 한 구성](../media/USB-Support/config-screenshot.png)

각 구성은 인터페이스 목록과 같은 특정 속성을 지정 해야 합니다. IoT 플랫폼은 usb 장치에서 USB 호스트로 노출 되는 USB 인터페이스에 의해 정의 되는 다양 한 구성을 사용 하 여 USB 장치로 작동할 수 있습니다.

`HKLM\System\CurrentControlSet\Control\USBFN\Configurations\Default`

```
bmAttributes=0xC0
bMaxPower=0xFA
InterfaceList =
InterfaceDescriptor =
InterfaceGUIDE =
```

현재 선택 된 구성은 USB 핫에 연결할 때 적용 되는 구성입니다. `HKLM\SYSTEM\ControlSet001\Control\USBFN`

_구성의 예_

1. 단일 구성
   1. 인터페이스를 하나 이상 포함 해야 합니다.
   2. 기본 구성 일 수 있음
   3. PC에 연결 된 경우 IoT 플랫폼은 해당 유형의 USB 장치 (예: 모뎀 또는 저장소)로 표시 됩니다.
   4. `HKLM\SYSTEM\ControlSet001\Control\USBFN\Configurations\default`, `InterfaceList = "MODEM\0MTP"`

2. 복합 구성
   1. 추가 매개 변수가 있는 인터페이스의 목록을 포함 합니다.
   2. PC에 연결 된 경우 IoT 플랫폼은 여러 장치 (예: MTP 장치, 직렬 장치, 사용자 지정 장치)가 포함 된 복합 USB 장치로 표시 됩니다.
   3. `HKLM\SYSTEM\ControlSet001\Control\USBFN\Configurations\mycfg`, `InterfaceList = "MODEM\0MTP"`

다음 키 아래에 있는 레지스트리에서 `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\USBFN\Interfaces`:

각 USB 인터페이스 항목에는 인터페이스 설명자 값과 인터페이스 GUID가 포함 되어야 합니다.

### <a name="supporting-from-the-host-side"></a>호스트 측에서 지원

OEM에서 표준 USB 인터페이스를 구현 하도록 선택 하는 경우 (예:  대용량 저장소)를 사용 하는 경우 호스트 PC는 해당 유형의 USB 장치에 대해 기본 Windows 드라이버를 사용할 수 있습니다. OEM이 장치 쪽에서 사용자 지정 USB 인터페이스를 구현 하는 경우 OEM에서 해당 사용자 지정 USB 기능 장치용 Windows 호스트 드라이버를 개발 하는 데 필요 합니다. 
