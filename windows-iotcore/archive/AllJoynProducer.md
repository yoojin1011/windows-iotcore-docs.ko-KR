---
title: AllJoyn 생산자
author: saraclay
ms.author: saclayt
ms.date: 09/07/17
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: 에 대 한 학습 검사 XML 및 다른 기능을 작성 하는 AllJoyn 생산자를 거는 방법에 알아봅니다.
keywords: windows iot, AllJoyn
ms.openlocfilehash: 014f6f4b4c33f4dbd85963bbddccb948322ccca9
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512822"
---
> [!NOTE]
> <span data-ttu-id="22de2-104">보관 된 설명서가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-104">You are viewing archived documentation.</span></span> <span data-ttu-id="22de2-105">Windows 10 IoT에서 더 이상 AllJoyn 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-105">AllJoyn is no longer supported by Windows 10 IoT.</span></span> <span data-ttu-id="22de2-106">질문에 대 한 GitHub에서 문제를 제기 하거나 아래 설명에 의견을 남길 하세요.</span><span class="sxs-lookup"><span data-stu-id="22de2-106">For questions, please open an issue on GitHub or leave us feedback in the comments below.</span></span>

# <a name="alljoyn-producers"></a><span data-ttu-id="22de2-107">AllJoyn 생산자</span><span class="sxs-lookup"><span data-stu-id="22de2-107">AllJoyn Producers</span></span>

