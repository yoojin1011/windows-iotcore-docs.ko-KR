---
title: 앱을 클라우드에 연결
ms.date: 08/28/2017
ms.topic: article
description: 앱을 클라우드에 연결 하는 방법에 대해 알아봅니다.
keywords: windows iot, 클라우드, Azure, Azure IoT Hub
ms.openlocfilehash: 281befbbbe5b71dece9b2bc139be1564f5c24a98
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918403"
---
# <a name="connect-your-app-to-the-cloud"></a><span data-ttu-id="7eca7-104">앱을 클라우드에 연결</span><span class="sxs-lookup"><span data-stu-id="7eca7-104">Connect your app to the cloud</span></span>

<span data-ttu-id="7eca7-105">이 단계별 가이드에서는 Windows 10 IoT Core를 숙지 하 고, 장치를 설정 하 고, Azure IoT Hub에 연결 하는 첫 번째 응용 프로그램을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7eca7-105">This step-by-step guide will allow you to familiarize yourself with Windows 10 IoT Core, set up your device and create your first application that connects to Azure IoT Hub.</span></span>

## <a name="step-1-prepare-your-device"></a><span data-ttu-id="7eca7-106">1 단계: 장치 준비</span><span class="sxs-lookup"><span data-stu-id="7eca7-106">Step 1: Prepare your device</span></span>

<span data-ttu-id="7eca7-107">[시작 페이지](https://developer.microsoft.com/en-us/windows/iot/getstarted) 에서 장치를 준비 하는 방법에 대 한 지침을 확인 하 여 [장치의 TPM을 프로 비전](../connect-to-cloud/ConnectDeviceToCloud.md) 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7eca7-107">You can find instructions on how to prepare your device on the [Get Started Page](https://developer.microsoft.com/en-us/windows/iot/getstarted) Make sure you [provision the TPM of your device](../connect-to-cloud/ConnectDeviceToCloud.md)</span></span>

## <a name="step-2-install-visual-studio-2017-and-tools"></a><span data-ttu-id="7eca7-108">2 단계: Visual Studio 2017 및 도구 설치</span><span class="sxs-lookup"><span data-stu-id="7eca7-108">Step 2: Install Visual Studio 2017 and tools</span></span>

<span data-ttu-id="7eca7-109">[Visual Studio 2017](https://go.microsoft.com/fwlink/?linkid=845271)을 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="7eca7-109">Install [Visual Studio 2017](https://go.microsoft.com/fwlink/?linkid=845271).</span></span> <span data-ttu-id="7eca7-110">무료 Community edition을 포함 하 여 모든 버전의 Visual Studio를 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7eca7-110">You can install any edition of Visual Studio, including the free Community edition.</span></span>

<span data-ttu-id="7eca7-111">Windows 10 앱을 작성 하는 데 필요한 구성 요소인 **유니버설 Windows 앱 개발 도구**를 선택 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7eca7-111">Make sure to select the **Universal Windows App Development Tools**, the component required for writing apps Windows 10:</span></span>

![유니버설 Windows 앱 개발 도구](../media/ConnectAppToCloud/install_tools_for_windows10.png)

## <a name="step-3-install-the-connected-services-for-azure-iot-hub"></a><span data-ttu-id="7eca7-113">3 단계: Azure IoT Hub에 대 한 연결된 서비스 설치</span><span class="sxs-lookup"><span data-stu-id="7eca7-113">Step 3: Install the Connected Services for Azure IoT Hub</span></span>

<span data-ttu-id="7eca7-114">Visual Studio 확장 Azure IoT Hub에 대 한 연결된 서비스를 사용 하 여 1 분 이내에 Azure IoT Hub와 상호 작용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7eca7-114">The Connected Services for Azure IoT Hub Visual Studio extension allows you to connect and start interacting with Azure IoT Hub in less than a minute.</span></span>

<span data-ttu-id="7eca7-115">[VS 갤러리](https://aka.ms/azure-iot-hub-vs-2017-cs-vs-gallery)에서 확장을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7eca7-115">You can install the extension from the [VS Gallery](https://aka.ms/azure-iot-hub-vs-2017-cs-vs-gallery).</span></span>

## <a name="step-4-create-a-visual-studio-uwp-solution"></a><span data-ttu-id="7eca7-116">4 단계: Visual Studio UWP 솔루션 만들기</span><span class="sxs-lookup"><span data-stu-id="7eca7-116">Step 4: Create a Visual Studio UWP solution</span></span>

<span data-ttu-id="7eca7-117">Visual Studio에서 UWP 솔루션을 만들려면 **파일** 메뉴에서 **새로 만들기** , **프로젝트**를 차례로 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7eca7-117">To create a UWP solution in Visual Studio, on the **File** menu, click **New** then **Project**:</span></span>

![새 프로젝트 만들기](../media/ConnectAppToCloud/new_project_menu.png)

<span data-ttu-id="7eca7-119">새 프로젝트 대화 상자에서 **비어 있는 앱 (유니버설 Windows) 시각적 개체 C#** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="7eca7-119">In the New Project dialog that comes up, select **Blank App (Universal Windows) Visual C#**.</span></span> <span data-ttu-id="7eca7-120">프로젝트에 이름 지정 (예:</span><span class="sxs-lookup"><span data-stu-id="7eca7-120">Give your project a name (e.x.</span></span> <span data-ttu-id="7eca7-121">**MyFirstIoTCoreApp**):</span><span class="sxs-lookup"><span data-stu-id="7eca7-121">**MyFirstIoTCoreApp**):</span></span>

![새 솔루션 대화 상자](../media/ConnectAppToCloud/new_solution.png)

## <a name="use-the-connected-services-for-azure-iot-hub-to-connect-to-azure-iot-hub"></a><span data-ttu-id="7eca7-123">Azure IoT Hub에 대 한 연결된 서비스를 사용 하 여 Azure IoT Hub에 연결</span><span class="sxs-lookup"><span data-stu-id="7eca7-123">Use the Connected Services for Azure IoT Hub to connect to Azure IoT Hub</span></span>

<span data-ttu-id="7eca7-124">[연결된 서비스 도구의](https://aka.ms/azure-iot-hub-vs-2017-cs-vs-gallery) 지침에 따라 프로젝트를 Azure IoT Hub에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="7eca7-124">Follow the instructions from the [Connected Services tool](https://aka.ms/azure-iot-hub-vs-2017-cs-vs-gallery) to connect your project to Azure IoT Hub.</span></span> <span data-ttu-id="7eca7-125">이 도구는 앱의 어디에서 나 호출할 수 있는 `SendDeviceToCloudMessageAsync` 및 `ReceiveCloudToDeviceMessageAsync`의 두 함수를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="7eca7-125">The tool will generate two functions, `SendDeviceToCloudMessageAsync` and `ReceiveCloudToDeviceMessageAsync` that you can invoke anywhere in your app.</span></span> <span data-ttu-id="7eca7-126">이러한 함수는 적합 한 것 처럼 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7eca7-126">You can modify these functions as you see fit.</span></span>  

