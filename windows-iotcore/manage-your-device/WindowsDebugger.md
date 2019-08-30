---
title: Windows 디버거
author: bfjelds
ms.author: bfjelds
ms.date: 08/28/2017
ms.topic: article
description: Windows 디버거를 사용 하 여 Windows IoT Core 장치를 디버그 하는 방법을 알아봅니다.
keywords: windows iot, 디버거, 디버깅, Windows 디버거, 장치, 도구
ms.openlocfilehash: e56f5ca837de79aaf0c36cf7d3c6ae6badf3fd16
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "60170281"
---
# <a name="windows-debugger-windbg"></a><span data-ttu-id="021e8-104">Windows 디버거 (WinDbg)</span><span class="sxs-lookup"><span data-stu-id="021e8-104">Windows Debugger (WinDbg)</span></span>
<span data-ttu-id="021e8-105">강력한 Windows 디버거 인 WinDbg를 사용 하 여 Windows 10 IoT Core 장치를 디버깅 합니다.</span><span class="sxs-lookup"><span data-stu-id="021e8-105">Debug your Windows 10 IoT Core device using the powerful Windows debugger, WinDbg.</span></span>

<span data-ttu-id="021e8-106">다음 섹션에서는 디버깅을 위해 WinDbg를 Windows 10 IoT Core 장치에 성공적으로 연결 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="021e8-106">The following sections describe how to successfully connect with WinDbg to a Windows 10 IoT Core device for debugging purposes.</span></span>  <span data-ttu-id="021e8-107">여기에는 장치에 대 한 필수 소프트웨어 설정 및 실제 하드웨어 연결에 대 한 설명이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="021e8-107">This includes a description of the necessary software settings on the device as well as the physical hardware connections.</span></span>  

<span data-ttu-id="021e8-108">WinDbg는 대부분의 Windows 개발자가 친숙 한 매우 강력한 디버거입니다.</span><span class="sxs-lookup"><span data-stu-id="021e8-108">WinDbg is a very powerful debugger that most Windows developers are familiar with.</span></span>  <span data-ttu-id="021e8-109">그러나 처음 시작 하 고 WinDbg에 대해 자세히 알아보려면 다음 링크를 방문 하세요.</span><span class="sxs-lookup"><span data-stu-id="021e8-109">However, if you are just getting started and would like to learn more about WinDbg, please visit the following links:</span></span>

