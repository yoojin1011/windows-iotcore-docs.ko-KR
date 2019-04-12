---
title: 버스 공급자
author: msalehmsft
ms.author: msaleh
ms.date: 08/28/2017
ms.topic: article
description: Windows 10 IoT Core 통해 사용할 수 있는 다양 한 공급자에 알아봅니다.
keywords: windows iot, 공급자, UWP, Gpio Spi 버스 공급자
ms.openlocfilehash: 63e62e649aa6f54576e47419fe0be86ae5e5f096
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513158"
---
# <a name="bus-providers"></a><span data-ttu-id="ac0f9-104">버스 공급자</span><span class="sxs-lookup"><span data-stu-id="ac0f9-104">Bus Providers</span></span>

<span data-ttu-id="ac0f9-105">Windows 10 부터는 Windows 했습니다 Gpio, Spi에 대 한 직접 액세스를 제공 하는 상자에서 UWP Api 또는 I2c 버스 soc.에 있는 상위 수준 API에서에서이 하드웨어에 쉽게 액세스할을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac0f9-105">Starting with Windows 10, Windows has had in-box UWP APIs that provide direct access to Gpio, Spi, or I2c busses located on-soc. This gives very easy access to this hardware from a high level API.</span></span> <span data-ttu-id="ac0f9-106">그러나 장치 제조업체는 soc 해제 컨트롤러를 사용 하 여 버스를 액세스 하려고 할 때 많은 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac0f9-106">However, there are many times when a device maker wants to use an off-soc controller to access a bus.</span></span> <span data-ttu-id="ac0f9-107">16 GPIO 핀을 추가 하는 저렴 한 칩 만큼 간단 하거나 Gpio, SPI, 및 I2C 핀을 추가 하지만 또한 PWM 및 ADC 지원 뿐 아니라 (예: Arduino) 전체 MCU 만큼 다양 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac0f9-107">It can be as simple as a cheap chip that adds 16 GPIO pins, or as rich as a full MCU (like an Arduino) that not only adds Gpio, SPI, and I2C pins, but also supports PWM and ADC.</span></span> <span data-ttu-id="ac0f9-108">"Bus 공급자" 모델을 사용 하 여 제공 개발자가 연결 하는 사용자 모드 공급자를 사용 하 여 기본 Api를 사용 하 여 이러한 soc 해제 버스 간격에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac0f9-108">With the "Bus Provider" model, we give developers the ability to access these off-soc busses using the in-box APIs, using a user-mode provider that bridges the gap.</span></span> 

<span data-ttu-id="ac0f9-109">공급자를 작성 중인 사용자는 UWP 클래스 라이브러리 및 하드웨어 단순히 구성 요소를 포함 하는 기본 Api에 대 한 지시와 통신할 수 있는 개발자는 다음 인터페이스 집합을 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac0f9-109">Someone building a provider implements a set of interfaces into a UWP class library and then any developer who wants to talk to that hardware simply includes the component and tells the in-box APIs about it.</span></span> <span data-ttu-id="ac0f9-110">예제 코드를 살펴보면 합니다 [Remote Arduino 공급자](https://github.com/ms-iot/BusProviders/tree/develop/Arduino) 공급자를 구성 하려면 얼마나 쉬운지 볼 수 있습니다 이며, 해당 앱에 대 한 기본 공급자로 설정 되 면 나머지 클라이언트 앱의 코드 하는 데 필요한 코드와 동일을 soc에 bus 액세스 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac0f9-110">If you look at the sample code from the [Remote Arduino provider](https://github.com/ms-iot/BusProviders/tree/develop/Arduino) you can see how easy it is to configure the provider and, once set as the default provider for that app, the rest of the code in the client app is identical to the code required to access an on-soc bus.</span></span>  

```
ArduinoProviders.ArduinoProvider.Configuration = 
    new ArduinoProviders.ArduinoConnectionConfiguration("VID_2341", "PID_0043", 57600);
Windows.Devices.LowLevelDevicesController.DefaultProvider =  new ArduinoProviders.ArduinoProvider();

gpioController = await GpioController.GetDefaultAsync();
i2cController = await I2cController.GetDefaultAsync();
adcController = await AdcController.GetDefaultAsync();
pwmController = await PwmController.GetDefaultAsync();

GpioPin pin = gpioController.OpenPin(LED_PIN, GpioSharingMode.Exclusive);`
```

## <a name="available-providers"></a><span data-ttu-id="ac0f9-111">사용 가능한 공급자</span><span class="sxs-lookup"><span data-stu-id="ac0f9-111">Available Providers</span></span>

<span data-ttu-id="ac0f9-112">사용할 수 있는 공급자의 수로 현재 우리는 [Bus 공급자](https://github.com/ms-iot/BusProviders) github 리포지토리.</span><span class="sxs-lookup"><span data-stu-id="ac0f9-112">We currently have a number of providers available on the [Bus Providers](https://github.com/ms-iot/BusProviders) github repo.</span></span> <span data-ttu-id="ac0f9-113">각 공급자는 공급자에 대 한 코드 외에 클라이언트는 해당 공급자를 사용 하는 방법을 보여 주는 샘플 VS 솔루션을 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac0f9-113">In addition to the code for the provider, each provider has a sample VS solution that demonstrates how a client would use that provider.</span></span> 

* <span data-ttu-id="ac0f9-114">ADC \*\* Ads1x15 \*\* Mcp3008 \*\* Remote Arduino</span><span class="sxs-lookup"><span data-stu-id="ac0f9-114">ADC \*\* Ads1x15 \*\* Mcp3008 \*\* Remote Arduino</span></span>
* <span data-ttu-id="ac0f9-115">PWM \* \* PCA9685 \* \* Gpio를 사용 하 여 시뮬레이션 된 \* \* Remote Arduino</span><span class="sxs-lookup"><span data-stu-id="ac0f9-115">PWM \*\* PCA9685 \*\* Simulated with Gpio \*\* Remote Arduino</span></span>
* <span data-ttu-id="ac0f9-116">Gpio, SPI, I2c \* \* Remote Arduino</span><span class="sxs-lookup"><span data-stu-id="ac0f9-116">Gpio, SPI, I2c \*\* Remote Arduino</span></span>

<span data-ttu-id="ac0f9-117">실제 하드웨어에 액세스할 수 있는 공급자 외에도 만들었습니다를 [시뮬레이션 된 공급자](https://github.com/ms-iot/BusProviders/tree/develop/SimulatedProvider) inifitely 수 있는 공급자로 되었으며는 작성 하지 않고도 응용 프로그램을 디버그할 수 있도록 설계 되었습니다 처럼 할 먼저 이러한 장치에 배포 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="ac0f9-117">In addition to the providers that give you access to real hardware, we have built a [Simulated Provider](https://github.com/ms-iot/BusProviders/tree/develop/SimulatedProvider) that will act as if it was an inifitely capable provider and is designed to let you write and debug your applications without having to first deploy them to a working device.</span></span> <span data-ttu-id="ac0f9-118">보다 풍부한 환경을 수 있도록 실제 하드웨어를 시뮬레이션 하기 위해 사용자 지정할 수 있습니다. 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac0f9-118">For a richer experience, you can customize it to simulate your actual hardware.</span></span> <span data-ttu-id="ac0f9-119">예를 들어: 지정 된 슬레이브 주소를 사용 하 여 장치에서 읽는 온도 대 한 명령을 보낼 때 "75" 결과 다시 반환할 I2c 공급자를 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac0f9-119">For example: updating the I2c provider to return back the result "75" when you send it the command for a temperature reading on a device with the designated slave address.</span></span> 
