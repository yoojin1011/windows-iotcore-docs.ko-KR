---
title: Windows 10 IoT Core 용 Soc 및 사용자 지정 보드
ms.date: 08/28/2017
ms.topic: article
description: 다양 한 제안 된 보드 및 커뮤니티 장치에 대 한 하드웨어 기능에 대해 알아봅니다.
keywords: windows iot, 개발 장치, 보드, SOC, SOM, 시스템의 칩, Raspberry Pi 2, Raspberry Pi 3, Minnowboard Max, DragonBoard
ms.openlocfilehash: 049cea0ede9740c95d49eba39c387fb1be49a86c
ms.sourcegitcommit: ea060254f9c4c25afcd0245c897b9e1425321859
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75721711"
---
# <a name="socs-and-custom-boards"></a>SoCs 및 사용자 지정 보드

## <a name="microsoft-enabled-socs"></a>Microsoft 지원 Soc

Microsoft는 Broadcom, Intel, NXP 및 Qualcomm와 함께 작동 하 여 여러 공급 업체의 시스템 (Soc)에 대 한 Windows 10 IoT Core 지원을 확인 합니다. 이러한 IoT Core 구동 Soc는 아이디어를 프로토타입 하 고 귀하 상용화할 권리 하는 데 사용할 수 있는 수백 개의 서로 다른 장치에서 사용 됩니다.

