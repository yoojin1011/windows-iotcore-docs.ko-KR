---
title: Windows 10 IoT Core 명령줄 유틸리티
author: bfjelds
ms.author: bfjelds
ms.date: 08/28/2017
ms.topic: article
description: 장치에 연결한 후 PowreShell 사용 하려면 명령줄 유틸리티에 알아봅니다.
keywords: windows iot, 명령줄, PowerShell, 명령줄 유틸리티
ms.openlocfilehash: 2fb009115dc929540c30d5403c1877051f6b7037
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513341"
---
# <a name="windows-10-iot-core-command-line-utils"></a><span data-ttu-id="71a7a-104">Windows 10 IoT Core 명령줄 유틸리티</span><span class="sxs-lookup"><span data-stu-id="71a7a-104">Windows 10 IoT Core Command Line Utils</span></span>

<span data-ttu-id="71a7a-105">장치에서 일부 설정이 구성 하려고 하나요?</span><span class="sxs-lookup"><span data-stu-id="71a7a-105">Looking to configure some of the settings on your device?</span></span> <span data-ttu-id="71a7a-106">도구 아래에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-106">The below tools are available at your disposal.</span></span> <span data-ttu-id="71a7a-107">PowerShell을 사용 하 여 후 다음이 명령을 실행 하려면 [장치로 연결](../connect-your-device/PowerShell.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-107">Use PowerShell to run these commands after [connecting to your device](../connect-your-device/PowerShell.md).</span></span>

> [!NOTE]
> <span data-ttu-id="71a7a-108">이러한 도구 미리 로드 되지 않은-이미지에서 이러한 도구를 다운로드 하려면 해당 기능 Id를 포함 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-108">These tools are not pre-loaded - you will need to include appropriate feature IDs to get these tools in the image.</span></span>

## <a name="iot-core-specific-command-line-utils"></a><span data-ttu-id="71a7a-109">IoT Core-관련 명령줄 유틸리티</span><span class="sxs-lookup"><span data-stu-id="71a7a-109">IoT Core-specific Command Line Utils</span></span>

### **<a name="setting-startup-app"></a><span data-ttu-id="71a7a-110">앱을 시작 하는 설정:</span><span class="sxs-lookup"><span data-stu-id="71a7a-110">Setting startup app:</span></span>**
<span data-ttu-id="71a7a-111">시작 편집기를 사용 하 여 Windows IoT Core 장치에서 시작 앱을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-111">Use the startup editor to configure startup apps on your Windows IoT Core device.</span></span> <span data-ttu-id="71a7a-112">실행 `IotStartup` 다음 옵션 중 하나를 사용 하 여:</span><span class="sxs-lookup"><span data-stu-id="71a7a-112">Run `IotStartup` with any of the following options:</span></span>