* <span data-ttu-id="021e8-110">[Windows 용 디버깅 도구](https://msdn.microsoft.com/library/windows/hardware/ff551063(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="021e8-110">[Debugging Tools for Windows](https://msdn.microsoft.com/library/windows/hardware/ff551063(v=vs.85).aspx)</span></span> 

* <span data-ttu-id="021e8-111">[Windows 디버깅 시작](https://msdn.microsoft.com/library/windows/hardware/mt219729(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="021e8-111">[Getting Started with Windows Debugging](https://msdn.microsoft.com/library/windows/hardware/mt219729(v=vs.85).aspx)</span></span> 

* <span data-ttu-id="021e8-112">[WinDbg를 사용 하 여 크래시 덤프 분석](https://msdn.microsoft.com/library/windows/hardware/ff539316(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="021e8-112">[Crash Dump Analysis Using WinDbg](https://msdn.microsoft.com/library/windows/hardware/ff539316(v=vs.85).aspx)</span></span> 


## <a name="minnowboard-max-mbm"></a><span data-ttu-id="021e8-113">MinnowBoard Max (MBM)</span><span class="sxs-lookup"><span data-stu-id="021e8-113">MinnowBoard Max (MBM)</span></span> 

<span data-ttu-id="021e8-114">네트워크 연결을 사용 하 여 WinDbg를 MinnowBoard Max 장치에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="021e8-114">You can connect WinDbg to the MinnowBoard Max device using a network connection.</span></span>

### <a name="setup-network-connection"></a><span data-ttu-id="021e8-115">네트워크 연결 설정</span><span class="sxs-lookup"><span data-stu-id="021e8-115">Setup network connection</span></span>

<span data-ttu-id="021e8-116">네트워크를 통해 WinDbg에서 커널 디버깅을 사용 하도록 설정 하려면 다음을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="021e8-116">In order to enable kernel debugging with WinDbg over a network, ensure that:</span></span>

* <span data-ttu-id="021e8-117">이더넷 케이블은 MinnowBoard Max 장치에 네트워크에 연결 됩니다.</span><span class="sxs-lookup"><span data-stu-id="021e8-117">An Ethernet cable is connected to MinnowBoard Max device to your network</span></span> 

* <span data-ttu-id="021e8-118">MinnowBoard Max 장치는 네트워크에 유효한 IP 주소를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="021e8-118">The MinnowBoard Max device has a valid IP address in your network</span></span>

* <span data-ttu-id="021e8-119">[PowerShell](../connect-your-device/PowerShell.md) 을 통해 MinnowBoard Max 장치에 대 한 활성 연결</span><span class="sxs-lookup"><span data-stu-id="021e8-119">An active connection to the MinnowBoard Max device via [PowerShell](../connect-your-device/PowerShell.md)</span></span> 

<span data-ttu-id="021e8-120">활성 PowerShell 연결을 사용 하 여 MinnowBoard Max에서 다음 명령을 실행 하 여 네트워크를 통해 디버깅을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="021e8-120">Using the active PowerShell connection, execute the following commands on the MinnowBoard Max to enable debugging over the network.</span></span>

* `bcdedit -dbgsettings net hostip:<DEV_PC_IP_ADDRESS> port:<PORT_NUM> key:<KEY>` 

    * <span data-ttu-id="021e8-121">이 명령은 네트워크를 통해 디버깅을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="021e8-121">This command enables debugging over the network.</span></span>  <span data-ttu-id="021e8-122">또한 WinDbg를 실행 하는 PC의 IP 주소 (DEV_PC_IP_ADDRESS), 연결에 사용할 네트워크 포트 번호 (PORT_NUM) 및 여러 연결을 구분 하는 데 사용할 고유 키 (키)를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="021e8-122">Additionally, it specifies the IP address of the PC where WinDbg will be running (DEV_PC_IP_ADDRESS), the network port number to use for the connection (PORT_NUM), and a unique key to be used to differentiate multiple connections (KEY)</span></span> 

    * <span data-ttu-id="021e8-123">PORT_NUM 및 키의 경우 다음 값을 예제로 사용할 수 있습니다. 50045 및 1.2.3.4 각각에 맞게 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="021e8-123">For PORT_NUM and KEY, you can use the following values as examples: 50045 and 1.2.3.4 respectively, although you are free to change them as you see fit</span></span>
    
* `bcdedit -debug on`

    * <span data-ttu-id="021e8-124">이 명령은 장치에서 디버깅을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="021e8-124">This command turns on debugging on the device</span></span> 

* <span data-ttu-id="021e8-125">개발자 PC에서 다음과 같이 이전 단계에서 제공 된 PORT_NUM 및 키 값을 사용 하 여 WinDbg를 시작 합니다.`"c:\Program Files (x86)\Debugging Tools for Windows (x86)\windbg.exe" -k net:port=<PORT_NUM>,key=<KEY>`</span><span class="sxs-lookup"><span data-stu-id="021e8-125">On the developer PC, start WinDbg with the PORT_NUM and the KEY values provided in the previous steps as follows: `"c:\Program Files (x86)\Debugging Tools for Windows (x86)\windbg.exe" -k net:port=<PORT_NUM>,key=<KEY>`</span></span>

> [!NOTE]
> <span data-ttu-id="021e8-126">Windows 키트가 설치 되어 있는 경우 다음 위치에서 WinDbg를 찾을 수 있습니다.`C:\Program Files (x86)\Windows Kits\10\Debuggers\x86\WinDbg.exe</code>`</span><span class="sxs-lookup"><span data-stu-id="021e8-126">If you have any of the Windows kits installed, you may find WinDbg under `C:\Program Files (x86)\Windows Kits\10\Debuggers\x86\WinDbg.exe</code>`</span></span>

* <span data-ttu-id="021e8-127">디버거를 다시 연결 하려면 IoTCore 장치를 다시 부팅 합니다.</span><span class="sxs-lookup"><span data-stu-id="021e8-127">Reboot the IoTCore device to reconnect to the debugger</span></span>

## <a name="raspberry-pi-2-or-3-rpi2-or-rpi3"></a><span data-ttu-id="021e8-128">Raspberry Pi 2 또는 3 (RPi2 또는 RPi3)</span><span class="sxs-lookup"><span data-stu-id="021e8-128">Raspberry Pi 2 or 3 (RPi2 or RPi3)</span></span> 

<span data-ttu-id="021e8-129">직렬 연결을 사용 하 여 WinDbg를 Raspberry Pi 2 또는 3에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="021e8-129">You can connect WinDbg to the Raspberry Pi 2 or 3 using a serial connection.</span></span>

### <a name="setup-serial-connection"></a><span data-ttu-id="021e8-130">직렬 연결 설정</span><span class="sxs-lookup"><span data-stu-id="021e8-130">Setup serial connection</span></span>

<span data-ttu-id="021e8-131">직렬 연결을 통해 WinDbg에서 커널 디버깅을 사용 하도록 설정 하려면 다음을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="021e8-131">In order to enable kernel debugging with WinDbg over a serial connection, ensure that:</span></span>

* <span data-ttu-id="021e8-132">[Adafruit](https://www.adafruit.com/product/954) 또는 [FTDI](http://shop.clickandbuild.com/cnb/shop/ftdichip?productID=53&op=catalogue-product_info-null&prodCategoryID=105)의 USB-TTL 직렬 케이블과 같은 디버그 케이블이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="021e8-132">You have a debug cable such as the USB-to-TTL Serial Cable from [Adafruit](https://www.adafruit.com/product/954) or [FTDI](http://shop.clickandbuild.com/cnb/shop/ftdichip?productID=53&op=catalogue-product_info-null&prodCategoryID=105).</span></span> 

* <span data-ttu-id="021e8-133">Raspberry Pi 2 또는 3 장치를 네트워크에 연결 하는 이더넷 케이블 또는 활성 WiFi (SSH 또는 PowerShell과 같은 IP 연결의 경우)</span><span class="sxs-lookup"><span data-stu-id="021e8-133">An Ethernet cable or active WiFi connecting your Raspberry Pi 2 or 3 device to your network (for IP connections like SSH or PowerShell)</span></span>

* <span data-ttu-id="021e8-134">Raspberry Pi 2 또는 3 장치는 네트워크에 유효한 IP 주소를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="021e8-134">The Raspberry Pi 2 or 3 device has a valid IP address in your network</span></span>

* <span data-ttu-id="021e8-135">[PowerShell](../connect-your-device/PowerShell.md) 또는 [SSH](../connect-your-device/SSH.md) 를 통해 Raspberry Pi 2 또는 3 장치에 대 한 활성 연결</span><span class="sxs-lookup"><span data-stu-id="021e8-135">An active connection to the Raspberry Pi 2 or 3 device via [PowerShell](../connect-your-device/PowerShell.md) or [SSH](../connect-your-device/SSH.md)</span></span>

<span data-ttu-id="021e8-136">UART0은 커널 디버깅 연결을 위해 Raspberry Pi 2 또는 3 장치에서 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="021e8-136">UART0 will be used on the Raspberry Pi 2 or 3 device for the kernel debugging connection.</span></span>  <span data-ttu-id="021e8-137">다음은 직렬 케이블 뿐만 아니라 Raspberry Pi 2 또는 3에 대 한 pin 매핑을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="021e8-137">The following shows the pin mappings for the Raspberry Pi 2 or 3 as well as the serial cables:</span></span> 

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
            
<span data-ttu-id="021e8-138">올바른 직렬 연결을 설정 하는 기본적인 이유는 한 장치가 해당 TX를 사용 하 여 데이터를 전송 하는 동안 다른 장치는 해당 RX를 사용 하 여 데이터를 받는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="021e8-138">The basic idea for making the correct serial connections is to remember that while one device uses its TX to transmit data, the other device uses its RX to receive the data.</span></span>  <span data-ttu-id="021e8-139">권장 연결은 아래에 나열 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="021e8-139">Recommended connections are listed below:</span></span>

        If using Adafruit's serial cable:
            [RPi2 or RPi3] Pin #6  (GND) <-> [Adafruti] Black (GND)
            [RPi2 or RPi3] Pin #8  (TX)  <-> [Adafruit] White (RX) 
            [RPi2 or RPi3] Pin #10 (RX)  <-> [Adafruit] Green (TX)
        
        If using FTDI's serial cable:
            [RPi2 or RPi3] Pin #6  (GND) <-> [FTDI] Black  (GND)
            [RPi2 or RPi3] Pin #8  (TX)  <-> [FTDI] Yellow (RX) 
            [RPi2 or RPi3] Pin #10 (RX)  <-> [FTDI] ORange (TX)

> [!NOTE] 
> <span data-ttu-id="021e8-140">EFIESP 연결을 더 이상 만들지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="021e8-140">The EFIESP junction is no longer created.</span></span> <span data-ttu-id="021e8-141">직접 탑재 해야 합니다. 그러면 mountvol 명령을 사용 하 여 GUID를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="021e8-141">You'll have to mount it yourself,you can use mountvol command to get the GUID.</span></span>
`mkdir C:\EFIESP` 
`mountvol C:\EFIESP \?\Volume{ae420040-0000-0000-0000-200000000000}` 

<span data-ttu-id="021e8-142">활성 PowerShell 연결을 사용 하 여 Raspberry Pi 2 또는 3 장치에서 다음 명령을 실행 하 여 직렬 연결을 통해 디버깅을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="021e8-142">Using the active PowerShell connection, execute the following commands on the Raspberry Pi 2 or 3 device to enable debugging over the serial connection.</span></span>

* `bcdedit /store c:\EFIESP\EFI\Microsoft\Boot\BCD -dbgsettings serial` 

    * <span data-ttu-id="021e8-143">위의 명령은 디버깅을 위해 직렬 연결을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="021e8-143">The above command enables the serial connection for debugging</span></span>
    * <span data-ttu-id="021e8-144">Raspberry Pi 2 또는 3의 전송 속도는 921600으로 하드 코딩 되므로 지정할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="021e8-144">The baud-rate for the Raspberry Pi 2 or 3 is hard-coded to 921600, so you don't have to specify it</span></span>

* `bcdedit /store c:\EFIESP\EFI\Microsoft\Boot\BCD -debug on`

    * <span data-ttu-id="021e8-145">이 명령은 장치에서 디버깅을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="021e8-145">This command turns on debugging on the device</span></span> 

<span data-ttu-id="021e8-146">개발자 PC에서 USB-TTL 케이블로 시스템에 할당 된 COM 포트 번호 포트를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="021e8-146">On the developer PC, get the COM port number PORT assigned in the system for the USB-to-TTL cable.</span></span> <span data-ttu-id="021e8-147">이는 "포트 (COM & LPT)" 아래 Device Manager에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="021e8-147">This will be available in Device Manager under "Ports (COM & LPT)".</span></span>

* `"C:\Program Files (x86)\Debugging Tools for Windows (x86)\windbg.exe" -k com:port=<PORT>,baud=921600` 

    * <span data-ttu-id="021e8-148">포트 번호를 사용 하 여 WinDbg 시작</span><span class="sxs-lookup"><span data-stu-id="021e8-148">Start WinDbg with the PORT number</span></span>
    
> [!NOTE]
> <span data-ttu-id="021e8-149">Windows 키트가 설치 되어 있는 경우 다음 위치에서 WinDbg를 찾을 수 있습니다.`C:\Program Files (x86)\Windows Kits\10\Debuggers\x86\WinDbg.exe`</span><span class="sxs-lookup"><span data-stu-id="021e8-149">If you have any of the Windows kits installed, you may find WinDbg under `C:\Program Files (x86)\Windows Kits\10\Debuggers\x86\WinDbg.exe`</span></span>

* <span data-ttu-id="021e8-150">디버거를 다시 연결 하려면 IoTCore 장치를 다시 부팅 합니다.</span><span class="sxs-lookup"><span data-stu-id="021e8-150">Reboot the IoTCore device to reconnect to the debugger</span></span>


## <a name="dragonboard-db"></a><span data-ttu-id="021e8-151">DragonBoard (DB)</span><span class="sxs-lookup"><span data-stu-id="021e8-151">DragonBoard (DB)</span></span> 
___

<span data-ttu-id="021e8-152">직렬 또는 USB 연결을 사용 하 여 WinDbg를 DragonBoard에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="021e8-152">You can connect WinDbg to the DragonBoard using a serial or USB connection.</span></span>

<span data-ttu-id="021e8-153">활성 PowerShell 또는 DragonBoard에 대 한 SSH 연결을 사용 하 여 다음 명령을 실행 하 여 디버깅을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="021e8-153">Using the active PowerShell or SSH connection to your DragonBoard, execute the following commands to enable debugging.</span></span>

* `bcdedit /store c:\EFIESP\EFI\Microsoft\Boot\BCD /debug {default} ON`
    * <span data-ttu-id="021e8-154">디버거를 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="021e8-154">Enables the debugger</span></span>

### <a name="setup-usb-connection"></a><span data-ttu-id="021e8-155">USB 연결 설정</span><span class="sxs-lookup"><span data-stu-id="021e8-155">Setup USB connection</span></span>
<span data-ttu-id="021e8-156">기본적으로 USB 디버거 설정은 테스트 이미지에 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="021e8-156">By default the USB debugger settings are configured in the test images.</span></span> 

> [!NOTE]
> <span data-ttu-id="021e8-157">USB 커널 디버거가 켜져 있으면 DragonBoard 장치의 USB 포트가 작동 하지 않을 수 있습니다 (즉, 키보드, usb 이더넷이 작동 하지 않을 수 있음).</span><span class="sxs-lookup"><span data-stu-id="021e8-157">Once USB kernel debugger is on, USB ports on the DragonBoard device might not work (i.e. keyboard, usb ethernet might not work).</span></span>

### <a name="setup-serial-connection"></a><span data-ttu-id="021e8-158">직렬 연결 설정</span><span class="sxs-lookup"><span data-stu-id="021e8-158">Setup serial connection</span></span>

* `bcdedit /store c:\EFIESP\EFI\Microsoft\Boot\BCD /dbgsettings  Serial debugport:1 baudrate:115200`
    * <span data-ttu-id="021e8-159">직렬 포트를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="021e8-159">Configures the serial port</span></span>

* <span data-ttu-id="021e8-160">디버거를 다시 연결 하려면 IoTCore 장치를 다시 부팅 합니다.</span><span class="sxs-lookup"><span data-stu-id="021e8-160">Reboot the IoTCore device to reconnect to the debugger</span></span>
