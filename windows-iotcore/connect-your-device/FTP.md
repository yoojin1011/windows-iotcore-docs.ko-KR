---
title: 파일 전송 프로토콜
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 장치에서 파일을 전송할 파일 전송 프로토콜 (FTP)를 사용 하는 방법에 알아봅니다.
keywords: windows iot, FTP, 파일 전송 프로토콜, 파일 전송 장치
ms.openlocfilehash: 43a64e186c2e783624bb47b89e4fa6322c93e04d
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512662"
---
# <a name="file-transfer-protocol"></a>파일 전송 프로토콜
(FTP (파일 전송 프로토콜)을 사용 하면 Windows 10 IoT Core 장치에서 파일을 전송할 수 있습니다.

> [!IMPORTANT]
> FTP는 초기 개발 프로세스를 간편 하는 개발자에 일반적으로 권장 됩니다. 소매 장치에서 FTP를 사용 하는 것은 좋지 않습니다.

## <a name="starting-the-ftp-server-on-your-device"></a>장치에서 FTP 서버를 시작합니다.
* 기본적으로 FTP 서버는 IoT Core 장치에서 비활성화 됩니다.  장치에서 FTP 서버를 시작 하려면 먼저 통해 장치에 연결할 [PowerShell](../connect-your-device/PowerShell.md) 하거나 [SSH](../connect-your-device/SSH.md)합니다.
* 형식 `start C:\Windows\System32\ftpd.exe`
* 서버를 입력 하 여 실행 되 고 있는지 확인할 수 있습니다 `tlist`, 실행 중인 모든 프로세스는 표시 합니다.  FTP 서버를 실행 하는 경우 표시 됩니다 `ftpd.exe` 목록에서입니다.

![FTP 시작](../media/ftp/ftp_start.png)

## <a name="stopping-the-ftp-server-on-your-devicea-namestopftp"></a>장치에서 FTP 서버를 중지합니다.<a name="stopftp"/>
* IoT Core 장치에서 FTP 서버를 중지 하려면 먼저 통해 장치에 연결할 [PowerShell](../connect-your-device/PowerShell.md) 하거나 [SSH](../connect-your-device/SSH.md)합니다.
* PowerShell을 사용 하 여 연결 하는 경우 입력 `kill -processname ftpd*` FTP 프로세스를 중지 합니다.

![FTP PowerShell 중지](../media/ftp/ftp_kill_powershell.png)

* SSH를 사용 하 여 연결 하는 경우 입력 `kill ftpd*` FTP 프로세스를 중지 합니다.

![FTP SSH 중지](../media/ftp/ftp_kill_ssh.png)

## <a name="accessing-your-files-over-ftp"></a>FTP를 통한 파일 액세스
* FTP 서버의 IoT Core 장치 부팅 시 자동으로 시작합니다.  연결 하기 위해 장치의 IP 주소가 필요 합니다.  장치를 시작할 때 부팅 하는 기본 앱에서 IP 주소를 찾을 수 있습니다.

![Windows IoT Core에 DefaultApp](../media/ftp/DefaultApp.png)

* IP를 만든 후 열어 **파일 탐색기** 에 입력 하 여 PC `ftp://<TARGET_DEVICE>`여기서 `<TARGET_DEVICE>` 는 이름 또는 IP 주소에 장치를 다음 Enter 키를 누릅니다.  메시지가 표시 되 면 관리자 사용자 이름 및 암호를 입력 합니다.

![FTP 탐색기](../media/ftp/ftp_explorer.png)

* 이제 FTP를 통해 장치에서 파일을 액세스할 수 있습니다.

## <a name="changing-the-root-ftp-directory"></a>FTP 루트 디렉터리를 변경합니다.
* 기본적으로 FTP 서버에서 장치의 루트 디렉터리 c: 모든 폴더를 표시\\합니다.  루트 디렉터리를 변경 하려면 루트 디렉터리를 매개 변수로 전달 해야 할 점을 제외 하 고 FTP 서버를 시작 하려면 동일한 단계를 수행 합니다.
* 변경 하려면 먼저를 통해 장치에 연결 [PowerShell](../connect-your-device/PowerShell.md) 하거나 [SSH](../connect-your-device/SSH.md)합니다.
* [중지](#stopftp) FTP 프로세스가 이미 실행 중인 경우.
* 형식 `start C:\Windows\System32\ftpd.exe <PATH_TO_DIRECTORY>`, 여기서 `<PATH_TO_DIRECTORY>` 같은 루트 디렉터리로 설정 하려는 디렉터리의 절대 경로 `C:\Users\DefaultAccount`합니다.

![매개 변수를 사용 하 여 FTP 시작](../media/ftp/ftp_start_parameter.png)

이제 FTP 통해 장치에 연결할 때 설정 하는 루트 디렉터리의 내용을 나타납니다.

![새 루트 디렉터리를 사용 하 여 FTP 탐색기](../media/ftp/ftp_explorer_parameter.png)

이와 같이 변경 영구 하려면 호출을 추가 해야 `start ftpd.exe <PATH_TO_DIRECTORY>` 여기서 `<PATH_TO_DIRECTORY>` 같은 루트 디렉터리로 설정 하려는 디렉터리의 절대 경로 `C:\Data\Users\DefaultAccount` OEMCustomization.cmd에에서 배치 `C:\Windows\System32`
