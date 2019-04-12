---
title: Visual Studio 사용 하 여 앱 배포
author: bfjelds
ms.author: bfjelds
ms.date: 08/28/2017
ms.topic: article
description: Visual Studio 원격 디버깅 기능을 사용 하 여 앱을 배포 하는 방법에 알아봅니다.
keywords: windows iot, visual studio, 앱 배포, 원격 디버깅
ms.openlocfilehash: 218cbf43a1b63a517091b80315f327954b3eae5a
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513238"
---
# <a name="deploying-an-app-with-visual-studio"></a><span data-ttu-id="e12a4-104">Visual Studio 사용 하 여 앱 배포</span><span class="sxs-lookup"><span data-stu-id="e12a4-104">Deploying an App with Visual Studio</span></span>

<span data-ttu-id="e12a4-105">배포 및 응용 프로그램 디버깅에 Visual Studio를 사용 하 여 간단 합니다.</span><span class="sxs-lookup"><span data-stu-id="e12a4-105">Deploying and debugging your application is straightforward with Visual Studio.</span></span> <span data-ttu-id="e12a4-106">사용 된 **원격 디버깅** 로컬로 연결 된 Windows 10 IoT Core 장치에 앱을 배포 하는 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="e12a4-106">We'll use the **Remote Debugging** feature to deploy the app to your locally connected Windows 10 IoT Core device.</span></span> 

> [!NOTE]
> <span data-ttu-id="e12a4-107">Visual Studio는 RS5를 배포 하는 경우 암호화 오류가 생성 됩니다 (또는 RS4 OpenSSH 사용 하 여 사용 하도록 설정) IoT 이미지에서 RS4 이상 SDK는 Visual Studio에 액세스할 수 있도록 설치 되어 있지 않으면입니다.</span><span class="sxs-lookup"><span data-stu-id="e12a4-107">Visual Studio will generate a cryptic error when deploying to a RS5 (or RS4 with OpenSSH enabled) IoT image unless a SDK from RS4 or greater is installed that Visual Studio can access.</span></span>

> [!NOTE]
> <span data-ttu-id="e12a4-108">원격 디버깅을 사용 하려면 먼저 개발 PC와 같은 로컬 네트워크에 대 IoT Core 장치 연결 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e12a4-108">In order to use remote debugging, your IoT Core device must first be connected to same local network as your development PC.</span></span>  
><span data-ttu-id="e12a4-109">참조를 [장치로 연결](../connect-your-device/SetupWiFi.md) 지침입니다.</span><span class="sxs-lookup"><span data-stu-id="e12a4-109">See the [Connecting to a device](../connect-your-device/SetupWiFi.md) instructions.</span></span>

## <a name="deploy-a-c-app-to-your-windows-10-iot-core-device"></a><span data-ttu-id="e12a4-110">배포는 C# Windows 10 IoT Core 장치에 앱</span><span class="sxs-lookup"><span data-stu-id="e12a4-110">Deploy a C# app to your Windows 10 IoT Core device</span></span> 
___

1. <span data-ttu-id="e12a4-111">Visual Studio에서 응용 프로그램을 열고 도구 모음 드롭다운 목록에서 아키텍처를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e12a4-111">With the application open in Visual Studio, set the architecture in the toolbar dropdown.</span></span> <span data-ttu-id="e12a4-112">Minnowboard 최대 만든다면 선택 `x86`합니다.</span><span class="sxs-lookup"><span data-stu-id="e12a4-112">If you're building for Minnowboard Max, select `x86`.</span></span> <span data-ttu-id="e12a4-113">Raspberry Pi 2, Raspberry Pi 3에는 Dragonboard 만든다면 선택 `ARM`합니다.</span><span class="sxs-lookup"><span data-stu-id="e12a4-113">If you're building for Raspberry Pi 2, Raspberry Pi 3 or the Dragonboard, select `ARM`.</span></span>

2. <span data-ttu-id="e12a4-114">다음으로 Visual Studio 도구 모음에서 클릭 합니다 `Local Machine` 드롭다운에서 선택한 `Remote Machine`합니다.</span><span class="sxs-lookup"><span data-stu-id="e12a4-114">Next, in the Visual Studio toolbar, click on the `Local Machine` dropdown and select `Remote Machine`.</span></span>

![원격 컴퓨터에서 Visual Studio](../media/AppDeployment/cs-remote-machine-debugging.png)

