---
title: AllJoyn 장치 시스템 브리지 개요
author: saraclay
ms.author: saclayt
ms.date: 09/06/17
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: 광범위 한 상호 운용성을 위해 alljoyn 장치를 AllJoyn 에코 시스템에 적응 하는 AllJoyn 장치 시스템 브리지에 대해 알아봅니다.
keywords: windows iot, AllJoyn
ms.openlocfilehash: 305629867bb85600b314fc34de268c46d90ce6e7
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "60167961"
---
> [!NOTE]
> <span data-ttu-id="8ff9a-104">보관 된 설명서를 보고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ff9a-104">You are viewing archived documentation.</span></span> <span data-ttu-id="8ff9a-105">AllJoyn는 Windows 10 IoT에서 더 이상 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8ff9a-105">AllJoyn is no longer supported by Windows 10 IoT.</span></span> <span data-ttu-id="8ff9a-106">질문이 있는 경우 GitHub에서 문제를 열거나 아래 설명에 의견을 남겨 주세요.</span><span class="sxs-lookup"><span data-stu-id="8ff9a-106">For questions, please open an issue on GitHub or leave us feedback in the comments below.</span></span>

# <a name="alljoyn-device-system-bridge"></a><span data-ttu-id="8ff9a-107">AllJoyn 장치 시스템 브리지</span><span class="sxs-lookup"><span data-stu-id="8ff9a-107">AllJoyn Device System Bridge</span></span>

<span data-ttu-id="8ff9a-108">AllJoyn는 개발자에 게 다양 한 플랫폼 및 연결 기술을 사용 하 여 AllJoyn 에코 시스템에 대 한 장치를 구축할 수 있는 유연성을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ff9a-108">AllJoyn provides developers with the flexibility to use a wide range of platforms and connection technologies to build  devices for the AllJoyn ecosystem.</span></span>  <span data-ttu-id="8ff9a-109">그러나 대부분의 장치 제조업체는 포트폴리오에 기존 장치 솔루션을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ff9a-109">However, many device makers have existing device solutions in their portfolios.</span></span> <span data-ttu-id="8ff9a-110">이러한 상황에서 Microsoft는 DSB (장치 시스템 브리지)를 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="8ff9a-110">For these situations, Microsoft created the Device System Bridge (DSB).</span></span> <span data-ttu-id="8ff9a-111">DSB는 적용 되는 장치가 AllJoyn와 공통 언어로 상호 운용할 수 있도록 비-AllJoyn 장치를 AllJoyn 에코 시스템에 적응 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ff9a-111">The DSB adapts non-AllJoyn devices to the AllJoyn ecosystem so that the adapted devices can interoperate with AllJoyn as their common language.</span></span> <span data-ttu-id="8ff9a-112">Microsoft DSB는 Zigbee 및 Z Wave와 같은 홈 자동화 시스템을 지원 하 고 BACnet 같은 산업 빌드 자동화 시스템도 지원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ff9a-112">Microsoft DSB’s support home automation systems such as Zigbee, and Z-Wave, and can even support industrial building automation systems such as BACnet.</span></span>  <span data-ttu-id="8ff9a-113">또한 소스 코드를 사용자 지정 하 여 다른 기술을 지원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ff9a-113">Additionally, the source code is available for customization to support other technologies</span></span>

## <a name="how-dsb-works"></a><span data-ttu-id="8ff9a-114">DSB 작동 방법</span><span class="sxs-lookup"><span data-stu-id="8ff9a-114">How DSB works</span></span>

<span data-ttu-id="8ff9a-115">DSB의 핵심 기능은 AllJoyn 버스에서 장치의 가상 표현을 만드는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="8ff9a-115">The key capability of a DSB is to create a virtual representation of devices on the AllJoyn bus.</span></span> <span data-ttu-id="8ff9a-116">따라서 이러한 장치는 네이티브 연결 또는 장치 에코 시스템에 대해 모두 표시 되 고 AllJoyn 장치로 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ff9a-116">So these devices, whatever their native connectivity or device ecosystem is, will appear and be accessible as AllJoyn devices.</span></span> <span data-ttu-id="8ff9a-117">두 DSBs 아래 그림에서 Z-웨이브 용으로 하나, ZigBee에 대 한 하나는 두 Z 웨이브의 가상 표현과 AllJoyn 버스의 ZigBee 장치 하나를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8ff9a-117">In the picture below two DSBs , one for Z-Wave and one for ZigBee create virtual representation of the two Z-Wave and the one ZigBee devices on the AllJoyn bus.</span></span> <span data-ttu-id="8ff9a-118">이를 사용 하 여 AllJoyn 사이트의 모든 장치는 서로 통신할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ff9a-118">With this all devices on the AllJoyn site can communicate with each other.</span></span> <span data-ttu-id="8ff9a-119">이제는 모든 AllJoyn 버스에서 Z-Wave 및 ZigBee 장치가 서로 통신할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ff9a-119">Because the Z-Wave and ZigBee devices all on the AllJoyn bus they now can communicate with each other as well.</span></span>

