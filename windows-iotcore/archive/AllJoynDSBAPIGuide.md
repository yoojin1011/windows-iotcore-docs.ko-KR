---
title: API 가이드-Alljoyn 장치 시스템 연결
author: saraclay
ms.author: saclayt
ms.date: 09/06/17
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: AllJoyn AllJoyn 버스에 매핑되는 하나 이상의 장치를 시스템에 대 한 컨트롤러를 나타내는 IAdapter를 사용 하려면 브리지 인터페이스 개체를 매핑하는 방법에 알아봅니다.
keywords: windows iot, AllJoyn
ms.openlocfilehash: 7c928ee0359ba705a4255d309339c48aa8d000a4
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59515075"
---
> [!NOTE]
> 보관 된 설명서가 표시 됩니다. Windows 10 IoT에서 더 이상 AllJoyn 사용할 수 없습니다. 질문에 대 한 GitHub에서 문제를 제기 하거나 아래 설명에 의견을 남길 하세요.

# <a name="mapping-bridge-interface-objects-to-alljoyn"></a>AllJoyn 매핑 브리지 인터페이스 개체

### <a name="i-iadapter"></a>9. IAdapter

브리지의 관점을 IAdapter AllJoyn 버스에 매핑되는 하나 이상의 장치를 시스템에 대 한 컨트롤러를 나타냅니다.  IAdapter 지원 장치를 열거, 일반 구성 및 수명 주기 관리 하는 데 필요한 인터페이스를 선언합니다.  또한 장치 또는 장치 속성, 메서드 및 신호를 사용 하 여 상호 작용 하는 메서드를 선언 합니다. 

AllJoyn 서비스로 장치를 노출 하려면 IAdapter에서 상속 되는 구체적인 클래스를 구현 하는 데 필요한 됩니다.  각 인터페이스 구현 되는 방식을 AllJoyn에 맞게 조정 하는 장치의 성격에 따라 달라 집니다. 

어댑터는 AllJoyn AllJoyn 버스에 나타납니다. 다음 이름의 service 보급 합니다. 

```
<ExposedAdapterPrefix>.DeviceSystemBridge.<AdapterName> 
```

각 어댑터는 두 개의 노출 `com.microsoft.alljoynmanagement.config` 해당 지원 브리지 및 어댑터 구성 인터페이스: 

```
/AdapterConfig 

/BusConfig
```
IAdapter 인터페이스를 구현 해야 하는 특정 속성을 선언 합니다.  다음 표에서 이러한 속성 및 AllJoyn 매핑되는 방법을 설명 합니다.

>  IAdapter 속성 | 설명 | 연결 매핑 |
> | :---------------- | :---------- | :------------- |
> | AdapterName       | 이 어댑터의 모델입니다.  또한 접미사가이 어댑터의 보급 알림된 이름에 사용 됩니다. (ExposedAdapterPrefix 참조). | 데이터 모델 수에 대 한 AllJoyn |
> | ExposedAdapterPrefix |이 브리지의 보급 알림된 이름 AllJoyn 버스 만들 때 사용 하는 접두사입니다.  어댑터 이름이 노출 됩니다. {ExposedAdapterPrefix}. DeviceSystemBridge 합니다. {AdapterName}입니다. | AllJoyn Bus 첨부 파일의 이름을 보급 |
> | ExposedApplciationGUID | 이 어댑터를 고유 하 게 식별 하는 어댑터에서 제공 되는 GUID입니다.  에 적용 됩니다이 GUID는이 어댑터에 의해 관리 되는 모든 장치에 대 한 데이터에 대 한 합니다.|AllJoyn에 대 한 데이터 응용 프로그램 ID이이 어댑터에 의해 노출 되는 모든 장치와이 어댑터에 대 한 합니다. |
> | ExposedApplicationName | 이 어댑터에 의해 노출 되는 친숙 한 응용 프로그램 이름입니다.  이 이름은이 어댑터에 의해 관리 되는 모든 장치에도 적용 됩니다. | AllJoyn에 대 한 데이터 응용 프로그램 이름을이 어댑터에 의해 노출 되는 모든 장치와이 어댑터에 대 한 합니다. |
> | 공급업체 | 이 어댑터의 공급 업체 이름 | 데이터 제조업체에 대 한 AllJoyn |
> | 버전 | 이 어댑터의 소프트웨어 버전 | 데이터 SW 버전에 대 한 AllJoyn |

#### <a name="iadapterinitialize"></a>IAdapter::Initialize

