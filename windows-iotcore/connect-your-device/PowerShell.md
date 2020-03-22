---
title: Windows IoT 용 PowerShell 사용
author: paulmon
ms.author: paulmon
ms.date: 08/28/2017
ms.topic: article
description: PowerShell을 사용 하 여 장치에 연결 하 고 장치를 관리 하는 방법을 알아봅니다.
keywords: windows iot, PowerShell, Windows PowerShell, 명령줄, 명령줄 셸
ms.openlocfilehash: f12fd88ee7c53937d92f163ae5acedc4197dbc8a
ms.sourcegitcommit: 9fb86fb605d6a8feb5c226a391045b908117a90a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80080574"
---
# <a name="using-powershell-for-windows-iot"></a>Windows IoT 용 PowerShell 사용

Windows PowerShell을 사용 하 여 Windows 10 IoT Core 장치를 원격으로 구성 하 고 관리 합니다.
PowerShell은 시스템 관리를 위해 특별히 설계 된 작업 기반 명령줄 셸 및 스크립트 언어입니다.

Visual Studio 2017에서 잘 작동 하도록 Windows 10 IoT Core를 실행 하는 장치를 올바르게 구성 하려면 다음 단계를 수행 해야 합니다.

## <a name="initiating-a-powershell-session"></a>PowerShell 세션 시작
1. Windows 10 IoT Core 장치를 사용 하 여 PowerShell 세션을 시작 하려면 먼저 호스트 PC와 장치 간에 트러스트 관계를 만들어야 합니다. Windows IoT Core 장치를 시작한 후에는 장치에 연결 된 화면에 IP 주소가 표시 됩니다.

    ![Windows 10 IoT Core의 DefaultApp](../media/PowerShell/DefaultApp.png)

   Windows 10 IoT Core 대시보드에서 동일한 정보를 찾을 수 있습니다.

2. 로컬 PC에서 관리자 PowerShell 콘솔을 엽니다. Windows 시작 메뉴 근처에서 **웹 및 Windows 검색** 상자에 **powershell** 을 입력 합니다. Windows는 PC에서 PowerShell을 찾습니다.

    ![PowerShell 찾기](../media/PowerShell/start-ps.png)

3. 관리자 권한으로 PowerShell을 시작 하려면 **Windows powershell**을 마우스 오른쪽 단추로 클릭 한 다음 **관리자 권한으로 실행**을 선택 합니다.

    ![관리자 권한으로 PowerShell 실행](../media/PowerShell/start-ps2.png)

   이제 PowerShell 콘솔이 표시 됩니다.

    ![PowerShell 콘솔](../media/PowerShell/ps.PNG)

4. 원격 연결을 사용 하도록 설정 하려면 바탕 화면에서 WinRM 서비스를 시작 해야 할 수 있습니다. 이렇게 하려면 PowerShell 콘솔에서 다음 명령을 입력 합니다.

        net start WinRM

5. PowerShell 콘솔에서 다음을 입력 합니다 .이 값을 적절 한 값으로 `<machine-name or IP address>` 대체 합니다. 즉, **컴퓨터 이름을** 사용 하는 것이 가장 쉽지만 네트워크에서 장치를 고유 하 게 이름 지정 하지 않은 경우 IP 주소를 사용해 보세요.

        Set-Item WSMan:\localhost\Client\TrustedHosts -Value <machine-name or IP Address>

6. `Y`를 입력 하 여 변경 내용을 확인 합니다.
        
        Set-Item WSMan:\localhost\Client\TrustedHosts -Value "<machine1-name or IP Address>,<machine2-name or IP Address>"
    
> [!NOTE]
> 여러 장치를 연결 하려는 경우 쉼표와 따옴표를 사용 하 여 각 장치를 구분할 수 있습니다.

7. 이제 Windows IoT Core 장치를 사용 하 여 세션을 시작할 수 있습니다. 관리자 PowerShell 콘솔에서 다음을 입력 합니다.

        Enter-PSSession -ComputerName <machine-name or IP Address> -Credential <machine-name or IP Address or localhost>\Administrator

8. 자격 증명 대화 상자에서 다음과 같은 기본 암호를 입력 합니다. `p@ssw0rd`
    
    <div class="alert alert-note">
      <h5><span class="win-icon win-icon-Page"></span>두고 </h5>
      <p>연결 프로세스는 즉시 수행 되지 않으며 최대 30 초까지 걸릴 수 있습니다.</p>
    </div>    
    
    장치에 성공적으로 연결한 경우 프롬프트 전에 장치의 IP 주소가 표시 되어야 합니다.

    ![PowerShell 콘솔](../media/PowerShell/ps_device.png)

9. 계정 암호를 업데이트 합니다. 관리자 계정에 대 한 기본 암호를 업데이트 하는 것 *이 좋습니다* . 이렇게 하려면 PowerShell 연결에서 다음 명령을 실행 합니다.

    a. `[new password]`를 강력한 암호로 바꿉니다.
    
            net user Administrator [new password]
            
    b. 그런 다음 `Exit-PSSession`를 사용 하 여 새 PowerShell 세션을 설정 하 고 새 자격 증명을 사용 하 여 `Enter-PSSession` 합니다.
    
            Exit-PSSession
            
            Enter-PSSession -ComputerName <machine-name or IP Address> -Credential <machine-name or IP Address or localhost>\Administrator

## <a name="commonly-used-powershell-commands"></a>일반적으로 사용 되는 PowerShell 명령

### <a name="troubleshooting-with-visual-studio-remote-debugger"></a>Visual Studio 원격 디버거 문제 해결

