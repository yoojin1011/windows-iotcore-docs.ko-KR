---
title: 메모리 누수 조사
author: paulmon
ms.author: paulmon
ms.date: 09/20/2017
ms.topic: article
description: 메모리 누수를 조사 하는 방법에 대해 알아봅니다.
keywords: windows iot, Visual Studio, 누수, 문제 해결
ms.openlocfilehash: 8385ae621c18c079d0a2ec7bf7b0b4042359eccc
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "60168621"
---
# <a name="investigating-memory-leaks"></a>메모리 누수 조사

Visual Studio를 사용 하 여 Windows IoT Core의 메모리 누수를 조사 하는 가장 좋은 도구는 통합 된 [진단 도구](https://docs.microsoft.com/visualstudio/profiling/memory-usage)

![진단 도구](../media/MemoryLeaks/DiagnosticTools.PNG)

포그라운드 응용 프로그램의 경우 [설명서를 따를](https://docs.microsoft.com/visualstudio/profiling/memory-usage)수 있습니다.

그러나 이러한 도구는 Windows IoT Core **백그라운드 응용 프로그램**에서 직접 작동 하지 않습니다. 백그라운드 응용 프로그램에서 사용 되는 코드를 프로 파일링 하는 한 가지 방법은 분석을 위해 포그라운드 앱에 래핑하는 것입니다.

1. **백그라운드 앱** 솔루션에 **빈 앱** 추가
2. **빈 앱** 참조를 마우스 오른쪽 단추로 클릭 하 고 **백그라운드 앱** 에 대 한 참조를 추가 합니다.
3. **백그라운드 앱** Run () 메서드를 변경 하 여 taskinstance 매개 변수가 null 인지 확인 하 고 이러한 사례를 다르게 처리 합니다.
4. **BlankApp** 호출 BackgroundApp:: Run (null)
5. BackgroundApp:: Run에 대 한 호출에 중단점 설정
6. 중단점이 적중 되 면 **진단 도구** 창을 찾은 다음 스냅숏 ![](../media/MemoryLeaks/Snapshot.PNG) 단추를 클릭 합니다.

8. 문제 재현
9. 다른 스냅숏 만들기
10. **진단 도구** 창을 사용 하 여 누수를 진단할 수 있습니다.

## <a name="create-a-test-app"></a>테스트 앱 만들기

메모리를 할당 하 고 누수를 시뮬레이트하는 데 사용 하지 않는 응용 프로그램부터 시작 해 보겠습니다.
먼저 새 C# 백그라운드 응용 프로그램을 만듭니다. [백그라운드 응용 프로그램 개발](./BackgroundApplications.md)

StartupTask.cs의 코드를 다음으로 바꿉니다.
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

이제 IoT 장치에서 백그라운드 응용 프로그램을 실행 하는 경우 많은 메모리를 사용 하 고 사용 하지 마십시오. 이 시점에서 진단 도구를 사용 하려고 하면 백그라운드 앱과 함께 도구를 사용 하는 것이 현재 지원 되지 않기 때문에 다음과 같은 내용이 표시 됩니다.

![진단 도구 백그라운드 앱](../media/MemoryLeaks/DiagnosticToolsBackgroundApp.png)

이 문제를 해결 하기 위해 포그라운드 앱을 솔루션에 추가 하겠습니다. **솔루션 탐색기** 에서 솔루션 폴더를 마우스 오른쪽 단추로 클릭 한 다음 **추가. 새 프로젝트**를 선택 합니다.

![새 프로젝트 추가](../media/MemoryLeaks/AddNewProject.png)

프로젝트 형식으로 **Visual C#> Windows 유니버설 > 비어 있는 앱** 을 선택 하 고 프로젝트 이름을 입력 한 다음 **확인**을 클릭 합니다.

![새 프로젝트 추가](../media/MemoryLeaks/NewForegroundApp.PNG)

새 포그라운드 앱 프로젝트의 **참조** 노드를 마우스 오른쪽 단추로 클릭 하 고 **참조 추가** ...를 선택 합니다.

![새 프로젝트 추가](../media/MemoryLeaks/AddReference.PNG)

**참조 관리자** 대화 상자의 왼쪽 창에서 **프로젝트** 를 선택 합니다.  가운데 창에서 백그라운드 응용 프로그램 프로젝트 옆에 있는 확인란을 선택 하 고 **확인**을 클릭 합니다.

![새 프로젝트 추가](../media/MemoryLeaks/AddReferenceDialog.PNG)

다음으로 포그라운드 앱 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 **시작 프로젝트로 설정**을 클릭 합니다.

![새 프로젝트 추가](../media/MemoryLeaks/SetAsStartup.PNG)

백그라운드 응용 프로그램 개체의 인스턴스를 만들고 null을 유일한 매개 변수로 전달 하는 실행을 호출 하는 코드를 추가 합니다.
```C#
public MainPage()
{
    this.InitializeComponent();
    LeakyBackgroundApp.StartupTask task = new LeakyBackgroundApp.StartupTask();
    task.Run(null);
}
```

그런 다음 백그라운드 응용 프로그램의 Run 메서드에서 taskInstance를 사용 하기 전에 null이 아닌지 확인 합니다.

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

1. 작업 호출에 대 한 중단점을 설정 합니다. (Null)를 실행 합니다.
2. 타이머에 다른 중단점을 설정 합니다. StartupTask.cs의 Timer_Tick에서 (Timeout. Infinite, Timeout. Infinite)를 변경 합니다.
3. F5 키를 눌러 디버깅을 시작 합니다.
4. 첫 번째 중단점에 도달 하면 스냅숏 단추를 눌러 비교할 기준선을 설정 합니다.

![스냅숏](../media/MemoryLeaks/Snapshot.PNG)

5. F5 키를 누릅니다.
6. 두 번째 중단점에 도달 하면 스냅숏 단추를 다시 눌러 현재 상태를 캡처합니다.

이제 진단 도구는 메모리 사용이 늘어나는 그래프가 표시 되 고 다음과 같이 두 개의 스냅숏이 표시 됩니다.

![누출 진단 도구](../media/MemoryLeaks/DiagnosticToolsWithLeaks.PNG)

힙 크기 열에서 2 행을 찾습니다. 더하기 기호 및 위쪽 화살표를 사용 하 여 두 번째 숫자를 클릭 합니다. 다음과 같이 표시되어야 합니다.

![스냅숏 테이블](../media/MemoryLeaks/Snapshot2_1.PNG)

크기 차이 별로 정렬 하 여 가장 큰 숫자가 맨 위에 오도록 한 다음 맨 위 행을 클릭 합니다. 두 번째 세부 정보 테이블 위에 **참조 된 유형**을 클릭 합니다.  이제 두 번째 테이블은 모든 메모리 사용의 원본으로 **List\<Byte []\>**  를 표시 합니다.

![스냅숏 테이블](../media/MemoryLeaks/Snapshot2_2.PNG)
