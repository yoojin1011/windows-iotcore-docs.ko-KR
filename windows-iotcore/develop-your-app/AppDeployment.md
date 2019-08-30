---
title: Visual Studio를 사용 하 여 앱 배포
author: bfjelds
ms.author: bfjelds
ms.date: 08/28/2017
ms.topic: article
description: Visual Studio 원격 디버깅 기능을 사용 하 여 앱을 배포 하는 방법을 알아봅니다.
keywords: windows iot, visual studio, 앱 배포, 원격 디버깅
ms.openlocfilehash: ea0d95fc3702e1cec7f6bda35450c5da495cd837
ms.sourcegitcommit: 77b86eee2bba3844e87f9d3dbef816761ddf0dd9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/11/2019
ms.locfileid: "65533370"
---
# <a name="deploying-an-app-with-visual-studio"></a><span data-ttu-id="7968e-104">Visual Studio를 사용 하 여 앱 배포</span><span class="sxs-lookup"><span data-stu-id="7968e-104">Deploying an App with Visual Studio</span></span>

<span data-ttu-id="7968e-105">Visual Studio를 사용 하면 응용 프로그램을 간편 하 게 배포 하 고 디버그할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7968e-105">Deploying and debugging your application is straightforward with Visual Studio.</span></span> <span data-ttu-id="7968e-106">**원격 디버깅** 기능을 사용 하 여 로컬에 연결 된 Windows 10 IoT Core 장치에 앱을 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="7968e-106">We'll use the **Remote Debugging** feature to deploy the app to your locally connected Windows 10 IoT Core device.</span></span> 

> [!NOTE]
> <span data-ttu-id="7968e-107">Visual Studio에서 액세스할 수 있는 RS4 이상의 SDK를 설치하지 않으면 RS5(또는 OpenSSH를 사용하는 RS4) IoT 이미지에 배포할 때 Visual Studio가 암호화 오류를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="7968e-107">Visual Studio will generate a cryptic error when deploying to a RS5 (or RS4 with OpenSSH enabled) IoT image unless a SDK from RS4 or greater is installed that Visual Studio can access.</span></span>

> [!NOTE]
> <span data-ttu-id="7968e-108">원격 디버깅을 사용 하려면 먼저 IoT Core 장치를 개발 PC와 동일한 로컬 네트워크에 연결 해야 하 고 UDP/TCP 통신이 네트워크에서 허용 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7968e-108">In order to use remote debugging, your IoT Core device must first be connected to the same local network as your development PC and UDP/TCP communications should be allowed on the network.</span></span> <span data-ttu-id="7968e-109">확실 하지 않은 경우 네트워크 트래픽이 허용 되는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="7968e-109">If in doubt, check with your IT on allowed network traffic.</span></span> <span data-ttu-id="7968e-110">지침은 [장치에 연결](../connect-your-device/SetupWiFi.md) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7968e-110">See [Connecting to a device](../connect-your-device/SetupWiFi.md) for instructions.</span></span>

## <a name="deploy-apps-to-your-windows-10-iot-core-device"></a><span data-ttu-id="7968e-111">Windows 10 IoT Core 장치에 앱 배포</span><span class="sxs-lookup"><span data-stu-id="7968e-111">Deploy apps to your Windows 10 IoT Core device</span></span>

1. <span data-ttu-id="7968e-112">Visual Studio에서 응용 프로그램을 열고 도구 모음 드롭다운에서 아키텍처를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7968e-112">With the application open in Visual Studio, set the architecture in the toolbar dropdown.</span></span> <span data-ttu-id="7968e-113">Minnowboard Max에 대해 빌드하는 경우를 선택 `x86`합니다.</span><span class="sxs-lookup"><span data-stu-id="7968e-113">If you're building for a Minnowboard Max, select `x86`.</span></span> <span data-ttu-id="7968e-114">Raspberry Pi 2, Raspberry Pi 3 또는 Dragonboard에 대해 빌드하는 경우를 선택 `ARM`합니다.</span><span class="sxs-lookup"><span data-stu-id="7968e-114">If you're building for Raspberry Pi 2, Raspberry Pi 3 or the Dragonboard, select `ARM`.</span></span>

