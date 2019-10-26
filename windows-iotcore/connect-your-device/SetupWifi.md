---
title: Windows 10 IoT Core 장치에서 WiFi 사용
ms.date: 08/28/2017
ms.topic: article
description: Windows 10 IoT Core 장치에서 wifi를 사용, 설정 및 구성 하는 방법에 대해 알아봅니다.
keywords: windows iot, wifi, 설정, 장치
ms.openlocfilehash: b8fa691da0560a741c0078d0030f10ae4ceb6c17
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918295"
---
# <a name="using-wifi-on-your-windows-10-iot-core-device"></a><span data-ttu-id="166f4-104">Windows 10 IoT Core 장치에서 WiFi 사용</span><span class="sxs-lookup"><span data-stu-id="166f4-104">Using WiFi on your Windows 10 IoT Core device</span></span>

<span data-ttu-id="166f4-105">WiFi는 USB WiFi 어댑터를 사용 하 여 Windows 10 IoT Core 장치에서 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="166f4-105">WiFi is supported on Windows 10 IoT Core devices through the use of a USB WiFi adapter.</span></span> <span data-ttu-id="166f4-106">WiFi를 사용 하면 [SSH](../connect-your-device/SSH.md), [Powershell](../connect-your-device/PowerShell.md), [Windows 장치 포털](../manage-your-device/DevicePortal.md), 응용 프로그램 디버깅 및 배포를 포함 하 여 유선 연결의 모든 기능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="166f4-106">Using WiFi provides all the functionality of a wired connection, including [SSH](../connect-your-device/SSH.md), [Powershell](../connect-your-device/PowerShell.md), [Windows Device Portal](../manage-your-device/DevicePortal.md), and application debugging and deployment.</span></span>

> [!NOTE]
> <span data-ttu-id="166f4-107">유선 이더넷 케이블을 꽂으면 기본 네트워크 인터페이스로 WiFi가 재정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="166f4-107">Plugging in a wired Ethernet cable will override WiFi as the default network interface.</span></span>

### <a name="supported-adapters"></a><span data-ttu-id="166f4-108">지원 되는 어댑터</span><span class="sxs-lookup"><span data-stu-id="166f4-108">Supported Adapters</span></span>
<span data-ttu-id="166f4-109">Windows 10 IoT Core에서 테스트 된 WiFi 어댑터의 목록은 [지원 되는 하드웨어](../learn-about-hardware/HardwareCompatList.md) 페이지에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="166f4-109">A list of WiFi adapters that have been tested on Windows 10 IoT Core can be found on our [Supported Hardware](../learn-about-hardware/HardwareCompatList.md) page.</span></span>

### <a name="configuring-wifi"></a><span data-ttu-id="166f4-110">WiFi 구성</span><span class="sxs-lookup"><span data-stu-id="166f4-110">Configuring WiFi</span></span>
<span data-ttu-id="166f4-111">WiFi를 사용 하려면 WiFi 네트워크 자격 증명을 사용 하 여 Windows 10 IoT core를 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="166f4-111">To use WiFi, you'll need to provide Windows 10 IoT core with the WiFi network credentials.</span></span> <span data-ttu-id="166f4-112">도우미 앱 및 WPS 사용자 지정 솔루션을 빌드하는 방법에 대 한 설명서 외에도 아래에 나열 된 몇 가지 다른 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="166f4-112">In addition to documentation on how to build companion app and WPS custom solutions, there are a few different options for doing so listed below.</span></span>

## <a name="custom-companion-app--wps-wi-fi-onboarding-samples"></a><span data-ttu-id="166f4-113">사용자 지정 도우미 앱 & WPS Wi-fi 온 보 딩 샘플</span><span class="sxs-lookup"><span data-stu-id="166f4-113">Custom Companion App & WPS Wi-Fi Onboarding Samples</span></span>

