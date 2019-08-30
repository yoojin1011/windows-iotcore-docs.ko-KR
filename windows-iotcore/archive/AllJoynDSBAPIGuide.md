---
title: Alljoyn 장치 시스템 브리지-API 가이드
author: saraclay
ms.author: saclayt
ms.date: 09/06/17
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: IAdapter를 사용 하 여 브리지 인터페이스 개체를 AllJoyn에 매핑하는 방법에 대해 알아봅니다 .이를 사용 하 여 AllJoyn 버스에 매핑되는 하나 이상의 장치의 시스템에 대 한 컨트롤러를 나타냅니다.
keywords: windows iot, AllJoyn
ms.openlocfilehash: 7c928ee0359ba705a4255d309339c48aa8d000a4
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "60169011"
---
> [!NOTE]
> 보관 된 설명서를 보고 있습니다. AllJoyn는 Windows 10 IoT에서 더 이상 지원 되지 않습니다. 질문이 있는 경우 GitHub에서 문제를 열거나 아래 설명에 의견을 남겨 주세요.

# <a name="mapping-bridge-interface-objects-to-alljoyn"></a>AllJoyn에 브리지 인터페이스 개체 매핑

### <a name="i-iadapter"></a>9\. IAdapter

브리지의 관점에서 IAdapter은 AllJoyn 버스에 매핑되는 하나 이상의 장치 시스템의 컨트롤러를 나타냅니다.  IAdapter는 장치 열거, 일반 구성 및 수명 주기 관리를 지 원하는 데 필요한 인터페이스를 선언 합니다.  또한 장치 또는 장치 속성, 메서드 및 신호와 상호 작용 하는 메서드를 선언 합니다. 

장치를 AllJoyn 서비스로 노출 하려면 IAdapter에서 상속 되는 구체적인 클래스를 구현 해야 합니다.  각 인터페이스를 구현 하는 방법은 AllJoyn에 적용 하는 장치의 특성에 따라 다릅니다. 

어댑터는 다음 이름으로 알린 AllJoyn 서비스로 AllJoyn 버스에 표시 됩니다. 

```
<ExposedAdapterPrefix>.DeviceSystemBridge.<AdapterName> 
```

각 어댑터는 브리지 `com.microsoft.alljoynmanagement.config` 및 어댑터 구성을 지 원하는 두 개의 인터페이스를 노출 합니다. 

```
/AdapterConfig 

/BusConfig
```
IAdapter 인터페이스는 구현 해야 하는 특정 속성을 선언 합니다.  다음 표에서는 이러한 속성과 이러한 속성을 AllJoyn에 매핑하는 방법에 대해 설명 합니다.

>  IAdapter 속성 | 설명 | 브리지 매핑 |
> | :---------------- | :---------- | :------------- |
> | AdapterName       | 이 어댑터의 모델입니다.  또한이 어댑터의 보급 이름에 사용 되는 접미사입니다. ExposedAdapterPrefix를 참조 하세요. | 데이터 모델 번호에 대 한 AllJoyn |
> | ExposedAdapterPrefix |AllJoyn 버스에서이 브리지의 보급 된 이름을 만들 때 사용 되는 접두사입니다.  어댑터는 {ExposedAdapterPrefix} 이름으로 노출 됩니다. DeviceSystemBridge. {AdapterName}. | AllJoyn 버스 첨부 파일의 보급 이름 |
> | ExposedApplciationGUID | 어댑터에서 제공 하며,이 어댑터를 고유 하 게 식별 하는 GUID입니다.  이 GUID는이 어댑터에서 관리 하는 모든 장치에 대 한 데이터 정보에도 적용 됩니다.|이 어댑터에 대 한 데이터 응용 프로그램 ID와이 어댑터에서 노출 하는 모든 장치에 대 한 AllJoyn 정보입니다. |
> | ExposedApplicationName | 이 어댑터에 의해 노출 되는 친숙 한 응용 프로그램 이름입니다.  이 이름은이 어댑터에서 관리 하는 모든 장치에도 적용 됩니다. | 이 어댑터에 대 한 데이터 응용 프로그램 이름 및이 어댑터에서 노출 하는 모든 장치에 대 한 AllJoyn입니다. |
> | Vendor | 이 어댑터의 공급 업체 이름 | 데이터 제조업체에 대 한 AllJoyn |
> | 버전 | 이 어댑터의 소프트웨어 버전 | 데이터 SW 버전에 대 한 AllJoyn |

#### <a name="iadapterinitialize"></a>IAdapter:: Initialize

