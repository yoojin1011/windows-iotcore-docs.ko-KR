---
title: 파일 전송 프로토콜
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 파일 전송 프로토콜 (FTP)를 사용 하 여 장치 간에 파일을 전송 하는 방법에 대해 알아봅니다.
keywords: windows iot, FTP, 파일 전송 프로토콜, 파일 전송, 장치
ms.openlocfilehash: 43a64e186c2e783624bb47b89e4fa6322c93e04d
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "60169191"
---
# <a name="file-transfer-protocol"></a>파일 전송 프로토콜
FTP (파일 전송 프로토콜)를 사용 하 여 Windows 10 IoT Core 장치 간에 파일을 전송할 수 있습니다.

> [!IMPORTANT]
> 일반적으로 개발자가 초기 개발 프로세스를 쉽게 수행할 수 있도록 FTP를 권장 합니다. 일반 정품 장치에서 FTP를 사용 하지 않는 것이 좋습니다.

## <a name="starting-the-ftp-server-on-your-device"></a>장치에서 FTP 서버 시작
* 기본적으로는 IoT Core 장치에서 FTP 서버를 사용할 수 없습니다.  장치에서 FTP 서버를 시작 하려면 먼저 [PowerShell](../connect-your-device/PowerShell.md) 또는 [SSH](../connect-your-device/SSH.md)를 통해 장치에 연결 해야 합니다.
* `start C:\Windows\System32\ftpd.exe`를 입력합니다.
* 실행 중인 모든 프로세스를 나열 하는를 입력 `tlist`하 여 서버가 실행 중인지 확인할 수 있습니다.  FTP 서버가를 실행 하는 경우 목록에이 `ftpd.exe` 표시 되어야 합니다.

![FTP 시작](../media/ftp/ftp_start.png)

## <a name="stopping-the-ftp-server-on-your-devicea-namestopftp"></a>장치에서 FTP 서버를 중지 하는 중<a name="stopftp"/>
* IoT Core 장치에서 FTP 서버를 중지 하려면 먼저 [PowerShell](../connect-your-device/PowerShell.md) 또는 [SSH](../connect-your-device/SSH.md)를 통해 장치에 연결 해야 합니다.
* PowerShell을 사용 하 여 연결한 경우 `kill -processname ftpd*` 를 입력 하 여 FTP 프로세스를 중지 합니다.

![FTP PowerShell 중지](../media/ftp/ftp_kill_powershell.png)

* SSH를 사용 하 여 연결한 경우 `kill ftpd*` 를 입력 하 여 FTP 프로세스를 중지 합니다.

![FTP SSH 중지](../media/ftp/ftp_kill_ssh.png)

## <a name="accessing-your-files-over-ftp"></a>FTP를 통해 파일에 액세스
* IoT Core 장치의 FTP 서버는 부팅 시 자동으로 시작 됩니다.  연결 하려면 장치의 IP 주소가 필요 합니다.  장치를 시작할 때 부팅 되는 기본 앱에서 IP 주소를 찾을 수 있습니다.

![Windows IoT Core의 DefaultApp](../media/ftp/DefaultApp.png)

* IP가 있으면 PC에서 **파일 탐색기** 를 열고를 입력 `ftp://<TARGET_DEVICE>`합니다. 여기서 `<TARGET_DEVICE>` 은 장치의 이름 또는 IP 주소입니다. enter 키를 누릅니다.  메시지가 표시 되 면 관리자 사용자 이름과 암호를 입력 합니다.

![FTP 탐색기](../media/ftp/ftp_explorer.png)

* 이제 FTP를 통해 장치의 파일에 액세스할 수 있습니다.

## <a name="changing-the-root-ftp-directory"></a>루트 FTP 디렉터리 변경
* 기본적으로 FTP 서버는 장치의 루트 디렉터리 C:\\에 모든 폴더를 표시 합니다.  루트 디렉터리를 변경 하려면 루트 디렉터리를 매개 변수로 전달 해야 한다는 점을 제외 하 고 동일한 단계를 수행 하 여 FTP 서버를 시작 합니다.
* 이를 변경 하려면 먼저 [PowerShell](../connect-your-device/PowerShell.md) 또는 [SSH](../connect-your-device/SSH.md)를 통해 장치에 연결 합니다.
* FTP 프로세스가 이미 실행 중인 경우이를 [중지](#stopftp) 합니다.
* 을 `start C:\Windows\System32\ftpd.exe <PATH_TO_DIRECTORY>`입력 `C:\Users\DefaultAccount`합니다 `<PATH_TO_DIRECTORY>` . 여기서은 루트 디렉터리 (예:)로 설정 하려는 디렉터리의 절대 경로입니다.

![FTP 시작 매개 변수](../media/ftp/ftp_start_parameter.png)

이제 FTP를 통해 장치에 연결할 때 설정 하는 루트 디렉터리의 내용이 표시 됩니다.

![새 루트 디렉터리가 있는 FTP 탐색기](../media/ftp/ftp_explorer_parameter.png)

이 변경 내용을 영구적으로 적용 하려면에 대 `start ftpd.exe <PATH_TO_DIRECTORY>` 한 호출을 추가 해야 합니다. 여기서은 `C:\Data\Users\DefaultAccount` 루트 디렉터리로 설정할 디렉터리의 절대 경로입니다. 여기 `<PATH_TO_DIRECTORY>` 에는 oemcustomization 지정. cmd를 입력 하 고`C:\Windows\System32`