<span data-ttu-id="22de2-108">AllJoyn, 만든 합니다 [AllSeen Alliance](https://allseenalliance.org/)를 함께 AllJoyn 사용에 대 한 최상의 환경을 제공 proximal 네트워크 및 Windows에서 앱 및 연결 된 장치에 대 한 유용한 프레임 워크를 제공 합니다 [AllJoyn Studio ](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286) Visual Studio 용 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-108">AllJoyn, created by the [AllSeen Alliance](https://allseenalliance.org/), provides a great framework for making connected devices and apps on a proximal network, and Windows provides the best experience for using AllJoyn with the [AllJoyn Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286) extension for Visual Studio.</span></span>  <span data-ttu-id="22de2-109">도구는 생산자와 소비자에 대 한 앱 만들기에 excel을 처음부터 새 AllJoyn 장치 시작 매우 혼란 스 러 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-109">While our tools excel at creating apps for producers and consumers, starting a new AllJoyn device from scratch can be quite confusing.</span></span>

<span data-ttu-id="22de2-110">주목할 만한 연결 된 장치 또는 창고나 탐색 하는 새 장난감에 대 한 아이디어가 있습니다 AllSeen Alliance에서 제공 하는 표준 인터페이스 중 하나를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-110">If you have an idea for the next great connected device or a new toy with which to tinker and explore, you may not be able to use one of the standard interfaces offered by the AllSeen Alliance.</span></span>  <span data-ttu-id="22de2-111">그렇다면 해야 새로운 AllJoyn 생산자를 만들려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-111">If so, then you need to create a brand new AllJoyn producer.</span></span>

<span data-ttu-id="22de2-112">새 AllJoyn 생산자를 확인 하려는 개발자가 자신의 검사 XML을 작성 해야 하지만 실무 지식이 필요 하 고 새 개발자를 위한 중요 한 학습 곡선에 검사 XML 만들기.</span><span class="sxs-lookup"><span data-stu-id="22de2-112">A developer wanting to make a new AllJoyn producer needs to author their own Introspection XML, but creating Introspection XML requires subject matter expertise and has a significant learning curve for new developers.</span></span>  <span data-ttu-id="22de2-113">이 블로그 게시물은 검사 XML의 다양 한 구성 요소를 세분화 하 고 용도 각 구성 요소의 제한 사항을 설명 하는 하며 사용 하기 쉬운 용어로 좋은 예를 제공 하 여 학습 곡선을 낮춥니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-113">This blogpost will lower the learning curve by breaking down the various components of Introspection XML, describing the purpose and restrictions of each component, and providing good examples in approachable terms.</span></span>

## <a name="existing-documentation"></a><span data-ttu-id="22de2-114">기존 설명서</span><span class="sxs-lookup"><span data-stu-id="22de2-114">Existing documentation</span></span>

<span data-ttu-id="22de2-115">이 블로그 게시물을 사용 하 여 결합 된 다음 리소스의 대략적인 심사가 개발자를 가속화 해야 검사 xml 이해:</span><span class="sxs-lookup"><span data-stu-id="22de2-115">A cursory examination of the following resources combined with this blogpost should accelerate developer understanding of Introspection XML:</span></span>

1. <span data-ttu-id="22de2-116">[AllJoyn 이벤트 및 작업 API 가이드](https://allseenalliance.org/developers/develop/api-guide/events-and-actions) – AllJoyn 구현 세부 정보 및 개요.</span><span class="sxs-lookup"><span data-stu-id="22de2-116">[AllJoyn Events and Actions API Guide](https://allseenalliance.org/developers/develop/api-guide/events-and-actions) – AllJoyn implementation details and overview.</span></span>
2. <span data-ttu-id="22de2-117">[AllJoyn 인터페이스 검토 보드 디자인 지침](https://wiki.allseenalliance.org/irb/interface_design_guidelines_1.0) -엄격한 구조화 및 AllJoyn 검사 XML에 대 한 사양입니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-117">[AllJoyn Interface Review Board Design Guidelines](https://wiki.allseenalliance.org/irb/interface_design_guidelines_1.0) - stringent structuring and specification for AllJoyn Introspection XML.</span></span>
3. <span data-ttu-id="22de2-118">[D-Bus 사양](http://dbus.freedesktop.org/doc/dbus-specification.html) – AllJoyn 검사 XML이이 사양은 기반 합니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-118">[D-Bus Specification](http://dbus.freedesktop.org/doc/dbus-specification.html) – AllJoyn bases Introspection XML on this specification.</span></span>

__<span data-ttu-id="22de2-119">세 가지 유형의 검사 XML</span><span class="sxs-lookup"><span data-stu-id="22de2-119">The three types of Introspection XML</span></span>__

<span data-ttu-id="22de2-120">AllJoyn 설명서를 살펴보면 대로 세 가지 유형의 검사 XML을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-120">As you peruse AllJoyn documentation, you will find three types of Introspection XML:</span></span>

1. <span data-ttu-id="22de2-121">데이터 표현에 대 한 형식 형식으로 D Bus 사양 XML: 오버 헤드가 낮은, 프로세스 간 통신.</span><span class="sxs-lookup"><span data-stu-id="22de2-121">D-Bus Specification XML: low-overhead, interprocess communication with a type format for data representation.</span></span>
2. <span data-ttu-id="22de2-122">AllJoyn 검사 XML: 또한 사양을 AllJoyn 원칙을 적용 하는 동안 텍스트 설명을 포함 하는 것에 대 한 XML 태그를 사용 하 여 D Bus 사양 XML을 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-122">AllJoyn Introspection XML: extends D-Bus Specification XML with XML tags for holding textual descriptions while also applying AllJoyn principles to the specification.</span></span>
3. <span data-ttu-id="22de2-123">AllJoyn 검사 XML 확장: 클래식 검사 XML 소개의 명명 된 형식 구조 및 사전에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-123">Extended AllJoyn Introspection XML: evolution of classic Introspection XML introducing named types for structures and dictionaries.</span></span>

<span data-ttu-id="22de2-124">AllJoyn Studio는 현재 D-Bus 사양 XML 및 AllJoyn 검사 XML 지원 이 블로그 만들고 AllJoyn 검사 XML을 형성 하는 방법에 따라 결정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-124">AllJoyn Studio currently supports D-Bus Specification XML and AllJoyn Introspection XML; this blog will dictate how to create and form AllJoyn Introspection XML.</span></span>  <span data-ttu-id="22de2-125">AllSeen Alliance의 인터페이스 검토 보드 (IRB) 형식으로 표준화 검토에 대 한 공식적인 제출에 대 한 새 확장 AllJoyn 검사를 사용 하지만 가까운 미래에 대 한 통합된 검사 XML 형식에 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-125">The AllSeen Alliance's Interface Review Board (IRB) uses the new Extended AllJoyn Introspection as the format for formal submissions for standardization reviews but is working on a unified introspection XML format for the near future.</span></span>

## <a name="introspection-high-level-overview"></a><span data-ttu-id="22de2-126">검사는 개략적인 단계</span><span class="sxs-lookup"><span data-stu-id="22de2-126">Introspection High Level Overview</span></span>

<span data-ttu-id="22de2-127">모든 AllJoyn 생산자는 공개적으로 검사 XML 신호, 속성 및 메서드를 통해 설명 하는 생산자의 지원 되는 기능 – 인터페이스를 보여주는 알립니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-127">Every AllJoyn producer publicly advertises an Introspection XML that surfaces the producer's supported functionality – interfaces as described via signals, properties and methods.</span></span>  <span data-ttu-id="22de2-128">AllJoyn Studio 확장을 같은 코드 생성 솔루션 개발을 가속화 하는 데 필요한 코드를 만들려면 검사 XML에 의존 합니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-128">Code Generation solutions, like the one in the AllJoyn Studio extension, rely on Introspection XML to create the necessary code to accelerate development.</span></span>  <span data-ttu-id="22de2-129">검사 XML 두 제조업체 동일한 기능을 사용 하 여 생산자를 구현 하는 XML을 사용할 수 있도록 모호한, 사람이 읽을 수 있는 방식으로 생산자의 기능을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-129">Introspection XML describes the functionality of a producer in a non-ambiguous, human-readable way such that two different manufacturers can use the XML to implement a producer with the same functionality.</span></span>  <span data-ttu-id="22de2-130">마찬가지로, 개발자는 AllJoyn 생산자 지식이 없는 이전에 해당 XML에 기반한 해당 공급자에 대해 개발 하기 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-130">By the same token, developers with no previous knowledge of an AllJoyn producer should be able to develop against that producer based on its XML.</span></span>

__<span data-ttu-id="22de2-131">AllJoyn 인터페이스</span><span class="sxs-lookup"><span data-stu-id="22de2-131">AllJoyn Interfaces</span></span>__

<span data-ttu-id="22de2-132">AllJoyn 검사 XML 다양 한 ""을 나타내는 인터페이스 기능과 동작의 다른 논리 그룹으로 분할 하 여이 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-132">AllJoyn accomplishes this by breaking an Introspection XML into various "interfaces" that represent different logical groupings of behavior and capabilities.</span></span>  <span data-ttu-id="22de2-133">AllJoyn 인터페이스는 역방향 DNS 규칙을 사용 하는 이름이 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-133">AllJoyn interfaces are named using a reverse-DNS convention.</span></span> <span data-ttu-id="22de2-134">예를 들어 contoso.com 도메인을 소유 하는 Contoso Ltd. 만든 인터페이스 "Foo" 인터페이스는 다음과 같이 작성</span><span class="sxs-lookup"><span data-stu-id="22de2-134">For example, the interface "Foo" interface created by Contoso Ltd., which owns the contoso.com domain, would be written as:</span></span>

    <interface name="com.contoso.Foo">

<span data-ttu-id="22de2-135">생산자 임의 개수의 인터페이스를 구현할 수 있지만 보급 하는 인터페이스의 모든 구성 요소를 구현 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-135">A producer may implement any number of interfaces, but must implement every component of an interface that they advertise.</span></span>  <span data-ttu-id="22de2-136">AllJoyn 구분 하 고 동작을 확장 하기 위해 기존 인터페이스 계층;와 관련 하 여 새 인터페이스를 만들기를 지원합니다 즉, `com.contoso.Foo.Bar` 아래에 있는 항목에 대 한 새 기능을 정의 합니다 `Foo.Bar` 범주 하지만 명시적 종속성이 없는 `com.contoso.Foo` 인터페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-136">In order to differentiate and extend behaviors, AllJoyn supports creating new interfaces with respect to an existing interface hierarchy; i.e. `com.contoso.Foo.Bar` defines new capabilities for things under the `Foo.Bar` category but doesn't have any explicit dependencies on the `com.contoso.Foo` interface.</span></span> 

<span data-ttu-id="22de2-137">예를 들어 두 개의 인터페이스가 있다고: `com.contoso.Sensor` 및 `com.contoso.Sensor.Humidity` – "습도" "센서" 범주 아래에 있는 논리적으로 대체 됩니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-137">For an example, we have two interfaces: `com.contoso.Sensor` and `com.contoso.Sensor.Humidity` – "Humidity" logically falls under the "Sensor" category.</span></span>  <span data-ttu-id="22de2-138">습도 생산자 개발 누군가가 지원 하도록 선택할 수만 `com.contoso.Sensor.Humdity` 있지만 인터페이스를 지원 하도록 선택할 수도 있습니다는 `com.contoso.Sensor` 인터페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-138">Someone developing a Humidity producer could choose to support just the `com.contoso.Sensor.Humdity` interface, but they could also choose to support the `com.contoso.Sensor` interface.</span></span>  <span data-ttu-id="22de2-139">그럼에도 불구 하 고 인터페이스를 보급 하는 경우 다음 생산자 지원 해야 모든 기능 합니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-139">Regardless, if they advertise an interface, then producers must support all of its functions.</span></span>

<span data-ttu-id="22de2-140">`<description>` 태그 인터페이스, 기능 및 인수에 설명 하는 데 사용 되 고 다양 한 언어에 대 한 지역화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-140">The `<description>` tag is used to describe interfaces, capabilities and arguments, and can be localized for various languages.</span></span>  <span data-ttu-id="22de2-141">자유롭게 사용 하 여는 `<description>` 태그 XML을 더 이해할 수 있게 및 모호성을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-141">Liberal use of the `<description>` tag makes the XML more understandable and removes ambiguity.</span></span>

<span data-ttu-id="22de2-142">표준 사례 사용 하도록 규정 합니다 `org.alljoyn.Bus.Secure` 보안 및 인증을 사용 하도록 설정 하려면 인터페이스에서 주석입니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-142">Standard practice dictates the use of the `org.alljoyn.Bus.Secure` annotation on an interface to enable security and authentication.</span></span>  <span data-ttu-id="22de2-143">강력한 인증을 위한 사전 공유 키 (PSK) 또는 인증서 키 교환 (ECDSA)를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-143">For strong authentication, use a pre-shared key (PSK) or a certificate key exchange (ECDSA).</span></span>  <span data-ttu-id="22de2-144">이 고, 그렇지 "null" 인증을 기본 동작이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-144">Otherwise, a "null" authentication becomes the default behavior.</span></span>  <span data-ttu-id="22de2-145">**실제 인증 메커니즘을 구현 하지 않습니다 진행**합니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-145">**The actual authentication mechanism happens in implementation, not the declaration**.</span></span> <span data-ttu-id="22de2-146">이 주석은 보안을 사용 하도록 설정 하지만 사용 되는 보안 형식 또는 구현 하는 방법을 지정 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-146">This annotation enables security but does not specify the type of security used or how it will be implemented.</span></span>

___<span data-ttu-id="22de2-147">예제</span><span class="sxs-lookup"><span data-stu-id="22de2-147">Example</span></span>___

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

<span data-ttu-id="22de2-148">이 예제에서는 장치에서 노출 된 인터페이스를 보여 줍니다. `com.example.Door.PrivateDoor`합니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-148">This example shows an interface exposed by a device: `com.example.Door.PrivateDoor`.</span></span> <span data-ttu-id="22de2-149">인터페이스의 범위에서 염려 되는 것은 어떤 유형의 메커니즘은 사용 되지 인터페이스를 사용 하는 경우 통신을 보호 해야 하는지 여부를 합니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-149">In the scope of the interface, the only thing we're concerned about is whether communication should be secured when using that interface, not what type of mechanism is being used.</span></span>

__<span data-ttu-id="22de2-150">기능 인터페이스</span><span class="sxs-lookup"><span data-stu-id="22de2-150">Interface Capabilities</span></span>__

<span data-ttu-id="22de2-151">세 가지 인터페이스 멤버를 사용 하 여 해당 기능을 선언 하는 인터페이스: 메서드, 속성 또는 신호입니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-151">Interfaces declare their capabilities with three interface members: methods, properties, or signals.</span></span> <span data-ttu-id="22de2-152">검사 XML에는 또한 추가 기능 또는 제약 조건을 설명 하는 주석을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-152">Introspection XML also supports annotations that describe additional functionality or constraints.</span></span>  <span data-ttu-id="22de2-153">이러한 기능은 인수 lowerCamelCase 표기법을 사용 하는 동안 UpperCamelCase 표기법을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-153">These capabilities use UpperCamelCase notation while arguments use lowerCamelCase notation.</span></span>

### <a name="argument-types"></a><span data-ttu-id="22de2-154">인수 형식</span><span class="sxs-lookup"><span data-stu-id="22de2-154">Argument Types</span></span>

<span data-ttu-id="22de2-155">인터페이스 멤버 보내고 ASCII 형식 코드를 가리키는 인수를 수신 합니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-155">Interface members send and receive arguments denoted by an ASCII type-code.</span></span>  <span data-ttu-id="22de2-156">인터페이스 멤버의 형식에 따라 인수가 전송할 수 있습니다 생산자는 소비자의 (방향 = "축소") 또는 소비자는 생산자 (방향 = "").</span><span class="sxs-lookup"><span data-stu-id="22de2-156">Depending on the type of interface member, arguments may have be sent to the producer from the consumer (direction="out") or from the consumer to the producer (direction="in").</span></span>  <span data-ttu-id="22de2-157">다음 표에서 일반적으로 사용 되는 형식에 간략하게 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-157">The following table provides a brief overview of commonly used types:</span></span>

> | *<span data-ttu-id="22de2-158">기본 이름</span><span class="sxs-lookup"><span data-stu-id="22de2-158">Conventional Name</span></span>* | *<span data-ttu-id="22de2-159">Type-Code</span><span class="sxs-lookup"><span data-stu-id="22de2-159">Type-Code</span></span>* | *<span data-ttu-id="22de2-160">이후</span><span class="sxs-lookup"><span data-stu-id="22de2-160">Use</span></span>* |
> |----------------- |---------| --- |
> |**<span data-ttu-id="22de2-161">부울</span><span class="sxs-lookup"><span data-stu-id="22de2-161">BOOLEAN</span></span>** | <span data-ttu-id="22de2-162">b</span><span class="sxs-lookup"><span data-stu-id="22de2-162">b</span></span> | <span data-ttu-id="22de2-163">(1) TRUE 또는 FALSE (0)를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-163">Represents TRUE (1) or FALSE (0).</span></span> <span data-ttu-id="22de2-164">간단한 이진 정보 또는 상태에 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-164">Used for simple binary information or states.</span></span> |
> |**<span data-ttu-id="22de2-165">바이트</span><span class="sxs-lookup"><span data-stu-id="22de2-165">BYTE</span></span>** | <span data-ttu-id="22de2-166">y</span><span class="sxs-lookup"><span data-stu-id="22de2-166">y</span></span> | <span data-ttu-id="22de2-167">정수 0에서 255 사이의 값입니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-167">Integer value from 0 to 255.</span></span> <span data-ttu-id="22de2-168">작은 양수를 처리할 때 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-168">Used when dealing with small positive numbers.</span></span> |
> |**<span data-ttu-id="22de2-169">UINT16</span><span class="sxs-lookup"><span data-stu-id="22de2-169">UINT16</span></span>** | <span data-ttu-id="22de2-170">q</span><span class="sxs-lookup"><span data-stu-id="22de2-170">q</span></span> | <span data-ttu-id="22de2-171">정수 값 0에서 2 ^16-1</span><span class="sxs-lookup"><span data-stu-id="22de2-171">Integer value from 0 to 2^16 - 1</span></span> |
> |**<span data-ttu-id="22de2-172">UINT32</span><span class="sxs-lookup"><span data-stu-id="22de2-172">UINT32</span></span>** | <span data-ttu-id="22de2-173">u</span><span class="sxs-lookup"><span data-stu-id="22de2-173">u</span></span> | <span data-ttu-id="22de2-174">정수 값 0에서 2 ^32-1</span><span class="sxs-lookup"><span data-stu-id="22de2-174">Integer value from 0 to 2^32 - 1</span></span> |
> |**<span data-ttu-id="22de2-175">UINT64</span><span class="sxs-lookup"><span data-stu-id="22de2-175">UINT64</span></span>** | <span data-ttu-id="22de2-176">t</span><span class="sxs-lookup"><span data-stu-id="22de2-176">t</span></span> | <span data-ttu-id="22de2-177">정수 값 0에서 2 ^64-1</span><span class="sxs-lookup"><span data-stu-id="22de2-177">Integer value from 0 to 2^64 - 1</span></span> |
> |**<span data-ttu-id="22de2-178">INT16</span><span class="sxs-lookup"><span data-stu-id="22de2-178">INT16</span></span>** | <span data-ttu-id="22de2-179">n</span><span class="sxs-lookup"><span data-stu-id="22de2-179">n</span></span> | <span data-ttu-id="22de2-180">정수 값 –(2^15)에서 2 ^15-1</span><span class="sxs-lookup"><span data-stu-id="22de2-180">Integer value from –(2^15) to 2^15 - 1</span></span> |
> |**<span data-ttu-id="22de2-181">INT32</span><span class="sxs-lookup"><span data-stu-id="22de2-181">INT32</span></span>** | <span data-ttu-id="22de2-182">i</span><span class="sxs-lookup"><span data-stu-id="22de2-182">i</span></span> | <span data-ttu-id="22de2-183">정수 값 –(2^31)에서 2 ^31-1</span><span class="sxs-lookup"><span data-stu-id="22de2-183">Integer value from –(2^31) to 2^31 - 1</span></span> |
> |**<span data-ttu-id="22de2-184">INT64</span><span class="sxs-lookup"><span data-stu-id="22de2-184">INT64</span></span>** | <span data-ttu-id="22de2-185">x</span><span class="sxs-lookup"><span data-stu-id="22de2-185">x</span></span> | <span data-ttu-id="22de2-186">정수 값 –(2^63)에서 2 ^63-1</span><span class="sxs-lookup"><span data-stu-id="22de2-186">Integer value from –(2^63) to 2^63 - 1</span></span> |
> |**<span data-ttu-id="22de2-187">DOUBLE</span><span class="sxs-lookup"><span data-stu-id="22de2-187">DOUBLE</span></span>** | <span data-ttu-id="22de2-188">d</span><span class="sxs-lookup"><span data-stu-id="22de2-188">d</span></span> | <span data-ttu-id="22de2-189">정밀도 실수 –(2^127)에서 2 ^127-1</span><span class="sxs-lookup"><span data-stu-id="22de2-189">Precision floating point numbers from –(2^127) to 2^127 - 1</span></span> |
> |**<span data-ttu-id="22de2-190">문자열</span><span class="sxs-lookup"><span data-stu-id="22de2-190">STRING</span></span>** | <span data-ttu-id="22de2-191">s</span><span class="sxs-lookup"><span data-stu-id="22de2-191">s</span></span> | <span data-ttu-id="22de2-192">Utf-8 문자열</span><span class="sxs-lookup"><span data-stu-id="22de2-192">UTF-8 string</span></span> |
 
<span data-ttu-id="22de2-193">지원 되는 모든 유형의 더 철저 한 개요를 참조 하세요 [여기](http://dbus.freedesktop.org/doc/dbus-specification.html#idp94392448)합니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-193">For a more exhaustive overview of all the supported types, see [here](http://dbus.freedesktop.org/doc/dbus-specification.html#idp94392448).</span></span>

<span data-ttu-id="22de2-194">이 문서의 작성 시점 현재 가능한 경우 SI 단위를 사용 하 고 명확 하 게 원하는 단위를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-194">As of this writing, use SI units where possible and clearly denote intended units.</span></span> <span data-ttu-id="22de2-195">가능 하면 형식-코드 시나리오;에 가장 제한적인 선택 예를 들어 년에 사람의 나이 나타내는 이며, 사용 하 여 바이트, UINT16 않거나 INT16 되므로 아무도 음수 연령 또는 이전 255 년 이상.</span><span class="sxs-lookup"><span data-stu-id="22de2-195">When possible, choose the type-code most restrictive to your scenario; e.g., if you are representing a person's age in years, then use BYTE, not UINT16 or INT16, since no one will be a negative age or more than 255 years old.</span></span>  <span data-ttu-id="22de2-196">항상 최신 따를 [AllJoyn 인터페이스 검토 보드 (IRB)](https://wiki.allseenalliance.org/interfacereviewboard?s%5b%5d=interface&s%5b%5d=review&s%5b%5d=board) 지침입니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-196">Always follow the latest [AllJoyn Interface Review Board (IRB)](https://wiki.allseenalliance.org/interfacereviewboard?s%5b%5d=interface&s%5b%5d=review&s%5b%5d=board) guidelines.</span></span>

<span data-ttu-id="22de2-197">다음 표에서 일반적인 단위를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-197">The following table summarizes common units:</span></span>


> |*<span data-ttu-id="22de2-198">수량</span><span class="sxs-lookup"><span data-stu-id="22de2-198">Quantity</span></span>* | *<span data-ttu-id="22de2-199">단위</span><span class="sxs-lookup"><span data-stu-id="22de2-199">Unit</span></span>*|
> |-------- | ---- |
> |**<span data-ttu-id="22de2-200">절대 시간 (날짜 및 시간)</span><span class="sxs-lookup"><span data-stu-id="22de2-200">Absolute time (date & time)</span></span>** | <span data-ttu-id="22de2-201">UNIX Epoch 이후의 초 (00: 00:00 1970 년 1 월 1 일에서)</span><span class="sxs-lookup"><span data-stu-id="22de2-201">Seconds since UNIX Epoch (00:00:00 on January 1, 1970)</span></span> |
> |**<span data-ttu-id="22de2-202">하루 중 시간</span><span class="sxs-lookup"><span data-stu-id="22de2-202">Time of Day</span></span>** | <span data-ttu-id="22de2-203">자정 이후의 시간 (초)</span><span class="sxs-lookup"><span data-stu-id="22de2-203">Seconds since midnight</span></span> |
> |**<span data-ttu-id="22de2-204">시간 간격</span><span class="sxs-lookup"><span data-stu-id="22de2-204">Time interval</span></span>** | <span data-ttu-id="22de2-205">초</span><span class="sxs-lookup"><span data-stu-id="22de2-205">Seconds</span></span> |
> |**<span data-ttu-id="22de2-206">대역폭</span><span class="sxs-lookup"><span data-stu-id="22de2-206">Bandwidth</span></span>** | <span data-ttu-id="22de2-207">비트/초</span><span class="sxs-lookup"><span data-stu-id="22de2-207">Bits per second</span></span> |
> |**<span data-ttu-id="22de2-208">데이터 크기</span><span class="sxs-lookup"><span data-stu-id="22de2-208">Data size</span></span>** | <span data-ttu-id="22de2-209">바이트</span><span class="sxs-lookup"><span data-stu-id="22de2-209">Bytes</span></span> |
 
### <a name="methods"></a><span data-ttu-id="22de2-210">메서드</span><span class="sxs-lookup"><span data-stu-id="22de2-210">Methods</span></span>

<span data-ttu-id="22de2-211">소비자는 생산자의 상태를 수정 하는 메서드를 호출 하 고 작업을 수행 하려면 생산자에 대 한 요청을 나타내므로 이름이 동사를 시작 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-211">Consumers call methods to modify the state of a producer, and their names should start with a verb because they represent requests for the producer to perform an action.</span></span>  <span data-ttu-id="22de2-212">메서드 입력 및 출력 인수입니다. 반환 메시지가 없다는 전송 해야 하는 경우 "org.freedesktop.DBus.Method.NoReply" 주석이 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-212">Methods may have input and output arguments; in the case that no return message needs to be sent, apply the annotation "org.freedesktop.DBus.Method.NoReply".</span></span>  <span data-ttu-id="22de2-213">그러나 AllJoyn 메서드는 SuccessResult 또는 FailureResult, 메서드 호출에 대 한 소비자에 게 피드백을 제공에 일반적으로 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-213">However, AllJoyn methods normally return a SuccessResult or a FailureResult, giving consumers feedback about the method call.</span></span>  <span data-ttu-id="22de2-214">인수의 형식을 따라야 합니다 [D 버스 사양](http://dbus.freedesktop.org/doc/dbus-specification.html)합니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-214">The type of the arguments must comply with the [D-Bus Specification](http://dbus.freedesktop.org/doc/dbus-specification.html).</span></span> 

___<span data-ttu-id="22de2-215">예 (편의상 인터페이스 정보 제외)</span><span class="sxs-lookup"><span data-stu-id="22de2-215">Example (excluding interface information for convenience)</span></span>___

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

*<span data-ttu-id="22de2-216">참고: 대부분의 경우에서 속성 메서드 대신에 사용할 공급자의 상태에 액세스 (예: GetColor 메서드 대신 색 속성을 사용).</span><span class="sxs-lookup"><span data-stu-id="22de2-216">Note: In most cases, properties should be used instead of methods to access a producer's state (e.g., use a Color property instead of a GetColor method).</span></span>*

### <a name="properties"></a><span data-ttu-id="22de2-217">속성</span><span class="sxs-lookup"><span data-stu-id="22de2-217">Properties</span></span>

<span data-ttu-id="22de2-218">주로 속성 공급자의 상태에 대 한 액세스를 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-218">Properties mainly allow access to a producer's state.</span></span>  <span data-ttu-id="22de2-219">속성 액세스 값이 있는 기술적으로 하는 동안 "읽기", "readwrite" 또는 "쓰기" 상태 수정 기능 방법 – 같이 일반적으로 속한, 개발자는 "읽음"으로 속성을 유지 하 고 상태를 표시 하는 경우에 "readwrite"를 사용 하기 위해 노력 해야 이 속성은 다른 모든 속성 무관 합니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-219">While properties technically have access values of "read", "readwrite", or "write", state-modifying functionality generally belongs to methods – as such, developers should strive to keep properties as "read" and use "readwrite" only when the state represented by that property is independent of all other properties.</span></span>  <span data-ttu-id="22de2-220">속성 되어서는 안 방금 "쓰기"-메서드의 역할은 관찰 하지 않고 상태를 수정 합니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-220">Properties should never be just "write" – modifying the state without observation is the role of methods.</span></span>

<span data-ttu-id="22de2-221">속성 값이 변경 하는 경우 경고 소비자에 게 지정 해야 합니다 (필요에 따라 속성에서에서 상속할 수 있습니다이 주석은 해당 부모 인터페이스인).</span><span class="sxs-lookup"><span data-stu-id="22de2-221">Properties must be annotated to alert consumers when their values change (optionally, properties can inherit this annotation from its parent interface).</span></span>  <span data-ttu-id="22de2-222">주석 `org.freedesktop.DBus.Property.EmitsChangedSignal` 4 개의 값을 가질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-222">The annotation `org.freedesktop.DBus.Property.EmitsChangedSignal` can have four values:</span></span>

* <span data-ttu-id="22de2-223">"true" – 속성이 변경 되 면 생산자는 변경된 된 속성 및 새 값을 나타내는 신호를 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-223">"true" – when the property changes, the producer will emit a signal denoting the changed property and the new value.</span></span> <span data-ttu-id="22de2-224">자주 사용 되 고 문이 대 한 "LockState"와 같은 활성 감독을 요구 하는 속성에 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-224">Used in properties that are frequently used and require active oversight, such as a "LockState" for a door.</span></span>
* <span data-ttu-id="22de2-225">""-때 무효화 속성 변경 내용을 생산자를 새 값을 제외한 변경된 된 속성을 나타내는 신호를 내보냅니다 됩니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-225">"invalidates" – when the property changes, the producer will emit a signal denoting the changed property but not the new value.</span></span> <span data-ttu-id="22de2-226">(예:는 "WashMode" 건조 기는 옷의) 과도 한 감독 필요 하거나 많은 양의 컨테이너와 같은 데이터를 나타내는 속성에 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-226">Used in properties that don't require heavy oversight (such as the "WashMode" of a clothes dryer) or represent a lot of data, such as a container.</span></span>
* <span data-ttu-id="22de2-227">"false" – 속성이 변경 되 면 생산자 없습니다 신호를 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-227">"false" – when the property changes, the producer emits no signal.</span></span> <span data-ttu-id="22de2-228">추적 탑승객을 지하철 운행 지하철 운행 턴 스타일의 속성을 "TransitCounter" 등을 신속 하 게 업데이트 되는 속성에 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-228">Used in properties that update rapidly, such as a "TransitCounter" property on a subway turnstile tracking people boarding the subway.</span></span> <span data-ttu-id="22de2-229">지정 하지 않으면 AllJoyn 속성 기본적으로이 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-229">If unspecified, AllJoyn properties use this as default.</span></span>
* <span data-ttu-id="22de2-230">"const" – 속성 값을 변경 되지 않습니다 되며 변경 된 신호를 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-230">"const" – the property will never change value and never emit a changed signal.</span></span> <span data-ttu-id="22de2-231">이 AllJoyn 16.04 릴리스에서 새로 도입 된 그때 까지는 "true"를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-231">This will be introduced in the AllJoyn 16.04 release; until then, use "true".</span></span>

___<span data-ttu-id="22de2-232">예제</span><span class="sxs-lookup"><span data-stu-id="22de2-232">Example</span></span>___

<span data-ttu-id="22de2-233">앞의 예제를 확장 했습니다 (간단히 하기 위해 메서드를 제외) 속성을 포함 하도록 XML을 수정 했습니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-233">Expanding upon the previous example, we have modified the XML to include properties (excluding the methods for brevity).</span></span>

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

### <a name="signals"></a><span data-ttu-id="22de2-234">신호</span><span class="sxs-lookup"><span data-stu-id="22de2-234">Signals</span></span>

<span data-ttu-id="22de2-235">생산자를 쿼리하여 확인할 수 없습니다는 이벤트의 소비자에 게 알리는 데 사용 하 여 알립니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-235">Use signals to inform consumers of an event that they could not determine by querying the producer.</span></span>  <span data-ttu-id="22de2-236">문 열기를 "true" EmitsChangedProperty 주석 사용 하 여 생산자의 DoorOpen 속성을 통해 전달 될 것입니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-236">A door opening would be conveyed through a producer's DoorOpen property with a "true" EmitsChangedProperty annotation.</span></span>  <span data-ttu-id="22de2-237">그러나 도어 통과 누군가가 파생 될 수 없습니다 속성 변경 내용을에서 적절 한 독립 실행형 신호를 이렇게 하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-237">Someone passing through the door, however, cannot be derived from any property changes, so this would make a good standalone signal.</span></span>  <span data-ttu-id="22de2-238">이러한 종류의 "상태 비저장"으로 이벤트를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-238">We refer to these kinds of events as "stateless".</span></span>  <span data-ttu-id="22de2-239">신호를 소비자 생산자에서 단방향 되므로 "out" 인수만 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-239">Since signals are unidirectional from producer to consumer, they can only contain "out" arguments.</span></span>

___<span data-ttu-id="22de2-240">예</span><span class="sxs-lookup"><span data-stu-id="22de2-240">Examples</span></span>___ 

<span data-ttu-id="22de2-241">(메서드 및 속성의 편의 위해 제외):</span><span class="sxs-lookup"><span data-stu-id="22de2-241">(excluding methods and properties for convenience):</span></span>

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

<span data-ttu-id="22de2-242">신호 좁은 범위에 없으므로 일반적으로 거의 나타나지 생산자의 XML.</span><span class="sxs-lookup"><span data-stu-id="22de2-242">Since signals have such a narrow scope, typically few appear in a producer's XML.</span></span>

### <a name="containers"></a><span data-ttu-id="22de2-243">컨테이너</span><span class="sxs-lookup"><span data-stu-id="22de2-243">Containers</span></span>

<span data-ttu-id="22de2-244">Serialize 된 JSON 문자열 처럼 복잡 한 컬렉션에 여러 개의 인수를 결합 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="22de2-244">Do not combine multiple arguments into a complex collection like a serialized JSON string.</span></span> <span data-ttu-id="22de2-245">D-Bus 사양 데이터 구조체, 배열, 변형 및 DICT_ENTRY 컨테이너용 affordances 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-245">The D-Bus specification makes affordances for containers of data – STRUCT, ARRAY, VARIANT, and DICT_ENTRY.</span></span>  <span data-ttu-id="22de2-246">이 사용 하 여 기본 형식 보다 더 많은 작업이 필요 하는 인수를 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-246">Use these to pass arguments that require more than basic types.</span></span>

___<span data-ttu-id="22de2-247">VARIANT</span><span class="sxs-lookup"><span data-stu-id="22de2-247">VARIANT</span></span>___

<span data-ttu-id="22de2-248">변형 "v" 형식으로 표시 됩니다 및 포함할 수 있습니다 [완전 한 형식 single](http://dbus.freedesktop.org/doc/dbus-specification.html#term-single-complete-type)합니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-248">VARIANTs are denoted by the type "v" and can contain any [single complete type](http://dbus.freedesktop.org/doc/dbus-specification.html#term-single-complete-type).</span></span> <span data-ttu-id="22de2-249">그러나 모호성 XML 정의에 추가 하기 때문에 변형은 가능 하면 피해 합니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-249">However, VARIANTs should be avoided whenever possible because they add ambiguity to XML definitions.</span></span>

___<span data-ttu-id="22de2-250">구조체</span><span class="sxs-lookup"><span data-stu-id="22de2-250">STRUCT</span></span>___

<span data-ttu-id="22de2-251">구조체 사용 "(" 및 ")"를 단일 전체 형식 – 데이터 구조의 시작과 끝을 나타내는입니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-251">STRUCTs use "(" and ")" to denote the beginning and end of a data structure – a single complete type.</span></span>  <span data-ttu-id="22de2-252">이러한 데이터 구조를 중첩할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-252">These data structures may be nested.</span></span>

<span data-ttu-id="22de2-253">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-253">Examples:</span></span>

<span data-ttu-id="22de2-254">"(Iii)" 형식의 3 개 정수의; 구조를 나타냅니다. "(i(ii))" 정수 구조체 및 유형을 구별 되는 두 정수의 구조체를 나타내는 "((ii) 있나요)".</span><span class="sxs-lookup"><span data-stu-id="22de2-254">A type of "(iii)" denotes a structure of three integers; "(i(ii))" denotes a STRUCT of an integer and a STRUCT of two integers, which is distinct from the type "((ii)i)".</span></span>

___<span data-ttu-id="22de2-255">배열</span><span class="sxs-lookup"><span data-stu-id="22de2-255">ARRAY</span></span>___

<span data-ttu-id="22de2-256">배열 형식 코드를 사용 하 여 "a" 및 단일 전체 형식으로와 야 합니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-256">ARRAYs use the type code "a" and must be followed by a single complete type.</span></span>  <span data-ttu-id="22de2-257">목록 데이터 구조와 유사 하므로 배열 집합 길이 갖지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-257">ARRAYs do not have set lengths, so they are similar to a list data structure.</span></span> <span data-ttu-id="22de2-258">배열은 하나의 완전 한 형식을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-258">ARRAYs represent a single complete type.</span></span>

<span data-ttu-id="22de2-259">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-259">Examples:</span></span>

<span data-ttu-id="22de2-260">"Ai" 유형의 정수의 배열을 나타내고 "aai" 정수 배열의 배열을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-260">A type of "ai" represents an ARRAY of integers, while "aai" represents an ARRAY of an ARRAY of integers.</span></span>  <span data-ttu-id="22de2-261">배열 구조체와도 사용할 수 있습니다. "a(ii)"입니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-261">An ARRAY may be used with STRUCTs as well: "a(ii)".</span></span>

___<span data-ttu-id="22de2-262">DICT_ENTRY</span><span class="sxs-lookup"><span data-stu-id="22de2-262">DICT_ENTRY</span></span>___

<span data-ttu-id="22de2-263">더 많은 제한이 포함 된 구조체와 같은 DICT_ENTRYs 함수: 사용 하 여 "{0}" 및 "}", 배열 요소 형식으로 발생할 수 있습니다 및 완전 한 중괄호 안의 형식 두 개 정확 하 게 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-263">DICT_ENTRYs function similar to a STRUCT with greater restrictions: they use "{" and "}", may only occur as an array element type, and must have exactly two complete types inside the curly braces.</span></span>  <span data-ttu-id="22de2-264">첫 번째 형식은 사전 데이터 구조에서 "키"를 나타내고 두 번째 사전의 키-값 쌍 "값"을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-264">The first type represents a "Key" in a dictionary data structure, and the second represents the "Value" in the dictionary's Key-Value pair.</span></span>  <span data-ttu-id="22de2-265">키를 사전에 고유 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-265">A Key should be unique in a dictionary.</span></span>

<span data-ttu-id="22de2-266">예:</span><span class="sxs-lookup"><span data-stu-id="22de2-266">Example:</span></span>

<span data-ttu-id="22de2-267">{Sy} 형식의 문자열 키 및 바이트 값의 사전을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-267">A type of a{sy} denotes a dictionary of string KEYs and byte VALUEs.</span></span>  <span data-ttu-id="22de2-268">이후</span><span class="sxs-lookup"><span data-stu-id="22de2-268">Use</span></span> <description> <span data-ttu-id="22de2-269">유효한 키 및 값을 설명 하는 태그입니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-269">tags to describe valid keys and values.</span></span> 

__<span data-ttu-id="22de2-270">마지막 예제 및 ajxmlcop</span><span class="sxs-lookup"><span data-stu-id="22de2-270">Final Example and ajxmlcop</span></span>__

<span data-ttu-id="22de2-271">컨테이너 개념이 유용한 인터페이스 멤버의 새 기회를 제공을 제공할 뿐만 아니라 기존 XML의 기능을 향상 시킵니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-271">The concept of containers improves the capabilities of the existing XML as well as providing an avenue for new useful interface members.</span></span>

<span data-ttu-id="22de2-272">Ajxmlcop.exe 명령줄 도구를 사용 하 여 XML 작성을 마쳤으면 (AllJoyn는에서 사용할 수 있습니다 [git 소스](https://git.allseenalliance.org/cgit/core/alljoyn.git/) 또는 [여기](https://github.com/MS-brock/AllJoynToasterDemo)) 유효성을 검사할 XML.</span><span class="sxs-lookup"><span data-stu-id="22de2-272">Once you have finished writing your XML, use the ajxmlcop.exe command line tool (available at the AllJoyn [git source](https://git.allseenalliance.org/cgit/core/alljoyn.git/) or [here](https://github.com/MS-brock/AllJoynToasterDemo)) to validate the XML.</span></span>  <span data-ttu-id="22de2-273">XML 파일을 사용 하 여 ajxmlcop.exe를 사용 하 여 입력 인수 (예를 들어 `C:\>ajxmlcop.exe doorExample.xml`) 오류, 경고 및 정보 메시지를 수신 하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-273">Use ajxmlcop.exe with your XML file as the input argument (e.g., `C:\>ajxmlcop.exe doorExample.xml`) to receive error, warning, and informational messages.</span></span>  <span data-ttu-id="22de2-274">이 도구는 구조 및 XML 형식 및 신호, 속성 및 메서드 사용에 대 한 소중한 피드백을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="22de2-274">This tool provides valuable feedback as to the structure and format of your XML and use of signals, properties, and methods.</span></span>

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

