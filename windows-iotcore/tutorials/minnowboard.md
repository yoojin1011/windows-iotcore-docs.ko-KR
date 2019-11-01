---
title: Minnowboard 설정
ms.date: 05/22/2019
ms.topic: article
description: Windows 10 IoT Core를 사용하여 Minnowboard를 설정하는 방법을 알아봅니다.
keywords: Windows 10 IoT Core, Minnowboard
ms.custom: RS5
ms.openlocfilehash: f74d15a5a20a6869544ad47798457067422590f4
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918661"
---
# <a name="setting-up-a-minnowboard"></a><span data-ttu-id="2ed31-104">MinnowBoard 설정</span><span class="sxs-lookup"><span data-stu-id="2ed31-104">Setting up a MinnowBoard</span></span>

## <a name="overview"></a><span data-ttu-id="2ed31-105">개요</span><span class="sxs-lookup"><span data-stu-id="2ed31-105">Overview</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2ed31-106">MinnowBoard Turbot의 최신 64비트 펌웨어는 [MinnowBoard 웹 사이트](https://minnowboard.org/tutorials/updating-the-firmware)에서 찾을 수 있습니다(MinnowBoard 사이트의 지침에서 4단계 생략).</span><span class="sxs-lookup"><span data-stu-id="2ed31-106">The latest 64-bit firmware for MinnowBoard Turbot can be found on the [MinnowBoard website](https://minnowboard.org/tutorials/updating-the-firmware) (skip step 4 on the MinnowBoard site's instructions).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2ed31-107">"이 디스크 포맷" 팝업이 나타나면 디스크를 포맷하지 _마세요_.</span><span class="sxs-lookup"><span data-stu-id="2ed31-107">When the "format this disk" pop up comes up, do _not_ format the disk.</span></span> <span data-ttu-id="2ed31-108">이 이슈를 수정하기 위한 작업을 진행 중입니다.</span><span class="sxs-lookup"><span data-stu-id="2ed31-108">We are working on a fix for this issue.</span></span>

