---
title: 헤드 및 헤드리스 장치
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Windows IoT Core 장치에 대 한 헤드 또는 헤드리스 모드로 구성 하는 방법에 알아봅니다.
keywords: windows iot, 화면, 양방향, 헤드리스 시스템인 UI
ms.openlocfilehash: 8ac0d7e06477836aa080af1b7556b054957d0cac
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513301"
---
# <a name="headed-and-headless-devices"></a>헤드 및 헤드리스 장치

Windows 10 IoT Core 대해 구성할 수 있습니다 *양방향* 하거나 *헤드리스* 모드입니다. 

## <a name="headed-mode"></a>헤드 모드만
헤드 모드만 UI의 존재로 정의 됩니다. *양방향* 모드는 단일 UI 앱 시스템 부팅 시 시작 됩니다 및 또한 수 있는 0 개 이상 "백그라운드 앱 일" (StartupTasks). 

## <a name="headless-mode"></a>헤드리스 모드
헤드리스 모드로 UI에 있습니다.  UI 기능을 사용 하지 않는 장치 설정할 수 있습니다 *헤드리스* 모드입니다. UI 스택을 사용 하지 않도록 설정 하 고 UI 앱이 시작 되지. 이 사용 된 시스템 리소스의 양을 줄입니다. 모니터 장치에 연결 하는 경우에 화면 black 됩니다.

> [!NOTE]
> 헤드리스 모드로 장치를 배치 하면 해당 IP 주소를 찾으려면 아래에 설명 된 Windows 10 IoT Core 대시보드 응용 프로그램을 사용할 수 있습니다.

## <a name="changing-the-mode"></a>모드 변경
Windows PowerShell 세션 또는 SSH 세션에서 장치의 지 향하는 방향/헤드리스 상태를 수정할 수 있습니다. PowerShell에 대 한 자세한 내용은 참조는 [IoT Core에 대 한 PowerShell](../connect-your-device/PowerShell.md) 페이지입니다. SSH에 대 한 자세한 내용은 참조는 [IoT Core에 대 한 SSH](../connect-your-device/SSH.md) 페이지입니다.

* 장치의 현재 상태를 표시 하려면 사용 된 `setbootoption` 유틸리티.

~~~
    [192.168.0.243]: PS C:\> setbootoption.exe
~~~

* 헤드리스 모드를 사용 하도록 설정 하는 장치의 상태를 수정 하려면 사용 합니다 `setbootoption` 유틸리티를 `headless` arg:

~~~
    [192.168.0.243]: PS C:\> setbootoption.exe headless
    [192.168.0.243]: PS C:\> shutdown /r /t 0
~~~

* 모드도 사용 하는 장치의 상태를 수정 하려면 사용 합니다 `setbootoption` 유틸리티를 `headed` arg:

~~~
    [192.168.0.243]: PS C:\> setbootoption.exe headed
    [192.168.0.243]: PS C:\> shutdown /r /t 0
~~~

## <a name="finding-your-headless-device"></a>헤드리스 장치 찾기

헤드리스 모드에 있는 IoT Core 장치를 사용 하 여 검색할 수는 **Windows 10 IoT Core 대시보드** 응용 프로그램입니다.  IoT 대시보드를 다운로드 하려면 참조는 [다운로드](http://go.microsoft.com/fwlink/?LinkID=708576) 페이지입니다.
를 실행 하는 경우 응용 프로그램에서 로컬 네트워크에 있는 모든 IoT Core 장치 ping에 대 한 수신 대기 하 고 이름, IP 주소 등과 같은 장치 정보를 표시 합니다.

![Windows 10 IoT Core 대시보드](../media/HeadlessMode/selectDevice.png)
