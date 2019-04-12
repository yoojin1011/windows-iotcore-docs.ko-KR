---
title: 네트워크 패킷 캡처
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Microsoft Message Analyzer를 사용 하 여 네트워크 패킷 캡처를 사용 하는 방법 알아보기
keywords: windows iot, 네트워크 패킷, 네트워크 패킷 캡처, Microsoft Message Analyzer, PowerShell
ms.openlocfilehash: 1880b6502099c50653e9e60ebc3d4ff3cd926450
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512669"
---
# <a name="network-packet-capture"></a>네트워크 패킷 캡처

사용할 수 있습니다 [Microsoft Message Analyzer](http://www.microsoft.com/en-us/download/details.aspx?id=44226) 를 캡처, 표시 및 Windows 10 IoT Core 장치에서 트래픽을 메시징 프로토콜을 분석 합니다.

![Message Analyzer](../media/NetworkPacketCapture/message-analyzer.png)

## <a name="prerequisites"></a>사전 요구 사항

PowerShell 연결 작업 (단계 1 ~ 8에서 설명한 [PowerShell](../connect-your-device/PowerShell.md)합니다.

## <a name="set-up-your-device"></a>장치 설정

Message Analyzer를 사용 하 여 장치에 연결 하려면 장치 이름을 바꾸려면 먼저 지정 해야 합니다.  통해이 작업을 수행할 수 있습니다 [SSH](../connect-your-device/SSH.md) 또는 [PowerShell](../connect-your-device/PowerShell.md) 사용 하는 `setcomputername` 명령입니다.

![PowerShell 이름 바꾸기 장치](../media/NetworkPacketCapture/powershell-rename-device.png)

장치에서 이름을 바꾼 후 이름 변경 내용을 적용 하려면 장치를 다시 부팅 합니다.

## <a name="turn-off-the-firewall"></a>방화벽을 해제

PowerShell 또는 SSH를 사용 하 여 장치를 연결 하 고 방화벽을 사용 하지 않도록 설정 하려면 다음 명령을 실행 합니다.
    
    netsh advfirewall set allprofiles state off
    
## <a name="connect-to-your-device-using-message-analyzer"></a>Message Analyzer를 사용 하 여 장치에 연결

장치를 설정 했으므로 Microsoft Message Analyzer를 사용 하 여 연결 하겠습니다.

1. 다운로드 합니다 [Microsoft Message Analyzer](http://www.microsoft.com/en-us/download/details.aspx?id=44226)합니다.
2. Message Analyzer를 엽니다.
3. 클릭 `New Session`합니다.

    ![Message Analyzer](../media/NetworkPacketCapture/message-analyzer-new-session.png)
4. 열리는 창에서 클릭 된 `Live Trace` 단추입니다.
    ![Message Analyzer](../media/NetworkPacketCapture/message-analyzer-live-trace.png)
5. 클릭 된 `Edit...` 단추입니다.
    ![Message Analyzer](../media/NetworkPacketCapture/message-analyzer-edit-button.png)
6. IoT 장치의 이름으로 Localhost를 대체 하 고 관리자 사용자 이름 및 암호를 입력 합니다.  클릭 `OK`합니다.
    ![Message Analyzer](../media/NetworkPacketCapture/message-analyzer-edit-target-computers.png)
7. 클릭 합니다 `Select a trace scenario` 드롭다운에서 선택한 `Local Network Interfaces`합니다.
    ![Message Analyzer](../media/NetworkPacketCapture/message-analyzer-trace-scenario.png)
8. 클릭 된 `Start` 단추입니다.
9. 장치의 네트워크 인터페이스를 통해 이동 하는 메시지가 표시 되기 시작 해야 합니다.
    ![Message Analyzer](../media/NetworkPacketCapture/message-analyzer.png)
10. Message Analyzer를 통해 추적을 시작한 후 확인할 수도 있습니다 패킷 캡처 드라이버에서 ETW 메시지 장치의 [웹 인터페이스](DevicePortal.md)합니다.  이 위해 선택 되는 웹 인터페이스의 ETW 탭으로 이동 `Microsoft-Windows-NDIS-PacketCapture` 에서 합니다 `Registered providers` 드롭다운 메뉴를 클릭 하 고는 `Enable` 단추.
    ![Message Analyzer](../media/NetworkPacketCapture/web-etw.png)    
