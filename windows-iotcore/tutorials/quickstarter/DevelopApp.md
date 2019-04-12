---
title: 장치에 대 한 앱 개발
author: saraclay
ms.author: saclayt
ms.date: 04/17/2018
ms.topic: article
description: 추가 하 고 장치에 앱을 개발 하는 방법 알아보기
keywords: Windows 10 IoT Core, 시작, 앱, 앱 개발
ms.openlocfilehash: f5ee15c2115d6e10a2a8ade1522c7b66cf788bee
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59515099"
---
# <a name="develop-an-app-for-your-device"></a>장치에 대 한 앱 개발

> [!NOTE]
> Visual Studio는 RS5를 배포 하는 경우 암호화 오류가 생성 됩니다 (또는 RS4 OpenSSH 사용 하 여 사용 하도록 설정) IoT 이미지에서 RS4 이상 SDK는 Visual Studio에 액세스할 수 있도록 설치 되어 있지 않으면입니다.

실행 중인 기본 앱을 사용 하 여 작업 장치를가지고 다음 수준으로 개발 하 고 장치에서 앱을 배포 하 여 장치를 수행 합니다. 예제를 살펴 보기 전에 다운로드 해야 [Visual Studio 2017](https://www.visualstudio.com/downloads/) 응용 프로그램 개발에 대 한 합니다.

사용 하려는 경우 C++ 프로젝트의 경우 Visual Studio 2017을 다운로드 하는 경우, 아래 예제에 있는 확인란을 동일한 방식으로 선택 하도록 확인 합니다.

![Essentials에 대 한 C++ 및 Windows 10 IoT](../../media/DevelopApp/VS-CPP.jpg)

백그라운드, Arduino 연결 또는 콘솔 응용 프로그램을 나중에 개발에 관심이 있는 경우 또한 싶어하는에서 프로젝트 템플릿을 다운로드 합니다 [Visual Studio 갤러리](https://marketplace.visualstudio.com/items?itemName=MicrosoftIoT.WindowsIoTCoreProjectTemplatesforVS15)합니다.


실행 중인 앱을 가져오려면 아래 제안 된 시작 샘플을 사용 하 여 시작 하는 것이 좋습니다. 그러나 뒤에 있는 섹션에 대 한 유용한 링크를 사용자 고유의 앱을 배포할 준비가 인 경우도 제공 했습니다.

## <a name="suggested-starter-samples"></a>제안 된 시작 샘플

* [Hello 쳐다](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/HelloBlinky)
* [Hello World](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/HelloWorld)
* [IoT 시작 앱 샘플](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/IoTStartApp)
* [RPi Cognitive Service 샘플](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/RPiCognitiveService) 



축 하 하 여 앱을 배포한 후이 quickstarter를 마쳤습니다! 계속 해 서, 여러분의 머릿속에 주위 반송 하는 몇 가지 아이디어를 있다면 Windows 10 IoT를 사용 하 여 상용화에서 설명서를 확인해 계속 합니다. 

## <a name="app-development-resources"></a>앱 개발 리소스

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
<td align="left"><p><a href="../../develop-your-app/buildingappsforiotcore.md" data-raw-source="[Developing foreground applications](../../develop-your-app/buildingappsforiotcore.md)">포그라운드 응용 프로그램 개발</a></p></td>
<td align="left"><p>UWP 뿐만 아니라 Windows 10 IoT Core 지원 되는 다른 언어 및 지원 되는 비 UWP 앱 형식에 알아봅니다.</p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="../../develop-your-app/backgroundapplications.md" data-raw-source="[Developing background applications](../../develop-your-app/backgroundapplications.md)">백그라운드 응용 프로그램 개발</a></p></td>
<td align="left"><p>UWP 뿐만 아니라 Windows 10 IoT Core 지원 되는 다른 언어 및 지원 되는 비 UWP 앱 형식에 알아봅니다.</p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="../../develop-your-app/appdeployment.md" data-raw-source="[Deploy an App with Visual Studio](../../develop-your-app/appdeployment.md)">Visual Studio 사용 하 여 앱 배포</a></p></td>
<td align="left"><p>Windows 10 IoT Core 장치에 Visual Studio를 사용 하 여 다른 앱을 배포 하는 방법에 알아봅니다.</p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="../../develop-your-app/remotedebugging.md" data-raw-source="[Debug your app using Remote Console App Debugging](../../develop-your-app/remotedebugging.md)">원격 콘솔 응용 프로그램 디버깅을 사용 하 여 앱 디버그</a></p></td>
<td align="left"><p>원격 콘솔 응용 프로그램 디버깅을 사용 하 여 Visual Studio에서 앱을 디버그 하는 방법에 알아봅니다.</p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="../../develop-your-app/appinstaller.md" data-raw-source="[Install your app on your Windows 10 IoT Core device](../../develop-your-app/appinstaller.md)">Windows 10 IoT Core 장치에 앱 설치</a></p></td>
<td align="left"><p>Windows 10 IoT Core 장치에 앱을 설치 하는 방법에 알아봅니다.</p></td>
</tr>

</tbody>
</table>
