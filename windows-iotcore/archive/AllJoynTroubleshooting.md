---
title: AllJoyn 문제 해결
author: saraclay
ms.author: saclayt
ms.date: 09/07/17
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: 알려진 문제 및 문제 해결 설정에 대해이 포괄적인 가이드를 사용 하 여 AllJoyn 기술 문제를 해결 하는 방법을 알아봅니다.
keywords: windows iot, AllJoyn
ms.openlocfilehash: 8b93242c8f583199ee5890c6d0d15985f9025175
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "60169971"
---
> [!NOTE]
> <span data-ttu-id="db4be-104">보관 된 설명서를 보고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db4be-104">You are viewing archived documentation.</span></span> <span data-ttu-id="db4be-105">AllJoyn는 Windows 10 IoT에서 더 이상 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="db4be-105">AllJoyn is no longer supported by Windows 10 IoT.</span></span> <span data-ttu-id="db4be-106">질문이 있는 경우 GitHub에서 문제를 열거나 아래 설명에 의견을 남겨 주세요.</span><span class="sxs-lookup"><span data-stu-id="db4be-106">For questions, please open an issue on GitHub or leave us feedback in the comments below.</span></span>

# <a name="alljoyn-troubleshooting"></a><span data-ttu-id="db4be-107">AllJoyn 문제 해결</span><span class="sxs-lookup"><span data-stu-id="db4be-107">AllJoyn Troubleshooting</span></span>

