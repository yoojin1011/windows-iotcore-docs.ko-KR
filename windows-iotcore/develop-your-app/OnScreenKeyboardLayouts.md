---
title: 사용 가능한 화상 키보드 언어 레이아웃 지정
author: johntasler
ms.author: jtasler
ms.date: 09/12/2018
ms.topic: article
description: Windows IoT 장치의 사용자가 사용할 수 있는 화상 키보드 언어 레이아웃을 지정 하는 방법에 대해 알아봅니다.
keywords: windows 10 IoT Core, 귀하 상용화할 권리, osk 화상 키보드 언어 레이아웃
ms.openlocfilehash: 003f280236733763b33f096f6574aad04921841f
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "60169620"
---
# <a name="on-screen-keyboard-language-layouts"></a>화상 키보드 언어 레이아웃

> [!IMPORTANT]
> Windows 10 IoT Core 버전 1809부터이 문서는 더 이상 적용 되지 않습니다. 현재 설명서는 [side-by-side 장치에 대 한 화상 키보드](./OnScreenKeyboard.md) 페이지를 참조 하세요.

Windows 10 IoT Core, 버전 1703, 1709 및 1803의 화상 키보드 (OSK)는 다음 언어에 대 한 레이아웃을 지원 합니다.

| 언어 태그  | 설명             | 코드 레이아웃 |
| :------------ | :---------------------- | -----------:|
| ko-KR         | 영어 (미국) |    00000409 |
| en-AU         | 영어(오스트레일리아)     |    00000C09 |
| en-CA         | 영어(캐나다)        |    00001009 |
| en-GB         | 영어 (Britain) |    00000809 |
| es-ES         | 스페인어(스페인)         |    0000040A |
| es-MX         | 스페인어(멕시코)        |    0000080A |
| de-DE         | 독일어                  |    00000407 |
| fr-CA         | 프랑스어(캐나다)         |    00000C0C |
| fr-FR         | 프랑스어 (프랑스)         |    0000040C |
| it-IT         | 이탈리아어                 |    00000410 |
| pt-BR         | 포르투갈어(브라질)     |    00000416 |

OSK의 "& 123" 단추를 누르고 있으면 사용할 레이아웃을 선택할 수 있습니다.

![모든 언어](../media/OnScreenKeyboard/AllLanguages.png)
 
그러나 OEM으로 서 사용자에 게 표시 되는 레이아웃 선택 항목을 제한할 수 있습니다. 사용자를 표시할 레이아웃을 제한 하려면 먼저 [TechNet의 키보드 레이아웃 doucmentation](https://technet.microsoft.com/library/cc978687.aspx)에서 지침을 참조 하세요.
 
구체적 예를 들어 북아메리카 언어 레이아웃 (en-us, en-us, es-mx, fr-fr, fr-fr)만 허용 하려는 경우 다음을 OEMCustomization 지정 cmd 스크립트에 추가할 수 있습니다.

```console
call "%~dp0\setKeyboardLanguages.cmd"
```

여기서 setKeyboardLanguages은이를 포함 하는 동일한 디렉터리의 스크립트입니다.
 
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

위의 명령 스크립트는 다음과 같은 결과가 나타납니다.

![북아메리카 언어](../media/OnScreenKeyboard/NorthAmericanLanguages.png)

### <a name="some-things-to-note"></a>몇 가지 참고 사항:
*  값 이름은 10 진수 시퀀스를 의미 합니다.
*  값은 문자열 값 (REG_SZ)입니다.
*  물론 위의 스크립트 텍스트를 OEMCustomization 지정 .cmd 스크립트에 직접 추가할 수 있습니다.
*  "미리 로드" 레지스트리 키는 화상 키보드 응용 프로그램에서 해당 값을 읽을 수 있도록 특별히 설정 된 권한이 있으므로 삭제 **하지 마십시오** .
*  이러한 지침을 적용 하기 위한 필수 구성 요소는 이미지에 다음 기능을 포함 해야 한다는 것입니다.
   * IOT_SHELL_ONSCREEN_KEYBOARD
   * IOT_SHELL_ONSCREEN_KEYBOARD_FOLLOWFOCUS

IoT 기능에 대 한 자세한 내용은 [Iot 핵심 기능 목록](https://docs.microsoft.com/windows-hardware/manufacture/iot/iot-core-feature-list)을 참조 하세요.
