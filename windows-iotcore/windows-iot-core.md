---
title: Windows 10 IoT Core 개요
author: saraclay
ms.author: saclayt
ms.date: 01/18/2018
ms.topic: article
description: Windows 10 IoT Core가 무엇인지와 이를 통해 수행할 수 있는 작업에 대해 알아봅니다.
keywords: Windows 10 IoT Core, 작은 사용 공간, 헤드리스
ms.openlocfilehash: 37bbf85028542573972f85954777b7ef26098ce9
ms.sourcegitcommit: 8a197111b5b7814b924d77dfea5f9d38760d4288
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/08/2019
ms.locfileid: "67627386"
---
# <a name="an-overview-of-windows-10-iot-core"></a>Windows 10 IoT Core 개요

> [!NOTE]
> Windows 10 컨테이너는 Microsoft Azure IoT Edge를 활용하는 상업용 배포를 위해 Windows IoT Core 및 Windows IoT Enterprise에서만 사용할 수 있습니다.

## <a name="what-is-windows-10-iot-core"></a>Windows 10 IoT Core란?
Windows 10 IoT Core는 ARM과 x86/x64 디바이스에서 실행되는 디스플레이가 있거나 없는 소형 디바이스에 최적화된 Windows 10 버전입니다. Windows IoT Core 설명서는 디바이스 연결, 관리, 업데이트, 보안 등에 대한 정보를 제공합니다. 

다음 수준으로 이동하여 솔루션 상용화를 시작할 준비가 된 경우 [Windows 10 IoT Core 제조 가이드](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)를 통해 Windows 10 IoT Core로 제조하는 방법을 알아볼 수 있습니다. 

## <a name="getting-started"></a>시작

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
<td align="left"><p><a href="https://docs.microsoft.com/en-us/windows/iot-core/develop-your-app/appinstaller">2. 3. 앱 설치</a></p></td>
<td align="left"><p>다양한 도구를 사용하여 앱을 설치하는 방법을 알아봅니다.</p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/en-us/windows/iot-core/develop-your-app/appdeployment">4. 앱 배포</a></p></td>
<td align="left"><p>Visual Studio를 사용하여 앱을 배포하는 방법을 알아봅니다.</p></td>
</tr>

</tbody>
</table>

## <a name="differences-between-windows-10-desktop-and-windows-10-iot-core"></a>Windows 10 Desktop과 Windows 10 IoT Core의 차이점

### <a name="different-features-available-on-desktop-and-iot-core"></a>데스크톱 및 IoT Core에서 사용할 수 있는 다양한 기능

