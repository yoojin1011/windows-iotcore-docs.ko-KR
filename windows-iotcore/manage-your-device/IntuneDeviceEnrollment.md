---
title: Intune에 Windows IoT Core 장치 등록
author: msmimart
ms.author: mimart
ms.date: 05/08/2018
ms.topic: article
description: Microsoft Intune 장치 관리 및 Windows IoT를 사용 하 여 장치를 관리 하는 방법에 대해 알아봅니다.
keywords: windows iot, Azure IoT, Intune 장치 관리, 장치 관리
ms.openlocfilehash: 6a82eab36882e6e2cac830e711b2bba6d4fc95bb
ms.sourcegitcommit: 58f66754eecff826756b686b202c8e21d658bb9d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/20/2019
ms.locfileid: "67277800"
---
# <a name="enrolling-windows-iot-core-devices-in-microsoft-intune"></a><span data-ttu-id="0e4ce-104">Microsoft Intune에서 Windows IoT Core 장치 등록</span><span class="sxs-lookup"><span data-stu-id="0e4ce-104">Enrolling Windows IoT Core devices in Microsoft Intune</span></span>

<span data-ttu-id="0e4ce-105">회사는 다른 모든 관리 되는 장치와 함께 IoT Core 장치를 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e4ce-105">Your company can manage IoT Core devices alongside all of your other managed devices.</span></span> <span data-ttu-id="0e4ce-106">이렇게 하면 Intune을 사용 하 여 IoT Core, IoT Enterprise 및 기타 Windows 장치를 관리 하는 일관 된 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e4ce-106">This gives you a consistent way to manage IoT Core, IoT Enterprise, and other Windows devices using Intune.</span></span>

## <a name="how-do-i-enroll-an-iot-core-device-into-intune"></a><span data-ttu-id="0e4ce-107">Intune에 IoT Core 장치를 등록 어떻게 할까요? 있나요?</span><span class="sxs-lookup"><span data-stu-id="0e4ce-107">How do I enroll an IoT Core device into Intune?</span></span>

<span data-ttu-id="0e4ce-108">Windows IoT core 대시보드를 사용 하 여 장치를 준비한 다음 Windows 구성 디자이너를 사용 하 여 프로 비전 패키지를 만들면 IoT Core 장치의 Intune 등록을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e4ce-108">Intune enrollment of an IoT Core device is accomplished by using the Windows IoT Core Dashboard to prepare the device, and then using Windows Configuration Designer to create a provisioning package.</span></span>

### <a name="change-the-intune-mdm-user-scope-in-azure-ad"></a><span data-ttu-id="0e4ce-109">Azure AD에서 Intune MDM 사용자 범위 변경</span><span class="sxs-lookup"><span data-stu-id="0e4ce-109">Change the Intune MDM user scope in Azure AD</span></span>

