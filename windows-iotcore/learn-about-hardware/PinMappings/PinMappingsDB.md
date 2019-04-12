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
# <a name="dragonboard-pin-mappings"></a><span data-ttu-id="94877-104">Dragonboard 핀 매핑</span><span class="sxs-lookup"><span data-stu-id="94877-104">Dragonboard Pin Mappings</span></span>

![Dragonboard Pin 헤더](../../media/PinMappingsDB/DB_Pinout.png)

<span data-ttu-id="94877-106">하드웨어 인터페이스는 Dragonboard 보드의 40 핀 헤더를 통해 노출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="94877-106">Hardware interfaces for the Dragonboard are exposed through the 40-pin header on the board.</span></span> <span data-ttu-id="94877-107">기능은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="94877-107">Functionality includes:</span></span>

* <span data-ttu-id="94877-108">**11 배** -GPIO pin</span><span class="sxs-lookup"><span data-stu-id="94877-108">**11x** - GPIO pins</span></span>
* <span data-ttu-id="94877-109">**2 x** -직렬 UARTs</span><span class="sxs-lookup"><span data-stu-id="94877-109">**2x** - Serial UARTs</span></span>
* <span data-ttu-id="94877-110">**1 x** -SPI 버스</span><span class="sxs-lookup"><span data-stu-id="94877-110">**1x** - SPI bus</span></span>
* <span data-ttu-id="94877-111">**2 x** -I2C 버스</span><span class="sxs-lookup"><span data-stu-id="94877-111">**2x** - I2C bus</span></span>
* <span data-ttu-id="94877-112">**1 x** -5V power pin</span><span class="sxs-lookup"><span data-stu-id="94877-112">**1x** - 5V power pin</span></span>
* <span data-ttu-id="94877-113">**1 x** -1.8 v power pin</span><span class="sxs-lookup"><span data-stu-id="94877-113">**1x** - 1.8V power pin</span></span>
* <span data-ttu-id="94877-114">**4 x** -pin 방지 매트를</span><span class="sxs-lookup"><span data-stu-id="94877-114">**4x** - Ground pins</span></span>

<span data-ttu-id="94877-115">참고는 Dragonboard 1.8 v는 모든 IO 핀에 논리 수준입니다.</span><span class="sxs-lookup"><span data-stu-id="94877-115">Note that the Dragonboard uses 1.8V logic levels on all IO pins.</span></span> 

## <a name="gpio-pins"></a><span data-ttu-id="94877-116">GPIO Pin</span><span class="sxs-lookup"><span data-stu-id="94877-116">GPIO Pins</span></span>

<span data-ttu-id="94877-117">이 장치에서 사용 가능한 GPIO를 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="94877-117">Let's look at the GPIO available on this device.</span></span>

### <a name="gpio-pin-table"></a><span data-ttu-id="94877-118">GPIO Pin 테이블</span><span class="sxs-lookup"><span data-stu-id="94877-118">GPIO Pin Table</span></span>

<span data-ttu-id="94877-119">다음 GPIO 핀은 Api를 통해 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="94877-119">The following GPIO pins are accessible through APIs:</span></span>

