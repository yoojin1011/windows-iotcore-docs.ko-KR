---
title: Computer Vision
ms.date: 08/28/2017
ms.topic: article
description: IoT 장치에 대해 마이크로 Osft Cognitive Services 및 OpenCV를 사용 하는 방법에 대해 알아봅니다.
keywords: windows iot, 컴퓨터 비전, Cognitive Services, OpenCV
ms.openlocfilehash: 74e4ee1303a9c59461f12b59f141c0f7b97d26db
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918187"
---
# <a name="computer-vision"></a>Computer Vision

어떤 사람이 상대적으로 3 차원 세계를 용이 하 게 합니다. 초기 시대에서 시작 하 여 brains는 기능 식별, 장애물 방지, 조정, 깊이 인식 등을 비롯 한 유용한 정보를 visual stimuli에서 수집할 수 있습니다. 컴퓨터 비전은 프로세서와 카메라를 사용 하 여 동일한 작업을 수행 하려고 합니다. 오늘날의 장치에는 수많은 응용 프로그램이 있습니다. 드 론은 비행 중에이를 사용 하 여 신속 하 게 장애를 감지 하 고 피할 수 있습니다. 팩터리는이를 사용 하 여 어셈블리 줄의 가장 작은 구성 요소에서 외관상 결함을 검색할 수 있습니다. 그리고 사용자는 모니터 또는 의사 장비를 사용 하지 않고 하트 요금을 검색 하는 데 사용할 수 있습니다. 데이터 중심 세계는 컴퓨터 비전을 매우 활발 한 연구 영역으로 만들었습니다. 회사는 10 년 전까지 희박 하지만 발생할 간주 되는 방식으로 활용 하 고 있습니다. 컴퓨터, 카메라 및 데이터가 사회에서 더 세분화 되 면 컴퓨터의 시각 효과를 활용 하는 도구는 쉽게 액세스 하 고 사용할 수 있도록 해야 합니다. Windows 10 IoT Core는 두 가지 제공 (Microsoft Cognitive Services 및 OpenCV)과의 호환성을 통해이 요구를 충족 하려고 시도 합니다.

## <a name="services"></a>서비스
___

### <a name="cognitive-services"></a>Cognitive Services

#### <a name="overview"></a>개요
Cognitive Services, 원래 Project Oxford 라는 Microsoft Research 프로젝트는 높은 수준의 "인지 작업"을 수행 하는 Api 컬렉션입니다. 이러한 Api는 Microsoft Research에서 몇 년간의 탐색 및 개발으로 학습 된 기계 학습 모델을 기반으로 데이터에서 정보를 가져옵니다.

Cognitive Services은 비전, 음성, 언어, 지식 및 검색의 5 가지 범주로 구성 됩니다.

