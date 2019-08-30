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
# <a name="on-screen-keyboard-language-layouts"></a><span data-ttu-id="dcc08-104">화상 키보드 언어 레이아웃</span><span class="sxs-lookup"><span data-stu-id="dcc08-104">On-Screen Keyboard Language Layouts</span></span>

> [!IMPORTANT]
> <span data-ttu-id="dcc08-105">Windows 10 IoT Core 버전 1809부터이 문서는 더 이상 적용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dcc08-105">As of Windows 10 IoT Core, version 1809, this article is no longer applicable.</span></span> <span data-ttu-id="dcc08-106">현재 설명서는 [side-by-side 장치에 대 한 화상 키보드](./OnScreenKeyboard.md) 페이지를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="dcc08-106">Please see the [On-screen keyboard for headed devices](./OnScreenKeyboard.md) page for the current documentation.</span></span>

<span data-ttu-id="dcc08-107">Windows 10 IoT Core, 버전 1703, 1709 및 1803의 화상 키보드 (OSK)는 다음 언어에 대 한 레이아웃을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcc08-107">The on-screen keyboard (OSK) in Windows 10 IoT Core, versions 1703, 1709, and 1803, supports layouts for the following languages:</span></span>

| <span data-ttu-id="dcc08-108">언어 태그</span><span class="sxs-lookup"><span data-stu-id="dcc08-108">Language Tag</span></span>  | <span data-ttu-id="dcc08-109">설명</span><span class="sxs-lookup"><span data-stu-id="dcc08-109">Description</span></span>             | <span data-ttu-id="dcc08-110">코드 레이아웃</span><span class="sxs-lookup"><span data-stu-id="dcc08-110">Layout Code</span></span> |
| :------------ | :---------------------- | -----------:|
| <span data-ttu-id="dcc08-111">ko-KR</span><span class="sxs-lookup"><span data-stu-id="dcc08-111">en-US</span></span>         | <span data-ttu-id="dcc08-112">영어 (미국)</span><span class="sxs-lookup"><span data-stu-id="dcc08-112">English (United States)</span></span> |    <span data-ttu-id="dcc08-113">00000409</span><span class="sxs-lookup"><span data-stu-id="dcc08-113">00000409</span></span> |
| <span data-ttu-id="dcc08-114">en-AU</span><span class="sxs-lookup"><span data-stu-id="dcc08-114">en-AU</span></span>         | <span data-ttu-id="dcc08-115">영어(오스트레일리아)</span><span class="sxs-lookup"><span data-stu-id="dcc08-115">English (Australia)</span></span>     |    <span data-ttu-id="dcc08-116">00000C09</span><span class="sxs-lookup"><span data-stu-id="dcc08-116">00000C09</span></span> |
| <span data-ttu-id="dcc08-117">en-CA</span><span class="sxs-lookup"><span data-stu-id="dcc08-117">en-CA</span></span>         | <span data-ttu-id="dcc08-118">영어(캐나다)</span><span class="sxs-lookup"><span data-stu-id="dcc08-118">English (Canada)</span></span>        |    <span data-ttu-id="dcc08-119">00001009</span><span class="sxs-lookup"><span data-stu-id="dcc08-119">00001009</span></span> |
| <span data-ttu-id="dcc08-120">en-GB</span><span class="sxs-lookup"><span data-stu-id="dcc08-120">en-GB</span></span>         | <span data-ttu-id="dcc08-121">영어 (Britain)</span><span class="sxs-lookup"><span data-stu-id="dcc08-121">English (Great Britain)</span></span> |    <span data-ttu-id="dcc08-122">00000809</span><span class="sxs-lookup"><span data-stu-id="dcc08-122">00000809</span></span> |
| <span data-ttu-id="dcc08-123">es-ES</span><span class="sxs-lookup"><span data-stu-id="dcc08-123">es-ES</span></span>         | <span data-ttu-id="dcc08-124">스페인어(스페인)</span><span class="sxs-lookup"><span data-stu-id="dcc08-124">Spanish (Spain)</span></span>         |    <span data-ttu-id="dcc08-125">0000040A</span><span class="sxs-lookup"><span data-stu-id="dcc08-125">0000040A</span></span> |
| <span data-ttu-id="dcc08-126">es-MX</span><span class="sxs-lookup"><span data-stu-id="dcc08-126">es-MX</span></span>         | <span data-ttu-id="dcc08-127">스페인어(멕시코)</span><span class="sxs-lookup"><span data-stu-id="dcc08-127">Spanish (Mexico)</span></span>        |    <span data-ttu-id="dcc08-128">0000080A</span><span class="sxs-lookup"><span data-stu-id="dcc08-128">0000080A</span></span> |
| <span data-ttu-id="dcc08-129">de-DE</span><span class="sxs-lookup"><span data-stu-id="dcc08-129">de-DE</span></span>         | <span data-ttu-id="dcc08-130">독일어</span><span class="sxs-lookup"><span data-stu-id="dcc08-130">German</span></span>                  |    <span data-ttu-id="dcc08-131">00000407</span><span class="sxs-lookup"><span data-stu-id="dcc08-131">00000407</span></span> |
| <span data-ttu-id="dcc08-132">fr-CA</span><span class="sxs-lookup"><span data-stu-id="dcc08-132">fr-CA</span></span>         | <span data-ttu-id="dcc08-133">프랑스어(캐나다)</span><span class="sxs-lookup"><span data-stu-id="dcc08-133">French (Canada)</span></span>         |    <span data-ttu-id="dcc08-134">00000C0C</span><span class="sxs-lookup"><span data-stu-id="dcc08-134">00000C0C</span></span> |
| <span data-ttu-id="dcc08-135">fr-FR</span><span class="sxs-lookup"><span data-stu-id="dcc08-135">fr-FR</span></span>         | <span data-ttu-id="dcc08-136">프랑스어 (프랑스)</span><span class="sxs-lookup"><span data-stu-id="dcc08-136">French (France)</span></span>         |    <span data-ttu-id="dcc08-137">0000040C</span><span class="sxs-lookup"><span data-stu-id="dcc08-137">0000040C</span></span> |
| <span data-ttu-id="dcc08-138">it-IT</span><span class="sxs-lookup"><span data-stu-id="dcc08-138">it-IT</span></span>         | <span data-ttu-id="dcc08-139">이탈리아어</span><span class="sxs-lookup"><span data-stu-id="dcc08-139">Italian</span></span>                 |    <span data-ttu-id="dcc08-140">00000410</span><span class="sxs-lookup"><span data-stu-id="dcc08-140">00000410</span></span> |
| <span data-ttu-id="dcc08-141">pt-BR</span><span class="sxs-lookup"><span data-stu-id="dcc08-141">pt-BR</span></span>         | <span data-ttu-id="dcc08-142">포르투갈어(브라질)</span><span class="sxs-lookup"><span data-stu-id="dcc08-142">Portuguese (Brazil)</span></span>     |    <span data-ttu-id="dcc08-143">00000416</span><span class="sxs-lookup"><span data-stu-id="dcc08-143">00000416</span></span> |

