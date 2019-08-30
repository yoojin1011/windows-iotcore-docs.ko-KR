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
# <a name="on-screen-keyboard-for-headed-devices"></a><span data-ttu-id="85e16-104">장치에 대 한 화상 키보드</span><span class="sxs-lookup"><span data-stu-id="85e16-104">On-screen keyboard for headed devices</span></span>

<span data-ttu-id="85e16-105">Windows 10 IoT Core 버전 1809에서는 화상 키보드 구성 요소가 크게 변경 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="85e16-105">In Windows 10 IoT Core, version 1809, the on-screen keyboard component has changed significantly, and for the better!</span></span> <span data-ttu-id="85e16-106">이제 IoT Core는 Windows 데스크톱 버전과 동일한 터치 키보드 구성 요소를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="85e16-106">IoT Core now uses the same touch keyboard components as the desktop edition of Windows.</span></span>

## <a name="new-features"></a><span data-ttu-id="85e16-107">새 기능</span><span class="sxs-lookup"><span data-stu-id="85e16-107">New features</span></span>
<span data-ttu-id="85e16-108">새 키보드 구현에서는 장치 개발에 다음과 같은 이점을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="85e16-108">The new keyboard implementation provides the following benefits to your headed device development:</span></span>

* [<span data-ttu-id="85e16-109">전체 Windows 키보드 언어 레이아웃 집합</span><span class="sxs-lookup"><span data-stu-id="85e16-109">The entire set of Windows keyboard language layouts</span></span>](#windows-keyboard-language-layouts)
* [<span data-ttu-id="85e16-110">입력 범위에 대 한 지원 (예: 전자 메일 주소, 숫자 PIN, 검색 필드 등)</span><span class="sxs-lookup"><span data-stu-id="85e16-110">Support for input scopes (e.g., Email Address, Numeric PIN, Search Field, etc.)</span></span>](#support-for-input-scopes)
* [<span data-ttu-id="85e16-111">IME (입력기)</span><span class="sxs-lookup"><span data-stu-id="85e16-111">Input Method Editor (IME)</span></span>](#input-method-editor-ime)
* [<span data-ttu-id="85e16-112">보이지 않는 텍스트 입력 필드</span><span class="sxs-lookup"><span data-stu-id="85e16-112">Non-obscured text input fields</span></span>](#non-obscured-text-input-fields)
* [<span data-ttu-id="85e16-113">받아쓰기 모드</span><span class="sxs-lookup"><span data-stu-id="85e16-113">Dictation mode</span></span>](#dictation-mode)
* [<span data-ttu-id="85e16-114">사용자 인터페이스 기본 설정 선택</span><span class="sxs-lookup"><span data-stu-id="85e16-114">A selection of user interface preferences</span></span>](#user-interface-configuration)

## <a name="feature-packages"></a><span data-ttu-id="85e16-115">기능 패키지</span><span class="sxs-lookup"><span data-stu-id="85e16-115">Feature packages</span></span>

<span data-ttu-id="85e16-116">프로토타입 (개발) 이미지의 경우 화상 키보드 기능이 이미 포함 되어 있지만 [Windows 장치 포털](../manage-your-device/deviceportal.md#iot-specific-features)의 장치 설정에서 사용 하도록 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="85e16-116">For prototyping (development) images, the on-screen keyboard feature is already included, but you will need to enable it from Device Settings in the [Windows Device Portal](../manage-your-device/deviceportal.md#iot-specific-features).</span></span>

<span data-ttu-id="85e16-117">상용화의 경우 다음과 같은 선택적 기능 패키지가 이미지에 화상 키보드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="85e16-117">For commercialization, the following optional feature packages will add the on-screen keyboard to your image:</span></span>
* <span data-ttu-id="85e16-118">IOT_SHELL_ONSCREEN_KEYBOARD</span><span class="sxs-lookup"><span data-stu-id="85e16-118">IOT_SHELL_ONSCREEN_KEYBOARD</span></span>
* <span data-ttu-id="85e16-119">IOT_SHELL_ONSCREEN_KEYBOARD_FOLLOWFOCUS</span><span class="sxs-lookup"><span data-stu-id="85e16-119">IOT_SHELL_ONSCREEN_KEYBOARD_FOLLOWFOCUS</span></span>

> [!TIP]
> <span data-ttu-id="85e16-120">IoT 핵심 기능에 대 한 자세한 내용은 [Iot Core 기능 목록](/windows-hardware/manufacture/iot/iot-core-feature-list) 및 [iot core 제조 가이드](/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="85e16-120">For more information about IoT Core Features, see [IoT Core Feature List](/windows-hardware/manufacture/iot/iot-core-feature-list) and [IoT Core manufacturing guide](/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).</span></span>

## <a name="windows-keyboard-language-layouts"></a><span data-ttu-id="85e16-121">Windows 키보드 언어 레이아웃</span><span class="sxs-lookup"><span data-stu-id="85e16-121">Windows keyboard language layouts</span></span>

<span data-ttu-id="85e16-122">이 릴리스에서는 지원 되는 언어 레이아웃이 데스크톱 Windows 버전에서 사용할 수 있는 전체 집합을 포함 하도록 확장 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="85e16-122">With this release, the supported language layouts has expanded to include the full set of those available in the desktop Windows edition.</span></span> <span data-ttu-id="85e16-123">사용자가 다양 한 언어 레이아웃 중에서 선택할 수 있도록 하기 위해 일반적으로 응용 프로그램의 설정 영역에 선택 UI를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="85e16-123">To allow your users to select between different language layouts, you would typically include selection UI in your application's Settings area.</span></span> <span data-ttu-id="85e16-124">응용 프로그램에서 화상 키보드에 사용 되는 언어를 설정할 수 있도록 다음 API가 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="85e16-124">The following API is provided to enable your application to set the language that the on-screen keyboard will use:</span></span>

[<span data-ttu-id="85e16-125">TrySetInputMethodLanguageTag.</span><span class="sxs-lookup"><span data-stu-id="85e16-125">Windows.Globalization.Language.TrySetInputMethodLanguageTag</span></span>](/uwp/api/windows.globalization.language.trysetinputmethodlanguagetag)

<span data-ttu-id="85e16-126">이 API의 예제는 [LanguageManager.cs](https://github.com/Microsoft/Windows-iotcore-samples/blob/develop/Samples/IoTCoreDefaultApp/CS/IoTCoreDefaultApp/Presenters/LanguageManager.cs) 파일의 [IoTCoreDefaultApp 샘플 응용 프로그램](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/IoTCoreDefaultApp)에서 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85e16-126">An example of this API can be seen in the [IoTCoreDefaultApp sample application](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/IoTCoreDefaultApp), in the [LanguageManager.cs](https://github.com/Microsoft/Windows-iotcore-samples/blob/develop/Samples/IoTCoreDefaultApp/CS/IoTCoreDefaultApp/Presenters/LanguageManager.cs) file.</span></span>

## <a name="support-for-input-scopes"></a><span data-ttu-id="85e16-127">입력 범위 지원</span><span class="sxs-lookup"><span data-stu-id="85e16-127">Support for input scopes</span></span>

<span data-ttu-id="85e16-128">이전 릴리스에서는 EmailSmtpAddress 입력 범위만 사용할 수 있었습니다.</span><span class="sxs-lookup"><span data-stu-id="85e16-128">In previous releases, only the EmailSmtpAddress input scope was available.</span></span> <span data-ttu-id="85e16-129">이 릴리스에서는 전체 입력 범위 집합을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85e16-129">In this release, the full set of input scopes are available.</span></span> <span data-ttu-id="85e16-130">다음 항목에서는 입력 범위 및 응용 프로그램에서 사용 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="85e16-130">The following topic explains input scopes and how to use them in your applications:</span></span>

[<span data-ttu-id="85e16-131">입력 범위를 사용 하 여 터치 키보드 변경</span><span class="sxs-lookup"><span data-stu-id="85e16-131">Use input scope to change the touch keyboard</span></span>](/windows/uwp/design/input/use-input-scope-to-change-the-touch-keyboard)

## <a name="input-method-editor-ime"></a><span data-ttu-id="85e16-132">IME(입력기)</span><span class="sxs-lookup"><span data-stu-id="85e16-132">Input Method Editor (IME)</span></span>

<span data-ttu-id="85e16-133">이 릴리스는 키보드의 키 (예: 중국어, 일본어, 한국어) 보다 더 많은 graphemes가 있는 모든 언어에 필요한 입력 방법 편집기를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="85e16-133">This release provides an Input Method Editor, which is required for any language that has more graphemes than there are keys on the keyboard, such as Chinese, Japanese, and Korean.</span></span>

## <a name="non-obscured-text-input-fields"></a><span data-ttu-id="85e16-134">보이지 않는 텍스트 입력 필드</span><span class="sxs-lookup"><span data-stu-id="85e16-134">Non-obscured text input fields</span></span>

<span data-ttu-id="85e16-135">이전 릴리스에서 터치 키보드는 사용자가 입력 한 내용을 볼 수 없도록 포커스가 있는 텍스트 필드를 모호 하 게 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85e16-135">In previous releases, the touch keyboard might obscure the focused text field so that the user was unable to see what they were typing.</span></span> <span data-ttu-id="85e16-136">이 릴리스에서는 텍스트 필드를 자동으로 보기로 스크롤하여이 문제를 해결 합니다. 그러면 터치 키보드에 의해 더 이상 보이지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="85e16-136">This release fixes this problem by automatically scrolling the text field into view so that it's no longer obscured by the touch keyboard.</span></span>

## <a name="dictation-mode"></a><span data-ttu-id="85e16-137">받아쓰기 모드</span><span class="sxs-lookup"><span data-stu-id="85e16-137">Dictation mode</span></span>

<span data-ttu-id="85e16-138">입력 언어가 OS 언어 (기본값)로 설정 된 경우 음성 인식 입력 기능을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85e16-138">When the input language is set to the OS language, which is the default, the voice recognition input feature is available.</span></span>
<span data-ttu-id="85e16-139">키보드에 받아쓰기 단추를 표시 하려면 [사용자 인터페이스 구성](#user-interface-configuration)에서 다음 섹션을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="85e16-139">To show the dictation button in the keyboard, refer to the following section on [User Interface configuration](#user-interface-configuration).</span></span>

## <a name="user-interface-configuration"></a><span data-ttu-id="85e16-140">사용자 인터페이스 구성</span><span class="sxs-lookup"><span data-stu-id="85e16-140">User Interface configuration</span></span>

<span data-ttu-id="85e16-141">화상 키보드는 해당 사용자 인터페이스에 대 한 몇 가지 구성 가능 옵션을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="85e16-141">The on-screen keyboard provides several configurable options for its user interface.</span></span> <span data-ttu-id="85e16-142">이러한 설정은 레지스트리를 통해 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="85e16-142">These are configured via the registry.</span></span>
<span data-ttu-id="85e16-143">개발 하는 동안 [PowerShell](/windows/iot-core/connect-your-device/powershell) 또는 [SSH (Secure Shell](/windows/iot-core/connect-your-device/ssh))를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85e16-143">During development you can use [PowerShell](/windows/iot-core/connect-your-device/powershell) or [Secure Shell (SSH)](/windows/iot-core/connect-your-device/ssh).</span></span> <span data-ttu-id="85e16-144">OEM 이미지를 만들기 위해 레지스트리 값을 설정 하는 기본 메커니즘은 여기서 `OEMInput.xml` 설명 하는 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="85e16-144">For creating an OEM image, the preferred mechanism for setting registry values is the `OEMInput.xml` file discussed here:</span></span>

[<span data-ttu-id="85e16-145">런타임 사용자 지정</span><span class="sxs-lookup"><span data-stu-id="85e16-145">Runtime customizations</span></span>](/windows-hardware/manufacture/iot/oscustomizations#runtime-customizations)

> [!NOTE]
> <span data-ttu-id="85e16-146">여기에 설명 된 대부분의 레지스트리 설정은 화면 키보드를 표시 하는 동안 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="85e16-146">Most of the registry settings documented here will take effect while the on-screen keyboard is visible.</span></span>
> <span data-ttu-id="85e16-147">이렇게 하면 개발 중에 다른 combinatations 설정 값을 쉽게 시도 하 여 결과 변경 내용을 실시간으로 바로 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85e16-147">This allows you during development to easily try different combinatations of settings values, immediately seeing the resulting changes in real time.</span></span> <span data-ttu-id="85e16-148">설정이 즉시 적용 되지 않으면 키보드 UI에 대 한 변경 내용을 확인 하기 위해 장치를 다시 부팅 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="85e16-148">If a setting does not take effect immediately, you will need to reboot the device in order to see the changes to the keyboard UI.</span></span>

### <a name="keyboard-height"></a><span data-ttu-id="85e16-149">키보드 높이</span><span class="sxs-lookup"><span data-stu-id="85e16-149">Keyboard Height</span></span>

<span data-ttu-id="85e16-150">기본적으로 터치 키보드는 화면 높이의 하위 45%를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="85e16-150">By default, the touch keyboard will use the lower 45% of the screen's height.</span></span> <span data-ttu-id="85e16-151">크기 및 해상도에 따라 장치에 너무 크거나 작게 표시 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85e16-151">This may appear too large or small on your device, depending on its size and resolution.</span></span> <span data-ttu-id="85e16-152">화면 높이의 높이를 최대 2/3까지 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85e16-152">You can adjust the height up to a maximum of two-thirds the height of the screen.</span></span> <span data-ttu-id="85e16-153">범위에 없는 모든 값은 고정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="85e16-153">Any value not in range will be clamped into range.</span></span> <span data-ttu-id="85e16-154">이 값은 부동 소수점 값으로 지정 되므로 픽셀 수준의 전체 자릿수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85e16-154">Because this is specified as a floating point value, it allows for pixel-level precision.</span></span> <span data-ttu-id="85e16-155">다음 수식을 적용 하 여 비율을 계산 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="85e16-155">Simply apply the following formula to calculate the percentage:</span></span>

`percentage = (100 * <desired_pixel_height>) / <screen_height>`

<span data-ttu-id="85e16-156">예를 들어 높이를 56.783%로 변경 하려면 다음 레지스트리 값을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="85e16-156">As an example, to change the height to 56.783%, you would set the following registry value:</span></span>
```console
set OskRootKey=HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\OSK
reg.exe ADD "%OskRootKey%" /v MaxHeightPercentage /t REG_SZ /d "56.783" /f
```
<span data-ttu-id="85e16-157">또는 PowerShell에서:</span><span class="sxs-lookup"><span data-stu-id="85e16-157">or from PowerShell:</span></span>
```powershell
set OskRootKey "HKLM:\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\OSK"
cd $OskRootKey
Set-ItemProperty -Path . -Name MaxHeightPercentage -Type String -Value 56.783
```

> [!NOTE]
> <span data-ttu-id="85e16-158">레지스트리 값 형식은 문자열 (`REG_SZ`) 이어야 하므로 소수 값을로 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85e16-158">The registry value type must be a String (`REG_SZ`), so that the fractional values can be represented with.</span></span>
> <span data-ttu-id="85e16-159">소수점입니다.</span><span class="sxs-lookup"><span data-stu-id="85e16-159">a decimal point.</span></span> <span data-ttu-id="85e16-160">정수 백분율의`REG_DWORD`경우에도 DWord ()를 사용할 수 _없습니다_ .</span><span class="sxs-lookup"><span data-stu-id="85e16-160">Using DWord (`REG_DWORD`) will _not_ work, even for whole number percentages.</span></span>

### <a name="additional-preferences"></a><span data-ttu-id="85e16-161">추가 기본 설정</span><span class="sxs-lookup"><span data-stu-id="85e16-161">Additional preferences</span></span>

<span data-ttu-id="85e16-162">나머지 기본 설정 집합은 기본 설정 하위 키의 문자열 값입니다.</span><span class="sxs-lookup"><span data-stu-id="85e16-162">The remaining set of preferences are String values in the Preferences subkey:</span></span>
```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\OSK\Preferences
```

| <span data-ttu-id="85e16-163">레지스트리 값</span><span class="sxs-lookup"><span data-stu-id="85e16-163">Registry Value</span></span>               | <span data-ttu-id="85e16-164">Default Value</span><span class="sxs-lookup"><span data-stu-id="85e16-164">Default Value</span></span>      | <span data-ttu-id="85e16-165">설명</span><span class="sxs-lookup"><span data-stu-id="85e16-165">Description</span></span>                                                                                         |
| ---------------------------- | ------------------ | --------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="85e16-166">AudioFeedback_Disabled</span><span class="sxs-lookup"><span data-stu-id="85e16-166">AudioFeedback_Disabled</span></span>       | <span data-ttu-id="85e16-167">"0"</span><span class="sxs-lookup"><span data-stu-id="85e16-167">"0"</span></span>                | <span data-ttu-id="85e16-168">"0"은 키 클릭 오디오 피드백을 사용 하도록 설정 합니다. "1"은이를 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="85e16-168">"0" enables the key click audio feedback; "1" disables it.</span></span>                                          |
| <span data-ttu-id="85e16-169">Dictation_Disabled</span><span class="sxs-lookup"><span data-stu-id="85e16-169">Dictation_Disabled</span></span>           | <span data-ttu-id="85e16-170">"1"</span><span class="sxs-lookup"><span data-stu-id="85e16-170">"1"</span></span>                | <span data-ttu-id="85e16-171">"0"은 받아쓰기 (음성 인식) 단추를 표시 합니다. "1"은 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="85e16-171">"0" shows the dictation (voice recognition) button; "1" hides it.</span></span><br/> <span data-ttu-id="85e16-172">(아래 참고 참조)</span><span class="sxs-lookup"><span data-stu-id="85e16-172">(see note below)</span></span>             |
| <span data-ttu-id="85e16-173">KeyboardModeEnabled_full</span><span class="sxs-lookup"><span data-stu-id="85e16-173">KeyboardModeEnabled_full</span></span>     | <span data-ttu-id="85e16-174">"0"</span><span class="sxs-lookup"><span data-stu-id="85e16-174">"0"</span></span>                | <span data-ttu-id="85e16-175">"0"은 전체 키보드 모드를 사용 하지 않도록 설정 합니다. "1"을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="85e16-175">"0" disables the full keyboard mode; "1" enables it.</span></span>                                                |
| <span data-ttu-id="85e16-176">KeyboardModeEnabled_narrow</span><span class="sxs-lookup"><span data-stu-id="85e16-176">KeyboardModeEnabled_narrow</span></span>   | <span data-ttu-id="85e16-177">"1"</span><span class="sxs-lookup"><span data-stu-id="85e16-177">"1"</span></span>                | <span data-ttu-id="85e16-178">"0"은 좁은 키보드 모드를 사용 하지 않도록 설정 합니다. "1"을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="85e16-178">"0" disables the narrow keyboard mode; "1" enables it.</span></span>                                              |
| <span data-ttu-id="85e16-179">KeyboardModeEnabled_wide</span><span class="sxs-lookup"><span data-stu-id="85e16-179">KeyboardModeEnabled_wide</span></span>     | <span data-ttu-id="85e16-180">"1"</span><span class="sxs-lookup"><span data-stu-id="85e16-180">"1"</span></span>                | <span data-ttu-id="85e16-181">"0"은 와이드 키보드 모드를 사용 하지 않도록 설정 합니다. "1"을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="85e16-181">"0" disables the wide keyboard mode; "1" enables it.</span></span>                                                |
| <span data-ttu-id="85e16-182">ModeOrder</span><span class="sxs-lookup"><span data-stu-id="85e16-182">ModeOrder</span></span>                    | <span data-ttu-id="85e16-183">"와이드; 좁게; full"</span><span class="sxs-lookup"><span data-stu-id="85e16-183">"wide;narrow;full"</span></span> | <span data-ttu-id="85e16-184">모드 드롭다운 메뉴에서 모드가 표시 되는 순서 (왼쪽에서 오른쪽)입니다 (설정 된 경우).</span><span class="sxs-lookup"><span data-stu-id="85e16-184">The order (from left to right) in which the modes are listed in the mode drop-down menu, if enabled</span></span> |
| <span data-ttu-id="85e16-185">SettingsMenuKey_Collapsed</span><span class="sxs-lookup"><span data-stu-id="85e16-185">SettingsMenuKey_Collapsed</span></span>    | <span data-ttu-id="85e16-186">"0"</span><span class="sxs-lookup"><span data-stu-id="85e16-186">"0"</span></span>                | <span data-ttu-id="85e16-187">모드 드롭다운 메뉴를 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="85e16-187">Hides the mode drop-down menu.</span></span> <span data-ttu-id="85e16-188">한 모드만 사용 하도록 설정 된 경우이 항목을 "1"로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="85e16-188">Set this to "1" if only one mode is enabled.</span></span>                         |
| <span data-ttu-id="85e16-189">Paste_Disabled</span><span class="sxs-lookup"><span data-stu-id="85e16-189">Paste_Disabled</span></span>               | <span data-ttu-id="85e16-190">"0"</span><span class="sxs-lookup"><span data-stu-id="85e16-190">"0"</span></span>                | <span data-ttu-id="85e16-191">"0"은 붙여넣기 단추를 표시 합니다. "1"은 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="85e16-191">"0" shows the Paste button; "1" hides it.</span></span><br/> <span data-ttu-id="85e16-192">다시 부팅 한 후 변경 내용이 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="85e16-192">Change takes effect after reboot.</span></span>                    |
| <span data-ttu-id="85e16-193">CloseButton_Disabled</span><span class="sxs-lookup"><span data-stu-id="85e16-193">CloseButton_Disabled</span></span>         | <span data-ttu-id="85e16-194">"0"</span><span class="sxs-lookup"><span data-stu-id="85e16-194">"0"</span></span>                | <span data-ttu-id="85e16-195">"0"은 닫기 단추를 표시 합니다. "1"은 닫기 단추를 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="85e16-195">"0" shows the Close button; "1" hides the Close button</span></span><br/> <span data-ttu-id="85e16-196">다시 부팅 한 후 변경 내용이 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="85e16-196">Change takes effect after reboot.</span></span>       |
| <span data-ttu-id="85e16-197">EmojiKeyEnabled</span><span class="sxs-lookup"><span data-stu-id="85e16-197">EmojiKeyEnabled</span></span>              | <span data-ttu-id="85e16-198">"0"</span><span class="sxs-lookup"><span data-stu-id="85e16-198">"0"</span></span>                | <span data-ttu-id="85e16-199">"0"은이 모 지 키를 숨깁니다. "1"은이를 표시 하 여 사용자에 게이 모 지 문자를 입력할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="85e16-199">"0" hides the Emoji key; "1" shows it, allowing the user to enter Emoji characters.</span></span>                 |

> [!NOTE]
> <span data-ttu-id="85e16-200">받아쓰기 모드에서는 선택 된 입력 언어 뿐만 아니라 오디오 입력 장치에 대해 음성 패키지를 설치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="85e16-200">Dictation mode requires a speech package to be installed for the selected input language, as well as an audio input device.</span></span> <span data-ttu-id="85e16-201">일치 하는 음성 패키지가 설치 되지 않은 경우 받아쓰기 단추가 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="85e16-201">If a matching speech packages is not installed, the dictation button will not be shown.</span></span>
> 
> <span data-ttu-id="85e16-202">모든 이미지는 en-us 음성 언어를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="85e16-202">All images include the en-US speech language.</span></span> <span data-ttu-id="85e16-203">다른 음성 패키지는 선택적 기능으로 설치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="85e16-203">Other speech packages are installed as optional features.</span></span>
> <span data-ttu-id="85e16-204">IoT 기능에 대 한 자세한 내용은 [Iot Core 기능 목록](/windows-hardware/manufacture/iot/iot-core-feature-list) 및 [iot core 제조 가이드](/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="85e16-204">For more information about IoT Features, see [IoT Core Feature List](/windows-hardware/manufacture/iot/iot-core-feature-list) and [IoT Core manufacturing guide](/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).</span></span>

<span data-ttu-id="85e16-205">예를 들어 `wide` 키보드 모드만 사용 하도록 설정 하려면 PowerShell에서 다음을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85e16-205">As an example, to enable only `wide` keyboard mode, in PowerShell you could do the following:</span></span>
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
