---
title: 드라이버 배포
author: parameshbabu
ms.author: pabab
ms.date: 08/22/2017
ms.topic: article
description: 빌드 및 Visual Studio를 사용 하 여 드라이버를 배포 하는 방법에 알아봅니다.
keywords: windows 10 IoT Core, 드라이버 배포
ms.openlocfilehash: aad50718ea44c46d676509fe2c5b408d471afc19
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513750"
---
# <a name="driver-deployment"></a><span data-ttu-id="7b88f-104">드라이버 배포</span><span class="sxs-lookup"><span data-stu-id="7b88f-104">Driver deployment</span></span>

<span data-ttu-id="7b88f-105">Visual Studio를 사용 하 여 Windows 10 IoT Core 드라이버를 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b88f-105">Deploy a driver on Windows 10 IoT Core with Visual Studio.</span></span> 

<span data-ttu-id="7b88f-106">컴파일 및 드라이버 개발 단계는 특정 플랫폼에 대 한 드라이버를 배포할 수 있도록 Visual Studio 드라이버 프로젝트를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b88f-106">Configure your Visual Studio driver project so that you can compile and deploy a driver for a specific platform during driver development phase.</span></span> 

<span data-ttu-id="7b88f-107">이 연습에 사용할 수 있습니다 합니다 [gpiokmdfdemo 샘플 드라이버](https://github.com/ms-iot/samples/tree/develop/DriverSamples)합니다.</span><span class="sxs-lookup"><span data-stu-id="7b88f-107">For this exercise you can use the [gpiokmdfdemo sample driver](https://github.com/ms-iot/samples/tree/develop/DriverSamples).</span></span>

<span data-ttu-id="7b88f-108">이미지에 드라이버를 추가 하려는 경우의 지침을 방문 하십시오 우리의 [IoT 제조 가이드](https://docs.microsoft.com/windows-hardware/manufacture/iot/add-a-driver-to-an-image)합니다.</span><span class="sxs-lookup"><span data-stu-id="7b88f-108">If you're looking to add a driver to an image, please visit the instructions in our [IoT Manufacturing Guide](https://docs.microsoft.com/windows-hardware/manufacture/iot/add-a-driver-to-an-image).</span></span>

## <a name="step-1--setup"></a><span data-ttu-id="7b88f-109">1 단계: 설치 프로그램</span><span class="sxs-lookup"><span data-stu-id="7b88f-109">Step 1 : Setup</span></span> 
___

### <a name="on-the-device"></a><span data-ttu-id="7b88f-110">장치에서</span><span class="sxs-lookup"><span data-stu-id="7b88f-110">On the device</span></span>

* <span data-ttu-id="7b88f-111">장치에 IoTCore 이미지에 따라 설치 되어 있는지 확인 합니다 [시작 하기 지침이](https://go.microsoft.com/fwlink/?linkid=860461)합니다.</span><span class="sxs-lookup"><span data-stu-id="7b88f-111">Make sure that your device has an IoTCore image installed by following the [Get Started instructions](https://go.microsoft.com/fwlink/?linkid=860461).</span></span>
* <span data-ttu-id="7b88f-112">통해 장치에 연결할 [Powershell](../connect-your-device/PowerShell.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="7b88f-112">Connect to your device via [Powershell](../connect-your-device/PowerShell.md).</span></span>

### <a name="on-the-pc"></a><span data-ttu-id="7b88f-113">PC에</span><span class="sxs-lookup"><span data-stu-id="7b88f-113">On the PC</span></span>

* <span data-ttu-id="7b88f-114">Visual Studio 2017 설치 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b88f-114">Make sure you have installed Visual Studio 2017.</span></span>
* <span data-ttu-id="7b88f-115">설치 합니다 [Windows 드라이버 키트](https://developer.microsoft.com/windows/hardware/windows-driver-kit)합니다.</span><span class="sxs-lookup"><span data-stu-id="7b88f-115">Install the [Windows Driver Kit](https://developer.microsoft.com/windows/hardware/windows-driver-kit).</span></span>  <span data-ttu-id="7b88f-116">SDK 및 WDK를 설치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b88f-116">You will need to install the SDK and WDK.</span></span>
* <span data-ttu-id="7b88f-117">드라이버가 올바르게 서명 되 고 장치에서 실행할 수 있도록 인증서를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b88f-117">Install the certificates so that the driver is signed correctly and can run on your device.</span></span> <span data-ttu-id="7b88f-118">관리자 권한 명령 프롬프트에서 아래 나열 된 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b88f-118">From an elevated command prompt execute the commands listed below:</span></span>

    1.  `cd c:\Program Files (x86)\Windows Kits\10\Tools\bin\i386` 
    2.  `set WPDKContentRoot=c:\Program Files (x86)\Windows Kits\10`
    3.  `InstallOEMCerts.cmd`
  
* <span data-ttu-id="7b88f-119">적용 VS에서 F5 배포를 사용 하도록 수정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b88f-119">Apply fix to enable F5 deployment from VS.</span></span> <span data-ttu-id="7b88f-120">관리자 권한 명령 프롬프트에서 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b88f-120">In the elevated command prompt, execute the following commands:</span></span>

    1.  `cd %TEMP%` <span data-ttu-id="7b88f-121">(디렉터리 변경 됩니다 `c:\users\<usernsme>\Appdata\Local\Temp`)</span><span class="sxs-lookup"><span data-stu-id="7b88f-121">( will change directory to `c:\users\<usernsme>\Appdata\Local\Temp`)</span></span>
    2.  <span data-ttu-id="7b88f-122">`md “WdkTempFiles”` 이 도구에서 버그가 해결 하는 및 수행 하는 데 필요한 "WdkTempFiles" 디렉터리를 수동으로 만듭니다 *한 번만* PC에서.</span><span class="sxs-lookup"><span data-stu-id="7b88f-122">`md “WdkTempFiles”` Manually create a “WdkTempFiles” directory This is a workaround for a bug in the tooling and requires to be done *only once* in the PC.</span></span>


## <a name="step-2--provision-device-with-visual-studio"></a><span data-ttu-id="7b88f-123">2 단계: Visual Studio를 사용 하 여 장치 프로 비전</span><span class="sxs-lookup"><span data-stu-id="7b88f-123">Step 2 : Provision device with Visual Studio</span></span> 
___
* <span data-ttu-id="7b88f-124">Visual Studio를 열고 선택 **드라이버 > 테스트 > 장치 구성 > 새 장치 추가**</span><span class="sxs-lookup"><span data-stu-id="7b88f-124">Open Visual Studio and select **Driver > Test > Configure Devices > Add New Device**</span></span>
    * <span data-ttu-id="7b88f-125">드라이버 메뉴 옵션이 표시 되지 않으면 SDK가 설치 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b88f-125">If the Driver Menu option is not shown, check if SDK is installed.</span></span>

* <span data-ttu-id="7b88f-126">에 **장치 구성** 대화 상자에서</span><span class="sxs-lookup"><span data-stu-id="7b88f-126">In the **Device Configuration** dialog,</span></span> 
    * <span data-ttu-id="7b88f-127">사용자를 입력 하면 대상 장치에 대 한 표시 이름</span><span class="sxs-lookup"><span data-stu-id="7b88f-127">Enter a user friendly Display Name for your target device</span></span>
    * <span data-ttu-id="7b88f-128">장치 유형 선택 = 모바일</span><span class="sxs-lookup"><span data-stu-id="7b88f-128">Select Device Type = Mobile</span></span>
    * <span data-ttu-id="7b88f-129">표시 목록에서 IP 주소순으로 정렬 하 고 IoT 장치에 대 한 주소를 찾으려면 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b88f-129">In the list displayed, sort by IP address, and find the address for the IoT device and select.</span></span> <span data-ttu-id="7b88f-130">두 항목의 경우 0이 아닌 GUID 사용 하 여 하나를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b88f-130">If there are two entries, select the one with the non-zero GUID.</span></span>  <span data-ttu-id="7b88f-131">파란색 강조 표시 해야 하면이 – 행이 선택 되어 있는지 확인</span><span class="sxs-lookup"><span data-stu-id="7b88f-131">Make sure the row is selected – it should highlight blue</span></span>
    * <span data-ttu-id="7b88f-132">대화 상자의 맨 아래에 두 개의 라디오 단추가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b88f-132">At the bottom of the dialog are two radio buttons.</span></span>  <span data-ttu-id="7b88f-133">선택 **장치를 프로 비전 하 고 디버거 설정 선택**합니다.</span><span class="sxs-lookup"><span data-stu-id="7b88f-133">Select the one which says **Provision device and choose debugger settings**.</span></span>  <span data-ttu-id="7b88f-134">선택 **다음**</span><span class="sxs-lookup"><span data-stu-id="7b88f-134">Select **Next**</span></span>

* <span data-ttu-id="7b88f-135">에 **디버거 설정을 구성**, 설정을 적절 하 게 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b88f-135">On the **Configure debugger settings**, set the appropriate settings.</span></span>  <span data-ttu-id="7b88f-136">다음에 유의하세요.</span><span class="sxs-lookup"><span data-stu-id="7b88f-136">Note the following:</span></span>
   * <span data-ttu-id="7b88f-137">MinnowBoardMax 디버깅에 대 한 네트워크를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b88f-137">The MinnowBoardMax can use the network for debugging.</span></span>
       * <span data-ttu-id="7b88f-138">연결 유형을 사용 하 여 **네트워크**</span><span class="sxs-lookup"><span data-stu-id="7b88f-138">Use connection type **Network**</span></span>
       * <span data-ttu-id="7b88f-139">일부 포트를 선택 합니다. – 기본을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b88f-139">Select some port – default can be used</span></span>
       * <span data-ttu-id="7b88f-140">일부 키 선택 – 기본을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b88f-140">Select some key – default can be used</span></span>
       * <span data-ttu-id="7b88f-141">Visual studio를 실행 하는 컴퓨터의 호스트 IP를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b88f-141">Select the host IP of the machine running visual studio.</span></span>  <span data-ttu-id="7b88f-142">Autonet (169.xxx) 주소를 사용 하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="7b88f-142">Do not use the autonet (169.xxx) address.</span></span>
       * <span data-ttu-id="7b88f-143">선택 **다음**</span><span class="sxs-lookup"><span data-stu-id="7b88f-143">Select **Next**</span></span>
       
  ![디버그 설정 구성](../media/DriverDeployment/confdbgsettings.png)
       
    * <span data-ttu-id="7b88f-145">Raspberry Pi의 커널 디버깅에 대 한 직렬 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="7b88f-145">The Raspberry Pi uses serial for kernel debugging.</span></span>
       *  <span data-ttu-id="7b88f-146">PI 및 호스트 컴퓨터에 적절 한 직렬 디버깅 케이블 연결</span><span class="sxs-lookup"><span data-stu-id="7b88f-146">Connect the appropriate serial debugging cable to the PI and the host machine</span></span>
       *  <span data-ttu-id="7b88f-147">선택 **직렬** 연결 형식에 대 한</span><span class="sxs-lookup"><span data-stu-id="7b88f-147">Select **Serial** for the connection type</span></span>
       *  <span data-ttu-id="7b88f-148">Raspberry Pi에 대 한 적절 하 게 매개 변수의 나머지를 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="7b88f-148">Fill out the rest of the parameters as appropriate for the Raspberry Pi.</span></span>
       *  <span data-ttu-id="7b88f-149">선택 **다음**</span><span class="sxs-lookup"><span data-stu-id="7b88f-149">Select **Next**</span></span>

* <span data-ttu-id="7b88f-150">VS 통해 WDK 이제 IoT 장치 프로 비전 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b88f-150">The WDK, through VS, will now provision the IoT device.</span></span>  <span data-ttu-id="7b88f-151">TAEF 고 WDTF은 장치에 설치 하 고 위에 제공 된 설정에 따라 디버깅 커널에 대 한 장치 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7b88f-151">TAEF and WDTF will be installed on the device, and the device will be set up for kernel debugging per the settings provided above.</span></span>

* <span data-ttu-id="7b88f-152">완료 되 면 장치 재부팅 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b88f-152">When complete, the device may reboot.</span></span>  <span data-ttu-id="7b88f-153">진행률 화면에는 **장치 구성** 상태를 제공 하 고 IoT 장치 설치 완료 되 면 표시 완료 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b88f-153">The progress screen on the **Device Configuration** will provide status, and shows complete when the IoT device has completed the installation.</span></span> <span data-ttu-id="7b88f-154">키를 눌러 **완료**합니다.</span><span class="sxs-lookup"><span data-stu-id="7b88f-154">Press **Finish**.</span></span>

![구성 진행률](../media/DriverDeployment/confprogress.png)

* <span data-ttu-id="7b88f-156">장치는 이제 프로 비전 하며 **장치 테스트 구성을** 상태 표시 **드라이버 테스트를 위해 구성**</span><span class="sxs-lookup"><span data-stu-id="7b88f-156">The device is now provisioned and the **Device test configuration** status shows **Configured for driver testing**</span></span>

![ConfigureDevices](../media/DriverDeployment/ConfigureDevices.png)

## <a name="step-3--configure-visual-studio-driver-project"></a><span data-ttu-id="7b88f-158">3 단계: Visual Studio 드라이버 프로젝트 구성</span><span class="sxs-lookup"><span data-stu-id="7b88f-158">Step 3 : Configure Visual Studio driver project</span></span>
___    
1. <span data-ttu-id="7b88f-159">관리자 모드에서 Visual Studio를 시작 하 고 visual studio 드라이버 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="7b88f-159">Launch Visual Studio in the administrator mode and open the visual studio driver project.</span></span>
2. <span data-ttu-id="7b88f-160">대상 플랫폼 버전에는 개발 컴퓨터에 설치 된 SDK와 일치 하는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b88f-160">Make sure the Target Platform Version matches the SDK installed on your development machine.</span></span> <span data-ttu-id="7b88f-161">솔루션 탐색기 창에서 프로젝트 속성을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b88f-161">Select Project Properties from the Solution Explorer window.</span></span>  <span data-ttu-id="7b88f-162">일반 구성 속성에서 개발 컴퓨터에 SDK 설치 대상 플랫폼 버전 일치 항목을 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b88f-162">Under General Configuration Properties assure that the Target Platform Version matches the SDK installed on your development computer.</span></span>  <span data-ttu-id="7b88f-163">SDK의 버전을 확인할 수는 **제어판 > 프로그램 > 프로그램 및 기능**합니다.</span><span class="sxs-lookup"><span data-stu-id="7b88f-163">You can check the version of the SDK from the **Control Panel > Programs > Programs and Features**.</span></span>
3. <span data-ttu-id="7b88f-164">아래 **프로젝트 > 새 항목 추가 > Visual C++ > Windows 드라이버**를 선택 **패키지 매니페스트** 누릅니다 **추가**.</span><span class="sxs-lookup"><span data-stu-id="7b88f-164">Under **Project > Add New Item > Visual C++ > Windows Driver**, select **Package Manifest** and Press **Add**.</span></span>

![PackageManifest](../media/DriverDeployment/PackageManifest.png)

 `Package.pkg.xml` <span data-ttu-id="7b88f-166">파일을 프로젝트에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7b88f-166">file will be added to the project.</span></span> <span data-ttu-id="7b88f-167">이 파일의 소유자, 플랫폼, 구성 요소 및 하위 구성 요소 태그를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b88f-167">In this file, specify the Owner, Platform, Component and SubComponent tags.</span></span> 
 
![Package-pkg-xml](../media/DriverDeployment/Package-pkg-xml.png)
 
4. <span data-ttu-id="7b88f-169">패키지 버전 번호를 설정 **프로젝트 속성 > PackageGen > 버전**합니다.</span><span class="sxs-lookup"><span data-stu-id="7b88f-169">Set package version number at **Project Properties > PackageGen > Version**.</span></span> <span data-ttu-id="7b88f-170">드라이버의 설치/다시 설치를 수행 해야 할 때마다이 버전 번호에 증가를 참고 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b88f-170">Note that every time you need to perform a Install/Reinstall of the driver, this version number has to be incremented.</span></span>

![PackageVersion](../media/DriverDeployment/PackageVersion.png)

5. <span data-ttu-id="7b88f-172">아래 **프로젝트 속성 > 드라이버 서명 > 테스트 인증서**, 인증서 (Phone OEM 테스트 인증서) 테스트 선택</span><span class="sxs-lookup"><span data-stu-id="7b88f-172">Under **Project Properties > Driver Signing > Test Certificate**, select test certificate (Phone OEM Test Certificate)</span></span>

![DriverSigning](../media/DriverDeployment/DriverTestSigning.png)

6. <span data-ttu-id="7b88f-174">로 이동 **드라이버 설치** 선택한 **배포**</span><span class="sxs-lookup"><span data-stu-id="7b88f-174">Go to **Driver Install** and select **Deployment**</span></span>

![InstallOptions](../media/DriverDeployment/installOptions.png)

* <span data-ttu-id="7b88f-176">**대상 장치 이름** 드롭다운 대상 프로 비전 프로세스에서 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b88f-176">From the **Target Device Name** dropdown, select the target created above in the provisioning process.</span></span> <span data-ttu-id="7b88f-177">에 대 한 두 가지 옵션을 확인할 수 있습니다 **설치 / 다시 설치** 하 고 **빠른 다시 설치**합니다.</span><span class="sxs-lookup"><span data-stu-id="7b88f-177">Notice the two options for **Install / Reinstall** and **Fast Reinstall**.</span></span> <span data-ttu-id="7b88f-178">선택 옵션 및 클릭 **확인**합니다.</span><span class="sxs-lookup"><span data-stu-id="7b88f-178">Choose an option and Click **Ok**.</span></span>
* <span data-ttu-id="7b88f-179">**설치 / 다시 설치** 대상 하는 드라이버의 초기 설치에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7b88f-179">**Install / Reinstall** is used for the initial installation of a driver to the target.</span></span>  <span data-ttu-id="7b88f-180">이 Windows 업데이트 스택을 사용 하 여 드라이버 패키지를 설치 하 고 몇 분 정도 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b88f-180">This installs the driver package using the Windows update stack and can take several minutes.</span></span> <span data-ttu-id="7b88f-181">INF 파일 변경 될 때마다이 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b88f-181">This must be used every time the INF file is changed.</span></span> 
    
> [!TIP]
> <span data-ttu-id="7b88f-182">초기 설치 후 드라이버를 설치 하려면이 옵션을 사용 될 때마다 패키지 버전 번호가 증가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b88f-182">Every time this option is used to install a driver after the initial installation, the package version number must be incremented.</span></span>

* <span data-ttu-id="7b88f-183">**다시 설치 빠른** 드라이버 설치가 시작 된 후 변경 내용이 없습니다 후속 드라이버 INF 파일에 레지스트리를 영향을 줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b88f-183">**Fast Reinstall** can be used once a driver has been installed, and there are no subsequent changes to the drivers INF file which affect the registry.</span></span>  <span data-ttu-id="7b88f-184">설치 프로세스를 무시 하 드라이버와 관련 된 모든 devnodes 종료, 드라이버를 복사 및 devnode를 원래 대로 다시 시작 하는이 메서드.</span><span class="sxs-lookup"><span data-stu-id="7b88f-184">This method bypasses the install process, shuts down all devnodes associated with the driver, copies the driver over, and restarts the devnode.</span></span>  <span data-ttu-id="7b88f-185">그러면 몇 (< 20) 시간 (초)입니다.</span><span class="sxs-lookup"><span data-stu-id="7b88f-185">This takes a few (<20) seconds.</span></span>

    
> [!WARNING]
> <span data-ttu-id="7b88f-186">이 메서드는 devnode 종료 드라이버를 릴리스 하 여야 합니다. 어떤 이유로 작업이 실패 하는 경우 – 되려면 보장 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7b88f-186">This method is not guaranteed to succeed – If for some reason a devnode cannot be shutdown to release the driver, the operation will fail.</span></span>  <span data-ttu-id="7b88f-187">이 하드웨어 오류 또는 잘못 된 드라이버 구현을 초기 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b88f-187">This can be due to faulty hardware, or an initial faulty implementation of the driver.</span></span>  <span data-ttu-id="7b88f-188">설치/다시 설치 옵션은이 경우에 사용 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b88f-188">The Install/Reinstall option must be used in this case.</span></span>


<span data-ttu-id="7b88f-189">이제 Visual Studio 프로젝트를 빌드하고 대상 장치의 드라이버를 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b88f-189">Your Visual Studio project is now ready to build and deploy a driver to your target device.</span></span> <span data-ttu-id="7b88f-190">ACPI 테이블 및 대상 장치에 복사본을 생성 해야 하는 샘플 gpiokmdfdemo 드라이버를 사용 하는 경우 다음의 단계를 따릅니다 [Visual Studio에서 드라이버를 빌드할](https://developer.microsoft.com/en-us/windows/iot/samples/driverlab2)합니다.</span><span class="sxs-lookup"><span data-stu-id="7b88f-190">If you are using the sample gpiokmdfdemo driver you need to generate ACPI table and copy to your target device, then follow the steps in [building the driver in Visual Studio](https://developer.microsoft.com/en-us/windows/iot/samples/driverlab2).</span></span>


## <a name="step-4--build-and-deploy-driver"></a><span data-ttu-id="7b88f-191">4 단계: 빌드 및 드라이버를 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b88f-191">Step 4 : Build and deploy driver</span></span>
___
<span data-ttu-id="7b88f-192">사용 하 여 두 가지 방법으로이 작업을 수행할 수 있습니다 합니다 **F5** 키 및 사용 하 여 합니다 **배포** 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="7b88f-192">This can be done in two ways, using the **F5** key and using the **Deploy** option.</span></span> <span data-ttu-id="7b88f-193">두 가지 방법으로 드라이버를 빌드 및 배포 (즉, 해당 장치에 설치) F5 설치 및 로드 된 드라이버를 Visual Studio 커널 디버거를 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b88f-193">In both ways, the driver will be built and deployed (i.e. installs it on device) and the F5 attaches the Visual Studio kernel debugger to the installed and loaded driver.</span></span> 

<span data-ttu-id="7b88f-194">일부 사용자가 선호 하는 **배포** 기능 WinDBG에서 KD 등 다른 커널 디버거를 연결 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b88f-194">Some users prefer to use the **Deploy** functionality and attach a different kernel debugger, such as WinDBG or KD.</span></span>  <span data-ttu-id="7b88f-195">이 VS 디버거를 사용 하 여 보다 더 많은 유연성을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b88f-195">This can provide more flexibility than using the VS debugger.</span></span>

### <a name="deploy"></a><span data-ttu-id="7b88f-196">배포</span><span class="sxs-lookup"><span data-stu-id="7b88f-196">Deploy</span></span>
1.  <span data-ttu-id="7b88f-197">솔루션 탐색기에서 프로젝트를 마우스 오른쪽 단추로 클릭</span><span class="sxs-lookup"><span data-stu-id="7b88f-197">Right-click on the project in the solution explorer</span></span>
2.  <span data-ttu-id="7b88f-198">선택 **배포**</span><span class="sxs-lookup"><span data-stu-id="7b88f-198">Select **Deploy**</span></span>

![배포](../media/DriverDeployment/deploy.png) 

3.  <span data-ttu-id="7b88f-200">배포 프로세스를 진행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b88f-200">The deployment process should proceed.</span></span>  <span data-ttu-id="7b88f-201">IoT 장치를 배포 후 다시 부팅 됩니다 및 설치가 진행 되는 동안 "기어" 화면을 표시 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b88f-201">The IoT device will be rebooted after deployment, and should show the “Gears” screen while installation is taking place.</span></span>

<span data-ttu-id="7b88f-202">빌드 출력은는 **출력** 상태는 경우 설치 [출력] 창을 창 배포가 완료 되 고 장치 마찬가지로 다시 부팅 됩니다 VS 출력 화면 성공 또는 실패를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b88f-202">Build output is in the **Output** Window Deployment status is also in the output window When Installation completes, the device will reboot again, and the VS Output screen will indicate success or failure.</span></span>

### <a name="f5"></a><span data-ttu-id="7b88f-203">F5</span><span class="sxs-lookup"><span data-stu-id="7b88f-203">F5</span></span>

1.  <span data-ttu-id="7b88f-204">빌드 창에서 있는지 확인 하는 구성이 올바른지 – 현재 빌드 arch 대상 장치 arch 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b88f-204">From the build window, make sure that the configurations are correct – the current build arch is the same as the target device arch.</span></span>  <span data-ttu-id="7b88f-205">이 여기서 아치 대상 이름에는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b88f-205">This is where having the arch in the target name is valuable.</span></span>  <span data-ttu-id="7b88f-206">대상 VS에서 위쪽-가운데-오른쪽의 메뉴 모음에서 보기 상자에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7b88f-206">The target will be displayed in the view box on the menu bar in VS on the top-middle-right.</span></span>
2.  <span data-ttu-id="7b88f-207">키를 눌러 **F5**합니다.</span><span class="sxs-lookup"><span data-stu-id="7b88f-207">Press **F5**.</span></span>  <span data-ttu-id="7b88f-208">대상 빌드, 배포 및 VS 커널 디버거를 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b88f-208">The target will be built, deployed, and attached to the VS Kernel Debugger.</span></span>

* <span data-ttu-id="7b88f-209">다시 부팅 하면 확인 되는지 PowerShell을 아직 연결 되어이 고, 그렇지 다시 연결 PowerShell을 사용 하 여 대상 장치로 `enter-pssession` 명령...</span><span class="sxs-lookup"><span data-stu-id="7b88f-209">After the reboot, make sure PowerShell is still connected to it, otherwise, re-connect to the target device using the PowerShell `enter-pssession` command..</span></span>


## <a name="known-issues"></a><span data-ttu-id="7b88f-210">알려진 문제</span><span class="sxs-lookup"><span data-stu-id="7b88f-210">Known Issues</span></span>
___

### <a name="provisioning-errors"></a><span data-ttu-id="7b88f-211">프로 비전 오류</span><span class="sxs-lookup"><span data-stu-id="7b88f-211">Provisioning Errors</span></span>
<span data-ttu-id="7b88f-212">프로 비전 중 MinnowBoardMax와의 상호 작용 하는 동안 경합 상태가 보고 된 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b88f-212">A race condition during the interaction with MinnowBoardMax can result in a reported failure during provisioning.</span></span>  <span data-ttu-id="7b88f-213">사실, 프로 비전 가능성이 성공 했습니다.</span><span class="sxs-lookup"><span data-stu-id="7b88f-213">In fact, the provisioning most likely succeeded.</span></span>

**<span data-ttu-id="7b88f-214">오류 목록:</span><span class="sxs-lookup"><span data-stu-id="7b88f-214">List of Errors:</span></span>**
 
* <span data-ttu-id="7b88f-215">오류: 작업 "등록 WDTF" 성공적으로 완료 하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="7b88f-215">ERROR: Task "Registering WDTF" failed to complete successfully.</span></span>
* <span data-ttu-id="7b88f-216">오류: 작업 "커널 디버거 설정 구성 (재부팅이)"를 성공적으로 완료 하지 못함</span><span class="sxs-lookup"><span data-stu-id="7b88f-216">ERROR: Task "Configuring kernel debugger settings (possible reboot)" failed to complete successfully</span></span>

<span data-ttu-id="7b88f-217">**해결 방법:** 이러한 오류는 거의 확실히 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7b88f-217">**Workaround:** These error can almost certainly be ignored.</span></span>

**<span data-ttu-id="7b88f-218">세부 정보:</span><span class="sxs-lookup"><span data-stu-id="7b88f-218">Details:</span></span>**

<span data-ttu-id="7b88f-219">에 다음 오류가 표시 됩니다는 **장치 구성 구성 진행률** 대화 상자:</span><span class="sxs-lookup"><span data-stu-id="7b88f-219">The following error will be displayed in the **Device Configuration Configuration Progress** dialog:</span></span>

```
Installing necessary components...
Removing TAEF test service
    Task "Removing TAEF test service" completed successfully
Copying required files
    Task "Copying required files" completed successfully
Registering TAEF Test Service
    Task "Registering TAEF Test Service" completed successfully
Starting TAEF Test Service
    Task "Starting TAEF Test Service" completed successfully
Registering WDTF
    Task "Registering WDTF" completed successfully 
Configuring TAEF test service to start automatically
    Task "Configuring TAEF test service to start automatically" completed successfully
Configuring kernel debugger settings (possible reboot)
    ERROR: Task "Configuring kernel debugger settings (possible reboot)" failed to complete successfully. Look at the logs in the driver test group explorer for more details on the failure.
Configuring computer settings (possible reboot)
Waiting for task to complete...
Waiting for task to complete...
    Task "Configuring computer settings (possible reboot)" completed successfully
Computer configuration log file://C:/Users/username/AppData/Roaming/Microsoft/WDKTestInfrastructure/ProvisioningLogs/Driver%20Test%20Computer%20Configuration%log
Failed installing components
```

<span data-ttu-id="7b88f-220">이 시점에서 클릭할 수 있습니다 안전 하 게 합니다 **완료** 차례로 합니다 **적용** 및 **확인**합니다.</span><span class="sxs-lookup"><span data-stu-id="7b88f-220">At this point you can safely click on the **Finish** and then the **Apply** and **OK**.</span></span>

<span data-ttu-id="7b88f-221">이 형식이 잘못 된 결과 로그를 일으키는 경합 형성 된 심각 하지 않은 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="7b88f-221">This is a benign error formed by a race condition causing a result log to be malformed.</span></span> <span data-ttu-id="7b88f-222">이 다음 영역에서 로그 파일을 보면 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b88f-222">This can be verified by looking at the log file in the following area:</span></span>

1. <span data-ttu-id="7b88f-223">장치 화면의 같이 장치의 IP에 대 한 FTP 연결을 엽니다는 `Data/test/bin/DriverTest/Run` 디렉터리입니다.</span><span class="sxs-lookup"><span data-stu-id="7b88f-223">Open an FTP connection to the IP of the device (as shown on the device screen) to the `Data/test/bin/DriverTest/Run` directory.</span></span>
<span data-ttu-id="7b88f-224">예:</span><span class="sxs-lookup"><span data-stu-id="7b88f-224">e.g.</span></span>
`ftp://<ip address of device>/Data/test/bin/DriverTest/Run/`

2. <span data-ttu-id="7b88f-225">복사를 `Configuring_computer_settings_(possible_reboot)_identifier.wtl` 로컬 컴퓨터에는 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="7b88f-225">copy the `Configuring_computer_settings_(possible_reboot)_identifier.wtl` file to your local machine.</span></span>  <span data-ttu-id="7b88f-226">실패 한 작업의 이름과 일치 하는 로그 파일 이름에 있는 참고 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b88f-226">Note that the log file name matches the name of the failing task.</span></span>
3. <span data-ttu-id="7b88f-227">메모장에서 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="7b88f-227">Open the file in notepad</span></span>
4. <span data-ttu-id="7b88f-228">로그의 아래쪽으로 스크롤하십시오.</span><span class="sxs-lookup"><span data-stu-id="7b88f-228">Scroll to the bottom of the log.</span></span>  <span data-ttu-id="7b88f-229">다음 텍스트를 표시 됩니다, 프로 비전 성공적 임을 나타내는입니다.</span><span class="sxs-lookup"><span data-stu-id="7b88f-229">The following text will be present, indicating that the provisioning is successful.</span></span>

```
<PFRollup 
    Total="1" 
    Passed="1" 
    Failed="0" 
    Blocked="0" 
    Warned="0" 
    Skipped="0" CA="6191559" LA="6191619" >
    <rti id="2109770915" />
    <ctx id="384048256" />
</PFRollup>
</WTT-Logger>
```

