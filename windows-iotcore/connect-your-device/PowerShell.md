---
title: Windows IoT 용 PowerShell 사용
author: paulmon
ms.author: paulmon
ms.date: 08/28/2017
ms.topic: article
description: PowerShell을 사용 하 여 장치에 연결 하 고 장치를 관리 하는 방법을 알아봅니다.
keywords: windows iot, PowerShell, Windows PowerShell, 명령줄, 명령줄 셸
ms.openlocfilehash: fb8ec04365e330c2466c1287b446a5d3b15729a1
ms.sourcegitcommit: ea060254f9c4c25afcd0245c897b9e1425321859
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75721588"
---
# <a name="using-powershell-for-windows-iot"></a><span data-ttu-id="c0675-104">Windows IoT 용 PowerShell 사용</span><span class="sxs-lookup"><span data-stu-id="c0675-104">Using PowerShell for Windows IoT</span></span>

<span data-ttu-id="c0675-105">Windows PowerShell을 사용 하 여 Windows 10 IoT Core 장치를 원격으로 구성 하 고 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0675-105">Remotely configure and manage any Windows 10 IoT Core device by using Windows PowerShell.</span></span>
<span data-ttu-id="c0675-106">PowerShell은 시스템 관리를 위해 특별히 설계 된 작업 기반 명령줄 셸 및 스크립트 언어입니다.</span><span class="sxs-lookup"><span data-stu-id="c0675-106">PowerShell is a task-based command-line shell and scripting language, designed especially for system administration.</span></span>

<span data-ttu-id="c0675-107">Visual Studio 2017에서 잘 작동 하도록 Windows 10 IoT Core를 실행 하는 장치를 올바르게 구성 하려면 다음 단계를 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0675-107">Make sure to follow these steps to correctly configure your device running Windows 10 IoT Core to work well with Visual Studio 2017.</span></span>

## <a name="initiating-a-powershell-session"></a><span data-ttu-id="c0675-108">PowerShell 세션 시작</span><span class="sxs-lookup"><span data-stu-id="c0675-108">Initiating a PowerShell session</span></span>
1. <span data-ttu-id="c0675-109">Windows 10 IoT Core 장치를 사용 하 여 PowerShell 세션을 시작 하려면 먼저 호스트 PC와 장치 간에 트러스트 관계를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0675-109">To start a PowerShell session with your Windows 10 IoT Core device, you'll first need to create a trust relationship between your host PC and your device.</span></span> <span data-ttu-id="c0675-110">Windows IoT Core 장치를 시작한 후에는 장치에 연결 된 화면에 IP 주소가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0675-110">After starting your Windows IoT Core device, an IP address will be shown on the screen attached to the device.</span></span>

    ![Windows 10 IoT Core의 DefaultApp](../media/PowerShell/DefaultApp.png)

   <span data-ttu-id="c0675-112">Windows 10 IoT Core 대시보드에서 동일한 정보를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0675-112">You can find the same information on the Windows 10 IoT Core Dashboard.</span></span>

2. <span data-ttu-id="c0675-113">로컬 PC에서 관리자 PowerShell 콘솔을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="c0675-113">Open an administrator PowerShell console on your local PC.</span></span> <span data-ttu-id="c0675-114">Windows 시작 메뉴 근처에서 **웹 및 Windows 검색** 상자에 **powershell** 을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0675-114">Type **powershell** in the **Search the web and Windows** box near the Windows Start menu.</span></span> <span data-ttu-id="c0675-115">Windows는 PC에서 PowerShell을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="c0675-115">Windows will find PowerShell on your PC.</span></span>

    ![PowerShell 찾기](../media/PowerShell/start-ps.png)

3. <span data-ttu-id="c0675-117">관리자 권한으로 PowerShell을 시작 하려면 **Windows powershell**을 마우스 오른쪽 단추로 클릭 한 다음 **관리자 권한으로 실행**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0675-117">To start PowerShell as an administrator, right-click **Windows PowerShell**, and then select **Run as administrator**.</span></span>

    ![관리자 권한으로 PowerShell을 실행합니다.](../media/PowerShell/start-ps2.png)

   <span data-ttu-id="c0675-119">이제 PowerShell 콘솔이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0675-119">Now you should see the PowerShell console.</span></span>

    ![PowerShell 콘솔](../media/PowerShell/ps.PNG)

