---
title: 백그라운드 응용 프로그램
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: IoT 장치용 백그라운드 응용 프로그램을 개발 하는 방법을 알아봅니다.
keywords: windows iot, 백그라운드 응용 프로그램
ms.openlocfilehash: 1b3fd831a4cdf3ebb8bc2d80c544344b13115617
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "60167893"
---
# <a name="developing-background-applications"></a><span data-ttu-id="5802b-104">백그라운드 응용 프로그램 개발</span><span class="sxs-lookup"><span data-stu-id="5802b-104">Developing Background Applications</span></span>

> [!NOTE]
> <span data-ttu-id="5802b-105">Visual Studio에서 액세스할 수 있는 RS4 이상의 SDK를 설치하지 않으면 RS5(또는 OpenSSH를 사용하는 RS4) IoT 이미지에 배포할 때 Visual Studio가 암호화 오류를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="5802b-105">Visual Studio will generate a cryptic error when deploying to a RS5 (or RS4 with OpenSSH enabled) IoT image unless a SDK from RS4 or greater is installed that Visual Studio can access.</span></span>

<span data-ttu-id="5802b-106">백그라운드 응용 프로그램은 직접 UI가 없는 응용 프로그램입니다.</span><span class="sxs-lookup"><span data-stu-id="5802b-106">Background applications are applications that have no direct UI.</span></span> <span data-ttu-id="5802b-107">배포 및 구성 되 면 이러한 응용 프로그램은 컴퓨터 시작 시 시작 되 고 프로세스 수명 관리 리소스 사용 제한 없이 계속 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5802b-107">Once deployed and configured, these applications launch at machine startup and run continuously without any process lifetime management resource use limitations.</span></span> <span data-ttu-id="5802b-108">충돌이 발생 하거나 종료 되 면 시스템은 자동으로 다시 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5802b-108">If they crash or exit the system will automatically restart them.</span></span>
<span data-ttu-id="5802b-109">이러한 백그라운드 응용 프로그램은 매우 간단한 실행 모델을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="5802b-109">These Background Applications have a very simple execution model.</span></span> <span data-ttu-id="5802b-110">템플릿은 "IBackgroundTask" 인터페이스를 구현 하 고 빈 "Run" 메서드를 생성 하는 클래스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5802b-110">The templates create a class that implements the "IBackgroundTask" interface and generates the empty "Run" method.</span></span> <span data-ttu-id="5802b-111">이 "실행" 메서드는 응용 프로그램에 대 한 진입점입니다.</span><span class="sxs-lookup"><span data-stu-id="5802b-111">This "Run" method is the entry point to your application.</span></span>

![백그라운드 작업](../media/BackgroundApplications/backgroundTaskScreenshot.png)

<span data-ttu-id="5802b-113">한 가지 중요 한 점이 있습니다. 기본적으로 실행 메서드가 완료 되 면 응용 프로그램이 종료 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5802b-113">There is one critical point to note: by default, the application will shut down when the run method completes.</span></span> <span data-ttu-id="5802b-114">즉, 입력을 기다리는 서버 또는 타이머를 실행 하는 일반적인 IoT 패턴을 따르는 앱은 앱 종료를 중간에 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="5802b-114">This means that apps that follow the common IoT pattern of running a server waiting for input or on a timer will find the app exit prematurely.</span></span> <span data-ttu-id="5802b-115">이러한 상황이 발생 하지 않도록 하려면 "GetDeferral" 메서드를 호출 하 여 응용 프로그램을 종료 하지 않도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5802b-115">To prevent this from happening you must call the "GetDeferral" method to prevent the application from exiting.</span></span> <span data-ttu-id="5802b-116">지연 패턴에 대 한 자세한 내용은 [여기](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Background.BackgroundTaskDeferral)에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5802b-116">You can find more information on the deferral pattern [here](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Background.BackgroundTaskDeferral).</span></span>

## <a name="where-can-background-applications-be-installed-from"></a><span data-ttu-id="5802b-117">백그라운드 응용 프로그램은 어디에서 설치할 수 있나요?</span><span class="sxs-lookup"><span data-stu-id="5802b-117">Where can Background Applications be installed from?</span></span> 

