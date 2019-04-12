---
title: IoT Core 장치에 앱 설치
author: parameshbabu
ms.author: pabab
ms.date: 08/28/2017
ms.topic: article
description: Windows Device Portal 사용 하 여 앱을 설치 하는 방법을 알아봅니다 또는 IoT의 일환으로 이미지를 핵심입니다.
keywords: windows iot, 앱 설치, Windows Device Portal 장치
ms.openlocfilehash: 6e188eaef6551548c6c71ac50859516d4cbe7e9c
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513030"
---
# <a name="install-your-app-on-an-iot-core-device"></a><span data-ttu-id="99054-104">IoT Core 장치에 앱 설치</span><span class="sxs-lookup"><span data-stu-id="99054-104">Install your app on an IoT Core device</span></span>
<span data-ttu-id="99054-105">아래 나열 된 두 가지 방법 중 하나를 사용 하 여 앱을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99054-105">You can install your app using one of the two methods that are listed below.</span></span>

> [!NOTE]
> <span data-ttu-id="99054-106">Windows Device Portal 사용 하 여 메서드는 개발자 시나리오에 대해서만 됩니다.</span><span class="sxs-lookup"><span data-stu-id="99054-106">The method using the Windows Device Portal is only for developer scenarios.</span></span> <span data-ttu-id="99054-107">다른 두 메서드는 프로덕션 시나리오에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="99054-107">The other two methods are for production scenarios.</span></span>

## <a name="using-windows-device-portal"></a><span data-ttu-id="99054-108">Windows Device Portal 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="99054-108">Using Windows Device Portal</span></span>

<span data-ttu-id="99054-109">이 방법에서는 인터넷에 연결 되어 있는지 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="99054-109">For this method, you will need to ensure that you are connected to the internet.</span></span> <span data-ttu-id="99054-110">인터넷에 액세스할 수 없는 경우 장치 및 공개 인터넷 액세스에 대 한 경로 포함 하지 않는 클라이언트 컴퓨터 간의 피어-투-피어 이더넷 연결을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99054-110">If you do not have access to the internet, you can also have a peer-to-peer ethernet connection between the device and a client machine that doesn't include a path to access the open internet.</span></span> <span data-ttu-id="99054-111">두 번째 방법에 대 한 지속적인이 앱을 설치 하지만 앱 스토어 로그인이 시작 되지 것입니다.</span><span class="sxs-lookup"><span data-stu-id="99054-111">However, going about the latter way will install the app but will fail to launch if the app is store-signed.</span></span>

<span data-ttu-id="99054-112">설치 하려면 장치에서 응용 프로그램 다음을 수행 하십시오.</span><span class="sxs-lookup"><span data-stu-id="99054-112">To install your application on the device please do the following:</span></span>

1. <span data-ttu-id="99054-113">엽니다는 [Windows Device Portal](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal) IoT 장치에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="99054-113">Open the [Windows Device Portal](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal) for your IoT device.</span></span>

2. <span data-ttu-id="99054-114">에 *앱* 메뉴에서 앱 패키지를 업로드 하 여 앱을 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="99054-114">In the *Apps* menu, install your app by uploading the app package.</span></span>
 ![앱 설치](../media/AppInstaller/install-app.gif)

3. <span data-ttu-id="99054-116">앱을 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="99054-116">Deploy the app.</span></span>

4. <span data-ttu-id="99054-117">이제 응용 프로그램 장치에서 응용 프로그램 목록에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="99054-117">The application will now be visible on the list of applications on your device.</span></span>
 ![앱 목록](../media/AppInstaller/AppList.png)


## <a name="using-provisioning-package-from-wcd"></a><span data-ttu-id="99054-119">WCD에서 프로 비전 패키지를 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="99054-119">Using provisioning package from WCD</span></span>
<span data-ttu-id="99054-120">앱을 사용 하 여 프로 비전 패키지를 만들고 장치의 프로 비전 패키지를 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99054-120">You can create a provisioning package with the app and install the provisioning package on the device.</span></span> <span data-ttu-id="99054-121">이 메서드는 인터넷에 연결 되지 않은 장치 에서도 작동 하며 저장소 라이선스 파일을 설치 하기 위한 방법이 더 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="99054-121">This method works even on devices that do not have internet connection, and is the preferred method for installing the store license file.</span></span> <span data-ttu-id="99054-122">예를 들어 여기서는 장치가 인터넷에 연결 되어 있지 않지만 기본 앱은 스토어 로그인 UWP 앱 팩터리 시나리오 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="99054-122">For example, this enables factory scenarios where the device is not connected to the internet but the primary app is a store-signed UWP app.</span></span>

> [!NOTE]
> <span data-ttu-id="99054-123">패키지 제품군 이름 (PFN) 아래 Windows 개발자 센터에서 찾을 수 있습니다 **앱 관리 > 앱 Id**</span><span class="sxs-lookup"><span data-stu-id="99054-123">The Package Family Name (PFN) can be found in the Windows Dev Center under **App Management > App Identity**</span></span>