4. <span data-ttu-id="c0675-121">원격 연결을 사용 하도록 설정 하려면 바탕 화면에서 WinRM 서비스를 시작 해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0675-121">You may need to start the WinRM service on your desktop to enable remote connections.</span></span> <span data-ttu-id="c0675-122">이렇게 하려면 PowerShell 콘솔에서 다음 명령을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0675-122">To do so, from the PowerShell console, type the following command:</span></span>

        net start WinRM

5. <span data-ttu-id="c0675-123">PowerShell 콘솔에서 다음을 입력 합니다 .이 값을 적절 한 값으로 `<machine-name or IP address>` 대체 합니다. 즉, **컴퓨터 이름을** 사용 하는 것이 가장 쉽지만 네트워크에서 장치를 고유 하 게 이름 지정 하지 않은 경우 IP 주소를 사용해 보세요.</span><span class="sxs-lookup"><span data-stu-id="c0675-123">From the PowerShell console, type the following, substituting `<machine-name or IP address>` with the appropriate value (using your **machine-name** is the easiest, but if your device is not uniquely named on your network, try the IP address):</span></span>

        Set-Item WSMan:\localhost\Client\TrustedHosts -Value <machine-name or IP Address>

6. <span data-ttu-id="c0675-124">`Y`를 입력 하 여 변경 내용을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0675-124">Enter `Y` to confirm the change.</span></span>

> [!NOTE]
> <span data-ttu-id="c0675-125">여러 장치를 연결 하려는 경우 쉼표와 따옴표를 사용 하 여 각 장치를 구분할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0675-125">If you want to connect multiple devices, you can use commas and quotation marks to separate each device.</span></span>
        
        Set-Item WSMan:\localhost\Client\TrustedHosts -Value "<machine1-name or IP Address>,<machine2-name or IP Address>"
    
7. <span data-ttu-id="c0675-126">이제 Windows IoT Core 장치를 사용 하 여 세션을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0675-126">Now you can start a session with your Windows IoT Core device.</span></span> <span data-ttu-id="c0675-127">관리자 PowerShell 콘솔에서 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0675-127">From you administrator PowerShell console, type:</span></span>

        Enter-PSSession -ComputerName <machine-name or IP Address> -Credential <machine-name or IP Address or localhost>\Administrator

8. <span data-ttu-id="c0675-128">자격 증명 대화 상자에서 다음과 같은 기본 암호를 입력 합니다. `p@ssw0rd`</span><span class="sxs-lookup"><span data-stu-id="c0675-128">In the credential dialog, enter the following default password: `p@ssw0rd`</span></span>
    
    <div class="alert alert-note">
      <h5><span data-ttu-id="c0675-129"><span class="win-icon win-icon-Page"></span>두고</span><span class="sxs-lookup"><span data-stu-id="c0675-129"><span class="win-icon win-icon-Page"></span> NOTE</span></span> </h5>
      <p><span data-ttu-id="c0675-130">연결 프로세스는 즉시 수행 되지 않으며 최대 30 초까지 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0675-130">The connection process is not immediate and can take up to 30 seconds.</span></span></p>
    </div>    
    
    <span data-ttu-id="c0675-131">장치에 성공적으로 연결한 경우 프롬프트 전에 장치의 IP 주소가 표시 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0675-131">If you successfully connected to the device, you should see the IP address of your device before the prompt.</span></span>

    ![PowerShell 콘솔](../media/PowerShell/ps_device.png)

9. <span data-ttu-id="c0675-133">계정 암호를 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0675-133">Update your account password.</span></span> <span data-ttu-id="c0675-134">관리자 계정에 대 한 기본 암호를 업데이트 하는 것 *이 좋습니다* .</span><span class="sxs-lookup"><span data-stu-id="c0675-134">We *highly recommend* that you update the default password for the Administrator account.</span></span> <span data-ttu-id="c0675-135">이렇게 하려면 PowerShell 연결에서 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0675-135">To do this, issue the following commands in your PowerShell connection:</span></span>

    <span data-ttu-id="c0675-136">a.</span><span class="sxs-lookup"><span data-stu-id="c0675-136">a.</span></span> <span data-ttu-id="c0675-137">`[new password]`를 강력한 암호로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="c0675-137">Replace `[new password]` with a strong password:</span></span>
    
            net user Administrator [new password]
            
    <span data-ttu-id="c0675-138">b.</span><span class="sxs-lookup"><span data-stu-id="c0675-138">b.</span></span> <span data-ttu-id="c0675-139">그런 다음 `Exit-PSSession`를 사용 하 여 새 PowerShell 세션을 설정 하 고 새 자격 증명을 사용 하 여 `Enter-PSSession` 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0675-139">Next, establish a new PowerShell session using `Exit-PSSession` and `Enter-PSSession` with the new credentials.</span></span>
    
            Exit-PSSession
            
            Enter-PSSession -ComputerName <machine-name or IP Address> -Credential <machine-name or IP Address or localhost>\Administrator

