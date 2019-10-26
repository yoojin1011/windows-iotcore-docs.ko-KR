---
title: headed 및 headless 디바이스
ms.date: 08/28/2017
ms.topic: article
description: 장치에 대해 Windows IoT Core를 구성 하는 방법에 대해 알아봅니다.
keywords: windows iot, 화면, 양방향, 헤드리스, UI
ms.openlocfilehash: 138bc19b355e39db7e6bd4f4441159b03fde26c1
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918097"
---
# <a name="headed-and-headless-devices"></a>양방향 및 헤드리스 장치

Windows 10 IoT Core는 *양방향* 또는 *헤드리스* 모드로 구성할 수 있습니다. 

## <a name="headed-mode"></a>양방향 모드
화살표는 UI가 있는지 여부에 따라 정의 됩니다. 또한 시스템 부팅 시 단일 UI 앱이 시작 되 고 0 개 이상의 "백그라운드 앱" (startuptasks)이 있을 수 있습니다. 

## <a name="headless-mode"></a>헤드리스 모드
헤드리스 모드에는 UI가 없습니다.  UI 기능이 필요 하지 않은 장치는 *헤드리스* 모드로 설정할 수 있습니다. UI 스택이 사용 하지 않도록 설정 되 고 UI 앱이 시작 되지 않습니다. 이렇게 하면 사용 되는 시스템 리소스의 양이 줄어듭니다. 장치에 모니터를 연결 하면 화면이 검게 표시 됩니다.

> [!NOTE]
> 장치를 헤드리스 모드로 전환 하는 경우 아래에 설명 된 Windows 10 IoT Core 대시보드 응용 프로그램을 사용 하 여 해당 IP 주소를 찾을 수 있습니다.

## <a name="changing-the-mode"></a>모드 변경
Windows PowerShell 세션 또는 SSH 세션에서 장치의 양방향/헤드리스 상태를 수정할 수 있습니다. PowerShell에 대해 자세히 알아보려면 [IoT Core 용 PowerShell](../connect-your-device/PowerShell.md) 페이지를 참조 하세요. SSH에 대 한 자세한 내용은 [IoT Core 용 SSH](../connect-your-device/SSH.md) 페이지를 참조 하세요.

* 장치의 현재 상태를 표시 하려면 `setbootoption` 유틸리티를 사용 합니다.

~~~
    [192.168.0.243]: PS C:\> setbootoption.exe
~~~

* 헤드리스 모드를 사용 하도록 장치 상태를 수정 하려면 `setbootoption` 유틸리티 `headless` arg를 사용 합니다.

~~~
    [192.168.0.243]: PS C:\> setbootoption.exe headless
    [192.168.0.243]: PS C:\> shutdown /r /t 0
~~~

* 양방향 모드를 사용 하도록 장치의 상태를 수정 하려면 `setbootoption` 유틸리티 `headed` arg를 사용 합니다.

~~~
    [192.168.0.243]: PS C:\> setbootoption.exe headed
    [192.168.0.243]: PS C:\> shutdown /r /t 0
~~~

## <a name="finding-your-headless-device"></a>헤드리스 장치 찾기

헤드리스 모드에 있는 IoT Core 장치는 **Windows 10 Iot Core 대시보드** 응용 프로그램을 사용 하 여 검색할 수 있습니다.  IoT 대시보드를 다운로드 하려면 [다운로드](http://go.microsoft.com/fwlink/?LinkID=708576) 페이지를 참조 하세요.
응용 프로그램을 실행 하면 로컬 네트워크의 모든 IoT Core 장치에서 ping을 수신 대기 하 고 이름, IP 주소 등의 장치 정보를 표시 합니다.

![Windows 10 IoT Core 대시보드](../media/HeadlessMode/selectDevice.png)
