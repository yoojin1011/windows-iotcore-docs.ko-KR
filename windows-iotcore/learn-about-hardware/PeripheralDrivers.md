---
title: USB 주변 장치 드라이버 설치
ms.date: 08/28/2017
ms.topic: article
description: 드라이버 패키지를 만들고 장치에 타사 드라이버를 설치 하는 방법에 대해 알아봅니다.
keywords: windows iot, USB 드라이버, 주변 장치, USB
ms.openlocfilehash: 96e234c943771c336a9f5d7c0b7568cb11c0f6ce
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918064"
---
# <a name="install-usb-peripheral-drivers"></a><span data-ttu-id="ab452-104">USB 주변 장치 드라이버 설치</span><span class="sxs-lookup"><span data-stu-id="ab452-104">Install USB peripheral drivers</span></span>
<span data-ttu-id="ab452-105">USB 모바일 광대역 모뎀, 프린터, 스캐너 등의 주변 장치에 대 한 타사 드라이버 (usb)를 추가 하려면 다음 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab452-105">Follow the steps below to add third-party drivers (usb) for peripheral devices such as USB Mobile broadband modems, printers, scanners etc.</span></span> 

## <a name="step-1-get-drivers-from-pc"></a><span data-ttu-id="ab452-106">1 단계: PC에서 드라이버 가져오기</span><span class="sxs-lookup"><span data-stu-id="ab452-106">Step 1: Get Drivers from PC</span></span>
___
<span data-ttu-id="ab452-107">이 단계는 PC에서 x86 버전의 드라이버를 가져오는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="ab452-107">The Step is to get the x86 version of the drivers from PC.</span></span> <span data-ttu-id="ab452-108">ARM의 경우 sys/inf 파일을 가져오려면 주변 장치의 공급 업체에 문의 하세요.</span><span class="sxs-lookup"><span data-stu-id="ab452-108">For ARM, please contact the supplier of the peripheral to get the sys/inf files.</span></span>


1. <span data-ttu-id="ab452-109">Windows PC에 장치 연결</span><span class="sxs-lookup"><span data-stu-id="ab452-109">Connect the device to the windows PC</span></span>

2. <span data-ttu-id="ab452-110">PC에 장치에 대 한 드라이버를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab452-110">Install the driver for the device on the PC</span></span>

3. <span data-ttu-id="ab452-111">Device Manager로 이동 하 고이 장치 (유니버설 직렬 버스 컨트롤러 아래에 나열 됨)를 선택한 후 마우스 오른쪽 단추를 클릭 하 고 속성을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab452-111">Go to Device Manager, select this device (listed under Universal Serial Bus controllers) and right click and select Properties.</span></span>

4. <span data-ttu-id="ab452-112">속성 창에서 드라이버 탭으로 이동 하 여 드라이버 세부 정보를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab452-112">Go to Driver tab in the Properties window, and click on Driver Details.</span></span> <span data-ttu-id="ab452-113">여기에는 sys 파일이 나열 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab452-113">Note the sys files listed there.</span></span>

5. <span data-ttu-id="ab452-114">`C:\Windows\system32`에서 sys 파일을 복사 하 고 `C:\Windows\Inf`에서 관련 inf 파일도 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab452-114">Copy the sys files from `C:\Windows\system32` and also the related inf file from `C:\Windows\Inf`.</span></span> <span data-ttu-id="ab452-115">`.inf` 파일에서 sys 파일 참조를 searcing 하 여 inf 파일을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab452-115">You can find the inf file by searcing for the sys file reference in the `.inf` files.</span></span> <span data-ttu-id="ab452-116">Inf에 나열 된 추가 파일을 복사 해야 할 수 있습니다. 이러한 파일은 다음 단계에서 `inf2pkg.cmd`를 사용할 때 생성 되는 inf_filelist 파일에 나열 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ab452-116">You may need to copy additional files listed in the Inf and these will be listed in the inf_filelist.txt file created when using  `inf2pkg.cmd` in the next step.</span></span>


## <a name="step-2-create-a-driver-package"></a><span data-ttu-id="ab452-117">2 단계: 드라이버 패키지 만들기</span><span class="sxs-lookup"><span data-stu-id="ab452-117">Step 2: Create a driver package</span></span>
___

<span data-ttu-id="ab452-118">드라이버 패키지에는 드라이버의 Inf 파일에 대 한 참조 (InfSource)가 포함 되며, Inf 파일에서 참조 되는 모든 파일도 나열 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ab452-118">The Driver package contains the references(InfSource)to the Inf file for the driver and also lists all the files referenced in the Inf file.</span></span> <span data-ttu-id="ab452-119">[새 IoTDriverPackage 패키지](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools/IoTCoreImaging/Docs/Add-IoTDriverPackage.md)를 사용 하 여 드라이버를 제작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab452-119">You can author the driver .wm.xml using [New-IoTDriverPackage](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools/IoTCoreImaging/Docs/Add-IoTDriverPackage.md).</span></span>

