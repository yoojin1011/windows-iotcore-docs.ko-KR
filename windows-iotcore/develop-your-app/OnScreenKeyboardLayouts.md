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
# <a name="on-screen-keyboard-language-layouts"></a><span data-ttu-id="d844a-104">화상 키보드 언어 레이아웃</span><span class="sxs-lookup"><span data-stu-id="d844a-104">On-Screen Keyboard Language Layouts</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d844a-105">Windows 10 IoT Core, 1809, 버전을 기준으로이 문서에서는 더 이상 적용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d844a-105">As of Windows 10 IoT Core, version 1809, this article is no longer applicable.</span></span> <span data-ttu-id="d844a-106">참조 하세요 합니다 [십자형된 장치에 대 한 화상 키보드](./OnScreenKeyboard.md) 현재 설명서 페이지.</span><span class="sxs-lookup"><span data-stu-id="d844a-106">Please see the [On-screen keyboard for headed devices](./OnScreenKeyboard.md) page for the current documentation.</span></span>

<span data-ttu-id="d844a-107">Windows 10 IoT Core, 버전 1703, 1709 및 1803에서 키보드 (OSK)는 다음 언어에 대 한 레이아웃을 지원 하는 화면:</span><span class="sxs-lookup"><span data-stu-id="d844a-107">The on-screen keyboard (OSK) in Windows 10 IoT Core, versions 1703, 1709, and 1803, supports layouts for the following languages:</span></span>

