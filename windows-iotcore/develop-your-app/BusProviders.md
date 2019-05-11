---
title: 버스 공급자
author: msalehmsft
ms.author: msaleh
ms.date: 08/28/2017
ms.topic: article
description: Windows 10 IoT Core 통해 사용할 수 있는 다양 한 공급자에 알아봅니다.
keywords: windows iot, 공급자, UWP, Gpio Spi 버스 공급자
ms.openlocfilehash: 7e2a3bf45317cd11ca558db6f1b6845e0e0f7a67
ms.sourcegitcommit: 77b86eee2bba3844e87f9d3dbef816761ddf0dd9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/11/2019
ms.locfileid: "65533277"
---
# <a name="usermode-access-to-gpio-i2c-and-spi"></a>GPIO, I2C 및 SPI 있는 Usermode 액세스

Windows 10에는 사용자 모드에서 직접 GPIO, I2C, SPI 및 UART에 액세스하기 위한 새로운 API가 포함되어 있습니다. Raspberry Pi 2와 같은 개발 보드는 사용자 지정 회로로 기본 컴퓨팅 모듈을 확장하여 특정 응용 프로그램을 처리할 수 있도록 하는 이러한 연결 일부를 노출합니다. 이러한 낮은 수준의 버스는 일반적으로 GPIO 핀 및 버스 일부만 헤더에 노출된 상태로 다른 중요한 온보드 기능과 공유됩니다. 시스템의 안정성을 유지하기 위해서는 사용자 모드 응용 프로그램에 의해 수정해도 안전한 핀 및 버스를 지정해야 합니다.

Windows의 낮은 수준 버스에 대한 사용자 모드 액세스는 기존 `GpioClx` 및 `SpbCx` 프레임워크를 통해 연결됩니다. 새 드라이버 RhProxy, Windows Enterprise, Windows IoT Core에 사용할 수 있는 호출을 노출 `GpioClx` 및 `SpbCx` usermode 리소스입니다. 이 API를 사용하도록 설정하려면 사용자 모드에 공개해야 하는 각 GPIO 및 SPB 리소스를 사용하여 ACPI 테이블에서 rhproxy에 대한 디바이스 노드를 선언해야 합니다.

RhProxy 통해 있는 UserMode 액세스 추가 심층적인 설명서를 찾을 수 있습니다 [여기](https://docs.microsoft.com/en-us/windows/uwp/devices-sensors/enable-usermode-access)합니다.

## <a name="bus-providers"></a>버스 공급자

Windows 10 부터는 Windows 했습니다 Gpio, Spi에 대 한 직접 액세스를 제공 하는 상자에서 UWP Api 또는 I2c 버스 soc.에 있는 상위 수준 API에서에서이 하드웨어에 쉽게 액세스할을 수 있습니다. 그러나 장치 제조업체는 soc 해제 컨트롤러를 사용 하 여 버스를 액세스 하려고 할 때 많은 경우가 있습니다. 16 GPIO 핀을 추가 하는 저렴 한 칩 만큼 간단 하거나 Gpio, SPI, 및 I2C 핀을 추가 하지만 또한 PWM 및 ADC 지원 뿐 아니라 (예: Arduino) 전체 MCU 만큼 다양 수 있습니다. "Bus 공급자" 모델을 사용 하 여 제공 개발자가 연결 하는 사용자 모드 공급자를 사용 하 여 기본 Api를 사용 하 여 이러한 soc 해제 버스 간격에 액세스할 수 있습니다.

공급자를 작성 중인 사용자는 UWP 클래스 라이브러리 및 하드웨어 단순히 구성 요소를 포함 하는 기본 Api에 대 한 지시와 통신할 수 있는 개발자는 다음 인터페이스 집합을 구현 합니다. 예제 코드를 살펴보면 합니다 [Remote Arduino 공급자](https://github.com/ms-iot/BusProviders/tree/develop/Arduino) 공급자를 구성 하려면 얼마나 쉬운지 볼 수 있습니다 이며, 해당 앱에 대 한 기본 공급자로 설정 되 면 나머지 클라이언트 앱의 코드 하는 데 필요한 코드와 동일을 soc에 bus 액세스 합니다.


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

## <a name="available-providers"></a>사용 가능한 공급자

사용할 수 있는 공급자의 수로 현재 우리는 [Bus 공급자](https://github.com/ms-iot/BusProviders) github 리포지토리. 각 공급자는 공급자에 대 한 코드 외에 클라이언트는 해당 공급자를 사용 하는 방법을 보여 주는 샘플 VS 솔루션을 있습니다. 

- **ADC**
  - Ads1x15
  - Mcp3008
  - Remote Arduino

- **PWM**
  - PCA9685
  - Gpio를 사용 하 여 시뮬레이션 된
  - Remote Arduino
  
- **Gpio, SPI, I2C**
  - Remote Arduino

실제 하드웨어에 액세스할 수 있는 공급자 외에도 만들었습니다를 [시뮬레이션 된 공급자](https://github.com/ms-iot/BusProviders/tree/develop/SimulatedProvider) inifitely 수 있는 공급자로 되었으며는 작성 하지 않고도 응용 프로그램을 디버그할 수 있도록 설계 되었습니다 처럼 할 먼저 이러한 장치에 배포 작업입니다. 보다 풍부한 환경을 수 있도록 실제 하드웨어를 시뮬레이션 하기 위해 사용자 지정할 수 있습니다. 합니다. 예를 들어: 지정 된 슬레이브 주소를 사용 하 여 장치에서 읽는 온도 대 한 명령을 보낼 때 "75" 결과 다시 반환할 I2c 공급자를 업데이트 합니다.

## <a name="additional-resources"></a>추가 리소스

MinComm/UART 있습니다 추가 bus 도구, 샘플 코드 및 빌드 및 테스트 I2C, SPI, GPIO [여기](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/BusTools)합니다.

