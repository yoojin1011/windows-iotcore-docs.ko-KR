---
title: ETW(Windows용 이벤트 추적) IoT 코어
ms.date: 08/28/2017
ms.topic: article
description: 이벤트 추적을 사용 하 여 이벤트를 쓰고 Windows IoT Core에 대 한 이벤트를 사용 하는 방법을 알아봅니다.
keywords: windows iot, 이벤트 추적, ETW, windows 용 이벤트 추적, 장치
ms.openlocfilehash: e5d017c28640f78011ef0b7d82071a51524b2185
ms.sourcegitcommit: ea060254f9c4c25afcd0245c897b9e1425321859
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75721576"
---
# <a name="event-tracing-for-windows-iot-core"></a><span data-ttu-id="d1269-104">ETW(Windows용 이벤트 추적) IoT 코어</span><span class="sxs-lookup"><span data-stu-id="d1269-104">Event Tracing for Windows IoT Core</span></span>

<span data-ttu-id="d1269-105">ETW (ETW(Windows용 이벤트 추적))를 통해 개발자는 이벤트 추적 세션을 시작 및 중지 하 고, 응용 프로그램을 계측 하 여 추적 이벤트를 제공 하 고, 추적 이벤트를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d1269-105">Event Tracing for Windows (ETW) provides developers the ability to start and stop event tracing sessions, instrument an application to provide trace events, and consume trace events.</span></span>
<span data-ttu-id="d1269-106">Windows IoT Core 장치에서 ETW는 매니페스트 기반 이벤트와 클래식 이벤트를 모두 지원 하며, 다른 Windows 10 장치와는 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="d1269-106">ETW on Windows IoT Core devices supports both manifest-based and classic events, and is no different than other Windows 10 devices.</span></span>

