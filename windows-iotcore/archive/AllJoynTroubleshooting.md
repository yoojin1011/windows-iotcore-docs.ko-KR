---
title: AllJoyn 문제 해결
author: saraclay
ms.author: saclayt
ms.date: 09/07/17
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: 알려진 문제 및 문제 해결 설정에 대해이 포괄적인 가이드를 사용 하 여 AllJoyn 기술 문제를 해결 하는 방법을 알아봅니다.
keywords: windows iot, AllJoyn
ms.openlocfilehash: 8b93242c8f583199ee5890c6d0d15985f9025175
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "60169971"
---
> [!NOTE]
> 보관 된 설명서를 보고 있습니다. AllJoyn는 Windows 10 IoT에서 더 이상 지원 되지 않습니다. 질문이 있는 경우 GitHub에서 문제를 열거나 아래 설명에 의견을 남겨 주세요.

# <a name="alljoyn-troubleshooting"></a>AllJoyn 문제 해결

[AllJoyn](https://allseenalliance.org/developers/learn) 는 IoT 장치와 응용 프로그램이 서로를 검색 하 고 상호 작용할 수 있도록 하는 기술입니다. AllJoyn는 Windows 10 및 Windows 10 SDK에 기본 제공 되므로 유니버설 Windows 플랫폼 (UWP)를 사용 하 여 AllJoyn을 쉽게 활용할 수 있습니다.

![AJ_Troubleshooting_intro](../media/AllJoyn/AJ_Troubleshooting_intro.jpg)

이 블로그 게시물은 AllJoyn 네트워크 및 장치를 구성 하는 데 도움이 되며, 예상 대로 작동 하지 않는 경우 따라야 하는 문제 해결 단계도 제공 합니다. 이 문서의 주요 초점은 UWP AllJoyn 클라이언트 앱 (AllJoyn 소비자) 및 AllJoyn 장치 (AllJoyn 생산자) 간의 통신을 사용 하도록 설정 하는 것입니다. UWP AllJoyn 생산자 앱과의 통신을 사용 하도록 설정 하는 데는 동일한 구성 단계가 많이 필요 하지만 이후 블로그 게시물 및 문서에 대 한 자세한 정보는 남아 있습니다.

### <a name="app-development-checklist"></a>앱 개발 검사 목록

Windows 10 용 UWP 앱을 작성 하는 경우 다음을 확인 해야 합니다.

1. 앱의 매니페스트에서 ' allJoyn ' 기능을 선언 했습니다 (참고 대/소문자 구분).
2. 대상으로 지정할 특정 아키텍처를 선택 했습니다. (일부 경우에는 ' Any CPU '를 사용 하 여 Windows 런타임 구성 요소를 빌드할 수 없습니다. 몇 가지 Visual Studio 2017 빌드의 알려진 문제).

Windows 10 용 UWP 기반 응용 프로그램이 아닌 앱 또는 장치 소프트웨어를 작성 하는 경우 Windows 10의 AllJoyn과의 호환성을 위해 다음 검사 목록을 검토 해야 합니다.

1. 생산자를 구현 하는 경우 정보 인터페이스 및 정보 기반 광고/검색이 사용 되 고 있는지 확인 합니다. About 인터페이스는 [AllSeen 된 동맹 웹 사이트에 설명](https://allseenalliance.org/developers/learn/core/about-announcement/interface)되어 있습니다.
2. 최상의 결과를 위해 AllSeen 동맹 웹 사이트의 [다운로드 섹션](https://allseenalliance.org/developers/download) 에서 사용할 수 있는 15.04 AllJoyn 코드 베이스를 사용 합니다.

### <a name="network-setup-and-troubleshooting"></a>네트워크 설정 및 문제 해결

AllJoyn 장치가 서로를 검색 하 고 상호 작용할 수 있도록 하려면 각 장치의 네트워크 구성 및 설정이 다음을 충족 해야 합니다.

1. 모든 AllJoyn 장치는 동일한 네트워크에 연결 되며 동일한 서브넷에 있습니다.
2. Windows 10 PC: "장치 및 콘텐츠 찾기"는 AllJoyn에서 사용 중인 네트워크에 대해 사용 하도록 설정 됩니다 (Phone에는 적용 되지 않음).

PC에서는 CMD 또는 PowerShell 창의 추적 경로 명령을 사용 하 여 다른 컴퓨터/장치가 다음과 같은 서브넷에 있는지 확인할 수 있습니다.

    PS C:\Users\user> tracert WIN10PC1
     
    Tracing route to WIN10PC1 [fe80::657d:d8bf:176f:d0b2%24]
     
    over a maximum of 30 hops:
     
    1       1 ms     1 ms     1 ms   WIN10PC1 [fe80::657d:d8bf:176f:d0b2]
     
    Trace complete.

여기에 표시 되는 첫 번째 숫자는 홉 수입니다 .이 값은 "1" 이므로 두 컴퓨터가 동일한 서브넷에 있음을 의미 합니다.

다음은 일반적인 AllJoyn 네트워크 설정의 예입니다. 이 예제에서 표시 되는 모든 장치는 동일한 서브넷에 있다고 가정 하 여 각 장치를 검색 하 고 서로 상호 작용할 수 있습니다.

![AJ_Troubleshooting_Devices](../media/AllJoyn/AJ_Troubleshooting_Devices.jpg)

Windows 10 PC를 AllJoyn 장치를 사용 하 여 네트워크에 연결 하는 경우 네트워크의 장치 및 Pc 찾기와 관련 된 대화 상자가 표시 되 면 "예"를 클릭 해야 합니다. 두고 이러한 대화 상자는 나타나지 않으므로 Windows 10 Phone에서 네트워크를 연결 하는 경우에는 적용 되지 않습니다.

다음과 같이 Wi-fi 설정의 "고급 설정" 페이지에서이 설정을 관리할 수도 있습니다 .이 페이지는 사용 중인 Windows 10 참가자 빌드에 따라 약간 다르게 보일 수 있습니다.

![AJ_Troubleshooting_Settings](../media/AllJoyn/AJ_Troubleshooting_Settings.jpg)

"장치 찾기 및 내용"에 대 한 토글은 AllJoyn 기능을 사용 하기 위해 "On" 위치에 있어야 합니다.

기존 네트워크 연결의 경우 "Get NetConnectionProfile" Powershell cmdlet을 실행 하 여이 옵션이 올바르게 구성 되었는지 쉽게 확인할 수 있습니다. 이는 Windows 10 Phone에는 적용 되지 않습니다.

예제 Get NetConnectionProfile 출력:

    PS C:\Users\user> Get-NetConnectionProfile
     
    Name             : myWirelessNetwork
    InterfaceAlias   : vEthernet (Intel(R) Dual Band Wireless-AC 7260 Virtual Switch)
    InterfaceIndex   : 24
    NetworkCategory : Private
    IPv4Connectivity : Internet
    IPv6Connectivity : LocalNetwork


"NetworkCategory" 값이 "Private" (위와 같이) 인 경우,이는 AllJoyn에 대 한 네트워크 연결을 올바르게 구성 했음을 나타냅니다.

### <a name="about-advertisement-and-troubleshooting-discovery-with-getajxmlexe"></a>Getajxml를 사용 하 여 보급 알림 및 문제 해결 정보

Windows 10 UWP AllJoyn 앱에서 AllJoyn 생산자 장치나 앱을 검색할 수 있도록 하려면 정보 기반 검색을 적절 하 게 구현 해야 합니다. GetAjXml 도구를 사용 하 여 쉽게 확인할 수 있습니다. GetAjXml와 관련 된 다운로드 및 사용 정보를 찾으려면 [AllJoyn Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286)를 확인 합니다.

다음은 정보 기반 검색을 지 원하는 예제 장치에 대 한 GetAjXml 출력을 보여 줍니다.

    ----------------------------------------------------------------------
    Discovery   : About Announcement
    Manufacturer: Microsoft
    Model #     : 070773
    Device Name : Raspberry Pi Toaster
    Device ID   : 41d9a124-6913-40c5-a20a-9d1b20f8121b
    App Name   : Toaster Producer
          Bus Name                       Port Object Path
          ============================== ===== ===============================
          :3yZG_wu1.2                       25 /emergency
          :3yZG_wu1.2                       25 /info
          :3yZG_wu1.2                       25 /notificationDismisser
          :3yZG_wu1.2                       25 /notificationProducer
          :3yZG_wu1.2                       25 /toaster
          :3yZG_wu1.2                       25 /warning


위의 예제 `Discovery   : About Announcement` 에서가이 출력에 포함 되었으므로이 alljoyn 생산자는 Windows 10 AllJoyn UWP 앱에서 검색할 수 있습니다. 특정 AllJoyn 생산자에 대해이 출력이 표시 되지 않으면 장치 (생산자) 측의 검색 구현을 조사 해야 합니다.

### <a name="advanced-troubleshooting-with-etw-log-output"></a>ETW 로그 출력을 사용한 고급 문제 해결

ETW (ETW(Windows용 이벤트 추적))는 Windows의 다양 한 기능에 대 한 고급 디버깅 정보를 얻는 데 도움이 될 수 있습니다. 다행히 AllJoyn는 ETW 로깅을 지 원하는 기능 중 하나 이므로이 섹션에서는 AllJoyn에 대해 ETW 로깅을 사용 하도록 설정 하는 방법과 로그에 액세스 하는 방법을 보여 줍니다.

1. 시작 메뉴 검색 텍스트 상자에 "이벤트 로그"를 입력 하 여 이벤트 뷰어를 시작 하 고 "이벤트 로그 보기"를 선택 합니다.
2. "보기" 메뉴에서 "분석 및 디버그 로그 표시"가 선택 되어 있는지 확인 합니다.
3. 왼쪽 탐색 영역에서 "응용 프로그램 및 서비스 로그 > Microsoft > Windows > AllJoyn"로 이동 하 여 디버그 채널과 작동 채널을 모두 사용 하도록 설정 합니다. 아래 스크린샷에서 빨간색 상자를 참조 하세요.
4. AllJoyn에서 발생 하는 문제를 재현 합니다.
5. 오른쪽 "작업" 표시줄에서 "새로 고침"을 클릭 한 다음 "AllJoyn" 폴더 아래의 왼쪽 탐색 모음에서 작동 및 디버그 채널을 확인 합니다.

![AJ_Troubleshooting_ETW](../media/AllJoyn/AJ_Troubleshooting_ETW.jpg)

AllJoyn ETW 추적은 다음과 같이 분할 됩니다.

- 디버그 채널: 자세한 정보 표시, 오류 없음/정보 추적
- 작동 채널: 오류 추적, 오류는 작동 채널에만 출력 됩니다.

ETW 항목에서 정보를 추출 하려면 지정 된 채널에 대 한 목록 보기에서 항목을 마우스 오른쪽 단추로 클릭 한 다음 "복사"를 선택 하 고 "세부 정보를 텍스트로 복사"를 선택 합니다. 그런 다음 텍스트 편집기에 해당 텍스트를 붙여넣으면 아래 예제와 같이 정보를 얻게 됩니다.


    Log Name:       Microsoft-Windows-AllJoyn/Operational
    Source:         Microsoft-Windows-AllJoyn
    Date:           6/1/2015 3:57:45 PM
    Event ID:     2
    Task Category: AJ
    Level:         Error
    Keywords:      (70368744177664),AJ
    User:         LOCAL SERVICE
    Computer:       <computer name>
     
    Description:
    AllJoyn encountered an error 0x902D in module UDP, file ..\udptransport.cc, at line number 10809. See the event user data for more information.
    Event Xml:
    <Event xmlns="http://schemas.microsoft.com/win/2004/08/events/event">
    <System>
       <Provider Name="Microsoft-Windows-AllJoyn" Guid="{2ED299D2-2F6B-411D-8D15-F4CC6FDE0C70}" />
        <EventID>2</EventID>
        <Version>0</Version>
        <Level>2</Level>
        <Task>1</Task>
        <Opcode>10</Opcode>
        <Keywords>0x8000400000000001</Keywords>
       <TimeCreated SystemTime="2015-06-01T22:57:45.626729500Z" />
        <EventRecordID>16</EventRecordID>
       <Correlation />
       <Execution ProcessID="1392" ThreadID="5768" />
       <Channel>Microsoft-Windows-AllJoyn/Operational</Channel>
        <Computer>computer name</Computer>
       <Security UserID="SID" />
    </System>
    <UserData>
       <AJErrorData xmlns="http://manifests.microsoft.com/win/2005/08/windows/alljoyn/events">
           <QStatus>0x902d</QStatus>
           <Message>UDPTransport::DisbleDiscovery(): Not running or stopping; exiting</Message>
           <Module>UDP</Module>
           <File>..\udptransport.cc</File>
           <Line>10809</Line>
        </AJErrorData>
    </UserData>
    </Event>


이 정보는 Microsoft 또는 다른 파트너에 게 문제를 보고할 때 정보를 제공 하거나 AllJoyn 문제를 추적 하는 데 도움이 될 수 있습니다. [ETW 추적 및 MSDN의 이벤트 뷰어](https://msdn.microsoft.com/library/windows/desktop/bb968803.aspx)에 대해 자세히 알아볼 수 있습니다.

### <a name="known-issues-and-limitations"></a>알려진 문제 및 제한 사항

Windows 10의 AllJoyn에 대 한 디자인 별 제한 사항:

- Windows 10 PC에서 실행 되는 앱이 없는 경우 alljoyn 장치 또는 네트워크의 앱에서 AllJoyn 라우터 노드가 자동으로 시작 되지 않습니다. "Net start ajrouter" 명령을 실행 하 여 관리자 권한 명령 프롬프트 또는 Powershell 세션에서 Windows 10 라우터 노드를 시작할 수 있습니다.
- AllJoyn UWP 앱은 동일한 컴퓨터에서 실행 되는 다른 AllJoyn UWP 앱 또는 AllJoyn 데스크톱 앱을 검색 하거나 조작할 수 없습니다. 이는 UWP 앱 용 Windows 10에서 구현 된 앱 격리 약속의 일부입니다. 
  - Visual Studio에서 AllJoyn UWP 앱을 배포 하는 경우 해당 앱에 대해 앱 격리 앱 격리가 무시 됩니다 ("루프백 예외" 라고 함). Visual Studio에서 배포 된 각 UWP 앱은 이러한 앱이 정보 기반 보급 알림/검색을 사용 하는 한 다른 루프백 제외 UWP 앱 및 데스크톱 앱을 검색 하 고 상호 작용할 수 있습니다. "포함 모드"에서 Windows 10 IoT Core를 실행 하는 경우이 루프백 예외가 자동으로 적용 되 고 구성 해야 하는 것은 아닙니다. [MSDN의](https://msdn.microsoft.com/library/windows/apps/Hh780593.aspx)루프백 예외에 대해 자세히 알아볼 수 있습니다.

