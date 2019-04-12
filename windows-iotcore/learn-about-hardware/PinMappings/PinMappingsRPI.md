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
# <a name="raspberry-pi-2--3-pin-mappings"></a><span data-ttu-id="09239-104">Raspberry Pi 2 및 3 핀 매핑</span><span class="sxs-lookup"><span data-stu-id="09239-104">Raspberry Pi 2 & 3 Pin Mappings</span></span>

![Raspberry Pi 2 및 3 핀 헤더](../../media/PinMappingsRPI/RP2_Pinout.png)

<span data-ttu-id="09239-106">40 핀 헤더를 통해 Raspberry Pi 2 및 Raspberry Pi 3에 대 한 하드웨어 인터페이스를 노출 시키는 **J8** 보드입니다.</span><span class="sxs-lookup"><span data-stu-id="09239-106">Hardware interfaces for the Raspberry Pi 2 and Raspberry Pi 3 are exposed through the 40-pin header **J8** on the board.</span></span> <span data-ttu-id="09239-107">기능은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="09239-107">Functionality includes:</span></span>

* <span data-ttu-id="09239-108">**24 x** -GPIO pin</span><span class="sxs-lookup"><span data-stu-id="09239-108">**24x** - GPIO pins</span></span>
* <span data-ttu-id="09239-109">**1 x** -직렬 UARTs (포함 미니 UART RPi3)</span><span class="sxs-lookup"><span data-stu-id="09239-109">**1x** - Serial UARTs (RPi3 only includes mini UART)</span></span>
* <span data-ttu-id="09239-110">**2 x** -SPI 버스</span><span class="sxs-lookup"><span data-stu-id="09239-110">**2x** - SPI bus</span></span>
* <span data-ttu-id="09239-111">**1x** - I2C bus</span><span class="sxs-lookup"><span data-stu-id="09239-111">**1x** - I2C bus</span></span>
* <span data-ttu-id="09239-112">**2 x** -5V power pin</span><span class="sxs-lookup"><span data-stu-id="09239-112">**2x** - 5V power pins</span></span>
* <span data-ttu-id="09239-113">**2 x** -3.3V 핀 power</span><span class="sxs-lookup"><span data-stu-id="09239-113">**2x** - 3.3V power pins</span></span>
* <span data-ttu-id="09239-114">**8 x** -pin 방지 매트를</span><span class="sxs-lookup"><span data-stu-id="09239-114">**8x** - Ground pins</span></span>

## <a name="gpio-pins"></a><span data-ttu-id="09239-115">GPIO Pin</span><span class="sxs-lookup"><span data-stu-id="09239-115">GPIO Pins</span></span>

<span data-ttu-id="09239-116">이 장치에서 사용 가능한 GPIO를 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="09239-116">Let's look at the GPIO available on this device.</span></span>

### <a name="gpio-pin-overview"></a><span data-ttu-id="09239-117">GPIO Pin 개요</span><span class="sxs-lookup"><span data-stu-id="09239-117">GPIO Pin Overview</span></span>

<span data-ttu-id="09239-118">다음 GPIO 핀은 Api를 통해 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="09239-118">The following GPIO pins are accessible through APIs:</span></span>

