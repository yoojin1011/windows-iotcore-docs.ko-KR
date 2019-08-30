---
title: Raspberry Pi 2 & 3 Pin 매핑
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Raspberry Pi 2 및 3에 대 한 pin 매핑 기능에 대해 알아봅니다.
keywords: windows iot, Rasperry Pi 2, Raspberry Pi 3, pin 매핑, GPIO
ms.openlocfilehash: 86e641bdcc6b4895161c6509ca7529b0dd55fad9
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "60167523"
---
# <a name="raspberry-pi-2--3-pin-mappings"></a>Raspberry Pi 2 & 3 Pin 매핑

![Raspberry Pi 2 & 3 핀 헤더](../../media/PinMappingsRPI/RP2_Pinout.png)

Raspberry Pi 2 및 Raspberry Pi 3의 하드웨어 인터페이스는 보드의 40 핀 헤더 **J8** 를 통해 노출 됩니다. 기능은 다음과 같습니다.

* **24x** -GPIO 핀
* **1x** -직렬 uarts (RPi3에만 미니 UART 포함)
* **2x** -SPI 버스
* **1x** -I2C 버스
* **2** -5v 전원 핀
* **2x** -3.3 v 전원 핀
* **8x** -접지 핀

## <a name="gpio-pins"></a>GPIO 핀

이 장치에서 사용 가능한 GPIO를 살펴보겠습니다.

### <a name="gpio-pin-overview"></a>GPIO 고정 개요

다음 GPIO pin은 Api를 통해 액세스할 수 있습니다.

> | GPIO # | 전원 켜기 풀 | 대체 함수 | 헤더 Pin         |
> |-------|---------------|---------------------|--------------------|
> | 2     | PullUp        | I2C1 SDA            | 3                  |
> | 3     | PullUp        | I2C1 SCL            | 5                  |
> | 4     | PullUp        |                     | 7                  |
> | 5     | PullUp        |                     | 29                 |
> | 6     | PullUp        |                     | 31                 |
> | 7     | PullUp        | SPI0 CS1            | 26                 |
> | 8     | PullUp        | SPI0 CS0            | 24                 |
> | 9     | 3:2      | SPI0 MISO           | 21                 |
> | 10    | 3:2      | SPI0 MOSI           | 19                 |
> | 11    | 3:2      | SPI0 SCLK           | 23                 |
> | 12    | 3:2      |                     | 32                 |
> | 13    | 3:2      |                     | 33                 |
> | 16    | 3:2      | SPI1 CS0            | 36                 |
> | 17    | 3:2      |                     | 11                 |
> | 18    | 3:2      |                     | 12                 |
> | 19    | 3:2      | SPI1 MISO           | 35                 |
> | 20    | 3:2      | SPI1 MOSI           | 38                 |
> | 21    | 3:2      | SPI1 SCLK           | 40                 |
> | 22    | 3:2      |                     | 15                 |
> | 23    | 3:2      |                     | 16                 |
> | 24    | 3:2      |                     | 18                 |
> | 25    | 3:2      |                     | 22                 |
> | 26    | 3:2      |                     | 37                 |
> | 27    | 3:2      |                     | 13                 |
> | 35 *   | PullUp        |                     | 빨간색 전원 LED      |
> | 47 *   | PullUp        |                     | 녹색 작업 LED |

\*= Raspberry Pi 2에만 해당 합니다. GPIO 35 & 47은 Raspberry Pi 3에서 사용할 수 없습니다.

### <a name="gpio-sample"></a>GPIO 샘플

예를 들어 다음 코드는 **GPIO 5** 를 출력으로 열고 pin에 디지털 '**1**'을 기록 합니다.

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

Pin을 열면 전원 켜기 상태가 되며,이는 풀 저항기를 포함할 수 있습니다. 풀 저항기의 연결을 끊고 높은 임피던스 입력을 얻으려면 드라이브 모드를 GpioPinDriveMode로 설정 합니다.

    pin.SetDriveMode(GpioPinDriveMode.Input);