> | <span data-ttu-id="94877-120">GPIO#</span><span class="sxs-lookup"><span data-stu-id="94877-120">GPIO#</span></span> | <span data-ttu-id="94877-121">헤더 Pin</span><span class="sxs-lookup"><span data-stu-id="94877-121">Header Pin</span></span>         |
> |-------|--------------------|
> | <span data-ttu-id="94877-122">36</span><span class="sxs-lookup"><span data-stu-id="94877-122">36</span></span>    | <span data-ttu-id="94877-123">23</span><span class="sxs-lookup"><span data-stu-id="94877-123">23</span></span>                 |
> | <span data-ttu-id="94877-124">12</span><span class="sxs-lookup"><span data-stu-id="94877-124">12</span></span>    | <span data-ttu-id="94877-125">24</span><span class="sxs-lookup"><span data-stu-id="94877-125">24</span></span>                 |
> | <span data-ttu-id="94877-126">13</span><span class="sxs-lookup"><span data-stu-id="94877-126">13</span></span>    | <span data-ttu-id="94877-127">25</span><span class="sxs-lookup"><span data-stu-id="94877-127">25</span></span>                 |
> | <span data-ttu-id="94877-128">69</span><span class="sxs-lookup"><span data-stu-id="94877-128">69</span></span>    | <span data-ttu-id="94877-129">26</span><span class="sxs-lookup"><span data-stu-id="94877-129">26</span></span>                 |
> | <span data-ttu-id="94877-130">115</span><span class="sxs-lookup"><span data-stu-id="94877-130">115</span></span>   | <span data-ttu-id="94877-131">27</span><span class="sxs-lookup"><span data-stu-id="94877-131">27</span></span>                 |
> | <span data-ttu-id="94877-132">24</span><span class="sxs-lookup"><span data-stu-id="94877-132">24</span></span>    | <span data-ttu-id="94877-133">29</span><span class="sxs-lookup"><span data-stu-id="94877-133">29</span></span>                 |
> | <span data-ttu-id="94877-134">25</span><span class="sxs-lookup"><span data-stu-id="94877-134">25</span></span>    | <span data-ttu-id="94877-135">30</span><span class="sxs-lookup"><span data-stu-id="94877-135">30</span></span>                 |
> | <span data-ttu-id="94877-136">35</span><span class="sxs-lookup"><span data-stu-id="94877-136">35</span></span>    | <span data-ttu-id="94877-137">31</span><span class="sxs-lookup"><span data-stu-id="94877-137">31</span></span>                 |
> | <span data-ttu-id="94877-138">34</span><span class="sxs-lookup"><span data-stu-id="94877-138">34</span></span>    | <span data-ttu-id="94877-139">32</span><span class="sxs-lookup"><span data-stu-id="94877-139">32</span></span>                 |
> | <span data-ttu-id="94877-140">28</span><span class="sxs-lookup"><span data-stu-id="94877-140">28</span></span>    | <span data-ttu-id="94877-141">33</span><span class="sxs-lookup"><span data-stu-id="94877-141">33</span></span>                 |
> | <span data-ttu-id="94877-142">33</span><span class="sxs-lookup"><span data-stu-id="94877-142">33</span></span>    | <span data-ttu-id="94877-143">34</span><span class="sxs-lookup"><span data-stu-id="94877-143">34</span></span>                 |
> | <span data-ttu-id="94877-144">21</span><span class="sxs-lookup"><span data-stu-id="94877-144">21</span></span>    | <span data-ttu-id="94877-145">사용자 1 LED</span><span class="sxs-lookup"><span data-stu-id="94877-145">User LED 1</span></span>         | 
> | <span data-ttu-id="94877-146">120</span><span class="sxs-lookup"><span data-stu-id="94877-146">120</span></span>   | <span data-ttu-id="94877-147">사용자 led가 2</span><span class="sxs-lookup"><span data-stu-id="94877-147">User LED 2</span></span>         |         


<span data-ttu-id="94877-148">예를 들어 다음 코드 열립니다 **GPIO 35** 출력으로 디지털 쓰고 '**1**' 핀 아웃 합니다.</span><span class="sxs-lookup"><span data-stu-id="94877-148">As an example, the following code opens **GPIO 35** as an output and writes a digital '**1**' out on the pin:</span></span>
         
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

### <a name="gpio-issues"></a><span data-ttu-id="94877-149">GPIO 문제</span><span class="sxs-lookup"><span data-stu-id="94877-149">GPIO Issues</span></span>

* <span data-ttu-id="94877-150">출력은 GPIO 24에서 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="94877-150">Output doesn't work on GPIO 24.</span></span> <span data-ttu-id="94877-151">입력이 제대로 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="94877-151">Input works fine.</span></span>
* <span data-ttu-id="94877-152">Pin, 부팅 시 InputPullDown으로 구성 되어 있지만 입력 (부동)로 변경 됩니다 처음 열 때</span><span class="sxs-lookup"><span data-stu-id="94877-152">Pins are configured as InputPullDown at boot, but will change to Input (floating) the first time they are opened</span></span>
* <span data-ttu-id="94877-153">Pin을 닫을 때 기본 상태로 전환 되지 않고 수행</span><span class="sxs-lookup"><span data-stu-id="94877-153">Pins do not revert to their default state when closed</span></span>
* <span data-ttu-id="94877-154">의사 인터럽트 인터럽트 다중 핀에 설정 된 경우 표시 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="94877-154">Spurious interrupts may be seen when interrupts are enabled on multiple pins</span></span>


## <a name="serial-uart"></a><span data-ttu-id="94877-155">직렬 UART</span><span class="sxs-lookup"><span data-stu-id="94877-155">Serial UART</span></span>

<span data-ttu-id="94877-156">Dragonboard에서 두 직렬 UARTS 됩니다 **UART0** 고 **UART1**</span><span class="sxs-lookup"><span data-stu-id="94877-156">There are two Serial UARTS available on the Dragonboard **UART0** and **UART1**</span></span>

