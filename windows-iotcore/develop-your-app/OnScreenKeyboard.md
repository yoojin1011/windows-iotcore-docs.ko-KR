---
title: Windows 10 IoT Core 화상 키보드를 사용 하 여 side-by-side 장치 구성
author: johntasler
ms.author: jtasler
ms.date: 09/13/2018
ms.topic: article
description: 새로운 화상 키보드 및 Windows 10 IoT Core 버전 1809에서이를 구성 하는 방법에 대해 알아봅니다.
keywords: Windows 10 IoT Core, 터치, 키보드, osk, 화면, 화상, sip, 입력, ime, 터치, 받아쓰기, 음성, 음성
ms.custom: RS5
ms.openlocfilehash: 100aeb484690c462deac56dcadf7d17667487ae2
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "60169211"
---
# <a name="on-screen-keyboard-for-headed-devices"></a>장치에 대 한 화상 키보드

Windows 10 IoT Core 버전 1809에서는 화상 키보드 구성 요소가 크게 변경 되었습니다. 이제 IoT Core는 Windows 데스크톱 버전과 동일한 터치 키보드 구성 요소를 사용 합니다.

## <a name="new-features"></a>새 기능
새 키보드 구현에서는 장치 개발에 다음과 같은 이점을 제공 합니다.

