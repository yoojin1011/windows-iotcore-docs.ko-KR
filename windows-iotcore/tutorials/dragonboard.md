---
title: Dragonboard 설정
ms.author: saclayt
ms.date: 05/22/2019
ms.topic: article
description: Windows 10 IoT Core 사용 하 여 프로그램 Dragonboard를 설정 하는 방법에 알아봅니다.
keywords: Windows 10 IoT Core, Dragonboard
ms.custom: RS5
ms.openlocfilehash: 8e4acc77d902124934e1bdae249f76c7f76306a6
ms.sourcegitcommit: 8aadc776da7b473159f9023cd555145819e7e952
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66182275"
---
# <a name="setting-up-a-dragonboard"></a><span data-ttu-id="b7f40-104">Dragonboard 설정</span><span class="sxs-lookup"><span data-stu-id="b7f40-104">Setting up a Dragonboard</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b7f40-105">새 Dragonboard을 사용 하는 경우 설치 하는 Android를 사용 하 여 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b7f40-105">When you're working with a new Dragonboard, it comes with Android installed.</span></span> <span data-ttu-id="b7f40-106">초기화 및 eMMC 깜박이 메서드를 사용 하 여 장치를 로드 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7f40-106">You will need to wipe and load the device using the eMMC flashing method.</span></span>

