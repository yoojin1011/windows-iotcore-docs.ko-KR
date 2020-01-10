---
title: 제안된 프로토타입 보드
ms.date: 04/17/2018
ms.topic: article
description: Windows 10 IoT용 제안 프로토타입 보드에 대해 알아봅니다.
keywords: windows iot, 디바이스 개발, 보드, Raspberry Pi 2, Raspberry Pi 3, Minnowboard Max, Dragonboard
ms.openlocfilehash: d1dde3bf04622dfdbdc611fcca96f3fdd3cfae3c
ms.sourcegitcommit: ea060254f9c4c25afcd0245c897b9e1425321859
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75721888"
---
# <a name="suggested-prototype-boards"></a>제안된 프로토타입 보드

## <a name="windows-10-iot-core-development-devices"></a>Windows 10 IoT Core 개발 디바이스
아래에는 Windows 10 IoT Core를 시작하는 데 도움이 되는 보드가 나와 있습니다. 이러한 보드는 기성 이미지로 프로토타입을 빠르게 만들고 Windows 10 IoT Core 플래싱 과정을 만드는 FFU(전체 플래시 업데이트) 이미지를 제공합니다.

> [!IMPORTANT]
> 디바이스를 상용화할 계획이라면 아래에 제공된 이미지를 사용하지 말고 사용자 고유의 이미지를 만들어야 합니다.

