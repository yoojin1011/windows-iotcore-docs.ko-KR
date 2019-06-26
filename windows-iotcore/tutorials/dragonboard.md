---
title: Dragonboard 설정
ms.author: saclayt
ms.date: 05/22/2019
ms.topic: article
description: Windows 10 IoT Core를 사용하여 Dragonboard를 설정하는 방법을 알아봅니다.
keywords: Windows 10 IoT Core, Dragonboard
ms.custom: RS5
ms.openlocfilehash: 6488237a41f42c7acbe9e5e1c68466548577ab38
ms.sourcegitcommit: 9ec4716afde25fdc8b94f7c0794448501f451b55
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/17/2019
ms.locfileid: "66835605"
---
# <a name="setting-up-a-dragonboard"></a><span data-ttu-id="3efa1-104">Dragonboard 설정</span><span class="sxs-lookup"><span data-stu-id="3efa1-104">Setting up a Dragonboard</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3efa1-105">새 Dragonboard를 사용하는 경우 Android가 설치된 상태로 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="3efa1-105">When you're working with a new Dragonboard, it comes with Android installed.</span></span> <span data-ttu-id="3efa1-106">[여기](https://docs.microsoft.com/en-us/windows/iot-core/tutorials/qualcomm)서 eMMC 플래시 메서드를 사용하여 디바이스의 데이터를 지우고 다시 로드해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3efa1-106">You will need to wipe and load the device using the eMMC flashing method, [here](https://docs.microsoft.com/en-us/windows/iot-core/tutorials/qualcomm).</span></span>

