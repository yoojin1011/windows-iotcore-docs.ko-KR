---
title: Windows 10 IoT Core 기본 앱
author: saraclay
ms.author: saclayt
ms.date: 08/08/2018
ms.topic: article
description: Windows 10 IoT Core 기본 앱 및 해당 기능에 대해 알아봅니다.
keywords: windows iot, windows 10 iot core, 기본 앱
ms.custom: RS5
ms.openlocfilehash: 12baa759c9085360431c2b7f87f72816cd24680b
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "60168025"
---
# <a name="windows-10-iot-core-default-app-overview"></a><span data-ttu-id="a6308-104">Windows 10 IoT Core 기본 앱 개요</span><span class="sxs-lookup"><span data-stu-id="a6308-104">Windows 10 IoT Core Default App Overview</span></span>

> [!TIP]
> <span data-ttu-id="a6308-105">이 샘플 앱에 추가 된 기능을 확인 하려는 경우 GitHub에서 [문제를 열어](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoredefaultapp) 알려주세요.</span><span class="sxs-lookup"><span data-stu-id="a6308-105">If you find that you'd like to see a feature added to this sample app, [open an issue](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoredefaultapp) on GitHub to let us know.</span></span> <span data-ttu-id="a6308-106">버그를 파일로 보내려면 [여기](https://social.msdn.microsoft.com/Forums/en-US/fad1c6a0-e578-44a7-8e8d-95cc28c06ccd/need-logs-if-your-device-hasnt-updated-to-the-latest-iotcore-version?forum=WindowsIoT)에서 피드백 허브에 대 한 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="a6308-106">If you'd like to file a bug, follow the instructions for the Feedback Hub [here](https://social.msdn.microsoft.com/Forums/en-US/fad1c6a0-e578-44a7-8e8d-95cc28c06ccd/need-logs-if-your-device-hasnt-updated-to-the-latest-iotcore-version?forum=WindowsIoT).</span></span>

<span data-ttu-id="a6308-107">처음에 Windows 10 IoT Core를 플래시 하면 시작 시 Windows 10 IoT Core 기본 앱이 표시 되며 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a6308-107">When you initially flash Windows 10 IoT Core, you will be presented with the Windows 10 IoT Core Default App upon startup, which looks like this:</span></span>

![IoT Core 기본 앱의 스크린샷](../media/IoTCoreDefaultApp/DeviceInfoPage-Screenshot.jpg)

<span data-ttu-id="a6308-109">이 응용 프로그램의 목적은 Windows 10 IoT Core를 처음 부팅할 때 상호 작용할 수 있는 친숙 한 셸을 제공 하기 위한 것이 아니라이 [응용 프로그램에](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/IoTCoreDefaultApp) 대 한 코드를 오픈 소스로 사용 하 여 사용자 고유의 cu에서 이러한 기능을 연결 하 고 재생할 수 있도록 하는 것입니다. stom 응용 프로그램입니다.</span><span class="sxs-lookup"><span data-stu-id="a6308-109">The purpose of this application is not only to provide you with a friendly shell to interact with when you first boot up Windows 10 IoT Core, but we have open-sourced the code for this application [here](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/IoTCoreDefaultApp) so that you can plug and play with these features on your own custom application(s).</span></span>

<span data-ttu-id="a6308-110">이 문서에서는 Windows 10 IoT Core 기본 앱에서 제공 하는 다양 한 기능에 대 한 개요를 제공 하 고 응용 프로그램에 대해 이러한 여러 기능을 활용할 수 있는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6308-110">This article will give you a rundown of the different features that the Windows 10 IoT Core Default App offers as well as how you can leverage these different features for your own applications.</span></span>

## <a name="leveraging-the-iot-core-default-app"></a><span data-ttu-id="a6308-111">IoT Core 기본 앱 활용</span><span class="sxs-lookup"><span data-stu-id="a6308-111">Leveraging the IoT Core Default App</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="a6308-112">상용화에 제조사 이미지를 사용하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="a6308-112">Do not use maker images for commercialization.</span></span> <span data-ttu-id="a6308-113">디바이스를 상용화하려는 경우 최적의 보안을 위해 사용자 지정 FFU를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6308-113">If you are commercializing a device, you must use a custom FFU for optimal security.</span></span> <span data-ttu-id="a6308-114">[여기](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)에서 자세한 내용을 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="a6308-114">Learn more [here](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).</span></span>

<span data-ttu-id="a6308-115">IoT Core 기본 앱을 사용자 지정 하 고 확장할 수 있습니다. 또는 소스 코드를 사용자 고유의 앱에 대 한 예제로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6308-115">The IoT Core Default App can be customized and extended, or you can use the source code as an example for your own app.</span></span> <span data-ttu-id="a6308-116">직접 사용해 보려면 샘플의 zip을 다운로드 하거나 [여기](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/IoTCoreDefaultApp)에서 IoT Core 기본 앱에 대 한 코드를 확인 하세요.</span><span class="sxs-lookup"><span data-stu-id="a6308-116">To try this out for yourself, download the zip of our samples or check out the code for the IoT Core Default App [here](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/IoTCoreDefaultApp).</span></span> <span data-ttu-id="a6308-117">질문을 하려면 [여기](https://github.com/Microsoft/Windows-iotcore-samples/issues)의 샘플 리포지토리에서 문제를 파일 하세요.</span><span class="sxs-lookup"><span data-stu-id="a6308-117">For any questions, please file an issue on our samples repo [here](https://github.com/Microsoft/Windows-iotcore-samples/issues).</span></span>

<span data-ttu-id="a6308-118">아래 설정 섹션](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoredefaultapp#settings
) 에 [표시 된 것 처럼 경우에 따라 최종 사용자를 대신 하 여 고객 시스템에서 기본 설정 및 기능을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6308-118">As shown under the [Settings section](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoredefaultapp#settings
) below, in some cases, you may configure default settings and features on your customer system on behalf of the end user.</span></span> <span data-ttu-id="a6308-119">그러나 기본적으로 이러한 설정 및 기능을 설정 하거나 진단이 기본 설정 위에 있는 경우 다음을 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6308-119">However, if you turn these settings and features on by default or if diagnostics are above the basic setting, you must:</span></span>

