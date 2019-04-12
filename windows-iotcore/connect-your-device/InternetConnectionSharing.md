---
title: 인터넷 연결 공유
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Windows IoT Core에서 인터넷 연결 공유를 구성 하는 방법에 알아봅니다.
keywords: windows iot, Internet Connection Sharing, ICS와 장치 포털
ms.openlocfilehash: dcf51d98bc618c1a843c43b2d33fc8f832ef73d4
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512973"
---
# <a name="internet-connection-sharing"></a>인터넷 연결 공유

이 문서에서는 Windows IoT Core에서 인터넷 연결 공유를 사용할 수 있습니다 하는 방법을 설명 합니다. 개발자는 ICS를 프로그래밍 방식으로 구성 하려면 NetworkTetheringManager API를 사용할 수 있습니다. API에 설명 되어는 [NetworkOperatorTetheringManager](https://msdn.microsoft.com/library/windows/apps/windows.networking.networkoperators.networkoperatortetheringmanager.aspx) 클래스입니다.
중 하나를 사용 하는 경우는 [Windows 10 IoT Core 릴리스 이미지](https://developer.microsoft.com/en-us/windows/iot/downloads) 장치 포털을 사용 하 여 ICS 구성할 수도 있습니다.

> [!IMPORTANT]
> WiFi 프로필을 먼저 만들어야 하 고 다음 매니페스트에 추가 해야 합니다.
`<DeviceCapability Name="wiFiControl" />`

공유 자습서를 참조 하십시오 합니다 [Windows IoT Core 2015 년 11 월 릴리스](InternetConnectionSharingNov2015.md) 문서.

## <a name="configuring-ics-using-the-device-portal"></a>ICS 장치 포털을 사용 하 여 구성
설명서를 참조 하세요 [Windows Device Portal](../manage-your-device/deviceportal.md) (WDP).

## <a name="ics-code-sample"></a>ICS 코드 샘플
다음 코드 예제를 보여 줍니다 하는 방법을 [NetworkOperatorTetheringManager](https://msdn.microsoft.com/library/windows/apps/windows.networking.networkoperators.networkoperatortetheringmanager.aspx) Wi-fi 상에 서 이더넷 연결을 공유 하려면 API를 사용 합니다. CreateFromConnectionProfile 메서드는 public 및 private 인터페이스를 지정 하는 인수를 허용 합니다. 잘못 된 구성의 모든 경우에 Wi-fi 라디오 꺼져 있거나 이더넷 연결을 제한적으로 같은 인터넷 공유를 시작 하려고 전달이 시나리오와 관련 된 적절 한 오류 코드입니다.

```
using Windows.Networking.NetworkOperators;
using Windows.Networking.Connectivity; 
 
// Find the Ethernet profile (IANA Type 6)
var connectionProfiles = NetworkInformation.GetConnectionProfiles(); 
var ethernetConnectionProfile = connectionProfiles.FirstOrDefault(x => x.NetworkAdapter.IanaInterfaceType == 6); 

// Find an 802.11 wireless network interface (IANA Type 71)
var wirelessConnectionProfile = connectionProfiles.FirstOrDefault(x => x.NetworkAdapter.IanaInterfaceType == 71);
var targetNetworkAdapter = wirelessConnectionProfile.NetworkAdapter;

if (ethernetConnectionProfile != null && targetNetworkAdapter != null)
{
    var tetheringManager = NetworkOperatorTetheringManager.CreateFromConnectionProfile(ethernetConnectionProfile, targetNetworkAdapter); 

    var result = await tetheringManager.StartTetheringAsync(); 
    if (result.Status == TetheringOperationStatus.Success)
    {
        UpdateUI();
    }
    else
    {
        ProcessTetheringError(result);
    }
}
```