어댑터를 초기화 합니다. 이는 필요한 경우에 사용할 수 있습니다.  예를 들어 장치 검색을 시작 하기 위해 백그라운드 스레드를 시작할 수 있습니다.  일반적으로 장치 도착 및 장치 제거 신호를 만드는 데에도 사용 됩니다. 

#### <a name="iadaptergetsetconfig"></a>IAdapter:: Get/SetConfig

이 메서드 쌍은 어댑터의 구성 데이터에 액세스 하는 데 사용 됩니다.  일반적으로 이러한 설정은 어댑터에서 장치 열거를 위해 필요로 하는 통신 설정으로 구성 되어 있지만 해당 목적으로 제한 되지 않습니다.  

브리지는 "alljoynmanagement" 인터페이스를 통해 AllJoyn에 어댑터 구성 데이터를 노출 합니다.  브리지의 관점에서 어댑터 구성 데이터 설정은 완전히 임의로 사용 되며 어댑터와 단순 바이트 배열로 교환 됩니다.  어댑터에 내부적으로 이러한 설정을 원하는 대로 저장할 수 있습니다.   

#### <a name="iadapterenumdevices"></a>IAdapter:: EnumDevices

이 메서드는 버스에서 사용할 수 있는 장치에 대 한 정보를 제공 합니다.  브리지로 반환 된 장치 목록이 개별 AllJoyn 서비스로 AllJoyn 버스에 추가 됩니다. 

이 메서드를 통해 목록을 반환 해야 하지만 열거형이 완료 되지 않은 경우 여기에서 IAdapterIoRequest를 반환할 수도 있습니다.  이 브리지는 어댑터가 장치 열거를 완료 하기 위해 IAdapterIoRequest 신호를 받을 때까지 대기 합니다.   
### <a name="ii-iadapterdevice"></a>부. IAdapterDevice

브리지의 관점에서 장치는 어댑터 구현자가 alljoyn 버스에 AllJoyn 서비스로 노출 하려는 장치를 나타냅니다.  장치가 버스에 노출 하는 속성, 메서드 및 신호는 구현자의 역할을 하는 것 이지만 일반적으로 장치 또는 장치가 네이티브 통신 네트워크를 통해 기본적으로 노출 하는 속성, 메서드 및 신호에 직접 매핑됩니다. . 

각 IAdapterDevice는 다음 이름을 사용 하 여 alljoyn에 보급 됩니다. 

    {ExposedAdapterPrefix}.{AdapterName}.{Name} 

각 장치는 장치에서 캡슐화 하는 모든 속성, 메서드 및 신호를 노출 하기 위한 단일 alljoyn 인터페이스를 노출 합니다.  Alljoyn 인터페이스 이름은 다음과 같습니다. 

    {ExposedAdapterPrefix}.{AdapterName}.{Name}.MainInterface 

IAdapter와 마찬가지로 각 IAdapterDevice는 브리지가 장치를 AllJoyn에 노출 하는 데 사용 하는 속성을 구현 하는 데 필요 합니다.  다음 표에서는 각 속성에 대해 설명 하 고, 브리지가이를 AllJoyn에 매핑하는 방법을 설명 합니다. 

> | IAdapterDevice 속성 | 설명 | 브리지 매핑 |
> | :---------------------- | :---------- | :------------- |
> | ControlPanelHandler     | 이 장치를 작동할 수 있는 제어판입니다. | /Werererererererererererererererererererererererv 개체 아래에 |
> | 설명             | 이 장치에 대 한 설명입니다. | 데이터에 대 한 AllJoyn 정보 설명 |
> | FirmwareVersion         | 이 장치의 소프트웨어 버전 | 데이터 펌웨어 버전에 대 한 AllJoyn |
> | 아이콘                    | 이 장치가 alljoyn에 노출 하는 그래픽 아이콘입니다. 이는 아이콘이 없는 경우 null 일 수 있습니다. |     표준 AllJoyn 정보 아이콘으로 노출 됨 |
> | 메서드                 | 장치가 AllJoyn에 노출 하는 모든 메서드를 설정 합니다. | 메서드가 없으면 비어 있을 수 있습니다. 각 메서드의 이름을 사용 하 여 MainInterface 아래에 메서드로 노출 됩니다. 고유 하지 않은 이름에는 고유 ID가 추가 됩니다. |
> | Model                   | 이 장치의 모델 | AllJoyn 버스 데이터 모델 번호 |
> | 이름                      | 데이터 장치 이름에 대 한이 장치 AllJoyn의 이름입니다. | 이는이 장치의 보급 이름 {ExposedAdapterPrefix}에 대 한 접미사에도 사용 됩니다. {AdapterName}. 이름의 |
> | 속성              | 장치가 AllJoyn에 노출 하는 모든 속성의 집합입니다. 속성이 없는 경우이 값은 비어 있을 수 있지만 비어 있지 않은 경우 하나 이상의 신호는 값 신호의 변경도 지원 되어야 합니다. | IProperty를 참조 하세요. |
> | SerialNumber            | 이 장치의 일련 번호 | 데이터 일련 번호에 대 한 AllJoyn |
> | 연산                 | 이 장치가 AllJoyn에 노출 하는 모든 신호의 집합입니다. | AllJoyn 신호로 노출 됨 |
> | Vendor                  | 이 장치의 공급 업체 이름 | 데이터 제조업체에 대 한 AllJoyn |
> | 버전                 | 이 장치의 소프트웨어 버전 | 데이터 SW 버전에 대 한 AllJoyn |


