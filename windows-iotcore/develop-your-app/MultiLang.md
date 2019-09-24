---
title: Windows 10 IoT Core 언어 지원
author: msalehmsft
ms.author: msaleh
ms.date: 09/12/17
ms.topic: article
description: IoT Core에서 UWP 응용 프로그램 및 OS의 여러 언어 지원에 대해 알아봅니다.
keywords: windows iot, 언어, 앱 유형, UWP, OS
ms.openlocfilehash: aad3005a008264223750b7ede5b154306d9d3015
ms.sourcegitcommit: b005de492d52cd5139fa410dd31c3ca369030dd9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/16/2019
ms.locfileid: "69545523"
---
# <a name="language-support"></a>언어 지원

언어 지원은 이미지에서 사용할 수 있는 언어 리소스에 따라 응용 프로그램 수준 및 OS 수준에서 사용 하도록 설정할 수 있습니다.

## <a name="languages-in-uwp-applications"></a>UWP 응용 프로그램의 언어
UWP 응용 프로그램 언어는 OS에 포함 된 언어로 국한 되지 않습니다.  실제로 셸 UI를 트리거하지 않거나 음성 리소스를 활용 하지 않는 IoT 장치는 기본 Windows 10 IoT Core OS가 en-us 기본 모드에서 간단히 구축 되더라도 UWP 응용 프로그램을 통해 다양 한 언어로 장치 환경을 제공할 수 있습니다. 

UWP 응용 프로그램은 지원 되는 데 필요한 언어에 대 한 리소스를 제공 해야 합니다. [Windows.](https://docs.microsoft.com/uwp/api/windows.globalization.applicationlanguages) r u s e r 언어 api를 사용 하 여 언어 관련 기본 설정을 지정할 수 있습니다.

아래 샘플 응용 프로그램을 참조 하세요.

* [IoTDefaultApp 샘플](https://developer.microsoft.com/en-us/windows/iot/samples/iotdefaultapp)

* [ApplicationResources 샘플](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/ApplicationResources)


## <a name="languages-in-os"></a>OS 언어

이제 Windows 10 I이상 코어 키트에는 다음 언어에 대 한 언어 리소스가 포함 되어 있습니다.

> | 언어  | 코드 | Region |
> |-------------|-----|-----|
> | 영어 (미국) | ko-KR | North America | 
> | 영어 (영국) | en-GB | Europe |
> | 프랑스어 (프랑스) | fr-FR | Europe |
> | 프랑스어(캐나다) | fr-CA | North America |
> | 스페인어(스페인) | es-ES | Europe |
> | 스페인어(멕시코) | es-MX | North America |
> | 중국어 | zh-CN | 아시아 | 
> | 아랍어 | ar-SA | 아시아 |
> | 독일어 | de-DE | Europe |
> | 이탈리아어 | it-IT | Europe | 
> | 일본어 | ja-JP | 아시아 |
> | 한국어 | ko-KR | 아시아 |
> | 네덜란드어 | nl-NL | Europe |
> | 폴란드어 | pl-PL | Europe | 
> | 루마니아어 | ro-RO | Europe |
> | 러시아어 | ru-RU | Europe |
> | 그리스어 | el-GR | Europe |
> | 포르투갈어 (브라질) | pt-BR | 남부 아메리카/유럽 |
> | Portuese (포르투갈) | pt-PT | 남부 아메리카/유럽 |

이러한 언어 리소스에는 UI 문자열, 음성 언어 및 음성 (음성 합성)이 포함 됩니다. 이러한 리소스 중 하나 이상을 사용 하 여 Windows IoT 이미지를 빌드할 수 있으며 이미지 시간 동안 지정 해야 하며 나중에 수정할 수 없습니다. UI 언어 관련 리소스는 음성 언어 및 음성 리소스와는 독립적입니다.

### <a name="specifying-ui-and-speech-resources"></a>UI 및 음성 리소스 지정 
OEM 입력 xml 파일에서 필요한 UI 및 음성 언어는 아래와 같이 지정 됩니다.

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


### <a name="specifying-speech-data-resources"></a>음성 데이터 리소스 지정
OEM 입력 xml 파일에서 필요한 음성 데이터 리소스는 아래와 같이 지정 됩니다.

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
> 기본적으로 en-us 음성 데이터는 이미지에 포함 되어 있습니다.

### <a name="samples"></a>샘플
* 여러 언어 지원에 대 한 [MultiLangSample](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/MultiLangSample) 를 참조 하세요.
* 대체 언어로 en-us를 사용 하는 [SingleLangSample](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/SingleLangSample) 에 대 한 자세한 내용을 참조 하세요.
    * 부팅 ui 언어가 변경 `administrator` 되 면 계정 이름도 부팅 ui 언어로 번역 됩니다. 따라서 fr-fr은 `administrateur`입니다. [Oemcustomization 지정 .cmd를](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/SingleLangSample/oemcustomization.cmd) 참조 하세요.

## <a name="changing-user-preferences-language-region-speech-and-voice"></a>사용자 기본 설정 변경 (언어, 지역, 음성 및 음성)

UWP 응용 프로그램은 WinRT Api를 사용 하 여 기본적으로 사용 해야 하는 지역, 기본 UI 언어 목록, 음성 언어 및 음성을 설정할 수 있습니다. 기본 UI 언어 목록이 설정 되 면 UWP 응용 프로그램은 해당 리소스를 로드 하려고 합니다 (응용 프로그램에서 프로그래밍 방식으로 차단 하지 않는 한).
 
응용 프로그램에 해당 리소스가 없으면 대체 리소스가 로드 됩니다. 마찬가지로 기본 설정 언어에 대 한 OS 리소스가 Windows IoT 이미지의 일부가 아닌 경우 Windows IoT는 영어 (en-us)로 대체 되는 대체 항목을 사용 합니다.

* [GlobalizationPreferences](https://docs.microsoft.com/uwp/api/windows.system.userprofile.globalizationpreferences)에서 `TrySetHomeGeographicRegion`를 사용하여 지역 설정
* [GlobalizationPreferences](https://docs.microsoft.com/uwp/api/windows.system.userprofile.globalizationpreferences)에서 `TrySetLanguages`를 사용하여 UI 언어 설정
* SpeechRecognition에서를 사용 `TrySetSystemSpeechLanguageAsync` 하 여 음성 언어를 설정 합니다. [SpeechRecognizer](https://docs.microsoft.com/uwp/api/windows.media.speechrecognition.speechrecognizer)
* SpeechSynthesis에서 음성 `TrySetDefaultVoiceAsync` 사용을 설정 합니다. [SpeechSynthesizer](https://docs.microsoft.com/en-us/uwp/api/windows.media.speechsynthesis.speechsynthesizer)

> [!NOTE]
> 적절 한 기능을 제공 하기 위해 Cortana를 사용 하려면 지역, ui 언어 및 음성 언어를 일관 되 게 사용 해야 합니다 (예: 지역 FR, UI 및 음성 언어 fr-fr 또는 지역 ES, UI 및 음성 언어 es). Cortana는 자체 음성을 사용 하 고 UWP 응용 프로그램은 변경할 수 없습니다.

## <a name="iotsettingsexe"></a>IoTSettings .exe

Cortana 사용 제품을 빌드하기 위한 지역 및 사용자 또는 음성 언어 설정을 변경 하는 방법에 대해 자세히 알아보려면 [명령줄 유틸리티](../manage-your-device/CommandLineUtils.md) 설명서를 참조 하세요.
