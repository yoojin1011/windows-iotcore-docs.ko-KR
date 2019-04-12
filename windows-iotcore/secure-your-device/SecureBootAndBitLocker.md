---
title: 보안 부팅, BitLocker 및 Windows 10 IoT Core Device Guard를 사용 하도록 설정
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 보안 부팅, BitLocker 및 Windows 10 IoT Core Device Guard를 사용 하도록 설정 하는 방법 알아보기
keywords: windows iot, 보안 부팅, BitLocker, 턴키 보안 장치 가드, 보안
ms.openlocfilehash: 68698a1b440b297eb9bfa9223bd324ce330386b9
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513598"
---
# <a name="enabling-secure-boot-bitlocker-and-device-guard-on-windows-10-iot-core"></a>보안 부팅, BitLocker 및 Windows 10 IoT Core Device Guard를 사용 하도록 설정

## <a name="introduction"></a>소개

크리에이터 업데이트의 릴리스부터 Windows 10 IoT Core UEFI 보안 부팅, BitLocker 장치 암호화 및 Device Guard를 포함 하는 보안 기능 제품을 개선 합니다.  다양 한 유형의 공격에 복원 력 있는 Windows IoT 장치로 완벽 하 게 잠겨 만드는 장치 작성기 수는 있습니다.  함께 이러한 기능은 플랫폼을 알 수 없는 이진 파일을 잠그지 및 장치 암호화를 사용 하 여 사용자 데이터를 보호 하는 동안 정의 된 방식으로 시작 됩니다 보장 하는 최적의 보호를 제공 합니다.

### <a name="secure-boot"></a>보안 부팅

UEFI 보안 부팅은 UEFI에 있는 첫 번째 정책 적용 지점입니다.  지정 된 인증 기관에서 서명 된 바이너리만 실행할 수만 있도록 시스템을 제한 합니다. 이 기능은 플랫폼에서 실행 되 고 잠재적으로의 보안 상태가 약화 되 알 수 없는 코드를 방지 합니다.

### <a name="bitlocker-device-encryption"></a>BitLocker 장치 암호화

Windows 10 IoT Core 경량 버전의 BitLocker 장치 암호화를 오프 라인 공격 으로부터 IoT 장치가 보호도 구현 합니다.  이 기능은 preOS 프로토콜을 포함 하 여 필요한 측정을 수행 하는 UEFI의 플랫폼에서 TPM의 존재에 강력한 종속성을 갖습니다. 이러한 preOS 측정을 갖도록 OS 나중에 OS가 시작 하는 방법을; 한 명확한 기록이 그러나 실행 제한을 적용 하지 않습니다.

> [!TIP]
> Windows 10 IoT Core 대 한 BitLocker 기능을 사용할 수 있는 모든 NTFS 데이터 볼륨을 바인딩하는 동안 자동 NTFS 기반 OS 볼륨 암호화를 위한 수 있습니다.  이 위해 EFIESP 볼륨 GUID로 설정 되어 있는지 확인 하는 데 필요한 것 _C12A7328-F81F-11D2-BA4B-00A0C93EC93B_합니다.

### <a name="device-guard-on-windows-iot-core"></a>Windows IoT Core에서 device Guard

대부분의 IoT 장치는 고정 함수 장치로 빌드됩니다.  이 장치 작성기는 펌웨어, 운영 체제, 드라이버 및 응용 프로그램 특정된 장치에서 실행 되어야 합니다 정확히 알고 있는 것을 의미 합니다.  이 정보를 수 있습니다만 알려져 있고 신뢰할 수 있는 코드의 실행을 허용 하 여 IoT 장치를 완벽 하 게 잠금에 사용 합니다.  Windows 10 IoT Core device Guard는 잠긴 장치에서 알 수 없거나 신뢰할 수 없는 실행 코드를 실행할 수 없음을 확인 하 여 IoT 장치를 보호할 수 있습니다.

## <a name="locking-down-iot-devices"></a>잠금 다운 IoT 장치

