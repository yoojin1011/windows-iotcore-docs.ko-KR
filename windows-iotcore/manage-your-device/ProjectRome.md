---
title: Windows 10 IoT Core에서 Project 로마 사용
ms.date: 11/14/2017
ms.topic: article
description: Windows IoT 장치를 출시 하는 단계를 알아보고 파악 합니다.
keywords: windows 10 IoT Core, 프로젝트 로마, 원격 장치
ms.openlocfilehash: dcf1ba9bec776b2ebde0d374266bb4d7dba3baec
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72917315"
---
# <a name="using-project-rome-with-windows-10-iot-core"></a><span data-ttu-id="69a19-104">Windows 10 IoT Core에서 Project 로마 사용</span><span class="sxs-lookup"><span data-stu-id="69a19-104">Using Project Rome with Windows 10 IoT Core</span></span> 
 
<span data-ttu-id="69a19-105">[프로젝트 로마](https://developer.microsoft.com/en-us/windows/project-rome) 를 사용 하면 RemoteSystems 및 AppServiceProvider api를 사용 하 여 Windows 10 IoT Core를 실행 하는 장치에서 원격으로 작업할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69a19-105">[Project Rome](https://developer.microsoft.com/en-us/windows/project-rome) allows you to work remotely with devices running Windows 10 IoT Core using the RemoteSystems and AppServiceProvider APIs.</span></span> 
 
<span data-ttu-id="69a19-106">이 문서에서는 Project 로마를 사용 하 여 Windows 10 IoT Core를 실행 하는 장치를 검색, 제어 및 연결 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="69a19-106">In this article, we'll go through how to discover, control, and connect to devices running Windows 10 IoT Core with Project Rome.</span></span>  
 
## <a name="discovering-iot-core-devices-with-the-remotesystem-apis"></a><span data-ttu-id="69a19-107">RemoteSystem Api를 사용 하 여 IoT Core 장치 검색</span><span class="sxs-lookup"><span data-stu-id="69a19-107">Discovering IoT Core devices with the RemoteSystem APIs</span></span> 
 
<span data-ttu-id="69a19-108">_설치_</span><span class="sxs-lookup"><span data-stu-id="69a19-108">_Setup:_</span></span>
* <span data-ttu-id="69a19-109">Microsoft 계정에 로그인 한 상태에서 바탕 화면에서 RemoteSystems 샘플을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="69a19-109">Run the RemoteSystems sample on a Desktop while signed into your Microsoft account.</span></span>  
* <span data-ttu-id="69a19-110">IoT Core에서 실행 되는 앱이 없는 경우 Cortana로 이동 하 여 로그인으로 이동 하 여 Microsoft 계정에 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="69a19-110">With no app running on IoT Core, sign into your Microsoft account by going to Cortana to login.</span></span> 
 
<span data-ttu-id="69a19-111">_위한_</span><span class="sxs-lookup"><span data-stu-id="69a19-111">_Steps:_</span></span>
1. <span data-ttu-id="69a19-112">바탕 화면에서 RemoteSystems 샘플 실행</span><span class="sxs-lookup"><span data-stu-id="69a19-112">Run the RemoteSystems sample on your desktop</span></span> 
2. <span data-ttu-id="69a19-113">"1" 검색에서 "시스템 검색"을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="69a19-113">Under "1) Discovery," click "Search for systems"</span></span> 

![시스템 검색](../media/ProjectRome/SearchForSystems.gif)
 
## <a name="control-iot-core-devices-with-remotesystemslaunchuri"></a><span data-ttu-id="69a19-115">RemoteSystems Uri를 사용 하 여 IoT Core 장치 제어</span><span class="sxs-lookup"><span data-stu-id="69a19-115">Control IoT Core devices with RemoteSystems.LaunchUri</span></span> 
 
<span data-ttu-id="69a19-116">_설치_</span><span class="sxs-lookup"><span data-stu-id="69a19-116">_Setup:_</span></span>
* <span data-ttu-id="69a19-117">[Microsoft 계정에 로그인](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WebAccountManagement)한 상태에서 바탕 화면에서 [RemoteSystems 샘플](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/RemoteSystems) 을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="69a19-117">Run the [RemoteSystems sample](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/RemoteSystems) on a Desktop while [signed into your Microsoft account](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WebAccountManagement).</span></span>
* <span data-ttu-id="69a19-118">IoT Core에서 실행 되는 앱이 없는 경우 Cortana로 이동 하 여 로그인으로 이동 하 여 Microsoft 계정에 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="69a19-118">With no app running on IoT Core, sign into your Microsoft account by going to Cortana to login.</span></span> 
 
<span data-ttu-id="69a19-119">_위한_</span><span class="sxs-lookup"><span data-stu-id="69a19-119">_Steps:_</span></span>
1. <span data-ttu-id="69a19-120">Cortana를 사용 하 여 IoT Core 가상 머신을 켜고 Cortana에서 Microsoft 계정에 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="69a19-120">Turn on the IoT Core virtual machine with Cortana and sign into your Microsoft account from Cortana.</span></span> 
2. <span data-ttu-id="69a19-121">바탕 화면에서 RemoteSystems 샘플을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="69a19-121">Run the RemoteSystems sample on Desktop.</span></span> 
3. <span data-ttu-id="69a19-122">"1) 검색"에서 "시스템 검색"을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="69a19-122">Under "1) Discovery", click "Search for systems".</span></span> 
4. <span data-ttu-id="69a19-123">"2) 시작 URI"에서 Cortana를 실행 하는 IoT Core 장치를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="69a19-123">Under "2) Launch URI", select the IoT Core device that is running Cortana.</span></span> 
5. <span data-ttu-id="69a19-124">이 URI를 입력 하 고 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="69a19-124">Enter this URI and launch.</span></span> 

![시작 URI](../media/ProjectRome/LaunchURI.gif)

## <a name="connecting-to-the-remote-app-service-running-on-iot-core"></a><span data-ttu-id="69a19-126">IoT Core에서 실행 되는 원격 App Service에 연결</span><span class="sxs-lookup"><span data-stu-id="69a19-126">Connecting to the Remote App Service running on IoT Core</span></span> 
<span data-ttu-id="69a19-127">_설치_</span><span class="sxs-lookup"><span data-stu-id="69a19-127">_Setup:_</span></span>
* <span data-ttu-id="69a19-128">[Microsoft 계정에 로그인](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WebAccountManagement)한 상태에서 바탕 화면에서 [RemoteSystems 샘플](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/RemoteSystems) 을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="69a19-128">Run the [RemoteSystems sample](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/RemoteSystems) on a Desktop while [signed into your Microsoft account](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WebAccountManagement).</span></span> 
* <span data-ttu-id="69a19-129">[AppServiceProvider 앱](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/AppServices) 이 하나 이상의 IoT Core 장치에 배포 되 고 실행 중인지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="69a19-129">Make sure to have the [AppServiceProvider app](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/AppServices) deployed and running on at least one IoT Core device.</span></span> 
 
<span data-ttu-id="69a19-130">_위한_</span><span class="sxs-lookup"><span data-stu-id="69a19-130">_Steps:_</span></span>
1. <span data-ttu-id="69a19-131">Cortana를 사용 하 여 IoT Core 가상 머신을 켜고 Cortana에서 Microsoft 계정에 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="69a19-131">Turn on the IoT Core Virtual Machine with Cortana, and sign into your Microsoft account from Cortana.</span></span> <span data-ttu-id="69a19-132">AppServiceProvider 앱을 배포 하 고 한 번 실행 한 후 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="69a19-132">Deploy the AppServiceProvider app, run it once, then shut it down.</span></span> 
2. <span data-ttu-id="69a19-133">바탕 화면에서 RemoteSystems 샘플을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="69a19-133">Run the RemoteSystems sample on desktop.</span></span> 
3. <span data-ttu-id="69a19-134">"1) 검색"에서 "시스템 검색"을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="69a19-134">Under "1) Discovery", click "Search for systems".</span></span> 
4. <span data-ttu-id="69a19-135">"3) 시작 App Services에서" AppServiceProvider 앱을 배포 하 고 이전에 실행 한 IoT core 장치를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="69a19-135">Under "3) Launch App Services," select the IoT core device that has the AppServiceProvider app deployed and has been run previously.</span></span> 
5. <span data-ttu-id="69a19-136">난수를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="69a19-136">Generate a random number.</span></span>  

![시작 App Services](../media/ProjectRome/LaunchAppServices.gif)
 
## <a name="controlling-other-devices-and-app-services-from-an-iot-core-device"></a><span data-ttu-id="69a19-138">IoT Core 장치에서 기타 장치 및 앱 서비스 제어</span><span class="sxs-lookup"><span data-stu-id="69a19-138">Controlling other devices and app services from an IoT Core device</span></span> 

<span data-ttu-id="69a19-139">_설치_</span><span class="sxs-lookup"><span data-stu-id="69a19-139">_Setup:_</span></span>
* <span data-ttu-id="69a19-140">Cortana 앱에서 [Microsoft 계정에 로그인](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WebAccountManagement) 한 상태에서 IoT Core 장치에 배포 된 [RemoteSystems 샘플](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/RemoteSystems) 을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="69a19-140">Run the [RemoteSystems sample](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/RemoteSystems) deployed on an IoT Core device while [signed into your Microsoft account](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WebAccountManagement) from the Cortana app.</span></span> 
* <span data-ttu-id="69a19-141">[AppServiceProvider 앱](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/AppServices) 을 사용 하 여 데스크톱 컴퓨터를 배포 하 고 한 번 이상 실행 했습니다.</span><span class="sxs-lookup"><span data-stu-id="69a19-141">Have a desktop machine with the [AppServiceProvider app](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/AppServices) deployed and having been run at least once.</span></span> 
 
<span data-ttu-id="69a19-142">_위한_</span><span class="sxs-lookup"><span data-stu-id="69a19-142">_Steps:_</span></span>
1. <span data-ttu-id="69a19-143">RemoteSystems 샘플을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="69a19-143">Run the RemoteSystems sample.</span></span> 
2. <span data-ttu-id="69a19-144">"1) 검색"에서 "시스템 검색"을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="69a19-144">Under "1) Discovery", click on "Search for systems".</span></span> 
3. <span data-ttu-id="69a19-145">"2) 시작 URI"에서 데스크톱 컴퓨터를 선택 하 고를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="69a19-145">Under "2) Launch URI", select the Desktop machine and launch.</span></span> 
4. <span data-ttu-id="69a19-146">"3) 시작 App Services"에서 데스크톱 컴퓨터를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="69a19-146">Under "3) Launch App Services", select the desktop machine.</span></span>  
 
> [!NOTE] 
> <span data-ttu-id="69a19-147">처음 시도 하면 시간이 오래 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69a19-147">On first attempt, this may take a long time.</span></span> <span data-ttu-id="69a19-148">훨씬 더 빠른 응답을 위해 다시 시도 하세요.</span><span class="sxs-lookup"><span data-stu-id="69a19-148">Try this again for a much quicker response.</span></span> 
 
### <a name="helpful-links"></a><span data-ttu-id="69a19-149">유용한 링크:</span><span class="sxs-lookup"><span data-stu-id="69a19-149">Helpful links:</span></span> 
* [<span data-ttu-id="69a19-150">MSDN의 Project 로마 설명서</span><span class="sxs-lookup"><span data-stu-id="69a19-150">Project Rome documentation on MSDN</span></span>](https://developer.microsoft.com/en-us/windows/project-rome )
* [<span data-ttu-id="69a19-151">UWP 용 Project 로마 사용</span><span class="sxs-lookup"><span data-stu-id="69a19-151">Using Project Rome for UWP</span></span>](https://docs.microsoft.com/windows/uwp/launch-resume/connected-apps-and-devices )
 
