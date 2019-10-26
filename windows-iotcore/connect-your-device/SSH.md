---
title: SSH (Secure Shell)
ms.date: 08/28/2017
ms.topic: article
description: Secure shell을 사용 하 여 IoT Core 장치를 원격으로 관리 하 고 구성 하는 방법을 알아봅니다.
keywords: windows iot, secure shell, remote, SSH client, PuTTY, SSH
ms.openlocfilehash: 1fe94a29f04ac01efc94079425ac4a5a0dab34f6
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918304"
---
# <a name="secure-shell-ssh"></a>SSH (Secure Shell)
SSH (Secure Shell)를 사용 하 여 Windows IoT Core 장치를 원격으로 관리 하 고 구성할 수 있습니다.

## <a name="using-the-windows-10-openssh-client"></a>Windows 10 OpenSSH 클라이언트 사용
> [!IMPORTANT]
> Windows OpenSSH 클라이언트를 사용 하려면 SSH 클라이언트 호스트 OS가 Windows 10 버전 1803 (17134) 여야 합니다. 또한 Windows 10 IoT Core 장치는 RS5 Windows Insider Preview 릴리스 17723 이상을 실행 해야 합니다.

**OpenSSH Client** 가 선택적 기능으로 1803 (빌드 17134)의 Windows 10에 추가 되었습니다. 클라이언트를 설치 하려면 Windows 10 설정에서 **관리 옵션 기능** 을 검색 합니다. **OpenSSH 클라이언트가** 설치 된 기능 목록에 표시 되지 않는 경우 **기능 추가**를 선택 합니다.

![기능 추가](../media/SSH/add_a_feature.png)

그런 다음 목록에서 **OpenSSH Client** 를 선택 하 고 **설치**를 클릭 합니다.

![OpenSSH Client 설치](../media/SSH/optional_features.png)

사용자 이름 및 암호로 로그인 하려면 다음 명령을 사용 합니다.

```cmd
ssh administrator@host
```

여기서 host는 Windows IoT Core 장치의 IP 주소 또는 장치 이름입니다.

처음 연결 하는 경우 다음과 같은 메시지가 표시 됩니다.

```cmd
The authenticity of host 'hostname (192.168.0.12)' can't be established.
ECDSA key fingerprint is SHA256:RahZpBFpecRiPmw8NGSa+7VKs8mgqQi/j2i1Qr9lUNU.
Are you sure you want to continue connecting (yes/no)?
```

**예** 를 입력 하 고 **enter**키를 누릅니다.

관리자가 아닌 **Defaultaccount** 로 로그인 해야 하는 경우 키를 생성 하 고 키를 사용 하 여 로그인 해야 합니다.  IoT 장치에 연결 하려는 바탕 화면에서 powershell 창을 열고 개인 데이터 폴더 (예: cd ~)로 변경 합니다.

```cmd
cd ~
ssh-keygen -t rsa -f id_rsa
```

Ssh-에이전트를 사용 하 여 키를 등록 합니다 (선택 사항, Single Sign-On 환경의 경우).  사용자가 로그인 한 사용자 (Builtin\Administrators 및 NT_AUTHORITY\System 사용자 이기도 함)로 ACL을 사용 하는 폴더에서 ssh 추가를 수행 해야 합니다.  기본적으로 cd ~ powershell은 아래와 같이 충분 해야 합니다.

```cmd
cd ~
net start ssh-agent
ssh-add id_rsa
```

> [!TIP]
> Ssh 에이전트 서비스를 사용할 수 없다는 메시지가 표시 되 면 **sc.exe 구성 ssh-에이전트 시작 = auto** 를 사용 하 여 사용 하도록 설정할 수 있습니다.

Single sign을 사용 하도록 설정 하려면 공개 키를 Windows IoT Core device **authorized_keys** 파일에 추가 합니다.  또는 키가 하나만 있는 경우에는 공개 키 파일을 원격 **authorized_keys** 파일에 복사 합니다.

```cmd
net use X: \\host\c$ /user:host\administrator
if not exist x:\data\users\defaultaccount\.ssh md x:\data\users\defaultaccount\.ssh
copy .\id_rsa.pub x:\data\users\defaultaccount\.ssh\authorized_keys
```

Ssh 에이전트를 사용 하 여 키를 등록 하지 않은 경우 로그인 하려면 명령줄에 지정 해야 합니다. 

```cmd
ssh -i .\id_rsa DefaultAccount@host
```

개인 키가 ssh 에이전트에 등록 된 경우 <strong>DefaultAccount@host</strong>지정 해야 합니다.

```cmd
ssh DefaultAccount@host
```

처음 연결 하는 경우 다음과 같은 메시지가 표시 됩니다.

```cmd
The authenticity of host 'hostname (192.168.0.12)' can't be established.
ECDSA key fingerprint is SHA256:RahZpBFpecRiPmw8NGSa+7VKs8mgqQi/j2i1Qr9lUNU.
Are you sure you want to continue connecting (yes/no)?
```

**예** 를 입력 하 고 **enter**키를 누릅니다.

이제 **Defaultaccount** 로 연결 되어야 합니다.

**관리자** 계정으로 Single Sign-On를 사용 하려면 Windows IoT Core 장치의 c:\data\ProgramData\ssh\administrators_authorized_keys에 공개 키를 추가 합니다. 

