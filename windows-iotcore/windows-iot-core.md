---
title: Windows 10 IoT Core 개요
author: saraclay
ms.author: saclayt
ms.date: 01/18/2018
ms.topic: article
description: Windows 10 IoT Core가 무엇인지와 이를 통해 수행할 수 있는 작업에 대해 알아봅니다.
keywords: Windows 10 IoT Core, 작은 사용 공간, 헤드리스
ms.openlocfilehash: 15a3d3e5f1703f87b0f0a0c782bb4cab9b99557f
ms.sourcegitcommit: 9ec4716afde25fdc8b94f7c0794448501f451b55
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/17/2019
ms.locfileid: "66263863"
---
# <a name="an-overview-of-windows-10-iot-core"></a><span data-ttu-id="f8cfa-104">Windows 10 IoT Core 개요</span><span class="sxs-lookup"><span data-stu-id="f8cfa-104">An overview of Windows 10 IoT Core</span></span>

> [!NOTE]
> <span data-ttu-id="f8cfa-105">Windows 10 컨테이너는 Microsoft Azure IoT Edge를 활용하는 상업용 배포를 위해 Windows IoT Core 및 Windows IoT Enterprise에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8cfa-105">Windows 10 Containers can only be used with Windows IoT Core and Windows IoT Enterprise for commercial deployments utilizing Microsoft Azure IoT Edge.</span></span>

## <a name="what-is-windows-10-iot-core"></a><span data-ttu-id="f8cfa-106">Windows 10 IoT Core란?</span><span class="sxs-lookup"><span data-stu-id="f8cfa-106">What is Windows 10 IoT Core?</span></span>
<span data-ttu-id="f8cfa-107">Windows 10 IoT Core는 ARM과 x86/x64 디바이스에서 실행되는 디스플레이가 있거나 없는 소형 디바이스에 최적화된 Windows 10 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="f8cfa-107">Windows 10 IoT Core is a version of Windows 10 that is optimized for smaller devices with or without a display that run on both ARM and x86/x64 devices.</span></span> <span data-ttu-id="f8cfa-108">Windows IoT Core 설명서는 디바이스 연결, 관리, 업데이트, 보안 등에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f8cfa-108">The Windows IoT Core documentation provides information on connecting, managing, updating, securing your devices, and more.</span></span> 

<span data-ttu-id="f8cfa-109">다음 수준으로 이동하여 솔루션 상용화를 시작할 준비가 된 경우 [Windows 10 IoT Core 제조 가이드](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)를 통해 Windows 10 IoT Core로 제조하는 방법을 알아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8cfa-109">If you're ready to go to the next level and start commercializing your solution, you can learn how to manufacture with Windows 10 IoT Core with our [Windows 10 IoT Core Manufacturing Guide](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).</span></span> 

## <a name="getting-started"></a><span data-ttu-id="f8cfa-110">시작</span><span class="sxs-lookup"><span data-stu-id="f8cfa-110">Getting started</span></span>

<span data-ttu-id="f8cfa-111">디바이스를 제작하기 전에, 먼저 Windows 10 IoT Core를 사용하여 디바이스의 프로토타입을 만드는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f8cfa-111">Before attempting to manufacture a device, it's best to first try and prototype a device with Windows 10 IoT Core.</span></span> <span data-ttu-id="f8cfa-112">이렇게 하면 디바이스를 만들 때 어떤 기능이 필요하고 어떤 구성을 원하는지 알아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8cfa-112">That way, you can understand what features you'll need and what configurations you'll want when it's time to manufacture.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="f8cfa-113">항목</span><span class="sxs-lookup"><span data-stu-id="f8cfa-113">Topic</span></span></th>
<th align="left"><span data-ttu-id="f8cfa-114">설명</span><span class="sxs-lookup"><span data-stu-id="f8cfa-114">Description</span></span></th>
</tr>
</thead>
<tbody>

