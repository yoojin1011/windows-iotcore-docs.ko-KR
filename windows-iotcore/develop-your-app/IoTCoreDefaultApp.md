---
title: Windows 10 IoT Core 기본 앱
author: saraclay
ms.author: saclayt
ms.date: 08/08/2018
ms.topic: article
description: Windows 10 IoT Core 기본 앱 및 해당 기능에 알아봅니다.
keywords: windows iot, windows 10 iot core, 기본 앱
ms.custom: RS5
ms.openlocfilehash: 12baa759c9085360431c2b7f87f72816cd24680b
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512406"
---
# <a name="windows-10-iot-core-default-app-overview"></a><span data-ttu-id="7e598-104">Windows 10 IoT Core 기본 앱 개요</span><span class="sxs-lookup"><span data-stu-id="7e598-104">Windows 10 IoT Core Default App Overview</span></span>

> [!TIP]
> <span data-ttu-id="7e598-105">이 샘플 앱에 추가 된 기능을 참조 하려는 경우 [문제를 제기](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoredefaultapp) 알려주세요 GitHub에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e598-105">If you find that you'd like to see a feature added to this sample app, [open an issue](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoredefaultapp) on GitHub to let us know.</span></span> <span data-ttu-id="7e598-106">버그를 제출 하려면 원하는 피드백 허브에 대 한 지침을 따릅니다 [여기](https://social.msdn.microsoft.com/Forums/en-US/fad1c6a0-e578-44a7-8e8d-95cc28c06ccd/need-logs-if-your-device-hasnt-updated-to-the-latest-iotcore-version?forum=WindowsIoT)합니다.</span><span class="sxs-lookup"><span data-stu-id="7e598-106">If you'd like to file a bug, follow the instructions for the Feedback Hub [here](https://social.msdn.microsoft.com/Forums/en-US/fad1c6a0-e578-44a7-8e8d-95cc28c06ccd/need-logs-if-your-device-hasnt-updated-to-the-latest-iotcore-version?forum=WindowsIoT).</span></span>

<span data-ttu-id="7e598-107">처음에 Windows 10 IoT Core flash를 Windows 10 IoT Core 기본 앱과 같은 시작 시 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7e598-107">When you initially flash Windows 10 IoT Core, you will be presented with the Windows 10 IoT Core Default App upon startup, which looks like this:</span></span>

![IoT Core 기본 앱의 스크린 샷](../media/IoTCoreDefaultApp/DeviceInfoPage-Screenshot.jpg)

<span data-ttu-id="7e598-109">이 응용 프로그램의 목적은 먼저 부팅 하면 Windows 10 IoT Core 설치 하는 상호 작용 하는 친숙 한 셸을 제공에 되지 않지만 우리는 오픈 소스이 응용 프로그램에 대 한 코드 [여기](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/IoTCoreDefaultApp) 있습니다 수 플러그 앤 플레이 이러한 있도록 사용자 고유의 사용자 지정 응용 프로그램에 대 한 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="7e598-109">The purpose of this application is not only to provide you with a friendly shell to interact with when you first boot up Windows 10 IoT Core, but we have open-sourced the code for this application [here](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/IoTCoreDefaultApp) so that you can plug and play with these features on your own custom application(s).</span></span>

<span data-ttu-id="7e598-110">이 문서에서는 이러한 다양 한 기능을 활용 하 여 사용자 고유의 응용 프로그램에 대 한 방법과 Windows 10 IoT Core 기본 앱 에서도 제공 하는 다양 한 기능에 대 한 개요를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e598-110">This article will give you a rundown of the different features that the Windows 10 IoT Core Default App offers as well as how you can leverage these different features for your own applications.</span></span>

