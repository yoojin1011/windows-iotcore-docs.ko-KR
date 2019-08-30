---
title: Windows IoT Core 장치에 대 한 Arduino 배선
author: msalehmsft
ms.author: msaleh
ms.date: 09/06/17
ms.topic: article
description: 지원 되는 Windows IoT Core 장치에서 Arduino 배선 스케치를 만들고, 배포 하 고, 디버그 하는 방법을 알아봅니다.
keywords: windows iot, Arduino, Arduino 배선, 템플릿, IoT Core, UWP
ms.openlocfilehash: ee6c64bdfd01e79d26bfa0a6c5f88f7735150393
ms.sourcegitcommit: cbea9d713986fbe8b85e1bba1561a000188bd91c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64744791"
---
# <a name="arduino-wiring-for-windows-iot-core-devices"></a>Windows IoT Core 장치에 대 한 Arduino 배선

> [!IMPORTANT]
> Windows 10 IoT 팀은 더 이상 Arduino를 적극적으로 유지 관리 하지 않습니다.

IoT Core 장치에서 친숙 한 [Arduino 배선](https://www.arduino.cc/en/Reference/HomePage) 스케치의 개발 및 재사용을 가능 하 게 하기 위해 Arduino 배선 용 Visual Studio 프로젝트 템플릿은 [Windows IoT core 프로젝트 템플릿 확장](https://go.microsoft.com/fwlink/?linkid=847472)의 일부로 제공 됩니다.

Arduino 배선 프로젝트 템플릿을 사용 하면 개발자와 결정자는 Arduino 플랫폼에서 사용할 수 있는 것과 동일한 Arduino 배선 언어 의미 체계와 구문을 사용 하 여 지원 되는 IoT Core 장치에서 Arduino 배선 스케치를 만들고 배포 하 고 디버그할 수 있습니다. 이를 통해 기존 Arduino 스케치를 매우 적은 비용으로 IoT Core에 이식할 수 있지만, IoT Core에서 실행 되는 Arduino 배선 스케치는 UWP (유니버설 Windows Platform) API를 사용할 수 있는 전체 Windows 10 앱입니다. 따라서 Arduino 배선 스케치는 Windows 10 IoT Core 장치에서 실행 되는 종단 간 시나리오를 만드는 데 사용할 수 있는 통신, 데이터 액세스, 네트워킹, 그래픽 등의 Api에 대 한 모든 액세스 권한을 가집니다. UWP (유니버설 Windows 플랫폼) 앱을 개발 하는 방법에 대 한 자세한 내용은 [Windows 10 IoT Core 용 응용 프로그램 빌드](../develop-your-app/BuildingAppsForIoTCore.md)를 참조 하세요.

또한 Arduino 배선 스케치는 지원 되는 장치에서 고성능을 제공 하는 직접 메모리 매핑된 드라이버를 활용 합니다. 성능 세부 정보에 대 한 자세한 내용은 [Windows IoT 라이트닝 성능 테스트](../develop-your-app/LightningPerformance.md) 보고서를 참조 하세요.

Raspberry Pi2, Pi3 또는 Minnowboard Max에 대 한 Arduino 배선 프로젝트 빌드를 시작 하려면 [Arduino 와이어링 프로젝트 가이드](ArduinoWiringProjectGuide.md)를 참조 하세요.

> [!NOTE]
> Arduino 유선은 현재 DragonBoard 410c에서 지원 *되지 않습니다* .
