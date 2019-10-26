---
title: Raspberry Pi 2 & 3 Pin 매핑
ms.date: 08/28/2017
ms.topic: article
description: Raspberry Pi 2 및 3에 대 한 pin 매핑 기능에 대해 알아봅니다.
keywords: windows iot, Rasperry Pi 2, Raspberry Pi 3, pin 매핑, GPIO
ms.openlocfilehash: 2a3155b28fb01434ff8596de6e2f75b06b42f6ae
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72917845"
---
# <a name="raspberry-pi-2--3-pin-mappings"></a><span data-ttu-id="554da-104">Raspberry Pi 2 & 3 Pin 매핑</span><span class="sxs-lookup"><span data-stu-id="554da-104">Raspberry Pi 2 & 3 Pin Mappings</span></span>

![Raspberry Pi 2 & 3 핀 헤더](../../media/PinMappingsRPI/RP2_Pinout.png)

<span data-ttu-id="554da-106">Raspberry Pi 2 및 Raspberry Pi 3의 하드웨어 인터페이스는 보드의 40 핀 헤더 **J8** 를 통해 노출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="554da-106">Hardware interfaces for the Raspberry Pi 2 and Raspberry Pi 3 are exposed through the 40-pin header **J8** on the board.</span></span> <span data-ttu-id="554da-107">기능은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="554da-107">Functionality includes:</span></span>

* <span data-ttu-id="554da-108">**24x** -GPIO 핀</span><span class="sxs-lookup"><span data-stu-id="554da-108">**24x** - GPIO pins</span></span>
* <span data-ttu-id="554da-109">**1x** -직렬 uarts (RPi3에만 미니 UART 포함)</span><span class="sxs-lookup"><span data-stu-id="554da-109">**1x** - Serial UARTs (RPi3 only includes mini UART)</span></span>
* <span data-ttu-id="554da-110">**2x** -SPI 버스</span><span class="sxs-lookup"><span data-stu-id="554da-110">**2x** - SPI bus</span></span>
* <span data-ttu-id="554da-111">**1x** -I2C 버스</span><span class="sxs-lookup"><span data-stu-id="554da-111">**1x** - I2C bus</span></span>
* <span data-ttu-id="554da-112">**2** -5v 전원 핀</span><span class="sxs-lookup"><span data-stu-id="554da-112">**2x** - 5V power pins</span></span>
* <span data-ttu-id="554da-113">**2x** -3.3 v 전원 핀</span><span class="sxs-lookup"><span data-stu-id="554da-113">**2x** - 3.3V power pins</span></span>
* <span data-ttu-id="554da-114">**8x** -접지 핀</span><span class="sxs-lookup"><span data-stu-id="554da-114">**8x** - Ground pins</span></span>

## <a name="gpio-pins"></a><span data-ttu-id="554da-115">GPIO 핀</span><span class="sxs-lookup"><span data-stu-id="554da-115">GPIO Pins</span></span>

<span data-ttu-id="554da-116">이 장치에서 사용 가능한 GPIO를 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="554da-116">Let's look at the GPIO available on this device.</span></span>

### <a name="gpio-pin-overview"></a><span data-ttu-id="554da-117">GPIO 고정 개요</span><span class="sxs-lookup"><span data-stu-id="554da-117">GPIO Pin Overview</span></span>

<span data-ttu-id="554da-118">다음 GPIO pin은 Api를 통해 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="554da-118">The following GPIO pins are accessible through APIs:</span></span>

