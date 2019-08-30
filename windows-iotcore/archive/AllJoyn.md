---
title: AllJoyn 개요
author: saraclay
ms.author: saclayt
ms.date: 09/06/17
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: Windows IoT에서 다른 확장 및 기능을 사용 하도록 설정 하는 방법 및 IoT 장치에 대 한 일반적인 프로토콜인 AllJoyn에 대해 알아봅니다.
keywords: windows iot, AllJoyn
ms.openlocfilehash: 6b558680d479c71b6b8a22d34d03b04e5cbdbd76
ms.sourcegitcommit: 0f46b7b5c15906a6c82b847ffcd9f4d2674f9fd0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65226832"
---
> [!NOTE]
> <span data-ttu-id="aeee7-104">보관 된 설명서를 보고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aeee7-104">You are viewing archived documentation.</span></span> <span data-ttu-id="aeee7-105">AllJoyn는 Windows 10 IoT에서 더 이상 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="aeee7-105">AllJoyn is no longer supported by Windows 10 IoT.</span></span> <span data-ttu-id="aeee7-106">질문에 대 한 대안 인 경우 AllJoyn에 사용 되는 앱 계층 IoT 프로토콜은 [오픈 연결 기반이](https://openconnectivity.org)됩니다.</span><span class="sxs-lookup"><span data-stu-id="aeee7-106">For questions, alternatives, the app-layer IoT protocol that serves for AllJoyn is the [Open Connectivity Foundation](https://openconnectivity.org).</span></span> <span data-ttu-id="aeee7-107">OCF 사양의 표준 구현은 Iotivity입니다. Iotivity에 대 한 Windows 지원은 [여기](https://wiki.iotivity.org/windows)에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aeee7-107">The standard implementation of the OCF spec is Iotivity - Windows support for Iotivity can be found [here](https://wiki.iotivity.org/windows).</span></span>

# <a name="alljoyn"></a><span data-ttu-id="aeee7-108">AllJoyn</span><span class="sxs-lookup"><span data-stu-id="aeee7-108">AllJoyn</span></span>

<span data-ttu-id="aeee7-109">AllJoyn은 사물 인터넷를 강화 합니다.</span><span class="sxs-lookup"><span data-stu-id="aeee7-109">AllJoyn empowers the Internet of Things.</span></span> <span data-ttu-id="aeee7-110">AllJoyn은 장치 및 응용 프로그램이 전송 기술, 플랫폼 또는 제조업체와 관계 없이 서로를 검색 하 고 통신 하는 데 사용할 수 있는 공통 프로토콜을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="aeee7-110">AllJoyn defines a common protocol for devices and applications to discover and communicate with each other regardless of transport technology, platform or manufacturer.</span></span>  <span data-ttu-id="aeee7-111">AllJoyn는 사물 인터넷에 대 한 수십억 개의 장치, 서비스 및 응용 프로그램의 상호 운용성을 사용 하도록 설정 하는 데 사용 되는 다중 업계 컨소시엄 인 [Allseen 동맹](https://allseenalliance.org/)에 의해 구동 되는 오픈 소스 표준입니다.</span><span class="sxs-lookup"><span data-stu-id="aeee7-111">AllJoyn is an open source standard driven by the [AllSeen Alliance](https://allseenalliance.org/), a cross-industry consortium dedicated to enabling the interoperability of billions of devices, services and applications for the Internet of Things.</span></span>

<span data-ttu-id="aeee7-112">Microsoft는 Windows 10에서 Windows 10의 핵심 구성 요소로, 2014에 AllSeen 동맹을 조인 했습니다.</span><span class="sxs-lookup"><span data-stu-id="aeee7-112">Microsoft joined the AllSeen Alliance in 2014 and added AllJoyn as a core component in Windows 10.</span></span> <span data-ttu-id="aeee7-113">기본 제공 [Alljoyn api](https://msdn.microsoft.com/library/windows/apps/windows.devices.alljoyn.aspx)를 사용 하는 개발자는 pc, 태블릿, 휴대폰, Xbox 뿐만 아니라 Windows IoT Core를 사용 하는 장치를 비롯 한 모든 windows 10 장치에서 실행 되는 AllJoyn 지원 응용 프로그램을 자유롭게 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aeee7-113">With the built-in [AllJoyn APIs](https://msdn.microsoft.com/library/windows/apps/windows.devices.alljoyn.aspx), developers are free to write AllJoyn capable applications that run on any of the Windows 10 devices including PCs, tablets, phones, Xbox as well as devices using Windows IoT Core.</span></span> <span data-ttu-id="aeee7-114">Microsoft에서는 alljoyn에 대 한 플랫폼 지원 외에도 미리 만들어진 응용 프로그램 템플릿과 코드 생성을 결합 하 여 AllJoyn 개발을 가속화 하는 Visual Studio 확장인 [Alljoyn studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286)를 출시 했습니다.</span><span class="sxs-lookup"><span data-stu-id="aeee7-114">In addition to the platform support for AllJoyn, Microsoft released [AllJoyn Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286), a Visual Studio extension that accelerates AllJoyn development by combining code generation with ready-made application templates.</span></span> <span data-ttu-id="aeee7-115">개발자는 AllJoyn Studio를 사용 하 여 설정 및 구성을 하지 않고도 AllJoyn 기능을 활용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aeee7-115">AllJoyn Studio allows developers to benefit from the power of AllJoyn without the hassle of set-up and configuration.</span></span>

<span data-ttu-id="aeee7-116">AllJoyn이 있나요?</span><span class="sxs-lookup"><span data-stu-id="aeee7-116">Excited about AllJoyn?</span></span> <span data-ttu-id="aeee7-117">Windows에서 AllJoyn를 시작 하는 방법에 대 한 [이](AllJoynStudio.md) 블로그 게시물을 살펴보세요.</span><span class="sxs-lookup"><span data-stu-id="aeee7-117">Have a look at [this](AllJoynStudio.md) blog post on how to get started with AllJoyn on Windows.</span></span>


## <a name="developer-resources-and-tools"></a><span data-ttu-id="aeee7-118">개발자 리소스 및 도구</span><span class="sxs-lookup"><span data-stu-id="aeee7-118">Developer Resources and Tools</span></span>

<span data-ttu-id="aeee7-119">**장치 시스템 브리지**</span><span class="sxs-lookup"><span data-stu-id="aeee7-119">**Device System Bridge**</span></span>

<span data-ttu-id="aeee7-120">AllJoyn [장치 시스템 브리지](AllJoynDSB.md) 를 사용 하면 비 alljoyn 장치에서 alljoyn를 공용 언어로 사용 하 여 alljoyn 에코 시스템과 상호 작용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aeee7-120">AllJoyn [Device System Bridge](AllJoynDSB.md) enables non-AllJoyn devices to interact with the AllJoyn ecosystem using AllJoyn as their common language.</span></span>

<span data-ttu-id="aeee7-121">기능:</span><span class="sxs-lookup"><span data-stu-id="aeee7-121">Features:</span></span>
* <span data-ttu-id="aeee7-122">어댑터에서 노출 하는 각 비 AllJoyn 장치에 대 한 가상 장치를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="aeee7-122">Creates virtual devices for each non-AllJoyn device exposed by Adapter</span></span>
* <span data-ttu-id="aeee7-123">어댑터 장치에서 자동화 된 런타임 인터페이스 생성</span><span class="sxs-lookup"><span data-stu-id="aeee7-123">Automated runtime interface generation from Adapter device</span></span>
* <span data-ttu-id="aeee7-124">LSF, 제어판 기본 서비스를 지원 하 고 확장 가능한 서비스를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="aeee7-124">Supports LSF, Control Panel base services, extensible to add more services</span></span>
* <span data-ttu-id="aeee7-125">유니버설 앱 템플릿 (C#, C++), 데스크톱 UI 응용 프로그램 및 Windows IoT 시작 작업</span><span class="sxs-lookup"><span data-stu-id="aeee7-125">Universal app templates (C#, C++), for Desktop UI applications and Windows IoT startup tasks</span></span>
* <span data-ttu-id="aeee7-126">오픈 소스로 사용 가능</span><span class="sxs-lookup"><span data-stu-id="aeee7-126">Available as open source</span></span>

<span data-ttu-id="aeee7-127">자세한 내용은 [장치 시스템 브리지 페이지](AllJoynDSB.md)에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aeee7-127">More details can be found on the [Device System Bridge page](AllJoynDSB.md).</span></span>


<span data-ttu-id="aeee7-128">**AllJoyn Studio**</span><span class="sxs-lookup"><span data-stu-id="aeee7-128">**AllJoyn Studio**</span></span>

<span data-ttu-id="aeee7-129">[Alljoyn 스튜디오](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286) 는 자동화 된 프로젝트 관리 및 미리 만들어진 응용 프로그램 템플릿과 코드 생성 및 WinRT API를 결합 하 여 alljoyn® 개발을 가속화 하는 Microsoft에서 개발 된 Visual Studio의 확장입니다.</span><span class="sxs-lookup"><span data-stu-id="aeee7-129">[AllJoyn Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286) is an extension to Visual Studio developed by Microsoft that accelerates AllJoyn® development by combining code generation and the WinRT API with automated project management and ready-made application templates.</span></span> <span data-ttu-id="aeee7-130">개발자는 이러한 기능을 통해 설정 및 구성을 하지 않고도 AllJoyn의 기능을 활용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aeee7-130">It allows developers to benefit from the power of AllJoyn without the hassle of set-up and configuration.</span></span>

<span data-ttu-id="aeee7-131">기능:</span><span class="sxs-lookup"><span data-stu-id="aeee7-131">Features:</span></span>
* <span data-ttu-id="aeee7-132">유니버설 앱 템플릿 (C#, JavaScript, C++Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aeee7-132">Universal app templates (C#, JavaScript, C++, Visual Basic)</span></span>
* <span data-ttu-id="aeee7-133">자동화 된 참조 관리 및 프로젝트 구성</span><span class="sxs-lookup"><span data-stu-id="aeee7-133">Automated reference management and project configuration</span></span>
* <span data-ttu-id="aeee7-134">솔루션에 대 한 인터페이스 추가/제거</span><span class="sxs-lookup"><span data-stu-id="aeee7-134">Adding/removing interfaces to/from a solution</span></span>
* <span data-ttu-id="aeee7-135">AllJoyn® 메뉴를 통해 프로젝트 관리에 쉽게 액세스</span><span class="sxs-lookup"><span data-stu-id="aeee7-135">Easy access to project management via the AllJoyn® menu</span></span>
* <span data-ttu-id="aeee7-136">검사 XML 파일에서 인터페이스를 로드 하는 중</span><span class="sxs-lookup"><span data-stu-id="aeee7-136">Loading interfaces from introspection XML file(s)</span></span>
* <span data-ttu-id="aeee7-137">D 1의 생산자에서 인터페이스를 검색 하는 중</span><span class="sxs-lookup"><span data-stu-id="aeee7-137">Discovering interfaces from producer(s) on the network1</span></span>

<span data-ttu-id="aeee7-138">Visual Studio Tools > 확장 및 업데이트를 통해 AllJoyn Studio를 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aeee7-138">AllJoyn Studio can be installed through Visual Studio Tools -> Extensions and Updates …</span></span> <span data-ttu-id="aeee7-139">-> 온라인-"검색" 필드 형식 "AllJoyn"의 ></span><span class="sxs-lookup"><span data-stu-id="aeee7-139">-> Online -> In the "Search" field type "AllJoyn"</span></span>

<span data-ttu-id="aeee7-140">AllJoyn Studio를 사용 하는 방법에 대 한 자세한 내용은 [여기](AllJoynStudio.md)에서 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="aeee7-140">More detail about how to use AllJoyn Studio are available [here](AllJoynStudio.md).</span></span>

<span data-ttu-id="aeee7-141">**AllJoyn 용 IoT Explorer (AllJoyn 탐색기)**</span><span class="sxs-lookup"><span data-stu-id="aeee7-141">**IoT Explorer for AllJoyn (AllJoyn Explorer)**</span></span>

<span data-ttu-id="aeee7-142">AllJoyn 용 IoT 탐색기 (이전에는 AllJoyn 탐색기)는 로컬 근접 네트워크에서 AllJoyn 장치와 상호 작용 하기 위한 Windows 유니버설 응용 프로그램입니다.</span><span class="sxs-lookup"><span data-stu-id="aeee7-142">The IoT Explorer for AllJoyn (previously known as AllJoyn Explorer) is a Windows Universal Application for interacting with AllJoyn devices on the local proximity network.</span></span> <span data-ttu-id="aeee7-143">개발자는 사용 가능한 모든 AllJoyn 장치를 나열 하 고, 인터페이스 및 개체 구조를 검사 하 고, 신호를 수신 하 고, 속성을 설정 및 가져오고, 메서드를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aeee7-143">Developers can list all available AllJoyn devices, inspect their interface and object structure, as well as receive signals, set and get properties, and call methods.</span></span>

* <span data-ttu-id="aeee7-144">[AllJoyn 스토어 앱 용 IoT 탐색기](https://www.microsoft.com/store/apps/9nblggh6gpxl): 이는 공식 스토어 앱 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="aeee7-144">[IoT Explorer for AllJoyn Store App](https://www.microsoft.com/store/apps/9nblggh6gpxl): This is the official store app location.</span></span>
* <span data-ttu-id="aeee7-145">[AllJoyn 탐색기 1.0.1.11 (이전 릴리스)](https://github.com/ms-iot/samples/releases/download/AllJoynExplorer_1.0.11/AllJoynExplorer_1.0.1.11.zip): 이 zip에는 개발자 컴퓨터에 테스트용으로 로드 될 AllJoyn 탐색기 AppX 번들이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aeee7-145">[AllJoyn Explorer 1.0.1.11 (previous release)](https://github.com/ms-iot/samples/releases/download/AllJoynExplorer_1.0.11/AllJoynExplorer_1.0.1.11.zip): This zip contains the AllJoyn Explorer AppX bundle to be side-loaded on a developer machine.</span></span> <span data-ttu-id="aeee7-146">이는 이전에 릴리스된 버전의 AllJoyn 응용 프로그램용 IoT 탐색기입니다.</span><span class="sxs-lookup"><span data-stu-id="aeee7-146">This is a previously released version of the IoT Explorer for AllJoyn application.</span></span>
* <span data-ttu-id="aeee7-147">[AllJoyn 탐색기 설치 가이드](https://github.com/ms-iot/samples/releases/download/AllJoynExplorer_1.0.11/AllJoyn_Explorer_Setup_Guide_v1.0.pdf): 이 pdf에는 AllJoyn 탐색기를 배포 하는 방법에 대 한 설명서가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aeee7-147">[AllJoyn Explorer Setup Guide](https://github.com/ms-iot/samples/releases/download/AllJoynExplorer_1.0.11/AllJoyn_Explorer_Setup_Guide_v1.0.pdf): This pdf contains the documentation for how to deploy the AllJoyn Explorer.</span></span>
* <span data-ttu-id="aeee7-148">[AllJoyn 탐색기 사용자 가이드](https://github.com/ms-iot/samples/releases/download/AllJoynExplorer_1.0.11/AllJoyn_Explorer_User_Guide_v1.0.pdf): 이 pdf에는 AllJoyn 탐색기를 사용 하는 방법에 대 한 설명서가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aeee7-148">[AllJoyn Explorer User Guide](https://github.com/ms-iot/samples/releases/download/AllJoynExplorer_1.0.11/AllJoyn_Explorer_User_Guide_v1.0.pdf): This pdf contains the documentation for how to use the AllJoyn Explorer.</span></span>


### <a name="additional-resources"></a><span data-ttu-id="aeee7-149">추가 리소스</span><span class="sxs-lookup"><span data-stu-id="aeee7-149">Additional Resources</span></span>

* [<span data-ttu-id="aeee7-150">AllJoyn Studio 확장 사용</span><span class="sxs-lookup"><span data-stu-id="aeee7-150">Using the AllJoyn Studio extension</span></span>](AllJoynStudio.md)
* [<span data-ttu-id="aeee7-151">AllJoyn 생산자 및 Authoring 검사</span><span class="sxs-lookup"><span data-stu-id="aeee7-151">AllJoyn Producer and Authoring AllJoyn Introspection</span></span>](AllJoynProducer.md)
* [<span data-ttu-id="aeee7-152">Windows 10을 사용 하 여 AllJoyn 문제 해결</span><span class="sxs-lookup"><span data-stu-id="aeee7-152">Troubleshooting AllJoyn with Windows 10</span></span>](AllJoynTroubleshooting.md)

<span data-ttu-id="aeee7-153">**비디오**</span><span class="sxs-lookup"><span data-stu-id="aeee7-153">**Videos**</span></span>

* [<span data-ttu-id="aeee7-154">빌드 2015 AllJoyn 기술 세션</span><span class="sxs-lookup"><span data-stu-id="aeee7-154">//build 2015 AllJoyn Technical Session</span></span>](https://channel9.msdn.com/Events/Build/2015/2-623)
* [<span data-ttu-id="aeee7-155">WinHEC 2015 AllJoyn 기술 세션</span><span class="sxs-lookup"><span data-stu-id="aeee7-155">WinHEC 2015 AllJoyn Technical Session</span></span>](https://channel9.msdn.com/Events/WinHEC/2015/IOT200)

<span data-ttu-id="aeee7-156">**샘플**</span><span class="sxs-lookup"><span data-stu-id="aeee7-156">**Samples**</span></span>

* [<span data-ttu-id="aeee7-157">AllJoyn 생산자</span><span class="sxs-lookup"><span data-stu-id="aeee7-157">AllJoyn Producers</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AllJoyn/ProducerExperiences)
* [<span data-ttu-id="aeee7-158">AllJoyn 소비자</span><span class="sxs-lookup"><span data-stu-id="aeee7-158">AllJoyn Consumers</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AllJoyn/ConsumerExperiences)
* [<span data-ttu-id="aeee7-159">AllJoyn UWP 샘플 (MSDN)</span><span class="sxs-lookup"><span data-stu-id="aeee7-159">AllJoyn UWP Samples (MSDN)</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AllJoyn/ConsumerExperiences)

<span data-ttu-id="aeee7-160">**참조**</span><span class="sxs-lookup"><span data-stu-id="aeee7-160">**Reference**</span></span>

* [<span data-ttu-id="aeee7-161">Windows 10의 AllJoyn Api (MSDN)</span><span class="sxs-lookup"><span data-stu-id="aeee7-161">AllJoyn APIs in Windows 10 (MSDN)</span></span>](https://msdn.microsoft.com/library/windows/apps/xaml/windows.devices.alljoyn.aspx)
* [<span data-ttu-id="aeee7-162">AllJoyn 아키텍처 세부 정보 (Allseen 동맹)</span><span class="sxs-lookup"><span data-stu-id="aeee7-162">AllJoyn Architecture Details (Allseen Alliance)</span></span>](https://allseenalliance.org/developers/learn/)
* [<span data-ttu-id="aeee7-163">AllJoyn 개발자 리소스 (Allseen 동맹)</span><span class="sxs-lookup"><span data-stu-id="aeee7-163">AllJoyn Developer Resources (Allseen Alliance)</span></span>](https://allseenalliance.org/developers/develop/)
* [<span data-ttu-id="aeee7-164">AllJoyn C API 참조 수동 (Allseen 동맹)</span><span class="sxs-lookup"><span data-stu-id="aeee7-164">AllJoyn C API Reference Manual (Allseen Alliance)</span></span>](https://allseenalliance.org/docs/api/c/index.html)

