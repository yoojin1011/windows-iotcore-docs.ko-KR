---
title: Windows 파일 공유
ms.date: 08/28/2017
ms.topic: article
description: Windows 파일 공유를 사용 하 여 장치 간에 파일을 전송 하는 방법에 대해 알아봅니다.
keywords: windows iot, 파일 전송, 파일 공유, windows 파일 공유
ms.openlocfilehash: 4ea27622dee8f51d9548bd805a4d9900968f4a17
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918345"
---
# <a name="windows-file-sharing"></a>Windows 파일 공유

Windows 파일 공유를 사용 하 여 장치 간에 파일을 전송할 수 있습니다.

## <a name="accessing-your-files-using-windows-file-sharing"></a>Windows 파일 공유를 사용 하 여 파일 액세스
* Windows IoT Core 장치의 파일 공유 서버는 부팅 시 자동으로 시작 됩니다.  연결 하려면 장치의 IP 주소가 필요 합니다.  장치를 시작할 때 부팅 되는 기본 앱에서 IP 주소를 찾을 수 있습니다.

    ![Windows IoT Core의 DefaultApp](../media/WindowsFileSharing/DefaultApp.png)
    
* IP가 있으면 컴퓨터에서 **파일 탐색기** 를 열고 `\\<TARGET_DEVICE>\c$`를 입력 합니다. 여기서 `<TARGET_DEVICE>`은 Windows IoT Core 장치의 이름 또는 IP 주소입니다. enter 키를 누릅니다.  

메시지가 표시 되 면 관리자 사용자 이름과 암호를 입력 합니다. 사용자 이름은 Windows IoT Core 장치의 IP 주소 앞에와 야 합니다. 예: **Username:** `192.168.1.118\Administrator`  **Password:** `{your_password}`.

![파일 탐색기](../media/WindowsFileSharing/smb_file_explorer.png)

* 이제 Windows 파일 공유를 사용 하 여 장치에서 파일에 액세스할 수 있습니다.

## <a name="starting-and-stopping-the-file-sharing-server"></a>파일 공유 서버 시작 및 중지
* [PowerShell](../connect-your-device/powershell.md) 또는 [SSH](../connect-your-device/ssh.md)를 통해 장치에 연결 합니다.
* 기본적으로 파일 공유 서버는 장치가 부팅 될 때 시작 됩니다.
* 파일 공유 서버를 중지 하려면 다음을 입력 `net stop Server /y`
* 파일 공유 서버를 시작 하려면 다음을 입력 `net start Server`

    ![서버 시작 및 중지](../media/WindowsFileSharing/smb_start_stop.png)
    
## <a name="disabling-and-enabling-the-file-sharing-server-on-startup"></a>시작할 때 파일 공유 서버 사용 안 함 및 사용
* [PowerShell](../connect-your-device/powershell.md) 또는 [SSH](../connect-your-device/ssh.md)를 통해 장치에 연결 합니다.
* 기본적으로 파일 공유 서버는 장치가 부팅 될 때 시작 됩니다.
* 장치를 시작할 때 시작 되지 않도록 파일 공유 서버를 사용 하지 않도록 설정 하려면 다음을 입력 `reg add HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\lanmanserver /v Start /t REG_DWORD /d 0x3 /f`
* 장치를 시작할 때가 시작 되도록 파일 공유 서버를 사용 하도록 설정 하려면을 입력 `reg add HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\lanmanserver /v Start /t REG_DWORD /d 0x2 /f`

    ![서버 사용 안 함](../media/WindowsFileSharing/smb_enable_disable.png)