> | <span data-ttu-id="554da-119">GPIO #</span><span class="sxs-lookup"><span data-stu-id="554da-119">GPIO#</span></span> | <span data-ttu-id="554da-120">전원 켜기 풀</span><span class="sxs-lookup"><span data-stu-id="554da-120">Power-on Pull</span></span> | <span data-ttu-id="554da-121">대체 함수</span><span class="sxs-lookup"><span data-stu-id="554da-121">Alternate Functions</span></span> | <span data-ttu-id="554da-122">헤더 Pin</span><span class="sxs-lookup"><span data-stu-id="554da-122">Header Pin</span></span>         |
> |-------|---------------|---------------------|--------------------|
> | <span data-ttu-id="554da-123">2</span><span class="sxs-lookup"><span data-stu-id="554da-123">2</span></span>     | <span data-ttu-id="554da-124">PullUp</span><span class="sxs-lookup"><span data-stu-id="554da-124">PullUp</span></span>        | <span data-ttu-id="554da-125">I2C1 SDA</span><span class="sxs-lookup"><span data-stu-id="554da-125">I2C1 SDA</span></span>            | <span data-ttu-id="554da-126">3</span><span class="sxs-lookup"><span data-stu-id="554da-126">3</span></span>                  |
> | <span data-ttu-id="554da-127">3</span><span class="sxs-lookup"><span data-stu-id="554da-127">3</span></span>     | <span data-ttu-id="554da-128">PullUp</span><span class="sxs-lookup"><span data-stu-id="554da-128">PullUp</span></span>        | <span data-ttu-id="554da-129">I2C1 SCL</span><span class="sxs-lookup"><span data-stu-id="554da-129">I2C1 SCL</span></span>            | <span data-ttu-id="554da-130">5</span><span class="sxs-lookup"><span data-stu-id="554da-130">5</span></span>                  |
> | <span data-ttu-id="554da-131">추가를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="554da-131">4</span></span>     | <span data-ttu-id="554da-132">PullUp</span><span class="sxs-lookup"><span data-stu-id="554da-132">PullUp</span></span>        |                     | <span data-ttu-id="554da-133">7</span><span class="sxs-lookup"><span data-stu-id="554da-133">7</span></span>                  |
> | <span data-ttu-id="554da-134">5</span><span class="sxs-lookup"><span data-stu-id="554da-134">5</span></span>     | <span data-ttu-id="554da-135">PullUp</span><span class="sxs-lookup"><span data-stu-id="554da-135">PullUp</span></span>        |                     | <span data-ttu-id="554da-136">29</span><span class="sxs-lookup"><span data-stu-id="554da-136">29</span></span>                 |
> | <span data-ttu-id="554da-137">6</span><span class="sxs-lookup"><span data-stu-id="554da-137">6</span></span>     | <span data-ttu-id="554da-138">PullUp</span><span class="sxs-lookup"><span data-stu-id="554da-138">PullUp</span></span>        |                     | <span data-ttu-id="554da-139">31</span><span class="sxs-lookup"><span data-stu-id="554da-139">31</span></span>                 |
> | <span data-ttu-id="554da-140">7</span><span class="sxs-lookup"><span data-stu-id="554da-140">7</span></span>     | <span data-ttu-id="554da-141">PullUp</span><span class="sxs-lookup"><span data-stu-id="554da-141">PullUp</span></span>        | <span data-ttu-id="554da-142">SPI0 CS1</span><span class="sxs-lookup"><span data-stu-id="554da-142">SPI0 CS1</span></span>            | <span data-ttu-id="554da-143">26</span><span class="sxs-lookup"><span data-stu-id="554da-143">26</span></span>                 |
> | <span data-ttu-id="554da-144">8</span><span class="sxs-lookup"><span data-stu-id="554da-144">8</span></span>     | <span data-ttu-id="554da-145">PullUp</span><span class="sxs-lookup"><span data-stu-id="554da-145">PullUp</span></span>        | <span data-ttu-id="554da-146">SPI0 CS0</span><span class="sxs-lookup"><span data-stu-id="554da-146">SPI0 CS0</span></span>            | <span data-ttu-id="554da-147">24</span><span class="sxs-lookup"><span data-stu-id="554da-147">24</span></span>                 |
> | <span data-ttu-id="554da-148">9</span><span class="sxs-lookup"><span data-stu-id="554da-148">9</span></span>     | <span data-ttu-id="554da-149">3:2</span><span class="sxs-lookup"><span data-stu-id="554da-149">PullDown</span></span>      | <span data-ttu-id="554da-150">SPI0 MISO</span><span class="sxs-lookup"><span data-stu-id="554da-150">SPI0 MISO</span></span>           | <span data-ttu-id="554da-151">RD 세션 호스트 서버 팜의 이름을 지정하는 새 RD RAP 만들기</span><span class="sxs-lookup"><span data-stu-id="554da-151">21</span></span>                 |
> | <span data-ttu-id="554da-152">10</span><span class="sxs-lookup"><span data-stu-id="554da-152">10</span></span>    | <span data-ttu-id="554da-153">3:2</span><span class="sxs-lookup"><span data-stu-id="554da-153">PullDown</span></span>      | <span data-ttu-id="554da-154">SPI0 MOSI</span><span class="sxs-lookup"><span data-stu-id="554da-154">SPI0 MOSI</span></span>           | <span data-ttu-id="554da-155">19</span><span class="sxs-lookup"><span data-stu-id="554da-155">19</span></span>                 |
> | <span data-ttu-id="554da-156">11</span><span class="sxs-lookup"><span data-stu-id="554da-156">11</span></span>    | <span data-ttu-id="554da-157">3:2</span><span class="sxs-lookup"><span data-stu-id="554da-157">PullDown</span></span>      | <span data-ttu-id="554da-158">SPI0 SCLK</span><span class="sxs-lookup"><span data-stu-id="554da-158">SPI0 SCLK</span></span>           | <span data-ttu-id="554da-159">23</span><span class="sxs-lookup"><span data-stu-id="554da-159">23</span></span>                 |
> | <span data-ttu-id="554da-160">12</span><span class="sxs-lookup"><span data-stu-id="554da-160">12</span></span>    | <span data-ttu-id="554da-161">3:2</span><span class="sxs-lookup"><span data-stu-id="554da-161">PullDown</span></span>      |                     | <span data-ttu-id="554da-162">32</span><span class="sxs-lookup"><span data-stu-id="554da-162">32</span></span>                 |
> | <span data-ttu-id="554da-163">13</span><span class="sxs-lookup"><span data-stu-id="554da-163">13</span></span>    | <span data-ttu-id="554da-164">3:2</span><span class="sxs-lookup"><span data-stu-id="554da-164">PullDown</span></span>      |                     | <span data-ttu-id="554da-165">33</span><span class="sxs-lookup"><span data-stu-id="554da-165">33</span></span>                 |
> | <span data-ttu-id="554da-166">16</span><span class="sxs-lookup"><span data-stu-id="554da-166">16</span></span>    | <span data-ttu-id="554da-167">3:2</span><span class="sxs-lookup"><span data-stu-id="554da-167">PullDown</span></span>      | <span data-ttu-id="554da-168">SPI1 CS0</span><span class="sxs-lookup"><span data-stu-id="554da-168">SPI1 CS0</span></span>            | <span data-ttu-id="554da-169">36</span><span class="sxs-lookup"><span data-stu-id="554da-169">36</span></span>                 |
> | <span data-ttu-id="554da-170">17</span><span class="sxs-lookup"><span data-stu-id="554da-170">17</span></span>    | <span data-ttu-id="554da-171">3:2</span><span class="sxs-lookup"><span data-stu-id="554da-171">PullDown</span></span>      |                     | <span data-ttu-id="554da-172">11</span><span class="sxs-lookup"><span data-stu-id="554da-172">11</span></span>                 |
> | <span data-ttu-id="554da-173">18</span><span class="sxs-lookup"><span data-stu-id="554da-173">18</span></span>    | <span data-ttu-id="554da-174">3:2</span><span class="sxs-lookup"><span data-stu-id="554da-174">PullDown</span></span>      |                     | <span data-ttu-id="554da-175">12</span><span class="sxs-lookup"><span data-stu-id="554da-175">12</span></span>                 |
> | <span data-ttu-id="554da-176">19</span><span class="sxs-lookup"><span data-stu-id="554da-176">19</span></span>    | <span data-ttu-id="554da-177">3:2</span><span class="sxs-lookup"><span data-stu-id="554da-177">PullDown</span></span>      | <span data-ttu-id="554da-178">SPI1 MISO</span><span class="sxs-lookup"><span data-stu-id="554da-178">SPI1 MISO</span></span>           | <span data-ttu-id="554da-179">35</span><span class="sxs-lookup"><span data-stu-id="554da-179">35</span></span>                 |
> | <span data-ttu-id="554da-180">20</span><span class="sxs-lookup"><span data-stu-id="554da-180">20</span></span>    | <span data-ttu-id="554da-181">3:2</span><span class="sxs-lookup"><span data-stu-id="554da-181">PullDown</span></span>      | <span data-ttu-id="554da-182">SPI1 MOSI</span><span class="sxs-lookup"><span data-stu-id="554da-182">SPI1 MOSI</span></span>           | <span data-ttu-id="554da-183">38</span><span class="sxs-lookup"><span data-stu-id="554da-183">38</span></span>                 |
> | <span data-ttu-id="554da-184">RD 세션 호스트 서버 팜의 이름을 지정하는 새 RD RAP 만들기</span><span class="sxs-lookup"><span data-stu-id="554da-184">21</span></span>    | <span data-ttu-id="554da-185">3:2</span><span class="sxs-lookup"><span data-stu-id="554da-185">PullDown</span></span>      | <span data-ttu-id="554da-186">SPI1 SCLK</span><span class="sxs-lookup"><span data-stu-id="554da-186">SPI1 SCLK</span></span>           | <span data-ttu-id="554da-187">40</span><span class="sxs-lookup"><span data-stu-id="554da-187">40</span></span>                 |
> | <span data-ttu-id="554da-188">22</span><span class="sxs-lookup"><span data-stu-id="554da-188">22</span></span>    | <span data-ttu-id="554da-189">3:2</span><span class="sxs-lookup"><span data-stu-id="554da-189">PullDown</span></span>      |                     | <span data-ttu-id="554da-190">15일</span><span class="sxs-lookup"><span data-stu-id="554da-190">15</span></span>                 |
> | <span data-ttu-id="554da-191">23</span><span class="sxs-lookup"><span data-stu-id="554da-191">23</span></span>    | <span data-ttu-id="554da-192">3:2</span><span class="sxs-lookup"><span data-stu-id="554da-192">PullDown</span></span>      |                     | <span data-ttu-id="554da-193">16</span><span class="sxs-lookup"><span data-stu-id="554da-193">16</span></span>                 |
> | <span data-ttu-id="554da-194">24</span><span class="sxs-lookup"><span data-stu-id="554da-194">24</span></span>    | <span data-ttu-id="554da-195">3:2</span><span class="sxs-lookup"><span data-stu-id="554da-195">PullDown</span></span>      |                     | <span data-ttu-id="554da-196">18</span><span class="sxs-lookup"><span data-stu-id="554da-196">18</span></span>                 |
> | <span data-ttu-id="554da-197">25일</span><span class="sxs-lookup"><span data-stu-id="554da-197">25</span></span>    | <span data-ttu-id="554da-198">3:2</span><span class="sxs-lookup"><span data-stu-id="554da-198">PullDown</span></span>      |                     | <span data-ttu-id="554da-199">22</span><span class="sxs-lookup"><span data-stu-id="554da-199">22</span></span>                 |
> | <span data-ttu-id="554da-200">26</span><span class="sxs-lookup"><span data-stu-id="554da-200">26</span></span>    | <span data-ttu-id="554da-201">3:2</span><span class="sxs-lookup"><span data-stu-id="554da-201">PullDown</span></span>      |                     | <span data-ttu-id="554da-202">37</span><span class="sxs-lookup"><span data-stu-id="554da-202">37</span></span>                 |
> | <span data-ttu-id="554da-203">27</span><span class="sxs-lookup"><span data-stu-id="554da-203">27</span></span>    | <span data-ttu-id="554da-204">3:2</span><span class="sxs-lookup"><span data-stu-id="554da-204">PullDown</span></span>      |                     | <span data-ttu-id="554da-205">13</span><span class="sxs-lookup"><span data-stu-id="554da-205">13</span></span>                 |
> | <span data-ttu-id="554da-206">35 \*</span><span class="sxs-lookup"><span data-stu-id="554da-206">35\*</span></span>   | <span data-ttu-id="554da-207">PullUp</span><span class="sxs-lookup"><span data-stu-id="554da-207">PullUp</span></span>        |                     | <span data-ttu-id="554da-208">빨간색 전원 LED</span><span class="sxs-lookup"><span data-stu-id="554da-208">Red Power LED</span></span>      |
> | <span data-ttu-id="554da-209">47 \*</span><span class="sxs-lookup"><span data-stu-id="554da-209">47\*</span></span>   | <span data-ttu-id="554da-210">PullUp</span><span class="sxs-lookup"><span data-stu-id="554da-210">PullUp</span></span>        |                     | <span data-ttu-id="554da-211">녹색 작업 LED</span><span class="sxs-lookup"><span data-stu-id="554da-211">Green Activity LED</span></span> |

