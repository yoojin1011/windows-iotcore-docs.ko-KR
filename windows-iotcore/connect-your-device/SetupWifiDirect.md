---
title: Windows 10 Iot Core 장치에서 WiFi Direct를 사용 하 여
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 설치, 테스트 및 활성화 된 USB 어댑터를 사용 하 여 장치에서 wifi direct를 사용 하는 방법에 알아봅니다.
keywords: windows iot "," wifi 직접 "," 설치 "," wifi "," 장치
ms.openlocfilehash: 04ecf1820356c59fecea81be47f69617ab42ab36
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513405"
---
# <a name="using-wifi-direct-on-your-windows-10-iot-core-device"></a><span data-ttu-id="1d541-104">Windows 10 IoT Core 장치에서 WiFi Direct를 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="1d541-104">Using WiFi Direct on your Windows 10 IoT Core device</span></span>

<span data-ttu-id="1d541-105">WiFi 직접 지원 되는 WiFi 직접 사용 하 여 장치에서 Windows 10 IoT Core USB 어댑터를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d541-105">WiFi Direct is supported on Windows 10 IoT Core devices through the use of a WiFi Direct enabled USB WiFi adapter.</span></span> <span data-ttu-id="1d541-106">WiFi 직접 두 가지 작업을 사용 하도록 설정된 되었는지 확인 하려면 true 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d541-106">To make sure that WiFi Direct is enabled two things need to be true:</span></span>
* <span data-ttu-id="1d541-107">USB 어댑터의 하드웨어를 WiFi Direct를 지원 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d541-107">the hardware of the USB WiFi adapter needs to support WiFi Direct,</span></span>
* <span data-ttu-id="1d541-108">USB 어댑터의 해당 하는 드라이버는 WiFi Direct를 지원 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d541-108">the corresponding driver of the USB WiFi adapter needs to support WiFi Direct.</span></span> 

