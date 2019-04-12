---
title: USB 지원 및 Windows 10 IoT Core 대 한 이중 역할에 대 한 개요
author: saraclay
ms.author: saclayt
ms.date: 10/11/2017
ms.topic: article
description: USB 지원 및 이중 역할 이란 Windows 10 IoT Core 장치에 대 한이 사용자 지정 하는 방법을 알아봅니다.
keywords: windows iot, USB 지원, 이중 역할, USB
ms.openlocfilehash: be1ba523975a0a39414537242ca3b14b680d9799
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512854"
---
# <a name="overview-of-usb-support-and-dual-role"></a><span data-ttu-id="c4d1b-104">USB 지원 및 이중 역할 개요</span><span class="sxs-lookup"><span data-stu-id="c4d1b-104">Overview of USB Support and Dual Role</span></span>

<span data-ttu-id="c4d1b-105">키보드, 마우스, 조이스틱, 프린터, 스캐너, 저장 장치, 모뎀 및 비디오와 같은 주변 장치에 대 한 표준, 저렴 한 비용 연결을 보장 하는 확장 가능한 핫 플러그형 플러그 앤 플레이 직렬 인터페이스를 제공 하는 범용 직렬 버스 (USB) 회의 카메라입니다.</span><span class="sxs-lookup"><span data-stu-id="c4d1b-105">A Universal Serial Bus (USB) provides an expandable, hot-pluggable Plug and Play serial interface that ensures a standard, low-cost connection for peripheral devices such as keyboards, mice, joysticks, printers, scanners, storage devices, modems, and video conferencing cameras.</span></span>  
<span data-ttu-id="c4d1b-106">USB 장치에 대 한 이야기를 열거 하 고 플러그 앤 플레이 관리자가 로드 되는 드라이버 그룹에 USB 함수 스택에 나타내며 복합 USB 장치에 대 한 단일 구성을 여러 인터페이스를 지원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4d1b-106">When we talk about USB devices, the USB function stack refers to a group of drivers that are enumerated and loaded by the Plug and Play Manager, and a composite USB device can support multiple interfaces in a single configuration.</span></span> <span data-ttu-id="c4d1b-107">항목에 대 한 이야기이 대부분 USB 2.0에 대 한 이중 역할에 관련 된 문서 USB 이동 하거나 USB OTG OTG로 더 많이 알려진, 이기도 USB 3.0 및 USB 2.0의 차이점에 대해 알아야 하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c4d1b-107">While most of what we talk about in this article relates to the dual role for USB 2.0, more commonly known as USB On-The-Go or USB OTG or OTG, it is also helpful to know about USB 3.0 and how it differs from USB 2.0.</span></span> <span data-ttu-id="c4d1b-108">USB OTG 장치에 대 한 두 가지 역할을 정의합니다. OTG는 장치 및 장치 OTG B, 링크 및 호스트를 처음에 power를 제공 어느 쪽을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4d1b-108">The USB OTG defines two roles for devices: OTG A-device and OTG B-device, specifying which side supplies power to the link and which is the host initially.</span></span> <span data-ttu-id="c4d1b-109">모든 OTG 컨트롤러 역할을 모두를 지원 하므로 자주 라고 "합니다. 컨트롤러 OTG" 보다는 "이중-Role" 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="c4d1b-109">Since every OTG controller supports both roles, they are often called "Dual-Role" controllers rather than "OTG controllers."</span></span> <span data-ttu-id="c4d1b-110">반면에 USB 3.0 호스트 또는 주변 장치에 장치를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4d1b-110">USB 3.0, on the other hand, can make devices into either hosts or peripherals.</span></span> <span data-ttu-id="c4d1b-111">일부 장치는 다른 쪽 끝에서 검색 되 면 종류에 따라 두 역할 중 하나를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4d1b-111">Some devices can take either role depending on what kind is detected on the other end.</span></span> <span data-ttu-id="c4d1b-112">이러한 유형의 포트 이중-역할-데이터 (DRD) 라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4d1b-112">These types of ports are called Dual-Role-Data (DRD).</span></span> <span data-ttu-id="c4d1b-113">이러한 두 개의 장치에 연결 하는 역할이 임의로 할당 되지만 한쪽 끝에서 교체를 지시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4d1b-113">When two such devices are connected, the roles are randomly assigned but a swap can be commanded from either end.</span></span> 