<span data-ttu-id="554da-212">\* = Raspberry Pi 2에만 해당 합니다.</span><span class="sxs-lookup"><span data-stu-id="554da-212">\* = Raspberry Pi 2 ONLY.</span></span> <span data-ttu-id="554da-213">GPIO 35 & 47은 Raspberry Pi 3에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="554da-213">GPIO 35 & 47 are not available on Raspberry Pi 3.</span></span>

### <a name="gpio-sample"></a><span data-ttu-id="554da-214">GPIO 샘플</span><span class="sxs-lookup"><span data-stu-id="554da-214">GPIO Sample</span></span>

<span data-ttu-id="554da-215">예를 들어 다음 코드는 **GPIO 5** 를 출력으로 열고 pin에 디지털 '**1**'을 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="554da-215">As an example, the following code opens **GPIO 5** as an output and writes a digital '**1**' out on the pin:</span></span>

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

<span data-ttu-id="554da-216">Pin을 열면 전원 켜기 상태가 되며,이는 풀 저항기를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="554da-216">When you open a pin, it will be in its power-on state, which may include a pull resistor.</span></span> <span data-ttu-id="554da-217">풀 저항기의 연결을 끊고 높은 임피던스 입력을 얻으려면 드라이브 모드를 GpioPinDriveMode로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="554da-217">To disconnect the pull resistors and get a high-impedance input, set the drive mode to GpioPinDriveMode.Input:</span></span>

    pin.SetDriveMode(GpioPinDriveMode.Input);

