---
title: Soc 및 Windows 10 IoT Core 대 한 사용자 지정 보드
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 다양 한 제안 된 보드 및 커뮤니티 장치 하드웨어 기능에 알아봅니다.
keywords: windows iot, 개발 장치, SOC, SOM 칩을 DragonBoard, Minnowboard 최대, Raspberry Pi 3, Raspberry Pi 2에는 시스템 보드
ms.openlocfilehash: 7b3839a222c8e15e006f03ca5d125d81f175b46e
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513245"
---
# <a name="socs-and-custom-boards"></a>Soc 및 사용자 지정 보드

## <a name="microsoft-enabled-socs"></a>Soc Microsoft 지원

Microsoft는 Broadcom, Intel, NXP, 및 Qualcomm 칩 (Soc)의 여러 공급 업체의 시스템에서 Windows 10 IoT Core 대 한 지원을 확인 하려면 함께 작동 합니다. 이러한 IoT Core 기반 Soc 수백 대의 프로토타입에 사용 하 고 아이디어를 상용화할 수 있는 다양 한 장치에서 사용 됩니다.

| Broadcom | Intel | Qualcomm | NXP |
|----------|-------|----------|-----|
| BCM2837 | [Intel® Atom 프로세서 E3900 시리즈 (Apollo Lake)](https://ark.intel.com/products/codename/80644/#@embedded)                                | [Snapdragon 410 (APQ8016)](https://www.qualcomm.com/products/snapdragon/processors/410) | [i.MX 6 제품군](http://aka.ms/iotnxp) |
| BCM2836 | [Intel® Celeron® 프로세서 N3350 (Apollo Lake)](https://ark.intel.com/products/codename/80644/#@embedded)                                    | [Snapdragon 212 (APQ8009)](https://www.qualcomm.com/products/snapdragon/processors/212) | [i.MX 7 제품군](http://aka.ms/iotnxp)     |
|         | [Intel® Pentium® N4200 프로세서 플랫폼 (Apollo Lake)](https://ark.intel.com/products/codename/80644/#@embedded)                           |                                                                                         | [i.MX 8m 제품군](http://aka.ms/iotnxp) |
|         | [Intel® Pentium® 및 Celeron® 프로세서 N3000 시리즈 (Braswell)](http://ark.intel.com/products/codename/66094/#@embedded)                    |                                                                                         |      |
|         | [Intel® Atom® x5 E8000 프로세서 (Braswell)](http://ark.intel.com/products/codename/66094/#@embedded)                                        |                                                                                         |  |
|         | [Intel® Atom® x5 Z8350 프로세서 (Cherry 내역)](https://ark.intel.com/products/93361/Intel-Atom-x5-Z8350-Processor-2M-Cache-up-to-1_92-GHz) |                                                                                         |     |
|         | [Intel® Atom 프로세서 E3800 제품군 (베이 내역-I)](http://ark.intel.com/products/codename/55844/#@Embedded)                     |                                                                                         |  |
|         | [Intel® Pentium® 및 Celeron® 프로세서 N J 계열 (베이 내역-M/D)](http://ark.intel.com/products/codename/55844/)                     |                                                                                         |       |

채택 하려는 SoC 성능 요구 사항, 전원 프로필, 비용, 물리적 연결 옵션, 긴 용어 지원 및 작동 상태와 같은 고려 사항에 따라 달라 집니다.

에서는 또한 상업용 보드 또는 장치를 사용 하려는 지 여부를 결정 시스템 모듈 (SoM) 및 사용자 지정 운송 업체 보드를 사용 하 여 사용자 지정 장치를 구축 하거나 보드 전체 사용자 지정 빌드. 비용 및 사용자 지정 정도 핵심적인 요소 모두 일반적으로 증가 추가로 사용자 지정할 때이 의사 결정 됩니다.

## <a name="windows-10-iot-core-features-by-processor-family"></a>프로세서 제품군에서 Windows 10 IoT Core 기능

> [!NOTE]
> 이 목록은 비 상업적 공개 미리 보기로 제공에서 되는 고려 사항 프로세서를 고려 합니다.

아래 표에 장치에 대 한 올바른 플랫폼을 선택할 수 있도록, Windows 10 IoT Core 사용 하 여 프로세서 제품군에서 지원 되는 기능을 보여 줍니다. 아래에 나열 된 모든 기능은 일부 Soc 디자인에 포함 된 특정 IP에 없을 수 있으며 "n/A"와 같이 표시 됩니다 있지만 Windows 10 IoT Core에서 지원 됩니다. 이러한 경우에는 타사 솔루션에 필요한 기능을 제공 하도록 디자인 회사 수 있습니다.  Windows 10 IoT Core 기능을 프로세서에서 구현 되지 않았습니다 하는 경우의 제한 된 수의 항목을 비워 둡니다.

> |    | Intel  |  Qualcomm  | NXP i.MX6 | NXP i.MX7 | NXP i.MX8M | Broadcom |
> |----|--------|------------|-----------|-----------|------------|----------|
> | 오디오 | x | x | x | x | x | x |
> | GPIO | x | x | x | x | x | x |
> | I2C | x | x | x | x | x | x |
> | 이더넷 | x | 해당 사항 없음 | x | x | x | x |
> | SPI | x | x | x | x | x | x |
> | 표시 | x | x | x | x | x | x |
> | UART | x | x | x | x | x | x |
> | USB | x | x | x | x | x | x |
> | PCIe | x | 해당 사항 없음 | x | 개발 중 | 개발 중 | 해당 사항 없음 |
> |MIPI-CSI | 해당 사항 없음 | x | 해당 사항 없음 | 해당 사항 없음 | 해당 사항 없음 | 해당 사항 없음 |
> | 그래픽/비디오 | x | x | 소프트웨어 렌더링 | 소프트웨어 렌더링 | 소프트웨어 렌더링 | 소프트웨어 렌더링 |
> | GPS | 해당 사항 없음 | x | 해당 사항 없음 | 해당 사항 없음 | 해당 사항 없음 | 해당 사항 없음 |
> | Wi-Fi/BT | 해당 사항 없음 | x | 해당 사항 없음 | 해당 사항 없음 | 해당 사항 없음 | 해당 사항 없음 |
> | 신뢰할 수 있는 I/O | 해당 사항 없음 | 해당 사항 없음 | x | x | x | 해당 사항 없음 |
> | 프로세서 전원 관리 |  | x | x | x | 개발 중 | |
> | TPM | x | x | x | x | x | 해당 사항 없음 |
> | 보안 부팅 | x | x | 개발 중 | 개발 중 | 개발 중 | |
> | 최대 절전 모드 | x | | | | | | 
> | PWM | x | 해당 사항 없음 | x | x | x | |
> | JTAG | x | 해당 사항 없음 | x | x | x | |
> | eMMC | x | x | x | x | x | |
> | SDHC | x | x | x | x | x | x |

## <a name="customized-boards"></a>사용자 지정된 보드

상업용 장치에 있는 경우 시나리오에 사용할 수 있는 연결 옵션을 포함 하는 폼 팩터 하는 경우가 가장 비용 및 시간-유효한 선택입니다.  

대부분의 사용자에 대 한 전체 사용자 지정 보드 개발 합리적일 것 제품 수십, 수백, 수천 개의 단위로 보다 큰 볼륨의 판매 될 예상 되는 경우. 더 작은 볼륨, SoM을 사용 하 여 완전히 새로운 보드를 디자인 하는 대신 사용자 지정 운송 업체 보드, 디자인 및 크게 줄일 수 비용 및 출시 시간을 뿐만 아니라 스트리밍을 소프트웨어 개발 및 통합.

각 플랫폼에 구현 하는 동안 주의 해야 하는 고유한 특색이 있습니다.  다음은 시작 하는 방법에 몇 가지 제안 사항입니다. 및 Windows 10 IoT Core 사용 하는 경험으로 입증 된 일부 목록은 다음과 같습니다 Windows 10 IoT Core 구축 하는 많은 회사 있기는 합니다.

* __[Raspberry Pi](#raspberry-pi-derived-custom-design)__
* __[Intel](#intel-based-custom-design)__
* __[Qualcomm](#qualcomm-dragonboard-410c-apq8016-based-custom-design)__
* __[NXP](#nxp-preview)__

*SoM 공급자나는 ODM 있고 아래 목록에 추가 하려는 경우 메일을 보내 주세요 [ winiotsomhelp@microsoft.com ](mailto:winiotsomhelp@microsoft.com) 또는 직접이 페이지를 편집 하 고 끌어오기 요청을 제출 합니다.*

*여기에 나열 된 대부분의 회사는 크고 복잡 한 됩니다.  적합 한 사람에 도달 하는 데 문제가 있으면 전자 메일 [ winiotsomhelp@microsoft.com ](mailto:winiotsomhelp@microsoft.com) 것이 가장 권한이 있는 사용자에 연결 합니다.*

### **<a name="raspberry-pi-derived-custom-design"></a>Raspberry Pi에서 파생 된 사용자 지정 디자인**

[요소 14](https://www.element14.com/community/docs/DOC-76955/l/raspberry-pi-customization-service) 제품 보드 사용자 지정 서비스 연결 옵션을 추가 또는 제거할 수 있도록 Raspberry Pi에 대 한 합니다. 활용할 수 있습니다 BSP를 사용자 지정을 수행 해야 하는 경우는 [Github의 소스 BSP 코드를 열고](https://github.com/ms-iot/rpi-iotcore)합니다.

### **<a name="intel-based-custom-design"></a>Intel 기반 사용자 지정 디자인**

활발 한 에코 시스템을 방법이 [Intel 장치 작성기 발생](https://solutionsdirectory.intel.com/solutions-directory/processors/278/processors/309/processors/402/processors/782/processors/788/processors/1103/processors/1107/processors/1110/processors/1175/processors/1344/processors/1348/processors/1349) 작업할 수 있는 Windows에 대 한 합니다. Windows 10 IoT Core 실행 하도록 설계 된 Intel 장치에는 몇 가지 일반적인 Pc에서 차이가 있습니다.

1. GPIO, I2C, SPI 같은 간단한 버스에 대 한 사용자 모드 유니버설 Windows 플랫폼 (UWP) API 액세스를 제공 해야 할 경우에 UEFI 펌웨어에 ACPI 테이블 RHProxy에 대 한 적절 한 항목을 포함 하는 않도록 해야 합니다. 참조 하십시오 [사용자 모드 액세스](https://docs.microsoft.com/windows/uwp/devices-sensors/enable-usermode-access) 자세한 내용은 합니다.
2. 펌웨어에 SMBIOS에 나열 된 정보를 포함 해야 [OEM 라이선스 요구 사항](https://docs.microsoft.com/windows/iot-core/commercialize-your-device/oemlicenserequirements)합니다.

사용자 고유의 보드를 작성 하는 경우 ACPI 또는 SMBIOS 변경에 대 한 지침을 사용 해야 하는 경우 BIOS 공급 업체를 문의 하십시오.

#### *<a name="experienced-partners"></a>숙련 된 파트너*

* [Aaeon](http://www.aaeon.com/en/)
* [Advantech](http://www.advantech.com/) - buy@advantech.tw
* [Kontron](http://www.kontron.com/) - martin.unverdorben@kontron.com
* [Nexcom](http://www.nexcom.com/)

### **<a name="qualcomm-dragonboard-410c-apq8016-based-custom-design"></a>Qualcomm DragonBoard 410 c (APQ8016)-기반 사용자 지정 디자인**

DragonBoard 410 c (Qualcomm AQP8016 SoC에 기반)에 대 한 이진 BSP에서 다운로드할 수 있습니다 [Qualcomm Developer Network](https://developer.qualcomm.com/hardware/dragonboard-410c/software)합니다.

BSP 패키지에만 ACPI 변경 해야 하는 간단한 하드웨어 사용자 지정할 수 있도록 ACPI에 대 한 소스 코드를 포함 합니다.  

> [!IMPORTANT] 
> 추가 하드웨어 사용자 지정을 할 경우 특정 MIPI-DSI를 사용 하는 등 패널을 표시, 플랫폼 보안 부팅, RF 보정 및 인증 (예:를 사용 하도록 설정 FCC, CE) Qualcomm BSP 소스 코드 정식 사용자 될 해야 합니다 또는 액세스할 수 있는 공급자를 사용 하려면 (숙련 된 파트너 아래 참조).

권장 사항:

1. 가능한 경우 사용자 지정된 디자인을 사용 하도록 설정 하는 숙련 된 SoM 공급 업체를 사용 하 여 작동 합니다.
2. 사용자 지정 보드를 작성 하는 경우 작업할 SoM 공급 업체 또는 숙련 된 Qualcomm BSP의 사용자 지정 서비스 공급자와 같은 [Intrinsyc](https://www.intrinsyc.com/) 또는 [Thundersoft](http://www.thundersoft.com/) BSP 사용자 지정 및 설계 지원 합니다.
3. 매우 높은 볼륨 (수백만 개)를 갖는 경우 [Qualcomm 문의](https://assets.qualcomm.com/contact-sales-iot.html)합니다.

#### *<a name="experienced-partners"></a>숙련 된 파트너*

* [Intrinsyc](https://www.intrinsyc.com/computing-platforms/410-som/) -표시 Waldenberg (mwaldenberg@intrinsyc.com)
* [Keith & Koep](https://keith-koep.com/en/products/products-som/myon-1-features-snapdragon-410/) - contact@keith-koep.com
* [Reycom](http://www.reycom.swiss/en/home-swiss.html) - welcome@reycom.swiss
* [Unitech](http://ute.com/products_info.php?pc1=4&pc2=461&rbu=0&pid=2395) -Sam (saml@tw.ute.com); Perry (perryt@te.ute.com)

### **<a name="nxp-preview"></a>NXP 미리 보기**

Windows 10 IoT Core 대 한 NXP 지원 공개 미리 보기입니다. 자세한 내용은 액세스는 BSP 또는 하드웨어 파트너를 찾아야로 이동 하십시오 합니다 [NXP SoC 페이지](http://aka.ms/iotnxp)합니다.

연결할 수도 있습니다 아웃 파트너에 게 협력 하 고 있습니다.

* Advantech [RSB-4411](http://www.advantech.com/products/single_board_computer/rsb-4411/mod_d3901250-b0a0-4a5f-9762-b26fa0c36858) - buy@advantech.tw
* Keith & Koep [pConXS](http://wce.keith-koep.com/en/products/pconxs-ff/) 사용 하 여 [Trizeps VII](http://wce.keith-koep.com/en/products/trizeps7-i.MX6/) - contact@keith-koep.com
* Kontron [SMARC sAMX6i](https://www.kontron.com/products/boards-and-standard-form-factors/smarc/smarc-samx6i.html) -Martin Unverdorben (martin.unverdorben@kontron.com)
* Solid 실행 [Hummingboard Edge](https://www.solid-run.com/imx6-win-10-iot-core/ )-Ilya Viten (ilya@solid-run.com)
* Geniatech [Q7-iMX6Q-SoM](https://www.geniatech.com/product/som-imx6q-q7/) & [SoM iMX7D](https://www.geniatech.com/product/som-imx7d/) -Mike Decker (mike.decker@geniatech.com) 또는 팡 Jijun (Fjj@geniatech.com)
* 통해 [VAB 820](https://www.viaembeddedstore.com/shop/boards/vab-820/) -Michael Fox (MichaelFox@via.com.tw) 또는 ku가 Dream (dreamku@via.com.tw)
* Phytec [phyBOARD i.MX7](https://phytec.com/products/single-board-computers/phyboard-i.mx7/) -Brad Dodson (sales@phytec.com)


## <a name="other-options"></a>기타 옵션

사용자 지정 보드 만들기 하려는 여전히 있다면 제공 했습니다 설계도 및 보드에 대 한 레이아웃 아래에 제조업체의 몇 가지 제안 도움이 될 수 있습니다.

* [모든 PCB](http://www.allpcb.com/)
* [Geppetto/Gumstix](https://www.gumstix.com/geppetto/)
* [JLC PCB](https://jlcpcb.com/)
* [Myro PCB](http://www.myropcb.com/)
* [OSH PARK](https://oshpark.com/)
* [seeed studio](https://www.seeedstudio.com/)
