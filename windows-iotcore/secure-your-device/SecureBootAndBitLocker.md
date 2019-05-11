---
title: 보안 부팅, BitLocker 및 Windows 10 IoT Core Device Guard를 사용 하도록 설정
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 보안 부팅, BitLocker 및 Windows 10 IoT Core Device Guard를 사용 하도록 설정 하는 방법 알아보기
keywords: windows iot, 보안 부팅, BitLocker, 턴키 보안 장치 가드, 보안
ms.openlocfilehash: 957b81a0a5bc032c62fa75598418778862fdf76d
ms.sourcegitcommit: 77b86eee2bba3844e87f9d3dbef816761ddf0dd9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/11/2019
ms.locfileid: "65533349"
---
# <a name="enabling-secure-boot-bitlocker-and-device-guard-on-windows-10-iot-core"></a><span data-ttu-id="81253-104">보안 부팅, BitLocker 및 Windows 10 IoT Core Device Guard를 사용 하도록 설정</span><span class="sxs-lookup"><span data-stu-id="81253-104">Enabling Secure Boot, BitLocker, and Device Guard on Windows 10 IoT Core</span></span>

<span data-ttu-id="81253-105">Windows 10 IoT Core는 UEFI 보안 부팅, BitLocker 장치 암호화 및 Device Guard와 같은 보안 기능 제공 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="81253-105">Windows 10 IoT Core now includes security feature offerings such as UEFI Secure Boot, BitLocker Device Encryption and Device Guard.</span></span>  <span data-ttu-id="81253-106">다양 한 유형의 공격에 복원 력 있는 Windows IoT 장치로 완벽 하 게 잠겨 만드는 이러한 장치 작성기 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="81253-106">These will assist device builders in creating fully locked down Windows IoT devices that are resilient to many different types of attacks.</span></span>  <span data-ttu-id="81253-107">함께 이러한 기능은 플랫폼을 알 수 없는 이진 파일을 잠그지 및 장치 암호화를 사용 하 여 사용자 데이터를 보호 하는 동안 정의 된 방식으로 시작 됩니다 보장 하는 최적의 보호를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="81253-107">Together, these features provide the optimal protection that ensures that a platform will launch in a defined way, while locking out unknown binaries and protecting user data through the use of device encryption.</span></span>

## <a name="boot-order"></a><span data-ttu-id="81253-108">부팅 순서</span><span class="sxs-lookup"><span data-stu-id="81253-108">Boot Order</span></span>

<span data-ttu-id="81253-109">IoT 장치에 대 한 안전한 플랫폼을 제공 하는 개별 구성 요소 자세히 살펴 보겠습니다 수 전에 부팅 순서를 Windows 10 IoT Core 장치에 대 한 이해가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="81253-109">An understanding of the boot order on a Windows 10 IoT Core device is needed before we can delve into the individual components that provide a secure platform for the IoT device.</span></span>

<span data-ttu-id="81253-110">다음 세 가지 주요 영역에서 IoT 장치를 때 발생 하는 OS 커널 로드 하 고 설치 된 응용 프로그램을 실행 하려면까지 기반 합니다.</span><span class="sxs-lookup"><span data-stu-id="81253-110">There are three main areas that occur from when an IoT device is powered on, all the way through to the OS kernel loading and execution of installed application.</span></span>

* <span data-ttu-id="81253-111">플랫폼 보안 부팅</span><span class="sxs-lookup"><span data-stu-id="81253-111">Platform Secure Boot</span></span>
* <span data-ttu-id="81253-112">Unified Extensible Firmware (UEFI) 인터페이스 보안 부팅</span><span class="sxs-lookup"><span data-stu-id="81253-112">Unified Extensible Firmware Interface (UEFI) Secure Boot</span></span>
* <span data-ttu-id="81253-113">Windows 코드 무결성</span><span class="sxs-lookup"><span data-stu-id="81253-113">Windows Code Integrity</span></span>

![대시보드 스크린샷](../media/SecureBootAndBitLocker/BootOrder.jpg)

