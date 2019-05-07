---
title: Windows 10 IoT Core 개요
author: saraclay
ms.author: saclayt
ms.date: 01/18/2018
ms.topic: article
description: Windows 10 IoT Core 란 무엇 이며이 사용 하 여 수행할 수 있는 작업에 대해 알아봅니다.
keywords: Windows 10 IoT Core 헤드리스 작은 공간
ms.openlocfilehash: d5b9c59ad735d66b4812e6303f6298a33da44d33
ms.sourcegitcommit: 1f6afcfee0cb5557dc21c7b15e199bc557d8eedb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65171355"
---
# <a name="windows-10-iot-core"></a><span data-ttu-id="3fae1-104">Windows 10 IoT Core K</span><span class="sxs-lookup"><span data-stu-id="3fae1-104">Windows 10 IoT Core</span></span>

> [!NOTE]
> <span data-ttu-id="3fae1-105">만 Windows 10 컨테이너 Microsoft Azure IoT Edge를 활용 하는 상업용 배포에 대 한 Windows IoT Core 및 Windows IoT Enterprise를 사용 하 여 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3fae1-105">Windows 10 Containers can only be used with Windows IoT Core and Windows IoT Enterprise for commercial deployments utilizing Microsoft Azure IoT Edge.</span></span>

## <a name="what-is-windows-10-iot-core"></a><span data-ttu-id="3fae1-106">Windows 10 IoT Core 란?</span><span class="sxs-lookup"><span data-stu-id="3fae1-106">What is Windows 10 IoT Core?</span></span>
<span data-ttu-id="3fae1-107">Windows 10 IoT Core 모두 ARM에서 실행 되는 작은 장치 디스플레이 유무 및 x86 x64 장치에 최적화 된 Windows 10의 버전.</span><span class="sxs-lookup"><span data-stu-id="3fae1-107">Windows 10 IoT Core is a version of Windows 10 that is optimized for smaller devices with or without a display that run on both ARM and x86/x64 devices.</span></span> <span data-ttu-id="3fae1-108">Windows IoT Core 설명서에서 연결, 관리, 업데이트, 장치 및 기타 보안 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="3fae1-108">The Windows IoT Core documentation provides information on connecting, managing, updating, securing your devices, and more.</span></span> 

## <a name="getting-started"></a><span data-ttu-id="3fae1-109">시작</span><span class="sxs-lookup"><span data-stu-id="3fae1-109">Getting started</span></span>
<span data-ttu-id="3fae1-110">Windows 10 IoT Core 사용 하 여 시작 하려면 만들었습니다를 [Windows 10 IoT Core Quickstarter](tutorials/Tutorials.md) 플랫폼을 사용 하 여 친숙 한 신속 하 게 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3fae1-110">To get started with Windows 10 IoT Core, we've created a [Windows 10 IoT Core Quickstarter](tutorials/Tutorials.md) to help you get familiar with the platform quickly.</span></span> 

<span data-ttu-id="3fae1-111">여기에서 사용자 고유의 응용 프로그램을 개발 하 여 플랫폼을 사용 하 여 실험을 시장에 장치를 적용할 계획 시작 또는 장치의 상용화할 계속 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3fae1-111">From there, you can continue to experiment with the platform by developing your own application or start making plans to bring your device to market, or commercialize your device.</span></span> <span data-ttu-id="3fae1-112">참조 섹션에서 출시 Bring 장치 상용화 사용을 시작 합니다 [시작된 문서](https://docs.microsoft.com/windows/iot-core/getstarted)합니다.</span><span class="sxs-lookup"><span data-stu-id="3fae1-112">To get started with commercializing, see the Bring a device to market section in the [Get started article](https://docs.microsoft.com/windows/iot-core/getstarted).</span></span>

## <a name="differences-between-windows-10-desktop-and-windows-10-iot-core"></a><span data-ttu-id="3fae1-113">Windows 10 Desktop 및 Windows 10 IoT Core 차이점</span><span class="sxs-lookup"><span data-stu-id="3fae1-113">Differences between Windows 10 Desktop and Windows 10 IoT Core</span></span>

### <a name="different-features-available-on-desktop-and-iot-core"></a><span data-ttu-id="3fae1-114">데스크톱 및 IoT Core에서 사용할 수 있는 다양 한 기능</span><span class="sxs-lookup"><span data-stu-id="3fae1-114">Different features available on Desktop and IoT Core</span></span>

