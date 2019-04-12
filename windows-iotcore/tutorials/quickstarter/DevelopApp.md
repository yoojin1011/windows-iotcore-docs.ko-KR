---
title: 장치에 대 한 앱 개발
author: saraclay
ms.author: saclayt
ms.date: 04/17/2018
ms.topic: article
description: 추가 하 고 장치에 앱을 개발 하는 방법 알아보기
keywords: Windows 10 IoT Core, 시작, 앱, 앱 개발
ms.openlocfilehash: f5ee15c2115d6e10a2a8ade1522c7b66cf788bee
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59515099"
---
# <a name="develop-an-app-for-your-device"></a><span data-ttu-id="2a034-104">장치에 대 한 앱 개발</span><span class="sxs-lookup"><span data-stu-id="2a034-104">Develop an app for your device</span></span>

> [!NOTE]
> <span data-ttu-id="2a034-105">Visual Studio는 RS5를 배포 하는 경우 암호화 오류가 생성 됩니다 (또는 RS4 OpenSSH 사용 하 여 사용 하도록 설정) IoT 이미지에서 RS4 이상 SDK는 Visual Studio에 액세스할 수 있도록 설치 되어 있지 않으면입니다.</span><span class="sxs-lookup"><span data-stu-id="2a034-105">Visual Studio will generate a cryptic error when deploying to a RS5 (or RS4 with OpenSSH enabled) IoT image unless a SDK from RS4 or greater is installed that Visual Studio can access.</span></span>

<span data-ttu-id="2a034-106">실행 중인 기본 앱을 사용 하 여 작업 장치를가지고 다음 수준으로 개발 하 고 장치에서 앱을 배포 하 여 장치를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a034-106">Now that you have a working device with the default app running, you'll want to take your device to the next level by developing and deploying an app on your device.</span></span> <span data-ttu-id="2a034-107">예제를 살펴 보기 전에 다운로드 해야 [Visual Studio 2017](https://www.visualstudio.com/downloads/) 응용 프로그램 개발에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a034-107">Before diving into samples, you'll need to download [Visual Studio 2017](https://www.visualstudio.com/downloads/) for application development.</span></span>

<span data-ttu-id="2a034-108">사용 하려는 경우 C++ 프로젝트의 경우 Visual Studio 2017을 다운로드 하는 경우, 아래 예제에 있는 확인란을 동일한 방식으로 선택 하도록 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a034-108">If you're planning to use C++ for your projects, when downloading Visual Studio 2017, make sure to check the boxes the same way as they are in the example below:</span></span>

![Essentials에 대 한 C++ 및 Windows 10 IoT](../../media/DevelopApp/VS-CPP.jpg)