* `IotStartup list` <span data-ttu-id="71a7a-113">설치 된 응용 프로그램 나열</span><span class="sxs-lookup"><span data-stu-id="71a7a-113">lists installed applications</span></span>
* `IotStartup list headed` <span data-ttu-id="71a7a-114">설치 된 목록으로 응용 프로그램</span><span class="sxs-lookup"><span data-stu-id="71a7a-114">lists installed headed applications</span></span>
* `IotStartup list headless` <span data-ttu-id="71a7a-115">설치 된 헤드리스 응용 프로그램 나열</span><span class="sxs-lookup"><span data-stu-id="71a7a-115">lists installed headless applications</span></span>
* `IotStartup list [MyApp]` <span data-ttu-id="71a7a-116">설치 된 패턴과 일치 하는 응용 프로그램 나열</span><span class="sxs-lookup"><span data-stu-id="71a7a-116">list installed applications that match pattern</span></span> `MyApp`
* `IotStartup add` <span data-ttu-id="71a7a-117">헤드 및 헤드리스 응용 프로그램 추가</span><span class="sxs-lookup"><span data-stu-id="71a7a-117">adds headed and headless applications</span></span>
* `IotStartup add headed [MyApp]` <span data-ttu-id="71a7a-118">패턴과 일치 하는 헤드 응용 프로그램이 추가 `MyApp`합니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-118">adds headed applications that match pattern `MyApp`.</span></span>  <span data-ttu-id="71a7a-119">패턴에는 하나의 응용 프로그램을 일치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-119">Pattern must match only one application.</span></span>
* `IotStartup add headless [Task1]` <span data-ttu-id="71a7a-120">패턴과 일치 하는 헤드리스 응용 프로그램 추가</span><span class="sxs-lookup"><span data-stu-id="71a7a-120">adds headless applications that match pattern</span></span> `Task1`
* `IotStartup remove` <span data-ttu-id="71a7a-121">제거를 지 향하는 방향 및 헤드리스 응용 프로그램</span><span class="sxs-lookup"><span data-stu-id="71a7a-121">removes headed and headless applications</span></span>
* `IotStartup remove headed [MyApp]` <span data-ttu-id="71a7a-122">패턴과 일치 하는 응용 프로그램을 지 향하는 방향 제거</span><span class="sxs-lookup"><span data-stu-id="71a7a-122">removes headed applications that match pattern</span></span> `MyApp`
* `IotStartup remove headless [Task1]` <span data-ttu-id="71a7a-123">패턴과 일치 하는 헤드리스 응용 프로그램 제거</span><span class="sxs-lookup"><span data-stu-id="71a7a-123">removes headless applications that match pattern</span></span> `Task1`
* `IotStartup startup` <span data-ttu-id="71a7a-124">시작에 대 한 양방향 목록과 헤드리스 응용 프로그램 등록</span><span class="sxs-lookup"><span data-stu-id="71a7a-124">lists headed and headless applications registered for startup</span></span>
* `IotStartup startup [MyApp]` <span data-ttu-id="71a7a-125">양방향 목록과 헤드리스 응용 프로그램 등록 시작에 대 한 일치 패턴</span><span class="sxs-lookup"><span data-stu-id="71a7a-125">lists headed and headless applications registered for startup that match pattern</span></span> `MyApp`
* `IotStartup startup headed [MyApp]` <span data-ttu-id="71a7a-126">목록으로 일치 하는 응용 프로그램 시작에 대 한 등록</span><span class="sxs-lookup"><span data-stu-id="71a7a-126">lists headed applications registered for startup that match</span></span> `MyApp`
* `IotStartup startup headless [Task1]` <span data-ttu-id="71a7a-127">헤드리스 시작에 대 한 등록 하는 응용 프로그램 일치를 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-127">lists headless applications registered for startup that match</span></span> `Task1`

    * <span data-ttu-id="71a7a-128">추가 도움말을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="71a7a-128">For further help, try</span></span> `IotStartup help`
    
### **<a name="change-settings-for-region-and-user-or-speech-language"></a><span data-ttu-id="71a7a-129">지역 및 사용자 또는 음성 언어에 대 한 설정을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-129">Change settings for region and user or speech language:</span></span>**

<span data-ttu-id="71a7a-130">`IoTSettings` 도구 영역, 사용자 언어 또는 음성 언어를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-130">The `IoTSettings` tool changes region, user language or speech language.</span></span> <span data-ttu-id="71a7a-131">ProcessLauncher API를 사용 하 여 응용 프로그램에서 호출할 수 있는 명령줄 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-131">This is a command line tool that can be invoked from an application using the ProcessLauncher API.</span></span> <span data-ttu-id="71a7a-132">이 명령은 관리자 계정이 아닌 기본 계정으로 실행 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-132">These commands must be run as default account, not administrator.</span></span>

