---
title: SSH (보안 셸)
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 보안 셸을 사용 하 여 원격으로 관리 하 고 IoT Core 장치를 구성 하는 방법에 알아봅니다.
keywords: SSH 클라이언트, PuTTY, SSH, 원격, 보안 셸, windows iot
ms.openlocfilehash: 2c83184507a840c6017b1dfe36ac915004057d9a
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513230"
---
# <a name="secure-shell-ssh"></a>SSH (보안 셸)
보안 셸 (SSH)를 사용 하면 원격으로 관리 및 Windows IoT Core 장치를 구성할 수 있습니다.

## <a name="using-the-windows-10-openssh-client"></a>Windows 10 OpenSSH 클라이언트를 사용 하 여
> [!IMPORTANT]
> 클라이언트 Windows OpenSSH SSH 클라이언트 호스트 OS는 Windows 10 버전 1803(17134) 필요 합니다. 또한 Windows 10 IoT Core 장치 실행 되어야 합니다 RS5 Windows Insider Preview 릴리스 17723 이상.

합니다 **OpenSSH 클라이언트** 선택적 기능으로 1803 (빌드 17134)에서 Windows 10에 추가 되었습니다. 검색할 수 있습니다 클라이언트를 설치 하려면 **선택적 기능 관리** Windows 10 설정에서 합니다. 경우는 **OpenSSH 클라이언트가** 선택한 설치 된 기능 목록에 나열 되지 **기능을 추가할**합니다.

![기능 추가](../media/SSH/add_a_feature.png)

다음 선택 **OpenSSH 클라이언트가** 목록에서 클릭 **설치**합니다.

![OpenSSH 클라이언트 설치](../media/SSH/optional_features.png)

다음 명령을 사용 하는 사용자 이름 및 암호 로그인:

```cmd
ssh administrator@host
```

여기서 호스트는 Windows IoT Core 장치 IP 주소 또는 장치 이름입니다.

처음 연결 하면 다음과 같은 메시지가 표시:

```cmd
The authenticity of host 'hostname (192.168.0.12)' can't be established.
ECDSA key fingerprint is SHA256:RahZpBFpecRiPmw8NGSa+7VKs8mgqQi/j2i1Qr9lUNU.
Are you sure you want to continue connecting (yes/no)?
```

형식 **yes** 누릅니다 **입력**합니다.

으로 로그인 해야 할 경우 **DefaultAccount** 대신 관리자로 해야 키를 생성 하 고 키를 사용 하 여 로그인 합니다.  IoT 장치에 연결 하려는 데스크톱에서 powershell 창을 열고 개인 데이터 폴더로 변경 (예: cd ~)

```cmd
cd ~
ssh-keygen -t rsa -f id_rsa
```

Ssh 에이전트 (선택 사항, single sign-on 환경을)를 사용 하 여 키를 등록 합니다.  Ssh-추가 로그인으로 ACL에 처리 됩니다 하는 폴더에서 수행 해야 사용자 (Builtin\Administrators NT_AUTHORITY\System 사용자와도 확인).  기본 cd에서 ~ powershell에서 충분 해야 아래와 같이 합니다.

```cmd
cd ~
net start ssh-agent
ssh-add id_rsa
```

> [!TIP]
> Ssh 에이전트 서비스는 사용 하지 않도록 하는 메시지가 표시 되 면 사용 하 여 설정할 수 있습니다. **sc.exe의 config ssh 에이전트 시작 = auto**

사용 하도록 설정 하려면 single Windows IoT Core 장치에 공개 키를 추가 **authorized_keys** 파일입니다.  하나만 있는 경우 키 복사한 공개 키 파일을 원격으로 또는 **authorized_keys** 파일입니다.

```cmd
net use X: \\host\c$ /user:host\administrator
if not exist x:\data\users\defaultaccount\.ssh md x:\data\users\defaultaccount\.ssh
copy .\id_rsa.pub x:\data\users\defaultaccount\.ssh\authorized_keys
```

Ssh 에이전트를 사용 하 여 키를 등록 하지 않은 경우 로그인 하려면 명령줄에 지정 해야 합니다. 

```cmd
ssh -i .\id_rsa DefaultAccount@host
```

Ssh 에이전트를 사용 하 여 개인 키가 등록 하는 경우 지정 해야 <strong>DefaultAccount@host</strong>:

```cmd
ssh DefaultAccount@host
```

처음 연결 하면 다음과 같은 메시지가 표시:

```cmd
The authenticity of host 'hostname (192.168.0.12)' can't be established.
ECDSA key fingerprint is SHA256:RahZpBFpecRiPmw8NGSa+7VKs8mgqQi/j2i1Qr9lUNU.
Are you sure you want to continue connecting (yes/no)?
```

형식 **yes** 누릅니다 **입력**합니다.

하면 이제 연결로 **DefaultAccount**

Single sign-on을 사용 하 여 **관리자** 계정, Windows IoT Core 장치에서 c:\data\ProgramData\ssh\administrators_authorized_keys에 공개 키를 추가 합니다. 

