---
title: Windows 10 IoT Core 언어 지원
author: msalehmsft
ms.author: msaleh
ms.date: 09/12/17
ms.topic: article
description: UWP 응용 프로그램 및 IoT Core에는 OS의 다중 언어 지원에 알아봅니다.
keywords: windows iot, 언어, UWP, OS 앱 형식
ms.openlocfilehash: 211ed2ee8350d8c92d6f959f8d9e7b5d6f567af7
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512389"
---
# <a name="language-support"></a><span data-ttu-id="a0e53-104">언어 지원</span><span class="sxs-lookup"><span data-stu-id="a0e53-104">Language Support</span></span>

<span data-ttu-id="a0e53-105">두 개의 수준, 응용 프로그램 수준 및 이미지에서 사용할 수 있는 언어 리소스에 따라 OS 수준에서 언어 지원을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a0e53-105">Language support can be enabled at two levels, Application level and OS level, depending on the language resources made available on the image.</span></span>

## <a name="languages-in-uwp-applications"></a><span data-ttu-id="a0e53-106">UWP 응용 프로그램의 언어</span><span class="sxs-lookup"><span data-stu-id="a0e53-106">Languages in UWP Applications</span></span>
<span data-ttu-id="a0e53-107">UWP 응용 프로그램 언어 OS에 포함 된 언어에 제한 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a0e53-107">UWP application languages are not limited to the languages included in the OS.</span></span>  <span data-ttu-id="a0e53-108">사실, 셸 UI를 트리거할 되지 않거나 음성 리소스를 활용 하는 IoT 장치 EN-US 기본 모드에 있는 기본 Windows 10 IoT Core OS 빌드되는 경우에 해당 UWP 응용 프로그램을 통해 여러 다른 언어에 장치 환경을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a0e53-108">In fact, an IoT device that does not trigger shell UI or utilize speech resources can provide a device experience in many different languages through its UWP applications even though the underlying Windows 10 IoT Core OS is built simply in the en-US default mode.</span></span> 

