---
title: 백그라운드 응용 프로그램
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: IoT 장치에 대 한 백그라운드 응용 프로그램을 개발 하는 방법에 알아봅니다.
keywords: windows iot, 백그라운드 응용 프로그램
ms.openlocfilehash: 1b3fd831a4cdf3ebb8bc2d80c544344b13115617
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512917"
---
# <a name="developing-background-applications"></a><span data-ttu-id="ce249-104">백그라운드 응용 프로그램 개발</span><span class="sxs-lookup"><span data-stu-id="ce249-104">Developing Background Applications</span></span>

> [!NOTE]
> <span data-ttu-id="ce249-105">Visual Studio는 RS5를 배포 하는 경우 암호화 오류가 생성 됩니다 (또는 RS4 OpenSSH 사용 하 여 사용 하도록 설정) IoT 이미지에서 RS4 이상 SDK는 Visual Studio에 액세스할 수 있도록 설치 되어 있지 않으면입니다.</span><span class="sxs-lookup"><span data-stu-id="ce249-105">Visual Studio will generate a cryptic error when deploying to a RS5 (or RS4 with OpenSSH enabled) IoT image unless a SDK from RS4 or greater is installed that Visual Studio can access.</span></span>

<span data-ttu-id="ce249-106">백그라운드 응용 프로그램은 UI가 없는 직접 응용 프로그램.</span><span class="sxs-lookup"><span data-stu-id="ce249-106">Background applications are applications that have no direct UI.</span></span> <span data-ttu-id="ce249-107">배포 후 구성 된 이러한 응용 프로그램 컴퓨터 시작 시 시작 하 고 모든 프로세스 수명 관리 리소스 사용 제한 없이 계속 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce249-107">Once deployed and configured, these applications launch at machine startup and run continuously without any process lifetime management resource use limitations.</span></span> <span data-ttu-id="ce249-108">충돌 하거나 종료 시스템은 자동으로 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce249-108">If they crash or exit the system will automatically restart them.</span></span>
<span data-ttu-id="ce249-109">이러한 백그라운드 응용 프로그램에는 매우 간단한 실행 모델이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce249-109">These Background Applications have a very simple execution model.</span></span> <span data-ttu-id="ce249-110">템플릿을 "IBackgroundTask" 인터페이스를 구현 하 고 빈 "Run" 메서드를 생성 하는 클래스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ce249-110">The templates create a class that implements the "IBackgroundTask" interface and generates the empty "Run" method.</span></span> <span data-ttu-id="ce249-111">이 "실행" 메서드는 응용 프로그램 진입점입니다.</span><span class="sxs-lookup"><span data-stu-id="ce249-111">This "Run" method is the entry point to your application.</span></span>

![백그라운드 작업](../media/BackgroundApplications/backgroundTaskScreenshot.png)

<span data-ttu-id="ce249-113">점이 하나 위험 지점이: 기본적으로 응용 프로그램 종료 실행된 메서드를 완료 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce249-113">There is one critical point to note: by default, the application will shut down when the run method completes.</span></span> <span data-ttu-id="ce249-114">이 입력 또는 타이머 대기 서버를 실행 하는 일반적인 IoT 패턴을 따르는 앱 중간 앱 종료를 찾을 수는 것을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce249-114">This means that apps that follow the common IoT pattern of running a server waiting for input or on a timer will find the app exit prematurely.</span></span> <span data-ttu-id="ce249-115">이를 방지 하려면 응용 프로그램 종료를 방지 하기 위해 "GetDeferral" 메서드를 호출 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce249-115">To prevent this from happening you must call the "GetDeferral" method to prevent the application from exiting.</span></span> <span data-ttu-id="ce249-116">지연 패턴에 대 한 자세한 정보를 찾을 수 있습니다 [여기](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Background.BackgroundTaskDeferral)합니다.</span><span class="sxs-lookup"><span data-stu-id="ce249-116">You can find more information on the deferral pattern [here](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Background.BackgroundTaskDeferral).</span></span>

## <a name="where-can-background-applications-be-installed-from"></a><span data-ttu-id="ce249-117">여기서 백그라운드 응용 프로그램에서 설치할 수 있습니까?</span><span class="sxs-lookup"><span data-stu-id="ce249-117">Where can Background Applications be installed from?</span></span> 