```cmd
net use X: \\host\c$ /user:host\administrator
copy .\id_rsa.pub x:\data\ProgramData\ssh\administrators_authorized_keys
icacls x:\data\ProgramData\ssh\administrators_authorized_keys /remove "NT AUTHORITY\Authenticated Users"
icaclsx:\data\ProgramData\ssh\administrators_authorized_keys /inheritance:r
```

또한 동일한 디렉터리에 ssh_host_dsa_key의 ACL에 맞게 administrators_authorized_keys에 대 한 ACL을 설정 해야 합니다.

```cmd
icacls x:\data\ProgramData\ssh\administrators_authorized_keys /remove "NT AUTHORITY\Authenticated Users"
icacls x:\data\ProgramData\ssh\administrators_authorized_keys /inheritance:r
```

Powershell을 사용 하 여 ACL을 설정 하려면

```cmd
get-acl x:\data\ProgramData\ssh\ssh_host_dsa_key | set-acl x:\data\ProgramData\ssh\administrators_authorized_keys
```

> [!NOTE]
> 표시 되 면을 **원격 호스트가 식별 변경** Windows 10 IoT Core 장치에 변경을 수행한 후 메시지를 편집 C:\Users\<사용자 이름 >\.ssh\known_hosts 및 변경 된 호스트를 제거 합니다.

참고 항목: [Win32-OpenSSH](https://github.com/PowerShell/Win32-OpenSSH/wiki/ssh.exe-examples)

## <a name="using-putty"></a>PuTTY를 사용 하 여

### <a name="download-a-ssh-client"></a>SSH 클라이언트를 다운로드 합니다.
SSH를 사용 하 여 장치에 연결 하려면 먼저 해야와 같은 SSH 클라이언트를 다운로드 [PuTTY](http://the.earth.li/~sgtatham/putty/latest/x86/putty.exe)합니다.

### <a name="connect-to-your-device"></a>장치에 연결
* 장치에 연결 하려면 먼저 장치의 IP 주소를 가져올 해야 합니다.  Windows IoT Core 장치를 부팅 한 후 IP 주소는 장치에 연결 화면에 표시 됩니다.

    ![Windows IoT Core에 DefaultApp](../media/SSH/DefaultApp.png)

* 이제 PuTTY를 시작 하 고 IP 주소를 입력 합니다 `Host Name` 있는지 확인 하 고 텍스트 상자를 `SSH` 라디오 단추를 선택 합니다.  클릭 `Open`합니다.

    ![PuTTY 구성](../media/SSH/putty_config.png)

* 컴퓨터에서 처음으로 장치에 연결 하는 않으려면, 다음과 같은 보안 경고가 표시 될 수 있습니다.  클릭 `Yes` 를 계속 합니다.

    ![PuTTY 보안 경고](../media/SSH/putty_security_prompt.png)

* 연결이 성공적으로 수행 되었으면 표시 `login as:` 화면에서 로그인 하 라는 합니다.  
    입력 `Administrator` 및 enter 키를 누릅니다.  기본 암호를 입력 한 다음 `p@ssw0rd` 누릅니다 암호를 입력 합니다.

    ![PuTTY 로그인](../media/SSH/putty_login.png)

    성공적으로 로그인 할 경우 다음과 같이 표시 됩니다.

    ![PuTTY 콘솔](../media/ssh/putty_console.png)

### <a name="update-account-password"></a>계정 암호 업데이트

것 **좋습니다** 관리자 계정에 대 한 기본 암호를 업데이트 하는 합니다.

이렇게 하려면 PuTTY 콘솔에서 다음 명령을 입력 바꾸기 `[new password]` 강력한 암호를 사용 하 여:
    
    net user Administrator [new password]
    
### <a name="configure-your-windows-iot-core-device"></a>Windows IoT Core 장치 구성
* Visual Studio 2017에서 응용 프로그램을 배포 하는 일을 할 일에 Visual Studio 원격 디버거를 Windows IoT Core 장치에서 실행 되 고 있는지 확인 해야 합니다. 원격 디버거는 컴퓨터 부팅 시 자동으로 시작 됩니다. 이중을 확인 하려면 tlist 명령을 사용 하 여 powershell에서 실행 중인 모든 프로세스를 나열 합니다. 장치에서 실행 되는 msvsmon.exe의 두 인스턴스가 없어야 합니다.

* 있기 시간 제한 초과로 Visual Studio 원격 디버거를 오랜 기간 전까지 비활성 시간 후 합니다. Visual Studio Windows IoT Core 장치에 연결할 수 없는 경우, 장치 다시 부팅 하십시오.

* 원한다 면 장치를 이름을 변경할 수 있습니다. '컴퓨터 이름'를 변경 하려면 사용 된 `setcomputername` 유틸리티.

        setcomputername <new-name>

    변경 내용을 적용 하려면 장치를 다시 부팅 해야 합니다. 사용할 수는 `shutdown` 다음과 같이 명령:

        shutdown /r /t 0
        
### <a name="commonly-used-utilities"></a>유틸리티를 사용 하는 일반적으로

참조를 [명령줄 유틸리티](../manage-your-device/CommandLineUtils.md) 페이지 목록은 명령 및 유틸리티 SSH와 함께 사용할 수 있습니다.
