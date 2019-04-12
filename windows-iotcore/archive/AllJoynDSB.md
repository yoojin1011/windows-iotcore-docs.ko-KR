---
title: AllJoyn 장치 시스템 연결 개요
author: saraclay
ms.author: saclayt
ms.date: 09/06/17
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: 광범위 한 상호 운용성을 위해 AllJoyn 에코 시스템에 비 AllJoyn 장치 적응할 수 있는 AllJoyn 장치 시스템 연결에 알아봅니다.
keywords: windows iot, AllJoyn
ms.openlocfilehash: 305629867bb85600b314fc34de268c46d90ce6e7
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512469"
---
> [!NOTE]
> 보관 된 설명서가 표시 됩니다. Windows 10 IoT에서 더 이상 AllJoyn 사용할 수 없습니다. 질문에 대 한 GitHub에서 문제를 제기 하거나 아래 설명에 의견을 남길 하세요.

# <a name="alljoyn-device-system-bridge"></a>AllJoyn 장치 시스템 연결

AllJoyn 자유롭게 AllJoyn 에코 시스템에 대 한 장치 빌드에 광범위 한 플랫폼 및 연결 기술을 사용 하 여 개발자에 게 제공 합니다.  그러나 많은 장치 제조업체 경우 기존 장치 솔루션 포트폴리오 이러한 상황에 대 한 Microsoft 장치 시스템 브리지 (DSB)를 만들었습니다. DSB 맞게 조정된 장치를 공통 언어로 AllJoyn 상호 운용할 수 있도록 AllJoyn 에코 시스템에 AllJoyn 아닌 장치를 변경 합니다. Microsoft DSB Zigbee, 등 Z-wave를 자동화 시스템 홈 지원과 지원 산업 BACnet 같은 자동화 시스템을 구축할 수 있습니다.  또한, 소스 코드는 다른 기술을 지원 하기 위해 사용자 지정에 대 한 사용 가능

## <a name="how-dsb-works"></a>DSB의 작동 원리

DSB의 주요 기능이 AllJoyn 버스에 가상 장치 표현을 만드는 것입니다. 이러한 장치는 네이티브 연결 또는 장치 에코 시스템은 모든 표시 되 고 AllJoyn 장치로 액세스할 수 있습니다. 두 DSBs 아래 그림에서는 Z-wave에 대 한 개와 ZigBee AllJoyn 버스의 두 Z-wave와 하나의 ZigBee 장치의 가상 표현을 생성 합니다. AllJoyn에서이 모든 장치를 사용 하 여 사이트는 서로 통신할 수 있습니다. AllJoyn 버스에 모든 ZigBee 장치와 Z-wave 통신할 수 없기 때문에 이제 수 서로 합니다.

![AJ_Docu_DSB_Overview](../media/AllJoyn/AJ_Docu_DSB_Overview.png)

DSB 디자인의 또 다른 핵심 요소는 AllJoyn 또는 비 AllJoyn 장치 시스템 변경 필요 하지 것입니다. 모든 필요한 도입 된 DSB에서 수행 됩니다.

또한 그림과 같이 비 AllJoyn 쪽 AllJoyn 장치의 매핑이 지원 되지 않습니다. DSB의 목표는 AllJoyn 에코 시스템으로 장치를 가져오는 것입니다. 하나의 방법을 개발을 간소화 합니다. 위험이 해당 AllJoyn 안전 하지 않은 AllJoyn 장치 시스템 보안 기능 약화 될 수도 줄어듭니다.

## <a name="dsb-architecture"></a>DSB 아키텍처

Microsoft 제안 DSB 아키텍처 브리지, 어댑터 및 네트워크 액세스 스택의 세 가지 주요 구성 요소로 구성 됩니다. 아래 그림은이 아키텍처의 대략적인 개요를 보여줍니다.

![AJ_Docu_DSB_Architecture](../media/AllJoyn/AJ_Docu_DSB_Architecture.png)

### <a name="bridge"></a>브리지
* 각 장치에 대 한 별도 버스 첨부 AllJoyn 장치로 각 내부 장치 개체를 나타냅니다.
* 장치 동적으로 추가 되거나 AllJoyn 버스에서 제거
* 장치 유형과 보안 구성 관리
* 브리지와 어댑터 구성 인터페이스에 bus 첨부 파일을 만듭니다.
* 브리지 코드는 내부 디바이스를 다시 사용할 수 있는 모든 형식에 대 한 알 수 없는

### <a name="adapter"></a>어댑터
* 인스턴스화하고 AllJoyn 비 네트워크에서 각 장치를 대신 하 여 가상 장치를 관리 합니다.
* 장치 스키마를 내부 장치 개체 변환
* 네트워크 리소스, 예: 액세스 키를 자격 증명 관리

### <a name="network-access-stack"></a>네트워크 액세스 스택
* 예를 들어 Z-wave 스택 AllJoyn 비 네트워크 관련에 대 한 액세스

## <a name="adapter-classes"></a>어댑터 클래스

아래 다이어그램 AllJoyn에 해결 해야 하는 네이티브 장치 추상화를 만들려면 Microsoft DSB 템플릿에서 개발자가 사용 하 여 클래스를 보여 줍니다. 브리지는 Adapter.devices 목록의 각 장치에 대 한 버스 첨부 파일을 만들려면 어댑터 클래스의 인스턴스를 사용 합니다.
![AJ_Docu_DSB_Class_Diagram](../media/AllJoyn/AJ_Docu_DSB_Class_Diagram.png)

