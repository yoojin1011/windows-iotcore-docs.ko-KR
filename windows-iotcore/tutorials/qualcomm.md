---
title: Qualcomm 장치 설정
ms.author: saclayt
ms.date: 05/22/2019
ms.topic: article
description: Windows 10 IoT Core 사용 하 여 Qualcomm 장치를 설정 하는 방법에 알아봅니다.
keywords: Windows 10 IoT Core, Qualcomm
ms.custom: RS5
ms.openlocfilehash: 02f6c013c428a271d3b3956c88edc1ce8f4fdbf2
ms.sourcegitcommit: fa4a29fcd5af464924a0a5ab581f08f631a3ad72
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66835608"
---
# <a name="setting-up-a-qualcomm-device"></a><span data-ttu-id="7e6fc-104">Qualcomm 장치 설정</span><span class="sxs-lookup"><span data-stu-id="7e6fc-104">Setting up a Qualcomm device</span></span>

<span data-ttu-id="7e6fc-105">Qualcomm 장치를 사용 하 여 제조 하려는 경우 참조 하는 [IoT Core 제조 가이드](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)합니다.</span><span class="sxs-lookup"><span data-stu-id="7e6fc-105">If you're looking to manufacture with a Qualcomm device, please refer to the [IoT Core Manufacturing Guide](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).</span></span> <span data-ttu-id="7e6fc-106">제조를 위한 작성자 이미지를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7e6fc-106">You cannot use maker images for manufacturing.</span></span>

> [!NOTE]
> <span data-ttu-id="7e6fc-107">BIOS 설정을 다시 입력 하 고 대신 USB 드라이브에서 하드 드라이브에서 로드 하는 부팅 드라이브 순서를 전환 하 여 eMMC 메모리에서 장치는 이제 부팅 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e6fc-107">Make sure the device is now booting from the eMMC memory by entering the BIOS setup again and switching the Boot Drive order to load from the Hard Drive instead of from the USB Drive.</span></span>

## <a name="using-emmc"></a><span data-ttu-id="7e6fc-108">EMMC를 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="7e6fc-108">Using eMMC</span></span>

