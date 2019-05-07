---
title: Windows IoT 및 NXP i.MX
author: chsha
ms.author: chsha
ms.date: 02/22/2019
ms.topic: article
description: 및 NXP i.MX Soc Windows 10 IoT Core 알아봅니다
keywords: Windows 10 IoT Core 시작 i.MX, NXP
ms.openlocfilehash: a6331b8f5695c2a432e1b22f1ba275cd48c549e4
ms.sourcegitcommit: 3eacb968296e79e7e981fdc2a6f7f4f69c0920d1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65040188"
---
# <a name="window-10-iot-core-and-nxp-imx-socs"></a><span data-ttu-id="be87f-104">Window 10 IoT Core 및 NXP i.MX Soc</span><span class="sxs-lookup"><span data-stu-id="be87f-104">Window 10 IoT Core and NXP i.MX SoCs</span></span>

<span data-ttu-id="be87f-105">2018 년 5 월에서 Microsoft NXP NXP i.MX 6 및 7 i.MX 실리콘에서 Windows 10 IoT Core 비공개 미리 보기를 발표 하 고 8m i.MX 작업 시작 Soc 합니다.</span><span class="sxs-lookup"><span data-stu-id="be87f-105">In 2018, Microsoft and NXP announced a private preview of Windows 10 IoT Core on NXP i.MX 6 and i.MX 7 silicon and began work on the i.MX 8M SoCs.</span></span> <span data-ttu-id="be87f-106">수백 개의 상업용 제품 개발자, 연구원 및 결정권자 10 년 동안 Windows 보안 업데이트 및 유연성 및 안정성 NXP 실리콘의 조합에서 자신의 관심사를 표현 됩니다.</span><span class="sxs-lookup"><span data-stu-id="be87f-106">Hundreds of commercial developers, researchers, and Makers expressed their interest in the combination of 10 years of Windows security updates and the flexibility and reliability of NXP silicon.</span></span> 
 
