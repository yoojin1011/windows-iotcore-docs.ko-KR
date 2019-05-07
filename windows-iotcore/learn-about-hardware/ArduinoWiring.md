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
# <a name="arduino-wiring-for-windows-iot-core-devices"></a>Windows IoT Core 장치에 대 한 Arduino 연결

> [!IMPORTANT]
> Windows 10 IoT 팀은 더 이상 적극적으로 Arduino 유지 관리 합니다.

개발 및 친숙 한 다시 사용할 수 있도록 [Arduino 연결](https://www.arduino.cc/en/Reference/HomePage) IoT Core 장치에서 스케치, Arduino 연결에 대 한 Visual Studio 프로젝트 템플릿을의 일부로 제공 되는 [Windows IoT Core 프로젝트 템플릿 확장](https://go.microsoft.com/fwlink/?linkid=847472)합니다.

Arduino 연결 프로젝트 템플릿을 사용 하면 개발자와 작성자를 만들고 배포 하 고 동일한 Arduino 연결 언어 의미 체계를 사용 하 여 지원 되는 IoT Core 장치에 연결 하는 Arduino 스케치를 디버그 하 고 Arduino 플랫폼에서 사용할 수 있습니다 생성 합니다. 이 포트 기존 Arduino 스케치 하는 데 도움이 IoT Core 매우 적은 비용으로 할 뿐만 아니라 연결 Arduino 스케치 IoT Core에서 실행 되는 유니버설 Windows 플랫폼 (UWP) API의 사용을 만들 수 있는 전체 Windows 10 앱. 따라서 연결 Arduino 스케치에 완전히 액세스할 Api 통신, 데이터 액세스, 네트워킹, 그래픽 등 많은 다른 Windows 10 IoT Core 장치에서 실행 되는 종단 간 시나리오를 만드는 데 사용할 수 있습니다. 유니버설 Windows 플랫폼 (UWP) 앱 개발에 대 한 자세한 내용은 참조 하십시오 [건물 응용 프로그램에 대 한 Windows 10 IoT Core](../develop-your-app/BuildingAppsForIoTCore.md)합니다.

또한 지원 되는 장치에 높은 성능을 제공 하는 직접 메모리 매핑된 드라이버의 사용 Arduino 스케치 확인을 연결 합니다. 성능 세부 정보에 대 한 자세한 내용은를 참조 하십시오 합니다 [Windows IoT 번개 성능 테스트](../develop-your-app/LightningPerformance.md) 보고서입니다.

Minnowboard 최대 Raspberry Pi2, Pi3에 Arduino 연결 프로젝트 빌드를 시작 하려면를 참조 하십시오 합니다 [project 가이드 Arduino 연결](ArduinoWiringProjectGuide.md)합니다.

> [!NOTE]
> Arduino 연결 됩니다 *되지* 현재 DragonBoard 410 c에서 지원 됩니다.
