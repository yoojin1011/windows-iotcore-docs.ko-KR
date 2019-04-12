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
# <a name="secure-shell-ssh"></a><span data-ttu-id="6cb66-104">SSH (보안 셸)</span><span class="sxs-lookup"><span data-stu-id="6cb66-104">Secure Shell (SSH)</span></span>
<span data-ttu-id="6cb66-105">보안 셸 (SSH)를 사용 하면 원격으로 관리 및 Windows IoT Core 장치를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6cb66-105">Secure Shell (SSH) allows you to remotely administer and configure your Windows IoT Core device</span></span>

## <a name="using-the-windows-10-openssh-client"></a><span data-ttu-id="6cb66-106">Windows 10 OpenSSH 클라이언트를 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="6cb66-106">Using the Windows 10 OpenSSH client</span></span>
> [!IMPORTANT]
> <span data-ttu-id="6cb66-107">클라이언트 Windows OpenSSH SSH 클라이언트 호스트 OS는 Windows 10 버전 1803(17134) 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="6cb66-107">The Windows OpenSSH client requires that your SSH client host OS is Windows 10 version 1803(17134).</span></span> <span data-ttu-id="6cb66-108">또한 Windows 10 IoT Core 장치 실행 되어야 합니다 RS5 Windows Insider Preview 릴리스 17723 이상.</span><span class="sxs-lookup"><span data-stu-id="6cb66-108">Also, the Windows 10 IoT Core device must be running RS5 Windows Insider Preview release 17723 or greater.</span></span>

<span data-ttu-id="6cb66-109">합니다 **OpenSSH 클라이언트** 선택적 기능으로 1803 (빌드 17134)에서 Windows 10에 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="6cb66-109">The **OpenSSH Client** was added to Windows 10 in 1803 (build 17134) as an optional feature.</span></span> <span data-ttu-id="6cb66-110">검색할 수 있습니다 클라이언트를 설치 하려면 **선택적 기능 관리** Windows 10 설정에서 합니다.</span><span class="sxs-lookup"><span data-stu-id="6cb66-110">To install the client you can search for **Manage Optional Features** in Windows 10 settings.</span></span> <span data-ttu-id="6cb66-111">경우는 **OpenSSH 클라이언트가** 선택한 설치 된 기능 목록에 나열 되지 **기능을 추가할**합니다.</span><span class="sxs-lookup"><span data-stu-id="6cb66-111">If the **OpenSSH Client** is not listed in the list of installed features then choose **Add a feature**.</span></span>

![기능 추가](../media/SSH/add_a_feature.png)

<span data-ttu-id="6cb66-113">다음 선택 **OpenSSH 클라이언트가** 목록에서 클릭 **설치**합니다.</span><span class="sxs-lookup"><span data-stu-id="6cb66-113">Next select **OpenSSH Client** in the list and click **Install**.</span></span>

![OpenSSH 클라이언트 설치](../media/SSH/optional_features.png)

<span data-ttu-id="6cb66-115">다음 명령을 사용 하는 사용자 이름 및 암호 로그인:</span><span class="sxs-lookup"><span data-stu-id="6cb66-115">To login with a username and password use the following command:</span></span>

```cmd
ssh administrator@host
```

<span data-ttu-id="6cb66-116">여기서 호스트는 Windows IoT Core 장치 IP 주소 또는 장치 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="6cb66-116">Where host is either the IP address of the Windows IoT Core device or the device name.</span></span>

<span data-ttu-id="6cb66-117">처음 연결 하면 다음과 같은 메시지가 표시:</span><span class="sxs-lookup"><span data-stu-id="6cb66-117">The first time you connect you see a message like the following:</span></span>

```cmd
The authenticity of host 'hostname (192.168.0.12)' can't be established.
ECDSA key fingerprint is SHA256:RahZpBFpecRiPmw8NGSa+7VKs8mgqQi/j2i1Qr9lUNU.
Are you sure you want to continue connecting (yes/no)?
```

