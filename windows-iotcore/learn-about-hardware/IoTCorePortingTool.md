---
title: Windows 10 IoT Core API 포팅 도구
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Windows 10 IoT Core API 포팅 도구를 사용 하 여 이식 비용을 예측 하는 방법에 알아봅니다.
keywords: windows iot, 도구, API 포팅 이진 파일을 이식 하는 API
ms.openlocfilehash: 56ca0d57752f000bf9e908fd32f514c3ae3264e5
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513006"
---
# <a name="windows-10-iot-core-api-porting-tool"></a>Windows 10 IoT Core API 포팅 도구

만 Windows 10 IoT Core 다양 한 이전 버전 Windows의 Win32 및.Net API 노출 영역 중 일부를 지원 합니다. 이 도구를 이진 파일을 검색 하 고 사용할 수 없고 가능한 대체에 대 한 제안을 제공 하는 이러한 이진 파일을 사용 Api에 대 한 보고서를 제공 합니다. 이 둘 다 IoT Core로 이식 비용을 예측에 도움이 뿐만 아니라이 과정에서 도움이 합니다.


## <a name="usage"></a>사용법

Windows 10 IoT Core API 포팅 도구에서 찾을 수 있습니다 합니다 [ms iot/iot 유틸리티](https://github.com/ms-iot/iot-utilities) github 리포지토리.  다운로드 합니다 [리포지토리 zip](https://github.com/ms-iot/iot-utilities/archive/master.zip) IoTAPIPortingTool 폴더를 로컬 컴퓨터에 복사 합니다.  오픈 **IoTAPIPortingTool.sln** Visual Studio 2017에는 프로젝트를 빌드합니다.  이 생성 됩니다 `IotAPIPortingTool.exe`합니다.

도구를 사용 하 여 실행 하 여 `IoTAPIPortingTool.exe <Application path> [-os]`입니다.

*  `<Application path>` 이식 도구에 사용 되는 응용 프로그램의 exe 파일

*  `-os` 지정 해야 UWP 사용할 계획이 없는 경우.  기본적으로 도구는 Windows UWP 플랫폼에 대 한 이진 파일을 확인합니다.

> [!NOTE] 
> IoTAPIPortingTool.exe Visual Studio 개발자 명령 프롬프트에서 실행 되어야 합니다. IotAPIPortingTool.exe 포함 된 폴더로 이동 해야 합니다. 

        Sample command: C:\IoTAPIPortingTool\bin\Debug>IoTAPIPortingTool.exe C:\Sample\Sample.exe -os 

## <a name="output"></a>출력

쉼표로 구분 된 값 (csv) 파일을 포함 하는 동일한 폴더에 생성 됩니다는 `IotAPIPortingTool.exe`합니다. 파일 이름은 `IoTAPIPortingTool.csv` (또는 `IoTAPIPortingToolOS.csv` os 지정 된 경우) 명령줄에서 요약 됩니다. 열기는 `.csv` 전체 출력을 분석 하는 Excel에서 파일입니다.
