---
title: AllJoyn 문제 해결
author: saraclay
ms.author: saclayt
ms.date: 09/07/17
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: 설정 문제 해결 및 알려진된 문제를 다루는이 포괄적인 가이드를 사용 하 여 AllJoyn 기술 문제를 해결 하는 방법을 알아봅니다.
keywords: windows iot, AllJoyn
ms.openlocfilehash: 8b93242c8f583199ee5890c6d0d15985f9025175
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512478"
---
> [!NOTE]
> 보관 된 설명서가 표시 됩니다. Windows 10 IoT에서 더 이상 AllJoyn 사용할 수 없습니다. 질문에 대 한 GitHub에서 문제를 제기 하거나 아래 설명에 의견을 남길 하세요.

# <a name="alljoyn-troubleshooting"></a>AllJoyn 문제 해결

[AllJoyn](https://allseenalliance.org/developers/learn) 는 IoT 장치 및 응용 프로그램을 검색 하 고 서로 상호 작용할 수 있도록 하는 기술입니다. AllJoyn으로 Windows 10 및 Windows 10 SDK를 빌드 되었기 때문 AllJoyn 유니버설 Windows 플랫폼 (UWP)를 사용 하 여 기능을 활용 하기 쉽습니다.

![AJ_Troubleshooting_intro](../media/AllJoyn/AJ_Troubleshooting_intro.jpg)

이 블로그 게시물 AllJoyn 네트워크와 장치를 구성 하 고 또한 작업은 예상 대로 작동 하지 않을 경우에 따라 문제 해결 단계를 제공 하는 데 도움이 됩니다. 이 문서의 주된 초점은 UWP AllJoyn 클라이언트 앱 (AllJoyn 소비자) AllJoyn 장치 (AllJoyn 생산자)와 통신을 하도록 할 예정입니다. UWP AllJoyn 생산자 앱 통신할 수 있도록 하는 데 필요한 구성 단계와 동일한 대부분 0.020 추가 세부 정보 향후 블로그 포스트와 기사를 합니다.

### <a name="app-development-checklist"></a>앱 개발 검사 목록

Windows 10 용 UWP 앱을 작성 하는 경우 있습니다 되었는지 확인 해야 합니다.

1. (참고 대/소문자 구분) 응용 프로그램 매니페스트에 'allJoyn' 기능을 선언 했습니다.
2. 특정 아키텍처를 대상으로 수를 선택 했습니다. (' 임의 CPU'를 사용 하 여 Windows 런타임 구성 요소를 빌드할 수 없으므로 일부 경우에 필요한 일부 Visual Studio 2017 알려진된 문제를 작성).

Windows 10 용 UWP 기반 응용 프로그램을 되지 않는 앱 또는 장치 소프트웨어를 작성 하는 경우 Windows 10에서 AllJoyn와 호환성을 위해 다음 검사 목록을 검토 해야 합니다.

1. 생산자를 구현 하는 경우 확인 된 정보는 사용 중인 인터페이스와 광고/검색 정보 기반입니다. 정보 인터페이스가 [AllSeen Alliance 웹 사이트에서 문서화 된](https://allseenalliance.org/developers/learn/core/about-announcement/interface)합니다.
2. 최상의 결과 얻으려면 15.04 AllJoyn 코드 베이스에서 사용할 수 있는 사용 합니다 [다운로드 섹션](https://allseenalliance.org/developers/download) AllSeen Alliance 웹 사이트의.

### <a name="network-setup-and-troubleshooting"></a>네트워크 설정 및 문제 해결

검색 하 고 서로 상호 작용 하는 일을 할 수 AllJoyn 장치에 대 한 네트워크 구성 및 각 장치에 대 한 설정을 다음 충족 해야 합니다.

1. 모든 AllJoyn 장치 동일한 네트워크에 연결 되어 있고 동일한 서브넷에 있습니다.
2. Windows 10 PC: "장치 및 콘텐츠를 찾을" AllJoyn (Phone에 적용 되지 않음)를 사용 하 여 사용 중인 네트워크에 대해 활성화 됩니다.

PC에서 인지 확인 하려면 다른 컴퓨터/장치는 동일한 서브넷에 다음과 같이 CMD 또는 PowerShell 창에서 추적 경로 명령을 사용할 수 있습니다.

    PS C:\Users\user> tracert WIN10PC1
     
    Tracing route to WIN10PC1 [fe80::657d:d8bf:176f:d0b2%24]
     
    over a maximum of 30 hops:
     
    1       1 ms     1 ms     1 ms   WIN10PC1 [fe80::657d:d8bf:176f:d0b2]
     
    Trace complete.

첫 번째 숫자 출력, 홉 수 이며 해당 값은 "1" 이므로 두 컴퓨터가 동일한 서브넷에는 의미입니다.

일반적인 AllJoyn 네트워크 설정의 예는 다음과 같습니다. 이 예제에서는 검색 하 고 동일한 서브넷에 있는 것을 가정 AllJoyn 사용 하 여 서로 상호 작용할 수 있게 됩니다 모든 장치 표시 합니다.

![AJ_Troubleshooting_Devices](../media/AllJoyn/AJ_Troubleshooting_Devices.jpg)

AllJoyn 장치를 사용 하 여 네트워크에 Windows 10 PC를 연결한 경우에 찾기 장치 및 Pc에 대 한 네트워크에 있는 대화 상자가 표시 하는 경우 "예"를 클릭 해야 합니다. (참고: 이 적용 되지 않습니다 이러한 대화 상자는 Windows 10 Phone에서 네트워크를 조인 하는 경우).

여기에 표시 된 대로 Wi-fi 설정에서 "고급 설정" 페이지에서이 설정을 관리할 수도 있습니다. (이 페이지는 사용 하는 Windows 10 참가자 빌드에 따라 약간 다르게 보일 수 있습니다)

![AJ_Troubleshooting_Settings](../media/AllJoyn/AJ_Troubleshooting_Settings.jpg)

"장치 찾기 및 콘텐츠"에 대 한 토글 AllJoyn 기능을 사용 하도록 설정 하려면 "On" 위치에 있어야 합니다.

기존 네트워크 연결의 경우이 옵션은 "Get-NetConnectionProfile" Powershell cmdlet을 실행 하 여 제대로 구성 되어 있는지 여부를 쉽게 확인할 수 있습니다. (Windows 10 Phone 용는 적용 되지 않습니다 note).

Get-NetConnectionProfile 출력의 예:

    PS C:\Users\user> Get-NetConnectionProfile
     
    Name             : myWirelessNetwork
    InterfaceAlias   : vEthernet (Intel(R) Dual Band Wireless-AC 7260 Virtual Switch)
    InterfaceIndex   : 24
    NetworkCategory : Private
    IPv4Connectivity : Internet
    IPv6Connectivity : LocalNetwork


적절히 구성 된 것을 지정이 "NetworkCategory" 값 "개인" (위와 같이) 인 경우 AllJoyn에 대 한 네트워크 연결 합니다.

### <a name="about-advertisement-and-troubleshooting-discovery-with-getajxmlexe"></a>보급 알림 및 Getajxml.exe 사용 하 여 검색 문제 해결에 대 한

AllJoyn 생산자 장치 또는 Windows 10 UWP AllJoyn 앱에서 검색 가능 하도록 앱에 대 한 기준에 대 한 검색 올바르게 구현 되어야 합니다. GetAjXml.exe 도구를 사용 하 여 쉽게 확인할 수 있습니다. 다운로드 및 GetAjXml.exe와 관련 된 사용량 정보를 찾으려면 체크 아웃 [AllJoyn Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286)합니다.

다음 검색에 대 한 기반을 지 원하는 예제 장치의 GetAjXml.exe 출력을 보여 줍니다.

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


위의 예에서 있으므로 `Discovery   : About Announcement` 포함 된이 출력에서이 AllJoyn 생산자를 Windows 10 AllJoyn UWP 앱에서 검색할 수 있습니다. 이 출력은 특정 AllJoyn 생산자에 대 한 표시 되지 않는 경우에 검색 구현 (공급자) 장치 쪽에서 조사 해야 합니다.

### <a name="advanced-troubleshooting-with-etw-log-output"></a>ETW 로그 출력을 사용한 고급 문제 해결

이벤트 추적에 대 한 Windows (ETW) Windows에서 다양 한 기능에 대 한 디버깅 정보를 고급 가져올 수 있습니다. 다행히 AllJoyn ETW 로깅을 지원,이 섹션에서 살펴보겠습니다 ETW AllJoyn에 대 한 로깅을 사용 하도록 설정 하는 방법과 로그에 액세스 하는 방법을 사용 하 여 기능 중 하나입니다.

1. 시작 메뉴 검색 텍스트 상자에 "이벤트 로그"를 입력 하 여 이벤트 뷰어를 시작 하 고 "이벤트 로그 보기"를 선택 합니다.
2. [보기] 메뉴에서 "표시 분석 및 디버그 로그"가 선택 되어 있는지를 확인 합니다.
3. "응용 프로그램 및 서비스 로그 > Microsoft > Windows > AllJoyn" 폴더 보기에서 왼쪽된 탐색에서 트리 뷰를 탐색 및 디버그 채널 및 Operational 채널을 사용 하도록 설정 합니다. (아래 스크린샷에서 빨간색 상자 참조).
4. AllJoyn를 사용 하 여 발생 하는 문제를 재현 합니다.
5. "Refresh" 오른쪽 "작업" 막대에서 클릭 한 다음 "AllJoyn" 폴더 아래에 있는 왼쪽된 탐색 모음에서 운영 및 디버그 채널을 확인 합니다.

![AJ_Troubleshooting_ETW](../media/AllJoyn/AJ_Troubleshooting_ETW.jpg)

AllJoyn ETW 추적 같이 분할 됩니다.

- 채널을 디버그 합니다. 자세한 정보 표시, 비-오류/정보 추적
- 작동 채널: 오류 추적, 오류는 작동 채널에만 출력

ETW 항목에서 정보를 추출, 하기 위해 지정된 된 채널에 대 한 목록 뷰에서 항목을 마우스 오른쪽 단추로 클릭 하 고 "복사" 및 "세부 정보로 텍스트 복사"를 선택 합니다 수 있습니다. 다음 해당 텍스트를 텍스트 편집기에 붙여 넣을 경우 아래 예제와 같은 정보를 해야 합니다.


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


이 정보는 AllJoyn 문제를 추적 하거나 Microsoft 또는 다른 파트너에 문제를 보고할 때 세부 정보를 제공할 수 있습니다. 에 대 한 자세한 내용은 [ETW 추적 및 MSDN에서 이벤트 뷰어](https://msdn.microsoft.com/library/windows/desktop/bb968803.aspx)합니다.

### <a name="known-issues-and-limitations"></a>알려진 문제 및 제한 사항

Windows 10에서 AllJoyn에 대 한 설계에 따른 제한 사항:

- AllJoyn 라우터 노드에 앱이 없습니다. Windows 10 PC에서 실행 하는 경우는 AllJoyn 장치 또는 네트워크에서 앱 자동 시작 아닙니다. Windows 10 라우터 노드의 "ajrouter net start" 명령을 실행 하 여 관리자 권한 명령 프롬프트 또는 Powershell 세션에서 시작할 수 있습니다.
- AllJoyn UWP 앱을 검색 하거나 다른 AllJoyn UWP 앱 또는 동일한 컴퓨터에서 실행 중인 AllJoyn 데스크톱 앱을 조작할 수 없습니다. UWP 앱 용 Windows 10에서 구현 되는 앱 격리 약속의 부분입니다. 
  - Visual Studio에서 AllJoyn UWP 앱을 배포 하는 경우 앱 격리 앱 격리 ("루프백 제외" 라는) 해당 앱에 대해 무시 됩니다. Visual Studio에서 배포 된 각 UWP 앱 검색 하 고 광고/검색에 대 한 기반을 사용 하 여 해당 앱으로 다른 루프백 예외 UWP 앱 및 데스크톱 앱과 상호 작용 하는 일을 할 수 있습니다. "포함 모드"에서 Windows 10 IoT Core 실행 하는이 루프백 예외를 자동으로 적용 되 면 구성 해야 하는 사항도 아닙니다. 자세한 내용은 루프백 예외에 대 한 [MSDN의](https://msdn.microsoft.com/library/windows/apps/Hh780593.aspx)합니다.

