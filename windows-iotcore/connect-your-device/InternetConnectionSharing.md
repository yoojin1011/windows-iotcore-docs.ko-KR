---
title: 인터넷 연결 공유
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Windows IoT Core에서 인터넷 연결 공유를 사용 하도록 설정 하 고 구성 하는 방법을 알아봅니다.
keywords: windows iot, 인터넷 연결 공유, ICS, 장치 포털
ms.openlocfilehash: dcf51d98bc618c1a843c43b2d33fc8f832ef73d4
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "60169021"
---
# <a name="internet-connection-sharing"></a><span data-ttu-id="df5e6-104">인터넷 연결 공유</span><span class="sxs-lookup"><span data-stu-id="df5e6-104">Internet connection sharing</span></span>

<span data-ttu-id="df5e6-105">이 문서에서는 Windows IoT Core에서 ICS (인터넷 연결 공유)를 사용 하도록 설정 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="df5e6-105">This document describes how internet connection sharing (ICS) can be enabled on Windows IoT Core.</span></span> <span data-ttu-id="df5e6-106">개발자는 NetworkTetheringManager API를 사용 하 여 ICS를 프로그래밍 방식으로 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df5e6-106">Developers can use the NetworkTetheringManager API to configure ICS programmatically.</span></span> <span data-ttu-id="df5e6-107">API는 [NetworkOperatorTetheringManager](https://msdn.microsoft.com/library/windows/apps/windows.networking.networkoperators.networkoperatortetheringmanager.aspx) 클래스에 설명 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df5e6-107">The API is described in the [NetworkOperatorTetheringManager](https://msdn.microsoft.com/library/windows/apps/windows.networking.networkoperators.networkoperatortetheringmanager.aspx) class.</span></span>
<span data-ttu-id="df5e6-108">[Windows 10 IoT Core 릴리스 이미지](https://developer.microsoft.com/en-us/windows/iot/downloads) 중 하나를 사용 하는 경우 장치 포털을 사용 하 여 ICS를 구성할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df5e6-108">When using one of the [Windows 10 IoT Core Release Image](https://developer.microsoft.com/en-us/windows/iot/downloads) ICS can also be configured using the device portal.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="df5e6-109">먼저 WiFi 프로필을 만들고 다음을 매니페스트에 추가 해야 합니다.`<DeviceCapability Name="wiFiControl" />`</span><span class="sxs-lookup"><span data-stu-id="df5e6-109">A WiFi profile must be created first and the following will need to be added to the manifest: `<DeviceCapability Name="wiFiControl" />`</span></span>

<span data-ttu-id="df5e6-110">공유 자습서는 [Windows IoT Core 11 월 2015 릴리스](InternetConnectionSharingNov2015.md) 문서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="df5e6-110">For the Sharing Tutorial, please view the [Windows IoT Core November 2015 Release](InternetConnectionSharingNov2015.md) document.</span></span>

## <a name="configuring-ics-using-the-device-portal"></a><span data-ttu-id="df5e6-111">장치 포털을 사용 하 여 ICS 구성</span><span class="sxs-lookup"><span data-stu-id="df5e6-111">Configuring ICS using the device portal</span></span>
<span data-ttu-id="df5e6-112">[Windows Device Portal](../manage-your-device/deviceportal.md) 의 설명서 (WDP)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="df5e6-112">See documentation on [Windows Device Portal](../manage-your-device/deviceportal.md) (WDP).</span></span>

## <a name="ics-code-sample"></a><span data-ttu-id="df5e6-113">ICS 코드 샘플</span><span class="sxs-lookup"><span data-stu-id="df5e6-113">ICS code sample</span></span>
<span data-ttu-id="df5e6-114">아래 코드 샘플은 [NetworkOperatorTetheringManager](https://msdn.microsoft.com/library/windows/apps/windows.networking.networkoperators.networkoperatortetheringmanager.aspx) API를 사용 하 여 wi-fi를 통한 이더넷 연결 공유를 시작 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="df5e6-114">The code sample below demonstrates how the [NetworkOperatorTetheringManager](https://msdn.microsoft.com/library/windows/apps/windows.networking.networkoperators.networkoperatortetheringmanager.aspx) API is used to start sharing an Ethernet connection over Wi-Fi.</span></span> <span data-ttu-id="df5e6-115">CreateFromConnectionProfile 메서드는 public 및 private 인터페이스를 지정 하는 인수를 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="df5e6-115">The CreateFromConnectionProfile method accepts arguments that specifies the public and private interface.</span></span> <span data-ttu-id="df5e6-116">Wi-fi 라디오가 꺼져 있거나 이더넷 연결이 제한 된 경우와 같이 잘못 된 구성의 경우 인터넷 공유를 시작 하려는 시도는이 시나리오와 관련 된 적절 한 오류 코드를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="df5e6-116">In any cases of misconfiguration, such as the Wi-Fi radio is turned off, or Ethernet has limited connectivity, then the attempt to start internet sharing conveys an appropriate error code pertaining to this scenario.</span></span>

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
