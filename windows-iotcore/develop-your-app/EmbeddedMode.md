---
title: Embedded(포함) 모드
author: lilyhou
ms.author: lihou
ms.date: 11/10/2017
ms.topic: article
description: 백그라운드 응용 프로그램 및 기타 기능을 사용 하도록 설정 하는 포함 된 모드를 허용 하도록 Windows를 구성 하는 방법에 알아봅니다.
keywords: windows iot, 포함 된 모드, 백그라운드 응용 프로그램
ms.openlocfilehash: ca8124d97a9161a1539eff92c55cf3630cf0a049
ms.sourcegitcommit: b719e66699372e1339c2316cab45df2a474d09a0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/28/2019
ms.locfileid: "66252173"
---
# <a name="embedded-mode"></a><span data-ttu-id="410b9-104">Embedded(포함) 모드</span><span class="sxs-lookup"><span data-stu-id="410b9-104">Embedded mode</span></span>

<span data-ttu-id="410b9-105">Windows IoT Core 및 Windows IoT Enterprise에 포함 된 모드는 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="410b9-105">Embedded Mode is supported on Windows IoT Core and Windows IoT Enterprise.</span></span> <span data-ttu-id="410b9-106">포함 된 모드를 사용 하면:</span><span class="sxs-lookup"><span data-stu-id="410b9-106">Embedded Mode enables:</span></span>