* <span data-ttu-id="a6308-120">최종 사용자에 게 이러한 기능을 사용할 수 있음을 알리고 [여기](http://go.microsoft.com/fwlink/?LinkId=521839)에서 Microsoft 개인 정보 취급 방침 웹 페이지에 대 한 링크를 최종 사용자에 게 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6308-120">Notify the end user that these features have been enable and provide the end user with the link to Microsoft's Privacy Statement web page [here](http://go.microsoft.com/fwlink/?LinkId=521839).</span></span> 
* <span data-ttu-id="a6308-121">관련 최종 사용자의 보안 동의를 통해 해당 법률에서 요구 하는 대로 기본적으로 이러한 기능을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6308-121">Secure consent from the relevant end user to enable such features by default (as required by applicable law).</span></span>
* <span data-ttu-id="a6308-122">최종 사용자에 게 진단 설정을 다시 기본 설정으로 변경할 수 있는 기능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6308-122">Provide end users the ability to change the Diagnostics setting back to the basic setting.</span></span>
* <span data-ttu-id="a6308-123">Microsoft 계정을 사용 하도록 설정 하 고 최종 사용자 데이터에 대 한 액세스 권한이 있는 경우 최종 사용자가 Microsoft 계정을 삭제 하는 경우 장치에서 모든 최종 사용자의 Microsoft 계정 데이터를 동시에 삭제할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6308-123">If you enable Microsoft Accounts and you have access to end user data, if the end user deletes the Microsoft Account, you must enable simultaneous deletion of all the end user's Microsoft Account data on the device.</span></span> 

## <a name="out-of-box-experience-oobe"></a><span data-ttu-id="a6308-124">OOBE (기본 제공 환경)</span><span class="sxs-lookup"><span data-stu-id="a6308-124">Out-of-Box Experience (OOBE)</span></span>

<span data-ttu-id="a6308-125">IoT Core 기본 앱에 대 한 기본 제공 환경은 가져오는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a6308-125">The out-of-box experience for the IoT Core Default App is as lean as it gets.</span></span> <span data-ttu-id="a6308-126">첫 번째 페이지에는 기본 언어 및 wi-fi 설정이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6308-126">The first pages will ask for a default language and wi-fi settings.</span></span> <span data-ttu-id="a6308-127">여기서 앱이 GDPR 규격을 준수 하도록 하려면 진단 데이터 화면이 있어야 하 고, 위치를 추적할 계획인 경우 위치 사용 권한 화면도 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6308-127">From there, in order for your app to be GDPR-compliant, you must have a diagnostic data screen and, if you're planning to track location, you will need to have a location permissions screen too.</span></span> <span data-ttu-id="a6308-128">둘 다의 예가 아래에 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6308-128">Examples of both are shown below.</span></span> 

<span data-ttu-id="a6308-129">![Oobe에 대 한](../media/IoTCoreDefaultApp/OOBE3.jpg)
oobe![진단 설정의 위치 설정](../media/IoTCoreDefaultApp/OOBE4.jpg)</span><span class="sxs-lookup"><span data-stu-id="a6308-129">![Location settings for OOBE](../media/IoTCoreDefaultApp/OOBE3.jpg)
![Diagnostic settings for OOBE](../media/IoTCoreDefaultApp/OOBE4.jpg)</span></span>

## <a name="command-bar"></a><span data-ttu-id="a6308-130">명령 모음</span><span class="sxs-lookup"><span data-stu-id="a6308-130">Command Bar</span></span>
<span data-ttu-id="a6308-131">명령 모음은 화면 아래쪽에 있는 영구적인 horizonatal Bar입니다.</span><span class="sxs-lookup"><span data-stu-id="a6308-131">The Command Bar is the persistant horizonatal bar located at the bottom of the screen.</span></span> <span data-ttu-id="a6308-132">이렇게 하면 다음 기능이에 쉽게 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6308-132">This provides easy access to the following funtionality:</span></span>
- <span data-ttu-id="a6308-133">앞으로 및 뒤로 페이지 탐색</span><span class="sxs-lookup"><span data-stu-id="a6308-133">Forward and backward page navigation</span></span>
- <span data-ttu-id="a6308-134">현재 페이지를 떠나지 않고 기본 장치 정보</span><span class="sxs-lookup"><span data-stu-id="a6308-134">Basic device info without leaving the current page</span></span>
- <span data-ttu-id="a6308-135">전체 화면 모드 설정 또는 해제</span><span class="sxs-lookup"><span data-stu-id="a6308-135">Turning fullscreen mode on or off</span></span>
- <span data-ttu-id="a6308-136">바로 가기 키</span><span class="sxs-lookup"><span data-stu-id="a6308-136">Advance shortcuts</span></span>
- <span data-ttu-id="a6308-137">페이지 특정 단추</span><span class="sxs-lookup"><span data-stu-id="a6308-137">Page specific buttons</span></span>

<span data-ttu-id="a6308-138">명령 모음에는 많은 단추가 있으며 때로는 이러한 단추를 혼동 하거나 숨길 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6308-138">There are a lot buttons in the Command Bar, and sometimes those buttons can be confusing or hidden.</span></span> <span data-ttu-id="a6308-139">명령 모음을 확장 하 고 해당 단추에 액세스 하려면 오른쪽 아래에 있는 메뉴 단추를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="a6308-139">To expand the Command Bar and access those buttons, please press the menu button in the bottom right:</span></span>

![명령 모음을 확장 하는 방법](../media/IoTCoreDefaultApp/CommandBar.gif)

## <a name="start-menu---play"></a><span data-ttu-id="a6308-141">시작 메뉴-재생</span><span class="sxs-lookup"><span data-stu-id="a6308-141">Start Menu - Play</span></span>

<span data-ttu-id="a6308-142">시작 메뉴에는 대부분의 플러그 앤 플레이 기능이 라이브 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6308-142">The Start Menu is where most plug and play features live.</span></span>

### <a name="weather"></a><span data-ttu-id="a6308-143">날씨</span><span class="sxs-lookup"><span data-stu-id="a6308-143">Weather</span></span>
<span data-ttu-id="a6308-144">날씨 페이지는 국가별 날씨 서비스의 데이터를 사용 하 여 현재 위치에 날씨 정보를 렌더링 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6308-144">Using data from the National Weather Service, the weather page renders weather information in your current location.</span></span>

### <a name="web-browser"></a><span data-ttu-id="a6308-145">웹 브라우저</span><span class="sxs-lookup"><span data-stu-id="a6308-145">Web Browser</span></span>
<span data-ttu-id="a6308-146">웹 브라우저를 사용 하 여 웹에서 대부분의 사이트를 끌어올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6308-146">The web browser allows you to pull up most sites from the web.</span></span>

### <a name="music"></a><span data-ttu-id="a6308-147">음악</span><span class="sxs-lookup"><span data-stu-id="a6308-147">Music</span></span>
<span data-ttu-id="a6308-148">이 페이지는 [Windows 장치 포털](../manage-your-device/DevicePortal.md)을 통해 액세스할 수 있는 **음악 라이브러리**에서 MP3 및 WAV 파일을 재생 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6308-148">This page will play MP3 and WAV files from the **Music Library**, that can be accessed via the [Windows Device Portal](../manage-your-device/DevicePortal.md).</span></span>  <span data-ttu-id="a6308-149">음악 플레이어에 파일을 업로드 하려면 Windows 장치 포털로 이동 하 여 "앱" 드롭다운을 클릭 하 고 "파일 탐색기"로 이동한 다음 "음악"을 선택 하 고 여기에서 파일을 업로드 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6308-149">To upload files to the music player, you will need to navigate to the Windows Device Portal, click on the "Apps" dropdown, navigate to "File Explorer", select "Music" and upload your files from there.</span></span>


![음악 파일을 업로드 하는 방법](../media/IoTCoreDefaultApp/music.gif)

### <a name="slideshow"></a><span data-ttu-id="a6308-151">Slideshow</span><span class="sxs-lookup"><span data-stu-id="a6308-151">Slideshow</span></span>
<span data-ttu-id="a6308-152">이 페이지에는 [Windows 장치 포털](../manage-your-device/DevicePortal.md)을 통해 액세스할 수 있는 **그림 라이브러리**의 모든 PNG 또는 JPEG 이미지 파일이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6308-152">This page will display any PNG or JPEG image files from the **Pictures Library**, that can be accessed via the [Windows Device Portal](../manage-your-device/DevicePortal.md).</span></span> <span data-ttu-id="a6308-153">이미지를 슬라이드 쇼에 업로드 하려면 Windows 장치 포털로 이동 하 여 "앱" 드롭다운을 클릭 하 고 "파일 탐색기"로 이동한 다음 "그림"을 선택 하 고 여기에서 파일을 업로드 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6308-153">To upload images to the slideshow, you will need to navigate to the Windows Device Portal, click on the "Apps" dropdown, navigate to "File Explorer", select "Pictures" and upload your files from there.</span></span>


![음악 파일을 업로드 하는 방법](../media/IoTCoreDefaultApp/slideshow.gif)

### <a name="draw"></a><span data-ttu-id="a6308-155">Draw</span><span class="sxs-lookup"><span data-stu-id="a6308-155">Draw</span></span>
<span data-ttu-id="a6308-156">이 페이지에서는 Windows 10 IoT Core의 잉크 기능을 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6308-156">This page allows you to test out Windows 10 IoT Core's inking capabilities.</span></span>

## <a name="start-menu---explore"></a><span data-ttu-id="a6308-157">시작 메뉴-탐색</span><span class="sxs-lookup"><span data-stu-id="a6308-157">Start Menu - Explore</span></span> 

### <a name="apps"></a><span data-ttu-id="a6308-158">앱</span><span class="sxs-lookup"><span data-stu-id="a6308-158">Apps</span></span> 
<span data-ttu-id="a6308-159">이 페이지에서 장치에 설치 된 다른 포그라운드 응용 프로그램을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6308-159">This page allows you to launch other foreground applications installed on the device.</span></span> <span data-ttu-id="a6308-160">응용 프로그램을 시작 하면 [Windows 장치 포털](../manage-your-device/DevicePortal.md)에서 app Manager를 사용 하 여 고 수 있는 IoT Core 기본 앱이 일시 중단 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6308-160">Launching an application will suspend IoT Core Default App, which can be relaunched by using App Manager in [Windows Device Portal](../manage-your-device/DevicePortal.md).</span></span>

<span data-ttu-id="a6308-161">전경 응용 프로그램을 페이지에 나열 하는 데 특별 한 사항은 없으며, 응용 프로그램을 [설치](AppInstaller.md) 하거나 [배포](AppDeployment.md) 하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6308-161">Nothing special is needed to have your foreground application listed in the page, simply [install](AppInstaller.md) or [deploy](AppDeployment.md) the application.</span></span> <span data-ttu-id="a6308-162">설치 또는 배포를 성공적으로 수행한 후 응용 프로그램 페이지를 다시 탐색 하 여 응용 프로그램 목록을 새로 고칩니다.</span><span class="sxs-lookup"><span data-stu-id="a6308-162">After successful installation or deployment, re-navigate to the Apps page to refresh the list of applications.</span></span>

<span data-ttu-id="a6308-163">필터링 하는 자동 생성 된 OS 관련 응용 프로그램이 몇 가지 있습니다. [여기](http://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/IoTCoreDefaultApp/CS/Views/AppLauncherPage.xaml.cs)에서 앱 이름 목록을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6308-163">Note that there are a couple of auto-generated OS related applications that we filter out, you can find the list of app names [here](http://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/IoTCoreDefaultApp/CS/Views/AppLauncherPage.xaml.cs).</span></span>

### <a name="notifications"></a><span data-ttu-id="a6308-164">알림</span><span class="sxs-lookup"><span data-stu-id="a6308-164">Notifications</span></span>
<span data-ttu-id="a6308-165">이 페이지에는 IoT Core 기본 앱이 시작 된 이후 지난 20 개의 알림이 나열 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6308-165">This page will list the past 20 notifications since IoT Core Default App was launched.</span></span> <span data-ttu-id="a6308-166">IoT Core 기본 앱이 디버그 모드에서 실행 되는 경우 테스트 알림을 만드는 단추가 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6308-166">When IoT Core Default App is running in debug mode, buttons are added that will create test notifications.</span></span>

### <a name="logs"></a><span data-ttu-id="a6308-167">로그</span><span class="sxs-lookup"><span data-stu-id="a6308-167">Logs</span></span>
<span data-ttu-id="a6308-168">이 페이지에는 자동 생성 된 충돌 또는 오류 로그가 표시 됩니다 .이 로그는 장치에서 가져와서 분석할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6308-168">This page will list any auto-generated crash or error logs, which then can be taken off the device and analyzed.</span></span>

### <a name="github"></a><span data-ttu-id="a6308-169">GitHub</span><span class="sxs-lookup"><span data-stu-id="a6308-169">GitHub</span></span>
<span data-ttu-id="a6308-170">이 페이지에서는 IoT Core 기본 앱 코드의 오픈 소스 GitHub 위치로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6308-170">This page will take you to the open-sourced GitHub location of the IoT Core Default App code.</span></span>

## <a name="start-menu---windows-device-portal"></a><span data-ttu-id="a6308-171">시작 메뉴-Windows 장치 포털</span><span class="sxs-lookup"><span data-stu-id="a6308-171">Start Menu - Windows Device Portal</span></span>

<span data-ttu-id="a6308-172">이 섹션의 페이지에서는 windows 장치 포털 자격 증명을 사용 하 여 로그인 해야 하는 Windows 장치 포털 REST Api를 활용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6308-172">The pages in this section leverage the Windows Device Portal REST APIs, which requires you to sign in using your Windows Device Portal credentials.</span></span>

## <a name="device-information"></a><span data-ttu-id="a6308-173">장치 정보</span><span class="sxs-lookup"><span data-stu-id="a6308-173">Device Information</span></span>

<span data-ttu-id="a6308-174">이 페이지에서는 이더넷, OS 버전, 연결 된 장치 등 장치에 대 한 다양 한 기능을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6308-174">This page allows you to see the different features for your device including Ethernet, OS version, connected devices, and more.</span></span>

## <a name="command-line"></a><span data-ttu-id="a6308-175">명령줄</span><span class="sxs-lookup"><span data-stu-id="a6308-175">Command Line</span></span>

<span data-ttu-id="a6308-176">이 페이지에서는 장치에서 직접 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6308-176">This page allows you to run commands directly on your device.</span></span>

<span data-ttu-id="a6308-177">이 기능을 사용 하려면 앱에서 명령을 실행할 수 있도록 레지스트리 키를 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6308-177">To enable this feature you have to set a registry key so that the app can run the commands.</span></span> <span data-ttu-id="a6308-178">처음으로 명령을 실행 하려고 하면 Windows 장치 포털에 대 한 호출을 사용 하 여 레지스트리 키를 설정할 수 있는 링크가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6308-178">The first time you try to run a command you will see a link that allows you to set the registry key using a call to Windows Device Portal.</span></span> <span data-ttu-id="a6308-179">장치에서 명령을 실행할 수 있도록 하려면 링크를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6308-179">Click the link to enable your device to run commands.</span></span>

<span data-ttu-id="a6308-180">일부 명령에는 관리자 액세스 권한이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6308-180">Some commands require administrator access.</span></span> <span data-ttu-id="a6308-181">보안을 위해 앱은 기본적으로 관리자가 아닌 계정을 사용 하 여 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6308-181">For security purposes the app uses a non-admin account by default to run commands.</span></span> <span data-ttu-id="a6308-182">관리자 권한으로 명령을 실행 해야 하는 경우 명령줄 프롬프트에서 "RunAsAdmin <your command>"를 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6308-182">If you need to run a command as an admin you can type "RunAsAdmin <your command>" in the command line prompt.</span></span>

## <a name="settings"></a><span data-ttu-id="a6308-183">설정</span><span class="sxs-lookup"><span data-stu-id="a6308-183">Settings</span></span>
<span data-ttu-id="a6308-184">Wi-fi, Bluetooth, 전원 옵션 등을 비롯 한 다양 한 설정을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6308-184">You'll be able to configure a number of settings here including Wi-Fi, Bluetooth, power options, and more.</span></span>

### <a name="app-settings"></a><span data-ttu-id="a6308-185">앱 설정</span><span class="sxs-lookup"><span data-stu-id="a6308-185">App Settings</span></span>
<span data-ttu-id="a6308-186">**앱 설정** 섹션에서 앱의 페이지에 대 한 다양 한 설정을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6308-186">The **App Settings** section allows you to configure various settings for pages in the app.</span></span>  

<span data-ttu-id="a6308-187">사용자 지정할 수 있는 몇 가지 설정은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a6308-187">Some of the settings you can customize are:</span></span>

##### <a name="general-settings"></a><span data-ttu-id="a6308-188">일반 설정</span><span class="sxs-lookup"><span data-stu-id="a6308-188">General Settings</span></span>
* <span data-ttu-id="a6308-189">앱이 시작 될 때 표시 되는 기본 페이지를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6308-189">Set the default page that appears when the app is started</span></span>
* <span data-ttu-id="a6308-190">화면 보호기 사용/사용 안 함</span><span class="sxs-lookup"><span data-stu-id="a6308-190">Enable/disable the screensaver</span></span>

##### <a name="weather-settings"></a><span data-ttu-id="a6308-191">날씨 설정</span><span class="sxs-lookup"><span data-stu-id="a6308-191">Weather Settings</span></span>
* <span data-ttu-id="a6308-192">위치 변경</span><span class="sxs-lookup"><span data-stu-id="a6308-192">Change the location</span></span>
  > <span data-ttu-id="a6308-193">이 기능은 유효한 [Bing 지도 서비스 토큰](https://msdn.microsoft.com/library/ff428642.aspx)을 제공한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6308-193">This feature is only enabled if you have provided a valid [Bing Map Service Token](https://msdn.microsoft.com/library/ff428642.aspx).</span></span>  <span data-ttu-id="a6308-194">앱에 토큰을 전달 하려면 앱의 localstate 폴더 (예: C:\Data\USERS\\[User Account] \AppData\Packages\\[Package Full Name] \localst\maptoken.config)에 **maptoken .config** 파일을 만들고 앱을 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6308-194">To pass the token to the app, create a **MapToken.config** file in the LocalState folder of the app (e.g. C:\Data\USERS\\[User Account]\AppData\Packages\\[Package Full Name]\LocalState\MapToken.config) and restart the app.</span></span>
* <span data-ttu-id="a6308-195">지도 확장</span><span class="sxs-lookup"><span data-stu-id="a6308-195">Expand the map</span></span>
* <span data-ttu-id="a6308-196">지도와 날씨 스위치를 주기적으로 배치 하 여 화면 굽기를 방지 하는 맵 대칭 이동 사용/사용 안 함</span><span class="sxs-lookup"><span data-stu-id="a6308-196">Enable/disable map flipping so that the map and the weather switch places periodically to prevent screen burn-in</span></span>

##### <a name="web-browser-settings"></a><span data-ttu-id="a6308-197">웹 브라우저 설정</span><span class="sxs-lookup"><span data-stu-id="a6308-197">Web Browser Settings</span></span>
* <span data-ttu-id="a6308-198">웹 브라우저의 홈 페이지를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6308-198">Set the home page for the Web Browser</span></span>

##### <a name="slideshow-settings"></a><span data-ttu-id="a6308-199">슬라이드 쇼 설정</span><span class="sxs-lookup"><span data-stu-id="a6308-199">Slideshow Settings</span></span>
* <span data-ttu-id="a6308-200">슬라이드쇼 간격 설정</span><span class="sxs-lookup"><span data-stu-id="a6308-200">Set the slideshow interval</span></span>

##### <a name="appearance"></a><span data-ttu-id="a6308-201">모양</span><span class="sxs-lookup"><span data-stu-id="a6308-201">Appearance</span></span>
* <span data-ttu-id="a6308-202">타일 아이콘에 대해 Emojis 대신 MDL2 자산을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6308-202">Use MDL2 Assets instead of Emojis for the tile icons</span></span>
* <span data-ttu-id="a6308-203">타일 너비와 높이를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6308-203">Set the tile width and height</span></span>
* <span data-ttu-id="a6308-204">UI 배율 설정-자동 크기 조정은 기본적으로 설정 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6308-204">Set UI scaling - Automatic scaling is set by default</span></span>
* <span data-ttu-id="a6308-205">타일 색 설정</span><span class="sxs-lookup"><span data-stu-id="a6308-205">Set the tile color</span></span>

#### <a name="system"></a><span data-ttu-id="a6308-206">시스템</span><span class="sxs-lookup"><span data-stu-id="a6308-206">System</span></span>
<span data-ttu-id="a6308-207">언어, 키보드 레이아웃 및 표준 시간대를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6308-207">Change the language, keyboard layout, and time zone.</span></span>

#### <a name="network--wi-fi"></a><span data-ttu-id="a6308-208">네트워크 & Wi-fi</span><span class="sxs-lookup"><span data-stu-id="a6308-208">Network & Wi-Fi</span></span>
<span data-ttu-id="a6308-209">네트워크 어댑터 속성을 보거나 사용 가능한 Wi-fi 네트워크에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6308-209">View network adapter properties or connect to an available Wi-Fi network.</span></span>

#### <a name="bluetooth"></a><span data-ttu-id="a6308-210">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="a6308-210">Bluetooth</span></span>
<span data-ttu-id="a6308-211">Bluetooth 장치와 페어링 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6308-211">Pair with a Bluetooth device.</span></span>

#### <a name="app-updates"></a><span data-ttu-id="a6308-212">앱 업데이트</span><span class="sxs-lookup"><span data-stu-id="a6308-212">App Updates</span></span>
<span data-ttu-id="a6308-213">앱 업데이트를 확인 하거나 자동 업데이트 설정을 변경 하세요.</span><span class="sxs-lookup"><span data-stu-id="a6308-213">Check for app updates or change automatic update settings.</span></span>

#### <a name="power-options"></a><span data-ttu-id="a6308-214">전원 옵션</span><span class="sxs-lookup"><span data-stu-id="a6308-214">Power Options</span></span>
<span data-ttu-id="a6308-215">장치를 다시 시작 하거나 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6308-215">Restart or shutdown the device.</span></span>

#### <a name="diagnostics"></a><span data-ttu-id="a6308-216">진단</span><span class="sxs-lookup"><span data-stu-id="a6308-216">Diagnostics</span></span>
<span data-ttu-id="a6308-217">Microsoft에서 제공 하려는 진단 데이터의 양을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6308-217">Select the amount of diagnostic data you wish to provide Microsoft.</span></span>  <span data-ttu-id="a6308-218">사용자가 문제를 신속 하 게 진단 하 고 제품을 개선할 수 있도록 **전체** 진단 데이터를 옵트인 (opt in) 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="a6308-218">We encourage users to opt into **Full** diagnostic data so we can diagnose issues quickly and make improvements to the product.</span></span>

##### <a name="basic"></a><span data-ttu-id="a6308-219">기본</span><span class="sxs-lookup"><span data-stu-id="a6308-219">Basic</span></span> 
<span data-ttu-id="a6308-220">장치에 대 한 정보, 해당 설정 및 기능, 제대로 작동 하 고 있는지 여부에 대 한 정보만 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="a6308-220">Send only info about your device, its settings and capabilities, and whether it is performing properly.</span></span>

##### <a name="full"></a><span data-ttu-id="a6308-221">전체</span><span class="sxs-lookup"><span data-stu-id="a6308-221">Full</span></span>
<span data-ttu-id="a6308-222">검색 한 웹 사이트에 대 한 정보, 앱 및 기능을 사용 하는 방법, 장치 상태, 장치 작업 및 고급 오류 보고에 대 한 추가 정보를 비롯 하 여 모든 기본 진단 데이터를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="a6308-222">Send all Basic diagnostic data, along with info about websites you browse and how you use apps and features, plus additional info about device health, device activity, and enhanced error reporting.</span></span>

#### <a name="location"></a><span data-ttu-id="a6308-223">위치</span><span class="sxs-lookup"><span data-stu-id="a6308-223">Location</span></span>
<span data-ttu-id="a6308-224">사용자의 위치에 대 한 앱 액세스를 허용 하거나 거부 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6308-224">Allow or deny the app access to your location.</span></span>