> | <span data-ttu-id="09239-119">GPIO#</span><span class="sxs-lookup"><span data-stu-id="09239-119">GPIO#</span></span> | <span data-ttu-id="09239-120">전원 켜기 끌어오기</span><span class="sxs-lookup"><span data-stu-id="09239-120">Power-on Pull</span></span> | <span data-ttu-id="09239-121">대체 함수</span><span class="sxs-lookup"><span data-stu-id="09239-121">Alternate Functions</span></span> | <span data-ttu-id="09239-122">헤더 Pin</span><span class="sxs-lookup"><span data-stu-id="09239-122">Header Pin</span></span>         |
> |-------|---------------|---------------------|--------------------|
> | <span data-ttu-id="09239-123">2</span><span class="sxs-lookup"><span data-stu-id="09239-123">2</span></span>     | <span data-ttu-id="09239-124">PullUp</span><span class="sxs-lookup"><span data-stu-id="09239-124">PullUp</span></span>        | <span data-ttu-id="09239-125">I2C1 SDA</span><span class="sxs-lookup"><span data-stu-id="09239-125">I2C1 SDA</span></span>            | <span data-ttu-id="09239-126">3</span><span class="sxs-lookup"><span data-stu-id="09239-126">3</span></span>                  |
> | <span data-ttu-id="09239-127">3</span><span class="sxs-lookup"><span data-stu-id="09239-127">3</span></span>     | <span data-ttu-id="09239-128">PullUp</span><span class="sxs-lookup"><span data-stu-id="09239-128">PullUp</span></span>        | <span data-ttu-id="09239-129">I2C1 SCL</span><span class="sxs-lookup"><span data-stu-id="09239-129">I2C1 SCL</span></span>            | <span data-ttu-id="09239-130">5</span><span class="sxs-lookup"><span data-stu-id="09239-130">5</span></span>                  |
> | <span data-ttu-id="09239-131">4</span><span class="sxs-lookup"><span data-stu-id="09239-131">4</span></span>     | <span data-ttu-id="09239-132">PullUp</span><span class="sxs-lookup"><span data-stu-id="09239-132">PullUp</span></span>        |                     | <span data-ttu-id="09239-133">7</span><span class="sxs-lookup"><span data-stu-id="09239-133">7</span></span>                  |
> | <span data-ttu-id="09239-134">5</span><span class="sxs-lookup"><span data-stu-id="09239-134">5</span></span>     | <span data-ttu-id="09239-135">PullUp</span><span class="sxs-lookup"><span data-stu-id="09239-135">PullUp</span></span>        |                     | <span data-ttu-id="09239-136">29</span><span class="sxs-lookup"><span data-stu-id="09239-136">29</span></span>                 |
> | <span data-ttu-id="09239-137">6</span><span class="sxs-lookup"><span data-stu-id="09239-137">6</span></span>     | <span data-ttu-id="09239-138">PullUp</span><span class="sxs-lookup"><span data-stu-id="09239-138">PullUp</span></span>        |                     | <span data-ttu-id="09239-139">31</span><span class="sxs-lookup"><span data-stu-id="09239-139">31</span></span>                 |
> | <span data-ttu-id="09239-140">7</span><span class="sxs-lookup"><span data-stu-id="09239-140">7</span></span>     | <span data-ttu-id="09239-141">PullUp</span><span class="sxs-lookup"><span data-stu-id="09239-141">PullUp</span></span>        | <span data-ttu-id="09239-142">SPI0 CS1</span><span class="sxs-lookup"><span data-stu-id="09239-142">SPI0 CS1</span></span>            | <span data-ttu-id="09239-143">26</span><span class="sxs-lookup"><span data-stu-id="09239-143">26</span></span>                 |
> | <span data-ttu-id="09239-144">8</span><span class="sxs-lookup"><span data-stu-id="09239-144">8</span></span>     | <span data-ttu-id="09239-145">PullUp</span><span class="sxs-lookup"><span data-stu-id="09239-145">PullUp</span></span>        | <span data-ttu-id="09239-146">SPI0 CS0</span><span class="sxs-lookup"><span data-stu-id="09239-146">SPI0 CS0</span></span>            | <span data-ttu-id="09239-147">24</span><span class="sxs-lookup"><span data-stu-id="09239-147">24</span></span>                 |
> | <span data-ttu-id="09239-148">9</span><span class="sxs-lookup"><span data-stu-id="09239-148">9</span></span>     | <span data-ttu-id="09239-149">PullDown</span><span class="sxs-lookup"><span data-stu-id="09239-149">PullDown</span></span>      | <span data-ttu-id="09239-150">SPI0 MISO</span><span class="sxs-lookup"><span data-stu-id="09239-150">SPI0 MISO</span></span>           | <span data-ttu-id="09239-151">21</span><span class="sxs-lookup"><span data-stu-id="09239-151">21</span></span>                 |
> | <span data-ttu-id="09239-152">10</span><span class="sxs-lookup"><span data-stu-id="09239-152">10</span></span>    | <span data-ttu-id="09239-153">PullDown</span><span class="sxs-lookup"><span data-stu-id="09239-153">PullDown</span></span>      | <span data-ttu-id="09239-154">SPI0 MOSI</span><span class="sxs-lookup"><span data-stu-id="09239-154">SPI0 MOSI</span></span>           | <span data-ttu-id="09239-155">19</span><span class="sxs-lookup"><span data-stu-id="09239-155">19</span></span>                 |
> | <span data-ttu-id="09239-156">11</span><span class="sxs-lookup"><span data-stu-id="09239-156">11</span></span>    | <span data-ttu-id="09239-157">PullDown</span><span class="sxs-lookup"><span data-stu-id="09239-157">PullDown</span></span>      | <span data-ttu-id="09239-158">SPI0 SCLK</span><span class="sxs-lookup"><span data-stu-id="09239-158">SPI0 SCLK</span></span>           | <span data-ttu-id="09239-159">23</span><span class="sxs-lookup"><span data-stu-id="09239-159">23</span></span>                 |
> | <span data-ttu-id="09239-160">12</span><span class="sxs-lookup"><span data-stu-id="09239-160">12</span></span>    | <span data-ttu-id="09239-161">PullDown</span><span class="sxs-lookup"><span data-stu-id="09239-161">PullDown</span></span>      |                     | <span data-ttu-id="09239-162">32</span><span class="sxs-lookup"><span data-stu-id="09239-162">32</span></span>                 |
> | <span data-ttu-id="09239-163">13</span><span class="sxs-lookup"><span data-stu-id="09239-163">13</span></span>    | <span data-ttu-id="09239-164">PullDown</span><span class="sxs-lookup"><span data-stu-id="09239-164">PullDown</span></span>      |                     | <span data-ttu-id="09239-165">33</span><span class="sxs-lookup"><span data-stu-id="09239-165">33</span></span>                 |
> | <span data-ttu-id="09239-166">16</span><span class="sxs-lookup"><span data-stu-id="09239-166">16</span></span>    | <span data-ttu-id="09239-167">PullDown</span><span class="sxs-lookup"><span data-stu-id="09239-167">PullDown</span></span>      | <span data-ttu-id="09239-168">SPI1 CS0</span><span class="sxs-lookup"><span data-stu-id="09239-168">SPI1 CS0</span></span>            | <span data-ttu-id="09239-169">36</span><span class="sxs-lookup"><span data-stu-id="09239-169">36</span></span>                 |
> | <span data-ttu-id="09239-170">17</span><span class="sxs-lookup"><span data-stu-id="09239-170">17</span></span>    | <span data-ttu-id="09239-171">PullDown</span><span class="sxs-lookup"><span data-stu-id="09239-171">PullDown</span></span>      |                     | <span data-ttu-id="09239-172">11</span><span class="sxs-lookup"><span data-stu-id="09239-172">11</span></span>                 |
> | <span data-ttu-id="09239-173">18</span><span class="sxs-lookup"><span data-stu-id="09239-173">18</span></span>    | <span data-ttu-id="09239-174">PullDown</span><span class="sxs-lookup"><span data-stu-id="09239-174">PullDown</span></span>      |                     | <span data-ttu-id="09239-175">12</span><span class="sxs-lookup"><span data-stu-id="09239-175">12</span></span>                 |
> | <span data-ttu-id="09239-176">19</span><span class="sxs-lookup"><span data-stu-id="09239-176">19</span></span>    | <span data-ttu-id="09239-177">PullDown</span><span class="sxs-lookup"><span data-stu-id="09239-177">PullDown</span></span>      | <span data-ttu-id="09239-178">SPI1 MISO</span><span class="sxs-lookup"><span data-stu-id="09239-178">SPI1 MISO</span></span>           | <span data-ttu-id="09239-179">35</span><span class="sxs-lookup"><span data-stu-id="09239-179">35</span></span>                 |
> | <span data-ttu-id="09239-180">20</span><span class="sxs-lookup"><span data-stu-id="09239-180">20</span></span>    | <span data-ttu-id="09239-181">PullDown</span><span class="sxs-lookup"><span data-stu-id="09239-181">PullDown</span></span>      | <span data-ttu-id="09239-182">SPI1 MOSI</span><span class="sxs-lookup"><span data-stu-id="09239-182">SPI1 MOSI</span></span>           | <span data-ttu-id="09239-183">38</span><span class="sxs-lookup"><span data-stu-id="09239-183">38</span></span>                 |
> | <span data-ttu-id="09239-184">21</span><span class="sxs-lookup"><span data-stu-id="09239-184">21</span></span>    | <span data-ttu-id="09239-185">PullDown</span><span class="sxs-lookup"><span data-stu-id="09239-185">PullDown</span></span>      | <span data-ttu-id="09239-186">SPI1 SCLK</span><span class="sxs-lookup"><span data-stu-id="09239-186">SPI1 SCLK</span></span>           | <span data-ttu-id="09239-187">40</span><span class="sxs-lookup"><span data-stu-id="09239-187">40</span></span>                 |
> | <span data-ttu-id="09239-188">22</span><span class="sxs-lookup"><span data-stu-id="09239-188">22</span></span>    | <span data-ttu-id="09239-189">PullDown</span><span class="sxs-lookup"><span data-stu-id="09239-189">PullDown</span></span>      |                     | <span data-ttu-id="09239-190">15</span><span class="sxs-lookup"><span data-stu-id="09239-190">15</span></span>                 |
> | <span data-ttu-id="09239-191">23</span><span class="sxs-lookup"><span data-stu-id="09239-191">23</span></span>    | <span data-ttu-id="09239-192">PullDown</span><span class="sxs-lookup"><span data-stu-id="09239-192">PullDown</span></span>      |                     | <span data-ttu-id="09239-193">16</span><span class="sxs-lookup"><span data-stu-id="09239-193">16</span></span>                 |
> | <span data-ttu-id="09239-194">24</span><span class="sxs-lookup"><span data-stu-id="09239-194">24</span></span>    | <span data-ttu-id="09239-195">PullDown</span><span class="sxs-lookup"><span data-stu-id="09239-195">PullDown</span></span>      |                     | <span data-ttu-id="09239-196">18</span><span class="sxs-lookup"><span data-stu-id="09239-196">18</span></span>                 |
> | <span data-ttu-id="09239-197">25</span><span class="sxs-lookup"><span data-stu-id="09239-197">25</span></span>    | <span data-ttu-id="09239-198">PullDown</span><span class="sxs-lookup"><span data-stu-id="09239-198">PullDown</span></span>      |                     | <span data-ttu-id="09239-199">22</span><span class="sxs-lookup"><span data-stu-id="09239-199">22</span></span>                 |
> | <span data-ttu-id="09239-200">26</span><span class="sxs-lookup"><span data-stu-id="09239-200">26</span></span>    | <span data-ttu-id="09239-201">PullDown</span><span class="sxs-lookup"><span data-stu-id="09239-201">PullDown</span></span>      |                     | <span data-ttu-id="09239-202">37</span><span class="sxs-lookup"><span data-stu-id="09239-202">37</span></span>                 |
> | <span data-ttu-id="09239-203">27</span><span class="sxs-lookup"><span data-stu-id="09239-203">27</span></span>    | <span data-ttu-id="09239-204">PullDown</span><span class="sxs-lookup"><span data-stu-id="09239-204">PullDown</span></span>      |                     | <span data-ttu-id="09239-205">13</span><span class="sxs-lookup"><span data-stu-id="09239-205">13</span></span>                 |
> | <span data-ttu-id="09239-206">35\*</span><span class="sxs-lookup"><span data-stu-id="09239-206">35\*</span></span>   | <span data-ttu-id="09239-207">PullUp</span><span class="sxs-lookup"><span data-stu-id="09239-207">PullUp</span></span>        |                     | <span data-ttu-id="09239-208">빨간색 전원 LED</span><span class="sxs-lookup"><span data-stu-id="09239-208">Red Power LED</span></span>      |
> | <span data-ttu-id="09239-209">47\*</span><span class="sxs-lookup"><span data-stu-id="09239-209">47\*</span></span>   | <span data-ttu-id="09239-210">PullUp</span><span class="sxs-lookup"><span data-stu-id="09239-210">PullUp</span></span>        |                     | <span data-ttu-id="09239-211">녹색 동작 LED</span><span class="sxs-lookup"><span data-stu-id="09239-211">Green Activity LED</span></span> |

