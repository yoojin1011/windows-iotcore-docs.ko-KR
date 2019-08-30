---
title: Dragonboard Pin 매핑
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Dragonboard에 대 한 pin 매핑 기능에 대해 알아봅니다.
keywords: windows iot, Dragonboard, pin 매핑, GPIO
ms.openlocfilehash: f6df962c6d05aa912013f8f0819c0789bfc393ce
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "60167693"
---
# <a name="dragonboard-pin-mappings"></a><span data-ttu-id="6b1b3-104">Dragonboard Pin 매핑</span><span class="sxs-lookup"><span data-stu-id="6b1b3-104">Dragonboard Pin Mappings</span></span>

![Dragonboard Pin 헤더](../../media/PinMappingsDB/DB_Pinout.png)

<span data-ttu-id="6b1b3-106">Dragonboard에 대 한 하드웨어 인터페이스는 보드의 40 핀 헤더를 통해 노출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6b1b3-106">Hardware interfaces for the Dragonboard are exposed through the 40-pin header on the board.</span></span> <span data-ttu-id="6b1b3-107">기능은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="6b1b3-107">Functionality includes:</span></span>

* <span data-ttu-id="6b1b3-108">**11x** -GPIO 핀</span><span class="sxs-lookup"><span data-stu-id="6b1b3-108">**11x** - GPIO pins</span></span>
* <span data-ttu-id="6b1b3-109">**2x** -직렬 uarts</span><span class="sxs-lookup"><span data-stu-id="6b1b3-109">**2x** - Serial UARTs</span></span>
* <span data-ttu-id="6b1b3-110">**1x** -SPI 버스</span><span class="sxs-lookup"><span data-stu-id="6b1b3-110">**1x** - SPI bus</span></span>
* <span data-ttu-id="6b1b3-111">**2** -I2C 버스</span><span class="sxs-lookup"><span data-stu-id="6b1b3-111">**2x** - I2C bus</span></span>
* <span data-ttu-id="6b1b3-112">**1x** -5v 전원 pin</span><span class="sxs-lookup"><span data-stu-id="6b1b3-112">**1x** - 5V power pin</span></span>
* <span data-ttu-id="6b1b3-113">**1x** -1.8 v 전원 pin</span><span class="sxs-lookup"><span data-stu-id="6b1b3-113">**1x** - 1.8V power pin</span></span>
* <span data-ttu-id="6b1b3-114">**4x** -접지 핀</span><span class="sxs-lookup"><span data-stu-id="6b1b3-114">**4x** - Ground pins</span></span>

<span data-ttu-id="6b1b3-115">Dragonboard에서는 모든 IO 핀에서 1.8 V 논리 수준을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b1b3-115">Note that the Dragonboard uses 1.8V logic levels on all IO pins.</span></span> 

## <a name="gpio-pins"></a><span data-ttu-id="6b1b3-116">GPIO 핀</span><span class="sxs-lookup"><span data-stu-id="6b1b3-116">GPIO Pins</span></span>

<span data-ttu-id="6b1b3-117">이 장치에서 사용 가능한 GPIO를 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="6b1b3-117">Let's look at the GPIO available on this device.</span></span>

### <a name="gpio-pin-table"></a><span data-ttu-id="6b1b3-118">GPIO 고정 테이블</span><span class="sxs-lookup"><span data-stu-id="6b1b3-118">GPIO Pin Table</span></span>

<span data-ttu-id="6b1b3-119">다음 GPIO pin은 Api를 통해 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b1b3-119">The following GPIO pins are accessible through APIs:</span></span>

