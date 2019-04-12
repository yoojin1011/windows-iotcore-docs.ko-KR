---
title: 번개 공급자
author: msalehmsft
ms.author: msaleh
ms.date: 08/28/2017
ms.topic: article
description: Microosft 번개 공급자 라이브러리를 사용 하는 방법을 자세히 알아봅니다.
keywords: windows iot, 번개 공급자 번개 성능 테스트, 버스
ms.openlocfilehash: 8f290bf741f64e07b7b048287128e1ae42ef6b9e
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513622"
---
# <a name="working-with-lightning-providers"></a><span data-ttu-id="7d27d-104">번개 공급자 작업</span><span class="sxs-lookup"><span data-stu-id="7d27d-104">Working with lightning providers</span></span>
<span data-ttu-id="7d27d-105">Microsoft.IoT.Lightning.Providers 라이브러리 집합에 포함 된의 공급자에서 보드를 사용 하 여 인터페이스를 통해 번개 컨트롤러 버스 직접 메모리 매핑된 드라이버 (DMAP).</span><span class="sxs-lookup"><span data-stu-id="7d27d-105">The Microsoft.IoT.Lightning.Providers library contains a set of providers to interface with the on board controller buses through the Lightning direct memory mapped driver (DMAP).</span></span>


## <a name="about-the-direct-memory-mapped-driver-dmap"></a><span data-ttu-id="7d27d-106">직접 메모리에 대 한 드라이버 (DMAP) 매핑</span><span class="sxs-lookup"><span data-stu-id="7d27d-106">About the direct memory mapped driver (DMAP)</span></span>

<span data-ttu-id="7d27d-107">DMAP 드라이버는 기본 드라이버를 통해 GPIO 성능 향상을 제공 하는 개발에서 드라이버.</span><span class="sxs-lookup"><span data-stu-id="7d27d-107">The DMAP driver is an in-development driver that provides GPIO performance improvements over the default inbox driver.</span></span> <span data-ttu-id="7d27d-108">이러한 성능 향상에 대 한 자세한 내용은 방문에 대해 알아보려면 합니다 [번개 성능 테스트](../develop-your-app/LightningPerformance.md) 페이지입니다.</span><span class="sxs-lookup"><span data-stu-id="7d27d-108">To learn more about these performance improvements visit the [Lightning Performance Testing](../develop-your-app/LightningPerformance.md) page.</span></span>

<span data-ttu-id="7d27d-109">DMAP 드라이버 제품 GPIO 성능 향상 드라이버를 하는 동안 컨트롤러 명령은 각 컨트롤러에 대 한 사용자 모드 메모리 매핑된 주소를 통해 DMAP 드라이버에 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7d27d-109">While DMAP driver offer GPIO performance improvements over the Inbox driver, controller commands are sent to the DMAP driver through user-mode memory mapped addresses for each of the controllers.</span></span> <span data-ttu-id="7d27d-110">만 Microsoft.IoT.Lightning.Providers 또는 번개 공급자 Api 사용 하는 앱입니다.</span><span class="sxs-lookup"><span data-stu-id="7d27d-110">An app that only uses the Lightning provider APIs or Microsoft.IoT.Lightning.Providers.</span></span> <span data-ttu-id="7d27d-111">그러나 악성 앱은 해당 메모리를 직접 작성 하 고 하드웨어/보안 문제를 일으킬 수. 있습니다</span><span class="sxs-lookup"><span data-stu-id="7d27d-111">However, a malicious app would be able to write directly to that memory and cause hardware/security issues.</span></span> <span data-ttu-id="7d27d-112">신뢰할 수 있는 앱만을 사용 하 여 컴퓨터를 DMAP는 일반적으로 안전 하 게 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d27d-112">On a machine with only trusted apps, the DMAP is generally safe to use.</span></span>   

## <a name="obtaining-the-library"></a><span data-ttu-id="7d27d-113">라이브러리 가져오기</span><span class="sxs-lookup"><span data-stu-id="7d27d-113">Obtaining the library</span></span>

