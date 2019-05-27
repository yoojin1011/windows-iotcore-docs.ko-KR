---
title: 프로토타입 보드를 제안합니다.
author: saraclay
ms.author: saclayt
ms.date: 04/17/2018
ms.topic: article
description: Windows 10 IoT에 대 한 제안 된 프로토타입 보드에 알아봅니다.
keywords: windows iot, 장치 개발 보드, Raspberry Pi 2, Raspberry Pi 3, Minnowboard 최대, Dragonboard
ms.openlocfilehash: 9718fc0bf82d4ae0feb8842438a0a0dbffd28d1d
ms.sourcegitcommit: 8aadc776da7b473159f9023cd555145819e7e952
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66174036"
---
# <a name="suggested-prototype-boards"></a>프로토타입 보드를 제안합니다.

## <a name="windows-10-iot-core-development-devices"></a>Windows 10 IoT Core 개발 장치
다음 Windows 10 IoT Core 사용 하 여 시작 하는 데 좋습니다 보드를 찾을 수 있습니다. 이 보드를 바로 사용할 수 있는 이미지를 사용 하 여 프로토타입 생성을 빠르게 만들기 및 수 있으므로 깜박이 Windows 10 IoT Core 간편해 집니다 전체 플래시 업데이트 (FFU) 이미지를 제공 합니다.

> [!IMPORTANT]
> 사용자 고유의 이미지를 만들고 장치 상용화할 하려는 경우 아래 제공 된 이미지를 사용 하지 해야 합니다.