<span data-ttu-id="09239-212">\* Raspberry Pi 2만 =.</span><span class="sxs-lookup"><span data-stu-id="09239-212">\* = Raspberry Pi 2 ONLY.</span></span> <span data-ttu-id="09239-213">GPIO 35 & 47 Raspberry Pi 3에서 제공 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="09239-213">GPIO 35 & 47 are not available on Raspberry Pi 3.</span></span>

### <a name="gpio-sample"></a><span data-ttu-id="09239-214">GPIO 샘플</span><span class="sxs-lookup"><span data-stu-id="09239-214">GPIO Sample</span></span>

<span data-ttu-id="09239-215">예를 들어 다음 코드 열립니다 **GPIO 5** 출력으로 디지털 쓰고 '**1**' 핀 아웃 합니다.</span><span class="sxs-lookup"><span data-stu-id="09239-215">As an example, the following code opens **GPIO 5** as an output and writes a digital '**1**' out on the pin:</span></span>

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

<span data-ttu-id="09239-216">Pin을 열면 끌어오기 저항기를 포함할 수 있는 해당 전원 켜기 상태가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="09239-216">When you open a pin, it will be in its power-on state, which may include a pull resistor.</span></span> <span data-ttu-id="09239-217">끌어오기 반대자 분리를 높은 임피던스 입력을 가져오려면 GpioPinDriveMode.Input을 드라이브 모드를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="09239-217">To disconnect the pull resistors and get a high-impedance input, set the drive mode to GpioPinDriveMode.Input:</span></span>

    pin.SetDriveMode(GpioPinDriveMode.Input);