<span data-ttu-id="be87f-107">미리 보기에서 Microsoft 및 NXP 엔지니어 수천 개의 솔루션 평가에서 입력을 기반으로 튜닝 하 고 BSP 향상 시간 소요 합니다.</span><span class="sxs-lookup"><span data-stu-id="be87f-107">During the preview, Microsoft and NXP engineers spent thousands of hours tuning and improving the BSP based on input from those evaluating the solution.</span></span> <span data-ttu-id="be87f-108">레거시 산업 현대화에 관심이 있는 고객 들과 협력 컨트롤러 자동화 솔루션을 구축 하는 연결 된 새 클라우드 개발 및 사용 하 여 게이트웨이 선행 보안 클래스 [I/O를 신뢰할 수 있는](https://blogs.windows.com/windowsexperience/2018/04/24/trusted-cyber-physical-systems-looks-to-protect-your-critical-infrastructure-from-modern-threats-in-the-world-of-iot/#A0WkfgLBpgbLaFe3.97)합니다.</span><span class="sxs-lookup"><span data-stu-id="be87f-108">We worked with customers interested in modernizing legacy industrial controllers, developing new cloud connected building automation solutions, and gateways with class leading security such as [trusted I/O](https://blogs.windows.com/windowsexperience/2018/04/24/trusted-cyber-physical-systems-looks-to-protect-your-critical-infrastructure-from-modern-threats-in-the-world-of-iot/#A0WkfgLBpgbLaFe3.97).</span></span>
 
<span data-ttu-id="be87f-109">매우 많은 관심이 솔루션에 따라 Microsoft 및 NXP 이제 중인 Bsp i.MX 6, 7, i.MX 및 Soc i.MX 8m 제품군에 대 한 비 상업적 공개 미리 보기로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be87f-109">Based on the overwhelming interest in the solution, Microsoft and NXP are now making BSPs for the i.MX 6, i.MX 7, and i.MX 8M family of SoCs available as a non-commercial public preview.</span></span> <span data-ttu-id="be87f-110">긴 기록으로 인해 Microsoft 및 NXP에 포함 및 IoT 시장, 디자인 유연성에 대 한 필요성을 이해 했습니다.</span><span class="sxs-lookup"><span data-stu-id="be87f-110">Because of the long history Microsoft and NXP have in the embedded and IoT markets, we understand the need for design flexibility.</span></span> <span data-ttu-id="be87f-111">따라서, 외에도 여러 단일 보드 컴퓨터 및 시스템 모듈 솔루션 Microsoft NXP, 파트너 사용 하도록 설정 하는 하드웨어, 고 i.MX 6, 7, i.MX i.MX 8m Bsp 나와 오픈 소스 라이선스 아래 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be87f-111">Therefore, in addition to the multiple single board computers and system on module solutions Microsoft, NXP, and our hardware partners have enabled, the i.MX 6, i.MX 7, and i.MX 8M BSPs are provided under open source licensing.</span></span> <span data-ttu-id="be87f-112">이제 everyone i.MX 6, 7, i.MX 및 i.MX 8m 기술 제품군의 2018 년 10 월 릴리스의 Windows 10 IoT Core 함께 해당 하드웨어에서 평가 사용에 대 한 전체 BSP 내용에 액세스할 수 없게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="be87f-112">Now, everyone will be able to access the complete BSP contents for the i.MX 6, i.MX 7, and i.MX 8M product families for evaluation use on their hardware along with the October 2018 release of Windows 10 IoT Core.</span></span>


## <a name="bsp-access"></a><span data-ttu-id="be87f-113">BSP 액세스</span><span class="sxs-lookup"><span data-stu-id="be87f-113">BSP Access</span></span>

<span data-ttu-id="be87f-114">사용자 고유의 i.MX 하드웨어에 대 한 지원을 사용 하도록 설정 하려면 BSP 소스 및 설명서에 액세스 하세요 관심이 있다면 [Github]( https://github.com/ms-iot/imx-iotcore)합니다.</span><span class="sxs-lookup"><span data-stu-id="be87f-114">If you are interested to enable support for your own i.MX hardware, please access the BSP source and documentation on [Github]( https://github.com/ms-iot/imx-iotcore).</span></span> <span data-ttu-id="be87f-115">설명이 없는 한, 대부분의 원본 MIT 라이선스로 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="be87f-115">Unless noted, the majority of the source is provided under MIT license.</span></span> <span data-ttu-id="be87f-116">아직 개발 중인 코드가입니다.</span><span class="sxs-lookup"><span data-stu-id="be87f-116">The code is still under development.</span></span> <span data-ttu-id="be87f-117">모든 플랫폼 기능을 활성화 하거나 액세스에 최적화 된 완벽 하 게 합니다.</span><span class="sxs-lookup"><span data-stu-id="be87f-117">Not all platform features are fully enabled or optimized.</span></span> <span data-ttu-id="be87f-118">현재 코드를 시간에만 비 상업적 개발을 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="be87f-118">The code is currently intended for non-commercial development only at time time.</span></span> <span data-ttu-id="be87f-119">상용 품질 릴리스 2019 뒷부분에서 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="be87f-119">A commercial quality release is expected later in 2019.</span></span>

<span data-ttu-id="be87f-120">NXP 하드웨어/BSP 관련 질문이 나 BSP 대상된 솔루션 더 잘 지 원하는 방법에 대 한 피드백 경우 포럼에 [NXP 커뮤니티](https://community.nxp.com/community/imx/content?filterID=contentstatus%5Bpublished%5D%7Ecategory%5Bwindows%5D)합니다.</span><span class="sxs-lookup"><span data-stu-id="be87f-120">If you have NXP hardware/BSP releated questions or feedback on how the BSP can better support your targeted solution, please post to the [NXP Community](https://community.nxp.com/community/imx/content?filterID=contentstatus%5Bpublished%5D%7Ecategory%5Bwindows%5D).</span></span> <span data-ttu-id="be87f-121">Windows 관련된 질문을 사용 합니다 [Microsoft 커뮤니티](https://social.msdn.microsoft.com/forums/en-US/home?forum=WindowsIoT)합니다.</span><span class="sxs-lookup"><span data-stu-id="be87f-121">For any Windows related questions, please use the [Microsoft Community](https://social.msdn.microsoft.com/forums/en-US/home?forum=WindowsIoT).</span></span>


## <a name="ecosystem-resources"></a><span data-ttu-id="be87f-122">에코 시스템 리소스</span><span class="sxs-lookup"><span data-stu-id="be87f-122">Ecosystem Resources</span></span>

<span data-ttu-id="be87f-123">여러 Microsoft 및 NXP 파트너 상용 i.MX 6, 7, i.MX 사용 하도록 설정 하 고 i.MX 8m 장치를 Windows 10 IoT Core 대 한 지원.</span><span class="sxs-lookup"><span data-stu-id="be87f-123">Several Microsoft and NXP partners have enabled commercial i.MX 6, i.MX 7, and i.MX 8M devices with support for Windows 10 IoT Core.</span></span> <span data-ttu-id="be87f-124">하드웨어 및 플랫폼 이미지를 직접 파트너에 문의 하세요.</span><span class="sxs-lookup"><span data-stu-id="be87f-124">Please contact the partner directly for hardware and a platform image.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="be87f-125">장치</span><span class="sxs-lookup"><span data-stu-id="be87f-125">Device</span></span></th>
<th align="left"><span data-ttu-id="be87f-126">연락처</span><span class="sxs-lookup"><span data-stu-id="be87f-126">Contact</span></span></th>
</tr>
</thead>
<tbody>

<tr class="odd">
<td align="left"><p><span data-ttu-id="be87f-127"><a href="https://www.aaeon.com/en/p/pico-itx-boards-pico-imx6/">Aaeon PICO-IMX6</a></span><span class="sxs-lookup"><span data-stu-id="be87f-127"><a href="https://www.aaeon.com/en/p/pico-itx-boards-pico-imx6/">Aaeon PICO-IMX6</a></span></span></p></td>
<td align="left"><p><p><span data-ttu-id="be87f-128"><a href="mailto:davidhung@aaeon.com.tw">David 여 닫</a></span><span class="sxs-lookup"><span data-stu-id="be87f-128"><a href="mailto:davidhung@aaeon.com.tw">David Hung</a></span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><p><span data-ttu-id="be87f-129"><a href="http://www.advantech.com/products/single_board_computer/rsb-4411/mod_d3901250-b0a0-4a5f-9762-b26fa0c36858">Advantech RSB-4411</a></span><span class="sxs-lookup"><span data-stu-id="be87f-129"><a href="http://www.advantech.com/products/single_board_computer/rsb-4411/mod_d3901250-b0a0-4a5f-9762-b26fa0c36858">Advantech RSB-4411</a></span></span></p></td>
<td align="left"><p><p><a href="mailto:buy@advantech.com">buy@advantech.com</a></p></td>
</tr>

<tr class="odd">
<td align="left"><p><span data-ttu-id="be87f-130"><a href="https://www.compulab.com/products/iot-gateways/iot-gate-imx7-nxp-i-mx-7-internet-of-things-gateway/">Compulab IoT-Gate</a></span><span class="sxs-lookup"><span data-stu-id="be87f-130"><a href="https://www.compulab.com/products/iot-gateways/iot-gate-imx7-nxp-i-mx-7-internet-of-things-gateway/">Compulab IoT-Gate</a></span></span></p></td>
<td align="left"><p><p><span data-ttu-id="be87f-131"><a href="mailto:igor@compulab.co.il">Igor Vaisbein</a></span><span class="sxs-lookup"><span data-stu-id="be87f-131"><a href="mailto:igor@compulab.co.il">Igor Vaisbein</a></span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><p><span data-ttu-id="be87f-132"><a href="https://www.geniatech.com/product/som-imx6q-q7/">Geniatech SoM-iMX6Q-Q7</a></span><span class="sxs-lookup"><span data-stu-id="be87f-132"><a href="https://www.geniatech.com/product/som-imx6q-q7/">Geniatech SoM-iMX6Q-Q7</a></span></span></p></td>
<td align="left"><p><p><span data-ttu-id="be87f-133"><a href="mailto:mike.decker@geniatech.com">Mike Decker</a> 또는 <a href="mailto:Fjj@geniatech.com">팡 Jijun</a></span><span class="sxs-lookup"><span data-stu-id="be87f-133"><a href="mailto:mike.decker@geniatech.com">Mike Decker</a> or <a href="mailto:Fjj@geniatech.com">Fang Jijun</a></span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><p><span data-ttu-id="be87f-134"><a href="https://www.geniatech.com/product/som-imx7d/">Geniatech SoM-iMX7D</a></span><span class="sxs-lookup"><span data-stu-id="be87f-134"><a href="https://www.geniatech.com/product/som-imx7d/">Geniatech SoM-iMX7D</a></span></span></p></td>
<td align="left"><p><p><span data-ttu-id="be87f-135"><a href="mailto:mike.decker@geniatech.com">Mike Decker</a> 또는 <a href="mailto:Fjj@geniatech.com">팡 Jijun</a></span><span class="sxs-lookup"><span data-stu-id="be87f-135"><a href="mailto:mike.decker@geniatech.com">Mike Decker</a> or <a href="mailto:Fjj@geniatech.com">Fang Jijun</a></span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><p><span data-ttu-id="be87f-136"><a href="https://www.karo-electronics.de/tx-standard.html?&L=1">Ka-Ro Electronics TX6UL, TX6S, TX6DL, and TX6Q</a></span><span class="sxs-lookup"><span data-stu-id="be87f-136"><a href="https://www.karo-electronics.de/tx-standard.html?&L=1">Ka-Ro Electronics TX6UL, TX6S, TX6DL, and TX6Q</a></span></span></p></td>
<td align="left"><p><p><span data-ttu-id="be87f-137"><a href="mailto:us@karo-electronics.de">Uwe Steinkohl</a></span><span class="sxs-lookup"><span data-stu-id="be87f-137"><a href="mailto:us@karo-electronics.de">Uwe Steinkohl</a></span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><p><span data-ttu-id="be87f-138"><a href="https://keith-koep.com/de/produkte/produkte-baseboards/pconxs-baseboard-vollausstattung-technische-daten/">Keith & Koep pConXS</a> 사용 하 여 <a href="https://keith-koep.com/de/produkte/produkte-trizeps/trizeps-vii-technische-daten-imx6/">Trizeps VII</a></span><span class="sxs-lookup"><span data-stu-id="be87f-138"><a href="https://keith-koep.com/de/produkte/produkte-baseboards/pconxs-baseboard-vollausstattung-technische-daten/">Keith & Koep pConXS</a> with <a href="https://keith-koep.com/de/produkte/produkte-trizeps/trizeps-vii-technische-daten-imx6/">Trizeps VII</a></span></span></p></td>
<td align="left"><p><p><a href="mailto:contact@keith-koep.com">contact@keith-koep.com</a></p></td>
</tr>

<tr class="odd">
<td align="left"><p><span data-ttu-id="be87f-139"><a href="https://www.kontron.com/products/boards-and-standard-form-factors/smarc/smarc-samx6i.html">Kontron SMARC-sAMX6i</a></span><span class="sxs-lookup"><span data-stu-id="be87f-139"><a href="https://www.kontron.com/products/boards-and-standard-form-factors/smarc/smarc-samx6i.html">Kontron SMARC-sAMX6i</a></span></span></p></td>
<td align="left"><p><p><span data-ttu-id="be87f-140"><a href="mailto:martin.unverdorben@kontron.com">Martin Unverdorben</a></span><span class="sxs-lookup"><span data-stu-id="be87f-140"><a href="mailto:martin.unverdorben@kontron.com">Martin Unverdorben</a></span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><p><span data-ttu-id="be87f-141"><a href="https://phytec.com/product/phyboard-imx7-development-kit/">phyBOARD-i.MX 7 개발 키트</a></span><span class="sxs-lookup"><span data-stu-id="be87f-141"><a href="https://phytec.com/product/phyboard-imx7-development-kit/">phyBOARD-i.MX 7 Development Kit</a></span></span></p></td>
<td align="left"><p><p><span data-ttu-id="be87f-142"><a href="mailto:sales@phytec.com">Fernando Benitez</a></span><span class="sxs-lookup"><span data-stu-id="be87f-142"><a href="mailto:sales@phytec.com">Fernando Benitez</a></span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><p><span data-ttu-id="be87f-143"><a href="https://www.solid-run.com/imx6-win-10-iot-core/">Solid Run Hummingboard Edge</a></span><span class="sxs-lookup"><span data-stu-id="be87f-143"><a href="https://www.solid-run.com/imx6-win-10-iot-core/">Solid Run Hummingboard Edge</a></span></span></p></td>
<td align="left"><p><p><span data-ttu-id="be87f-144"><a href="mailto:ilya@solid-run.com">Ilya Viten</a></span><span class="sxs-lookup"><span data-stu-id="be87f-144"><a href="mailto:ilya@solid-run.com">Ilya Viten</a></span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><p><span data-ttu-id="be87f-145"><a href="https://www.viaembeddedstore.com/shop/boards/vab-820/">VIA VAB-820</a></span><span class="sxs-lookup"><span data-stu-id="be87f-145"><a href="https://www.viaembeddedstore.com/shop/boards/vab-820/">VIA VAB-820</a></span></span></p></td>
<td align="left"><p><p><span data-ttu-id="be87f-146"><a href="mailto:MichaelFox@via.com.tw">Michael Fox</a> 또는 <a href="mailto:dreamku@via.com.tw">ku가 Dream</span><span class="sxs-lookup"><span data-stu-id="be87f-146"><a href="mailto:MichaelFox@via.com.tw">Michael Fox</a> or <a href="mailto:dreamku@via.com.tw">Dream Ku</span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><p><span data-ttu-id="be87f-147"><a href="https://www.nxp.com/products/processors-and-microcontrollers/arm-based-processors-and-mcus/i.mx-applications-processors/i.mx-6-processors/evaluation-kit-for-the-i.mx-6ull-and-6ulz-applications-processor:MCIMX6ULL-EVK">MCIMX6ULL-EVK</a></span><span class="sxs-lookup"><span data-stu-id="be87f-147"><a href="https://www.nxp.com/products/processors-and-microcontrollers/arm-based-processors-and-mcus/i.mx-applications-processors/i.mx-6-processors/evaluation-kit-for-the-i.mx-6ull-and-6ulz-applications-processor:MCIMX6ULL-EVK">MCIMX6ULL-EVK</a></span></span></p></td>
<td align="left"><p><p><span data-ttu-id="be87f-148"><a href="mailto:Wei.A.Wang@nxp.com">Wei Wang</a></span><span class="sxs-lookup"><span data-stu-id="be87f-148"><a href="mailto:Wei.A.Wang@nxp.com">Wei Wang</a></span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><p><span data-ttu-id="be87f-149"><a href="https://www.nxp.com/support/developer-resources/software-development-tools/i.mx-developer-resources/evaluation-kit-for-the-i.mx-8m-applications-processor:MCIMX8M-EVK">MCIMX8M-EVK</a></span><span class="sxs-lookup"><span data-stu-id="be87f-149"><a href="https://www.nxp.com/support/developer-resources/software-development-tools/i.mx-developer-resources/evaluation-kit-for-the-i.mx-8m-applications-processor:MCIMX8M-EVK">MCIMX8M-EVK</a></span></span></p></td>
<td align="left"></td>
</tr>

<tr class="odd">
<td align="left"><p><span data-ttu-id="be87f-150"><a href="http://www.nxp.com/imx8mminievk">MCIMX8MMINI-EVK</a></span><span class="sxs-lookup"><span data-stu-id="be87f-150"><a href="http://www.nxp.com/imx8mminievk">MCIMX8MMINI-EVK</a></span></span></p></td>
<td align="left"></td>
</tr>
</tbody>
</table>
