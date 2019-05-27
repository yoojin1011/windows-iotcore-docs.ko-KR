---
title: 가져오기 시작 개요
author: saraclay
ms.author: saclayt
ms.date: 04/10/2018
ms.topic: article
description: Windows 10 IoT Core 사용 하 여 시작 하는 방법을 알아봅니다.
keywords: Windows 10 IoT Core, 시작 이미지
ms.openlocfilehash: d52fbf7efe5f61e99910d26a02304dc16fabb683
ms.sourcegitcommit: 8aadc776da7b473159f9023cd555145819e7e952
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66174012"
---
# <a name="get-started-with-windows-10-iot-core"></a>Windows 10 IoT Core 시작

고유한 장치를 만드는 흥미로운 부분 이지만 이해 하는 위협적일 수도 있습니다. 아래 리소스 도움이 프로토타입 또는 상용화 경험 합니다. 

이 과정에서 질문이 있나요? Microsoft 담당자와 함께 또는에 질문을 게시 하세요. 당사의 [Windows 10 IoT 포럼](https://social.msdn.microsoft.com/forums/en-US/home?forum=WindowsIoT)합니다.

## <a name="what-is-windows-10-iot"></a>Windows 10 IoT 란?

이 제품에 대 한 자세한 내용은 자세히 알아보려면 아래 설명서를 참조 하세요. 

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
<td align="left"><p>두 개의 Windows 10 IoT 제품을 비교 하 고 적합 하는 방법은 참조 하세요.</p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="windows-iot-enterprise.md" data-raw-source="[Windows 10 IoT Enterprise Overview](windows-iot-enterprise.md)">Windows 10 IoT Enterprise 개요</a></p></td>
<td align="left"><p>Windows 10 IoT Enterprise를 사용 하 여 시작 하는 방법을 자세히 알아봅니다.</p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="windows-iot-core.md" data-raw-source="[Windows 10 IoT Core Overview](windows-iot-core.md)">Windows 10 IoT Core 개요</a></p></td>
<td align="left"><p>Windows 10 IoT Core 사용 하 여 시작 하는 방법을 자세히 알아봅니다.</p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="windows-iot-core.md" data-raw-source="[Windows 10 IoT Core Overview](windows-server.md)">Windows Server IoT 2019 개요</a></p></td>
<td align="left"><p>Windows Server IoT 2019 시작 하는 방법을 자세히 알아봅니다.</p></td>
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
<td align="left"><p>프로토타입</p></td>
<td align="left"><p>무료</p></td>
</tr>

<tr class="odd">
<td align="left"><p>장기 서비스 채널 (LTSC) 상용화에 대 한</p></td>
<td align="left"><p>작은 장치당 10 년에 대 한 액세스를 사용 하 여 지원, 제어 및 상태 증명 DHA (장치)를 업데이트 합니다. <a href="https://docs.microsoft.com/windows-hardware/manufacture/iot/iotcoreservicesoverview" data-raw-source="[here](https://docs.microsoft.com/windows-hardware/manufacture/iot/iotcoreservicesoverview)">여기</a>에서 자세한 내용을 알아보세요.</p></td>
</tr>

<tr class="odd">
<td align="left"><p>반기 채널 (SAC) 상용화에 대 한</p></td>
<td align="left"><p>무료 이지만 10 년 동안 지원 이용할 수, 컨트롤 또는 DHA 업데이트 됩니다. 또한이 상용화 계약에 서명 해야 합니다. 요청할 <a href="https://www.aka.ms/SAC-agreement">여기</a>합니다.</p></td>
</tr>

</tbody>
</table>

<i>자세한 지원 기간 정보에 자세히 알아보려면 [같습니다](https://support.microsoft.com/en-us/lifecycle/search?alpha=IoT%20Core)</i>합니다.

## <a name="prototype-a-device"></a>디바이스 프로토타입

장치 제조 하기 전에 첫 번째 시도 및 Windows 10 IoT Core 사용 하 여 장치 프로토타입 하는 것이 좋습니다. 이렇게 하면 기능을 이해할 수 있습니다 및 구성 하는 것이 좋습니다 제조 하는 때가 되었을 때 필요 합니다.

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
>1. 프로토타입 보드를 선택 합니다.</a></p></td>
<td align="left"><p>일반적인 프로토타입 보드 살펴봅니다 및로 프로토타입 만들기를 시작 하려면 하나를 선택 합니다.</p></td>
</tr>

<tr class="odd">
<td align="left"><p>2. 프로토타입 이미지가 플래시</p></td>
<td align="left"><p>선택한 장치에 대 한 프로토타입 이미지를 플래시 하는 방법을 알아보려면이 자습서 섹션으로 이동 합니다. </p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/en-us/windows/iot-core/develop-your-app/appinstaller">3. 앱 설치</a></p></td>
<td align="left"><p>다양 한 도구를 사용 하 여 앱을 설치 하는 방법에 알아봅니다.</p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/en-us/windows/iot-core/develop-your-app/appdeployment">4. 앱 배포</a></p></td>
<td align="left"><p>Visual Studio를 사용 하 여 앱을 배포 하는 방법에 알아봅니다.</p></td>
</tr>

</tbody>
</table>

## <a name="bring-a-device-to-market"></a>장치 시장 출시 기간

상업화, 또는을 시장에 장치를 전환 하는 프로세스 개인 시간에 더 이동 부분 및만 프로토타입 장치 보다는 사용자를 포함 합니다. 상용화 최대한 안전 하다 고 및 준수를 다양 한 장치, 전 세계 어디서 나 업데이트를 받을 수 있는지 확인 하는 단계에 필요 합니다. 
<br>
적합 한 Windows 10 IoT의 버전에 따라 사용 하려는 경우는 제조 지침을 사용 하 여 시작 합니다.

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
>가이드를 제조 하는 Windows 10 IoT Core</a></p></td>
<td align="left"><p>여기에서 시작 하 고 사용자 지정 테스트 및 상용 Windows 10 IoT Core 솔루션에 대 한 일반 정품 이미지를 만드는 방법을 알아봅니다.</p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/iot-ent-overview">가이드를 제조 하는 Windows 10 IoT Enterprise</a></p></td>
<td align="left"><p>여기에서 시작 하 고 상용 Windows 10 IoT Enterprise 솔루션에 대 한 이미지를 만드는 방법을 알아봅니다.</p></td>
</tr>

</tbody>
</table>
