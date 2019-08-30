---
title: Arduino 배선 프로젝트 가이드
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Windows IoT Core를 사용 하 여 Arduino 배선 프로젝트를 만들고, 설치 하 고, 배포 하는 방법에 대해 알아봅니다.
keywords: windows iot, Arduino, Arduino 배선, 라이트닝 성능, Visual Studio
ms.openlocfilehash: 7c5e51efd20de014af4533587fbe6f210140b793
ms.sourcegitcommit: cbea9d713986fbe8b85e1bba1561a000188bd91c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64744811"
---
# <a name="arduino-wiring-project-guide"></a>Arduino 배선 프로젝트 가이드

> [!IMPORTANT]
> Windows 10 IoT 팀은 더 이상 Arduino를 적극적으로 유지 관리 하지 않습니다.

이 가이드는 Windows IoT Core를 사용 하 여 Arduino 배선 프로젝트를 만들고, 설치 하 고, 배포 하는 과정을 안내 합니다.

Arduino 배선 프로젝트는 친숙 하 고 사용 하기 쉬운 Arduino 배선 API를 사용 하 여 Windows IoT 번개 드라이버: 직접 메모리 매핑을 사용 하는 드라이버로 상당한 [성능 속도](../develop-your-app/LightningPerformance.md)를 제공 합니다. Arduino 스케치 및 라이브러리를 복사 하 & IoT Core Arduino 배선 프로젝트에 붙여 넣고 Raspberry Pi2, 3 및 Minnowboard Max를 비롯 한 지원 되는 IoT Core 장치에서 실행할 수 있습니다. 자세한 내용은이 페이지의 개발 섹션을 참조 하세요.

## <a name="install-the-microsoft-iot-templates"></a>Microsoft IoT 템플릿 설치

> [!NOTE]
> VS 2015를 다운로드 하 여 Arduino 배선 템플릿에 액세스-이 템플릿은 VS 2017 이상에서 지원 되지 않습니다.

Arduino 배선 프로젝트 뿐만 아니라 다른 Microsoft IoT 프로젝트 형식에 대 한 VS 템플릿을 자동으로 설치 하는 Visual Studio 확장을 제공 했습니다. 

- [Windows IoT Core 프로젝트 템플릿 확장 페이지로](https://go.microsoft.com/fwlink/?linkid=847472) 이동 하 여 Visual Studio 갤러리에서 확장을 다운로드 합니다.
- 확장을 설치 하 고 Visual Studio가 이미 열려 있는 경우 다시 시작 합니다.

## <a name="change-the-default-controller-driver"></a>기본 컨트롤러 드라이버 변경

Arduino 배선 솔루션을 쓰려면 직접 메모리 매핑된 드라이버를 실행 해야 합니다. 지침은 [번개 설정 가이드](../develop-your-app/LightningSetup.md) 를 참조 하세요.

## <a name="develop"></a>개발
[샘플 페이지](https://developer.microsoft.com/en-us/windows/iot/samples)의 "배선" 샘플 중 하나를 완료 하거나 고유한 프로젝트를 빌드합니다. Arduino 배선을 사용 하 여 작성 된 샘플은 다음과 같이 나열 됩니다. [Blinky (배선)](https://developer.microsoft.com/en-us/windows/iot/samples/helloblinkybackgroundwiring). Blinky, IoT 프로젝트용 cononical "Hello World" 프로젝트는 첫 번째 프로젝트를 시작할 수 있는 좋은 장소입니다.

### <a name="create-a-new-project"></a>새 프로젝트 만들기
1. Visual Studio를 엽니다.

2. 파일-> 새로 만들기-> 프로젝트 ...를 선택 합니다.

3. 표시 되는 대화 상자에서 다음을 선택 합니다.  
Visual C++ > windows-Windows iot core > Windows iot core 용 > Arduino 배선 응용 프로그램  
(대신에 표시 될 수 있음)  
Visual C++ > Windows iot Core-Windows iot core 용 > Arduino 배선 응용 프로그램 


![앱 만들기](../media/ArduinoWiring/appcreate.png)

### <a name="porting"></a>포팅

Arduino 배선 API는 라이브러리 및 스케치를 Arduino 배선 프로젝트에 복사 하 여 붙여 넣을 수 있도록 신중 하 게 구현 되었습니다. 그럼에도 불구 하 고 일부 경우에는 스케치 또는 라이브러리에 대해 약간의 수정이 필요할 수 있습니다. 이러한 잠재적인 문제를 다루기 위해 [Arduino 배선 포팅 가이드](ArduinoWiringPortingGuide.md) 를 쉽게 수행할 수 있습니다.

## <a name="build-and-deploy"></a>빌드 및 배포

- Visual Studio에서 "원격 컴퓨터"가 배포 대상으로 선택 되어 있는지 확인 합니다.
- 또한 프로젝트를 실행 하는 보드와 일치 하도록 아키텍처가 설정 되었는지 확인 합니다. Raspberry Pi 2 또는 3의 경우 "ARM"을 선택 하 고 Minnowboard Max의 경우 "x86"을 선택 합니다.

![원격 컴퓨터](../media/ArduinoWiring/wiringapp_remotemachine.png)

- Visual Studio의 디버그 상황에 맞는 메뉴에 있는 솔루션 속성을 엽니다.

![솔루션 속성](../media/ArduinoWiring/wiringapp_properties.png)

- 장치의 IP 주소 또는 컴퓨터 이름을 찾습니다. Windows 10 IoT Core 대시보드 응용 프로그램을 사용 하거나 장치를 모니터에 연결 합니다.
- 컴퓨터 이름 (기본적으로 minwinpc) 또는 원격 컴퓨터의 IP 주소를 ' 컴퓨터 이름 ' 필드에 입력 합니다. ' Minwinpc ' 이외의 이름으로 장치 이름을 변경한 경우 대신 로그인 상자에서 해당 이름을 사용 합니다.
- Authentican 형식 인지 확인 합니다. 유니버설 (암호화 되지 않은 프로토콜)

![솔루션 속성](../media/ArduinoWiring/wiringapp_properties2.png)

- F5 키를 눌러 프로젝트를 빌드하고 장치에 배포 합니다.
