---
title: Intune에서 Windows IoT Core 장치 등록
author: msmimart
ms.author: mimart
ms.date: 05/08/2018
ms.topic: article
description: Microsoft Intune 장치 관리 및 Windows IoT를 사용 하 여 장치를 관리 하는 방법에 알아봅니다.
keywords: windows iot, Azure IoT 장치를 Intune에서 관리 장치 관리
ms.openlocfilehash: 6a82eab36882e6e2cac830e711b2bba6d4fc95bb
ms.sourcegitcommit: 58f66754eecff826756b686b202c8e21d658bb9d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/20/2019
ms.locfileid: "67277800"
---
# <a name="enrolling-windows-iot-core-devices-in-microsoft-intune"></a><span data-ttu-id="1359b-104">Microsoft Intune에서 Windows IoT Core 장치 등록</span><span class="sxs-lookup"><span data-stu-id="1359b-104">Enrolling Windows IoT Core devices in Microsoft Intune</span></span>

<span data-ttu-id="1359b-105">회사는 다른 관리 되는 장치를 모두 함께 IoT Core 장치를 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1359b-105">Your company can manage IoT Core devices alongside all of your other managed devices.</span></span> <span data-ttu-id="1359b-106">이렇게 하면 일관 된 방식으로 IoT Core, IoT Enterprise 및 Intune을 사용 하 여 다른 Windows 장치를 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1359b-106">This gives you a consistent way to manage IoT Core, IoT Enterprise, and other Windows devices using Intune.</span></span>

## <a name="how-do-i-enroll-an-iot-core-device-into-intune"></a><span data-ttu-id="1359b-107">IoT Core 장치를 Intune에 등록 하려면 어떻게 해야 하나요?</span><span class="sxs-lookup"><span data-stu-id="1359b-107">How do I enroll an IoT Core device into Intune?</span></span>

<span data-ttu-id="1359b-108">IoT Core 장치를 Intune 등록 Windows IoT Core 대시보드를 사용 하 여 장치를 준비 하 고 프로 비전 패키지를 만드는 Windows 구성 디자이너를 사용 하 여 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1359b-108">Intune enrollment of an IoT Core device is accomplished by using the Windows IoT Core Dashboard to prepare the device, and then using Windows Configuration Designer to create a provisioning package.</span></span>

### <a name="change-the-intune-mdm-user-scope-in-azure-ad"></a><span data-ttu-id="1359b-109">Azure AD에서 Intune MDM 사용자 범위를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="1359b-109">Change the Intune MDM user scope in Azure AD</span></span>

