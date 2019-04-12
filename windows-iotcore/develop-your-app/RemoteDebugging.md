---
title: 원격 콘솔 응용 프로그램 디버깅을 사용 하 여 앱 디버그
author: bfjelds
ms.author: bfjelds
ms.date: 09/12/17
ms.topic: article
description: Visual Studio에서 원격으로 IoT Core 콘솔 응용 프로그램을 원격으로 디버그 하는 방법에 알아봅니다.
keywords: windows iot, visual studio, 앱 배포, 원격 디버깅
ms.openlocfilehash: dc3afad193bc6356a5f897f386f5061adaf6bc01
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512893"
---
# <a name="debug-your-app-using-remote-console-app-debugging"></a><span data-ttu-id="8092a-104">원격 콘솔 응용 프로그램 디버깅을 사용 하 여 앱 디버그</span><span class="sxs-lookup"><span data-stu-id="8092a-104">Debug your app using Remote Console App Debugging</span></span>

<span data-ttu-id="8092a-105">Visual Studio에서 원격으로 IoT Core 콘솔 응용 프로그램을 디버그 하는 방법을 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8092a-105">Here's how to debug your IoT Core console application remotely in Visual Studio:</span></span>

* <span data-ttu-id="8092a-106">먼저 Windows IoT Core 장치에서 원격 디버거를 설치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8092a-106">You will first need to setup the Remote Debugger on your Windows IoT Core device.</span></span> <span data-ttu-id="8092a-107">먼저 단계를 따릅니다 [여기](AppDeployment.md) 다른 유니버설 Windows 응용 프로그램 (시도 HelloWorld 프로젝트) 장치에 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="8092a-107">First follow the steps [here](AppDeployment.md) to deploy any other Universal Windows Application on your device (try the HelloWorld project).</span></span> <span data-ttu-id="8092a-108">장치에 필요한 모든 이진 파일이 복사 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8092a-108">This will copy all the required binaries to your device.</span></span> 

