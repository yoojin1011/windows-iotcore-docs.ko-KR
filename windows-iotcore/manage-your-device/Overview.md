---
title: 디버깅 개요
author: saraclay
ms.author: saclayt
ms.date: 05/10/2019
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: Windows 10 IoT Core를 디버그할 수 있는 여러 가지 방법에 대해 알아봅니다.
keywords: windows iot, 디버깅, PowerShell, SSH
ms.openlocfilehash: 64fa743416823a849deb2cb7826c149f9023a893
ms.sourcegitcommit: 77b86eee2bba3844e87f9d3dbef816761ddf0dd9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/11/2019
ms.locfileid: "65535833"
---
# <a name="debugging-on-windows-iot-core"></a><span data-ttu-id="d70e0-104">Windows IoT Core에서 디버깅</span><span class="sxs-lookup"><span data-stu-id="d70e0-104">Debugging on Windows IoT Core</span></span>
<span data-ttu-id="d70e0-105">응용 프로그램을 실행 하 여 IoT Core 이미지를 설치한 후에는 필요에 따라 응용 프로그램 또는 시스템을 디버그할 수 있는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="d70e0-105">Once you have your IoT Core image setup with running application, it is important that you can debug the application or the system as needed.</span></span> <span data-ttu-id="d70e0-106">시스템을 디버깅 하 고 테스트 하는 데 가장 적합 한 시기는 테스트 이미지 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="d70e0-106">The best time to debug and test the system is while the test image state.</span></span> <span data-ttu-id="d70e0-107">IoT 코어 기반 시스템이 야생 경우 디버깅이 challanging 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d70e0-107">Once IoT Core based systems is out in the wild, debugging can become challanging.</span></span> <span data-ttu-id="d70e0-108">이는 수행할 수 없으며 테스트 단계와의 비교를 디버그 하기 위해 추가 어려움이 추가 된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="d70e0-108">That is not to say it can not be done but with additional layers of difficulties added to debug compare to a testing phases.</span></span> <span data-ttu-id="d70e0-109">테스트 모드에서 다음을 사용 하 여 응용 프로그램 또는 이미지를 디버그할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d70e0-109">You can use the following to debug your application or image while in test mode:</span></span>