<span data-ttu-id="554da-218">Pin이 닫히면 전원 켜기 상태로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="554da-218">When a pin is closed, it reverts to its power-on state.</span></span>

### <a name="pin-muxing"></a><span data-ttu-id="554da-219">Muxing 고정</span><span class="sxs-lookup"><span data-stu-id="554da-219">Pin Muxing</span></span>

<span data-ttu-id="554da-220">일부 GPIO pin은 여러 기능을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="554da-220">Some GPIO pins can perform multiple functions.</span></span> <span data-ttu-id="554da-221">기본적으로 pin은 GPIO 입력으로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="554da-221">By default, pins are configured as GPIO inputs.</span></span> <span data-ttu-id="554da-222">`I2cDevice.FromIdAsync()` 또는 `SpiDevice.FromIdAsync()`를 호출 하 여 대체 함수를 열면 함수에 필요한 pin이 자동으로 올바른 함수로 전환 됩니다 ("muxed").</span><span class="sxs-lookup"><span data-stu-id="554da-222">When you open an alternate function by calling `I2cDevice.FromIdAsync()` or `SpiDevice.FromIdAsync()` , the pins required by the function are automatically switched ("muxed") to the correct function.</span></span> <span data-ttu-id="554da-223">`I2cDevice.Dispose()` 또는 `SpiDevice.Dispose()`를 호출 하 여 장치를 닫으면 pin은 해당 기본 함수로 되돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="554da-223">When the device is closed by calling `I2cDevice.Dispose()` or `SpiDevice.Dispose()`, the pins revert back to their default function.</span></span> <span data-ttu-id="554da-224">두 개의 다른 함수에 대해 한 번에 pin을 사용 하려고 하면 충돌 하는 함수를 열려고 할 때 예외가 throw 됩니다.</span><span class="sxs-lookup"><span data-stu-id="554da-224">If you try to use a pin for two different functions at once, an exception will be thrown when you try to open the conflicting function.</span></span> <span data-ttu-id="554da-225">예를 들면</span><span class="sxs-lookup"><span data-stu-id="554da-225">For example,</span></span>

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

