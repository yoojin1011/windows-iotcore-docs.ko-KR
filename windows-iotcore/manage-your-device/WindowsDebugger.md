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
# <a name="windows-debugger-windbg"></a>Windows 디버거 (WinDbg)
강력한 Windows 디버거 인 WinDbg를 사용 하 여 Windows 10 IoT Core 장치를 디버깅 합니다.

다음 섹션에서는 디버깅을 위해 WinDbg를 Windows 10 IoT Core 장치에 성공적으로 연결 하는 방법을 설명 합니다.  여기에는 장치에 대 한 필수 소프트웨어 설정 및 실제 하드웨어 연결에 대 한 설명이 포함 됩니다.  

WinDbg는 대부분의 Windows 개발자가 친숙 한 매우 강력한 디버거입니다.  그러나 처음 시작 하 고 WinDbg에 대해 자세히 알아보려면 다음 링크를 방문 하세요.

* [Windows 용 디버깅 도구](https://msdn.microsoft.com/library/windows/hardware/ff551063(v=vs.85).aspx) 

* [Windows 디버깅 시작](https://msdn.microsoft.com/library/windows/hardware/mt219729(v=vs.85).aspx) 

* [WinDbg를 사용 하 여 크래시 덤프 분석](https://msdn.microsoft.com/library/windows/hardware/ff539316(v=vs.85).aspx) 


## <a name="minnowboard-max-mbm"></a>MinnowBoard Max (MBM) 

네트워크 연결을 사용 하 여 WinDbg를 MinnowBoard Max 장치에 연결할 수 있습니다.

### <a name="setup-network-connection"></a>네트워크 연결 설정

네트워크를 통해 WinDbg에서 커널 디버깅을 사용 하도록 설정 하려면 다음을 확인 합니다.

* 이더넷 케이블은 MinnowBoard Max 장치에 네트워크에 연결 됩니다. 

* MinnowBoard Max 장치는 네트워크에 유효한 IP 주소를 포함 합니다.

* [PowerShell](../connect-your-device/PowerShell.md) 을 통해 MinnowBoard Max 장치에 대 한 활성 연결 

활성 PowerShell 연결을 사용 하 여 MinnowBoard Max에서 다음 명령을 실행 하 여 네트워크를 통해 디버깅을 사용 하도록 설정 합니다.

* `bcdedit -dbgsettings net hostip:<DEV_PC_IP_ADDRESS> port:<PORT_NUM> key:<KEY>` 

    * 이 명령은 네트워크를 통해 디버깅을 사용 하도록 설정 합니다.  또한 WinDbg를 실행 하는 PC의 IP 주소 (DEV_PC_IP_ADDRESS), 연결에 사용할 네트워크 포트 번호 (PORT_NUM) 및 여러 연결을 구분 하는 데 사용할 고유 키 (키)를 지정 합니다. 

    * PORT_NUM 및 키의 경우 다음 값을 예제로 사용할 수 있습니다. 50045 및 1.2.3.4 각각에 맞게 변경할 수 있습니다.
    
* `bcdedit -debug on`

    * 이 명령은 장치에서 디버깅을 설정 합니다. 

* 개발자 PC에서 다음과 같이 이전 단계에서 제공 된 PORT_NUM 및 키 값을 사용 하 여 WinDbg를 시작 합니다.`"c:\Program Files (x86)\Debugging Tools for Windows (x86)\windbg.exe" -k net:port=<PORT_NUM>,key=<KEY>`

> [!NOTE]
> Windows 키트가 설치 되어 있는 경우 다음 위치에서 WinDbg를 찾을 수 있습니다.`C:\Program Files (x86)\Windows Kits\10\Debuggers\x86\WinDbg.exe</code>`

* 디버거를 다시 연결 하려면 IoTCore 장치를 다시 부팅 합니다.

## <a name="raspberry-pi-2-or-3-rpi2-or-rpi3"></a>Raspberry Pi 2 또는 3 (RPi2 또는 RPi3) 

직렬 연결을 사용 하 여 WinDbg를 Raspberry Pi 2 또는 3에 연결할 수 있습니다.

### <a name="setup-serial-connection"></a>직렬 연결 설정

직렬 연결을 통해 WinDbg에서 커널 디버깅을 사용 하도록 설정 하려면 다음을 확인 합니다.

* [Adafruit](https://www.adafruit.com/product/954) 또는 [FTDI](http://shop.clickandbuild.com/cnb/shop/ftdichip?productID=53&op=catalogue-product_info-null&prodCategoryID=105)의 USB-TTL 직렬 케이블과 같은 디버그 케이블이 있습니다. 

* Raspberry Pi 2 또는 3 장치를 네트워크에 연결 하는 이더넷 케이블 또는 활성 WiFi (SSH 또는 PowerShell과 같은 IP 연결의 경우)

* Raspberry Pi 2 또는 3 장치는 네트워크에 유효한 IP 주소를 포함 합니다.

* [PowerShell](../connect-your-device/PowerShell.md) 또는 [SSH](../connect-your-device/SSH.md) 를 통해 Raspberry Pi 2 또는 3 장치에 대 한 활성 연결

UART0은 커널 디버깅 연결을 위해 Raspberry Pi 2 또는 3 장치에서 사용 됩니다.  다음은 직렬 케이블 뿐만 아니라 Raspberry Pi 2 또는 3에 대 한 pin 매핑을 보여 줍니다. 

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
            
올바른 직렬 연결을 설정 하는 기본적인 이유는 한 장치가 해당 TX를 사용 하 여 데이터를 전송 하는 동안 다른 장치는 해당 RX를 사용 하 여 데이터를 받는 것입니다.  권장 연결은 아래에 나열 되어 있습니다.

        If using Adafruit's serial cable:
            [RPi2 or RPi3] Pin #6  (GND) <-> [Adafruti] Black (GND)
            [RPi2 or RPi3] Pin #8  (TX)  <-> [Adafruit] White (RX) 
            [RPi2 or RPi3] Pin #10 (RX)  <-> [Adafruit] Green (TX)
        
        If using FTDI's serial cable:
            [RPi2 or RPi3] Pin #6  (GND) <-> [FTDI] Black  (GND)
            [RPi2 or RPi3] Pin #8  (TX)  <-> [FTDI] Yellow (RX) 
            [RPi2 or RPi3] Pin #10 (RX)  <-> [FTDI] ORange (TX)

> [!NOTE] 
> EFIESP 연결을 더 이상 만들지 않습니다. 직접 탑재 해야 합니다. 그러면 mountvol 명령을 사용 하 여 GUID를 가져올 수 있습니다.
`mkdir C:\EFIESP` 
`mountvol C:\EFIESP \?\Volume{ae420040-0000-0000-0000-200000000000}` 

활성 PowerShell 연결을 사용 하 여 Raspberry Pi 2 또는 3 장치에서 다음 명령을 실행 하 여 직렬 연결을 통해 디버깅을 사용 하도록 설정 합니다.

* `bcdedit /store c:\EFIESP\EFI\Microsoft\Boot\BCD -dbgsettings serial` 

    * 위의 명령은 디버깅을 위해 직렬 연결을 사용 하도록 설정 합니다.
    * Raspberry Pi 2 또는 3의 전송 속도는 921600으로 하드 코딩 되므로 지정할 필요가 없습니다.

* `bcdedit /store c:\EFIESP\EFI\Microsoft\Boot\BCD -debug on`

    * 이 명령은 장치에서 디버깅을 설정 합니다. 

개발자 PC에서 USB-TTL 케이블로 시스템에 할당 된 COM 포트 번호 포트를 가져옵니다. 이는 "포트 (COM & LPT)" 아래 Device Manager에서 사용할 수 있습니다.

* `"C:\Program Files (x86)\Debugging Tools for Windows (x86)\windbg.exe" -k com:port=<PORT>,baud=921600` 

    * 포트 번호를 사용 하 여 WinDbg 시작
    
> [!NOTE]
> Windows 키트가 설치 되어 있는 경우 다음 위치에서 WinDbg를 찾을 수 있습니다.`C:\Program Files (x86)\Windows Kits\10\Debuggers\x86\WinDbg.exe`

* 디버거를 다시 연결 하려면 IoTCore 장치를 다시 부팅 합니다.


## <a name="dragonboard-db"></a>DragonBoard (DB) 
___

직렬 또는 USB 연결을 사용 하 여 WinDbg를 DragonBoard에 연결할 수 있습니다.

활성 PowerShell 또는 DragonBoard에 대 한 SSH 연결을 사용 하 여 다음 명령을 실행 하 여 디버깅을 사용 하도록 설정 합니다.

* `bcdedit /store c:\EFIESP\EFI\Microsoft\Boot\BCD /debug {default} ON`
    * 디버거를 사용 하도록 설정 합니다.

### <a name="setup-usb-connection"></a>USB 연결 설정
기본적으로 USB 디버거 설정은 테스트 이미지에 구성 됩니다. 

> [!NOTE]
> USB 커널 디버거가 켜져 있으면 DragonBoard 장치의 USB 포트가 작동 하지 않을 수 있습니다 (즉, 키보드, usb 이더넷이 작동 하지 않을 수 있음).

### <a name="setup-serial-connection"></a>직렬 연결 설정

* `bcdedit /store c:\EFIESP\EFI\Microsoft\Boot\BCD /dbgsettings  Serial debugport:1 baudrate:115200`
    * 직렬 포트를 구성 합니다.

* 디버거를 다시 연결 하려면 IoTCore 장치를 다시 부팅 합니다.
