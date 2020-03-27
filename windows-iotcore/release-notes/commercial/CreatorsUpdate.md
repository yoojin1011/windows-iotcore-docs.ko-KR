---
title: 크리에이터스 업데이트 - 빌드 15063
ms.date: 08/28/2017
ms.topic: article
description: 크리에이터스 업데이트의 새로운 기능을 참조하여 자세히 알아봅니다.
keywords: Windows IoT, 크리에이터스 업데이트, 릴리스 정보
ms.openlocfilehash: 09157cb634de971bfe57f549c3c87354f814f9e9
ms.sourcegitcommit: 9fb86fb605d6a8feb5c226a391045b908117a90a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80080556"
---
# <a name="creators-update-release-notes-for-windows-10-iot-core"></a><span data-ttu-id="a8e97-104">Windows 10 IoT용 크리에이터스 업데이트 릴리스 정보</span><span class="sxs-lookup"><span data-stu-id="a8e97-104">Creators Update Release Notes for Windows 10 IoT Core</span></span>
<span data-ttu-id="a8e97-105">빌드 번호 15063.</span><span class="sxs-lookup"><span data-stu-id="a8e97-105">Build Number 15063.</span></span> <span data-ttu-id="a8e97-106">2017년 4월</span><span class="sxs-lookup"><span data-stu-id="a8e97-106">April 2017</span></span>

<span data-ttu-id="a8e97-107">Windows 10 IoT Core는 임베디드 또는 전용 디바이스를 개발할 수 있도록 하며, 소형 디바이스용 Windows 솔루션을 빌드하는 OEM 및 개발자에게 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-107">Windows 10 IoT Core enables development of embedded or dedicated-purpose devices and is the choice for the OEMs and developers building Windows solutions for small devices.</span></span>

<span data-ttu-id="a8e97-108">이 문서에서는 이 Windows 10 IoT Core 릴리스에 대한 다른 내용과 설명서를 보충하는 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-108">This document provides information that supplements other content and documentation for this release of Windows 10 IoT Core.</span></span>

<span data-ttu-id="a8e97-109">이 릴리스의 패키지에는 Intel Atom 프로세서 기반 Minnowboard Max 플랫폼, ARM Cortex A7 기반 Raspberry Pi 2 및 Qualcomm Snapdragon 400 시리즈 프로세서 기반 Dragonboard 410c에 Windows 10 IoT Core를 설치하는 데 필요한 도구와 구성 요소가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-109">The packages within this release contain tools and components needed to install Windows 10 IoT Core on Minnowboard Max platform based on Intel Atom processers, Raspberry Pi 2 based on ARM Cortex A7, and Dragonboard 410c based on Qualcomm Snapdragon 400 series processors.</span></span>   

<span data-ttu-id="a8e97-110">[다른 플랫폼 및 프로세서](../../learn-about-hardware/SoCsAndCustomBoards.md)는 파트너에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-110">[Other platforms and processors](../../learn-about-hardware/SoCsAndCustomBoards.md) may be available from partners.</span></span>

## <a name="privacy-statement"></a><span data-ttu-id="a8e97-111">개인 정보 취급 방침</span><span class="sxs-lookup"><span data-stu-id="a8e97-111">Privacy Statement</span></span>

