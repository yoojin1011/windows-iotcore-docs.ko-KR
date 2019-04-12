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
# <a name="windows-debugger-windbg"></a>Windows 디버거 (WinDbg)
강력한 Windows 디버거, WinDbg를 사용 하 여 Windows 10 IoT Core 장치를 디버그 합니다.

다음 섹션에서는 WinDbg를 사용 하 여 디버깅을 위해 Windows 10 IoT Core 장치에 성공적으로 연결 하는 방법에 설명 합니다.  물리적 하드웨어 연결 뿐만 아니라 장치에 필요한 소프트웨어 설정에 대 한 설명을 포함 됩니다.  

WinDbg는 대부분의 Windows 개발자는 잘 알고 있는 강력한 디버거를 합니다.  그러나 바로 시작 하 고 WinDbg에 대 한 자세한 정보를 알아보려면 다음 링크를

* [Windows용 디버깅 도구](https://msdn.microsoft.com/library/windows/hardware/ff551063(v=vs.85).aspx) 

* [Windows 디버깅을 시작 하기](https://msdn.microsoft.com/library/windows/hardware/mt219729(v=vs.85).aspx) 

* [Crash Dump Analysis WinDbg를 사용 하 여](https://msdn.microsoft.com/library/windows/hardware/ff539316(v=vs.85).aspx) 


## <a name="minnowboard-max-mbm"></a>MinnowBoard 최대 MBM) 

네트워크 연결을 사용 하 여 MinnowBoard 최대 장치로 WinDbg를 연결할 수 있습니다.

### <a name="setup-network-connection"></a>네트워크 연결 설정

네트워크를 통해 WinDbg를 사용 하 여 커널 디버깅을 사용 하기 위해을 확인 합니다.

* 이더넷 케이블 MinnowBoard 최대 장치를 네트워크에 연결 되어 

* MinnowBoard 최대 장치가 네트워크에 대 한 유효한 IP 주소

* 활성 연결을 통해 MinnowBoard 최대 장치로 [PowerShell](../connect-your-device/PowerShell.md) 

현재 PowerShell 연결을 사용 하 MinnowBoard 최대 네트워크를 통해 디버깅을 사용 하려면에서 다음 명령을 실행 합니다.

* `bcdedit -dbgsettings net hostip:<DEV_PC_IP_ADDRESS> port:<PORT_NUM> key:<KEY>` 

    * 이 명령은 네트워크를 통해 디버깅할 수 있습니다.  또한 여기서 WinDbg 실행 됩니다 (DEV_PC_IP_ADDRESS) PC의 IP 주소를 지정 (PORT_NUM) 연결과 고유 키에 대 한 여러 연결 (키)를 구분 하는 데 사용 하는 네트워크 포트 번호 

    * PORT_NUM와 키에 대 한 예제로 다음 값을 사용할 수 있습니다. 50045 및 1.2.3.4 각각 수는 있지만 가능 하다 면 이러한 변경
    
* `bcdedit -debug on`

    * 이 명령은 장치에서 디버깅 설정 

* 개발자 PC에서 WinDbg를 PORT_NUM와 같이 이전 단계에서 제공 되는 키 값 시작: `"c:\Program Files (x86)\Debugging Tools for Windows (x86)\windbg.exe" -k net:port=<PORT_NUM>,key=<KEY>`

> [!NOTE]
> 설치 된 Windows 키트에 있는 경우에 WinDbg 아래을 알 수 있습니다.
`C:\Program Files (x86)\Windows Kits\10\Debuggers\x86\WinDbg.exe</code>`

* 디버거를 연결할 IoTCore 장치를 다시 부팅

## <a name="raspberry-pi-2-or-3-rpi2-or-rpi3"></a>Raspberry Pi 2 또는 3 (RPi2 또는 RPi3) 

WinDbg는 Raspberry Pi 2 또는 3 대 한 직렬 연결을 사용 하 여 연결할 수 있습니다.

### <a name="setup-serial-connection"></a>직렬 연결 설정

직렬 연결을 통해 WinDbg를 사용 하 여 커널 디버깅을 사용 하기 위해을 확인 합니다.

* USB-TTL 직렬 케이블을 같은 디버그 케이블이 [Adafruit](https://www.adafruit.com/product/954) 하거나 [FTDI](http://shop.clickandbuild.com/cnb/shop/ftdichip?productID=53&op=catalogue-product_info-null&prodCategoryID=105)합니다. 

* 이더넷 케이블이 나 (SSH 또는 PowerShell과 같은 IP 연결)에 대 한 네트워크에 Raspberry Pi 2 또는 3 장치를 연결 하는 활성 WiFi를

* Raspberry Pi 2 또는 3 장치에 올바른 IP 주소를 네트워크

* Raspberry Pi 2 또는 3 장치를 통해 활성 연결이 [PowerShell](../connect-your-device/PowerShell.md) 또는 [SSH](../connect-your-device/SSH.md)

UART0은 Raspberry Pi 2 또는 3 장치 커널 디버깅 연결에 사용 됩니다.  다음은 직렬 케이블 뿐만 아니라 Raspberry Pi 2 또는 3 핀 매핑. 

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
            
올바른 직렬 연결에 대 한 기본 개념 하나의 장치에서는 해당 TX 데이터를 전송 하는 동안 다른 장치 데이터를 수신 하는 RX를 사용 해야 하는 것입니다.  연결 권장된 사항은 다음과 같습니다.

        If using Adafruit's serial cable:
            [RPi2 or RPi3] Pin #6  (GND) <-> [Adafruti] Black (GND)
            [RPi2 or RPi3] Pin #8  (TX)  <-> [Adafruit] White (RX) 
            [RPi2 or RPi3] Pin #10 (RX)  <-> [Adafruit] Green (TX)
        
        If using FTDI's serial cable:
            [RPi2 or RPi3] Pin #6  (GND) <-> [FTDI] Black  (GND)
            [RPi2 or RPi3] Pin #8  (TX)  <-> [FTDI] Yellow (RX) 
            [RPi2 or RPi3] Pin #10 (RX)  <-> [FTDI] ORange (TX)

> [!NOTE] 
> 더 이상 EFIESP 접합이 만들어집니다. 직접 탑재 해야, GUID를 가져올 mountvol 명령을 사용할 수 있습니다.
`mkdir C:\EFIESP` 
`mountvol C:\EFIESP \?\Volume{ae420040-0000-0000-0000-200000000000}` 

활성 PowerShell 연결을 사용 하 여, 직렬 연결을 통해 디버깅을 사용 하려면 Raspberry Pi 2 또는 3 장치에서 다음 명령을 실행 합니다.

* `bcdedit /store c:\EFIESP\EFI\Microsoft\Boot\BCD -dbgsettings serial` 

    * 위의 명령은 디버깅에 대 한 직렬 연결을 설정
    * Raspberry Pi 2 또는 3에 대 한 전송 속도 이므로 921600,으로 하드 코딩 지정할 필요가 없습니다.

* `bcdedit /store c:\EFIESP\EFI\Microsoft\Boot\BCD -debug on`

    * 이 명령은 장치에서 디버깅 설정 

개발자 PC에 USB-TTL 케이블 시스템의 할당 된 포트 번호 포트를 COM 가져옵니다. 이 장치 관리자에서 "포트 (COM 및 LPT)" 아래에서 사용할 수 있습니다.

* `"C:\Program Files (x86)\Debugging Tools for Windows (x86)\windbg.exe" -k com:port=<PORT>,baud=921600` 

    * 포트 번호를 사용 하 여 WinDbg 시작
    
> [!NOTE]
> 설치 된 Windows 키트에 있는 경우에 WinDbg 아래을 알 수 있습니다.
`C:\Program Files (x86)\Windows Kits\10\Debuggers\x86\WinDbg.exe`

* 디버거를 연결할 IoTCore 장치를 다시 부팅


## <a name="dragonboard-db"></a>DragonBoard (DB) 
___

WinDbg는 직렬 또는 USB 연결을 사용 하 여 DragonBoard 연결할 수 있습니다.

디버깅을 사용 하려면 다음 명령을 실행 하 여 DragonBoard 현재 PowerShell 또는 SSH 연결을 사용 하 합니다.

* `bcdedit /store c:\EFIESP\EFI\Microsoft\Boot\BCD /debug {default} ON`
    * 디버거를 사용 하도록 설정

### <a name="setup-usb-connection"></a>USB 연결 설정
기본적으로 USB 디버거 설정 테스트 이미지에서 구성 됩니다. 

> [!NOTE]
> USB 커널 디버거를 DragonBoard 장치에서 USB 포트 (예:: 키보드, usb 이더넷 작동 하지 않을 수 있습니다) 작동 하지 않을 수 있습니다.

### <a name="setup-serial-connection"></a>직렬 연결 설정

* `bcdedit /store c:\EFIESP\EFI\Microsoft\Boot\BCD /dbgsettings  Serial debugport:1 baudrate:115200`
    * 직렬 포트를 구성합니다.

* 디버거를 연결할 IoTCore 장치를 다시 부팅
