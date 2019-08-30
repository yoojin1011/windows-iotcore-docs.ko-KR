---
title: IoT Core의 Miracast
author: saraclay
ms.author: saclayt
ms.date: 11/30/2017
ms.topic: article
description: 장치에 Miracast 기능을 포함 하는 방법을 알아봅니다.
keywords: windows iot, miracast, 연결
ms.openlocfilehash: c58def4b218d35c78532f54df4a74fb572c8549e
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "60168110"
---
# <a name="miracast-on-iot-core"></a><span data-ttu-id="7df8e-104">IoT Core의 Miracast</span><span class="sxs-lookup"><span data-stu-id="7df8e-104">Miracast on IoT Core</span></span>

<span data-ttu-id="7df8e-105">이 문서에서는 IoT Core 장치에 Miracast 기능을 포함 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7df8e-105">This document will show you how to include Miracast functionality on your IoT Core device.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7df8e-106">이 기능은 Insider Build 17093 이상 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7df8e-106">This feature is only available on Insider Build 17093 and above</span></span>

## <a name="miracast-overview"></a><span data-ttu-id="7df8e-107">Miracast 개요</span><span class="sxs-lookup"><span data-stu-id="7df8e-107">Miracast Overview</span></span>

<span data-ttu-id="7df8e-108">Miracast 연결은 두 가지 구성 요소인 원본 및 싱크로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7df8e-108">A Miracast connection is made up of two components: the Source and the Sink.</span></span> <span data-ttu-id="7df8e-109">**Miracast 소스** 는 콘텐츠를 표시 하는 **miracast 싱크로**콘텐츠를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="7df8e-109">The **Miracast Source** sends content to the **Miracast Sink**, which displays the content.</span></span> <span data-ttu-id="7df8e-110">연결을 만들기 위해 싱크는 연결 된 Wi-fi 네트워크에 자신을 알립니다.</span><span class="sxs-lookup"><span data-stu-id="7df8e-110">To create the connection, the Sink advertises itself to the connected Wi-Fi network.</span></span> <span data-ttu-id="7df8e-111">소스는 **장치 선택기** 를 사용 하 여 싱크를 선택 하 고 연결을 요청 합니다.</span><span class="sxs-lookup"><span data-stu-id="7df8e-111">The Source uses the **Device Picker** to select the Sink and request a connection.</span></span> <span data-ttu-id="7df8e-112">연결이 요청 되 면 싱크의 사용자는 원본에서 연결을 시도 하 고 있는지 확인 하 고 연결이 발생 해야 하는지 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7df8e-112">Once the connection is requested, a user at the Sink receives an alert that the source is attempting to make a connection and must verify that the connection should take place.</span></span> <span data-ttu-id="7df8e-113">이 문제가 발생 하면 소스가 연결을 취소 하거나 싱크가 광고를 중지할 때까지 소스는 싱크로 캐스트를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="7df8e-113">Once this happens, the Source begins casting to the Sink until either the Source cancels the connection or the Sink stops advertising.</span></span>

## <a name="hardware-requirements"></a><span data-ttu-id="7df8e-114">하드웨어 요구 사항</span><span class="sxs-lookup"><span data-stu-id="7df8e-114">Hardware requirements</span></span>

<span data-ttu-id="7df8e-115">원본 및 싱크 장치는 모두 제대로 작동 하려면 Miracast 호환 Wi-fi 및 그래픽 드라이버와 칩셋이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="7df8e-115">Both Source and Sink devices require Miracast-compatible Wi-Fi and Graphics drivers and chipsets to function properly.</span></span> <span data-ttu-id="7df8e-116">장치에 Miracast 호환 하드웨어가 있는지 확인 하려면 다음을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="7df8e-116">To find out if your device has Miracast-compatible hardware, run:</span></span> 
```
netsh wlan show driver
```
<span data-ttu-id="7df8e-117">장치 명령 프롬프트에서.</span><span class="sxs-lookup"><span data-stu-id="7df8e-117">in the device's command prompt.</span></span>

<span data-ttu-id="7df8e-118">장치에서 Miracast를 지 원하는 경우 아래 출력이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7df8e-118">If the device supports Miracast, you should see the output below:</span></span>

![호환 되는 장치 출력](../media/Miracast/CompatibleDevice.png)

<span data-ttu-id="7df8e-120">아래 표에는 IoT Core 참조 플랫폼에 대 한 Miracast 호환성이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7df8e-120">The below table shows Miracast compatibility for the IoT Core reference platforms:</span></span>

