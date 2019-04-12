---
title: IoT Core에는 Miracast
author: saraclay
ms.author: saclayt
ms.date: 11/30/2017
ms.topic: article
description: 장치에서 Miracast 기능을 포함 하는 방법 알아보기
keywords: windows iot, miracast, 연결
ms.openlocfilehash: c58def4b218d35c78532f54df4a74fb572c8549e
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59515242"
---
# <a name="miracast-on-iot-core"></a><span data-ttu-id="f4102-104">IoT Core에는 Miracast</span><span class="sxs-lookup"><span data-stu-id="f4102-104">Miracast on IoT Core</span></span>

<span data-ttu-id="f4102-105">이 문서에서는 IoT Core 장치에서 Miracast 기능을 포함 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4102-105">This document will show you how to include Miracast functionality on your IoT Core device.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f4102-106">이 기능은 에서만 Insider 빌드 17093 이상 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4102-106">This feature is only available on Insider Build 17093 and above</span></span>

## <a name="miracast-overview"></a><span data-ttu-id="f4102-107">Miracast 개요</span><span class="sxs-lookup"><span data-stu-id="f4102-107">Miracast Overview</span></span>

<span data-ttu-id="f4102-108">Miracast 연결을 두 가지 구성 요소로 이루어집니다: 원본과 싱크 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4102-108">A Miracast connection is made up of two components: the Source and the Sink.</span></span> <span data-ttu-id="f4102-109">**Miracast 원본** 콘텐츠를 전송 합니다 **Miracast 싱크**, 콘텐츠를 표시 하는 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4102-109">The **Miracast Source** sends content to the **Miracast Sink**, which displays the content.</span></span> <span data-ttu-id="f4102-110">연결을 만들려면 싱크 보급 자체 연결 된 Wi-fi 네트워크에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4102-110">To create the connection, the Sink advertises itself to the connected Wi-Fi network.</span></span> <span data-ttu-id="f4102-111">원본을 사용 하는 **장치 선택** 싱크를 선택 하 고 연결 요청을 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4102-111">The Source uses the **Device Picker** to select the Sink and request a connection.</span></span> <span data-ttu-id="f4102-112">연결 요청 되 면 싱크에 받을지 경고 원본에 연결 하려고 하는 연결 수행 해야 할지 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4102-112">Once the connection is requested, a user at the Sink receives an alert that the source is attempting to make a connection and must verify that the connection should take place.</span></span> <span data-ttu-id="f4102-113">이렇게 되 면, 원본 연결을 취소 하는 원본 또는 싱크 광고 중지 될 때까지 싱크로 캐스팅을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4102-113">Once this happens, the Source begins casting to the Sink until either the Source cancels the connection or the Sink stops advertising.</span></span>

## <a name="hardware-requirements"></a><span data-ttu-id="f4102-114">하드웨어 요구 사항</span><span class="sxs-lookup"><span data-stu-id="f4102-114">Hardware requirements</span></span>

<span data-ttu-id="f4102-115">둘 다가 원본 및 싱크는 장치도 Miracast-호환 Wi-fi 및 그래픽 드라이버 및 칩셋 제대로 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4102-115">Both Source and Sink devices require Miracast-compatible Wi-Fi and Graphics drivers and chipsets to function properly.</span></span> <span data-ttu-id="f4102-116">장치의 Miracast 호환 하드웨어 있는지를 확인 하려면 다음을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4102-116">To find out if your device has Miracast-compatible hardware, run:</span></span> 
```
netsh wlan show driver
```
<span data-ttu-id="f4102-117">장치의 명령 프롬프트입니다.</span><span class="sxs-lookup"><span data-stu-id="f4102-117">in the device's command prompt.</span></span>

<span data-ttu-id="f4102-118">장치에서 Miracast 지원, 아래 출력이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4102-118">If the device supports Miracast, you should see the output below:</span></span>

![호환 장치 출력](../media/Miracast/CompatibleDevice.png)

<span data-ttu-id="f4102-120">아래 표에서 IoT Core 참조 플랫폼용 Miracast 호환성을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f4102-120">The below table shows Miracast compatibility for the IoT Core reference platforms:</span></span>

