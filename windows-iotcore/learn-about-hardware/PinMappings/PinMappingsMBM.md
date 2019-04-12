---
title: Minnowboard 최대 핀 매핑
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Minnowboard 최대 핀 매핑 기능을 알아봅니다.
keywords: windows iot, 핀 매핑, GPIO Minnowboard Max
ms.openlocfilehash: 884d9ee0d93167a13f39a28b28454daccb2eebad
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513382"
---
# <a name="minnowboard-max-pin-mappings"></a>MinnowBoard 최대 핀 매핑

> [!NOTE] 
> 이 pin 매핑에 Minnowboard의 최신 버전을 비교 하려면 설명서를 참조 하세요 [여기](https://minnowboard.org/minnowboard-turbot/documentation)합니다.

## <a name="overview"></a>개요

![MinnowBoard 최대 Pin 헤더](../../media/PinMappingsMBM/MBM_Pinout.png)

26 pin 헤더를 통해 MinnowBoard 최대 하드웨어 인터페이스를 노출 시키는 **JP1** 보드. 기능은 다음과 같습니다.

* **10 배** -GPIO pin
* **2 x** -직렬 UARTs
* **1 x** -SPI 버스
* **1x** - I2C bus
* **1 x** -5V power pin
* **1 x** -3.3V power pin
* **2 x** -pin 방지 매트를

모든 IO 핀에 MinnowBoard 최대 사용 3.3V 논리 수준입니다. 모든 핀으로 버퍼링 됩니다는 또한 [TXS0104E](http://www.ti.com/product/txs0104e) 전원 및 그라운드 핀을 제외 하 고 변환기 수준입니다.
이러한 수준 변환기 열기 수집기의 출력으로 표시를 **10k&#x2126; 저항 식 풀업은 풀업 이며 IO 입력 또는 출력으로 설정 되어 있는지 여부에 관계 없이 표시 합니다.**
 
오픈 수집기 수준 변환기 의미 하는 ' 0 ', 강력 하 게 하지만 약한만 출력 ' 1' 핀을 출력할 수 있습니다. 이 장치 (예: LED) 핀에서 현재 그리기를 연결 하는 경우에 유의 해야 합니다. 참조 된 [쳐다 샘플](https://developer.microsoft.com/en-us/windows/iot/samples/helloblinky) MinnowBoard max LED를 인터페이스에 대 한 올바른 방법에 대 한 합니다.

## <a name="gpio-pins"></a>GPIO Pin

다음 GPIO 핀은 Api를 통해 액세스할 수 있습니다.

> | GPIO# | 헤더 Pin         |
> |-------|--------------------|
> | 0     | 21                 |
> | 1     | 23                 |
> | 2     | 25                 |
> | 3     | 14                 |
> | 4     | 16                 |
> | 5     | 18                 |
> | 6     | 20                 |
> | 7     | 22                 |
> | 8     | 24                 |
> | 9     | 26                 |

**참고:** **GPIO 4** 하 고 **GPIO 5** MinnowBoard 최대에서 BIOS 부트스트랩 구성 핀으로 사용 됩니다.
MBM 부팅 되지 않을 수 있습니다이 연결 된 장치를 유도 하지 않습니다 이러한 GPIO 낮은 부팅 하는 동안 입력 되어 있는지 확인 합니다.
BIOS 과거의 MBM가 부팅 되 면 이러한 GPIO 일반적으로 사용할 수 있습니다.
     
## <a name="gpio-sample"></a>GPIO 샘플

예를 들어 다음 코드 열립니다 **GPIO 5** 출력으로 디지털 쓰고 '**1**' 핀 아웃 합니다.
         
```C#
using Windows.Devices.Gpio;
         
public void GPIO()
{
    GpioController Controller = GpioController.GetDefault(); /* Get the default GPIO controller on the system */

    GpioPin Pin = Controller.OpenPin(5);        /* Open GPIO 5                      */
    Pin.SetDriveMode(GpioPinDriveMode.Output);  /* Set the IO direction as output   */
    Pin.Write(GpioPinValue.High);               /* Output a digital '1'             */
}
```

## <a name="serial-uart"></a>직렬 UART

MBM에 사용할 직렬 UARTS 두 가지. **UART1** 고 **UART2**

**UART1** 에 표준 **UART1 TX** 하 고 **UART1 RX** flow와 함께 줄 제어 신호 **UART1 CTS** 및 **UART1 RTS**.

* 6-고정 **UART1 TX**
* 8-고정 **UART1 RX**
* 고정 10- **UART1 CTS**
* 12-고정 **UART1 RTS**

UART1 빌드 10240 기준으로 작동 하지 않습니다. UART2 또는 USB-직렬 변환기를 사용 하세요.

**UART2** 포함 요소만 **UART2 TX** 하 고 **UART2 RX** 줄.

* 17-고정 **UART2 TX**
* 19-고정 **UART2 RX**

예외가 발생 하면 직렬의 다음 속성에 액세스 하므로 UART2 흐름 제어를 지원 하지 않습니다.

 * BreakSignalState
 * IsDataTerminalReadyEnabled
 * IsRequestToSendEnabled
 * 핸드셰이크-SerialHandshake.None만 지원 됩니다.

초기화 아래 예에서 **UART2** 읽기 뒤 쓰기를 수행 합니다.

```C#
using Windows.Storage.Streams;
using Windows.Devices.Enumeration;
using Windows.Devices.SerialCommunication;

public async void Serial()
{
    string aqs = SerialDevice.GetDeviceSelector("UART2");                   /* Find the selector string for the serial device   */
    var dis = await DeviceInformation.FindAllAsync(aqs);                    /* Find the serial device with our selector string  */
    SerialDevice SerialPort = await SerialDevice.FromIdAsync(dis[0].Id);    /* Create an serial device with our selected device */

    /* Configure serial settings */
    SerialPort.WriteTimeout = TimeSpan.FromMilliseconds(1000);
    SerialPort.ReadTimeout = TimeSpan.FromMilliseconds(1000);
    SerialPort.BaudRate = 9600;
    SerialPort.Parity = SerialParity.None;         
    SerialPort.StopBits = SerialStopBitCount.One;
    SerialPort.DataBits = 8;

    /* Write a string out over serial */
    string txBuffer = "Hello Serial";
    DataWriter dataWriter = new DataWriter();
    dataWriter.WriteString(txBuffer);
    uint bytesWritten = await SerialPort.OutputStream.WriteAsync(dataWriter.DetachBuffer());

    /* Read data in from the serial port */
    const uint maxReadLength = 1024;
    DataReader dataReader = new DataReader(SerialPort.InputStream);
    uint bytesToRead = await dataReader.LoadAsync(maxReadLength);
    string rxBuffer = dataReader.ReadString(bytesToRead);
}
```

다음 기능을 추가 해야 합니다 **Package.appxmanifest** 직렬 UART 코드를 실행 하기 위해 UWP 프로젝트에서 파일:

Visual Studio 2017에 매니페스트 디자이너에서 (appxmanifest 파일에 대 한 시각적 편집기) serialcommunication 기능에 영향을 주는 알려진된 버그가 있습니다.  프로그램 appxmanifest serialcommunication 기능에 추가 하는 경우 디자이너를 사용 하 여 프로그램 appxmanifest 수정 프로그램 appxmanifest (장치 xml 자식 없어집니다.) 손상 됩니다.  수 해결 방법이이 문제 appxmanifest 직접 편집 하 여 프로그램 appxmanifest를 마우스 오른쪽 단추로 클릭 하 고 상황에 맞는 메뉴에서 코드 보기를 선택 하 여.

```
  <Capabilities>
    <DeviceCapability Name="serialcommunication">
      <Device Id="any">
        <Function Type="name:serialPort" />
      </Device>
    </DeviceCapability>
  </Capabilities>
```

## <a name="i2c-bus"></a>I2C 버스

이 장치에서 사용할 수 있는 I2C 버스를 살펴보겠습니다.

### <a name="i2c-overview"></a>I2C 개요

하나의 I2C 컨트롤러가 **I2C5** 두 줄을 사용 하 여 pin 헤더에 노출 **SDA** 하 고 **SCL**합니다. 10k&#x2126; 다음이 줄에서 내부 풀업 반대자 이미 있습니다.

* Pin 15 - **I2C5 SDA**
* 13-고정 **I2C5 SCL**

### <a name="i2c-sample"></a>I2C 샘플

초기화 아래 예에서 **I2C5** I2C 장치 주소를 사용 하 여 데이터를 쓰고 **0x40**:

```C#
using Windows.Devices.Enumeration;
using Windows.Devices.I2c;

public async void I2C()
{
    // 0x40 is the I2C device address
    var settings = new I2cConnectionSettings(0x40);

    // FastMode = 400KHz
    settings.BusSpeed = I2cBusSpeed.FastMode;

    // Create an I2cDevice with the specified I2C settings
    var controller = await I2cController.GetDefaultAsync();

    using (I2cDevice device = controller.GetDevice(settings))
    {
        byte[] writeBuf = { 0x01, 0x02, 0x03, 0x04 };
        device.Write(writeBuf);
    }

}
```

### <a name="i2c-issues"></a>I2C 문제

MinnowBoard 최대에 특정 I2C 장치와 통신 문제를 일으키는 I2C 버스를 사용 하 여 알려진된 문제가 있는 경우 일반적으로 I2C 장치를 버스 요청 하는 동안 해당 주소를 승인 됩니다.
그러나 특정 조건에서이 승인은 MBM 수준 변환기를 통해 다시 전파할 수 실패 하 고 장치가 응답 하지 않았습니다 고 bus 트랜잭션을 취소 CPU가 생각 하는 결과적으로 합니다.
문제에 관련 된 것으로 보입니다 합니다 [TXS0104E](http://www.ti.com/product/txs0104e) 줄에서 전압 급증으로 인해 중간을 트리거할 수 있는 IO 핀에 변환기 수준입니다.
현재 해결 방법은 급증을 표시 하지 않을 수 있는 I2C SCK 줄을 사용 하 여 계열의 100 옴 저항기를 삽입 하는 것입니다. 모든 장치에는 영향을이 해결 방법은 이므로 필요한 경우 문제가 버스 응답 합니다. 이 해결 방법은 필요으로 알려진 하나의 장치는 HTU21D는입니다.

## <a name="spi-bus"></a>SPI 버스

이 장치에서 사용할 수 있는 SPI 버스를 살펴보겠습니다.

### <a name="spi-overview"></a>SPI 개요

하나의 SPI 컨트롤러가 **SPI0** 는 MBM에서 사용할 수 있습니다.

* 9-고정 **SPI0 MOSI**
* 7-고정 **SPI0 MISO**
* 11-고정 **SPI0 SCLK**
* 5-고정 **SPI0 CS0**


### <a name="spi-sample"></a>SPI 샘플

SPI를 수행 하는 방법을 예로 버스에 작성할 **SPI0** 아래에 표시 됩니다.

```C#
using Windows.Devices.Enumeration;
using Windows.Devices.Spi;

public async void SPI()
{
    // Use chip select line CS0
    var settings = new SpiConnectionSettings(0);
    // Set clock to 10MHz
    settings.ClockFrequency = 10000000;

    // Create an SpiDevice with the specified Spi settings
    var controller = await SpiController.GetDefaultAsync();

    using (SpiDevice device = controller.GetDevice(settings))
    {
        byte[] writeBuf = { 0x01, 0x02, 0x03, 0x04 };
        device.Write(writeBuf);
    }
}
```

