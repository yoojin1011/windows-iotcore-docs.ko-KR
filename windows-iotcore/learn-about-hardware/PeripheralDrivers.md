---
title: USB 주변 장치 드라이버 설치
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 드라이버 패키지 만들기 및 장치에 타사 드라이버를 설치 하는 방법에 알아봅니다.
keywords: windows iot, USB 드라이버, USB 주변 장치
ms.openlocfilehash: dd7eec9defc676bb84efe988d771794d9bb7c9ef
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513582"
---
# <a name="install-usb-peripheral-drivers"></a><span data-ttu-id="5189d-104">USB 주변 장치 드라이버 설치</span><span class="sxs-lookup"><span data-stu-id="5189d-104">Install USB peripheral drivers</span></span>
<span data-ttu-id="5189d-105">타사 드라이버 (usb) USB 모바일 광대역 모뎀, 프린터, 스캐너 등과 같은 주변 장치에 대 한 추가 하려면 다음 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="5189d-105">Follow the steps below to add third-party drivers (usb) for peripheral devices such as USB Mobile broadband modems, printers, scanners etc.</span></span> 

## <a name="step-1-get-drivers-from-pc"></a><span data-ttu-id="5189d-106">1단계: PC에서 드라이버를 가져오려면</span><span class="sxs-lookup"><span data-stu-id="5189d-106">Step 1: Get Drivers from PC</span></span>
___
<span data-ttu-id="5189d-107">X86을 가져오려는 단계는 PC에서 드라이버의 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="5189d-107">The Step is to get the x86 version of the drivers from PC.</span></span> <span data-ttu-id="5189d-108">ARM, sys/inf 파일을 가져올 주변 장치 공급 업체에 문의 하세요.</span><span class="sxs-lookup"><span data-stu-id="5189d-108">For ARM, please contact the supplier of the peripheral to get the sys/inf files.</span></span>


1. <span data-ttu-id="5189d-109">Windows PC에 장치 연결</span><span class="sxs-lookup"><span data-stu-id="5189d-109">Connect the device to the windows PC</span></span>

2. <span data-ttu-id="5189d-110">PC에 장치 드라이버를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="5189d-110">Install the driver for the device on the PC</span></span>

3. <span data-ttu-id="5189d-111">장치 관리자, (범용 직렬 버스 컨트롤러 아래 나열 됨)이이 장치를 선택 하 고 마우스 오른쪽 단추로 클릭를 속성을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="5189d-111">Go to Device Manager, select this device (listed under Universal Serial Bus controllers) and right click and select Properties.</span></span>

4. <span data-ttu-id="5189d-112">속성 창에서 드라이버 탭으로 이동한 다음 드라이버 세부 정보 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5189d-112">Go to Driver tab in the Properties window, and click on Driver Details.</span></span> <span data-ttu-id="5189d-113">참고 sys 파일을 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="5189d-113">Note the sys files listed there.</span></span>

5. <span data-ttu-id="5189d-114">Sys 파일을 복사할 `C:\Windows\system32` 및에서 관련된 inf 파일 또한 `C:\Windows\Inf`합니다.</span><span class="sxs-lookup"><span data-stu-id="5189d-114">Copy the sys files from `C:\Windows\system32` and also the related inf file from `C:\Windows\Inf`.</span></span> <span data-ttu-id="5189d-115">찾을 수 있습니다 inf 파일에서 검색 해 보십시오는 sys 파일 참조는 `.inf` 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="5189d-115">You can find the inf file by searcing for the sys file reference in the `.inf` files.</span></span> <span data-ttu-id="5189d-116">Inf에 나열 된 추가 파일을 복사 해야 하 고 사용 하는 경우 만든 inf_filelist.txt 파일에 나열 됩니다 `inf2pkg.cmd` 다음 단계에서 합니다.</span><span class="sxs-lookup"><span data-stu-id="5189d-116">You may need to copy additional files listed in the Inf and these will be listed in the inf_filelist.txt file created when using  `inf2pkg.cmd` in the next step.</span></span>


## <a name="step-2-create-a-driver-package"></a><span data-ttu-id="5189d-117">2단계: 드라이버 패키지 만들기</span><span class="sxs-lookup"><span data-stu-id="5189d-117">Step 2: Create a driver package</span></span>
___

