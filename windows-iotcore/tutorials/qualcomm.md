---
title: Qualcomm 디바이스 설정
ms.date: 05/22/2019
ms.topic: article
description: Windows 10 IoT Core를 사용하여 Qualcomm 디바이스를 설정하는 방법을 알아봅니다.
keywords: Windows 10 IoT Core, Qualcomm
ms.custom: RS5
ms.openlocfilehash: 9c27f6011503ea557687817bc044b08695ee7add
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918642"
---
# <a name="setting-up-a-qualcomm-device"></a><span data-ttu-id="cdbfd-104">Qualcomm 디바이스 설정</span><span class="sxs-lookup"><span data-stu-id="cdbfd-104">Setting up a Qualcomm device</span></span>

<span data-ttu-id="cdbfd-105">Qualcomm 디바이스로 제작하려는 경우에는 [IoT Core 제작 가이드](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cdbfd-105">If you're looking to manufacture with a Qualcomm device, please refer to the [IoT Core Manufacturing Guide](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).</span></span> <span data-ttu-id="cdbfd-106">제조사 이미지는 제작에 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="cdbfd-106">You cannot use maker images for manufacturing.</span></span>

> [!NOTE]
> <span data-ttu-id="cdbfd-107">BIOS 설정을 다시 입력하고, USB 드라이브 대신 하드 드라이브에서 로드하도록 부팅 드라이브 순서를 전환하여 디바이스가 eMMC 메모리에서 부팅되도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="cdbfd-107">Make sure the device is now booting from the eMMC memory by entering the BIOS setup again and switching the Boot Drive order to load from the Hard Drive instead of from the USB Drive.</span></span>

## <a name="using-emmc"></a><span data-ttu-id="cdbfd-108">eMMC 사용</span><span class="sxs-lookup"><span data-stu-id="cdbfd-108">Using eMMC</span></span>

1. <span data-ttu-id="cdbfd-109">[x86](https://developer.qualcomm.com/download/db410c/windows-10-iot-update-tool-dragonboard-410c-x86.zip) 또는 [x64](https://developer.qualcomm.com/download/db410c/windows-10-iot-update-tool-dragonboard-410c-x64.zip) 머신에 맞는 DragonBoard 업데이트 도구를 다운로드하여 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="cdbfd-109">Download and install the DragonBoard Update Tool for your [x86](https://developer.qualcomm.com/download/db410c/windows-10-iot-update-tool-dragonboard-410c-x86.zip) or [x64](https://developer.qualcomm.com/download/db410c/windows-10-iot-update-tool-dragonboard-410c-x64.zip) machine.</span></span>
2. <span data-ttu-id="cdbfd-110">[Windows 10 IoT Core DragonBoard FFU](https://docs.microsoft.com/en-us/windows/iot-core/downloads)를 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="cdbfd-110">Download the [Windows 10 IoT Core DragonBoard FFU](https://docs.microsoft.com/en-us/windows/iot-core/downloads).</span></span>
3. <span data-ttu-id="cdbfd-111">다운로드한 ISO 파일을 두 번 클릭하고 탑재된 가상 CD 드라이브를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="cdbfd-111">Double-click on the downloaded ISO file and locate the mounted Virtual CD-drive.</span></span> <span data-ttu-id="cdbfd-112">이 드라이브에 설치 관리자 파일(.msi)이 포함되어 있습니다. 이 파일을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cdbfd-112">This drive will contain an installer file (.msi); double-click on it.</span></span> <span data-ttu-id="cdbfd-113">그러면 PC의  `C:\Program Files (x86)\Microsoft IoT\FFU\` 아래에 새 디렉터리가 생성되고 "flash.ffu" 이미지 파일이 보입니다.</span><span class="sxs-lookup"><span data-stu-id="cdbfd-113">This creates a new directory on your PC under `C:\Program Files (x86)\Microsoft IoT\FFU\` in which you should see an image file, "flash.ffu".</span></span>
4. <span data-ttu-id="cdbfd-114">아래와 같이 보드의 첫 번째 스위치를 USB 부팅으로 설정하여 DragonBoard를 다운로드 모드로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="cdbfd-114">Ensure your DragonBoard is in download mode by setting the first boot switch on the board to USB Boot, as shown below.</span></span> <span data-ttu-id="cdbfd-115">그런 다음, microUSB 케이블을 통해 DragonBoard를 호스트 PC에 연결하고, DragonBoard를 12V(>1A) 전원 공급 장치에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="cdbfd-115">Then, connect the DragonBoard to the host PC via a microUSB cable, then plug in the DragonBoard to a 12V (> 1A) power supply.</span></span>
5. <span data-ttu-id="cdbfd-116">녹색 원을 사용하여 DragonBoard가 PC에 연결되어 있는지 탐지하는 DragonBoard 업데이트 도구를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="cdbfd-116">Start the DragonBoard Update Tool, which should detect that the DragonBoard is connect to your PC with a green circle.</span></span> <span data-ttu-id="cdbfd-117">다운로드한 DragonBoard의 FFU를 찾은 다음, _프로그램_ 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cdbfd-117">"Browse" to the DragonBoard's FFU that you downloaded, then click the _Program_ button.</span></span>
6. <span data-ttu-id="cdbfd-118">"찾아보기"를 다시 클릭하고 5단계에서 생성된 "rawprogram0.xml"을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cdbfd-118">Click "Browse" again and select "rawprogram0.xml" that was generated in step 5.</span></span> <span data-ttu-id="cdbfd-119">그런 다음, "프로그램" 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cdbfd-119">Then click the "Program" button.</span></span>
7. <span data-ttu-id="cdbfd-120">다운로드가 완료되면 보드에서 전원 공급 장치와 microUSB 케이블을 분리하고 USB 부팅 스위치를 다시 _OFF_로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="cdbfd-120">Once the download is complete, disconnect the power supply and microUSB cable from the board and toggle the USB Boot switch back to _OFF_.</span></span> <span data-ttu-id="cdbfd-121">HDMI 디스플레이, 마우스 및 키보드를 DragonBoard에 연결하고 전원 공급 장치를 다시 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="cdbfd-121">Connect a HDMI display, a mouse, and a keyboard to the DragonBoard and reconnect the power supply.</span></span> <span data-ttu-id="cdbfd-122">몇 분 후 Windows 10 IoT Core 기본 애플리케이션이 보입니다.</span><span class="sxs-lookup"><span data-stu-id="cdbfd-122">After a few minutes, you should see the Windows 10 IoT Core default application.</span></span> 

![다운로드 모드인 DragonBoard](../media/DeviceSetup/db1.png)

## <a name="connect-to-a-network"></a><span data-ttu-id="cdbfd-124">네트워크에 연결</span><span class="sxs-lookup"><span data-stu-id="cdbfd-124">Connect to a network</span></span>

### <a name="wired-connection"></a><span data-ttu-id="cdbfd-125">유선 연결</span><span class="sxs-lookup"><span data-stu-id="cdbfd-125">Wired connection</span></span>
<span data-ttu-id="cdbfd-126">디바이스에 유선 연결을 지원하는 이더넷 포트 또는 USB 이더넷 어댑터가 있는 경우 이더넷 케이블을 연결하여 네트워크에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="cdbfd-126">If your device comes with an Ethernet port or USB Ethernet adapter support to enable a wired connection, attach an Ethernet cable to connect it to your network.</span></span>

### <a name="wireless-connection"></a><span data-ttu-id="cdbfd-127">무선 연결</span><span class="sxs-lookup"><span data-stu-id="cdbfd-127">Wireless connection</span></span>
<span data-ttu-id="cdbfd-128">디바이스에서 Wi-Fi 연결이 지원되고 디바이스를 디스플레이에 연결한 경우 다음 단계를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cdbfd-128">If your device supports Wi-Fi connectivity and you've connected a display to it, you'll need to:</span></span>

1. <span data-ttu-id="cdbfd-129">기본 애플리케이션으로 이동하여 시계 옆에 있는 설정 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cdbfd-129">Go into your default application and click the settings button next to the clock.</span></span>
2. <span data-ttu-id="cdbfd-130">설정 페이지에서 _네트워크 및 Wi-Fi_를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cdbfd-130">On the settings page, select _Network and Wi-Fi_.</span></span>
3. <span data-ttu-id="cdbfd-131">디바이스가 무선 네트워크 검색을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="cdbfd-131">Your device will begin scanning for wireless networks.</span></span>
4. <span data-ttu-id="cdbfd-132">이 목록에 네트워크가 나타나면 네트워크를 선택하고 _연결_을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cdbfd-132">Once your network appears in this list, select it and click _Connect_.</span></span>

<span data-ttu-id="cdbfd-133">디스플레이를 연결하지 않았으며 Wi-Fi를 통해 연결하려는 경우에는 다음 단계를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cdbfd-133">If you haven't connected a display and would like to connect via Wi-Fi, you'll need to:</span></span>

1. <span data-ttu-id="cdbfd-134">IoT 대시보드로 이동하여 _내 디바이스_를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cdbfd-134">Go to the IoT Dashboard and click on _My Devices_.</span></span>
2. <span data-ttu-id="cdbfd-135">목록에서 구성되지 않은 보드를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="cdbfd-135">Find your unconfigured board from the list.</span></span> <span data-ttu-id="cdbfd-136">보드 이름은 "AJ_"로 시작합니다(예: AJ_58EA6C68).</span><span class="sxs-lookup"><span data-stu-id="cdbfd-136">Its name will begin with "AJ_"... (e.g. AJ_58EA6C68).</span></span> <span data-ttu-id="cdbfd-137">몇 분이 지나도 보드가 보이지 않으면 보드를 다시 부팅합니다.</span><span class="sxs-lookup"><span data-stu-id="cdbfd-137">If you don't see your board appear after a few minutes, try rebooting your board.</span></span>
3. <span data-ttu-id="cdbfd-138">_디바이스 구성_을 클릭하고 네트워크 자격 증명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="cdbfd-138">Click on _Configure Device_ and enter your network credentials.</span></span> <span data-ttu-id="cdbfd-139">그러면 보드가 네트워크에 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="cdbfd-139">This will connect your board to the network.</span></span>

> [!NOTE]
> <span data-ttu-id="cdbfd-140">다른 네트워크를 찾으려면 컴퓨터의 Wifi를 켜야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cdbfd-140">Wifi on your computer will need to be turned on in order to find other networks.</span></span>

## <a name="connect-to-windows-device-portal"></a><span data-ttu-id="cdbfd-141">Windows 디바이스 포털에 연결</span><span class="sxs-lookup"><span data-stu-id="cdbfd-141">Connect to Windows Device Portal</span></span>

<span data-ttu-id="cdbfd-142">[Windows 디바이스 포털](../manage-your-device/DevicePortal.md)을 사용하여 웹 브라우저를 통해 디바이스를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="cdbfd-142">Use the [Windows Device Portal](../manage-your-device/DevicePortal.md) to connect your device through a web browser.</span></span> <span data-ttu-id="cdbfd-143">디바이스 포털에서는 중요한 구성과 디바이스 관리 기능을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cdbfd-143">The device portal makes valuable configuration and device management capabilities available.</span></span> 