![AJ_Docu_DSB_Overview](../media/AllJoyn/AJ_Docu_DSB_Overview.png)

<span data-ttu-id="8ff9a-121">DSB 디자인의 또 다른 주요 요소는 AllJoyn 또는 비-장치 시스템에 대 한 변경이 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8ff9a-121">Another key element of the DSB design is that it will not require any changes to the AllJoyn or non-AllJoyn device system.</span></span> <span data-ttu-id="8ff9a-122">필요한 모든 유발할는 dsb에서 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ff9a-122">All necessary adoptions are done in the DSB.</span></span>

<span data-ttu-id="8ff9a-123">그림에 표시 된 것 처럼, AllJoyn 장치에서 비 AllJoyn 쪽으로의 매핑이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8ff9a-123">As the picture also shows, there is no mapping from AllJoyn devices to the non-AllJoyn side.</span></span> <span data-ttu-id="8ff9a-124">DSB의 목표는 장치를 AllJoyn 에코 시스템으로 가져오는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="8ff9a-124">The objective of the DSB is to bring devices into the AllJoyn ecosystem.</span></span> <span data-ttu-id="8ff9a-125">한 가지 방법만 사용 하도록 설정 하면 개발이 간단해 집니다.</span><span class="sxs-lookup"><span data-stu-id="8ff9a-125">Enabling only one way simplifies the development.</span></span> <span data-ttu-id="8ff9a-126">또한 잠재적으로 보안이 유지 되는 비 AllJoyn 장치 시스템에 의해 AllJoyn 보안 기능이 약화 될 위험이 줄어듭니다.</span><span class="sxs-lookup"><span data-stu-id="8ff9a-126">It also reduces the risk that AllJoyn security capabilities become weakened by the potentially less secure non-AllJoyn device system.</span></span>

## <a name="dsb-architecture"></a><span data-ttu-id="8ff9a-127">DSB 아키텍처</span><span class="sxs-lookup"><span data-stu-id="8ff9a-127">DSB Architecture</span></span>

<span data-ttu-id="8ff9a-128">Microsoft 제안 DSB 아키텍처는 네트워크 액세스 스택, 어댑터 및 브리지의 세 가지 주요 구성 요소로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ff9a-128">The Microsoft proposed DSB architecture consists of three main components, Network Access Stack, Adapter and Bridge.</span></span> <span data-ttu-id="8ff9a-129">아래 그림은이 아키텍처의 대략적인 개요를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8ff9a-129">The picture below shows the high level overview of this architecture.</span></span>

![AJ_Docu_DSB_Architecture](../media/AllJoyn/AJ_Docu_DSB_Architecture.png)

### <a name="bridge"></a><span data-ttu-id="8ff9a-131">Bridge</span><span class="sxs-lookup"><span data-stu-id="8ff9a-131">Bridge</span></span>
* <span data-ttu-id="8ff9a-132">각 내부 장치 개체를 각 장치에 대 한 별도의 버스 첨부 파일, AllJoyn 장치로 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8ff9a-132">Represents each internal device object as AllJoyn device, separate bus attachment for each device</span></span>
* <span data-ttu-id="8ff9a-133">장치는 AllJoyn 버스에서 동적으로 추가 되거나 제거 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ff9a-133">Devices are dynamically added to or removed from the AllJoyn bus</span></span>
* <span data-ttu-id="8ff9a-134">구성에서 장치 표시 유형 및 보안 관리</span><span class="sxs-lookup"><span data-stu-id="8ff9a-134">Configuration manages device visibility and security</span></span>
* <span data-ttu-id="8ff9a-135">브리지 및 어댑터 구성 인터페이스용 버스 첨부 파일 만들기</span><span class="sxs-lookup"><span data-stu-id="8ff9a-135">Creates bus attachment for bridge and adapter configuration interface</span></span>
* <span data-ttu-id="8ff9a-136">브리지 코드는 내부 장치 형식에 독립적 이며 모든 형식에 대해 다시 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ff9a-136">Bridge code is agnostic to internal device types and reusable for any type</span></span>