<span data-ttu-id="1d541-109">WiFi 직접 연결을 설정 하거나 무선 액세스 지점 (무선 AP)에 대 한 필요 없이 WiFi 장치-장치 연결에 대 한 솔루션을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d541-109">WiFi Direct provides a solution for WiFi device-to-device connectivity without the need for either a Wireless Access Point (wireless AP) to setup the connection.</span></span> <span data-ttu-id="1d541-110">사용 가능한 UWP Api를 살펴보세요를 [Windows.Devices.WiFiDirect 네임 스페이스](https://msdn.microsoft.com/library/windows/apps/windows.devices.wifidirect.aspx) WiFiDirect를 사용 하 여 수행할 수 있는 작업을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d541-110">Take a look at the UWP APIs available in the [Windows.Devices.WiFiDirect namespace](https://msdn.microsoft.com/library/windows/apps/windows.devices.wifidirect.aspx) to see what you can do with WiFiDirect.</span></span>

## <a name="supported-adapters"></a><span data-ttu-id="1d541-111">지원 되는 어댑터</span><span class="sxs-lookup"><span data-stu-id="1d541-111">Supported Adapters</span></span>

<span data-ttu-id="1d541-112">Windows 10 IoT Core 테스트 된 WiFi 어댑터 목록을 복지부 우리의 [지원 되는 하드웨어](../learn-about-hardware/HardwareCompatList.md) 페이지.</span><span class="sxs-lookup"><span data-stu-id="1d541-112">A list of WiFi adapters that have been tested on Windows 10 IoT Core can be found on our [Supported Hardware](../learn-about-hardware/HardwareCompatList.md) page.</span></span> 

## <a name="basic-sample-for-wifi-direct"></a><span data-ttu-id="1d541-113">WiFi Direct에 대 한 기본 샘플</span><span class="sxs-lookup"><span data-stu-id="1d541-113">Basic sample for WiFi Direct</span></span>

<span data-ttu-id="1d541-114">WiFi 직접 UWP를 사용 하 여 WiFi 직접 기능을 쉽게 테스트할 수 있습니다 [샘플](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WiFiDirect)합니다.</span><span class="sxs-lookup"><span data-stu-id="1d541-114">You can easily test the WiFi Direct functionality with the WiFi Direct UWP [sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WiFiDirect).</span></span> <span data-ttu-id="1d541-115">사용 하 여는 C# 버전 및 두 개의 장치의 샘플을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d541-115">We will use the C# version and run the sample of two devices.</span></span>

### <a name="set-up-the-two-devices"></a><span data-ttu-id="1d541-116">두 개의 장치 설정</span><span class="sxs-lookup"><span data-stu-id="1d541-116">Set up the two devices</span></span>
* <span data-ttu-id="1d541-117">MinnowBoardMax MBM () Windows 10 IoT Core 실행 (여기의 지침 참조), CanaKit WiFi 동글을 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="1d541-117">MinnowBoardMax (MBM) running Windows 10 IoT Core (see instructions here), with a CanaKit WiFi dongle</span></span>
* <span data-ttu-id="1d541-118">모니터, 키보드 및 마우스를 MBM 연결</span><span class="sxs-lookup"><span data-stu-id="1d541-118">Connect monitor, keyboard and mouse to the MBM</span></span>
* <span data-ttu-id="1d541-119">최신 Windows 10 1 주년 업데이트를 실행 하는 Windows 10 PC.</span><span class="sxs-lookup"><span data-stu-id="1d541-119">A Windows 10 PC running the latest Windows 10 Anniversary Update.</span></span> <span data-ttu-id="1d541-120">PC (또는 랩톱) 해야 합니다 (예: Microsoft Surface) 지원 되는 WiFi 직접</span><span class="sxs-lookup"><span data-stu-id="1d541-120">The PC (or laptop) will need to have WiFi Direct support (e.g. a Microsoft Surface)</span></span>
* <span data-ttu-id="1d541-121">Windows 10 PC에서 Visual Studio 2017 설치</span><span class="sxs-lookup"><span data-stu-id="1d541-121">Install Visual Studio 2017 on your Windows 10 PC</span></span>
* <span data-ttu-id="1d541-122">복제 또는 다운로드 WiFi 직접 UWP [샘플](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WiFiDirect)(GitHub 리포지토리의 루트가 [여기](https://github.com/Microsoft/Windows-universal-samples)).</span><span class="sxs-lookup"><span data-stu-id="1d541-122">Clone or download the WiFi Direct UWP [sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WiFiDirect)(root of the GitHub repo is [here](https://github.com/Microsoft/Windows-universal-samples)).</span></span>
* <span data-ttu-id="1d541-123">부하는 C# 버전의 Visual Studio 2017에서 WiFi 직접 UWP 샘플</span><span class="sxs-lookup"><span data-stu-id="1d541-123">Load the C# version of the WiFi Direct UWP sample in Visual Studio 2017</span></span>

#### <a name="run-the-sample-on-the-two-devices"></a><span data-ttu-id="1d541-124">두 장치에서 샘플을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d541-124">Run the sample on the two devices</span></span>
* <span data-ttu-id="1d541-125">샘플 컴파일 및 배포/실행 하는 MBM에서:</span><span class="sxs-lookup"><span data-stu-id="1d541-125">Compile the sample and deploy/run it on the MBM:</span></span>

    * <span data-ttu-id="1d541-126">"솔루션 플랫폼" combobox "x86"으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d541-126">Set the "Solution Platforms" combobox to "x86"</span></span>
    * <span data-ttu-id="1d541-127">"실행" 드롭다운 목록에서 "원격 컴퓨터"를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d541-127">Select "Remote Machine" from the "Run" dropdown</span></span>
    * <span data-ttu-id="1d541-128">(Ctrl-F5 키를 눌러 또는 "디버그" 메뉴에서 "디버깅 하지 않고 시작"을 선택 하 여) 디버깅 하지 않고는 MBM에서 샘플 시작</span><span class="sxs-lookup"><span data-stu-id="1d541-128">Start the sample on the MBM without debugging (either by pressing Ctrl-F5 or by selecting "Start Without Debugging" from the "Debug" menu)</span></span>
    * <span data-ttu-id="1d541-129">MBM 연결 모니터에서 실행 되는 WiFi 직접 샘플을 표시</span><span class="sxs-lookup"><span data-stu-id="1d541-129">You should see the WiFi Direct sample running on the monitor connected to the MBM</span></span>
* <span data-ttu-id="1d541-130">샘플 컴파일 및 배포/실행 하는 Windows 10 PC에서:</span><span class="sxs-lookup"><span data-stu-id="1d541-130">Compile the sample and deploy/run it on the Windows 10 PC:</span></span>
    * <span data-ttu-id="1d541-131">"솔루션 플랫폼" combobox "x86"으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d541-131">Set the "Solution Platforms" combobox to "x86"</span></span>
    * <span data-ttu-id="1d541-132">"실행" 드롭다운에서 "Local" 선택</span><span class="sxs-lookup"><span data-stu-id="1d541-132">Select "Local" from the "Run" dropdown</span></span>
    * <span data-ttu-id="1d541-133">(F5 또는 ctrl+f5) 샘플 시작</span><span class="sxs-lookup"><span data-stu-id="1d541-133">Start the sample (either F5 or Ctrl-F5)</span></span>
    * <span data-ttu-id="1d541-134">Windows 10 PC에서 실행 되는 WiFi 직접 샘플을 표시</span><span class="sxs-lookup"><span data-stu-id="1d541-134">You should see the WiFi Direct sample running on your Windows 10 PC</span></span>

### <a name="set-up-advertiser-and-connector"></a><span data-ttu-id="1d541-135">광고 및 커넥터 설정</span><span class="sxs-lookup"><span data-stu-id="1d541-135">Set up Advertiser and Connector</span></span>
* <span data-ttu-id="1d541-136">MBM에서 (1) "광고"를 선택 하 고 "광고 시작" 단추</span><span class="sxs-lookup"><span data-stu-id="1d541-136">On the MBM, select (1) "Advertiser" and press the "Start Advertisement" button</span></span>

    * <span data-ttu-id="1d541-137">자체 WiFi 직접 채널에서 광고를 MBM 시작</span><span class="sxs-lookup"><span data-stu-id="1d541-137">The MBM will start advertising itself on the WiFi Direct channel</span></span>

        ![광고 구성 화면](../media/SetupWiFiDirect/Advertiser01.png)

        <span data-ttu-id="1d541-139">앱의 맨 아래에 "보급 알림 상태" 배너를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d541-139">Notice the "Advertisement Status" banner at the bottom of the app.</span></span>
    
* <span data-ttu-id="1d541-140">Windows 10 PC에서 (2) "커넥터"를 선택 하 고 "감시자 시작" 단추</span><span class="sxs-lookup"><span data-stu-id="1d541-140">On the Windows 10 PC, select (2) "Connector" and press the "Start Watcher" button</span></span> 

    * <span data-ttu-id="1d541-141">Windows 10 PC는 사용 가능한 WiFi 직접 연결에 대 한 검색을 시작합니다</span><span class="sxs-lookup"><span data-stu-id="1d541-141">The Windows 10 PC will start scanning for available WiFi Direct connections</span></span>
    * <span data-ttu-id="1d541-142">검색이 완료 되 면 "검색 된 장치" 목록의 MBM 프로그램의 이름을 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1d541-142">When the scanning is complete, you should see the name of your MBM in the "Discovered Devices" list</span></span>

        ![커넥터 구성 화면](../media/SetupWiFiDirect/Connector01.png)

        <span data-ttu-id="1d541-144">나열 된 두 개의 장치를 볼 수 있습니다 (에 관심이 "ale mbm01"), 및 "DeviceWatcher 열거형 완료" 메시지입니다.</span><span class="sxs-lookup"><span data-stu-id="1d541-144">You can see two devices listed (we're interested in "ale-mbm01"), and the "DeviceWatcher enumeration completed" message.</span></span>

### <a name="pair-the-devices"></a><span data-ttu-id="1d541-145">장치 쌍</span><span class="sxs-lookup"><span data-stu-id="1d541-145">Pair the devices</span></span>
* <span data-ttu-id="1d541-146">Windows 10 PC에서 "검색 된 장치" 목록의 MBM ("ale-mbm01" 예제의)를 선택 하 고 "연결" 단추를 눌러</span><span class="sxs-lookup"><span data-stu-id="1d541-146">On the Windows 10 PC, select the MBM ("ale-mbm01" in our example) from the "Discovered Devices" list and press the "Connect" button</span></span>
* <span data-ttu-id="1d541-147">Windows 10 PC에 연결 하는 프로세스를 시작 하려면 "예" 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="1d541-147">On the Windows 10 PC, press "Yes" to initiate the pairing process</span></span>

    ![커넥터 시작 페어링](../media/SetupWiFiDirect/Connector02.png)

* <span data-ttu-id="1d541-149">PIN 사용 하 여 메시지를 수행 해야 MBM 모니터</span><span class="sxs-lookup"><span data-stu-id="1d541-149">On the MBM monitor you should a message with the PIN</span></span>

    ![광고 PIN 대화 상자](../media/SetupWiFiDirect/Advertiser02.png)

* <span data-ttu-id="1d541-151">Windows 10 PC에서 하는 대화 상자가 표시 됩니다 PIN을 입력 해야 하는</span><span class="sxs-lookup"><span data-stu-id="1d541-151">On the Windows 10 PC, you should see a dialog where you need to enter the PIN</span></span>

    ![커넥터 핀 대화 상자](../media/SetupWiFiDirect/Connector03.png)

### <a name="talk-on-the-channel"></a><span data-ttu-id="1d541-153">채널에서 통신 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d541-153">Talk on the channel</span></span>
* <span data-ttu-id="1d541-154">두 개의 장치를 연결 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d541-154">The two devices should be connected.</span></span> <span data-ttu-id="1d541-155">임의로 생성 된 장치 id (이 예제의 경우 "hqffpzhz.ggg") "연결 된 장치" 목록의 양쪽 화면에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1d541-155">You should see a randomly generated device id ("hqffpzhz.ggg" in our example) on both screens in the "Connected Devices" list</span></span>

    ![광고 연결 된 장치](../media/SetupWiFiDirect/Advertiser03.png)

    ![커넥터 연결 된 장치](../media/SetupWiFiDirect/Connector04.png)

* <span data-ttu-id="1d541-158">이제는 전체 이중 채널 (또는 소켓) 설정</span><span class="sxs-lookup"><span data-stu-id="1d541-158">You now have a full-duplex channel (or socket) set up</span></span>

    * <span data-ttu-id="1d541-159">MBM, 장치 ("hqffpzhz.ggg") "연결 된 장치" 목록에서 선택</span><span class="sxs-lookup"><span data-stu-id="1d541-159">on the MBM, select the device ("hqffpzhz.ggg") from the "Connected Devices" list</span></span>
    * <span data-ttu-id="1d541-160">"메시지를 입력 합니다." 텍스트 상자에 메시지를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d541-160">type a message in the "Enter a message" textbox</span></span>
    * <span data-ttu-id="1d541-161">"보내기" 단추를 클릭</span><span class="sxs-lookup"><span data-stu-id="1d541-161">press the "Send" button</span></span>
    * <span data-ttu-id="1d541-162">Windows 10 PC에서 수신 되는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1d541-162">you should see the message being received from the Windows 10 PC</span></span>
    * <span data-ttu-id="1d541-163">Windows 10 PC에서 MBM는 메시지를 보내기 시도</span><span class="sxs-lookup"><span data-stu-id="1d541-163">try sending a message from the Windows 10 PC to the MBM</span></span>
