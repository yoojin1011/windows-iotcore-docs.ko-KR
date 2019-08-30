---
title: AllJoyn 장치 시스템 브리지 개요
author: saraclay
ms.author: saclayt
ms.date: 09/06/17
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: 광범위 한 상호 운용성을 위해 alljoyn 장치를 AllJoyn 에코 시스템에 적응 하는 AllJoyn 장치 시스템 브리지에 대해 알아봅니다.
keywords: windows iot, AllJoyn
ms.openlocfilehash: 305629867bb85600b314fc34de268c46d90ce6e7
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "60167961"
---
> [!NOTE]
> 보관 된 설명서를 보고 있습니다. AllJoyn는 Windows 10 IoT에서 더 이상 지원 되지 않습니다. 질문이 있는 경우 GitHub에서 문제를 열거나 아래 설명에 의견을 남겨 주세요.

# <a name="alljoyn-device-system-bridge"></a>AllJoyn 장치 시스템 브리지

AllJoyn는 개발자에 게 다양 한 플랫폼 및 연결 기술을 사용 하 여 AllJoyn 에코 시스템에 대 한 장치를 구축할 수 있는 유연성을 제공 합니다.  그러나 대부분의 장치 제조업체는 포트폴리오에 기존 장치 솔루션을 포함 합니다. 이러한 상황에서 Microsoft는 DSB (장치 시스템 브리지)를 만들었습니다. DSB는 적용 되는 장치가 AllJoyn와 공통 언어로 상호 운용할 수 있도록 비-AllJoyn 장치를 AllJoyn 에코 시스템에 적응 합니다. Microsoft DSB는 Zigbee 및 Z Wave와 같은 홈 자동화 시스템을 지원 하 고 BACnet 같은 산업 빌드 자동화 시스템도 지원할 수 있습니다.  또한 소스 코드를 사용자 지정 하 여 다른 기술을 지원할 수 있습니다.

## <a name="how-dsb-works"></a>DSB 작동 방법

DSB의 핵심 기능은 AllJoyn 버스에서 장치의 가상 표현을 만드는 것입니다. 따라서 이러한 장치는 네이티브 연결 또는 장치 에코 시스템에 대해 모두 표시 되 고 AllJoyn 장치로 액세스할 수 있습니다. 두 DSBs 아래 그림에서 Z-웨이브 용으로 하나, ZigBee에 대 한 하나는 두 Z 웨이브의 가상 표현과 AllJoyn 버스의 ZigBee 장치 하나를 만듭니다. 이를 사용 하 여 AllJoyn 사이트의 모든 장치는 서로 통신할 수 있습니다. 이제는 모든 AllJoyn 버스에서 Z-Wave 및 ZigBee 장치가 서로 통신할 수 있습니다.

![AJ_Docu_DSB_Overview](../media/AllJoyn/AJ_Docu_DSB_Overview.png)

DSB 디자인의 또 다른 주요 요소는 AllJoyn 또는 비-장치 시스템에 대 한 변경이 필요 하지 않습니다. 필요한 모든 유발할는 dsb에서 수행 됩니다.

그림에 표시 된 것 처럼, AllJoyn 장치에서 비 AllJoyn 쪽으로의 매핑이 없습니다. DSB의 목표는 장치를 AllJoyn 에코 시스템으로 가져오는 것입니다. 한 가지 방법만 사용 하도록 설정 하면 개발이 간단해 집니다. 또한 잠재적으로 보안이 유지 되는 비 AllJoyn 장치 시스템에 의해 AllJoyn 보안 기능이 약화 될 위험이 줄어듭니다.

## <a name="dsb-architecture"></a>DSB 아키텍처

Microsoft 제안 DSB 아키텍처는 네트워크 액세스 스택, 어댑터 및 브리지의 세 가지 주요 구성 요소로 구성 됩니다. 아래 그림은이 아키텍처의 대략적인 개요를 보여 줍니다.

![AJ_Docu_DSB_Architecture](../media/AllJoyn/AJ_Docu_DSB_Architecture.png)

### <a name="bridge"></a>Bridge
* 각 내부 장치 개체를 각 장치에 대 한 별도의 버스 첨부 파일, AllJoyn 장치로 나타냅니다.
* 장치는 AllJoyn 버스에서 동적으로 추가 되거나 제거 됩니다.
* 구성에서 장치 표시 유형 및 보안 관리
* 브리지 및 어댑터 구성 인터페이스용 버스 첨부 파일 만들기
* 브리지 코드는 내부 장치 형식에 독립적 이며 모든 형식에 대해 다시 사용할 수 있습니다.

### <a name="adapter"></a>어댑터
* 비-AllJoyn 네트워크에서 각 장치를 대신 하 여 가상 장치를 인스턴스화하고 관리 합니다.
* 장치 스키마를 내부 장치 개체로 변환 합니다.
* 네트워크 리소스 (예: 액세스 키, 자격 증명)를 관리 합니다.

### <a name="network-access-stack"></a>네트워크 액세스 스택
* 비 AllJoyn 네트워크 관련 액세스 (예: Z-웨이브 스택)

## <a name="adapter-classes"></a>어댑터 클래스

아래 다이어그램에서는 개발자가 Microsoft DSB 템플릿에서 사용 하는 클래스를 사용 하 여 AllJoyn로 브리지로 브리지로 사용 해야 하는 네이티브 장치의 추상화를 만듭니다. 브리지는 어댑터 클래스의 인스턴스를 사용 하 여 어댑터. 장치 목록에서 각 장치에 대 한 버스 첨부 파일을 만듭니다.
![AJ_Docu_DSB_Class_Diagram](../media/AllJoyn/AJ_Docu_DSB_Class_Diagram.png)

