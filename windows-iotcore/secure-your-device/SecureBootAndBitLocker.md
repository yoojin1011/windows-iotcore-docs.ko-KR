---
title: 보안 부팅, BitLocker 및 Windows 10 IoT Core Device Guard를 사용 하도록 설정
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 보안 부팅, BitLocker 및 Windows 10 IoT Core Device Guard를 사용 하도록 설정 하는 방법 알아보기
keywords: windows iot, 보안 부팅, BitLocker, 턴키 보안 장치 가드, 보안
ms.openlocfilehash: 26e0949dd8ee0a8cfec8aeafee3908a3ade86293
ms.sourcegitcommit: 9ec4716afde25fdc8b94f7c0794448501f451b55
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/14/2019
ms.locfileid: "67142358"
---
# <a name="enabling-secure-boot-bitlocker-and-device-guard-on-windows-10-iot-core"></a>보안 부팅, BitLocker 및 Windows 10 IoT Core Device Guard를 사용 하도록 설정

Windows 10 IoT Core UEFI 보안 부팅, BitLocker 장치 암호화 및 Device Guard와 같은 보안 기능 제공을 포함합니다.  다양 한 유형의 공격에 복원 력 있는 Windows IoT 장치로 완벽 하 게 잠겨 만드는 이러한 장치 작성기 데 도움이 됩니다.  함께 이러한 기능은 플랫폼을 알 수 없는 이진 파일을 잠그지 및 장치 암호화를 사용 하 여 사용자 데이터를 보호 하는 동안 정의 된 방식으로 시작 됩니다 보장 하는 최적의 보호를 제공 합니다.

## <a name="boot-order"></a>부팅 순서

IoT 장치에 대 한 안전한 플랫폼을 제공 하는 개별 구성 요소 자세히 살펴 보겠습니다 수 전에 부팅 순서를 Windows 10 IoT Core 장치에 대 한 이해가 필요 합니다.

다음 세 가지 주요 영역에서 IoT 장치를 때 발생 하는 OS 커널 로드 하 고 설치 된 응용 프로그램을 실행 하려면까지 기반 합니다.

* 플랫폼 보안 부팅
* Unified Extensible Firmware (UEFI) 인터페이스 보안 부팅
* Windows 코드 무결성

![부팅 순서](../media/SecureBootAndBitLocker/BootOrder.jpg)

