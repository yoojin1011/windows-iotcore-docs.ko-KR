---
title: Windows 10 Iot Core 장치에서 WiFi Direct 사용
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: USB wifi 어댑터를 사용 하는 장치에서 wifi direct를 설정, 테스트 및 사용 하는 방법을 알아봅니다.
keywords: windows iot, wifi direct, 설정, wifi, 장치
ms.openlocfilehash: 04ecf1820356c59fecea81be47f69617ab42ab36
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "60169411"
---
# <a name="using-wifi-direct-on-your-windows-10-iot-core-device"></a><span data-ttu-id="41e29-104">Windows 10 IoT Core 장치에서 WiFi Direct 사용</span><span class="sxs-lookup"><span data-stu-id="41e29-104">Using WiFi Direct on your Windows 10 IoT Core device</span></span>

<span data-ttu-id="41e29-105">Wifi direct는 WiFi Direct가 설정 된 USB WiFi 어댑터를 사용 하 여 Windows 10 IoT Core 장치에서 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="41e29-105">WiFi Direct is supported on Windows 10 IoT Core devices through the use of a WiFi Direct enabled USB WiFi adapter.</span></span> <span data-ttu-id="41e29-106">WiFi Direct가 사용 하도록 설정 되었는지 확인 하려면 다음 두 가지를 충족 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="41e29-106">To make sure that WiFi Direct is enabled two things need to be true:</span></span>
* <span data-ttu-id="41e29-107">USB WiFi 어댑터의 하드웨어는 WiFi Direct를 지원 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="41e29-107">the hardware of the USB WiFi adapter needs to support WiFi Direct,</span></span>
* <span data-ttu-id="41e29-108">USB WiFi 어댑터의 해당 드라이버는 WiFi Direct를 지원 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="41e29-108">the corresponding driver of the USB WiFi adapter needs to support WiFi Direct.</span></span> 