> [!NOTE]
> Raspberry Pi 3B + Windows 10 IoT Core 사용 하 여 호환성을 제한 했습니다. 참조 하십시오 합니다 [릴리스](https://docs.microsoft.com/en-us/windows/iot-core/release-notes/insider/rpi3bp) 자세한 내용은 합니다. 전체 Windows 10 IoT Core 환경을 3B, DragonBoard, Up2 보드나 NXP Raspberry Pi 장치를 사용 하십시오. 


| 보드 | 추가 정보 | FFU 링크 | 설정 하는 방법 | 시작 |
|-----------|----------|---------|---------|---------|---------|-------|
| [등록 AAEON 제곱](https://up-board.org/upsquared/specifications/) | [보드 사이트](https://up-shop.org/28-up-squared) | [FFU 다운로드](https://downloads.up-community.org/?post_type=wpdmpro&p=204&preview=true) | [Intel 장치 설정](https://docs.microsoft.com/en-us/windows/iot-core/tutorials/intel) | [귀하는](https://up-shop.org/home/270-up-squared.html) | 
| [DragonBoard 410 c](https://developer.qualcomm.com/hardware/dragonboard-410c) | [화살표 사이트](https://www.arrow.com/en/products/dragonboard410c/arrow-development-tools) | [FFU 다운로드](https://www.microsoft.com/en-us/software-download/windows10IoTCore#!) | [Dragonboard 설정](https://docs.microsoft.com/en-us/windows/iot-core/tutorials/dragonboard),<br>[Qualcomm 장치 설정](https://docs.microsoft.com/en-us/windows/iot-core/tutorials/qualcomm) | [귀하는](https://www.arrow.com/en/products/dragonboard410c/arrow-development-tools) | 
| [Keith & Koep i 팬 M7 CoverLens](https://keith-koep.com/de/produkte/produkte-hmi/i-pan-m7-coverlens-arm-touch-panel-pc-eigenschaften/) | [Keith & Koep 사이트](https://keith-koep.com/de/produkte/produkte-hmi/i-pan-m7-coverlens-arm-touch-panel-computer-technische-daten/) | [FFU 다운로드](https://support.keith-koep.com/service/doku.php/service/winiot/images) | [Keith & Koep Wiki](https://support.keith-koep.com/service/doku.php/service/hardware/panel/ipanm7) | [i-PAN M7 CoverLens Starter Kit](https://keith-koep.com/de/produkte/produkte-eval-kits/i-pan-m7-coverlens-starter-kit-technische-daten/) | 
| [Keith & Koep i 팬 T7 CoverLens](https://keith-koep.com/de/produkte/produkte-hmi/i-pan-t7-coverlens-arm-touch-panel-pc-eigenschaften/) | [Keith & Koep 사이트](https://keith-koep.com/de/produkte/produkte-hmi/i-pan-t7-coverlens-arm-touch-panel-computer-technische-daten/) | [FFU 다운로드](https://support.keith-koep.com/service/doku.php/service/winiot/images) | [Keith & Koep Wiki](https://support.keith-koep.com/service/doku.php/service/hardware/panel/ipant7) | [T7 키트 CoverLens Eval-i-이동](https://keith-koep.com/de/produkte/produkte-eval-kits/i-pan-t7-coverlens-eval-kit-technische-daten/) | 
| [MinnowBoard Turbot](https://minnowboard.org) | [Minnowboard 사이트](https://minnowboard.org/get-a-board) | [FFU 다운로드](https://www.microsoft.com/en-us/software-download/windows10IoTCore#!) | [MinnowBoard 설정](https://docs.microsoft.com/en-us/windows/iot-core/tutorials/minnowboard) | 해당 사항 없음 |
| [NXP i.MX 6](https://www.nxp.com/products/processors-and-microcontrollers/arm-based-processors-and-mcus/i.mx-applications-processors/i.mx-6-processors:IMX6X_SERIES) | [NXP 사이트](https://www.nxp.com/products/processors-and-microcontrollers/arm-based-processors-and-mcus/i.mx-applications-processors/i.mx-6-processors:IMX6X_SERIES) | [FFU 다운로드](https://github.com/ms-iot/imx-iotcore) | [NXP 장치 설정](https://docs.microsoft.com/en-us/windows/iot-core/tutorials/nxp) | [귀하는](https://www.solid-run.com/nxp-family/hummingboard/imx6-win-10-iot-core/) | 
| [NXP i.MX 7](https://www.nxp.com/products/processors-and-microcontrollers/arm-based-processors-and-mcus/i.mx-applications-processors/i.mx-7-processors:IMX7-SERIES) | [NXP 사이트](https://www.nxp.com/products/processors-and-microcontrollers/arm-based-processors-and-mcus/i.mx-applications-processors/i.mx-7-processors:IMX7-SERIES) | [FFU 다운로드](https://github.com/ms-iot/imx-iotcore) | [NXP 장치 설정](https://docs.microsoft.com/en-us/windows/iot-core/tutorials/nxp) | [귀하는](https://www.solid-run.com/nxp-family/hummingboard/imx6-win-10-iot-core/) | [귀하는](https://www.compulab.com/products/iot-gateways/iot-gate-imx7-nxp-i-mx-7-internet-of-things-gateway/) | 
| [NXP i.MX 8M/8M Mini](https://www.nxp.com/products/processors-and-microcontrollers/arm-based-processors-and-mcus/i.mx-applications-processors/i.mx-8-processors:IMX8-SERIES) | [NXP 사이트](https://www.nxp.com/products/processors-and-microcontrollers/arm-based-processors-and-mcus/i.mx-applications-processors/i.mx-8-processors:IMX8-SERIES) | [FFU 다운로드](https://github.com/ms-iot/imx-iotcore) | [NXP 장치 설정](https://docs.microsoft.com/en-us/windows/iot-core/tutorials/nxp) | [귀하는](https://www.solid-run.com/nxp-family/hummingboard/imx6-win-10-iot-core/) | [Dev 키트 8m](https://www.nxp.com/support/developer-resources/software-development-tools/i.mx-developer-resources/evaluation-kit-for-the-i.mx-8m-applications-processor:MCIMX8M-EVK) 또는 [8m 미니 Dev 키트](https://www.nxp.com/support/developer-resources/software-development-tools/i.mx-developer-resources/evaluation-kit-for-the-i.mx-8m-mini-applications-processor:8MMINILPD4-EVK) |
| [Raspberry Pi 2](https://www.raspberrypi.org/products/raspberry-pi-2-model-b/)<br> (1.2 지원 되지 않습니다.) | [Raspberry Pi 사이트](https://www.raspberrypi.org/products/raspberry-pi-2-model-b/) | [FFU 다운로드](https://www.microsoft.com/en-us/software-download/windows10IoTCore#!) | [Raspberry Pi 설정](https://docs.microsoft.com/en-us/windows/iot-core/tutorials/rpi) | [Adafruit Kit](https://docs.microsoft.com/en-us/windows/iot-core/tutorials/adafruitkit) | 
| [Raspberry Pi 3B](https://www.raspberrypi.org/products/raspberry-pi-3-model-b/)<br> (3B +는 지원 되지 않는 기술 미리 보기) | [Raspberry Pi 사이트](https://www.raspberrypi.org/products/raspberry-pi-3-model-b/) | [FFU 다운로드](https://www.microsoft.com/en-us/software-download/windows10IoTCore#!) | [Raspberry Pi 설정](https://docs.microsoft.com/en-us/windows/iot-core/tutorials/rpi) | [Adafruit Kit](https://docs.microsoft.com/en-us/windows/iot-core/tutorials/adafruitkit) |
