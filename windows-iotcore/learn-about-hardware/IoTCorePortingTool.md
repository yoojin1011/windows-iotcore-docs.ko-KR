---
title: Windows 10 IoT Core API 포팅 도구
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Windows 10 IoT Core API 포팅 도구를 사용 하 여 포팅 비용을 예측 하는 방법을 알아봅니다.
keywords: windows iot, API 포팅 도구, API 포팅, 이진 파일
ms.openlocfilehash: 56ca0d57752f000bf9e908fd32f514c3ae3264e5
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "60169631"
---
# <a name="windows-10-iot-core-api-porting-tool"></a>Windows 10 IoT Core API 포팅 도구

Windows 10 IoT Core는 다양 한 이전 버전의 Windows에서 사용할 수 있는 Win32 및 .Net API 노출 영역의 하위 집합만 지원 합니다. 이 도구는 이진 파일을 검사 하 고 이러한 이진 파일이 사용 되지 않는 Api에 대 한 보고서를 제공 하며 가능한 대체 항목에 대 한 제안을 제공 합니다. 이를 통해 IoT 코어에 대 한 포트의 비용을 예측 하 고이에 따라 도움을 받을 수 있습니다.


## <a name="usage"></a>사용법

Windows 10 IoT Core API 포팅 도구는 [ms-iot/iot 유틸리티](https://github.com/ms-iot/iot-utilities) github 리포지토리에서 찾을 수 있습니다.  [리포지토리 zip](https://github.com/ms-iot/iot-utilities/archive/master.zip) 을 다운로드 하 고 IoTAPIPortingTool 폴더를 로컬 컴퓨터에 복사 합니다.  Visual Studio 2017에서 **Iotapiportingtool .sln** 을 열고 프로젝트를 빌드합니다.  그러면이 생성 `IotAPIPortingTool.exe`됩니다.

을 실행 `IoTAPIPortingTool.exe <Application path> [-os]`하 여 도구를 사용할 수 있습니다.

*  `<Application path>`포팅 도구를 사용 하는 응용 프로그램의 exe

*  `-os`UWP를 사용 하지 않으려는 경우에는를 지정 해야 합니다.  기본적으로이 도구는 Windows UWP 플랫폼에 대해 이진 파일의 유효성을 검사 합니다.

> [!NOTE] 
> Visual Studio 개발자 명령 프롬프트에서 IoTAPIPortingTool .exe를 실행 해야 합니다. IotAPIPortingTool .exe를 포함 하는 폴더로 이동 해야 합니다. 

        Sample command: C:\IoTAPIPortingTool\bin\Debug>IoTAPIPortingTool.exe C:\Sample\Sample.exe -os 

## <a name="output"></a>출력

이 도구는를 `IotAPIPortingTool.exe`포함 하는 동일한 폴더에서 csv (쉼표로 구분 된 값) 파일을 생성 합니다. 파일의 이름은로 `IoTAPIPortingTool.csv` 지정 되 고 `IoTAPIPortingToolOS.csv` ,-os가 지정 된 경우에는 명령줄에 요약이 지정 됩니다. Excel에서 `.csv` 파일을 열어 전체 출력을 분석 합니다.
