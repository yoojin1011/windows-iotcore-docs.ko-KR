---
title: Windows 10 IoT Core 장치에서 WiFi를 사용 하 여
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 사용, 설치 및 Windows 10 IoT Core 장치에서 wifi를 구성 하는 방법에 알아봅니다.
keywords: windows iot, wifi, 설치, 장치
ms.openlocfilehash: 20f61114323baa60c8052038df68a8c172ce1c95
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513398"
---
# <a name="using-wifi-on-your-windows-10-iot-core-device"></a><span data-ttu-id="d9b32-104">Windows 10 IoT Core 장치에서 WiFi를 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="d9b32-104">Using WiFi on your Windows 10 IoT Core device</span></span>

<span data-ttu-id="d9b32-105">WiFi는 WiFi USB 어댑터를 사용 하 여 Windows 10 IoT Core 장치에서 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9b32-105">WiFi is supported on Windows 10 IoT Core devices through the use of a USB WiFi adapter.</span></span> <span data-ttu-id="d9b32-106">WiFi를 사용 하 여 유선된 된 연결의 모든 기능을 제공 등 [SSH](../connect-your-device/SSH.md)를 [Powershell](../connect-your-device/PowerShell.md)를 [Windows Device Portal](../manage-your-device/DevicePortal.md), 응용 프로그램 디버깅 및 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b32-106">Using WiFi provides all the functionality of a wired connection, including [SSH](../connect-your-device/SSH.md), [Powershell](../connect-your-device/PowerShell.md), [Windows Device Portal](../manage-your-device/DevicePortal.md), and application debugging and deployment.</span></span>

> [!NOTE]
> <span data-ttu-id="d9b32-107">유선된 이더넷 케이블을 연결의 기본 네트워크 인터페이스로 WiFi를 재정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b32-107">Plugging in a wired Ethernet cable will override WiFi as the default network interface.</span></span>

### <a name="supported-adapters"></a><span data-ttu-id="d9b32-108">지원 되는 어댑터</span><span class="sxs-lookup"><span data-stu-id="d9b32-108">Supported Adapters</span></span>
<span data-ttu-id="d9b32-109">Windows 10 IoT Core 테스트 된 WiFi 어댑터 목록을 복지부 우리의 [지원 되는 하드웨어](../learn-about-hardware/HardwareCompatList.md) 페이지.</span><span class="sxs-lookup"><span data-stu-id="d9b32-109">A list of WiFi adapters that have been tested on Windows 10 IoT Core can be found on our [Supported Hardware](../learn-about-hardware/HardwareCompatList.md) page.</span></span>

### <a name="configuring-wifi"></a><span data-ttu-id="d9b32-110">WiFi 구성</span><span class="sxs-lookup"><span data-stu-id="d9b32-110">Configuring WiFi</span></span>
<span data-ttu-id="d9b32-111">WiFi를 사용 하려면 Windows 10 IoT core WiFi 네트워크 자격 증명을 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b32-111">To use WiFi, you'll need to provide Windows 10 IoT core with the WiFi network credentials.</span></span> <span data-ttu-id="d9b32-112">도우미 앱 및 WPS 사용자 지정 솔루션을 빌드하는 방법에 대 한 설명서, 외에도 따라서 아래에 나열 된 수행 하기 위한 몇 가지 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9b32-112">In addition to documentation on how to build companion app and WPS custom solutions, there are a few different options for doing so listed below.</span></span>

## <a name="custom-companion-app--wps-wi-fi-onboarding-samples"></a><span data-ttu-id="d9b32-113">사용자 지정 도우미 앱 및 WPS Wi-fi 온 보 딩 샘플</span><span class="sxs-lookup"><span data-stu-id="d9b32-113">Custom Companion App & WPS Wi-Fi Onboarding Samples</span></span>

<span data-ttu-id="d9b32-114">현재 다양 한 장치에 대 한 사용자 지정 wifi 온 보 딩 솔루션을 구축 하는 개발자를 위한 방법 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b32-114">Currently, we offer a number of ways for developers to build a custom wifi onboarding solution for their device.</span></span> 