## <a name="architecture-of-usb-function-in-windows-10-iot-core"></a><span data-ttu-id="c4d1b-114">Windows 10 IoT Core USB 함수 아키텍처</span><span class="sxs-lookup"><span data-stu-id="c4d1b-114">Architecture of USB Function in Windows 10 IoT Core</span></span>

<span data-ttu-id="c4d1b-115">USB 장치로 작동 하는 Windows 10 IoT 플랫폼, 경우 여러 구성 중 하나를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4d1b-115">When the Windows 10 IoT platform acts as USB device, it will use one of several configurations.</span></span> <span data-ttu-id="c4d1b-116">각 구성에는 하나 이상의 USB 인터페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="c4d1b-116">Each configuration has one or more USB interfaces.</span></span> <span data-ttu-id="c4d1b-117">USB OTG Windows 10 iot을 올바르게 지원 하려면 몇 가지 처리 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4d1b-117">To properly support USB OTG on Windows 10 IoT, several things need to be taken care of.</span></span>  

## <a name="components-oems-have-to-supply"></a><span data-ttu-id="c4d1b-118">구성 요소 Oem 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4d1b-118">Components OEMs have to supply</span></span>

<span data-ttu-id="c4d1b-119">Oem 양쪽-USB 장치 쪽에 대 한 및 USB 호스트 쪽에 대 한 구성 요소를 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4d1b-119">OEMs need to supply components on both sides – for the USB device-side and possibly for the USB host-side.</span></span>  

![구성 요소 OEM 제공](../media/USB-Support/OEM-Components.png)

### <a name="oems-support-for-both-sides"></a><span data-ttu-id="c4d1b-121">Oem 양쪽 모두에 대 한 지원</span><span class="sxs-lookup"><span data-stu-id="c4d1b-121">OEMs support for both sides</span></span>

<span data-ttu-id="c4d1b-122">모든 USB 장치에 고유한 VID 및 PID를 식별 하는 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4d1b-122">Every USB device has unique VID and PID, which identify it.</span></span> <span data-ttu-id="c4d1b-123">OEM은 Windows IoT 기반 USB 장치의 제조업체를 제공 해야 해당 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4d1b-123">An OEM, as the manufacturer of a Windows IoT-based USB device, needs to supply those.</span></span>  <span data-ttu-id="c4d1b-124">Oem에서 USB 컨소시엄에 적용 하 고 (없는 경우 하나 이미) 회사 VID를 얻을 수를 해당 제품에 대 한 고유 PID를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4d1b-124">OEMs can apply to the USB Consortium and obtain their company VID (if they don't have one already) and then choose a PID that will be unique for that product.</span></span> <span data-ttu-id="c4d1b-125">USBFN 기능을 사용 하 여 Windows 10 IoT를 PC에 연결 된 경우 USB 장치를 선택 하는 모든 기능 myUSBFN.sys에서 설정), (of 처럼 "PID_NNN"와 "VID_nnn"를 사용 하 여 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4d1b-125">When Windows 10 IoT with USBFN functionality is connected to a PC it will act as USB device (of whatever functionality to choose as set in myUSBFN.sys), with those "VID_nnn" and "PID_NNN".</span></span> <span data-ttu-id="c4d1b-126">이 VID 및 PID 조합은 다음 (myUSB.sys)를 로드 하려면 적절 한 드라이버를 찾는 호스트 PC에서 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c4d1b-126">This VID and PID combination is then used by the host PC to find the appropriate drivers to load (myUSB.sys).</span></span> 

![USB 함수 함께 일 하는 방법](../media/USB-Support/OEM-supplies.png)

### <a name="supporting-from-the-device-side"></a><span data-ttu-id="c4d1b-128">장치 쪽에서 지원</span><span class="sxs-lookup"><span data-stu-id="c4d1b-128">Supporting from the device side</span></span>

