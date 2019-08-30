---
title: 라이트닝 성능 테스트
author: msalehmsft
ms.author: msaleh
ms.date: 08/28/2017
ms.topic: article
description: 다양 한 플랫폼 및 언어에 대 한 Windows IoT 라이트닝 기능 및 전환 빈도에 대해 알아봅니다.
keywords: windows iot, 라이트닝 성능, 라이트닝 기능, GPIO
ms.openlocfilehash: e7d57f72f6db85fbb8e453943c87e8ee31ef8a40
ms.sourcegitcommit: cbea9d713986fbe8b85e1bba1561a000188bd91c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64744785"
---
# <a name="windows-iot-lightning-performance-testing"></a><span data-ttu-id="55caf-104">Windows IoT 라이트닝 성능 테스트</span><span class="sxs-lookup"><span data-stu-id="55caf-104">Windows IoT Lightning Performance Testing</span></span>

> [!IMPORTANT]
> <span data-ttu-id="55caf-105">Windows 10 IoT 팀은 더 이상 Arduino을 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="55caf-105">The Windows 10 IoT team is no longer actively supporting Arduino.</span></span>

<span data-ttu-id="55caf-106">GPIO 성능은 [여기에서 사용할 수 있는](https://github.com/ms-iot/lightning/tree/develop/PerformanceTestSuite)간단한 GPIO 설정/해제 앱을 사용 하 여 Windows IoT 라이트닝 기능을 테스트 했습니다.</span><span class="sxs-lookup"><span data-stu-id="55caf-106">The GPIO performance was tested for Windows IoT Lightning functionality using a simple GPIO toggle app, [available here](https://github.com/ms-iot/lightning/tree/develop/PerformanceTestSuite).</span></span> <span data-ttu-id="55caf-107">테스트는 5 ~ 007e; 1 사이의 가장 빠른 속도로 GPIO 5를 전환 하 여 수행 했습니다.</span><span class="sxs-lookup"><span data-stu-id="55caf-107">The tests were performed by toggling GPIO 5 between 0 and 1 at the fastest possible speed.</span></span> <span data-ttu-id="55caf-108">각 사례에 대 한 토글 빈도는 Tektronix 2024 Oscilloscope를 사용 하 여 측정 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="55caf-108">The toggle frequency for each case was measured using a Tektronix TPS 2024 Oscilloscope.</span></span>

<span data-ttu-id="55caf-109">분석에서 얻은 결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="55caf-109">The following results were obtained from the analysis:</span></span>

> | <span data-ttu-id="55caf-110">테스트 된 플랫폼</span><span class="sxs-lookup"><span data-stu-id="55caf-110">Platform Tested</span></span>                     | <span data-ttu-id="55caf-111">언어</span><span class="sxs-lookup"><span data-stu-id="55caf-111">Language</span></span>        | <span data-ttu-id="55caf-112">빈도</span><span class="sxs-lookup"><span data-stu-id="55caf-112">Frequency</span></span>     |
> | ----------------------------------- | --------------- | ------------- |
> | <span data-ttu-id="55caf-113">Arduino Uno</span><span class="sxs-lookup"><span data-stu-id="55caf-113">Arduino Uno</span></span>                         | <span data-ttu-id="55caf-114">Arduino 스케치</span><span class="sxs-lookup"><span data-stu-id="55caf-114">Arduino Sketch</span></span>  | <span data-ttu-id="55caf-115">75.06 kHz</span><span class="sxs-lookup"><span data-stu-id="55caf-115">75.06 kHz</span></span>     |
> | <span data-ttu-id="55caf-116">Windows 10 IoT Core Native Stack</span><span class="sxs-lookup"><span data-stu-id="55caf-116">Windows 10 IoT Core Native Stack</span></span>    | <span data-ttu-id="55caf-117">C#</span><span class="sxs-lookup"><span data-stu-id="55caf-117">C#</span></span>              | <span data-ttu-id="55caf-118">239 KHz</span><span class="sxs-lookup"><span data-stu-id="55caf-118">239 KHz</span></span>       |
> | <span data-ttu-id="55caf-119">Windows 10 IoT Core Native Stack</span><span class="sxs-lookup"><span data-stu-id="55caf-119">Windows 10 IoT Core Native Stack</span></span>    | <span data-ttu-id="55caf-120">C++/CX</span><span class="sxs-lookup"><span data-stu-id="55caf-120">C++/CX</span></span>          | <span data-ttu-id="55caf-121">278 kHz</span><span class="sxs-lookup"><span data-stu-id="55caf-121">278 kHz</span></span>       |
> | <span data-ttu-id="55caf-122">Windows 10 IoT Core Native Stack</span><span class="sxs-lookup"><span data-stu-id="55caf-122">Windows 10 IoT Core Native Stack</span></span>    | <span data-ttu-id="55caf-123">WinJS</span><span class="sxs-lookup"><span data-stu-id="55caf-123">WinJS</span></span>           | <span data-ttu-id="55caf-124">34 kHz</span><span class="sxs-lookup"><span data-stu-id="55caf-124">34 kHz</span></span>        |
> | <span data-ttu-id="55caf-125">Windows 10 IoT Core Arduino 배선</span><span class="sxs-lookup"><span data-stu-id="55caf-125">Windows 10 IoT Core Arduino Wiring</span></span>  | <span data-ttu-id="55caf-126">Arduino 배선</span><span class="sxs-lookup"><span data-stu-id="55caf-126">Arduino Wiring</span></span>  | <span data-ttu-id="55caf-127">**7.36 MHz**</span><span class="sxs-lookup"><span data-stu-id="55caf-127">**7.36 MHz**</span></span>  |
> | <span data-ttu-id="55caf-128">Windows 10 IoT Core의 스택 스택</span><span class="sxs-lookup"><span data-stu-id="55caf-128">Windows 10 IoT Core DMAP Stack</span></span>      | <span data-ttu-id="55caf-129">C#</span><span class="sxs-lookup"><span data-stu-id="55caf-129">C#</span></span>              | <span data-ttu-id="55caf-130">**1.76 MHz**</span><span class="sxs-lookup"><span data-stu-id="55caf-130">**1.76 MHz**</span></span>  |
> | <span data-ttu-id="55caf-131">Windows 10 IoT Core의 스택 스택</span><span class="sxs-lookup"><span data-stu-id="55caf-131">Windows 10 IoT Core DMAP Stack</span></span>      | <span data-ttu-id="55caf-132">C++/CX</span><span class="sxs-lookup"><span data-stu-id="55caf-132">C++/CX</span></span>          | <span data-ttu-id="55caf-133">**3.78 MHz**</span><span class="sxs-lookup"><span data-stu-id="55caf-133">**3.78 MHz**</span></span>  |
> | <span data-ttu-id="55caf-134">Windows 10 IoT Core의 스택 스택</span><span class="sxs-lookup"><span data-stu-id="55caf-134">Windows 10 IoT Core DMAP Stack</span></span>      | <span data-ttu-id="55caf-135">WinJS</span><span class="sxs-lookup"><span data-stu-id="55caf-135">WinJS</span></span>           | <span data-ttu-id="55caf-136">42 kHz</span><span class="sxs-lookup"><span data-stu-id="55caf-136">42 kHz</span></span>        |

<span data-ttu-id="55caf-137">Windows 10 IoT Core 테스트는 Windows 10 IoT Core Insider Preview 빌드 15026 (코드명 Redstone 2)을 사용 하 여 Raspberry Pi 3에서 실행 되었으며 Microsoft IoT 라이트닝 SDK 1.1.0를 사용 하 여 빌드 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="55caf-137">Windows 10 IoT Core tests were run on a Raspberry Pi 3 using Windows 10 IoT Core Insider Preview Build 15026 (codename Redstone 2) and built using Microsoft IoT Lightning SDK 1.1.0.</span></span>
