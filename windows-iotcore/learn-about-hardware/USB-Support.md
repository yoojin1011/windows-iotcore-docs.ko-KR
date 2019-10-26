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
# <a name="overview-of-usb-support-and-dual-role"></a><span data-ttu-id="197f8-104">USB 지원 및 이중 역할 개요</span><span class="sxs-lookup"><span data-stu-id="197f8-104">Overview of USB Support and Dual Role</span></span>

<span data-ttu-id="197f8-105">USB (범용 직렬 버스)는 키보드, 마우스, 조이스틱, 프린터, 스캐너, 저장 장치, 모뎀 및 비디오와 같은 주변 장치에 대 한 표준 저렴 한 연결을 보장 하는 확장 가능한 핫 플러그형 플러그 앤 플레이 직렬 인터페이스를 제공 합니다. 회의 카메라.</span><span class="sxs-lookup"><span data-stu-id="197f8-105">A Universal Serial Bus (USB) provides an expandable, hot-pluggable Plug and Play serial interface that ensures a standard, low-cost connection for peripheral devices such as keyboards, mice, joysticks, printers, scanners, storage devices, modems, and video conferencing cameras.</span></span>  
<span data-ttu-id="197f8-106">USB 장치에 대해 설명할 때 USB 함수 스택은 플러그 앤 플레이 Manager에서 열거 하 고 로드 하는 드라이버 그룹을 나타내며, 복합 USB 장치는 단일 구성에서 여러 인터페이스를 지원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="197f8-106">When we talk about USB devices, the USB function stack refers to a group of drivers that are enumerated and loaded by the Plug and Play Manager, and a composite USB device can support multiple interfaces in a single configuration.</span></span> <span data-ttu-id="197f8-107">이 문서에서 설명 하는 대부분의 기능은 usb 2.0에 대 한 이중 역할, 일반적으로 usb (usb) 또는 USB (usb)와 관련 된 것으로, usb 3.0 및 usb 2.0와 어떻게 다른 지에 대해 알고 있는 것도 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="197f8-107">While most of what we talk about in this article relates to the dual role for USB 2.0, more commonly known as USB On-The-Go or USB OTG or OTG, it is also helpful to know about USB 3.0 and how it differs from USB 2.0.</span></span> <span data-ttu-id="197f8-108">USB OTG는 장치에 대 한 두 가지 역할을 정의 합니다. 즉, OTG는 장치 및 OTG B-장치 이며,이를 통해 연결에 전원을 공급 하는 측면과 초기에 호스트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="197f8-108">The USB OTG defines two roles for devices: OTG A-device and OTG B-device, specifying which side supplies power to the link and which is the host initially.</span></span> <span data-ttu-id="197f8-109">모든 OTG 컨트롤러는 두 역할을 모두 지원 하므로 "OTG 컨트롤러"가 아닌 "이중 역할" 컨트롤러 라고도 합니다.</span><span class="sxs-lookup"><span data-stu-id="197f8-109">Since every OTG controller supports both roles, they are often called "Dual-Role" controllers rather than "OTG controllers."</span></span> <span data-ttu-id="197f8-110">반면에 USB 3.0는 호스트 또는 주변 장치로 장치를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="197f8-110">USB 3.0, on the other hand, can make devices into either hosts or peripherals.</span></span> <span data-ttu-id="197f8-111">일부 장치는 다른 쪽에서 검색 된 종류에 따라 두 역할을 모두 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="197f8-111">Some devices can take either role depending on what kind is detected on the other end.</span></span> <span data-ttu-id="197f8-112">이러한 유형의 포트를 DRD (이중 역할 데이터) 라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="197f8-112">These types of ports are called Dual-Role-Data (DRD).</span></span> <span data-ttu-id="197f8-113">이러한 두 장치가 연결 되 면 역할은 임의로 할당 되지만 한 쪽에서 교환이 가능 합니다.</span><span class="sxs-lookup"><span data-stu-id="197f8-113">When two such devices are connected, the roles are randomly assigned but a swap can be commanded from either end.</span></span> 

## <a name="architecture-of-usb-function-in-windows-10-iot-core"></a><span data-ttu-id="197f8-114">Windows 10 IoT Core의 USB 기능 아키텍처</span><span class="sxs-lookup"><span data-stu-id="197f8-114">Architecture of USB Function in Windows 10 IoT Core</span></span>