> | <span data-ttu-id="d9b32-115">샘플</span><span class="sxs-lookup"><span data-stu-id="d9b32-115">Samples</span></span> | <span data-ttu-id="d9b32-116">설명</span><span class="sxs-lookup"><span data-stu-id="d9b32-116">Description</span></span> | <span data-ttu-id="d9b32-117">이점</span><span class="sxs-lookup"><span data-stu-id="d9b32-117">Benefits</span></span>  |  <span data-ttu-id="d9b32-118">단점</span><span class="sxs-lookup"><span data-stu-id="d9b32-118">Drawbacks</span></span>  |
> |-------------|----------|---------|---------|
> | [<span data-ttu-id="d9b32-119">도우미 앱</span><span class="sxs-lookup"><span data-stu-id="d9b32-119">Companion App</span></span>](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/CompanionApp) | <span data-ttu-id="d9b32-120">장치의 Wi-fi를 구성할 수 있는 간단한 Xamarin 앱을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d9b32-120">Create a simple Xamarin app that can configure your device's Wi-Fi.</span></span> |  <span data-ttu-id="d9b32-121">간단 하 게 지정 해야 합니다. 헤드 또는 IoT Core;에 대 한 헤드리스 클라이언트는 플랫폼 간 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b32-121">Simple to use; Headed or headless for IoT Core; Clients work cross-platform</span></span> | <span data-ttu-id="d9b32-122">개발자가 자신의 프로토콜; 만드는 보안을 구현 하는 개발자</span><span class="sxs-lookup"><span data-stu-id="d9b32-122">Developer is creating his or her own protocol; requires developer to implement security</span></span> |
> | [<span data-ttu-id="d9b32-123">Bluetooth RFCOMM를 사용 하 여 IoT 온 보 딩</span><span class="sxs-lookup"><span data-stu-id="d9b32-123">IoT Onboarding with Bluetooth RFCOMM</span></span>](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/IoTOnboarding_RFCOMM) | <span data-ttu-id="d9b32-124">헤드리스 IoT 장치에서 Wi-fi를 사용 하 여 연결을 구성 하는 솔루션을 만들 Bluetooth RFCOMM를 사용 하 여 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b32-124">Create solution to configure your headless IoT device to connect with your Wi-Fi using Bluetooth RFCOMM.</span></span>  | <span data-ttu-id="d9b32-125">헤드 또는 헤드리스 장치에서 관련 친숙 한 기술 및 개념을 사용 하 여 IoT 장치 SoftAP;를 시작 하지 않아도 방화벽 설정을 조정할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d9b32-125">Relevant in headed or headless devices; Uses familiar technologies and concepts; Does not require IoT device to start a SoftAP; Does not need to adjust firewall settings</span></span> | <span data-ttu-id="d9b32-126">클라이언트 및 서버 장치에 대 한 Bluetooth 지원이 필요 샘플은 Windows 10에 대 한 클라이언트 앱 제공 서버 앱 사전-defines/하드 코드 클라이언트 장치의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="d9b32-126">Requires Bluetooth support for client and server devices; Sample only provides client app for Windows 10; Server app pre-defines/hard-codes the names of the client device.</span></span> |
> | [<span data-ttu-id="d9b32-127">AllJoyn 사용 하 여 IoT 온 보 딩</span><span class="sxs-lookup"><span data-stu-id="d9b32-127">IoT Onboarding with AllJoyn</span></span>](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/IoTOnboarding) | <span data-ttu-id="d9b32-128">홈 Wi-fi 네트워크를 사용 하 여 헤드리스 IoT 장치를 원격으로 조인 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b32-128">Remotely join your headless IoT device with your home Wi-Fi network.</span></span> | <span data-ttu-id="d9b32-129">AllJoyn 사용</span><span class="sxs-lookup"><span data-stu-id="d9b32-129">Works with AllJoyn</span></span> | <span data-ttu-id="d9b32-130">AllJoyn에 대 한 지원이 사용 되지 않음</span><span class="sxs-lookup"><span data-stu-id="d9b32-130">Some support for AllJoyn is deprecated</span></span> |
> | <span data-ttu-id="d9b32-131">-Fi 보호 설정 (WPS) 장치에 대 한 Api</span><span class="sxs-lookup"><span data-stu-id="d9b32-131">Wi-Fi Protected Setup (WPS) APIs for devices</span></span> | <span data-ttu-id="d9b32-132">네트워크에서 지 원하는 WPS 메서드 쿼리 WPS 검색을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b32-132">Perform WPS discovery to query the WPS methods supported by the network.</span></span> | <span data-ttu-id="d9b32-133">단순히 활용 합니다 [WiFiAdapter.GetWpsConfigurationAsync (WiFiAvailableNetwork](https://docs.microsoft.com/uwp/api/windows.devices.wifi.wifiadapter.getwpsconfigurationasync) 및 [WiFiAdapter.ConnectAsync](https://docs.microsoft.com/uwp/api/windows.devices.wifi.wifiadapter.connectasync) wi-fi 장치 특정 네트워크에 연결 하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="d9b32-133">Simply leverage the [WiFiAdapter.GetWpsConfigurationAsync(WiFiAvailableNetwork](https://docs.microsoft.com/uwp/api/windows.devices.wifi.wifiadapter.getwpsconfigurationasync) and [WiFiAdapter.ConnectAsync](https://docs.microsoft.com/uwp/api/windows.devices.wifi.wifiadapter.connectasync) methods to connect wi-fi devices to specific networks.</span></span> | <span data-ttu-id="d9b32-134">활용 하려면 이러한 Api를 사용 하 여 파악 해야 합니다.; WPS 사용 라우터를 사용 하 여 호환 될 뿐</span><span class="sxs-lookup"><span data-stu-id="d9b32-134">You will need to become familiar with these APIs to leverage them.; only compatible with WPS-enabled routers</span></span>|

