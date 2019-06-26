---
title: 디바이스용 앱 개발
author: saraclay
ms.author: saclayt
ms.date: 04/17/2018
ms.topic: article
description: 디바이스용 앱을 추가 및 개발하는 방법 알아보기
keywords: Windows 10 IoT Core, 시작, 앱 개발, 앱
ms.openlocfilehash: f5ee15c2115d6e10a2a8ade1522c7b66cf788bee
ms.sourcegitcommit: 9ec4716afde25fdc8b94f7c0794448501f451b55
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/17/2019
ms.locfileid: "60170103"
---
# <a name="develop-an-app-for-your-device"></a><span data-ttu-id="760c5-104">디바이스용 앱 개발</span><span class="sxs-lookup"><span data-stu-id="760c5-104">Develop an app for your device</span></span>

> [!NOTE]
> <span data-ttu-id="760c5-105">Visual Studio에서 액세스할 수 있는 RS4 이상의 SDK를 설치하지 않으면 RS5(또는 OpenSSH를 사용하는 RS4) IoT 이미지에 배포할 때 Visual Studio가 암호화 오류를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="760c5-105">Visual Studio will generate a cryptic error when deploying to a RS5 (or RS4 with OpenSSH enabled) IoT image unless a SDK from RS4 or greater is installed that Visual Studio can access.</span></span>