## <a name="commonly-used-powershell-commands"></a><span data-ttu-id="c0675-140">일반적으로 사용 되는 PowerShell 명령</span><span class="sxs-lookup"><span data-stu-id="c0675-140">Commonly used PowerShell commands</span></span>

### <a name="troubleshooting-with-visual-studio-remote-debugger"></a><span data-ttu-id="c0675-141">Visual Studio 원격 디버거 문제 해결</span><span class="sxs-lookup"><span data-stu-id="c0675-141">Troubleshooting with Visual Studio Remote Debugger</span></span>

<span data-ttu-id="c0675-142">Visual Studio 2017에서 응용 프로그램을 배포할 수 있으려면 Visual Studio 원격 디버거 Windows IoT Core 장치에서 실행 되 고 있는지 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0675-142">To be able to deploy applications from Visual Studio 2017, you will need to make sure that the Visual Studio Remote Debugger is running on your Windows IoT Core device.</span></span> <span data-ttu-id="c0675-143">원격 디버거는 컴퓨터를 시작할 때 자동으로 열립니다.</span><span class="sxs-lookup"><span data-stu-id="c0675-143">The remote debugger should open automatically when you start your computer.</span></span> <span data-ttu-id="c0675-144">두 번 확인 하려면 `tlist` 명령을 사용 하 여 PowerShell에서 실행 중인 모든 프로세스를 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0675-144">To double check, use the `tlist` command to list all the running processes from PowerShell.</span></span> <span data-ttu-id="c0675-145">장치에서 실행 되는 두 개의 msvsmon.exe 인스턴스가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0675-145">There should be two instances of msvsmon.exe running on the device.</span></span>

<span data-ttu-id="c0675-146">장시간의 비활성 시간이 지난 후에도 Visual Studio 원격 디버거 시간이 초과 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0675-146">It is possible for the Visual Studio Remote Debugger to time out after long periods of inactivity.</span></span> <span data-ttu-id="c0675-147">Visual Studio에서 Windows IoT Core 장치에 연결할 수 없는 경우 장치를 다시 시작 해 보세요.</span><span class="sxs-lookup"><span data-stu-id="c0675-147">If Visual Studio cannot connect to your Windows IoT Core device, try restarting the device.</span></span>

### <a name="configure-your-windows-iot-core-device"></a><span data-ttu-id="c0675-148">Windows IoT 핵심 장치 구성</span><span class="sxs-lookup"><span data-stu-id="c0675-148">Configure your Windows IoT Core device</span></span>

<span data-ttu-id="c0675-149">원하는 경우 장치 이름을 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0675-149">If you want, you can rename your device.</span></span> 

1. <span data-ttu-id="c0675-150">컴퓨터 이름을 변경 하려면 `setcomputername` 유틸리티를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0675-150">To change the computer name, use the `setcomputername` utility:</span></span>

        setcomputername <new-name>

2. <span data-ttu-id="c0675-151">변경 내용을 적용 하려면 장치를 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0675-151">Restart the device for the change to take effect.</span></span> <span data-ttu-id="c0675-152">다음과 같이 `shutdown` 명령을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0675-152">You can use the `shutdown` command as follows:</span></span>

        shutdown /r /t 0

3. <span data-ttu-id="c0675-153">컴퓨터 이름이 변경 되었기 때문에를 다시 시작한 후에는 다음 명령을 다시 실행 하 여 새 이름을 사용 하 여 장치에 연결 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0675-153">Because the computer name was changed, after you restart you will need to rerun this command to connect to your device using the new name:</span></span>

        Set-Item WSMan:\localhost\Client\TrustedHosts -Value <new-name>
        