> | <span data-ttu-id="6b1b3-120">GPIO #</span><span class="sxs-lookup"><span data-stu-id="6b1b3-120">GPIO#</span></span> | <span data-ttu-id="6b1b3-121">헤더 Pin</span><span class="sxs-lookup"><span data-stu-id="6b1b3-121">Header Pin</span></span>         |
> |-------|--------------------|
> | <span data-ttu-id="6b1b3-122">36</span><span class="sxs-lookup"><span data-stu-id="6b1b3-122">36</span></span>    | <span data-ttu-id="6b1b3-123">23</span><span class="sxs-lookup"><span data-stu-id="6b1b3-123">23</span></span>                 |
> | <span data-ttu-id="6b1b3-124">12</span><span class="sxs-lookup"><span data-stu-id="6b1b3-124">12</span></span>    | <span data-ttu-id="6b1b3-125">24</span><span class="sxs-lookup"><span data-stu-id="6b1b3-125">24</span></span>                 |
> | <span data-ttu-id="6b1b3-126">13</span><span class="sxs-lookup"><span data-stu-id="6b1b3-126">13</span></span>    | <span data-ttu-id="6b1b3-127">25</span><span class="sxs-lookup"><span data-stu-id="6b1b3-127">25</span></span>                 |
> | <span data-ttu-id="6b1b3-128">69</span><span class="sxs-lookup"><span data-stu-id="6b1b3-128">69</span></span>    | <span data-ttu-id="6b1b3-129">26</span><span class="sxs-lookup"><span data-stu-id="6b1b3-129">26</span></span>                 |
> | <span data-ttu-id="6b1b3-130">115</span><span class="sxs-lookup"><span data-stu-id="6b1b3-130">115</span></span>   | <span data-ttu-id="6b1b3-131">27</span><span class="sxs-lookup"><span data-stu-id="6b1b3-131">27</span></span>                 |
> | <span data-ttu-id="6b1b3-132">24</span><span class="sxs-lookup"><span data-stu-id="6b1b3-132">24</span></span>    | <span data-ttu-id="6b1b3-133">29</span><span class="sxs-lookup"><span data-stu-id="6b1b3-133">29</span></span>                 |
> | <span data-ttu-id="6b1b3-134">25</span><span class="sxs-lookup"><span data-stu-id="6b1b3-134">25</span></span>    | <span data-ttu-id="6b1b3-135">30</span><span class="sxs-lookup"><span data-stu-id="6b1b3-135">30</span></span>                 |
> | <span data-ttu-id="6b1b3-136">35</span><span class="sxs-lookup"><span data-stu-id="6b1b3-136">35</span></span>    | <span data-ttu-id="6b1b3-137">31</span><span class="sxs-lookup"><span data-stu-id="6b1b3-137">31</span></span>                 |
> | <span data-ttu-id="6b1b3-138">34</span><span class="sxs-lookup"><span data-stu-id="6b1b3-138">34</span></span>    | <span data-ttu-id="6b1b3-139">32</span><span class="sxs-lookup"><span data-stu-id="6b1b3-139">32</span></span>                 |
> | <span data-ttu-id="6b1b3-140">28</span><span class="sxs-lookup"><span data-stu-id="6b1b3-140">28</span></span>    | <span data-ttu-id="6b1b3-141">33</span><span class="sxs-lookup"><span data-stu-id="6b1b3-141">33</span></span>                 |
> | <span data-ttu-id="6b1b3-142">33</span><span class="sxs-lookup"><span data-stu-id="6b1b3-142">33</span></span>    | <span data-ttu-id="6b1b3-143">34</span><span class="sxs-lookup"><span data-stu-id="6b1b3-143">34</span></span>                 |
> | <span data-ttu-id="6b1b3-144">21</span><span class="sxs-lookup"><span data-stu-id="6b1b3-144">21</span></span>    | <span data-ttu-id="6b1b3-145">사용자 LED 1</span><span class="sxs-lookup"><span data-stu-id="6b1b3-145">User LED 1</span></span>         | 
> | <span data-ttu-id="6b1b3-146">120</span><span class="sxs-lookup"><span data-stu-id="6b1b3-146">120</span></span>   | <span data-ttu-id="6b1b3-147">사용자 LED 2</span><span class="sxs-lookup"><span data-stu-id="6b1b3-147">User LED 2</span></span>         |         


<span data-ttu-id="6b1b3-148">예를 들어 다음 코드는 **GPIO 35** 을 출력으로 열고 pin에 디지털 '**1**'을 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b1b3-148">As an example, the following code opens **GPIO 35** as an output and writes a digital '**1**' out on the pin:</span></span>
         
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

### <a name="gpio-issues"></a><span data-ttu-id="6b1b3-149">GPIO 문제</span><span class="sxs-lookup"><span data-stu-id="6b1b3-149">GPIO Issues</span></span>

* <span data-ttu-id="6b1b3-150">GPIO 24에서는 출력이 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6b1b3-150">Output doesn't work on GPIO 24.</span></span> <span data-ttu-id="6b1b3-151">입력이 제대로 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b1b3-151">Input works fine.</span></span>
* <span data-ttu-id="6b1b3-152">Pin은 부팅 시 InputPullDown로 구성 되지만 처음 열릴 때 입력 (부동)으로 변경 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6b1b3-152">Pins are configured as InputPullDown at boot, but will change to Input (floating) the first time they are opened</span></span>
* <span data-ttu-id="6b1b3-153">닫히면 pin은 기본 상태로 되돌아가지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6b1b3-153">Pins do not revert to their default state when closed</span></span>
* <span data-ttu-id="6b1b3-154">여러 핀에서 인터럽트를 사용 하는 경우 의사 인터럽트가 표시 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b1b3-154">Spurious interrupts may be seen when interrupts are enabled on multiple pins</span></span>


## <a name="serial-uart"></a><span data-ttu-id="6b1b3-155">직렬 UART</span><span class="sxs-lookup"><span data-stu-id="6b1b3-155">Serial UART</span></span>