어댑터를 초기화합니다. 사용할 수 있습니다 진행 해야 합니다.  예를 들어, 장치 검색을 시작 하려면 백그라운드 스레드를 시작할 수 없습니다.  일반적으로 장치 도착 및 장치 제거 신호를 만들려면이 사용 하는 것은 수도 있습니다. 

#### <a name="iadaptergetsetconfig"></a>IAdapter::Get/SetConfig

어댑터의 구성 데이터에 액세스 하기 위한 메서드이 쌍이 사용 됩니다.  일반적으로 이러한 설정을 장치 열거에 대 한 어댑터에 필요한 통신 설정 구성 되지만 해당 용도에 제한 되지 않습니다.  

브리지는 "com.microsoft.alljoynmanagement.config" 인터페이스를 통해 AllJoyn에 어댑터 구성 데이터를 노출합니다.  브리지의 관점에서 어댑터 구성 데이터 설정을 완전히 임의적 이며 간단한 바이트 배열로 어댑터를 사용 하 여 교환 됩니다.  내부적으로를 어댑터에 필요에 따라 이러한 설정을 저장할 수 있습니다.   

#### <a name="iadapterenumdevices"></a>IAdapter::EnumDevices

이 메서드는에 bus에 사용할 수 있는 장치에 대 한 정보를 사용 하 여 브리지를 제공합니다.  브리지에 반환 하는 장치 목록에는 개별 AllJoyn 서비스로 AllJoyn 버스에 추가 됩니다. 

이 메서드를 통해 목록을 반환 되어야 합니다 열거형을 IAdapterIoRequest 완료 되지 않은 경우 여기 반환 수도 있습니다.  브리지는 어댑터 장치 열거를 완료 하려면 IAdapterIoRequest 알릴 때까지이 대기 됩니다.   
### <a name="ii-iadapterdevice"></a>II. IAdapterDevice

브리지의 관점에서 장치를 어댑터 구현 자가 원하는 AllJoyn 서비스로 AllJoyn 버스에 노출 된 장치를 나타냅니다.  속성, 메서드 및 장치는 버스에 노출 하는 신호 이란 사용자의 몫을 구현자로 않지만 일반적으로이 속성, 메서드 및 장치 또는 장치 기본적으로 해당 네이티브 통신 네트워크를 통해 노출 하는 신호 직접 매핑 . 

각 IAdapterDevice 다음 이름의 alljoyn 게 보급 됩니다. 

    {ExposedAdapterPrefix}.{AdapterName}.{Name} 

각 장치에는 모든 속성, 메서드 및 장치에서 캡슐화 하는 신호를 노출 하기 위한 단일 alljoyn 인터페이스를 노출 합니다.  Alljoyn 인터페이스 이름은 다음과 같습니다. 

    {ExposedAdapterPrefix}.{AdapterName}.{Name}.MainInterface 

IAdapter와 마찬가지로 각 IAdapterDevice 브리지 AllJoyn 하기 위해 장치를 노출 하는 데 사용 하는 속성을 구현 하려면 필요 합니다.  다음 표에 각 속성 및 방법을 브리지에 매핑하기 AllJoyn 있습니다. 

> | IAdapterDevice 속성 | 설명 | 연결 매핑 |
> | :---------------------- | :---------- | :------------- |
> | ControlPanelHandler     | 이 장치를 작동할 수 있는 제어판입니다. | org.alljoyn.ControlPanel.ControlPanel /ControlPanel bus 개체에서 노출 |
> | 설명             | 이 장치의 설명입니다. | 데이터 설명에 대 한 AllJoyn |
> | FirmwareVersion         | 이 장치의 소프트웨어 버전 | 데이터 펌웨어 버전에 대 한 AllJoyn |
> | 아이콘                    | 이 장치 alljoyn를 노출 하는 그래픽 아이콘입니다. 아이콘이 없을 경우 null 일 수 있습니다. |     아이콘에 대 한 표준 AllJoyn으로 노출합니다. |
> | 메서드                 | 이 장치의 AllJoyn를 노출 하는 모든 메서드 집합인 합니다. | 이 메서드가 없는 경우에 비워 둘 수 있습니다. 각 메서드 이름의 MainInterface에서 메서드로 노출 합니다. 고유 하지 않은 이름이 고유 ID를 사용 하 여 추가 됩니다. |
> | Model                   | 이 장치 모델 | AllJoyn Bus 데이터 모델 번호 |
> | 이름                      | 이 장치의 데이터 장치 이름에 대 한 AllJoyn 이름입니다. | 이 장치의 보급 알림된 이름에 대 한 접미사도 사용 됩니다. {ExposedAdapterPrefix}. {AdapterName}입니다. {Name} |
> | 속성              | 장치의 AllJoyn를 노출 하는 모든 속성의 집합입니다. 이 비워 둘 수 없는 속성을 비어 있는 경우이 하나 이상 신호 경우, 값 변경의 신호도 지원 해야 합니다. | IProperty를 참조 하세요. |
> | SerialNumber            | 이 장치의 일련 번호 | 데이터 일련 번호에 대 한 AllJoyn |
> | 신호                 | 이 장치 AllJoyn를 노출 하는 모든 신호의 집합입니다. | AllJoyn 신호도 노출 |
> | 공급업체                  | 이 장치의 공급 업체 이름 | 데이터 제조업체에 대 한 AllJoyn |
> | 버전                 | 이 장치의 소프트웨어 버전 | 데이터 SW 버전에 대 한 AllJoyn |


