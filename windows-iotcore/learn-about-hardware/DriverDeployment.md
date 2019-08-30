---
title: 드라이버 배포
author: parameshbabu
ms.author: pabab
ms.date: 08/22/2017
ms.topic: article
description: Visual Studio를 사용 하 여 드라이버를 빌드하고 배포 하는 방법을 알아봅니다.
keywords: windows 10 IoT Core, 드라이버 배포
ms.openlocfilehash: aad50718ea44c46d676509fe2c5b408d471afc19
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "60169863"
---
# <a name="driver-deployment"></a><span data-ttu-id="1a58a-104">드라이버 배포</span><span class="sxs-lookup"><span data-stu-id="1a58a-104">Driver deployment</span></span>

<span data-ttu-id="1a58a-105">Visual Studio를 사용 하 여 Windows 10 IoT Core에 드라이버를 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-105">Deploy a driver on Windows 10 IoT Core with Visual Studio.</span></span> 

<span data-ttu-id="1a58a-106">드라이버 개발 단계에서 특정 플랫폼용 드라이버를 컴파일 및 배포할 수 있도록 Visual Studio 드라이버 프로젝트를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-106">Configure your Visual Studio driver project so that you can compile and deploy a driver for a specific platform during driver development phase.</span></span> 

<span data-ttu-id="1a58a-107">이 연습에서는 [gpiokmdfdemo 샘플 드라이버](https://github.com/ms-iot/samples/tree/develop/DriverSamples)를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-107">For this exercise you can use the [gpiokmdfdemo sample driver](https://github.com/ms-iot/samples/tree/develop/DriverSamples).</span></span>

<span data-ttu-id="1a58a-108">이미지에 드라이버를 추가 하려는 경우 [IoT 제조 가이드](https://docs.microsoft.com/windows-hardware/manufacture/iot/add-a-driver-to-an-image)의 지침을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1a58a-108">If you're looking to add a driver to an image, please visit the instructions in our [IoT Manufacturing Guide](https://docs.microsoft.com/windows-hardware/manufacture/iot/add-a-driver-to-an-image).</span></span>

## <a name="step-1--setup"></a><span data-ttu-id="1a58a-109">1 단계: 설정</span><span class="sxs-lookup"><span data-stu-id="1a58a-109">Step 1 : Setup</span></span> 
___

### <a name="on-the-device"></a><span data-ttu-id="1a58a-110">장치에서</span><span class="sxs-lookup"><span data-stu-id="1a58a-110">On the device</span></span>

* <span data-ttu-id="1a58a-111">[시작 지침](https://go.microsoft.com/fwlink/?linkid=860461)에 따라 장치에 설치 된 IoTCore 이미지가 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-111">Make sure that your device has an IoTCore image installed by following the [Get Started instructions](https://go.microsoft.com/fwlink/?linkid=860461).</span></span>
* <span data-ttu-id="1a58a-112">[Powershell](../connect-your-device/PowerShell.md)을 통해 장치에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-112">Connect to your device via [Powershell](../connect-your-device/PowerShell.md).</span></span>

### <a name="on-the-pc"></a><span data-ttu-id="1a58a-113">PC에서</span><span class="sxs-lookup"><span data-stu-id="1a58a-113">On the PC</span></span>

* <span data-ttu-id="1a58a-114">Visual Studio 2017를 설치 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-114">Make sure you have installed Visual Studio 2017.</span></span>
* <span data-ttu-id="1a58a-115">[Windows 드라이버 키트](https://developer.microsoft.com/windows/hardware/windows-driver-kit)를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-115">Install the [Windows Driver Kit](https://developer.microsoft.com/windows/hardware/windows-driver-kit).</span></span>  <span data-ttu-id="1a58a-116">SDK 및 WDK를 설치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-116">You will need to install the SDK and WDK.</span></span>
* <span data-ttu-id="1a58a-117">드라이버가 올바르게 서명 되 고 장치에서 실행 될 수 있도록 인증서를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-117">Install the certificates so that the driver is signed correctly and can run on your device.</span></span> <span data-ttu-id="1a58a-118">관리자 권한 명령 프롬프트에서 아래 나열 된 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-118">From an elevated command prompt execute the commands listed below:</span></span>

    1.  `cd c:\Program Files (x86)\Windows Kits\10\Tools\bin\i386` 
    2.  `set WPDKContentRoot=c:\Program Files (x86)\Windows Kits\10`
    3.  `InstallOEMCerts.cmd`
  
* <span data-ttu-id="1a58a-119">수정 사항을 적용 하 여 VS에서 F5 배포를 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-119">Apply fix to enable F5 deployment from VS.</span></span> <span data-ttu-id="1a58a-120">관리자 권한 명령 프롬프트에서 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-120">In the elevated command prompt, execute the following commands:</span></span>

    1.  <span data-ttu-id="1a58a-121">`cd %TEMP%`(디렉터리를로 `c:\users\<usernsme>\Appdata\Local\Temp`변경 합니다.)</span><span class="sxs-lookup"><span data-stu-id="1a58a-121">`cd %TEMP%` ( will change directory to `c:\users\<usernsme>\Appdata\Local\Temp`)</span></span>
    2.  <span data-ttu-id="1a58a-122">`md “WdkTempFiles”`"WdkTempFiles" 디렉터리 수동 만들기 도구에서 버그에 대 한 해결 방법 이며 PC에서 *한 번만* 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-122">`md “WdkTempFiles”` Manually create a “WdkTempFiles” directory This is a workaround for a bug in the tooling and requires to be done *only once* in the PC.</span></span>


## <a name="step-2--provision-device-with-visual-studio"></a><span data-ttu-id="1a58a-123">2 단계: Visual Studio를 사용 하 여 장치 프로 비전</span><span class="sxs-lookup"><span data-stu-id="1a58a-123">Step 2 : Provision device with Visual Studio</span></span> 
___
* <span data-ttu-id="1a58a-124">Visual Studio를 열고 **드라이버 > 테스트 > 장치 구성을 선택 하 > 새 장치를 추가** 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-124">Open Visual Studio and select **Driver > Test > Configure Devices > Add New Device**</span></span>
    * <span data-ttu-id="1a58a-125">드라이버 메뉴 옵션이 표시 되지 않으면 SDK가 설치 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-125">If the Driver Menu option is not shown, check if SDK is installed.</span></span>

* <span data-ttu-id="1a58a-126">**장치 구성** 대화 상자에서</span><span class="sxs-lookup"><span data-stu-id="1a58a-126">In the **Device Configuration** dialog,</span></span> 
    * <span data-ttu-id="1a58a-127">대상 장치의 사용자에 게 친숙 한 표시 이름 입력</span><span class="sxs-lookup"><span data-stu-id="1a58a-127">Enter a user friendly Display Name for your target device</span></span>
    * <span data-ttu-id="1a58a-128">장치 유형 = 모바일 선택</span><span class="sxs-lookup"><span data-stu-id="1a58a-128">Select Device Type = Mobile</span></span>
    * <span data-ttu-id="1a58a-129">표시 된 목록에서 IP 주소를 기준으로 정렬 하 고 IoT 장치의 주소를 찾은 다음 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-129">In the list displayed, sort by IP address, and find the address for the IoT device and select.</span></span> <span data-ttu-id="1a58a-130">두 개의 항목이 있는 경우 0이 아닌 GUID를 가진 항목을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-130">If there are two entries, select the one with the non-zero GUID.</span></span>  <span data-ttu-id="1a58a-131">행이 선택 되어 있는지 확인 합니다. 파란색을 강조 표시 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-131">Make sure the row is selected – it should highlight blue</span></span>
    * <span data-ttu-id="1a58a-132">대화 상자 아래쪽에 두 개의 라디오 단추가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-132">At the bottom of the dialog are two radio buttons.</span></span>  <span data-ttu-id="1a58a-133">장치 프로 비전을 표시 하는 항목을 선택 **하 고 디버거 설정을 선택**합니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-133">Select the one which says **Provision device and choose debugger settings**.</span></span>  <span data-ttu-id="1a58a-134">**다음** 선택</span><span class="sxs-lookup"><span data-stu-id="1a58a-134">Select **Next**</span></span>

* <span data-ttu-id="1a58a-135">**디버거 설정 구성**에서 적절 한 설정을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-135">On the **Configure debugger settings**, set the appropriate settings.</span></span>  <span data-ttu-id="1a58a-136">다음에 유의하세요.</span><span class="sxs-lookup"><span data-stu-id="1a58a-136">Note the following:</span></span>
   * <span data-ttu-id="1a58a-137">MinnowBoardMax는 디버깅에 네트워크를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-137">The MinnowBoardMax can use the network for debugging.</span></span>
       * <span data-ttu-id="1a58a-138">**네트워크** 연결 유형 사용</span><span class="sxs-lookup"><span data-stu-id="1a58a-138">Use connection type **Network**</span></span>
       * <span data-ttu-id="1a58a-139">포트 선택 – 기본값 사용 가능</span><span class="sxs-lookup"><span data-stu-id="1a58a-139">Select some port – default can be used</span></span>
       * <span data-ttu-id="1a58a-140">일부 키 선택 – 기본값을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-140">Select some key – default can be used</span></span>
       * <span data-ttu-id="1a58a-141">Visual studio를 실행 하는 컴퓨터의 호스트 IP를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-141">Select the host IP of the machine running visual studio.</span></span>  <span data-ttu-id="1a58a-142">Autonet (169.xxx) 주소를 사용 하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="1a58a-142">Do not use the autonet (169.xxx) address.</span></span>
       * <span data-ttu-id="1a58a-143">**다음** 선택</span><span class="sxs-lookup"><span data-stu-id="1a58a-143">Select **Next**</span></span>
       
  ![디버그 설정 구성](../media/DriverDeployment/confdbgsettings.png)
       
    * <span data-ttu-id="1a58a-145">Raspberry Pi는 커널 디버깅에 직렬를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-145">The Raspberry Pi uses serial for kernel debugging.</span></span>
       *  <span data-ttu-id="1a58a-146">적절 한 직렬 디버깅 케이블을 PI와 호스트 컴퓨터에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-146">Connect the appropriate serial debugging cable to the PI and the host machine</span></span>
       *  <span data-ttu-id="1a58a-147">연결 형식에 대 한 **직렬** 선택</span><span class="sxs-lookup"><span data-stu-id="1a58a-147">Select **Serial** for the connection type</span></span>
       *  <span data-ttu-id="1a58a-148">Raspberry Pi에 적절 한 나머지 매개 변수를 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-148">Fill out the rest of the parameters as appropriate for the Raspberry Pi.</span></span>
       *  <span data-ttu-id="1a58a-149">**다음** 선택</span><span class="sxs-lookup"><span data-stu-id="1a58a-149">Select **Next**</span></span>

* <span data-ttu-id="1a58a-150">VS를 통해 WDK가 IoT 장치를 프로 비전 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-150">The WDK, through VS, will now provision the IoT device.</span></span>  <span data-ttu-id="1a58a-151">TAEF 및 WDTF가 장치에 설치 되 고, 위에 제공 된 설정에 따라 장치가 커널 디버깅에 대해 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-151">TAEF and WDTF will be installed on the device, and the device will be set up for kernel debugging per the settings provided above.</span></span>

* <span data-ttu-id="1a58a-152">완료 되 면 장치를 다시 부팅할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-152">When complete, the device may reboot.</span></span>  <span data-ttu-id="1a58a-153">**장치 구성** 의 진행률 화면은 상태를 제공 하 고 IoT 장치에서 설치를 완료 하면 완료 된 것을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-153">The progress screen on the **Device Configuration** will provide status, and shows complete when the IoT device has completed the installation.</span></span> <span data-ttu-id="1a58a-154">**마침**을 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-154">Press **Finish**.</span></span>

![진행률 구성](../media/DriverDeployment/confprogress.png)

* <span data-ttu-id="1a58a-156">이제 장치가 프로 비전 되 고 **장치 테스트 구성** 상태에 **드라이버 테스트를 위해 구성** 됨이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-156">The device is now provisioned and the **Device test configuration** status shows **Configured for driver testing**</span></span>

![ConfigureDevices](../media/DriverDeployment/ConfigureDevices.png)

## <a name="step-3--configure-visual-studio-driver-project"></a><span data-ttu-id="1a58a-158">3 단계: Visual Studio 드라이버 프로젝트 구성</span><span class="sxs-lookup"><span data-stu-id="1a58a-158">Step 3 : Configure Visual Studio driver project</span></span>
___    
1. <span data-ttu-id="1a58a-159">관리자 모드에서 Visual Studio를 시작 하 고 visual studio 드라이버 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-159">Launch Visual Studio in the administrator mode and open the visual studio driver project.</span></span>
2. <span data-ttu-id="1a58a-160">대상 플랫폼 버전이 개발 컴퓨터에 설치 된 SDK와 일치 하는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-160">Make sure the Target Platform Version matches the SDK installed on your development machine.</span></span> <span data-ttu-id="1a58a-161">솔루션 탐색기 창에서 프로젝트 속성을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-161">Select Project Properties from the Solution Explorer window.</span></span>  <span data-ttu-id="1a58a-162">일반 구성 속성에서 대상 플랫폼 버전이 개발 컴퓨터에 설치 된 SDK와 일치 하는지 보장 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-162">Under General Configuration Properties assure that the Target Platform Version matches the SDK installed on your development computer.</span></span>  <span data-ttu-id="1a58a-163">제어판의 프로그램 **및 기능 > >** SDK 버전을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-163">You can check the version of the SDK from the **Control Panel > Programs > Programs and Features**.</span></span>
3. <span data-ttu-id="1a58a-164">**Project > Visual C++ > Windows 드라이버 > 새 항목 추가**에서 **패키지 매니페스트** 를 선택 하 고 **추가**를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-164">Under **Project > Add New Item > Visual C++ > Windows Driver**, select **Package Manifest** and Press **Add**.</span></span>

![PackageManifest](../media/DriverDeployment/PackageManifest.png)

 <span data-ttu-id="1a58a-166">`Package.pkg.xml`파일이 프로젝트에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-166">`Package.pkg.xml` file will be added to the project.</span></span> <span data-ttu-id="1a58a-167">이 파일에서 소유자, 플랫폼, 구성 요소 및 하위 구성 요소 태그를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-167">In this file, specify the Owner, Platform, Component and SubComponent tags.</span></span> 
 
![Pkg-xml](../media/DriverDeployment/Package-pkg-xml.png)
 
4. <span data-ttu-id="1a58a-169">프로젝트 속성에서 패키지 버전 번호를 Set **> PackageGen > 버전**으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-169">Set package version number at **Project Properties > PackageGen > Version**.</span></span> <span data-ttu-id="1a58a-170">드라이버의 설치/다시 설치를 수행 해야 할 때마다이 버전 번호를 증가 시켜야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-170">Note that every time you need to perform a Install/Reinstall of the driver, this version number has to be incremented.</span></span>

![PackageVersion](../media/DriverDeployment/PackageVersion.png)

5. <span data-ttu-id="1a58a-172">**프로젝트 속성 > 드라이버 서명 > 테스트 인증서**에서 테스트 인증서 (Phone OEM 테스트 인증서)를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-172">Under **Project Properties > Driver Signing > Test Certificate**, select test certificate (Phone OEM Test Certificate)</span></span>

![DriverSigning](../media/DriverDeployment/DriverTestSigning.png)

6. <span data-ttu-id="1a58a-174">**드라이버 설치** 로 이동 하 여 **배포** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-174">Go to **Driver Install** and select **Deployment**</span></span>

![InstallOptions](../media/DriverDeployment/installOptions.png)

* <span data-ttu-id="1a58a-176">**대상 장치 이름** 드롭다운에서 프로 비전 프로세스에서 위에서 만든 대상을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-176">From the **Target Device Name** dropdown, select the target created above in the provisioning process.</span></span> <span data-ttu-id="1a58a-177">**설치/다시** 설치 및 **빠른 다시 설치**에 대 한 두 가지 옵션을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-177">Notice the two options for **Install / Reinstall** and **Fast Reinstall**.</span></span> <span data-ttu-id="1a58a-178">옵션을 선택 하 고 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-178">Choose an option and Click **Ok**.</span></span>
* <span data-ttu-id="1a58a-179">**설치/다시 설치** 는 대상에 드라이버를 처음 설치 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-179">**Install / Reinstall** is used for the initial installation of a driver to the target.</span></span>  <span data-ttu-id="1a58a-180">Windows 업데이트 스택을 사용 하 여 드라이버 패키지를 설치 하 고 몇 분 정도 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-180">This installs the driver package using the Windows update stack and can take several minutes.</span></span> <span data-ttu-id="1a58a-181">이는 INF 파일이 변경 될 때마다 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-181">This must be used every time the INF file is changed.</span></span> 
    
> [!TIP]
> <span data-ttu-id="1a58a-182">초기 설치 후에이 옵션을 사용 하 여 드라이버를 설치할 때마다 패키지 버전 번호가 증가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-182">Every time this option is used to install a driver after the initial installation, the package version number must be incremented.</span></span>

* <span data-ttu-id="1a58a-183">**빠른 다시 설치** 는 드라이버를 설치한 후에 사용할 수 있으며 레지스트리에 영향을 주는 드라이버 INF 파일에 대 한 이후 변경 내용이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-183">**Fast Reinstall** can be used once a driver has been installed, and there are no subsequent changes to the drivers INF file which affect the registry.</span></span>  <span data-ttu-id="1a58a-184">이 메서드는 설치 프로세스를 건너뛰고, 드라이버와 연결 된 모든 devnodes를 종료 하 고, 드라이버를에 복사 하 고, devnode를 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-184">This method bypasses the install process, shuts down all devnodes associated with the driver, copies the driver over, and restarts the devnode.</span></span>  <span data-ttu-id="1a58a-185">몇 초 (< 20 초)가 소요 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-185">This takes a few (<20) seconds.</span></span>

    
> [!WARNING]
> <span data-ttu-id="1a58a-186">이 방법이 반드시 성공 하는 것은 아닙니다. 어떤 이유로 드라이버를 devnode 종료할 수 없는 경우 작업은 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-186">This method is not guaranteed to succeed – If for some reason a devnode cannot be shutdown to release the driver, the operation will fail.</span></span>  <span data-ttu-id="1a58a-187">이는 잘못 된 하드웨어 또는 초기에 잘못 된 드라이버 구현이 원인일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-187">This can be due to faulty hardware, or an initial faulty implementation of the driver.</span></span>  <span data-ttu-id="1a58a-188">이 경우 설치/다시 설치 옵션을 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-188">The Install/Reinstall option must be used in this case.</span></span>


<span data-ttu-id="1a58a-189">이제 Visual Studio 프로젝트가 대상 장치에 드라이버를 빌드하고 배포할 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-189">Your Visual Studio project is now ready to build and deploy a driver to your target device.</span></span> <span data-ttu-id="1a58a-190">샘플 gpiokmdfdemo 드라이버를 사용 하는 경우 ACPI 테이블을 생성 하 고 대상 장치에 복사한 다음 [Visual Studio에서 드라이버 빌드](https://developer.microsoft.com/en-us/windows/iot/samples/driverlab2)의 단계를 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-190">If you are using the sample gpiokmdfdemo driver you need to generate ACPI table and copy to your target device, then follow the steps in [building the driver in Visual Studio](https://developer.microsoft.com/en-us/windows/iot/samples/driverlab2).</span></span>


## <a name="step-4--build-and-deploy-driver"></a><span data-ttu-id="1a58a-191">4 단계: 드라이버 빌드 및 배포</span><span class="sxs-lookup"><span data-stu-id="1a58a-191">Step 4 : Build and deploy driver</span></span>
___
<span data-ttu-id="1a58a-192">이 작업은 **F5** 키를 사용 하 고 **배포** 옵션을 사용 하 여 두 가지 방법으로 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-192">This can be done in two ways, using the **F5** key and using the **Deploy** option.</span></span> <span data-ttu-id="1a58a-193">두 가지 방법으로 드라이버를 빌드하고 배포 (즉, 장치에 설치) 하 고, F5 키를 눌러 Visual Studio 커널 디버거를 설치 되 고 로드 된 드라이버에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-193">In both ways, the driver will be built and deployed (i.e. installs it on device) and the F5 attaches the Visual Studio kernel debugger to the installed and loaded driver.</span></span> 

<span data-ttu-id="1a58a-194">일부 사용자는 **배포** 기능을 사용 하 고 다른 커널 디버거 (예: WINDBG 또는 KD)를 연결 하는 것을 선호 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-194">Some users prefer to use the **Deploy** functionality and attach a different kernel debugger, such as WinDBG or KD.</span></span>  <span data-ttu-id="1a58a-195">이를 통해 VS 디버거를 사용 하는 것 보다 더 많은 유연성을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-195">This can provide more flexibility than using the VS debugger.</span></span>

### <a name="deploy"></a><span data-ttu-id="1a58a-196">배포</span><span class="sxs-lookup"><span data-stu-id="1a58a-196">Deploy</span></span>
1.  <span data-ttu-id="1a58a-197">솔루션 탐색기에서 프로젝트를 마우스 오른쪽 단추로 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-197">Right-click on the project in the solution explorer</span></span>
2.  <span data-ttu-id="1a58a-198">**배포** 선택</span><span class="sxs-lookup"><span data-stu-id="1a58a-198">Select **Deploy**</span></span>

![배포](../media/DriverDeployment/deploy.png) 

3.  <span data-ttu-id="1a58a-200">배포 프로세스를 진행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-200">The deployment process should proceed.</span></span>  <span data-ttu-id="1a58a-201">IoT 장치는 배포 후 다시 부팅 되 고 설치가 진행 되는 동안 "기어" 화면을 표시 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-201">The IoT device will be rebooted after deployment, and should show the “Gears” screen while installation is taking place.</span></span>

<span data-ttu-id="1a58a-202">빌드 출력이 출력 창에 표시 됩니다. 배포 상태는 설치가 완료 되 면 장치는 다시 부팅 되 고 VS 출력 화면에는 성공 또는 실패가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-202">Build output is in the **Output** Window Deployment status is also in the output window When Installation completes, the device will reboot again, and the VS Output screen will indicate success or failure.</span></span>

### <a name="f5"></a><span data-ttu-id="1a58a-203">F5</span><span class="sxs-lookup"><span data-stu-id="1a58a-203">F5</span></span>

1.  <span data-ttu-id="1a58a-204">빌드 창에서 구성이 올바른지 확인 합니다. 현재 빌드 아치는 대상 장치 아치와 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-204">From the build window, make sure that the configurations are correct – the current build arch is the same as the target device arch.</span></span>  <span data-ttu-id="1a58a-205">여기서는 대상 이름의 아치가 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-205">This is where having the arch in the target name is valuable.</span></span>  <span data-ttu-id="1a58a-206">대상은 메뉴 모음의 보기 상자에 표시 되며, 오른쪽 위를 중심으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-206">The target will be displayed in the view box on the menu bar in VS on the top-middle-right.</span></span>
2.  <span data-ttu-id="1a58a-207">**F5**키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-207">Press **F5**.</span></span>  <span data-ttu-id="1a58a-208">대상이 빌드, 배포 및 VS Kernel 디버거에 연결 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-208">The target will be built, deployed, and attached to the VS Kernel Debugger.</span></span>

* <span data-ttu-id="1a58a-209">다시 부팅 한 후 powershell이 아직 연결 되어 있는지 확인 하 고, 그렇지 않은 경우 powershell `enter-pssession` 명령을 사용 하 여 대상 장치에 다시 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-209">After the reboot, make sure PowerShell is still connected to it, otherwise, re-connect to the target device using the PowerShell `enter-pssession` command..</span></span>


## <a name="known-issues"></a><span data-ttu-id="1a58a-210">알려진 문제</span><span class="sxs-lookup"><span data-stu-id="1a58a-210">Known Issues</span></span>
___

### <a name="provisioning-errors"></a><span data-ttu-id="1a58a-211">프로 비전 오류</span><span class="sxs-lookup"><span data-stu-id="1a58a-211">Provisioning Errors</span></span>
<span data-ttu-id="1a58a-212">MinnowBoardMax와 상호 작용 하는 동안의 경합 상태는 프로 비전 중에 보고 된 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-212">A race condition during the interaction with MinnowBoardMax can result in a reported failure during provisioning.</span></span>  <span data-ttu-id="1a58a-213">실제로 프로 비전은 성공 가능성이 높습니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-213">In fact, the provisioning most likely succeeded.</span></span>

<span data-ttu-id="1a58a-214">**오류 목록:**</span><span class="sxs-lookup"><span data-stu-id="1a58a-214">**List of Errors:**</span></span>
 
* <span data-ttu-id="1a58a-215">오류: "WDTF를 등록 하는 중" 작업을 완료 하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-215">ERROR: Task "Registering WDTF" failed to complete successfully.</span></span>
* <span data-ttu-id="1a58a-216">오류: "커널 디버거 설정 구성 (다시 부팅 가능)" 작업을 성공적으로 완료 하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-216">ERROR: Task "Configuring kernel debugger settings (possible reboot)" failed to complete successfully</span></span>

<span data-ttu-id="1a58a-217">**해결 방법:** 이러한 오류는 거의 무시 해도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-217">**Workaround:** These error can almost certainly be ignored.</span></span>

<span data-ttu-id="1a58a-218">**대해**</span><span class="sxs-lookup"><span data-stu-id="1a58a-218">**Details:**</span></span>

<span data-ttu-id="1a58a-219">**장치 구성 구성 진행률** 대화 상자에 표시 되는 오류는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-219">The following error will be displayed in the **Device Configuration Configuration Progress** dialog:</span></span>

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

<span data-ttu-id="1a58a-220">이 시점에서 **완료** 를 안전 하 게 클릭 한 다음 **적용** 및 **확인**을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-220">At this point you can safely click on the **Finish** and then the **Apply** and **OK**.</span></span>

<span data-ttu-id="1a58a-221">이는 결과 로그의 형식이 잘못 되는 경합 상태에서 형성 되는 무해 한 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-221">This is a benign error formed by a race condition causing a result log to be malformed.</span></span> <span data-ttu-id="1a58a-222">이는 다음 영역에 있는 로그 파일을 확인 하 여 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-222">This can be verified by looking at the log file in the following area:</span></span>

1. <span data-ttu-id="1a58a-223">장치 화면에 표시 된 대로 장치의 IP에 대 한 FTP 연결을 `Data/test/bin/DriverTest/Run` 디렉터리에 엽니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-223">Open an FTP connection to the IP of the device (as shown on the device screen) to the `Data/test/bin/DriverTest/Run` directory.</span></span>
<span data-ttu-id="1a58a-224">예: `ftp://<ip address of device>/Data/test/bin/DriverTest/Run/`</span><span class="sxs-lookup"><span data-stu-id="1a58a-224">e.g. `ftp://<ip address of device>/Data/test/bin/DriverTest/Run/`</span></span>

2. <span data-ttu-id="1a58a-225">로컬 컴퓨터에 파일을 복사 합니다. `Configuring_computer_settings_(possible_reboot)_identifier.wtl`</span><span class="sxs-lookup"><span data-stu-id="1a58a-225">copy the `Configuring_computer_settings_(possible_reboot)_identifier.wtl` file to your local machine.</span></span>  <span data-ttu-id="1a58a-226">로그 파일 이름은 실패 한 작업의 이름과 일치 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-226">Note that the log file name matches the name of the failing task.</span></span>
3. <span data-ttu-id="1a58a-227">메모장에서 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-227">Open the file in notepad</span></span>
4. <span data-ttu-id="1a58a-228">로그의 아래쪽으로 스크롤합니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-228">Scroll to the bottom of the log.</span></span>  <span data-ttu-id="1a58a-229">프로 비전이 성공 했음을 나타내는 다음 텍스트가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1a58a-229">The following text will be present, indicating that the provisioning is successful.</span></span>

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