<span data-ttu-id="09239-218">Pin 닫힐 때 전원 켜기 상태로 되돌립니다.</span><span class="sxs-lookup"><span data-stu-id="09239-218">When a pin is closed, it reverts to its power-on state.</span></span>

### <a name="pin-muxing"></a><span data-ttu-id="09239-219">Pin Muxing</span><span class="sxs-lookup"><span data-stu-id="09239-219">Pin Muxing</span></span>

<span data-ttu-id="09239-220">일부 GPIO pin 여러 함수를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="09239-220">Some GPIO pins can perform multiple functions.</span></span> <span data-ttu-id="09239-221">기본적으로 pin GPIO 입력으로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="09239-221">By default, pins are configured as GPIO inputs.</span></span> <span data-ttu-id="09239-222">호출 하 여 대체 함수를 열면 `I2cDevice.FromIdAsync()` 또는 `SpiDevice.FromIdAsync()` 를 함수에 필요한 pin은 자동으로 전환된 ("muxed") 올바른 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="09239-222">When you open an alternate function by calling `I2cDevice.FromIdAsync()` or `SpiDevice.FromIdAsync()` , the pins required by the function are automatically switched ("muxed") to the correct function.</span></span> <span data-ttu-id="09239-223">호출 하 여 장치를 닫을 때 `I2cDevice.Dispose()` 또는 `SpiDevice.Dispose()`, 핀으로 해당 기본 함수 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="09239-223">When the device is closed by calling `I2cDevice.Dispose()` or `SpiDevice.Dispose()`, the pins revert back to their default function.</span></span> <span data-ttu-id="09239-224">한 번에 두 개의 다른 함수에 대 한 pin을 사용 하려는 경우 충돌 하는 함수를 열 때 예외가 throw 됩니다.</span><span class="sxs-lookup"><span data-stu-id="09239-224">If you try to use a pin for two different functions at once, an exception will be thrown when you try to open the conflicting function.</span></span> <span data-ttu-id="09239-225">예:</span><span class="sxs-lookup"><span data-stu-id="09239-225">For example,</span></span>

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

