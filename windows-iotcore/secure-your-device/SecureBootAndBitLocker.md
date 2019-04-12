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
# <a name="enabling-secure-boot-bitlocker-and-device-guard-on-windows-10-iot-core"></a><span data-ttu-id="37905-104">보안 부팅, BitLocker 및 Windows 10 IoT Core Device Guard를 사용 하도록 설정</span><span class="sxs-lookup"><span data-stu-id="37905-104">Enabling Secure Boot, BitLocker, and Device Guard on Windows 10 IoT Core</span></span>

## <a name="introduction"></a><span data-ttu-id="37905-105">소개</span><span class="sxs-lookup"><span data-stu-id="37905-105">Introduction</span></span>

<span data-ttu-id="37905-106">크리에이터 업데이트의 릴리스부터 Windows 10 IoT Core UEFI 보안 부팅, BitLocker 장치 암호화 및 Device Guard를 포함 하는 보안 기능 제품을 개선 합니다.</span><span class="sxs-lookup"><span data-stu-id="37905-106">With the release of Creators Update, Windows 10 IoT Core improves its security feature offerings to include UEFI Secure Boot, BitLocker Device Encryption and Device Guard.</span></span>  <span data-ttu-id="37905-107">다양 한 유형의 공격에 복원 력 있는 Windows IoT 장치로 완벽 하 게 잠겨 만드는 장치 작성기 수는 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37905-107">These will allow device builders in creating fully locked down Windows IoT devices that are resilient to many different types of attacks.</span></span>  <span data-ttu-id="37905-108">함께 이러한 기능은 플랫폼을 알 수 없는 이진 파일을 잠그지 및 장치 암호화를 사용 하 여 사용자 데이터를 보호 하는 동안 정의 된 방식으로 시작 됩니다 보장 하는 최적의 보호를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="37905-108">Together, these features provide the optimal protection that ensures that a platform will launch in a defined way, while locking out unknown binaries and protecting user data through the use of device encryption.</span></span>

### <a name="secure-boot"></a><span data-ttu-id="37905-109">보안 부팅</span><span class="sxs-lookup"><span data-stu-id="37905-109">Secure Boot</span></span>

<span data-ttu-id="37905-110">UEFI 보안 부팅은 UEFI에 있는 첫 번째 정책 적용 지점입니다.</span><span class="sxs-lookup"><span data-stu-id="37905-110">UEFI Secure Boot is the first policy enforcement point, located in UEFI.</span></span>  <span data-ttu-id="37905-111">지정 된 인증 기관에서 서명 된 바이너리만 실행할 수만 있도록 시스템을 제한 합니다.</span><span class="sxs-lookup"><span data-stu-id="37905-111">It restricts the system to only allow execution of binaries signed by a specified authority.</span></span> <span data-ttu-id="37905-112">이 기능은 플랫폼에서 실행 되 고 잠재적으로의 보안 상태가 약화 되 알 수 없는 코드를 방지 합니다.</span><span class="sxs-lookup"><span data-stu-id="37905-112">This feature prevents unknown code from being executed on the platform and potentially weakening the security posture of it.</span></span>

### <a name="bitlocker-device-encryption"></a><span data-ttu-id="37905-113">BitLocker 장치 암호화</span><span class="sxs-lookup"><span data-stu-id="37905-113">BitLocker Device Encryption</span></span>

<span data-ttu-id="37905-114">Windows 10 IoT Core 경량 버전의 BitLocker 장치 암호화를 오프 라인 공격 으로부터 IoT 장치가 보호도 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="37905-114">Windows 10 IoT Core also implements a lightweight version of BitLocker Device Encryption, protecting IoT devices against offline attacks.</span></span>  <span data-ttu-id="37905-115">이 기능은 preOS 프로토콜을 포함 하 여 필요한 측정을 수행 하는 UEFI의 플랫폼에서 TPM의 존재에 강력한 종속성을 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="37905-115">This capability has a strong dependency on the presence of a TPM on the platform, including the necessary preOS protocol in UEFI that conducts the necessary measurements.</span></span> <span data-ttu-id="37905-116">이러한 preOS 측정을 갖도록 OS 나중에 OS가 시작 하는 방법을; 한 명확한 기록이 그러나 실행 제한을 적용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="37905-116">These preOS measurements ensure that the OS later has a definitive record of how the OS was launched; however, it does not enforce any execution restrictions.</span></span>

> [!TIP]
> <span data-ttu-id="37905-117">Windows 10 IoT Core 대 한 BitLocker 기능을 사용할 수 있는 모든 NTFS 데이터 볼륨을 바인딩하는 동안 자동 NTFS 기반 OS 볼륨 암호화를 위한 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37905-117">BitLocker functionality on Windows 10 IoT Core allows for automatic encryption of NTFS-based OS volume while binding all available NTFS data volumes to it.</span></span>  <span data-ttu-id="37905-118">이 위해 EFIESP 볼륨 GUID로 설정 되어 있는지 확인 하는 데 필요한 것 _C12A7328-F81F-11D2-BA4B-00A0C93EC93B_합니다.</span><span class="sxs-lookup"><span data-stu-id="37905-118">For this, it’s necessary to ensure that the EFIESP volume GUID is set to _C12A7328-F81F-11D2-BA4B-00A0C93EC93B_.</span></span>

### <a name="device-guard-on-windows-iot-core"></a><span data-ttu-id="37905-119">Windows IoT Core에서 device Guard</span><span class="sxs-lookup"><span data-stu-id="37905-119">Device Guard on Windows IoT Core</span></span>

