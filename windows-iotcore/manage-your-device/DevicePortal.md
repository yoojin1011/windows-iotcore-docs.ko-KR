---
title: Windows Device Portal
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: Windows Device Portal 사용 하 여 구성 하 고 장치를 원격으로 관리 하는 방법에 알아봅니다.
keywords: windows iot, Windows Device Portal, 원격 장치 포털
ms.openlocfilehash: 8e430365ea09509f5638d86ac77b151226df488f
ms.sourcegitcommit: 8932969dc50805113c330bc2ba6ec9003d067b3c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67412157"
---
# <a name="windows-device-portal"></a><span data-ttu-id="ad757-104">Windows Device Portal</span><span class="sxs-lookup"><span data-stu-id="ad757-104">Windows Device Portal</span></span>
   <span data-ttu-id="ad757-105">Windows Device Portal (WDP)를 사용 하 여 구성 하 고 로컬 네트워크를 통해 장치를 원격으로 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-105">The Windows Device Portal (WDP) lets you configure and manage your device remotely over your local network.</span></span>
<span data-ttu-id="ad757-106">주요 기능에 설명 되어는 [Windows Device Portal 개요 페이지](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal)</span><span class="sxs-lookup"><span data-stu-id="ad757-106">The main features are documented on the [Windows Device Portal overview page](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal)</span></span>

![장치 포털 홈](../media/deviceportal/deviceportal.png)

> [!IMPORTANT]
> <span data-ttu-id="ad757-108">상용화에 제조사 이미지를 사용하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="ad757-108">Do not use maker images for commercialization.</span></span> <span data-ttu-id="ad757-109">디바이스를 상용화하려는 경우 최적의 보안을 위해 사용자 지정 FFU를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-109">If you are commercializing a device, you must use a custom FFU for optimal security.</span></span> <span data-ttu-id="ad757-110">[여기](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)에서 자세한 내용을 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="ad757-110">Learn more [here](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).</span></span>

> [!WARNING]
> <span data-ttu-id="ad757-111">현재 라이브 커널 디버그 ARM 장치에 대 한 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-111">Live kernel debug is currently failing for ARM devices.</span></span> <span data-ttu-id="ad757-112">고정이 노력 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-112">We are working to get this fixed.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ad757-113">"특정/제한 installation"에 상용 배포에 대 한 열기 소매용 장치를 빌드하는 경우 (예:: factory 또는 소매 저장소)는 최종 사용자가 최종 구성을 수행 하 고 시켜야 하는 고객을 문서 [가져올를 WDP 변경 되 WDP 및 연결 브라우저와 암호에 WDP 및 설치에 대 한 인증서](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-ssl), WDP를 사용 하 여 좁은 상용 인스턴스에서이 허용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-113">If you are building an open retail device for commercial deployment to a "specific/limited installation" (i.e. factory or retail store) where the end-user does the final configuration and you document your customers that they must [obtain a certificate for WDP and install it on both WDP and connecting browsers and passwords are changed on WDP](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-ssl), then using WDP in this narrow commercial instance is acceptable.</span></span> <span data-ttu-id="ad757-114">이 시나리오에서는 일반 정품 이미지는 여전히 *되지* IOT_TOOLKIT를 포함 하지만 IOT_WEBBEXTN 패키지 WDP에서 끌어오기를 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-114">Retail images in this scenario should still *not* include IOT_TOOLKIT, but should use the IOT_WEBBEXTN package to pull in WDP.</span></span> 

## <a name="shared-documentation"></a><span data-ttu-id="ad757-115">공유 설명서</span><span class="sxs-lookup"><span data-stu-id="ad757-115">Shared Documentation</span></span>
<span data-ttu-id="ad757-116">WDP는 모든 Windows 10 장치 간에 공유 하는 개발자 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-116">WDP is a developer tool shared among all Windows 10 devices.</span></span> <span data-ttu-id="ad757-117">각 제품에는 자체 고유 기능이 있지만 핵심 기능은 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-117">Each product has its own unique features, but the core functionality is the same.</span></span>
<span data-ttu-id="ad757-118">주요 기능에 대 한 설명서에서 검색 되는 [Windows Device Portal 개요 페이지](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal)합니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-118">Documentation for the main features are found on the [Windows Device Portal overview page](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal).</span></span> <span data-ttu-id="ad757-119">아래 설명서의 나머지 부분에는 특정 IoT 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-119">The rest of the documentation below will be IoT specific.</span></span>