<span data-ttu-id="d1269-107">이 섹션에서는 이벤트 작성 및 사용에 대 한 유용한 링크를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1269-107">This section will provide useful links on the basics of writing and consuming events.</span></span> <span data-ttu-id="d1269-108">[Windows 이벤트 추적 페이지](https://msdn.microsoft.com/library/windows/desktop/bb968803(v=vs.85).aspx)에서 자세한 정보를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1269-108">Find more detailed information from the [Windows Event Tracing page](https://msdn.microsoft.com/library/windows/desktop/bb968803(v=vs.85).aspx).</span></span>

## <a name="writing-events"></a><span data-ttu-id="d1269-109">이벤트 작성</span><span class="sxs-lookup"><span data-stu-id="d1269-109">Writing Events</span></span>

<span data-ttu-id="d1269-110">[Windows 유니버설 샘플 Github](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/Logging)의 일부로 이벤트를 작성 하는 여러 가지 방법을 구현 하는 UWP 샘플을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="d1269-110">Find a UWP sample that implements the different methods of writing events as part of the [Windows Universal Samples Github](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/Logging).</span></span>
<span data-ttu-id="d1269-111">이는 Windows IoT Core 장치에서 실행 되며 좋은 코드 참조 이기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1269-111">This will run on Windows IoT Core devices and is also a great code reference.</span></span>

<span data-ttu-id="d1269-112">이벤트 작성 및 Guid 가져오기에 대 한 자세한 가이드는 [여기](https://msdn.microsoft.com/library/windows/desktop/aa364161(v=vs.85).aspx)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d1269-112">Detailed guide on writing events and obtaining GUIDs can be found [here](https://msdn.microsoft.com/library/windows/desktop/aa364161(v=vs.85).aspx).</span></span>

## <a name="consuming-events"></a><span data-ttu-id="d1269-113">이벤트 소비</span><span class="sxs-lookup"><span data-stu-id="d1269-113">Consuming Events</span></span>

<span data-ttu-id="d1269-114">이벤트는 ETL 파일에 저장 되거나 실시간으로 캡처됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1269-114">Events are either saved to an ETL file or captured in real-time.</span></span>
<span data-ttu-id="d1269-115">[FTP](../connect-your-device/FTP.md) 또는 [windows 파일 공유](../manage-your-device/WindowsFileSharing.md) 를 사용 하 여 windows IOT Core 장치에서 ETL 파일을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1269-115">Use [FTP](../connect-your-device/FTP.md) or [Windows File Sharing](../manage-your-device/WindowsFileSharing.md) to retrieve ETL files from Windows IoT Core devices.</span></span>

## <a name="use-tools-in-windows-assessment-and-deployment-kit"></a><span data-ttu-id="d1269-116">Windows 평가 및 배포 키트의 도구 사용</span><span class="sxs-lookup"><span data-stu-id="d1269-116">Use Tools in Windows Assessment and Deployment Kit</span></span>

<span data-ttu-id="d1269-117">Windows 평가 및 배포 키트에는 이벤트를 캡처 및 분석 하는 데 유용한 3 가지 도구가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d1269-117">Windows Assessment and Deployment Kit includes 3 tools to help capture and analyze events.</span></span> [<span data-ttu-id="d1269-118">다운로드 하려면 여기를 클릭 하세요.</span><span class="sxs-lookup"><span data-stu-id="d1269-118">Click here to download</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=526740)


1. <span data-ttu-id="d1269-119">**Windows Performance Analyzer** 는 데스크톱에서 ETL 파일을 시각화 [여기](https://msdn.microsoft.com/library/windows/hardware/dn927319(v=vs.85).aspx)에 단계별 가이드를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1269-119">**Windows Performance Analyzer** visualizes ETL files on desktop, with a step by step guide [here](https://msdn.microsoft.com/library/windows/hardware/dn927319(v=vs.85).aspx).</span></span>

2. <span data-ttu-id="d1269-120">**Xperf 명령줄 도구** 는 실시간 이벤트를 캡처하고 ETL 파일에 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1269-120">**Xperf command line tool** captures real-time events and writes them to an ETL file.</span></span> <span data-ttu-id="d1269-121">이 도구는 Windows IoT Core 장치에 이미 설치 되어 있으므로 장치에서 다음 명령을 실행 하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1269-121">This tool is already installed on Windows IoT Core devices, just run the following commands on the devices:</span></span>

        // Start capturing events from specific GUID and save them to an ETL file
        xperf -start <Session Name> -f <ETL File> -on <GUID>

        // Stop capturing events with the specified session name
        xperf -stop <Session Name>


3. <span data-ttu-id="d1269-122">**Tracerpt 명령줄 도구** 는 ETL 파일을 xml 파일로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1269-122">**Tracerpt command line tool** converts ETL files into xml files.</span></span>

        // Generate dumpfile.xml from ETL file
        tracerpt <ETL File>


## <a name="use-device-portal"></a><span data-ttu-id="d1269-123">장치 포털 사용</span><span class="sxs-lookup"><span data-stu-id="d1269-123">Use Device Portal</span></span>

<span data-ttu-id="d1269-124">장치 포털은 [여기](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal)에 설명 된 대로 이벤트를 실시간으로 캡처할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d1269-124">Device portal can capture events in real-time, with instructions [here](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal).</span></span>

> [!NOTE]
> <span data-ttu-id="d1269-125">이 방법은 추가 분석을 위해 ETL 파일을 생성 하지 않지만 최소한의 설치를 요구 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1269-125">This method does not produce an ETL file for further analysis, but requires minimal setup.</span></span>

## <a name="use-function-calls"></a><span data-ttu-id="d1269-126">함수 호출 사용</span><span class="sxs-lookup"><span data-stu-id="d1269-126">Use Function Calls</span></span>

<span data-ttu-id="d1269-127">응용 프로그램에서 ETL 파일의 이벤트 또는 함수 호출을 사용 하 여 실시간으로 이벤트를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d1269-127">Enable an application to consume events from an ETL file or in real-time using function calls.</span></span>
<span data-ttu-id="d1269-128">[여기](https://msdn.microsoft.com/library/windows/desktop/aa363692(v=vs.85).aspx)에서 이러한 함수를 사용 하는 방법을 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="d1269-128">Learn how to use these functions [here](https://msdn.microsoft.com/library/windows/desktop/aa363692(v=vs.85).aspx).</span></span>
