---
title: 단위 테스트 만들기
author: bfjelds
ms.author: bfjelds
ms.date: 10/08/2018
ms.topic: article
description: IoT Core에서 지원 되는 단위 테스트에 알아봅니다.
keywords: windows iot, 단위 테스트 UWP
ms.openlocfilehash: 0a54ad7ffa3065353045f0e2f81306a1a1e0ac13
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513349"
---
# <a name="developing-unit-tests"></a><span data-ttu-id="2a507-104">개발 단위 테스트</span><span class="sxs-lookup"><span data-stu-id="2a507-104">Developing unit tests</span></span>
<span data-ttu-id="2a507-105">Windows 10 IoT Core 지원 되는 테스트 하는 UWP 단위에 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="2a507-105">Learn about UWP unit testing supported on Windows 10 IoT Core.</span></span>

## <a name="uwp-unit-tests"></a><span data-ttu-id="2a507-106">UWP 유닛 테스트</span><span class="sxs-lookup"><span data-stu-id="2a507-106">UWP Unit Tests</span></span>
___

<span data-ttu-id="2a507-107">단위 테스트는 중요 한 보호 및 앱 개발자를 위한 유효성 검사를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="2a507-107">Unit tests provide vital protection and validation for app developers.</span></span>  <span data-ttu-id="2a507-108">Visual Studio 15.6의 새 테스트 플랫폼의 Windows 10 IoT Core 대 한 지원 추가.</span><span class="sxs-lookup"><span data-stu-id="2a507-108">Visual Studio 15.6 added support for Windows 10 IoT Core in its new test platform.</span></span>  <span data-ttu-id="2a507-109">이 새로운 지원을 통해 Visual Studio에서 직접 또는 지속적인 통합 빌드의 일부로 실행할 수 있는 UWP 기능에 대 한 단위 테스트를 만들 수는 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a507-109">With this new support, it is possible to create unit tests for UWP functionality that can execute as part of a Continuous Integration build or directly from Visual Studio.</span></span>


### <a name="create-new-unit-test-project"></a><span data-ttu-id="2a507-110">새 단위 테스트 프로젝트 만들기</span><span class="sxs-lookup"><span data-stu-id="2a507-110">Create new unit test project</span></span>
___

1. <span data-ttu-id="2a507-111">Visual Studio를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="2a507-111">Open Visual Studio</span></span>

2. <span data-ttu-id="2a507-112">새 단위 테스트 프로젝트 만들기 ![앱 설치](../media/UnitTests/newproject.png)</span><span class="sxs-lookup"><span data-stu-id="2a507-112">Create a new unit test project ![Install App](../media/UnitTests/newproject.png)</span></span>

3. <span data-ttu-id="2a507-113">테스트 코드를 포함 하도록 업데이트 UnitTest.cs</span><span class="sxs-lookup"><span data-stu-id="2a507-113">Update UnitTest.cs to include your test code</span></span>
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


### <a name="remotely-run-unit-test-on-windows-10-iot-core-device"></a><span data-ttu-id="2a507-114">Windows 10 IoT Core 장치에서 단위 테스트를 원격으로 실행</span><span class="sxs-lookup"><span data-stu-id="2a507-114">Remotely run unit test on Windows 10 IoT Core device</span></span>
___

1. <span data-ttu-id="2a507-115">Visual Studio 테스트 탐색기를 엽니다 (테스트 > Windows > 테스트 탐색기).</span><span class="sxs-lookup"><span data-stu-id="2a507-115">Open the Visual Studio Test Explorer (Test > Windows > Test Explorer).</span></span>
 ![테스트 탐색기](../media/UnitTests/show-test-explorer.png)

1. <span data-ttu-id="2a507-117">테스트를 배포 하려면,에 대 한 프로젝트는 uwp (유니버설 인증 및 원격 컴퓨터에 특별히 사용)으로 구성 된 동일한 방식으로 구성 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a507-117">For test deployment to work, your project must be configured in the same way UWP apps are configured (specifically using Universal Authentication and Remote Machine).</span></span>  <span data-ttu-id="2a507-118">참조 [Visual Studio를 사용 하 여 앱을 배포](../develop-your-app/appdeployment.md) 세부 사항에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a507-118">See [Deploy an App with Visual Studio](../develop-your-app/appdeployment.md) for specifics.</span></span>

1. <span data-ttu-id="2a507-119">단위 테스트를 원격으로 실행 하려면 테스트 탐색기 및 원하는 TestMethod 오른쪽 단추로 클릭 하 고 실행/디버그 선택한 테스트를 선택 하면 사용할 수 있습니다 ![테스트 탐색기](../media/UnitTests/test-explorer.png)</span><span class="sxs-lookup"><span data-stu-id="2a507-119">To remotely run a unit test, you can use the Test Explorer and right clicking the desired TestMethod and selecting Run/Debug Selected Tests ![Test Explorer](../media/UnitTests/test-explorer.png)</span></span>

1. <span data-ttu-id="2a507-120">원격으로 실행 하거나 모든 단위 테스트를 디버깅, 테스트를 사용할 수 있습니다 > 실행 또는 테스트 > 디버그 ![테스트 탐색기](../media/UnitTests/run-tests.png)
 ![테스트 탐색기](../media/UnitTests/debug-tests.png)</span><span class="sxs-lookup"><span data-stu-id="2a507-120">To remotely run or debug all unit tests, you can use Test > Run or Test > Debug ![Test Explorer](../media/UnitTests/run-tests.png)
 ![Test Explorer](../media/UnitTests/debug-tests.png)</span></span>
   

### <a name="configure-unit-tests-as-part-of-a-continuous-integration-build"></a><span data-ttu-id="2a507-121">지속적인 통합 빌드의 일부로 단위 테스트 구성</span><span class="sxs-lookup"><span data-stu-id="2a507-121">Configure unit tests as part of a Continuous Integration build</span></span>
___

<span data-ttu-id="2a507-122">Visual Studio 팀 블로그 게시물에서 VSTS 빌드를 Windows 10 IoT Core 단위 테스트를 통합 하는 방법을 보여 주는 만들었습니다. [Win10 IoT Core, UWP 및 VSTS를 사용 하 여 IoT 용 DevOps](https://blogs.msdn.microsoft.com/devops/2018/03/07/devops-for-iot-with-win10-iot-core-uwp-and-vsts/)</span><span class="sxs-lookup"><span data-stu-id="2a507-122">The Visual Studio team has created a great blog post showing how to incorporate Windows 10 IoT Core unit tests into a VSTS build: [DevOps for IoT with Win10 IoT Core, UWP, and VSTS](https://blogs.msdn.microsoft.com/devops/2018/03/07/devops-for-iot-with-win10-iot-core-uwp-and-vsts/)</span></span>