| <span data-ttu-id="7df8e-121">팀</span><span class="sxs-lookup"><span data-stu-id="7df8e-121">Board</span></span> | <span data-ttu-id="7df8e-122">SoC</span><span class="sxs-lookup"><span data-stu-id="7df8e-122">SoC</span></span> | <span data-ttu-id="7df8e-123">WiFi 드라이버가 있음</span><span class="sxs-lookup"><span data-stu-id="7df8e-123">WiFi Drivers Present</span></span> | <span data-ttu-id="7df8e-124">그래픽 드라이버 있음</span><span class="sxs-lookup"><span data-stu-id="7df8e-124">Graphics Drivers Present</span></span> | <span data-ttu-id="7df8e-125">Miracast 호환</span><span class="sxs-lookup"><span data-stu-id="7df8e-125">Miracast-Compatible</span></span> |
|-------|-----|----------------------|--------------------------|---------------------|
| <span data-ttu-id="7df8e-126">Qualcomm Dragonboard 410c</span><span class="sxs-lookup"><span data-stu-id="7df8e-126">Qualcomm Dragonboard 410c</span></span> | <span data-ttu-id="7df8e-127">Snapdragon 410</span><span class="sxs-lookup"><span data-stu-id="7df8e-127">Snapdragon 410</span></span> | <span data-ttu-id="7df8e-128">예</span><span class="sxs-lookup"><span data-stu-id="7df8e-128">Yes</span></span> | <span data-ttu-id="7df8e-129">예</span><span class="sxs-lookup"><span data-stu-id="7df8e-129">Yes</span></span> | <span data-ttu-id="7df8e-130">예</span><span class="sxs-lookup"><span data-stu-id="7df8e-130">Yes</span></span> |
| <span data-ttu-id="7df8e-131">Raspberry Pi 2/3</span><span class="sxs-lookup"><span data-stu-id="7df8e-131">Raspberry Pi 2/3</span></span> | <span data-ttu-id="7df8e-132">Broadcom BCM283x</span><span class="sxs-lookup"><span data-stu-id="7df8e-132">Broadcom BCM283x</span></span> | <span data-ttu-id="7df8e-133">예</span><span class="sxs-lookup"><span data-stu-id="7df8e-133">Yes</span></span> | <span data-ttu-id="7df8e-134">아니오</span><span class="sxs-lookup"><span data-stu-id="7df8e-134">No</span></span> | <span data-ttu-id="7df8e-135">아니요</span><span class="sxs-lookup"><span data-stu-id="7df8e-135">No</span></span> |
| <span data-ttu-id="7df8e-136">Minnowboard Max</span><span class="sxs-lookup"><span data-stu-id="7df8e-136">Minnowboard Max</span></span> | <span data-ttu-id="7df8e-137">Intel Atom E3825</span><span class="sxs-lookup"><span data-stu-id="7df8e-137">Intel Atom E3825</span></span> | <span data-ttu-id="7df8e-138">예</span><span class="sxs-lookup"><span data-stu-id="7df8e-138">Yes</span></span> | <span data-ttu-id="7df8e-139">아니오</span><span class="sxs-lookup"><span data-stu-id="7df8e-139">No</span></span> | <span data-ttu-id="7df8e-140">아니요</span><span class="sxs-lookup"><span data-stu-id="7df8e-140">No</span></span> |
| <span data-ttu-id="7df8e-141">위쪽 제곱</span><span class="sxs-lookup"><span data-stu-id="7df8e-141">UP Squared</span></span> | <span data-ttu-id="7df8e-142">Intel 셀러론 N3350</span><span class="sxs-lookup"><span data-stu-id="7df8e-142">Intel Celeron N3350</span></span> | <span data-ttu-id="7df8e-143">예</span><span class="sxs-lookup"><span data-stu-id="7df8e-143">Yes</span></span> | <span data-ttu-id="7df8e-144">예</span><span class="sxs-lookup"><span data-stu-id="7df8e-144">Yes</span></span> | <span data-ttu-id="7df8e-145">예</span><span class="sxs-lookup"><span data-stu-id="7df8e-145">Yes</span></span> |


### <a name="wi-fi"></a><span data-ttu-id="7df8e-146">Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="7df8e-146">Wi-Fi</span></span>

