---
title: 디버깅 개요
author: saraclay
ms.author: saclayt
ms.date: 05/10/2019
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: Windows 10 IoT Core 디버깅할 수 있는 다양 한 방법에 알아봅니다.
keywords: windows iot, 디버깅, PowerShell, SSH
ms.openlocfilehash: 64fa743416823a849deb2cb7826c149f9023a893
ms.sourcegitcommit: 77b86eee2bba3844e87f9d3dbef816761ddf0dd9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/11/2019
ms.locfileid: "65535833"
---
# <a name="debugging-on-windows-iot-core"></a><span data-ttu-id="606f0-104">Windows IoT Core에서 디버깅</span><span class="sxs-lookup"><span data-stu-id="606f0-104">Debugging on Windows IoT Core</span></span>
<span data-ttu-id="606f0-105">IoT Core 이미지 설치 프로그램을 만든 후 응용 프로그램을 실행 된 것이 중요 필요에 따라 응용 프로그램 또는 시스템을 디버그할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="606f0-105">Once you have your IoT Core image setup with running application, it is important that you can debug the application or the system as needed.</span></span> <span data-ttu-id="606f0-106">디버깅 및 테스트 시스템 가장 좋은 시간은 테스트 이미지 상태 동안입니다.</span><span class="sxs-lookup"><span data-stu-id="606f0-106">The best time to debug and test the system is while the test image state.</span></span> <span data-ttu-id="606f0-107">IoT Core 기반 시스템 실제로 초과 되 면 디버깅 challanging 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="606f0-107">Once IoT Core based systems is out in the wild, debugging can become challanging.</span></span> <span data-ttu-id="606f0-108">예를 들어을 수행할 수 없습니다 있지만 문제 디버그에 추가할 추가 계층을 사용 하 여 테스트를 비교 하지 않습니다 단계입니다.</span><span class="sxs-lookup"><span data-stu-id="606f0-108">That is not to say it can not be done but with additional layers of difficulties added to debug compare to a testing phases.</span></span> <span data-ttu-id="606f0-109">응용 프로그램 또는 테스트 모드에서 이미지를 디버깅 하려면 다음을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="606f0-109">You can use the following to debug your application or image while in test mode:</span></span>

