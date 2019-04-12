---
title: Windows IoT Core에 대 한 이벤트 추적
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 이벤트를 작성 하 고 Windows IoT Core에 대 한 이벤트를 사용할 이벤트 추적을 사용 하는 방법에 알아봅니다.
keywords: windows iot 장치 windows 용 이벤트 추적, ETW, 이벤트 추적
ms.openlocfilehash: 7e01681e2af2ed8913614ba23bd12dfd36bcd76e
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59515194"
---
# <a name="event-tracing-for-windows-iot-core"></a><span data-ttu-id="da512-104">Windows IoT Core에 대 한 이벤트 추적</span><span class="sxs-lookup"><span data-stu-id="da512-104">Event Tracing for Windows IoT Core</span></span>

<span data-ttu-id="da512-105">이벤트 추적에 대 한 Windows (ETW) 개발자 시작 및 추적 이벤트를 제공 하 고 추적 이벤트를 사용 하려면 응용 프로그램 계측 이벤트 추적 세션을 중지 하는 기능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="da512-105">Event Tracing for Windows (ETW) provides developers the ability to start and stop event tracing sessions, instrument an application to provide trace events, and consume trace events.</span></span>
<span data-ttu-id="da512-106">Windows IoT Core 장치에서 ETW 매니페스트 기반 및 클래식 이벤트를 지원 하며 다른 Windows 10 장치에 차이가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="da512-106">ETW on Windows IoT Core devices supports both manifest-based and classic events, and is no different than other Windows 10 devices.</span></span>

