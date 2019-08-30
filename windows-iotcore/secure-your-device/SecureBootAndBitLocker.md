---
title: Windows 10 IoT Core에서 보안 부팅, BitLocker 및 Device Guard 사용
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Windows 10 IoT Core에서 보안 부팅, BitLocker 및 Device Guard를 사용 하도록 설정 하는 방법을 알아봅니다.
keywords: windows iot, 보안 부팅, BitLocker, device guard, 보안, 턴키 보안
ms.openlocfilehash: 26e0949dd8ee0a8cfec8aeafee3908a3ade86293
ms.sourcegitcommit: 9ec4716afde25fdc8b94f7c0794448501f451b55
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/14/2019
ms.locfileid: "67142358"
---
# <a name="enabling-secure-boot-bitlocker-and-device-guard-on-windows-10-iot-core"></a>Windows 10 IoT Core에서 보안 부팅, BitLocker 및 Device Guard 사용

Windows 10 IoT Core는 UEFI 보안 부팅, BitLocker 장치 암호화 및 Device Guard와 같은 보안 기능 제공을 포함 합니다.  이러한 기능은 다양 한 유형의 공격에 탄력적으로 복원 가능한 완전히 잠긴 Windows IoT 장치를 만드는 장치 빌더가 지원 합니다.  이러한 기능은 장치 암호화를 사용 하 여 알 수 없는 이진 파일을 잠그고 사용자 데이터를 보호 하는 동시에 정의 된 방식으로 플랫폼이 시작 되도록 하는 최적의 보호를 제공 합니다.

## <a name="boot-order"></a>부팅 순서

IoT 장치에 대 한 보안 플랫폼을 제공 하는 개별 구성 요소에 대해 자세히 살펴보기 전에 Windows 10 IoT Core 장치에서 부팅 순서를 이해 해야 합니다.

IoT 장치의 전원이 켜 졌을 때에서 발생 하는 세 가지 주요 영역은 OS 커널 로드 및 설치 된 응용 프로그램 실행까지 모든 방법입니다.

* 플랫폼 보안 부팅
* UEFI(Unified Extensible Firmware Interface) (UEFI) 보안 부팅
* Windows 코드 무결성

![부팅 순서](../media/SecureBootAndBitLocker/BootOrder.jpg)