3. <span data-ttu-id="e12a4-116">Visual Studio가 제공 하는 시점에서 **원격 연결** 대화 합니다.</span><span class="sxs-lookup"><span data-stu-id="e12a4-116">At this point, Visual Studio will present the **Remote Connections** dialog.</span></span> <span data-ttu-id="e12a4-117">이전에 사용한 [PowerShell](../connect-your-device/PowerShell.md) 장치에 대 한 고유 이름을 설정 하려면 사용자가 입력할 수 여기 (이 예제에서는 사용 중인 것 **내 장치**).</span><span class="sxs-lookup"><span data-stu-id="e12a4-117">If you previously used [PowerShell](../connect-your-device/PowerShell.md) to set a unique name for your device, you can enter it here (in this example, we're using **my device**).</span></span> <span data-ttu-id="e12a4-118">그렇지 않은 경우 Windows IoT Core 장치 IP 주소를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e12a4-118">Otherwise, use the IP address of your Windows IoT Core device.</span></span>

4. <span data-ttu-id="e12a4-119">장치 이름/i P를 입력 한 후 선택 `Universal (Unencrypted Protocol)` 인증 모드, 클릭 **선택**합니다.</span><span class="sxs-lookup"><span data-stu-id="e12a4-119">After entering the device name/IP select `Universal (Unencrypted Protocol)` Authentication Mode, then click **Select**.</span></span> 

![유니버설 인증 모드](../media/AppDeployment/cs-remote-connections.png)

<span data-ttu-id="e12a4-121">확인 하거나 프로젝트 속성으로 이동 하 여 이러한 값을 수정할 수 있습니다 (선택 **속성** 솔루션 탐색기에서)를 선택 하 고는 `Debug` 왼쪽 탭:</span><span class="sxs-lookup"><span data-stu-id="e12a4-121">You can verify or modify these values by navigating to the project properties (select **Properties** in the Solution Explorer) and choosing the `Debug` tab on the left:</span></span>

![디버그 탭](../media/AppDeployment/cs-debug-project-properties.png)

5. <span data-ttu-id="e12a4-123">이제 배포할 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e12a4-123">Now we're ready to deploy.</span></span> <span data-ttu-id="e12a4-124">간단히 F5 키를 눌러 (디버그 선택 또는 \| 디버깅 시작) 앱 디버깅을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="e12a4-124">Simply press F5 (or select Debug \| Start Debugging) to start debugging our app.</span></span> <span data-ttu-id="e12a4-125">장치의 화면에 표시 하는 앱이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e12a4-125">You should see the app come up on your device's screen.</span></span>

6. <span data-ttu-id="e12a4-126">을 배포한 후에 중단점, 참조 변수 값을 설정할 수 있습니다. 앱 키를 눌러 ' 디버깅 중지 ' 단추를 중지 하려면 (디버그 선택 또는 \| 디버깅 중지) 합니다.</span><span class="sxs-lookup"><span data-stu-id="e12a4-126">Once deployed, you can set breakpoints, see variable values, etc. To stop the app press on the 'Stop Debugging' button (or select Debug \| Stop Debugging).</span></span>

7. <span data-ttu-id="e12a4-127">성공적으로 배포 하 고 UWP 응용 프로그램 디버깅 만든 릴리스 버전-Visual Studio 도구 모음 구성 드롭다운 목록에서 변경할 `Debug` 에 `Release`입니다.</span><span class="sxs-lookup"><span data-stu-id="e12a4-127">After successfully deploying and debugging your UWP application, create a Release version - change the Visual Studio toolbar configuration dropdown from `Debug` to `Release`.</span></span>  <span data-ttu-id="e12a4-128">이제 빌드 및 빌드를 선택 하 여 장치에 앱을 배포할 수 있습니다 \| 솔루션 다시 빌드 및 빌드 \| 솔루션 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="e12a4-128">You can now build and deploy your app to your device by selecting Build \| Rebuild Solution and Build \| Deploy Solution.</span></span>

## <a name="deploy-a-c-app-to-your-windows-10-iot-core-device"></a><span data-ttu-id="e12a4-129">배포는 C++ Windows 10 IoT Core 장치에 앱</span><span class="sxs-lookup"><span data-stu-id="e12a4-129">Deploy a C++ app to your Windows 10 IoT Core device</span></span>

1. <span data-ttu-id="e12a4-130">Visual Studio에서 응용 프로그램을 열고 도구 모음 드롭다운 목록에서 아키텍처를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e12a4-130">With the application open in Visual Studio, set the architecture in the toolbar dropdown.</span></span> <span data-ttu-id="e12a4-131">Minnowboard 최대 만든다면 선택 `86`합니다.</span><span class="sxs-lookup"><span data-stu-id="e12a4-131">If you're building for Minnowboard Max, select `86`.</span></span> <span data-ttu-id="e12a4-132">Raspberry Pi 2 또는 3을 빌드하는 경우 선택 `ARM`합니다.</span><span class="sxs-lookup"><span data-stu-id="e12a4-132">If you're building for Raspberry Pi 2 or 3, select `ARM`.</span></span>

2. <span data-ttu-id="e12a4-133">다음으로 Visual Studio 도구 모음에서 클릭 된 `Local Machine` 드롭다운 선택</span><span class="sxs-lookup"><span data-stu-id="e12a4-133">Next, in the Visual Studio toolbar, click on the `Local Machine` dropdown and select</span></span> `Remote Machine`

![로컬 컴퓨터에서 Visual Studio](../media/AppDeployment/cpp-remote-machine-debugging.png)

3. <span data-ttu-id="e12a4-135">프로젝트를 마우스 오른쪽 단추로 클릭 다음에 **솔루션 탐색기** 창입니다.</span><span class="sxs-lookup"><span data-stu-id="e12a4-135">Next, right click on your project in the **Solution Explorer** pane.</span></span> <span data-ttu-id="e12a4-136">**속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e12a4-136">Select **Properties**.</span></span> 

![Visual Studio에서 속성](../media/AppDeployment/cpp-project-properties.png)

4. <span data-ttu-id="e12a4-138">아래 **구성 속성-> 디버깅**, 다음 필드를 수정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e12a4-138">Under **Configuration Properties -> Debugging**, modify the following fields:</span></span>

    * <span data-ttu-id="e12a4-139">**컴퓨터 이름을**: 이전에 사용한 [PowerShell](../connect-your-device/PowerShell.md) 장치에 대 한 고유 이름을 설정 하려면 사용자가 입력할 수 여기 (이 예제에서는 사용 중인 것 **내 장치**).</span><span class="sxs-lookup"><span data-stu-id="e12a4-139">**Machine Name**: If you previously used [PowerShell](../connect-your-device/PowerShell.md) to set a unique name for your device, you can enter it here (in this example, we're using **my-device**).</span></span> <span data-ttu-id="e12a4-140">그렇지 않은 경우 Windows IoT Core 장치 IP 주소를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e12a4-140">Otherwise, use the IP address of your Windows IoT Core device.</span></span>
    * <span data-ttu-id="e12a4-141">**인증 모드**: 로 **유니버설 (암호화 되지 않은 프로토콜)**</span><span class="sxs-lookup"><span data-stu-id="e12a4-141">**Authentication Mode**: Set to **Universal (Unencrypted Protocol)**</span></span>
    
![유니버설 인증 모드](../media/AppDeployment/cpp-debug-project-properties.png)

5. <span data-ttu-id="e12a4-143">이제 배포할 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e12a4-143">Now we're ready to deploy.</span></span> <span data-ttu-id="e12a4-144">간단히 F5 키를 눌러 (디버그 선택 또는 \| 디버깅 시작) 앱 디버깅을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="e12a4-144">Simply press F5 (or select Debug \| Start Debugging) to start debugging our app.</span></span> <span data-ttu-id="e12a4-145">Windows IoT Core 장치 화면에서 앱이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e12a4-145">You should see the app come up in Windows IoT Core device screen.</span></span>

6. <span data-ttu-id="e12a4-146">을 배포한 후에 중단점, 참조 변수 값을 설정할 수 있습니다. 앱을 중지 하려면 ' 디버깅 중지 ' 단추를 누릅니다 (디버그 선택 또는 \| 디버깅 중지) 합니다.</span><span class="sxs-lookup"><span data-stu-id="e12a4-146">Once deployed, you can set breakpoints, see variable values, etc. To stop the app, press on the 'Stop Debugging' button (or select Debug \| Stop Debugging).</span></span>

7. <span data-ttu-id="e12a4-147">성공적으로 배포 하 고 UWP 응용 프로그램을 디버깅 하지 릴리스 버전 만들기-Visual Studio 도구 모음 구성 드롭다운 목록에서 변경할 `Debug` 에 `Release`입니다.</span><span class="sxs-lookup"><span data-stu-id="e12a4-147">Having successfully deployed and debugged your UWP application, create a Release version - change the Visual Studio toolbar configuration dropdown from `Debug` to `Release`.</span></span>  <span data-ttu-id="e12a4-148">이제 빌드 및 빌드를 선택 하 여 장치에 앱을 배포할 수 있습니다 \| 솔루션 다시 빌드 및 빌드 \| 솔루션 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="e12a4-148">You can now build and deploy your app to your device by selecting Build \| Rebuild Solution and Build \| Deploy Solution.</span></span>

