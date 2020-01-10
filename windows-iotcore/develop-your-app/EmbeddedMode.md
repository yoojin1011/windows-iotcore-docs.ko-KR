---
title: Embedded(포함) 모드
author: lilyhou
ms.author: lihou
ms.date: 11/10/2017
ms.topic: article
description: Windows에서 포함 모드를 허용 하도록 구성 하 여 백그라운드 응용 프로그램 및 기타 기능을 사용 하도록 구성 하는 방법을 알아봅니다.
keywords: windows iot, 포함 모드, 백그라운드 응용 프로그램
ms.openlocfilehash: 7305853515b5bd1ca53c9b8be34c2449752c4897
ms.sourcegitcommit: ea060254f9c4c25afcd0245c897b9e1425321859
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75721673"
---
# <a name="embedded-mode"></a><span data-ttu-id="5ef93-104">Embedded(포함) 모드</span><span class="sxs-lookup"><span data-stu-id="5ef93-104">Embedded mode</span></span>

<span data-ttu-id="5ef93-105">임베디드 모드는 Windows IoT Core 및 Windows IoT Enterprise에서 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ef93-105">Embedded Mode is supported on Windows IoT Core and Windows IoT Enterprise.</span></span> <span data-ttu-id="5ef93-106">포함 모드를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ef93-106">Embedded Mode enables:</span></span>

