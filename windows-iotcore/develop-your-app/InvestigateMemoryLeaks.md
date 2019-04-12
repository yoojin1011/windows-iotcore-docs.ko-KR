---
title: 조사할 메모리 누수
author: paulmon
ms.author: paulmon
ms.date: 09/20/2017
ms.topic: article
description: 메모리 누수를 확인 하는 방법에 알아봅니다.
keywords: windows iot, Visual Studio 누수, 문제 해결
ms.openlocfilehash: 8385ae621c18c079d0a2ec7bf7b0b4042359eccc
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512742"
---
# <a name="investigating-memory-leaks"></a><span data-ttu-id="343ab-104">메모리 누수 검사</span><span class="sxs-lookup"><span data-stu-id="343ab-104">Investigating Memory Leaks</span></span>

<span data-ttu-id="343ab-105">Visual Studio를 사용 하 여 Windows IoT Core에서 메모리 누수를 조사 하는 데 가장 적합 한 도구 통합은 [진단 도구](https://docs.microsoft.com/visualstudio/profiling/memory-usage)</span><span class="sxs-lookup"><span data-stu-id="343ab-105">The best tool for investigating memory leaks on Windows IoT Core with Visual Studio is the integrated [Diagnostic Tools](https://docs.microsoft.com/visualstudio/profiling/memory-usage)</span></span>

![진단 도구](../media/MemoryLeaks/DiagnosticTools.PNG)

<span data-ttu-id="343ab-107">포그라운드 응용 프로그램 할 수 있습니다 [설명서를 따라](https://docs.microsoft.com/visualstudio/profiling/memory-usage)합니다.</span><span class="sxs-lookup"><span data-stu-id="343ab-107">For foreground applications you can [follow the documentation](https://docs.microsoft.com/visualstudio/profiling/memory-usage).</span></span>

<span data-ttu-id="343ab-108">하지만 이러한 도구는 Windows IoT Core를 사용 하 여 직접 작동 하지 않습니다 **백그라운드 응용 프로그램**합니다.</span><span class="sxs-lookup"><span data-stu-id="343ab-108">However, these tools don't work directly with a Windows IoT Core **Background Application**.</span></span> <span data-ttu-id="343ab-109">백그라운드 응용 프로그램에 사용 되는 코드를 프로 파일링 하는 한 가지 방법은 다음과 같습니다. 분석을 위해 전경 앱을 래핑해야 합니다</span><span class="sxs-lookup"><span data-stu-id="343ab-109">One way to profile code used in a background application is to wrap it in a foreground app for analysis:</span></span>

1. <span data-ttu-id="343ab-110">추가 된 **비어 있는 앱** 에 **백그라운드 앱** 솔루션</span><span class="sxs-lookup"><span data-stu-id="343ab-110">Add a **Blank App** to the **Background App** solution</span></span>
2. <span data-ttu-id="343ab-111">마우스 오른쪽 단추로 클릭 합니다 **비어 있는 앱** 에 대 한 참조를 추가한 참조는 **백그라운드 앱**</span><span class="sxs-lookup"><span data-stu-id="343ab-111">Right-click the **Blank App** references and add a reference to the **Background App**</span></span>
3. <span data-ttu-id="343ab-112">변경 된 **백그라운드 앱** run () 메서드 taskInstance 매개 변수가 null 인지 확인 하 고 해당 처리를 다르게 경우.</span><span class="sxs-lookup"><span data-stu-id="343ab-112">Change the **Background App** Run() method to check if the taskInstance parameter is null and handle those cases differently.</span></span>
4. <span data-ttu-id="343ab-113">**BlankApp** BackgroundApp::Run(null) 호출</span><span class="sxs-lookup"><span data-stu-id="343ab-113">From the **BlankApp** call BackgroundApp::Run(null)</span></span>
5. <span data-ttu-id="343ab-114">BackgroundApp::Run에 대 한 호출에 중단점을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="343ab-114">Set a breakpoint on the call to BackgroundApp::Run</span></span>
6. <span data-ttu-id="343ab-115">중단점이 적중 될 때 합니다 **진단 도구** 창과 클릭 합니다 ![스냅숏](../media/MemoryLeaks/Snapshot.PNG) 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="343ab-115">When the breakpoint is hit find the **Diagnostic Tools** windows and click the ![Snapshot](../media/MemoryLeaks/Snapshot.PNG) button.</span></span>

8. <span data-ttu-id="343ab-116">문제를 재현</span><span class="sxs-lookup"><span data-stu-id="343ab-116">Reproduce the problem</span></span>
9. <span data-ttu-id="343ab-117">다른 스냅숏 만들기</span><span class="sxs-lookup"><span data-stu-id="343ab-117">Take another snapshot</span></span>
10. <span data-ttu-id="343ab-118">사용 된 **진단 도구** 누수를 진단 하는 창입니다.</span><span class="sxs-lookup"><span data-stu-id="343ab-118">Use the **Diagnostic Tools** window to diagnose the leak.</span></span>

## <a name="create-a-test-app"></a><span data-ttu-id="343ab-119">테스트 앱 만들기</span><span class="sxs-lookup"><span data-stu-id="343ab-119">Create a test app</span></span>

<span data-ttu-id="343ab-120">메모리를 할당 하 고 누수를 시뮬레이션 하기 위해 해제 하지 않습니다 하는 응용 프로그램을 사용 하 여 시작 해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="343ab-120">Let's start with an application that allocates memory and doesn't free it to simulate a leak.</span></span>
<span data-ttu-id="343ab-121">먼저 새 C# 응용 프로그램을 백그라운드: [백그라운드 응용 프로그램 개발](./BackgroundApplications.md)</span><span class="sxs-lookup"><span data-stu-id="343ab-121">Begin by creating a new C# Background application: [Developing Background Applications](./BackgroundApplications.md)</span></span>

<span data-ttu-id="343ab-122">이 사용 하 여 StartupTask.cs에서 코드를 바꿉니다</span><span class="sxs-lookup"><span data-stu-id="343ab-122">Replace the code in StartupTask.cs with this</span></span>
```C#
using System;
using System.Collections.Generic;
using System.Diagnostics;
using System.Threading;
using Windows.ApplicationModel.Background;
using Windows.System;

namespace LeakyBackgroundApp
{
    public sealed class StartupTask : IBackgroundTask
    {
        private Timer timer;
        private BackgroundTaskDeferral deferral;
        List<byte[]> buffer = new List<byte[]>();
        private const ulong minRemaining = 300 * 1024 * 1024;

        public void Run(IBackgroundTaskInstance taskInstance)
        {
            deferral = taskInstance.GetDeferral();
            timer = new Timer(Timer_Tick, null, 500, 500);
        }

        private void Timer_Tick(object state)
        {
            ulong remaining = (MemoryManager.AppMemoryUsageLimit - MemoryManager.AppMemoryUsage);
            ulong chunkSize = remaining / 100;

            try
            {
                if (remaining > minRemaining)
                {
                    var chunk = new byte[chunkSize];

                    // force virtual memory to be commited by writing to it
                    for (int i = 0; i < chunk.Length; i += 4096)
                    {
                        chunk[i] = 0xDA;
                    }

                    // "leak" memory by adding it to the list
                    buffer.Add(chunk);
                    Debug.WriteLine(String.Format("Allocated {0} chunk(s)", buffer.Count));
                }
                else
                {
                    timer.Change(Timeout.Infinite, Timeout.Infinite);
                }
            }
            catch (OutOfMemoryException ex)
            {
                Debug.Write(ex.Message);
                timer.Change(Timeout.Infinite, Timeout.Infinite);
            }
        }
    }
}
```

<span data-ttu-id="343ab-123">이 시점에서 IoT 장치에서 백그라운드 응용 프로그램을 실행 하는 경우 메모리를 많이 사용 하 고 해제 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="343ab-123">At this point if you run the background application on your IoT device it should use up a lot of memory and never free it.</span></span> <span data-ttu-id="343ab-124">진단 도구를 사용 하려는 경우이 시점에서 표시 됩니다이 처럼 보이는 하므로 백그라운드 앱을 사용 하 여 도구를 사용 하 여 현재 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="343ab-124">If you try to use the diagnostic tools at this point you will see something that looks like this, because using the tools with background apps is currently unsupported.</span></span>

![백그라운드 앱 진단 도구](../media/MemoryLeaks/DiagnosticToolsBackgroundApp.png)

<span data-ttu-id="343ab-126">이 문제를 해결 하려면 포그라운드 앱 솔루션에 추가 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="343ab-126">To work around this we are going to add a foreground app to the solution.</span></span> <span data-ttu-id="343ab-127">에 **솔루션 탐색기** 솔루션 폴더를 마우스 오른쪽 단추로 클릭 하 고 선택한 **Add.New 프로젝트**합니다.</span><span class="sxs-lookup"><span data-stu-id="343ab-127">In the **Solution Explorer** right-click on the solution folder and then select **Add.New Project**.</span></span>

![새 프로젝트 추가](../media/MemoryLeaks/AddNewProject.png)

<span data-ttu-id="343ab-129">선택할 **시각적 C#> Windows 유니버설 > 비어 있는 앱** 프로젝트 유형으로 프로젝트 이름을 지정 하 고 클릭 **확인**합니다.</span><span class="sxs-lookup"><span data-stu-id="343ab-129">Choose **Visual C#>Windows Universal>Blank App** as the project type, name your project and click **OK**.</span></span>

![새 프로젝트 추가](../media/MemoryLeaks/NewForegroundApp.PNG)

<span data-ttu-id="343ab-131">새 포그라운드 응용 프로그램 프로젝트를 마우스 오른쪽 단추로 클릭 **참조가** 노드와 선택 **참조 추가...**</span><span class="sxs-lookup"><span data-stu-id="343ab-131">Right-click on the new foreground app project's **References** node and select **Add Reference...**</span></span>

![새 프로젝트 추가](../media/MemoryLeaks/AddReference.PNG)

<span data-ttu-id="343ab-133">에 **참조 관리자** 대화 상자 선택 **프로젝트** 왼쪽 창에서.</span><span class="sxs-lookup"><span data-stu-id="343ab-133">In the **Reference Manager** dialog choose **Projects** in the left-hand pane.</span></span>  <span data-ttu-id="343ab-134">가운데 창에서 확인을 백그라운드 응용 프로그램 프로젝트 옆의 확인란을 추가 하 고 클릭 **확인**합니다.</span><span class="sxs-lookup"><span data-stu-id="343ab-134">In the center pane add a check in the checkbox next to your background application project and click **OK**.</span></span>

![새 프로젝트 추가](../media/MemoryLeaks/AddReferenceDialog.PNG)

<span data-ttu-id="343ab-136">그런 다음 포그라운드 응용 프로그램 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 클릭 **시작 프로젝트로 설정**합니다.</span><span class="sxs-lookup"><span data-stu-id="343ab-136">Next right-click the foreground app project and click **Set as StartUp Project**.</span></span>

![새 프로젝트 추가](../media/MemoryLeaks/SetAsStartup.PNG)

<span data-ttu-id="343ab-138">백그라운드 응용 프로그램 개체의 인스턴스를 만들어 null를 유일한 매개 변수로 전달 하는 실행을 호출 하는 코드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="343ab-138">Add code to create an instance of your background application object and call Run passing in null as the only parameter.</span></span>
```C#
public MainPage()
{
    this.InitializeComponent();
    LeakyBackgroundApp.StartupTask task = new LeakyBackgroundApp.StartupTask();
    task.Run(null);
}
```

<span data-ttu-id="343ab-139">다음 백그라운드 앱의 실행에서 메서드 확인 되었는지 taskInstance isnotnull 사용 하기 전에 합니다.</span><span class="sxs-lookup"><span data-stu-id="343ab-139">Then in your background app's Run method check to make sure taskInstance is not null before using it.</span></span>

```C#
public void Run(IBackgroundTaskInstance taskInstance)
{
    if (taskInstance != null)
    {
        deferral = taskInstance.GetDeferral();
    }

    timer = new Timer(Timer_Tick, null, 500, 500);
}
```

1. <span data-ttu-id="343ab-140">작업에 대 한 호출에 중단점을 설정 합니다. Run(null) 합니다.</span><span class="sxs-lookup"><span data-stu-id="343ab-140">Set a breakpoint on the call to task.Run(null).</span></span>
2. <span data-ttu-id="343ab-141">타이머에 다른 중단점을 설정 합니다. StartupTask.cs에서 Timer_Tick 변경 (Timeout.Infinite, Timeout.Infinite).</span><span class="sxs-lookup"><span data-stu-id="343ab-141">Set another breakpoint on timer.Change(Timeout.Infinite, Timeout.Infinite) in Timer_Tick in StartupTask.cs.</span></span>
3. <span data-ttu-id="343ab-142">F5 키를 눌러 디버깅을 시작 하려면</span><span class="sxs-lookup"><span data-stu-id="343ab-142">Press F5 to begin debugging</span></span>
4. <span data-ttu-id="343ab-143">첫 번째 중단점 눌러 비교할 초기 스냅숏 단추를 누를 때</span><span class="sxs-lookup"><span data-stu-id="343ab-143">When you hit the first breakpoint press the snapshot button to set the baseline to compare against</span></span>

![스냅숏](../media/MemoryLeaks/Snapshot.PNG)

5. <span data-ttu-id="343ab-145">F5 키를 눌러</span><span class="sxs-lookup"><span data-stu-id="343ab-145">Press F5</span></span>
6. <span data-ttu-id="343ab-146">두 번째 중단점 눌러의 현재 상태를 캡처하기 위해 다시 스냅숏 단추를 누를 때.</span><span class="sxs-lookup"><span data-stu-id="343ab-146">When you hit the second breakpoint press the snapshot button again to capture the current state.</span></span>

<span data-ttu-id="343ab-147">이제 진단 도구는 다음과 같은 2 스냅숏과 메모리 사용 증가 하는 그래프를 표시 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="343ab-147">Now the diagnostic tools should show a graph with increasing memory use and 2 snapshot like this:</span></span>

![누수를 사용 하 여 진단 도구](../media/MemoryLeaks/DiagnosticToolsWithLeaks.PNG)

<span data-ttu-id="343ab-149">힙 크기 열에서 2 행을 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="343ab-149">Look at row 2 in the Heap Size column.</span></span> <span data-ttu-id="343ab-150">두 번째 숫자 더하기 기호를 사용 하 여 및 위쪽 화살표를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="343ab-150">Click the second number with the plus sign and up arrow.</span></span> <span data-ttu-id="343ab-151">다음과 유사한 결과가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="343ab-151">You should see something like this:</span></span>

![스냅숏 테이블](../media/MemoryLeaks/Snapshot2_1.PNG)

<span data-ttu-id="343ab-153">크기 차이 정렬 맨 위에 있는 가장 큰 수 있도록 클릭 맨 위 행입니다.</span><span class="sxs-lookup"><span data-stu-id="343ab-153">Sort by size diff so that the largest number is at the top, then click the top row.</span></span> <span data-ttu-id="343ab-154">두 번째 세부 정보 테이블 위에 클릭 **참조 된 형식**합니다.</span><span class="sxs-lookup"><span data-stu-id="343ab-154">Above the second detail table click **Referenced Types**.</span></span>  <span data-ttu-id="343ab-155">두 번째 표에서 이제 표시 **목록\<byte\>**  모든 메모리 사용량의 원본으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="343ab-155">The second table should now show **List\<Byte[]\>** as the source of all the memory usage.</span></span>

![스냅숏 테이블](../media/MemoryLeaks/Snapshot2_2.PNG)
