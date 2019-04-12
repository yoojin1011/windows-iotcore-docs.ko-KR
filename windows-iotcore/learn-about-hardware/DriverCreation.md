---
title: 범용 드라이버 만들기
author: parameshbabu
ms.author: pabab
ms.date: 08/28/2017
ms.topic: article
description: 장치에서 단일 드라이버 패키지를 만들 수 있도록 범용 드라이버를 만드는 방법에 알아봅니다.
keywords: windows iot, 범용 드라이버, 드라이버를 Windows 10 UWP
ms.openlocfilehash: 839a742598481e3ff70e3a0ccf1ff072bd62e051
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512326"
---
# <a name="universal-driver-creation"></a>범용 드라이버 만들기

이 문서에서는 IoT Core 장치에 대 한 범용 드라이버 만들기 안내 합니다.

범용 드라이버를 통해 Windows 10 IoT Core를 포함 하 여 UWP 기반 버전을 실행 하는 몇 가지 장치 유형에 서 실행 되는 단일 드라이버 패키지를 만들 수 있습니다.

이 드라이버 패키지는 범용 INF 파일 및 몇 가지 바이너리를 포함합니다. 각각에 대 한 요구 사항은 다음과 같습니다.
- 범용 INF 파일에만 사용할 수 [UWP 기반 Windows 버전에서 지원 되는 INF 구문 하위 집합](https://docs.microsoft.com/windows-hardware/drivers/install/using-a-universal-inf-file#which-inf-sections-are-invalid-in-a-universal-inf-file)합니다. INF 파일을 작성 하는 동안 사용 합니다 [InfVerif 도구](https://docs.microsoft.com/windows-hardware/drivers/devtest/infverif) 파일 해당 구문에 부합 하는지 확인 합니다.

- 이진 파일 (설명서 참조 페이지에 보편적으로 표시) 하는 Windows 10의 UWP 기반 버전에서 지원 되는 장치 드라이버 인터페이스 사용할 수 있습니다. [KMDF](https://docs.microsoft.com/windows-hardware/drivers/wdf/index), [UMDF 2](https://docs.microsoft.com/windows-hardware/drivers/wdf/getting-started-with-umdf-version-2), 또는 Windows Driver Model (WDM). OneCore 하위 집합에 포함 된 Api만 호출할 수 있습니다. 사용 된 [ApiValidator 도구](https://docs.microsoft.com/windows-hardware/drivers/develop/validating-universal-drivers) 이진 파일 Api를 호출 하는 확인 하려면 유효 합니다.

자세한 방법 **Visual Studio에서 드라이버 패키지를 만들**를 방문 하십시오 [드라이버 패키지 만들기](https://docs.microsoft.com/windows-hardware/drivers/develop/creating-a-driver-package)

싶다면 **IoT Core에는 범용 드라이버를 만들 수 있도록 샘플**를 방문 하십시오 우리의 [범용 드라이버 샘플](https://developer.microsoft.com/en-us/windows/iot/samples/driverlab)

## <a name="additional-universal-driver-resources"></a>범용 드라이버 추가 리소스

1. 에 대 한 자세한 **디자인 원칙** 하 고 **모범 사례** 범용 드라이버 패키지를 개발할 때 방문 하십시오 [범용 드라이버를 사용 하 여 시작](https://docs.microsoft.com/windows-hardware/drivers/develop/getting-started-with-universal-drivers)

2. 도움말에 대 한 **범용 드라이버 디버깅**를 방문 하십시오 [유니버설 Windows 드라이버 디버깅](https://docs.microsoft.com/windows-hardware/drivers/develop/debugging-a-universal-driver)합니다.