<span data-ttu-id="197f8-115">Windows 10 IoT 플랫폼은 USB 장치 역할을 하는 경우 여러 구성 중 하나를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="197f8-115">When the Windows 10 IoT platform acts as USB device, it will use one of several configurations.</span></span> <span data-ttu-id="197f8-116">각 구성에는 하나 이상의 USB 인터페이스가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="197f8-116">Each configuration has one or more USB interfaces.</span></span> <span data-ttu-id="197f8-117">Windows 10 IoT에서 USB OTG를 올바르게 지원 하려면 몇 가지 작업을 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="197f8-117">To properly support USB OTG on Windows 10 IoT, several things need to be taken care of.</span></span>  

## <a name="components-oems-have-to-supply"></a><span data-ttu-id="197f8-118">Oem에서 제공 해야 하는 구성 요소</span><span class="sxs-lookup"><span data-stu-id="197f8-118">Components OEMs have to supply</span></span>

<span data-ttu-id="197f8-119">Oem은 usb 장치 측 및 USB 호스트 쪽의 구성 요소를 모두 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="197f8-119">OEMs need to supply components on both sides – for the USB device-side and possibly for the USB host-side.</span></span>  

![OEM이 제공 하는 구성 요소](../media/USB-Support/OEM-Components.png)

### <a name="oems-support-for-both-sides"></a><span data-ttu-id="197f8-121">양쪽 모두에 대 한 Oem 지원</span><span class="sxs-lookup"><span data-stu-id="197f8-121">OEMs support for both sides</span></span>

