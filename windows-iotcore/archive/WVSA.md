---
title: Arduino 용 Windows 가상 실드 개요
author: saraclay
ms.author: saclayt
ms.date: 09/13/17
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: Arduino에 대 한 Windows 가상 실드를 설정 하 고 첫 번째 Windows 10 IoT Core 앱을 빌드하는 방법을 알아봅니다.
keywords: windows iot, WVSA, Windows 가상 실드, Arduino, 앱
ms.openlocfilehash: bd1dccd59fbc99de9076260f6e21b0ac1403660a
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "60169001"
---
> [!NOTE]
> 보관 된 설명서를 보고 있습니다. AllJoyn는 Windows 10 IoT에서 더 이상 지원 되지 않습니다. 질문이 있는 경우 GitHub에서 문제를 열거나 아래 설명에 의견을 남겨 주세요.

# <a name="set-up-windows-virtual-shields-for-arduino"></a>Arduino에 대 한 Windows 가상 실드 설정

## <a name="overview"></a>개요
[Arduino](https://www.arduino.cc)를 사용 하는 경우 방패 개념에 대해 잘 알고 있습니다. 각 방패는 특별 한 용도 (예: 온도 쉴드,가 속도계 방패)를 가지 며 여러 실드를 사용 하 여 장치를 빌드하는 것은 복잡 하 고, 비용이 많이 들고, 공간이 비효율적입니다. 이제 저비용의 Windows Lumia Phone을 압축 된 실드 집합으로 사용할 수 있다고 가정 합니다. Arduino 스케치는 사용 하기 쉬운 라이브러리 호출을 통해 Windows Phone에서 수많은 센서 및 기능에 액세스할 수 있습니다.

이는 개발자를 위해 Windows 가상 실드 for Arduino 라이브러리를 사용 하는 것과 정확히 일치 합니다. 가장 좋은 부분은 아닙니다 .이 기술은 모든 Windows 10 장치에서 작동 하므로 PC 또는 표면의 센서와 기능을 사용할 수 있습니다. 또한 Arduino는 음성 인식 및 웹 구문 분석과 같은 계산 부담이 큰 작업을 Windows 10 자매 장치로 오프 로드할 수 있습니다.

Arduino 용 Windows 가상 실드를 사용 하도록 하드웨어 및 소프트웨어를 설정 하는 방법에 대해 알아보겠습니다.


## <a name="1-get-your-windows-10-device-ready-for-developing-projects-using-windows-virtual-shields-for-arduino"></a>1. Windows 가상 실드 for Arduino를 사용 하 여 프로젝트를 개발할 준비가 된 Windows 10 장치를 다운로드 합니다.

자습서의이 섹션에서는 Windows 가상 실드 for Arduino 응용 프로그램을 사용 하 여 로드 하 여 원하는 Windows 10 장치를 준비 합니다 .이 유니버설 Windows 응용 프로그램을 사용 하면 Arduino 보드에 대 한 "가상 실드"로 장치를 사용할 수 있습니다.  이로 인해 작성자가 음성 인식, 터치 스크린, 상대적으로 Windows의 계산 능력을 활용할 수 있는 몇 가지 강력한 가능성이 있습니다.

### <a name="hardware"></a>하드웨어
Windows 가상 실드 for Arduino 응용 프로그램은 모든 Windows 10 장치에서 실행할 수 있지만이 자습서에서는 Windows Phone를 사용 하는 설정을 설명 합니다.

*필요한 항목* Windows 10을 실행 하는 Windows Phone- [Lumia 520](http://www.microsoft.com/en-us/mobile/phone/lumia520) 또는 [Lumia 635](http://www.microsoft.com/en-us/mobile/phone/lumia635)를 권장 합니다.

*Windows Phone 설정*

휴대폰에 아직 Windows 10이 실행 되 고 있지 않은 경우 소프트웨어의 미리 보기 버전을 설치 하는 옵션이 있습니다.  Windows Phone 8 사용자가 Microsoft Store 앱으로 이동 하 여 "Windows 참가자" 응용 프로그램을 다운로드할 수 있습니다 .이 앱을 통해 사용자는 Windows 10 Technical preview를 업데이트로 받도록 선택할 수 있습니다.  앱을 열 때 표시 되는 메시지 및 지침에 따라 휴대폰에서 Windows 10이 성공적으로 실행 되 면 계속 합니다.

### <a name="software"></a>소프트웨어

Windows Phone에 Windows 가상 실드 for Arduino UWP 앱을 설치 하는 두 가지 옵션이 있습니다.  앱을 다운로드 하는 것이 더 간단 합니다.

* Microsoft Store에서 앱 다운로드
* PC 및 Visual Studio를 사용 하 여 앱 테스트용으로 로드

*옵션 1: Microsoft Store에서 앱 다운로드*

Arduino에 대 한 Windows 가상 실드의 Microsoft Store 페이지에 대 한 [링크](https://www.microsoft.com/store/apps/9nblgggz0mld) 를 따라 응용 프로그램을 다운로드 한 다음를 설치 합니다. 그런 다음 응용 프로그램이 제대로 실행 되는지 확인 하기 위해 응용 프로그램을 열 수 있습니다.  이제 장치가 Arduino에 대 한 "가상 실드"로 사용 되도록 설정 됩니다.  다음 페이지로 진행할 수 있습니다.

*옵션 2: PC 및 Visual Studio*
를 사용 하 여 앱 테스트용으로 로드_필요한 항목_
* Visual Studio 2017는 Arduino 용 Windows 가상 실드 앱을 개발자가 잠근 휴대폰으로 테스트용으로 로드.
* Arduino 용 Windows 가상 실드 응용 프로그램에 대 한 코드를 포함 하는이 [리포지토리입니다](https://github.com/ms-iot/virtual-shields-universal) .  리포지토리를 복제 하거나 로컬 디스크에서 ZIP으로 다운로드 합니다.  Git에 익숙하지 않은 경우 적절 한 복제본을 사용 하려면 [여기](https://help.github.com/articles/cloning-a-repository)에 있는 지침을 따르세요.

_Visual Studio 2017 설정_
1. [Dev.windows.com](https://developer.microsoft.com/en-us/windows/downloads)의 Windows 10 Developer Preview 도구를 사용 하 여 Visual Studio 2017을 설치 합니다.  Visual Studio의 무료 Community 버전을 사용 하는 것이 좋지만 Enterprise와 Professional은 모두 작동 합니다.  Visual Studio가 이미 설치 되어 있는 경우 다음 단계로 건너뜁니다.
2. Visual Studio에서 위의 "필요한 항목" 섹션에 다운로드 한 리포지토리에서 실드를 로드 합니다.
3. Windows 10 장치 (이 경우 Windows Phone)가 개발자 잠금 해제 되어 있는지 확인 합니다. [이 페이지](https://msdn.microsoft.com/library/windows/apps/dn614128.aspx) 에서는 Windows Phone 8.1, 8 및 7.1의 잠금을 해제 하는 방법을 설명 합니다. 그러나 Windows 10 phone의 단계는 동일 합니다.
4. Windows 10 장치를 컴퓨터에 연결 하 고 실드 .sln 프로그램을 장치에 배포 합니다.  이렇게 하려면 "로컬 컴퓨터"에 배포 하 고 장치의 아키텍처를 "ARM"으로 설정 해야 합니다.
5. 휴대폰에서 새로 설치 된 Arduino 용 Windows 가상 실드 응용 프로그램을 실행 하 여 배포가 성공적으로 완료 되었는지 확인 합니다.  이제 Windows 10 장치가 가상 실드로 사용 되도록 설정 됩니다.

## <a name="2-set-up-your-arduino-to-use-the-windows-virtual-shields-for-arduino-library"></a>2. Arduino 라이브러리에 Windows 가상 실드를 사용 하도록 Arduino 설정 
Windows 10 자매 장치를 제대로 설정 하면 Arduino 라이브러리에 Windows 가상 실드를 사용할 수 있도록 준비 Arduino. USB, Bluetooth 또는 Wi-fi를 통해 Arduino와 Windows 10 "가상 실드" 간에 연결을 설정할 수 있습니다. 이 특정 자습서에서는 Bluetooth 연결을 사용 하 여 설치를 완료 하는 방법을 설명 하지만 다른 옵션을 사용해 보세요.

### <a name="hardware"></a>하드웨어
*필요한 항목*
* Arduino Uno 또는 호환 장치
* 와이어 연결
* Arduino 스케치를 업로드 하는 데 사용 되는 PC
* 표준 A ~ 표준 B USB-Arduino 장치에 대 한 스케치를 업로드 하는 데 필요 합니다.
* 선택 사항: Bluetooth 모듈-Bluetooth에서 연결 하도록 선택한 경우에만 필요 합니다.
* 선택 사항: Wi-fi 모듈-wi-fi로 연결 하도록 선택한 경우에만 필요 합니다.

* Arduino 설정
* 필요한 경우 Bluetooth 모듈을 준비 합니다 (Bluetooth 모듈에 헤더를 납땜 해야 할 수 있음).
* 아래에 설명 된 것과 다른 하나를 제외 하 고, [배선 다이어그램](https://learn.sparkfun.com/tutorials/using-the-bluesmirf/hardware-hookup)에 따라 Bluetooth 모듈을 Arduino에 연결 했습니다.

  * 뺀 2 및 3 대신 pin 0과 1을 사용 합니다.
    * Bluetooth TX는 핀 0 (Arduino RX 또는 RX0)에 연결 해야 합니다.
    * Bluetooth RX는 pin 1 (Arduino TX 또는 TX1)에 연결 해야 합니다.

### <a name="software"></a>소프트웨어
*필요한 항목*
* Arduino IDE 1.6 이상
* ArduinoJSON 라이브러리
* [이 리포지토리](https://github.com/ms-iot/virtual-shields-arduino)는 Arduino에서 실행 되는 예제 스케치를 포함 합니다.

*Arduino IDE 설정*
* Arduino IDE를 다운로드 하 여 설치한 후 프로그램을 시작 합니다.
* *도구 > 보드*에서 올바른 Arduino board가 선택 되어 있는지 확인 합니다.
* *도구 > 포트*에서 올바른 COM 포트가 선택 되어 있는지 확인 합니다. 보드의 이름은 각 옵션 옆에 표시 되므로 올바른 옵션을 훨씬 쉽게 선택할 수 있습니다.

*ArduinoJSON 라이브러리 설정*
* [ArduinoJson 리포지토리에서](https://github.com/bblanchon/ArduinoJson)리포지토리를 복제 하거나 zip을 다운로드 합니다.
* 라이브러리 폴더에 전체 리포지토리를 저장 합니다 (예: `Documents\Arduino\libraries\ArduinoJson\`).

*Arduino 라이브러리에 대 한 Windows 가상 실드 설정*
* [이 리포지토리](https://github.com/ms-iot/virtual-shields-arduino) 를 복제 하거나 ZIP을 다운로드 합니다. Git에 익숙하지 않은 경우 적절 한 복제본을 사용 하려면 [여기](https://help.github.com/articles/cloning-a-repository/)에 있는 지침을 따르세요.
* 방금 다운로드 한 리포지토리의 "Arduino\Libraries" 폴더에 있는 "VirtualShield" 폴더를 Arduino library 폴더 (예: `Documents\Arduino\libraries\VirtualShield\`)에 복사 합니다.

*설치 테스트*
* Arduino IDE에서 메뉴 항목 *파일-> 예제 > 가상 실드 > HelloWorld-음성 이벤트*로 이동 합니다. 이렇게 하면이 자습서에 사용 하는 Hello World을 기반으로 음성 인식을 로드 해야 합니다.
* Arduino에 스케치를 업로드 하기 전에 Arduino에서 Bluetooth TX 및 RX 와이어를 일시적으로 제거 합니다 (USB와 Bluetooth 간에는 하나의 직렬 포트만 공유 됨). Bluetooth는 업로드를 방해 합니다.
* IDE에서 "업로드" 단추를 눌러 스케치를 업로드 합니다.
* Bluetooth TX 및 RX 와이어를 Arduino 핀 (Bluetooth TX에서 Arduino RX (또는 RX0)으로, Bluetooth RX에서 Arduino TX 또는 (TX1))으로 바꿉니다.
* 이전 페이지에서 준비한 휴대폰 (또는 기타 Windows 장치)에서 Bluetooth 설정의 Arduino Bluetooth 장치에 연결 합니다. BlueSMiRF를 사용 하는 경우 기본 pin 코드는 1234입니다. 

> [!NOTE]
> BlueSMiRF에 깜박이는 빨간색 빛은 성공적으로 페어링 된 후 계속 빨간색으로 깜박입니다. 이는 예정된 동작입니다. Arduino 용 Windows 가상 실드 응용 프로그램을 연결한 후에만 녹색으로 바뀝니다.


## <a name="3-write-your-first-app-hello-blinky"></a>3. 첫 번째 앱 작성: 안녕하세요. 

### <a name="hello-world-speech-enabled-led-example"></a>Hello World 음성 사용 LED 예제
이 자습서의 이전 단계에 자세히 설명 된 대로 Windows Phone (또는 잠재적으로 Windows 10 장치!)를 사용 하 고 Arduino 준비 되었으므로 이제 샘플을 사용해 볼 수 있습니다.

1. 저항기가 있는 LED를 핀 8에 연결 하 여 Arduino 보드를 준비 합니다.
2. Arduino이 아직 HelloWorld-음성 이벤트 샘플로 업로드 되었는지 확인 한 다음 Arduino를 전원 공급 장치에 연결 합니다.
3. 이전에 준비한 Windows Phone에서 Arduino 용 Windows 가상 실드 앱을 실행 합니다.
4. 모든 것이 제대로 설정 된 경우 휴대폰은 Arduino 스케치에 연결 하 여 오디오 신호를 시작 해야 합니다. 이제 Windows 10 장치에 대 한 ' 켜기 ' 또는 ' 끄기 '를 통해 Arduino의 LED를 설정 하 고 해제할 수 있습니다.

### <a name="arduino-wiring-sketch-hello-world-example"></a>Arduino 배선 스케치: Hello World 예제

```C++
#include <ArduinoJson.h>

#include <VirtualShield.h>
#include <Text.h>
#include <Speech.h>
#include <Recognition.h>

VirtualShield shield;             // identify the shield
Text screen = Text(shield);       // connect the screen
Speech speech = Speech(shield);   // connect text to speech
Recognition recognition = Recognition(shield);    // connect speech to text

int LED_PIN = 8;

void recognitionEvent(ShieldEvent* event)
{
  if (event->resultId > 0) {
    digitalWrite(LED_PIN, recognition.recognizedIndex == 1 ? HIGH : LOW);
    screen.printAt(4, "Heard " + String(recognition.recognizedIndex == 1 ? "on" : "off"));
    recognition.listenFor("on,off", false);     // reset up the recognition after each event
  }
}

// when Bluetooth connects, or the 'Refresh' button is pressed
void refresh(ShieldEvent* event)
{
  String message = "Hello Virtual Shields. Say the word 'on' or 'off' to affect the LED";

  screen.clear();
  screen.print(message);
  speech.speak(message);

  recognition.listenFor("on,off", false);   // NON-blocking instruction to recognize speech
}

void setup()
{
  pinMode(LED_PIN, OUTPUT);
  pinMode(LED_PIN, LOW);

  recognition.setOnEvent(recognitionEvent); // set up a function to handle recognition events (turns auto-blocking off)
  shield.setOnRefresh(refresh);

  // begin() communication - you may specify a baud rate here, default is 115200
  shield.begin();
}

void loop()
{
  shield.checkSensors();            // handles Virtual Shield events.
}
```


