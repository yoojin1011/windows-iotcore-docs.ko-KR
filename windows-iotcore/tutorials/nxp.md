---
title: NXP 디바이스 설정
ms.date: 05/22/2019
ms.topic: article
description: Windows 10 IoT Core를 사용하여 NXP 디바이스를 설정하는 방법을 알아봅니다.
keywords: Windows 10 IoT Core, NXP
ms.custom: RS5
ms.openlocfilehash: aa3e28cb79e69c1faccd733d993c8ec12f6ae314
ms.sourcegitcommit: ea060254f9c4c25afcd0245c897b9e1425321859
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75721734"
---
# <a name="setting-up-a-nxp-device"></a><span data-ttu-id="cd4d7-104">NXP 디바이스 설정</span><span class="sxs-lookup"><span data-stu-id="cd4d7-104">Setting up a NXP device</span></span>

## <a name="overview"></a><span data-ttu-id="cd4d7-105">개요</span><span class="sxs-lookup"><span data-stu-id="cd4d7-105">Overview</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cd4d7-106">"이 디스크 포맷" 팝업이 나타나면 디스크를 포맷하지 _마세요_.</span><span class="sxs-lookup"><span data-stu-id="cd4d7-106">When the "format this disk" pop up comes up, do _not_ format the disk.</span></span> <span data-ttu-id="cd4d7-107">이 이슈를 수정하기 위한 작업을 진행 중입니다.</span><span class="sxs-lookup"><span data-stu-id="cd4d7-107">We are working on a fix for this issue.</span></span>

> [!NOTE]
> <span data-ttu-id="cd4d7-108">NXP에 대한 설정은 Raspberry Pi를 설정하는 것과 거의 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="cd4d7-108">Set up for the NXP is nearly identical to setting up a Raspberry Pi.</span></span>