* `IotSettings del account {all | username}` <span data-ttu-id="71a7a-133">시스템에서 모든 MSA 또는 AAD 계정 또는 특정 계정을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-133">deletes all MSA or AAD accounts on the system or a specific account.</span></span>  <span data-ttu-id="71a7a-134">특정 계정 형태 username@provider.com</span><span class="sxs-lookup"><span data-stu-id="71a7a-134">Specific accounts take the form username@provider.com</span></span>
* `IotSettings del diagnostics` <span data-ttu-id="71a7a-135">현재 장치를 위해 클라우드의 진단 정보를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-135">deletes diagnostic information in the cloud for the current device.</span></span>  <span data-ttu-id="71a7a-136">이 호출 시점까지 기록 제거 note 합니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-136">Note that this removes the history up to the time of invocation.</span></span>  <span data-ttu-id="71a7a-137">새 진단 정보를 기록 하려면 계속 됩니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-137">New diagnostics information will continue to be logged.</span></span>
* `IotSettings list account` <span data-ttu-id="71a7a-138">장치에 서명 된 모든 MSA 또는 AAD 계정을 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-138">lists all MSA or AAD accounts that have been signed into the device.</span></span>
* `IotSettings list uilanguage` <span data-ttu-id="71a7a-139">모든 UI 언어를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-139">lists all UI languages</span></span>
* `IotSettings list speechlanguage` <span data-ttu-id="71a7a-140">모든 음성 언어를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-140">lists all speech languages</span></span>
* `IotSettings get uilanguage` <span data-ttu-id="71a7a-141">현재 UI 언어를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-141">displays current UI language</span></span>
* `IotSettings get speechlanguage` <span data-ttu-id="71a7a-142">현재 음성 언어를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-142">displays current speech language</span></span>
* `IotSettings get region` <span data-ttu-id="71a7a-143">현재 영역을 표시</span><span class="sxs-lookup"><span data-stu-id="71a7a-143">displays current region</span></span>
* `IotSettings set uilanguage language\_tag - (e.g. fr-CA)` <span data-ttu-id="71a7a-144">기본 UI 언어가 프랑스어 (캐나다) 설정)</span><span class="sxs-lookup"><span data-stu-id="71a7a-144">sets default UI language French Canadian)</span></span>
* `IotSettings set speechlanguage language\_tag - (e.g. fr-CA)` <span data-ttu-id="71a7a-145">음성 언어 프랑스어 (캐나다) 설정)</span><span class="sxs-lookup"><span data-stu-id="71a7a-145">sets speech language French Canadian)</span></span>
* `IotSettings set region region\_code - (e.g. CA)` <span data-ttu-id="71a7a-146">캐나다 기본 지역 설정)</span><span class="sxs-lookup"><span data-stu-id="71a7a-146">sets default region to Canada)</span></span>
* `IotSettings set bluetoothpref {sink | source}` <span data-ttu-id="71a7a-147">장치 IOT_BLUETOOTH_A2DP_SOURCE와 IOT_BLUETOOTH_A2DP_SINK 기능을 사용 하 여 빌드한도 역할을 모두 지 원하는 다른 장치에 연결할 때 선택 된 Bluetooth 역할 기본 설정을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-147">Specifies the Bluetooth role preference to select when devices built with both IOT_BLUETOOTH_A2DP_SOURCE and IOT_BLUETOOTH_A2DP_SINK features connect to another device that also supports both roles.</span></span>
* `IotSettings get bluetoothpref` <span data-ttu-id="71a7a-148">IOT_BLUETOOTH_A2DP_SOURCE와 IOT_BLUETOOTH_A2DP_SINK를 사용 하 여 작성 하는 장치에 대 한 현재 Bluetooth 역할 선호도 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-148">returns the current Bluetooth role preference for devices built with both IOT_BLUETOOTH_A2DP_SOURCE and IOT_BLUETOOTH_A2DP_SINK.</span></span>  <span data-ttu-id="71a7a-149">기본값은 원본입니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-149">The default is source.</span></span>

> [!TIP]
> `IoTSettings -list uiLanguage` <span data-ttu-id="71a7a-150">에 제공 됩니다 다시 지원 되는 UI 언어 목록 (Windows IoT core 이미지에 대해 실행 된 버전)</span><span class="sxs-lookup"><span data-stu-id="71a7a-150">will give back the list of supported UI language (in the version of Windows IoT core image it has been executed against)</span></span>
    
### **<a name="change-default-audio-device-and-volume"></a><span data-ttu-id="71a7a-151">기본 오디오 장치 및 볼륨을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-151">Change default audio device and volume:</span></span>**

<span data-ttu-id="71a7a-152">`IoTCoreAudioControlTool` 캡처 및 재생 장치 기본 설정 및 볼륨을 변경 하는 등의 오디오 관련된 옵션을 제어 하는 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-152">The `IoTCoreAudioControlTool` tool controls audio related options, such as setting default capture and playback devices and changing the volume.</span></span> <span data-ttu-id="71a7a-153">매개 변수의 전체 목록을 실행 `IoTCoreAudioControlTool h`합니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-153">For a full list of parameters, run `IoTCoreAudioControlTool h`.</span></span>

### **<a name="manually-installing-appx-files"></a><span data-ttu-id="71a7a-154">수동으로 설치 합니다. APPX 파일:</span><span class="sxs-lookup"><span data-stu-id="71a7a-154">Manually installing .APPX files:</span></span>**
<span data-ttu-id="71a7a-155">DeployAppx 설치 및 제거에 사용 하도록 설정 합니다. 개발 시나리오에서 APPX 패키지입니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-155">DeployAppx enables installing, and removing in .APPX packages in development scenarios.</span></span>  <span data-ttu-id="71a7a-156">설치에 대 한 올바른 메서드입니다. APPX 패키지의 프로덕션 이미지에 설명 된 대로 프로 비전 패키지를 사용 하는 것은 [응용 프로그램 설치](https://docs.microsoft.com/en-us/windows/iot-core/develop-your-app/appinstaller#using-provisioning-package-from-wcd) 주체.</span><span class="sxs-lookup"><span data-stu-id="71a7a-156">The correct method for installing .APPX packages in production images is to use a provisioning package as documented in the [Install your app](https://docs.microsoft.com/en-us/windows/iot-core/develop-your-app/appinstaller#using-provisioning-package-from-wcd) subject.</span></span>  <span data-ttu-id="71a7a-157">DeployAppx 쿼리도 지원 합니다. APPX 패키지 정보입니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-157">DeployAppx also supports querying .APPX package information.</span></span>