<span data-ttu-id="dcc08-144">OSK의 "& 123" 단추를 누르고 있으면 사용할 레이아웃을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dcc08-144">By pressing and holding the OSK's "&123" button, the user can select which layout they want to use:</span></span>

![모든 언어](../media/OnScreenKeyboard/AllLanguages.png)
 
<span data-ttu-id="dcc08-146">그러나 OEM으로 서 사용자에 게 표시 되는 레이아웃 선택 항목을 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dcc08-146">As an OEM, however, you can limit which layout choices are displayed to the user.</span></span> <span data-ttu-id="dcc08-147">사용자를 표시할 레이아웃을 제한 하려면 먼저 [TechNet의 키보드 레이아웃 doucmentation](https://technet.microsoft.com/library/cc978687.aspx)에서 지침을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="dcc08-147">To limit which layouts to show the user, first reference the guidance from the [Keyboard Layout doucmentation on TechNet](https://technet.microsoft.com/library/cc978687.aspx).</span></span>
 
<span data-ttu-id="dcc08-148">구체적 예를 들어 북아메리카 언어 레이아웃 (en-us, en-us, es-mx, fr-fr, fr-fr)만 허용 하려는 경우 다음을 OEMCustomization 지정 cmd 스크립트에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dcc08-148">For a concrete example, if you want to only allow North America language layouts (en-US, en-CA, es-MX, fr-CA), you could add the following to your OEMCustomization.cmd script:</span></span>