## <a name="serial-uart"></a><span data-ttu-id="09239-226">직렬 UART</span><span class="sxs-lookup"><span data-stu-id="09239-226">Serial UART</span></span>

<span data-ttu-id="09239-227">RPi2/3에서 사용 가능한 하나의 직렬 UART 방법이: **UART0**</span><span class="sxs-lookup"><span data-stu-id="09239-227">There is one Serial UART available on the RPi2/3: **UART0**</span></span>

* <span data-ttu-id="09239-228">8-고정 **UART0 TX**</span><span class="sxs-lookup"><span data-stu-id="09239-228">Pin 8  - **UART0 TX**</span></span>
* <span data-ttu-id="09239-229">고정 10- **UART0 RX**</span><span class="sxs-lookup"><span data-stu-id="09239-229">Pin 10  - **UART0 RX**</span></span>

<span data-ttu-id="09239-230">초기화 아래 예에서 **UART0** 읽기 뒤 쓰기를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="09239-230">The example below initializes **UART0** and performs a write followed by a read:</span></span>


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

<span data-ttu-id="09239-231">다음 기능을 추가 해야 합니다 **Package.appxmanifest** 직렬 UART 코드를 실행 하기 위해 UWP 프로젝트에서 파일:</span><span class="sxs-lookup"><span data-stu-id="09239-231">Note that you must add the following capability to the **Package.appxmanifest** file in your UWP project to run Serial UART code:</span></span>