<span data-ttu-id="166f4-114">현재는 개발자가 자신의 장치에 대 한 사용자 지정 wifi 온 보 딩 솔루션을 빌드하는 다양 한 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="166f4-114">Currently, we offer a number of ways for developers to build a custom wifi onboarding solution for their device.</span></span> 

> | <span data-ttu-id="166f4-115">샘플</span><span class="sxs-lookup"><span data-stu-id="166f4-115">Samples</span></span> | <span data-ttu-id="166f4-116">설명</span><span class="sxs-lookup"><span data-stu-id="166f4-116">Description</span></span> | <span data-ttu-id="166f4-117">장점</span><span class="sxs-lookup"><span data-stu-id="166f4-117">Benefits</span></span>  |  <span data-ttu-id="166f4-118">단점</span><span class="sxs-lookup"><span data-stu-id="166f4-118">Drawbacks</span></span>  |
> |-------------|----------|---------|---------|
> | [<span data-ttu-id="166f4-119">도우미 앱</span><span class="sxs-lookup"><span data-stu-id="166f4-119">Companion App</span></span>](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/CompanionApp) | <span data-ttu-id="166f4-120">장치의 Wi-fi를 구성할 수 있는 간단한 Xamarin 앱을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="166f4-120">Create a simple Xamarin app that can configure your device's Wi-Fi.</span></span> |  <span data-ttu-id="166f4-121">간단히 사용할 수 있습니다. IoT Core 용으로 또는 헤드리스 클라이언트가 플랫폼 간 작동</span><span class="sxs-lookup"><span data-stu-id="166f4-121">Simple to use; Headed or headless for IoT Core; Clients work cross-platform</span></span> | <span data-ttu-id="166f4-122">개발자가 자체 프로토콜을 만들고 있습니다. 개발자가 보안을 구현 하도록 요구</span><span class="sxs-lookup"><span data-stu-id="166f4-122">Developer is creating his or her own protocol; requires developer to implement security</span></span> |
> | [<span data-ttu-id="166f4-123">Bluetooth RFCOMM를 사용 하 여 IoT 온 보 딩</span><span class="sxs-lookup"><span data-stu-id="166f4-123">IoT Onboarding with Bluetooth RFCOMM</span></span>](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/IoTOnboarding_RFCOMM) | <span data-ttu-id="166f4-124">Bluetooth RFCOMM를 사용 하 여 Wi-fi에 연결 하도록 헤드리스 IoT 장치를 구성 하는 솔루션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="166f4-124">Create solution to configure your headless IoT device to connect with your Wi-Fi using Bluetooth RFCOMM.</span></span>  | <span data-ttu-id="166f4-125">I 또는 헤드리스 장치에서 관련 익숙한 기술 및 개념을 사용 합니다. IoT 장치가 SoftAP을 시작할 필요가 없습니다. 방화벽 설정을 조정할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="166f4-125">Relevant in headed or headless devices; Uses familiar technologies and concepts; Does not require IoT device to start a SoftAP; Does not need to adjust firewall settings</span></span> | <span data-ttu-id="166f4-126">클라이언트 및 서버 장치에 대 한 Bluetooth 지원이 필요 합니다. 샘플은 Windows 10 용 클라이언트 앱만 제공 합니다. 서버 앱은 클라이언트 장치 이름을 미리 정의 하거나 하드 코드 합니다.</span><span class="sxs-lookup"><span data-stu-id="166f4-126">Requires Bluetooth support for client and server devices; Sample only provides client app for Windows 10; Server app pre-defines/hard-codes the names of the client device.</span></span> |
> | [<span data-ttu-id="166f4-127">AllJoyn를 사용 하 여 IoT 온 보 딩</span><span class="sxs-lookup"><span data-stu-id="166f4-127">IoT Onboarding with AllJoyn</span></span>](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/IoTOnboarding) | <span data-ttu-id="166f4-128">사용자의 헤드리스 IoT 장치를 홈 Wi-fi 네트워크와 원격으로 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="166f4-128">Remotely join your headless IoT device with your home Wi-Fi network.</span></span> | <span data-ttu-id="166f4-129">AllJoyn에서 작동</span><span class="sxs-lookup"><span data-stu-id="166f4-129">Works with AllJoyn</span></span> | <span data-ttu-id="166f4-130">일부 AllJoyn 지원은 사용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="166f4-130">Some support for AllJoyn is deprecated</span></span> |
> | <span data-ttu-id="166f4-131">장치용 wi-fi 보호 설치 (WPS) Api</span><span class="sxs-lookup"><span data-stu-id="166f4-131">Wi-Fi Protected Setup (WPS) APIs for devices</span></span> | <span data-ttu-id="166f4-132">WPS 검색을 수행 하 여 네트워크에서 지원 되는 WPS 메서드를 쿼리 합니다.</span><span class="sxs-lookup"><span data-stu-id="166f4-132">Perform WPS discovery to query the WPS methods supported by the network.</span></span> | <span data-ttu-id="166f4-133">[WiFiAdapter GetWpsConfigurationAsync (WiFiAvailableNetwork](https://docs.microsoft.com/uwp/api/windows.devices.wifi.wifiadapter.getwpsconfigurationasync) 및 [WiFiAdapter](https://docs.microsoft.com/uwp/api/windows.devices.wifi.wifiadapter.connectasync) 메서드를 활용 하 여 wi-fi 장치를 특정 네트워크에 연결 하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="166f4-133">Simply leverage the [WiFiAdapter.GetWpsConfigurationAsync(WiFiAvailableNetwork](https://docs.microsoft.com/uwp/api/windows.devices.wifi.wifiadapter.getwpsconfigurationasync) and [WiFiAdapter.ConnectAsync](https://docs.microsoft.com/uwp/api/windows.devices.wifi.wifiadapter.connectasync) methods to connect wi-fi devices to specific networks.</span></span> | <span data-ttu-id="166f4-134">이러한 Api를 활용 하려면 이러한 Api에 대해 잘 알고 있어야 합니다. WPS 사용 라우터와만 호환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="166f4-134">You will need to become familiar with these APIs to leverage them.; only compatible with WPS-enabled routers</span></span>|

## <a name="headed-options"></a><span data-ttu-id="166f4-135">옵션:</span><span class="sxs-lookup"><span data-stu-id="166f4-135">Headed Options:</span></span>

### <a name="option-1-startup-configuration"></a><span data-ttu-id="166f4-136">옵션 1: 시작 구성</span><span class="sxs-lookup"><span data-stu-id="166f4-136">Option 1: Startup Configuration</span></span>
<span data-ttu-id="166f4-137">**필수 구성 요소:** Windows 10 IoT core 장치에는 연결 된 마우스, 키보드, 디스플레이 및 USB WiFi 어댑터가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="166f4-137">**Prerequisite:** The Windows 10 IoT core device needs a mouse, keyboard, display, and USB WiFi Adapter plugged in</span></span>

<span data-ttu-id="166f4-138">지원 되는 USB WiFi 어댑터를 사용 하 여 Windows 10 IoT Core를 처음 부팅할 때 구성 화면이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="166f4-138">The first time you boot Windows 10 IoT Core with a supported USB WiFi adapter, you will be presented with a configuration screen.</span></span>
<span data-ttu-id="166f4-139">구성 화면에서 연결할 WiFi 네트워크를 선택 하 고 암호를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="166f4-139">On the configuration screen, select the WiFi network you would like to connect to and supply the password.</span></span> <span data-ttu-id="166f4-140">연결 **을 클릭 하** 여 연결을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="166f4-140">Click **connect** to initiate the connection.</span></span>

![시작 WiFi 구성 화면](../media/SetupWiFi/WiFiStartupConfig.png)

### <a name="option-2-default-app-configuration"></a><span data-ttu-id="166f4-142">옵션 2: 기본 앱 구성</span><span class="sxs-lookup"><span data-stu-id="166f4-142">Option 2: Default App Configuration</span></span>
<span data-ttu-id="166f4-143">**필수 구성 요소:** Windows 10 IoT core 장치에는 연결 된 마우스, 키보드, 디스플레이 및 USB WiFi 어댑터가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="166f4-143">**Prerequisite:** The Windows 10 IoT core device needs a mouse, keyboard, display, and USB WiFi Adapter plugged in</span></span>

<span data-ttu-id="166f4-144">WiFi를 구성 하는 다른 방법은 기본 앱을 사용 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="166f4-144">An alternative way to configure WiFi is to use the default app.</span></span> <span data-ttu-id="166f4-145">장치가 부팅 된 후이를 사용 하 여 WiFi 설정을 구성 하거나 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="166f4-145">You can use this to configure or modify WiFi settings after the device has booted.</span></span>

1. <span data-ttu-id="166f4-146">홈페이지에서 기어 모양의 설정 아이콘을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="166f4-146">Click on the gear-shaped settings icon on the homepage</span></span>
2. <span data-ttu-id="166f4-147">왼쪽 창에서 **네트워크 & wi-fi** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="166f4-147">Select **Network & Wi-Fi** in the left pane</span></span>
3. <span data-ttu-id="166f4-148">연결 하려는 WiFi 네트워크를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="166f4-148">Click on the WiFi network you want to connect to.</span></span> <span data-ttu-id="166f4-149">메시지가 표시 되 면 암호를 입력 하 고 **연결** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="166f4-149">Supply the password if prompted, and click **Connect**</span></span>

![기본 앱 WiFi 구성](../media/SetupWiFi/DefaultAppWiFiConfig.png)

## <a name="headless-options"></a><span data-ttu-id="166f4-151">헤드리스 옵션:</span><span class="sxs-lookup"><span data-stu-id="166f4-151">Headless Options:</span></span>




### <a name="option-1-web-based-configuration"></a><span data-ttu-id="166f4-152">옵션 1: 웹 기반 구성</span><span class="sxs-lookup"><span data-stu-id="166f4-152">Option 1: Web-Based Configuration</span></span>
<span data-ttu-id="166f4-153">**필수 구성 요소:** 장치는 이미 이더넷을 통해 로컬 네트워크에 연결 되어 있어야 하며 USB WiFi 어댑터가 연결 되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="166f4-153">**Prerequisite:** Your device will already need to be connected to your local network through Ethernet and should have a USB WiFi Adapter plugged in</span></span>

<span data-ttu-id="166f4-154">UI, 디스플레이 또는 입력 장치가 없는 장치 a를 사용 하는 경우에도 [Windows 장치 포털](../manage-your-device/DevicePortal.md)을 통해 장치를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="166f4-154">If you have device a with no UI, display, or input devices, you can still configure it through the [Windows Device Portal](../manage-your-device/DevicePortal.md).</span></span>
<span data-ttu-id="166f4-155">**Windows 10 IoT Core 대시보드**에서 장치에 대 한 **장치 포털에서 열기** 아이콘을 *클릭* 합니다.</span><span class="sxs-lookup"><span data-stu-id="166f4-155">In **Windows 10 IoT Core Dashboard**, *Click* on the **Open in Device Portal** icon for your device.</span></span>

<!-- This content is replicated at en-US/Docs/KitSetupRPI.md -->

1. <span data-ttu-id="166f4-156">사용자 이름에 **관리자** 를 입력 하 고 암호를 입력 합니다 (기본적으로p@ssw0rd).</span><span class="sxs-lookup"><span data-stu-id="166f4-156">Enter **Administrator** for the username, and supply your password (p@ssw0rd by default)</span></span>
2. <span data-ttu-id="166f4-157">왼쪽 창에서 **네트워크** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="166f4-157">Click on **Network** in the left-hand pane</span></span>
3. <span data-ttu-id="166f4-158">**사용 가능한 네트워크**에서 연결 하려는 네트워크를 선택 하 고 연결 자격 증명을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="166f4-158">Under **Available networks**, select network you would like to connect to and supply the connection credentials.</span></span> <span data-ttu-id="166f4-159">연결 **을 클릭 하** 여 연결을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="166f4-159">Click **Connect** to initiate the connection</span></span>

![웹 기반 WiFi 구성](../media/SetupWiFi/WebBWiFiConfig.png)

<!-- End of Replicated Content -->


### <a name="option-2-connect-using-wifi-profiles"></a><span data-ttu-id="166f4-161">옵션 2: WiFi 프로필을 사용 하 여 연결</span><span class="sxs-lookup"><span data-stu-id="166f4-161">Option 2: Connect using WiFi Profiles</span></span>

<span data-ttu-id="166f4-162">**필수 구성 요소:** 장치는 이미 이더넷을 통해 로컬 네트워크에 연결 되어 있어야 하며 USB WiFi 어댑터가 연결 되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="166f4-162">**Prerequisite:** Your device will already need to be connected to your local network through Ethernet and should have a USB WiFi Adapter plugged in.</span></span> <span data-ttu-id="166f4-163">또한 WiFi 기능이 포함 된 Windows PC가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="166f4-163">You also need a Windows PC with WiFi capability.</span></span>

<span data-ttu-id="166f4-164">무선 프로필을 사용 하 여 WiFi를 설정 하는 것은 Windows 10 IoT Core에서 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="166f4-164">Setting up WiFi using wireless profiles is supported in Windows 10 IoT Core.</span></span> <span data-ttu-id="166f4-165">자세한 내용과 예제는 [MSDN](https://msdn.microsoft.com/library/windows/desktop/aa369853) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="166f4-165">See [MSDN](https://msdn.microsoft.com/library/windows/desktop/aa369853) for details and examples.</span></span>

1. <span data-ttu-id="166f4-166">Windows PC를 원하는 무선 네트워크에 연결 하 고 다음 명령을 사용 하 여 WiFi 프로필 XML 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="166f4-166">Connect your Windows PC to the desired wireless network and create WiFi profile XML file with these commands:</span></span>

    * <span data-ttu-id="166f4-167">`netsh wlan show profiles` > 방금 추가한 프로필의 이름을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="166f4-167">`netsh wlan show profiles` -> find the name of the profile you just added</span></span>

    * <span data-ttu-id="166f4-168">`netsh wlan export profile name=<your profilename>`을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="166f4-168">`netsh wlan export profile name=<your profilename>`.</span></span> <span data-ttu-id="166f4-169">그러면 프로필이 XML 파일로 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="166f4-169">This will export the profile to an XML file</span></span>

2. <span data-ttu-id="166f4-170">**파일 탐색기** 창을 열고 주소 표시줄에 `\\<TARGET_DEVICE>\C$\`를 입력 한 다음 enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="166f4-170">Open up a **File Explorer** window, and in the address bar type `\\<TARGET_DEVICE>\C$\` and then hit enter.</span></span>  <span data-ttu-id="166f4-171">이 특정 경우에 `<TARGET_DEVICE>`은 Windows 10 IoT Core 장치의 이름 또는 IP 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="166f4-171">In this particular case, `<TARGET_DEVICE>` is either the name or the IP address of your Windows 10 IoT Core device:</span></span>

    ![파일 탐색기를 사용 하는 SMB](../media/SetupWifi/smb1.png)

    <span data-ttu-id="166f4-173">사용자 이름 및 암호를 입력 하 라는 메시지가 표시 되 면 다음 자격 증명을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="166f4-173">If you are prompted for a user name and password, use the following credentials:</span></span>

        User Name: <TARGET_DEVICE>\Administrator
        Password:  p@ssw0rd

    ![파일 탐색기를 사용 하는 SMB](../media/SetupWifi/cred1.png)

> [!NOTE]
> <span data-ttu-id="166f4-175">관리자 계정에 대 한 기본 암호를 업데이트 하는 것이 **좋습니다** .</span><span class="sxs-lookup"><span data-stu-id="166f4-175">It is **highly recommended** that you update the default password for the Administrator account.</span></span>  <span data-ttu-id="166f4-176">[여기](../connect-your-device/PowerShell.md)에 있는 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="166f4-176">Please follow the instructions found [here](../connect-your-device/PowerShell.md).</span></span>

3. <span data-ttu-id="166f4-177">Windows PC에서 Windows 10 IoT Core 장치로 내보낸 WiFi 프로필 XML 파일을 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="166f4-177">Copy the exported WiFi profile XML file from the Windows PC to your Windows 10 IoT Core device</span></span>

4. <span data-ttu-id="166f4-178">[PowerShell](../connect-your-device/PowerShell.md) 을 사용 하 여 장치에 연결 하 고 다음 명령을 실행 하 여 장치에 새 WiFi 프로필을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="166f4-178">Connect to your device using [PowerShell](../connect-your-device/PowerShell.md) and add the new WiFi profile to your device by executing the following commands</span></span>

    * `netsh wlan add profile filename=<copied XML path>`

    * `netsh wlan show profiles`

5. <span data-ttu-id="166f4-179">Netsh를 통해 Windows 10 IoT Core 장치를 무선 네트워크에 연결</span><span class="sxs-lookup"><span data-stu-id="166f4-179">Connect the Windows 10 IoT Core device to wireless network via netsh</span></span>

    * `netsh wlan connect name=<profile name>`

6. <span data-ttu-id="166f4-180">장치가 무선 네트워크에 연결 되어 있고 인터넷에 연결할 수 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="166f4-180">Verify that your device is connected to the wireless network and can reach the internet</span></span>

    * `netsh wlan show interfaces`

    * `ipconfig /all`

    * `ping /S <your WiFi adapter ip address> bing.com`


#### <a name="connecting-to-wpa2-psk-personal-networks"></a><span data-ttu-id="166f4-181">WPA2-PSK 개인 네트워크에 연결</span><span class="sxs-lookup"><span data-stu-id="166f4-181">Connecting to WPA2-PSK Personal networks</span></span>

<span data-ttu-id="166f4-182">WPA2-PSK 개인 WiFi 네트워크에 연결 해야 하는 경우 먼저 위의 지침을 따르고 XML 파일을 다음과 같이 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="166f4-182">If you need to connect to a WPA2-PSK Personal WiFi network, follow the instructions above first, but make the following changes to the XML file.</span></span> <span data-ttu-id="166f4-183">유일한 차이점은 Windows PC에서 XML을 내보낼 때 암호를 암호화 한다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="166f4-183">The only difference is that when your Windows PC exports the XML it encrypts the password.</span></span>

> [!WARNING] 
> <span data-ttu-id="166f4-184">이렇게 하면 연결이 안전 하지 않게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="166f4-184">This will make your connection insecure.</span></span>

<span data-ttu-id="166f4-185">Windows PC에서 내보낸 프로필 XML:</span><span class="sxs-lookup"><span data-stu-id="166f4-185">Profile XML exported from Windows PC:</span></span>

    <sharedKey>
        <keyType>passPhrase</keyType>
        <protected>true</protected>
        <keyMaterial><Your Encrypted password></keyMaterial>
    </sharedKey>


<span data-ttu-id="166f4-186">Windows 10 IoT Core에서 작업을 수행 하는 데 필요한 변경 사항:</span><span class="sxs-lookup"><span data-stu-id="166f4-186">Changes needed to work on Windows 10 IoT Core:</span></span>

    <sharedKey>
        <keyType>passPhrase</keyType>
        <protected>false</protected>
        <keyMaterial><Your Unencrypted password></keyMaterial>
    </sharedKey>