*  `DeployAppx install MyApp.appx` <span data-ttu-id="71a7a-158">설치 합니다. APPX와 이름이 같은 인증서 경우 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-158">installs the .APPX and the certificate of the same name if found.</span></span>
* `DeployAppx install force MyApp.appx` <span data-ttu-id="71a7a-159">현재 설치 된 제거 하도록 합니다. 동일한 패키지를 사용 하 여 APPX 이름을 지정 하는 경우 새 설치 되기 전에 발견 합니다. APPX입니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-159">forces uninstalling the currently installed .APPX with the same package name if found before installing the new .APPX.</span></span>  <span data-ttu-id="71a7a-160">이 설치 하는 데는 합니다. 현재 설치 된와 동일 하거나 더 낮은 버전 번호를 사용 하 여 APPX입니다. APPX입니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-160">This is useful for installing an .APPX with the same or lower version number as the currently installed .APPX.</span></span>
* `DeployAppx install retry MyApp.appx` <span data-ttu-id="71a7a-161">설치 다시 시도 합니다. 2 초를 사용 하 여 실패 시 APPX 10 번 시도 간 연기 합니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-161">retry installing the .APPX 10 times on failure with 2 second delay between attempts.</span></span>
* `DeployAppx uninstall App_1.0.1.0_x86__publisherid123` <span data-ttu-id="71a7a-162">일치 하는 패키지의 전체 이름을 사용 하 여.appx를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-162">uninstall the .appx with the matching package full name.</span></span>
*  `DeployAppx uninstall MyApp.appx` <span data-ttu-id="71a7a-163">설치 된 모든를 제거 합니다. 일치 하는 패키지 제품군 이름을 사용 하 여 APPX입니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-163">uninstall any installed .APPX with a matching package family name.</span></span>
* `DeployAppx getpackages` <span data-ttu-id="71a7a-164">설치 된 패키지 전체 이름을 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-164">lists installed package full names.</span></span>
* `DeployAppx getpackageid IotCoreDefaultApp.appx` <span data-ttu-id="71a7a-165">패키지 이름, 패키지 제품군 이름 및 전체 이름에 대 한 패키지를 출력 합니다. APPX입니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-165">prints out the package name, the package family name, and the package full name for the .APPX.</span></span>
```cmd
DeployAppx getpackageid IotCoreDefaultApp.appx
         Package Name: 16454Windows10IOTCore.IOTCoreDefaultApplication
  Package Family Name: 16454Windows10IOTCore.IOTCoreDefaultApplication_rz84sjny4rf58
    Package Full Name: 16454Windows10IOTCore.IOTCoreDefaultApplication_2.0.8.0_arm__rz84sjny4rf58
```
* `DeployAppx register appxmanifest.xml` <span data-ttu-id="71a7a-166">지원되지 않음</span><span class="sxs-lookup"><span data-stu-id="71a7a-166">unsupported</span></span>


## <a name="general-command-line-utils"></a><span data-ttu-id="71a7a-167">일반 명령줄 유틸리티</span><span class="sxs-lookup"><span data-stu-id="71a7a-167">General Command Line Utils</span></span>

### **<a name="update-account-password"></a><span data-ttu-id="71a7a-168">계정 암호를 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-168">Update account password:</span></span>**

<span data-ttu-id="71a7a-169">관리자 계정에 대 한 기본 암호를 업데이트 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-169">It is highly recommended that you update the default password for the Administrator account.</span></span> <span data-ttu-id="71a7a-170">이렇게 하려면 다음 명령을 실행 수: `net user Administrator [new password]` 여기서 `[new password]` 원하는 강력한 암호를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-170">To do this, you can issue the following command: `net user Administrator [new password]` where `[new password]` represents a strong password of your choice.</span></span>

