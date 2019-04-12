---
title: Raspberry Pi 2 및 3 핀 매핑
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Raspberry Pi 2 및 3 핀 매핑 기능에 알아봅니다.
keywords: windows iot, Rasperry Pi 2, Raspberry Pi 3에 고정 매핑을 GPIO
ms.openlocfilehash: 86e641bdcc6b4895161c6509ca7529b0dd55fad9
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512877"
---
# <a name="raspberry-pi-2--3-pin-mappings"></a>Raspberry Pi 2 및 3 핀 매핑

![Raspberry Pi 2 및 3 핀 헤더](../../media/PinMappingsRPI/RP2_Pinout.png)

40 핀 헤더를 통해 Raspberry Pi 2 및 Raspberry Pi 3에 대 한 하드웨어 인터페이스를 노출 시키는 **J8** 보드입니다. 기능은 다음과 같습니다.

* **24 x** -GPIO pin
* **1 x** -직렬 UARTs (포함 미니 UART RPi3)
* **2 x** -SPI 버스
* **1x** - I2C bus
* **2 x** -5V power pin
* **2 x** -3.3V 핀 power
* **8 x** -pin 방지 매트를

## <a name="gpio-pins"></a>GPIO Pin

이 장치에서 사용 가능한 GPIO를 살펴보겠습니다.

### <a name="gpio-pin-overview"></a>GPIO Pin 개요

다음 GPIO 핀은 Api를 통해 액세스할 수 있습니다.

> | GPIO# | 전원 켜기 끌어오기 | 대체 함수 | 헤더 Pin         |
> |-------|---------------|---------------------|--------------------|
> | 2     | PullUp        | I2C1 SDA            | 3                  |
> | 3     | PullUp        | I2C1 SCL            | 5                  |
> | 4     | PullUp        |                     | 7                  |
> | 5     | PullUp        |                     | 29                 |
> | 6     | PullUp        |                     | 31                 |
> | 7     | PullUp        | SPI0 CS1            | 26                 |
> | 8     | PullUp        | SPI0 CS0            | 24                 |
> | 9     | PullDown      | SPI0 MISO           | 21                 |
> | 10    | PullDown      | SPI0 MOSI           | 19                 |
> | 11    | PullDown      | SPI0 SCLK           | 23                 |
> | 12    | PullDown      |                     | 32                 |
> | 13    | PullDown      |                     | 33                 |
> | 16    | PullDown      | SPI1 CS0            | 36                 |
> | 17    | PullDown      |                     | 11                 |
> | 18    | PullDown      |                     | 12                 |
> | 19    | PullDown      | SPI1 MISO           | 35                 |
> | 20    | PullDown      | SPI1 MOSI           | 38                 |
> | 21    | PullDown      | SPI1 SCLK           | 40                 |
> | 22    | PullDown      |                     | 15                 |
> | 23    | PullDown      |                     | 16                 |
> | 24    | PullDown      |                     | 18                 |
> | 25    | PullDown      |                     | 22                 |
> | 26    | PullDown      |                     | 37                 |
> | 27    | PullDown      |                     | 13                 |
> | 35*   | PullUp        |                     | 빨간색 전원 LED      |
> | 47*   | PullUp        |                     | 녹색 동작 LED |

\* Raspberry Pi 2만 =. GPIO 35 & 47 Raspberry Pi 3에서 제공 되지 않습니다.

### <a name="gpio-sample"></a>GPIO 샘플

예를 들어 다음 코드 열립니다 **GPIO 5** 출력으로 디지털 쓰고 '**1**' 핀 아웃 합니다.

```csharp
using Windows.Devices.Gpio;

public void GPIO()
{
    // Get the default GPIO controller on the system
    GpioController gpio = GpioController.GetDefault();
    if (gpio == null)
        return; // GPIO not available on this system

    // Open GPIO 5
    using (GpioPin pin = gpio.OpenPin(5))
    {
        // Latch HIGH value first. This ensures a default value when the pin is set as output
        pin.Write(GpioPinValue.High);

        // Set the IO direction as output
        pin.SetDriveMode(GpioPinDriveMode.Output);

    } // Close pin - will revert to its power-on state
}
```

Pin을 열면 끌어오기 저항기를 포함할 수 있는 해당 전원 켜기 상태가 됩니다. 끌어오기 반대자 분리를 높은 임피던스 입력을 가져오려면 GpioPinDriveMode.Input을 드라이브 모드를 설정 합니다.

    pin.SetDriveMode(GpioPinDriveMode.Input);

Pin 닫힐 때 전원 켜기 상태로 되돌립니다.

### <a name="pin-muxing"></a>Pin Muxing

일부 GPIO pin 여러 함수를 수행할 수 있습니다. 기본적으로 pin GPIO 입력으로 구성 됩니다. 호출 하 여 대체 함수를 열면 `I2cDevice.FromIdAsync()` 또는 `SpiDevice.FromIdAsync()` 를 함수에 필요한 pin은 자동으로 전환된 ("muxed") 올바른 함수입니다. 호출 하 여 장치를 닫을 때 `I2cDevice.Dispose()` 또는 `SpiDevice.Dispose()`, 핀으로 해당 기본 함수 돌아갑니다. 한 번에 두 개의 다른 함수에 대 한 pin을 사용 하려는 경우 충돌 하는 함수를 열 때 예외가 throw 됩니다. 예:

