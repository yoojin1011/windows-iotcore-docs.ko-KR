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
# <a name="language-support"></a>언어 지원

두 개의 수준, 응용 프로그램 수준 및 이미지에서 사용할 수 있는 언어 리소스에 따라 OS 수준에서 언어 지원을 사용할 수 있습니다.

## <a name="languages-in-uwp-applications"></a>UWP 응용 프로그램의 언어
UWP 응용 프로그램 언어 OS에 포함 된 언어에 제한 되지 않습니다.  사실, 셸 UI를 트리거할 되지 않거나 음성 리소스를 활용 하는 IoT 장치 EN-US 기본 모드에 있는 기본 Windows 10 IoT Core OS 빌드되는 경우에 해당 UWP 응용 프로그램을 통해 여러 다른 언어에 장치 환경을 제공할 수 있습니다. 

UWP 응용 프로그램은 지원 되는 데 필요한 언어에 대 한 리소스를 제공 해야 합니다. [Windows.Globalization.ApplicationLanguage](https://docs.microsoft.com/uwp/api/windows.globalization.applicationlanguages) 언어 관련 기본 설정을 지정 하려면 Api를 사용할 수 있습니다.

참조는 아래 샘플 응용 프로그램:

* [IoTDefaultApp 샘플](https://developer.microsoft.com/en-us/windows/iot/samples/iotdefaultapp)

* [ApplicationResources 샘플](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/ApplicationResources)


## <a name="languages-in-os"></a>OS 언어

Windows 10 IoTCore 키트에는 이제 다음 언어에 대 한 언어 리소스가 포함 됩니다.

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
> | 러시아어 | ro-RU | Europe |
> | 그리스어 | el-GR | Europe |
> | 포르투갈어 (브라질) | pt-BR | 남아메리카 유럽 |
> | Portuese (포르투갈) | pt-PR | 남아메리카 유럽 |

이러한 언어 리소스 UI 문자열, 음성 언어 및 음성 (음성 합성)를 포함 합니다. 이러한 리소스 중 하나 이상을 사용 하 여 Windows IoT 이미지를 빌드할 수 있습니다 및 이미지 시간 동안 지정 해야 하며 나중에 수정할 수 없습니다. UI 언어 관련 리소스 음성 언어와 독립적 이며 리소스 음성는 note 합니다.

### <a name="specifying-ui-and-speech-resources"></a>UI 및 음성 리소스를 지정합니다. 
아래와 같이 OEM 입력 xml 파일의 필요한 UI 및 음성 언어를 지정 된

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


### <a name="specifying-speech-data-resources"></a>음성 데이터 리소스를 지정합니다.
OEM 입력 xml 파일에서 필요한 음성 데이터 리소스는 아래와 같이 지정

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
> 기본적으로 EN-US 음성 데이터가 이미지에 포함 됩니다.

### <a name="samples"></a>샘플
* 참조 [MultiLangSample](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/MultiLangSample) 여러 언어 지원
* 참조 [SingleLangSample](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/SingleLangSample) EN-US 대체 언어를 사용 하 여 FR-FR 언어에 대 한 합니다.
    * 부팅 하는 UI 언어 변경 되 면 사용자에 게 유의 합니다 `administrator` 부팅 UI 언어에서에서 계정 이름을 변환도 됩니다. 따라서-FR에서는 `administrateur`합니다. 참조 [OEMCustomization.cmd](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/SingleLangSample/oemcustomization.cmd)

## <a name="changing-user-preferences-language-region-speech-and-voice"></a>사용자 기본 설정 (예: 언어, 지역, 음성 및 음성)를 변경합니다.

UWP 응용 프로그램 WinRT Api를 사용 하 여 지역, 기본 설정된 UI 언어 목록, 음성 언어 및 음성 기본적으로 사용 해야 하는 설정 수 있습니다. 한 번 기본 설정된 UI 언어 목록 집합 UWP 응용 프로그램 (하지 않는 한 응용 프로그램을 방지 하는 프로그래밍 방식으로) 해당 리소스를 로드 하려고 시도 합니다.
 
응용 프로그램이 해당 리소스에 없는 경우 대체 (fallback) 리소스가 로드 됩니다. 마찬가지로, 기본 설정된 언어에 대 한 해당 OS 리소스가 Windows IoT 이미지의 일부로 없는 경우 Windows IoT를 사용 하 여 해당 대체 항목 가능성이 영어 (EN-US).

* 사용 하 여 영역 설정 `TrySetHomeGeographicRegion` 에서 [Windows.System.UserProfile.GlobalizationPreferences](https://docs.microsoft.com/uwp/api/windows.system.userprofile.globalizationpreferences)
* 사용 하 여 설정 UI 언어 `TrySetLanguages` 에서 [Windows.System.UserProfile.GlobalizationPreferences](https://docs.microsoft.com/uwp/api/windows.system.userprofile.globalizationpreferences)
* 사용 하 여 집합 음성 언어 `TrySetSystemSpeechLanguageAsync` 에서 [Windows.Media.SpeechRecognition.SpeechRecognizer](https://docs.microsoft.com/uwp/api/windows.media.speechrecognition.speechrecognizer)
* 음성을 사용 하 여 설정할 `TrySetDefaultVoiceAsync` 에서 [Windows.Media.SpeechSynthesis.SpeechSynthesizer](https://docs.microsoft.com/en-us/uwp/api/windows.media.speechsynthesis.speechsynthesizer)

> [!NOTE]
> 적절 하 게 작동 하는 것에 대 한 Cortana 필요 지역, UI 언어와 일관 되어야 예: 음성 언어: 지역 FR, UI 및 음성 언어-FR 또는 지역 ES, UI 및 음성 언어 ES-ES 합니다. Cortana 음성 자체를 사용 하 여, UWP 응용 프로그램에서 변경할 수 없습니다.

## <a name="iotsettingsexe"></a>IoTSettings.exe

지역 및 사용자 또는 사용 하도록 설정 하는 Cortana 제품을 빌드할 음성 언어에 대 한 설정을 변경 하는 방법에 대 한 자세한 내용은 읽어보세요 우리의 [명령줄 유틸리티](../manage-your-device/CommandLineUtils.md) 설명서.