* [<span data-ttu-id="410b9-107">백그라운드 응용 프로그램 (자세히)</span><span class="sxs-lookup"><span data-stu-id="410b9-107">Background Applications (read more)</span></span>](https://docs.microsoft.com/windows/iot-core/develop-your-app/backgroundapplications)
* <span data-ttu-id="410b9-108">LowLevelDevice 기능 사용</span><span class="sxs-lookup"><span data-stu-id="410b9-108">Use of the lowLevelDevice capability</span></span>
* <span data-ttu-id="410b9-109">SystemManagement 기능 사용</span><span class="sxs-lookup"><span data-stu-id="410b9-109">Use of systemManagement capability</span></span>

<span data-ttu-id="410b9-110">포함 된 모드 창 IoT Core에 항상 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="410b9-110">Embedded mode is always enabled on Window IoT Core.</span></span>
<span data-ttu-id="410b9-111">Windows IoT Enterprise에서 아래 단계에 따라 포함된 모드를 사용할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="410b9-111">Embedded mode must be enabled by following the steps below on Windows IoT Enterprise.</span></span>

## <a name="background-applications"></a><span data-ttu-id="410b9-112">백그라운드 응용 프로그램</span><span class="sxs-lookup"><span data-stu-id="410b9-112">Background Applications</span></span>

<span data-ttu-id="410b9-113">백그라운드 응용 프로그램은 백그라운드 응용 프로그램 (IoT) 템플릿을 사용 하 여 Visual Studio에서 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="410b9-113">Background Applications are created using the Background Application (IoT) template in Visual Studio.</span></span>
<span data-ttu-id="410b9-114">만들기에 대해 자세히 알아보세요 [백그라운드 응용 프로그램](https://docs.microsoft.com/windows/iot-core/develop-your-app/backgroundapplications)합니다.</span><span class="sxs-lookup"><span data-stu-id="410b9-114">Read more about creating [Background Applications](https://docs.microsoft.com/windows/iot-core/develop-your-app/backgroundapplications).</span></span>

<span data-ttu-id="410b9-115">백그라운드 응용 프로그램 중지 하지 않고 리소스에 제한 없이 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="410b9-115">Background applications run without stopping and without resource limits.</span></span> <span data-ttu-id="410b9-116">또한 백그라운드 응용 프로그램이 어떤 이유로 중지 하 고 포함 하는 경우 모드가 설정 된 시스템에 의해 백그라운드 응용 프로그램을 다시 시작 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="410b9-116">Also, if the background application stops for some reason and embedded mode is enabled the background application will be restarted by the system.</span></span>

<span data-ttu-id="410b9-117">시스템 자동 백그라운드 응용 프로그램으로 시작 하는 동안 사용자가 중지 하거나 백그라운드 응용 프로그램의 작업을 방해 하지 못하도록 시스템 잠금 기능을 활성화 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="410b9-117">While the system will automatically restart background applications, system lockdown features must be enabled to prevent users from stopping or interfering with the operation of Background Applications.</span></span>

## <a name="lowlevel-device-capability-and-lowleveldevice-capability"></a><span data-ttu-id="410b9-118">lowLevel 장치 기능 및 lowLevelDevice 기능</span><span class="sxs-lookup"><span data-stu-id="410b9-118">lowLevel device Capability and lowLevelDevice capability</span></span>

<span data-ttu-id="410b9-119">합니다 **lowLevel** 장치 기능 I2C, SPI, GPIO 같은 하위 수준의 하드웨어 인터페이스에 액세스를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="410b9-119">The **lowLevel** device Capability gives access to low-level hardware interfaces like GPIO, SPI, and I2C.</span></span>

* [<span data-ttu-id="410b9-120">쳐다 Sample(GPIO)</span><span class="sxs-lookup"><span data-stu-id="410b9-120">Blinky Sample(GPIO)</span></span>](https://developer.microsoft.com/en-us/windows/iot/samples/helloblinky)
* [<span data-ttu-id="410b9-121">가 속도계 샘플</span><span class="sxs-lookup"><span data-stu-id="410b9-121">Accelerometer Sample</span></span>](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/Accelerometer)

<span data-ttu-id="410b9-122">합니다 **lowLevelDevices** 기능 많은 추가 요구 사항이 충족 되 면 사용자 지정 장치에 액세스 하는 앱을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="410b9-122">The **lowLevelDevices** Capability allows apps to access custom devices when a number of additional requirements are met.</span></span> <span data-ttu-id="410b9-123">이 기능은 GPIO, I2C, SPI, 및 PWM 장치에 대 한 액세스를 허용 하는 lowLevel 장치 기능을 혼동 해서는 안됩니다.</span><span class="sxs-lookup"><span data-stu-id="410b9-123">This capability should not be confused with the lowLevel device capability, which allows access to GPIO, I2C, SPI, and PWM devices.</span></span>

<span data-ttu-id="410b9-124">가리킵니다 [앱 기능 선언](https://docs.microsoft.com/en-us/windows/uwp/packaging/app-capability-declarations) 세부 정보에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="410b9-124">Refer to [App capability declarations](https://docs.microsoft.com/en-us/windows/uwp/packaging/app-capability-declarations) for details.</span></span>

## <a name="systemmanagment-capability"></a><span data-ttu-id="410b9-125">systemManagment 기능</span><span class="sxs-lookup"><span data-stu-id="410b9-125">systemManagment Capability</span></span>

<span data-ttu-id="410b9-126">응용 프로그램에 대 한 systemManagment 기능을 사용 하도록 설정 하면 잠금 해제 됩니다 하는 api 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="410b9-126">When you enable the systemManagment capabilities for your application this is the set of APIs that gets unlocked:</span></span>  

* [<span data-ttu-id="410b9-127">Windows.System.ProcessLauncher</span><span class="sxs-lookup"><span data-stu-id="410b9-127">Windows.System.ProcessLauncher</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.system.processlauncher.aspx)
* [<span data-ttu-id="410b9-128">Windows.System.TimeZoneSettings</span><span class="sxs-lookup"><span data-stu-id="410b9-128">Windows.System.TimeZoneSettings</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.system.timezonesettings.aspx)
* [<span data-ttu-id="410b9-129">Windows.System.ShutdownManager</span><span class="sxs-lookup"><span data-stu-id="410b9-129">Windows.System.ShutdownManager</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.system.shutdownmanager.aspx)
* [<span data-ttu-id="410b9-130">Windows.Globalization.Language.TrySetInputMethodLanguageTag</span><span class="sxs-lookup"><span data-stu-id="410b9-130">Windows.Globalization.Language.TrySetInputMethodLanguageTag</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.globalization.language.trysetinputmethodlanguagetag.aspx)

## <a name="debugging-background-applications"></a><span data-ttu-id="410b9-131">백그라운드 응용 프로그램 디버깅</span><span class="sxs-lookup"><span data-stu-id="410b9-131">Debugging Background Applications</span></span>

<span data-ttu-id="410b9-132">Windows IoT Core를 실행 하지 않는 장치에서 디버깅 하는 경우 다음 오류 메시지 중 하나가 표시 AllowEmbeddedMode 장치에서 사용 하 고 포함 된 모드 서비스가 실행 되 고 있는지 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="410b9-132">If you are debugging on a device that is not running Windows IoT Core and you see either of the following error messages you need to ensure AllowEmbeddedMode is enabled on the device and that the Embedded Mode service is running:</span></span>

* <span data-ttu-id="410b9-133">끝점 매퍼에서 사용할 수 있는 끝점이 더 이상 있습니다.</span><span class="sxs-lookup"><span data-stu-id="410b9-133">There are no more endpoints available from the endpoint mapper.</span></span>
* <span data-ttu-id="410b9-134">이 프로그램은 그룹 정책에 의해 차단 됩니다.</span><span class="sxs-lookup"><span data-stu-id="410b9-134">This program is blocked by group policy.</span></span> <span data-ttu-id="410b9-135">자세한 내용은 시스템 관리자에 게 문의 합니다.</span><span class="sxs-lookup"><span data-stu-id="410b9-135">For more information, contact your system administrator.</span></span>

## <a name="changing-the-mode"></a><span data-ttu-id="410b9-136">모드 변경</span><span class="sxs-lookup"><span data-stu-id="410b9-136">Changing the mode</span></span>
<span data-ttu-id="410b9-137">이미징 및 구성 디자이너 (ICD) AllowEmbeddedMode 설정으로 프로 비전 패키지를 만들 해야 포함된 모드를 사용 하도록 설정 하려면 = 1입니다.</span><span class="sxs-lookup"><span data-stu-id="410b9-137">To enable embedded mode you will need to create a provisioning package in Imaging and Configuration Designer (ICD) that sets AllowEmbeddedMode=1.</span></span>  <span data-ttu-id="410b9-138">ICD를 설치 하려면 다운로드 하 고 Windows 10 용 Windows ADK를 설치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="410b9-138">To install ICD you need to download and install the Windows ADK for Windows 10.</span></span>

* [<span data-ttu-id="410b9-139">Windows 10 용 Windows ADK 다운로드</span><span class="sxs-lookup"><span data-stu-id="410b9-139">Download the Windows ADK for Windows 10</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=526740)
* <span data-ttu-id="410b9-140">[Windows 10 용 Windows ADK의에서 새로운 기능 알아보기](https://msdn.microsoft.com/library/windows/hardware/dn927348(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="410b9-140">[Learn about what's new in the Windows ADK for Windows 10](https://msdn.microsoft.com/library/windows/hardware/dn927348(v=vs.85).aspx)</span></span>

1. <span data-ttu-id="410b9-141">ADK를 설치할 때 선택 **이미징 및 구성 디자이너 (ICD)**</span><span class="sxs-lookup"><span data-stu-id="410b9-141">When installing the ADK select **Imaging and Configuration Designer (ICD)**</span></span>
2. <span data-ttu-id="410b9-142">설치가 완료 된 후 Windows 이미징 및 구성 디자이너 (WICD)를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="410b9-142">After installation is complete run Windows Imaging and Configuration Designer (WICD).</span></span>

    ![WICD 아이콘](../media/EmbeddedMode/WICD_Icon.png)

3. <span data-ttu-id="410b9-144">**Advanced provisioning**(고급 프로비전)을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="410b9-144">Click **Advanced provisioning**.</span></span>  <span data-ttu-id="410b9-145">프로젝트 이름을 **AllowEmbeddedMode** 누릅니다 **다음**합니다.</span><span class="sxs-lookup"><span data-stu-id="410b9-145">Name the project **AllowEmbeddedMode** and click **Next**.</span></span>
    <span data-ttu-id="410b9-146">![Step3](../media/EmbeddedMode/Step3.png)</span><span class="sxs-lookup"><span data-stu-id="410b9-146">![Step3](../media/EmbeddedMode/Step3.png)</span></span>

4. <span data-ttu-id="410b9-147">선택할 **모든 Windows 버전에 공통적으로 적용** 한 다음 **다음**합니다.</span><span class="sxs-lookup"><span data-stu-id="410b9-147">Choose **Common to all Windows editions** then **Next**.</span></span>
    <span data-ttu-id="410b9-148">![Step4](../media/EmbeddedMode/Step4.png)</span><span class="sxs-lookup"><span data-stu-id="410b9-148">![Step4](../media/EmbeddedMode/Step4.png)</span></span>

5. <span data-ttu-id="410b9-149">**마침**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="410b9-149">Click **Finish**.</span></span>

    ![5 단계](../media/EmbeddedMode/Step5.png)

6. <span data-ttu-id="410b9-151">검색 상자에 입력 **EmbeddedMode** 를 클릭 하 고 **AllowEmbeddedMode**합니다.</span><span class="sxs-lookup"><span data-stu-id="410b9-151">In the search box type **EmbeddedMode** and then click on **AllowEmbeddedMode**.</span></span>

    ![6 단계](../media/EmbeddedMode/Step6.png)

7. <span data-ttu-id="410b9-153">창 가운데에 값을 설정 **AllowEmbeddedMode** 하 **예** ![Step7](../media/EmbeddedMode/Step7.png)</span><span class="sxs-lookup"><span data-stu-id="410b9-153">In the center pane set the value of **AllowEmbeddedMode** to **Yes** ![Step7](../media/EmbeddedMode/Step7.png)</span></span>

8. <span data-ttu-id="410b9-154">내보내기를 클릭 > 패키지를 프로 비전</span><span class="sxs-lookup"><span data-stu-id="410b9-154">Click Export > Provisioning Package</span></span>

    ![Step8](../media/EmbeddedMode/Step8.png)

9. <span data-ttu-id="410b9-156">다음을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="410b9-156">Click Next.</span></span>

    ![Step9](../media/EmbeddedMode/Step9.png)

10. <span data-ttu-id="410b9-158">다음을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="410b9-158">Click Next.</span></span>

    ![Step10](../media/EmbeddedMode/Step10.png)

11. <span data-ttu-id="410b9-160">다음을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="410b9-160">Click Next.</span></span>

    ![Step11](../media/EmbeddedMode/Step11.png)

12. <span data-ttu-id="410b9-162">빌드를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="410b9-162">Click Build.</span></span>

    ![Step12](../media/EmbeddedMode/Step12.png)

13. <span data-ttu-id="410b9-164">포함 된 모드를 설치 합니다. Windows IoT enterprise PPKG 두 번 클릭 합니다. PPKG 합니다.</span><span class="sxs-lookup"><span data-stu-id="410b9-164">To install the embedded mode .PPKG on Windows IoT Enterprise double-click on the .PPKG.</span></span>

14. <span data-ttu-id="410b9-165">클릭 **예, 추가**합니다.</span><span class="sxs-lookup"><span data-stu-id="410b9-165">Click **Yes, add it**.</span></span>
    <span data-ttu-id="410b9-166">LUA 대화 상자, 표시 되는 경우 예를 클릭 하 고 클릭 **예, 추가** 아래에 표시 된 대화 상자에서.</span><span class="sxs-lookup"><span data-stu-id="410b9-166">Click yes on the LUA dialog if it appears, and the click **Yes, add it** on the dialog shown below.</span></span>
    <span data-ttu-id="410b9-167">![Step14Standard](../media/EmbeddedMode/Step14Standard.png)</span><span class="sxs-lookup"><span data-stu-id="410b9-167">![Step14Standard](../media/EmbeddedMode/Step14Standard.png)</span></span>


## <a name="configuring-a-background-application-to-run-automatically"></a><span data-ttu-id="410b9-168">자동으로 실행 하는 백그라운드 응용 프로그램 구성</span><span class="sxs-lookup"><span data-stu-id="410b9-168">Configuring a Background Application to Run automatically</span></span>
1. <span data-ttu-id="410b9-169">지침에 따라 자동으로 실행 하는 백그라운드 응용 프로그램을 구성 하려면이 필요 [MinnowBoardMax SD 카드를 만듭니다](https://developer.microsoft.com/en-us/windows/iot/getstarted) 복사 `D:\windows\system32\iotstartup.exe` (d:가 SD 카드).</span><span class="sxs-lookup"><span data-stu-id="410b9-169">To configure a Background Application to automatically run you will need to follow the directions to [create an MinnowBoardMax SD Card](https://developer.microsoft.com/en-us/windows/iot/getstarted) and copy `D:\windows\system32\iotstartup.exe` (where D: is your SD Card).</span></span>

2. <span data-ttu-id="410b9-170">설치 된 백그라운드 응용 프로그램 유형 목록을 가져오려면:</span><span class="sxs-lookup"><span data-stu-id="410b9-170">To get a list of installed Background Applications type:</span></span>

        C:\> iotstartup list BackgroundApplication1

3. <span data-ttu-id="410b9-171">출력은 다음과 같이 표시 됩니다는 각 설치 된 백그라운드 응용 프로그램에서의 전체 이름을 포함 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="410b9-171">The output should include the full name of each installed Background Application, which will look like this:</span></span>

        Headless : BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpvee

5. <span data-ttu-id="410b9-172">부팅 유형에 실행 되도록이 앱을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="410b9-172">To configure this app to run at boot type:</span></span>

        C:\> iotstartup add headless BackgroundApplication1

6. <span data-ttu-id="410b9-173">백그라운드 응용 프로그램이 성공적으로 시작 목록에 추가 된 경우이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="410b9-173">If the Background Application has been successfully added to the startup list you should see this:</span></span>

        Added Headless: BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpveeplication1

7. <span data-ttu-id="410b9-174">포함 된 모드 장치를 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="410b9-174">Restart the embedded mode device:</span></span>

8. <span data-ttu-id="410b9-175">장치를 다시 시작한 후 백그라운드 응용 프로그램에 자동으로 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="410b9-175">Once the device has restarted, your Background Application will start automatically.</span></span>  <span data-ttu-id="410b9-176">백그라운드 응용 프로그램을 관리 하는 포함 된 모드를 시작 하려면 몇 분 정도 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="410b9-176">The Embedded Mode service which manages Background Applications can take a few minutes to start.</span></span>  <span data-ttu-id="410b9-177">포함된 모드를 시작 프로그램 목록에서 백그라운드 응용 프로그램을 모니터링 하 고는 중지 되 면 다시 시작 가져오기 있는지 확인 됩니다.</span><span class="sxs-lookup"><span data-stu-id="410b9-177">The embedded mode service will monitor Background Applications on the startup list and make sure they get restarted if they stops.</span></span>  <span data-ttu-id="410b9-178">짧은 기간에 여러 번 백그라운드 응용 프로그램을 중지 하는 경우 더 이상 시작할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="410b9-178">If a Background Application stops several times in a short period of time it will no longer be restarted.</span></span>

9. <span data-ttu-id="410b9-179">시작 목록 형식에서 백그라운드 응용 프로그램을 제거:</span><span class="sxs-lookup"><span data-stu-id="410b9-179">To remove your Background Application from the startup list type:</span></span>

        C:\> iotstartup remove headless BackgroundApplication1

10. <span data-ttu-id="410b9-180">백그라운드 응용 프로그램 구동 목록에서 제거 되 면 다음과 같은 출력이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="410b9-180">If the Background Application is removed from the startup list the output will look like this:</span></span>

        Removed headless: BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpvee
