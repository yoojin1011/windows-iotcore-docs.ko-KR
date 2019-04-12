---
title: Arduino 포팅 가이드 연결
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 수정 및 Arduino 연결 하는 프로젝트를 배포할 때 발생 하는 일반적인 문제에 알아봅니다.
keywords: windows iot에 Arduino 연결, Visual Studio에서 이식
ms.openlocfilehash: 9b1d54807c21a54d8186d7f7ddabc31f16d3dab3
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512421"
---
# <a name="arduino-wiring-porting-guide"></a>Arduino 포팅 가이드 연결

라이브러리 및 배선 Arduino 스케치 Visual Studio 내에서 Arduino 연결 프로젝트로 복사/붙여넣을 하 고 Minnowboard 최대, Raspberry Pi 2 및 Raspberry Pi 3에서 실행 될 수 있습니다. 경우에 따라 개 Windows 환경과 더 호환 되도록 하기 위해 이러한 파일에 대해 필요로 하는 약간의 수정을 작업할 보드입니다. 이 가이드에서는 Arduino 연결 하는 프로젝트를 배포할 때 발생할 수 있는 일반적인 문제 뿐만 아니라 이러한 수정 사항을 설명 합니다.

## <a name="porting"></a>포팅

### <a name="updating-pins"></a>Pin 업데이트

언급 하지 않아도 당연 이동 수 있지만 많은 스케치 및 라이브러리 (특히 해당 arduino shields) Arduino 장치에 대 한 특정 커넥터 핀에 대 한 참조를 포함할 수 있습니다. 작업 중인 장치와 사용 하는 구성에 대 한 적절 한 커넥터 핀을 사용 하 여 스케치를 사용자 지정 해야 합니다.

'Pin'를 참조 하는 모든 함수에 대 한 실제 커넥터 pin 번호를 필요 궁극적으로 Arduino 연결 합니다. 이러한 번호를 직접 사용할 수 있지만 특정 보드에서 커넥터 핀에 해당 하는 몇 가지 미리 정의 된 고정 이름이 제공 했습니다.

예를 들어, Raspberry Pi 2 및 3에 있는 실제 커넥터 핀 29 라고도 `GPIO5`합니다. 다음 명령 중 하나를 사용 하 여 Raspberry Pi 2 및 3에서 높은 상태를 GPIO pin 5를 설정할 수 있습니다.
```
pinMode( 29, OUTPUT );
digitalWrite( 29, HIGH );
```

로 구분하거나 여러

```
pinMode( GPIO5, OUTPUT );
digitalWrite( GPIO5, HIGH );
```