| Broadcom | Intel | Qualcomm | NXP |
|----------|-------|----------|-----|
| BCM2837 | [Intel® Atom® processor E3900 시리즈 (아폴로 Lake)](https://ark.intel.com/products/codename/80644/#@embedded)                                | [Snapdragon 410 (APQ8016)](https://www.qualcomm.com/products/snapdragon/processors/410) | [i.MX 6 제품군](https://aka.ms/iotnxp) |
| BCM2836 | [Intel® 셀러론® processor N3350 (아폴로 Lake)](https://ark.intel.com/products/codename/80644/#@embedded)                                    | [Snapdragon 212 (APQ8009)](https://www.qualcomm.com/products/snapdragon/processors/212) | [i.MX 7 제품군](https://aka.ms/iotnxp)     |
|         | [Intel® Pentium® processor N4200 platform (아폴로 Lake)](https://ark.intel.com/products/codename/80644/#@embedded)                           |                                                                                         | [i.MX 8M 및 8M 미니 제품군](https://aka.ms/iotnxp) |
|         | [Intel® Pentium® 및 셀러론® Processor N3000 시리즈 (Braswell)](http://ark.intel.com/products/codename/66094/#@embedded)                    |                                                                                         |      |
|         | [Intel® Atom® x5-E8000 Processor (Braswell)](http://ark.intel.com/products/codename/66094/#@embedded)                                        |                                                                                         |  |
|         | [Intel® Atom® x5-Z8350 프로세서 (Cherry-pick 트레일)](https://ark.intel.com/products/93361/Intel-Atom-x5-Z8350-Processor-2M-Cache-up-to-1_92-GHz) |                                                                                         |     |
|         | [Intel® Atom® Processor E3800 제품군 (베이 트레일)](http://ark.intel.com/products/codename/55844/#@Embedded)                     |                                                                                         |  |
|         | [Intel® Pentium® 및 셀러론® 프로세서 N 및 J 시리즈 (베이 트레일-M/D)](http://ark.intel.com/products/codename/55844/)                     |                                                                                         |       |

채택 하도록 선택한 SoC는 성능 요구 사항, 전원 프로필, 비용, 물리적 연결 옵션, 장기 지원 및 운영 상태와 같은 고려 사항에 따라 달라 집니다.

또한, 선반 보드 또는 장치를 사용 하 고, 모듈 (SoM)의 시스템을 사용 하 여 사용자 지정 장치를 빌드하거나, 사용자 지정 캐리어 보드를 작성 하거나, 완전 한 사용자 지정 보드를 작성 하려는 지 여부를 결정 해야 합니다. 비용 및 사용자 지정의 정도는이 결정의 핵심 요소 이며, 나중에 사용자 지정 하는 경우 보다 일반적으로 향상 됩니다.

## <a name="windows-10-iot-core-features-by-processor-family"></a>프로세서 제품군 별 Windows 10 IoT Core 기능

> [!NOTE]
> 이 목록은 비 상업적 공개 미리 보기에 있는 프로세서를 고려 합니다.

다음 표에서는 장치에 적합 한 플랫폼을 선택 하는 데 도움이 되도록 Windows 10 IoT Core를 사용 하는 프로세서 제품군에서 지원 되는 기능을 보여 줍니다. 아래에 나열 된 모든 기능은 Windows 10 IoT Core에서 지원 되지만 일부 Soc는 해당 디자인에 포함 된 특정 IP를 갖지 않을 수 있으며 "N/A"로 표시 됩니다. 이러한 경우 타사 솔루션을 디자인에 통합 하 여 필요한 기능을 제공할 수 있습니다.  Windows 10 IoT Core 기능이 프로세서에서 구현 되지 않는 제한 된 수의 경우 항목이 비어 있습니다.

> |    | Intel  |  Qualcomm  | NXP MX6 | NXP MX7 | NXP MX8M | Broadcom |
> |----|--------|------------|-----------|-----------|------------|----------|
> | 오디오 | x | x | x | x | x | x |
> | GPIO | x | x | x | x | x | x |
> | I2C | x | x | x | x | x | x |
> | Ethernet | x | 해당 없음 | x | x | x | x |
> | SPI | x | x | x | x | x | x |
> | Display | x | x | x | x | x | x |
> | UART | x | x | x | x | x | x |
> | USB를 선택합니다 | x | x | x | x | x | x |
> | PCIe | x | 해당 없음 | x | 개발 중 | 개발 중 | 해당 없음 |
> |MIPI-CSI | 해당 없음 | x | 해당 없음 | 해당 없음 | 해당 없음 | 해당 없음 |
> | 그래픽/비디오 | x | x | 소프트웨어 렌더링 | 소프트웨어 렌더링 | 소프트웨어 렌더링 | 소프트웨어 렌더링 |
> | GPS | 해당 없음 | x | 해당 없음 | 해당 없음 | 해당 없음 | 해당 없음 |
> | Wi-fi/BT | 해당 없음 | x | 해당 없음 | 해당 없음 | 해당 없음 | 해당 없음 |
> | 신뢰할 수 있는 i/o | 해당 없음 | 해당 없음 | x | x | x | 해당 없음 |
> | 프로세서 전원 관리 |  | x | x | x | 개발 중 | |
> | TPM | x | x | x | x | x | 해당 없음 |
> | 보안 부팅 | x | x | 개발 중 | 개발 중 | 개발 중 | |
> | 최대 절전 모드 | x | | | | | | 
> | PWM | x | 해당 없음 | x | x | x | |
> | JTAG | x | 해당 없음 | x | x | x | |
> | eMMC | x | x | x | x | x | |
> | SDHC | x | x | x | x | x | x |

## <a name="customized-boards"></a>사용자 지정 보드

사용자의 시나리오에서 작동 하는 연결 옵션을 포함 하는 구성 요소를 사용 하는 경우에는 대개 가장 비용 및 시간 효율성이 좋은 선택이 됩니다.  

대부분의 사용자에 게는 제품이 수십, 000 개 이상의 장치에서 판매 될 것으로 예상 되는 경우 완전 한 사용자 지정 보드를 개발 하는 것이 적합 합니다. 더 작은 볼륨의 경우, SoM을 사용 하 고 사용자 지정 운송 업체 보드를 디자인 하는 대신, 완전히 새로운 보드를 설계 하는 대신를 사용 하면 비용 및 출시 시간을 크게 줄일 수 있을 뿐만 아니라 소프트웨어 개발 및 통합을 간소화할 수 있습니다.

각 플랫폼에는 구현 중 주의가 필요한 고유한 특수 한 권한이 있습니다.  다음은 시작 하는 방법에 대 한 몇 가지 제안 사항입니다. Windows 10 IoT Core를 기반으로 하는 많은 회사가 있지만 다음은 Windows 10 IoT Core를 사용 하 여 작업 하는 입증 된 환경을 제공 하는 일부 목록입니다.

* __[Raspberry Pi](#raspberry-pi-derived-custom-design)__
* __[Intel](#intel-based-custom-design)__
* __[Qualcomm](#qualcomm-dragonboard-410c-apq8016-based-custom-design)__
* __[NXP](#nxp-preview)__

*SoM 공급자 또는 ODM이 고 아래 목록에 추가 하려는 경우 [winiotsomhelp@microsoft.com](mailto:winiotsomhelp@microsoft.com) 전자 메일을 보내거나이 페이지를 직접 편집 하 고 끌어오기 요청을 제출 하세요.*

*여기에 나열 된 많은 회사는 크고 복잡 합니다.  적절 한 사람에 게 연락 하는 데 문제가 있는 경우 [winiotsomhelp@microsoft.com](mailto:winiotsomhelp@microsoft.com) 메일을 보내 주시기 바랍니다.*

### <a name="raspberry-pi-derived-custom-design"></a>**Raspberry Pi 파생 사용자 지정 디자인**

[요소 14](https://www.element14.com/community/docs/DOC-76955/l/raspberry-pi-customization-service) 는 연결 옵션을 추가 또는 제거할 수 있도록 Raspberry Pi에 대 한 보드 사용자 지정 서비스를 제공 합니다. 또한 사용자 지정을 수행 해야 하는 경우 [Github에서 오픈 소스 BSP 코드](https://github.com/ms-iot/rpi-iotcore)를 활용할 수 있습니다.

### <a name="intel-based-custom-design"></a>**Intel 기반 사용자 지정 디자인**

사용할 수 있는 Windows 용 [숙련 된 Intel 장치 빌더](https://solutionsdirectory.intel.com/solutions-directory/processors/278/processors/309/processors/402/processors/782/processors/788/processors/1103/processors/1107/processors/1110/processors/1175/processors/1344/processors/1348/processors/1349) 의 생생한 에코 시스템이 있습니다. Windows 10 IoT Core를 실행 하도록 설계 된 Intel 장치에는 보다 일반적인 Pc와 몇 가지 차이점이 있습니다.

1. I2C, GPIO 및 SPI와 같은 단순 버스에 UWP (사용자 모드 유니버설 Windows 플랫폼) API 액세스를 제공 해야 하는 경우 UEFI 펌웨어의 ACPI 테이블에 RHProxy에 대 한 적절 한 항목이 포함 되어 있는지 확인 해야 합니다. 자세한 내용은 [사용자 모드 액세스](https://docs.microsoft.com/windows/uwp/devices-sensors/enable-usermode-access) 를 참조 하세요.
2. 펌웨어의 SMBIOS에 [OEM 라이선스 요구 사항](https://docs.microsoft.com/windows/iot-core/commercialize-your-device/oemlicenserequirements)에 나열 된 정보가 포함 되어 있는지 확인 해야 합니다.

사용자 고유의 보드를 빌드하는 경우에는 BIOS 공급 업체에 문의 하 여 ACPI 또는 SMBIOS 변경에 대 한 지침이 필요 합니다.

#### <a name="experienced-partners"></a>*숙련 된 파트너*

* [Aaeon](http://www.aaeon.com/en/)
* [Advantech co.](http://www.advantech.com/) -buy@advantech.tw
* [Kontron](http://www.kontron.com/) -martin.unverdorben@kontron.com
* [Nexcom](http://www.nexcom.com/)

### <a name="qualcomm-dragonboard-410c-apq8016-based-custom-design"></a>**Qualcomm DragonBoard 410c (APQ8016) 기반 사용자 지정 디자인**

Qualcomm AQP8016 SoC를 기반으로 하는 DragonBoard 410c의 이진 BSP를 [Qualcomm Developer Network](https://developer.qualcomm.com/hardware/dragonboard-410c/software)에서 다운로드할 수 있습니다.

BSP 패키지에는 acpi를 변경 해야 하는 단순한 하드웨어 사용자 지정을 허용 하는 ACPI의 소스 코드가 포함 되어 있습니다.  

> [!IMPORTANT] 
> 특정 MIPI를 사용 하는 등의 추가 하드웨어 사용자 지정이 필요한 경우 플랫폼 보안 부팅, RF 보정 및 인증을 사용 하도록 설정 합니다 (예: FCC, CE), 액세스 권한이 있는 공급자 (아래에서 숙련 된 파트너 참조)로 작업 하려면 Qualcomm BSP 소스 코드 정식 사용자가 되어야 합니다.

권장 사항:

1. 가능 하면 숙련 된 SoM 공급 업체와 협력 하 여 사용자 지정 디자인을 사용 하도록 설정 합니다.
2. 사용자 지정 보드를 빌드하는 경우에는 SoM 공급 업체 또는 숙련 된 Qualcomm BSP 사용자 지정 서비스 공급자 (예: BSP 사용자 지정 및 디자인 지원에 대 한 [Intrinsyc](https://www.intrinsyc.com/) 또는 [Thundersoft](http://www.thundersoft.com/) )를 사용 하세요.
3. 볼륨이 매우 많은 것으로 간주 되는 경우 (수백만) [Qualcomm에 문의 하세요](https://assets.qualcomm.com/contact-sales-iot.html).

#### <a name="experienced-partners"></a>*숙련 된 파트너*

* [Intrinsyc](https://www.intrinsyc.com/computing-platforms/410-som/) Waldenberg (mwaldenberg@intrinsyc.com)
* [Keith & Koep](https://keith-koep.com/en/products/products-som/myon-1-features-snapdragon-410/) -contact@keith-koep.com
* [Reycom](http://www.reycom.swiss/en/home-swiss.html) -welcome@reycom.swiss
* [Unitech](http://ute.com/products_info.php?pc1=4&pc2=461&rbu=0&pid=2395) -Sam (saml@tw.ute.com); Perry (perryt@te.ute.com)

### <a name="nxp-preview"></a>**NXP 미리 보기**

NXP for Windows 10 IoT Core는 공개 미리 보기로 제공 됩니다. 자세한 내용은 BSP에 액세스 하거나 하드웨어 파트너를 찾으려면 [Nxp SoC 페이지로](https://aka.ms/iotnxp)이동 하세요.

작업 중인 파트너에 게 연락할 수도 있습니다.

* Advantech co. [Rsb-4411](http://www.advantech.com/products/single_board_computer/rsb-4411/mod_d3901250-b0a0-4a5f-9762-b26fa0c36858) -buy@advantech.tw
* Keith & Koep [Pconxs](https://keith-koep.com/de/produkte/produkte-baseboards/pconxs-baseboard-vollausstattung-technische-daten/
) 와 [Trizeps vii](https://keith-koep.com/de/produkte/produkte-trizeps/trizeps-vii-technische-daten-imx6/) -contact@keith-koep.com
* Kontron [SMARC-sAMX6i](https://www.kontron.com/products/boards-and-standard-form-factors/smarc/smarc-samx6i.html) -Martin Unverdorben (martin.unverdorben@kontron.com)
* Solid Run [Hummingboard Edge](https://www.solid-run.com/imx6-win-10-iot-core/ )-ilya (ilya@solid-run.com)
* Geniatech [som-iMX6Q-Q7](https://www.geniatech.com/product/som-imx6q-q7/) & [som-IMX7D](https://www.geniatech.com/product/som-imx7d/) -Mike Decker (mike.decker@geniatech.com) 또는 Fang Jijun (Fjj@geniatech.com)
* VIA [Vab-820](https://www.viaembeddedstore.com/shop/boards/vab-820/) -Michael Fox (MichaelFox@via.com.tw) 또는 꿈 Ku (dreamku@via.com.tw)
* Phytec [phyBOARD-i. MX7](https://phytec.com/products/single-board-computers/phyboard-i.mx7/) -Brad Dodson (sales@phytec.com)


## <a name="other-options"></a>기타 옵션

사용자 지정 보드를 만들어야 하는 경우 보드의 계통도와 레이아웃에 도움이 될 수 있는 아래 제조업체의 제안 사항을 제공 합니다.

* [모든 PCB](http://www.allpcb.com/)
* [Geppetto/Gumstix](https://www.gumstix.com/geppetto/)
* [JLC PCB](https://jlcpcb.com/)
* [Myro PCB](http://www.myropcb.com/)
* [OSH 공원](https://oshpark.com/)
* [seeed studio](https://www.seeedstudio.com/)
