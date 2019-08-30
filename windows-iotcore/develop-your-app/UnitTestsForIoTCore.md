---
title: 단위 테스트 만들기
author: bfjelds
ms.author: bfjelds
ms.date: 10/08/2018
ms.topic: article
description: IoT Core에서 지 원하는 단위 테스트에 대해 알아봅니다.
keywords: windows iot, 단위 테스트, UWP
ms.openlocfilehash: 0a54ad7ffa3065353045f0e2f81306a1a1e0ac13
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "60169331"
---
# <a name="developing-unit-tests"></a><span data-ttu-id="2658a-104">단위 테스트 개발</span><span class="sxs-lookup"><span data-stu-id="2658a-104">Developing unit tests</span></span>
<span data-ttu-id="2658a-105">Windows 10 IoT Core에서 지원 되는 UWP 단위 테스트에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="2658a-105">Learn about UWP unit testing supported on Windows 10 IoT Core.</span></span>

## <a name="uwp-unit-tests"></a><span data-ttu-id="2658a-106">UWP 단위 테스트</span><span class="sxs-lookup"><span data-stu-id="2658a-106">UWP Unit Tests</span></span>
___

<span data-ttu-id="2658a-107">단위 테스트는 앱 개발자를 위한 중요 한 보호 및 유효성 검사를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="2658a-107">Unit tests provide vital protection and validation for app developers.</span></span>  <span data-ttu-id="2658a-108">Visual Studio 15.6에는 새로운 테스트 플랫폼에서 Windows 10 IoT Core에 대 한 지원이 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="2658a-108">Visual Studio 15.6 added support for Windows 10 IoT Core in its new test platform.</span></span>  <span data-ttu-id="2658a-109">이 새로운 지원을 통해 연속 통합 빌드의 일부로 실행 하거나 Visual Studio에서 직접 실행할 수 있는 UWP 기능에 대 한 단위 테스트를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2658a-109">With this new support, it is possible to create unit tests for UWP functionality that can execute as part of a Continuous Integration build or directly from Visual Studio.</span></span>


### <a name="create-new-unit-test-project"></a><span data-ttu-id="2658a-110">새 단위 테스트 프로젝트 만들기</span><span class="sxs-lookup"><span data-stu-id="2658a-110">Create new unit test project</span></span>
___

1. <span data-ttu-id="2658a-111">Visual Studio를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="2658a-111">Open Visual Studio</span></span>

2. <span data-ttu-id="2658a-112">새 단위 테스트 프로젝트 ![만들기 앱 설치](../media/UnitTests/newproject.png)</span><span class="sxs-lookup"><span data-stu-id="2658a-112">Create a new unit test project ![Install App](../media/UnitTests/newproject.png)</span></span>

3. <span data-ttu-id="2658a-113">테스트 코드를 포함 하도록 UnitTest.cs를 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="2658a-113">Update UnitTest.cs to include your test code</span></span>
   ```C#
   namespace UnitTestProject1
   {
    [TestClass]
    public class UnitTest1
    {
        [TestMethod]
        public void TestMethod1()
        {
            // test code here
        }
    }
   }
   ```


### <a name="remotely-run-unit-test-on-windows-10-iot-core-device"></a><span data-ttu-id="2658a-114">Windows 10 IoT Core 장치에서 단위 테스트 원격 실행</span><span class="sxs-lookup"><span data-stu-id="2658a-114">Remotely run unit test on Windows 10 IoT Core device</span></span>
___

1. <span data-ttu-id="2658a-115">Visual Studio 테스트 탐색기 (테스트 > Windows > 테스트 탐색기)를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="2658a-115">Open the Visual Studio Test Explorer (Test > Windows > Test Explorer).</span></span>
 <span data-ttu-id="2658a-116">![테스트 탐색기](../media/UnitTests/show-test-explorer.png)</span><span class="sxs-lookup"><span data-stu-id="2658a-116">![Test Explorer](../media/UnitTests/show-test-explorer.png)</span></span>

1. <span data-ttu-id="2658a-117">테스트 배포가 작동 하려면 UWP 앱을 구성 하는 것과 같은 방식으로 프로젝트를 구성 해야 합니다 (특히 유니버설 인증 및 원격 컴퓨터 사용).</span><span class="sxs-lookup"><span data-stu-id="2658a-117">For test deployment to work, your project must be configured in the same way UWP apps are configured (specifically using Universal Authentication and Remote Machine).</span></span>  <span data-ttu-id="2658a-118">자세한 내용은 [Visual Studio를 사용 하 여 앱 배포](../develop-your-app/appdeployment.md) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="2658a-118">See [Deploy an App with Visual Studio](../develop-your-app/appdeployment.md) for specifics.</span></span>

1. <span data-ttu-id="2658a-119">단위 테스트를 원격으로 실행 하려면 테스트 탐색기를 사용 하 고 원하는 TestMethod를 마우스 오른쪽 단추로 클릭 한 다음 선택한 테스트 ![실행/디버그 테스트 탐색기를 선택 합니다.](../media/UnitTests/test-explorer.png)</span><span class="sxs-lookup"><span data-stu-id="2658a-119">To remotely run a unit test, you can use the Test Explorer and right clicking the desired TestMethod and selecting Run/Debug Selected Tests ![Test Explorer](../media/UnitTests/test-explorer.png)</span></span>

1. <span data-ttu-id="2658a-120">모든 단위 테스트를 원격으로 실행 하거나 디버그 하기 위해 테스트 > 실행 또는 테스트 > ![테스트 탐색기](../media/UnitTests/run-tests.png)
 ![테스트 탐색기를 사용 하 여 테스트를 수행할 수 있습니다.](../media/UnitTests/debug-tests.png)</span><span class="sxs-lookup"><span data-stu-id="2658a-120">To remotely run or debug all unit tests, you can use Test > Run or Test > Debug ![Test Explorer](../media/UnitTests/run-tests.png)
 ![Test Explorer](../media/UnitTests/debug-tests.png)</span></span>
   

### <a name="configure-unit-tests-as-part-of-a-continuous-integration-build"></a><span data-ttu-id="2658a-121">연속 통합 빌드의 일부로 단위 테스트 구성</span><span class="sxs-lookup"><span data-stu-id="2658a-121">Configure unit tests as part of a Continuous Integration build</span></span>
___

<span data-ttu-id="2658a-122">Visual Studio 팀은 Windows 10 IoT Core 단위 테스트를 VSTS 빌드에 통합 하는 방법을 보여 주는 유용한 블로그 게시물을 만들었습니다. [Win10 IoT Core, UWP 및 VSTS를 사용 하는 IoT 용 DevOps](https://blogs.msdn.microsoft.com/devops/2018/03/07/devops-for-iot-with-win10-iot-core-uwp-and-vsts/)</span><span class="sxs-lookup"><span data-stu-id="2658a-122">The Visual Studio team has created a great blog post showing how to incorporate Windows 10 IoT Core unit tests into a VSTS build: [DevOps for IoT with Win10 IoT Core, UWP, and VSTS](https://blogs.msdn.microsoft.com/devops/2018/03/07/devops-for-iot-with-win10-iot-core-uwp-and-vsts/)</span></span>