## <a name="device-portal"></a><span data-ttu-id="d70e0-110">장치 포털</span><span class="sxs-lookup"><span data-stu-id="d70e0-110">Device Portal</span></span>
<span data-ttu-id="d70e0-111">WDP (Windows 장치 포털)를 사용 하면 로컬 네트워크를 통해 IoT 장치 remoately을 구성 하 고 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d70e0-111">Windows Device Portal (WDP) allows for you to configure and manage your IoT Device remoately over local network.</span></span> <span data-ttu-id="d70e0-112">IoT 장치의 로컬 ip를 통해 WDP에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d70e0-112">WDP can be reachable via local ip of the IoT Device.</span></span> <span data-ttu-id="d70e0-113">IoT의 WDP에 대 한 추가 정보는 [여기](https://docs.microsoft.com/en-us/windows/iot-core/manage-your-device/DevicePortal)에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d70e0-113">Additional information on WDP on IoT can be found [here](https://docs.microsoft.com/en-us/windows/iot-core/manage-your-device/DevicePortal).</span></span>

### <a name="collecting-etw--wpp-logs"></a><span data-ttu-id="d70e0-114">ETW/WPP 로그 수집</span><span class="sxs-lookup"><span data-stu-id="d70e0-114">Collecting ETW / WPP Logs</span></span> 
-----

### <a name="file-sharing"></a><span data-ttu-id="d70e0-115">파일 공유</span><span class="sxs-lookup"><span data-stu-id="d70e0-115">File Sharing</span></span>
<span data-ttu-id="d70e0-116">앱 파일 탐색기는 앱이 액세스할 수 있는 디렉터리에 대 한 액세스를 허용할 수 있습니다. \* vCameraRoll는 모든 앱에서 공유 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d70e0-116">The App File Explorer can allow access to the directories that your apps can access \*vCameraRoll is shared among all apps</span></span>
* <span data-ttu-id="d70e0-117">문서는 모든 앱에서 공유 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d70e0-117">Documents is shared among all apps</span></span>
* <span data-ttu-id="d70e0-118">LocalAppData에는 각 앱에 해당 하는 폴더가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d70e0-118">LocalAppData contains folders specific to each app.</span></span> <span data-ttu-id="d70e0-119">이 폴더는 앱과 이름이 같으며 다른 앱은 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d70e0-119">This folder will be the same name as your app and other apps cannot access it.</span></span>
<span data-ttu-id="d70e0-120">자세한 내용은 위의 링크를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="d70e0-120">See above link for additional information.</span></span>

### <a name="kernel-debug"></a><span data-ttu-id="d70e0-121">커널 디버그</span><span class="sxs-lookup"><span data-stu-id="d70e0-121">Kernel Debug</span></span>
<span data-ttu-id="d70e0-122">WDP를 통해 live Kernel 덤프를 다운로드할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d70e0-122">You can download live Kernel dumps via WDP as well.</span></span> <span data-ttu-id="d70e0-123">모든 시스템 크래시는 자동으로 기록 되 고 다운로드 가능 합니다.</span><span class="sxs-lookup"><span data-stu-id="d70e0-123">Any system crashes will be automatically be logged and available for download.</span></span> <span data-ttu-id="d70e0-124">자세한 내용은 위의 링크를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="d70e0-124">See above link for additional information.</span></span>

### <a name="enable-crash-dump"></a><span data-ttu-id="d70e0-125">크래시 덤프 사용</span><span class="sxs-lookup"><span data-stu-id="d70e0-125">Enable Crash Dump</span></span>
<span data-ttu-id="d70e0-126">WDP를 통해 IoT 장치에서 응용 프로그램의 크래시 덤프를 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d70e0-126">You can download crash dumps of applications on IoT Device via WDP.</span></span> <span data-ttu-id="d70e0-127">자세한 내용은 위의 링크를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="d70e0-127">See above link for additional information.</span></span>

## <a name="sshpowershelltshell"></a><span data-ttu-id="d70e0-128">SSH/PowerShell/TShell</span><span class="sxs-lookup"><span data-stu-id="d70e0-128">SSH/PowerShell/TShell</span></span>
<span data-ttu-id="d70e0-129">PowerShell은 시스템 관리를 위해 특별히 설계 된 작업 기반 명령줄 셸 및 스크립트 언어입니다.</span><span class="sxs-lookup"><span data-stu-id="d70e0-129">PowerShell is a task-based command-line shell and scripting language, designed especially for system administration.</span></span> <span data-ttu-id="d70e0-130">Powershell 디버깅 및 설정에 대 한 자세한 내용은 [여기](../connect-your-device/powershell.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d70e0-130">Details on debugging and setting up powershell can be found [here](../connect-your-device/powershell.md).</span></span>

## <a name="debug-through-visual-studio-deployment"></a><span data-ttu-id="d70e0-131">Visual Studio 배포를 통해 디버그</span><span class="sxs-lookup"><span data-stu-id="d70e0-131">Debug through Visual Studio Deployment</span></span>
<span data-ttu-id="d70e0-132">Visual Studio를 사용 하면 응용 프로그램을 간편 하 게 배포 하 고 디버그할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d70e0-132">Deploying and debugging your application is straightforward with Visual Studio.</span></span> <span data-ttu-id="d70e0-133">원격 디버깅 기능을 사용 하 여 로컬에 연결 된 Windows 10 IoT Core 장치에 앱을 배포 하 고 디버그할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d70e0-133">Remote Debugging feature can be used to deploy and debug the app to your locally connected Windows 10 IoT Core device.</span></span> <span data-ttu-id="d70e0-134">배포 및 디버깅에 대 한 자세한 내용은 [여기](../develop-your-app/RemoteDebugging.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d70e0-134">Detailed on deployment and debugging can be found [here](../develop-your-app/RemoteDebugging.md).</span></span>

-----
## <a name="live-app-debug"></a><span data-ttu-id="d70e0-135">라이브 앱 디버그</span><span class="sxs-lookup"><span data-stu-id="d70e0-135">Live App Debug</span></span>
<span data-ttu-id="d70e0-136">Visual Studio (2015 이상)에서는 Azure 애플리케이션 Insights의 원격 분석을 사용 하 여 디버깅 및 프로덕션 환경에서 ASP.NET 웹 앱의 성능을 분석 하 고 문제를 진단할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d70e0-136">In Visual Studio (2015 and later), you can analyze performance and diagnose issues in your ASP.NET web app both in debugging and in production, using telemetry from Azure Application Insights.</span></span> <span data-ttu-id="d70e0-137">이 기능은 나중에 Visual Studio 2017 및 Azure Portal을 통해 데스크톱 및 UWP 응용 프로그램을 포함 하도록 확장 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="d70e0-137">The feature is later extended to include desktop and UWP applications in Visual Studio 2017 and via Azure Portal.</span></span> <span data-ttu-id="d70e0-138">프로젝트를 디버그 하는 방법에 대 한 추가 정보는 [여기](https://docs.microsoft.com/en-us/azure/azure-monitor/app/visual-studio) 에서 확인할 수 있으며, 데스크톱 또는 UWP 응용 프로그램의 성능 및 모니터링은 [여기](https://docs.microsoft.com/en-us/azure/azure-monitor/app/windows-desktop)에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d70e0-138">Additional information on debugging your project can be found [here](https://docs.microsoft.com/en-us/azure/azure-monitor/app/visual-studio) and monitoring usage, and performance in desktop or UWP appplications can be found [here](https://docs.microsoft.com/en-us/azure/azure-monitor/app/windows-desktop).</span></span>