<span data-ttu-id="ce249-118">다운로드 하 고 Visual Studio 갤러리의 백그라운드 응용 프로그램을 사용 하도록 설정 하려면 IoT 템플릿을 설치할 수 있습니다 [여기](https://go.microsoft.com/fwlink/?linkid=847472)합니다.</span><span class="sxs-lookup"><span data-stu-id="ce249-118">You can download and install IoT templates to enable Background Applications from the Visual Studio Gallery [here](https://go.microsoft.com/fwlink/?linkid=847472).</span></span>  <span data-ttu-id="ce249-119">또는 검색 하 여 템플릿을 찾을 수 있습니다 `Windows IoT Core Project Templates` 에 [Visual Studio 갤러리](https://visualstudiogallery.msdn.microsoft.com/) 또는 확장 및 업데이트 대화 상자에서 Visual Studio에서 직접 (도구 > 확장 및 업데이트 > 온라인).</span><span class="sxs-lookup"><span data-stu-id="ce249-119">Alternatively, the templates can be found by searching for `Windows IoT Core Project Templates` in the [Visual Studio Gallery](https://visualstudiogallery.msdn.microsoft.com/) or directly from Visual Studio in the Extension and Updates dialog (Tools > Extensions and Updates > Online).</span></span>

## <a name="what-languages-are-available"></a><span data-ttu-id="ce249-120">어떤 언어로 제공 되나요?</span><span class="sxs-lookup"><span data-stu-id="ce249-120">What languages are available?</span></span>

<span data-ttu-id="ce249-121">**응용 프로그램 (IoT) 백그라운드** 에 대 한 템플릿을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce249-121">**Background Application (IoT)** templates can be found for:</span></span>

* **<span data-ttu-id="ce249-122">C++</span><span class="sxs-lookup"><span data-stu-id="ce249-122">C++</span></span>** `File > New > Project > Installed > Visual C++ > Windows > Windows IoT Core`
* **<span data-ttu-id="ce249-123">C#</span><span class="sxs-lookup"><span data-stu-id="ce249-123">C#</span></span>** `File > New > Project > Installed > Visual C# > Windows > Windows IoT Core`
* **<span data-ttu-id="ce249-124">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ce249-124">Visual Basic</span></span>** `File > New > Project > Installed > Visual Basic > Windows > Windows IoT Core`
* **<span data-ttu-id="ce249-125">JavaScript</span><span class="sxs-lookup"><span data-stu-id="ce249-125">JavaScript</span></span>** `File > New > Project > Installed > JavaScript > Windows > Windows IoT Core`

## <a name="how-are-background-applications-used"></a><span data-ttu-id="ce249-126">백그라운드 응용 프로그램을 사용 하는 방법</span><span class="sxs-lookup"><span data-stu-id="ce249-126">How are background applications used?</span></span> 

<span data-ttu-id="ce249-127">백그라운드 응용 프로그램 만들기를 백그라운드 작업을 만드는 매우 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="ce249-127">Creating a background application is very similar to creating a Background Task.</span></span>  <span data-ttu-id="ce249-128">백그라운드 응용 프로그램이 시작 되 면 Run 메서드가 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce249-128">When the Background Application starts, the Run method is called:</span></span>

```csharp
public void Run(IBackgroundTaskInstance taskInstance)
{
}
```

<span data-ttu-id="ce249-129">Run 메서드가 종료 지연 개체를 만들지 않으면 백그라운드 응용 프로그램이 종료 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce249-129">When the Run method ends, unless a deferral object is created, the background application ends.</span></span> <span data-ttu-id="ce249-130">비동기 프로그래밍에 대 한 일반적으로, 다음과 같습니다. 이와 같은 지연 수행</span><span class="sxs-lookup"><span data-stu-id="ce249-130">The common practice, for asynchronous programming is to take a deferral like this:</span></span>

```csharp
private BackgroundTaskDeferral deferral;
public void Run(IBackgroundTaskInstance taskInstance)
{
    deferral = taskInstance.GetDeferral();
    
    //
    // TODO: Insert code to start one or more asynchronous methods
    //
}
```

<span data-ttu-id="ce249-131">지연은 수행 되지 않고 백그라운드 응용 프로그램이 deferral 개체의 Complete 메서드를 호출할 때까지 계속 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce249-131">Once a deferral is taken, the background application will continue until the deferral object's Complete method is called.</span></span>

```csharp
deferral.Complete();
```

## <a name="how-do-background-applications-start"></a><span data-ttu-id="ce249-132">백그라운드 응용 프로그램을 시작 하려면 어떻게?</span><span class="sxs-lookup"><span data-stu-id="ce249-132">How do background applications start?</span></span>

<span data-ttu-id="ce249-133">이 질문은 배포 및 호출으로 분류할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce249-133">This question can be broken into deployment and invocation.</span></span>  

<span data-ttu-id="ce249-134">백그라운드 응용 프로그램을 배포 하려면 다음 하거나 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce249-134">To deploy a background application, you can either:</span></span>

* <span data-ttu-id="ce249-135">Visual Studio F5 (하는 빌드, 배포 호출)를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce249-135">Use Visual Studio's F5 (which will build, deploy and invoke).</span></span>  <span data-ttu-id="ce249-136">자세한 내용은 참조 하세요. 당사의 [헬로 월드 샘플](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/HelloWorld) 배포 하 고 Visual Studio에서 시작 하는 방법을 설명 하는 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce249-136">For more details, see our [Hello World sample](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/HelloWorld) where we describe how to deploy and launch from Visual Studio.</span></span>

> [!NOTE]
> <span data-ttu-id="ce249-137">이 장치를 부팅할 때도 시작 하도록 백그라운드 응용 프로그램을 구성 하지 않을 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="ce249-137">This will not configure your background application to start when the device boots.</span></span>

* <span data-ttu-id="ce249-138">Visual Studio에서 프로젝트를 선택 하 여 AppX를 만들기 > 저장소 > 앱 패키지 만들기.</span><span class="sxs-lookup"><span data-stu-id="ce249-138">Create an AppX in Visual Studio by selecting Project > Store > Create App Packages.</span></span>  <span data-ttu-id="ce249-139">AppX를 만든 후 사용할 수 있습니다 [Windows Device Portal](../manage-your-device/DevicePortal.md) Windows 10 IoT Core 장치에 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce249-139">Once you have created an AppX, you can use [Windows Device Portal](../manage-your-device/DevicePortal.md) to deploy it to your Windows 10 IoT Core device.</span></span>

<span data-ttu-id="ce249-140">백그라운드 응용 프로그램을 호출 하기 위해 제출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce249-140">To invoke a background application, you can either:</span></span>

* <span data-ttu-id="ce249-141">위에서 설명한 대로 Visual Studio F5 기능 배포를 업데이트 하 고 백그라운드 응용 프로그램을 즉시 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce249-141">As mentioned above, Visual Studio's F5 functionality will deploy and immediately start your Background Application.</span></span>

> [!NOTE]
> <span data-ttu-id="ce249-142">이 장치를 부팅할 때도 시작 하도록 백그라운드 응용 프로그램을 구성 하지 않을 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="ce249-142">This will not configure your background application to start when the device boots.</span></span>

* <span data-ttu-id="ce249-143">IoT 장치에 배포 된 백그라운드 응용 프로그램을 시작할 장치를 부팅할 때 백그라운드 응용 프로그램을 구성 하려면 iotstartup.exe 유틸리티를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce249-143">For a background application that has been deployed to an IoT device, you can use the iotstartup.exe utility to configure your background application to start when the device boots.</span></span>  <span data-ttu-id="ce249-144">백그라운드 응용 프로그램에 앱을 시작으로 지정 하려면 다음이 지침을 따릅니다 (**앱의 이름으로 대체** 에 대 한 `BackgroundApplication1` 아래).</span><span class="sxs-lookup"><span data-stu-id="ce249-144">To specify your background application as a Startup App, follow these instructions (**substitute your app's name** for `BackgroundApplication1` below):</span></span>

1. <span data-ttu-id="ce249-145">설명 된 대로 Windows IoT Core 장치를 사용 하 여 PS (PowerShell) 세션을 시작 [여기](../connect-your-device/PowerShell.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="ce249-145">Start a PowerShell (PS) session with your Windows IoT Core device as described [here](../connect-your-device/PowerShell.md).</span></span>

2. <span data-ttu-id="ce249-146">PS 세션에서 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce249-146">From the PS session, type:</span></span>
            
`[<your IP address>]: PS C:\> iotstartup list BackgroundApplication1`

3. <span data-ttu-id="ce249-147">즉, 같은 백그라운드 응용 프로그램의 전체 이름을 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce249-147">You should see the full name of your background application, i.e. something like:</span></span>

`Headed   : BackgroundApplication1-uwp_cqewk5knvpvee!App
Headless : BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpvee`

4. <span data-ttu-id="ce249-148">유틸리티는 백그라운드 응용 프로그램 '헤드리스' 응용 프로그램은 하 고이 올바르게 설치 되어 있는지 확인 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce249-148">The utility is confirming that your background application is an 'headless' application, and is installed correctly.</span></span>  <span data-ttu-id="ce249-149">표시 될 가능성이 높습니다 Headed 항목을도 백그라운드 응용 프로그램에 대 한 있지만이 무시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce249-149">You will likely see a Headed entry as well for your Background Applications, but this can be disregarded.</span></span>

5. <span data-ttu-id="ce249-150">이제 ' 시작 ' 앱으로이 앱을 설정 하기 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="ce249-150">Now, it's easy to set this app as a 'Startup App'.</span></span> <span data-ttu-id="ce249-151">명령을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce249-151">Just type the command:</span></span>

`[<your IP address>]: PS C:\> iotstartup add headless BackgroundApplication1`

6. <span data-ttu-id="ce249-152">유틸리티는 백그라운드 응용 프로그램에 헤드리스 ' 시작 앱 ' 목록에 추가 되었는지 확인 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce249-152">The utility will confirm that your background application has been added to the list of headless 'Startup Apps':</span></span>

`Added Headless: BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpveeplication1`

7. <span data-ttu-id="ce249-153">계속 해 서 Windows IoT Core 장치 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce249-153">Go ahead and restart your Windows IoT Core device.</span></span> <span data-ttu-id="ce249-154">PS 세션에서를 종료 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce249-154">From the PS session, you can issue the shutdown command:</span></span>

`[<your IP address>]: PS C:\> shutdown /r /t 0`

8. <span data-ttu-id="ce249-155">장치를 다시 시작한 후 백그라운드 응용 프로그램은 자동으로 시작 하 고 Windows 10 IoT Core 중지 언제 든 지 다시 가져옵니다 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce249-155">Once the device has restarted, your background application will start automatically and Windows 10 IoT Core will make sure that it gets restarted anytime it stops.</span></span>  

> [!NOTE]
> <span data-ttu-id="ce249-156">앱 종료 또는 충돌 하는 경우 자동으로 실행 하는 백그라운드 앱 등록 되 면 자동으로 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce249-156">Once a background app is registered to run automatically, if the app exits or crashes it will be automatically restarted.</span></span>  <span data-ttu-id="ce249-157">앱이 시작 되 고 또는 앱에서 앱 상태를 추적 해야 다시 시작 시 특수 한 작업을 수행 하려는 경우에이 다시 시작 이유 내용 알림이 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ce249-157">The app isn't informed of the reason that it's being started or restarted so if you want to take special action on a restart you will need to track the app state in your app.</span></span>

9. <span data-ttu-id="ce249-158">헤드리스 시작 앱 목록에서 명령을 입력 하 여 백그라운드 응용 프로그램을 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce249-158">You can remove your background application from the list of headless Startup Apps by typing the command:</span></span>

`[<your IP address>]: PS C:\> iotstartup remove headless BackgroundApplication1`

10. <span data-ttu-id="ce249-159">유틸리티는 백그라운드 응용 프로그램가 제거 된 앱 목록에서 헤드리스 ' 시작 ' 확인:</span><span class="sxs-lookup"><span data-stu-id="ce249-159">The utility will confirm that your background application has been removed from the list of headless 'Startup Apps':</span></span>

`Removed headless: BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpvee`

# <a name="see-also"></a><span data-ttu-id="ce249-160">관련 항목</span><span class="sxs-lookup"><span data-stu-id="ce249-160">See Also</span></span>
<span data-ttu-id="ce249-161">백그라운드 앱을 사용자 지정 이미지 참조를 빌드할 때 추가할 [Appx 패키지 만들기](../build-your-image/createinstallpackage.md)</span><span class="sxs-lookup"><span data-stu-id="ce249-161">To add a background app when building a custom image see [Create an Appx package](../build-your-image/createinstallpackage.md)</span></span>
