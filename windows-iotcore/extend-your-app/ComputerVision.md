---
title: Computer Vision
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Microosft Cognitive Services 및 OpenCV IoT 장치를 사용 하는 방법을 알아봅니다.
keywords: windows iot, 컴퓨터 비전, Cognitive Services, OpenCV
ms.openlocfilehash: f6d10024f0f52f7219eb3a63dcefa7fd2b4a6fe3
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512678"
---
# <a name="computer-vision"></a>Computer Vision

사용자는 상대적인 편의성에 3 차원 세계 인식할. 무언가 사고할 이른에서 시작 하며, 기능 식별, 장애물 방지, 조정, 깊이 인식 및 기타 여러 visual의에서 포함 하 여 중요 한 정보를 수집할 수 있습니다. 컴퓨터 비전은 프로세서 및 카메라를 사용 하 여 동일한 작업을 수행 하려고 합니다. 오늘날의 장치에 수많은 응용 프로그램이 있습니다. 드 론을 신속 하 게 감지 하 고 비행; 중 장애를 방지 하는 데 사용할 수 있습니다. 팩터리 디자인 결함 어셈블리 라인;에 가장 작은 구성 요소를 검색 하는 데 사용할 수 있습니다. 및 사용자 모니터 또는 의사의 장비를 사용 하지 않고 자신의 핵심 속도 검색 하는 데 사용할 수 있습니다. 데이터 중심 세계는 매우 활발 한 연구 영역 비전 컴퓨터를 만들었습니다. 회사는 현실성이 10 년 전에 것으로 간주 하는 방법으로를 활용 합니다. 컴퓨터, 카메라 및 데이터에는 더 배어 됩니다,으로 컴퓨터 비전 가장 흥미로운 기능을 활용 하는 도구 이루어져야 쉽게 액세스 하 고 최대한 사용 합니다. Windows 10 IoT Core 두 가지 제품을 사용 하 여 호환성을 통해 이러한 요구를 충족 하려고 합니다. Microsoft Cognitive Services 및 OpenCV 합니다.

## <a name="services"></a>서비스
___

### <a name="cognitive-services"></a>Cognitive Services

#### <a name="overview"></a>개요
Cognitive Services, 원래 Microsoft 연구 프로젝트 Project Oxford 호출를 상위 수준 "cognitive 작업"을 수행 하는 Api 모음입니다. 이러한 Api는 항상 학습 된 기계 학습 년 간 탐색 및 Microsoft Research에서 개발에서에서 모델 기반 데이터에서 통찰력을 끌어옵니다.

Cognitive Services는 5 개 범주의 구성 됩니다. 시각, 음성, 언어, 지식 및 검색 합니다.

