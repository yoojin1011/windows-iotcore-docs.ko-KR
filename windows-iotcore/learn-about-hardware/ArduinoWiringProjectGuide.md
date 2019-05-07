---
title: Arduino 배선 프로젝트 가이드
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 만들기, 설정 및 Windows IoT Core를 사용 하 여 Arduino 연결 프로젝트의 배포에 알아봅니다.
keywords: windows iot에 Arduino, Arduino 연결, 번개 성능, Visual Studio
ms.openlocfilehash: 7c5e51efd20de014af4533587fbe6f210140b793
ms.sourcegitcommit: cbea9d713986fbe8b85e1bba1561a000188bd91c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64744811"
---
# <a name="arduino-wiring-project-guide"></a>Arduino 배선 프로젝트 가이드

> [!IMPORTANT]
> Windows 10 IoT 팀은 더 이상 적극적으로 Arduino 유지 관리 합니다.

이 가이드는 만들기, 설정 및 Windows IoT Core를 사용 하 여 Arduino 연결 프로젝트의 배포를 단계별로 안내 합니다.

프로젝트 Arduino 연결, 친숙 하 고 사용 하기 쉬운 Arduino 연결 API 활용 Windows IoT 번개 DMAP 드라이버로: 중요 한 있도록 직접 메모리 매핑을 사용 하 여 드라이버 [성능 속도](../develop-your-app/LightningPerformance.md)합니다. 복사 하 & IoT Core Arduino 연결 프로젝트로 Arduino 스케치 및 라이브러리를 붙여, 3 및 Minnowboard Max Raspberry Pi2를 비롯 한 장치를 지원 되는 IoT Core에서 실행할 수 있습니다! 자세한 내용은이 페이지의 개발 섹션을 참조 하세요.

## <a name="install-the-microsoft-iot-templates"></a>Microsoft IoT 템플릿 설치

> [!NOTE]
> 템플릿 Arduino 연결-이러한 템플릿에 액세스 하려면 VS 2015 다운로드는 VS 2017 이상 지원 되지 않습니다 loner입니다.

Arduino 연결 프로젝트 뿐만 아니라 다른 Microsoft IoT 프로젝트 형식에 대 한 VS 템플릿을 자동으로 설치 하는 Visual Studio 확장을 제공 했습니다. 

- 로 이동 [Windows IoT Core 프로젝트 템플릿에 확장 페이지](https://go.microsoft.com/fwlink/?linkid=847472) Visual Studio 갤러리에서 확장을 다운로드 하려면!
- 확장을 설치 하 고 이미 열려 있으면 Visual Studio를 다시 시작

## <a name="change-the-default-controller-driver"></a>기본 컨트롤러 드라이버 변경

Arduino 연결 솔루션을 작성 하려면 직접 메모리 매핑된 드라이버가 실행 해야 합니다. 참조 된 [번개 설치 가이드](../develop-your-app/LightningSetup.md) 지침은!

## <a name="develop"></a>개발
"연결" 샘플 중 하나를 완료 합니다 [샘플 페이지](https://developer.microsoft.com/en-us/windows/iot/samples), 고유한 프로젝트를 빌드하거나! 나열 될 Arduino 연결을 사용 하 여 작성 된 샘플 만들었습니다 다음과 같이 합니다. [쳐다 (연결)](https://developer.microsoft.com/en-us/windows/iot/samples/helloblinkybackgroundwiring)합니다. 쳐다, IoT 프로젝트용 cononical "Hello World" 프로젝트가 되었습니다. 첫 번째 프로젝트에 대 한 시작 하기에 적합

### <a name="create-a-new-project"></a>새 프로젝트 만들기
1. Visual Studio를 엽니다.

2. 파일 선택-> 새로 만들기-> 프로젝트...

3. 나타나는 대화 상자에서 다음을 선택 합니다.  
Visual C++ -> Windows-Windows > IoT Core에 Windows IoT Core에 대 한 응용 프로그램을 연결 하는 Arduino->  
(대신 나타날으로)  
Visual C++ Windows-> IoT Core에 Windows IoT Core에 대 한 응용 프로그램을 연결 하는 Arduino-> 


![앱 만들기](../media/ArduinoWiring/appcreate.png)

### <a name="porting"></a>포팅

Arduino 연결 API로 복사/붙여넣기 라이브러리 및 스케치를 Arduino 연결 프로젝트로 수 있도록 신중 하 게 구현 되었습니다. 그럼에도 불구 하 고,에 경우에 따라 약간의 수정을 스케치 나 라이브러리 할 수 있습니다. 따라 하기 쉬운 만들었습니다 [Arduino 연결 포팅 가이드](ArduinoWiringPortingGuide.md) 이러한 잠재적인 문제를 처리 하기 위해.

## <a name="build-and-deploy"></a>빌드 및 배포

- Visual Studio에서 "원격 컴퓨터가" 배포 대상으로 선택 되어 있는지를 확인 합니다.
- 또한 아키텍처에서 프로젝트를 실행 하는 보드를 일치 하도록 설정 되어 있는지 확인 합니다. Raspberry Pi 2 또는 3에 대 한 "ARM"를 선택 하 고 Minnowboard 최대 "x86"를 선택 합니다.

![원격 컴퓨터](../media/ArduinoWiring/wiringapp_remotemachine.png)

- Visual Studio에서 디버그 상황에 맞는 메뉴에 있는 솔루션 속성을 엽니다.

![솔루션 속성](../media/ArduinoWiring/wiringapp_properties.png)

- 장치의 IP 주소 또는 컴퓨터 이름을 찾습니다. Windows 10 IoT Core 대시보드 응용 프로그램을 사용 하거나 모니터를 장치에 연결 합니다.
- 'Machine name' 필드에 컴퓨터 이름 (기본적으로 minwinpc) 또는 원격 컴퓨터의 IP 주소를 입력 합니다. 변경한 경우 장치를 'minwinpc' 대신 해당 이름을 로그인 상자 외에 있습니다.
- Authentican 형식이 확인 합니다. 유니버설 (암호화 되지 않은 프로토콜)

![솔루션 속성](../media/ArduinoWiring/wiringapp_properties2.png)

- F5 키를 눌러를 장치에서 프로젝트를 빌드하여 배포 합니다.
