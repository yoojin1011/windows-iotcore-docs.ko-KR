---
title: AllJoyn 장치 시스템 연결 개요
author: saraclay
ms.author: saclayt
ms.date: 09/06/17
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: 광범위 한 상호 운용성을 위해 AllJoyn 에코 시스템에 비 AllJoyn 장치 적응할 수 있는 AllJoyn 장치 시스템 연결에 알아봅니다.
keywords: windows iot, AllJoyn
ms.openlocfilehash: 305629867bb85600b314fc34de268c46d90ce6e7
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512469"
---
> [!NOTE]
> <span data-ttu-id="c383d-104">보관 된 설명서가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c383d-104">You are viewing archived documentation.</span></span> <span data-ttu-id="c383d-105">Windows 10 IoT에서 더 이상 AllJoyn 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c383d-105">AllJoyn is no longer supported by Windows 10 IoT.</span></span> <span data-ttu-id="c383d-106">질문에 대 한 GitHub에서 문제를 제기 하거나 아래 설명에 의견을 남길 하세요.</span><span class="sxs-lookup"><span data-stu-id="c383d-106">For questions, please open an issue on GitHub or leave us feedback in the comments below.</span></span>

# <a name="alljoyn-device-system-bridge"></a><span data-ttu-id="c383d-107">AllJoyn 장치 시스템 연결</span><span class="sxs-lookup"><span data-stu-id="c383d-107">AllJoyn Device System Bridge</span></span>

<span data-ttu-id="c383d-108">AllJoyn 자유롭게 AllJoyn 에코 시스템에 대 한 장치 빌드에 광범위 한 플랫폼 및 연결 기술을 사용 하 여 개발자에 게 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="c383d-108">AllJoyn provides developers with the flexibility to use a wide range of platforms and connection technologies to build  devices for the AllJoyn ecosystem.</span></span>  <span data-ttu-id="c383d-109">그러나 많은 장치 제조업체 경우 기존 장치 솔루션 포트폴리오</span><span class="sxs-lookup"><span data-stu-id="c383d-109">However, many device makers have existing device solutions in their portfolios.</span></span> <span data-ttu-id="c383d-110">이러한 상황에 대 한 Microsoft 장치 시스템 브리지 (DSB)를 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="c383d-110">For these situations, Microsoft created the Device System Bridge (DSB).</span></span> <span data-ttu-id="c383d-111">DSB 맞게 조정된 장치를 공통 언어로 AllJoyn 상호 운용할 수 있도록 AllJoyn 에코 시스템에 AllJoyn 아닌 장치를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="c383d-111">The DSB adapts non-AllJoyn devices to the AllJoyn ecosystem so that the adapted devices can interoperate with AllJoyn as their common language.</span></span> <span data-ttu-id="c383d-112">Microsoft DSB Zigbee, 등 Z-wave를 자동화 시스템 홈 지원과 지원 산업 BACnet 같은 자동화 시스템을 구축할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c383d-112">Microsoft DSB’s support home automation systems such as Zigbee, and Z-Wave, and can even support industrial building automation systems such as BACnet.</span></span>  <span data-ttu-id="c383d-113">또한, 소스 코드는 다른 기술을 지원 하기 위해 사용자 지정에 대 한 사용 가능</span><span class="sxs-lookup"><span data-stu-id="c383d-113">Additionally, the source code is available for customization to support other technologies</span></span>

## <a name="how-dsb-works"></a><span data-ttu-id="c383d-114">DSB의 작동 원리</span><span class="sxs-lookup"><span data-stu-id="c383d-114">How DSB works</span></span>

<span data-ttu-id="c383d-115">DSB의 주요 기능이 AllJoyn 버스에 가상 장치 표현을 만드는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="c383d-115">The key capability of a DSB is to create a virtual representation of devices on the AllJoyn bus.</span></span> <span data-ttu-id="c383d-116">이러한 장치는 네이티브 연결 또는 장치 에코 시스템은 모든 표시 되 고 AllJoyn 장치로 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c383d-116">So these devices, whatever their native connectivity or device ecosystem is, will appear and be accessible as AllJoyn devices.</span></span> <span data-ttu-id="c383d-117">두 DSBs 아래 그림에서는 Z-wave에 대 한 개와 ZigBee AllJoyn 버스의 두 Z-wave와 하나의 ZigBee 장치의 가상 표현을 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="c383d-117">In the picture below two DSBs , one for Z-Wave and one for ZigBee create virtual representation of the two Z-Wave and the one ZigBee devices on the AllJoyn bus.</span></span> <span data-ttu-id="c383d-118">AllJoyn에서이 모든 장치를 사용 하 여 사이트는 서로 통신할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c383d-118">With this all devices on the AllJoyn site can communicate with each other.</span></span> <span data-ttu-id="c383d-119">AllJoyn 버스에 모든 ZigBee 장치와 Z-wave 통신할 수 없기 때문에 이제 수 서로 합니다.</span><span class="sxs-lookup"><span data-stu-id="c383d-119">Because the Z-Wave and ZigBee devices all on the AllJoyn bus they now can communicate with each other as well.</span></span>

