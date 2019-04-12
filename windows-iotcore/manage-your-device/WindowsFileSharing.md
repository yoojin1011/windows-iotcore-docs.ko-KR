---
title: Windows 파일 공유
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 장치에서 파일을 전송 하려면 Windows 파일 공유를 사용 하는 방법에 알아봅니다.
keywords: windows iot, 파일 전송, 파일 공유를 windows 파일 공유
ms.openlocfilehash: 00dc17ded4b9c4fbea05faca794766f965d0632a
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513870"
---
# <a name="windows-file-sharing"></a>Windows 파일 공유

장치에서 파일을 전송 하려면 Windows 파일 공유를 사용할 수 있습니다.

## <a name="accessing-your-files-using-windows-file-sharing"></a>Windows 파일 공유를 사용 하 여 파일 액세스
* Windows IoT Core 장치에서 서버를 공유 하는 파일을 부팅 시 자동으로 시작 합니다.  연결 하기 위해 장치의 IP 주소가 필요 합니다.  장치를 시작할 때 부팅 하는 기본 앱에서 IP 주소를 찾을 수 있습니다.

    ![Windows IoT Core에 DefaultApp](../media/WindowsFileSharing/DefaultApp.png)
    
* IP를 만든 후 열어 **파일 탐색기** 입력 하 여 컴퓨터에 `\\<TARGET_DEVICE>\c$`여기서 `<TARGET_DEVICE>` 이름 또는 IP 주소의 Windows IoT Core 장치를 다음 Enter 키를 누릅니다.  

메시지가 표시 되 면 관리자 사용자 이름 및 암호를 입력 합니다. 사용자 이름이 Windows IoT Core 장치 IP 주소 접두사로 추가 해야 합니다. 예: **사용자 이름:** `192.168.1.118\Administrator`  **암호:** `{your_password}`합니다.

![파일 탐색기](../media/WindowsFileSharing/smb_file_explorer.png)

* 이제 Windows 파일 공유를 사용 하 여 장치에서 파일을 액세스할 수 있습니다.

## <a name="starting-and-stopping-the-file-sharing-server"></a>시작 하 고 파일 서버 공유를 중지 합니다.
* 통해 장치에 연결할 [PowerShell](../connect-your-device/powershell.md) 하거나 [SSH](../connect-your-device/ssh.md)합니다.
* 기본적으로 파일 서버 공유 장치 부팅 될 때 시작 됩니다.
* 파일 서버 공유를 중지 하려면 입력 합니다. `net stop Server /y`
* 파일 서버 공유를 시작 하려면 입력 합니다. `net start Server`

    ![서버 시작 및 중지](../media/WindowsFileSharing/smb_start_stop.png)
    
## <a name="disabling-and-enabling-the-file-sharing-server-on-startup"></a>사용 하지 않도록 설정 하 고 시작 시 서버를 공유 하는 파일을 사용 하도록 설정
* 통해 장치에 연결할 [PowerShell](../connect-your-device/powershell.md) 하거나 [SSH](../connect-your-device/ssh.md)합니다.
* 기본적으로 파일 서버 공유 장치 부팅 될 때 시작 됩니다.
* 서버를 공유 하 여 장치를 시작할 때 시작 되지 않도록 파일을 사용 하지 않으려면 입력 `reg add HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\lanmanserver /v Start /t REG_DWORD /d 0x3 /f`
* 장치가 시작 되 면 작업이 시작 되는 서버를 공유 하는 파일을 사용 하도록 설정 하려면 입력 합니다. `reg add HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\lanmanserver /v Start /t REG_DWORD /d 0x2 /f`

    ![서버 사용 안 함](../media/WindowsFileSharing/smb_enable_disable.png)
