---
title: AllJoyn Studio
author: saraclay
ms.author: saclayt
ms.date: 09/07/17
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: 유니버설 Windows 플랫폼 (UWP) AllJoyn Api 및 Visual Studio 2017을 사용 하 여 AllJoyn UWP 앱을 만드는 방법에 알아봅니다.
keywords: windows iot, AllJoyn
ms.openlocfilehash: 5326873218c0126b918679308e3a8e08cdddf84c
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513725"
---
> [!NOTE]
> <span data-ttu-id="689f4-104">보관 된 설명서가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="689f4-104">You are viewing archived documentation.</span></span> <span data-ttu-id="689f4-105">Windows 10 IoT에서 더 이상 AllJoyn 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="689f4-105">AllJoyn is no longer supported by Windows 10 IoT.</span></span> <span data-ttu-id="689f4-106">질문에 대 한 GitHub에서 문제를 제기 하거나 아래 설명에 의견을 남길 하세요.</span><span class="sxs-lookup"><span data-stu-id="689f4-106">For questions, please open an issue on GitHub or leave us feedback in the comments below.</span></span>

# <a name="using-the-alljoyn-studio-extension"></a><span data-ttu-id="689f4-107">AllJoyn Studio 확장을 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="689f4-107">Using the AllJoyn Studio Extension</span></span>

