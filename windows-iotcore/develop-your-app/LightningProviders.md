---
title: Lightning 공급자
author: msalehmsft
ms.author: msaleh
ms.date: 08/28/2017
ms.topic: article
description: 마이크로 Osft 라이트닝 공급자 라이브러리를 사용 하는 방법에 대해 자세히 알아보세요.
keywords: windows iot, 번개 공급자, 라이트닝 성능 테스트, 버스
ms.openlocfilehash: 50cbf4f9940538da1570cebb6cc142e7fbe06588
ms.sourcegitcommit: fcc0c6add468040e2f676893b44b260e3ddc3c52
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/16/2019
ms.locfileid: "65779381"
---
# <a name="working-with-lightning-providers"></a><span data-ttu-id="767e6-104">라이트닝 공급자 작업</span><span class="sxs-lookup"><span data-stu-id="767e6-104">Working with lightning providers</span></span>
<span data-ttu-id="767e6-105">Microsoft. a s a. s a t a r. s a t a r a s 라이브러리에는 amdirect 메모리 매핑된 드라이버 (AMAP)를 통해 보드 컨트롤러 버스와 인터페이스 하는 공급자 집합이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="767e6-105">The Microsoft.IoT.Lightning.Providers library contains a set of providers to interface with the on board controller buses through the Lightning direct memory mapped driver (DMAP).</span></span>


## <a name="about-the-direct-memory-mapped-driver-dmap"></a><span data-ttu-id="767e6-106">직접 메모리 매핑된 드라이버 정보 (6MAP)</span><span class="sxs-lookup"><span data-stu-id="767e6-106">About the direct memory mapped driver (DMAP)</span></span>

<span data-ttu-id="767e6-107">EMAP 드라이버는 기본 수신함 드라이버에 대 한 GPIO 성능 개선을 제공 하는 개발 내 드라이버입니다.</span><span class="sxs-lookup"><span data-stu-id="767e6-107">The DMAP driver is an in-development driver that provides GPIO performance improvements over the default inbox driver.</span></span> <span data-ttu-id="767e6-108">이러한 성능 향상에 대해 자세히 알아보려면 [번개 성능 테스트](../develop-your-app/LightningPerformance.md) 페이지를 방문 하세요.</span><span class="sxs-lookup"><span data-stu-id="767e6-108">To learn more about these performance improvements visit the [Lightning Performance Testing](../develop-your-app/LightningPerformance.md) page.</span></span>

<span data-ttu-id="767e6-109">EMAP 드라이버는 수신함 드라이버를 통해 GPIO 성능 개선을 제공 하지만 컨트롤러 명령은 각 컨트롤러에 대 한 사용자 모드 메모리 매핑된 주소를 통해 AMAP 드라이버에 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="767e6-109">While DMAP driver offer GPIO performance improvements over the Inbox driver, controller commands are sent to the DMAP driver through user-mode memory mapped addresses for each of the controllers.</span></span> <span data-ttu-id="767e6-110">번개 공급자 Api 또는 Microsoft만 사용 하는 앱입니다.</span><span class="sxs-lookup"><span data-stu-id="767e6-110">An app that only uses the Lightning provider APIs or Microsoft.IoT.Lightning.Providers.</span></span> <span data-ttu-id="767e6-111">그러나 악성 앱은 해당 메모리에 직접 기록 하 고 하드웨어/보안 문제를 일으킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="767e6-111">However, a malicious app would be able to write directly to that memory and cause hardware/security issues.</span></span> <span data-ttu-id="767e6-112">신뢰할 수 있는 앱만 있는 컴퓨터에서는 일반적으로이를 사용 하는 것이 안전 합니다.</span><span class="sxs-lookup"><span data-stu-id="767e6-112">On a machine with only trusted apps, the DMAP is generally safe to use.</span></span>   

## <a name="obtaining-the-library"></a><span data-ttu-id="767e6-113">라이브러리 가져오기</span><span class="sxs-lookup"><span data-stu-id="767e6-113">Obtaining the library</span></span>