## <a name="serial-uart"></a><span data-ttu-id="554da-226">직렬 UART</span><span class="sxs-lookup"><span data-stu-id="554da-226">Serial UART</span></span>

<span data-ttu-id="554da-227">RPi2/3: **UART0** 에는 하나의 직렬 UART를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="554da-227">There is one Serial UART available on the RPi2/3: **UART0**</span></span>

* <span data-ttu-id="554da-228">Pin 8- **UART0 TX**</span><span class="sxs-lookup"><span data-stu-id="554da-228">Pin 8  - **UART0 TX**</span></span>
* <span data-ttu-id="554da-229">Pin 10- **UART0 RX**</span><span class="sxs-lookup"><span data-stu-id="554da-229">Pin 10  - **UART0 RX**</span></span>

<span data-ttu-id="554da-230">아래 예제에서는 **UART0** 를 초기화 하 고 쓰기 후에 읽기를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="554da-230">The example below initializes **UART0** and performs a write followed by a read:</span></span>


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

<span data-ttu-id="554da-231">직렬 UART 코드를 실행 하려면 UWP 프로젝트의 **appxmanifest.xml** 파일에 다음 기능을 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="554da-231">Note that you must add the following capability to the **Package.appxmanifest** file in your UWP project to run Serial UART code:</span></span>