1. <span data-ttu-id="1359b-110">에 로그인 합니다 [Azure portal](https://portal.azure.com)를 선택한 후 **Azure Active Directory**합니다.</span><span class="sxs-lookup"><span data-stu-id="1359b-110">Sign in to the [Azure portal](https://portal.azure.com), and then select **Azure Active Directory**.</span></span>
2. <span data-ttu-id="1359b-111">선택 **이동성 (MDM 및 MAM)** 합니다.</span><span class="sxs-lookup"><span data-stu-id="1359b-111">Select **Mobility (MDM and MAM)**.</span></span>

     ![선택한 모바일 및 Microsoft Intune](../media/IntuneDeviceEnrollment/iot-ap-mobility-intune.png)

3. <span data-ttu-id="1359b-113">선택 **Microsoft Intune**합니다.</span><span class="sxs-lookup"><span data-stu-id="1359b-113">Select **Microsoft Intune**.</span></span> <span data-ttu-id="1359b-114">에 **Microsoft Intune 구성** 페이지 옆에 **MDM 사용자 범위**를 선택 **모든**합니다.</span><span class="sxs-lookup"><span data-stu-id="1359b-114">On the **Configure Microsoft Intune** page, next to **MDM user scope**, select **All**.</span></span> <span data-ttu-id="1359b-115">이렇게 하면 프로그램 IoT Core 장치 사용자는 Azure AD에 가입한 후 Intune에 등록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1359b-115">This will allow your IoT Core device user to be enrolled in Intune after joining Azure AD.</span></span>

### <a name="create-a-setup-sd-card-for-the-iot-core-device"></a><span data-ttu-id="1359b-116">IoT Core 장치에 대 한 설치 SD 카드 만들기</span><span class="sxs-lookup"><span data-stu-id="1359b-116">Create a setup SD card for the IoT Core device</span></span>

1. <span data-ttu-id="1359b-117">PC에서 카드 판독기에 microSD 카드를 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="1359b-117">Insert a microSD card into the card reader on your PC.</span></span>
     > [!NOTE]
     > <span data-ttu-id="1359b-118">MicroSD 카드를 카드에 데이터를 삭제할 수는이 과정에서 포맷 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1359b-118">The microSD card will be formatted during this process, so any data on the card will be deleted.</span></span>
2. <span data-ttu-id="1359b-119">로 이동 [Windows IoT Core 대시보드](https://docs.microsoft.com/windows/iot-core/connect-your-device/iotdashboard) 다운로드 하 고 대시보드를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="1359b-119">Go to [Windows IoT Core Dashboard](https://docs.microsoft.com/windows/iot-core/connect-your-device/iotdashboard) to download and install the dashboard.</span></span>
3. <span data-ttu-id="1359b-120">대시보드를 설치한 후 열고 선택 **새 장치 설정**합니다.</span><span class="sxs-lookup"><span data-stu-id="1359b-120">After the dashboard installs, open it and select **Set up a new device**.</span></span>

     ![Windows IoT Core 대시보드](../media/IntuneDeviceEnrollment/IoT-dashboard-my-devices.png)

4. <span data-ttu-id="1359b-122">입력 **장치 이름**합니다.</span><span class="sxs-lookup"><span data-stu-id="1359b-122">Type a **Device name**.</span></span>
5. <span data-ttu-id="1359b-123">새 관리자 암호를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="1359b-123">Enter a new administrator password.</span></span>
6. <span data-ttu-id="1359b-124">장치의 Wi-fi를 사용 하도록 설정 하려는 경우 선택 합니다 **Wi-fi 네트워크 연결** 확인란을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="1359b-124">If you want to enable Wi-Fi for the device, select the **Wi-Fi Network Connection** checkbox.</span></span> <span data-ttu-id="1359b-125">장치는 이더넷 네트워크 연결에만 사용 하는 경우이 건너뜁니다.</span><span class="sxs-lookup"><span data-stu-id="1359b-125">Skip this if the device will use an ethernet network connection only.</span></span>

     ![IoT 대시보드에서 Wi-fi 확인란](../media/IntuneDeviceEnrollment/IoT-dashboard-wifi-connection.png)

7. <span data-ttu-id="1359b-127">선택 된 **소프트웨어 라이선스 조건에 동의** 확인란을 선택한 후 **다운로드 및 설치**합니다.</span><span class="sxs-lookup"><span data-stu-id="1359b-127">Select the **I accept the software license terms** checkbox, and then select **Download and Install**.</span></span>
8. <span data-ttu-id="1359b-128">옵션을 선택 하는 확인 메시지가 나타나면 **형식** SD 카드.</span><span class="sxs-lookup"><span data-stu-id="1359b-128">When the confirmation message appears, select the option to **Format** the SD Card.</span></span>
     > [!NOTE]
     > <span data-ttu-id="1359b-129">감시 합니다 **형식** 설치 하는 동안 확인 메시지입니다.</span><span class="sxs-lookup"><span data-stu-id="1359b-129">Watch for the **Format** confirmation message during setup.</span></span> <span data-ttu-id="1359b-130">다른 열린 응용 프로그램에서 메시지를 숨길 수 없습니다 하지만 형식 옵션을 선택 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1359b-130">The message could be hidden by another open application, but it’s important to select the Format option.</span></span> <span data-ttu-id="1359b-131">드라이브를 포맷 제대로 되지 부팅 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="1359b-131">If the drive isn't properly formatted, boot will fail.</span></span>
9. <span data-ttu-id="1359b-132">메시지 **Your SD 카드가 준비** 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="1359b-132">The message **Your SD card is ready** appears.</span></span>

     ![SD 카드에 대 한 준비 메시지](../media/IntuneDeviceEnrollment/IoT-dashboard-sd-card-ready.png)

10. <span data-ttu-id="1359b-134">이 페이지를 최소화 합니다.</span><span class="sxs-lookup"><span data-stu-id="1359b-134">Minimize this page.</span></span>  <span data-ttu-id="1359b-135">에서는 다시 뵙 되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="1359b-135">You'll come back to it later.</span></span>

### <a name="create-a-provisioning-package-for-intune-enrollment"></a><span data-ttu-id="1359b-136">Intune 등록에 대 한 프로 비전 패키지 만들기</span><span class="sxs-lookup"><span data-stu-id="1359b-136">Create a provisioning package for Intune enrollment</span></span>

1. <span data-ttu-id="1359b-137">단계를 수행 하 여 Windows 구성 디자인 앱을 설치할 [Windows 구성 디자이너 설치](https://docs.microsoft.com/windows/configuration/provisioning-packages/provisioning-install-icd)합니다.</span><span class="sxs-lookup"><span data-stu-id="1359b-137">Install the Windows Configuration Design app by following the steps in [Install Windows Configuration Designer](https://docs.microsoft.com/windows/configuration/provisioning-packages/provisioning-install-icd).</span></span>

2. <span data-ttu-id="1359b-138">엽니다는 **Windows 이미징 및 구성 디자이너**합니다.</span><span class="sxs-lookup"><span data-stu-id="1359b-138">Open the **Windows Imaging and Configuration Designer**.</span></span>
3. <span data-ttu-id="1359b-139">선택할 **데스크톱 장치를 프로 비전** 프로젝트를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1359b-139">Choose **Provision desktop devices** to create a project.</span></span>

     ![프로 비전 데스크톱 서비스를 선택합니다.](../media/IntuneDeviceEnrollment/iot-wcd-provision-desktop-devices.png)

4. <span data-ttu-id="1359b-141">입력 된 **프로젝트 세부 정보** 필요에 따라 합니다.</span><span class="sxs-lookup"><span data-stu-id="1359b-141">Enter the **Project Details** as desired.</span></span> <span data-ttu-id="1359b-142">선택한 **완료**합니다.</span><span class="sxs-lookup"><span data-stu-id="1359b-142">Then select **Finish**.</span></span>
5. <span data-ttu-id="1359b-143">로 이동 합니다 **계정 관리** 선택한 페이지 **Azure AD에 등록**합니다.</span><span class="sxs-lookup"><span data-stu-id="1359b-143">Go to the **Account Management** page and select **Enroll in Azure AD**.</span></span>
     > [!NOTE]
     > <span data-ttu-id="1359b-144">Microsoft Store 또는 Windows 평가 및 배포 키트 (ADK) 중 하나에서 앱을 설치 해도 괜찮습니다.</span><span class="sxs-lookup"><span data-stu-id="1359b-144">Installing the app from either the Microsoft Store or the Windows Assessment and Deployment Kit (ADK) is fine.</span></span>

     ![Azure AD에 등록 선택](../media/IntuneDeviceEnrollment/iot-wcd-enroll-in-azure-ad.png)

6. <span data-ttu-id="1359b-146">옆에 **대량 토큰 만료**, 대량 토큰 만료 날짜를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="1359b-146">Next to **Bulk Token Expiry**, enter a bulk token expiry date.</span></span>
7. <span data-ttu-id="1359b-147">선택 **대량 토큰 가져오기**합니다.</span><span class="sxs-lookup"><span data-stu-id="1359b-147">Select **Get Bulk Token**.</span></span> <span data-ttu-id="1359b-148">Azure AD에 연결 하는 것에 대 한 로그인 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1359b-148">A sign-in message appears for connecting to Azure AD.</span></span>

     ![Azure AD 로그인 페이지](../media/IntuneDeviceEnrollment/iot-wcd-sign-in.png)

8. <span data-ttu-id="1359b-150">테 넌 트 사용자 이름을 입력 (예를 들어 john@mycompany.onmicrosoft.com) 및 암호입니다.</span><span class="sxs-lookup"><span data-stu-id="1359b-150">Enter your tenant username (for example, john@mycompany.onmicrosoft.com) and your password.</span></span>
9. <span data-ttu-id="1359b-151">Windows 구성 디자인 응용 프로그램에서 Azure AD 정보에 액세스할 수 있도록 동의 합니다.</span><span class="sxs-lookup"><span data-stu-id="1359b-151">Agree to allow the Windows Configuration Design app to access your Azure AD information.</span></span>
10. <span data-ttu-id="1359b-152">페이지의 메시지를 대량 AAD 토큰을 성공적으로 가져온 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1359b-152">A message on the page shows that the Bulk AAD token was fetched successfully.</span></span>

     ![대량 토큰 성공 메시지](../media/IntuneDeviceEnrollment/iot-wcd-bulk-token-successful.png)

11. <span data-ttu-id="1359b-154">선택 **고급 편집기로 전환**를 선택한 후 *예*합니다.</span><span class="sxs-lookup"><span data-stu-id="1359b-154">Select **Switch to advanced editor**, and then select *Yes*.</span></span>

     ![고급 편집기 확인 페이지로 전환 합니다.](../media/IntuneDeviceEnrollment/iot-wcd-switch-to-advanced-editor.png)

12. <span data-ttu-id="1359b-156">아래 **사용자 지정 항목을 선택**를 유지 합니다 **계정** 설정에는 있지만 다른 모든 설정을 제거:</span><span class="sxs-lookup"><span data-stu-id="1359b-156">Under **Selected customizations**, Leave the **Account** settings, but remove all other settings:</span></span>
13. <span data-ttu-id="1359b-157">선택 **OOBE**를 선택한 후 **제거**합니다.</span><span class="sxs-lookup"><span data-stu-id="1359b-157">Select **OOBE**, and then select **Remove**.</span></span>
14. <span data-ttu-id="1359b-158">하는 경우 **SharedPC** 는 표시를 선택한 후 **제거**합니다.</span><span class="sxs-lookup"><span data-stu-id="1359b-158">If **SharedPC** is listed, select it, and then select **Remove**.</span></span>

     ![사용자 지정 제거](../media/IntuneDeviceEnrollment/iot-wcd-select-customizations.png)

15. <span data-ttu-id="1359b-160">선택 **내보낼**를 선택한 후 **프로 비전 패키지**합니다.</span><span class="sxs-lookup"><span data-stu-id="1359b-160">Select **Export**, and then choose **Provisioning package**.</span></span>

     ![프로 비전 패키지를 선택합니다.](../media/IntuneDeviceEnrollment/iot-wcd-export-provisioning-package.png)

16. <span data-ttu-id="1359b-162">다음 페이지에서 기본 설정을 적용 하 고 선택 **다음**합니다.</span><span class="sxs-lookup"><span data-stu-id="1359b-162">On the next page, accept the default settings and select **Next**.</span></span>
17. <span data-ttu-id="1359b-163">마찬가지로 다음 페이지에서 기본 설정을 적용 하 고 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="1359b-163">Again, on the next page, accept the default settings and select Next.</span></span>
18. <span data-ttu-id="1359b-164">변경 된 **프로 비전 패키지** 대상 또는 두고 기본 경로 선택한 후 **다음**합니다.</span><span class="sxs-lookup"><span data-stu-id="1359b-164">Change the **Provisioning Package** destination or leave the default path, and then select **Next**.</span></span>
19. <span data-ttu-id="1359b-165">선택 **빌드**합니다.</span><span class="sxs-lookup"><span data-stu-id="1359b-165">Select **Build**.</span></span>
20. <span data-ttu-id="1359b-166">선택 된 **출력 위치** 준비가 되 면.ppkg 파일을 찾을 수 있도록 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="1359b-166">Select the **Output Location** link so that you can locate the .ppkg file when it's ready.</span></span>

     ![출력 위치 링크](../media/IntuneDeviceEnrollment/iot-wcd-all-done.png)

21. <span data-ttu-id="1359b-168">선택 **완료**합니다.</span><span class="sxs-lookup"><span data-stu-id="1359b-168">Select **Finish**.</span></span>
22. <span data-ttu-id="1359b-169">파일 탐색기로 이동 하 고 IoT Core 장치 프로 비전 패키지를 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="1359b-169">Go to File Explorer and copy the provisioning package to your IoT Core device.</span></span> <span data-ttu-id="1359b-170">아래의 microSD 카드에 저장 합니다 **MainOS** 드라이브에 **c:\windows\provisioning\packages** 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="1359b-170">Save it to the microSD card under the **MainOS** drive in the **c:\windows\provisioning\packages** folder.</span></span>  <span data-ttu-id="1359b-171">이 폴더에 파일을 저장 하는 권한을 부여 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1359b-171">You'll have to grant permissions to save the file in this folder.</span></span>

### <a name="provision-and-enroll-the-iot-core-device-in-intune"></a><span data-ttu-id="1359b-172">프로 비전 하 고 Intune에서 IoT Core 장치 등록</span><span class="sxs-lookup"><span data-stu-id="1359b-172">Provision and enroll the IoT Core device in Intune</span></span>

1. <span data-ttu-id="1359b-173">IoT Core 장치에 microSD 카드를 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="1359b-173">Insert the microSD card into your IoT Core device.</span></span>
2. <span data-ttu-id="1359b-174">IoT Core 장치를 켜고 시간을 시작 하 고 표준 화면을 표시 하도록 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1359b-174">Turn on your IoT Core device and allow time for it to start up and display the standard screen.</span></span>
3. <span data-ttu-id="1359b-175">Azure portal에서 Microsoft Intune 콘솔에 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="1359b-175">Return to the Microsoft Intune console in the Azure portal.</span></span> <span data-ttu-id="1359b-176">장치는 장치 목록에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1359b-176">Your device should appear in the list of devices.</span></span>
     > [!NOTE]
     > <span data-ttu-id="1359b-177">등록을 완료 하는 데 15 분 이상 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1359b-177">Enrollment could take 15 minutes or more to complete.</span></span>

     ![Intune 장치 목록](../media/IntuneDeviceEnrollment/iot-ap-devices-after-enrollment.png)

## <a name="next-steps"></a><span data-ttu-id="1359b-179">다음 단계</span><span class="sxs-lookup"><span data-stu-id="1359b-179">Next steps</span></span>

- <span data-ttu-id="1359b-180">[Intune에서 장치 세부 정보를 참조 하세요.](https://docs.microsoft.com/intune/device-inventory)합니다.</span><span class="sxs-lookup"><span data-stu-id="1359b-180">[See device details in Intune](https://docs.microsoft.com/intune/device-inventory).</span></span>
- <span data-ttu-id="1359b-181">[최신 정책 및 Intune 사용 하 여 작업을 가져오는 장치 동기화](https://docs.microsoft.com/intune/device-sync)합니다.</span><span class="sxs-lookup"><span data-stu-id="1359b-181">[Sync the device to get the latest policies and actions with Intune](https://docs.microsoft.com/intune/device-sync).</span></span>
- <span data-ttu-id="1359b-182">[Intune 사용 하 여 장치를 원격으로 다시 시작](https://docs.microsoft.com/intune/device-restart)합니다.</span><span class="sxs-lookup"><span data-stu-id="1359b-182">[Remotely restart the device with Intune](https://docs.microsoft.com/intune/device-restart).</span></span>