### <a name="adapter"></a><span data-ttu-id="8ff9a-137">어댑터</span><span class="sxs-lookup"><span data-stu-id="8ff9a-137">Adapter</span></span>
* <span data-ttu-id="8ff9a-138">비-AllJoyn 네트워크에서 각 장치를 대신 하 여 가상 장치를 인스턴스화하고 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ff9a-138">Instantiates and manages virtual devices on behalf of each device from the non-AllJoyn network</span></span>
* <span data-ttu-id="8ff9a-139">장치 스키마를 내부 장치 개체로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ff9a-139">Translates device schemas into internal device objects</span></span>
* <span data-ttu-id="8ff9a-140">네트워크 리소스 (예: 액세스 키, 자격 증명)를 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ff9a-140">Manages network resources, e.g. access keys, credentials</span></span>

### <a name="network-access-stack"></a><span data-ttu-id="8ff9a-141">네트워크 액세스 스택</span><span class="sxs-lookup"><span data-stu-id="8ff9a-141">Network Access Stack</span></span>
* <span data-ttu-id="8ff9a-142">비 AllJoyn 네트워크 관련 액세스 (예: Z-웨이브 스택)</span><span class="sxs-lookup"><span data-stu-id="8ff9a-142">Access to non-AllJoyn Network specific , e.g. Z-Wave stack</span></span>

## <a name="adapter-classes"></a><span data-ttu-id="8ff9a-143">어댑터 클래스</span><span class="sxs-lookup"><span data-stu-id="8ff9a-143">Adapter Classes</span></span>

<span data-ttu-id="8ff9a-144">아래 다이어그램에서는 개발자가 Microsoft DSB 템플릿에서 사용 하는 클래스를 사용 하 여 AllJoyn로 브리지로 브리지로 사용 해야 하는 네이티브 장치의 추상화를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8ff9a-144">The diagram below show the classes developers will use in the Microsoft DSB template to create an abstraction of the native devices that need to be bridged into AllJoyn.</span></span> <span data-ttu-id="8ff9a-145">브리지는 어댑터 클래스의 인스턴스를 사용 하 여 어댑터. 장치 목록에서 각 장치에 대 한 버스 첨부 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8ff9a-145">The Bridge will use the instance of the adapter class to create the bus attachments for each device in the Adapter.devices list.</span></span>
<span data-ttu-id="8ff9a-146">![AJ_Docu_DSB_Class_Diagram](../media/AllJoyn/AJ_Docu_DSB_Class_Diagram.png)</span><span class="sxs-lookup"><span data-stu-id="8ff9a-146">![AJ_Docu_DSB_Class_Diagram](../media/AllJoyn/AJ_Docu_DSB_Class_Diagram.png)</span></span>

## <a name="special-handlers"></a><span data-ttu-id="8ff9a-147">특수 처리기</span><span class="sxs-lookup"><span data-stu-id="8ff9a-147">Special Handlers</span></span>

<span data-ttu-id="8ff9a-148">AllJoyn은 몇 가지 기본 서비스와 표준 인터페이스 프레임 워크 (예: LSF, HAE 또는 제어판)를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ff9a-148">AllJoyn specifies several base services and standard interfaces frameworks such as LSF, HAE or Control Panel.</span></span> <span data-ttu-id="8ff9a-149">DSB는 특수 한 처리기를 사용 하 여 이러한 것을 노출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ff9a-149">The DSB can exposes those with special handlers.</span></span> <span data-ttu-id="8ff9a-150">현재 DSB 템플릿 릴리스에는 LSF 및 제어판 인터페이스의 구현이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ff9a-150">The current release of the DSB template contains implementations of the LSF and Control Panel interfaces.</span></span> <span data-ttu-id="8ff9a-151">개발자는 브리지의 LSN 및 제어판 인터페이스에 대 한 콜백 함수에 해당 코드를 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ff9a-151">Developers will connect their code to the callback functions for LSF and Control Panel interfaces in the bridge.</span></span>

![AJ_Docu_DSB_Special_Handlers](../media/AllJoyn/AJ_Docu_DSB_Special_Handlers.png)

## <a name="dsb-resources"></a><span data-ttu-id="8ff9a-153">DSB 리소스</span><span class="sxs-lookup"><span data-stu-id="8ff9a-153">DSB Resources</span></span>

