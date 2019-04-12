---
title: Windows 10 IoT Core 사용 하 여 네트워크 3D 프린터
author: saraclay
ms.author: saclayt
ms.date: 09/05/17
ms.topic: article
description: 인쇄 서버에 Windows 10 IoT Core 장치를 사용 하 여 3D 프린터에 연결 하는 방법을 알아봅니다.
keywords: windows iot, 3D, 3D 프린터, 인쇄 서버, 네트워크 3D 프린터
ms.openlocfilehash: 7a9bcc7871c62be5a73319ca284127ee4abc42f5
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512374"
---
# <a name="network-3d-printer-with-windows-10-iot-core"></a><span data-ttu-id="fa4ad-104">Windows 10 IoT Core 사용 하 여 네트워크 3D 프린터</span><span class="sxs-lookup"><span data-stu-id="fa4ad-104">Network 3D Printer with Windows 10 IoT Core</span></span>

<span data-ttu-id="fa4ad-105">인쇄 서버에 Windows 10 IoT Core 장치를 설정 하 고 3D 프린터 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa4ad-105">Turn your Windows 10 IoT Core device into a print server and connect your 3D Printer to it.</span></span> <span data-ttu-id="fa4ad-106">다른 장치에서 프린터를 무선으로 액세스할 수 없게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa4ad-106">You will be able to access your printer wirelessly from other devices.</span></span>

## <a name="1-install-windows-10-iot-core-on-your-device"></a><span data-ttu-id="fa4ad-107">1. Windows 10 IoT Core 장치에 설치</span><span class="sxs-lookup"><span data-stu-id="fa4ad-107">1. Install Windows 10 IoT Core on your device</span></span>
___
<span data-ttu-id="fa4ad-108">시작 하기 전에 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa4ad-108">Before you start, you will need:</span></span>