```cmd
net use X: \\host\c$ /user:host\administrator
copy .\id_rsa.pub x:\data\ProgramData\ssh\administrators_authorized_keys
icacls x:\data\ProgramData\ssh\administrators_authorized_keys /remove "NT AUTHORITY\Authenticated Users"
icaclsx:\data\ProgramData\ssh\administrators_authorized_keys /inheritance:r
```

또한 administrators_authorized_keys에 대 한 ACL이 동일한 디렉터리에 있는 ssh_host_dsa_key의 ACL과 일치 하도록 설정 해야 합니다.

```cmd
icacls x:\data\ProgramData\ssh\administrators_authorized_keys /remove "NT AUTHORITY\Authenticated Users"
icacls x:\data\ProgramData\ssh\administrators_authorized_keys /inheritance:r
```

Powershell을 사용 하 여 ACL을 설정 하려면

```cmd
get-acl x:\data\ProgramData\ssh\ssh_host_dsa_key | set-acl x:\data\ProgramData\ssh\administrators_authorized_keys
```

> [!NOTE]
> Windows 10 IoT Core 장치를 변경한 후 **원격 호스트 ID 변경** 메시지가 표시 되 면 C:\Users\<사용자 이름 >\.하 고 변경 된 호스트를 제거 합니다.

참고 항목: [Win32-OpenSSH](https://github.com/PowerShell/Win32-OpenSSH/wiki/ssh.exe-examples)

## <a name="using-putty"></a>PuTTY 사용

### <a name="download-a-ssh-client"></a>SSH 클라이언트 다운로드
SSH를 사용 하 여 장치에 연결 하기 위해 먼저 [PuTTY](http://the.earth.li/~sgtatham/putty/latest/x86/putty.exe)와 같은 ssh 클라이언트를 다운로드 해야 합니다.

### <a name="connect-to-your-device"></a>장치에 연결
* 장치에 연결 하려면 먼저 장치의 IP 주소를 가져와야 합니다.  Windows IoT Core 장치를 부팅 한 후 장치에 연결 된 화면에 IP 주소를 표시 합니다.

    ![Windows IoT Core의 DefaultApp](../media/SSH/DefaultApp.png)

* 이제 PuTTY을 시작 하 고 `Host Name` 텍스트 상자에 IP 주소를 입력 한 다음 `SSH` 라디오 단추가 선택 되어 있는지 확인 합니다.  그런 다음 `Open`를 클릭 합니다.

    ![PuTTY 구성](../media/SSH/putty_config.png)

* 컴퓨터에서 처음으로 장치에 연결 하는 경우 다음과 같은 보안 경고가 표시 될 수 있습니다.  `Yes`를 클릭 하 여 계속 합니다.

    ![PuTTY 보안 경고](../media/SSH/putty_security_prompt.png)

* 성공적으로 연결 되 면 화면에 `login as:` 하 여 로그인 하 라는 메시지가 표시 됩니다.  
    `Administrator`를 입력 하 고 enter 키를 누릅니다.  그런 다음 암호 `p@ssw0rd` 기본 암호를 입력 하 고 enter 키를 누릅니다.

    ![PuTTY 로그인](../media/SSH/putty_login.png)

    성공적으로 로그인 할 수 있는 경우 다음과 같은 내용이 표시 됩니다.

    ![PuTTY 콘솔](../media/ssh/putty_console.png)

### <a name="update-account-password"></a>계정 암호 업데이트

관리자 계정에 대 한 기본 암호를 업데이트 하는 것이 **좋습니다** .

이렇게 하려면 PuTTY 콘솔에 다음 명령을 입력 하 고 `[new password]`를 강력한 암호로 바꿉니다.
    
    net user Administrator [new password]
    
### <a name="configure-your-windows-iot-core-device"></a>Windows IoT 핵심 장치 구성
* Visual Studio 2017에서 응용 프로그램을 배포할 수 있으려면 Visual Studio 원격 디버거 Windows IoT Core 장치에서 실행 되 고 있는지 확인 해야 합니다. 원격 디버거는 컴퓨터 부팅 시 자동으로 시작 됩니다. 두 번 확인 하려면 tlist.exe 명령을 사용 하 여 powershell에서 실행 중인 모든 프로세스를 나열 합니다. 장치에서 실행 되는 두 개의 msvsmon.exe 인스턴스가 있어야 합니다.

* 장시간의 비활성 시간이 지난 후에도 Visual Studio 원격 디버거 시간이 초과 될 수 있습니다. Visual Studio에서 Windows IoT Core 장치에 연결할 수 없는 경우 장치를 다시 부팅 합니다.

* 원하는 경우 장치 이름을 바꿀 수도 있습니다. ' 컴퓨터 이름 '을 변경 하려면 `setcomputername` 유틸리티를 사용 합니다.

        setcomputername <new-name>

    변경 내용을 적용 하려면 장치를 다시 부팅 해야 합니다. 다음과 같이 `shutdown` 명령을 사용할 수 있습니다.

        shutdown /r /t 0
        
### <a name="commonly-used-utilities"></a>일반적으로 사용 되는 유틸리티

SSH에서 사용할 수 있는 명령 및 유틸리티 목록은 [명령줄 유틸리티](../manage-your-device/CommandLineUtils.md) 페이지를 참조 하세요.