```console
call "%~dp0\setKeyboardLanguages.cmd"
```

<span data-ttu-id="dcc08-149">여기서 setKeyboardLanguages은이를 포함 하는 동일한 디렉터리의 스크립트입니다.</span><span class="sxs-lookup"><span data-stu-id="dcc08-149">Where setKeyboardLanguages.cmd is a script in the same directory containing this:</span></span>
 
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

<span data-ttu-id="dcc08-150">위의 명령 스크립트는 다음과 같은 결과가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="dcc08-150">The resulting effect of the above command script will be:</span></span>

![북아메리카 언어](../media/OnScreenKeyboard/NorthAmericanLanguages.png)

### <a name="some-things-to-note"></a><span data-ttu-id="dcc08-152">몇 가지 참고 사항:</span><span class="sxs-lookup"><span data-stu-id="dcc08-152">Some things to note:</span></span>
*  <span data-ttu-id="dcc08-153">값 이름은 10 진수 시퀀스를 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcc08-153">The value names indicate a decimal sequence.</span></span>
*  <span data-ttu-id="dcc08-154">값은 문자열 값 (REG_SZ)입니다.</span><span class="sxs-lookup"><span data-stu-id="dcc08-154">The values are string values (REG_SZ).</span></span>
*  <span data-ttu-id="dcc08-155">물론 위의 스크립트 텍스트를 OEMCustomization 지정 .cmd 스크립트에 직접 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dcc08-155">The script text above, of course, could be added directly into the OEMCustomization.cmd script.</span></span>
*  <span data-ttu-id="dcc08-156">"미리 로드" 레지스트리 키는 화상 키보드 응용 프로그램에서 해당 값을 읽을 수 있도록 특별히 설정 된 권한이 있으므로 삭제 **하지 마십시오** .</span><span class="sxs-lookup"><span data-stu-id="dcc08-156">**Do not** delete the "Preload" registry key since it has permissions set on it specifically to allow the on-screen keyboard application to read its values.</span></span>
*  <span data-ttu-id="dcc08-157">이러한 지침을 적용 하기 위한 필수 구성 요소는 이미지에 다음 기능을 포함 해야 한다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="dcc08-157">A prerequisite for these instructions to be applicable, is that your image must include the following features\*:</span></span>
   * <span data-ttu-id="dcc08-158">IOT_SHELL_ONSCREEN_KEYBOARD</span><span class="sxs-lookup"><span data-stu-id="dcc08-158">IOT_SHELL_ONSCREEN_KEYBOARD</span></span>
   * <span data-ttu-id="dcc08-159">IOT_SHELL_ONSCREEN_KEYBOARD_FOLLOWFOCUS</span><span class="sxs-lookup"><span data-stu-id="dcc08-159">IOT_SHELL_ONSCREEN_KEYBOARD_FOLLOWFOCUS</span></span>

<span data-ttu-id="dcc08-160">IoT 기능에 대 한 자세한 내용은 [Iot 핵심 기능 목록](https://docs.microsoft.com/windows-hardware/manufacture/iot/iot-core-feature-list)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="dcc08-160">For more information about IoT Features, see [IoT Core Feature List](https://docs.microsoft.com/windows-hardware/manufacture/iot/iot-core-feature-list).</span></span>