<span data-ttu-id="2a034-110">백그라운드, Arduino 연결 또는 콘솔 응용 프로그램을 나중에 개발에 관심이 있는 경우 또한 싶어하는에서 프로젝트 템플릿을 다운로드 합니다 [Visual Studio 갤러리](https://marketplace.visualstudio.com/items?itemName=MicrosoftIoT.WindowsIoTCoreProjectTemplatesforVS15)합니다.</span><span class="sxs-lookup"><span data-stu-id="2a034-110">If you're interested in developing background, Arduino Wiring or console applications in the future, you'll also want to download project templates from the [Visual Studio Gallery](https://marketplace.visualstudio.com/items?itemName=MicrosoftIoT.WindowsIoTCoreProjectTemplatesforVS15).</span></span>


<span data-ttu-id="2a034-111">실행 중인 앱을 가져오려면 아래 제안 된 시작 샘플을 사용 하 여 시작 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="2a034-111">To get up and running with an app, we recommend starting with a suggested starter sample below.</span></span> <span data-ttu-id="2a034-112">그러나 뒤에 있는 섹션에 대 한 유용한 링크를 사용자 고유의 앱을 배포할 준비가 인 경우도 제공 했습니다.</span><span class="sxs-lookup"><span data-stu-id="2a034-112">But if you're ready to deploy your own app, we've also provided helpful links in the section after.</span></span>

## <a name="suggested-starter-samples"></a><span data-ttu-id="2a034-113">제안 된 시작 샘플</span><span class="sxs-lookup"><span data-stu-id="2a034-113">Suggested starter samples</span></span>

* [<span data-ttu-id="2a034-114">Hello 쳐다</span><span class="sxs-lookup"><span data-stu-id="2a034-114">Hello Blinky</span></span>](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/HelloBlinky)
* [<span data-ttu-id="2a034-115">Hello World</span><span class="sxs-lookup"><span data-stu-id="2a034-115">Hello World</span></span>](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/HelloWorld)
* [<span data-ttu-id="2a034-116">IoT 시작 앱 샘플</span><span class="sxs-lookup"><span data-stu-id="2a034-116">IoT Startup App sample</span></span>](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/IoTStartApp)
* [<span data-ttu-id="2a034-117">RPi Cognitive Service 샘플</span><span class="sxs-lookup"><span data-stu-id="2a034-117">RPi Cognitive Service sample</span></span>](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/RPiCognitiveService) 



<span data-ttu-id="2a034-118">축 하 하 여 앱을 배포한 후이 quickstarter를 마쳤습니다!</span><span class="sxs-lookup"><span data-stu-id="2a034-118">Once you've deployed your app - congratulations, you've finished this quickstarter!</span></span> <span data-ttu-id="2a034-119">계속 해 서, 여러분의 머릿속에 주위 반송 하는 몇 가지 아이디어를 있다면 Windows 10 IoT를 사용 하 여 상용화에서 설명서를 확인해 계속 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a034-119">Continue to play around or, if you have a few ideas bouncing around in your head, check out our documentation on commercializing with Windows 10 IoT.</span></span> 

## <a name="app-development-resources"></a><span data-ttu-id="2a034-120">앱 개발 리소스</span><span class="sxs-lookup"><span data-stu-id="2a034-120">App development resources</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="2a034-121">항목</span><span class="sxs-lookup"><span data-stu-id="2a034-121">Topic</span></span></th>
<th align="left"><span data-ttu-id="2a034-122">설명</span><span class="sxs-lookup"><span data-stu-id="2a034-122">Description</span></span></th>
</tr>
</thead>
<tbody>

<tr class="odd">
<td align="left"><p><a href="../../develop-your-app/buildingappsforiotcore.md" data-raw-source="[Developing foreground applications](../../develop-your-app/buildingappsforiotcore.md)"><span data-ttu-id="2a034-123">포그라운드 응용 프로그램 개발</span><span class="sxs-lookup"><span data-stu-id="2a034-123">Developing foreground applications</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="2a034-124">UWP 뿐만 아니라 Windows 10 IoT Core 지원 되는 다른 언어 및 지원 되는 비 UWP 앱 형식에 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="2a034-124">Learn about the different languages that are supported on Windows 10 IoT Core as well as the UWP and non-UWP app types that are supported.</span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="../../develop-your-app/backgroundapplications.md" data-raw-source="[Developing background applications](../../develop-your-app/backgroundapplications.md)"><span data-ttu-id="2a034-125">백그라운드 응용 프로그램 개발</span><span class="sxs-lookup"><span data-stu-id="2a034-125">Developing background applications</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="2a034-126">UWP 뿐만 아니라 Windows 10 IoT Core 지원 되는 다른 언어 및 지원 되는 비 UWP 앱 형식에 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="2a034-126">Learn about the different languages that are supported on Windows 10 IoT Core as well as the UWP and non-UWP app types that are supported.</span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="../../develop-your-app/appdeployment.md" data-raw-source="[Deploy an App with Visual Studio](../../develop-your-app/appdeployment.md)"><span data-ttu-id="2a034-127">Visual Studio 사용 하 여 앱 배포</span><span class="sxs-lookup"><span data-stu-id="2a034-127">Deploy an App with Visual Studio</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="2a034-128">Windows 10 IoT Core 장치에 Visual Studio를 사용 하 여 다른 앱을 배포 하는 방법에 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="2a034-128">Learn how to deploy your different apps with Visual Studio to your Windows 10 IoT Core device.</span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="../../develop-your-app/remotedebugging.md" data-raw-source="[Debug your app using Remote Console App Debugging](../../develop-your-app/remotedebugging.md)"><span data-ttu-id="2a034-129">원격 콘솔 응용 프로그램 디버깅을 사용 하 여 앱 디버그</span><span class="sxs-lookup"><span data-stu-id="2a034-129">Debug your app using Remote Console App Debugging</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="2a034-130">원격 콘솔 응용 프로그램 디버깅을 사용 하 여 Visual Studio에서 앱을 디버그 하는 방법에 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="2a034-130">Learn how to debug your apps using Remote Console App Debugging in Visual Studio.</span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="../../develop-your-app/appinstaller.md" data-raw-source="[Install your app on your Windows 10 IoT Core device](../../develop-your-app/appinstaller.md)"><span data-ttu-id="2a034-131">Windows 10 IoT Core 장치에 앱 설치</span><span class="sxs-lookup"><span data-stu-id="2a034-131">Install your app on your Windows 10 IoT Core device</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="2a034-132">Windows 10 IoT Core 장치에 앱을 설치 하는 방법에 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="2a034-132">Learn how to install your app to your Windows 10 IoT Core device.</span></span></p></td>
</tr>

</tbody>
</table>
