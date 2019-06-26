---
title: 시작 개요
author: saraclay
ms.author: saclayt
ms.date: 04/10/2018
ms.topic: article
description: Windows 10 IoT Core를 시작하는 방법을 알아봅니다.
keywords: Windows 10 IoT Core, 시작, 이미지
ms.openlocfilehash: c11e37c982c1e38ec270527d54127013b8df7515
ms.sourcegitcommit: 9ec4716afde25fdc8b94f7c0794448501f451b55
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/17/2019
ms.locfileid: "66373147"
---
# <a name="get-started-with-windows-10-iot-core"></a>Windows 10 IoT Core 시작

어떤 도움도 받지 않고 혼자 디바이스를 만드는 것은 재미있기도 하지만, 매우 버거운 일일 수도 있습니다. 아래는 프로토타입 제작 또는 상용화를 도와주는 리소스입니다. 

이 과정에서 궁금한 점이 있나요? Microsoft 담당자와 협력하거나 [Windows 10 IoT 포럼](https://social.msdn.microsoft.com/forums/en-US/home?forum=WindowsIoT)에 질문을 게시하세요.

## <a name="what-is-windows-10-iot"></a>Windows 10 IoT란?

제품에 대한 자세한 내용은 아래 설명서를 참조하세요. 

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">항목</th>
<th align="left">설명</th>
</tr>
</thead>
<tbody>

<tr class="odd">
<td align="left"><p><a href="windows-iot.md" data-raw-source="[Windows IoT Overview](windows-iot.md)">Windows IoT 개요</a></p></td>
<td align="left"><p>두 Windows 10 IoT 제품을 비교하여 어떤 솔루션이 더 적합한지 알아보세요.</p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="windows-iot-enterprise.md" data-raw-source="[Windows 10 IoT Enterprise Overview](windows-iot-enterprise.md)">Windows 10 IoT Enterprise 개요</a></p></td>
<td align="left"><p>Windows 10 IoT Enterprise를 시작하는 방법을 자세히 알아보세요.</p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="windows-iot-core.md" data-raw-source="[Windows 10 IoT Core Overview](windows-iot-core.md)">Windows 10 IoT Core 개요</a></p></td>
<td align="left"><p>Windows 10 IoT Core를 시작하는 방법을 자세히 알아보세요.</p></td>
</tr>

<tr class="odd">
  <td align="left"><p><a href="windows-server.md" data-raw-source="[Windows Server IoT 2019](https://docs.microsoft.com/en-us/windows/iot-core/windows-server)">Windows Server IoT 2019</a></p></td>
<td align="left"><p>Windows Server IoT 2019를 시작하는 방법을 자세히 알아보세요.</p></td>
</tr>

</tbody>
</table>

## <a name="windows-10-iot-pricing"></a>Windows 10 IoT 가격 책정

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">용도</th>
<th align="left">가격 책정</th>
</tr>
</thead>
<tbody>

<tr class="odd">
<td align="left"><p>프로토타입 제작</p></td>
<td align="left"><p>무료</p></td>
</tr>

<tr class="odd">
<td align="left"><p>상용화를 위한 LTSC(장기 서비스 채널)</p></td>
<td align="left"><p>소액의 디바이스당 요금을 지불하면 10년 지원, 업데이트 제어 및 DHA(디바이스 상태 증명)를 사용할 수 있습니다. <a href="https://docs.microsoft.com/windows-hardware/manufacture/iot/iotcoreservicesoverview" data-raw-source="[here](https://docs.microsoft.com/windows-hardware/manufacture/iot/iotcoreservicesoverview)">여기</a>에서 자세한 내용을 알아보세요.</p></td>
</tr>

<tr class="odd">
<td align="left"><p>상용화를 위한 SAC(반기 채널)</p></td>
<td align="left"><p>무료지만 10년 지원, 업데이트 제어 및 DHA를 사용할 수 없습니다. 또한 상용화 계약에 서명해야 합니다. <a href="https://www.aka.ms/SAC-agreement">여기</a>서 요청하세요.</p></td>
</tr>

</tbody>
</table>

<i>[여기](https://support.microsoft.com/en-us/lifecycle/search?alpha=IoT%20Core)서 자세한 수명 주기 정보를 알아보세요</i>.

## <a name="prototype-a-device"></a>디바이스 프로토타입

디바이스를 제작하기 전에, 먼저 Windows 10 IoT Core를 사용하여 디바이스의 프로토타입을 만드는 것이 좋습니다. 이렇게 하면 디바이스를 만들 때 어떤 기능이 필요하고 어떤 구성을 원하는지 알아볼 수 있습니다.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">항목</th>
<th align="left">설명</th>
</tr>
</thead>
<tbody>

<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/en-us/windows/iot-core/tutorials/quickstarter/PrototypeBoards"
>1. 프로토타입 보드 선택</a></p></td>
<td align="left"><p>일반 프로토타입 보드를 살펴보고 프로토타입 제작에 사용할 프로토타입 보드를 선택합니다.</p></td>
</tr>

<tr class="odd">
<td align="left"><p>2. 프로토타입 이미지 플래시</p></td>
<td align="left"><p>선택한 디바이스에 프로토타입 이미지를 플래시하는 방법을 알아보려면 자습서 섹션으로 이동합니다. </p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/en-us/windows/iot-core/develop-your-app/appinstaller">3. 앱 설치</a></p></td>
<td align="left"><p>다양한 도구를 사용하여 앱을 설치하는 방법을 알아봅니다.</p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/en-us/windows/iot-core/develop-your-app/appdeployment">4. 앱 배포</a></p></td>
<td align="left"><p>Visual Studio를 사용하여 앱을 배포하는 방법을 알아봅니다.</p></td>
</tr>

</tbody>
</table>

## <a name="bring-a-device-to-market"></a>디바이스 출시

디바이스를 상용화 또는 출시하려면 한가한 시간에 디바이스의 프로토타입을 제작하는 것보다 훨씬 많은 과정과 인력이 필요합니다. 디바이스가 전 세계 어디에 있든, 디바이스를 상용화하려면 디바이스의 보안과 규정 준수를 보장하기 위한 수많은 단계가 필요합니다. 

현재 사용하는 Windows 10 IoT 버전에 가장 적합한 제작 가이드에 따라 시작하세요.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">항목</th>
<th align="left">설명</th>
</tr>
</thead>
<tbody>

<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide"
>Windows 10 IoT Core 제작 가이드</a></p></td>
<td align="left"><p>이 가이드로 시작하여 상용 Windows 10 IoT Core 솔루션의 사용자 지정 테스트 및 정품 이미지를 만드는 방법을 알아보세요.</p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/iot-ent-overview">Windows 10 IoT Enterprise 제작 가이드</a></p></td>
<td align="left"><p>이 가이드로 시작하여 상용 Windows 10 IoT Enterprise 솔루션의 이미지를 만드는 방법을 알아보세요.</p></td>
</tr>

</tbody>
</table>