<span data-ttu-id="7df8e-147">장치에 대 한 Wi-fi 드라이버와 칩셋은 Miracast를 지원 하기 위해 다른 기능 중에서 Wi-fi Direct를 지원 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7df8e-147">The Wi-Fi driver and chipset for the device must support Wi-Fi Direct, among other capabilities, to support Miracast.</span></span> <span data-ttu-id="7df8e-148">장치에 이러한 기능이 없는 경우에는 대신 USB Wi-fi 동글을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7df8e-148">If your device does not have these features, you can use a USB Wi-Fi dongle instead.</span></span> <span data-ttu-id="7df8e-149">[300M 무선 USB 어댑터](http://a.co/fdhEhV9)를 권장 합니다.</span><span class="sxs-lookup"><span data-stu-id="7df8e-149">We recommend the [300M Wireless USB Adapter](http://a.co/fdhEhV9).</span></span>

### <a name="graphics"></a><span data-ttu-id="7df8e-150">그래픽</span><span class="sxs-lookup"><span data-stu-id="7df8e-150">Graphics</span></span>

<span data-ttu-id="7df8e-151">그래픽 드라이버와 칩셋은 Miracast 인코딩 및 디코딩을 지원 해야 Miracast를 지원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7df8e-151">The Graphics driver and chipset must support h.264 encoding and decoding to support Miracast.</span></span> <span data-ttu-id="7df8e-152">장치에 호환 되는 그래픽 드라이버 및/또는 칩셋이 없는 경우 새 장치를 선택 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7df8e-152">If your device does not have a compatible graphics driver and/or chipset, you will have to pick a new device.</span></span> <span data-ttu-id="7df8e-153">Miracast 호환 장치를 선택 하는 경우 위의 매트릭스를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7df8e-153">Please consult the above matrix when choosing a Miracast-compatible device.</span></span>

## <a name="windows-iot-as-a-miracast-sink"></a><span data-ttu-id="7df8e-154">Windows IoT를 Miracast 싱크로</span><span class="sxs-lookup"><span data-stu-id="7df8e-154">Windows IoT as a Miracast Sink</span></span>

<span data-ttu-id="7df8e-155">장치를 Miracast 싱크로 사용 하도록 설정 하려면 장치에서 연결 앱을 사용 하도록 설정한 다음 레지스트리에서 Miracast를 사용 하도록 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7df8e-155">To enable your device as a Miracast sink, you will need to enable the Connect app on your device, then enable Miracast in the registry.</span></span>

### <a name="enable-the-connect-app"></a><span data-ttu-id="7df8e-156">연결 앱 사용</span><span class="sxs-lookup"><span data-stu-id="7df8e-156">Enable the Connect App</span></span>

<span data-ttu-id="7df8e-157">Connect 앱을 사용 하도록 설정 하려면 이미지에 **IOT_MIRACAST_RX_APP** 기능을 포함 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7df8e-157">To enable the Connect app, you'll need to include the **IOT_MIRACAST_RX_APP** feature to your image.</span></span> <span data-ttu-id="7df8e-158">또한 이미지에 **Microsoft-Connect-Package** 및 **Microsoft-Connect-Package_Lang_XXXX** 를 포함 해야 합니다. 여기서 XXXX는 언어 (예: "enus")입니다.</span><span class="sxs-lookup"><span data-stu-id="7df8e-158">You'll also need to include  **Microsoft-Connect-Package.cab** and **Microsoft-Connect-Package_Lang_XXXX.cab** in your image (where XXXX is a language, i.e. "enUS").</span></span> 

<span data-ttu-id="7df8e-159">이미지에 기능과 패키지를 추가 하는 방법에 대 한 자세한 내용은 [이 페이지](https://docs.microsoft.com/windows-hardware/manufacture/iot/deploy-your-app-with-a-standard-board#update-the-feature-manifest) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7df8e-159">See [this page](https://docs.microsoft.com/windows-hardware/manufacture/iot/deploy-your-app-with-a-standard-board#update-the-feature-manifest) for more details about how to add features and packages to your image.</span></span> <span data-ttu-id="7df8e-160">다음 [지침](https://docs.microsoft.com/windows/iot-core/build-your-image/createinstallpackage)에 따라 패키지 및 기능을 기존 이미지에 테스트용으로 로드할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7df8e-160">You can also side-load the package and features to existing images by following [these instructions](https://docs.microsoft.com/windows/iot-core/build-your-image/createinstallpackage).</span></span> <span data-ttu-id="7df8e-161">이 기능을 함께 로드 하면 업데이트가 수신 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7df8e-161">Keep in mind that side-loading this feature will prevent it from receiving updates.</span></span>


### <a name="enable-miracast"></a><span data-ttu-id="7df8e-162">Miracast 사용</span><span class="sxs-lookup"><span data-stu-id="7df8e-162">Enable Miracast</span></span>

<span data-ttu-id="7df8e-163">[PowerShell](https://docs.microsoft.com/windows/iot-core/connect-your-device/powershell) 또는 [Windows 장치 포털](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal) 을 통해 장치에 연결 하 고 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="7df8e-163">Connect to your device through [PowerShell](https://docs.microsoft.com/windows/iot-core/connect-your-device/powershell) or the [Windows Device Portal](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal) and run the following commands:</span></span>
```
reg add HKLM\Software\Microsoft\PlayToReceiver /v AutoEnabled /t REG_DWORD /d 1  
reg add HKLM\Software\Microsoft\MiracastReceiver /v  ConsentToast /t REG_DWORD /d 0  
reg add HKLM\Software\Microsoft\MiracastReceiver /v NetworkQualificationEnabled /t REG_DWORD /d 1  
reg add HKLM\Software\Microsoft\MiracastReceiver /v EnabledOnACOnly /t REG_DWORD /d 1  
```
<span data-ttu-id="7df8e-164">이렇게 하면 A/C 전원에 연결 되어 있는 동안에만 동의 알림 없이 Miracast를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7df8e-164">This will enable Miracast without a consent notification, only on secure networks, and only while connected to A/C power.</span></span> <span data-ttu-id="7df8e-165">IoT Core에서 Miracast 수신기를 실행 하는 데 권장 되는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="7df8e-165">This is the recommended way to run a Miracast receiver on IoT Core.</span></span>

## <a name="windows-iot-as-a-miracast-source"></a><span data-ttu-id="7df8e-166">Windows IoT를 Miracast 원본으로</span><span class="sxs-lookup"><span data-stu-id="7df8e-166">Windows IoT as a Miracast Source</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7df8e-167">장치를 Miracast 원본으로 사용 하기 전에 아래와 같이 [Windows 장치 포털](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal) 에서 Is\on보드 ingtask 앱을 꺼야 합니다. 단, 한 번만 수행 하면 됩니다. ![Is\on보드 Ingtask 앱 해제](../media/Miracast/IoTOnboardingOff.gif)</span><span class="sxs-lookup"><span data-stu-id="7df8e-167">Before trying to use your device as a Miracast Source, please turn off the IoTOnboardingTask app from the [Windows Device Portal](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal) as shown below, which you'll only need to do once: ![Turn off IoTOnboardingTask app](../media/Miracast/IoTOnboardingOff.gif)</span></span>
>
> <span data-ttu-id="7df8e-168">그런 다음 장치를 다시 시작 하세요.</span><span class="sxs-lookup"><span data-stu-id="7df8e-168">Afterwards, please restart the device</span></span>

<span data-ttu-id="7df8e-169">앱에서 네임 스페이스의 공용 api를 통해 호환 되는 `Windows.Media.Casting` 장치에서 Miracast 캐스트를 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7df8e-169">You can set up Miracast casting on your compatible device through public APIs from the `Windows.Media.Casting` namespace in your app.</span></span>

<span data-ttu-id="7df8e-170">이러한 Api의 작동 방식을 확인 하려면 [BASICMEDIACASTING UWP 샘플](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/BasicMediaCasting) 을 다운로드 하 고 장치에서 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="7df8e-170">To see these APIs in action, download the [BasicMediaCasting UWP sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/BasicMediaCasting) and run it on your device.</span></span> <span data-ttu-id="7df8e-171">이 샘플의 Api는 다음과 같은 시나리오를 다룹니다. 이러한 시나리오는 모두 Miracast 호환 IoT Core 장치에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7df8e-171">The APIs in the sample cover the following scenarios, all of which run on Miracast-compatible IoT Core devices:</span></span>
1. <span data-ttu-id="7df8e-172">기본 제공 캐스트를 사용 하 여 Miracast, DLNA 및 Bluetooth 장치로 콘텐츠를 전송 하는 기본 미디어 캐스팅</span><span class="sxs-lookup"><span data-stu-id="7df8e-172">Basic Media Casting, which uses the built-in casting to send content to Miracast, DLNA, and Bluetooth devices</span></span>
2. <span data-ttu-id="7df8e-173">캐스팅 선택기를 사용 하 여 캐스팅 하 여 장치 선택기를 추가로 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7df8e-173">Casting Using the Casting Picker, which allows you to further customize the Device Picker</span></span>
3. <span data-ttu-id="7df8e-174">사용자 지정 선택기를 사용 하 여 캐스팅-장치를 선택 하기 위한 사용자 지정 UX를 빌드하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7df8e-174">Casting Using a Custom Picker, which illustrates how to build custom UX for selecting devices</span></span>

> [!NOTE]
> <span data-ttu-id="7df8e-175">일부 Miracast 싱크 (Surface 노트북, Surface Hub, 무선 디스플레이 어댑터가 있는 PC)는 IoT Core 캐스트 장치와 호환 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7df8e-175">Some Miracast sinks (Surface Laptop, Surface Hub, PC with a Wireless Display Adapter) are incompatible with IoT Core casting devices.</span></span> <span data-ttu-id="7df8e-176">Miracast 싱크와 호환 되는 모니터와 함께 [Microsoft 무선 디스플레이 어댑터](https://www.microsoft.com/accessories/en-us/products/adapters/wireless-display-adapter-2/p3q-00001) 를 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="7df8e-176">We recommend using the [Microsoft Wireless Display Adapter](https://www.microsoft.com/accessories/en-us/products/adapters/wireless-display-adapter-2/p3q-00001) with a compatible monitor as your Miracast sink.</span></span>