<span data-ttu-id="a0e53-109">UWP 응용 프로그램은 지원 되는 데 필요한 언어에 대 한 리소스를 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0e53-109">UWP applications must provide the resources for the languages that are required to be supported.</span></span> <span data-ttu-id="a0e53-110">[Windows.Globalization.ApplicationLanguage](https://docs.microsoft.com/uwp/api/windows.globalization.applicationlanguages) 언어 관련 기본 설정을 지정 하려면 Api를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a0e53-110">[Windows.Globalization.ApplicationLanguage](https://docs.microsoft.com/uwp/api/windows.globalization.applicationlanguages) APIs can be used to specify the language-related preferences.</span></span>

<span data-ttu-id="a0e53-111">참조는 아래 샘플 응용 프로그램:</span><span class="sxs-lookup"><span data-stu-id="a0e53-111">See the below sample applications:</span></span>

* [<span data-ttu-id="a0e53-112">IoTDefaultApp 샘플</span><span class="sxs-lookup"><span data-stu-id="a0e53-112">IoTDefaultApp sample</span></span>](https://developer.microsoft.com/en-us/windows/iot/samples/iotdefaultapp)

* [<span data-ttu-id="a0e53-113">ApplicationResources 샘플</span><span class="sxs-lookup"><span data-stu-id="a0e53-113">ApplicationResources sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/ApplicationResources)


## <a name="languages-in-os"></a><span data-ttu-id="a0e53-114">OS 언어</span><span class="sxs-lookup"><span data-stu-id="a0e53-114">Languages in OS</span></span>

<span data-ttu-id="a0e53-115">Windows 10 IoTCore 키트에는 이제 다음 언어에 대 한 언어 리소스가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a0e53-115">Windows 10 IoTCore kits now include the language resources for the following languages:</span></span>

> | <span data-ttu-id="a0e53-116">언어</span><span class="sxs-lookup"><span data-stu-id="a0e53-116">Language</span></span>  | <span data-ttu-id="a0e53-117">코드</span><span class="sxs-lookup"><span data-stu-id="a0e53-117">Code</span></span> | <span data-ttu-id="a0e53-118">Region</span><span class="sxs-lookup"><span data-stu-id="a0e53-118">Region</span></span> |
> |-------------|-----|-----|
> | <span data-ttu-id="a0e53-119">영어 (미국)</span><span class="sxs-lookup"><span data-stu-id="a0e53-119">English (United States)</span></span> | <span data-ttu-id="a0e53-120">ko-KR</span><span class="sxs-lookup"><span data-stu-id="a0e53-120">en-US</span></span> | <span data-ttu-id="a0e53-121">North America</span><span class="sxs-lookup"><span data-stu-id="a0e53-121">North America</span></span> | 
> | <span data-ttu-id="a0e53-122">영어 (영국)</span><span class="sxs-lookup"><span data-stu-id="a0e53-122">English (UK)</span></span> | <span data-ttu-id="a0e53-123">en-GB</span><span class="sxs-lookup"><span data-stu-id="a0e53-123">en-GB</span></span> | <span data-ttu-id="a0e53-124">Europe</span><span class="sxs-lookup"><span data-stu-id="a0e53-124">Europe</span></span> |
> | <span data-ttu-id="a0e53-125">프랑스어 (프랑스)</span><span class="sxs-lookup"><span data-stu-id="a0e53-125">French (France)</span></span> | <span data-ttu-id="a0e53-126">fr-FR</span><span class="sxs-lookup"><span data-stu-id="a0e53-126">fr-FR</span></span> | <span data-ttu-id="a0e53-127">Europe</span><span class="sxs-lookup"><span data-stu-id="a0e53-127">Europe</span></span> |
> | <span data-ttu-id="a0e53-128">프랑스어(캐나다)</span><span class="sxs-lookup"><span data-stu-id="a0e53-128">French (Canada)</span></span> | <span data-ttu-id="a0e53-129">fr-CA</span><span class="sxs-lookup"><span data-stu-id="a0e53-129">fr-CA</span></span> | <span data-ttu-id="a0e53-130">North America</span><span class="sxs-lookup"><span data-stu-id="a0e53-130">North America</span></span> |
> | <span data-ttu-id="a0e53-131">스페인어(스페인)</span><span class="sxs-lookup"><span data-stu-id="a0e53-131">Spanish (Spain)</span></span> | <span data-ttu-id="a0e53-132">es-ES</span><span class="sxs-lookup"><span data-stu-id="a0e53-132">es-ES</span></span> | <span data-ttu-id="a0e53-133">Europe</span><span class="sxs-lookup"><span data-stu-id="a0e53-133">Europe</span></span> |
> | <span data-ttu-id="a0e53-134">스페인어(멕시코)</span><span class="sxs-lookup"><span data-stu-id="a0e53-134">Spanish (Mexico)</span></span> | <span data-ttu-id="a0e53-135">es-MX</span><span class="sxs-lookup"><span data-stu-id="a0e53-135">es-MX</span></span> | <span data-ttu-id="a0e53-136">North America</span><span class="sxs-lookup"><span data-stu-id="a0e53-136">North America</span></span> |
> | <span data-ttu-id="a0e53-137">중국어</span><span class="sxs-lookup"><span data-stu-id="a0e53-137">Chinese</span></span> | <span data-ttu-id="a0e53-138">zh-CN</span><span class="sxs-lookup"><span data-stu-id="a0e53-138">zh-CN</span></span> | <span data-ttu-id="a0e53-139">아시아</span><span class="sxs-lookup"><span data-stu-id="a0e53-139">Asia</span></span> | 
> | <span data-ttu-id="a0e53-140">아랍어</span><span class="sxs-lookup"><span data-stu-id="a0e53-140">Arabic</span></span> | <span data-ttu-id="a0e53-141">ar-SA</span><span class="sxs-lookup"><span data-stu-id="a0e53-141">ar-SA</span></span> | <span data-ttu-id="a0e53-142">아시아</span><span class="sxs-lookup"><span data-stu-id="a0e53-142">Asia</span></span> |
> | <span data-ttu-id="a0e53-143">독일어</span><span class="sxs-lookup"><span data-stu-id="a0e53-143">German</span></span> | <span data-ttu-id="a0e53-144">de-DE</span><span class="sxs-lookup"><span data-stu-id="a0e53-144">de-DE</span></span> | <span data-ttu-id="a0e53-145">Europe</span><span class="sxs-lookup"><span data-stu-id="a0e53-145">Europe</span></span> |
> | <span data-ttu-id="a0e53-146">이탈리아어</span><span class="sxs-lookup"><span data-stu-id="a0e53-146">Italian</span></span> | <span data-ttu-id="a0e53-147">it-IT</span><span class="sxs-lookup"><span data-stu-id="a0e53-147">it-IT</span></span> | <span data-ttu-id="a0e53-148">Europe</span><span class="sxs-lookup"><span data-stu-id="a0e53-148">Europe</span></span> | 
> | <span data-ttu-id="a0e53-149">일본어</span><span class="sxs-lookup"><span data-stu-id="a0e53-149">Japanese</span></span> | <span data-ttu-id="a0e53-150">ja-JP</span><span class="sxs-lookup"><span data-stu-id="a0e53-150">ja-JP</span></span> | <span data-ttu-id="a0e53-151">아시아</span><span class="sxs-lookup"><span data-stu-id="a0e53-151">Asia</span></span> |
> | <span data-ttu-id="a0e53-152">한국어</span><span class="sxs-lookup"><span data-stu-id="a0e53-152">Korean</span></span> | <span data-ttu-id="a0e53-153">ko-KR</span><span class="sxs-lookup"><span data-stu-id="a0e53-153">ko-KR</span></span> | <span data-ttu-id="a0e53-154">아시아</span><span class="sxs-lookup"><span data-stu-id="a0e53-154">Asia</span></span> |
> | <span data-ttu-id="a0e53-155">네덜란드어</span><span class="sxs-lookup"><span data-stu-id="a0e53-155">Dutch</span></span> | <span data-ttu-id="a0e53-156">nl-NL</span><span class="sxs-lookup"><span data-stu-id="a0e53-156">nl-NL</span></span> | <span data-ttu-id="a0e53-157">Europe</span><span class="sxs-lookup"><span data-stu-id="a0e53-157">Europe</span></span> |
> | <span data-ttu-id="a0e53-158">폴란드어</span><span class="sxs-lookup"><span data-stu-id="a0e53-158">Polish</span></span> | <span data-ttu-id="a0e53-159">pl-PL</span><span class="sxs-lookup"><span data-stu-id="a0e53-159">pl-PL</span></span> | <span data-ttu-id="a0e53-160">Europe</span><span class="sxs-lookup"><span data-stu-id="a0e53-160">Europe</span></span> | 
> | <span data-ttu-id="a0e53-161">루마니아어</span><span class="sxs-lookup"><span data-stu-id="a0e53-161">Romanian</span></span> | <span data-ttu-id="a0e53-162">ro-RO</span><span class="sxs-lookup"><span data-stu-id="a0e53-162">ro-RO</span></span> | <span data-ttu-id="a0e53-163">Europe</span><span class="sxs-lookup"><span data-stu-id="a0e53-163">Europe</span></span> |
> | <span data-ttu-id="a0e53-164">러시아어</span><span class="sxs-lookup"><span data-stu-id="a0e53-164">Russian</span></span> | <span data-ttu-id="a0e53-165">ro-RU</span><span class="sxs-lookup"><span data-stu-id="a0e53-165">ro-RU</span></span> | <span data-ttu-id="a0e53-166">Europe</span><span class="sxs-lookup"><span data-stu-id="a0e53-166">Europe</span></span> |
> | <span data-ttu-id="a0e53-167">그리스어</span><span class="sxs-lookup"><span data-stu-id="a0e53-167">Greek</span></span> | <span data-ttu-id="a0e53-168">el-GR</span><span class="sxs-lookup"><span data-stu-id="a0e53-168">el-GR</span></span> | <span data-ttu-id="a0e53-169">Europe</span><span class="sxs-lookup"><span data-stu-id="a0e53-169">Europe</span></span> |
> | <span data-ttu-id="a0e53-170">포르투갈어 (브라질)</span><span class="sxs-lookup"><span data-stu-id="a0e53-170">Portugese (Brazil)</span></span> | <span data-ttu-id="a0e53-171">pt-BR</span><span class="sxs-lookup"><span data-stu-id="a0e53-171">pt-BR</span></span> | <span data-ttu-id="a0e53-172">남아메리카 유럽</span><span class="sxs-lookup"><span data-stu-id="a0e53-172">South America/Europe</span></span> |
> | <span data-ttu-id="a0e53-173">Portuese (포르투갈)</span><span class="sxs-lookup"><span data-stu-id="a0e53-173">Portuese (Portugal)</span></span> | <span data-ttu-id="a0e53-174">pt-PR</span><span class="sxs-lookup"><span data-stu-id="a0e53-174">pt-PR</span></span> | <span data-ttu-id="a0e53-175">남아메리카 유럽</span><span class="sxs-lookup"><span data-stu-id="a0e53-175">South America/Europe</span></span> |

<span data-ttu-id="a0e53-176">이러한 언어 리소스 UI 문자열, 음성 언어 및 음성 (음성 합성)를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0e53-176">These language resources contain UI strings, speech language and voices (speech synthesis).</span></span> <span data-ttu-id="a0e53-177">이러한 리소스 중 하나 이상을 사용 하 여 Windows IoT 이미지를 빌드할 수 있습니다 및 이미지 시간 동안 지정 해야 하며 나중에 수정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a0e53-177">Windows IoT images can be built with one or more of these resources and they must be specified during the image time and cannot be modified later.</span></span> <span data-ttu-id="a0e53-178">UI 언어 관련 리소스 음성 언어와 독립적 이며 리소스 음성는 note 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0e53-178">Note that UI language related resources are independent than speech language and voice resources.</span></span>

### <a name="specifying-ui-and-speech-resources"></a><span data-ttu-id="a0e53-179">UI 및 음성 리소스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a0e53-179">Specifying UI and Speech resources</span></span> 
<span data-ttu-id="a0e53-180">아래와 같이 OEM 입력 xml 파일의 필요한 UI 및 음성 언어를 지정 된</span><span class="sxs-lookup"><span data-stu-id="a0e53-180">In the OEM Input xml file, the required UI and speech languages are specified as shown below</span></span>

``` xml
  <SupportedLanguages>
    <UserInterface>
      <Language>en-US</Language>
      <Language>en-GB</Language> 
      <Language>fr-CA</Language> 
      <Language>es-MX</Language> 
      <Language>es-ES</Language> 
      <Language>fr-FR</Language>
    </UserInterface>
    <Keyboard>
      <Language>en-US</Language>
      <Language>en-GB</Language> 
      <Language>fr-CA</Language> 
      <Language>es-MX</Language> 
      <Language>es-ES</Language> 
      <Language>fr-FR</Language>
    </Keyboard>
    <Speech>
      <Language>en-US</Language>
      <Language>en-GB</Language> 
      <Language>fr-CA</Language> 
      <Language>es-MX</Language> 
      <Language>es-ES</Language> 
      <Language>fr-FR</Language>
    </Speech>
  </SupportedLanguages>
  <BootUILanguage>en-us</BootUILanguage>
  <BootLocale>en-us</BootLocale>
```


### <a name="specifying-speech-data-resources"></a><span data-ttu-id="a0e53-181">음성 데이터 리소스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a0e53-181">Specifying Speech Data resources</span></span>
<span data-ttu-id="a0e53-182">OEM 입력 xml 파일에서 필요한 음성 데이터 리소스는 아래와 같이 지정</span><span class="sxs-lookup"><span data-stu-id="a0e53-182">In the OEM Input xml file, the required speech data resources are specified as shown below,</span></span>

``` xml
    <Microsoft>
       ...
      <Feature>IOT_SPEECHDATA_EN_CA</Feature>
      <Feature>IOT_SPEECHDATA_ES_MX</Feature> 
      <Feature>IOT_SPEECHDATA_FR_CA</Feature> 
      <Feature>IOT_SPEECHDATA_EN_GB</Feature>
      <Feature>IOT_SPEECHDATA_ES_ES</Feature>  
      <Feature>IOT_SPEECHDATA_FR_FR</Feature> 
    </Microsoft>
```

> [!NOTE]
> <span data-ttu-id="a0e53-183">기본적으로 EN-US 음성 데이터가 이미지에 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a0e53-183">By default, en-US speech data is included in the image.</span></span>

### <a name="samples"></a><span data-ttu-id="a0e53-184">샘플</span><span class="sxs-lookup"><span data-stu-id="a0e53-184">Samples</span></span>
* <span data-ttu-id="a0e53-185">참조 [MultiLangSample](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/MultiLangSample) 여러 언어 지원</span><span class="sxs-lookup"><span data-stu-id="a0e53-185">See [MultiLangSample](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/MultiLangSample) for multiple languages support</span></span>
* <span data-ttu-id="a0e53-186">참조 [SingleLangSample](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/SingleLangSample) EN-US 대체 언어를 사용 하 여 FR-FR 언어에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0e53-186">See [SingleLangSample](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/SingleLangSample) for fr-FR language with en-US as fallback language.</span></span>
    * <span data-ttu-id="a0e53-187">부팅 하는 UI 언어 변경 되 면 사용자에 게 유의 합니다 `administrator` 부팅 UI 언어에서에서 계정 이름을 변환도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a0e53-187">Note that when the boot UI language is changed, the `administrator` account name is also translated in the boot UI language.</span></span> <span data-ttu-id="a0e53-188">따라서-FR에서는 `administrateur`합니다.</span><span class="sxs-lookup"><span data-stu-id="a0e53-188">So, in fr-FR it is `administrateur`.</span></span> <span data-ttu-id="a0e53-189">참조 [OEMCustomization.cmd](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/SingleLangSample/oemcustomization.cmd)</span><span class="sxs-lookup"><span data-stu-id="a0e53-189">See [OEMCustomization.cmd](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/SingleLangSample/oemcustomization.cmd)</span></span>

## <a name="changing-user-preferences-language-region-speech-and-voice"></a><span data-ttu-id="a0e53-190">사용자 기본 설정 (예: 언어, 지역, 음성 및 음성)를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="a0e53-190">Changing user preferences (language, region, speech and voice)</span></span>

<span data-ttu-id="a0e53-191">UWP 응용 프로그램 WinRT Api를 사용 하 여 지역, 기본 설정된 UI 언어 목록, 음성 언어 및 음성 기본적으로 사용 해야 하는 설정 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a0e53-191">UWP application can use WinRT APIs to set the region, preferred UI language list, speech language and voice that should be by default used.</span></span> <span data-ttu-id="a0e53-192">한 번 기본 설정된 UI 언어 목록 집합 UWP 응용 프로그램 (하지 않는 한 응용 프로그램을 방지 하는 프로그래밍 방식으로) 해당 리소스를 로드 하려고 시도 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0e53-192">Once preferred UI language list set, UWP application will try to load the corresponding resources (unless application programmatically prevents that).</span></span>
 
<span data-ttu-id="a0e53-193">응용 프로그램이 해당 리소스에 없는 경우 대체 (fallback) 리소스가 로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a0e53-193">If the application doesn’t have the corresponding resources, then fallback resources will be loaded.</span></span> <span data-ttu-id="a0e53-194">마찬가지로, 기본 설정된 언어에 대 한 해당 OS 리소스가 Windows IoT 이미지의 일부로 없는 경우 Windows IoT를 사용 하 여 해당 대체 항목 가능성이 영어 (EN-US).</span><span class="sxs-lookup"><span data-stu-id="a0e53-194">Similarly, if the OS resources for the preferred languages aren’t part of the Windows IoT image, Windows IoT will use its fallback ones likely English (en-US).</span></span>

* <span data-ttu-id="a0e53-195">사용 하 여 영역 설정 `TrySetHomeGeographicRegion` 에서 [Windows.System.UserProfile.GlobalizationPreferences](https://docs.microsoft.com/uwp/api/windows.system.userprofile.globalizationpreferences)</span><span class="sxs-lookup"><span data-stu-id="a0e53-195">Set region using `TrySetHomeGeographicRegion` in [Windows.System.UserProfile.GlobalizationPreferences](https://docs.microsoft.com/uwp/api/windows.system.userprofile.globalizationpreferences)</span></span>
* <span data-ttu-id="a0e53-196">사용 하 여 설정 UI 언어 `TrySetLanguages` 에서 [Windows.System.UserProfile.GlobalizationPreferences](https://docs.microsoft.com/uwp/api/windows.system.userprofile.globalizationpreferences)</span><span class="sxs-lookup"><span data-stu-id="a0e53-196">Set UI language using `TrySetLanguages` in [Windows.System.UserProfile.GlobalizationPreferences](https://docs.microsoft.com/uwp/api/windows.system.userprofile.globalizationpreferences)</span></span>
* <span data-ttu-id="a0e53-197">사용 하 여 집합 음성 언어 `TrySetSystemSpeechLanguageAsync` 에서 [Windows.Media.SpeechRecognition.SpeechRecognizer](https://docs.microsoft.com/uwp/api/windows.media.speechrecognition.speechrecognizer)</span><span class="sxs-lookup"><span data-stu-id="a0e53-197">Set speech language using `TrySetSystemSpeechLanguageAsync` in [Windows.Media.SpeechRecognition.SpeechRecognizer](https://docs.microsoft.com/uwp/api/windows.media.speechrecognition.speechrecognizer)</span></span>
* <span data-ttu-id="a0e53-198">음성을 사용 하 여 설정할 `TrySetDefaultVoiceAsync` 에서 [Windows.Media.SpeechSynthesis.SpeechSynthesizer](https://docs.microsoft.com/en-us/uwp/api/windows.media.speechsynthesis.speechsynthesizer)</span><span class="sxs-lookup"><span data-stu-id="a0e53-198">Set voice using `TrySetDefaultVoiceAsync` in [Windows.Media.SpeechSynthesis.SpeechSynthesizer](https://docs.microsoft.com/en-us/uwp/api/windows.media.speechsynthesis.speechsynthesizer)</span></span>

> [!NOTE]
> <span data-ttu-id="a0e53-199">적절 하 게 작동 하는 것에 대 한 Cortana 필요 지역, UI 언어와 일관 되어야 예: 음성 언어: 지역 FR, UI 및 음성 언어-FR 또는 지역 ES, UI 및 음성 언어 ES-ES 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0e53-199">For proper functioning, Cortana requires the region, UI language and speech language to be consistent, e.g.: region FR, UI and speech languages fr-FR or region ES, UI and speech languages es-ES.</span></span> <span data-ttu-id="a0e53-200">Cortana 음성 자체를 사용 하 여, UWP 응용 프로그램에서 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a0e53-200">Cortana uses its own voice, UWP application cannot change it.</span></span>

## <a name="iotsettingsexe"></a><span data-ttu-id="a0e53-201">IoTSettings.exe</span><span class="sxs-lookup"><span data-stu-id="a0e53-201">IoTSettings.exe</span></span>

<span data-ttu-id="a0e53-202">지역 및 사용자 또는 사용 하도록 설정 하는 Cortana 제품을 빌드할 음성 언어에 대 한 설정을 변경 하는 방법에 대 한 자세한 내용은 읽어보세요 우리의 [명령줄 유틸리티](../manage-your-device/CommandLineUtils.md) 설명서.</span><span class="sxs-lookup"><span data-stu-id="a0e53-202">To learn more about changing settings for region and user or speech language to build Cortana enabled products, please read our [Command Line Utils](../manage-your-device/CommandLineUtils.md) documentation.</span></span>
