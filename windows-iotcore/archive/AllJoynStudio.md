---
title: AllJoyn Studio
author: saraclay
ms.author: saclayt
ms.date: 09/07/17
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: UWP (유니버설 Windows 플랫폼) AllJoyn Api 및 Visual Studio 2017을 사용 하 여 AllJoyn UWP 앱을 만드는 방법에 대해 알아봅니다.
keywords: windows iot, AllJoyn
ms.openlocfilehash: 5326873218c0126b918679308e3a8e08cdddf84c
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "60168501"
---
> [!NOTE]
> <span data-ttu-id="51eeb-104">보관 된 설명서를 보고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51eeb-104">You are viewing archived documentation.</span></span> <span data-ttu-id="51eeb-105">AllJoyn는 Windows 10 IoT에서 더 이상 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="51eeb-105">AllJoyn is no longer supported by Windows 10 IoT.</span></span> <span data-ttu-id="51eeb-106">질문이 있는 경우 GitHub에서 문제를 열거나 아래 설명에 의견을 남겨 주세요.</span><span class="sxs-lookup"><span data-stu-id="51eeb-106">For questions, please open an issue on GitHub or leave us feedback in the comments below.</span></span>

# <a name="using-the-alljoyn-studio-extension"></a><span data-ttu-id="51eeb-107">AllJoyn Studio 확장 사용</span><span class="sxs-lookup"><span data-stu-id="51eeb-107">Using the AllJoyn Studio Extension</span></span>

