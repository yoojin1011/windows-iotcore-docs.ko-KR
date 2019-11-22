---
title: Intel 디바이스 설정
ms.date: 05/22/2019
ms.topic: article
description: Windows 10 IoT Core를 사용하여 Intel 디바이스를 설정하는 방법을 알아봅니다.
keywords: Windows 10 IoT Core, Intel
ms.custom: RS5
ms.openlocfilehash: bd1aa788e11bf4d01fdd897c64c9ae947928a46f
ms.sourcegitcommit: 833f64e5c9ef8edc6ea62824d5f4f0b7d5a03270
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/18/2019
ms.locfileid: "74154972"
---
# <a name="setting-up-an-intel-device"></a><span data-ttu-id="66f4c-104">Intel 디바이스 설정</span><span class="sxs-lookup"><span data-stu-id="66f4c-104">Setting up an Intel device</span></span>

<span data-ttu-id="66f4c-105">Qualcomm 디바이스로 제작하려는 경우에는 [IoT Core 제작 가이드](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="66f4c-105">If you're looking to manufacture with a Qualcomm device, please refer to the [IoT Core Manufacturing Guide](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).</span></span> <span data-ttu-id="66f4c-106">제조사 이미지는 제작에 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="66f4c-106">You cannot use maker images for manufacturing.</span></span>

> [!NOTE]
> <span data-ttu-id="66f4c-107">BIOS 설정을 다시 입력하고, USB 드라이브 대신 하드 드라이브에서 로드하도록 부팅 드라이브 순서를 전환하여 디바이스가 eMMC 메모리에서 부팅되도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="66f4c-107">Make sure the device is now booting from the eMMC memory by entering the BIOS setup again and switching the Boot Drive order to load from the Hard Drive instead of from the USB Drive.</span></span>

## <a name="using-emmc"></a><span data-ttu-id="66f4c-108">eMMC 사용</span><span class="sxs-lookup"><span data-stu-id="66f4c-108">Using eMMC</span></span>

1. <span data-ttu-id="66f4c-109">실행 중인 Windows 10 버전과 관련된 [Windows 평가 및 배포 키트](https://docs.microsoft.com/windows-hardware/get-started/adk-install)를 다운로드하여 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="66f4c-109">Download and install the [Windows Assessment and Deployment kit](https://docs.microsoft.com/windows-hardware/get-started/adk-install) with the correlating version of Windows 10 you're running.</span></span>
2. <span data-ttu-id="66f4c-110">USB 드라이브를 머신에 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="66f4c-110">Insert a USB drive into your machine.</span></span>
3. <span data-ttu-id="66f4c-111">USB 부팅 가능 WinPE 이미지 만들기:</span><span class="sxs-lookup"><span data-stu-id="66f4c-111">Create a USB-bootable WinPE image:</span></span>
4. <span data-ttu-id="66f4c-112">관리자로 배포 및 이미지 도구 환경 `(C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Deployment Tools)`를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="66f4c-112">Start the Deployment and Imaging Tools Environment `(C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Deployment Tools)` as an administrator.</span></span>
5. <span data-ttu-id="66f4c-113">Windows PE 파일의 작업 복사본을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="66f4c-113">Create a working copy of the Windows PE files.</span></span> <span data-ttu-id="66f4c-114">x86, amd64 또는 ARM: `Copype amd64 C:\WINPE_amd64`를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="66f4c-114">Specify either x86, amd64 or ARM: `Copype amd64 C:\WINPE_amd64`</span></span>
6. <span data-ttu-id="66f4c-115">아래의 WinPE 드라이브 문자를 지정하여 USB 플래시 드라이브에 Windows PE를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="66f4c-115">Install Windows PE to the USB flash drive, specifying the WinPE drive letter below.</span></span> <span data-ttu-id="66f4c-116">자세한 내용은 [여기](https://docs.microsoft.com/windows-hardware/manufacture/desktop/winpe-create-usb-bootable-drive)서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66f4c-116">More information can be found [here](https://docs.microsoft.com/windows-hardware/manufacture/desktop/winpe-create-usb-bootable-drive).</span></span> `MakeWinPEMedia /UFD C:\WinPE_amd64 P:`
7. <span data-ttu-id="66f4c-117">다운로드한 ISO 파일을 두 번 클릭하고 탑재된 가상 CD 드라이브를 찾아 [Windows 10 IoT Core 이미지](https://downloads.up-community.org/?post_type=wpdmpro&p=204&preview=true)를 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="66f4c-117">Download the [Windows 10 IoT Core image](https://downloads.up-community.org/?post_type=wpdmpro&p=204&preview=true) by double-clicking on the downloaded ISO file and locating the mounted Virtual CD-drive.</span></span>
8. <span data-ttu-id="66f4c-118">이 드라이브에 포함된 설치 관리자 파일(.msi)을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="66f4c-118">This drive will contain an install file (.msi); double click it.</span></span> <span data-ttu-id="66f4c-119">그러면 PC의 C:\Program Files (x86)\Microsoft IoT\FFU\ 아래에 새 디렉터리가 생성됩니다. 이 디렉터리에 "flash.ffu" 이미지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66f4c-119">This will create a new directory on your PC under C:\Program Files (x86)\Microsoft IoT\FFU\ in which you shoul d see an image file, "flash.ffu".</span></span>
9. <span data-ttu-id="66f4c-120">디바이스의 FFU와 함께 [eMMC 설치 관리자 스크립트](https://github.com/ms-iot/content/blob/develop/Resources/eMMCInstaller.zip)를 USB 디바이스의 루트 디렉터리에 다운로드하여 압축을 풀고 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="66f4c-120">Download, unzip and copy the [eMMC Installer script](https://github.com/ms-iot/content/blob/develop/Resources/eMMCInstaller.zip) to the USB device's root directory, along with the device's FFU.</span></span>
10. <span data-ttu-id="66f4c-121">USB 드라이브, 마우스 및 키보드를 USB 허브에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="66f4c-121">Connect the USB drive, mouse, and keyboard to the USB hub.</span></span> <span data-ttu-id="66f4c-122">HDMI 디스플레이를 디바이스에 연결하고, 디바이스를 USB 허브에 연결하고, 전원 코드를 디바이스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="66f4c-122">Attach the HDMI display to your device, the device to the USB hub, and the power cord to the device.</span></span>
11. <span data-ttu-id="66f4c-123">디바이스의 BIOS 설정으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="66f4c-123">Go to the BIOS setup of the device.</span></span> <span data-ttu-id="66f4c-124">운영 체제로 *Windows*를 선택하고, USB 드라이브에서 부팅하도록 디바이스를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="66f4c-124">Select *Windows* as the Operating system and set the device to boot from your uSB drive.</span></span> <span data-ttu-id="66f4c-125">시스템이 다시 부팅되면 WinPE 명령 프롬프트가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="66f4c-125">When the system reboots, you will see the WinPE command prompt.</span></span> <span data-ttu-id="66f4c-126">WinPE 프롬프트를 USB 드라이브로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="66f4c-126">Switch the WinPE prompt to the USB Drive.</span></span> <span data-ttu-id="66f4c-127">일반적으로 C: 또는 D:이지만 다른 드라이버 문자를 사용해야 하는 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66f4c-127">This is usually C: or D: but you may need to try other driver letters.</span></span>
12. <span data-ttu-id="66f4c-128">디바이스의 eMMC 메모리에 Windows 10 IoT Core 이미지를 설치하는 eMMC 설치 관리자 스크립트를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="66f4c-128">Run the eMMC Installer script, which will install the Windows 10 IoT Core image to the device's eMMC memory.</span></span> <span data-ttu-id="66f4c-129">스크립트가 완료되면 아무 키를 눌러 `wpeutil reboot`를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="66f4c-129">When it completes, press any key and run `wpeutil reboot`.</span></span> <span data-ttu-id="66f4c-130">시스템이 Windows 10 IoT Core로 부팅되고, 구성 프로세스를 시작하고, 기본 애플리케이션을 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="66f4c-130">The system should boot into Windows 10 IoT Core, start the configuration process, and load the default application.</span></span>

## <a name="connect-to-a-network"></a><span data-ttu-id="66f4c-131">네트워크에 연결</span><span class="sxs-lookup"><span data-stu-id="66f4c-131">Connect to a network</span></span>

### <a name="wired-connection"></a><span data-ttu-id="66f4c-132">유선 연결</span><span class="sxs-lookup"><span data-stu-id="66f4c-132">Wired connection</span></span>
<span data-ttu-id="66f4c-133">디바이스에 유선 연결을 지원하는 이더넷 포트 또는 USB 이더넷 어댑터가 있는 경우 이더넷 케이블을 연결하여 네트워크에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="66f4c-133">If your device comes with an Ethernet port or USB Ethernet adapter support to enable a wired connection, attach an Ethernet cable to connect it to your network.</span></span>

### <a name="wireless-connection"></a><span data-ttu-id="66f4c-134">무선 연결</span><span class="sxs-lookup"><span data-stu-id="66f4c-134">Wireless connection</span></span>
<span data-ttu-id="66f4c-135">디바이스에서 Wi-Fi 연결이 지원되고 디바이스를 디스플레이에 연결한 경우 다음 단계를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="66f4c-135">If your device supports Wi-Fi connectivity and you've connected a display to it, you'll need to:</span></span>

1. <span data-ttu-id="66f4c-136">기본 애플리케이션으로 이동하여 시계 옆에 있는 설정 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="66f4c-136">Go into your default application and click the settings button next to the clock.</span></span>
2. <span data-ttu-id="66f4c-137">설정 페이지에서 _네트워크 및 Wi-Fi_를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="66f4c-137">On the settings page, select _Network and Wi-Fi_.</span></span>
3. <span data-ttu-id="66f4c-138">디바이스가 무선 네트워크 검색을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="66f4c-138">Your device will begin scanning for wireless networks.</span></span>
4. <span data-ttu-id="66f4c-139">이 목록에 네트워크가 나타나면 네트워크를 선택하고 _연결_을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="66f4c-139">Once your network appears in this list, select it and click _Connect_.</span></span>

<span data-ttu-id="66f4c-140">디스플레이를 연결하지 않았으며 Wi-Fi를 통해 연결하려는 경우에는 다음 단계를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="66f4c-140">If you haven't connected a display and would like to connect via Wi-Fi, you'll need to:</span></span>

1. <span data-ttu-id="66f4c-141">IoT 대시보드로 이동하여 _내 디바이스_를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="66f4c-141">Go to the IoT Dashboard and click on _My Devices_.</span></span>
2. <span data-ttu-id="66f4c-142">목록에서 구성되지 않은 보드를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="66f4c-142">Find your unconfigured board from the list.</span></span> <span data-ttu-id="66f4c-143">보드 이름은 "AJ_"로 시작합니다(예: AJ_58EA6C68).</span><span class="sxs-lookup"><span data-stu-id="66f4c-143">Its name will begin with "AJ_"... (e.g. AJ_58EA6C68).</span></span> <span data-ttu-id="66f4c-144">몇 분이 지나도 보드가 보이지 않으면 보드를 다시 부팅합니다.</span><span class="sxs-lookup"><span data-stu-id="66f4c-144">If you don't see your board appear after a few minutes, try rebooting your board.</span></span>
3. <span data-ttu-id="66f4c-145">_디바이스 구성_을 클릭하고 네트워크 자격 증명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="66f4c-145">Click on _Configure Device_ and enter your network credentials.</span></span> <span data-ttu-id="66f4c-146">그러면 보드가 네트워크에 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="66f4c-146">This will connect your board to the network.</span></span>

> [!NOTE]
> <span data-ttu-id="66f4c-147">다른 네트워크를 찾으려면 컴퓨터의 Wifi를 켜야 합니다.</span><span class="sxs-lookup"><span data-stu-id="66f4c-147">Wifi on your computer will need to be turned on in order to find other networks.</span></span>

## <a name="connect-to-windows-device-portal"></a><span data-ttu-id="66f4c-148">Windows 디바이스 포털에 연결</span><span class="sxs-lookup"><span data-stu-id="66f4c-148">Connect to Windows Device Portal</span></span>

<span data-ttu-id="66f4c-149">[Windows 디바이스 포털](../manage-your-device/DevicePortal.md)을 사용하여 웹 브라우저를 통해 디바이스를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="66f4c-149">Use the [Windows Device Portal](../manage-your-device/DevicePortal.md) to connect your device through a web browser.</span></span> <span data-ttu-id="66f4c-150">디바이스 포털에서는 중요한 구성과 디바이스 관리 기능을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66f4c-150">The device portal makes valuable configuration and device management capabilities available.</span></span> 


