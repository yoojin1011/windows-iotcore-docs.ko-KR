---
title: IoT Core 장치에 앱 설치
author: parameshbabu
ms.author: pabab
ms.date: 08/28/2017
ms.topic: article
description: Windows 장치 포털을 사용 하거나 IoT core 이미지의 일부로 앱을 설치 하는 방법에 대해 알아봅니다.
keywords: windows iot, 앱 설치, Windows 장치 포털, 장치
ms.openlocfilehash: 23df6bec04395eb31f066eb3befc84a4ff4bbe56
ms.sourcegitcommit: 5a103405cbc5c61101139aff6aaa709bd4ef9582
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66694160"
---
# <a name="install-your-app-on-an-iot-core-device"></a><span data-ttu-id="ed2df-104">IoT Core 장치에 앱 설치</span><span class="sxs-lookup"><span data-stu-id="ed2df-104">Install your app on an IoT Core device</span></span>
<span data-ttu-id="ed2df-105">아래에 나열 된 두 가지 방법 중 하나를 사용 하 여 앱을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ed2df-105">You can install your app using one of the two methods that are listed below.</span></span>

> [!NOTE]
> <span data-ttu-id="ed2df-106">Windows 장치 포털을 사용 하 여 앱을 설치 하는 것은 개발자 시나리오에만 해당 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ed2df-106">Installing apps using the Windows Device Portal is only for developer scenarios.</span></span>
> <span data-ttu-id="ed2df-107">프로덕션 시나리오에 대 한 프로 비전 패키지를 만들거나 Windows IoT Core 이미지에 앱을 추가 하세요.</span><span class="sxs-lookup"><span data-stu-id="ed2df-107">Please create a provisioning package or add the app to your Windows IoT Core image for production scenarios.</span></span>

## <a name="using-windows-device-portal"></a><span data-ttu-id="ed2df-108">Windows 장치 포털 사용</span><span class="sxs-lookup"><span data-stu-id="ed2df-108">Using Windows Device Portal</span></span>