<span data-ttu-id="51eeb-108">사물 인터넷에 대 한 권한을 부여 하는 데에는 모든 권한을 부여 하는 [Allseen 동맹](https://allseenalliance.org/)</span><span class="sxs-lookup"><span data-stu-id="51eeb-108">The [AllSeen Alliance](https://allseenalliance.org/) created AllJoyn to empower the Internet of Things.</span></span> <span data-ttu-id="51eeb-109">Windows 10에는 기본적으로 해당 플랫폼에 빌드되는 개발자가 Windows 10 앱을 "IoT (IoT)" 하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51eeb-109">Windows 10 has AllJoyn built natively into its platform, allowing developers to easily take advantage of AllJoyn to "IoT-enable" your Windows 10 apps.</span></span> <span data-ttu-id="51eeb-110">이 문서에서는 UWP (유니버설 Windows 플랫폼) AllJoyn Api 및 Visual Studio 2017 [Alljoyn Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286) 확장을 사용 하 여 Windows 10 용 앱을 빌드하는 데 필요한 단계를 간략하게 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="51eeb-110">This article will outline the steps required to build apps for Windows 10 using the Universal Windows Platform (UWP) AllJoyn APIs and the Visual Studio 2017 [AllJoyn Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286) Extension.</span></span>

## <a name="understanding-alljoyn-uwp-app-development"></a><span data-ttu-id="51eeb-111">AllJoyn UWP 앱 개발 이해</span><span class="sxs-lookup"><span data-stu-id="51eeb-111">Understanding AllJoyn UWP App Development</span></span>

<span data-ttu-id="51eeb-112">다음 세 가지 주요 구성 요소는 AllJoyn UWP 앱을 형성 합니다.</span><span class="sxs-lookup"><span data-stu-id="51eeb-112">Three major components form AllJoyn UWP apps:</span></span>

1. <span data-ttu-id="51eeb-113">앱 레이아웃 및 디자인 (XAML 또는 HTML) 및 클래스 구성 요소C#(, JavaScript C++, 또는 VB)</span><span class="sxs-lookup"><span data-stu-id="51eeb-113">App layout and design (XAML or HTML) and class components (C#, JavaScript, C++, or VB).</span></span>
2. <span data-ttu-id="51eeb-114">AllJoyn 핵심 Api: Windows 10 SDK에서 사용 가능한 AllJoyn 표준 클라이언트 API (C) 및 Windows (WinRT)</span><span class="sxs-lookup"><span data-stu-id="51eeb-114">The AllJoyn core APIs: AllJoyn Standard Client API (C) and Windows.Devices.AllJoyn API (WinRT)  available in the Windows 10 SDK.</span></span>
3. <span data-ttu-id="51eeb-115">하나 이상의 UWP Windows 런타임 구성 요소 (는 AllJoyn 인터페이스에서이 코드를 생성)</span><span class="sxs-lookup"><span data-stu-id="51eeb-115">One or more UWP Windows Runtime Components (the  generates this code from AllJoyn interfaces).</span></span>

<span data-ttu-id="51eeb-116">다음 다이어그램에서는 일반적인 AllJoyn UWP 프로젝트의 아키텍처를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="51eeb-116">The following diagram shows the architecture of a typical AllJoyn UWP project:</span></span>

![AJ_UWP_Architecture](../media/AllJoyn/AJ_UWP_Architecture.jpg)

<span data-ttu-id="51eeb-118">AllJoyn 지원 UWP 앱은 생산자 (인터페이스를 구현 하 고 노출 하는 방법, 일반적으로 장치), 소비자 (인터페이스, 일반적으로 앱) 또는 둘 다 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51eeb-118">AllJoyn-enabled UWP apps can be either producers  (implement and expose interfaces, typically a device ), consumers (use interfaces, typically apps), or both.</span></span> <span data-ttu-id="51eeb-119">소비자 및 생산자는 구현 세부 정보에서 분기 된 동일한 시작 단계를 공유 합니다.</span><span class="sxs-lookup"><span data-stu-id="51eeb-119">Consumers and producers share the same starting steps, only diverging in the implementation details.</span></span>

## <a name="creating-an-alljoyn-enabled-uwp-app"></a><span data-ttu-id="51eeb-120">AllJoyn 사용 UWP 앱 만들기</span><span class="sxs-lookup"><span data-stu-id="51eeb-120">Creating an AllJoyn-enabled UWP app</span></span>

<span data-ttu-id="51eeb-121">Windows 10 용 AllJoyn 사용 UWP 앱을 개발 하려면 다음 단계를 수행 합니다 (이 문서의 뒷부분에서 설명).</span><span class="sxs-lookup"><span data-stu-id="51eeb-121">Follow these steps to develop AllJoyn-enabled UWP apps for Windows 10: (explained in detail later in this document)</span></span>

1. <span data-ttu-id="51eeb-122">빌드 환경을 준비 합니다.</span><span class="sxs-lookup"><span data-stu-id="51eeb-122">Prepare your build environment.</span></span>
2. <span data-ttu-id="51eeb-123">사용 될 AllJoyn 인터페이스를 확인 하 고 필요한 검사 XML을 가져오거나 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="51eeb-123">Determine which AllJoyn interfaces will be used, and obtain or create necessary Introspection XML.</span></span>
3. <span data-ttu-id="51eeb-124">AllJoyn 앱 프로젝트를 만든 다음 검사 XML 및 원하는 인터페이스를 선택 하 여 코드를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="51eeb-124">Create an AllJoyn App project then select Introspection XML and desired Interfaces for code generation.</span></span>
4. <span data-ttu-id="51eeb-125">생성 된 UWP Windows 런타임 구성 요소에서 노출 된 Api를 사용 하 여 앱에서 생산자 또는 ponsumer 코드를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="51eeb-125">Implement producer or ponsumer code in your app using APIs exposed from the generated UWP Windows Runtime Components.</span></span>
5. <span data-ttu-id="51eeb-126">UI를 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="51eeb-126">Build your UI.</span></span>

## <a name="preparing-your-build-environment"></a><span data-ttu-id="51eeb-127">빌드 환경 준비</span><span class="sxs-lookup"><span data-stu-id="51eeb-127">Preparing your Build Environment</span></span>

<span data-ttu-id="51eeb-128">Windows 10 빌드 및 관련 도구에는 AllJoyn 사용 UWP 앱을 작성 하는 데 필요한 모든 리소스가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51eeb-128">The Windows 10 build and related tools include all of the resources that you'll need to write AllJoyn-enabled UWP apps.</span></span>

<span data-ttu-id="51eeb-129">코드 작성을 시작 하기 전에 수행 해야 하는 작업은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="51eeb-129">Here's what you'll need to do before you get started writing code:</span></span>

* <span data-ttu-id="51eeb-130">PC에 [Windows 10](https://www.microsoft.com/windows/) 설치</span><span class="sxs-lookup"><span data-stu-id="51eeb-130">Install [Windows 10](https://www.microsoft.com/windows/) on a PC</span></span>
* <span data-ttu-id="51eeb-131">[Visual Studio 2017](https://www.visualstudio.com/downloads/download-visual-studio-vs) 설치 (Express edition 사용 안 함)</span><span class="sxs-lookup"><span data-stu-id="51eeb-131">Install [Visual Studio 2017](https://www.visualstudio.com/downloads/download-visual-studio-vs) (do NOT use an  Express edition)</span></span>
* <span data-ttu-id="51eeb-132">Visual Studio 갤러리에서 [AllJoyn® Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286) 확장을 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="51eeb-132">Download the [AllJoyn® Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286) Extension from the Visual Studio Gallery.</span></span> 


## <a name="obtaining-introspection-xml-for-alljoyn-interfaces"></a><span data-ttu-id="51eeb-133">검사 XML for AllJoyn 인터페이스 가져오기</span><span class="sxs-lookup"><span data-stu-id="51eeb-133">Obtaining Introspection XML for AllJoyn Interfaces</span></span>

<span data-ttu-id="51eeb-134">다음 세 가지 방법으로 프로젝트를 시작 하는 데 필요한 AllJoyn 인터페이스 정의를 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51eeb-134">There are three ways that you can obtain the AllJoyn interface  definitions that you will need to start your project:</span></span>

1. <span data-ttu-id="51eeb-135">런타임에 네트워크에 있는 AllJoyn 생산자에서 검사 XML을 추출 합니다.</span><span class="sxs-lookup"><span data-stu-id="51eeb-135">Extract the Introspection XML from AllJoyn Producers present on your network at runtime.</span></span>
2. <span data-ttu-id="51eeb-136">설명서에서 검사 XML을 가져옵니다. 예 들어 AllSeen 동맹의 [Umservice Framework (LSF) 설명서](https://wiki.allseenalliance.org/_media/compliance/alljoyn_lamp_service_14.06_interface_definition.pdf) 입니다.</span><span class="sxs-lookup"><span data-stu-id="51eeb-136">Obtain the Introspection XML from documentation ; example: [Lighting Service Framework (LSF) documentation](https://wiki.allseenalliance.org/_media/compliance/alljoyn_lamp_service_14.06_interface_definition.pdf) from the AllSeen Alliance.</span></span>
3. <span data-ttu-id="51eeb-137">AllJoyn/[D-Bus 검사](http://dbus.freedesktop.org/doc/dbus-specification.html) 형식과 호환 되는 고유한 검사 XML을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="51eeb-137">Create your own Introspection XML that is compliant with the AllJoyn/[D-Bus introspection](http://dbus.freedesktop.org/doc/dbus-specification.html) format.</span></span>

<span data-ttu-id="51eeb-138">이 문서에서는 처음 두® 가지 방법으로 검사를 설명 합니다. Studio는 기본적으로 AllJoyn 생산자 용 네트워크 쿼리를 지원 하 고 XML 파일을 추출 하 고 XML 파일을 업로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="51eeb-138">This article covers the first two ways - AllJoyn® Studio natively supports querying the network for AllJoyn producers and extracting their XML as well as uploading Introspection XML files.</span></span>  <span data-ttu-id="51eeb-139">[여기](AllJoynProducer.md)에서 직접 만드는 방법을 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="51eeb-139">Learn how to create your own [here](AllJoynProducer.md).</span></span>

<span data-ttu-id="51eeb-140">AllJoyn 지원 toaster 장치는이 게시물에 대 한 예제로 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="51eeb-140">An AllJoyn-enabled toaster device will serve as the example for this post.</span></span> <span data-ttu-id="51eeb-141">이 toaster는 toasting 시퀀스를 시작 및 중지 하 고, "어둡기"를 설정 하 고, 알림이 burnt 경우 알림을 표시 하는 컨트롤을 노출 합니다.</span><span class="sxs-lookup"><span data-stu-id="51eeb-141">This toaster exposes controls for starting and stopping the toasting sequence, setting the "darkness", and notifications when the toast is burnt.</span></span>

![AJ_toaster](../media/AllJoyn/AJ_toaster.jpg)

<span data-ttu-id="51eeb-143">Toaster는 다음 XML을 노출 합니다.</span><span class="sxs-lookup"><span data-stu-id="51eeb-143">The toaster exposes the following XML:</span></span>

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

## <a name="creating-an-alljoyn-project"></a><span data-ttu-id="51eeb-144">AllJoyn 프로젝트 만들기</span><span class="sxs-lookup"><span data-stu-id="51eeb-144">Creating an AllJoyn Project</span></span>

<span data-ttu-id="51eeb-145">일반적인 방법으로 프로젝트를 만듭니다. 클릭 `File->New->New Project` 하 여 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="51eeb-145">Create a Project the way you normally would: Click `File->New->New Project` to begin.</span></span>

![AJ_Studio_NewProject](../media/AllJoyn/AJ_Studio_NewProject.png)

<span data-ttu-id="51eeb-147">Windows 유니버설 템플릿으로 이동 하는 대신 확장과 함께 설치 된 대상 언어에 대 한 "AllJoyn 앱" 템플릿을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="51eeb-147">Instead of navigating to a Windows Universal Template, select the "AllJoyn App" Template for your target language which was installed with the Extension.</span></span>  <span data-ttu-id="51eeb-148">프로젝트 이름을로 하 고 개발을 시작할 파일 위치를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="51eeb-148">Name your project and choose a file location to begin developing.</span></span>

![AJ_Studio_NameProj](../media/AllJoyn/AJ_Studio_NameProj.png)

<span data-ttu-id="51eeb-150">AllJoyn 앱 템플릿을 선택 하 고 나면 Visual Studio에서 프로젝트에 포함 하려는 AllJoyn 인터페이스를 선택 하도록 요청 합니다.</span><span class="sxs-lookup"><span data-stu-id="51eeb-150">Immediately after selecting an AllJoyn App Template, Visual Studio will ask you to select the AllJoyn Interfaces you would like to include in your Project.</span></span> 

![AJ_Studio_Interfaces](../media/AllJoyn/AJ_Studio_Interfaces.png)

<span data-ttu-id="51eeb-152">__네트워크의 장치에서 인터페이스 추출__</span><span class="sxs-lookup"><span data-stu-id="51eeb-152">__Extracting interfaces from a device on the network__</span></span>

<span data-ttu-id="51eeb-153">네트워크에서 AllJoyn 장치 또는 인터페이스를 찾을 수 없는 경우 [이 가이드](AllJoynTroubleshooting.md) 에 따라 문제를 해결 하십시오.</span><span class="sxs-lookup"><span data-stu-id="51eeb-153">If you cannot find your AllJoyn device or interface on the network, follow [this guide](AllJoynTroubleshooting.md) to troubleshoot.</span></span> 

![AJ_Studio_FindDevices](../media/AllJoyn/AJ_Studio_FindDevices.png)

<span data-ttu-id="51eeb-155">네트워크에서 노출 된 인터페이스를 쿼리하려면 왼쪽 패널에서 "네트워크에서 생산자"를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="51eeb-155">To query your network for exposed interfaces, select the "Producers on the network" in the left-hand panel.</span></span> <span data-ttu-id="51eeb-156">그러면 네트워크에서 모든 AllJoyn 생산자가 검색 되어 지원 되는 인터페이스가 나열 됩니다.</span><span class="sxs-lookup"><span data-stu-id="51eeb-156">This will find any AllJoyn producer on the network and list the interfaces they support.</span></span>

![AJ_Studio_ListDevices](../media/AllJoyn/AJ_Studio_ListDevices.png)

<span data-ttu-id="51eeb-158">프로젝트에서 포함 인터페이스를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="51eeb-158">Select the interfaces you would like to inlude in your project.</span></span>  <span data-ttu-id="51eeb-159">이 경우에는 toaster 인터페이스만 사용 하 고 있으므로 "Toaster" 인터페이스만 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="51eeb-159">In this case, we are only using the toaster interface, so we select just the "org.alljoyn.example.Toaster" interface.</span></span>

![AJ_Studio_SelectDevices](../media/AllJoyn/AJ_Studio_SelectDevices.png)

<span data-ttu-id="51eeb-161">"작업" 열은 프로젝트에 대해 보류 중인 변경 내용을 설명 하 고 새로 선택 된 인터페이스에 대해 "추가"를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="51eeb-161">The "Actions" column describes the pending changes to the Project, displaying "Add" for newly-selected Interfaces.</span></span> <span data-ttu-id="51eeb-162">여기에서 인터페이스에 "ToasterLibrary" 라는 친숙 한 이름을 지정 하 여 "Rename" 작업을 적용 하도록 트리거합니다.</span><span class="sxs-lookup"><span data-stu-id="51eeb-162">Here we have given the interface a friendly name of "ToasterLibrary", which triggers the "Rename" action to be applied.</span></span>

![AJ_Studio_DeviceAction](../media/AllJoyn/AJ_Studio_DeviceAction.png)

<span data-ttu-id="51eeb-164">__파일에서 XML 로드__</span><span class="sxs-lookup"><span data-stu-id="51eeb-164">__Loading an XML from a File__</span></span>

<span data-ttu-id="51eeb-165">"찾아보기" 단추를 통해 원하는 수의 검사 XML 파일을 선택 하 여 포함 된 인터페이스를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="51eeb-165">Choose any number of Introspection XML files via the "Browse" button to see their contained Interface(s).</span></span>

![AJ_Studio_BrowseXML](../media/AllJoyn/AJ_Studio_BrowseXML.png)

<span data-ttu-id="51eeb-167">적절 한 XML로 이동 하 여 선택 합니다. 여기서는 toaster를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="51eeb-167">Navigate to and select the appropriate XML (here, we are using toaster.xml).</span></span>

![AJ_Studio_BrowseXML_2](../media/AllJoyn/AJ_Studio_BrowseXML_2.png)

<span data-ttu-id="51eeb-169">AllJoyn® Studio에서 XML을 로드 하면 여러 인터페이스와에 포함 된 설명을 구문 분석 하 여 지원 하려는 인터페이스를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51eeb-169">Once AllJoyn® Studio loads the XML, it will parse the various Interfaces and the descriptions contained within, allowing you select which Interfaces you would like to support.</span></span>

![AJ_Studio_BrowseXML_3](../media/AllJoyn/AJ_Studio_BrowseXML_3.png)

<span data-ttu-id="51eeb-171">"작업" 열은 프로젝트에 대해 보류 중인 변경 내용을 설명 하 고 새로 선택 된 인터페이스에 대해 "추가"를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="51eeb-171">The "Actions" column describes the pending changes to the Project, displaying "Add" for newly-selected Interfaces.</span></span>

![AJ_Studio_BrowseXML_4](../media/AllJoyn/AJ_Studio_BrowseXML_4.png)

<span data-ttu-id="51eeb-173">여기서는 "Toaster" 인터페이스를 포함 하 고 "ToasterLibrary" 라는 친숙 한 이름을 지정 하 여 "Rename" 작업을 적용 하도록 선택 했습니다.</span><span class="sxs-lookup"><span data-stu-id="51eeb-173">Here we have chosen to include the "org.alljoyn.example.Toaster" Interface and have given it a friendly name of "ToasterLibrary", triggering the "Rename" action to be applied.</span></span>

![AJ_Studio_BrowseXML_5](../media/AllJoyn/AJ_Studio_BrowseXML_5.png)

<span data-ttu-id="51eeb-175">__인터페이스 추가 및 제거__</span><span class="sxs-lookup"><span data-stu-id="51eeb-175">__Adding and Removing Interfaces__</span></span>

<span data-ttu-id="51eeb-176">이러한 단계를 완료 한 후 생성 된 파일은 위의 이름을 가진 C++ Windows 런타임 구성 요소에 자동으로 추가 되 고 응용 프로그램 프로젝트에 대 한 참조로 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="51eeb-176">After completing these steps, the generated files are automatically added to a C++ Windows Runtime Component with the friendly name from above and added as a Reference to the application Project.</span></span>  <span data-ttu-id="51eeb-177">그러나 루트 네임 스페이스는 여전히 인터페이스에서 정의 된 것과 동일한 "Toaster"입니다.</span><span class="sxs-lookup"><span data-stu-id="51eeb-177">However, the Root Namespace is still the same "org.alljoyn.example.Toaster" as defined by the interface.</span></span>  <span data-ttu-id="51eeb-178">이러한 구성 요소에 액세스 하는 모든 클래스에는 구성 요소의 루트 네임 스페이스에 대 한 "using" 절이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="51eeb-178">Any classes that access these components need to have a "using" clause for the component's root namespace.</span></span>

![AJ_Studio_SolutionExplorer](../media/AllJoyn/AJ_Studio_SolutionExplorer.png)

<span data-ttu-id="51eeb-180">_잠깐만 IntelliSense를 활용 하기 위해 이제 생성 된 구성 요소를 빌드합니다._</span><span class="sxs-lookup"><span data-stu-id="51eeb-180">_TIP: Build the generated components now in order to benefit from IntelliSense._</span></span>

<span data-ttu-id="51eeb-181">AllJoyn 앱 솔루션을 만든 후에는 언제 든 지 다시 돌아가서 사용 중인 인터페이스를 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51eeb-181">After you have created your AllJoyn App solution, you can always go back and modify the interfaces you are using.</span></span> <span data-ttu-id="51eeb-182">주 메뉴 모음에서 "AllJoyn-> 인터페이스 추가/제거 ..."를 클릭 합니다. 인터페이스 관리자를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="51eeb-182">From the main menu bar, click "AllJoyn->Add/Remove Interfaces..." to launch the Interface manager.</span></span>

![AJ_Studio_AddInterfaces](../media/AllJoyn/AJ_Studio_AddInterfaces.png)

<span data-ttu-id="51eeb-184">여기에서 "찾아보기 ..."를 클릭할 수 있습니다. XML 파일을 더 추가 하거나 기존 인터페이스를 선택 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="51eeb-184">From here, you may click "Browse..." to add more XML files, or de-select existing Interface(s).</span></span> <span data-ttu-id="51eeb-185">인터페이스를 선택 취소 하면 해당 작업이 "제거"로 업데이트 되 고 확인 단추를 클릭 하면 솔루션에서 연결 된 Windows 런타임 구성 요소가 제거 됩니다.</span><span class="sxs-lookup"><span data-stu-id="51eeb-185">De-selecting an Interface updates its Action to "Remove", and clicking the Ok button removes the associated Windows Runtime Component from your solution.</span></span>

![AJ_Studio_AddXML](../media/AllJoyn/AJ_Studio_AddXML.png)

<span data-ttu-id="51eeb-187">솔루션 탐색기를 살펴보면 Windows 런타임 구성 요소가 제거 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="51eeb-187">Looking at the Solution Explorer, the Windows Runtime Component has been removed.</span></span>

![AJ_Studio_SolutionExplorer_2](../media/AllJoyn/AJ_Studio_SolutionExplorer_2.png)

## <a name="next-steps"></a><span data-ttu-id="51eeb-189">다음 단계</span><span class="sxs-lookup"><span data-stu-id="51eeb-189">Next Steps</span></span>

<span data-ttu-id="51eeb-190">AllJoyn 기능을 구현 하는 경우 사용 하려는 인터페이스의 네임 스페이스 뿐만 아니라 항상 "Windows.</span><span class="sxs-lookup"><span data-stu-id="51eeb-190">When implementing AllJoyn functionality, always be sure to include the "Windows.Devices.AllJoyn" namespace as well as the namespace from the interface you want to use.</span></span>

![AJ_Studio_namespace](../media/AllJoyn/AJ_Studio_namespace.png)

<span data-ttu-id="51eeb-192">__AllJoyn 소비자 구현__</span><span class="sxs-lookup"><span data-stu-id="51eeb-192">__Implementing an AllJoyn Consumer__</span></span>

<span data-ttu-id="51eeb-193">인터페이스에 대해 생성 된 코드에는 생산자를 찾고 제어 하는 데 사용 되는 감시자 및 소비자 클래스가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="51eeb-193">The code generated for the interfaces contains a watcher and consumer class used to find and then control a producer.</span></span> <span data-ttu-id="51eeb-194">새 AllJoynBusAttachment을 만들고, 해당 AllJoynBusAttachment를 사용 하 여 감시자를 초기화 하 고, 공급자 ("추가" 이벤트)를 찾는 감시자를 등록 한 다음 감시자를 시작 하 여 감시자를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="51eeb-194">Implement the watcher by creating a new AllJoynBusAttachment, initialize the watcher with that AllJoynBusAttachment, register for the watcher finding a producer (the "Added" event), then start the watcher.</span></span>

![AJ_Studio_Code_1](../media/AllJoyn/AJ_Studio_Code_1.png)

<span data-ttu-id="51eeb-196">ToasterWatcher_Added 이벤트는 감시자가 생산자를 찾을 때마다 트리거됩니다.</span><span class="sxs-lookup"><span data-stu-id="51eeb-196">The ToasterWatcher_Added event triggers whenever the watcher finds a producer.</span></span>  <span data-ttu-id="51eeb-197">이 이벤트를 사용 하 여 소비자를 등록 합니다.</span><span class="sxs-lookup"><span data-stu-id="51eeb-197">Use this event to register a consumer.</span></span> <span data-ttu-id="51eeb-198">Visual Studio는 빠른 작업을 통해 필요한 셸 메서드를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="51eeb-198">Note that Visual Studio will generate the necessary shell method through the Quick Actions.</span></span>

![AJ_Studio_Code_2](../media/AllJoyn/AJ_Studio_Code_2.png)

<span data-ttu-id="51eeb-200">메서드를 생성 하면 다음 셸 코드가 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="51eeb-200">Generating the method produces the following shell code:</span></span>

![AJ_Studio_Code_3](../media/AllJoyn/AJ_Studio_Code_3.png)

<span data-ttu-id="51eeb-202">올바른 논리를 사용 하 여 셸 코드를 채우면 소비자를 등록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51eeb-202">Filling in the shell code with the correct logic enables registering the consumer.</span></span>

![AJ_Studio_Code_4](../media/AllJoyn/AJ_Studio_Code_4.png)

<span data-ttu-id="51eeb-204">이 이벤트는 감시자가 생산자를 검색할 때마다 트리거됩니다.</span><span class="sxs-lookup"><span data-stu-id="51eeb-204">Note that this event triggers every time the watcher discovers a producer.</span></span>  <span data-ttu-id="51eeb-205">여러 생산자를 찾아야 하는 경우 각 생산자에 대해 소비자가 하나씩 있으므로 소비자의 데이터 구조를 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="51eeb-205">If you expect to find multiple producers, keep a data structure of the consumer as there will be one consumer for each producer.</span></span>

<span data-ttu-id="51eeb-206">생산자가 내보내는 다양 한 신호에 대 한 이벤트 등록 – 속성 변경 신호는 소비자 클래스의 직접 멤버 이지만 다른 신호는 신호 클래스의 멤버입니다. 이전 처럼 빠른 작업을 사용 하 여 이러한 이벤트에 대 한 셸 코드를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="51eeb-206">Register events for the various signals the producer will emit – property changed signals are direct members of the consumer class, but other signals are members of the Signals class (just as before, use the Quick Actions to generate the shell code for these events).</span></span>

![AJ_Studio_Code_5](../media/AllJoyn/AJ_Studio_Code_5.png)

<span data-ttu-id="51eeb-208">소비자 개체를 사용 하 여 메서드를 호출 하는 것 뿐만 아니라 속성을 읽고 씁니다.</span><span class="sxs-lookup"><span data-stu-id="51eeb-208">Use the consumer object to read and write properties as well as call methods.</span></span>

![AJ_Studio_Code_6](../media/AllJoyn/AJ_Studio_Code_6.png)

### <a name="implementing-an-alljoyn-producer"></a><span data-ttu-id="51eeb-210">AllJoyn 생산자 구현</span><span class="sxs-lookup"><span data-stu-id="51eeb-210">Implementing an AllJoyn Producer</span></span>

<span data-ttu-id="51eeb-211">__서비스 구현__</span><span class="sxs-lookup"><span data-stu-id="51eeb-211">__Implementing the Service__</span></span>

<span data-ttu-id="51eeb-212">생산자는 인터페이스를 노출 하는 서비스를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="51eeb-212">Producers implement a service that expose their interfaces.</span></span>  <span data-ttu-id="51eeb-213">생산자를 구현 하려면 먼저 해당 서비스에 대 한 클래스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="51eeb-213">To implement a producer, first create a class for its service.</span></span>

![AJ_Studio_Code_7](../media/AllJoyn/AJ_Studio_Code_7.png)

<span data-ttu-id="51eeb-215">인터페이스에 대 한 네임 스페이스를 "using" 문에 추가 하 고, 서비스에 대해 생성 된 셸 인터페이스를 상속 하 고, 빠른 작업을 사용 하 여 클래스를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="51eeb-215">Add the namespace for the interface to the "using" statements, then inherit the shell interface generated for the service and use the Quick Action to implement the class.</span></span>

![AJ_Studio_Code_8](../media/AllJoyn/AJ_Studio_Code_8.png)

<span data-ttu-id="51eeb-217">여기서 빠른 작업은 필요한 구성 요소를 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="51eeb-217">From here, the Quick Action will fill in the necessary components.</span></span>

![AJ_Studio_Code_9](../media/AllJoyn/AJ_Studio_Code_9.png)

<span data-ttu-id="51eeb-219">코드의 모든 필요한 부분이 작동할 준비가 되었지만 각 메서드와 속성 호출에 대 한 실제 논리를 구현 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="51eeb-219">All the necessary parts of the code are ready to function, but you still need to implement the actual logic for each method and property call.</span></span>

![AJ_Studio_Code_10](../media/AllJoyn/AJ_Studio_Code_10.png)

<span data-ttu-id="51eeb-221">SetDarknessLevelAsync를 예로 들어 보겠습니다. 작업을 사용 하 여 성공 결과를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="51eeb-221">Taking the SetDarknessLevelAsync as an example, we use a task to create a success result.</span></span>  <span data-ttu-id="51eeb-222">오류가 발생 하는 경우 ToasterSetDarknessLevelResult. CreateFailureResult ()을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="51eeb-222">In case of failure, return ToasterSetDarknessLevelResult.CreateFailureResult().</span></span>

![AJ_Studio_Code_11](../media/AllJoyn/AJ_Studio_Code_11.png)

<span data-ttu-id="51eeb-224">나머지 메서드 및 속성 호출을 구현 하 여 서비스를 완료 합니다.</span><span class="sxs-lookup"><span data-stu-id="51eeb-224">Implement the rest of the method and property calls to finish the service.</span></span>

<span data-ttu-id="51eeb-225">__생산자 구현__</span><span class="sxs-lookup"><span data-stu-id="51eeb-225">__Implementing the Producer__</span></span>

<span data-ttu-id="51eeb-226">생산자를 만드는 과정은 간단 합니다. 새 AllJoynBusAttachment을 만들고, 해당 AllJoynBusAttachment를 사용 하 여 생산자를 초기화 하 고, 생산자에 대해 새로 만든 서비스를 초기화 한 다음 생산자를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="51eeb-226">Creating the producer is straightforward – create a new AllJoynBusAttachment, initialize a producer with that AllJoynBusAttachment, initialize the newly created service for the producer, then start the producer.</span></span>

![AJ_Studio_Code_12](../media/AllJoyn/AJ_Studio_Code_12.png)

<span data-ttu-id="51eeb-228">서비스에는 대부분의 논리가 포함 되어 있기 때문에 구현할 수 있는 주요 기능은 속성 변경에 대 한 신호를 보내는 것이 고, 비 상태 이벤트의 경우 불연속 신호를 보내는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="51eeb-228">Since the service contains the majority of the logic, the main functionality left to implement is to send the signals for property changes and discrete signals for non-state events.</span></span>  <span data-ttu-id="51eeb-229">메서드 호출을 통해 필요에 따라 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="51eeb-229">Implement these as necessary through method calls.</span></span>

![AJ_Studio_Code_13](../media/AllJoyn/AJ_Studio_Code_13.png)

<span data-ttu-id="51eeb-231">__자세한 정보__</span><span class="sxs-lookup"><span data-stu-id="51eeb-231">__More Information__</span></span>

<span data-ttu-id="51eeb-232">이 문서의 모든 지침을 제대로 완료 한 경우 앱에서 AllJoyn 코드 작성을 시작할 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="51eeb-232">If you've completed all of the instructions in this document correctly, you are ready to start writing AllJoyn code in your app.</span></span>

<span data-ttu-id="51eeb-233">참조를 위해 Microsoft 샘플 GitHub for [Alljoyn 생산자](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AllJoyn/ProducerExperiences) 및 [alljoyn 소비자](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AllJoyn/ConsumerExperiences)에 대 한 alljoyn 유니버설 Windows 앱 샘플을 확인 하세요.</span><span class="sxs-lookup"><span data-stu-id="51eeb-233">For reference, please look to the AllJoyn Universal Windows Apps samples on the Microsoft Sample GitHub for [AllJoyn Producers](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AllJoyn/ProducerExperiences) and [AllJoyn Consumers](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AllJoyn/ConsumerExperiences).</span></span>

<span data-ttu-id="51eeb-234">AllJoyn 앱을 만드는 방법에 대 한 자세한 연습은 AllJoyn 세션 623을 시청 하세요.</span><span class="sxs-lookup"><span data-stu-id="51eeb-234">For a detailed walkthrough of how to create an AllJoyn app, please watch the AllJoyn session 623:</span></span>

> [!VIDEO https://channel9.msdn.com/Events/Build/2015/2-623/player]

<span data-ttu-id="51eeb-235">Visual Studio에서 직접 배포 되는 경우와 같이 루프백 예외를 사용 하도록 설정 하지 않는 한 동일한 컴퓨터에서 두 UWP 앱 간의 AllJoyn 통신은 Windows 정책에 의해 사용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="51eeb-235">Note that AllJoyn communication between two UWP apps on the same machine is disabled by Windows policy unless they have enabled a loopback exception, such as when being directly deployed from Visual Studio.</span></span>  <span data-ttu-id="51eeb-236">루프백 예외를 사용 하는 방법에 대 한 자세한 내용은 [여기](https://msdn.microsoft.com/library/windows/apps/Hh780593.aspx)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="51eeb-236">For detailed instructions on enabling loopback exemption, see [here](https://msdn.microsoft.com/library/windows/apps/Hh780593.aspx).</span></span>



