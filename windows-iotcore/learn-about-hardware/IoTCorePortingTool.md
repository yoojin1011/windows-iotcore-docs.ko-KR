---
title: Windows 10 IoT Core API 포팅 도구
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Windows 10 IoT Core API 포팅 도구를 사용 하 여 포팅 비용을 예측 하는 방법을 알아봅니다.
keywords: windows iot, API 포팅 도구, API 포팅, 이진 파일
ms.openlocfilehash: 56ca0d57752f000bf9e908fd32f514c3ae3264e5
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "60169631"
---
# <a name="windows-10-iot-core-api-porting-tool"></a><span data-ttu-id="505de-104">Windows 10 IoT Core API 포팅 도구</span><span class="sxs-lookup"><span data-stu-id="505de-104">Windows 10 IoT Core API Porting Tool</span></span>

<span data-ttu-id="505de-105">Windows 10 IoT Core는 다양 한 이전 버전의 Windows에서 사용할 수 있는 Win32 및 .Net API 노출 영역의 하위 집합만 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="505de-105">Windows 10 IoT Core only supports a subset of the Win32 and .Net API surface area available on various prior versions of Windows.</span></span> <span data-ttu-id="505de-106">이 도구는 이진 파일을 검사 하 고 이러한 이진 파일이 사용 되지 않는 Api에 대 한 보고서를 제공 하며 가능한 대체 항목에 대 한 제안을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="505de-106">This tool will scan your binaries and give you a report of the APIs these binaries use that aren't available and give suggestions for possible replacements.</span></span> <span data-ttu-id="505de-107">이를 통해 IoT 코어에 대 한 포트의 비용을 예측 하 고이에 따라 도움을 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="505de-107">This will both help with estimating the cost of a port to IoT Core as well as help you along the way.</span></span>


## <a name="usage"></a><span data-ttu-id="505de-108">사용법</span><span class="sxs-lookup"><span data-stu-id="505de-108">Usage</span></span>

<span data-ttu-id="505de-109">Windows 10 IoT Core API 포팅 도구는 [ms-iot/iot 유틸리티](https://github.com/ms-iot/iot-utilities) github 리포지토리에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="505de-109">The Windows 10 IoT Core API Porting Tool can be found in the [ms-iot/iot-utilities](https://github.com/ms-iot/iot-utilities) github repository.</span></span>  <span data-ttu-id="505de-110">[리포지토리 zip](https://github.com/ms-iot/iot-utilities/archive/master.zip) 을 다운로드 하 고 IoTAPIPortingTool 폴더를 로컬 컴퓨터에 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="505de-110">Download the [repository zip](https://github.com/ms-iot/iot-utilities/archive/master.zip) and copy the IoTAPIPortingTool folder to your local machine.</span></span>  <span data-ttu-id="505de-111">Visual Studio 2017에서 **Iotapiportingtool .sln** 을 열고 프로젝트를 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="505de-111">Open **IoTAPIPortingTool.sln** in Visual Studio 2017 and build the project.</span></span>  <span data-ttu-id="505de-112">그러면이 생성 `IotAPIPortingTool.exe`됩니다.</span><span class="sxs-lookup"><span data-stu-id="505de-112">This will generate `IotAPIPortingTool.exe`.</span></span>

<span data-ttu-id="505de-113">을 실행 `IoTAPIPortingTool.exe <Application path> [-os]`하 여 도구를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="505de-113">You can use the tool by running `IoTAPIPortingTool.exe <Application path> [-os]`.</span></span>

*  <span data-ttu-id="505de-114">`<Application path>`포팅 도구를 사용 하는 응용 프로그램의 exe</span><span class="sxs-lookup"><span data-stu-id="505de-114">`<Application path>` exe of application that porting tool is used for</span></span>

*  <span data-ttu-id="505de-115">`-os`UWP를 사용 하지 않으려는 경우에는를 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="505de-115">`-os` should be specified if you are not planning to use UWP.</span></span>  <span data-ttu-id="505de-116">기본적으로이 도구는 Windows UWP 플랫폼에 대해 이진 파일의 유효성을 검사 합니다.</span><span class="sxs-lookup"><span data-stu-id="505de-116">By default, the tool validates your binaries against the Windows UWP platform.</span></span>

> [!NOTE] 
> <span data-ttu-id="505de-117">Visual Studio 개발자 명령 프롬프트에서 IoTAPIPortingTool .exe를 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="505de-117">IoTAPIPortingTool.exe must be run from a Visual Studio Developer Command Prompt.</span></span> <span data-ttu-id="505de-118">IotAPIPortingTool .exe를 포함 하는 폴더로 이동 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="505de-118">You need to navigate to the folder that contains the IotAPIPortingTool.exe.</span></span> 

        Sample command: C:\IoTAPIPortingTool\bin\Debug>IoTAPIPortingTool.exe C:\Sample\Sample.exe -os 

## <a name="output"></a><span data-ttu-id="505de-119">출력</span><span class="sxs-lookup"><span data-stu-id="505de-119">Output</span></span>

<span data-ttu-id="505de-120">이 도구는를 `IotAPIPortingTool.exe`포함 하는 동일한 폴더에서 csv (쉼표로 구분 된 값) 파일을 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="505de-120">The tool will generate a comma separated values (csv) file in same folder that contains the `IotAPIPortingTool.exe`.</span></span> <span data-ttu-id="505de-121">파일의 이름은로 `IoTAPIPortingTool.csv` 지정 되 고 `IoTAPIPortingToolOS.csv` ,-os가 지정 된 경우에는 명령줄에 요약이 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="505de-121">The file is named `IoTAPIPortingTool.csv` (or, `IoTAPIPortingToolOS.csv` if -os is specified) and a summary will be on the command line.</span></span> <span data-ttu-id="505de-122">Excel에서 `.csv` 파일을 열어 전체 출력을 분석 합니다.</span><span class="sxs-lookup"><span data-stu-id="505de-122">Open the `.csv` file in Excel to analyze the complete output.</span></span>