* <span data-ttu-id="3fae1-115">받은 편지함 Cortana를 더 이상 1809 (17763) 버전부터 Windows 10 IoT Core 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3fae1-115">Inbox Cortana is no longer available on Windows 10 IoT Core since version 1809 (17763).</span></span> <span data-ttu-id="3fae1-116">빠르게 시장에 음성 기능을 사용할 장치를 찾으려는 경우 Cortana 지원을 사용 하 여 장치에 통합할 수 있습니다 합니다 [Cortana 디바이스 SDK의 미리 보기](https://developer.microsoft.com/en-us/cortana/devices)합니다.</span><span class="sxs-lookup"><span data-stu-id="3fae1-116">If you are looking to bring a voice-enabled device to market quickly, you can integrate Cortana support into the device using the [preview of the Cortana Devices SDK](https://developer.microsoft.com/en-us/cortana/devices).</span></span>
* <span data-ttu-id="3fae1-117">합니다 [FileOpenPicker API](https://docs.microsoft.com/en-us/uwp/api/windows.storage.pickers.fileopenpicker) Windows 10 IoT Core 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3fae1-117">The [FileOpenPicker API](https://docs.microsoft.com/en-us/uwp/api/windows.storage.pickers.fileopenpicker) is not supported in Windows 10 IoT Core.</span></span> <span data-ttu-id="3fae1-118">로컬 드라이브 또는 이동식 저장소에 액세스 하려면 사용자 고유의 응용 프로그램에서이 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3fae1-118">To access local drives or removable storage, you can implement this in your own application.</span></span>
* <span data-ttu-id="3fae1-119">Windows 10 IoT Core 장치로 부팅 합니다 [기본 앱](https://docs.microsoft.com/en-us/windows/iot-core/develop-your-app/iotcoredefaultapp) 같은 데스크톱 PC 대신 합니다.</span><span class="sxs-lookup"><span data-stu-id="3fae1-119">The Windows 10 IoT Core device will boot to the [default app](https://docs.microsoft.com/en-us/windows/iot-core/develop-your-app/iotcoredefaultapp) instead of a desktop-like PC.</span></span> <span data-ttu-id="3fae1-120">이 응용 프로그램의 목적은 최초 부팅 시 상호 작용할 수 있지만 사용할 수 있도록 하는 친숙 한 셸을 제공 합니다 [오픈 소스 코드](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/IoTCoreDefaultApp) 이 응용 프로그램에 대 한 플러그 앤 플레이에 이러한 기능을 사용할 수 있도록 사용자 고유의 사용자 지정 응용 프로그램입니다.</span><span class="sxs-lookup"><span data-stu-id="3fae1-120">The purpose of this application is not only to provide you with a friendly shell to interact with upon first boot, but to also allow you to use the [open-sourced code](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/IoTCoreDefaultApp) for this application so that you can use these features to plug and play your own custom application(s).</span></span>

### <a name="differences-in-driver-supported-areas"></a><span data-ttu-id="3fae1-121">드라이버에서 지 원하는 영역의 차이점</span><span class="sxs-lookup"><span data-stu-id="3fae1-121">Differences in driver-supported areas</span></span>

* <span data-ttu-id="3fae1-122">Windows 10 Desktop에는 Windows 10 IoT Core 보다 드라이버 지원 더 합니다.</span><span class="sxs-lookup"><span data-stu-id="3fae1-122">Windows 10 Desktop has more supported drivers than Windows 10 IoT Core.</span></span> <span data-ttu-id="3fae1-123">바탕 화면에서 Windows 10 IoT Core 장치에 대 한 원본에서 드라이버를 빌드 또는 ARM 아키텍처에 대 한 특히 다른 문제를 해결 하려면 찾을 해야 할 수 있습니다를 동일 하 게 하려면 Windows 10 IoT Core 장치 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="3fae1-123">To make the same device(s) work on Windows 10 IoT Core as on Desktop, you may need to build a driver from soruce for a Windows 10 IoT Core device or find another workaround, especially for ARM architecture.</span></span>
* <span data-ttu-id="3fae1-124">Windows 10 IoT Core (ARM)에 대 한 libusb에 대 한 기본 제공 드라이버가 없는-ARM 아키텍처를 대상으로 하는 원본에서 작성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3fae1-124">There is no out-of-the-box driver for libusb for Windows 10 IoT Core (ARM) - you will need to build from source to target the ARM architecture.</span></span>

### <a name="differences-in-available-registry-set"></a><span data-ttu-id="3fae1-125">사용 가능한 레지스트리 설정의 차이점</span><span class="sxs-lookup"><span data-stu-id="3fae1-125">Differences in available registry set</span></span>

* <span data-ttu-id="3fae1-126">바탕 화면에서 "자동 숨기기 스크롤 막대의 Windows" off로 설정할 수 있는 하는 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3fae1-126">On desktop, there is an option to "Automatically hide scroll bars in Windows" that can be set to off.</span></span> <span data-ttu-id="3fae1-127">다음 레지스트리 항목에 의해 제어 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3fae1-127">It is controlled by the following registry entry:</span></span> 

```
HKEY_CURRENTUSER\Control Panel\Accessibility
```

* <span data-ttu-id="3fae1-128">기본적으로 Windows 10 IoT Core 장치에 이러한 레지스트리 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3fae1-128">There is no such registry on Windows 10 IoT Core devices by default.</span></span> <span data-ttu-id="3fae1-129">원하는 경우 "동적 스크롤 막대" 등록을 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3fae1-129">You will need to add a "Dynamic Scrollbars" register if you want.</span></span>
* <span data-ttu-id="3fae1-130">UWP 응용 프로그램에서 자동 숨기기 스크롤 막대를 사용 하려면 등록 하 고 값이 같은 "1"을 설정 하는 "DynamicScrollbars"를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3fae1-130">To enable hide scroll bars automatically in a UWP application, you can add the "DynamicScrollbars" register and set the value to "1" like this:</span></span>

```
REG ADD "HKCU\Control Panel\Accessibility" /v DynamicScrollbars /t REG_DWORD \d "1"
```

* <span data-ttu-id="3fae1-131">기본 계정에서 레지스트리 키를 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3fae1-131">The registry key must be set from the Default Account.</span></span> <span data-ttu-id="3fae1-132">ScrollViewer의 XAML 설정이 "Visible" 인 경우 0 nthe 레지스트리 설정을 스크롤 막대 표시 여부 regardlss를 강제로 스크롤 UI에 표시 하도록 충분 한 콘텐츠가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3fae1-132">If the ScrollViewer's XAML setting is "Visible", the nthe registry setting of 0 will force the scroll bar to appear regardlss of whether there is sufficient content to have the scroll appear in the UI.</span></span> <span data-ttu-id="3fae1-133">레지스트리 설정을 1은 충분 한 콘텐츠가 있을 때까지 숨겨진 스크롤 막대를 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="3fae1-133">A registry setting of 1 will keep the scroll bar hidden until there is sufficient content.</span></span>

```
<TextBox Height="200" Width="100" IsEnabled="True" FontSize="50" TextWrapping="Wrap" ScrollViewer.VerticalScrollBarVisibility="Visible" Text="..."/>
```

* <span data-ttu-id="3fae1-134">마지막으로, ScrollViewer XAML의 설정이 "Auto" 경우 다음 레지스트리 설정을 0만 표시 됩니다 전체 스크롤 막대를 충분 한 콘텐츠가 스크롤 막대를 표시 하는 경우.</span><span class="sxs-lookup"><span data-stu-id="3fae1-134">Lastly, if the ScrollViewer XAML's setting is "Auto" then the registry setting of 0 will only show the full scroll bar when there is enough content to display the scroll bar.</span></span> <span data-ttu-id="3fae1-135">레지스트리 설정을 1 이면 내용이 없을 때 콘텐츠 또는 숨겨진 경우에 충분 한 후 스크롤 막대에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3fae1-135">When the registry setting is 1, the scroll bar will appear then when there is enough content or hidden if there is no content.</span></span>

```
<TextBox Height="200" Width="100" IsEnabled="True" FontSize="50" TextWrapping="Wrap" ScrollViewer.VerticalScrollBarVisibility="Auto" Text="..."/>
```

### <a name="different-commands-supported"></a><span data-ttu-id="3fae1-136">지원 되는 다른 명령</span><span class="sxs-lookup"><span data-stu-id="3fae1-136">Different commands supported</span></span>

* <span data-ttu-id="3fae1-137">제거-AppxPackage PowerShell 명령에는 Windows 10 IoT Core는 없지만 데스크톱에서 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="3fae1-137">The PowerShell Remove-AppxPackage command works on Dekstop but not on Windows 10 IoT Core.</span></span>
* <span data-ttu-id="3fae1-138">장치에서 일부 폴더 유니버설 Windows 앱에서 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3fae1-138">Not all folders on your device are accessible by Universal Windows Apps.</span></span> <span data-ttu-id="3fae1-139">Windows 10 IoT Core는 폴더에 UWP 앱에 액세스할 수 있도록 FolderPermissions 도구를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3fae1-139">On Windows 10 IoT Core you can use the FolderPermissions tool to make a folder accessible to a UWP app.</span></span> <span data-ttu-id="3fae1-140">예를 들어 c:\test 폴더에 UWP 앱 액세스 권한을 부여 하려면 FolderPermissions c:\test-e를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="3fae1-140">For example, run FolderPermissions c:\test -e to give UWP apps access to c:\test folder.</span></span> <span data-ttu-id="3fae1-141">그러나, 바탕 화면에서 가능 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3fae1-141">However, this is not available on Desktop.</span></span>

<span data-ttu-id="3fae1-142">이 게시물에서 설명 하는 모든 차이점 유효 하지 않을 나중에 Windows 10 IoT Core 지속적으로 업데이트 되 고 있어.</span><span class="sxs-lookup"><span data-stu-id="3fae1-142">All differences described in this post may not be valid in the future because Windows 10 IoT Core is constantly being updated.</span></span>

## <a name="helpful-resources"></a><span data-ttu-id="3fae1-143">유용한 리소스</span><span class="sxs-lookup"><span data-stu-id="3fae1-143">Helpful resources</span></span>
<span data-ttu-id="3fae1-144">[설명서 읽기](https://docs.microsoft.com/windows/iot-core/) Windows 10 IoT Core 자세히 알아보려면 합니다.</span><span class="sxs-lookup"><span data-stu-id="3fae1-144">[Read our documentation](https://docs.microsoft.com/windows/iot-core/) to learn more about Windows 10 IoT Core.</span></span>
