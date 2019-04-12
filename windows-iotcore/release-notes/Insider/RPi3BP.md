---
title: Raspberry Pi 3B +에 대 한 릴리스 정보
author: zeeshanfurqan
ms.author: zeeshanf
ms.date: 05/16/2018
ms.topic: article
description: 읽기 및 Raspberry Pi 3B +에 대 한 빌드에 포함 된 내용에 대해 알아봅니다.
keywords: windows iot, Windows Insider 릴리스 정보, Raspberry Pi 3B +
ms.openlocfilehash: f9a1bf98e6ef53ff7f96d35cb34af9527f1c6de1
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512701"
---
# <a name="release-notes-for-raspberry-pi-3b"></a><span data-ttu-id="8384e-104">Raspberry Pi 3B +에 대 한 릴리스 정보</span><span class="sxs-lookup"><span data-stu-id="8384e-104">Release Notes for Raspberry Pi 3B+</span></span>

<span data-ttu-id="8384e-105">&copy; 2018 Microsoft Corporation.</span><span class="sxs-lookup"><span data-stu-id="8384e-105">&copy; 2018 Microsoft Corporation.</span></span> <span data-ttu-id="8384e-106">All rights reserved.</span><span class="sxs-lookup"><span data-stu-id="8384e-106">All rights reserved.</span></span>

> [!NOTE]
> <span data-ttu-id="8384e-107">Raspberry Pi 3B +이 릴리스에서 지원 되지 않는 기술 미리 보기를 합니다.</span><span class="sxs-lookup"><span data-stu-id="8384e-107">This release for the Raspberry Pi 3B+ is an unsupported technical preview.</span></span> <span data-ttu-id="8384e-108">제한 된 유효성 검사 및 활성화가 완료 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8384e-108">Limited validation and enablement has been completed.</span></span> <span data-ttu-id="8384e-109">현재 릴리스를 찾을 수 있습니다 [여기](https://www.microsoft.com/en-us/software-download/windowsiot)합니다.</span><span class="sxs-lookup"><span data-stu-id="8384e-109">The current release can be found [here](https://www.microsoft.com/en-us/software-download/windowsiot).</span></span> <span data-ttu-id="8384e-110">더 나은 평가판 환경과 모든 상용 제품을 사용 하세요 Raspberry Pi 3B 또는 기타 장치 지원 되는 Intel, Qualcomm, 또는 NXP Soc를 사용 하 여 합니다.</span><span class="sxs-lookup"><span data-stu-id="8384e-110">For a better evaluation experience and for any commercial products, please use the Raspberry Pi 3B or other devices with supported Intel, Qualcomm, or NXP SoCs.</span></span> <span data-ttu-id="8384e-111">Raspberry Pi 3B +를 사용 하 여 문제를 해결, 문제 해결 가이드를 참조 하세요 [여기](https://docs.microsoft.com/en-us/windows/iot-core/troubleshooting?branch=master#raspberry-pi-3b-booting-issues)합니다.</span><span class="sxs-lookup"><span data-stu-id="8384e-111">For troubleshooting issues with the Raspberry Pi 3B+, please see our Troubleshooting Guide, [here](https://docs.microsoft.com/en-us/windows/iot-core/troubleshooting?branch=master#raspberry-pi-3b-booting-issues).</span></span> 

## <a name="whats-new-in-this-build"></a><span data-ttu-id="8384e-112">이 빌드의 새 소식:</span><span class="sxs-lookup"><span data-stu-id="8384e-112">What's new in this build:</span></span> 
* <span data-ttu-id="8384e-113">일반 버그 수정</span><span class="sxs-lookup"><span data-stu-id="8384e-113">General bug fixes</span></span>