<tr class="odd">
<td align="left"><p><span data-ttu-id="f8cfa-115"><a href="https://docs.microsoft.com/en-us/windows/iot-core/tutorials/quickstarter/PrototypeBoards"
>1. 프로토타입 보드 선택</a></span><span class="sxs-lookup"><span data-stu-id="f8cfa-115"><a href="https://docs.microsoft.com/en-us/windows/iot-core/tutorials/quickstarter/PrototypeBoards"
>1. Pick a prototype board</a></span></span></p></td>
<td align="left"><p><span data-ttu-id="f8cfa-116">일반 프로토타입 보드를 살펴보고 프로토타입 제작에 사용할 프로토타입 보드를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f8cfa-116">Take a look at common prototype boards and choose one to start prototyping with.</span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><p><span data-ttu-id="f8cfa-117">2. 프로토타입 이미지 플래시</span><span class="sxs-lookup"><span data-stu-id="f8cfa-117">2. Flash a prototype image</span></span></p></td>
<td align="left"><p><span data-ttu-id="f8cfa-118">선택한 디바이스에 프로토타입 이미지를 플래시하는 방법을 알아보려면 자습서 섹션으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="f8cfa-118">Go to our tutorial sections to learn how to flash prototype images onto your selected device(s).</span></span> </p></td>
</tr>

<tr class="odd">
<td align="left"><p><span data-ttu-id="f8cfa-119"><a href="https://docs.microsoft.com/en-us/windows/iot-core/develop-your-app/appinstaller">2. 3. 앱 설치</a></span><span class="sxs-lookup"><span data-stu-id="f8cfa-119"><a href="https://docs.microsoft.com/en-us/windows/iot-core/develop-your-app/appinstaller">2. 3. Install your app</a></span></span></p></td>
<td align="left"><p><span data-ttu-id="f8cfa-120">다양한 도구를 사용하여 앱을 설치하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="f8cfa-120">Learn how to install your app using different tools.</span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><p><span data-ttu-id="f8cfa-121"><a href="https://docs.microsoft.com/en-us/windows/iot-core/develop-your-app/appdeployment">4. 앱 배포</a></span><span class="sxs-lookup"><span data-stu-id="f8cfa-121"><a href="https://docs.microsoft.com/en-us/windows/iot-core/develop-your-app/appdeployment">4. Deploy your app</a></span></span></p></td>
<td align="left"><p><span data-ttu-id="f8cfa-122">Visual Studio를 사용하여 앱을 배포하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="f8cfa-122">Learn how to deploy an app using Visual Studio.</span></span></p></td>
</tr>

</tbody>
</table>

## <a name="differences-between-windows-10-desktop-and-windows-10-iot-core"></a><span data-ttu-id="f8cfa-123">Windows 10 Desktop과 Windows 10 IoT Core의 차이점</span><span class="sxs-lookup"><span data-stu-id="f8cfa-123">Differences between Windows 10 Desktop and Windows 10 IoT Core</span></span>

### <a name="different-features-available-on-desktop-and-iot-core"></a><span data-ttu-id="f8cfa-124">데스크톱 및 IoT Core에서 사용할 수 있는 다양한 기능</span><span class="sxs-lookup"><span data-stu-id="f8cfa-124">Different features available on Desktop and IoT Core</span></span>