### <a name="visual-studio-dsb-template"></a><span data-ttu-id="8ff9a-154">Visual Studio DSB 템플릿</span><span class="sxs-lookup"><span data-stu-id="8ff9a-154">Visual Studio DSB Template</span></span>

<span data-ttu-id="8ff9a-155">Visual Studio DSB 템플릿은 새 DSB 프로젝트를 쉽게 만들 수 있는 Visual Studio의 확장입니다.</span><span class="sxs-lookup"><span data-stu-id="8ff9a-155">Visual Studio DSB Template is an extension to Visual Studio that lets you easily create new DSB projects.</span></span> <span data-ttu-id="8ff9a-156">이 프로젝트는 연결, 어댑터에 대 한 셸 프로젝트, 모든 솔루션 파일 등 모든 필수 구성 요소를 만들어 DSB를 단방향 또는 헤드리스 장치로 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="8ff9a-156">The project will create all the necessary components such as the Bridge, a shell project for the adapter and all solution files to build the DSB as headed or headless device.</span></span> <span data-ttu-id="8ff9a-157">이 Visual Studio 확장에는 네이티브 및 관리 되는 AllJoyn 장치 시스템 브리지 템플릿이 모두 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ff9a-157">This Visual Studio extension contains both the Native and Managed AllJoyn Device System Bridge templates.</span></span>

<span data-ttu-id="8ff9a-158">다음 위치에서 DSB 템플릿을 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ff9a-158">Download DSB Template from these locations:</span></span>

