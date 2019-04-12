---
title: 포함 된 모드
author: lilyhou
ms.author: lihou
ms.date: 11/10/2017
ms.topic: article
description: 백그라운드 응용 프로그램 및 기타 기능을 사용 하도록 설정 하는 포함 된 모드를 허용 하도록 Windows를 구성 하는 방법에 알아봅니다.
keywords: windows iot, 포함 된 모드, 백그라운드 응용 프로그램
ms.openlocfilehash: 1944cec09400cff4d895bb9e55b89b3b19a3f5f5
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512318"
---
# <a name="embedded-mode"></a><span data-ttu-id="e7f98-104">포함 된 모드</span><span class="sxs-lookup"><span data-stu-id="e7f98-104">Embedded mode</span></span>

<span data-ttu-id="e7f98-105">Windows IoT Core 및 Windows IoT Enterprise에 포함 된 모드는 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e7f98-105">Embedded Mode is supported on Windows IoT Core and Windows IoT Enterprise.</span></span> <span data-ttu-id="e7f98-106">포함 된 모드를 사용 하면:</span><span class="sxs-lookup"><span data-stu-id="e7f98-106">Embedded Mode enables:</span></span>

* [<span data-ttu-id="e7f98-107">백그라운드 응용 프로그램 (자세히)</span><span class="sxs-lookup"><span data-stu-id="e7f98-107">Background Applications (read more)</span></span>](https://docs.microsoft.com/windows/iot-core/develop-your-app/backgroundapplications)
* <span data-ttu-id="e7f98-108">LowLevelDevice 기능 사용</span><span class="sxs-lookup"><span data-stu-id="e7f98-108">Use of the lowLevelDevice capability</span></span>
* <span data-ttu-id="e7f98-109">SystemManagement 기능 사용</span><span class="sxs-lookup"><span data-stu-id="e7f98-109">Use of systemManagement capability</span></span>

<span data-ttu-id="e7f98-110">포함 된 모드 창 IoT Core에 항상 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e7f98-110">Embedded mode is always enabled on Window IoT Core.</span></span>
<span data-ttu-id="e7f98-111">Windows IoT Enterprise에서 아래 단계에 따라 포함된 모드를 사용할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e7f98-111">Embedded mode must be enabled by following the steps below on Windows IoT Enterprise.</span></span>

## <a name="background-applications"></a><span data-ttu-id="e7f98-112">백그라운드 응용 프로그램</span><span class="sxs-lookup"><span data-stu-id="e7f98-112">Background Applications</span></span>

<span data-ttu-id="e7f98-113">백그라운드 응용 프로그램은 백그라운드 응용 프로그램 (IoT) 템플릿을 사용 하 여 Visual Studio에서 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e7f98-113">Background Applications are created using the Background Application (IoT) template in Visual Studio.</span></span>
<span data-ttu-id="e7f98-114">만들기에 대해 자세히 알아보세요 [백그라운드 응용 프로그램](https://docs.microsoft.com/windows/iot-core/develop-your-app/backgroundapplications)합니다.</span><span class="sxs-lookup"><span data-stu-id="e7f98-114">Read more about creating [Background Applications](https://docs.microsoft.com/windows/iot-core/develop-your-app/backgroundapplications).</span></span>

<span data-ttu-id="e7f98-115">백그라운드 응용 프로그램 중지 하지 않고 리소스에 제한 없이 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e7f98-115">Background applications run without stopping and without resource limits.</span></span> <span data-ttu-id="e7f98-116">또한 백그라운드 응용 프로그램이 어떤 이유로 중지 하 고 포함 하는 경우 모드가 설정 된 시스템에 의해 백그라운드 응용 프로그램을 다시 시작 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e7f98-116">Also, if the background application stops for some reason and embedded mode is enabled the background application will be restarted by the system.</span></span>

<span data-ttu-id="e7f98-117">시스템 자동 백그라운드 응용 프로그램으로 시작 하는 동안 사용자가 중지 하거나 백그라운드 응용 프로그램의 작업을 방해 하지 못하도록 시스템 잠금 기능을 활성화 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e7f98-117">While the system will automatically restart background applications, system lockdown features must be enabled to prevent users from stopping or interfering with the operation of Background Applications.</span></span>

## <a name="lowleveldevice-capability"></a><span data-ttu-id="e7f98-118">lowLevelDevice 기능</span><span class="sxs-lookup"><span data-stu-id="e7f98-118">lowLevelDevice Capability</span></span>

<span data-ttu-id="e7f98-119">기능 lowLevelDevice I2C, SPI, GPIO 같은 하위 수준의 하드웨어 인터페이스에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e7f98-119">The lowLevelDevice Capability gives access to low-level hardware interfaces like GPIO, SPI, and I2C.</span></span>

* [<span data-ttu-id="e7f98-120">쳐다 Sample(GPIO)</span><span class="sxs-lookup"><span data-stu-id="e7f98-120">Blinky Sample(GPIO)</span></span>](https://developer.microsoft.com/en-us/windows/iot/samples/helloblinky)
* [<span data-ttu-id="e7f98-121">가속도계 샘플</span><span class="sxs-lookup"><span data-stu-id="e7f98-121">Accelerometer Sample</span></span>](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/Accelerometer)

## <a name="systemmanagment-capability"></a><span data-ttu-id="e7f98-122">systemManagment 기능</span><span class="sxs-lookup"><span data-stu-id="e7f98-122">systemManagment Capability</span></span>

<span data-ttu-id="e7f98-123">응용 프로그램에 대 한 systemManagment 기능을 사용 하도록 설정 하면 잠금 해제 됩니다 하는 api 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="e7f98-123">When you enable the systemManagment capabilities for your application this is the set of APIs that gets unlocked:</span></span>  

* [<span data-ttu-id="e7f98-124">Windows.System.ProcessLauncher</span><span class="sxs-lookup"><span data-stu-id="e7f98-124">Windows.System.ProcessLauncher</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.system.processlauncher.aspx)
* [<span data-ttu-id="e7f98-125">Windows.System.TimeZoneSettings</span><span class="sxs-lookup"><span data-stu-id="e7f98-125">Windows.System.TimeZoneSettings</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.system.timezonesettings.aspx)
* [<span data-ttu-id="e7f98-126">Windows.System.ShutdownManager</span><span class="sxs-lookup"><span data-stu-id="e7f98-126">Windows.System.ShutdownManager</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.system.shutdownmanager.aspx)
* [<span data-ttu-id="e7f98-127">Windows.Globalization.Language.TrySetInputMethodLanguageTag</span><span class="sxs-lookup"><span data-stu-id="e7f98-127">Windows.Globalization.Language.TrySetInputMethodLanguageTag</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.globalization.language.trysetinputmethodlanguagetag.aspx)

## <a name="debugging-background-applications"></a><span data-ttu-id="e7f98-128">백그라운드 응용 프로그램 디버깅</span><span class="sxs-lookup"><span data-stu-id="e7f98-128">Debugging Background Applications</span></span>

<span data-ttu-id="e7f98-129">Windows IoT Core를 실행 하지 않는 장치에서 디버깅 하는 경우 다음 오류 메시지 중 하나가 표시 AllowEmbeddedMode 장치에서 사용 하 고 포함 된 모드 서비스가 실행 되 고 있는지 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e7f98-129">If you are debugging on a device that is not running Windows IoT Core and you see either of the following error messages you need to ensure AllowEmbeddedMode is enabled on the device and that the Embedded Mode service is running:</span></span>

* <span data-ttu-id="e7f98-130">끝점 매퍼에서 사용할 수 있는 끝점이 더 이상 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e7f98-130">There are no more endpoints available from the endpoint mapper.</span></span>
* <span data-ttu-id="e7f98-131">이 프로그램은 그룹 정책에 의해 차단 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e7f98-131">This program is blocked by group policy.</span></span> <span data-ttu-id="e7f98-132">자세한 내용은 시스템 관리자에 게 문의 합니다.</span><span class="sxs-lookup"><span data-stu-id="e7f98-132">For more information, contact your system administrator.</span></span>

## <a name="changing-the-mode"></a><span data-ttu-id="e7f98-133">모드 변경</span><span class="sxs-lookup"><span data-stu-id="e7f98-133">Changing the mode</span></span>
<span data-ttu-id="e7f98-134">이미징 및 구성 디자이너 (ICD) AllowEmbeddedMode 설정으로 프로 비전 패키지를 만들 해야 포함된 모드를 사용 하도록 설정 하려면 = 1입니다.</span><span class="sxs-lookup"><span data-stu-id="e7f98-134">To enable embedded mode you will need to create a provisioning package in Imaging and Configuration Designer (ICD) that sets AllowEmbeddedMode=1.</span></span>  <span data-ttu-id="e7f98-135">ICD를 설치 하려면 다운로드 하 고 Windows 10 용 Windows ADK를 설치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e7f98-135">To install ICD you need to download and install the Windows ADK for Windows 10.</span></span>

* [<span data-ttu-id="e7f98-136">Windows 10 용 Windows ADK 다운로드</span><span class="sxs-lookup"><span data-stu-id="e7f98-136">Download the Windows ADK for Windows 10</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=526740)
* [<span data-ttu-id="e7f98-137">Windows 10 용 Windows ADK의에서 새로운 기능 알아보기</span><span class="sxs-lookup"><span data-stu-id="e7f98-137">Learn about what's new in the Windows ADK for Windows 10</span></span>](https://msdn.microsoft.com/library/windows/hardware/dn927348(v=vs.85).aspx)

1. <span data-ttu-id="e7f98-138">ADK를 설치할 때 선택 **이미징 및 구성 디자이너 (ICD)**</span><span class="sxs-lookup"><span data-stu-id="e7f98-138">When installing the ADK select **Imaging and Configuration Designer (ICD)**</span></span>
2. <span data-ttu-id="e7f98-139">설치가 완료 된 후 Windows 이미징 및 구성 디자이너 (WICD)를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="e7f98-139">After installation is complete run Windows Imaging and Configuration Designer (WICD).</span></span>

    ![WICD 아이콘](../media/EmbeddedMode/WICD_Icon.png)

3. <span data-ttu-id="e7f98-141">**Advanced provisioning**(고급 프로비전)을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e7f98-141">Click **Advanced provisioning**.</span></span>  <span data-ttu-id="e7f98-142">프로젝트 이름을 **AllowEmbeddedMode** 누릅니다 **다음**합니다.</span><span class="sxs-lookup"><span data-stu-id="e7f98-142">Name the project **AllowEmbeddedMode** and click **Next**.</span></span>
    ![3 단계](../media/EmbeddedMode/Step3.png)

4. <span data-ttu-id="e7f98-144">선택할 **모든 Windows 버전에 공통적으로 적용** 한 다음 **다음**합니다.</span><span class="sxs-lookup"><span data-stu-id="e7f98-144">Choose **Common to all Windows editions** then **Next**.</span></span>
    ![4 단계](../media/EmbeddedMode/Step4.png)

5. <span data-ttu-id="e7f98-146">**마침**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e7f98-146">Click **Finish**.</span></span>

    ![5 단계](../media/EmbeddedMode/Step5.png)

6. <span data-ttu-id="e7f98-148">검색 상자에 입력 **EmbeddedMode** 를 클릭 하 고 **AllowEmbeddedMode**합니다.</span><span class="sxs-lookup"><span data-stu-id="e7f98-148">In the search box type **EmbeddedMode** and then click on **AllowEmbeddedMode**.</span></span>

    ![6 단계](../media/EmbeddedMode/Step6.png)

7. <span data-ttu-id="e7f98-150">창 가운데에 값을 설정 **AllowEmbeddedMode** 하 **예** ![Step7](../media/EmbeddedMode/Step7.png)</span><span class="sxs-lookup"><span data-stu-id="e7f98-150">In the center pane set the value of **AllowEmbeddedMode** to **Yes** ![Step7](../media/EmbeddedMode/Step7.png)</span></span>

8. <span data-ttu-id="e7f98-151">내보내기를 클릭 > 패키지를 프로 비전</span><span class="sxs-lookup"><span data-stu-id="e7f98-151">Click Export > Provisioning Package</span></span>

    ![Step8](../media/EmbeddedMode/Step8.png)

9. <span data-ttu-id="e7f98-153">다음을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e7f98-153">Click Next.</span></span>

    ![Step9](../media/EmbeddedMode/Step9.png)

10. <span data-ttu-id="e7f98-155">다음을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e7f98-155">Click Next.</span></span>

    ![Step10](../media/EmbeddedMode/Step10.png)

11. <span data-ttu-id="e7f98-157">다음을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e7f98-157">Click Next.</span></span>

    ![Step11](../media/EmbeddedMode/Step11.png)

12. <span data-ttu-id="e7f98-159">빌드를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e7f98-159">Click Build.</span></span>

    ![Step12](../media/EmbeddedMode/Step12.png)

13. <span data-ttu-id="e7f98-161">포함 된 모드를 설치 합니다. Windows IoT enterprise PPKG 두 번 클릭 합니다. PPKG 합니다.</span><span class="sxs-lookup"><span data-stu-id="e7f98-161">To install the embedded mode .PPKG on Windows IoT Enterprise double-click on the .PPKG.</span></span>

14. <span data-ttu-id="e7f98-162">클릭 **예, 추가**합니다.</span><span class="sxs-lookup"><span data-stu-id="e7f98-162">Click **Yes, add it**.</span></span>
    <span data-ttu-id="e7f98-163">LUA 대화 상자, 표시 되는 경우 예를 클릭 하 고 클릭 **예, 추가** 아래에 표시 된 대화 상자에서.</span><span class="sxs-lookup"><span data-stu-id="e7f98-163">Click yes on the LUA dialog if it appears, and the click **Yes, add it** on the dialog shown below.</span></span>
    ![Step14Standard](../media/EmbeddedMode/Step14Standard.png)


## <a name="configuring-a-background-application-to-run-automatically"></a><span data-ttu-id="e7f98-165">자동으로 실행 하는 백그라운드 응용 프로그램 구성</span><span class="sxs-lookup"><span data-stu-id="e7f98-165">Configuring a Background Application to Run automatically</span></span>
1. <span data-ttu-id="e7f98-166">지침에 따라 자동으로 실행 하는 백그라운드 응용 프로그램을 구성 하려면이 필요 [MinnowBoardMax SD 카드를 만듭니다](https://developer.microsoft.com/en-us/windows/iot/getstarted) 복사 `D:\windows\system32\iotstartup.exe` (d:가 SD 카드).</span><span class="sxs-lookup"><span data-stu-id="e7f98-166">To configure a Background Application to automatically run you will need to follow the directions to [create an MinnowBoardMax SD Card](https://developer.microsoft.com/en-us/windows/iot/getstarted) and copy `D:\windows\system32\iotstartup.exe` (where D: is your SD Card).</span></span>

2. <span data-ttu-id="e7f98-167">설치 된 백그라운드 응용 프로그램 유형 목록을 가져오려면:</span><span class="sxs-lookup"><span data-stu-id="e7f98-167">To get a list of installed Background Applications type:</span></span>

        C:\> iotstartup list BackgroundApplication1

3. <span data-ttu-id="e7f98-168">출력은 다음과 같이 표시 됩니다는 각 설치 된 백그라운드 응용 프로그램에서의 전체 이름을 포함 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e7f98-168">The output should include the full name of each installed Background Application, which will look like this:</span></span>

        Headless : BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpvee

5. <span data-ttu-id="e7f98-169">부팅 유형에 실행 되도록이 앱을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="e7f98-169">To configure this app to run at boot type:</span></span>

        C:\> iotstartup add headless BackgroundApplication1

6. <span data-ttu-id="e7f98-170">백그라운드 응용 프로그램이 성공적으로 시작 목록에 추가 된 경우이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e7f98-170">If the Background Application has been successfully added to the startup list you should see this:</span></span>

        Added Headless: BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpveeplication1

7. <span data-ttu-id="e7f98-171">포함 된 모드 장치를 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="e7f98-171">Restart the embedded mode device:</span></span>

8. <span data-ttu-id="e7f98-172">장치를 다시 시작한 후 백그라운드 응용 프로그램에 자동으로 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e7f98-172">Once the device has restarted, your Background Application will start automatically.</span></span>  <span data-ttu-id="e7f98-173">백그라운드 응용 프로그램을 관리 하는 포함 된 모드를 시작 하려면 몇 분 정도 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e7f98-173">The Embedded Mode service which manages Background Applications can take a few minutes to start.</span></span>  <span data-ttu-id="e7f98-174">포함된 모드를 시작 프로그램 목록에서 백그라운드 응용 프로그램을 모니터링 하 고는 중지 되 면 다시 시작 가져오기 있는지 확인 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e7f98-174">The embedded mode service will monitor Background Applications on the startup list and make sure they get restarted if they stops.</span></span>  <span data-ttu-id="e7f98-175">짧은 기간에 여러 번 백그라운드 응용 프로그램을 중지 하는 경우 더 이상 시작할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e7f98-175">If a Background Application stops several times in a short period of time it will no longer be restarted.</span></span>

9. <span data-ttu-id="e7f98-176">시작 목록 형식에서 백그라운드 응용 프로그램을 제거:</span><span class="sxs-lookup"><span data-stu-id="e7f98-176">To remove your Background Application from the startup list type:</span></span>

        C:\> iotstartup remove headless BackgroundApplication1

10. <span data-ttu-id="e7f98-177">백그라운드 응용 프로그램 구동 목록에서 제거 되 면 다음과 같은 출력이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e7f98-177">If the Background Application is removed from the startup list the output will look like this:</span></span>

        Removed headless: BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpvee
