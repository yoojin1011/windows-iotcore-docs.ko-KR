---
title: Minnowboard 최대 Pin 매핑
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Minnowboard Max의 pin 매핑 기능에 대해 알아봅니다.
keywords: windows iot, Minnowboard Max, pin 매핑, GPIO
ms.openlocfilehash: 884d9ee0d93167a13f39a28b28454daccb2eebad
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "60167504"
---
# <a name="minnowboard-max-pin-mappings"></a>MinnowBoard 최대 Pin 매핑

> [!NOTE] 
> 이 pin 매핑을 최신 버전의 Minnowboard와 비교 하려면 [여기](https://minnowboard.org/minnowboard-turbot/documentation)에서 설명서를 참조 하세요.

## <a name="overview"></a>개요

![MinnowBoard Max Pin 헤더](../../media/PinMappingsMBM/MBM_Pinout.png)

MinnowBoard Max의 하드웨어 인터페이스는 보드에서 26 핀 헤더 **JP1** 를 통해 노출 됩니다. 기능은 다음과 같습니다.

* **10 배** -GPIO 핀
* **2x** -직렬 uarts
* **1x** -SPI 버스
* **1x** -I2C 버스
* **1x** -5v 전원 pin
* **1x** -3.3 v 전원 pin
* **2** -접지 핀

MinnowBoard Max는 모든 IO 핀에 3.3 V 논리 수준을 사용 합니다. 또한 모든 pin은 [TXS0104E](http://www.ti.com/product/txs0104e) 수준 shifters에 의해 버퍼링 되며 전원 및 접지 핀은 제외 됩니다.
이러한 수준 shifters는 **&#x2126; 10k resistive 풀을 포함 하는 개방형 수집기 출력으로 나타나며, IO가 입력으로 설정 되었는지 또는 출력으로 설정 되었는지에 관계 없이 풀에 존재 합니다.**
 
수준 shifters의 개방형 수집기 특성은 핀에서 ' 0 '을 강력 하 게 출력할 수 있지만 약하게 출력 하는 ' 1 '을 의미 합니다. 이는 핀에서 현재를 그리는 장치 (예: LED)를 연결할 때 주의 해야 합니다. MinnowBoard Max에 LED를 인터페이스 하는 올바른 방법은 [Blinky 샘플](https://developer.microsoft.com/en-us/windows/iot/samples/helloblinky) 을 참조 하세요.

## <a name="gpio-pins"></a>GPIO 핀

다음 GPIO pin은 Api를 통해 액세스할 수 있습니다.

> | GPIO # | 헤더 Pin         |
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

**참고:** **Gpio 4** 및 **GPIO 5** 는 BIOS에 대 한 부트스트랩 구성 핀으로 MinnowBoard Max에서 사용 됩니다.
장치를 부팅 하는 동안 연결 된 장치에서 이러한 GPIO를 사용 하지 않도록 해야 합니다 .이로 인해 MBM이 부팅 되지 않을 수 있습니다.
MBM이 BIOS를 지 나 부팅 되 면 일반적으로 이러한 GPIO를 사용할 수 있습니다.
     
## <a name="gpio-sample"></a>GPIO 샘플

예를 들어 다음 코드는 **GPIO 5** 를 출력으로 열고 pin에 디지털 '**1**'을 기록 합니다.
         
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

MBM에서 사용할 수 있는 두 개의 직렬 UARTS가 있습니다. **UART1** 및 **UART2**

**UART1** 에는 표준 **UART1 TX** 및 **UART1 RX** 회선이 있으며,이는 CTS 및 **UART1 RTS**를 **UART1** 하는 흐름 제어 신호와 함께 있습니다.

* 핀 6- **UART1 TX**
* Pin 8- **UART1 RX**
* Pin 10- **UART1 CTS**
* 12- **UART1 RTS** 고정

UART1가 빌드 10240으로 작동 하지 않습니다. UART2 또는 USB 직렬 변환기를 사용 하십시오.

**UART2** 에는 **UART2 TX** 및 **UART2 RX** 줄만 포함 됩니다.

* Pin 17- **UART2 TX**
* Pin 19- **UART2 RX**

UART2는 흐름 제어를 지원 하지 않으므로 SerialDevice의 다음 속성에 액세스 하면 예외가 throw 될 수 있습니다.

 * BreakSignalState
 * IsDataTerminalReadyEnabled
 * IsRequestToSendEnabled
 * 핸드셰이크 전용 SerialHandshake는 지원 되지 않습니다.

아래 예제에서는 **UART2** 를 초기화 하 고 쓰기 후에 읽기를 수행 합니다.

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

직렬 UART 코드를 실행 하려면 UWP 프로젝트의 **appxmanifest.xml** 파일에 다음 기능을 추가 해야 합니다.

Visual Studio 2017에는 매니페스트 디자이너 (appxmanifest.xml 파일용 시각적 편집기)에서 serialcommunication 기능에 영향을 주는 알려진 버그가 있습니다.  Appxmanifest.xml가 serialcommunication 기능을 추가 하는 경우 디자이너를 사용 하 여 appxmanifest.xml를 수정 하면 appxmanifest.xml가 손상 됩니다 (장치 xml 자식은 손실 됨).  Appxmanifest.xml를 마우스 오른쪽 단추로 클릭 하 고 상황에 맞는 메뉴에서 코드 보기를 선택 하 여 appxmanifest.xml를 직접 편집이 문제를 해결할 수 있습니다.

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

이 장치에서 사용할 수 있는 I2C bus를 살펴보겠습니다.

### <a name="i2c-overview"></a>I2C 개요

**Sda** 와 **SCL**이라는 두 줄로 된 핀 헤더에는 하나의 I2C 컨트롤러 **I2C5** 노출 됩니다. 10K&#x2126; 내부 풀에 있는 저항기는 이미 이러한 줄에 있습니다.

* Pin 15- **I2C5 SDA**
* Pin 13- **I2C5 SCL**

### <a name="i2c-sample"></a>I2C 샘플

아래 예제에서는 **I2C5** 를 초기화 하 고 주소가 **0x40**인 I2C 장치에 데이터를 씁니다.

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

MinnowBoard Max에 I2C 버스와 관련 하 여 알려진 문제가 있어 특정 I2C 장치에서 통신 문제가 발생 합니다. 일반적으로 I2C 장치는 버스 요청 중에 해당 주소를 승인 합니다.
그러나 특정 조건에서이 승인은 shifters 수준에서 MBM으로 다시 전파 되지 않으므로 CPU에서 장치가 응답 하지 않았고 버스 트랜잭션을 취소 하는 것으로 간주 됩니다.
이 문제는 IO 핀에서 [TXS0104E](http://www.ti.com/product/txs0104e) 수준 shifters와 관련 된 것으로 보입니다 .이는 줄의 전압 급증으로 인해 중간에 트리거될 수 있습니다.
현재 해결 방법은 급증을 방지 하는 데 도움이 되는 I2C SCK 줄에서 100 옴 저항기를 계열에 삽입 하는 것입니다. 모든 장치가 영향을 받지 않으므로이 해결 방법은 버스 응답을 가져오는 데 문제가 있는 경우에만 필요 합니다. 이 해결 방법이 필요한 것으로 알려진 장치 하나는 HTU21D입니다.

## <a name="spi-bus"></a>SPI 버스

이 장치에서 사용할 수 있는 SPI bus를 살펴보겠습니다.

### <a name="spi-overview"></a>SPI 개요

MBM에서 사용할 수 있는 SPI 컨트롤러 **SPI0** 하나는 다음과 같습니다.

* 핀 9- **SPI0 MOSI**
* 핀 7- **SPI0 mia**
* 핀 11- **SPI0 SCLK**
* 핀 5- **SPI0 CS0**


### <a name="spi-sample"></a>SPI 샘플

다음은 bus **SPI0** 에서 SPI 쓰기를 수행 하는 방법에 대 한 예제입니다.

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

