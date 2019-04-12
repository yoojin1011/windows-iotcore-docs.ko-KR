---
title: IoT Shell 개요
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 장치에 대 한 탐색을 탐색할 수 있도록 IoT Shell을 활용 하는 방법에 알아봅니다.
keywords: windows iot, IoT core 셸, 응용 프로그램, 포그라운드 응용 프로그램, 백그라운드 응용 프로그램
ms.openlocfilehash: be72fabc91fc5748a029b61ebd9a306deb23f726
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513326"
---
# <a name="iot-shell-overview"></a><span data-ttu-id="38e7b-104">IoT Shell 개요</span><span class="sxs-lookup"><span data-stu-id="38e7b-104">IoT Shell Overview</span></span>

<span data-ttu-id="38e7b-105">이 문서에서는 IoT 셸, 전경색 및 배경색 응용 프로그램 및 장치에서 이러한 응용 프로그램 간에 탐색 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="38e7b-105">This document covers the IoT Shell, foreground and background applications, and how to navigate between these applications on your device.</span></span>

## <a name="iot-shell-foreground-and-background-apps"></a><span data-ttu-id="38e7b-106">IoT 셸, 전경 및 배경 앱</span><span class="sxs-lookup"><span data-stu-id="38e7b-106">IoT Shell, Foreground, and Background Apps</span></span>

<span data-ttu-id="38e7b-107">IoT Core 장치에 IoT 셸에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="38e7b-107">Your IoT Core device runs the IoT Shell.</span></span> <span data-ttu-id="38e7b-108">여러 책임을 갖지만 해당 기본 작업은 등록 된 시작 앱 시작 되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="38e7b-108">It has many responsibilities, but its primary job is to make sure registered startup apps are launched.</span></span> <span data-ttu-id="38e7b-109">두 가지 모드가 있습니다. 헤드 및 헤드리스 합니다.</span><span class="sxs-lookup"><span data-stu-id="38e7b-109">It has two modes: Headed and Headless.</span></span> <span data-ttu-id="38e7b-110">Headed 모드로 IoT Shell에는 전체 화면 (Headed 앱이 라고도 함)에서 해당 UI에 표시 되는 단일 등록된 시작 앱을 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="38e7b-110">In Headed mode, the IoT Shell will launch a single registered startup app that will show its UI in full screen (also known as a Headed app).</span></span> <span data-ttu-id="38e7b-111">헤드 모드만 연결 화면 및 UI 표시를 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="38e7b-111">Headed mode assumes you have a screen connected and shows UI.</span></span> <span data-ttu-id="38e7b-112">헤드리스 모드로 (자세히 설명 [여기](../learn-about-hardware/HeadlessMode.md)), UI가 없습니다; IoT 셸이 백그라운드 응용 프로그램의 경우에 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="38e7b-112">In Headless mode (explained in detail [here](../learn-about-hardware/HeadlessMode.md)), there is no UI; the IoT Shell launches background applications only.</span></span>

<span data-ttu-id="38e7b-113">포그라운드 및 백그라운드 응용 프로그램 간의 주요 차이점은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="38e7b-113">Here are the main differences between foreground and background applications:</span></span>

- <span data-ttu-id="38e7b-114">**포그라운드 응용 프로그램** UI가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38e7b-114">**Foreground applications** have a UI.</span></span> <span data-ttu-id="38e7b-115">장치 헤드 모드일 때 다음 중 하나는 시작 시 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="38e7b-115">One of these is launched at startup when the device is in headed mode.</span></span> <span data-ttu-id="38e7b-116">장치에서 등록 된 모든 포그라운드 앱 및 장치 작업 하는 동안 전경 앱 간에 전환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38e7b-116">All foreground apps are registered on the device and the user can switch between foreground apps during device operation.</span></span>

- <span data-ttu-id="38e7b-117">**응용 프로그램을 백그라운드** UI 있고 따라서 UI 스택을 해제 하 여 장치 리소스를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="38e7b-117">**Background applications** have no UI and thus save device resources by turning off the UI stack.</span></span> <span data-ttu-id="38e7b-118">종종 백그라운드 응용 프로그램 시작에서 지속적으로 실행 하 고는 장치를 모니터링 하는 데 종종 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="38e7b-118">Background applications often run continuously from startup and are often used to monitor the device.</span></span>

## <a name="switching-between-apps-with-a-home-app"></a><span data-ttu-id="38e7b-119">홈 앱을 사용 하 여 앱 간 전환</span><span class="sxs-lookup"><span data-stu-id="38e7b-119">Switching between apps with a Home App</span></span>

<span data-ttu-id="38e7b-120">지금은 시작 앱을 사용 하면 다른 포그라운드 응용 프로그램 간에 전환할 수 있는 Windows 10 IoT Core 대 한 홈 앱을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38e7b-120">At the moment, the Startup App allows you to create a home app for Windows 10 IoT Core, which allows you to switch between different foreground applications.</span></span> 

