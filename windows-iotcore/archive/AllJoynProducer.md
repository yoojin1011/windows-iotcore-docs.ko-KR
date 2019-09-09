---
title: AllJoyn 생산자
author: saraclay
ms.author: saclayt
ms.date: 09/07/17
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: 검사 XML 및 다양 한 기능을 학습 하 고 작성 하 여 AllJoyn 생산자를 만드는 방법에 대해 알아봅니다.
keywords: windows iot, AllJoyn
ms.openlocfilehash: 014f6f4b4c33f4dbd85963bbddccb948322ccca9
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "60167407"
---
> [!NOTE]
> 보관 된 설명서를 보고 있습니다. AllJoyn는 Windows 10 IoT에서 더 이상 지원 되지 않습니다. 질문이 있는 경우 GitHub에서 문제를 열거나 아래 설명에 의견을 남겨 주세요.

# <a name="alljoyn-producers"></a>AllJoyn 생산자

Proximal 네트워크에서 연결 된 장치 및 [앱을 만들기](https://allseenalliance.org/)위한 뛰어난 프레임 워크를 제공 하는 Alljoyn은 Visual Studio 용 [alljoyn Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286) 확장에서 alljoyn를 사용 하는 최상의 환경을 제공 합니다.  Microsoft의 도구를 통해 생산자와 소비자를 위한 앱을 만들 때 새 AllJoyn 장치를 처음부터 시작 하는 것은 매우 복잡할 수 있습니다.

Tinker 하 고 탐색 하는 데 사용할 수 있는 차세대 장난감 장치 또는 새 장난감에 대 한 아이디어가 있는 경우 AllSeen 동맹에서 제공 하는 표준 인터페이스 중 하나를 사용 하지 못할 수 있습니다.  그렇다면 새 AllJoyn 생산자를 만들어야 합니다.

새 AllJoyn 생산자를 만들려는 개발자는 자신의 검사 XML을 작성 해야 하지만 검사 XML을 만들려면 중요 한 전문 지식이 필요 하며 새로운 개발자를 위한 상당한 학습 곡선이 필요 합니다.  이 블로그 게시물는 검사 XML의 다양 한 구성 요소를 분석 하 고, 각 구성 요소의 목적과 제한 사항을 설명 하 고, 하기 쉬우며 용어로 좋은 예제를 제공 하 여 학습 곡선을 낮춥니다.

## <a name="existing-documentation"></a>기존 설명서

이 블로그 게시물와 결합 된 다음 리소스를 간단한 검사 하면 검사 XML의 개발자 이해를 가속화 해야 합니다.

1. [Alljoyn 이벤트 및 작업 API 가이드](https://allseenalliance.org/developers/develop/api-guide/events-and-actions) – alljoyn 구현 세부 정보 및 개요.
2. [Alljoyn 인터페이스 검토 보드 디자인 지침](https://wiki.allseenalliance.org/irb/interface_design_guidelines_1.0) -ALLJOYN 검사 XML에 대 한 엄격한 구조 및 사양입니다.
3. [D-Bus 사양](http://dbus.freedesktop.org/doc/dbus-specification.html) –이 사양에서는 AllJoyn 기본 검사 XML입니다.

__검사 XML의 세 가지 유형__

정독 AllJoyn 설명서는 세 가지 유형의 검사 XML을 찾을 수 있습니다.

1. D-Bus 사양 XML: 데이터 표현에 대 한 형식 형식과 오버 헤드가 낮은 프로세스 간 통신입니다.
2. AllJoyn 검사 XML: 사양에 AllJoyn 원칙을 적용 하는 동시에 텍스트 설명을 포함 하는 XML 태그를 사용 하 여 D-버스 사양 XML을 확장 합니다.
3. 확장 된 AllJoyn 검사 XML: 기본 검사 XML의 진화 구조 및 사전에 대 한 명명 된 형식을 소개 합니다.

AllJoyn 스튜디오는 현재 D-Bus 사양 XML 및 AllJoyn 검사 XML을 지원 합니다. 이 블로그에서는 AllJoyn 검사 XML을 만들고 구성 하는 방법을 지시 합니다.  AllSeen 동맹의 IRB (Interface Review)는 새로운 확장 된 AllJoyn 검사를 표준화 검토에 대 한 정식 제출의 형식으로 사용 하지만, 가까운 미래를 위해 통합 검사 XML 형식으로 작업 하 고 있습니다.

## <a name="introspection-high-level-overview"></a>검사 개략적인 개요

모든 AllJoyn 생산자는 신호, 속성 및 메서드를 통해 설명 된 대로 생산자의 지원 되는 기능 (인터페이스)을 표시 하는 검사 XML을 공개적으로 알립니다.  검사 XML을 사용 하 여 코드를 생성 하는 것과 같은 코드 생성 솔루션은 개발을 가속화 하는 데 필요한 코드를 만듭니다.  검사 XML은 두 명의 제조업체에서 XML을 사용 하 여 동일한 기능을 가진 생산자를 구현할 수 있도록 명확 하지 않은 사람이 인식할 수 있는 방식으로 생산자의 기능을 설명 합니다.  동일한 토큰을 사용 하 여 AllJoyn 생산자에 대해 이전에 알지 못하는 개발자는 해당 XML을 기반으로 해당 생산자에 대해 개발할 수 있어야 합니다.

__AllJoyn 인터페이스__

AllJoyn에서는 검사 XML을 동작 및 기능의 서로 다른 논리적 그룹화를 나타내는 다양 한 "인터페이스"로 분리 하 여이를 수행 합니다.  AllJoyn 인터페이스는 역방향 DNS 규칙을 사용 하 여 명명 됩니다. 예를 들어 contoso.com 도메인을 소유 하는 Contoso l t d .에서 만든 "Foo" 인터페이스는 다음과 같이 작성 됩니다.

    <interface name="com.contoso.Foo">

생산자는 원하는 수의 인터페이스를 구현할 수 있지만 보급 하는 인터페이스의 모든 구성 요소를 구현 해야 합니다.  동작을 구분 하 고 확장 하기 위해 AllJoyn에서는 기존 인터페이스 계층 구조와 관련 하 여 새 인터페이스를 만들 수 있도록 지원 합니다. 즉,는 `Foo.Bar` 범주 아래에 있는 항목에 대 한 새로운 기능을 `com.contoso.Foo`정의하지만 인터페이스에 대 한 명시적 종속성은 없습니다. `com.contoso.Foo.Bar` 

예를 들어 두 개의 인터페이스가 있습니다. `com.contoso.Sensor` 및 `com.contoso.Sensor.Humidity` – "습도"는 논리적으로 "센서" 범주 아래에 있습니다.  습도 생산자를 개발 하는 사람은 `com.contoso.Sensor.Humdity` 인터페이스를 지원 하도록 선택할 수 있지만 `com.contoso.Sensor` 인터페이스를 지원 하도록 선택할 수도 있습니다.  인터페이스를 보급 하는 경우와 관계 없이 생산자는 모든 기능을 지원 해야 합니다.

`<description>` 태그는 인터페이스, 기능 및 인수를 설명 하는 데 사용 되며 다양 한 언어에 대해 지역화할 수 있습니다.  `<description>` 태그를 자유롭게 사용 하면 XML을 이해 하기 쉽고 모호성을 제거 합니다.

표준 방법은 인터페이스에 `org.alljoyn.Bus.Secure` 주석을 사용 하 여 보안 및 인증을 사용 하도록 설정 하는 것을 말합니다.  강력한 인증의 경우 PSK (미리 공유한 키) 또는 ECDSA (certificate key exchange)를 사용 합니다.  그렇지 않으면 "null" 인증이 기본 동작이 됩니다.  **실제 인증 메커니즘은 선언이 아니라 구현에서 발생**합니다. 이 주석은 보안을 사용 하지만 사용 되는 보안 형식 또는 구현 방법을 지정 하지 않습니다.

___예제___

``` xml
<node>
 
  <interface name="com.example.Door.PrivateDoor">
 
    <annotation name="org.allJoyn.Bus.Secure" value="true" />
 
    <description language="en">
 
      Private interface for a Door the consumer owns. 
 
    </description>
 
  </interface>
 
</node>
```

이 예제에서는 장치 `com.example.Door.PrivateDoor`에서 노출 하는 인터페이스를 보여 줍니다. 인터페이스의 범위에서는 사용 되는 메커니즘 유형이 아닌 해당 인터페이스를 사용 하는 경우 통신을 보호 해야 하는지 여부를 고려해 야 합니다.

__인터페이스 기능__

인터페이스는 메서드, 속성 또는 신호의 세 가지 인터페이스 멤버를 사용 하 여 해당 기능을 선언 합니다. 또한 검사 XML은 추가 기능 또는 제약 조건을 설명 하는 주석을 지원 합니다.  이러한 기능은 UpperCamelCase 표기법을 사용 하지만 인수는 lowerCamelCase 표기법을 사용 합니다.

### <a name="argument-types"></a>인수 형식

인터페이스 멤버는 ASCII 형식 코드로 표시 되는 인수를 보내고 받습니다.  인터페이스 멤버의 형식에 따라 인수는 소비자 (direction = "out") 또는 소비자 (direction = "in")에서 생산자로 전송 될 수 있습니다.  다음 표에서는 일반적으로 사용 되는 형식에 대 한 간략 한 개요를 제공 합니다.

> | *기본 이름* | *형식-코드* | *사용* |
> |----------------- |---------| --- |
> |**부울** | b | TRUE (1) 또는 FALSE (0)를 나타냅니다. 간단한 이진 정보 또는 상태에 사용 됩니다. |
> |**BYTE** | y | 0에서 255 사이의 정수 값입니다. 작은 양수를 처리할 때 사용 됩니다. |
> |**UINT16** | q | 0에서 2 ^ 16-1 사이의 정수 값 |
> |**UINT32** | u | 0에서 2 ^ 32-1 사이의 정수 값 |
> |**UINT64** | t | 0에서 2 ^ 64-1 사이의 정수 값 |
> |**INT16** | n | – (2 ^ 15)부터 2 ^ 15-1 까지의 정수 값 |
> |**INT32** | i | – (2 ^ 31)부터 2 ^ 31-1 까지의 정수 값 |
> |**INT64** | x | – (2 ^ 63)부터 2 ^ 63-1 까지의 정수 값 |
> |**차례로** | d | – (2 ^ 127)에서 2 ^ 127-1 까지의 전체 자릿수 부동 소수점 숫자 |
> |**문자열** | s | UTF-8 문자열 |
 
지원 되는 모든 유형에 대 한 자세한 개요는 [여기](http://dbus.freedesktop.org/doc/dbus-specification.html#idp94392448)를 참조 하세요.

이 문서를 작성할 때 가능 하면 SI 단위를 사용 하 고 원하는 단위를 명확 하 게 나타냅니다. 가능 하면 시나리오에 가장 제한적인 형식 코드를 선택 합니다. 예를 들어 사용자의 나이가 년 단위로 표시 되는 경우 음수가 아니거나 INT16이 아닌 BYTE를 사용 합니다. 즉, 음수가 아니거나 255 년 보다 많은 시간을 사용 합니다.  항상 최신 [IRB (AllJoyn 인터페이스 검토 보드)](https://wiki.allseenalliance.org/interfacereviewboard?s%5b%5d=interface&s%5b%5d=review&s%5b%5d=board) 지침을 따르세요.

다음 표에서는 일반적인 단위를 요약 합니다.


> |*수량* | *Unit*|
> |-------- | ---- |
> |**절대 시간 (날짜 & 시간)** | UNIX Epoch 이후 시간 (초) (1970 1 월 1 일 00:00:00) |
> |**하루 중 시간** | 자정 이후 시간 (초) |
> |**시간 간격** | 초 |
> |**대역** | 비트/초 |
> |**데이터 크기** | 바이트 |
 
### <a name="methods"></a>메서드

소비자는 메서드를 호출 하 여 생산자의 상태를 수정할 수 있으며 해당 이름은 생산자가 작업을 수행 하기 위한 요청을 나타내므로 동사로 시작 해야 합니다.  메서드에는 입력 및 출력 인수가 있을 수 있습니다. 반환 메시지를 보내야 하는 경우에는 "NoReply" 라는 주석을 적용 합니다.  그러나 일반적으로는 일반적으로 SuccessResult 또는 FailureResult를 반환 하 여 메서드 호출에 대 한 소비자 의견을 제공 합니다.  인수의 형식은 [D-Bus 사양을](http://dbus.freedesktop.org/doc/dbus-specification.html)따라야 합니다. 

___예 (편의를 위해 인터페이스 정보 제외)___

``` xml
<node>
 
  <interface name="com.example.Door.PrivateDoor">
 
    <!-- Method showing arguments with only directions in -->
 
    <method name="SetPasscode">
 
      <description language="en">
 
        Allows owner of the door to change the code needed to unlock it.
 
      </description>
 
      <argument name="currentPasscode" type="u" direction="in">
 
        <description language="en">
 
          Current code (00000000 to 99999999) needed to unlock door
 
        </description>
 
      </argument>
 
      <argument name="newPasscode" type="u" direction="in">
 
        <description language="en">
 
          New code (00000000 to 99999999) needed to unlock door
 
        </description>
 
      </argument>
 
    </method>
 
  </interface>
 
  <interface name="com.example.Door.PublicDoor">
 
    <!-- Method showing both arguments in and out -->
 
    <method name="UnlockDoor">
 
      <description language="en">
 
        Allows guests with the code to unlock the door.
 
      </description>
 
      <argument name="passcode" type="u" direction="in">
 
        <description language="en">
 
          Current code (00000000 to 99999999) needed to unlock door
 
        </description>
 
      </argument>
 
      <argument name="welcomeMessage" type="s" direction="out">
 
        <description language="en">
 
          Message from the owner of the door.
 
        </description>
 
      </argument>
 
    </method>
 
  </interface>
 
</node>
```

*참고: 대부분의 경우 생산자의 상태에 액세스 하는 메서드 대신 속성을 사용 해야 합니다 (예: GetColor 메서드 대신 Color 속성 사용).*

### <a name="properties"></a>속성

속성은 주로 생산자의 상태에 대 한 액세스를 허용 합니다.  속성이 기술적으로 "읽기", "readwrite" 또는 "write"의 액세스 값을 가지는 반면, 상태 수정 기능은 일반적으로 메서드에 속합니다. 따라서 개발자는 상태를 나타내는 경우에만 속성을 "읽기"로 유지 하 고 "readwrite"를 사용 해야 합니다. 해당 속성은 다른 모든 속성과는 독립적입니다.  속성은 단순히 "write" 일 수 없습니다. 관찰 하지 않고 상태를 수정 하는 것은 메서드 역할입니다.

값이 변경 될 때 경고 소비자에 대 한 속성을 주석으로 처리 해야 합니다. 선택적으로 속성은 부모 인터페이스에서이 주석을 상속할 수 있습니다.  주석에 `org.freedesktop.DBus.Property.EmitsChangedSignal` 는 다음과 같은 4 개의 값이 있을 수 있습니다.

* "true"-속성이 변경 되 면 생산자는 변경 된 속성 및 새 값을 나타내는 신호를 내보냅니다. 자주 사용 되는 속성에 사용 되며, 문에 대 한 "LockState"와 같이 활성 감독을 요구 합니다.
* "무효화" – 속성이 변경 되 면 생산자는 변경 된 속성을 나타내는 신호를 내보내고 새 값은 내보내지 않습니다. 많은 감독 (예: 옷의 "WashMode")을 요구 하지 않거나 컨테이너와 같은 많은 데이터를 나타내는 속성에 사용 됩니다.
* "false"-속성이 변경 되 면 생산자는 신호를 내보냅니다. 지하철 회전식 추적 사용자 지하철를 탑재 하는 사람을 추적 하는 "TransitCounter" 속성과 같이 신속 하 게 업데이트 되는 속성에 사용 됩니다. 지정 하지 않으면 AllJoyn 속성은이를 기본값으로 사용 합니다.
* "const" – 속성은 값을 변경 하지 않으며 변경 된 신호를 내보내지 않습니다. 이는 AllJoyn 16.04 릴리스에서 도입 되었습니다. 그때까지 "true"를 사용 합니다.

___예제___

이전 예제를 확장 하면 속성을 포함 하도록 XML을 수정 했습니다 (간단 하 게 하기 위한 메서드 제외).

``` xml
<node>
 
  <interface name="com.example.Door.PrivateDoor">
 
    <!—- Read property that sends a signal when the value changes -->
 
    <property name="IsLocked" type="b" access="read">
 
      <annotation name="org.freedesktop.DBus.Property.EmitsChangedSignal" value="true"/>
 
      <description language="en">
 
        Owner of the door may freely lock and unlock the door.
 
      </description>
 
    </property>  
 
  </interface>
 
  <interface name="com.example.Door.PublicDoor">
 
    <!—- Read-only property that never sends a signal and never changes -->
 
    <property name="Owner" type="s" access="read">
 
      <annotation name="org.freedesktop.DBus.Property.EmitsChangedSignal" value="true"/>
 
      <description language="en">
 
        Owner of the door is public knowledge.
 
      </description>
 
    </property>
 
  </interface>
 
</node>
```

### <a name="signals"></a>연산

신호를 사용 하 여 생산자를 쿼리하여 결정할 수 없는 이벤트를 소비자에 게 알립니다.  문이 열리면 "true" EmitsChangedProperty 주석을 사용 하 여 생산자의 DoorOpen 속성을 통해 전달 됩니다.  그러나 도어를 전달 하는 다른 사용자는 속성 변경에서 파생 될 수 없으므로이로 인해 좋은 독립 실행형 신호가 생성 됩니다.  이러한 종류의 이벤트를 "상태 비저장"으로 지칭 합니다.  신호는 생산자에서 소비자로 단방향 이므로 "out" 인수만 포함할 수 있습니다.

___예___ 

(편의를 위해 메서드와 속성 제외):

``` xml
<node>
 
  <interface name="com.example.Door.PrivateDoor">
 
    <!—- Signals may contain arguments about non-state information -->
 
    <signal name="ThresholdCrossed" sessioncast="true">
 
      <description>
 
        Signal to notify owner whenever anyone passes through the door.
 
      </description>
 
      <argument name="crossedInward" type="b" direction="out">
 
        If true, someone entered; if false, someone left.
 
      </argument>
 
    </signal>
 
  </interface>
 
</node>
```

신호에는 좁은 범위가 있으므로 일반적으로 생산자의 XML에 표시 됩니다.

### <a name="containers"></a>컨테이너

여러 인수를 serialize 된 JSON 문자열과 같은 복합 컬렉션으로 결합 하지 마십시오. D-버스 사양은 데이터 컨테이너 (구조체, 배열, 변형 및 DICT_ENTRY)에 대해 affordances를 만듭니다.  이를 사용 하 여 기본 형식이 넘는 인수를 전달 합니다.

___변형은___

변형은 "v" 형식으로 표시 되며 임의의 [단일 전체 형식을](http://dbus.freedesktop.org/doc/dbus-specification.html#term-single-complete-type)포함할 수 있습니다. 그러나 XML 정의에 모호성을 추가 하므로 가능 하면 항상 변형을 피해 야 합니다.

___STRUCT___

구조체는 "(" 및 ")"를 사용 하 여 데이터 구조의 시작과 끝을 나타냅니다. 단일 전체 형식입니다.  이러한 데이터 구조는 중첩 될 수 있습니다.

예를 들면 다음과 같습니다.

"(Iii)" 형식은 세 정수의 구조체를 나타냅니다. "(i (ii))"는 "((ii) i)" 형식과는 다른 정수의 구조체와 두 정수의 구조체를 나타냅니다.

___배열과___

배열에는 "a" 형식 코드가 사용 되며 그 뒤에는 단일 전체 형식이 있어야 합니다.  배열에는 설정 된 길이가 없으므로 목록 데이터 구조와 유사 합니다. 배열은 단일 전체 형식을 나타냅니다.

예를 들면 다음과 같습니다.

"Ai"의 형식은 정수 배열을 나타내며 "aai"는 정수 배열의 배열을 나타냅니다.  배열은 "a (ii)"와 함께 사용할 수 있습니다.

___DICT_ENTRY___

DICT_ENTRYs 함수는 "{" 및 "}"를 사용 하 고, 배열 요소 형식 으로만 발생 하 고, 중괄호 안에 정확히 두 개의 완전 한 형식을 포함 해야 하는 더 큰 제한이 있는 구조체와 유사 합니다.  첫 번째 형식은 사전 데이터 구조체의 "키"를 나타내고, 두 번째 형식은 사전 키-값 쌍의 "값"을 나타냅니다.  키는 사전에서 고유 해야 합니다.

예:

{Sy}의 형식은 문자열 키와 바이트 값의 사전을 나타냅니다.  이후 <description> 올바른 키 및 값을 설명 하는 태그입니다. 

__최종 예제 및 ajxmlcop__

컨테이너 개념은 기존 XML의 기능을 개선 하 고 새로운 유용한 인터페이스 멤버에 대 한 통로을 제공 합니다.

XML 작성을 완료 한 후에는 ajxmlcop 명령줄 도구 (AllJoyn [git 원본](https://git.allseenalliance.org/cgit/core/alljoyn.git/) 또는 [여기](https://github.com/MS-brock/AllJoynToasterDemo)에서 사용 가능)를 사용 하 여 xml의 유효성을 검사 합니다.  XML 파일을 입력 인수 (예: `C:\>ajxmlcop.exe doorExample.xml`)로 사용 하 여 오류, 경고 및 정보 메시지를 수신 하려면 ajxmlcop을 입력 인수 (예:)로 사용 합니다.  이 도구는 XML의 구조와 형식 및 신호, 속성 및 메서드의 사용에 대 한 유용한 피드백을 제공 합니다.

``` xml
<node>
  <interface name="com.example.Door.PrivateDoor">
    <annotation name="org.alljoyn.Bus.Secure" value="true" />
    <description language="en">
      Examples for an AllJoyn-enabled door.  Private interface that can only be used by the producer’s owner.
    </description>
    <method name="SetPasscode">
      <description language="en">
        Change the code needed to unlock the door.
      </description>
      <argument name="currentPasscode" type="u" direction="in">
        <description language="en">
          Current code needed to unlock door
        </description>
      </argument>
      <argument name="newPasscode" type="u" direction="in">
        <description language="en">
          New code needed to unlock door
        </description>
      </argument>
    </method>
    <method name="UpdateGuestRatings">
      <description language="en">
        Update the list of guests and their personality scores.
      </description>
      <annotation name="org.freedesktop.DBus.Method.NoReply" value="true" />
      <argument name="guestName" type="s">
        <description language="en">
          The name of the guest being entered.
        </description>
      </argument>
      <argument name="qualityScores" type="a{sy}">
        <description language="en">
          DICTIONARY[Key:(string)guestQuality, Value:(byte)score]
          KEYs: "Friendly", "Social", "Punctual" 
          VALUEs: [0-10]
          The qualities of the guest, scored appropriately. If the guestName matches an existing entry, this updates that entry.
        </description>
      </argument>
    </method>
    <method name="SetDoorSecurity">
      <description language="en">
        Close and lock the door or unlock the door.
      </description>
      <argument name="secured" type="b" direction="in">
        <description language="en">
          If TRUE, shut and lock the door.
          If FALSE, unlock the door.
        </description>
      </argument>
    </method>
    <property name="MessageBook" type="a(ss)" access="read">
      <annotation name="org.freedesktop.DBus.Property.EmitsChangedSignal" value="invalidates"/>
      <description language="en">
        (struct)[(string)guestName, (string)message]
        A list of names of people and the messages they have left.
      </description>
    </property>
    <property name="GuestRatings" type="a(sa{sy})" access="read">
      <annotation name="org.freedesktop.DBus.Property.EmitsChangedSignal" value="false"/>
      <description language="en">
        ARRAY[(string)guestName, DICTIONARY(Key:(string)guestQuality, Value:(byte)score)]
        KEYs: "Friendly", "Social", "Punctual"
        VALUEs: [0-10]
        A collection of the previous guests and their scored qualities.
      </description>
    </property>
    <property name="IsLocked" type="b" access="read">
      <annotation name="org.freedesktop.DBus.Property.EmitsChangedSignal" value="true"/>
      <description language="en">
        Owner of the door may freely lock and unlock the door.
      </description>
    </property>
    <property name="Version" type="q" access="read">
      <annotation name="org.freedesktop.DBus.Property.EmitsChangedSignal" value="false"/>
      <description language="en">
        Version of the implementation being used.
      </description>
    </property>
    <signal name="ThresholdCrossed" sessioncast="true">
      <description>
        Signal to notify owner whenever anyone passes through the door.
      </description>
      <argument name="crossedInwards" type="b" direction="out">
        If true, someone entered; if false, someone left.
      </argument>    
    </signal>
  </interface>
  <interface name="com.example.Door.PublicDoor">
    <annotation name="org.alljoyn.Bus.Secure" value="true" />
    <description language="en">
      Examples for an AllJoyn-enabled door. Public interface that can be used by any consumer.
    </description>
    <method name="UnlockDoor">
      <description language="en">
        Allows guests with the code to unlock the door.
      </description>
      <argument name="passcode" type="u" direction="in">
        <description language="en">
          Current code (00000000 to 99999999) needed to unlock door
        </description>
      </argument>
      <argument name="welcomeMessage" type="s" direction="out">
        <description language="en">
          Message from the owner of the door.
        </description>
      </argument>
    </method>
    <method name="LeaveMessage">
      <description language="en">
        Leave a message for the owner of the door.
      </description>
      <argument name="guestName" type="s" direction="in">
        <description language="en">
          Name of guest leaving a message
        </description>
      </argument>
      <argument name="message" type="s" direction="in">
        <description language="en">
          Message left for owner of the door
        </description>
      </argument>
    </method>
    <method name="AnnouncePresence">
      <description language="en">
        Send a message to the owner of the door.
      </description>
      <argument name="announcingGuest" type="s" direction="in">
        <description language="en">
          Name of the guest announcing their presence.
        </description>
      </argument>
      <argument name="forcefulnessOfAnnouncment" type="y" direction="in">
        <description language="en">
          Degree to which the guest attempts to make their presence known, on bounds [1:10], where 1 is softly and 10 is aggressively.
        </description>
      </argument>
    </method>
    <property name="Version" type="q" access="read">
      <annotation name="org.freedesktop.DBus.Property.EmitsChangedSignal" value="false"/>
      <description language="en">
        Version of the implementation being used.
      </description>
    </property>
    <property name="Owner" type="s" access="read">
      <annotation name="org.freedesktop.DBus.Property.EmitsChangedSignal" value="false"/>
      <description language="en">
        Owner of the door is public knowledge.
      </description>
    </property>
  </interface>
</node>
```

