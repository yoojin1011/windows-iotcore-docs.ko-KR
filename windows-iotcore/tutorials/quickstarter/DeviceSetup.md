---
title: 디바이스 설정
ms.date: 04/10/2018
ms.topic: article
description: SD 카드를 사용하여 Windows 10 IoT Core로 디바이스를 설정하는 방법을 알아보세요.
keywords: Windows 10 IoT Core, SD 카드, Windows 10 IoT Core 대시보드
ms.custom: RS5
ms.openlocfilehash: 7575889b94cf7a69550c5c4128ab5ff8a82dde9c
ms.sourcegitcommit: ea060254f9c4c25afcd0245c897b9e1425321859
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75721838"
---
# <a name="setting-up-your-device"></a><span data-ttu-id="cf2c9-104">디바이스 설정</span><span class="sxs-lookup"><span data-stu-id="cf2c9-104">Setting up your device</span></span>

<span data-ttu-id="cf2c9-105">아래에서는 Windows 10 IoT Core로 디바이스를 플래시하는 네 가지 방법을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-105">Below you'll find four different ways to flash your device with Windows 10 IoT Core.</span></span> <span data-ttu-id="cf2c9-106">[프로토타입 제작에 추천하는 보드 목록](PrototypeBoards.md)에 포함된 차트에 따라 적절한 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-106">Based on the chart included in the [list of suggested boards for prototyping](PrototypeBoards.md), follow the appropriate directions.</span></span> <span data-ttu-id="cf2c9-107">오른쪽 열을 사용하여 다양한 플래시 방법을 탐색하세요.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-107">Use the right column to navigate between these different methods of flashing.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cf2c9-108">상용화에 제조사 이미지를 사용하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-108">Do not use maker images for commercialization.</span></span> <span data-ttu-id="cf2c9-109">디바이스를 상용화하려는 경우 최적의 보안을 위해 사용자 지정 FFU를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-109">If you are commercializing a device, you must use a custom FFU for optimal security.</span></span> <span data-ttu-id="cf2c9-110">[여기](https://docs.microsoft.com/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)에서 자세한 내용을 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-110">Learn more [here](https://docs.microsoft.com/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cf2c9-111">"이 디스크 포맷" 팝업이 나타나면 디스크를 포맷하지 _마세요_.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-111">When the "format this disk" pop up comes up, do _not_ format the disk.</span></span> <span data-ttu-id="cf2c9-112">이 이슈를 수정하지 위한 작업을 진행 중입니다.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-112">We are working on a fix for this issue.</span></span>

## <a name="using-the-iot-dashboard-raspberry-pi-minnowboard-nxp"></a><span data-ttu-id="cf2c9-113">IoT 대시보드(Raspberry Pi, MinnowBoard, NXP) 사용</span><span class="sxs-lookup"><span data-stu-id="cf2c9-113">Using the IoT Dashboard (Raspberry Pi, MinnowBoard, NXP)</span></span>

> [!Video https://www.youtube.com/embed/JPRUbGIyODY]


> [!IMPORTANT]
> <span data-ttu-id="cf2c9-114">MinnowBoard Turbot의 최신 64비트 펌웨어는 [MinnowBoard 웹 사이트](https://minnowboard.org/tutorials/updating-the-firmware)에서 찾을 수 있습니다(MinnowBoard 사이트의 지침에서 4단계 생략).</span><span class="sxs-lookup"><span data-stu-id="cf2c9-114">The latest 64-bit firmware for MinnowBoard Turbot can be found on the [MinnowBoard website](https://minnowboard.org/tutorials/updating-the-firmware) (skip step 4 on the MinnowBoard site's instructions).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cf2c9-115">NXP는 사용자 지정 이미지만 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-115">NXP only supports custom images.</span></span> <span data-ttu-id="cf2c9-116">사용자 지정 이미지를 플래시하려는 경우 OS 빌드 드롭다운 목록에서 "사용자 지정"을 선택하고, [여기](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image)의 지침에 따라 기본 이미지를 만들고, 아래의 나머지 지침에 따라 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-116">If you're looking to flash a custom image, select "Custom" from the OS Build dropdown, follow the instructions [here](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image) to create a basic image, and follow the rest of the instructions below to finish.</span></span>

> [!NOTE]
> <span data-ttu-id="cf2c9-117">대시보드는 Raspberry Pi 3B+를 설정하는 데 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-117">Dashboard cannot be used used to setup the Raspberry Pi 3B+.</span></span> <span data-ttu-id="cf2c9-118">3B+ 디바이스가 있는 경우 [3B+ 기술 미리 보기](https://www.microsoft.com/software-download/windowsiot)를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-118">If you have a 3B+ device, you must use the [3B+ technical preview](https://www.microsoft.com/software-download/windowsiot).</span></span> <span data-ttu-id="cf2c9-119">기술 미리 보기의 [알려진 제한 사항](https://docs.microsoft.com/windows/iot-core/troubleshooting)을 확인하여 개발 작업에 적합한지 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-119">Please view the [known limitations](https://docs.microsoft.com/windows/iot-core/troubleshooting) of the technical preview to determine if this is suitable for your development.</span></span>

> [!TIP]
> <span data-ttu-id="cf2c9-120">안정성을 높이고 디바이스를 외부 디스플레이에 연결하여 기본 애플리케이션이 부팅되는 것을 볼 수 있도록 SanDisk SD 카드 같은 고성능 SD 카드를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-120">We recommend using a high-performance SD card, such as a SanDisk SD card, for increased stability as well as plugging your device into an external display to see the default application booting up.</span></span>


1. <span data-ttu-id="cf2c9-121">[여기](https://docs.microsoft.com/windows/iot-core/downloads)서 Windows 10 IoT Core 대시보드를 다운로드하세요.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-121">Download the Windows 10 IoT Core Dashboard [here](https://docs.microsoft.com/windows/iot-core/downloads).</span></span>
2. <span data-ttu-id="cf2c9-122">다운로드한 후에는 대시보드를 열고, _새 디바이스 설치_를 클릭하고, 컴퓨터에 SD 카드를 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-122">Once downloaded, open the Dashboard and click on _set up a new device_ and insert a SD card into your computer.</span></span>
3. <span data-ttu-id="cf2c9-123">표시된 대로 모든 필드를 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-123">Fill out all of the fields as indicated.</span></span>
4. <span data-ttu-id="cf2c9-124">소프트웨어 사용 조건에 동의하고 _다운로드 및 설치_를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-124">Accept the software license terms and click _Download and install_.</span></span> <span data-ttu-id="cf2c9-125">Windows 10 IoT Core가 SD 카드에 플래시되는 것을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-125">You'll see that Windows 10 IoT Core is now flashing your SD card.</span></span>


![대시보드 스크린샷](../../media/DeviceSetup/Dashboard-Screenshot.jpg)
 

## <a name="using-the-iot-dashboard-dragonboard-410c"></a><span data-ttu-id="cf2c9-127">IoT 대시보드(DragonBoard 410c) 사용</span><span class="sxs-lookup"><span data-stu-id="cf2c9-127">Using the IoT Dashboard (DragonBoard 410c)</span></span>

> [!Video https://www.youtube.com/embed/iPm57hGq-Q8]

> [!TIP]
> <span data-ttu-id="cf2c9-128">기본 애플리케이션이 부팅되는 것을 보려면 디바이스를 외부 디스플레이에 연결하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-128">We recommend plugging your device into an external display to see the default application booting up.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cf2c9-129">사용자 지정 이미지를 플래시하려는 경우 OS 빌드 드롭다운 목록에서 "사용자 지정"을 선택하고, [여기](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image)의 지침에 따라 기본 이미지를 만들고, 아래의 나머지 지침에 따라 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-129">If you're looking to flash a custom image, select "Custom" from the OS Build dropdown, follow the instructions [here](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image) to create a basic image, and follow the rest of the instructions below to finish.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cf2c9-130">새 Dragonboard를 사용하는 경우 Android가 설치된 상태로 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-130">When you're working with a new Dragonboard, it comes with Android installed.</span></span> <span data-ttu-id="cf2c9-131">eMMC 플래시 메서드를 사용하여 디바이스의 데이터를 지우고 다시 로드해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-131">You will need to wipe and load the device using the eMMC flashing method.</span></span>

> [!NOTE]
> <span data-ttu-id="cf2c9-132">DragonBoard에서 오디오 관련 이슈가 발생하는 경우 [여기서](https://developer.qualcomm.com/download/db410c/stereo-connector-and-audio-routing-application-note.pdf) Qualcomm의 설명서를 읽어보시기를 권장합니다.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-132">If you're running into any audio-related issues with your DragonBoard, we advise that you read through Qualcomm's manual [here](https://developer.qualcomm.com/download/db410c/stereo-connector-and-audio-routing-application-note.pdf).</span></span> 

1. <span data-ttu-id="cf2c9-133">[여기](https://docs.microsoft.com/windows/iot-core/downloads)서 Windows 10 IoT Core 대시보드를 다운로드하세요.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-133">Download the Windows 10 IoT Core Dashboard [here](https://docs.microsoft.com/windows/iot-core/downloads).</span></span>
2. <span data-ttu-id="cf2c9-134">다운로드한 후 대시보드를 열고 "Qualcomm DragonBoard 410c"를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-134">Once downloaded, open the Dashboard and select "Qualcomm DragonBoard 410c".</span></span> <span data-ttu-id="cf2c9-135">그런 다음, _Windows 참가자로 로그인_합니다.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-135">Then _sign in as a Windows Insider_.</span></span> <span data-ttu-id="cf2c9-136">DragonBoard 410c를 플래시하려면 참가자로 로그인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-136">You need to be signed in as an insider in order to flash DragonBoard 410c.</span></span> 
3. <span data-ttu-id="cf2c9-137">microUSB 케이블을 사용하여 Qualcomm 보드를 개발자 머신에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-137">Connect the Qualcomm board to the developer machine using a microUSB cable.</span></span>
4. <span data-ttu-id="cf2c9-138">볼륨 크게(+) 단추를 누른 상태에서 12V(>1A) 전원 공급 장치를 사용하여 Dragonboard를 켭니다.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-138">Power on your Dragonboard using a 12V (>1A) power supply while holding down the volume up (+) button.</span></span> <span data-ttu-id="cf2c9-139">디바이스를 디스플레이에 연결하면 망치, 번개 및 톱니 이미지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-139">The device - when connected to a display - should show the image of a hammer, a lightning bolt, and a cog.</span></span> 
5. <span data-ttu-id="cf2c9-140">이제 디바이스가 대시보드에 아래와 같이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-140">The device should now be visible on the Dashboard as shown below.</span></span> <span data-ttu-id="cf2c9-141">적절한 디바이스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-141">Select the appropriate device.</span></span>
6. <span data-ttu-id="cf2c9-142">소프트웨어 사용 조건에 동의하고 _다운로드 및 설치_를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-142">Accept the software license terms and click _Download and install_.</span></span> <span data-ttu-id="cf2c9-143">Windows 10 IoT Core가 디바이스에 플래시되는 것을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-143">You'll see that Windows 10 IoT Core is now flashing onto your device.</span></span>


![플래시 모드의 DragonBoard](../../media/DeviceSetup/db4.png)


## <a name="flashing-with-emmc-for-dragonboard-410c-other-qualcomm-devices"></a><span data-ttu-id="cf2c9-145">eMMC로 플래시(DragonBoard 410c의 경우 다른 Qualcomm 디바이스)</span><span class="sxs-lookup"><span data-stu-id="cf2c9-145">Flashing with eMMC (for DragonBoard 410c, other Qualcomm devices)</span></span>

1. <span data-ttu-id="cf2c9-146">[x86](https://developer.qualcomm.com/download/db410c/windows-10-iot-update-tool-dragonboard-410c-x86.zip) 또는 [x64](https://developer.qualcomm.com/download/db410c/windows-10-iot-update-tool-dragonboard-410c-x64.zip) 머신에 맞는 DragonBoard 업데이트 도구를 다운로드하여 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-146">Download and install the DragonBoard Update Tool for your [x86](https://developer.qualcomm.com/download/db410c/windows-10-iot-update-tool-dragonboard-410c-x86.zip) or [x64](https://developer.qualcomm.com/download/db410c/windows-10-iot-update-tool-dragonboard-410c-x64.zip) machine.</span></span>
2. <span data-ttu-id="cf2c9-147">[Windows 10 IoT Core DragonBoard FFU](https://developer.microsoft.com/windows/iot/Downloads)를 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-147">Download the [Windows 10 IoT Core DragonBoard FFU](https://developer.microsoft.com/windows/iot/Downloads).</span></span>
3. <span data-ttu-id="cf2c9-148">다운로드한 ISO 파일을 두 번 클릭하고 탑재된 가상 CD 드라이브를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-148">Double-click on the downloaded ISO file and locate the mounted Virtual CD-drive.</span></span> <span data-ttu-id="cf2c9-149">이 드라이브에 설치 관리자 파일(.msi)이 포함되어 있습니다. 이 파일을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-149">This drive will contain an installer file (.msi); double-click on it.</span></span> <span data-ttu-id="cf2c9-150">그러면 PC의  `C:\Program Files (x86)\Microsoft IoT\FFU\` 아래에 새 디렉터리가 생성되고 "flash.ffu" 이미지 파일이 보입니다.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-150">This creates a new directory on your PC under `C:\Program Files (x86)\Microsoft IoT\FFU\` in which you should see an image file, "flash.ffu".</span></span>
4. <span data-ttu-id="cf2c9-151">아래와 같이 보드의 첫 번째 스위치를 USB 부팅으로 설정하여 DragonBoard를 다운로드 모드로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-151">Ensure your DragonBoard is in download mode by setting the first boot switch on the board to USB Boot, as shown below.</span></span> <span data-ttu-id="cf2c9-152">그런 다음, microUSB 케이블을 통해 DragonBoard를 호스트 PC에 연결하고, DragonBoard를 12V(>1A) 전원 공급 장치에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-152">Then, connect DragonBoard the host PC via a microUSB cable, then plug in the DragonBoard to a 12V (> 1A) power supply.</span></span>
5. <span data-ttu-id="cf2c9-153">녹색 원을 사용하여 DragonBoard가 PC에 연결되어 있는지 탐지하는 DragonBoard 업데이트 도구를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-153">Start the DragonBoard Update Tool, which should detect that the DragonBoard is connect to your PC with a green circle.</span></span> <span data-ttu-id="cf2c9-154">다운로드한 DragonBoard의 FFU를 찾은 다음, _프로그램_ 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-154">"Browse" to the DragonBoard's FFU that you downloaded, then click the _Program_ button.</span></span>
6. <span data-ttu-id="cf2c9-155">"찾아보기"를 다시 클릭하고 5단계에서 생성된 "rawprogram0.xml"을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-155">Click "Browse" again and select "rawprogram0.xml" that was generated in step 5.</span></span> <span data-ttu-id="cf2c9-156">그런 다음, "프로그램" 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-156">Then click the "Program" button.</span></span>
7. <span data-ttu-id="cf2c9-157">다운로드가 완료되면 보드에서 전원 공급 장치와 microUSB 케이블을 분리하고 USB 부팅 스위치를 다시 _OFF_로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-157">Once the download is complete, disconnect the power supply and microUSB cable from the board and toggle the USB Boot switch back to _OFF_.</span></span> <span data-ttu-id="cf2c9-158">HDMI 디스플레이, 마우스 및 키보드를 DragonBoard에 연결하고 전원 공급 장치를 다시 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-158">Connect a HDMI display, a mouse, and a keyboard to the DragonBoard and re-connect the power supply.</span></span> <span data-ttu-id="cf2c9-159">몇 분 후 Windows 10 IoT Core 기본 애플리케이션이 보입니다.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-159">After a few minutes, you should see the Windows 10 IoT Core default application.</span></span> 

![다운로드 모드인 DragonBoard](../../media/DeviceSetup/db1.png)

> [!NOTE]
> <span data-ttu-id="cf2c9-161">BIOS 설정을 다시 입력하고, USB 드라이브 대신 하드 드라이브에서 로드하도록 부팅 드라이브 순서를 전환하여 디바이스가 eMMC 메모리에서 부팅되도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-161">Make sure the device is now booting from the eMMC memory by entering the BIOS setup again and switching the Boot Drive order to load from the Hard Drive instead of from the USB Drive.</span></span>


## <a name="flashing-with-emmc-for-up-squared-other-intel-devices"></a><span data-ttu-id="cf2c9-162">eMMC를 사용하여 플래시(Up Squared의 경우 다른 Intel 디바이스)</span><span class="sxs-lookup"><span data-stu-id="cf2c9-162">Flashing with eMMC (for Up Squared, other Intel devices)</span></span>

#### <a name="download-and-install-tools"></a><span data-ttu-id="cf2c9-163">도구 다운로드 및 설치</span><span class="sxs-lookup"><span data-stu-id="cf2c9-163">Download and Install Tools</span></span>

1. <span data-ttu-id="cf2c9-164">머신에서 실행 중인 Windows 10 버전과 관련된 [Windows 평가 및 배포 키트](https://docs.microsoft.com/windows-hardware/get-started/adk-install)(Windows ADK)를 다운로드하여 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-164">Download and install the [Windows Assessment and Deployment Kit](https://docs.microsoft.com/windows-hardware/get-started/adk-install)  (Windows ADK) with the correlating version of Windows 10 you're running on your machine.</span></span>
2. <span data-ttu-id="cf2c9-165">[ADK용 Windows PE 추가 기능](https://go.microsoft.com/fwlink/?linkid=2087112)을 다운로드하여 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-165">Download and install the [Windows PE add-on for the ADK](https://go.microsoft.com/fwlink/?linkid=2087112).</span></span>

#### <a name="create-a-usb-bootable-windows-pehttpsdocsmicrosoftcomwindows-hardwaremanufacturedesktopwinpe-intro-image"></a><span data-ttu-id="cf2c9-166">USB 부팅 가능 [Windows PE](https://docs.microsoft.com/windows-hardware/manufacture/desktop/winpe-intro) 이미지 만들기</span><span class="sxs-lookup"><span data-stu-id="cf2c9-166">Create a USB-bootable [Windows PE](https://docs.microsoft.com/windows-hardware/manufacture/desktop/winpe-intro) image</span></span>

3. <span data-ttu-id="cf2c9-167">USB 드라이브를 머신에 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-167">Insert a USB drive into your machine.</span></span>
4. <span data-ttu-id="cf2c9-168">관리자로 배포 및 이미지 도구 환경을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-168">Start the Deployment and Imaging Tools Environment as an administrator.</span></span> <span data-ttu-id="cf2c9-169">기본 설치 경로는 `C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Deployment Tools\DandISetEnv.bat`입니다.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-169">The default installation path is `C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Deployment Tools\DandISetEnv.bat`.</span></span>
5. <span data-ttu-id="cf2c9-170">[`Copype`](https://docs.microsoft.com/windows-hardware/manufacture/desktop/copype-command-line-options)를 사용하여 Windows PE 파일의 작업 복사본을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-170">Use [`Copype`](https://docs.microsoft.com/windows-hardware/manufacture/desktop/copype-command-line-options) to create a working copy of the Windows PE files.</span></span> <span data-ttu-id="cf2c9-171">x86, amd64 또는 ARM 아키텍처 중 하나를 지정해야 합니다(예: `Copype amd64 C:\WINPE_amd64`).</span><span class="sxs-lookup"><span data-stu-id="cf2c9-171">You must specify either x86, amd64 or ARM architectures (e.g. `Copype amd64 C:\WINPE_amd64`)</span></span>
6. <span data-ttu-id="cf2c9-172">[`MakeWinPEMedia`](https://docs.microsoft.com/windows-hardware/manufacture/desktop/makewinpemedia-command-line-options)를 사용하여 Windows PE를 USB 플래시 드라이브에 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-172">Install Windows PE to the USB flash drive using [`MakeWinPEMedia`](https://docs.microsoft.com/windows-hardware/manufacture/desktop/makewinpemedia-command-line-options).</span></span> <span data-ttu-id="cf2c9-173">대상 USB 드라이브를 지정해야 합니다(예: `MakeWinPEMedia /UFD C:\WinPE_amd64 P:`).</span><span class="sxs-lookup"><span data-stu-id="cf2c9-173">You must specify the destination USB drive (e.g. `MakeWinPEMedia /UFD C:\WinPE_amd64 P:`).</span></span>
7. <span data-ttu-id="cf2c9-174">다운로드한 ISO 파일을 두 번 클릭하고 탑재된 가상 CD 드라이브를 찾아 [Windows 10 IoT Core 이미지](https://downloads.up-community.org/?post_type=wpdmpro&p=204&preview=true)를 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-174">Download the [Windows 10 IoT Core image](https://downloads.up-community.org/?post_type=wpdmpro&p=204&preview=true) by double-clicking on the downloaded ISO file and locating the mounted Virtual CD-drive.</span></span>
8. <span data-ttu-id="cf2c9-175">이 드라이브에 포함된 설치 관리자 파일(.msi)을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-175">This drive will contain an install file (.msi); double click it.</span></span> <span data-ttu-id="cf2c9-176">그러면 PC의 `C:\Program Files (x86)\Microsoft IoT\FFU\` 아래에 새 디렉터리가 생성되고 `flash.ffu` 이미지 파일이 보입니다.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-176">This will create a new directory on your PC under `C:\Program Files (x86)\Microsoft IoT\FFU\` in which you should see an image file `flash.ffu`.</span></span>
9. <span data-ttu-id="cf2c9-177">디바이스의 FFU와 함께 [eMMC 설치 관리자 스크립트](https://github.com/ms-iot/content/blob/develop/Resources/eMMCInstaller.zip)를 USB 디바이스의 루트 디렉터리에 다운로드하여 압축을 풀고 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-177">Download, unzip and copy the [eMMC Installer script](https://github.com/ms-iot/content/blob/develop/Resources/eMMCInstaller.zip) to the USB device's root directory, along with the device's FFU.</span></span>
10. <span data-ttu-id="cf2c9-178">USB 드라이브, 마우스 및 키보드를 USB 허브에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-178">Connect the USB drive, mouse, and keyboard to the USB hub.</span></span> <span data-ttu-id="cf2c9-179">HDMI 디스플레이를 디바이스에 연결하고, 디바이스를 USB 허브에 연결하고, 전원 코드를 디바이스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-179">Attach the HDMI display to your device, the device to the USB hub, and the power cord to the device.</span></span>
11. <span data-ttu-id="cf2c9-180">필요한 경우 디바이스의 BIOS 설정으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-180">If necessary, go to the BIOS setup of the device.</span></span> <span data-ttu-id="cf2c9-181">운영 체제로 *Windows*를 선택하고, USB 드라이브에서 부팅하도록 디바이스를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-181">Select *Windows* as the Operating system and set the device to boot from your uSB drive.</span></span> <span data-ttu-id="cf2c9-182">시스템이 다시 부팅되면 WinPE 명령 프롬프트가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-182">When the system reboots, you will see the WinPE command prompt.</span></span> <span data-ttu-id="cf2c9-183">WinPE 프롬프트를 USB 드라이브로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-183">Switch the WinPE prompt to the USB Drive.</span></span> <span data-ttu-id="cf2c9-184">일반적으로 C: 또는 D:이지만 다른 드라이버 문자를 사용해야 하는 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-184">This is usually C: or D: but you may need to try other driver letters.</span></span>
12. <span data-ttu-id="cf2c9-185">디바이스의 eMMC 메모리에 Windows 10 IoT Core 이미지를 설치하는 eMMC 설치 관리자 스크립트를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-185">Run the eMMC Installer script, which will install the Windows 10 IoT Core image to the device's eMMC memory.</span></span> <span data-ttu-id="cf2c9-186">스크립트가 완료되면 아무 키를 눌러 `wpeutil reboot`를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-186">When it completes, press any key and run `wpeutil reboot`.</span></span> <span data-ttu-id="cf2c9-187">시스템이 Windows 10 IoT Core로 부팅되고, 구성 프로세스를 시작하고, 기본 애플리케이션을 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-187">The system should boot into Windows 10 IoT Core, start the configuration process, and load the default application.</span></span>

> [!NOTE]
> <span data-ttu-id="cf2c9-188">BIOS 설정을 다시 입력하고, USB 드라이브 대신 하드 드라이브에서 로드하도록 부팅 드라이브 순서를 전환하여 디바이스가 eMMC 메모리에서 부팅되도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-188">Make sure the device is now booting from the eMMC memory by entering the BIOS setup again and switching the Boot Drive order to load from the Hard Drive instead of from the USB Drive.</span></span>


## <a name="connecting-to-a-network"></a><span data-ttu-id="cf2c9-189">네트워크에 연결</span><span class="sxs-lookup"><span data-stu-id="cf2c9-189">Connecting to a network</span></span>

#### <a name="wired-connection"></a><span data-ttu-id="cf2c9-190">유선 연결</span><span class="sxs-lookup"><span data-stu-id="cf2c9-190">Wired connection</span></span>
<span data-ttu-id="cf2c9-191">디바이스에 유선 연결을 지원하는 이더넷 포트 또는 USB 이더넷 어댑터가 있는 경우 이더넷 케이블을 연결하여 네트워크에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-191">If your device comes with an Ethernet port or USB Ethernet adapter support to enable a wired connection, attach an Ethernet cable to connect it to your network.</span></span>

#### <a name="wireless-connection"></a><span data-ttu-id="cf2c9-192">무선 연결</span><span class="sxs-lookup"><span data-stu-id="cf2c9-192">Wireless connection</span></span>
<span data-ttu-id="cf2c9-193">디바이스에서 Wi-Fi 연결이 지원되고 디바이스를 디스플레이에 연결한 경우 다음 단계를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-193">If your device supports Wi-Fi connectivity and you've connected a display to it, you'll need to:</span></span>

1. <span data-ttu-id="cf2c9-194">기본 애플리케이션으로 이동하여 시계 옆에 있는 설정 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-194">Go into your default application and click the settings button next to the clock.</span></span>
2. <span data-ttu-id="cf2c9-195">설정 페이지에서 _네트워크 및 Wi-Fi_를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-195">On the settings page, select _Network and Wi-Fi_.</span></span>
3. <span data-ttu-id="cf2c9-196">디바이스가 무선 네트워크 검색을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-196">Your device will begin scanning for wireless networks.</span></span>
4. <span data-ttu-id="cf2c9-197">이 목록에 네트워크가 나타나면 네트워크를 선택하고 _연결_을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-197">Once your network appears in this list, select it and click _Connect_.</span></span>

<span data-ttu-id="cf2c9-198">디스플레이를 연결하지 않았으며 Wi-Fi를 통해 연결하려는 경우에는 다음 단계를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-198">If you haven't connected a display and would like to connect via Wi-Fi, you'll need to:</span></span>

1. <span data-ttu-id="cf2c9-199">IoT 대시보드로 이동하여 _내 디바이스_를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-199">Go to the IoT Dashboard and click on _My Devices_.</span></span>
2. <span data-ttu-id="cf2c9-200">목록에서 구성되지 않은 보드를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-200">Find your unconfigured board from the list.</span></span> <span data-ttu-id="cf2c9-201">보드 이름은 "AJ_"로 시작합니다(예: AJ_58EA6C68).</span><span class="sxs-lookup"><span data-stu-id="cf2c9-201">Its name will begin with "AJ_"... (e.g. AJ_58EA6C68).</span></span> <span data-ttu-id="cf2c9-202">몇 분이 지나도 보드가 보이지 않으면 보드를 다시 부팅합니다.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-202">If you don't see your board appear after a few minutes, try rebooting your board.</span></span>
3. <span data-ttu-id="cf2c9-203">_디바이스 구성_을 클릭하고 네트워크 자격 증명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-203">Click on _Configure Device_ and enter your network credentials.</span></span> <span data-ttu-id="cf2c9-204">그러면 보드가 네트워크에 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-204">This will connect your board to the network.</span></span>

> [!NOTE]
> <span data-ttu-id="cf2c9-205">다른 네트워크를 찾으려면 컴퓨터의 Wifi를 켜야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-205">Wifi on your computer will need to be turned on in order to find other networks.</span></span>

## <a name="connecting-to-windows-device-portal"></a><span data-ttu-id="cf2c9-206">Windows 디바이스 포털에 연결</span><span class="sxs-lookup"><span data-stu-id="cf2c9-206">Connecting to Windows Device Portal</span></span>

<span data-ttu-id="cf2c9-207">[Windows 디바이스 포털](../../manage-your-device/DevicePortal.md)을 사용하여 웹 브라우저를 통해 디바이스를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-207">Use the [Windows Device Portal](../../manage-your-device/DevicePortal.md) to connect your device through a web browser.</span></span> <span data-ttu-id="cf2c9-208">디바이스 포털에서는 중요한 구성과 디바이스 관리 기능을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf2c9-208">The device portal makes valuable configuration and device management capabilities available.</span></span> 