### <a name="iii-iadapterproperty"></a>등에. IAdapterProperty

브리지의 관점에서 IAdapterProperty는 어댑터 구현자가 특정 장치에 대해 AllJoyn 버스에 노출 하려는 관련 데이터 값의 컬렉션을 나타냅니다.  각 속성에는 하나 이상의 IAdapterValues 집합이 포함 되어 있습니다.  각 IAdapterValue는 AllJoyn 클라이언트에서 액세스할 수 있는 개별 데이터 단위를 나타냅니다.     

각 IAdapterProperty은 다음과 같이 인터페이스 이름을 사용 하는 버스 개체로 Alljoyn에 알려집니다. 

    /{PropertyName} 

    {ExposedAdapterPrefix}.{AdapterName}.{PropertyName} 

또는 속성에 의해 인터페이스 이름을 재정의 하 여 특정 인터페이스 형식에 매핑할 수도 있습니다.  이 경우 IAdapterProperty 이름은 다음과 같이 인터페이스 이름을 사용 하는 버스 개체로 알려집니다. 

    /{PropertyName} 

    {InterfaceHint} 

> | IAdapterProperty 속성 |   설명                        | 브리지 매핑 |
> | :-------------------------- | :--------------------------------- | :-------------------------------------------- |
> | 특성                |IAdapterAttributes의 컬렉션입니다.    | AllJoyn 속성 집합 (IAdapterValue 참조) |
> | 인터페이스 힌트 | 이 속성에 대해 잘 알려진 다른 인터페이스 형식에이 속성을 매핑하는 데 사용할 수 있는 재정의입니다.  기본 동작을 사용 하려면 null을 반환 합니다. | 이 속성의 AllJoyn 인터페이스 이름입니다 (지정 된 경우). |
> | 이름 | 속성의 이름입니다. | AllJoyn 속성 |

### <a name="v-iadaptervalue"></a>HYPER-V. IAdapterValue

각 IAdapterValue는 다음 버스 개체 및 인터페이스 이름을 사용 하 여 AllJoyn 속성의 자식으로 노출 됩니다.

    /{PropertyName}/{ValueName}
    
    {ExposedAdapterPrefix}.{AdapterName}.{PropertyName}.{ValueName}

> | IAdapterValue 속성    | 설명                        | 브리지 매핑                                |
> | :-------------------------- | :--------------------------------- | :-------------------------------------------- |
> | data                          | 브리지 된 장치에 있는 속성의 실제 데이터 값입니다.| AllJoyn 속성|
> | 이름                        | 값 이름                      | AllJoyn 속성의 이름입니다.|

### <a name="iv-iadaptersignal"></a>IV. IAdapterSignal

브리지의 관점에서 볼 때 ISignal은 장치가 변경 될 때 발생 하는 이벤트를 나타냅니다.  모든 장치는 일반적으로 값 신호를 변경 합니다.  이 신호는 장치에서 하나 이상의 속성이 변경 되었음을 AllJoyn 클라이언트에 알립니다. 추가 신호가 지원 될 수도 있습니다.

각 ISignal은 장치에 대 한 신호 이름으로 호스 티 드 세션 신호로 AllJoyn에 알려집니다.  
ISignal에 대해 다음 속성을 구현 해야 합니다.

> | ISignal 속성          | 설명                        | 브리지 매핑                                |
> | :-------------------------- | :--------------------------------- | :-------------------------------------------- |
> | 이름                          |신호 이름                      | AllJoyn 신호 |
> | Params | 변경 된 개체 집합 및 새 값 또는이가 순수한 신호의 경우 null입니다. | 신호에 전달 된 alljoyn 신호 인수의 배열에 매핑합니다. |