<span data-ttu-id="c0675-154">이제 Windows IoT 핵심 장치가 올바르게 구성 되어 사용할 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c0675-154">Your Windows IoT Core device should now be properly configured and ready to use!</span></span>

### <a name="commonly-used-utilities"></a><span data-ttu-id="c0675-155">일반적으로 사용 되는 유틸리티</span><span class="sxs-lookup"><span data-stu-id="c0675-155">Commonly used utilities</span></span>

<span data-ttu-id="c0675-156">PowerShell에서 사용할 수 있는 명령 및 유틸리티 목록은 [명령줄 유틸리티](../manage-your-device/CommandLineUtils.md) 페이지를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c0675-156">For a list of commands and utilities that you can use with PowerShell, see the [Command Line Utils](../manage-your-device/CommandLineUtils.md) page.</span></span>

## <a name="known-issues-and-workarounds"></a><span data-ttu-id="c0675-157">알려진 문제 및 해결 방법</span><span class="sxs-lookup"><span data-stu-id="c0675-157">Known issues and workarounds</span></span>

<span data-ttu-id="c0675-158">**문제**: PowerShell 보안 정책의 알려진 버그로 인해 원격 세션 내에서 다음과 같은 문제가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0675-158">**ISSUE**: A known bug in PowerShell security policies causes the following issues to manifest within the remote session:</span></span>
* <span data-ttu-id="c0675-159">Get-help는 예기치 않은 일치 항목을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0675-159">Get-Help returns unexpected matches.</span></span>
* <span data-ttu-id="c0675-160">지정 된 모듈의 Get 명령이 빈 명령 목록을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0675-160">Get-Command on a specified module returns an empty command list.</span></span>
* <span data-ttu-id="c0675-161">이러한 모듈에서 cmdlet을 실행 하면 CommandNotFoundException: Appx, Get-netadapter, NetSecurity, Netsecurity, Pnp 장치가 throw 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0675-161">Running a cmdlet from any of these modules throws CommandNotFoundException: Appx, NetAdapter, NetSecurity, NetTCPIP, PnpDevice.</span></span>
* <span data-ttu-id="c0675-162">위의 모듈에서 import-module은 UnauthorizedAccess를 사용 하 여 PSSecurityException 예외를 throw 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0675-162">Import-Module on any of the above modules throws PSSecurityException exception with UnauthorizedAccess.</span></span> <span data-ttu-id="c0675-163">모듈 자동 로딩이 작동 하지 않는 것 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c0675-163">Module auto loading does not seem to work either.</span></span>