## <a name="known-issues-in-this-build"></a><span data-ttu-id="8384e-114">이 빌드의 알려진된 문제:</span><span class="sxs-lookup"><span data-stu-id="8384e-114">Known issues in this build:</span></span>
* <span data-ttu-id="8384e-115">이 이미지는 기능만 RPi3B + 및 RPi2에서 부팅 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8384e-115">This image is only meant for RPi3B+ and will not boot on RPi2.</span></span> 
* <span data-ttu-id="8384e-116">Visual Studio에서 F5 드라이버 배포 IoT Core에서 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8384e-116">F5 driver deployment from Visual Studio does not work on IoT Core.</span></span> 
* <span data-ttu-id="8384e-117">온 보 딩 WIFI 및 Bluetooth RPI3B 이상에서 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8384e-117">Onboard WIFI and Bluetooth do not work on RPI3B+.</span></span> 
* <span data-ttu-id="8384e-118">Ft5406 터치 화면 드라이버 RPi3B +에서 비활성화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8384e-118">Ft5406 touch screen driver is disabled on RPi3B+.</span></span> 
* <span data-ttu-id="8384e-119">SD 카드 활동 LED 비활성화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8384e-119">SD card activity LED is disabled.</span></span> 


### <a name="display-resolution-is-monitor-is-disconnected"></a><span data-ttu-id="8384e-120">디스플레이 해상도 모니터 연결이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8384e-120">Display resolution is monitor is disconnected</span></span>
<span data-ttu-id="8384e-121">Raspberry Pi 3B + 모니터 연결이 끊어진 경우 디스플레이 해상도 유지 하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8384e-121">The Raspberry Pi 3B+ may not maintain Display Resolution if monitor is disconnected.</span></span> <span data-ttu-id="8384e-122">모니터의 EDID가 연결 된 경우 시스템의 해상도 설정 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8384e-122">The EDID of the monitor is used to set the resolution of the system when one is connected.</span></span> <span data-ttu-id="8384e-123">연결이 끊긴 경우 펌웨어 SD 카드의 루트에 config.txt의 기본값으로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8384e-123">When disconnected, the firmware defaults to what is in the config.txt in the root of the SD card.</span></span> 


### <a name="video-performance"></a><span data-ttu-id="8384e-124">비디오 성능</span><span class="sxs-lookup"><span data-stu-id="8384e-124">Video performance</span></span>
<span data-ttu-id="8384e-125">플랫폼에서 비디오 재생 성능이 최적화 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8384e-125">Video playback performance on the platform is not optimized.</span></span>  <span data-ttu-id="8384e-126">XAML 기반 드롭다운 메뉴를 포함 하는 요소는 최상의 성능을 얻지 그러지 않을 사용자를 애니메이션 합니다.</span><span class="sxs-lookup"><span data-stu-id="8384e-126">Animated user elements including XAML-based dropdown menus may exhibit less than optimal performance.</span></span>  

### <a name="camera-support"></a><span data-ttu-id="8384e-127">카메라 지원</span><span class="sxs-lookup"><span data-stu-id="8384e-127">Camera support</span></span>
<span data-ttu-id="8384e-128">주변 장치 카메라에 대 한 지원은 제한 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8384e-128">Support for camera peripheral devices is limited.</span></span> <span data-ttu-id="8384e-129">PiCam 장치 내장 카메라 버스에 직접 연결 된 USB 호스트 컨트롤러에서 매우 까다로운 D3D 최신 USB 웹캠 생성 데이터 스트림을 지 원하는 플랫폼의 제한으로 인해 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8384e-129">The PiCam device directly connected to the onboard camera bus is not supported due to limitations in the platform to support D3D Modern USB webcams produce data streams that are very demanding on the USB Host controller.</span></span>  <span data-ttu-id="8384e-130">도 함께 사용할 경우 낮은 해상도 설정 웹캠 추가 USB 미세 하 게 조정 해야 및 제어 논리를 특수화 합니다.</span><span class="sxs-lookup"><span data-stu-id="8384e-130">Even when used with low resolution settings webcams will require additional USB fine tuning and specialized control logic.</span></span>  


### <a name="mouse-pointer-disappears-while-debugging"></a><span data-ttu-id="8384e-131">디버깅 하는 동안 마우스 포인터가 사라집니다.</span><span class="sxs-lookup"><span data-stu-id="8384e-131">Mouse pointer disappears while debugging</span></span>
<span data-ttu-id="8384e-132">일부 경우에 배포 하거나 Visual Studio를 사용 하 여 앱을 디버깅 한 후 마우스 포인터를 보이지 않으면, 키보드 (탭) (8038595)를 사용 하 여 포커스를 변경 하는 경우 마우스 포인터를 다시 표시 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8384e-132">In some cases, the mouse pointer is not visible after deploying or debugging apps with Visual Studio, the mouse pointer should reappear if you change focus using the keyboard (Tab) (8038595).</span></span>

