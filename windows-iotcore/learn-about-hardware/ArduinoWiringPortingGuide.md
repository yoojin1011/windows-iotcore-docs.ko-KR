---
title: Arduino 배선 포팅 가이드
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Arduino 배선 프로젝트를 배포할 때 발생 하는 수정 사항 및 일반적인 문제에 대해 알아봅니다.
keywords: windows iot, Arduino, 배선, Visual Studio, 포팅
ms.openlocfilehash: 9b1d54807c21a54d8186d7f7ddabc31f16d3dab3
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "60170031"
---
# <a name="arduino-wiring-porting-guide"></a>Arduino 배선 포팅 가이드

Arduino 배선 스케치와 라이브러리를 Visual Studio 내부의 Arduino 배선 프로젝트에 복사/붙여 넣고 Raspberry Pi 2, Raspberry Pi 3 또는 Minnowboard Max에서 실행할 수 있습니다. Windows 환경 또는 작업 중인 보드와의 호환성을 위해 이러한 파일을 변경 해야 하는 경우가 가끔 있습니다. 이 가이드에서는 Arduino 배선 프로젝트를 배포할 때 발생할 수 있는 일반적인 문제 및 이러한 수정 사항을 다룹니다.

## <a name="porting"></a>포팅

### <a name="updating-pins"></a>Pin 업데이트

이 경우를 몰라도 되지만 많은 스케치와 라이브러리 (특히 arduino 실드의 경우)에는 Arduino 장치에 대 한 특정 커넥터 핀에 대 한 참조가 포함 될 수 있습니다. 작업 중인 장치와 사용 중인 구성에 적절 한 커넥터 pin을 사용 하도록 스케치를 사용자 지정할 수 있습니다.

Arduino 와이어링은 궁극적으로 ' 핀 '을 참조 하는 모든 함수에 대 한 실제 커넥터 pin 번호가 필요 합니다. 이러한 숫자를 직접 사용할 수 있지만 특정 보드의 커넥터 핀에 해당 하는 미리 정의 된 pin 이름을 제공 했습니다.

예를 들어, Raspberry Pi 2 및 3 `GPIO5`에 대 한 실제 커넥터 29는 라고도 합니다. 다음 명령 중 하나를 사용 하 여 Raspberry Pi 2 및 3에서 GPIO pin 5를 높은 상태로 설정할 수 있습니다.
```
pinMode( 29, OUTPUT );
digitalWrite( 29, HIGH );
```

로 구분하거나 여러

```
pinMode( GPIO5, OUTPUT );
digitalWrite( GPIO5, HIGH );
```

