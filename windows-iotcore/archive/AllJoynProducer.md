---
title: AllJoyn 생산자
author: saraclay
ms.author: saclayt
ms.date: 09/07/17
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: 검사 XML 및 다양 한 기능을 학습 하 고 작성 하 여 AllJoyn 생산자를 만드는 방법에 대해 알아봅니다.
keywords: windows iot, AllJoyn
ms.openlocfilehash: 014f6f4b4c33f4dbd85963bbddccb948322ccca9
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "60167407"
---
> [!NOTE]
> <span data-ttu-id="b1ce5-104">보관 된 설명서를 보고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-104">You are viewing archived documentation.</span></span> <span data-ttu-id="b1ce5-105">AllJoyn는 Windows 10 IoT에서 더 이상 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-105">AllJoyn is no longer supported by Windows 10 IoT.</span></span> <span data-ttu-id="b1ce5-106">질문이 있는 경우 GitHub에서 문제를 열거나 아래 설명에 의견을 남겨 주세요.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-106">For questions, please open an issue on GitHub or leave us feedback in the comments below.</span></span>

# <a name="alljoyn-producers"></a><span data-ttu-id="b1ce5-107">AllJoyn 생산자</span><span class="sxs-lookup"><span data-stu-id="b1ce5-107">AllJoyn Producers</span></span>

