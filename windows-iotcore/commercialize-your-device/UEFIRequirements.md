---
title: UEFI 요구 사항
author: parameshbabu
ms.author: pabab
ms.date: 08/28/2017
ms.topic: article
description: Windows 10 IoT Core OS에 대 한 UEFI 요구 사항에 알아봅니다.
keywords: windows iot, 이미지를 생성, 이미지 사용자 지정, UEFI OEM 사용자 지정
ms.openlocfilehash: efd8f104d61667b443d48e1722e26789a490196b
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512286"
---
# <a name="uefi-requirements"></a><span data-ttu-id="4273b-104">UEFI 요구 사항</span><span class="sxs-lookup"><span data-stu-id="4273b-104">UEFI Requirements</span></span>

<span data-ttu-id="4273b-105">IoT Core에 대 한 UEFI 요구 사항 데스크톱 등 다른 windows 버전와 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="4273b-105">The UEFI requirements for IoT Core are similar to other windows editions like desktop.</span></span> <span data-ttu-id="4273b-106">참조 [Windows의 UEFI](https://docs.microsoft.com/windows-hardware/drivers/bringup/uefi-in-windows) 세부 정보 및 특히 참조 [SoC 플랫폼에서 Windows 버전에 대 한 UEFI 요구 사항](https://docs.microsoft.com/windows-hardware/drivers/bringup/uefi-requirements-that-apply-to-all-windows-platforms)합니다.</span><span class="sxs-lookup"><span data-stu-id="4273b-106">See [UEFI in Windows](https://docs.microsoft.com/windows-hardware/drivers/bringup/uefi-in-windows) for details and specifically see [UEFI requirements for Windows editions on SoC platforms](https://docs.microsoft.com/windows-hardware/drivers/bringup/uefi-requirements-that-apply-to-all-windows-platforms).</span></span> 

## <a name="acpi-design"></a><span data-ttu-id="4273b-107">ACPI 디자인</span><span class="sxs-lookup"><span data-stu-id="4273b-107">ACPI Design</span></span>

<span data-ttu-id="4273b-108">참조 [SoC 플랫폼용 Windows ACPI 디자인 가이드](https://docs.microsoft.com/windows-hardware/drivers/bringup/windows-acpi-design-guide-for-soc-platforms) IoT Core의 ACPI 요구 사항에 세부 정보에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="4273b-108">See [Windows ACPI design guide for SoC platforms](https://docs.microsoft.com/windows-hardware/drivers/bringup/windows-acpi-design-guide-for-soc-platforms) for the details on the ACPI requirements for IoT Core.</span></span>

## <a name="replacing-windows-boot-logo"></a><span data-ttu-id="4273b-109">대체 Windows 부팅 로고</span><span class="sxs-lookup"><span data-stu-id="4273b-109">Replacing Windows Boot Logo</span></span>

<span data-ttu-id="4273b-110">여러 가지 방법으로 BIOS 또는 UEFI에서 표시 되는 부팅 로고를 교체할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4273b-110">There are multiple ways to replace the boot logo that is displayed by the BIOS or UEFI:</span></span>

* <span data-ttu-id="4273b-111">하나의 방법은 UEFI, 라이선스 또는 지불이 위해 보드 제조업체 공급 업체 및 UEFI 소스 코드를 직접 변경 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="4273b-111">One way is to license the UEFI, or pay a board manufacturer vendor to do so, and make changes directly to the UEFI source code.</span></span>
* <span data-ttu-id="4273b-112">또는 UEFI 구현이 로드 가능한 UEFI 드라이버 서명 된 지원 되는 장치에 있는 샘플은 [여기](https://github.com/Microsoft/MS_UEFI/tree/share/MsIoTSamples) 부팅 로고를 대체 하는 드라이버는 Windows 부팅 되도록 bootmgr BGRT 테이블을 제공 하는 방법을 보여 주는 프로세스는 Windows 로고를 사용 하 여 대체 하지 않고 부팅 하는 동안 위치에 로고를 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="4273b-112">Alternatively, on devices whose UEFI implementation supports signed loadable UEFI drivers there is a sample [here](https://github.com/Microsoft/MS_UEFI/tree/share/MsIoTSamples) that shows how to build a driver that replaces the boot logo and supply a BGRT table to bootmgr so that the Windows boot process leaves your logo in place during boot instead of replacing it with the Windows logo.</span></span>

## <a name="smbios-settings"></a><span data-ttu-id="4273b-113">SMBIOS 설정</span><span class="sxs-lookup"><span data-stu-id="4273b-113">SMBIOS settings</span></span>

<span data-ttu-id="4273b-114">SMBIOS 설정에 설명 되어 최소한 [OEM 라이선스 요구 사항](OEMLicenseRequirements.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="4273b-114">Minimum required SMBIOS settings are described in [OEM License Requirements](OEMLicenseRequirements.md).</span></span>

## <a name="io-bus-access"></a><span data-ttu-id="4273b-115">I/O 버스 액세스</span><span class="sxs-lookup"><span data-stu-id="4273b-115">I/O Bus Access</span></span>

<span data-ttu-id="4273b-116">Windows IoT Core 및 IoT Enterprise 시스템 I/O pin 사용 하 여 인터페이스를 사용자 응용 프로그램 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="4273b-116">Windows IoT Core and IoT Enterprise allow for user applications to interface with system I/O pins.</span></span> <span data-ttu-id="4273b-117">이 작업이 가능 하도록 ASL 테이블의 특정 구성이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="4273b-117">To enable this, specific configuration is required in the ASL table.</span></span> <span data-ttu-id="4273b-118">읽기 [Windows 10 IoT Core 대 한 사용자 모드 액세스를 사용 하도록 설정](https://docs.microsoft.com/windows/uwp/devices-sensors/enable-usermode-access) 자세한 내용은 합니다.</span><span class="sxs-lookup"><span data-stu-id="4273b-118">Read [Enable user mode access on Windows 10 IoT Core](https://docs.microsoft.com/windows/uwp/devices-sensors/enable-usermode-access) for more information.</span></span>

## <a name="recovery-trigger"></a><span data-ttu-id="4273b-119">복구 트리거</span><span class="sxs-lookup"><span data-stu-id="4273b-119">Recovery Trigger</span></span>

<span data-ttu-id="4273b-120">검토 [Windows 10 IoT Core 복구 옵션](Recovery.md) 하드웨어 복구 모드에는 트리거를 필요로 하는 경우 UEFI 앱에서이 구현 하 고 windows 부팅 하기 전에 필요한 bootsequence를 설정 하 여 복구를 호출 하 필요할 수 있습니다 .</span><span class="sxs-lookup"><span data-stu-id="4273b-120">Review [Windows 10 IoT Core Recovery Options](Recovery.md) and if you require hardware trigger to get into recovery mode, you may require to implement this in the UEFI apps and invoke recovery by setting the required bootsequence before windows boots.</span></span>

<span data-ttu-id="4273b-121">복구 OS로 부팅 하는 데 필요한 bootsequence 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4273b-121">The bootsequence required to boot into the recovery OS is given below</span></span>

```
bcdedit /set {bootmgr} bootsequence {a5935ff2-32ba-4617-bf36-5ac314b3f9bf}
```