| <span data-ttu-id="d844a-108">언어 태그</span><span class="sxs-lookup"><span data-stu-id="d844a-108">Language Tag</span></span>  | <span data-ttu-id="d844a-109">설명</span><span class="sxs-lookup"><span data-stu-id="d844a-109">Description</span></span>             | <span data-ttu-id="d844a-110">레이아웃 코드</span><span class="sxs-lookup"><span data-stu-id="d844a-110">Layout Code</span></span> |
| :------------ | :---------------------- | -----------:|
| <span data-ttu-id="d844a-111">ko-KR</span><span class="sxs-lookup"><span data-stu-id="d844a-111">en-US</span></span>         | <span data-ttu-id="d844a-112">영어 (미국)</span><span class="sxs-lookup"><span data-stu-id="d844a-112">English (United States)</span></span> |    <span data-ttu-id="d844a-113">00000409</span><span class="sxs-lookup"><span data-stu-id="d844a-113">00000409</span></span> |
| <span data-ttu-id="d844a-114">en-AU</span><span class="sxs-lookup"><span data-stu-id="d844a-114">en-AU</span></span>         | <span data-ttu-id="d844a-115">영어(오스트레일리아)</span><span class="sxs-lookup"><span data-stu-id="d844a-115">English (Australia)</span></span>     |    <span data-ttu-id="d844a-116">00000C09</span><span class="sxs-lookup"><span data-stu-id="d844a-116">00000C09</span></span> |
| <span data-ttu-id="d844a-117">en-CA</span><span class="sxs-lookup"><span data-stu-id="d844a-117">en-CA</span></span>         | <span data-ttu-id="d844a-118">영어(캐나다)</span><span class="sxs-lookup"><span data-stu-id="d844a-118">English (Canada)</span></span>        |    <span data-ttu-id="d844a-119">00001009</span><span class="sxs-lookup"><span data-stu-id="d844a-119">00001009</span></span> |
| <span data-ttu-id="d844a-120">en-GB</span><span class="sxs-lookup"><span data-stu-id="d844a-120">en-GB</span></span>         | <span data-ttu-id="d844a-121">영어 (영국)</span><span class="sxs-lookup"><span data-stu-id="d844a-121">English (Great Britain)</span></span> |    <span data-ttu-id="d844a-122">00000809</span><span class="sxs-lookup"><span data-stu-id="d844a-122">00000809</span></span> |
| <span data-ttu-id="d844a-123">es-ES</span><span class="sxs-lookup"><span data-stu-id="d844a-123">es-ES</span></span>         | <span data-ttu-id="d844a-124">스페인어(스페인)</span><span class="sxs-lookup"><span data-stu-id="d844a-124">Spanish (Spain)</span></span>         |    <span data-ttu-id="d844a-125">0000040A</span><span class="sxs-lookup"><span data-stu-id="d844a-125">0000040A</span></span> |
| <span data-ttu-id="d844a-126">es-MX</span><span class="sxs-lookup"><span data-stu-id="d844a-126">es-MX</span></span>         | <span data-ttu-id="d844a-127">스페인어(멕시코)</span><span class="sxs-lookup"><span data-stu-id="d844a-127">Spanish (Mexico)</span></span>        |    <span data-ttu-id="d844a-128">0000080A</span><span class="sxs-lookup"><span data-stu-id="d844a-128">0000080A</span></span> |
| <span data-ttu-id="d844a-129">de-DE</span><span class="sxs-lookup"><span data-stu-id="d844a-129">de-DE</span></span>         | <span data-ttu-id="d844a-130">독일어</span><span class="sxs-lookup"><span data-stu-id="d844a-130">German</span></span>                  |    <span data-ttu-id="d844a-131">00000407</span><span class="sxs-lookup"><span data-stu-id="d844a-131">00000407</span></span> |
| <span data-ttu-id="d844a-132">fr-CA</span><span class="sxs-lookup"><span data-stu-id="d844a-132">fr-CA</span></span>         | <span data-ttu-id="d844a-133">프랑스어(캐나다)</span><span class="sxs-lookup"><span data-stu-id="d844a-133">French (Canada)</span></span>         |    <span data-ttu-id="d844a-134">00000C0C</span><span class="sxs-lookup"><span data-stu-id="d844a-134">00000C0C</span></span> |
| <span data-ttu-id="d844a-135">fr-FR</span><span class="sxs-lookup"><span data-stu-id="d844a-135">fr-FR</span></span>         | <span data-ttu-id="d844a-136">프랑스어 (프랑스)</span><span class="sxs-lookup"><span data-stu-id="d844a-136">French (France)</span></span>         |    <span data-ttu-id="d844a-137">0000040C</span><span class="sxs-lookup"><span data-stu-id="d844a-137">0000040C</span></span> |
| <span data-ttu-id="d844a-138">it-IT</span><span class="sxs-lookup"><span data-stu-id="d844a-138">it-IT</span></span>         | <span data-ttu-id="d844a-139">이탈리아어</span><span class="sxs-lookup"><span data-stu-id="d844a-139">Italian</span></span>                 |    <span data-ttu-id="d844a-140">00000410</span><span class="sxs-lookup"><span data-stu-id="d844a-140">00000410</span></span> |
| <span data-ttu-id="d844a-141">pt-BR</span><span class="sxs-lookup"><span data-stu-id="d844a-141">pt-BR</span></span>         | <span data-ttu-id="d844a-142">포르투갈어(브라질)</span><span class="sxs-lookup"><span data-stu-id="d844a-142">Portuguese (Brazil)</span></span>     |    <span data-ttu-id="d844a-143">00000416</span><span class="sxs-lookup"><span data-stu-id="d844a-143">00000416</span></span> |

<span data-ttu-id="d844a-144">눌러 OSK의 "& 123" 단추를 사용 하고자 하는 레이아웃을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d844a-144">By pressing and holding the OSK's "&123" button, the user can select which layout they want to use:</span></span>

![모든 언어](../media/OnScreenKeyboard/AllLanguages.png)
 
<span data-ttu-id="d844a-146">그러나 Oem의 경우 제한할 수 있습니다는 레이아웃 옵션은 사용자에 게 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d844a-146">As an OEM, however, you can limit which layout choices are displayed to the user.</span></span> <span data-ttu-id="d844a-147">사용자에 게 표시 하는 레이아웃을 제한 하려면 먼저의 지침 참조를 [TechNet의 자판 doucmentation](https://technet.microsoft.com/library/cc978687.aspx)합니다.</span><span class="sxs-lookup"><span data-stu-id="d844a-147">To limit which layouts to show the user, first reference the guidance from the [Keyboard Layout doucmentation on TechNet](https://technet.microsoft.com/library/cc978687.aspx).</span></span>
 