## <a name="headed-options"></a><span data-ttu-id="d9b32-135">헤드 옵션:</span><span class="sxs-lookup"><span data-stu-id="d9b32-135">Headed Options:</span></span>

### <a name="option-1-startup-configuration"></a><span data-ttu-id="d9b32-136">옵션 1: 시작 구성</span><span class="sxs-lookup"><span data-stu-id="d9b32-136">Option 1: Startup Configuration</span></span>
<span data-ttu-id="d9b32-137">**필수 구성 요소:** Windows 10 IoT core 장치 마우스, 키보드, 표시 하며 USB 어댑터 연결</span><span class="sxs-lookup"><span data-stu-id="d9b32-137">**Prerequisite:** The Windows 10 IoT core device needs a mouse, keyboard, display, and USB WiFi Adapter plugged in</span></span>

<span data-ttu-id="d9b32-138">첫 번째 Windows 10 IoT Core 지원 되는 WiFi USB 어댑터를 사용 하 여 부팅 구성 화면이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9b32-138">The first time you boot Windows 10 IoT Core with a supported USB WiFi adapter, you will be presented with a configuration screen.</span></span>
<span data-ttu-id="d9b32-139">구성 화면에서 연결 하 고 암호를 입력 하려는 WiFi 네트워크를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b32-139">On the configuration screen, select the WiFi network you would like to connect to and supply the password.</span></span> <span data-ttu-id="d9b32-140">클릭 **연결** 의 연결을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b32-140">Click **connect** to initiate the connection.</span></span>

![시작 WiFi 구성 화면](../media/SetupWiFi/WiFiStartupConfig.png)

### <a name="option-2-default-app-configuration"></a><span data-ttu-id="d9b32-142">옵션 2: 기본 앱 구성</span><span class="sxs-lookup"><span data-stu-id="d9b32-142">Option 2: Default App Configuration</span></span>
<span data-ttu-id="d9b32-143">**필수 구성 요소:** Windows 10 IoT core 장치 마우스, 키보드, 표시 하며 USB 어댑터 연결</span><span class="sxs-lookup"><span data-stu-id="d9b32-143">**Prerequisite:** The Windows 10 IoT core device needs a mouse, keyboard, display, and USB WiFi Adapter plugged in</span></span>

