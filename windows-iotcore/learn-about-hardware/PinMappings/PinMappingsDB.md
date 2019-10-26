---
title: Dragonboard Pin 매핑
ms.date: 08/28/2017
ms.topic: article
description: Dragonboard에 대 한 pin 매핑 기능에 대해 알아봅니다.
keywords: windows iot, Dragonboard, pin 매핑, GPIO
ms.openlocfilehash: 170b14ce640fed33754f90bd4df188f4629f04c2
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72917970"
---
# <a name="dragonboard-pin-mappings"></a>Dragonboard Pin 매핑

![Dragonboard Pin 헤더](../../media/PinMappingsDB/DB_Pinout.png)

Dragonboard에 대 한 하드웨어 인터페이스는 보드의 40 핀 헤더를 통해 노출 됩니다. 기능은 다음과 같습니다.

* **11x** -GPIO 핀
* **2x** -직렬 uarts
* **1x** -SPI 버스
* **2** -I2C 버스
* **1x** -5v 전원 pin
* **1x** -1.8 v 전원 pin
* **4x** -접지 핀

Dragonboard에서는 모든 IO 핀에서 1.8 V 논리 수준을 사용 합니다. 

## <a name="gpio-pins"></a>GPIO 핀

이 장치에서 사용 가능한 GPIO를 살펴보겠습니다.

### <a name="gpio-pin-table"></a>GPIO 고정 테이블

다음 GPIO pin은 Api를 통해 액세스할 수 있습니다.

> | GPIO # | 헤더 Pin         |
> |-------|--------------------|
> | 36    | 23                 |
> | 12    | 24                 |
> | 13    | 25일                 |
> | 69    | 26                 |
> | 115   | 27                 |
> | 24    | 29                 |
> | 25일    | 30                 |
> | 35    | 31                 |
> | 34    | 32                 |
> | 28    | 33                 |
> | 33    | 34                 |
> | RD 세션 호스트 서버 팜의 이름을 지정하는 새 RD RAP 만들기    | 사용자 LED 1         | 
> | 120   | 사용자 LED 2         |         


예를 들어 다음 코드는 **GPIO 35** 을 출력으로 열고 pin에 디지털 '**1**'을 기록 합니다.
         
```C#
using Windows.Devices.Gpio;
         
public void GPIO()
{
    GpioController Controller = GpioController.GetDefault(); /* Get the default GPIO controller on the system */

    GpioPin Pin = Controller.OpenPin(35);       /* Open GPIO 35                      */
    Pin.SetDriveMode(GpioPinDriveMode.Output);  /* Set the IO direction as output   */
    Pin.Write(GpioPinValue.High);               /* Output a digital '1'             */
}
```

### <a name="gpio-issues"></a>GPIO 문제

* GPIO 24에서는 출력이 작동 하지 않습니다. 입력이 제대로 작동 합니다.
* Pin은 부팅 시 InputPullDown로 구성 되지만 처음 열릴 때 입력 (부동)으로 변경 됩니다.
* 닫히면 pin은 기본 상태로 되돌아가지 않습니다.
* 여러 핀에서 인터럽트를 사용 하는 경우 의사 인터럽트가 표시 될 수 있습니다.


## <a name="serial-uart"></a>직렬 UART

Dragonboard **UART0** 및 **UART1** 에는 두 개의 직렬 uarts를 사용할 수 있습니다.

**UART0** 에는 표준 **UART0 TX** 및 **UART0 RX** 회선이 있으며,이는 CTS 및 **UART0 RTS**를 **UART0** 하는 흐름 제어 신호와 함께 있습니다.

* 핀 5- **UART0 TX**
* Pin 7- **UART0 RX**
* Pin 3- **UART0 CTS**
* Pin 9- **UART0 RTS**


**UART1** 에는 **UART1 TX** 및 **UART1 RX** 줄만 포함 됩니다.

* 핀 11- **UART1 TX**
* Pin 13- **UART1 RX**

아래 예제에서는 **UART1** 를 초기화 하 고 쓰기 후에 읽기를 수행 합니다.