### **<a name="create-local-user-accounts"></a><span data-ttu-id="71a7a-171">로컬 사용자 계정을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-171">Create local user accounts:</span></span>**

<span data-ttu-id="71a7a-172">Windows IoT Core 장치에 다른 사용자가 액세스할 수 있도록 하려는 경우에 추가 로컬 사용자 계정을 입력 하 여 PS를 사용 하 여을 만들 수 있습니다 `net user [username] [password] /add`합니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-172">If you wish to give others access to your Windows IoT Core device, you can create additional local user accounts using PS by typing in `net user [username] [password] /add`.</span></span> <span data-ttu-id="71a7a-173">관리자 그룹과 같은 다른 그룹에이 사용자를 추가 하려는 경우 사용 하 여 `net localgroup Administrators [username] /add`입니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-173">If you wish to add this user to other groups, such as the Administrator group, use `net localgroup Administrators [username] /add`.</span></span>

### **<a name="set-password"></a><span data-ttu-id="71a7a-174">암호를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-174">Set password:</span></span>**

<span data-ttu-id="71a7a-175">장치에서 계정에 암호를 변경 하려면 `net user [account-username] [new-password]` 계정 암호를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-175">To change the password on an account on your device, run `net user [account-username] [new-password]` to change the account password.</span></span>

### **<a name="query-and-set-device-name"></a><span data-ttu-id="71a7a-176">쿼리 및 장치 이름을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-176">Query and set device name:</span></span>**

<span data-ttu-id="71a7a-177">현재 장치 이름이 식별 하려면 입력 `hostname`합니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-177">To identify your current device name, simply type `hostname`.</span></span> <span data-ttu-id="71a7a-178">Windows IoT Core 장치 이름을 변경 하려면 입력 `SetComputerName [new machinename]`합니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-178">To change the name of your Windows IoT Core device, type `SetComputerName [new machinename]`.</span></span> <span data-ttu-id="71a7a-179">장치 이름 변경 내용을 적용 하려면 다시 시작 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-179">You may need to restart your device for the name change to take effect.</span></span>

### **<a name="basic-network-configuration"></a><span data-ttu-id="71a7a-180">기본 네트워크 구성:</span><span class="sxs-lookup"><span data-stu-id="71a7a-180">Basic network configuration:</span></span>**

<span data-ttu-id="71a7a-181">와 같은 명령을 포함 하 여 Windows IoT Core에서 사용할 수 있는 다양 한 기본 네트워크 구성 유틸리티를 사용 하 여 이미 익숙할 수도 있습니다 `ping.exe`, `netstat.exe`를 `netsh.exe`, `ipconfig.exe`에 `tracert.exe`, 및 `arp.exe`합니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-181">Many of the basic network configuration utilities you may already be familiar with are available in Windows IoT Core, including commands such as `ping.exe`, `netstat.exe`, `netsh.exe`, `ipconfig.exe`, `tracert.exe`, and `arp.exe`.</span></span>

### **<a name="copy-utilities"></a><span data-ttu-id="71a7a-182">유틸리티를 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-182">Copy utilities:</span></span>**

<span data-ttu-id="71a7a-183">Microsoft는 등의 익숙한 도구를 제공 `sfpcopy.exe` 뿐만 `xcopy.exe`합니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-183">Microsoft is providing familiar tools, including `sfpcopy.exe` as well as `xcopy.exe`.</span></span>

### **<a name="process-management"></a><span data-ttu-id="71a7a-184">프로세스 관리:</span><span class="sxs-lookup"><span data-stu-id="71a7a-184">Process Management:</span></span>**

<span data-ttu-id="71a7a-185">현재 실행 중인 프로세스를 보려면 하나를 시도 `get-process` 또는 `tlist.exe`합니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-185">To view currently running processes, you can try either `get-process` or alternatively `tlist.exe`.</span></span> <span data-ttu-id="71a7a-186">실행 중인 프로세스를 중지 하려면 입력 `kill.exe [pid or process name]`합니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-186">To stop a running process, type `kill.exe [pid or process name]`.</span></span>


### **<a name="set-boot-option-headless-vs-headed-boot"></a><span data-ttu-id="71a7a-187">부팅 옵션 (헤드 부팅 및 헤드리스)를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-187">Set Boot Option (Headless vs. headed boot):</span></span>**

