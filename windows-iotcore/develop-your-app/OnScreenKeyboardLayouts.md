---
title: 지정 화면의 사용 가능한 언어 자판
author: johntasler
ms.author: jtasler
ms.date: 09/12/2018
ms.topic: article
description: 화상 키보드에 언어를 지정 하는 방법을 알아봅니다 레이아웃은 Windows IoT 장치의 사용자에 게 제공 합니다.
keywords: windows 10 IoT Core 상용화할 osk 화면 키보드 언어 레이아웃
ms.openlocfilehash: 003f280236733763b33f096f6574aad04921841f
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513029"
---
# <a name="on-screen-keyboard-language-layouts"></a>화상 키보드 언어 레이아웃

> [!IMPORTANT]
> Windows 10 IoT Core, 1809, 버전을 기준으로이 문서에서는 더 이상 적용할 수 없습니다. 참조 하세요 합니다 [십자형된 장치에 대 한 화상 키보드](./OnScreenKeyboard.md) 현재 설명서 페이지.

Windows 10 IoT Core, 버전 1703, 1709 및 1803에서 키보드 (OSK)는 다음 언어에 대 한 레이아웃을 지원 하는 화면:

| 언어 태그  | 설명             | 레이아웃 코드 |
| :------------ | :---------------------- | -----------:|
| ko-KR         | 영어 (미국) |    00000409 |
| en-AU         | 영어(오스트레일리아)     |    00000C09 |
| en-CA         | 영어(캐나다)        |    00001009 |
| en-GB         | 영어 (영국) |    00000809 |
| es-ES         | 스페인어(스페인)         |    0000040A |
| es-MX         | 스페인어(멕시코)        |    0000080A |
| de-DE         | 독일어                  |    00000407 |
| fr-CA         | 프랑스어(캐나다)         |    00000C0C |
| fr-FR         | 프랑스어 (프랑스)         |    0000040C |
| it-IT         | 이탈리아어                 |    00000410 |
| pt-BR         | 포르투갈어(브라질)     |    00000416 |

눌러 OSK의 "& 123" 단추를 사용 하고자 하는 레이아웃을 선택할 수 있습니다.

![모든 언어](../media/OnScreenKeyboard/AllLanguages.png)
 
그러나 Oem의 경우 제한할 수 있습니다는 레이아웃 옵션은 사용자에 게 표시 됩니다. 사용자에 게 표시 하는 레이아웃을 제한 하려면 먼저의 지침 참조를 [TechNet의 자판 doucmentation](https://technet.microsoft.com/library/cc978687.aspx)합니다.
 
구체적인 예로, North America 언어 레이아웃을 허용 하려는 경우 (EN-US, EN-CA es-MX, FR-CA), OEMCustomization.cmd 스크립트에 다음을 추가할 수 있습니다.

```console
call "%~dp0\setKeyboardLanguages.cmd"
```

여기서 setKeyboardLanguages.cmd은이 포함 하는 동일한 디렉터리에서 스크립트입니다.
 
```console
@echo off

set getDefaultAccountSID="wmic.exe useraccount where name='DefaultAccount' get sid"

for /F "tokens=2 usebackq delims== " %%s in (`%getDefaultAccountSID%`) do (
    set registryKey="HKEY_USERS\%%~s\Keyboard Layout\Preload"
    goto :setRegistry
  )
)
echo Unable to determine SID for DefaultAccount
goto :eof

:setRegistry
  echo on
  REG ADD %registryKey% /v "1" /d "00000409" /f
  REG ADD %registryKey% /v "2" /d "00001009" /f
  REG ADD %registryKey% /v "3" /d "0000080A" /f
  REG ADD %registryKey% /v "4" /d "00000C0C" /f
  @echo off
goto :eof
```

위의 명령 스크립트의 결과 적용이 됩니다.

![북아메리카 언어](../media/OnScreenKeyboard/NorthAmericanLanguages.png)

### <a name="some-things-to-note"></a>알아두어야 할 사항:
*  값 이름이 10 진수 시퀀스를 나타냅니다.
*  값은 문자열 값 (REG_SZ)입니다.
*  물론, 위의 스크립트 텍스트 OEMCustomization.cmd 스크립트에 직접 추가할 수 있었습니다.
*  **하지** 허용 하도록 특별히 설정 권한이 있으므로 "Preload" 레지스트리 키를 삭제는 화상 키보드를 해당 값을 읽는 응용 프로그램입니다.
*  를 적용 하기 위해 다음이 지침에 대 한 필수 구성 요소는 다음 기능 * 이미지 포함 해야 합니다.
   * IOT_SHELL_ONSCREEN_KEYBOARD
   * IOT_SHELL_ONSCREEN_KEYBOARD_FOLLOWFOCUS

IoT 기능에 대 한 자세한 내용은 참조 하십시오 [IoT Core 기능 목록](https://docs.microsoft.com/windows-hardware/manufacture/iot/iot-core-feature-list)합니다.