<span data-ttu-id="94877-157">**UART0** 에 표준 **UART0 TX** 하 고 **UART0 RX** flow와 함께 줄 제어 신호 **UART0 CTS** 및 **UART0 RTS**.</span><span class="sxs-lookup"><span data-stu-id="94877-157">**UART0** has the standard **UART0 TX** and **UART0 RX** lines, along with flow control signals **UART0 CTS** and **UART0 RTS**.</span></span>

* <span data-ttu-id="94877-158">5-고정 **UART0 TX**</span><span class="sxs-lookup"><span data-stu-id="94877-158">Pin 5  - **UART0 TX**</span></span>
* <span data-ttu-id="94877-159">7-고정 **UART0 RX**</span><span class="sxs-lookup"><span data-stu-id="94877-159">Pin 7  - **UART0 RX**</span></span>
* <span data-ttu-id="94877-160">3-고정 **UART0 CTS**</span><span class="sxs-lookup"><span data-stu-id="94877-160">Pin 3 - **UART0 CTS**</span></span>
* <span data-ttu-id="94877-161">9-고정 **UART0 RTS**</span><span class="sxs-lookup"><span data-stu-id="94877-161">Pin 9 - **UART0 RTS**</span></span>


<span data-ttu-id="94877-162">**UART1** 포함 요소만 **UART1 TX** 하 고 **UART1 RX** 줄.</span><span class="sxs-lookup"><span data-stu-id="94877-162">**UART1** includes just the **UART1 TX** and **UART1 RX** lines.</span></span>

* <span data-ttu-id="94877-163">11-고정 **UART1 TX**</span><span class="sxs-lookup"><span data-stu-id="94877-163">Pin 11  - **UART1 TX**</span></span>
* <span data-ttu-id="94877-164">13-고정 **UART1 RX**</span><span class="sxs-lookup"><span data-stu-id="94877-164">Pin 13  - **UART1 RX**</span></span>

<span data-ttu-id="94877-165">초기화 아래 예에서 **UART1** 읽기 뒤 쓰기를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="94877-165">The example below initializes **UART1** and performs a write followed by a read:</span></span>

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
> <span data-ttu-id="94877-166">Visual Studio 2017에 매니페스트 디자이너에서 (appxmanifest 파일에 대 한 시각적 편집기) serialcommunication 기능에 영향을 주는 알려진된 버그가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="94877-166">Visual Studio 2017 has a known bug in the Manifest Designer (the visual editor for appxmanifest files) that affects the serialcommunication capability.</span></span>  <span data-ttu-id="94877-167">프로그램 appxmanifest serialcommunication 기능에 추가 하는 경우 디자이너를 사용 하 여 프로그램 appxmanifest 수정 프로그램 appxmanifest (장치 xml 자식 없어집니다.) 손상 됩니다.</span><span class="sxs-lookup"><span data-stu-id="94877-167">If your appxmanifest adds the serialcommunication capability, modifying your appxmanifest with the designer will corrupt your appxmanifest (the Device xml child will be lost).</span></span>  <span data-ttu-id="94877-168">수 해결 방법이이 문제 appxmanifest 직접 편집 하 여 프로그램 appxmanifest를 마우스 오른쪽 단추로 클릭 하 고 상황에 맞는 메뉴에서 코드 보기를 선택 하 여.</span><span class="sxs-lookup"><span data-stu-id="94877-168">You can workaround this problem by hand editting the appxmanifest by right-clicking your appxmanifest and selecting View Code from the context menu.</span></span>

<span data-ttu-id="94877-169">다음 기능을 추가 해야 합니다 **Package.appxmanifest** 직렬 UART 코드를 실행 하기 위해 UWP 프로젝트에서 파일:</span><span class="sxs-lookup"><span data-stu-id="94877-169">You must add the following capability to the **Package.appxmanifest** file in your UWP project to run Serial UART code:</span></span>

```xml
  <Capabilities>
    <DeviceCapability Name="serialcommunication">
      <Device Id="any">
        <Function Type="name:serialPort" />
      </Device>
    </DeviceCapability>
  </Capabilities>
```

## <a name="i2c-bus"></a><span data-ttu-id="94877-170">I2C 버스</span><span class="sxs-lookup"><span data-stu-id="94877-170">I2C Bus</span></span>

<span data-ttu-id="94877-171">이 장치에서 사용할 수 있는 I2C 버스를 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="94877-171">Let's look at the I2C busses available on this device.</span></span>