### <a name="server-applications-with-softap"></a><span data-ttu-id="8384e-133">SoftAP 사용 하 여 서버 응용 프로그램</span><span class="sxs-lookup"><span data-stu-id="8384e-133">Server applications with SoftAP</span></span>
<span data-ttu-id="8384e-134">클라이언트 UAP 앱에 의해 노출 되는 콘텐츠에 액세스할 수 없게 됩니다 SoftAP을 사용할 때</span><span class="sxs-lookup"><span data-stu-id="8384e-134">When using the SoftAP clients will not be able to access content exposed by UAP apps.</span></span> <span data-ttu-id="8384e-135">SoftAP 통해 UAP 응용 프로그램을 노출 하는 다음 변경 해야 장치 (8111807)의 콘솔에서:</span><span class="sxs-lookup"><span data-stu-id="8384e-135">To expose UAP applications via SoftAP the following changes must be made from the console on the device (8111807):</span></span>  

```
reg add hklm\system\currentcontrolset\services\mpssvc\parameters /v IoTInboundLoopbackPolicy /t REG_DWORD /d 1 
checknetisolation loopbackexempt -a -n=<AppID for SoftAP App> 
checknetisolation loopbackexempt -a -n=<AppID for Additional App>  
For example:  checknetisolation loopbackexempt -a -n=IoTOnboardingTask-uwp_1w720vyc4ccym 
```

<span data-ttu-id="8384e-136">다시 부팅 합니다.</span><span class="sxs-lookup"><span data-stu-id="8384e-136">Reboot.</span></span>

### <a name="sensor-driver-conflict-in-pre-built-ffus"></a><span data-ttu-id="8384e-137">미리 빌드된 FFUs 센서 드라이버 충돌</span><span class="sxs-lookup"><span data-stu-id="8384e-137">Sensor Driver conflict in pre-built FFUs</span></span> 
<span data-ttu-id="8384e-138">제공 된 FFUs에 충돌 하는 센서 드라이버가 없는 경우</span><span class="sxs-lookup"><span data-stu-id="8384e-138">There is a Sensor Driver Conflict in the provided FFUs.</span></span> <span data-ttu-id="8384e-139">원격 센서 Framework 나침반, 지자기 센터가 속도계 및이 컴 파스에 대 한 드라이버를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="8384e-139">The Remote Sensor Framework installs drivers for Compass, Magnetometer, Accelerometer and Gyro.</span></span> <span data-ttu-id="8384e-140">응용 프로그램에서 이러한 액세스에 대 한 UWP Api 설치 되어 있는 것을 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8384e-140">The UWP APIs for accessing these from an application assume just one is installed.</span></span> <span data-ttu-id="8384e-141">물리적으로 연결 된 장치 드라이버를 개발 하는 경우 microsoft 원격 드라이버 FFUs 충돌을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="8384e-141">If you are developing a driver for a physically attached device, the remote driver on the Microsoft provided FFUs will conflict.</span></span>  

<span data-ttu-id="8384e-142">이 해결 하기 위해 SSH 또는 Powershell을 통해 장치에 연결 하 고를 입력 하 여 원격 센서 드라이버를 제거할 도구 devcon.exe를 사용 하 여 충돌 하는 드라이버를 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8384e-142">To solve for this, the conflicting driver can be removed by connecting to the device via SSH or Powershell and using the tool devcon.exe to remove the remote sensor driver by typing:</span></span> 

```
"devcon.exe remove @"ROOT\REMOTESENSORDRIVER*"
```

<span data-ttu-id="8384e-143">원격 센서 드라이버 FFUs를 생성 하는 OEM 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8384e-143">The remote sensor driver does not affect OEM created FFUs.</span></span> 


### <a name="default-administrator-user-name-and-password"></a><span data-ttu-id="8384e-144">기본 관리자 사용자 이름 및 암호</span><span class="sxs-lookup"><span data-stu-id="8384e-144">Default administrator user name and password</span></span>
<span data-ttu-id="8384e-145">기본 관리자 사용자 이름 및 암호를 하드 코딩 되어 Windows 10 IoT Core 이미지.</span><span class="sxs-lookup"><span data-stu-id="8384e-145">The default administrator user name and password are hard coded in the Windows 10 IoT Core image.</span></span> <span data-ttu-id="8384e-146">이 장치에 대 한 보안 위험 및 암호가 변경 될 때까지 열려 인터넷 연결으로 노출 되지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8384e-146">This is a security risk for the device, and it should not be exposed to an open internet connection until the password has been changed.</span></span> 