<span data-ttu-id="554da-232">Visual Studio 2017에는 매니페스트 디자이너 (appxmanifest.xml 파일용 시각적 편집기)에서 serialcommunication 기능에 영향을 주는 알려진 버그가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="554da-232">Visual Studio 2017 has a known bug in the Manifest Designer (the visual editor for appxmanifest files) that affects the serialcommunication capability.</span></span>  <span data-ttu-id="554da-233">Appxmanifest.xml가 serialcommunication 기능을 추가 하는 경우 디자이너를 사용 하 여 appxmanifest.xml를 수정 하면 appxmanifest.xml가 손상 됩니다 (장치 xml 자식은 손실 됨).</span><span class="sxs-lookup"><span data-stu-id="554da-233">If your appxmanifest adds the serialcommunication capability, modifying your appxmanifest with the designer will corrupt your appxmanifest (the Device xml child will be lost).</span></span>  <span data-ttu-id="554da-234">Appxmanifest.xml를 마우스 오른쪽 단추로 클릭 하 고 상황에 맞는 메뉴에서 코드 보기를 선택 하 여 appxmanifest.xml를 직접 편집이 문제를 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="554da-234">You can workaround this problem by hand editting the appxmanifest by right-clicking your appxmanifest and selecting View Code from the context menu.</span></span>

```xml
  <Capabilities>
    <DeviceCapability Name="serialcommunication">
      <Device Id="any">
        <Function Type="name:serialPort" />
      </Device>
    </DeviceCapability>
  </Capabilities>
```

## <a name="i2c-bus"></a><span data-ttu-id="554da-235">I2C 버스</span><span class="sxs-lookup"><span data-stu-id="554da-235">I2C Bus</span></span>

<span data-ttu-id="554da-236">이 장치에서 사용할 수 있는 I2C bus를 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="554da-236">Let's look at the I2C bus available on this device.</span></span>

### <a name="i2c-overview"></a><span data-ttu-id="554da-237">I2C 개요</span><span class="sxs-lookup"><span data-stu-id="554da-237">I2C Overview</span></span>

