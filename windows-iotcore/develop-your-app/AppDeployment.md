---
title: Visual Studio 사용 하 여 앱 배포
author: bfjelds
ms.author: bfjelds
ms.date: 08/28/2017
ms.topic: article
description: Visual Studio 원격 디버깅 기능을 사용 하 여 앱을 배포 하는 방법에 알아봅니다.
keywords: windows iot, visual studio, 앱 배포, 원격 디버깅
ms.openlocfilehash: ea0d95fc3702e1cec7f6bda35450c5da495cd837
ms.sourcegitcommit: 77b86eee2bba3844e87f9d3dbef816761ddf0dd9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/11/2019
ms.locfileid: "65533370"
---
# <a name="deploying-an-app-with-visual-studio"></a><span data-ttu-id="0d6da-104">Visual Studio 사용 하 여 앱 배포</span><span class="sxs-lookup"><span data-stu-id="0d6da-104">Deploying an App with Visual Studio</span></span>

<span data-ttu-id="0d6da-105">배포 및 응용 프로그램 디버깅에 Visual Studio를 사용 하 여 간단 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d6da-105">Deploying and debugging your application is straightforward with Visual Studio.</span></span> <span data-ttu-id="0d6da-106">사용 된 **원격 디버깅** 로컬로 연결 된 Windows 10 IoT Core 장치에 앱을 배포 하는 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="0d6da-106">We'll use the **Remote Debugging** feature to deploy the app to your locally connected Windows 10 IoT Core device.</span></span> 

> [!NOTE]
> <span data-ttu-id="0d6da-107">Visual Studio는 RS5를 배포 하는 경우 암호화 오류가 생성 됩니다 (또는 RS4 OpenSSH 사용 하 여 사용 하도록 설정) IoT 이미지에서 RS4 이상 SDK는 Visual Studio에 액세스할 수 있도록 설치 되어 있지 않으면입니다.</span><span class="sxs-lookup"><span data-stu-id="0d6da-107">Visual Studio will generate a cryptic error when deploying to a RS5 (or RS4 with OpenSSH enabled) IoT image unless a SDK from RS4 or greater is installed that Visual Studio can access.</span></span>

> [!NOTE]
> <span data-ttu-id="0d6da-108">원격 디버깅을 사용 하려면 IoT Core 장치 먼저 연결 해야 개발 PC와 같은 로컬 네트워크에 및 네트워크에서 UDP/TCP 통신을 허용 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d6da-108">In order to use remote debugging, your IoT Core device must first be connected to the same local network as your development PC and UDP/TCP communications should be allowed on the network.</span></span> <span data-ttu-id="0d6da-109">확실 하지 않은의 경우 it 부서에서 허용 되는 네트워크 트래픽 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d6da-109">If in doubt, check with your IT on allowed network traffic.</span></span> <span data-ttu-id="0d6da-110">참조 [장치로 연결](../connect-your-device/SetupWiFi.md) 지침에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d6da-110">See [Connecting to a device](../connect-your-device/SetupWiFi.md) for instructions.</span></span>

## <a name="deploy-apps-to-your-windows-10-iot-core-device"></a><span data-ttu-id="0d6da-111">Windows 10 IoT Core 장치에 앱 배포</span><span class="sxs-lookup"><span data-stu-id="0d6da-111">Deploy apps to your Windows 10 IoT Core device</span></span>

1. <span data-ttu-id="0d6da-112">Visual Studio에서 응용 프로그램을 열고 도구 모음 드롭다운 목록에서 아키텍처를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d6da-112">With the application open in Visual Studio, set the architecture in the toolbar dropdown.</span></span> <span data-ttu-id="0d6da-113">Minnowboard 최대 만든다면 선택 `x86`합니다.</span><span class="sxs-lookup"><span data-stu-id="0d6da-113">If you're building for a Minnowboard Max, select `x86`.</span></span> <span data-ttu-id="0d6da-114">Raspberry Pi 2, Raspberry Pi 3에는 Dragonboard 만든다면 선택 `ARM`합니다.</span><span class="sxs-lookup"><span data-stu-id="0d6da-114">If you're building for Raspberry Pi 2, Raspberry Pi 3 or the Dragonboard, select `ARM`.</span></span>

