---
title: Dragonboard 핀 매핑
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Dragonboard pin 매핑의 기능에 알아봅니다.
keywords: windows iot, Dragonboard, pin 매핑을 GPIO
ms.openlocfilehash: f6df962c6d05aa912013f8f0819c0789bfc393ce
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59515080"
---
# <a name="dragonboard-pin-mappings"></a>Dragonboard 핀 매핑

![Dragonboard Pin 헤더](../../media/PinMappingsDB/DB_Pinout.png)

하드웨어 인터페이스는 Dragonboard 보드의 40 핀 헤더를 통해 노출 됩니다. 기능은 다음과 같습니다.

* **11 배** -GPIO pin
* **2 x** -직렬 UARTs
* **1 x** -SPI 버스
* **2 x** -I2C 버스
* **1 x** -5V power pin
* **1 x** -1.8 v power pin
* **4 x** -pin 방지 매트를

참고는 Dragonboard 1.8 v는 모든 IO 핀에 논리 수준입니다. 

## <a name="gpio-pins"></a>GPIO Pin

이 장치에서 사용 가능한 GPIO를 살펴보겠습니다.

### <a name="gpio-pin-table"></a>GPIO Pin 테이블

다음 GPIO 핀은 Api를 통해 액세스할 수 있습니다.

> | GPIO# | 헤더 Pin         |
> |-------|--------------------|
> | 36    | 23                 |
> | 12    | 24                 |
> | 13    | 25                 |
> | 69    | 26                 |
> | 115   | 27                 |
> | 24    | 29                 |
> | 25    | 30                 |
> | 35    | 31                 |
> | 34    | 32                 |
> | 28    | 33                 |
> | 33    | 34                 |
> | 21    | 사용자 1 LED         | 
> | 120   | 사용자 led가 2         |         


예를 들어 다음 코드 열립니다 **GPIO 35** 출력으로 디지털 쓰고 '**1**' 핀 아웃 합니다.
         
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

* 출력은 GPIO 24에서 작동 하지 않습니다. 입력이 제대로 작동합니다.
* Pin, 부팅 시 InputPullDown으로 구성 되어 있지만 입력 (부동)로 변경 됩니다 처음 열 때
* Pin을 닫을 때 기본 상태로 전환 되지 않고 수행
* 의사 인터럽트 인터럽트 다중 핀에 설정 된 경우 표시 될 수 있습니다.


## <a name="serial-uart"></a>직렬 UART

Dragonboard에서 두 직렬 UARTS 됩니다 **UART0** 고 **UART1**

**UART0** 에 표준 **UART0 TX** 하 고 **UART0 RX** flow와 함께 줄 제어 신호 **UART0 CTS** 및 **UART0 RTS**.

* 5-고정 **UART0 TX**
* 7-고정 **UART0 RX**
* 3-고정 **UART0 CTS**
* 9-고정 **UART0 RTS**


**UART1** 포함 요소만 **UART1 TX** 하 고 **UART1 RX** 줄.

* 11-고정 **UART1 TX**
* 13-고정 **UART1 RX**

초기화 아래 예에서 **UART1** 읽기 뒤 쓰기를 수행 합니다.

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
> Visual Studio 2017에 매니페스트 디자이너에서 (appxmanifest 파일에 대 한 시각적 편집기) serialcommunication 기능에 영향을 주는 알려진된 버그가 있습니다.  프로그램 appxmanifest serialcommunication 기능에 추가 하는 경우 디자이너를 사용 하 여 프로그램 appxmanifest 수정 프로그램 appxmanifest (장치 xml 자식 없어집니다.) 손상 됩니다.  수 해결 방법이이 문제 appxmanifest 직접 편집 하 여 프로그램 appxmanifest를 마우스 오른쪽 단추로 클릭 하 고 상황에 맞는 메뉴에서 코드 보기를 선택 하 여.

다음 기능을 추가 해야 합니다 **Package.appxmanifest** 직렬 UART 코드를 실행 하기 위해 UWP 프로젝트에서 파일:

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

### <a name="i2c-pins"></a>I2C Pin

**I2C0** 두 줄을 사용 하 여 pin 헤더에 노출 **SDA** 고 **SCL**

* 17-고정 **I2C0 SDA**
* 15-고정 **I2C0 SCL**

**I2C1** 두 줄을 사용 하 여 pin 헤더에 노출 **SDA** 고 **SCL**

* Pin 21 - **I2C1 SDA**
* 19-고정 **I2C1 SCL**

### <a name="i2c-sample"></a>I2C 샘플

초기화 아래 예에서 **I2C0** I2C 장치 주소를 사용 하 여 데이터를 쓰고 **0x40**:

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

이 장치에서 사용할 수 있는 SPI 버스를 살펴보겠습니다.

### <a name="spi-pins"></a>SPI Pin

하나의 SPI 컨트롤러가 **SPI0** DB에서 사용할 수 있습니다.

* 고정 10- **SPI0 MISO**
* 14-고정 **SPI0 MOSI**
* 8-고정 **SPI0 SCLK**
* 12-고정 **SPI0 CS0**

### <a name="spi-issues"></a>SPI 문제

SPI 클록 4.8 mhz에 고정 됩니다. 요청 된 SPI 클록은 무시 됩니다. 


### <a name="spi-sample"></a>SPI 샘플

SPI를 수행 하는 방법을 예로 버스에 작성할 **SPI0** 아래에 표시 됩니다.

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