<span data-ttu-id="09239-232">Visual Studio 2017에 매니페스트 디자이너에서 (appxmanifest 파일에 대 한 시각적 편집기) serialcommunication 기능에 영향을 주는 알려진된 버그가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="09239-232">Visual Studio 2017 has a known bug in the Manifest Designer (the visual editor for appxmanifest files) that affects the serialcommunication capability.</span></span>  <span data-ttu-id="09239-233">프로그램 appxmanifest serialcommunication 기능에 추가 하는 경우 디자이너를 사용 하 여 프로그램 appxmanifest 수정 프로그램 appxmanifest (장치 xml 자식 없어집니다.) 손상 됩니다.</span><span class="sxs-lookup"><span data-stu-id="09239-233">If your appxmanifest adds the serialcommunication capability, modifying your appxmanifest with the designer will corrupt your appxmanifest (the Device xml child will be lost).</span></span>  <span data-ttu-id="09239-234">수 해결 방법이이 문제 appxmanifest 직접 편집 하 여 프로그램 appxmanifest를 마우스 오른쪽 단추로 클릭 하 고 상황에 맞는 메뉴에서 코드 보기를 선택 하 여.</span><span class="sxs-lookup"><span data-stu-id="09239-234">You can workaround this problem by hand editting the appxmanifest by right-clicking your appxmanifest and selecting View Code from the context menu.</span></span>

```xml
  <Capabilities>
    <DeviceCapability Name="serialcommunication">
      <Device Id="any">
        <Function Type="name:serialPort" />
      </Device>
    </DeviceCapability>
  </Capabilities>
```

## <a name="i2c-bus"></a><span data-ttu-id="09239-235">I2C 버스</span><span class="sxs-lookup"><span data-stu-id="09239-235">I2C Bus</span></span>

<span data-ttu-id="09239-236">이 장치에서 사용할 수 있는 I2C 버스를 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="09239-236">Let's look at the I2C bus available on this device.</span></span>

### <a name="i2c-overview"></a><span data-ttu-id="09239-237">I2C 개요</span><span class="sxs-lookup"><span data-stu-id="09239-237">I2C Overview</span></span>