<span data-ttu-id="d9b32-144">WiFi를 구성 하는 다른 방법은 기본 앱을 사용 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="d9b32-144">An alternative way to configure WiFi is to use the default app.</span></span> <span data-ttu-id="d9b32-145">이 설정을 구성 하거나 수정할 WiFi 장치가 부팅 한 후에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9b32-145">You can use this to configure or modify WiFi settings after the device has booted.</span></span>

1. <span data-ttu-id="d9b32-146">홈 페이지에서 기어 모양의 설정 아이콘 클릭</span><span class="sxs-lookup"><span data-stu-id="d9b32-146">Click on the gear-shaped settings icon on the homepage</span></span>
2. <span data-ttu-id="d9b32-147">선택 **네트워크 및 Wi-fi** 왼쪽된 창에서</span><span class="sxs-lookup"><span data-stu-id="d9b32-147">Select **Network & Wi-Fi** in the left pane</span></span>
3. <span data-ttu-id="d9b32-148">에 연결 하려는 WiFi 네트워크를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b32-148">Click on the WiFi network you want to connect to.</span></span> <span data-ttu-id="d9b32-149">메시지가 표시 되 면 암호를 입력 하 고 클릭 **연결**</span><span class="sxs-lookup"><span data-stu-id="d9b32-149">Supply the password if prompted, and click **Connect**</span></span>

![기본 앱 WiFi 구성](../media/SetupWiFi/DefaultAppWiFiConfig.png)

## <a name="headless-options"></a><span data-ttu-id="d9b32-151">헤드리스 옵션:</span><span class="sxs-lookup"><span data-stu-id="d9b32-151">Headless Options:</span></span>




### <a name="option-1-web-based-configuration"></a><span data-ttu-id="d9b32-152">옵션 1: 웹 기반 구성</span><span class="sxs-lookup"><span data-stu-id="d9b32-152">Option 1: Web-Based Configuration</span></span>
<span data-ttu-id="d9b32-153">**필수 구성 요소:** 장치에 이미 이더넷을 통해 로컬 네트워크에 연결 해야 하 고 해야 WiFi USB 어댑터를 연결한 없는</span><span class="sxs-lookup"><span data-stu-id="d9b32-153">**Prerequisite:** Your device will already need to be connected to your local network through Ethernet and should have a USB WiFi Adapter plugged in</span></span>

