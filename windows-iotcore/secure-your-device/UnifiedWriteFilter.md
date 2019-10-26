---
title: 통합 쓰기 필터 사용
ms.date: 08/28/2017
ms.topic: article
description: 통합 쓰기 필터를 사용 하 여 데이터 쓰기에서 실제 저장소 미디어를 보호 하는 방법에 대해 알아봅니다.
keywords: windows iot, 통합 쓰기 필터, 보안, 메모리, 저장소 미디어
ms.openlocfilehash: 7c8632cf12d391d458861ef22e2c3a9fc77a3a08
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918675"
---
# <a name="using-the-unified-write-filter-uwf-on-windows-10-iot-core"></a><span data-ttu-id="e1a86-104">Windows 10 IoT Core에서 UWF (통합 쓰기 필터) 사용</span><span class="sxs-lookup"><span data-stu-id="e1a86-104">Using the Unified Write Filter (UWF) on Windows 10 IoT Core</span></span>

> [!WARNING]
> <span data-ttu-id="e1a86-105">UWF에는 동적 디스크가 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e1a86-105">The dynamic disk is not supported for the UWF.</span></span>

<span data-ttu-id="e1a86-106">UWF (통합 쓰기 필터)는 데이터 쓰기에서 실제 저장소 미디어를 보호 하는 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="e1a86-106">The Unified Write Filter (UWF) is a feature that protects physical storage media from data writes.</span></span> <span data-ttu-id="e1a86-107">UWF는 보호 볼륨에 대한 모든 쓰기 시도를 가로채서 가상 오버레이로 리디렉션합니다.</span><span class="sxs-lookup"><span data-stu-id="e1a86-107">UWF intercepts all write attempts to a protected volume and redirects those write attempts to a virtual overlay.</span></span> <span data-ttu-id="e1a86-108">따라서 장치의 신뢰성과 안정성을 높이고 플래시 메모리 미디어(예: SSD) 같은 민감한 미디어에서 마모를 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1a86-108">This improves the reliability and stability of your device and reduces the wear on write-sensitive media, such as flash memory media like solid-state drives.</span></span>

