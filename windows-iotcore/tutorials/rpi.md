---
title: Raspberry Pi 설정
ms.author: saclayt
ms.date: 05/22/2019
ms.topic: article
description: Windows 10 IoT Core 사용 하 여 Raspberry Pi를 설정 하는 방법에 알아봅니다.
keywords: Windows 10 IoT Core, Raspberry Pi
ms.custom: RS5
ms.openlocfilehash: 3269aa2ed102b667519baa9212e604083f910783
ms.sourcegitcommit: 8aadc776da7b473159f9023cd555145819e7e952
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66182195"
---
# <a name="setting-up-a-raspberry-pi"></a><span data-ttu-id="3c114-104">Raspberry Pi 설정</span><span class="sxs-lookup"><span data-stu-id="3c114-104">Setting up a Raspberry Pi</span></span>

## <a name="overview"></a><span data-ttu-id="3c114-105">개요</span><span class="sxs-lookup"><span data-stu-id="3c114-105">Overview</span></span>

> [!NOTE]
> <span data-ttu-id="3c114-106">대시보드는 Raspberry Pi 3B +를 설치 하는 데 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3c114-106">Dashboard cannot be used used to setup the Raspberry Pi 3B+.</span></span> <span data-ttu-id="3c114-107">3B + 장치가 있는 경우 사용 해야 합니다 [3B + 기술 미리 보기](https://www.microsoft.com/en-us/software-download/windowsiot)합니다.</span><span class="sxs-lookup"><span data-stu-id="3c114-107">If you have a 3B+ device, you must use the [3B+ technical preview](https://www.microsoft.com/en-us/software-download/windowsiot).</span></span> <span data-ttu-id="3c114-108">참조 하십시오 합니다 [알려진 제한 사항](https://docs.microsoft.com/en-us/windows/iot-core/troubleshooting) 이 개발에 적합 한지 여부를 확인 하려면 기술 미리 보기.</span><span class="sxs-lookup"><span data-stu-id="3c114-108">Please view the [known limitations](https://docs.microsoft.com/en-us/windows/iot-core/troubleshooting) of the technical preview to determine if this is suitable for your development.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3c114-109">"Format이 디스크" 팝업 최대 나타난 경우 수행 _되지_ 디스크를 포맷 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c114-109">When the "format this disk" pop up comes up, do _not_ format the disk.</span></span> <span data-ttu-id="3c114-110">이 문제에 대 한 수정 노력 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c114-110">We are working on a fix for this issue.</span></span>