<span data-ttu-id="d9b32-154">장치가 있는 경우는 UI, 표시 또는 입력된 장치를 사용 하 여 구성할 수 있습니다 통해 합니다 [Windows Device Portal](../manage-your-device/DevicePortal.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b32-154">If you have device a with no UI, display, or input devices, you can still configure it through the [Windows Device Portal](../manage-your-device/DevicePortal.md).</span></span>
<span data-ttu-id="d9b32-155">**Windows 10 IoT Core 대시보드**를 *클릭* 에 **장치 포털에서 열기** 장치에 대 한 아이콘입니다.</span><span class="sxs-lookup"><span data-stu-id="d9b32-155">In **Windows 10 IoT Core Dashboard**, *Click* on the **Open in Device Portal** icon for your device.</span></span>

<!-- This content is replicated at en-US/Docs/KitSetupRPI.md -->

1. <span data-ttu-id="d9b32-156">입력 **관리자** 사용자 이름에 대 한 사용자 암호를 입력 하 고 (p@ssw0rd 기본적으로)</span><span class="sxs-lookup"><span data-stu-id="d9b32-156">Enter **Administrator** for the username, and supply your password (p@ssw0rd by default)</span></span>
2. <span data-ttu-id="d9b32-157">클릭할 **네트워크** 왼쪽 창에서</span><span class="sxs-lookup"><span data-stu-id="d9b32-157">Click on **Network** in the left-hand pane</span></span>
3. <span data-ttu-id="d9b32-158">아래 **사용 가능한 네트워크**선택, 네트워크에 연결 하 고 연결 자격 증명을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b32-158">Under **Available networks**, select network you would like to connect to and supply the connection credentials.</span></span> <span data-ttu-id="d9b32-159">클릭 **Connect** 연결 시작 하려면</span><span class="sxs-lookup"><span data-stu-id="d9b32-159">Click **Connect** to initiate the connection</span></span>

![웹 기반 WiFi 구성](../media/SetupWiFi/WebBWiFiConfig.png)

<!-- End of Replicated Content -->


### <a name="option-2-connect-using-wifi-profiles"></a><span data-ttu-id="d9b32-161">옵션 2: Wi-fi 프로필을 사용 하 여 연결</span><span class="sxs-lookup"><span data-stu-id="d9b32-161">Option 2: Connect using WiFi Profiles</span></span>

<span data-ttu-id="d9b32-162">**필수 구성 요소:** 장치에 이미 이더넷을 통해 로컬 네트워크에 연결 해야 하 고 해야 WiFi USB 어댑터를 연결한 없는 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b32-162">**Prerequisite:** Your device will already need to be connected to your local network through Ethernet and should have a USB WiFi Adapter plugged in.</span></span> <span data-ttu-id="d9b32-163">WiFi 기능을 사용 하 여 Windows PC를 해야합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b32-163">You also need a Windows PC with WiFi capability.</span></span>

<span data-ttu-id="d9b32-164">무선 프로필을 사용 하 여 WiFi 설정는 Windows 10 IoT Core 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9b32-164">Setting up WiFi using wireless profiles is supported in Windows 10 IoT Core.</span></span> <span data-ttu-id="d9b32-165">참조 [MSDN](https://msdn.microsoft.com/library/windows/desktop/aa369853) 세부 정보 및 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="d9b32-165">See [MSDN](https://msdn.microsoft.com/library/windows/desktop/aa369853) for details and examples.</span></span>

1. <span data-ttu-id="d9b32-166">Windows PC를 원하는 무선 네트워크에 연결 하 고 이러한 명령을 사용 하 여 WiFi 프로필 XML 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d9b32-166">Connect your Windows PC to the desired wireless network and create WiFi profile XML file with these commands:</span></span>

    * `netsh wlan show profiles` <span data-ttu-id="d9b32-167">-> 방금 추가한 프로필의 이름 찾기</span><span class="sxs-lookup"><span data-stu-id="d9b32-167">-> find the name of the profile you just added</span></span>

    * `netsh wlan export profile name=<your profilename>`<span data-ttu-id="d9b32-168">.</span><span class="sxs-lookup"><span data-stu-id="d9b32-168">.</span></span> <span data-ttu-id="d9b32-169">프로필을 XML 파일로 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="d9b32-169">This will export the profile to an XML file</span></span>

2. <span data-ttu-id="d9b32-170">엽니다는 **파일 탐색기** 창에 주소 표시줄 유형 `\\<TARGET_DEVICE>\C$\` 및 입력 한 다음 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="d9b32-170">Open up a **File Explorer** window, and in the address bar type `\\<TARGET_DEVICE>\C$\` and then hit enter.</span></span>  <span data-ttu-id="d9b32-171">이 특정 예제의 `<TARGET_DEVICE>` 이름 또는 Windows 10 IoT Core 장치 IP 주소 중 하나:</span><span class="sxs-lookup"><span data-stu-id="d9b32-171">In this particular case, `<TARGET_DEVICE>` is either the name or the IP address of your Windows 10 IoT Core device:</span></span>

    ![파일 탐색기를 사용 하 여 SMB](../media/SetupWifi/smb1.png)

    <span data-ttu-id="d9b32-173">사용자 이름 및 암호에 대 한 메시지가 표시 되 면 다음 자격 증명을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b32-173">If you are prompted for a user name and password, use the following credentials:</span></span>

        User Name: <TARGET_DEVICE>\Administrator
        Password:  p@ssw0rd

    ![파일 탐색기를 사용 하 여 SMB](../media/SetupWifi/cred1.png)

> [!NOTE]
> <span data-ttu-id="d9b32-175">것 **좋습니다** 관리자 계정에 대 한 기본 암호를 업데이트 하는 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b32-175">It is **highly recommended** that you update the default password for the Administrator account.</span></span>  <span data-ttu-id="d9b32-176">지침을 따르세요 [여기](../connect-your-device/PowerShell.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b32-176">Please follow the instructions found [here](../connect-your-device/PowerShell.md).</span></span>

3. <span data-ttu-id="d9b32-177">Windows 10 IoT Core 장치에 Windows PC에서 내보낸된 WiFi 프로필 XML 파일을 복사</span><span class="sxs-lookup"><span data-stu-id="d9b32-177">Copy the exported WiFi profile XML file from the Windows PC to your Windows 10 IoT Core device</span></span>

4. <span data-ttu-id="d9b32-178">사용 하 여 장치에 연결할 [PowerShell](../connect-your-device/PowerShell.md) 하 고 다음 명령을 실행 하 여 장치에 새 Wi-fi 프로필 추가</span><span class="sxs-lookup"><span data-stu-id="d9b32-178">Connect to your device using [PowerShell](../connect-your-device/PowerShell.md) and add the new WiFi profile to your device by executing the following commands</span></span>

    * `netsh wlan add profile filename=<copied XML path>`

    * `netsh wlan show profiles`

5. <span data-ttu-id="d9b32-179">Windows 10 IoT Core 장치 netsh 통해 무선 네트워크에 연결</span><span class="sxs-lookup"><span data-stu-id="d9b32-179">Connect the Windows 10 IoT Core device to wireless network via netsh</span></span>

    * `netsh wlan connect name=<profile name>`

6. <span data-ttu-id="d9b32-180">장치의 무선 네트워크에 연결 되어 및 인터넷에 연결할 수 있는지를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b32-180">Verify that your device is connected to the wireless network and can reach the internet</span></span>

    * `netsh wlan show interfaces`

    * `ipconfig /all`

    * `ping /S <your WiFi adapter ip address> bing.com`


#### <a name="connecting-to-wpa2-psk-personal-networks"></a><span data-ttu-id="d9b32-181">WPA2-PSK 개인 네트워크에 연결</span><span class="sxs-lookup"><span data-stu-id="d9b32-181">Connecting to WPA2-PSK Personal networks</span></span>

<span data-ttu-id="d9b32-182">WPA2-PSK 개인 WiFi 네트워크에 연결 해야 하는 경우 위의 지침을 먼저 수행 하지만 XML 파일에 다음과 같이 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b32-182">If you need to connect to a WPA2-PSK Personal WiFi network, follow the instructions above first, but make the following changes to the XML file.</span></span> <span data-ttu-id="d9b32-183">유일한 차이점은 Windows PC XML을 내보낼 때 암호화 암호입니다.</span><span class="sxs-lookup"><span data-stu-id="d9b32-183">The only difference is that when your Windows PC exports the XML it encrypts the password.</span></span>

> [!WARNING] 
> <span data-ttu-id="d9b32-184">이렇게 하면 연결이 안전 하지 않은 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b32-184">This will make your connection insecure.</span></span>

<span data-ttu-id="d9b32-185">Windows PC에서 내보낸 되는 XML 프로필:</span><span class="sxs-lookup"><span data-stu-id="d9b32-185">Profile XML exported from Windows PC:</span></span>

    <sharedKey>
        <keyType>passPhrase</keyType>
        <protected>true</protected>
        <keyMaterial><Your Encrypted password></keyMaterial>
    </sharedKey>


<span data-ttu-id="d9b32-186">Windows 10 IoT Core 작동 하는 데 필요한 변경 내용:</span><span class="sxs-lookup"><span data-stu-id="d9b32-186">Changes needed to work on Windows 10 IoT Core:</span></span>

    <sharedKey>
        <keyType>passPhrase</keyType>
        <protected>false</protected>
        <keyMaterial><Your Unencrypted password></keyMaterial>
    </sharedKey>
