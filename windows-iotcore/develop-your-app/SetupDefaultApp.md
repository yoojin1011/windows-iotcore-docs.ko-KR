---
title: 기본 앱 설정
author: bfjelds
ms.author: bfjelds
ms.date: 09/05/17
ms.topic: article
description: Windows Device Portal 이나 셸을 사용 하 여 기본 앱을 설정 하는 방법에 알아봅니다.
keywords: windows iot, 기본 앱, PowerShell, iot
ms.openlocfilehash: f3f7a5194491250a8a0b49e81e073282c8f5660b
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513325"
---
# <a name="setup-a-default-app"></a><span data-ttu-id="11521-104">기본 앱 설정</span><span class="sxs-lookup"><span data-stu-id="11521-104">Setup a default app</span></span>
<span data-ttu-id="11521-105">여기에 기본 응용 프로그램으로 응용 프로그램을 설정 하는 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="11521-105">Here you'll learn the ways to set your application as the default application.</span></span> <span data-ttu-id="11521-106">기본 응용 프로그램 시스템을 부팅할 때 실행 되는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="11521-106">The default application is the one that is launched when the system boots.</span></span>  

> [!NOTE]
> <span data-ttu-id="11521-107">Visual Studio는 RS5를 배포 하는 경우 암호화 오류가 생성 됩니다 (또는 RS4 OpenSSH 사용 하 여 사용 하도록 설정) IoT 이미지에서 RS4 이상 SDK는 Visual Studio에 액세스할 수 있도록 설치 되어 있지 않으면입니다.</span><span class="sxs-lookup"><span data-stu-id="11521-107">Visual Studio will generate a cryptic error when deploying to a RS5 (or RS4 with OpenSSH enabled) IoT image unless a SDK from RS4 or greater is installed that Visual Studio can access.</span></span>

## <a name="runtime-options"></a><span data-ttu-id="11521-108">런타임 옵션</span><span class="sxs-lookup"><span data-stu-id="11521-108">Runtime options</span></span>

<span data-ttu-id="11521-109">개발 중 / 실험적 단계로 다음과 같은 방법으로 기본 앱을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11521-109">During development / experimental phases, you can change the default app by following means.</span></span>

### <a name="using-windows-device-portal"></a><span data-ttu-id="11521-110">Windows Device Portal 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="11521-110">Using Windows Device Portal</span></span>

<span data-ttu-id="11521-111">클릭할 수 있습니다 **시작** 앱에 해당 하는 열입니다.</span><span class="sxs-lookup"><span data-stu-id="11521-111">You can click on **Startup** column corresponding to the app.</span></span>
![SetupDefaultAppWDP](../media/SetupDefaultApp/DefaultAppWDP.png)

### <a name="using-the-shell"></a><span data-ttu-id="11521-113">셸 사용</span><span class="sxs-lookup"><span data-stu-id="11521-113">Using the shell</span></span>

<span data-ttu-id="11521-114">셸을 사용 하 여 기본 앱을 설정 하는 단계</span><span class="sxs-lookup"><span data-stu-id="11521-114">Steps to set the default app using the shell</span></span> 

1. <span data-ttu-id="11521-115">통해 장치를 연결할 [Powershell](../connect-your-device/PowerShell.md)</span><span class="sxs-lookup"><span data-stu-id="11521-115">Connect to the device via [Powershell](../connect-your-device/PowerShell.md)</span></span>

2. <span data-ttu-id="11521-116">사용 하 여 설치할 응용 프로그램 나열</span><span class="sxs-lookup"><span data-stu-id="11521-116">List the applications installed using</span></span> `iotstartup list`

3. <span data-ttu-id="11521-117">기본적으로 확인 하 여 설정 하려는 응용 프로그램에 대 한 appid 참고 `iotstartup add headed <appid>`합니다.</span><span class="sxs-lookup"><span data-stu-id="11521-117">Note the appid for the application you want to make as default and set it using `iotstartup add headed <appid>`.</span></span> <span data-ttu-id="11521-118">헤드리스 앱에 대 한 사용할지 `iotstartup add headless <appid>`합니다.</span><span class="sxs-lookup"><span data-stu-id="11521-118">For headless app, you should use `iotstartup add headless <appid>`.</span></span>


## <a name="build-time-option"></a><span data-ttu-id="11521-119">빌드 시간 옵션</span><span class="sxs-lookup"><span data-stu-id="11521-119">Build time option</span></span>

<span data-ttu-id="11521-120">대규모 배포를 수행 하면 프로 비전 패키지를 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="11521-120">For large deployments, you can achieve this using provisioning package</span></span>

<span data-ttu-id="11521-121">프로 비전 패키지를 만드는 동안 StartupApp/기본 설정 된 WCD에서 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11521-121">You can specify the StartupApp/Default setting in the WCD during the provisioning package creation.</span></span>
![SetupDefaultAppICD](../media/SetupDefaultApp/DefaultAppICD.png)

<span data-ttu-id="11521-123">참조 [Appx.IoTCoreDefaultApp](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Packages/Appx.IoTCoreDefaultApp/customizations.xml) 예입니다.</span><span class="sxs-lookup"><span data-stu-id="11521-123">See [Appx.IoTCoreDefaultApp](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Packages/Appx.IoTCoreDefaultApp/customizations.xml) as an example.</span></span> <span data-ttu-id="11521-124">응용 프로그램 사용자 모델 ID ()의 AUMID를 사용 하 여 appx를 가져올 수 있습니다 [GetAppxInfo 도구](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools/GetAppxInfo.exe)합니다.</span><span class="sxs-lookup"><span data-stu-id="11521-124">You can get the Application User Model ID (AUMID) of an appx using [GetAppxInfo tool](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools/GetAppxInfo.exe).</span></span>

## <a name="how-to-configure-home-key"></a><span data-ttu-id="11521-125">"홈" 키를 구성 하는 방법</span><span class="sxs-lookup"><span data-stu-id="11521-125">How to configure "Home" key</span></span>

<span data-ttu-id="11521-126">Windows 10 IoT 1 주년 업데이트 (1607) 다른 응용 프로그램에서 현재 실행 중인 경우 기본 응용 프로그램 창을 전경으로 가져오는 셸 지원을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="11521-126">Windows 10 IoT Anniversary Update (1607) provides shell support for bringing the default application window to the foreground when another application is currently running.</span></span>

<span data-ttu-id="11521-127">를 "홈" 키를 사용 하는 방법을 보려면 알아보려면 우리의 [IoT 셸 페이지](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoreshell#switching-between-apps-with-hid-injection-keys)</span><span class="sxs-lookup"><span data-stu-id="11521-127">To see how to enable the "Home" key, please visit our [IoT Shell page](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoreshell#switching-between-apps-with-hid-injection-keys)</span></span>