2. <span data-ttu-id="0d6da-115">다음으로 Visual Studio 도구 모음에서 클릭 합니다 `Local Machine` 드롭다운에서 선택한 `Remote Machine`합니다.</span><span class="sxs-lookup"><span data-stu-id="0d6da-115">Next, in the Visual Studio toolbar, click on the `Local Machine` dropdown and select `Remote Machine`.</span></span>

![원격 컴퓨터에서 Visual Studio](../media/AppDeployment/remote-vs.png)

3. <span data-ttu-id="0d6da-117">Visual Studio가 제공 하는 시점에서 **원격 연결** 대화 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d6da-117">At this point, Visual Studio will present the **Remote Connections** dialog.</span></span> <span data-ttu-id="0d6da-118">이전에 사용한 [PowerShell](../connect-your-device/PowerShell.md) 장치에 대 한 고유 이름을 설정 하려면 사용자가 입력할 수 여기 (이 예제에서는 사용 중인 것 **내 장치**).</span><span class="sxs-lookup"><span data-stu-id="0d6da-118">If you previously used [PowerShell](../connect-your-device/PowerShell.md) to set a unique name for your device, you can enter it here (in this example, we're using **my device**).</span></span> <span data-ttu-id="0d6da-119">그렇지 않은 경우 Windows IoT Core 장치 IP 주소를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d6da-119">Otherwise, use the IP address of your Windows IoT Core device.</span></span>

4. <span data-ttu-id="0d6da-120">장치 이름/i P를 입력 한 후 선택 `Universal (Unencrypted Protocol)` 인증 모드, 클릭 **선택**합니다.</span><span class="sxs-lookup"><span data-stu-id="0d6da-120">After entering the device name/IP select `Universal (Unencrypted Protocol)` Authentication Mode, then click **Select**.</span></span> 

![유니버설 인증 모드](../media/AppDeployment/remote-connections.png)

<span data-ttu-id="0d6da-122">확인 하거나 프로젝트 속성으로 이동 하 여 이러한 값을 수정할 수 있습니다 (선택 **속성** 솔루션 탐색기에서)를 선택 하 고는 `Debug` 왼쪽 탭:</span><span class="sxs-lookup"><span data-stu-id="0d6da-122">You can verify or modify these values by navigating to the project properties (select **Properties** in the Solution Explorer) and choosing the `Debug` tab on the left:</span></span>

![디버그 탭](../media/AppDeployment/debug-tab.png)

5. <span data-ttu-id="0d6da-124">이제 배포할 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0d6da-124">Now we're ready to deploy.</span></span> <span data-ttu-id="0d6da-125">간단히 F5 키를 눌러 (또는 디버그 선택 | 디버깅을 시작 하는) 앱을 디버깅을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d6da-125">Simply press F5 (or select Debug | Start Debugging) to start debugging our app.</span></span> <span data-ttu-id="0d6da-126">장치의 화면에 표시 하는 앱이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0d6da-126">You should see the app come up on your device's screen.</span></span>

6. <span data-ttu-id="0d6da-127">을 배포한 후에 중단점, 참조 변수 값을 설정할 수 있습니다. 앱 키를 눌러 ' 디버깅 중지 ' 단추를 중지 하려면 (디버그 선택 또는 | 디버깅 중지) 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d6da-127">Once deployed, you can set breakpoints, see variable values, etc. To stop the app press on the 'Stop Debugging' button (or select Debug | Stop Debugging).</span></span>

7. <span data-ttu-id="0d6da-128">성공적으로 배포 하 고 UWP 응용 프로그램 디버깅 만든 릴리스 버전-Visual Studio 도구 모음 구성 드롭다운 목록에서 변경할 `Debug` 에 `Release`입니다.</span><span class="sxs-lookup"><span data-stu-id="0d6da-128">After successfully deploying and debugging your UWP application, create a Release version - change the Visual Studio toolbar configuration dropdown from `Debug` to `Release`.</span></span>  <span data-ttu-id="0d6da-129">이제 빌드 및 빌드를 선택 하 여 장치에 앱을 배포할 수 있습니다 | 솔루션 다시 빌드 및 빌드 | 솔루션을 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d6da-129">You can now build and deploy your app to your device by selecting Build | Rebuild Solution and Build | Deploy Solution.</span></span>
