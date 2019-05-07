---
title: Windows IoT Core 장치에 대 한 Arduino 연결
author: msalehmsft
ms.author: msaleh
ms.date: 09/06/17
ms.topic: article
description: 만들기, 배포 및 지원 되는 Windows IoT Core 장치에 연결 하는 Arduino 스케치를 디버그 하는 방법에 알아봅니다.
keywords: windows iot에 Arduino, Arduino 연결, 템플릿, IoT Core, UWP
ms.openlocfilehash: ee6c64bdfd01e79d26bfa0a6c5f88f7735150393
ms.sourcegitcommit: cbea9d713986fbe8b85e1bba1561a000188bd91c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64744791"
---
# <a name="arduino-wiring-for-windows-iot-core-devices"></a><span data-ttu-id="78b06-104">Windows IoT Core 장치에 대 한 Arduino 연결</span><span class="sxs-lookup"><span data-stu-id="78b06-104">Arduino Wiring for Windows IoT Core Devices</span></span>

> [!IMPORTANT]
> <span data-ttu-id="78b06-105">Windows 10 IoT 팀은 더 이상 적극적으로 Arduino 유지 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="78b06-105">The Windows 10 IoT team is no longer actively maintaining Arduino.</span></span>

<span data-ttu-id="78b06-106">개발 및 친숙 한 다시 사용할 수 있도록 [Arduino 연결](https://www.arduino.cc/en/Reference/HomePage) IoT Core 장치에서 스케치, Arduino 연결에 대 한 Visual Studio 프로젝트 템플릿을의 일부로 제공 되는 [Windows IoT Core 프로젝트 템플릿 확장](https://go.microsoft.com/fwlink/?linkid=847472)합니다.</span><span class="sxs-lookup"><span data-stu-id="78b06-106">To enable the development and reuse of the familiar [Arduino Wiring](https://www.arduino.cc/en/Reference/HomePage) sketches on IoT Core devices, a Visual Studio project template for Arduino Wiring is provided as part of the [Windows IoT Core Project Templates extension](https://go.microsoft.com/fwlink/?linkid=847472).</span></span>

<span data-ttu-id="78b06-107">Arduino 연결 프로젝트 템플릿을 사용 하면 개발자와 작성자를 만들고 배포 하 고 동일한 Arduino 연결 언어 의미 체계를 사용 하 여 지원 되는 IoT Core 장치에 연결 하는 Arduino 스케치를 디버그 하 고 Arduino 플랫폼에서 사용할 수 있습니다 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="78b06-107">The Arduino Wiring project template enables developers and makers to create, deploy and debug Arduino Wiring sketches on supported IoT Core devices using the same Arduino Wiring language semantics and constructs available on Arduino platforms.</span></span> <span data-ttu-id="78b06-108">이 포트 기존 Arduino 스케치 하는 데 도움이 IoT Core 매우 적은 비용으로 할 뿐만 아니라 연결 Arduino 스케치 IoT Core에서 실행 되는 유니버설 Windows 플랫폼 (UWP) API의 사용을 만들 수 있는 전체 Windows 10 앱.</span><span class="sxs-lookup"><span data-stu-id="78b06-108">Not only this can help port existing Arduino sketches to IoT Core with very little cost, but Arduino Wiring sketches running on IoT Core are full Windows 10 apps that can make use of the Univeral Windows Platform (UWP) API.</span></span> <span data-ttu-id="78b06-109">따라서 연결 Arduino 스케치에 완전히 액세스할 Api 통신, 데이터 액세스, 네트워킹, 그래픽 등 많은 다른 Windows 10 IoT Core 장치에서 실행 되는 종단 간 시나리오를 만드는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78b06-109">So, Arduino Wiring sketches have full access to APIs such as communication, data access, networking, graphics, among many others, which can be used to create end to end scenarios running on Windows 10 IoT Core devices.</span></span> <span data-ttu-id="78b06-110">유니버설 Windows 플랫폼 (UWP) 앱 개발에 대 한 자세한 내용은 참조 하십시오 [건물 응용 프로그램에 대 한 Windows 10 IoT Core](../develop-your-app/BuildingAppsForIoTCore.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="78b06-110">For more information on developing Universal Windows Platform (UWP) Apps, please refer to [Building Applications for Windows 10 IoT Core](../develop-your-app/BuildingAppsForIoTCore.md).</span></span>

<span data-ttu-id="78b06-111">또한 지원 되는 장치에 높은 성능을 제공 하는 직접 메모리 매핑된 드라이버의 사용 Arduino 스케치 확인을 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="78b06-111">Additionally, Arduino Wiring sketches make use of a direct memory mapped driver that offers high performance on supported devices.</span></span> <span data-ttu-id="78b06-112">성능 세부 정보에 대 한 자세한 내용은를 참조 하십시오 합니다 [Windows IoT 번개 성능 테스트](../develop-your-app/LightningPerformance.md) 보고서입니다.</span><span class="sxs-lookup"><span data-stu-id="78b06-112">For more details on performance details, please refer to the [Windows IoT Lightning Performance Testing](../develop-your-app/LightningPerformance.md) report.</span></span>

<span data-ttu-id="78b06-113">Minnowboard 최대 Raspberry Pi2, Pi3에 Arduino 연결 프로젝트 빌드를 시작 하려면를 참조 하십시오 합니다 [project 가이드 Arduino 연결](ArduinoWiringProjectGuide.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="78b06-113">To start building Arduino Wiring projects for Raspberry Pi2, Pi3 or Minnowboard Max, please refer to the [Arduino Wiring project guide](ArduinoWiringProjectGuide.md).</span></span>

> [!NOTE]
> <span data-ttu-id="78b06-114">Arduino 연결 됩니다 *되지* 현재 DragonBoard 410 c에서 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="78b06-114">Arduino Wiring is *not* currently supported on DragonBoard 410c.</span></span>