* <span data-ttu-id="f8cfa-125">받은 편지함 Cortana는 버전 1809(17763) 이후 Windows 10 IoT Core에서 더 이상 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f8cfa-125">Inbox Cortana is no longer available on Windows 10 IoT Core since version 1809 (17763).</span></span> <span data-ttu-id="f8cfa-126">음성 사용 디바이스를 빠르게 출시하려는 경우 [Cortana 디바이스 SDK의 미리 보기](https://developer.microsoft.com/en-us/cortana/devices)를 사용하여 Cortana 지원을 디바이스에 통합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8cfa-126">If you are looking to bring a voice-enabled device to market quickly, you can integrate Cortana support into the device using the [preview of the Cortana Devices SDK](https://developer.microsoft.com/en-us/cortana/devices).</span></span>
* <span data-ttu-id="f8cfa-127">[FileOpenPicker API](https://docs.microsoft.com/en-us/uwp/api/windows.storage.pickers.fileopenpicker)는 Windows 10 IoT Core에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f8cfa-127">The [FileOpenPicker API](https://docs.microsoft.com/en-us/uwp/api/windows.storage.pickers.fileopenpicker) is not supported in Windows 10 IoT Core.</span></span> <span data-ttu-id="f8cfa-128">로컬 드라이브 또는 이동식 스토리지에 액세스하려면 이를 자신의 애플리케이션에서 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="f8cfa-128">To access local drives or removable storage, you can implement this in your own application.</span></span>
* <span data-ttu-id="f8cfa-129">기본적으로 Windows 10 IoT Core 디바이스가 데스크톱과 같은 PC 대신 [기본 앱](https://docs.microsoft.com/en-us/windows/iot-core/develop-your-app/iotcoredefaultapp)으로 부팅됩니다.</span><span class="sxs-lookup"><span data-stu-id="f8cfa-129">Out of the box, The Windows 10 IoT Core device will boot to the [default app](https://docs.microsoft.com/en-us/windows/iot-core/develop-your-app/iotcoredefaultapp) instead of a desktop-like PC.</span></span> <span data-ttu-id="f8cfa-130">그러나 상용화를 위해서는 이 기본 앱을 수정할 수 있는 사용자 지정 앱이나 기본 앱으로 대체**해야** 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8cfa-130">However, for commercialization, this default app **must** be replaced by either a custom app or a default app that can be modified.</span></span> <span data-ttu-id="f8cfa-131">이 애플리케이션의 목적은 최초 부팅 시 상호 작용할 수 있는 친숙한 셸을 제공할 뿐만 아니라, 이 애플리케이션에 대해 [오픈 소스 코드](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/IoTCoreDefaultApp)를 사용할 수 있도록 함으로써 이러한 기능을 사용하여 고유한 사용자 지정 애플리케이션을 플러그 앤 플레이할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8cfa-131">The purpose of this application is not only to provide you with a friendly shell to interact with upon first boot, but to also allow you to use the [open-sourced code](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/IoTCoreDefaultApp) for this application so that you can use these features to plug and play your own custom application(s).</span></span>

### <a name="differences-in-driver-supported-areas"></a><span data-ttu-id="f8cfa-132">드라이버 지원 영역의 차이점</span><span class="sxs-lookup"><span data-stu-id="f8cfa-132">Differences in driver-supported areas</span></span>

* <span data-ttu-id="f8cfa-133">Windows 10 Desktop에는 Windows 10 IoT Core보다 지원 드라이버가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="f8cfa-133">Windows 10 Desktop has more supported drivers than Windows 10 IoT Core.</span></span> <span data-ttu-id="f8cfa-134">Windows 10 IoT Core에서 테스크톱에서와 동일한 디바이스를 작동시키려면 Windows 10 IoT Core 디바이스용 원본에서 드라이버를 빌드하거나, 특히 ARM 아키텍처에 대한 다른 해결 방법을 찾아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8cfa-134">To make the same device(s) work on Windows 10 IoT Core as on Desktop, you may need to build a driver from soruce for a Windows 10 IoT Core device or find another workaround, especially for ARM architecture.</span></span>
* <span data-ttu-id="f8cfa-135">Windows 10 IoT Core(ARM)용 libusb에 대한 기본 제공 드라이버가 없습니다. ARM 아키텍처를 대상으로 하는 원본에서 빌드해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8cfa-135">There is no out-of-the-box driver for libusb for Windows 10 IoT Core (ARM) - you will need to build from source to target the ARM architecture.</span></span>

### <a name="differences-in-available-registry-set"></a><span data-ttu-id="f8cfa-136">사용 가능한 레지스트리 집합의 차이점</span><span class="sxs-lookup"><span data-stu-id="f8cfa-136">Differences in available registry set</span></span>

* <span data-ttu-id="f8cfa-137">데스크톱에서는 "Windows의 스크롤 막대를 자동으로 숨기기" 옵션을 off로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8cfa-137">On desktop, there is an option to "Automatically hide scroll bars in Windows" that can be set to off.</span></span> <span data-ttu-id="f8cfa-138">다음 레지스트리 항목에 의해 제어됩니다.</span><span class="sxs-lookup"><span data-stu-id="f8cfa-138">It is controlled by the following registry entry:</span></span> 

```
HKEY_CURRENTUSER\Control Panel\Accessibility
```

* <span data-ttu-id="f8cfa-139">기본적으로 Windows 10 IoT Core 디바이스에는 이러한 레지스트리가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f8cfa-139">There is no such registry on Windows 10 IoT Core devices by default.</span></span> <span data-ttu-id="f8cfa-140">원하는 경우 "동적 스크롤 막대" 레지스터를 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8cfa-140">You will need to add a "Dynamic Scrollbars" register if you want.</span></span>
* <span data-ttu-id="f8cfa-141">UWP 애플리케이션에서 자동으로 스크롤 막대 숨기기를 활성화하려면 "DynamicScrollbars"를 추가하고 다음과 같이 값을 "1"로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f8cfa-141">To enable hide scroll bars automatically in a UWP application, you can add the "DynamicScrollbars" register and set the value to "1" like this:</span></span>

```
REG ADD "HKCU\Control Panel\Accessibility" /v DynamicScrollbars /t REG_DWORD \d "1"
```

* <span data-ttu-id="f8cfa-142">레지스트리 키는 기본 계정에서 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8cfa-142">The registry key must be set from the Default Account.</span></span> <span data-ttu-id="f8cfa-143">ScrollViewer의 XAML 설정이 "Visible"인 경우, nthe 레지스트리 설정 0은 UI에 스크롤을 표시하기에 충분한 콘텐츠가 있는지 여부와 상관없이 스크롤 막대를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f8cfa-143">If the ScrollViewer's XAML setting is "Visible", the nthe registry setting of 0 will force the scroll bar to appear regardlss of whether there is sufficient content to have the scroll appear in the UI.</span></span> <span data-ttu-id="f8cfa-144">레지스트리 설정 1은 충분한 콘텐츠가 있을 때까지 스크롤 막대가 숨겨집니다.</span><span class="sxs-lookup"><span data-stu-id="f8cfa-144">A registry setting of 1 will keep the scroll bar hidden until there is sufficient content.</span></span>

```
<TextBox Height="200" Width="100" IsEnabled="True" FontSize="50" TextWrapping="Wrap" ScrollViewer.VerticalScrollBarVisibility="Visible" Text="..."/>
```

* <span data-ttu-id="f8cfa-145">마지막으로, ScrollViewer XAML의 설정이 "Auto"인 경우 레지스트리 설정 0은 스크롤 막대를 표시할 수 있는 충분한 콘텐츠가 있을 때에만 전체 스크롤 막대를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f8cfa-145">Lastly, if the ScrollViewer XAML's setting is "Auto" then the registry setting of 0 will only show the full scroll bar when there is enough content to display the scroll bar.</span></span> <span data-ttu-id="f8cfa-146">레지스트리 설정이 1이면 콘텐츠가 충분하거나 콘텐츠가 없으면 숨겨진 스크롤 막대가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f8cfa-146">When the registry setting is 1, the scroll bar will appear then when there is enough content or hidden if there is no content.</span></span>

```
<TextBox Height="200" Width="100" IsEnabled="True" FontSize="50" TextWrapping="Wrap" ScrollViewer.VerticalScrollBarVisibility="Auto" Text="..."/>
```

### <a name="different-commands-supported"></a><span data-ttu-id="f8cfa-147">지원되는 다른 명령</span><span class="sxs-lookup"><span data-stu-id="f8cfa-147">Different commands supported</span></span>

* <span data-ttu-id="f8cfa-148">PowerShell Remove-AppxPackage 명령은 데스크톱에서 작동하지만 Windows 10 IoT Core에서는 작동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f8cfa-148">The PowerShell Remove-AppxPackage command works on Dekstop but not on Windows 10 IoT Core.</span></span>
* <span data-ttu-id="f8cfa-149">유니버설 Windows 앱에서는 디바이스의 모든 폴더에 액세스할 수 있는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="f8cfa-149">Not all folders on your device are accessible by Universal Windows Apps.</span></span> <span data-ttu-id="f8cfa-150">Windows 10 IoT Core에서는 FolderPermissions 도구를 사용하여 UWP 앱에서 액세스할 수 있는 폴더를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8cfa-150">On Windows 10 IoT Core you can use the FolderPermissions tool to make a folder accessible to a UWP app.</span></span> <span data-ttu-id="f8cfa-151">예를 들어 FolderPermissions c:\test -e를 실행하여 UWP 앱에 c:\test 폴더에 대한 액세스 권한을 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="f8cfa-151">For example, run FolderPermissions c:\test -e to give UWP apps access to c:\test folder.</span></span> <span data-ttu-id="f8cfa-152">그러나 데스크톱에서는 이 기능을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f8cfa-152">However, this is not available on Desktop.</span></span>

<span data-ttu-id="f8cfa-153">Windows 10 IoT Core가 지속적으로 업데이트되고 있기 때문에 이 게시물에 설명된 모든 차이점은 향후에 유효하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8cfa-153">All differences described in this post may not be valid in the future because Windows 10 IoT Core is constantly being updated.</span></span>

## <a name="helpful-resources"></a><span data-ttu-id="f8cfa-154">유용한 리소스</span><span class="sxs-lookup"><span data-stu-id="f8cfa-154">Helpful resources</span></span>
<span data-ttu-id="f8cfa-155">Windows 10 IoT Core에 대해 자세히 알아보려면 [설명서를 읽어보세요](https://docs.microsoft.com/windows/iot-core/).</span><span class="sxs-lookup"><span data-stu-id="f8cfa-155">[Read our documentation](https://docs.microsoft.com/windows/iot-core/) to learn more about Windows 10 IoT Core.</span></span>
