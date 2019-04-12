---
title: PowerShell을 사용 하 여 Windows IoT에 대 한
author: paulmon
ms.author: paulmon
ms.date: 08/28/2017
ms.topic: article
description: PowerShell을 사용 하 여 장치에 연결할 수 있을 뿐만 아니라 장치를 관리 하는 방법에 알아봅니다.
keywords: windows iot, PowerShell, Windows PowerShell, 명령줄 및 명령줄 셸입니다
ms.openlocfilehash: 1519fb9dd61a8d6521757fdd97999f03b74afa7d
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59515068"
---
# <a name="using-powershell-for-windows-iot"></a>PowerShell을 사용 하 여 Windows IoT에 대 한

원격으로 구성 하 고 Windows PowerShell을 사용 하 여 모든 Windows 10 IoT Core 장치를 관리 합니다.
PowerShell 작업 기반 명령줄 셸이자 스크립팅 언어, 시스템 관리를 위해 특별히 설계 된 경우

Visual Studio 2017에서 작동 하도록 Windows 10 IoT Core 실행 하는 장치를 올바르게 구성 하려면 다음이 단계를 수행 해야 합니다.

## <a name="initiating-a-powershell-session"></a>PowerShell 세션을 시작합니다.
1. Windows 10 IoT Core 장치를 사용 하 여 PowerShell 세션을 시작 하는 호스트 PC와 장치 간에 트러스트 관계를 만들려면 먼저 해야 합니다. Windows IoT Core 장치를 시작한 후 IP 주소는 장치에 연결 화면에 표시 됩니다.

    ![Windows 10 IoT Core DefaultApp](../media/PowerShell/DefaultApp.png)

   Windows 10 IoT Core 대시보드에 같은 정보를 찾을 수 있습니다.

2. 로컬 PC에서 관리자 권한 PowerShell 콘솔을 엽니다. 형식 **powershell** 에 **웹 및 Windows 검색** Windows 시작 메뉴에 있는 상자입니다. Windows PC에서 PowerShell을 찾을 수 있습니다.

    ![Powershell](../media/PowerShell/start-ps.png)

3. 관리자 권한으로 PowerShell을 시작 하려면 마우스 오른쪽 단추로 클릭 **Windows PowerShell**를 선택한 후 **관리자 권한으로 실행**합니다.

    ![관리자 권한으로 PowerShell을 실행 합니다.](../media/PowerShell/start-ps2.png)

   이제 PowerShell 콘솔에 표시 됩니다.

    ![PowerShell 콘솔](../media/PowerShell/ps.PNG)

4. 원격 연결을 사용 하도록 설정 하려면 바탕 화면에서 WinRM 서비스를 시작 해야 합니다. 이렇게 하려면, PowerShell 콘솔에서 다음 명령을 입력 합니다.

        net start WinRM

5. PowerShell 콘솔에서 다음을 입력으로 대체 `<machine-name or IP address>` 적절 한 값 (사용 하 여 프로그램 **컴퓨터 이름** 는 IP 주소를 네트워크에서 장치의 고유 하 게 하는 경우 이름이 지정 되지 않은 하지만 가장을 시도):

        Set-Item WSMan:\localhost\Client\TrustedHosts -Value <machine-name or IP Address>

6. 입력 `Y` 여 변경 내용을 확인 합니다.

> [!NOTE]
> 여러 장치를 연결 하려는 경우 각 장치를 구분 하려면 쉼표와 큰따옴표를 사용할 수 있습니다.
        
        Set-Item WSMan:\localhost\Client\TrustedHosts -Value "<machine1-name or IP Address>,<machine2-name or IP Address>"
    
7. 이제 Windows IoT Core 장치를 사용 하 여 세션을 시작할 수 있습니다. 사용자 관리자 PowerShell 콘솔에서 다음을 입력 합니다.

        Enter-PSSession -ComputerName <machine-name or IP Address> -Credential <machine-name or IP Address or localhost>\Administrator

8. 자격 증명 대화 상자에서 다음 기본 암호를 입력 합니다. `p@ssw0rd`
    
    <div class="alert alert-note">
      <h5><span class="win-icon win-icon-Page"></span> 참고 </h5>
      <p>연결 프로세스가 즉시 이며 30 초 정도 걸릴 수 있습니다.</p>
    </div>    
    
    장치에 성공적으로 연결 하는 경우 프롬프트 하기 전에 장치의 IP 주소를 표시 됩니다.

    ![PowerShell 콘솔](../media/PowerShell/ps_device.png)

9. 계정 암호를 업데이트 합니다. 우리 *것이 좋습니다* 관리자 계정에 대 한 기본 암호를 업데이트 합니다. 이렇게 하려면 PowerShell 연결에서 다음 명령을 실행 합니다.

    a. 대체 `[new password]` 강력한 암호를 사용 하 여:
    
            net user Administrator [new password]
            
    b. 다음으로 사용 하 여 새 PowerShell 세션을 설정할 `Exit-PSSession` 및 `Enter-PSSession` 새 자격 증명을 사용 합니다.
    
            Exit-PSSession
            
            Enter-PSSession -ComputerName <machine-name or IP Address> -Credential <machine-name or IP Address or localhost>\Administrator

## <a name="commonly-used-powershell-commands"></a>일반적으로 사용 하는 PowerShell 명령

### <a name="troubleshooting-with-visual-studio-remote-debugger"></a>Visual Studio 원격 디버거를 사용 하 여 문제 해결