<span data-ttu-id="c0675-164">**해결 방법**: 원격 PowerShell 세션 내에서 실행 정책을 **RemoteSigned**로 수정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0675-164">**Workaround**: Modify the execution policy within the remote PowerShell session to **RemoteSigned**.</span></span> <span data-ttu-id="c0675-165">다른 실행 정책에 대 한 자세한 내용은 [Set-executionpolicy Cmdlet 사용](https://technet.microsoft.com/library/ee176961.aspx)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c0675-165">For more details on the different execution policies, see [Using the Set-ExecutionPolicy Cmdlet](https://technet.microsoft.com/library/ee176961.aspx).</span></span>

<span data-ttu-id="c0675-166">**문제**: get-netadapter와 같은 일부 모듈의 cmdlet이 표시 되지 않는 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0675-166">**ISSUE**: Cmdlets from some modules such as NetAdapter are sometimes not visible.</span></span> <span data-ttu-id="c0675-167">예를 들어 Import-module Get-netadapter는 빈 목록을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0675-167">For example, Get-Module NetAdapter returns an empty list.</span></span> 

<span data-ttu-id="c0675-168">**해결 방법**: import-module에-Force 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0675-168">**Workaround**: Use the -Force parameter with Import-Module.</span></span> <span data-ttu-id="c0675-169">예를 들면 `Import-Module NetAdapter -Force`입니다.</span><span class="sxs-lookup"><span data-stu-id="c0675-169">For example, `Import-Module NetAdapter -Force`.</span></span>

<span data-ttu-id="c0675-170">**문제**: 실행 정책을 "AllSigned"로 설정 하면 PowerShell 원격이 중단 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0675-170">**ISSUE**: Setting execution policy to "AllSigned" breaks PowerShell remoting.</span></span> <span data-ttu-id="c0675-171">Typesv3. types.ps1xml를 로드 하는 SecurityException을 사용 하 여 원격 세션을 만드는 후속 시도가 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0675-171">Subsequent attempts to create a remote session fail with a SecurityException loading Typesv3.ps1xml.</span></span> 

<span data-ttu-id="c0675-172">**해결 방법**: Winrs.exe를 사용 하 여 PowerShell의 실행 정책을 복원 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0675-172">**Workaround**: Use winrs.exe to restore PowerShell's execution policy:</span></span>
* <span data-ttu-id="c0675-173">콘솔 코드 페이지 `Chcp 65001` 변경</span><span class="sxs-lookup"><span data-stu-id="c0675-173">Change console code page `Chcp 65001`</span></span>
* <span data-ttu-id="c0675-174">원격 cmd.exe 셸에 로그온 `Winrs.exe -r:<target> -u:<username> -p:<password> cmd.exe`</span><span class="sxs-lookup"><span data-stu-id="c0675-174">Log on to a remote cmd.exe shell `Winrs.exe -r:<target> -u:<username> -p:<password> cmd.exe`</span></span>
* <span data-ttu-id="c0675-175">원격 cmd.exe 내에서 적절 한 레지스트리 키를 수정 `reg add HKLM\Software\Microsoft\PowerShell\1\ShellIds\Microsoft.PowerShell /v ExecutionPolicy /d RemoteSigned /f`</span><span class="sxs-lookup"><span data-stu-id="c0675-175">Within remote cmd.exe, modify the appropriate registry key `reg add HKLM\Software\Microsoft\PowerShell\1\ShellIds\Microsoft.PowerShell /v ExecutionPolicy /d RemoteSigned /f`</span></span>
* <span data-ttu-id="c0675-176">원격 cmd.exe 세션 `exit`을 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0675-176">Exit remote cmd.exe session `exit`</span></span>

### <a name="other-known-issues"></a><span data-ttu-id="c0675-177">기타 알려진 문제</span><span class="sxs-lookup"><span data-stu-id="c0675-177">Other known issues</span></span>

- <span data-ttu-id="c0675-178">PowerShell 스크립트에서 PowerShell 클래스 또는 열거형에 대 한 특성은 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c0675-178">In PowerShell scripts, attributes to PowerShell class or enumeration do not work.</span></span> <span data-ttu-id="c0675-179">특성을 추가 하는 경우 throw 되는 예외는 다음과 같습니다. *형식이 런타임 형식 개체*여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0675-179">Adding attributed results in the following exception thrown: *Type must be a runtime Type object*.</span></span>

- <span data-ttu-id="c0675-180">아웃 바운드 CIM 및 PowerShell remoting은 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c0675-180">Outbound CIM and PowerShell remoting is not supported.</span></span> <span data-ttu-id="c0675-181">신뢰 cmdlet의 관련 기능은 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c0675-181">Relevant functionality in relying cmdlets will not work.</span></span> <span data-ttu-id="c0675-182">여기에는 입력 PSSession, 작업 가져오기, 수신 작업, Import-module, 호출 명령, 복사 항목이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0675-182">These include  Enter-PSSession, Get-Job, Receive-Job, Import-Module, Invoke-Command, and Copy-Item.</span></span>

- <span data-ttu-id="c0675-183">SecureString 명령이 Convertfrom-csv 및 Convertto-html는 CredSSP 인증을 사용 하 여 세션을 만들지 않으면 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c0675-183">SecureString commands ConvertFrom-SecureString and ConvertTo-SecureString do not work unless the session is created using CredSSP authentication.</span></span> <span data-ttu-id="c0675-184">그렇지 않으면-Key 매개 변수를 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0675-184">Otherwise, the -Key parameter must be specified.</span></span> <span data-ttu-id="c0675-185">CredSSP 인증 구성에 대 한 자세한 내용은 [credssp를 사용 하 여 PowerShell "두 번째 홉" 기능 사용](https://devblogs.microsoft.com/scripting/enable-powershell-second-hop-functionality-with-credssp/)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c0675-185">For details on configuring CredSSP authentication, see [Enable PowerShell “Second-Hop” Functionality with CredSSP](https://devblogs.microsoft.com/scripting/enable-powershell-second-hop-functionality-with-credssp/).</span></span>


