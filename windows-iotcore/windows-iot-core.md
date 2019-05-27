---
title: Windows 10 IoT Core 개요
author: saraclay
ms.author: saclayt
ms.date: 01/18/2018
ms.topic: article
description: Windows 10 IoT Core 란 무엇 이며이 사용 하 여 수행할 수 있는 작업에 대해 알아봅니다.
keywords: Windows 10 IoT Core 헤드리스 작은 공간
ms.openlocfilehash: 0fbcc6a96f8e35227acf32a9507ed3c7a038a83d
ms.sourcegitcommit: 8aadc776da7b473159f9023cd555145819e7e952
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66174052"
---
# <a name="an-overview-of-windows-10-iot-core"></a>Windows 10 IoT Core 개요

> [!NOTE]
> 만 Windows 10 컨테이너 Microsoft Azure IoT Edge를 활용 하는 상업용 배포에 대 한 Windows IoT Core 및 Windows IoT Enterprise를 사용 하 여 사용할 수 있습니다.

## <a name="what-is-windows-10-iot-core"></a>Windows 10 IoT Core 란?
Windows 10 IoT Core 모두 ARM에서 실행 되는 작은 장치 디스플레이 유무 및 x86 x64 장치에 최적화 된 Windows 10의 버전. Windows IoT Core 설명서에서 연결, 관리, 업데이트, 장치 및 기타 보안 정보를 제공 합니다. 

사용 하 여 Windows 10 IoT Core 사용 하 여 제조 하는 방법을 알아보십시오 솔루션이 상용화 시작 확인 하 고 다음 수준으로 이동할 준비가 우리의 [Windows 10 IoT Core 제조 가이드](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)합니다. 

## <a name="getting-started"></a>시작

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
<td align="left"><p><a href="https://docs.microsoft.com/en-us/windows/iot-core/develop-your-app/appinstaller">2. 3. 앱 설치</a></p></td>
<td align="left"><p>다양 한 도구를 사용 하 여 앱을 설치 하는 방법에 알아봅니다.</p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/en-us/windows/iot-core/develop-your-app/appdeployment">4. 앱 배포</a></p></td>
<td align="left"><p>Visual Studio를 사용 하 여 앱을 배포 하는 방법에 알아봅니다.</p></td>
</tr>

</tbody>
</table>

## <a name="differences-between-windows-10-desktop-and-windows-10-iot-core"></a>Windows 10 Desktop 및 Windows 10 IoT Core 차이점

### <a name="different-features-available-on-desktop-and-iot-core"></a>데스크톱 및 IoT Core에서 사용할 수 있는 다양 한 기능