| <span data-ttu-id="f4102-121">보드</span><span class="sxs-lookup"><span data-stu-id="f4102-121">Board</span></span> | <span data-ttu-id="f4102-122">SoC</span><span class="sxs-lookup"><span data-stu-id="f4102-122">SoC</span></span> | <span data-ttu-id="f4102-123">WiFi 드라이버 제공</span><span class="sxs-lookup"><span data-stu-id="f4102-123">WiFi Drivers Present</span></span> | <span data-ttu-id="f4102-124">그래픽 드라이버 제공</span><span class="sxs-lookup"><span data-stu-id="f4102-124">Graphics Drivers Present</span></span> | <span data-ttu-id="f4102-125">Miracast 호환</span><span class="sxs-lookup"><span data-stu-id="f4102-125">Miracast-Compatible</span></span> |
|-------|-----|----------------------|--------------------------|---------------------|
| <span data-ttu-id="f4102-126">Qualcomm Dragonboard 410 c</span><span class="sxs-lookup"><span data-stu-id="f4102-126">Qualcomm Dragonboard 410c</span></span> | <span data-ttu-id="f4102-127">Snapdragon 410</span><span class="sxs-lookup"><span data-stu-id="f4102-127">Snapdragon 410</span></span> | <span data-ttu-id="f4102-128">예</span><span class="sxs-lookup"><span data-stu-id="f4102-128">Yes</span></span> | <span data-ttu-id="f4102-129">예</span><span class="sxs-lookup"><span data-stu-id="f4102-129">Yes</span></span> | <span data-ttu-id="f4102-130">예</span><span class="sxs-lookup"><span data-stu-id="f4102-130">Yes</span></span> |
| <span data-ttu-id="f4102-131">Raspberry Pi 2/3</span><span class="sxs-lookup"><span data-stu-id="f4102-131">Raspberry Pi 2/3</span></span> | <span data-ttu-id="f4102-132">Broadcom BCM283x</span><span class="sxs-lookup"><span data-stu-id="f4102-132">Broadcom BCM283x</span></span> | <span data-ttu-id="f4102-133">예</span><span class="sxs-lookup"><span data-stu-id="f4102-133">Yes</span></span> | <span data-ttu-id="f4102-134">아니오</span><span class="sxs-lookup"><span data-stu-id="f4102-134">No</span></span> | <span data-ttu-id="f4102-135">아니요</span><span class="sxs-lookup"><span data-stu-id="f4102-135">No</span></span> |
| <span data-ttu-id="f4102-136">Minnowboard 최대</span><span class="sxs-lookup"><span data-stu-id="f4102-136">Minnowboard Max</span></span> | <span data-ttu-id="f4102-137">Intel Atom E3825</span><span class="sxs-lookup"><span data-stu-id="f4102-137">Intel Atom E3825</span></span> | <span data-ttu-id="f4102-138">예</span><span class="sxs-lookup"><span data-stu-id="f4102-138">Yes</span></span> | <span data-ttu-id="f4102-139">아니오</span><span class="sxs-lookup"><span data-stu-id="f4102-139">No</span></span> | <span data-ttu-id="f4102-140">아니요</span><span class="sxs-lookup"><span data-stu-id="f4102-140">No</span></span> |
| <span data-ttu-id="f4102-141">최대 제곱</span><span class="sxs-lookup"><span data-stu-id="f4102-141">UP Squared</span></span> | <span data-ttu-id="f4102-142">Intel Celeron N3350</span><span class="sxs-lookup"><span data-stu-id="f4102-142">Intel Celeron N3350</span></span> | <span data-ttu-id="f4102-143">예</span><span class="sxs-lookup"><span data-stu-id="f4102-143">Yes</span></span> | <span data-ttu-id="f4102-144">예</span><span class="sxs-lookup"><span data-stu-id="f4102-144">Yes</span></span> | <span data-ttu-id="f4102-145">예</span><span class="sxs-lookup"><span data-stu-id="f4102-145">Yes</span></span> |


### <a name="wi-fi"></a><span data-ttu-id="f4102-146">Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="f4102-146">Wi-Fi</span></span>