![AJ_Docu_DSB_Overview](../media/AllJoyn/AJ_Docu_DSB_Overview.png)

<span data-ttu-id="c383d-121">DSB 디자인의 또 다른 핵심 요소는 AllJoyn 또는 비 AllJoyn 장치 시스템 변경 필요 하지 것입니다.</span><span class="sxs-lookup"><span data-stu-id="c383d-121">Another key element of the DSB design is that it will not require any changes to the AllJoyn or non-AllJoyn device system.</span></span> <span data-ttu-id="c383d-122">모든 필요한 도입 된 DSB에서 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c383d-122">All necessary adoptions are done in the DSB.</span></span>

<span data-ttu-id="c383d-123">또한 그림과 같이 비 AllJoyn 쪽 AllJoyn 장치의 매핑이 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c383d-123">As the picture also shows, there is no mapping from AllJoyn devices to the non-AllJoyn side.</span></span> <span data-ttu-id="c383d-124">DSB의 목표는 AllJoyn 에코 시스템으로 장치를 가져오는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="c383d-124">The objective of the DSB is to bring devices into the AllJoyn ecosystem.</span></span> <span data-ttu-id="c383d-125">하나의 방법을 개발을 간소화 합니다.</span><span class="sxs-lookup"><span data-stu-id="c383d-125">Enabling only one way simplifies the development.</span></span> <span data-ttu-id="c383d-126">위험이 해당 AllJoyn 안전 하지 않은 AllJoyn 장치 시스템 보안 기능 약화 될 수도 줄어듭니다.</span><span class="sxs-lookup"><span data-stu-id="c383d-126">It also reduces the risk that AllJoyn security capabilities become weakened by the potentially less secure non-AllJoyn device system.</span></span>

## <a name="dsb-architecture"></a><span data-ttu-id="c383d-127">DSB 아키텍처</span><span class="sxs-lookup"><span data-stu-id="c383d-127">DSB Architecture</span></span>

<span data-ttu-id="c383d-128">Microsoft 제안 DSB 아키텍처 브리지, 어댑터 및 네트워크 액세스 스택의 세 가지 주요 구성 요소로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c383d-128">The Microsoft proposed DSB architecture consists of three main components, Network Access Stack, Adapter and Bridge.</span></span> <span data-ttu-id="c383d-129">아래 그림은이 아키텍처의 대략적인 개요를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="c383d-129">The picture below shows the high level overview of this architecture.</span></span>

![AJ_Docu_DSB_Architecture](../media/AllJoyn/AJ_Docu_DSB_Architecture.png)

### <a name="bridge"></a><span data-ttu-id="c383d-131">브리지</span><span class="sxs-lookup"><span data-stu-id="c383d-131">Bridge</span></span>
* <span data-ttu-id="c383d-132">각 장치에 대 한 별도 버스 첨부 AllJoyn 장치로 각 내부 장치 개체를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c383d-132">Represents each internal device object as AllJoyn device, separate bus attachment for each device</span></span>
* <span data-ttu-id="c383d-133">장치 동적으로 추가 되거나 AllJoyn 버스에서 제거</span><span class="sxs-lookup"><span data-stu-id="c383d-133">Devices are dynamically added to or removed from the AllJoyn bus</span></span>
* <span data-ttu-id="c383d-134">장치 유형과 보안 구성 관리</span><span class="sxs-lookup"><span data-stu-id="c383d-134">Configuration manages device visibility and security</span></span>
* <span data-ttu-id="c383d-135">브리지와 어댑터 구성 인터페이스에 bus 첨부 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c383d-135">Creates bus attachment for bridge and adapter configuration interface</span></span>
* <span data-ttu-id="c383d-136">브리지 코드는 내부 디바이스를 다시 사용할 수 있는 모든 형식에 대 한 알 수 없는</span><span class="sxs-lookup"><span data-stu-id="c383d-136">Bridge code is agnostic to internal device types and reusable for any type</span></span>