<span data-ttu-id="7d27d-114">라이브러리의 일부로 제공 되는 [번개 SDK Nuget 패키지](https://www.nuget.org/packages/Microsoft.IoT.Lightning) 에서 사용할 수 있는 소스 코드를 사용 하 여 [GitHub ms-iot/번개 리포지토리](https://github.com/ms-iot/lightning/)합니다.</span><span class="sxs-lookup"><span data-stu-id="7d27d-114">The library is provided as part of the [Lightning SDK Nuget package](https://www.nuget.org/packages/Microsoft.IoT.Lightning) with source code available on [GitHub ms-iot/Lightning repository](https://github.com/ms-iot/lightning/).</span></span>

<span data-ttu-id="7d27d-115">또한 다른 공급자를 사용 하는 방법을 보여 주는 샘플에서 사용할 수 있는 [ms-iot/BusProviders GitHub 리포지토리](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers)합니다.</span><span class="sxs-lookup"><span data-stu-id="7d27d-115">Additonally, samples showing how to use the different providers are available on [GitHub ms-iot/BusProviders repository](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers).</span></span>

## <a name="adding-the-library-to-your-application"></a><span data-ttu-id="7d27d-116">응용 프로그램에 라이브러리 추가</span><span class="sxs-lookup"><span data-stu-id="7d27d-116">Adding the library to your application</span></span>

### <a name="option-1-starting-from-an-existing-sample"></a><span data-ttu-id="7d27d-117">옵션 1: 기존 샘플에서 시작</span><span class="sxs-lookup"><span data-stu-id="7d27d-117">Option 1: Starting from an existing sample</span></span>
<span data-ttu-id="7d27d-118">번개 공급자를 사용 하 여 코딩을 시작 하는 빠른 방법은의 샘플 중 하나를 사용 하 여 시작 하는 것은 [ms-iot/BusProviders GitHub 리포지토리](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers)합니다.</span><span class="sxs-lookup"><span data-stu-id="7d27d-118">A quick way to start coding using the Lightning providers is to start with one of the samples in the [GitHub ms-iot/BusProviders repository](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers).</span></span>

<span data-ttu-id="7d27d-119">각 샘플 번개 SDK를 참조 및 번개 공급자 라이브러리를 사용 하도록 올바르게 구성 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d27d-119">Each of the samples references the Lightning SDK and is configured properly to use the Lightning providers library.</span></span>

<span data-ttu-id="7d27d-120">**참고**DMAP 드라이버 필요가 Windows 장치 웹 포털을 사용 하는 데 사용할 샘플을 실행 하는 등입니다.</span><span class="sxs-lookup"><span data-stu-id="7d27d-120">**Note**, To run the samples, the DMAP driver need to be enabled using the Windows Devices Web Portal.</span></span> <span data-ttu-id="7d27d-121">참조 된 [번개 설치 가이드](LightningSetup.md) 사용 하도록 설정 하는 방법에 대 한 자세한 내용은 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d27d-121">Refer to the [Lightning Setup Guide](LightningSetup.md) for detailed information on how to enable it.</span></span>

### <a name="option-2-referencing-the-library"></a><span data-ttu-id="7d27d-122">옵션 2: 라이브러리 참조</span><span class="sxs-lookup"><span data-stu-id="7d27d-122">Option 2: Referencing the library</span></span>

<span data-ttu-id="7d27d-123">또한 쉽습니다 필요한 번개 공급자 Nuget 참조를 추가 하 고 새 또는 기존 응용 프로그램을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d27d-123">Additionally, it's straightforward to add the required Lightning providers Nuget reference and support to a new or existing application.</span></span> <span data-ttu-id="7d27d-124">아래의 단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="7d27d-124">Follow the steps below:</span></span>

1. <span data-ttu-id="7d27d-125">응용 프로그램에서 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 "NuGet 패키지 관리..."를 클릭 합니다. 메뉴 항목 ![UWP 프로젝트</span><span class="sxs-lookup"><span data-stu-id="7d27d-125">In your application, right click the project and click the "Manage NuGet Packages..." menu item ![UWP Project</span></span>](../media/LightningProviders/manage-nuget-project.png)

2. <span data-ttu-id="7d27d-126">NuGet 패키지 관리자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="7d27d-126">The NuGet Package Manager will open.</span></span> <span data-ttu-id="7d27d-127">찾아보기 탭에서 "번개 SDK", "시험판 포함" 확인란을 선택 하 여 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d27d-127">In the Browse tab, search for the "Lightning SDK", making sure to check the "Include prerelease" checkbox.</span></span>

3. <span data-ttu-id="7d27d-128">최신 버전을 선택 하 고 매우 SDK 프로젝트를 추가 하려면 [설치]를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d27d-128">Select the latest version, and click "Install" to add the Lightning SDK to your project.</span></span> 
![NuGet 패키지 관리자](../media/LightningProviders/nuget-package-manager.png)

4. <span data-ttu-id="7d27d-130">화면의 지침을 따릅니다 필요한 경우.</span><span class="sxs-lookup"><span data-stu-id="7d27d-130">Follow any on-screen instructions if needed.</span></span> <span data-ttu-id="7d27d-131">설치가 완료 되 면 번개 SDK에 대 한 참조를 프로젝트에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7d27d-131">When installation is complete, a reference to the Lightning SDK will be added to your project.</span></span>

![번개 SDK 참조](../media/LightningProviders/lightning-sdk-added-to-solution.png)

5. <span data-ttu-id="7d27d-133">Package.appxmanifest에 매니페스트 파일에 아래 코드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d27d-133">Add the code below to your manifest file, Package.appxmanifest.</span></span>

``` XML
<iot:Capability Name="lowLevelDevices" />
<DeviceCapability Name="109b86ad-f53d-4b76-aa5f-821e2ddf2141"/>
```

* <span data-ttu-id="7d27d-134">첫 번째는 응용 프로그램을 사용자 지정 장치에 액세스할 수 있게 해 주는 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="7d27d-134">The first is a capability that will enable the application to access custom devices.</span></span>
* <span data-ttu-id="7d27d-135">두 번째는 번개 인터페이스에 대 한 장치 guid id</span><span class="sxs-lookup"><span data-stu-id="7d27d-135">The second is the device guid id for the Lightning interface</span></span>

<span data-ttu-id="7d27d-136">두 기능을 AppX를 추가 해야 아래에 있는 프로젝트의 매니페스트를 `<Capabilities>` 노드.</span><span class="sxs-lookup"><span data-stu-id="7d27d-136">Both capabilities must be added to the AppX manifest of your project under the `<Capabilities>` node.</span></span> <span data-ttu-id="7d27d-137">또한 필요한 경우 프로그램 매니페스트에 필요한 네임 스페이스를 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d27d-137">Also, make sure to add the required namespaces to your manifest if needed.</span></span>

![AppX 매니페스트 Capabailities](../media/LightningProviders/package-manifest-updates.png)

## <a name="updating-your-code-to-use-the-lightning-providers"></a><span data-ttu-id="7d27d-139">번개 공급자를 사용 하도록 코드를 업데이트 하는 중</span><span class="sxs-lookup"><span data-stu-id="7d27d-139">Updating your code to use the Lightning providers</span></span>

### <a name="checking-for-the-lightning-dmap-driver"></a><span data-ttu-id="7d27d-140">번개 (DMAP) 드라이버에 대 한 확인</span><span class="sxs-lookup"><span data-stu-id="7d27d-140">Checking for the Lightning (DMAP) driver</span></span>

<span data-ttu-id="7d27d-141">번개 사용 되는지 여부를 확인 하 여 `LightningProvider.IsLightningEnabled` 속성을 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d27d-141">To check if Lightning is enabled, the `LightningProvider.IsLightningEnabled` property should be used.</span></span> <span data-ttu-id="7d27d-142">일반적으로 것이 항상 번개 공급자 Api를 사용 하기 전에 번개 드라이버를 사용할 수 있는지 확인 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="7d27d-142">In general, it is always a good practice to verify if the Lightning driver is enabled before using the Lightning provider APIs.</span></span> 

``` C#
if (Microsoft.IoT.Lightning.Providers.LightningProvider.IsLightningEnabled)
{
    // Do something with the Lightning providers
}
```

### <a name="general-usage-pattern"></a><span data-ttu-id="7d27d-143">일반적인 사용 패턴</span><span class="sxs-lookup"><span data-stu-id="7d27d-143">General usage pattern</span></span>

<span data-ttu-id="7d27d-144">공급자를 사용 하는 가장 간단한 방법은 앱 내에서 기본적으로 매우 공급자를 설정 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="7d27d-144">The simplest way to use the providers is to set the Lightning Provider as the default inside your app.</span></span> 

<span data-ttu-id="7d27d-145">아래 코드 번개 공급자가 사용 가능한 설정 `Microsoft.IoT.Lightning.Providers.LightningProvider` 기본 공급자로 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d27d-145">The code below will, if the Lightning Provider is available, set `Microsoft.IoT.Lightning.Providers.LightningProvider` as the default provider.</span></span> <span data-ttu-id="7d27d-146">그렇지 않으면 기본 공급자를 명시적으로 설정 하는 경우 다양 한 버스도 대체 됩니다 기본입니다.</span><span class="sxs-lookup"><span data-stu-id="7d27d-146">Otherwise, when no default provider is explicitly set, the various busses will fall back to the default one.</span></span>
``` C#
using Microsoft.IoT.Lightning.Providers;
using Windows.Devices;
if (LightningProvider.IsLightningEnabled)
{
    LowLevelDevicesController.DefaultProvider = LightningProvider.GetAggregateProvider();
}

gpioController = await GpioController.GetDefaultAsync();
i2cController = await I2cController.GetDefaultAsync();
spiController = await SpiController.GetDefaultAsync();
```

<span data-ttu-id="7d27d-147">원하는 버스에 대 한 컨트롤러를 설정한 후 평소와 같이 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d27d-147">After you have a controller for the desired bus, you can use it as you normally would.</span></span> 

### <a name="using-lightning-for-individual-buses"></a><span data-ttu-id="7d27d-148">번개를 사용 하 여 개별 버스에 대 한</span><span class="sxs-lookup"><span data-stu-id="7d27d-148">Using Lightning for individual buses</span></span>

<span data-ttu-id="7d27d-149">다른 기본 공급자를 사용 하려는 경우 다음 섹션에서는 개별 버스에 대 한 매우 공급자를 사용 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7d27d-149">If you want to use a different default provider, the sections below show how you can use the Lightning providers for individual busses.</span></span> 

#### <a name="for-gpio-bus-controller"></a><span data-ttu-id="7d27d-150">GPIO 버스 컨트롤러:</span><span class="sxs-lookup"><span data-stu-id="7d27d-150">For GPIO bus controller:</span></span>

``` C#
using Microsoft.IoT.Lightning.Providers;
using Windows.Devices;
using Windows.Devices.Gpio;

if (LightningProvider.IsLightningEnabled)
{
    GpioController gpioController = (await GpioController.GetControllersAsync(LightningGpioProvider.GetGpioProvider()))[0];
    GpioPin pin = gpioController.OpenPin(LED_PIN, GpioSharingMode.Exclusive);
}
```

#### <a name="for-i2c-bus-controller"></a><span data-ttu-id="7d27d-151">I2C 버스 컨트롤러:</span><span class="sxs-lookup"><span data-stu-id="7d27d-151">For I2C bus controller:</span></span>

``` C#
using Microsoft.IoT.Lightning.Providers;
using Windows.Devices;
using Windows.Devices.I2c;

if (LightningProvider.IsLightningEnabled)
{
    I2cController controller =  (await I2cController.GetControllersAsync(LightningI2cProvider.GetI2cProvider()))[0];
    I2cDevice sensor = controller.GetDevice(new I2cConnectionSettings(0x40));
}
```

#### <a name="for-spi-bus-controller"></a><span data-ttu-id="7d27d-152">SPI 버스 컨트롤러:</span><span class="sxs-lookup"><span data-stu-id="7d27d-152">For SPI bus controller:</span></span>
<span data-ttu-id="7d27d-153">Microsoft.IoT.Lightning.Providers;를 사용 하 여 Windows.Devices;를 사용 하 여 Windows.Devices.Spi;를 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="7d27d-153">using Microsoft.IoT.Lightning.Providers; using Windows.Devices; using Windows.Devices.Spi;</span></span>

``` C#
if (LightningProvider.IsLightningEnabled)
{
    SpiController controller =  (await SpiController.GetControllersAsync(LightningSpiProvider.GetSpiProvider()))[0];
    SpiDevice SpiDisplay = controller.GetDevice(spiConnectionSettings);
}
```

## <a name="lightning-provider-samples"></a><span data-ttu-id="7d27d-154">번개 공급자 샘플</span><span class="sxs-lookup"><span data-stu-id="7d27d-154">Lightning Provider Samples</span></span>

<span data-ttu-id="7d27d-155">다음 샘플 번개 공급자를 사용 하 여 지원 되는 버스 형식을 사용 하 여 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7d27d-155">The following samples demonstrate using the Lightning providers with supported bus types:</span></span>

* <span data-ttu-id="7d27d-156">[쳐다 (UI) 번개 공급자를 사용 하 여](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/Blinky) GPIO 번개 공급자를 사용 하 여 포그라운드 응용 프로그램에서 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7d27d-156">[Blinky (UI) with Lightning Provider](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/Blinky) demonstrates GPIO with Lightning Provider in a foreground application</span></span>

* <span data-ttu-id="7d27d-157">[번개 공급자를 사용 하 여 BlinkyHeadless](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/Blinky/Background) 헤드리스 응용 프로그램에서 매우 공급자를 사용 하 여 GPIO를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7d27d-157">[BlinkyHeadless with Lightning Provider](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/Blinky/Background) demonstrates GPIO with Lightning Provider in a headless application</span></span>

* <span data-ttu-id="7d27d-158">[번개 공급자를 사용 하 여 SPIDisplay](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/SPIDisplay) 번개 공급자를 사용 하 여 SPI를 사용 하는 장치를 제어 하는 API의 사용법을 보여 줍니다</span><span class="sxs-lookup"><span data-stu-id="7d27d-158">[SPIDisplay with Lightning Provider](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/SPIDisplay) demonstrates the usage of the API to control a device using SPI with Lightning Provider</span></span>
 
* <span data-ttu-id="7d27d-159">[번개 공급자를 사용 하 여 WeatherStation](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/WeatherStation) 번개 공급자를 사용 하 여 I2C를 사용 하는 장치를 사용 하 여 상호 작용 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7d27d-159">[WeatherStation with Lightning Provider](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/WeatherStation) demonstrates interacting with a device using I2C with Lightning Provider</span></span>

## <a name="build-requirements"></a><span data-ttu-id="7d27d-160">빌드 요구 사항</span><span class="sxs-lookup"><span data-stu-id="7d27d-160">Build Requirements</span></span>



### <a name="windows-sdk-update"></a><span data-ttu-id="7d27d-161">Windows SDK 업데이트</span><span class="sxs-lookup"><span data-stu-id="7d27d-161">Windows SDK Update</span></span>

<span data-ttu-id="7d27d-162">빌드 및 라이브러리를 사용 하는 데 필요한 Windows SDK는 10.0.10586.0에서 다운로드 가능한 이상 또는 [여기](https://dev.windows.com/en-US/downloads/windows-10-sdk)합니다.</span><span class="sxs-lookup"><span data-stu-id="7d27d-162">Windows SDK required for building and using the library is 10.0.10586.0 or higher which can be downloaded from [here](https://dev.windows.com/en-US/downloads/windows-10-sdk).</span></span>

<span data-ttu-id="7d27d-163">모든 설정에 대 한 자세한 내용은 참조 [이 시작 가이드입니다.](https://developer.microsoft.com/en-us/windows/iot/getstarted)합니다.</span><span class="sxs-lookup"><span data-stu-id="7d27d-163">For more information on setting everything up, refer to [our get started guide.](https://developer.microsoft.com/en-us/windows/iot/getstarted).</span></span>

### <a name="nuget-package-dependencies"></a><span data-ttu-id="7d27d-164">Nuget 패키지 종속성</span><span class="sxs-lookup"><span data-stu-id="7d27d-164">Nuget Package Dependencies</span></span>

<span data-ttu-id="7d27d-165">번개 공급자 라이브러리에 의존 합니다 [Microsoft.IoT.Lightning Nuget 패키지](https://www.nuget.org/packages/Microsoft.IoT.Lightning)에 따라는 [Arduino SDK Nuget 패키지](https://www.nuget.org/packages/Microsoft.IoT.SDKFromArduino)합니다.</span><span class="sxs-lookup"><span data-stu-id="7d27d-165">The Lightning Provider library depends on the [Microsoft.IoT.Lightning Nuget package](https://www.nuget.org/packages/Microsoft.IoT.Lightning), which in turn depends on the [Arduino SDK Nuget package](https://www.nuget.org/packages/Microsoft.IoT.SDKFromArduino).</span></span> <span data-ttu-id="7d27d-166">Nuget 패키지를 모두 라이브러리 프로젝트에서 참조 되 고 Nuget.org에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d27d-166">Both Nuget packages are referenced in the library projects, and are available from Nuget.org.</span></span>

<span data-ttu-id="7d27d-167">필요한 경우 각각에 대 한 소스 코드에서 GitHub에서 사용할 수 있는 이기도 합니다 [번개](https://github.com/ms-iot/lightning) 및 [Arduino SDK](https://github.com/ms-iot/arduino-sdk) 리포지토리.</span><span class="sxs-lookup"><span data-stu-id="7d27d-167">If needed, source code for each is also available on GitHub at the [Lightning](https://github.com/ms-iot/lightning) and [Arduino SDK](https://github.com/ms-iot/arduino-sdk) repositories.</span></span>

<span data-ttu-id="7d27d-168">현재 Microsoft.IoT.Lightning Nuget은 여전히 시험판 버전을 최신 버전을 사용할 수 있는 경우 Nuget.org에서 업데이트할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d27d-168">Currently, Microsoft.IoT.Lightning Nuget is still pre-release, so should be updated from Nuget.org, when newer versions are available.</span></span>

<span data-ttu-id="7d27d-169">번개 패키지에 시험판 업데이트를 수신 뿐만 아니라 (현재) 시험판 버전의 Microsoft.IoT.Lightning Nuget 패키지 설치를 위해 Nuget 패키지 관리자에서 "시험판 포함" 옵션을 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d27d-169">In order to install prerelease (current) version of Microsoft.IoT.Lightning Nuget package as well as receive prerelease updates to the Lightning package, make sure to set the "Include prerelease" option in the Nuget Package Manager.</span></span>

1. <span data-ttu-id="7d27d-170">프로젝트에서 참조 마우스 오른쪽 단추로 클릭</span><span class="sxs-lookup"><span data-stu-id="7d27d-170">Right click References in your project</span></span>
1. <span data-ttu-id="7d27d-171">"Nuget 패키지 관리"를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d27d-171">Click "Manage Nuget Packages..."</span></span>
1. <span data-ttu-id="7d27d-172">번개 nuget 패키지 소스를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d27d-172">Select package sources for Lightning nuget</span></span>
1. <span data-ttu-id="7d27d-173">"시험판 포함"을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d27d-173">Click "Include prerelease".</span></span>
1. <span data-ttu-id="7d27d-174">프로젝트에 nuget 패키지를 설치 하려면 "설치"를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d27d-174">Click "Install" to install the nuget package to your project</span></span>

![패키지 관리자 구성](../media/LightningProviders/Nuget_PackageManager.png)

## <a name="runtime-requirements"></a><span data-ttu-id="7d27d-176">런타임 요구 사항</span><span class="sxs-lookup"><span data-stu-id="7d27d-176">Runtime Requirements</span></span>

### <a name="windows-iot-core-fall-update-required"></a><span data-ttu-id="7d27d-177">Windows IoT Core Fall 업데이트 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d27d-177">Windows IoT Core Fall Update required</span></span>
<span data-ttu-id="7d27d-178">Windows IoT Core에 대 한 지원을 현재 Fall Update에 포함 된 매우 공급자 작성 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d27d-178">Lightning providers support is currently included in the Fall Update builds for Windows IoT Core.</span></span>
<span data-ttu-id="7d27d-179">Windows 10 IoT Core 이미지를 다운로드할 수 있습니다 우리의 [다운로드 페이지](https://developer.microsoft.com/windows/iot/Downloads)합니다.</span><span class="sxs-lookup"><span data-stu-id="7d27d-179">You can download a Windows 10 IoT Core image from our [downloads page](https://developer.microsoft.com/windows/iot/Downloads).</span></span> <span data-ttu-id="7d27d-180">장치 유형에 대 한 "Insider Preview 다운로드"를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d27d-180">Click on "Download Insider Preview" for your device type.</span></span>

### <a name="direct-memory-mapped-driver-must-be-enabled"></a><span data-ttu-id="7d27d-181">메모리 매핑된 직접 드라이버를 사용 하도록 설정</span><span class="sxs-lookup"><span data-stu-id="7d27d-181">Direct Memory Mapped driver must be enabled</span></span>
 
<span data-ttu-id="7d27d-182">번개 공급자 라이브러리의 Api를 사용 하려면 대상 장치에서 사용 하도록 설정 번개 직접 메모리 매핑된 드라이버가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d27d-182">The APIs in the Lightning Provider library require the Lightning Direct Memory Mapped driver to be enabled on the target device.</span></span> <span data-ttu-id="7d27d-183">Raspberry Pi 2/3와 MinnowBoard 최대에 드라이버를 사용할 수 있지만 기본적으로 사용 안 함.</span><span class="sxs-lookup"><span data-stu-id="7d27d-183">Both Raspberry Pi 2/3 and MinnowBoard Max have the driver available, but not enabled by default.</span></span>

<span data-ttu-id="7d27d-184">Windows 장치 웹 포털을 사용 하 여 드라이버를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d27d-184">The driver can be enabled using the Windows Devices Web Portal.</span></span> <span data-ttu-id="7d27d-185">참조 된 [번개 설치 가이드](LightningSetup.md) 번개 드라이버를 사용 하는 방법에 대 한 자세한 내용은 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d27d-185">Refer to the [Lightning Setup Guide](LightningSetup.md) for detailed information on how to enable the Lightning driver.</span></span>

![장치 페이지](../media/LightningProviders/dmap4.png)

<span data-ttu-id="7d27d-187">드라이버는 DmapUtil 명령을 사용 하 여 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d27d-187">The driver can also be enabled with the DmapUtil command:</span></span>

<span data-ttu-id="7d27d-188">DmapUtil: 유틸리티를 켜거나 DMAP 직접 메모리 매퍼 드라이버 사용: dmaputil.exe 상태 |를 사용 하도록 설정 | 상태를 사용 하지 않도록 설정 [-v] dmap 현재 사용 여부를 인쇄 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d27d-188">DmapUtil: Utility to turn the DMAP direct memory mapper driver on or off Usage: dmaputil.exe status|enable|disable status [-v]   Print out whether dmap is currently enabled.</span></span> <span data-ttu-id="7d27d-189">자세한 구성 정보에 대 한-v 플래그를 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d27d-189">Pass the -v flag for detailed configuration information.</span></span>
<span data-ttu-id="7d27d-190">다음 부팅 시 사용 dmap 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d27d-190">enable        Enable dmap on next boot.</span></span>
<span data-ttu-id="7d27d-191">다음 부팅 시 사용 안 함 dmap를 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d27d-191">disable       Disable dmap on next boot.</span></span>