<span data-ttu-id="37905-120">대부분의 IoT 장치는 고정 함수 장치로 빌드됩니다.</span><span class="sxs-lookup"><span data-stu-id="37905-120">Most IoT devices are built as fixed-function devices.</span></span>  <span data-ttu-id="37905-121">이 장치 작성기는 펌웨어, 운영 체제, 드라이버 및 응용 프로그램 특정된 장치에서 실행 되어야 합니다 정확히 알고 있는 것을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="37905-121">This implies that device builders know exactly which firmware, operating system, drivers and applications should be running on a given device.</span></span>  <span data-ttu-id="37905-122">이 정보를 수 있습니다만 알려져 있고 신뢰할 수 있는 코드의 실행을 허용 하 여 IoT 장치를 완벽 하 게 잠금에 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="37905-122">In turn, this information can be used to fully lockdown an IoT device by only allowing execution of known and trusted code.</span></span>  <span data-ttu-id="37905-123">Windows 10 IoT Core device Guard는 잠긴 장치에서 알 수 없거나 신뢰할 수 없는 실행 코드를 실행할 수 없음을 확인 하 여 IoT 장치를 보호할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37905-123">Device Guard on Windows 10 IoT Core can help protect IoT devices by ensuring that unknown or untrusted executable code cannot be run on locked-down devices.</span></span>

## <a name="locking-down-iot-devices"></a><span data-ttu-id="37905-124">잠금 다운 IoT 장치</span><span class="sxs-lookup"><span data-stu-id="37905-124">Locking-down IoT Devices</span></span>

<span data-ttu-id="37905-125">Windows IoT 장치를 잠그고 순서로 다음 고려 사항은 만들어야 하는 중...</span><span class="sxs-lookup"><span data-stu-id="37905-125">In order to lockdown a Windows IoT device, the following considerations must be made...</span></span>

### <a name="uefi-platform--secure-boot"></a><span data-ttu-id="37905-126">보안 부팅 및 UEFI 플랫폼</span><span class="sxs-lookup"><span data-stu-id="37905-126">UEFI Platform & Secure Boot</span></span>

