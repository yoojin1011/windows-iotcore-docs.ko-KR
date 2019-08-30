---
title: AllJoyn 개요
author: saraclay
ms.author: saclayt
ms.date: 09/06/17
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: Windows IoT에서 다른 확장 및 기능을 사용 하도록 설정 하는 방법 및 IoT 장치에 대 한 일반적인 프로토콜인 AllJoyn에 대해 알아봅니다.
keywords: windows iot, AllJoyn
ms.openlocfilehash: 6b558680d479c71b6b8a22d34d03b04e5cbdbd76
ms.sourcegitcommit: 0f46b7b5c15906a6c82b847ffcd9f4d2674f9fd0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65226832"
---
> [!NOTE]
> 보관 된 설명서를 보고 있습니다. AllJoyn는 Windows 10 IoT에서 더 이상 지원 되지 않습니다. 질문에 대 한 대안 인 경우 AllJoyn에 사용 되는 앱 계층 IoT 프로토콜은 [오픈 연결 기반이](https://openconnectivity.org)됩니다. OCF 사양의 표준 구현은 Iotivity입니다. Iotivity에 대 한 Windows 지원은 [여기](https://wiki.iotivity.org/windows)에서 찾을 수 있습니다.

# <a name="alljoyn"></a>AllJoyn

AllJoyn은 사물 인터넷를 강화 합니다. AllJoyn은 장치 및 응용 프로그램이 전송 기술, 플랫폼 또는 제조업체와 관계 없이 서로를 검색 하 고 통신 하는 데 사용할 수 있는 공통 프로토콜을 정의 합니다.  AllJoyn는 사물 인터넷에 대 한 수십억 개의 장치, 서비스 및 응용 프로그램의 상호 운용성을 사용 하도록 설정 하는 데 사용 되는 다중 업계 컨소시엄 인 [Allseen 동맹](https://allseenalliance.org/)에 의해 구동 되는 오픈 소스 표준입니다.

Microsoft는 Windows 10에서 Windows 10의 핵심 구성 요소로, 2014에 AllSeen 동맹을 조인 했습니다. 기본 제공 [Alljoyn api](https://msdn.microsoft.com/library/windows/apps/windows.devices.alljoyn.aspx)를 사용 하는 개발자는 pc, 태블릿, 휴대폰, Xbox 뿐만 아니라 Windows IoT Core를 사용 하는 장치를 비롯 한 모든 windows 10 장치에서 실행 되는 AllJoyn 지원 응용 프로그램을 자유롭게 작성할 수 있습니다. Microsoft에서는 alljoyn에 대 한 플랫폼 지원 외에도 미리 만들어진 응용 프로그램 템플릿과 코드 생성을 결합 하 여 AllJoyn 개발을 가속화 하는 Visual Studio 확장인 [Alljoyn studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286)를 출시 했습니다. 개발자는 AllJoyn Studio를 사용 하 여 설정 및 구성을 하지 않고도 AllJoyn 기능을 활용할 수 있습니다.

AllJoyn이 있나요? Windows에서 AllJoyn를 시작 하는 방법에 대 한 [이](AllJoynStudio.md) 블로그 게시물을 살펴보세요.


## <a name="developer-resources-and-tools"></a>개발자 리소스 및 도구

**장치 시스템 브리지**

AllJoyn [장치 시스템 브리지](AllJoynDSB.md) 를 사용 하면 비 alljoyn 장치에서 alljoyn를 공용 언어로 사용 하 여 alljoyn 에코 시스템과 상호 작용할 수 있습니다.

기능:
* 어댑터에서 노출 하는 각 비 AllJoyn 장치에 대 한 가상 장치를 만듭니다.
* 어댑터 장치에서 자동화 된 런타임 인터페이스 생성
* LSF, 제어판 기본 서비스를 지원 하 고 확장 가능한 서비스를 추가 합니다.
* 유니버설 앱 템플릿 (C#, C++), 데스크톱 UI 응용 프로그램 및 Windows IoT 시작 작업
* 오픈 소스로 사용 가능

자세한 내용은 [장치 시스템 브리지 페이지](AllJoynDSB.md)에서 찾을 수 있습니다.


**AllJoyn Studio**

[Alljoyn 스튜디오](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286) 는 자동화 된 프로젝트 관리 및 미리 만들어진 응용 프로그램 템플릿과 코드 생성 및 WinRT API를 결합 하 여 alljoyn® 개발을 가속화 하는 Microsoft에서 개발 된 Visual Studio의 확장입니다. 개발자는 이러한 기능을 통해 설정 및 구성을 하지 않고도 AllJoyn의 기능을 활용할 수 있습니다.

기능:
* 유니버설 앱 템플릿 (C#, JavaScript, C++Visual Basic)
* 자동화 된 참조 관리 및 프로젝트 구성
* 솔루션에 대 한 인터페이스 추가/제거
* AllJoyn® 메뉴를 통해 프로젝트 관리에 쉽게 액세스
* 검사 XML 파일에서 인터페이스를 로드 하는 중
* D 1의 생산자에서 인터페이스를 검색 하는 중

Visual Studio Tools > 확장 및 업데이트를 통해 AllJoyn Studio를 설치할 수 있습니다. -> 온라인-"검색" 필드 형식 "AllJoyn"의 >

AllJoyn Studio를 사용 하는 방법에 대 한 자세한 내용은 [여기](AllJoynStudio.md)에서 제공 됩니다.

**AllJoyn 용 IoT Explorer (AllJoyn 탐색기)**

AllJoyn 용 IoT 탐색기 (이전에는 AllJoyn 탐색기)는 로컬 근접 네트워크에서 AllJoyn 장치와 상호 작용 하기 위한 Windows 유니버설 응용 프로그램입니다. 개발자는 사용 가능한 모든 AllJoyn 장치를 나열 하 고, 인터페이스 및 개체 구조를 검사 하 고, 신호를 수신 하 고, 속성을 설정 및 가져오고, 메서드를 호출할 수 있습니다.

* [AllJoyn 스토어 앱 용 IoT 탐색기](https://www.microsoft.com/store/apps/9nblggh6gpxl): 이는 공식 스토어 앱 위치입니다.
* [AllJoyn 탐색기 1.0.1.11 (이전 릴리스)](https://github.com/ms-iot/samples/releases/download/AllJoynExplorer_1.0.11/AllJoynExplorer_1.0.1.11.zip): 이 zip에는 개발자 컴퓨터에 테스트용으로 로드 될 AllJoyn 탐색기 AppX 번들이 포함 되어 있습니다. 이는 이전에 릴리스된 버전의 AllJoyn 응용 프로그램용 IoT 탐색기입니다.
* [AllJoyn 탐색기 설치 가이드](https://github.com/ms-iot/samples/releases/download/AllJoynExplorer_1.0.11/AllJoyn_Explorer_Setup_Guide_v1.0.pdf): 이 pdf에는 AllJoyn 탐색기를 배포 하는 방법에 대 한 설명서가 포함 되어 있습니다.
* [AllJoyn 탐색기 사용자 가이드](https://github.com/ms-iot/samples/releases/download/AllJoynExplorer_1.0.11/AllJoyn_Explorer_User_Guide_v1.0.pdf): 이 pdf에는 AllJoyn 탐색기를 사용 하는 방법에 대 한 설명서가 포함 되어 있습니다.


### <a name="additional-resources"></a>추가 리소스

* [AllJoyn Studio 확장 사용](AllJoynStudio.md)
* [AllJoyn 생산자 및 Authoring 검사](AllJoynProducer.md)
* [Windows 10을 사용 하 여 AllJoyn 문제 해결](AllJoynTroubleshooting.md)

**비디오**

* [빌드 2015 AllJoyn 기술 세션](https://channel9.msdn.com/Events/Build/2015/2-623)
* [WinHEC 2015 AllJoyn 기술 세션](https://channel9.msdn.com/Events/WinHEC/2015/IOT200)

**샘플**

* [AllJoyn 생산자](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AllJoyn/ProducerExperiences)
* [AllJoyn 소비자](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AllJoyn/ConsumerExperiences)
* [AllJoyn UWP 샘플 (MSDN)](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AllJoyn/ConsumerExperiences)

**참조**

* [Windows 10의 AllJoyn Api (MSDN)](https://msdn.microsoft.com/library/windows/apps/xaml/windows.devices.alljoyn.aspx)
* [AllJoyn 아키텍처 세부 정보 (Allseen 동맹)](https://allseenalliance.org/developers/learn/)
* [AllJoyn 개발자 리소스 (Allseen 동맹)](https://allseenalliance.org/developers/develop/)
* [AllJoyn C API 참조 수동 (Allseen 동맹)](https://allseenalliance.org/docs/api/c/index.html)