<span data-ttu-id="d844a-148">구체적인 예로, North America 언어 레이아웃을 허용 하려는 경우 (EN-US, EN-CA es-MX, FR-CA), OEMCustomization.cmd 스크립트에 다음을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d844a-148">For a concrete example, if you want to only allow North America language layouts (en-US, en-CA, es-MX, fr-CA), you could add the following to your OEMCustomization.cmd script:</span></span>

```console
call "%~dp0\setKeyboardLanguages.cmd"
```

<span data-ttu-id="d844a-149">여기서 setKeyboardLanguages.cmd은이 포함 하는 동일한 디렉터리에서 스크립트입니다.</span><span class="sxs-lookup"><span data-stu-id="d844a-149">Where setKeyboardLanguages.cmd is a script in the same directory containing this:</span></span>
 
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

<span data-ttu-id="d844a-150">위의 명령 스크립트의 결과 적용이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d844a-150">The resulting effect of the above command script will be:</span></span>

![북아메리카 언어](../media/OnScreenKeyboard/NorthAmericanLanguages.png)

### <a name="some-things-to-note"></a><span data-ttu-id="d844a-152">알아두어야 할 사항:</span><span class="sxs-lookup"><span data-stu-id="d844a-152">Some things to note:</span></span>
*  <span data-ttu-id="d844a-153">값 이름이 10 진수 시퀀스를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d844a-153">The value names indicate a decimal sequence.</span></span>
*  <span data-ttu-id="d844a-154">값은 문자열 값 (REG_SZ)입니다.</span><span class="sxs-lookup"><span data-stu-id="d844a-154">The values are string values (REG_SZ).</span></span>
*  <span data-ttu-id="d844a-155">물론, 위의 스크립트 텍스트 OEMCustomization.cmd 스크립트에 직접 추가할 수 있었습니다.</span><span class="sxs-lookup"><span data-stu-id="d844a-155">The script text above, of course, could be added directly into the OEMCustomization.cmd script.</span></span>
*  <span data-ttu-id="d844a-156">**하지** 허용 하도록 특별히 설정 권한이 있으므로 "Preload" 레지스트리 키를 삭제는 화상 키보드를 해당 값을 읽는 응용 프로그램입니다.</span><span class="sxs-lookup"><span data-stu-id="d844a-156">**Do not** delete the "Preload" registry key since it has permissions set on it specifically to allow the on-screen keyboard application to read its values.</span></span>
*  <span data-ttu-id="d844a-157">를 적용 하기 위해 다음이 지침에 대 한 필수 구성 요소는 다음 기능 \* 이미지 포함 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d844a-157">A prerequisite for these instructions to be applicable, is that your image must include the following features\*:</span></span>
   * <span data-ttu-id="d844a-158">IOT_SHELL_ONSCREEN_KEYBOARD</span><span class="sxs-lookup"><span data-stu-id="d844a-158">IOT_SHELL_ONSCREEN_KEYBOARD</span></span>
   * <span data-ttu-id="d844a-159">IOT_SHELL_ONSCREEN_KEYBOARD_FOLLOWFOCUS</span><span class="sxs-lookup"><span data-stu-id="d844a-159">IOT_SHELL_ONSCREEN_KEYBOARD_FOLLOWFOCUS</span></span>

<span data-ttu-id="d844a-160">IoT 기능에 대 한 자세한 내용은 참조 하십시오 [IoT Core 기능 목록](https://docs.microsoft.com/windows-hardware/manufacture/iot/iot-core-feature-list)합니다.</span><span class="sxs-lookup"><span data-stu-id="d844a-160">For more information about IoT Features, see [IoT Core Feature List](https://docs.microsoft.com/windows-hardware/manufacture/iot/iot-core-feature-list).</span></span>