1. <span data-ttu-id="99054-124">열기 [Windows 구성 디자이너 (WICD)](https://docs.microsoft.com/windows/configuration/provisioning-packages/provisioning-install-icd)</span><span class="sxs-lookup"><span data-stu-id="99054-124">Open [Windows Configuration Designer (WICD)](https://docs.microsoft.com/windows/configuration/provisioning-packages/provisioning-install-icd)</span></span>

2. <span data-ttu-id="99054-125">선택 **프로 비전 고급**, 프로젝트 이름 및 설명을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="99054-125">Select **Advanced Provisioning**, Enter the project name and a description</span></span>

3. <span data-ttu-id="99054-126">프로젝트 설정에 대 한 Windows 10 IoT Core 선택 하 고 프로 비전 패키지 가져오기를 건너뛸합니다</span><span class="sxs-lookup"><span data-stu-id="99054-126">Choose Windows 10 IoT Core for the project settings and skip the provisioning package import</span></span>

4. <span data-ttu-id="99054-127">왼쪽 창에서 확장 **런타임 설정을** 클릭 하 고 **유니버설 앱 설치 > 사용자 상황에 맞는 앱**</span><span class="sxs-lookup"><span data-stu-id="99054-127">On the left hand side expand **Runtime Settings** and click on **Universal App Install > User Context App**</span></span>

5. <span data-ttu-id="99054-128">앱의 패키지 패밀리 이름을 입력 **추가**</span><span class="sxs-lookup"><span data-stu-id="99054-128">Enter the Package Family Name of your app and click **Add**</span></span>

6. <span data-ttu-id="99054-129">새로 추가 된 PFN 아래</span><span class="sxs-lookup"><span data-stu-id="99054-129">Under the newly added PFN</span></span>
    - <span data-ttu-id="99054-130">추가 된 Appx 및 해당 종속성</span><span class="sxs-lookup"><span data-stu-id="99054-130">add the Appx and its dependencies</span></span>
    - <span data-ttu-id="99054-131">"Force 대상 응용 프로그램 종료" DeploymentOptions 설정</span><span class="sxs-lookup"><span data-stu-id="99054-131">set the DeploymentOptions to "Force target application shutdown"</span></span>

7. <span data-ttu-id="99054-132">저장소 서명 앱에 대 한 라이선스를 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="99054-132">For Store signed apps, you will need to specify the license.</span></span> <span data-ttu-id="99054-133">UserContextAppLicense, 아래</span><span class="sxs-lookup"><span data-stu-id="99054-133">Under UserContextAppLicense,</span></span>
    - <span data-ttu-id="99054-134">LicenseProductID (라이선스 XML 파일에서 LicenseID로 제공)를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="99054-134">add LicenseProductID (available as LicenseID in the license XML file)</span></span>
    - <span data-ttu-id="99054-135">라이선스 xml 확장을 변경 *.ms-windows-저장소-라이선스*합니다.</span><span class="sxs-lookup"><span data-stu-id="99054-135">change the license xml extension to *.ms-windows-store-license*.</span></span>
    - <span data-ttu-id="99054-136">왼쪽 창에서 라이선스 제품 ID를 선택 하 고 LicenseInstall 필드에 할당할 라이선스 파일 찾아보기</span><span class="sxs-lookup"><span data-stu-id="99054-136">select your License Product ID on the left hand side and browse your license file to assign LicenseInstall field</span></span>

8. <span data-ttu-id="99054-137">서명 된 앱의 스토어 이외의 경우 app.cer로 파일을 추가 해야 **인증서 > RootCertificates**</span><span class="sxs-lookup"><span data-stu-id="99054-137">For non-store signed apps, you will need to add the app.cer file under **Certificates > RootCertificates**</span></span> 

9. <span data-ttu-id="99054-138">패키지 내보내기</span><span class="sxs-lookup"><span data-stu-id="99054-138">Export the package</span></span>

10. <span data-ttu-id="99054-139">내보낸된.ppkg 파일을 복사 _C:\Windows\Provisioning\Packages_ 사용 하 여 IoT 장치 [SSH](../connect-your-device/SSH.md) 하거나 [Powershell](../connect-your-device/powershell.md)) 하 고 다시 부팅 합니다.</span><span class="sxs-lookup"><span data-stu-id="99054-139">Copy the exported .ppkg file to _C:\Windows\Provisioning\Packages_ on the IoT device using [SSH](../connect-your-device/SSH.md) or [Powershell](../connect-your-device/powershell.md)) and reboot.</span></span> <span data-ttu-id="99054-140">장치를 다시 부팅 하는 경우 프로 비전 패키지 처리 되 고 앱이 설치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="99054-140">When the device reboots, the provisioning package is processed and the app is installed.</span></span>


## <a name="add-to-the-iot-core-imageffu"></a><span data-ttu-id="99054-141">IoT core image(.ffu)에 추가</span><span class="sxs-lookup"><span data-stu-id="99054-141">Add to the IoT core image(.ffu)</span></span>   
<span data-ttu-id="99054-142">IoT Core 이미지 자체의 일부가 되도록 앱을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99054-142">You can add the app to be part of the IoT Core image itself.</span></span> <span data-ttu-id="99054-143">Oem 위한 널리 사용 되는 메커니즘입니다.</span><span class="sxs-lookup"><span data-stu-id="99054-143">This is the widely used mechanism for OEMs.</span></span> 

<span data-ttu-id="99054-144">참조 하는 방법 [이미지에 앱 추가](https://docs.microsoft.com/windows-hardware/manufacture/iot/deploy-your-app-with-a-standard-board) 와 [샘플 앱 패키지](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Packages/Appx.IoTCoreDefaultApp)합니다.</span><span class="sxs-lookup"><span data-stu-id="99054-144">See how to [add an app to your image](https://docs.microsoft.com/windows-hardware/manufacture/iot/deploy-your-app-with-a-standard-board) and a [sample app package](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Packages/Appx.IoTCoreDefaultApp).</span></span>