* <span data-ttu-id="8092a-109">장치에서 원격 디버거를 시작 하려면 PC에서 웹 브라우저를 열고 가리키도록 `http://<device name/IP address>:8080` 시작할 [Windows Device Portal](../manage-your-device/DevicePortal.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="8092a-109">To start the remote debugger on your device, open a Web Browser on your PC and point it to `http://<device name/IP address>:8080` to launch [Windows Device Portal](../manage-your-device/DevicePortal.md).</span></span> <span data-ttu-id="8092a-110">자격 증명 대화 상자에서 기본 사용자 이름 및 암호를 사용 합니다. `Administrator`, `p@ssw0rd`합니다.</span><span class="sxs-lookup"><span data-stu-id="8092a-110">In the credentials dialog, use the default username and password: `Administrator`, `p@ssw0rd`.</span></span> <span data-ttu-id="8092a-111">Windows 장치 관리를 시작 하 고 웹 관리 홈 화면을 표시 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8092a-111">Windows Device Management should launch and display the web management home screen.</span></span>

* <span data-ttu-id="8092a-112">이제 Windows Device Portal 디버그 설정 섹션으로 이동 하 고 Visual Studio 원격 디버거 시작에서 시작 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8092a-112">Now navigate to the Debug settings section of Windows Device Portal and click the Start button under Start Visual Studio Remote Debugger.</span></span> 

    ![원격 디버거 WindowsDevicePortalDebugSettings 시작](../media/Console/device_portal_start_debugger.png)

* <span data-ttu-id="8092a-114">이 팝업 메시지 상자를 표시 되며 연결 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="8092a-114">This will show pop-up a message box and give you the connection information.</span></span> 

*  <span data-ttu-id="8092a-115">Visual Studio에서 대상 (해야 모든 보드의 이름 또는 IP 주소를 적절 하 게 강조 표시 된 변경 내용 확인) 하는 프로젝트의 속성을 편집 하 여 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8092a-115">In Visual Studio, you can configure your target by editing your project's properties (be sure to make all of the highlighted changes as appropriate to your board's name or IP address):</span></span>

    ![ConsoleApplication 원격 컴퓨터 프로젝트 설정](../media/Console/console_project_settings.png)
    
> [!NOTE]
> <span data-ttu-id="8092a-117">위의 이미지에 표시 되지 않는 경우 상황에 맞는 메뉴에서 "솔루션 탐색기"로 이동 하 고 "프로젝트 속성"으로 이동 하세요.</span><span class="sxs-lookup"><span data-stu-id="8092a-117">If you're not seeing the image above, please go to the "Solution Explorer" in the context menu, and go to "Project Properties".</span></span> <span data-ttu-id="8092a-118">프로젝트 속성에 대 한 자세한 정보를 찾을 수 있습니다 [여기](https://docs.microsoft.com/visualstudio/ide/managing-project-and-solution-properties?view=vs-2017)합니다.</span><span class="sxs-lookup"><span data-stu-id="8092a-118">You can find more information for project properties [here](https://docs.microsoft.com/visualstudio/ide/managing-project-and-solution-properties?view=vs-2017).</span></span>

> [!TIP]
> <span data-ttu-id="8092a-119">Windows IoT Core 장치 이름 대신 IP 주소를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8092a-119">You can use the IP address instead of the Windows IoT Core device name.</span></span>

* <span data-ttu-id="8092a-120">프로젝트 구성 배포를 사용 하도록 수정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8092a-120">The project configuration needs to be modified to enable deployment.</span></span>  <span data-ttu-id="8092a-121">이 작업을 수행 하려면 도구 모음에서 솔루션 구성 드롭다운 메뉴에서 Configuration manger를 선택 하 여 Configuration Manager를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="8092a-121">To do this, open the Configuration Manager by selecting the Configuration manger from the Solution Configuration drop-down menu on the toolbar.</span></span>

    ![ConsoleApplication SolutionConfiguration](../media/Console/configuration_management.png)

    <span data-ttu-id="8092a-123">Configuration Manager에서 배포 확인란 프로젝트 구성에 대해 선택 되어 있는지 확인 (이 옵션을 사용 하지 않도록 설정 하는 경우 가능성이 배포 옵션 입력 하지 않았습니다 된 완벽 하 게 프로젝트 속성의 디버그 탭)</span><span class="sxs-lookup"><span data-stu-id="8092a-123">From the Configuration Manager, ensure that the Deploy checkbox is selected for your project configuration (if this options is disabled, it is likely that the deployment options have not been fully entered into the Debugging tab of the project properties)</span></span>

    ![ConsoleApplication 원격 컴퓨터 프로젝트 설정](../media/Console/deploy_checkbox.png)

* <span data-ttu-id="8092a-125">이제 원격 Windows IoT Core 장치에 배포할 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8092a-125">Now we're ready to deploy to the remote Windows IoT Core device.</span></span> <span data-ttu-id="8092a-126">간단히 F5 키를 눌러 (디버그 선택 또는 \| 디버깅 시작) 앱 디버깅을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="8092a-126">Simply press F5 (or select Debug \| Start Debugging) to start debugging our app.</span></span> <span data-ttu-id="8092a-127">빌드를 사용할 수도 있습니다 \| 하기만 하면 디버그 세션을 시작 하지 않고 응용 프로그램을 배포 하려면 솔루션을 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="8092a-127">You can also use Build \| Deploy Solution to simply deploy your application without starting a debug session.</span></span>

> [!NOTE]
> <span data-ttu-id="8092a-128">출력 Visual Studio에서 실행 하는 경우 어디서 나 표시 되지 않습니다 하지만 중단점을 설정, 변수 값 등 참조 하는 일을 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8092a-128">When run from Visual Studio, the output will not display anywhere, but you will be able to set breakpoints, see variable values, etc.</span></span>

* <span data-ttu-id="8092a-129">앱을 중지 하려면 ' 디버깅 중지 ' 단추를 누릅니다 (디버그 선택 또는 \| 디버깅 중지) 합니다.</span><span class="sxs-lookup"><span data-stu-id="8092a-129">To stop the app, press on the 'Stop Debugging' button (or select Debug \| Stop Debugging).</span></span>

* <span data-ttu-id="8092a-130">이제 응용 프로그램을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8092a-130">You can now run the application.</span></span>  <span data-ttu-id="8092a-131">PowerShell/SSH 연결을 열고 (지침을 찾을 수 있습니다 [PowerShell에 대 한 여기](../connect-your-device/PowerShell.md) 하 고 [SSH에 대 한 여기](../connect-your-device/SSH.md)) 위에서 지정한 원격 명령을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="8092a-131">Simply open a PowerShell/SSH connection (instructions can be found [here for PowerShell](../connect-your-device/PowerShell.md) and [here for SSH](../connect-your-device/SSH.md)) and enter the Remote Command you specified above.</span></span>

    ![ConsoleApplication 출력](../media/Console/console_output.png)

* <span data-ttu-id="8092a-133">완료 되 면 응용 프로그램 디버깅 Windows IoT Core 장치에서 원격 디버거를 중지 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8092a-133">Once you are done debugging your application, remember to stop the remote debugger on the Windows IoT Core device.</span></span> <span data-ttu-id="8092a-134">디버그 Windows Device Portal 설정 섹션으로 이동 하 고 원격 디버거 중지 단추를 클릭 하 여이 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8092a-134">You can do this by navigating to Debug settings section of Windows Device Portal and clicking on the Stop Remote Debugger button.</span></span>

    ![원격 디버거 WindowsDevicePortalDebugSettings 중지](../media/Console/device_portal_stop_debugger.PNG)