<span data-ttu-id="f4102-147">Wi-fi 드라이버 및 장치에 대 한 칩셋 지원 해야 Wi-Fi Direct Miracast 지원 하기 위해 기타 기능이 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4102-147">The Wi-Fi driver and chipset for the device must support Wi-Fi Direct, among other capabilities, to support Miracast.</span></span> <span data-ttu-id="f4102-148">장치에 이러한 기능이 없는 경우에 USB Wi-fi 동글 대신 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4102-148">If your device does not have these features, you can use a USB Wi-Fi dongle instead.</span></span> <span data-ttu-id="f4102-149">권장 합니다 [300 M 무선 USB 어댑터](http://a.co/fdhEhV9)합니다.</span><span class="sxs-lookup"><span data-stu-id="f4102-149">We recommend the [300M Wireless USB Adapter](http://a.co/fdhEhV9).</span></span>

### <a name="graphics"></a><span data-ttu-id="f4102-150">그래픽</span><span class="sxs-lookup"><span data-stu-id="f4102-150">Graphics</span></span>

<span data-ttu-id="f4102-151">그래픽 드라이버 및 칩셋 h.264 인코딩 및 디코딩 Miracast 지원 하도록 지원 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4102-151">The Graphics driver and chipset must support h.264 encoding and decoding to support Miracast.</span></span> <span data-ttu-id="f4102-152">장치의 호환 되는 그래픽 드라이버 및/또는 칩셋에 없는 사용 하는 경우에 새 장치를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4102-152">If your device does not have a compatible graphics driver and/or chipset, you will have to pick a new device.</span></span> <span data-ttu-id="f4102-153">Miracast 호환 장치를 선택할 때 위의 매트릭스를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f4102-153">Please consult the above matrix when choosing a Miracast-compatible device.</span></span>

## <a name="windows-iot-as-a-miracast-sink"></a><span data-ttu-id="f4102-154">Windows IoT Miracast 싱크로</span><span class="sxs-lookup"><span data-stu-id="f4102-154">Windows IoT as a Miracast Sink</span></span>

<span data-ttu-id="f4102-155">Miracast 싱크로 장치를 사용 하려면 장치에서 연결 앱을 사용 하도록 설정한 후 레지스트리에서 Miracast를 사용 하도록 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4102-155">To enable your device as a Miracast sink, you will need to enable the Connect app on your device, then enable Miracast in the registry.</span></span>

### <a name="enable-the-connect-app"></a><span data-ttu-id="f4102-156">사용 하도록 설정 된 앱 연결</span><span class="sxs-lookup"><span data-stu-id="f4102-156">Enable the Connect App</span></span>

<span data-ttu-id="f4102-157">연결 앱을 사용 하려면 포함 해야 합니다 **IOT_MIRACAST_RX_APP** 이미지에는 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="f4102-157">To enable the Connect app, you'll need to include the **IOT_MIRACAST_RX_APP** feature to your image.</span></span> <span data-ttu-id="f4102-158">포함 해야 **Microsoft Connect 둘** 하 고 **Microsoft 연결 Package_Lang_XXXX.cab** (여기서 XXXX는 언어, 즉 "enUS") 이미지에서.</span><span class="sxs-lookup"><span data-stu-id="f4102-158">You'll also need to include  **Microsoft-Connect-Package.cab** and **Microsoft-Connect-Package_Lang_XXXX.cab** in your image (where XXXX is a language, i.e. "enUS").</span></span> 

<span data-ttu-id="f4102-159">참조 [이 페이지](https://docs.microsoft.com/windows-hardware/manufacture/iot/deploy-your-app-with-a-standard-board#update-the-feature-manifest) 이미지에 기능 및 패키지를 추가 하는 방법에 대 한 자세한 내용은 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4102-159">See [this page](https://docs.microsoft.com/windows-hardware/manufacture/iot/deploy-your-app-with-a-standard-board#update-the-feature-manifest) for more details about how to add features and packages to your image.</span></span> <span data-ttu-id="f4102-160">있습니다 수 또한 테스트용으로 로드 패키지 및 기존 이미지에 기능을 수행 하 여 [이러한 지침](https://docs.microsoft.com/windows/iot-core/build-your-image/createinstallpackage)합니다.</span><span class="sxs-lookup"><span data-stu-id="f4102-160">You can also side-load the package and features to existing images by following [these instructions](https://docs.microsoft.com/windows/iot-core/build-your-image/createinstallpackage).</span></span> <span data-ttu-id="f4102-161">이 기능을 테스트용으로 로드를 방지 하는 업데이트 수신을 점을 염두에 두십시오.</span><span class="sxs-lookup"><span data-stu-id="f4102-161">Keep in mind that side-loading this feature will prevent it from receiving updates.</span></span>


### <a name="enable-miracast"></a><span data-ttu-id="f4102-162">Miracast를 사용 하도록 설정</span><span class="sxs-lookup"><span data-stu-id="f4102-162">Enable Miracast</span></span>

<span data-ttu-id="f4102-163">통해 장치에 연결할 [PowerShell](https://docs.microsoft.com/windows/iot-core/connect-your-device/powershell) 또는 [Windows Device Portal](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal) 하 고 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4102-163">Connect to your device through [PowerShell](https://docs.microsoft.com/windows/iot-core/connect-your-device/powershell) or the [Windows Device Portal](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal) and run the following commands:</span></span>
```
reg add HKLM\Software\Microsoft\PlayToReceiver /v AutoEnabled /t REG_DWORD /d 1  
reg add HKLM\Software\Microsoft\MiracastReceiver /v  ConsentToast /t REG_DWORD /d 0  
reg add HKLM\Software\Microsoft\MiracastReceiver /v NetworkQualificationEnabled /t REG_DWORD /d 1  
reg add HKLM\Software\Microsoft\MiracastReceiver /v EnabledOnACOnly /t REG_DWORD /d 1  
```
<span data-ttu-id="f4102-164">이렇게 하면 보안 네트워크 에서만 및 a/C 전원에 연결 하는 동안에 동의 알림을 없이 Miracast 활성화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4102-164">This will enable Miracast without a consent notification, only on secure networks, and only while connected to A/C power.</span></span> <span data-ttu-id="f4102-165">이것이 Miracast 수신기 IoT Core에서 실행 하는 권장된 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="f4102-165">This is the recommended way to run a Miracast receiver on IoT Core.</span></span>

## <a name="windows-iot-as-a-miracast-source"></a><span data-ttu-id="f4102-166">Windows IoT Miracast 원본으로</span><span class="sxs-lookup"><span data-stu-id="f4102-166">Windows IoT as a Miracast Source</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f4102-167">장치를 Miracast 소스로 사용 하기 전에 해제 하십시오 IoTOnboardingTask 앱 합니다 [Windows Device Portal](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal) 아래와 같이 한 번만 해야 하는: ![IoTOnboardingTask 앱 해제</span><span class="sxs-lookup"><span data-stu-id="f4102-167">Before trying to use your device as a Miracast Source, please turn off the IoTOnboardingTask app from the [Windows Device Portal](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal) as shown below, which you'll only need to do once: ![Turn off IoTOnboardingTask app</span></span>](../media/Miracast/IoTOnboardingOff.gif)
>
> <span data-ttu-id="f4102-168">그런 다음 다시 시작 하십시오 장치</span><span class="sxs-lookup"><span data-stu-id="f4102-168">Afterwards, please restart the device</span></span>

<span data-ttu-id="f4102-169">공용 Api 통해 호환 장치에서 Miracast 캐스팅을 설정할 수 있습니다는 `Windows.Media.Casting` 앱에서 네임 스페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="f4102-169">You can set up Miracast casting on your compatible device through public APIs from the `Windows.Media.Casting` namespace in your app.</span></span>

<span data-ttu-id="f4102-170">작업에서 이러한 Api를 보려면 다운로드 합니다 [BasicMediaCasting UWP 샘플](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/BasicMediaCasting) 및 장치에서 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4102-170">To see these APIs in action, download the [BasicMediaCasting UWP sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/BasicMediaCasting) and run it on your device.</span></span> <span data-ttu-id="f4102-171">이 샘플의 Api를 Miracast 호환 IoT Core 장치에서 실행 하는 모든 다음 시나리오를 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="f4102-171">The APIs in the sample cover the following scenarios, all of which run on Miracast-compatible IoT Core devices:</span></span>
1. <span data-ttu-id="f4102-172">Miracast 고 DLNA, Bluetooth 장치에 콘텐츠를 전송 하는 기본 제공 캐스팅을 사용 하는 기본 미디어 캐스팅</span><span class="sxs-lookup"><span data-stu-id="f4102-172">Basic Media Casting, which uses the built-in casting to send content to Miracast, DLNA, and Bluetooth devices</span></span>
2. <span data-ttu-id="f4102-173">장치 선택기를 사용자 지정할 수 있는 캐스팅 선택기를 사용 하는 캐스팅</span><span class="sxs-lookup"><span data-stu-id="f4102-173">Casting Using the Casting Picker, which allows you to further customize the Device Picker</span></span>
3. <span data-ttu-id="f4102-174">장치를 선택 하기 위한 사용자 지정 사용자 경험을 구축 하는 방법을 보여 주는 사용자 지정 선택기를 사용 하 여 캐스팅을</span><span class="sxs-lookup"><span data-stu-id="f4102-174">Casting Using a Custom Picker, which illustrates how to build custom UX for selecting devices</span></span>

> [!NOTE]
> <span data-ttu-id="f4102-175">일부 Miracast 싱크 (무선 디스플레이 어댑터를 사용 하 여 Surface Laptop, Surface Hub, PC) IoT Core 캐스팅 장치와 호환 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f4102-175">Some Miracast sinks (Surface Laptop, Surface Hub, PC with a Wireless Display Adapter) are incompatible with IoT Core casting devices.</span></span> <span data-ttu-id="f4102-176">사용 하는 것이 좋습니다 합니다 [Microsoft 무선 디스플레이 어댑터](https://www.microsoft.com/accessories/en-us/products/adapters/wireless-display-adapter-2/p3q-00001) 프로그램 Miracast 싱크로 호환 모니터를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4102-176">We recommend using the [Microsoft Wireless Display Adapter](https://www.microsoft.com/accessories/en-us/products/adapters/wireless-display-adapter-2/p3q-00001) with a compatible monitor as your Miracast sink.</span></span>
