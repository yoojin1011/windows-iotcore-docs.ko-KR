---
title: Windows IoT 및 NXP i.MX
author: chsha
ms.author: chsha
ms.date: 02/22/2019
ms.topic: article
description: Windows 10 IoT Core 및 NXP i.MX Soc에 대 한 자세한 정보
keywords: Windows 10 IoT Core, 시작 하기, i.MX, NXP
ms.openlocfilehash: 244d767507393680df7a48487522ff62be40692d
ms.sourcegitcommit: c5552007f5456e57512307f51b146406a23fa723
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/02/2019
ms.locfileid: "68739809"
---
# <a name="window-10-iot-core-and-nxp-imx-socs"></a>Windows 10 IoT Core 및 NXP i.MX Soc

2018에서 Microsoft 및 NXP는 NXP i.MX 6 및 i.MX 7 실리콘의 Windows 10 IoT Core 비공개 미리 보기를 발표 하 고 i.MX 8M Soc에서 작업을 시작 했습니다. 수백 명의 상업적 개발자, 연구원 및 결정자는 10 년간의 Windows 보안 업데이트와 NXP 실리콘의 유연성 및 안정성을 조합 하 여 관심을 표현 했습니다. 
 
미리 보기 중에 Microsoft 및 NXP 엔지니어는 솔루션을 평가 하는 입력을 기반으로 하는 수천 개의 시간을 조정 하 고 개선 했습니다. Microsoft는 기존 산업 컨트롤러 현대화에 관심이 있는 고객을 위해 노력 하 고 있으며, 자동화 솔루션을 구축 하는 새로운 클라우드를 개발 하 고, [신뢰할 수 있는 i/o](https://blogs.windows.com/windowsexperience/2018/04/24/trusted-cyber-physical-systems-looks-to-protect-your-critical-infrastructure-from-modern-threats-in-the-world-of-iot/#A0WkfgLBpgbLaFe3.97)와 같은 클래스의 주요 보안을 사용 합니다.
 
이제 Microsoft와 NXP는 솔루션에서 흥미로운 관심을 바탕으로 i.MX 6, i.MX 7 및 i.MX 8M 제품군의 BSPs를 비상업용 공개 미리 보기로 사용할 수 있도록 합니다. Microsoft와 NXP가 포함 된 및 IoT 시장에 포함 되어 있으므로 설계 유연성이 필요 하다는 것을 이해 하 고 있습니다. 따라서 Microsoft, NXP 및 하드웨어 파트너를 사용 하는 여러 단일 보드 컴퓨터 및 시스템의 시스템 뿐만 아니라 i.MX 6, i.MX 7 및 i.MX 8M BSPs가 오픈 소스 라이선스에 제공 됩니다. 이제 모든 사용자가 Windows 10 IoT Core의 10 월 2018 릴리스와 함께 하드웨어에서 평가를 사용 하기 위해 i.MX 6, i.MX 7 및 i.MX 8M 제품군에 대 한 전체 BSP 콘텐츠에 액세스할 수 있습니다.


## <a name="bsp-access"></a>BSP 액세스

사용자 고유의 i.MX 하드웨어에 대 한 지원을 사용 하도록 설정 하려는 경우 [Github]( https://github.com/ms-iot/imx-iotcore)의 BSP 원본 및 설명서에 액세스 하세요. 언급 하지 않는 한 원본의 대부분은 MIT 라이선스에서 제공 됩니다. NXP에서 제공 하는 지원과 함께 상업적 사용을 위해 코드가 릴리스 되었으며 [여기](https://www.nxp.com/support/developer-resources/evaluation-and-development-boards/i.mx-evaluation-and-development-boards/i.mx-software-and-development-tool:IMX-SW)에서 찾을 수 있습니다.

NXP 하드웨어/t o 관련 질문이 있거나 BSP에서 대상 솔루션을 더 잘 지원할 수 있는 방법에 대 한 의견이 있는 경우 [Nxp 커뮤니티](https://community.nxp.com/community/imx/content?filterID=contentstatus%5Bpublished%5D%7Ecategory%5Bwindows%5D)에 게시 해 주세요. Windows 관련 질문에 대해서는 [Microsoft 커뮤니티](https://social.msdn.microsoft.com/forums/en-US/home?forum=WindowsIoT)를 사용 하세요.


## <a name="ecosystem-resources"></a>에코 시스템 리소스

여러 Microsoft 및 NXP 파트너는 Windows 10 IoT Core를 지 원하는 상업적 i.MX 6, i.MX 7, i.MX 8M 장치를 사용 하도록 설정 했습니다. 하드웨어 및 플랫폼 이미지에 대해서는 파트너에 게 직접 문의 하세요.


> | 디바이스 | 연락처 |
> |-------|------|
> | [Aaeon PICO-IMX6](https://www.aaeon.com/en/p/pico-itx-boards-pico-imx6/) | [David 중단](mailto:davidhung@aaeon.com.tw) |
> | [Advantech co. RSB-4411](http://www.advantech.com/products/single_board_computer/rsb-4411/mod_d3901250-b0a0-4a5f-9762-b26fa0c36858) | [buy@advantech.com](mailto:buy@advantech.com) |
> | [Compulab IoT-게이트](https://www.compulab.com/products/iot-gateways/iot-gate-imx7-nxp-i-mx-7-internet-of-things-gateway/) | [Igor Vaisbein](mailto:igor@compulab.co.il) | 
> | [FS Eletronik 시스템 서버의 armStone A9](https://www.fs-net.de/en/products/armstone/armstonea9/) | [support@fs-net.de](mailto:support@fs-net.de) |
> | [Geniatech SoM-iMX6Q-Q7](https://www.geniatech.com/product/som-imx6q-q7/) | [Mike Decker](mailto:mike.decker@geniatech.com) 또는 [Fang Jijun](mailto:Fjj@geniatech.com) |
> | [Geniatech SoM-iMX7D](https://www.geniatech.com/product/som-imx7d/) | [Mike Decker](mailto:mike.decker@geniatech.com) 또는 [Fang Jijun](mailto:Fjj@geniatech.com) |
> | [TX6UL, TX6S, TX6DL 및 TX6Q](https://www.karo-electronics.de/tx-standard.html?&L=1) | [Steinkohl](mailto:us@karo-electronics.de) |
> | [Keith & Koep pConXS](https://keith-koep.com/de/produkte/produkte-baseboards/pconxs-baseboard-vollausstattung-technische-daten/) 와 [Trizeps vii](https://keith-koep.com/de/produkte/produkte-trizeps/trizeps-vii-technische-daten-imx6/) | [contact@keith-koep.com](mailto:contact@keith-koep.com) |
> | [Kontron SMARC-sAMX6i](https://www.kontron.com/products/boards-and-standard-form-factors/smarc/smarc-samx6i.html) | [Martin Unverdorben](mailto:martin.unverdorben@kontron.com) |
> | [Novtech Meerkat](http://novtech.com/products/meerkat96.html) | [sales@novtech.com](mailto:sales@novtech.com) |
> | [phyBOARD-i.MX 7 개발 키트](https://phytec.com/product/phyboard-imx7-development-kit/) | [김철수](mailto:sales@phytec.com) |
> | [Solid Run Hummingboard Edge](https://www.solid-run.com/imx6-win-10-iot-core/) | [Ilya](mailto:ilya@solid-run.com) |
> | [VIA VAB-820](https://www.viaembeddedstore.com/shop/boards/vab-820/) | [Michael Fox](mailto:MichaelFox@via.com.tw) 또는 [꿈 Ku](mailto:dreamku@via.com.tw) |
> | [WeAreDev WAD-MX6W](http://www.wearedev.net/?mod=wadmx6w) | [help@wearedev.net](mailto:help@wearedev.net) |
> | [MCIMX6ULL-EVK](https://www.nxp.com/products/processors-and-microcontrollers/arm-based-processors-and-mcus/i.mx-applications-processors/i.mx-6-processors/evaluation-kit-for-the-i.mx-6ull-and-6ulz-applications-processor:MCIMX6ULL-EVK) | [Wei Wang](mailto:Wei.A.Wang@nxp.com) |
> | [MCIMX8M-EVK](https://www.nxp.com/support/developer-resources/software-development-tools/i.mx-developer-resources/evaluation-kit-for-the-i.mx-8m-applications-processor:MCIMX8M-EVK) |  |
> | [MCIMX8MMINI-EVK](http://www.nxp.com/imx8mminievk) | []() |
