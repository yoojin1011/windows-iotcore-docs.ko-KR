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
# <a name="investigating-memory-leaks"></a>메모리 누수 검사

Visual Studio를 사용 하 여 Windows IoT Core에서 메모리 누수를 조사 하는 데 가장 적합 한 도구 통합은 [진단 도구](https://docs.microsoft.com/visualstudio/profiling/memory-usage)

![진단 도구](../media/MemoryLeaks/DiagnosticTools.PNG)

포그라운드 응용 프로그램 할 수 있습니다 [설명서를 따라](https://docs.microsoft.com/visualstudio/profiling/memory-usage)합니다.

하지만 이러한 도구는 Windows IoT Core를 사용 하 여 직접 작동 하지 않습니다 **백그라운드 응용 프로그램**합니다. 백그라운드 응용 프로그램에 사용 되는 코드를 프로 파일링 하는 한 가지 방법은 다음과 같습니다. 분석을 위해 전경 앱을 래핑해야 합니다

1. 추가 된 **비어 있는 앱** 에 **백그라운드 앱** 솔루션
2. 마우스 오른쪽 단추로 클릭 합니다 **비어 있는 앱** 에 대 한 참조를 추가한 참조는 **백그라운드 앱**
3. 변경 된 **백그라운드 앱** run () 메서드 taskInstance 매개 변수가 null 인지 확인 하 고 해당 처리를 다르게 경우.
4. **BlankApp** BackgroundApp::Run(null) 호출
5. BackgroundApp::Run에 대 한 호출에 중단점을 설정 합니다.
6. 중단점이 적중 될 때 합니다 **진단 도구** 창과 클릭 합니다 ![스냅숏](../media/MemoryLeaks/Snapshot.PNG) 단추입니다.

8. 문제를 재현
9. 다른 스냅숏 만들기
10. 사용 된 **진단 도구** 누수를 진단 하는 창입니다.

## <a name="create-a-test-app"></a>테스트 앱 만들기

메모리를 할당 하 고 누수를 시뮬레이션 하기 위해 해제 하지 않습니다 하는 응용 프로그램을 사용 하 여 시작 해 보겠습니다.
먼저 새 C# 응용 프로그램을 백그라운드: [백그라운드 응용 프로그램 개발](./BackgroundApplications.md)

이 사용 하 여 StartupTask.cs에서 코드를 바꿉니다
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

이 시점에서 IoT 장치에서 백그라운드 응용 프로그램을 실행 하는 경우 메모리를 많이 사용 하 고 해제 되지 않습니다. 진단 도구를 사용 하려는 경우이 시점에서 표시 됩니다이 처럼 보이는 하므로 백그라운드 앱을 사용 하 여 도구를 사용 하 여 현재 지원 되지 않습니다.

![백그라운드 앱 진단 도구](../media/MemoryLeaks/DiagnosticToolsBackgroundApp.png)

이 문제를 해결 하려면 포그라운드 앱 솔루션에 추가 하려고 합니다. 에 **솔루션 탐색기** 솔루션 폴더를 마우스 오른쪽 단추로 클릭 하 고 선택한 **Add.New 프로젝트**합니다.

![새 프로젝트 추가](../media/MemoryLeaks/AddNewProject.png)

선택할 **시각적 C#> Windows 유니버설 > 비어 있는 앱** 프로젝트 유형으로 프로젝트 이름을 지정 하 고 클릭 **확인**합니다.

![새 프로젝트 추가](../media/MemoryLeaks/NewForegroundApp.PNG)

새 포그라운드 응용 프로그램 프로젝트를 마우스 오른쪽 단추로 클릭 **참조가** 노드와 선택 **참조 추가...**

![새 프로젝트 추가](../media/MemoryLeaks/AddReference.PNG)

에 **참조 관리자** 대화 상자 선택 **프로젝트** 왼쪽 창에서.  가운데 창에서 확인을 백그라운드 응용 프로그램 프로젝트 옆의 확인란을 추가 하 고 클릭 **확인**합니다.

![새 프로젝트 추가](../media/MemoryLeaks/AddReferenceDialog.PNG)

그런 다음 포그라운드 응용 프로그램 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 클릭 **시작 프로젝트로 설정**합니다.

![새 프로젝트 추가](../media/MemoryLeaks/SetAsStartup.PNG)

백그라운드 응용 프로그램 개체의 인스턴스를 만들어 null를 유일한 매개 변수로 전달 하는 실행을 호출 하는 코드를 추가 합니다.
```C#
public MainPage()
{
    this.InitializeComponent();
    LeakyBackgroundApp.StartupTask task = new LeakyBackgroundApp.StartupTask();
    task.Run(null);
}
```

다음 백그라운드 앱의 실행에서 메서드 확인 되었는지 taskInstance isnotnull 사용 하기 전에 합니다.

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

1. 작업에 대 한 호출에 중단점을 설정 합니다. Run(null) 합니다.
2. 타이머에 다른 중단점을 설정 합니다. StartupTask.cs에서 Timer_Tick 변경 (Timeout.Infinite, Timeout.Infinite).
3. F5 키를 눌러 디버깅을 시작 하려면
4. 첫 번째 중단점 눌러 비교할 초기 스냅숏 단추를 누를 때

![스냅숏](../media/MemoryLeaks/Snapshot.PNG)

5. F5 키를 눌러
6. 두 번째 중단점 눌러의 현재 상태를 캡처하기 위해 다시 스냅숏 단추를 누를 때.

이제 진단 도구는 다음과 같은 2 스냅숏과 메모리 사용 증가 하는 그래프를 표시 해야 합니다.

![누수를 사용 하 여 진단 도구](../media/MemoryLeaks/DiagnosticToolsWithLeaks.PNG)

힙 크기 열에서 2 행을 살펴봅니다. 두 번째 숫자 더하기 기호를 사용 하 여 및 위쪽 화살표를 클릭 합니다. 다음과 유사한 결과가 나타납니다.

![스냅숏 테이블](../media/MemoryLeaks/Snapshot2_1.PNG)

크기 차이 정렬 맨 위에 있는 가장 큰 수 있도록 클릭 맨 위 행입니다. 두 번째 세부 정보 테이블 위에 클릭 **참조 된 형식**합니다.  두 번째 표에서 이제 표시 **목록\<byte\>**  모든 메모리 사용량의 원본으로 합니다.

![스냅숏 테이블](../media/MemoryLeaks/Snapshot2_2.PNG)