## <a name="leveraging-the-iot-core-default-app"></a><span data-ttu-id="7e598-111">IoT Core 기본 앱을 활용 하 여</span><span class="sxs-lookup"><span data-stu-id="7e598-111">Leveraging the IoT Core Default App</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="7e598-112">상용화에 대 한 작성자 이미지를 사용 하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="7e598-112">Do not use maker images for commercialization.</span></span> <span data-ttu-id="7e598-113">장치 상용화 되, 사용자 지정 FFU 최적의 보안을 위해 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e598-113">If you are commercializing a device, you must use a custom FFU for optimal security.</span></span> <span data-ttu-id="7e598-114">[여기](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)에서 자세한 내용을 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="7e598-114">Learn more [here](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).</span></span>

<span data-ttu-id="7e598-115">IoT Core 기본 앱을 사용자 지정 확장 하거나 사용자 고유의 앱에 대 한 예를 들어 소스 코드를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e598-115">The IoT Core Default App can be customized and extended, or you can use the source code as an example for your own app.</span></span> <span data-ttu-id="7e598-116">이 직접을 사용해 샘플의 zip을 다운로드 하거나 IoT Core 기본 앱에 대 한 코드를 확인해 [여기](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/IoTCoreDefaultApp)합니다.</span><span class="sxs-lookup"><span data-stu-id="7e598-116">To try this out for yourself, download the zip of our samples or check out the code for the IoT Core Default App [here](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/IoTCoreDefaultApp).</span></span> <span data-ttu-id="7e598-117">모든 질문에 대 한 문제를 제출 하세요에서 샘플 리포지토리에서 [여기](https://github.com/Microsoft/Windows-iotcore-samples/issues)합니다.</span><span class="sxs-lookup"><span data-stu-id="7e598-117">For any questions, please file an issue on our samples repo [here](https://github.com/Microsoft/Windows-iotcore-samples/issues).</span></span>

<span data-ttu-id="7e598-118">아래 표시 된 것 처럼 합니다 [설정 섹션](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoredefaultapp#settings
) 아래의 경우에 따라 수를 구성할 수 있습니다 기본 설정 및 기능 고객 시스템 최종 사용자 대신 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e598-118">As shown under the [Settings section](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoredefaultapp#settings
) below, in some cases, you may configure default settings and features on your customer system on behalf of the end user.</span></span> <span data-ttu-id="7e598-119">그러나 이러한 설정과 기본적으로 또는 진단 위에 기본 설정 된 경우 기능을 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e598-119">However, if you turn these settings and features on by default or if diagnostics are above the basic setting, you must:</span></span>

