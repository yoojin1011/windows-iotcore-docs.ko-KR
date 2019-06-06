---
title: IoT Core 장치에 앱 설치
author: parameshbabu
ms.author: pabab
ms.date: 08/28/2017
ms.topic: article
description: Windows Device Portal 사용 하 여 앱을 설치 하는 방법을 알아봅니다 또는 IoT의 일환으로 이미지를 핵심입니다.
keywords: windows iot, 앱 설치, Windows Device Portal 장치
ms.openlocfilehash: 23df6bec04395eb31f066eb3befc84a4ff4bbe56
ms.sourcegitcommit: 5a103405cbc5c61101139aff6aaa709bd4ef9582
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66694160"
---
# <a name="install-your-app-on-an-iot-core-device"></a><span data-ttu-id="ee29f-104">IoT Core 장치에 앱 설치</span><span class="sxs-lookup"><span data-stu-id="ee29f-104">Install your app on an IoT Core device</span></span>
<span data-ttu-id="ee29f-105">아래 나열 된 두 가지 방법 중 하나를 사용 하 여 앱을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ee29f-105">You can install your app using one of the two methods that are listed below.</span></span>

> [!NOTE]
> <span data-ttu-id="ee29f-106">Windows Device Portal 사용 하 여 앱을 설치 하는 것은 개발자 시나리오에 대해서만 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee29f-106">Installing apps using the Windows Device Portal is only for developer scenarios.</span></span>
> <span data-ttu-id="ee29f-107">프로 비전 패키지를 만들거나 프로덕션 시나리오에 대 한 Windows IoT Core 이미지에 앱을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee29f-107">Please create a provisioning package or add the app to your Windows IoT Core image for production scenarios.</span></span>

## <a name="using-windows-device-portal"></a><span data-ttu-id="ee29f-108">Windows Device Portal 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="ee29f-108">Using Windows Device Portal</span></span>