미리 정의 된 pin 이름을 찾을 수 있습니다 [pins_arduino.h](https://github.com/ms-iot/lightning/blob/develop/source/pins_arduino.h) 했습니다 Arduino 연결 모든 프로젝트에 있지만 사용할 수 있는 다른 물리적 커넥터 핀에 대 한 작성 하는 하드웨어 설정에 따라 이후를 포함 하 고 고정 이름은 각 장치에 사용할 수 있는 설명 하기 위해 여기에서 테이블도 포함 합니다.

#### <a name="raspberry-pi-2-and-3"></a>Raspberry Pi 2 및 3

![핀아웃 다이어그램](../media/ArduinoWiringPortingGuide/RP2_Pinout.png)

> [!div class="mx-tdBreakAll"]
> | Pin 정의 | 해당 Pin 번호|
> |-------------|----------|
> | LED_BUILTIN | *온보드 LED* |
> | GPIO * _여기서 * 참조 [0, 27]_ | *핀아웃 다이어그램을 참조 하세요* |
> | GCLK | 7 |
> | 범용 * _여기서 * 참조 [0, 5]_ | * 핀아웃 다이어그램을 참조 하세요. |
> | SCL1 | 5 |
> | SDA1 | 3 |
> | CS0 (CE0 또는 SS) | 24 |
> | CS1 (또는 CE1) | 26 |
> | SCLK (또는 SCK) | 23 |
> | MISO | 21 |
> | MOSI | 19 |
> | RXD | 10 |
> | TXD | 8 |

#### <a name="minnowboard-max"></a>Minnowboard 최대

![핀아웃 다이어그램](../media/ArduinoWiringPortingGuide/MBM_Pinout.png)
> [!div class="mx-tdBreakAll"]
> | Pin 정의 | 해당 Pin 번호|
> |-------------|----------|
> | GPIO * _여기서 * 참조 [0, 9]_  | *핀아웃 다이어그램을 참조 하세요* |
> | SCL | 13 |
> | SDA | 15 |
> | CS0 (CE0 또는 SS) | 5 |
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

### <a name="cant-find-arduino-wiring-application-visual-c-project-template-in-visual-studio"></a>"Arduino 응용 프로그램 연결" 시각적 개체를 찾을 수 없습니다 C++ Visual Studio에서 프로젝트 템플릿

**원인**: Visual Studio 용 Windows IoT 프로젝트 템플릿 확장 설치 되지 않았습니다.

**해결 방법**: Visual Studio 확장에 대 한 Windows IoT 프로젝트 템플릿을 설치 해야 Visual Studio에서 프로젝트 Arduino 연결을 만들 수 있습니다. 로 이동 [Windows IoT Core 프로젝트 템플릿에 확장 페이지](https://go.microsoft.com/fwlink/?linkid=847472) Visual Studio 갤러리에서 확장을 다운로드 하려면!

### <a name="error-identifier-not-found-when-calling-a-function"></a>오류: 찾을 수 없음 "식별자" 함수를 호출 하는 경우

**원인**: 이 오류는 문서에 아직 선언 되지 않은 함수 호출 되 면 링커 프로세스 중에 발생 합니다.

**해결 방법**: C++에서 모든 함수 호출 전에 선언 되어야 합니다. 스케치 파일에서 새 함수를 정의한 경우 선언 또는 함수의 전체 구현 (일반적으로 문서 위쪽)에서 호출 하려는 모든 시도가 보다 커야 합니다.

**예**:

다음 코드 블록은 오류 발생 "'myFunction': 식별자를 찾을 수 없습니다"

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

두 가지 솔루션이 있습니다. 첫째, 위의 모든 호출 함수를 선언할 수 있습니다. 일반적으로이 선언 파일의 맨 위에 있는 이루어집니다.

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

또는 전체 구현의 위의 모든 호출 함수를 이동할 수 있습니다. 이 선언와 동시에 함수 정의의 효과가 있습니다.

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

### <a name="my-solution-hangs-infinitely-when-being-initialized"></a>필자의 솔루션 초기화 되는 경우에 무한 중단 됩니다.

알려진 문제가 발생할 수 있습니다는 C++ 무한 중단 솔루션 초기화 되는 (deadlock). 하면 영원히 중단 솔루션이 나타나고 디버거를 사용 하 여 '중단' 문에 Arduino 연결 응용 프로그램의 setup() 또는 loop () 섹션에서 수 없는 경우이 유형의 문제가 발생할 수 있습니다.

**원인**: 개체를 만들 되 또는 솔루션 초기화 완료 되기 전에 비동기 작업을 이동 하는 함수 호출 되 고 있습니다. 와 같은 API 함수를 호출 하는 개체의 생성자에서 오류로 인 `pinMode`합니다.

**해결 방법**: 개체 생성자를 이동 하 고 함수 및 코드의 초기화 섹션에서 호출 된 `setup()` 블록입니다.

**예 1**:

호출 된 함수를 호출 하는이 스케치 실행 `setPinModes()` 솔루션 자체 초기화 되기 전에 합니다. 솔루션 실행 되지만를 표시 하는 무한 중단 합니다.

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

아래 솔루션은를 실행 하기만 하면 옮겼습니다 `setPinModes()` 에 `setup()` 함수:

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

이 스케치를 실행 하기 전에 스택에서 개체를 만듭니다 `setup()` 가 호출 되었습니다. 개체 호출 이후 `pinMode` 생성자를 통해이 또한는 교착 상태가 발생 합니다. 일반적이 지 않은 문제가 이지만 특정 라이브러리에서 개체를 사용 하 여 발생할 수 있습니다 (에서 Arduino 같은 `LiquidCrystal` 라이브러리)입니다.

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

솔루션에는 다음과 같습니다. 개체는 개체 포인터에 대 한 변경 되 고 개체를 초기화 하는 이동 되었습니다 `setup()`합니다.

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

### <a name="using-serialprint-and-serialprintln"></a>사용 하 여 `Serial.print()` 및 `Serial.println()`

많은 Arduino 스케치 사용 `Serial` (열) 하는 경우 직렬 콘솔에 데이터를 인쇄 하거나 (USB 또는 tx/rx) 직렬 회선에 쓸 수 있습니다. 하드웨어 번개 SDK의 이전 버전에서 `Serial` 지원의 제공 것 들이 포함 되지 않은 `Log()` 디버거를 인쇄 하는 함수 출력 Visual Studio의 창. `Serial.print*()` 또는 `Serial.write()` 제거 되었습니다.

그러나부터 _번개 SDK v1.1.0_를 추가 했습니다 `Hardware Serial` 지원과 둘 다 `Serial.print*()` 또는 `Serial.write()` 함수 완전히 지원 됩니다. 따라서 Arduino 용으로 빌드된 스케치를 복사 하는 경우 Windows IoT 버전 스케치에서 직렬 이러한 참조 중 하나를 바꿀 필요가 없습니다.

또한의 기능을 확장 한 것 `Serial.print()` 및 `Serial.println()`, 하드웨어 직렬 핀에 작성 하는 것 외에도-는 디버거가 연결 될 때 디버거 창에 출력 합니다.
디버그 인쇄 출력 집합 출력 때 사용할 대부분의 사용자는 읽기 이후 기본적으로 실행 중인 해당 스케치 합니다. 그러나 기능을 사용할 수도; 예: 성능 향상을 위해 호출 `Serial.enablePrintDebugOutput(false);` 스케치가 사용 하지 않도록 설정 합니다. 다시 사용 하려면 호출 `Serial.enablePrintDebugOutput(true);`합니다. 하드웨어 직렬 핀에 쓰기 호출을 받지 않습니다.

Note 출력이 디버거 창에 전송 하는 FTDI 같은 직렬 핀에는 모든 주변 장치를 연결할 필요가 없습니다. 그러나 응용 프로그램이 디버깅 되 고 하는 동안 디버거 창을 열려 있는지 확인 해야 합니다.

![디버거 출력](../media/ArduinoWiringPortingGuide/debugger_output.png)

업데이트 된 프로젝트 템플릿 합니다 [Windows IoT Core 프로젝트 템플릿에 확장 페이지](https://go.microsoft.com/fwlink/?linkid=847472) 하드웨어를 사용 하도록 설정 하려면 `Serial` 즉시 합니다. 그러나 Arduino 연결 응용 프로그램에 이미 생성 된 경우 이전 프로젝트 템플릿 버전을 사용 해야 1) 최신 번개 sdk 프로젝트를 업그레이드 하려면 v1.1.0 이상, 2)에 필요한 하드웨어 직렬 장치 기능이 추가 프로그램 사용할 수 있게 되기를 AppxManifest `Serial`합니다.

### <a name="hardware-serial-device-capability-requirements"></a>하드웨어 직렬 장치 기능 요구 사항

Windows 10 IoT Core 하드웨어 직렬 기능 AppX 매니페스트에 추가 하는 장치 기능 선언에 필요 합니다.

파일을 찾을 `Package.appxmanifest` 솔루션 탐색기에서 파일 이름을 입력 하 여 프로젝트에서. 그런 다음, 파일을 마우스 오른쪽 단추로 클릭 하 고 프로그램을 선택 '...'. 'XML (텍스트) 편집기'를 선택 하 고 [확인]을 클릭 합니다.

![Package.appxmanifest를 업데이트 하는 중](../media/ArduinoWiringPortingGuide/appxmanifest_search.png)

Appx 매니페스트 파일 편집기에서 추가 된 `serialcommunication` DeviceCapability 다음 XML 조각에서와 같이 프로젝트:

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

### <a name="upgrade-your-project-to-the-latest-lightning-sdk"></a>프로젝트가 최신 번개 SDK로 업그레이드

Arduino 연결 프로젝트에 따라 달라 집니다를 [번개 SDK Nuget 패키지](https://www.nuget.org/packages/Microsoft.IoT.Lightning/) 에서는 필요한 Arduino 연결 기능 및 선언으로 번개 드라이버를 사용 하 여 인터페이스를 구현 합니다. 최신 번개 SDK에는 최신 기능 향상 및 버그 수정 포함 됩니다. 최신 번개 SDK를 업그레이드 하려면 다음이 단계를 수행 합니다.

- 솔루션 탐색기에서 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 Nuget 패키지 관리 '를 클릭 합니다.
- NuGet 패키지 관리자에서 '설치 됨' 탭으로 이동 합니다. 설치 Microsoft.IoT.Lightning 패키지 표시
- 'Version' 콤보 상자 내에서 사용 가능한 버전에 나열 됩니다.
- 최신 버전을 선택 하 고 패키지를 업데이트 하려면 ' 업데이트'를 클릭 합니다.
- 시험판 버전으로 업그레이드 하 고 지 확인란 시험판 포함'도 해야 합니다.

![NuGet 패키지 관리자](../media/ArduinoWiringPortingGuide/Nuget_PackageManager.png)
