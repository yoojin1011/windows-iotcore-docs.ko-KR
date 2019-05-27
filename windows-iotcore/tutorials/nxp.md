---
title: NXP 장치 설정
ms.author: saclayt
ms.date: 05/22/2019
ms.topic: article
description: Windows 10 IoT Core 사용 하 여 NXP 장치를 설정 하는 방법에 알아봅니다.
keywords: Windows 10 IoT Core, NXP
ms.custom: RS5
ms.openlocfilehash: 58bed6c49a5a05afe0852572051132f8731dfcb1
ms.sourcegitcommit: 8aadc776da7b473159f9023cd555145819e7e952
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66182175"
---
# <a name="setting-up-a-nxp-device"></a><span data-ttu-id="813a7-104">NXP 장치 설정</span><span class="sxs-lookup"><span data-stu-id="813a7-104">Setting up a NXP device</span></span>

## <a name="overview"></a><span data-ttu-id="813a7-105">개요</span><span class="sxs-lookup"><span data-stu-id="813a7-105">Overview</span></span>

> [!IMPORTANT]
> <span data-ttu-id="813a7-106">"Format이 디스크" 팝업 최대 나타난 경우 수행 _되지_ 디스크를 포맷 합니다.</span><span class="sxs-lookup"><span data-stu-id="813a7-106">When the "format this disk" pop up comes up, do _not_ format the disk.</span></span> <span data-ttu-id="813a7-107">이 문제에 대 한 수정 노력 합니다.</span><span class="sxs-lookup"><span data-stu-id="813a7-107">We are working on a fix for this issue.</span></span>

