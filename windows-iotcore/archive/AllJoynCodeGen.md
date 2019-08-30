---
title: AllJoynCodeGen 개요
author: saraclay
ms.author: saclayt
ms.date: 09/06/17
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: AllJoyn 인터페이스를 사용 하 여 완전 한 Windows 런타임 구성 요소를 생성 하는 코드 생성 도구인 AllJoynCodeGen에 대해 알아봅니다.
keywords: windows iot, AllJoyn
ms.openlocfilehash: c8e9f08c5565c7e4252e1b15858c08402eedb712
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "60167753"
---
> [!NOTE]
> 보관 된 설명서를 보고 있습니다. AllJoyn는 Windows 10 IoT에서 더 이상 지원 되지 않습니다. 질문이 있는 경우 GitHub에서 문제를 열거나 아래 설명에 의견을 남겨 주세요.

# <a name="alljoyncodegen-overview"></a>AllJoynCodeGen 개요

사양 또는 장치에서 파생 된 하나 이상의 AllJoyn 인터페이스에 대 한 XML 설명을 사용 하 여 전체 Windows 런타임 구성 요소를 생성 하는 코드 생성 도구인 AllJoynCodeGen를 만들었습니다.

이 도구에서 생성 된 Windows 런타임 구성 요소는 유니버설 Windows SDK에서 사용할 수 있는 api를 C#사용 C++하 여 지원 되는 모든 언어 (JS,,/cx 등)에서 사용할 수 있습니다. 즉, 동일한 구성 요소는 AllJoyn OneCore 패키지 (라우터 서비스 및 C API dll)를 포함 하는 모든 플랫폼에서 사용할 수 있습니다. 그런 다음 개발자는 구성 요소를 사용 하 여 해당 인터페이스의 생산자 및/또는 소비자를 만들 수 있습니다. 

**참고**  AllJoyn C Api에 대 한 자세한 내용을 보려면 [AllSeen 동맹](http://go.microsoft.com/fwlink/?LinkId=524584)에서 ALLJOYN Core SDK 및 설명서를 다운로드할 수 있습니다.

## <a name="how-does-alljoyncodegen-work"></a>AllJoynCodeGen는 어떻게 작동 하나요?

기본 흐름은 다음과 같습니다.

1. 서비스를 설명 하는 AllJoyn XML (현재는 Ebus 검사 형식)으로 작성 된 XML 파일은 codegen 도구에 공급 됩니다.
2. AllJoynCodeGen 도구는 Windows 런타임 구성 요소가 발생 하는 코드를 생성 합니다. 이 생성 된 코드는 Windows 10 SDK의 **MSAJAPI** 및 [windows 기반 장치](https://msdn.microsoft.com/library/windows/apps/xaml/windows.devices.alljoyn.aspx) 를 사용 합니다.
3. 개발자는이 구성 요소를 사용 하는 응용 프로그램을 빌드합니다.
4. 런타임에 개발자 응용 프로그램은 도구에서 생성 된 Windows 런타임 구성 요소 (예: foo. dll) 뿐만 아니라 기본 Dll **MSAJAPI** 및 **Windows.** x x x. x x x. x x x. x x x. x x x. x x x. x x x. x x x.

다음 워크플로 다이어그램은이 프로세스를 보여 줍니다.

![AllJoyn CodeGen 다이어그램](../media/AllJoyn/alljoyncodegen.png)

## <a name="running-from-the-command-line"></a>명령줄에서 실행

AllJoynCodeGen 도구는 현재 Windows 10 SDK와 함께 제공 되는 명령줄 도구로 존재 합니다. 도구를 실행 하려면 다음 문자열을 사용 하 여 올바른 XML 파일을 전달 합니다.

    AllJoynCodeGen –i Foo.xml –o c:\users\developer1\documents\Foo\

## <a name="reviewing-the-output"></a>출력 검토

생성 된 클래스는 핵심 C API에 의해 노출 되는 기능을 래핑합니다. 생성 된 코드가 추상적 이기 때문에이는 일대일 매핑이 아닙니다. 아래 표에서는 생성 된 각 C++ 코드 클래스로 래핑된 핵심 api를 보여 줍니다. 다음은 테이블의 생성 된 이름에 사용 되는 자리 표시자입니다.

* `<Foo>`xml 파일에 정의 된 인터페이스의 이름입니다.
* `<Signal>`xml 파일에서 가져온 신호의 이름입니다.
* `<Method>`xml 파일에서 가져온 메서드의 이름입니다.
* `<Property>`xml 파일에서 가져온 속성의 이름입니다.


> | Windows 런타임 클래스 |  | 설명 | 핵심 C++ API |
> | ------------------------ | --- | --------- | ---------- |
> | `<Foo>`감시자 |  | 대상 서비스를 보급 하는 생산자를 검색 합니다. | *Buslistener* 클래스; *Busattachment* 클래스 |
> | `<Foo>`JoinSessionResult |  | 세션에 대 한 성공 또는 실패를 보고 하 고, 조인이 `<Foo>Consumer` 성공 하면 세션에 대 한 인스턴스를 노출 합니다. | *JoinSessionAsyncCB* 클래스 *Qstatus* |
> | `<Foo>`점에서 |  | 서비스를 보급 하 고 AllJoyn 이벤트에 대 한 처리기를 노출 합니다. | *Busobject* 클래스; *Busattachment* 클래스; *인터페이스 설명* 클래스; *Sessionportlistener* 클래스; *Message* 클래스 |
> | `<Foo>`연산 |  | 신호를 보내고 받는 메서드 및 처리기를 노출 합니다. 생산자와 소비자 모두에 사용 됩니다. | *Busobject* 클래스; *인터페이스 설명* 클래스; *Message* 클래스 |
> | `<Foo>`어설션 |  | 검색 된 서비스와 상호 작용 합니다. | *Proxybusobject* 클래스; *인터페이스 설명* 클래스; *Sessionlistener* 클래스; *Message* 클래스 |
> | `<Foo>``<Method>`CalledEventArgs |  | 의 `EventAdapters.<Foo>ServiceEventAdapter`메서드에 전달 된 인수입니다. | *Message* 클래스 |
> | `<Foo>``<Method>`만들어집니다 |  | 호출의 성공 또는 실패 및<Foo>반환 값을 보고 하기 위해 I 서비스의 메서드 구현에서 사용 됩니다. | *메시지* 클래스 *Qstatus* |
> | `<Foo>``<Signal>`ReceivedEventArgs |  | 신호의 신호 <Foo>에 전달 되는 인수입니다. | *Message* 클래스 |


## <a name="build-guide"></a>빌드 가이드

#### <a name="creating-the-component"></a>구성 요소 만들기

생성 된 코드는 XML과 동일한 인터페이스 이름을 공유 하는 구성 요소에 포함 되어 있어야 합니다. 예를 들어 toaster에 대 한 XML이 toaster으로 정의 된 경우에는 런타임 구성 요소를 만듭니다. 

또는 원하는 모든 구성 요소의 이름을 지정할 수 있습니다 (예: fooCodeGenComponent). 그러나 프로젝트 속성 아래의 루트 네임 스페이스를 인터페이스 이름과 동일 하 게 수동으로 업데이트 해야 합니다.

> [!TIP]
> AllJoynCodeGen 도구에서 생성 된 pch .h 파일에서 루트 네임 스페이스를 찾을 수 있습니다.
