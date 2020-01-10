---
title: ETW(Windows용 이벤트 추적) IoT 코어
ms.date: 08/28/2017
ms.topic: article
description: 이벤트 추적을 사용 하 여 이벤트를 쓰고 Windows IoT Core에 대 한 이벤트를 사용 하는 방법을 알아봅니다.
keywords: windows iot, 이벤트 추적, ETW, windows 용 이벤트 추적, 장치
ms.openlocfilehash: e5d017c28640f78011ef0b7d82071a51524b2185
ms.sourcegitcommit: ea060254f9c4c25afcd0245c897b9e1425321859
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75721576"
---
# <a name="event-tracing-for-windows-iot-core"></a>ETW(Windows용 이벤트 추적) IoT 코어

ETW (ETW(Windows용 이벤트 추적))를 통해 개발자는 이벤트 추적 세션을 시작 및 중지 하 고, 응용 프로그램을 계측 하 여 추적 이벤트를 제공 하 고, 추적 이벤트를 사용할 수 있습니다.
Windows IoT Core 장치에서 ETW는 매니페스트 기반 이벤트와 클래식 이벤트를 모두 지원 하며, 다른 Windows 10 장치와는 다릅니다.

이 섹션에서는 이벤트 작성 및 사용에 대 한 유용한 링크를 제공 합니다. [Windows 이벤트 추적 페이지](https://msdn.microsoft.com/library/windows/desktop/bb968803(v=vs.85).aspx)에서 자세한 정보를 확인 합니다.

## <a name="writing-events"></a>이벤트 작성

[Windows 유니버설 샘플 Github](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/Logging)의 일부로 이벤트를 작성 하는 여러 가지 방법을 구현 하는 UWP 샘플을 찾습니다.
이는 Windows IoT Core 장치에서 실행 되며 좋은 코드 참조 이기도 합니다.

이벤트 작성 및 Guid 가져오기에 대 한 자세한 가이드는 [여기](https://msdn.microsoft.com/library/windows/desktop/aa364161(v=vs.85).aspx)를 참조 하세요.

## <a name="consuming-events"></a>이벤트 소비

이벤트는 ETL 파일에 저장 되거나 실시간으로 캡처됩니다.
[FTP](../connect-your-device/FTP.md) 또는 [windows 파일 공유](../manage-your-device/WindowsFileSharing.md) 를 사용 하 여 windows IOT Core 장치에서 ETL 파일을 검색 합니다.

## <a name="use-tools-in-windows-assessment-and-deployment-kit"></a>Windows 평가 및 배포 키트의 도구 사용

Windows 평가 및 배포 키트에는 이벤트를 캡처 및 분석 하는 데 유용한 3 가지 도구가 포함 되어 있습니다. [다운로드 하려면 여기를 클릭 하세요.](https://go.microsoft.com/fwlink/p/?LinkId=526740)


1. **Windows Performance Analyzer** 는 데스크톱에서 ETL 파일을 시각화 [여기](https://msdn.microsoft.com/library/windows/hardware/dn927319(v=vs.85).aspx)에 단계별 가이드를 포함 합니다.

2. **Xperf 명령줄 도구** 는 실시간 이벤트를 캡처하고 ETL 파일에 기록 합니다. 이 도구는 Windows IoT Core 장치에 이미 설치 되어 있으므로 장치에서 다음 명령을 실행 하기만 하면 됩니다.

        // Start capturing events from specific GUID and save them to an ETL file
        xperf -start <Session Name> -f <ETL File> -on <GUID>

        // Stop capturing events with the specified session name
        xperf -stop <Session Name>


3. **Tracerpt 명령줄 도구** 는 ETL 파일을 xml 파일로 변환 합니다.

        // Generate dumpfile.xml from ETL file
        tracerpt <ETL File>


## <a name="use-device-portal"></a>장치 포털 사용

장치 포털은 [여기](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal)에 설명 된 대로 이벤트를 실시간으로 캡처할 수 있습니다.

> [!NOTE]
> 이 방법은 추가 분석을 위해 ETL 파일을 생성 하지 않지만 최소한의 설치를 요구 합니다.

## <a name="use-function-calls"></a>함수 호출 사용

응용 프로그램에서 ETL 파일의 이벤트 또는 함수 호출을 사용 하 여 실시간으로 이벤트를 사용할 수 있습니다.
[여기](https://msdn.microsoft.com/library/windows/desktop/aa363692(v=vs.85).aspx)에서 이러한 함수를 사용 하는 방법을 알아보세요.
