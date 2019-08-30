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
# <a name="minnowboard-max-pin-mappings"></a><span data-ttu-id="44397-104">MinnowBoard 최대 Pin 매핑</span><span class="sxs-lookup"><span data-stu-id="44397-104">MinnowBoard Max Pin Mappings</span></span>

> [!NOTE] 
> <span data-ttu-id="44397-105">이 pin 매핑을 최신 버전의 Minnowboard와 비교 하려면 [여기](https://minnowboard.org/minnowboard-turbot/documentation)에서 설명서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="44397-105">To compare this pin mapping to newer versions of the Minnowboard, please visit documentation [here](https://minnowboard.org/minnowboard-turbot/documentation).</span></span>

## <a name="overview"></a><span data-ttu-id="44397-106">개요</span><span class="sxs-lookup"><span data-stu-id="44397-106">Overview</span></span>

![MinnowBoard Max Pin 헤더](../../media/PinMappingsMBM/MBM_Pinout.png)

<span data-ttu-id="44397-108">MinnowBoard Max의 하드웨어 인터페이스는 보드에서 26 핀 헤더 **JP1** 를 통해 노출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="44397-108">Hardware interfaces for the MinnowBoard Max are exposed through the 26-pin header **JP1** on the board.</span></span> <span data-ttu-id="44397-109">기능은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="44397-109">Functionality includes:</span></span>

* <span data-ttu-id="44397-110">**10 배** -GPIO 핀</span><span class="sxs-lookup"><span data-stu-id="44397-110">**10x** - GPIO pins</span></span>
* <span data-ttu-id="44397-111">**2x** -직렬 uarts</span><span class="sxs-lookup"><span data-stu-id="44397-111">**2x** - Serial UARTs</span></span>
* <span data-ttu-id="44397-112">**1x** -SPI 버스</span><span class="sxs-lookup"><span data-stu-id="44397-112">**1x** - SPI bus</span></span>
* <span data-ttu-id="44397-113">**1x** -I2C 버스</span><span class="sxs-lookup"><span data-stu-id="44397-113">**1x** - I2C bus</span></span>
* <span data-ttu-id="44397-114">**1x** -5v 전원 pin</span><span class="sxs-lookup"><span data-stu-id="44397-114">**1x** - 5V power pin</span></span>
* <span data-ttu-id="44397-115">**1x** -3.3 v 전원 pin</span><span class="sxs-lookup"><span data-stu-id="44397-115">**1x** - 3.3V power pin</span></span>
* <span data-ttu-id="44397-116">**2** -접지 핀</span><span class="sxs-lookup"><span data-stu-id="44397-116">**2x** - Ground pins</span></span>

<span data-ttu-id="44397-117">MinnowBoard Max는 모든 IO 핀에 3.3 V 논리 수준을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="44397-117">The MinnowBoard Max uses 3.3V logic levels on all IO pins.</span></span> <span data-ttu-id="44397-118">또한 모든 pin은 [TXS0104E](http://www.ti.com/product/txs0104e) 수준 shifters에 의해 버퍼링 되며 전원 및 접지 핀은 제외 됩니다.</span><span class="sxs-lookup"><span data-stu-id="44397-118">In addition all the pins are buffered by [TXS0104E](http://www.ti.com/product/txs0104e) level shifters, with the exception of power and ground pins.</span></span>
<span data-ttu-id="44397-119">이러한 수준 shifters는 **&#x2126; 10k resistive 풀을 포함 하는 개방형 수집기 출력으로 나타나며, IO가 입력으로 설정 되었는지 또는 출력으로 설정 되었는지에 관계 없이 풀에 존재 합니다.**</span><span class="sxs-lookup"><span data-stu-id="44397-119">These level shifters appear as open collector outputs with a **10K&#x2126; resistive pull-up, and the pull-up is present regardless of whether the IO is set to input or output.**</span></span>
 
<span data-ttu-id="44397-120">수준 shifters의 개방형 수집기 특성은 핀에서 ' 0 '을 강력 하 게 출력할 수 있지만 약하게 출력 하는 ' 1 '을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="44397-120">The open-collector nature of the level shifters means is that the pins can output a '0' strongly, but only weakly output a '1'.</span></span> <span data-ttu-id="44397-121">이는 핀에서 현재를 그리는 장치 (예: LED)를 연결할 때 주의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="44397-121">This is important to keep in mind when attaching devices which draw current from the pins (such as an LED).</span></span> <span data-ttu-id="44397-122">MinnowBoard Max에 LED를 인터페이스 하는 올바른 방법은 [Blinky 샘플](https://developer.microsoft.com/en-us/windows/iot/samples/helloblinky) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="44397-122">See the [Blinky Sample](https://developer.microsoft.com/en-us/windows/iot/samples/helloblinky) for the correct way to interface an LED to the MinnowBoard Max.</span></span>

## <a name="gpio-pins"></a><span data-ttu-id="44397-123">GPIO 핀</span><span class="sxs-lookup"><span data-stu-id="44397-123">GPIO Pins</span></span>

<span data-ttu-id="44397-124">다음 GPIO pin은 Api를 통해 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44397-124">The following GPIO pins are accessible through APIs:</span></span>

> | <span data-ttu-id="44397-125">GPIO #</span><span class="sxs-lookup"><span data-stu-id="44397-125">GPIO#</span></span> | <span data-ttu-id="44397-126">헤더 Pin</span><span class="sxs-lookup"><span data-stu-id="44397-126">Header Pin</span></span>         |
> |-------|--------------------|
> | <span data-ttu-id="44397-127">0</span><span class="sxs-lookup"><span data-stu-id="44397-127">0</span></span>     | <span data-ttu-id="44397-128">21</span><span class="sxs-lookup"><span data-stu-id="44397-128">21</span></span>                 |
> | <span data-ttu-id="44397-129">1</span><span class="sxs-lookup"><span data-stu-id="44397-129">1</span></span>     | <span data-ttu-id="44397-130">23</span><span class="sxs-lookup"><span data-stu-id="44397-130">23</span></span>                 |
> | <span data-ttu-id="44397-131">2</span><span class="sxs-lookup"><span data-stu-id="44397-131">2</span></span>     | <span data-ttu-id="44397-132">25</span><span class="sxs-lookup"><span data-stu-id="44397-132">25</span></span>                 |
> | <span data-ttu-id="44397-133">3</span><span class="sxs-lookup"><span data-stu-id="44397-133">3</span></span>     | <span data-ttu-id="44397-134">14</span><span class="sxs-lookup"><span data-stu-id="44397-134">14</span></span>                 |
> | <span data-ttu-id="44397-135">4</span><span class="sxs-lookup"><span data-stu-id="44397-135">4</span></span>     | <span data-ttu-id="44397-136">16</span><span class="sxs-lookup"><span data-stu-id="44397-136">16</span></span>                 |
> | <span data-ttu-id="44397-137">5</span><span class="sxs-lookup"><span data-stu-id="44397-137">5</span></span>     | <span data-ttu-id="44397-138">18</span><span class="sxs-lookup"><span data-stu-id="44397-138">18</span></span>                 |
> | <span data-ttu-id="44397-139">6</span><span class="sxs-lookup"><span data-stu-id="44397-139">6</span></span>     | <span data-ttu-id="44397-140">20</span><span class="sxs-lookup"><span data-stu-id="44397-140">20</span></span>                 |
> | <span data-ttu-id="44397-141">7</span><span class="sxs-lookup"><span data-stu-id="44397-141">7</span></span>     | <span data-ttu-id="44397-142">22</span><span class="sxs-lookup"><span data-stu-id="44397-142">22</span></span>                 |
> | <span data-ttu-id="44397-143">8</span><span class="sxs-lookup"><span data-stu-id="44397-143">8</span></span>     | <span data-ttu-id="44397-144">24</span><span class="sxs-lookup"><span data-stu-id="44397-144">24</span></span>                 |
> | <span data-ttu-id="44397-145">9</span><span class="sxs-lookup"><span data-stu-id="44397-145">9</span></span>     | <span data-ttu-id="44397-146">26</span><span class="sxs-lookup"><span data-stu-id="44397-146">26</span></span>                 |

<span data-ttu-id="44397-147">**참고:** **Gpio 4** 및 **GPIO 5** 는 BIOS에 대 한 부트스트랩 구성 핀으로 MinnowBoard Max에서 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="44397-147">**Note:** **GPIO 4** and **GPIO 5** are used by the MinnowBoard Max as bootstrap configuration pins for the BIOS.</span></span>
<span data-ttu-id="44397-148">장치를 부팅 하는 동안 연결 된 장치에서 이러한 GPIO를 사용 하지 않도록 해야 합니다 .이로 인해 MBM이 부팅 되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44397-148">Make sure that attached devices do not drive these GPIO low during boot, as this could prevent the MBM from booting.</span></span>
<span data-ttu-id="44397-149">MBM이 BIOS를 지 나 부팅 되 면 일반적으로 이러한 GPIO를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44397-149">After the MBM has booted past the BIOS, these GPIO can be used normally.</span></span>
     
## <a name="gpio-sample"></a><span data-ttu-id="44397-150">GPIO 샘플</span><span class="sxs-lookup"><span data-stu-id="44397-150">GPIO Sample</span></span>

<span data-ttu-id="44397-151">예를 들어 다음 코드는 **GPIO 5** 를 출력으로 열고 pin에 디지털 '**1**'을 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="44397-151">As an example, the following code opens **GPIO 5** as an output and writes a digital '**1**' out on the pin:</span></span>
         
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

## <a name="serial-uart"></a><span data-ttu-id="44397-152">직렬 UART</span><span class="sxs-lookup"><span data-stu-id="44397-152">Serial UART</span></span>

<span data-ttu-id="44397-153">MBM에서 사용할 수 있는 두 개의 직렬 UARTS가 있습니다. **UART1** 및 **UART2**</span><span class="sxs-lookup"><span data-stu-id="44397-153">There are two Serial UARTS available on the MBM: **UART1** and **UART2**</span></span>

<span data-ttu-id="44397-154">**UART1** 에는 표준 **UART1 TX** 및 **UART1 RX** 회선이 있으며,이는 CTS 및 **UART1 RTS**를 **UART1** 하는 흐름 제어 신호와 함께 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44397-154">**UART1** has the standard **UART1 TX** and **UART1 RX** lines, along with flow control signals **UART1 CTS** and **UART1 RTS**.</span></span>

* <span data-ttu-id="44397-155">핀 6- **UART1 TX**</span><span class="sxs-lookup"><span data-stu-id="44397-155">Pin 6  - **UART1 TX**</span></span>
* <span data-ttu-id="44397-156">Pin 8- **UART1 RX**</span><span class="sxs-lookup"><span data-stu-id="44397-156">Pin 8  - **UART1 RX**</span></span>
* <span data-ttu-id="44397-157">Pin 10- **UART1 CTS**</span><span class="sxs-lookup"><span data-stu-id="44397-157">Pin 10 - **UART1 CTS**</span></span>
* <span data-ttu-id="44397-158">12- **UART1 RTS** 고정</span><span class="sxs-lookup"><span data-stu-id="44397-158">Pin 12 - **UART1 RTS**</span></span>

<span data-ttu-id="44397-159">UART1가 빌드 10240으로 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="44397-159">UART1 is not working as of build 10240.</span></span> <span data-ttu-id="44397-160">UART2 또는 USB 직렬 변환기를 사용 하십시오.</span><span class="sxs-lookup"><span data-stu-id="44397-160">Please use UART2 or a USB-Serial converter.</span></span>

<span data-ttu-id="44397-161">**UART2** 에는 **UART2 TX** 및 **UART2 RX** 줄만 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="44397-161">**UART2** includes just the **UART2 TX** and **UART2 RX** lines.</span></span>

* <span data-ttu-id="44397-162">Pin 17- **UART2 TX**</span><span class="sxs-lookup"><span data-stu-id="44397-162">Pin 17  - **UART2 TX**</span></span>
* <span data-ttu-id="44397-163">Pin 19- **UART2 RX**</span><span class="sxs-lookup"><span data-stu-id="44397-163">Pin 19  - **UART2 RX**</span></span>

<span data-ttu-id="44397-164">UART2는 흐름 제어를 지원 하지 않으므로 SerialDevice의 다음 속성에 액세스 하면 예외가 throw 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44397-164">UART2 does not support flow control, so accessing the following properties of SerialDevice can result in an exception being thrown:</span></span>

 * <span data-ttu-id="44397-165">BreakSignalState</span><span class="sxs-lookup"><span data-stu-id="44397-165">BreakSignalState</span></span>
 * <span data-ttu-id="44397-166">IsDataTerminalReadyEnabled</span><span class="sxs-lookup"><span data-stu-id="44397-166">IsDataTerminalReadyEnabled</span></span>
 * <span data-ttu-id="44397-167">IsRequestToSendEnabled</span><span class="sxs-lookup"><span data-stu-id="44397-167">IsRequestToSendEnabled</span></span>
 * <span data-ttu-id="44397-168">핸드셰이크 전용 SerialHandshake는 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="44397-168">Handshake - only SerialHandshake.None is supported</span></span>

<span data-ttu-id="44397-169">아래 예제에서는 **UART2** 를 초기화 하 고 쓰기 후에 읽기를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="44397-169">The example below initializes **UART2** and performs a write followed by a read:</span></span>

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

<span data-ttu-id="44397-170">직렬 UART 코드를 실행 하려면 UWP 프로젝트의 **appxmanifest.xml** 파일에 다음 기능을 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="44397-170">Note that you must add the following capability to the **Package.appxmanifest** file in your UWP project to run Serial UART code:</span></span>

<span data-ttu-id="44397-171">Visual Studio 2017에는 매니페스트 디자이너 (appxmanifest.xml 파일용 시각적 편집기)에서 serialcommunication 기능에 영향을 주는 알려진 버그가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44397-171">Visual Studio 2017 has a known bug in the Manifest Designer (the visual editor for appxmanifest files) that affects the serialcommunication capability.</span></span>  <span data-ttu-id="44397-172">Appxmanifest.xml가 serialcommunication 기능을 추가 하는 경우 디자이너를 사용 하 여 appxmanifest.xml를 수정 하면 appxmanifest.xml가 손상 됩니다 (장치 xml 자식은 손실 됨).</span><span class="sxs-lookup"><span data-stu-id="44397-172">If your appxmanifest adds the serialcommunication capability, modifying your appxmanifest with the designer will corrupt your appxmanifest (the Device xml child will be lost).</span></span>  <span data-ttu-id="44397-173">Appxmanifest.xml를 마우스 오른쪽 단추로 클릭 하 고 상황에 맞는 메뉴에서 코드 보기를 선택 하 여 appxmanifest.xml를 직접 편집이 문제를 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44397-173">You can workaround this problem by hand editting the appxmanifest by right-clicking your appxmanifest and selecting View Code from the context menu.</span></span>

```
  <Capabilities>
    <DeviceCapability Name="serialcommunication">
      <Device Id="any">
        <Function Type="name:serialPort" />
      </Device>
    </DeviceCapability>
  </Capabilities>
```

## <a name="i2c-bus"></a><span data-ttu-id="44397-174">I2C 버스</span><span class="sxs-lookup"><span data-stu-id="44397-174">I2C Bus</span></span>

<span data-ttu-id="44397-175">이 장치에서 사용할 수 있는 I2C bus를 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="44397-175">Let's look at the I2C bus available on this device.</span></span>

### <a name="i2c-overview"></a><span data-ttu-id="44397-176">I2C 개요</span><span class="sxs-lookup"><span data-stu-id="44397-176">I2C Overview</span></span>

<span data-ttu-id="44397-177">**Sda** 와 **SCL**이라는 두 줄로 된 핀 헤더에는 하나의 I2C 컨트롤러 **I2C5** 노출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="44397-177">There is one I2C controller **I2C5** exposed on the pin header with two lines **SDA** and **SCL**.</span></span> <span data-ttu-id="44397-178">10K&#x2126; 내부 풀에 있는 저항기는 이미 이러한 줄에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44397-178">10K&#x2126; internal pull-up resistors are already present on these lines.</span></span>

* <span data-ttu-id="44397-179">Pin 15- **I2C5 SDA**</span><span class="sxs-lookup"><span data-stu-id="44397-179">Pin 15 - **I2C5 SDA**</span></span>
* <span data-ttu-id="44397-180">Pin 13- **I2C5 SCL**</span><span class="sxs-lookup"><span data-stu-id="44397-180">Pin 13 - **I2C5 SCL**</span></span>

### <a name="i2c-sample"></a><span data-ttu-id="44397-181">I2C 샘플</span><span class="sxs-lookup"><span data-stu-id="44397-181">I2C Sample</span></span>

<span data-ttu-id="44397-182">아래 예제에서는 **I2C5** 를 초기화 하 고 주소가 **0x40**인 I2C 장치에 데이터를 씁니다.</span><span class="sxs-lookup"><span data-stu-id="44397-182">The example below initializes **I2C5** and writes data to an I2C device with address **0x40**:</span></span>

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

### <a name="i2c-issues"></a><span data-ttu-id="44397-183">I2C 문제</span><span class="sxs-lookup"><span data-stu-id="44397-183">I2C Issues</span></span>

<span data-ttu-id="44397-184">MinnowBoard Max에 I2C 버스와 관련 하 여 알려진 문제가 있어 특정 I2C 장치에서 통신 문제가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="44397-184">The MinnowBoard Max has a known issue with the I2C bus which causes communication problems with certain I2C devices.</span></span> <span data-ttu-id="44397-185">일반적으로 I2C 장치는 버스 요청 중에 해당 주소를 승인 합니다.</span><span class="sxs-lookup"><span data-stu-id="44397-185">Normally, an I2C device will acknowledge its address during a bus request.</span></span>
<span data-ttu-id="44397-186">그러나 특정 조건에서이 승인은 shifters 수준에서 MBM으로 다시 전파 되지 않으므로 CPU에서 장치가 응답 하지 않았고 버스 트랜잭션을 취소 하는 것으로 간주 됩니다.</span><span class="sxs-lookup"><span data-stu-id="44397-186">However, under certain conditions this acknowledge fails to propagate back through the level shifters to the MBM, and as a result the CPU thinks the device did not respond and cancels the bus transaction.</span></span>
<span data-ttu-id="44397-187">이 문제는 IO 핀에서 [TXS0104E](http://www.ti.com/product/txs0104e) 수준 shifters와 관련 된 것으로 보입니다 .이는 줄의 전압 급증으로 인해 중간에 트리거될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44397-187">The issue seems to be related to the [TXS0104E](http://www.ti.com/product/txs0104e) level shifters on the IO pins, which can trigger prematurely due to voltage spikes on the line.</span></span>
<span data-ttu-id="44397-188">현재 해결 방법은 급증을 방지 하는 데 도움이 되는 I2C SCK 줄에서 100 옴 저항기를 계열에 삽입 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="44397-188">The current workaround is to insert a 100 ohm resistor in series with the I2C SCK line, which helps suppress spikes.</span></span> <span data-ttu-id="44397-189">모든 장치가 영향을 받지 않으므로이 해결 방법은 버스 응답을 가져오는 데 문제가 있는 경우에만 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="44397-189">Not all devices are affected, so this workaround is only required if you are having trouble getting a bus response.</span></span> <span data-ttu-id="44397-190">이 해결 방법이 필요한 것으로 알려진 장치 하나는 HTU21D입니다.</span><span class="sxs-lookup"><span data-stu-id="44397-190">One device that is known to require this workaround is the HTU21D.</span></span>

## <a name="spi-bus"></a><span data-ttu-id="44397-191">SPI 버스</span><span class="sxs-lookup"><span data-stu-id="44397-191">SPI Bus</span></span>

<span data-ttu-id="44397-192">이 장치에서 사용할 수 있는 SPI bus를 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="44397-192">Let's look at the SPI bus available on this device.</span></span>

### <a name="spi-overview"></a><span data-ttu-id="44397-193">SPI 개요</span><span class="sxs-lookup"><span data-stu-id="44397-193">SPI Overview</span></span>

<span data-ttu-id="44397-194">MBM에서 사용할 수 있는 SPI 컨트롤러 **SPI0** 하나는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="44397-194">There is one SPI controller **SPI0** available on the MBM:</span></span>

* <span data-ttu-id="44397-195">핀 9- **SPI0 MOSI**</span><span class="sxs-lookup"><span data-stu-id="44397-195">Pin 9 - **SPI0 MOSI**</span></span>
* <span data-ttu-id="44397-196">핀 7- **SPI0 mia**</span><span class="sxs-lookup"><span data-stu-id="44397-196">Pin 7 - **SPI0 MISO**</span></span>
* <span data-ttu-id="44397-197">핀 11- **SPI0 SCLK**</span><span class="sxs-lookup"><span data-stu-id="44397-197">Pin 11 - **SPI0 SCLK**</span></span>
* <span data-ttu-id="44397-198">핀 5- **SPI0 CS0**</span><span class="sxs-lookup"><span data-stu-id="44397-198">Pin 5 - **SPI0 CS0**</span></span>


### <a name="spi-sample"></a><span data-ttu-id="44397-199">SPI 샘플</span><span class="sxs-lookup"><span data-stu-id="44397-199">SPI Sample</span></span>

<span data-ttu-id="44397-200">다음은 bus **SPI0** 에서 SPI 쓰기를 수행 하는 방법에 대 한 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="44397-200">An example on how to perform a SPI write on bus **SPI0** is shown below:</span></span>

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