### <a name="i2c-pins"></a><span data-ttu-id="94877-172">I2C Pin</span><span class="sxs-lookup"><span data-stu-id="94877-172">I2C Pins</span></span>

<span data-ttu-id="94877-173">**I2C0** 두 줄을 사용 하 여 pin 헤더에 노출 **SDA** 고 **SCL**</span><span class="sxs-lookup"><span data-stu-id="94877-173">**I2C0** exposed on the pin header with two lines **SDA** and **SCL**</span></span>

* <span data-ttu-id="94877-174">17-고정 **I2C0 SDA**</span><span class="sxs-lookup"><span data-stu-id="94877-174">Pin 17 - **I2C0 SDA**</span></span>
* <span data-ttu-id="94877-175">15-고정 **I2C0 SCL**</span><span class="sxs-lookup"><span data-stu-id="94877-175">Pin 15 - **I2C0 SCL**</span></span>

<span data-ttu-id="94877-176">**I2C1** 두 줄을 사용 하 여 pin 헤더에 노출 **SDA** 고 **SCL**</span><span class="sxs-lookup"><span data-stu-id="94877-176">**I2C1** exposed on the pin header with two lines **SDA** and **SCL**</span></span>

* <span data-ttu-id="94877-177">Pin 21 - **I2C1 SDA**</span><span class="sxs-lookup"><span data-stu-id="94877-177">Pin 21 - **I2C1 SDA**</span></span>
* <span data-ttu-id="94877-178">19-고정 **I2C1 SCL**</span><span class="sxs-lookup"><span data-stu-id="94877-178">Pin 19 - **I2C1 SCL**</span></span>

### <a name="i2c-sample"></a><span data-ttu-id="94877-179">I2C 샘플</span><span class="sxs-lookup"><span data-stu-id="94877-179">I2C Sample</span></span>

<span data-ttu-id="94877-180">초기화 아래 예에서 **I2C0** I2C 장치 주소를 사용 하 여 데이터를 쓰고 **0x40**:</span><span class="sxs-lookup"><span data-stu-id="94877-180">The example below initializes **I2C0** and writes data to an I2C device with address **0x40**:</span></span>

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


## <a name="spi-bus"></a><span data-ttu-id="94877-181">SPI 버스</span><span class="sxs-lookup"><span data-stu-id="94877-181">SPI Bus</span></span>

<span data-ttu-id="94877-182">이 장치에서 사용할 수 있는 SPI 버스를 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="94877-182">Let's look at the SPI bus available on this device.</span></span>

### <a name="spi-pins"></a><span data-ttu-id="94877-183">SPI Pin</span><span class="sxs-lookup"><span data-stu-id="94877-183">SPI Pins</span></span>

<span data-ttu-id="94877-184">하나의 SPI 컨트롤러가 **SPI0** DB에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="94877-184">There is one SPI controller **SPI0** available on the DB</span></span>

* <span data-ttu-id="94877-185">고정 10- **SPI0 MISO**</span><span class="sxs-lookup"><span data-stu-id="94877-185">Pin 10 - **SPI0 MISO**</span></span>
* <span data-ttu-id="94877-186">14-고정 **SPI0 MOSI**</span><span class="sxs-lookup"><span data-stu-id="94877-186">Pin 14 - **SPI0 MOSI**</span></span>
* <span data-ttu-id="94877-187">8-고정 **SPI0 SCLK**</span><span class="sxs-lookup"><span data-stu-id="94877-187">Pin 8 - **SPI0 SCLK**</span></span>
* <span data-ttu-id="94877-188">12-고정 **SPI0 CS0**</span><span class="sxs-lookup"><span data-stu-id="94877-188">Pin 12 - **SPI0 CS0**</span></span>

### <a name="spi-issues"></a><span data-ttu-id="94877-189">SPI 문제</span><span class="sxs-lookup"><span data-stu-id="94877-189">SPI Issues</span></span>

<span data-ttu-id="94877-190">SPI 클록 4.8 mhz에 고정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="94877-190">The SPI clock is fixed at 4.8mhz.</span></span> <span data-ttu-id="94877-191">요청 된 SPI 클록은 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="94877-191">The requested SPI clock will be ignored.</span></span> 


### <a name="spi-sample"></a><span data-ttu-id="94877-192">SPI 샘플</span><span class="sxs-lookup"><span data-stu-id="94877-192">SPI Sample</span></span>

<span data-ttu-id="94877-193">SPI를 수행 하는 방법을 예로 버스에 작성할 **SPI0** 아래에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="94877-193">An example on how to perform a SPI write on bus **SPI0** is shown below:</span></span>

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
