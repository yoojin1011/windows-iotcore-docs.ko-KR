---
title: Windows 10 IoT Core 언어 지원
author: msalehmsft
ms.author: msaleh
ms.date: 09/12/2017
ms.topic: article
description: IoT Core에서 UWP 응용 프로그램 및 OS의 여러 언어 지원에 대해 알아봅니다.
keywords: windows iot, 언어, 앱 유형, UWP, OS
ms.openlocfilehash: 5bc44fb090e6e198525e95d6aee6815afd0095da
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918222"
---
# <a name="language-support"></a><span data-ttu-id="0b7cd-104">언어 지원</span><span class="sxs-lookup"><span data-stu-id="0b7cd-104">Language Support</span></span>

<span data-ttu-id="0b7cd-105">언어 지원은 이미지에서 사용할 수 있는 언어 리소스에 따라 응용 프로그램 수준 및 OS 수준에서 사용 하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b7cd-105">Language support can be enabled at two levels, Application level and OS level, depending on the language resources made available on the image.</span></span>

## <a name="languages-in-uwp-applications"></a><span data-ttu-id="0b7cd-106">UWP 응용 프로그램의 언어</span><span class="sxs-lookup"><span data-stu-id="0b7cd-106">Languages in UWP Applications</span></span>
<span data-ttu-id="0b7cd-107">UWP 응용 프로그램 언어는 OS에 포함 된 언어로 국한 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0b7cd-107">UWP application languages are not limited to the languages included in the OS.</span></span>  <span data-ttu-id="0b7cd-108">실제로 셸 UI를 트리거하지 않거나 음성 리소스를 활용 하지 않는 IoT 장치는 기본 Windows 10 IoT Core OS가 en-us 기본 모드에서 간단히 구축 되더라도 UWP 응용 프로그램을 통해 다양 한 언어로 장치 환경을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b7cd-108">In fact, an IoT device that does not trigger shell UI or utilize speech resources can provide a device experience in many different languages through its UWP applications even though the underlying Windows 10 IoT Core OS is built simply in the en-US default mode.</span></span> 

