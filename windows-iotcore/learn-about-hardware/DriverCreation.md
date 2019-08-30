---
title: 범용 드라이버 만들기
author: parameshbabu
ms.author: pabab
ms.date: 08/28/2017
ms.topic: article
description: 장치에서 단일 드라이버 패키지를 만들 수 있도록 유니버설 드라이버를 만드는 방법에 대해 알아봅니다.
keywords: windows iot, 범용 드라이버, 드라이버, Windows 10, UWP
ms.openlocfilehash: 839a742598481e3ff70e3a0ccf1ff072bd62e051
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "60169581"
---
# <a name="universal-driver-creation"></a>범용 드라이버 만들기

이 문서에서는 IoT Core 장치에 대 한 범용 드라이버를 만드는 과정을 안내 합니다.

유니버설 드라이버를 사용 하면 IoT Core를 포함 하 여 UWP 기반 버전의 Windows 10을 실행 하는 여러 장치 유형 간에 실행 되는 단일 드라이버 패키지를 만들 수 있습니다.

이 드라이버 패키지에는 범용 INF 파일과 여러 바이너리가 포함 되어 있습니다. 각각에 대 한 요구 사항은 다음과 같습니다.
- 유니버설 INF 파일은 [Windows의 UWP 기반 버전에서 지원 되는 INF 구문의 하위 집합만](https://docs.microsoft.com/windows-hardware/drivers/install/using-a-universal-inf-file#which-inf-sections-are-invalid-in-a-universal-inf-file)사용할 수 있습니다. INF 파일을 작성 하는 동안 [InfVerif 도구](https://docs.microsoft.com/windows-hardware/drivers/devtest/infverif) 를 사용 하 여 파일이 해당 구문을 준수 하는지 확인 합니다.

- 이진 파일은 UWP 기반 버전의 Windows 10에서 지원 되는 장치 드라이버 인터페이스만 사용할 수 있습니다 (설명서 참조 페이지에서 유니버설로 표시 됨). [Kmdf](https://docs.microsoft.com/windows-hardware/drivers/wdf/index), [UMDF 2](https://docs.microsoft.com/windows-hardware/drivers/wdf/getting-started-with-umdf-version-2)또는 WDM (WDM(Windows Driver Model)). OneCore 하위 집합에 포함 된 Api를 호출할 수도 있습니다. [Apivalidator 도구](https://docs.microsoft.com/windows-hardware/drivers/develop/validating-universal-drivers) 를 사용 하 여 이진 파일이 호출 하는 api가 유효한 지 확인 합니다.

**Visual Studio에서 드라이버 패키지를 만드는**방법을 알아보려면 [드라이버 패키지 만들기](https://docs.microsoft.com/windows-hardware/drivers/develop/creating-a-driver-package) 를 참조 하세요.

**IoT Core에서 범용 드라이버를 만드는 데 도움이 되는 샘플**을 원하는 경우 [universal driver 샘플](https://developer.microsoft.com/en-us/windows/iot/samples/driverlab) 을 참조 하세요.

## <a name="additional-universal-driver-resources"></a>추가 범용 드라이버 리소스

1. 범용 드라이버 패키지를 개발할 때 **디자인 원칙** 및 **모범 사례** 에 대 한 자세한 내용은 [범용 드라이버 시작](https://docs.microsoft.com/windows-hardware/drivers/develop/getting-started-with-universal-drivers) 하기를 참조 하세요.

2. **유니버설 드라이버를 디버깅**하는 데 도움이 필요한 경우 [유니버설 Windows 드라이버 디버그](https://docs.microsoft.com/windows-hardware/drivers/develop/debugging-a-universal-driver)를 참조 하세요.