* <span data-ttu-id="7e598-120">이 기능이 사용 하도록 설정 된 하 고 Microsoft의 개인정보취급방침 웹 페이지에 대 한 링크를 사용 하 여 최종 사용자를 제공 합니다. 최종 사용자에 게 알립니다 [여기](http://go.microsoft.com/fwlink/?LinkId=521839)합니다.</span><span class="sxs-lookup"><span data-stu-id="7e598-120">Notify the end user that these features have been enable and provide the end user with the link to Microsoft's Privacy Statement web page [here](http://go.microsoft.com/fwlink/?LinkId=521839).</span></span> 
* <span data-ttu-id="7e598-121">필요에 따라 해당 법규에서 기본적으로 이러한 기능을 사용 하도록 설정 하려면 관련 최종 사용자의 동의 보호 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e598-121">Secure consent from the relevant end user to enable such features by default (as required by applicable law).</span></span>
* <span data-ttu-id="7e598-122">최종 사용자에 게 진단 설정을 기본 설정으로 다시 변경 하는 기능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e598-122">Provide end users the ability to change the Diagnostics setting back to the basic setting.</span></span>
* <span data-ttu-id="7e598-123">Microsoft 계정을 사용 하 고 최종 사용자는 Microsoft 계정을 삭제 하는 경우 최종 사용자 데이터에 액세스할 수, 동시 삭제할 장치에서 모든 최종 사용자의 Microsoft 계정 데이터를 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e598-123">If you enable Microsoft Accounts and you have access to end user data, if the end user deletes the Microsoft Account, you must enable simultaneous deletion of all the end user's Microsoft Account data on the device.</span></span> 

## <a name="out-of-box-experience-oobe"></a><span data-ttu-id="7e598-124">기본 제공 환경 (OOBE)</span><span class="sxs-lookup"><span data-stu-id="7e598-124">Out-of-Box Experience (OOBE)</span></span>

<span data-ttu-id="7e598-125">IoT Core 기본 앱에 대 한 기본 제공 환경은 져 간결 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e598-125">The out-of-box experience for the IoT Core Default App is as lean as it gets.</span></span> <span data-ttu-id="7e598-126">기본 언어 및 wi-fi 설정에 대 한 첫 번째 페이지를 묻습니다.</span><span class="sxs-lookup"><span data-stu-id="7e598-126">The first pages will ask for a default language and wi-fi settings.</span></span> <span data-ttu-id="7e598-127">GDPR 규격 앱에 대 한 순서 대로 여기에서 진단 데이터 화면 있어야 하 고 위치를 추적 하려는 경우 너무 위치 권한을 화면이 포함 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e598-127">From there, in order for your app to be GDPR-compliant, you must have a diagnostic data screen and, if you're planning to track location, you will need to have a location permissions screen too.</span></span> <span data-ttu-id="7e598-128">둘 다의 예제가 아래에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7e598-128">Examples of both are shown below.</span></span> 

![<span data-ttu-id="7e598-129">OOBE에 대 한 위치 설정을](../media/IoTCoreDefaultApp/OOBE3.jpg)
![OOBE에 대 한 진단 설정</span><span class="sxs-lookup"><span data-stu-id="7e598-129">Location settings for OOBE](../media/IoTCoreDefaultApp/OOBE3.jpg)
![Diagnostic settings for OOBE</span></span>](../media/IoTCoreDefaultApp/OOBE4.jpg)

## <a name="command-bar"></a><span data-ttu-id="7e598-130">명령 모음</span><span class="sxs-lookup"><span data-stu-id="7e598-130">Command Bar</span></span>
<span data-ttu-id="7e598-131">명령 모음 화면 아래쪽에 있는 영구 horizonatal 모음 이며</span><span class="sxs-lookup"><span data-stu-id="7e598-131">The Command Bar is the persistant horizonatal bar located at the bottom of the screen.</span></span> <span data-ttu-id="7e598-132">이 다음 기능에 쉽게 액세스할 수 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="7e598-132">This provides easy access to the following funtionality:</span></span>
- <span data-ttu-id="7e598-133">페이지를 앞뒤로 탐색</span><span class="sxs-lookup"><span data-stu-id="7e598-133">Forward and backward page navigation</span></span>
- <span data-ttu-id="7e598-134">현재 페이지를 떠나지 않고 기본 장치 정보</span><span class="sxs-lookup"><span data-stu-id="7e598-134">Basic device info without leaving the current page</span></span>
- <span data-ttu-id="7e598-135">전체 화면 모드를 설정 또는 해제</span><span class="sxs-lookup"><span data-stu-id="7e598-135">Turning fullscreen mode on or off</span></span>
- <span data-ttu-id="7e598-136">고급 바로 가기</span><span class="sxs-lookup"><span data-stu-id="7e598-136">Advance shortcuts</span></span>
- <span data-ttu-id="7e598-137">특정 페이지 단추</span><span class="sxs-lookup"><span data-stu-id="7e598-137">Page specific buttons</span></span>

<span data-ttu-id="7e598-138">명령 모음에 많은 단추 및 혼동 되거나 숨겨진 해당 단추 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e598-138">There are a lot buttons in the Command Bar, and sometimes those buttons can be confusing or hidden.</span></span> <span data-ttu-id="7e598-139">명령 모음을 확장 하 고 해당 단추에 액세스할 오른쪽 아래에서에서 메뉴 단추를 누르십시오.</span><span class="sxs-lookup"><span data-stu-id="7e598-139">To expand the Command Bar and access those buttons, please press the menu button in the bottom right:</span></span>

![명령 모음을 확장 하는 방법](../media/IoTCoreDefaultApp/CommandBar.gif)

## <a name="start-menu---play"></a><span data-ttu-id="7e598-141">시작 메뉴-재생</span><span class="sxs-lookup"><span data-stu-id="7e598-141">Start Menu - Play</span></span>

<span data-ttu-id="7e598-142">시작 메뉴는 대부분의 플러그 앤 플레이 기능은 어디에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e598-142">The Start Menu is where most plug and play features live.</span></span>

### <a name="weather"></a><span data-ttu-id="7e598-143">날씨</span><span class="sxs-lookup"><span data-stu-id="7e598-143">Weather</span></span>
<span data-ttu-id="7e598-144">날씨 페이지 National 날씨 서비스에서 데이터를 사용 하 여 현재 위치에 날씨 정보를 렌더링 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e598-144">Using data from the National Weather Service, the weather page renders weather information in your current location.</span></span>

### <a name="web-browser"></a><span data-ttu-id="7e598-145">웹 브라우저</span><span class="sxs-lookup"><span data-stu-id="7e598-145">Web Browser</span></span>
<span data-ttu-id="7e598-146">웹 브라우저를 사용 하면 웹에서 대부분의 사이트를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e598-146">The web browser allows you to pull up most sites from the web.</span></span>

### <a name="music"></a><span data-ttu-id="7e598-147">음악</span><span class="sxs-lookup"><span data-stu-id="7e598-147">Music</span></span>
<span data-ttu-id="7e598-148">이 페이지에서 MP3 및 WAV 파일 재생 됩니다 합니다 **음악 라이브러리**를 통해 액세스할 수 있는 합니다 [Windows Device Portal](../manage-your-device/DevicePortal.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="7e598-148">This page will play MP3 and WAV files from the **Music Library**, that can be accessed via the [Windows Device Portal](../manage-your-device/DevicePortal.md).</span></span>  <span data-ttu-id="7e598-149">음악 플레이어에 게 파일을 업로드 하려면 Windows Device Portal 이동, "앱" 드롭다운 목록에서 클릭, "File Explorer"로 이동, "Music" 선택 및 여기에서 파일을 업로드 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e598-149">To upload files to the music player, you will need to navigate to the Windows Device Portal, click on the "Apps" dropdown, navigate to "File Explorer", select "Music" and upload your files from there.</span></span>


![음악 파일을 업로드 하는 방법](../media/IoTCoreDefaultApp/music.gif)

### <a name="slideshow"></a><span data-ttu-id="7e598-151">Slideshow</span><span class="sxs-lookup"><span data-stu-id="7e598-151">Slideshow</span></span>
<span data-ttu-id="7e598-152">이 페이지에서 JPEG 또는 PNG 이미지 파일에 표시 됩니다는 **사진 라이브러리**를 통해 액세스할 수 있는 합니다 [Windows Device Portal](../manage-your-device/DevicePortal.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="7e598-152">This page will display any PNG or JPEG image files from the **Pictures Library**, that can be accessed via the [Windows Device Portal](../manage-your-device/DevicePortal.md).</span></span> <span data-ttu-id="7e598-153">슬라이드 쇼를 이미지를 업로드 하려면 Windows Device Portal 이동, "앱" 드롭다운 목록에서 클릭, "File Explorer"로 이동, "그림"을 선택 및 여기에서 파일을 업로드 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e598-153">To upload images to the slideshow, you will need to navigate to the Windows Device Portal, click on the "Apps" dropdown, navigate to "File Explorer", select "Pictures" and upload your files from there.</span></span>


![음악 파일을 업로드 하는 방법](../media/IoTCoreDefaultApp/slideshow.gif)

### <a name="draw"></a><span data-ttu-id="7e598-155">Draw</span><span class="sxs-lookup"><span data-stu-id="7e598-155">Draw</span></span>
<span data-ttu-id="7e598-156">이 페이지를 사용 하면 Windows 10 IoT Core 잉크 입력 기능을 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e598-156">This page allows you to test out Windows 10 IoT Core's inking capabilities.</span></span>

## <a name="start-menu---explore"></a><span data-ttu-id="7e598-157">시작 메뉴-탐색</span><span class="sxs-lookup"><span data-stu-id="7e598-157">Start Menu - Explore</span></span> 

### <a name="apps"></a><span data-ttu-id="7e598-158">앱</span><span class="sxs-lookup"><span data-stu-id="7e598-158">Apps</span></span> 
<span data-ttu-id="7e598-159">이 페이지를 사용 하는 장치에 설치 된 다른 포그라운드 응용 프로그램을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e598-159">This page allows you to launch other foreground applications installed on the device.</span></span> <span data-ttu-id="7e598-160">응용 프로그램 시작에서 IoT Core 기본 앱에서 응용 프로그램 관리자를 사용 하 여 다시 시작할 수 있습니다는 일시 중단 [Windows Device Portal](../manage-your-device/DevicePortal.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="7e598-160">Launching an application will suspend IoT Core Default App, which can be relaunched by using App Manager in [Windows Device Portal](../manage-your-device/DevicePortal.md).</span></span>

<span data-ttu-id="7e598-161">포그라운드 응용 프로그램을 간단히 페이지에서 나열 하는 데 필요한 특별 [설치](AppInstaller.md) 하거나 [배포](AppDeployment.md) 응용 프로그램입니다.</span><span class="sxs-lookup"><span data-stu-id="7e598-161">Nothing special is needed to have your foreground application listed in the page, simply [install](AppInstaller.md) or [deploy](AppDeployment.md) the application.</span></span> <span data-ttu-id="7e598-162">설치 성공 또는 배포 후 응용 프로그램의 목록을 새로 고치려면 앱 페이지로 이동 다시 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e598-162">After successful installation or deployment, re-navigate to the Apps page to refresh the list of applications.</span></span>

<span data-ttu-id="7e598-163">자동으로 생성 된 운영 체제의 몇 가지를 필터링 하는 응용 프로그램 관련, 앱 이름 목록을 찾을 수 있습니다 [여기](http://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/IoTCoreDefaultApp/CS/Views/AppLauncherPage.xaml.cs)합니다.</span><span class="sxs-lookup"><span data-stu-id="7e598-163">Note that there are a couple of auto-generated OS related applications that we filter out, you can find the list of app names [here](http://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/IoTCoreDefaultApp/CS/Views/AppLauncherPage.xaml.cs).</span></span>

### <a name="notifications"></a><span data-ttu-id="7e598-164">알림</span><span class="sxs-lookup"><span data-stu-id="7e598-164">Notifications</span></span>
<span data-ttu-id="7e598-165">이 페이지에는 과거 표시 IoT Core 기본 앱이 시작 된 이후 20 알림.</span><span class="sxs-lookup"><span data-stu-id="7e598-165">This page will list the past 20 notifications since IoT Core Default App was launched.</span></span> <span data-ttu-id="7e598-166">IoT Core 기본 앱은 디버그 모드에서 실행 하면 테스트 알림을 사용 하는 단추 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7e598-166">When IoT Core Default App is running in debug mode, buttons are added that will create test notifications.</span></span>

### <a name="logs"></a><span data-ttu-id="7e598-167">로그</span><span class="sxs-lookup"><span data-stu-id="7e598-167">Logs</span></span>
<span data-ttu-id="7e598-168">이 페이지에는 모든 자동으로 생성 된 충돌 또는 오류 로그에 있으며, 그런 다음 장치를 해제 하 고 수 분석 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7e598-168">This page will list any auto-generated crash or error logs, which then can be taken off the device and analyzed.</span></span>

### <a name="github"></a><span data-ttu-id="7e598-169">GitHub</span><span class="sxs-lookup"><span data-stu-id="7e598-169">GitHub</span></span>
<span data-ttu-id="7e598-170">이 페이지는 IoT Core 기본 응용 프로그램 코드의 오픈 소스 GitHub 위치를 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e598-170">This page will take you to the open-sourced GitHub location of the IoT Core Default App code.</span></span>

## <a name="start-menu---windows-device-portal"></a><span data-ttu-id="7e598-171">시작 메뉴-Windows Device Portal</span><span class="sxs-lookup"><span data-stu-id="7e598-171">Start Menu - Windows Device Portal</span></span>

<span data-ttu-id="7e598-172">Windows Device Portal 자격 증명을 사용 하 여 로그인 해야 하는 Windows Device Portal REST Api를 활용 하는이 섹션의 페이지입니다.</span><span class="sxs-lookup"><span data-stu-id="7e598-172">The pages in this section leverage the Windows Device Portal REST APIs, which requires you to sign in using your Windows Device Portal credentials.</span></span>

## <a name="device-information"></a><span data-ttu-id="7e598-173">장치 정보</span><span class="sxs-lookup"><span data-stu-id="7e598-173">Device Information</span></span>

<span data-ttu-id="7e598-174">이 페이지를 사용 하면 이더넷, OS 버전, 연결 된 장치 등을 포함 한 장치에 대 한 다양 한 기능을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e598-174">This page allows you to see the different features for your device including Ethernet, OS version, connected devices, and more.</span></span>

## <a name="command-line"></a><span data-ttu-id="7e598-175">명령줄</span><span class="sxs-lookup"><span data-stu-id="7e598-175">Command Line</span></span>

<span data-ttu-id="7e598-176">이 페이지를 사용 하면 장치에서 직접 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e598-176">This page allows you to run commands directly on your device.</span></span>

<span data-ttu-id="7e598-177">이 기능을 사용 하도록 설정 하려면 레지스트리 키를 설정 하 여 앱에는 명령을 실행할 수 있도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e598-177">To enable this feature you have to set a registry key so that the app can run the commands.</span></span> <span data-ttu-id="7e598-178">처음으로 명령을 실행 하려고 하면 Windows Device Portal 대 한 호출을 사용 하 여 레지스트리 키를 설정할 수 있는 링크가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="7e598-178">The first time you try to run a command you will see a link that allows you to set the registry key using a call to Windows Device Portal.</span></span> <span data-ttu-id="7e598-179">명령을 실행 하 여 장치에 대 한 링크를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e598-179">Click the link to enable your device to run commands.</span></span>

<span data-ttu-id="7e598-180">일부 명령에는 관리자 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="7e598-180">Some commands require administrator access.</span></span> <span data-ttu-id="7e598-181">보안상의 이유로 앱 기본적으로 관리자가 아닌 계정의 명령을 실행 하려면 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e598-181">For security purposes the app uses a non-admin account by default to run commands.</span></span> <span data-ttu-id="7e598-182">관리자로 서 명령을 실행 해야 하는 경우 입력할 수 있습니다 "RunAsAdmin <your command>" 명령줄 프롬프트에서.</span><span class="sxs-lookup"><span data-stu-id="7e598-182">If you need to run a command as an admin you can type "RunAsAdmin <your command>" in the command line prompt.</span></span>

## <a name="settings"></a><span data-ttu-id="7e598-183">설정</span><span class="sxs-lookup"><span data-stu-id="7e598-183">Settings</span></span>
<span data-ttu-id="7e598-184">Wi-fi, 블루투스, 전원 옵션 등을 포함 하 여 다음 설정을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e598-184">You'll be able to configure a number of settings here including Wi-Fi, Bluetooth, power options, and more.</span></span>

### <a name="app-settings"></a><span data-ttu-id="7e598-185">앱 설정</span><span class="sxs-lookup"><span data-stu-id="7e598-185">App Settings</span></span>
<span data-ttu-id="7e598-186">합니다 **앱 설정** 섹션을 사용 하면 앱에서 페이지의 다양 한 설정을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e598-186">The **App Settings** section allows you to configure various settings for pages in the app.</span></span>  

<span data-ttu-id="7e598-187">설정을 사용자 지정할 수는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="7e598-187">Some of the settings you can customize are:</span></span>

##### <a name="general-settings"></a><span data-ttu-id="7e598-188">일반 설정</span><span class="sxs-lookup"><span data-stu-id="7e598-188">General Settings</span></span>
* <span data-ttu-id="7e598-189">앱이 시작 될 때 표시 되는 기본 페이지를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e598-189">Set the default page that appears when the app is started</span></span>
* <span data-ttu-id="7e598-190">화면 보호기 사용/사용 안 함</span><span class="sxs-lookup"><span data-stu-id="7e598-190">Enable/disable the screensaver</span></span>

##### <a name="weather-settings"></a><span data-ttu-id="7e598-191">날씨 설정</span><span class="sxs-lookup"><span data-stu-id="7e598-191">Weather Settings</span></span>
* <span data-ttu-id="7e598-192">위치 변경</span><span class="sxs-lookup"><span data-stu-id="7e598-192">Change the location</span></span>
  > <span data-ttu-id="7e598-193">유효한 제공한 경우에이 기능이 설정 되어 [Bing 지도 서비스 토큰](https://msdn.microsoft.com/library/ff428642.aspx)합니다.</span><span class="sxs-lookup"><span data-stu-id="7e598-193">This feature is only enabled if you have provided a valid [Bing Map Service Token](https://msdn.microsoft.com/library/ff428642.aspx).</span></span>  <span data-ttu-id="7e598-194">앱에 토큰을 전달할를 만들려면를 **MapToken.config** 앱의 LocalState 폴더에 파일 (예: C:\Data\USERS\\[사용자 계정] \AppData\Packages\\[패키지 전체 이름] \LocalState\ MapToken.config) 하 고 앱 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e598-194">To pass the token to the app, create a **MapToken.config** file in the LocalState folder of the app (e.g. C:\Data\USERS\\[User Account]\AppData\Packages\\[Package Full Name]\LocalState\MapToken.config) and restart the app.</span></span>
* <span data-ttu-id="7e598-195">맵을 확장합니다</span><span class="sxs-lookup"><span data-stu-id="7e598-195">Expand the map</span></span>
* <span data-ttu-id="7e598-196">설정/해제 대칭 이동 된 데이터베이스 맵 및 날씨 스위치에서 화면 굽기 방지 하려면 정기적으로 배치 되도록 매핑</span><span class="sxs-lookup"><span data-stu-id="7e598-196">Enable/disable map flipping so that the map and the weather switch places periodically to prevent screen burn-in</span></span>

##### <a name="web-browser-settings"></a><span data-ttu-id="7e598-197">웹 브라우저 설정</span><span class="sxs-lookup"><span data-stu-id="7e598-197">Web Browser Settings</span></span>
* <span data-ttu-id="7e598-198">웹 브라우저의 홈 페이지를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e598-198">Set the home page for the Web Browser</span></span>

##### <a name="slideshow-settings"></a><span data-ttu-id="7e598-199">슬라이드 쇼 설정</span><span class="sxs-lookup"><span data-stu-id="7e598-199">Slideshow Settings</span></span>
* <span data-ttu-id="7e598-200">슬라이드 쇼 간격 설정</span><span class="sxs-lookup"><span data-stu-id="7e598-200">Set the slideshow interval</span></span>

##### <a name="appearance"></a><span data-ttu-id="7e598-201">모양</span><span class="sxs-lookup"><span data-stu-id="7e598-201">Appearance</span></span>
* <span data-ttu-id="7e598-202">타일 아이콘이 모 지 대신 MDL2 자산 사용</span><span class="sxs-lookup"><span data-stu-id="7e598-202">Use MDL2 Assets instead of Emojis for the tile icons</span></span>
* <span data-ttu-id="7e598-203">타일 너비와 높이 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e598-203">Set the tile width and height</span></span>
* <span data-ttu-id="7e598-204">UI 확장-설정 기본적으로 설정 되어 자동 크기 조정</span><span class="sxs-lookup"><span data-stu-id="7e598-204">Set UI scaling - Automatic scaling is set by default</span></span>
* <span data-ttu-id="7e598-205">타일 색 설정</span><span class="sxs-lookup"><span data-stu-id="7e598-205">Set the tile color</span></span>

#### <a name="system"></a><span data-ttu-id="7e598-206">시스템</span><span class="sxs-lookup"><span data-stu-id="7e598-206">System</span></span>
<span data-ttu-id="7e598-207">언어, 자판 배열, 표준 및 표준 시간대를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e598-207">Change the language, keyboard layout, and time zone.</span></span>

#### <a name="network--wi-fi"></a><span data-ttu-id="7e598-208">네트워크 및 Wi-fi</span><span class="sxs-lookup"><span data-stu-id="7e598-208">Network & Wi-Fi</span></span>
<span data-ttu-id="7e598-209">네트워크 어댑터 속성을 보거나 사용 가능한 Wi-fi 네트워크에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e598-209">View network adapter properties or connect to an available Wi-Fi network.</span></span>

#### <a name="bluetooth"></a><span data-ttu-id="7e598-210">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="7e598-210">Bluetooth</span></span>
<span data-ttu-id="7e598-211">Bluetooth 장치를 쌍으로 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e598-211">Pair with a Bluetooth device.</span></span>

#### <a name="app-updates"></a><span data-ttu-id="7e598-212">앱 업데이트</span><span class="sxs-lookup"><span data-stu-id="7e598-212">App Updates</span></span>
<span data-ttu-id="7e598-213">앱 업데이트를 확인 하거나 자동 업데이트 설정 변경.</span><span class="sxs-lookup"><span data-stu-id="7e598-213">Check for app updates or change automatic update settings.</span></span>

#### <a name="power-options"></a><span data-ttu-id="7e598-214">전원 옵션</span><span class="sxs-lookup"><span data-stu-id="7e598-214">Power Options</span></span>
<span data-ttu-id="7e598-215">다시 시작 또는 종료 장치입니다.</span><span class="sxs-lookup"><span data-stu-id="7e598-215">Restart or shutdown the device.</span></span>

#### <a name="diagnostics"></a><span data-ttu-id="7e598-216">진단</span><span class="sxs-lookup"><span data-stu-id="7e598-216">Diagnostics</span></span>
<span data-ttu-id="7e598-217">Microsoft 제공 하려는 진단 데이터의 크기를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e598-217">Select the amount of diagnostic data you wish to provide Microsoft.</span></span>  <span data-ttu-id="7e598-218">옵트인 할 것이 좋습니다 **전체** 진단 데이터를 신속 하 게 문제를 진단 하 제품을 개선할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e598-218">We encourage users to opt into **Full** diagnostic data so we can diagnose issues quickly and make improvements to the product.</span></span>

##### <a name="basic"></a><span data-ttu-id="7e598-219">Basic</span><span class="sxs-lookup"><span data-stu-id="7e598-219">Basic</span></span> 
<span data-ttu-id="7e598-220">장치, 설정 및 기능에 대 한 정보에만 보내기 여부이 제대로 수행 되 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e598-220">Send only info about your device, its settings and capabilities, and whether it is performing properly.</span></span>

##### <a name="full"></a><span data-ttu-id="7e598-221">전체</span><span class="sxs-lookup"><span data-stu-id="7e598-221">Full</span></span>
<span data-ttu-id="7e598-222">웹 사이트를 찾아보면 및 앱 및 기능을 사용 하는 방법에 대 한 정보 및 장치 상태, 장치 작업 및 향상 된 오류 보고에 대 한 추가 정보과 함께 모든 기본 진단 데이터를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="7e598-222">Send all Basic diagnostic data, along with info about websites you browse and how you use apps and features, plus additional info about device health, device activity, and enhanced error reporting.</span></span>

#### <a name="location"></a><span data-ttu-id="7e598-223">위치</span><span class="sxs-lookup"><span data-stu-id="7e598-223">Location</span></span>
<span data-ttu-id="7e598-224">허용 하거나 사용자의 위치에 대 한 앱 액세스를 거부 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e598-224">Allow or deny the app access to your location.</span></span>