<span data-ttu-id="6cb66-118">형식 **yes** 누릅니다 **입력**합니다.</span><span class="sxs-lookup"><span data-stu-id="6cb66-118">Type **yes** and press **enter**.</span></span>

<span data-ttu-id="6cb66-119">으로 로그인 해야 할 경우 **DefaultAccount** 대신 관리자로 해야 키를 생성 하 고 키를 사용 하 여 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="6cb66-119">If you need to log in as **DefaultAccount** rather than as administrator you will need to generate a key and use the key to log in.</span></span>  <span data-ttu-id="6cb66-120">IoT 장치에 연결 하려는 데스크톱에서 powershell 창을 열고 개인 데이터 폴더로 변경 (예: cd ~)</span><span class="sxs-lookup"><span data-stu-id="6cb66-120">From the desktop that you intend to connect to your IoT Device from, open a powershell window and change to your personal data folder (e.g cd ~)</span></span>

```cmd
cd ~
ssh-keygen -t rsa -f id_rsa
```

<span data-ttu-id="6cb66-121">Ssh 에이전트 (선택 사항, single sign-on 환경을)를 사용 하 여 키를 등록 합니다.</span><span class="sxs-lookup"><span data-stu-id="6cb66-121">Register the key with ssh-agent (optional, for single sign-on experience).</span></span>  <span data-ttu-id="6cb66-122">Ssh-추가 로그인으로 ACL에 처리 됩니다 하는 폴더에서 수행 해야 사용자 (Builtin\Administrators NT_AUTHORITY\System 사용자와도 확인).</span><span class="sxs-lookup"><span data-stu-id="6cb66-122">Note that ssh-add must be performed from a folder that is  ACL'd to you as the signed-in user (Builtin\Administrators and the NT_AUTHORITY\System user are also ok).</span></span>  <span data-ttu-id="6cb66-123">기본 cd에서 ~ powershell에서 충분 해야 아래와 같이 합니다.</span><span class="sxs-lookup"><span data-stu-id="6cb66-123">By default cd ~ from powershell should be sufficient as shown below.</span></span>

```cmd
cd ~
net start ssh-agent
ssh-add id_rsa
```

> [!TIP]
> <span data-ttu-id="6cb66-124">Ssh 에이전트 서비스는 사용 하지 않도록 하는 메시지가 표시 되 면 사용 하 여 설정할 수 있습니다. **sc.exe의 config ssh 에이전트 시작 = auto**</span><span class="sxs-lookup"><span data-stu-id="6cb66-124">If you receive a message that the ssh-agent service is disabled you can enable it with **sc.exe config ssh-agent start=auto**</span></span>

<span data-ttu-id="6cb66-125">사용 하도록 설정 하려면 single Windows IoT Core 장치에 공개 키를 추가 **authorized_keys** 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="6cb66-125">To enable single sign append the public key to the Windows IoT Core device **authorized_keys** file.</span></span>  <span data-ttu-id="6cb66-126">하나만 있는 경우 키 복사한 공개 키 파일을 원격으로 또는 **authorized_keys** 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="6cb66-126">Or if you only have one key you copy the public key file to the remote **authorized_keys** file.</span></span>

```cmd
net use X: \\host\c$ /user:host\administrator
if not exist x:\data\users\defaultaccount\.ssh md x:\data\users\defaultaccount\.ssh
copy .\id_rsa.pub x:\data\users\defaultaccount\.ssh\authorized_keys
```

<span data-ttu-id="6cb66-127">Ssh 에이전트를 사용 하 여 키를 등록 하지 않은 경우 로그인 하려면 명령줄에 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6cb66-127">If the key is not registered with ssh-agent it must be specified on the command line to login:</span></span> 

```cmd
ssh -i .\id_rsa DefaultAccount@host
```

<span data-ttu-id="6cb66-128">Ssh 에이전트를 사용 하 여 개인 키가 등록 하는 경우 지정 해야 <strong>DefaultAccount@host</strong>:</span><span class="sxs-lookup"><span data-stu-id="6cb66-128">If the private key is registered with ssh-agent then you only need to specify <strong>DefaultAccount@host</strong>:</span></span>

