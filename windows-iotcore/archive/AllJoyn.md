---
title: AllJoyn 개요
author: saraclay
ms.author: saclayt
ms.date: 09/06/17
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: AllJoyn, IoT 장치에 대 한 일반적인 프로토콜 및 기타 확장 및 Windows IoT를 사용 하 여 기능을 사용 하는 방법을 알아봅니다.
keywords: windows iot, AllJoyn
ms.openlocfilehash: 6b558680d479c71b6b8a22d34d03b04e5cbdbd76
ms.sourcegitcommit: 0f46b7b5c15906a6c82b847ffcd9f4d2674f9fd0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65226832"
---
> [!NOTE]
> 보관 된 설명서가 표시 됩니다. Windows 10 IoT에서 더 이상 AllJoyn 사용할 수 없습니다. 질문에 대 한 대체 AllJoyn에 사용 되는 앱 계층 IoT 프로토콜은는 [열린 연결 Foundation](https://openconnectivity.org)합니다. OCF 사양의 표준 구현은 Iotivity-Iotivity에 대 한 Windows 지원을 확인할 수 있습니다 [여기](https://wiki.iotivity.org/windows)합니다.

# <a name="alljoyn"></a>AllJoyn

AllJoyn은 Internet of Things 수 있도록 합니다. AllJoyn 장치 및 응용 프로그램을 검색 하 고 전송 기술, 플랫폼 또는 제조업체에 관계 없이 서로 통신은 일반 프로토콜을 정의 합니다.  AllJoyn는 여 기반 오픈 소스 표준 합니다 [AllSeen Alliance](https://allseenalliance.org/), 간 업계 컨소시엄 전용 수십억 개의 장치, 서비스 및 사물 인터넷에 대 한 응용 프로그램의 상호 운용성을 사용 하도록 설정 합니다.

Microsoft은 AllSeen Alliance 2014 년에 합류 하 고 Windows 10의 핵심 구성 요소로 AllJoyn를 추가 합니다. 기본 제공 [AllJoyn Api](https://msdn.microsoft.com/library/windows/apps/windows.devices.alljoyn.aspx), 개발자는 모든 Windows IoT Core를 사용 하 여 장치 뿐만 아니라 Pc, 태블릿, 휴대폰, Xbox를 포함 하 여 Windows 10 장치에서 실행 되는 AllJoyn 지원 응용 프로그램을 작성 합니다. Microsoft는 출시 AllJoyn 플랫폼 지원 외에도 [AllJoyn Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286)를 바로 사용할 수 있는 응용 프로그램 템플릿 사용 하 여 코드 생성을 결합 하 여 AllJoyn 개발을 가속화 하는 Visual Studio 확장입니다. AllJoyn Studio 개발자를 설치 및 구성 해야 하는 번거로움 없이 AllJoyn의 기능을 활용할 수 있습니다.

에 흥미가 AllJoyn 있으십니까? 살펴보겠습니다 [이](AllJoynStudio.md) AllJoyn Windows에서 시작 하는 방법에 대 한 블로그 게시물.


## <a name="developer-resources-and-tools"></a>개발자 리소스 및 도구

**장치 시스템 연결**

AllJoyn [장치 시스템 브리지](AllJoynDSB.md) AllJoyn 아닌 장치 AllJoyn을 공통 언어로 사용 하 여 AllJoyn 에코 시스템과 상호 작용할 수 있습니다.

기능:
* 어댑터에 의해 노출 된 각 AllJoyn 아닌 장치에 대 한 가상 장치를 만듭니다.
* 어댑터 장치에서 자동화 된 런타임 인터페이스 생성
* LSF, 더 많은 서비스를 추가 하는 확장 가능한 제어판 기본 서비스를 지원 합니다.
* 유니버설 앱 템플릿 (C#, C++), 데스크톱 UI 응용 프로그램 및 Windows IoT 시작 작업에 대 한
* 오픈 소스로 제공

자세한 내용은에서 확인할 수 있습니다 합니다 [장치 시스템 브리지 페이지](AllJoynDSB.md)합니다.


**AllJoyn Studio**

[AllJoyn Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286) 는 자동화 된 프로젝트 관리 및 바로 사용할 수 있는 응용 프로그램 템플릿을 사용 하 여 코드 생성 및 WinRT API를 결합 하 여 AllJoyn® 개발을 가속화 하는 Microsoft에서 개발한 Visual Studio를 확장 합니다. 개발자를 설치 및 구성 해야 하는 번거로움 없이 AllJoyn의 기능을 활용할 수 있습니다.

기능:
* 유니버설 앱 템플릿 (C#, JavaScript C++, Visual Basic)
* 자동화 된 참조 관리 및 프로젝트 구성
* 솔루션에서 인터페이스를 추가/제거
* AllJoyn® 메뉴를 통해 프로젝트 관리에 쉽게 액세스할 수
* 검사 XML 파일에서 인터페이스를 로드합니다.
* network1에 producer(s)에서 인터페이스를 검색합니다.

AllJoyn Studio를 통해 설치할 수 Visual Studio Tools-> 확장 및 업데이트 하는 중... 온라인-> "검색" 필드 형식 "AllJoyn"->

사용할 수 있는 AllJoyn Studio를 사용 하는 방법에 대 한 자세한 정보 [여기](AllJoynStudio.md)합니다.

**AllJoyn (AllJoyn 탐색기)에 대 한 IoT 탐색기**

AllJoyn (이전의 AllJoyn 탐색기)에 대 한 IoT 탐색기는 Windows 유니버설 응용 프로그램을 가까운 지역의 네트워크에 있는 AllJoyn 장치와 상호 작용 하는 것을입니다. 개발자가 모든 사용 가능한 AllJoyn 장치 목록, 해당 인터페이스 및 개체 구조를 검사 뿐만 아니라 신호를 받을, 설정 및 속성을 가져오기 하 고 메서드를 호출.

* [AllJoyn 스토어 앱 용 IoT 탐색기](https://www.microsoft.com/store/apps/9nblggh6gpxl): 공식 스토어 앱 위치입니다.
* [AllJoyn 탐색기 (이전 릴리스) 1.0.1.11](https://github.com/ms-iot/samples/releases/download/AllJoynExplorer_1.0.11/AllJoynExplorer_1.0.1.11.zip): 이 zip 개발자 컴퓨터에 테스트용으로 로드 되도록 AllJoyn 탐색기 AppX 번들을 포함 합니다. AllJoyn 응용 프로그램에 대 한 IoT 탐색기의 이전에 출시 된 버전입니다.
* [AllJoyn 탐색기 설치 가이드](https://github.com/ms-iot/samples/releases/download/AllJoynExplorer_1.0.11/AllJoyn_Explorer_Setup_Guide_v1.0.pdf): 이 pdf AllJoyn Explorer를 배포 하는 방법에 대 한 설명서를 포함 합니다.
* [AllJoyn 탐색기 사용자 가이드](https://github.com/ms-iot/samples/releases/download/AllJoynExplorer_1.0.11/AllJoyn_Explorer_User_Guide_v1.0.pdf): 이 pdf AllJoyn 탐색기를 사용 하는 방법에 대 한 설명서를 포함 합니다.


### <a name="additional-resources"></a>추가 리소스

* [AllJoyn Studio 확장을 사용 하 여](AllJoynStudio.md)
* [AllJoyn 생산자 및 AllJoyn 검사를 작성 합니다.](AllJoynProducer.md)
* [Windows 10 함께 AllJoyn 문제 해결](AllJoynTroubleshooting.md)

**비디오**

* [//build 2015 AllJoyn Technical Session](https://channel9.msdn.com/Events/Build/2015/2-623)
* [WinHEC 2015 AllJoyn 기술 세션](https://channel9.msdn.com/Events/WinHEC/2015/IOT200)

**샘플**

* [AllJoyn 생산자](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AllJoyn/ProducerExperiences)
* [AllJoyn 소비자](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AllJoyn/ConsumerExperiences)
* [AllJoyn UWP 샘플 (MSDN)](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AllJoyn/ConsumerExperiences)

**참조**

* [Windows 10 (MSDN)에서 AllJoyn Api](https://msdn.microsoft.com/library/windows/apps/xaml/windows.devices.alljoyn.aspx)
* [AllJoyn 아키텍처 세부 정보 (Allseen Alliance)](https://allseenalliance.org/developers/learn/)
* [AllJoyn 개발자 리소스 (Allseen Alliance)](https://allseenalliance.org/developers/develop/)
* [AllJoyn C API Reference Manual (Allseen Alliance)](https://allseenalliance.org/docs/api/c/index.html)