<span data-ttu-id="09239-238">하나의 I2C 컨트롤러가 **I2C1** 두 줄을 사용 하 여 pin 헤더에 노출 **SDA** 하 고 **SCL**합니다.</span><span class="sxs-lookup"><span data-stu-id="09239-238">There is one I2C controller **I2C1** exposed on the pin header with two lines **SDA** and **SCL**.</span></span> <span data-ttu-id="09239-239">1.8 K&#x2126; 내부 풀업 레지스터가이 버스 게시판에 이미 설치 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="09239-239">1.8K&#x2126; internal pull-up resistors are already installed on the board for this bus.</span></span>

> | <span data-ttu-id="09239-240">신호 이름</span><span class="sxs-lookup"><span data-stu-id="09239-240">Signal Name</span></span> | <span data-ttu-id="09239-241">Pin 번호 머리글</span><span class="sxs-lookup"><span data-stu-id="09239-241">Header Pin Number</span></span> | <span data-ttu-id="09239-242">Gpio 수</span><span class="sxs-lookup"><span data-stu-id="09239-242">Gpio Number</span></span> |
> |-------------|-------------------|-------------|
> | <span data-ttu-id="09239-243">SDA</span><span class="sxs-lookup"><span data-stu-id="09239-243">SDA</span></span>         | <span data-ttu-id="09239-244">3</span><span class="sxs-lookup"><span data-stu-id="09239-244">3</span></span>                 | <span data-ttu-id="09239-245">2</span><span class="sxs-lookup"><span data-stu-id="09239-245">2</span></span>           |
> | <span data-ttu-id="09239-246">SCL</span><span class="sxs-lookup"><span data-stu-id="09239-246">SCL</span></span>         | <span data-ttu-id="09239-247">5</span><span class="sxs-lookup"><span data-stu-id="09239-247">5</span></span>                 | <span data-ttu-id="09239-248">3</span><span class="sxs-lookup"><span data-stu-id="09239-248">3</span></span>           |

<span data-ttu-id="09239-249">초기화 아래 예에서 **I2C1** I2C 장치 주소를 사용 하 여 데이터를 쓰고 **0x40**:</span><span class="sxs-lookup"><span data-stu-id="09239-249">The example below initializes **I2C1** and writes data to an I2C device with address **0x40**:</span></span>

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

## <a name="spi-bus"></a><span data-ttu-id="09239-250">SPI 버스</span><span class="sxs-lookup"><span data-stu-id="09239-250">SPI Bus</span></span>

<span data-ttu-id="09239-251">RPi2/3에 사용할 수 있는 두 명의 SPI 버스 컨트롤러가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="09239-251">There are two SPI bus controllers available on the RPi2/3.</span></span>

### <a name="spi0"></a><span data-ttu-id="09239-252">SPI0</span><span class="sxs-lookup"><span data-stu-id="09239-252">SPI0</span></span>

> | <span data-ttu-id="09239-253">신호 이름</span><span class="sxs-lookup"><span data-stu-id="09239-253">Signal Name</span></span> | <span data-ttu-id="09239-254">Pin 번호 머리글</span><span class="sxs-lookup"><span data-stu-id="09239-254">Header Pin Number</span></span> | <span data-ttu-id="09239-255">Gpio 수</span><span class="sxs-lookup"><span data-stu-id="09239-255">Gpio Number</span></span> |
> |-------------|-------------------|-------------|
> | <span data-ttu-id="09239-256">MOSI</span><span class="sxs-lookup"><span data-stu-id="09239-256">MOSI</span></span>        | <span data-ttu-id="09239-257">19</span><span class="sxs-lookup"><span data-stu-id="09239-257">19</span></span>                | <span data-ttu-id="09239-258">10</span><span class="sxs-lookup"><span data-stu-id="09239-258">10</span></span>          |
> | <span data-ttu-id="09239-259">MISO</span><span class="sxs-lookup"><span data-stu-id="09239-259">MISO</span></span>        | <span data-ttu-id="09239-260">21</span><span class="sxs-lookup"><span data-stu-id="09239-260">21</span></span>                | <span data-ttu-id="09239-261">9</span><span class="sxs-lookup"><span data-stu-id="09239-261">9</span></span>           |
> | <span data-ttu-id="09239-262">SCLK</span><span class="sxs-lookup"><span data-stu-id="09239-262">SCLK</span></span>        | <span data-ttu-id="09239-263">23</span><span class="sxs-lookup"><span data-stu-id="09239-263">23</span></span>                | <span data-ttu-id="09239-264">11</span><span class="sxs-lookup"><span data-stu-id="09239-264">11</span></span>          |
> | <span data-ttu-id="09239-265">CS0</span><span class="sxs-lookup"><span data-stu-id="09239-265">CS0</span></span>         | <span data-ttu-id="09239-266">24</span><span class="sxs-lookup"><span data-stu-id="09239-266">24</span></span>                | <span data-ttu-id="09239-267">8</span><span class="sxs-lookup"><span data-stu-id="09239-267">8</span></span>           |
> | <span data-ttu-id="09239-268">CS1</span><span class="sxs-lookup"><span data-stu-id="09239-268">CS1</span></span>         | <span data-ttu-id="09239-269">26</span><span class="sxs-lookup"><span data-stu-id="09239-269">26</span></span>                | <span data-ttu-id="09239-270">7</span><span class="sxs-lookup"><span data-stu-id="09239-270">7</span></span>           |