<span data-ttu-id="71a7a-188">Windows IoT Core 장치 때 설정할 수 있습니다에 헤드 (표시 기능이 필요한 경우) 또는 (표시 되지 않음 필수 또는 사용 가능) 하는 경우에 헤드리스 장치 모드입니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-188">Windows IoT Core devices can be set to headed (when display capabilities are required) or headless (when a display is not required or available) device mode.</span></span> <span data-ttu-id="71a7a-189">이 설정을 변경 하려면 사용 하 여 `setbootoption.exe [headed | headless]`입니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-189">To change this setting, use `setbootoption.exe [headed | headless]`.</span></span>

> [!NOTE]
> <span data-ttu-id="71a7a-190">이 설정을 변경 하면 변경 내용이 적용 되려면에서 다시 부팅을 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-190">Changing this setting will require a reboot in order for the change to take effect.</span></span>

### **<a name="task-scheduler"></a><span data-ttu-id="71a7a-191">작업 스케줄러:</span><span class="sxs-lookup"><span data-stu-id="71a7a-191">Task scheduler:</span></span>**

<span data-ttu-id="71a7a-192">현재 예약 된 작업 목록을 보려면 사용 하 여는 `schtasks.exe` 명령입니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-192">To view the current list of scheduled tasks, use the `schtasks.exe` command.</span></span> <span data-ttu-id="71a7a-193">사용 하 여 새 작업을 만들 수 있습니다 합니다 `/create` 전환 하거나 사용 하 여 요청 시 작업 실행을 `/run` 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-193">You can create new tasks with the `/create` switch or run on-demand tasks with the `/run` switch.</span></span> <span data-ttu-id="71a7a-194">전체 목록은 지원 되는 매개 변수를 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="71a7a-194">For a full list of supported parameters, use</span></span> `schtasks.exe /?`

### **<a name="device-drivers"></a><span data-ttu-id="71a7a-195">장치 드라이버:</span><span class="sxs-lookup"><span data-stu-id="71a7a-195">Device drivers:</span></span>**

<span data-ttu-id="71a7a-196">장치 콘솔 유틸리티를 식별 하 고 설치 된 장치 및 드라이버 관리에 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-196">The device console utility is useful in identifying and managing installed devices and drivers.</span></span> <span data-ttu-id="71a7a-197">매개 변수의 전체 목록을 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="71a7a-197">For a full list of parameters, use</span></span> `devcon.exe /?`

### **<a name="registry-access"></a><span data-ttu-id="71a7a-198">레지스트리 액세스:</span><span class="sxs-lookup"><span data-stu-id="71a7a-198">Registry Access:</span></span>**

<span data-ttu-id="71a7a-199">보기 또는 설정 수정, 사용 하 여 레지스트리에 액세스 해야 하는 경우는 `reg.exe /?` 지원 되는 매개 변수의 전체 목록은 명령입니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-199">If you need to access the registry to view or modify settings, use the `reg.exe /?` Command for the full list of supported parameters.</span></span>

### **<a name="services"></a><span data-ttu-id="71a7a-200">서비스:</span><span class="sxs-lookup"><span data-stu-id="71a7a-200">Services:</span></span>**

<span data-ttu-id="71a7a-201">Windows 서비스 관리를 통해 수행할 수 있습니다는 `net.exe` 명령입니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-201">Managing Windows services can be accomplished via the `net.exe` command.</span></span> <span data-ttu-id="71a7a-202">실행 중인 서비스 목록을 보려면 `net start`합니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-202">To see a list of running services, type `net start`.</span></span> <span data-ttu-id="71a7a-203">입력을 시작 하거나 특정 서비스를 중지 하려면 `net [start | stop] [service name]`합니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-203">To start or stop a specific service, type `net [start | stop] [service name]`.</span></span> <span data-ttu-id="71a7a-204">또는 사용할 수도 있습니다 서비스 제어 관리자를 통해 `sc.exe` 명령입니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-204">Alternatively, you can also use the service control manager via `sc.exe` command.</span></span>

### **<a name="boot-configuration"></a><span data-ttu-id="71a7a-205">부팅 구성:</span><span class="sxs-lookup"><span data-stu-id="71a7a-205">Boot configuration:</span></span>**

<span data-ttu-id="71a7a-206">변경할 수 있습니다 Windows IoT Core 장치 부팅 구성을 사용 하 여 `bcdedit.exe`입니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-206">You can make changes to the boot configuration of your Windows IoT Core device by using `bcdedit.exe`.</span></span> <span data-ttu-id="71a7a-207">사용 하 여 설정할 수 있습니다. 예를 들어 `bcdedit –set testsigning on` 명령입니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-207">For instance, you can enable testsigning with `bcdedit –set testsigning on` command.</span></span>

