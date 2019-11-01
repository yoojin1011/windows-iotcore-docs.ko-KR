---
title: 디바이스용 앱 개발
ms.date: 04/17/2018
ms.topic: article
description: 디바이스용 앱을 추가 및 개발하는 방법 알아보기
keywords: Windows 10 IoT Core, 시작, 앱 개발, 앱
ms.openlocfilehash: 7c047e2bba686705db19b12ea3b31350f0240688
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918486"
---
# <a name="develop-an-app-for-your-device"></a>디바이스용 앱 개발

> [!NOTE]
> Visual Studio에서 액세스할 수 있는 RS4 이상의 SDK를 설치하지 않으면 RS5(또는 OpenSSH를 사용하는 RS4) IoT 이미지에 배포할 때 Visual Studio가 암호화 오류를 생성합니다.

디바이스가 정상 작동하고 기본 앱이 실행 중이므로, 이제 앱을 개발하고 디바이스에 배포하여 디바이스의 활용도를 높일 차례입니다. 샘플을 살펴보기 전에, 애플리케이션 개발에 사용할 [Visual Studio 2017](https://www.visualstudio.com/downloads/)을 다운로드해야 합니다.

프로젝트에 C++를 사용할 계획인 경우 Visual Studio 2017을 다운로드할 때 아래 예제와 동일한 방식으로 확인란을 선택해야 합니다.

![C++ 및 Windows 10 IoT를 위한 Essentials](../../media/DevelopApp/VS-CPP.jpg)

향후 백그라운드, Arduino 유선 또는 콘솔 애플리케이션 개발에 관심이 있는 경우 [Visual Studio 갤러리](https://marketplace.visualstudio.com/items?itemName=MicrosoftIoT.WindowsIoTCoreProjectTemplatesforVS15)에서 프로젝트 템플릿도 다운로드하세요.


앱을 실행하려면 아래의 추천 스타터 샘플로 시작하는 것이 좋습니다. 하지만 고유의 앱을 배포할 준비가 완료된 분들을 위해 이후 섹션에 유용한 링크를 준비해 두었습니다.

## <a name="suggested-starter-samples"></a>추천 스타터 샘플

* [Hello Blinky](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/HelloBlinky)
* [Hello World](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/HelloWorld)
* [IoT 시작 앱 샘플](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/IoTStartApp)
* [RPi Cognitive Service 샘플](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/RPiCognitiveService) 



앱을 배포하셨으니, 이 빠른 시작을 모두 마쳤습니다! 계속 둘러보셔도 되고, 아이디어가 떠오르는 분들은 Windows 10 IoT를 이용한 상용화 설명서를 확인해 보세요. 

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
<td align="left"><p><a href="../../develop-your-app/buildingappsforiotcore.md" data-raw-source="[Developing foreground applications](../../develop-your-app/buildingappsforiotcore.md)">포그라운드 애플리케이션 개발</a></p></td>
<td align="left"><p>Windows 10 IoT Core에서 지원되는 다양한 언어와 지원되는 UWP 및 비 UWP 앱 형식에 대해 알아봅니다.</p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="../../develop-your-app/backgroundapplications.md" data-raw-source="[Developing background applications](../../develop-your-app/backgroundapplications.md)">백그라운드 애플리케이션 개발</a></p></td>
<td align="left"><p>Windows 10 IoT Core에서 지원되는 다양한 언어와 지원되는 UWP 및 비 UWP 앱 형식에 대해 알아봅니다.</p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="../../develop-your-app/appdeployment.md" data-raw-source="[Deploy an App with Visual Studio](../../develop-your-app/appdeployment.md)">Visual Studio를 사용하여 앱 개발</a></p></td>
<td align="left"><p>Visual Studio를 사용하여 Windows 10 IoT Core 디바이스에 다양한 앱을 배포하는 방법을 알아봅니다.</p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="../../develop-your-app/remotedebugging.md" data-raw-source="[Debug your app using Remote Console App Debugging](../../develop-your-app/remotedebugging.md)">원격 콘솔 앱 디버깅을 사용하여 앱 디버그</a></p></td>
<td align="left"><p>Visual Studio에서 원격 콘솔 앱 디버깅을 사용하여 앱을 디버그하는 방법을 알아봅니다.</p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="../../develop-your-app/appinstaller.md" data-raw-source="[Install your app on your Windows 10 IoT Core device](../../develop-your-app/appinstaller.md)">Windows 10 IoT Core 디바이스에 앱 설치</a></p></td>
<td align="left"><p>Windows 10 IoT Core 디바이스에 앱을 설치하는 방법을 알아봅니다.</p></td>
</tr>

</tbody>
</table>
