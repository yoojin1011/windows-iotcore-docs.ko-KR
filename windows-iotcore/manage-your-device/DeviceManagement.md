---
title: Windows IoT Core 장치 관리
author: parameshbabu
ms.author: pabab
ms.date: 08/28/2017
ms.topic: article
description: Windows 10 IoT Core 장치를 관리 하는 다른 방법에 알아봅니다.
keywords: windows iot, windows iot, Azure DM, Azure Hub, Azure IoT 장치 관리
ms.openlocfilehash: dbcc6858ee32ce9eb8b33c3d1831a6581a8fa3c7
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513710"
---
# <a name="managing-windows-iot-core-devices"></a><span data-ttu-id="38e4d-104">Windows IoT Core 장치 관리</span><span class="sxs-lookup"><span data-stu-id="38e4d-104">Managing Windows IoT Core Devices</span></span>

<span data-ttu-id="38e4d-105">인증서 기반 등록을 지 원하는 기존의 OMA DM MDM 서버를 사용 하 여 또는 Azure IoT Hub 장치 관리를 사용 하 여 Windows 10 IoT Core 장치를 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38e4d-105">Windows 10 IoT Core devices can be managed using a traditional OMA DM MDM server that supports certificate based enrollment or using Azure IoT Hub's Device Management.</span></span>  

 _<span data-ttu-id="38e4d-106">MDM 및 Windows 10에 대 한 자세한 내용은 곧 [여기](https://msdn.microsoft.com/library/windows/hardware/dn914769(v=vs.85).aspx)합니다.</span><span class="sxs-lookup"><span data-stu-id="38e4d-106">Learn more about MDM and Windows 10 [here](https://msdn.microsoft.com/library/windows/hardware/dn914769(v=vs.85).aspx).</span></span>_  

<span data-ttu-id="38e4d-107">OMA DM server를 사용 하 여 관리 되는 장치에 대 한 Windows 10 IoT Core 대 한 MDM 정책을 다른 버전의 Windows 10에서 지원 되는 정책에 맞춰집니다.</span><span class="sxs-lookup"><span data-stu-id="38e4d-107">For devices that are managed using a OMA DM server the MDM policies for Windows 10 IoT Core align with the policies supported in other editions of Windows 10.</span></span> <span data-ttu-id="38e4d-108">뿐만 아니라 정책에 대 한 내용으로 IoT Core 장치에서 관리할 수 있습니다, 참조 구성 서비스 공급자 참조 Windows 10 용 [여기](https://aka.ms/csplist)합니다.</span><span class="sxs-lookup"><span data-stu-id="38e4d-108">To learn more about policies as well as what can be managed on IoT Core devices, see Configuration service provider reference for Windows 10 [here](https://aka.ms/csplist).</span></span> <span data-ttu-id="38e4d-109">MDM을 지 원하는 Windows 10에서 Open Mobile Alliance (OMA) 장치 관리 (DM) 1.2.1 프로토콜 사양을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="38e4d-109">The MDM support in Windows 10 is based on Open Mobile Alliance (OMA) Device Management (DM) protocol 1.2.1 specification.</span></span>

## <a name="how-do-i-enroll-an-iot-core-device-into-a-mdm"></a><span data-ttu-id="38e4d-110">IoT Core 장치를 MDM에 등록 하려면 어떻게 해야 하나요?</span><span class="sxs-lookup"><span data-stu-id="38e4d-110">How do I enroll an IoT Core device into a MDM?</span></span>
___
<span data-ttu-id="38e4d-111">MDM 등록을 IoT Core 장치 프로 비전 패키지를 사용 하 여 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="38e4d-111">MDM enrollment of an IoT Core device is accomplished using a Provisioning package.</span></span> <span data-ttu-id="38e4d-112">패키지를 프로 비전 Windows 이미지 구성 및 디자이너 (WICD)를 사용 하 여 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38e4d-112">Provisioning packages can be created using Windows Image Configuration and Designer (WICD).</span></span> <span data-ttu-id="38e4d-113">MDM.에 장치 등록을 시도해 보겠습니다</span><span class="sxs-lookup"><span data-stu-id="38e4d-113">Let's try enrolling a device into a MDM.</span></span>

### <a name="creating-a-provisioning-package"></a><span data-ttu-id="38e4d-114">프로 비전 패키지 만들기</span><span class="sxs-lookup"><span data-stu-id="38e4d-114">Creating a Provisioning package</span></span>

#### <a name="microsoft-system-center-configuration-manager-standalone-or-sccmintune-hybrid"></a><span data-ttu-id="38e4d-115">Microsoft System Center Configuration Manager (독립 실행형 또는 SCCM + Intune 하이브리드)</span><span class="sxs-lookup"><span data-stu-id="38e4d-115">Microsoft System Center Configuration Manager (Standalone or SCCM+Intune Hybrid)</span></span>

1. <span data-ttu-id="38e4d-116">Configuration Manager 관리 콘솔 (ConfigMgr 콘솔) 열기</span><span class="sxs-lookup"><span data-stu-id="38e4d-116">Open the Configuration Manager Management Console (ConfigMgr Console)</span></span>

2. <span data-ttu-id="38e4d-117">이동할 _자산 및 준수 > 규정 준수 설정 > 회사 리소스 액세스 > 인증서 프로필_
   ![인증서 프로필](../media/ManagingDevices/ConfigMgr-Certificate-Profiles.PNG)</span><span class="sxs-lookup"><span data-stu-id="38e4d-117">Navigate to _Assets and Compliance > Compliance Settings > Company Resource Access > Certificate Profiles_
![Certificate Profiles](../media/ManagingDevices/ConfigMgr-Certificate-Profiles.PNG)</span></span>

3. <span data-ttu-id="38e4d-118">클릭 **인증서 프로필 만들기**</span><span class="sxs-lookup"><span data-stu-id="38e4d-118">Click **Create Certificate Profile**</span></span>

4. <span data-ttu-id="38e4d-119">이름 및 프로필에 대 한 설명을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="38e4d-119">Provide a name and description for the profile</span></span>
   - <span data-ttu-id="38e4d-120">이름: ConfigMgr 예제에서는 신뢰할 수 있는 루트 인증서</span><span class="sxs-lookup"><span data-stu-id="38e4d-120">Name: ConfigMgr Example Trusted Root Certificate</span></span>
     - <span data-ttu-id="38e4d-121">인증서 프로필의 유형: 신뢰할 수 있는 CA 인증서</span><span class="sxs-lookup"><span data-stu-id="38e4d-121">Type of certificate profile: Trusted CA certificate</span></span>  
     ![신뢰할 수 있는 인증](../media/ManagingDevices/ConfigMgr-Certificate-Profiles-Wizard.png)

5. <span data-ttu-id="38e4d-123">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="38e4d-123">Click **Next**.</span></span>

6. <span data-ttu-id="38e4d-124">인증서 파일을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="38e4d-124">Import the certificate file.</span></span>

7. <span data-ttu-id="38e4d-125">선택 **컴퓨터 인증서 저장소-루트** 에 대 한 합니다 **대상 저장소**합니다.</span><span class="sxs-lookup"><span data-stu-id="38e4d-125">Select **Computer certificate store - Root** for the **Destination Store**.</span></span>

8. <span data-ttu-id="38e4d-126">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="38e4d-126">Click **Next**.</span></span>

9. <span data-ttu-id="38e4d-127">선택할 **모두 선택** 지원 되는 플랫폼에 대 한 ![지원 되는 플랫폼](../media/ManagingDevices/ConfigMgr-Certificate-Profiles-Wizard-Supported-Platforms.png)</span><span class="sxs-lookup"><span data-stu-id="38e4d-127">Choose **Select all** for Supported Platforms ![Supported platforms](../media/ManagingDevices/ConfigMgr-Certificate-Profiles-Wizard-Supported-Platforms.png)</span></span>

10. <span data-ttu-id="38e4d-128">클릭 **요약, Next 및 닫기** 마법사를 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="38e4d-128">Click **Summary, Next, and Close** to exit the wizard.</span></span>

11. <span data-ttu-id="38e4d-129">방금 만든 프로필을 마우스 오른쪽 단추로 클릭 하 고 클릭 **내보내기**합니다.</span><span class="sxs-lookup"><span data-stu-id="38e4d-129">Right-click on the profile just created and click **Export**.</span></span>

12. <span data-ttu-id="38e4d-130">클릭 **찾아보기**,.ppkg 파일을 내보내야 할 및 클릭 한 위치를 찾으려면 **저장**합니다.</span><span class="sxs-lookup"><span data-stu-id="38e4d-130">Click **Browse**, find a location where the .ppkg file should be exported, and then click **Save**.</span></span>

13. <span data-ttu-id="38e4d-131">클릭 **내보내기** 클릭 **확인** 마법사를 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="38e4d-131">Click **Export** and click **OK** to exit the wizard.</span></span>

#### <a name="other-mdm-servers"></a><span data-ttu-id="38e4d-132">다른 MDM 서버</span><span class="sxs-lookup"><span data-stu-id="38e4d-132">Other MDM Servers</span></span>

1. <span data-ttu-id="38e4d-133">다운로드 및 설치 합니다 [Windows 평가 및 배포 키트 (Windows ADK)](https://developer.microsoft.com/windows/hardware/windows-assessment-deployment-kit)합니다.</span><span class="sxs-lookup"><span data-stu-id="38e4d-133">Download and install the [Windows Assessment and Deployment Kit (Windows ADK)](https://developer.microsoft.com/windows/hardware/windows-assessment-deployment-kit).</span></span>

2. <span data-ttu-id="38e4d-134">Windows 이미징 및 구성 디자이너 (WICD)를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="38e4d-134">Open Windows Imaging and Configuration Designer (WICD).</span></span>
   ![Windows 이미징 및 구성 디자이너](../media/ManagingDevices/WICD-Start-Page.png)

3. <span data-ttu-id="38e4d-136">선택 **고급 프로 비전**</span><span class="sxs-lookup"><span data-stu-id="38e4d-136">Choose **Advanced Provisioning**</span></span>

4. <span data-ttu-id="38e4d-137">패키지의 이름을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="38e4d-137">Set a name for your package.</span></span>

5. <span data-ttu-id="38e4d-138">Windows 10 IoT Core 공통적으로 적용 설정을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="38e4d-138">Choose settings common to Windows 10 IoT Core.</span></span>

6. <span data-ttu-id="38e4d-139">패키지 가져오기 단계를 건너뜁니다.</span><span class="sxs-lookup"><span data-stu-id="38e4d-139">Skip the Import Package step.</span></span>
   ![<span data-ttu-id="38e4d-140">WICD-New-Project-Details](../media/ManagingDevices/WICD-Advanced-Provisioning-New-Project-Details.PNG) 
   ![WICD-New-Project-Editions](../media/ManagingDevices/WICD-Advanced-Provisioning-New-Project-Editions.PNG) 
   ![WICD-New-Project-Import</span><span class="sxs-lookup"><span data-stu-id="38e4d-140">WICD-New-Project-Details](../media/ManagingDevices/WICD-Advanced-Provisioning-New-Project-Details.PNG) 
![WICD-New-Project-Editions](../media/ManagingDevices/WICD-Advanced-Provisioning-New-Project-Editions.PNG) 
![WICD-New-Project-Import</span></span>](../media/ManagingDevices/WICD-Advanced-Provisioning-New-Project-Import.PNG)

7. <span data-ttu-id="38e4d-141">작업 공간으로 이동 등록-> 합니다.</span><span class="sxs-lookup"><span data-stu-id="38e4d-141">Navigate to Workplace -> Enrollments.</span></span>

8. <span data-ttu-id="38e4d-142">UPN 필드에 입력에서 장치를 등록 하려면 계정 (즉 trmck@contoso.co)를 누릅니다 **추가**합니다.</span><span class="sxs-lookup"><span data-stu-id="38e4d-142">In the UPN field enter the account you wish to enroll your device under (i.e. trmck@contoso.co) and click **Add**.</span></span>

   ![작업 공간 등록 입력](../media/ManagingDevices/WICD-Workplace-Enrollments-UPN-Filled.png)

9. <span data-ttu-id="38e4d-144">AuthPolicy 중에서 선택에 대 한 사용자 이름 암호 기반 인증 (온-프레미스) 또는 인증서 기반 인증 합니다.</span><span class="sxs-lookup"><span data-stu-id="38e4d-144">For AuthPolicy choose between Username Password based authentication (OnPremises) or Certificate based authentication.</span></span>

10. <span data-ttu-id="38e4d-145">MDM 서버에 대 한 검색 서비스 URL을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="38e4d-145">Enter the Discovery Service URL for your MDM server.</span></span>

> [!NOTE]
> <span data-ttu-id="38e4d-146">등록 서비스 URL 및 정책 서비스 URL은 선택적입니다.</span><span class="sxs-lookup"><span data-stu-id="38e4d-146">Enrollment Service URL and Policy Service URL are optional.</span></span>

11. <span data-ttu-id="38e4d-147">비밀 입력에 대 한</span><span class="sxs-lookup"><span data-stu-id="38e4d-147">For the Secret enter</span></span>  
    - <span data-ttu-id="38e4d-148">온-프레미스: 사용 하 여 등록 하는 계정의 암호</span><span class="sxs-lookup"><span data-stu-id="38e4d-148">OnPremises: The password for the account you're enrolling with</span></span>  
    - <span data-ttu-id="38e4d-149">인증서: 인증서의 지문</span><span class="sxs-lookup"><span data-stu-id="38e4d-149">Certificate: The thumbprint of the certificate</span></span>
    
    ![채워진된 온-프레미스](../media/ManagingDevices/WICD-Workplace-Enrollments-UPN-Details-Filled-Premise.png)  

12. <span data-ttu-id="38e4d-151">WICD 창의 맨 위에 있는 클릭 **내보내기 > 프로 비전 패키지**합니다.</span><span class="sxs-lookup"><span data-stu-id="38e4d-151">At the top of WICD window click **Export > Provisioning package**.</span></span>

13. <span data-ttu-id="38e4d-152">패키지에 대 한 이름 및 버전을 제공 하 고 클릭 **다음**합니다.</span><span class="sxs-lookup"><span data-stu-id="38e4d-152">Provide a name and version for your package and click **Next**.</span></span> 

> [!NOTE]
> <span data-ttu-id="38e4d-153">업데이트 된 패키지를 실행 되도록 버전 번호가 증가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38e4d-153">Be sure to increment the version number to ensure an updated package is executed.</span></span>

14. <span data-ttu-id="38e4d-154">클릭 **다음** 에 **보안 세부 정보 페이지**합니다.</span><span class="sxs-lookup"><span data-stu-id="38e4d-154">Click **Next** on the **security details page**.</span></span>

15. <span data-ttu-id="38e4d-155">패키지를 로컬 컴퓨터 클릭에서 내보낼 수 있는 위치를 선택 **다음**합니다.</span><span class="sxs-lookup"><span data-stu-id="38e4d-155">Choose the location where the package is to be exported on the local machine and click **Next**.</span></span>

16. <span data-ttu-id="38e4d-156">클릭 **빌드** 차례로 **마침** 마법사를 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="38e4d-156">Click **Build** and then **Finish** to exit the wizard.</span></span>

### <a name="installing-the-provisioning-package"></a><span data-ttu-id="38e4d-157">프로 비전 패키지를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="38e4d-157">Installing the Provisioning package</span></span>

<span data-ttu-id="38e4d-158">IoT 장치에 프로 비전 패키지를 배포할 수 있는 몇 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38e4d-158">There are a few ways in which a Provisioning package can be deployed to an IoT device.</span></span> <span data-ttu-id="38e4d-159">장치에 패키지를 복사 하거나 이미징 프로세스 중 이미지에 패키지를 추가 하 여 패키지를 배포 하는 것이 가능 합니다.</span><span class="sxs-lookup"><span data-stu-id="38e4d-159">It is possible to deploy a package by copying the package to the device or adding the package to the image during the imaging process.</span></span>

#### <a name="copying-package-to-device"></a><span data-ttu-id="38e4d-160">장치에 패키지 복사</span><span class="sxs-lookup"><span data-stu-id="38e4d-160">Copying package to device</span></span>

<span data-ttu-id="38e4d-161">SCCM 또는 WICD에서 내보낸 프로 비전 패키지를 가져오고.ppkg 파일을 복사 `C:\Windows\Provisioning\Packages` IoT 장치의 디렉터리입니다.</span><span class="sxs-lookup"><span data-stu-id="38e4d-161">Take the Provisioning package that was exported from SCCM or WICD and copy the .ppkg file to `C:\Windows\Provisioning\Packages` directory on the IoT device.</span></span> <span data-ttu-id="38e4d-162">장치 재부팅 시 패키지 실행 되 고 장치가 등록 프로세스를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="38e4d-162">Upon reboot of the device the package will be executed and the device will start the enrollment process.</span></span>

#### <a name="adding-package-to-image"></a><span data-ttu-id="38e4d-163">이미지에 패키지 추가</span><span class="sxs-lookup"><span data-stu-id="38e4d-163">Adding package to image</span></span>

<span data-ttu-id="38e4d-164">참조 [이미지에 프로 비전 패키지 추가](https://docs.microsoft.com/windows-hardware/manufacture/iot/add-a-provisioning-package-to-an-image)합니다.</span><span class="sxs-lookup"><span data-stu-id="38e4d-164">See [Add a provisioning package to an image](https://docs.microsoft.com/windows-hardware/manufacture/iot/add-a-provisioning-package-to-an-image).</span></span> <span data-ttu-id="38e4d-165">최초 부팅 시 장치 패키지를 실행 하 고 등록 프로세스를 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="38e4d-165">Upon first boot the device will execute the package and start the enrollment process.</span></span>