Cognitive Services [웹 사이트](https://www.microsoft.com/cognitive-services)에서 Cognitive Services에 대 한 자세한 정보를 찾을 수 있습니다.

컴퓨터 비전 응용 프로그램에 가장 중요 한 범주인 비전 범주에는 Computer Vision, Emotion, 얼굴 및 비디오의 네 가지 Api가 포함 되어 있습니다. 이러한 Api는 다음과 같은 기능을 제공 합니다.
- 얼굴 인식
- 동작 검색
- Emotion 인식
- 비디오 안정화
- 이미지 내용 분석

Cognitive Services은 많은 양의 데이터를 사용 하 고, Microsoft Azure에 액세스 하 고, 비전 Api가 독립적으로 개발 하는 데 많은 시간이 소요 되는 경우가 많기 때문에 응용 프로그램의 출시 시간을 크게 줄이는 데 유용 합니다. 이러한 Api에 사용 되는 모델은 Microsoft Research의 노력 덕분에 잘 학습 하 고 광범위 하 게 사용할 수 있습니다. 반면, 클라우드 연결 요구 사항은 시스템 성능을 줄이고 인터넷 연결에 대 한 요구 사항을 만듭니다.

#### <a name="pricing"></a>가격 책정
각 API 구독은 매월 무료 트랜잭션 집합 (API에 따라 300 ~ 3만)으로 제공 됩니다. 이 초기 금액을 초과 하면 서비스는 적절 한 가격으로 제공 됩니다. 예를 들어 Emotion API는 처음 3만 개 트랜잭션을 무료로 제공 하 고, 구독 유형에 따라 $0.10 또는 $0.25 이후 모든 1000 트랜잭션이 필요 합니다.

Cognitive Services 가격에 대 한 자세한 내용은 해당 [웹 사이트](https://www.microsoft.com/cognitive-services/en-us/pricing)에 있습니다.

#### <a name="get-started"></a>시작하기를
Cognitive Services를 사용 하려면 사용자가 API 키를 수신 하기 위해 Congitive Services 웹 사이트에 등록 해야 합니다. Cognitive Services에 대 한 API 키를 제공 하면 사용자는 "가격 책정" 섹션에서 언급 한 제한 내에서 Api를 호출할 수 있습니다.

각 API에 대 한 설명서는 Cognitive Services [웹 사이트](https://www.microsoft.com/cognitive-services/en-us/documentation)에서 찾을 수 있습니다.

모든 Cognitive Services API는를 사용 하 C#는 모든 하드웨어 플랫폼에서 구현할 수 있습니다.

IoT 장치에서 Cognitive Services를 실행 하 시겠습니까? [자습서](https://developer.microsoft.com/en-us/windows/iot/samples/cognitiveservices) 를 방문 하 여 시작 하세요.

### <a name="opencv"></a>OpenCV

OpenCV는 컴퓨팅 효율성 및 실시간 응용 프로그램을 위해 설계 된 오픈 소스 컴퓨터 비전 및 기계 학습 소프트웨어 라이브러리입니다. 이 기능은 전례 없는 효율성, 다양 한 플랫폼에 대 한 지원, 다양 한 플랫폼에 대 한 지원 및 개발자를 위한 생생한 온라인 커뮤니티 덕분에 개발자와 업계 간에 널리 사용 됩니다. 가장 인기 있는 오픈 소스 컴퓨터 비전 도구입니다. OpenCV 라이브러리는 C/C++, Java 및 C#에 사용할 수 있습니다.

OpenCV [웹 사이트](http://opencv.org/) 는 추가 세부 정보를 제공 합니다.

OpenCV 기능:
- 로컬 이미지 및 비디오 처리 및 분석
- 실시간 개체 식별, 일치 및 추적
- 실시간 얼굴 인식
- 이미지 및 실시간에서의 거리 결정
- 3D 매핑/모델링/재구성
- 이미지 편집 (예: 컴퍼지션 및 색 변경)

OpenCV는 다양 한 이점을 제공 합니다. OpenCL (사용 하도록 설정 된 경우)를 사용 하 여 최적화 된C++ C/내부 및 GPU에 대 한 액세스로 인해 로컬 데이터를 처리 하는 것이 매우 효율적입니다. 이 파일에는 대부분의 경우 대부분의 컴퓨터 비전 기능을 사용할 수 있습니다. 수명 및 유틸리티는 응용 프로그램 또는 라이브러리 문제를 해결 하는 새로운 사용자에 게 도움이 될 수 있는 광범위 하 고 숙련 된 온라인 커뮤니티를 형성 했습니다. 반면에 복잡 한 코드와 라이브러리 설정 및 자습서 및 샘플 코드의 불일치 때문에 깊은 학습 곡선이 있습니다.

현재, 사용자가 원본에서 라이브러리를 빌드하는 경우에만 IoT Core로 OpenCV를 사용할 수 있으며,이는 시간이 많이 걸릴 수 있습니다. 이로 인해이에 대 한 NuGet 패키지의 컬렉션을 만들어 IoT Core에서 쉽게 설정할 수 있도록 노력 하 고 있습니다. Cognitive Services에서 사용 하는 NuGet 패키지를 통해 개발자는 미리 빌드된 라이브러리를 응용 프로그램으로 가져와 몇 번의 클릭 만으로 전체 기능을 제공할 수 있습니다. NuGet 패키지를 사용 하는 응용 프로그램은 계속 해 서 전용 서버에서 라이브러리 업데이트를 받습니다. 오픈 소스 소프트웨어에 대 한 공용 변경 내용이 있는 경우 사용자는 새 소스 코드를 다시 빌드할 필요가 없습니다. 또한 패키지는 라이브러리 파트를 사용 하는 장치 에서만 저장소 공간을 확보 합니다.

현재 진행 중인 작업 이므로 WindowsOnDevices.com 업데이트를 계속 확인 하세요.

한편 ARM의 원본에서 라이브러리를 빌드하려면 [GitHub 리포지토리](https://github.com/Microsoft/opencv/tree/vs2015-samples-ARM)를 방문 하세요.

IoT Core 장치에서 OpenCV를 실행 하 고 싶으세요? [자습서](https://developer.microsoft.com/en-us/windows/iot/samples/opencv) 를 방문 하 여 시작 하세요.

## <a name="comparing-opencv-and-cognitive-services"></a>OpenCV와 Cognitive Services 비교

> |        |Microsoft Cognitive Services|OpenCV|
> |---------------------|--------|------|
> |Windows에서 사용 하기 쉬운 방법|예|아니요 |
> |아키텍처 지원|ARM, x86, x64 | ARM, x86, x64|
> |얼굴 인식 및 추적| 예 | 예|
> |Emotion 인식| 예 | 예|
> |3D 재구성 및 매핑| 아니요 | 예|
> |콘텐츠 검색| 특정 개체가 아닌 일반 기능을 검색 합니다. | 예|
> |비디오 안정화| 예 | 예|
> |동작 검색| 예 | 예|
> |커뮤니티| How-old.net 및 celebslike.me를 포함 하 여 여러 산업 및 널리 사용 되는 웹 사이트에서 많은 활성 사용자가 Cognitive Services | OpenCV는 매우 인기 있는 오픈 소스 프로젝트입니다. 수천 명의 사용자가이를 기고 하 고 유지 관리|
> |설명서| 전체 투명 하 고 광범위 한 설명서가 Cognitive Services | 온라인에서 사용할 수 있는 여러 샘플이 있지만 각 샘플은 다른 사용자가 작성 한 것 이므로 때때로 일치 하지 않을 수 있습니다.|
> |무료| 예, 익스텐트 (자세한 내용은 [여기](https://azure.microsoft.com/pricing/details/cognitive-services/)참조) | 예|
> |성능| 모든 작업 및 API 호출에서 클라우드의 데이터에 액세스 해야 함 | 모든 알고리즘은 최적화 되 고 로컬 이며 Python C++ 이 아닌를 사용 하면 속도가 훨씬 빨라집니다.|
> |지원 되는 카메라/하드웨어| 모든 USB 또는 임베디드 카메라 | 모든 USB 또는 임베디드 카메라|
> |지원 되는 언어/프레임 워크| C#, UWP | C/C++, Python, Java, C#, UWP|
> |시작 시간| 사용자는 설명서에서 직접 직관적인 Api와 함께 코드 샘플을 사용할 수 있습니다. | OpenCV의 능력과 유연성은 복잡 한 작업을 수행 하기 위한 많은 구성 및 코드가 필요 함을 의미 합니다.|
> |링크| [샘플 프로그램](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/CognitiveServicesExample) | [샘플 프로그램](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/OpenCVExample) |
> |    |   [웹 사이트 Cognitive Services](https://azure.microsoft.com/services/cognitive-services/) |  [OpenCV 웹 사이트](http://opencv.org/)