<span data-ttu-id="6b1b3-156">Dragonboard **UART0** 및 **UART1** 에는 두 개의 직렬 uarts를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b1b3-156">There are two Serial UARTS available on the Dragonboard **UART0** and **UART1**</span></span>

<span data-ttu-id="6b1b3-157">**UART0** 에는 표준 **UART0 TX** 및 **UART0 RX** 회선이 있으며,이는 CTS 및 **UART0 RTS**를 **UART0** 하는 흐름 제어 신호와 함께 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b1b3-157">**UART0** has the standard **UART0 TX** and **UART0 RX** lines, along with flow control signals **UART0 CTS** and **UART0 RTS**.</span></span>

* <span data-ttu-id="6b1b3-158">핀 5- **UART0 TX**</span><span class="sxs-lookup"><span data-stu-id="6b1b3-158">Pin 5  - **UART0 TX**</span></span>
* <span data-ttu-id="6b1b3-159">Pin 7- **UART0 RX**</span><span class="sxs-lookup"><span data-stu-id="6b1b3-159">Pin 7  - **UART0 RX**</span></span>
* <span data-ttu-id="6b1b3-160">Pin 3- **UART0 CTS**</span><span class="sxs-lookup"><span data-stu-id="6b1b3-160">Pin 3 - **UART0 CTS**</span></span>
* <span data-ttu-id="6b1b3-161">Pin 9- **UART0 RTS**</span><span class="sxs-lookup"><span data-stu-id="6b1b3-161">Pin 9 - **UART0 RTS**</span></span>


<span data-ttu-id="6b1b3-162">**UART1** 에는 **UART1 TX** 및 **UART1 RX** 줄만 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6b1b3-162">**UART1** includes just the **UART1 TX** and **UART1 RX** lines.</span></span>

* <span data-ttu-id="6b1b3-163">핀 11- **UART1 TX**</span><span class="sxs-lookup"><span data-stu-id="6b1b3-163">Pin 11  - **UART1 TX**</span></span>
* <span data-ttu-id="6b1b3-164">Pin 13- **UART1 RX**</span><span class="sxs-lookup"><span data-stu-id="6b1b3-164">Pin 13  - **UART1 RX**</span></span>

<span data-ttu-id="6b1b3-165">아래 예제에서는 **UART1** 를 초기화 하 고 쓰기 후에 읽기를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b1b3-165">The example below initializes **UART1** and performs a write followed by a read:</span></span>

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
> <span data-ttu-id="6b1b3-166">Visual Studio 2017에는 매니페스트 디자이너 (appxmanifest.xml 파일용 시각적 편집기)에서 serialcommunication 기능에 영향을 주는 알려진 버그가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b1b3-166">Visual Studio 2017 has a known bug in the Manifest Designer (the visual editor for appxmanifest files) that affects the serialcommunication capability.</span></span>  <span data-ttu-id="6b1b3-167">Appxmanifest.xml가 serialcommunication 기능을 추가 하는 경우 디자이너를 사용 하 여 appxmanifest.xml를 수정 하면 appxmanifest.xml가 손상 됩니다 (장치 xml 자식은 손실 됨).</span><span class="sxs-lookup"><span data-stu-id="6b1b3-167">If your appxmanifest adds the serialcommunication capability, modifying your appxmanifest with the designer will corrupt your appxmanifest (the Device xml child will be lost).</span></span>  <span data-ttu-id="6b1b3-168">Appxmanifest.xml를 마우스 오른쪽 단추로 클릭 하 고 상황에 맞는 메뉴에서 코드 보기를 선택 하 여 appxmanifest.xml를 직접 편집이 문제를 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b1b3-168">You can workaround this problem by hand editting the appxmanifest by right-clicking your appxmanifest and selecting View Code from the context menu.</span></span>

<span data-ttu-id="6b1b3-169">다음 기능을 UWP 프로젝트의 **appxmanifest.xml** 파일에 추가 하 여 직렬 UART 코드를 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b1b3-169">You must add the following capability to the **Package.appxmanifest** file in your UWP project to run Serial UART code:</span></span>

```xml
  <Capabilities>
    <DeviceCapability Name="serialcommunication">
      <Device Id="any">
        <Function Type="name:serialPort" />
      </Device>
    </DeviceCapability>
  </Capabilities>
```

## <a name="i2c-bus"></a><span data-ttu-id="6b1b3-170">I2C 버스</span><span class="sxs-lookup"><span data-stu-id="6b1b3-170">I2C Bus</span></span>

<span data-ttu-id="6b1b3-171">이 장치에서 사용할 수 있는 I2C 버스를 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="6b1b3-171">Let's look at the I2C busses available on this device.</span></span>

### <a name="i2c-pins"></a><span data-ttu-id="6b1b3-172">I2C 핀</span><span class="sxs-lookup"><span data-stu-id="6b1b3-172">I2C Pins</span></span>