Visual Studio 2017에서 응용 프로그램을 배포할 수 있는 Visual Studio 원격 디버거 Windows IoT Core 장치에서 실행 되 고 있는지 확인 해야 합니다. 컴퓨터를 시작할 때 원격 디버거가 자동으로 열립니다. 이중을 확인 하려면 사용 된 `tlist` PowerShell에서 실행 중인 모든를 나열 하는 명령 처리 합니다. 장치에서 실행 되는 msvsmon.exe의 두 인스턴스가 없어야 합니다.

있기 시간 제한 초과로 Visual Studio 원격 디버거를 오랜 기간 전까지 비활성 시간 후 합니다. Visual Studio Windows IoT Core 장치에 연결할 수 없는 경우 장치를 다시 시작 하십시오.

### <a name="configure-your-windows-iot-core-device"></a>Windows IoT Core 장치 구성

원한다 면 장치 이름을 바꿀 수 있습니다. 

1. 컴퓨터 이름을 변경 하려면 사용 된 `setcomputername` 유틸리티.

        setcomputername <new-name>

2. 변경 내용을 적용 하려면 장치를 다시 시작 합니다. 사용할 수는 `shutdown` 다음과 같이 명령:

        shutdown /r /t 0

3. 컴퓨터 이름 변경 되었으므로 사용자는를 다시 시작한 후 새 이름을 사용 하 여 장치에 연결 하려면이 명령을 다시 실행 해야 합니다.

        Set-Item WSMan:\localhost\Client\TrustedHosts -Value <new-name>
        
Windows IoT Core 장치 올바로 구성 되어 있고 사용할 준비가 됩니다!

### <a name="commonly-used-utilities"></a>유틸리티를 사용 하는 일반적으로

PowerShell을 사용 하 여 사용할 수 있는 유틸리티 및 명령 목록을 보려면 참조는 [명령줄 유틸리티](../manage-your-device/CommandLineUtils.md) 페이지입니다.

## <a name="known-issues-and-workarounds"></a>알려진 문제 및 해결 방법

**문제**: PowerShell 보안 정책에서 알려진된 버그로 인해 원격 세션 내에서 매니페스트를 다음과 같은 문제가 있습니다.
* Get-help 예기치 않은 일치 항목을 반환합니다.
* 지정된 된 모듈에서 Get-command는 비어 있는 명령 목록을 반환합니다.
* 이러한 모듈 중 하나에서 cmdlet을 실행 CommandNotFoundException throw 됩니다. Appx, NetAdapter, NetSecurity, NetTCPIP, PnpDevice.
* 위의 모듈은 Import-module 부분은 사용 하 여 PSSecurityException 예외를 throw합니다. 모듈 자동 로드 작동 하지 않는 것 같습니다.

**해결 방법**: 원격 PowerShell 세션 내에서 실행 정책을 수정 **RemoteSigned**합니다. 다른 실행 정책에 대 한 자세한 내용은 참조 하세요. [Set-executionpolicy Cmdlet을 사용 하 여](https://technet.microsoft.com/library/ee176961.aspx)입니다.

**문제**: NetAdapter 같은 일부 모듈의 Cmdlet 경우에 따라 표시 되지 않습니다. 예를 들어 Get-module NetAdapter 빈 목록을 반환 합니다. 

**해결 방법**: 사용 하 여 Import-module-Force 매개 변수입니다. `Import-Module NetAdapter -Force`) 을 입력합니다.

**문제**: PowerShell 원격 기능을 중단 "AllSigned"에 대 한 실행 정책을 설정 합니다. SecurityException Typesv3.ps1xml 로드를 사용 하 여 원격 세션을 만드는 후속 시도가 실패 합니다. 

**해결 방법**: PowerShell 실행 정책을 복원 하려면 winrs.exe를 사용 합니다.
* 변경 콘솔 코드 페이지 `Chcp 65001`
* 원격 cmd.exe 셸에 로그온 `Winrs.exe -r:<target> -u:<username> -p:<password> cmd.exe`
* 원격 cmd.exe 내에서 적절 한 레지스트리 키를 수정 합니다. `reg add HKLM\Software\Microsoft\PowerShell\1\ShellIds\Microsoft.PowerShell /v ExecutionPolicy /d RemoteSigned /f`
* Cmd.exe 원격 세션을 종료 `exit`

### <a name="other-known-issues"></a>기타 알려진된 문제

- PowerShell 스크립트에서 PowerShell 클래스 또는 열거형에는 특성 작동 하지 않습니다. 추가 결과 다음 예외가 throw 특성을 사용 합니다. *형식에는 런타임 형식 개체를 사용 해야 합니다.* 합니다.

- 아웃 바운드 CIM 및 PowerShell 원격을 사용 하는 것이 없습니다. 신뢰 cmdlet의 관련 기능을 작동 하지 않습니다. Enter-pssession Get-job을 Receive-job과, Import-module 다음과 Invoke-command, 및 Copy-item 합니다.

- Convertto-securestring 및 Convertfrom-securestring SecureString 명령을 CredSSP 인증을 사용 하 여 세션을 만들지 않으면 작동 하지 않습니다. 그렇지 않은 경우-키 매개 변수를 지정 해야 합니다. CredSSP 인증 구성에 대 한 세부 정보를 참조 하세요 ["이중 홉" 문제](http://blogs.msdn.com/b/clustering/archive/2009/06/25/9803001.aspx)합니다.