<span data-ttu-id="5802b-118">[여기](https://go.microsoft.com/fwlink/?linkid=847472)에서 Visual Studio 갤러리의 배경 응용 프로그램을 사용 하도록 설정 하는 IoT 템플릿을 다운로드 하 고 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5802b-118">You can download and install IoT templates to enable Background Applications from the Visual Studio Gallery [here](https://go.microsoft.com/fwlink/?linkid=847472).</span></span>  <span data-ttu-id="5802b-119">또는 `Windows IoT Core Project Templates` [visual studio 갤러리](https://visualstudiogallery.msdn.microsoft.com/) 에서를 검색 하거나 확장 및 업데이트 대화 상자 (도구 > 확장 및 업데이트 > 온라인)에서 직접 검색 하 여 템플릿을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5802b-119">Alternatively, the templates can be found by searching for `Windows IoT Core Project Templates` in the [Visual Studio Gallery](https://visualstudiogallery.msdn.microsoft.com/) or directly from Visual Studio in the Extension and Updates dialog (Tools > Extensions and Updates > Online).</span></span>

## <a name="what-languages-are-available"></a><span data-ttu-id="5802b-120">사용할 수 있는 언어는 무엇 인가요?</span><span class="sxs-lookup"><span data-stu-id="5802b-120">What languages are available?</span></span>

<span data-ttu-id="5802b-121">**IoT (백그라운드 응용 프로그램)** 템플릿은 다음에 대해 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5802b-121">**Background Application (IoT)** templates can be found for:</span></span>

* <span data-ttu-id="5802b-122">**C++** `File > New > Project > Installed > Visual C++ > Windows > Windows IoT Core`</span><span class="sxs-lookup"><span data-stu-id="5802b-122">**C++** `File > New > Project > Installed > Visual C++ > Windows > Windows IoT Core`</span></span>
* <span data-ttu-id="5802b-123">**C#** `File > New > Project > Installed > Visual C# > Windows > Windows IoT Core`</span><span class="sxs-lookup"><span data-stu-id="5802b-123">**C#** `File > New > Project > Installed > Visual C# > Windows > Windows IoT Core`</span></span>
* <span data-ttu-id="5802b-124">**Visual Basic**`File > New > Project > Installed > Visual Basic > Windows > Windows IoT Core`</span><span class="sxs-lookup"><span data-stu-id="5802b-124">**Visual Basic** `File > New > Project > Installed > Visual Basic > Windows > Windows IoT Core`</span></span>
* <span data-ttu-id="5802b-125">**JavaScript**`File > New > Project > Installed > JavaScript > Windows > Windows IoT Core`</span><span class="sxs-lookup"><span data-stu-id="5802b-125">**JavaScript** `File > New > Project > Installed > JavaScript > Windows > Windows IoT Core`</span></span>

## <a name="how-are-background-applications-used"></a><span data-ttu-id="5802b-126">백그라운드 응용 프로그램 사용 방법</span><span class="sxs-lookup"><span data-stu-id="5802b-126">How are background applications used?</span></span> 

<span data-ttu-id="5802b-127">백그라운드 응용 프로그램을 만드는 것은 백그라운드 작업을 만드는 것과 매우 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="5802b-127">Creating a background application is very similar to creating a Background Task.</span></span>  <span data-ttu-id="5802b-128">백그라운드 응용 프로그램이 시작 되 면 Run 메서드를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="5802b-128">When the Background Application starts, the Run method is called:</span></span>

```csharp
public void Run(IBackgroundTaskInstance taskInstance)
{
}
```

<span data-ttu-id="5802b-129">지연 개체를 만들지 않는 한 실행 메서드가 종료 되 면 백그라운드 응용 프로그램이 종료 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5802b-129">When the Run method ends, unless a deferral object is created, the background application ends.</span></span> <span data-ttu-id="5802b-130">비동기 프로그래밍에 대 한 일반적인 방법은 다음과 같이 지연 되는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="5802b-130">The common practice, for asynchronous programming is to take a deferral like this:</span></span>

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

<span data-ttu-id="5802b-131">지연이 발생 하면 지연 개체의 Complete 메서드가 호출 될 때까지 백그라운드 응용 프로그램은 계속 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5802b-131">Once a deferral is taken, the background application will continue until the deferral object's Complete method is called.</span></span>

```csharp
deferral.Complete();
```

## <a name="how-do-background-applications-start"></a><span data-ttu-id="5802b-132">백그라운드 응용 프로그램을 시작 하는 방법</span><span class="sxs-lookup"><span data-stu-id="5802b-132">How do background applications start?</span></span>

<span data-ttu-id="5802b-133">이 질문은 배포 및 호출로 나눌 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5802b-133">This question can be broken into deployment and invocation.</span></span>  

<span data-ttu-id="5802b-134">백그라운드 응용 프로그램을 배포 하려면 다음 중 하나를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="5802b-134">To deploy a background application, you can either:</span></span>

* <span data-ttu-id="5802b-135">Visual Studio의 F5 키 (빌드, 배포 및 호출)를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="5802b-135">Use Visual Studio's F5 (which will build, deploy and invoke).</span></span>  <span data-ttu-id="5802b-136">자세한 내용은 Visual Studio에서 배포 및 시작 하는 방법을 설명 하는 [Hello World 샘플](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/HelloWorld) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5802b-136">For more details, see our [Hello World sample](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/HelloWorld) where we describe how to deploy and launch from Visual Studio.</span></span>

> [!NOTE]
> <span data-ttu-id="5802b-137">그러면 장치가 부팅 될 때 백그라운드 응용 프로그램이 시작 되도록 구성 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5802b-137">This will not configure your background application to start when the device boots.</span></span>

* <span data-ttu-id="5802b-138">프로젝트 > 스토어 > 앱 패키지 만들기를 선택 하 여 Visual Studio에서 AppX를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5802b-138">Create an AppX in Visual Studio by selecting Project > Store > Create App Packages.</span></span>  <span data-ttu-id="5802b-139">AppX를 만든 후 [Windows 장치 포털](../manage-your-device/DevicePortal.md) 을 사용 하 여 Windows 10 IoT Core 장치에 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5802b-139">Once you have created an AppX, you can use [Windows Device Portal](../manage-your-device/DevicePortal.md) to deploy it to your Windows 10 IoT Core device.</span></span>

<span data-ttu-id="5802b-140">백그라운드 응용 프로그램을 호출 하기 위해 다음 중 하나를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5802b-140">To invoke a background application, you can either:</span></span>

* <span data-ttu-id="5802b-141">위에서 설명한 것 처럼 Visual Studio의 F5 기능을 통해 백그라운드 응용 프로그램을 배포 하 고 즉시 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5802b-141">As mentioned above, Visual Studio's F5 functionality will deploy and immediately start your Background Application.</span></span>

> [!NOTE]
> <span data-ttu-id="5802b-142">그러면 장치가 부팅 될 때 백그라운드 응용 프로그램이 시작 되도록 구성 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5802b-142">This will not configure your background application to start when the device boots.</span></span>

* <span data-ttu-id="5802b-143">IoT 장치에 배포 된 백그라운드 응용 프로그램의 경우, i이상 시작 .exe 유틸리티를 사용 하 여 장치가 부팅 될 때 백그라운드 응용 프로그램이 시작 되도록 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5802b-143">For a background application that has been deployed to an IoT device, you can use the iotstartup.exe utility to configure your background application to start when the device boots.</span></span>  <span data-ttu-id="5802b-144">백그라운드 응용 프로그램을 시작 앱으로 지정 하려면 다음 지침을 따르세요. (아래에 대 한 `BackgroundApplication1` **앱 이름을 대체** 합니다.)</span><span class="sxs-lookup"><span data-stu-id="5802b-144">To specify your background application as a Startup App, follow these instructions (**substitute your app's name** for `BackgroundApplication1` below):</span></span>

1. <span data-ttu-id="5802b-145">[여기](../connect-your-device/PowerShell.md)에 설명 된 대로 Windows IoT Core 장치로 POWERSHELL (PS) 세션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="5802b-145">Start a PowerShell (PS) session with your Windows IoT Core device as described [here](../connect-your-device/PowerShell.md).</span></span>

2. <span data-ttu-id="5802b-146">PS 세션에서 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="5802b-146">From the PS session, type:</span></span>
            
`[<your IP address>]: PS C:\> iotstartup list BackgroundApplication1`

3. <span data-ttu-id="5802b-147">백그라운드 응용 프로그램의 전체 이름이 표시 됩니다. 예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="5802b-147">You should see the full name of your background application, i.e. something like:</span></span>

`Headed   : BackgroundApplication1-uwp_cqewk5knvpvee!App
Headless : BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpvee`

4. <span data-ttu-id="5802b-148">이 유틸리티는 백그라운드 응용 프로그램이 ' 헤드리스 ' 응용 프로그램 인지 확인 하 고 올바르게 설치 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="5802b-148">The utility is confirming that your background application is an 'headless' application, and is installed correctly.</span></span>  <span data-ttu-id="5802b-149">배경 응용 프로그램의 경우에도 항목을 볼 수 있지만 무시 해도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5802b-149">You will likely see a Headed entry as well for your Background Applications, but this can be disregarded.</span></span>

5. <span data-ttu-id="5802b-150">이제이 앱을 ' 시작 앱 '으로 쉽게 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5802b-150">Now, it's easy to set this app as a 'Startup App'.</span></span> <span data-ttu-id="5802b-151">다음 명령을 입력 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5802b-151">Just type the command:</span></span>

`[<your IP address>]: PS C:\> iotstartup add headless BackgroundApplication1`

6. <span data-ttu-id="5802b-152">이 유틸리티는 배경 응용 프로그램이 헤드리스 ' 시작 앱 ' 목록에 추가 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="5802b-152">The utility will confirm that your background application has been added to the list of headless 'Startup Apps':</span></span>

`Added Headless: BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpveeplication1`

7. <span data-ttu-id="5802b-153">계속 진행 하 여 Windows IoT Core 장치를 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="5802b-153">Go ahead and restart your Windows IoT Core device.</span></span> <span data-ttu-id="5802b-154">PS 세션에서 shutdown 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5802b-154">From the PS session, you can issue the shutdown command:</span></span>

`[<your IP address>]: PS C:\> shutdown /r /t 0`

8. <span data-ttu-id="5802b-155">장치가 다시 시작 되 면 백그라운드 응용 프로그램이 자동으로 시작 되 고 Windows 10 IoT Core는 중지 될 때마다 다시 시작 되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="5802b-155">Once the device has restarted, your background application will start automatically and Windows 10 IoT Core will make sure that it gets restarted anytime it stops.</span></span>  

> [!NOTE]
> <span data-ttu-id="5802b-156">백그라운드 앱이 자동으로 실행 되도록 등록 되 면 앱이 종료 되거나 충돌 하는 경우 자동으로 다시 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5802b-156">Once a background app is registered to run automatically, if the app exits or crashes it will be automatically restarted.</span></span>  <span data-ttu-id="5802b-157">앱은 시작 되거나 다시 시작 되는 이유를 알 수 없으므로, 다시 시작 시 특별 한 작업을 수행 하려는 경우 앱에서 앱 상태를 추적 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5802b-157">The app isn't informed of the reason that it's being started or restarted so if you want to take special action on a restart you will need to track the app state in your app.</span></span>

9. <span data-ttu-id="5802b-158">다음 명령을 입력 하 여 헤드리스 시작 앱 목록에서 백그라운드 응용 프로그램을 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5802b-158">You can remove your background application from the list of headless Startup Apps by typing the command:</span></span>

`[<your IP address>]: PS C:\> iotstartup remove headless BackgroundApplication1`

10. <span data-ttu-id="5802b-159">이 유틸리티는 배경 응용 프로그램이 헤드리스 ' 시작 앱 ' 목록에서 제거 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="5802b-159">The utility will confirm that your background application has been removed from the list of headless 'Startup Apps':</span></span>

`Removed headless: BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpvee`

# <a name="see-also"></a><span data-ttu-id="5802b-160">관련 항목</span><span class="sxs-lookup"><span data-stu-id="5802b-160">See Also</span></span>
<span data-ttu-id="5802b-161">사용자 지정 이미지를 빌드할 때 백그라운드 앱을 추가 하려면 [Appx 패키지 만들기](../build-your-image/createinstallpackage.md) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5802b-161">To add a background app when building a custom image see [Create an Appx package](../build-your-image/createinstallpackage.md)</span></span>