<span data-ttu-id="db4be-108">[AllJoyn](https://allseenalliance.org/developers/learn) 는 IoT 장치와 응용 프로그램이 서로를 검색 하 고 상호 작용할 수 있도록 하는 기술입니다.</span><span class="sxs-lookup"><span data-stu-id="db4be-108">[AllJoyn](https://allseenalliance.org/developers/learn) is a technology that enables IoT devices and applications to discover and interact with each other.</span></span> <span data-ttu-id="db4be-109">AllJoyn는 Windows 10 및 Windows 10 SDK에 기본 제공 되므로 유니버설 Windows 플랫폼 (UWP)를 사용 하 여 AllJoyn을 쉽게 활용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db4be-109">Since AllJoyn is built into Windows 10 and the Windows 10 SDK, it's easy to take advantage of AllJoyn using the Universal Windows Platform (UWP).</span></span>

![AJ_Troubleshooting_intro](../media/AllJoyn/AJ_Troubleshooting_intro.jpg)

<span data-ttu-id="db4be-111">이 블로그 게시물은 AllJoyn 네트워크 및 장치를 구성 하는 데 도움이 되며, 예상 대로 작동 하지 않는 경우 따라야 하는 문제 해결 단계도 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="db4be-111">This blog post will help you configure your AllJoyn network and devices, and also provide troubleshooting steps to follow when things don't work as expected.</span></span> <span data-ttu-id="db4be-112">이 문서의 주요 초점은 UWP AllJoyn 클라이언트 앱 (AllJoyn 소비자) 및 AllJoyn 장치 (AllJoyn 생산자) 간의 통신을 사용 하도록 설정 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="db4be-112">The primary focus of this article will be enabling communication between UWP AllJoyn client apps (AllJoyn consumers) and AllJoyn devices (AllJoyn producers).</span></span> <span data-ttu-id="db4be-113">UWP AllJoyn 생산자 앱과의 통신을 사용 하도록 설정 하는 데는 동일한 구성 단계가 많이 필요 하지만 이후 블로그 게시물 및 문서에 대 한 자세한 정보는 남아 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db4be-113">Many of the same configuration steps are required to enable communication with UWP AllJoyn Producer apps, but further details will be left to future blog posts and articles.</span></span>

### <a name="app-development-checklist"></a><span data-ttu-id="db4be-114">앱 개발 검사 목록</span><span class="sxs-lookup"><span data-stu-id="db4be-114">App Development Checklist</span></span>

<span data-ttu-id="db4be-115">Windows 10 용 UWP 앱을 작성 하는 경우 다음을 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="db4be-115">If you are writing UWP apps for Windows 10, you should make sure that:</span></span>

1. <span data-ttu-id="db4be-116">앱의 매니페스트에서 ' allJoyn ' 기능을 선언 했습니다 (참고 대/소문자 구분).</span><span class="sxs-lookup"><span data-stu-id="db4be-116">You've declared the 'allJoyn' capability in your app's manifest (note casing).</span></span>
2. <span data-ttu-id="db4be-117">대상으로 지정할 특정 아키텍처를 선택 했습니다.</span><span class="sxs-lookup"><span data-stu-id="db4be-117">You've selected the specific architecture that you'll be targeting.</span></span> <span data-ttu-id="db4be-118">(일부 경우에는 ' Any CPU '를 사용 하 여 Windows 런타임 구성 요소를 빌드할 수 없습니다. 몇 가지 Visual Studio 2017 빌드의 알려진 문제).</span><span class="sxs-lookup"><span data-stu-id="db4be-118">(Required in some cases because Windows Runtime Components cannot be built using 'Any CPU', a known issue with some Visual Studio 2017 builds).</span></span>

<span data-ttu-id="db4be-119">Windows 10 용 UWP 기반 응용 프로그램이 아닌 앱 또는 장치 소프트웨어를 작성 하는 경우 Windows 10의 AllJoyn과의 호환성을 위해 다음 검사 목록을 검토 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="db4be-119">If you are writing an app or device software that is not a UWP-based application for Windows 10, you should review the following checklist to ensure compatibility with AllJoyn in Windows 10:</span></span>

1. <span data-ttu-id="db4be-120">생산자를 구현 하는 경우 정보 인터페이스 및 정보 기반 광고/검색이 사용 되 고 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="db4be-120">If implementing a Producer, ensure that the About interface and About-based advertisement/discovery are being used.</span></span> <span data-ttu-id="db4be-121">About 인터페이스는 [AllSeen 된 동맹 웹 사이트에 설명](https://allseenalliance.org/developers/learn/core/about-announcement/interface)되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db4be-121">The About interface is [documented at the AllSeen Alliance website](https://allseenalliance.org/developers/learn/core/about-announcement/interface).</span></span>
2. <span data-ttu-id="db4be-122">최상의 결과를 위해 AllSeen 동맹 웹 사이트의 [다운로드 섹션](https://allseenalliance.org/developers/download) 에서 사용할 수 있는 15.04 AllJoyn 코드 베이스를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="db4be-122">For best results, use the 15.04 AllJoyn code base, available in the [downloads section](https://allseenalliance.org/developers/download) of the AllSeen Alliance website.</span></span>

### <a name="network-setup-and-troubleshooting"></a><span data-ttu-id="db4be-123">네트워크 설정 및 문제 해결</span><span class="sxs-lookup"><span data-stu-id="db4be-123">Network Setup and Troubleshooting</span></span>

<span data-ttu-id="db4be-124">AllJoyn 장치가 서로를 검색 하 고 상호 작용할 수 있도록 하려면 각 장치의 네트워크 구성 및 설정이 다음을 충족 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="db4be-124">For AllJoyn devices to be able to discover and interact with each other, the network configuration and settings for each device must satisfy the following:</span></span>

1. <span data-ttu-id="db4be-125">모든 AllJoyn 장치는 동일한 네트워크에 연결 되며 동일한 서브넷에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db4be-125">All AllJoyn devices are connected to the same network, and are on the same subnet.</span></span>
2. <span data-ttu-id="db4be-126">Windows 10 PC: "장치 및 콘텐츠 찾기"는 AllJoyn에서 사용 중인 네트워크에 대해 사용 하도록 설정 됩니다 (Phone에는 적용 되지 않음).</span><span class="sxs-lookup"><span data-stu-id="db4be-126">Windows 10 PC: "Find devices and content" is enabled for the network in use with AllJoyn (does not apply for Phone).</span></span>

<span data-ttu-id="db4be-127">PC에서는 CMD 또는 PowerShell 창의 추적 경로 명령을 사용 하 여 다른 컴퓨터/장치가 다음과 같은 서브넷에 있는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db4be-127">On a PC you can use the trace route command from a CMD or PowerShell window to check if another machine/device is on the same subnet as follows:</span></span>

    PS C:\Users\user> tracert WIN10PC1
     
    Tracing route to WIN10PC1 [fe80::657d:d8bf:176f:d0b2%24]
     
    over a maximum of 30 hops:
     
    1       1 ms     1 ms     1 ms   WIN10PC1 [fe80::657d:d8bf:176f:d0b2]
     
    Trace complete.

<span data-ttu-id="db4be-128">여기에 표시 되는 첫 번째 숫자는 홉 수입니다 .이 값은 "1" 이므로 두 컴퓨터가 동일한 서브넷에 있음을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="db4be-128">The first number output here is the number of hops, and since that value is "1" it means that both machines are on the same subnet.</span></span>

<span data-ttu-id="db4be-129">다음은 일반적인 AllJoyn 네트워크 설정의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="db4be-129">Below is an example of a typical AllJoyn network setup.</span></span> <span data-ttu-id="db4be-130">이 예제에서 표시 되는 모든 장치는 동일한 서브넷에 있다고 가정 하 여 각 장치를 검색 하 고 서로 상호 작용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db4be-130">In this example, all of the devices shown would be able to discover and interact with each other using AllJoyn assuming they were on the same subnet.</span></span>

![AJ_Troubleshooting_Devices](../media/AllJoyn/AJ_Troubleshooting_Devices.jpg)

<span data-ttu-id="db4be-132">Windows 10 PC를 AllJoyn 장치를 사용 하 여 네트워크에 연결 하는 경우 네트워크의 장치 및 Pc 찾기와 관련 된 대화 상자가 표시 되 면 "예"를 클릭 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="db4be-132">When you connect your Windows 10 PC to the network with AllJoyn devices, you'll need to click "Yes" if a dialog is displayed regarding finding devices and PCs on the network.</span></span> <span data-ttu-id="db4be-133">두고 이러한 대화 상자는 나타나지 않으므로 Windows 10 Phone에서 네트워크를 연결 하는 경우에는 적용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="db4be-133">(Note: This does not apply when joining networks from Windows 10 Phone as there is no such dialog).</span></span>

<span data-ttu-id="db4be-134">다음과 같이 Wi-fi 설정의 "고급 설정" 페이지에서이 설정을 관리할 수도 있습니다 .이 페이지는 사용 중인 Windows 10 참가자 빌드에 따라 약간 다르게 보일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db4be-134">You can also manage this setting in the "Advanced Settings" page in Wi-Fi settings as shown here: (this page may look slightly different depending on which Windows 10 Insider build you are using)</span></span>

![AJ_Troubleshooting_Settings](../media/AllJoyn/AJ_Troubleshooting_Settings.jpg)

<span data-ttu-id="db4be-136">"장치 찾기 및 내용"에 대 한 토글은 AllJoyn 기능을 사용 하기 위해 "On" 위치에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="db4be-136">The toggle for "Find devices and content" should be in the "On" position in order to enable AllJoyn functionality.</span></span>

<span data-ttu-id="db4be-137">기존 네트워크 연결의 경우 "Get NetConnectionProfile" Powershell cmdlet을 실행 하 여이 옵션이 올바르게 구성 되었는지 쉽게 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db4be-137">For existing network connections, you can easily validate whether this option is configured properly by running the "Get-NetConnectionProfile" Powershell cmdlet .</span></span> <span data-ttu-id="db4be-138">이는 Windows 10 Phone에는 적용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="db4be-138">(Note that this does not apply for Windows 10 Phone).</span></span>

<span data-ttu-id="db4be-139">예제 Get NetConnectionProfile 출력:</span><span class="sxs-lookup"><span data-stu-id="db4be-139">Example Get-NetConnectionProfile output:</span></span>

    PS C:\Users\user> Get-NetConnectionProfile
     
    Name             : myWirelessNetwork
    InterfaceAlias   : vEthernet (Intel(R) Dual Band Wireless-AC 7260 Virtual Switch)
    InterfaceIndex   : 24
    NetworkCategory : Private
    IPv4Connectivity : Internet
    IPv6Connectivity : LocalNetwork


<span data-ttu-id="db4be-140">"NetworkCategory" 값이 "Private" (위와 같이) 인 경우,이는 AllJoyn에 대 한 네트워크 연결을 올바르게 구성 했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="db4be-140">If the "NetworkCategory" value is "Private" (as shown above), this indicates that you have a properly configured your network connection for AllJoyn.</span></span>

### <a name="about-advertisement-and-troubleshooting-discovery-with-getajxmlexe"></a><span data-ttu-id="db4be-141">Getajxml를 사용 하 여 보급 알림 및 문제 해결 정보</span><span class="sxs-lookup"><span data-stu-id="db4be-141">About Advertisement and Troubleshooting Discovery with Getajxml.exe</span></span>

<span data-ttu-id="db4be-142">Windows 10 UWP AllJoyn 앱에서 AllJoyn 생산자 장치나 앱을 검색할 수 있도록 하려면 정보 기반 검색을 적절 하 게 구현 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="db4be-142">For AllJoyn producer devices or apps to be discoverable by Windows 10 UWP AllJoyn apps, About-based discovery must be properly implemented.</span></span> <span data-ttu-id="db4be-143">GetAjXml 도구를 사용 하 여 쉽게 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db4be-143">This can be easily verified with the GetAjXml.exe tool.</span></span> <span data-ttu-id="db4be-144">GetAjXml와 관련 된 다운로드 및 사용 정보를 찾으려면 [AllJoyn Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286)를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="db4be-144">To find download and usage information related to GetAjXml.exe, check out [AllJoyn Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286).</span></span>

<span data-ttu-id="db4be-145">다음은 정보 기반 검색을 지 원하는 예제 장치에 대 한 GetAjXml 출력을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="db4be-145">The following shows GetAjXml.exe output for an example device that supports About-based discovery:</span></span>

    ----------------------------------------------------------------------
    Discovery   : About Announcement
    Manufacturer: Microsoft
    Model #     : 070773
    Device Name : Raspberry Pi Toaster
    Device ID   : 41d9a124-6913-40c5-a20a-9d1b20f8121b
    App Name   : Toaster Producer
          Bus Name                       Port Object Path
          ============================== ===== ===============================
          :3yZG_wu1.2                       25 /emergency
          :3yZG_wu1.2                       25 /info
          :3yZG_wu1.2                       25 /notificationDismisser
          :3yZG_wu1.2                       25 /notificationProducer
          :3yZG_wu1.2                       25 /toaster
          :3yZG_wu1.2                       25 /warning


<span data-ttu-id="db4be-146">위의 예제 `Discovery   : About Announcement` 에서가이 출력에 포함 되었으므로이 alljoyn 생산자는 Windows 10 AllJoyn UWP 앱에서 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db4be-146">In the above example, since `Discovery   : About Announcement` was included in this output, this AllJoyn producer will be discoverable by Windows 10 AllJoyn UWP apps.</span></span> <span data-ttu-id="db4be-147">특정 AllJoyn 생산자에 대해이 출력이 표시 되지 않으면 장치 (생산자) 측의 검색 구현을 조사 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="db4be-147">If you don't see this output for a particular AllJoyn producer, you will need to investigate the discovery implementation on the device (Producer) side.</span></span>

### <a name="advanced-troubleshooting-with-etw-log-output"></a><span data-ttu-id="db4be-148">ETW 로그 출력을 사용한 고급 문제 해결</span><span class="sxs-lookup"><span data-stu-id="db4be-148">Advanced Troubleshooting with ETW Log Output</span></span>

<span data-ttu-id="db4be-149">ETW (ETW(Windows용 이벤트 추적))는 Windows의 다양 한 기능에 대 한 고급 디버깅 정보를 얻는 데 도움이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db4be-149">Event Tracing for Windows (ETW) can help you get advanced debugging information for many different features in Windows.</span></span> <span data-ttu-id="db4be-150">다행히 AllJoyn는 ETW 로깅을 지 원하는 기능 중 하나 이므로이 섹션에서는 AllJoyn에 대해 ETW 로깅을 사용 하도록 설정 하는 방법과 로그에 액세스 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="db4be-150">Fortunately AllJoyn is one of the features with ETW logging support, so in this section I'll show you how to enable ETW logging for AllJoyn, and how to access logs.</span></span>

1. <span data-ttu-id="db4be-151">시작 메뉴 검색 텍스트 상자에 "이벤트 로그"를 입력 하 여 이벤트 뷰어를 시작 하 고 "이벤트 로그 보기"를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="db4be-151">Launch the Event Viewer by typing "Event Logs" into the Start Menu search textbox, select "View Event Logs".</span></span>
2. <span data-ttu-id="db4be-152">"보기" 메뉴에서 "분석 및 디버그 로그 표시"가 선택 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="db4be-152">In the "View" menu, ensure that "Show Analytic and Debug Logs" is checked.</span></span>
3. <span data-ttu-id="db4be-153">왼쪽 탐색 영역에서 "응용 프로그램 및 서비스 로그 > Microsoft > Windows > AllJoyn"로 이동 하 여 디버그 채널과 작동 채널을 모두 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="db4be-153">Navigate the tree view in the left navigation to "Applications and Services Logs > Microsoft > Windows > AllJoyn" in the folder view, and enable both the Debug channel and the Operational channel.</span></span> <span data-ttu-id="db4be-154">아래 스크린샷에서 빨간색 상자를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="db4be-154">(see red box in screenshot below).</span></span>
4. <span data-ttu-id="db4be-155">AllJoyn에서 발생 하는 문제를 재현 합니다.</span><span class="sxs-lookup"><span data-stu-id="db4be-155">Reproduce the problem that you are experiencing with AllJoyn.</span></span>
5. <span data-ttu-id="db4be-156">오른쪽 "작업" 표시줄에서 "새로 고침"을 클릭 한 다음 "AllJoyn" 폴더 아래의 왼쪽 탐색 모음에서 작동 및 디버그 채널을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="db4be-156">Click on "Refresh" in the right "Actions" bar, then check the Operational and Debug channels from the left navigation bar under the "AllJoyn" folder.</span></span>

![AJ_Troubleshooting_ETW](../media/AllJoyn/AJ_Troubleshooting_ETW.jpg)

<span data-ttu-id="db4be-158">AllJoyn ETW 추적은 다음과 같이 분할 됩니다.</span><span class="sxs-lookup"><span data-stu-id="db4be-158">AllJoyn ETW traces are partitioned as follows:</span></span>

- <span data-ttu-id="db4be-159">디버그 채널: 자세한 정보 표시, 오류 없음/정보 추적</span><span class="sxs-lookup"><span data-stu-id="db4be-159">Debug channel: Verbose, non-error/informational traces</span></span>
- <span data-ttu-id="db4be-160">작동 채널: 오류 추적, 오류는 작동 채널에만 출력 됩니다.</span><span class="sxs-lookup"><span data-stu-id="db4be-160">Operational channel: Error traces, errors are only output on the operational channel</span></span>

<span data-ttu-id="db4be-161">ETW 항목에서 정보를 추출 하려면 지정 된 채널에 대 한 목록 보기에서 항목을 마우스 오른쪽 단추로 클릭 한 다음 "복사"를 선택 하 고 "세부 정보를 텍스트로 복사"를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="db4be-161">In order to extract information from ETW entries, you can right-click on an entry in the list view for a given channel, and then select "Copy" and then "Copy Details as Text".</span></span> <span data-ttu-id="db4be-162">그런 다음 텍스트 편집기에 해당 텍스트를 붙여넣으면 아래 예제와 같이 정보를 얻게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="db4be-162">If you then paste the corresponding text into a text editor, you'll have detail like the example below:</span></span>


    Log Name:       Microsoft-Windows-AllJoyn/Operational
    Source:         Microsoft-Windows-AllJoyn
    Date:           6/1/2015 3:57:45 PM
    Event ID:     2
    Task Category: AJ
    Level:         Error
    Keywords:      (70368744177664),AJ
    User:         LOCAL SERVICE
    Computer:       <computer name>
     
    Description:
    AllJoyn encountered an error 0x902D in module UDP, file ..\udptransport.cc, at line number 10809. See the event user data for more information.
    Event Xml:
    <Event xmlns="http://schemas.microsoft.com/win/2004/08/events/event">
    <System>
       <Provider Name="Microsoft-Windows-AllJoyn" Guid="{2ED299D2-2F6B-411D-8D15-F4CC6FDE0C70}" />
        <EventID>2</EventID>
        <Version>0</Version>
        <Level>2</Level>
        <Task>1</Task>
        <Opcode>10</Opcode>
        <Keywords>0x8000400000000001</Keywords>
       <TimeCreated SystemTime="2015-06-01T22:57:45.626729500Z" />
        <EventRecordID>16</EventRecordID>
       <Correlation />
       <Execution ProcessID="1392" ThreadID="5768" />
       <Channel>Microsoft-Windows-AllJoyn/Operational</Channel>
        <Computer>computer name</Computer>
       <Security UserID="SID" />
    </System>
    <UserData>
       <AJErrorData xmlns="http://manifests.microsoft.com/win/2005/08/windows/alljoyn/events">
           <QStatus>0x902d</QStatus>
           <Message>UDPTransport::DisbleDiscovery(): Not running or stopping; exiting</Message>
           <Module>UDP</Module>
           <File>..\udptransport.cc</File>
           <Line>10809</Line>
        </AJErrorData>
    </UserData>
    </Event>


<span data-ttu-id="db4be-163">이 정보는 Microsoft 또는 다른 파트너에 게 문제를 보고할 때 정보를 제공 하거나 AllJoyn 문제를 추적 하는 데 도움이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db4be-163">This information can help track down AllJoyn issues, or assist in providing detail when reporting issues to Microsoft or other partners.</span></span> <span data-ttu-id="db4be-164">[ETW 추적 및 MSDN의 이벤트 뷰어](https://msdn.microsoft.com/library/windows/desktop/bb968803.aspx)에 대해 자세히 알아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db4be-164">You can learn more about [ETW traces and the Event Viewer on MSDN](https://msdn.microsoft.com/library/windows/desktop/bb968803.aspx).</span></span>

### <a name="known-issues-and-limitations"></a><span data-ttu-id="db4be-165">알려진 문제 및 제한 사항</span><span class="sxs-lookup"><span data-stu-id="db4be-165">Known Issues and Limitations</span></span>

<span data-ttu-id="db4be-166">Windows 10의 AllJoyn에 대 한 디자인 별 제한 사항:</span><span class="sxs-lookup"><span data-stu-id="db4be-166">By-Design limitations for AllJoyn in Windows 10:</span></span>

- <span data-ttu-id="db4be-167">Windows 10 PC에서 실행 되는 앱이 없는 경우 alljoyn 장치 또는 네트워크의 앱에서 AllJoyn 라우터 노드가 자동으로 시작 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="db4be-167">The AllJoyn Router Node is not auto-started by AllJoyn devices or apps on the network when no apps are running on the Windows 10 PC.</span></span> <span data-ttu-id="db4be-168">"Net start ajrouter" 명령을 실행 하 여 관리자 권한 명령 프롬프트 또는 Powershell 세션에서 Windows 10 라우터 노드를 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db4be-168">The Windows 10 Router Node can be started from an elevated command prompt or Powershell session by running the command "net start ajrouter".</span></span>
- <span data-ttu-id="db4be-169">AllJoyn UWP 앱은 동일한 컴퓨터에서 실행 되는 다른 AllJoyn UWP 앱 또는 AllJoyn 데스크톱 앱을 검색 하거나 조작할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="db4be-169">AllJoyn UWP apps can't discover or interact with other AllJoyn UWP apps or AllJoyn desktop apps running on the same machine.</span></span> <span data-ttu-id="db4be-170">이는 UWP 앱 용 Windows 10에서 구현 된 앱 격리 약속의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="db4be-170">This is a part of the app isolation promise that is implemented in Windows 10 for UWP apps.</span></span> 
  - <span data-ttu-id="db4be-171">Visual Studio에서 AllJoyn UWP 앱을 배포 하는 경우 해당 앱에 대해 앱 격리 앱 격리가 무시 됩니다 ("루프백 예외" 라고 함).</span><span class="sxs-lookup"><span data-stu-id="db4be-171">If you deploy an AllJoyn UWP app from Visual Studio, app isolation app isolation is bypassed for that app (this is called a "loopback exemption ").</span></span> <span data-ttu-id="db4be-172">Visual Studio에서 배포 된 각 UWP 앱은 이러한 앱이 정보 기반 보급 알림/검색을 사용 하는 한 다른 루프백 제외 UWP 앱 및 데스크톱 앱을 검색 하 고 상호 작용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db4be-172">Each UWP app that is deployed from Visual Studio will be able to discover and interact with other loopback-exempt UWP apps and desktop apps as long as those apps use About-based advertisement/discovery.</span></span> <span data-ttu-id="db4be-173">"포함 모드"에서 Windows 10 IoT Core를 실행 하는 경우이 루프백 예외가 자동으로 적용 되 고 구성 해야 하는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="db4be-173">If you are running Windows 10 IoT Core in "Embedded Mode", this loopback exception is automatically applied, it's not something that you need to configure.</span></span> <span data-ttu-id="db4be-174">[MSDN의](https://msdn.microsoft.com/library/windows/apps/Hh780593.aspx)루프백 예외에 대해 자세히 알아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db4be-174">You can read more about loopback exceptions [on MSDN](https://msdn.microsoft.com/library/windows/apps/Hh780593.aspx).</span></span>