<span data-ttu-id="e1a86-109">자세한 내용은 [통합 쓰기 필터](https://docs.microsoft.com/windows-hardware/customize/enterprise/unified-write-filter) 에 대 한 설명서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e1a86-109">Read our documentation on the [Unified Write Filter](https://docs.microsoft.com/windows-hardware/customize/enterprise/unified-write-filter) for more information.</span></span>

## <a name="how-to-install-uwf-on-a-device-running-windows-10-iot-core"></a><span data-ttu-id="e1a86-110">Windows 10 IoT Core를 실행 하는 장치에 UWF를 설치 하는 방법</span><span class="sxs-lookup"><span data-stu-id="e1a86-110">How to Install UWF on a device running Windows 10 IoT Core</span></span>

* <span data-ttu-id="e1a86-111">최신 버전의 Windows 10 IoT Core 키트가 아직 없는 경우 [windows 10 Iot Core 패키지](https://www.microsoft.com/en-us/software-download/windows10iotcore)를 다운로드 하 여 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1a86-111">If you do not have the current version of the Windows 10 IoT Core Kits yet, download and install the [Windows 10 IoT Core Packages](https://www.microsoft.com/en-us/software-download/windows10iotcore).</span></span>
* <span data-ttu-id="e1a86-112">장치 아키텍처에 따라 PC (`C:\Program Files (x86)\Windows Kits\10\MSPackages\Retail\<arch>\fre\`)에서 장치 (예: [Windows 파일 공유](../manage-your-device/WindowsFileSharing.md))로 UWF 패키지 (`Microsoft-IoTUAP-UnifiedWriteFilter-Package.cab` 및 `Microsoft-IoTUAP-UnifiedWriteFilter-Package_Lang_en-us.cab`)를 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1a86-112">Based on your device architecture, copy UWF packages ( `Microsoft-IoTUAP-UnifiedWriteFilter-Package.cab` and `Microsoft-IoTUAP-UnifiedWriteFilter-Package_Lang_en-us.cab` ) from your PC (`C:\Program Files (x86)\Windows Kits\10\MSPackages\Retail\<arch>\fre\`) to the device (for example, with [Windows file sharing](../manage-your-device/WindowsFileSharing.md)).</span></span>
* <span data-ttu-id="e1a86-113">[SSH](../connect-your-device/SSH.md) 또는 [Powershell](../connect-your-device/PowerShell.md) 을 시작 하 고 Windows 10 IoT Core를 실행 하는 장치에 액세스 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1a86-113">Launch [SSH](../connect-your-device/SSH.md) or [Powershell](../connect-your-device/PowerShell.md) and access your device running Windows 10 IoT Core.</span></span>
* <span data-ttu-id="e1a86-114">SSH 또는 Powershell에서 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1a86-114">From SSH or Powershell, do the following:</span></span>
  * <span data-ttu-id="e1a86-115">파일을 복사한 디렉터리로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1a86-115">change to the directory where you have copied your files</span></span>
    * `cd C:\<dir>`
  * <span data-ttu-id="e1a86-116">다음 명령을 실행 하 여 IoT 장치 시스템 이미지에 패키지를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1a86-116">Run these commands to install the packages to your IoT device system image:</span></span>
    * `applyupdate –stage .\Microsoft-IoTUAP-UnifiedWriteFilter-Package.cab`
    * `applyupdate –stage .\Microsoft-IoTUAP-UnifiedWriteFilter-Package_Lang_en-us.cab`
    * `applyupdate –commit`
* <span data-ttu-id="e1a86-117">장치가 업데이트 OS로 부팅 되 고, UWF 기능을 설치 하 고, MainOS로 다시 부팅 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1a86-117">The device will boot to the Update OS, install UWF features, and reboot to the MainOS.</span></span>
* <span data-ttu-id="e1a86-118">장치가 MainOS로 돌아오면 UWF 기능이 준비 되어 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1a86-118">Once the device comes back to the MainOS, the UWF feature is ready and available to use.</span></span> <span data-ttu-id="e1a86-119">Powershell 또는 SSH 창에 ```uwfmgr.exe```를 입력 하 여이를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1a86-119">This can be verified by typing ```uwfmgr.exe``` into your Powershell or SSH window.</span></span>

  ![Windows 10 IoT Core의 uwfmgr](../media/UnifiedWriteFilter/uwfmgr.png)


## <a name="how-to-include-uwf-in-your-custom-ffu"></a><span data-ttu-id="e1a86-121">사용자 지정 FFU에 UWF를 포함 하는 방법</span><span class="sxs-lookup"><span data-stu-id="e1a86-121">How to include UWF in Your Custom FFU</span></span> 

* <span data-ttu-id="e1a86-122">OEM 입력 파일에 **IOT_UNIFIED_WRITE_FILTER** 기능 id 추가</span><span class="sxs-lookup"><span data-stu-id="e1a86-122">Add **IOT_UNIFIED_WRITE_FILTER** feature id to the OEM Input file</span></span> 
* <span data-ttu-id="e1a86-123">Image\FFU.를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e1a86-123">Create the image\FFU.</span></span> <span data-ttu-id="e1a86-124">지침은 [기본 이미지 만들기](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e1a86-124">Read [Create a basic image](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image) for instructions.</span></span>


## <a name="how-to-use-uwf"></a><span data-ttu-id="e1a86-125">UWF를 사용 하는 방법</span><span class="sxs-lookup"><span data-stu-id="e1a86-125">How to Use UWF</span></span>

<span data-ttu-id="e1a86-126">UWF는 Powershell 또는 SSH 세션을 통해 uwfmgr 도구를 사용 하 여 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1a86-126">UWF can be configured using the uwfmgr.exe tool via a Powershell or SSH session.</span></span>
<span data-ttu-id="e1a86-127">IoT Core에서 지원 되지 않는 아래 나열 된 일부 명령을 제외 하 고 사용 가능한 옵션에 대 한 [`uwfmgr.exe` 도구](https://docs.microsoft.com/windows-hardware/customize/enterprise/uwfmgrexe) 를 읽으십시오.</span><span class="sxs-lookup"><span data-stu-id="e1a86-127">Read [`uwfmgr.exe` tool](https://docs.microsoft.com/windows-hardware/customize/enterprise/uwfmgrexe) for the available options with an exception of some commands listed below that are not supported in IoT Core.</span></span>
<span data-ttu-id="e1a86-128">오버레이 구성의 기본 설정을 검토 하 고 요구 사항에 따라 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1a86-128">Review the default settings of the Overlay configurations and adapt them per your requirements.</span></span>

<span data-ttu-id="e1a86-129">[통합 쓰기 필터 CSP](https://docs.microsoft.com/windows/client-management/mdm/unifiedwritefilter-csp)를 사용 하 여 MDM 채널을 통해 UWF를 구성할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1a86-129">UWF can also be configured via MDM channel using [Unified Write Filter CSP](https://docs.microsoft.com/windows/client-management/mdm/unifiedwritefilter-csp).</span></span>


* <span data-ttu-id="e1a86-130">예를 들어 다음 명령 조합을 사용 하 여 C 드라이브를 보호 하도록 uwfmgr 및를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1a86-130">For example, the following combination of commands enable uwfmgr and configure to protect the C drive</span></span>

  <span data-ttu-id="e1a86-131">쓰기 필터를 사용 하도록 설정 `uwfmgr.exe filter enable`</span><span class="sxs-lookup"><span data-stu-id="e1a86-131">`uwfmgr.exe filter enable`      Enables the write filter</span></span>
  <br>
  <span data-ttu-id="e1a86-132">볼륨 C를 보호 하는 `uwfmgr.exe volume protect c:`</span><span class="sxs-lookup"><span data-stu-id="e1a86-132">`uwfmgr.exe volume protect c:`  Protects the Volume C</span></span>
  <br>
  <span data-ttu-id="e1a86-133">`shutdown /r /t 0`는 장치를 다시 시작 하 여 쓰기 필터 설정을 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1a86-133">`shutdown /r /t 0`              Restarts the device to make the write filter settings effective</span></span>

<span data-ttu-id="e1a86-134">모든 uwfmgr 설정을 적용 하려면 *다시 부팅* 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1a86-134">*Reboot* is required to make all the uwfmgr settings effective.</span></span> 


## <a name="protecting-a-data-volume"></a><span data-ttu-id="e1a86-135">데이터 볼륨 보호</span><span class="sxs-lookup"><span data-stu-id="e1a86-135">Protecting a Data Volume</span></span>

<span data-ttu-id="e1a86-136">IoT Core의 데이터 볼륨은 볼륨의 GUID를 사용 하 여 보호할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1a86-136">Data volume in IoT Core can be protected using the GUID for the volume.</span></span> <span data-ttu-id="e1a86-137">사용 가능한 볼륨의 GUID는 다음 명령을 통해 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1a86-137">The GUID for the available volumes can be found through the following command</span></span>

  `dir /AL`
  <br>
  `uwfmgr.exe volume protect \\?\Volume {GUID}`


  ![Windows 10 IoT Core에서 볼륨 보호](../media/UnifiedWriteFilter/uwfmgr_protect.png)

### <a name="recommended-exclusions"></a><span data-ttu-id="e1a86-139">권장 제외</span><span class="sxs-lookup"><span data-stu-id="e1a86-139">Recommended Exclusions</span></span>
<span data-ttu-id="e1a86-140">데이터 볼륨을 보호 하는 경우 Windows OS 서비스에서 액세스 하는 서비스 및 로깅 폴더에 대 한 예외를 추가 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="e1a86-140">When protecting the data volume, we recommend that you add exceptions for the servicing and logging folders that are accessed by Windows OS Services.</span></span>

```
C:\Data\Users\System\AppData\Local\UpdateStagingRoot
C:\Data\SharedData\DuShared
C:\Data\SystemData\temp
C:\Data\users\defaultaccount\appdata\local\temp
C:\Data\Programdata\softwaredistribution
C:\Data\systemdata\nonetwlogs
```

<span data-ttu-id="e1a86-141">제외를 추가 하려면: `uwfmgr.exe file Add-Exclusion <file/folder name>`</span><span class="sxs-lookup"><span data-stu-id="e1a86-141">To add the exclusions: `uwfmgr.exe file Add-Exclusion <file/folder name>`</span></span>



## <a name="servicing-uwf-protected-devices"></a><span data-ttu-id="e1a86-142">UWF로 보호 된 장치 서비스</span><span class="sxs-lookup"><span data-stu-id="e1a86-142">Servicing UWF protected devices</span></span>

> [!Note]
> <span data-ttu-id="e1a86-143">Windows 10 IoT Core 릴리스 1709, 버전 16299부터 주 OS 볼륨 (C:\)은 UWF로 보호할 수 있으며 특별 한 단계 없이 *자동으로* 서비스 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e1a86-143">Starting Windows 10 IoT Core Release 1709, version 16299, the main OS volume (C:\) can be protected with UWF and serviced *automatically* without any special steps.</span></span>

<span data-ttu-id="e1a86-144">보호 된 데이터 볼륨을 사용 하 여 UWF로 보호 된 장치를 서비스 하려면 다음 단계가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1a86-144">The following steps are required to service UWF protected devices with protected data volumes.</span></span>

* <span data-ttu-id="e1a86-145">UWF를 사용 하지 않도록 설정 `uwfmgr.exe filter disable`</span><span class="sxs-lookup"><span data-stu-id="e1a86-145">`uwfmgr.exe filter disable` Disable UWF</span></span>
* <span data-ttu-id="e1a86-146">UWF를 사용 하지 않도록 장치를 다시 부팅 `shutdown /r /t 0`</span><span class="sxs-lookup"><span data-stu-id="e1a86-146">`shutdown /r /t 0` Reboot device to disable UWF</span></span>
* <span data-ttu-id="e1a86-147">서비스를 사용 하도록 설정 (프로 비전 패키지 또는 MDM을 사용 하 여 업데이트 정책 설정)</span><span class="sxs-lookup"><span data-stu-id="e1a86-147">Enable Servicing ( using provisioning package or MDM to set Update policy )</span></span>
   * <span data-ttu-id="e1a86-148">서비스 업데이트를 수행 하기 위해 장치가 자동으로 다시 부팅 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e1a86-148">Note that the device will automatically reboot to perform the servicing updates</span></span>
* <span data-ttu-id="e1a86-149">UWF를 사용 하도록 설정 `uwfmgr.exe filter enable`</span><span class="sxs-lookup"><span data-stu-id="e1a86-149">`uwfmgr.exe filter enable` Enable UWF</span></span>
* <span data-ttu-id="e1a86-150">UWF를 사용 하도록 장치를 다시 부팅 `shutdown /r /t 0`</span><span class="sxs-lookup"><span data-stu-id="e1a86-150">`shutdown /r /t 0` Reboot device to enable UWF</span></span>

## <a name="unsupported-uwfmgrexe-commands"></a><span data-ttu-id="e1a86-151">지원 되지 않는 uwfmgr 명령</span><span class="sxs-lookup"><span data-stu-id="e1a86-151">Unsupported uwfmgr.exe Commands</span></span>

<span data-ttu-id="e1a86-152">**UWF 서비스 모드** 는 IoT Core에서 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e1a86-152">**UWF Servicing Mode** is not supported in IoT Core.</span></span>

<span data-ttu-id="e1a86-153">Windows 10 IoT Core의 `uwfmgr.exe`는 아래 나열 된 명령을 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e1a86-153">`uwfmgr.exe` on Windows 10 IoT Core does not support commands listed below.</span></span>

```
Filter 
    Shutdown 
    Restart 
Servicing 
    Enable 
    Disable 
    Update-Windows
```
