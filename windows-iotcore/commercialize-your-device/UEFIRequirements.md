---
title: UEFI 요구 사항
author: parameshbabu
ms.author: pabab
ms.date: 08/28/2017
ms.topic: article
description: Windows 10 IoT Core OS에 대 한 UEFI 요구 사항을 알아봅니다.
keywords: windows iot, 이미지 만들기, 이미지 사용자 지정, OEM 사용자 지정, UEFI
ms.openlocfilehash: efd8f104d61667b443d48e1722e26789a490196b
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "60170411"
---
# <a name="uefi-requirements"></a><span data-ttu-id="8f90f-104">UEFI 요구 사항</span><span class="sxs-lookup"><span data-stu-id="8f90f-104">UEFI Requirements</span></span>

<span data-ttu-id="8f90f-105">IoT Core의 UEFI 요구 사항은 데스크톱과 같은 다른 windows 버전과 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="8f90f-105">The UEFI requirements for IoT Core are similar to other windows editions like desktop.</span></span> <span data-ttu-id="8f90f-106">자세한 내용은 [windows의 uefi](https://docs.microsoft.com/windows-hardware/drivers/bringup/uefi-in-windows) 를 참조 하 고, [SoC 플랫폼의 windows 버전에 대 한 uefi 요구 사항은](https://docs.microsoft.com/windows-hardware/drivers/bringup/uefi-requirements-that-apply-to-all-windows-platforms)특히 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8f90f-106">See [UEFI in Windows](https://docs.microsoft.com/windows-hardware/drivers/bringup/uefi-in-windows) for details and specifically see [UEFI requirements for Windows editions on SoC platforms](https://docs.microsoft.com/windows-hardware/drivers/bringup/uefi-requirements-that-apply-to-all-windows-platforms).</span></span> 

## <a name="acpi-design"></a><span data-ttu-id="8f90f-107">ACPI 디자인</span><span class="sxs-lookup"><span data-stu-id="8f90f-107">ACPI Design</span></span>

<span data-ttu-id="8f90f-108">IoT Core의 ACPI 요구 사항에 대 한 자세한 내용은 [SoC 플랫폼용 WINDOWS acpi 디자인 가이드](https://docs.microsoft.com/windows-hardware/drivers/bringup/windows-acpi-design-guide-for-soc-platforms) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8f90f-108">See [Windows ACPI design guide for SoC platforms](https://docs.microsoft.com/windows-hardware/drivers/bringup/windows-acpi-design-guide-for-soc-platforms) for the details on the ACPI requirements for IoT Core.</span></span>

## <a name="replacing-windows-boot-logo"></a><span data-ttu-id="8f90f-109">Windows 부팅 로고 바꾸기</span><span class="sxs-lookup"><span data-stu-id="8f90f-109">Replacing Windows Boot Logo</span></span>

<span data-ttu-id="8f90f-110">BIOS 또는 UEFI에 표시 되는 부팅 로고를 교체 하는 방법에는 여러 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f90f-110">There are multiple ways to replace the boot logo that is displayed by the BIOS or UEFI:</span></span>

* <span data-ttu-id="8f90f-111">한 가지 방법은 UEFI를 사용 하도록 설정 하거나,이를 위해 보드 제조업체 공급 업체에 지불 하 고, UEFI 소스 코드를 직접 변경 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="8f90f-111">One way is to license the UEFI, or pay a board manufacturer vendor to do so, and make changes directly to the UEFI source code.</span></span>
* <span data-ttu-id="8f90f-112">또는 UEFI 구현이 서명 된 로드 가능한 UEFI 드라이버를 지 원하는 장치에서 부팅 로고를 대체 하는 드라이버를 작성 하 고 Windows 부팅 프로세스에서 로고를 벗어나면 BGRT 테이블을 bootmgr에 제공 하는 방법을 보여 주는 샘플은 [여기](https://github.com/Microsoft/MS_UEFI/tree/share/MsIoTSamples) 에 있습니다. Windows 로고로 교체 하는 대신 부팅 중에 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8f90f-112">Alternatively, on devices whose UEFI implementation supports signed loadable UEFI drivers there is a sample [here](https://github.com/Microsoft/MS_UEFI/tree/share/MsIoTSamples) that shows how to build a driver that replaces the boot logo and supply a BGRT table to bootmgr so that the Windows boot process leaves your logo in place during boot instead of replacing it with the Windows logo.</span></span>

## <a name="smbios-settings"></a><span data-ttu-id="8f90f-113">SMBIOS 설정</span><span class="sxs-lookup"><span data-stu-id="8f90f-113">SMBIOS settings</span></span>

<span data-ttu-id="8f90f-114">필요한 최소 SMBIOS 설정은 [OEM 라이선스 요구 사항](OEMLicenseRequirements.md)에 설명 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f90f-114">Minimum required SMBIOS settings are described in [OEM License Requirements](OEMLicenseRequirements.md).</span></span>

## <a name="io-bus-access"></a><span data-ttu-id="8f90f-115">I/o 버스 액세스</span><span class="sxs-lookup"><span data-stu-id="8f90f-115">I/O Bus Access</span></span>

<span data-ttu-id="8f90f-116">Windows IoT Core 및 IoT Enterprise를 사용 하면 사용자 응용 프로그램이 시스템 i/o 핀과 상호 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f90f-116">Windows IoT Core and IoT Enterprise allow for user applications to interface with system I/O pins.</span></span> <span data-ttu-id="8f90f-117">이를 사용 하도록 설정 하려면 ASL 테이블에 특정 구성이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f90f-117">To enable this, specific configuration is required in the ASL table.</span></span> <span data-ttu-id="8f90f-118">자세한 내용은 [Windows 10 IoT Core에서 사용자 모드 액세스 사용](https://docs.microsoft.com/windows/uwp/devices-sensors/enable-usermode-access) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8f90f-118">Read [Enable user mode access on Windows 10 IoT Core](https://docs.microsoft.com/windows/uwp/devices-sensors/enable-usermode-access) for more information.</span></span>

## <a name="recovery-trigger"></a><span data-ttu-id="8f90f-119">복구 트리거</span><span class="sxs-lookup"><span data-stu-id="8f90f-119">Recovery Trigger</span></span>

<span data-ttu-id="8f90f-120">[Windows 10 IoT Core 복구 옵션](Recovery.md) 을 검토 하 고 하드웨어 트리거를 복구 모드로 전환 해야 하는 경우 UEFI 앱에서이를 구현 하 고 Windows 부팅 전에 필요한 bootsequence를 설정 하 여 복구를 호출 해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f90f-120">Review [Windows 10 IoT Core Recovery Options](Recovery.md) and if you require hardware trigger to get into recovery mode, you may require to implement this in the UEFI apps and invoke recovery by setting the required bootsequence before windows boots.</span></span>

<span data-ttu-id="8f90f-121">복구 OS로 부팅 하는 데 필요한 bootsequence는 아래에 제공 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f90f-121">The bootsequence required to boot into the recovery OS is given below</span></span>

```
bcdedit /set {bootmgr} bootsequence {a5935ff2-32ba-4617-bf36-5ac314b3f9bf}
```