### <a name="adapter"></a><span data-ttu-id="c383d-137">어댑터</span><span class="sxs-lookup"><span data-stu-id="c383d-137">Adapter</span></span>
* <span data-ttu-id="c383d-138">인스턴스화하고 AllJoyn 비 네트워크에서 각 장치를 대신 하 여 가상 장치를 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="c383d-138">Instantiates and manages virtual devices on behalf of each device from the non-AllJoyn network</span></span>
* <span data-ttu-id="c383d-139">장치 스키마를 내부 장치 개체 변환</span><span class="sxs-lookup"><span data-stu-id="c383d-139">Translates device schemas into internal device objects</span></span>
* <span data-ttu-id="c383d-140">네트워크 리소스, 예: 액세스 키를 자격 증명 관리</span><span class="sxs-lookup"><span data-stu-id="c383d-140">Manages network resources, e.g. access keys, credentials</span></span>

### <a name="network-access-stack"></a><span data-ttu-id="c383d-141">네트워크 액세스 스택</span><span class="sxs-lookup"><span data-stu-id="c383d-141">Network Access Stack</span></span>
* <span data-ttu-id="c383d-142">예를 들어 Z-wave 스택 AllJoyn 비 네트워크 관련에 대 한 액세스</span><span class="sxs-lookup"><span data-stu-id="c383d-142">Access to non-AllJoyn Network specific , e.g. Z-Wave stack</span></span>

## <a name="adapter-classes"></a><span data-ttu-id="c383d-143">어댑터 클래스</span><span class="sxs-lookup"><span data-stu-id="c383d-143">Adapter Classes</span></span>

<span data-ttu-id="c383d-144">아래 다이어그램 AllJoyn에 해결 해야 하는 네이티브 장치 추상화를 만들려면 Microsoft DSB 템플릿에서 개발자가 사용 하 여 클래스를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c383d-144">The diagram below show the classes developers will use in the Microsoft DSB template to create an abstraction of the native devices that need to be bridged into AllJoyn.</span></span> <span data-ttu-id="c383d-145">브리지는 Adapter.devices 목록의 각 장치에 대 한 버스 첨부 파일을 만들려면 어댑터 클래스의 인스턴스를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c383d-145">The Bridge will use the instance of the adapter class to create the bus attachments for each device in the Adapter.devices list.</span></span>
![AJ_Docu_DSB_Class_Diagram](../media/AllJoyn/AJ_Docu_DSB_Class_Diagram.png)

## <a name="special-handlers"></a><span data-ttu-id="c383d-147">특수 처리기</span><span class="sxs-lookup"><span data-stu-id="c383d-147">Special Handlers</span></span>

<span data-ttu-id="c383d-148">AllJoyn 몇 가지 기본 서비스 및 LSF, HAE 또는 Control Panel과 같은 표준 인터페이스 프레임 워크를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c383d-148">AllJoyn specifies several base services and standard interfaces frameworks such as LSF, HAE or Control Panel.</span></span> <span data-ttu-id="c383d-149">DSB 특수 처리기를 사용 하 여 해당 노출 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c383d-149">The DSB can exposes those with special handlers.</span></span> <span data-ttu-id="c383d-150">현재 릴리스의 DSB 템플릿 LSF 및 제어판 인터페이스의 구현을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="c383d-150">The current release of the DSB template contains implementations of the LSF and Control Panel interfaces.</span></span> <span data-ttu-id="c383d-151">개발자는 해당 코드 브리지에 LSF 및 제어판 인터페이스에 대 한 콜백 함수에 연결 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c383d-151">Developers will connect their code to the callback functions for LSF and Control Panel interfaces in the bridge.</span></span>

![AJ_Docu_DSB_Special_Handlers](../media/AllJoyn/AJ_Docu_DSB_Special_Handlers.png)

## <a name="dsb-resources"></a><span data-ttu-id="c383d-153">DSB 리소스</span><span class="sxs-lookup"><span data-stu-id="c383d-153">DSB Resources</span></span>

### <a name="visual-studio-dsb-template"></a><span data-ttu-id="c383d-154">Visual Studio DSB 템플릿</span><span class="sxs-lookup"><span data-stu-id="c383d-154">Visual Studio DSB Template</span></span>

