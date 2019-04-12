---
title: 장치 설정
ms.author: saclayt
ms.date: 04/10/2018
ms.topic: article
description: SD 카드를 사용 하 여 Windows 10 IoT Core 사용 하 여 장치를 설정 하는 방법에 알아봅니다.
keywords: Windows 10 IoT Core, SD 카드, Windows 10 IoT Core 대시보드
ms.custom: RS5
ms.openlocfilehash: ece83dcc7f6961a4614db2ee0c6a1331b009bb47
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512405"
---
# <a name="setting-up-your-device"></a><span data-ttu-id="706ad-104">장치 설정</span><span class="sxs-lookup"><span data-stu-id="706ad-104">Setting up your device</span></span>

<span data-ttu-id="706ad-105">다음 네 가지 방법으로 Windows 10 IoT Core 사용 하 여 장치를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-105">Below you'll find four different ways to flash your device with Windows 10 IoT Core.</span></span> <span data-ttu-id="706ad-106">에 포함 된 차트를 기반으로 합니다 [프로토타입 개발에 대 한 제안 된 보드 목록을](PrototypeBoards.md), 적절 한 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-106">Based on the chart included in the [list of suggested boards for prototyping](PrototypeBoards.md), follow the appropriate directions.</span></span> <span data-ttu-id="706ad-107">깜박임의 이러한 다른 메서드 사이 이동 하려면 오른쪽 열을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-107">Use the right column to navigate between these different methods of flashing.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="706ad-108">상용화에 대 한 작성자 이미지를 사용 하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="706ad-108">Do not use maker images for commercialization.</span></span> <span data-ttu-id="706ad-109">장치 상용화 되, 사용자 지정 FFU 최적의 보안을 위해 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-109">If you are commercializing a device, you must use a custom FFU for optimal security.</span></span> <span data-ttu-id="706ad-110">[여기](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)에서 자세한 내용을 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="706ad-110">Learn more [here](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="706ad-111">"Format이 디스크" 팝업 최대 나타난 경우 수행 _되지_ 디스크를 포맷 합니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-111">When the "format this disk" pop up comes up, do _not_ format the disk.</span></span> <span data-ttu-id="706ad-112">이 문제에 대 한 수정 노력 합니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-112">We are working on a fix for this issue.</span></span>

## <a name="using-the-iot-dashboard-raspberry-pi-minnowboard-nxp"></a><span data-ttu-id="706ad-113">(Raspberry Pi, MinnowBoard NXP) IoT 대시보드 사용</span><span class="sxs-lookup"><span data-stu-id="706ad-113">Using the IoT Dashboard (Raspberry Pi, MinnowBoard, NXP)</span></span>

> [!Video https://www.youtube.com/embed/JPRUbGIyODY]


> [!IMPORTANT]
> <span data-ttu-id="706ad-114">최신 64 비트 펌웨어 MinnowBoard Turbot를에서 찾을 수 있습니다 합니다 [MinnowBoard 웹 사이트](https://minnowboard.org/tutorials/updating-the-firmware) (MinnowBoard 사이트의 지침에 4 단계를 건너뛰고).</span><span class="sxs-lookup"><span data-stu-id="706ad-114">The latest 64-bit firmware for MinnowBoard Turbot can be found on the [MinnowBoard website](https://minnowboard.org/tutorials/updating-the-firmware) (skip step 4 on the MinnowBoard site's instructions).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="706ad-115">NXP만 사용자 지정 이미지를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-115">NXP only supports custom images.</span></span> <span data-ttu-id="706ad-116">사용자 지정 이미지를 플래시를 "Custom" OS 빌드 드롭다운 목록에서 원하는 지침을 따르세요 [여기](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image) 기본 이미지를 만들고 완료 하려면 아래 지시를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-116">If you're looking to flash a custom image, select "Custom" from the OS Build dropdown, follow the instructions [here](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image) to create a basic image, and follow the rest of the instructions below to finish.</span></span>

> [!NOTE]
> <span data-ttu-id="706ad-117">대시보드는 Raspberry Pi 3B +를 설치 하는 데 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-117">Dashboard cannot be used used to setup the Raspberry Pi 3B+.</span></span> <span data-ttu-id="706ad-118">3B + 장치가 있는 경우 사용 해야 합니다 [3B + 기술 미리 보기](https://www.microsoft.com/en-us/software-download/windowsiot)합니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-118">If you have a 3B+ device, you must use the [3B+ technical preview](https://www.microsoft.com/en-us/software-download/windowsiot).</span></span> <span data-ttu-id="706ad-119">참조 하십시오 합니다 [알려진 제한 사항](https://docs.microsoft.com/en-us/windows/iot-core/troubleshooting) 이 개발에 적합 한지 여부를 확인 하려면 기술 미리 보기.</span><span class="sxs-lookup"><span data-stu-id="706ad-119">Please view the [known limitations](https://docs.microsoft.com/en-us/windows/iot-core/troubleshooting) of the technical preview to determine if this is suitable for your development.</span></span>

> [!TIP]
> <span data-ttu-id="706ad-120">외부 디스플레이 하 부팅 하 여 기본 응용 프로그램을 장치를 연결 하는 것 뿐만 아니라 SanDisk SD 카드와 같은 고성능 SD 카드를 사용 하 여 향상 된 안정성에 대 한 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-120">We recommend using a high-performance SD card, such as a SanDisk SD card, for increased stability as well as plugging your device into an external display to see the default application booting up.</span></span>


1. <span data-ttu-id="706ad-121">Windows 10 IoT Core 대시보드 다운로드할 [여기](https://docs.microsoft.com/windows/iot-core/downloads)합니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-121">Download the Windows 10 IoT Core Dashboard [here](https://docs.microsoft.com/windows/iot-core/downloads).</span></span>
2. <span data-ttu-id="706ad-122">다운로드 한 후 대시보드를 열고 클릭 _새 장치 설정_ 컴퓨터에 SD 카드를 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-122">Once downloaded, open the Dashboard and click on _set up a new device_ and insert a SD card into your computer.</span></span>
3. <span data-ttu-id="706ad-123">표시 된 대로 모든 필드를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-123">Fill out all of the fields as indicated.</span></span>
4. <span data-ttu-id="706ad-124">소프트웨어 사용 조건에 동의 하 고 클릭 _다운로드 및 설치_합니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-124">Accept the software license terms and click _Download and install_.</span></span> <span data-ttu-id="706ad-125">Windows 10 IoT Core 지나가는 SD 카드에 이제는 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-125">You'll see that Windows 10 IoT Core is now flashing your SD card.</span></span>


![대시보드 스크린샷](../../media/DeviceSetup/Dashboard-Screenshot.jpg)
 

## <a name="using-the-iot-dashboard-dragonboard-410c"></a><span data-ttu-id="706ad-127">IoT 대시보드 (DragonBoard 410 c)를 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="706ad-127">Using the IoT Dashboard (DragonBoard 410c)</span></span>

> [!Video https://www.youtube.com/embed/iPm57hGq-Q8]

> [!TIP]
> <span data-ttu-id="706ad-128">부팅할 기본 응용 프로그램을 보려면 외장 디스플레이에 장치를 연결 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-128">We recommend plugging your device into an external display to see the default application booting up.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="706ad-129">사용자 지정 이미지를 플래시를 "Custom" OS 빌드 드롭다운 목록에서 원하는 지침을 따르세요 [여기](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image) 기본 이미지를 만들고 완료 하려면 아래 지시를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-129">If you're looking to flash a custom image, select "Custom" from the OS Build dropdown, follow the instructions [here](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image) to create a basic image, and follow the rest of the instructions below to finish.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="706ad-130">새 Dragonboard을 사용 하는 경우 설치 하는 Android를 사용 하 여 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-130">When you're working with a new Dragonboard, it comes with Android installed.</span></span> <span data-ttu-id="706ad-131">초기화 및 eMMC 깜박이 메서드를 사용 하 여 장치를 로드 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-131">You will need to wipe and load the device using the eMMC flashing method.</span></span>

> [!NOTE]
> <span data-ttu-id="706ad-132">프로그램 DragonBoard를 사용 하 여 오디오 관련 문제를 실행 하는 경우 Qualcomm의 수동를 읽는 것이 좋습니다 [여기](https://developer.qualcomm.com/download/db410c/stereo-connector-and-audio-routing-application-note.pdf)합니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-132">If you're running into any audio-related issues with your DragonBoard, we advise that you read through Qualcomm's manual [here](https://developer.qualcomm.com/download/db410c/stereo-connector-and-audio-routing-application-note.pdf).</span></span> 

1. <span data-ttu-id="706ad-133">Windows 10 IoT Core 대시보드 다운로드할 [여기](https://docs.microsoft.com/windows/iot-core/downloads)합니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-133">Download the Windows 10 IoT Core Dashboard [here](https://docs.microsoft.com/windows/iot-core/downloads).</span></span>
2. <span data-ttu-id="706ad-134">다운로드 한 후 대시보드를 열고 "Qualcomm DragonBoard 410 c"를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-134">Once downloaded, open the Dashboard and select "Qualcomm DragonBoard 410c".</span></span> <span data-ttu-id="706ad-135">그런 다음 _Windows Insider로 로그인_합니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-135">Then _sign in as a Windows Insider_.</span></span> <span data-ttu-id="706ad-136">DragonBoard 410 c를 플래시 하려면 참가자로 로그인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-136">You need to be signed in as an insider in order to flash DragonBoard 410c.</span></span> 
3. <span data-ttu-id="706ad-137">Qualcomm 보드 microUSB 케이블을 사용 하 여 개발자 컴퓨터에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-137">Connect the Qualcomm board to the developer machine using a microUSB cable.</span></span>
4. <span data-ttu-id="706ad-138">전원 켜기 12V를 사용 하 여 Dragonboard (> 1A) 전원 공급 장치 볼륨 크게 (+)를 누른 채 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-138">Power on your Dragonboard using a 12V (>1A) power supply while holding down the volume up (+) button.</span></span> <span data-ttu-id="706ad-139">장치--디스플레이에 연결 하는 경우 망치, 번개, 및는 코그의 이미지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-139">The device - when connected to a display - should show the image of a hammer, a lightning bolt, and a cog.</span></span> 
5. <span data-ttu-id="706ad-140">이제 장치 대시보드에서 아래와 같이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-140">The device should now be visible on the Dashboard as shown below.</span></span> <span data-ttu-id="706ad-141">적절 한 장치를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-141">Select the appropriate device.</span></span>
6. <span data-ttu-id="706ad-142">소프트웨어 사용 조건에 동의 하 고 클릭 _다운로드 및 설치_합니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-142">Accept the software license terms and click _Download and install_.</span></span> <span data-ttu-id="706ad-143">Windows 10 IoT Core 이제 장치에 깜박이 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-143">You'll see that Windows 10 IoT Core is now flashing onto your device.</span></span>


![플래시 모드로 DragonBoard](../../media/DeviceSetup/db4.png)


## <a name="flashing-with-emmc-for-dragonboard-410c-other-qualcomm-devices"></a><span data-ttu-id="706ad-145">깜박이 eMMC를 사용 하 여 (예: DragonBoard 410 c 다른 Qualcomm 장치)</span><span class="sxs-lookup"><span data-stu-id="706ad-145">Flashing with eMMC (for DragonBoard 410c, other Qualcomm devices)</span></span>

1. <span data-ttu-id="706ad-146">에 대 한 DragonBoard 업데이트 도구 다운로드 및 설치 프로그램 [x86](https://developer.qualcomm.com/download/db410c/windows-10-iot-update-tool-dragonboard-410c-x86.zip) 하거나 [x64](https://developer.qualcomm.com/download/db410c/windows-10-iot-update-tool-dragonboard-410c-x64.zip) 컴퓨터.</span><span class="sxs-lookup"><span data-stu-id="706ad-146">Download and install the DragonBoard Update Tool for your [x86](https://developer.qualcomm.com/download/db410c/windows-10-iot-update-tool-dragonboard-410c-x86.zip) or [x64](https://developer.qualcomm.com/download/db410c/windows-10-iot-update-tool-dragonboard-410c-x64.zip) machine.</span></span>
2. <span data-ttu-id="706ad-147">다운로드 합니다 [Windows 10 IoT Core DragonBoard FFU](https://developer.microsoft.com/en-us/windows/iot/Downloads)합니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-147">Download the [Windows 10 IoT Core DragonBoard FFU](https://developer.microsoft.com/en-us/windows/iot/Downloads).</span></span>
3. <span data-ttu-id="706ad-148">다운로드 한 ISO 파일을 두 번 누릅니다 하 고 탑재 된 가상 CD 드라이브를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-148">Double-click on the downloaded ISO file and locate the mounted Virtual CD-drive.</span></span> <span data-ttu-id="706ad-149">이 드라이브는 설치 관리자 파일 (.msi);에 포함 됩니다. 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-149">This drive will contain an installer file (.msi); double-click on it.</span></span> <span data-ttu-id="706ad-150">새 디렉터리 아래에 있는 PC에 이렇게 `C:\Program Files (x86)\Microsoft IoT\FFU\` 에서 표시 하는 이미지 파일을 "flash.ffu"입니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-150">This creates a new directory on your PC under `C:\Program Files (x86)\Microsoft IoT\FFU\` in which you should see an image file, "flash.ffu".</span></span>
4. <span data-ttu-id="706ad-151">아래와 같이 프로그램 DragonBoard가 다운로드 모드를 첫 번째 부팅 전환할 보드의 USB 부팅 설정 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-151">Ensure your DragonBoard is in download mode by setting the first boot switch on the board to USB Boot, as shown below.</span></span> <span data-ttu-id="706ad-152">그런 다음 DragonBoard microUSB 케이블을 통해 호스트 PC 연결한 후에 12V DragonBoard 플러그 인 (> 1A) 전원 공급 장치.</span><span class="sxs-lookup"><span data-stu-id="706ad-152">Then, connect DragonBoard the host PC via a microUSB cable, then plug in the DragonBoard to a 12V (> 1A) power supply.</span></span>
5. <span data-ttu-id="706ad-153">DragonBoard 녹색 원을 사용 하 여 사용자 PC에 연결 되어 있는지 검색 해야 하는 DragonBoard 업데이트 도구를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-153">Start the DragonBoard Update Tool, which should detect that the DragonBoard is connect to your PC with a green circle.</span></span> <span data-ttu-id="706ad-154">"찾아보기" DragonBoard의를 다운로드 한 FFU 클릭 합니다 _프로그램_ 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-154">"Browse" to the DragonBoard's FFU that you downloaded, then click the _Program_ button.</span></span>
6. <span data-ttu-id="706ad-155">"찾아보기"를 다시 클릭 하 고 5 단계에서 생성 된 "rawprogram0.xml"를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-155">Click "Browse" again and select "rawprogram0.xml" that was generated in step 5.</span></span> <span data-ttu-id="706ad-156">"프로그램" 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-156">Then click the "Program" button.</span></span>
7. <span data-ttu-id="706ad-157">다운로드가 완료 되 면 전원 공급 장치 및 microUSB 케이블 다시 USB 부팅 스위치 보드 및 설정/해제에서 연결 끊기 _OFF_합니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-157">Once the download is complete, disconnect the power supply and microUSB cable from the board and toggle the USB Boot switch back to _OFF_.</span></span> <span data-ttu-id="706ad-158">HDMI 디스플레이, 마우스 및 키보드 DragonBoard 및 rec-끊기 전원 공급 장치에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-158">Connect a HDMI display, a mouse, and a keyboard to the DragonBoard and rec-onnect the power supply.</span></span> <span data-ttu-id="706ad-159">몇 분 후 Windows 10 IoT Core 기본 응용 프로그램이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-159">After a few minutes, you should see the Windows 10 IoT Core default application.</span></span> 

![DragonBoard 다운로드 모드](../../media/DeviceSetup/db1.png)

> [!NOTE]
> <span data-ttu-id="706ad-161">BIOS 설정을 다시 입력 하 고 대신 USB 드라이브에서 하드 드라이브에서 로드 하는 부팅 드라이브 순서를 전환 하 여 eMMC 메모리에서 장치는 이제 부팅 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-161">Make sure the device is now booting from the eMMC memory by entering the BIOS setup again and switching the Boot Drive order to load from the Hard Drive instead of from the USB Drive.</span></span>


## <a name="flashing-with-emmc-for-up-squared-other-intel-devices"></a><span data-ttu-id="706ad-162">깜박이 eMMC를 사용 하 여 (에 대 한 등록 제곱, 기타 Intel 장치)</span><span class="sxs-lookup"><span data-stu-id="706ad-162">Flashing with eMMC (for Up Squared, other Intel devices)</span></span>

1. <span data-ttu-id="706ad-163">다운로드 및 설치 합니다 [Windows 평가 및 배포 키트](https://docs.microsoft.com/windows-hardware/get-started/adk-install) 실행 중인 Windows 10의 버전과 상관 관계 자동 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-163">Download and install the [Windows Assessment and Deployment kit](https://docs.microsoft.com/windows-hardware/get-started/adk-install) with the correlating version of Windows 10 you're running.</span></span>
2. <span data-ttu-id="706ad-164">컴퓨터에 USB 드라이브를 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-164">Insert a USB drive into your machine.</span></span>
3. <span data-ttu-id="706ad-165">USB 부팅 가능 WinPE 이미지를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-165">Create a USB-bootable WinPE image:</span></span>
4. <span data-ttu-id="706ad-166">배포 및 이미징 도구 환경을 시작 `(C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Deployment Tools)` 관리자 권한으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-166">Start the Deployment and Imaging Tools Environment `(C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Deployment Tools)` as an administrator.</span></span>
5. <span data-ttu-id="706ad-167">Windows PE 파일의 작업 복사본을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-167">Create a working copy of the Windows PE files.</span></span> <span data-ttu-id="706ad-168">X86, amd64 지정 또는 ARM:</span><span class="sxs-lookup"><span data-stu-id="706ad-168">Specify either x86, amd64 or ARM:</span></span> `Copype amd64 C:\WINPE_amd64`
6. <span data-ttu-id="706ad-169">Windows PE 아래 WinPE 드라이브 문자를 지정 하는 USB 플래시 드라이브에 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-169">Install Windows PE to the USB flash drive, specifying the WinPE drive letter below.</span></span> <span data-ttu-id="706ad-170">자세한 정보를 찾을 수 있습니다 [여기](https://docs.microsoft.com/windows-hardware/manufacture/desktop/winpe-create-usb-bootable-drive)합니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-170">More information can be found [here](https://docs.microsoft.com/windows-hardware/manufacture/desktop/winpe-create-usb-bootable-drive).</span></span> `MMakeWinPEMedia /UFD C:\WinPE_amd64 P:`
7. <span data-ttu-id="706ad-171">다운로드 합니다 [Windows 10 IoT Core 이미지](https://downloads.up-community.org/?post_type=wpdmpro&p=204&preview=true) 탑재 된 가상 CD 드라이브를 찾아 다운로드 한 ISO 파일을 두 번 클릭 하 여 합니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-171">Download the [Windows 10 IoT Core image](https://downloads.up-community.org/?post_type=wpdmpro&p=204&preview=true) by double-clicking on the downloaded ISO file and locating the mounted Virtual CD-drive.</span></span>
8. <span data-ttu-id="706ad-172">이 드라이브는 설치 파일 (.msi);에 포함 됩니다. 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-172">This drive will contain an install file (.msi); double click it.</span></span> <span data-ttu-id="706ad-173">C:\Program Files (x86) \Microsoft IoT\FFU\ shoul d 참조 이미지 파일에는 아래에 있는 PC에이 새 디렉터리를 만듭니다 "flash.ffu"입니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-173">This will create a new directory on your PC under C:\Program Files (x86)\Microsoft IoT\FFU\ in which you shoul d see an image file, "flash.ffu".</span></span>
9. <span data-ttu-id="706ad-174">다운로드 하 고 압축을 풉니다 복사 합니다 [eMMC 설치 관리자 스크립트](https://github.com/ms-iot/content/blob/develop/Resources/eMMCInstaller.zip) 장치의 FFU 함께 USB 장치의 루트 디렉터리입니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-174">Download, unzip and copy the [eMMC Installer script](https://github.com/ms-iot/content/blob/develop/Resources/eMMCInstaller.zip) to the USB device's root directory, along with the device's FFU.</span></span>
10. <span data-ttu-id="706ad-175">USB 허브를 USB 드라이브, 마우스 및 키보드를 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-175">Connect the USB drive, mouse, and keyboard to the USB hub.</span></span> <span data-ttu-id="706ad-176">USB 허브 및 장치에 전원 코드를 장치에 HDMI 표시, 장치를 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-176">Attach the HDMI display to your device, the device to the USB hub, and the power cord to the device.</span></span>
11. <span data-ttu-id="706ad-177">장치의 BIOS 설정으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-177">Go to the BIOS setup of the device.</span></span> <span data-ttu-id="706ad-178">선택 *Windows* uSB 드라이브에서 부팅 하려면 운영 체제 하며 장치를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-178">Select *Windows* as the Operating system and set the device to boot from your uSB drive.</span></span> <span data-ttu-id="706ad-179">시스템이 다시 부팅 하면 WinPE 명령 프롬프트 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-179">When the system reboots, you will see the WinPE command prompt.</span></span> <span data-ttu-id="706ad-180">USB 드라이브에 WinPE 프롬프트를 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-180">Switch the WinPE prompt to the USB Drive.</span></span> <span data-ttu-id="706ad-181">일반적으로 C: 또는 D 이지만 다른 드라이버 문자를 시도해 야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-181">This is usually C: or D: but you may need to try other driver letters.</span></span>
12. <span data-ttu-id="706ad-182">EMMC 장치의 eMMC 메모리를 Windows 10 IoT Core 이미지를 설치 하는 설치 관리자 스크립트를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-182">Run the eMMC Installer script, which will install the Windows 10 IoT Core image to the device's eMMC memory.</span></span> <span data-ttu-id="706ad-183">완료 되 면 아무 키나 눌러 및 실행 `wpeutil reboot`합니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-183">When it completes, press any key and run `wpeutil reboot`.</span></span> <span data-ttu-id="706ad-184">시스템은 Windows 10 IoT Core 부팅 하 고 구성 프로세스를 시작 하 고 기본 응용 프로그램 로드 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-184">The system should boot into Windows 10 IoT Core, start the configuration process, and load the default application.</span></span>

> [!NOTE]
> <span data-ttu-id="706ad-185">BIOS 설정을 다시 입력 하 고 대신 USB 드라이브에서 하드 드라이브에서 로드 하는 부팅 드라이브 순서를 전환 하 여 eMMC 메모리에서 장치는 이제 부팅 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-185">Make sure the device is now booting from the eMMC memory by entering the BIOS setup again and switching the Boot Drive order to load from the Hard Drive instead of from the USB Drive.</span></span>


## <a name="connecting-to-a-network"></a><span data-ttu-id="706ad-186">네트워크에 연결</span><span class="sxs-lookup"><span data-stu-id="706ad-186">Connecting to a network</span></span>

#### <a name="wired-connection"></a><span data-ttu-id="706ad-187">유선된으로 연결</span><span class="sxs-lookup"><span data-stu-id="706ad-187">Wired connection</span></span>
<span data-ttu-id="706ad-188">이더넷 포트 또는 유선된 연결을 사용 하려면 USB 이더넷 어댑터에서 지 원하는 장치의 상태가 되 면 네트워크에 연결할 이더넷 케이블을 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-188">If your device comes with an Ethernet port or USB Ethernet adapter support to enable a wired connection, attach an Ethernet cable to connect it to your network.</span></span>

#### <a name="wireless-connection"></a><span data-ttu-id="706ad-189">무선 연결</span><span class="sxs-lookup"><span data-stu-id="706ad-189">Wireless connection</span></span>
<span data-ttu-id="706ad-190">장치에서 Wi-fi 연결을 지 원하는 경우 디스플레이에 연결 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-190">If your device supports Wi-Fi connectivity and you've connected a display to it, you'll need to:</span></span>

1. <span data-ttu-id="706ad-191">기본 응용 프로그램으로 이동한 다음 클록 옆에 있는 설정 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-191">Go into your default application and click the settings button next to the clock.</span></span>
2. <span data-ttu-id="706ad-192">설정 페이지에서 선택 _네트워크 및 Wi-fi_합니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-192">On the settings page, select _Network and Wi-Fi_.</span></span>
3. <span data-ttu-id="706ad-193">장치의 무선 네트워크에 대 한 검색을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-193">Your device will begin scanning for wireless networks.</span></span>
4. <span data-ttu-id="706ad-194">이 목록에 표시 되는 네트워크를 선택 하 고 클릭 _Connect_합니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-194">Once your network appears in this list, select it and click _Connect_.</span></span>

<span data-ttu-id="706ad-195">디스플레이 연결 하지 않은 하 고 Wi-fi를 통해 연결 하려는 경우을 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-195">If you haven't connected a display and would like to connect via Wi-Fi, you'll need to:</span></span>

1. <span data-ttu-id="706ad-196">IoT 대시보드로 이동 하 고 클릭 _내 장치_합니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-196">Go to the IoT Dashboard and click on _My Devices_.</span></span>
2. <span data-ttu-id="706ad-197">목록에서 구성 되지 않은 보드를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-197">Find your unconfigured board from the list.</span></span> <span data-ttu-id="706ad-198">이름과 "AJ_"로 시작 됩니다... (예:: AJ_58EA6C68)입니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-198">Its name will begin with "AJ_"... (e.g. AJ_58EA6C68).</span></span> <span data-ttu-id="706ad-199">몇 분 정도 지나면 보드 표시 되지 않는 경우 보드를 다시 부팅 하십시오.</span><span class="sxs-lookup"><span data-stu-id="706ad-199">If you don't see your board appear after a few minutes, try rebooting your board.</span></span>
3. <span data-ttu-id="706ad-200">클릭할 _장치 구성_ 네트워크 자격 증명을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-200">Click on _Configure Device_ and enter your network credentials.</span></span> <span data-ttu-id="706ad-201">그러면 네트워크에 보드를 연결 됩니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-201">This will connect your board to the network.</span></span>

> [!NOTE]
> <span data-ttu-id="706ad-202">Wifi를 컴퓨터에 다른 네트워크를 찾을 수 있도록 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-202">Wifi on your computer will need to be turned on in order to find other networks.</span></span>

## <a name="connecting-to-windows-device-portal"></a><span data-ttu-id="706ad-203">Windows Device Portal 연결</span><span class="sxs-lookup"><span data-stu-id="706ad-203">Connecting to Windows Device Portal</span></span>

<span data-ttu-id="706ad-204">사용 합니다 [Windows Device Portal](../../manage-your-device/DevicePortal.md) 웹 브라우저를 통해 장치를 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-204">Use the [Windows Device Portal](../../manage-your-device/DevicePortal.md) to connect your device through a web browser.</span></span> <span data-ttu-id="706ad-205">장치 포털 중요 한 구성 및 장치 관리 기능을 사용할 수 있게 합니다.</span><span class="sxs-lookup"><span data-stu-id="706ad-205">The device portal makes valuable configuration and device management capabilities available.</span></span> 