Visual Studio 2017에서 응용 프로그램을 배포할 수 있으려면 Visual Studio 원격 디버거 Windows IoT Core 장치에서 실행 되 고 있는지 확인 해야 합니다. 원격 디버거는 컴퓨터를 시작할 때 자동으로 열립니다. 두 번 확인 하려면 `tlist` 명령을 사용 하 여 PowerShell에서 실행 중인 모든 프로세스를 나열 합니다. 장치에서 실행 되는 두 개의 msvsmon.exe 인스턴스가 있어야 합니다.

장시간의 비활성 시간이 지난 후에도 Visual Studio 원격 디버거 시간이 초과 될 수 있습니다. Visual Studio에서 Windows IoT Core 장치에 연결할 수 없는 경우 장치를 다시 시작 해 보세요.

### <a name="configure-your-windows-iot-core-device"></a>Windows IoT 핵심 장치 구성

원하는 경우 장치 이름을 바꿀 수 있습니다. 

1. 컴퓨터 이름을 변경 하려면 `setcomputername` 유틸리티를 사용 합니다.

        setcomputername <new-name>

2. 변경 내용을 적용 하려면 장치를 다시 시작 합니다. 다음과 같이 `shutdown` 명령을 사용할 수 있습니다.

        shutdown /r /t 0

3. 컴퓨터 이름이 변경 되었기 때문에를 다시 시작한 후에는 다음 명령을 다시 실행 하 여 새 이름을 사용 하 여 장치에 연결 해야 합니다.

        Set-Item WSMan:\localhost\Client\TrustedHosts -Value <new-name>
        
이제 Windows IoT 핵심 장치가 올바르게 구성 되어 사용할 준비가 되었습니다.

### <a name="commonly-used-utilities"></a>일반적으로 사용 되는 유틸리티

PowerShell에서 사용할 수 있는 명령 및 유틸리티 목록은 [명령줄 유틸리티](../manage-your-device/CommandLineUtils.md) 페이지를 참조 하세요.

## <a name="known-issues-and-workarounds"></a>알려진 문제 및 해결 방법

**문제**: PowerShell 보안 정책의 알려진 버그로 인해 원격 세션 내에서 다음과 같은 문제가 발생 합니다.
* Get-help는 예기치 않은 일치 항목을 반환 합니다.
* 지정 된 모듈의 Get 명령이 빈 명령 목록을 반환 합니다.
* 이러한 모듈에서 cmdlet을 실행 하면 CommandNotFoundException: Appx, Get-netadapter, NetSecurity, Netsecurity, Pnp 장치가 throw 됩니다.
* 위의 모듈에서 import-module은 UnauthorizedAccess를 사용 하 여 PSSecurityException 예외를 throw 합니다. 모듈 자동 로딩이 작동 하지 않는 것 같습니다.

**해결 방법**: 원격 PowerShell 세션 내에서 실행 정책을 **RemoteSigned**로 수정 합니다. 다른 실행 정책에 대 한 자세한 내용은 [Set-executionpolicy Cmdlet 사용](https://technet.microsoft.com/library/ee176961.aspx)을 참조 하세요.

**문제**: get-netadapter와 같은 일부 모듈의 cmdlet이 표시 되지 않는 경우가 있습니다. 예를 들어 Import-module Get-netadapter는 빈 목록을 반환 합니다. 

**해결 방법**: import-module에-Force 매개 변수를 사용 합니다. 예를 들면 `Import-Module NetAdapter -Force`입니다.

**문제**: 실행 정책을 "AllSigned"로 설정 하면 PowerShell 원격이 중단 됩니다. Typesv3. types.ps1xml를 로드 하는 SecurityException을 사용 하 여 원격 세션을 만드는 후속 시도가 실패 합니다. 

**해결 방법**: Winrs.exe를 사용 하 여 PowerShell의 실행 정책을 복원 합니다.
* 콘솔 코드 페이지 `Chcp 65001` 변경
* 원격 cmd.exe 셸에 로그온 `Winrs.exe -r:<target> -u:<username> -p:<password> cmd.exe`
* 원격 cmd.exe 내에서 적절 한 레지스트리 키를 수정 `reg add HKLM\Software\Microsoft\PowerShell\1\ShellIds\Microsoft.PowerShell /v ExecutionPolicy /d RemoteSigned /f`
* 원격 cmd.exe 세션 `exit`을 종료 합니다.

### <a name="other-known-issues"></a>기타 알려진 문제

- PowerShell 스크립트에서 PowerShell 클래스 또는 열거형에 대 한 특성은 작동 하지 않습니다. 특성을 추가 하는 경우 throw 되는 예외는 다음과 같습니다. *형식이 런타임 형식 개체*여야 합니다.

- 아웃 바운드 CIM 및 PowerShell remoting은 지원 되지 않습니다. 신뢰 cmdlet의 관련 기능은 작동 하지 않습니다. 여기에는 입력 PSSession, 작업 가져오기, 수신 작업, Import-module, 호출 명령, 복사 항목이 포함 됩니다.

- SecureString 명령이 Convertfrom-csv 및 Convertto-html는 CredSSP 인증을 사용 하 여 세션을 만들지 않으면 작동 하지 않습니다. 그렇지 않으면-Key 매개 변수를 지정 해야 합니다. CredSSP 인증 구성에 대 한 자세한 내용은 [credssp를 사용 하 여 PowerShell "두 번째 홉" 기능 사용](https://devblogs.microsoft.com/scripting/enable-powershell-second-hop-functionality-with-credssp/)을 참조 하세요.