* [전체 Windows 키보드 언어 레이아웃 집합](#windows-keyboard-language-layouts)
* [입력 범위에 대 한 지원 (예: 전자 메일 주소, 숫자 PIN, 검색 필드 등)](#support-for-input-scopes)
* [IME (입력기)](#input-method-editor-ime)
* [보이지 않는 텍스트 입력 필드](#non-obscured-text-input-fields)
* [받아쓰기 모드](#dictation-mode)
* [사용자 인터페이스 기본 설정 선택](#user-interface-configuration)

## <a name="feature-packages"></a>기능 패키지

프로토타입 (개발) 이미지의 경우 화상 키보드 기능이 이미 포함 되어 있지만 [Windows 장치 포털](../manage-your-device/deviceportal.md#iot-specific-features)의 장치 설정에서 사용 하도록 설정 해야 합니다.

상용화의 경우 다음과 같은 선택적 기능 패키지가 이미지에 화상 키보드를 추가 합니다.
* IOT_SHELL_ONSCREEN_KEYBOARD
* IOT_SHELL_ONSCREEN_KEYBOARD_FOLLOWFOCUS

> [!TIP]
> IoT 핵심 기능에 대 한 자세한 내용은 [Iot Core 기능 목록](/windows-hardware/manufacture/iot/iot-core-feature-list) 및 [iot core 제조 가이드](/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)를 참조 하세요.

## <a name="windows-keyboard-language-layouts"></a>Windows 키보드 언어 레이아웃

이 릴리스에서는 지원 되는 언어 레이아웃이 데스크톱 Windows 버전에서 사용할 수 있는 전체 집합을 포함 하도록 확장 되었습니다. 사용자가 다양 한 언어 레이아웃 중에서 선택할 수 있도록 하기 위해 일반적으로 응용 프로그램의 설정 영역에 선택 UI를 포함 합니다. 응용 프로그램에서 화상 키보드에 사용 되는 언어를 설정할 수 있도록 다음 API가 제공 됩니다.

[TrySetInputMethodLanguageTag.](/uwp/api/windows.globalization.language.trysetinputmethodlanguagetag)

이 API의 예제는 [LanguageManager.cs](https://github.com/Microsoft/Windows-iotcore-samples/blob/develop/Samples/IoTCoreDefaultApp/CS/IoTCoreDefaultApp/Presenters/LanguageManager.cs) 파일의 [IoTCoreDefaultApp 샘플 응용 프로그램](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/IoTCoreDefaultApp)에서 볼 수 있습니다.

## <a name="support-for-input-scopes"></a>입력 범위 지원

이전 릴리스에서는 EmailSmtpAddress 입력 범위만 사용할 수 있었습니다. 이 릴리스에서는 전체 입력 범위 집합을 사용할 수 있습니다. 다음 항목에서는 입력 범위 및 응용 프로그램에서 사용 하는 방법에 대해 설명 합니다.

[입력 범위를 사용 하 여 터치 키보드 변경](/windows/uwp/design/input/use-input-scope-to-change-the-touch-keyboard)

## <a name="input-method-editor-ime"></a>IME(입력기)

이 릴리스는 키보드의 키 (예: 중국어, 일본어, 한국어) 보다 더 많은 graphemes가 있는 모든 언어에 필요한 입력 방법 편집기를 제공 합니다.

## <a name="non-obscured-text-input-fields"></a>보이지 않는 텍스트 입력 필드

이전 릴리스에서 터치 키보드는 사용자가 입력 한 내용을 볼 수 없도록 포커스가 있는 텍스트 필드를 모호 하 게 할 수 있습니다. 이 릴리스에서는 텍스트 필드를 자동으로 보기로 스크롤하여이 문제를 해결 합니다. 그러면 터치 키보드에 의해 더 이상 보이지 않습니다.

## <a name="dictation-mode"></a>받아쓰기 모드

입력 언어가 OS 언어 (기본값)로 설정 된 경우 음성 인식 입력 기능을 사용할 수 있습니다.
키보드에 받아쓰기 단추를 표시 하려면 [사용자 인터페이스 구성](#user-interface-configuration)에서 다음 섹션을 참조 하세요.

## <a name="user-interface-configuration"></a>사용자 인터페이스 구성

화상 키보드는 해당 사용자 인터페이스에 대 한 몇 가지 구성 가능 옵션을 제공 합니다. 이러한 설정은 레지스트리를 통해 구성 됩니다.
개발 하는 동안 [PowerShell](/windows/iot-core/connect-your-device/powershell) 또는 [SSH (Secure Shell](/windows/iot-core/connect-your-device/ssh))를 사용할 수 있습니다. OEM 이미지를 만들기 위해 레지스트리 값을 설정 하는 기본 메커니즘은 여기서 `OEMInput.xml` 설명 하는 파일입니다.

[런타임 사용자 지정](/windows-hardware/manufacture/iot/oscustomizations#runtime-customizations)

> [!NOTE]
> 여기에 설명 된 대부분의 레지스트리 설정은 화면 키보드를 표시 하는 동안 적용 됩니다.
> 이렇게 하면 개발 중에 다른 combinatations 설정 값을 쉽게 시도 하 여 결과 변경 내용을 실시간으로 바로 볼 수 있습니다. 설정이 즉시 적용 되지 않으면 키보드 UI에 대 한 변경 내용을 확인 하기 위해 장치를 다시 부팅 해야 합니다.

### <a name="keyboard-height"></a>키보드 높이

기본적으로 터치 키보드는 화면 높이의 하위 45%를 사용 합니다. 크기 및 해상도에 따라 장치에 너무 크거나 작게 표시 될 수 있습니다. 화면 높이의 높이를 최대 2/3까지 조정할 수 있습니다. 범위에 없는 모든 값은 고정 됩니다. 이 값은 부동 소수점 값으로 지정 되므로 픽셀 수준의 전체 자릿수를 사용할 수 있습니다. 다음 수식을 적용 하 여 비율을 계산 하면 됩니다.

`percentage = (100 * <desired_pixel_height>) / <screen_height>`

예를 들어 높이를 56.783%로 변경 하려면 다음 레지스트리 값을 설정 합니다.
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
> 레지스트리 값 형식은 문자열 (`REG_SZ`) 이어야 하므로 소수 값을로 나타낼 수 있습니다.
> 소수점입니다. 정수 백분율의`REG_DWORD`경우에도 DWord ()를 사용할 수 _없습니다_ .

### <a name="additional-preferences"></a>추가 기본 설정

나머지 기본 설정 집합은 기본 설정 하위 키의 문자열 값입니다.
```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\OSK\Preferences
```

| 레지스트리 값               | Default Value      | 설명                                                                                         |
| ---------------------------- | ------------------ | --------------------------------------------------------------------------------------------------- |
| AudioFeedback_Disabled       | "0"                | "0"은 키 클릭 오디오 피드백을 사용 하도록 설정 합니다. "1"은이를 사용 하지 않도록 설정 합니다.                                          |
| Dictation_Disabled           | "1"                | "0"은 받아쓰기 (음성 인식) 단추를 표시 합니다. "1"은 숨깁니다.<br/> (아래 참고 참조)             |
| KeyboardModeEnabled_full     | "0"                | "0"은 전체 키보드 모드를 사용 하지 않도록 설정 합니다. "1"을 사용 하도록 설정 합니다.                                                |
| KeyboardModeEnabled_narrow   | "1"                | "0"은 좁은 키보드 모드를 사용 하지 않도록 설정 합니다. "1"을 사용 하도록 설정 합니다.                                              |
| KeyboardModeEnabled_wide     | "1"                | "0"은 와이드 키보드 모드를 사용 하지 않도록 설정 합니다. "1"을 사용 하도록 설정 합니다.                                                |
| ModeOrder                    | "와이드; 좁게; full" | 모드 드롭다운 메뉴에서 모드가 표시 되는 순서 (왼쪽에서 오른쪽)입니다 (설정 된 경우). |
| SettingsMenuKey_Collapsed    | "0"                | 모드 드롭다운 메뉴를 숨깁니다. 한 모드만 사용 하도록 설정 된 경우이 항목을 "1"로 설정 합니다.                         |
| Paste_Disabled               | "0"                | "0"은 붙여넣기 단추를 표시 합니다. "1"은 숨깁니다.<br/> 다시 부팅 한 후 변경 내용이 적용 됩니다.                    |
| CloseButton_Disabled         | "0"                | "0"은 닫기 단추를 표시 합니다. "1"은 닫기 단추를 숨깁니다.<br/> 다시 부팅 한 후 변경 내용이 적용 됩니다.       |
| EmojiKeyEnabled              | "0"                | "0"은이 모 지 키를 숨깁니다. "1"은이를 표시 하 여 사용자에 게이 모 지 문자를 입력할 수 있도록 합니다.                 |

> [!NOTE]
> 받아쓰기 모드에서는 선택 된 입력 언어 뿐만 아니라 오디오 입력 장치에 대해 음성 패키지를 설치 해야 합니다. 일치 하는 음성 패키지가 설치 되지 않은 경우 받아쓰기 단추가 표시 되지 않습니다.
> 
> 모든 이미지는 en-us 음성 언어를 포함 합니다. 다른 음성 패키지는 선택적 기능으로 설치 됩니다.
> IoT 기능에 대 한 자세한 내용은 [Iot Core 기능 목록](/windows-hardware/manufacture/iot/iot-core-feature-list) 및 [iot core 제조 가이드](/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)를 참조 하세요.

예를 들어 `wide` 키보드 모드만 사용 하도록 설정 하려면 PowerShell에서 다음을 수행할 수 있습니다.
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
