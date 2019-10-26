---
title: Windows 10 IoT Core에서 보안 부팅, BitLocker 및 Device Guard 사용
ms.date: 08/28/2017
ms.topic: article
description: Windows 10 IoT Core에서 보안 부팅, BitLocker 및 Device Guard를 사용 하도록 설정 하는 방법을 알아봅니다.
keywords: windows iot, 보안 부팅, BitLocker, device guard, 보안, 턴키 보안
ms.openlocfilehash: 00e2abf82a043dfebe956281995961692b45c3b9
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918536"
---
# <a name="enabling-secure-boot-bitlocker-and-device-guard-on-windows-10-iot-core"></a><span data-ttu-id="76d1d-104">Windows 10 IoT Core에서 보안 부팅, BitLocker 및 Device Guard 사용</span><span class="sxs-lookup"><span data-stu-id="76d1d-104">Enabling Secure Boot, BitLocker, and Device Guard on Windows 10 IoT Core</span></span>

<span data-ttu-id="76d1d-105">Windows 10 IoT Core는 UEFI 보안 부팅, BitLocker 장치 암호화 및 Device Guard와 같은 보안 기능 제공을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-105">Windows 10 IoT Core includes security feature offerings such as UEFI Secure Boot, BitLocker Device Encryption and Device Guard.</span></span>  <span data-ttu-id="76d1d-106">이러한 기능은 다양 한 유형의 공격에 탄력적으로 복원 가능한 완전히 잠긴 Windows IoT 장치를 만드는 장치 빌더가 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-106">These will assist device builders in creating fully locked down Windows IoT devices that are resilient to many different types of attacks.</span></span>  <span data-ttu-id="76d1d-107">이러한 기능은 장치 암호화를 사용 하 여 알 수 없는 이진 파일을 잠그고 사용자 데이터를 보호 하는 동시에 정의 된 방식으로 플랫폼이 시작 되도록 하는 최적의 보호를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-107">Together, these features provide the optimal protection that ensures that a platform will launch in a defined way, while locking out unknown binaries and protecting user data through the use of device encryption.</span></span>

## <a name="boot-order"></a><span data-ttu-id="76d1d-108">부팅 순서</span><span class="sxs-lookup"><span data-stu-id="76d1d-108">Boot Order</span></span>

<span data-ttu-id="76d1d-109">IoT 장치에 대 한 보안 플랫폼을 제공 하는 개별 구성 요소에 대해 자세히 살펴보기 전에 Windows 10 IoT Core 장치에서 부팅 순서를 이해 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-109">An understanding of the boot order on a Windows 10 IoT Core device is needed before we can delve into the individual components that provide a secure platform for the IoT device.</span></span>

<span data-ttu-id="76d1d-110">IoT 장치의 전원이 켜 졌을 때에서 발생 하는 세 가지 주요 영역은 OS 커널 로드 및 설치 된 응용 프로그램 실행까지 모든 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-110">There are three main areas that occur from when an IoT device is powered on, all the way through to the OS kernel loading and execution of installed application.</span></span>

* <span data-ttu-id="76d1d-111">플랫폼 보안 부팅</span><span class="sxs-lookup"><span data-stu-id="76d1d-111">Platform Secure Boot</span></span>
* <span data-ttu-id="76d1d-112">UEFI(Unified Extensible Firmware Interface) (UEFI) 보안 부팅</span><span class="sxs-lookup"><span data-stu-id="76d1d-112">Unified Extensible Firmware Interface (UEFI) Secure Boot</span></span>
* <span data-ttu-id="76d1d-113">Windows 코드 무결성</span><span class="sxs-lookup"><span data-stu-id="76d1d-113">Windows Code Integrity</span></span>

![부팅 순서](../media/SecureBootAndBitLocker/BootOrder.jpg)