<span data-ttu-id="b1ce5-108">Proximal 네트워크에서 연결 된 장치 및 [앱을 만들기](https://allseenalliance.org/)위한 뛰어난 프레임 워크를 제공 하는 Alljoyn은 Visual Studio 용 [alljoyn Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286) 확장에서 alljoyn를 사용 하는 최상의 환경을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-108">AllJoyn, created by the [AllSeen Alliance](https://allseenalliance.org/), provides a great framework for making connected devices and apps on a proximal network, and Windows provides the best experience for using AllJoyn with the [AllJoyn Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286) extension for Visual Studio.</span></span>  <span data-ttu-id="b1ce5-109">Microsoft의 도구를 통해 생산자와 소비자를 위한 앱을 만들 때 새 AllJoyn 장치를 처음부터 시작 하는 것은 매우 복잡할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-109">While our tools excel at creating apps for producers and consumers, starting a new AllJoyn device from scratch can be quite confusing.</span></span>

<span data-ttu-id="b1ce5-110">Tinker 하 고 탐색 하는 데 사용할 수 있는 차세대 장난감 장치 또는 새 장난감에 대 한 아이디어가 있는 경우 AllSeen 동맹에서 제공 하는 표준 인터페이스 중 하나를 사용 하지 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-110">If you have an idea for the next great connected device or a new toy with which to tinker and explore, you may not be able to use one of the standard interfaces offered by the AllSeen Alliance.</span></span>  <span data-ttu-id="b1ce5-111">그렇다면 새 AllJoyn 생산자를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-111">If so, then you need to create a brand new AllJoyn producer.</span></span>

<span data-ttu-id="b1ce5-112">새 AllJoyn 생산자를 만들려는 개발자는 자신의 검사 XML을 작성 해야 하지만 검사 XML을 만들려면 중요 한 전문 지식이 필요 하며 새로운 개발자를 위한 상당한 학습 곡선이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-112">A developer wanting to make a new AllJoyn producer needs to author their own Introspection XML, but creating Introspection XML requires subject matter expertise and has a significant learning curve for new developers.</span></span>  <span data-ttu-id="b1ce5-113">이 블로그 게시물는 검사 XML의 다양 한 구성 요소를 분석 하 고, 각 구성 요소의 목적과 제한 사항을 설명 하 고, 하기 쉬우며 용어로 좋은 예제를 제공 하 여 학습 곡선을 낮춥니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-113">This blogpost will lower the learning curve by breaking down the various components of Introspection XML, describing the purpose and restrictions of each component, and providing good examples in approachable terms.</span></span>

## <a name="existing-documentation"></a><span data-ttu-id="b1ce5-114">기존 설명서</span><span class="sxs-lookup"><span data-stu-id="b1ce5-114">Existing documentation</span></span>

<span data-ttu-id="b1ce5-115">이 블로그 게시물와 결합 된 다음 리소스를 간단한 검사 하면 검사 XML의 개발자 이해를 가속화 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-115">A cursory examination of the following resources combined with this blogpost should accelerate developer understanding of Introspection XML:</span></span>

1. <span data-ttu-id="b1ce5-116">[Alljoyn 이벤트 및 작업 API 가이드](https://allseenalliance.org/developers/develop/api-guide/events-and-actions) – alljoyn 구현 세부 정보 및 개요.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-116">[AllJoyn Events and Actions API Guide](https://allseenalliance.org/developers/develop/api-guide/events-and-actions) – AllJoyn implementation details and overview.</span></span>
2. <span data-ttu-id="b1ce5-117">[Alljoyn 인터페이스 검토 보드 디자인 지침](https://wiki.allseenalliance.org/irb/interface_design_guidelines_1.0) -ALLJOYN 검사 XML에 대 한 엄격한 구조 및 사양입니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-117">[AllJoyn Interface Review Board Design Guidelines](https://wiki.allseenalliance.org/irb/interface_design_guidelines_1.0) - stringent structuring and specification for AllJoyn Introspection XML.</span></span>
3. <span data-ttu-id="b1ce5-118">[D-Bus 사양](http://dbus.freedesktop.org/doc/dbus-specification.html) –이 사양에서는 AllJoyn 기본 검사 XML입니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-118">[D-Bus Specification](http://dbus.freedesktop.org/doc/dbus-specification.html) – AllJoyn bases Introspection XML on this specification.</span></span>

<span data-ttu-id="b1ce5-119">__검사 XML의 세 가지 유형__</span><span class="sxs-lookup"><span data-stu-id="b1ce5-119">__The three types of Introspection XML__</span></span>

<span data-ttu-id="b1ce5-120">정독 AllJoyn 설명서는 세 가지 유형의 검사 XML을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-120">As you peruse AllJoyn documentation, you will find three types of Introspection XML:</span></span>

1. <span data-ttu-id="b1ce5-121">D-Bus 사양 XML: 데이터 표현에 대 한 형식 형식과 오버 헤드가 낮은 프로세스 간 통신입니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-121">D-Bus Specification XML: low-overhead, interprocess communication with a type format for data representation.</span></span>
2. <span data-ttu-id="b1ce5-122">AllJoyn 검사 XML: 사양에 AllJoyn 원칙을 적용 하는 동시에 텍스트 설명을 포함 하는 XML 태그를 사용 하 여 D-버스 사양 XML을 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-122">AllJoyn Introspection XML: extends D-Bus Specification XML with XML tags for holding textual descriptions while also applying AllJoyn principles to the specification.</span></span>
3. <span data-ttu-id="b1ce5-123">확장 된 AllJoyn 검사 XML: 기본 검사 XML의 진화 구조 및 사전에 대 한 명명 된 형식을 소개 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-123">Extended AllJoyn Introspection XML: evolution of classic Introspection XML introducing named types for structures and dictionaries.</span></span>

<span data-ttu-id="b1ce5-124">AllJoyn 스튜디오는 현재 D-Bus 사양 XML 및 AllJoyn 검사 XML을 지원 합니다. 이 블로그에서는 AllJoyn 검사 XML을 만들고 구성 하는 방법을 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-124">AllJoyn Studio currently supports D-Bus Specification XML and AllJoyn Introspection XML; this blog will dictate how to create and form AllJoyn Introspection XML.</span></span>  <span data-ttu-id="b1ce5-125">AllSeen 동맹의 IRB (Interface Review)는 새로운 확장 된 AllJoyn 검사를 표준화 검토에 대 한 정식 제출의 형식으로 사용 하지만, 가까운 미래를 위해 통합 검사 XML 형식으로 작업 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-125">The AllSeen Alliance's Interface Review Board (IRB) uses the new Extended AllJoyn Introspection as the format for formal submissions for standardization reviews but is working on a unified introspection XML format for the near future.</span></span>

## <a name="introspection-high-level-overview"></a><span data-ttu-id="b1ce5-126">검사 개략적인 개요</span><span class="sxs-lookup"><span data-stu-id="b1ce5-126">Introspection High Level Overview</span></span>

<span data-ttu-id="b1ce5-127">모든 AllJoyn 생산자는 신호, 속성 및 메서드를 통해 설명 된 대로 생산자의 지원 되는 기능 (인터페이스)을 표시 하는 검사 XML을 공개적으로 알립니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-127">Every AllJoyn producer publicly advertises an Introspection XML that surfaces the producer's supported functionality – interfaces as described via signals, properties and methods.</span></span>  <span data-ttu-id="b1ce5-128">검사 XML을 사용 하 여 코드를 생성 하는 것과 같은 코드 생성 솔루션은 개발을 가속화 하는 데 필요한 코드를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-128">Code Generation solutions, like the one in the AllJoyn Studio extension, rely on Introspection XML to create the necessary code to accelerate development.</span></span>  <span data-ttu-id="b1ce5-129">검사 XML은 두 명의 제조업체에서 XML을 사용 하 여 동일한 기능을 가진 생산자를 구현할 수 있도록 명확 하지 않은 사람이 인식할 수 있는 방식으로 생산자의 기능을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-129">Introspection XML describes the functionality of a producer in a non-ambiguous, human-readable way such that two different manufacturers can use the XML to implement a producer with the same functionality.</span></span>  <span data-ttu-id="b1ce5-130">동일한 토큰을 사용 하 여 AllJoyn 생산자에 대해 이전에 알지 못하는 개발자는 해당 XML을 기반으로 해당 생산자에 대해 개발할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-130">By the same token, developers with no previous knowledge of an AllJoyn producer should be able to develop against that producer based on its XML.</span></span>

<span data-ttu-id="b1ce5-131">__AllJoyn 인터페이스__</span><span class="sxs-lookup"><span data-stu-id="b1ce5-131">__AllJoyn Interfaces__</span></span>

<span data-ttu-id="b1ce5-132">AllJoyn에서는 검사 XML을 동작 및 기능의 서로 다른 논리적 그룹화를 나타내는 다양 한 "인터페이스"로 분리 하 여이를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-132">AllJoyn accomplishes this by breaking an Introspection XML into various "interfaces" that represent different logical groupings of behavior and capabilities.</span></span>  <span data-ttu-id="b1ce5-133">AllJoyn 인터페이스는 역방향 DNS 규칙을 사용 하 여 명명 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-133">AllJoyn interfaces are named using a reverse-DNS convention.</span></span> <span data-ttu-id="b1ce5-134">예를 들어 contoso.com 도메인을 소유 하는 Contoso l t d .에서 만든 "Foo" 인터페이스는 다음과 같이 작성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-134">For example, the interface "Foo" interface created by Contoso Ltd., which owns the contoso.com domain, would be written as:</span></span>

    <interface name="com.contoso.Foo">

<span data-ttu-id="b1ce5-135">생산자는 원하는 수의 인터페이스를 구현할 수 있지만 보급 하는 인터페이스의 모든 구성 요소를 구현 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-135">A producer may implement any number of interfaces, but must implement every component of an interface that they advertise.</span></span>  <span data-ttu-id="b1ce5-136">동작을 구분 하 고 확장 하기 위해 AllJoyn에서는 기존 인터페이스 계층 구조와 관련 하 여 새 인터페이스를 만들 수 있도록 지원 합니다. 즉,는 `Foo.Bar` 범주 아래에 있는 항목에 대 한 새로운 기능을 `com.contoso.Foo`정의하지만 인터페이스에 대 한 명시적 종속성은 없습니다. `com.contoso.Foo.Bar`</span><span class="sxs-lookup"><span data-stu-id="b1ce5-136">In order to differentiate and extend behaviors, AllJoyn supports creating new interfaces with respect to an existing interface hierarchy; i.e. `com.contoso.Foo.Bar` defines new capabilities for things under the `Foo.Bar` category but doesn't have any explicit dependencies on the `com.contoso.Foo` interface.</span></span> 

<span data-ttu-id="b1ce5-137">예를 들어 두 개의 인터페이스가 있습니다. `com.contoso.Sensor` 및 `com.contoso.Sensor.Humidity` – "습도"는 논리적으로 "센서" 범주 아래에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-137">For an example, we have two interfaces: `com.contoso.Sensor` and `com.contoso.Sensor.Humidity` – "Humidity" logically falls under the "Sensor" category.</span></span>  <span data-ttu-id="b1ce5-138">습도 생산자를 개발 하는 사람은 `com.contoso.Sensor.Humdity` 인터페이스를 지원 하도록 선택할 수 있지만 `com.contoso.Sensor` 인터페이스를 지원 하도록 선택할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-138">Someone developing a Humidity producer could choose to support just the `com.contoso.Sensor.Humdity` interface, but they could also choose to support the `com.contoso.Sensor` interface.</span></span>  <span data-ttu-id="b1ce5-139">인터페이스를 보급 하는 경우와 관계 없이 생산자는 모든 기능을 지원 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-139">Regardless, if they advertise an interface, then producers must support all of its functions.</span></span>

<span data-ttu-id="b1ce5-140">`<description>` 태그는 인터페이스, 기능 및 인수를 설명 하는 데 사용 되며 다양 한 언어에 대해 지역화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-140">The `<description>` tag is used to describe interfaces, capabilities and arguments, and can be localized for various languages.</span></span>  <span data-ttu-id="b1ce5-141">`<description>` 태그를 자유롭게 사용 하면 XML을 이해 하기 쉽고 모호성을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-141">Liberal use of the `<description>` tag makes the XML more understandable and removes ambiguity.</span></span>

<span data-ttu-id="b1ce5-142">표준 방법은 인터페이스에 `org.alljoyn.Bus.Secure` 주석을 사용 하 여 보안 및 인증을 사용 하도록 설정 하는 것을 말합니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-142">Standard practice dictates the use of the `org.alljoyn.Bus.Secure` annotation on an interface to enable security and authentication.</span></span>  <span data-ttu-id="b1ce5-143">강력한 인증의 경우 PSK (미리 공유한 키) 또는 ECDSA (certificate key exchange)를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-143">For strong authentication, use a pre-shared key (PSK) or a certificate key exchange (ECDSA).</span></span>  <span data-ttu-id="b1ce5-144">그렇지 않으면 "null" 인증이 기본 동작이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-144">Otherwise, a "null" authentication becomes the default behavior.</span></span>  <span data-ttu-id="b1ce5-145">**실제 인증 메커니즘은 선언이 아니라 구현에서 발생**합니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-145">**The actual authentication mechanism happens in implementation, not the declaration**.</span></span> <span data-ttu-id="b1ce5-146">이 주석은 보안을 사용 하지만 사용 되는 보안 형식 또는 구현 방법을 지정 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-146">This annotation enables security but does not specify the type of security used or how it will be implemented.</span></span>

<span data-ttu-id="b1ce5-147">___예제___</span><span class="sxs-lookup"><span data-stu-id="b1ce5-147">___Example___</span></span>

``` xml
<node>
 
  <interface name="com.example.Door.PrivateDoor">
 
    <annotation name="org.allJoyn.Bus.Secure" value="true" />
 
    <description language="en">
 
      Private interface for a Door the consumer owns. 
 
    </description>
 
  </interface>
 
</node>
```

<span data-ttu-id="b1ce5-148">이 예제에서는 장치 `com.example.Door.PrivateDoor`에서 노출 하는 인터페이스를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-148">This example shows an interface exposed by a device: `com.example.Door.PrivateDoor`.</span></span> <span data-ttu-id="b1ce5-149">인터페이스의 범위에서는 사용 되는 메커니즘 유형이 아닌 해당 인터페이스를 사용 하는 경우 통신을 보호 해야 하는지 여부를 고려해 야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-149">In the scope of the interface, the only thing we're concerned about is whether communication should be secured when using that interface, not what type of mechanism is being used.</span></span>

<span data-ttu-id="b1ce5-150">__인터페이스 기능__</span><span class="sxs-lookup"><span data-stu-id="b1ce5-150">__Interface Capabilities__</span></span>

<span data-ttu-id="b1ce5-151">인터페이스는 메서드, 속성 또는 신호의 세 가지 인터페이스 멤버를 사용 하 여 해당 기능을 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-151">Interfaces declare their capabilities with three interface members: methods, properties, or signals.</span></span> <span data-ttu-id="b1ce5-152">또한 검사 XML은 추가 기능 또는 제약 조건을 설명 하는 주석을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-152">Introspection XML also supports annotations that describe additional functionality or constraints.</span></span>  <span data-ttu-id="b1ce5-153">이러한 기능은 UpperCamelCase 표기법을 사용 하지만 인수는 lowerCamelCase 표기법을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-153">These capabilities use UpperCamelCase notation while arguments use lowerCamelCase notation.</span></span>

### <a name="argument-types"></a><span data-ttu-id="b1ce5-154">인수 형식</span><span class="sxs-lookup"><span data-stu-id="b1ce5-154">Argument Types</span></span>

<span data-ttu-id="b1ce5-155">인터페이스 멤버는 ASCII 형식 코드로 표시 되는 인수를 보내고 받습니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-155">Interface members send and receive arguments denoted by an ASCII type-code.</span></span>  <span data-ttu-id="b1ce5-156">인터페이스 멤버의 형식에 따라 인수는 소비자 (direction = "out") 또는 소비자 (direction = "in")에서 생산자로 전송 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-156">Depending on the type of interface member, arguments may have be sent to the producer from the consumer (direction="out") or from the consumer to the producer (direction="in").</span></span>  <span data-ttu-id="b1ce5-157">다음 표에서는 일반적으로 사용 되는 형식에 대 한 간략 한 개요를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-157">The following table provides a brief overview of commonly used types:</span></span>

> | <span data-ttu-id="b1ce5-158">*기본 이름*</span><span class="sxs-lookup"><span data-stu-id="b1ce5-158">*Conventional Name*</span></span> | <span data-ttu-id="b1ce5-159">*형식-코드*</span><span class="sxs-lookup"><span data-stu-id="b1ce5-159">*Type-Code*</span></span> | <span data-ttu-id="b1ce5-160">*사용*</span><span class="sxs-lookup"><span data-stu-id="b1ce5-160">*Use*</span></span> |
> |----------------- |---------| --- |
> |<span data-ttu-id="b1ce5-161">**부울**</span><span class="sxs-lookup"><span data-stu-id="b1ce5-161">**BOOLEAN**</span></span> | <span data-ttu-id="b1ce5-162">b</span><span class="sxs-lookup"><span data-stu-id="b1ce5-162">b</span></span> | <span data-ttu-id="b1ce5-163">TRUE (1) 또는 FALSE (0)를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-163">Represents TRUE (1) or FALSE (0).</span></span> <span data-ttu-id="b1ce5-164">간단한 이진 정보 또는 상태에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-164">Used for simple binary information or states.</span></span> |
> |<span data-ttu-id="b1ce5-165">**BYTE**</span><span class="sxs-lookup"><span data-stu-id="b1ce5-165">**BYTE**</span></span> | <span data-ttu-id="b1ce5-166">y</span><span class="sxs-lookup"><span data-stu-id="b1ce5-166">y</span></span> | <span data-ttu-id="b1ce5-167">0에서 255 사이의 정수 값입니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-167">Integer value from 0 to 255.</span></span> <span data-ttu-id="b1ce5-168">작은 양수를 처리할 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-168">Used when dealing with small positive numbers.</span></span> |
> |<span data-ttu-id="b1ce5-169">**UINT16**</span><span class="sxs-lookup"><span data-stu-id="b1ce5-169">**UINT16**</span></span> | <span data-ttu-id="b1ce5-170">q</span><span class="sxs-lookup"><span data-stu-id="b1ce5-170">q</span></span> | <span data-ttu-id="b1ce5-171">0에서 2 ^ 16-1 사이의 정수 값</span><span class="sxs-lookup"><span data-stu-id="b1ce5-171">Integer value from 0 to 2^16 - 1</span></span> |
> |<span data-ttu-id="b1ce5-172">**UINT32**</span><span class="sxs-lookup"><span data-stu-id="b1ce5-172">**UINT32**</span></span> | <span data-ttu-id="b1ce5-173">u</span><span class="sxs-lookup"><span data-stu-id="b1ce5-173">u</span></span> | <span data-ttu-id="b1ce5-174">0에서 2 ^ 32-1 사이의 정수 값</span><span class="sxs-lookup"><span data-stu-id="b1ce5-174">Integer value from 0 to 2^32 - 1</span></span> |
> |<span data-ttu-id="b1ce5-175">**UINT64**</span><span class="sxs-lookup"><span data-stu-id="b1ce5-175">**UINT64**</span></span> | <span data-ttu-id="b1ce5-176">t</span><span class="sxs-lookup"><span data-stu-id="b1ce5-176">t</span></span> | <span data-ttu-id="b1ce5-177">0에서 2 ^ 64-1 사이의 정수 값</span><span class="sxs-lookup"><span data-stu-id="b1ce5-177">Integer value from 0 to 2^64 - 1</span></span> |
> |<span data-ttu-id="b1ce5-178">**INT16**</span><span class="sxs-lookup"><span data-stu-id="b1ce5-178">**INT16**</span></span> | <span data-ttu-id="b1ce5-179">n</span><span class="sxs-lookup"><span data-stu-id="b1ce5-179">n</span></span> | <span data-ttu-id="b1ce5-180">– (2 ^ 15)부터 2 ^ 15-1 까지의 정수 값</span><span class="sxs-lookup"><span data-stu-id="b1ce5-180">Integer value from –(2^15) to 2^15 - 1</span></span> |
> |<span data-ttu-id="b1ce5-181">**INT32**</span><span class="sxs-lookup"><span data-stu-id="b1ce5-181">**INT32**</span></span> | <span data-ttu-id="b1ce5-182">i</span><span class="sxs-lookup"><span data-stu-id="b1ce5-182">i</span></span> | <span data-ttu-id="b1ce5-183">– (2 ^ 31)부터 2 ^ 31-1 까지의 정수 값</span><span class="sxs-lookup"><span data-stu-id="b1ce5-183">Integer value from –(2^31) to 2^31 - 1</span></span> |
> |<span data-ttu-id="b1ce5-184">**INT64**</span><span class="sxs-lookup"><span data-stu-id="b1ce5-184">**INT64**</span></span> | <span data-ttu-id="b1ce5-185">x</span><span class="sxs-lookup"><span data-stu-id="b1ce5-185">x</span></span> | <span data-ttu-id="b1ce5-186">– (2 ^ 63)부터 2 ^ 63-1 까지의 정수 값</span><span class="sxs-lookup"><span data-stu-id="b1ce5-186">Integer value from –(2^63) to 2^63 - 1</span></span> |
> |<span data-ttu-id="b1ce5-187">**차례로**</span><span class="sxs-lookup"><span data-stu-id="b1ce5-187">**DOUBLE**</span></span> | <span data-ttu-id="b1ce5-188">d</span><span class="sxs-lookup"><span data-stu-id="b1ce5-188">d</span></span> | <span data-ttu-id="b1ce5-189">– (2 ^ 127)에서 2 ^ 127-1 까지의 전체 자릿수 부동 소수점 숫자</span><span class="sxs-lookup"><span data-stu-id="b1ce5-189">Precision floating point numbers from –(2^127) to 2^127 - 1</span></span> |
> |<span data-ttu-id="b1ce5-190">**문자열**</span><span class="sxs-lookup"><span data-stu-id="b1ce5-190">**STRING**</span></span> | <span data-ttu-id="b1ce5-191">s</span><span class="sxs-lookup"><span data-stu-id="b1ce5-191">s</span></span> | <span data-ttu-id="b1ce5-192">UTF-8 문자열</span><span class="sxs-lookup"><span data-stu-id="b1ce5-192">UTF-8 string</span></span> |
 
<span data-ttu-id="b1ce5-193">지원 되는 모든 유형에 대 한 자세한 개요는 [여기](http://dbus.freedesktop.org/doc/dbus-specification.html#idp94392448)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-193">For a more exhaustive overview of all the supported types, see [here](http://dbus.freedesktop.org/doc/dbus-specification.html#idp94392448).</span></span>

<span data-ttu-id="b1ce5-194">이 문서를 작성할 때 가능 하면 SI 단위를 사용 하 고 원하는 단위를 명확 하 게 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-194">As of this writing, use SI units where possible and clearly denote intended units.</span></span> <span data-ttu-id="b1ce5-195">가능 하면 시나리오에 가장 제한적인 형식 코드를 선택 합니다. 예를 들어 사용자의 나이가 년 단위로 표시 되는 경우 음수가 아니거나 INT16이 아닌 BYTE를 사용 합니다. 즉, 음수가 아니거나 255 년 보다 많은 시간을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-195">When possible, choose the type-code most restrictive to your scenario; e.g., if you are representing a person's age in years, then use BYTE, not UINT16 or INT16, since no one will be a negative age or more than 255 years old.</span></span>  <span data-ttu-id="b1ce5-196">항상 최신 [IRB (AllJoyn 인터페이스 검토 보드)](https://wiki.allseenalliance.org/interfacereviewboard?s%5b%5d=interface&s%5b%5d=review&s%5b%5d=board) 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-196">Always follow the latest [AllJoyn Interface Review Board (IRB)](https://wiki.allseenalliance.org/interfacereviewboard?s%5b%5d=interface&s%5b%5d=review&s%5b%5d=board) guidelines.</span></span>

<span data-ttu-id="b1ce5-197">다음 표에서는 일반적인 단위를 요약 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-197">The following table summarizes common units:</span></span>


> |<span data-ttu-id="b1ce5-198">*수량*</span><span class="sxs-lookup"><span data-stu-id="b1ce5-198">*Quantity*</span></span> | <span data-ttu-id="b1ce5-199">*Unit*</span><span class="sxs-lookup"><span data-stu-id="b1ce5-199">*Unit*</span></span>|
> |-------- | ---- |
> |<span data-ttu-id="b1ce5-200">**절대 시간 (날짜 & 시간)**</span><span class="sxs-lookup"><span data-stu-id="b1ce5-200">**Absolute time (date & time)**</span></span> | <span data-ttu-id="b1ce5-201">UNIX Epoch 이후 시간 (초) (1970 1 월 1 일 00:00:00)</span><span class="sxs-lookup"><span data-stu-id="b1ce5-201">Seconds since UNIX Epoch (00:00:00 on January 1, 1970)</span></span> |
> |<span data-ttu-id="b1ce5-202">**하루 중 시간**</span><span class="sxs-lookup"><span data-stu-id="b1ce5-202">**Time of Day**</span></span> | <span data-ttu-id="b1ce5-203">자정 이후 시간 (초)</span><span class="sxs-lookup"><span data-stu-id="b1ce5-203">Seconds since midnight</span></span> |
> |<span data-ttu-id="b1ce5-204">**시간 간격**</span><span class="sxs-lookup"><span data-stu-id="b1ce5-204">**Time interval**</span></span> | <span data-ttu-id="b1ce5-205">초</span><span class="sxs-lookup"><span data-stu-id="b1ce5-205">Seconds</span></span> |
> |<span data-ttu-id="b1ce5-206">**대역**</span><span class="sxs-lookup"><span data-stu-id="b1ce5-206">**Bandwidth**</span></span> | <span data-ttu-id="b1ce5-207">비트/초</span><span class="sxs-lookup"><span data-stu-id="b1ce5-207">Bits per second</span></span> |
> |<span data-ttu-id="b1ce5-208">**데이터 크기**</span><span class="sxs-lookup"><span data-stu-id="b1ce5-208">**Data size**</span></span> | <span data-ttu-id="b1ce5-209">바이트</span><span class="sxs-lookup"><span data-stu-id="b1ce5-209">Bytes</span></span> |
 
### <a name="methods"></a><span data-ttu-id="b1ce5-210">메서드</span><span class="sxs-lookup"><span data-stu-id="b1ce5-210">Methods</span></span>

<span data-ttu-id="b1ce5-211">소비자는 메서드를 호출 하 여 생산자의 상태를 수정할 수 있으며 해당 이름은 생산자가 작업을 수행 하기 위한 요청을 나타내므로 동사로 시작 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-211">Consumers call methods to modify the state of a producer, and their names should start with a verb because they represent requests for the producer to perform an action.</span></span>  <span data-ttu-id="b1ce5-212">메서드에는 입력 및 출력 인수가 있을 수 있습니다. 반환 메시지를 보내야 하는 경우에는 "NoReply" 라는 주석을 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-212">Methods may have input and output arguments; in the case that no return message needs to be sent, apply the annotation "org.freedesktop.DBus.Method.NoReply".</span></span>  <span data-ttu-id="b1ce5-213">그러나 일반적으로는 일반적으로 SuccessResult 또는 FailureResult를 반환 하 여 메서드 호출에 대 한 소비자 의견을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-213">However, AllJoyn methods normally return a SuccessResult or a FailureResult, giving consumers feedback about the method call.</span></span>  <span data-ttu-id="b1ce5-214">인수의 형식은 [D-Bus 사양을](http://dbus.freedesktop.org/doc/dbus-specification.html)따라야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-214">The type of the arguments must comply with the [D-Bus Specification](http://dbus.freedesktop.org/doc/dbus-specification.html).</span></span> 

<span data-ttu-id="b1ce5-215">___예 (편의를 위해 인터페이스 정보 제외)___</span><span class="sxs-lookup"><span data-stu-id="b1ce5-215">___Example (excluding interface information for convenience)___</span></span>

``` xml
<node>
 
  <interface name="com.example.Door.PrivateDoor">
 
    <!-- Method showing arguments with only directions in -->
 
    <method name="SetPasscode">
 
      <description language="en">
 
        Allows owner of the door to change the code needed to unlock it.
 
      </description>
 
      <argument name="currentPasscode" type="u" direction="in">
 
        <description language="en">
 
          Current code (00000000 to 99999999) needed to unlock door
 
        </description>
 
      </argument>
 
      <argument name="newPasscode" type="u" direction="in">
 
        <description language="en">
 
          New code (00000000 to 99999999) needed to unlock door
 
        </description>
 
      </argument>
 
    </method>
 
  </interface>
 
  <interface name="com.example.Door.PublicDoor">
 
    <!-- Method showing both arguments in and out -->
 
    <method name="UnlockDoor">
 
      <description language="en">
 
        Allows guests with the code to unlock the door.
 
      </description>
 
      <argument name="passcode" type="u" direction="in">
 
        <description language="en">
 
          Current code (00000000 to 99999999) needed to unlock door
 
        </description>
 
      </argument>
 
      <argument name="welcomeMessage" type="s" direction="out">
 
        <description language="en">
 
          Message from the owner of the door.
 
        </description>
 
      </argument>
 
    </method>
 
  </interface>
 
</node>
```

<span data-ttu-id="b1ce5-216">*참고: 대부분의 경우 생산자의 상태에 액세스 하는 메서드 대신 속성을 사용 해야 합니다 (예: GetColor 메서드 대신 Color 속성 사용).*</span><span class="sxs-lookup"><span data-stu-id="b1ce5-216">*Note: In most cases, properties should be used instead of methods to access a producer's state (e.g., use a Color property instead of a GetColor method).*</span></span>

### <a name="properties"></a><span data-ttu-id="b1ce5-217">속성</span><span class="sxs-lookup"><span data-stu-id="b1ce5-217">Properties</span></span>

<span data-ttu-id="b1ce5-218">속성은 주로 생산자의 상태에 대 한 액세스를 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-218">Properties mainly allow access to a producer's state.</span></span>  <span data-ttu-id="b1ce5-219">속성이 기술적으로 "읽기", "readwrite" 또는 "write"의 액세스 값을 가지는 반면, 상태 수정 기능은 일반적으로 메서드에 속합니다. 따라서 개발자는 상태를 나타내는 경우에만 속성을 "읽기"로 유지 하 고 "readwrite"를 사용 해야 합니다. 해당 속성은 다른 모든 속성과는 독립적입니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-219">While properties technically have access values of "read", "readwrite", or "write", state-modifying functionality generally belongs to methods – as such, developers should strive to keep properties as "read" and use "readwrite" only when the state represented by that property is independent of all other properties.</span></span>  <span data-ttu-id="b1ce5-220">속성은 단순히 "write" 일 수 없습니다. 관찰 하지 않고 상태를 수정 하는 것은 메서드 역할입니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-220">Properties should never be just "write" – modifying the state without observation is the role of methods.</span></span>

<span data-ttu-id="b1ce5-221">값이 변경 될 때 경고 소비자에 대 한 속성을 주석으로 처리 해야 합니다. 선택적으로 속성은 부모 인터페이스에서이 주석을 상속할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-221">Properties must be annotated to alert consumers when their values change (optionally, properties can inherit this annotation from its parent interface).</span></span>  <span data-ttu-id="b1ce5-222">주석에 `org.freedesktop.DBus.Property.EmitsChangedSignal` 는 다음과 같은 4 개의 값이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-222">The annotation `org.freedesktop.DBus.Property.EmitsChangedSignal` can have four values:</span></span>

* <span data-ttu-id="b1ce5-223">"true"-속성이 변경 되 면 생산자는 변경 된 속성 및 새 값을 나타내는 신호를 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-223">"true" – when the property changes, the producer will emit a signal denoting the changed property and the new value.</span></span> <span data-ttu-id="b1ce5-224">자주 사용 되는 속성에 사용 되며, 문에 대 한 "LockState"와 같이 활성 감독을 요구 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-224">Used in properties that are frequently used and require active oversight, such as a "LockState" for a door.</span></span>
* <span data-ttu-id="b1ce5-225">"무효화" – 속성이 변경 되 면 생산자는 변경 된 속성을 나타내는 신호를 내보내고 새 값은 내보내지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-225">"invalidates" – when the property changes, the producer will emit a signal denoting the changed property but not the new value.</span></span> <span data-ttu-id="b1ce5-226">많은 감독 (예: 옷의 "WashMode")을 요구 하지 않거나 컨테이너와 같은 많은 데이터를 나타내는 속성에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-226">Used in properties that don't require heavy oversight (such as the "WashMode" of a clothes dryer) or represent a lot of data, such as a container.</span></span>
* <span data-ttu-id="b1ce5-227">"false"-속성이 변경 되 면 생산자는 신호를 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-227">"false" – when the property changes, the producer emits no signal.</span></span> <span data-ttu-id="b1ce5-228">지하철 회전식 추적 사용자 지하철를 탑재 하는 사람을 추적 하는 "TransitCounter" 속성과 같이 신속 하 게 업데이트 되는 속성에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-228">Used in properties that update rapidly, such as a "TransitCounter" property on a subway turnstile tracking people boarding the subway.</span></span> <span data-ttu-id="b1ce5-229">지정 하지 않으면 AllJoyn 속성은이를 기본값으로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-229">If unspecified, AllJoyn properties use this as default.</span></span>
* <span data-ttu-id="b1ce5-230">"const" – 속성은 값을 변경 하지 않으며 변경 된 신호를 내보내지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-230">"const" – the property will never change value and never emit a changed signal.</span></span> <span data-ttu-id="b1ce5-231">이는 AllJoyn 16.04 릴리스에서 도입 되었습니다. 그때까지 "true"를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-231">This will be introduced in the AllJoyn 16.04 release; until then, use "true".</span></span>

<span data-ttu-id="b1ce5-232">___예제___</span><span class="sxs-lookup"><span data-stu-id="b1ce5-232">___Example___</span></span>

<span data-ttu-id="b1ce5-233">이전 예제를 확장 하면 속성을 포함 하도록 XML을 수정 했습니다 (간단 하 게 하기 위한 메서드 제외).</span><span class="sxs-lookup"><span data-stu-id="b1ce5-233">Expanding upon the previous example, we have modified the XML to include properties (excluding the methods for brevity).</span></span>

``` xml
<node>
 
  <interface name="com.example.Door.PrivateDoor">
 
    <!—- Read property that sends a signal when the value changes -->
 
    <property name="IsLocked" type="b" access="read">
 
      <annotation name="org.freedesktop.DBus.Property.EmitsChangedSignal" value="true"/>
 
      <description language="en">
 
        Owner of the door may freely lock and unlock the door.
 
      </description>
 
    </property>  
 
  </interface>
 
  <interface name="com.example.Door.PublicDoor">
 
    <!—- Read-only property that never sends a signal and never changes -->
 
    <property name="Owner" type="s" access="read">
 
      <annotation name="org.freedesktop.DBus.Property.EmitsChangedSignal" value="true"/>
 
      <description language="en">
 
        Owner of the door is public knowledge.
 
      </description>
 
    </property>
 
  </interface>
 
</node>
```

### <a name="signals"></a><span data-ttu-id="b1ce5-234">연산</span><span class="sxs-lookup"><span data-stu-id="b1ce5-234">Signals</span></span>

<span data-ttu-id="b1ce5-235">신호를 사용 하 여 생산자를 쿼리하여 결정할 수 없는 이벤트를 소비자에 게 알립니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-235">Use signals to inform consumers of an event that they could not determine by querying the producer.</span></span>  <span data-ttu-id="b1ce5-236">문이 열리면 "true" EmitsChangedProperty 주석을 사용 하 여 생산자의 DoorOpen 속성을 통해 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-236">A door opening would be conveyed through a producer's DoorOpen property with a "true" EmitsChangedProperty annotation.</span></span>  <span data-ttu-id="b1ce5-237">그러나 도어를 전달 하는 다른 사용자는 속성 변경에서 파생 될 수 없으므로이로 인해 좋은 독립 실행형 신호가 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-237">Someone passing through the door, however, cannot be derived from any property changes, so this would make a good standalone signal.</span></span>  <span data-ttu-id="b1ce5-238">이러한 종류의 이벤트를 "상태 비저장"으로 지칭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-238">We refer to these kinds of events as "stateless".</span></span>  <span data-ttu-id="b1ce5-239">신호는 생산자에서 소비자로 단방향 이므로 "out" 인수만 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-239">Since signals are unidirectional from producer to consumer, they can only contain "out" arguments.</span></span>

<span data-ttu-id="b1ce5-240">___예___</span><span class="sxs-lookup"><span data-stu-id="b1ce5-240">___Examples___</span></span> 

<span data-ttu-id="b1ce5-241">(편의를 위해 메서드와 속성 제외):</span><span class="sxs-lookup"><span data-stu-id="b1ce5-241">(excluding methods and properties for convenience):</span></span>

``` xml
<node>
 
  <interface name="com.example.Door.PrivateDoor">
 
    <!—- Signals may contain arguments about non-state information -->
 
    <signal name="ThresholdCrossed" sessioncast="true">
 
      <description>
 
        Signal to notify owner whenever anyone passes through the door.
 
      </description>
 
      <argument name="crossedInward" type="b" direction="out">
 
        If true, someone entered; if false, someone left.
 
      </argument>
 
    </signal>
 
  </interface>
 
</node>
```

<span data-ttu-id="b1ce5-242">신호에는 좁은 범위가 있으므로 일반적으로 생산자의 XML에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-242">Since signals have such a narrow scope, typically few appear in a producer's XML.</span></span>

### <a name="containers"></a><span data-ttu-id="b1ce5-243">컨테이너</span><span class="sxs-lookup"><span data-stu-id="b1ce5-243">Containers</span></span>

<span data-ttu-id="b1ce5-244">여러 인수를 serialize 된 JSON 문자열과 같은 복합 컬렉션으로 결합 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-244">Do not combine multiple arguments into a complex collection like a serialized JSON string.</span></span> <span data-ttu-id="b1ce5-245">D-버스 사양은 데이터 컨테이너 (구조체, 배열, 변형 및 DICT_ENTRY)에 대해 affordances를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-245">The D-Bus specification makes affordances for containers of data – STRUCT, ARRAY, VARIANT, and DICT_ENTRY.</span></span>  <span data-ttu-id="b1ce5-246">이를 사용 하 여 기본 형식이 넘는 인수를 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-246">Use these to pass arguments that require more than basic types.</span></span>

<span data-ttu-id="b1ce5-247">___변형은___</span><span class="sxs-lookup"><span data-stu-id="b1ce5-247">___VARIANT___</span></span>

<span data-ttu-id="b1ce5-248">변형은 "v" 형식으로 표시 되며 임의의 [단일 전체 형식을](http://dbus.freedesktop.org/doc/dbus-specification.html#term-single-complete-type)포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-248">VARIANTs are denoted by the type "v" and can contain any [single complete type](http://dbus.freedesktop.org/doc/dbus-specification.html#term-single-complete-type).</span></span> <span data-ttu-id="b1ce5-249">그러나 XML 정의에 모호성을 추가 하므로 가능 하면 항상 변형을 피해 야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-249">However, VARIANTs should be avoided whenever possible because they add ambiguity to XML definitions.</span></span>

<span data-ttu-id="b1ce5-250">___STRUCT___</span><span class="sxs-lookup"><span data-stu-id="b1ce5-250">___STRUCT___</span></span>

<span data-ttu-id="b1ce5-251">구조체는 "(" 및 ")"를 사용 하 여 데이터 구조의 시작과 끝을 나타냅니다. 단일 전체 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-251">STRUCTs use "(" and ")" to denote the beginning and end of a data structure – a single complete type.</span></span>  <span data-ttu-id="b1ce5-252">이러한 데이터 구조는 중첩 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-252">These data structures may be nested.</span></span>

<span data-ttu-id="b1ce5-253">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-253">Examples:</span></span>

<span data-ttu-id="b1ce5-254">"(Iii)" 형식은 세 정수의 구조체를 나타냅니다. "(i (ii))"는 "((ii) i)" 형식과는 다른 정수의 구조체와 두 정수의 구조체를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-254">A type of "(iii)" denotes a structure of three integers; "(i(ii))" denotes a STRUCT of an integer and a STRUCT of two integers, which is distinct from the type "((ii)i)".</span></span>

<span data-ttu-id="b1ce5-255">___배열과___</span><span class="sxs-lookup"><span data-stu-id="b1ce5-255">___ARRAY___</span></span>

<span data-ttu-id="b1ce5-256">배열에는 "a" 형식 코드가 사용 되며 그 뒤에는 단일 전체 형식이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-256">ARRAYs use the type code "a" and must be followed by a single complete type.</span></span>  <span data-ttu-id="b1ce5-257">배열에는 설정 된 길이가 없으므로 목록 데이터 구조와 유사 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-257">ARRAYs do not have set lengths, so they are similar to a list data structure.</span></span> <span data-ttu-id="b1ce5-258">배열은 단일 전체 형식을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-258">ARRAYs represent a single complete type.</span></span>

<span data-ttu-id="b1ce5-259">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-259">Examples:</span></span>

<span data-ttu-id="b1ce5-260">"Ai"의 형식은 정수 배열을 나타내며 "aai"는 정수 배열의 배열을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-260">A type of "ai" represents an ARRAY of integers, while "aai" represents an ARRAY of an ARRAY of integers.</span></span>  <span data-ttu-id="b1ce5-261">배열은 "a (ii)"와 함께 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-261">An ARRAY may be used with STRUCTs as well: "a(ii)".</span></span>

<span data-ttu-id="b1ce5-262">___DICT_ENTRY___</span><span class="sxs-lookup"><span data-stu-id="b1ce5-262">___DICT_ENTRY___</span></span>

<span data-ttu-id="b1ce5-263">DICT_ENTRYs 함수는 "{" 및 "}"를 사용 하 고, 배열 요소 형식 으로만 발생 하 고, 중괄호 안에 정확히 두 개의 완전 한 형식을 포함 해야 하는 더 큰 제한이 있는 구조체와 유사 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-263">DICT_ENTRYs function similar to a STRUCT with greater restrictions: they use "{" and "}", may only occur as an array element type, and must have exactly two complete types inside the curly braces.</span></span>  <span data-ttu-id="b1ce5-264">첫 번째 형식은 사전 데이터 구조체의 "키"를 나타내고, 두 번째 형식은 사전 키-값 쌍의 "값"을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-264">The first type represents a "Key" in a dictionary data structure, and the second represents the "Value" in the dictionary's Key-Value pair.</span></span>  <span data-ttu-id="b1ce5-265">키는 사전에서 고유 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-265">A Key should be unique in a dictionary.</span></span>

<span data-ttu-id="b1ce5-266">예:</span><span class="sxs-lookup"><span data-stu-id="b1ce5-266">Example:</span></span>

<span data-ttu-id="b1ce5-267">{Sy}의 형식은 문자열 키와 바이트 값의 사전을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-267">A type of a{sy} denotes a dictionary of string KEYs and byte VALUEs.</span></span>  <span data-ttu-id="b1ce5-268">이후</span><span class="sxs-lookup"><span data-stu-id="b1ce5-268">Use</span></span> <description> <span data-ttu-id="b1ce5-269">올바른 키 및 값을 설명 하는 태그입니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-269">tags to describe valid keys and values.</span></span> 

<span data-ttu-id="b1ce5-270">__최종 예제 및 ajxmlcop__</span><span class="sxs-lookup"><span data-stu-id="b1ce5-270">__Final Example and ajxmlcop__</span></span>

<span data-ttu-id="b1ce5-271">컨테이너 개념은 기존 XML의 기능을 개선 하 고 새로운 유용한 인터페이스 멤버에 대 한 통로을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-271">The concept of containers improves the capabilities of the existing XML as well as providing an avenue for new useful interface members.</span></span>

<span data-ttu-id="b1ce5-272">XML 작성을 완료 한 후에는 ajxmlcop 명령줄 도구 (AllJoyn [git 원본](https://git.allseenalliance.org/cgit/core/alljoyn.git/) 또는 [여기](https://github.com/MS-brock/AllJoynToasterDemo)에서 사용 가능)를 사용 하 여 xml의 유효성을 검사 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-272">Once you have finished writing your XML, use the ajxmlcop.exe command line tool (available at the AllJoyn [git source](https://git.allseenalliance.org/cgit/core/alljoyn.git/) or [here](https://github.com/MS-brock/AllJoynToasterDemo)) to validate the XML.</span></span>  <span data-ttu-id="b1ce5-273">XML 파일을 입력 인수 (예: `C:\>ajxmlcop.exe doorExample.xml`)로 사용 하 여 오류, 경고 및 정보 메시지를 수신 하려면 ajxmlcop을 입력 인수 (예:)로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-273">Use ajxmlcop.exe with your XML file as the input argument (e.g., `C:\>ajxmlcop.exe doorExample.xml`) to receive error, warning, and informational messages.</span></span>  <span data-ttu-id="b1ce5-274">이 도구는 XML의 구조와 형식 및 신호, 속성 및 메서드의 사용에 대 한 유용한 피드백을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1ce5-274">This tool provides valuable feedback as to the structure and format of your XML and use of signals, properties, and methods.</span></span>

``` xml
<node>
  <interface name="com.example.Door.PrivateDoor">
    <annotation name="org.alljoyn.Bus.Secure" value="true" />
    <description language="en">
      Examples for an AllJoyn-enabled door.  Private interface that can only be used by the producer’s owner.
    </description>
    <method name="SetPasscode">
      <description language="en">
        Change the code needed to unlock the door.
      </description>
      <argument name="currentPasscode" type="u" direction="in">
        <description language="en">
          Current code needed to unlock door
        </description>
      </argument>
      <argument name="newPasscode" type="u" direction="in">
        <description language="en">
          New code needed to unlock door
        </description>
      </argument>
    </method>
    <method name="UpdateGuestRatings">
      <description language="en">
        Update the list of guests and their personality scores.
      </description>
      <annotation name="org.freedesktop.DBus.Method.NoReply" value="true" />
      <argument name="guestName" type="s">
        <description language="en">
          The name of the guest being entered.
        </description>
      </argument>
      <argument name="qualityScores" type="a{sy}">
        <description language="en">
          DICTIONARY[Key:(string)guestQuality, Value:(byte)score]
          KEYs: "Friendly", "Social", "Punctual" 
          VALUEs: [0-10]
          The qualities of the guest, scored appropriately. If the guestName matches an existing entry, this updates that entry.
        </description>
      </argument>
    </method>
    <method name="SetDoorSecurity">
      <description language="en">
        Close and lock the door or unlock the door.
      </description>
      <argument name="secured" type="b" direction="in">
        <description language="en">
          If TRUE, shut and lock the door.
          If FALSE, unlock the door.
        </description>
      </argument>
    </method>
    <property name="MessageBook" type="a(ss)" access="read">
      <annotation name="org.freedesktop.DBus.Property.EmitsChangedSignal" value="invalidates"/>
      <description language="en">
        (struct)[(string)guestName, (string)message]
        A list of names of people and the messages they have left.
      </description>
    </property>
    <property name="GuestRatings" type="a(sa{sy})" access="read">
      <annotation name="org.freedesktop.DBus.Property.EmitsChangedSignal" value="false"/>
      <description language="en">
        ARRAY[(string)guestName, DICTIONARY(Key:(string)guestQuality, Value:(byte)score)]
        KEYs: "Friendly", "Social", "Punctual"
        VALUEs: [0-10]
        A collection of the previous guests and their scored qualities.
      </description>
    </property>
    <property name="IsLocked" type="b" access="read">
      <annotation name="org.freedesktop.DBus.Property.EmitsChangedSignal" value="true"/>
      <description language="en">
        Owner of the door may freely lock and unlock the door.
      </description>
    </property>
    <property name="Version" type="q" access="read">
      <annotation name="org.freedesktop.DBus.Property.EmitsChangedSignal" value="false"/>
      <description language="en">
        Version of the implementation being used.
      </description>
    </property>
    <signal name="ThresholdCrossed" sessioncast="true">
      <description>
        Signal to notify owner whenever anyone passes through the door.
      </description>
      <argument name="crossedInwards" type="b" direction="out">
        If true, someone entered; if false, someone left.
      </argument>    
    </signal>
  </interface>
  <interface name="com.example.Door.PublicDoor">
    <annotation name="org.alljoyn.Bus.Secure" value="true" />
    <description language="en">
      Examples for an AllJoyn-enabled door. Public interface that can be used by any consumer.
    </description>
    <method name="UnlockDoor">
      <description language="en">
        Allows guests with the code to unlock the door.
      </description>
      <argument name="passcode" type="u" direction="in">
        <description language="en">
          Current code (00000000 to 99999999) needed to unlock door
        </description>
      </argument>
      <argument name="welcomeMessage" type="s" direction="out">
        <description language="en">
          Message from the owner of the door.
        </description>
      </argument>
    </method>
    <method name="LeaveMessage">
      <description language="en">
        Leave a message for the owner of the door.
      </description>
      <argument name="guestName" type="s" direction="in">
        <description language="en">
          Name of guest leaving a message
        </description>
      </argument>
      <argument name="message" type="s" direction="in">
        <description language="en">
          Message left for owner of the door
        </description>
      </argument>
    </method>
    <method name="AnnouncePresence">
      <description language="en">
        Send a message to the owner of the door.
      </description>
      <argument name="announcingGuest" type="s" direction="in">
        <description language="en">
          Name of the guest announcing their presence.
        </description>
      </argument>
      <argument name="forcefulnessOfAnnouncment" type="y" direction="in">
        <description language="en">
          Degree to which the guest attempts to make their presence known, on bounds [1:10], where 1 is softly and 10 is aggressively.
        </description>
      </argument>
    </method>
    <property name="Version" type="q" access="read">
      <annotation name="org.freedesktop.DBus.Property.EmitsChangedSignal" value="false"/>
      <description language="en">
        Version of the implementation being used.
      </description>
    </property>
    <property name="Owner" type="s" access="read">
      <annotation name="org.freedesktop.DBus.Property.EmitsChangedSignal" value="false"/>
      <description language="en">
        Owner of the door is public knowledge.
      </description>
    </property>
  </interface>
</node>
```

