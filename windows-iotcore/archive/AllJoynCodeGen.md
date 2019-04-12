---
title: AllJoynCodeGen 개요
author: saraclay
ms.author: saclayt
ms.date: 09/06/17
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: AllJoynCodeGen, AllJoyn 인터페이스를 사용 하 여 전체 Windows 런타임 구성 요소를 생성 하는 코드 생성 도구에 알아봅니다.
keywords: windows iot, AllJoyn
ms.openlocfilehash: c8e9f08c5565c7e4252e1b15858c08402eedb712
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513733"
---
> [!NOTE]
> 보관 된 설명서가 표시 됩니다. Windows 10 IoT에서 더 이상 AllJoyn 사용할 수 없습니다. 질문에 대 한 GitHub에서 문제를 제기 하거나 아래 설명에 의견을 남길 하세요.

# <a name="alljoyncodegen-overview"></a>AllJoynCodeGen 개요

AllJoynCodeGen 사양 또는 장치에서 파생 하는 하나 이상의 AllJoyn 인터페이스에 대 한 XML 설명을 사용 하 여 전체 Windows 런타임 구성 요소를 생성 하는 코드 생성 도구를 만들었습니다.

지원 되는 언어에서이 도구에서 생성 된 Windows 런타임 구성 요소를 사용할 수 있습니다 (JS C#, C++/CX 등) 유니버설 Windows SDK에서 사용할 수 있는 Api를 사용 하 여 합니다. 즉, 동일한 구성 요소 (라우터 서비스와 C API dll) AllJoyn OneCore 패키지가 포함 된 모든 플랫폼에서 사용할 수 있도록 개발자 구성 요소 사용 하 여 생산자 및/또는 해당 인터페이스의 소비자를 만들 수 있습니다. 

**참고** AllJoyn C Api에 대 한 자세한 내용은 AllJoyn Core SDK 및 설명서를 다운로드할 수 있습니다 [The AllSeen Alliance](http://go.microsoft.com/fwlink/?LinkId=524584)합니다.

## <a name="how-does-alljoyncodegen-work"></a>AllJoynCodeGen는 어떻게 작동 하나요?

기본 흐름은 다음과 같습니다.

1. 서비스를 설명 하는 AllJoyn XML (현재 Dbu 검사 형식)에서 작성 된 XML 파일 codegen 도구에 공급 됩니다.
2. AllJoynCodeGen 도구는 Windows 런타임 구성 요소에서 발생 하는 코드를 생성 합니다. 이 생성 된 코드에 의존 **MSAJAPI.lib** 하 고 [Windows.Devices.AllJoyn](https://msdn.microsoft.com/library/windows/apps/xaml/windows.devices.alljoyn.aspx) Windows 10 SDK에서.
3. 개발자는이 구성 요소를 사용 하는 응용 프로그램을 빌드합니다.
4. 런타임 시 응용 프로그램 개발자의 도구로 생성 되 고 Windows 런타임 구성 요소 로드 됩니다 (예:: 이어야 합니다) 상자에서 Dll 뿐만 아니라 **MSAJAPI.dll** 하 고 **Windows.Devices.AllJoyn.dll**합니다.

다음 워크플로 다이어그램에서는이 프로세스를 보여 줍니다.

![AllJoyn CodeGen 다이어그램](../media/AllJoyn/alljoyncodegen.png)

## <a name="running-from-the-command-line"></a>명령줄에서 실행

AllJoynCodeGen 도구는 현재 Windows 10 SDK와 함께 제공 되는 명령줄 도구로 존재 합니다. 실행 하려면 도구는 다음 문자열을 사용 하는 유효한 XML 파일을 전달 합니다.

    AllJoynCodeGen –i Foo.xml –o c:\users\developer1\documents\Foo\

## <a name="reviewing-the-output"></a>출력 검토

생성된 된 클래스는 핵심 C API에서 노출 하는 기능을 래핑합니다. 생성된 된 코드 추상적 이기 때문에 이것이-1-1 매핑이 없습니다. 아래 표에 나와 있는 Core C++ Api는 각 생성 된 코드 클래스에 의해 래핑됩니다. 다음 자리 표시자의 테이블에 생성 된 이름에 사용 됩니다.

* `<Foo>` xml 파일에 정의 된 인터페이스의 이름
* `<Signal>` xml 파일에서 가져온 신호를의 이름인
* `<Method>` xml 파일에서 가져온 메서드의 이름
* `<Property>` xml 파일에서 수행 되는 속성의 이름


> | Windows 런타임 클래스 |  | 설명 | 핵심 C++ API |
> | ------------------------ | --- | --------- | ---------- |
> | `<Foo>`감시자 |  | 대상 서비스를 보급 하는 생산자에 대 한 검색 | *BusListener* 클래스 *BusAttachment* 클래스 |
> | `<Foo>`JoinSessionResult |  | 세션에 참가의 성공 여부를 보고 하 고 노출 된 `<Foo>Consumer` 성공적으로 조인 하는 경우 세션에 대 한 인스턴스. | *JoinSessionAsyncCB* class; *QStatus* |
> | `<Foo>`생산자 |  | 서비스를 보급 하 고 AllJoyn 이벤트에 대 한 처리기를 노출 합니다. | *BusObject* 클래스 *BusAttachment* 클래스 *InterfaceDescription* 클래스 *SessionPortListener* 클래스 *메시지* 클래스 |
> | `<Foo>`신호 |  | 메서드 및 신호를 수신 하는 처리기를 노출 합니다. 생산자와 소비자 모두가 사용 합니다. | *BusObject* 클래스 *InterfaceDescription* 클래스 *메시지* 클래스 |
> | `<Foo>`소비자 |  | 검색 후 서비스와 상호 작용 합니다. | *ProxyBusObject* 클래스 *InterfaceDescription* 클래스 *SessionListener* 클래스 *메시지* 클래스 |
> | `<Foo>``<Method>`CalledEventArgs |  | 메서드에 전달 된 인수 `EventAdapters.<Foo>ServiceEventAdapter`합니다. | *메시지* 클래스 |
> | `<Foo>``<Method>`결과 |  | I에서 메서드 구현에서 사용 하는<Foo>모든 값을 반환 하는 것은 물론 호출의 성공 여부를 보고 하는 서비스입니다. | *메시지* 클래스 *QStatus* |
> | `<Foo>``<Signal>`ReceivedEventArgs |  | 인수에서 신호를 전달할 <Foo>신호입니다. | *메시지* 클래스 |


## <a name="build-guide"></a>빌드 가이드

#### <a name="creating-the-component"></a>구성 요소 만들기

생성 된 코드를 XML로 동일한 인터페이스 이름을 공유 하는 구성 요소에 포함 해야 합니다. 예를 들어는 토스터에 대 한 XML com.microsoft.sample.toaster로 정의 된 경우 런타임 구성 요소 com.microsoft.sample를 만듭니다 됩니다. 

또는 모든 구성 요소 이름을 지정할 수 있습니다 (예: fooCodeGenComponent) 싶지만 인터페이스 이름이 동일 하도록 프로젝트 속성에서 루트 네임 스페이스를 수동으로 업데이트 해야 합니다.

> [!TIP]
> AllJoynCodeGen 도구에서 생성 되는 pch.h 파일의 루트 네임 스페이스를 찾을 수 있습니다.