<span data-ttu-id="689f4-108">합니다 [AllSeen Alliance](https://allseenalliance.org/) AllJoyn Internet of Things 부서를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="689f4-108">The [AllSeen Alliance](https://allseenalliance.org/) created AllJoyn to empower the Internet of Things.</span></span> <span data-ttu-id="689f4-109">Windows 10 개발자가 쉽게 활용 하도록 AllJoyn "IoT-enable" Windows 10 앱에는 플랫폼에 기본적으로 내장 AllJoyn에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="689f4-109">Windows 10 has AllJoyn built natively into its platform, allowing developers to easily take advantage of AllJoyn to "IoT-enable" your Windows 10 apps.</span></span> <span data-ttu-id="689f4-110">이 문서는 Visual Studio 2017 및 유니버설 Windows 플랫폼 (UWP) AllJoyn Api를 사용 하 여 Windows 10 용 앱을 빌드하는 데 필요한 단계를 간략하게 설명 [AllJoyn Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286) 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="689f4-110">This article will outline the steps required to build apps for Windows 10 using the Universal Windows Platform (UWP) AllJoyn APIs and the Visual Studio 2017 [AllJoyn Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286) Extension.</span></span>

## <a name="understanding-alljoyn-uwp-app-development"></a><span data-ttu-id="689f4-111">AllJoyn UWP 앱 개발을 이해</span><span class="sxs-lookup"><span data-stu-id="689f4-111">Understanding AllJoyn UWP App Development</span></span>

<span data-ttu-id="689f4-112">세 가지 주요 구성 요소 폼 AllJoyn UWP 앱:</span><span class="sxs-lookup"><span data-stu-id="689f4-112">Three major components form AllJoyn UWP apps:</span></span>

1. <span data-ttu-id="689f4-113">앱 레이아웃 및 디자인 (XAML 또는 HTML) 및 구성 요소 클래스 (C#, JavaScript C++, 또는 VB).</span><span class="sxs-lookup"><span data-stu-id="689f4-113">App layout and design (XAML or HTML) and class components (C#, JavaScript, C++, or VB).</span></span>
2. <span data-ttu-id="689f4-114">AllJoyn core Api: AllJoyn Standard Client API (C) 및 Windows.Devices.AllJoyn API (WinRT) Windows 10 SDK에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="689f4-114">The AllJoyn core APIs: AllJoyn Standard Client API (C) and Windows.Devices.AllJoyn API (WinRT)  available in the Windows 10 SDK.</span></span>
3. <span data-ttu-id="689f4-115">하나 이상의 UWP Windows 런타임 구성 요소 (의 AllJoyn 인터페이스에서이 코드 생성).</span><span class="sxs-lookup"><span data-stu-id="689f4-115">One or more UWP Windows Runtime Components (the  generates this code from AllJoyn interfaces).</span></span>

<span data-ttu-id="689f4-116">다음 다이어그램은 일반적인 AllJoyn UWP 프로젝트의 아키텍처를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="689f4-116">The following diagram shows the architecture of a typical AllJoyn UWP project:</span></span>

![AJ_UWP_Architecture](../media/AllJoyn/AJ_UWP_Architecture.jpg)

<span data-ttu-id="689f4-118">UWP 앱 AllJoyn 사용 하거나 생산자를 수 있습니다 (구현 및 인터페이스를 장치에 일반적으로 표시) (일반적으로 앱 인터페이스 사용) 소비자 또는 둘 다.</span><span class="sxs-lookup"><span data-stu-id="689f4-118">AllJoyn-enabled UWP apps can be either producers  (implement and expose interfaces, typically a device ), consumers (use interfaces, typically apps), or both.</span></span> <span data-ttu-id="689f4-119">소비자 및 생산자는 동일한 시작 단계를을 공유는 구현 세부 정보에만 다양 합니다.</span><span class="sxs-lookup"><span data-stu-id="689f4-119">Consumers and producers share the same starting steps, only diverging in the implementation details.</span></span>

## <a name="creating-an-alljoyn-enabled-uwp-app"></a><span data-ttu-id="689f4-120">UWP AllJoyn 사용 앱을 만드는 방법</span><span class="sxs-lookup"><span data-stu-id="689f4-120">Creating an AllJoyn-enabled UWP app</span></span>

<span data-ttu-id="689f4-121">Windows 10 용 UWP AllJoyn 사용 앱을 개발 하려면 다음이 단계를 수행 합니다. (이 문서의 뒷부분에 자세히 설명)</span><span class="sxs-lookup"><span data-stu-id="689f4-121">Follow these steps to develop AllJoyn-enabled UWP apps for Windows 10: (explained in detail later in this document)</span></span>

1. <span data-ttu-id="689f4-122">빌드 환경을 준비 합니다.</span><span class="sxs-lookup"><span data-stu-id="689f4-122">Prepare your build environment.</span></span>
2. <span data-ttu-id="689f4-123">인터페이스는, 및를 만들거나 가져와야 필요한 검사 XML에 있는 AllJoyn를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="689f4-123">Determine which AllJoyn interfaces will be used, and obtain or create necessary Introspection XML.</span></span>
3. <span data-ttu-id="689f4-124">AllJoyn 앱 프로젝트를 만든 다음 코드 생성에 대 한 검사 XML 및 원하는 인터페이스를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="689f4-124">Create an AllJoyn App project then select Introspection XML and desired Interfaces for code generation.</span></span>
4. <span data-ttu-id="689f4-125">생성 된 UWP Windows 런타임 구성 요소에서 노출 된 Api를 사용 하 여 앱에서 생산자 또는 ponsumer 코드를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="689f4-125">Implement producer or ponsumer code in your app using APIs exposed from the generated UWP Windows Runtime Components.</span></span>
5. <span data-ttu-id="689f4-126">UI를 빌드하십시오.</span><span class="sxs-lookup"><span data-stu-id="689f4-126">Build your UI.</span></span>

## <a name="preparing-your-build-environment"></a><span data-ttu-id="689f4-127">빌드 환경 준비</span><span class="sxs-lookup"><span data-stu-id="689f4-127">Preparing your Build Environment</span></span>

<span data-ttu-id="689f4-128">Windows 10 빌드 및 관련된 도구를 모든 UWP AllJoyn 사용 앱을 작성 해야 하는 리소스를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="689f4-128">The Windows 10 build and related tools include all of the resources that you'll need to write AllJoyn-enabled UWP apps.</span></span>

<span data-ttu-id="689f4-129">코드 작성 시작 하기 전에 수행 해야 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="689f4-129">Here's what you'll need to do before you get started writing code:</span></span>

* <span data-ttu-id="689f4-130">설치할 [Windows 10](https://www.microsoft.com/windows/) PC에서</span><span class="sxs-lookup"><span data-stu-id="689f4-130">Install [Windows 10](https://www.microsoft.com/windows/) on a PC</span></span>
* <span data-ttu-id="689f4-131">설치할 [Visual Studio 2017](https://www.visualstudio.com/downloads/download-visual-studio-vs) (Express edition을 사용 하지 마십시오)</span><span class="sxs-lookup"><span data-stu-id="689f4-131">Install [Visual Studio 2017](https://www.visualstudio.com/downloads/download-visual-studio-vs) (do NOT use an  Express edition)</span></span>
* <span data-ttu-id="689f4-132">다운로드 합니다 [AllJoyn® Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286) Visual Studio 갤러리에서 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="689f4-132">Download the [AllJoyn® Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286) Extension from the Visual Studio Gallery.</span></span> 


## <a name="obtaining-introspection-xml-for-alljoyn-interfaces"></a><span data-ttu-id="689f4-133">AllJoyn 인터페이스에 대 한 검사 XML 가져오기</span><span class="sxs-lookup"><span data-stu-id="689f4-133">Obtaining Introspection XML for AllJoyn Interfaces</span></span>

<span data-ttu-id="689f4-134">프로젝트를 시작 해야 하는 AllJoyn 인터페이스 정의 얻을 수 있는 방법은 세 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="689f4-134">There are three ways that you can obtain the AllJoyn interface  definitions that you will need to start your project:</span></span>

1. <span data-ttu-id="689f4-135">런타임 시 네트워크에 있는 AllJoyn 생산자에서 검사 XML을 추출 합니다.</span><span class="sxs-lookup"><span data-stu-id="689f4-135">Extract the Introspection XML from AllJoyn Producers present on your network at runtime.</span></span>
2. <span data-ttu-id="689f4-136">검사 XML 문서에서 가져오기 예: [서비스 프레임 워크 (LSF) 설명서를 조명](https://wiki.allseenalliance.org/_media/compliance/alljoyn_lamp_service_14.06_interface_definition.pdf) AllSeen Alliance에서.</span><span class="sxs-lookup"><span data-stu-id="689f4-136">Obtain the Introspection XML from documentation ; example: [Lighting Service Framework (LSF) documentation](https://wiki.allseenalliance.org/_media/compliance/alljoyn_lamp_service_14.06_interface_definition.pdf) from the AllSeen Alliance.</span></span>
3. <span data-ttu-id="689f4-137">AllJoyn 호환 되는 고유한 검사 XML 만듭니다 /[D Bus 검사](http://dbus.freedesktop.org/doc/dbus-specification.html) 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="689f4-137">Create your own Introspection XML that is compliant with the AllJoyn/[D-Bus introspection](http://dbus.freedesktop.org/doc/dbus-specification.html) format.</span></span>

<span data-ttu-id="689f4-138">이 문서에서는 처음 두 가지 방법-AllJoyn® Studio 기본적으로 지 원하는 네트워크 AllJoyn 생산자에 대 한 쿼리 및 해당 XML 추출 뿐만 아니라 검사 XML 파일을 업로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="689f4-138">This article covers the first two ways - AllJoyn® Studio natively supports querying the network for AllJoyn producers and extracting their XML as well as uploading Introspection XML files.</span></span>  <span data-ttu-id="689f4-139">나만의 사이트 생성 하는 방법을 알아봅니다 [여기](AllJoynProducer.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="689f4-139">Learn how to create your own [here](AllJoynProducer.md).</span></span>

<span data-ttu-id="689f4-140">토스터 AllJoyn 사용 장치를이 게시물에 대 한 예제로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="689f4-140">An AllJoyn-enabled toaster device will serve as the example for this post.</span></span> <span data-ttu-id="689f4-141">이 토스터 시작 하 고 알림을 버린 경우 toasting 시퀀스, "어둠" 설정 및 알림 중지에 대 한 컨트롤을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="689f4-141">This toaster exposes controls for starting and stopping the toasting sequence, setting the "darkness", and notifications when the toast is burnt.</span></span>

![AJ_toaster](../media/AllJoyn/AJ_toaster.jpg)

<span data-ttu-id="689f4-143">토스터는 다음 XML을 노출합니다.</span><span class="sxs-lookup"><span data-stu-id="689f4-143">The toaster exposes the following XML:</span></span>

``` xml
<node name="/toaster">
  <interface name="org.alljoyn.example.Toaster">
    <annotation name="org.alljoyn.Bus.Secure" value="true"/>
    <description language="en">Example interface for controlling a toaster appliance</description>
    <description language="fr">Interface Exemple de commande d'un appareil de grille-pain</description>
    <property name="Version" type="q" access="read">
      <description>Interface version</description>
      <annotation name="org.freedesktop.DBus.Property.EmitsChangedSignal" value="const"/>
    </property>
    <signal name="ToastBurnt" sessioncast="true">
      <description language="en">Toast is burnt</description>
      <description language="fr">Toast est brûlé</description>
    </signal>
    <method name="StartToasting">
      <description language="en">Start toasting</description>
      <description language="fr">Lancer grillage</description>
    </method>
    <method name="StopToasting">
      <description language="en">Stop toasting</description>
      <description language="fr">Arrêtez de grillage</description>
    </method>
    <property name="DarknessLevel" type="y" access="readwrite">
      <annotation name="org.freedesktop.DBus.Property.EmitsChangedSignal" value="true"/>
      <description language="en">Toasting darkness level</description>
      <description language="fr">Grillage niveau de l'obscurité</description>
    </property>
  </interface>
</node>
```

## <a name="creating-an-alljoyn-project"></a><span data-ttu-id="689f4-144">AllJoyn 프로젝트 만들기</span><span class="sxs-lookup"><span data-stu-id="689f4-144">Creating an AllJoyn Project</span></span>

<span data-ttu-id="689f4-145">일반적으로 동일한 방식으로 프로젝트를 만듭니다. 클릭 `File->New->New Project` 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="689f4-145">Create a Project the way you normally would: Click `File->New->New Project` to begin.</span></span>

![AJ_Studio_NewProject](../media/AllJoyn/AJ_Studio_NewProject.png)

<span data-ttu-id="689f4-147">Windows 유니버설 템플릿을 탐색 하는 대신 확장을 사용 하 여 설치 된 대상 언어에 대 한 "AllJoyn App" 템플릿을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="689f4-147">Instead of navigating to a Windows Universal Template, select the "AllJoyn App" Template for your target language which was installed with the Extension.</span></span>  <span data-ttu-id="689f4-148">프로젝트 이름을 지정 하 고 개발을 시작 하려면 파일 위치를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="689f4-148">Name your project and choose a file location to begin developing.</span></span>

![AJ_Studio_NameProj](../media/AllJoyn/AJ_Studio_NameProj.png)

<span data-ttu-id="689f4-150">AllJoyn 앱 템플릿의 선택한 후 즉시 Visual Studio 프로젝트에 포함 하려는 AllJoyn 인터페이스를 선택할 수 있습니다 묻습니다.</span><span class="sxs-lookup"><span data-stu-id="689f4-150">Immediately after selecting an AllJoyn App Template, Visual Studio will ask you to select the AllJoyn Interfaces you would like to include in your Project.</span></span> 

![AJ_Studio_Interfaces](../media/AllJoyn/AJ_Studio_Interfaces.png)

__<span data-ttu-id="689f4-152">네트워크의 장치에서 인터페이스 추출</span><span class="sxs-lookup"><span data-stu-id="689f4-152">Extracting interfaces from a device on the network</span></span>__

<span data-ttu-id="689f4-153">AllJoyn 장치 또는 네트워크 인터페이스를 찾을 수 없는 경우에 따라 [이 가이드](AllJoynTroubleshooting.md) 문제를 해결 하려면.</span><span class="sxs-lookup"><span data-stu-id="689f4-153">If you cannot find your AllJoyn device or interface on the network, follow [this guide](AllJoynTroubleshooting.md) to troubleshoot.</span></span> 

![AJ_Studio_FindDevices](../media/AllJoyn/AJ_Studio_FindDevices.png)

<span data-ttu-id="689f4-155">노출 된 인터페이스에 대 한 네트워크를 쿼리하려면 왼쪽 패널에서 "네트워크에서 생산자"를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="689f4-155">To query your network for exposed interfaces, select the "Producers on the network" in the left-hand panel.</span></span> <span data-ttu-id="689f4-156">인터페이스를 지 원하는 네트워크 및 목록에 있는 AllJoyn 생산자를 찾을 수이 합니다.</span><span class="sxs-lookup"><span data-stu-id="689f4-156">This will find any AllJoyn producer on the network and list the interfaces they support.</span></span>

![AJ_Studio_ListDevices](../media/AllJoyn/AJ_Studio_ListDevices.png)

<span data-ttu-id="689f4-158">프로젝트에 포함 하려면 원하는 인터페이스를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="689f4-158">Select the interfaces you would like to inlude in your project.</span></span>  <span data-ttu-id="689f4-159">이 경우에서는 사용 하는 토스터 인터페이스 "org.alljoyn.example.Toaster" 인터페이스에만 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="689f4-159">In this case, we are only using the toaster interface, so we select just the "org.alljoyn.example.Toaster" interface.</span></span>

![AJ_Studio_SelectDevices](../media/AllJoyn/AJ_Studio_SelectDevices.png)

<span data-ttu-id="689f4-161">"작업" 열에는 새로 선택한 인터페이스에 대 한 "추가"를 표시 합니다. 프로젝트에 보류 중인 변경 내용을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="689f4-161">The "Actions" column describes the pending changes to the Project, displaying "Add" for newly-selected Interfaces.</span></span> <span data-ttu-id="689f4-162">여기에서는 부여한 인터페이스 적용할 "이름 바꾸기" 작업을 트리거하는 "ToasterLibrary" 친숙 한 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="689f4-162">Here we have given the interface a friendly name of "ToasterLibrary", which triggers the "Rename" action to be applied.</span></span>

![AJ_Studio_DeviceAction](../media/AllJoyn/AJ_Studio_DeviceAction.png)

__<span data-ttu-id="689f4-164">파일에서 XML 로드</span><span class="sxs-lookup"><span data-stu-id="689f4-164">Loading an XML from a File</span></span>__

<span data-ttu-id="689f4-165">포함 된 해당 인터페이스를 확인 하려면 "찾아보기" 단추를 통해 검사 XML 파일을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="689f4-165">Choose any number of Introspection XML files via the "Browse" button to see their contained Interface(s).</span></span>

![AJ_Studio_BrowseXML](../media/AllJoyn/AJ_Studio_BrowseXML.png)

<span data-ttu-id="689f4-167">탐색 하 고 적절 한 XML 선택 (여기서 toaster.xml 사용).</span><span class="sxs-lookup"><span data-stu-id="689f4-167">Navigate to and select the appropriate XML (here, we are using toaster.xml).</span></span>

![AJ_Studio_BrowseXML_2](../media/AllJoyn/AJ_Studio_BrowseXML_2.png)

<span data-ttu-id="689f4-169">한 번 AllJoyn® Studio에서 XML 로드, 다양 한 인터페이스를 구문 분석 하 고 및 수 있도록 그 안에 포함 된 설명을 지원 하려는 하는 인터페이스를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="689f4-169">Once AllJoyn® Studio loads the XML, it will parse the various Interfaces and the descriptions contained within, allowing you select which Interfaces you would like to support.</span></span>

![AJ_Studio_BrowseXML_3](../media/AllJoyn/AJ_Studio_BrowseXML_3.png)

<span data-ttu-id="689f4-171">"작업" 열에는 새로 선택한 인터페이스에 대 한 "추가"를 표시 합니다. 프로젝트에 보류 중인 변경 내용을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="689f4-171">The "Actions" column describes the pending changes to the Project, displaying "Add" for newly-selected Interfaces.</span></span>

![AJ_Studio_BrowseXML_4](../media/AllJoyn/AJ_Studio_BrowseXML_4.png)

<span data-ttu-id="689f4-173">여기로 했습니다 "org.alljoyn.example.Toaster" 인터페이스를 포함 하 고 "ToasterLibrary" 친숙 한 이름에 제공 하면 적용할 "이름 바꾸기" 작업 트리거.</span><span class="sxs-lookup"><span data-stu-id="689f4-173">Here we have chosen to include the "org.alljoyn.example.Toaster" Interface and have given it a friendly name of "ToasterLibrary", triggering the "Rename" action to be applied.</span></span>

![AJ_Studio_BrowseXML_5](../media/AllJoyn/AJ_Studio_BrowseXML_5.png)

__<span data-ttu-id="689f4-175">추가 및 인터페이스를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="689f4-175">Adding and Removing Interfaces</span></span>__

<span data-ttu-id="689f4-176">다음이 단계를 완료 한 후 생성된 된 파일 자동으로 추가 됩니다는 C++ 위의 및 응용 프로그램 프로젝트에 대 한 참조로 추가에서 이름으로 Windows 런타임 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="689f4-176">After completing these steps, the generated files are automatically added to a C++ Windows Runtime Component with the friendly name from above and added as a Reference to the application Project.</span></span>  <span data-ttu-id="689f4-177">그러나 루트 Namespace은 여전히는 동일한 "org.alljoyn.example.Toaster"으로 인터페이스에서 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="689f4-177">However, the Root Namespace is still the same "org.alljoyn.example.Toaster" as defined by the interface.</span></span>  <span data-ttu-id="689f4-178">이러한 구성 요소에 액세스 하는 모든 클래스는 구성 요소의 루트 네임 스페이스에 대 한 "using" 절을 포함 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="689f4-178">Any classes that access these components need to have a "using" clause for the component's root namespace.</span></span>

![AJ_Studio_SolutionExplorer](../media/AllJoyn/AJ_Studio_SolutionExplorer.png)

_<span data-ttu-id="689f4-180">팁: IntelliSense의 이점을 얻기 위해서는 이제 생성 된 구성 요소를 빌드하십시오.</span><span class="sxs-lookup"><span data-stu-id="689f4-180">TIP: Build the generated components now in order to benefit from IntelliSense.</span></span>_

<span data-ttu-id="689f4-181">AllJoyn 앱 솔루션을 만든 후 항상 돌아가서 고 사용 하는 인터페이스를 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="689f4-181">After you have created your AllJoyn App solution, you can always go back and modify the interfaces you are using.</span></span> <span data-ttu-id="689f4-182">주 메뉴 모음에서 "AllJoyn-> 추가/제거 인터페이스..." 클릭 인터페이스 관리자를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="689f4-182">From the main menu bar, click "AllJoyn->Add/Remove Interfaces..." to launch the Interface manager.</span></span>

![AJ_Studio_AddInterfaces](../media/AllJoyn/AJ_Studio_AddInterfaces.png)

<span data-ttu-id="689f4-184">여기에서 "찾아보기..."를 클릭 수 있습니다. XML 파일을 추가 하거나 기존 인터페이스를 선택 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="689f4-184">From here, you may click "Browse..." to add more XML files, or de-select existing Interface(s).</span></span> <span data-ttu-id="689f4-185">해당 작업을 "제거" 하 고 확인 단추를 클릭 하는 인터페이스 업데이트를 선택 취소 솔루션에서 연결된 된 Windows 런타임 구성 요소를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="689f4-185">De-selecting an Interface updates its Action to "Remove", and clicking the Ok button removes the associated Windows Runtime Component from your solution.</span></span>

![AJ_Studio_AddXML](../media/AllJoyn/AJ_Studio_AddXML.png)

<span data-ttu-id="689f4-187">솔루션 탐색기를 보면 Windows 런타임 구성 요소 제거 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="689f4-187">Looking at the Solution Explorer, the Windows Runtime Component has been removed.</span></span>

![AJ_Studio_SolutionExplorer_2](../media/AllJoyn/AJ_Studio_SolutionExplorer_2.png)

## <a name="next-steps"></a><span data-ttu-id="689f4-189">다음 단계</span><span class="sxs-lookup"><span data-stu-id="689f4-189">Next Steps</span></span>

<span data-ttu-id="689f4-190">AllJoyn 기능을 구현할 때 항상 해야 "Windows.Devices.AllJoyn" 네임 스페이스에 사용 하려는 인터페이스에서 네임 스페이스를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="689f4-190">When implementing AllJoyn functionality, always be sure to include the "Windows.Devices.AllJoyn" namespace as well as the namespace from the interface you want to use.</span></span>

![AJ_Studio_namespace](../media/AllJoyn/AJ_Studio_namespace.png)

__<span data-ttu-id="689f4-192">AllJoyn 소비자를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="689f4-192">Implementing an AllJoyn Consumer</span></span>__

<span data-ttu-id="689f4-193">인터페이스에 대해 생성 된 코드 찾기 및 다음 생산자를 제어 하는 데 사용 하는 감시자 및 소비자 클래스를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="689f4-193">The code generated for the interfaces contains a watcher and consumer class used to find and then control a producer.</span></span> <span data-ttu-id="689f4-194">새 AllJoynBusAttachment 만들어 감시자 구현, 해당 AllJoynBusAttachment 사용 하 여 감시자를 초기화, 생산자 ("추가" 이벤트)을 찾는 감시자에 대 한 등록 다음 감시자를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="689f4-194">Implement the watcher by creating a new AllJoynBusAttachment, initialize the watcher with that AllJoynBusAttachment, register for the watcher finding a producer (the "Added" event), then start the watcher.</span></span>

![AJ_Studio_Code_1](../media/AllJoyn/AJ_Studio_Code_1.png)

<span data-ttu-id="689f4-196">감시자는 생산자를 발견 될 때마다 ToasterWatcher_Added 이벤트 트리거.</span><span class="sxs-lookup"><span data-stu-id="689f4-196">The ToasterWatcher_Added event triggers whenever the watcher finds a producer.</span></span>  <span data-ttu-id="689f4-197">이 이벤트를 사용 하 여 소비자를 등록 합니다.</span><span class="sxs-lookup"><span data-stu-id="689f4-197">Use this event to register a consumer.</span></span> <span data-ttu-id="689f4-198">Visual Studio에서 빠른 작업을 통해 필요한 셸 메서드를 생성 하는 참고 합니다.</span><span class="sxs-lookup"><span data-stu-id="689f4-198">Note that Visual Studio will generate the necessary shell method through the Quick Actions.</span></span>

![AJ_Studio_Code_2](../media/AllJoyn/AJ_Studio_Code_2.png)

<span data-ttu-id="689f4-200">다음 셸 코드를 생성 메서드를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="689f4-200">Generating the method produces the following shell code:</span></span>

![AJ_Studio_Code_3](../media/AllJoyn/AJ_Studio_Code_3.png)

<span data-ttu-id="689f4-202">올바른 논리를 사용 하 여 셸 코드를 해소 소비자를 등록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="689f4-202">Filling in the shell code with the correct logic enables registering the consumer.</span></span>

![AJ_Studio_Code_4](../media/AllJoyn/AJ_Studio_Code_4.png)

<span data-ttu-id="689f4-204">감시자 생산자 검색 될 때마다이 이벤트를 트리거하는 참고 합니다.</span><span class="sxs-lookup"><span data-stu-id="689f4-204">Note that this event triggers every time the watcher discovers a producer.</span></span>  <span data-ttu-id="689f4-205">여러 생산자를 찾으려는 경우 각 공급자에 대 한 하나의 소비자로 소비자의 데이터 구조를 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="689f4-205">If you expect to find multiple producers, keep a data structure of the consumer as there will be one consumer for each producer.</span></span>

<span data-ttu-id="689f4-206">다양 한 생산자는 내보냅니다 – 신호 속성 변경 이벤트 등록 신호 소비자 클래스의 직접 구성원 이지만 다른 신호 (방금 전 처럼, 사용 하 여 이러한 이벤트에 대 한 셸 코드를 생성 하려면 빠른 작업) 신호 클래스의 멤버는 합니다.</span><span class="sxs-lookup"><span data-stu-id="689f4-206">Register events for the various signals the producer will emit – property changed signals are direct members of the consumer class, but other signals are members of the Signals class (just as before, use the Quick Actions to generate the shell code for these events).</span></span>

![AJ_Studio_Code_5](../media/AllJoyn/AJ_Studio_Code_5.png)

<span data-ttu-id="689f4-208">소비자 개체를 사용 하 여 읽기 및 쓰기 속성 뿐만 아니라 메서드를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="689f4-208">Use the consumer object to read and write properties as well as call methods.</span></span>

![AJ_Studio_Code_6](../media/AllJoyn/AJ_Studio_Code_6.png)

### <a name="implementing-an-alljoyn-producer"></a><span data-ttu-id="689f4-210">AllJoyn 생산자를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="689f4-210">Implementing an AllJoyn Producer</span></span>

__<span data-ttu-id="689f4-211">서비스 구현</span><span class="sxs-lookup"><span data-stu-id="689f4-211">Implementing the Service</span></span>__

<span data-ttu-id="689f4-212">생산자는 해당 인터페이스를 노출 하는 서비스를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="689f4-212">Producers implement a service that expose their interfaces.</span></span>  <span data-ttu-id="689f4-213">생산자를 구현 하려면 먼저 해당 서비스에 대 한 클래스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="689f4-213">To implement a producer, first create a class for its service.</span></span>

![AJ_Studio_Code_7](../media/AllJoyn/AJ_Studio_Code_7.png)

<span data-ttu-id="689f4-215">인터페이스에 대 한 네임 스페이스를 "using" 문을 추가 하 고 서비스에 대해 생성 된 셸 인터페이스를 상속할 클래스를 구현 하려면 빠른 작업을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="689f4-215">Add the namespace for the interface to the "using" statements, then inherit the shell interface generated for the service and use the Quick Action to implement the class.</span></span>

![AJ_Studio_Code_8](../media/AllJoyn/AJ_Studio_Code_8.png)

<span data-ttu-id="689f4-217">여기에서 빠른 작업을 필요한 구성 요소 입력 됩니다.</span><span class="sxs-lookup"><span data-stu-id="689f4-217">From here, the Quick Action will fill in the necessary components.</span></span>

![AJ_Studio_Code_9](../media/AllJoyn/AJ_Studio_Code_9.png)

<span data-ttu-id="689f4-219">코드의 모든 필요한 부품 함수 준비가 되었지만 각 메서드 및 속성 호출에 대 한 실제 논리를 구현 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="689f4-219">All the necessary parts of the code are ready to function, but you still need to implement the actual logic for each method and property call.</span></span>

![AJ_Studio_Code_10](../media/AllJoyn/AJ_Studio_Code_10.png)

<span data-ttu-id="689f4-221">작업을 사용 하 여 성공 결과 만드는 예를 들어 SetDarknessLevelAsync를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="689f4-221">Taking the SetDarknessLevelAsync as an example, we use a task to create a success result.</span></span>  <span data-ttu-id="689f4-222">오류가 발생 한 경우 ToasterSetDarknessLevelResult.CreateFailureResult()를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="689f4-222">In case of failure, return ToasterSetDarknessLevelResult.CreateFailureResult().</span></span>

![AJ_Studio_Code_11](../media/AllJoyn/AJ_Studio_Code_11.png)

<span data-ttu-id="689f4-224">서비스를 완료 하려면 메서드 및 속성 호출의 나머지 부분을 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="689f4-224">Implement the rest of the method and property calls to finish the service.</span></span>

__<span data-ttu-id="689f4-225">생산자를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="689f4-225">Implementing the Producer</span></span>__

<span data-ttu-id="689f4-226">생산자를 만드는 과정은 간단 – 새 AllJoynBusAttachment 만든, 해당 AllJoynBusAttachment 사용 하 여 생산자를 초기화, 생산자, 새로 만든된 서비스를 초기화한 다음 생산자를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="689f4-226">Creating the producer is straightforward – create a new AllJoynBusAttachment, initialize a producer with that AllJoynBusAttachment, initialize the newly created service for the producer, then start the producer.</span></span>

![AJ_Studio_Code_12](../media/AllJoyn/AJ_Studio_Code_12.png)

<span data-ttu-id="689f4-228">대부분의 논리를 포함 하는 서비스에 있으므로 구현 과정이 남아 주요 기능을 속성 변경에 대 한 신호 및 비 상태 이벤트에 대 한 불연속 신호를 보내는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="689f4-228">Since the service contains the majority of the logic, the main functionality left to implement is to send the signals for property changes and discrete signals for non-state events.</span></span>  <span data-ttu-id="689f4-229">메서드 호출을 통해 필요에 따라이 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="689f4-229">Implement these as necessary through method calls.</span></span>

![AJ_Studio_Code_13](../media/AllJoyn/AJ_Studio_Code_13.png)

__<span data-ttu-id="689f4-231">추가 정보</span><span class="sxs-lookup"><span data-stu-id="689f4-231">More Information</span></span>__

<span data-ttu-id="689f4-232">이 문서에서 지침의 모든 올바르게 완료 했다면, 앱에서 AllJoyn 코드 작성을 시작할 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="689f4-232">If you've completed all of the instructions in this document correctly, you are ready to start writing AllJoyn code in your app.</span></span>

<span data-ttu-id="689f4-233">참조를 확인 하세요 AllJoyn 유니버설 Windows 앱 샘플에 대 한 Microsoft 샘플 github [AllJoyn 생산자](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AllJoyn/ProducerExperiences) 하 고 [AllJoyn 소비자](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AllJoyn/ConsumerExperiences)합니다.</span><span class="sxs-lookup"><span data-stu-id="689f4-233">For reference, please look to the AllJoyn Universal Windows Apps samples on the Microsoft Sample GitHub for [AllJoyn Producers](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AllJoyn/ProducerExperiences) and [AllJoyn Consumers](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AllJoyn/ConsumerExperiences).</span></span>

<span data-ttu-id="689f4-234">AllJoyn 앱을 만드는 방법의 자세한 연습 과정에서는 623 AllJoyn 세션을 시청 하세요.</span><span class="sxs-lookup"><span data-stu-id="689f4-234">For a detailed walkthrough of how to create an AllJoyn app, please watch the AllJoyn session 623:</span></span>

> [!VIDEO https://channel9.msdn.com/Events/Build/2015/2-623/player]

<span data-ttu-id="689f4-235">이러한 경우와 같이 루프백 예외를 활성화 하지 않은 Windows 정책에 의해 AllJoyn 통신 동일한 컴퓨터에 두 개의 UWP 앱은 비활성화 되었음을 참고 Visual Studio에서 직접 배포 중입니다.</span><span class="sxs-lookup"><span data-stu-id="689f4-235">Note that AllJoyn communication between two UWP apps on the same machine is disabled by Windows policy unless they have enabled a loopback exception, such as when being directly deployed from Visual Studio.</span></span>  <span data-ttu-id="689f4-236">루프백 예외를 사용 하도록 설정 하는 방법은 참조 하세요 [여기](https://msdn.microsoft.com/library/windows/apps/Hh780593.aspx)합니다.</span><span class="sxs-lookup"><span data-stu-id="689f4-236">For detailed instructions on enabling loopback exemption, see [here](https://msdn.microsoft.com/library/windows/apps/Hh780593.aspx).</span></span>



