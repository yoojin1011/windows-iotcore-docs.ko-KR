---
title: Windows 10 IoT Core 대시보드
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Windows 10 IoT Core 대시보드 기능에 대해 알아봅니다 및 시작 방법입니다.
keywords: windows iot, windows 10 iot core 대시보드, windows iot 대시보드, 장치
ms.openlocfilehash: d21b67dad15d510564ec7fae28a2431d28faf8be
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513718"
---
# <a name="windows-10-iot-core-dashboard"></a><span data-ttu-id="11b05-104">Windows 10 IoT Core 대시보드</span><span class="sxs-lookup"><span data-stu-id="11b05-104">Windows 10 IoT Core Dashboard</span></span>

<span data-ttu-id="11b05-105">Windows 10 IoT Core 다운로드, 설치 하는 가장 좋은 방법은 대시보드와 모든 PC에서 Windows 10 IoT Core 장치에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="11b05-105">Windows 10 IoT Core Dashboard is the best way to download, set up and connect your Windows 10 IoT Core devices, all from your PC.</span></span>

<span data-ttu-id="11b05-106">다운로드할 수 있습니다 합니다 [여기에 IoT Core 대시보드](http://go.microsoft.com/fwlink/?LinkID=708576)합니다.</span><span class="sxs-lookup"><span data-stu-id="11b05-106">You can download the [IoT Core Dashboard here](http://go.microsoft.com/fwlink/?LinkID=708576).</span></span>

> [!NOTE]
> <span data-ttu-id="11b05-107">다운로드 한 후 IoT 대시보드를 열 때 흰색 화면 보시기 수 있는지를 찾는 경우 드라이버 문제 때문일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11b05-107">If you're finding that you're getting a white screen when opening the IoT Dashboard after downloading, it may due to a driver issue.</span></span> <span data-ttu-id="11b05-108">이 문제를 해결 하기 위해 다운로드 해야 합니다 [zip 형식으로](https://downloadmirror.intel.com/27894/a08/win64_24.20.100.6229.zip) Intel 그래픽 드라이버의 드라이버를 수동으로 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="11b05-108">To overcome this issue, you'll need to download the [zip format](https://downloadmirror.intel.com/27894/a08/win64_24.20.100.6229.zip) of the Intel Graphics Driver and install the driver manually.</span></span> 

## <a name="set-up-a-new-device"></a><span data-ttu-id="11b05-109">새 장치 설정</span><span class="sxs-lookup"><span data-stu-id="11b05-109">Set up a new device</span></span>

> [!NOTE]
> <span data-ttu-id="11b05-110">대시보드는 Raspberry Pi 3B +를 설치 하는 데 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="11b05-110">Dashboard cannot be used used to setup the Raspberry Pi 3B+.</span></span> <span data-ttu-id="11b05-111">3B + 장치가 있는 경우 사용 해야 합니다 [3B + 기술 미리 보기](https://www.microsoft.com/en-us/software-download/windowsiot)합니다.</span><span class="sxs-lookup"><span data-stu-id="11b05-111">If you have a 3B+ device, you must use the [3B+ technical preview](https://www.microsoft.com/en-us/software-download/windowsiot).</span></span> <span data-ttu-id="11b05-112">참조 하십시오 합니다 [알려진 제한 사항](https://docs.microsoft.com/en-us/windows/iot-core/troubleshooting) 이 개발에 적합 한지 여부를 확인 하려면 기술 미리 보기.</span><span class="sxs-lookup"><span data-stu-id="11b05-112">Please view the [known limitations](https://docs.microsoft.com/en-us/windows/iot-core/troubleshooting) of the technical preview to determine if this is suitable for your development.</span></span>

> [!NOTE]
> <span data-ttu-id="11b05-113">현재 OS SD 카드에 파티션을 통해 이동 하 고는 'Format'...' 라는 메시지를 표시 하는 위치의 알려진된 문제</span><span class="sxs-lookup"><span data-stu-id="11b05-113">There is currently a known issue where the OS goes through the partitions on the SD card and prompts a 'Format ..'</span></span> <span data-ttu-id="11b05-114">모든 파일 시스템을 포함 하지 않는 특정 데이터 파티션에 대 한 메시지입니다.</span><span class="sxs-lookup"><span data-stu-id="11b05-114">message for a specific data partition that does not contain any file system.</span></span> <span data-ttu-id="11b05-115">취소 눌러이 프롬프트를 해제 하세요.</span><span class="sxs-lookup"><span data-stu-id="11b05-115">Please dismiss this prompt by pressing cancel.</span></span> <span data-ttu-id="11b05-116">솔루션에서 작업을 하는 동안에 'Format 이제'를 클릭 하면 있습니다 경감 FFU 이미지를 사용 하 여 SD 카드 다시 업데이트 프로세스 및 장치 업데이트 실패 형식 작업 영향으로는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="11b05-116">While we work on a solution, we recommend that if you click on 'Format now,' you reflash the SD card with the FFU image again as the format action impacts the update process and the device will fail to update.</span></span>


<span data-ttu-id="11b05-117">IoT 대시보드에 쉽게 새 장치를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="11b05-117">The IoT Dashboard makes it easy to set up a new device.</span></span> <span data-ttu-id="11b05-118">시작 하는 방법에 대 한 자세한 내용은 참조는 [시작](https://docs.microsoft.com/en-us/windows/iot-core/getstarted) 페이지입니다.</span><span class="sxs-lookup"><span data-stu-id="11b05-118">For detailed instructions on how to get started, see the [Get Started](https://docs.microsoft.com/en-us/windows/iot-core/getstarted) page.</span></span>

![IoT 대시보드 설정 페이지](../media/IoTDashboard/IoTDashboard_SetupPage.PNG)

### <a name="sd-card"></a><span data-ttu-id="11b05-120">SD 카드</span><span class="sxs-lookup"><span data-stu-id="11b05-120">SD card</span></span>
<span data-ttu-id="11b05-121">유형, 제조업체 및 모델 SD 카드의 성능 및 IoT Core의 품질에 영향을 크게입니다.</span><span class="sxs-lookup"><span data-stu-id="11b05-121">The type, make and model of the SD card greatly affects both the performance and the quality of IoT Core.</span></span>
<span data-ttu-id="11b05-122">느린 카드 보다 부팅 하는 데 최대 5 배 더 걸릴 수 있습니다 우리의 [카드 권장](../learn-about-hardware/hardwarecompatlist.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="11b05-122">A slow card can take up to five times longer to boot than our [recommended cards](../learn-about-hardware/hardwarecompatlist.md).</span></span>
<span data-ttu-id="11b05-123">오래 되 고 덜 안정적인 SD 카드도 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="11b05-123">An older, less reliable SD card may not even work.</span></span> <span data-ttu-id="11b05-124">를 계속 설치 하는 문제가 발생 하는 경우에 SD 카드를 대체 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="11b05-124">If you continue to run into problems installing, consider replacing the SD card.</span></span>

### <a name="device-name"></a><span data-ttu-id="11b05-125">장치 이름</span><span class="sxs-lookup"><span data-stu-id="11b05-125">Device Name</span></span>
<span data-ttu-id="11b05-126">기본 장치 이름은 minwinpc입니다.</span><span class="sxs-lookup"><span data-stu-id="11b05-126">The default device name is minwinpc.</span></span> <span data-ttu-id="11b05-127">이 인해 쉽게 네트워크에 장치를 찾을 수 있도록 고유한 값으로 변경 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="11b05-127">We recommend changing it to something unique as this makes it easier to find the device on the network.</span></span> <span data-ttu-id="11b05-128">장치 이름을 최대 15 자일 수 장기 있으며 문자, 숫자와 기호만 포함할 수: @ # $ % ^ & ') (합니다.</span><span class="sxs-lookup"><span data-stu-id="11b05-128">The device name can be at most 15 characters long and can include letters, numbers and the following symbols:  @ # $ % ^ & ' ) ( .</span></span> <span data-ttu-id="11b05-129">-_ {} ~ 자동 다시 부팅을 장치에 전원을 경우 처음으로 현상이 장치를 설정 하는 경우 IoT 대시보드에서 장치 이름을 변경 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="11b05-129">- _ { } ~ If you change the device name in IoT Dashboard when setting up your device, an automatic reboot will happen the first time when you power on the device.</span></span>

### <a name="password"></a><span data-ttu-id="11b05-130">암호</span><span class="sxs-lookup"><span data-stu-id="11b05-130">Password</span></span>
<span data-ttu-id="11b05-131">암호는 필수 필드 및 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="11b05-131">Password is a mandatory field and must be set.</span></span> <span data-ttu-id="11b05-132">기본적으로 관리자가 사용자의 암호를 수정 IoT 대시보드에서 암호를 설정 합니다. "p@ssw0rd"입니다.</span><span class="sxs-lookup"><span data-stu-id="11b05-132">Setting a password in IoT Dashboard modifies the password for Administrator user which by default is "p@ssw0rd".</span></span>

### <a name="wi-fi-network-connection"></a><span data-ttu-id="11b05-133">Wi-fi 네트워크 연결</span><span class="sxs-lookup"><span data-stu-id="11b05-133">Wi-Fi Network connection</span></span>
<span data-ttu-id="11b05-134">IoT 대시보드 사용자 PC에 연결 된 이전에 사용 가능한 모든 네트워크를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="11b05-134">IoT Dashboard shows all available networks that your PC has previously connected to.</span></span> <span data-ttu-id="11b05-135">목록에서 원하는 Wi-fi 네트워크를 보이지 않으면 PC에 연결을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="11b05-135">If you don't see the desired Wi-Fi network on the list, ensure you're connected to it on your PC.</span></span>
<span data-ttu-id="11b05-136">확인란의 선택을 취소 하는 경우 깜박임 후 보드로 이더넷 케이블을 연결 해야 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11b05-136">If you uncheck the box, you must connect an Ethernet cable to your board after flashing.</span></span>

### <a name="first-boot"></a><span data-ttu-id="11b05-137">처음 부팅</span><span class="sxs-lookup"><span data-stu-id="11b05-137">First boot</span></span>
<span data-ttu-id="11b05-138">첫 번째 부팅 하는 모든 후속 부팅 보다 더 오래 걸립니다 항상.</span><span class="sxs-lookup"><span data-stu-id="11b05-138">The first boot will always take longer than all subsequent boots.</span></span> <span data-ttu-id="11b05-139">운영 체제를 설치 하 고 네트워크에 연결 하는 데 시간이 걸립니다.</span><span class="sxs-lookup"><span data-stu-id="11b05-139">The operating system will take some time to install and connect to your network.</span></span>
<span data-ttu-id="11b05-140">부팅 시간에 SD 카드에 따라 크게 달라질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11b05-140">Boot time can vary greatly based on your SD card.</span></span> <span data-ttu-id="11b05-141">예를 들어이 권장 되는 SD 카드에서 실행 중인 Raspberry Pi 3 첫 번째 부팅 3-4 분이 걸립니다.</span><span class="sxs-lookup"><span data-stu-id="11b05-141">For example, a Raspberry Pi 3 running on our recommended SD card takes 3-4 minutes for first boot.</span></span> <span data-ttu-id="11b05-142">저품질 SD 카드를 사용 하 여 동일한 Pi에서 부팅 시간 15 분 이상에 대해 살펴보았습니다.</span><span class="sxs-lookup"><span data-stu-id="11b05-142">On the same Pi with a poor quality SD card, we have seen boot times longer than 15 minutes.</span></span>

### <a name="connecting-to-the-internet"></a><span data-ttu-id="11b05-143">인터넷에 연결</span><span class="sxs-lookup"><span data-stu-id="11b05-143">Connecting to the internet</span></span>
<span data-ttu-id="11b05-144">IoT Core 장치를 인터넷에 연결 하는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="11b05-144">Having your IoT Core device connect to the internet is essential.</span></span> <span data-ttu-id="11b05-145">다양 한 최신 보드 수반 빌드된 Wi-fi 어댑터에서.</span><span class="sxs-lookup"><span data-stu-id="11b05-145">Many of the newer boards come with built in Wi-Fi adapters.</span></span> <span data-ttu-id="11b05-146">네트워크에 연결 하는 데 문제가 있으면 다음을 시도 합니다.</span><span class="sxs-lookup"><span data-stu-id="11b05-146">If you have trouble getting connected to your network, try the following:</span></span>

* <span data-ttu-id="11b05-147">장치 다시 부팅</span><span class="sxs-lookup"><span data-stu-id="11b05-147">Rebooting the device</span></span>
* <span data-ttu-id="11b05-148">이더넷 케이블 연결</span><span class="sxs-lookup"><span data-stu-id="11b05-148">Plugging in an Ethernet cable</span></span>
* <span data-ttu-id="11b05-149">모니터 장치를 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="11b05-149">Plugging in a monitor to the device.</span></span> <span data-ttu-id="11b05-150">장치에 대 한 진단 정보가 표시 됩니다이</span><span class="sxs-lookup"><span data-stu-id="11b05-150">This will show you diagnostic information about your device</span></span>

> [!NOTE]
> <span data-ttu-id="11b05-151">공식 Raspberry Pi 2 Wi-fi 어댑터 Wi-fi에 연결할 때 안정적인 없습니다 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11b05-151">The official Raspberry Pi 2 Wi-Fi adapter can be unstable when connecting to Wi-Fi.</span></span>


## <a name="my-devices"></a><span data-ttu-id="11b05-152">내 장치</span><span class="sxs-lookup"><span data-stu-id="11b05-152">My Devices</span></span>
___
<span data-ttu-id="11b05-153">장치는 인터넷에 연결 되 면 IoT 대시보드는 장치를 자동으로 검색 됩니다.</span><span class="sxs-lookup"><span data-stu-id="11b05-153">After your device is connected to the internet, the IoT Dashboard will automatically detect your device.</span></span>
<span data-ttu-id="11b05-154">장치를 찾으려면에서로 이동 **내 장치**합니다.</span><span class="sxs-lookup"><span data-stu-id="11b05-154">To find your device, go to **My Devices**.</span></span> <span data-ttu-id="11b05-155">장치가 나열 되지 않으면, 장치 다시 부팅 하십시오.</span><span class="sxs-lookup"><span data-stu-id="11b05-155">If your device is not listed, try rebooting the device.</span></span> <span data-ttu-id="11b05-156">경우 둘 이상의 장치를 네트워크에 각각 고유한 이름이 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="11b05-156">Make sure that if there are more than one devices on the network, they each have a unique name.</span></span> <span data-ttu-id="11b05-157">확인 프로그램 **windows10iotcoredashboard.exe** 다음 단계를 수행 하 여 Windows 방화벽을 통해 통신 하도록 허용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="11b05-157">Also make sure that your **windows10iotcoredashboard.exe** is allowed to communicate through Windows Firewall by following the steps below:</span></span>

1. <span data-ttu-id="11b05-158">오픈 **네트워크 및 공유 센터** 을 PC에 연결 된 네트워크 (도메인/사설/공용)의 종류를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="11b05-158">Open **Network and Sharing Center** and then find the type of network (Domain/Private/Public) your PC is connected to.</span></span>
2. <span data-ttu-id="11b05-159">오픈 **Control Panel** 클릭 **시스템 및 보안**합니다.</span><span class="sxs-lookup"><span data-stu-id="11b05-159">Open **Control Panel** and click **System and Security**.</span></span>
3. <span data-ttu-id="11b05-160">클릭 **Windows 방화벽을 통해 앱 허용** 아래에서 **Windows 방화벽**합니다.</span><span class="sxs-lookup"><span data-stu-id="11b05-160">Click **Allow an app through Windows Firewall** under **Windows Firewall**.</span></span>
4. <span data-ttu-id="11b05-161">클릭 **설정을 변경**합니다.</span><span class="sxs-lookup"><span data-stu-id="11b05-161">Click **Change settings**.</span></span>
5. <span data-ttu-id="11b05-162">찾을 **windows10iotcoredashboard.exe** 에 **허용 되는 앱 및 기능** 다음 적절 한 네트워크 확인란 (즉, 1 단계에서 찾은 네트워크 형식)를 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="11b05-162">Find **windows10iotcoredashboard.exe** in **Allowed apps and features** and then enable the appropriate network check box (i.e. the network type you found in step 1).</span></span>


### <a name="connect-to-your-device"></a><span data-ttu-id="11b05-163">장치에 연결</span><span class="sxs-lookup"><span data-stu-id="11b05-163">Connect to your device</span></span>

> [!NOTE]
> <span data-ttu-id="11b05-164">대시보드에서 장치를 찾을 수 없는 경우 [IP 주소]를 입력 해 보세요 및 [: 8080] Windows Device Portal 시작 및 실행 하 여 브라우저에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11b05-164">If you are unable to find your device in the dashboard, try typing your [IP Address] and [:8080] into the browser to get Windows Device Portal up and running.</span></span> <span data-ttu-id="11b05-165">대시보드에 표시 하기 위해 장치를 가져오려면 장치 다시 부팅을 시도 합니다.</span><span class="sxs-lookup"><span data-stu-id="11b05-165">To get your device to show in the dashboard, try rebooting your device.</span></span>


<span data-ttu-id="11b05-166">마우스 오른쪽 단추로 클릭 하 고 선택 **장치 포털에서 열기**합니다.</span><span class="sxs-lookup"><span data-stu-id="11b05-166">Right click and select **Open in Device Portal**.</span></span> <span data-ttu-id="11b05-167">시작 합니다 [Windows Device Portal](../manage-your-device/DevicePortal.md) 페이지와 상호 작용 하 고 장치를 관리 하는 가장 좋은 방법은 합니다.</span><span class="sxs-lookup"><span data-stu-id="11b05-167">This will launch the [Windows Device Portal](../manage-your-device/DevicePortal.md) page and is the best way to interact and manage your device.</span></span>

![장치 IoTDashboard 보기](../media/IoTDashboard/IoTDashboard_RightClickMenu.PNG)

<span data-ttu-id="11b05-169">Windows PowerShell을 사용 하 여 장치에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11b05-169">You can also connect to the device using Windows PowerShell.</span></span>

## <a name="connect-to-azure"></a><span data-ttu-id="11b05-170">Azure에 연결</span><span class="sxs-lookup"><span data-stu-id="11b05-170">Connect to Azure</span></span>
___
<span data-ttu-id="11b05-171">IoT 대시보드 사용 하면 Azure IoT Hub를 사용 하 여 IoT Core 장치 프로 비전 합니다.</span><span class="sxs-lookup"><span data-stu-id="11b05-171">IoT Dashboard lets you provision IoT Core devices with Azure IoT Hub.</span></span> <span data-ttu-id="11b05-172">자세한 내용은이 대 한 [블로그 게시물](https://blogs.windows.com/buildingapps/2016/07/20/building-secure-apps-for-windows-iot-core)합니다.</span><span class="sxs-lookup"><span data-stu-id="11b05-172">You can read more about it in this [blog post](https://blogs.windows.com/buildingapps/2016/07/20/building-secure-apps-for-windows-iot-core).</span></span>

[<span data-ttu-id="11b05-173">Azure IoT 대시보드를 사용 하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="11b05-173">Learn how to use the IoT Dashboard with Azure</span></span>](https://docs.microsoft.com/windows/iot-core/connect-to-cloud/connectdevicetocloud)

## <a name="quick-run-samples"></a><span data-ttu-id="11b05-174">빠른 실행된 샘플</span><span class="sxs-lookup"><span data-stu-id="11b05-174">Quick Run Samples</span></span>
___

<span data-ttu-id="11b05-175">빠른 실행 샘플에는 모든 코드 컴파일, Visual studio 설치 필요 하지 않습니다 또는 SDK를 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="11b05-175">Quick run samples do not require any code compilation, Visual studio installation or SDK download.</span></span> <span data-ttu-id="11b05-176">신속 하 게 IoT Core에서 수행할 수 있는 작업 확인에 대 한 이러한 탁월 합니다.</span><span class="sxs-lookup"><span data-stu-id="11b05-176">They are great for quickly checking out what IoT Core can do.</span></span>

### <a name="network-3d-printer"></a><span data-ttu-id="11b05-177">3D 네트워크 프린터</span><span class="sxs-lookup"><span data-stu-id="11b05-177">Network 3D Printer</span></span>
<span data-ttu-id="11b05-178">사용 하 여 3D 프린터 보드를 연결할 네트워크 3D 프린터 샘플 수를 찾을 수 있도록 홈 네트워크를 통해.</span><span class="sxs-lookup"><span data-stu-id="11b05-178">Use the Network 3D Printer sample to connect your 3D Printer to your board can make it discoverable over your home network.</span></span> 

![3D IoTDashboard 네트워크 프린터](../media/IoTDashboard/IoTDashboard_3DPrinter.PNG)

### <a name="internet-radio"></a><span data-ttu-id="11b05-180">인터넷 라디오</span><span class="sxs-lookup"><span data-stu-id="11b05-180">Internet radio</span></span>
<span data-ttu-id="11b05-181">Windows 10 IoT Core 장치 제어할 수 있는에서 아무 곳 이나 집에는 인터넷 라디오를 바꿔 보세요.</span><span class="sxs-lookup"><span data-stu-id="11b05-181">Turn your Windows 10 IoT Core device into an internet radio that can be controlled from anywhere in your home.</span></span>

![IoTDashboard 인터넷 라디오](../media/IoTDashboard/IoTDashboard_InternetRadio.PNG)

### <a name="iot-core-blockly"></a><span data-ttu-id="11b05-183">IoT Core Blockly</span><span class="sxs-lookup"><span data-stu-id="11b05-183">IoT Core Blockly</span></span>
<span data-ttu-id="11b05-184">IoT Core Blockly 샘플 프로그램을 Raspberry Pi2 또는 3 및 브라우저에서 "블록"이 편집기를 사용 하는 Raspberry Pi Sense hat 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11b05-184">IoT Core Blockly sample lets your program a Raspberry Pi2 or 3 and a Raspberry Pi Sense hat using a "block" editor from your browser.</span></span>

![IoTDashboard Blockly](../media/IoTDashboard/IoTDashboard_Blockly.PNG)