<span data-ttu-id="37905-127">Device Guard 기능을 활용 하기 위해 부팅 이진 파일 및 UEFI 펌웨어 서명 되 고 변조 될 수 없음을 확인 하는 데 필요한 됩니다.</span><span class="sxs-lookup"><span data-stu-id="37905-127">In order to leverage Device Guard capabilities, it is necessary to ensure that the boot binaries and UEFI firmware are signed and cannot be tampered with.</span></span>  <span data-ttu-id="37905-128">UEFI 보안 부팅은 UEFI에 있는 첫 번째 정책 적용 지점입니다.</span><span class="sxs-lookup"><span data-stu-id="37905-128">UEFI Secure Boot is the first policy enforcement point, located in UEFI.</span></span>  <span data-ttu-id="37905-129">지정된 된 권한으로 로그인 하는 부팅 이진 파일의 실행만 사용할 수 있도록 시스템을 제한 하 여 변조를 방지 합니다.</span><span class="sxs-lookup"><span data-stu-id="37905-129">It prevents tampering by restricting the system to only allow execution of boot binaries signed by a specified authority.</span></span> <span data-ttu-id="37905-130">키 생성 및 관리 지침, 보안 부팅에 대 한 추가 정보를 사용할 수 [여기](https://technet.microsoft.com/library/dn747883.aspx)합니다.</span><span class="sxs-lookup"><span data-stu-id="37905-130">Additional details on Secure Boot, along with key creation and management guidance, is available [here](https://technet.microsoft.com/library/dn747883.aspx).</span></span>

### <a name="configurable-code-integrity-cci"></a><span data-ttu-id="37905-131">구성 가능한 코드 무결성 (CCI)</span><span class="sxs-lookup"><span data-stu-id="37905-131">Configurable Code Integrity (CCI)</span></span>

<span data-ttu-id="37905-132">응용 프로그램 메모리에 로드 될 때마다 드라이버의 무결성을 확인 하 여 운영 체제의 보안을 강화 하는 코드 무결성 (CI).</span><span class="sxs-lookup"><span data-stu-id="37905-132">Code Integrity (CI) improves the security of the operating system by validating the integrity of a driver or application each time it is loaded into memory.</span></span> <span data-ttu-id="37905-133">CI는 두 개의 주요 구성-커널 모드 코드 무결성 (KMCI) 및 사용자 모드 코드 무결성 (UMCI)를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="37905-133">CI contains two main components - Kernel Mode Code Integrity (KMCI) and User Mode Code Integrity (UMCI).</span></span>

<span data-ttu-id="37905-134">구성 가능한 코드 무결성 (CCI)는 Windows 10 장치를 잠그고 장치 작성기를 사용 하면만 실행 하 고 서명 되 고 신뢰할 수 있는 코드를 실행할 수 있도록 하는 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="37905-134">Configurable Code Integrity (CCI) is a feature in Windows 10 that allows device builders to lockdown a device and only allow it to run and execute code that is signed and trusted.</span></span>  <span data-ttu-id="37905-135">이렇게 하려면 장치 작성기 수 코드 무결성 정책을 'golden' 장치 (하드웨어 및 소프트웨어의 최종 릴리스 버전)에 다음 보안 만들고 공장 현장에서 모든 장치에서이 정책을 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="37905-135">To do so, device builders can create a code integrity policy on a 'golden' device (final release version of hardware and software) and then secure and apply this policy on all devices on the factory floor.</span></span>

<span data-ttu-id="37905-136">코드 무결성 정책을 배포 하는 방법에 대 한 자세한 내용은 감사 및 적용, 설명서를 확인해 최신 technet [여기](https://technet.microsoft.com/itpro/windows/keep-secure/deploy-code-integrity-policies-steps)합니다.</span><span class="sxs-lookup"><span data-stu-id="37905-136">To learn more about deploying code integrity policies, auditing and enforcement, check out the latest technet documentation [here](https://technet.microsoft.com/itpro/windows/keep-secure/deploy-code-integrity-policies-steps).</span></span>

## <a name="turnkey-security-on-iot-core"></a><span data-ttu-id="37905-137">IoT Core에 대 한 턴키 보안</span><span class="sxs-lookup"><span data-stu-id="37905-137">Turnkey Security on IoT Core</span></span>

<span data-ttu-id="37905-138">Microsoft는 턴키 ' 보안 패키지 '을 제공 하는 데 쉽게 사용 IoT Core 장치에서 주요 보안 기능을 위해 장치 작성기 빌드할 수 있는 IoT 장치를 완벽 하 게 잠겨 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37905-138">To facilitate easy enablement of key security features on IoT Core devices, Microsoft is providing a turnkey 'Security Package' that allows device builders to build fully locked down IoT devices.</span></span>  <span data-ttu-id="37905-139">이 패키지에 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="37905-139">This package will help with:</span></span>

* <span data-ttu-id="37905-140">보안 부팅 키 프로 비전 하 고 지원 되는 IoT 플랫폼에서이 기능을 사용 하도록 설정</span><span class="sxs-lookup"><span data-stu-id="37905-140">Provisioning Secure Boot keys and enabling the feature on supported IoT platforms</span></span>
* <span data-ttu-id="37905-141">BitLocker를 사용 하 여 장치 암호화의 설정 및 구성</span><span class="sxs-lookup"><span data-stu-id="37905-141">Setup and configuration of device encryption using BitLocker</span></span> 
* <span data-ttu-id="37905-142">시작만 서명 된 응용 프로그램 및 드라이버를 실행할 수 있도록 장치 잠금</span><span class="sxs-lookup"><span data-stu-id="37905-142">Initiating device lockdown to only allow execution of signed applications and drivers</span></span>

### <a name="pre-requisites"></a><span data-ttu-id="37905-143">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="37905-143">Pre-requisites</span></span>

* <span data-ttu-id="37905-144">Windows 10 Enterprise 실행 하는 PC</span><span class="sxs-lookup"><span data-stu-id="37905-144">A PC running Windows 10 Enterprise</span></span>
* <span data-ttu-id="37905-145">[Windows 10 SDK](https://developer.microsoft.com/en-US/windows/downloads/windows-10-sdk) -인증서 생성에 대 한 필수</span><span class="sxs-lookup"><span data-stu-id="37905-145">[Windows 10 SDK](https://developer.microsoft.com/en-US/windows/downloads/windows-10-sdk) - Required for Certificate Generation</span></span>
* <span data-ttu-id="37905-146">[Windows 10 ADK](https://developer.microsoft.com/en-us/windows/hardware/windows-assessment-deployment-kit) -CAB 생성을 위한 필수 항목</span><span class="sxs-lookup"><span data-stu-id="37905-146">[Windows 10 ADK](https://developer.microsoft.com/en-us/windows/hardware/windows-assessment-deployment-kit) - Required for CAB generation</span></span>
* <span data-ttu-id="37905-147">참조 하는 플랫폼 전달 펌웨어, OS, 드라이버 및 응용 프로그램을 사용 하 여 릴리스 하드웨어 해야 최종 잠금에 대 한</span><span class="sxs-lookup"><span data-stu-id="37905-147">Reference platform - release hardware with shipping firmware, OS, drivers and applications will be required for final lockdown</span></span>

### <a name="development-iot-devices"></a><span data-ttu-id="37905-148">IoT 장치 개발</span><span class="sxs-lookup"><span data-stu-id="37905-148">Development IoT Devices</span></span>

<span data-ttu-id="37905-149">Windows 10 IoT Core 수백 대의 장치에서 사용 되는 다양 한 silicons를 사용 하 여 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="37905-149">Windows 10 IoT Core works with various silicons that are utilized in hundreds of devices.</span></span> <span data-ttu-id="37905-150">[IoT 개발 장치 제안](../learn-about-hardware/SoCsAndCustomBoards.md), 기본적으로 보안 부팅, 계획 부팅, BitLocker 및 Device Guard 기능과 함께 펌웨어 TPM 기능을 제공 하는 다음:</span><span class="sxs-lookup"><span data-stu-id="37905-150">Of the [suggested IoT development devices](../learn-about-hardware/SoCsAndCustomBoards.md), the following provide firmware TPM functionality out of the box, along with Secure Boot, Measured Boot, BitLocker and Device Guard capabilities:</span></span>

* <span data-ttu-id="37905-151">Qualcomm DragonBoard 410 c</span><span class="sxs-lookup"><span data-stu-id="37905-151">Qualcomm DragonBoard 410c</span></span>

    <span data-ttu-id="37905-152">보안 부팅을 사용 하도록 설정 하기 위해 RPMB 프로 비전 해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37905-152">In order to enable Secure Boot, it may be necessary to provision RPMB.</span></span> <span data-ttu-id="37905-153">eMMC Windows 10 IoT Core 사용 하 여 플래시 됨 된가 되 면 (지침에 따라 [여기](https://docs.microsoft.com/windows/iot-core/tutorials/quickstarter/devicesetup#using-the-iot-dashboard-dragonboard-410c), 키를 눌러 [Power] + [Vol +] + [Vol-]을 선택 "프로 비전 RPMB" BDS 메뉴에서 전원을 켤 때 장치에서 동시에 합니다.</span><span class="sxs-lookup"><span data-stu-id="37905-153">Once the eMMC has been flashed with Windows 10 IoT Core (as per instructions [here](https://docs.microsoft.com/windows/iot-core/tutorials/quickstarter/devicesetup#using-the-iot-dashboard-dragonboard-410c), press [Power] + [Vol+] + [Vol-] simultaneously on the device when powering up and select "Provision RPMB" from the BDS menu.</span></span> *<span data-ttu-id="37905-154">이 단계를 취소할 수는 note 하십시오.</span><span class="sxs-lookup"><span data-stu-id="37905-154">Please note that this is an irreversible step.</span></span>*

* <span data-ttu-id="37905-155">Intel MinnowBoardMax</span><span class="sxs-lookup"><span data-stu-id="37905-155">Intel MinnowBoardMax</span></span>

    <span data-ttu-id="37905-156">Intel의 MinnowBoard 최대 펌웨어 버전 0.82 이상 이어야 합니다 (가져오기의 [최신 펌웨어로](https://firmware.intel.com/projects/minnowboard-max)).</span><span class="sxs-lookup"><span data-stu-id="37905-156">For Intel's MinnowBoard Max, firmware version must be 0.82 or higher (get the [latest firmware](https://firmware.intel.com/projects/minnowboard-max)).</span></span> <span data-ttu-id="37905-157">TPM 기능을 사용 하려면 키보드와 디스플레이 보드의 전원을 연결 및 UEFI 설치 F2 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="37905-157">To enable TPM capabilities, power up board with a keyboard & display attached and press F2 to enter UEFI setup.</span></span> <span data-ttu-id="37905-158">로 이동 _Device Manager 시스템 설정-> 보안 구성-> PTT->_ 로 설정 하 고  _&lt;사용 하도록 설정&gt;_ 합니다.</span><span class="sxs-lookup"><span data-stu-id="37905-158">Go to _Device Manager -> System Setup -> Security Configuration -> PTT_ and set it to _&lt;Enable&gt;_.</span></span> <span data-ttu-id="37905-159">F10 키를 눌러 변경 내용을 저장 하는 플랫폼의 다시 부팅을 사용 하 여 계속 합니다.</span><span class="sxs-lookup"><span data-stu-id="37905-159">Press F10 to save changes and proceed with a reboot of the platform.</span></span>

> [!NOTE]
> <span data-ttu-id="37905-160">Raspberry Pi 2 또는 3 TPM을 지원 하지 않으며 따라서에서는 잠금 시나리오를 구성할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="37905-160">Raspberry Pi 2 nor 3 do not support TPM and so we cannot configure Lockdown scenarios.</span></span>

### <a name="generate-lockdown-packages"></a><span data-ttu-id="37905-161">잠금 패키지를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="37905-161">Generate Lockdown Packages</span></span>

1. <span data-ttu-id="37905-162">다운로드 합니다 [DeviceLockDown 스크립트](https://github.com/ms-iot/security/tree/master/TurnkeySecurity) 모든 추가 도구 및 구성 하 고 장치를 잠그는 데 필요한 스크립트를 포함 하는 패키지</span><span class="sxs-lookup"><span data-stu-id="37905-162">Download the [DeviceLockDown Script](https://github.com/ms-iot/security/tree/master/TurnkeySecurity) package, which contains all of the additional tools and scripts required for configuring and locking down devices</span></span>
2. <span data-ttu-id="37905-163">Windows 10 pc를 관리 PS (PowerShell) 콘솔을 시작 하 고 다운로드 한 스크립트의 위치로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="37905-163">Start an Administrative PowerShell (PS) console on your Windows 10 PC and navigate to the location of the downloaded script.</span></span>
3. <span data-ttu-id="37905-164">(잠금 해제 된 이미지를 실행) 하 여 참조 하드웨어 플랫폼을 사용 하 여 네트워크 공유를 통해 PC에 탑재</span><span class="sxs-lookup"><span data-stu-id="37905-164">Mount your reference hardware platform (running the unlocked image) to your PC via network share using</span></span>

    ```powershell
    net use \\a.b.c.d\c$ /user:username password
    ```

4. <span data-ttu-id="37905-165">사용 하 여 장치에 대 한 키를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="37905-165">Generate keys for your device using</span></span>

    ```powershell
    .\GenerateKeys.ps1 -OemName '<your oem name>' -outputPath '<output directory>'
    ```

    * <span data-ttu-id="37905-166">키 및 인증서를 적절 한 접미사를 사용 하 여 지정 된 출력 폴더에 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="37905-166">The keys and certificates are generated in the specified output folder with appropriate suffix.</span></span>
    * <span data-ttu-id="37905-167">**생성 된 키를 보호할** 장치는 이진 파일을 신뢰 하는 대로 잠금 후에 이러한 키를 사용 하 여 서명 합니다.</span><span class="sxs-lookup"><span data-stu-id="37905-167">**Secure your generated keys** as the device will trust binaries signed with these keys only after lockdown.</span></span>
    * <span data-ttu-id="37905-168">이 단계를 건너뛸 수 있습니다를 미리 생성 된 키를 사용 하 여 테스트 전용</span><span class="sxs-lookup"><span data-stu-id="37905-168">You may skip this step and use the pre-generated keys for testing only</span></span>

5. <span data-ttu-id="37905-169">Pfx 파일에서 직접 클릭 하거나 사용 하 여 생성 된.pfx 인증서를 설치할는 아래 powershell 명령을</span><span class="sxs-lookup"><span data-stu-id="37905-169">Install the generated .pfx certificates by clicking on the pfx files directly or using the below powershell command</span></span>

    ```powershell
    Import-PfxCertificate -FilePath $pfxfile -CertStoreLocation Cert:\CurrentUser\My
    ```

6. <span data-ttu-id="37905-170">구성 _settings.xml_</span><span class="sxs-lookup"><span data-stu-id="37905-170">Configure _settings.xml_</span></span>

    * <span data-ttu-id="37905-171">일반 섹션: 패키지 디렉터리를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="37905-171">General section : Specify the package directories</span></span>
    * <span data-ttu-id="37905-172">도구 섹션: 도구에 대 한 경로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="37905-172">Tools section : Set the path for the tools</span></span>
        * <span data-ttu-id="37905-173">Windows10KitsRoot</span><span class="sxs-lookup"><span data-stu-id="37905-173">Windows10KitsRoot</span></span> `(e.g. <Windows10KitsRoot>C:\Program Files (x86)\Windows Kits\10\</Windows10KitsRoot>)`
        * <span data-ttu-id="37905-174">WindowsSDKVersion</span><span class="sxs-lookup"><span data-stu-id="37905-174">WindowsSDKVersion</span></span> `(e.g. <WindowsSDKVersion>10.0.15063.0</WindowsSDKVersion>)`
            * <span data-ttu-id="37905-175">컴퓨터에 설치 된 SDK 버전은</span><span class="sxs-lookup"><span data-stu-id="37905-175">SDK version installed on your machine is under</span></span> `C:\Program Files (x86)\Windows Kits\10\`
    * <span data-ttu-id="37905-176">SecureBoot 섹션: 보안 부팅 (PK 및 SB 키)에 사용할 키를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="37905-176">SecureBoot section : Specify which keys to use for secure boot (PK and SB keys)</span></span>
    * <span data-ttu-id="37905-177">BitLocker 섹션: Bitlocker 데이터 복구 (DRA 키)에 대 한 인증서를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="37905-177">BitLocker section : Specify a certificate for Bitlocker data recovery (DRA key)</span></span>
    * <span data-ttu-id="37905-178">SIPolicy 섹션: 신뢰할 수 있는 인증서를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="37905-178">SIPolicy section : Specify certs that should be trusted</span></span>
        * <span data-ttu-id="37905-179">ScanPath : 이진 파일을 검색 하는 것에 대 한 장치의 경로</span><span class="sxs-lookup"><span data-stu-id="37905-179">ScanPath : Path of the device for scanning binaries ,</span></span> `\\a.b.c.d\C$`
        * <span data-ttu-id="37905-180">업데이트: 서명자의 SIPolicy (PAUTH 키)</span><span class="sxs-lookup"><span data-stu-id="37905-180">Update   : Signer of the SIPolicy (PAUTH keys)</span></span>
        * <span data-ttu-id="37905-181">사용자: 사용자 모드 인증서 (UMCI 키)</span><span class="sxs-lookup"><span data-stu-id="37905-181">User     : User mode certificates (UMCI keys)</span></span> 
        * <span data-ttu-id="37905-182">커널: 커널 모드 (KMCI 키) 인증서</span><span class="sxs-lookup"><span data-stu-id="37905-182">Kernel   : Kernel mode certificates (KMCI keys)</span></span>
    * <span data-ttu-id="37905-183">패키징: 패키지 생성을 위한 설정 지정</span><span class="sxs-lookup"><span data-stu-id="37905-183">Packaging : Specify the settings for the package generation</span></span>

> [!IMPORTANT]
> <span data-ttu-id="37905-184">초기 개발 주기 동안 테스트를 지원 하기 위해 Microsoft에 제공 미리 생성 된 키 및 인증서 적절 한 경우.</span><span class="sxs-lookup"><span data-stu-id="37905-184">In order to assist with testing during the initial development cycle, Microsoft has provided pre-generated keys and certificates where appropriate.</span></span>  <span data-ttu-id="37905-185">즉, 신뢰할 수 있는 Microsoft 테스트, 개발 및 시험판 버전 이진 파일 간주 됩니다.</span><span class="sxs-lookup"><span data-stu-id="37905-185">This implies that Microsoft Test, Development and Pre-Release binaries are considered trusted.</span></span>  <span data-ttu-id="37905-186">최종 제품 만들기 및 이미지를 생성 하는 동안 사용할 이러한 인증서를 제거 하 고 사용자 고유의 키를 사용 하 여 장치를 완벽 하 게 잠겨 있는지 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="37905-186">During final product creation and image generation, be sure to remove these certifcates and use your own keys to ensure a fully locked down device.</span></span>

> [!TIP]
> <span data-ttu-id="37905-187">Microsoft 앱 스토어에서 앱 구성에서 Microsoft Marketplace PCA 2011 인증서를 포함 하 여 허용 될 수 있습니다 _settings.xml_:</span><span class="sxs-lookup"><span data-stu-id="37905-187">The apps from Microsoft App Store can be allowed by including the Microsoft Marketplace PCA 2011 certificate in the configuration _settings.xml_:</span></span> 
    ```xml
    <Cert>db\MicrosoftMarketPlacePCA2011.cer</Cert>              <!-- Microsoft MarketPlace PCA 2011 -->
    ```

<span data-ttu-id="37905-188">6. 필요한 패키지를 생성 하려면 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="37905-188">6.Execute the following commands to generate required packages:</span></span>

    ```powershell
    Import-Module .\IoTTurnkeySecurity.psm1
    # Generate the security packages for retail
    New-IoTTurnkeySecurity -ConfigFileName .\settings.xml
    (or)
    # Generate the security packages for test
    New-IoTTurnkeySecurity -ConfigFileName .\settings.xml -Test
    ```

### <a name="test-lockdown-packages"></a><span data-ttu-id="37905-189">잠금 패키지 테스트</span><span class="sxs-lookup"><span data-stu-id="37905-189">Test Lockdown packages</span></span>
<span data-ttu-id="37905-190">수동으로 다음 단계에 따라 잠금 해제 된 장치에 설치 하 여 생성된 된 패키지를 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37905-190">You can test the generated packages by manually installing them on a unlocked device by the following steps</span></span>

1. <span data-ttu-id="37905-191">잠금이 해제 된 이미지 (이전 단계에서 스캔 하는 데 사용 되는 이미지)를 사용 하 여 장치를 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="37905-191">Flash the device with the unlocked image (image used for scanning in earlier step).</span></span>
2. <span data-ttu-id="37905-192">장치에 연결 ([SSH를 사용 하 여](../connect-your-device/SSH.md) 알거나 [Powershell](../connect-your-device/PowerShell.md))</span><span class="sxs-lookup"><span data-stu-id="37905-192">Connect to the device ([using SSH](../connect-your-device/SSH.md) or using [Powershell](../connect-your-device/PowerShell.md))</span></span>
3. <span data-ttu-id="37905-193">예를 들어 디렉터리에 있는 장치에 다음.cab 파일을 복사</span><span class="sxs-lookup"><span data-stu-id="37905-193">Copy the following .cab files to the device under a directory e.g.</span></span> `c:\OemInstall`
    * <span data-ttu-id="37905-194">OEM.Custom.Cmd.cab</span><span class="sxs-lookup"><span data-stu-id="37905-194">OEM.Custom.Cmd.cab</span></span>
    * <span data-ttu-id="37905-195">OEM.Security.BitLocker.cab</span><span class="sxs-lookup"><span data-stu-id="37905-195">OEM.Security.BitLocker.cab</span></span>
    * <span data-ttu-id="37905-196">OEM.Security.SecureBoot.cab</span><span class="sxs-lookup"><span data-stu-id="37905-196">OEM.Security.SecureBoot.cab</span></span>
    * <span data-ttu-id="37905-197">OEM.Security.DeviceGuard.cab</span><span class="sxs-lookup"><span data-stu-id="37905-197">OEM.Security.DeviceGuard.cab</span></span>
4. <span data-ttu-id="37905-198">다음 명령을 내림 하 여 생성된 된 패키지의 준비 시작</span><span class="sxs-lookup"><span data-stu-id="37905-198">Initiate staging of the generated packages by issueing the following commands</span></span>

    ```C
    applyupdate -stage c:\OemInstall\OEM.Custom.Cmd.cab
    ```
    <span data-ttu-id="37905-199">사용자 지정 이미지를 사용 하는 경우 해야 *건너뜁니다* 이 파일을 수동으로 편집 합니다 `c:\windows\system32\oemcustomization.cmd` 에서 사용할 수 있는 내용으로 `Output\OEMCustomization\OEMCustomization.cmd` 파일</span><span class="sxs-lookup"><span data-stu-id="37905-199">If you are using custom image, then you will have to *skip* this file and manually edit the `c:\windows\system32\oemcustomization.cmd` with the contents available in `Output\OEMCustomization\OEMCustomization.cmd` file</span></span>

    ```C
    applyupdate -stage c:\OemInstall\OEM.Security.BitLocker.cab
    applyupdate -stage c:\OemInstall\OEM.Security.SecureBoot.cab
    applyupdate -stage c:\OemInstall\OEM.Security.DeviceGuard.cab

5. Finally, commit the packages via

    ```C
    applyupdate -commit
    ```

6. <span data-ttu-id="37905-200">장치가는 업데이트 패키지를 설치 하려면 OS (보여 주는 gears)으로 다시 부팅 됩니다 하 고 기본 OS를 다시 부팅 됩니다.</span><span class="sxs-lookup"><span data-stu-id="37905-200">The device will reboot into update OS (showing gears) to install the packages and will reboot again to main OS.</span></span>  <span data-ttu-id="37905-201">장치를 MainOS 되돌려 다시 부팅 보안 부팅을 사용할 및 SIPolicy 참여 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="37905-201">Once the device reboots back into MainOS, Secure Boot will be enabled and SIPolicy should be engaged.</span></span>
7. <span data-ttu-id="37905-202">Bitlocker 암호화를 활성화 하려면 다시 장치를 다시 부팅 합니다.</span><span class="sxs-lookup"><span data-stu-id="37905-202">Reboot the device again to activate the Bitlocker encryption.</span></span>
8. <span data-ttu-id="37905-203">보안 기능 테스트</span><span class="sxs-lookup"><span data-stu-id="37905-203">Test the security features</span></span>
    * <span data-ttu-id="37905-204">**SecureBoot** : 시도 `bcdedit /debug on` , 값 보안 부팅 정책에 의해 보호 되는 내용의 오류가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="37905-204">**SecureBoot** : try `bcdedit /debug on` , you will get an error stating that the value is protected by secure boot policy.</span></span>
   * <span data-ttu-id="37905-205">**BitLocker** : 유효성을 검사할 해당 bitlocker 암호화 완료 되 면 실행</span><span class="sxs-lookup"><span data-stu-id="37905-205">**BitLocker** : To validate that bitlocker encryption has been completed, run</span></span><p>
        `sectask.exe -waitenableforcompletion 1`<p>
        <span data-ttu-id="37905-206">0을 반환 하는 경우 시스템의 모든 드라이브를 만들었습니다. bitlockered 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="37905-206">If it returns 0, that means all drives on the system have been bitlockered successfully.</span></span>  <span data-ttu-id="37905-207">다른 모든 반환 코드는 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="37905-207">Any other return code is failure.</span></span><p>
        *<span data-ttu-id="37905-208">추가 구문</span><span class="sxs-lookup"><span data-stu-id="37905-208">Additional Syntax</span></span>*<p>
         `-waitenableforcompletion [timeout]` <p>
        <span data-ttu-id="37905-209">= > 모든 NTFS 볼륨에서 BitLocker 암호화 완료 될 때까지 대기 합니다.</span><span class="sxs-lookup"><span data-stu-id="37905-209">=> Wait until BitLocker encryption is completed on all NTFS volumes.</span></span><p>
        <span data-ttu-id="37905-210">= >는 데 사용 될 때까지 기다리는 시간 (초) 시간 제한입니다.</span><span class="sxs-lookup"><span data-stu-id="37905-210">=> Timeout in seconds to wait for enable to complete.</span></span><p>
        <span data-ttu-id="37905-211">= > 경우 제한 시간 지정 하지 않으면 활성화가 완료 될 때까지 또는 무기한 대기 합니다.</span><span class="sxs-lookup"><span data-stu-id="37905-211">=> If timeout not specified, it will wait indefinitely or until enable completes.</span></span><p>
        <span data-ttu-id="37905-212">이 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="37905-212">Returns:</span></span> <p>
        <span data-ttu-id="37905-213">0 : 성공적으로 완료 되는 BitLocker 암호화를 볼륨은 Bitlocker로 암호화 됨입니다.</span><span class="sxs-lookup"><span data-stu-id="37905-213">0 : BitLocker encryption successfully completed, volume is Bitlocker encrypted.</span></span><p>
        <span data-ttu-id="37905-214">ERROR_TIMEOUT: 완료 되 면 암호화 진행에서 될 때까지 기다리는 동안 시간이 초과 됩니다.</span><span class="sxs-lookup"><span data-stu-id="37905-214">ERROR_TIMEOUT: Timeout waiting for completion, encryption still in progress.</span></span><p>
        <span data-ttu-id="37905-215">오류 / 기타 코드: 비트 보관 서비스를 반환한 실패 오류 코드를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="37905-215">Failure/Other code: returns the failure error code returned by the bit locker service.</span></span>

    * <span data-ttu-id="37905-216">**DeviceGuard** : 모든 부호 없는 이진 또는 SIPolicy 목록에 없는 인증서로 서명 된 이진 파일을 실행 하 고 실행 해 서 실패 하는지를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="37905-216">**DeviceGuard** : Run any unsigned binary or a binary signed with certificate not in the SIPolicy list and confirm that it fails to run.</span></span>

### <a name="generate-lockdown-image"></a><span data-ttu-id="37905-217">잠금 이미지 생성</span><span class="sxs-lookup"><span data-stu-id="37905-217">Generate Lockdown image</span></span>

<span data-ttu-id="37905-218">앞에서 정의한 설정에 따라 작업 하는 잠금 패키지 유효성 검사 후 포함할 수 있습니다 이러한 패키지를 이미지에 따라는 아래 단계를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="37905-218">After validating that the lockdown packages are working as per the settings defined earlier, you can then include these packages into the image by following the below given steps.</span></span> <span data-ttu-id="37905-219">읽기 [IoT 제조 가이드](https://aka.ms/iotcoreguide) 사용자 지정 이미지 만들기 지침에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="37905-219">Read [IoT manufacturing guide](https://aka.ms/iotcoreguide) for custom image creation instructions.</span></span>

1. <span data-ttu-id="37905-220">작업 영역 디렉터리에 생성 된 출력 디렉터리에서 다음 파일 업데이트</span><span class="sxs-lookup"><span data-stu-id="37905-220">In the workspace directory, update the following files from the generated output directory above</span></span>
    * <span data-ttu-id="37905-221">SecureBoot:</span><span class="sxs-lookup"><span data-stu-id="37905-221">SecureBoot :</span></span> `Copy ..\Output\SecureBoot\*.bin  ..\Workspace\Common\Packages\Security.SecureBoot`
      * <span data-ttu-id="37905-222">SetVariable_db.bin</span><span class="sxs-lookup"><span data-stu-id="37905-222">SetVariable_db.bin</span></span>
      * <span data-ttu-id="37905-223">SetVariable_kek.bin</span><span class="sxs-lookup"><span data-stu-id="37905-223">SetVariable_kek.bin</span></span>
      * <span data-ttu-id="37905-224">SetVariable_pk.bin</span><span class="sxs-lookup"><span data-stu-id="37905-224">SetVariable_pk.bin</span></span>
    * <span data-ttu-id="37905-225">BitLocker:</span><span class="sxs-lookup"><span data-stu-id="37905-225">BitLocker :</span></span> `Copy ..\Output\Bitlocker\*.* ..\Workspace\Common\Packages\Security.Bitlocker`
      * <span data-ttu-id="37905-226">DETask.xml</span><span class="sxs-lookup"><span data-stu-id="37905-226">DETask.xml</span></span>
      * <span data-ttu-id="37905-227">Security.Bitlocker.wm.xml</span><span class="sxs-lookup"><span data-stu-id="37905-227">Security.Bitlocker.wm.xml</span></span>
      * <span data-ttu-id="37905-228">setup.bitlocker.cmd</span><span class="sxs-lookup"><span data-stu-id="37905-228">setup.bitlocker.cmd</span></span>
    * <span data-ttu-id="37905-229">DeviceGuard:</span><span class="sxs-lookup"><span data-stu-id="37905-229">DeviceGuard :</span></span> `Copy ..\Output\DeviceGuard\*.*  ..\Workspace\Common\Packages\Security.DeviceGuard`
      * <span data-ttu-id="37905-230">SIPolicyOn.p7b</span><span class="sxs-lookup"><span data-stu-id="37905-230">SIPolicyOn.p7b</span></span>
      * <span data-ttu-id="37905-231">SIPolicyOff.p7b</span><span class="sxs-lookup"><span data-stu-id="37905-231">SIPolicyOff.p7b</span></span>
  
2. <span data-ttu-id="37905-232">RetailOEMInput.xml 및 TestOEMInput.xml 잠금 패키지 기능 ID 사용 하 여 ProductName 디렉터리 아래에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="37905-232">Add RetailOEMInput.xml and TestOEMInput.xml under the ProductName directory with lockdown package feature ID</span></span>
    * `<Feature>SEC_BITLOCKER</Feature>`
    * `<Feature>SEC_SECUREBOOT</Feature>`
    * `<Feature>SEC_DEVICEGUARD</Feature>`
3. <span data-ttu-id="37905-233">이미지를 다시 생성</span><span class="sxs-lookup"><span data-stu-id="37905-233">Re-generate Image</span></span>
    * `buildpkg all` <span data-ttu-id="37905-234">(위의 정책 파일에 따라 새 잠금 패키지 생성)</span><span class="sxs-lookup"><span data-stu-id="37905-234">(this generates new lockdown packages based on above policy files)</span></span>
    * `buildimage ProductName test(or)retail`  <span data-ttu-id="37905-235">(새 Flash.ffu 생성)</span><span class="sxs-lookup"><span data-stu-id="37905-235">(this generates new Flash.ffu)</span></span>
4. <span data-ttu-id="37905-236">이 새 Flash.ffu 사용 하 여 장치를 플래시 하 고 보안 기능을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="37905-236">Flash the device with this new Flash.ffu and validate the security features.</span></span>

<span data-ttu-id="37905-237">참조 [SecureSample](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/SecureSample) 잠금 dragon 보드 구성의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="37905-237">See [SecureSample](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/SecureSample) as an example of a lockdown dragon board configuration.</span></span>

<span data-ttu-id="37905-238">자체 IoTCore 셸에서 보안 패키지를 생성, 참조 수 또는 [보안 패키지를 추가](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools#adding-security-packages) 세부 정보에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="37905-238">Alternatively, you can generate the security packages in the IoTCore Shell itself, see [adding security packages](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools#adding-security-packages) for the details.</span></span>


### <a name="developing-with-codesigning-enforcement-enabled"></a><span data-ttu-id="37905-239">코드 서명 적용 사용를 사용 하 여 개발</span><span class="sxs-lookup"><span data-stu-id="37905-239">Developing with CodeSigning Enforcement Enabled</span></span>

<span data-ttu-id="37905-240">패키지 생성 된 잠금 활성화 되 고 개발 하는 동안 이미지에 도입 된 이진 파일 적절 하 게 서명 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="37905-240">Once the packages are generated and lockdown is activated, any binaries introduced into the image during development will need to be signed appropriately.</span></span> <span data-ttu-id="37905-241">사용자 모드 바이너리 키로 서명 되었는지 확인 _. \Keys\ \* \* \*-UMCI.pfx_합니다.</span><span class="sxs-lookup"><span data-stu-id="37905-241">Ensure that your user-mode binaries are signed with the key  _.\Keys\ \*\*\*-UMCI.pfx_.</span></span> <span data-ttu-id="37905-242">커널 모드 서명에 대 한 고유한 서명 키를 지정 하 고 있는지 확인 하려면 해야 드라이버의 경우와 같이 이러한에 에서도 나와 위의 SIPolicy 합니다.</span><span class="sxs-lookup"><span data-stu-id="37905-242">For kernel-mode signing, such as for drivers, you’ll need to specify your own signing keys and make sure that they are also included in the SIPolicy above.</span></span>

### <a name="unlocking-encrypted-drives"></a><span data-ttu-id="37905-243">암호화 된 드라이브를 잠금 해제</span><span class="sxs-lookup"><span data-stu-id="37905-243">Unlocking Encrypted Drives</span></span>

<span data-ttu-id="37905-244">개발 및 테스트 하는 동안 (예: USB 대용량 저장 모드를 통해 MinnowBoardMax 또는 DragonBoard의 eMMC에 SD 카드)를 암호화 된 장치를 오프 라인에서 내용을 읽을 하려고 할 때 'diskpart' 사용할 수 있습니다 (보겠습니다 MainOS 및 데이터 볼륨에 드라이브 문자를 할당 하려면 가정 시킵니다 MainOS 및 w:에 대 한 데이터에 대 한).</span><span class="sxs-lookup"><span data-stu-id="37905-244">During development and testing, when attempting to read contents from an encrypted device offline (e.g. SD card for MinnowBoardMax or DragonBoard's eMMC through USB mass storage mode), 'diskpart' may be used to assign a drive letter to MainOS and Data volume (let's assume v: for MainOS and w: for Data).</span></span>
<span data-ttu-id="37905-245">볼륨 잠긴 표시 되며 수동으로 잠금이 해제 되도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="37905-245">The volumes will appear locked and need to be manually unlocked.</span></span> <span data-ttu-id="37905-246">OEM DRA.pfx 인증서가 설치 되어 있는 모든 컴퓨터에서이 작업을 수행할 수 있습니다 (에 포함 된 [DeviceLockDown 샘플](https://github.com/ms-iot/security/tree/master/TurnkeySecurity)).</span><span class="sxs-lookup"><span data-stu-id="37905-246">This can be done on any machine that has the OEM-DRA.pfx certificate installed (included in the [DeviceLockDown sample](https://github.com/ms-iot/security/tree/master/TurnkeySecurity)).</span></span> <span data-ttu-id="37905-247">PFX를 설치 하 고 관리 CMD 프롬프트에서 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="37905-247">Install the PFX and then run the following commands from an administrative CMD prompt:</span></span>

* `manage-bde -unlock v: -cert -cf OEM-DRA.cer`
* `manage-bde -unlock w: -cert -cf OEM-DRA.cer`

<span data-ttu-id="37905-248">콘텐츠를 오프 라인으로 자주 액세스 됨 해야 하는 경우 BitLocker 잠금 설정할 수 있습니다 볼륨에 대 한 초기 다음 명령을 사용 하 여 잠금을 해제 한 후:</span><span class="sxs-lookup"><span data-stu-id="37905-248">If the contents need to be frequently accessed offline, BitLocker autounlock can be set up for the volumes after the initial unlock using the following commands:</span></span>

* `manage-bde -autounlock v: -enable`
* `manage-bde -autounlock w: -enable`

### <a name="disabling-bitlocker"></a><span data-ttu-id="37905-249">BitLocker를 사용 하지 않도록 설정</span><span class="sxs-lookup"><span data-stu-id="37905-249">Disabling BitLocker</span></span>

<span data-ttu-id="37905-250">일시적으로 BitLocker를 사용 하지 않도록 설정 해야 발생할 수 있습니다는 다음 명령 실행 하 고 IoT 장치를 사용 하 여 원격 PowerShell 세션을 시작할: `sectask.exe -disable`합니다.</span><span class="sxs-lookup"><span data-stu-id="37905-250">Should there arise a need to temporarily disable BitLocker, initate a remote PowerShell session with your IoT device and run the following command: `sectask.exe -disable`.</span></span>  
<span data-ttu-id="37905-251">**참고:** 예약 된 암호화 작업이 비활성화 되어 있지 않으면 장치 암호화 후속 장치 부팅 시 다시 활성화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="37905-251">**Note:** Device encryption will be re-enabled on subsequent device boot unless the scheduled encryption task is disabled.</span></span>

### <a name="disabling-device-guard"></a><span data-ttu-id="37905-252">Device Guard를 사용 하지 않도록 설정</span><span class="sxs-lookup"><span data-stu-id="37905-252">Disabling Device Guard</span></span>

<span data-ttu-id="37905-253">턴키 보안 스크립트 폴더에 SIPolicyOn.p7b 및 SIPolicyOff.p7b 파일을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="37905-253">The turnkey security script generates SIPolicyOn.p7b and SIPolicyOff.p7b files in the folder.</span></span>
<span data-ttu-id="37905-254">wm.xml는 SIPolicyOn.p7b 패키지 및 SIPolicy.p7b으로 시스템에 배치 합니다.</span><span class="sxs-lookup"><span data-stu-id="37905-254">The wm.xml packages the SIPolicyOn.p7b and places it on the system as SIPolicy.p7b.</span></span>

<span data-ttu-id="37905-255">예를 들어 다음과 같은 가치를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="37905-255">For example:</span></span>

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

<span data-ttu-id="37905-256">SIPolicyOff.p7b 파일을 사용 하는 SIPolicy.p7b으로 배치 하는 패키지를 만든 경우이 패키지를 적용 및 Device Guard가 해제 됩니다.</span><span class="sxs-lookup"><span data-stu-id="37905-256">If you create a package that takes the SIPolicyOff.p7b file and places it as a SIPolicy.p7b, it will apply this package and the Device Guard will be turned off.</span></span>



