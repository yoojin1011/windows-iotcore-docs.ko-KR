---
title: Windows Device Portal
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: Windows 장치 포털을 사용 하 여 장치를 원격으로 구성 하 고 관리 하는 방법에 대해 알아봅니다.
keywords: windows iot, Windows 장치 포털, 원격, 장치 포털
ms.openlocfilehash: 8e430365ea09509f5638d86ac77b151226df488f
ms.sourcegitcommit: 8932969dc50805113c330bc2ba6ec9003d067b3c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67412157"
---
# <a name="windows-device-portal"></a><span data-ttu-id="e5552-104">Windows Device Portal</span><span class="sxs-lookup"><span data-stu-id="e5552-104">Windows Device Portal</span></span>
   <span data-ttu-id="e5552-105">Windows 장치 포털 (WDP)을 사용 하 여 로컬 네트워크를 통해 원격으로 장치를 구성 하 고 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-105">The Windows Device Portal (WDP) lets you configure and manage your device remotely over your local network.</span></span>
<span data-ttu-id="e5552-106">주요 기능은 [Windows 장치 포털 개요 페이지](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal) 에 설명 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-106">The main features are documented on the [Windows Device Portal overview page](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal)</span></span>

![장치 포털 홈](../media/deviceportal/deviceportal.png)

> [!IMPORTANT]
> <span data-ttu-id="e5552-108">상용화에 제조사 이미지를 사용하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="e5552-108">Do not use maker images for commercialization.</span></span> <span data-ttu-id="e5552-109">디바이스를 상용화하려는 경우 최적의 보안을 위해 사용자 지정 FFU를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-109">If you are commercializing a device, you must use a custom FFU for optimal security.</span></span> <span data-ttu-id="e5552-110">[여기](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)에서 자세한 내용을 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="e5552-110">Learn more [here](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).</span></span>

> [!WARNING]
> <span data-ttu-id="e5552-111">라이브 커널 디버그가 현재 ARM 장치에 대해 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-111">Live kernel debug is currently failing for ARM devices.</span></span> <span data-ttu-id="e5552-112">이 문제를 해결 하기 위해 노력 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-112">We are working to get this fixed.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e5552-113">최종 사용자가 최종 구성을 수행 하 고 고객에 게 [WDP에 대 한 인증서를 얻어야 하는 고객을 문서화 하는 "특정/제한 된 설치" (즉, 공장 또는 소매점)에 대해 상용 배포를 위한 오픈 정품 장치를 구축 하는 경우 그리고 WDP에 설치 하 고 브라우저와 암호를 연결 하면 WDP에서](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-ssl)WDP를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-113">If you are building an open retail device for commercial deployment to a "specific/limited installation" (i.e. factory or retail store) where the end-user does the final configuration and you document your customers that they must [obtain a certificate for WDP and install it on both WDP and connecting browsers and passwords are changed on WDP](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-ssl), then using WDP in this narrow commercial instance is acceptable.</span></span> <span data-ttu-id="e5552-114">이 시나리오에서 소매점 이미지는 여전히 IOT_TOOLKIT를 포함 *하지* 않지만 IOT_WEBBEXTN 패키지를 사용 하 여 WDP로 가져와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-114">Retail images in this scenario should still *not* include IOT_TOOLKIT, but should use the IOT_WEBBEXTN package to pull in WDP.</span></span> 

## <a name="shared-documentation"></a><span data-ttu-id="e5552-115">공유 설명서</span><span class="sxs-lookup"><span data-stu-id="e5552-115">Shared Documentation</span></span>
<span data-ttu-id="e5552-116">WDP는 모든 Windows 10 장치에서 공유 되는 개발자 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-116">WDP is a developer tool shared among all Windows 10 devices.</span></span> <span data-ttu-id="e5552-117">각 제품에는 고유한 기능이 있지만 핵심 기능은 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-117">Each product has its own unique features, but the core functionality is the same.</span></span>
<span data-ttu-id="e5552-118">주요 기능에 대 한 설명서는 [Windows 장치 포털 개요 페이지](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal)에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-118">Documentation for the main features are found on the [Windows Device Portal overview page](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal).</span></span> <span data-ttu-id="e5552-119">아래 설명서의 나머지 부분은 IoT 관련 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-119">The rest of the documentation below will be IoT specific.</span></span>

## <a name="set-up"></a><span data-ttu-id="e5552-120">설정</span><span class="sxs-lookup"><span data-stu-id="e5552-120">Set up</span></span>

