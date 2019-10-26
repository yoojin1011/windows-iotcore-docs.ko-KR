---
title: 네트워크 패킷 캡처
ms.date: 08/28/2017
ms.topic: article
description: Microsoft Message Analyzer를 사용 하 여 네트워크 패킷 캡처를 사용 하도록 설정 하는 방법을 알아봅니다.
keywords: windows iot, 네트워크 패킷, 네트워크 패킷 캡처, Microsoft Message Analyzer, PowerShell
ms.openlocfilehash: 593b6f4f8650e074666dda06feb88e6afccf5e61
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72917425"
---
# <a name="network-packet-capture"></a>네트워크 패킷 캡처

[Microsoft Message Analyzer](http://www.microsoft.com/en-us/download/details.aspx?id=44226) 를 사용 하 여 Windows 10 IoT Core 장치에서 프로토콜 메시징 트래픽을 캡처, 표시 및 분석할 수 있습니다.

![메시지 분석기](../media/NetworkPacketCapture/message-analyzer.png)

## <a name="prerequisites"></a>필수 구성 요소

Powershell 연결 작업 ( [powershell](../connect-your-device/PowerShell.md)에서 설명 하는 1 ~ 8 단계).

## <a name="set-up-your-device"></a>장치 설정

메시지 분석기를 사용 하 여 장치에 연결 하려면 먼저 장치 이름을 변경 해야 합니다.  `setcomputername` 명령을 사용 하 여 [SSH](../connect-your-device/SSH.md) 또는 [PowerShell](../connect-your-device/PowerShell.md) 을 통해 수행할 수 있습니다.

![PowerShell 장치 이름 바꾸기](../media/NetworkPacketCapture/powershell-rename-device.png)

장치의 이름을 바꾼 후 장치를 다시 부팅 하 여 이름 변경을 적용 합니다.

## <a name="turn-off-the-firewall"></a>방화벽 해제

PowerShell 또는 SSH를 사용 하 여 장치에 연결 하 고 다음 명령을 실행 하 여 방화벽을 사용 하지 않도록 설정 합니다.
    
    netsh advfirewall set allprofiles state off
    
## <a name="connect-to-your-device-using-message-analyzer"></a>메시지 분석기를 사용 하 여 장치에 연결

이제 장치가 설정 되었으므로 Microsoft Message Analyzer를 사용 하 여 연결 하겠습니다.

1. [Microsoft Message Analyzer](http://www.microsoft.com/en-us/download/details.aspx?id=44226)를 다운로드 합니다.
2. 메시지 분석기를 엽니다.
3. `New Session`를 클릭 합니다.

    ![메시지 분석기](../media/NetworkPacketCapture/message-analyzer-new-session.png)
4. 열리는 창에서 `Live Trace` 단추를 클릭 합니다.
    ![Message Analyzer](../media/NetworkPacketCapture/message-analyzer-live-trace.png)
5. `Edit...` 단추를 클릭 합니다.
    ![Message Analyzer](../media/NetworkPacketCapture/message-analyzer-edit-button.png)
6. Localhost를 IoT 장치의 이름으로 바꾸고 관리자 사용자 이름 및 암호를 입력 합니다.  그런 다음 `OK`를 클릭 합니다.
    ![Message Analyzer](../media/NetworkPacketCapture/message-analyzer-edit-target-computers.png)
7. `Select a trace scenario` 드롭다운을 클릭 하 고 `Local Network Interfaces`을 선택 합니다.
    ![Message Analyzer](../media/NetworkPacketCapture/message-analyzer-trace-scenario.png)
8. `Start` 단추를 클릭 합니다.
9. 장치에서 네트워크 인터페이스를 통과 하는 메시지가 표시 되기 시작 해야 합니다.
    ![Message Analyzer](../media/NetworkPacketCapture/message-analyzer.png)
10. 메시지 분석기를 통해 추적을 시작한 후 장치의 [웹 인터페이스](DevicePortal.md)에서 패킷 캡처 드라이버의 ETW 메시지도 볼 수 있습니다.  이렇게 하려면 웹 인터페이스의 ETW 탭으로 이동 하 여 `Registered providers` 드롭다운 메뉴에서 `Microsoft-Windows-NDIS-PacketCapture`를 선택 하 고 `Enable` 단추를 클릭 합니다.
    ![Message Analyzer](../media/NetworkPacketCapture/web-etw.png)    