* <span data-ttu-id="fa4ad-109">최신 버전의 Windows 10 IoT Core Insider Preview 설치를 사용 하 여 보드입니다.</span><span class="sxs-lookup"><span data-stu-id="fa4ad-109">A board with the latest version of Windows 10 IoT Core Insider Preview installed.</span></span> <span data-ttu-id="fa4ad-110">에 따라 합니다 [시작 가이드](https://developer.microsoft.com/en-us/windows/iot/getstarted) IoT 대시보드 앱 및 Windows 10 IoT Core 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa4ad-110">Follow the [Get Started guide](https://developer.microsoft.com/en-us/windows/iot/getstarted) to get the IoT Dashboard app and install Windows 10 IoT Core.</span></span>
* <span data-ttu-id="fa4ad-111">네트워크 3D 프린터 앱 호환 3D 프린터:</span><span class="sxs-lookup"><span data-stu-id="fa4ad-111">A 3D Printer compatible with our Network 3D Printer app:</span></span>

    * <span data-ttu-id="fa4ad-112">Lulzbot Taz 6</span><span class="sxs-lookup"><span data-stu-id="fa4ad-112">Lulzbot Taz 6</span></span>
    * <span data-ttu-id="fa4ad-113">Makergear M2</span><span class="sxs-lookup"><span data-stu-id="fa4ad-113">Makergear M2</span></span>
    * <span data-ttu-id="fa4ad-114">더하기 및 간단한 Printrbot Play</span><span class="sxs-lookup"><span data-stu-id="fa4ad-114">Printrbot Play, Plus and Simple</span></span>
    * <span data-ttu-id="fa4ad-115">Prusa i3 Mk2</span><span class="sxs-lookup"><span data-stu-id="fa4ad-115">Prusa i3 Mk2</span></span>
    * <span data-ttu-id="fa4ad-116">Ultimaker 원래 값과 원래 +</span><span class="sxs-lookup"><span data-stu-id="fa4ad-116">Ultimaker Original and Original+</span></span>
    * <span data-ttu-id="fa4ad-117">Ultimaker 2, 2 +</span><span class="sxs-lookup"><span data-stu-id="fa4ad-117">Ultimaker 2 and 2+</span></span>
    * <span data-ttu-id="fa4ad-118">Ultimaker 2 확장 및 확장 +</span><span class="sxs-lookup"><span data-stu-id="fa4ad-118">Ultimaker 2 Extended and Extended+</span></span>
    * <span data-ttu-id="fa4ad-119">CraftBot 2</span><span class="sxs-lookup"><span data-stu-id="fa4ad-119">CraftBot 2</span></span>
    * <span data-ttu-id="fa4ad-120">CraftBot 더하기</span><span class="sxs-lookup"><span data-stu-id="fa4ad-120">CraftBot PLUS</span></span>
    * <span data-ttu-id="fa4ad-121">LulzBot 미니</span><span class="sxs-lookup"><span data-stu-id="fa4ad-121">LulzBot Mini</span></span>
    * <span data-ttu-id="fa4ad-122">Velleman K8200</span><span class="sxs-lookup"><span data-stu-id="fa4ad-122">Velleman K8200</span></span>

## <a name="2-connect-your-3d-printer-to-your-device"></a><span data-ttu-id="fa4ad-123">2. 3D 프린터 장치에 연결</span><span class="sxs-lookup"><span data-stu-id="fa4ad-123">2. Connect your 3D Printer to your device</span></span>
___
* <span data-ttu-id="fa4ad-124">플러그 인에 Windows 10 IoT Core 3D 프린터 보드는 USB 케이블을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa4ad-124">Plug-in your 3D printer to your Windows 10 IoT Core board using the USB cable.</span></span>

    ![3D 프린터 장치에 연결](../media/3DPrintServer/connect-3d-printer.png)

* <span data-ttu-id="fa4ad-126">IoT 대시보드 앱을 열고 장치에 표시 되는지 확인 합니다 **내 장치** 탭 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa4ad-126">Open the IoT Dashboard app and verify that your device shows up in the **My devices** tab.</span></span>

    ![장치의 IoT 대시보드에서 표시 되는지 확인 합니다.](../media/3DPrintServer/selectDevice.png)
    
## <a name="3-deploy-the-network-3d-printer-app"></a><span data-ttu-id="fa4ad-128">3. 네트워크를 배포 3D 프린터 앱</span><span class="sxs-lookup"><span data-stu-id="fa4ad-128">3. Deploy the Network 3D Printer app</span></span>
___
* <span data-ttu-id="fa4ad-129">IoT 대시보드에서 다음을 클릭 합니다 **몇 가지 샘플을 시험해 볼** 섹션입니다.</span><span class="sxs-lookup"><span data-stu-id="fa4ad-129">In IoT Dashboard, click on the **Try some samples** section.</span></span>
* <span data-ttu-id="fa4ad-130">네트워크 3D 프린터 샘플 앱을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa4ad-130">Select the Network 3D Printer sample app.</span></span>

   ![3D 네트워크 프린터를 설치 합니다.](../media/3dprintserver/dashboard-samples.png)

* <span data-ttu-id="fa4ad-132">3D 프린터 모델 및 키를 눌러 선택 합니다 **배포 및 실행** IoT Core 장치에 앱을 배포 하는 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="fa4ad-132">Select your 3D Printer model and press the **Deploy and run** button to deploy the app to your IoT Core device.</span></span> 

    ![3D 네트워크 프린터를 설치 합니다.](../media/3dprintserver/dashboard-app.png)

    <span data-ttu-id="fa4ad-134">[LulzBot TAZ 6 이미지](http://devel.lulzbot.com/TAZ/Olive/photos/TAZ_6_Angle_Rock2pus_transparent.png) 하 여 [Aleph 개체, Inc.](https://www.alephobjects.com/) 사용이 허가 됩니다 [CC BY SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/)합니다.</span><span class="sxs-lookup"><span data-stu-id="fa4ad-134">[LulzBot TAZ 6 image](http://devel.lulzbot.com/TAZ/Olive/photos/TAZ_6_Angle_Rock2pus_transparent.png) by [Aleph Objects, Inc.](https://www.alephobjects.com/) is licensed under [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/).</span></span>
    
    <span data-ttu-id="fa4ad-135">프린터 목록에서 사용자 지정 프린터 선택 "사용자 지정" 옵션을 설치 하려면.</span><span class="sxs-lookup"><span data-stu-id="fa4ad-135">If you wish to install a custom printer select the "Custom" option from the list of Printers.</span></span> <span data-ttu-id="fa4ad-136">사용자 지정 3d 프린터 호출 PrintDeviceCapabilities.xml 파일을 올바르게 연결 하 고 3d 프린터에 인쇄를 제공 해야 하는 구성 xml을 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa4ad-136">Custom 3d Printers need a configuration xml called the PrintDeviceCapabilities.xml file to be provided to correctly connect and print to the 3d printer.</span></span> <span data-ttu-id="fa4ad-137">샘플 PrintDeviceCapabilities.xml 파일을 확인할 수 있습니다. https://docs.microsoft.com/windows-hardware/drivers/3dprint/sample-configuration-xml</span><span class="sxs-lookup"><span data-stu-id="fa4ad-137">A sample PrintDeviceCapabilities.xml file can be found here https://docs.microsoft.com/windows-hardware/drivers/3dprint/sample-configuration-xml</span></span>
   
   <span data-ttu-id="fa4ad-138">Xml 파일에서 해야 할 최소 변경 내용을 다음 섹션에서는 특정 호환 프린터에 올바른 값으로 업데이트 되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa4ad-138">The minimum changes you need to make in the xml file are to update the following sections with the correct values specific to your compatible printer.</span></span>

<span data-ttu-id="fa4ad-139">3d 모델을 처리할 때 이러한 값에 슬라이서에 3d 프린터의 인쇄 평판 크기 지정</span><span class="sxs-lookup"><span data-stu-id="fa4ad-139">These values specify the print bed dimensions of your 3d printer to the slicer when processing the 3d model</span></span>

    <psk3d:Job3DOutputAreaWidth>200000</psk3d:Job3DOutputAreaWidth>
    <psk3d:Job3DOutputAreaDepth>200000</psk3d:Job3DOutputAreaDepth>
    <psk3d:Job3DOutputAreaHeight>200000</psk3d:Job3DOutputAreaHeight>


<span data-ttu-id="fa4ad-140">Psk3dx:baudrate xml 태그에 값 raspberry pi3에서 3d 프린터와 통신 하는 동안 사용할 특정 전송 속도 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa4ad-140">The value in the psk3dx:baudrate xml tag controls the specific baud rate to use while communicating with the 3d printer from the raspberry pi3.</span></span> <span data-ttu-id="fa4ad-141">3d 프린터 관련 적절 한 전송 속도 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa4ad-141">Set the appropriate baud rate specific to your 3d printer.</span></span> 

```
\<psk3dx:baudrate\>115200</psk3dx:baudrate>
```

<span data-ttu-id="fa4ad-142">PrintDeviceCapabilities xml에 다른 값은 3d 인쇄 드라이버에서 특정 호환 프린터를 사용 하 여 작동 방법을 미세 조정 하려면 슬라이서를 알리는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa4ad-142">The other values in the PrintDeviceCapabilities xml are used to notify the slicer in the 3d print driver to fine tune how it works with your specific compatible printer.</span></span>
<span data-ttu-id="fa4ad-143">자세한 내용은 이러한 값을 제공 하는 모든 [여기](https://docs.microsoft.com/windows-hardware/drivers/3dprint/slicer-settings)합니다.</span><span class="sxs-lookup"><span data-stu-id="fa4ad-143">More information on all these values are provided [here](https://docs.microsoft.com/windows-hardware/drivers/3dprint/slicer-settings).</span></span>

    
    
## <a name="4-add-your-3d-printer"></a><span data-ttu-id="fa4ad-144">4. 3D 프린터를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa4ad-144">4. Add your 3D Printer</span></span>
___
* <span data-ttu-id="fa4ad-145">Windows 10 PC로 이동할 **설정을** -> **장치** -> **프린터 및 스캐너**합니다.</span><span class="sxs-lookup"><span data-stu-id="fa4ad-145">Go to your Windows 10 PC and go to **Settings** -> **Devices** -> **Printers & Scanners**.</span></span>
* <span data-ttu-id="fa4ad-146">키를 눌러 **프린터 또는 스캐너 추가**합니다.</span><span class="sxs-lookup"><span data-stu-id="fa4ad-146">Press **Add a printer or scanner**.</span></span>

     ![장치를 추가 하는 Windows 설정](../media/3dprintserver/add-printer.png)

* <span data-ttu-id="fa4ad-148">3D 프린터 및 키를 눌러 선택할 **장치 추가**합니다.</span><span class="sxs-lookup"><span data-stu-id="fa4ad-148">Select your 3D Printer and press **Add device**.</span></span> <span data-ttu-id="fa4ad-149">프린터를 자동으로 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa4ad-149">The printer will install automatically.</span></span>

     ![장치를 추가 하는 Windows 설정](../media/3dprintserver/add-device.png)

<span data-ttu-id="fa4ad-151">프린터는 이제 설치 하는 축을 선택 하 고 USB 케이블을 사용 하 여 연결 된 것 처럼 정확 하 게 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa4ad-151">Congratulations your printer is now installed and will behave exactly as if it was connected with a USB cable.</span></span>
<span data-ttu-id="fa4ad-152">이제 사용 하 여 인쇄할 수 있습니다 [3D 작성기](https://msdn.microsoft.com/windows/hardware/mt561568.aspx)합니다.</span><span class="sxs-lookup"><span data-stu-id="fa4ad-152">You can now print to it using [3D Builder](https://msdn.microsoft.com/windows/hardware/mt561568.aspx).</span></span>