미리 정의 된 pin 이름은 pins_arduino에서 찾을 수 있으며 모든 Arduino 배선 프로젝트에 포함 될 수 있지만, 빌드 중인 하드웨어 설정에 따라 사용할 수 있는 다른 실제 커넥터 pin이 있으므로 테이블도 포함 되어 있습니다 [.](https://github.com/ms-iot/lightning/blob/develop/source/pins_arduino.h) 각 장치에 사용할 수 있는 pin 이름을 설명 합니다.

#### <a name="raspberry-pi-2-and-3"></a>Raspberry Pi 2 및 3

![핀아웃 다이어그램](../media/ArduinoWiringPortingGuide/RP2_Pinout.png)

> [!div class="mx-tdBreakAll"]
> | Pin 정의 | 해당 Pin 번호|
> |-------------|----------|
> | LED_BUILTIN | *온보드 LED* |
> | GPIO * _여기서 *는 [0, 27]을 참조 합니다_ . | *핀아웃 다이어그램 참조* |
> | GCLK | 7 |
> | GEN * _여기서 *는 [0, 5]를 참조 합니다_ . | \* 핀아웃 다이어그램 참조 |
> | SCL1 | 5 |
> | SDA1 | 3 |
> | CS0 (또는 CE0 또는 SS) | 24 |
> | CS1 (또는 CE1) | 26 |
> | SCLK (또는 SCK) | 23 |
> | MISO | 21 |
> | MOSI | 19 |
> | RXD | 10 |
> | 트랜잭션 | 8 |

#### <a name="minnowboard-max"></a>Minnowboard Max

![핀아웃 다이어그램](../media/ArduinoWiringPortingGuide/MBM_Pinout.png)
> [!div class="mx-tdBreakAll"]
> | Pin 정의 | 해당 Pin 번호|
> |-------------|----------|
> | GPIO * _여기서 *은 [0, 9]를 참조 합니다_ .  | *핀아웃 다이어그램 참조* |
> | SCL | 13 |
> | SDA | 15 |
> | CS0 (또는 CE0 또는 SS) | 5 |
> | SCLK (또는 SCK)| 11 |
> | MISO |7 |
> | MOSI | 9 |
> | CTS1 | 10 |
> | RTS1 | 12 |
> | RX1 | 8 |
> | TX1 | 6 |
> | RX2 | 19 |
> | TX2 | 17 |


## <a name="common-problems"></a>일반적인 문제

### <a name="cant-find-arduino-wiring-application-visual-c-project-template-in-visual-studio"></a>Visual Studio에서 "Arduino 배선 응용 프로그램 C++ " 시각적 프로젝트 템플릿을 찾을 수 없습니다.

**원인**: Visual Studio 용 Windows IoT 프로젝트 템플릿 확장이 설치 되어 있지 않습니다.

**해결 방법**: Visual Studio에서 Arduino 배선 프로젝트를 만들려면 먼저 Windows IoT 용 Visual Studio 확장 프로젝트 템플릿을 설치 해야 합니다. [Windows IoT Core 프로젝트 템플릿 확장 페이지로](https://go.microsoft.com/fwlink/?linkid=847472) 이동 하 여 Visual Studio 갤러리에서 확장을 다운로드 합니다.

### <a name="error-identifier-not-found-when-calling-a-function"></a>오류: 함수를 호출 하는 동안 "식별자를 찾을 수 없습니다."

**원인**: 이 오류는 문서에서 아직 선언 되지 않은 함수를 호출할 때 링커 프로세스 중에 발생 합니다.

**해결 방법**: 에서는 C++모든 함수를 호출 하기 전에 선언 해야 합니다. 스케치 파일에 새 함수를 정의한 경우 함수를 호출 하는 데 필요한 선언 또는 전체 구현에서이 함수를 호출 해야 합니다 (일반적으로 문서 맨 위).

**예**:

다음 코드 블록은 "' myFunction ': 식별자를 찾을 수 없음" 오류를 발생 시킵니다.

```
void setup()
{

}

void loop()
{
    myFunction();
}

void myFunction()
{
    //do something
}
```

두 가지 솔루션이 있습니다. 먼저 모든 호출 위에 함수를 선언할 수 있습니다. 일반적으로이 선언은 파일 위쪽에서 수행 됩니다.

```C++
// Declare function here
void myFunction();

void setup()
{

}

void loop()
{
    myFunction();
}

// And, define the function here
void myFunction()
{
    //do something
}
```

또는 함수의 전체 구현을 모든 호출 위로 이동할 수 있습니다. 이 경우 함수를 동시에 선언 하 고 정의 하는 효과가 있습니다.

```C++
void setup()
{
}

void myFunction()
{
    //do something
}

void loop()
{
    myFunction();
}
```

### <a name="my-solution-hangs-infinitely-when-being-initialized"></a>초기화 될 때 내 솔루션이 무한히 중단 됨

초기화 될 때 C++ 솔루션이 무한히 중단 (교착 상태)을 일으킬 수 있는 알려진 문제가 있습니다. 솔루션이 중단 된 것 처럼 보이고 디버거를 사용 하 여 Arduino 배선 응용 프로그램의 setup () 또는 loop () 섹션에 있는 모든 문에 ' 중단 ' 하는 경우이 문제가 발생할 수 있습니다.

**원인**: 솔루션의 초기화가 완료 되기 전에 asyncronous 작업을 수행 하는 함수가 생성 되거나 함수가 호출 되 고 있습니다. 개체의 생성자가와 같은 `pinMode`API 함수를 호출 하는 경우에 발생할 수 있습니다.

**해결 방법**: 모든 개체 생성자 및 함수 호출을 코드의 초기화 섹션과 `setup()` 블록으로 이동 합니다.

**예 1**:

이 스케치의 실행은 솔루션 자체가 초기화 되기 `setPinModes()` 전에 호출 되는 함수를 호출 합니다. 솔루션이 실행 되는 것 처럼 보이지만 무한히 중단 됩니다.

```C++
bool setPinModes();

int pin = GPIO5;
bool initialized = setPinModes();

void setup()
{

}

void loop()
{
    if( initialized )
    {
        //do something
    }
}

bool setPinModes()
{
    if( pin < 0 ) return false;
    pinMode( pin, OUTPUT );
    return true;
}
```

이 솔루션은 아래와 같이 단순히 실행 `setPinModes()` `setup()` 을 함수로 이동 했습니다.

```C++
bool setPinModes();

int pin = GPIO5;
bool initialized;

void setup()
{
    initialized = setPinModes();
}

void loop()
{
    if( initialized )
    {
        //do something
    }
}

bool setPinModes()
{
    if( pin < 0 ) return false;
    pinMode( pin, OUTPUT );
    return true;
}
```

**예 2**:

이 스케치를 실행 하면가 호출 되기 전에 `setup()` 스택에서 개체가 만들어집니다. 개체는 생성자에서 `pinMode` 를 호출 하므로 교착 상태가 발생 하기도 합니다. 이러한 문제는 드문 경우 지만 특정 라이브러리 (예: Arduino `LiquidCrystal` 라이브러리)의 개체에 발생할 수 있습니다.

```C++
class MyObject
{
public:
    MyObject()
    {
        pinMode( GPIO5, OUTPUT );
    }

    void doSomething()
    {
        //... 
    }
};

MyObject myObject;

void setup()
{
}

void loop()
{
    myObject.doSomething();
}
```

해결 방법은 다음과 같습니다. 개체를 개체 포인터로 변경 하 고 개체 초기화를로 `setup()`이동 했습니다.

```C++
class MyObject
{
public:
    MyObject()
    {
        pinMode( GPIO5, OUTPUT );
    }

    void doSomething()
    {
        //... 
    }
};

MyObject *myObject;

void setup()
{
    myObject = new MyObject();
}

void loop()
{
    myObject->doSomething();
}
```

### <a name="using-serialprint-and-serialprintln"></a>및 `Serial.print()` 사용`Serial.println()`

많은 Arduino 스케치는 `Serial` 데이터를 직렬 콘솔에 인쇄 하거나 (열려 있는 경우) 직렬 회선 (USB 또는 tx/rx)에 쓰는 데 사용 합니다. 이전 버전의 라이트닝 SDK에서는 하드웨어 `Serial` 지원이 포함 되지 않았기 때문에 Visual Studio의 디버거 출력 창에 인쇄 되는 `Log()` 함수를 제공 했습니다. `Serial.print*()`또는 `Serial.write()` 를 제거 해야 했습니다.

그러나 _라이트닝 SDK v 1.1.0_부터 지원을 추가 `Hardware Serial` 하 고 또는 `Serial.write()` 함수를 모두 `Serial.print*()` 완전히 지원 합니다. 따라서 Arduino에 대해 빌드된 스케치를 복사 하는 경우에는 Windows IoT 버전의 스케치에서 이러한 직렬 참조를 바꿀 필요가 없습니다.

또한 및의 `Serial.print()` 기능을 확장 하 고, `Serial.println()`디버거가 연결 될 때 디버거 창에 출력 하 고, 하드웨어 직렬 핀에 쓰기를 추가 합니다.
디버그 출력은 해당 출력을 읽을 때 대부분의 사용자가 해당 스케치를 실행할 때 사용할 수 있는 것 이므로 기본값으로 설정 됩니다. 그러나이 기능을 사용 하지 않도록 설정할 수도 있습니다. 예를 들어 성능을 향상 시키려면를 호출 `Serial.enablePrintDebugOutput(false);` 하 여 스케치에서 사용 하지 않도록 설정 하면 됩니다. 다시 사용 하도록 설정 하려면를 호출 `Serial.enablePrintDebugOutput(true);`합니다. 하드웨어 직렬 pin에 대 한 쓰기는 해당 호출의 영향을 받지 않습니다.

디버거 창으로 전송 되는 출력을 가져오기 위해 FTDI와 같은 직렬 핀에는 주변 장치를 연결할 필요가 없습니다. 그러나 응용 프로그램을 디버깅 하는 동안 디버거 창이 열려 있는지 확인 해야 합니다.

![디버거 출력](../media/ArduinoWiringPortingGuide/debugger_output.png)

기본 하드웨어 `Serial` 를 사용할 수 있도록 [Windows IoT Core 프로젝트 템플릿 확장 페이지](https://go.microsoft.com/fwlink/?linkid=847472) 에서 프로젝트 템플릿이 업데이트 되었습니다. 그러나 이전 프로젝트 템플릿 버전을 사용 하 여 Arduino 배선 응용 프로그램을 이미 만든 경우에는 1) 프로젝트를 최신 번개 SDK, v 1.1.0 이상으로 업그레이드 하 고 2) 필요한 하드웨어 직렬 장치 기능을에 추가 해야 합니다. 사용할 `Serial`수 있는 appxmanifest.xml입니다.

### <a name="hardware-serial-device-capability-requirements"></a>하드웨어 직렬 장치 기능 요구 사항

Windows 10 IoT Core의 하드웨어 직렬 기능을 사용 하려면 장치 기능 선언이 AppX 매니페스트에 추가 되어야 합니다.

솔루션 탐색기에서 `Package.appxmanifest` 파일 이름을 입력 하 여 프로젝트에서 파일을 찾습니다. 그런 다음 파일을 마우스 오른쪽 단추로 클릭 하 고 ' 연결 프로그램 ... '을 선택 합니다. ' XML (텍스트) 편집기 '를 선택 하 고 ' 확인 '을 클릭 합니다.

![Appxmanifest.xml를 업데이트 하는 중](../media/ArduinoWiringPortingGuide/appxmanifest_search.png)

Appx 매니페스트 파일 편집기에서 다음 XML 코드 조각과 `serialcommunication` 같이 DeviceCapability를 프로젝트에 추가 합니다.

```xml
<Capabilities>
  <Capability Name="internetClient" />

  <!-- General Arduino Wiring required capabilities -->
  <iot:Capability Name="lowLevelDevices" />
  <DeviceCapability Name="109b86ad-f53d-4b76-aa5f-821e2ddf2141"/>

  <!-- The serialcommunication capability is required to access Hardware Serial. --> 
  <DeviceCapability Name="serialcommunication">
    <Device Id="any">
      <Function Type="name:serialPort"/>
    </Device>
  </DeviceCapability>

</Capabilities>
```

### <a name="upgrade-your-project-to-the-latest-lightning-sdk"></a>프로젝트를 최신 번개 SDK로 업그레이드

Arduino 배선 프로젝트는 라이트닝 [SDK Nuget 패키지](https://www.nuget.org/packages/Microsoft.IoT.Lightning/) 를 사용 하 여 필요한 Arduino 배선 함수 및 선언 뿐만 아니라 번개 드라이버로의 인터페이스를 구현 합니다. 최신 라이트닝 SDK에는 최신 향상 된 기능 및 버그 수정이 포함 됩니다. 최신 라이트닝 SDK로 업그레이드 하려면 다음 단계를 수행 합니다.

- 솔루션 탐색기에서 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 ' Nuget 패키지 관리 ... '를 클릭 합니다.
- NuGet 패키지 관리자에서 ' 설치 됨 ' 탭으로 이동 합니다. 설치 된 Microsoft. a. a. a.
- 사용 가능한 버전이 ' 버전 ' combobox 안에 나열 됩니다.
- 최신 버전을 선택 하 고 ' 업데이트 '를 클릭 하 여 패키지를 업데이트 합니다.
- 시험판 버전으로 업그레이드 하려면 ' 시험판 포함 ' 확인란을 선택 해야 합니다.

![NuGet 패키지 관리자](../media/ArduinoWiringPortingGuide/Nuget_PackageManager.png)
