---
title: 17744 빌드의 릴리스 정보
author: zeeshanfurqan
ms.author: zeeshanf
ms.date: 08/24/2018
ms.topic: article
description: Windows 참가자 빌드 번호 17744의 새로운 기능에 대해 알아봅니다.
keywords: windows iot, Windows 참가자, 릴리스 정보
ms.openlocfilehash: 3f78aa22f6edd4692d1e7956edc30856eeed2e7c
ms.sourcegitcommit: 9ec4716afde25fdc8b94f7c0794448501f451b55
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/17/2019
ms.locfileid: "60170291"
---
# <a name="release-notes-for-build-17744"></a><span data-ttu-id="1e586-104">17744 빌드의 릴리스 정보</span><span class="sxs-lookup"><span data-stu-id="1e586-104">Release Notes for Build 17744</span></span>
<span data-ttu-id="1e586-105">_빌드 번호 17744. 2018년 8월._</span><span class="sxs-lookup"><span data-stu-id="1e586-105">_Build Number 17744. August 2018._</span></span>

<span data-ttu-id="1e586-106">&copy; 2018 Microsoft Corporation.</span><span class="sxs-lookup"><span data-stu-id="1e586-106">&copy; 2018 Microsoft Corporation.</span></span> <span data-ttu-id="1e586-107">All rights reserved.</span><span class="sxs-lookup"><span data-stu-id="1e586-107">All rights reserved.</span></span>

<span data-ttu-id="1e586-108">이 문서는 Windows 10 IoT Core에 포함된 설명서를 보완하는 최신 뉴스 또는 기타 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-108">This document provides late-breaking or other information that supplements the documentation included with the Windows 10 IoT Core.</span></span>

<span data-ttu-id="1e586-109">Windows 10 IoT Core를 다운로드해 주셔서 감사합니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-109">Thank you for downloading Windows 10 IoT Core.</span></span> <span data-ttu-id="1e586-110">Windows 10 IoT Core는 임베디드 또는 전용 디바이스 개발을 목적으로 설계된 Windows 10 버전으로 제조사 커뮤니티에 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-110">Windows 10 IoT Core is the version of Windows 10 intended for development of embedded or dedicated purpose devices and the choice for the Maker community.</span></span> <span data-ttu-id="1e586-111">이 릴리스의 패키지에는 Intel Atom 프로세서 기반의 Minnowboard Max 플랫폼, Broadcom 2836/2837 기반의 Raspberry Pi 2/3, Qualcomm Snapdragon 400 시리즈 프로세서 기반의 Dragonboard 410c에 Windows 10 IoT Core를 설치하는 데 필요한 도구 및 콘텐츠가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-111">The packages within this release contain tools and content needed to install Windows 10 IoT Core on Minnowboard Max platform based on Intel Atom processers, Raspberry Pi 2/3 based on Broadcom 2836/2837, and Dragonboard 410c based on Qualcomm Snapdragon 400 series processors.</span></span>


## <a name="privacy-statement"></a><span data-ttu-id="1e586-112">개인정보처리방침</span><span class="sxs-lookup"><span data-stu-id="1e586-112">Privacy Statement</span></span>