* 받은 편지함 Cortana는 버전 1809(17763) 이후 Windows 10 IoT Core에서 더 이상 사용할 수 없습니다. 음성 사용 디바이스를 빠르게 출시하려는 경우 [Cortana 디바이스 SDK의 미리 보기](https://developer.microsoft.com/en-us/cortana/devices)를 사용하여 Cortana 지원을 디바이스에 통합할 수 있습니다.
* [FileOpenPicker API](https://docs.microsoft.com/en-us/uwp/api/windows.storage.pickers.fileopenpicker)는 Windows 10 IoT Core에서 지원되지 않습니다. 로컬 드라이브 또는 이동식 스토리지에 액세스하려면 이를 자신의 애플리케이션에서 구현합니다.
* 기본적으로 Windows 10 IoT Core 디바이스가 데스크톱과 같은 PC 대신 [기본 앱](https://docs.microsoft.com/en-us/windows/iot-core/develop-your-app/iotcoredefaultapp)으로 부팅됩니다. 그러나 상용화를 위해서는 이 기본 앱을 수정할 수 있는 사용자 지정 앱이나 기본 앱으로 대체**해야** 합니다. 이 애플리케이션의 목적은 최초 부팅 시 상호 작용할 수 있는 친숙한 셸을 제공할 뿐만 아니라, 이 애플리케이션에 대해 [오픈 소스 코드](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/IoTCoreDefaultApp)를 사용할 수 있도록 함으로써 이러한 기능을 사용하여 고유한 사용자 지정 애플리케이션을 플러그 앤 플레이할 수 있습니다.

### <a name="differences-in-driver-supported-areas"></a>드라이버 지원 영역의 차이점

* Windows 10 Desktop에는 Windows 10 IoT Core보다 지원 드라이버가 많습니다. Windows 10 IoT Core에서 테스크톱에서와 동일한 디바이스를 작동시키려면 Windows 10 IoT Core 디바이스용 원본에서 드라이버를 빌드하거나, 특히 ARM 아키텍처에 대한 다른 해결 방법을 찾아야 합니다.
* Windows 10 IoT Core(ARM)용 libusb에 대한 기본 제공 드라이버가 없습니다. ARM 아키텍처를 대상으로 하는 원본에서 빌드해야 합니다.

### <a name="differences-in-available-registry-set"></a>사용 가능한 레지스트리 세트의 차이점

* 데스크톱에서는 "Windows의 스크롤 막대를 자동으로 숨기기" 옵션을 off로 설정할 수 있습니다. 다음 레지스트리 항목에 의해 제어됩니다. 

```
HKEY_CURRENTUSER\Control Panel\Accessibility
```

* 기본적으로 Windows 10 IoT Core 디바이스에는 이러한 레지스트리가 없습니다. 원하는 경우 "동적 스크롤 막대" 레지스터를 추가해야 합니다.
* UWP 애플리케이션에서 자동으로 스크롤 막대 숨기기를 활성화하려면 "DynamicScrollbars"를 추가하고 다음과 같이 값을 "1"로 설정합니다.

```
REG ADD "HKCU\Control Panel\Accessibility" /v DynamicScrollbars /t REG_DWORD \d "1"
```

* 레지스트리 키는 기본 계정에서 설정해야 합니다. ScrollViewer의 XAML 설정이 "Visible"인 경우, nthe 레지스트리 설정 0은 UI에 스크롤을 표시하기에 충분한 콘텐츠가 있는지 여부와 상관없이 스크롤 막대를 표시합니다. 레지스트리 설정 1은 충분한 콘텐츠가 있을 때까지 스크롤 막대가 숨겨집니다.

```
<TextBox Height="200" Width="100" IsEnabled="True" FontSize="50" TextWrapping="Wrap" ScrollViewer.VerticalScrollBarVisibility="Visible" Text="..."/>
```

* 마지막으로, ScrollViewer XAML의 설정이 "Auto"인 경우 레지스트리 설정 0은 스크롤 막대를 표시할 수 있는 충분한 콘텐츠가 있을 때에만 전체 스크롤 막대를 표시합니다. 레지스트리 설정이 1이면 콘텐츠가 충분하거나 콘텐츠가 없으면 숨겨진 스크롤 막대가 표시됩니다.

```
<TextBox Height="200" Width="100" IsEnabled="True" FontSize="50" TextWrapping="Wrap" ScrollViewer.VerticalScrollBarVisibility="Auto" Text="..."/>
```

### <a name="different-commands-supported"></a>지원되는 다른 명령

* PowerShell Remove-AppxPackage 명령은 데스크톱에서 작동하지만 Windows 10 IoT Core에서는 작동하지 않습니다.
* 유니버설 Windows 앱에서는 디바이스의 모든 폴더에 액세스할 수 있는 것은 아닙니다. Windows 10 IoT Core에서는 FolderPermissions 도구를 사용하여 UWP 앱에서 액세스할 수 있는 폴더를 만들 수 있습니다. 예를 들어 FolderPermissions c:\test -e를 실행하여 UWP 앱에 c:\test 폴더에 대한 액세스 권한을 부여합니다. 그러나 데스크톱에서는 이 기능을 사용할 수 없습니다.

Windows 10 IoT Core가 지속적으로 업데이트되고 있기 때문에 이 게시물에 설명된 모든 차이점은 향후에 유효하지 않을 수 있습니다.

## <a name="helpful-resources"></a>유용한 리소스
Windows 10 IoT Core에 대해 자세히 알아보려면 [설명서를 읽어보세요](https://docs.microsoft.com/windows/iot-core/).