<span data-ttu-id="0b7cd-109">UWP 응용 프로그램은 지원 되는 데 필요한 언어에 대 한 리소스를 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b7cd-109">UWP applications must provide the resources for the languages that are required to be supported.</span></span> <span data-ttu-id="0b7cd-110">[Windows.](https://docs.microsoft.com/uwp/api/windows.globalization.applicationlanguages) r u s e r 언어 api를 사용 하 여 언어 관련 기본 설정을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b7cd-110">[Windows.Globalization.ApplicationLanguage](https://docs.microsoft.com/uwp/api/windows.globalization.applicationlanguages) APIs can be used to specify the language-related preferences.</span></span>

<span data-ttu-id="0b7cd-111">아래 샘플 응용 프로그램을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0b7cd-111">See the below sample applications:</span></span>

* [<span data-ttu-id="0b7cd-112">IoTDefaultApp 샘플</span><span class="sxs-lookup"><span data-stu-id="0b7cd-112">IoTDefaultApp sample</span></span>](https://developer.microsoft.com/en-us/windows/iot/samples/iotdefaultapp)

* [<span data-ttu-id="0b7cd-113">ApplicationResources 샘플</span><span class="sxs-lookup"><span data-stu-id="0b7cd-113">ApplicationResources sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/ApplicationResources)


## <a name="languages-in-os"></a><span data-ttu-id="0b7cd-114">OS 언어</span><span class="sxs-lookup"><span data-stu-id="0b7cd-114">Languages in OS</span></span>

<span data-ttu-id="0b7cd-115">이제 Windows 10 I이상 코어 키트에는 다음 언어에 대 한 언어 리소스가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b7cd-115">Windows 10 IoTCore kits now include the language resources for the following languages:</span></span>

> | <span data-ttu-id="0b7cd-116">언어</span><span class="sxs-lookup"><span data-stu-id="0b7cd-116">Language</span></span>  | <span data-ttu-id="0b7cd-117">Code</span><span class="sxs-lookup"><span data-stu-id="0b7cd-117">Code</span></span> | <span data-ttu-id="0b7cd-118">국가</span><span class="sxs-lookup"><span data-stu-id="0b7cd-118">Region</span></span> |
> |-------------|-----|-----|
> | <span data-ttu-id="0b7cd-119">영어(미국)</span><span class="sxs-lookup"><span data-stu-id="0b7cd-119">English (United States)</span></span> | <span data-ttu-id="0b7cd-120">en-US</span><span class="sxs-lookup"><span data-stu-id="0b7cd-120">en-US</span></span> | <span data-ttu-id="0b7cd-121">북아메리카</span><span class="sxs-lookup"><span data-stu-id="0b7cd-121">North America</span></span> | 
> | <span data-ttu-id="0b7cd-122">영어 (영국)</span><span class="sxs-lookup"><span data-stu-id="0b7cd-122">English (UK)</span></span> | <span data-ttu-id="0b7cd-123">en-GB</span><span class="sxs-lookup"><span data-stu-id="0b7cd-123">en-GB</span></span> | <span data-ttu-id="0b7cd-124">유럽</span><span class="sxs-lookup"><span data-stu-id="0b7cd-124">Europe</span></span> |
> | <span data-ttu-id="0b7cd-125">프랑스어(프랑스)</span><span class="sxs-lookup"><span data-stu-id="0b7cd-125">French (France)</span></span> | <span data-ttu-id="0b7cd-126">fr-FR</span><span class="sxs-lookup"><span data-stu-id="0b7cd-126">fr-FR</span></span> | <span data-ttu-id="0b7cd-127">유럽</span><span class="sxs-lookup"><span data-stu-id="0b7cd-127">Europe</span></span> |
> | <span data-ttu-id="0b7cd-128">프랑스어(캐나다)</span><span class="sxs-lookup"><span data-stu-id="0b7cd-128">French (Canada)</span></span> | <span data-ttu-id="0b7cd-129">fr-CA</span><span class="sxs-lookup"><span data-stu-id="0b7cd-129">fr-CA</span></span> | <span data-ttu-id="0b7cd-130">북아메리카</span><span class="sxs-lookup"><span data-stu-id="0b7cd-130">North America</span></span> |
> | <span data-ttu-id="0b7cd-131">스페인어(스페인)</span><span class="sxs-lookup"><span data-stu-id="0b7cd-131">Spanish (Spain)</span></span> | <span data-ttu-id="0b7cd-132">es-ES</span><span class="sxs-lookup"><span data-stu-id="0b7cd-132">es-ES</span></span> | <span data-ttu-id="0b7cd-133">유럽</span><span class="sxs-lookup"><span data-stu-id="0b7cd-133">Europe</span></span> |
> | <span data-ttu-id="0b7cd-134">스페인어(멕시코)</span><span class="sxs-lookup"><span data-stu-id="0b7cd-134">Spanish (Mexico)</span></span> | <span data-ttu-id="0b7cd-135">es-MX</span><span class="sxs-lookup"><span data-stu-id="0b7cd-135">es-MX</span></span> | <span data-ttu-id="0b7cd-136">북아메리카</span><span class="sxs-lookup"><span data-stu-id="0b7cd-136">North America</span></span> |
> | <span data-ttu-id="0b7cd-137">중국어</span><span class="sxs-lookup"><span data-stu-id="0b7cd-137">Chinese</span></span> | <span data-ttu-id="0b7cd-138">zh-CN</span><span class="sxs-lookup"><span data-stu-id="0b7cd-138">zh-CN</span></span> | <span data-ttu-id="0b7cd-139">아시아</span><span class="sxs-lookup"><span data-stu-id="0b7cd-139">Asia</span></span> | 
> | <span data-ttu-id="0b7cd-140">아랍어</span><span class="sxs-lookup"><span data-stu-id="0b7cd-140">Arabic</span></span> | <span data-ttu-id="0b7cd-141">ar-SA</span><span class="sxs-lookup"><span data-stu-id="0b7cd-141">ar-SA</span></span> | <span data-ttu-id="0b7cd-142">아시아</span><span class="sxs-lookup"><span data-stu-id="0b7cd-142">Asia</span></span> |
> | <span data-ttu-id="0b7cd-143">독일어</span><span class="sxs-lookup"><span data-stu-id="0b7cd-143">German</span></span> | <span data-ttu-id="0b7cd-144">de-DE</span><span class="sxs-lookup"><span data-stu-id="0b7cd-144">de-DE</span></span> | <span data-ttu-id="0b7cd-145">유럽</span><span class="sxs-lookup"><span data-stu-id="0b7cd-145">Europe</span></span> |
> | <span data-ttu-id="0b7cd-146">이탈리아어</span><span class="sxs-lookup"><span data-stu-id="0b7cd-146">Italian</span></span> | <span data-ttu-id="0b7cd-147">it-IT</span><span class="sxs-lookup"><span data-stu-id="0b7cd-147">it-IT</span></span> | <span data-ttu-id="0b7cd-148">유럽</span><span class="sxs-lookup"><span data-stu-id="0b7cd-148">Europe</span></span> | 
> | <span data-ttu-id="0b7cd-149">일본어</span><span class="sxs-lookup"><span data-stu-id="0b7cd-149">Japanese</span></span> | <span data-ttu-id="0b7cd-150">ja-JP</span><span class="sxs-lookup"><span data-stu-id="0b7cd-150">ja-JP</span></span> | <span data-ttu-id="0b7cd-151">아시아</span><span class="sxs-lookup"><span data-stu-id="0b7cd-151">Asia</span></span> |
> | <span data-ttu-id="0b7cd-152">한국어</span><span class="sxs-lookup"><span data-stu-id="0b7cd-152">Korean</span></span> | <span data-ttu-id="0b7cd-153">ko-KR</span><span class="sxs-lookup"><span data-stu-id="0b7cd-153">ko-KR</span></span> | <span data-ttu-id="0b7cd-154">아시아</span><span class="sxs-lookup"><span data-stu-id="0b7cd-154">Asia</span></span> |
> | <span data-ttu-id="0b7cd-155">네덜란드어</span><span class="sxs-lookup"><span data-stu-id="0b7cd-155">Dutch</span></span> | <span data-ttu-id="0b7cd-156">nl-NL</span><span class="sxs-lookup"><span data-stu-id="0b7cd-156">nl-NL</span></span> | <span data-ttu-id="0b7cd-157">유럽</span><span class="sxs-lookup"><span data-stu-id="0b7cd-157">Europe</span></span> |
> | <span data-ttu-id="0b7cd-158">폴란드어</span><span class="sxs-lookup"><span data-stu-id="0b7cd-158">Polish</span></span> | <span data-ttu-id="0b7cd-159">pl-PL</span><span class="sxs-lookup"><span data-stu-id="0b7cd-159">pl-PL</span></span> | <span data-ttu-id="0b7cd-160">유럽</span><span class="sxs-lookup"><span data-stu-id="0b7cd-160">Europe</span></span> | 
> | <span data-ttu-id="0b7cd-161">루마니아어</span><span class="sxs-lookup"><span data-stu-id="0b7cd-161">Romanian</span></span> | <span data-ttu-id="0b7cd-162">ro-RO</span><span class="sxs-lookup"><span data-stu-id="0b7cd-162">ro-RO</span></span> | <span data-ttu-id="0b7cd-163">유럽</span><span class="sxs-lookup"><span data-stu-id="0b7cd-163">Europe</span></span> |
> | <span data-ttu-id="0b7cd-164">러시아어</span><span class="sxs-lookup"><span data-stu-id="0b7cd-164">Russian</span></span> | <span data-ttu-id="0b7cd-165">ru-RU</span><span class="sxs-lookup"><span data-stu-id="0b7cd-165">ru-RU</span></span> | <span data-ttu-id="0b7cd-166">유럽</span><span class="sxs-lookup"><span data-stu-id="0b7cd-166">Europe</span></span> |
> | <span data-ttu-id="0b7cd-167">그리스어</span><span class="sxs-lookup"><span data-stu-id="0b7cd-167">Greek</span></span> | <span data-ttu-id="0b7cd-168">el-GR</span><span class="sxs-lookup"><span data-stu-id="0b7cd-168">el-GR</span></span> | <span data-ttu-id="0b7cd-169">유럽</span><span class="sxs-lookup"><span data-stu-id="0b7cd-169">Europe</span></span> |
> | <span data-ttu-id="0b7cd-170">포르투갈어 (브라질)</span><span class="sxs-lookup"><span data-stu-id="0b7cd-170">Portugese (Brazil)</span></span> | <span data-ttu-id="0b7cd-171">pt-BR</span><span class="sxs-lookup"><span data-stu-id="0b7cd-171">pt-BR</span></span> | <span data-ttu-id="0b7cd-172">남부 아메리카/유럽</span><span class="sxs-lookup"><span data-stu-id="0b7cd-172">South America/Europe</span></span> |
> | <span data-ttu-id="0b7cd-173">Portuese (포르투갈)</span><span class="sxs-lookup"><span data-stu-id="0b7cd-173">Portuese (Portugal)</span></span> | <span data-ttu-id="0b7cd-174">pt-PT</span><span class="sxs-lookup"><span data-stu-id="0b7cd-174">pt-PT</span></span> | <span data-ttu-id="0b7cd-175">남부 아메리카/유럽</span><span class="sxs-lookup"><span data-stu-id="0b7cd-175">South America/Europe</span></span> |

<span data-ttu-id="0b7cd-176">이러한 언어 리소스에는 UI 문자열, 음성 언어 및 음성 (음성 합성)이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0b7cd-176">These language resources contain UI strings, speech language and voices (speech synthesis).</span></span> <span data-ttu-id="0b7cd-177">이러한 리소스 중 하나 이상을 사용 하 여 Windows IoT 이미지를 빌드할 수 있으며 이미지 시간 동안 지정 해야 하며 나중에 수정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0b7cd-177">Windows IoT images can be built with one or more of these resources and they must be specified during the image time and cannot be modified later.</span></span> <span data-ttu-id="0b7cd-178">UI 언어 관련 리소스는 음성 언어 및 음성 리소스와는 독립적입니다.</span><span class="sxs-lookup"><span data-stu-id="0b7cd-178">Note that UI language related resources are independent than speech language and voice resources.</span></span>

### <a name="specifying-ui-and-speech-resources"></a><span data-ttu-id="0b7cd-179">UI 및 음성 리소스 지정</span><span class="sxs-lookup"><span data-stu-id="0b7cd-179">Specifying UI and Speech resources</span></span> 
<span data-ttu-id="0b7cd-180">OEM 입력 xml 파일에서 필요한 UI 및 음성 언어는 아래와 같이 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0b7cd-180">In the OEM Input xml file, the required UI and speech languages are specified as shown below</span></span>

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


### <a name="specifying-speech-data-resources"></a><span data-ttu-id="0b7cd-181">음성 데이터 리소스 지정</span><span class="sxs-lookup"><span data-stu-id="0b7cd-181">Specifying Speech Data resources</span></span>
<span data-ttu-id="0b7cd-182">OEM 입력 xml 파일에서 필요한 음성 데이터 리소스는 아래와 같이 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0b7cd-182">In the OEM Input xml file, the required speech data resources are specified as shown below,</span></span>

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
> <span data-ttu-id="0b7cd-183">기본적으로 en-us 음성 데이터는 이미지에 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b7cd-183">By default, en-US speech data is included in the image.</span></span>

### <a name="samples"></a><span data-ttu-id="0b7cd-184">샘플</span><span class="sxs-lookup"><span data-stu-id="0b7cd-184">Samples</span></span>
* <span data-ttu-id="0b7cd-185">여러 언어 지원에 대 한 [MultiLangSample](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/MultiLangSample) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0b7cd-185">See [MultiLangSample](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/MultiLangSample) for multiple languages support</span></span>
* <span data-ttu-id="0b7cd-186">대체 언어로 en-us를 사용 하는 [SingleLangSample](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/SingleLangSample) 에 대 한 자세한 내용을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0b7cd-186">See [SingleLangSample](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/SingleLangSample) for fr-FR language with en-US as fallback language.</span></span>
    * <span data-ttu-id="0b7cd-187">부팅 UI 언어가 변경 되 면 `administrator` 계정 이름도 부팅 UI 언어로 번역 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0b7cd-187">Note that when the boot UI language is changed, the `administrator` account name is also translated in the boot UI language.</span></span> <span data-ttu-id="0b7cd-188">따라서 fr-fr에서는 `administrateur`입니다.</span><span class="sxs-lookup"><span data-stu-id="0b7cd-188">So, in fr-FR it is `administrateur`.</span></span> <span data-ttu-id="0b7cd-189">[Oemcustomization 지정 .cmd를](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/SingleLangSample/oemcustomization.cmd) 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0b7cd-189">See [OEMCustomization.cmd](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/SingleLangSample/oemcustomization.cmd)</span></span>

## <a name="changing-user-preferences-language-region-speech-and-voice"></a><span data-ttu-id="0b7cd-190">사용자 기본 설정 변경 (언어, 지역, 음성 및 음성)</span><span class="sxs-lookup"><span data-stu-id="0b7cd-190">Changing user preferences (language, region, speech and voice)</span></span>

<span data-ttu-id="0b7cd-191">UWP 응용 프로그램은 WinRT Api를 사용 하 여 기본적으로 사용 해야 하는 지역, 기본 UI 언어 목록, 음성 언어 및 음성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b7cd-191">UWP application can use WinRT APIs to set the region, preferred UI language list, speech language and voice that should be by default used.</span></span> <span data-ttu-id="0b7cd-192">기본 UI 언어 목록이 설정 되 면 UWP 응용 프로그램은 해당 리소스를 로드 하려고 합니다 (응용 프로그램에서 프로그래밍 방식으로 차단 하지 않는 한).</span><span class="sxs-lookup"><span data-stu-id="0b7cd-192">Once preferred UI language list set, UWP application will try to load the corresponding resources (unless application programmatically prevents that).</span></span>
 
<span data-ttu-id="0b7cd-193">응용 프로그램에 해당 리소스가 없으면 대체 리소스가 로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0b7cd-193">If the application doesn’t have the corresponding resources, then fallback resources will be loaded.</span></span> <span data-ttu-id="0b7cd-194">마찬가지로 기본 설정 언어에 대 한 OS 리소스가 Windows IoT 이미지의 일부가 아닌 경우 Windows IoT는 영어 (en-us)로 대체 되는 대체 항목을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b7cd-194">Similarly, if the OS resources for the preferred languages aren’t part of the Windows IoT image, Windows IoT will use its fallback ones likely English (en-US).</span></span>

* <span data-ttu-id="0b7cd-195">[GlobalizationPreferences](https://docs.microsoft.com/uwp/api/windows.system.userprofile.globalizationpreferences)에서 `TrySetHomeGeographicRegion`를 사용하여 지역 설정</span><span class="sxs-lookup"><span data-stu-id="0b7cd-195">Set region using `TrySetHomeGeographicRegion` in [Windows.System.UserProfile.GlobalizationPreferences](https://docs.microsoft.com/uwp/api/windows.system.userprofile.globalizationpreferences)</span></span>
* <span data-ttu-id="0b7cd-196">[GlobalizationPreferences](https://docs.microsoft.com/uwp/api/windows.system.userprofile.globalizationpreferences)에서 `TrySetLanguages`를 사용하여 UI 언어 설정</span><span class="sxs-lookup"><span data-stu-id="0b7cd-196">Set UI language using `TrySetLanguages` in [Windows.System.UserProfile.GlobalizationPreferences](https://docs.microsoft.com/uwp/api/windows.system.userprofile.globalizationpreferences)</span></span>
* <span data-ttu-id="0b7cd-197">SpeechRecognition에서 `TrySetSystemSpeechLanguageAsync`를 사용 하 여 음성 언어를 설정 합니다. [SpeechRecognizer](https://docs.microsoft.com/uwp/api/windows.media.speechrecognition.speechrecognizer)</span><span class="sxs-lookup"><span data-stu-id="0b7cd-197">Set speech language using `TrySetSystemSpeechLanguageAsync` in [Windows.Media.SpeechRecognition.SpeechRecognizer](https://docs.microsoft.com/uwp/api/windows.media.speechrecognition.speechrecognizer)</span></span>
* <span data-ttu-id="0b7cd-198">SpeechSynthesis에서 `TrySetDefaultVoiceAsync`를 사용 하 여 음성 설정 [SpeechSynthesizer](https://docs.microsoft.com/en-us/uwp/api/windows.media.speechsynthesis.speechsynthesizer)</span><span class="sxs-lookup"><span data-stu-id="0b7cd-198">Set voice using `TrySetDefaultVoiceAsync` in [Windows.Media.SpeechSynthesis.SpeechSynthesizer](https://docs.microsoft.com/en-us/uwp/api/windows.media.speechsynthesis.speechsynthesizer)</span></span>

> [!NOTE]
> <span data-ttu-id="0b7cd-199">적절 한 기능을 제공 하기 위해 Cortana를 사용 하려면 지역, ui 언어 및 음성 언어를 일관 되 게 사용 해야 합니다 (예: 지역 FR, UI 및 음성 언어 fr-fr 또는 지역 ES, UI 및 음성 언어 es).</span><span class="sxs-lookup"><span data-stu-id="0b7cd-199">For proper functioning, Cortana requires the region, UI language and speech language to be consistent, e.g.: region FR, UI and speech languages fr-FR or region ES, UI and speech languages es-ES.</span></span> <span data-ttu-id="0b7cd-200">Cortana는 자체 음성을 사용 하 고 UWP 응용 프로그램은 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0b7cd-200">Cortana uses its own voice, UWP application cannot change it.</span></span>

## <a name="iotsettingsexe"></a><span data-ttu-id="0b7cd-201">IoTSettings .exe</span><span class="sxs-lookup"><span data-stu-id="0b7cd-201">IoTSettings.exe</span></span>

<span data-ttu-id="0b7cd-202">Cortana 사용 제품을 빌드하기 위한 지역 및 사용자 또는 음성 언어 설정을 변경 하는 방법에 대해 자세히 알아보려면 [명령줄 유틸리티](../manage-your-device/CommandLineUtils.md) 설명서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0b7cd-202">To learn more about changing settings for region and user or speech language to build Cortana enabled products, please read our [Command Line Utils](../manage-your-device/CommandLineUtils.md) documentation.</span></span>