<span data-ttu-id="41e29-109">WiFi Direct는 무선 AP (무선 액세스 지점)를 사용 하 여 연결을 설정할 필요 없이 WiFi 장치-장치 연결에 대 한 솔루션을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="41e29-109">WiFi Direct provides a solution for WiFi device-to-device connectivity without the need for either a Wireless Access Point (wireless AP) to setup the connection.</span></span> <span data-ttu-id="41e29-110">WiFiDirect로 수행할 수 있는 작업을 확인 하려면 [WiFiDirect 네임 스페이스](https://msdn.microsoft.com/library/windows/apps/windows.devices.wifidirect.aspx) 에서 제공 하는 UWP api를 살펴보세요.</span><span class="sxs-lookup"><span data-stu-id="41e29-110">Take a look at the UWP APIs available in the [Windows.Devices.WiFiDirect namespace](https://msdn.microsoft.com/library/windows/apps/windows.devices.wifidirect.aspx) to see what you can do with WiFiDirect.</span></span>

## <a name="supported-adapters"></a><span data-ttu-id="41e29-111">지원 되는 어댑터</span><span class="sxs-lookup"><span data-stu-id="41e29-111">Supported Adapters</span></span>

<span data-ttu-id="41e29-112">Windows 10 IoT Core에서 테스트 된 WiFi 어댑터의 목록은 [지원 되는 하드웨어](../learn-about-hardware/HardwareCompatList.md) 페이지에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41e29-112">A list of WiFi adapters that have been tested on Windows 10 IoT Core can be found on our [Supported Hardware](../learn-about-hardware/HardwareCompatList.md) page.</span></span> 

## <a name="basic-sample-for-wifi-direct"></a><span data-ttu-id="41e29-113">WiFi Direct 용 기본 샘플</span><span class="sxs-lookup"><span data-stu-id="41e29-113">Basic sample for WiFi Direct</span></span>

<span data-ttu-id="41e29-114">Wifi Direct UWP [샘플](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WiFiDirect)을 사용 하 여 wifi direct 기능을 쉽게 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41e29-114">You can easily test the WiFi Direct functionality with the WiFi Direct UWP [sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WiFiDirect).</span></span> <span data-ttu-id="41e29-115">C# 버전을 사용 하 고 두 개의 장치에 대 한 샘플을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="41e29-115">We will use the C# version and run the sample of two devices.</span></span>

### <a name="set-up-the-two-devices"></a><span data-ttu-id="41e29-116">두 장치 설정</span><span class="sxs-lookup"><span data-stu-id="41e29-116">Set up the two devices</span></span>
* <span data-ttu-id="41e29-117">MinnowBoardMax (MBM) Windows 10 IoT Core를 실행 하 고 있습니다 (지침 참조), CanaKit WiFi 동글을 사용</span><span class="sxs-lookup"><span data-stu-id="41e29-117">MinnowBoardMax (MBM) running Windows 10 IoT Core (see instructions here), with a CanaKit WiFi dongle</span></span>
* <span data-ttu-id="41e29-118">모니터, 키보드 및 마우스를 MBM에 연결</span><span class="sxs-lookup"><span data-stu-id="41e29-118">Connect monitor, keyboard and mouse to the MBM</span></span>
* <span data-ttu-id="41e29-119">최신 Windows 10 기념일 업데이트를 실행 하는 Windows 10 PC입니다.</span><span class="sxs-lookup"><span data-stu-id="41e29-119">A Windows 10 PC running the latest Windows 10 Anniversary Update.</span></span> <span data-ttu-id="41e29-120">PC (또는 랩톱)에는 WiFi Direct 지원이 있어야 합니다 (예: Microsoft Surface).</span><span class="sxs-lookup"><span data-stu-id="41e29-120">The PC (or laptop) will need to have WiFi Direct support (e.g. a Microsoft Surface)</span></span>
* <span data-ttu-id="41e29-121">Windows 10 PC에 Visual Studio 2017 설치</span><span class="sxs-lookup"><span data-stu-id="41e29-121">Install Visual Studio 2017 on your Windows 10 PC</span></span>
* <span data-ttu-id="41e29-122">WiFi Direct UWP [샘플](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WiFiDirect)(GitHub 리포지토리의 루트는 [여기](https://github.com/Microsoft/Windows-universal-samples)에 있습니다)을 복제 하거나 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="41e29-122">Clone or download the WiFi Direct UWP [sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WiFiDirect)(root of the GitHub repo is [here](https://github.com/Microsoft/Windows-universal-samples)).</span></span>
* <span data-ttu-id="41e29-123">Visual Studio C# 2017에서 WIFI Direct UWP 샘플의 버전을 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="41e29-123">Load the C# version of the WiFi Direct UWP sample in Visual Studio 2017</span></span>

#### <a name="run-the-sample-on-the-two-devices"></a><span data-ttu-id="41e29-124">두 장치에서 샘플 실행</span><span class="sxs-lookup"><span data-stu-id="41e29-124">Run the sample on the two devices</span></span>
* <span data-ttu-id="41e29-125">샘플을 컴파일하고 MBM에서 배포/실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="41e29-125">Compile the sample and deploy/run it on the MBM:</span></span>

    * <span data-ttu-id="41e29-126">"솔루션 플랫폼" combobox를 "x86"으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="41e29-126">Set the "Solution Platforms" combobox to "x86"</span></span>
    * <span data-ttu-id="41e29-127">"실행" 드롭다운에서 "원격 컴퓨터"를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="41e29-127">Select "Remote Machine" from the "Run" dropdown</span></span>
    * <span data-ttu-id="41e29-128">Ctrl + F5 키를 누르거나 "디버그" 메뉴에서 "디버깅 하지 않고 시작"을 선택 하 여, 디버깅 하지 않고 MBM에서 샘플을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="41e29-128">Start the sample on the MBM without debugging (either by pressing Ctrl-F5 or by selecting "Start Without Debugging" from the "Debug" menu)</span></span>
    * <span data-ttu-id="41e29-129">MBM에 연결 된 모니터에서 실행 중인 WiFi Direct 샘플이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="41e29-129">You should see the WiFi Direct sample running on the monitor connected to the MBM</span></span>
* <span data-ttu-id="41e29-130">샘플을 컴파일하고 Windows 10 PC에서 배포/실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="41e29-130">Compile the sample and deploy/run it on the Windows 10 PC:</span></span>
    * <span data-ttu-id="41e29-131">"솔루션 플랫폼" combobox를 "x86"으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="41e29-131">Set the "Solution Platforms" combobox to "x86"</span></span>
    * <span data-ttu-id="41e29-132">"실행" 드롭다운에서 "로컬"을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="41e29-132">Select "Local" from the "Run" dropdown</span></span>
    * <span data-ttu-id="41e29-133">샘플 (F5 또는 Ctrl + F5)을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="41e29-133">Start the sample (either F5 or Ctrl-F5)</span></span>
    * <span data-ttu-id="41e29-134">Windows 10 PC에서 실행 되는 WiFi Direct 샘플이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="41e29-134">You should see the WiFi Direct sample running on your Windows 10 PC</span></span>

### <a name="set-up-advertiser-and-connector"></a><span data-ttu-id="41e29-135">광고주 및 커넥터 설정</span><span class="sxs-lookup"><span data-stu-id="41e29-135">Set up Advertiser and Connector</span></span>
* <span data-ttu-id="41e29-136">MBM에서 (1) "광고주"를 선택 하 고 "보급 알림 시작" 단추를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="41e29-136">On the MBM, select (1) "Advertiser" and press the "Start Advertisement" button</span></span>

    * <span data-ttu-id="41e29-137">MBM이 WiFi Direct 채널에서 자체 보급을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="41e29-137">The MBM will start advertising itself on the WiFi Direct channel</span></span>

        ![광고주 구성 화면](../media/SetupWiFiDirect/Advertiser01.png)

        <span data-ttu-id="41e29-139">앱 아래쪽의 "보급 알림 상태" 배너를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="41e29-139">Notice the "Advertisement Status" banner at the bottom of the app.</span></span>
    
* <span data-ttu-id="41e29-140">Windows 10 PC에서 (2) "커넥터"를 선택 하 고 "감시자 시작" 단추를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="41e29-140">On the Windows 10 PC, select (2) "Connector" and press the "Start Watcher" button</span></span> 

    * <span data-ttu-id="41e29-141">사용 가능한 WiFi 직접 연결에 대 한 검색을 시작 하는 Windows 10 PC</span><span class="sxs-lookup"><span data-stu-id="41e29-141">The Windows 10 PC will start scanning for available WiFi Direct connections</span></span>
    * <span data-ttu-id="41e29-142">검색이 완료 되 면 "검색 된 장치" 목록에 MBM 이름이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="41e29-142">When the scanning is complete, you should see the name of your MBM in the "Discovered Devices" list</span></span>

        ![커넥터 구성 화면](../media/SetupWiFiDirect/Connector01.png)

        <span data-ttu-id="41e29-144">표시 되는 두 개의 장치 ("mbm01"에 관심 있음)와 "DeviceWatcher 열거 완료" 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="41e29-144">You can see two devices listed (we're interested in "ale-mbm01"), and the "DeviceWatcher enumeration completed" message.</span></span>

### <a name="pair-the-devices"></a><span data-ttu-id="41e29-145">장치 페어링</span><span class="sxs-lookup"><span data-stu-id="41e29-145">Pair the devices</span></span>
* <span data-ttu-id="41e29-146">Windows 10 PC의 "검색 된 장치" 목록에서 MBM (이 예제에서는 "ale-mbm01")을 선택 하 고 "연결" 단추를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="41e29-146">On the Windows 10 PC, select the MBM ("ale-mbm01" in our example) from the "Discovered Devices" list and press the "Connect" button</span></span>
* <span data-ttu-id="41e29-147">Windows 10 PC에서 "예"를 눌러 페어링 프로세스를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="41e29-147">On the Windows 10 PC, press "Yes" to initiate the pairing process</span></span>

    ![커넥터 시작 페어링](../media/SetupWiFiDirect/Connector02.png)

* <span data-ttu-id="41e29-149">MBM 모니터에서 PIN을 포함 하는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="41e29-149">On the MBM monitor you should a message with the PIN</span></span>

    ![광고주 고정 대화 상자](../media/SetupWiFiDirect/Advertiser02.png)

* <span data-ttu-id="41e29-151">Windows 10 PC에서 PIN을 입력 해야 하는 대화 상자가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="41e29-151">On the Windows 10 PC, you should see a dialog where you need to enter the PIN</span></span>

    ![커넥터 고정 대화 상자](../media/SetupWiFiDirect/Connector03.png)

### <a name="talk-on-the-channel"></a><span data-ttu-id="41e29-153">채널에 대 한 대화</span><span class="sxs-lookup"><span data-stu-id="41e29-153">Talk on the channel</span></span>
* <span data-ttu-id="41e29-154">두 장치를 연결 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="41e29-154">The two devices should be connected.</span></span> <span data-ttu-id="41e29-155">"연결 된 장치" 목록의 두 화면에 임의로 생성 된 장치 id (이 예제에서는 "hqffggg")가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="41e29-155">You should see a randomly generated device id ("hqffpzhz.ggg" in our example) on both screens in the "Connected Devices" list</span></span>

    ![광고주 연결 장치](../media/SetupWiFiDirect/Advertiser03.png)

    ![커넥터 연결 장치](../media/SetupWiFiDirect/Connector04.png)

* <span data-ttu-id="41e29-158">이제 전체 이중 채널 (또는 소켓)이 설정 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="41e29-158">You now have a full-duplex channel (or socket) set up</span></span>

    * <span data-ttu-id="41e29-159">MBM의 "연결 된 장치" 목록에서 장치 ("hqffggg")를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="41e29-159">on the MBM, select the device ("hqffpzhz.ggg") from the "Connected Devices" list</span></span>
    * <span data-ttu-id="41e29-160">"메시지 입력" 텍스트 상자에 메시지를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="41e29-160">type a message in the "Enter a message" textbox</span></span>
    * <span data-ttu-id="41e29-161">"보내기" 단추를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="41e29-161">press the "Send" button</span></span>
    * <span data-ttu-id="41e29-162">Windows 10 PC에서 메시지가 수신 되는 것을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41e29-162">you should see the message being received from the Windows 10 PC</span></span>
    * <span data-ttu-id="41e29-163">Windows 10 PC에서 MBM으로 메시지를 전송 해 보세요.</span><span class="sxs-lookup"><span data-stu-id="41e29-163">try sending a message from the Windows 10 PC to the MBM</span></span>
