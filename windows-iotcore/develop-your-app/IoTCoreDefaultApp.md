---
title: Windows 10 IoT Core 기본 앱
author: saraclay
ms.author: saclayt
ms.date: 08/08/2018
ms.topic: article
description: Windows 10 IoT Core 기본 앱 및 해당 기능에 알아봅니다.
keywords: windows iot, windows 10 iot core, 기본 앱
ms.custom: RS5
ms.openlocfilehash: 12baa759c9085360431c2b7f87f72816cd24680b
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512406"
---
# <a name="windows-10-iot-core-default-app-overview"></a>Windows 10 IoT Core 기본 앱 개요

> [!TIP]
> 이 샘플 앱에 추가 된 기능을 참조 하려는 경우 [문제를 제기](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoredefaultapp) 알려주세요 GitHub에 있습니다. 버그를 제출 하려면 원하는 피드백 허브에 대 한 지침을 따릅니다 [여기](https://social.msdn.microsoft.com/Forums/en-US/fad1c6a0-e578-44a7-8e8d-95cc28c06ccd/need-logs-if-your-device-hasnt-updated-to-the-latest-iotcore-version?forum=WindowsIoT)합니다.

처음에 Windows 10 IoT Core flash를 Windows 10 IoT Core 기본 앱과 같은 시작 시 표시 됩니다.

![IoT Core 기본 앱의 스크린 샷](../media/IoTCoreDefaultApp/DeviceInfoPage-Screenshot.jpg)

이 응용 프로그램의 목적은 먼저 부팅 하면 Windows 10 IoT Core 설치 하는 상호 작용 하는 친숙 한 셸을 제공에 되지 않지만 우리는 오픈 소스이 응용 프로그램에 대 한 코드 [여기](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/IoTCoreDefaultApp) 있습니다 수 플러그 앤 플레이 이러한 있도록 사용자 고유의 사용자 지정 응용 프로그램에 대 한 기능입니다.

이 문서에서는 이러한 다양 한 기능을 활용 하 여 사용자 고유의 응용 프로그램에 대 한 방법과 Windows 10 IoT Core 기본 앱 에서도 제공 하는 다양 한 기능에 대 한 개요를 제공 합니다.

## <a name="leveraging-the-iot-core-default-app"></a>IoT Core 기본 앱을 활용 하 여 

> [!IMPORTANT]
> 상용화에 대 한 작성자 이미지를 사용 하지 마세요. 장치 상용화 되, 사용자 지정 FFU 최적의 보안을 위해 사용 해야 합니다. [여기](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)에서 자세한 내용을 알아보세요.

IoT Core 기본 앱을 사용자 지정 확장 하거나 사용자 고유의 앱에 대 한 예를 들어 소스 코드를 사용할 수 있습니다. 이 직접을 사용해 샘플의 zip을 다운로드 하거나 IoT Core 기본 앱에 대 한 코드를 확인해 [여기](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/IoTCoreDefaultApp)합니다. 모든 질문에 대 한 문제를 제출 하세요에서 샘플 리포지토리에서 [여기](https://github.com/Microsoft/Windows-iotcore-samples/issues)합니다.

아래 표시 된 것 처럼 합니다 [설정 섹션](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoredefaultapp#settings
) 아래의 경우에 따라 수를 구성할 수 있습니다 기본 설정 및 기능 고객 시스템 최종 사용자 대신 합니다. 그러나 이러한 설정과 기본적으로 또는 진단 위에 기본 설정 된 경우 기능을 사용 해야 합니다.

* 이 기능이 사용 하도록 설정 된 하 고 Microsoft의 개인정보취급방침 웹 페이지에 대 한 링크를 사용 하 여 최종 사용자를 제공 합니다. 최종 사용자에 게 알립니다 [여기](http://go.microsoft.com/fwlink/?LinkId=521839)합니다. 
* 필요에 따라 해당 법규에서 기본적으로 이러한 기능을 사용 하도록 설정 하려면 관련 최종 사용자의 동의 보호 합니다.
* 최종 사용자에 게 진단 설정을 기본 설정으로 다시 변경 하는 기능을 제공 합니다.
* Microsoft 계정을 사용 하 고 최종 사용자는 Microsoft 계정을 삭제 하는 경우 최종 사용자 데이터에 액세스할 수, 동시 삭제할 장치에서 모든 최종 사용자의 Microsoft 계정 데이터를 사용 해야 합니다. 

## <a name="out-of-box-experience-oobe"></a>기본 제공 환경 (OOBE)

IoT Core 기본 앱에 대 한 기본 제공 환경은 져 간결 합니다. 기본 언어 및 wi-fi 설정에 대 한 첫 번째 페이지를 묻습니다. GDPR 규격 앱에 대 한 순서 대로 여기에서 진단 데이터 화면 있어야 하 고 위치를 추적 하려는 경우 너무 위치 권한을 화면이 포함 해야 합니다. 둘 다의 예제가 아래에 표시 됩니다. 

![OOBE에 대 한 위치 설정을](../media/IoTCoreDefaultApp/OOBE3.jpg)
![OOBE에 대 한 진단 설정](../media/IoTCoreDefaultApp/OOBE4.jpg)

## <a name="command-bar"></a>명령 모음
명령 모음 화면 아래쪽에 있는 영구 horizonatal 모음 이며 이 다음 기능에 쉽게 액세스할 수 제공합니다.
- 페이지를 앞뒤로 탐색
- 현재 페이지를 떠나지 않고 기본 장치 정보
- 전체 화면 모드를 설정 또는 해제
- 고급 바로 가기
- 특정 페이지 단추

명령 모음에 많은 단추 및 혼동 되거나 숨겨진 해당 단추 경우도 있습니다. 명령 모음을 확장 하 고 해당 단추에 액세스할 오른쪽 아래에서에서 메뉴 단추를 누르십시오.

![명령 모음을 확장 하는 방법](../media/IoTCoreDefaultApp/CommandBar.gif)

## <a name="start-menu---play"></a>시작 메뉴-재생

시작 메뉴는 대부분의 플러그 앤 플레이 기능은 어디에 있습니다.

### <a name="weather"></a>날씨
날씨 페이지 National 날씨 서비스에서 데이터를 사용 하 여 현재 위치에 날씨 정보를 렌더링 합니다.

### <a name="web-browser"></a>웹 브라우저
웹 브라우저를 사용 하면 웹에서 대부분의 사이트를 가져올 수 있습니다.

### <a name="music"></a>음악
이 페이지에서 MP3 및 WAV 파일 재생 됩니다 합니다 **음악 라이브러리**를 통해 액세스할 수 있는 합니다 [Windows Device Portal](../manage-your-device/DevicePortal.md)합니다.  음악 플레이어에 게 파일을 업로드 하려면 Windows Device Portal 이동, "앱" 드롭다운 목록에서 클릭, "File Explorer"로 이동, "Music" 선택 및 여기에서 파일을 업로드 해야 합니다.


![음악 파일을 업로드 하는 방법](../media/IoTCoreDefaultApp/music.gif)

### <a name="slideshow"></a>Slideshow
이 페이지에서 JPEG 또는 PNG 이미지 파일에 표시 됩니다는 **사진 라이브러리**를 통해 액세스할 수 있는 합니다 [Windows Device Portal](../manage-your-device/DevicePortal.md)합니다. 슬라이드 쇼를 이미지를 업로드 하려면 Windows Device Portal 이동, "앱" 드롭다운 목록에서 클릭, "File Explorer"로 이동, "그림"을 선택 및 여기에서 파일을 업로드 해야 합니다.


![음악 파일을 업로드 하는 방법](../media/IoTCoreDefaultApp/slideshow.gif)

### <a name="draw"></a>Draw
이 페이지를 사용 하면 Windows 10 IoT Core 잉크 입력 기능을 테스트할 수 있습니다.

## <a name="start-menu---explore"></a>시작 메뉴-탐색 

### <a name="apps"></a>앱 
이 페이지를 사용 하는 장치에 설치 된 다른 포그라운드 응용 프로그램을 실행할 수 있습니다. 응용 프로그램 시작에서 IoT Core 기본 앱에서 응용 프로그램 관리자를 사용 하 여 다시 시작할 수 있습니다는 일시 중단 [Windows Device Portal](../manage-your-device/DevicePortal.md)합니다.

포그라운드 응용 프로그램을 간단히 페이지에서 나열 하는 데 필요한 특별 [설치](AppInstaller.md) 하거나 [배포](AppDeployment.md) 응용 프로그램입니다. 설치 성공 또는 배포 후 응용 프로그램의 목록을 새로 고치려면 앱 페이지로 이동 다시 합니다.

자동으로 생성 된 운영 체제의 몇 가지를 필터링 하는 응용 프로그램 관련, 앱 이름 목록을 찾을 수 있습니다 [여기](http://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/IoTCoreDefaultApp/CS/Views/AppLauncherPage.xaml.cs)합니다.

### <a name="notifications"></a>알림
이 페이지에는 과거 표시 IoT Core 기본 앱이 시작 된 이후 20 알림. IoT Core 기본 앱은 디버그 모드에서 실행 하면 테스트 알림을 사용 하는 단추 추가 됩니다.

### <a name="logs"></a>로그
이 페이지에는 모든 자동으로 생성 된 충돌 또는 오류 로그에 있으며, 그런 다음 장치를 해제 하 고 수 분석 표시 됩니다.

### <a name="github"></a>GitHub
이 페이지는 IoT Core 기본 응용 프로그램 코드의 오픈 소스 GitHub 위치를 이동할 수 있습니다.

## <a name="start-menu---windows-device-portal"></a>시작 메뉴-Windows Device Portal

Windows Device Portal 자격 증명을 사용 하 여 로그인 해야 하는 Windows Device Portal REST Api를 활용 하는이 섹션의 페이지입니다.

## <a name="device-information"></a>장치 정보

이 페이지를 사용 하면 이더넷, OS 버전, 연결 된 장치 등을 포함 한 장치에 대 한 다양 한 기능을 볼 수 있습니다.

## <a name="command-line"></a>명령줄

이 페이지를 사용 하면 장치에서 직접 명령을 실행할 수 있습니다.

이 기능을 사용 하도록 설정 하려면 레지스트리 키를 설정 하 여 앱에는 명령을 실행할 수 있도록 해야 합니다. 처음으로 명령을 실행 하려고 하면 Windows Device Portal 대 한 호출을 사용 하 여 레지스트리 키를 설정할 수 있는 링크가 나타납니다. 명령을 실행 하 여 장치에 대 한 링크를 클릭 합니다.

일부 명령에는 관리자 권한이 필요합니다. 보안상의 이유로 앱 기본적으로 관리자가 아닌 계정의 명령을 실행 하려면 사용 합니다. 관리자로 서 명령을 실행 해야 하는 경우 입력할 수 있습니다 "RunAsAdmin <your command>" 명령줄 프롬프트에서.

## <a name="settings"></a>설정
Wi-fi, 블루투스, 전원 옵션 등을 포함 하 여 다음 설정을 구성할 수 있습니다.

### <a name="app-settings"></a>앱 설정
합니다 **앱 설정** 섹션을 사용 하면 앱에서 페이지의 다양 한 설정을 구성할 수 있습니다.  

설정을 사용자 지정할 수는 다음과 같습니다.

##### <a name="general-settings"></a>일반 설정
* 앱이 시작 될 때 표시 되는 기본 페이지를 설정 합니다.
* 화면 보호기 사용/사용 안 함

##### <a name="weather-settings"></a>날씨 설정
* 위치 변경
  > 유효한 제공한 경우에이 기능이 설정 되어 [Bing 지도 서비스 토큰](https://msdn.microsoft.com/library/ff428642.aspx)합니다.  앱에 토큰을 전달할를 만들려면를 **MapToken.config** 앱의 LocalState 폴더에 파일 (예: C:\Data\USERS\\[사용자 계정] \AppData\Packages\\[패키지 전체 이름] \LocalState\ MapToken.config) 하 고 앱 다시 시작 합니다.
* 맵을 확장합니다
* 설정/해제 대칭 이동 된 데이터베이스 맵 및 날씨 스위치에서 화면 굽기 방지 하려면 정기적으로 배치 되도록 매핑

##### <a name="web-browser-settings"></a>웹 브라우저 설정
* 웹 브라우저의 홈 페이지를 설정 합니다.

##### <a name="slideshow-settings"></a>슬라이드 쇼 설정
* 슬라이드 쇼 간격 설정

##### <a name="appearance"></a>모양
* 타일 아이콘이 모 지 대신 MDL2 자산 사용
* 타일 너비와 높이 설정 합니다.
* UI 확장-설정 기본적으로 설정 되어 자동 크기 조정
* 타일 색 설정

#### <a name="system"></a>시스템
언어, 자판 배열, 표준 및 표준 시간대를 변경 합니다.

#### <a name="network--wi-fi"></a>네트워크 및 Wi-fi
네트워크 어댑터 속성을 보거나 사용 가능한 Wi-fi 네트워크에 연결 합니다.

#### <a name="bluetooth"></a>Bluetooth
Bluetooth 장치를 쌍으로 연결 합니다.

#### <a name="app-updates"></a>앱 업데이트
앱 업데이트를 확인 하거나 자동 업데이트 설정 변경.

#### <a name="power-options"></a>전원 옵션
다시 시작 또는 종료 장치입니다.

#### <a name="diagnostics"></a>진단
Microsoft 제공 하려는 진단 데이터의 크기를 선택 합니다.  옵트인 할 것이 좋습니다 **전체** 진단 데이터를 신속 하 게 문제를 진단 하 제품을 개선할 수 있도록 합니다.

##### <a name="basic"></a>Basic 
장치, 설정 및 기능에 대 한 정보에만 보내기 여부이 제대로 수행 되 고 있습니다.

##### <a name="full"></a>전체
웹 사이트를 찾아보면 및 앱 및 기능을 사용 하는 방법에 대 한 정보 및 장치 상태, 장치 작업 및 향상 된 오류 보고에 대 한 추가 정보과 함께 모든 기본 진단 데이터를 보냅니다.

#### <a name="location"></a>위치
허용 하거나 사용자의 위치에 대 한 앱 액세스를 거부 합니다.