<span data-ttu-id="76d1d-115">Windows 10 부팅 프로세스에 대 한 추가 정보는 [여기](https://docs.microsoft.com/windows/security/information-protection/secure-the-windows-10-boot-process)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="76d1d-115">Additional information on the Windows 10 boot process can be found [here](https://docs.microsoft.com/windows/security/information-protection/secure-the-windows-10-boot-process).</span></span>

## <a name="locking-down-iot-devices"></a><span data-ttu-id="76d1d-116">IoT 장치 잠금 해제</span><span class="sxs-lookup"><span data-stu-id="76d1d-116">Locking-down IoT Devices</span></span>

<span data-ttu-id="76d1d-117">Windows IoT 장치를 잠금으로 설정 하려면 다음 사항을 고려해 야 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-117">In order to lockdown a Windows IoT device, the following considerations must be made.</span></span>

### <a name="platform-secure-boot"></a><span data-ttu-id="76d1d-118">플랫폼 보안 부팅</span><span class="sxs-lookup"><span data-stu-id="76d1d-118">Platform Secure Boot</span></span>

<span data-ttu-id="76d1d-119">장치를 처음 켤 때 전체 부팅 프로세스의 첫 번째 단계는 펌웨어 부팅 로더를 로드 하 고 실행 하는 것입니다 .이는 장치의 하드웨어를 초기화 하 고 응급 플래시 기능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-119">When the device is first powered on, the first step in the overall boot process is to load and run firmware boot loaders, which initialize the hardware on the devies and provide emergency flashing functionality.</span></span> <span data-ttu-id="76d1d-120">그런 다음 UEFI 환경을 로드 하 고 제어를 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-120">The UEFI environment is then loaded and control is handed over.</span></span>

<span data-ttu-id="76d1d-121">이러한 펌웨어 부팅 로더는 SoC와 관련 되어 있으므로 해당 장치 제조업체와 협력 하 여 이러한 부팅 로더가 장치에 생성 되도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-121">These firmware boot loaders are SoC-specific, so you will need to work with the appropriate device manufacturer to have these boot loaders created on the device.</span></span>

### <a name="uefi-secure-boot"></a><span data-ttu-id="76d1d-122">UEFI 보안 부팅</span><span class="sxs-lookup"><span data-stu-id="76d1d-122">UEFI Secure Boot</span></span>

<span data-ttu-id="76d1d-123">UEFI 보안 부팅은 첫 번째 정책 적용 지점이 며 UEFI에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-123">UEFI Secure Boot is the first policy enforcement point, and is located in UEFI.</span></span>  <span data-ttu-id="76d1d-124">펌웨어 드라이버, 옵션 Rom, UEFI 드라이버 또는 응용 프로그램, UEFI 부팅 로더 등 지정 된 기관에서 서명한 이진 파일의 실행만 허용 하도록 시스템을 제한 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-124">It restricts the system to only allow execution of binaries signed by a specified authority, such as firmware drivers, option ROMs, UEFI drivers or applications, and UEFI boot loaders.</span></span> <span data-ttu-id="76d1d-125">이 기능은 플랫폼에서 알 수 없는 코드가 실행 되는 것을 방지 하 고 잠재적으로 보안 상태를 약화 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-125">This feature prevents unknown code from being executed on the platform and potentially weakening the security posture of it.</span></span> <span data-ttu-id="76d1d-126">보안 부팅은 장치에 대 한 사전 부팅 맬웨어 공격 (예: 루트킷)의 위험을 줄여줍니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-126">Secure Boot reduces the risk of pre-boot malware attacks to the device, such as rootkits.</span></span> 

<span data-ttu-id="76d1d-127">OEM으로 서는 제조할 때 IoT 장치에 UEFI 보안 부팅 데이터베이스를 저장 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-127">As the OEM, you need to store the UEFI Secure Boot databases on the IoT device at manufacture time.</span></span> <span data-ttu-id="76d1d-128">이러한 데이터베이스에는 서명 데이터베이스 (db), 해지 된 서명 데이터베이스 (.dbx) 및 키 등록 키 데이터베이스 (KEK)가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-128">These databases include the Signature database (db), Revoked Signature database (dbx), and the Key Enrollment Key database (KEK).</span></span> <span data-ttu-id="76d1d-129">이러한 데이터베이스는 장치의 펌웨어 비휘발성 RAM (NV-RAM)에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-129">These databases are stored on the firmware nonvolatile RAM (NV-RAM) of the device.</span></span>

* <span data-ttu-id="76d1d-130">**서명 데이터베이스 (db):** 그러면 장치에 로드 될 수 있는 운영 체제 로더, UEFI 응용 프로그램 및 UEFI 드라이버의 서명자 또는 이미지 해시가 나열 됩니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-130">**Signature Database (db):** This lists the signers or image hashes of operating system loaders, UEFI applications and UEFI drivers that are allowed to be loaded on the device</span></span>

* <span data-ttu-id="76d1d-131">**해지 된 서명 데이터베이스 (.dbx):** 이는 더 이상 신뢰할 수 없고 장치에 로드 *될 수 없는* 운영 체제 로더, uefi 응용 프로그램 및 uefi 드라이버의 서명자 또는 이미지 해시를 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-131">**Revoked Signature Database (dbx):** This lists the signers or image hashes of operating system loaders, UEFI applications and UEFI drivers that are no longer trusted, and are *NOT* allowed to be loaded on the device</span></span> 

* <span data-ttu-id="76d1d-132">**키 등록 키 데이터베이스 (KEK):** 서명 및 해지 된 서명 데이터베이스를 업데이트 하는 데 사용할 수 있는 서명 키의 목록을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-132">**Key Enrollment Key database (KEK):** Contains a list of signing keys that can be used to update the signature and revoked signature databases.</span></span>

<span data-ttu-id="76d1d-133">이러한 데이터베이스가 만들어지고 장치에 추가 되 면 OEM은 편집에서 펌웨어를 잠그고 PK (플랫폼 서명 키)를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-133">Once these databases are created and added to the device, the OEM locks the firmware from editing, and generates a platform signing key (PK).</span></span> <span data-ttu-id="76d1d-134">이 키는 KEK에 대 한 업데이트에 서명 하거나 UEFI 보안 부팅을 사용 하지 않도록 설정 하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-134">This key can be used to sign updates to the KEK or to disable UEFI Secure Boot.</span></span>

<span data-ttu-id="76d1d-135">UEFI 보안 부팅에서 수행 하는 단계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-135">Here are the steps taken by UEFI Secure Boot:</span></span>

1. <span data-ttu-id="76d1d-136">장치의 전원이 켜진 후에 서명 데이터베이스는 각각 PK (플랫폼 서명 키)에 대해 확인 됩니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-136">After the device is powered on, the signature databases are each checked against the platform signing key (PK).</span></span>
2. <span data-ttu-id="76d1d-137">펌웨어가 트러스트 되지 않은 경우 UEFI 펌웨어는 OEM 특정 복구를 시작 하 여 신뢰할 수 있는 펌웨어를 복원 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-137">If the firmware isn't trusted, UEFI firmware initiates OEM-specific recovery to restore trusted firmware.</span></span>
3. <span data-ttu-id="76d1d-138">Windows 부팅 관리자를 로드할 수 없는 경우 펌웨어는 Windows 부팅 관리자의 백업 복사본을 부팅 하려고 시도 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-138">If Windows Boot Manager cannot be loaded, the firmware will attempt to boot a backup copy of Windows Boot Manager.</span></span> <span data-ttu-id="76d1d-139">그래도 오류가 발생 하면 UEFI 펌웨어가 OEM 관련 수정을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-139">If this also fails, the UEFI firmware initiates OEM-specific remediation.</span></span>
4. <span data-ttu-id="76d1d-140">Windows 부팅 관리자가 Windows 커널의 디지털 서명을 실행 하 고 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-140">Windows Boot Manager runs and verifies the digital signature of the Windows Kernel.</span></span> <span data-ttu-id="76d1d-141">신뢰할 수 있는 경우 Windows 부팅 관리자가 Windows 커널로 제어를 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-141">If trusted, Windows Boot Manager passes control to the Windows Kernel.</span></span>

<span data-ttu-id="76d1d-142">키 만들기 및 관리 지침과 함께 보안 부팅에 대 한 추가 세부 정보는 [여기](https://technet.microsoft.com/library/dn747883.aspx)에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-142">Additional details on Secure Boot, along with key creation and management guidance, is available [here](https://technet.microsoft.com/library/dn747883.aspx).</span></span>

### <a name="windows-code-integrity"></a><span data-ttu-id="76d1d-143">Windows 코드 무결성</span><span class="sxs-lookup"><span data-stu-id="76d1d-143">Windows Code Integrity</span></span>

<span data-ttu-id="76d1d-144">Windows 코드 무결성 (WCI)은 메모리에 로드 될 때마다 드라이버 또는 응용 프로그램의 무결성을 확인 하 여 운영 체제의 보안을 향상 시킵니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-144">Windows Code Integrity (WCI) improves the security of the operating system by validating the integrity of a driver or application each time it is loaded into memory.</span></span> <span data-ttu-id="76d1d-145">CI에는 두 가지 주요 구성 요소인 KMCI (커널 모드 코드 무결성)와 UMCI (사용자 모드 코드 무결성)가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-145">CI contains two main components - Kernel Mode Code Integrity (KMCI) and User Mode Code Integrity (UMCI).</span></span>

<span data-ttu-id="76d1d-146">CCI (구성 가능한 코드 무결성)는 장치 빌더가 장치를 잠금 가능 하 게 하 고 서명 되 고 신뢰할 수 있는 코드를 실행 하 여 실행할 수 있도록 하는 Windows 10의 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-146">Configurable Code Integrity (CCI) is a feature in Windows 10 that allows device builders to lockdown a device and only allow it to run and execute code that is signed and trusted.</span></span>  <span data-ttu-id="76d1d-147">이렇게 하기 위해 장치 빌더는 ' 골든 ' 장치 (하드웨어 및 소프트웨어의 최종 릴리스 버전)에서 코드 무결성 정책을 만든 다음 공장에서 모든 장치에 대해이 정책을 보호 하 고 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-147">To do so, device builders can create a code integrity policy on a 'golden' device (final release version of hardware and software) and then secure and apply this policy on all devices on the factory floor.</span></span>

<span data-ttu-id="76d1d-148">코드 무결성 정책, 감사 및 적용을 배포 하는 방법에 대 한 자세한 내용은 [여기](https://technet.microsoft.com/itpro/windows/keep-secure/deploy-code-integrity-policies-steps)에서 최신 technet 설명서를 확인 하세요.</span><span class="sxs-lookup"><span data-stu-id="76d1d-148">To learn more about deploying code integrity policies, auditing and enforcement, check out the latest technet documentation [here](https://technet.microsoft.com/itpro/windows/keep-secure/deploy-code-integrity-policies-steps).</span></span>

<span data-ttu-id="76d1d-149">Windows 코드 무결성에서 수행 하는 단계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-149">Here are the steps taken by Windows Code Integrity:</span></span>

1. <span data-ttu-id="76d1d-150">Windows 커널은 로드 전에 서명 데이터베이스에 대해 다른 모든 구성 요소를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-150">Windows Kernel will verify all other components against the signature database before loading.</span></span> <span data-ttu-id="76d1d-151">여기에는 드라이버, 시작 파일 및 ELAM (맬웨어 방지 조기 실행)이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-151">This includes drivers, startup files and ELAM (Early Launch Anti-Malware).</span></span>
2. <span data-ttu-id="76d1d-152">Windows 커널이 시작 프로세스에서 신뢰할 수 있는 구성 요소를 로드 하 고 신뢰할 수 없는 구성 요소를 로드 하는 것을 금지 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-152">Windows Kernel will load the trusted components in the startup process, and prohibit loading of the untrusted components.</span></span>
3. <span data-ttu-id="76d1d-153">Windows 10 IoT Core 운영 체제가 설치 된 모든 응용 프로그램과 함께 로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-153">Windows 10 IoT Core operating system loads, along with any installed applications.</span></span>

### <a name="bitlocker-device-encryption"></a><span data-ttu-id="76d1d-154">BitLocker 장치 암호화</span><span class="sxs-lookup"><span data-stu-id="76d1d-154">BitLocker Device Encryption</span></span>

<span data-ttu-id="76d1d-155">또한 Windows 10 IoT Core는 경량 버전의 BitLocker 장치 암호화를 구현 하 여 오프 라인 공격 으로부터 IoT 장치를 보호 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-155">Windows 10 IoT Core also implements a lightweight version of BitLocker Device Encryption, protecting IoT devices against offline attacks.</span></span> <span data-ttu-id="76d1d-156">이 기능은 UEFI에서 필요한 측정을 수행 하는 필수 사전 OS 프로토콜을 포함 하 여 TPM의 존재에 대 한 강력한 종속성을 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-156">This capability has a strong dependency on the presence of a TPM on the platform, including the necessary pre-OS protocol in UEFI that conducts the necessary measurements.</span></span> <span data-ttu-id="76d1d-157">이러한 OS 이전 측정은 나중에 os가 실행 되는 방법에 대 한 결정적인 기록이 있는지 확인 합니다. 그러나 실행 제한을 적용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-157">These pre-OS measurements ensure that the OS later has a definitive record of how the OS was launched; however, it does not enforce any execution restrictions.</span></span>

> [!TIP]
> <span data-ttu-id="76d1d-158">Windows 10 IoT Core의 BitLocker 기능을 사용 하면 사용 가능한 모든 NTFS 데이터 볼륨을 바인딩하는 동안 NTFS 기반 OS 볼륨을 자동으로 암호화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-158">BitLocker functionality on Windows 10 IoT Core allows for automatic encryption of NTFS-based OS volume while binding all available NTFS data volumes to it.</span></span> <span data-ttu-id="76d1d-159">이를 위해 EFIESP 볼륨 GUID가 _C12A7328-F81F-11D2-BA4B-00A0C93EC93B_으로 설정 되어 있는지 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-159">For this, it’s necessary to ensure that the EFIESP volume GUID is set to _C12A7328-F81F-11D2-BA4B-00A0C93EC93B_.</span></span>

### <a name="device-guard-on-windows-iot-core"></a><span data-ttu-id="76d1d-160">Windows IoT Core의 Device Guard</span><span class="sxs-lookup"><span data-stu-id="76d1d-160">Device Guard on Windows IoT Core</span></span>

<span data-ttu-id="76d1d-161">대부분의 IoT 장치는 고정 된 기능 장치로 빌드됩니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-161">Most IoT devices are built as fixed-function devices.</span></span> <span data-ttu-id="76d1d-162">이는 장치 빌더가 지정 된 장치에서 실행 해야 하는 펌웨어, 운영 체제, 드라이버 및 응용 프로그램을 정확 하 게 알고 있음을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-162">This implies that device builders know exactly which firmware, operating system, drivers and applications should be running on a given device.</span></span> <span data-ttu-id="76d1d-163">또한이 정보는 알려진 코드와 신뢰할 수 있는 코드의 실행만 허용 하 여 IoT 장치를 완전히 잠그는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-163">In turn, this information can be used to fully lockdown an IoT device by only allowing execution of known and trusted code.</span></span> <span data-ttu-id="76d1d-164">Windows 10 IoT Core의 Device Guard는 잠긴 장치에서 알 수 없거나 신뢰할 수 없는 실행 코드를 실행할 수 없도록 하 여 IoT 장치를 보호 하는 데 도움이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-164">Device Guard on Windows 10 IoT Core can help protect IoT devices by ensuring that unknown or untrusted executable code cannot be run on locked-down devices.</span></span>


## <a name="turnkey-security-on-iot-core"></a><span data-ttu-id="76d1d-165">IoT Core의 턴키 보안</span><span class="sxs-lookup"><span data-stu-id="76d1d-165">Turnkey Security on IoT Core</span></span>

<span data-ttu-id="76d1d-166">IoT Core 장치에서 주요 보안 기능을 쉽게 사용할 수 있도록 Microsoft는 장치 빌더가 완전히 잠긴 IoT 장치를 빌드할 수 있는 [턴키 보안 패키지]( https://github.com/ms-iot/security/tree/master/TurnkeySecurity) 를 제공 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-166">To facilitate easy enablement of key security features on IoT Core devices, Microsoft is providing a [Turnkey Security Package]( https://github.com/ms-iot/security/tree/master/TurnkeySecurity) that allows device builders to build fully locked down IoT devices.</span></span> <span data-ttu-id="76d1d-167">이 패키지는 다음에 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-167">This package will help with:</span></span>

* <span data-ttu-id="76d1d-168">보안 부팅 키 프로 비전 및 지원 되는 IoT 플랫폼에서 기능 사용</span><span class="sxs-lookup"><span data-stu-id="76d1d-168">Provisioning Secure Boot keys and enabling the feature on supported IoT platforms</span></span>
* <span data-ttu-id="76d1d-169">BitLocker를 사용 하 여 장치 암호화 설정 및 구성</span><span class="sxs-lookup"><span data-stu-id="76d1d-169">Setup and configuration of device encryption using BitLocker</span></span>
* <span data-ttu-id="76d1d-170">서명 된 응용 프로그램 및 드라이버 실행만 허용 하도록 장치 잠금 시작</span><span class="sxs-lookup"><span data-stu-id="76d1d-170">Initiating device lockdown to only allow execution of signed applications and drivers</span></span>

<span data-ttu-id="76d1d-171">다음 단계에서는 [턴키 보안 패키지]( https://github.com/ms-iot/security/tree/master/TurnkeySecurity) 를 사용 하 여 잠금 이미지를 만드는 과정을 안내 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-171">The following steps will lead through the process to create a lockdown image using the [Turnkey Security Package]( https://github.com/ms-iot/security/tree/master/TurnkeySecurity)</span></span>

![잠금 이미지 만들기](../media/SecurityFlowAndCertificates/ImageLockDown.png)

### <a name="prerequisites"></a><span data-ttu-id="76d1d-173">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="76d1d-173">Prerequisites</span></span>

* <span data-ttu-id="76d1d-174">Windows 10 Enterprise를 실행 하는 PC (다른 Windows 버전은 제공 된 스크립트에서 지원 **되지 않음** )</span><span class="sxs-lookup"><span data-stu-id="76d1d-174">A PC running Windows 10 Enterprise (other Windows versions are **not** supported by the provided scripts)</span></span> 
* <span data-ttu-id="76d1d-175">[Windows 10 SDK](https://developer.microsoft.com/en-US/windows/downloads/windows-10-sdk) -인증서 생성에 필요</span><span class="sxs-lookup"><span data-stu-id="76d1d-175">[Windows 10 SDK](https://developer.microsoft.com/en-US/windows/downloads/windows-10-sdk) - Required for Certificate Generation</span></span>
* <span data-ttu-id="76d1d-176">[Windows 10 ADK](https://developer.microsoft.com/en-us/windows/hardware/windows-assessment-deployment-kit) -CAB 생성에 필요</span><span class="sxs-lookup"><span data-stu-id="76d1d-176">[Windows 10 ADK](https://developer.microsoft.com/en-us/windows/hardware/windows-assessment-deployment-kit) - Required for CAB generation</span></span>
* <span data-ttu-id="76d1d-177">최종 잠금에 대 한 배송 펌웨어, OS, 드라이버 및 응용 프로그램을 사용 하 여 플랫폼 릴리스 하드웨어 참조</span><span class="sxs-lookup"><span data-stu-id="76d1d-177">Reference platform - release hardware with shipping firmware, OS, drivers and applications will be required for final lockdown</span></span>

### <a name="development-iot-devices"></a><span data-ttu-id="76d1d-178">개발 IoT 장치</span><span class="sxs-lookup"><span data-stu-id="76d1d-178">Development IoT Devices</span></span>

<span data-ttu-id="76d1d-179">Windows 10 IoT Core는 수백 개의 장치에서 활용 되는 다양 한 silicons에서 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-179">Windows 10 IoT Core works with various silicons that are utilized in hundreds of devices.</span></span> <span data-ttu-id="76d1d-180">제안 된 [IoT 개발 장치](../learn-about-hardware/SoCsAndCustomBoards.md)중에서 다음은 보안 부팅, 측정 된 부팅, BitLocker 및 Device Guard 기능과 함께 펌웨어 TPM 기능을 즉시 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-180">Of the [suggested IoT development devices](../learn-about-hardware/SoCsAndCustomBoards.md), the following provide firmware TPM functionality out of the box, along with Secure Boot, Measured Boot, BitLocker and Device Guard capabilities:</span></span>

* <span data-ttu-id="76d1d-181">Qualcomm DragonBoard 410c</span><span class="sxs-lookup"><span data-stu-id="76d1d-181">Qualcomm DragonBoard 410c</span></span>

    <span data-ttu-id="76d1d-182">보안 부팅을 사용 하려면 RPMB를 프로 비전 해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-182">In order to enable Secure Boot, it may be necessary to provision RPMB.</span></span> <span data-ttu-id="76d1d-183">Windows 10 IoT Core를 사용 하 여 eMMC가 제공 되 면 ( [여기](https://docs.microsoft.com/windows/iot-core/tutorials/quickstarter/devicesetup#using-the-iot-dashboard-dragonboard-410c)에 설명 된 대로) 전원을 켤 때 장치에서 [전원] + [vol +] + [vol-]을 동시에 누르고 bds 메뉴에서 "RPMB 프로 비전"을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-183">Once the eMMC has been flashed with Windows 10 IoT Core (as per instructions [here](https://docs.microsoft.com/windows/iot-core/tutorials/quickstarter/devicesetup#using-the-iot-dashboard-dragonboard-410c), press [Power] + [Vol+] + [Vol-] simultaneously on the device when powering up and select "Provision RPMB" from the BDS menu.</span></span> <span data-ttu-id="76d1d-184">*이는 되돌릴 수 없는 단계입니다.*</span><span class="sxs-lookup"><span data-stu-id="76d1d-184">*Please note that this is an irreversible step.*</span></span>

* <span data-ttu-id="76d1d-185">Intel MinnowBoardMax</span><span class="sxs-lookup"><span data-stu-id="76d1d-185">Intel MinnowBoardMax</span></span>

    <span data-ttu-id="76d1d-186">Intel의 MinnowBoard Max의 경우 펌웨어 버전은 0.82 이상 이어야 합니다 ( [최신 펌웨어](https://firmware.intel.com/projects/minnowboard-max)다운로드).</span><span class="sxs-lookup"><span data-stu-id="76d1d-186">For Intel's MinnowBoard Max, firmware version must be 0.82 or higher (get the [latest firmware](https://firmware.intel.com/projects/minnowboard-max)).</span></span> <span data-ttu-id="76d1d-187">TPM 기능을 사용 하도록 설정 하려면 키보드를 사용 하 여 보드를 켜고, 연결 된 & 표시 하 고 F2 키를 눌러 UEFI 설치를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-187">To enable TPM capabilities, power up board with a keyboard & display attached and press F2 to enter UEFI setup.</span></span> <span data-ttu-id="76d1d-188">_Device Manager-> 시스템 설정-> 보안 구성-> PTT_ 로 이동 하 고&lt;_사용_ &gt;로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-188">Go to _Device Manager -> System Setup -> Security Configuration -> PTT_ and set it to _&lt;Enable&gt;_.</span></span> <span data-ttu-id="76d1d-189">F10 키를 눌러 변경 내용을 저장 하 고 플랫폼 다시 부팅을 진행 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-189">Press F10 to save changes and proceed with a reboot of the platform.</span></span>

> [!NOTE]
> <span data-ttu-id="76d1d-190">Raspberry Pi 2 또는 3은 TPM을 지원 하지 않으므로 잠금 시나리오를 구성할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-190">Raspberry Pi 2 nor 3 do not support TPM and so we cannot configure Lockdown scenarios.</span></span>

### <a name="generate-lockdown-packages"></a><span data-ttu-id="76d1d-191">잠금 패키지 생성</span><span class="sxs-lookup"><span data-stu-id="76d1d-191">Generate Lockdown Packages</span></span>

1. <span data-ttu-id="76d1d-192">장치를 구성 하 고 잠그기 위해 필요한 추가 도구 및 스크립트를 모두 포함 하는 [Devicelockdown 스크립트](https://github.com/ms-iot/security/tree/master/TurnkeySecurity) 패키지를 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-192">Download the [DeviceLockDown Script](https://github.com/ms-iot/security/tree/master/TurnkeySecurity) package, which contains all of the additional tools and scripts required for configuring and locking down devices</span></span>
2. <span data-ttu-id="76d1d-193">Windows 10 PC에서 PS (관리 PowerShell) 콘솔을 시작 하 고 다운로드 한 스크립트의 위치로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-193">Start an Administrative PowerShell (PS) console on your Windows 10 PC and navigate to the location of the downloaded script.</span></span>
3. <span data-ttu-id="76d1d-194">을 사용 하 여 네트워크 공유를 통해 PC에 참조 하드웨어 플랫폼 (잠금 해제 된 이미지 실행) 탑재</span><span class="sxs-lookup"><span data-stu-id="76d1d-194">Mount your reference hardware platform (running the unlocked image) to your PC via network share using</span></span>

    ```powershell
    net use \\a.b.c.d\c$ /user:username password
    ```

4. <span data-ttu-id="76d1d-195">를 사용 하 여 장치에 대 한 키 생성</span><span class="sxs-lookup"><span data-stu-id="76d1d-195">Generate keys for your device using</span></span>

    ```powershell
    .\GenerateKeys.ps1 -OemName '<your oem name>' -outputPath '<output directory>'
    ```

    * <span data-ttu-id="76d1d-196">키와 인증서가 지정 된 출력 폴더에 적절 한 접미사로 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-196">The keys and certificates are generated in the specified output folder with appropriate suffix.</span></span>
    * <span data-ttu-id="76d1d-197">장치는 잠금 후에만 이러한 키로 서명 된 이진 파일을 신뢰 하므로 **생성 된 키의 보안을 유지** 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-197">**Secure your generated keys** as the device will trust binaries signed with these keys only after lockdown.</span></span>
    * <span data-ttu-id="76d1d-198">이 단계를 건너뛰고 테스트용 으로만 미리 생성 된 키를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-198">You may skip this step and use the pre-generated keys for testing only</span></span>

5. <span data-ttu-id="76d1d-199">_설정 .xml_ 구성</span><span class="sxs-lookup"><span data-stu-id="76d1d-199">Configure _settings.xml_</span></span>

    * <span data-ttu-id="76d1d-200">일반 섹션: 패키지 디렉터리 지정</span><span class="sxs-lookup"><span data-stu-id="76d1d-200">General section : Specify the package directories</span></span>
    * <span data-ttu-id="76d1d-201">도구 섹션: 도구에 대 한 경로 설정</span><span class="sxs-lookup"><span data-stu-id="76d1d-201">Tools section : Set the path for the tools</span></span>
        * <span data-ttu-id="76d1d-202">Windows10KitsRoot `(e.g. <Windows10KitsRoot>C:\Program Files (x86)\Windows Kits\10\</Windows10KitsRoot>)`</span><span class="sxs-lookup"><span data-stu-id="76d1d-202">Windows10KitsRoot `(e.g. <Windows10KitsRoot>C:\Program Files (x86)\Windows Kits\10\</Windows10KitsRoot>)`</span></span>
        * <span data-ttu-id="76d1d-203">WindowsSDKVersion `(e.g. <WindowsSDKVersion>10.0.15063.0</WindowsSDKVersion>)`</span><span class="sxs-lookup"><span data-stu-id="76d1d-203">WindowsSDKVersion `(e.g. <WindowsSDKVersion>10.0.15063.0</WindowsSDKVersion>)`</span></span>
            * <span data-ttu-id="76d1d-204">컴퓨터에 설치 된 SDK 버전이 `C:\Program Files (x86)\Windows Kits\10\`에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-204">SDK version installed on your machine is under `C:\Program Files (x86)\Windows Kits\10\`</span></span>
    * <span data-ttu-id="76d1d-205">SecureBoot 섹션: 보안 부팅에 사용할 키를 지정 합니다 (PK 및 SB 키).</span><span class="sxs-lookup"><span data-stu-id="76d1d-205">SecureBoot section : Specify which keys to use for secure boot (PK and SB keys)</span></span>
    * <span data-ttu-id="76d1d-206">BitLocker 섹션: Bitlocker 데이터 복구에 대 한 인증서 지정 (DRA 키)</span><span class="sxs-lookup"><span data-stu-id="76d1d-206">BitLocker section : Specify a certificate for Bitlocker data recovery (DRA key)</span></span>
    * <span data-ttu-id="76d1d-207">SIPolicy 섹션: 신뢰할 수 있는 인증서를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-207">SIPolicy section : Specify certs that should be trusted</span></span>
        * <span data-ttu-id="76d1d-208">ScanPath: 이진 파일을 검색 하기 위한 장치의 경로 `\\a.b.c.d\C$`</span><span class="sxs-lookup"><span data-stu-id="76d1d-208">ScanPath : Path of the device for scanning binaries , `\\a.b.c.d\C$`</span></span>
        * <span data-ttu-id="76d1d-209">업데이트: SIPolicy (PAUTH 키)의 서명자</span><span class="sxs-lookup"><span data-stu-id="76d1d-209">Update   : Signer of the SIPolicy (PAUTH keys)</span></span>
        * <span data-ttu-id="76d1d-210">사용자: 사용자 모드 인증서 (UMCI 키)</span><span class="sxs-lookup"><span data-stu-id="76d1d-210">User     : User mode certificates (UMCI keys)</span></span> 
        * <span data-ttu-id="76d1d-211">커널: 커널 모드 인증서 (KMCI 키)</span><span class="sxs-lookup"><span data-stu-id="76d1d-211">Kernel   : Kernel mode certificates (KMCI keys)</span></span>
    * <span data-ttu-id="76d1d-212">패키징: 패키지 생성에 대 한 설정을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-212">Packaging : Specify the settings for the package generation</span></span>

> [!IMPORTANT]
> <span data-ttu-id="76d1d-213">초기 개발 주기 중 테스트를 지원 하기 위해 Microsoft는 해당 하는 경우 미리 생성 된 키 및 인증서를 제공 했습니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-213">In order to assist with testing during the initial development cycle, Microsoft has provided pre-generated keys and certificates where appropriate.</span></span>  <span data-ttu-id="76d1d-214">이는 Microsoft 테스트, 개발 및 시험판 이진 파일이 신뢰할 수 있는 것으로 간주 됨을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-214">This implies that Microsoft Test, Development and Pre-Release binaries are considered trusted.</span></span>  <span data-ttu-id="76d1d-215">최종 제품을 만들고 이미지를 생성 하는 동안 이러한 인증서를 제거 하 고 자신의 키를 사용 하 여 완전히 잠기는 장치를 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-215">During final product creation and image generation, be sure to remove these certifcates and use your own keys to ensure a fully locked down device.</span></span>

<span data-ttu-id="76d1d-216">6. 다음 명령을 실행 하 여 필요한 패키지를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-216">6.Execute the following commands to generate required packages:</span></span>

    ```powershell
    Import-Module .\IoTTurnkeySecurity.psm1
    # Generate the security packages for retail
    New-IoTTurnkeySecurity -ConfigFileName .\settings.xml
    (or)
    # Generate the security packages for test
    New-IoTTurnkeySecurity -ConfigFileName .\settings.xml -Test
    ```

### <a name="test-lockdown-packages"></a><span data-ttu-id="76d1d-217">잠금 패키지 테스트</span><span class="sxs-lookup"><span data-stu-id="76d1d-217">Test Lockdown packages</span></span>
<span data-ttu-id="76d1d-218">다음 단계를 수행 하 여 생성 된 패키지를 잠금이 해제 된 장치에 수동으로 설치 하 여 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-218">You can test the generated packages by manually installing them on a unlocked device by the following steps</span></span>

1. <span data-ttu-id="76d1d-219">잠금 해제 된 이미지를 사용 하 여 장치를 깜박입니다 (이전 단계에서 스캔 하는 데 사용 되는 이미지).</span><span class="sxs-lookup"><span data-stu-id="76d1d-219">Flash the device with the unlocked image (image used for scanning in earlier step).</span></span>
2. <span data-ttu-id="76d1d-220">장치에 연결 ([SSH 사용](../connect-your-device/SSH.md) 또는 [Powershell](../connect-your-device/PowerShell.md)사용)</span><span class="sxs-lookup"><span data-stu-id="76d1d-220">Connect to the device ([using SSH](../connect-your-device/SSH.md) or using [Powershell](../connect-your-device/PowerShell.md))</span></span>
3. <span data-ttu-id="76d1d-221">다음 .cab 파일을 디렉터리 아래의 장치에 복사 합니다 (예: `c:\OemInstall`</span><span class="sxs-lookup"><span data-stu-id="76d1d-221">Copy the following .cab files to the device under a directory e.g. `c:\OemInstall`</span></span>
    * <span data-ttu-id="76d1d-222">지원을. 사용자 지정 .Cmd .cab</span><span class="sxs-lookup"><span data-stu-id="76d1d-222">OEM.Custom.Cmd.cab</span></span>
    * <span data-ttu-id="76d1d-223">지원을. 보안. BitLocker .cab</span><span class="sxs-lookup"><span data-stu-id="76d1d-223">OEM.Security.BitLocker.cab</span></span>
    * <span data-ttu-id="76d1d-224">지원을. 보안. c a b .cab .cab</span><span class="sxs-lookup"><span data-stu-id="76d1d-224">OEM.Security.SecureBoot.cab</span></span>
    * <span data-ttu-id="76d1d-225">지원을. 보안. DeviceGuard .cab</span><span class="sxs-lookup"><span data-stu-id="76d1d-225">OEM.Security.DeviceGuard.cab</span></span>
4. <span data-ttu-id="76d1d-226">다음 명령을 issueing 여 생성 된 패키지의 준비를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-226">Initiate staging of the generated packages by issueing the following commands</span></span>

    ```C
    applyupdate -stage c:\OemInstall\OEM.Custom.Cmd.cab
    ```
    <span data-ttu-id="76d1d-227">사용자 지정 이미지를 사용 하는 경우이 파일을 *건너뛰고* `Output\OEMCustomization\OEMCustomization.cmd` 파일에서 사용할 수 있는 콘텐츠를 사용 하 여 `c:\windows\system32\oemcustomization.cmd`를 수동으로 편집 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-227">If you are using custom image, then you will have to *skip* this file and manually edit the `c:\windows\system32\oemcustomization.cmd` with the contents available in `Output\OEMCustomization\OEMCustomization.cmd` file</span></span>

    ```C
    applyupdate -stage c:\OemInstall\OEM.Security.BitLocker.cab
    applyupdate -stage c:\OemInstall\OEM.Security.SecureBoot.cab
    applyupdate -stage c:\OemInstall\OEM.Security.DeviceGuard.cab

5. Finally, commit the packages via

    ```C
    applyupdate -commit
    ```

6. <span data-ttu-id="76d1d-228">장치는 패키지를 설치 하기 위해 업데이트 OS (기어 표시)로 다시 부팅 되 고, 다시 주 OS로 다시 부팅 됩니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-228">The device will reboot into update OS (showing gears) to install the packages and will reboot again to main OS.</span></span>  <span data-ttu-id="76d1d-229">장치가 MainOS로 다시 부팅 되 면 보안 부팅이 사용 하도록 설정 되 고 SIPolicy를 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-229">Once the device reboots back into MainOS, Secure Boot will be enabled and SIPolicy should be engaged.</span></span>
7. <span data-ttu-id="76d1d-230">장치를 다시 부팅 하 여 Bitlocker 암호화를 활성화 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-230">Reboot the device again to activate the Bitlocker encryption.</span></span>
8. <span data-ttu-id="76d1d-231">보안 기능 테스트</span><span class="sxs-lookup"><span data-stu-id="76d1d-231">Test the security features</span></span>
    * <span data-ttu-id="76d1d-232">SecureBoot: `bcdedit /debug on` 시도 하면 보안 부팅 정책에 의해 값이 보호 됨을 나타내는 오류가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-232">SecureBoot: try `bcdedit /debug on` , you will get an error stating that the value is protected by secure boot policy</span></span>
    * <span data-ttu-id="76d1d-233">BitLocker: `start /wait sectask.exe -waitencryptcomplete:1`를 실행 합니다. ERRORLEVEL이 `-2147023436` (ERROR_TIMEOUT) 이면 암호화가 완료 되지 않은 것입니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-233">BitLocker: Run `start /wait sectask.exe -waitencryptcomplete:1`, if ERRORLEVEL is `-2147023436` (ERROR_TIMEOUT) then encryption is not complete.</span></span> <span data-ttu-id="76d1d-234">.Cmd 파일에서 sectask를 실행 하는 경우 `start /wait`를 생략 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-234">When running sectask.exe from a .cmd file omit the `start /wait`.</span></span>
    * <span data-ttu-id="76d1d-235">DeviceGuard: SIPolicy 목록에 없는 서명 된 이진 또는 이진 서명 된 인증서를 실행 하 고 실행이 실패 하는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-235">DeviceGuard : Run any unsigned binary or a binary signed with certificate not in the SIPolicy list and confirm that it fails to run.</span></span>

### <a name="generate-lockdown-image"></a><span data-ttu-id="76d1d-236">잠금 이미지 생성</span><span class="sxs-lookup"><span data-stu-id="76d1d-236">Generate Lockdown image</span></span>

<span data-ttu-id="76d1d-237">이전에 정의 된 설정에 따라 잠금 패키지가 작동 하는지 확인 한 후에는 다음 단계를 수행 하 여 이러한 패키지를 이미지에 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-237">After validating that the lockdown packages are working as per the settings defined earlier, you can then include these packages into the image by following the below given steps.</span></span> <span data-ttu-id="76d1d-238">사용자 지정 이미지 생성 지침은 [IoT 제조 가이드](https://aka.ms/iotcoreguide) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="76d1d-238">Read the [IoT manufacturing guide](https://aka.ms/iotcoreguide) for custom image creation instructions.</span></span>

1. <span data-ttu-id="76d1d-239">작업 영역 디렉터리에서 위의 생성 된 출력 디렉터리에서 다음 파일을 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-239">In the workspace directory, update the following files from the generated output directory above</span></span>
    * <span data-ttu-id="76d1d-240">SecureBoot: `Copy ..\Output\SecureBoot\*.bin  ..\Workspace\Common\Packages\Security.SecureBoot`</span><span class="sxs-lookup"><span data-stu-id="76d1d-240">SecureBoot : `Copy ..\Output\SecureBoot\*.bin  ..\Workspace\Common\Packages\Security.SecureBoot`</span></span>
      * <span data-ttu-id="76d1d-241">SetVariable_db</span><span class="sxs-lookup"><span data-stu-id="76d1d-241">SetVariable_db.bin</span></span>
      * <span data-ttu-id="76d1d-242">SetVariable_kek</span><span class="sxs-lookup"><span data-stu-id="76d1d-242">SetVariable_kek.bin</span></span>
      * <span data-ttu-id="76d1d-243">SetVariable_pk</span><span class="sxs-lookup"><span data-stu-id="76d1d-243">SetVariable_pk.bin</span></span>
    * <span data-ttu-id="76d1d-244">BitLocker: `Copy ..\Output\Bitlocker\*.* ..\Workspace\Common\Packages\Security.Bitlocker`</span><span class="sxs-lookup"><span data-stu-id="76d1d-244">BitLocker : `Copy ..\Output\Bitlocker\*.* ..\Workspace\Common\Packages\Security.Bitlocker`</span></span>
      * <span data-ttu-id="76d1d-245">DETask .xml</span><span class="sxs-lookup"><span data-stu-id="76d1d-245">DETask.xml</span></span>
      * <span data-ttu-id="76d1d-246">보안.</span><span class="sxs-lookup"><span data-stu-id="76d1d-246">Security.Bitlocker.wm.xml</span></span>
      * <span data-ttu-id="76d1d-247">설정. bitlocker.</span><span class="sxs-lookup"><span data-stu-id="76d1d-247">setup.bitlocker.cmd</span></span>
    * <span data-ttu-id="76d1d-248">DeviceGuard: `Copy ..\Output\DeviceGuard\*.*  ..\Workspace\Common\Packages\Security.DeviceGuard`</span><span class="sxs-lookup"><span data-stu-id="76d1d-248">DeviceGuard : `Copy ..\Output\DeviceGuard\*.*  ..\Workspace\Common\Packages\Security.DeviceGuard`</span></span>
      * <span data-ttu-id="76d1d-249">SIPolicyOn. p7b</span><span class="sxs-lookup"><span data-stu-id="76d1d-249">SIPolicyOn.p7b</span></span>
      * <span data-ttu-id="76d1d-250">SIPolicyOff. p7b</span><span class="sxs-lookup"><span data-stu-id="76d1d-250">SIPolicyOff.p7b</span></span>
  
2. <span data-ttu-id="76d1d-251">잠금 패키지 기능 ID를 사용 하 여 ProductName 디렉터리 아래에 RetailOEMInput 및 TestOEMInput를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-251">Add RetailOEMInput.xml and TestOEMInput.xml under the ProductName directory with lockdown package feature ID</span></span>
    * `<Feature>SEC_BITLOCKER</Feature>`
    * `<Feature>SEC_SECUREBOOT</Feature>`
    * `<Feature>SEC_DEVICEGUARD</Feature>`
3. <span data-ttu-id="76d1d-252">이미지 다시 생성</span><span class="sxs-lookup"><span data-stu-id="76d1d-252">Re-generate Image</span></span>
    * <span data-ttu-id="76d1d-253">`buildpkg all` (위의 정책 파일을 기반으로 새 잠금 패키지 생성)</span><span class="sxs-lookup"><span data-stu-id="76d1d-253">`buildpkg all` (this generates new lockdown packages based on above policy files)</span></span>
    * <span data-ttu-id="76d1d-254">`buildimage ProductName test(or)retail` (새 Flash .ffu 생성)</span><span class="sxs-lookup"><span data-stu-id="76d1d-254">`buildimage ProductName test(or)retail`  (this generates new Flash.ffu)</span></span>
4. <span data-ttu-id="76d1d-255">이 새로운 Flash .ffu를 사용 하 여 장치를 플래시 하 고 보안 기능의 유효성을 검사 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-255">Flash the device with this new Flash.ffu and validate the security features.</span></span>

<span data-ttu-id="76d1d-256">[SecureSample](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/SecureSample) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="76d1d-256">See [SecureSample](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/SecureSample) as an example of a lockdown dragon board configuration.</span></span>

<span data-ttu-id="76d1d-257">또는 IoTCore Shell 자체에서 보안 패키지를 생성할 수 있습니다. 자세한 내용은 [보안 패키지 추가](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools#adding-security-packages) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="76d1d-257">Alternatively, you can generate the security packages in the IoTCore Shell itself, see [adding security packages](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools#adding-security-packages) for the details.</span></span>


### <a name="developing-with-codesigning-enforcement-enabled"></a><span data-ttu-id="76d1d-258">코드 서명 적용을 사용 하 여 개발</span><span class="sxs-lookup"><span data-stu-id="76d1d-258">Developing with CodeSigning Enforcement Enabled</span></span>

<span data-ttu-id="76d1d-259">패키지가 생성 되 고 잠금이 활성화 되 면 개발 중에 이미지에 도입 된 이진 파일을 적절 하 게 서명 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-259">Once the packages are generated and lockdown is activated, any binaries introduced into the image during development will need to be signed appropriately.</span></span> <span data-ttu-id="76d1d-260">사용자 모드 이진 파일이 _.\Keys\ \* \* \*-UMCI .pfx_키로 서명 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-260">Ensure that your user-mode binaries are signed with the key  _.\Keys\ \*\*\*-UMCI.pfx_.</span></span> <span data-ttu-id="76d1d-261">드라이버의 경우와 같이 커널 모드 서명의 경우 고유한 서명 키를 지정 하 고 위의 SIPolicy에도 포함 되어 있는지 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-261">For kernel-mode signing, such as for drivers, you’ll need to specify your own signing keys and make sure that they are also included in the SIPolicy above.</span></span>

### <a name="unlocking-encrypted-drives"></a><span data-ttu-id="76d1d-262">암호화 된 드라이브 잠금 해제</span><span class="sxs-lookup"><span data-stu-id="76d1d-262">Unlocking Encrypted Drives</span></span>

<span data-ttu-id="76d1d-263">개발 및 테스트 중에 암호화 된 장치에서 오프 라인으로 콘텐츠를 읽으려고 할 때 (예: SD card for MinnowBoardMax 또는 DragonBoard의 eMMC에서 USB 대량 저장소 모드를 통해) ' diskpart '를 사용 하 여 드라이브 문자를 MainOS 및 데이터 볼륨에 할당할 수 있습니다. MainOS 및 w: 데이터의 경우 v:를 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-263">During development and testing, when attempting to read contents from an encrypted device offline (e.g. SD card for MinnowBoardMax or DragonBoard's eMMC through USB mass storage mode), 'diskpart' may be used to assign a drive letter to MainOS and Data volume (let's assume v: for MainOS and w: for Data).</span></span>
<span data-ttu-id="76d1d-264">볼륨이 잠긴 것으로 표시 되며 수동으로 잠금을 해제 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-264">The volumes will appear locked and need to be manually unlocked.</span></span> <span data-ttu-id="76d1d-265">OEM-DRA 인증서가 설치 되어 있는 모든 컴퓨터에서이 작업을 수행할 수 있습니다 ( [Devicelockdown 샘플](https://github.com/ms-iot/security/tree/master/TurnkeySecurity)에 포함 됨).</span><span class="sxs-lookup"><span data-stu-id="76d1d-265">This can be done on any machine that has the OEM-DRA.pfx certificate installed (included in the [DeviceLockDown sample](https://github.com/ms-iot/security/tree/master/TurnkeySecurity)).</span></span> <span data-ttu-id="76d1d-266">PFX를 설치 하 고 관리 CMD 프롬프트에서 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-266">Install the PFX and then run the following commands from an administrative CMD prompt:</span></span>

* `manage-bde -unlock v: -cert -cf OEM-DRA.cer`
* `manage-bde -unlock w: -cert -cf OEM-DRA.cer`

<span data-ttu-id="76d1d-267">콘텐츠를 오프 라인으로 자주 액세스 해야 하는 경우 다음 명령을 사용 하 여 초기 잠금 해제 후 볼륨에 대해 BitLocker autounlock을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-267">If the contents need to be frequently accessed offline, BitLocker autounlock can be set up for the volumes after the initial unlock using the following commands:</span></span>

* `manage-bde -autounlock v: -enable`
* `manage-bde -autounlock w: -enable`

### <a name="disabling-bitlocker"></a><span data-ttu-id="76d1d-268">BitLocker 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="76d1d-268">Disabling BitLocker</span></span>

<span data-ttu-id="76d1d-269">BitLocker를 일시적으로 사용 하지 않도록 설정 하 고, IoT 장치를 사용 하 여 원격 PowerShell 세션을 초기화 하 고, 다음 명령을 실행 해야 하는 경우에는 `sectask.exe -disable`합니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-269">Should there arise a need to temporarily disable BitLocker, initate a remote PowerShell session with your IoT device and run the following command: `sectask.exe -disable`.</span></span>  

> [!NOTE]
> <span data-ttu-id="76d1d-270">예약 된 암호화 작업이 사용 하지 않도록 설정 된 경우를 제외 하 고 다음 장치 부팅에서 장치 암호화를 다시 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="76d1d-270">Device encryption will be re-enabled on subsequent device boot unless the scheduled encryption task is disabled.</span></span>


