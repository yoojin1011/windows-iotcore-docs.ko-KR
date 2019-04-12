---
title: Windows IoT Core에 대 한 이벤트 추적
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 이벤트를 작성 하 고 Windows IoT Core에 대 한 이벤트를 사용할 이벤트 추적을 사용 하는 방법에 알아봅니다.
keywords: windows iot 장치 windows 용 이벤트 추적, ETW, 이벤트 추적
ms.openlocfilehash: 7e01681e2af2ed8913614ba23bd12dfd36bcd76e
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59515194"
---
# <a name="event-tracing-for-windows-iot-core"></a>Windows IoT Core에 대 한 이벤트 추적

이벤트 추적에 대 한 Windows (ETW) 개발자 시작 및 추적 이벤트를 제공 하 고 추적 이벤트를 사용 하려면 응용 프로그램 계측 이벤트 추적 세션을 중지 하는 기능을 제공 합니다.
Windows IoT Core 장치에서 ETW 매니페스트 기반 및 클래식 이벤트를 지원 하며 다른 Windows 10 장치에 차이가 없습니다.

이 섹션에서는 작성 하 고 이벤트의 기본 사항에 대 한 유용한 링크를 제공 합니다. 자세한 정보를 찾을 합니다 [Windows 이벤트 추적 페이지](https://msdn.microsoft.com/library/windows/desktop/bb968803(v=vs.85).aspx)합니다.

## <a name="writing-events"></a>쓰기 이벤트

이벤트의 일부로 작성 하는 다른 메서드를 구현 하는 UWP 샘플 찾기 합니다 [Windows 유니버설 샘플 Github](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/Logging)합니다.
이 Windows IoT Core 장치에서 실행 되 고 훌륭한 코드 참조 이기도.

이벤트를 작성 하 고 Guid 가져오기에 대 한 자세한 가이드를 찾을 수 있습니다 [여기](https://msdn.microsoft.com/library/windows/desktop/aa364161(v=vs.85).aspx)합니다.

## <a name="consuming-events"></a>이벤트 사용

이벤트는 ETL 파일에 저장 또는 실시간에 캡처됩니다.
사용 하 여 [FTP](../connect-your-device/FTP.md) 하거나 [Windows 파일 공유](../manage-your-device/WindowsFileSharing.md) Windows IoT Core 장치에서 ETL 파일을 검색 합니다.

## <a name="use-tools-in-windows-assessment-and-deployment-kit"></a>Windows 평가 및 배포 키트의 도구를 사용 합니다.

Windows Assessment and Deployment Kit를 캡처 및 이벤트를 분석 하는 데 3 도구를 포함 합니다. [다운로드 하려면 여기를 클릭 합니다.](http://go.microsoft.com/fwlink/p/?LinkId=526740)


1. **Windows Performance Analyzer** 단계별 가이드를 사용 하 여 바탕 화면에서 ETL 파일을 시각화 [여기](https://msdn.microsoft.com/library/windows/hardware/dn927319(v=vs.85).aspx)합니다.

2. **Xperf 명령줄 도구** 실시간 이벤트를 캡처하고 ETL 파일에 씁니다. 이 도구에 이미 설치 되어 Windows IoT Core 장치, 장치에서 다음 명령을 실행 합니다.

        // Start capturing events from specific GUID and save them to an ETL file
        xperf -start <Session Name> -f <ETL File> -on <GUID>

        // Stop capturing events with the specified session name
        xperf -stop <Session Name>


3. **Tracerpt 명령줄 도구** ETL 파일을 xml 파일로 변환 합니다.

        // Generate dumpfile.xml from ETL file
        tracerpt <ETL File>


## <a name="use-device-portal"></a>장치 포털 사용

장치 포털에서 이벤트를 캡처할 수 지침을 사용 하 여 실시간 [여기](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal)합니다.

> [!NOTE]
> 이 메서드 추가 분석을 위해 ETL 파일을 생성 하지 않지만 최소 설정이 필요 합니다.

## <a name="use-function-calls"></a>사용 하 여 함수 호출

함수 호출을 사용 하는 ETL 파일에서 또는 실시간 이벤트를 사용 하는 응용 프로그램 사용 합니다.
이러한 함수를 사용 하는 방법을 알아봅니다 [여기](https://msdn.microsoft.com/library/windows/desktop/aa363692(v=vs.85).aspx)합니다.