* [<span data-ttu-id="5ef93-107">백그라운드 응용 프로그램 (자세히 읽기)</span><span class="sxs-lookup"><span data-stu-id="5ef93-107">Background Applications (read more)</span></span>](https://docs.microsoft.com/windows/iot-core/develop-your-app/backgroundapplications)
* <span data-ttu-id="5ef93-108">LowLevelDevice 기능 사용</span><span class="sxs-lookup"><span data-stu-id="5ef93-108">Use of the lowLevelDevice capability</span></span>
* <span data-ttu-id="5ef93-109">SystemManagement 기능 사용</span><span class="sxs-lookup"><span data-stu-id="5ef93-109">Use of systemManagement capability</span></span>

<span data-ttu-id="5ef93-110">임베디드 모드는 Windows IoT Core에서 항상 사용 하도록 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ef93-110">Embedded mode is always enabled on Window IoT Core.</span></span>
<span data-ttu-id="5ef93-111">Windows IoT Enterprise에서 아래 단계를 수행 하 여 포함 모드를 사용 하도록 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ef93-111">Embedded mode must be enabled by following the steps below on Windows IoT Enterprise.</span></span>

## <a name="background-applications"></a><span data-ttu-id="5ef93-112">백그라운드 응용 프로그램</span><span class="sxs-lookup"><span data-stu-id="5ef93-112">Background Applications</span></span>

<span data-ttu-id="5ef93-113">백그라운드 응용 프로그램은 Visual Studio의 IoT (배경 응용 프로그램) 템플릿을 사용 하 여 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5ef93-113">Background Applications are created using the Background Application (IoT) template in Visual Studio.</span></span>
<span data-ttu-id="5ef93-114">자세한 내용은 [백그라운드 응용 프로그램](https://docs.microsoft.com/windows/iot-core/develop-your-app/backgroundapplications)만들기를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5ef93-114">Read more about creating [Background Applications](https://docs.microsoft.com/windows/iot-core/develop-your-app/backgroundapplications).</span></span>

<span data-ttu-id="5ef93-115">백그라운드 응용 프로그램은 리소스 제한 없이 중지 하지 않고 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ef93-115">Background applications run without stopping and without resource limits.</span></span> <span data-ttu-id="5ef93-116">또한 백그라운드 응용 프로그램이 어떤 이유로 중지 되 고 포함 모드를 사용 하는 경우 시스템에서 백그라운드 응용 프로그램을 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ef93-116">Also, if the background application stops for some reason and embedded mode is enabled the background application will be restarted by the system.</span></span>

<span data-ttu-id="5ef93-117">시스템이 백그라운드 응용 프로그램을 자동으로 다시 시작 하는 동안 사용자가 백그라운드 응용 프로그램의 작업을 중지 하거나 방해 하지 않도록 시스템 잠금 기능을 사용 하도록 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ef93-117">While the system will automatically restart background applications, system lockdown features must be enabled to prevent users from stopping or interfering with the operation of Background Applications.</span></span>

## <a name="lowlevel-device-capability-and-lowleveldevice-capability"></a><span data-ttu-id="5ef93-118">lowLevel 장치 기능 및 lowLevelDevice 기능</span><span class="sxs-lookup"><span data-stu-id="5ef93-118">lowLevel device Capability and lowLevelDevice capability</span></span>

<span data-ttu-id="5ef93-119">**Lowlevel** 장치 기능을 사용 하면 GPIO, SPI 및 I2C와 같은 하위 수준 하드웨어 인터페이스에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ef93-119">The **lowLevel** device Capability gives access to low-level hardware interfaces like GPIO, SPI, and I2C.</span></span>

* [<span data-ttu-id="5ef93-120">Blinky 샘플 (GPIO)</span><span class="sxs-lookup"><span data-stu-id="5ef93-120">Blinky Sample(GPIO)</span></span>](https://developer.microsoft.com/en-us/windows/iot/samples/helloblinky)
* [<span data-ttu-id="5ef93-121">가 속도계 샘플</span><span class="sxs-lookup"><span data-stu-id="5ef93-121">Accelerometer Sample</span></span>](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/Accelerometer)

<span data-ttu-id="5ef93-122">**Lowleveldevices** 기능을 통해 많은 추가 요구 사항이 충족 되 면 앱에서 사용자 지정 장치에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ef93-122">The **lowLevelDevices** Capability allows apps to access custom devices when a number of additional requirements are met.</span></span> <span data-ttu-id="5ef93-123">이 기능은 GPIO, I2C, SPI 및 PWM) 장치에 대 한 액세스를 허용 하는 lowLevel 장치 기능과 혼동 해서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ef93-123">This capability should not be confused with the lowLevel device capability, which allows access to GPIO, I2C, SPI, and PWM devices.</span></span>

<span data-ttu-id="5ef93-124">자세한 내용은 [앱 기능 선언](https://docs.microsoft.com/windows/uwp/packaging/app-capability-declarations) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5ef93-124">Refer to [App capability declarations](https://docs.microsoft.com/windows/uwp/packaging/app-capability-declarations) for details.</span></span>

## <a name="systemmanagment-capability"></a><span data-ttu-id="5ef93-125">systemManagment 기능</span><span class="sxs-lookup"><span data-stu-id="5ef93-125">systemManagment Capability</span></span>

<span data-ttu-id="5ef93-126">응용 프로그램에 대 한 systemManagment 기능을 사용 하도록 설정 하는 경우 잠금 해제 된 Api 집합은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="5ef93-126">When you enable the systemManagment capabilities for your application this is the set of APIs that gets unlocked:</span></span>  

* [<span data-ttu-id="5ef93-127">Windows. System.object</span><span class="sxs-lookup"><span data-stu-id="5ef93-127">Windows.System.ProcessLauncher</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.system.processlauncher.aspx)
* [<span data-ttu-id="5ef93-128">TimeZoneSettings</span><span class="sxs-lookup"><span data-stu-id="5ef93-128">Windows.System.TimeZoneSettings</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.system.timezonesettings.aspx)
* [<span data-ttu-id="5ef93-129">ShutdownManager</span><span class="sxs-lookup"><span data-stu-id="5ef93-129">Windows.System.ShutdownManager</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.system.shutdownmanager.aspx)
* [<span data-ttu-id="5ef93-130">TrySetInputMethodLanguageTag.</span><span class="sxs-lookup"><span data-stu-id="5ef93-130">Windows.Globalization.Language.TrySetInputMethodLanguageTag</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.globalization.language.trysetinputmethodlanguagetag.aspx)

## <a name="debugging-background-applications"></a><span data-ttu-id="5ef93-131">백그라운드 응용 프로그램 디버깅</span><span class="sxs-lookup"><span data-stu-id="5ef93-131">Debugging Background Applications</span></span>

<span data-ttu-id="5ef93-132">Windows IoT Core를 실행 하지 않는 장치에서 디버깅 하는 경우 다음 오류 메시지 중 하나가 표시 되 면 장치에서 AllowEmbeddedMode을 사용 하도록 설정 하 고 포함 된 모드 서비스가 실행 중인지 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ef93-132">If you are debugging on a device that is not running Windows IoT Core and you see either of the following error messages you need to ensure AllowEmbeddedMode is enabled on the device and that the Embedded Mode service is running:</span></span>

* <span data-ttu-id="5ef93-133">엔드포인트 매퍼에서 사용 가능한 엔드포인트가 더 이상 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5ef93-133">There are no more endpoints available from the endpoint mapper.</span></span>
* <span data-ttu-id="5ef93-134">이 프로그램은 그룹 정책에 의해 차단 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ef93-134">This program is blocked by group policy.</span></span> <span data-ttu-id="5ef93-135">자세한 내용은 시스템 관리자에 게 문의 하십시오.</span><span class="sxs-lookup"><span data-stu-id="5ef93-135">For more information, contact your system administrator.</span></span>

## <a name="changing-the-mode"></a><span data-ttu-id="5ef93-136">모드 변경</span><span class="sxs-lookup"><span data-stu-id="5ef93-136">Changing the mode</span></span>
<span data-ttu-id="5ef93-137">포함 모드를 사용 하도록 설정 하려면 AllowEmbeddedMode = 1을 설정 하는 ICD (이미징 및 구성 디자이너)에서 프로 비전 패키지를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ef93-137">To enable embedded mode you will need to create a provisioning package in Imaging and Configuration Designer (ICD) that sets AllowEmbeddedMode=1.</span></span>  <span data-ttu-id="5ef93-138">ICD를 설치 하려면 Windows 10 용 Windows ADK를 다운로드 하 여 설치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ef93-138">To install ICD you need to download and install the Windows ADK for Windows 10.</span></span>

* [<span data-ttu-id="5ef93-139">Windows 10용 Windows ADK 다운로드</span><span class="sxs-lookup"><span data-stu-id="5ef93-139">Download the Windows ADK for Windows 10</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=526740)
* <span data-ttu-id="5ef93-140">[Windows 10 용 Windows ADK의 새로운 기능에 대해 알아봅니다.](https://msdn.microsoft.com/library/windows/hardware/dn927348(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="5ef93-140">[Learn about what's new in the Windows ADK for Windows 10](https://msdn.microsoft.com/library/windows/hardware/dn927348(v=vs.85).aspx)</span></span>

1. <span data-ttu-id="5ef93-141">ADK를 설치할 때 **ICD (이미징 및 구성 디자이너)** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ef93-141">When installing the ADK select **Imaging and Configuration Designer (ICD)**</span></span>
2. <span data-ttu-id="5ef93-142">설치가 완료 되 면 Windows 이미징 및 구성 디자이너 (WICD)를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ef93-142">After installation is complete run Windows Imaging and Configuration Designer (WICD).</span></span>

    ![WICD 아이콘](../media/EmbeddedMode/WICD_Icon.png)

3. <span data-ttu-id="5ef93-144">**고급 프로비저닝**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5ef93-144">Click **Advanced provisioning**.</span></span>  <span data-ttu-id="5ef93-145">프로젝트 이름을 **AllowEmbeddedMode** 로, **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ef93-145">Name the project **AllowEmbeddedMode** and click **Next**.</span></span>
    <span data-ttu-id="5ef93-146">![3 단계](../media/EmbeddedMode/Step3.png)</span><span class="sxs-lookup"><span data-stu-id="5ef93-146">![Step3](../media/EmbeddedMode/Step3.png)</span></span>

4. <span data-ttu-id="5ef93-147">**모든 Windows 버전에 공통을 선택 하** 고 **다음**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ef93-147">Choose **Common to all Windows editions** then **Next**.</span></span>
    <span data-ttu-id="5ef93-148">![4 단계](../media/EmbeddedMode/Step4.png)</span><span class="sxs-lookup"><span data-stu-id="5ef93-148">![Step4](../media/EmbeddedMode/Step4.png)</span></span>

5. <span data-ttu-id="5ef93-149">**마침**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5ef93-149">Click **Finish**.</span></span>

    ![5 단계](../media/EmbeddedMode/Step5.png)

6. <span data-ttu-id="5ef93-151">검색 상자에 **EmbeddedMode** 를 입력 한 다음 **AllowEmbeddedMode**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ef93-151">In the search box type **EmbeddedMode** and then click on **AllowEmbeddedMode**.</span></span>

    ![6 단계](../media/EmbeddedMode/Step6.png)

7. <span data-ttu-id="5ef93-153">가운데 창에서 **AllowEmbeddedMode** 값을 **예** ![Step7로 설정](../media/EmbeddedMode/Step7.png)</span><span class="sxs-lookup"><span data-stu-id="5ef93-153">In the center pane set the value of **AllowEmbeddedMode** to **Yes** ![Step7](../media/EmbeddedMode/Step7.png)</span></span>

8. <span data-ttu-id="5ef93-154">내보내기 > 프로 비전 패키지를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ef93-154">Click Export > Provisioning Package</span></span>

    ![Step8](../media/EmbeddedMode/Step8.png)

9. <span data-ttu-id="5ef93-156">다음을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5ef93-156">Click Next.</span></span>

    ![Step9](../media/EmbeddedMode/Step9.png)

10. <span data-ttu-id="5ef93-158">다음을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5ef93-158">Click Next.</span></span>

    ![Step10](../media/EmbeddedMode/Step10.png)

11. <span data-ttu-id="5ef93-160">다음을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5ef93-160">Click Next.</span></span>

    ![Step11](../media/EmbeddedMode/Step11.png)

12. <span data-ttu-id="5ef93-162">빌드를 클릭한 다음</span><span class="sxs-lookup"><span data-stu-id="5ef93-162">Click Build.</span></span>

    ![Step12](../media/EmbeddedMode/Step12.png)

13. <span data-ttu-id="5ef93-164">포함 모드를 설치 합니다. PPKG Windows IoT Enterprise에서을 두 번 클릭 합니다. PPKG.</span><span class="sxs-lookup"><span data-stu-id="5ef93-164">To install the embedded mode .PPKG on Windows IoT Enterprise double-click on the .PPKG.</span></span>

14. <span data-ttu-id="5ef93-165">**예, 추가를**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ef93-165">Click **Yes, add it**.</span></span>
    <span data-ttu-id="5ef93-166">LUA 대화 상자가 나타나면 예를 클릭 하 고 **예를** 클릭 하 여 아래에 표시 된 대화 상자에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ef93-166">Click yes on the LUA dialog if it appears, and the click **Yes, add it** on the dialog shown below.</span></span>
    <span data-ttu-id="5ef93-167">![Step14Standard](../media/EmbeddedMode/Step14Standard.png)</span><span class="sxs-lookup"><span data-stu-id="5ef93-167">![Step14Standard](../media/EmbeddedMode/Step14Standard.png)</span></span>


## <a name="configuring-a-background-application-to-run-automatically"></a><span data-ttu-id="5ef93-168">백그라운드 응용 프로그램이 자동으로 실행 되도록 구성</span><span class="sxs-lookup"><span data-stu-id="5ef93-168">Configuring a Background Application to Run automatically</span></span>
1. <span data-ttu-id="5ef93-169">백그라운드 응용 프로그램을 자동으로 실행 하도록 구성 하려면 지침에 따라 [MINNOWBOARDMAX SD 카드를 만들고](https://developer.microsoft.com/en-us/windows/iot/getstarted) `D:\windows\system32\iotstartup.exe` (여기서 D:는 SD 카드)를 복사 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ef93-169">To configure a Background Application to automatically run you will need to follow the directions to [create an MinnowBoardMax SD Card](https://developer.microsoft.com/en-us/windows/iot/getstarted) and copy `D:\windows\system32\iotstartup.exe` (where D: is your SD Card).</span></span>

2. <span data-ttu-id="5ef93-170">설치 된 백그라운드 응용 프로그램의 목록을 가져오려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ef93-170">To get a list of installed Background Applications type:</span></span>

        C:\> iotstartup list BackgroundApplication1

3. <span data-ttu-id="5ef93-171">출력에는 설치 된 각 백그라운드 응용 프로그램의 전체 이름이 포함 되어야 하며,이는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="5ef93-171">The output should include the full name of each installed Background Application, which will look like this:</span></span>

        Headless : BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpvee

5. <span data-ttu-id="5ef93-172">부팅 형식에서 실행 되도록이 앱을 구성 하려면:</span><span class="sxs-lookup"><span data-stu-id="5ef93-172">To configure this app to run at boot type:</span></span>

        C:\> iotstartup add headless BackgroundApplication1

6. <span data-ttu-id="5ef93-173">백그라운드 응용 프로그램이 시작 목록에 성공적으로 추가 되 면 다음이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ef93-173">If the Background Application has been successfully added to the startup list you should see this:</span></span>

        Added Headless: BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpveeplication1

7. <span data-ttu-id="5ef93-174">포함 된 모드 장치를 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ef93-174">Restart the embedded mode device:</span></span>

8. <span data-ttu-id="5ef93-175">장치가 다시 시작 되 면 백그라운드 응용 프로그램이 자동으로 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ef93-175">Once the device has restarted, your Background Application will start automatically.</span></span>  <span data-ttu-id="5ef93-176">백그라운드 응용 프로그램을 관리 하는 포함 모드 서비스를 시작 하는 데 몇 분 정도 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ef93-176">The Embedded Mode service which manages Background Applications can take a few minutes to start.</span></span>  <span data-ttu-id="5ef93-177">포함 모드 서비스는 시작 목록에서 백그라운드 응용 프로그램을 모니터링 하 고 중지 시 다시 시작 되는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ef93-177">The embedded mode service will monitor Background Applications on the startup list and make sure they get restarted if they stops.</span></span>  <span data-ttu-id="5ef93-178">백그라운드 응용 프로그램이 짧은 시간 동안 여러 번 중지 하는 경우 더 이상 다시 시작 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5ef93-178">If a Background Application stops several times in a short period of time it will no longer be restarted.</span></span>

9. <span data-ttu-id="5ef93-179">시작 목록에서 백그라운드 응용 프로그램을 제거 하려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ef93-179">To remove your Background Application from the startup list type:</span></span>

        C:\> iotstartup remove headless BackgroundApplication1

10. <span data-ttu-id="5ef93-180">백그라운드 응용 프로그램이 시작 목록에서 제거 되 면 출력은 다음과 같이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ef93-180">If the Background Application is removed from the startup list the output will look like this:</span></span>

        Removed headless: BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpvee
