---
title: Windows 디버거
author: bfjelds
ms.author: bfjelds
ms.date: 08/28/2017
ms.topic: article
description: Windows 디버거를 사용 하 여 Windows IoT Core 장치를 디버그 하는 방법에 알아봅니다.
keywords: windows iot, 디버거, 디버깅, Windows 디버거, 장치, 도구
ms.openlocfilehash: e56f5ca837de79aaf0c36cf7d3c6ae6badf3fd16
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513302"
---
# <a name="windows-debugger-windbg"></a><span data-ttu-id="27e71-104">Windows 디버거 (WinDbg)</span><span class="sxs-lookup"><span data-stu-id="27e71-104">Windows Debugger (WinDbg)</span></span>
<span data-ttu-id="27e71-105">강력한 Windows 디버거, WinDbg를 사용 하 여 Windows 10 IoT Core 장치를 디버그 합니다.</span><span class="sxs-lookup"><span data-stu-id="27e71-105">Debug your Windows 10 IoT Core device using the powerful Windows debugger, WinDbg.</span></span>

<span data-ttu-id="27e71-106">다음 섹션에서는 WinDbg를 사용 하 여 디버깅을 위해 Windows 10 IoT Core 장치에 성공적으로 연결 하는 방법에 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="27e71-106">The following sections describe how to successfully connect with WinDbg to a Windows 10 IoT Core device for debugging purposes.</span></span>  <span data-ttu-id="27e71-107">물리적 하드웨어 연결 뿐만 아니라 장치에 필요한 소프트웨어 설정에 대 한 설명을 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="27e71-107">This includes a description of the necessary software settings on the device as well as the physical hardware connections.</span></span>  

<span data-ttu-id="27e71-108">WinDbg는 대부분의 Windows 개발자는 잘 알고 있는 강력한 디버거를 합니다.</span><span class="sxs-lookup"><span data-stu-id="27e71-108">WinDbg is a very powerful debugger that most Windows developers are familiar with.</span></span>  <span data-ttu-id="27e71-109">그러나 바로 시작 하 고 WinDbg에 대 한 자세한 정보를 알아보려면 다음 링크를</span><span class="sxs-lookup"><span data-stu-id="27e71-109">However, if you are just getting started and would like to learn more about WinDbg, please visit the following links:</span></span>