```cmd
ssh DefaultAccount@host
```

<span data-ttu-id="6cb66-129">처음 연결 하면 다음과 같은 메시지가 표시:</span><span class="sxs-lookup"><span data-stu-id="6cb66-129">The first time you connect you see a message like the following:</span></span>

```cmd
The authenticity of host 'hostname (192.168.0.12)' can't be established.
ECDSA key fingerprint is SHA256:RahZpBFpecRiPmw8NGSa+7VKs8mgqQi/j2i1Qr9lUNU.
Are you sure you want to continue connecting (yes/no)?
```

<span data-ttu-id="6cb66-130">형식 **yes** 누릅니다 **입력**합니다.</span><span class="sxs-lookup"><span data-stu-id="6cb66-130">Type **yes** and press **enter**.</span></span>

<span data-ttu-id="6cb66-131">하면 이제 연결로 **DefaultAccount**</span><span class="sxs-lookup"><span data-stu-id="6cb66-131">You should now be connected as **DefaultAccount**</span></span>

<span data-ttu-id="6cb66-132">Single sign-on을 사용 하 여 **관리자** 계정, Windows IoT Core 장치에서 c:\data\ProgramData\ssh\administrators_authorized_keys에 공개 키를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="6cb66-132">To use single sign-on with the **administrator** account, append your public key to c:\data\ProgramData\ssh\administrators_authorized_keys on the Windows IoT Core device.</span></span> 

```cmd
net use X: \\host\c$ /user:host\administrator
copy .\id_rsa.pub x:\data\ProgramData\ssh\administrators_authorized_keys
icacls x:\data\ProgramData\ssh\administrators_authorized_keys /remove "NT AUTHORITY\Authenticated Users"
icaclsx:\data\ProgramData\ssh\administrators_authorized_keys /inheritance:r
```

<span data-ttu-id="6cb66-133">또한 동일한 디렉터리에 ssh_host_dsa_key의 ACL에 맞게 administrators_authorized_keys에 대 한 ACL을 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6cb66-133">You will also need to set the ACL for administrators_authorized_keys to match the ACL of ssh_host_dsa_key in the same directory.</span></span>

```cmd
icacls x:\data\ProgramData\ssh\administrators_authorized_keys /remove "NT AUTHORITY\Authenticated Users"
icacls x:\data\ProgramData\ssh\administrators_authorized_keys /inheritance:r
```

<span data-ttu-id="6cb66-134">Powershell을 사용 하 여 ACL을 설정 하려면</span><span class="sxs-lookup"><span data-stu-id="6cb66-134">To set the ACL using powershell</span></span>

```cmd
get-acl x:\data\ProgramData\ssh\ssh_host_dsa_key | set-acl x:\data\ProgramData\ssh\administrators_authorized_keys
```

> [!NOTE]
> <span data-ttu-id="6cb66-135">표시 되 면을 **원격 호스트가 식별 변경** Windows 10 IoT Core 장치에 변경을 수행한 후 메시지를 편집 C:\Users\<사용자 이름 >\.ssh\known_hosts 및 변경 된 호스트를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="6cb66-135">If you see a **REMOTE HOST IDENTIFICATION CHANGED** message after making changes to the Windows 10 IoT Core device, then edit C:\Users\<username>\.ssh\known_hosts and remove the host that has changed.</span></span>