<span data-ttu-id="81253-115">Windows 10 부팅 프로세스에 대 한 추가 정보를 찾을 수 있습니다 [여기](https://docs.microsoft.com/windows/security/information-protection/secure-the-windows-10-boot-process)합니다.</span><span class="sxs-lookup"><span data-stu-id="81253-115">Additional information on the Windows 10 boot process can be found [here](https://docs.microsoft.com/windows/security/information-protection/secure-the-windows-10-boot-process).</span></span>

## <a name="locking-down-iot-devices"></a><span data-ttu-id="81253-116">잠금 다운 IoT 장치</span><span class="sxs-lookup"><span data-stu-id="81253-116">Locking-down IoT Devices</span></span>

<span data-ttu-id="81253-117">Windows IoT 장치를 잠그고 순서로 다음과 같은 고려 사항이 수행 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="81253-117">In order to lockdown a Windows IoT device, the following considerations must be made.</span></span>

### <a name="platform-secure-boot"></a><span data-ttu-id="81253-118">플랫폼 보안 부팅</span><span class="sxs-lookup"><span data-stu-id="81253-118">Platform Secure Boot</span></span>

<span data-ttu-id="81253-119">전체 부팅 프로세스의 첫 번째 단계는 로드 하 고 펌웨어에 하드웨어를 초기화 하는 부팅 로더를 실행 하는 장치를 처음 켤 때의 devies 및 응급 깜박이 기능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="81253-119">When the device is first powered on, the first step in the overall boot process is to load and run firmware boot loaders, which initialize the hardware on the devies and provide emergency flashing functionality.</span></span> <span data-ttu-id="81253-120">UEFI 환경을 로드 하 고 컨트롤을 통해 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="81253-120">The UEFI environment is then loaded and control is handed over.</span></span>

<span data-ttu-id="81253-121">이러한 펌웨어 부팅 로더 SoC 관련 되므로 적절 한 장치 제조업체에 있는 장치에 만들어진 이러한 부팅 로더를 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="81253-121">These firmware boot loaders are SoC-specific, so you will need to work with the appropriate device manufacturer to have these boot loaders created on the device.</span></span>

### <a name="uefi-secure-boot"></a><span data-ttu-id="81253-122">UEFI 보안 부팅</span><span class="sxs-lookup"><span data-stu-id="81253-122">UEFI Secure Boot</span></span>

<span data-ttu-id="81253-123">UEFI 보안 부팅 지점인 첫 번째 정책 적용, 및 UEFI에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81253-123">UEFI Secure Boot is the first policy enforcement point, and is located in UEFI.</span></span>  <span data-ttu-id="81253-124">시스템 펌웨어 드라이버, 옵션 rom을 보유, UEFI 드라이버 또는 응용 프로그램 및 UEFI 부팅 로더 같은 지정된 된 권한으로 서명 된 바이너리만 실행할 수만 있도록 제한 합니다.</span><span class="sxs-lookup"><span data-stu-id="81253-124">It restricts the system to only allow execution of binaries signed by a specified authority, such as firmware drivers, option ROMs, UEFI drivers or applications, and UEFI boot loaders.</span></span> <span data-ttu-id="81253-125">이 기능은 플랫폼에서 실행 되 고 잠재적으로의 보안 상태가 약화 되 알 수 없는 코드를 방지 합니다.</span><span class="sxs-lookup"><span data-stu-id="81253-125">This feature prevents unknown code from being executed on the platform and potentially weakening the security posture of it.</span></span> <span data-ttu-id="81253-126">보안 부팅 루트킷과 같은 장치에 사전 부팅 맬웨어 공격의 위험을 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="81253-126">Secure Boot reduces the risk of pre-boot malware attacks to the device, such as rootkits.</span></span> 

<span data-ttu-id="81253-127">OEM,으로 UEFI 보안 부팅 제조 시간에 IoT 장치에서 데이터베이스를 저장 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="81253-127">As the OEM, you need to store the UEFI Secure Boot databases on the IoT device at manufacture time.</span></span> <span data-ttu-id="81253-128">이러한 데이터베이스 서명이 데이터베이스 (db), 서명을 해지 데이터베이스 (dbx) 및 등록 키 (KEK) 데이터베이스에 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="81253-128">These databases include the Signature database (db), Revoked Signature database (dbx), and the Key Enrollment Key database (KEK).</span></span> <span data-ttu-id="81253-129">이러한 데이터베이스는 장치의 펌웨어 비휘발성 RAM (RAM NV)에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="81253-129">These databases are stored on the firmware nonvolatile RAM (NV-RAM) of the device.</span></span>

* <span data-ttu-id="81253-130">**서명 데이터베이스 (db):** 서명자 또는 운영 체제 로더, UEFI 응용 프로그램 및 장치에서 로드할 수 있는 UEFI 드라이버의 이미지 해시 나열</span><span class="sxs-lookup"><span data-stu-id="81253-130">**Signature Database (db):** This lists the signers or image hashes of operating system loaders, UEFI applications and UEFI drivers that are allowed to be loaded on the device</span></span>

* <span data-ttu-id="81253-131">**해지 된 서명을 데이터베이스 (dbx):** 서명자 또는 운영 체제 로더, UEFI 응용 프로그램 및 UEFI 드라이버와 더 이상 신뢰할 수 있는 이미지 해시 나열 *되지* 장치에서 로드 되도록 허용</span><span class="sxs-lookup"><span data-stu-id="81253-131">**Revoked Signature Database (dbx):** This lists the signers or image hashes of operating system loaders, UEFI applications and UEFI drivers that are no longer trusted, and are *NOT* allowed to be loaded on the device</span></span> 

* <span data-ttu-id="81253-132">**등록 키 (KEK)를 데이터베이스:** 서명 서명 업데이트를 사용할 수 있으며 서명 데이터베이스를 해지 하는 키의 목록을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="81253-132">**Key Enrollment Key database (KEK):** Contains a list of signing keys that can be used to update the signature and revoked signature databases.</span></span>

<span data-ttu-id="81253-133">이러한 데이터베이스를 만들고 장치에 추가 되 면 OEM 편집에서 펌웨어를 잠그고 서명 키 (PK) 플랫폼을 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="81253-133">Once these databases are created and added to the device, the OEM locks the firmware from editing, and generates a platform signing key (PK).</span></span> <span data-ttu-id="81253-134">KEK에 대 한 업데이트에 서명 하거나 UEFI 보안 부팅을 사용 하지 않도록 설정 하려면이 키를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81253-134">This key can be used to sign updates to the KEK or to disable UEFI Secure Boot.</span></span>

<span data-ttu-id="81253-135">UEFI 보안 부팅을 수행한 단계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="81253-135">Here are the steps taken by UEFI Secure Boot:</span></span>

1. <span data-ttu-id="81253-136">장치 전원이 켜지 면 서명을 데이터베이스 각각 서명 키 (PK) 플랫폼에 대해 확인 됩니다.</span><span class="sxs-lookup"><span data-stu-id="81253-136">After the device is powered on, the signature databases are each checked against the platform signing key (PK).</span></span>
2. <span data-ttu-id="81253-137">펌웨어를 신뢰할 수 없는 경우 UEFI 펌웨어는 신뢰할 수 있는 펌웨어를 복원 하려면 OEM 특정 복구를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="81253-137">If the firmware isn't trusted, UEFI firmware initiates OEM-specific recovery to restore trusted firmware.</span></span>
3. <span data-ttu-id="81253-138">Windows 부팅 관리자를 로드할 수 없는 경우 펌웨어가 Windows 부팅 관리자의 백업 복사본을 부팅 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="81253-138">If Windows Boot Manager cannot be loaded, the firmware will attempt to boot a backup copy of Windows Boot Manager.</span></span> <span data-ttu-id="81253-139">또한 실패 하면 UEFI 펌웨어 OEM 전용 업데이트 관리를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="81253-139">If this also fails, the UEFI firmware initiates OEM-specific remediation.</span></span>
4. <span data-ttu-id="81253-140">Windows 부팅 관리자 실행 되며 Windows 커널 디지털 서명을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="81253-140">Windows Boot Manager runs and verifies the digital signature of the Windows Kernel.</span></span> <span data-ttu-id="81253-141">신뢰할 수 있는 경우 Windows 부팅 관리자는 Windows 커널에 제어를 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="81253-141">If trusted, Windows Boot Manager passes control to the Windows Kernel.</span></span>


<span data-ttu-id="81253-142">키 생성 및 관리 지침, 보안 부팅에 대 한 추가 정보를 사용할 수 [여기](https://technet.microsoft.com/library/dn747883.aspx)합니다.</span><span class="sxs-lookup"><span data-stu-id="81253-142">Additional details on Secure Boot, along with key creation and management guidance, is available [here](https://technet.microsoft.com/library/dn747883.aspx).</span></span>

### <a name="windows-code-integrity"></a><span data-ttu-id="81253-143">Windows 코드 무결성</span><span class="sxs-lookup"><span data-stu-id="81253-143">Windows Code Integrity</span></span>

<span data-ttu-id="81253-144">Windows 코드 무결성 (WCI) 드라이버 또는 메모리에 로드 될 때마다 응용 프로그램의 무결성을 검사 하 여 운영 체제의 보안을 개선 합니다.</span><span class="sxs-lookup"><span data-stu-id="81253-144">Windows Code Integrity (WCI) improves the security of the operating system by validating the integrity of a driver or application each time it is loaded into memory.</span></span> <span data-ttu-id="81253-145">CI는 두 개의 주요 구성-커널 모드 코드 무결성 (KMCI) 및 사용자 모드 코드 무결성 (UMCI)를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="81253-145">CI contains two main components - Kernel Mode Code Integrity (KMCI) and User Mode Code Integrity (UMCI).</span></span>

<span data-ttu-id="81253-146">구성 가능한 코드 무결성 (CCI)는 Windows 10 장치를 잠그고 장치 작성기를 사용 하면만 실행 하 고 서명 되 고 신뢰할 수 있는 코드를 실행할 수 있도록 하는 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="81253-146">Configurable Code Integrity (CCI) is a feature in Windows 10 that allows device builders to lockdown a device and only allow it to run and execute code that is signed and trusted.</span></span>  <span data-ttu-id="81253-147">이렇게 하려면 장치 작성기 수 코드 무결성 정책을 'golden' 장치 (하드웨어 및 소프트웨어의 최종 릴리스 버전)에 다음 보안 만들고 공장 현장에서 모든 장치에서이 정책을 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="81253-147">To do so, device builders can create a code integrity policy on a 'golden' device (final release version of hardware and software) and then secure and apply this policy on all devices on the factory floor.</span></span>

<span data-ttu-id="81253-148">코드 무결성 정책을 배포 하는 방법에 대 한 자세한 내용은 감사 및 적용, 설명서를 확인해 최신 technet [여기](https://technet.microsoft.com/itpro/windows/keep-secure/deploy-code-integrity-policies-steps)합니다.</span><span class="sxs-lookup"><span data-stu-id="81253-148">To learn more about deploying code integrity policies, auditing and enforcement, check out the latest technet documentation [here](https://technet.microsoft.com/itpro/windows/keep-secure/deploy-code-integrity-policies-steps).</span></span>

<span data-ttu-id="81253-149">Windows 코드 무결성을 수행한 단계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="81253-149">Here are the steps taken by Windows Code Integrity:</span></span>

1. <span data-ttu-id="81253-150">Windows 커널에 로드 하기 전에 서명 데이터베이스에 대해 다른 모든 구성 요소 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="81253-150">Windows Kernel will verify all other components against the signature database before loading.</span></span> <span data-ttu-id="81253-151">시작 파일, 드라이버 및 ELAM (맬웨어 방지 조기 실행-)이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="81253-151">This includes drivers, startup files and ELAM (Early Launch Anti-Malware).</span></span>
2. <span data-ttu-id="81253-152">Windows 커널 시작 프로세스의 신뢰할 수 있는 구성 요소를 로드 하 고 신뢰할 수 없는 구성 요소 로드 금지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="81253-152">Windows Kernel will load the trusted components in the startup process, and prohibit loading of the untrusted components.</span></span>
3. <span data-ttu-id="81253-153">Windows 10 IoT Core 운영 체제 설치 된 모든 응용 프로그램과 함께 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="81253-153">Windows 10 IoT Core operating system loads, along with any installed applications.</span></span>

### <a name="bitlocker-device-encryption"></a><span data-ttu-id="81253-154">BitLocker 장치 암호화</span><span class="sxs-lookup"><span data-stu-id="81253-154">BitLocker Device Encryption</span></span>

<span data-ttu-id="81253-155">Windows 10 IoT Core 경량 버전의 BitLocker 장치 암호화를 오프 라인 공격 으로부터 IoT 장치가 보호도 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="81253-155">Windows 10 IoT Core also implements a lightweight version of BitLocker Device Encryption, protecting IoT devices against offline attacks.</span></span> <span data-ttu-id="81253-156">이 기능은 필요한 os 시작 전 프로토콜을 포함 하 여 필요한 측정을 수행 하는 UEFI의 플랫폼에서 TPM의 존재에 강력한 종속성을 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="81253-156">This capability has a strong dependency on the presence of a TPM on the platform, including the necessary pre-OS protocol in UEFI that conducts the necessary measurements.</span></span> <span data-ttu-id="81253-157">이러한 os 시작 전 측정 OS 나중에 OS가 시작 하는 방법을; 한 명확한 기록이 확인 그러나 실행 제한을 적용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="81253-157">These pre-OS measurements ensure that the OS later has a definitive record of how the OS was launched; however, it does not enforce any execution restrictions.</span></span>

> [!TIP]
> <span data-ttu-id="81253-158">Windows 10 IoT Core 대 한 BitLocker 기능을 사용할 수 있는 모든 NTFS 데이터 볼륨을 바인딩하는 동안 자동 NTFS 기반 OS 볼륨 암호화를 위한 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81253-158">BitLocker functionality on Windows 10 IoT Core allows for automatic encryption of NTFS-based OS volume while binding all available NTFS data volumes to it.</span></span> <span data-ttu-id="81253-159">이 위해 EFIESP 볼륨 GUID로 설정 되어 있는지 확인 하는 데 필요한 것 _C12A7328-F81F-11D2-BA4B-00A0C93EC93B_합니다.</span><span class="sxs-lookup"><span data-stu-id="81253-159">For this, it’s necessary to ensure that the EFIESP volume GUID is set to _C12A7328-F81F-11D2-BA4B-00A0C93EC93B_.</span></span>

### <a name="device-guard-on-windows-iot-core"></a><span data-ttu-id="81253-160">Windows IoT Core에서 device Guard</span><span class="sxs-lookup"><span data-stu-id="81253-160">Device Guard on Windows IoT Core</span></span>

<span data-ttu-id="81253-161">대부분의 IoT 장치는 고정 함수 장치로 빌드됩니다.</span><span class="sxs-lookup"><span data-stu-id="81253-161">Most IoT devices are built as fixed-function devices.</span></span> <span data-ttu-id="81253-162">이 장치 작성기는 펌웨어, 운영 체제, 드라이버 및 응용 프로그램 특정된 장치에서 실행 되어야 합니다 정확히 알고 있는 것을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="81253-162">This implies that device builders know exactly which firmware, operating system, drivers and applications should be running on a given device.</span></span> <span data-ttu-id="81253-163">이 정보를 수 있습니다만 알려져 있고 신뢰할 수 있는 코드의 실행을 허용 하 여 IoT 장치를 완벽 하 게 잠금에 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="81253-163">In turn, this information can be used to fully lockdown an IoT device by only allowing execution of known and trusted code.</span></span> <span data-ttu-id="81253-164">Windows 10 IoT Core device Guard는 잠긴 장치에서 알 수 없거나 신뢰할 수 없는 실행 코드를 실행할 수 없음을 확인 하 여 IoT 장치를 보호할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81253-164">Device Guard on Windows 10 IoT Core can help protect IoT devices by ensuring that unknown or untrusted executable code cannot be run on locked-down devices.</span></span>


## <a name="turnkey-security-on-iot-core"></a><span data-ttu-id="81253-165">IoT Core에 대 한 턴키 보안</span><span class="sxs-lookup"><span data-stu-id="81253-165">Turnkey Security on IoT Core</span></span>

<span data-ttu-id="81253-166">Microsoft는 턴키 ' 보안 패키지 '을 제공 하는 데 쉽게 사용 IoT Core 장치에서 주요 보안 기능을 위해 장치 작성기 빌드할 수 있는 IoT 장치를 완벽 하 게 잠겨 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81253-166">To facilitate easy enablement of key security features on IoT Core devices, Microsoft is providing a turnkey 'Security Package' that allows device builders to build fully locked down IoT devices.</span></span>  <span data-ttu-id="81253-167">이 패키지에 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="81253-167">This package will help with:</span></span>

* <span data-ttu-id="81253-168">보안 부팅 키 프로 비전 하 고 지원 되는 IoT 플랫폼에서이 기능을 사용 하도록 설정</span><span class="sxs-lookup"><span data-stu-id="81253-168">Provisioning Secure Boot keys and enabling the feature on supported IoT platforms</span></span>
* <span data-ttu-id="81253-169">BitLocker를 사용 하 여 장치 암호화의 설정 및 구성</span><span class="sxs-lookup"><span data-stu-id="81253-169">Setup and configuration of device encryption using BitLocker</span></span> 
* <span data-ttu-id="81253-170">시작만 서명 된 응용 프로그램 및 드라이버를 실행할 수 있도록 장치 잠금</span><span class="sxs-lookup"><span data-stu-id="81253-170">Initiating device lockdown to only allow execution of signed applications and drivers</span></span>

### <a name="prerequisites"></a><span data-ttu-id="81253-171">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="81253-171">Prerequisites</span></span>

* <span data-ttu-id="81253-172">Windows 10 Enterprise 실행 하는 PC</span><span class="sxs-lookup"><span data-stu-id="81253-172">A PC running Windows 10 Enterprise</span></span>
* <span data-ttu-id="81253-173">[Windows 10 SDK](https://developer.microsoft.com/en-US/windows/downloads/windows-10-sdk) -인증서 생성에 대 한 필수</span><span class="sxs-lookup"><span data-stu-id="81253-173">[Windows 10 SDK](https://developer.microsoft.com/en-US/windows/downloads/windows-10-sdk) - Required for Certificate Generation</span></span>
* <span data-ttu-id="81253-174">[Windows 10 ADK](https://developer.microsoft.com/en-us/windows/hardware/windows-assessment-deployment-kit) -CAB 생성을 위한 필수 항목</span><span class="sxs-lookup"><span data-stu-id="81253-174">[Windows 10 ADK](https://developer.microsoft.com/en-us/windows/hardware/windows-assessment-deployment-kit) - Required for CAB generation</span></span>
* <span data-ttu-id="81253-175">참조 하는 플랫폼 전달 펌웨어, OS, 드라이버 및 응용 프로그램을 사용 하 여 릴리스 하드웨어 해야 최종 잠금에 대 한</span><span class="sxs-lookup"><span data-stu-id="81253-175">Reference platform - release hardware with shipping firmware, OS, drivers and applications will be required for final lockdown</span></span>

### <a name="development-iot-devices"></a><span data-ttu-id="81253-176">IoT 장치 개발</span><span class="sxs-lookup"><span data-stu-id="81253-176">Development IoT Devices</span></span>

<span data-ttu-id="81253-177">Windows 10 IoT Core 수백 대의 장치에서 사용 되는 다양 한 silicons를 사용 하 여 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="81253-177">Windows 10 IoT Core works with various silicons that are utilized in hundreds of devices.</span></span> <span data-ttu-id="81253-178">[IoT 개발 장치 제안](../learn-about-hardware/SoCsAndCustomBoards.md), 기본적으로 보안 부팅, 계획 부팅, BitLocker 및 Device Guard 기능과 함께 펌웨어 TPM 기능을 제공 하는 다음:</span><span class="sxs-lookup"><span data-stu-id="81253-178">Of the [suggested IoT development devices](../learn-about-hardware/SoCsAndCustomBoards.md), the following provide firmware TPM functionality out of the box, along with Secure Boot, Measured Boot, BitLocker and Device Guard capabilities:</span></span>

* <span data-ttu-id="81253-179">Qualcomm DragonBoard 410 c</span><span class="sxs-lookup"><span data-stu-id="81253-179">Qualcomm DragonBoard 410c</span></span>

    <span data-ttu-id="81253-180">보안 부팅을 사용 하도록 설정 하기 위해 RPMB 프로 비전 해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81253-180">In order to enable Secure Boot, it may be necessary to provision RPMB.</span></span> <span data-ttu-id="81253-181">eMMC Windows 10 IoT Core 사용 하 여 플래시 됨 된가 되 면 (지침에 따라 [여기](https://docs.microsoft.com/windows/iot-core/tutorials/quickstarter/devicesetup#using-the-iot-dashboard-dragonboard-410c), 키를 눌러 [Power] + [Vol +] + [Vol-]을 선택 "프로 비전 RPMB" BDS 메뉴에서 전원을 켤 때 장치에서 동시에 합니다.</span><span class="sxs-lookup"><span data-stu-id="81253-181">Once the eMMC has been flashed with Windows 10 IoT Core (as per instructions [here](https://docs.microsoft.com/windows/iot-core/tutorials/quickstarter/devicesetup#using-the-iot-dashboard-dragonboard-410c), press [Power] + [Vol+] + [Vol-] simultaneously on the device when powering up and select "Provision RPMB" from the BDS menu.</span></span> <span data-ttu-id="81253-182">*이 단계를 취소할 수는 note 하십시오.*</span><span class="sxs-lookup"><span data-stu-id="81253-182">*Please note that this is an irreversible step.*</span></span>

* <span data-ttu-id="81253-183">Intel MinnowBoardMax</span><span class="sxs-lookup"><span data-stu-id="81253-183">Intel MinnowBoardMax</span></span>

    <span data-ttu-id="81253-184">Intel의 MinnowBoard 최대 펌웨어 버전 0.82 이상 이어야 합니다 (가져오기의 [최신 펌웨어로](https://firmware.intel.com/projects/minnowboard-max)).</span><span class="sxs-lookup"><span data-stu-id="81253-184">For Intel's MinnowBoard Max, firmware version must be 0.82 or higher (get the [latest firmware](https://firmware.intel.com/projects/minnowboard-max)).</span></span> <span data-ttu-id="81253-185">TPM 기능을 사용 하려면 키보드와 디스플레이 보드의 전원을 연결 및 UEFI 설치 F2 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="81253-185">To enable TPM capabilities, power up board with a keyboard & display attached and press F2 to enter UEFI setup.</span></span> <span data-ttu-id="81253-186">로 이동 _Device Manager 시스템 설정-> 보안 구성-> PTT->_ 로 설정 하 고  _&lt;사용 하도록 설정&gt;_ 합니다.</span><span class="sxs-lookup"><span data-stu-id="81253-186">Go to _Device Manager -> System Setup -> Security Configuration -> PTT_ and set it to _&lt;Enable&gt;_.</span></span> <span data-ttu-id="81253-187">F10 키를 눌러 변경 내용을 저장 하는 플랫폼의 다시 부팅을 사용 하 여 계속 합니다.</span><span class="sxs-lookup"><span data-stu-id="81253-187">Press F10 to save changes and proceed with a reboot of the platform.</span></span>

> [!NOTE]
> <span data-ttu-id="81253-188">Raspberry Pi 2 또는 3 TPM을 지원 하지 않으며 따라서에서는 잠금 시나리오를 구성할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="81253-188">Raspberry Pi 2 nor 3 do not support TPM and so we cannot configure Lockdown scenarios.</span></span>

### <a name="generate-lockdown-packages"></a><span data-ttu-id="81253-189">잠금 패키지를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="81253-189">Generate Lockdown Packages</span></span>

1. <span data-ttu-id="81253-190">다운로드 합니다 [DeviceLockDown 스크립트](https://github.com/ms-iot/security/tree/master/TurnkeySecurity) 모든 추가 도구 및 구성 하 고 장치를 잠그는 데 필요한 스크립트를 포함 하는 패키지</span><span class="sxs-lookup"><span data-stu-id="81253-190">Download the [DeviceLockDown Script](https://github.com/ms-iot/security/tree/master/TurnkeySecurity) package, which contains all of the additional tools and scripts required for configuring and locking down devices</span></span>
2. <span data-ttu-id="81253-191">Windows 10 pc를 관리 PS (PowerShell) 콘솔을 시작 하 고 다운로드 한 스크립트의 위치로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="81253-191">Start an Administrative PowerShell (PS) console on your Windows 10 PC and navigate to the location of the downloaded script.</span></span>
3. <span data-ttu-id="81253-192">(잠금 해제 된 이미지를 실행) 하 여 참조 하드웨어 플랫폼을 사용 하 여 네트워크 공유를 통해 PC에 탑재</span><span class="sxs-lookup"><span data-stu-id="81253-192">Mount your reference hardware platform (running the unlocked image) to your PC via network share using</span></span>

    ```powershell
    net use \\a.b.c.d\c$ /user:username password
    ```

4. <span data-ttu-id="81253-193">사용 하 여 장치에 대 한 키를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="81253-193">Generate keys for your device using</span></span>

    ```powershell
    .\GenerateKeys.ps1 -OemName '<your oem name>' -outputPath '<output directory>'
    ```

    * <span data-ttu-id="81253-194">키 및 인증서를 적절 한 접미사를 사용 하 여 지정 된 출력 폴더에 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="81253-194">The keys and certificates are generated in the specified output folder with appropriate suffix.</span></span>
    * <span data-ttu-id="81253-195">**생성 된 키를 보호할** 장치는 이진 파일을 신뢰 하는 대로 잠금 후에 이러한 키를 사용 하 여 서명 합니다.</span><span class="sxs-lookup"><span data-stu-id="81253-195">**Secure your generated keys** as the device will trust binaries signed with these keys only after lockdown.</span></span>
    * <span data-ttu-id="81253-196">이 단계를 건너뛸 수 있습니다를 미리 생성 된 키를 사용 하 여 테스트 전용</span><span class="sxs-lookup"><span data-stu-id="81253-196">You may skip this step and use the pre-generated keys for testing only</span></span>

5. <span data-ttu-id="81253-197">구성 _settings.xml_</span><span class="sxs-lookup"><span data-stu-id="81253-197">Configure _settings.xml_</span></span>

    * <span data-ttu-id="81253-198">일반 섹션: 패키지 디렉터리를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="81253-198">General section : Specify the package directories</span></span>
    * <span data-ttu-id="81253-199">도구 섹션: 도구에 대 한 경로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="81253-199">Tools section : Set the path for the tools</span></span>
        * <span data-ttu-id="81253-200">Windows10KitsRoot `(e.g. <Windows10KitsRoot>C:\Program Files (x86)\Windows Kits\10\</Windows10KitsRoot>)`</span><span class="sxs-lookup"><span data-stu-id="81253-200">Windows10KitsRoot `(e.g. <Windows10KitsRoot>C:\Program Files (x86)\Windows Kits\10\</Windows10KitsRoot>)`</span></span>
        * <span data-ttu-id="81253-201">WindowsSDKVersion `(e.g. <WindowsSDKVersion>10.0.15063.0</WindowsSDKVersion>)`</span><span class="sxs-lookup"><span data-stu-id="81253-201">WindowsSDKVersion `(e.g. <WindowsSDKVersion>10.0.15063.0</WindowsSDKVersion>)`</span></span>
            * <span data-ttu-id="81253-202">컴퓨터에 설치 된 SDK 버전은 `C:\Program Files (x86)\Windows Kits\10\`</span><span class="sxs-lookup"><span data-stu-id="81253-202">SDK version installed on your machine is under `C:\Program Files (x86)\Windows Kits\10\`</span></span>
    * <span data-ttu-id="81253-203">SecureBoot 섹션: 보안 부팅 (PK 및 SB 키)에 사용할 키를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="81253-203">SecureBoot section : Specify which keys to use for secure boot (PK and SB keys)</span></span>
    * <span data-ttu-id="81253-204">BitLocker 섹션: Bitlocker 데이터 복구 (DRA 키)에 대 한 인증서를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="81253-204">BitLocker section : Specify a certificate for Bitlocker data recovery (DRA key)</span></span>
    * <span data-ttu-id="81253-205">SIPolicy 섹션: 신뢰할 수 있는 인증서를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="81253-205">SIPolicy section : Specify certs that should be trusted</span></span>
        * <span data-ttu-id="81253-206">ScanPath : 이진 파일을 검색 하는 것에 대 한 장치의 경로 `\\a.b.c.d\C$`</span><span class="sxs-lookup"><span data-stu-id="81253-206">ScanPath : Path of the device for scanning binaries , `\\a.b.c.d\C$`</span></span>
        * <span data-ttu-id="81253-207">업데이트: 서명자의 SIPolicy (PAUTH 키)</span><span class="sxs-lookup"><span data-stu-id="81253-207">Update   : Signer of the SIPolicy (PAUTH keys)</span></span>
        * <span data-ttu-id="81253-208">사용자: 사용자 모드 인증서 (UMCI 키)</span><span class="sxs-lookup"><span data-stu-id="81253-208">User     : User mode certificates (UMCI keys)</span></span> 
        * <span data-ttu-id="81253-209">커널: 커널 모드 (KMCI 키) 인증서</span><span class="sxs-lookup"><span data-stu-id="81253-209">Kernel   : Kernel mode certificates (KMCI keys)</span></span>
    * <span data-ttu-id="81253-210">패키징: 패키지 생성을 위한 설정 지정</span><span class="sxs-lookup"><span data-stu-id="81253-210">Packaging : Specify the settings for the package generation</span></span>

> [!IMPORTANT]
> <span data-ttu-id="81253-211">초기 개발 주기 동안 테스트를 지원 하기 위해 Microsoft에 제공 미리 생성 된 키 및 인증서 적절 한 경우.</span><span class="sxs-lookup"><span data-stu-id="81253-211">In order to assist with testing during the initial development cycle, Microsoft has provided pre-generated keys and certificates where appropriate.</span></span>  <span data-ttu-id="81253-212">즉, 신뢰할 수 있는 Microsoft 테스트, 개발 및 시험판 버전 이진 파일 간주 됩니다.</span><span class="sxs-lookup"><span data-stu-id="81253-212">This implies that Microsoft Test, Development and Pre-Release binaries are considered trusted.</span></span>  <span data-ttu-id="81253-213">최종 제품 만들기 및 이미지를 생성 하는 동안 사용할 이러한 인증서를 제거 하 고 사용자 고유의 키를 사용 하 여 장치를 완벽 하 게 잠겨 있는지 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="81253-213">During final product creation and image generation, be sure to remove these certifcates and use your own keys to ensure a fully locked down device.</span></span>

<span data-ttu-id="81253-214">6. 필요한 패키지를 생성 하려면 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="81253-214">6.Execute the following commands to generate required packages:</span></span>

    ```powershell
    Import-Module .\IoTTurnkeySecurity.psm1
    # Generate the security packages for retail
    New-IoTTurnkeySecurity -ConfigFileName .\settings.xml
    (or)
    # Generate the security packages for test
    New-IoTTurnkeySecurity -ConfigFileName .\settings.xml -Test
    ```

### <a name="test-lockdown-packages"></a><span data-ttu-id="81253-215">잠금 패키지 테스트</span><span class="sxs-lookup"><span data-stu-id="81253-215">Test Lockdown packages</span></span>
<span data-ttu-id="81253-216">수동으로 다음 단계에 따라 잠금 해제 된 장치에 설치 하 여 생성된 된 패키지를 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81253-216">You can test the generated packages by manually installing them on a unlocked device by the following steps</span></span>

1. <span data-ttu-id="81253-217">잠금이 해제 된 이미지 (이전 단계에서 스캔 하는 데 사용 되는 이미지)를 사용 하 여 장치를 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="81253-217">Flash the device with the unlocked image (image used for scanning in earlier step).</span></span>
2. <span data-ttu-id="81253-218">장치에 연결 ([SSH를 사용 하 여](../connect-your-device/SSH.md) 알거나 [Powershell](../connect-your-device/PowerShell.md))</span><span class="sxs-lookup"><span data-stu-id="81253-218">Connect to the device ([using SSH](../connect-your-device/SSH.md) or using [Powershell](../connect-your-device/PowerShell.md))</span></span>
3. <span data-ttu-id="81253-219">예를 들어 디렉터리에 있는 장치에 다음.cab 파일을 복사 `c:\OemInstall`</span><span class="sxs-lookup"><span data-stu-id="81253-219">Copy the following .cab files to the device under a directory e.g. `c:\OemInstall`</span></span>
    * <span data-ttu-id="81253-220">OEM.Custom.Cmd.cab</span><span class="sxs-lookup"><span data-stu-id="81253-220">OEM.Custom.Cmd.cab</span></span>
    * <span data-ttu-id="81253-221">OEM.Security.BitLocker.cab</span><span class="sxs-lookup"><span data-stu-id="81253-221">OEM.Security.BitLocker.cab</span></span>
    * <span data-ttu-id="81253-222">OEM.Security.SecureBoot.cab</span><span class="sxs-lookup"><span data-stu-id="81253-222">OEM.Security.SecureBoot.cab</span></span>
    * <span data-ttu-id="81253-223">OEM.Security.DeviceGuard.cab</span><span class="sxs-lookup"><span data-stu-id="81253-223">OEM.Security.DeviceGuard.cab</span></span>
4. <span data-ttu-id="81253-224">다음 명령을 내림 하 여 생성된 된 패키지의 준비 시작</span><span class="sxs-lookup"><span data-stu-id="81253-224">Initiate staging of the generated packages by issueing the following commands</span></span>

    ```C
    applyupdate -stage c:\OemInstall\OEM.Custom.Cmd.cab
    ```
    <span data-ttu-id="81253-225">사용자 지정 이미지를 사용 하는 경우 해야 *건너뜁니다* 이 파일을 수동으로 편집 합니다 `c:\windows\system32\oemcustomization.cmd` 에서 사용할 수 있는 내용으로 `Output\OEMCustomization\OEMCustomization.cmd` 파일</span><span class="sxs-lookup"><span data-stu-id="81253-225">If you are using custom image, then you will have to *skip* this file and manually edit the `c:\windows\system32\oemcustomization.cmd` with the contents available in `Output\OEMCustomization\OEMCustomization.cmd` file</span></span>

    ```C
    applyupdate -stage c:\OemInstall\OEM.Security.BitLocker.cab
    applyupdate -stage c:\OemInstall\OEM.Security.SecureBoot.cab
    applyupdate -stage c:\OemInstall\OEM.Security.DeviceGuard.cab

5. Finally, commit the packages via

    ```C
    applyupdate -commit
    ```

6. <span data-ttu-id="81253-226">장치가는 업데이트 패키지를 설치 하려면 OS (보여 주는 gears)으로 다시 부팅 됩니다 하 고 기본 OS를 다시 부팅 됩니다.</span><span class="sxs-lookup"><span data-stu-id="81253-226">The device will reboot into update OS (showing gears) to install the packages and will reboot again to main OS.</span></span>  <span data-ttu-id="81253-227">장치를 MainOS 되돌려 다시 부팅 보안 부팅을 사용할 및 SIPolicy 참여 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="81253-227">Once the device reboots back into MainOS, Secure Boot will be enabled and SIPolicy should be engaged.</span></span>
7. <span data-ttu-id="81253-228">Bitlocker 암호화를 활성화 하려면 다시 장치를 다시 부팅 합니다.</span><span class="sxs-lookup"><span data-stu-id="81253-228">Reboot the device again to activate the Bitlocker encryption.</span></span>
8. <span data-ttu-id="81253-229">보안 기능 테스트</span><span class="sxs-lookup"><span data-stu-id="81253-229">Test the security features</span></span>
    * <span data-ttu-id="81253-230">SecureBoot: 시도 `bcdedit /debug on` , 값 보안 부팅 정책에 의해 보호 되는 내용의 오류가 표시 됩니다</span><span class="sxs-lookup"><span data-stu-id="81253-230">SecureBoot: try `bcdedit /debug on` , you will get an error stating that the value is protected by secure boot policy</span></span>
    * <span data-ttu-id="81253-231">BitLocker: 실행할 `fvecon -status c:`, 상태 언급 하면 *에 암호화가 복구 데이터 (외부 키), TPM 데이터에, 보안, 부팅 파티션, 사용 중인 공간만*</span><span class="sxs-lookup"><span data-stu-id="81253-231">BitLocker: Run `fvecon -status c:`, you will get the status mentioning *On, Encrypted, Has Recovery Data (external key), Has TPM Data, Secure, Boot Partition, Used Space Only*</span></span>
    * <span data-ttu-id="81253-232">DeviceGuard: 모든 부호 없는 이진 또는 SIPolicy 목록에 없는 인증서로 서명 된 이진 파일을 실행 하 고 실행 해 서 실패 하는지를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="81253-232">DeviceGuard : Run any unsigned binary or a binary signed with certificate not in the SIPolicy list and confirm that it fails to run.</span></span>

### <a name="generate-lockdown-image"></a><span data-ttu-id="81253-233">잠금 이미지 생성</span><span class="sxs-lookup"><span data-stu-id="81253-233">Generate Lockdown image</span></span>

<span data-ttu-id="81253-234">앞에서 정의한 설정에 따라 작업 하는 잠금 패키지 유효성 검사 후 포함할 수 있습니다 이러한 패키지를 이미지에 따라는 아래 단계를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="81253-234">After validating that the lockdown packages are working as per the settings defined earlier, you can then include these packages into the image by following the below given steps.</span></span> <span data-ttu-id="81253-235">읽기를 [IoT 제조 가이드](https://aka.ms/iotcoreguide) 사용자 지정 이미지 만들기 지침에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="81253-235">Read the [IoT manufacturing guide](https://aka.ms/iotcoreguide) for custom image creation instructions.</span></span>

1. <span data-ttu-id="81253-236">작업 영역 디렉터리에 생성 된 출력 디렉터리에서 다음 파일 업데이트</span><span class="sxs-lookup"><span data-stu-id="81253-236">In the workspace directory, update the following files from the generated output directory above</span></span>
    * <span data-ttu-id="81253-237">SecureBoot : `Copy ..\Output\SecureBoot\*.bin  ..\Workspace\Common\Packages\Security.SecureBoot`</span><span class="sxs-lookup"><span data-stu-id="81253-237">SecureBoot : `Copy ..\Output\SecureBoot\*.bin  ..\Workspace\Common\Packages\Security.SecureBoot`</span></span>
      * <span data-ttu-id="81253-238">SetVariable_db.bin</span><span class="sxs-lookup"><span data-stu-id="81253-238">SetVariable_db.bin</span></span>
      * <span data-ttu-id="81253-239">SetVariable_kek.bin</span><span class="sxs-lookup"><span data-stu-id="81253-239">SetVariable_kek.bin</span></span>
      * <span data-ttu-id="81253-240">SetVariable_pk.bin</span><span class="sxs-lookup"><span data-stu-id="81253-240">SetVariable_pk.bin</span></span>
    * <span data-ttu-id="81253-241">BitLocker : `Copy ..\Output\Bitlocker\*.* ..\Workspace\Common\Packages\Security.Bitlocker`</span><span class="sxs-lookup"><span data-stu-id="81253-241">BitLocker : `Copy ..\Output\Bitlocker\*.* ..\Workspace\Common\Packages\Security.Bitlocker`</span></span>
      * <span data-ttu-id="81253-242">DETask.xml</span><span class="sxs-lookup"><span data-stu-id="81253-242">DETask.xml</span></span>
      * <span data-ttu-id="81253-243">Security.Bitlocker.wm.xml</span><span class="sxs-lookup"><span data-stu-id="81253-243">Security.Bitlocker.wm.xml</span></span>
      * <span data-ttu-id="81253-244">setup.bitlocker.cmd</span><span class="sxs-lookup"><span data-stu-id="81253-244">setup.bitlocker.cmd</span></span>
    * <span data-ttu-id="81253-245">DeviceGuard : `Copy ..\Output\DeviceGuard\*.*  ..\Workspace\Common\Packages\Security.DeviceGuard`</span><span class="sxs-lookup"><span data-stu-id="81253-245">DeviceGuard : `Copy ..\Output\DeviceGuard\*.*  ..\Workspace\Common\Packages\Security.DeviceGuard`</span></span>
      * <span data-ttu-id="81253-246">SIPolicyOn.p7b</span><span class="sxs-lookup"><span data-stu-id="81253-246">SIPolicyOn.p7b</span></span>
      * <span data-ttu-id="81253-247">SIPolicyOff.p7b</span><span class="sxs-lookup"><span data-stu-id="81253-247">SIPolicyOff.p7b</span></span>
  
2. <span data-ttu-id="81253-248">RetailOEMInput.xml 및 TestOEMInput.xml 잠금 패키지 기능 ID 사용 하 여 ProductName 디렉터리 아래에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="81253-248">Add RetailOEMInput.xml and TestOEMInput.xml under the ProductName directory with lockdown package feature ID</span></span>
    * `<Feature>SEC_BITLOCKER</Feature>`
    * `<Feature>SEC_SECUREBOOT</Feature>`
    * `<Feature>SEC_DEVICEGUARD</Feature>`
3. <span data-ttu-id="81253-249">이미지를 다시 생성</span><span class="sxs-lookup"><span data-stu-id="81253-249">Re-generate Image</span></span>
    * <span data-ttu-id="81253-250">`buildpkg all` (위의 정책 파일에 따라 새 잠금 패키지 생성)</span><span class="sxs-lookup"><span data-stu-id="81253-250">`buildpkg all` (this generates new lockdown packages based on above policy files)</span></span>
    * <span data-ttu-id="81253-251">`buildimage ProductName test(or)retail`  (새 Flash.ffu 생성)</span><span class="sxs-lookup"><span data-stu-id="81253-251">`buildimage ProductName test(or)retail`  (this generates new Flash.ffu)</span></span>
4. <span data-ttu-id="81253-252">이 새 Flash.ffu 사용 하 여 장치를 플래시 하 고 보안 기능을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="81253-252">Flash the device with this new Flash.ffu and validate the security features.</span></span>

<span data-ttu-id="81253-253">참조 [SecureSample](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/SecureSample) 잠금 dragon 보드 구성의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="81253-253">See [SecureSample](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/SecureSample) as an example of a lockdown dragon board configuration.</span></span>

<span data-ttu-id="81253-254">자체 IoTCore 셸에서 보안 패키지를 생성, 참조 수 또는 [보안 패키지를 추가](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools#adding-security-packages) 세부 정보에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="81253-254">Alternatively, you can generate the security packages in the IoTCore Shell itself, see [adding security packages](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools#adding-security-packages) for the details.</span></span>


### <a name="developing-with-codesigning-enforcement-enabled"></a><span data-ttu-id="81253-255">코드 서명 적용 사용를 사용 하 여 개발</span><span class="sxs-lookup"><span data-stu-id="81253-255">Developing with CodeSigning Enforcement Enabled</span></span>

<span data-ttu-id="81253-256">패키지 생성 된 잠금 활성화 되 고 개발 하는 동안 이미지에 도입 된 이진 파일 적절 하 게 서명 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="81253-256">Once the packages are generated and lockdown is activated, any binaries introduced into the image during development will need to be signed appropriately.</span></span> <span data-ttu-id="81253-257">사용자 모드 바이너리 키로 서명 되었는지 확인 _. \Keys\ \* \* \*-UMCI.pfx_합니다.</span><span class="sxs-lookup"><span data-stu-id="81253-257">Ensure that your user-mode binaries are signed with the key  _.\Keys\ \*\*\*-UMCI.pfx_.</span></span> <span data-ttu-id="81253-258">커널 모드 서명에 대 한 고유한 서명 키를 지정 하 고 있는지 확인 하려면 해야 드라이버의 경우와 같이 이러한에 에서도 나와 위의 SIPolicy 합니다.</span><span class="sxs-lookup"><span data-stu-id="81253-258">For kernel-mode signing, such as for drivers, you’ll need to specify your own signing keys and make sure that they are also included in the SIPolicy above.</span></span>

### <a name="unlocking-encrypted-drives"></a><span data-ttu-id="81253-259">암호화 된 드라이브를 잠금 해제</span><span class="sxs-lookup"><span data-stu-id="81253-259">Unlocking Encrypted Drives</span></span>

<span data-ttu-id="81253-260">개발 및 테스트 하는 동안 (예: USB 대용량 저장 모드를 통해 MinnowBoardMax 또는 DragonBoard의 eMMC에 SD 카드)를 암호화 된 장치를 오프 라인에서 내용을 읽을 하려고 할 때 'diskpart' 사용할 수 있습니다 (보겠습니다 MainOS 및 데이터 볼륨에 드라이브 문자를 할당 하려면 가정 시킵니다 MainOS 및 w:에 대 한 데이터에 대 한).</span><span class="sxs-lookup"><span data-stu-id="81253-260">During development and testing, when attempting to read contents from an encrypted device offline (e.g. SD card for MinnowBoardMax or DragonBoard's eMMC through USB mass storage mode), 'diskpart' may be used to assign a drive letter to MainOS and Data volume (let's assume v: for MainOS and w: for Data).</span></span>
<span data-ttu-id="81253-261">볼륨 잠긴 표시 되며 수동으로 잠금이 해제 되도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="81253-261">The volumes will appear locked and need to be manually unlocked.</span></span> <span data-ttu-id="81253-262">OEM DRA.pfx 인증서가 설치 되어 있는 모든 컴퓨터에서이 작업을 수행할 수 있습니다 (에 포함 된 [DeviceLockDown 샘플](https://github.com/ms-iot/security/tree/master/TurnkeySecurity)).</span><span class="sxs-lookup"><span data-stu-id="81253-262">This can be done on any machine that has the OEM-DRA.pfx certificate installed (included in the [DeviceLockDown sample](https://github.com/ms-iot/security/tree/master/TurnkeySecurity)).</span></span> <span data-ttu-id="81253-263">PFX를 설치 하 고 관리 CMD 프롬프트에서 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="81253-263">Install the PFX and then run the following commands from an administrative CMD prompt:</span></span>

* `manage-bde -unlock v: -cert -cf OEM-DRA.cer`
* `manage-bde -unlock w: -cert -cf OEM-DRA.cer`

<span data-ttu-id="81253-264">콘텐츠를 오프 라인으로 자주 액세스 됨 해야 하는 경우 BitLocker 잠금 설정할 수 있습니다 볼륨에 대 한 초기 다음 명령을 사용 하 여 잠금을 해제 한 후:</span><span class="sxs-lookup"><span data-stu-id="81253-264">If the contents need to be frequently accessed offline, BitLocker autounlock can be set up for the volumes after the initial unlock using the following commands:</span></span>

* `manage-bde -autounlock v: -enable`
* `manage-bde -autounlock w: -enable`

### <a name="disabling-bitlocker"></a><span data-ttu-id="81253-265">BitLocker를 사용 하지 않도록 설정</span><span class="sxs-lookup"><span data-stu-id="81253-265">Disabling BitLocker</span></span>

<span data-ttu-id="81253-266">일시적으로 BitLocker를 사용 하지 않도록 설정 해야 발생할 수 있습니다는 다음 명령 실행 하 고 IoT 장치를 사용 하 여 원격 PowerShell 세션을 시작할: `sectask.exe -disable`합니다.</span><span class="sxs-lookup"><span data-stu-id="81253-266">Should there arise a need to temporarily disable BitLocker, initate a remote PowerShell session with your IoT device and run the following command: `sectask.exe -disable`.</span></span>  

> [!NOTE]
> <span data-ttu-id="81253-267">예약 된 암호화 작업이 비활성화 되어 있지 않으면 장치 암호화 후속 장치 부팅 시 다시 활성화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="81253-267">Device encryption will be re-enabled on subsequent device boot unless the scheduled encryption task is disabled.</span></span>