<span data-ttu-id="da512-107">이 섹션에서는 작성 하 고 이벤트의 기본 사항에 대 한 유용한 링크를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="da512-107">This section will provide useful links on the basics of writing and consuming events.</span></span> <span data-ttu-id="da512-108">자세한 정보를 찾을 합니다 [Windows 이벤트 추적 페이지](https://msdn.microsoft.com/library/windows/desktop/bb968803(v=vs.85).aspx)합니다.</span><span class="sxs-lookup"><span data-stu-id="da512-108">Find more detailed information from the [Windows Event Tracing page](https://msdn.microsoft.com/library/windows/desktop/bb968803(v=vs.85).aspx).</span></span>

## <a name="writing-events"></a><span data-ttu-id="da512-109">쓰기 이벤트</span><span class="sxs-lookup"><span data-stu-id="da512-109">Writing Events</span></span>

<span data-ttu-id="da512-110">이벤트의 일부로 작성 하는 다른 메서드를 구현 하는 UWP 샘플 찾기 합니다 [Windows 유니버설 샘플 Github](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/Logging)합니다.</span><span class="sxs-lookup"><span data-stu-id="da512-110">Find a UWP sample that implements the different methods of writing events as part of the [Windows Universal Samples Github](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/Logging).</span></span>
<span data-ttu-id="da512-111">이 Windows IoT Core 장치에서 실행 되 고 훌륭한 코드 참조 이기도.</span><span class="sxs-lookup"><span data-stu-id="da512-111">This will run on Windows IoT Core devices and is also a great code reference.</span></span>

<span data-ttu-id="da512-112">이벤트를 작성 하 고 Guid 가져오기에 대 한 자세한 가이드를 찾을 수 있습니다 [여기](https://msdn.microsoft.com/library/windows/desktop/aa364161(v=vs.85).aspx)합니다.</span><span class="sxs-lookup"><span data-stu-id="da512-112">Detailed guide on writing events and obtaining GUIDs can be found [here](https://msdn.microsoft.com/library/windows/desktop/aa364161(v=vs.85).aspx).</span></span>

## <a name="consuming-events"></a><span data-ttu-id="da512-113">이벤트 사용</span><span class="sxs-lookup"><span data-stu-id="da512-113">Consuming Events</span></span>

<span data-ttu-id="da512-114">이벤트는 ETL 파일에 저장 또는 실시간에 캡처됩니다.</span><span class="sxs-lookup"><span data-stu-id="da512-114">Events are either saved to an ETL file or captured in real-time.</span></span>
<span data-ttu-id="da512-115">사용 하 여 [FTP](../connect-your-device/FTP.md) 하거나 [Windows 파일 공유](../manage-your-device/WindowsFileSharing.md) Windows IoT Core 장치에서 ETL 파일을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="da512-115">Use [FTP](../connect-your-device/FTP.md) or [Windows File Sharing](../manage-your-device/WindowsFileSharing.md) to retrieve ETL files from Windows IoT Core devices.</span></span>

## <a name="use-tools-in-windows-assessment-and-deployment-kit"></a><span data-ttu-id="da512-116">Windows 평가 및 배포 키트의 도구를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="da512-116">Use Tools in Windows Assessment and Deployment Kit</span></span>

<span data-ttu-id="da512-117">Windows Assessment and Deployment Kit를 캡처 및 이벤트를 분석 하는 데 3 도구를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="da512-117">Windows Assessment and Deployment Kit includes 3 tools to help capture and analyze events.</span></span> [<span data-ttu-id="da512-118">다운로드 하려면 여기를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="da512-118">Click here to download</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=526740)


1. <span data-ttu-id="da512-119">**Windows Performance Analyzer** 단계별 가이드를 사용 하 여 바탕 화면에서 ETL 파일을 시각화 [여기](https://msdn.microsoft.com/library/windows/hardware/dn927319(v=vs.85).aspx)합니다.</span><span class="sxs-lookup"><span data-stu-id="da512-119">**Windows Performance Analyzer** visualizes ETL files on desktop, with a step by step guide [here](https://msdn.microsoft.com/library/windows/hardware/dn927319(v=vs.85).aspx).</span></span>

2. <span data-ttu-id="da512-120">**Xperf 명령줄 도구** 실시간 이벤트를 캡처하고 ETL 파일에 씁니다.</span><span class="sxs-lookup"><span data-stu-id="da512-120">**Xperf command line tool** captures real-time events and writes them to an ETL file.</span></span> <span data-ttu-id="da512-121">이 도구에 이미 설치 되어 Windows IoT Core 장치, 장치에서 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="da512-121">This tool is already installed on Windows IoT Core devices, just run the following commands on the devices:</span></span>

        // Start capturing events from specific GUID and save them to an ETL file
        xperf -start <Session Name> -f <ETL File> -on <GUID>

        // Stop capturing events with the specified session name
        xperf -stop <Session Name>


3. <span data-ttu-id="da512-122">**Tracerpt 명령줄 도구** ETL 파일을 xml 파일로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="da512-122">**Tracerpt command line tool** converts ETL files into xml files.</span></span>

        // Generate dumpfile.xml from ETL file
        tracerpt <ETL File>


## <a name="use-device-portal"></a><span data-ttu-id="da512-123">장치 포털 사용</span><span class="sxs-lookup"><span data-stu-id="da512-123">Use Device Portal</span></span>

<span data-ttu-id="da512-124">장치 포털에서 이벤트를 캡처할 수 지침을 사용 하 여 실시간 [여기](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal)합니다.</span><span class="sxs-lookup"><span data-stu-id="da512-124">Device portal can capture events in real-time, with instructions [here](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal).</span></span>

> [!NOTE]
> <span data-ttu-id="da512-125">이 메서드 추가 분석을 위해 ETL 파일을 생성 하지 않지만 최소 설정이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="da512-125">This method does not produce an ETL file for further analysis, but requires minimal setup.</span></span>

## <a name="use-function-calls"></a><span data-ttu-id="da512-126">사용 하 여 함수 호출</span><span class="sxs-lookup"><span data-stu-id="da512-126">Use Function Calls</span></span>

<span data-ttu-id="da512-127">함수 호출을 사용 하는 ETL 파일에서 또는 실시간 이벤트를 사용 하는 응용 프로그램 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="da512-127">Enable an application to consume events from an ETL file or in real-time using function calls.</span></span>
<span data-ttu-id="da512-128">이러한 함수를 사용 하는 방법을 알아봅니다 [여기](https://msdn.microsoft.com/library/windows/desktop/aa363692(v=vs.85).aspx)합니다.</span><span class="sxs-lookup"><span data-stu-id="da512-128">Learn how to use these functions [here](https://msdn.microsoft.com/library/windows/desktop/aa363692(v=vs.85).aspx).</span></span>