```C#
using Windows.Storage.Streams;
using Windows.Devices.Enumeration;
using Windows.Devices.SerialCommunication;

public async void Serial()
{
    string aqs = SerialDevice.GetDeviceSelector("UART1");                   /* Find the selector string for the serial device   */
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
> [!NOTE]
> Visual Studio 2017에는 매니페스트 디자이너 (appxmanifest.xml 파일용 시각적 편집기)에서 serialcommunication 기능에 영향을 주는 알려진 버그가 있습니다.  Appxmanifest.xml가 serialcommunication 기능을 추가 하는 경우 디자이너를 사용 하 여 appxmanifest.xml를 수정 하면 appxmanifest.xml가 손상 됩니다 (장치 xml 자식은 손실 됨).  Appxmanifest.xml를 마우스 오른쪽 단추로 클릭 하 고 상황에 맞는 메뉴에서 코드 보기를 선택 하 여 appxmanifest.xml를 직접 편집이 문제를 해결할 수 있습니다.

다음 기능을 UWP 프로젝트의 **appxmanifest.xml** 파일에 추가 하 여 직렬 UART 코드를 실행 해야 합니다.

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

### <a name="i2c-pins"></a>I2C 핀

**I2C0** 는 두 줄 **Sda** 와 **SCL** 을 사용 하 여 pin 헤더에 노출 됩니다.

* Pin 17- **I2C0 SDA**
* Pin 15- **I2C0 SCL**

**I2C1** 는 두 줄 **Sda** 와 **SCL** 을 사용 하 여 pin 헤더에 노출 됩니다.

* 핀 21- **I2C1 SDA**
* Pin 19- **I2C1 SCL**

### <a name="i2c-sample"></a>I2C 샘플

아래 예제에서는 **I2C0** 를 초기화 하 고 주소가 **0x40**인 I2C 장치에 데이터를 씁니다.

```C#
using Windows.Devices.Enumeration;
using Windows.Devices.I2c;

public async void I2C()
{
    // 0x40 is the I2C device address
    var settings = new I2cConnectionSettings(0x40);
    // FastMode = 400KHz
    settings.BusSpeed = I2cBusSpeed.FastMode;

    // Get a selector string that will return our wanted I2C controller
    string aqs = I2cDevice.GetDeviceSelector("I2C0");
    
    // Find the I2C bus controller devices with our selector string
    var dis = await DeviceInformation.FindAllAsync(aqs);

    // Create an I2cDevice with our selected bus controller and I2C settings 
    using (I2cDevice device = await I2cDevice.FromIdAsync(dis[0].Id, settings))
    {
        byte[] writeBuf = { 0x01, 0x02, 0x03, 0x04 };
        device.Write(writeBuf);
    }
}
```


## <a name="spi-bus"></a>SPI 버스

이 장치에서 사용할 수 있는 SPI bus를 살펴보겠습니다.

### <a name="spi-pins"></a>SPI Pin

DB에서 사용할 수 있는 SPI 컨트롤러 **SPI0** 하나 있습니다.

* Pin 10- **SPI0 miso**
* Pin 14- **SPI0 MOSI**
* Pin 8- **SPI0 SCLK**
* Pin 12- **SPI0 CS0**

### <a name="spi-issues"></a>SPI 문제

SPI clock은 4.8 mhz에서 고정 됩니다. 요청 된 SPI clock은 무시 됩니다. 


### <a name="spi-sample"></a>SPI 샘플

다음은 bus **SPI0** 에서 SPI 쓰기를 수행 하는 방법에 대 한 예제입니다.

```C3
using Windows.Devices.Enumeration;
using Windows.Devices.Spi;

public async void SPI()
{
    // Use chip select line CS0
    var settings = new SpiConnectionSettings(0);

    // Create an SpiDevice with the specified Spi settings
    var controller = await SpiController.GetDefaultAsync();

    using (SpiDevice device = controller.GetDevice(settings))
    {
        byte[] writeBuf = { 0x01, 0x02, 0x03, 0x04 };
        device.Write(writeBuf);
    }
}
```
