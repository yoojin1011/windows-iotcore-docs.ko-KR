---
title: Bluetooth 지원
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Windows 10 IoT Core 실행 하는 장치에 대 한 Bluetooth를 활용 하는 방법에 알아봅니다.
keywords: windows iot, bluetooth, bluetooth 지원, 장치, 장치 포털
ms.openlocfilehash: f24b50b65b192ed6bd9309eeda30dbadfedf5bc2
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513261"
---
# <a name="bluetooth-support"></a><span data-ttu-id="bf452-104">Bluetooth 지원</span><span class="sxs-lookup"><span data-stu-id="bf452-104">Bluetooth Support</span></span>
<span data-ttu-id="bf452-105">Windows 10 IoT Core Bluetooth 4.0을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf452-105">Windows 10 IoT Core supports Bluetooth 4.0.</span></span> <span data-ttu-id="bf452-106">지원 되는 Bluetooth 동글 목록에서 찾을 수 있습니다 합니다 [하드웨어 호환성 목록](../learn-about-hardware/HardwareCompatList.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="bf452-106">A list of supported Bluetooth dongles can be found in the [Hardware Compatibility List](../learn-about-hardware/HardwareCompatList.md).</span></span>

## <a name="about-bluetooth"></a><span data-ttu-id="bf452-107">Bluetooth에 대 한</span><span class="sxs-lookup"><span data-stu-id="bf452-107">About Bluetooth</span></span>
<span data-ttu-id="bf452-108">앱에서 구현 하도록 선택할 수 있는 다른 bluetooth 기술을 두 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf452-108">There are two different bluetooth technologies that you can choose to implement in your app:</span></span>

* <span data-ttu-id="bf452-109">장치는 클래식 Bluetooth (RFCOMM) 하기 전에 Bluetooth LE, Bluetooth를 사용 하 여 통신할이 프로토콜을 일반적으로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf452-109">Classic Bluetooth (RFCOMM) Before Bluetooth LE, devices commonly used this protocol to communicate using Bluetooth.</span></span> <span data-ttu-id="bf452-110">이 프로토콜은 에너지 절약이 필요 없이 장치 간 통신하는 데 간단하고 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="bf452-110">This protocol is simple and useful for device-to-device communication without the need of energy savings.</span></span> <span data-ttu-id="bf452-111">연결에 연결 해야합니다.</span><span class="sxs-lookup"><span data-stu-id="bf452-111">Connectivity requires pairing.</span></span>

* <span data-ttu-id="bf452-112">Bluetooth 저 에너지 (BLE/LE) Bluetooth Low Energy (LE)는 검색 및는 효율적인 에너지 사용 요구 사항이 있는 장치 간의 통신에 대 한 프로토콜을 정의 하는 사양입니다.</span><span class="sxs-lookup"><span data-stu-id="bf452-112">Bluetooth Low-Energy (BLE/LE) Bluetooth Low Energy (LE) is a specification that defines protocols for discovery and communication between devices that have an efficient energy usage requirement.</span></span> <span data-ttu-id="bf452-113">최근 빌드에 따라 코드 샘플을 비롯 한 자세한 내용은 장치를 연결 하지 않고 BLE 장치에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf452-113">For more information including code samples, As per recent builds, a device can connect to a BLE device without pairing.</span></span>

## <a name="supported-bluetooth-profiles"></a><span data-ttu-id="bf452-114">지원 되는 Bluetooth 프로필</span><span class="sxs-lookup"><span data-stu-id="bf452-114">Supported Bluetooth Profiles</span></span>
<span data-ttu-id="bf452-115">Windows 10 IoT Core는 다음 Bluetooth 프로필을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="bf452-115">Windows 10 IoT Core supports the following Bluetooth profiles:</span></span>

1.  <span data-ttu-id="bf452-116">**장치 프로필 개념 HID (human Interface)** 는 HID 장치 사람이에서 입력을 가져와서 및 사람이 consumpation에 대 한 출력을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf452-116">**Human Interface Device Profiles Concepts (HID)** An HID device takes input from a human and presents output for human consumpation.</span></span> <span data-ttu-id="bf452-117">키보드, 마우스, 게임 컨트롤러, 바코드 판독기, LED 및 영숫자 디스플레이 예로 들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf452-117">Examples are keyboard, mouse, game controller, barcode reader, LED, and alphanumeric display.</span></span> <span data-ttu-id="bf452-118">Windows 10 IoT Core 장치 Bluetooth를 통한 HID 장치를 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf452-118">A Windows 10 IoT Core device can connect to an HID device over Bluetooth.</span></span> <span data-ttu-id="bf452-119">Windows 컨텍스트에서 HID에 대 한 일반 항목을 참조 하세요. [HID 개념 소개](https://docs.microsoft.com/windows-hardware/drivers/hid/introduction-to-hid-concepts)합니다.</span><span class="sxs-lookup"><span data-stu-id="bf452-119">See the general topic about HID in the Windows context: [Introduction to HID Concepts](https://docs.microsoft.com/windows-hardware/drivers/hid/introduction-to-hid-concepts).</span></span> 