_<span data-ttu-id="c4d1b-129">USBFN 활성화를 사용 하 여 이미지를 생성 하기 위해 FFU에 포함할 기능을</span><span class="sxs-lookup"><span data-stu-id="c4d1b-129">Features to include in FFU for image generation with USBFN enabled</span></span>_
* <span data-ttu-id="c4d1b-130">IoT 이미지 것, 즉 ufx01000.sys 및 usbfnclx.sys에서 필요한 패키지를 가져야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4d1b-130">The IoT image must have the necessary packages in it, namely ufx01000.sys and usbfnclx.sys.</span></span> <span data-ttu-id="c4d1b-131">다음 패키지를 사용 하 여 제공 둘 `Microsoft-IoTUAP-USBFN-Class-Extension-Package.cab`합니다.</span><span class="sxs-lookup"><span data-stu-id="c4d1b-131">They both come with the following package `Microsoft-IoTUAP-USBFN-Class-Extension-Package.cab`.</span></span> <span data-ttu-id="c4d1b-132">Oem은 FFU에 포함 된 모든 기능을 나열 하는 해당 XML 파일에서 적절 한 "기능" 태그를 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4d1b-132">OEMs must use a proper "feature" tag in their XML file, which lists all features included in the FFU.</span></span> <span data-ttu-id="c4d1b-133">예를 들어 BoardTestOEMInput.xml 파일 됩니다 건너뛰었는지 <Feature>IOT_USBFN_CLASS_EXTENSION</Feature> 아래에 포함 <Microsoft> 기능 섹션입니다.</span><span class="sxs-lookup"><span data-stu-id="c4d1b-133">For example, in the BoardTestOEMInput.xml file there will be the following entry <Feature>IOT_USBFN_CLASS_EXTENSION</Feature>  included under <Microsoft> features section.</span></span> 

_<span data-ttu-id="c4d1b-134">역할 전환 하는 USB 드라이버</span><span class="sxs-lookup"><span data-stu-id="c4d1b-134">USB Role Switching driver</span></span>_
* <span data-ttu-id="c4d1b-135">올바른 ACPI 테이블 항목을 제공 해야 할 Oem USB otg (*myOTGacpi*) USB 역할 전환 드라이버 및 드라이버 자체에 대 한 (\* myURS.sys).</span><span class="sxs-lookup"><span data-stu-id="c4d1b-135">For the USB OTG, OEMs have to supply the correct ACPI table entry (*myOTGacpi*) for the USB role-switching driver and the driver itself (\*myURS.sys).</span></span>

_<span data-ttu-id="c4d1b-136">USB 함수 컨트롤러 드라이버</span><span class="sxs-lookup"><span data-stu-id="c4d1b-136">USB Function Controller Driver</span></span>_
* <span data-ttu-id="c4d1b-137">Oem에서 사용 하는 하드웨어에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="c4d1b-137">This depends on the hardware used by OEMs.</span></span> <span data-ttu-id="c4d1b-138">Microsoft는 두 가지 인기 있는 USB OTG 칩셋-Synopsys 및 ChipIdea USB 함수 컨트롤러 드라이버를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c4d1b-138">Microsoft supplies USB Function Controller drivers for two popular USB OTG chipsets - Synopsys and ChipIdea.</span></span>
* <span data-ttu-id="c4d1b-139">OEM 다른 USB OTG 칩셋, 사용을 선택한 경우 OEM 자신의 USB 함수 컨트롤러 하드웨어를 제공 해야 합니다 (*myfunctioncontroller.sys*).</span><span class="sxs-lookup"><span data-stu-id="c4d1b-139">If an OEM chooses to use another USB OTG chipset, then the OEM must supply their own USB function controller hardware (*myfunctioncontroller.sys*).</span></span>

_<span data-ttu-id="c4d1b-140">USB 함수 클래스 드라이버</span><span class="sxs-lookup"><span data-stu-id="c4d1b-140">USB Function Class drivers</span></span>_
* <span data-ttu-id="c4d1b-141">하나 이상의 USB 함수 클래스 드라이버를 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4d1b-141">At least one USB function class driver must be supplied.</span></span>
* <span data-ttu-id="c4d1b-142">이 드라이버는 특정 USB 장치 기능을 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="c4d1b-142">This driver implements specific USB device functionality.</span></span> <span data-ttu-id="c4d1b-143">나타납니다 장치 결정 호스트 쪽도 it로를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4d1b-143">It determines what the device will appear as on the host side as well as what it will do.</span></span>
<span data-ttu-id="c4d1b-144">직렬 통신 장치 또는 대용량 저장 장치 또는 장치를 완전히 사용자 지정 형식으로 나타날 수 있습니다는 예를 들어, (*myUSBFN.sys*).</span><span class="sxs-lookup"><span data-stu-id="c4d1b-144">For example, it may appear as a serial communications device or as a mass storage device or a completely custom type device (*myUSBFN.sys*).</span></span>

