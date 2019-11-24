---
title: Windows IoT Core 장치 관리
author: parameshbabu
ms.author: pabab
ms.date: 08/28/2017
ms.topic: article
description: Windows 10 IoT Core 장치를 관리 하는 다양 한 방법에 대해 알아봅니다.
keywords: windows iot, 장치 관리, windows iot, Azure DM, azure 허브, azure IoT
ms.openlocfilehash: dbcc6858ee32ce9eb8b33c3d1831a6581a8fa3c7
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "60170923"
---
# <a name="managing-windows-iot-core-devices"></a><span data-ttu-id="33ace-104">Windows IoT Core 장치 관리</span><span class="sxs-lookup"><span data-stu-id="33ace-104">Managing Windows IoT Core Devices</span></span>

<span data-ttu-id="33ace-105">Windows 10 IoT Core 장치는 인증서 기반 등록을 지 원하는 기존 OMA DM MDM 서버를 사용 하거나 Azure IoT Hub의 장치 관리를 사용 하 여 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33ace-105">Windows 10 IoT Core devices can be managed using a traditional OMA DM MDM server that supports certificate based enrollment or using Azure IoT Hub's Device Management.</span></span>  

 <span data-ttu-id="33ace-106">_MDM 및 Windows 10에 대 한 자세한 내용은 [여기](https://msdn.microsoft.com/library/windows/hardware/dn914769(v=vs.85).aspx)를 참조 하세요._</span><span class="sxs-lookup"><span data-stu-id="33ace-106">_Learn more about MDM and Windows 10 [here](https://msdn.microsoft.com/library/windows/hardware/dn914769(v=vs.85).aspx)._</span></span>  

<span data-ttu-id="33ace-107">OMA DM 서버를 사용 하 여 관리 되는 장치의 경우 Windows 10 IoT Core 용 MDM 정책은 다른 버전의 Windows 10에서 지원 되는 정책과 일치 합니다.</span><span class="sxs-lookup"><span data-stu-id="33ace-107">For devices that are managed using a OMA DM server the MDM policies for Windows 10 IoT Core align with the policies supported in other editions of Windows 10.</span></span> <span data-ttu-id="33ace-108">정책 및 IoT Core 장치에서 관리할 수 있는 항목에 대 한 자세한 내용은 [여기](https://aka.ms/csplist)에서 Windows 10에 대 한 구성 서비스 공급자 참조를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="33ace-108">To learn more about policies as well as what can be managed on IoT Core devices, see Configuration service provider reference for Windows 10 [here](https://aka.ms/csplist).</span></span> <span data-ttu-id="33ace-109">Windows 10의 MDM 지원은 오픈 Mobile (모바일 동맹) DM (장치 관리) 프로토콜 1.2.1 사양을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="33ace-109">The MDM support in Windows 10 is based on Open Mobile Alliance (OMA) Device Management (DM) protocol 1.2.1 specification.</span></span>

## <a name="how-do-i-enroll-an-iot-core-device-into-a-mdm"></a><span data-ttu-id="33ace-110">IoT Core 장치를 MDM에 등록 어떻게 할까요? 있나요?</span><span class="sxs-lookup"><span data-stu-id="33ace-110">How do I enroll an IoT Core device into a MDM?</span></span>
___
<span data-ttu-id="33ace-111">IoT Core 장치의 MDM 등록은 프로 비전 패키지를 사용 하 여 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="33ace-111">MDM enrollment of an IoT Core device is accomplished using a Provisioning package.</span></span> <span data-ttu-id="33ace-112">프로 비전 패키지는 Windows 이미지 구성 및 디자이너 (WICD)를 사용 하 여 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33ace-112">Provisioning packages can be created using Windows Image Configuration and Designer (WICD).</span></span> <span data-ttu-id="33ace-113">장치를 MDM에 등록 해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="33ace-113">Let's try enrolling a device into a MDM.</span></span>

### <a name="creating-a-provisioning-package"></a><span data-ttu-id="33ace-114">프로 비전 패키지 만들기</span><span class="sxs-lookup"><span data-stu-id="33ace-114">Creating a Provisioning package</span></span>

#### <a name="microsoft-system-center-configuration-manager-standalone-or-sccmintune-hybrid"></a><span data-ttu-id="33ace-115">Microsoft System Center Configuration Manager (독립 실행형 또는 SCCM + Intune 하이브리드)</span><span class="sxs-lookup"><span data-stu-id="33ace-115">Microsoft System Center Configuration Manager (Standalone or SCCM+Intune Hybrid)</span></span>

1. <span data-ttu-id="33ace-116">Configuration Manager Management Console (ConfigMgr 콘솔)을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="33ace-116">Open the Configuration Manager Management Console (ConfigMgr Console)</span></span>

2. <span data-ttu-id="33ace-117">_자산 및 준수 > 준수 설정 > 회사 리소스 액세스 > 인증서 프로필_
   ![인증서 프로필로 이동](../media/ManagingDevices/ConfigMgr-Certificate-Profiles.PNG)</span><span class="sxs-lookup"><span data-stu-id="33ace-117">Navigate to _Assets and Compliance > Compliance Settings > Company Resource Access > Certificate Profiles_
![Certificate Profiles](../media/ManagingDevices/ConfigMgr-Certificate-Profiles.PNG)</span></span>

3. <span data-ttu-id="33ace-118">**인증서 프로필 만들기** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="33ace-118">Click **Create Certificate Profile**</span></span>

4. <span data-ttu-id="33ace-119">프로필에 대 한 이름 및 설명을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="33ace-119">Provide a name and description for the profile</span></span>
   - <span data-ttu-id="33ace-120">이름: ConfigMgr 예제 신뢰할 수 있는 루트 인증서</span><span class="sxs-lookup"><span data-stu-id="33ace-120">Name: ConfigMgr Example Trusted Root Certificate</span></span>
     - <span data-ttu-id="33ace-121">인증서 프로필 유형: 신뢰할 수 있는 CA 인증서</span><span class="sxs-lookup"><span data-stu-id="33ace-121">Type of certificate profile: Trusted CA certificate</span></span>  
     ![신뢰할 수 있는 인증](../media/ManagingDevices/ConfigMgr-Certificate-Profiles-Wizard.png)

5. <span data-ttu-id="33ace-123">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="33ace-123">Click **Next**.</span></span>

6. <span data-ttu-id="33ace-124">인증서 파일을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="33ace-124">Import the certificate file.</span></span>

7. <span data-ttu-id="33ace-125">**대상 저장소**에 대 한 **컴퓨터 인증서 저장소-루트** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="33ace-125">Select **Computer certificate store - Root** for the **Destination Store**.</span></span>

8. <span data-ttu-id="33ace-126">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="33ace-126">Click **Next**.</span></span>

9. <span data-ttu-id="33ace-127">지원 되는 플랫폼 ![지원 되는 플랫폼에 대해 **모두 선택** 을 선택](../media/ManagingDevices/ConfigMgr-Certificate-Profiles-Wizard-Supported-Platforms.png)</span><span class="sxs-lookup"><span data-stu-id="33ace-127">Choose **Select all** for Supported Platforms ![Supported platforms](../media/ManagingDevices/ConfigMgr-Certificate-Profiles-Wizard-Supported-Platforms.png)</span></span>

10. <span data-ttu-id="33ace-128">**요약, 다음, 닫기** 를 차례로 클릭 하 여 마법사를 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="33ace-128">Click **Summary, Next, and Close** to exit the wizard.</span></span>

11. <span data-ttu-id="33ace-129">앞서 만든 프로필을 마우스 오른쪽 단추로 클릭 하 고 **내보내기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="33ace-129">Right-click on the profile just created and click **Export**.</span></span>

12. <span data-ttu-id="33ace-130">**찾아보기**를 클릭 하 고 파일을 내보낼 위치를 찾은 다음 **저장**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="33ace-130">Click **Browse**, find a location where the .ppkg file should be exported, and then click **Save**.</span></span>

13. <span data-ttu-id="33ace-131">**내보내기** 를 클릭 하 고 **확인** 을 클릭 하 여 마법사를 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="33ace-131">Click **Export** and click **OK** to exit the wizard.</span></span>

#### <a name="other-mdm-servers"></a><span data-ttu-id="33ace-132">기타 MDM 서버</span><span class="sxs-lookup"><span data-stu-id="33ace-132">Other MDM Servers</span></span>

1. <span data-ttu-id="33ace-133">Windows [ADK (평가 및 배포 키트)](https://developer.microsoft.com/windows/hardware/windows-assessment-deployment-kit)를 다운로드 하 여 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="33ace-133">Download and install the [Windows Assessment and Deployment Kit (Windows ADK)](https://developer.microsoft.com/windows/hardware/windows-assessment-deployment-kit).</span></span>

2. <span data-ttu-id="33ace-134">Windows 이미징 및 구성 디자이너 (WICD)를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="33ace-134">Open Windows Imaging and Configuration Designer (WICD).</span></span>
   <span data-ttu-id="33ace-135">Windows 이미징 및 구성 디자이너를 ![](../media/ManagingDevices/WICD-Start-Page.png)</span><span class="sxs-lookup"><span data-stu-id="33ace-135">![Windows Imaging and Configuration Designer](../media/ManagingDevices/WICD-Start-Page.png)</span></span>

3. <span data-ttu-id="33ace-136">**고급 프로 비전** 선택</span><span class="sxs-lookup"><span data-stu-id="33ace-136">Choose **Advanced Provisioning**</span></span>

4. <span data-ttu-id="33ace-137">패키지의 이름을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="33ace-137">Set a name for your package.</span></span>

5. <span data-ttu-id="33ace-138">Windows 10 IoT Core에 공통적인 설정을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="33ace-138">Choose settings common to Windows 10 IoT Core.</span></span>

6. <span data-ttu-id="33ace-139">패키지 가져오기 단계를 건너뜁니다.</span><span class="sxs-lookup"><span data-stu-id="33ace-139">Skip the Import Package step.</span></span>
   <span data-ttu-id="33ace-140">![WICD](../media/ManagingDevices/WICD-Advanced-Provisioning-New-Project-Details.PNG) 
   ![WICD](../media/ManagingDevices/WICD-Advanced-Provisioning-New-Project-Editions.PNG) 
   ![WICD-새 프로젝트-가져오기-프로젝트-가져오기](../media/ManagingDevices/WICD-Advanced-Provisioning-New-Project-Import.PNG)</span><span class="sxs-lookup"><span data-stu-id="33ace-140">![WICD-New-Project-Details](../media/ManagingDevices/WICD-Advanced-Provisioning-New-Project-Details.PNG) 
![WICD-New-Project-Editions](../media/ManagingDevices/WICD-Advanced-Provisioning-New-Project-Editions.PNG) 
![WICD-New-Project-Import](../media/ManagingDevices/WICD-Advanced-Provisioning-New-Project-Import.PNG)</span></span>

7. <span data-ttu-id="33ace-141">작업 공간-> 등록로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="33ace-141">Navigate to Workplace -> Enrollments.</span></span>

8. <span data-ttu-id="33ace-142">UPN 필드에서 장치를 등록 하려는 계정 (예: trmck@contoso.co)을 입력 하 고 **추가**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="33ace-142">In the UPN field enter the account you wish to enroll your device under (i.e. trmck@contoso.co) and click **Add**.</span></span>

   ![작업 공간 등록 채우기](../media/ManagingDevices/WICD-Workplace-Enrollments-UPN-Filled.png)

9. <span data-ttu-id="33ace-144">AuthPolicy의 경우 사용자 이름으로 OnPremises (암호 기반 인증) 또는 인증서 기반 인증 중 하나를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="33ace-144">For AuthPolicy choose between Username Password based authentication (OnPremises) or Certificate based authentication.</span></span>

10. <span data-ttu-id="33ace-145">MDM 서버에 대 한 검색 서비스 URL을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="33ace-145">Enter the Discovery Service URL for your MDM server.</span></span>

> [!NOTE]
> <span data-ttu-id="33ace-146">등록 서비스 URL 및 정책 서비스 URL은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="33ace-146">Enrollment Service URL and Policy Service URL are optional.</span></span>

11. <span data-ttu-id="33ace-147">비밀을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="33ace-147">For the Secret enter</span></span>  
    - <span data-ttu-id="33ace-148">OnPremises: 등록 하는 계정의 암호</span><span class="sxs-lookup"><span data-stu-id="33ace-148">OnPremises: The password for the account you're enrolling with</span></span>  
    - <span data-ttu-id="33ace-149">Certificate: 인증서의 손 도장 (thumbprint)</span><span class="sxs-lookup"><span data-stu-id="33ace-149">Certificate: The thumbprint of the certificate</span></span>
    
    ![채워진 온-프레미스](../media/ManagingDevices/WICD-Workplace-Enrollments-UPN-Details-Filled-Premise.png)  

12. <span data-ttu-id="33ace-151">WICD 창 맨 위에서 **내보내기 > 프로 비전 패키지**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="33ace-151">At the top of WICD window click **Export > Provisioning package**.</span></span>

13. <span data-ttu-id="33ace-152">패키지의 이름 및 버전을 입력 하 고 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="33ace-152">Provide a name and version for your package and click **Next**.</span></span> 

> [!NOTE]
> <span data-ttu-id="33ace-153">업데이트 된 패키지가 실행 되도록 버전 번호를 증분 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="33ace-153">Be sure to increment the version number to ensure an updated package is executed.</span></span>

14. <span data-ttu-id="33ace-154">**보안 정보 페이지**에서 **다음** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="33ace-154">Click **Next** on the **security details page**.</span></span>

15. <span data-ttu-id="33ace-155">로컬 컴퓨터에서 패키지를 내보낼 위치를 선택 하 고 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="33ace-155">Choose the location where the package is to be exported on the local machine and click **Next**.</span></span>

16. <span data-ttu-id="33ace-156">**빌드** 를 클릭 한 다음 **마침** 을 클릭 하 여 마법사를 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="33ace-156">Click **Build** and then **Finish** to exit the wizard.</span></span>

### <a name="installing-the-provisioning-package"></a><span data-ttu-id="33ace-157">프로 비전 패키지를 설치 하는 중</span><span class="sxs-lookup"><span data-stu-id="33ace-157">Installing the Provisioning package</span></span>

<span data-ttu-id="33ace-158">프로 비전 패키지를 IoT 장치에 배포 하는 방법에는 몇 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33ace-158">There are a few ways in which a Provisioning package can be deployed to an IoT device.</span></span> <span data-ttu-id="33ace-159">패키지를 장치에 복사 하거나 이미징 프로세스 중에 패키지를 이미지에 추가 하 여 패키지를 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33ace-159">It is possible to deploy a package by copying the package to the device or adding the package to the image during the imaging process.</span></span>

#### <a name="copying-package-to-device"></a><span data-ttu-id="33ace-160">장치에 패키지를 복사 하는 중</span><span class="sxs-lookup"><span data-stu-id="33ace-160">Copying package to device</span></span>

<span data-ttu-id="33ace-161">SCCM 또는 WICD에서 내보낸 프로 비전 패키지를 가져와. n a p kg 파일을 IoT 장치의 `C:\Windows\Provisioning\Packages` 디렉터리에 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="33ace-161">Take the Provisioning package that was exported from SCCM or WICD and copy the .ppkg file to `C:\Windows\Provisioning\Packages` directory on the IoT device.</span></span> <span data-ttu-id="33ace-162">장치를 다시 부팅 하면 패키지가 실행 되 고 장치에서 등록 프로세스가 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="33ace-162">Upon reboot of the device the package will be executed and the device will start the enrollment process.</span></span>

#### <a name="adding-package-to-image"></a><span data-ttu-id="33ace-163">이미지에 패키지 추가</span><span class="sxs-lookup"><span data-stu-id="33ace-163">Adding package to image</span></span>

<span data-ttu-id="33ace-164">[이미지에 프로 비전 패키지 추가](https://docs.microsoft.com/windows-hardware/manufacture/iot/add-a-provisioning-package-to-an-image)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="33ace-164">See [Add a provisioning package to an image](https://docs.microsoft.com/windows-hardware/manufacture/iot/add-a-provisioning-package-to-an-image).</span></span> <span data-ttu-id="33ace-165">처음 부팅 될 때 장치는 패키지를 실행 하 고 등록 프로세스를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="33ace-165">Upon first boot the device will execute the package and start the enrollment process.</span></span>