<span data-ttu-id="813a7-108">프로토타입 제작 NXP 장치를 설정 하는 경우에 Windows 10 IoT Core 대시보드를 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="813a7-108">When setting up a NXP device for prototyping, we recommend using the Windows 10 IoT Core Dashboard.</span></span> <span data-ttu-id="813a7-109">그러나 NXP 장치를 사용 하 여 제조 하려는 경우를 참조 하십시오 합니다 [IoT Core 제조 가이드](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)합니다.</span><span class="sxs-lookup"><span data-stu-id="813a7-109">However, if you're looking to manufacture with a NXP device, please refer to the [IoT Core Manufacturing Guide](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).</span></span> <span data-ttu-id="813a7-110">제조를 위한 작성자 이미지를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="813a7-110">You cannot use maker images for manufacturing.</span></span>
<br>
> [!Video https://www.youtube.com/embed/JPRUbGIyODY]

## <a name="using-the-dashboard"></a><span data-ttu-id="813a7-111">대시보드 사용</span><span class="sxs-lookup"><span data-stu-id="813a7-111">Using the Dashboard</span></span>

<span data-ttu-id="813a7-112">Flash를 또는 NXP 장치에 IoT Core를 다운로드 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="813a7-112">To flash, or download, IoT Core onto your NXP device, you'll need:</span></span>
* <span data-ttu-id="813a7-113">Windows 10을 실행 하는 컴퓨터</span><span class="sxs-lookup"><span data-stu-id="813a7-113">A computer running Windows 10</span></span> 
* [<span data-ttu-id="813a7-114">Windows 10 IoT Core 대시보드</span><span class="sxs-lookup"><span data-stu-id="813a7-114">Windows 10 IoT Core Dashboard</span></span>](https://docs.microsoft.com/windows/iot-core/downloads)
* <span data-ttu-id="813a7-115">SanDisk SD 카드와 같은 고성능 SD 카드</span><span class="sxs-lookup"><span data-stu-id="813a7-115">A high-performance SD card, such as a SanDisk SD card</span></span>
* <span data-ttu-id="813a7-116">외부 디스플레이</span><span class="sxs-lookup"><span data-stu-id="813a7-116">An external display</span></span>
* <span data-ttu-id="813a7-117">모든 기타 주변 장치 (예: 마우스, 키보드 등)</span><span class="sxs-lookup"><span data-stu-id="813a7-117">Any other peripherals (e.g. mouse, keyboard, etc.)</span></span>

### <a name="instructions"></a><span data-ttu-id="813a7-118">지침</span><span class="sxs-lookup"><span data-stu-id="813a7-118">Instructions</span></span>

1. <span data-ttu-id="813a7-119">Windows 10 IOT Core 대시보드를 실행 하 고 클릭 *새 장치 설정* 컴퓨터에 SD 카드를 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="813a7-119">Run the Windows 10 IOT Core Dashboard and click on *Set up a new device* and insert a SD card into your computer.</span></span>
2. <span data-ttu-id="813a7-120">외장 디스플레이 NXP 장치에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="813a7-120">Hook up your NXP device to an external display.</span></span>
3. <span data-ttu-id="813a7-121">필드를 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="813a7-121">Fill out the fields.</span></span> <span data-ttu-id="813a7-122">장치 유형으로 "NXP [i.MX6/i.MX7]"를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="813a7-122">Select "NXP [i.MX6/i.MX7]" as the device type.</span></span> <span data-ttu-id="813a7-123">장치를 새 이름 및 암호를 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="813a7-123">Make sure to give your device a new name and password.</span></span> <span data-ttu-id="813a7-124">그렇지 않은 경우 기본 자격 증명으로 그대로 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="813a7-124">Otherwise the default credentials will remain as:</span></span>

```
Device: minwinpc
Password: p@ssw0rd
```

4. <span data-ttu-id="813a7-125">"찾아보기" 함수를 사용 하 여 미리 다운로드 한 이미지 파일을 업로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="813a7-125">Upload your pre-downloaded image file using the "Browse" function.</span></span> <span data-ttu-id="813a7-126">자세한 내용은 참조 하세요. 당사의 [NXP 설명서](https://docs.microsoft.com/en-us/windows/iot-core/learn-about-hardware/iotnxp)합니다.</span><span class="sxs-lookup"><span data-stu-id="813a7-126">For more information, see our [NXP documentation](https://docs.microsoft.com/en-us/windows/iot-core/learn-about-hardware/iotnxp).</span></span>
5. <span data-ttu-id="813a7-127">소프트웨어 사용 조건에 동의 하 고 클릭 *다운로드 및 설치*합니다.</span><span class="sxs-lookup"><span data-stu-id="813a7-127">Accept the software license terms and click *Download and Install*.</span></span> <span data-ttu-id="813a7-128">정상적으로 작동 하는 경우에 Windows 10 IoT Core 이제 깜박이 SD 카드에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="813a7-128">If all goes well, you'll see that Windows 10 IoT Core is now flashing your SD card.</span></span>

![대시보드 스크린샷](../media/DeviceSetup/Dashboard-Screenshot.jpg)


## <a name="connect-to-a-network"></a><span data-ttu-id="813a7-130">네트워크에 연결</span><span class="sxs-lookup"><span data-stu-id="813a7-130">Connect to a network</span></span>
### <a name="wired-connection"></a><span data-ttu-id="813a7-131">유선된으로 연결</span><span class="sxs-lookup"><span data-stu-id="813a7-131">Wired connection</span></span>
<span data-ttu-id="813a7-132">이더넷 포트 또는 유선된 연결을 사용 하려면 USB 이더넷 어댑터에서 지 원하는 장치의 상태가 되 면 네트워크에 연결할 이더넷 케이블을 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="813a7-132">If your device comes with an Ethernet port or USB Ethernet adapter support to enable a wired connection, attach an Ethernet cable to connect it to your network.</span></span>

### <a name="wireless-connection"></a><span data-ttu-id="813a7-133">무선 연결</span><span class="sxs-lookup"><span data-stu-id="813a7-133">Wireless connection</span></span>
<span data-ttu-id="813a7-134">장치에서 Wi-fi 연결을 지 원하는 경우 디스플레이에 연결 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="813a7-134">If your device supports Wi-Fi connectivity and you've connected a display to it, you'll need to:</span></span>

1. <span data-ttu-id="813a7-135">기본 응용 프로그램으로 이동한 다음 클록 옆에 있는 설정 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="813a7-135">Go into your default application and click the settings button next to the clock.</span></span>
2. <span data-ttu-id="813a7-136">설정 페이지에서 선택 _네트워크 및 Wi-fi_합니다.</span><span class="sxs-lookup"><span data-stu-id="813a7-136">On the settings page, select _Network and Wi-Fi_.</span></span>
3. <span data-ttu-id="813a7-137">장치의 무선 네트워크에 대 한 검색을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="813a7-137">Your device will begin scanning for wireless networks.</span></span>
4. <span data-ttu-id="813a7-138">이 목록에 표시 되는 네트워크를 선택 하 고 클릭 _Connect_합니다.</span><span class="sxs-lookup"><span data-stu-id="813a7-138">Once your network appears in this list, select it and click _Connect_.</span></span>

<span data-ttu-id="813a7-139">디스플레이 연결 하지 않은 하 고 Wi-fi를 통해 연결 하려는 경우을 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="813a7-139">If you haven't connected a display and would like to connect via Wi-Fi, you'll need to:</span></span>

1. <span data-ttu-id="813a7-140">IoT 대시보드로 이동 하 고 클릭 _내 장치_합니다.</span><span class="sxs-lookup"><span data-stu-id="813a7-140">Go to the IoT Dashboard and click on _My Devices_.</span></span>
2. <span data-ttu-id="813a7-141">목록에서 구성 되지 않은 보드를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="813a7-141">Find your unconfigured board from the list.</span></span> <span data-ttu-id="813a7-142">이름과 "AJ_"로 시작 됩니다... (예:: AJ_58EA6C68)입니다.</span><span class="sxs-lookup"><span data-stu-id="813a7-142">Its name will begin with "AJ_"... (e.g. AJ_58EA6C68).</span></span> <span data-ttu-id="813a7-143">몇 분 정도 지나면 보드 표시 되지 않는 경우 보드를 다시 부팅 하십시오.</span><span class="sxs-lookup"><span data-stu-id="813a7-143">If you don't see your board appear after a few minutes, try rebooting your board.</span></span>
3. <span data-ttu-id="813a7-144">클릭할 _장치 구성_ 네트워크 자격 증명을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="813a7-144">Click on _Configure Device_ and enter your network credentials.</span></span> <span data-ttu-id="813a7-145">그러면 네트워크에 보드를 연결 됩니다.</span><span class="sxs-lookup"><span data-stu-id="813a7-145">This will connect your board to the network.</span></span>

> [!NOTE]
> <span data-ttu-id="813a7-146">Wifi를 컴퓨터에 다른 네트워크를 찾을 수 있도록 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="813a7-146">Wifi on your computer will need to be turned on in order to find other networks.</span></span>

## <a name="connect-to-windows-device-portal"></a><span data-ttu-id="813a7-147">Windows Device Portal 연결</span><span class="sxs-lookup"><span data-stu-id="813a7-147">Connect to Windows Device Portal</span></span>

<span data-ttu-id="813a7-148">사용 합니다 [Windows Device Portal](../manage-your-device/DevicePortal.md) 웹 브라우저를 통해 장치를 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="813a7-148">Use the [Windows Device Portal](../manage-your-device/DevicePortal.md) to connect your device through a web browser.</span></span> <span data-ttu-id="813a7-149">장치 포털 중요 한 구성 및 장치 관리 기능을 사용할 수 있게 합니다.</span><span class="sxs-lookup"><span data-stu-id="813a7-149">The device portal makes valuable configuration and device management capabilities available.</span></span> 