<span data-ttu-id="ab452-120">[IoTInf2Cab](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools/IoTCoreImaging/Docs/New-IoTInf2Cab.md) 는 패키지 xml 파일을 만들고 cab 파일도 직접 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="ab452-120">[New-IoTInf2Cab](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools/IoTCoreImaging/Docs/New-IoTInf2Cab.md) creates the package xml file and also builds the cab file directly.</span></span>

> [!NOTE]
> <span data-ttu-id="ab452-121">Windows IoT Core는 [범용 INF 및 범용 드라이버만](https://docs.microsoft.com/en-us/windows-hardware/drivers/develop/getting-started-with-universal-drivers)지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab452-121">Windows IoT Core only supports [Universal INF and Universal Drivers](https://docs.microsoft.com/en-us/windows-hardware/drivers/develop/getting-started-with-universal-drivers).</span></span>


<span data-ttu-id="ab452-122">참고 항목: [샘플 드라이버 패키지](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/BSP/CustomRpi2/Packages/CustomRPi2.GPIO)</span><span class="sxs-lookup"><span data-stu-id="ab452-122">See also: [Sample Driver Package](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/BSP/CustomRpi2/Packages/CustomRPi2.GPIO)</span></span> 

## <a name="step-3-install-on-device"></a><span data-ttu-id="ab452-123">3 단계: 장치에 설치</span><span class="sxs-lookup"><span data-stu-id="ab452-123">Step 3: Install on device</span></span>
___

* <span data-ttu-id="ab452-124">장치에 연결 ([SSH 사용](../connect-your-device/ssh.md) 또는 [Powershell 사용](../connect-your-device/powershell.md))</span><span class="sxs-lookup"><span data-stu-id="ab452-124">Connect to the device ([using SSH](../connect-your-device/ssh.md) or [using Powershell](../connect-your-device/powershell.md))</span></span>
* <span data-ttu-id="ab452-125"><filename>.cab 파일을 장치에 복사 합니다 (예: C:\OemInstall).</span><span class="sxs-lookup"><span data-stu-id="ab452-125">Copy the <filename>.cab file to the device to a directory say C:\OemInstall</span></span>
* <span data-ttu-id="ab452-126">`applyupdate -stage C:\OemInstall\<filename>.cab`를 사용 하 여 패키지 준비를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab452-126">Initiate staging of the package using `applyupdate -stage C:\OemInstall\<filename>.cab`.</span></span> <span data-ttu-id="ab452-127">설치할 패키지가 여러 개 있는 경우이 단계는 각 패키지에 대해 반복 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ab452-127">Note that this step is be repeated for each package, when you have multiple packages to install.</span></span>
* <span data-ttu-id="ab452-128">`applyupdate -commit`를 사용 하 여 패키지를 커밋합니다.</span><span class="sxs-lookup"><span data-stu-id="ab452-128">Commit the packages using `applyupdate -commit`.</span></span>

<span data-ttu-id="ab452-129">장치를 업데이트 OS (기어 표시)로 다시 부팅 하 여 패키지를 설치 하 고 다시 주 OS로 다시 부팅 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab452-129">The device will reboot into the update OS (showing gears) to install the packages and will reboot again to main OS.</span></span> <span data-ttu-id="ab452-130">이 프로세스는 몇 분 정도 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab452-130">This process can take a few minutes.</span></span>

## <a name="step-4-check-status-of-driver"></a><span data-ttu-id="ab452-131">4 단계: 드라이버 상태 확인</span><span class="sxs-lookup"><span data-stu-id="ab452-131">Step 4: Check status of driver</span></span>
___

* <span data-ttu-id="ab452-132">[Powershell](../connect-your-device/PowerShell.md) 시작</span><span class="sxs-lookup"><span data-stu-id="ab452-132">Launch the [Powershell](../connect-your-device/PowerShell.md)</span></span>
* <span data-ttu-id="ab452-133">다음 Powershell commandlet을 사용 하 여 설치 된 드라이버의 상태를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab452-133">You can get the status of the installed drivers using the following Powershell commandlets</span></span>

    * [<span data-ttu-id="ab452-134">Pnp 장치</span><span class="sxs-lookup"><span data-stu-id="ab452-134">Get-PnpDevice</span></span>](https://docs.microsoft.com/powershell/module/pnpdevice/get-pnpdevice?view=win10-ps)
    * [<span data-ttu-id="ab452-135">PnpDeviceProperty</span><span class="sxs-lookup"><span data-stu-id="ab452-135">Get-PnpDeviceProperty</span></span>](https://docs.microsoft.com/powershell/module/pnpdevice/get-pnpdeviceproperty?view=win10-ps)
    