### <a name="spi1"></a><span data-ttu-id="09239-271">SPI1</span><span class="sxs-lookup"><span data-stu-id="09239-271">SPI1</span></span>

> | <span data-ttu-id="09239-272">신호 이름</span><span class="sxs-lookup"><span data-stu-id="09239-272">Signal Name</span></span> | <span data-ttu-id="09239-273">Pin 번호 머리글</span><span class="sxs-lookup"><span data-stu-id="09239-273">Header Pin Number</span></span> | <span data-ttu-id="09239-274">Gpio 수</span><span class="sxs-lookup"><span data-stu-id="09239-274">Gpio Number</span></span> |
> |-------------|-------------------|-------------|
> | <span data-ttu-id="09239-275">MOSI</span><span class="sxs-lookup"><span data-stu-id="09239-275">MOSI</span></span>        | <span data-ttu-id="09239-276">38</span><span class="sxs-lookup"><span data-stu-id="09239-276">38</span></span>                | <span data-ttu-id="09239-277">20</span><span class="sxs-lookup"><span data-stu-id="09239-277">20</span></span>          |
> | <span data-ttu-id="09239-278">MISO</span><span class="sxs-lookup"><span data-stu-id="09239-278">MISO</span></span>        | <span data-ttu-id="09239-279">35</span><span class="sxs-lookup"><span data-stu-id="09239-279">35</span></span>                | <span data-ttu-id="09239-280">19</span><span class="sxs-lookup"><span data-stu-id="09239-280">19</span></span>          |
> | <span data-ttu-id="09239-281">SCLK</span><span class="sxs-lookup"><span data-stu-id="09239-281">SCLK</span></span>        | <span data-ttu-id="09239-282">40</span><span class="sxs-lookup"><span data-stu-id="09239-282">40</span></span>                | <span data-ttu-id="09239-283">21</span><span class="sxs-lookup"><span data-stu-id="09239-283">21</span></span>          |
> | <span data-ttu-id="09239-284">CS0</span><span class="sxs-lookup"><span data-stu-id="09239-284">CS0</span></span>         | <span data-ttu-id="09239-285">36</span><span class="sxs-lookup"><span data-stu-id="09239-285">36</span></span>                | <span data-ttu-id="09239-286">16</span><span class="sxs-lookup"><span data-stu-id="09239-286">16</span></span>          |


### <a name="spi-sample"></a><span data-ttu-id="09239-287">SPI 샘플</span><span class="sxs-lookup"><span data-stu-id="09239-287">SPI Sample</span></span>

<span data-ttu-id="09239-288">SPI를 수행 하는 방법의 예가 버스에 작성할 **SPI0** 칩 선택 0을 사용 하는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="09239-288">An example of how to perform a SPI write on bus **SPI0** using chip select 0 is shown below:</span></span>

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