<span data-ttu-id="3c114-111">프로토타입 제작 Raspberry Pi를 설정 하는 경우에 Windows 10 IoT Core 대시보드를 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="3c114-111">When setting up a Raspberry Pi for prototyping, we recommend using the Windows 10 IoT Core Dashboard.</span></span> <span data-ttu-id="3c114-112">그러나 Raspberry Pi를 사용 하 여 제조 하려는 경우를 참조 하십시오 합니다 [IoT Core 제조 가이드](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)합니다.</span><span class="sxs-lookup"><span data-stu-id="3c114-112">However, if you're looking to manufacture with a Raspberry Pi, please refer to the [IoT Core Manufacturing Guide](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).</span></span> <span data-ttu-id="3c114-113">제조를 위한 작성자 이미지를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3c114-113">You cannot use maker images for manufacturing.</span></span>
<br>
> [!Video https://www.youtube.com/embed/JPRUbGIyODY]

## <a name="using-the-dashboard"></a><span data-ttu-id="3c114-114">대시보드 사용</span><span class="sxs-lookup"><span data-stu-id="3c114-114">Using the Dashboard</span></span>

<span data-ttu-id="3c114-115">Flash를 또는 Raspberry Pi를 IoT Core를 다운로드 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c114-115">To flash, or download, IoT Core onto your Raspberry Pi, you'll need:</span></span>
* <span data-ttu-id="3c114-116">Windows 10을 실행 하는 컴퓨터</span><span class="sxs-lookup"><span data-stu-id="3c114-116">A computer running Windows 10</span></span> 
* [<span data-ttu-id="3c114-117">Windows 10 IoT Core 대시보드</span><span class="sxs-lookup"><span data-stu-id="3c114-117">Windows 10 IoT Core Dashboard</span></span>](https://docs.microsoft.com/windows/iot-core/downloads)
* <span data-ttu-id="3c114-118">SanDisk SD 카드와 같은 고성능 SD 카드</span><span class="sxs-lookup"><span data-stu-id="3c114-118">A high-performance SD card, such as a SanDisk SD card</span></span>
* <span data-ttu-id="3c114-119">외부 디스플레이</span><span class="sxs-lookup"><span data-stu-id="3c114-119">An external display</span></span>
* <span data-ttu-id="3c114-120">모든 기타 주변 장치 (예: 마우스, 키보드 등)</span><span class="sxs-lookup"><span data-stu-id="3c114-120">Any other peripherals (e.g. mouse, keyboard, etc.)</span></span>

### <a name="instructions"></a><span data-ttu-id="3c114-121">지침</span><span class="sxs-lookup"><span data-stu-id="3c114-121">Instructions</span></span>

1. <span data-ttu-id="3c114-122">Windows 10 IoT Core 대시보드를 실행 하 고 클릭 *새 장치 설정* 컴퓨터에 SD 카드를 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c114-122">Run the Windows 10 IoT Core Dashboard and click on *Set up a new device* and insert a SD card into your computer.</span></span>
2. <span data-ttu-id="3c114-123">Raspberry Pi을 외장 디스플레이 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c114-123">Hook up your Raspberry Pi to an external display.</span></span>
3. <span data-ttu-id="3c114-124">필드를 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="3c114-124">Fill out the fields.</span></span> <span data-ttu-id="3c114-125">장치 유형으로 "목록의 [Raspberry Pi 2 및 3]"를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c114-125">Select "Broadcomm [Raspberry Pi 2 & 3]" as the device type.</span></span> <span data-ttu-id="3c114-126">장치를 새 이름 및 암호를 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c114-126">Make sure to give your device a new name and password.</span></span> <span data-ttu-id="3c114-127">그렇지 않은 경우 기본 자격 증명으로 그대로 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c114-127">Otherwise the default credentials will remain as:</span></span>

```
Device: minwinpc
Password: p@ssw0rd
```

4. <span data-ttu-id="3c114-128">소프트웨어 사용 조건에 동의 하 고 클릭 *다운로드 및 설치*합니다.</span><span class="sxs-lookup"><span data-stu-id="3c114-128">Accept the software license terms and click *Download and Install*.</span></span> <span data-ttu-id="3c114-129">정상적으로 작동 하는 경우에 Windows 10 IoT Core 이제 깜박이 SD 카드에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c114-129">If all goes well, you'll see that Windows 10 IoT Core is now flashing your SD card.</span></span>

![대시보드 스크린샷](../media/DeviceSetup/Dashboard-Screenshot.jpg)

## <a name="connect-to-a-network"></a><span data-ttu-id="3c114-131">네트워크에 연결</span><span class="sxs-lookup"><span data-stu-id="3c114-131">Connect to a network</span></span>
### <a name="wired-connection"></a><span data-ttu-id="3c114-132">유선된으로 연결</span><span class="sxs-lookup"><span data-stu-id="3c114-132">Wired connection</span></span>
<span data-ttu-id="3c114-133">이더넷 포트 또는 유선된 연결을 사용 하려면 USB 이더넷 어댑터에서 지 원하는 장치의 상태가 되 면 네트워크에 연결할 이더넷 케이블을 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c114-133">If your device comes with an Ethernet port or USB Ethernet adapter support to enable a wired connection, attach an Ethernet cable to connect it to your network.</span></span>

### <a name="wireless-connection"></a><span data-ttu-id="3c114-134">무선 연결</span><span class="sxs-lookup"><span data-stu-id="3c114-134">Wireless connection</span></span>
<span data-ttu-id="3c114-135">장치에서 Wi-fi 연결을 지 원하는 경우 디스플레이에 연결 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c114-135">If your device supports Wi-Fi connectivity and you've connected a display to it, you'll need to:</span></span>

1. <span data-ttu-id="3c114-136">기본 응용 프로그램으로 이동한 다음 클록 옆에 있는 설정 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c114-136">Go into your default application and click the settings button next to the clock.</span></span>
2. <span data-ttu-id="3c114-137">설정 페이지에서 선택 _네트워크 및 Wi-fi_합니다.</span><span class="sxs-lookup"><span data-stu-id="3c114-137">On the settings page, select _Network and Wi-Fi_.</span></span>
3. <span data-ttu-id="3c114-138">장치의 무선 네트워크에 대 한 검색을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c114-138">Your device will begin scanning for wireless networks.</span></span>
4. <span data-ttu-id="3c114-139">이 목록에 표시 되는 네트워크를 선택 하 고 클릭 _Connect_합니다.</span><span class="sxs-lookup"><span data-stu-id="3c114-139">Once your network appears in this list, select it and click _Connect_.</span></span>

<span data-ttu-id="3c114-140">디스플레이 연결 하지 않은 하 고 Wi-fi를 통해 연결 하려는 경우을 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c114-140">If you haven't connected a display and would like to connect via Wi-Fi, you'll need to:</span></span>

1. <span data-ttu-id="3c114-141">IoT 대시보드로 이동 하 고 클릭 _내 장치_합니다.</span><span class="sxs-lookup"><span data-stu-id="3c114-141">Go to the IoT Dashboard and click on _My Devices_.</span></span>
2. <span data-ttu-id="3c114-142">목록에서 구성 되지 않은 보드를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="3c114-142">Find your unconfigured board from the list.</span></span> <span data-ttu-id="3c114-143">이름과 "AJ_"로 시작 됩니다... (예:: AJ_58EA6C68)입니다.</span><span class="sxs-lookup"><span data-stu-id="3c114-143">Its name will begin with "AJ_"... (e.g. AJ_58EA6C68).</span></span> <span data-ttu-id="3c114-144">몇 분 정도 지나면 보드 표시 되지 않는 경우 보드를 다시 부팅 하십시오.</span><span class="sxs-lookup"><span data-stu-id="3c114-144">If you don't see your board appear after a few minutes, try rebooting your board.</span></span>
3. <span data-ttu-id="3c114-145">클릭할 _장치 구성_ 네트워크 자격 증명을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c114-145">Click on _Configure Device_ and enter your network credentials.</span></span> <span data-ttu-id="3c114-146">그러면 네트워크에 보드를 연결 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c114-146">This will connect your board to the network.</span></span>

> [!NOTE]
> <span data-ttu-id="3c114-147">Wifi를 컴퓨터에 다른 네트워크를 찾을 수 있도록 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c114-147">Wifi on your computer will need to be turned on in order to find other networks.</span></span>

## <a name="connect-to-windows-device-portal"></a><span data-ttu-id="3c114-148">Windows Device Portal 연결</span><span class="sxs-lookup"><span data-stu-id="3c114-148">Connect to Windows Device Portal</span></span>

<span data-ttu-id="3c114-149">사용 합니다 [Windows Device Portal](../manage-your-device/DevicePortal.md) 웹 브라우저를 통해 장치를 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c114-149">Use the [Windows Device Portal](../manage-your-device/DevicePortal.md) to connect your device through a web browser.</span></span> <span data-ttu-id="3c114-150">장치 포털 중요 한 구성 및 장치 관리 기능을 사용할 수 있게 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c114-150">The device portal makes valuable configuration and device management capabilities available.</span></span> 