<span data-ttu-id="c383d-155">Visual Studio DSB 서식 파일에는 쉽게 새 DSB 프로젝트를 만들 수 있는 Visual studio 확장입니다.</span><span class="sxs-lookup"><span data-stu-id="c383d-155">Visual Studio DSB Template is an extension to Visual Studio that lets you easily create new DSB projects.</span></span> <span data-ttu-id="c383d-156">프로젝트에 브리지 헤드 또는 헤드리스 장치로 DSB 빌드하려면 어댑터 및 모든 솔루션 파일에 대 한 셸 프로젝트와 같은 필요한 모든 구성 요소가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="c383d-156">The project will create all the necessary components such as the Bridge, a shell project for the adapter and all solution files to build the DSB as headed or headless device.</span></span> <span data-ttu-id="c383d-157">이 Visual Studio 확장에는 네이티브 및 관리 되는 AllJoyn 장치 시스템 브리지 템플릿을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="c383d-157">This Visual Studio extension contains both the Native and Managed AllJoyn Device System Bridge templates.</span></span>

<span data-ttu-id="c383d-158">이러한 위치에서 DSB 템플릿을 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="c383d-158">Download DSB Template from these locations:</span></span>

* [<span data-ttu-id="c383d-159">Visual Studio 2015 용 DSB 템플릿</span><span class="sxs-lookup"><span data-stu-id="c383d-159">DSB Template for Visual Studio 2015</span></span>](https://visualstudiogallery.msdn.microsoft.com/aea0b437-ef07-42e3-bd88-8c7f906d5da8)
* <span data-ttu-id="c383d-160">[Visual Studio 2017에 대 한 템플릿을 DSB](https://marketplace.visualstudio.com/vsgallery/c5f52768-8df7-42ff-b84e-d66d3d22fb50)
_DSB 템플릿을 통해도 설치할 수 있습니다 Visual Studio Tools-> 확장 및 업데이트... 온라인-> "검색" 필드 형식 "DSB"-> 합니다._</span><span class="sxs-lookup"><span data-stu-id="c383d-160">[DSB Template for Visual Studio 2017](https://marketplace.visualstudio.com/vsgallery/c5f52768-8df7-42ff-b84e-d66d3d22fb50)
_DSB Template can also be installed through Visual Studio Tools -> Extensions and Updates … -> Online -> In the "Search" field type "DSB"._</span></span>

<span data-ttu-id="c383d-161">합니다 [AllJoyn DSB 개체 매핑](AlljoynDsbApiGuide.md) 문서 키 인터페이스 및 Alljoyn 시스템 브리지를 빌드하는 데 사용 하는 방법에 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="c383d-161">The [Mapping DSB Objects to AllJoyn](AlljoynDsbApiGuide.md) document describes the key interfaces and methods used to build the Alljoyn System Bridge.</span></span>

### <a name="sample-dsbs"></a><span data-ttu-id="c383d-162">샘플 DSBs</span><span class="sxs-lookup"><span data-stu-id="c383d-162">Sample DSBs</span></span>

* [<span data-ttu-id="c383d-163">AllJoyn DSB 모의 어댑터 자습서 및 샘플</span><span class="sxs-lookup"><span data-stu-id="c383d-163">AllJoyn DSB Mock Adapter Tutorial and Sample</span></span>](https://developer.microsoft.com/en-us/windows/iot/samples/alljoynmockadapter)
  * <span data-ttu-id="c383d-164">이 자습서에서는 모의 BACnet 장치를 IoT Core 장치에 연결할 장치 시스템 브리지 앱을 사용 하는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="c383d-164">This tutorial shows how to use the Device System Bridge app to connect your  IoT Core devices to mock BACnet devices.</span></span>
* [<span data-ttu-id="c383d-165">AllJoyn DSB Z-wave 어댑터 자습서 및 샘플</span><span class="sxs-lookup"><span data-stu-id="c383d-165">AllJoyn DSB Z-Wave Adapter Tutorial and Sample</span></span>](https://developer.microsoft.com/en-us/windows/iot/samples/zwaveadapter)
  * <span data-ttu-id="c383d-166">이 자습서에는 장치 시스템 브리지 앱을 사용 하 여 IoT Core 장치 Z-wave 장치를 연결 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c383d-166">This tutorial shows how to use the Device System Bridge app to connect your  IoT Core devices to Z-Wave devices.</span></span>
* [<span data-ttu-id="c383d-167">AllJoyn DSB GPIO 어댑터 자습서C++</span><span class="sxs-lookup"><span data-stu-id="c383d-167">AllJoyn DSB GPIO Adapter Tutorial C++</span></span>](https://developer.microsoft.com/en-us/windows/iot/samples/alljoyndsb)
  * <span data-ttu-id="c383d-168">이 자습서에는 예제를 만들려면 AllJoyn 장치 시스템 브리지 템플릿을 사용 하는 방법을 보여 줍니다. C++ GPIO 장치를 실행 하는 앱입니다.</span><span class="sxs-lookup"><span data-stu-id="c383d-168">This tutorial demonstrates how to use the AllJoyn Device System Bridge template to create a sample C++ app that exercises the device GPIO.</span></span>
* [<span data-ttu-id="c383d-169">AllJoyn DSB GPIO 어댑터 자습서C#</span><span class="sxs-lookup"><span data-stu-id="c383d-169">AllJoyn DSB GPIO Adapter Tutorial C#</span></span>](https://developer.microsoft.com/en-us/windows/iot/samples/alljoyndsbcs)
  * <span data-ttu-id="c383d-170">이 자습서에는 AllJoyn 장치 시스템 브리지 템플릿을 사용 하 여 장치 GPIO를 실행 하는 샘플 관리 되는 앱을 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c383d-170">This tutorial demonstrates how to use the AllJoyn Device System Bridge template to create a sample managed app that exercises the device GPIO.</span></span>
* [<span data-ttu-id="c383d-171">AllJoyn DSB ZigBee 어댑터 자습서 및 샘플</span><span class="sxs-lookup"><span data-stu-id="c383d-171">AllJoyn DSB ZigBee Adapter Tutorial and Sample</span></span>](https://developer.microsoft.com/en-us/windows/iot/samples/ZigBeeAdapter)
  * <span data-ttu-id="c383d-172">이 자습서에는 장치 시스템 브리지 앱을 사용 하 여 IoT Core 장치 ZigBee 장치를 연결 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c383d-172">This tutorial shows how to use the Device System Bridge app to connect your IoT Core devices to ZigBee devices.</span></span>
* [<span data-ttu-id="c383d-173">AllJoyn DSB BACnet 어댑터 자습서 및 샘플</span><span class="sxs-lookup"><span data-stu-id="c383d-173">AllJoyn DSB BACnet Adapter Tutorial and Sample</span></span>](https://developer.microsoft.com/en-us/windows/iot/samples/BACnetAdapter)
  * <span data-ttu-id="c383d-174">이 자습서에는 장치 시스템 브리지 앱을 사용 하 여 IoT Core 장치 BACnet 장치를 연결 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c383d-174">This tutorial shows how to use the Device System Bridge app to connect your IoT Core devices to BACnet devices.</span></span>
* [<span data-ttu-id="c383d-175">AllJoyn.JS 자습서</span><span class="sxs-lookup"><span data-stu-id="c383d-175">AllJoyn.JS Tutorial</span></span>](https://developer.microsoft.com/en-us/windows/iot/samples/AllJoynJS)
  * <span data-ttu-id="c383d-176">이 자습서에는 Windows 10 응용 프로그램으로 Allseen Alliance 개발한 AllJoyn.JS 응용 프로그램을 실행 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c383d-176">This tutorial shows how to run AllJoyn.JS application developed by Allseen Alliance as a Windows 10 application.</span></span> <span data-ttu-id="c383d-177">AllJoyn.JS를 사용 하면 만들기, 모니터링 및 AllJoyn 장치를 제어 하는 JavaScript를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c383d-177">AllJoyn.JS allows you to write JavaScript to create, monitor and control AllJoyn devices.</span></span>
* [<span data-ttu-id="c383d-178">AllJoyn DSB OIC 어댑터 자습서 및 샘플</span><span class="sxs-lookup"><span data-stu-id="c383d-178">AllJoyn DSB OIC Adapter Tutorial and Sample</span></span>](https://developer.microsoft.com/en-us/windows/iot/samples/OICAdapter)
  * <span data-ttu-id="c383d-179">이 자습서에는 장치 시스템 브리지 앱을 사용 하 여 IoT Core 장치 IoTivity/OIC 장치를 연결 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c383d-179">This tutorial shows how to use the Device System Bridge app to connect your  IoT Core devices to IoTivity/OIC devices.</span></span>