Pin이 닫히면 전원 켜기 상태로 돌아갑니다.

### <a name="pin-muxing"></a>Muxing 고정

일부 GPIO pin은 여러 기능을 수행할 수 있습니다. 기본적으로 pin은 GPIO 입력으로 구성 됩니다. `I2cDevice.FromIdAsync()` 또는`SpiDevice.FromIdAsync()` 를 호출 하 여 대체 함수를 열면 함수에 필요한 pin이 자동으로 올바른 함수로 전환 됩니다 ("muxed"). `I2cDevice.Dispose()` 또는`SpiDevice.Dispose()`를 호출 하 여 장치를 닫으면 pin은 해당 기본 함수로 다시 돌아갑니다. 두 개의 다른 함수에 대해 한 번에 pin을 사용 하려고 하면 충돌 하는 함수를 열려고 할 때 예외가 throw 됩니다. 예:

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

RPi2/3에는 하나의 직렬 UART를 사용할 수 있습니다. **UART0**

* Pin 8- **UART0 TX**
* Pin 10- **UART0 RX**

아래 예제에서는 **UART0** 를 초기화 하 고 쓰기 후에 읽기를 수행 합니다.


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

직렬 UART 코드를 실행 하려면 UWP 프로젝트의 **appxmanifest.xml** 파일에 다음 기능을 추가 해야 합니다.

Visual Studio 2017에는 매니페스트 디자이너 (appxmanifest.xml 파일용 시각적 편집기)에서 serialcommunication 기능에 영향을 주는 알려진 버그가 있습니다.  Appxmanifest.xml가 serialcommunication 기능을 추가 하는 경우 디자이너를 사용 하 여 appxmanifest.xml를 수정 하면 appxmanifest.xml가 손상 됩니다 (장치 xml 자식은 손실 됨).  Appxmanifest.xml를 마우스 오른쪽 단추로 클릭 하 고 상황에 맞는 메뉴에서 코드 보기를 선택 하 여 appxmanifest.xml를 직접 편집이 문제를 해결할 수 있습니다.

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

이 장치에서 사용할 수 있는 I2C bus를 살펴보겠습니다.

### <a name="i2c-overview"></a>I2C 개요

**Sda** 와 **SCL**이라는 두 줄로 된 핀 헤더에는 하나의 I2C 컨트롤러 **I2C1** 노출 됩니다. 1.8 k&#x2126; 내부 풀 (pull) 저항기는이 버스에 대해 보드에 이미 설치 되어 있습니다.

> | 신호 이름 | 헤더 Pin 번호 | Gpio 번호 |
> |-------------|-------------------|-------------|
> | SDA         | 3                 | 2           |
> | SCL         | 5                 | 3           |

아래 예제에서는 **I2C1** 를 초기화 하 고 주소가 **0x40**인 I2C 장치에 데이터를 씁니다.

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

RPi2/3에서 사용 가능한 두 개의 SPI bus 컨트롤러가 있습니다.

### <a name="spi0"></a>SPI0

> | 신호 이름 | 헤더 Pin 번호 | Gpio 번호 |
> |-------------|-------------------|-------------|
> | MOSI        | 19                | 10          |
> | MISO        | 21                | 9           |
> | SCLK        | 23                | 11          |
> | CS0         | 24                | 8           |
> | CS1         | 26                | 7           |

### <a name="spi1"></a>SPI1

> | 신호 이름 | 헤더 Pin 번호 | Gpio 번호 |
> |-------------|-------------------|-------------|
> | MOSI        | 38                | 20          |
> | MISO        | 35                | 19          |
> | SCLK        | 40                | 21          |
> | CS0         | 36                | 16          |


### <a name="spi-sample"></a>SPI 샘플

칩 select 0을 사용 하 여 bus **SPI0** 에서 SPI 쓰기를 수행 하는 방법의 예는 다음과 같습니다.

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