<span data-ttu-id="197f8-122">모든 USB 장치에는이를 식별 하는 고유한 VID 및 PID가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="197f8-122">Every USB device has unique VID and PID, which identify it.</span></span> <span data-ttu-id="197f8-123">Windows IoT 기반 USB 장치의 제조업체 인 OEM은 이러한 기능을 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="197f8-123">An OEM, as the manufacturer of a Windows IoT-based USB device, needs to supply those.</span></span>  <span data-ttu-id="197f8-124">Oem은 USB 컨소시엄에 적용 하 고 회사 VID (아직 없는 경우)를 가져온 다음 해당 제품에 대해 고유 하 게 사용할 PID를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="197f8-124">OEMs can apply to the USB Consortium and obtain their company VID (if they don't have one already) and then choose a PID that will be unique for that product.</span></span> <span data-ttu-id="197f8-125">C #의 Windows 10 IoT 기능이 PC에 연결 된 경우 해당 "VID_nnn" 및 "PID_NNN"를 사용 하 여 USB 장치 (My에 설정 된 대로 선택할 수 있는 모든 기능)의 역할을 합니다.</span><span class="sxs-lookup"><span data-stu-id="197f8-125">When Windows 10 IoT with USBFN functionality is connected to a PC it will act as USB device (of whatever functionality to choose as set in myUSBFN.sys), with those "VID_nnn" and "PID_NNN".</span></span> <span data-ttu-id="197f8-126">그런 다음 호스트 PC에서이 VID 및 PID 조합을 사용 하 여 로드할 적절 한 드라이버 (myUSB .sys)를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="197f8-126">This VID and PID combination is then used by the host PC to find the appropriate drivers to load (myUSB.sys).</span></span> 

![USB 기능을 함께 제공 하는 방법](../media/USB-Support/OEM-supplies.png)

### <a name="supporting-from-the-device-side"></a><span data-ttu-id="197f8-128">장치 쪽에서 지원</span><span class="sxs-lookup"><span data-stu-id="197f8-128">Supporting from the device side</span></span>

<span data-ttu-id="197f8-129">_AFN을 사용 하도록 설정 된 이미지 생성을 위해 FFU에 포함할 기능_</span><span class="sxs-lookup"><span data-stu-id="197f8-129">_Features to include in FFU for image generation with USBFN enabled_</span></span>
* <span data-ttu-id="197f8-130">IoT 이미지에는 필요한 패키지 (즉, ufx01000 및 usbfnclx)가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="197f8-130">The IoT image must have the necessary packages in it, namely ufx01000.sys and usbfnclx.sys.</span></span> <span data-ttu-id="197f8-131">둘 다 다음 패키지 `Microsoft-IoTUAP-USBFN-Class-Extension-Package.cab`와 함께 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="197f8-131">They both come with the following package `Microsoft-IoTUAP-USBFN-Class-Extension-Package.cab`.</span></span> <span data-ttu-id="197f8-132">Oem은 FFU에 포함 된 모든 기능을 나열 하는 XML 파일에서 적절 한 "기능" 태그를 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="197f8-132">OEMs must use a proper "feature" tag in their XML file, which lists all features included in the FFU.</span></span> <span data-ttu-id="197f8-133">예를 들어 BoardTestOEMInput 파일의 <Feature>IOT_USBFN_CLASS_EXTENSION</Feature> 섹션에는 다음과 같은 항목이 <Microsoft> 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="197f8-133">For example, in the BoardTestOEMInput.xml file there will be the following entry <Feature>IOT_USBFN_CLASS_EXTENSION</Feature>  included under <Microsoft> features section.</span></span> 

<span data-ttu-id="197f8-134">_USB 역할 전환 드라이버_</span><span class="sxs-lookup"><span data-stu-id="197f8-134">_USB Role Switching driver_</span></span>
* <span data-ttu-id="197f8-135">USB OTG의 경우 Oem은 USB 역할 전환 드라이버와 드라이버 자체 (\* myURS)에 대 한 올바른 ACPI 테이블 항목 (*myOTGacpi*)을 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="197f8-135">For the USB OTG, OEMs have to supply the correct ACPI table entry (*myOTGacpi*) for the USB role-switching driver and the driver itself (\*myURS.sys).</span></span>

<span data-ttu-id="197f8-136">_USB 기능 컨트롤러 드라이버_</span><span class="sxs-lookup"><span data-stu-id="197f8-136">_USB Function Controller Driver_</span></span>
* <span data-ttu-id="197f8-137">이는 Oem에서 사용 하는 하드웨어에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="197f8-137">This depends on the hardware used by OEMs.</span></span> <span data-ttu-id="197f8-138">Microsoft는 널리 사용 되는 두 개의 USB 인 Synopsys 및 ChipIdea에 대 한 USB 기능 컨트롤러 드라이버를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="197f8-138">Microsoft supplies USB Function Controller drivers for two popular USB OTG chipsets - Synopsys and ChipIdea.</span></span>
* <span data-ttu-id="197f8-139">OEM에서 다른 USB OTG 칩셋을 사용 하도록 선택 하는 경우 OEM은 고유한 USB 함수 컨트롤러 하드웨어 (*myfunctioncontroller. sys*)를 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="197f8-139">If an OEM chooses to use another USB OTG chipset, then the OEM must supply their own USB function controller hardware (*myfunctioncontroller.sys*).</span></span>

<span data-ttu-id="197f8-140">_USB 함수 클래스 드라이버_</span><span class="sxs-lookup"><span data-stu-id="197f8-140">_USB Function Class drivers_</span></span>
* <span data-ttu-id="197f8-141">하나 이상의 USB 함수 클래스 드라이버를 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="197f8-141">At least one USB function class driver must be supplied.</span></span>
* <span data-ttu-id="197f8-142">이 드라이버는 특정 USB 장치 기능을 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="197f8-142">This driver implements specific USB device functionality.</span></span> <span data-ttu-id="197f8-143">호스트 쪽에 표시 되는 장치 및 수행할 작업을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="197f8-143">It determines what the device will appear as on the host side as well as what it will do.</span></span>
<span data-ttu-id="197f8-144">예를 들어, 직렬 통신 장치 또는 대용량 저장 장치 또는 완전히 사용자 지정 유형 장치 (*myc*o n s. m s)로 표시 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="197f8-144">For example, it may appear as a serial communications device or as a mass storage device or a completely custom type device (*myUSBFN.sys*).</span></span>

<span data-ttu-id="197f8-145">_USB 기능 장치 구성_</span><span class="sxs-lookup"><span data-stu-id="197f8-145">_Configuring USB Function Device_</span></span>
* <span data-ttu-id="197f8-146">IoT 플랫폼이 USB 장치 모드인 경우 하나 이상의 구성에서 작동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="197f8-146">When the IoT platform is in USB device mode, it can operate under one or more configurations.</span></span> <span data-ttu-id="197f8-147">사용 중인 각 구성을 추가 하 고 해당 속성을 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="197f8-147">Each configuration in use must be added and have its properties specified.</span></span>

<span data-ttu-id="197f8-148">_공용 속성_</span><span class="sxs-lookup"><span data-stu-id="197f8-148">_Common Properties_</span></span>
* <span data-ttu-id="197f8-149">IoT 플랫폼의 모든 USB 기능 구성에 대 한 공용 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="197f8-149">There are common properties for all USB function configurations of the IoT platform.</span></span> <span data-ttu-id="197f8-150">궁극적으로는 VID, PID, DeviceClass, DeviceProtocol, Manufacturerer string, 일련 번호 등과 같은 표준 USB 설명자 항목을 지정 하는 것이 OEM에 게 달려 있습니다.</span><span class="sxs-lookup"><span data-stu-id="197f8-150">It is ultimately up to the OEM to specify standard USB descriptor entries such as VID, PID, DeviceClass, DeviceProtocol, Manufacturerer string, serial number, etc.</span></span>
* <span data-ttu-id="197f8-151">이러한 공용 속성은 레지스트리의 다음 위치에 설정 됩니다. `HKLM\System\ControlSet001\Control\USBFN\default`</span><span class="sxs-lookup"><span data-stu-id="197f8-151">These common properties are set in registry in the following location: `HKLM\System\ControlSet001\Control\USBFN\default`</span></span>

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
> <span data-ttu-id="197f8-152">위의 값은 데모용 으로만 사용 되며 모든 제품에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="197f8-152">The values above are for demonstration purposes only and cannot be used in any product.</span></span> <span data-ttu-id="197f8-153">OEM은 위의 각 항목에서 이러한 자리 표시자 필드를 *실제 값* 으로 바꾸어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="197f8-153">The OEM must replace these placeholder fields with *actual values* in each entry above.</span></span>

<span data-ttu-id="197f8-154">_구성 당 속성_</span><span class="sxs-lookup"><span data-stu-id="197f8-154">_Per configuration properties_</span></span>

<span data-ttu-id="197f8-155">구성은 다음 키의 레지스트리에 저장 됩니다. `HKLM\SYSTEM\ControlSet001\Control\USBFN\Configurations`</span><span class="sxs-lookup"><span data-stu-id="197f8-155">Configurations are stored in a registry under the following key: `HKLM\SYSTEM\ControlSet001\Control\USBFN\Configurations`</span></span>

<span data-ttu-id="197f8-156">기본적으로에는 다음과 같이 FFU에 포함 된 빈 기본 USB 함수 구성이 있습니다 `HKLM\SYSTEM\ControlSet001\Control\USBFN\Configurations\default`</span><span class="sxs-lookup"><span data-stu-id="197f8-156">By default, there is an empty default USB function configuration included in the FFU, as set in: `HKLM\SYSTEM\ControlSet001\Control\USBFN\Configurations\default`</span></span>

<span data-ttu-id="197f8-157">이 빈 기본 구성으로 인해 IoT 플랫폼이 설치 된 호스트 쪽에 드라이버가 없는 Windows IoT 장치로 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="197f8-157">This empty default configuration results in the IoT platform appearing as a Windows IoT device for which there is no driver on the host side installed.</span></span>

![에 대 한 구성](../media/USB-Support/config-screenshot.png)

<span data-ttu-id="197f8-159">각 구성은 인터페이스 목록과 같은 특정 속성을 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="197f8-159">Each configuration must specify certain properties, such as the Interface List.</span></span> <span data-ttu-id="197f8-160">IoT 플랫폼은 usb 장치에서 USB 호스트로 노출 되는 USB 인터페이스에 의해 정의 되는 다양 한 구성을 사용 하 여 USB 장치로 작동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="197f8-160">The IoT platform can operate as a USB device with different configurations, whic hare defined by USB interfaces that are exposed from USB device to USB host.</span></span>

`HKLM\System\CurrentControlSet\Control\USBFN\Configurations\Default`

```
bmAttributes=0xC0
bMaxPower=0xFA
InterfaceList =
InterfaceDescriptor =
InterfaceGUIDE =
```

<span data-ttu-id="197f8-161">현재 선택 된 구성은 USB 핫에 연결할 때 적용 되는 구성입니다. `HKLM\SYSTEM\ControlSet001\Control\USBFN`</span><span class="sxs-lookup"><span data-stu-id="197f8-161">Currently, the selected configuration is the one that will be in effect when connecting to the USB hot: `HKLM\SYSTEM\ControlSet001\Control\USBFN`</span></span>

<span data-ttu-id="197f8-162">_구성의 예_</span><span class="sxs-lookup"><span data-stu-id="197f8-162">_Examples of configurations_</span></span>

1. <span data-ttu-id="197f8-163">단일 구성</span><span class="sxs-lookup"><span data-stu-id="197f8-163">Single configuration</span></span>
   1. <span data-ttu-id="197f8-164">인터페이스를 하나 이상 포함 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="197f8-164">Must contain at least one interface</span></span>
   2. <span data-ttu-id="197f8-165">기본 구성 일 수 있음</span><span class="sxs-lookup"><span data-stu-id="197f8-165">Can be a default configuration</span></span>
   3. <span data-ttu-id="197f8-166">PC에 연결 된 경우 IoT 플랫폼은 해당 유형의 USB 장치 (예: 모뎀 또는 저장소)로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="197f8-166">When connected to a PC, the IoT platform will appear as that type of USB device (e.g. modem or storage).</span></span>
   4. <span data-ttu-id="197f8-167">`HKLM\SYSTEM\ControlSet001\Control\USBFN\Configurations\default`, `InterfaceList = "MODEM\0MTP"`</span><span class="sxs-lookup"><span data-stu-id="197f8-167">`HKLM\SYSTEM\ControlSet001\Control\USBFN\Configurations\default`, `InterfaceList = "MODEM\0MTP"`</span></span>

2. <span data-ttu-id="197f8-168">복합 구성</span><span class="sxs-lookup"><span data-stu-id="197f8-168">Composite configuration</span></span>
   1. <span data-ttu-id="197f8-169">추가 매개 변수가 있는 인터페이스의 목록을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="197f8-169">Contains a list of interfaces with additional parameters</span></span>
   2. <span data-ttu-id="197f8-170">PC에 연결 된 경우 IoT 플랫폼은 여러 장치 (예: MTP 장치, 직렬 장치, 사용자 지정 장치)가 포함 된 복합 USB 장치로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="197f8-170">When connected to a PC, the IoT platform will appear as a composite USB device with multiple units in it (i.e. MTP device, serial device, custom device).</span></span>
   3. <span data-ttu-id="197f8-171">`HKLM\SYSTEM\ControlSet001\Control\USBFN\Configurations\mycfg`, `InterfaceList = "MODEM\0MTP"`</span><span class="sxs-lookup"><span data-stu-id="197f8-171">`HKLM\SYSTEM\ControlSet001\Control\USBFN\Configurations\mycfg`, `InterfaceList = "MODEM\0MTP"`</span></span>

<span data-ttu-id="197f8-172">다음 키 아래에 있는 레지스트리에서 `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\USBFN\Interfaces`:</span><span class="sxs-lookup"><span data-stu-id="197f8-172">USBFN Interfaces are enumerated in registry under the following key: `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\USBFN\Interfaces`</span></span>

<span data-ttu-id="197f8-173">각 USB 인터페이스 항목에는 인터페이스 설명자 값과 인터페이스 GUID가 포함 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="197f8-173">Each USB interface entry must contain an interface descriptor value and an interface GUID.</span></span>

### <a name="supporting-from-the-host-side"></a><span data-ttu-id="197f8-174">호스트 측에서 지원</span><span class="sxs-lookup"><span data-stu-id="197f8-174">Supporting from the host side</span></span>

<span data-ttu-id="197f8-175">OEM에서 표준 USB 인터페이스를 구현 하도록 선택 하는 경우 (예:  대용량 저장소)를 사용 하는 경우 호스트 PC는 해당 유형의 USB 장치에 대해 기본 Windows 드라이버를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="197f8-175">If an OEM chooses to implement any standard USB interface (e.g.  mass storage) on the device side, then a host PC can use in-box Windows drivers for that type of USB device.</span></span> <span data-ttu-id="197f8-176">OEM이 장치 쪽에서 사용자 지정 USB 인터페이스를 구현 하는 경우 OEM에서 해당 사용자 지정 USB 기능 장치용 Windows 호스트 드라이버를 개발 하는 데 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="197f8-176">If an OEM implements any custom USB interface on device side, then it is necessary for the OEM to develop a Windows host driver for that custom USB Function device.</span></span> 