<span data-ttu-id="5189d-118">드라이버 패키지는 드라이버의 Inf 파일에 대 한 참조 (InfSource)를 포함 하 고 또한 Inf 파일에서 참조 하는 모든 파일을 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="5189d-118">The Driver package contains the references(InfSource)to the Inf file for the driver and also lists all the files referenced in the Inf file.</span></span> <span data-ttu-id="5189d-119">드라이버를 작성할 수 있습니다. wm.xml를 사용 하 여 [새로 만들기-IoTDriverPackage](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools/IoTCoreImaging/Docs/Add-IoTDriverPackage.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="5189d-119">You can author the driver .wm.xml using [New-IoTDriverPackage](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools/IoTCoreImaging/Docs/Add-IoTDriverPackage.md).</span></span>

<span data-ttu-id="5189d-120">[새 IoTInf2Cab](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools/IoTCoreImaging/Docs/New-IoTInf2Cab.md) 패키지 xml 파일을 만들고 cab 파일을 직접 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="5189d-120">[New-IoTInf2Cab](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools/IoTCoreImaging/Docs/New-IoTInf2Cab.md) creates the package xml file and also builds the cab file directly.</span></span>

> [!NOTE]
> <span data-ttu-id="5189d-121">Windows IoT Core 지원 [범용 INF 및 범용 드라이버](https://docs.microsoft.com/en-us/windows-hardware/drivers/develop/getting-started-with-universal-drivers)합니다.</span><span class="sxs-lookup"><span data-stu-id="5189d-121">Windows IoT Core only supports [Universal INF and Universal Drivers](https://docs.microsoft.com/en-us/windows-hardware/drivers/develop/getting-started-with-universal-drivers).</span></span>


<span data-ttu-id="5189d-122">참고 항목: [샘플 드라이버 패키지](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/BSP/CustomRpi2/Packages/CustomRPi2.GPIO)</span><span class="sxs-lookup"><span data-stu-id="5189d-122">See also: [Sample Driver Package](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/BSP/CustomRpi2/Packages/CustomRPi2.GPIO)</span></span> 

## <a name="step-3-install-on-device"></a><span data-ttu-id="5189d-123">3단계: 장치 설치</span><span class="sxs-lookup"><span data-stu-id="5189d-123">Step 3: Install on device</span></span>
___

* <span data-ttu-id="5189d-124">장치에 연결 ([SSH를 사용 하 여](../connect-your-device/ssh.md) 하거나 [Powershell을 사용 하 여](../connect-your-device/powershell.md))</span><span class="sxs-lookup"><span data-stu-id="5189d-124">Connect to the device ([using SSH](../connect-your-device/ssh.md) or [using Powershell](../connect-your-device/powershell.md))</span></span>
* <span data-ttu-id="5189d-125">복사를 <filename>.cab 파일 디렉터리로 장치로 가정해 C:\OemInstall</span><span class="sxs-lookup"><span data-stu-id="5189d-125">Copy the <filename>.cab file to the device to a directory say C:\OemInstall</span></span>
* <span data-ttu-id="5189d-126">사용 하 여 패키지 준비 시작 `applyupdate -stage C:\OemInstall\<filename>.cab`합니다.</span><span class="sxs-lookup"><span data-stu-id="5189d-126">Initiate staging of the package using `applyupdate -stage C:\OemInstall\<filename>.cab`.</span></span> <span data-ttu-id="5189d-127">여러 패키지를 설치 해야 하는 경우이 단계는 각 패키지에 대해 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="5189d-127">Note that this step is be repeated for each package, when you have multiple packages to install.</span></span>
* <span data-ttu-id="5189d-128">사용 하 여 패키지를 커밋 `applyupdate -commit`합니다.</span><span class="sxs-lookup"><span data-stu-id="5189d-128">Commit the packages using `applyupdate -commit`.</span></span>

<span data-ttu-id="5189d-129">장치가는 업데이트 패키지를 설치 하려면 OS (보여 주는 gears)으로 다시 부팅 됩니다 하 고 기본 OS를 다시 부팅 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5189d-129">The device will reboot into the update OS (showing gears) to install the packages and will reboot again to main OS.</span></span> <span data-ttu-id="5189d-130">이 프로세스는 몇 분 정도 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5189d-130">This process can take a few minutes.</span></span>

## <a name="step-4-check-status-of-driver"></a><span data-ttu-id="5189d-131">4단계: 드라이버의 상태를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="5189d-131">Step 4: Check status of driver</span></span>
___

* <span data-ttu-id="5189d-132">시작 된 [Powershell](../connect-your-device/PowerShell.md)</span><span class="sxs-lookup"><span data-stu-id="5189d-132">Launch the [Powershell](../connect-your-device/PowerShell.md)</span></span>
* <span data-ttu-id="5189d-133">다음 Powershell commandlet을 사용 하 여 설치 된 드라이버의 상태를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5189d-133">You can get the status of the installed drivers using the following Powershell commandlets</span></span>

    * [<span data-ttu-id="5189d-134">Get-PnpDevice</span><span class="sxs-lookup"><span data-stu-id="5189d-134">Get-PnpDevice</span></span>](https://docs.microsoft.com/powershell/module/pnpdevice/get-pnpdevice?view=win10-ps)
    * [<span data-ttu-id="5189d-135">Get-PnpDeviceProperty</span><span class="sxs-lookup"><span data-stu-id="5189d-135">Get-PnpDeviceProperty</span></span>](https://docs.microsoft.com/powershell/module/pnpdevice/get-pnpdeviceproperty?view=win10-ps)
    