### **<a name="shutdownrestart-device"></a><span data-ttu-id="71a7a-208">종료/다시 시작 장치:</span><span class="sxs-lookup"><span data-stu-id="71a7a-208">Shutdown/restart device:</span></span>**

<span data-ttu-id="71a7a-209">장치를 종료 하려면 입력 `shutdown /s /t 0`합니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-209">To shut down your device, type `shutdown /s /t 0`.</span></span> <span data-ttu-id="71a7a-210">장치를 다시 시작 하려면 사용 합니다 `/r` 명령을 사용 하 여 대신 전환 `shutdown /r /t 0`합니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-210">To restart the device, use the `/r` switch instead with the command `shutdown /r /t 0`.</span></span>

### **<a name="viewing-and-changing-display-settings"></a><span data-ttu-id="71a7a-211">보기 및 표시 설정 변경</span><span class="sxs-lookup"><span data-stu-id="71a7a-211">Viewing and changing display settings</span></span>**
<span data-ttu-id="71a7a-212">현재 디스플레이 설정을 나열에 대 한 지원 되는 값의 목록을 표시 하려면 SetDisplayResolution 도구를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-212">The SetDisplayResolution tool may be used for listing the current display settings and to show the list of supported values.</span></span>  <span data-ttu-id="71a7a-213">디스플레이 해상도, 새로 고침 빈도 및/또는 방향 플랫폼에서 지 원하는 값으로 조정 하기 위해 사용할 더 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-213">It can further be used for adjusting the display's resolution, refresh rate and/or orientation to values supported by your platform.</span></span>  <span data-ttu-id="71a7a-214">유틸리티는 다음 명령줄 인수를 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-214">The utility accepts the following command line arguments:</span></span>

* `SetDisplayResolution` <span data-ttu-id="71a7a-215">현재 표시 resoltuion를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-215">Lists the current display resoltuion.</span></span>
* `SetDisplayResolution -list` <span data-ttu-id="71a7a-216">지원 되는 디스플레이 해상도 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-216">Lists supported display resolutions.</span></span>
* `SetDisplayResolution -orientation:[n]` <span data-ttu-id="71a7a-217">표시 방향 변경, 여기서 n = 0, 90, 180 또는 270 합니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-217">Change the display orientation, where n=0,90,180 or 270.</span></span>
* `SetDisplayResolution [width] [height]` <span data-ttu-id="71a7a-218">너비와 높이 (픽셀) 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-218">Change the width and height in pixels</span></span> 
* `SetDisplayResolution [width] [height] [refreshrate]` <span data-ttu-id="71a7a-219">너비와 높이에 있는 픽셀 및 Hz 단위로 refreshrate 변경 너비, 높이 및 새로 고침 비율</span><span class="sxs-lookup"><span data-stu-id="71a7a-219">Change width, height and refresh rate where width and height are in pixels and refreshrate in Hz</span></span> 
* `SetDisplayResolution [width] [height] [refreshrate] [orientation]` <span data-ttu-id="71a7a-220">너비와 높이 픽셀 Hz 단위로 refreshrate 않았고 방향을 0, 90, 180 또는 270 중 하나인 너비, 높이, refreshrate 및 화면 방향을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-220">Change width, height, refreshrate and screen orientation where width and height are in pixels, refreshrate in Hz and orientation is one of 0, 90, 180 or 270.</span></span>

### **<a name="take-screenshot"></a><span data-ttu-id="71a7a-221">스크린 샷을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-221">Take screenshot:</span></span>**

<span data-ttu-id="71a7a-222">사용 하 여 Windows IoTCore 장치의 스크린 샷을 수행할 수 있는 `ScreenCapture.exe`합니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-222">You can take the screenshot of your Windows IoTCore device by using `ScreenCapture.exe`.</span></span> <span data-ttu-id="71a7a-223">예를 들어 실행 `ScreenCapture c:\folder\screencap.jpg` 스크린샷 및 screencap.jpg 파일에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-223">For example, run `ScreenCapture c:\folder\screencap.jpg` will take the screenshot and save it in screencap.jpg file.</span></span>

### **<a name="get-information-about-network-adapters"></a><span data-ttu-id="71a7a-224">네트워크 어댑터에 대 한 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-224">Get information about Network Adapters:</span></span>**

<span data-ttu-id="71a7a-225">모든 사용 가능한 네트워크 어댑터 목록을 보려면 실행 `GetAdapterInfo` 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-225">To view the list of all the available network adapters, run `GetAdapterInfo` tool.</span></span>

