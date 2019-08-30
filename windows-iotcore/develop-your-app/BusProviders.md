---
title: 버스 공급자
author: msalehmsft
ms.author: msaleh
ms.date: 08/28/2017
ms.topic: article
description: Windows 10 IoT Core를 통해 제공 되는 다양 한 공급자에 대해 알아봅니다.
keywords: windows iot, 공급자, 버스 공급자, UWP, Gpio, Spi
ms.openlocfilehash: 7e2a3bf45317cd11ca558db6f1b6845e0e0f7a67
ms.sourcegitcommit: 77b86eee2bba3844e87f9d3dbef816761ddf0dd9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/11/2019
ms.locfileid: "65533277"
---
# <a name="usermode-access-to-gpio-i2c-and-spi"></a>GPIO, I2C 및 SPI에 대 한 Usermode 액세스

Windows 10에는 사용자 모드에서 직접 GPIO, I2C, SPI 및 UART에 액세스하기 위한 새로운 API가 포함되어 있습니다. Raspberry Pi 2와 같은 개발 보드는 사용자 지정 회로로 기본 컴퓨팅 모듈을 확장하여 특정 응용 프로그램을 처리할 수 있도록 하는 이러한 연결 일부를 노출합니다. 이러한 낮은 수준의 버스는 일반적으로 GPIO 핀 및 버스 일부만 헤더에 노출된 상태로 다른 중요한 온보드 기능과 공유됩니다. 시스템의 안정성을 유지하기 위해서는 사용자 모드 응용 프로그램에 의해 수정해도 안전한 핀 및 버스를 지정해야 합니다.

Windows의 낮은 수준 버스에 대한 사용자 모드 액세스는 기존 `GpioClx` 및 `SpbCx` 프레임워크를 통해 연결됩니다. Windows IoT Core 및 windows Enterprise에서 사용할 수 있는 RhProxy 라는 새 드라이버가 usermode에 `GpioClx` `SpbCx` 리소스를 노출 합니다. 이 API를 사용하도록 설정하려면 사용자 모드에 공개해야 하는 각 GPIO 및 SPB 리소스를 사용하여 ACPI 테이블에서 rhproxy에 대한 디바이스 노드를 선언해야 합니다.

RhProxy를 통한 UserMode 액세스에 대 한 추가 심층 설명서는 [여기](https://docs.microsoft.com/en-us/windows/uwp/devices-sensors/enable-usermode-access)에서 찾을 수 있습니다.

## <a name="bus-providers"></a>버스 공급자

Windows 10부터 Windows에는-soc에 있는 Gpio, Spi 또는 I2c 버스에 직접 액세스할 수 있도록 하는 기본 UWP Api가 있습니다. 이를 통해 높은 수준의 API에서이 하드웨어에 쉽게 액세스할 수 있습니다. 그러나 장치 제조업체에서 외부 soc 컨트롤러를 사용 하 여 버스에 액세스 하려고 하는 경우가 많습니다. 이는 gpio, SPI 및 I2C pin을 추가 하는 것 뿐만 아니라 PWM) 및 ADC도 지 원하는 16 개의 GPIO 핀을 추가 하는 저렴 한 칩 (예: Arduino) 만큼 간단할 수 있습니다. "Bus 공급자" 모델을 사용 하 여 개발자는 격차를 연결 하는 사용자 모드 공급자를 사용 하 여 기본 Api를 사용 하 여 이러한 외부 soc 버스에 액세스할 수 있습니다.

공급자를 작성 하는 사용자는 UWP 클래스 라이브러리에 인터페이스 집합을 구현 하 고, 해당 하드웨어와 통신 하려는 개발자는 구성 요소를 포함 하 고이에 대 한 기본 Api를 제공 합니다. [원격 Arduino 공급자](https://github.com/ms-iot/BusProviders/tree/develop/Arduino) 의 샘플 코드를 살펴보면 공급자를 구성 하는 것이 얼마나 쉬운지 확인할 수 있으며, 해당 앱에 대 한 기본 공급자로 설정 되 면 클라이언트 앱의 나머지 코드는 soc 버스에 액세스 하는 데 필요한 코드와 동일 합니다.


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

현재는 [버스 공급자](https://github.com/ms-iot/BusProviders) github 리포지토리에서 많은 공급자를 사용할 수 있습니다. 공급자의 코드 외에도 각 공급자에는 클라이언트에서 해당 공급자를 사용 하는 방법을 보여 주는 샘플 VS 솔루션이 있습니다. 

- **ADC**
  - Ads1x15
  - Mcp3008
  - 원격 Arduino

- **PWM)**
  - PCA9685
  - Gpio를 사용 하 여 시뮬레이션
  - 원격 Arduino
  
- **Gpio, SPI, I2C**
  - 원격 Arduino

실제 하드웨어에 대 한 액세스를 제공 하는 공급자 외에도, inifitely 지원 공급자 인 것 처럼 작동 하는 [시뮬레이션 된 공급자](https://github.com/ms-iot/BusProviders/tree/develop/SimulatedProvider) 를 빌드하고 먼저 응용 프로그램을에 배포 하지 않고도 응용 프로그램을 작성 하 고 디버그할 수 있도록 설계 되었습니다. 작업 장치. 더 풍부한 환경을 위해 실제 하드웨어를 시뮬레이션 하도록 사용자 지정할 수 있습니다. 예: 지정 된 슬레이브 주소를 사용 하 여 장치에서 온도 읽기에 대 한 명령을 보낼 때 I2c 공급자를 업데이트 하면 결과 "75"이 반환 됩니다.

## <a name="additional-resources"></a>추가 리소스

추가 버스 도구, 샘플 코드 및 I2C, SPI, GPIO, MinComm/UART에 대 한 빌드 및 테스트는 [여기](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/BusTools)에서 찾을 수 있습니다.