> [!NOTE]
> <span data-ttu-id="ed2df-109">Windows 장치 포털에는 .appx 또는 .appxbundle가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed2df-109">An .appx or .appxbundle is required for Windows Device Portal.</span></span> <span data-ttu-id="ed2df-110">SDK 및 도구의 버전 17763부터 응용 프로그램 > 프로젝트의 최소 대상 버전이 17763 이상인 경우 도구에서 [. msix 또는. a n x 번들](https://developercommunity.visualstudio.com/content/problem/391934/makeappx-now-creates-msix-files-instead-of-appx.html)을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ed2df-110">Beginning with version 17763 of the SDK and tools if the minimum target version of the app project> is 17763 or greater the tools will create an [.msix or .msixbundle](https://developercommunity.visualstudio.com/content/problem/391934/makeappx-now-creates-msix-files-instead-of-appx.html).</span></span>
> <span data-ttu-id="ed2df-111">.Appx 또는 .appxbundle를 만들려면 최소 버전을 17763 보다 작은 버전으로 설정 하거나 [makeappx .exe를 직접 실행](https://docs.microsoft.com/en-us/windows/desktop/appxpkg/make-appx-package--makeappx-exe-#command-line-syntax)합니다.</span><span class="sxs-lookup"><span data-stu-id="ed2df-111">To create an .appx or .appxbundle set the minimum version to a version less than 17763 or [run makeappx.exe directly](https://docs.microsoft.com/en-us/windows/desktop/appxpkg/make-appx-package--makeappx-exe-#command-line-syntax).</span></span> <span data-ttu-id="ed2df-112">또한. m 6에서 .appx 또는. m x x로 이름을 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ed2df-112">It may also be possible to rename the .msix to .appx, or .msixbundle to .appxbundle.</span></span>

<span data-ttu-id="ed2df-113">이 방법에서는 사용자가 인터넷에 연결 되어 있는지 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed2df-113">For this method, you will need to ensure that you are connected to the internet.</span></span> <span data-ttu-id="ed2df-114">인터넷에 액세스할 수 없는 경우 오픈 인터넷에 액세스 하는 경로를 포함 하지 않는 장치와 클라이언트 컴퓨터 간에 피어 투 피어 이더넷 연결을 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ed2df-114">If you do not have access to the internet, you can also have a peer-to-peer ethernet connection between the device and a client machine that doesn't include a path to access the open internet.</span></span> <span data-ttu-id="ed2df-115">그러나 후자의 방법으로 앱이 설치 되지만 앱이 스토어 서명 된 경우에는 시작 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ed2df-115">However, going about the latter way will install the app but will fail to launch if the app is store-signed.</span></span>

<span data-ttu-id="ed2df-116">장치에 응용 프로그램을 설치 하려면 다음을 수행 하세요.</span><span class="sxs-lookup"><span data-stu-id="ed2df-116">To install your application on the device please do the following:</span></span>

1. <span data-ttu-id="ed2df-117">IoT 장치에 대 한 [Windows 장치 포털](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal) 을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="ed2df-117">Open the [Windows Device Portal](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal) for your IoT device.</span></span>

2. <span data-ttu-id="ed2df-118">앱 메뉴 에서 응용 프로그램 파일을 선택 하 고 **설치**를 클릭 하 여 앱을 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed2df-118">In the **Apps** menu, install your app by selecting your app files and clicking **Install**.</span></span>

3. <span data-ttu-id="ed2df-119">**파일 선택** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed2df-119">Click **Select File**</span></span>

4. <span data-ttu-id="ed2df-120">.Appx 파일을 선택 하 고 **열기** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed2df-120">Select your .appx file and click **Open**</span></span>

5. <span data-ttu-id="ed2df-121">**프레임 워크 패키지 선택 허용을 선택 합니다** .</span><span class="sxs-lookup"><span data-stu-id="ed2df-121">Check **Allow me to select framework packages**</span></span>

6. <span data-ttu-id="ed2df-122">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ed2df-122">Click **Next**</span></span>

7. <span data-ttu-id="ed2df-123">.Appx의 **종속성** 폴더에 있는 각 항목에 대해 7.1 및 7.2 단계를 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed2df-123">For each item in the **Dependencies** folder for your .appx repeat step 7.1 and 7.2</span></span>

    <span data-ttu-id="ed2df-124">7.1 **파일 선택** 클릭</span><span class="sxs-lookup"><span data-stu-id="ed2df-124">7.1 Click **Choose File**</span></span>

    <span data-ttu-id="ed2df-125">7.2 depenency를 선택 하 고 **열기** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed2df-125">7.2 Select the depenency .appx and click **Open**</span></span>

8. <span data-ttu-id="ed2df-126">모든 종속성이 추가 되 면 **설치** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed2df-126">When all of the dependencies are added click **Install**</span></span>

9. <span data-ttu-id="ed2df-127">설치가 완료 될 때까지 기다렸다가 **완료** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed2df-127">Wait for the install is completed and click **Done**</span></span>

 ![앱 설치](../media/AppInstaller/install-app.gif)

10. <span data-ttu-id="ed2df-129">이제 응용 프로그램이 장치의 응용 프로그램 목록에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ed2df-129">The application will now be visible on the list of applications on your device.</span></span>
 <span data-ttu-id="ed2df-130">![앱 설치](../media/AppInstaller/install-app.gif)</span><span class="sxs-lookup"><span data-stu-id="ed2df-130">![Install App](../media/AppInstaller/install-app.gif)</span></span>


## <a name="using-provisioning-package-from-wcd"></a><span data-ttu-id="ed2df-131">WCD에서 프로 비전 패키지 사용</span><span class="sxs-lookup"><span data-stu-id="ed2df-131">Using provisioning package from WCD</span></span>
<span data-ttu-id="ed2df-132">앱을 사용 하 여 프로 비전 패키지를 만들고 장치에 프로 비전 패키지를 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ed2df-132">You can create a provisioning package with the app and install the provisioning package on the device.</span></span> <span data-ttu-id="ed2df-133">이 방법은 인터넷에 연결 되지 않은 장치 에서도 작동 하며, 스토어 라이선스 파일을 설치 하는 기본 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="ed2df-133">This method works even on devices that do not have internet connection, and is the preferred method for installing the store license file.</span></span> <span data-ttu-id="ed2df-134">예를 들어 장치가 인터넷에 연결 되어 있지 않지만 기본 앱이 스토어 서명 된 UWP 앱 인 팩터리 시나리오를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ed2df-134">For example, this enables factory scenarios where the device is not connected to the internet but the primary app is a store-signed UWP app.</span></span>

> [!NOTE]
> <span data-ttu-id="ed2df-135">PFN (패키지 패밀리 이름)은 앱 **관리 > 앱 id** 의 Windows 개발자 센터에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ed2df-135">The Package Family Name (PFN) can be found in the Windows Dev Center under **App Management > App Identity**</span></span>

1. <span data-ttu-id="ed2df-136">[Windows 구성 디자이너 열기 (WICD)](https://docs.microsoft.com/windows/configuration/provisioning-packages/provisioning-install-icd)</span><span class="sxs-lookup"><span data-stu-id="ed2df-136">Open [Windows Configuration Designer (WICD)](https://docs.microsoft.com/windows/configuration/provisioning-packages/provisioning-install-icd)</span></span>

2. <span data-ttu-id="ed2df-137">**고급 프로 비전**을 선택 하 고 프로젝트 이름 및 설명을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed2df-137">Select **Advanced Provisioning**, Enter the project name and a description</span></span>

3. <span data-ttu-id="ed2df-138">프로젝트 설정에 대해 Windows 10 IoT Core를 선택 하 고 프로 비전 패키지 가져오기를 건너뜁니다.</span><span class="sxs-lookup"><span data-stu-id="ed2df-138">Choose Windows 10 IoT Core for the project settings and skip the provisioning package import</span></span>

4. <span data-ttu-id="ed2df-139">왼쪽에서 **런타임 설정** 을 확장 하 고 **유니버설 앱 설치 > 사용자 컨텍스트 앱** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed2df-139">On the left hand side expand **Runtime Settings** and click on **Universal App Install > User Context App**</span></span>

5. <span data-ttu-id="ed2df-140">앱의 패키지 패밀리 이름을 입력 하 고 **추가** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed2df-140">Enter the Package Family Name of your app and click **Add**</span></span>

6. <span data-ttu-id="ed2df-141">새로 추가 된 PFN에서</span><span class="sxs-lookup"><span data-stu-id="ed2df-141">Under the newly added PFN</span></span>
    - <span data-ttu-id="ed2df-142">Appx 및 해당 종속성 추가</span><span class="sxs-lookup"><span data-stu-id="ed2df-142">add the Appx and its dependencies</span></span>
    - <span data-ttu-id="ed2df-143">DeploymentOptions를 "대상 응용 프로그램 종료 강제 종료"로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed2df-143">set the DeploymentOptions to "Force target application shutdown"</span></span>

7. <span data-ttu-id="ed2df-144">스토어 서명 된 앱의 경우 라이선스를 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed2df-144">For Store signed apps, you will need to specify the license.</span></span> <span data-ttu-id="ed2df-145">UserContextAppLicense 아래에서</span><span class="sxs-lookup"><span data-stu-id="ed2df-145">Under UserContextAppLicense,</span></span>
    - <span data-ttu-id="ed2df-146">LicenseProductID 추가 (라이선스 XML 파일에서 LicenseID로 사용 가능)</span><span class="sxs-lookup"><span data-stu-id="ed2df-146">add LicenseProductID (available as LicenseID in the license XML file)</span></span>
    - <span data-ttu-id="ed2df-147">라이선스 xml 확장을 *. m s-windows 스토어 라이선스*로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed2df-147">change the license xml extension to *.ms-windows-store-license*.</span></span>
    - <span data-ttu-id="ed2df-148">왼쪽에서 라이선스 제품 ID를 선택 하 고 라이선스 파일을 검색 하 여 LicenseInstall 필드를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed2df-148">select your License Product ID on the left hand side and browse your license file to assign LicenseInstall field</span></span>

8. <span data-ttu-id="ed2df-149">비 스토어 서명 된 앱의 경우 **인증서 > RootCertificates** 에 앱 .cer 파일을 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed2df-149">For non-store signed apps, you will need to add the app.cer file under **Certificates > RootCertificates**</span></span> 

9. <span data-ttu-id="ed2df-150">패키지 내보내기</span><span class="sxs-lookup"><span data-stu-id="ed2df-150">Export the package</span></span>

10. <span data-ttu-id="ed2df-151">[SSH](../connect-your-device/SSH.md) 또는 [Powershell](../connect-your-device/powershell.md)을 사용 하 여 내보낸. Ppkg 파일을 IoT 장치의 _C:\Windows\Provisioning\Packages_ 에 복사 하 고 다시 부팅 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed2df-151">Copy the exported .ppkg file to _C:\Windows\Provisioning\Packages_ on the IoT device using [SSH](../connect-your-device/SSH.md) or [Powershell](../connect-your-device/powershell.md)) and reboot.</span></span> <span data-ttu-id="ed2df-152">장치를 다시 부팅 하면 프로 비전 패키지가 처리 되 고 앱이 설치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ed2df-152">When the device reboots, the provisioning package is processed and the app is installed.</span></span>


## <a name="add-the-app-to-the-windows-iot-core-imageffu"></a><span data-ttu-id="ed2df-153">Windows IoT Core 이미지 (.ffu)에 앱 추가</span><span class="sxs-lookup"><span data-stu-id="ed2df-153">Add the app to the Windows IoT Core image(.ffu)</span></span>
<span data-ttu-id="ed2df-154">Windows IoT Core 이미지 자체의 일부가 되도록 앱을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ed2df-154">You can add the app to be part of the Windows IoT Core image itself.</span></span>
<span data-ttu-id="ed2df-155">이 방법은 Oem이 장치에 앱을 설치 하는 데 선호 되는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="ed2df-155">This is the preferred method for OEMs to install apps on their devices.</span></span>

<span data-ttu-id="ed2df-156">[이미지에 앱을 추가](https://docs.microsoft.com/windows-hardware/manufacture/iot/deploy-your-app-with-a-standard-board) 하는 방법 및 [샘플 앱 패키지](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Packages/Appx.IoTCoreDefaultApp)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ed2df-156">See how to [add an app to your image](https://docs.microsoft.com/windows-hardware/manufacture/iot/deploy-your-app-with-a-standard-board) and a [sample app package](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Packages/Appx.IoTCoreDefaultApp).</span></span>
