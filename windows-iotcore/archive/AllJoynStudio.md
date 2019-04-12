---
title: AllJoyn Studio
author: saraclay
ms.author: saclayt
ms.date: 09/07/17
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: 유니버설 Windows 플랫폼 (UWP) AllJoyn Api 및 Visual Studio 2017을 사용 하 여 AllJoyn UWP 앱을 만드는 방법에 알아봅니다.
keywords: windows iot, AllJoyn
ms.openlocfilehash: 5326873218c0126b918679308e3a8e08cdddf84c
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513725"
---
> [!NOTE]
> 보관 된 설명서가 표시 됩니다. Windows 10 IoT에서 더 이상 AllJoyn 사용할 수 없습니다. 질문에 대 한 GitHub에서 문제를 제기 하거나 아래 설명에 의견을 남길 하세요.

# <a name="using-the-alljoyn-studio-extension"></a>AllJoyn Studio 확장을 사용 하 여

합니다 [AllSeen Alliance](https://allseenalliance.org/) AllJoyn Internet of Things 부서를 생성 합니다. Windows 10 개발자가 쉽게 활용 하도록 AllJoyn "IoT-enable" Windows 10 앱에는 플랫폼에 기본적으로 내장 AllJoyn에 있습니다. 이 문서는 Visual Studio 2017 및 유니버설 Windows 플랫폼 (UWP) AllJoyn Api를 사용 하 여 Windows 10 용 앱을 빌드하는 데 필요한 단계를 간략하게 설명 [AllJoyn Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286) 확장 합니다.

## <a name="understanding-alljoyn-uwp-app-development"></a>AllJoyn UWP 앱 개발을 이해

세 가지 주요 구성 요소 폼 AllJoyn UWP 앱:

1. 앱 레이아웃 및 디자인 (XAML 또는 HTML) 및 구성 요소 클래스 (C#, JavaScript C++, 또는 VB).
2. AllJoyn core Api: AllJoyn Standard Client API (C) 및 Windows.Devices.AllJoyn API (WinRT) Windows 10 SDK에서 사용할 수 있습니다.
3. 하나 이상의 UWP Windows 런타임 구성 요소 (의 AllJoyn 인터페이스에서이 코드 생성).

다음 다이어그램은 일반적인 AllJoyn UWP 프로젝트의 아키텍처를 보여줍니다.

![AJ_UWP_Architecture](../media/AllJoyn/AJ_UWP_Architecture.jpg)

UWP 앱 AllJoyn 사용 하거나 생산자를 수 있습니다 (구현 및 인터페이스를 장치에 일반적으로 표시) (일반적으로 앱 인터페이스 사용) 소비자 또는 둘 다. 소비자 및 생산자는 동일한 시작 단계를을 공유는 구현 세부 정보에만 다양 합니다.

## <a name="creating-an-alljoyn-enabled-uwp-app"></a>UWP AllJoyn 사용 앱을 만드는 방법

Windows 10 용 UWP AllJoyn 사용 앱을 개발 하려면 다음이 단계를 수행 합니다. (이 문서의 뒷부분에 자세히 설명)

1. 빌드 환경을 준비 합니다.
2. 인터페이스는, 및를 만들거나 가져와야 필요한 검사 XML에 있는 AllJoyn를 결정 합니다.
3. AllJoyn 앱 프로젝트를 만든 다음 코드 생성에 대 한 검사 XML 및 원하는 인터페이스를 선택 합니다.
4. 생성 된 UWP Windows 런타임 구성 요소에서 노출 된 Api를 사용 하 여 앱에서 생산자 또는 ponsumer 코드를 구현 합니다.
5. UI를 빌드하십시오.

## <a name="preparing-your-build-environment"></a>빌드 환경 준비

Windows 10 빌드 및 관련된 도구를 모든 UWP AllJoyn 사용 앱을 작성 해야 하는 리소스를 포함 합니다.

코드 작성 시작 하기 전에 수행 해야 다음과 같습니다.

* 설치할 [Windows 10](https://www.microsoft.com/windows/) PC에서
* 설치할 [Visual Studio 2017](https://www.visualstudio.com/downloads/download-visual-studio-vs) (Express edition을 사용 하지 마십시오)
* 다운로드 합니다 [AllJoyn® Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286) Visual Studio 갤러리에서 확장 합니다. 


## <a name="obtaining-introspection-xml-for-alljoyn-interfaces"></a>AllJoyn 인터페이스에 대 한 검사 XML 가져오기

프로젝트를 시작 해야 하는 AllJoyn 인터페이스 정의 얻을 수 있는 방법은 세 가지가 있습니다.

1. 런타임 시 네트워크에 있는 AllJoyn 생산자에서 검사 XML을 추출 합니다.
2. 검사 XML 문서에서 가져오기 예: [서비스 프레임 워크 (LSF) 설명서를 조명](https://wiki.allseenalliance.org/_media/compliance/alljoyn_lamp_service_14.06_interface_definition.pdf) AllSeen Alliance에서.
3. AllJoyn 호환 되는 고유한 검사 XML 만듭니다 /[D Bus 검사](http://dbus.freedesktop.org/doc/dbus-specification.html) 형식입니다.

이 문서에서는 처음 두 가지 방법-AllJoyn® Studio 기본적으로 지 원하는 네트워크 AllJoyn 생산자에 대 한 쿼리 및 해당 XML 추출 뿐만 아니라 검사 XML 파일을 업로드 합니다.  나만의 사이트 생성 하는 방법을 알아봅니다 [여기](AllJoynProducer.md)합니다.

토스터 AllJoyn 사용 장치를이 게시물에 대 한 예제로 사용 됩니다. 이 토스터 시작 하 고 알림을 버린 경우 toasting 시퀀스, "어둠" 설정 및 알림 중지에 대 한 컨트롤을 표시 합니다.

![AJ_toaster](../media/AllJoyn/AJ_toaster.jpg)

토스터는 다음 XML을 노출합니다.

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

일반적으로 동일한 방식으로 프로젝트를 만듭니다. 클릭 `File->New->New Project` 시작 합니다.

![AJ_Studio_NewProject](../media/AllJoyn/AJ_Studio_NewProject.png)

Windows 유니버설 템플릿을 탐색 하는 대신 확장을 사용 하 여 설치 된 대상 언어에 대 한 "AllJoyn App" 템플릿을 선택 합니다.  프로젝트 이름을 지정 하 고 개발을 시작 하려면 파일 위치를 선택 합니다.

![AJ_Studio_NameProj](../media/AllJoyn/AJ_Studio_NameProj.png)

AllJoyn 앱 템플릿의 선택한 후 즉시 Visual Studio 프로젝트에 포함 하려는 AllJoyn 인터페이스를 선택할 수 있습니다 묻습니다. 

![AJ_Studio_Interfaces](../media/AllJoyn/AJ_Studio_Interfaces.png)

__네트워크의 장치에서 인터페이스 추출__

AllJoyn 장치 또는 네트워크 인터페이스를 찾을 수 없는 경우에 따라 [이 가이드](AllJoynTroubleshooting.md) 문제를 해결 하려면. 

![AJ_Studio_FindDevices](../media/AllJoyn/AJ_Studio_FindDevices.png)

노출 된 인터페이스에 대 한 네트워크를 쿼리하려면 왼쪽 패널에서 "네트워크에서 생산자"를 선택 합니다. 인터페이스를 지 원하는 네트워크 및 목록에 있는 AllJoyn 생산자를 찾을 수이 합니다.

![AJ_Studio_ListDevices](../media/AllJoyn/AJ_Studio_ListDevices.png)

프로젝트에 포함 하려면 원하는 인터페이스를 선택 합니다.  이 경우에서는 사용 하는 토스터 인터페이스 "org.alljoyn.example.Toaster" 인터페이스에만 선택 합니다.

![AJ_Studio_SelectDevices](../media/AllJoyn/AJ_Studio_SelectDevices.png)

"작업" 열에는 새로 선택한 인터페이스에 대 한 "추가"를 표시 합니다. 프로젝트에 보류 중인 변경 내용을 설명 합니다. 여기에서는 부여한 인터페이스 적용할 "이름 바꾸기" 작업을 트리거하는 "ToasterLibrary" 친숙 한 이름입니다.

![AJ_Studio_DeviceAction](../media/AllJoyn/AJ_Studio_DeviceAction.png)

__파일에서 XML 로드__

포함 된 해당 인터페이스를 확인 하려면 "찾아보기" 단추를 통해 검사 XML 파일을 선택 합니다.

![AJ_Studio_BrowseXML](../media/AllJoyn/AJ_Studio_BrowseXML.png)

탐색 하 고 적절 한 XML 선택 (여기서 toaster.xml 사용).

![AJ_Studio_BrowseXML_2](../media/AllJoyn/AJ_Studio_BrowseXML_2.png)

한 번 AllJoyn® Studio에서 XML 로드, 다양 한 인터페이스를 구문 분석 하 고 및 수 있도록 그 안에 포함 된 설명을 지원 하려는 하는 인터페이스를 선택 합니다.

![AJ_Studio_BrowseXML_3](../media/AllJoyn/AJ_Studio_BrowseXML_3.png)

"작업" 열에는 새로 선택한 인터페이스에 대 한 "추가"를 표시 합니다. 프로젝트에 보류 중인 변경 내용을 설명 합니다.

![AJ_Studio_BrowseXML_4](../media/AllJoyn/AJ_Studio_BrowseXML_4.png)

여기로 했습니다 "org.alljoyn.example.Toaster" 인터페이스를 포함 하 고 "ToasterLibrary" 친숙 한 이름에 제공 하면 적용할 "이름 바꾸기" 작업 트리거.

![AJ_Studio_BrowseXML_5](../media/AllJoyn/AJ_Studio_BrowseXML_5.png)

__추가 및 인터페이스를 제거 합니다.__

다음이 단계를 완료 한 후 생성된 된 파일 자동으로 추가 됩니다는 C++ 위의 및 응용 프로그램 프로젝트에 대 한 참조로 추가에서 이름으로 Windows 런타임 구성 요소입니다.  그러나 루트 Namespace은 여전히는 동일한 "org.alljoyn.example.Toaster"으로 인터페이스에서 정의 합니다.  이러한 구성 요소에 액세스 하는 모든 클래스는 구성 요소의 루트 네임 스페이스에 대 한 "using" 절을 포함 해야 합니다.

![AJ_Studio_SolutionExplorer](../media/AllJoyn/AJ_Studio_SolutionExplorer.png)

_팁: IntelliSense의 이점을 얻기 위해서는 이제 생성 된 구성 요소를 빌드하십시오._

AllJoyn 앱 솔루션을 만든 후 항상 돌아가서 고 사용 하는 인터페이스를 수정할 수 있습니다. 주 메뉴 모음에서 "AllJoyn-> 추가/제거 인터페이스..." 클릭 인터페이스 관리자를 시작 합니다.

![AJ_Studio_AddInterfaces](../media/AllJoyn/AJ_Studio_AddInterfaces.png)

여기에서 "찾아보기..."를 클릭 수 있습니다. XML 파일을 추가 하거나 기존 인터페이스를 선택 취소 합니다. 해당 작업을 "제거" 하 고 확인 단추를 클릭 하는 인터페이스 업데이트를 선택 취소 솔루션에서 연결된 된 Windows 런타임 구성 요소를 제거 합니다.

![AJ_Studio_AddXML](../media/AllJoyn/AJ_Studio_AddXML.png)

솔루션 탐색기를 보면 Windows 런타임 구성 요소 제거 되었습니다.

![AJ_Studio_SolutionExplorer_2](../media/AllJoyn/AJ_Studio_SolutionExplorer_2.png)

## <a name="next-steps"></a>다음 단계

AllJoyn 기능을 구현할 때 항상 해야 "Windows.Devices.AllJoyn" 네임 스페이스에 사용 하려는 인터페이스에서 네임 스페이스를 포함 합니다.

![AJ_Studio_namespace](../media/AllJoyn/AJ_Studio_namespace.png)

__AllJoyn 소비자를 구현합니다.__

인터페이스에 대해 생성 된 코드 찾기 및 다음 생산자를 제어 하는 데 사용 하는 감시자 및 소비자 클래스를 포함 합니다. 새 AllJoynBusAttachment 만들어 감시자 구현, 해당 AllJoynBusAttachment 사용 하 여 감시자를 초기화, 생산자 ("추가" 이벤트)을 찾는 감시자에 대 한 등록 다음 감시자를 시작 합니다.

![AJ_Studio_Code_1](../media/AllJoyn/AJ_Studio_Code_1.png)

감시자는 생산자를 발견 될 때마다 ToasterWatcher_Added 이벤트 트리거.  이 이벤트를 사용 하 여 소비자를 등록 합니다. Visual Studio에서 빠른 작업을 통해 필요한 셸 메서드를 생성 하는 참고 합니다.

![AJ_Studio_Code_2](../media/AllJoyn/AJ_Studio_Code_2.png)

다음 셸 코드를 생성 메서드를 생성 합니다.

![AJ_Studio_Code_3](../media/AllJoyn/AJ_Studio_Code_3.png)

올바른 논리를 사용 하 여 셸 코드를 해소 소비자를 등록할 수 있습니다.

![AJ_Studio_Code_4](../media/AllJoyn/AJ_Studio_Code_4.png)

감시자 생산자 검색 될 때마다이 이벤트를 트리거하는 참고 합니다.  여러 생산자를 찾으려는 경우 각 공급자에 대 한 하나의 소비자로 소비자의 데이터 구조를 유지 합니다.

다양 한 생산자는 내보냅니다 – 신호 속성 변경 이벤트 등록 신호 소비자 클래스의 직접 구성원 이지만 다른 신호 (방금 전 처럼, 사용 하 여 이러한 이벤트에 대 한 셸 코드를 생성 하려면 빠른 작업) 신호 클래스의 멤버는 합니다.

![AJ_Studio_Code_5](../media/AllJoyn/AJ_Studio_Code_5.png)

소비자 개체를 사용 하 여 읽기 및 쓰기 속성 뿐만 아니라 메서드를 호출 합니다.

![AJ_Studio_Code_6](../media/AllJoyn/AJ_Studio_Code_6.png)

### <a name="implementing-an-alljoyn-producer"></a>AllJoyn 생산자를 구현합니다.

__서비스 구현__

생산자는 해당 인터페이스를 노출 하는 서비스를 구현 합니다.  생산자를 구현 하려면 먼저 해당 서비스에 대 한 클래스를 만듭니다.

![AJ_Studio_Code_7](../media/AllJoyn/AJ_Studio_Code_7.png)

인터페이스에 대 한 네임 스페이스를 "using" 문을 추가 하 고 서비스에 대해 생성 된 셸 인터페이스를 상속할 클래스를 구현 하려면 빠른 작업을 사용 합니다.

![AJ_Studio_Code_8](../media/AllJoyn/AJ_Studio_Code_8.png)

여기에서 빠른 작업을 필요한 구성 요소 입력 됩니다.

![AJ_Studio_Code_9](../media/AllJoyn/AJ_Studio_Code_9.png)

코드의 모든 필요한 부품 함수 준비가 되었지만 각 메서드 및 속성 호출에 대 한 실제 논리를 구현 해야 합니다.

![AJ_Studio_Code_10](../media/AllJoyn/AJ_Studio_Code_10.png)

작업을 사용 하 여 성공 결과 만드는 예를 들어 SetDarknessLevelAsync를 수행 합니다.  오류가 발생 한 경우 ToasterSetDarknessLevelResult.CreateFailureResult()를 반환 합니다.

![AJ_Studio_Code_11](../media/AllJoyn/AJ_Studio_Code_11.png)

서비스를 완료 하려면 메서드 및 속성 호출의 나머지 부분을 구현 합니다.

__생산자를 구현합니다.__

생산자를 만드는 과정은 간단 – 새 AllJoynBusAttachment 만든, 해당 AllJoynBusAttachment 사용 하 여 생산자를 초기화, 생산자, 새로 만든된 서비스를 초기화한 다음 생산자를 시작 합니다.

![AJ_Studio_Code_12](../media/AllJoyn/AJ_Studio_Code_12.png)

대부분의 논리를 포함 하는 서비스에 있으므로 구현 과정이 남아 주요 기능을 속성 변경에 대 한 신호 및 비 상태 이벤트에 대 한 불연속 신호를 보내는 것입니다.  메서드 호출을 통해 필요에 따라이 구현 합니다.

![AJ_Studio_Code_13](../media/AllJoyn/AJ_Studio_Code_13.png)

__추가 정보__

이 문서에서 지침의 모든 올바르게 완료 했다면, 앱에서 AllJoyn 코드 작성을 시작할 준비가 되었습니다.

참조를 확인 하세요 AllJoyn 유니버설 Windows 앱 샘플에 대 한 Microsoft 샘플 github [AllJoyn 생산자](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AllJoyn/ProducerExperiences) 하 고 [AllJoyn 소비자](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AllJoyn/ConsumerExperiences)합니다.

AllJoyn 앱을 만드는 방법의 자세한 연습 과정에서는 623 AllJoyn 세션을 시청 하세요.

> [!VIDEO https://channel9.msdn.com/Events/Build/2015/2-623/player]

이러한 경우와 같이 루프백 예외를 활성화 하지 않은 Windows 정책에 의해 AllJoyn 통신 동일한 컴퓨터에 두 개의 UWP 앱은 비활성화 되었음을 참고 Visual Studio에서 직접 배포 중입니다.  루프백 예외를 사용 하도록 설정 하는 방법은 참조 하세요 [여기](https://msdn.microsoft.com/library/windows/apps/Hh780593.aspx)합니다.



