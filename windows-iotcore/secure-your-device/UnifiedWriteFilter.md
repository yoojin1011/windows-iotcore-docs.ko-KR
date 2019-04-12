---
title: 통합된 쓰기 필터를 사용 하 여
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 기록 된 데이터에서에서 실제 저장소 미디어를 보호 하기 위해 통합 쓰기 필터를 사용 하는 방법에 알아봅니다.
keywords: windows iot, 통합 쓰기 필터, 보안, 메모리, 저장소 미디어
ms.openlocfilehash: d1d6927fe19b5888ef0393d0b101065096cd9f63
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59515260"
---
# <a name="using-the-unified-write-filter-uwf-on-windows-10-iot-core"></a><span data-ttu-id="8c5fc-104">통합된 쓰기 필터 (UWF)를 사용 하 여 Windows 10 IoT Core</span><span class="sxs-lookup"><span data-stu-id="8c5fc-104">Using the Unified Write Filter (UWF) on Windows 10 IoT Core</span></span>

> [!WARNING]
> <span data-ttu-id="8c5fc-105">동적 디스크는 UWF에 대해 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8c5fc-105">The dynamic disk is not supported for the UWF.</span></span>

<span data-ttu-id="8c5fc-106">쓰기 필터 (UWF (통합)에 기록 된 데이터에서에서 실제 저장소 미디어를 보호 하는 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="8c5fc-106">The Unified Write Filter (UWF) is a feature that protects physical storage media from data writes.</span></span> <span data-ttu-id="8c5fc-107">UWF는 보호 볼륨에 대한 모든 쓰기 시도를 가로채서 가상 오버레이로 리디렉션합니다.</span><span class="sxs-lookup"><span data-stu-id="8c5fc-107">UWF intercepts all write attempts to a protected volume and redirects those write attempts to a virtual overlay.</span></span> <span data-ttu-id="8c5fc-108">따라서 장치의 신뢰성과 안정성을 높이고 플래시 메모리 미디어(예: SSD) 같은 민감한 미디어에서 마모를 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c5fc-108">This improves the reliability and stability of your device and reduces the wear on write-sensitive media, such as flash memory media like solid-state drives.</span></span>

<span data-ttu-id="8c5fc-109">설명서를 읽기를 [통합 쓰기 필터](https://docs.microsoft.com/windows-hardware/customize/enterprise/unified-write-filter) 자세한 내용은 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c5fc-109">Read our documentation on the [Unified Write Filter](https://docs.microsoft.com/windows-hardware/customize/enterprise/unified-write-filter) for more information.</span></span>

## <a name="how-to-install-uwf-on-a-device-running-windows-10-iot-core"></a><span data-ttu-id="8c5fc-110">Windows 10 IoT Core 실행 하는 장치에서 UWF 설치 하는 방법</span><span class="sxs-lookup"><span data-stu-id="8c5fc-110">How to Install UWF on a device running Windows 10 IoT Core</span></span>

* <span data-ttu-id="8c5fc-111">하지 않은 경우 현재 버전의 Windows 10 IoT Core 키트 아직, 다운로드 및 설치 합니다 [Windows 10 IoT Core 패키지](https://www.microsoft.com/en-us/software-download/windows10iotcore)합니다.</span><span class="sxs-lookup"><span data-stu-id="8c5fc-111">If you do not have the current version of the Windows 10 IoT Core Kits yet, download and install the [Windows 10 IoT Core Packages](https://www.microsoft.com/en-us/software-download/windows10iotcore).</span></span>
* <span data-ttu-id="8c5fc-112">UWF 패키지를 복사 하 여 장치 아키텍처에 따라 ( `Microsoft-IoTUAP-UnifiedWriteFilter-Package.cab` 하 고 `Microsoft-IoTUAP-UnifiedWriteFilter-Package_Lang_en-us.cab` ) PC에서 (`C:\Program Files (x86)\Windows Kits\10\MSPackages\Retail\<arch>\fre\`) 장치 (예를 들어 [Windows 파일 공유](../manage-your-device/WindowsFileSharing.md)).</span><span class="sxs-lookup"><span data-stu-id="8c5fc-112">Based on your device architecture, copy UWF packages ( `Microsoft-IoTUAP-UnifiedWriteFilter-Package.cab` and `Microsoft-IoTUAP-UnifiedWriteFilter-Package_Lang_en-us.cab` ) from your PC (`C:\Program Files (x86)\Windows Kits\10\MSPackages\Retail\<arch>\fre\`) to the device (for example, with [Windows file sharing](../manage-your-device/WindowsFileSharing.md)).</span></span>
* <span data-ttu-id="8c5fc-113">시작 [SSH](../connect-your-device/SSH.md) 하거나 [Powershell](../connect-your-device/PowerShell.md) 및 Windows 10 IoT Core 실행 하는 장치에 액세스 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c5fc-113">Launch [SSH](../connect-your-device/SSH.md) or [Powershell](../connect-your-device/PowerShell.md) and access your device running Windows 10 IoT Core.</span></span>
* <span data-ttu-id="8c5fc-114">SSH 또는 Powershell에서 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c5fc-114">From SSH or Powershell, do the following:</span></span>
  * <span data-ttu-id="8c5fc-115">파일을 복사한 디렉터리로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c5fc-115">change to the directory where you have copied your files</span></span>
    * `cd C:\<dir>`
  * <span data-ttu-id="8c5fc-116">IoT 장치 시스템 이미지에 패키지를 설치 하려면 다음이 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c5fc-116">Run these commands to install the packages to your IoT device system image:</span></span>
    * `applyupdate –stage .\Microsoft-IoTUAP-UnifiedWriteFilter-Package.cab`
    * `applyupdate –stage .\Microsoft-IoTUAP-UnifiedWriteFilter-Package_Lang_en-us.cab`
    * `applyupdate –commit`
* <span data-ttu-id="8c5fc-117">장치는 업데이트 OS로 부팅, UWF 기능을 설치 및는 MainOS 하려면 다시 부팅 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c5fc-117">The device will boot to the Update OS, install UWF features, and reboot to the MainOS.</span></span>
* <span data-ttu-id="8c5fc-118">장치는 MainOS 돌아갑니다, 면 UWF 기능은 준비 하 고 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c5fc-118">Once the device comes back to the MainOS, the UWF feature is ready and available to use.</span></span> <span data-ttu-id="8c5fc-119">입력 하 여 확인할 수 있습니다 ```uwfmgr.exe``` Powershell 또는 SSH 창에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c5fc-119">This can be verified by typing ```uwfmgr.exe``` into your Powershell or SSH window.</span></span>

  ![Windows 10 IoT Core uwfmgr.exe](../media/UnifiedWriteFilter/uwfmgr.png)


## <a name="how-to-include-uwf-in-your-custom-ffu"></a><span data-ttu-id="8c5fc-121">UWF Your Custom FFU 포함 하는 방법</span><span class="sxs-lookup"><span data-stu-id="8c5fc-121">How to include UWF in Your Custom FFU</span></span> 

* <span data-ttu-id="8c5fc-122">추가 **IOT_UNIFIED_WRITE_FILTER** OEM 입력 파일에 기능 id</span><span class="sxs-lookup"><span data-stu-id="8c5fc-122">Add **IOT_UNIFIED_WRITE_FILTER** feature id to the OEM Input file</span></span> 
* <span data-ttu-id="8c5fc-123">image\FFU를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8c5fc-123">Create the image\FFU.</span></span> <span data-ttu-id="8c5fc-124">읽기 [기본 이미지를 만드는](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image) 지침에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c5fc-124">Read [Create a basic image](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image) for instructions.</span></span>


## <a name="how-to-use-uwf"></a><span data-ttu-id="8c5fc-125">UWF를 사용 하는 방법</span><span class="sxs-lookup"><span data-stu-id="8c5fc-125">How to Use UWF</span></span>

<span data-ttu-id="8c5fc-126">UWF는 Powershell 또는 SSH 세션을 통해 uwfmgr.exe 도구를 사용 하 여 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c5fc-126">UWF can be configured using the uwfmgr.exe tool via a Powershell or SSH session.</span></span>
<span data-ttu-id="8c5fc-127">읽기 [ `uwfmgr.exe` 도구](https://docs.microsoft.com/windows-hardware/customize/enterprise/uwfmgrexe) IoT Core에서 지원 되지 않는 일부 명령 아래에 나열 된 예외와 함께 사용할 수 있는 옵션에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c5fc-127">Read [`uwfmgr.exe` tool](https://docs.microsoft.com/windows-hardware/customize/enterprise/uwfmgrexe) for the available options with an exception of some commands listed below that are not supported in IoT Core.</span></span>
<span data-ttu-id="8c5fc-128">오버레이 구성의 기본 설정을 검토 하 고 요구 사항에 따라 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c5fc-128">Review the default settings of the Overlay configurations and adapt them per your requirements.</span></span>

<span data-ttu-id="8c5fc-129">UWF 사용 하 여 MDM 채널을 통해 구성할 수도 있습니다 [통합 쓰기 필터 CSP](https://docs.microsoft.com/windows/client-management/mdm/unifiedwritefilter-csp)합니다.</span><span class="sxs-lookup"><span data-stu-id="8c5fc-129">UWF can also be configured via MDM channel using [Unified Write Filter CSP](https://docs.microsoft.com/windows/client-management/mdm/unifiedwritefilter-csp).</span></span>


* <span data-ttu-id="8c5fc-130">명령의 다음 조합 uwfmgr를 사용 하도록 설정 하 고 C 드라이브를 보호 하기 위해 구성 하는 예를 들어,</span><span class="sxs-lookup"><span data-stu-id="8c5fc-130">For example, the following combination of commands enable uwfmgr and configure to protect the C drive</span></span>

  `uwfmgr.exe filter enable`      <span data-ttu-id="8c5fc-131">쓰기 필터를 사용 하도록 설정</span><span class="sxs-lookup"><span data-stu-id="8c5fc-131">Enables the write filter</span></span>
  <br>
  `uwfmgr.exe volume protect c:`  <span data-ttu-id="8c5fc-132">C 볼륨을 보호</span><span class="sxs-lookup"><span data-stu-id="8c5fc-132">Protects the Volume C</span></span>
  <br>
  `shutdown /r /t 0`              <span data-ttu-id="8c5fc-133">쓰기 필터 설정을 적용 하기 위해 장치를 다시 시작</span><span class="sxs-lookup"><span data-stu-id="8c5fc-133">Restarts the device to make the write filter settings effective</span></span>

<span data-ttu-id="8c5fc-134">*다시 부팅* 모든 uwfmgr 설정을 적용 하기 위해 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c5fc-134">*Reboot* is required to make all the uwfmgr settings effective.</span></span> 


## <a name="protecting-a-data-volume"></a><span data-ttu-id="8c5fc-135">데이터 볼륨을 보호</span><span class="sxs-lookup"><span data-stu-id="8c5fc-135">Protecting a Data Volume</span></span>

<span data-ttu-id="8c5fc-136">볼륨 GUID를 사용 하 여 IoT Core에서 데이터 볼륨을 보호할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c5fc-136">Data volume in IoT Core can be protected using the GUID for the volume.</span></span> <span data-ttu-id="8c5fc-137">다음 명령을 통해 사용 가능한 볼륨에 대 한 GUID는 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c5fc-137">The GUID for the available volumes can be found through the following command</span></span>

  `dir /AL`
  <br>
  `uwfmgr.exe volume protect \\?\Volume {GUID}`


  ![Windows 10 IoT Core 볼륨을 보호](../media/UnifiedWriteFilter/uwfmgr_protect.png)

### <a name="recommended-exclusions"></a><span data-ttu-id="8c5fc-139">권장 되는 예외</span><span class="sxs-lookup"><span data-stu-id="8c5fc-139">Recommended Exclusions</span></span>
<span data-ttu-id="8c5fc-140">데이터 볼륨을 보호 하는 경우에 서비스 및 Windows OS 서비스에서 액세스할 수 있는 로깅 폴더에 대 한 예외를 추가 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8c5fc-140">When protecting the data volume, we recommend that you add exceptions for the servicing and logging folders that are accessed by Windows OS Services.</span></span>

```
C:\Data\Users\System\AppData\Local\UpdateStagingRoot
C:\Data\SharedData\DuShared
C:\Data\SystemData\temp
C:\Data\users\defaultaccount\appdata\local\temp
C:\Data\Programdata\softwaredistribution
C:\Data\systemdata\nonetwlogs
```

<span data-ttu-id="8c5fc-141">제외를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c5fc-141">To add the exclusions:</span></span> `uwfmgr.exe file Add-Exclusion <file/folder name>`



## <a name="servicing-uwf-protected-devices"></a><span data-ttu-id="8c5fc-142">장치를 보호 UWF 서비스</span><span class="sxs-lookup"><span data-stu-id="8c5fc-142">Servicing UWF protected devices</span></span>

> [!Note]
> <span data-ttu-id="8c5fc-143">Windows 10 IoT Core 릴리스 1709 버전 16299, 기본 OS 볼륨을 시작 (c:\) UWF로 보호할 수 있고 서비스 *자동으로* 특별 단계 없이 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c5fc-143">Starting Windows 10 IoT Core Release 1709, version 16299, the main OS volume (C:\) can be protected with UWF and serviced *automatically* without any special steps.</span></span>

<span data-ttu-id="8c5fc-144">다음 단계는 보호 된 데이터 볼륨을 사용 하 여 서비스 UWF 보호 장치에 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c5fc-144">The following steps are required to service UWF protected devices with protected data volumes.</span></span>

* `uwfmgr.exe filter disable` <span data-ttu-id="8c5fc-145">UWF를 사용 하지 않도록 설정</span><span class="sxs-lookup"><span data-stu-id="8c5fc-145">Disable UWF</span></span>
* `shutdown /r /t 0` <span data-ttu-id="8c5fc-146">UWF를 사용 하지 않도록 설정 하는 장치를 다시 부팅</span><span class="sxs-lookup"><span data-stu-id="8c5fc-146">Reboot device to disable UWF</span></span>
* <span data-ttu-id="8c5fc-147">(사용 하 여 프로 비전 패키지 또는 MDM 업데이트 정책 설정) 서비스를 사용 하도록 설정</span><span class="sxs-lookup"><span data-stu-id="8c5fc-147">Enable Servicing ( using provisioning package or MDM to set Update policy )</span></span>
   * <span data-ttu-id="8c5fc-148">장치를 서비스 하는 데 자동으로 다시 부팅 하는 업데이트</span><span class="sxs-lookup"><span data-stu-id="8c5fc-148">Note that the device will automatically reboot to perform the servicing updates</span></span>
* `uwfmgr.exe filter enable` <span data-ttu-id="8c5fc-149">UWF를 사용 하도록 설정</span><span class="sxs-lookup"><span data-stu-id="8c5fc-149">Enable UWF</span></span>
* `shutdown /r /t 0` <span data-ttu-id="8c5fc-150">UWF를 사용 하도록 설정 하려면 장치를 다시 부팅</span><span class="sxs-lookup"><span data-stu-id="8c5fc-150">Reboot device to enable UWF</span></span>

## <a name="unsupported-uwfmgrexe-commands"></a><span data-ttu-id="8c5fc-151">지원 되지 않는 uwfmgr.exe 명령</span><span class="sxs-lookup"><span data-stu-id="8c5fc-151">Unsupported uwfmgr.exe Commands</span></span>

<span data-ttu-id="8c5fc-152">**UWF 서비스 모드** IoT Core에서 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8c5fc-152">**UWF Servicing Mode** is not supported in IoT Core.</span></span>

`uwfmgr.exe` <span data-ttu-id="8c5fc-153">Windows 10 IoT Core 아래 나열 된 명령을 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8c5fc-153">on Windows 10 IoT Core does not support commands listed below.</span></span>

```
Filter 
    Shutdown 
    Restart 
Servicing 
    Enable 
    Disable 
    Update-Windows
```