* [<span data-ttu-id="27e71-110">Windows용 디버깅 도구</span><span class="sxs-lookup"><span data-stu-id="27e71-110">Debugging Tools for Windows</span></span>](https://msdn.microsoft.com/library/windows/hardware/ff551063(v=vs.85).aspx) 

* [<span data-ttu-id="27e71-111">Windows 디버깅을 시작 하기</span><span class="sxs-lookup"><span data-stu-id="27e71-111">Getting Started with Windows Debugging</span></span>](https://msdn.microsoft.com/library/windows/hardware/mt219729(v=vs.85).aspx) 

* [<span data-ttu-id="27e71-112">Crash Dump Analysis WinDbg를 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="27e71-112">Crash Dump Analysis Using WinDbg</span></span>](https://msdn.microsoft.com/library/windows/hardware/ff539316(v=vs.85).aspx) 


## <a name="minnowboard-max-mbm"></a><span data-ttu-id="27e71-113">MinnowBoard 최대 MBM)</span><span class="sxs-lookup"><span data-stu-id="27e71-113">MinnowBoard Max (MBM)</span></span> 

<span data-ttu-id="27e71-114">네트워크 연결을 사용 하 여 MinnowBoard 최대 장치로 WinDbg를 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27e71-114">You can connect WinDbg to the MinnowBoard Max device using a network connection.</span></span>

### <a name="setup-network-connection"></a><span data-ttu-id="27e71-115">네트워크 연결 설정</span><span class="sxs-lookup"><span data-stu-id="27e71-115">Setup network connection</span></span>

<span data-ttu-id="27e71-116">네트워크를 통해 WinDbg를 사용 하 여 커널 디버깅을 사용 하기 위해을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="27e71-116">In order to enable kernel debugging with WinDbg over a network, ensure that:</span></span>

* <span data-ttu-id="27e71-117">이더넷 케이블 MinnowBoard 최대 장치를 네트워크에 연결 되어</span><span class="sxs-lookup"><span data-stu-id="27e71-117">An Ethernet cable is connected to MinnowBoard Max device to your network</span></span> 

* <span data-ttu-id="27e71-118">MinnowBoard 최대 장치가 네트워크에 대 한 유효한 IP 주소</span><span class="sxs-lookup"><span data-stu-id="27e71-118">The MinnowBoard Max device has a valid IP address in your network</span></span>

* <span data-ttu-id="27e71-119">활성 연결을 통해 MinnowBoard 최대 장치로 [PowerShell](../connect-your-device/PowerShell.md)</span><span class="sxs-lookup"><span data-stu-id="27e71-119">An active connection to the MinnowBoard Max device via [PowerShell](../connect-your-device/PowerShell.md)</span></span> 

<span data-ttu-id="27e71-120">현재 PowerShell 연결을 사용 하 MinnowBoard 최대 네트워크를 통해 디버깅을 사용 하려면에서 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="27e71-120">Using the active PowerShell connection, execute the following commands on the MinnowBoard Max to enable debugging over the network.</span></span>

* `bcdedit -dbgsettings net hostip:<DEV_PC_IP_ADDRESS> port:<PORT_NUM> key:<KEY>` 

    * <span data-ttu-id="27e71-121">이 명령은 네트워크를 통해 디버깅할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27e71-121">This command enables debugging over the network.</span></span>  <span data-ttu-id="27e71-122">또한 여기서 WinDbg 실행 됩니다 (DEV_PC_IP_ADDRESS) PC의 IP 주소를 지정 (PORT_NUM) 연결과 고유 키에 대 한 여러 연결 (키)를 구분 하는 데 사용 하는 네트워크 포트 번호</span><span class="sxs-lookup"><span data-stu-id="27e71-122">Additionally, it specifies the IP address of the PC where WinDbg will be running (DEV_PC_IP_ADDRESS), the network port number to use for the connection (PORT_NUM), and a unique key to be used to differentiate multiple connections (KEY)</span></span> 

    * <span data-ttu-id="27e71-123">PORT_NUM와 키에 대 한 예제로 다음 값을 사용할 수 있습니다. 50045 및 1.2.3.4 각각 수는 있지만 가능 하다 면 이러한 변경</span><span class="sxs-lookup"><span data-stu-id="27e71-123">For PORT_NUM and KEY, you can use the following values as examples: 50045 and 1.2.3.4 respectively, although you are free to change them as you see fit</span></span>
    
* `bcdedit -debug on`

    * <span data-ttu-id="27e71-124">이 명령은 장치에서 디버깅 설정</span><span class="sxs-lookup"><span data-stu-id="27e71-124">This command turns on debugging on the device</span></span> 

* <span data-ttu-id="27e71-125">개발자 PC에서 WinDbg를 PORT_NUM와 같이 이전 단계에서 제공 되는 키 값 시작: `"c:\Program Files (x86)\Debugging Tools for Windows (x86)\windbg.exe" -k net:port=<PORT_NUM>,key=<KEY>`</span><span class="sxs-lookup"><span data-stu-id="27e71-125">On the developer PC, start WinDbg with the PORT_NUM and the KEY values provided in the previous steps as follows: `"c:\Program Files (x86)\Debugging Tools for Windows (x86)\windbg.exe" -k net:port=<PORT_NUM>,key=<KEY>`</span></span>

> [!NOTE]
> <span data-ttu-id="27e71-126">설치 된 Windows 키트에 있는 경우에 WinDbg 아래을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27e71-126">If you have any of the Windows kits installed, you may find WinDbg under</span></span>
`C:\Program Files (x86)\Windows Kits\10\Debuggers\x86\WinDbg.exe</code>`

* <span data-ttu-id="27e71-127">디버거를 연결할 IoTCore 장치를 다시 부팅</span><span class="sxs-lookup"><span data-stu-id="27e71-127">Reboot the IoTCore device to reconnect to the debugger</span></span>

## <a name="raspberry-pi-2-or-3-rpi2-or-rpi3"></a><span data-ttu-id="27e71-128">Raspberry Pi 2 또는 3 (RPi2 또는 RPi3)</span><span class="sxs-lookup"><span data-stu-id="27e71-128">Raspberry Pi 2 or 3 (RPi2 or RPi3)</span></span> 

<span data-ttu-id="27e71-129">WinDbg는 Raspberry Pi 2 또는 3 대 한 직렬 연결을 사용 하 여 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27e71-129">You can connect WinDbg to the Raspberry Pi 2 or 3 using a serial connection.</span></span>

### <a name="setup-serial-connection"></a><span data-ttu-id="27e71-130">직렬 연결 설정</span><span class="sxs-lookup"><span data-stu-id="27e71-130">Setup serial connection</span></span>

<span data-ttu-id="27e71-131">직렬 연결을 통해 WinDbg를 사용 하 여 커널 디버깅을 사용 하기 위해을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="27e71-131">In order to enable kernel debugging with WinDbg over a serial connection, ensure that:</span></span>

* <span data-ttu-id="27e71-132">USB-TTL 직렬 케이블을 같은 디버그 케이블이 [Adafruit](https://www.adafruit.com/product/954) 하거나 [FTDI](http://shop.clickandbuild.com/cnb/shop/ftdichip?productID=53&op=catalogue-product_info-null&prodCategoryID=105)합니다.</span><span class="sxs-lookup"><span data-stu-id="27e71-132">You have a debug cable such as the USB-to-TTL Serial Cable from [Adafruit](https://www.adafruit.com/product/954) or [FTDI](http://shop.clickandbuild.com/cnb/shop/ftdichip?productID=53&op=catalogue-product_info-null&prodCategoryID=105).</span></span> 

* <span data-ttu-id="27e71-133">이더넷 케이블이 나 (SSH 또는 PowerShell과 같은 IP 연결)에 대 한 네트워크에 Raspberry Pi 2 또는 3 장치를 연결 하는 활성 WiFi를</span><span class="sxs-lookup"><span data-stu-id="27e71-133">An Ethernet cable or active WiFi connecting your Raspberry Pi 2 or 3 device to your network (for IP connections like SSH or PowerShell)</span></span>

* <span data-ttu-id="27e71-134">Raspberry Pi 2 또는 3 장치에 올바른 IP 주소를 네트워크</span><span class="sxs-lookup"><span data-stu-id="27e71-134">The Raspberry Pi 2 or 3 device has a valid IP address in your network</span></span>

* <span data-ttu-id="27e71-135">Raspberry Pi 2 또는 3 장치를 통해 활성 연결이 [PowerShell](../connect-your-device/PowerShell.md) 또는 [SSH](../connect-your-device/SSH.md)</span><span class="sxs-lookup"><span data-stu-id="27e71-135">An active connection to the Raspberry Pi 2 or 3 device via [PowerShell](../connect-your-device/PowerShell.md) or [SSH](../connect-your-device/SSH.md)</span></span>

<span data-ttu-id="27e71-136">UART0은 Raspberry Pi 2 또는 3 장치 커널 디버깅 연결에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="27e71-136">UART0 will be used on the Raspberry Pi 2 or 3 device for the kernel debugging connection.</span></span>  <span data-ttu-id="27e71-137">다음은 직렬 케이블 뿐만 아니라 Raspberry Pi 2 또는 3 핀 매핑.</span><span class="sxs-lookup"><span data-stu-id="27e71-137">The following shows the pin mappings for the Raspberry Pi 2 or 3 as well as the serial cables:</span></span> 

        Raspberry Pi 2 or 3 pins:
            Pin #6 : GND
            Pin #8 : UART0 TX (3.3V)
            pin #10: UART0 RX (3.3V)

        Adafruit Cable:
            Black  : GND
            White  : RX  (3.3V)
            Green  : TX  (3.3V)
            Red    : PWR (5.0V NOT USED) <- DO NOT CONNECT!!
        
        FTDI Cable:
            Black  : GND
            Brown  : CTS (NOT USED)
            Red    : PWR (5.0V NOT USED) <- DO NOT CONNECT!!
            Orange : TX  (3.3V)
            Yellow : RX  (3.3V)
            Green  : RTS (NOT USED)
            
<span data-ttu-id="27e71-138">올바른 직렬 연결에 대 한 기본 개념 하나의 장치에서는 해당 TX 데이터를 전송 하는 동안 다른 장치 데이터를 수신 하는 RX를 사용 해야 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="27e71-138">The basic idea for making the correct serial connections is to remember that while one device uses its TX to transmit data, the other device uses its RX to receive the data.</span></span>  <span data-ttu-id="27e71-139">연결 권장된 사항은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="27e71-139">Recommended connections are listed below:</span></span>

        If using Adafruit's serial cable:
            [RPi2 or RPi3] Pin #6  (GND) <-> [Adafruti] Black (GND)
            [RPi2 or RPi3] Pin #8  (TX)  <-> [Adafruit] White (RX) 
            [RPi2 or RPi3] Pin #10 (RX)  <-> [Adafruit] Green (TX)
        
        If using FTDI's serial cable:
            [RPi2 or RPi3] Pin #6  (GND) <-> [FTDI] Black  (GND)
            [RPi2 or RPi3] Pin #8  (TX)  <-> [FTDI] Yellow (RX) 
            [RPi2 or RPi3] Pin #10 (RX)  <-> [FTDI] ORange (TX)

> [!NOTE] 
> <span data-ttu-id="27e71-140">더 이상 EFIESP 접합이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="27e71-140">The EFIESP junction is no longer created.</span></span> <span data-ttu-id="27e71-141">직접 탑재 해야, GUID를 가져올 mountvol 명령을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27e71-141">You'll have to mount it yourself,you can use mountvol command to get the GUID.</span></span>
`mkdir C:\EFIESP` 
`mountvol C:\EFIESP \?\Volume{ae420040-0000-0000-0000-200000000000}` 

<span data-ttu-id="27e71-142">활성 PowerShell 연결을 사용 하 여, 직렬 연결을 통해 디버깅을 사용 하려면 Raspberry Pi 2 또는 3 장치에서 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="27e71-142">Using the active PowerShell connection, execute the following commands on the Raspberry Pi 2 or 3 device to enable debugging over the serial connection.</span></span>

* `bcdedit /store c:\EFIESP\EFI\Microsoft\Boot\BCD -dbgsettings serial` 

    * <span data-ttu-id="27e71-143">위의 명령은 디버깅에 대 한 직렬 연결을 설정</span><span class="sxs-lookup"><span data-stu-id="27e71-143">The above command enables the serial connection for debugging</span></span>
    * <span data-ttu-id="27e71-144">Raspberry Pi 2 또는 3에 대 한 전송 속도 이므로 921600,으로 하드 코딩 지정할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="27e71-144">The baud-rate for the Raspberry Pi 2 or 3 is hard-coded to 921600, so you don't have to specify it</span></span>

* `bcdedit /store c:\EFIESP\EFI\Microsoft\Boot\BCD -debug on`

    * <span data-ttu-id="27e71-145">이 명령은 장치에서 디버깅 설정</span><span class="sxs-lookup"><span data-stu-id="27e71-145">This command turns on debugging on the device</span></span> 

<span data-ttu-id="27e71-146">개발자 PC에 USB-TTL 케이블 시스템의 할당 된 포트 번호 포트를 COM 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="27e71-146">On the developer PC, get the COM port number PORT assigned in the system for the USB-to-TTL cable.</span></span> <span data-ttu-id="27e71-147">이 장치 관리자에서 "포트 (COM 및 LPT)" 아래에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27e71-147">This will be available in Device Manager under "Ports (COM & LPT)".</span></span>

* `"C:\Program Files (x86)\Debugging Tools for Windows (x86)\windbg.exe" -k com:port=<PORT>,baud=921600` 

    * <span data-ttu-id="27e71-148">포트 번호를 사용 하 여 WinDbg 시작</span><span class="sxs-lookup"><span data-stu-id="27e71-148">Start WinDbg with the PORT number</span></span>
    
> [!NOTE]
> <span data-ttu-id="27e71-149">설치 된 Windows 키트에 있는 경우에 WinDbg 아래을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27e71-149">If you have any of the Windows kits installed, you may find WinDbg under</span></span>
`C:\Program Files (x86)\Windows Kits\10\Debuggers\x86\WinDbg.exe`

* <span data-ttu-id="27e71-150">디버거를 연결할 IoTCore 장치를 다시 부팅</span><span class="sxs-lookup"><span data-stu-id="27e71-150">Reboot the IoTCore device to reconnect to the debugger</span></span>


## <a name="dragonboard-db"></a><span data-ttu-id="27e71-151">DragonBoard (DB)</span><span class="sxs-lookup"><span data-stu-id="27e71-151">DragonBoard (DB)</span></span> 
___

<span data-ttu-id="27e71-152">WinDbg는 직렬 또는 USB 연결을 사용 하 여 DragonBoard 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27e71-152">You can connect WinDbg to the DragonBoard using a serial or USB connection.</span></span>

<span data-ttu-id="27e71-153">디버깅을 사용 하려면 다음 명령을 실행 하 여 DragonBoard 현재 PowerShell 또는 SSH 연결을 사용 하 합니다.</span><span class="sxs-lookup"><span data-stu-id="27e71-153">Using the active PowerShell or SSH connection to your DragonBoard, execute the following commands to enable debugging.</span></span>

* `bcdedit /store c:\EFIESP\EFI\Microsoft\Boot\BCD /debug {default} ON`
    * <span data-ttu-id="27e71-154">디버거를 사용 하도록 설정</span><span class="sxs-lookup"><span data-stu-id="27e71-154">Enables the debugger</span></span>

### <a name="setup-usb-connection"></a><span data-ttu-id="27e71-155">USB 연결 설정</span><span class="sxs-lookup"><span data-stu-id="27e71-155">Setup USB connection</span></span>
<span data-ttu-id="27e71-156">기본적으로 USB 디버거 설정 테스트 이미지에서 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="27e71-156">By default the USB debugger settings are configured in the test images.</span></span> 

> [!NOTE]
> <span data-ttu-id="27e71-157">USB 커널 디버거를 DragonBoard 장치에서 USB 포트 (예:: 키보드, usb 이더넷 작동 하지 않을 수 있습니다) 작동 하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27e71-157">Once USB kernel debugger is on, USB ports on the DragonBoard device might not work (i.e. keyboard, usb ethernet might not work).</span></span>

### <a name="setup-serial-connection"></a><span data-ttu-id="27e71-158">직렬 연결 설정</span><span class="sxs-lookup"><span data-stu-id="27e71-158">Setup serial connection</span></span>

* `bcdedit /store c:\EFIESP\EFI\Microsoft\Boot\BCD /dbgsettings  Serial debugport:1 baudrate:115200`
    * <span data-ttu-id="27e71-159">직렬 포트를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="27e71-159">Configures the serial port</span></span>

* <span data-ttu-id="27e71-160">디버거를 연결할 IoTCore 장치를 다시 부팅</span><span class="sxs-lookup"><span data-stu-id="27e71-160">Reboot the IoTCore device to reconnect to the debugger</span></span>