Cognitive Services에서 Cognitive Services에 대 한 자세한 정보를 찾을 수 있습니다 [웹 사이트](https://www.microsoft.com/cognitive-services)합니다.

비전 범주, 컴퓨터 비전 응용 프로그램에 대 한 가장 중요 한 범주에는 네 가지 Api 포함 됩니다. Computer Vision, Emotion, 얼굴, 및 비디오입니다. 이러한 Api는 다음과 같은 기능을 제공합니다.
- 얼굴 인식
- 동작 감지
- 감정 인식
- 비디오 안정화
- 이미지 콘텐츠 분석

Cognitive Services는 많은 양의 데이터를 사용 하기 위한 유용한 Microsoft Azure에 액세스 하 고 독립적으로 개발 하는 많은 시간이 소요 되도록 응용 프로그램의 시간 시장 진출, 종종 Vision Api와 증명할 수를 크게 줄일 합니다. 이러한 Api에 사용 된 모델은 교육 및 광범위 한 감사 인사를 전 Microsoft Research의 노력 합니다. 반면에 해당 클라우드 연결 요구 사항 시스템 성능이 저하 하 고 인터넷에 연결에 대 한 요구 사항을 만듭니다.

#### <a name="pricing"></a>가격 책정
각 API 구독 매월 (300에 30,000 API에 따라) 무료 트랜잭션 집합이 포함 되어 있습니다. 이 초기 용량을 초과한 후 서비스는 적절 한 가격을 함께 제공 됩니다. 예를 들어, Emotion API는 먼저 30,000 개의 트랜잭션을 무료로 제공 하 고 0.10 달러 또는 $0.25가 구독에 따라 그 후 마다 1000 트랜잭션 유형 필요 합니다.

Cognitive Services 가격 책정에 대 한 자세한 내용은에서 발견 된 해당 [웹 사이트](https://www.microsoft.com/cognitive-services/en-us/pricing)합니다.

#### <a name="get-started"></a>시작
Cognitive Services를 사용 하 여 사용자 등록 해야 합니다 Congitive Services 웹 사이트에서 API 키를 받을 수 있습니다. Cognitive Services에 API 키를 입력 한 후 사용자는 "가격" 섹션에 설명 된 제한 내에서 Api를 호출할 수 있습니다.

Cognitive Services에서 각 API에 대 한 설명서를 찾을 수 있습니다 [웹 사이트](https://www.microsoft.com/cognitive-services/en-us/documentation)합니다.

모든 Cognitive Services Api를 사용 하 여 모든 하드웨어 플랫폼에서 구현할 수 있습니다 C#입니다.

IoT 장치에서 Cognitive Services를 실행 하 시겠습니까? 방문 우리의 [자습서](https://developer.microsoft.com/en-us/windows/iot/samples/cognitiveservices) 를 시작 합니다.

### <a name="opencv"></a>OpenCV

OpenCV는 오픈 소스 컴퓨터 비전 및 기계 학습 계산 효율성과 실시간 응용 프로그램을 위한 소프트웨어 라이브러리입니다. 것 및 업계의 전례 없는 효율성, 다양 한 도구, 다양 한 플랫폼에 대 한 지원으로 인해 개발자 들 사이에서 널리 사용 되 고 활발 한 온라인 개발자 커뮤니티의 광범위 하 게 합니다. 가장 인기 있는 오픈 소스 컴퓨터 비전 도구입니다. OpenCV 라이브러리는 C에 사용할 수 있는 /C++, Java, 및 C#합니다.

OpenCV [웹 사이트](http://opencv.org/) 추가 정보를 제공 합니다.

OpenCV 기능은 다음과 같습니다.
- 로컬 이미지 및 비디오 처리 및 분석
- 실시간으로 개체 id, 일치 및 추적
- 실시간으로 얼굴 인식
- 이미지에서 실시간 거리 결정
- 3D 매핑/모델링/재구성
- 이미지 (예: 컴퍼지션 및 색 변경) 편집

OpenCV 여러 장점을 제공합니다. 이 오류의 원인은 로컬 데이터 처리에 매우 효율적으로 최적화 된 C /C++ 내부 및 OpenCL (설정 된 경우)를 사용 하 여 GPU에 대 한 액세스. 포함 대부분 경우 항상 그렇지는 않지만 현재 사용할 수 있는 컴퓨터 비전 기능 합니다. 해당 수명 및 유틸리티가 광범위 하 고 숙련 된 온라인 커뮤니티 응용 프로그램 또는 라이브러리 문제를 사용 하 여 새 사용자가 도움이 되는 구성 합니다. 반면에 자습서 및 샘플 코드에서 배우기 불일치 뿐만 아니라 복잡 한 코드 및 라이브러리 설치로 인해 됩니다.

현재 OpenCV IoT Core를 사용 하 여 사용자가 시간이 많이 걸릴 수 있는 원본에서 라이브러리를 빌드할 경우에 작동 합니다. 이 인해는 OpenCV를 보다 쉽게에 대 한 NuGet 패키지의 컬렉션을 만들어 IoT Core를 설정 하기 위해 적극적으로 노력 합니다. Cognitive Services를 사용 하는 NuGet 패키지를 개발자가 몇 번의 클릭으로 전체 기능을 제공 하는 응용 프로그램에 미리 빌드된 라이브러리를 가져올 수 있습니다. NuGet 패키지를 사용 하 여 응용 프로그램 업데이트를 받는 라이브러리는 전용된 서버에서 계속 합니다. 사용자는 오픈 소스 소프트웨어를 공개 변경 될 때 새 소스 코드를 다시 작성할 필요가 없습니다. 또한 패키지를 사용 하 여 저장소 공간을에 라이브러리의 일부를 사용 하 여 장치 필요가 없습니다.

이 현재 진행 중인 작업, 되므로 계속 WindowsOnDevices.com 업데이트 확인!

그동안 ARM에 대 한 원본에서 라이브러리를 빌드, 방문 합니다 [GitHub 리포지토리](https://github.com/Microsoft/opencv/tree/vs2015-samples-ARM)합니다.

OpenCV IoT Core 장치에서 실행 하 시겠습니까? 방문 우리의 [자습서](https://developer.microsoft.com/en-us/windows/iot/samples/opencv) 를 시작 합니다.

## <a name="comparing-opencv-and-cognitive-services"></a>OpenCV 및 Cognitive Services 비교

> |        |Microsoft Cognitive Services|OpenCV|
> |---------------------|--------|------|
> |Windows에서 사용 하기 쉬운|예|아니요 |
> |아키텍처 지원|ARM, x86, x64 | ARM, x86, x64|
> |얼굴 인식 및 추적| 예 | 예|
> |감정 인식| 예 | 예|
> |3D 재구성 및 매핑| 아니요 | 예|
> |콘텐츠 검색| 특정 개체 대신 일반 기능 검색 | 예|
> |비디오 안정화| 예 | 예|
> |동작 감지| 예 | 예|
> |커뮤니티| Cognitive Services 여러 산업 및 몇 가지 인기 있는 웹 사이트 how-old.net 등 celebslike.me 간에 활성 사용자 수에 | OpenCV는 매우 인기 있는 오픈 소스 프로젝트; 수천 명이에 제공한 있고이 유지 관리|
> |설명서| Cognitive Services에는 전체 명확 하 고 광범위 한 설명서 | 샘플이 사용 가능한 온라인 있지만 각 샘플 다른 사용자가 기록 되 고 결과적으로 수 일관 된 시간에|
> |무료| 익스텐트를 예 (자세한 내용은 [여기](https://azure.microsoft.com/pricing/details/cognitive-services/)) | 예|
> |성능| 모든 작업 및 API 호출, 클라우드에서 데이터 액세스 필요 | 모든 알고리즘은 최적화 하 고 로컬을 사용 하 여 C++ Python 증가 속도 더 많은 것이 아니라|
> |지원 되는 카메라/하드웨어| 모든 USB 또는 포함 된 카메라 | 모든 USB 또는 포함 된 카메라|
> |지원 되는 언어/프레임 워크| C#, UWP | C /C++, Python, Java, C#, UWP|
> |시작 시간| 사용자는 설명서에서 직접 직관적인 Api와 함께 코드 샘플을 사용할 수 있습니다. | OpenCV의 강력 함과 유연함 의미도 많은 복잡 한 작업을 수행 하는 코드 및 구성 필요|
> |링크| [샘플 프로그램](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/CognitiveServicesExample) | [샘플 프로그램](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/OpenCVExample) |
> |    |   [Cognitive Services 웹 사이트](https://azure.microsoft.com/services/cognitive-services/) |  [OpenCV 웹 사이트](http://opencv.org/)