Windows 10 부팅 프로세스에 대 한 추가 정보를 찾을 수 있습니다 [여기](https://docs.microsoft.com/windows/security/information-protection/secure-the-windows-10-boot-process)합니다.

## <a name="locking-down-iot-devices"></a>잠금 다운 IoT 장치

Windows IoT 장치를 잠그고 순서로 다음과 같은 고려 사항이 수행 되어야 합니다.

### <a name="platform-secure-boot"></a>플랫폼 보안 부팅

전체 부팅 프로세스의 첫 번째 단계는 로드 하 고 펌웨어에 하드웨어를 초기화 하는 부팅 로더를 실행 하는 장치를 처음 켤 때의 devies 및 응급 깜박이 기능을 제공 합니다. UEFI 환경을 로드 하 고 컨트롤을 통해 전달 됩니다.

이러한 펌웨어 부팅 로더 SoC 관련 되므로 적절 한 장치 제조업체에 있는 장치에 만들어진 이러한 부팅 로더를 사용 해야 합니다.

### <a name="uefi-secure-boot"></a>UEFI 보안 부팅

UEFI 보안 부팅 지점인 첫 번째 정책 적용, 및 UEFI에 있습니다.  시스템 펌웨어 드라이버, 옵션 rom을 보유, UEFI 드라이버 또는 응용 프로그램 및 UEFI 부팅 로더 같은 지정된 된 권한으로 서명 된 바이너리만 실행할 수만 있도록 제한 합니다. 이 기능은 플랫폼에서 실행 되 고 잠재적으로의 보안 상태가 약화 되 알 수 없는 코드를 방지 합니다. 보안 부팅 루트킷과 같은 장치에 사전 부팅 맬웨어 공격의 위험을 줄입니다. 

OEM,으로 UEFI 보안 부팅 제조 시간에 IoT 장치에서 데이터베이스를 저장 해야 합니다. 이러한 데이터베이스 서명이 데이터베이스 (db), 서명을 해지 데이터베이스 (dbx) 및 등록 키 (KEK) 데이터베이스에 포함 됩니다. 이러한 데이터베이스는 장치의 펌웨어 비휘발성 RAM (RAM NV)에 저장 됩니다.

* **서명 데이터베이스 (db):** 서명자 또는 운영 체제 로더, UEFI 응용 프로그램 및 장치에서 로드할 수 있는 UEFI 드라이버의 이미지 해시 나열

* **해지 된 서명을 데이터베이스 (dbx):** 서명자 또는 운영 체제 로더, UEFI 응용 프로그램 및 UEFI 드라이버와 더 이상 신뢰할 수 있는 이미지 해시 나열 *되지* 장치에서 로드 되도록 허용 

* **등록 키 (KEK)를 데이터베이스:** 서명 서명 업데이트를 사용할 수 있으며 서명 데이터베이스를 해지 하는 키의 목록을 포함 합니다.

이러한 데이터베이스를 만들고 장치에 추가 되 면 OEM 편집에서 펌웨어를 잠그고 서명 키 (PK) 플랫폼을 생성 합니다. KEK에 대 한 업데이트에 서명 하거나 UEFI 보안 부팅을 사용 하지 않도록 설정 하려면이 키를 사용할 수 있습니다.

UEFI 보안 부팅을 수행한 단계는 다음과 같습니다.

1. 장치 전원이 켜지 면 서명을 데이터베이스 각각 서명 키 (PK) 플랫폼에 대해 확인 됩니다.
2. 펌웨어를 신뢰할 수 없는 경우 UEFI 펌웨어는 신뢰할 수 있는 펌웨어를 복원 하려면 OEM 특정 복구를 시작 합니다.
3. Windows 부팅 관리자를 로드할 수 없는 경우 펌웨어가 Windows 부팅 관리자의 백업 복사본을 부팅 하려고 합니다. 또한 실패 하면 UEFI 펌웨어 OEM 전용 업데이트 관리를 시작 합니다.
4. Windows 부팅 관리자 실행 되며 Windows 커널 디지털 서명을 확인 합니다. 신뢰할 수 있는 경우 Windows 부팅 관리자는 Windows 커널에 제어를 전달 합니다.

키 생성 및 관리 지침, 보안 부팅에 대 한 추가 정보를 사용할 수 [여기](https://technet.microsoft.com/library/dn747883.aspx)합니다.

### <a name="windows-code-integrity"></a>Windows 코드 무결성

Windows 코드 무결성 (WCI) 드라이버 또는 메모리에 로드 될 때마다 응용 프로그램의 무결성을 검사 하 여 운영 체제의 보안을 개선 합니다. CI는 두 개의 주요 구성-커널 모드 코드 무결성 (KMCI) 및 사용자 모드 코드 무결성 (UMCI)를 포함합니다.

구성 가능한 코드 무결성 (CCI)는 Windows 10 장치를 잠그고 장치 작성기를 사용 하면만 실행 하 고 서명 되 고 신뢰할 수 있는 코드를 실행할 수 있도록 하는 기능입니다.  이렇게 하려면 장치 작성기 수 코드 무결성 정책을 'golden' 장치 (하드웨어 및 소프트웨어의 최종 릴리스 버전)에 다음 보안 만들고 공장 현장에서 모든 장치에서이 정책을 적용 합니다.

코드 무결성 정책을 배포 하는 방법에 대 한 자세한 내용은 감사 및 적용, 설명서를 확인해 최신 technet [여기](https://technet.microsoft.com/itpro/windows/keep-secure/deploy-code-integrity-policies-steps)합니다.

Windows 코드 무결성을 수행한 단계는 다음과 같습니다.

1. Windows 커널에 로드 하기 전에 서명 데이터베이스에 대해 다른 모든 구성 요소 확인 합니다. 시작 파일, 드라이버 및 ELAM (맬웨어 방지 조기 실행-)이 포함 됩니다.
2. Windows 커널 시작 프로세스의 신뢰할 수 있는 구성 요소를 로드 하 고 신뢰할 수 없는 구성 요소 로드 금지 됩니다.
3. Windows 10 IoT Core 운영 체제 설치 된 모든 응용 프로그램과 함께 로드합니다.

### <a name="bitlocker-device-encryption"></a>BitLocker 장치 암호화

Windows 10 IoT Core 경량 버전의 BitLocker 장치 암호화를 오프 라인 공격 으로부터 IoT 장치가 보호도 구현 합니다. 이 기능은 필요한 os 시작 전 프로토콜을 포함 하 여 필요한 측정을 수행 하는 UEFI의 플랫폼에서 TPM의 존재에 강력한 종속성을 갖습니다. 이러한 os 시작 전 측정 OS 나중에 OS가 시작 하는 방법을; 한 명확한 기록이 확인 그러나 실행 제한을 적용 하지 않습니다.

> [!TIP]
> Windows 10 IoT Core 대 한 BitLocker 기능을 사용할 수 있는 모든 NTFS 데이터 볼륨을 바인딩하는 동안 자동 NTFS 기반 OS 볼륨 암호화를 위한 수 있습니다. 이 위해 EFIESP 볼륨 GUID로 설정 되어 있는지 확인 하는 데 필요한 것 _C12A7328-F81F-11D2-BA4B-00A0C93EC93B_합니다.

### <a name="device-guard-on-windows-iot-core"></a>Windows IoT Core에서 device Guard

대부분의 IoT 장치는 고정 함수 장치로 빌드됩니다. 이 장치 작성기는 펌웨어, 운영 체제, 드라이버 및 응용 프로그램 특정된 장치에서 실행 되어야 합니다 정확히 알고 있는 것을 의미 합니다. 이 정보를 수 있습니다만 알려져 있고 신뢰할 수 있는 코드의 실행을 허용 하 여 IoT 장치를 완벽 하 게 잠금에 사용 합니다. Windows 10 IoT Core device Guard는 잠긴 장치에서 알 수 없거나 신뢰할 수 없는 실행 코드를 실행할 수 없음을 확인 하 여 IoT 장치를 보호할 수 있습니다.


## <a name="turnkey-security-on-iot-core"></a>IoT Core에 대 한 턴키 보안

IoT Core 장치에 대 한 주요 보안 기능의 간편한 사용을 위해 Microsoft는 제공 하는 [턴키 보안 패키지]( https://github.com/ms-iot/security/tree/master/TurnkeySecurity) 장치 작성기 빌드할 수 있는 완벽 하 게 IoT 장치를 잠글 합니다. 이 패키지에 도움이 됩니다.

* 보안 부팅 키 프로 비전 하 고 지원 되는 IoT 플랫폼에서이 기능을 사용 하도록 설정
* BitLocker를 사용 하 여 장치 암호화의 설정 및 구성
* 시작만 서명 된 응용 프로그램 및 드라이버를 실행할 수 있도록 장치 잠금

다음 단계를 사용 하 여 잠금 이미지를 만드는 프로세스를 통해 이어질는 [턴키 보안 패키지]( https://github.com/ms-iot/security/tree/master/TurnkeySecurity)

![잠금 이미지 만들기](../media/SecurityFlowAndCertificates/ImageLockDown.png)

### <a name="prerequisites"></a>사전 요구 사항

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

5. 구성 _settings.xml_

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
    * SecureBoot: 시도 `bcdedit /debug on` , 값 보안 부팅 정책에 의해 보호 되는 내용의 오류가 표시 됩니다
    * BitLocker: 실행할 `start /wait sectask.exe -waitencryptcomplete:1`ERRORLEVEL 있으면 `-2147023436` (ERROR_TIMEOUT) 한 다음 암호화가 완료 되지 않습니다. Sectask.exe.cmd 파일에서 실행 하는 경우 생략 된 `start /wait`합니다.
    * DeviceGuard: 모든 부호 없는 이진 또는 SIPolicy 목록에 없는 인증서로 서명 된 이진 파일을 실행 하 고 실행 해 서 실패 하는지를 확인 합니다.

### <a name="generate-lockdown-image"></a>잠금 이미지 생성

앞에서 정의한 설정에 따라 작업 하는 잠금 패키지 유효성 검사 후 포함할 수 있습니다 이러한 패키지를 이미지에 따라는 아래 단계를 제공 합니다. 읽기를 [IoT 제조 가이드](https://aka.ms/iotcoreguide) 사용자 지정 이미지 만들기 지침에 대 한 합니다.

1. 작업 영역 디렉터리에 생성 된 출력 디렉터리에서 다음 파일 업데이트
    * SecureBoot : `Copy ..\Output\SecureBoot\*.bin  ..\Workspace\Common\Packages\Security.SecureBoot`
      * SetVariable_db.bin
      * SetVariable_kek.bin
      * SetVariable_pk.bin
    * BitLocker : `Copy ..\Output\Bitlocker\*.* ..\Workspace\Common\Packages\Security.Bitlocker`
      * DETask.xml
      * Security.Bitlocker.wm.xml
      * setup.bitlocker.cmd
    * DeviceGuard : `Copy ..\Output\DeviceGuard\*.*  ..\Workspace\Common\Packages\Security.DeviceGuard`
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

> [!NOTE]
> 예약 된 암호화 작업이 비활성화 되어 있지 않으면 장치 암호화 후속 장치 부팅 시 다시 활성화 됩니다.