2. <span data-ttu-id="7968e-115">그런 다음 Visual Studio 도구 모음에서 `Local Machine` 드롭다운을 클릭 하 고를 선택 `Remote Machine`합니다.</span><span class="sxs-lookup"><span data-stu-id="7968e-115">Next, in the Visual Studio toolbar, click on the `Local Machine` dropdown and select `Remote Machine`.</span></span>

![Visual Studio의 원격 컴퓨터](../media/AppDeployment/remote-vs.png)

3. <span data-ttu-id="7968e-117">이 시점에서 Visual Studio는 **원격 연결** 대화 상자를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="7968e-117">At this point, Visual Studio will present the **Remote Connections** dialog.</span></span> <span data-ttu-id="7968e-118">이전에 [PowerShell](../connect-your-device/PowerShell.md) 을 사용 하 여 장치에 대 한 고유한 이름을 설정한 경우 여기에 입력할 수 있습니다 (이 예제에서는 **내 장치**를 사용 하 고 있음).</span><span class="sxs-lookup"><span data-stu-id="7968e-118">If you previously used [PowerShell](../connect-your-device/PowerShell.md) to set a unique name for your device, you can enter it here (in this example, we're using **my device**).</span></span> <span data-ttu-id="7968e-119">그렇지 않으면 Windows IoT 핵심 장치의 IP 주소를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7968e-119">Otherwise, use the IP address of your Windows IoT Core device.</span></span>

4. <span data-ttu-id="7968e-120">장치 이름/i p를 입력 한 `Universal (Unencrypted Protocol)` 후 인증 모드를 선택 하 고 **선택**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7968e-120">After entering the device name/IP select `Universal (Unencrypted Protocol)` Authentication Mode, then click **Select**.</span></span> 

![유니버설 인증 모드](../media/AppDeployment/remote-connections.png)

<span data-ttu-id="7968e-122">프로젝트 속성 (솔루션 탐색기에서 **속성** 선택)으로 이동 하 고 왼쪽의 `Debug` 탭을 선택 하 여 이러한 값을 확인 하거나 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7968e-122">You can verify or modify these values by navigating to the project properties (select **Properties** in the Solution Explorer) and choosing the `Debug` tab on the left:</span></span>

![디버그 탭](../media/AppDeployment/debug-tab.png)

5. <span data-ttu-id="7968e-124">이제 배포할 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7968e-124">Now we're ready to deploy.</span></span> <span data-ttu-id="7968e-125">F5 키를 누르면 됩니다 (또는 디버그 | 선택 디버깅 시작)을 시작 하 여 응용 프로그램 디버깅을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="7968e-125">Simply press F5 (or select Debug | Start Debugging) to start debugging our app.</span></span> <span data-ttu-id="7968e-126">앱이 장치 화면에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7968e-126">You should see the app come up on your device's screen.</span></span>

6. <span data-ttu-id="7968e-127">일단 배포 되 면 중단점을 설정 하 고 변수 값 등을 볼 수 있습니다. 앱을 중지 하려면 ' 디버깅 중지 ' 단추를 누르거나 [디버그]를 선택 합니다. 디버깅 중지).</span><span class="sxs-lookup"><span data-stu-id="7968e-127">Once deployed, you can set breakpoints, see variable values, etc. To stop the app press on the 'Stop Debugging' button (or select Debug | Stop Debugging).</span></span>

7. <span data-ttu-id="7968e-128">UWP 응용 프로그램을 성공적으로 배포 하 고 디버깅 한 후 릴리스 버전을 만듭니다.-Visual Studio 도구 모음 `Debug` 구성 `Release`드롭다운을에서로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="7968e-128">After successfully deploying and debugging your UWP application, create a Release version - change the Visual Studio toolbar configuration dropdown from `Debug` to `Release`.</span></span>  <span data-ttu-id="7968e-129">이제 빌드를 선택 하 여 장치에 앱을 빌드하고 배포할 수 있습니다. 솔루션 다시 빌드 및 빌드 | 솔루션 배포.</span><span class="sxs-lookup"><span data-stu-id="7968e-129">You can now build and deploy your app to your device by selecting Build | Rebuild Solution and Build | Deploy Solution.</span></span>