<span data-ttu-id="2ed31-109">프로토타입 제작용 MinnowBoard를 설정할 때 Windows 10 IoT Core 대시보드를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="2ed31-109">When setting up a MinnowBoard for prototyping, we recommend using the Windows 10 IoT Core Dashboard.</span></span> <span data-ttu-id="2ed31-110">그러나 MinnowBoard를 사용하여 제작하려는 경우에는 [IoT Core 제작 가이드](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2ed31-110">However, if you're looking to manufacture with a MinnowBoard, please refer to the [IoT Core Manufacturing Guide](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).</span></span> <span data-ttu-id="2ed31-111">제조사 이미지는 제작에 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2ed31-111">You cannot use maker images for manufacturing.</span></span>
<br>
> [!Video https://www.youtube.com/embed/JPRUbGIyODY]

## <a name="using-the-dashboard"></a><span data-ttu-id="2ed31-112">대시보드 사용</span><span class="sxs-lookup"><span data-stu-id="2ed31-112">Using the Dashboard</span></span>

<span data-ttu-id="2ed31-113">IoT Core를 MinnowBoard에 플래시 또는 다운로드하려면 다음이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="2ed31-113">To flash, or download, IoT Core onto your MinnowBoard, you'll need:</span></span>
* <span data-ttu-id="2ed31-114">Windows 10을 실행하는 컴퓨터</span><span class="sxs-lookup"><span data-stu-id="2ed31-114">A computer running Windows 10</span></span> 
* [<span data-ttu-id="2ed31-115">Windows 10 IoT Core 대시보드</span><span class="sxs-lookup"><span data-stu-id="2ed31-115">Windows 10 IoT Core Dashboard</span></span>](https://docs.microsoft.com/windows/iot-core/downloads)
* <span data-ttu-id="2ed31-116">SanDisk SD 카드와 같은 고성능 SD 카드</span><span class="sxs-lookup"><span data-stu-id="2ed31-116">A high-performance SD card, such as a SanDisk SD card</span></span>
* <span data-ttu-id="2ed31-117">외부 디스플레이</span><span class="sxs-lookup"><span data-stu-id="2ed31-117">An external display</span></span>
* <span data-ttu-id="2ed31-118">그 외 주변 기기(예: 마우스, 키보드 등)</span><span class="sxs-lookup"><span data-stu-id="2ed31-118">Any other peripherals (e.g. mouse, keyboard, etc.)</span></span>

### <a name="instructions"></a><span data-ttu-id="2ed31-119">지침</span><span class="sxs-lookup"><span data-stu-id="2ed31-119">Instructions</span></span>

1. <span data-ttu-id="2ed31-120">Windows 10 IoT Core 대시보드를 실행하고, *새 디바이스 설치*를 클릭하고, 컴퓨터에 SD 카드를 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="2ed31-120">Run the Windows 10 IoT Core Dashboard and click on *Set up a new device* and insert a SD card into your computer.</span></span>
2. <span data-ttu-id="2ed31-121">MinnowBoard를 외부 디스플레이에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="2ed31-121">Hook up your MinnowBoard to an external display.</span></span>
3. <span data-ttu-id="2ed31-122">필드를 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="2ed31-122">Fill out the fields.</span></span> <span data-ttu-id="2ed31-123">디바이스 유형으로 "Intel [MinnowBoard Turbox/MAX (x64)]"를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2ed31-123">Select "Intel [MinnowBoard Turbox/MAX (x64)]" as the device type.</span></span> <span data-ttu-id="2ed31-124">디바이스에 새 이름과 암호를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2ed31-124">Make sure to give your device a new name and password.</span></span> <span data-ttu-id="2ed31-125">그렇지 않으면 기본 자격 증명은 다음과 같이 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="2ed31-125">Otherwise the default credentials will remain as:</span></span>

```
Device: minwinpc
Password: p@ssw0rd
```

4. <span data-ttu-id="2ed31-126">소프트웨어 사용 조건에 동의하고 *다운로드 및 설치*를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2ed31-126">Accept the software license terms and click *Download and Install*.</span></span> <span data-ttu-id="2ed31-127">정상적으로 작동하는 경우 Windows 10 IoT Core가 SD 카드에 플래시되는 것을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2ed31-127">If all goes well, you'll see that Windows 10 IoT Core is now flashing your SD card.</span></span>

![대시보드 스크린샷](../media/DeviceSetup/Dashboard-Screenshot.jpg)

## <a name="connect-to-a-network"></a><span data-ttu-id="2ed31-129">네트워크에 연결</span><span class="sxs-lookup"><span data-stu-id="2ed31-129">Connect to a network</span></span>
### <a name="wired-connection"></a><span data-ttu-id="2ed31-130">유선 연결</span><span class="sxs-lookup"><span data-stu-id="2ed31-130">Wired connection</span></span>
<span data-ttu-id="2ed31-131">디바이스에 유선 연결을 지원하는 이더넷 포트 또는 USB 이더넷 어댑터가 있는 경우 이더넷 케이블을 연결하여 네트워크에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="2ed31-131">If your device comes with an Ethernet port or USB Ethernet adapter support to enable a wired connection, attach an Ethernet cable to connect it to your network.</span></span>

### <a name="wireless-connection"></a><span data-ttu-id="2ed31-132">무선 연결</span><span class="sxs-lookup"><span data-stu-id="2ed31-132">Wireless connection</span></span>
<span data-ttu-id="2ed31-133">디바이스에서 Wi-Fi 연결이 지원되고 디바이스를 디스플레이에 연결한 경우 다음 단계를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2ed31-133">If your device supports Wi-Fi connectivity and you've connected a display to it, you'll need to:</span></span>

1. <span data-ttu-id="2ed31-134">기본 애플리케이션으로 이동하여 시계 옆에 있는 설정 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2ed31-134">Go into your default application and click the settings button next to the clock.</span></span>
2. <span data-ttu-id="2ed31-135">설정 페이지에서 _네트워크 및 Wi-Fi_를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2ed31-135">On the settings page, select _Network and Wi-Fi_.</span></span>
3. <span data-ttu-id="2ed31-136">디바이스가 무선 네트워크 검색을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="2ed31-136">Your device will begin scanning for wireless networks.</span></span>
4. <span data-ttu-id="2ed31-137">이 목록에 네트워크가 나타나면 네트워크를 선택하고 _연결_을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2ed31-137">Once your network appears in this list, select it and click _Connect_.</span></span>

<span data-ttu-id="2ed31-138">디스플레이를 연결하지 않았으며 Wi-Fi를 통해 연결하려는 경우에는 다음 단계를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2ed31-138">If you haven't connected a display and would like to connect via Wi-Fi, you'll need to:</span></span>

1. <span data-ttu-id="2ed31-139">IoT 대시보드로 이동하여 _내 디바이스_를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2ed31-139">Go to the IoT Dashboard and click on _My Devices_.</span></span>
2. <span data-ttu-id="2ed31-140">목록에서 구성되지 않은 보드를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="2ed31-140">Find your unconfigured board from the list.</span></span> <span data-ttu-id="2ed31-141">보드 이름은 "AJ_"로 시작합니다(예: AJ_58EA6C68).</span><span class="sxs-lookup"><span data-stu-id="2ed31-141">Its name will begin with "AJ_"... (e.g. AJ_58EA6C68).</span></span> <span data-ttu-id="2ed31-142">몇 분이 지나도 보드가 보이지 않으면 보드를 다시 부팅합니다.</span><span class="sxs-lookup"><span data-stu-id="2ed31-142">If you don't see your board appear after a few minutes, try rebooting your board.</span></span>
3. <span data-ttu-id="2ed31-143">_디바이스 구성_을 클릭하고 네트워크 자격 증명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="2ed31-143">Click on _Configure Device_ and enter your network credentials.</span></span> <span data-ttu-id="2ed31-144">그러면 보드가 네트워크에 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="2ed31-144">This will connect your board to the network.</span></span>

> [!NOTE]
> <span data-ttu-id="2ed31-145">다른 네트워크를 찾으려면 컴퓨터의 Wifi를 켜야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2ed31-145">Wifi on your computer will need to be turned on in order to find other networks.</span></span>

## <a name="connect-to-windows-device-portal"></a><span data-ttu-id="2ed31-146">Windows 디바이스 포털에 연결</span><span class="sxs-lookup"><span data-stu-id="2ed31-146">Connect to Windows Device Portal</span></span>

<span data-ttu-id="2ed31-147">[Windows 디바이스 포털](../manage-your-device/DevicePortal.md)을 사용하여 웹 브라우저를 통해 디바이스를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="2ed31-147">Use the [Windows Device Portal](../manage-your-device/DevicePortal.md) to connect your device through a web browser.</span></span> <span data-ttu-id="2ed31-148">디바이스 포털에서는 중요한 구성과 디바이스 관리 기능을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2ed31-148">The device portal makes valuable configuration and device management capabilities available.</span></span> 
