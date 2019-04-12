---
title: Windows 가상 Shields Arduino 개요
author: saraclay
ms.author: saclayt
ms.date: 09/13/17
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: Arduino에 대 한 Windows 가상 Shields 설정 하 여 첫 번째 Windows 10 IoT Core 앱을 구축 하는 방법을 알아봅니다.
keywords: windows iot, WVSA, Windows 가상 방패, Arduino, 앱
ms.openlocfilehash: bd1dccd59fbc99de9076260f6e21b0ac1403660a
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513174"
---
> [!NOTE]
> 보관 된 설명서가 표시 됩니다. Windows 10 IoT에서 더 이상 AllJoyn 사용할 수 없습니다. 질문에 대 한 GitHub에서 문제를 제기 하거나 아래 설명에 의견을 남길 하세요.

# <a name="set-up-windows-virtual-shields-for-arduino"></a>Windows 가상 Shields Arduino에 대 한 설정

## <a name="overview"></a>개요
사용한 경우는 [Arduino](https://www.arduino.cc), 방어막의 개념에 익숙할 것입니다. 각 보호 특수 용도 (예:는 온도 shield는가 속도계 방패), 있으며 복잡 하 고, 비용이 많이 들며, 공간 비효율적인 수 여러 방패 표시를 사용 하 여 장치를 구축 합니다. 이제 사용할 수 있는 저렴 한 비용 Windows Lumia 휴대폰 shields의 간단한 집합으로 가정해 보겠습니다. 사용자가 Arduino 스케치에 수백 달러 가치가 센서에 Windows Phone 기능을 사용 하기 쉬운 라이브러리 호출을 통해 액세스할 수 있게 됩니다.

이것이 개발자를 위한 덕분에 Arduino 라이브러리에 대 한 Windows 가상 Shields입니다. 가장 중요 한 부분 없는-고이 기술이 작동 하는 모든 Windows 10 장치에서 사용할 수 있도록 기능과 센서 PC 또는 Surface도 합니다. 또한에서 Arduino 음성 인식 및 Windows 10 포함 장치를 구문 분석 하는 웹과 같은 계산 비용이 많이 드는 작업을 오프 로드할 수 있습니다!

하드웨어 및 소프트웨어를 Windows 가상 Shields Arduino에 대 한 작업을 설정 하는 방법을 알아보겠습니다.


## <a name="1-get-your-windows-10-device-ready-for-developing-projects-using-windows-virtual-shields-for-arduino"></a>1. Windows 가상 Shields를 사용 하 여 Arduino에 대 한 프로젝트를 개발 하기 위한 준비 된 Windows 10 장치를 가져옵니다.

자습서의이 섹션에서는 Arduino 응용 프로그램에 대 한 Windows 가상 Shields를 사용 하 여 로드 하 여 원하는 Windows 10 장치 준비-이 유니버설 Windows 응용 프로그램을 Arduino 보드에 대 한 "가상 방패"으로 장치를 사용할 수 있습니다.  이 인해 결정권자 음성 인식 기능을 활용할 수 있도록 몇 가지 강력한 가능성에 상대적인 편의성에 화면 및 Windows의 계산 능력을 터치 합니다.

### <a name="hardware"></a>하드웨어
Arduino 응용 프로그램에 대 한 Windows 가상 Shields는 모든 Windows 10 장치에서 실행할 수는 있지만이 자습서에서는 Windows Phone 사용 하 여 설치에 설명 합니다.

*필요한* Windows Phone 좋습니다-Windows 10을 실행 합니다 [Lumia 520](http://www.microsoft.com/en-us/mobile/phone/lumia520) 또는 [Lumia 635](http://www.microsoft.com/en-us/mobile/phone/lumia635)합니다.

*에 Windows Phone 설정*

휴대폰 이미 Windows 10를 실행 하지 않는 경우 미리 보기 버전의 소프트웨어를 설치 하는 옵션이 있습니다.  Windows Phone 8 사용자가 "Windows Insider" 응용 프로그램을 다운로드 하려면 Microsoft Store 앱을 이동할 수-이 앱이 Windows 10 Technical Preview로 업데이트 수신을 선택할 수 있습니다.  프롬프트 및 앱을 열 때 지침을 따르고 휴대폰 성공적으로 Windows 10을 실행 한 후 계속 합니다.

### <a name="software"></a>소프트웨어

Windows Phone Arduino UWP 앱에 대 한 Windows 가상 Shields 설치에 대 한 두 가지 옵션이 있습니다.  앱을 다운로드 하는 보다 쉽게, 더 빠른 좋습니다.

* Microsoft Store 앱을 다운로드 합니다.
* PC 및 Visual Studio를 사용 하 여 앱을 테스트용으로 로드

*옵션 1: Microsoft Store 앱을 다운로드 합니다.*

이 따라 [링크](https://www.microsoft.com/store/apps/9nblgggz0mld) Arduino에 대 한 가상 Shields Windows에 대 한 Microsoft Store 페이지로 응용 프로그램을 다운로드 및 설치 합니다. 응용 프로그램이 제대로 실행 되도록 응용 프로그램을 열 수 있습니다.  장치의는 Arduino에 대 한 "가상 방패"로 사용할 설치 되었습니다.  다음 페이지로 진행할 수 있습니다.

*옵션 2: PC 및 Visual Studio를 사용 하 여 앱을 테스트용으로 로드*
_해야 하는 작업_
* 개발자 잠금 해제 된 휴대폰으로 Arduino 앱에 대 한 Windows 가상 Shields 테스트용으로 로드 하려면 visual Studio 2017.
* 이렇게 [리포지토리](https://github.com/ms-iot/virtual-shields-universal) Arduino 응용 프로그램에 대 한 Windows 가상 Shields에 대 한 코드를 포함 합니다.  리포지토리 복제 또는 로컬 디스크에 ZIP으로 다운로드 합니다.  적절 한 복제 작업을 수행 하 고 git를 사용 하 여 잘 모르는 경우 지침을 따릅니다 [여기](https://help.github.com/articles/cloning-a-repository)합니다.

_Visual Studio 2017 설정_
1. Windows 10 개발자 미리 보기 도구를 사용 하 여 Visual Studio 2017 설치 [dev.windows.com](https://developer.microsoft.com/en-us/windows/downloads)합니다.  무료 커뮤니티 버전의 Visual Studio에서 권장 되지만 Enterprise 및 Professional도 작동 합니다.  설치 된 Visual Studio에 이미 있는 경우 다음 단계를 건너뜁니다.
2. Visual Studio에서 부하 리포지토리에서 Shield.sln에는 "필요한"에서 다운로드 하는 한 위 섹션입니다.
3. (이 경우에는 Windows Phone)에서 Windows 10 장치는 개발자 잠금 해제를 확인 합니다. [하지만이 페이지](https://msdn.microsoft.com/library/windows/apps/dn614128.aspx) Windows Phone 8.1, 8 및 7.1; 잠금을 해제 하는 방법에 설명 단계는 동일한 Windows 10 phone 용입니다.
4. Windows 10 장치를 컴퓨터에 연결 하 고 장치의 Shield.sln 프로그램을 배포 합니다.  이 위해 "로컬 컴퓨터"에 배포 하 고 장치 "ARM"로 아키텍처를 설정 해야 합니다.
5. Windows 배포 되도록 휴대폰 Arduino 응용 프로그램에 대 한 가상 Shields는 새로 설치 된 실행 성공 했습니다.  Windows 10 장치의 가상 방어막으로 사용 하도록 설정 되었습니다!

## <a name="2-set-up-your-arduino-to-use-the-windows-virtual-shields-for-arduino-library"></a>2. Arduino 라이브러리에 대 한 Windows 가상 방패 표시를 사용 하 여 Arduino 설정 
Windows 10 관련 장치를 사용 하 여 제대로 설정, Arduino 라이브러리에 대 한 Windows 가상 방패 표시를 사용 하 여 Arduino 살펴보겠습니다. USB, Bluetooth 또는 Wi-fi에 Arduino 및 Windows 10 "가상 방패" 간의 연결을 설정할 수 있습니다. 이 특정 자습서 Bluetooth 연결을 사용 하 여 설치를 완료 하는 방법에 설명 하지만 다른 옵션을 사용해 자유롭게 됩니다.

### <a name="hardware"></a>하드웨어
*필요한 것*
* Arduino Uno 또는 호환 되는 장치
* 와이어를 연결합니다.
* PC에 Arduino 스케치를 업로드 하는 데 사용
* 표준 장치의 Arduino 스케치를 업로드 하는 데 필요한 표준 B USB-A
* 선택 사항: Bluetooth 모듈-Bluetooth 하 여 연결 하려는 경우에 필요 합니다.
* 선택 사항: -Fi 모듈--fi 하 여 연결 하려는 경우에 필요 합니다.

* 에 Arduino 설정
* (Bluetooth 모듈 야 할 수도 납땜 헤더) 필요한 경우 Bluetooth 모듈을 준비 합니다.
* 제외 하 고 다른 아래 나와 있는, Bluetooth 모듈 당 Arduino에 연결 [배선 다이어그램이](https://learn.sparkfun.com/tutorials/using-the-bluesmirf/hardware-hookup)합니다.

  * 차이점: 대신 2 및 3 핀 0과 1을 사용 합니다.
    * Bluetooth TX 핀 0 (Arduino RX 또는 RX0)에 연결 해야 합니다.
    * Bluetooth RX (Arduino TX 또는 TX1) 1 핀에 연결 해야 합니다.

### <a name="software"></a>소프트웨어
*필요한 것*
* Arduino IDE 버전 1.6 이상
* ArduinoJSON 라이브러리
* [이 리포지토리에](https://github.com/ms-iot/virtual-shields-arduino),이 Arduino에서 실행 하는 예제 스케치를 포함 하는 합니다.

*Arduino IDE 설정*
* 다운로드 하 고 Arduino IDE 설치 프로그램을 시작 합니다.
* 올바른 Arduino 보드에서 선택 했는지 확인 하십시오 *도구 > 보드*합니다.
* 아래에서 선택 되는 올바른 COM 포트가 있는지 확인 하십시오 *도구 > 포트*합니다. 보드의 이름을 쉽게 올바른 옵션을 선택 하는 각 옵션에 옆에 표시 됩니다.

*ArduinoJSON 라이브러리 설정*
* [ArduinoJson 리포지토리](https://github.com/bblanchon/ArduinoJson), 리포지토리를 복제 하거나 zip을 다운로드 합니다.
* 전체 저장소 라이브러리 폴더에 배치 (즉, `Documents\Arduino\libraries\ArduinoJson\`).

*Windows 가상 Shields Arduino 라이브러리에 대 한 설정*
* 클론 [이 리포지토리](https://github.com/ms-iot/virtual-shields-arduino) 또는 ZIP을 다운로드 합니다. 적절 한 복제 작업을 수행 하 고 git를 사용 하 여 잘 모르는 경우 지침을 따릅니다 [여기](https://help.github.com/articles/cloning-a-repository/)합니다.
* "VirtualShield" 폴더를 복사, Arduino 라이브러리 폴더에 방금 다운로드 한 리포지토리의 "Arduino\Libraries" 폴더에 있는 (즉, `Documents\Arduino\libraries\VirtualShield\`).

*설정 테스트*
* Arduino IDE에서 메뉴 항목으로 이동 *파일에는 예제-> 가상 방패-> HelloWorld-음성-이벤트->* 합니다. 이이 자습서에서는 기반 음성 인식 Hello World 예제를 로드 해야 합니다.
* 하 여 Arduino 스케치를 업로드 하기 전에 일시적으로 (하나씩만 있기 USB 및 Bluetooth-Bluetooth 간에 공유 되는 직렬 포트 업로드 방해) Arduino에서 Bluetooth TX 및 RX 와이어를 제거 합니다.
* IDE의 "업로드" 단추를 눌러 스케치를 업로드 합니다.
* Bluetooth TX 및 RX 와이어 Arduino pin으로 바꿉니다 (Arduino RX (또는 RX0) TX Bluetooth 및 Bluetooth Arduino tx RX 또는 (TX1)).
* 휴대폰 (또는 다른 Windows 장치) 쌍 Bluetooth 장치에서 Bluetooth 설정 프로그램 Arduino에 이전 페이지에서 준비 합니다. 기본 pin 코드를 BlueSMiRF를 사용 하는 경우 1234입니다. 

> [!NOTE]
> 깜박이 빨간색 표시등은 BlueSMiRF 빨간색으로 성공한 연결 후 깜박임 계속 합니다. 이는 예정된 동작입니다. 만 하면 녹색으로 Arduino 응용 프로그램에 대 한 Windows 가상 Shields를 사용 하 여 연결한 후 합니다.


## <a name="3-write-your-first-app-hello-blinky"></a>3. 첫 번째 앱을 작성 합니다. Hello, 쳐다! 

### <a name="hello-world-speech-enabled-led-example"></a>Hello World 음성 지원 LED 예제
Windows Phone 사용자 (또는 잠재적으로 모든 Windows 10 장치!)를 사용 하 여이 자습서의 이전 단계에서 설명한 대로 준비 하 여 Arduino, 이제 샘플을 시도 하 고 있습니다.

1. 핀 8 저항기를 사용 하 여 LED를 연결 하 여 Arduino 보드를 준비 합니다.
2. 에 Arduino 이벤트-음성-HelloWorld 샘플을 계속 업로드 되는 있는지 확인 하 고는 Arduino 전원 공급 장치를 연결 합니다.
3. 이전에 준비한 Windows Phone Arduino 앱에 대 한 Windows 가상 Shields를 실행 합니다.
4. 모든 설치 되었으면 제대로, 휴대폰 사용자가 Arduino 스케치를 연결할를 업데이트 하 고 있습니다에서 오디오 큐를 사용 하 여 시작 해야 합니다. 간을 전환 하 여 Arduino의 LED 켜고 Windows 10 장치에 'on' 또는 'f'를 말할 수 있습니다.

### <a name="arduino-wiring-sketch-hello-world-example"></a>Arduino 스케치를 연결 합니다. Hello World 예제

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