<span data-ttu-id="6cb66-136">참고 항목: [Win32-OpenSSH](https://github.com/PowerShell/Win32-OpenSSH/wiki/ssh.exe-examples)</span><span class="sxs-lookup"><span data-stu-id="6cb66-136">See also: [Win32-OpenSSH](https://github.com/PowerShell/Win32-OpenSSH/wiki/ssh.exe-examples)</span></span>

## <a name="using-putty"></a><span data-ttu-id="6cb66-137">PuTTY를 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="6cb66-137">Using PuTTY</span></span>

### <a name="download-a-ssh-client"></a><span data-ttu-id="6cb66-138">SSH 클라이언트를 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="6cb66-138">Download a SSH client</span></span>
<span data-ttu-id="6cb66-139">SSH를 사용 하 여 장치에 연결 하려면 먼저 해야와 같은 SSH 클라이언트를 다운로드 [PuTTY](http://the.earth.li/~sgtatham/putty/latest/x86/putty.exe)합니다.</span><span class="sxs-lookup"><span data-stu-id="6cb66-139">In order to connect to your device using SSH, you'll first need to download a SSH client, such as [PuTTY](http://the.earth.li/~sgtatham/putty/latest/x86/putty.exe).</span></span>

### <a name="connect-to-your-device"></a><span data-ttu-id="6cb66-140">장치에 연결</span><span class="sxs-lookup"><span data-stu-id="6cb66-140">Connect to your device</span></span>
* <span data-ttu-id="6cb66-141">장치에 연결 하려면 먼저 장치의 IP 주소를 가져올 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6cb66-141">In order to connect to your device, you need to first get the IP address of the device.</span></span>  <span data-ttu-id="6cb66-142">Windows IoT Core 장치를 부팅 한 후 IP 주소는 장치에 연결 화면에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6cb66-142">After booting your Windows IoT Core device, an IP address will be shown on the screen attached to the device:</span></span>

    ![Windows IoT Core에 DefaultApp](../media/SSH/DefaultApp.png)

* <span data-ttu-id="6cb66-144">이제 PuTTY를 시작 하 고 IP 주소를 입력 합니다 `Host Name` 있는지 확인 하 고 텍스트 상자를 `SSH` 라디오 단추를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="6cb66-144">Now launch PuTTY and enter the IP address in the `Host Name` text box and make sure the `SSH` radio button is selected.</span></span>  <span data-ttu-id="6cb66-145">클릭 `Open`합니다.</span><span class="sxs-lookup"><span data-stu-id="6cb66-145">Then click `Open`.</span></span>

    ![PuTTY 구성](../media/SSH/putty_config.png)

* <span data-ttu-id="6cb66-147">컴퓨터에서 처음으로 장치에 연결 하는 않으려면, 다음과 같은 보안 경고가 표시 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6cb66-147">If you're connecting to your device for the first time from your computer, you may see the following security alert.</span></span>  <span data-ttu-id="6cb66-148">클릭 `Yes` 를 계속 합니다.</span><span class="sxs-lookup"><span data-stu-id="6cb66-148">Just click `Yes` to continue.</span></span>

    ![PuTTY 보안 경고](../media/SSH/putty_security_prompt.png)

* <span data-ttu-id="6cb66-150">연결이 성공적으로 수행 되었으면 표시 `login as:` 화면에서 로그인 하 라는 합니다.</span><span class="sxs-lookup"><span data-stu-id="6cb66-150">If the connection was successful, you should see `login as:` on the screen, prompting you to login.</span></span>  
    <span data-ttu-id="6cb66-151">입력 `Administrator` 및 enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="6cb66-151">Enter `Administrator` and press enter.</span></span>  <span data-ttu-id="6cb66-152">기본 암호를 입력 한 다음 `p@ssw0rd` 누릅니다 암호를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="6cb66-152">Then enter the default password `p@ssw0rd` as the password and press enter.</span></span>

    ![PuTTY 로그인](../media/SSH/putty_login.png)

    <span data-ttu-id="6cb66-154">성공적으로 로그인 할 경우 다음과 같이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6cb66-154">If you were able to login successfully, you should see something like this:</span></span>

    ![PuTTY 콘솔](../media/ssh/putty_console.png)

### <a name="update-account-password"></a><span data-ttu-id="6cb66-156">계정 암호 업데이트</span><span class="sxs-lookup"><span data-stu-id="6cb66-156">Update account password</span></span>

<span data-ttu-id="6cb66-157">것 **좋습니다** 관리자 계정에 대 한 기본 암호를 업데이트 하는 합니다.</span><span class="sxs-lookup"><span data-stu-id="6cb66-157">It is **highly recommended** that you update the default password for the Administrator account.</span></span>

<span data-ttu-id="6cb66-158">이렇게 하려면 PuTTY 콘솔에서 다음 명령을 입력 바꾸기 `[new password]` 강력한 암호를 사용 하 여:</span><span class="sxs-lookup"><span data-stu-id="6cb66-158">To do this, enter the following command in the PuTTY console, replacing `[new password]` with a strong password:</span></span>
    
    net user Administrator [new password]
    
### <a name="configure-your-windows-iot-core-device"></a><span data-ttu-id="6cb66-159">Windows IoT Core 장치 구성</span><span class="sxs-lookup"><span data-stu-id="6cb66-159">Configure your Windows IoT Core device</span></span>
* <span data-ttu-id="6cb66-160">Visual Studio 2017에서 응용 프로그램을 배포 하는 일을 할 일에 Visual Studio 원격 디버거를 Windows IoT Core 장치에서 실행 되 고 있는지 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6cb66-160">To be able to deploy applications from Visual Studio 2017, you will need to make sure the Visual Studio Remote Debugger is running on your Windows IoT Core device.</span></span> <span data-ttu-id="6cb66-161">원격 디버거는 컴퓨터 부팅 시 자동으로 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6cb66-161">The remote debugger should launch automatically at machine boot time.</span></span> <span data-ttu-id="6cb66-162">이중을 확인 하려면 tlist 명령을 사용 하 여 powershell에서 실행 중인 모든 프로세스를 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="6cb66-162">To double check, use the tlist command to list all the running processes from powershell.</span></span> <span data-ttu-id="6cb66-163">장치에서 실행 되는 msvsmon.exe의 두 인스턴스가 없어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6cb66-163">There should be two instances of msvsmon.exe running on the device.</span></span>

* <span data-ttu-id="6cb66-164">있기 시간 제한 초과로 Visual Studio 원격 디버거를 오랜 기간 전까지 비활성 시간 후 합니다.</span><span class="sxs-lookup"><span data-stu-id="6cb66-164">It is possible for the Visual Studio Remote Debugger to time out after long periods of inactivity.</span></span> <span data-ttu-id="6cb66-165">Visual Studio Windows IoT Core 장치에 연결할 수 없는 경우, 장치 다시 부팅 하십시오.</span><span class="sxs-lookup"><span data-stu-id="6cb66-165">If Visual Studio cannot connect to your Windows IoT Core device, try rebooting the device.</span></span>

* <span data-ttu-id="6cb66-166">원한다 면 장치를 이름을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6cb66-166">If you want, you can also rename your device.</span></span> <span data-ttu-id="6cb66-167">'컴퓨터 이름'를 변경 하려면 사용 된 `setcomputername` 유틸리티.</span><span class="sxs-lookup"><span data-stu-id="6cb66-167">To change the 'computer name', use the `setcomputername` utility:</span></span>

        setcomputername <new-name>

    <span data-ttu-id="6cb66-168">변경 내용을 적용 하려면 장치를 다시 부팅 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6cb66-168">You will need to reboot the device for the change to take effect.</span></span> <span data-ttu-id="6cb66-169">사용할 수는 `shutdown` 다음과 같이 명령:</span><span class="sxs-lookup"><span data-stu-id="6cb66-169">You can use the `shutdown` command as follows:</span></span>

        shutdown /r /t 0
        
### <a name="commonly-used-utilities"></a><span data-ttu-id="6cb66-170">유틸리티를 사용 하는 일반적으로</span><span class="sxs-lookup"><span data-stu-id="6cb66-170">Commonly used utilities</span></span>

<span data-ttu-id="6cb66-171">참조를 [명령줄 유틸리티](../manage-your-device/CommandLineUtils.md) 페이지 목록은 명령 및 유틸리티 SSH와 함께 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6cb66-171">See the [Command Line Utils](../manage-your-device/CommandLineUtils.md) page for a list of commands and utilities you can use with SSH.</span></span>
