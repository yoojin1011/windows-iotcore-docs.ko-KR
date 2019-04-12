---
title: 헤드 장치의 Windows 10 IoT Core 사용 하 여 화상 키보드 구성
author: johntasler
ms.author: jtasler
ms.date: 09/13/2018
ms.topic: article
description: 알아봅니다 새 화면 키보드 및 Windows 10 IoT Core, 1809 버전에서에서 구성 하는 방법입니다.
keywords: Windows 10 IoT Core, 터치, 키보드, osk, 화면, 화면, sip, 입력된, ime, 양방향, 받아쓰기, 음성, 음성
ms.custom: RS5
ms.openlocfilehash: 100aeb484690c462deac56dcadf7d17667487ae2
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512349"
---
# <a name="on-screen-keyboard-for-headed-devices"></a>십자형된 장치에 대 한 화상 키보드

1809, 버전, Windows 10 IoT Core는 크게 및 향상에 대 한 키보드 구성 요소가 변경 하는 화면에 나타나는! 이제 IoT Core는 Windows 데스크톱 버전으로 동일한 터치 키보드 구성 요소를 사용합니다.

## <a name="new-features"></a>새로운 기능
새 키보드 구현을 헤드 장치 개발에는 다음과 같은 이점을 제공.

* [Windows 자판 언어의 전체 집합](#windows-keyboard-language-layouts)
* [입력된 범위 (예: 전자 메일 주소, 숫자 PIN, 검색 필드 등)에 대 한 지원](#support-for-input-scopes)
* [IME(입력기)](#input-method-editor-ime)
* [비 가려진 텍스트 입력된 필드](#non-obscured-text-input-fields)
* [받아쓰기 모드](#dictation-mode)
* [다양 한 사용자 인터페이스 환경 설정](#user-interface-configuration)

## <a name="feature-packages"></a>기능 패키지

프로토타입 (개발) 이미지에 대 한는 화상 키보드 기능은 이미 포함 되어 있지만에서 장치 설정에서 사용 하도록 설정 해야 합니다 [Windows Device Portal](../manage-your-device/deviceportal.md#iot-specific-features)합니다.

상업화, 다음과 같은 선택적 기능이 패키지 추가 화상 키보드를 이미지:
* IOT_SHELL_ONSCREEN_KEYBOARD
* IOT_SHELL_ONSCREEN_KEYBOARD_FOLLOWFOCUS

> [!TIP]
> IoT Core 기능에 대 한 자세한 내용은 참조 하세요. [IoT Core 기능 목록](/windows-hardware/manufacture/iot/iot-core-feature-list) 하 고 [IoT Core 제조 가이드](/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)합니다.

## <a name="windows-keyboard-language-layouts"></a>Windows 자판 언어

이 릴리스에서 지원 되는 언어 레이아웃 데스크톱 Windows 버전에서 사용할 수 있는 파일의 전체 집합을 포함 하도록 확장 되었습니다. 사용자가 다른 언어 레이아웃 중에서 선택할 수 있도록, 응용 프로그램의 설정 영역에서 일반적으로 선택 UI를 포함할 수도 있습니다. 응용 프로그램을 사용 하도록 설정 하려면 다음 API가 제공 하는 언어를 설정 합니다 키보드를 사용 하 여 화면:

[Windows.Globalization.Language.TrySetInputMethodLanguageTag](/uwp/api/windows.globalization.language.trysetinputmethodlanguagetag)

이 API의 예제에서 볼 수 있습니다 합니다 [IoTCoreDefaultApp 샘플 응용 프로그램](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/IoTCoreDefaultApp)를 [LanguageManager.cs](https://github.com/Microsoft/Windows-iotcore-samples/blob/develop/Samples/IoTCoreDefaultApp/CS/IoTCoreDefaultApp/Presenters/LanguageManager.cs) 파일입니다.

## <a name="support-for-input-scopes"></a>입력된 범위에 대 한 지원

이전 릴리스에서 EmailSmtpAddress 입력된 범위 에서만 사용할 수 있었습니다. 이 릴리스에서 전체 입력 범위 제공 됩니다. 다음 항목에는 입력된 범위 및 응용 프로그램에서 사용 하는 방법을 설명 합니다.

[입력 범위를 사용하여 터치 키보드 변경](/windows/uwp/design/input/use-input-scope-to-change-the-touch-keyboard)

## <a name="input-method-editor-ime"></a>IME(입력기)

이 릴리스에서 중국어, 일본어 및 한국어 등 키보드의 키 보다 더 많은 제자가 있는 언어에 필요한 입력 방법 편집기를 제공 합니다.

## <a name="non-obscured-text-input-fields"></a>비 가려진 텍스트 입력된 필드

이전 릴리스에서 사용자 입력 된 내용을 볼 수 없습니다 있도록 터치 키보드 포커스가 있는 텍스트 필드를 보이지 않을 수도 있습니다. 이 릴리스에서 터치 키보드를 사용 하는 더 이상 가려지는지 있도록 뷰로 텍스트 필드를 자동으로 스크롤 하 여이 문제를 해결 합니다.

## <a name="dictation-mode"></a>받아쓰기 모드

입력된 언어를 기본적으로 운영 체제 언어에 설정 된 경우 음성 인식 입력 기능은 사용할 수 있습니다.
키보드에서 받아쓰기 단추를 표시 하려면 다음 섹션을를 참조 [사용자 인터페이스 구성](#user-interface-configuration)합니다.

## <a name="user-interface-configuration"></a>사용자 인터페이스 구성

화상 키보드는 해당 사용자 인터페이스에 대 한 구성 가능한 여러 옵션을 제공 합니다. 이러한 레지스트리를 통해 구성 됩니다.
개발 중 사용할 수 있습니다 [PowerShell](/windows/iot-core/connect-your-device/powershell) 하거나 [SSH (보안 셸)](/windows/iot-core/connect-your-device/ssh)합니다. 레지스트리 값을 설정 하는 기본 메커니즘은 OEM 이미지를 만들기 위해는 `OEMInput.xml` 여기에 설명 된 파일:

[런타임 사용자 지정](/windows-hardware/manufacture/iot/oscustomizations#runtime-customizations)

> [!NOTE]
> 대부분의 레지스트리 설정은 여기서 설명 하는 동안 적용 됩니다는 화상 키보드는 표시 합니다.
> 이렇게 하면 다른 combinatations 즉시 실시간으로 결과 변경 내용 표시 설정 값을 쉽게 개발 하는 동안 있습니다. 설정을 효과 즉시 사용 하지 않는 경우에 키보드 UI 변경 내용을 확인 하기 위해 장치를 다시 부팅 해야 합니다.

### <a name="keyboard-height"></a>키보드 높이

기본적으로 터치 키보드 화면의 높이 중 더 낮은 45% 사용 됩니다. 이 너무 크거나 작은 크기와 해상도 따라 사용자의 장치에 나타날 수 있습니다. 2 / 3의 최대 높이 조정할 수는 화면의 높이입니다. 범위를 벗어났습니다. 값 범위로 고정 됩니다. 이 부동 소수점으로 지정 되어 있으므로 픽셀 수준의 전체 자릿수 값을 허용 합니다. 백분율을 계산 하는 다음 수식을 적용 하기만 하면 됩니다.

`percentage = (100 * <desired_pixel_height>) / <screen_height>`

예를 들어 56.783% 높이 변경 하려면 설정한 다음 레지스트리 값:
```console
set OskRootKey=HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\OSK
reg.exe ADD "%OskRootKey%" /v MaxHeightPercentage /t REG_SZ /d "56.783" /f
```
또는 PowerShell에서:
```powershell
set OskRootKey "HKLM:\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\OSK"
cd $OskRootKey
Set-ItemProperty -Path . -Name MaxHeightPercentage -Type String -Value 56.783
```

> [!NOTE]
> 레지스트리 값 형식과 문자열 이어야 합니다 (`REG_SZ`) 소수 자릿수 값을 사용 하 여 표현할 수 있도록 합니다.
> 소수점입니다. DWord를 사용 하 여 (`REG_DWORD`)는 _하지_ 정수 백분율에 대해서도 작동 합니다.

### <a name="additional-preferences"></a>추가 기본 설정

기본 설정의 나머지 집합은 기본 하위 키의 문자열 값입니다.
```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\OSK\Preferences
```

| 레지스트리 값               | 기본값      | 설명                                                                                         |
| ---------------------------- | ------------------ | --------------------------------------------------------------------------------------------------- |
| AudioFeedback_Disabled       | "0"                | "0" 키 클릭 오디오 피드백을 사용 하도록 설정 "1" 사용 되지 않습니다.                                          |
| Dictation_Disabled           | "1"                | "0" 받아쓰기 (음성 인식) 단추를 보여 줍니다. "1"이 숨겨집니다.<br/> (아래 참고 참조)             |
| KeyboardModeEnabled_full     | "0"                | "0" 사용 하지 않도록 설정 된 전체 키보드 모드 "1" 사용 하도록 설정 합니다.                                                |
| KeyboardModeEnabled_narrow   | "1"                | "0" 좁은 키보드 모드가; 적용 되지 않습니다. "1" 사용 하도록 설정 합니다.                                              |
| KeyboardModeEnabled_wide     | "1"                | "0" 와이드 키보드 모드가; 적용 되지 않습니다. "1" 사용 하도록 설정 합니다.                                                |
| ModeOrder                    | "범위를 좁힐; 전체 와이드;" | 모드 나열 되는 모드 드롭다운 메뉴에서 사용 하도록 설정 하는 경우 순서 (왼쪽에서 오른쪽) |
| SettingsMenuKey_Collapsed    | "0"                | 모드 드롭다운 메뉴를 숨깁니다. 이 경우 "1"로 설정 하나의 모드를 사용 합니다.                         |
| Paste_Disabled               | "0"                | "0" 붙여넣기 단추 표시 "1"이 숨겨집니다.<br/> 다시 부팅 한 후 변경 내용을 적용 합니다.                    |
| CloseButton_Disabled         | "0"                | "0" 닫기 단추 표시 "1" [닫기] 단추를 숨깁니다.<br/> 다시 부팅 한 후 변경 내용을 적용 합니다.       |
| EmojiKeyEnabled              | "0"                | "0"이 모 지 키를 숨깁니다. "1"은 표시,이 모 지 문자를 입력할 수 있도록 허용 합니다.                 |

> [!NOTE]
> 받아쓰기 모드에는 오디오 입력된 장치 뿐만 아니라 선택한 입력된 언어에 대 한 설치 된 음성 패키지가 필요 합니다. 일치 하는 음성 패키지를 설치 하지 않은 경우 받아쓰기 단추가 표시 되지 않습니다.
> 
> 모든 이미지는 EN-US 음성 언어를 포함합니다. 다른 음성 패키지는 선택적 기능으로 설치 됩니다.
> IoT 기능에 대 한 자세한 내용은 참조 하십시오 [IoT Core 기능 목록](/windows-hardware/manufacture/iot/iot-core-feature-list) 하 고 [IoT Core 제조 가이드](/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)합니다.

예를 들어, 사용할 수 있도록 `wide` 키보드 모드로 PowerShell에서 다음을 수행할 수 있습니다.
```powershell
set OskRootKey "HKLM:\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\OSK"
cd $OskRootKey
mkdir Preferences
cd Preferences
Set-ItemProperty . -Name KeyboardModeEnabled_full -Value "0"      # Optional, since the default is "0"
Set-ItemProperty . -Name KeyboardModeEnabled_narrow -Value "0"
Set-ItemProperty . -Name KeyboardModeEnabled_wide -Value "1"      # Optional, since the default is "1"
Set-ItemProperty . -Name SettingsMenuKey_Collapsed -Value "1"
```
