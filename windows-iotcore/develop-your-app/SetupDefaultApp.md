---
title: 기본 앱 설정
author: bfjelds
ms.author: bfjelds
ms.date: 09/05/17
ms.topic: article
description: Windows 장치 포털 또는 셸을 사용 하 여 기본 앱을 설정 하는 방법을 알아봅니다.
keywords: windows iot, 기본 앱, PowerShell, iot
ms.openlocfilehash: f3f7a5194491250a8a0b49e81e073282c8f5660b
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "60170250"
---
# <a name="setup-a-default-app"></a><span data-ttu-id="23ee9-104">기본 앱 설정</span><span class="sxs-lookup"><span data-stu-id="23ee9-104">Setup a default app</span></span>
<span data-ttu-id="23ee9-105">여기서는 응용 프로그램을 기본 응용 프로그램으로 설정 하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="23ee9-105">Here you'll learn the ways to set your application as the default application.</span></span> <span data-ttu-id="23ee9-106">기본 응용 프로그램은 시스템이 부팅 될 때 실행 되는 응용 프로그램입니다.</span><span class="sxs-lookup"><span data-stu-id="23ee9-106">The default application is the one that is launched when the system boots.</span></span>  

> [!NOTE]
> <span data-ttu-id="23ee9-107">Visual Studio에서 액세스할 수 있는 RS4 이상의 SDK를 설치하지 않으면 RS5(또는 OpenSSH를 사용하는 RS4) IoT 이미지에 배포할 때 Visual Studio가 암호화 오류를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="23ee9-107">Visual Studio will generate a cryptic error when deploying to a RS5 (or RS4 with OpenSSH enabled) IoT image unless a SDK from RS4 or greater is installed that Visual Studio can access.</span></span>

## <a name="runtime-options"></a><span data-ttu-id="23ee9-108">런타임 옵션</span><span class="sxs-lookup"><span data-stu-id="23ee9-108">Runtime options</span></span>

<span data-ttu-id="23ee9-109">개발/실험적 단계 중에 다음 방법으로 기본 앱을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23ee9-109">During development / experimental phases, you can change the default app by following means.</span></span>

### <a name="using-windows-device-portal"></a><span data-ttu-id="23ee9-110">Windows 장치 포털 사용</span><span class="sxs-lookup"><span data-stu-id="23ee9-110">Using Windows Device Portal</span></span>

<span data-ttu-id="23ee9-111">앱에 해당 하는 **시작** 열을 클릭할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23ee9-111">You can click on **Startup** column corresponding to the app.</span></span>
<span data-ttu-id="23ee9-112">![SetupDefaultAppWDP](../media/SetupDefaultApp/DefaultAppWDP.png)</span><span class="sxs-lookup"><span data-stu-id="23ee9-112">![SetupDefaultAppWDP](../media/SetupDefaultApp/DefaultAppWDP.png)</span></span>

### <a name="using-the-shell"></a><span data-ttu-id="23ee9-113">Shell 사용</span><span class="sxs-lookup"><span data-stu-id="23ee9-113">Using the shell</span></span>

<span data-ttu-id="23ee9-114">셸을 사용 하 여 기본 앱을 설정 하는 단계</span><span class="sxs-lookup"><span data-stu-id="23ee9-114">Steps to set the default app using the shell</span></span> 

1. <span data-ttu-id="23ee9-115">[Powershell](../connect-your-device/PowerShell.md) 을 통해 장치에 연결</span><span class="sxs-lookup"><span data-stu-id="23ee9-115">Connect to the device via [Powershell](../connect-your-device/PowerShell.md)</span></span>

2. <span data-ttu-id="23ee9-116">을 사용 하 여 설치 된 응용 프로그램 나열`iotstartup list`</span><span class="sxs-lookup"><span data-stu-id="23ee9-116">List the applications installed using `iotstartup list`</span></span>

3. <span data-ttu-id="23ee9-117">기본값으로 지정할 응용 프로그램의 appid를 확인 하 고을 사용 하 여 `iotstartup add headed <appid>`설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="23ee9-117">Note the appid for the application you want to make as default and set it using `iotstartup add headed <appid>`.</span></span> <span data-ttu-id="23ee9-118">헤드리스 응용 프로그램의 경우를 사용 `iotstartup add headless <appid>`해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="23ee9-118">For headless app, you should use `iotstartup add headless <appid>`.</span></span>


## <a name="build-time-option"></a><span data-ttu-id="23ee9-119">빌드 시간 옵션</span><span class="sxs-lookup"><span data-stu-id="23ee9-119">Build time option</span></span>

<span data-ttu-id="23ee9-120">대량 배포의 경우 프로 비전 패키지를 사용 하 여이를 달성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23ee9-120">For large deployments, you can achieve this using provisioning package</span></span>

<span data-ttu-id="23ee9-121">프로 비전 패키지를 만드는 동안 WCD에서 StartupApp/Default 설정을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23ee9-121">You can specify the StartupApp/Default setting in the WCD during the provisioning package creation.</span></span>
<span data-ttu-id="23ee9-122">![SetupDefaultAppICD](../media/SetupDefaultApp/DefaultAppICD.png)</span><span class="sxs-lookup"><span data-stu-id="23ee9-122">![SetupDefaultAppICD](../media/SetupDefaultApp/DefaultAppICD.png)</span></span>

<span data-ttu-id="23ee9-123">예를 들어 [IoTCoreDefaultApp](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Packages/Appx.IoTCoreDefaultApp/customizations.xml) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="23ee9-123">See [Appx.IoTCoreDefaultApp](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Packages/Appx.IoTCoreDefaultApp/customizations.xml) as an example.</span></span> <span data-ttu-id="23ee9-124">[GetAppxInfo 도구](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools/GetAppxInfo.exe)를 사용 하 여 Appx의 응용 프로그램 사용자 모델 ID (AUMID)를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23ee9-124">You can get the Application User Model ID (AUMID) of an appx using [GetAppxInfo tool](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools/GetAppxInfo.exe).</span></span>

## <a name="how-to-configure-home-key"></a><span data-ttu-id="23ee9-125">"홈" 키를 구성 하는 방법</span><span class="sxs-lookup"><span data-stu-id="23ee9-125">How to configure "Home" key</span></span>

<span data-ttu-id="23ee9-126">Windows 10 IoT 기념일 업데이트 (1607)는 다른 응용 프로그램이 현재 실행 중일 때 기본 응용 프로그램 창을 포그라운드로 가져오기 위한 셸을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="23ee9-126">Windows 10 IoT Anniversary Update (1607) provides shell support for bringing the default application window to the foreground when another application is currently running.</span></span>

<span data-ttu-id="23ee9-127">"홈" 키를 사용 하도록 설정 하는 방법을 보려면 [IoT Shell 페이지](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoreshell#switching-between-apps-with-hid-injection-keys) 를 방문 하세요.</span><span class="sxs-lookup"><span data-stu-id="23ee9-127">To see how to enable the "Home" key, please visit our [IoT Shell page](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoreshell#switching-between-apps-with-hid-injection-keys)</span></span>
