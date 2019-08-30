---
title: Raspberry Pi 3B +에 대 한 릴리스 정보
author: zeeshanfurqan
ms.author: zeeshanf
ms.date: 05/16/2018
ms.topic: article
description: Raspberry Pi 3B +에 대 한 빌드에 있는 항목을 읽고 자세히 알아보세요.
keywords: windows iot, Windows 참가자, 릴리스 정보, Raspberry Pi 3B 이상
ms.openlocfilehash: f9a1bf98e6ef53ff7f96d35cb34af9527f1c6de1
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "60167361"
---
# <a name="release-notes-for-raspberry-pi-3b"></a><span data-ttu-id="cdae1-104">Raspberry Pi 3B +에 대 한 릴리스 정보</span><span class="sxs-lookup"><span data-stu-id="cdae1-104">Release Notes for Raspberry Pi 3B+</span></span>

<span data-ttu-id="cdae1-105">&copy; 2018 Microsoft Corporation.</span><span class="sxs-lookup"><span data-stu-id="cdae1-105">&copy; 2018 Microsoft Corporation.</span></span> <span data-ttu-id="cdae1-106">All rights reserved.</span><span class="sxs-lookup"><span data-stu-id="cdae1-106">All rights reserved.</span></span>

> [!NOTE]
> <span data-ttu-id="cdae1-107">이번 Raspberry Pi 3B용 릴리스에서는 기술 미리 보기를 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cdae1-107">This release for the Raspberry Pi 3B+ is an unsupported technical preview.</span></span> <span data-ttu-id="cdae1-108">유효성 검사 및 활성화가 제한적으로 완료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="cdae1-108">Limited validation and enablement has been completed.</span></span> <span data-ttu-id="cdae1-109">현재 릴리스는 [여기](https://www.microsoft.com/en-us/software-download/windowsiot)에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cdae1-109">The current release can be found [here](https://www.microsoft.com/en-us/software-download/windowsiot).</span></span> <span data-ttu-id="cdae1-110">보다 나은 평가 환경은 물론, 상용 제품을 위해 Raspberry Pi 3B 또는 Intel, Qualcomm 또는 NXP SoC가 지원되는 기타 디바이스를 사용해 주세요.</span><span class="sxs-lookup"><span data-stu-id="cdae1-110">For a better evaluation experience and for any commercial products, please use the Raspberry Pi 3B or other devices with supported Intel, Qualcomm, or NXP SoCs.</span></span> <span data-ttu-id="cdae1-111">Raspberry Pi 3B+ 관련 문제 해결의 경우 문제 해결 가이드([여기](https://docs.microsoft.com/en-us/windows/iot-core/troubleshooting?branch=master#raspberry-pi-3b-booting-issues))를 참조해 주세요.</span><span class="sxs-lookup"><span data-stu-id="cdae1-111">For troubleshooting issues with the Raspberry Pi 3B+, please see our Troubleshooting Guide, [here](https://docs.microsoft.com/en-us/windows/iot-core/troubleshooting?branch=master#raspberry-pi-3b-booting-issues).</span></span> 

## <a name="whats-new-in-this-build"></a><span data-ttu-id="cdae1-112">이 빌드의 새로운 기능</span><span class="sxs-lookup"><span data-stu-id="cdae1-112">What's new in this build:</span></span> 
* <span data-ttu-id="cdae1-113">일반 버그 수정</span><span class="sxs-lookup"><span data-stu-id="cdae1-113">General bug fixes</span></span>

## <a name="known-issues-in-this-build"></a><span data-ttu-id="cdae1-114">이 빌드의 알려진 이슈:</span><span class="sxs-lookup"><span data-stu-id="cdae1-114">Known issues in this build:</span></span>
* <span data-ttu-id="cdae1-115">이 이미지는 RPi3B +에만 사용할 수 있으며 RPi2에서 부팅 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cdae1-115">This image is only meant for RPi3B+ and will not boot on RPi2.</span></span> 
* <span data-ttu-id="cdae1-116">Visual Studio에서 배포하는 F5 드라이버는 IoT Core에서 작동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cdae1-116">F5 driver deployment from Visual Studio does not work on IoT Core.</span></span> 
* <span data-ttu-id="cdae1-117">RPI3B +에서 WIFI 및 Bluetooth가 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cdae1-117">Onboard WIFI and Bluetooth do not work on RPI3B+.</span></span> 
* <span data-ttu-id="cdae1-118">RPi3B +에서 Ft5406 touch screen 드라이버를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="cdae1-118">Ft5406 touch screen driver is disabled on RPi3B+.</span></span> 
* <span data-ttu-id="cdae1-119">SD 카드 활동 LED를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="cdae1-119">SD card activity LED is disabled.</span></span> 


### <a name="display-resolution-is-monitor-is-disconnected"></a><span data-ttu-id="cdae1-120">디스플레이 해상도가 모니터의 연결이 끊어져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cdae1-120">Display resolution is monitor is disconnected</span></span>
<span data-ttu-id="cdae1-121">Raspberry Pi 3B +는 모니터의 연결이 끊어지면 디스플레이 해상도를 유지 관리할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="cdae1-121">The Raspberry Pi 3B+ may not maintain Display Resolution if monitor is disconnected.</span></span> <span data-ttu-id="cdae1-122">모니터의 EDID는 모니터가 연결될 때 시스템의 해상도를 설정하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="cdae1-122">The EDID of the monitor is used to set the resolution of the system when one is connected.</span></span> <span data-ttu-id="cdae1-123">연결이 끊어지면 펌웨어는 SD 카드 루트의 config.xml에 있는 것으로 기본 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cdae1-123">When disconnected, the firmware defaults to what is in the config.txt in the root of the SD card.</span></span> 


### <a name="video-performance"></a><span data-ttu-id="cdae1-124">비디오 성능</span><span class="sxs-lookup"><span data-stu-id="cdae1-124">Video performance</span></span>
<span data-ttu-id="cdae1-125">플랫폼의 비디오 재생 성능이 최적화 되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="cdae1-125">Video playback performance on the platform is not optimized.</span></span>  <span data-ttu-id="cdae1-126">XAML 기반 드롭다운 메뉴를 비롯한 애니메이션 사용자 요소가 최적화된 성능을 발휘하지 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cdae1-126">Animated user elements including XAML-based dropdown menus may exhibit less than optimal performance.</span></span>  

### <a name="camera-support"></a><span data-ttu-id="cdae1-127">카메라 지원</span><span class="sxs-lookup"><span data-stu-id="cdae1-127">Camera support</span></span>
<span data-ttu-id="cdae1-128">카메라 주변 기기 지원이 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="cdae1-128">Support for camera peripheral devices is limited.</span></span> <span data-ttu-id="cdae1-129">D3D 최신 USB 웹캠이 USB 호스트 컨트롤러의 매우 까다로운 데이터 스트림을 생성하도록 지원하기 위해 플랫폼이 제한되므로 온보드 카메라 버스에 직접 연결되는 PiCam 디바이스는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cdae1-129">The PiCam device directly connected to the onboard camera bus is not supported due to limitations in the platform to support D3D Modern USB webcams produce data streams that are very demanding on the USB Host controller.</span></span>  <span data-ttu-id="cdae1-130">저해상도 설정으로 사용하더라도 웹캠에서 USB를 미세 조정해야 하며 특수한 제어 논리가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="cdae1-130">Even when used with low resolution settings webcams will require additional USB fine tuning and specialized control logic.</span></span>  


### <a name="mouse-pointer-disappears-while-debugging"></a><span data-ttu-id="cdae1-131">디버깅 하는 동안 마우스 포인터가 사라진다</span><span class="sxs-lookup"><span data-stu-id="cdae1-131">Mouse pointer disappears while debugging</span></span>
<span data-ttu-id="cdae1-132">경우에 따라 Visual Studio를 사용 하 여 앱을 배포 하거나 디버깅 한 후 마우스 포인터가 표시 되지 않으면 키보드 (탭) (8038595)를 사용 하 여 포커스를 변경 하는 경우 마우스 포인터가 다시 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="cdae1-132">In some cases, the mouse pointer is not visible after deploying or debugging apps with Visual Studio, the mouse pointer should reappear if you change focus using the keyboard (Tab) (8038595).</span></span>

### <a name="server-applications-with-softap"></a><span data-ttu-id="cdae1-133">SoftAP를 사용 하는 서버 응용 프로그램</span><span class="sxs-lookup"><span data-stu-id="cdae1-133">Server applications with SoftAP</span></span>
<span data-ttu-id="cdae1-134">SoftAP를 사용하면 클라이언트가 UAP 앱에 의해 노출되는 콘텐츠에 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="cdae1-134">When using the SoftAP clients will not be able to access content exposed by UAP apps.</span></span> <span data-ttu-id="cdae1-135">SoftAP을 통해 UAP 응용 프로그램을 노출 하려면 장치의 콘솔에서 다음과 같이 변경 해야 합니다 (8111807).</span><span class="sxs-lookup"><span data-stu-id="cdae1-135">To expose UAP applications via SoftAP the following changes must be made from the console on the device (8111807):</span></span>  

```
reg add hklm\system\currentcontrolset\services\mpssvc\parameters /v IoTInboundLoopbackPolicy /t REG_DWORD /d 1 
checknetisolation loopbackexempt -a -n=<AppID for SoftAP App> 
checknetisolation loopbackexempt -a -n=<AppID for Additional App>  
For example:  checknetisolation loopbackexempt -a -n=IoTOnboardingTask-uwp_1w720vyc4ccym 
```

<span data-ttu-id="cdae1-136">부팅이.</span><span class="sxs-lookup"><span data-stu-id="cdae1-136">Reboot.</span></span>

### <a name="sensor-driver-conflict-in-pre-built-ffus"></a><span data-ttu-id="cdae1-137">미리 빌드된 FFU의 센서 드라이버 충돌</span><span class="sxs-lookup"><span data-stu-id="cdae1-137">Sensor Driver conflict in pre-built FFUs</span></span> 
<span data-ttu-id="cdae1-138">제공된 FFU의 센서 드라이버가 충돌합니다.</span><span class="sxs-lookup"><span data-stu-id="cdae1-138">There is a Sensor Driver Conflict in the provided FFUs.</span></span> <span data-ttu-id="cdae1-139">원격 센서 프레임워크는 나침반, 자력계, 가속도계 및 자이로스코프의 드라이버를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="cdae1-139">The Remote Sensor Framework installs drivers for Compass, Magnetometer, Accelerometer and Gyro.</span></span> <span data-ttu-id="cdae1-140">응용 프로그램에서 이러한 응용 프로그램에 액세스 하기 위한 UWP Api는 설치 된 것으로 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="cdae1-140">The UWP APIs for accessing these from an application assume just one is installed.</span></span> <span data-ttu-id="cdae1-141">물리적으로 연결되는 디바이스의 드라이버를 개발하는 경우 Microsoft에서 제공한 FFU의 원격 드라이버가 충돌합니다.</span><span class="sxs-lookup"><span data-stu-id="cdae1-141">If you are developing a driver for a physically attached device, the remote driver on the Microsoft provided FFUs will conflict.</span></span>  

<span data-ttu-id="cdae1-142">이를 해결 하기 위해 SSH 또는 Powershell을 통해 장치에 연결 하 고 도구를 사용 하 여 다음을 입력 하 여 원격 센서 드라이버를 제거 함으로써 충돌 하는 드라이버를 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cdae1-142">To solve for this, the conflicting driver can be removed by connecting to the device via SSH or Powershell and using the tool devcon.exe to remove the remote sensor driver by typing:</span></span> 

```
"devcon.exe remove @"ROOT\REMOTESENSORDRIVER*"
```

<span data-ttu-id="cdae1-143">원격 센서 드라이버는 OEM에서 만든 FFU에 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cdae1-143">The remote sensor driver does not affect OEM created FFUs.</span></span> 


### <a name="default-administrator-user-name-and-password"></a><span data-ttu-id="cdae1-144">기본 관리자 사용자 이름 및 암호</span><span class="sxs-lookup"><span data-stu-id="cdae1-144">Default administrator user name and password</span></span>
<span data-ttu-id="cdae1-145">기본 관리자 사용자 이름 및 암호는 Windows 10 IoT Core 이미지에 하드 코딩됩니다.</span><span class="sxs-lookup"><span data-stu-id="cdae1-145">The default administrator user name and password are hard coded in the Windows 10 IoT Core image.</span></span> <span data-ttu-id="cdae1-146">이는 디바이스의 보안에 위험 요소로 작동하며, 암호가 변경되기 전에는 열린 인터넷 연결에 노출되면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cdae1-146">This is a security risk for the device, and it should not be exposed to an open internet connection until the password has been changed.</span></span> 

### <a name="volume-controls"></a><span data-ttu-id="cdae1-147">볼륨 컨트롤</span><span class="sxs-lookup"><span data-stu-id="cdae1-147">Volume controls</span></span>
<span data-ttu-id="cdae1-148">Windows 시스템을 사용하여 시스템 볼륨을 변경하는 USB 마이크 및 스피커의 시스템 볼륨 컨트롤은 현재 Windows 10 IoT Core에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cdae1-148">Hardware volume controls for USB microphones and speakers which depend on Windows system to change system volume are currently not supported on Windows 10 IoT Core.</span></span> 

### <a name="usb-keyboards"></a><span data-ttu-id="cdae1-149">USB 키보드</span><span class="sxs-lookup"><span data-stu-id="cdae1-149">USB keyboards</span></span>
<span data-ttu-id="cdae1-150">일부 USB 키보드 및 마우스는 IoT Core에서 작동하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cdae1-150">Some USB keyboards and mice may not work on IoT Core.</span></span> <span data-ttu-id="cdae1-151">다른 키보드 또는 마우스를 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="cdae1-151">Use a different keyboard or mouse.</span></span> <span data-ttu-id="cdae1-152">유효성이 검사 된 주변 장치의 목록은 [여기](http://go.microsoft.com/fwlink/?LinkId=619428)의 설명서에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cdae1-152">A list of validated peripheral devices can be found in the documentation [here](http://go.microsoft.com/fwlink/?LinkId=619428).</span></span>
 
### <a name="screen-orientation"></a><span data-ttu-id="cdae1-153">화면 방향</span><span class="sxs-lookup"><span data-stu-id="cdae1-153">Screen orientation</span></span>
<span data-ttu-id="cdae1-154">방향을 "세로"로 설정하는 기능이 유니버설 앱에서는 작동하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cdae1-154">Setting the orientation to “Portrait” may not be honored in a Universal App.</span></span>

### <a name="referencing-adapters-with-alljoyn-templates"></a><span data-ttu-id="cdae1-155">AllJoyn 템플릿을 사용 하 여 어댑터 참조</span><span class="sxs-lookup"><span data-stu-id="cdae1-155">Referencing adapters with AllJoyn templates</span></span>
<span data-ttu-id="cdae1-156">특정 SDK 버전을 사용하는 경우 AllJoyn 어댑터 프로젝트에 대한 참조를 추가하려고 하면 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cdae1-156">Attempting to add references to AllJoyn adapter projects may result in errors when using specific SDK versions.</span></span>  <span data-ttu-id="cdae1-157">이 오류를 해결하려면 Visual Studio의 대상 플랫폼을 현재 SDK 버전에 맞게 변경한 다음, 프로젝트를 다시 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="cdae1-157">To resolve these errors, change Visual Studio’s target platform to match the current SDK version, then reload the project.</span></span>  

### <a name="wifi-direct-limitations-on-windows-10-iot-core"></a><span data-ttu-id="cdae1-158">Windows 10 IoT Core의 WiFi Direct 제한 사항</span><span class="sxs-lookup"><span data-stu-id="cdae1-158">WiFi Direct limitations on Windows 10 IoT Core</span></span>
1. <span data-ttu-id="cdae1-159">Windows 10 IoT Core 장치는 연결 장치 여야 합니다. 즉, 다른 장치에서 연결을 시작 하는 광고 장치로 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cdae1-159">The Windows 10 IoT Core device has to be the connecting device – it will not work as the advertising device with another device initiating the connection.</span></span>   
2. <span data-ttu-id="cdae1-160">고급 페어링을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cdae1-160">Advanced pairing must be used.</span></span>  <span data-ttu-id="cdae1-161">샘플 앱은 디바이스를 연결하기 전에 고급 페어링 API를 사용하여 페어링하는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="cdae1-161">The sample app demonstrates how to use the advanced pairing API’s to pair the devices prior to connecting.</span></span> 
3. <span data-ttu-id="cdae1-162">모든 무선 어댑터가 WiFi Direct를 지원하는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="cdae1-162">Not all wireless adapters support WiFi direct.</span></span> <span data-ttu-id="cdae1-163">"Realtek RTL8188EU Wireless Lan 802.11 n USB 2.0 네트워크 어댑터"가 작동 하는지 테스트 하 고 유효성을 검사 했지만 다른 어댑터가 지원 되지 않을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cdae1-163">We have tested and validated that the "Realtek RTL8188EU Wireless Lan 802.11n USB 2.0 Network adapter" works, but other adapters may not be supported.</span></span> 

### <a name="non-default-drive-mode-3890679"></a><span data-ttu-id="cdae1-164">기본이 아닌 드라이브 모드 (3890679)</span><span class="sxs-lookup"><span data-stu-id="cdae1-164">Non-default drive mode (3890679)</span></span> 
<span data-ttu-id="cdae1-165">Raspberry Pi 및 Dragonboard에서, 기본이 아닌 드라이브 모드에서 기본이 아닌 다른 드라이브 모드로 전환하면 GPIO 핀에서 문제가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cdae1-165">On Raspberry Pi and Dragonboard, switching from a non-default drive mode to a different non-default drive mode may produce a glitch on the GPIO pin.</span></span> <span data-ttu-id="cdae1-166">이 문제를 해결 하려면 응용 프로그램의 시작 부분에서 드라이브 모드를 한 번 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="cdae1-166">To workaround this issue, set drive mode once at the beginning of the application.</span></span> 

### <a name="application-already-running-1244550"></a><span data-ttu-id="cdae1-167">응용 프로그램이 이미 실행 중입니다. (1244550)</span><span class="sxs-lookup"><span data-stu-id="cdae1-167">Application already running (1244550)</span></span> 
<span data-ttu-id="cdae1-168">기본 시작 앱 역시 Visual Studio에서 배포하면 자체 앱과 충돌할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cdae1-168">The Default startup app may conflict with itself when it is also deployed from Visual Studio.</span></span> <span data-ttu-id="cdae1-169">해결 방법: 기본 시작 앱을 배포하려는 앱이 아닌 다른 애플리케이션으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="cdae1-169">WORKAROUND: Change the default startup app to an application other than that you wish to deploy.</span></span> 

### <a name="backgroundmediaplayermessagereceivedfromforeground-may-crash-2199869"></a><span data-ttu-id="cdae1-170">BackgroundMediaPlayer. MessageReceivedFromForeground가 충돌할 수 있습니다 (2199869).</span><span class="sxs-lookup"><span data-stu-id="cdae1-170">BackgroundMediaPlayer.MessageReceivedFromForeground may crash (2199869)</span></span> 
<span data-ttu-id="cdae1-171">다음 코드 줄이 충돌할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cdae1-171">The following line of code may crash:</span></span> 
```
BackgroundMediaPlayer.MessageReceivedFromForeground += OnMessageReceivedFromForeground
```

<span data-ttu-id="cdae1-172">충돌을 방지 하려면 먼저 실행 되도록이 코드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="cdae1-172">To prevent the crash, add this code so that it is executed first:</span></span>
```
var player = BackgroundMediaPlayer.Current;
```

### <a name="azure-active-directory-authentication-support-4266261"></a><span data-ttu-id="cdae1-173">Azure Active Directory 인증 지원 (4266261)</span><span class="sxs-lookup"><span data-stu-id="cdae1-173">Azure Active Directory Authentication Support (4266261)</span></span> 
<span data-ttu-id="cdae1-174">Azure Active Directory 인증 라이브러리는 Windows 10 IoT Core에서 작동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cdae1-174">The Azure Active Directory Authentication Library does not work on Windows 10 IoT Core.</span></span>  

### <a name="shell-management-of-application-crashes"></a><span data-ttu-id="cdae1-175">애플리케이션 충돌의 셸 관리</span><span class="sxs-lookup"><span data-stu-id="cdae1-175">Shell Management of Application Crashes</span></span>
<span data-ttu-id="cdae1-176">IoT Core의 셸 인프라는 디바이스에서 실행되는 APPX 형식 애플리케이션의 충돌을 모니터링하다가 충돌이 발생하면 해당 애플리케이션을 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="cdae1-176">IoT Core’s shell infrastructure monitors APPX-type applications running on the device for crashes, and restarts those applications when crashes occur.</span></span>  <span data-ttu-id="cdae1-177">다시 시작 된 응용 프로그램의 작동이 중단 되 면 셸에서는 복구를 시도 하는 동안 오류를 발생 시키고 다시 부팅 하는 시스템 중요 프로세스를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="cdae1-177">If the restarted applications continue to crash, the shell will employ a failfast – a system critical process that causes a bugcheck and reboot in an attempt to recover.</span></span>  <span data-ttu-id="cdae1-178">헤드 구성의 백그라운드 작업과 포그라운드 애플리케이션에 비슷한 논리와 처리 방법이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="cdae1-178">Comparable logic and handling is used to background tasks and foreground applications in a headed configuration.</span></span>   <span data-ttu-id="cdae1-179">다음은 충돌 처리 및 다시 시도 논리를 캡처한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="cdae1-179">Crash handling and retry logic is captured below:</span></span>

```
Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\CBTConfig  (or ForegroundAppConfig for headed) 
  Qword:"FailureResetIntervalMs" – length of time app has to run successfully to reset failures seen to 0. – default is 0x00000000000493E0 == 5 minutes 
  Qword:"BaseRetryDelayMs"  -- wait time coefficient.  Default is 0xa. 
  Dword:"MaxFailureCount". Default is 10 
  DWord:"FallbackExponentNumerator", default is 31. 
  Dword:"FallbackExponentDenominator", default is 20 
  
  
Fallback_exponent = FallbackExponentNumerator / FallbackExponentDenominator; // default is 1.55 
When app crash is detected: 
    if time_since_last_crash > failureresetinterval then crashes_seen = 1 
    else ++crashes_seen; 
  
if crashes_seen > MaxFailureCount then __failfast; 
  
else  
  
delay = (dword) ((float)BaseRetryDelayMs * (crashes_seen ** Fallback_exponent)) 
```

<span data-ttu-id="cdae1-180">지연 시간을 기다린 후 앱을 다시 실행할 것입니다.</span><span class="sxs-lookup"><span data-stu-id="cdae1-180">Wait for the delay and relaunch the app.</span></span>

#### <a name="dragonboard-spi-runs-at-48mhz"></a><span data-ttu-id="cdae1-181">4\.8Mhz로 실행되는 Dragonboard SPI</span><span class="sxs-lookup"><span data-stu-id="cdae1-181">Dragonboard SPI runs at 4.8Mhz</span></span>
<span data-ttu-id="cdae1-182">Dragonboard의 SPI는 요청된 속도를 무시하고 항상 4.8Mhz로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="cdae1-182">The SPI on the Dragonboard will ignore the requested speed and always run at 4.8 Mhz.</span></span>  

#### <a name="dragonboard-connected-standby"></a><span data-ttu-id="cdae1-183">Dragonboard 연결된 대기 상태</span><span class="sxs-lookup"><span data-stu-id="cdae1-183">Dragonboard Connected Standby</span></span> 
<span data-ttu-id="cdae1-184">연결된 대기 상태는 Qualcomm Dragonboard에서 기본적으로 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cdae1-184">Connected Standby is not enabled on the Qualcomm Dragonboard by default.</span></span>  <span data-ttu-id="cdae1-185">DragonBoard에서 연결 된 대기를 사용 하도록 설정 하려면 다음 레지스트리 키를 "1"로 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cdae1-185">To enable Connected Standby on DragonBoard the following registry key needs to be set to “1”.</span></span>


### <a name="time-synchronization"></a><span data-ttu-id="cdae1-186">시간 동기화</span><span class="sxs-lookup"><span data-stu-id="cdae1-186">Time synchronization</span></span>
<span data-ttu-id="cdae1-187">시간 동기화가 실패하거나 시간이 초과되면 시간 서버가 멀리 떨어져 있거나 연결할 수 없는 것이 원인일 수 있습니다. 다음을 수행하여 추가 또는 로컬 시간 서버를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cdae1-187">If time sync is failing or timing out this may be due to unreachable or a distant time server, the following can be done to add additional or local time servers.</span></span> 
 
1. <span data-ttu-id="cdae1-188">디바이스의 명령줄(예:</span><span class="sxs-lookup"><span data-stu-id="cdae1-188">From a command line on the device (eg.</span></span> <span data-ttu-id="cdae1-189">SSH, Powershell).</span><span class="sxs-lookup"><span data-stu-id="cdae1-189">SSH, Powershell).</span></span>
   ```
   w32tm /config /syncfromflags:manual /manualpeerlist:"0.windows.time.com 1.pool.ntp.org 2.something else, ..."
   ```
2. <span data-ttu-id="cdae1-190">필요한 경우 부팅 스크립트 또는 이미지 만들기 프로세스 도중에 포함된 사용자 지정 런타임 구성 패키지를 레지스트리에 추가할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cdae1-190">You may also make these additions to the registry via a boot script or a custom runtime configuration package included as part of the image creation process if needed.</span></span> 

### <a name="starting-the-ftp-server"></a><span data-ttu-id="cdae1-191">FTP 서버 시작</span><span class="sxs-lookup"><span data-stu-id="cdae1-191">Starting the FTP Server</span></span> 
* <span data-ttu-id="cdae1-192">SSH\PS를 사용 하 여 한 번 로그인을 실행 하 고이 명령을 실행 하 여 FTP를 시작 하려면:</span><span class="sxs-lookup"><span data-stu-id="cdae1-192">To run once - Login with SSH\PS and run this command to start FTP:</span></span>  

```
start ftpd.exe 
```

* <span data-ttu-id="cdae1-193">모든 부팅에서 실행 하려면 사용자는 SSH\PS를 사용 하 여 scheduler 작업 로그인을 만들고 scheduler 작업을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cdae1-193">To run on every boot, users should create a scheduler task - Login with SSH\PS and create a scheduler task:</span></span>

```
schtasks /create /tn "IoTFTPD" /tr ftpd.exe /ru system /sc onstart 
Schtasks /run /tn “IoTFTPD” 
```

### <a name="partition-size-requirements-for-update"></a><span data-ttu-id="cdae1-194">업데이트를 위한 파티션 크기 요구 사항</span><span class="sxs-lookup"><span data-stu-id="cdae1-194">Partition size requirements for Update</span></span> 
<span data-ttu-id="cdae1-195">데이터 파티션이 업데이트 기능을 위한 충분 한 공간을 유지 하는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="cdae1-195">Ensure data partition maintains sufficient space for update functionality.</span></span><span data-ttu-id="cdae1-196">  전체 업데이트 기능에는 1GB를 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="cdae1-196">  We recommend 1GB free for full update functionality.</span></span> <span data-ttu-id="cdae1-197"> 데이터 파티션에 공간이 충분 하지 않은 경우 설치 단계에서 업데이트가 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="cdae1-197"> If Data partition does not have enough space, updates will fail in the installation phase.</span></span> 

### <a name="powershell-log-generation-on-iot-core"></a><span data-ttu-id="cdae1-198">IoT Core의 PowerShell 로그 생성</span><span class="sxs-lookup"><span data-stu-id="cdae1-198">PowerShell log generation on IoT Core</span></span> 
<span data-ttu-id="cdae1-199">Iot Core의 PowerShell은 기본적으로 파일 시스템의 공간을 차지 하는 로그 파일을 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cdae1-199">PowerShell on Iot Core may generate log files by default taking up space on the filesystem.</span></span> <span data-ttu-id="cdae1-200">로그 파일 크기는 제한 되어 있지만 디스크 공간을 더 많이 사용 하는 경우에도 디스크 공간 부족으로 인해 업데이트가 실패할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cdae1-200">Although the log file sizes are limited they can take up space potentially resulting in a low disk space situation which, among other things, can result in updates failing.</span></span> <span data-ttu-id="cdae1-201">.Evtx 이벤트 로그 파일에는 각각 20mb의 미리 정의 된 최대 크기가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cdae1-201">The .evtx event log files have a predefined maximum size of 20 MB each.</span></span> <span data-ttu-id="cdae1-202">레지스트리를 통해 서로 다른 최대 크기를 갖도록 파일을 개별적으로 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cdae1-202">You  can individually limit files to have a different max size via registry.</span></span> <span data-ttu-id="cdae1-203">예를 들어, 보안 .evtx를 최대 10mb로 유지 하려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="cdae1-203">For example, To keep security.evtx at 10 MB max size:</span></span> 
```
regd add HKLM\SYSTEM\CurrentControlSet\Services\EventLog\Security /v MaxSize /t REG_DWORD /d 0xa00000 /f 
```

### <a name="schtasks-limitation"></a><span data-ttu-id="cdae1-204">Schtasks 제한</span><span class="sxs-lookup"><span data-stu-id="cdae1-204">Schtasks limitation</span></span>  
<span data-ttu-id="cdae1-205">Schtasks는/xml 스위치 사용을 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cdae1-205">Schtasks does not support using /xml switch.</span></span> <span data-ttu-id="cdae1-206">예를 들어 다음과 같은 가치를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cdae1-206">For example:</span></span> 
```
schtasks /create /xml <xmlfile> /TN <taskname>
```
<span data-ttu-id="cdae1-207">IoT Core에서 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="cdae1-207">This will fail on IoT Core.</span></span> <span data-ttu-id="cdae1-208">명령을 실행 하면 오류가 생성 됩니다. 오류: 지정 된 프로시저를 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="cdae1-208">Running the command will generate the error: ERROR: The specified procedure could not be found.</span></span> 