<span data-ttu-id="554da-238">**Sda** 와 **SCL**이라는 두 줄로 된 핀 헤더에는 하나의 I2C 컨트롤러 **I2C1** 노출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="554da-238">There is one I2C controller **I2C1** exposed on the pin header with two lines **SDA** and **SCL**.</span></span> <span data-ttu-id="554da-239">1.8 k&#x2126; 내부 풀 (pull) 저항기는이 버스에 대해 보드에 이미 설치 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="554da-239">1.8K&#x2126; internal pull-up resistors are already installed on the board for this bus.</span></span>

> | <span data-ttu-id="554da-240">신호 이름</span><span class="sxs-lookup"><span data-stu-id="554da-240">Signal Name</span></span> | <span data-ttu-id="554da-241">헤더 Pin 번호</span><span class="sxs-lookup"><span data-stu-id="554da-241">Header Pin Number</span></span> | <span data-ttu-id="554da-242">Gpio 번호</span><span class="sxs-lookup"><span data-stu-id="554da-242">Gpio Number</span></span> |
> |-------------|-------------------|-------------|
> | <span data-ttu-id="554da-243">SDA</span><span class="sxs-lookup"><span data-stu-id="554da-243">SDA</span></span>         | <span data-ttu-id="554da-244">3</span><span class="sxs-lookup"><span data-stu-id="554da-244">3</span></span>                 | <span data-ttu-id="554da-245">2</span><span class="sxs-lookup"><span data-stu-id="554da-245">2</span></span>           |
> | <span data-ttu-id="554da-246">SCL</span><span class="sxs-lookup"><span data-stu-id="554da-246">SCL</span></span>         | <span data-ttu-id="554da-247">5</span><span class="sxs-lookup"><span data-stu-id="554da-247">5</span></span>                 | <span data-ttu-id="554da-248">3</span><span class="sxs-lookup"><span data-stu-id="554da-248">3</span></span>           |

<span data-ttu-id="554da-249">아래 예제에서는 **I2C1** 를 초기화 하 고 주소가 **0x40**인 I2C 장치에 데이터를 씁니다.</span><span class="sxs-lookup"><span data-stu-id="554da-249">The example below initializes **I2C1** and writes data to an I2C device with address **0x40**:</span></span>

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

## <a name="spi-bus"></a><span data-ttu-id="554da-250">SPI 버스</span><span class="sxs-lookup"><span data-stu-id="554da-250">SPI Bus</span></span>

<span data-ttu-id="554da-251">RPi2/3에서 사용 가능한 두 개의 SPI bus 컨트롤러가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="554da-251">There are two SPI bus controllers available on the RPi2/3.</span></span>

### <a name="spi0"></a><span data-ttu-id="554da-252">SPI0</span><span class="sxs-lookup"><span data-stu-id="554da-252">SPI0</span></span>

> | <span data-ttu-id="554da-253">신호 이름</span><span class="sxs-lookup"><span data-stu-id="554da-253">Signal Name</span></span> | <span data-ttu-id="554da-254">헤더 Pin 번호</span><span class="sxs-lookup"><span data-stu-id="554da-254">Header Pin Number</span></span> | <span data-ttu-id="554da-255">Gpio 번호</span><span class="sxs-lookup"><span data-stu-id="554da-255">Gpio Number</span></span> |
> |-------------|-------------------|-------------|
> | <span data-ttu-id="554da-256">MOSI</span><span class="sxs-lookup"><span data-stu-id="554da-256">MOSI</span></span>        | <span data-ttu-id="554da-257">19</span><span class="sxs-lookup"><span data-stu-id="554da-257">19</span></span>                | <span data-ttu-id="554da-258">10</span><span class="sxs-lookup"><span data-stu-id="554da-258">10</span></span>          |
> | <span data-ttu-id="554da-259">MISO</span><span class="sxs-lookup"><span data-stu-id="554da-259">MISO</span></span>        | <span data-ttu-id="554da-260">RD 세션 호스트 서버 팜의 이름을 지정하는 새 RD RAP 만들기</span><span class="sxs-lookup"><span data-stu-id="554da-260">21</span></span>                | <span data-ttu-id="554da-261">9</span><span class="sxs-lookup"><span data-stu-id="554da-261">9</span></span>           |
> | <span data-ttu-id="554da-262">SCLK</span><span class="sxs-lookup"><span data-stu-id="554da-262">SCLK</span></span>        | <span data-ttu-id="554da-263">23</span><span class="sxs-lookup"><span data-stu-id="554da-263">23</span></span>                | <span data-ttu-id="554da-264">11</span><span class="sxs-lookup"><span data-stu-id="554da-264">11</span></span>          |
> | <span data-ttu-id="554da-265">CS0</span><span class="sxs-lookup"><span data-stu-id="554da-265">CS0</span></span>         | <span data-ttu-id="554da-266">24</span><span class="sxs-lookup"><span data-stu-id="554da-266">24</span></span>                | <span data-ttu-id="554da-267">8</span><span class="sxs-lookup"><span data-stu-id="554da-267">8</span></span>           |
> | <span data-ttu-id="554da-268">CS1</span><span class="sxs-lookup"><span data-stu-id="554da-268">CS1</span></span>         | <span data-ttu-id="554da-269">26</span><span class="sxs-lookup"><span data-stu-id="554da-269">26</span></span>                | <span data-ttu-id="554da-270">7</span><span class="sxs-lookup"><span data-stu-id="554da-270">7</span></span>           |

