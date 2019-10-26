---
title: Windows Device Portal
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: Windows 장치 포털을 사용 하 여 장치를 원격으로 구성 하 고 관리 하는 방법에 대해 알아봅니다.
keywords: windows iot, Windows 장치 포털, 원격, 장치 포털
ms.openlocfilehash: d7e5285b7a29a61f15a5272cc822832230e56f75
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72917440"
---
# <a name="windows-device-portal"></a><span data-ttu-id="5cfa7-104">Windows Device Portal</span><span class="sxs-lookup"><span data-stu-id="5cfa7-104">Windows Device Portal</span></span>
   <span data-ttu-id="5cfa7-105">Windows 장치 포털 (WDP)을 사용 하 여 로컬 네트워크를 통해 원격으로 장치를 구성 하 고 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-105">The Windows Device Portal (WDP) lets you configure and manage your device remotely over your local network.</span></span>
<span data-ttu-id="5cfa7-106">주요 기능은 [Windows 장치 포털 개요 페이지](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal) 에 설명 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-106">The main features are documented on the [Windows Device Portal overview page](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal)</span></span>

![장치 포털 홈](../media/deviceportal/deviceportal.png)

> [!IMPORTANT]
> <span data-ttu-id="5cfa7-108">상용화에 제조사 이미지를 사용하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-108">Do not use maker images for commercialization.</span></span> <span data-ttu-id="5cfa7-109">디바이스를 상용화하려는 경우 최적의 보안을 위해 사용자 지정 FFU를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-109">If you are commercializing a device, you must use a custom FFU for optimal security.</span></span> <span data-ttu-id="5cfa7-110">[여기](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)에서 자세한 내용을 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-110">Learn more [here](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).</span></span>

> [!WARNING]
> <span data-ttu-id="5cfa7-111">라이브 커널 디버그가 현재 ARM 장치에 대해 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-111">Live kernel debug is currently failing for ARM devices.</span></span> <span data-ttu-id="5cfa7-112">이 문제를 해결 하기 위해 노력 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-112">We are working to get this fixed.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5cfa7-113">최종 사용자가 최종 구성을 수행 하 고 고객에 게 [WDP에 대 한 인증서를 얻어야 하는 고객을 문서화 하는 "특정/제한 된 설치" (즉, 공장 또는 소매점)에 대해 상용 배포를 위한 오픈 정품 장치를 구축 하는 경우 그리고 WDP에 설치 하 고 브라우저와 암호를 연결 하면 WDP에서](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-ssl)WDP를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-113">If you are building an open retail device for commercial deployment to a "specific/limited installation" (i.e. factory or retail store) where the end-user does the final configuration and you document your customers that they must [obtain a certificate for WDP and install it on both WDP and connecting browsers and passwords are changed on WDP](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-ssl), then using WDP in this narrow commercial instance is acceptable.</span></span> <span data-ttu-id="5cfa7-114">이 시나리오에서 소매점 이미지는 여전히 IOT_TOOLKIT를 포함 *하지* 않지만 IOT_WEBBEXTN 패키지를 사용 하 여 WDP로 가져와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-114">Retail images in this scenario should still *not* include IOT_TOOLKIT, but should use the IOT_WEBBEXTN package to pull in WDP.</span></span> 

## <a name="shared-documentation"></a><span data-ttu-id="5cfa7-115">공유 설명서</span><span class="sxs-lookup"><span data-stu-id="5cfa7-115">Shared Documentation</span></span>
<span data-ttu-id="5cfa7-116">WDP는 모든 Windows 10 장치에서 공유 되는 개발자 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-116">WDP is a developer tool shared among all Windows 10 devices.</span></span> <span data-ttu-id="5cfa7-117">각 제품에는 고유한 기능이 있지만 핵심 기능은 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-117">Each product has its own unique features, but the core functionality is the same.</span></span>
<span data-ttu-id="5cfa7-118">주요 기능에 대 한 설명서는 [Windows 장치 포털 개요 페이지](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal)에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-118">Documentation for the main features are found on the [Windows Device Portal overview page](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal).</span></span> <span data-ttu-id="5cfa7-119">아래 설명서의 나머지 부분은 IoT 관련 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-119">The rest of the documentation below will be IoT specific.</span></span>

## <a name="set-up"></a><span data-ttu-id="5cfa7-120">설정</span><span class="sxs-lookup"><span data-stu-id="5cfa7-120">Set up</span></span>

<span data-ttu-id="5cfa7-121">Windows 장치 포털을 시작 하 고 실행 하는 방법에는 두 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-121">There are two ways to go get the Windows Device Portal up and running.</span></span>