## <a name="device-portal"></a><span data-ttu-id="606f0-110">장치 포털</span><span class="sxs-lookup"><span data-stu-id="606f0-110">Device Portal</span></span>
<span data-ttu-id="606f0-111">Windows Device Portal (WDP) 구성 하 고 로컬 네트워크를 통해 IoT 장치 remoately 프로그램을 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="606f0-111">Windows Device Portal (WDP) allows for you to configure and manage your IoT Device remoately over local network.</span></span> <span data-ttu-id="606f0-112">WDP은 IoT 장치의 로컬 ip를 통해 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="606f0-112">WDP can be reachable via local ip of the IoT Device.</span></span> <span data-ttu-id="606f0-113">WDP IoT에 대 한 추가 정보를 찾을 수 있습니다 [여기](https://docs.microsoft.com/en-us/windows/iot-core/manage-your-device/DevicePortal)합니다.</span><span class="sxs-lookup"><span data-stu-id="606f0-113">Additional information on WDP on IoT can be found [here](https://docs.microsoft.com/en-us/windows/iot-core/manage-your-device/DevicePortal).</span></span>

### <a name="collecting-etw--wpp-logs"></a><span data-ttu-id="606f0-114">ETW 수집 WPP 로그 /</span><span class="sxs-lookup"><span data-stu-id="606f0-114">Collecting ETW / WPP Logs</span></span> 
-----

### <a name="file-sharing"></a><span data-ttu-id="606f0-115">파일 공유</span><span class="sxs-lookup"><span data-stu-id="606f0-115">File Sharing</span></span>
<span data-ttu-id="606f0-116">앱 파일 탐색기를 앱에 액세스할 수 있는 디렉터리에 액세스를 허용할 수 있습니다 \* vCameraRoll가 모든 앱 공유</span><span class="sxs-lookup"><span data-stu-id="606f0-116">The App File Explorer can allow access to the directories that your apps can access \*vCameraRoll is shared among all apps</span></span>
* <span data-ttu-id="606f0-117">모든 앱에서 문서 공유</span><span class="sxs-lookup"><span data-stu-id="606f0-117">Documents is shared among all apps</span></span>
* <span data-ttu-id="606f0-118">LocalAppData 각 앱에 특정 폴더를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="606f0-118">LocalAppData contains folders specific to each app.</span></span> <span data-ttu-id="606f0-119">이 폴더의 이름은 앱 되며 다른 앱에 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="606f0-119">This folder will be the same name as your app and other apps cannot access it.</span></span>
<span data-ttu-id="606f0-120">위의 링크 추가 정보를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="606f0-120">See above link for additional information.</span></span>

### <a name="kernel-debug"></a><span data-ttu-id="606f0-121">커널 디버그</span><span class="sxs-lookup"><span data-stu-id="606f0-121">Kernel Debug</span></span>
<span data-ttu-id="606f0-122">라이브 커널 덤프 WDP 통해 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="606f0-122">You can download live Kernel dumps via WDP as well.</span></span> <span data-ttu-id="606f0-123">모든 시스템 충돌은 자동으로 기록 되어 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="606f0-123">Any system crashes will be automatically be logged and available for download.</span></span> <span data-ttu-id="606f0-124">위의 링크 추가 정보를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="606f0-124">See above link for additional information.</span></span>

### <a name="enable-crash-dump"></a><span data-ttu-id="606f0-125">크래시 덤프를 사용 하도록 설정</span><span class="sxs-lookup"><span data-stu-id="606f0-125">Enable Crash Dump</span></span>
<span data-ttu-id="606f0-126">WDP 통해 IoT 장치에 응용 프로그램의 크래시 덤프를 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="606f0-126">You can download crash dumps of applications on IoT Device via WDP.</span></span> <span data-ttu-id="606f0-127">위의 링크 추가 정보를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="606f0-127">See above link for additional information.</span></span>

## <a name="sshpowershelltshell"></a><span data-ttu-id="606f0-128">SSH/PowerShell/TShell</span><span class="sxs-lookup"><span data-stu-id="606f0-128">SSH/PowerShell/TShell</span></span>
<span data-ttu-id="606f0-129">PowerShell 작업 기반 명령줄 셸이자 스크립팅 언어, 시스템 관리를 위해 특별히 설계 된 경우</span><span class="sxs-lookup"><span data-stu-id="606f0-129">PowerShell is a task-based command-line shell and scripting language, designed especially for system administration.</span></span> <span data-ttu-id="606f0-130">디버깅 및 powershell 설정에 대 한 세부 정보를 찾을 수 있습니다 [여기](../connect-your-device/powershell.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="606f0-130">Details on debugging and setting up powershell can be found [here](../connect-your-device/powershell.md).</span></span>

## <a name="debug-through-visual-studio-deployment"></a><span data-ttu-id="606f0-131">Visual Studio 배포를 통해 디버그</span><span class="sxs-lookup"><span data-stu-id="606f0-131">Debug through Visual Studio Deployment</span></span>
<span data-ttu-id="606f0-132">배포 및 응용 프로그램 디버깅에 Visual Studio를 사용 하 여 간단 합니다.</span><span class="sxs-lookup"><span data-stu-id="606f0-132">Deploying and debugging your application is straightforward with Visual Studio.</span></span> <span data-ttu-id="606f0-133">원격 디버깅 기능을 배포 하 고 로컬로 연결 된 Windows 10 IoT Core 장치에 앱을 디버그할 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="606f0-133">Remote Debugging feature can be used to deploy and debug the app to your locally connected Windows 10 IoT Core device.</span></span> <span data-ttu-id="606f0-134">자세한 배포 및 디버깅 찾을 수 있습니다 [여기](../develop-your-app/RemoteDebugging.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="606f0-134">Detailed on deployment and debugging can be found [here](../develop-your-app/RemoteDebugging.md).</span></span>

-----
## <a name="live-app-debug"></a><span data-ttu-id="606f0-135">라이브 앱 디버그</span><span class="sxs-lookup"><span data-stu-id="606f0-135">Live App Debug</span></span>
<span data-ttu-id="606f0-136">Visual Studio 2015 이상에서 성능을 분석할 수 있으며 Azure Application Insights에서 원격 분석을 사용 하 여 ASP.NET 웹 앱 디버깅 및 프로덕션 환경에서의 문제를 진단할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="606f0-136">In Visual Studio (2015 and later), you can analyze performance and diagnose issues in your ASP.NET web app both in debugging and in production, using telemetry from Azure Application Insights.</span></span> <span data-ttu-id="606f0-137">기능은 나중에 Visual Studio 2017 및 Azure Portal을 통해 데스크톱 및 UWP 응용 프로그램을 포함 하도록 확장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="606f0-137">The feature is later extended to include desktop and UWP applications in Visual Studio 2017 and via Azure Portal.</span></span> <span data-ttu-id="606f0-138">프로젝트 디버깅에 대 한 추가 정보를 찾을 수 있습니다 [같습니다](https://docs.microsoft.com/en-us/azure/azure-monitor/app/visual-studio) 사용량과 데스크톱 또는 UWP 응용 프로그램에서 성능 모니터링을 확인할 수 있습니다 [여기](https://docs.microsoft.com/en-us/azure/azure-monitor/app/windows-desktop)합니다.</span><span class="sxs-lookup"><span data-stu-id="606f0-138">Additional information on debugging your project can be found [here](https://docs.microsoft.com/en-us/azure/azure-monitor/app/visual-studio) and monitoring usage, and performance in desktop or UWP appplications can be found [here](https://docs.microsoft.com/en-us/azure/azure-monitor/app/windows-desktop).</span></span>
