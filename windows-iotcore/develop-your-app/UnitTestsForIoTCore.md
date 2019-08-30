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
# <a name="developing-unit-tests"></a>단위 테스트 개발
Windows 10 IoT Core에서 지원 되는 UWP 단위 테스트에 대해 알아봅니다.

## <a name="uwp-unit-tests"></a>UWP 단위 테스트
___

단위 테스트는 앱 개발자를 위한 중요 한 보호 및 유효성 검사를 제공 합니다.  Visual Studio 15.6에는 새로운 테스트 플랫폼에서 Windows 10 IoT Core에 대 한 지원이 추가 되었습니다.  이 새로운 지원을 통해 연속 통합 빌드의 일부로 실행 하거나 Visual Studio에서 직접 실행할 수 있는 UWP 기능에 대 한 단위 테스트를 만들 수 있습니다.


### <a name="create-new-unit-test-project"></a>새 단위 테스트 프로젝트 만들기
___

1. Visual Studio를 엽니다.

2. 새 단위 테스트 프로젝트 ![만들기 앱 설치](../media/UnitTests/newproject.png)

3. 테스트 코드를 포함 하도록 UnitTest.cs를 업데이트 합니다.
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


### <a name="remotely-run-unit-test-on-windows-10-iot-core-device"></a>Windows 10 IoT Core 장치에서 단위 테스트 원격 실행
___

1. Visual Studio 테스트 탐색기 (테스트 > Windows > 테스트 탐색기)를 엽니다.
 ![테스트 탐색기](../media/UnitTests/show-test-explorer.png)

1. 테스트 배포가 작동 하려면 UWP 앱을 구성 하는 것과 같은 방식으로 프로젝트를 구성 해야 합니다 (특히 유니버설 인증 및 원격 컴퓨터 사용).  자세한 내용은 [Visual Studio를 사용 하 여 앱 배포](../develop-your-app/appdeployment.md) 를 참조 하세요.

1. 단위 테스트를 원격으로 실행 하려면 테스트 탐색기를 사용 하 고 원하는 TestMethod를 마우스 오른쪽 단추로 클릭 한 다음 선택한 테스트 ![실행/디버그 테스트 탐색기를 선택 합니다.](../media/UnitTests/test-explorer.png)

1. 모든 단위 테스트를 원격으로 실행 하거나 디버그 하기 위해 테스트 > 실행 또는 테스트 > ![테스트 탐색기](../media/UnitTests/run-tests.png)
 ![테스트 탐색기를 사용 하 여 테스트를 수행할 수 있습니다.](../media/UnitTests/debug-tests.png)
   

### <a name="configure-unit-tests-as-part-of-a-continuous-integration-build"></a>연속 통합 빌드의 일부로 단위 테스트 구성
___

Visual Studio 팀은 Windows 10 IoT Core 단위 테스트를 VSTS 빌드에 통합 하는 방법을 보여 주는 유용한 블로그 게시물을 만들었습니다. [Win10 IoT Core, UWP 및 VSTS를 사용 하는 IoT 용 DevOps](https://blogs.msdn.microsoft.com/devops/2018/03/07/devops-for-iot-with-win10-iot-core-uwp-and-vsts/)

