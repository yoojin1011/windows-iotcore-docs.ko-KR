---
title: Windows 10 IoT Core 대시보드
ms.date: 08/28/2017
ms.topic: article
description: Windows 10 IoT Core 대시보드의 기능 및 시작 하는 방법에 대해 알아봅니다.
keywords: windows iot, windows 10 iot core 대시보드, windows iot 대시보드, 장치
ms.openlocfilehash: 53a8be4e29f93ab3f6d9979e247c598ea5e637c8
ms.sourcegitcommit: ea060254f9c4c25afcd0245c897b9e1425321859
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75721488"
---
# <a name="windows-10-iot-core-dashboard"></a><span data-ttu-id="787c6-104">Windows 10 IoT Core 대시보드</span><span class="sxs-lookup"><span data-stu-id="787c6-104">Windows 10 IoT Core Dashboard</span></span>

<span data-ttu-id="787c6-105">Windows 10 IoT Core 대시보드는 PC에서 Windows 10 IoT Core 장치를 다운로드 하 고 설정 하 고 연결 하는 가장 좋은 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="787c6-105">Windows 10 IoT Core Dashboard is the best way to download, set up and connect your Windows 10 IoT Core devices, all from your PC.</span></span>

<span data-ttu-id="787c6-106">[IoT Core 대시보드는 여기](https://go.microsoft.com/fwlink/?LinkID=708576)에서 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="787c6-106">You can download the [IoT Core Dashboard here](https://go.microsoft.com/fwlink/?LinkID=708576).</span></span>

> [!NOTE]
> <span data-ttu-id="787c6-107">다운로드 한 후 IoT 대시보드를 열 때 흰색 화면이 표시 되는 경우 드라이버 문제 때문일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="787c6-107">If you're finding that you're getting a white screen when opening the IoT Dashboard after downloading, it may be due to a driver issue.</span></span> <span data-ttu-id="787c6-108">이 문제를 해결 하려면 Intel Graphics Driver의 [zip 형식을](https://downloadmirror.intel.com/27894/a08/win64_24.20.100.6229.zip) 다운로드 하 고 드라이버를 수동으로 설치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="787c6-108">To overcome this issue, you'll need to download the [zip format](https://downloadmirror.intel.com/27894/a08/win64_24.20.100.6229.zip) of the Intel Graphics Driver and install the driver manually.</span></span> 

## <a name="set-up-a-new-device"></a><span data-ttu-id="787c6-109">새 장치 설정</span><span class="sxs-lookup"><span data-stu-id="787c6-109">Set up a new device</span></span>

> [!NOTE]
> <span data-ttu-id="787c6-110">대시보드는 Raspberry Pi 3B+를 설정하는 데 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="787c6-110">Dashboard cannot be used used to setup the Raspberry Pi 3B+.</span></span> <span data-ttu-id="787c6-111">3B+ 디바이스가 있는 경우 [3B+ 기술 미리 보기](https://www.microsoft.com/software-download/windowsiot)를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="787c6-111">If you have a 3B+ device, you must use the [3B+ technical preview](https://www.microsoft.com/software-download/windowsiot).</span></span> <span data-ttu-id="787c6-112">기술 미리 보기의 [알려진 제한 사항](https://docs.microsoft.com/windows/iot-core/troubleshooting)을 확인하여 개발 작업에 적합한지 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="787c6-112">Please view the [known limitations](https://docs.microsoft.com/windows/iot-core/troubleshooting) of the technical preview to determine if this is suitable for your development.</span></span>

> [!NOTE]
> <span data-ttu-id="787c6-113">현재 OS가 SD 카드의 파티션을 통해 이동 하 고 ' 형식. '를 요청 하는 알려진 문제가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="787c6-113">There is currently a known issue where the OS goes through the partitions on the SD card and prompts a 'Format ..'</span></span> <span data-ttu-id="787c6-114">파일 시스템을 포함 하지 않는 특정 데이터 파티션에 대 한 메시지입니다.</span><span class="sxs-lookup"><span data-stu-id="787c6-114">message for a specific data partition that does not contain any file system.</span></span> <span data-ttu-id="787c6-115">[취소]를 눌러이 프롬프트를 해제 하십시오.</span><span class="sxs-lookup"><span data-stu-id="787c6-115">Please dismiss this prompt by pressing cancel.</span></span> <span data-ttu-id="787c6-116">솔루션에서 작업 하는 동안 ' 지금 서식 '을 클릭 하면 경감 하기 위해가 업데이트 프로세스에 영향을 주는 형식 작업이 업데이트 프로세스에 영향을 주므로 장치를 업데이트 하지 못하여 SD 카드를 다시 FFU 이미지로 다시 설정 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="787c6-116">While we work on a solution, we recommend that if you click on 'Format now,' you reflash the SD card with the FFU image again as the format action impacts the update process and the device will fail to update.</span></span>


<span data-ttu-id="787c6-117">IoT 대시보드를 사용 하면 새 장치를 쉽게 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="787c6-117">The IoT Dashboard makes it easy to set up a new device.</span></span> <span data-ttu-id="787c6-118">시작 하는 방법에 대 한 자세한 내용은 [시작](https://docs.microsoft.com/windows/iot-core/getstarted) 페이지를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="787c6-118">For detailed instructions on how to get started, see the [Get Started](https://docs.microsoft.com/windows/iot-core/getstarted) page.</span></span>

![IoT 대시보드 설정 페이지](../media/IoTDashboard/IoTDashboard_SetupPage.PNG)

### <a name="sd-card"></a><span data-ttu-id="787c6-120">SD 카드</span><span class="sxs-lookup"><span data-stu-id="787c6-120">SD card</span></span>
<span data-ttu-id="787c6-121">SD 카드의 유형, 제조업체 및 모델이 IoT Core의 성능 및 품질에 크게 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="787c6-121">The type, make and model of the SD card greatly affects both the performance and the quality of IoT Core.</span></span>
<span data-ttu-id="787c6-122">저속 카드는 [권장 카드](../learn-about-hardware/hardwarecompatlist.md)보다 부팅 하는 데 최대 5 배 더 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="787c6-122">A slow card can take up to five times longer to boot than our [recommended cards](../learn-about-hardware/hardwarecompatlist.md).</span></span>
<span data-ttu-id="787c6-123">이전의 더 안정적인 SD 카드는 작동 하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="787c6-123">An older, less reliable SD card may not even work.</span></span> <span data-ttu-id="787c6-124">설치 문제가 계속 되 면 SD 카드를 교체 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="787c6-124">If you continue to run into problems installing, consider replacing the SD card.</span></span>

### <a name="device-name"></a><span data-ttu-id="787c6-125">장치 이름</span><span class="sxs-lookup"><span data-stu-id="787c6-125">Device Name</span></span>
<span data-ttu-id="787c6-126">기본 장치 이름은 minwinpc입니다.</span><span class="sxs-lookup"><span data-stu-id="787c6-126">The default device name is minwinpc.</span></span> <span data-ttu-id="787c6-127">네트워크에서 장치를 보다 쉽게 찾을 수 있도록 하기 때문에 고유한 항목으로 변경 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="787c6-127">We recommend changing it to something unique as this makes it easier to find the device on the network.</span></span> <span data-ttu-id="787c6-128">장치 이름은 15 자이 하 여야 하 고, 문자, 숫자 및 다음 기호를 포함할 수 있습니다. @ # $% ^ & ') (.</span><span class="sxs-lookup"><span data-stu-id="787c6-128">The device name can be at most 15 characters long and can include letters, numbers and the following symbols:  @ # $ % ^ & ' ) ( .</span></span> <span data-ttu-id="787c6-129">-_ {} ~ 장치를 설정할 때 IoT 대시보드에서 장치 이름을 변경 하는 경우 처음으로 장치를 켤 때 자동 다시 부팅이 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="787c6-129">- _ { } ~ If you change the device name in IoT Dashboard when setting up your device, an automatic reboot will happen the first time when you power on the device.</span></span>

### <a name="password"></a><span data-ttu-id="787c6-130">Password(암호)</span><span class="sxs-lookup"><span data-stu-id="787c6-130">Password</span></span>
<span data-ttu-id="787c6-131">암호는 필수 필드 이므로 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="787c6-131">Password is a mandatory field and must be set.</span></span> <span data-ttu-id="787c6-132">IoT 대시보드에서 암호를 설정 하면 관리자 사용자에 대 한 암호를 수정 합니다 .이 암호는 기본적으로 "p@ssw0rd"입니다.</span><span class="sxs-lookup"><span data-stu-id="787c6-132">Setting a password in IoT Dashboard modifies the password for Administrator user which by default is "p@ssw0rd".</span></span>

### <a name="wi-fi-network-connection"></a><span data-ttu-id="787c6-133">Wi-fi 네트워크 연결</span><span class="sxs-lookup"><span data-stu-id="787c6-133">Wi-Fi Network connection</span></span>
<span data-ttu-id="787c6-134">IoT 대시보드에는 PC가 이전에 연결한 모든 사용 가능한 네트워크가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="787c6-134">IoT Dashboard shows all available networks that your PC has previously connected to.</span></span> <span data-ttu-id="787c6-135">원하는 Wi-fi 네트워크가 목록에 표시 되지 않으면 PC에서 해당 Wi-fi 네트워크에 연결 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="787c6-135">If you don't see the desired Wi-Fi network on the list, ensure you're connected to it on your PC.</span></span>
<span data-ttu-id="787c6-136">이 확인란의 선택을 취소 하는 경우 플래시 후에 보드에 이더넷 케이블을 연결 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="787c6-136">If you uncheck the box, you must connect an Ethernet cable to your board after flashing.</span></span>

### <a name="first-boot"></a><span data-ttu-id="787c6-137">처음 부팅</span><span class="sxs-lookup"><span data-stu-id="787c6-137">First boot</span></span>
<span data-ttu-id="787c6-138">첫 번째 부팅은 항상 모든 후속 부팅 보다 더 오래 걸립니다.</span><span class="sxs-lookup"><span data-stu-id="787c6-138">The first boot will always take longer than all subsequent boots.</span></span> <span data-ttu-id="787c6-139">운영 체제를 설치 하 고 네트워크에 연결 하는 데 약간의 시간이 걸립니다.</span><span class="sxs-lookup"><span data-stu-id="787c6-139">The operating system will take some time to install and connect to your network.</span></span>
<span data-ttu-id="787c6-140">부팅 시간은 SD 카드에 따라 크게 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="787c6-140">Boot time can vary greatly based on your SD card.</span></span> <span data-ttu-id="787c6-141">예를 들어 권장 SD 카드에서 실행 되는 Raspberry Pi 3은 첫 번째 부팅에 대해 3-4 분이 소요 됩니다.</span><span class="sxs-lookup"><span data-stu-id="787c6-141">For example, a Raspberry Pi 3 running on our recommended SD card takes 3-4 minutes for first boot.</span></span> <span data-ttu-id="787c6-142">품질이 낮은 SD 카드를 사용 하는 동일한 Pi에서 15 분 보다 긴 부팅 시간이 나타났습니다.</span><span class="sxs-lookup"><span data-stu-id="787c6-142">On the same Pi with a poor quality SD card, we have seen boot times longer than 15 minutes.</span></span>

### <a name="connecting-to-the-internet"></a><span data-ttu-id="787c6-143">인터넷에 연결</span><span class="sxs-lookup"><span data-stu-id="787c6-143">Connecting to the internet</span></span>
<span data-ttu-id="787c6-144">IoT Core 장치를 인터넷에 연결 하는 것이 필수적입니다.</span><span class="sxs-lookup"><span data-stu-id="787c6-144">Having your IoT Core device connect to the internet is essential.</span></span> <span data-ttu-id="787c6-145">최신 보드의 대부분은 기본 제공 Wi-fi 어댑터와 함께 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="787c6-145">Many of the newer boards come with built in Wi-Fi adapters.</span></span> <span data-ttu-id="787c6-146">네트워크에 연결 하는 데 문제가 있는 경우 다음을 시도 합니다.</span><span class="sxs-lookup"><span data-stu-id="787c6-146">If you have trouble getting connected to your network, try the following:</span></span>

* <span data-ttu-id="787c6-147">장치 재부팅</span><span class="sxs-lookup"><span data-stu-id="787c6-147">Rebooting the device</span></span>
* <span data-ttu-id="787c6-148">이더넷 케이블 연결</span><span class="sxs-lookup"><span data-stu-id="787c6-148">Plugging in an Ethernet cable</span></span>
* <span data-ttu-id="787c6-149">장치에 모니터를 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="787c6-149">Plugging in a monitor to the device.</span></span> <span data-ttu-id="787c6-150">그러면 장치에 대 한 진단 정보가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="787c6-150">This will show you diagnostic information about your device</span></span>

> [!NOTE]
> <span data-ttu-id="787c6-151">Wi-fi에 연결 하는 경우 공식 Raspberry Pi 2 Wi-fi 어댑터를 불안정 하 게 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="787c6-151">The official Raspberry Pi 2 Wi-Fi adapter can be unstable when connecting to Wi-Fi.</span></span>


## <a name="my-devices"></a><span data-ttu-id="787c6-152">내 디바이스</span><span class="sxs-lookup"><span data-stu-id="787c6-152">My Devices</span></span>
___
<span data-ttu-id="787c6-153">장치가 인터넷에 연결 되 면 IoT 대시보드가 자동으로 장치를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="787c6-153">After your device is connected to the internet, the IoT Dashboard will automatically detect your device.</span></span>
<span data-ttu-id="787c6-154">장치를 찾으려면 **내 장치**로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="787c6-154">To find your device, go to **My Devices**.</span></span> <span data-ttu-id="787c6-155">장치가 나열 되지 않으면 장치를 다시 부팅 합니다.</span><span class="sxs-lookup"><span data-stu-id="787c6-155">If your device is not listed, try rebooting the device.</span></span> <span data-ttu-id="787c6-156">네트워크에 장치가 둘 이상 있는지 확인 하 고 각각에 고유한 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="787c6-156">Make sure that if there are more than one devices on the network, they each have a unique name.</span></span> <span data-ttu-id="787c6-157">또한 다음 단계를 수행 하 여 **windows10iotcoredashboard** 가 Windows 방화벽을 통해 통신할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="787c6-157">Also make sure that your **windows10iotcoredashboard.exe** is allowed to communicate through Windows Firewall by following the steps below:</span></span>

1. <span data-ttu-id="787c6-158">**네트워크 및 공유 센터** 를 연 다음 PC가 연결 된 네트워크 유형 (도메인/개인/공용)을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="787c6-158">Open **Network and Sharing Center** and then find the type of network (Domain/Private/Public) your PC is connected to.</span></span>
2. <span data-ttu-id="787c6-159">**제어판** 을 열고 **시스템 및 보안**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="787c6-159">Open **Control Panel** and click **System and Security**.</span></span>
3. <span data-ttu-id="787c6-160">**Windows 방화벽**에서 **windows 방화벽을 통해 앱 허용** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="787c6-160">Click **Allow an app through Windows Firewall** under **Windows Firewall**.</span></span>
4. <span data-ttu-id="787c6-161">**설정 변경**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="787c6-161">Click **Change settings**.</span></span>
5. <span data-ttu-id="787c6-162">**허용 되는 앱 및 기능** 에서 **windows10iotcoredashboard** 을 찾은 다음 적절 한 네트워크 확인란을 사용 하도록 설정 합니다 (예: 1 단계에서 찾은 네트워크 유형).</span><span class="sxs-lookup"><span data-stu-id="787c6-162">Find **windows10iotcoredashboard.exe** in **Allowed apps and features** and then enable the appropriate network check box (i.e. the network type you found in step 1).</span></span>


### <a name="connect-to-your-device"></a><span data-ttu-id="787c6-163">디바이스에 연결</span><span class="sxs-lookup"><span data-stu-id="787c6-163">Connect to your device</span></span>

> [!NOTE]
> <span data-ttu-id="787c6-164">대시보드에서 장치를 찾을 수 없는 경우 [IP 주소] 및 [: 8080]를 브라우저에 입력 하 여 Windows 장치 포털을 시작 하 고 실행 하세요.</span><span class="sxs-lookup"><span data-stu-id="787c6-164">If you are unable to find your device in the dashboard, try typing your [IP Address] and [:8080] into the browser to get Windows Device Portal up and running.</span></span> <span data-ttu-id="787c6-165">대시보드에 장치를 표시 하려면 장치를 다시 부팅 합니다.</span><span class="sxs-lookup"><span data-stu-id="787c6-165">To get your device to show in the dashboard, try rebooting your device.</span></span>


<span data-ttu-id="787c6-166">마우스 오른쪽 단추를 클릭 하 고 **장치 포털에서 열기**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="787c6-166">Right click and select **Open in Device Portal**.</span></span> <span data-ttu-id="787c6-167">그러면 [Windows 장치 포털](../manage-your-device/DevicePortal.md) 페이지가 시작 되 고 장치를 조작 하 고 관리 하는 데 가장 적합 한 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="787c6-167">This will launch the [Windows Device Portal](../manage-your-device/DevicePortal.md) page and is the best way to interact and manage your device.</span></span>

![I이상 대시보드 보기 장치](../media/IoTDashboard/IoTDashboard_RightClickMenu.PNG)

<span data-ttu-id="787c6-169">Windows PowerShell을 사용 하 여 장치에 연결할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="787c6-169">You can also connect to the device using Windows PowerShell.</span></span>

## <a name="connect-to-azure"></a><span data-ttu-id="787c6-170">Azure 연결</span><span class="sxs-lookup"><span data-stu-id="787c6-170">Connect to Azure</span></span>
___
<span data-ttu-id="787c6-171">IoT 대시보드에서 Azure IoT Hub를 사용 하 여 IoT Core 장치를 프로 비전 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="787c6-171">IoT Dashboard lets you provision IoT Core devices with Azure IoT Hub.</span></span> <span data-ttu-id="787c6-172">이에 대 한 자세한 내용은이 [블로그 게시물](https://blogs.windows.com/buildingapps/2016/07/20/building-secure-apps-for-windows-iot-core)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="787c6-172">You can read more about it in this [blog post](https://blogs.windows.com/buildingapps/2016/07/20/building-secure-apps-for-windows-iot-core).</span></span>

[<span data-ttu-id="787c6-173">Azure에서 IoT 대시보드를 사용 하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="787c6-173">Learn how to use the IoT Dashboard with Azure</span></span>](https://docs.microsoft.com/windows/iot-core/connect-to-cloud/connectdevicetocloud)

## <a name="quick-run-samples"></a><span data-ttu-id="787c6-174">빠른 실행 샘플</span><span class="sxs-lookup"><span data-stu-id="787c6-174">Quick Run Samples</span></span>
___

<span data-ttu-id="787c6-175">빠른 실행 샘플에는 코드 컴파일, Visual studio 설치 또는 SDK 다운로드가 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="787c6-175">Quick run samples do not require any code compilation, Visual studio installation or SDK download.</span></span> <span data-ttu-id="787c6-176">IoT Core에서 수행할 수 있는 작업을 신속 하 게 확인 하는 데 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="787c6-176">They are great for quickly checking out what IoT Core can do.</span></span>

### <a name="network-3d-printer"></a><span data-ttu-id="787c6-177">네트워크 3D 프린터</span><span class="sxs-lookup"><span data-stu-id="787c6-177">Network 3D Printer</span></span>
<span data-ttu-id="787c6-178">네트워크 3D 프린터 샘플을 사용 하 여 3D 프린터를 보드에 연결 하면 홈 네트워크를 통해 검색 가능 하 게 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="787c6-178">Use the Network 3D Printer sample to connect your 3D Printer to your board can make it discoverable over your home network.</span></span> 

![IoTDashboard 네트워크 3D 프린터](../media/IoTDashboard/IoTDashboard_3DPrinter.PNG)

### <a name="internet-radio"></a><span data-ttu-id="787c6-180">인터넷 라디오</span><span class="sxs-lookup"><span data-stu-id="787c6-180">Internet radio</span></span>
<span data-ttu-id="787c6-181">Windows 10 IoT Core 장치를 홈의 어디에서 나 제어할 수 있는 인터넷 라디오로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="787c6-181">Turn your Windows 10 IoT Core device into an internet radio that can be controlled from anywhere in your home.</span></span>

![IoTDashboard 인터넷 라디오](../media/IoTDashboard/IoTDashboard_InternetRadio.PNG)

### <a name="iot-core-blockly"></a><span data-ttu-id="787c6-183">IoT Core Blockly</span><span class="sxs-lookup"><span data-stu-id="787c6-183">IoT Core Blockly</span></span>
<span data-ttu-id="787c6-184">IoT Core Blockly 샘플을 통해 프로그램은 브라우저에서 "블록" 편집기를 사용 하 여 Raspberry Pi2 또는 3 및 Raspberry Pi Sense hat를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="787c6-184">IoT Core Blockly sample lets your program a Raspberry Pi2 or 3 and a Raspberry Pi Sense hat using a "block" editor from your browser.</span></span>

![IoTDashboard Blockly](../media/IoTDashboard/IoTDashboard_Blockly.PNG)