## <a name="special-handlers"></a>특수 처리기

AllJoyn은 몇 가지 기본 서비스와 표준 인터페이스 프레임 워크 (예: LSF, HAE 또는 제어판)를 지정 합니다. DSB는 특수 한 처리기를 사용 하 여 이러한 것을 노출할 수 있습니다. 현재 DSB 템플릿 릴리스에는 LSF 및 제어판 인터페이스의 구현이 포함 되어 있습니다. 개발자는 브리지의 LSN 및 제어판 인터페이스에 대 한 콜백 함수에 해당 코드를 연결 합니다.

![AJ_Docu_DSB_Special_Handlers](../media/AllJoyn/AJ_Docu_DSB_Special_Handlers.png)

## <a name="dsb-resources"></a>DSB 리소스

### <a name="visual-studio-dsb-template"></a>Visual Studio DSB 템플릿

Visual Studio DSB 템플릿은 새 DSB 프로젝트를 쉽게 만들 수 있는 Visual Studio의 확장입니다. 이 프로젝트는 연결, 어댑터에 대 한 셸 프로젝트, 모든 솔루션 파일 등 모든 필수 구성 요소를 만들어 DSB를 단방향 또는 헤드리스 장치로 빌드합니다. 이 Visual Studio 확장에는 네이티브 및 관리 되는 AllJoyn 장치 시스템 브리지 템플릿이 모두 포함 되어 있습니다.

다음 위치에서 DSB 템플릿을 다운로드 합니다.

* [Visual Studio 2015 용 DSB 템플릿](https://visualstudiogallery.msdn.microsoft.com/aea0b437-ef07-42e3-bd88-8c7f906d5da8)
* [Visual Studio 2017](https://marketplace.visualstudio.com/vsgallery/c5f52768-8df7-42ff-b84e-d66d3d22fb50)
dsb 용 dsb 템플릿은_Visual Studio Tools > 확장 및 업데이트 ...-> 온라인-> "검색" 필드 형식 "dsb"를 통해 설치할 수도_ 있습니다.

[DSB 개체를 alljoyn에 매핑](AlljoynDsbApiGuide.md) 문서에서는 Alljoyn 시스템 브리지를 빌드하는 데 사용 되는 키 인터페이스 및 메서드에 대해 설명 합니다.

### <a name="sample-dsbs"></a>샘플 DSBs

* [AllJoyn DSB 모의 어댑터 자습서 및 샘플](https://developer.microsoft.com/en-us/windows/iot/samples/alljoynmockadapter)
  * 이 자습서에서는 장치 시스템 브리지 앱을 사용 하 여 IoT Core 장치를 모의 BACnet 장치에 연결 하는 방법을 보여 줍니다.
* [AllJoyn DSB Z-웨이브 어댑터 자습서 및 샘플](https://developer.microsoft.com/en-us/windows/iot/samples/zwaveadapter)
  * 이 자습서에서는 장치 시스템 브리지 앱을 사용 하 여 IoT Core 장치를 Z 웨이브 장치에 연결 하는 방법을 보여 줍니다.
* [AllJoyn DSB GPIO 어댑터 자습서C++](https://developer.microsoft.com/en-us/windows/iot/samples/alljoyndsb)
  * 이 자습서에서는 AllJoyn 장치 시스템 브리지 템플릿을 사용 하 여 장치 GPIO를 연습 하 C++ 는 샘플 앱을 만드는 방법을 보여 줍니다.
* [AllJoyn DSB GPIO 어댑터 자습서C#](https://developer.microsoft.com/en-us/windows/iot/samples/alljoyndsbcs)
  * 이 자습서에서는 AllJoyn 장치 시스템 브리지 템플릿을 사용 하 여 장치 GPIO를 연습 하는 샘플 관리 앱을 만드는 방법을 보여 줍니다.
* [AllJoyn DSB ZigBee Adapter 자습서 및 샘플](https://developer.microsoft.com/en-us/windows/iot/samples/ZigBeeAdapter)
  * 이 자습서에서는 장치 시스템 브리지 앱을 사용 하 여 IoT Core 장치를 ZigBee 장치에 연결 하는 방법을 보여 줍니다.
* [AllJoyn DSB BACnet Adapter 자습서 및 샘플](https://developer.microsoft.com/en-us/windows/iot/samples/BACnetAdapter)
  * 이 자습서에서는 장치 시스템 브리지 앱을 사용 하 여 IoT Core 장치를 BACnet 장치에 연결 하는 방법을 보여 줍니다.
* [AllJoyn 자습서](https://developer.microsoft.com/en-us/windows/iot/samples/AllJoynJS)
  * 이 자습서에서는 Allseen 동맹에서 개발한 응용 프로그램을 Windows 10 응용 프로그램으로 실행 하는 방법을 보여 줍니다. AllJoyn를 사용 하면 JavaScript를 작성 하 여 AllJoyn 장치를 만들고 모니터링 하 고 제어할 수 있습니다.
* [AllJoyn DSB OIC 어댑터 자습서 및 샘플](https://developer.microsoft.com/en-us/windows/iot/samples/OICAdapter)
  * 이 자습서에서는 장치 시스템 브리지 앱을 사용 하 여 IoT Core 장치를 IoTivity/OIC 장치에 연결 하는 방법을 보여 줍니다.