* [<span data-ttu-id="8ff9a-159">Visual Studio 2015 용 DSB 템플릿</span><span class="sxs-lookup"><span data-stu-id="8ff9a-159">DSB Template for Visual Studio 2015</span></span>](https://visualstudiogallery.msdn.microsoft.com/aea0b437-ef07-42e3-bd88-8c7f906d5da8)
* <span data-ttu-id="8ff9a-160">[Visual Studio 2017](https://marketplace.visualstudio.com/vsgallery/c5f52768-8df7-42ff-b84e-d66d3d22fb50)
dsb 용 dsb 템플릿은_Visual Studio Tools > 확장 및 업데이트 ...-> 온라인-> "검색" 필드 형식 "dsb"를 통해 설치할 수도_ 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ff9a-160">[DSB Template for Visual Studio 2017](https://marketplace.visualstudio.com/vsgallery/c5f52768-8df7-42ff-b84e-d66d3d22fb50)
_DSB Template can also be installed through Visual Studio Tools -> Extensions and Updates … -> Online -> In the "Search" field type "DSB"._</span></span>

<span data-ttu-id="8ff9a-161">[DSB 개체를 alljoyn에 매핑](AlljoynDsbApiGuide.md) 문서에서는 Alljoyn 시스템 브리지를 빌드하는 데 사용 되는 키 인터페이스 및 메서드에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ff9a-161">The [Mapping DSB Objects to AllJoyn](AlljoynDsbApiGuide.md) document describes the key interfaces and methods used to build the Alljoyn System Bridge.</span></span>

### <a name="sample-dsbs"></a><span data-ttu-id="8ff9a-162">샘플 DSBs</span><span class="sxs-lookup"><span data-stu-id="8ff9a-162">Sample DSBs</span></span>

* [<span data-ttu-id="8ff9a-163">AllJoyn DSB 모의 어댑터 자습서 및 샘플</span><span class="sxs-lookup"><span data-stu-id="8ff9a-163">AllJoyn DSB Mock Adapter Tutorial and Sample</span></span>](https://developer.microsoft.com/en-us/windows/iot/samples/alljoynmockadapter)
  * <span data-ttu-id="8ff9a-164">이 자습서에서는 장치 시스템 브리지 앱을 사용 하 여 IoT Core 장치를 모의 BACnet 장치에 연결 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8ff9a-164">This tutorial shows how to use the Device System Bridge app to connect your  IoT Core devices to mock BACnet devices.</span></span>
* [<span data-ttu-id="8ff9a-165">AllJoyn DSB Z-웨이브 어댑터 자습서 및 샘플</span><span class="sxs-lookup"><span data-stu-id="8ff9a-165">AllJoyn DSB Z-Wave Adapter Tutorial and Sample</span></span>](https://developer.microsoft.com/en-us/windows/iot/samples/zwaveadapter)
  * <span data-ttu-id="8ff9a-166">이 자습서에서는 장치 시스템 브리지 앱을 사용 하 여 IoT Core 장치를 Z 웨이브 장치에 연결 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8ff9a-166">This tutorial shows how to use the Device System Bridge app to connect your  IoT Core devices to Z-Wave devices.</span></span>
* [<span data-ttu-id="8ff9a-167">AllJoyn DSB GPIO 어댑터 자습서C++</span><span class="sxs-lookup"><span data-stu-id="8ff9a-167">AllJoyn DSB GPIO Adapter Tutorial C++</span></span>](https://developer.microsoft.com/en-us/windows/iot/samples/alljoyndsb)
  * <span data-ttu-id="8ff9a-168">이 자습서에서는 AllJoyn 장치 시스템 브리지 템플릿을 사용 하 여 장치 GPIO를 연습 하 C++ 는 샘플 앱을 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8ff9a-168">This tutorial demonstrates how to use the AllJoyn Device System Bridge template to create a sample C++ app that exercises the device GPIO.</span></span>
* [<span data-ttu-id="8ff9a-169">AllJoyn DSB GPIO 어댑터 자습서C#</span><span class="sxs-lookup"><span data-stu-id="8ff9a-169">AllJoyn DSB GPIO Adapter Tutorial C#</span></span>](https://developer.microsoft.com/en-us/windows/iot/samples/alljoyndsbcs)
  * <span data-ttu-id="8ff9a-170">이 자습서에서는 AllJoyn 장치 시스템 브리지 템플릿을 사용 하 여 장치 GPIO를 연습 하는 샘플 관리 앱을 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8ff9a-170">This tutorial demonstrates how to use the AllJoyn Device System Bridge template to create a sample managed app that exercises the device GPIO.</span></span>
* [<span data-ttu-id="8ff9a-171">AllJoyn DSB ZigBee Adapter 자습서 및 샘플</span><span class="sxs-lookup"><span data-stu-id="8ff9a-171">AllJoyn DSB ZigBee Adapter Tutorial and Sample</span></span>](https://developer.microsoft.com/en-us/windows/iot/samples/ZigBeeAdapter)
  * <span data-ttu-id="8ff9a-172">이 자습서에서는 장치 시스템 브리지 앱을 사용 하 여 IoT Core 장치를 ZigBee 장치에 연결 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8ff9a-172">This tutorial shows how to use the Device System Bridge app to connect your IoT Core devices to ZigBee devices.</span></span>
* [<span data-ttu-id="8ff9a-173">AllJoyn DSB BACnet Adapter 자습서 및 샘플</span><span class="sxs-lookup"><span data-stu-id="8ff9a-173">AllJoyn DSB BACnet Adapter Tutorial and Sample</span></span>](https://developer.microsoft.com/en-us/windows/iot/samples/BACnetAdapter)
  * <span data-ttu-id="8ff9a-174">이 자습서에서는 장치 시스템 브리지 앱을 사용 하 여 IoT Core 장치를 BACnet 장치에 연결 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8ff9a-174">This tutorial shows how to use the Device System Bridge app to connect your IoT Core devices to BACnet devices.</span></span>
* [<span data-ttu-id="8ff9a-175">AllJoyn 자습서</span><span class="sxs-lookup"><span data-stu-id="8ff9a-175">AllJoyn.JS Tutorial</span></span>](https://developer.microsoft.com/en-us/windows/iot/samples/AllJoynJS)
  * <span data-ttu-id="8ff9a-176">이 자습서에서는 Allseen 동맹에서 개발한 응용 프로그램을 Windows 10 응용 프로그램으로 실행 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8ff9a-176">This tutorial shows how to run AllJoyn.JS application developed by Allseen Alliance as a Windows 10 application.</span></span> <span data-ttu-id="8ff9a-177">AllJoyn를 사용 하면 JavaScript를 작성 하 여 AllJoyn 장치를 만들고 모니터링 하 고 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ff9a-177">AllJoyn.JS allows you to write JavaScript to create, monitor and control AllJoyn devices.</span></span>
* [<span data-ttu-id="8ff9a-178">AllJoyn DSB OIC 어댑터 자습서 및 샘플</span><span class="sxs-lookup"><span data-stu-id="8ff9a-178">AllJoyn DSB OIC Adapter Tutorial and Sample</span></span>](https://developer.microsoft.com/en-us/windows/iot/samples/OICAdapter)
  * <span data-ttu-id="8ff9a-179">이 자습서에서는 장치 시스템 브리지 앱을 사용 하 여 IoT Core 장치를 IoTivity/OIC 장치에 연결 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8ff9a-179">This tutorial shows how to use the Device System Bridge app to connect your  IoT Core devices to IoTivity/OIC devices.</span></span>