### <a name="iii-iadapterproperty"></a>III. IAdapterProperty

브리지의 관점을 IAdapterProperty, 어댑터 구현 자가 노출 하려는 AllJoyn 버스 특정 장치에는 관련된 데이터 값의 컬렉션을 나타냅니다.  각 속성에는 하나 이상의 IAdapterValues 집합을 포함합니다.  각 IAdapterValue AllJoyn 클라이언트에서 액세스할 수 있는 데이터의 개별 단위를 나타냅니다.     

각 IAdapterProperty 발표 Alljoyn에 인터페이스 이름 사용 하 여 버스 개체로 다음과 같습니다. 

    /{PropertyName} 

    {ExposedAdapterPrefix}.{AdapterName}.{PropertyName} 

또는 인터페이스 이름은 특정 인터페이스 형식에 매핑할 속성에서 재정의할 수 있습니다.  이런 경우 IAdapterProperty 이름을 발표 인터페이스 이름 사용 하 여 버스 개체로 다음과 같습니다. 

    /{PropertyName} 

    {InterfaceHint} 

> | IAdapterProperty 속성 |   설명                        | 연결 매핑 |
> | :-------------------------- | :--------------------------------- | :-------------------------------------------- |
> | 특성                |IAdapterAttributes 컬렉션    | AllJoyn 속성 집합 (IAdapterValue 참조) |
> | InterfaceHint | 몇 가지 잘 알려진 인터페이스 형식으로이 속성에 매핑할 수 있는이 속성을 재정의 합니다.  기본 동작을 사용 하려면 null을 반환합니다 | 지정 하는 경우이 속성에 대 한 AllJoyn 인터페이스 이름 |
> | 이름 | 속성의 이름 | AllJoyn 속성 |

### <a name="v-iadaptervalue"></a>V. IAdapterValue

각 IAdapterValue bus 개체 및 인터페이스 이름이 AllJoyn 속성의 자식으로 노출 됩니다.

    /{PropertyName}/{ValueName}
    
    {ExposedAdapterPrefix}.{AdapterName}.{PropertyName}.{ValueName}

> | IAdapterValue 속성    | 설명                        | 연결 매핑                                |
> | :-------------------------- | :--------------------------------- | :-------------------------------------------- |
> | data                          | 브리지 된 장치의 속성의 실제 데이터 값입니다.| AllJoyn 속성|
> | 이름                        | 값의 이름                      | AllJoyn 속성의 이름|

### <a name="iv-iadaptersignal"></a>IV. IAdapterSignal

브리지의 관점을 ISignal 장치에 변경 된 경우 발생 시킬 수 있는 이벤트를 나타냅니다.  모든 장치는 일반적으로 변경의 값이 신호를 가집니다.  이 신호 경고 AllJoyn 클라이언트 장치에서 하나 이상의 속성이 변경 되었습니다. 또한 추가 신호를 지원할 수 있습니다.

각 ISignal 이름 신호를 사용 하 여 장치에 대 한 호스트 세션 신호로 AllJoyn에 발표 됩니다.  
ISignal에 대 한 다음 속성을 구현 해야 합니다.

> | ISignal 속성          | 설명                        | 연결 매핑                                |
> | :-------------------------- | :--------------------------------- | :-------------------------------------------- |
> | 이름                          |신호 이름                      | AllJoyn 신호 |
> | 매개 변수 | 집합 변경 된 개체 및 해당 새 값 또는 순수 신호 경우 null입니다. | Alljoyn 신호 인수 배열에 신호를 전달 합니다. |
