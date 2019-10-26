---
title: 네트워크 패킷 캡처
ms.date: 08/28/2017
ms.topic: article
description: Microsoft Message Analyzer를 사용 하 여 네트워크 패킷 캡처를 사용 하도록 설정 하는 방법을 알아봅니다.
keywords: windows iot, 네트워크 패킷, 네트워크 패킷 캡처, Microsoft Message Analyzer, PowerShell
ms.openlocfilehash: 593b6f4f8650e074666dda06feb88e6afccf5e61
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72917425"
---
# <a name="network-packet-capture"></a><span data-ttu-id="8825c-104">네트워크 패킷 캡처</span><span class="sxs-lookup"><span data-stu-id="8825c-104">Network packet capture</span></span>

<span data-ttu-id="8825c-105">[Microsoft Message Analyzer](http://www.microsoft.com/en-us/download/details.aspx?id=44226) 를 사용 하 여 Windows 10 IoT Core 장치에서 프로토콜 메시징 트래픽을 캡처, 표시 및 분석할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8825c-105">You can use [Microsoft Message Analyzer](http://www.microsoft.com/en-us/download/details.aspx?id=44226) to capture, display, and analyze protocol messaging traffic on your Windows 10 IoT Core device.</span></span>

![메시지 분석기](../media/NetworkPacketCapture/message-analyzer.png)

## <a name="prerequisites"></a><span data-ttu-id="8825c-107">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="8825c-107">Prerequisites</span></span>

<span data-ttu-id="8825c-108">Powershell 연결 작업 ( [powershell](../connect-your-device/PowerShell.md)에서 설명 하는 1 ~ 8 단계).</span><span class="sxs-lookup"><span data-stu-id="8825c-108">Working PowerShell Connection (Step 1 to 8 described at [PowerShell](../connect-your-device/PowerShell.md).</span></span>

## <a name="set-up-your-device"></a><span data-ttu-id="8825c-109">장치 설정</span><span class="sxs-lookup"><span data-stu-id="8825c-109">Set up your device</span></span>

<span data-ttu-id="8825c-110">메시지 분석기를 사용 하 여 장치에 연결 하려면 먼저 장치 이름을 변경 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8825c-110">In order to connect to your device using Message Analyzer, you need to first rename your device.</span></span>  <span data-ttu-id="8825c-111">`setcomputername` 명령을 사용 하 여 [SSH](../connect-your-device/SSH.md) 또는 [PowerShell](../connect-your-device/PowerShell.md) 을 통해 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8825c-111">This can be done through [SSH](../connect-your-device/SSH.md) or [PowerShell](../connect-your-device/PowerShell.md) using the `setcomputername` command.</span></span>

![PowerShell 장치 이름 바꾸기](../media/NetworkPacketCapture/powershell-rename-device.png)

<span data-ttu-id="8825c-113">장치의 이름을 바꾼 후 장치를 다시 부팅 하 여 이름 변경을 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8825c-113">After you rename your device, reboot the device to apply the name change.</span></span>

## <a name="turn-off-the-firewall"></a><span data-ttu-id="8825c-114">방화벽 해제</span><span class="sxs-lookup"><span data-stu-id="8825c-114">Turn off the firewall</span></span>

<span data-ttu-id="8825c-115">PowerShell 또는 SSH를 사용 하 여 장치에 연결 하 고 다음 명령을 실행 하 여 방화벽을 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8825c-115">Connect to your device using PowerShell or SSH and run the following command to disable the firewall.</span></span>
    
    netsh advfirewall set allprofiles state off
    
## <a name="connect-to-your-device-using-message-analyzer"></a><span data-ttu-id="8825c-116">메시지 분석기를 사용 하 여 장치에 연결</span><span class="sxs-lookup"><span data-stu-id="8825c-116">Connect to your device using Message Analyzer</span></span>

<span data-ttu-id="8825c-117">이제 장치가 설정 되었으므로 Microsoft Message Analyzer를 사용 하 여 연결 하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="8825c-117">Now that your device is set up, let's connect to it using Microsoft Message Analyzer.</span></span>

1. <span data-ttu-id="8825c-118">[Microsoft Message Analyzer](http://www.microsoft.com/en-us/download/details.aspx?id=44226)를 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="8825c-118">Download the [Microsoft Message Analyzer](http://www.microsoft.com/en-us/download/details.aspx?id=44226).</span></span>
2. <span data-ttu-id="8825c-119">메시지 분석기를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="8825c-119">Open Message Analyzer.</span></span>
3. <span data-ttu-id="8825c-120">`New Session`를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8825c-120">Click on `New Session`.</span></span>

    ![메시지 분석기](../media/NetworkPacketCapture/message-analyzer-new-session.png)
4. <span data-ttu-id="8825c-122">열리는 창에서 `Live Trace` 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8825c-122">In the window that opens, click on the `Live Trace` button.</span></span>
    <span data-ttu-id="8825c-123">![Message Analyzer](../media/NetworkPacketCapture/message-analyzer-live-trace.png)</span><span class="sxs-lookup"><span data-stu-id="8825c-123">![Message Analyzer](../media/NetworkPacketCapture/message-analyzer-live-trace.png)</span></span>
5. <span data-ttu-id="8825c-124">`Edit...` 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8825c-124">Click on the `Edit...` button.</span></span>
    <span data-ttu-id="8825c-125">![Message Analyzer](../media/NetworkPacketCapture/message-analyzer-edit-button.png)</span><span class="sxs-lookup"><span data-stu-id="8825c-125">![Message Analyzer](../media/NetworkPacketCapture/message-analyzer-edit-button.png)</span></span>
6. <span data-ttu-id="8825c-126">Localhost를 IoT 장치의 이름으로 바꾸고 관리자 사용자 이름 및 암호를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="8825c-126">Replace Localhost with the name of your IoT device, and enter the administrator user name and password.</span></span>  <span data-ttu-id="8825c-127">그런 다음 `OK`를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8825c-127">Then click `OK`.</span></span>
    <span data-ttu-id="8825c-128">![Message Analyzer](../media/NetworkPacketCapture/message-analyzer-edit-target-computers.png)</span><span class="sxs-lookup"><span data-stu-id="8825c-128">![Message Analyzer](../media/NetworkPacketCapture/message-analyzer-edit-target-computers.png)</span></span>
7. <span data-ttu-id="8825c-129">`Select a trace scenario` 드롭다운을 클릭 하 고 `Local Network Interfaces`을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="8825c-129">Click on the `Select a trace scenario` dropdown and select `Local Network Interfaces`.</span></span>
    <span data-ttu-id="8825c-130">![Message Analyzer](../media/NetworkPacketCapture/message-analyzer-trace-scenario.png)</span><span class="sxs-lookup"><span data-stu-id="8825c-130">![Message Analyzer](../media/NetworkPacketCapture/message-analyzer-trace-scenario.png)</span></span>
8. <span data-ttu-id="8825c-131">`Start` 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8825c-131">Click the `Start` button.</span></span>
9. <span data-ttu-id="8825c-132">장치에서 네트워크 인터페이스를 통과 하는 메시지가 표시 되기 시작 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8825c-132">You should start to see the messages going through the network interfaces on your device.</span></span>
    <span data-ttu-id="8825c-133">![Message Analyzer](../media/NetworkPacketCapture/message-analyzer.png)</span><span class="sxs-lookup"><span data-stu-id="8825c-133">![Message Analyzer](../media/NetworkPacketCapture/message-analyzer.png)</span></span>
10. <span data-ttu-id="8825c-134">메시지 분석기를 통해 추적을 시작한 후 장치의 [웹 인터페이스](DevicePortal.md)에서 패킷 캡처 드라이버의 ETW 메시지도 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8825c-134">After you start the trace through Message Analyzer, you can also view the ETW messages from the packet capture driver in your device's [web interface](DevicePortal.md).</span></span>  <span data-ttu-id="8825c-135">이렇게 하려면 웹 인터페이스의 ETW 탭으로 이동 하 여 `Registered providers` 드롭다운 메뉴에서 `Microsoft-Windows-NDIS-PacketCapture`를 선택 하 고 `Enable` 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8825c-135">To do this, go to the ETW tab of the web interface, select `Microsoft-Windows-NDIS-PacketCapture` from the `Registered providers` dropdown menu and click the `Enable` button.</span></span>
    <span data-ttu-id="8825c-136">![Message Analyzer](../media/NetworkPacketCapture/web-etw.png)</span><span class="sxs-lookup"><span data-stu-id="8825c-136">![Message Analyzer](../media/NetworkPacketCapture/web-etw.png)</span></span>    
