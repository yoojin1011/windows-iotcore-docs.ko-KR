---
title: Windows IoT 용어집
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: 설명서를 통해 다양한 Windows IoT Core 관련 용어에 대해 알아봅니다.
keywords: windows iot, 용어집, 용어, 용어, 정의
ms.openlocfilehash: 155de380459cbb74642352ff2a2ff718ebfe1ed7
ms.sourcegitcommit: 9ec4716afde25fdc8b94f7c0794448501f451b55
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/17/2019
ms.locfileid: "60168911"
---
# <a name="glossary-for-windows-iot"></a>Windows IoT 용어집

**ACPI(고급 구성 및 전원 인터페이스)** ACPI(고급 구성 및 전원 인터페이스)는 Hewlett-Packard, Intel, Microsoft, Phoenix 및 Toshiba가 공동으로 개발한 공개 산업 규격입니다.  ACPI는 모바일, 데스크톱 및 서버 플랫폼의 OS 지향 구성, 전원 관리 및 열 관리를 지원하는 업계 표준 인터페이스를 구축합니다.

**BIOS(기본 입출력 시스템)** 시작할 때 하드웨어를 테스트하고, 운영 체제를 시작하고, 하드웨어 디바이스 간의 데이터 전송을 지원하는 필수 소프트웨어 루틴 세트입니다.

**상용화** 디바이스를 상업적으로 일반에 배포할 목적으로 개발 및 제조하는 것입니다.

**GPIO(범용 입출력)** GPIO는 입력 핀으로 동작하는 경우와 출력 핀으로 동작하는 경우를 포함하여 런타임 시 사용자가 제어할 수 있는 집적 회로의 일반 핀입니다.  애플리케이션의 Windows.Devices.Gpio 네임스페이스를 사용하여 보드의 GPIO 핀을 조작할 수 있습니다.

**헤드** Windows IoT Core는 헤드 또는 헤드리스 모드일 수 있습니다. 이 두 가지 모드의 차이점은 UI의 형식이 있는지 여부입니다. 기본적으로 Windows 10 IoT Core는 헤드 모드에 있으며 컴퓨터 이름 및 IP 주소와 같은 시스템 정보를 표시합니다.

**헤드리스** 헤드리스 모드에는 사용할 수 있는 UI 스택이 없으며 앱이 대화형 모드가 아닙니다. 헤드리스 모드 앱은 서비스라고 간주할 수 있습니다.

**I2C(회로간 통합 회로)** 회로간 통합 회로 제어를 위한 단순 양방향 2선 직렬 데이터(SDA) 및 시리얼 클럭(SCL) 버스입니다.  앱의 Windows.Devices.I2c 네임스페이스를 사용하여 I2C를 통해 디바이스와 통신할 수 있습니다.

**LED(발광 다이오드)** LED는 2리드 반도체 광원입니다. 이 다이오드는 활성화되면 빛을 방출하는 pn-junction 다이오드입니다.

**Microsoft Windows KMDF(커널 모드 드라이버 프레임워크)** 드라이버 개발자가 커널 모드에서 드라이버 기능을 노출하여 드라이버가 시스템 메모리 및 하드웨어에 액세스할 수 있도록 하는 Microsoft 개발 프레임워크입니다.

**프로토타입** 만들려는 디바이스의 최종 버전을 더 원시 버전으로 개발하는 것입니다. 제조 공정의 필수 단계가 아니라면 프로토타입 개발을 적극 권장합니다. 이 단계는 디바이스의 최종 버전에 사용할 모든 기능을 테스트하는 데 사용해야 합니다.

**SPI(직렬 주변기기 인터페이스) 버스** SPI 버스는 주로 포함된 시스템에서 근거리 통신에 사용되는 동기 직렬 통신 인터페이스 규격입니다.  앱의 Windows.Devices.Spi 네임스페이스를 사용하여 SPI를 통해 디바이스와 통신할 수 있습니다.

**UART(유니버셜 비동기 수신기/송신기)** UART는 데이터 바이트를 받아 개별 비트를 순차적으로 전송하는 컴퓨터 하드웨어입니다.

**UWP(유니버설 Windows 플랫폼)** 유니버설 Windows 플랫폼은 여러 디바이스에 걸쳐 핵심 API 계층을 보장합니다.  광범위한 디바이스에 설치할 수 있는 단일 앱 패키지를 만들 수 있습니다.

**VM(가상 머신)**<br/>
컴파일러 바이너리 코드와 실제로 프로그램의 명령을 수행하는 마이크로프로세서 사이의 인터페이스 역할을 하는 소프트웨어입니다.  Windows에서는 Hyper-V 관리자를 사용하여 가상 머신을 관리할 수 있습니다.

**Windows 디바이스 콘솔(Devcon.exe)** 디바이스 콘솔인 DevCon(Devcon.exe)은 Windows를 실행하는 컴퓨터의 디바이스에 대한 자세한 정보를 표시하는 명령줄 도구입니다. DevCon을 사용하여 디바이스를 활성화, 비활성화, 설치, 구성 및 제거할 수 있습니다.  이 도구는 드라이버를 수동으로 설치하고 제거하는 데 주로 사용됩니다.