1. <span data-ttu-id="7e6fc-109">에 대 한 DragonBoard 업데이트 도구 다운로드 및 설치 프로그램 [x86](https://developer.qualcomm.com/download/db410c/windows-10-iot-update-tool-dragonboard-410c-x86.zip) 하거나 [x64](https://developer.qualcomm.com/download/db410c/windows-10-iot-update-tool-dragonboard-410c-x64.zip) 컴퓨터.</span><span class="sxs-lookup"><span data-stu-id="7e6fc-109">Download and install the DragonBoard Update Tool for your [x86](https://developer.qualcomm.com/download/db410c/windows-10-iot-update-tool-dragonboard-410c-x86.zip) or [x64](https://developer.qualcomm.com/download/db410c/windows-10-iot-update-tool-dragonboard-410c-x64.zip) machine.</span></span>
2. <span data-ttu-id="7e6fc-110">다운로드 합니다 [Windows 10 IoT Core DragonBoard FFU](https://docs.microsoft.com/en-us/windows/iot-core/downloads)합니다.</span><span class="sxs-lookup"><span data-stu-id="7e6fc-110">Download the [Windows 10 IoT Core DragonBoard FFU](https://docs.microsoft.com/en-us/windows/iot-core/downloads).</span></span>
3. <span data-ttu-id="7e6fc-111">다운로드 한 ISO 파일을 두 번 누릅니다 하 고 탑재 된 가상 CD 드라이브를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="7e6fc-111">Double-click on the downloaded ISO file and locate the mounted Virtual CD-drive.</span></span> <span data-ttu-id="7e6fc-112">이 드라이브는 설치 관리자 파일 (.msi);에 포함 됩니다. 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e6fc-112">This drive will contain an installer file (.msi); double-click on it.</span></span> <span data-ttu-id="7e6fc-113">새 디렉터리 아래에 있는 PC에 이렇게 `C:\Program Files (x86)\Microsoft IoT\FFU\` 에서 표시 하는 이미지 파일을 "flash.ffu"입니다.</span><span class="sxs-lookup"><span data-stu-id="7e6fc-113">This creates a new directory on your PC under `C:\Program Files (x86)\Microsoft IoT\FFU\` in which you should see an image file, "flash.ffu".</span></span>
4. <span data-ttu-id="7e6fc-114">아래와 같이 프로그램 DragonBoard가 다운로드 모드를 첫 번째 부팅 전환할 보드의 USB 부팅 설정 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e6fc-114">Ensure your DragonBoard is in download mode by setting the first boot switch on the board to USB Boot, as shown below.</span></span> <span data-ttu-id="7e6fc-115">그런 다음는 DragonBoard microUSB 케이블을 통해 호스트 PC에 연결 합니다. 다음에 12V DragonBoard 플러그 인 (> 1A) 전원 공급 장치.</span><span class="sxs-lookup"><span data-stu-id="7e6fc-115">Then, connect the DragonBoard to the host PC via a microUSB cable, then plug in the DragonBoard to a 12V (> 1A) power supply.</span></span>
5. <span data-ttu-id="7e6fc-116">DragonBoard 녹색 원을 사용 하 여 사용자 PC에 연결 되어 있는지 검색 해야 하는 DragonBoard 업데이트 도구를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e6fc-116">Start the DragonBoard Update Tool, which should detect that the DragonBoard is connect to your PC with a green circle.</span></span> <span data-ttu-id="7e6fc-117">"찾아보기" DragonBoard의를 다운로드 한 FFU 클릭 합니다 _프로그램_ 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="7e6fc-117">"Browse" to the DragonBoard's FFU that you downloaded, then click the _Program_ button.</span></span>
6. <span data-ttu-id="7e6fc-118">"찾아보기"를 다시 클릭 하 고 5 단계에서 생성 된 "rawprogram0.xml"를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e6fc-118">Click "Browse" again and select "rawprogram0.xml" that was generated in step 5.</span></span> <span data-ttu-id="7e6fc-119">"프로그램" 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e6fc-119">Then click the "Program" button.</span></span>
7. <span data-ttu-id="7e6fc-120">다운로드가 완료 되 면 전원 공급 장치 및 microUSB 케이블 다시 USB 부팅 스위치 보드 및 설정/해제에서 연결 끊기 _OFF_합니다.</span><span class="sxs-lookup"><span data-stu-id="7e6fc-120">Once the download is complete, disconnect the power supply and microUSB cable from the board and toggle the USB Boot switch back to _OFF_.</span></span> <span data-ttu-id="7e6fc-121">HDMI 디스플레이, 마우스 및 키보드를 DragonBoard 연결한 전원 공급 장치를 다시 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e6fc-121">Connect a HDMI display, a mouse, and a keyboard to the DragonBoard and reconnect the power supply.</span></span> <span data-ttu-id="7e6fc-122">몇 분 후 Windows 10 IoT Core 기본 응용 프로그램이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7e6fc-122">After a few minutes, you should see the Windows 10 IoT Core default application.</span></span> 

![DragonBoard 다운로드 모드](../media/DeviceSetup/db1.png)

## <a name="connect-to-a-network"></a><span data-ttu-id="7e6fc-124">네트워크에 연결</span><span class="sxs-lookup"><span data-stu-id="7e6fc-124">Connect to a network</span></span>

### <a name="wired-connection"></a><span data-ttu-id="7e6fc-125">유선된으로 연결</span><span class="sxs-lookup"><span data-stu-id="7e6fc-125">Wired connection</span></span>
<span data-ttu-id="7e6fc-126">이더넷 포트 또는 유선된 연결을 사용 하려면 USB 이더넷 어댑터에서 지 원하는 장치의 상태가 되 면 네트워크에 연결할 이더넷 케이블을 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e6fc-126">If your device comes with an Ethernet port or USB Ethernet adapter support to enable a wired connection, attach an Ethernet cable to connect it to your network.</span></span>

### <a name="wireless-connection"></a><span data-ttu-id="7e6fc-127">무선 연결</span><span class="sxs-lookup"><span data-stu-id="7e6fc-127">Wireless connection</span></span>
<span data-ttu-id="7e6fc-128">장치에서 Wi-fi 연결을 지 원하는 경우 디스플레이에 연결 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e6fc-128">If your device supports Wi-Fi connectivity and you've connected a display to it, you'll need to:</span></span>

1. <span data-ttu-id="7e6fc-129">기본 응용 프로그램으로 이동한 다음 클록 옆에 있는 설정 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e6fc-129">Go into your default application and click the settings button next to the clock.</span></span>
2. <span data-ttu-id="7e6fc-130">설정 페이지에서 선택 _네트워크 및 Wi-fi_합니다.</span><span class="sxs-lookup"><span data-stu-id="7e6fc-130">On the settings page, select _Network and Wi-Fi_.</span></span>
3. <span data-ttu-id="7e6fc-131">장치의 무선 네트워크에 대 한 검색을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e6fc-131">Your device will begin scanning for wireless networks.</span></span>
4. <span data-ttu-id="7e6fc-132">이 목록에 표시 되는 네트워크를 선택 하 고 클릭 _Connect_합니다.</span><span class="sxs-lookup"><span data-stu-id="7e6fc-132">Once your network appears in this list, select it and click _Connect_.</span></span>

<span data-ttu-id="7e6fc-133">디스플레이 연결 하지 않은 하 고 Wi-fi를 통해 연결 하려는 경우을 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e6fc-133">If you haven't connected a display and would like to connect via Wi-Fi, you'll need to:</span></span>

1. <span data-ttu-id="7e6fc-134">IoT 대시보드로 이동 하 고 클릭 _내 장치_합니다.</span><span class="sxs-lookup"><span data-stu-id="7e6fc-134">Go to the IoT Dashboard and click on _My Devices_.</span></span>
2. <span data-ttu-id="7e6fc-135">목록에서 구성 되지 않은 보드를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="7e6fc-135">Find your unconfigured board from the list.</span></span> <span data-ttu-id="7e6fc-136">이름과 "AJ_"로 시작 됩니다... (예:: AJ_58EA6C68)입니다.</span><span class="sxs-lookup"><span data-stu-id="7e6fc-136">Its name will begin with "AJ_"... (e.g. AJ_58EA6C68).</span></span> <span data-ttu-id="7e6fc-137">몇 분 정도 지나면 보드 표시 되지 않는 경우 보드를 다시 부팅 하십시오.</span><span class="sxs-lookup"><span data-stu-id="7e6fc-137">If you don't see your board appear after a few minutes, try rebooting your board.</span></span>
3. <span data-ttu-id="7e6fc-138">클릭할 _장치 구성_ 네트워크 자격 증명을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e6fc-138">Click on _Configure Device_ and enter your network credentials.</span></span> <span data-ttu-id="7e6fc-139">그러면 네트워크에 보드를 연결 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7e6fc-139">This will connect your board to the network.</span></span>

> [!NOTE]
> <span data-ttu-id="7e6fc-140">Wifi를 컴퓨터에 다른 네트워크를 찾을 수 있도록 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e6fc-140">Wifi on your computer will need to be turned on in order to find other networks.</span></span>

## <a name="connect-to-windows-device-portal"></a><span data-ttu-id="7e6fc-141">Windows Device Portal 연결</span><span class="sxs-lookup"><span data-stu-id="7e6fc-141">Connect to Windows Device Portal</span></span>

<span data-ttu-id="7e6fc-142">사용 합니다 [Windows Device Portal](../manage-your-device/DevicePortal.md) 웹 브라우저를 통해 장치를 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e6fc-142">Use the [Windows Device Portal](../manage-your-device/DevicePortal.md) to connect your device through a web browser.</span></span> <span data-ttu-id="7e6fc-143">장치 포털 중요 한 구성 및 장치 관리 기능을 사용할 수 있게 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e6fc-143">The device portal makes valuable configuration and device management capabilities available.</span></span> 