1. <span data-ttu-id="0e4ce-110">[Azure Portal](https://portal.azure.com)에 로그인 한 다음 **Azure Active Directory**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e4ce-110">Sign in to the [Azure portal](https://portal.azure.com), and then select **Azure Active Directory**.</span></span>
2. <span data-ttu-id="0e4ce-111">**모바일 (MDM 및 MAM)** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e4ce-111">Select **Mobility (MDM and MAM)**.</span></span>

     ![이동성 및 Microsoft Intune 선택](../media/IntuneDeviceEnrollment/iot-ap-mobility-intune.png)

3. <span data-ttu-id="0e4ce-113">**Microsoft Intune**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e4ce-113">Select **Microsoft Intune**.</span></span> <span data-ttu-id="0e4ce-114">**Microsoft Intune 구성** 페이지에서 **MDM 사용자 범위**옆의 **모두**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e4ce-114">On the **Configure Microsoft Intune** page, next to **MDM user scope**, select **All**.</span></span> <span data-ttu-id="0e4ce-115">이렇게 하면 Azure AD에 가입한 후에 IoT Core 장치 사용자를 Intune에 등록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e4ce-115">This will allow your IoT Core device user to be enrolled in Intune after joining Azure AD.</span></span>

### <a name="create-a-setup-sd-card-for-the-iot-core-device"></a><span data-ttu-id="0e4ce-116">IoT Core 장치에 대 한 설치 SD 카드 만들기</span><span class="sxs-lookup"><span data-stu-id="0e4ce-116">Create a setup SD card for the IoT Core device</span></span>

1. <span data-ttu-id="0e4ce-117">PC의 카드 판독기에 마이크로 Sd 카드를 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e4ce-117">Insert a microSD card into the card reader on your PC.</span></span>
     > [!NOTE]
     > <span data-ttu-id="0e4ce-118">마이크로 Sd 카드는이 프로세스 중에 포맷 되므로 카드의 모든 데이터가 삭제 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0e4ce-118">The microSD card will be formatted during this process, so any data on the card will be deleted.</span></span>
2. <span data-ttu-id="0e4ce-119">[Windows IoT Core 대시보드](https://docs.microsoft.com/windows/iot-core/connect-your-device/iotdashboard) 로 이동 하 여 대시보드를 다운로드 하 고 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e4ce-119">Go to [Windows IoT Core Dashboard](https://docs.microsoft.com/windows/iot-core/connect-your-device/iotdashboard) to download and install the dashboard.</span></span>
3. <span data-ttu-id="0e4ce-120">대시보드를 설치한 후 열고 **새 장치 설정**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e4ce-120">After the dashboard installs, open it and select **Set up a new device**.</span></span>

     ![Windows IoT Core 대시보드](../media/IntuneDeviceEnrollment/IoT-dashboard-my-devices.png)

4. <span data-ttu-id="0e4ce-122">**장치 이름을**입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e4ce-122">Type a **Device name**.</span></span>
5. <span data-ttu-id="0e4ce-123">새 관리자 암호를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e4ce-123">Enter a new administrator password.</span></span>
6. <span data-ttu-id="0e4ce-124">장치에 Wi-fi를 사용 하도록 설정 하려면 **Wi-fi 네트워크 연결** 확인란을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e4ce-124">If you want to enable Wi-Fi for the device, select the **Wi-Fi Network Connection** checkbox.</span></span> <span data-ttu-id="0e4ce-125">장치에서 이더넷 네트워크 연결만 사용 하는 경우이를 건너뜁니다.</span><span class="sxs-lookup"><span data-stu-id="0e4ce-125">Skip this if the device will use an ethernet network connection only.</span></span>

     ![IoT 대시보드의 wi-fi 확인란](../media/IntuneDeviceEnrollment/IoT-dashboard-wifi-connection.png)

7. <span data-ttu-id="0e4ce-127">**소프트웨어 사용 조건에 동의** 함 확인란을 선택 하 고 **다운로드 및 설치**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e4ce-127">Select the **I accept the software license terms** checkbox, and then select **Download and Install**.</span></span>
8. <span data-ttu-id="0e4ce-128">확인 메시지가 표시 되 면 SD 카드의 **형식을 지정** 하는 옵션을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e4ce-128">When the confirmation message appears, select the option to **Format** the SD Card.</span></span>
     > [!NOTE]
     > <span data-ttu-id="0e4ce-129">설치 중에 **형식** 확인 메시지를 봅니다.</span><span class="sxs-lookup"><span data-stu-id="0e4ce-129">Watch for the **Format** confirmation message during setup.</span></span> <span data-ttu-id="0e4ce-130">다른 열려 있는 응용 프로그램에서 메시지를 숨길 수 있지만 서식 옵션을 선택 하는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e4ce-130">The message could be hidden by another open application, but it’s important to select the Format option.</span></span> <span data-ttu-id="0e4ce-131">드라이브가 올바르게 포맷 되지 않은 경우 부팅이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e4ce-131">If the drive isn't properly formatted, boot will fail.</span></span>
9. <span data-ttu-id="0e4ce-132">**SD 카드가 준비 되었습니다** . 라는 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="0e4ce-132">The message **Your SD card is ready** appears.</span></span>

     ![SD 카드 준비 메시지](../media/IntuneDeviceEnrollment/IoT-dashboard-sd-card-ready.png)

10. <span data-ttu-id="0e4ce-134">이 페이지를 최소화 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e4ce-134">Minimize this page.</span></span>  <span data-ttu-id="0e4ce-135">나중에 다시 돌아올 것입니다.</span><span class="sxs-lookup"><span data-stu-id="0e4ce-135">You'll come back to it later.</span></span>

### <a name="create-a-provisioning-package-for-intune-enrollment"></a><span data-ttu-id="0e4ce-136">Intune 등록을 위한 프로 비전 패키지 만들기</span><span class="sxs-lookup"><span data-stu-id="0e4ce-136">Create a provisioning package for Intune enrollment</span></span>

1. <span data-ttu-id="0e4ce-137">Windows [구성 디자이너 설치](https://docs.microsoft.com/windows/configuration/provisioning-packages/provisioning-install-icd)의 단계에 따라 Windows 구성 디자인 앱을 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e4ce-137">Install the Windows Configuration Design app by following the steps in [Install Windows Configuration Designer](https://docs.microsoft.com/windows/configuration/provisioning-packages/provisioning-install-icd).</span></span>

2. <span data-ttu-id="0e4ce-138">**Windows 이미징 및 구성 디자이너**를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="0e4ce-138">Open the **Windows Imaging and Configuration Designer**.</span></span>
3. <span data-ttu-id="0e4ce-139">**데스크톱 장치 프로 비전** 을 선택 하 여 프로젝트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0e4ce-139">Choose **Provision desktop devices** to create a project.</span></span>

     ![데스크톱 서비스 프로 비전 선택](../media/IntuneDeviceEnrollment/iot-wcd-provision-desktop-devices.png)

4. <span data-ttu-id="0e4ce-141">**프로젝트 세부 정보** 를 원하는 대로 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e4ce-141">Enter the **Project Details** as desired.</span></span> <span data-ttu-id="0e4ce-142">그런 다음 **마침**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e4ce-142">Then select **Finish**.</span></span>
5. <span data-ttu-id="0e4ce-143">**계정 관리** 페이지로 이동 하 여 **Azure AD에 등록**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e4ce-143">Go to the **Account Management** page and select **Enroll in Azure AD**.</span></span>
     > [!NOTE]
     > <span data-ttu-id="0e4ce-144">Microsoft Store 또는 Windows ADK (평가 및 배포 키트)에서 앱을 설치 하는 것은 좋은 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="0e4ce-144">Installing the app from either the Microsoft Store or the Windows Assessment and Deployment Kit (ADK) is fine.</span></span>

     ![Azure AD에서 등록 선택](../media/IntuneDeviceEnrollment/iot-wcd-enroll-in-azure-ad.png)

6. <span data-ttu-id="0e4ce-146">**대량 토큰 만료**옆에 대량 토큰 만료 날짜를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e4ce-146">Next to **Bulk Token Expiry**, enter a bulk token expiry date.</span></span>
7. <span data-ttu-id="0e4ce-147">**대량 토큰 가져오기**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e4ce-147">Select **Get Bulk Token**.</span></span> <span data-ttu-id="0e4ce-148">Azure AD에 연결 하기 위한 로그인 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0e4ce-148">A sign-in message appears for connecting to Azure AD.</span></span>

     ![Azure AD 로그인 페이지](../media/IntuneDeviceEnrollment/iot-wcd-sign-in.png)

8. <span data-ttu-id="0e4ce-150">테 넌 트 사용자 이름 (예: john@mycompany.onmicrosoft.com)과 암호를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e4ce-150">Enter your tenant username (for example, john@mycompany.onmicrosoft.com) and your password.</span></span>
9. <span data-ttu-id="0e4ce-151">Windows 구성 디자인 앱이 Azure AD 정보에 액세스할 수 있도록 동의 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e4ce-151">Agree to allow the Windows Configuration Design app to access your Azure AD information.</span></span>
10. <span data-ttu-id="0e4ce-152">페이지의 메시지는 대량 AAD 토큰이 성공적으로 인출 되었음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0e4ce-152">A message on the page shows that the Bulk AAD token was fetched successfully.</span></span>

     ![대량 토큰 성공 메시지](../media/IntuneDeviceEnrollment/iot-wcd-bulk-token-successful.png)

11. <span data-ttu-id="0e4ce-154">**고급 편집기로 전환**을 선택 하 고 *예*를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e4ce-154">Select **Switch to advanced editor**, and then select *Yes*.</span></span>

     ![고급 편집기로 전환 확인 페이지](../media/IntuneDeviceEnrollment/iot-wcd-switch-to-advanced-editor.png)

12. <span data-ttu-id="0e4ce-156">**선택한 사용자 지정**에서 **계정** 설정을 그대로 두고 다른 모든 설정을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e4ce-156">Under **Selected customizations**, Leave the **Account** settings, but remove all other settings:</span></span>
13. <span data-ttu-id="0e4ce-157">**OOBE**를 선택 하 고 **제거**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e4ce-157">Select **OOBE**, and then select **Remove**.</span></span>
14. <span data-ttu-id="0e4ce-158">**Sharedpc** 가 표시 되 면 선택 하 고 **제거**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e4ce-158">If **SharedPC** is listed, select it, and then select **Remove**.</span></span>

     ![사용자 지정 제거](../media/IntuneDeviceEnrollment/iot-wcd-select-customizations.png)

15. <span data-ttu-id="0e4ce-160">**내보내기**를 선택한 다음 **프로 비전 패키지**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e4ce-160">Select **Export**, and then choose **Provisioning package**.</span></span>

     ![프로 비전 패키지 선택](../media/IntuneDeviceEnrollment/iot-wcd-export-provisioning-package.png)

16. <span data-ttu-id="0e4ce-162">다음 페이지에서 기본 설정을 그대로 적용 하 고 **다음**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e4ce-162">On the next page, accept the default settings and select **Next**.</span></span>
17. <span data-ttu-id="0e4ce-163">다시, 다음 페이지에서 기본 설정을 그대로 적용 하 고 다음을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e4ce-163">Again, on the next page, accept the default settings and select Next.</span></span>
18. <span data-ttu-id="0e4ce-164">**프로 비전 패키지** 대상을 변경 하거나 기본 경로를 그대로 두고 **다음**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e4ce-164">Change the **Provisioning Package** destination or leave the default path, and then select **Next**.</span></span>
19. <span data-ttu-id="0e4ce-165">**빌드**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e4ce-165">Select **Build**.</span></span>
20. <span data-ttu-id="0e4ce-166">준비가 되 면 파일을 찾을 수 있도록 **출력 위치** 링크를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e4ce-166">Select the **Output Location** link so that you can locate the .ppkg file when it's ready.</span></span>

     ![출력 위치 링크](../media/IntuneDeviceEnrollment/iot-wcd-all-done.png)

21. <span data-ttu-id="0e4ce-168">**마침**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e4ce-168">Select **Finish**.</span></span>
22. <span data-ttu-id="0e4ce-169">파일 탐색기로 이동 하 여 프로 비전 패키지를 IoT Core 장치에 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e4ce-169">Go to File Explorer and copy the provisioning package to your IoT Core device.</span></span> <span data-ttu-id="0e4ce-170">**C:\windows\provisioning\packages** 폴더의 **mainos** 드라이브 아래 마이크로 sd 카드에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e4ce-170">Save it to the microSD card under the **MainOS** drive in the **c:\windows\provisioning\packages** folder.</span></span>  <span data-ttu-id="0e4ce-171">이 폴더에 파일을 저장할 수 있는 권한을 부여 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e4ce-171">You'll have to grant permissions to save the file in this folder.</span></span>

### <a name="provision-and-enroll-the-iot-core-device-in-intune"></a><span data-ttu-id="0e4ce-172">Intune에서 IoT Core 장치 프로 비전 및 등록</span><span class="sxs-lookup"><span data-stu-id="0e4ce-172">Provision and enroll the IoT Core device in Intune</span></span>

1. <span data-ttu-id="0e4ce-173">IoT Core 장치에 마이크로 Sd 카드를 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e4ce-173">Insert the microSD card into your IoT Core device.</span></span>
2. <span data-ttu-id="0e4ce-174">IoT Core 장치를 켜고 시작 하는 시간을 허용 하 고 표준 화면을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e4ce-174">Turn on your IoT Core device and allow time for it to start up and display the standard screen.</span></span>
3. <span data-ttu-id="0e4ce-175">Azure Portal의 Microsoft Intune 콘솔로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="0e4ce-175">Return to the Microsoft Intune console in the Azure portal.</span></span> <span data-ttu-id="0e4ce-176">장치가 장치 목록에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0e4ce-176">Your device should appear in the list of devices.</span></span>
     > [!NOTE]
     > <span data-ttu-id="0e4ce-177">등록을 완료 하는 데 15 분 이상이 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e4ce-177">Enrollment could take 15 minutes or more to complete.</span></span>

     ![Intune 장치 목록](../media/IntuneDeviceEnrollment/iot-ap-devices-after-enrollment.png)

## <a name="next-steps"></a><span data-ttu-id="0e4ce-179">다음 단계</span><span class="sxs-lookup"><span data-stu-id="0e4ce-179">Next steps</span></span>

- <span data-ttu-id="0e4ce-180">[Intune의 장치 세부 정보를 참조 하세요](https://docs.microsoft.com/intune/device-inventory).</span><span class="sxs-lookup"><span data-stu-id="0e4ce-180">[See device details in Intune](https://docs.microsoft.com/intune/device-inventory).</span></span>
- <span data-ttu-id="0e4ce-181">[장치를 동기화 하 여 Intune에서 최신 정책과 작업을 가져옵니다](https://docs.microsoft.com/intune/device-sync).</span><span class="sxs-lookup"><span data-stu-id="0e4ce-181">[Sync the device to get the latest policies and actions with Intune](https://docs.microsoft.com/intune/device-sync).</span></span>
- <span data-ttu-id="0e4ce-182">[Intune을 사용 하 여 장치를 원격으로 다시 시작](https://docs.microsoft.com/intune/device-restart)합니다.</span><span class="sxs-lookup"><span data-stu-id="0e4ce-182">[Remotely restart the device with Intune](https://docs.microsoft.com/intune/device-restart).</span></span>