<span data-ttu-id="1e586-113">이 Windows 운영 체제 버전의 개인정보처리방침은 [여기](http://go.microsoft.com/fwlink/?LinkId=506737)서 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-113">The privacy statement for this version of the Windows operating system can be viewed [here](http://go.microsoft.com/fwlink/?LinkId=506737).</span></span>

<span data-ttu-id="1e586-114">브라우저 창에 전달 링크를 붙여넣는 방법으로 연결된 조건을 검토할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-114">You can review linked terms by pasting the forward link into your browser window.</span></span>

## <a name="whats-new-in-this-build"></a><span data-ttu-id="1e586-115">이 빌드의 새로운 기능</span><span class="sxs-lookup"><span data-stu-id="1e586-115">What's new in this build:</span></span> 
* <span data-ttu-id="1e586-116">일반 버그 수정</span><span class="sxs-lookup"><span data-stu-id="1e586-116">General bug fixes</span></span> 


## <a name="additional-information"></a><span data-ttu-id="1e586-117">추가 정보</span><span class="sxs-lookup"><span data-stu-id="1e586-117">Additional Information</span></span>
* <span data-ttu-id="1e586-118">DragonBoard 이미지에 사용되는 BSP 버전은 2118.0.0.0입니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-118">The BSP version used for our Dragon Board image is 2118.0.0.0.</span></span> 


## <a name="known-issues-in-this-build"></a><span data-ttu-id="1e586-119">이 빌드의 알려진 이슈:</span><span class="sxs-lookup"><span data-stu-id="1e586-119">Known issues in this build:</span></span>
* <span data-ttu-id="1e586-120">Visual Studio에서 배포하는 F5 드라이버는 IoT Core에서 작동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-120">F5 driver deployment from Visual Studio does not work on IoT Core.</span></span>
* <span data-ttu-id="1e586-121">NOOBS를 통해 설치된 디바이스는 커널 디버거를 사용하도록 설정하는 bcdedit 도구를 실행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-121">Devices that were installed via NOOBS cannot run the bcdedit tool to enable the kernel debugger.</span></span> <span data-ttu-id="1e586-122">이 문제는 다음과 같은 방법으로 해결할 수 있습니다. \*\*  SD 카드를 PC에 장착 \*\*  diskpart 또는 디스크 관리를 사용하여 EFIESP 디스크 파티션 번호 찾기(이것을 “M:”이라고 함) \*\*  “bcdedit /store M:\EFI\Microsoft\boot\bcd /set {default} debug yes” 명령 실행 \*\*  SD 카드 분리.</span><span class="sxs-lookup"><span data-stu-id="1e586-122">This can be achieved with the following workaround: \*\*  Mount the SD card on your PC \*\*  Find the EFIESP drive partition number with diskpart or Disk Management (say it’s “M:”) \*\*  Run the command “bcdedit /store M:\EFI\Microsoft\boot\bcd /set {default} debug yes” \*\*  Unmount the SD card.</span></span>
<span data-ttu-id="1e586-123">\*\*  이제 평소처럼 디버거를 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-123">\*\*  You should now be able to connect the debugger as usual</span></span>
* <span data-ttu-id="1e586-124">경우에 따라 IoT 디바이스로 명령을 보낼 때 PSSession이 중단되기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-124">On occasion, PSSession will break when sending commands to IoT devices.</span></span>
* <span data-ttu-id="1e586-125">RPi3는 BT + BTLE를 온보드 Bluetooth와 페어링하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-125">RPi3 will not pair BT + BTLE with onboard Bluetooth.</span></span>
* <span data-ttu-id="1e586-126">Up2의 SoftAp를 사용하여 WIFI 연결을 통해 인터넷에 연결할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-126">Unable to connect to internet through WIFI connection with SoftAp of Up2.</span></span>
* <span data-ttu-id="1e586-127">UWF가 일시적으로 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-127">UWF is failing intermittently.</span></span>
* <span data-ttu-id="1e586-128">Windows IoT 원격 클라이언트가 Raspberry Pi와 함께 작동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-128">The Windows IoT Remote client does not work for Raspberry Pi.</span></span> <span data-ttu-id="1e586-129">Minnowboard Max 또는 Dragonboard처럼 가속 그래픽을 사용하는 보드를 사용하거나 로컬 표시용 모니터를 연결하세요.</span><span class="sxs-lookup"><span data-stu-id="1e586-129">Use a board with accelerated graphics such as Minnowboard Max or Dragonboard or attach a monitor for local display.</span></span>


## <a name="iot-core-general-known-issues-and-work-arounds"></a><span data-ttu-id="1e586-130">IoT Core 알려진 일반 이슈 및 해결 방법</span><span class="sxs-lookup"><span data-stu-id="1e586-130">IoT Core general known issues and work arounds</span></span>

### <a name="for-raspberry-pi"></a><span data-ttu-id="1e586-131">Raspberry Pi</span><span class="sxs-lookup"><span data-stu-id="1e586-131">For Raspberry Pi</span></span>

#### <a name="raspberry-pi-display-resolution-if-monitor-is-disconnected"></a><span data-ttu-id="1e586-132">모니터 연결이 끊어진 경우 Raspberry Pi 디스플레이 해상도</span><span class="sxs-lookup"><span data-stu-id="1e586-132">Raspberry Pi Display Resolution if monitor is disconnected</span></span> 
<span data-ttu-id="1e586-133">모니터 연결이 끊어진 경우 Raspberry Pi가 디스플레이 해상도를 유지하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-133">The Raspberry Pi may not maintain Display Resolution if monitor is disconnected.</span></span> <span data-ttu-id="1e586-134">모니터의 EDID는 모니터가 연결될 때 시스템의 해상도를 설정하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-134">The EDID of the monitor is used to set the resolution of the system when one is connected.</span></span> <span data-ttu-id="1e586-135">연결이 끊어지면 Raspberry Pi 펌웨어는 SD 카드의 루트에 있는 config.txt를 기본값으로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-135">When disconnected, the Raspberry Pi firmware defaults to what is in the config.txt in the root of the SD card.</span></span> 

#### <a name="raspberry-pi-video-performance"></a><span data-ttu-id="1e586-136">Raspberry Pi 비디오 성능</span><span class="sxs-lookup"><span data-stu-id="1e586-136">Raspberry Pi Video Performance</span></span> 
<span data-ttu-id="1e586-137">Raspberry Pi 플랫폼의 비디오 재생 성능이 최적화되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-137">Video playback performance on the Raspberry Pi platform is not optimized.</span></span><span data-ttu-id="1e586-138">  XAML 기반 드롭다운 메뉴를 비롯한 애니메이션 사용자 요소가 최적화된 성능을 발휘하지 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-138">  Animated user elements including XAML-based dropdown menus may exhibit less than optimal performance.</span></span> 
 
#### <a name="raspberry-pi-camera-support"></a><span data-ttu-id="1e586-139">Raspberry Pi 카메라 지원</span><span class="sxs-lookup"><span data-stu-id="1e586-139">Raspberry Pi Camera Support</span></span> 
<span data-ttu-id="1e586-140">카메라 주변 기기 지원이 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-140">Support for camera peripheral devices is limited.</span></span> <span data-ttu-id="1e586-141">D3D 최신 USB 웹캠이 USB 호스트 컨트롤러의 매우 까다로운 데이터 스트림을 생성하도록 지원하기 위해 플랫폼이 제한되므로 온보드 카메라 버스에 직접 연결되는 PiCam 디바이스는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-141">The PiCam device directly connected to the onboard camera bus is not supported due to limitations in the platform to support D3D Modern USB webcams produce data streams that are very demanding on the USB Host controller.</span></span><span data-ttu-id="1e586-142">  저해상도 설정으로 사용하더라도 웹캠에서 USB를 미세 조정해야 하며 특수한 제어 논리가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-142">  Even when used with low resolution settings webcams will require additional USB fine tuning and specialized control logic.</span></span> 

#### <a name="raspberry-pi3-bluetooth-support"></a><span data-ttu-id="1e586-143">Raspberry Pi3 Bluetooth 지원</span><span class="sxs-lookup"><span data-stu-id="1e586-143">Raspberry Pi3 Bluetooth support</span></span> 
<span data-ttu-id="1e586-144">Raspberry Pi3 기본 제공 Bluetooth 드라이버는 낮은 대역폭 디바이스만 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-144">The Raspberry Pi3 built-in Bluetooth driver only supports low bandwidth devices.</span></span> 

#### <a name="serial-port-usage-and-access-on-rpi2"></a><span data-ttu-id="1e586-145">RPi2의 직렬 포트 사용 및 액세스</span><span class="sxs-lookup"><span data-stu-id="1e586-145">Serial Port Usage and Access on RPi2</span></span> 
<span data-ttu-id="1e586-146">Raspberry Pi 2는 PL011 UART을 통해 통신에 대한 직렬 전송을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-146">Raspberry Pi 2 supports the serial transport for communication through the PL011 UART.</span></span><span data-ttu-id="1e586-147">  이는 커널 디버깅 시나리오에서 기본적으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-147">  This is set by default in kernel debugging scenarios.</span></span><span data-ttu-id="1e586-148">  애플리케이션 또는 디바이스 드라이버는 PL011 UART를 사용하여 다음 명령을 통해 PL011 디바이스 드라이버와 데이터를 주고받은 후 디버거를 끌 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-148">  An application or device driver can use the PL011 UART to send and receive data with the PL011 device driver turning off the debugger using the following command:</span></span>

```
bcdedit /set debug off 
```

#### <a name="data-breakpoints-have-been-disabled-on-the-raspberry-pi2"></a><span data-ttu-id="1e586-149">데이터 중단점은 Raspberry Pi2에서 비활성화되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-149">Data breakpoints have been disabled on the Raspberry Pi2</span></span>
<span data-ttu-id="1e586-150">현재는 해결 방법이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-150">No workaround at this time.</span></span>

#### <a name="disabling-the-onboard-adapters-for-raspberry-pi-3"></a><span data-ttu-id="1e586-151">Raspberry Pi 3의 온보드 어댑터 비활성화</span><span class="sxs-lookup"><span data-stu-id="1e586-151">Disabling the onboard adapters for Raspberry Pi 3</span></span>
<span data-ttu-id="1e586-152">Raspberry Pi 3에는 다른 동글을 사용하여 Bluetooth를 온보딩하고, 텔넷/ssh 세션을 열고 실행하려면 반드시 비활성화해야 하는 온보드 Bluetooth가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-152">The Raspberry Pi 3 has onboard Bluetooth which must be disabled to use a different dongle to disable to onboard Bluetooth, open a telnet/ssh session and run:</span></span> 
```
reg add hklm\system\controlset001\services\BtwSerialH5Bus /v Start /t REG_DWORD /d 4 
```

<span data-ttu-id="1e586-153">다음 명령을 사용하여 WiFi를 비활성화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-153">You may disable WiFi with the following command:</span></span> 
```
reg add hklm\system\controlset001\services\bcmsdh43xx /v Start /t REG_DWORD /d 4 
``` 

### <a name="for-dragonboard"></a><span data-ttu-id="1e586-154">DragonBoard</span><span class="sxs-lookup"><span data-stu-id="1e586-154">For DragonBoard</span></span>

#### <a name="dragonboard-410c-shutdown"></a><span data-ttu-id="1e586-155">Dragonboard 410c 종료</span><span class="sxs-lookup"><span data-stu-id="1e586-155">Dragonboard 410c Shutdown</span></span>
<span data-ttu-id="1e586-156">DragonBoard에서 종료 명령을 실행해도 보드 전원이 꺼지지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-156">On the DragonBoard, a shutdown command will not power off the board.</span></span> <span data-ttu-id="1e586-157">시스템이 다시 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-157">The system will restart.</span></span> <span data-ttu-id="1e586-158">전원을 차단하여 보드를 끄세요.</span><span class="sxs-lookup"><span data-stu-id="1e586-158">Please power off the board by disconnecting the power.</span></span>

#### <a name="dragonboard-and-windbg"></a><span data-ttu-id="1e586-159">DragonBoard 및 windbg</span><span class="sxs-lookup"><span data-stu-id="1e586-159">DragonBoard and windbg</span></span>
<span data-ttu-id="1e586-160">windbg를 사용하여 DragonBoard에 연결하면 GPIO/I2C/SPI/UART 드라이버가 비활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-160">The GPIO/I2C/SPI/UART drivers will be disabled when connecting to the DragonBoard with windbg.</span></span>

#### <a name="dragonboard-headset--microphone-jack"></a><span data-ttu-id="1e586-161">DragonBoard 헤드셋 및 마이크 잭</span><span class="sxs-lookup"><span data-stu-id="1e586-161">DragonBoard headset & microphone jack</span></span>
<span data-ttu-id="1e586-162">Dragonboard BSP에는 헤드셋 잭과 마이크 잭의 드라이버가 있지만, 둘 중 어느 잭도 보드에 통합되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-162">The Dragonboard BSP has drivers for the headset jack and microphone jack, but it doesn't have either of these jacks on board.</span></span>  

#### <a name="dragonboard-spi-runs-at-48mhz"></a><span data-ttu-id="1e586-163">4\.8Mhz로 실행되는 DragonBoard SPI</span><span class="sxs-lookup"><span data-stu-id="1e586-163">DragonBoard SPI runs at 4.8Mhz</span></span>
<span data-ttu-id="1e586-164">Dragonboard의 SPI는 요청된 속도를 무시하고 항상 4.8Mhz로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-164">The SPI on the Dragonboard will ignore the requested speed and always run at 4.8 Mhz.</span></span>  

#### <a name="dragonboard-connected-standby"></a><span data-ttu-id="1e586-165">DragonBoard 연결된 대기 상태</span><span class="sxs-lookup"><span data-stu-id="1e586-165">DragonBoard Connected Standby</span></span> 
<span data-ttu-id="1e586-166">연결된 대기 상태는 Qualcomm Dragonboard에서 기본적으로 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-166">Connected Standby is not enabled on the Qualcomm Dragonboard by default.</span></span>  <span data-ttu-id="1e586-167">DragonBoard에서 연결된 대기 상태를 사용하도록 설정하려면 다음 레지스트리 키를 "1"로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-167">To enable Connected Standby on DragonBoard the following registry key needs to be set to “1”:</span></span>

```
HKLM\System\Controlset001\Control\Power\CsEnabled=DWORD:1 
```

> [!NOTE]
> <span data-ttu-id="1e586-168">모든 플랫폼이 연결된 대기 상태를 지원하는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-168">Not all platforms have support for Connected Standby.</span></span>  <span data-ttu-id="1e586-169">일부 플랫폼에서 작동하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-169">This may not work on all platforms.</span></span>    


### <a name="for-minnowboard"></a><span data-ttu-id="1e586-170">MinnowBoard</span><span class="sxs-lookup"><span data-stu-id="1e586-170">For MinnowBoard</span></span>
#### <a name="minnowboard-max-boot-and-firmware-update"></a><span data-ttu-id="1e586-171">Minnowboard Max 부팅 및 펌웨어 업데이트</span><span class="sxs-lookup"><span data-stu-id="1e586-171">Minnowboard Max Boot and Firmware Update</span></span> 
<span data-ttu-id="1e586-172">MinnowBoard Max는 펌웨어가 .092 이상이어야만 부팅됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-172">The MinnowBoard Max will not boot unless the firmware is version .092 or later.</span></span> <span data-ttu-id="1e586-173">최소 권장 펌웨어 버전은 “MinnowBoard MAX 0.92 32-Bit”입니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-173">The minimum recommended version of the firmware is “MinnowBoard MAX 0.92 32-Bit”.</span></span> <span data-ttu-id="1e586-174">펌웨어 업데이트는 [여기](http://go.microsoft.com/fwlink/?LinkId=708613)서 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-174">Firmware updates can be downloaded from [here](http://go.microsoft.com/fwlink/?LinkId=708613).</span></span>

#### <a name="minnow-board-peripheral-support"></a><span data-ttu-id="1e586-175">MinnowBoard 주변 기기 지원</span><span class="sxs-lookup"><span data-stu-id="1e586-175">Minnow Board Peripheral Support</span></span>
<span data-ttu-id="1e586-176">이 드롭에 포함된 Windows 10 IoT Core 이미지는 MinnowBoard MAX 보드에 노출되는 주변 기기를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-176">The Windows 10 IoT Core image included in this drop supports the peripherals that are exposed on the MinnowBoard MAX board.</span></span> <span data-ttu-id="1e586-177">향후 Intel에서&reg; Baytrail 프로세서의 전체 기능 세트를 지원할 예정&trade;이며 여기에는 Intel Celeron 프로세서 N2807-J1900/N2930 및 Intel Atom&trade; 프로세서 E38XX가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-177">Subsequently, Intel&reg; will provide support of the full feature set of the Baytrail processors including the Intel Celeron&trade; Processors J1900/N2930/N2807 and Intel Atom&trade; Processors E38XX.</span></span>


### <a name="for-all-platforms"></a><span data-ttu-id="1e586-178">모든 플랫폼</span><span class="sxs-lookup"><span data-stu-id="1e586-178">For All Platforms</span></span> 

#### <a name="mouse-pointer-disappears-while-debugging"></a><span data-ttu-id="1e586-179">디버깅하는 동안 사라지는 마우스 포인터</span><span class="sxs-lookup"><span data-stu-id="1e586-179">Mouse Pointer disappears while debugging</span></span> 
<span data-ttu-id="1e586-180">Visual Studio에서 앱을 배포 또는 디버깅한 후 마우스 포인터가 사라지는 경우가 가끔 있는데, 키보드(Tab)를 사용하여 포커스를 변경하면 마우스 포인터가 다시 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-180">In some cases, the mouse pointer is not visible after deploying or debugging apps with Visual Studio, the mouse pointer should reappear if you change focus using the keyboard (Tab).</span></span>


#### <a name="server-applications-with-softap"></a><span data-ttu-id="1e586-181">SoftAP를 사용하는 서버 애플리케이션</span><span class="sxs-lookup"><span data-stu-id="1e586-181">Server Applications with SoftAP</span></span>
<span data-ttu-id="1e586-182">SoftAP를 사용하면 클라이언트가 UAP 앱에 의해 노출되는 콘텐츠에 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-182">When using the SoftAP clients will not be able to access content exposed by UAP apps.</span></span>  
<span data-ttu-id="1e586-183">SoftAP를 통해 UAP 애플리케이션을 노출하려면 디바이스의 콘솔에서 다음과 같이 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-183">To expose UAP applications via SoftAP the following changes must be made from the console on the device:</span></span>  

```
reg add hklm\system\currentcontrolset\services\mpssvc\parameters /v IoTInboundLoopbackPolicy /t REG_DWORD /d 1 
checknetisolation loopbackexempt -a -n=<AppID for SoftAP App> 
checknetisolation loopbackexempt -a -n=<AppID for Additional App>  
```

<span data-ttu-id="1e586-184">예를 들어 다음과 같은 가치를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-184">For example:</span></span>  
```
checknetisolation loopbackexempt -a -n=IoTOnboardingTask-uwp_1w720vyc4ccym
```
<span data-ttu-id="1e586-185">다시 부팅</span><span class="sxs-lookup"><span data-stu-id="1e586-185">Reboot</span></span> 


#### <a name="sensor-driver-conflict-in-pre-built-ffus"></a><span data-ttu-id="1e586-186">미리 빌드된 FFU의 센서 드라이버 충돌</span><span class="sxs-lookup"><span data-stu-id="1e586-186">Sensor Driver conflict in pre-built FFUs</span></span> 
<span data-ttu-id="1e586-187">제공된 FFU의 센서 드라이버가 충돌합니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-187">There is a Sensor Driver Conflict in the provided FFUs.</span></span> <span data-ttu-id="1e586-188">원격 센서 프레임워크는 나침반, 자력계, 가속도계 및 자이로스코프의 드라이버를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-188">The Remote Sensor Framework installs drivers for Compass, Magnetometer, Accelerometer and Gyro.</span></span> <span data-ttu-id="1e586-189">애플리케이션에서 이러한 도구에 액세스하는 데 사용되는 UWP API는 1개만 설치된 것으로 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-189">The UWP APIs for accessing these from an application assume just 1 is installed.</span></span> <span data-ttu-id="1e586-190">물리적으로 연결되는 디바이스의 드라이버를 개발하는 경우 Microsoft에서 제공한 FFU의 원격 드라이버가 충돌합니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-190">If you are developing a driver for a physically attached device, the remote driver on the Microsoft provided FFUs will conflict.</span></span>

<span data-ttu-id="1e586-191">해결 방법: SSH 또는 Powershell을 통해 디바이스에 연결하고 devcon.exe 도구에서 “devcon.exe remove @”ROOT\REMOTESENSORDRIVER\*”를 입력하여 원격 센서 드라이버를 제거하는 방법으로 충돌하는 드라이버를 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-191">Resolution: The conflicting driver can be removed by connecting to the device via SSH or Powershell and using the tool devcon.exe to remove the remote sensor driver by typing “devcon.exe remove @”ROOT\REMOTESENSORDRIVER\*”.</span></span> <span data-ttu-id="1e586-192">원격 센서 드라이버는 OEM에서 만든 FFU에 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-192">The remote sensor driver does not affect OEM created FFUs.</span></span>


#### <a name="default-administrator-user-name-and-password"></a><span data-ttu-id="1e586-193">기본 관리자 사용자 이름 및 암호</span><span class="sxs-lookup"><span data-stu-id="1e586-193">Default Administrator User Name and Password</span></span>
<span data-ttu-id="1e586-194">기본 관리자 사용자 이름 및 암호는 Windows 10 IoT Core 이미지에 하드 코딩됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-194">The default administrator user name and password are hard coded in the Windows 10 IoT Core image.</span></span> <span data-ttu-id="1e586-195">이는 디바이스의 보안에 위험 요소로 작동하며, 암호가 변경되기 전에는 열린 인터넷 연결에 노출되면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-195">This is a security risk for the device, and it should not be exposed to an open internet connection until the password has been changed.</span></span>

#### <a name="volume-controls"></a><span data-ttu-id="1e586-196">볼륨 컨트롤</span><span class="sxs-lookup"><span data-stu-id="1e586-196">Volume Controls</span></span>
<span data-ttu-id="1e586-197">Windows 시스템을 사용하여 시스템 볼륨을 변경하는 USB 마이크 및 스피커의 시스템 볼륨 컨트롤은 현재 Windows 10 IoT Core에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-197">Hardware volume controls for USB microphones and speakers which depend on Windows system to change system volume are currently not supported on Windows 10 IoT Core.</span></span> 

#### <a name="usb-keyboards"></a><span data-ttu-id="1e586-198">USB 키보드</span><span class="sxs-lookup"><span data-stu-id="1e586-198">USB Keyboards</span></span>  
<span data-ttu-id="1e586-199">일부 USB 키보드 및 마우스는 IoT Core에서 작동하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-199">Some USB keyboards and mice may not work on IoT Core.</span></span> <span data-ttu-id="1e586-200">다른 키보드 또는 마우스를 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="1e586-200">Use a different keyboard or mouse.</span></span> <span data-ttu-id="1e586-201">검증된 주변 기기 목록은 [여기 설명서](https://docs.microsoft.com/windows/iot-core/learn-about-hardware/hardwarecompatlist)에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-201">A list of validated peripheral devices can be found in the [documentation here](https://docs.microsoft.com/windows/iot-core/learn-about-hardware/hardwarecompatlist).</span></span>


#### <a name="screen-orientation"></a><span data-ttu-id="1e586-202">화면 회전</span><span class="sxs-lookup"><span data-stu-id="1e586-202">Screen Orientation</span></span>
<span data-ttu-id="1e586-203">방향을 "세로"로 설정하는 기능이 유니버설 앱에서는 작동하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-203">Setting the orientation to “Portrait” may not be honored in a Universal App.</span></span>

#### <a name="referencing-adapters-with-alljoyn-templates"></a><span data-ttu-id="1e586-204">AllJoyn 템플릿을 사용하여 어댑터 참조</span><span class="sxs-lookup"><span data-stu-id="1e586-204">Referencing Adapters with AllJoyn Templates</span></span>
<span data-ttu-id="1e586-205">특정 SDK 버전을 사용하는 경우 AllJoyn 어댑터 프로젝트에 대한 참조를 추가하려고 하면 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-205">Attempting to add references to AllJoyn adapter projects may result in errors when using specific SDK versions.</span></span>  <span data-ttu-id="1e586-206">이 오류를 해결하려면 Visual Studio의 대상 플랫폼을 현재 SDK 버전에 맞게 변경한 다음, 프로젝트를 다시 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-206">To resolve these errors, change Visual Studio’s target platform to match the current SDK version, then reload the project.</span></span>

#### <a name="wifi-direct-limitations-on-iotcore"></a><span data-ttu-id="1e586-207">IoTCore의 WiFi Direct 제한 사항</span><span class="sxs-lookup"><span data-stu-id="1e586-207">WiFi Direct limitations on IoTCore</span></span>
* <span data-ttu-id="1e586-208">IoTCore 디바이스는 연결 디바이스여야 합니다. 연결을 시작하는 다른 디바이스와 함께 광고용 디바이스로 작동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-208">The IoTCore device has to be the connecting device – it will not work as the advertising device with another device initiating the connection.</span></span>   
* <span data-ttu-id="1e586-209">고급 페어링을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-209">Advanced pairing must be used.</span></span>  <span data-ttu-id="1e586-210">샘플 앱은 디바이스를 연결하기 전에 고급 페어링 API를 사용하여 페어링하는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-210">The sample app demonstrates how to use the advanced pairing API’s to pair the devices prior to connecting.</span></span> 
* <span data-ttu-id="1e586-211">모든 무선 어댑터가 WiFi Direct를 지원하는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-211">Not all wireless adapters support WiFi direct.</span></span> <span data-ttu-id="1e586-212">“Realtek RTL8188EU Wireless Lan 802.11n USB 2.0 네트워크 어댑터”는 정상 작동하는 것으로 테스트 결과가 나왔지만, 다른 어댑터는 지원되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-212">We have tested and validated that the “Realtek RTL8188EU Wireless Lan 802.11n USB 2.0 Network adapter” works, but other adapters may not be supported.</span></span> 


#### <a name="non-default-drive-mode"></a><span data-ttu-id="1e586-213">기본이 아닌 드라이브 모드</span><span class="sxs-lookup"><span data-stu-id="1e586-213">Non-default drive mode</span></span>
<span data-ttu-id="1e586-214">Raspberry Pi 및 Dragonboard에서, 기본이 아닌 드라이브 모드에서 기본이 아닌 다른 드라이브 모드로 전환하면 GPIO 핀에서 문제가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-214">On Raspberry Pi and Dragonboard, switching from a non-default drive mode to a different non-default drive mode may produce a glitch on the GPIO pin.</span></span> <span data-ttu-id="1e586-215">해결 방법: 애플리케이션을 시작할 때 드라이브 모드를 한 번 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-215">WORKAROUND: Set drive mode once at the beginning of the application.</span></span>

#### <a name="application-already-running"></a><span data-ttu-id="1e586-216">이미 실행 중인 애플리케이션</span><span class="sxs-lookup"><span data-stu-id="1e586-216">Application already running</span></span>
<span data-ttu-id="1e586-217">기본 시작 앱 역시 Visual Studio에서 배포하면 자체 앱과 충돌할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-217">The Default startup app may conflict with itself when it is also deployed from Visual Studio.</span></span> <span data-ttu-id="1e586-218">해결 방법: 기본 시작 앱을 배포하려는 앱이 아닌 다른 애플리케이션으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-218">WORKAROUND: Change the default startup app to an application other than that you wish to deploy.</span></span> 

#### <a name="backgroundmediaplayermessagereceivedfromforeground-may-crash"></a><span data-ttu-id="1e586-219">BackgroundMediaPlayer.MessageReceivedFromForeground가 충돌할 수 있음</span><span class="sxs-lookup"><span data-stu-id="1e586-219">BackgroundMediaPlayer.MessageReceivedFromForeground may crash</span></span>
<span data-ttu-id="1e586-220">다음 코드 줄이 충돌할 수 있습니다. “BackgroundMediaPlayer.MessageReceivedFromForeground += OnMessageReceivedFromForeground;”.</span><span class="sxs-lookup"><span data-stu-id="1e586-220">The following line of code may crash: “BackgroundMediaPlayer.MessageReceivedFromForeground += OnMessageReceivedFromForeground;”.</span></span> <span data-ttu-id="1e586-221">충돌을 방지하려면 먼저 실행되도록 “var player = BackgroundMediaPlayer.Current;” 코드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-221">To prevent the crash, add this code so that it is executed first “var player = BackgroundMediaPlayer.Current;”</span></span> 

#### <a name="azure-active-directory-authentication-support"></a><span data-ttu-id="1e586-222">Azure Active Directory 인증 지원</span><span class="sxs-lookup"><span data-stu-id="1e586-222">Azure Active Directory Authentication Support</span></span>
<span data-ttu-id="1e586-223">Azure Active Directory 인증 라이브러리는 Windows 10 IoT Core에서 작동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-223">The Azure Active Directory Authentication Library does not work on Windows 10 IoT Core.</span></span>  

#### <a name="shell-management-of-application-crashes"></a><span data-ttu-id="1e586-224">애플리케이션 충돌의 셸 관리</span><span class="sxs-lookup"><span data-stu-id="1e586-224">Shell Management of Application Crashes</span></span>
<span data-ttu-id="1e586-225">IoT Core의 셸 인프라는 디바이스에서 실행되는 APPX 형식 애플리케이션의 충돌을 모니터링하다가 충돌이 발생하면 해당 애플리케이션을 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-225">IoT Core’s shell infrastructure monitors APPX-type applications running on the device for crashes, and restarts those applications when crashes occur.</span></span>  <span data-ttu-id="1e586-226">다시 시작된 애플리케이션이 여전히 충돌하면 셸에서는 시스템 복구를 위해 버그를 확인하고 시스템을 다시 부팅하는 중요한 시스템 프로세스인 __failfast를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-226">If the restarted applications continue to crash, the shell will employ a __failfast – a system critical process that causes a bugcheck and reboot in an attempt to recover.</span></span>  <span data-ttu-id="1e586-227">헤드 구성의 백그라운드 작업과 포그라운드 애플리케이션에 비슷한 논리와 처리 방법이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-227">Comparable logic and handling is used to background tasks and foreground applications in a headed configuration.</span></span>   <span data-ttu-id="1e586-228">충돌 처리 및 재시도 논리는 아래에 캡처되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-228">Crash handing and retry logic is captured below:</span></span>

```
Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\CBTConfig  (or ForegroundAppConfig for headed) 
Qword:"FailureResetIntervalMs" – length of time app has to run successfully to reset failures seen to 0. – default is 0x00000000000493E0 == 5 minutes 
Qword:"BaseRetryDelayMs"  -- wait time coefficient.  Default is 0xa. 
Dword:"MaxFailureCount". Default is 10 
DWord:"FallbackExponentNumerator", default is 31. 
Dword:"FallbackExponentDenominator", default is 20 
Fallback_exponent = FallbackExponentNumerator / FallbackExponentDenominator; // default is 1.55 
```

<span data-ttu-id="1e586-229">앱 충돌이 감지되면 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-229">When app crash is detected:</span></span> 

```
if time_since_last_crash > failureresetinterval then crashes_seen = 1 

else ++crashes_seen; 

if crashes_seen > MaxFailureCount then __failfast; 

else  

delay = (dword) ((float)BaseRetryDelayMs * (crashes_seen ** Fallback_exponent)) 
```

<span data-ttu-id="1e586-230">시간 지연을 기다렸다가 앱 다시 시작</span><span class="sxs-lookup"><span data-stu-id="1e586-230">Wait for delay and relaunch app</span></span> 


#### <a name="time-synchronization"></a><span data-ttu-id="1e586-231">시간 동기화</span><span class="sxs-lookup"><span data-stu-id="1e586-231">Time Synchronization</span></span>  
<span data-ttu-id="1e586-232">시간 동기화가 실패하거나 시간이 초과되면 시간 서버가 멀리 떨어져 있거나 연결할 수 없는 것이 원인일 수 있습니다. 다음을 수행하여 추가 또는 로컬 시간 서버를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-232">If time sync is failing or timing out this may be due to unreachable or a distant time server, the following can be done to add additional or local time servers.</span></span> 

1) <span data-ttu-id="1e586-233">디바이스의 명령줄(예:</span><span class="sxs-lookup"><span data-stu-id="1e586-233">From a command line on the device (eg.</span></span> <span data-ttu-id="1e586-234">SSH, Powershell)에서 w32tm /config /syncfromflags:manual /manualpeerlist:"0.windows.time.com 1.pool.ntp.org 2.something else, ..."를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-234">SSH, Powershell) w32tm /config /syncfromflags:manual /manualpeerlist:"0.windows.time.com 1.pool.ntp.org 2.something else, ..."</span></span> 

2) <span data-ttu-id="1e586-235">필요한 경우 부팅 스크립트 또는 이미지 만들기 프로세스 도중에 포함된 사용자 지정 런타임 구성 패키지를 레지스트리에 추가할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-235">You may also make these additions to the registry via a boot script or a custom runtime configuration package included as part of the image creation process if needed.</span></span> <span data-ttu-id="1e586-236">자세한 내용은 다음 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1e586-236">For more details, see:</span></span> 

* <span data-ttu-id="1e586-237">[이미지에 파일 및 레지스트리 설정 추가](https://msdn.microsoft.com/library/windows/hardware/mt670641(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="1e586-237">[Adding a file and registry setting to an image](https://msdn.microsoft.com/library/windows/hardware/mt670641(v=vs.85).aspx)</span></span>


### <a name="starting-the-ftp-server"></a><span data-ttu-id="1e586-238">FTP 서버 시작</span><span class="sxs-lookup"><span data-stu-id="1e586-238">Starting the FTP Server</span></span> 
<span data-ttu-id="1e586-239">시작 시 FTP 서버가 더 이상 기본적으로 실행되지 않음</span><span class="sxs-lookup"><span data-stu-id="1e586-239">The FTP Server no longer runs by default at start-up</span></span> 

<span data-ttu-id="1e586-240">한 번만 실행하려면: SSH\PS로 로그인하여 다음 명령으로 FTP를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-240">To run once: Login with SSH\PS and run this command to start FTP:</span></span>  
```
start ftpd.exe 
```

<span data-ttu-id="1e586-241">부팅 때마다 실행하려면 사용자가 스케줄러 작업을 만들어야 합니다. SSH\PS로 로그인하여 스케줄러 작업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1e586-241">To run on every boot Users should create a scheduler task: Login with SSH\PS and create a scheduler task:</span></span> 
```
schtasks /create /tn "IoTFTPD" /tr ftpd.exe /ru system /sc onstart 
Schtasks /run /tn “IoTFTPD”
```
