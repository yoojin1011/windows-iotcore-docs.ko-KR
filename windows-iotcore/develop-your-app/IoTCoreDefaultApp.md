---
title: Windows 10 IoT Core 기본 앱
author: saraclay
ms.author: saclayt
ms.date: 08/08/2018
ms.topic: article
description: Windows 10 IoT Core 기본 앱 및 해당 기능에 대해 알아봅니다.
keywords: windows iot, windows 10 iot core, 기본 앱
ms.custom: RS5
ms.openlocfilehash: 12baa759c9085360431c2b7f87f72816cd24680b
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "60168025"
---
# <a name="windows-10-iot-core-default-app-overview"></a>Windows 10 IoT Core 기본 앱 개요

> [!TIP]
> 이 샘플 앱에 추가 된 기능을 확인 하려는 경우 GitHub에서 [문제를 열어](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoredefaultapp) 알려주세요. 버그를 파일로 보내려면 [여기](https://social.msdn.microsoft.com/Forums/en-US/fad1c6a0-e578-44a7-8e8d-95cc28c06ccd/need-logs-if-your-device-hasnt-updated-to-the-latest-iotcore-version?forum=WindowsIoT)에서 피드백 허브에 대 한 지침을 따르세요.

처음에 Windows 10 IoT Core를 플래시 하면 시작 시 Windows 10 IoT Core 기본 앱이 표시 되며 다음과 같습니다.

![IoT Core 기본 앱의 스크린샷](../media/IoTCoreDefaultApp/DeviceInfoPage-Screenshot.jpg)

이 응용 프로그램의 목적은 Windows 10 IoT Core를 처음 부팅할 때 상호 작용할 수 있는 친숙 한 셸을 제공 하기 위한 것이 아니라이 [응용 프로그램에](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/IoTCoreDefaultApp) 대 한 코드를 오픈 소스로 사용 하 여 사용자 고유의 cu에서 이러한 기능을 연결 하 고 재생할 수 있도록 하는 것입니다. stom 응용 프로그램입니다.

이 문서에서는 Windows 10 IoT Core 기본 앱에서 제공 하는 다양 한 기능에 대 한 개요를 제공 하 고 응용 프로그램에 대해 이러한 여러 기능을 활용할 수 있는 방법을 설명 합니다.

## <a name="leveraging-the-iot-core-default-app"></a>IoT Core 기본 앱 활용 

> [!IMPORTANT]
> 상용화에 제조사 이미지를 사용하지 마세요. 디바이스를 상용화하려는 경우 최적의 보안을 위해 사용자 지정 FFU를 사용해야 합니다. [여기](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)에서 자세한 내용을 알아보세요.

IoT Core 기본 앱을 사용자 지정 하 고 확장할 수 있습니다. 또는 소스 코드를 사용자 고유의 앱에 대 한 예제로 사용할 수 있습니다. 직접 사용해 보려면 샘플의 zip을 다운로드 하거나 [여기](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/IoTCoreDefaultApp)에서 IoT Core 기본 앱에 대 한 코드를 확인 하세요. 질문을 하려면 [여기](https://github.com/Microsoft/Windows-iotcore-samples/issues)의 샘플 리포지토리에서 문제를 파일 하세요.

아래 설정 섹션](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoredefaultapp#settings
) 에 [표시 된 것 처럼 경우에 따라 최종 사용자를 대신 하 여 고객 시스템에서 기본 설정 및 기능을 구성할 수 있습니다. 그러나 기본적으로 이러한 설정 및 기능을 설정 하거나 진단이 기본 설정 위에 있는 경우 다음을 수행 해야 합니다.

* 최종 사용자에 게 이러한 기능을 사용할 수 있음을 알리고 [여기](http://go.microsoft.com/fwlink/?LinkId=521839)에서 Microsoft 개인 정보 취급 방침 웹 페이지에 대 한 링크를 최종 사용자에 게 제공 합니다. 
* 관련 최종 사용자의 보안 동의를 통해 해당 법률에서 요구 하는 대로 기본적으로 이러한 기능을 사용 하도록 설정 합니다.
* 최종 사용자에 게 진단 설정을 다시 기본 설정으로 변경할 수 있는 기능을 제공 합니다.
* Microsoft 계정을 사용 하도록 설정 하 고 최종 사용자 데이터에 대 한 액세스 권한이 있는 경우 최종 사용자가 Microsoft 계정을 삭제 하는 경우 장치에서 모든 최종 사용자의 Microsoft 계정 데이터를 동시에 삭제할 수 있어야 합니다. 

## <a name="out-of-box-experience-oobe"></a>OOBE (기본 제공 환경)

IoT Core 기본 앱에 대 한 기본 제공 환경은 가져오는 것과 같습니다. 첫 번째 페이지에는 기본 언어 및 wi-fi 설정이 표시 됩니다. 여기서 앱이 GDPR 규격을 준수 하도록 하려면 진단 데이터 화면이 있어야 하 고, 위치를 추적할 계획인 경우 위치 사용 권한 화면도 필요 합니다. 둘 다의 예가 아래에 나와 있습니다. 

![Oobe에 대 한](../media/IoTCoreDefaultApp/OOBE3.jpg)
oobe![진단 설정의 위치 설정](../media/IoTCoreDefaultApp/OOBE4.jpg)

## <a name="command-bar"></a>명령 모음
명령 모음은 화면 아래쪽에 있는 영구적인 horizonatal Bar입니다. 이렇게 하면 다음 기능이에 쉽게 액세스할 수 있습니다.
- 앞으로 및 뒤로 페이지 탐색
- 현재 페이지를 떠나지 않고 기본 장치 정보
- 전체 화면 모드 설정 또는 해제
- 바로 가기 키
- 페이지 특정 단추

명령 모음에는 많은 단추가 있으며 때로는 이러한 단추를 혼동 하거나 숨길 수 있습니다. 명령 모음을 확장 하 고 해당 단추에 액세스 하려면 오른쪽 아래에 있는 메뉴 단추를 누릅니다.

![명령 모음을 확장 하는 방법](../media/IoTCoreDefaultApp/CommandBar.gif)

## <a name="start-menu---play"></a>시작 메뉴-재생

시작 메뉴에는 대부분의 플러그 앤 플레이 기능이 라이브 되어 있습니다.

### <a name="weather"></a>날씨
날씨 페이지는 국가별 날씨 서비스의 데이터를 사용 하 여 현재 위치에 날씨 정보를 렌더링 합니다.

### <a name="web-browser"></a>웹 브라우저
웹 브라우저를 사용 하 여 웹에서 대부분의 사이트를 끌어올 수 있습니다.

### <a name="music"></a>음악
이 페이지는 [Windows 장치 포털](../manage-your-device/DevicePortal.md)을 통해 액세스할 수 있는 **음악 라이브러리**에서 MP3 및 WAV 파일을 재생 합니다.  음악 플레이어에 파일을 업로드 하려면 Windows 장치 포털로 이동 하 여 "앱" 드롭다운을 클릭 하 고 "파일 탐색기"로 이동한 다음 "음악"을 선택 하 고 여기에서 파일을 업로드 해야 합니다.


![음악 파일을 업로드 하는 방법](../media/IoTCoreDefaultApp/music.gif)

### <a name="slideshow"></a>Slideshow
이 페이지에는 [Windows 장치 포털](../manage-your-device/DevicePortal.md)을 통해 액세스할 수 있는 **그림 라이브러리**의 모든 PNG 또는 JPEG 이미지 파일이 표시 됩니다. 이미지를 슬라이드 쇼에 업로드 하려면 Windows 장치 포털로 이동 하 여 "앱" 드롭다운을 클릭 하 고 "파일 탐색기"로 이동한 다음 "그림"을 선택 하 고 여기에서 파일을 업로드 해야 합니다.


![음악 파일을 업로드 하는 방법](../media/IoTCoreDefaultApp/slideshow.gif)

### <a name="draw"></a>Draw
이 페이지에서는 Windows 10 IoT Core의 잉크 기능을 테스트할 수 있습니다.

## <a name="start-menu---explore"></a>시작 메뉴-탐색 

### <a name="apps"></a>앱 
이 페이지에서 장치에 설치 된 다른 포그라운드 응용 프로그램을 시작할 수 있습니다. 응용 프로그램을 시작 하면 [Windows 장치 포털](../manage-your-device/DevicePortal.md)에서 app Manager를 사용 하 여 고 수 있는 IoT Core 기본 앱이 일시 중단 됩니다.

전경 응용 프로그램을 페이지에 나열 하는 데 특별 한 사항은 없으며, 응용 프로그램을 [설치](AppInstaller.md) 하거나 [배포](AppDeployment.md) 하기만 하면 됩니다. 설치 또는 배포를 성공적으로 수행한 후 응용 프로그램 페이지를 다시 탐색 하 여 응용 프로그램 목록을 새로 고칩니다.

필터링 하는 자동 생성 된 OS 관련 응용 프로그램이 몇 가지 있습니다. [여기](http://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/IoTCoreDefaultApp/CS/Views/AppLauncherPage.xaml.cs)에서 앱 이름 목록을 찾을 수 있습니다.

### <a name="notifications"></a>알림
이 페이지에는 IoT Core 기본 앱이 시작 된 이후 지난 20 개의 알림이 나열 됩니다. IoT Core 기본 앱이 디버그 모드에서 실행 되는 경우 테스트 알림을 만드는 단추가 추가 됩니다.

### <a name="logs"></a>로그
이 페이지에는 자동 생성 된 충돌 또는 오류 로그가 표시 됩니다 .이 로그는 장치에서 가져와서 분석할 수 있습니다.

### <a name="github"></a>GitHub
이 페이지에서는 IoT Core 기본 앱 코드의 오픈 소스 GitHub 위치로 이동 합니다.

## <a name="start-menu---windows-device-portal"></a>시작 메뉴-Windows 장치 포털

이 섹션의 페이지에서는 windows 장치 포털 자격 증명을 사용 하 여 로그인 해야 하는 Windows 장치 포털 REST Api를 활용 합니다.

## <a name="device-information"></a>장치 정보

이 페이지에서는 이더넷, OS 버전, 연결 된 장치 등 장치에 대 한 다양 한 기능을 확인할 수 있습니다.

## <a name="command-line"></a>명령줄

이 페이지에서는 장치에서 직접 명령을 실행할 수 있습니다.

이 기능을 사용 하려면 앱에서 명령을 실행할 수 있도록 레지스트리 키를 설정 해야 합니다. 처음으로 명령을 실행 하려고 하면 Windows 장치 포털에 대 한 호출을 사용 하 여 레지스트리 키를 설정할 수 있는 링크가 표시 됩니다. 장치에서 명령을 실행할 수 있도록 하려면 링크를 클릭 합니다.

일부 명령에는 관리자 액세스 권한이 필요 합니다. 보안을 위해 앱은 기본적으로 관리자가 아닌 계정을 사용 하 여 명령을 실행 합니다. 관리자 권한으로 명령을 실행 해야 하는 경우 명령줄 프롬프트에서 "RunAsAdmin <your command>"를 입력할 수 있습니다.

## <a name="settings"></a>설정
Wi-fi, Bluetooth, 전원 옵션 등을 비롯 한 다양 한 설정을 구성할 수 있습니다.

### <a name="app-settings"></a>앱 설정
**앱 설정** 섹션에서 앱의 페이지에 대 한 다양 한 설정을 구성할 수 있습니다.  

사용자 지정할 수 있는 몇 가지 설정은 다음과 같습니다.

##### <a name="general-settings"></a>일반 설정
* 앱이 시작 될 때 표시 되는 기본 페이지를 설정 합니다.
* 화면 보호기 사용/사용 안 함

##### <a name="weather-settings"></a>날씨 설정
* 위치 변경
  > 이 기능은 유효한 [Bing 지도 서비스 토큰](https://msdn.microsoft.com/library/ff428642.aspx)을 제공한 경우에만 사용할 수 있습니다.  앱에 토큰을 전달 하려면 앱의 localstate 폴더 (예: C:\Data\USERS\\[User Account] \AppData\Packages\\[Package Full Name] \localst\maptoken.config)에 **maptoken .config** 파일을 만들고 앱을 다시 시작 합니다.
* 지도 확장
* 지도와 날씨 스위치를 주기적으로 배치 하 여 화면 굽기를 방지 하는 맵 대칭 이동 사용/사용 안 함

##### <a name="web-browser-settings"></a>웹 브라우저 설정
* 웹 브라우저의 홈 페이지를 설정 합니다.

##### <a name="slideshow-settings"></a>슬라이드 쇼 설정
* 슬라이드쇼 간격 설정

##### <a name="appearance"></a>모양
* 타일 아이콘에 대해 Emojis 대신 MDL2 자산을 사용 합니다.
* 타일 너비와 높이를 설정 합니다.
* UI 배율 설정-자동 크기 조정은 기본적으로 설정 되어 있습니다.
* 타일 색 설정

#### <a name="system"></a>시스템
언어, 키보드 레이아웃 및 표준 시간대를 변경 합니다.

#### <a name="network--wi-fi"></a>네트워크 & Wi-fi
네트워크 어댑터 속성을 보거나 사용 가능한 Wi-fi 네트워크에 연결 합니다.

#### <a name="bluetooth"></a>Bluetooth
Bluetooth 장치와 페어링 합니다.

#### <a name="app-updates"></a>앱 업데이트
앱 업데이트를 확인 하거나 자동 업데이트 설정을 변경 하세요.

#### <a name="power-options"></a>전원 옵션
장치를 다시 시작 하거나 종료 합니다.

#### <a name="diagnostics"></a>진단
Microsoft에서 제공 하려는 진단 데이터의 양을 선택 합니다.  사용자가 문제를 신속 하 게 진단 하 고 제품을 개선할 수 있도록 **전체** 진단 데이터를 옵트인 (opt in) 하는 것이 좋습니다.

##### <a name="basic"></a>기본 
장치에 대 한 정보, 해당 설정 및 기능, 제대로 작동 하 고 있는지 여부에 대 한 정보만 보냅니다.

##### <a name="full"></a>전체
검색 한 웹 사이트에 대 한 정보, 앱 및 기능을 사용 하는 방법, 장치 상태, 장치 작업 및 고급 오류 보고에 대 한 추가 정보를 비롯 하 여 모든 기본 진단 데이터를 보냅니다.

#### <a name="location"></a>위치
사용자의 위치에 대 한 앱 액세스를 허용 하거나 거부 합니다.