### <a name="1-windows-10-iot-dashboard"></a><span data-ttu-id="5cfa7-122">1. Windows 10 IoT 대시보드</span><span class="sxs-lookup"><span data-stu-id="5cfa7-122">1. Windows 10 IoT Dashboard</span></span>

<span data-ttu-id="5cfa7-123">먼저 새 장치를 쉽게 설정할 수 있도록 하는 개발자 도구인 [Windows 10 IoT 대시보드](https://docs.microsoft.com/en-us/windows/iot-core/connect-your-device/iotdashboard)를 다운로드 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-123">First, you'll want to download the [Windows 10 IoT Dashboard](https://docs.microsoft.com/en-us/windows/iot-core/connect-your-device/iotdashboard), a developer tool that makes it easy to set up new devices.</span></span> <span data-ttu-id="5cfa7-124">대시보드를 사용 하 여 Windows 10 IoT Core 이미지를 장치에 플래시 한 후 장치가 "내 장치" 아래에 표시 되는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-124">Once you've used the Dashboard to flash a Windows 10 IoT Core image onto your device, check that your device shows up under "My devices".</span></span> 

<span data-ttu-id="5cfa7-125">여기에서 "작업" 아래에 있는 줄임표를 사용 하 여 "장치 포털에서 열기"를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-125">From there, use the ellipses under "Actions" to select "Open in Device Portal".</span></span> <span data-ttu-id="5cfa7-126">여기서는 처음에 자격 증명을 변경 하지 않은 경우 기본 자격 증명을 사용 하 여 장치 포털 인증 페이지로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-126">From there, you'll be taken to the Device Portal authentication page where, unless you changed the credentials initially, the default credentials are:</span></span> 

    Username: `Administrator`<br/>
    Password: `p@ssw0rd`
 
 ### <a name="2-browser"></a><span data-ttu-id="5cfa7-127">2. 브라우저</span><span class="sxs-lookup"><span data-stu-id="5cfa7-127">2. Browser</span></span>
<span data-ttu-id="5cfa7-128">대시보드에서 장치를 찾을 수 없거나 대시보드 사용을 건너뛰도록 선호 하는 경우 장치의 IP 주소를 입력 하 고 끝에 `:8080` 하 여 장치 포털을 열 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-128">If you cannot find your device in the dashboard or prefer to skip using the dashboard, you can also open the Device Portal by entering the IP address of your device plus `:8080` onto the end.</span></span> <span data-ttu-id="5cfa7-129">올바르게 수행 되 면 다음과 같이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-129">When done correctly, it should look something like this:</span></span>


   ![I이상 대시보드 보기 장치](../media/deviceportal/Dashboard-Action.gif)

    
## <a name="iot-specific-features"></a><span data-ttu-id="5cfa7-131">IoT 관련 기능</span><span class="sxs-lookup"><span data-stu-id="5cfa7-131">IoT specific features</span></span>

### <a name="device-settings"></a><span data-ttu-id="5cfa7-132">장치 설정</span><span class="sxs-lookup"><span data-stu-id="5cfa7-132">Device Settings</span></span>

<span data-ttu-id="5cfa7-133">IoT Core는 [화상 키보드](../develop-your-app/OnScreenKeyboard.md) 를 사용 하거나 사용 하지 않도록 확인란을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-133">IoT Core adds a checkbox to enable or disable the [on-screen keyboard](../develop-your-app/OnScreenKeyboard.md)</span></span>
> [!NOTE]
> <span data-ttu-id="5cfa7-134">이 확인란은 선택 된 상태에서 선택 되지 않은 것으로 "flash"가 되는 알려진 버그를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-134">This checkbox has a known bug where it will "flash" from checked to non-checked.</span></span> <span data-ttu-id="5cfa7-135">확인란이 원하는 상태를 표시 하는지 확인 하려면 클릭 한 후 페이지를 새로 고칩니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-135">Please refresh the page (F5) after clicking to ensure that the checkbox is showing your desired state.</span></span>

### <a name="apps"></a><span data-ttu-id="5cfa7-136">앱을 선택하고</span><span class="sxs-lookup"><span data-stu-id="5cfa7-136">Apps</span></span>
<span data-ttu-id="5cfa7-137">장치에서 AppX 패키지 및 번들에 대 한 설치/제거 기능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-137">Provides install/uninstall functionality for AppX packages and bundles on your device.</span></span>
<span data-ttu-id="5cfa7-138">앱 목록 ![](../media/DevicePortal/AppList.png)</span><span class="sxs-lookup"><span data-stu-id="5cfa7-138">![App list](../media/DevicePortal/AppList.png)</span></span>

<span data-ttu-id="5cfa7-139">IoT Core는 한 번에 하나의 포그라운드 앱만 실행할 수 있다는 면에서 고유 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-139">IoT Core is unique in that it only allows one foreground app to run at one time.</span></span> <span data-ttu-id="5cfa7-140">이 경우 앱 목록이 수정 되어이를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-140">The app list is modified to ensure that this is the case.</span></span> <span data-ttu-id="5cfa7-141">**시작** 열에서 기본적으로 시작할 백그라운드 응용 프로그램 수를 선택할 수 있지만 전경 응용 프로그램은 하나만 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-141">Under the **STARTUP** column, you can select as many background applications to start by default, but can only set one foreground application.</span></span>  

### <a name="app-file-explorer"></a><span data-ttu-id="5cfa7-142">앱 파일 탐색기</span><span class="sxs-lookup"><span data-stu-id="5cfa7-142">App File Explorer</span></span>

<span data-ttu-id="5cfa7-143">앱 파일 탐색기에는 앱이 액세스할 수 있는 디렉터리가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-143">The app file explorer shows the directories that your apps can access.</span></span>

* <span data-ttu-id="5cfa7-144">CameraRoll는 모든 앱에서 공유 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-144">CameraRoll is shared among all apps</span></span>
* <span data-ttu-id="5cfa7-145">문서는 모든 앱에서 공유 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-145">Documents is shared among all apps</span></span>
* <span data-ttu-id="5cfa7-146">LocalAppData에는 각 앱에 해당 하는 폴더가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-146">LocalAppData contains folders specific to each app.</span></span> <span data-ttu-id="5cfa7-147">이 폴더는 앱과 이름이 같으며 다른 앱은 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-147">This folder will be the same name as your app and other apps cannot access it.</span></span>

### <a name="debugging"></a><span data-ttu-id="5cfa7-148">디버깅</span><span class="sxs-lookup"><span data-stu-id="5cfa7-148">Debugging</span></span>

#### <a name="kernel-dumps"></a><span data-ttu-id="5cfa7-149">커널 덤프</span><span class="sxs-lookup"><span data-stu-id="5cfa7-149">Kernel dumps</span></span>
![커널 덤프를 사용 하 여 디버깅](../media/DevicePortal/Debug1.png)

<span data-ttu-id="5cfa7-151">모든 시스템 크래시는 자동으로 기록 되 고 웹 관리 도구를 통해 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-151">Any system crashes will automatically be logged and available to view through the web management tool.</span></span>  <span data-ttu-id="5cfa7-152">그런 다음 커널 덤프를 다운로드 하 고 진행 상황을 파악할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-152">You can then download the kernel dump and try to figure out what's going on.</span></span>

#### <a name="process-dumps"></a><span data-ttu-id="5cfa7-153">덤프 처리</span><span class="sxs-lookup"><span data-stu-id="5cfa7-153">Process dumps</span></span>
![프로세스 덤프를 사용 하 여 디버깅](../media/DevicePortal/Debug2.png)

<span data-ttu-id="5cfa7-155">이는 라이브 커널 덤프와 유사 하지만 사용자 모드 프로세스의 경우입니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-155">This is similar to Live kernel dumps, but for the user mode processes.</span></span> <span data-ttu-id="5cfa7-156">**다운로드** 단추를 클릭 하면 ' 미니 덤프 '가 발생 하 고 해당 프로세스의 전체 상태가 다운로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-156">Clicking the **download** button will cause a 'minidump', and the entire state of that process will be downloaded.</span></span> <span data-ttu-id="5cfa7-157">이는 분기 프로세스를 디버깅 하는 데 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-157">This is good for debugging hanging processes.</span></span>

#### <a name="kernel-crash-settings"></a><span data-ttu-id="5cfa7-158">커널 충돌 설정</span><span class="sxs-lookup"><span data-stu-id="5cfa7-158">Kernel crash settings</span></span>
![커널 충돌 설정](../media/DevicePortal/Debug3.png)

### <a name="bluetooth"></a><span data-ttu-id="5cfa7-160">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="5cfa7-160">Bluetooth</span></span>
<span data-ttu-id="5cfa7-161">이 페이지에는 모든 bluetooth 페어링 장치와 검색 가능한 모든 장치가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-161">This page shows you all the bluetooth paired devices and all the devices which are discoverable.</span></span> <span data-ttu-id="5cfa7-162">다른 Bluetooth 장치와 페어링 하려면 장치를 페어링 모드로 전환 하 고 사용 가능한 장치 목록에 표시 될 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-162">To pair with another Bluetooth device, put the device in pairing mode and wait for it to appear in the available devices list.</span></span>  
![Bluetooth 장치 목록](../media/DevicePortal/Bluetooth.png)

<span data-ttu-id="5cfa7-164">**페어링 링크** 를 클릭 하 여 장치를 페어링 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-164">Click on **Pair link** to pair the device.</span></span> <span data-ttu-id="5cfa7-165">장치에서 페어링을 위해 PIN을 요구 하는 경우 PIN을 표시 하는 메시지 상자가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-165">If the device requires a PIN for pairing, it will pop-up a message box displaying the PIN.</span></span> <span data-ttu-id="5cfa7-166">장치가 페어링된 후 페어링 된 장치 목록에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-166">Once the device is paired, it will show up in the Paired devices list.</span></span> <span data-ttu-id="5cfa7-167">**제거**를 클릭 하 여 장치 쌍을 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-167">You can un-pair the device by clicking on **Remove**.</span></span> 

<span data-ttu-id="5cfa7-168">Bluetooth 페이지로 이동 하면 다른 장치에서 장치를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-168">Once you navigate to the Bluetooth page, your device will be discoverable by other devices.</span></span> <span data-ttu-id="5cfa7-169">또한 PC/휴대폰에서 해당 파일을 찾아 쌍으로 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-169">You can also find it from your PC/Phone and pair it from there.</span></span>

<span data-ttu-id="5cfa7-170">Bluetooth에 대 한 자세한 내용은 [bluetooth 페이지](https://go.microsoft.com/fwlink/?linkid=823223)에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-170">More information on bluetooth can be found on the [bluetooth page](https://go.microsoft.com/fwlink/?linkid=823223).</span></span>

### <a name="iot-onboarding"></a><span data-ttu-id="5cfa7-171">IoT 온 보 딩</span><span class="sxs-lookup"><span data-stu-id="5cfa7-171">IoT Onboarding</span></span>

<span data-ttu-id="5cfa7-172">IoT 온 보 딩은 IoT 장치의 Wi-fi 연결 옵션을 구성 하는 기능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-172">IoT Onboarding provides support for configuring an IoT device's Wi-Fi connectivity options.</span></span>

<span data-ttu-id="5cfa7-173">**ICS (인터넷 연결 공유)** 인터넷 연결 공유를 사용 하면 Wi-fi SoftAP에서 장치에 연결 된 다른 장치와 장치의 인터넷 액세스를 공유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-173">**Internet Connection Sharing (ICS)** Internet Connection Sharing allows you to share the Internet access of your device with other devices connected to your device over the Wi-Fi SoftAP.</span></span>
<span data-ttu-id="5cfa7-174">이 기능을 사용 하려면 Windows 10 IoT 장치에서 인터넷에 액세스할 수 있어야 합니다 (예: 유선 LAN 연결을 통해).</span><span class="sxs-lookup"><span data-stu-id="5cfa7-174">To use this feature, your Windows 10 IoT Device needs to have access to the internet (e.g. through a wired LAN connection).</span></span>  <span data-ttu-id="5cfa7-175">' 연결-> 온 보 딩-> SoftAP 설정 '에서 ' 사용 '을 클릭 하 고 SSID 이름과 암호를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-175">In 'Connectivity->Onboarding->SoftAP settings' click 'enable' and set SSID name and password.</span></span>  <span data-ttu-id="5cfa7-176">그런 다음 ' 연결-> 인터넷 연결 공유 '에서 ' 액세스 지점 어댑터 '를 선택 하 고, ' Microsoft Wi-fi 직접 가상 어댑터 #2 "를 선택 하 고, ' 공유 네트워크 어댑터 '에서 유선 이더넷 어댑터를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-176">Then in 'Connectivity->Internet connection sharing' for 'access point adapter' select "Microsoft Wi-FI Direct Virtual Adapter #2" and for 'shared network adapter' select your wired ethernet adapter.</span></span>  <span data-ttu-id="5cfa7-177">마지막으로 ' 공유 액세스 시작 '을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-177">Finally, click 'start shared access.'</span></span>  <span data-ttu-id="5cfa7-178">시작 되 면 별도의 Wi-fi 사용 장치를 Windows 10 IoT 장치의 SoftAP에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-178">Once started, connect a separate Wi-Fi enabled device to the SoftAP on your Windows 10 IoT device.</span></span>  <span data-ttu-id="5cfa7-179">연결이 설정 되 면 별도의 Wi-fi 사용 장치에서 Windows 10 IoT 장치를 통해 인터넷에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-179">After a connection is established your separate Wi-Fi enabled device will be able to connect to the internet through your Windows 10 IoT device.</span></span>

> [!NOTE]
> <span data-ttu-id="5cfa7-180">Wi-fi 프로필이 장치에 있는 경우 ICS를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-180">ICS is disabled when a Wi-Fi profile exists on the device.</span></span> <span data-ttu-id="5cfa7-181">예를 들어 Wi-fi 액세스 지점에 연결 하 고 "프로필 만들기 (자동 다시 연결)"를 선택 하는 경우 ICS를 사용 하지 않도록 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-181">For example, ICS will be disabled if you connect to a Wi-Fi access point and check “Create profile (auto re-connect)”.</span></span>

<span data-ttu-id="5cfa7-182">**SoftAP 설정** SoftAP 설정을 사용 하 여 장치의 SoftAP 사용 여부를 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-182">**SoftAP Settings** The SoftAP Settings allow you to control whether or not your device's SoftAP is enabled.</span></span>  <span data-ttu-id="5cfa7-183">또한 다른 장치에서 SoftAP를 연결 하는 데 필요한 SoftAP의 SSID와 WPA2-PSK 키를 구성 하는 수단을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-183">It also provides a means for configuring your SoftAP's SSID and the WPA2-PSK key which are necessary to connect the SoftAP from another device.</span></span>

<span data-ttu-id="5cfa7-184">**AllJoyn 온 보 딩 설정** AllJoyn 온 보 딩 설정을 사용 하 여 장치의 AllJoyn 등록 생산자를 통해 장치의 Wi-fi 연결을 구성할 수 있는지 여부를 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-184">**AllJoyn Onboarding Settings** The AllJoyn Onboarding Settings allow you to control whether or not your device's Wi-Fi connection can configured through your device's AllJoyn Onboarding Producer.</span></span>  <span data-ttu-id="5cfa7-185">AllJoyn 온 보 딩 소비자 응용 프로그램을 실행 하는 별도 장치에서 Windows 10 IoT SoftAP에 연결 하는 경우 AllJoyn 온 보 딩 소비자 응용 프로그램을 사용 하 여 IoT 장치의 Wi-fi 어댑터를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-185">When a separate device running an AllJoyn Onboarding Consumer application connects to your Windows 10 IoT SoftAP, the AllJoyn Onboarding Consumer application can be used to configure your IoT device's Wi-Fi adapter.</span></span>  <span data-ttu-id="5cfa7-186">이 기능을 사용 하도록 설정 하면 ECDHE_NULL 인증 방법을 사용 하는 AllJoyn 온 보 딩 생산자 앱</span><span class="sxs-lookup"><span data-stu-id="5cfa7-186">When enabled, the AllJoyn Onboarding Producer app (IoTOnboarding) uses the ECDHE_NULL authentication method.</span></span> 

> [!NOTE]
> <span data-ttu-id="5cfa7-187">Windows 10 IoT 빌드에서 10.0.14393 또는 이전 버전을 사용 하려면 [여기에서 다운로드할](https://github.com/ms-iot/samples)수 있는 <strong>iotonboarding 보 딩</strong> 샘플에 대 한 업데이트가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-187">To use AllJoyn Onboarding with Windows 10 IoT builds 10.0.14393 or earlier requires an update to the <strong>IotOnboarding</strong> sample which may be [downloaded here](https://github.com/ms-iot/samples).</span></span>

<span data-ttu-id="5cfa7-188">](../media/DevicePortal/OnboardingAllJoyn.png)
![를 통해 ![에 온 보 딩에 온 보 딩](../media/DevicePortal/OnboardingICS.png)</span><span class="sxs-lookup"><span data-stu-id="5cfa7-188">![Onboarding onto AllJoyn](../media/DevicePortal/OnboardingAllJoyn.png)
![Onboarding onto ICS](../media/DevicePortal/OnboardingICS.png)</span></span>

> [!NOTE]
> <span data-ttu-id="5cfa7-189">액세스 지점 어댑터는 WiFi 액세스 지점 역할을 하는 WiFi 어댑터 이며 일반적으로 192.168.137.1와 같은 IP 주소가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-189">Access point adapter is the WiFi adapter that act as a WiFi access point (it usually has an IP address like 192.168.137.1).</span></span>
> <span data-ttu-id="5cfa7-190">공유 네트워크 어댑터는 인터넷 (예: 이더넷 어댑터)에 연결 되는 어댑터입니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-190">Shared network adapter is the adapter that connects to Internet (e.g.: Ethernet adapter).</span></span>

![소프트 AP로 등록](../media/DevicePortal/OnboardingSoftAP.png)

> [!NOTE]
> <span data-ttu-id="5cfa7-192">SoftAP SSID는 AllJoyn 등록을 사용 하도록 설정 하 고, Wifi 어댑터의 MAC 주소를 사용 하 여 되도록 후 위를 사용 하는 경우 "AJ_"로 자동 접두사가 붙습니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-192">SoftAP SSID will be automatically prefixed by "AJ_" if AllJoyn onboarding is enabled and postfixed with the MAC address of the Wifi adapter.</span></span> <span data-ttu-id="5cfa7-193">SoftAP 암호는 8 ~ 007e; 63 ASCII 문자 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-193">The SoftAP passphrase must be between 8 and 63 ASCII characters.</span></span>


### <a name="tpm-configuration"></a><span data-ttu-id="5cfa7-194">TPM 구성</span><span class="sxs-lookup"><span data-stu-id="5cfa7-194">TPM configuration</span></span>
<span data-ttu-id="5cfa7-195">TPM (신뢰할 수 있는 플랫폼 모듈)은 난수 생성, 암호화 키의 보안 생성 및 사용 제한에 대 한 기능을 포함 하는 암호화 보조 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-195">The Trusted Platform Module (TPM) is a cryptographic coprocessor including capabilities for random number generation, secure generation of cryptographic keys and limitation of their use.</span></span> <span data-ttu-id="5cfa7-196">또한 원격 증명 및 봉인 된 저장소와 같은 기능을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-196">It also includes capabilities such as remote attestation and sealed storage.</span></span> <span data-ttu-id="5cfa7-197">IoT Core의 TPM 및 보안에 대 한 자세한 내용은 [보안 장치 구축](../secure-your-device/BuildingSecureDevices.md) 페이지 및 [tpm](../secure-your-device/TPM.md) 페이지를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-197">To learn about the TPM and security on IoT Core, visit the [Building secure devices](../secure-your-device/BuildingSecureDevices.md) page and the [TPM](../secure-your-device/TPM.md) page.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5cfa7-198">Limpet는 Windows IoT Core의 일부로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-198">Limpet.exe used to be part of Windows IoT Core.</span></span> <span data-ttu-id="5cfa7-199">2018 년 10 월부터 이제 [https://github.com/ms-iot/azure-dm-client](https://github.com/ms-iot/azure-dm-client)에서 오픈 소스로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-199">Starting with October 2018, it is now available as an open source porject at [https://github.com/ms-iot/azure-dm-client](https://github.com/ms-iot/azure-dm-client).</span></span>

<span data-ttu-id="5cfa7-200">테스트를 용이 하 게 하기 위해 Limpet의 서명 되지 않은 미리 작성 된 버전을 사용할 수 있으며 WDP에서 바로 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-200">To make testing easier, we have a non-signed pre-built version of Limpet.exe available and can be downloaded right from WDP.</span></span> <span data-ttu-id="5cfa7-201">' TPM 구성 ' 탭으로 이동 하 여 ' 최신 버전 설치 ' 단추를 클릭 하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-201">You just need to go the 'TPM Configuration' tab and click the 'Install Latest' button.</span></span> 

> [!NOTE]
> <span data-ttu-id="5cfa7-202">이 버전의 Limpet를 최종 제품과 함께 제공 해서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-202">This version of Limpet.exe should not be shipped with your final product.</span></span> <span data-ttu-id="5cfa7-203">대신 오픈 소스 프로젝트를 빌드하고, 서명 하 고, 이미지를 사용 하 여 패키지 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-203">Instead, you need to build the open source project, sign it, and package it with your image.</span></span>

### <a name="azure-clients-configuration"></a><span data-ttu-id="5cfa7-204">Azure 클라이언트 구성</span><span class="sxs-lookup"><span data-stu-id="5cfa7-204">Azure Clients configuration</span></span>

<span data-ttu-id="5cfa7-205">IoT 장치는 클라우드 서비스를 통해 원격으로 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-205">IoT devices can be remotely managed through cloud services.</span></span> <span data-ttu-id="5cfa7-206">Azure는 이러한 시나리오를 가능 하 게 해 주는 매우 다양 한 서비스 집합을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-206">Azure provides a very rich set of services to enable such scenarios.</span></span> <span data-ttu-id="5cfa7-207">Microsoft는 Windows 플랫폼에서 Azure의 DPS (장치 프로 비전 서비스)와 Azure의 IoT Hub 서비스를 보완 하 고 몇 가지 Windows 관리 효율성 기능을 노출 하는 장치 관리 클라이언트를 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-207">We have created a device management client that complements Azure's Device Provisioning Service (DPS) and Azure's IoT Hub service on the Windows platform and which also exposes several Windows manageability features.</span></span>

<span data-ttu-id="5cfa7-208">클라이언트는 오픈 소스 프로젝트로 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-208">The clients will be provided as open source projects.</span></span> <span data-ttu-id="5cfa7-209">테스트를 더 쉽게 수행 하기 위해 미리 작성 된 이진 파일을 제공할 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-209">To make testing them easier, we will be providing pre-built binaries.</span></span> <span data-ttu-id="5cfa7-210">WDP에서 ' Azure 클라이언트 ' 탭을 사용 하 여 해당 테스트 바이너리를 설치 하 고 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-210">You can use the 'Azure Clients' tab in WDP to install and run those test binaries.</span></span>

> [!NOTE]
> <span data-ttu-id="5cfa7-211">이 버전의 도구를 최종 제품과 함께 제공 해서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-211">This version of the tools should not be shipped with your final product.</span></span> <span data-ttu-id="5cfa7-212">대신 오픈 소스 프로젝트를 빌드하고, 서명 하 고, 이미지를 사용 하 여 패키지 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-212">Instead, you need to build the open source project, sign it, and package it with your image.</span></span>

<span data-ttu-id="5cfa7-213">오픈 소스 프로젝트를 사용할 수 있게 되 면이 설명서를 업데이트할 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-213">We will update this documentation once the open source projects are available for consumption.</span></span>

### <a name="remote"></a><span data-ttu-id="5cfa7-214">리모컨</span><span class="sxs-lookup"><span data-stu-id="5cfa7-214">Remote</span></span>
<span data-ttu-id="5cfa7-215">사용자는 Windows IoT 원격 서버를 사용 하 여 실제 모니터를 키보드에 연결 하지 않고도 장치에 표시 되는 항목을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-215">The Windows IoT Remote Server allows users to see what their device is displaying without connecting a physical monitor to the keyboard.</span></span>


## <a name="additional-information"></a><span data-ttu-id="5cfa7-216">추가 정보</span><span class="sxs-lookup"><span data-stu-id="5cfa7-216">Additional Information</span></span> 

### <a name="changing-the-default-port"></a><span data-ttu-id="5cfa7-217">기본 포트 변경</span><span class="sxs-lookup"><span data-stu-id="5cfa7-217">Changing the default port</span></span>
 
1. <span data-ttu-id="5cfa7-218">Powershell을 시작 하 고 [장치에 연결 합니다.](../connect-your-device/PowerShell.md)</span><span class="sxs-lookup"><span data-stu-id="5cfa7-218">Launch powershell and [connect to your device.](../connect-your-device/PowerShell.md)</span></span>
2. <span data-ttu-id="5cfa7-219">[TakeRegistryOwnership](https://github.com/ms-iot/iot-utilities/tree/master/TakeRegistryOwnership) 도구를 다운로드 하 고 빌드하고 장치에 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-219">Download [TakeRegistryOwnership](https://github.com/ms-iot/iot-utilities/tree/master/TakeRegistryOwnership) tool, build it, and copy it to your device.</span></span> 
3. <span data-ttu-id="5cfa7-220">을 실행 하 여 서비스에 대 한 레지스트리 키의 소유권 가져오기</span><span class="sxs-lookup"><span data-stu-id="5cfa7-220">Take ownership of the registry key for the service by running</span></span>

        .\TakeRegistryOwnership.exe MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\webmanagement\service

4. <span data-ttu-id="5cfa7-221">레지스트리 설정을 수정 하 여 원하는 포트를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-221">Set the desired port by modifying the registry settings</span></span> 

        reg add HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\webmanagement\service /v HttpPort /t REG_DWORD /d <your port number>
        
5. <span data-ttu-id="5cfa7-222">다음을 실행 하거나 장치를 다시 시작 하 여 WebManagement 서비스를 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-222">Restart the WebManagement service by running following or by restarting the device</span></span>

        net stop webmanagement ; net start webmanagement

### <a name="using-https"></a><span data-ttu-id="5cfa7-223">HTTPS 사용</span><span class="sxs-lookup"><span data-stu-id="5cfa7-223">Using HTTPS</span></span> 

<span data-ttu-id="5cfa7-224">HTTPS를 사용 하려면 먼저 이전 섹션에 설명 된 대로 레지스트리 키의 소유권을 가져오고 아래와 같이 HttpsPort 및 \stststststststststh 키를 설정한 후 webmanagement 서비스를 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-224">If you want to use HTTPS, first take the ownership of the registry key as described in previous section and set the HttpsPort and EncryptionMode registry keys as below and then restart the webmanagement service</span></span>

        reg add HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\webmanagement\service /v EncryptionMode /t REG_DWORD /d 0x3 /f
        reg add HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\webmanagement\service /v HttpsPort /t REG_DWORD /d <your port number> /f
        net stop webmanagement ; net start webmanagement

### <a name="provisoning-device-portal-with-a-custom-ssl-certificate"></a><span data-ttu-id="5cfa7-225">사용자 지정 SSL 인증서를 사용 하 여 장치 포털 프로 비전</span><span class="sxs-lookup"><span data-stu-id="5cfa7-225">Provisoning Device Portal with a custom SSL certificate</span></span>

<span data-ttu-id="5cfa7-226">Windows 10 크리에이터 업데이트에서 Windows 장치 포털은 장치 관리자가 HTTPS 통신에 사용할 사용자 지정 인증서를 설치할 수 있는 방법을 추가 했습니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-226">In the Windows 10 Creators Update, the Windows Device Portal added a way for device administrators to install a custom certificate for use in HTTPS communication.</span></span>

<span data-ttu-id="5cfa7-227">자세히 알아보려면 [Windows 장치 포털 문서에서 설명서를 참조](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-ssl)하세요.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-227">To learn more, [read the documentation under the Windows Device Portal docs](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-ssl).</span></span> 

### <a name="crash-dump-settings-for-capturing-memory-dump"></a><span data-ttu-id="5cfa7-228">메모리 덤프 캡처에 대 한 크래시 덤프 설정:</span><span class="sxs-lookup"><span data-stu-id="5cfa7-228">Crash Dump Settings for Capturing Memory Dump:</span></span>

<span data-ttu-id="5cfa7-229">전체 메모리 덤프를 캡처하려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-229">To capture a Full Memory Dump, do the following:</span></span>

1. <span data-ttu-id="5cfa7-230">WDP를 통해 IoT 장치에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-230">Connect to a IoT device through WDP.</span></span>

2. <span data-ttu-id="5cfa7-231">디버그 > 디버그 설정-> 커널 충돌 설정-> 크래시 덤프 유형입니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-231">From Debug -> Debug settings -> Kernel crash settings -> Crash dump type.</span></span> 

3. <span data-ttu-id="5cfa7-232">: 메모리 덤프 완료 (사용 중인 메모리)를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-232">Select: Complete memory dump (in use memory).</span></span>
    <span data-ttu-id="5cfa7-233">설정을 적용 하려면 장치를 다시 부팅 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-233">Make sure the device is rebooted for the setting to take effect.</span></span> 
    
4. <span data-ttu-id="5cfa7-234">`HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\CrashControl\CrashDumpEnabled`가 0x1로 설정 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-234">Verify  that `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\CrashControl\CrashDumpEnabled` is set to 0x1.</span></span>

5. <span data-ttu-id="5cfa7-235">`HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\CrashControl\DumpFileSize`를 0x0으로 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-235">Update `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\CrashControl\DumpFileSize` to 0x0.</span></span>

6. <span data-ttu-id="5cfa7-236">이 덤프를 생성 하기에 충분 한 공간이 장치에 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="5cfa7-236">Make sure you have enough space on the device for this Dump to be generated.</span></span> <span data-ttu-id="5cfa7-237">덤프 파일 위치를 변경 하는 작업은 다음 위치에서 구성할 수 있습니다. `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\CrashControl\DumpFile`</span><span class="sxs-lookup"><span data-stu-id="5cfa7-237">You can configure the changing the DumpFile location from here: `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\CrashControl\DumpFile`</span></span>


## <a name="additional-resources"></a><span data-ttu-id="5cfa7-238">추가 리소스</span><span class="sxs-lookup"><span data-stu-id="5cfa7-238">Additional Resources</span></span>
___ 

1. [<span data-ttu-id="5cfa7-239">Windows 장치 포털 개요 페이지</span><span class="sxs-lookup"><span data-stu-id="5cfa7-239">Windows Device Portal overview page</span></span>](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal)