### **<a name="set-folder-permissions-for-uwp-apps"></a><span data-ttu-id="71a7a-226">UWP 앱에 대 한 폴더 사용 권한을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-226">Set folder permissions for UWP apps:</span></span>**

<span data-ttu-id="71a7a-227">장치에서 일부 폴더에는 유니버설 Windows 앱에서 액세스할 수는 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-227">Not all folders on your device are accesible by Universal Windows Apps.</span></span> <span data-ttu-id="71a7a-228">UWP 앱에는 폴더 액세스할 수 있도록 사용할 수 있습니다 `FolderPermissions` 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-228">To make a folder accesible to a UWP app, you can use `FolderPermissions` tool.</span></span> <span data-ttu-id="71a7a-229">예를 들어 실행할 `FolderPermissions c:\test -e` UWP 앱에 액세스 권한을 부여 하려면 `c:\test` 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-229">For example run `FolderPermissions c:\test -e` to give UWP apps access to `c:\test` folder.</span></span> <span data-ttu-id="71a7a-230">이 작동 하기 위한 네이티브 Win32 api를 사용 하 여만 예를 들어 참고 합니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-230">Note this will work only with native Win32 apis for eg.</span></span> <span data-ttu-id="71a7a-231">CreateFile2 StorageFolder, StorageFile 등과 같은 WinRT api 관련이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-231">CreateFile2 and not with WinRT apis like StorageFolder, StorageFile etc.</span></span>

### **<a name="work-with-serial-ports"></a><span data-ttu-id="71a7a-232">직렬 포트를 사용 하 여 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-232">Work with Serial Ports:</span></span>**
<span data-ttu-id="71a7a-233">[MinComm](https://github.com/ms-iot/samples/tree/develop/MinComm) 명령줄에서 직렬 포트를 사용 하 여 작업할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-233">[MinComm](https://github.com/ms-iot/samples/tree/develop/MinComm) allows you to work with serial ports from the command line.</span></span> <span data-ttu-id="71a7a-234">Ms iot 샘플 리포지토리에서 샘플 프로젝트로 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="71a7a-234">It is provided as a sample project in the ms-iot samples repo.</span></span> 

``` 
Usage: MinComm.exe [-list] device_path [baud=<B>] [parity=<P>] [data=<D>] [stop=<S>] [xon={on|off}] [odsr={on|off}] [octs={on|off}] [dtr={on|off|hs}] [rts={on|off|hs|tg}] [idsr={on|off}]

  -list                List all available serial ports on the system and exit.
  device_path          Device path or COM port to open (e.g. COM1)
  baud=<B>             Specifies the transmission rate in bits per second.
  parity={n|e|o|m|s}   Specifies how the system uses the parity bit to check
                       for transmission errors. The abbreviations stand for
                       none, even, odd, mark, and space.
  data={5|6|7|8}       Specifies the number of data bits in a character.
  stop={1|1.5|2}       Specifies the number of stop bits that define the end of
                       a character.
  xon={on|off}         Specifies whether the xon or xoff protocol for data-flow
                       control is on or off.
  odsr={on|off}        Specifies whether output handshaking that uses the
                       Data Set Ready (DSR) circuit is on or off.
  octs={on|off}        Specifies whether output handshaking that uses the
                       Clear To Send (CTS) circuit is on or off.
  dtr={on|off|hs}      Specifies whether the Data Terminal Ready (DTR) circuit
                       is on or off or set to handshake.
  rts={on|off|hs|tg}   Specifies whether the Request To Send (RTS) circuit is
                       set to on, off, handshake, or toggle.
  idsr={on|off}        Specifies whether the DSR circuit sensitivity is on
                       or off.

Parameters that are not specified will default to the port's current
configuration. For more information on the connection parameters, see the
Technet documentation for the Mode command:
  https://technet.microsoft.com/library/cc732236.aspx

Examples:
  Connect to the first serial port found in the port's current configuration:
    MinComm.exe

  List all serial ports on the system:
    MinComm.exe -list

  Open COM1 in 115200 8N1 configuration:
    MinComm.exe COM1 baud=115200 parity=n data=8 stop=1

  Open COM1 in 115200 8N1 configuration:
    MinComm.exe \\.\COM1 baud=115200 parity=n data=8 stop=1

  Open device interface in 115200 8N1 configuration:
    MinComm.exe \\?\USB#VID_FFFF&PID_0005#{86e0d1e0-8089-11d0-9ce4-08003e301f73} baud=115200 parity=n data=8 stop=1```

