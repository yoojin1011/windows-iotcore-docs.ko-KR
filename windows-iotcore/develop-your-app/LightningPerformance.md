---
title: 라이트닝 성능 테스트
author: msalehmsft
ms.author: msaleh
ms.date: 08/28/2017
ms.topic: article
description: 다양 한 플랫폼 및 언어에 대 한 Windows IoT 라이트닝 기능 및 전환 빈도에 대해 알아봅니다.
keywords: windows iot, 라이트닝 성능, 라이트닝 기능, GPIO
ms.openlocfilehash: e7d57f72f6db85fbb8e453943c87e8ee31ef8a40
ms.sourcegitcommit: cbea9d713986fbe8b85e1bba1561a000188bd91c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64744785"
---
# <a name="windows-iot-lightning-performance-testing"></a>Windows IoT 라이트닝 성능 테스트

> [!IMPORTANT]
> Windows 10 IoT 팀은 더 이상 Arduino을 지원 하지 않습니다.

GPIO 성능은 [여기에서 사용할 수 있는](https://github.com/ms-iot/lightning/tree/develop/PerformanceTestSuite)간단한 GPIO 설정/해제 앱을 사용 하 여 Windows IoT 라이트닝 기능을 테스트 했습니다. 테스트는 5 ~ 007e; 1 사이의 가장 빠른 속도로 GPIO 5를 전환 하 여 수행 했습니다. 각 사례에 대 한 토글 빈도는 Tektronix 2024 Oscilloscope를 사용 하 여 측정 되었습니다.

분석에서 얻은 결과는 다음과 같습니다.

> | 테스트 된 플랫폼                     | 언어        | 빈도     |
> | ----------------------------------- | --------------- | ------------- |
> | Arduino Uno                         | Arduino 스케치  | 75.06 kHz     |
> | Windows 10 IoT Core Native Stack    | C#              | 239 KHz       |
> | Windows 10 IoT Core Native Stack    | C++/CX          | 278 kHz       |
> | Windows 10 IoT Core Native Stack    | WinJS           | 34 kHz        |
> | Windows 10 IoT Core Arduino 배선  | Arduino 배선  | **7.36 MHz**  |
> | Windows 10 IoT Core의 스택 스택      | C#              | **1.76 MHz**  |
> | Windows 10 IoT Core의 스택 스택      | C++/CX          | **3.78 MHz**  |
> | Windows 10 IoT Core의 스택 스택      | WinJS           | 42 kHz        |

Windows 10 IoT Core 테스트는 Windows 10 IoT Core Insider Preview 빌드 15026 (코드명 Redstone 2)을 사용 하 여 Raspberry Pi 3에서 실행 되었으며 Microsoft IoT 라이트닝 SDK 1.1.0를 사용 하 여 빌드 되었습니다.