> [!NOTE]
> Raspberry Pi 3B +는 Windows 10 IoT Core와의 호환성이 제한되어 있습니다. 자세한 내용은 [릴리스 정보](https://docs.microsoft.com/windows/iot-core/release-notes/insider/rpi3bp)를 참조하세요. 보다 완벽한 Windows 10 IoT Core 환경을 위해 Raspberry Pi 3B, DragonBoard, Up2 Board 또는 NXP 디바이스를 사용하세요. 


| 보드 | 자세한 정보 | FFU 링크 | 설정 방법 | 시작 |
|-----------|----------|---------|---------|---------|---------|-------|
| [AAEON Up 제곱](https://up-board.org/upsquared/specifications/) | [Up Board 사이트](https://up-shop.org/28-up-squared) | [FFU 다운로드](https://downloads.up-community.org/?post_type=wpdmpro&p=204&preview=true) | [Intel 디바이스 설정](https://docs.microsoft.com/windows/iot-core/tutorials/intel) | [상용화](https://up-shop.org/home/270-up-squared.html) | 
| [DragonBoard 410c](https://developer.qualcomm.com/hardware/dragonboard-410c) | [화살표 사이트](https://www.arrow.com/en/products/dragonboard410c/arrow-development-tools) | [FFU 다운로드](https://www.microsoft.com/software-download/windows10IoTCore#!) | [Dragonboard 설정](https://docs.microsoft.com/windows/iot-core/tutorials/dragonboard),<br>[Qualcomm 디바이스 설정](https://docs.microsoft.com/windows/iot-core/tutorials/qualcomm) | [상용화](https://www.arrow.com/en/products/dragonboard410c/arrow-development-tools) | 
| [Keith & Koep i-PAN M7 CoverLens](https://keith-koep.com/de/produkte/produkte-hmi/i-pan-m7-coverlens-arm-touch-panel-pc-eigenschaften/) | [Keith & Koep 사이트](https://keith-koep.com/de/produkte/produkte-hmi/i-pan-m7-coverlens-arm-touch-panel-computer-technische-daten/) | [FFU 다운로드](https://support.keith-koep.com/service/doku.php/service/winiot/images) | [Keith & Koep Wiki](https://support.keith-koep.com/service/doku.php/service/hardware/panel/ipanm7) | [i-PAN M7 CoverLens Starter 키트](https://keith-koep.com/de/produkte/produkte-eval-kits/i-pan-m7-coverlens-starter-kit-technische-daten/) | 
| [Keith & Koep i-PAN T7 CoverLens](https://keith-koep.com/de/produkte/produkte-hmi/i-pan-t7-coverlens-arm-touch-panel-pc-eigenschaften/) | [Keith & Koep 사이트](https://keith-koep.com/de/produkte/produkte-hmi/i-pan-t7-coverlens-arm-touch-panel-computer-technische-daten/) | [FFU 다운로드](https://support.keith-koep.com/service/doku.php/service/winiot/images) | [Keith & Koep Wiki](https://support.keith-koep.com/service/doku.php/service/hardware/panel/ipant7) | [i-PAN T7 CoverLens Eval-Kit](https://keith-koep.com/de/produkte/produkte-eval-kits/i-pan-t7-coverlens-eval-kit-technische-daten/) | 
| [MinnowBoard Turbot](https://minnowboard.org) | [Minnowboard 사이트](https://minnowboard.org/get-a-board) | [FFU 다운로드](https://www.microsoft.com/software-download/windows10IoTCore#!) | [MinnowBoard 설정](https://docs.microsoft.com/windows/iot-core/tutorials/minnowboard) | 해당 없음 |
| [NXP i.MX 6](https://www.nxp.com/products/processors-and-microcontrollers/arm-based-processors-and-mcus/i.mx-applications-processors/i.mx-6-processors:IMX6X_SERIES) | [NXP 사이트](https://www.nxp.com/products/processors-and-microcontrollers/arm-based-processors-and-mcus/i.mx-applications-processors/i.mx-6-processors:IMX6X_SERIES) | [FFU 다운로드](https://github.com/ms-iot/imx-iotcore) | [NXP 디바이스 설정](https://docs.microsoft.com/windows/iot-core/tutorials/nxp) | [상용화](https://www.solid-run.com/nxp-family/hummingboard/imx6-win-10-iot-core/) | 
| [NXP i.MX 7](https://www.nxp.com/products/processors-and-microcontrollers/arm-based-processors-and-mcus/i.mx-applications-processors/i.mx-7-processors:IMX7-SERIES) | [NXP 사이트](https://www.nxp.com/products/processors-and-microcontrollers/arm-based-processors-and-mcus/i.mx-applications-processors/i.mx-7-processors:IMX7-SERIES) | [FFU 다운로드](https://github.com/ms-iot/imx-iotcore) | [NXP 디바이스 설정](https://docs.microsoft.com/windows/iot-core/tutorials/nxp) | [상용화](https://www.compulab.com/products/iot-gateways/iot-gate-imx7-nxp-i-mx-7-internet-of-things-gateway/) | 
| [NXP i.MX 8M/8M Mini](https://www.nxp.com/products/processors-and-microcontrollers/arm-based-processors-and-mcus/i.mx-applications-processors/i.mx-8-processors:IMX8-SERIES) | [NXP 사이트](https://www.nxp.com/products/processors-and-microcontrollers/arm-based-processors-and-mcus/i.mx-applications-processors/i.mx-8-processors:IMX8-SERIES) | [FFU 다운로드](https://github.com/ms-iot/imx-iotcore) | [NXP 디바이스 설정](https://docs.microsoft.com/windows/iot-core/tutorials/nxp) | [8M Dev 키트](https://www.nxp.com/support/developer-resources/software-development-tools/i.mx-developer-resources/evaluation-kit-for-the-i.mx-8m-applications-processor:MCIMX8M-EVK) 또는 [8M Mini Dev 키트](https://www.nxp.com/support/developer-resources/software-development-tools/i.mx-developer-resources/evaluation-kit-for-the-i.mx-8m-mini-applications-processor:8MMINILPD4-EVK) |
| [Raspberry Pi 2](https://www.raspberrypi.org/products/raspberry-pi-2-model-b/)<br> (1.2이 지원되지 않음) | [Raspberry Pi 사이트](https://www.raspberrypi.org/products/raspberry-pi-2-model-b/) | [FFU 다운로드](https://www.microsoft.com/software-download/windows10IoTCore#!) | [Raspberry Pi 설정](https://docs.microsoft.com/windows/iot-core/tutorials/rpi) | [Adafruit 키트](https://docs.microsoft.com/windows/iot-core/tutorials/adafruitkit) | 
| [Raspberry Pi 3B](https://www.raspberrypi.org/products/raspberry-pi-3-model-b/)<br> (3B+는 지원되지 않는 기술 미리 보기입니다.) | [Raspberry Pi 사이트](https://www.raspberrypi.org/products/raspberry-pi-3-model-b/) | [FFU 다운로드](https://www.microsoft.com/software-download/windows10IoTCore#!) | [Raspberry Pi 설정](https://docs.microsoft.com/windows/iot-core/tutorials/rpi) | [Adafruit 키트](https://docs.microsoft.com/windows/iot-core/tutorials/adafruitkit) |