<span data-ttu-id="760c5-106">디바이스가 정상 작동하고 기본 앱이 실행 중이므로, 이제 앱을 개발하고 디바이스에 배포하여 디바이스의 활용도를 높일 차례입니다.</span><span class="sxs-lookup"><span data-stu-id="760c5-106">Now that you have a working device with the default app running, you'll want to take your device to the next level by developing and deploying an app on your device.</span></span> <span data-ttu-id="760c5-107">샘플을 살펴보기 전에, 애플리케이션 개발에 사용할 [Visual Studio 2017](https://www.visualstudio.com/downloads/)을 다운로드해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="760c5-107">Before diving into samples, you'll need to download [Visual Studio 2017](https://www.visualstudio.com/downloads/) for application development.</span></span>

<span data-ttu-id="760c5-108">프로젝트에 C++를 사용할 계획인 경우 Visual Studio 2017을 다운로드할 때 아래 예제와 동일한 방식으로 확인란을 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="760c5-108">If you're planning to use C++ for your projects, when downloading Visual Studio 2017, make sure to check the boxes the same way as they are in the example below:</span></span>

![C++ 및 Windows 10 IoT를 위한 Essentials](../../media/DevelopApp/VS-CPP.jpg)

<span data-ttu-id="760c5-110">향후 백그라운드, Arduino 유선 또는 콘솔 애플리케이션 개발에 관심이 있는 경우 [Visual Studio 갤러리](https://marketplace.visualstudio.com/items?itemName=MicrosoftIoT.WindowsIoTCoreProjectTemplatesforVS15)에서 프로젝트 템플릿도 다운로드하세요.</span><span class="sxs-lookup"><span data-stu-id="760c5-110">If you're interested in developing background, Arduino Wiring or console applications in the future, you'll also want to download project templates from the [Visual Studio Gallery](https://marketplace.visualstudio.com/items?itemName=MicrosoftIoT.WindowsIoTCoreProjectTemplatesforVS15).</span></span>


<span data-ttu-id="760c5-111">앱을 실행하려면 아래의 추천 스타터 샘플로 시작하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="760c5-111">To get up and running with an app, we recommend starting with a suggested starter sample below.</span></span> <span data-ttu-id="760c5-112">하지만 고유의 앱을 배포할 준비가 완료된 분들을 위해 이후 섹션에 유용한 링크를 준비해 두었습니다.</span><span class="sxs-lookup"><span data-stu-id="760c5-112">But if you're ready to deploy your own app, we've also provided helpful links in the section after.</span></span>

## <a name="suggested-starter-samples"></a><span data-ttu-id="760c5-113">추천 스타터 샘플</span><span class="sxs-lookup"><span data-stu-id="760c5-113">Suggested starter samples</span></span>

* [<span data-ttu-id="760c5-114">Hello Blinky</span><span class="sxs-lookup"><span data-stu-id="760c5-114">Hello Blinky</span></span>](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/HelloBlinky)
* [<span data-ttu-id="760c5-115">Hello World</span><span class="sxs-lookup"><span data-stu-id="760c5-115">Hello World</span></span>](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/HelloWorld)
* [<span data-ttu-id="760c5-116">IoT 시작 앱 샘플</span><span class="sxs-lookup"><span data-stu-id="760c5-116">IoT Startup App sample</span></span>](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/IoTStartApp)
* [<span data-ttu-id="760c5-117">RPi Cognitive Service 샘플</span><span class="sxs-lookup"><span data-stu-id="760c5-117">RPi Cognitive Service sample</span></span>](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/RPiCognitiveService) 



<span data-ttu-id="760c5-118">앱을 배포하셨으니, 이 빠른 시작을 모두 마쳤습니다!</span><span class="sxs-lookup"><span data-stu-id="760c5-118">Once you've deployed your app - congratulations, you've finished this quickstarter!</span></span> <span data-ttu-id="760c5-119">계속 둘러보셔도 되고, 아이디어가 떠오르는 분들은 Windows 10 IoT를 이용한 상용화 설명서를 확인해 보세요.</span><span class="sxs-lookup"><span data-stu-id="760c5-119">Continue to play around or, if you have a few ideas bouncing around in your head, check out our documentation on commercializing with Windows 10 IoT.</span></span> 

## <a name="app-development-resources"></a><span data-ttu-id="760c5-120">앱 개발 리소스</span><span class="sxs-lookup"><span data-stu-id="760c5-120">App development resources</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="760c5-121">항목</span><span class="sxs-lookup"><span data-stu-id="760c5-121">Topic</span></span></th>
<th align="left"><span data-ttu-id="760c5-122">설명</span><span class="sxs-lookup"><span data-stu-id="760c5-122">Description</span></span></th>
</tr>
</thead>
<tbody>

<tr class="odd">
<td align="left"><p><span data-ttu-id="760c5-123"><a href="../../develop-your-app/buildingappsforiotcore.md" data-raw-source="[Developing foreground applications](../../develop-your-app/buildingappsforiotcore.md)">포그라운드 애플리케이션 개발</a></span><span class="sxs-lookup"><span data-stu-id="760c5-123"><a href="../../develop-your-app/buildingappsforiotcore.md" data-raw-source="[Developing foreground applications](../../develop-your-app/buildingappsforiotcore.md)">Developing foreground applications</a></span></span></p></td>
<td align="left"><p><span data-ttu-id="760c5-124">Windows 10 IoT Core에서 지원되는 다양한 언어와 지원되는 UWP 및 비 UWP 앱 형식에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="760c5-124">Learn about the different languages that are supported on Windows 10 IoT Core as well as the UWP and non-UWP app types that are supported.</span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><p><span data-ttu-id="760c5-125"><a href="../../develop-your-app/backgroundapplications.md" data-raw-source="[Developing background applications](../../develop-your-app/backgroundapplications.md)">백그라운드 애플리케이션 개발</a></span><span class="sxs-lookup"><span data-stu-id="760c5-125"><a href="../../develop-your-app/backgroundapplications.md" data-raw-source="[Developing background applications](../../develop-your-app/backgroundapplications.md)">Developing background applications</a></span></span></p></td>
<td align="left"><p><span data-ttu-id="760c5-126">Windows 10 IoT Core에서 지원되는 다양한 언어와 지원되는 UWP 및 비 UWP 앱 형식에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="760c5-126">Learn about the different languages that are supported on Windows 10 IoT Core as well as the UWP and non-UWP app types that are supported.</span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><p><span data-ttu-id="760c5-127"><a href="../../develop-your-app/appdeployment.md" data-raw-source="[Deploy an App with Visual Studio](../../develop-your-app/appdeployment.md)">Visual Studio를 사용하여 앱 개발</a></span><span class="sxs-lookup"><span data-stu-id="760c5-127"><a href="../../develop-your-app/appdeployment.md" data-raw-source="[Deploy an App with Visual Studio](../../develop-your-app/appdeployment.md)">Deploy an App with Visual Studio</a></span></span></p></td>
<td align="left"><p><span data-ttu-id="760c5-128">Visual Studio를 사용하여 Windows 10 IoT Core 디바이스에 다양한 앱을 배포하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="760c5-128">Learn how to deploy your different apps with Visual Studio to your Windows 10 IoT Core device.</span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><p><span data-ttu-id="760c5-129"><a href="../../develop-your-app/remotedebugging.md" data-raw-source="[Debug your app using Remote Console App Debugging](../../develop-your-app/remotedebugging.md)">원격 콘솔 앱 디버깅을 사용하여 앱 디버그</a></span><span class="sxs-lookup"><span data-stu-id="760c5-129"><a href="../../develop-your-app/remotedebugging.md" data-raw-source="[Debug your app using Remote Console App Debugging](../../develop-your-app/remotedebugging.md)">Debug your app using Remote Console App Debugging</a></span></span></p></td>
<td align="left"><p><span data-ttu-id="760c5-130">Visual Studio에서 원격 콘솔 앱 디버깅을 사용하여 앱을 디버그하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="760c5-130">Learn how to debug your apps using Remote Console App Debugging in Visual Studio.</span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><p><span data-ttu-id="760c5-131"><a href="../../develop-your-app/appinstaller.md" data-raw-source="[Install your app on your Windows 10 IoT Core device](../../develop-your-app/appinstaller.md)">Windows 10 IoT Core 디바이스에 앱 설치</a></span><span class="sxs-lookup"><span data-stu-id="760c5-131"><a href="../../develop-your-app/appinstaller.md" data-raw-source="[Install your app on your Windows 10 IoT Core device](../../develop-your-app/appinstaller.md)">Install your app on your Windows 10 IoT Core device</a></span></span></p></td>
<td align="left"><p><span data-ttu-id="760c5-132">Windows 10 IoT Core 디바이스에 앱을 설치하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="760c5-132">Learn how to install your app to your Windows 10 IoT Core device.</span></span></p></td>
</tr>

</tbody>
</table>
