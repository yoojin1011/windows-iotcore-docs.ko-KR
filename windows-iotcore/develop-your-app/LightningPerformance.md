---
title: 번개 성능 테스트
author: msalehmsft
ms.author: msaleh
ms.date: 08/28/2017
ms.topic: article
description: 다양 한 플랫폼과 언어에 대 한 Windows IoT 번개 기능 및 설정/해제 빈도에 대해 알아봅니다.
keywords: windows iot, 번개 성능, 기능 번개 GPIO
ms.openlocfilehash: e7d57f72f6db85fbb8e453943c87e8ee31ef8a40
ms.sourcegitcommit: cbea9d713986fbe8b85e1bba1561a000188bd91c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64744785"
---
# <a name="windows-iot-lightning-performance-testing"></a><span data-ttu-id="64a0b-104">Windows IoT 번개 성능 테스트</span><span class="sxs-lookup"><span data-stu-id="64a0b-104">Windows IoT Lightning Performance Testing</span></span>

> [!IMPORTANT]
> <span data-ttu-id="64a0b-105">Windows 10 IoT 팀 Arduino 지 원하는 더 이상 적극적으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="64a0b-105">The Windows 10 IoT team is no longer actively supporting Arduino.</span></span>

<span data-ttu-id="64a0b-106">GPIO 성능 간단한 GPIO 토글 앱을 사용 하 여 Windows IoT 번개 기능에 대해 테스트 되었습니다 [사용 가능한 여기](https://github.com/ms-iot/lightning/tree/develop/PerformanceTestSuite)합니다.</span><span class="sxs-lookup"><span data-stu-id="64a0b-106">The GPIO performance was tested for Windows IoT Lightning functionality using a simple GPIO toggle app, [available here](https://github.com/ms-iot/lightning/tree/develop/PerformanceTestSuite).</span></span> <span data-ttu-id="64a0b-107">테스트는 0-1 가능한 가장 빠른 속도로 GPIO 5로 전환 하 여 수행 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="64a0b-107">The tests were performed by toggling GPIO 5 between 0 and 1 at the fastest possible speed.</span></span> <span data-ttu-id="64a0b-108">각 사례에 대 한 토글 빈도 Tektronix TP 2024 Oscilloscope를 사용 하 여 측정 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="64a0b-108">The toggle frequency for each case was measured using a Tektronix TPS 2024 Oscilloscope.</span></span>

<span data-ttu-id="64a0b-109">다음 결과 분석에서 가져왔습니다.</span><span class="sxs-lookup"><span data-stu-id="64a0b-109">The following results were obtained from the analysis:</span></span>

> | <span data-ttu-id="64a0b-110">테스트 플랫폼</span><span class="sxs-lookup"><span data-stu-id="64a0b-110">Platform Tested</span></span>                     | <span data-ttu-id="64a0b-111">언어</span><span class="sxs-lookup"><span data-stu-id="64a0b-111">Language</span></span>        | <span data-ttu-id="64a0b-112">빈도</span><span class="sxs-lookup"><span data-stu-id="64a0b-112">Frequency</span></span>     |
> | ----------------------------------- | --------------- | ------------- |
> | <span data-ttu-id="64a0b-113">Arduino Uno</span><span class="sxs-lookup"><span data-stu-id="64a0b-113">Arduino Uno</span></span>                         | <span data-ttu-id="64a0b-114">Arduino 스케치</span><span class="sxs-lookup"><span data-stu-id="64a0b-114">Arduino Sketch</span></span>  | <span data-ttu-id="64a0b-115">75.06 kHz</span><span class="sxs-lookup"><span data-stu-id="64a0b-115">75.06 kHz</span></span>     |
> | <span data-ttu-id="64a0b-116">Windows 10 IoT Core 대 한 기본 스택</span><span class="sxs-lookup"><span data-stu-id="64a0b-116">Windows 10 IoT Core Native Stack</span></span>    | <span data-ttu-id="64a0b-117">C#</span><span class="sxs-lookup"><span data-stu-id="64a0b-117">C#</span></span>              | <span data-ttu-id="64a0b-118">239 kHz</span><span class="sxs-lookup"><span data-stu-id="64a0b-118">239 KHz</span></span>       |
> | <span data-ttu-id="64a0b-119">Windows 10 IoT Core 대 한 기본 스택</span><span class="sxs-lookup"><span data-stu-id="64a0b-119">Windows 10 IoT Core Native Stack</span></span>    | <span data-ttu-id="64a0b-120">C++/CX</span><span class="sxs-lookup"><span data-stu-id="64a0b-120">C++/CX</span></span>          | <span data-ttu-id="64a0b-121">278 kHz</span><span class="sxs-lookup"><span data-stu-id="64a0b-121">278 kHz</span></span>       |
> | <span data-ttu-id="64a0b-122">Windows 10 IoT Core 대 한 기본 스택</span><span class="sxs-lookup"><span data-stu-id="64a0b-122">Windows 10 IoT Core Native Stack</span></span>    | <span data-ttu-id="64a0b-123">WinJS</span><span class="sxs-lookup"><span data-stu-id="64a0b-123">WinJS</span></span>           | <span data-ttu-id="64a0b-124">34 kHz</span><span class="sxs-lookup"><span data-stu-id="64a0b-124">34 kHz</span></span>        |
> | <span data-ttu-id="64a0b-125">Windows 10 IoT Core Arduino 연결</span><span class="sxs-lookup"><span data-stu-id="64a0b-125">Windows 10 IoT Core Arduino Wiring</span></span>  | <span data-ttu-id="64a0b-126">Arduino 연결</span><span class="sxs-lookup"><span data-stu-id="64a0b-126">Arduino Wiring</span></span>  | <span data-ttu-id="64a0b-127">**7.36 MHz**</span><span class="sxs-lookup"><span data-stu-id="64a0b-127">**7.36 MHz**</span></span>  |
> | <span data-ttu-id="64a0b-128">Windows 10 IoT Core DMAP 스택</span><span class="sxs-lookup"><span data-stu-id="64a0b-128">Windows 10 IoT Core DMAP Stack</span></span>      | <span data-ttu-id="64a0b-129">C#</span><span class="sxs-lookup"><span data-stu-id="64a0b-129">C#</span></span>              | <span data-ttu-id="64a0b-130">**1.76 MHz**</span><span class="sxs-lookup"><span data-stu-id="64a0b-130">**1.76 MHz**</span></span>  |
> | <span data-ttu-id="64a0b-131">Windows 10 IoT Core DMAP 스택</span><span class="sxs-lookup"><span data-stu-id="64a0b-131">Windows 10 IoT Core DMAP Stack</span></span>      | <span data-ttu-id="64a0b-132">C++/CX</span><span class="sxs-lookup"><span data-stu-id="64a0b-132">C++/CX</span></span>          | <span data-ttu-id="64a0b-133">**3.78 MHz**</span><span class="sxs-lookup"><span data-stu-id="64a0b-133">**3.78 MHz**</span></span>  |
> | <span data-ttu-id="64a0b-134">Windows 10 IoT Core DMAP 스택</span><span class="sxs-lookup"><span data-stu-id="64a0b-134">Windows 10 IoT Core DMAP Stack</span></span>      | <span data-ttu-id="64a0b-135">WinJS</span><span class="sxs-lookup"><span data-stu-id="64a0b-135">WinJS</span></span>           | <span data-ttu-id="64a0b-136">42 kHz</span><span class="sxs-lookup"><span data-stu-id="64a0b-136">42 kHz</span></span>        |

<span data-ttu-id="64a0b-137">Windows 10 IoT Core Insider Preview 빌드 15026 (코드명 Redstone 2)를 사용 하 여 Raspberry Pi 3에서 실행 되었으며 Microsoft IoT 번개 SDK 1.1.0을 사용 하 여 작성 하는 Windows 10 IoT Core 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="64a0b-137">Windows 10 IoT Core tests were run on a Raspberry Pi 3 using Windows 10 IoT Core Insider Preview Build 15026 (codename Redstone 2) and built using Microsoft IoT Lightning SDK 1.1.0.</span></span>
