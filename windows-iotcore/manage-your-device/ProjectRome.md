---
title: Windows 10 IoT Core 사용 하 여 프로젝트 로마를 사용 하 여
author: saraclay
ms.author: saclayt
ms.date: 11/14/2017
ms.topic: article
description: 알아보고 출시 Windows IoT 장치를 수행 하는 단계를 이해 합니다.
keywords: windows 10 IoT Core, 프로젝트 로마 원격 장치
ms.openlocfilehash: cc016abad05dd54c7b948bcae8120b6da1724ee0
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59515051"
---
# <a name="using-project-rome-with-windows-10-iot-core"></a><span data-ttu-id="79b4b-104">Windows 10 IoT Core 사용 하 여 프로젝트 로마를 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="79b4b-104">Using Project Rome with Windows 10 IoT Core</span></span> 
 
<span data-ttu-id="79b4b-105">[로마 프로젝트](https://developer.microsoft.com/en-us/windows/project-rome) RemoteSystems 및 AppServiceProvider Api를 사용 하 여 Windows 10 IoT Core 실행 하는 장치를 원격으로 작업할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79b4b-105">[Project Rome](https://developer.microsoft.com/en-us/windows/project-rome) allows you to work remotely with devices running Windows 10 IoT Core using the RemoteSystems and AppServiceProvider APIs.</span></span> 
 
<span data-ttu-id="79b4b-106">이 문서에서는 컨트롤을 검색 하 고 프로젝트 로마를 사용 하 여 Windows 10 IoT Core 실행 하는 장치에 연결 하는 방법을 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="79b4b-106">In this article, we'll go through how to discover, control, and connect to devices running Windows 10 IoT Core with Project Rome.</span></span>  
 
## <a name="discovering-iot-core-devices-with-the-remotesystem-apis"></a><span data-ttu-id="79b4b-107">RemoteSystem Api를 사용 하 여 IoT Core 장치를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="79b4b-107">Discovering IoT Core devices with the RemoteSystem APIs</span></span> 
 
_<span data-ttu-id="79b4b-108">설정:</span><span class="sxs-lookup"><span data-stu-id="79b4b-108">Setup:</span></span>_
* <span data-ttu-id="79b4b-109">Microsoft 계정에 로그인 하는 동안 데스크톱에서 RemoteSystems 샘플을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="79b4b-109">Run the RemoteSystems sample on a Desktop while signed into your Microsoft account.</span></span>  
* <span data-ttu-id="79b4b-110">IoT Core에서 실행 중인 앱이 없음를 사용 하 여 로그인에 Cortana로 이동 하 여 Microsoft 계정에 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="79b4b-110">With no app running on IoT Core, sign into your Microsoft account by going to Cortana to login.</span></span> 
 
_<span data-ttu-id="79b4b-111">단계:</span><span class="sxs-lookup"><span data-stu-id="79b4b-111">Steps:</span></span>_
1. <span data-ttu-id="79b4b-112">바탕 화면에 RemoteSystems 샘플을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="79b4b-112">Run the RemoteSystems sample on your desktop</span></span> 
2. <span data-ttu-id="79b4b-113">"1) 검색에"에서 "시스템에 대 한 검색"를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="79b4b-113">Under "1) Discovery," click "Search for systems"</span></span> 

![시스템에 대 한 검색](../media/ProjectRome/SearchForSystems.gif)
 
## <a name="control-iot-core-devices-with-remotesystemslaunchuri"></a><span data-ttu-id="79b4b-115">RemoteSystems.LaunchUri 사용 하 여 IoT Core 장치를 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="79b4b-115">Control IoT Core devices with RemoteSystems.LaunchUri</span></span> 
 
_<span data-ttu-id="79b4b-116">설정:</span><span class="sxs-lookup"><span data-stu-id="79b4b-116">Setup:</span></span>_
* <span data-ttu-id="79b4b-117">실행 합니다 [RemoteSystems 샘플](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/RemoteSystems) 데스크톱 잠시에 [Microsoft 계정 로그인](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WebAccountManagement)합니다.</span><span class="sxs-lookup"><span data-stu-id="79b4b-117">Run the [RemoteSystems sample](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/RemoteSystems) on a Desktop while [signed into your Microsoft account](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WebAccountManagement).</span></span>
* <span data-ttu-id="79b4b-118">IoT Core에서 실행 중인 앱이 없음를 사용 하 여 로그인에 Cortana로 이동 하 여 Microsoft 계정에 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="79b4b-118">With no app running on IoT Core, sign into your Microsoft account by going to Cortana to login.</span></span> 
 
_<span data-ttu-id="79b4b-119">단계:</span><span class="sxs-lookup"><span data-stu-id="79b4b-119">Steps:</span></span>_
1. <span data-ttu-id="79b4b-120">Cortana 및 Cortana에서 Microsoft 계정의 로그인을 사용 하 여 IoT Core 가상 컴퓨터를 켭니다.</span><span class="sxs-lookup"><span data-stu-id="79b4b-120">Turn on the IoT Core virtual machine with Cortana and sign into your Microsoft account from Cortana.</span></span> 
2. <span data-ttu-id="79b4b-121">데스크톱에서 RemoteSystems 샘플을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="79b4b-121">Run the RemoteSystems sample on Desktop.</span></span> 
3. <span data-ttu-id="79b4b-122">"1) 검색", "시스템에 대 한 검색"을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="79b4b-122">Under "1) Discovery", click "Search for systems".</span></span> 
4. <span data-ttu-id="79b4b-123">"2) 시작 URI" 아래에서 Cortana를 실행 하는 IoT Core 장치를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="79b4b-123">Under "2) Launch URI", select the IoT Core device that is running Cortana.</span></span> 
5. <span data-ttu-id="79b4b-124">이 URI와 실행을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="79b4b-124">Enter this URI and launch.</span></span> 

![시작 URI](../media/ProjectRome/LaunchURI.gif)

## <a name="connecting-to-the-remote-app-service-running-on-iot-core"></a><span data-ttu-id="79b4b-126">IoT Core에서 실행 중인 원격 App Service에 연결</span><span class="sxs-lookup"><span data-stu-id="79b4b-126">Connecting to the Remote App Service running on IoT Core</span></span> 
_<span data-ttu-id="79b4b-127">설정:</span><span class="sxs-lookup"><span data-stu-id="79b4b-127">Setup:</span></span>_
* <span data-ttu-id="79b4b-128">실행 합니다 [RemoteSystems 샘플](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/RemoteSystems) 데스크톱 잠시에 [Microsoft 계정 로그인](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WebAccountManagement)합니다.</span><span class="sxs-lookup"><span data-stu-id="79b4b-128">Run the [RemoteSystems sample](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/RemoteSystems) on a Desktop while [signed into your Microsoft account](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WebAccountManagement).</span></span> 
* <span data-ttu-id="79b4b-129">되었는지 확인 합니다 [AppServiceProvider 앱](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/AppServices) 하나 이상의 IoT Core 장치에서 실행 되 고 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="79b4b-129">Make sure to have the [AppServiceProvider app](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/AppServices) deployed and running on at least one IoT Core device.</span></span> 
 
_<span data-ttu-id="79b4b-130">단계:</span><span class="sxs-lookup"><span data-stu-id="79b4b-130">Steps:</span></span>_
1. <span data-ttu-id="79b4b-131">Cortana 사용 하 여 IoT 코어 가상 머신에서에서 설정 및 Cortana에서 Microsoft 계정에 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="79b4b-131">Turn on the IoT Core Virtual Machine with Cortana, and sign into your Microsoft account from Cortana.</span></span> <span data-ttu-id="79b4b-132">AppServiceProvider 앱 배포, 한 번 실행 한 다음 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="79b4b-132">Deploy the AppServiceProvider app, run it once, then shut it down.</span></span> 
2. <span data-ttu-id="79b4b-133">데스크톱에서 RemoteSystems 샘플을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="79b4b-133">Run the RemoteSystems sample on desktop.</span></span> 
3. <span data-ttu-id="79b4b-134">"1) 검색", "시스템에 대 한 검색"을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="79b4b-134">Under "1) Discovery", click "Search for systems".</span></span> 
4. <span data-ttu-id="79b4b-135">"3) 시작 App services 에서" IoT core 장치 AppServiceProvider 앱이 배포 된 이전에 실행을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="79b4b-135">Under "3) Launch App Services," select the IoT core device that has the AppServiceProvider app deployed and has been run previously.</span></span> 
5. <span data-ttu-id="79b4b-136">난수를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="79b4b-136">Generate a random number.</span></span>  

![App Services 시작](../media/ProjectRome/LaunchAppServices.gif)
 
## <a name="controlling-other-devices-and-app-services-from-an-iot-core-device"></a><span data-ttu-id="79b4b-138">다른 장치 및 IoT Core 장치에서 앱 서비스를 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="79b4b-138">Controlling other devices and app services from an IoT Core device</span></span> 

_<span data-ttu-id="79b4b-139">설정:</span><span class="sxs-lookup"><span data-stu-id="79b4b-139">Setup:</span></span>_
* <span data-ttu-id="79b4b-140">실행 합니다 [RemoteSystems 샘플](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/RemoteSystems) 하는 동안 IoT Core 장치에 배포 된 [Microsoft 계정 로그인](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WebAccountManagement) Cortana 앱에서.</span><span class="sxs-lookup"><span data-stu-id="79b4b-140">Run the [RemoteSystems sample](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/RemoteSystems) deployed on an IoT Core device while [signed into your Microsoft account](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WebAccountManagement) from the Cortana app.</span></span> 
* <span data-ttu-id="79b4b-141">데스크톱 컴퓨터를 [AppServiceProvider 앱](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/AppServices) 배포 하 고 한 번 이상 실행 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="79b4b-141">Have a desktop machine with the [AppServiceProvider app](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/AppServices) deployed and having been run at least once.</span></span> 
 
_<span data-ttu-id="79b4b-142">단계:</span><span class="sxs-lookup"><span data-stu-id="79b4b-142">Steps:</span></span>_
1. <span data-ttu-id="79b4b-143">RemoteSystems 샘플을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="79b4b-143">Run the RemoteSystems sample.</span></span> 
2. <span data-ttu-id="79b4b-144">"1) 검색", "시스템에 대 한 검색"을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="79b4b-144">Under "1) Discovery", click on "Search for systems".</span></span> 
3. <span data-ttu-id="79b4b-145">"2) 시작 URI" 아래에서 선택 하 고 데스크톱 컴퓨터 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="79b4b-145">Under "2) Launch URI", select the Desktop machine and launch.</span></span> 
4. <span data-ttu-id="79b4b-146">"3) 시작 App services"에서 데스크톱 컴퓨터를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="79b4b-146">Under "3) Launch App Services", select the desktop machine.</span></span>  
 
> [!NOTE] 
> <span data-ttu-id="79b4b-147">첫 번째 시도에서 시간이 오래 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79b4b-147">On first attempt, this may take a long time.</span></span> <span data-ttu-id="79b4b-148">다시이 훨씬 더 빠르게 응답 합니다.</span><span class="sxs-lookup"><span data-stu-id="79b4b-148">Try this again for a much quicker response.</span></span> 
 
### <a name="helpful-links"></a><span data-ttu-id="79b4b-149">유용한 링크:</span><span class="sxs-lookup"><span data-stu-id="79b4b-149">Helpful links:</span></span> 
* [<span data-ttu-id="79b4b-150">MSDN에 대 한 프로젝트 로마 설명서</span><span class="sxs-lookup"><span data-stu-id="79b4b-150">Project Rome documentation on MSDN</span></span>](https://developer.microsoft.com/en-us/windows/project-rome )
* [<span data-ttu-id="79b4b-151">Uwp 프로젝트 로마를 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="79b4b-151">Using Project Rome for UWP</span></span>](https://docs.microsoft.com/windows/uwp/launch-resume/connected-apps-and-devices )
 