<span data-ttu-id="767e6-114">라이브러리는 [GitHub ms-iot/라이트닝 리포지토리에서](https://github.com/ms-iot/lightning/)사용할 수 있는 소스 코드를 사용 하 여 [번개 SDK Nuget 패키지](https://www.nuget.org/packages/Microsoft.IoT.Lightning) 의 일부로 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="767e6-114">The library is provided as part of the [Lightning SDK Nuget package](https://www.nuget.org/packages/Microsoft.IoT.Lightning) with source code available on [GitHub ms-iot/Lightning repository](https://github.com/ms-iot/lightning/).</span></span>

<span data-ttu-id="767e6-115">또한 다양 한 공급자를 사용 하는 방법을 보여 주는 샘플은 [GitHub ms-iot/BusProviders 리포지토리에서](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers)사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="767e6-115">Additonally, samples showing how to use the different providers are available on [GitHub ms-iot/BusProviders repository](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers).</span></span>

## <a name="adding-the-library-to-your-application"></a><span data-ttu-id="767e6-116">응용 프로그램에 라이브러리 추가</span><span class="sxs-lookup"><span data-stu-id="767e6-116">Adding the library to your application</span></span>

### <a name="option-1-starting-from-an-existing-sample"></a><span data-ttu-id="767e6-117">옵션 1: 기존 샘플에서 시작</span><span class="sxs-lookup"><span data-stu-id="767e6-117">Option 1: Starting from an existing sample</span></span>
<span data-ttu-id="767e6-118">라이트닝 공급자를 사용 하 여 코딩을 시작 하는 빠른 방법은 [GitHub ms-iot/BusProviders 리포지토리의](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers)샘플 중 하나를 사용 하 여 시작 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="767e6-118">A quick way to start coding using the Lightning providers is to start with one of the samples in the [GitHub ms-iot/BusProviders repository](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers).</span></span>

<span data-ttu-id="767e6-119">각 샘플은 번개 SDK를 참조 하며 번개 공급자 라이브러리를 사용 하도록 올바르게 구성 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="767e6-119">Each of the samples references the Lightning SDK and is configured properly to use the Lightning providers library.</span></span>

<span data-ttu-id="767e6-120">샘플을 실행 하려면 Windows 장치 웹 포털을 사용 하 여 emap 드라이버를 사용 하도록 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="767e6-120">**Note**, To run the samples, the DMAP driver need to be enabled using the Windows Devices Web Portal.</span></span> <span data-ttu-id="767e6-121">사용 하도록 설정 하는 방법에 대 한 자세한 내용은 [번개 설정 가이드](LightningSetup.md) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="767e6-121">Refer to the [Lightning Setup Guide](LightningSetup.md) for detailed information on how to enable it.</span></span>

### <a name="option-2-referencing-the-library"></a><span data-ttu-id="767e6-122">옵션 2: 라이브러리 참조</span><span class="sxs-lookup"><span data-stu-id="767e6-122">Option 2: Referencing the library</span></span>

<span data-ttu-id="767e6-123">또한 새 응용 프로그램 또는 기존 응용 프로그램에 필요한 번개 공급자 Nuget 참조 및 지원을 추가 하는 것이 간단 합니다.</span><span class="sxs-lookup"><span data-stu-id="767e6-123">Additionally, it's straightforward to add the required Lightning providers Nuget reference and support to a new or existing application.</span></span> <span data-ttu-id="767e6-124">아래의 단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="767e6-124">Follow the steps below:</span></span>

1. <span data-ttu-id="767e6-125">응용 프로그램에서 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 "NuGet 패키지 관리 ..."를 클릭 합니다. 메뉴 항목</span><span class="sxs-lookup"><span data-stu-id="767e6-125">In your application, right click the project and click the "Manage NuGet Packages..." menu item</span></span>  
![UWP 프로젝트](../media/LightningProviders/manage-nuget-project.png)

2. <span data-ttu-id="767e6-127">NuGet 패키지 관리자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="767e6-127">The NuGet Package Manager will open.</span></span> <span data-ttu-id="767e6-128">찾아보기 탭에서 "낙뢰 SDK"를 검색 하 고 "시험판 포함" 확인란을 선택 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="767e6-128">In the Browse tab, search for the "Lightning SDK", making sure to check the "Include prerelease" checkbox.</span></span>

3. <span data-ttu-id="767e6-129">최신 버전을 선택 하 고 "설치"를 클릭 하 여 프로젝트에 번개 SDK를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="767e6-129">Select the latest version, and click "Install" to add the Lightning SDK to your project.</span></span> 
<span data-ttu-id="767e6-130">![NuGet 패키지 관리자](../media/LightningProviders/nuget-package-manager.png)</span><span class="sxs-lookup"><span data-stu-id="767e6-130">![NuGet Package Manager](../media/LightningProviders/nuget-package-manager.png)</span></span>

4. <span data-ttu-id="767e6-131">필요한 경우 화면의 지시를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="767e6-131">Follow any on-screen instructions if needed.</span></span> <span data-ttu-id="767e6-132">설치가 완료 되 면 번개 SDK에 대 한 참조가 프로젝트에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="767e6-132">When installation is complete, a reference to the Lightning SDK will be added to your project.</span></span>

![번개 SDK 참조](../media/LightningProviders/lightning-sdk-added-to-solution.png)

5. <span data-ttu-id="767e6-134">매니페스트 파일 appxmanifest.xml에 아래 코드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="767e6-134">Add the code below to your manifest file, Package.appxmanifest.</span></span>

``` XML
<iot:Capability Name="lowLevelDevices" />
<DeviceCapability Name="109b86ad-f53d-4b76-aa5f-821e2ddf2141"/>
```

* <span data-ttu-id="767e6-135">첫 번째는 응용 프로그램이 사용자 지정 장치에 액세스할 수 있게 해 주는 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="767e6-135">The first is a capability that will enable the application to access custom devices.</span></span>
* <span data-ttu-id="767e6-136">두 번째는 번개 인터페이스의 장치 guid id입니다.</span><span class="sxs-lookup"><span data-stu-id="767e6-136">The second is the device guid id for the Lightning interface</span></span>

<span data-ttu-id="767e6-137">두 기능 모두 `<Capabilities>` 노드 아래 프로젝트의 AppX 매니페스트에 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="767e6-137">Both capabilities must be added to the AppX manifest of your project under the `<Capabilities>` node.</span></span> <span data-ttu-id="767e6-138">또한 필요한 경우 매니페스트에 필요한 네임 스페이스를 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="767e6-138">Also, make sure to add the required namespaces to your manifest if needed.</span></span>

![AppX 매니페스트 Capabailities](../media/LightningProviders/package-manifest-updates.png)

## <a name="updating-your-code-to-use-the-lightning-providers"></a><span data-ttu-id="767e6-140">라이트닝 공급자를 사용 하도록 코드 업데이트</span><span class="sxs-lookup"><span data-stu-id="767e6-140">Updating your code to use the Lightning providers</span></span>

### <a name="checking-for-the-lightning-dmap-driver"></a><span data-ttu-id="767e6-141">번개 (6MAP) 드라이버를 확인 하는 중</span><span class="sxs-lookup"><span data-stu-id="767e6-141">Checking for the Lightning (DMAP) driver</span></span>

<span data-ttu-id="767e6-142">번개를 사용할 `LightningProvider.IsLightningEnabled` 수 있는지 확인 하려면 속성을 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="767e6-142">To check if Lightning is enabled, the `LightningProvider.IsLightningEnabled` property should be used.</span></span> <span data-ttu-id="767e6-143">일반적으로 라이트닝 공급자 Api를 사용 하기 전에 번개 드라이버가 사용 되는지 확인 하는 것이 항상 좋은 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="767e6-143">In general, it is always a good practice to verify if the Lightning driver is enabled before using the Lightning provider APIs.</span></span> 

``` C#
if (Microsoft.IoT.Lightning.Providers.LightningProvider.IsLightningEnabled)
{
    // Do something with the Lightning providers
}
```

### <a name="general-usage-pattern"></a><span data-ttu-id="767e6-144">일반 사용 패턴</span><span class="sxs-lookup"><span data-stu-id="767e6-144">General usage pattern</span></span>

<span data-ttu-id="767e6-145">공급자를 사용 하는 가장 간단한 방법은 번개 공급자를 앱 내부에서 기본값으로 설정 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="767e6-145">The simplest way to use the providers is to set the Lightning Provider as the default inside your app.</span></span> 

<span data-ttu-id="767e6-146">아래 코드는 번개 공급자를 사용할 수 있는 경우를 기본 공급자로 `Microsoft.IoT.Lightning.Providers.LightningProvider` 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="767e6-146">The code below will, if the Lightning Provider is available, set `Microsoft.IoT.Lightning.Providers.LightningProvider` as the default provider.</span></span> <span data-ttu-id="767e6-147">그렇지 않으면 기본 공급자가 명시적으로 설정 되지 않은 경우에는 다양 한 버스 기본 공급자로 대체 됩니다.</span><span class="sxs-lookup"><span data-stu-id="767e6-147">Otherwise, when no default provider is explicitly set, the various busses will fall back to the default one.</span></span>
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

<span data-ttu-id="767e6-148">원하는 버스에 대 한 컨트롤러를 만든 후에는 평소와 같이 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="767e6-148">After you have a controller for the desired bus, you can use it as you normally would.</span></span> 

### <a name="using-lightning-for-individual-buses"></a><span data-ttu-id="767e6-149">개별 버스에 번개 사용</span><span class="sxs-lookup"><span data-stu-id="767e6-149">Using Lightning for individual buses</span></span>

<span data-ttu-id="767e6-150">다른 기본 공급자를 사용 하려는 경우 아래 섹션에서 개별 버스에 대 한 번개 공급자를 사용 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="767e6-150">If you want to use a different default provider, the sections below show how you can use the Lightning providers for individual busses.</span></span> 

#### <a name="for-gpio-bus-controller"></a><span data-ttu-id="767e6-151">GPIO 버스 컨트롤러의 경우:</span><span class="sxs-lookup"><span data-stu-id="767e6-151">For GPIO bus controller:</span></span>

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

#### <a name="for-i2c-bus-controller"></a><span data-ttu-id="767e6-152">I2C bus 컨트롤러의 경우:</span><span class="sxs-lookup"><span data-stu-id="767e6-152">For I2C bus controller:</span></span>

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

#### <a name="for-spi-bus-controller"></a><span data-ttu-id="767e6-153">SPI bus 컨트롤러의 경우:</span><span class="sxs-lookup"><span data-stu-id="767e6-153">For SPI bus controller:</span></span>
<span data-ttu-id="767e6-154">사용 하 여 Windows. 장치 사용 Windows. Devices 사용</span><span class="sxs-lookup"><span data-stu-id="767e6-154">using Microsoft.IoT.Lightning.Providers; using Windows.Devices; using Windows.Devices.Spi;</span></span>

``` C#
if (LightningProvider.IsLightningEnabled)
{
    SpiController controller =  (await SpiController.GetControllersAsync(LightningSpiProvider.GetSpiProvider()))[0];
    SpiDevice SpiDisplay = controller.GetDevice(spiConnectionSettings);
}
```

## <a name="lightning-provider-samples"></a><span data-ttu-id="767e6-155">라이트닝 공급자 샘플</span><span class="sxs-lookup"><span data-stu-id="767e6-155">Lightning Provider Samples</span></span>

<span data-ttu-id="767e6-156">다음 샘플에서는 지원 되는 버스 형식으로 라이트닝 공급자를 사용 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="767e6-156">The following samples demonstrate using the Lightning providers with supported bus types:</span></span>

* <span data-ttu-id="767e6-157">[라이트닝 공급자를 사용 하는 Blinky (UI)](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/Blinky) 는 포그라운드 응용 프로그램에서 번개 공급자와의 GPIO를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="767e6-157">[Blinky (UI) with Lightning Provider](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/Blinky) demonstrates GPIO with Lightning Provider in a foreground application</span></span>

* <span data-ttu-id="767e6-158">[Blinkyheadless와 라이트닝 공급자](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/Blinky/Background) 는 헤드리스 응용 프로그램에서 번개 공급자와의 GPIO를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="767e6-158">[BlinkyHeadless with Lightning Provider](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/Blinky/Background) demonstrates GPIO with Lightning Provider in a headless application</span></span>

* <span data-ttu-id="767e6-159">[SPIDisplay를](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/SPIDisplay) 사용 하는 경우 API를 사용 하 여 번개 공급자와 SPI를 사용 하 여 장치를 제어 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="767e6-159">[SPIDisplay with Lightning Provider](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/SPIDisplay) demonstrates the usage of the API to control a device using SPI with Lightning Provider</span></span>
 
* <span data-ttu-id="767e6-160">[WeatherStation를](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/WeatherStation) 사용 하는 번개 공급자를 사용 하 여 장치와 상호 작용 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="767e6-160">[WeatherStation with Lightning Provider](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/WeatherStation) demonstrates interacting with a device using I2C with Lightning Provider</span></span>

## <a name="build-requirements"></a><span data-ttu-id="767e6-161">빌드 요구 사항</span><span class="sxs-lookup"><span data-stu-id="767e6-161">Build Requirements</span></span>



### <a name="windows-sdk-update"></a><span data-ttu-id="767e6-162">Windows SDK 업데이트</span><span class="sxs-lookup"><span data-stu-id="767e6-162">Windows SDK Update</span></span>

<span data-ttu-id="767e6-163">라이브러리를 작성 하 고 사용 하는 데 필요한 Windows SDK는 [여기](https://dev.windows.com/en-US/downloads/windows-10-sdk)에서 다운로드할 수 있는 10.0.10586.0 이상입니다.</span><span class="sxs-lookup"><span data-stu-id="767e6-163">Windows SDK required for building and using the library is 10.0.10586.0 or higher which can be downloaded from [here](https://dev.windows.com/en-US/downloads/windows-10-sdk).</span></span>

<span data-ttu-id="767e6-164">모든 항목을 설정 하는 방법에 대 한 자세한 내용은 [시작 가이드](https://developer.microsoft.com/en-us/windows/iot/getstarted)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="767e6-164">For more information on setting everything up, refer to [our get started guide.](https://developer.microsoft.com/en-us/windows/iot/getstarted).</span></span>

### <a name="nuget-package-dependencies"></a><span data-ttu-id="767e6-165">Nuget 패키지 종속성</span><span class="sxs-lookup"><span data-stu-id="767e6-165">Nuget Package Dependencies</span></span>

<span data-ttu-id="767e6-166">라이트닝 공급자 라이브러리는 [ARDUINO SDK nuget 패키지](https://www.nuget.org/packages/Microsoft.IoT.SDKFromArduino)에 따라 달라 지는 Microsoft의 라이트닝 [nuget 패키지](https://www.nuget.org/packages/Microsoft.IoT.Lightning)를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="767e6-166">The Lightning Provider library depends on the [Microsoft.IoT.Lightning Nuget package](https://www.nuget.org/packages/Microsoft.IoT.Lightning), which in turn depends on the [Arduino SDK Nuget package](https://www.nuget.org/packages/Microsoft.IoT.SDKFromArduino).</span></span> <span data-ttu-id="767e6-167">두 Nuget 패키지는 모두 라이브러리 프로젝트에서 참조 되며 Nuget.org에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="767e6-167">Both Nuget packages are referenced in the library projects, and are available from Nuget.org.</span></span>

<span data-ttu-id="767e6-168">필요한 경우 각각에 대 한 소스 코드를 GitHub에서 [번개](https://github.com/ms-iot/lightning) 및 [Arduino SDK](https://github.com/ms-iot/arduino-sdk) 리포지토리에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="767e6-168">If needed, source code for each is also available on GitHub at the [Lightning](https://github.com/ms-iot/lightning) and [Arduino SDK](https://github.com/ms-iot/arduino-sdk) repositories.</span></span>

<span data-ttu-id="767e6-169">현재 Microsoft. Nuget.org Nuget은 여전히 시험판 이므로 최신 버전을 사용할 수 있는 경우에는에서 업데이트 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="767e6-169">Currently, Microsoft.IoT.Lightning Nuget is still pre-release, so should be updated from Nuget.org, when newer versions are available.</span></span>

<span data-ttu-id="767e6-170">시험판 (현재) 버전의 Microsoft IoT를 설치 하 고 번개 패키지에 대 한 시험판 업데이트를 받으려면 Nuget 패키지 관리자에서 "시험판 포함" 옵션을 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="767e6-170">In order to install prerelease (current) version of Microsoft.IoT.Lightning Nuget package as well as receive prerelease updates to the Lightning package, make sure to set the "Include prerelease" option in the Nuget Package Manager.</span></span>

1. <span data-ttu-id="767e6-171">프로젝트에서 참조를 마우스 오른쪽 단추로 클릭</span><span class="sxs-lookup"><span data-stu-id="767e6-171">Right click References in your project</span></span>
1. <span data-ttu-id="767e6-172">"Nuget 패키지 관리 ..."를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="767e6-172">Click "Manage Nuget Packages..."</span></span>
1. <span data-ttu-id="767e6-173">라이트닝 nuget의 패키지 소스 선택</span><span class="sxs-lookup"><span data-stu-id="767e6-173">Select package sources for Lightning nuget</span></span>
1. <span data-ttu-id="767e6-174">"시험판 포함"을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="767e6-174">Click "Include prerelease".</span></span>
1. <span data-ttu-id="767e6-175">프로젝트에 nuget 패키지를 설치 하려면 "설치"를 클릭 하십시오.</span><span class="sxs-lookup"><span data-stu-id="767e6-175">Click "Install" to install the nuget package to your project</span></span>

![패키지 관리자 구성](../media/LightningProviders/Nuget_PackageManager.png)

## <a name="runtime-requirements"></a><span data-ttu-id="767e6-177">런타임 요구 사항</span><span class="sxs-lookup"><span data-stu-id="767e6-177">Runtime Requirements</span></span>

### <a name="windows-iot-core-fall-update-required"></a><span data-ttu-id="767e6-178">Windows IoT Core를 업데이트 해야 함</span><span class="sxs-lookup"><span data-stu-id="767e6-178">Windows IoT Core Fall Update required</span></span>
<span data-ttu-id="767e6-179">라이트닝 공급자 지원은 현재 Windows IoT Core에 대 한 현재 범위 업데이트 빌드에 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="767e6-179">Lightning providers support is currently included in the Fall Update builds for Windows IoT Core.</span></span>
<span data-ttu-id="767e6-180">[다운로드 페이지](https://developer.microsoft.com/windows/iot/Downloads)에서 Windows 10 IoT Core 이미지를 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="767e6-180">You can download a Windows 10 IoT Core image from our [downloads page](https://developer.microsoft.com/windows/iot/Downloads).</span></span> <span data-ttu-id="767e6-181">장치 유형에 대 한 "Insider Preview 다운로드"를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="767e6-181">Click on "Download Insider Preview" for your device type.</span></span>

### <a name="direct-memory-mapped-driver-must-be-enabled"></a><span data-ttu-id="767e6-182">직접 메모리 매핑된 드라이버를 사용 하도록 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="767e6-182">Direct Memory Mapped driver must be enabled</span></span>
 
<span data-ttu-id="767e6-183">라이트닝 공급자 라이브러리의 Api를 사용 하려면 대상 장치에서 번개 직접 메모리 매핑된 드라이버를 사용 하도록 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="767e6-183">The APIs in the Lightning Provider library require the Lightning Direct Memory Mapped driver to be enabled on the target device.</span></span> <span data-ttu-id="767e6-184">Raspberry Pi 2/3 및 MinnowBoard Max는 모두 드라이버를 사용할 수 있지만 기본적으로 사용 하도록 설정 되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="767e6-184">Both Raspberry Pi 2/3 and MinnowBoard Max have the driver available, but not enabled by default.</span></span>

<span data-ttu-id="767e6-185">Windows 장치 웹 포털을 사용 하 여 드라이버를 사용 하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="767e6-185">The driver can be enabled using the Windows Devices Web Portal.</span></span> <span data-ttu-id="767e6-186">라이트닝 드라이버를 사용 하도록 설정 하는 방법에 대 한 자세한 내용은 [번개 설정 가이드](LightningSetup.md) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="767e6-186">Refer to the [Lightning Setup Guide](LightningSetup.md) for detailed information on how to enable the Lightning driver.</span></span>

![장치 페이지](../media/LightningProviders/dmap4.png)

<span data-ttu-id="767e6-188">이 드라이버는 다음과 같은 경우에도 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="767e6-188">The driver can also be enabled with the DmapUtil command:</span></span>

<span data-ttu-id="767e6-189">DmapUtil: 다음을 사용 하 여 VMAP 직접 메모리 매퍼 드라이버를 설정 하거나 해제 하는 유틸리티:. d a d p. .exe 상태 | 사용 | 사용 안 함 상태 [-v] vmap이 현재 활성화 되어 있는지 여부를 출력 합니다.</span><span class="sxs-lookup"><span data-stu-id="767e6-189">DmapUtil: Utility to turn the DMAP direct memory mapper driver on or off Usage: dmaputil.exe status|enable|disable status [-v]   Print out whether dmap is currently enabled.</span></span> <span data-ttu-id="767e6-190">자세한 구성 정보는-v 플래그를 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="767e6-190">Pass the -v flag for detailed configuration information.</span></span>
<span data-ttu-id="767e6-191">다음 부팅 시에는 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="767e6-191">enable        Enable dmap on next boot.</span></span>
<span data-ttu-id="767e6-192">다음 부팅 시에는 사용 안 함을 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="767e6-192">disable       Disable dmap on next boot.</span></span>