<span data-ttu-id="6b1b3-173">**I2C0** 는 두 줄 **Sda** 와 **SCL** 을 사용 하 여 pin 헤더에 노출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6b1b3-173">**I2C0** exposed on the pin header with two lines **SDA** and **SCL**</span></span>

* <span data-ttu-id="6b1b3-174">Pin 17- **I2C0 SDA**</span><span class="sxs-lookup"><span data-stu-id="6b1b3-174">Pin 17 - **I2C0 SDA**</span></span>
* <span data-ttu-id="6b1b3-175">Pin 15- **I2C0 SCL**</span><span class="sxs-lookup"><span data-stu-id="6b1b3-175">Pin 15 - **I2C0 SCL**</span></span>

<span data-ttu-id="6b1b3-176">**I2C1** 는 두 줄 **Sda** 와 **SCL** 을 사용 하 여 pin 헤더에 노출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6b1b3-176">**I2C1** exposed on the pin header with two lines **SDA** and **SCL**</span></span>

* <span data-ttu-id="6b1b3-177">핀 21- **I2C1 SDA**</span><span class="sxs-lookup"><span data-stu-id="6b1b3-177">Pin 21 - **I2C1 SDA**</span></span>
* <span data-ttu-id="6b1b3-178">Pin 19- **I2C1 SCL**</span><span class="sxs-lookup"><span data-stu-id="6b1b3-178">Pin 19 - **I2C1 SCL**</span></span>

### <a name="i2c-sample"></a><span data-ttu-id="6b1b3-179">I2C 샘플</span><span class="sxs-lookup"><span data-stu-id="6b1b3-179">I2C Sample</span></span>

<span data-ttu-id="6b1b3-180">아래 예제에서는 **I2C0** 를 초기화 하 고 주소가 **0x40**인 I2C 장치에 데이터를 씁니다.</span><span class="sxs-lookup"><span data-stu-id="6b1b3-180">The example below initializes **I2C0** and writes data to an I2C device with address **0x40**:</span></span>

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


## <a name="spi-bus"></a><span data-ttu-id="6b1b3-181">SPI 버스</span><span class="sxs-lookup"><span data-stu-id="6b1b3-181">SPI Bus</span></span>

<span data-ttu-id="6b1b3-182">이 장치에서 사용할 수 있는 SPI bus를 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="6b1b3-182">Let's look at the SPI bus available on this device.</span></span>

### <a name="spi-pins"></a><span data-ttu-id="6b1b3-183">SPI Pin</span><span class="sxs-lookup"><span data-stu-id="6b1b3-183">SPI Pins</span></span>

<span data-ttu-id="6b1b3-184">DB에서 사용할 수 있는 SPI 컨트롤러 **SPI0** 하나 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b1b3-184">There is one SPI controller **SPI0** available on the DB</span></span>

* <span data-ttu-id="6b1b3-185">Pin 10- **SPI0 miso**</span><span class="sxs-lookup"><span data-stu-id="6b1b3-185">Pin 10 - **SPI0 MISO**</span></span>
* <span data-ttu-id="6b1b3-186">Pin 14- **SPI0 MOSI**</span><span class="sxs-lookup"><span data-stu-id="6b1b3-186">Pin 14 - **SPI0 MOSI**</span></span>
* <span data-ttu-id="6b1b3-187">Pin 8- **SPI0 SCLK**</span><span class="sxs-lookup"><span data-stu-id="6b1b3-187">Pin 8 - **SPI0 SCLK**</span></span>
* <span data-ttu-id="6b1b3-188">Pin 12- **SPI0 CS0**</span><span class="sxs-lookup"><span data-stu-id="6b1b3-188">Pin 12 - **SPI0 CS0**</span></span>

### <a name="spi-issues"></a><span data-ttu-id="6b1b3-189">SPI 문제</span><span class="sxs-lookup"><span data-stu-id="6b1b3-189">SPI Issues</span></span>

<span data-ttu-id="6b1b3-190">SPI clock은 4.8 mhz에서 고정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6b1b3-190">The SPI clock is fixed at 4.8mhz.</span></span> <span data-ttu-id="6b1b3-191">요청 된 SPI clock은 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6b1b3-191">The requested SPI clock will be ignored.</span></span> 


### <a name="spi-sample"></a><span data-ttu-id="6b1b3-192">SPI 샘플</span><span class="sxs-lookup"><span data-stu-id="6b1b3-192">SPI Sample</span></span>

<span data-ttu-id="6b1b3-193">다음은 bus **SPI0** 에서 SPI 쓰기를 수행 하는 방법에 대 한 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="6b1b3-193">An example on how to perform a SPI write on bus **SPI0** is shown below:</span></span>

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