## <a name="special-handlers"></a>특수 처리기

AllJoyn 몇 가지 기본 서비스 및 LSF, HAE 또는 Control Panel과 같은 표준 인터페이스 프레임 워크를 지정합니다. DSB 특수 처리기를 사용 하 여 해당 노출 수 있습니다. 현재 릴리스의 DSB 템플릿 LSF 및 제어판 인터페이스의 구현을 포함합니다. 개발자는 해당 코드 브리지에 LSF 및 제어판 인터페이스에 대 한 콜백 함수에 연결 됩니다.

![AJ_Docu_DSB_Special_Handlers](../media/AllJoyn/AJ_Docu_DSB_Special_Handlers.png)

## <a name="dsb-resources"></a>DSB 리소스

### <a name="visual-studio-dsb-template"></a>Visual Studio DSB 템플릿

Visual Studio DSB 서식 파일에는 쉽게 새 DSB 프로젝트를 만들 수 있는 Visual studio 확장입니다. 프로젝트에 브리지 헤드 또는 헤드리스 장치로 DSB 빌드하려면 어댑터 및 모든 솔루션 파일에 대 한 셸 프로젝트와 같은 필요한 모든 구성 요소가 만들어집니다. 이 Visual Studio 확장에는 네이티브 및 관리 되는 AllJoyn 장치 시스템 브리지 템플릿을 포함합니다.

이러한 위치에서 DSB 템플릿을 다운로드 합니다.

* [Visual Studio 2015 용 DSB 템플릿](https://visualstudiogallery.msdn.microsoft.com/aea0b437-ef07-42e3-bd88-8c7f906d5da8)
* [Visual Studio 2017에 대 한 템플릿을 DSB](https://marketplace.visualstudio.com/vsgallery/c5f52768-8df7-42ff-b84e-d66d3d22fb50)
_DSB 템플릿을 통해도 설치할 수 있습니다 Visual Studio Tools-> 확장 및 업데이트... 온라인-> "검색" 필드 형식 "DSB"-> 합니다._

합니다 [AllJoyn DSB 개체 매핑](AlljoynDsbApiGuide.md) 문서 키 인터페이스 및 Alljoyn 시스템 브리지를 빌드하는 데 사용 하는 방법에 설명 합니다.

### <a name="sample-dsbs"></a>샘플 DSBs

* [AllJoyn DSB 모의 어댑터 자습서 및 샘플](https://developer.microsoft.com/en-us/windows/iot/samples/alljoynmockadapter)
  * 이 자습서에서는 모의 BACnet 장치를 IoT Core 장치에 연결할 장치 시스템 브리지 앱을 사용 하는 방법을 보여줍니다.
* [AllJoyn DSB Z-wave 어댑터 자습서 및 샘플](https://developer.microsoft.com/en-us/windows/iot/samples/zwaveadapter)
  * 이 자습서에는 장치 시스템 브리지 앱을 사용 하 여 IoT Core 장치 Z-wave 장치를 연결 하는 방법을 보여 줍니다.
* [AllJoyn DSB GPIO 어댑터 자습서C++](https://developer.microsoft.com/en-us/windows/iot/samples/alljoyndsb)
  * 이 자습서에는 예제를 만들려면 AllJoyn 장치 시스템 브리지 템플릿을 사용 하는 방법을 보여 줍니다. C++ GPIO 장치를 실행 하는 앱입니다.
* [AllJoyn DSB GPIO 어댑터 자습서C#](https://developer.microsoft.com/en-us/windows/iot/samples/alljoyndsbcs)
  * 이 자습서에는 AllJoyn 장치 시스템 브리지 템플릿을 사용 하 여 장치 GPIO를 실행 하는 샘플 관리 되는 앱을 만드는 방법을 보여 줍니다.
* [AllJoyn DSB ZigBee 어댑터 자습서 및 샘플](https://developer.microsoft.com/en-us/windows/iot/samples/ZigBeeAdapter)
  * 이 자습서에는 장치 시스템 브리지 앱을 사용 하 여 IoT Core 장치 ZigBee 장치를 연결 하는 방법을 보여 줍니다.
* [AllJoyn DSB BACnet 어댑터 자습서 및 샘플](https://developer.microsoft.com/en-us/windows/iot/samples/BACnetAdapter)
  * 이 자습서에는 장치 시스템 브리지 앱을 사용 하 여 IoT Core 장치 BACnet 장치를 연결 하는 방법을 보여 줍니다.
* [AllJoyn.JS 자습서](https://developer.microsoft.com/en-us/windows/iot/samples/AllJoynJS)
  * 이 자습서에는 Windows 10 응용 프로그램으로 Allseen Alliance 개발한 AllJoyn.JS 응용 프로그램을 실행 하는 방법을 보여 줍니다. AllJoyn.JS를 사용 하면 만들기, 모니터링 및 AllJoyn 장치를 제어 하는 JavaScript를 작성할 수 있습니다.
* [AllJoyn DSB OIC 어댑터 자습서 및 샘플](https://developer.microsoft.com/en-us/windows/iot/samples/OICAdapter)
  * 이 자습서에는 장치 시스템 브리지 앱을 사용 하 여 IoT Core 장치 IoTivity/OIC 장치를 연결 하는 방법을 보여 줍니다.