* 받은 편지함 Cortana를 더 이상 1809 (17763) 버전부터 Windows 10 IoT Core 사용할 수 없습니다. 빠르게 시장에 음성 기능을 사용할 장치를 찾으려는 경우 Cortana 지원을 사용 하 여 장치에 통합할 수 있습니다 합니다 [Cortana 디바이스 SDK의 미리 보기](https://developer.microsoft.com/en-us/cortana/devices)합니다.
* 합니다 [FileOpenPicker API](https://docs.microsoft.com/en-us/uwp/api/windows.storage.pickers.fileopenpicker) Windows 10 IoT Core 지원 되지 않습니다. 로컬 드라이브 또는 이동식 저장소에 액세스 하려면 사용자 고유의 응용 프로그램에서이 구현할 수 있습니다.
* Windows 10 IoT Core 장치로 부팅 합니다 [기본 앱](https://docs.microsoft.com/en-us/windows/iot-core/develop-your-app/iotcoredefaultapp) 같은 데스크톱 PC 대신 합니다. 이 응용 프로그램의 목적은 최초 부팅 시 상호 작용할 수 있지만 사용할 수 있도록 하는 친숙 한 셸을 제공 합니다 [오픈 소스 코드](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/IoTCoreDefaultApp) 이 응용 프로그램에 대 한 플러그 앤 플레이에 이러한 기능을 사용할 수 있도록 사용자 고유의 사용자 지정 응용 프로그램입니다.

### <a name="differences-in-driver-supported-areas"></a>드라이버에서 지 원하는 영역의 차이점

* Windows 10 Desktop에는 Windows 10 IoT Core 보다 드라이버 지원 더 합니다. 바탕 화면에서 Windows 10 IoT Core 장치에 대 한 원본에서 드라이버를 빌드 또는 ARM 아키텍처에 대 한 특히 다른 문제를 해결 하려면 찾을 해야 할 수 있습니다를 동일 하 게 하려면 Windows 10 IoT Core 장치 작동 합니다.
* Windows 10 IoT Core (ARM)에 대 한 libusb에 대 한 기본 제공 드라이버가 없는-ARM 아키텍처를 대상으로 하는 원본에서 작성 해야 합니다.

### <a name="differences-in-available-registry-set"></a>사용 가능한 레지스트리 설정의 차이점

* 바탕 화면에서 "자동 숨기기 스크롤 막대의 Windows" off로 설정할 수 있는 하는 옵션이 있습니다. 다음 레지스트리 항목에 의해 제어 됩니다. 

```
HKEY_CURRENTUSER\Control Panel\Accessibility
```

* 기본적으로 Windows 10 IoT Core 장치에 이러한 레지스트리 하지 않습니다. 원하는 경우 "동적 스크롤 막대" 등록을 추가 해야 합니다.
* UWP 응용 프로그램에서 자동 숨기기 스크롤 막대를 사용 하려면 등록 하 고 값이 같은 "1"을 설정 하는 "DynamicScrollbars"를 추가할 수 있습니다.

```
REG ADD "HKCU\Control Panel\Accessibility" /v DynamicScrollbars /t REG_DWORD \d "1"
```

* 기본 계정에서 레지스트리 키를 설정 해야 합니다. ScrollViewer의 XAML 설정이 "Visible" 인 경우 0 nthe 레지스트리 설정을 스크롤 막대 표시 여부 regardlss를 강제로 스크롤 UI에 표시 하도록 충분 한 콘텐츠가 있습니다. 레지스트리 설정을 1은 충분 한 콘텐츠가 있을 때까지 숨겨진 스크롤 막대를 유지 합니다.

```
<TextBox Height="200" Width="100" IsEnabled="True" FontSize="50" TextWrapping="Wrap" ScrollViewer.VerticalScrollBarVisibility="Visible" Text="..."/>
```

* 마지막으로, ScrollViewer XAML의 설정이 "Auto" 경우 다음 레지스트리 설정을 0만 표시 됩니다 전체 스크롤 막대를 충분 한 콘텐츠가 스크롤 막대를 표시 하는 경우. 레지스트리 설정을 1 이면 내용이 없을 때 콘텐츠 또는 숨겨진 경우에 충분 한 후 스크롤 막대에 표시 됩니다.

```
<TextBox Height="200" Width="100" IsEnabled="True" FontSize="50" TextWrapping="Wrap" ScrollViewer.VerticalScrollBarVisibility="Auto" Text="..."/>
```

### <a name="different-commands-supported"></a>지원 되는 다른 명령

* 제거-AppxPackage PowerShell 명령에는 Windows 10 IoT Core는 없지만 데스크톱에서 작동합니다.
* 장치에서 일부 폴더 유니버설 Windows 앱에서 액세스할 수 있습니다. Windows 10 IoT Core는 폴더에 UWP 앱에 액세스할 수 있도록 FolderPermissions 도구를 사용할 수 있습니다. 예를 들어 c:\test 폴더에 UWP 앱 액세스 권한을 부여 하려면 FolderPermissions c:\test-e를 실행 합니다. 그러나, 바탕 화면에서 가능 하지 않습니다.

이 게시물에서 설명 하는 모든 차이점 유효 하지 않을 나중에 Windows 10 IoT Core 지속적으로 업데이트 되 고 있어.

## <a name="helpful-resources"></a>유용한 리소스
[설명서 읽기](https://docs.microsoft.com/windows/iot-core/) Windows 10 IoT Core 자세히 알아보려면 합니다.