### <a name="spi1"></a><span data-ttu-id="554da-271">SPI1</span><span class="sxs-lookup"><span data-stu-id="554da-271">SPI1</span></span>

> | <span data-ttu-id="554da-272">신호 이름</span><span class="sxs-lookup"><span data-stu-id="554da-272">Signal Name</span></span> | <span data-ttu-id="554da-273">헤더 Pin 번호</span><span class="sxs-lookup"><span data-stu-id="554da-273">Header Pin Number</span></span> | <span data-ttu-id="554da-274">Gpio 번호</span><span class="sxs-lookup"><span data-stu-id="554da-274">Gpio Number</span></span> |
> |-------------|-------------------|-------------|
> | <span data-ttu-id="554da-275">MOSI</span><span class="sxs-lookup"><span data-stu-id="554da-275">MOSI</span></span>        | <span data-ttu-id="554da-276">38</span><span class="sxs-lookup"><span data-stu-id="554da-276">38</span></span>                | <span data-ttu-id="554da-277">20</span><span class="sxs-lookup"><span data-stu-id="554da-277">20</span></span>          |
> | <span data-ttu-id="554da-278">MISO</span><span class="sxs-lookup"><span data-stu-id="554da-278">MISO</span></span>        | <span data-ttu-id="554da-279">35</span><span class="sxs-lookup"><span data-stu-id="554da-279">35</span></span>                | <span data-ttu-id="554da-280">19</span><span class="sxs-lookup"><span data-stu-id="554da-280">19</span></span>          |
> | <span data-ttu-id="554da-281">SCLK</span><span class="sxs-lookup"><span data-stu-id="554da-281">SCLK</span></span>        | <span data-ttu-id="554da-282">40</span><span class="sxs-lookup"><span data-stu-id="554da-282">40</span></span>                | <span data-ttu-id="554da-283">RD 세션 호스트 서버 팜의 이름을 지정하는 새 RD RAP 만들기</span><span class="sxs-lookup"><span data-stu-id="554da-283">21</span></span>          |
> | <span data-ttu-id="554da-284">CS0</span><span class="sxs-lookup"><span data-stu-id="554da-284">CS0</span></span>         | <span data-ttu-id="554da-285">36</span><span class="sxs-lookup"><span data-stu-id="554da-285">36</span></span>                | <span data-ttu-id="554da-286">16</span><span class="sxs-lookup"><span data-stu-id="554da-286">16</span></span>          |


### <a name="spi-sample"></a><span data-ttu-id="554da-287">SPI 샘플</span><span class="sxs-lookup"><span data-stu-id="554da-287">SPI Sample</span></span>

<span data-ttu-id="554da-288">칩 select 0을 사용 하 여 bus **SPI0** 에서 SPI 쓰기를 수행 하는 방법의 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="554da-288">An example of how to perform a SPI write on bus **SPI0** using chip select 0 is shown below:</span></span>

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