Windows IoT 장치를 잠그고 순서로 다음 고려 사항은 만들어야 하는 중...

### <a name="uefi-platform--secure-boot"></a>보안 부팅 및 UEFI 플랫폼

Device Guard 기능을 활용 하기 위해 부팅 이진 파일 및 UEFI 펌웨어 서명 되 고 변조 될 수 없음을 확인 하는 데 필요한 됩니다.  UEFI 보안 부팅은 UEFI에 있는 첫 번째 정책 적용 지점입니다.  지정된 된 권한으로 로그인 하는 부팅 이진 파일의 실행만 사용할 수 있도록 시스템을 제한 하 여 변조를 방지 합니다. 키 생성 및 관리 지침, 보안 부팅에 대 한 추가 정보를 사용할 수 [여기](https://technet.microsoft.com/library/dn747883.aspx)합니다.

### <a name="configurable-code-integrity-cci"></a>구성 가능한 코드 무결성 (CCI)

응용 프로그램 메모리에 로드 될 때마다 드라이버의 무결성을 확인 하 여 운영 체제의 보안을 강화 하는 코드 무결성 (CI). CI는 두 개의 주요 구성-커널 모드 코드 무결성 (KMCI) 및 사용자 모드 코드 무결성 (UMCI)를 포함합니다.

구성 가능한 코드 무결성 (CCI)는 Windows 10 장치를 잠그고 장치 작성기를 사용 하면만 실행 하 고 서명 되 고 신뢰할 수 있는 코드를 실행할 수 있도록 하는 기능입니다.  이렇게 하려면 장치 작성기 수 코드 무결성 정책을 'golden' 장치 (하드웨어 및 소프트웨어의 최종 릴리스 버전)에 다음 보안 만들고 공장 현장에서 모든 장치에서이 정책을 적용 합니다.

코드 무결성 정책을 배포 하는 방법에 대 한 자세한 내용은 감사 및 적용, 설명서를 확인해 최신 technet [여기](https://technet.microsoft.com/itpro/windows/keep-secure/deploy-code-integrity-policies-steps)합니다.

## <a name="turnkey-security-on-iot-core"></a>IoT Core에 대 한 턴키 보안

Microsoft는 턴키 ' 보안 패키지 '을 제공 하는 데 쉽게 사용 IoT Core 장치에서 주요 보안 기능을 위해 장치 작성기 빌드할 수 있는 IoT 장치를 완벽 하 게 잠겨 있습니다.  이 패키지에 도움이 됩니다.

* 보안 부팅 키 프로 비전 하 고 지원 되는 IoT 플랫폼에서이 기능을 사용 하도록 설정
* BitLocker를 사용 하 여 장치 암호화의 설정 및 구성 
* 시작만 서명 된 응용 프로그램 및 드라이버를 실행할 수 있도록 장치 잠금

### <a name="pre-requisites"></a>필수 구성 요소

* Windows 10 Enterprise 실행 하는 PC
* [Windows 10 SDK](https://developer.microsoft.com/en-US/windows/downloads/windows-10-sdk) -인증서 생성에 대 한 필수
* [Windows 10 ADK](https://developer.microsoft.com/en-us/windows/hardware/windows-assessment-deployment-kit) -CAB 생성을 위한 필수 항목
* 참조 하는 플랫폼 전달 펌웨어, OS, 드라이버 및 응용 프로그램을 사용 하 여 릴리스 하드웨어 해야 최종 잠금에 대 한

### <a name="development-iot-devices"></a>IoT 장치 개발

Windows 10 IoT Core 수백 대의 장치에서 사용 되는 다양 한 silicons를 사용 하 여 작동 합니다. [IoT 개발 장치 제안](../learn-about-hardware/SoCsAndCustomBoards.md), 기본적으로 보안 부팅, 계획 부팅, BitLocker 및 Device Guard 기능과 함께 펌웨어 TPM 기능을 제공 하는 다음:

* Qualcomm DragonBoard 410 c

    보안 부팅을 사용 하도록 설정 하기 위해 RPMB 프로 비전 해야 할 수도 있습니다. eMMC Windows 10 IoT Core 사용 하 여 플래시 됨 된가 되 면 (지침에 따라 [여기](https://docs.microsoft.com/windows/iot-core/tutorials/quickstarter/devicesetup#using-the-iot-dashboard-dragonboard-410c), 키를 눌러 [Power] + [Vol +] + [Vol-]을 선택 "프로 비전 RPMB" BDS 메뉴에서 전원을 켤 때 장치에서 동시에 합니다. *이 단계를 취소할 수는 note 하십시오.*

* Intel MinnowBoardMax

    Intel의 MinnowBoard 최대 펌웨어 버전 0.82 이상 이어야 합니다 (가져오기의 [최신 펌웨어로](https://firmware.intel.com/projects/minnowboard-max)). TPM 기능을 사용 하려면 키보드와 디스플레이 보드의 전원을 연결 및 UEFI 설치 F2 키를 누릅니다. 로 이동 _Device Manager 시스템 설정-> 보안 구성-> PTT->_ 로 설정 하 고  _&lt;사용 하도록 설정&gt;_ 합니다. F10 키를 눌러 변경 내용을 저장 하는 플랫폼의 다시 부팅을 사용 하 여 계속 합니다.

> [!NOTE]
> Raspberry Pi 2 또는 3 TPM을 지원 하지 않으며 따라서에서는 잠금 시나리오를 구성할 수 없습니다.

### <a name="generate-lockdown-packages"></a>잠금 패키지를 생성 합니다.

1. 다운로드 합니다 [DeviceLockDown 스크립트](https://github.com/ms-iot/security/tree/master/TurnkeySecurity) 모든 추가 도구 및 구성 하 고 장치를 잠그는 데 필요한 스크립트를 포함 하는 패키지
2. Windows 10 pc를 관리 PS (PowerShell) 콘솔을 시작 하 고 다운로드 한 스크립트의 위치로 이동 합니다.
3. (잠금 해제 된 이미지를 실행) 하 여 참조 하드웨어 플랫폼을 사용 하 여 네트워크 공유를 통해 PC에 탑재

    ```powershell
    net use \\a.b.c.d\c$ /user:username password
    ```

4. 사용 하 여 장치에 대 한 키를 생성 합니다.

    ```powershell
    .\GenerateKeys.ps1 -OemName '<your oem name>' -outputPath '<output directory>'
    ```

    * 키 및 인증서를 적절 한 접미사를 사용 하 여 지정 된 출력 폴더에 생성 됩니다.
    * **생성 된 키를 보호할** 장치는 이진 파일을 신뢰 하는 대로 잠금 후에 이러한 키를 사용 하 여 서명 합니다.
    * 이 단계를 건너뛸 수 있습니다를 미리 생성 된 키를 사용 하 여 테스트 전용

5. Pfx 파일에서 직접 클릭 하거나 사용 하 여 생성 된.pfx 인증서를 설치할는 아래 powershell 명령을

    ```powershell
    Import-PfxCertificate -FilePath $pfxfile -CertStoreLocation Cert:\CurrentUser\My
    ```

6. 구성 _settings.xml_

    * 일반 섹션: 패키지 디렉터리를 지정 합니다.
    * 도구 섹션: 도구에 대 한 경로 설정 합니다.
        * Windows10KitsRoot `(e.g. <Windows10KitsRoot>C:\Program Files (x86)\Windows Kits\10\</Windows10KitsRoot>)`
        * WindowsSDKVersion `(e.g. <WindowsSDKVersion>10.0.15063.0</WindowsSDKVersion>)`
            * 컴퓨터에 설치 된 SDK 버전은 `C:\Program Files (x86)\Windows Kits\10\`
    * SecureBoot 섹션: 보안 부팅 (PK 및 SB 키)에 사용할 키를 지정 합니다.
    * BitLocker 섹션: Bitlocker 데이터 복구 (DRA 키)에 대 한 인증서를 지정 합니다.
    * SIPolicy 섹션: 신뢰할 수 있는 인증서를 지정 합니다.
        * ScanPath : 이진 파일을 검색 하는 것에 대 한 장치의 경로 `\\a.b.c.d\C$`
        * 업데이트: 서명자의 SIPolicy (PAUTH 키)
        * 사용자: 사용자 모드 인증서 (UMCI 키) 
        * 커널: 커널 모드 (KMCI 키) 인증서
    * 패키징: 패키지 생성을 위한 설정 지정

> [!IMPORTANT]
> 초기 개발 주기 동안 테스트를 지원 하기 위해 Microsoft에 제공 미리 생성 된 키 및 인증서 적절 한 경우.  즉, 신뢰할 수 있는 Microsoft 테스트, 개발 및 시험판 버전 이진 파일 간주 됩니다.  최종 제품 만들기 및 이미지를 생성 하는 동안 사용할 이러한 인증서를 제거 하 고 사용자 고유의 키를 사용 하 여 장치를 완벽 하 게 잠겨 있는지 확인 해야 합니다.

> [!TIP]
> Microsoft 앱 스토어에서 앱 구성에서 Microsoft Marketplace PCA 2011 인증서를 포함 하 여 허용 될 수 있습니다 _settings.xml_: 
    ```xml
    <Cert>db\MicrosoftMarketPlacePCA2011.cer</Cert>              <!-- Microsoft MarketPlace PCA 2011 -->
    ```

6. 필요한 패키지를 생성 하려면 다음 명령을 실행 합니다.

    ```powershell
    Import-Module .\IoTTurnkeySecurity.psm1
    # Generate the security packages for retail
    New-IoTTurnkeySecurity -ConfigFileName .\settings.xml
    (or)
    # Generate the security packages for test
    New-IoTTurnkeySecurity -ConfigFileName .\settings.xml -Test
    ```

### <a name="test-lockdown-packages"></a>잠금 패키지 테스트
수동으로 다음 단계에 따라 잠금 해제 된 장치에 설치 하 여 생성된 된 패키지를 테스트할 수 있습니다.

1. 잠금이 해제 된 이미지 (이전 단계에서 스캔 하는 데 사용 되는 이미지)를 사용 하 여 장치를 업데이트 합니다.
2. 장치에 연결 ([SSH를 사용 하 여](../connect-your-device/SSH.md) 알거나 [Powershell](../connect-your-device/PowerShell.md))
3. 예를 들어 디렉터리에 있는 장치에 다음.cab 파일을 복사 `c:\OemInstall`
    * OEM.Custom.Cmd.cab
    * OEM.Security.BitLocker.cab
    * OEM.Security.SecureBoot.cab
    * OEM.Security.DeviceGuard.cab
4. 다음 명령을 내림 하 여 생성된 된 패키지의 준비 시작

    ```C
    applyupdate -stage c:\OemInstall\OEM.Custom.Cmd.cab
    ```
    사용자 지정 이미지를 사용 하는 경우 해야 *건너뜁니다* 이 파일을 수동으로 편집 합니다 `c:\windows\system32\oemcustomization.cmd` 에서 사용할 수 있는 내용으로 `Output\OEMCustomization\OEMCustomization.cmd` 파일

    ```C
    applyupdate -stage c:\OemInstall\OEM.Security.BitLocker.cab
    applyupdate -stage c:\OemInstall\OEM.Security.SecureBoot.cab
    applyupdate -stage c:\OemInstall\OEM.Security.DeviceGuard.cab

5. Finally, commit the packages via

    ```C
    applyupdate -commit
    ```

6. 장치가는 업데이트 패키지를 설치 하려면 OS (보여 주는 gears)으로 다시 부팅 됩니다 하 고 기본 OS를 다시 부팅 됩니다.  장치를 MainOS 되돌려 다시 부팅 보안 부팅을 사용할 및 SIPolicy 참여 해야 합니다.
7. Bitlocker 암호화를 활성화 하려면 다시 장치를 다시 부팅 합니다.
8. 보안 기능 테스트
    * **SecureBoot** : 시도 `bcdedit /debug on` , 값 보안 부팅 정책에 의해 보호 되는 내용의 오류가 표시 됩니다.
   * **BitLocker** : 유효성을 검사할 해당 bitlocker 암호화 완료 되 면 실행<p>
        `sectask.exe -waitenableforcompletion 1`<p>
        0을 반환 하는 경우 시스템의 모든 드라이브를 만들었습니다. bitlockered 의미 합니다.  다른 모든 반환 코드는 오류입니다.<p>
        *추가 구문*<p>
         `-waitenableforcompletion [timeout]` <p>
        = > 모든 NTFS 볼륨에서 BitLocker 암호화 완료 될 때까지 대기 합니다.<p>
        = >는 데 사용 될 때까지 기다리는 시간 (초) 시간 제한입니다.<p>
        = > 경우 제한 시간 지정 하지 않으면 활성화가 완료 될 때까지 또는 무기한 대기 합니다.<p>
        이 반환 됩니다. <p>
        0 : 성공적으로 완료 되는 BitLocker 암호화를 볼륨은 Bitlocker로 암호화 됨입니다.<p>
        ERROR_TIMEOUT: 완료 되 면 암호화 진행에서 될 때까지 기다리는 동안 시간이 초과 됩니다.<p>
        오류 / 기타 코드: 비트 보관 서비스를 반환한 실패 오류 코드를 반환 합니다.

    * **DeviceGuard** : 모든 부호 없는 이진 또는 SIPolicy 목록에 없는 인증서로 서명 된 이진 파일을 실행 하 고 실행 해 서 실패 하는지를 확인 합니다.

### <a name="generate-lockdown-image"></a>잠금 이미지 생성

앞에서 정의한 설정에 따라 작업 하는 잠금 패키지 유효성 검사 후 포함할 수 있습니다 이러한 패키지를 이미지에 따라는 아래 단계를 제공 합니다. 읽기 [IoT 제조 가이드](https://aka.ms/iotcoreguide) 사용자 지정 이미지 만들기 지침에 대 한 합니다.

1. 작업 영역 디렉터리에 생성 된 출력 디렉터리에서 다음 파일 업데이트
    * SecureBoot: `Copy ..\Output\SecureBoot\*.bin  ..\Workspace\Common\Packages\Security.SecureBoot`
      * SetVariable_db.bin
      * SetVariable_kek.bin
      * SetVariable_pk.bin
    * BitLocker: `Copy ..\Output\Bitlocker\*.* ..\Workspace\Common\Packages\Security.Bitlocker`
      * DETask.xml
      * Security.Bitlocker.wm.xml
      * setup.bitlocker.cmd
    * DeviceGuard: `Copy ..\Output\DeviceGuard\*.*  ..\Workspace\Common\Packages\Security.DeviceGuard`
      * SIPolicyOn.p7b
      * SIPolicyOff.p7b
  
2. RetailOEMInput.xml 및 TestOEMInput.xml 잠금 패키지 기능 ID 사용 하 여 ProductName 디렉터리 아래에 추가 합니다.
    * `<Feature>SEC_BITLOCKER</Feature>`
    * `<Feature>SEC_SECUREBOOT</Feature>`
    * `<Feature>SEC_DEVICEGUARD</Feature>`
3. 이미지를 다시 생성
    * `buildpkg all` (위의 정책 파일에 따라 새 잠금 패키지 생성)
    * `buildimage ProductName test(or)retail`  (새 Flash.ffu 생성)
4. 이 새 Flash.ffu 사용 하 여 장치를 플래시 하 고 보안 기능을 확인 합니다.

참조 [SecureSample](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/SecureSample) 잠금 dragon 보드 구성의 예입니다.

자체 IoTCore 셸에서 보안 패키지를 생성, 참조 수 또는 [보안 패키지를 추가](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools#adding-security-packages) 세부 정보에 대 한 합니다.


### <a name="developing-with-codesigning-enforcement-enabled"></a>코드 서명 적용 사용를 사용 하 여 개발

패키지 생성 된 잠금 활성화 되 고 개발 하는 동안 이미지에 도입 된 이진 파일 적절 하 게 서명 해야 합니다. 사용자 모드 바이너리 키로 서명 되었는지 확인 _. \Keys\ * * *-UMCI.pfx_합니다. 커널 모드 서명에 대 한 고유한 서명 키를 지정 하 고 있는지 확인 하려면 해야 드라이버의 경우와 같이 이러한에 에서도 나와 위의 SIPolicy 합니다.

### <a name="unlocking-encrypted-drives"></a>암호화 된 드라이브를 잠금 해제

개발 및 테스트 하는 동안 (예: USB 대용량 저장 모드를 통해 MinnowBoardMax 또는 DragonBoard의 eMMC에 SD 카드)를 암호화 된 장치를 오프 라인에서 내용을 읽을 하려고 할 때 'diskpart' 사용할 수 있습니다 (보겠습니다 MainOS 및 데이터 볼륨에 드라이브 문자를 할당 하려면 가정 시킵니다 MainOS 및 w:에 대 한 데이터에 대 한).
볼륨 잠긴 표시 되며 수동으로 잠금이 해제 되도록 해야 합니다. OEM DRA.pfx 인증서가 설치 되어 있는 모든 컴퓨터에서이 작업을 수행할 수 있습니다 (에 포함 된 [DeviceLockDown 샘플](https://github.com/ms-iot/security/tree/master/TurnkeySecurity)). PFX를 설치 하 고 관리 CMD 프롬프트에서 다음 명령을 실행 합니다.

* `manage-bde -unlock v: -cert -cf OEM-DRA.cer`
* `manage-bde -unlock w: -cert -cf OEM-DRA.cer`

콘텐츠를 오프 라인으로 자주 액세스 됨 해야 하는 경우 BitLocker 잠금 설정할 수 있습니다 볼륨에 대 한 초기 다음 명령을 사용 하 여 잠금을 해제 한 후:

* `manage-bde -autounlock v: -enable`
* `manage-bde -autounlock w: -enable`

### <a name="disabling-bitlocker"></a>BitLocker를 사용 하지 않도록 설정

일시적으로 BitLocker를 사용 하지 않도록 설정 해야 발생할 수 있습니다는 다음 명령 실행 하 고 IoT 장치를 사용 하 여 원격 PowerShell 세션을 시작할: `sectask.exe -disable`합니다.  
**참고:** 예약 된 암호화 작업이 비활성화 되어 있지 않으면 장치 암호화 후속 장치 부팅 시 다시 활성화 됩니다.

### <a name="disabling-device-guard"></a>Device Guard를 사용 하지 않도록 설정

턴키 보안 스크립트 폴더에 SIPolicyOn.p7b 및 SIPolicyOff.p7b 파일을 생성합니다.
wm.xml는 SIPolicyOn.p7b 패키지 및 SIPolicy.p7b으로 시스템에 배치 합니다.

예를 들어 다음과 같은 가치를 제공해야 합니다.

```
C:\src\iot-adk-addonkit.db410c\TurnkeySecurity\QCDB\Output\DeviceGuard\Security.DeviceGuard.wm.xml
…
    <files>
        <file
            destinationDir="$(runtime.bootDrive)\efi\microsoft\boot"
            source="SIPolicyOn.p7b"
            name="SIPolicy.p7b" />
    </files>
..

```

SIPolicyOff.p7b 파일을 사용 하는 SIPolicy.p7b으로 배치 하는 패키지를 만든 경우이 패키지를 적용 및 Device Guard가 해제 됩니다.