<span data-ttu-id="38e7b-121">합니다 **IoT 시작 앱** ([샘플](https://developer.microsoft.com/en-us/windows/iot/samples/iotstartapp) PackageManager Api를 사용 하 여 시작 한 후 사용자의 장치에 설치 된 앱을 나열 하는 간단한 시작 앱을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="38e7b-121">The **IoT Startup App** ([sample](https://developer.microsoft.com/en-us/windows/iot/samples/iotstartapp) represents a simple startup app that lists the installed apps on your device, then launches one using the PackageManager APIs.</span></span>

## <a name="switching-between-apps-with-hid-injection-keys"></a><span data-ttu-id="38e7b-122">HID 삽입 키를 사용 하 여 앱 간 전환</span><span class="sxs-lookup"><span data-stu-id="38e7b-122">Switching between apps with HID Injection Keys</span></span>

<span data-ttu-id="38e7b-123">아래 지침 하는 방법을 보여 레지스트리에 항목을 통해 바로 가기 키 지원을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="38e7b-123">The below instructions show you how to turn on Hotkey support through entries to the registry.</span></span> <span data-ttu-id="38e7b-124">사용자 고유의 이미지를 빌드하는 하 고 지원 하려는 경우는 바로 가기 키 (홈, 이전 앱 및 다음 앱)는 레지스트리에 액세스 하지 않고도, 아래이 단계를 처리 하는 선택적 기능 패키지를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38e7b-124">If you are building your own image and want to support the below hotkeys (Home, previous app, and next app) without needing to access the registry, you can include an optional feature package that handles these steps for you.</span></span>

<span data-ttu-id="38e7b-125">검색할 기능 패키지 라고 합니다. **Microsoft-OneCore-IoTUAP-Shell-HotKeys-Feature-Package.cab** 기능 이라고 **IOT_SHELL_HOTKEY_SUPPORT**합니다.</span><span class="sxs-lookup"><span data-stu-id="38e7b-125">The feature package to look for is called: **Microsoft-OneCore-IoTUAP-Shell-HotKeys-Feature-Package.cab** and the feature is called **IOT_SHELL_HOTKEY_SUPPORT**.</span></span> <span data-ttu-id="38e7b-126">참조 된 [Settings.HotKey 샘플 패키지](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Common/Packages/Settings.HotKey/Settings.HotKey.pkg.xml) 예입니다.</span><span class="sxs-lookup"><span data-stu-id="38e7b-126">See the [Settings.HotKey sample package](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Common/Packages/Settings.HotKey/Settings.HotKey.pkg.xml) for an example.</span></span>

<span data-ttu-id="38e7b-127">이 문서의 나머지 부분에서는이 기능을 수동으로 구현 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="38e7b-127">The rest of this document covers how to implement this feature manually.</span></span>

### <a name="return-home"></a><span data-ttu-id="38e7b-128">반환 홈</span><span class="sxs-lookup"><span data-stu-id="38e7b-128">Return Home</span></span>

<span data-ttu-id="38e7b-129">Windows 10 IoT 1 주년 업데이트 (1607)를 사용 하 여 IoT 셸 키를 눌러 "GO HOME", 키보드에서 Windows 단추를 출시로 설정 되어 있는 다른 응용 프로그램이 실행 중이면 전경으로 기본 응용 프로그램 창 가져오기는 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="38e7b-129">With the Windows 10 IoT Anniversary Update (1607), the IoT Shell supports bringing the default application window to the foreground when another application is running by pressing the "GO HOME" key, which is set to the release of the Windows Button on a keyboard.</span></span> <span data-ttu-id="38e7b-130">IoT 장치의 키보드가 통해 하위 수준 키보드 이벤트를 삽입 해야 있지 않을 경우 [HID 주입](https://developer.microsoft.com/en-us/windows/iot/samples/hidinjection), "GO HOME" 기능을 앱에서 다른 키를 다시 매핑 하려는 경우에 키 값을 조정할 수 있습니다 또는 레지스트리입니다.</span><span class="sxs-lookup"><span data-stu-id="38e7b-130">If you don't have a keyboard on your IoT Device and need to inject low-level keyboard events through [HID Injection](https://developer.microsoft.com/en-us/windows/iot/samples/hidinjection), or if you just want to re-map the "GO HOME" functionality to a different key in your app, you can adjust the key value in the registry.</span></span> <span data-ttu-id="38e7b-131">예를 들어 사용할 수 있도록 이스케이프를 누르면 키 (0x1B) "이동 홈"으로, 레지스트리에서 다음 명령을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="38e7b-131">For example, to enable pressing the ESCAPE key (0x1B) to "GO HOME", enter the following command in the registry:</span></span>

``
“HKLM\Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\HotKeys” “HOME” QWORD    0x0000000 0000001B  
``

<span data-ttu-id="38e7b-132">REG 파일로이 모양은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="38e7b-132">As a REG file, this looks as follows:</span></span>

``
[HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\HotKeys]
"Home"=hex(b):1B,00,00,00,00,00,00,00
``

### <a name="switch-between-apps"></a><span data-ttu-id="38e7b-133">앱 간 전환</span><span class="sxs-lookup"><span data-stu-id="38e7b-133">Switch Between Apps</span></span>

<span data-ttu-id="38e7b-134">또는 포그라운드 응용 프로그램 사이 전환 하려는 경우 설정할 수 있습니다 Alt + Tab (다음 앱) 및 레지스트리에서 다음 명령을 입력 하 여 이미지에서 Shift-Alt + Tab (이전 앱) 기능:</span><span class="sxs-lookup"><span data-stu-id="38e7b-134">Alternatively, if you want to switch between your foreground apps, you can set up Alt-Tab (next app) and Shift-Alt-Tab (previous app) functionality in your image by entering the following command in the registry:</span></span>

``
“HKLM\Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\HotKeys”
“PREV” QWORD 0x00010000 00010009 
“NEXT” QWORD 0x00020000 00050009 
``

<span data-ttu-id="38e7b-135">REG 파일로이 모양은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="38e7b-135">As a REG file, this looks as follows:</span></span>
``
[HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\HotKeys]
"Prev"=hex(b):09,00,01,00,00,00,01,00
"Next"=hex(b):09,00,05,00,00,00,02,00
``

### <a name="bit-translation"></a><span data-ttu-id="38e7b-136">비트 변환</span><span class="sxs-lookup"><span data-stu-id="38e7b-136">Bit Translation</span></span>

<span data-ttu-id="38e7b-137">위의 레지스트리 파일 항목을 다음과 같이 왼쪽에서 오른쪽으로 디코딩:</span><span class="sxs-lookup"><span data-stu-id="38e7b-137">The above REG file entries decode left to right as follows:</span></span>

- <span data-ttu-id="38e7b-138">Bits 0-15: 가상 키 코드 (예: 1B 이스케이프는 00)입니다.</span><span class="sxs-lookup"><span data-stu-id="38e7b-138">Bits 0-15: Virtual Key Code (i.e. 1B,00 for ESCAPE).</span></span> <span data-ttu-id="38e7b-139">참조 [가상 키 코드](https://msdn.microsoft.com/library/windows/desktop/dd375731(v=vs.85).aspx) 키 코드 값의 전체 목록은</span><span class="sxs-lookup"><span data-stu-id="38e7b-139">See [Virtual Key Code](https://msdn.microsoft.com/library/windows/desktop/dd375731(v=vs.85).aspx) for the complete list of key code values</span></span>
- <span data-ttu-id="38e7b-140">16-19 비트: 보조키입니다.</span><span class="sxs-lookup"><span data-stu-id="38e7b-140">Bits 16-19: Modifier Key.</span></span> <span data-ttu-id="38e7b-141">0x0 = 없음 한정자가 0x1 ALT, 0x2 = CTRL 및 0x4 = SHIFT =.</span><span class="sxs-lookup"><span data-stu-id="38e7b-141">0x0 = No Modifier, 0x1 = ALT, 0x2 = CTRL, and 0x4 = SHIFT.</span></span> <span data-ttu-id="38e7b-142">값을 함께 추가 키 조합 (예: ALT + SHIFT는 0x5)</span><span class="sxs-lookup"><span data-stu-id="38e7b-142">Combining keys adds the values together (i.e. ALT+SHIFT is 0x5)</span></span>
- <span data-ttu-id="38e7b-143">Bits 20-47: 사용 하도록 예약 됩니다. 0 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38e7b-143">Bits 20-47: Reserved for future use; must be 0</span></span>
- <span data-ttu-id="38e7b-144">48 62 비트:  작업</span><span class="sxs-lookup"><span data-stu-id="38e7b-144">Bits 48-62:  Action</span></span>
    - <span data-ttu-id="38e7b-145">0 = 홈</span><span class="sxs-lookup"><span data-stu-id="38e7b-145">0 = Home</span></span>
    - <span data-ttu-id="38e7b-146">1 = 이전 뷰 (향후 릴리스에서 작동 하지 않을 수 있습니다)</span><span class="sxs-lookup"><span data-stu-id="38e7b-146">1 = Previous View (may not work in future releases)</span></span>
    - <span data-ttu-id="38e7b-147">2 = 다음 뷰 (향후 릴리스에서 작동 하지 않을 수 있습니다)</span><span class="sxs-lookup"><span data-stu-id="38e7b-147">2 = Next View (may not work in future releases)</span></span>
- <span data-ttu-id="38e7b-148">63 비트: 예약 되었습니다. 0 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38e7b-148">Bit 63: Reserved; must be 0</span></span>