### <a name="volume-controls"></a><span data-ttu-id="8384e-147">볼륨 컨트롤</span><span class="sxs-lookup"><span data-stu-id="8384e-147">Volume controls</span></span>
<span data-ttu-id="8384e-148">USB 마이크와 스피커 시스템 볼륨을 변경 하려면 Windows 시스템에 종속 된에 대 한 하드웨어 볼륨 컨트롤은 현재 Windows 10 IoT Core 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8384e-148">Hardware volume controls for USB microphones and speakers which depend on Windows system to change system volume are currently not supported on Windows 10 IoT Core.</span></span> 

### <a name="usb-keyboards"></a><span data-ttu-id="8384e-149">USB 키보드</span><span class="sxs-lookup"><span data-stu-id="8384e-149">USB keyboards</span></span>
<span data-ttu-id="8384e-150">일부 USB 키보드 및 마우스 IoT Core에서 작동 하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8384e-150">Some USB keyboards and mice may not work on IoT Core.</span></span> <span data-ttu-id="8384e-151">다른 키보드 또는 마우스를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8384e-151">Use a different keyboard or mouse.</span></span> <span data-ttu-id="8384e-152">유효성이 검사 된 주변 장치 목록을 설명서에서 찾을 수 있습니다 [여기](http://go.microsoft.com/fwlink/?LinkId=619428)합니다.</span><span class="sxs-lookup"><span data-stu-id="8384e-152">A list of validated peripheral devices can be found in the documentation [here](http://go.microsoft.com/fwlink/?LinkId=619428).</span></span>
 
### <a name="screen-orientation"></a><span data-ttu-id="8384e-153">화면 방향</span><span class="sxs-lookup"><span data-stu-id="8384e-153">Screen orientation</span></span>
<span data-ttu-id="8384e-154">유니버설 앱에서 "Portrait" 방향을 설정 유지 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8384e-154">Setting the orientation to “Portrait” may not be honored in a Universal App.</span></span>

### <a name="referencing-adapters-with-alljoyn-templates"></a><span data-ttu-id="8384e-155">AllJoyn 템플릿 사용 하 여 어댑터 참조</span><span class="sxs-lookup"><span data-stu-id="8384e-155">Referencing adapters with AllJoyn templates</span></span>
<span data-ttu-id="8384e-156">특정 SDK 버전을 사용 하는 경우 AllJoyn 어댑터 프로젝트에 대 한 참조를 추가 하는 동안 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8384e-156">Attempting to add references to AllJoyn adapter projects may result in errors when using specific SDK versions.</span></span>  <span data-ttu-id="8384e-157">이러한 오류를 해결 하려면 현재 SDK 버전에 맞게 Visual Studio의 대상 플랫폼을 변경 하 고 프로젝트를 다시 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="8384e-157">To resolve these errors, change Visual Studio’s target platform to match the current SDK version, then reload the project.</span></span>  

### <a name="wifi-direct-limitations-on-windows-10-iot-core"></a><span data-ttu-id="8384e-158">Windows 10 IoT Core WiFi 직접 제한 사항</span><span class="sxs-lookup"><span data-stu-id="8384e-158">WiFi Direct limitations on Windows 10 IoT Core</span></span>
1. <span data-ttu-id="8384e-159">– 연결 된 장치를 장치에 Windows 10 IoT Core 작동 하지 않습니다 연결을 시작 하는 다른 장치를 사용 하 여 광고 장치로 합니다.</span><span class="sxs-lookup"><span data-stu-id="8384e-159">The Windows 10 IoT Core device has to be the connecting device – it will not work as the advertising device with another device initiating the connection.</span></span>   
2. <span data-ttu-id="8384e-160">고급 연결을 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8384e-160">Advanced pairing must be used.</span></span>  <span data-ttu-id="8384e-161">샘플 앱에 고급 페어링 API의 쌍으로 연결 하기 전에 장치를 사용 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8384e-161">The sample app demonstrates how to use the advanced pairing API’s to pair the devices prior to connecting.</span></span> 
3. <span data-ttu-id="8384e-162">일부 무선 어댑터 WiFi direct를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="8384e-162">Not all wireless adapters support WiFi direct.</span></span> <span data-ttu-id="8384e-163">테스트 하 고 유효성을 검사 하는 "Realtek RTL8188EU 무선 Lan 802.11n USB 2.0 네트워크 어댑터" 작동 하지만 그 밖의 어댑터에 지원 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8384e-163">We have tested and validated that the "Realtek RTL8188EU Wireless Lan 802.11n USB 2.0 Network adapter" works, but other adapters may not be supported.</span></span> 

### <a name="non-default-drive-mode-3890679"></a><span data-ttu-id="8384e-164">기본이 아닌 드라이브 모드 (3890679)</span><span class="sxs-lookup"><span data-stu-id="8384e-164">Non-default drive mode (3890679)</span></span> 
<span data-ttu-id="8384e-165">Raspberry Pi에 Dragonboard 모드로 전환할 경우 기본이 아닌 드라이브 모드에서는 다른 기본이 아닌 드라이브 GPIO 핀에 결함이 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8384e-165">On Raspberry Pi and Dragonboard, switching from a non-default drive mode to a different non-default drive mode may produce a glitch on the GPIO pin.</span></span> <span data-ttu-id="8384e-166">이 문제를 해결 하려면, 응용 프로그램의 시작 부분에 한 번 드라이브 모드를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8384e-166">To workaround this issue, set drive mode once at the beginning of the application.</span></span> 

### <a name="application-already-running-1244550"></a><span data-ttu-id="8384e-167">이미 (1244550)를 실행 하는 응용 프로그램</span><span class="sxs-lookup"><span data-stu-id="8384e-167">Application already running (1244550)</span></span> 
<span data-ttu-id="8384e-168">또한 Visual Studio에서 배포 될 때 기본 시작 앱 자체와 충돌할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8384e-168">The Default startup app may conflict with itself when it is also deployed from Visual Studio.</span></span> <span data-ttu-id="8384e-169">해결 방법: 배포 하려는 이외의 응용 프로그램에 기본 시작 앱을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="8384e-169">WORKAROUND: Change the default startup app to an application other than that you wish to deploy.</span></span> 

### <a name="backgroundmediaplayermessagereceivedfromforeground-may-crash-2199869"></a><span data-ttu-id="8384e-170">BackgroundMediaPlayer.MessageReceivedFromForeground (2199869) 충돌이 발생할 수 있음</span><span class="sxs-lookup"><span data-stu-id="8384e-170">BackgroundMediaPlayer.MessageReceivedFromForeground may crash (2199869)</span></span> 
<span data-ttu-id="8384e-171">다음 코드 줄 충돌이 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8384e-171">The following line of code may crash:</span></span> 
```
BackgroundMediaPlayer.MessageReceivedFromForeground += OnMessageReceivedFromForeground
```

<span data-ttu-id="8384e-172">충돌을 방지 하려면 먼저 실행 되도록이 코드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="8384e-172">To prevent the crash, add this code so that it is executed first:</span></span>
```
var player = BackgroundMediaPlayer.Current;
```

### <a name="azure-active-directory-authentication-support-4266261"></a><span data-ttu-id="8384e-173">Azure Active Directory 인증 지원 (4266261)</span><span class="sxs-lookup"><span data-stu-id="8384e-173">Azure Active Directory Authentication Support (4266261)</span></span> 
<span data-ttu-id="8384e-174">Azure Active Directory 인증 라이브러리는 Windows 10 IoT Core 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8384e-174">The Azure Active Directory Authentication Library does not work on Windows 10 IoT Core.</span></span>  

### <a name="shell-management-of-application-crashes"></a><span data-ttu-id="8384e-175">응용 프로그램 충돌의 셸 관리</span><span class="sxs-lookup"><span data-stu-id="8384e-175">Shell Management of Application Crashes</span></span>
<span data-ttu-id="8384e-176">IoT Core shell 인프라 APPX 형 응용 프로그램 충돌에 대 한 장치에서 실행을 모니터링 하 고 작동 중단 발생 시 해당 응용 프로그램을 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="8384e-176">IoT Core’s shell infrastructure monitors APPX-type applications running on the device for crashes, and restarts those applications when crashes occur.</span></span>  <span data-ttu-id="8384e-177">다시 시작된 응용 프로그램에 계속 셸에서 failfast-버그 확인 시키는 중요 한 시스템 프로세스를 적용할를 복구 하기 위해 다시 부팅 합니다.</span><span class="sxs-lookup"><span data-stu-id="8384e-177">If the restarted applications continue to crash, the shell will employ a failfast – a system critical process that causes a bugcheck and reboot in an attempt to recover.</span></span>  <span data-ttu-id="8384e-178">비교할 수 있는 논리와 처리는 백그라운드 작업 및 헤드 구성에서 포그라운드 응용 프로그램에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8384e-178">Comparable logic and handling is used to background tasks and foreground applications in a headed configuration.</span></span>   <span data-ttu-id="8384e-179">충돌 처리 및 재시도 논리는 아래 캡처됩니다.</span><span class="sxs-lookup"><span data-stu-id="8384e-179">Crash handling and retry logic is captured below:</span></span>

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

<span data-ttu-id="8384e-180">지연 시간을 기다린 후 앱을 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="8384e-180">Wait for the delay and relaunch the app.</span></span>

#### <a name="dragonboard-spi-runs-at-48mhz"></a><span data-ttu-id="8384e-181">4.8 mhz Dragonboard SPI 실행</span><span class="sxs-lookup"><span data-stu-id="8384e-181">Dragonboard SPI runs at 4.8Mhz</span></span>
<span data-ttu-id="8384e-182">에 Dragonboard SPI 요청된 속도 무시 하 고 4.8 mhz 항상 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8384e-182">The SPI on the Dragonboard will ignore the requested speed and always run at 4.8 Mhz.</span></span>  

#### <a name="dragonboard-connected-standby"></a><span data-ttu-id="8384e-183">Dragonboard 대기 연결</span><span class="sxs-lookup"><span data-stu-id="8384e-183">Dragonboard Connected Standby</span></span> 
<span data-ttu-id="8384e-184">연결 된 대기 Qualcomm Dragonboard에서 기본적으로 사용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8384e-184">Connected Standby is not enabled on the Qualcomm Dragonboard by default.</span></span>  <span data-ttu-id="8384e-185">DragonBoard에 연결 된 대기 상태를 사용 하도록 설정 하려면 다음 레지스트리 키 "1"로 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8384e-185">To enable Connected Standby on DragonBoard the following registry key needs to be set to “1”.</span></span>


### <a name="time-synchronization"></a><span data-ttu-id="8384e-186">시간 동기화</span><span class="sxs-lookup"><span data-stu-id="8384e-186">Time synchronization</span></span>
<span data-ttu-id="8384e-187">시간 동기화 실패 하거나 시간 초과이 연결할 수 없는 때문일 수 있습니다 또는 먼 시간 서버를 다음 수행할 수 있는 시간을 추가 또는 로컬 서버를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="8384e-187">If time sync is failing or timing out this may be due to unreachable or a distant time server, the following can be done to add additional or local time servers.</span></span> 
 
1. <span data-ttu-id="8384e-188">(예: 장치의 명령줄에서</span><span class="sxs-lookup"><span data-stu-id="8384e-188">From a command line on the device (eg.</span></span> <span data-ttu-id="8384e-189">SSH, Powershell).</span><span class="sxs-lookup"><span data-stu-id="8384e-189">SSH, Powershell).</span></span>
   ```
   w32tm /config /syncfromflags:manual /manualpeerlist:"0.windows.time.com 1.pool.ntp.org 2.something else, ..."
   ```
2. <span data-ttu-id="8384e-190">부팅 스크립트를 통해 레지스트리에 이러한 추가 기능을 만들 수 있습니다 하거나 필요한 경우 이미지 만들기 프로세스의 일부분으로 사용자 지정 런타임을 구성 패키지를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="8384e-190">You may also make these additions to the registry via a boot script or a custom runtime configuration package included as part of the image creation process if needed.</span></span> 

### <a name="starting-the-ftp-server"></a><span data-ttu-id="8384e-191">FTP 서버를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="8384e-191">Starting the FTP Server</span></span> 
* <span data-ttu-id="8384e-192">SSH\PS 사용 하 여 로그인을 한 번만 실행 및 FTP를 시작 하려면이 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="8384e-192">To run once - Login with SSH\PS and run this command to start FTP:</span></span>  

```
start ftpd.exe 
```

* <span data-ttu-id="8384e-193">모든 부팅을 실행 하려면 사용자가 해야 스케줄러 작업-SSH\PS 사용 하 여 로그인을 만들고 스케줄러 작업 만들기:</span><span class="sxs-lookup"><span data-stu-id="8384e-193">To run on every boot, users should create a scheduler task - Login with SSH\PS and create a scheduler task:</span></span>

```
schtasks /create /tn "IoTFTPD" /tr ftpd.exe /ru system /sc onstart 
Schtasks /run /tn “IoTFTPD” 
```

### <a name="partition-size-requirements-for-update"></a><span data-ttu-id="8384e-194">업데이트에 대 한 파티션 크기 요구 사항</span><span class="sxs-lookup"><span data-stu-id="8384e-194">Partition size requirements for Update</span></span> 
<span data-ttu-id="8384e-195">업데이트 기능에 대 한 충분 한 공간을 유지 하는 데이터 파티션을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="8384e-195">Ensure data partition maintains sufficient space for update functionality.</span></span><span data-ttu-id="8384e-196">  1GB 전체 업데이트 기능을 무료로 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8384e-196">  We recommend 1GB free for full update functionality.</span></span> <span data-ttu-id="8384e-197"> 데이터 파티션에 충분 한 공간이 없는 경우 설치 단계에서 업데이트가 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="8384e-197"> If Data partition does not have enough space, updates will fail in the installation phase.</span></span> 

### <a name="powershell-log-generation-on-iot-core"></a><span data-ttu-id="8384e-198">IoT Core에 PowerShell 로그 생성</span><span class="sxs-lookup"><span data-stu-id="8384e-198">PowerShell log generation on IoT Core</span></span> 
<span data-ttu-id="8384e-199">Iot Core에는 PowerShell 파일 시스템에서 공간을 차지 하는 기본적으로 로그 파일을 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8384e-199">PowerShell on Iot Core may generate log files by default taking up space on the filesystem.</span></span> <span data-ttu-id="8384e-200">로그 파일 크기는 제한 되지만, 무엇 보다도 개선할 수 있는 업데이트 하지 못한 부족 한 디스크 공간 상황에서는 잠재적으로 발생 하는 공간 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8384e-200">Although the log file sizes are limited they can take up space potentially resulting in a low disk space situation which, among other things, can result in updates failing.</span></span> <span data-ttu-id="8384e-201">이벤트.evtx 로그가 미리 정의 된 최대 크기는 20MB입니다.</span><span class="sxs-lookup"><span data-stu-id="8384e-201">The .evtx event log files have a predefined maximum size of 20 MB each.</span></span> <span data-ttu-id="8384e-202">레지스트리를 통해 다양 한 최대 크기를 사용 하려면 파일이 개별적으로 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8384e-202">You  can individually limit files to have a different max size via registry.</span></span> <span data-ttu-id="8384e-203">예를 들어 10MB 최대 크기로 security.evtx를 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="8384e-203">For example, To keep security.evtx at 10 MB max size:</span></span> 
```
regd add HKLM\SYSTEM\CurrentControlSet\Services\EventLog\Security /v MaxSize /t REG_DWORD /d 0xa00000 /f 
```

### <a name="schtasks-limitation"></a><span data-ttu-id="8384e-204">Schtasks 제한</span><span class="sxs-lookup"><span data-stu-id="8384e-204">Schtasks limitation</span></span>  
<span data-ttu-id="8384e-205">Schtasks는 /xml 스위치를 사용 하는 것을 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8384e-205">Schtasks does not support using /xml switch.</span></span> <span data-ttu-id="8384e-206">예를 들어 다음과 같은 가치를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8384e-206">For example:</span></span> 
```
schtasks /create /xml <xmlfile> /TN <taskname>
```
<span data-ttu-id="8384e-207">IoT Core에 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="8384e-207">This will fail on IoT Core.</span></span> <span data-ttu-id="8384e-208">명령을 실행 하면 오류가 생성 됩니다. 오류: 지정된 된 프로시저를 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8384e-208">Running the command will generate the error: ERROR: The specified procedure could not be found.</span></span> 