```csharp
var controller = GpioController.GetDefault();
var gpio2 = controller.OpenPin(2);      // open GPIO2, shared with I2C1 SDA

var dis = await DeviceInformation.FindAllAsync(I2cDevice.GetDeviceSelector());
var i2cDevice = await I2cDevice.FromIdAsync(dis[0].Id, new I2cConnectionSettings(0x55)); // exception thrown because GPIO2 is open

gpio2.Dispose(); // close GPIO2
var i2cDevice = await I2cDevice.FromIdAsync(dis[0].Id, new I2cConnectionSettings(0x55)); // succeeds because gpio2 is now available

var gpio2 = controller.OpenPin(2); // throws exception because GPIO2 is in use as SDA1

i2cDevice.Dispose(); // release I2C device
var gpio2 = controller.OpenPin(2); // succeeds now that GPIO2 is available
```

## <a name="serial-uart"></a>직렬 UART

RPi2/3에서 사용 가능한 하나의 직렬 UART 방법이: **UART0**

* 8-고정 **UART0 TX**
* 고정 10- **UART0 RX**

초기화 아래 예에서 **UART0** 읽기 뒤 쓰기를 수행 합니다.


```csharp
using Windows.Storage.Streams;
using Windows.Devices.Enumeration;
using Windows.Devices.SerialCommunication;

public async void Serial()
{
    string aqs = SerialDevice.GetDeviceSelector("UART0");                   /* Find the selector string for the serial device   */
    var dis = await DeviceInformation.FindAllAsync(aqs);                    /* Find the serial device with our selector string  */
    SerialDevice SerialPort = await SerialDevice.FromIdAsync(dis[0].Id);    /* Create an serial device with our selected device */

    /* Configure serial settings */
    SerialPort.WriteTimeout = TimeSpan.FromMilliseconds(1000);
    SerialPort.ReadTimeout = TimeSpan.FromMilliseconds(1000);
    SerialPort.BaudRate = 9600;                                             /* mini UART: only standard baudrates */
    SerialPort.Parity = SerialParity.None;                                  /* mini UART: no parities */  
    SerialPort.StopBits = SerialStopBitCount.One;                           /* mini UART: 1 stop bit */
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

```xml
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

하나의 I2C 컨트롤러가 **I2C1** 두 줄을 사용 하 여 pin 헤더에 노출 **SDA** 하 고 **SCL**합니다. 1.8 K&#x2126; 내부 풀업 레지스터가이 버스 게시판에 이미 설치 되어 있습니다.

> | 신호 이름 | Pin 번호 머리글 | Gpio 수 |
> |-------------|-------------------|-------------|
> | SDA         | 3                 | 2           |
> | SCL         | 5                 | 3           |

초기화 아래 예에서 **I2C1** I2C 장치 주소를 사용 하 여 데이터를 쓰고 **0x40**:

```csharp
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

## <a name="spi-bus"></a>SPI 버스

RPi2/3에 사용할 수 있는 두 명의 SPI 버스 컨트롤러가 있습니다.

### <a name="spi0"></a>SPI0

> | 신호 이름 | Pin 번호 머리글 | Gpio 수 |
> |-------------|-------------------|-------------|
> | MOSI        | 19                | 10          |
> | MISO        | 21                | 9           |
> | SCLK        | 23                | 11          |
> | CS0         | 24                | 8           |
> | CS1         | 26                | 7           |

### <a name="spi1"></a>SPI1

> | 신호 이름 | Pin 번호 머리글 | Gpio 수 |
> |-------------|-------------------|-------------|
> | MOSI        | 38                | 20          |
> | MISO        | 35                | 19          |
> | SCLK        | 40                | 21          |
> | CS0         | 36                | 16          |


### <a name="spi-sample"></a>SPI 샘플

SPI를 수행 하는 방법의 예가 버스에 작성할 **SPI0** 칩 선택 0을 사용 하는 다음과 같습니다.

```csharp
using Windows.Devices.Enumeration;
using Windows.Devices.Spi;

public async void SPI()
{
    // Use chip select line CS0
    var settings = new SpiConnectionSettings(0);
    // Set clock to 10MHz 
    settings.ClockFrequency = 10000000;

    // Get a selector string that will return our wanted SPI controller
    string aqs = SpiDevice.GetDeviceSelector("SPI0");
    
    // Find the SPI bus controller devices with our selector string
    var dis = await DeviceInformation.FindAllAsync(aqs);
    
    // Create an SpiDevice with our selected bus controller and Spi settings
    using (SpiDevice device = await SpiDevice.FromIdAsync(dis[0].Id, settings))
    {
        byte[] writeBuf = { 0x01, 0x02, 0x03, 0x04 };
        device.Write(writeBuf);
    }
}
```