> [!NOTE]
> <span data-ttu-id="b7f40-107">프로그램 DragonBoard를 사용 하 여 오디오 관련 문제를 실행 하는 경우 Qualcomm의 수동를 읽는 것이 좋습니다 [여기](https://developer.qualcomm.com/download/db410c/stereo-connector-and-audio-routing-application-note.pdf)합니다.</span><span class="sxs-lookup"><span data-stu-id="b7f40-107">If you're running into any audio-related issues with your DragonBoard, we advise that you read through Qualcomm's manual [here](https://developer.qualcomm.com/download/db410c/stereo-connector-and-audio-routing-application-note.pdf).</span></span> 

<span data-ttu-id="b7f40-108">프로토타입 제작 Dragonboard를 설정할 때 Windows 10 IoT Core 대시보드를 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="b7f40-108">When setting up a Dragonboard for prototyping, we recommend using the Windows 10 IoT Core Dashboard.</span></span> <span data-ttu-id="b7f40-109">그러나는 Dragonboard를 사용 하 여 제조 하려는 경우를 참조 하십시오 합니다 [IoT Core 제조 가이드](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)합니다.</span><span class="sxs-lookup"><span data-stu-id="b7f40-109">However, if you're looking to manufacture with a Dragonboard, please refer to the [IoT Core Manufacturing Guide](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).</span></span> <span data-ttu-id="b7f40-110">제조를 위한 작성자 이미지를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b7f40-110">You cannot use maker images for manufacturing.</span></span>
<br>
> [!Video https://www.youtube.com/embed/iPm57hGq-Q8]

## <a name="using-the-dashboard"></a><span data-ttu-id="b7f40-111">대시보드 사용</span><span class="sxs-lookup"><span data-stu-id="b7f40-111">Using the Dashboard</span></span>

<span data-ttu-id="b7f40-112">Flash를 또는 MinnowBoard에 IoT Core를 다운로드 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7f40-112">To flash, or download, IoT Core onto your MinnowBoard, you'll need:</span></span>
* <span data-ttu-id="b7f40-113">Windows 10을 실행 하는 컴퓨터</span><span class="sxs-lookup"><span data-stu-id="b7f40-113">A computer running Windows 10</span></span> 
* [<span data-ttu-id="b7f40-114">Windows 10 IoT Core 대시보드</span><span class="sxs-lookup"><span data-stu-id="b7f40-114">Windows 10 IoT Core Dashboard</span></span>](https://docs.microsoft.com/windows/iot-core/downloads)
* <span data-ttu-id="b7f40-115">MicroUSB 케이블</span><span class="sxs-lookup"><span data-stu-id="b7f40-115">MicroUSB cable</span></span>
* <span data-ttu-id="b7f40-116">외부 디스플레이</span><span class="sxs-lookup"><span data-stu-id="b7f40-116">An external display</span></span>
* <span data-ttu-id="b7f40-117">모든 기타 주변 장치 (예: 마우스, 키보드 등)</span><span class="sxs-lookup"><span data-stu-id="b7f40-117">Any other peripherals (e.g. mouse, keyboard, etc.)</span></span>

### <a name="instructions"></a><span data-ttu-id="b7f40-118">지침</span><span class="sxs-lookup"><span data-stu-id="b7f40-118">Instructions</span></span>

1. <span data-ttu-id="b7f40-119">Windows 10 IoT Core 대시보드를 실행 하 고 클릭 *새 장치 설정*합니다.</span><span class="sxs-lookup"><span data-stu-id="b7f40-119">Run the Windows 10 IoT Core Dashboard and click on *Set up a new device*.</span></span>
2. <span data-ttu-id="b7f40-120">장치 유형으로 "Qualcomm [DragonBoard 410 c]"를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7f40-120">Select "Qualcomm [DragonBoard 410c]" as the device type.</span></span>
3. <span data-ttu-id="b7f40-121">DragonBoard microUSB 케이블을 사용 하 여 compuetr에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7f40-121">Connect the DragonBoard to your compuetr using a microUSB cable.</span></span>
4. <span data-ttu-id="b7f40-122">프로그램 DragongBoard 외부 디스플레이에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7f40-122">Hook up your DragongBoard to a external display.</span></span>
5. <span data-ttu-id="b7f40-123">전원 켜기 12V를 사용 하 여 Dragonboard (> 1A) 전원 공급 장치 볼륨 크게 (+)를 누른 채 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="b7f40-123">Power on your Dragonboard using a 12V (>1A) power supply while holding down the volume up (+) button.</span></span> <span data-ttu-id="b7f40-124">장치--디스플레이에 연결 하는 경우 망치, 번개, 및는 코그의 이미지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b7f40-124">The device - when connected to a display - should show the image of a hammer, a lightning bolt, and a cog.</span></span>
6. <span data-ttu-id="b7f40-125">이제 장치 대시보드에서 아래와 같이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b7f40-125">The device should now be visible on the Dashboard as shown below.</span></span> <span data-ttu-id="b7f40-126">적절 한 장치를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7f40-126">Select the appropriate device.</span></span>
7. <span data-ttu-id="b7f40-127">소프트웨어 licnse 조건에 동의 하 고 클릭 **다운로드 및 설치**합니다.</span><span class="sxs-lookup"><span data-stu-id="b7f40-127">Accept the software licnse terms and click **Download and install**.</span></span> <span data-ttu-id="b7f40-128">Windows 10 IoT Core 이제 장치에 깜박이 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b7f40-128">You'll see that Windows 10 IoT Core is now flashing onto your device.</span></span>

![플래시 모드로 DragonBoard](../media/DeviceSetup/db4.png)

## <a name="connect-to-a-network"></a><span data-ttu-id="b7f40-130">네트워크에 연결</span><span class="sxs-lookup"><span data-stu-id="b7f40-130">Connect to a network</span></span>
### <a name="wired-connection"></a><span data-ttu-id="b7f40-131">유선된으로 연결</span><span class="sxs-lookup"><span data-stu-id="b7f40-131">Wired connection</span></span>
<span data-ttu-id="b7f40-132">이더넷 포트 또는 유선된 연결을 사용 하려면 USB 이더넷 어댑터에서 지 원하는 장치의 상태가 되 면 네트워크에 연결할 이더넷 케이블을 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7f40-132">If your device comes with an Ethernet port or USB Ethernet adapter support to enable a wired connection, attach an Ethernet cable to connect it to your network.</span></span>

### <a name="wireless-connection"></a><span data-ttu-id="b7f40-133">무선 연결</span><span class="sxs-lookup"><span data-stu-id="b7f40-133">Wireless connection</span></span>
<span data-ttu-id="b7f40-134">장치에서 Wi-fi 연결을 지 원하는 경우 디스플레이에 연결 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7f40-134">If your device supports Wi-Fi connectivity and you've connected a display to it, you'll need to:</span></span>

1. <span data-ttu-id="b7f40-135">기본 응용 프로그램으로 이동한 다음 클록 옆에 있는 설정 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7f40-135">Go into your default application and click the settings button next to the clock.</span></span>
2. <span data-ttu-id="b7f40-136">설정 페이지에서 선택 _네트워크 및 Wi-fi_합니다.</span><span class="sxs-lookup"><span data-stu-id="b7f40-136">On the settings page, select _Network and Wi-Fi_.</span></span>
3. <span data-ttu-id="b7f40-137">장치의 무선 네트워크에 대 한 검색을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7f40-137">Your device will begin scanning for wireless networks.</span></span>
4. <span data-ttu-id="b7f40-138">이 목록에 표시 되는 네트워크를 선택 하 고 클릭 _Connect_합니다.</span><span class="sxs-lookup"><span data-stu-id="b7f40-138">Once your network appears in this list, select it and click _Connect_.</span></span>

<span data-ttu-id="b7f40-139">디스플레이 연결 하지 않은 하 고 Wi-fi를 통해 연결 하려는 경우을 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7f40-139">If you haven't connected a display and would like to connect via Wi-Fi, you'll need to:</span></span>

1. <span data-ttu-id="b7f40-140">IoT 대시보드로 이동 하 고 클릭 _내 장치_합니다.</span><span class="sxs-lookup"><span data-stu-id="b7f40-140">Go to the IoT Dashboard and click on _My Devices_.</span></span>
2. <span data-ttu-id="b7f40-141">목록에서 구성 되지 않은 보드를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="b7f40-141">Find your unconfigured board from the list.</span></span> <span data-ttu-id="b7f40-142">이름과 "AJ_"로 시작 됩니다... (예:: AJ_58EA6C68)입니다.</span><span class="sxs-lookup"><span data-stu-id="b7f40-142">Its name will begin with "AJ_"... (e.g. AJ_58EA6C68).</span></span> <span data-ttu-id="b7f40-143">몇 분 정도 지나면 보드 표시 되지 않는 경우 보드를 다시 부팅 하십시오.</span><span class="sxs-lookup"><span data-stu-id="b7f40-143">If you don't see your board appear after a few minutes, try rebooting your board.</span></span>
3. <span data-ttu-id="b7f40-144">클릭할 _장치 구성_ 네트워크 자격 증명을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7f40-144">Click on _Configure Device_ and enter your network credentials.</span></span> <span data-ttu-id="b7f40-145">그러면 네트워크에 보드를 연결 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b7f40-145">This will connect your board to the network.</span></span>

> [!NOTE]
> <span data-ttu-id="b7f40-146">Wifi를 컴퓨터에 다른 네트워크를 찾을 수 있도록 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7f40-146">Wifi on your computer will need to be turned on in order to find other networks.</span></span>

## <a name="connect-to-windows-device-portal"></a><span data-ttu-id="b7f40-147">Windows Device Portal 연결</span><span class="sxs-lookup"><span data-stu-id="b7f40-147">Connect to Windows Device Portal</span></span>

<span data-ttu-id="b7f40-148">사용 합니다 [Windows Device Portal](../manage-your-device/DevicePortal.md) 웹 브라우저를 통해 장치를 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7f40-148">Use the [Windows Device Portal](../manage-your-device/DevicePortal.md) to connect your device through a web browser.</span></span> <span data-ttu-id="b7f40-149">장치 포털 중요 한 구성 및 장치 관리 기능을 사용할 수 있게 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7f40-149">The device portal makes valuable configuration and device management capabilities available.</span></span> 