_<span data-ttu-id="c4d1b-145">USB 함수 장치 구성</span><span class="sxs-lookup"><span data-stu-id="c4d1b-145">Configuring USB Function Device</span></span>_
* <span data-ttu-id="c4d1b-146">IoT 플랫폼 USB 장치 모드일 때에 하나 이상의 구성에서 작동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4d1b-146">When the IoT platform is in USB device mode, it can operate under one or more configurations.</span></span> <span data-ttu-id="c4d1b-147">사용 하 여 각 구성을 추가 하 고 해당 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4d1b-147">Each configuration in use must be added and have its properties specified.</span></span>

_<span data-ttu-id="c4d1b-148">공용 속성</span><span class="sxs-lookup"><span data-stu-id="c4d1b-148">Common Properties</span></span>_
* <span data-ttu-id="c4d1b-149">개의 IoT 플랫폼의 모든 USB 함수 구성에 대 한 공통 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4d1b-149">There are common properties for all USB function configurations of the IoT platform.</span></span> <span data-ttu-id="c4d1b-150">궁극적으로 VID, PID, DeviceClass DeviceProtocol, 등 표준 USB 설명자 항목을 지정 하는 OEM 최대 Manufacturerer 문자열, 일련 번호, 등입니다.</span><span class="sxs-lookup"><span data-stu-id="c4d1b-150">It is ultimately up to the OEM to specify standard USB descriptor entries such as VID, PID, DeviceClass, DeviceProtocol, Manufacturerer string, serial number, etc.</span></span>
* <span data-ttu-id="c4d1b-151">이러한 공용 속성은 다음 위치에서 레지스트리에 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c4d1b-151">These common properties are set in registry in the following location:</span></span> `HKLM\System\ControlSet001\Control\USBFN\default`

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
> <span data-ttu-id="c4d1b-152">위의 값 데모용 으로만 제공 되며 모든 제품에 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c4d1b-152">The values above are for demonstration purposes only and cannot be used in any product.</span></span> <span data-ttu-id="c4d1b-153">OEM에 이러한 자리 표시자 필드를 바꾸어야 *실제 값* 위의 각 항목의 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4d1b-153">The OEM must replace these placeholder fields with *actual values* in each entry above.</span></span>

_<span data-ttu-id="c4d1b-154">구성 속성 당</span><span class="sxs-lookup"><span data-stu-id="c4d1b-154">Per configuration properties</span></span>_

<span data-ttu-id="c4d1b-155">구성이는 레지스트리에 다음 키 아래에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c4d1b-155">Configurations are stored in a registry under the following key:</span></span> `HKLM\SYSTEM\ControlSet001\Control\USBFN\Configurations`

<span data-ttu-id="c4d1b-156">기본적으로 구성이 비어 있는 기본 USB 함수에 설정 된 대로 FFU에 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4d1b-156">By default, there is an empty default USB function configuration included in the FFU, as set in:</span></span> `HKLM\SYSTEM\ControlSet001\Control\USBFN\Configurations\default`

<span data-ttu-id="c4d1b-157">거기에 Windows IoT 장치는 IoT 플랫폼에서 비어 있는 기본 구성 결과이 설치 된 호스트 쪽에 드라이버가 없는 경우</span><span class="sxs-lookup"><span data-stu-id="c4d1b-157">This empty default configuration results in the IoT platform appearing as a Windows IoT device for which there is no driver on the host side installed.</span></span>

![USBFN에 대 한 구성](../media/USB-Support/config-screenshot.png)

<span data-ttu-id="c4d1b-159">각 구성에는 인터페이스 목록 등의 특정 속성을 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4d1b-159">Each configuration must specify certain properties, such as the Interface List.</span></span> <span data-ttu-id="c4d1b-160">IoT 플랫폼 hare USB 호스트에 USB 장치에서 노출 되는 USB 인터페이스에서 정의 하는 다른 구성 사용 하 여 USB 장치로 작동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4d1b-160">The IoT platform can operate as a USB device with different configurations, whic hare defined by USB interfaces that are exposed from USB device to USB host.</span></span>

`HKLM\System\CurrentControlSet\Control\USBFN\Configurations\Default`

```
bmAttributes=0xC0
bMaxPower=0xFA
InterfaceList =
InterfaceDescriptor =
InterfaceGUIDE =
```