Windows 10 부팅 프로세스에 대 한 추가 정보는 [여기](https://docs.microsoft.com/windows/security/information-protection/secure-the-windows-10-boot-process)를 참조 하세요.

## <a name="locking-down-iot-devices"></a>IoT 장치 잠금 해제

Windows IoT 장치를 잠금으로 설정 하려면 다음 사항을 고려해 야 합니다.

### <a name="platform-secure-boot"></a>플랫폼 보안 부팅

장치를 처음 켤 때 전체 부팅 프로세스의 첫 번째 단계는 펌웨어 부팅 로더를 로드 하 고 실행 하는 것입니다 .이는 장치의 하드웨어를 초기화 하 고 응급 플래시 기능을 제공 합니다. 그런 다음 UEFI 환경을 로드 하 고 제어를 전달 합니다.

이러한 펌웨어 부팅 로더는 SoC와 관련 되어 있으므로 해당 장치 제조업체와 협력 하 여 이러한 부팅 로더가 장치에 생성 되도록 해야 합니다.

### <a name="uefi-secure-boot"></a>UEFI 보안 부팅

UEFI 보안 부팅은 첫 번째 정책 적용 지점이 며 UEFI에 있습니다.  펌웨어 드라이버, 옵션 Rom, UEFI 드라이버 또는 응용 프로그램, UEFI 부팅 로더 등 지정 된 기관에서 서명한 이진 파일의 실행만 허용 하도록 시스템을 제한 합니다. 이 기능은 플랫폼에서 알 수 없는 코드가 실행 되는 것을 방지 하 고 잠재적으로 보안 상태를 약화 합니다. 보안 부팅은 장치에 대 한 사전 부팅 맬웨어 공격 (예: 루트킷)의 위험을 줄여줍니다. 

OEM으로 서는 제조할 때 IoT 장치에 UEFI 보안 부팅 데이터베이스를 저장 해야 합니다. 이러한 데이터베이스에는 서명 데이터베이스 (db), 해지 된 서명 데이터베이스 (.dbx) 및 키 등록 키 데이터베이스 (KEK)가 포함 됩니다. 이러한 데이터베이스는 장치의 펌웨어 비휘발성 RAM (NV-RAM)에 저장 됩니다.

* **서명 데이터베이스 (db):** 그러면 장치에 로드 될 수 있는 운영 체제 로더, UEFI 응용 프로그램 및 UEFI 드라이버의 서명자 또는 이미지 해시가 나열 됩니다.

* **해지 된 서명 데이터베이스 (.dbx):** 이는 더 이상 신뢰할 수 없고 장치에 로드 될 수 없는 운영 체제 로더, UEFI 응용 프로그램 및 UEFI 드라이버의 서명자 또는 이미지 해시를 나열 합니다. 

* **키 등록 키 데이터베이스 (KEK):** 서명 및 해지 된 서명 데이터베이스를 업데이트 하는 데 사용할 수 있는 서명 키의 목록을 포함 합니다.

이러한 데이터베이스가 만들어지고 장치에 추가 되 면 OEM은 편집에서 펌웨어를 잠그고 PK (플랫폼 서명 키)를 생성 합니다. 이 키는 KEK에 대 한 업데이트에 서명 하거나 UEFI 보안 부팅을 사용 하지 않도록 설정 하는 데 사용할 수 있습니다.

UEFI 보안 부팅에서 수행 하는 단계는 다음과 같습니다.

1. 장치의 전원이 켜진 후에 서명 데이터베이스는 각각 PK (플랫폼 서명 키)에 대해 확인 됩니다.
2. 펌웨어가 트러스트 되지 않은 경우 UEFI 펌웨어는 OEM 특정 복구를 시작 하 여 신뢰할 수 있는 펌웨어를 복원 합니다.
3. Windows 부팅 관리자를 로드할 수 없는 경우 펌웨어는 Windows 부팅 관리자의 백업 복사본을 부팅 하려고 시도 합니다. 그래도 오류가 발생 하면 UEFI 펌웨어가 OEM 관련 수정을 시작 합니다.
4. Windows 부팅 관리자가 Windows 커널의 디지털 서명을 실행 하 고 확인 합니다. 신뢰할 수 있는 경우 Windows 부팅 관리자가 Windows 커널로 제어를 전달 합니다.

키 만들기 및 관리 지침과 함께 보안 부팅에 대 한 추가 세부 정보는 [여기](https://technet.microsoft.com/library/dn747883.aspx)에서 확인할 수 있습니다.

### <a name="windows-code-integrity"></a>Windows 코드 무결성

Windows 코드 무결성 (WCI)은 메모리에 로드 될 때마다 드라이버 또는 응용 프로그램의 무결성을 확인 하 여 운영 체제의 보안을 향상 시킵니다. CI에는 두 가지 주요 구성 요소인 KMCI (커널 모드 코드 무결성)와 UMCI (사용자 모드 코드 무결성)가 포함 되어 있습니다.

CCI (구성 가능한 코드 무결성)는 장치 빌더가 장치를 잠금 가능 하 게 하 고 서명 되 고 신뢰할 수 있는 코드를 실행 하 여 실행할 수 있도록 하는 Windows 10의 기능입니다.  이렇게 하기 위해 장치 빌더는 ' 골든 ' 장치 (하드웨어 및 소프트웨어의 최종 릴리스 버전)에서 코드 무결성 정책을 만든 다음 공장에서 모든 장치에 대해이 정책을 보호 하 고 적용할 수 있습니다.

코드 무결성 정책, 감사 및 적용을 배포 하는 방법에 대 한 자세한 내용은 [여기](https://technet.microsoft.com/itpro/windows/keep-secure/deploy-code-integrity-policies-steps)에서 최신 technet 설명서를 확인 하세요.

Windows 코드 무결성에서 수행 하는 단계는 다음과 같습니다.

1. Windows 커널은 로드 전에 서명 데이터베이스에 대해 다른 모든 구성 요소를 확인 합니다. 여기에는 드라이버, 시작 파일 및 ELAM (맬웨어 방지 조기 실행)이 포함 됩니다.
2. Windows 커널이 시작 프로세스에서 신뢰할 수 있는 구성 요소를 로드 하 고 신뢰할 수 없는 구성 요소를 로드 하는 것을 금지 합니다.
3. Windows 10 IoT Core 운영 체제가 설치 된 모든 응용 프로그램과 함께 로드 됩니다.

### <a name="bitlocker-device-encryption"></a>BitLocker 장치 암호화

또한 Windows 10 IoT Core는 경량 버전의 BitLocker 장치 암호화를 구현 하 여 오프 라인 공격 으로부터 IoT 장치를 보호 합니다. 이 기능은 UEFI에서 필요한 측정을 수행 하는 필수 사전 OS 프로토콜을 포함 하 여 TPM의 존재에 대 한 강력한 종속성을 갖습니다. 이러한 OS 이전 측정은 나중에 os가 실행 되는 방법에 대 한 결정적인 기록이 있는지 확인 합니다. 그러나 실행 제한을 적용 하지 않습니다.

> [!TIP]
> Windows 10 IoT Core의 BitLocker 기능을 사용 하면 사용 가능한 모든 NTFS 데이터 볼륨을 바인딩하는 동안 NTFS 기반 OS 볼륨을 자동으로 암호화할 수 있습니다. 이를 위해 EFIESP 볼륨 GUID가 _C12A7328-F81F-11D2-BA4B-00A0C93EC93B_으로 설정 되어 있는지 확인 해야 합니다.

### <a name="device-guard-on-windows-iot-core"></a>Windows IoT Core의 Device Guard

대부분의 IoT 장치는 고정 된 기능 장치로 빌드됩니다. 이는 장치 빌더가 지정 된 장치에서 실행 해야 하는 펌웨어, 운영 체제, 드라이버 및 응용 프로그램을 정확 하 게 알고 있음을 의미 합니다. 또한이 정보는 알려진 코드와 신뢰할 수 있는 코드의 실행만 허용 하 여 IoT 장치를 완전히 잠그는 데 사용할 수 있습니다. Windows 10 IoT Core의 Device Guard는 잠긴 장치에서 알 수 없거나 신뢰할 수 없는 실행 코드를 실행할 수 없도록 하 여 IoT 장치를 보호 하는 데 도움이 될 수 있습니다.


## <a name="turnkey-security-on-iot-core"></a>IoT Core의 턴키 보안

IoT Core 장치에서 주요 보안 기능을 쉽게 사용할 수 있도록 Microsoft는 장치 빌더가 완전히 잠긴 IoT 장치를 빌드할 수 있는 [턴키 보안 패키지]( https://github.com/ms-iot/security/tree/master/TurnkeySecurity) 를 제공 하 고 있습니다. 이 패키지는 다음에 도움이 됩니다.

* 보안 부팅 키 프로 비전 및 지원 되는 IoT 플랫폼에서 기능 사용
* BitLocker를 사용 하 여 장치 암호화 설정 및 구성
* 서명 된 응용 프로그램 및 드라이버 실행만 허용 하도록 장치 잠금 시작

다음 단계에서는 [턴키 보안 패키지]( https://github.com/ms-iot/security/tree/master/TurnkeySecurity) 를 사용 하 여 잠금 이미지를 만드는 과정을 안내 합니다.

![잠금 이미지 만들기](../media/SecurityFlowAndCertificates/ImageLockDown.png)

### <a name="prerequisites"></a>사전 요구 사항

* Windows 10 Enterprise를 실행 하는 PC
* [Windows 10 SDK](https://developer.microsoft.com/en-US/windows/downloads/windows-10-sdk) -인증서 생성에 필요
* [Windows 10 ADK](https://developer.microsoft.com/en-us/windows/hardware/windows-assessment-deployment-kit) -CAB 생성에 필요
* 최종 잠금에 대 한 배송 펌웨어, OS, 드라이버 및 응용 프로그램을 사용 하 여 플랫폼 릴리스 하드웨어 참조

### <a name="development-iot-devices"></a>개발 IoT 장치

Windows 10 IoT Core는 수백 개의 장치에서 활용 되는 다양 한 silicons에서 작동 합니다. 제안 된 [IoT 개발 장치](../learn-about-hardware/SoCsAndCustomBoards.md)중에서 다음은 보안 부팅, 측정 된 부팅, BitLocker 및 Device Guard 기능과 함께 펌웨어 TPM 기능을 즉시 제공 합니다.

* Qualcomm DragonBoard 410c

    보안 부팅을 사용 하려면 RPMB를 프로 비전 해야 할 수 있습니다. Windows 10 IoT Core를 사용 하 여 eMMC가 제공 되 면 ( [여기](https://docs.microsoft.com/windows/iot-core/tutorials/quickstarter/devicesetup#using-the-iot-dashboard-dragonboard-410c)에 설명 된 대로) 전원을 켤 때 장치에서 [전원] + [vol +] + [vol-]을 동시에 누르고 bds 메뉴에서 "RPMB 프로 비전"을 선택 합니다. *이는 되돌릴 수 없는 단계입니다.*

* Intel MinnowBoardMax

    Intel의 MinnowBoard Max의 경우 펌웨어 버전은 0.82 이상 이어야 합니다 ( [최신 펌웨어](https://firmware.intel.com/projects/minnowboard-max)다운로드). TPM 기능을 사용 하도록 설정 하려면 키보드를 사용 하 여 보드를 켜고, 연결 된 & 표시 하 고 F2 키를 눌러 UEFI 설치를 시작 합니다. _Device Manager-> 시스템 설정-> 보안 구성-> ptt_ 로 이동 하 여  _&lt;사용&gt;_ 으로 설정 합니다. F10 키를 눌러 변경 내용을 저장 하 고 플랫폼 다시 부팅을 진행 합니다.

> [!NOTE]
> Raspberry Pi 2 또는 3은 TPM을 지원 하지 않으므로 잠금 시나리오를 구성할 수 없습니다.

### <a name="generate-lockdown-packages"></a>잠금 패키지 생성

1. 장치를 구성 하 고 잠그기 위해 필요한 추가 도구 및 스크립트를 모두 포함 하는 [Devicelockdown 스크립트](https://github.com/ms-iot/security/tree/master/TurnkeySecurity) 패키지를 다운로드 합니다.
2. Windows 10 PC에서 PS (관리 PowerShell) 콘솔을 시작 하 고 다운로드 한 스크립트의 위치로 이동 합니다.
3. 을 사용 하 여 네트워크 공유를 통해 PC에 참조 하드웨어 플랫폼 (잠금 해제 된 이미지 실행) 탑재

    ```powershell
    net use \\a.b.c.d\c$ /user:username password
    ```

4. 를 사용 하 여 장치에 대 한 키 생성

    ```powershell
    .\GenerateKeys.ps1 -OemName '<your oem name>' -outputPath '<output directory>'
    ```

    * 키와 인증서가 지정 된 출력 폴더에 적절 한 접미사로 생성 됩니다.
    * 장치는 잠금 후에만 이러한 키로 서명 된 이진 파일을 신뢰 하므로 **생성 된 키의 보안을 유지** 합니다.
    * 이 단계를 건너뛰고 테스트용 으로만 미리 생성 된 키를 사용할 수 있습니다.

5. _설정 .xml_ 구성

    * 일반 섹션: 패키지 디렉터리 지정
    * 도구 섹션: 도구의 경로 설정
        * Windows10KitsRoot`(e.g. <Windows10KitsRoot>C:\Program Files (x86)\Windows Kits\10\</Windows10KitsRoot>)`
        * WindowsSDKVersion`(e.g. <WindowsSDKVersion>10.0.15063.0</WindowsSDKVersion>)`
            * 컴퓨터에 설치 된 SDK 버전이 아래에 있습니다.`C:\Program Files (x86)\Windows Kits\10\`
    * SecureBoot 섹션: 보안 부팅에 사용할 키를 지정 합니다 (PK 및 SB 키).
    * BitLocker 섹션: Bitlocker 데이터 복구에 대 한 인증서 지정 (DRA 키)
    * SIPolicy 섹션: 신뢰할 수 있는 인증서 지정
        * ScanPath: 이진 파일을 검색할 장치의 경로`\\a.b.c.d\C$`
        * 고침 SIPolicy (PAUTH 키)의 서명자
        * 정의 사용자 모드 인증서 (UMCI 키) 
        * Kernel 커널 모드 인증서 (KMCI 키)
    * 패키지 패키지 생성에 대 한 설정 지정

> [!IMPORTANT]
> 초기 개발 주기 중 테스트를 지원 하기 위해 Microsoft는 해당 하는 경우 미리 생성 된 키 및 인증서를 제공 했습니다.  이는 Microsoft 테스트, 개발 및 시험판 이진 파일이 신뢰할 수 있는 것으로 간주 됨을 의미 합니다.  최종 제품을 만들고 이미지를 생성 하는 동안 이러한 인증서를 제거 하 고 자신의 키를 사용 하 여 완전히 잠기는 장치를 확인 해야 합니다.

6. 다음 명령을 실행 하 여 필요한 패키지를 생성 합니다.

    ```powershell
    Import-Module .\IoTTurnkeySecurity.psm1
    # Generate the security packages for retail
    New-IoTTurnkeySecurity -ConfigFileName .\settings.xml
    (or)
    # Generate the security packages for test
    New-IoTTurnkeySecurity -ConfigFileName .\settings.xml -Test
    ```

### <a name="test-lockdown-packages"></a>잠금 패키지 테스트
다음 단계를 수행 하 여 생성 된 패키지를 잠금이 해제 된 장치에 수동으로 설치 하 여 테스트할 수 있습니다.

1. 잠금 해제 된 이미지를 사용 하 여 장치를 깜박입니다 (이전 단계에서 스캔 하는 데 사용 되는 이미지).
2. 장치에 연결 ([SSH 사용](../connect-your-device/SSH.md) 또는 [Powershell](../connect-your-device/PowerShell.md)사용)
3. 다음 .cab 파일을 디렉터리 아래의 장치에 복사 합니다 (예:).`c:\OemInstall`
    * 지원을. 사용자 지정 .Cmd .cab
    * 지원을. 보안. BitLocker .cab
    * 지원을. 보안. c a b .cab .cab
    * 지원을. 보안. DeviceGuard .cab
4. 다음 명령을 issueing 여 생성 된 패키지의 준비를 시작 합니다.

    ```C
    applyupdate -stage c:\OemInstall\OEM.Custom.Cmd.cab
    ```
    사용자 지정 이미지를 사용 하는 경우이 파일을 *건너뛰고* 파일에서 `c:\windows\system32\oemcustomization.cmd` `Output\OEMCustomization\OEMCustomization.cmd` 사용할 수 있는 콘텐츠를 사용 하 여를 수동으로 편집 해야 합니다.

    ```C
    applyupdate -stage c:\OemInstall\OEM.Security.BitLocker.cab
    applyupdate -stage c:\OemInstall\OEM.Security.SecureBoot.cab
    applyupdate -stage c:\OemInstall\OEM.Security.DeviceGuard.cab

5. Finally, commit the packages via

    ```C
    applyupdate -commit
    ```

6. 장치는 패키지를 설치 하기 위해 업데이트 OS (기어 표시)로 다시 부팅 되 고, 다시 주 OS로 다시 부팅 됩니다.  장치가 MainOS로 다시 부팅 되 면 보안 부팅이 사용 하도록 설정 되 고 SIPolicy를 사용 해야 합니다.
7. 장치를 다시 부팅 하 여 Bitlocker 암호화를 활성화 합니다.
8. 보안 기능 테스트
    * SecureBoot: 시도 `bcdedit /debug on` 하면 보안 부팅 정책에 의해 값이 보호 됨을 나타내는 오류가 발생 합니다.
    * BitLocker: 를 `start /wait sectask.exe -waitencryptcomplete:1`실행 합니다. ERRORLEVEL `-2147023436` 이 (ERROR_TIMEOUT) 이면 암호화가 완료 되지 않은 것입니다. .Cmd 파일에서 sectask를 실행 하는 경우를 `start /wait`생략 합니다.
    * DeviceGuard: SIPolicy 목록에 없는 서명 된 이진 파일 또는 인증서로 서명 된 이진 파일을 실행 하 고 실행이 실패 하는지 확인 합니다.

### <a name="generate-lockdown-image"></a>잠금 이미지 생성

이전에 정의 된 설정에 따라 잠금 패키지가 작동 하는지 확인 한 후에는 다음 단계를 수행 하 여 이러한 패키지를 이미지에 포함할 수 있습니다. 사용자 지정 이미지 생성 지침은 [IoT 제조 가이드](https://aka.ms/iotcoreguide) 를 참조 하세요.

1. 작업 영역 디렉터리에서 위의 생성 된 출력 디렉터리에서 다음 파일을 업데이트 합니다.
    * SecureBoot`Copy ..\Output\SecureBoot\*.bin  ..\Workspace\Common\Packages\Security.SecureBoot`
      * SetVariable_db
      * SetVariable_kek
      * SetVariable_pk
    * BitLocker`Copy ..\Output\Bitlocker\*.* ..\Workspace\Common\Packages\Security.Bitlocker`
      * DETask .xml
      * 보안.
      * 설정. bitlocker.
    * DeviceGuard:`Copy ..\Output\DeviceGuard\*.*  ..\Workspace\Common\Packages\Security.DeviceGuard`
      * SIPolicyOn. p7b
      * SIPolicyOff. p7b
  
2. 잠금 패키지 기능 ID를 사용 하 여 ProductName 디렉터리 아래에 RetailOEMInput 및 TestOEMInput를 추가 합니다.
    * `<Feature>SEC_BITLOCKER</Feature>`
    * `<Feature>SEC_SECUREBOOT</Feature>`
    * `<Feature>SEC_DEVICEGUARD</Feature>`
3. 이미지 다시 생성
    * `buildpkg all`이는 위의 정책 파일을 기반으로 새 잠금 패키지를 생성 합니다.
    * `buildimage ProductName test(or)retail`(새 Flash .ffu 생성)
4. 이 새로운 Flash .ffu를 사용 하 여 장치를 플래시 하 고 보안 기능의 유효성을 검사 합니다.

[SecureSample](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/SecureSample) 를 참조 하세요.

또는 IoTCore Shell 자체에서 보안 패키지를 생성할 수 있습니다. 자세한 내용은 [보안 패키지 추가](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools#adding-security-packages) 를 참조 하세요.


### <a name="developing-with-codesigning-enforcement-enabled"></a>코드 서명 적용을 사용 하 여 개발

패키지가 생성 되 고 잠금이 활성화 되 면 개발 중에 이미지에 도입 된 이진 파일을 적절 하 게 서명 해야 합니다. 사용자 모드 이진 파일이 _.\Keys\ * * *-UMCI .pfx_키로 서명 되었는지 확인 합니다. 드라이버의 경우와 같이 커널 모드 서명의 경우 고유한 서명 키를 지정 하 고 위의 SIPolicy에도 포함 되어 있는지 확인 해야 합니다.

### <a name="unlocking-encrypted-drives"></a>암호화 된 드라이브 잠금 해제

개발 및 테스트 중에 암호화 된 장치에서 오프 라인으로 콘텐츠를 읽으려고 할 때 (예: SD card for MinnowBoardMax 또는 DragonBoard의 eMMC에서 USB 대량 저장소 모드를 통해) ' diskpart '를 사용 하 여 드라이브 문자를 MainOS 및 데이터 볼륨에 할당할 수 있습니다. MainOS 및 w: 데이터의 경우 v:를 가정 합니다.
볼륨이 잠긴 것으로 표시 되며 수동으로 잠금을 해제 해야 합니다. OEM-DRA 인증서가 설치 되어 있는 모든 컴퓨터에서이 작업을 수행할 수 있습니다 ( [Devicelockdown 샘플](https://github.com/ms-iot/security/tree/master/TurnkeySecurity)에 포함 됨). PFX를 설치 하 고 관리 CMD 프롬프트에서 다음 명령을 실행 합니다.

* `manage-bde -unlock v: -cert -cf OEM-DRA.cer`
* `manage-bde -unlock w: -cert -cf OEM-DRA.cer`

콘텐츠를 오프 라인으로 자주 액세스 해야 하는 경우 다음 명령을 사용 하 여 초기 잠금 해제 후 볼륨에 대해 BitLocker autounlock을 설정할 수 있습니다.

* `manage-bde -autounlock v: -enable`
* `manage-bde -autounlock w: -enable`

### <a name="disabling-bitlocker"></a>BitLocker 사용 안 함

BitLocker를 일시적으로 사용 하지 않도록 설정 하 고, IoT 장치를 사용 하 여 원격 PowerShell 세션을 초기화 하 고, 명령을 `sectask.exe -disable`실행 해야 하는 경우가 발생 합니다.  

> [!NOTE]
> 예약 된 암호화 작업이 사용 하지 않도록 설정 된 경우를 제외 하 고 다음 장치 부팅에서 장치 암호화를 다시 사용 하도록 설정 합니다.


