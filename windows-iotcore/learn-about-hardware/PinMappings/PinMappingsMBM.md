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
# <a name="minnowboard-max-pin-mappings"></a><span data-ttu-id="d44bf-104">MinnowBoard 최대 핀 매핑</span><span class="sxs-lookup"><span data-stu-id="d44bf-104">MinnowBoard Max Pin Mappings</span></span>

> [!NOTE] 
> <span data-ttu-id="d44bf-105">이 pin 매핑에 Minnowboard의 최신 버전을 비교 하려면 설명서를 참조 하세요 [여기](https://minnowboard.org/minnowboard-turbot/documentation)합니다.</span><span class="sxs-lookup"><span data-stu-id="d44bf-105">To compare this pin mapping to newer versions of the Minnowboard, please visit documentation [here](https://minnowboard.org/minnowboard-turbot/documentation).</span></span>

## <a name="overview"></a><span data-ttu-id="d44bf-106">개요</span><span class="sxs-lookup"><span data-stu-id="d44bf-106">Overview</span></span>

![MinnowBoard 최대 Pin 헤더](../../media/PinMappingsMBM/MBM_Pinout.png)

<span data-ttu-id="d44bf-108">26 pin 헤더를 통해 MinnowBoard 최대 하드웨어 인터페이스를 노출 시키는 **JP1** 보드.</span><span class="sxs-lookup"><span data-stu-id="d44bf-108">Hardware interfaces for the MinnowBoard Max are exposed through the 26-pin header **JP1** on the board.</span></span> <span data-ttu-id="d44bf-109">기능은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d44bf-109">Functionality includes:</span></span>

* <span data-ttu-id="d44bf-110">**10 배** -GPIO pin</span><span class="sxs-lookup"><span data-stu-id="d44bf-110">**10x** - GPIO pins</span></span>
* <span data-ttu-id="d44bf-111">**2 x** -직렬 UARTs</span><span class="sxs-lookup"><span data-stu-id="d44bf-111">**2x** - Serial UARTs</span></span>
* <span data-ttu-id="d44bf-112">**1 x** -SPI 버스</span><span class="sxs-lookup"><span data-stu-id="d44bf-112">**1x** - SPI bus</span></span>
* <span data-ttu-id="d44bf-113">**1x** - I2C bus</span><span class="sxs-lookup"><span data-stu-id="d44bf-113">**1x** - I2C bus</span></span>
* <span data-ttu-id="d44bf-114">**1 x** -5V power pin</span><span class="sxs-lookup"><span data-stu-id="d44bf-114">**1x** - 5V power pin</span></span>
* <span data-ttu-id="d44bf-115">**1 x** -3.3V power pin</span><span class="sxs-lookup"><span data-stu-id="d44bf-115">**1x** - 3.3V power pin</span></span>
* <span data-ttu-id="d44bf-116">**2 x** -pin 방지 매트를</span><span class="sxs-lookup"><span data-stu-id="d44bf-116">**2x** - Ground pins</span></span>

<span data-ttu-id="d44bf-117">모든 IO 핀에 MinnowBoard 최대 사용 3.3V 논리 수준입니다.</span><span class="sxs-lookup"><span data-stu-id="d44bf-117">The MinnowBoard Max uses 3.3V logic levels on all IO pins.</span></span> <span data-ttu-id="d44bf-118">모든 핀으로 버퍼링 됩니다는 또한 [TXS0104E](http://www.ti.com/product/txs0104e) 전원 및 그라운드 핀을 제외 하 고 변환기 수준입니다.</span><span class="sxs-lookup"><span data-stu-id="d44bf-118">In addition all the pins are buffered by [TXS0104E](http://www.ti.com/product/txs0104e) level shifters, with the exception of power and ground pins.</span></span>
<span data-ttu-id="d44bf-119">이러한 수준 변환기 열기 수집기의 출력으로 표시를 **10k&#x2126; 저항 식 풀업은 풀업 이며 IO 입력 또는 출력으로 설정 되어 있는지 여부에 관계 없이 표시 합니다.**</span><span class="sxs-lookup"><span data-stu-id="d44bf-119">These level shifters appear as open collector outputs with a **10K&#x2126; resistive pull-up, and the pull-up is present regardless of whether the IO is set to input or output.**</span></span>
 
<span data-ttu-id="d44bf-120">오픈 수집기 수준 변환기 의미 하는 ' 0 ', 강력 하 게 하지만 약한만 출력 ' 1' 핀을 출력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d44bf-120">The open-collector nature of the level shifters means is that the pins can output a '0' strongly, but only weakly output a '1'.</span></span> <span data-ttu-id="d44bf-121">이 장치 (예: LED) 핀에서 현재 그리기를 연결 하는 경우에 유의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d44bf-121">This is important to keep in mind when attaching devices which draw current from the pins (such as an LED).</span></span> <span data-ttu-id="d44bf-122">참조 된 [쳐다 샘플](https://developer.microsoft.com/en-us/windows/iot/samples/helloblinky) MinnowBoard max LED를 인터페이스에 대 한 올바른 방법에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="d44bf-122">See the [Blinky Sample](https://developer.microsoft.com/en-us/windows/iot/samples/helloblinky) for the correct way to interface an LED to the MinnowBoard Max.</span></span>

## <a name="gpio-pins"></a><span data-ttu-id="d44bf-123">GPIO Pin</span><span class="sxs-lookup"><span data-stu-id="d44bf-123">GPIO Pins</span></span>

<span data-ttu-id="d44bf-124">다음 GPIO 핀은 Api를 통해 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d44bf-124">The following GPIO pins are accessible through APIs:</span></span>

> | <span data-ttu-id="d44bf-125">GPIO#</span><span class="sxs-lookup"><span data-stu-id="d44bf-125">GPIO#</span></span> | <span data-ttu-id="d44bf-126">헤더 Pin</span><span class="sxs-lookup"><span data-stu-id="d44bf-126">Header Pin</span></span>         |
> |-------|--------------------|
> | <span data-ttu-id="d44bf-127">0</span><span class="sxs-lookup"><span data-stu-id="d44bf-127">0</span></span>     | <span data-ttu-id="d44bf-128">21</span><span class="sxs-lookup"><span data-stu-id="d44bf-128">21</span></span>                 |
> | <span data-ttu-id="d44bf-129">1</span><span class="sxs-lookup"><span data-stu-id="d44bf-129">1</span></span>     | <span data-ttu-id="d44bf-130">23</span><span class="sxs-lookup"><span data-stu-id="d44bf-130">23</span></span>                 |
> | <span data-ttu-id="d44bf-131">2</span><span class="sxs-lookup"><span data-stu-id="d44bf-131">2</span></span>     | <span data-ttu-id="d44bf-132">25</span><span class="sxs-lookup"><span data-stu-id="d44bf-132">25</span></span>                 |
> | <span data-ttu-id="d44bf-133">3</span><span class="sxs-lookup"><span data-stu-id="d44bf-133">3</span></span>     | <span data-ttu-id="d44bf-134">14</span><span class="sxs-lookup"><span data-stu-id="d44bf-134">14</span></span>                 |
> | <span data-ttu-id="d44bf-135">4</span><span class="sxs-lookup"><span data-stu-id="d44bf-135">4</span></span>     | <span data-ttu-id="d44bf-136">16</span><span class="sxs-lookup"><span data-stu-id="d44bf-136">16</span></span>                 |
> | <span data-ttu-id="d44bf-137">5</span><span class="sxs-lookup"><span data-stu-id="d44bf-137">5</span></span>     | <span data-ttu-id="d44bf-138">18</span><span class="sxs-lookup"><span data-stu-id="d44bf-138">18</span></span>                 |
> | <span data-ttu-id="d44bf-139">6</span><span class="sxs-lookup"><span data-stu-id="d44bf-139">6</span></span>     | <span data-ttu-id="d44bf-140">20</span><span class="sxs-lookup"><span data-stu-id="d44bf-140">20</span></span>                 |
> | <span data-ttu-id="d44bf-141">7</span><span class="sxs-lookup"><span data-stu-id="d44bf-141">7</span></span>     | <span data-ttu-id="d44bf-142">22</span><span class="sxs-lookup"><span data-stu-id="d44bf-142">22</span></span>                 |
> | <span data-ttu-id="d44bf-143">8</span><span class="sxs-lookup"><span data-stu-id="d44bf-143">8</span></span>     | <span data-ttu-id="d44bf-144">24</span><span class="sxs-lookup"><span data-stu-id="d44bf-144">24</span></span>                 |
> | <span data-ttu-id="d44bf-145">9</span><span class="sxs-lookup"><span data-stu-id="d44bf-145">9</span></span>     | <span data-ttu-id="d44bf-146">26</span><span class="sxs-lookup"><span data-stu-id="d44bf-146">26</span></span>                 |

<span data-ttu-id="d44bf-147">**참고:** **GPIO 4** 하 고 **GPIO 5** MinnowBoard 최대에서 BIOS 부트스트랩 구성 핀으로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d44bf-147">**Note:** **GPIO 4** and **GPIO 5** are used by the MinnowBoard Max as bootstrap configuration pins for the BIOS.</span></span>
<span data-ttu-id="d44bf-148">MBM 부팅 되지 않을 수 있습니다이 연결 된 장치를 유도 하지 않습니다 이러한 GPIO 낮은 부팅 하는 동안 입력 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="d44bf-148">Make sure that attached devices do not drive these GPIO low during boot, as this could prevent the MBM from booting.</span></span>
<span data-ttu-id="d44bf-149">BIOS 과거의 MBM가 부팅 되 면 이러한 GPIO 일반적으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d44bf-149">After the MBM has booted past the BIOS, these GPIO can be used normally.</span></span>
     
## <a name="gpio-sample"></a><span data-ttu-id="d44bf-150">GPIO 샘플</span><span class="sxs-lookup"><span data-stu-id="d44bf-150">GPIO Sample</span></span>

<span data-ttu-id="d44bf-151">예를 들어 다음 코드 열립니다 **GPIO 5** 출력으로 디지털 쓰고 '**1**' 핀 아웃 합니다.</span><span class="sxs-lookup"><span data-stu-id="d44bf-151">As an example, the following code opens **GPIO 5** as an output and writes a digital '**1**' out on the pin:</span></span>
         
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

## <a name="serial-uart"></a><span data-ttu-id="d44bf-152">직렬 UART</span><span class="sxs-lookup"><span data-stu-id="d44bf-152">Serial UART</span></span>

<span data-ttu-id="d44bf-153">MBM에 사용할 직렬 UARTS 두 가지. **UART1** 고 **UART2**</span><span class="sxs-lookup"><span data-stu-id="d44bf-153">There are two Serial UARTS available on the MBM: **UART1** and **UART2**</span></span>

<span data-ttu-id="d44bf-154">**UART1** 에 표준 **UART1 TX** 하 고 **UART1 RX** flow와 함께 줄 제어 신호 **UART1 CTS** 및 **UART1 RTS**.</span><span class="sxs-lookup"><span data-stu-id="d44bf-154">**UART1** has the standard **UART1 TX** and **UART1 RX** lines, along with flow control signals **UART1 CTS** and **UART1 RTS**.</span></span>

* <span data-ttu-id="d44bf-155">6-고정 **UART1 TX**</span><span class="sxs-lookup"><span data-stu-id="d44bf-155">Pin 6  - **UART1 TX**</span></span>
* <span data-ttu-id="d44bf-156">8-고정 **UART1 RX**</span><span class="sxs-lookup"><span data-stu-id="d44bf-156">Pin 8  - **UART1 RX**</span></span>
* <span data-ttu-id="d44bf-157">고정 10- **UART1 CTS**</span><span class="sxs-lookup"><span data-stu-id="d44bf-157">Pin 10 - **UART1 CTS**</span></span>
* <span data-ttu-id="d44bf-158">12-고정 **UART1 RTS**</span><span class="sxs-lookup"><span data-stu-id="d44bf-158">Pin 12 - **UART1 RTS**</span></span>

<span data-ttu-id="d44bf-159">UART1 빌드 10240 기준으로 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d44bf-159">UART1 is not working as of build 10240.</span></span> <span data-ttu-id="d44bf-160">UART2 또는 USB-직렬 변환기를 사용 하세요.</span><span class="sxs-lookup"><span data-stu-id="d44bf-160">Please use UART2 or a USB-Serial converter.</span></span>

<span data-ttu-id="d44bf-161">**UART2** 포함 요소만 **UART2 TX** 하 고 **UART2 RX** 줄.</span><span class="sxs-lookup"><span data-stu-id="d44bf-161">**UART2** includes just the **UART2 TX** and **UART2 RX** lines.</span></span>

* <span data-ttu-id="d44bf-162">17-고정 **UART2 TX**</span><span class="sxs-lookup"><span data-stu-id="d44bf-162">Pin 17  - **UART2 TX**</span></span>
* <span data-ttu-id="d44bf-163">19-고정 **UART2 RX**</span><span class="sxs-lookup"><span data-stu-id="d44bf-163">Pin 19  - **UART2 RX**</span></span>

<span data-ttu-id="d44bf-164">예외가 발생 하면 직렬의 다음 속성에 액세스 하므로 UART2 흐름 제어를 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d44bf-164">UART2 does not support flow control, so accessing the following properties of SerialDevice can result in an exception being thrown:</span></span>

 * <span data-ttu-id="d44bf-165">BreakSignalState</span><span class="sxs-lookup"><span data-stu-id="d44bf-165">BreakSignalState</span></span>
 * <span data-ttu-id="d44bf-166">IsDataTerminalReadyEnabled</span><span class="sxs-lookup"><span data-stu-id="d44bf-166">IsDataTerminalReadyEnabled</span></span>
 * <span data-ttu-id="d44bf-167">IsRequestToSendEnabled</span><span class="sxs-lookup"><span data-stu-id="d44bf-167">IsRequestToSendEnabled</span></span>
 * <span data-ttu-id="d44bf-168">핸드셰이크-SerialHandshake.None만 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d44bf-168">Handshake - only SerialHandshake.None is supported</span></span>

<span data-ttu-id="d44bf-169">초기화 아래 예에서 **UART2** 읽기 뒤 쓰기를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="d44bf-169">The example below initializes **UART2** and performs a write followed by a read:</span></span>

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

<span data-ttu-id="d44bf-170">다음 기능을 추가 해야 합니다 **Package.appxmanifest** 직렬 UART 코드를 실행 하기 위해 UWP 프로젝트에서 파일:</span><span class="sxs-lookup"><span data-stu-id="d44bf-170">Note that you must add the following capability to the **Package.appxmanifest** file in your UWP project to run Serial UART code:</span></span>

<span data-ttu-id="d44bf-171">Visual Studio 2017에 매니페스트 디자이너에서 (appxmanifest 파일에 대 한 시각적 편집기) serialcommunication 기능에 영향을 주는 알려진된 버그가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d44bf-171">Visual Studio 2017 has a known bug in the Manifest Designer (the visual editor for appxmanifest files) that affects the serialcommunication capability.</span></span>  <span data-ttu-id="d44bf-172">프로그램 appxmanifest serialcommunication 기능에 추가 하는 경우 디자이너를 사용 하 여 프로그램 appxmanifest 수정 프로그램 appxmanifest (장치 xml 자식 없어집니다.) 손상 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d44bf-172">If your appxmanifest adds the serialcommunication capability, modifying your appxmanifest with the designer will corrupt your appxmanifest (the Device xml child will be lost).</span></span>  <span data-ttu-id="d44bf-173">수 해결 방법이이 문제 appxmanifest 직접 편집 하 여 프로그램 appxmanifest를 마우스 오른쪽 단추로 클릭 하 고 상황에 맞는 메뉴에서 코드 보기를 선택 하 여.</span><span class="sxs-lookup"><span data-stu-id="d44bf-173">You can workaround this problem by hand editting the appxmanifest by right-clicking your appxmanifest and selecting View Code from the context menu.</span></span>

```
  <Capabilities>
    <DeviceCapability Name="serialcommunication">
      <Device Id="any">
        <Function Type="name:serialPort" />
      </Device>
    </DeviceCapability>
  </Capabilities>
```

## <a name="i2c-bus"></a><span data-ttu-id="d44bf-174">I2C 버스</span><span class="sxs-lookup"><span data-stu-id="d44bf-174">I2C Bus</span></span>

<span data-ttu-id="d44bf-175">이 장치에서 사용할 수 있는 I2C 버스를 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="d44bf-175">Let's look at the I2C bus available on this device.</span></span>

### <a name="i2c-overview"></a><span data-ttu-id="d44bf-176">I2C 개요</span><span class="sxs-lookup"><span data-stu-id="d44bf-176">I2C Overview</span></span>

<span data-ttu-id="d44bf-177">하나의 I2C 컨트롤러가 **I2C5** 두 줄을 사용 하 여 pin 헤더에 노출 **SDA** 하 고 **SCL**합니다.</span><span class="sxs-lookup"><span data-stu-id="d44bf-177">There is one I2C controller **I2C5** exposed on the pin header with two lines **SDA** and **SCL**.</span></span> <span data-ttu-id="d44bf-178">10k&#x2126; 다음이 줄에서 내부 풀업 반대자 이미 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d44bf-178">10K&#x2126; internal pull-up resistors are already present on these lines.</span></span>

* <span data-ttu-id="d44bf-179">Pin 15 - **I2C5 SDA**</span><span class="sxs-lookup"><span data-stu-id="d44bf-179">Pin 15 - **I2C5 SDA**</span></span>
* <span data-ttu-id="d44bf-180">13-고정 **I2C5 SCL**</span><span class="sxs-lookup"><span data-stu-id="d44bf-180">Pin 13 - **I2C5 SCL**</span></span>

### <a name="i2c-sample"></a><span data-ttu-id="d44bf-181">I2C 샘플</span><span class="sxs-lookup"><span data-stu-id="d44bf-181">I2C Sample</span></span>

<span data-ttu-id="d44bf-182">초기화 아래 예에서 **I2C5** I2C 장치 주소를 사용 하 여 데이터를 쓰고 **0x40**:</span><span class="sxs-lookup"><span data-stu-id="d44bf-182">The example below initializes **I2C5** and writes data to an I2C device with address **0x40**:</span></span>

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

### <a name="i2c-issues"></a><span data-ttu-id="d44bf-183">I2C 문제</span><span class="sxs-lookup"><span data-stu-id="d44bf-183">I2C Issues</span></span>

<span data-ttu-id="d44bf-184">MinnowBoard 최대에 특정 I2C 장치와 통신 문제를 일으키는 I2C 버스를 사용 하 여 알려진된 문제가 있는 경우</span><span class="sxs-lookup"><span data-stu-id="d44bf-184">The MinnowBoard Max has a known issue with the I2C bus which causes communication problems with certain I2C devices.</span></span> <span data-ttu-id="d44bf-185">일반적으로 I2C 장치를 버스 요청 하는 동안 해당 주소를 승인 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d44bf-185">Normally, an I2C device will acknowledge its address during a bus request.</span></span>
<span data-ttu-id="d44bf-186">그러나 특정 조건에서이 승인은 MBM 수준 변환기를 통해 다시 전파할 수 실패 하 고 장치가 응답 하지 않았습니다 고 bus 트랜잭션을 취소 CPU가 생각 하는 결과적으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="d44bf-186">However, under certain conditions this acknowledge fails to propagate back through the level shifters to the MBM, and as a result the CPU thinks the device did not respond and cancels the bus transaction.</span></span>
<span data-ttu-id="d44bf-187">문제에 관련 된 것으로 보입니다 합니다 [TXS0104E](http://www.ti.com/product/txs0104e) 줄에서 전압 급증으로 인해 중간을 트리거할 수 있는 IO 핀에 변환기 수준입니다.</span><span class="sxs-lookup"><span data-stu-id="d44bf-187">The issue seems to be related to the [TXS0104E](http://www.ti.com/product/txs0104e) level shifters on the IO pins, which can trigger prematurely due to voltage spikes on the line.</span></span>
<span data-ttu-id="d44bf-188">현재 해결 방법은 급증을 표시 하지 않을 수 있는 I2C SCK 줄을 사용 하 여 계열의 100 옴 저항기를 삽입 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="d44bf-188">The current workaround is to insert a 100 ohm resistor in series with the I2C SCK line, which helps suppress spikes.</span></span> <span data-ttu-id="d44bf-189">모든 장치에는 영향을이 해결 방법은 이므로 필요한 경우 문제가 버스 응답 합니다.</span><span class="sxs-lookup"><span data-stu-id="d44bf-189">Not all devices are affected, so this workaround is only required if you are having trouble getting a bus response.</span></span> <span data-ttu-id="d44bf-190">이 해결 방법은 필요으로 알려진 하나의 장치는 HTU21D는입니다.</span><span class="sxs-lookup"><span data-stu-id="d44bf-190">One device that is known to require this workaround is the HTU21D.</span></span>

## <a name="spi-bus"></a><span data-ttu-id="d44bf-191">SPI 버스</span><span class="sxs-lookup"><span data-stu-id="d44bf-191">SPI Bus</span></span>

<span data-ttu-id="d44bf-192">이 장치에서 사용할 수 있는 SPI 버스를 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="d44bf-192">Let's look at the SPI bus available on this device.</span></span>

### <a name="spi-overview"></a><span data-ttu-id="d44bf-193">SPI 개요</span><span class="sxs-lookup"><span data-stu-id="d44bf-193">SPI Overview</span></span>

<span data-ttu-id="d44bf-194">하나의 SPI 컨트롤러가 **SPI0** 는 MBM에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d44bf-194">There is one SPI controller **SPI0** available on the MBM:</span></span>

* <span data-ttu-id="d44bf-195">9-고정 **SPI0 MOSI**</span><span class="sxs-lookup"><span data-stu-id="d44bf-195">Pin 9 - **SPI0 MOSI**</span></span>
* <span data-ttu-id="d44bf-196">7-고정 **SPI0 MISO**</span><span class="sxs-lookup"><span data-stu-id="d44bf-196">Pin 7 - **SPI0 MISO**</span></span>
* <span data-ttu-id="d44bf-197">11-고정 **SPI0 SCLK**</span><span class="sxs-lookup"><span data-stu-id="d44bf-197">Pin 11 - **SPI0 SCLK**</span></span>
* <span data-ttu-id="d44bf-198">5-고정 **SPI0 CS0**</span><span class="sxs-lookup"><span data-stu-id="d44bf-198">Pin 5 - **SPI0 CS0**</span></span>


### <a name="spi-sample"></a><span data-ttu-id="d44bf-199">SPI 샘플</span><span class="sxs-lookup"><span data-stu-id="d44bf-199">SPI Sample</span></span>

<span data-ttu-id="d44bf-200">SPI를 수행 하는 방법을 예로 버스에 작성할 **SPI0** 아래에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d44bf-200">An example on how to perform a SPI write on bus **SPI0** is shown below:</span></span>

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