2.  <span data-ttu-id="bf452-120">**주파수 통신 (RFCOMM)** RFCOMMM는 클래식 Bluetooth에 대 한 기본 직렬 통신 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf452-120">**Radio Frequency Communication (RFCOMM)** RFCOMMM is the underlying serial communications for Classic Bluetooth.</span></span> <span data-ttu-id="bf452-121">UWP 앱을 사용 하 여 다음 RFCOMM 서비스 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf452-121">With UWP apps, the following RFCOMM services are supported:</span></span>

* <span data-ttu-id="bf452-122">SerialPort</span><span class="sxs-lookup"><span data-stu-id="bf452-122">serialPort</span></span>
* <span data-ttu-id="bf452-123">obexObjectPush</span><span class="sxs-lookup"><span data-stu-id="bf452-123">obexObjectPush</span></span>
* <span data-ttu-id="bf452-124">obexFileTransfer</span><span class="sxs-lookup"><span data-stu-id="bf452-124">obexFileTransfer</span></span>
* <span data-ttu-id="bf452-125">phoneBookAccessPce</span><span class="sxs-lookup"><span data-stu-id="bf452-125">phoneBookAccessPce</span></span>
* <span data-ttu-id="bf452-126">phoneBookAccessPse</span><span class="sxs-lookup"><span data-stu-id="bf452-126">phoneBookAccessPse</span></span>
* <span data-ttu-id="bf452-127">genericFileTransfer</span><span class="sxs-lookup"><span data-stu-id="bf452-127">genericFileTransfer</span></span>

3. <span data-ttu-id="bf452-128">**일반 특성 프로필 (GATT)** 를 참조 합니다 [UWP Bluetooth 저 에너지](https://docs.microsoft.com/windows/uwp/devices-sensors/bluetooth-low-energy-overview) 항목입니다.</span><span class="sxs-lookup"><span data-stu-id="bf452-128">**Generic Attribute Profile (GATT)** See the [UWP-Bluetooth Low Energy](https://docs.microsoft.com/windows/uwp/devices-sensors/bluetooth-low-energy-overview) topic.</span></span> 

> [!NOTE]
> <span data-ttu-id="bf452-129">AppManifest에서 RFCOMM 서비스를 수동으로 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf452-129">You will need to manually specify the RFCOMM services in the AppManifest.</span></span>  <span data-ttu-id="bf452-130">참조 된 [UWP Bluetooth RFCOMM](https://docs.microsoft.com/windows/uwp/devices-sensors/send-or-receive-files-with-rfcomm) 항목입니다.</span><span class="sxs-lookup"><span data-stu-id="bf452-130">See the [UWP-Bluetooth RFCOMM](https://docs.microsoft.com/windows/uwp/devices-sensors/send-or-receive-files-with-rfcomm) topic.</span></span> <span data-ttu-id="bf452-131">참조를 [UWP Bluetooth Rfcomm 채팅 샘플](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/BluetoothRfcommChat) 항목입니다.</span><span class="sxs-lookup"><span data-stu-id="bf452-131">Also see the [UWP-Bluetooth Rfcomm Chat Sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/BluetoothRfcommChat) topic.</span></span>

## <a name="connecting-bluetooth-devices-using-the-device-portal"></a><span data-ttu-id="bf452-132">장치 포털을 사용 하 여 Bluetooth 장치 연결</span><span class="sxs-lookup"><span data-stu-id="bf452-132">Connecting Bluetooth devices using the device portal</span></span>
<span data-ttu-id="bf452-133">중 하나를 사용 하는 경우는 [Windows 10 IoT Core 릴리스 이미지](https://developer.microsoft.com/en-us/windows/iot/downloads) 장치 포털을 사용 하 여 Windows IoT Core 장치를 사용 하 여 Bluetooth 장치를 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf452-133">When using one of the [Windows 10 IoT Core Release Image](https://developer.microsoft.com/en-us/windows/iot/downloads) Bluetooth devices can be paired with the Windows IoT Core device using the device portal.</span></span> <span data-ttu-id="bf452-134">Bluetooth 탭으로 이동 하는 경우 Bluetooth 장치에 대 한 보입니다 장치와 다른 Bluetooth 장치 검색 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf452-134">When navigating to the Bluetooth tab the device will look for Bluetooth devices and will also be discoverable to other Bluetooth devices.</span></span> <span data-ttu-id="bf452-135">아래 그림에는 들어오는 연결 요청을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="bf452-135">The picture below shows an incoming pairing request.</span></span> 

![Bluetooth 들어오는 연결](../media/Bluetooth/Portal_BT_2.png)

<span data-ttu-id="bf452-137">장치는 성공적으로 연결 후 그 아래에 나열 됩니다 장치 쌍을 이루는 섹션</span><span class="sxs-lookup"><span data-stu-id="bf452-137">After the device is successfully paired it will be listed under the paired device section</span></span> 

![Bluetooth 들어오는 연결](../media/Bluetooth/Portal_BT_3.png)
