---
title: 번개 성능 테스트
author: msalehmsft
ms.author: msaleh
ms.date: 08/28/2017
ms.topic: article
description: 다양 한 플랫폼과 언어에 대 한 Windows IoT 번개 기능 및 설정/해제 빈도에 대해 알아봅니다.
keywords: windows iot, 번개 성능, 기능 번개 GPIO
ms.openlocfilehash: 65f6732dd945b199902bb7eb4a9e0cc41aac2131
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513589"
---
# <a name="windows-iot-lightning-performance-testing"></a>Windows IoT 번개 성능 테스트

GPIO 성능 간단한 GPIO 토글 앱을 사용 하 여 Windows IoT 번개 기능에 대해 테스트 되었습니다 [사용 가능한 여기](https://github.com/ms-iot/lightning/tree/develop/PerformanceTestSuite)합니다. 테스트는 0-1 가능한 가장 빠른 속도로 GPIO 5로 전환 하 여 수행 되었습니다. 각 사례에 대 한 토글 빈도 Tektronix TP 2024 Oscilloscope를 사용 하 여 측정 되었습니다.

다음 결과 분석에서 가져왔습니다.

> | 테스트 플랫폼                     | 언어        | 빈도     |
> | ----------------------------------- | --------------- | ------------- |
> | Arduino Uno                         | Arduino 스케치  | 75.06 kHz     |
> | Windows 10 IoT Core 대 한 기본 스택    | C#              | 239 kHz       |
> | Windows 10 IoT Core 대 한 기본 스택    | C++/CX          | 278 kHz       |
> | Windows 10 IoT Core 대 한 기본 스택    | WinJS           | 34 kHz        |
> | Windows 10 IoT Core Arduino 연결  | Arduino 연결  | **7.36 MHz**  |
> | Windows 10 IoT Core DMAP 스택      | C#              | **1.76 MHz**  |
> | Windows 10 IoT Core DMAP 스택      | C++/CX          | **3.78 MHz**  |
> | Windows 10 IoT Core DMAP 스택      | WinJS           | 42 kHz        |

Windows 10 IoT Core Insider Preview 빌드 15026 (코드명 Redstone 2)를 사용 하 여 Raspberry Pi 3에서 실행 되었으며 Microsoft IoT 번개 SDK 1.1.0을 사용 하 여 작성 하는 Windows 10 IoT Core 테스트 합니다.