## <a name="set-up"></a><span data-ttu-id="ad757-120">설정</span><span class="sxs-lookup"><span data-stu-id="ad757-120">Set up</span></span>

<span data-ttu-id="ad757-121">Windows Device Portal 시작 및 실행을 이동 하는 방법은 두 가지입니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-121">There are two ways to go get the Windows Device Portal up and running.</span></span>

### <a name="1-windows-10-iot-dashboard"></a><span data-ttu-id="ad757-122">1. Windows 10 IoT 대시보드</span><span class="sxs-lookup"><span data-stu-id="ad757-122">1. Windows 10 IoT Dashboard</span></span>

<span data-ttu-id="ad757-123">다운로드 하려는 먼저 합니다 [Windows 10 IoT 대시보드](https://docs.microsoft.com/en-us/windows/iot-core/connect-your-device/iotdashboard), 새 장치를 쉽게 설치할 수 있도록 하는 개발자 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-123">First, you'll want to download the [Windows 10 IoT Dashboard](https://docs.microsoft.com/en-us/windows/iot-core/connect-your-device/iotdashboard), a developer tool that makes it easy to set up new devices.</span></span> <span data-ttu-id="ad757-124">대시보드에서 장치를 Windows 10 IoT Core 이미지를 사용한 후 장치 "내 장치"에서 표시 되는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-124">Once you've used the Dashboard to flash a Windows 10 IoT Core image onto your device, check that your device shows up under "My devices".</span></span> 

<span data-ttu-id="ad757-125">여기에서 "작업" 아래에 있는 줄임표를 사용 "에서 장치 포털 열기"를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-125">From there, use the ellipses under "Actions" to select "Open in Device Portal".</span></span> <span data-ttu-id="ad757-126">여기에서 있습니다 이동 장치 포털 인증 페이지를 처음에 자격 증명을 변경 하지 않는 한 기본 자격 증명이 있는:</span><span class="sxs-lookup"><span data-stu-id="ad757-126">From there, you'll be taken to the Device Portal authentication page where, unless you changed the credentials initially, the default credentials are:</span></span> 

    Username: `Administrator`<br/>
    Password: `p@ssw0rd`
 
 ### <a name="2-browser"></a><span data-ttu-id="ad757-127">2. 브라우저</span><span class="sxs-lookup"><span data-stu-id="ad757-127">2. Browser</span></span>
<span data-ttu-id="ad757-128">대시보드에서 장치를 찾을 수 없거나 대시보드를 사용 하 여 표시 하지 않으려면 선호를 열 수도 있습니다는 장치 포털 더하기 장치의 IP 주소를 입력 하 여 `:8080` 끝에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-128">If you cannot find your device in the dashboard or prefer to skip using the dashboard, you can also open the Device Portal by entering the IP address of your device plus `:8080` onto the end.</span></span> <span data-ttu-id="ad757-129">올바르게 수행 하는 경우 다음과 같이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-129">When done correctly, it should look something like this:</span></span>


   ![장치 IoTDashboard 보기](../media/deviceportal/Dashboard-Action.gif)

    
## <a name="iot-specific-features"></a><span data-ttu-id="ad757-131">IoT 특정 기능</span><span class="sxs-lookup"><span data-stu-id="ad757-131">IoT specific features</span></span>

### <a name="device-settings"></a><span data-ttu-id="ad757-132">장치 설정</span><span class="sxs-lookup"><span data-stu-id="ad757-132">Device Settings</span></span>

<span data-ttu-id="ad757-133">IoT Core를 사용 하도록 설정 하거나 사용 하지 않도록 설정 하 라는 확인란이 추가 된 [화상 키보드](../develop-your-app/OnScreenKeyboard.md)</span><span class="sxs-lookup"><span data-stu-id="ad757-133">IoT Core adds a checkbox to enable or disable the [on-screen keyboard](../develop-your-app/OnScreenKeyboard.md)</span></span>
> [!NOTE]
> <span data-ttu-id="ad757-134">이 확인란을 선택 되지 않은 확인 여기서 "깜박입니다"에서 알려진된 버그를 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-134">This checkbox has a known bug where it will "flash" from checked to non-checked.</span></span> <span data-ttu-id="ad757-135">확인란을 원하는 상태를 표시 하 고 있는지 확인을 클릭 한 후 f5 키를 눌러 페이지를 새로 고치십시오.</span><span class="sxs-lookup"><span data-stu-id="ad757-135">Please refresh the page (F5) after clicking to ensure that the checkbox is showing your desired state.</span></span>

### <a name="apps"></a><span data-ttu-id="ad757-136">앱</span><span class="sxs-lookup"><span data-stu-id="ad757-136">Apps</span></span>
<span data-ttu-id="ad757-137">AppX 패키지 및 장치에는 번들에 대 한 설치/제거 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-137">Provides install/uninstall functionality for AppX packages and bundles on your device.</span></span>
<span data-ttu-id="ad757-138">![앱 목록](../media/DevicePortal/AppList.png)</span><span class="sxs-lookup"><span data-stu-id="ad757-138">![App list](../media/DevicePortal/AppList.png)</span></span>

<span data-ttu-id="ad757-139">IoT Core는 한 번에 실행할 하나의 전경 앱만 허용 하는 고유 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-139">IoT Core is unique in that it only allows one foreground app to run at one time.</span></span> <span data-ttu-id="ad757-140">앱 목록의 경우 인지 확인 하도록 수정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-140">The app list is modified to ensure that this is the case.</span></span> <span data-ttu-id="ad757-141">아래는 **시작** 열 있습니다 기본적으로 시작 하는 만큼 백그라운드 응용 프로그램을 선택할 수 있지만 하나의 포그라운드 응용 프로그램에만 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-141">Under the **STARTUP** column, you can select as many background applications to start by default, but can only set one foreground application.</span></span>  

### <a name="app-file-explorer"></a><span data-ttu-id="ad757-142">앱 파일 탐색기</span><span class="sxs-lookup"><span data-stu-id="ad757-142">App File Explorer</span></span>

<span data-ttu-id="ad757-143">앱 파일 탐색기를 앱에 액세스할 수 있도록 디렉터리를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-143">The app file explorer shows the directories that your apps can access.</span></span>

* <span data-ttu-id="ad757-144">CameraRoll가 모든 앱 공유</span><span class="sxs-lookup"><span data-stu-id="ad757-144">CameraRoll is shared among all apps</span></span>
* <span data-ttu-id="ad757-145">모든 앱에서 문서 공유</span><span class="sxs-lookup"><span data-stu-id="ad757-145">Documents is shared among all apps</span></span>
* <span data-ttu-id="ad757-146">LocalAppData 각 앱에 특정 폴더를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-146">LocalAppData contains folders specific to each app.</span></span> <span data-ttu-id="ad757-147">이 폴더의 이름은 앱 되며 다른 앱에 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-147">This folder will be the same name as your app and other apps cannot access it.</span></span>

### <a name="debugging"></a><span data-ttu-id="ad757-148">디버깅</span><span class="sxs-lookup"><span data-stu-id="ad757-148">Debugging</span></span>

#### <a name="kernel-dumps"></a><span data-ttu-id="ad757-149">커널 덤프</span><span class="sxs-lookup"><span data-stu-id="ad757-149">Kernel dumps</span></span>
![커널 덤프를 사용 하 여 디버깅](../media/DevicePortal/Debug1.png)

<span data-ttu-id="ad757-151">기록 되 고 웹 관리 도구를 통해 볼 수 있습니다에 자동으로 모든 시스템 작동 중지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-151">Any system crashes will automatically be logged and available to view through the web management tool.</span></span>  <span data-ttu-id="ad757-152">그런 다음 커널 덤프를 다운로드 하 고 진행 상황을 파악 하려고 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-152">You can then download the kernel dump and try to figure out what's going on.</span></span>

#### <a name="process-dumps"></a><span data-ttu-id="ad757-153">프로세스 덤프</span><span class="sxs-lookup"><span data-stu-id="ad757-153">Process dumps</span></span>
![프로세스 덤프를 사용 하 여 디버깅](../media/DevicePortal/Debug2.png)

<span data-ttu-id="ad757-155">와 유사 하지만 사용자 모드 프로세스에 대 한 라이브 커널 덤프 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-155">This is similar to Live kernel dumps, but for the user mode processes.</span></span> <span data-ttu-id="ad757-156">클릭 하 여 **다운로드** 단추 '미니 덤프', 하는 프로세스의 전체 상태 다운로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-156">Clicking the **download** button will cause a 'minidump', and the entire state of that process will be downloaded.</span></span> <span data-ttu-id="ad757-157">중지 프로세스를 디버깅할 때 적합 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-157">This is good for debugging hanging processes.</span></span>

#### <a name="kernel-crash-settings"></a><span data-ttu-id="ad757-158">커널 작동 중단 설정</span><span class="sxs-lookup"><span data-stu-id="ad757-158">Kernel crash settings</span></span>
![커널 작동 중단 설정](../media/DevicePortal/Debug3.png)

### <a name="bluetooth"></a><span data-ttu-id="ad757-160">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="ad757-160">Bluetooth</span></span>
<span data-ttu-id="ad757-161">이 페이지에는 모든 페어링된 bluetooth 장치와 검색할 수 있는 모든 장치가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-161">This page shows you all the bluetooth paired devices and all the devices which are discoverable.</span></span> <span data-ttu-id="ad757-162">다른 Bluetooth 장치 연결, 장치 쌍 모드로 전환 하 고 사용 가능한 장치 목록에 표시 되도록 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-162">To pair with another Bluetooth device, put the device in pairing mode and wait for it to appear in the available devices list.</span></span>  
![Bluetooth 장치 목록](../media/DevicePortal/Bluetooth.png)

<span data-ttu-id="ad757-164">클릭할 **쌍 링크** 장치를 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-164">Click on **Pair link** to pair the device.</span></span> <span data-ttu-id="ad757-165">장치 쌍에서 PIN을 요구 하는 경우 팝업 메시지 상자를 PIN 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-165">If the device requires a PIN for pairing, it will pop-up a message box displaying the PIN.</span></span> <span data-ttu-id="ad757-166">장치 쌍을 이루 면 쌍으로 연결 된 장치 목록에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-166">Once the device is paired, it will show up in the Paired devices list.</span></span> <span data-ttu-id="ad757-167">클릭 하 여 취소 쌍 장치 수 **제거**합니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-167">You can un-pair the device by clicking on **Remove**.</span></span> 

<span data-ttu-id="ad757-168">Bluetooth 페이지로 이동 하면 장치의 다른 장치에서 검색 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-168">Once you navigate to the Bluetooth page, your device will be discoverable by other devices.</span></span> <span data-ttu-id="ad757-169">또한 PC/휴대폰에서 찾을 수 있으며 여기에서 쌍으로 연결.</span><span class="sxs-lookup"><span data-stu-id="ad757-169">You can also find it from your PC/Phone and pair it from there.</span></span>

<span data-ttu-id="ad757-170">Bluetooth에 대 한 자세한 내용은에서 확인할 수 있습니다 합니다 [bluetooth 페이지](https://go.microsoft.com/fwlink/?linkid=823223)합니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-170">More information on bluetooth can be found on the [bluetooth page](https://go.microsoft.com/fwlink/?linkid=823223).</span></span>

### <a name="iot-onboarding"></a><span data-ttu-id="ad757-171">IoT 온 보 딩</span><span class="sxs-lookup"><span data-stu-id="ad757-171">IoT Onboarding</span></span>

<span data-ttu-id="ad757-172">온 보 딩 IoT는 IoT 장치에서 Wi-fi 연결 옵션을 구성 하는 것에 대 한 지원을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-172">IoT Onboarding provides support for configuring an IoT device's Wi-Fi connectivity options.</span></span>

<span data-ttu-id="ad757-173">**인터넷 연결 공유 (ICS)** Wi-fi SoftAP을 통해 장치에 연결 하는 다른 장치를 사용 하 여 장치에 대 한 인터넷 액세스를 공유할 수 있도록 인터넷 연결 공유 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-173">**Internet Connection Sharing (ICS)** Internet Connection Sharing allows you to share the Internet access of your device with other devices connected to your device over the Wi-Fi SoftAP.</span></span>
<span data-ttu-id="ad757-174">이 기능을 사용 하려면 Windows 10 IoT 장치 (예: LAN 통해 유선) 인터넷에 액세스할 수 있도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-174">To use this feature, your Windows 10 IoT Device needs to have access to the internet (e.g. through a wired LAN connection).</span></span>  <span data-ttu-id="ad757-175">' 연결 온 보 딩->-> SoftAP 설정 클릭 'enable' 및 SSID 이름 및 암호를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-175">In 'Connectivity->Onboarding->SoftAP settings' click 'enable' and set SSID name and password.</span></span>  <span data-ttu-id="ad757-176">그런 다음 '연결-> 인터넷 연결 공유' '공유 네트워크 어댑터' 및 '액세스 지점 어댑터' 선택 "Microsoft WI-FI Direct 가상 어댑터 2"에서 유선된 이더넷 어댑터를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-176">Then in 'Connectivity->Internet connection sharing' for 'access point adapter' select "Microsoft Wi-FI Direct Virtual Adapter #2" and for 'shared network adapter' select your wired ethernet adapter.</span></span>  <span data-ttu-id="ad757-177">마지막으로, '공유 액세스를 시작 합니다.'를 클릭합니다</span><span class="sxs-lookup"><span data-stu-id="ad757-177">Finally, click 'start shared access.'</span></span>  <span data-ttu-id="ad757-178">시작 되 면 Windows 10 IoT 장치의 SoftAP 별도 Wi-fi 사용 장치를 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-178">Once started, connect a separate Wi-Fi enabled device to the SoftAP on your Windows 10 IoT device.</span></span>  <span data-ttu-id="ad757-179">연결이 설정 되 면 별도 Wi-fi 사용 장치를 Windows 10 IoT 장치를 통해 인터넷에 연결할 수 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-179">After a connection is established your separate Wi-Fi enabled device will be able to connect to the internet through your Windows 10 IoT device.</span></span>

> [!NOTE]
> <span data-ttu-id="ad757-180">Wi-fi 프로필을 장치에 있는 ICS 비활성화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-180">ICS is disabled when a Wi-Fi profile exists on the device.</span></span> <span data-ttu-id="ad757-181">예를 들어 Wi-fi 액세스 지점에 연결 하 고 "만들기 프로필 (자동 다시 연결)"를 확인 하는 경우 ICS 비활성화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-181">For example, ICS will be disabled if you connect to a Wi-Fi access point and check “Create profile (auto re-connect)”.</span></span>

<span data-ttu-id="ad757-182">**SoftAP 설정을** SoftAP 설정 장치의 SoftAP 사용 하도록 설정할지 여부를 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-182">**SoftAP Settings** The SoftAP Settings allow you to control whether or not your device's SoftAP is enabled.</span></span>  <span data-ttu-id="ad757-183">또한 수단 제공 SoftAP의 구성에 대 한 SSID 및 WPA2-PSK 키 되는 SoftAP 다른 장치에서 연결 하는 데 필요한 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-183">It also provides a means for configuring your SoftAP's SSID and the WPA2-PSK key which are necessary to connect the SoftAP from another device.</span></span>

<span data-ttu-id="ad757-184">**AllJoyn 온 보 딩 설정** The AllJoyn 온 보 딩 설정을 사용 하면 장치에서 Wi-fi 연결 수 여부를 제어 하려면 장치의 AllJoyn 온 보 딩 생산자를 통해 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-184">**AllJoyn Onboarding Settings** The AllJoyn Onboarding Settings allow you to control whether or not your device's Wi-Fi connection can configured through your device's AllJoyn Onboarding Producer.</span></span>  <span data-ttu-id="ad757-185">때 응용 프로그램에 Windows 10 IoT SoftAP 연결할 AllJoyn 온 보 딩 소비자를를 실행 하는 별도 장치를 AllJoyn 온 보 딩 소비자 응용 프로그램에서 IoT 장치의 Wi-fi 어댑터를 구성 하려면 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-185">When a separate device running an AllJoyn Onboarding Consumer application connects to your Windows 10 IoT SoftAP, the AllJoyn Onboarding Consumer application can be used to configure your IoT device's Wi-Fi adapter.</span></span>  <span data-ttu-id="ad757-186">사용 하도록 설정 하면 AllJoyn 온 보 딩 생산자 앱 (IoTOnboarding) ECDHE_NULL 인증 메서드를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-186">When enabled, the AllJoyn Onboarding Producer app (IoTOnboarding) uses the ECDHE_NULL authentication method.</span></span> 

> [!NOTE]
> <span data-ttu-id="ad757-187">AllJoyn 사용 하려면 Windows 10 IoT를 사용 하 여 온 보 딩 10.0.14393 빌드 또는 이전 버전을 업데이트 해야 합니다 <strong>IotOnboarding</strong> 일 수 있는 샘플 [에서 다운로드할](https://github.com/ms-iot/samples)합니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-187">To use AllJoyn Onboarding with Windows 10 IoT builds 10.0.14393 or earlier requires an update to the <strong>IotOnboarding</strong> sample which may be [downloaded here](https://github.com/ms-iot/samples).</span></span>

<span data-ttu-id="ad757-188">![AllJoyn에 온 보 딩](../media/DevicePortal/OnboardingAllJoyn.png)
![ICS에 온 보 딩](../media/DevicePortal/OnboardingICS.png)</span><span class="sxs-lookup"><span data-stu-id="ad757-188">![Onboarding onto AllJoyn](../media/DevicePortal/OnboardingAllJoyn.png)
![Onboarding onto ICS](../media/DevicePortal/OnboardingICS.png)</span></span>

> [!NOTE]
> <span data-ttu-id="ad757-189">액세스 지점 어댑터는 WiFi 어댑터 (일반적으로 있기 192.168.137.1과 같은 IP 주소)가 WiFi 액세스 지점입니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-189">Access point adapter is the WiFi adapter that act as a WiFi access point (it usually has an IP address like 192.168.137.1).</span></span>
> <span data-ttu-id="ad757-190">공유 네트워크 어댑터는 인터넷에 연결 하는 어댑터 (예: 이더넷 어댑터)입니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-190">Shared network adapter is the adapter that connects to Internet (e.g.: Ethernet adapter).</span></span>

![소프트 AP에 온 보 딩](../media/DevicePortal/OnboardingSoftAP.png)

> [!NOTE]
> <span data-ttu-id="ad757-192">SoftAP SSID가 자동으로 붙일 수 "AJ_" AllJoyn 온 보 딩을 활성화 하 고 Wifi 어댑터의 MAC 주소를 사용 하 여 후 위 하는 경우.</span><span class="sxs-lookup"><span data-stu-id="ad757-192">SoftAP SSID will be automatically prefixed by "AJ_" if AllJoyn onboarding is enabled and postfixed with the MAC address of the Wifi adapter.</span></span> <span data-ttu-id="ad757-193">SoftAP 암호는 8 자에서 63 ASCII 자 사이 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-193">The SoftAP passphrase must be between 8 and 63 ASCII characters.</span></span>


### <a name="tpm-configuration"></a><span data-ttu-id="ad757-194">TPM 구성</span><span class="sxs-lookup"><span data-stu-id="ad757-194">TPM configuration</span></span>
<span data-ttu-id="ad757-195">모듈 TPM (Trusted Platform)는 난수 생성, 암호화 키의 보안 생성 및 사용의 제한 사항에 대 한 기능을 포함 하는 암호화 프로세서입니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-195">The Trusted Platform Module (TPM) is a cryptographic coprocessor including capabilities for random number generation, secure generation of cryptographic keys and limitation of their use.</span></span> <span data-ttu-id="ad757-196">또한 원격 증명 및 봉인 된 저장소와 같은 기능을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-196">It also includes capabilities such as remote attestation and sealed storage.</span></span> <span data-ttu-id="ad757-197">TPM 및 보안 IoT Core에 대 한 자세한 내용은 참조는 [보안 장치를 구축](../secure-your-device/BuildingSecureDevices.md) 페이지와 [TPM](../secure-your-device/TPM.md) 페이지.</span><span class="sxs-lookup"><span data-stu-id="ad757-197">To learn about the TPM and security on IoT Core, visit the [Building secure devices](../secure-your-device/BuildingSecureDevices.md) page and the [TPM](../secure-your-device/TPM.md) page.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ad757-198">Windows IoT Core의 일부가 되려면 Limpet.exe 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-198">Limpet.exe used to be part of Windows IoT Core.</span></span> <span data-ttu-id="ad757-199">2018 년 10 월부터,이 제품은 현재에 오픈 소스 프로젝트가 [ https://github.com/ms-iot/azure-dm-client ](https://github.com/ms-iot/azure-dm-client)합니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-199">Starting with October 2018, it is now available as an open source porject at [https://github.com/ms-iot/azure-dm-client](https://github.com/ms-iot/azure-dm-client).</span></span>

<span data-ttu-id="ad757-200">테스트를 보다 쉽게 확인, 서명 되지 않은 미리 작성 된 버전을 사용할 수 있는 Limpet.exe 하 고 WDP에서 바로 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-200">To make testing easier, we have a non-signed pre-built version of Limpet.exe available and can be downloaded right from WDP.</span></span> <span data-ttu-id="ad757-201">' TPM 구성 ' 탭 이동 하 여 최신 설치 ' 단추를 클릭 하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-201">You just need to go the 'TPM Configuration' tab and click the 'Install Latest' button.</span></span> 

> [!NOTE]
> <span data-ttu-id="ad757-202">이 버전의 Limpet.exe 최종 제품을 사용 하 여 제공 되지 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-202">This version of Limpet.exe should not be shipped with your final product.</span></span> <span data-ttu-id="ad757-203">대신, 오픈 소스 프로젝트를 빌드하고, 서명, 이미지를 사용 하 여 패키지를 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-203">Instead, you need to build the open source project, sign it, and package it with your image.</span></span>

### <a name="azure-clients-configuration"></a><span data-ttu-id="ad757-204">Azure 클라이언트 구성</span><span class="sxs-lookup"><span data-stu-id="ad757-204">Azure Clients configuration</span></span>

<span data-ttu-id="ad757-205">클라우드 서비스를 통해 IoT 장치를 원격으로 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-205">IoT devices can be remotely managed through cloud services.</span></span> <span data-ttu-id="ad757-206">Azure는 이러한 시나리오를 사용 하는 서비스는 매우 다양 한 집합을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-206">Azure provides a very rich set of services to enable such scenarios.</span></span> <span data-ttu-id="ad757-207">도 노출 하는 몇 가지 Windows 관리 효율성 기능 및 Windows 플랫폼에서 Azure의 장치 프로 비전 서비스 (DPS) 및 Azure의 IoT Hub 서비스를 보완 하는 장치 관리 클라이언트를 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-207">We have created a device management client that complements Azure's Device Provisioning Service (DPS) and Azure's IoT Hub service on the Windows platform and which also exposes several Windows manageability features.</span></span>

<span data-ttu-id="ad757-208">클라이언트는 오픈 소스 프로젝트로 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-208">The clients will be provided as open source projects.</span></span> <span data-ttu-id="ad757-209">이러한 테스트를 쉽게 미리 작성된 된 이진 파일 제공할 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-209">To make testing them easier, we will be providing pre-built binaries.</span></span> <span data-ttu-id="ad757-210">' Azure 클라이언트 ' 탭을 사용할 수 있습니다 이러한 테스트 이진 파일에서 WDP 설치 하 고 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-210">You can use the 'Azure Clients' tab in WDP to install and run those test binaries.</span></span>

> [!NOTE]
> <span data-ttu-id="ad757-211">최종 제품을 사용 하 여이 버전의 도구를 배송 하지 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-211">This version of the tools should not be shipped with your final product.</span></span> <span data-ttu-id="ad757-212">대신, 오픈 소스 프로젝트를 빌드하고, 서명, 이미지를 사용 하 여 패키지를 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-212">Instead, you need to build the open source project, sign it, and package it with your image.</span></span>

<span data-ttu-id="ad757-213">오픈 소스 프로젝트에 사용할 수 있으면이 설명서를 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-213">We will update this documentation once the open source projects are available for consumption.</span></span>

### <a name="remote"></a><span data-ttu-id="ad757-214">리모컨</span><span class="sxs-lookup"><span data-stu-id="ad757-214">Remote</span></span>
<span data-ttu-id="ad757-215">Windows IoT 원격 서버를 사용 하면 키보드에 실제 모니터를 연결 하지 않고 표시 하는 장치는 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-215">The Windows IoT Remote Server allows users to see what their device is displaying without connecting a physical monitor to the keyboard.</span></span>


## <a name="additional-information"></a><span data-ttu-id="ad757-216">추가 정보</span><span class="sxs-lookup"><span data-stu-id="ad757-216">Additional Information</span></span> 

### <a name="changing-the-default-port"></a><span data-ttu-id="ad757-217">기본 포트를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-217">Changing the default port</span></span>
 
1. <span data-ttu-id="ad757-218">Powershell을 시작 하 고 [장치에 연결 합니다.](../connect-your-device/PowerShell.md)</span><span class="sxs-lookup"><span data-stu-id="ad757-218">Launch powershell and [connect to your device.](../connect-your-device/PowerShell.md)</span></span>
2. <span data-ttu-id="ad757-219">다운로드 [TakeRegistryOwnership](https://github.com/ms-iot/iot-utilities/tree/master/TakeRegistryOwnership) 도구를 빌드하고 장치에 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-219">Download [TakeRegistryOwnership](https://github.com/ms-iot/iot-utilities/tree/master/TakeRegistryOwnership) tool, build it, and copy it to your device.</span></span> 
3. <span data-ttu-id="ad757-220">실행 하 여 서비스에 대 한 레지스트리 키의 소유권 가져오기</span><span class="sxs-lookup"><span data-stu-id="ad757-220">Take ownership of the registry key for the service by running</span></span>

        .\TakeRegistryOwnership.exe MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\webmanagement\service

4. <span data-ttu-id="ad757-221">레지스트리 설정을 수정 하 여 원하는 포트를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-221">Set the desired port by modifying the registry settings</span></span> 

        reg add HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\webmanagement\service /v HttpPort /t REG_DWORD /d <your port number>
        
5. <span data-ttu-id="ad757-222">WebManagement 서비스를 실행 하 여 다음 또는 장치를 다시 시작 하 여 다시 시작</span><span class="sxs-lookup"><span data-stu-id="ad757-222">Restart the WebManagement service by running following or by restarting the device</span></span>

        net stop webmanagement ; net start webmanagement

### <a name="using-https"></a><span data-ttu-id="ad757-223">HTTPS를 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="ad757-223">Using HTTPS</span></span> 

<span data-ttu-id="ad757-224">HTTPS를 사용 하려는 경우 먼저 이전 섹션에 설명 된 대로 레지스트리 키의 소유권을 수행 및 아래와 같이 HttpsPort 및 EncryptionMode 레지스트리 키를 설정 하 고 webmanagement 서비스를 다시 시작</span><span class="sxs-lookup"><span data-stu-id="ad757-224">If you want to use HTTPS, first take the ownership of the registry key as described in previous section and set the HttpsPort and EncryptionMode registry keys as below and then restart the webmanagement service</span></span>

        reg add HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\webmanagement\service /v EncryptionMode /t REG_DWORD /d 0x3 /f
        reg add HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\webmanagement\service /v HttpsPort /t REG_DWORD /d <your port number> /f
        net stop webmanagement ; net start webmanagement

### <a name="provisoning-device-portal-with-a-custom-ssl-certificate"></a><span data-ttu-id="ad757-225">사용자 지정 SSL 인증서를 사용 하 여 프로 비전 장치 포털</span><span class="sxs-lookup"><span data-stu-id="ad757-225">Provisoning Device Portal with a custom SSL certificate</span></span>

<span data-ttu-id="ad757-226">Windows 10 크리에이터 업데이트 Windows Device Portal HTTPS 통신에 사용 하기 위해 사용자 지정 인증서를 설치 하려면 장치 관리자를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-226">In the Windows 10 Creators Update, the Windows Device Portal added a way for device administrators to install a custom certificate for use in HTTPS communication.</span></span>

<span data-ttu-id="ad757-227">자세한 내용은 [Windows Device Portal 문서에 있는 설명서를 읽을](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-ssl)합니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-227">To learn more, [read the documentation under the Windows Device Portal docs](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-ssl).</span></span> 

### <a name="crash-dump-settings-for-capturing-memory-dump"></a><span data-ttu-id="ad757-228">덤프 설정은 메모리 덤프 캡처에 대 한 충돌 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-228">Crash Dump Settings for Capturing Memory Dump:</span></span>

<span data-ttu-id="ad757-229">전체 메모리 덤프를 캡처하려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-229">To capture a Full Memory Dump, do the following:</span></span>

1. <span data-ttu-id="ad757-230">WDP 통해 IoT 장치에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-230">Connect to a IoT device through WDP.</span></span>

2. <span data-ttu-id="ad757-231">디버그에서 설정-> 디버그-> 커널 크래시 설정-크래시 덤프 유형 >입니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-231">From Debug -> Debug settings -> Kernel crash settings -> Crash dump type.</span></span> 

3. <span data-ttu-id="ad757-232">선택: 사용 하 여 메모리의 메모리 덤프를 완료 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-232">Select: Complete memory dump (in use memory).</span></span>
    <span data-ttu-id="ad757-233">장치 설정을 적용 하려면 다시 부팅 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-233">Make sure the device is rebooted for the setting to take effect.</span></span> 
    
4. <span data-ttu-id="ad757-234">확인 `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\CrashControl\CrashDumpEnabled` 0x1로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-234">Verify  that `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\CrashControl\CrashDumpEnabled` is set to 0x1.</span></span>

5. <span data-ttu-id="ad757-235">업데이트 `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\CrashControl\DumpFileSize` 0x0을 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-235">Update `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\CrashControl\DumpFileSize` to 0x0.</span></span>

6. <span data-ttu-id="ad757-236">이 덤프 생성에 대 한 장치에 충분 한 공간이 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad757-236">Make sure you have enough space on the device for this Dump to be generated.</span></span> <span data-ttu-id="ad757-237">여기에서 변경 된 덤프 파일 위치를 구성할 수 있습니다. `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\CrashControl\DumpFile`</span><span class="sxs-lookup"><span data-stu-id="ad757-237">You can configure the changing the DumpFile location from here: `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\CrashControl\DumpFile`</span></span>


## <a name="additional-resources"></a><span data-ttu-id="ad757-238">추가 리소스</span><span class="sxs-lookup"><span data-stu-id="ad757-238">Additional Resources</span></span>
___ 

1. [<span data-ttu-id="ad757-239">Windows Device Portal 개요 페이지</span><span class="sxs-lookup"><span data-stu-id="ad757-239">Windows Device Portal overview page</span></span>](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal)
