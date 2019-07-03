---
title: Raspberry Pi 설정
ms.author: saclayt
ms.date: 05/22/2019
ms.topic: article
description: Windows 10 IoT Core를 사용하여 Raspberry Pi를 설정하는 방법을 알아봅니다.
keywords: Windows 10 IoT Core, Raspberry Pi
ms.custom: RS5
ms.openlocfilehash: 3269aa2ed102b667519baa9212e604083f910783
ms.sourcegitcommit: 9ec4716afde25fdc8b94f7c0794448501f451b55
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/17/2019
ms.locfileid: "66182195"
---
# <a name="setting-up-a-raspberry-pi"></a><span data-ttu-id="016ac-104">Raspberry Pi 설정</span><span class="sxs-lookup"><span data-stu-id="016ac-104">Setting up a Raspberry Pi</span></span>

## <a name="overview"></a><span data-ttu-id="016ac-105">개요</span><span class="sxs-lookup"><span data-stu-id="016ac-105">Overview</span></span>

> [!NOTE]
> <span data-ttu-id="016ac-106">대시보드는 Raspberry Pi 3B+를 설정하는 데 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="016ac-106">Dashboard cannot be used used to setup the Raspberry Pi 3B+.</span></span> <span data-ttu-id="016ac-107">3B+ 디바이스가 있는 경우 [3B+ 기술 미리 보기](https://www.microsoft.com/en-us/software-download/windowsiot)를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="016ac-107">If you have a 3B+ device, you must use the [3B+ technical preview](https://www.microsoft.com/en-us/software-download/windowsiot).</span></span> <span data-ttu-id="016ac-108">기술 미리 보기의 [알려진 제한 사항](https://docs.microsoft.com/en-us/windows/iot-core/troubleshooting)을 확인하여 개발 작업에 적합한지 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="016ac-108">Please view the [known limitations](https://docs.microsoft.com/en-us/windows/iot-core/troubleshooting) of the technical preview to determine if this is suitable for your development.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="016ac-109">"이 디스크 포맷" 팝업이 나타나면 디스크를 포맷하지 _마세요_.</span><span class="sxs-lookup"><span data-stu-id="016ac-109">When the "format this disk" pop up comes up, do _not_ format the disk.</span></span> <span data-ttu-id="016ac-110">이 이슈를 수정하기 위한 작업을 진행 중입니다.</span><span class="sxs-lookup"><span data-stu-id="016ac-110">We are working on a fix for this issue.</span></span>

<span data-ttu-id="016ac-111">프로토타입 제작용 Raspberry Pi를 설정할 때 Windows 10 IoT Core 대시보드를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="016ac-111">When setting up a Raspberry Pi for prototyping, we recommend using the Windows 10 IoT Core Dashboard.</span></span> <span data-ttu-id="016ac-112">그러나 Raspberry Pi를 사용하여 제작하려는 경우에는 [IoT Core 제작 가이드](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="016ac-112">However, if you're looking to manufacture with a Raspberry Pi, please refer to the [IoT Core Manufacturing Guide](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).</span></span> <span data-ttu-id="016ac-113">제조사 이미지는 제작에 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="016ac-113">You cannot use maker images for manufacturing.</span></span>
<br>
> [!Video https://www.youtube.com/embed/JPRUbGIyODY]

## <a name="using-the-dashboard"></a><span data-ttu-id="016ac-114">대시보드 사용</span><span class="sxs-lookup"><span data-stu-id="016ac-114">Using the Dashboard</span></span>

<span data-ttu-id="016ac-115">IoT Core를 Raspberry Pi에 플래시 또는 다운로드하려면 다음이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="016ac-115">To flash, or download, IoT Core onto your Raspberry Pi, you'll need:</span></span>
* <span data-ttu-id="016ac-116">Windows 10을 실행하는 컴퓨터</span><span class="sxs-lookup"><span data-stu-id="016ac-116">A computer running Windows 10</span></span> 
* [<span data-ttu-id="016ac-117">Windows 10 IoT Core 대시보드</span><span class="sxs-lookup"><span data-stu-id="016ac-117">Windows 10 IoT Core Dashboard</span></span>](https://docs.microsoft.com/windows/iot-core/downloads)
* <span data-ttu-id="016ac-118">SanDisk SD 카드와 같은 고성능 SD 카드</span><span class="sxs-lookup"><span data-stu-id="016ac-118">A high-performance SD card, such as a SanDisk SD card</span></span>
* <span data-ttu-id="016ac-119">외부 디스플레이</span><span class="sxs-lookup"><span data-stu-id="016ac-119">An external display</span></span>
* <span data-ttu-id="016ac-120">그 외 주변 기기(예: 마우스, 키보드 등)</span><span class="sxs-lookup"><span data-stu-id="016ac-120">Any other peripherals (e.g. mouse, keyboard, etc.)</span></span>

### <a name="instructions"></a><span data-ttu-id="016ac-121">지침</span><span class="sxs-lookup"><span data-stu-id="016ac-121">Instructions</span></span>

1. <span data-ttu-id="016ac-122">Windows 10 IoT Core 대시보드를 실행하고, *새 디바이스 설치*를 클릭하고, 컴퓨터에 SD 카드를 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="016ac-122">Run the Windows 10 IoT Core Dashboard and click on *Set up a new device* and insert a SD card into your computer.</span></span>
2. <span data-ttu-id="016ac-123">Raspberry Pi를 외부 디스플레이에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="016ac-123">Hook up your Raspberry Pi to an external display.</span></span>
3. <span data-ttu-id="016ac-124">필드를 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="016ac-124">Fill out the fields.</span></span> <span data-ttu-id="016ac-125">디바이스 유형으로 "Broadcomm [Raspberry Pi 2 & 3]"을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="016ac-125">Select "Broadcomm [Raspberry Pi 2 & 3]" as the device type.</span></span> <span data-ttu-id="016ac-126">디바이스에 새 이름과 암호를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="016ac-126">Make sure to give your device a new name and password.</span></span> <span data-ttu-id="016ac-127">그렇지 않으면 기본 자격 증명은 다음과 같이 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="016ac-127">Otherwise the default credentials will remain as:</span></span>

```
Device: minwinpc
Password: p@ssw0rd
```

4. <span data-ttu-id="016ac-128">소프트웨어 사용 조건에 동의하고 *다운로드 및 설치*를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="016ac-128">Accept the software license terms and click *Download and Install*.</span></span> <span data-ttu-id="016ac-129">정상적으로 작동하는 경우 Windows 10 IoT Core가 SD 카드에 플래시되는 것을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="016ac-129">If all goes well, you'll see that Windows 10 IoT Core is now flashing your SD card.</span></span>

![대시보드 스크린샷](../media/DeviceSetup/Dashboard-Screenshot.jpg)

## <a name="connect-to-a-network"></a><span data-ttu-id="016ac-131">네트워크에 연결</span><span class="sxs-lookup"><span data-stu-id="016ac-131">Connect to a network</span></span>
### <a name="wired-connection"></a><span data-ttu-id="016ac-132">유선 연결</span><span class="sxs-lookup"><span data-stu-id="016ac-132">Wired connection</span></span>
<span data-ttu-id="016ac-133">디바이스에 유선 연결을 지원하는 이더넷 포트 또는 USB 이더넷 어댑터가 있는 경우 이더넷 케이블을 연결하여 네트워크에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="016ac-133">If your device comes with an Ethernet port or USB Ethernet adapter support to enable a wired connection, attach an Ethernet cable to connect it to your network.</span></span>

### <a name="wireless-connection"></a><span data-ttu-id="016ac-134">무선 연결</span><span class="sxs-lookup"><span data-stu-id="016ac-134">Wireless connection</span></span>
<span data-ttu-id="016ac-135">디바이스에서 Wi-Fi 연결이 지원되고 디바이스를 디스플레이에 연결한 경우 다음 단계를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="016ac-135">If your device supports Wi-Fi connectivity and you've connected a display to it, you'll need to:</span></span>

1. <span data-ttu-id="016ac-136">기본 애플리케이션으로 이동하여 시계 옆에 있는 설정 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="016ac-136">Go into your default application and click the settings button next to the clock.</span></span>
2. <span data-ttu-id="016ac-137">설정 페이지에서 _네트워크 및 Wi-Fi_를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="016ac-137">On the settings page, select _Network and Wi-Fi_.</span></span>
3. <span data-ttu-id="016ac-138">디바이스가 무선 네트워크 검색을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="016ac-138">Your device will begin scanning for wireless networks.</span></span>
4. <span data-ttu-id="016ac-139">이 목록에 네트워크가 나타나면 네트워크를 선택하고 _연결_을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="016ac-139">Once your network appears in this list, select it and click _Connect_.</span></span>

<span data-ttu-id="016ac-140">디스플레이를 연결하지 않았으며 Wi-Fi를 통해 연결하려는 경우에는 다음 단계를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="016ac-140">If you haven't connected a display and would like to connect via Wi-Fi, you'll need to:</span></span>

1. <span data-ttu-id="016ac-141">IoT 대시보드로 이동하여 _내 디바이스_를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="016ac-141">Go to the IoT Dashboard and click on _My Devices_.</span></span>
2. <span data-ttu-id="016ac-142">목록에서 구성되지 않은 보드를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="016ac-142">Find your unconfigured board from the list.</span></span> <span data-ttu-id="016ac-143">보드 이름은 "AJ_"로 시작합니다(예: AJ_58EA6C68).</span><span class="sxs-lookup"><span data-stu-id="016ac-143">Its name will begin with "AJ_"... (e.g. AJ_58EA6C68).</span></span> <span data-ttu-id="016ac-144">몇 분이 지나도 보드가 보이지 않으면 보드를 다시 부팅합니다.</span><span class="sxs-lookup"><span data-stu-id="016ac-144">If you don't see your board appear after a few minutes, try rebooting your board.</span></span>
3. <span data-ttu-id="016ac-145">_디바이스 구성_을 클릭하고 네트워크 자격 증명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="016ac-145">Click on _Configure Device_ and enter your network credentials.</span></span> <span data-ttu-id="016ac-146">그러면 보드가 네트워크에 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="016ac-146">This will connect your board to the network.</span></span>

> [!NOTE]
> <span data-ttu-id="016ac-147">다른 네트워크를 찾으려면 컴퓨터의 Wifi를 켜야 합니다.</span><span class="sxs-lookup"><span data-stu-id="016ac-147">Wifi on your computer will need to be turned on in order to find other networks.</span></span>

## <a name="connect-to-windows-device-portal"></a><span data-ttu-id="016ac-148">Windows 디바이스 포털에 연결</span><span class="sxs-lookup"><span data-stu-id="016ac-148">Connect to Windows Device Portal</span></span>

<span data-ttu-id="016ac-149">[Windows 디바이스 포털](../manage-your-device/DevicePortal.md)을 사용하여 웹 브라우저를 통해 디바이스를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="016ac-149">Use the [Windows Device Portal](../manage-your-device/DevicePortal.md) to connect your device through a web browser.</span></span> <span data-ttu-id="016ac-150">디바이스 포털에서는 중요한 구성과 디바이스 관리 기능을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="016ac-150">The device portal makes valuable configuration and device management capabilities available.</span></span> 
