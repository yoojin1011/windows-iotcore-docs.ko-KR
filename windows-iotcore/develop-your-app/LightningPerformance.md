---
title: 번개 성능 테스트
author: msalehmsft
ms.author: msaleh
ms.date: 08/28/2017
ms.topic: article
description: 다양 한 플랫폼과 언어에 대 한 Windows IoT 번개 기능 및 설정/해제 빈도에 대해 알아봅니다.
keywords: windows iot, 번개 성능, 기능 번개 GPIO
ms.openlocfilehash: 65f6732dd945b199902bb7eb4a9e0cc41aac2131
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513589"
---
# <a name="windows-iot-lightning-performance-testing"></a><span data-ttu-id="d388b-104">Windows IoT 번개 성능 테스트</span><span class="sxs-lookup"><span data-stu-id="d388b-104">Windows IoT Lightning Performance Testing</span></span>

<span data-ttu-id="d388b-105">GPIO 성능 간단한 GPIO 토글 앱을 사용 하 여 Windows IoT 번개 기능에 대해 테스트 되었습니다 [사용 가능한 여기](https://github.com/ms-iot/lightning/tree/develop/PerformanceTestSuite)합니다.</span><span class="sxs-lookup"><span data-stu-id="d388b-105">The GPIO performance was tested for Windows IoT Lightning functionality using a simple GPIO toggle app, [available here](https://github.com/ms-iot/lightning/tree/develop/PerformanceTestSuite).</span></span> <span data-ttu-id="d388b-106">테스트는 0-1 가능한 가장 빠른 속도로 GPIO 5로 전환 하 여 수행 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="d388b-106">The tests were performed by toggling GPIO 5 between 0 and 1 at the fastest possible speed.</span></span> <span data-ttu-id="d388b-107">각 사례에 대 한 토글 빈도 Tektronix TP 2024 Oscilloscope를 사용 하 여 측정 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="d388b-107">The toggle frequency for each case was measured using a Tektronix TPS 2024 Oscilloscope.</span></span>

<span data-ttu-id="d388b-108">다음 결과 분석에서 가져왔습니다.</span><span class="sxs-lookup"><span data-stu-id="d388b-108">The following results were obtained from the analysis:</span></span>

> | <span data-ttu-id="d388b-109">테스트 플랫폼</span><span class="sxs-lookup"><span data-stu-id="d388b-109">Platform Tested</span></span>                     | <span data-ttu-id="d388b-110">언어</span><span class="sxs-lookup"><span data-stu-id="d388b-110">Language</span></span>        | <span data-ttu-id="d388b-111">빈도</span><span class="sxs-lookup"><span data-stu-id="d388b-111">Frequency</span></span>     |
> | ----------------------------------- | --------------- | ------------- |
> | <span data-ttu-id="d388b-112">Arduino Uno</span><span class="sxs-lookup"><span data-stu-id="d388b-112">Arduino Uno</span></span>                         | <span data-ttu-id="d388b-113">Arduino 스케치</span><span class="sxs-lookup"><span data-stu-id="d388b-113">Arduino Sketch</span></span>  | <span data-ttu-id="d388b-114">75.06 kHz</span><span class="sxs-lookup"><span data-stu-id="d388b-114">75.06 kHz</span></span>     |
> | <span data-ttu-id="d388b-115">Windows 10 IoT Core 대 한 기본 스택</span><span class="sxs-lookup"><span data-stu-id="d388b-115">Windows 10 IoT Core Native Stack</span></span>    | <span data-ttu-id="d388b-116">C#</span><span class="sxs-lookup"><span data-stu-id="d388b-116">C#</span></span>              | <span data-ttu-id="d388b-117">239 kHz</span><span class="sxs-lookup"><span data-stu-id="d388b-117">239 KHz</span></span>       |
> | <span data-ttu-id="d388b-118">Windows 10 IoT Core 대 한 기본 스택</span><span class="sxs-lookup"><span data-stu-id="d388b-118">Windows 10 IoT Core Native Stack</span></span>    | <span data-ttu-id="d388b-119">C++/CX</span><span class="sxs-lookup"><span data-stu-id="d388b-119">C++/CX</span></span>          | <span data-ttu-id="d388b-120">278 kHz</span><span class="sxs-lookup"><span data-stu-id="d388b-120">278 kHz</span></span>       |
> | <span data-ttu-id="d388b-121">Windows 10 IoT Core 대 한 기본 스택</span><span class="sxs-lookup"><span data-stu-id="d388b-121">Windows 10 IoT Core Native Stack</span></span>    | <span data-ttu-id="d388b-122">WinJS</span><span class="sxs-lookup"><span data-stu-id="d388b-122">WinJS</span></span>           | <span data-ttu-id="d388b-123">34 kHz</span><span class="sxs-lookup"><span data-stu-id="d388b-123">34 kHz</span></span>        |
> | <span data-ttu-id="d388b-124">Windows 10 IoT Core Arduino 연결</span><span class="sxs-lookup"><span data-stu-id="d388b-124">Windows 10 IoT Core Arduino Wiring</span></span>  | <span data-ttu-id="d388b-125">Arduino 연결</span><span class="sxs-lookup"><span data-stu-id="d388b-125">Arduino Wiring</span></span>  | **<span data-ttu-id="d388b-126">7.36 MHz</span><span class="sxs-lookup"><span data-stu-id="d388b-126">7.36 MHz</span></span>**  |
> | <span data-ttu-id="d388b-127">Windows 10 IoT Core DMAP 스택</span><span class="sxs-lookup"><span data-stu-id="d388b-127">Windows 10 IoT Core DMAP Stack</span></span>      | <span data-ttu-id="d388b-128">C#</span><span class="sxs-lookup"><span data-stu-id="d388b-128">C#</span></span>              | **<span data-ttu-id="d388b-129">1.76 MHz</span><span class="sxs-lookup"><span data-stu-id="d388b-129">1.76 MHz</span></span>**  |
> | <span data-ttu-id="d388b-130">Windows 10 IoT Core DMAP 스택</span><span class="sxs-lookup"><span data-stu-id="d388b-130">Windows 10 IoT Core DMAP Stack</span></span>      | <span data-ttu-id="d388b-131">C++/CX</span><span class="sxs-lookup"><span data-stu-id="d388b-131">C++/CX</span></span>          | **<span data-ttu-id="d388b-132">3.78 MHz</span><span class="sxs-lookup"><span data-stu-id="d388b-132">3.78 MHz</span></span>**  |
> | <span data-ttu-id="d388b-133">Windows 10 IoT Core DMAP 스택</span><span class="sxs-lookup"><span data-stu-id="d388b-133">Windows 10 IoT Core DMAP Stack</span></span>      | <span data-ttu-id="d388b-134">WinJS</span><span class="sxs-lookup"><span data-stu-id="d388b-134">WinJS</span></span>           | <span data-ttu-id="d388b-135">42 kHz</span><span class="sxs-lookup"><span data-stu-id="d388b-135">42 kHz</span></span>        |

<span data-ttu-id="d388b-136">Windows 10 IoT Core Insider Preview 빌드 15026 (코드명 Redstone 2)를 사용 하 여 Raspberry Pi 3에서 실행 되었으며 Microsoft IoT 번개 SDK 1.1.0을 사용 하 여 작성 하는 Windows 10 IoT Core 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="d388b-136">Windows 10 IoT Core tests were run on a Raspberry Pi 3 using Windows 10 IoT Core Insider Preview Build 15026 (codename Redstone 2) and built using Microsoft IoT Lightning SDK 1.1.0.</span></span>