<span data-ttu-id="cd4d7-109">프로토타입 제작용 NXP 디바이스를 설정할 때 Windows 10 IoT Core 대시보드를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="cd4d7-109">When setting up a NXP device for prototyping, we recommend using the Windows 10 IoT Core Dashboard.</span></span> <span data-ttu-id="cd4d7-110">그러나 NXP 디바이스를 사용하여 제작하려는 경우에는 [IoT Core 제작 가이드](https://docs.microsoft.com/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cd4d7-110">However, if you're looking to manufacture with a NXP device, please refer to the [IoT Core Manufacturing Guide](https://docs.microsoft.com/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).</span></span> <span data-ttu-id="cd4d7-111">제조사 이미지는 제작에 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="cd4d7-111">You cannot use maker images for manufacturing.</span></span>
<br>
> [!Video https://www.youtube.com/embed/JPRUbGIyODY]

## <a name="using-the-dashboard"></a><span data-ttu-id="cd4d7-112">대시보드 사용</span><span class="sxs-lookup"><span data-stu-id="cd4d7-112">Using the Dashboard</span></span>

<span data-ttu-id="cd4d7-113">IoT Core를 NXP 디바이스에 플래시 또는 다운로드하려면 다음이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="cd4d7-113">To flash, or download, IoT Core onto your NXP device, you'll need:</span></span>
* <span data-ttu-id="cd4d7-114">Windows 10을 실행하는 컴퓨터</span><span class="sxs-lookup"><span data-stu-id="cd4d7-114">A computer running Windows 10</span></span> 
* [<span data-ttu-id="cd4d7-115">Windows 10 IoT Core 대시보드</span><span class="sxs-lookup"><span data-stu-id="cd4d7-115">Windows 10 IoT Core Dashboard</span></span>](https://docs.microsoft.com/windows/iot-core/downloads)
* <span data-ttu-id="cd4d7-116">SanDisk SD 카드와 같은 고성능 SD 카드</span><span class="sxs-lookup"><span data-stu-id="cd4d7-116">A high-performance SD card, such as a SanDisk SD card</span></span>
* <span data-ttu-id="cd4d7-117">외부 디스플레이</span><span class="sxs-lookup"><span data-stu-id="cd4d7-117">An external display</span></span>
* <span data-ttu-id="cd4d7-118">그 외 주변 기기(예: 마우스, 키보드 등)</span><span class="sxs-lookup"><span data-stu-id="cd4d7-118">Any other peripherals (e.g. mouse, keyboard, etc.)</span></span>

### <a name="instructions"></a><span data-ttu-id="cd4d7-119">지침</span><span class="sxs-lookup"><span data-stu-id="cd4d7-119">Instructions</span></span>

1. <span data-ttu-id="cd4d7-120">Windows 10 IOT Core 대시보드를 실행하고, *새 디바이스 설치*를 클릭하고, 컴퓨터에 SD 카드를 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="cd4d7-120">Run the Windows 10 IOT Core Dashboard and click on *Set up a new device* and insert a SD card into your computer.</span></span>
2. <span data-ttu-id="cd4d7-121">NXP 디바이스를 외부 디스플레이에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="cd4d7-121">Hook up your NXP device to an external display.</span></span>
3. <span data-ttu-id="cd4d7-122">필드를 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="cd4d7-122">Fill out the fields.</span></span> <span data-ttu-id="cd4d7-123">디바이스 유형으로 "NXP [i.MX6/i.MX7]"을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cd4d7-123">Select "NXP [i.MX6/i.MX7]" as the device type.</span></span> <span data-ttu-id="cd4d7-124">디바이스에 새 이름과 암호를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd4d7-124">Make sure to give your device a new name and password.</span></span> <span data-ttu-id="cd4d7-125">그렇지 않으면 기본 자격 증명은 다음과 같이 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd4d7-125">Otherwise the default credentials will remain as:</span></span>

```
Device: minwinpc
Password: p@ssw0rd
```

4. <span data-ttu-id="cd4d7-126">"찾아보기" 함수를 사용하여 미리 다운로드한 이미지 파일을 업로드합니다.</span><span class="sxs-lookup"><span data-stu-id="cd4d7-126">Upload your pre-downloaded image file using the "Browse" function.</span></span> <span data-ttu-id="cd4d7-127">자세한 내용은 [NXP 설명서](https://docs.microsoft.com/windows/iot-core/learn-about-hardware/iotnxp)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cd4d7-127">For more information, see our [NXP documentation](https://docs.microsoft.com/windows/iot-core/learn-about-hardware/iotnxp).</span></span>
5. <span data-ttu-id="cd4d7-128">소프트웨어 사용 조건에 동의하고 *다운로드 및 설치*를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cd4d7-128">Accept the software license terms and click *Download and Install*.</span></span> <span data-ttu-id="cd4d7-129">정상적으로 작동하는 경우 Windows 10 IoT Core가 SD 카드에 플래시되는 것을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd4d7-129">If all goes well, you'll see that Windows 10 IoT Core is now flashing your SD card.</span></span>

![대시보드 스크린샷](../media/DeviceSetup/Dashboard-Screenshot.jpg)


## <a name="connect-to-a-network"></a><span data-ttu-id="cd4d7-131">네트워크에 연결</span><span class="sxs-lookup"><span data-stu-id="cd4d7-131">Connect to a network</span></span>
### <a name="wired-connection"></a><span data-ttu-id="cd4d7-132">유선 연결</span><span class="sxs-lookup"><span data-stu-id="cd4d7-132">Wired connection</span></span>
<span data-ttu-id="cd4d7-133">디바이스에 유선 연결을 지원하는 이더넷 포트 또는 USB 이더넷 어댑터가 있는 경우 이더넷 케이블을 연결하여 네트워크에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="cd4d7-133">If your device comes with an Ethernet port or USB Ethernet adapter support to enable a wired connection, attach an Ethernet cable to connect it to your network.</span></span>

### <a name="wireless-connection"></a><span data-ttu-id="cd4d7-134">무선 연결</span><span class="sxs-lookup"><span data-stu-id="cd4d7-134">Wireless connection</span></span>
<span data-ttu-id="cd4d7-135">디바이스에서 Wi-Fi 연결이 지원되고 디바이스를 디스플레이에 연결한 경우 다음 단계를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd4d7-135">If your device supports Wi-Fi connectivity and you've connected a display to it, you'll need to:</span></span>

1. <span data-ttu-id="cd4d7-136">기본 애플리케이션으로 이동하여 시계 옆에 있는 설정 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cd4d7-136">Go into your default application and click the settings button next to the clock.</span></span>
2. <span data-ttu-id="cd4d7-137">설정 페이지에서 _네트워크 및 Wi-Fi_를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cd4d7-137">On the settings page, select _Network and Wi-Fi_.</span></span>
3. <span data-ttu-id="cd4d7-138">디바이스가 무선 네트워크 검색을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="cd4d7-138">Your device will begin scanning for wireless networks.</span></span>
4. <span data-ttu-id="cd4d7-139">이 목록에 네트워크가 나타나면 네트워크를 선택하고 _연결_을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cd4d7-139">Once your network appears in this list, select it and click _Connect_.</span></span>

<span data-ttu-id="cd4d7-140">디스플레이를 연결하지 않았으며 Wi-Fi를 통해 연결하려는 경우에는 다음 단계를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd4d7-140">If you haven't connected a display and would like to connect via Wi-Fi, you'll need to:</span></span>

1. <span data-ttu-id="cd4d7-141">IoT 대시보드로 이동하여 _내 디바이스_를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cd4d7-141">Go to the IoT Dashboard and click on _My Devices_.</span></span>
2. <span data-ttu-id="cd4d7-142">목록에서 구성되지 않은 보드를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="cd4d7-142">Find your unconfigured board from the list.</span></span> <span data-ttu-id="cd4d7-143">보드 이름은 "AJ_"로 시작합니다(예: AJ_58EA6C68).</span><span class="sxs-lookup"><span data-stu-id="cd4d7-143">Its name will begin with "AJ_"... (e.g. AJ_58EA6C68).</span></span> <span data-ttu-id="cd4d7-144">몇 분이 지나도 보드가 보이지 않으면 보드를 다시 부팅합니다.</span><span class="sxs-lookup"><span data-stu-id="cd4d7-144">If you don't see your board appear after a few minutes, try rebooting your board.</span></span>
3. <span data-ttu-id="cd4d7-145">_디바이스 구성_을 클릭하고 네트워크 자격 증명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="cd4d7-145">Click on _Configure Device_ and enter your network credentials.</span></span> <span data-ttu-id="cd4d7-146">그러면 보드가 네트워크에 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd4d7-146">This will connect your board to the network.</span></span>

> [!NOTE]
> <span data-ttu-id="cd4d7-147">다른 네트워크를 찾으려면 컴퓨터의 Wifi를 켜야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd4d7-147">Wifi on your computer will need to be turned on in order to find other networks.</span></span>

## <a name="connect-to-windows-device-portal"></a><span data-ttu-id="cd4d7-148">Windows 디바이스 포털에 연결</span><span class="sxs-lookup"><span data-stu-id="cd4d7-148">Connect to Windows Device Portal</span></span>

<span data-ttu-id="cd4d7-149">[Windows 디바이스 포털](../manage-your-device/DevicePortal.md)을 사용하여 웹 브라우저를 통해 디바이스를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="cd4d7-149">Use the [Windows Device Portal](../manage-your-device/DevicePortal.md) to connect your device through a web browser.</span></span> <span data-ttu-id="cd4d7-150">디바이스 포털에서는 중요한 구성과 디바이스 관리 기능을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd4d7-150">The device portal makes valuable configuration and device management capabilities available.</span></span> 