<span data-ttu-id="c4d1b-161">현재 선택한 구성을 핫 USB에 연결할 때 적용 되는 것은:</span><span class="sxs-lookup"><span data-stu-id="c4d1b-161">Currently, the selected configuration is the one that will be in effect when connecting to the USB hot:</span></span> `HKLM\SYSTEM\ControlSet001\Control\USBFN`

_<span data-ttu-id="c4d1b-162">구성의 예</span><span class="sxs-lookup"><span data-stu-id="c4d1b-162">Examples of configurations</span></span>_

1. <span data-ttu-id="c4d1b-163">단일 구성</span><span class="sxs-lookup"><span data-stu-id="c4d1b-163">Single configuration</span></span>
   1. <span data-ttu-id="c4d1b-164">인터페이스가 하나 이상 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4d1b-164">Must contain at least one interface</span></span>
   2. <span data-ttu-id="c4d1b-165">기본 구성 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4d1b-165">Can be a default configuration</span></span>
   3. <span data-ttu-id="c4d1b-166">PC에 연결 되 면 IoT 플랫폼 USB 장치 (예:: 모뎀 또는 저장소)의 해당 형식으로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c4d1b-166">When connected to a PC, the IoT platform will appear as that type of USB device (e.g. modem or storage).</span></span>
   4. `HKLM\SYSTEM\ControlSet001\Control\USBFN\Configurations\default`<span data-ttu-id="c4d1b-167">,</span><span class="sxs-lookup"><span data-stu-id="c4d1b-167">,</span></span> `InterfaceList = "MODEM\0MTP"`

2. <span data-ttu-id="c4d1b-168">복합 구성</span><span class="sxs-lookup"><span data-stu-id="c4d1b-168">Composite configuration</span></span>
   1. <span data-ttu-id="c4d1b-169">추가 매개 변수를 사용 하 여 인터페이스의 목록을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="c4d1b-169">Contains a list of interfaces with additional parameters</span></span>
   2. <span data-ttu-id="c4d1b-170">PC에 연결 되 면 IoT 플랫폼 (예:: MTP 장치, 직렬 장치, 사용자 지정 장치)에 여러 장치를 사용 하 여 복합 USB 장치로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c4d1b-170">When connected to a PC, the IoT platform will appear as a composite USB device with multiple units in it (i.e. MTP device, serial device, custom device).</span></span>
   3. `HKLM\SYSTEM\ControlSet001\Control\USBFN\Configurations\mycfg`<span data-ttu-id="c4d1b-171">,</span><span class="sxs-lookup"><span data-stu-id="c4d1b-171">,</span></span> `InterfaceList = "MODEM\0MTP"`

<span data-ttu-id="c4d1b-172">USBFN 인터페이스 레지스트리에서 다음 키 아래에 열거 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c4d1b-172">USBFN Interfaces are enumerated in registry under the following key:</span></span>
`HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\USBFN\Interfaces`

<span data-ttu-id="c4d1b-173">USB 인터페이스 항목별로 인터페이스 설명자 값을 GUID 인터페이스를 포함 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4d1b-173">Each USB interface entry must contain an interface descriptor value and an interface GUID.</span></span>

### <a name="supporting-from-the-host-side"></a><span data-ttu-id="c4d1b-174">호스트 측에서 지원</span><span class="sxs-lookup"><span data-stu-id="c4d1b-174">Supporting from the host side</span></span>

<span data-ttu-id="c4d1b-175">OEM (예: 표준 USB 인터페이스를 구현 하 고 싶다면  저장소 질량) 장치 쪽에서는 다음 호스트 PC에 사용할 수 상자에서 Windows 드라이버 USB 장치 유형에 해당 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4d1b-175">If an OEM chooses to implement any standard USB interface (e.g.  mass storage) on the device side, then a host PC can use in-box Windows drivers for that type of USB device.</span></span> <span data-ttu-id="c4d1b-176">장치 쪽에서 모든 사용자 지정 USB 인터페이스를 구현 하는 OEM, 있으면 해당 사용자 지정 함수 USB 장치용 Windows 호스트 드라이버 개발에 OEM에 대 한 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4d1b-176">If an OEM implements any custom USB interface on device side, then it is necessary for the OEM to develop a Windows host driver for that custom USB Function device.</span></span> 