<span data-ttu-id="a8e97-112">이 Windows 운영 체제 버전의 개인정보처리방침은 [여기](https://go.microsoft.com/fwlink/?LinkId=506737)서 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-112">The privacy statement for this version of the Windows operating system can be viewed [here](https://go.microsoft.com/fwlink/?LinkId=506737).</span></span>

## <a name="whats-new"></a><span data-ttu-id="a8e97-113">새로운 기능</span><span class="sxs-lookup"><span data-stu-id="a8e97-113">What's New</span></span>
* <span data-ttu-id="a8e97-114">Windows 10 IoT Core 퍼블릭 릴리스</span><span class="sxs-lookup"><span data-stu-id="a8e97-114">Windows 10 IoT Core Public Release.</span></span> 
   * <span data-ttu-id="a8e97-115">Azure 디바이스 관리 지원 - OEM에서 Windows IoT Azure DM 클라이언트 라이브러리를 사용하여 디바이스 관리 기능을 Azure IoT 허브에 연결된 디바이스에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-115">Azure Device Management Support - OEMs can use the Windows IoT Azure DM client library to add device management capabilities to their Azure IoT hub connected devices.</span></span>
   * <span data-ttu-id="a8e97-116">추가 실리콘 지원</span><span class="sxs-lookup"><span data-stu-id="a8e97-116">Additional Silicon Support</span></span>
      * <span data-ttu-id="a8e97-117">Intel Joule, Intel Pentium N4200, Intel Celeron N3350, 예정된 Atom x5-E39xx 프로세서(이전의 Apollo Lake) 및 Raspberry Pi 3 SOM에 대한 Windows 10 IoT Core 지원이 확인되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-117">Verified support for Windows 10 IoT Core on Intel Joule, Intel Pentium N4200, Intel Celeron N3350, upcoming Atom x5-E39xx processors (formerly Apollo Lake) and Raspberry Pi 3 SOMs.</span></span>
      * <span data-ttu-id="a8e97-118">Allwinner는 Allwinner A64 SoC를 사용하여 Pine 64 및 Banana Pi 디바이스를 지원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-118">Allwinner has enabled support for their Pine 64 and Banana Pi devices using the Allwinner A64 SoC.</span></span> 
   * <span data-ttu-id="a8e97-119">원격 디바이스 검색 - Microsoft 계정으로 로그인한 디바이스를 검색하는 데 특별한 소프트웨어가 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-119">Discovering your Remote Devices - No special software is needed to discover your devices that are signed in with your Microsoft Account.</span></span>
   * <span data-ttu-id="a8e97-120">진동, 밝기, 최신 연결된 대기 상태, 전원 관리, 배터리 충전 및 NFC(HCE 없음)에 대한 UWP API 및 컨트롤이 새로 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-120">New UWP APIs And controls for vibration, brightness, modern connected standby, power management, battery charge  and NFC (w/o HCE).</span></span> 
   * <span data-ttu-id="a8e97-121">ARM PCIe, USB 기능 모드, Wi-Fi Direct 및 GPIO 인터럽트 계산 API에 대한 버스와 기능이 새로 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-121">New busses and capabilities for ARM PCIe, USB function mode, Wi-Fi Direct and  GPIO interrupt counting API.</span></span> 
   * <span data-ttu-id="a8e97-122">다시 설정/복구, On-SOC PWM 및 자동 USB 프로비저닝에 대한 포함 기능이 새로 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-122">New Embedded features on Reset/Recovery, On-SOC PWM and Automatic USB provisioning</span></span> 
   * <span data-ttu-id="a8e97-123">향상된 도구 - VS Code, 새 Windows 디바이스 포털 및 IoT 대시보드 기능, VS 2017 지원</span><span class="sxs-lookup"><span data-stu-id="a8e97-123">Improved Tools - VS Code, New Windows Device Portal and IoT Dashboard features, VS 2017 support.</span></span>
   * <span data-ttu-id="a8e97-124">Windows IoT Core의 Cortana - Cortana는 이제 Windows 10 IoT Core에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-124">Cortana on Windows IoT Core - Cortana is now available on Windows 10 IoT Core.</span></span> <span data-ttu-id="a8e97-125">Cortana에 문의하세요.</span><span class="sxs-lookup"><span data-stu-id="a8e97-125">Ask Cortana a question.</span></span>
   * <span data-ttu-id="a8e97-126">향상된 IoT 대시보드 - 새로운 기능 및 안정성 버그 수정</span><span class="sxs-lookup"><span data-stu-id="a8e97-126">IoT Dashboard Improvements - New features and stability bug fixes</span></span>
      * <span data-ttu-id="a8e97-127">Windows Insider Preview 빌드(Raspberry Pi 및 Minnowboard용)</span><span class="sxs-lookup"><span data-stu-id="a8e97-127">Windows Insider Preview builds for Raspberry Pi and Minnowboard</span></span> 
      * <span data-ttu-id="a8e97-128">Windows IoT 원격 클라이언트를 사용하여 디바이스 연결</span><span class="sxs-lookup"><span data-stu-id="a8e97-128">Connecting device using Windows IoT Remote Client</span></span> 
      * <span data-ttu-id="a8e97-129">디바이스 검색의 Ipv6 주소</span><span class="sxs-lookup"><span data-stu-id="a8e97-129">Ipv6 addresses in discovering devices</span></span> 
      * <span data-ttu-id="a8e97-130">피드백을 제출하는 동안 디바이스 로그 업로드</span><span class="sxs-lookup"><span data-stu-id="a8e97-130">Uploading device logs while submitting feedback</span></span>
   *  <span data-ttu-id="a8e97-131">새 고정밀 GPIO API - GPIO 인터럽트를 사용하여 펄스 너비를 정확하고 효율적으로 측정하는 새 API(Windows.Devices.Gpio.GpioInterruptBuffer)입니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-131">New high precision GPIO APIs -  New APIs (Windows.Devices.Gpio.GpioInterruptBuffer) for precise and efficient measurement of pulse widths using GPIO interrupts.</span></span><span data-ttu-id="a8e97-132">  GPIO 공급자에는 회전식 인코더 및 거리 측정 디바이스와 같이 높은 고정밀 인터럽트 타이밍을 애플리케이션에 허용하는 새 인터럽트 버퍼 인터페이스가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-132">  GPIO providers include new Interrupt Buffer interface to allow for high precision interrupt timing for applications like rotary encoders and distance measuring devices</span></span>
   * <span data-ttu-id="a8e97-133">IoT용 Device Guard - 디바이스 작성기는 이제 IoT 디바이스를 완전히 잠그고 새롭거나 알 수 없는 맬웨어 변형으로부터 고급 맬웨어를 보호할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-133">Device Guard for IoT - Device builders can now fully lock down IoT devices and get advanced malware protection against new and unknown malware variants.</span></span><span data-ttu-id="a8e97-134">  이 작업은 알 수 없거나 신뢰할 수 없는 코드를 실행하도록 허용하지 않으면서 디바이스에서 실행되는 허용 가능한 애플리케이션 및 드라이버에 대한 서명 권한을 지정하여 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-134">  This can be done by specifying signing authorities for permissible applications and drivers that run on the device while disallowing execution of unknown or untrusted code.</span></span><span data-ttu-id="a8e97-135">  즉, 맬웨어 및 제로 데이 공격에 대한 보안이 향상되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-135">  This means improved security against malware and zero day attacks.</span></span> 
   * <span data-ttu-id="a8e97-136">기타 업데이트는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-136">Other updates include:</span></span> 
      * <span data-ttu-id="a8e97-137">향상된 업데이트 지원</span><span class="sxs-lookup"><span data-stu-id="a8e97-137">Improved Update Support</span></span> 
      * <span data-ttu-id="a8e97-138">Azure 게이트웨이 SDK 지원</span><span class="sxs-lookup"><span data-stu-id="a8e97-138">Azure Gateway SDK support</span></span> 
      * <span data-ttu-id="a8e97-139">USB 드라이브 기반 자동 프로비저닝</span><span class="sxs-lookup"><span data-stu-id="a8e97-139">USB drive based auto-provisioning</span></span> 
      * <span data-ttu-id="a8e97-140">디바이스 포털 재설계</span><span class="sxs-lookup"><span data-stu-id="a8e97-140">Device Portal redesign</span></span> 
      * <span data-ttu-id="a8e97-141">64비트 이미지 - 이제 최대 16,384MB 메모리를 지원함</span><span class="sxs-lookup"><span data-stu-id="a8e97-141">64-bit images now supports up to 16,384 MB of memory</span></span> 
      * <span data-ttu-id="a8e97-142">WinRT 진동 API</span><span class="sxs-lookup"><span data-stu-id="a8e97-142">WinRT Vibration APIs</span></span> 
      * <span data-ttu-id="a8e97-143">향상된 언어 지원</span><span class="sxs-lookup"><span data-stu-id="a8e97-143">Improved language support</span></span> 
   * <span data-ttu-id="a8e97-144">기타</span><span class="sxs-lookup"><span data-stu-id="a8e97-144">Miscellaneous</span></span>  
      * <span data-ttu-id="a8e97-145">복구 모드가 없는 경우 디바이스에서 복구 모드로 부팅하지 못하도록 기본 BCD 설정이 변경되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-145">A change has been made to the default BCD settings to prevent devices from attempting to boot to recovery mode when recovery mode does not exist.</span></span> 
      * <span data-ttu-id="a8e97-146">이제 powercfg.exe가 IOT_POWER_SETTINGS 기능에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-146">IOT_POWER_SETTINGS feature now includes powercfg.exe.</span></span> <span data-ttu-id="a8e97-147">이는 모든 아키텍처(ARM32, x86 및 x64)에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-147">This is available for all architectures (ARM32, x86 and x64).</span></span> 
      * <span data-ttu-id="a8e97-148">blockrebooton/blockrebootoff 플래그를 추가하도록 Applyupdate.exe가 변경되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-148">Changes were made to Applyupdate.exe to add the blockrebooton/blockrebootoff flags</span></span> 
      * <span data-ttu-id="a8e97-149">하드웨어 알림(hwnclx) 및 USB 함수(usbfnclx)에 대한 클래스 확장이 기본 IoT Core 이미지에 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-149">The Class Extensions for Hardware Notification (hwnclx) and USB Function (usbfnclx) have been added to the default IoT Core images</span></span>

## <a name="known-issues"></a><span data-ttu-id="a8e97-150">알려진 문제</span><span class="sxs-lookup"><span data-stu-id="a8e97-150">Known Issues</span></span>

### <a name="raspberry-pi"></a><span data-ttu-id="a8e97-151">Raspberry Pi</span><span class="sxs-lookup"><span data-stu-id="a8e97-151">Raspberry Pi</span></span>  

#### <a name="raspberry-pi-display-resolution-if-monitor-is-disconnected"></a><span data-ttu-id="a8e97-152">모니터 연결이 끊어진 경우 Raspberry Pi 디스플레이 해상도</span><span class="sxs-lookup"><span data-stu-id="a8e97-152">Raspberry Pi Display Resolution if monitor is disconnected</span></span> 
<span data-ttu-id="a8e97-153">모니터 연결이 끊어진 경우 Raspberry Pi가 디스플레이 해상도를 유지하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-153">The Raspberry Pi may not maintain Display Resolution if monitor is disconnected.</span></span> <span data-ttu-id="a8e97-154">시스템이 연결되는 경우 모니터의 EDID를 사용하여 시스템의 해상도를 설정합니다.  </span><span class="sxs-lookup"><span data-stu-id="a8e97-154">The EDID of the monitor is used to set the resolution of the system when one is connected.  </span></span>
<span data-ttu-id="a8e97-155">연결이 끊어지면 Raspberry Pi 펌웨어는 SD 카드의 루트에 있는 config.txt를 기본값으로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-155">When disconnected, the Raspberry Pi firmware defaults to what is in the config.txt in the root of the SD card.</span></span> 

#### <a name="raspberry-pi-video-performance"></a><span data-ttu-id="a8e97-156">Raspberry Pi 비디오 성능</span><span class="sxs-lookup"><span data-stu-id="a8e97-156">Raspberry Pi Video Performance</span></span> 
<span data-ttu-id="a8e97-157">Raspberry Pi 플랫폼의 비디오 재생 성능이 최적화되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-157">Video playback performance on the Raspberry Pi platform has not been optimized.</span></span><span data-ttu-id="a8e97-158">  XAML 기반 드롭다운 메뉴를 비롯한 애니메이션 사용자 요소가 최적화된 성능을 발휘하지 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-158">  Animated user elements including XAML-based dropdown menus may exhibit less than optimal performance.</span></span> 

#### <a name="raspberry-pi-camera-support"></a><span data-ttu-id="a8e97-159">Raspberry Pi 카메라 지원</span><span class="sxs-lookup"><span data-stu-id="a8e97-159">Raspberry Pi Camera Support</span></span> 
<span data-ttu-id="a8e97-160">Raspberry Pi 디바이스가 있는 카메라 주변 장치에 대한 Windows 10 IoT Core 지원이 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-160">Windows 10 IoT Core support for camera peripheral devices with Raspberry Pi devices is limited.</span></span> <span data-ttu-id="a8e97-161">DirectX 드라이버가 구현되지 않아 현재 Raspberry Pi에서 사용할 수 없는 GPU 서비스가 필요하므로 온보드 카메라 버스에 직접 연결된 PiCam 디바이스는 현재 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-161">The PiCam device directly connected to the onboard camera bus is not currently supported, as it requires GPU services that are not currently available on the Raspberry Pi because the DirectX driver is not implemented.</span></span> <span data-ttu-id="a8e97-162">최신 USB 웹캠은 USB 호스트 컨트롤러에서 매우 까다로운 데이터 스트림을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-162">Modern USB webcams produce data streams that are very demanding on the USB Host controller.</span></span><span data-ttu-id="a8e97-163">  저해상도 설정으로 사용하더라도 웹캠에서 USB를 미세 조정해야 하며 특수한 제어 논리가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-163">  Even when used with low resolution settings webcams will require additional USB fine tuning and specialized control logic.</span></span>  

#### <a name="raspberry-pi-3-bluetooth-support"></a><span data-ttu-id="a8e97-164">Raspberry Pi 3 Bluetooth 지원</span><span class="sxs-lookup"><span data-stu-id="a8e97-164">Raspberry Pi 3 Bluetooth support</span></span> 
<span data-ttu-id="a8e97-165">Raspberry Pi3 기본 제공 Bluetooth 드라이버는 낮은 대역폭 디바이스만 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-165">The Raspberry Pi3 built-in Bluetooth driver only supports low bandwidth devices</span></span>  

#### <a name="serial-port-usage-and-access-on-raspberry-pi-2"></a><span data-ttu-id="a8e97-166">Raspberry Pi 2의 직렬 포트 사용 및 액세스</span><span class="sxs-lookup"><span data-stu-id="a8e97-166">Serial Port Usage and Access on Raspberry Pi 2</span></span> 
<span data-ttu-id="a8e97-167">Raspberry Pi 2는 PL011 UART을 통해 통신에 대한 직렬 전송을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-167">Raspberry Pi 2 supports the serial transport for communication through the PL011 UART.</span></span><span data-ttu-id="a8e97-168">  이는 커널 디버깅 시나리오에서 기본적으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-168">  This is set by default in kernel debugging scenarios.</span></span><span data-ttu-id="a8e97-169">  애플리케이션 또는 디바이스 드라이버는 PL011 UART를 사용하여 다음 명령으로 디버거를 끄는 PL011 디바이스 드라이버와 데이터를 보내고 받을 수 있습니다.   
`bcedit /set debug off`</span><span class="sxs-lookup"><span data-stu-id="a8e97-169">  An application or device driver can use the PL011 UART to send and receive data with the PL011 device driver turning off the debugger using the following command:   
`bcedit /set debug off`</span></span> 
 
### <a name="dragon-board"></a><span data-ttu-id="a8e97-170">DragonBoard</span><span class="sxs-lookup"><span data-stu-id="a8e97-170">Dragon Board</span></span> 

#### <a name="dragonboard-410c-shutdown"></a><span data-ttu-id="a8e97-171">Dragonboard 410c 종료</span><span class="sxs-lookup"><span data-stu-id="a8e97-171">Dragonboard 410c Shutdown</span></span> 
<span data-ttu-id="a8e97-172">DragonBoard에서 종료 명령을 실행해도 보드 전원이 꺼지지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-172">On the DragonBoard, a shutdown command will not power off the board.</span></span> <span data-ttu-id="a8e97-173">시스템이 다시 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-173">The system will restart.</span></span> <span data-ttu-id="a8e97-174">전원을 차단하여 보드를 끄세요.</span><span class="sxs-lookup"><span data-stu-id="a8e97-174">Please power off the board by disconnecting the power.</span></span> 

#### <a name="dragon-board-headset--microphone-jack"></a><span data-ttu-id="a8e97-175">DragonBoard 헤드셋 및 마이크 잭</span><span class="sxs-lookup"><span data-stu-id="a8e97-175">Dragon Board headset & microphone jack</span></span>  
<span data-ttu-id="a8e97-176">Dragonboard BSP에는 헤드셋 잭과 마이크 잭의 드라이버가 있지만, 둘 중 어느 잭도 보드에 통합되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-176">The Dragonboard BSP has drivers for the headset jack and microphone jack, but it doesn't have either of these jacks on board.</span></span>  

#### <a name="dragonboard-spi-runs-at-lock-speed"></a><span data-ttu-id="a8e97-177">잠금 속도로 실행되는 Dragonboard SPI</span><span class="sxs-lookup"><span data-stu-id="a8e97-177">Dragonboard SPI runs at lock speed</span></span>  
<span data-ttu-id="a8e97-178">Dragonboard의 SPI는 요청된 속도를 무시하고 항상 미리 구성된 속도로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-178">The SPI on the Dragonboard will ignore the requested speed and always run at a preconfigured speed.</span></span>  

#### <a name="dragonboard-connected-standby"></a><span data-ttu-id="a8e97-179">Dragonboard 연결된 대기 상태</span><span class="sxs-lookup"><span data-stu-id="a8e97-179">Dragonboard Connected Standby</span></span> 
<span data-ttu-id="a8e97-180">연결된 대기 상태는 Qualcomm Dragonboard에서 기본적으로 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-180">Connected Standby is not enabled on the Qualcomm Dragonboard by default.</span></span><span data-ttu-id="a8e97-181">  DragonBoard에서 연결된 대기 상태를 사용하도록 설정하려면 다음 레지스트리 키를 "1"로 설정해야 합니다. 
</span><span class="sxs-lookup"><span data-stu-id="a8e97-181">  To enable Connected Standby on DragonBoard the following registry key needs to be set to “1” 
</span></span><br>
`HKLM\System\Controlset001\Control\Power\CsEnabled=DWORD:1`
<br>
<span data-ttu-id="a8e97-182">모든 플랫폼에서 CS를 지원하는 것은 아니므로 다른 플랫폼에서는 작동하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-182">Note that not all platforms have support for CS, so this may not work on other platforms.</span></span>    

#### <a name="vibration-api-may-not-function-on-some-qualcomm-platforms"></a><span data-ttu-id="a8e97-183">일부 Qualcomm 플랫폼에서 진동 API가 작동하지 않을 수 있음</span><span class="sxs-lookup"><span data-stu-id="a8e97-183">Vibration API may not function on some Qualcomm platforms</span></span> 
<span data-ttu-id="a8e97-184">제안되는 해결 방법은 다음 레지스트리 키를 추가하는 것입니다. 
</span><span class="sxs-lookup"><span data-stu-id="a8e97-184">The suggested workaround is to add the following registry key: 
</span></span><br>
`[HKEY_LOCAL_MACHINE\SYSTEM\controlset001\services\hwnhaptics]` 
<br>
`"EnableOemSecurity"=dword:00000001 `
<br>
<span data-ttu-id="a8e97-185">기존 이미지를 확인/증명하기 위해 SSH 또는 PowerShell에 연결하고 다음 명령을 실행합니다. 
</span><span class="sxs-lookup"><span data-stu-id="a8e97-185">For confirmation / verification on an existing image connect with SSH or PowerShell and run the following command: 
</span></span><br>
`reg add HKEY_LOCAL_MACHINE\SYSTEM\controlset001\services\hwnhaptics /t REG_DWORD /v EnableOemSecurity /d 1 `

### <a name="minnowboard"></a><span data-ttu-id="a8e97-186">MinnowBoard</span><span class="sxs-lookup"><span data-stu-id="a8e97-186">MinnowBoard</span></span>  

#### <a name="minnowboard-max-firmware-update"></a><span data-ttu-id="a8e97-187">Minnowboard Max 펌웨어 업데이트</span><span class="sxs-lookup"><span data-stu-id="a8e97-187">Minnowboard Max Firmware Update</span></span> 
<span data-ttu-id="a8e97-188">펌웨어 버전이 0.92 이상인 경우에만 MinnowBoard Max가 부팅됩니다.  </span><span class="sxs-lookup"><span data-stu-id="a8e97-188">The MinnowBoard Max will not boot unless the firmware is version 0.92 or later.  </span></span>
<span data-ttu-id="a8e97-189">MBM(MinnowBoard Max) 펌웨어 버전 0.93에는 네트워크 연결 오류가 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-189">There may be network connectivity failures in MinnowBoard Max (MBM) firmware version 0.93.</span></span><span data-ttu-id="a8e97-190">   이 문제는 펌웨어 버전 0.94에서 해결되었습니다.  추천되는 최소 펌웨어 버전은 "MinnowBoard MAX 0.94 32비트"입니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-190">   The issue is fixed in firmware version 0.94.)  The minimum recommended version of the firmware is “MinnowBoard MAX 0.94 32-bit”.</span></span> <span data-ttu-id="a8e97-191">펌웨어 업데이트는  [여기](https://go.microsoft.com/fwlink/?LinkId=708613)서 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-191">Firmware updates can be downloaded from [here](https://go.microsoft.com/fwlink/?LinkId=708613).</span></span>
  
 
### <a name="all-platforms"></a><span data-ttu-id="a8e97-192">모든 플랫폼</span><span class="sxs-lookup"><span data-stu-id="a8e97-192">All Platforms</span></span> 

#### <a name="mouse-pointer-disappears-while-debugging"></a><span data-ttu-id="a8e97-193">디버깅하는 동안 사라지는 마우스 포인터</span><span class="sxs-lookup"><span data-stu-id="a8e97-193">Mouse Pointer disappears while debugging</span></span> 
<span data-ttu-id="a8e97-194">경우에 따라 Visual Studio를 사용하여 앱을 배포하거나 디버그한 후에 마우스 포인터가 표시되지 않을 때 키보드(탭 키)를 사용하여 포커스를 변경하면 마우스 포인터가 다시 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-194">In some cases, the mouse pointer is not visible after deploying or debugging apps with Visual Studio, the mouse pointer should reappear if you change focus using the keyboard (Tab)</span></span>  

#### <a name="server-applications-with-softap"></a><span data-ttu-id="a8e97-195">SoftAP를 사용하는 서버 애플리케이션</span><span class="sxs-lookup"><span data-stu-id="a8e97-195">Server Applications with SoftAP</span></span>  
<span data-ttu-id="a8e97-196">SoftAP를 사용하면 클라이언트가 UAP 앱에서 공개하는 콘텐츠에 액세스할 수 없습니다.  </span><span class="sxs-lookup"><span data-stu-id="a8e97-196">When using the SoftAP clients will not be able to access content exposed by UAP apps.  </span></span>
<span data-ttu-id="a8e97-197">SoftAP를 통해 UAP 애플리케이션을 공개하려면 디바이스의 콘솔에서 다음과 같이 변경해야 합니다.  
</span><span class="sxs-lookup"><span data-stu-id="a8e97-197">To expose UAP applications via SoftAP the following changes must be made from the console on the device :  
</span></span><br>
`reg add hklm\system\currentcontrolset\services\mpssvc\parameters /v IoTInboundLoopbackPolicy /t REG_DWORD /d 1 `
<br>
`checknetisolation loopbackexempt -a -n=<AppID for SoftAP App>`
<br>
`checknetisolation loopbackexempt -a -n=<AppID for Additional App> `
<br>
`For example:  checknetisolation loopbackexempt -a -n=IoTOnboardingTask-uwp_1w720vyc4ccym`
<br>
`Reboot`

#### <a name="sensor-driver-conflict-in-pre-built-ffus"></a><span data-ttu-id="a8e97-198">미리 빌드된 FFU의 센서 드라이버 충돌</span><span class="sxs-lookup"><span data-stu-id="a8e97-198">Sensor Driver conflict in pre-built FFUs</span></span> 
<span data-ttu-id="a8e97-199">제공된 FFU의 센서 드라이버가 충돌합니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-199">There is a Sensor Driver Conflict in the provided FFUs.</span></span> <span data-ttu-id="a8e97-200">원격 센서 프레임워크는 나침반, 자력계, 가속도계 및 자이로스코프의 드라이버를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-200">The Remote Sensor Framework installs drivers for Compass, Magnetometer, Accelerometer and Gyro.</span></span> <span data-ttu-id="a8e97-201">애플리케이션에서 이러한 도구에 액세스하는 데 사용되는 UWP API는 1개만 설치된 것으로 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-201">The UWP APIs for accessing these from an application assume just 1 is installed.</span></span> <span data-ttu-id="a8e97-202">물리적으로 연결되는 디바이스의 드라이버를 개발하는 경우 Microsoft에서 제공한 FFU의 원격 드라이버가 충돌합니다.  </span><span class="sxs-lookup"><span data-stu-id="a8e97-202">If you are developing a driver for a physically attached device, the remote driver on the Microsoft provided FFUs will conflict.  </span></span>
<span data-ttu-id="a8e97-203">해상도: SSH 또는 PowerShell을 통해 디바이스에 연결하고 devcon.exe 도구에서 "devcon.exe remove @"ROOT\REMOTESENSORDRIVER\*"를 입력하여 원격 센서 드라이버를 제거함으로써 충돌하는 드라이버를 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-203">Resolution: The conflicting driver can be removed by connecting to the device via SSH or PowerShell and using the tool devcon.exe to remove the remote sensor driver by typing “devcon.exe remove @”ROOT\REMOTESENSORDRIVER\*”.</span></span> <span data-ttu-id="a8e97-204">원격 센서 드라이버는 OEM에서 만든 FFU에 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-204">The remote sensor driver does not affect OEM created FFUs.</span></span> 
 
#### <a name="default-administrator-user-name-and-password"></a><span data-ttu-id="a8e97-205">기본 관리자 사용자 이름 및 암호</span><span class="sxs-lookup"><span data-stu-id="a8e97-205">Default Administrator User Name and Password</span></span> 
<span data-ttu-id="a8e97-206">기본 관리자 사용자 이름 및 암호는 Windows 10 IoT Core 이미지에 하드 코딩됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-206">The default administrator user name and password are hard coded in the Windows 10 IoT Core image.</span></span> <span data-ttu-id="a8e97-207">이는 디바이스의 보안에 위험 요소로 작동하며, 암호가 변경되기 전에는 열린 인터넷 연결에 노출되면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-207">This is a security risk for the device, and it should not be exposed to an open internet connection until the password has been changed.</span></span> 
 
#### <a name="volume-controls"></a><span data-ttu-id="a8e97-208">볼륨 컨트롤</span><span class="sxs-lookup"><span data-stu-id="a8e97-208">Volume Controls</span></span> 
<span data-ttu-id="a8e97-209">Windows 시스템을 사용하여 시스템 볼륨을 변경하는 USB 마이크 및 스피커의 시스템 볼륨 컨트롤은 현재 Windows 10 IoT Core에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-209">Hardware volume controls for USB microphones and speakers which depend on Windows system to change system volume are currently not supported on Windows 10 IoT Core.</span></span> 
 
#### <a name="usb-keyboards"></a><span data-ttu-id="a8e97-210">USB 키보드</span><span class="sxs-lookup"><span data-stu-id="a8e97-210">USB Keyboards</span></span>  
<span data-ttu-id="a8e97-211">일부 USB 키보드 및 마우스는 IoT Core에서 작동하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-211">Some USB keyboards and mice may not work on IoT Core.</span></span> <span data-ttu-id="a8e97-212">다른 키보드 또는 마우스를 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="a8e97-212">Use a different keyboard or mouse.</span></span> <span data-ttu-id="a8e97-213">유효성이 검사된 주변 장치의 목록은 [여기](../../learn-about-hardware/HardwareCompatList.md)서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-213">A list of validated peripheral devices can be found [here](../../learn-about-hardware/HardwareCompatList.md).</span></span>  
 
#### <a name="screen-orientation"></a><span data-ttu-id="a8e97-214">화면 회전</span><span class="sxs-lookup"><span data-stu-id="a8e97-214">Screen Orientation</span></span> 
<span data-ttu-id="a8e97-215">방향을 "세로"로 설정하는 것은 유니버설 앱에서 허용되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-215">Setting the orientation to “Portrait” may not be honored in a Universal App</span></span> 
 
#### <a name="referencing-adapters-with-alljoyn-templates"></a><span data-ttu-id="a8e97-216">AllJoyn 템플릿을 사용하여 어댑터 참조</span><span class="sxs-lookup"><span data-stu-id="a8e97-216">Referencing Adapters with AllJoyn Templates</span></span> 
<span data-ttu-id="a8e97-217">특정 SDK 버전을 사용하는 경우 AllJoyn 어댑터 프로젝트에 대한 참조를 추가하려고 하면 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-217">Attempting to add references to AllJoyn adapter projects may result in errors when using specific SDK versions.</span></span><span data-ttu-id="a8e97-218">  이 오류를 해결하려면 Visual Studio의 대상 플랫폼을 현재 SDK 버전에 맞게 변경한 다음, 프로젝트를 다시 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-218">  To resolve these errors, change Visual Studio’s target platform to match the current SDK version, then reload the project.</span></span> 

#### <a name="non-default-drive-mode"></a><span data-ttu-id="a8e97-219">기본이 아닌 드라이브 모드</span><span class="sxs-lookup"><span data-stu-id="a8e97-219">Non-default drive mode</span></span>  
<span data-ttu-id="a8e97-220">Raspberry Pi 및 Dragonboard에서, 기본이 아닌 드라이브 모드에서 기본이 아닌 다른 드라이브 모드로 전환하면 GPIO 핀에서 문제가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-220">On Raspberry Pi and Dragonboard, switching from a non-default drive mode to a different non-default drive mode may produce a glitch on the GPIO pin.</span></span> <span data-ttu-id="a8e97-221">해결 방법: 애플리케이션을 시작할 때 드라이브 모드를 한 번 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-221">WORKAROUND: Set drive mode once at the beginning of the application.</span></span> 
 
#### <a name="application-already-running"></a><span data-ttu-id="a8e97-222">이미 실행 중인 애플리케이션</span><span class="sxs-lookup"><span data-stu-id="a8e97-222">Application already running</span></span>  
<span data-ttu-id="a8e97-223">기본 시작 앱 역시 Visual Studio에서 배포하면 자체 앱과 충돌할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-223">The Default startup app may conflict with itself when it is also deployed from Visual Studio.</span></span> <span data-ttu-id="a8e97-224">해결 방법: 기본 시작 앱을 배포하려는 앱이 아닌 다른 애플리케이션으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-224">WORKAROUND: Change the default startup app to an application other than that you wish to deploy.</span></span> 
 
#### <a name="backgroundmediaplayermessagereceivedfromforeground-may-crash"></a><span data-ttu-id="a8e97-225">BackgroundMediaPlayer.MessageReceivedFromForeground가 충돌할 수 있음</span><span class="sxs-lookup"><span data-stu-id="a8e97-225">BackgroundMediaPlayer.MessageReceivedFromForeground may crash</span></span>  
<span data-ttu-id="a8e97-226">다음 코드 줄의 작동이 중단될 수 있습니다.`BackgroundMediaPlayer.MessageReceivedFromForeground += OnMessageReceivedFromForeground;`</span><span class="sxs-lookup"><span data-stu-id="a8e97-226">The following line of code may crash: `BackgroundMediaPlayer.MessageReceivedFromForeground += OnMessageReceivedFromForeground;`.</span></span>
<br>
<span data-ttu-id="a8e97-227">작동 중단을 방지하려면 먼저 실행되도록 다음 코드를 추가합니다.`var player = BackgroundMediaPlayer.Current;`</span><span class="sxs-lookup"><span data-stu-id="a8e97-227">To prevent the crash, add this code so that it is executed first `var player = BackgroundMediaPlayer.Current;`</span></span> 
 
#### <a name="azure-active-directory-authentication-support"></a><span data-ttu-id="a8e97-228">Azure Active Directory 인증 지원</span><span class="sxs-lookup"><span data-stu-id="a8e97-228">Azure Active Directory Authentication Support</span></span>  
<span data-ttu-id="a8e97-229">Azure Active Directory 인증 라이브러리는 Windows 10 IoT Core에서 작동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-229">The Azure Active Directory Authentication Library does not work on Windows 10 IoT Core.</span></span>  
 
#### <a name="shell-management-of-application-crashes"></a><span data-ttu-id="a8e97-230">애플리케이션 충돌의 셸 관리</span><span class="sxs-lookup"><span data-stu-id="a8e97-230">Shell Management of Application Crashes</span></span> 
<span data-ttu-id="a8e97-231">IoT Core의 셸 인프라는 디바이스에서 실행되는 APPX 형식 애플리케이션의 충돌을 모니터링하다가 충돌이 발생하면 해당 애플리케이션을 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-231">IoT Core’s shell infrastructure monitors APPX-type applications running on the device for crashes, and restarts those applications when crashes occur.</span></span><span data-ttu-id="a8e97-232">  다시 시작된 애플리케이션의 작동이 여전히 중단되면 셸에서 __failfast를 사용합니다. 이는 복구를 위해 버그를 검사하고 다시 부팅하는 중요한 시스템 프로세스입니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-232">  If the restarted applications continue to crash, the shell will employ a __failfast – a system critical process that causes a bug check and reboot in an attempt to recover.</span></span><span data-ttu-id="a8e97-233">  헤드 구성의 백그라운드 작업과 포그라운드 애플리케이션에 비슷한 논리와 처리 방법이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-233">  Comparable logic and handling is used to background tasks and foreground applications in a headed configuration.</span></span>   

<span data-ttu-id="a8e97-234">충돌 처리 및 재시도 논리는 아래에 캡처되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-234">Crash handing and retry logic is captured below:</span></span> 

<span data-ttu-id="a8e97-235">Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\CBTConfig(또는 헤드 구성의 경우 ForegroundAppConfig)</span><span class="sxs-lookup"><span data-stu-id="a8e97-235">Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\CBTConfig  (or ForegroundAppConfig for headed)</span></span> 
* <span data-ttu-id="a8e97-236">Qword:"FailureResetIntervalMs" – 앱을 성공적으로 실행하여 0으로 표시되는 오류를 다시 설정해야 하는 기간입니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-236">Qword:"FailureResetIntervalMs" – length of time app has to run successfully to reset failures seen to 0.</span></span> <span data-ttu-id="a8e97-237">– 기본값은 0x00000000000493E0 == 5분입니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-237">– default is 0x00000000000493E0 == 5 minutes.</span></span> 
* <span data-ttu-id="a8e97-238">Qword:"BaseRetryDelayMs"  -- 대기 시간 계수입니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-238">Qword:"BaseRetryDelayMs"  -- wait time coefficient.</span></span><span data-ttu-id="a8e97-239">  기본값은 0xa입니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-239">  Default is 0xa.</span></span>
* <span data-ttu-id="a8e97-240">Dword:"MaxFailureCount".</span><span class="sxs-lookup"><span data-stu-id="a8e97-240">Dword:"MaxFailureCount".</span></span> <span data-ttu-id="a8e97-241">기본값은 10입니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-241">Default is 10.</span></span>
* <span data-ttu-id="a8e97-242">DWord:"FallbackExponentNumerator", 기본값은 31입니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-242">DWord:"FallbackExponentNumerator", default is 31.</span></span>
* <span data-ttu-id="a8e97-243">Dword:"FallbackExponentDenominator", 기본값은 20입니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-243">Dword:"FallbackExponentDenominator", default is 20.</span></span>
 
```C#
Fallback_exponent = FallbackExponentNumerator / FallbackExponentDenominator;
// default is 1.55
When app crash is detected:
    if time_since_last_crash > failureresetinterval then crashes_seen = 1
    else ++crashes_seen;

if crashes_seen > MaxFailureCount then __failfast;

else

delay = (dword) ((float)BaseRetryDelayMs * (crashes_seen ** Fallback_exponent))
// wait for delay and relaunch app
```
 
#### <a name="time-synchronization"></a><span data-ttu-id="a8e97-244">시간 동기화</span><span class="sxs-lookup"><span data-stu-id="a8e97-244">Time Synchronization</span></span>  
<span data-ttu-id="a8e97-245">시간 동기화가 실패하거나 시간이 초과되면 시간 서버가 멀리 떨어져 있거나 연결할 수 없는 것이 원인일 수 있습니다. 다음을 수행하여 추가 또는 로컬 시간 서버를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-245">If time sync is failing or timing out this may be due to unreachable or a distant time server, the following can be done to add additional or local time servers.</span></span> 
 
* <span data-ttu-id="a8e97-246">디바이스의 명령줄(예:</span><span class="sxs-lookup"><span data-stu-id="a8e97-246">From a command line on the device (eg.</span></span> <span data-ttu-id="a8e97-247">SSH, PowerShell)에서 다음을 실행합니다.  w32tm /config /syncfromflags:manual /manualpeerlist:"0.windows.time.com 1.pool.ntp.org 2.something else, ..."</span><span class="sxs-lookup"><span data-stu-id="a8e97-247">SSH, PowerShell)  w32tm /config /syncfromflags:manual /manualpeerlist:"0.windows.time.com 1.pool.ntp.org 2.something else, ..."</span></span> 
* <span data-ttu-id="a8e97-248">필요한 경우 이미지 만들기 프로세스의 일부로 포함된 부팅 스크립트 또는 사용자 지정 런타임 구성 패키지를 통해 이러한 추가 작업을 레지스트리에 수행할 수도 있습니다. </span><span class="sxs-lookup"><span data-stu-id="a8e97-248">You may also make these additions to the registry via a boot script or a custom runtime configuration package included as part of the image creation process if needed. </span></span>
<span data-ttu-id="a8e97-249">자세한 내용은 다음 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a8e97-249">For more details, see:</span></span> 
* <span data-ttu-id="a8e97-250">[이미지에 파일 및 레지스트리 설정 추가](https://msdn.microsoft.com/library/windows/hardware/mt670641(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="a8e97-250">[Add a file and a registry setting to an image](https://msdn.microsoft.com/library/windows/hardware/mt670641(v=vs.85).aspx)</span></span>
* [<span data-ttu-id="a8e97-251">Windows 10 IoT Core 이미지 만들기</span><span class="sxs-lookup"><span data-stu-id="a8e97-251">Windows 10 IoT Core Image Creation</span></span>](https://blogs.msdn.microsoft.com/iot/2015/12/14/windows-10-iot-core-image-creation/)

#### <a name="starting-the-ftp-server"></a><span data-ttu-id="a8e97-252">FTP 서버 시작</span><span class="sxs-lookup"><span data-stu-id="a8e97-252">Starting the FTP Server</span></span> 
<span data-ttu-id="a8e97-253">시작 시 FTP 서버가 더 이상 기본적으로 실행되지 않음 
</span><span class="sxs-lookup"><span data-stu-id="a8e97-253">The FTP Server no longer runs by default at start-up 
</span></span><br>
<span data-ttu-id="a8e97-254">한 번만 실행하려면 
`Login with SSH\PS`를 수행합니다. 다음 명령을 실행하여 FTP를 시작합니다.  
`start ftpd.exe`    </span><span class="sxs-lookup"><span data-stu-id="a8e97-254">To run once: 
`Login with SSH\PS` Run this command to start FTP:  
`start ftpd.exe`    </span></span>
<span data-ttu-id="a8e97-255">부팅할 때마다 실행하려면 사용자가 스케줄러 작업을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-255">To run on every boot users should create a scheduler task.</span></span> 

    Login with SSH\PS and create a scheduler task:       
    schtasks /create /tn "IoTFTPD" /tr ftpd.exe /ru system /sc onstart 
    schtasks /run /tn “IoTFTPD” 

## <a name="copyright-information"></a><span data-ttu-id="a8e97-256">저작권 정보</span><span class="sxs-lookup"><span data-stu-id="a8e97-256">Copyright Information</span></span> 

<span data-ttu-id="a8e97-257">© Microsoft.</span><span class="sxs-lookup"><span data-stu-id="a8e97-257">© Microsoft.</span></span> <span data-ttu-id="a8e97-258">All rights reserved.</span><span class="sxs-lookup"><span data-stu-id="a8e97-258">All rights reserved.</span></span> 
 
<span data-ttu-id="a8e97-259">이 설명서는 “있는 그대로” 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-259">This document is provided “as-is”.</span></span><span data-ttu-id="a8e97-260">  URL 및 기타 인터넷 웹 사이트 참조를 포함하여 이 문서에 표현된 정보와 보기는 예고 없이 변경될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-260">  Information and views expressed in this document, including URL and other Internet Web site references may change without notice.</span></span> 

<span data-ttu-id="a8e97-261">여기에서 설명한 일부 예시는 설명을 위한 것이며 실제가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-261">Some examples depicted herein are provided for illustration only and are fictitious.</span></span><span data-ttu-id="a8e97-262">  실제 연관이나 관련성을 나타낼 의도가 없으며 그렇게 유추해서도 안됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-262">  No real association or connection is intended or should be inferred.</span></span>  

<span data-ttu-id="a8e97-263">이 문서는 Microsoft 제품의 지적 재산권에 대한 어떠한 법적 권한도 제공하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-263">This document does not provide any legal rights to any intellectual property in any Microsoft product.</span></span><span data-ttu-id="a8e97-264">  이 문서는 내부 참조용으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-264">  This document may be used for internal, references purposes.</span></span> 
  
<span data-ttu-id="a8e97-265">Microsoft는 어떠한 명시적 또는 묵시적 보증도 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-265">Microsoft makes no warranties, express or implied.</span></span>  

<span data-ttu-id="a8e97-266">상표권이 있는 제품의 목록은 Microsoft 상표를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a8e97-266">Please refer to Microsoft Trademarks for a list of trademarked products.</span></span> 

<span data-ttu-id="a8e97-267">다른 모든 상표는 해당 소유자의 자산입니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-267">All other trademarks are property of their respective owners.</span></span>  

<span data-ttu-id="a8e97-268">UPnP™은 UPnP™ Implementers Corporation의 인증 표시입니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-268">UPnP™ is a certification mark of the UPnP™ Implementers Corporation.</span></span> 

<span data-ttu-id="a8e97-269">Bluetooth®는 Bluetooth SIG, Inc. 소유의 상표입니다. 미국 및 Microsoft Corporation에 사용이 허가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-269">Bluetooth® is a trademark owned by Bluetooth SIG, Inc. USA and licensed to Microsoft Corporation.</span></span> 

<span data-ttu-id="a8e97-270">Intel은 Intel Corporation의 등록 상표입니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-270">Intel is a registered trademark of Intel Corporation.</span></span> 

<span data-ttu-id="a8e97-271">Itanium은 Intel Corporation의 등록 상표입니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-271">Itanium is a registered trademark of Intel Corporation.</span></span>
 
<span data-ttu-id="a8e97-272">이 소프트웨어의 일부는 University of Illinois의 Urbana-Champaign 소재의 National Center for Supercomputing Applications에서 개발하고 Spyglass, Inc.와의 사용권 계약 하에 배포되는 MCSA Mosaic를 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-272">Portions of this software are based on MCSA Mosaic, developed by the National Center for Supercomputing Applications at the University of Illinois at Urbana-Champaign, distributed under a licensing agreement with Spyglass, Inc.</span></span> 

<span data-ttu-id="a8e97-273">이 제품에는 RSA Data Security, Inc.에서 사용권을 부여한 보안 소프트웨어가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8e97-273">This product contains security software licensed from RSA Data Security, Inc.</span></span> 