<span data-ttu-id="e5552-121">Windows 장치 포털을 시작 하 고 실행 하는 방법에는 두 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-121">There are two ways to go get the Windows Device Portal up and running.</span></span>

### <a name="1-windows-10-iot-dashboard"></a><span data-ttu-id="e5552-122">1. Windows 10 IoT 대시보드</span><span class="sxs-lookup"><span data-stu-id="e5552-122">1. Windows 10 IoT Dashboard</span></span>

<span data-ttu-id="e5552-123">먼저 새 장치를 쉽게 설정할 수 있도록 하는 개발자 도구인 [Windows 10 IoT 대시보드](https://docs.microsoft.com/en-us/windows/iot-core/connect-your-device/iotdashboard)를 다운로드 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-123">First, you'll want to download the [Windows 10 IoT Dashboard](https://docs.microsoft.com/en-us/windows/iot-core/connect-your-device/iotdashboard), a developer tool that makes it easy to set up new devices.</span></span> <span data-ttu-id="e5552-124">대시보드를 사용 하 여 Windows 10 IoT Core 이미지를 장치에 플래시 한 후 장치가 "내 장치" 아래에 표시 되는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-124">Once you've used the Dashboard to flash a Windows 10 IoT Core image onto your device, check that your device shows up under "My devices".</span></span> 

<span data-ttu-id="e5552-125">여기에서 "작업" 아래에 있는 줄임표를 사용 하 여 "장치 포털에서 열기"를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-125">From there, use the ellipses under "Actions" to select "Open in Device Portal".</span></span> <span data-ttu-id="e5552-126">여기서는 처음에 자격 증명을 변경 하지 않은 경우 기본 자격 증명을 사용 하 여 장치 포털 인증 페이지로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-126">From there, you'll be taken to the Device Portal authentication page where, unless you changed the credentials initially, the default credentials are:</span></span> 

    Username: `Administrator`<br/>
    Password: `p@ssw0rd`
 
 ### <a name="2-browser"></a><span data-ttu-id="e5552-127">2. 브라우저</span><span class="sxs-lookup"><span data-stu-id="e5552-127">2. Browser</span></span>
<span data-ttu-id="e5552-128">대시보드에서 장치를 찾을 수 없거나 대시보드를 사용 하는 것을 선호 하는 경우 장치의 IP 주소와 `:8080` 끝에를 입력 하 여 장치 포털을 열 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-128">If you cannot find your device in the dashboard or prefer to skip using the dashboard, you can also open the Device Portal by entering the IP address of your device plus `:8080` onto the end.</span></span> <span data-ttu-id="e5552-129">올바르게 수행 되 면 다음과 같이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-129">When done correctly, it should look something like this:</span></span>


   ![I이상 대시보드 보기 장치](../media/deviceportal/Dashboard-Action.gif)

    
## <a name="iot-specific-features"></a><span data-ttu-id="e5552-131">IoT 관련 기능</span><span class="sxs-lookup"><span data-stu-id="e5552-131">IoT specific features</span></span>

### <a name="device-settings"></a><span data-ttu-id="e5552-132">장치 설정</span><span class="sxs-lookup"><span data-stu-id="e5552-132">Device Settings</span></span>

<span data-ttu-id="e5552-133">IoT Core는 [화상 키보드](../develop-your-app/OnScreenKeyboard.md) 를 사용 하거나 사용 하지 않도록 확인란을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-133">IoT Core adds a checkbox to enable or disable the [on-screen keyboard](../develop-your-app/OnScreenKeyboard.md)</span></span>
> [!NOTE]
> <span data-ttu-id="e5552-134">이 확인란은 선택 된 상태에서 선택 되지 않은 것으로 "flash"가 되는 알려진 버그를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-134">This checkbox has a known bug where it will "flash" from checked to non-checked.</span></span> <span data-ttu-id="e5552-135">확인란이 원하는 상태를 표시 하는지 확인 하려면 클릭 한 후 페이지를 새로 고칩니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-135">Please refresh the page (F5) after clicking to ensure that the checkbox is showing your desired state.</span></span>

### <a name="apps"></a><span data-ttu-id="e5552-136">앱</span><span class="sxs-lookup"><span data-stu-id="e5552-136">Apps</span></span>
<span data-ttu-id="e5552-137">장치에서 AppX 패키지 및 번들에 대 한 설치/제거 기능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-137">Provides install/uninstall functionality for AppX packages and bundles on your device.</span></span>
<span data-ttu-id="e5552-138">![앱 목록](../media/DevicePortal/AppList.png)</span><span class="sxs-lookup"><span data-stu-id="e5552-138">![App list](../media/DevicePortal/AppList.png)</span></span>

<span data-ttu-id="e5552-139">IoT Core는 한 번에 하나의 포그라운드 앱만 실행할 수 있다는 면에서 고유 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-139">IoT Core is unique in that it only allows one foreground app to run at one time.</span></span> <span data-ttu-id="e5552-140">이 경우 앱 목록이 수정 되어이를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-140">The app list is modified to ensure that this is the case.</span></span> <span data-ttu-id="e5552-141">**시작** 열에서 기본적으로 시작할 백그라운드 응용 프로그램 수를 선택할 수 있지만 전경 응용 프로그램은 하나만 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-141">Under the **STARTUP** column, you can select as many background applications to start by default, but can only set one foreground application.</span></span>  

### <a name="app-file-explorer"></a><span data-ttu-id="e5552-142">앱 파일 탐색기</span><span class="sxs-lookup"><span data-stu-id="e5552-142">App File Explorer</span></span>

<span data-ttu-id="e5552-143">앱 파일 탐색기에는 앱이 액세스할 수 있는 디렉터리가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-143">The app file explorer shows the directories that your apps can access.</span></span>

* <span data-ttu-id="e5552-144">CameraRoll는 모든 앱에서 공유 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-144">CameraRoll is shared among all apps</span></span>
* <span data-ttu-id="e5552-145">문서는 모든 앱에서 공유 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-145">Documents is shared among all apps</span></span>
* <span data-ttu-id="e5552-146">LocalAppData에는 각 앱에 해당 하는 폴더가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-146">LocalAppData contains folders specific to each app.</span></span> <span data-ttu-id="e5552-147">이 폴더는 앱과 이름이 같으며 다른 앱은 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-147">This folder will be the same name as your app and other apps cannot access it.</span></span>

### <a name="debugging"></a><span data-ttu-id="e5552-148">디버깅</span><span class="sxs-lookup"><span data-stu-id="e5552-148">Debugging</span></span>

#### <a name="kernel-dumps"></a><span data-ttu-id="e5552-149">커널 덤프</span><span class="sxs-lookup"><span data-stu-id="e5552-149">Kernel dumps</span></span>
![커널 덤프를 사용 하 여 디버깅](../media/DevicePortal/Debug1.png)

<span data-ttu-id="e5552-151">모든 시스템 크래시는 자동으로 기록 되 고 웹 관리 도구를 통해 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-151">Any system crashes will automatically be logged and available to view through the web management tool.</span></span>  <span data-ttu-id="e5552-152">그런 다음 커널 덤프를 다운로드 하 고 진행 상황을 파악할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-152">You can then download the kernel dump and try to figure out what's going on.</span></span>

#### <a name="process-dumps"></a><span data-ttu-id="e5552-153">덤프 처리</span><span class="sxs-lookup"><span data-stu-id="e5552-153">Process dumps</span></span>
![프로세스 덤프를 사용 하 여 디버깅](../media/DevicePortal/Debug2.png)

<span data-ttu-id="e5552-155">이는 라이브 커널 덤프와 유사 하지만 사용자 모드 프로세스의 경우입니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-155">This is similar to Live kernel dumps, but for the user mode processes.</span></span> <span data-ttu-id="e5552-156">**다운로드** 단추를 클릭 하면 ' 미니 덤프 '가 발생 하 고 해당 프로세스의 전체 상태가 다운로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-156">Clicking the **download** button will cause a 'minidump', and the entire state of that process will be downloaded.</span></span> <span data-ttu-id="e5552-157">이는 분기 프로세스를 디버깅 하는 데 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-157">This is good for debugging hanging processes.</span></span>

#### <a name="kernel-crash-settings"></a><span data-ttu-id="e5552-158">커널 충돌 설정</span><span class="sxs-lookup"><span data-stu-id="e5552-158">Kernel crash settings</span></span>
![커널 충돌 설정](../media/DevicePortal/Debug3.png)

### <a name="bluetooth"></a><span data-ttu-id="e5552-160">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="e5552-160">Bluetooth</span></span>
<span data-ttu-id="e5552-161">이 페이지에는 모든 bluetooth 페어링 장치와 검색 가능한 모든 장치가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-161">This page shows you all the bluetooth paired devices and all the devices which are discoverable.</span></span> <span data-ttu-id="e5552-162">다른 Bluetooth 장치와 페어링 하려면 장치를 페어링 모드로 전환 하 고 사용 가능한 장치 목록에 표시 될 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-162">To pair with another Bluetooth device, put the device in pairing mode and wait for it to appear in the available devices list.</span></span>  
![Bluetooth 장치 목록](../media/DevicePortal/Bluetooth.png)

<span data-ttu-id="e5552-164">**페어링 링크** 를 클릭 하 여 장치를 페어링 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-164">Click on **Pair link** to pair the device.</span></span> <span data-ttu-id="e5552-165">장치에서 페어링을 위해 PIN을 요구 하는 경우 PIN을 표시 하는 메시지 상자가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-165">If the device requires a PIN for pairing, it will pop-up a message box displaying the PIN.</span></span> <span data-ttu-id="e5552-166">장치가 페어링된 후 페어링 된 장치 목록에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-166">Once the device is paired, it will show up in the Paired devices list.</span></span> <span data-ttu-id="e5552-167">**제거**를 클릭 하 여 장치 쌍을 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-167">You can un-pair the device by clicking on **Remove**.</span></span> 

<span data-ttu-id="e5552-168">Bluetooth 페이지로 이동 하면 다른 장치에서 장치를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-168">Once you navigate to the Bluetooth page, your device will be discoverable by other devices.</span></span> <span data-ttu-id="e5552-169">또한 PC/휴대폰에서 해당 파일을 찾아 쌍으로 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-169">You can also find it from your PC/Phone and pair it from there.</span></span>

<span data-ttu-id="e5552-170">Bluetooth에 대 한 자세한 내용은 [bluetooth 페이지](https://go.microsoft.com/fwlink/?linkid=823223)에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-170">More information on bluetooth can be found on the [bluetooth page](https://go.microsoft.com/fwlink/?linkid=823223).</span></span>

### <a name="iot-onboarding"></a><span data-ttu-id="e5552-171">IoT 온 보 딩</span><span class="sxs-lookup"><span data-stu-id="e5552-171">IoT Onboarding</span></span>

<span data-ttu-id="e5552-172">IoT 온 보 딩은 IoT 장치의 Wi-fi 연결 옵션을 구성 하는 기능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-172">IoT Onboarding provides support for configuring an IoT device's Wi-Fi connectivity options.</span></span>

<span data-ttu-id="e5552-173">**ICS (인터넷 연결 공유)** 인터넷 연결 공유를 사용 하면 Wi-fi SoftAP에서 장치에 연결 된 다른 장치와 장치의 인터넷 액세스를 공유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-173">**Internet Connection Sharing (ICS)** Internet Connection Sharing allows you to share the Internet access of your device with other devices connected to your device over the Wi-Fi SoftAP.</span></span>
<span data-ttu-id="e5552-174">이 기능을 사용 하려면 Windows 10 IoT 장치에서 인터넷에 액세스할 수 있어야 합니다 (예: 유선 LAN 연결을 통해).</span><span class="sxs-lookup"><span data-stu-id="e5552-174">To use this feature, your Windows 10 IoT Device needs to have access to the internet (e.g. through a wired LAN connection).</span></span>  <span data-ttu-id="e5552-175">' 연결-> 온 보 딩-> SoftAP 설정 '에서 ' 사용 '을 클릭 하 고 SSID 이름과 암호를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-175">In 'Connectivity->Onboarding->SoftAP settings' click 'enable' and set SSID name and password.</span></span>  <span data-ttu-id="e5552-176">그런 다음 ' 연결-> 인터넷 연결 공유 '에서 ' 액세스 지점 어댑터 '를 선택 하 고, ' Microsoft Wi-fi 직접 가상 어댑터 #2 "를 선택 하 고, ' 공유 네트워크 어댑터 '에서 유선 이더넷 어댑터를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-176">Then in 'Connectivity->Internet connection sharing' for 'access point adapter' select "Microsoft Wi-FI Direct Virtual Adapter #2" and for 'shared network adapter' select your wired ethernet adapter.</span></span>  <span data-ttu-id="e5552-177">마지막으로 ' 공유 액세스 시작 '을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-177">Finally, click 'start shared access.'</span></span>  <span data-ttu-id="e5552-178">시작 되 면 별도의 Wi-fi 사용 장치를 Windows 10 IoT 장치의 SoftAP에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-178">Once started, connect a separate Wi-Fi enabled device to the SoftAP on your Windows 10 IoT device.</span></span>  <span data-ttu-id="e5552-179">연결이 설정 되 면 별도의 Wi-fi 사용 장치에서 Windows 10 IoT 장치를 통해 인터넷에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-179">After a connection is established your separate Wi-Fi enabled device will be able to connect to the internet through your Windows 10 IoT device.</span></span>

> [!NOTE]
> <span data-ttu-id="e5552-180">Wi-fi 프로필이 장치에 있는 경우 ICS를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-180">ICS is disabled when a Wi-Fi profile exists on the device.</span></span> <span data-ttu-id="e5552-181">예를 들어 Wi-fi 액세스 지점에 연결 하 고 "프로필 만들기 (자동 다시 연결)"를 선택 하는 경우 ICS를 사용 하지 않도록 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-181">For example, ICS will be disabled if you connect to a Wi-Fi access point and check “Create profile (auto re-connect)”.</span></span>

<span data-ttu-id="e5552-182">**SoftAP 설정** SoftAP 설정을 사용 하 여 장치의 SoftAP 사용 여부를 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-182">**SoftAP Settings** The SoftAP Settings allow you to control whether or not your device's SoftAP is enabled.</span></span>  <span data-ttu-id="e5552-183">또한 다른 장치에서 SoftAP를 연결 하는 데 필요한 SoftAP의 SSID와 WPA2-PSK 키를 구성 하는 수단을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-183">It also provides a means for configuring your SoftAP's SSID and the WPA2-PSK key which are necessary to connect the SoftAP from another device.</span></span>

<span data-ttu-id="e5552-184">**AllJoyn 온 보 딩 설정** AllJoyn 온 보 딩 설정을 사용 하 여 장치의 AllJoyn 등록 생산자를 통해 장치의 Wi-fi 연결을 구성할 수 있는지 여부를 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-184">**AllJoyn Onboarding Settings** The AllJoyn Onboarding Settings allow you to control whether or not your device's Wi-Fi connection can configured through your device's AllJoyn Onboarding Producer.</span></span>  <span data-ttu-id="e5552-185">AllJoyn 온 보 딩 소비자 응용 프로그램을 실행 하는 별도 장치에서 Windows 10 IoT SoftAP에 연결 하는 경우 AllJoyn 온 보 딩 소비자 응용 프로그램을 사용 하 여 IoT 장치의 Wi-fi 어댑터를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-185">When a separate device running an AllJoyn Onboarding Consumer application connects to your Windows 10 IoT SoftAP, the AllJoyn Onboarding Consumer application can be used to configure your IoT device's Wi-Fi adapter.</span></span>  <span data-ttu-id="e5552-186">이 기능을 사용 하도록 설정 하면 ECDHE_NULL 인증 방법을 사용 하는 AllJoyn 온 보 딩 생산자 앱</span><span class="sxs-lookup"><span data-stu-id="e5552-186">When enabled, the AllJoyn Onboarding Producer app (IoTOnboarding) uses the ECDHE_NULL authentication method.</span></span> 

> [!NOTE]
> <span data-ttu-id="e5552-187">Windows 10 IoT 빌드에서 10.0.14393 또는 이전 버전을 사용 하려면 [여기에서 다운로드할](https://github.com/ms-iot/samples)수 있는 <strong>iotonboarding 보 딩</strong> 샘플에 대 한 업데이트가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-187">To use AllJoyn Onboarding with Windows 10 IoT builds 10.0.14393 or earlier requires an update to the <strong>IotOnboarding</strong> sample which may be [downloaded here](https://github.com/ms-iot/samples).</span></span>

<span data-ttu-id="e5552-188">![ICS에 대](../media/DevicePortal/OnboardingAllJoyn.png)
한 AllJoyn![등록에 온 보 딩](../media/DevicePortal/OnboardingICS.png)</span><span class="sxs-lookup"><span data-stu-id="e5552-188">![Onboarding onto AllJoyn](../media/DevicePortal/OnboardingAllJoyn.png)
![Onboarding onto ICS](../media/DevicePortal/OnboardingICS.png)</span></span>

> [!NOTE]
> <span data-ttu-id="e5552-189">액세스 지점 어댑터는 WiFi 액세스 지점 역할을 하는 WiFi 어댑터 이며 일반적으로 192.168.137.1와 같은 IP 주소가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-189">Access point adapter is the WiFi adapter that act as a WiFi access point (it usually has an IP address like 192.168.137.1).</span></span>
> <span data-ttu-id="e5552-190">공유 네트워크 어댑터는 인터넷에 연결 하는 어댑터 (예: 이더넷 어댑터).</span><span class="sxs-lookup"><span data-stu-id="e5552-190">Shared network adapter is the adapter that connects to Internet (e.g.: Ethernet adapter).</span></span>

![소프트 AP로 등록](../media/DevicePortal/OnboardingSoftAP.png)

> [!NOTE]
> <span data-ttu-id="e5552-192">SoftAP SSID는 AllJoyn 등록을 사용 하도록 설정 하 고, Wifi 어댑터의 MAC 주소를 사용 하 여 되도록 후 위를 사용 하는 경우 "AJ_"로 자동 접두사가 붙습니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-192">SoftAP SSID will be automatically prefixed by "AJ_" if AllJoyn onboarding is enabled and postfixed with the MAC address of the Wifi adapter.</span></span> <span data-ttu-id="e5552-193">SoftAP 암호는 8 ~ 007e; 63 ASCII 문자 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-193">The SoftAP passphrase must be between 8 and 63 ASCII characters.</span></span>


### <a name="tpm-configuration"></a><span data-ttu-id="e5552-194">TPM 구성</span><span class="sxs-lookup"><span data-stu-id="e5552-194">TPM configuration</span></span>
<span data-ttu-id="e5552-195">TPM (신뢰할 수 있는 플랫폼 모듈)은 난수 생성, 암호화 키의 보안 생성 및 사용 제한에 대 한 기능을 포함 하는 암호화 보조 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-195">The Trusted Platform Module (TPM) is a cryptographic coprocessor including capabilities for random number generation, secure generation of cryptographic keys and limitation of their use.</span></span> <span data-ttu-id="e5552-196">또한 원격 증명 및 봉인 된 저장소와 같은 기능을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-196">It also includes capabilities such as remote attestation and sealed storage.</span></span> <span data-ttu-id="e5552-197">IoT Core의 TPM 및 보안에 대 한 자세한 내용은 [보안 장치 구축](../secure-your-device/BuildingSecureDevices.md) 페이지 및 [tpm](../secure-your-device/TPM.md) 페이지를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e5552-197">To learn about the TPM and security on IoT Core, visit the [Building secure devices](../secure-your-device/BuildingSecureDevices.md) page and the [TPM](../secure-your-device/TPM.md) page.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e5552-198">Limpet는 Windows IoT Core의 일부로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-198">Limpet.exe used to be part of Windows IoT Core.</span></span> <span data-ttu-id="e5552-199">2018 년 10 월부터 현재 오픈 소스에서 [https://github.com/ms-iot/azure-dm-client](https://github.com/ms-iot/azure-dm-client)사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-199">Starting with October 2018, it is now available as an open source porject at [https://github.com/ms-iot/azure-dm-client](https://github.com/ms-iot/azure-dm-client).</span></span>

<span data-ttu-id="e5552-200">테스트를 용이 하 게 하기 위해 Limpet의 서명 되지 않은 미리 작성 된 버전을 사용할 수 있으며 WDP에서 바로 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-200">To make testing easier, we have a non-signed pre-built version of Limpet.exe available and can be downloaded right from WDP.</span></span> <span data-ttu-id="e5552-201">' TPM 구성 ' 탭으로 이동 하 여 ' 최신 버전 설치 ' 단추를 클릭 하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-201">You just need to go the 'TPM Configuration' tab and click the 'Install Latest' button.</span></span> 

> [!NOTE]
> <span data-ttu-id="e5552-202">이 버전의 Limpet를 최종 제품과 함께 제공 해서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-202">This version of Limpet.exe should not be shipped with your final product.</span></span> <span data-ttu-id="e5552-203">대신 오픈 소스 프로젝트를 빌드하고, 서명 하 고, 이미지를 사용 하 여 패키지 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-203">Instead, you need to build the open source project, sign it, and package it with your image.</span></span>

### <a name="azure-clients-configuration"></a><span data-ttu-id="e5552-204">Azure 클라이언트 구성</span><span class="sxs-lookup"><span data-stu-id="e5552-204">Azure Clients configuration</span></span>

<span data-ttu-id="e5552-205">IoT 장치는 클라우드 서비스를 통해 원격으로 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-205">IoT devices can be remotely managed through cloud services.</span></span> <span data-ttu-id="e5552-206">Azure는 이러한 시나리오를 가능 하 게 해 주는 매우 다양 한 서비스 집합을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-206">Azure provides a very rich set of services to enable such scenarios.</span></span> <span data-ttu-id="e5552-207">Microsoft는 Windows 플랫폼에서 Azure의 DPS (장치 프로 비전 서비스)와 Azure의 IoT Hub 서비스를 보완 하 고 몇 가지 Windows 관리 효율성 기능을 노출 하는 장치 관리 클라이언트를 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-207">We have created a device management client that complements Azure's Device Provisioning Service (DPS) and Azure's IoT Hub service on the Windows platform and which also exposes several Windows manageability features.</span></span>

<span data-ttu-id="e5552-208">클라이언트는 오픈 소스 프로젝트로 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-208">The clients will be provided as open source projects.</span></span> <span data-ttu-id="e5552-209">테스트를 더 쉽게 수행 하기 위해 미리 작성 된 이진 파일을 제공할 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-209">To make testing them easier, we will be providing pre-built binaries.</span></span> <span data-ttu-id="e5552-210">WDP에서 ' Azure 클라이언트 ' 탭을 사용 하 여 해당 테스트 바이너리를 설치 하 고 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-210">You can use the 'Azure Clients' tab in WDP to install and run those test binaries.</span></span>

> [!NOTE]
> <span data-ttu-id="e5552-211">이 버전의 도구를 최종 제품과 함께 제공 해서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-211">This version of the tools should not be shipped with your final product.</span></span> <span data-ttu-id="e5552-212">대신 오픈 소스 프로젝트를 빌드하고, 서명 하 고, 이미지를 사용 하 여 패키지 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-212">Instead, you need to build the open source project, sign it, and package it with your image.</span></span>

<span data-ttu-id="e5552-213">오픈 소스 프로젝트를 사용할 수 있게 되 면이 설명서를 업데이트할 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-213">We will update this documentation once the open source projects are available for consumption.</span></span>

### <a name="remote"></a><span data-ttu-id="e5552-214">리모컨</span><span class="sxs-lookup"><span data-stu-id="e5552-214">Remote</span></span>
<span data-ttu-id="e5552-215">사용자는 Windows IoT 원격 서버를 사용 하 여 실제 모니터를 키보드에 연결 하지 않고도 장치에 표시 되는 항목을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-215">The Windows IoT Remote Server allows users to see what their device is displaying without connecting a physical monitor to the keyboard.</span></span>


## <a name="additional-information"></a><span data-ttu-id="e5552-216">추가 정보</span><span class="sxs-lookup"><span data-stu-id="e5552-216">Additional Information</span></span> 

### <a name="changing-the-default-port"></a><span data-ttu-id="e5552-217">기본 포트 변경</span><span class="sxs-lookup"><span data-stu-id="e5552-217">Changing the default port</span></span>
 
1. <span data-ttu-id="e5552-218">Powershell을 시작 하 고 [장치에 연결 합니다.](../connect-your-device/PowerShell.md)</span><span class="sxs-lookup"><span data-stu-id="e5552-218">Launch powershell and [connect to your device.](../connect-your-device/PowerShell.md)</span></span>
2. <span data-ttu-id="e5552-219">[TakeRegistryOwnership](https://github.com/ms-iot/iot-utilities/tree/master/TakeRegistryOwnership) 도구를 다운로드 하 고 빌드하고 장치에 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-219">Download [TakeRegistryOwnership](https://github.com/ms-iot/iot-utilities/tree/master/TakeRegistryOwnership) tool, build it, and copy it to your device.</span></span> 
3. <span data-ttu-id="e5552-220">을 실행 하 여 서비스에 대 한 레지스트리 키의 소유권 가져오기</span><span class="sxs-lookup"><span data-stu-id="e5552-220">Take ownership of the registry key for the service by running</span></span>

        .\TakeRegistryOwnership.exe MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\webmanagement\service

4. <span data-ttu-id="e5552-221">레지스트리 설정을 수정 하 여 원하는 포트를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-221">Set the desired port by modifying the registry settings</span></span> 

        reg add HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\webmanagement\service /v HttpPort /t REG_DWORD /d <your port number>
        
5. <span data-ttu-id="e5552-222">다음을 실행 하거나 장치를 다시 시작 하 여 WebManagement 서비스를 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-222">Restart the WebManagement service by running following or by restarting the device</span></span>

        net stop webmanagement ; net start webmanagement

### <a name="using-https"></a><span data-ttu-id="e5552-223">HTTPS 사용</span><span class="sxs-lookup"><span data-stu-id="e5552-223">Using HTTPS</span></span> 

<span data-ttu-id="e5552-224">HTTPS를 사용 하려면 먼저 이전 섹션에 설명 된 대로 레지스트리 키의 소유권을 가져오고 아래와 같이 HttpsPort 및 \stststststststststh 키를 설정한 후 webmanagement 서비스를 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-224">If you want to use HTTPS, first take the ownership of the registry key as described in previous section and set the HttpsPort and EncryptionMode registry keys as below and then restart the webmanagement service</span></span>

        reg add HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\webmanagement\service /v EncryptionMode /t REG_DWORD /d 0x3 /f
        reg add HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\webmanagement\service /v HttpsPort /t REG_DWORD /d <your port number> /f
        net stop webmanagement ; net start webmanagement

### <a name="provisoning-device-portal-with-a-custom-ssl-certificate"></a><span data-ttu-id="e5552-225">사용자 지정 SSL 인증서를 사용 하 여 장치 포털 프로 비전</span><span class="sxs-lookup"><span data-stu-id="e5552-225">Provisoning Device Portal with a custom SSL certificate</span></span>

<span data-ttu-id="e5552-226">Windows 10 크리에이터 업데이트에서 Windows 장치 포털은 장치 관리자가 HTTPS 통신에 사용할 사용자 지정 인증서를 설치할 수 있는 방법을 추가 했습니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-226">In the Windows 10 Creators Update, the Windows Device Portal added a way for device administrators to install a custom certificate for use in HTTPS communication.</span></span>

<span data-ttu-id="e5552-227">자세히 알아보려면 [Windows 장치 포털 문서에서 설명서를 참조](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-ssl)하세요.</span><span class="sxs-lookup"><span data-stu-id="e5552-227">To learn more, [read the documentation under the Windows Device Portal docs](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-ssl).</span></span> 

### <a name="crash-dump-settings-for-capturing-memory-dump"></a><span data-ttu-id="e5552-228">메모리 덤프 캡처에 대 한 크래시 덤프 설정:</span><span class="sxs-lookup"><span data-stu-id="e5552-228">Crash Dump Settings for Capturing Memory Dump:</span></span>

<span data-ttu-id="e5552-229">전체 메모리 덤프를 캡처하려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-229">To capture a Full Memory Dump, do the following:</span></span>

1. <span data-ttu-id="e5552-230">WDP를 통해 IoT 장치에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-230">Connect to a IoT device through WDP.</span></span>

2. <span data-ttu-id="e5552-231">디버그 > 디버그 설정-> 커널 충돌 설정-> 크래시 덤프 유형입니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-231">From Debug -> Debug settings -> Kernel crash settings -> Crash dump type.</span></span> 

3. <span data-ttu-id="e5552-232">선택: 메모리 덤프 (사용 중인 메모리)를 완료 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-232">Select: Complete memory dump (in use memory).</span></span>
    <span data-ttu-id="e5552-233">설정을 적용 하려면 장치를 다시 부팅 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-233">Make sure the device is rebooted for the setting to take effect.</span></span> 
    
4. <span data-ttu-id="e5552-234">`HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\CrashControl\CrashDumpEnabled` 가 0x1로 설정 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-234">Verify  that `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\CrashControl\CrashDumpEnabled` is set to 0x1.</span></span>

5. <span data-ttu-id="e5552-235">0x0 `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\CrashControl\DumpFileSize` 으로 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-235">Update `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\CrashControl\DumpFileSize` to 0x0.</span></span>

6. <span data-ttu-id="e5552-236">이 덤프를 생성 하기에 충분 한 공간이 장치에 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5552-236">Make sure you have enough space on the device for this Dump to be generated.</span></span> <span data-ttu-id="e5552-237">덤프 파일 위치를 다음과 같이 변경 하도록 구성할 수 있습니다.`HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\CrashControl\DumpFile`</span><span class="sxs-lookup"><span data-stu-id="e5552-237">You can configure the changing the DumpFile location from here: `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\CrashControl\DumpFile`</span></span>


## <a name="additional-resources"></a><span data-ttu-id="e5552-238">추가 리소스</span><span class="sxs-lookup"><span data-stu-id="e5552-238">Additional Resources</span></span>
___ 

1. [<span data-ttu-id="e5552-239">Windows 장치 포털 개요 페이지</span><span class="sxs-lookup"><span data-stu-id="e5552-239">Windows Device Portal overview page</span></span>](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal)