> [!NOTE]
> <span data-ttu-id="ee29f-109">.appx 또는.appxbundle Windows Device Portal 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee29f-109">An .appx or .appxbundle is required for Windows Device Portal.</span></span> <span data-ttu-id="ee29f-110">최소 버전 응용 프로그램 프로젝트의 대상으로 하는 경우 버전의 SDK 및 도구 17763부터 > 17763 크거나 도구 만듭니다는 [.msix 또는.msixbundle](https://developercommunity.visualstudio.com/content/problem/391934/makeappx-now-creates-msix-files-instead-of-appx.html)합니다.</span><span class="sxs-lookup"><span data-stu-id="ee29f-110">Beginning with version 17763 of the SDK and tools if the minimum target version of the app project> is 17763 or greater the tools will create an [.msix or .msixbundle](https://developercommunity.visualstudio.com/content/problem/391934/makeappx-now-creates-msix-files-instead-of-appx.html).</span></span>
> <span data-ttu-id="ee29f-111">.Appx 또는.appxbundle 집합 17763 보다 이전 버전이 최소 버전을 만들려면 또는 [makeappx.exe를 직접 실행](https://docs.microsoft.com/en-us/windows/desktop/appxpkg/make-appx-package--makeappx-exe-#command-line-syntax)합니다.</span><span class="sxs-lookup"><span data-stu-id="ee29f-111">To create an .appx or .appxbundle set the minimum version to a version less than 17763 or [run makeappx.exe directly](https://docs.microsoft.com/en-us/windows/desktop/appxpkg/make-appx-package--makeappx-exe-#command-line-syntax).</span></span> <span data-ttu-id="ee29f-112">.msix.appx,.appxbundle를.msixbundle에 이름을 바꿀 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ee29f-112">It may also be possible to rename the .msix to .appx, or .msixbundle to .appxbundle.</span></span>

<span data-ttu-id="ee29f-113">이 방법에서는 인터넷에 연결 되어 있는지 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee29f-113">For this method, you will need to ensure that you are connected to the internet.</span></span> <span data-ttu-id="ee29f-114">인터넷에 액세스할 수 없는 경우 장치 및 공개 인터넷 액세스에 대 한 경로 포함 하지 않는 클라이언트 컴퓨터 간의 피어-투-피어 이더넷 연결을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ee29f-114">If you do not have access to the internet, you can also have a peer-to-peer ethernet connection between the device and a client machine that doesn't include a path to access the open internet.</span></span> <span data-ttu-id="ee29f-115">두 번째 방법에 대 한 지속적인이 앱을 설치 하지만 앱 스토어 로그인이 시작 되지 것입니다.</span><span class="sxs-lookup"><span data-stu-id="ee29f-115">However, going about the latter way will install the app but will fail to launch if the app is store-signed.</span></span>

<span data-ttu-id="ee29f-116">설치 하려면 장치에서 응용 프로그램 다음을 수행 하십시오.</span><span class="sxs-lookup"><span data-stu-id="ee29f-116">To install your application on the device please do the following:</span></span>

1. <span data-ttu-id="ee29f-117">엽니다는 [Windows Device Portal](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal) IoT 장치에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee29f-117">Open the [Windows Device Portal](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal) for your IoT device.</span></span>

2. <span data-ttu-id="ee29f-118">에 **앱** 메뉴에서 앱 파일을 선택 하 고 클릭 하 여 앱을 설치할 **설치**합니다.</span><span class="sxs-lookup"><span data-stu-id="ee29f-118">In the **Apps** menu, install your app by selecting your app files and clicking **Install**.</span></span>

3. <span data-ttu-id="ee29f-119">클릭 **파일 선택**</span><span class="sxs-lookup"><span data-stu-id="ee29f-119">Click **Select File**</span></span>

4. <span data-ttu-id="ee29f-120">.Appx 파일을 선택 하 고 클릭 **열기**</span><span class="sxs-lookup"><span data-stu-id="ee29f-120">Select your .appx file and click **Open**</span></span>

5. <span data-ttu-id="ee29f-121">확인 **나 프레임 워크 패키지를 선택할 수 있음**</span><span class="sxs-lookup"><span data-stu-id="ee29f-121">Check **Allow me to select framework packages**</span></span>

6. <span data-ttu-id="ee29f-122">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ee29f-122">Click **Next**</span></span>

7. <span data-ttu-id="ee29f-123">각 항목에는 **종속성** 7.1 및 7.2에.appx 반복 단계에 대 한 폴더</span><span class="sxs-lookup"><span data-stu-id="ee29f-123">For each item in the **Dependencies** folder for your .appx repeat step 7.1 and 7.2</span></span>

    <span data-ttu-id="ee29f-124">7.1 클릭 **파일 선택**</span><span class="sxs-lookup"><span data-stu-id="ee29f-124">7.1 Click **Choose File**</span></span>

    <span data-ttu-id="ee29f-125">7.2 depenency.appx를 선택 하 고 클릭 **열기**</span><span class="sxs-lookup"><span data-stu-id="ee29f-125">7.2 Select the depenency .appx and click **Open**</span></span>

8. <span data-ttu-id="ee29f-126">모든 종속성 클릭 추가 될 때 **설치**</span><span class="sxs-lookup"><span data-stu-id="ee29f-126">When all of the dependencies are added click **Install**</span></span>

9. <span data-ttu-id="ee29f-127">설치가 완료 될 대기 하 고 클릭 **수행**</span><span class="sxs-lookup"><span data-stu-id="ee29f-127">Wait for the install is completed and click **Done**</span></span>

 ![앱 설치](../media/AppInstaller/install-app.gif)

10. <span data-ttu-id="ee29f-129">이제 응용 프로그램 장치에서 응용 프로그램 목록에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ee29f-129">The application will now be visible on the list of applications on your device.</span></span>
 <span data-ttu-id="ee29f-130">![앱 설치](../media/AppInstaller/install-app.gif)</span><span class="sxs-lookup"><span data-stu-id="ee29f-130">![Install App](../media/AppInstaller/install-app.gif)</span></span>


## <a name="using-provisioning-package-from-wcd"></a><span data-ttu-id="ee29f-131">WCD에서 프로 비전 패키지를 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="ee29f-131">Using provisioning package from WCD</span></span>
<span data-ttu-id="ee29f-132">앱을 사용 하 여 프로 비전 패키지를 만들고 장치의 프로 비전 패키지를 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ee29f-132">You can create a provisioning package with the app and install the provisioning package on the device.</span></span> <span data-ttu-id="ee29f-133">이 메서드는 인터넷에 연결 되지 않은 장치 에서도 작동 하며 저장소 라이선스 파일을 설치 하기 위한 방법이 더 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ee29f-133">This method works even on devices that do not have internet connection, and is the preferred method for installing the store license file.</span></span> <span data-ttu-id="ee29f-134">예를 들어 여기서는 장치가 인터넷에 연결 되어 있지 않지만 기본 앱은 스토어 로그인 UWP 앱 팩터리 시나리오 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee29f-134">For example, this enables factory scenarios where the device is not connected to the internet but the primary app is a store-signed UWP app.</span></span>

> [!NOTE]
> <span data-ttu-id="ee29f-135">패키지 제품군 이름 (PFN) 아래 Windows 개발자 센터에서 찾을 수 있습니다 **앱 관리 > 앱 Id**</span><span class="sxs-lookup"><span data-stu-id="ee29f-135">The Package Family Name (PFN) can be found in the Windows Dev Center under **App Management > App Identity**</span></span>

1. <span data-ttu-id="ee29f-136">열기 [Windows 구성 디자이너 (WICD)](https://docs.microsoft.com/windows/configuration/provisioning-packages/provisioning-install-icd)</span><span class="sxs-lookup"><span data-stu-id="ee29f-136">Open [Windows Configuration Designer (WICD)](https://docs.microsoft.com/windows/configuration/provisioning-packages/provisioning-install-icd)</span></span>

2. <span data-ttu-id="ee29f-137">선택 **프로 비전 고급**, 프로젝트 이름 및 설명을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee29f-137">Select **Advanced Provisioning**, Enter the project name and a description</span></span>

3. <span data-ttu-id="ee29f-138">프로젝트 설정에 대 한 Windows 10 IoT Core 선택 하 고 프로 비전 패키지 가져오기를 건너뛸합니다</span><span class="sxs-lookup"><span data-stu-id="ee29f-138">Choose Windows 10 IoT Core for the project settings and skip the provisioning package import</span></span>

4. <span data-ttu-id="ee29f-139">왼쪽 창에서 확장 **런타임 설정을** 클릭 하 고 **유니버설 앱 설치 > 사용자 상황에 맞는 앱**</span><span class="sxs-lookup"><span data-stu-id="ee29f-139">On the left hand side expand **Runtime Settings** and click on **Universal App Install > User Context App**</span></span>

5. <span data-ttu-id="ee29f-140">앱의 패키지 패밀리 이름을 입력 **추가**</span><span class="sxs-lookup"><span data-stu-id="ee29f-140">Enter the Package Family Name of your app and click **Add**</span></span>

6. <span data-ttu-id="ee29f-141">새로 추가 된 PFN 아래</span><span class="sxs-lookup"><span data-stu-id="ee29f-141">Under the newly added PFN</span></span>
    - <span data-ttu-id="ee29f-142">추가 된 Appx 및 해당 종속성</span><span class="sxs-lookup"><span data-stu-id="ee29f-142">add the Appx and its dependencies</span></span>
    - <span data-ttu-id="ee29f-143">"Force 대상 응용 프로그램 종료" DeploymentOptions 설정</span><span class="sxs-lookup"><span data-stu-id="ee29f-143">set the DeploymentOptions to "Force target application shutdown"</span></span>

7. <span data-ttu-id="ee29f-144">저장소 서명 앱에 대 한 라이선스를 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee29f-144">For Store signed apps, you will need to specify the license.</span></span> <span data-ttu-id="ee29f-145">UserContextAppLicense, 아래</span><span class="sxs-lookup"><span data-stu-id="ee29f-145">Under UserContextAppLicense,</span></span>
    - <span data-ttu-id="ee29f-146">LicenseProductID (라이선스 XML 파일에서 LicenseID로 제공)를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee29f-146">add LicenseProductID (available as LicenseID in the license XML file)</span></span>
    - <span data-ttu-id="ee29f-147">라이선스 xml 확장을 변경 *.ms-windows-저장소-라이선스*합니다.</span><span class="sxs-lookup"><span data-stu-id="ee29f-147">change the license xml extension to *.ms-windows-store-license*.</span></span>
    - <span data-ttu-id="ee29f-148">왼쪽 창에서 라이선스 제품 ID를 선택 하 고 LicenseInstall 필드에 할당할 라이선스 파일 찾아보기</span><span class="sxs-lookup"><span data-stu-id="ee29f-148">select your License Product ID on the left hand side and browse your license file to assign LicenseInstall field</span></span>

8. <span data-ttu-id="ee29f-149">서명 된 앱의 스토어 이외의 경우 app.cer로 파일을 추가 해야 **인증서 > RootCertificates**</span><span class="sxs-lookup"><span data-stu-id="ee29f-149">For non-store signed apps, you will need to add the app.cer file under **Certificates > RootCertificates**</span></span> 

9. <span data-ttu-id="ee29f-150">패키지 내보내기</span><span class="sxs-lookup"><span data-stu-id="ee29f-150">Export the package</span></span>

10. <span data-ttu-id="ee29f-151">내보낸된.ppkg 파일을 복사 _C:\Windows\Provisioning\Packages_ 사용 하 여 IoT 장치 [SSH](../connect-your-device/SSH.md) 하거나 [Powershell](../connect-your-device/powershell.md)) 하 고 다시 부팅 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee29f-151">Copy the exported .ppkg file to _C:\Windows\Provisioning\Packages_ on the IoT device using [SSH](../connect-your-device/SSH.md) or [Powershell](../connect-your-device/powershell.md)) and reboot.</span></span> <span data-ttu-id="ee29f-152">장치를 다시 부팅 하는 경우 프로 비전 패키지 처리 되 고 앱이 설치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ee29f-152">When the device reboots, the provisioning package is processed and the app is installed.</span></span>


## <a name="add-the-app-to-the-windows-iot-core-imageffu"></a><span data-ttu-id="ee29f-153">Windows IoT Core image(.ffu)에 앱 추가</span><span class="sxs-lookup"><span data-stu-id="ee29f-153">Add the app to the Windows IoT Core image(.ffu)</span></span>
<span data-ttu-id="ee29f-154">Windows IoT Core 이미지 자체의 일부가 되도록 앱을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ee29f-154">You can add the app to be part of the Windows IoT Core image itself.</span></span>
<span data-ttu-id="ee29f-155">이것은 자신의 장치에 앱을 설치 하는 Oem 위한 기본 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="ee29f-155">This is the preferred method for OEMs to install apps on their devices.</span></span>

<span data-ttu-id="ee29f-156">참조 하는 방법 [이미지에 앱 추가](https://docs.microsoft.com/windows-hardware/manufacture/iot/deploy-your-app-with-a-standard-board) 와 [샘플 앱 패키지](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Packages/Appx.IoTCoreDefaultApp)합니다.</span><span class="sxs-lookup"><span data-stu-id="ee29f-156">See how to [add an app to your image](https://docs.microsoft.com/windows-hardware/manufacture/iot/deploy-your-app-with-a-standard-board) and a [sample app package](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Packages/Appx.IoTCoreDefaultApp).</span></span>
