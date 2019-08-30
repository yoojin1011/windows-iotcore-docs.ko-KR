---
title: AllJoyn Studio
author: saraclay
ms.author: saclayt
ms.date: 09/07/17
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: UWP (유니버설 Windows 플랫폼) AllJoyn Api 및 Visual Studio 2017을 사용 하 여 AllJoyn UWP 앱을 만드는 방법에 대해 알아봅니다.
keywords: windows iot, AllJoyn
ms.openlocfilehash: 5326873218c0126b918679308e3a8e08cdddf84c
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "60168501"
---
> [!NOTE]
> 보관 된 설명서를 보고 있습니다. AllJoyn는 Windows 10 IoT에서 더 이상 지원 되지 않습니다. 질문이 있는 경우 GitHub에서 문제를 열거나 아래 설명에 의견을 남겨 주세요.

# <a name="using-the-alljoyn-studio-extension"></a>AllJoyn Studio 확장 사용

사물 인터넷에 대 한 권한을 부여 하는 데에는 모든 권한을 부여 하는 [Allseen 동맹](https://allseenalliance.org/) Windows 10에는 기본적으로 해당 플랫폼에 빌드되는 개발자가 Windows 10 앱을 "IoT (IoT)" 하는 데 사용할 수 있습니다. 이 문서에서는 UWP (유니버설 Windows 플랫폼) AllJoyn Api 및 Visual Studio 2017 [Alljoyn Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286) 확장을 사용 하 여 Windows 10 용 앱을 빌드하는 데 필요한 단계를 간략하게 설명 합니다.

## <a name="understanding-alljoyn-uwp-app-development"></a>AllJoyn UWP 앱 개발 이해

다음 세 가지 주요 구성 요소는 AllJoyn UWP 앱을 형성 합니다.

1. 앱 레이아웃 및 디자인 (XAML 또는 HTML) 및 클래스 구성 요소C#(, JavaScript C++, 또는 VB)
2. AllJoyn 핵심 Api: Windows 10 SDK에서 사용 가능한 AllJoyn 표준 클라이언트 API (C) 및 Windows (WinRT)
3. 하나 이상의 UWP Windows 런타임 구성 요소 (는 AllJoyn 인터페이스에서이 코드를 생성)

다음 다이어그램에서는 일반적인 AllJoyn UWP 프로젝트의 아키텍처를 보여 줍니다.

![AJ_UWP_Architecture](../media/AllJoyn/AJ_UWP_Architecture.jpg)

AllJoyn 지원 UWP 앱은 생산자 (인터페이스를 구현 하 고 노출 하는 방법, 일반적으로 장치), 소비자 (인터페이스, 일반적으로 앱) 또는 둘 다 일 수 있습니다. 소비자 및 생산자는 구현 세부 정보에서 분기 된 동일한 시작 단계를 공유 합니다.

## <a name="creating-an-alljoyn-enabled-uwp-app"></a>AllJoyn 사용 UWP 앱 만들기

Windows 10 용 AllJoyn 사용 UWP 앱을 개발 하려면 다음 단계를 수행 합니다 (이 문서의 뒷부분에서 설명).

1. 빌드 환경을 준비 합니다.
2. 사용 될 AllJoyn 인터페이스를 확인 하 고 필요한 검사 XML을 가져오거나 만듭니다.
3. AllJoyn 앱 프로젝트를 만든 다음 검사 XML 및 원하는 인터페이스를 선택 하 여 코드를 생성 합니다.
4. 생성 된 UWP Windows 런타임 구성 요소에서 노출 된 Api를 사용 하 여 앱에서 생산자 또는 ponsumer 코드를 구현 합니다.
5. UI를 빌드합니다.

## <a name="preparing-your-build-environment"></a>빌드 환경 준비

Windows 10 빌드 및 관련 도구에는 AllJoyn 사용 UWP 앱을 작성 하는 데 필요한 모든 리소스가 포함 되어 있습니다.

코드 작성을 시작 하기 전에 수행 해야 하는 작업은 다음과 같습니다.

* PC에 [Windows 10](https://www.microsoft.com/windows/) 설치
* [Visual Studio 2017](https://www.visualstudio.com/downloads/download-visual-studio-vs) 설치 (Express edition 사용 안 함)
* Visual Studio 갤러리에서 [AllJoyn® Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286) 확장을 다운로드 합니다. 


## <a name="obtaining-introspection-xml-for-alljoyn-interfaces"></a>검사 XML for AllJoyn 인터페이스 가져오기

다음 세 가지 방법으로 프로젝트를 시작 하는 데 필요한 AllJoyn 인터페이스 정의를 얻을 수 있습니다.

1. 런타임에 네트워크에 있는 AllJoyn 생산자에서 검사 XML을 추출 합니다.
2. 설명서에서 검사 XML을 가져옵니다. 예 들어 AllSeen 동맹의 [Umservice Framework (LSF) 설명서](https://wiki.allseenalliance.org/_media/compliance/alljoyn_lamp_service_14.06_interface_definition.pdf) 입니다.
3. AllJoyn/[D-Bus 검사](http://dbus.freedesktop.org/doc/dbus-specification.html) 형식과 호환 되는 고유한 검사 XML을 만듭니다.

이 문서에서는 처음 두® 가지 방법으로 검사를 설명 합니다. Studio는 기본적으로 AllJoyn 생산자 용 네트워크 쿼리를 지원 하 고 XML 파일을 추출 하 고 XML 파일을 업로드 합니다.  [여기](AllJoynProducer.md)에서 직접 만드는 방법을 알아보세요.

AllJoyn 지원 toaster 장치는이 게시물에 대 한 예제로 제공 됩니다. 이 toaster는 toasting 시퀀스를 시작 및 중지 하 고, "어둡기"를 설정 하 고, 알림이 burnt 경우 알림을 표시 하는 컨트롤을 노출 합니다.

![AJ_toaster](../media/AllJoyn/AJ_toaster.jpg)

Toaster는 다음 XML을 노출 합니다.

``` xml
<node name="/toaster">
  <interface name="org.alljoyn.example.Toaster">
    <annotation name="org.alljoyn.Bus.Secure" value="true"/>
    <description language="en">Example interface for controlling a toaster appliance</description>
    <description language="fr">Interface Exemple de commande d'un appareil de grille-pain</description>
    <property name="Version" type="q" access="read">
      <description>Interface version</description>
      <annotation name="org.freedesktop.DBus.Property.EmitsChangedSignal" value="const"/>
    </property>
    <signal name="ToastBurnt" sessioncast="true">
      <description language="en">Toast is burnt</description>
      <description language="fr">Toast est brûlé</description>
    </signal>
    <method name="StartToasting">
      <description language="en">Start toasting</description>
      <description language="fr">Lancer grillage</description>
    </method>
    <method name="StopToasting">
      <description language="en">Stop toasting</description>
      <description language="fr">Arrêtez de grillage</description>
    </method>
    <property name="DarknessLevel" type="y" access="readwrite">
      <annotation name="org.freedesktop.DBus.Property.EmitsChangedSignal" value="true"/>
      <description language="en">Toasting darkness level</description>
      <description language="fr">Grillage niveau de l'obscurité</description>
    </property>
  </interface>
</node>
```

## <a name="creating-an-alljoyn-project"></a>AllJoyn 프로젝트 만들기

일반적인 방법으로 프로젝트를 만듭니다. 클릭 `File->New->New Project` 하 여 시작 합니다.

![AJ_Studio_NewProject](../media/AllJoyn/AJ_Studio_NewProject.png)

Windows 유니버설 템플릿으로 이동 하는 대신 확장과 함께 설치 된 대상 언어에 대 한 "AllJoyn 앱" 템플릿을 선택 합니다.  프로젝트 이름을로 하 고 개발을 시작할 파일 위치를 선택 합니다.

![AJ_Studio_NameProj](../media/AllJoyn/AJ_Studio_NameProj.png)

AllJoyn 앱 템플릿을 선택 하 고 나면 Visual Studio에서 프로젝트에 포함 하려는 AllJoyn 인터페이스를 선택 하도록 요청 합니다. 

![AJ_Studio_Interfaces](../media/AllJoyn/AJ_Studio_Interfaces.png)

__네트워크의 장치에서 인터페이스 추출__

네트워크에서 AllJoyn 장치 또는 인터페이스를 찾을 수 없는 경우 [이 가이드](AllJoynTroubleshooting.md) 에 따라 문제를 해결 하십시오. 

![AJ_Studio_FindDevices](../media/AllJoyn/AJ_Studio_FindDevices.png)

네트워크에서 노출 된 인터페이스를 쿼리하려면 왼쪽 패널에서 "네트워크에서 생산자"를 선택 합니다. 그러면 네트워크에서 모든 AllJoyn 생산자가 검색 되어 지원 되는 인터페이스가 나열 됩니다.

![AJ_Studio_ListDevices](../media/AllJoyn/AJ_Studio_ListDevices.png)

프로젝트에서 포함 인터페이스를 선택 합니다.  이 경우에는 toaster 인터페이스만 사용 하 고 있으므로 "Toaster" 인터페이스만 선택 합니다.

![AJ_Studio_SelectDevices](../media/AllJoyn/AJ_Studio_SelectDevices.png)

"작업" 열은 프로젝트에 대해 보류 중인 변경 내용을 설명 하 고 새로 선택 된 인터페이스에 대해 "추가"를 표시 합니다. 여기에서 인터페이스에 "ToasterLibrary" 라는 친숙 한 이름을 지정 하 여 "Rename" 작업을 적용 하도록 트리거합니다.

![AJ_Studio_DeviceAction](../media/AllJoyn/AJ_Studio_DeviceAction.png)

__파일에서 XML 로드__

"찾아보기" 단추를 통해 원하는 수의 검사 XML 파일을 선택 하 여 포함 된 인터페이스를 확인 합니다.

![AJ_Studio_BrowseXML](../media/AllJoyn/AJ_Studio_BrowseXML.png)

적절 한 XML로 이동 하 여 선택 합니다. 여기서는 toaster를 사용 합니다.

![AJ_Studio_BrowseXML_2](../media/AllJoyn/AJ_Studio_BrowseXML_2.png)

AllJoyn® Studio에서 XML을 로드 하면 여러 인터페이스와에 포함 된 설명을 구문 분석 하 여 지원 하려는 인터페이스를 선택할 수 있습니다.

![AJ_Studio_BrowseXML_3](../media/AllJoyn/AJ_Studio_BrowseXML_3.png)

"작업" 열은 프로젝트에 대해 보류 중인 변경 내용을 설명 하 고 새로 선택 된 인터페이스에 대해 "추가"를 표시 합니다.

![AJ_Studio_BrowseXML_4](../media/AllJoyn/AJ_Studio_BrowseXML_4.png)

여기서는 "Toaster" 인터페이스를 포함 하 고 "ToasterLibrary" 라는 친숙 한 이름을 지정 하 여 "Rename" 작업을 적용 하도록 선택 했습니다.

![AJ_Studio_BrowseXML_5](../media/AllJoyn/AJ_Studio_BrowseXML_5.png)

__인터페이스 추가 및 제거__

이러한 단계를 완료 한 후 생성 된 파일은 위의 이름을 가진 C++ Windows 런타임 구성 요소에 자동으로 추가 되 고 응용 프로그램 프로젝트에 대 한 참조로 추가 됩니다.  그러나 루트 네임 스페이스는 여전히 인터페이스에서 정의 된 것과 동일한 "Toaster"입니다.  이러한 구성 요소에 액세스 하는 모든 클래스에는 구성 요소의 루트 네임 스페이스에 대 한 "using" 절이 있어야 합니다.

![AJ_Studio_SolutionExplorer](../media/AllJoyn/AJ_Studio_SolutionExplorer.png)

_잠깐만 IntelliSense를 활용 하기 위해 이제 생성 된 구성 요소를 빌드합니다._

AllJoyn 앱 솔루션을 만든 후에는 언제 든 지 다시 돌아가서 사용 중인 인터페이스를 수정할 수 있습니다. 주 메뉴 모음에서 "AllJoyn-> 인터페이스 추가/제거 ..."를 클릭 합니다. 인터페이스 관리자를 시작 합니다.

![AJ_Studio_AddInterfaces](../media/AllJoyn/AJ_Studio_AddInterfaces.png)

여기에서 "찾아보기 ..."를 클릭할 수 있습니다. XML 파일을 더 추가 하거나 기존 인터페이스를 선택 취소 합니다. 인터페이스를 선택 취소 하면 해당 작업이 "제거"로 업데이트 되 고 확인 단추를 클릭 하면 솔루션에서 연결 된 Windows 런타임 구성 요소가 제거 됩니다.

![AJ_Studio_AddXML](../media/AllJoyn/AJ_Studio_AddXML.png)

솔루션 탐색기를 살펴보면 Windows 런타임 구성 요소가 제거 되었습니다.

![AJ_Studio_SolutionExplorer_2](../media/AllJoyn/AJ_Studio_SolutionExplorer_2.png)

## <a name="next-steps"></a>다음 단계

AllJoyn 기능을 구현 하는 경우 사용 하려는 인터페이스의 네임 스페이스 뿐만 아니라 항상 "Windows.

![AJ_Studio_namespace](../media/AllJoyn/AJ_Studio_namespace.png)

__AllJoyn 소비자 구현__

인터페이스에 대해 생성 된 코드에는 생산자를 찾고 제어 하는 데 사용 되는 감시자 및 소비자 클래스가 포함 됩니다. 새 AllJoynBusAttachment을 만들고, 해당 AllJoynBusAttachment를 사용 하 여 감시자를 초기화 하 고, 공급자 ("추가" 이벤트)를 찾는 감시자를 등록 한 다음 감시자를 시작 하 여 감시자를 구현 합니다.

![AJ_Studio_Code_1](../media/AllJoyn/AJ_Studio_Code_1.png)

ToasterWatcher_Added 이벤트는 감시자가 생산자를 찾을 때마다 트리거됩니다.  이 이벤트를 사용 하 여 소비자를 등록 합니다. Visual Studio는 빠른 작업을 통해 필요한 셸 메서드를 생성 합니다.

![AJ_Studio_Code_2](../media/AllJoyn/AJ_Studio_Code_2.png)

메서드를 생성 하면 다음 셸 코드가 생성 됩니다.

![AJ_Studio_Code_3](../media/AllJoyn/AJ_Studio_Code_3.png)

올바른 논리를 사용 하 여 셸 코드를 채우면 소비자를 등록할 수 있습니다.

![AJ_Studio_Code_4](../media/AllJoyn/AJ_Studio_Code_4.png)

이 이벤트는 감시자가 생산자를 검색할 때마다 트리거됩니다.  여러 생산자를 찾아야 하는 경우 각 생산자에 대해 소비자가 하나씩 있으므로 소비자의 데이터 구조를 유지 합니다.

생산자가 내보내는 다양 한 신호에 대 한 이벤트 등록 – 속성 변경 신호는 소비자 클래스의 직접 멤버 이지만 다른 신호는 신호 클래스의 멤버입니다. 이전 처럼 빠른 작업을 사용 하 여 이러한 이벤트에 대 한 셸 코드를 생성 합니다.

![AJ_Studio_Code_5](../media/AllJoyn/AJ_Studio_Code_5.png)

소비자 개체를 사용 하 여 메서드를 호출 하는 것 뿐만 아니라 속성을 읽고 씁니다.

![AJ_Studio_Code_6](../media/AllJoyn/AJ_Studio_Code_6.png)

### <a name="implementing-an-alljoyn-producer"></a>AllJoyn 생산자 구현

__서비스 구현__

생산자는 인터페이스를 노출 하는 서비스를 구현 합니다.  생산자를 구현 하려면 먼저 해당 서비스에 대 한 클래스를 만듭니다.

![AJ_Studio_Code_7](../media/AllJoyn/AJ_Studio_Code_7.png)

인터페이스에 대 한 네임 스페이스를 "using" 문에 추가 하 고, 서비스에 대해 생성 된 셸 인터페이스를 상속 하 고, 빠른 작업을 사용 하 여 클래스를 구현 합니다.

![AJ_Studio_Code_8](../media/AllJoyn/AJ_Studio_Code_8.png)

여기서 빠른 작업은 필요한 구성 요소를 채웁니다.

![AJ_Studio_Code_9](../media/AllJoyn/AJ_Studio_Code_9.png)

코드의 모든 필요한 부분이 작동할 준비가 되었지만 각 메서드와 속성 호출에 대 한 실제 논리를 구현 해야 합니다.

![AJ_Studio_Code_10](../media/AllJoyn/AJ_Studio_Code_10.png)

SetDarknessLevelAsync를 예로 들어 보겠습니다. 작업을 사용 하 여 성공 결과를 만듭니다.  오류가 발생 하는 경우 ToasterSetDarknessLevelResult. CreateFailureResult ()을 반환 합니다.

![AJ_Studio_Code_11](../media/AllJoyn/AJ_Studio_Code_11.png)

나머지 메서드 및 속성 호출을 구현 하 여 서비스를 완료 합니다.

__생산자 구현__

생산자를 만드는 과정은 간단 합니다. 새 AllJoynBusAttachment을 만들고, 해당 AllJoynBusAttachment를 사용 하 여 생산자를 초기화 하 고, 생산자에 대해 새로 만든 서비스를 초기화 한 다음 생산자를 시작 합니다.

![AJ_Studio_Code_12](../media/AllJoyn/AJ_Studio_Code_12.png)

서비스에는 대부분의 논리가 포함 되어 있기 때문에 구현할 수 있는 주요 기능은 속성 변경에 대 한 신호를 보내는 것이 고, 비 상태 이벤트의 경우 불연속 신호를 보내는 것입니다.  메서드 호출을 통해 필요에 따라 구현 합니다.

![AJ_Studio_Code_13](../media/AllJoyn/AJ_Studio_Code_13.png)

__자세한 정보__

이 문서의 모든 지침을 제대로 완료 한 경우 앱에서 AllJoyn 코드 작성을 시작할 준비가 되었습니다.

참조를 위해 Microsoft 샘플 GitHub for [Alljoyn 생산자](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AllJoyn/ProducerExperiences) 및 [alljoyn 소비자](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AllJoyn/ConsumerExperiences)에 대 한 alljoyn 유니버설 Windows 앱 샘플을 확인 하세요.

AllJoyn 앱을 만드는 방법에 대 한 자세한 연습은 AllJoyn 세션 623을 시청 하세요.

> [!VIDEO https://channel9.msdn.com/Events/Build/2015/2-623/player]

Visual Studio에서 직접 배포 되는 경우와 같이 루프백 예외를 사용 하도록 설정 하지 않는 한 동일한 컴퓨터에서 두 UWP 앱 간의 AllJoyn 통신은 Windows 정책에 의해 사용 되지 않습니다.  루프백 예외를 사용 하는 방법에 대 한 자세한 내용은 [여기](https://msdn.microsoft.com/library/windows/apps/Hh780593.aspx)를 참조 하세요.