> [!NOTE]
> <span data-ttu-id="3efa1-107">DragonBoard에서 오디오 관련 이슈가 발생하는 경우 [여기서](https://developer.qualcomm.com/download/db410c/stereo-connector-and-audio-routing-application-note.pdf) Qualcomm의 설명서를 읽어보시기를 권장합니다.</span><span class="sxs-lookup"><span data-stu-id="3efa1-107">If you're running into any audio-related issues with your DragonBoard, we advise that you read through Qualcomm's manual [here](https://developer.qualcomm.com/download/db410c/stereo-connector-and-audio-routing-application-note.pdf).</span></span> 

<span data-ttu-id="3efa1-108">프로토타입 제작용 Dragonboard를 설정할 때 Windows 10 IoT Core 대시보드를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="3efa1-108">When setting up a Dragonboard for prototyping, we recommend using the Windows 10 IoT Core Dashboard.</span></span> <span data-ttu-id="3efa1-109">그러나 Dragonboard를 사용하여 제작하려는 경우에는 [IoT Core 제작 가이드](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3efa1-109">However, if you're looking to manufacture with a Dragonboard, please refer to the [IoT Core Manufacturing Guide](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).</span></span> <span data-ttu-id="3efa1-110">제조사 이미지는 제작에 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3efa1-110">You cannot use maker images for manufacturing.</span></span>
<br>
> [!Video https://www.youtube.com/embed/iPm57hGq-Q8]

## <a name="using-the-dashboard"></a><span data-ttu-id="3efa1-111">대시보드 사용</span><span class="sxs-lookup"><span data-stu-id="3efa1-111">Using the Dashboard</span></span>

<span data-ttu-id="3efa1-112">IoT Core를 MinnowBoard에 플래시 또는 다운로드하려면 다음이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="3efa1-112">To flash, or download, IoT Core onto your MinnowBoard, you'll need:</span></span>
* <span data-ttu-id="3efa1-113">Windows 10을 실행하는 컴퓨터</span><span class="sxs-lookup"><span data-stu-id="3efa1-113">A computer running Windows 10</span></span> 
* [<span data-ttu-id="3efa1-114">Windows 10 IoT Core 대시보드</span><span class="sxs-lookup"><span data-stu-id="3efa1-114">Windows 10 IoT Core Dashboard</span></span>](https://docs.microsoft.com/windows/iot-core/downloads)
* <span data-ttu-id="3efa1-115">MicroUSB 케이블</span><span class="sxs-lookup"><span data-stu-id="3efa1-115">MicroUSB cable</span></span>
* <span data-ttu-id="3efa1-116">외부 디스플레이</span><span class="sxs-lookup"><span data-stu-id="3efa1-116">An external display</span></span>
* <span data-ttu-id="3efa1-117">그 외 주변 기기(예: 마우스, 키보드 등)</span><span class="sxs-lookup"><span data-stu-id="3efa1-117">Any other peripherals (e.g. mouse, keyboard, etc.)</span></span>

### <a name="instructions"></a><span data-ttu-id="3efa1-118">지침</span><span class="sxs-lookup"><span data-stu-id="3efa1-118">Instructions</span></span>

1. <span data-ttu-id="3efa1-119">Windows 10 IoT Core 대시보드를 실행하고 *새 디바이스 설정*을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3efa1-119">Run the Windows 10 IoT Core Dashboard and click on *Set up a new device*.</span></span>
2. <span data-ttu-id="3efa1-120">디바이스 유형으로 "Qualcomm [DragonBoard 410c]"를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3efa1-120">Select "Qualcomm [DragonBoard 410c]" as the device type.</span></span>
3. <span data-ttu-id="3efa1-121">microUSB 케이블을 사용하여 DragonBoard를 컴퓨터에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="3efa1-121">Connect the DragonBoard to your compuetr using a microUSB cable.</span></span>
4. <span data-ttu-id="3efa1-122">DragongBoard를 외부 디스플레이에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="3efa1-122">Hook up your DragongBoard to a external display.</span></span>
5. <span data-ttu-id="3efa1-123">볼륨 크게(+) 단추를 누른 상태에서 12V(>1A) 전원 공급 장치를 사용하여 Dragonboard를 켭니다.</span><span class="sxs-lookup"><span data-stu-id="3efa1-123">Power on your Dragonboard using a 12V (>1A) power supply while holding down the volume up (+) button.</span></span> <span data-ttu-id="3efa1-124">디바이스를 디스플레이에 연결하면 망치, 번개 및 톱니 이미지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3efa1-124">The device - when connected to a display - should show the image of a hammer, a lightning bolt, and a cog.</span></span>
6. <span data-ttu-id="3efa1-125">이제 디바이스가 대시보드에 아래와 같이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3efa1-125">The device should now be visible on the Dashboard as shown below.</span></span> <span data-ttu-id="3efa1-126">적절한 디바이스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3efa1-126">Select the appropriate device.</span></span>
7. <span data-ttu-id="3efa1-127">소프트웨어 사용 조건에 동의하고 **다운로드 및 설치**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3efa1-127">Accept the software license terms and click **Download and install**.</span></span> <span data-ttu-id="3efa1-128">Windows 10 IoT Core가 디바이스에 플래시되는 것을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3efa1-128">You'll see that Windows 10 IoT Core is now flashing onto your device.</span></span>

![플래시 모드의 DragonBoard](../media/DeviceSetup/db4.png)

## <a name="connect-to-a-network"></a><span data-ttu-id="3efa1-130">네트워크에 연결</span><span class="sxs-lookup"><span data-stu-id="3efa1-130">Connect to a network</span></span>
### <a name="wired-connection"></a><span data-ttu-id="3efa1-131">유선 연결</span><span class="sxs-lookup"><span data-stu-id="3efa1-131">Wired connection</span></span>
<span data-ttu-id="3efa1-132">디바이스에 유선 연결을 지원하는 이더넷 포트 또는 USB 이더넷 어댑터가 있는 경우 이더넷 케이블을 연결하여 네트워크에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="3efa1-132">If your device comes with an Ethernet port or USB Ethernet adapter support to enable a wired connection, attach an Ethernet cable to connect it to your network.</span></span>

### <a name="wireless-connection"></a><span data-ttu-id="3efa1-133">무선 연결</span><span class="sxs-lookup"><span data-stu-id="3efa1-133">Wireless connection</span></span>
<span data-ttu-id="3efa1-134">디바이스에서 Wi-Fi 연결이 지원되고 디바이스를 디스플레이에 연결한 경우 다음 단계를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3efa1-134">If your device supports Wi-Fi connectivity and you've connected a display to it, you'll need to:</span></span>

1. <span data-ttu-id="3efa1-135">기본 애플리케이션으로 이동하여 시계 옆에 있는 설정 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3efa1-135">Go into your default application and click the settings button next to the clock.</span></span>
2. <span data-ttu-id="3efa1-136">설정 페이지에서 _네트워크 및 Wi-Fi_를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3efa1-136">On the settings page, select _Network and Wi-Fi_.</span></span>
3. <span data-ttu-id="3efa1-137">디바이스가 무선 네트워크 검색을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="3efa1-137">Your device will begin scanning for wireless networks.</span></span>
4. <span data-ttu-id="3efa1-138">이 목록에 네트워크가 나타나면 네트워크를 선택하고 _연결_을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3efa1-138">Once your network appears in this list, select it and click _Connect_.</span></span>

<span data-ttu-id="3efa1-139">디스플레이를 연결하지 않았으며 Wi-Fi를 통해 연결하려는 경우에는 다음 단계를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3efa1-139">If you haven't connected a display and would like to connect via Wi-Fi, you'll need to:</span></span>

1. <span data-ttu-id="3efa1-140">IoT 대시보드로 이동하여 _내 디바이스_를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3efa1-140">Go to the IoT Dashboard and click on _My Devices_.</span></span>
2. <span data-ttu-id="3efa1-141">목록에서 구성되지 않은 보드를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="3efa1-141">Find your unconfigured board from the list.</span></span> <span data-ttu-id="3efa1-142">보드 이름은 "AJ_"로 시작합니다(예: AJ_58EA6C68).</span><span class="sxs-lookup"><span data-stu-id="3efa1-142">Its name will begin with "AJ_"... (e.g. AJ_58EA6C68).</span></span> <span data-ttu-id="3efa1-143">몇 분이 지나도 보드가 보이지 않으면 보드를 다시 부팅합니다.</span><span class="sxs-lookup"><span data-stu-id="3efa1-143">If you don't see your board appear after a few minutes, try rebooting your board.</span></span>
3. <span data-ttu-id="3efa1-144">_디바이스 구성_을 클릭하고 네트워크 자격 증명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3efa1-144">Click on _Configure Device_ and enter your network credentials.</span></span> <span data-ttu-id="3efa1-145">그러면 보드가 네트워크에 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="3efa1-145">This will connect your board to the network.</span></span>

> [!NOTE]
> <span data-ttu-id="3efa1-146">다른 네트워크를 찾으려면 컴퓨터의 Wifi를 켜야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3efa1-146">Wifi on your computer will need to be turned on in order to find other networks.</span></span>

## <a name="connect-to-windows-device-portal"></a><span data-ttu-id="3efa1-147">Windows 디바이스 포털에 연결</span><span class="sxs-lookup"><span data-stu-id="3efa1-147">Connect to Windows Device Portal</span></span>

<span data-ttu-id="3efa1-148">[Windows 디바이스 포털](../manage-your-device/DevicePortal.md)을 사용하여 웹 브라우저를 통해 디바이스를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="3efa1-148">Use the [Windows Device Portal](../manage-your-device/DevicePortal.md) to connect your device through a web browser.</span></span> <span data-ttu-id="3efa1-149">디바이스 포털에서는 중요한 구성과 디바이스 관리 기능을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3efa1-149">The device portal makes valuable configuration and device management capabilities available.</span></span> 

