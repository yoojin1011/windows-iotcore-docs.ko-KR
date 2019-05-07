---
title: Windows 10 IoT Core 대시보드
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Windows 10 IoT Core 대시보드 기능에 대해 알아봅니다 및 시작 방법입니다.
keywords: windows iot, windows 10 iot core 대시보드, windows iot 대시보드, 장치
ms.openlocfilehash: af87ff8224cf77b567b1dd96e6de2297b4752530
ms.sourcegitcommit: f447681d9a73ebdec97a3da973bd798a02df975d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65197674"
---
# <a name="windows-10-iot-core-dashboard"></a>Windows 10 IoT Core 대시보드

Windows 10 IoT Core 다운로드, 설치 하는 가장 좋은 방법은 대시보드와 모든 PC에서 Windows 10 IoT Core 장치에 연결 합니다.

다운로드할 수 있습니다 합니다 [여기에 IoT Core 대시보드](http://go.microsoft.com/fwlink/?LinkID=708576)합니다.

> [!NOTE]
> 다운로드 한 후 IoT 대시보드를 열 때 흰색 화면 보시기 수 있는지를 찾는 경우 드라이버 문제 때문일 수 있습니다. 이 문제를 해결 하기 위해 다운로드 해야 합니다 [zip 형식으로](https://downloadmirror.intel.com/27894/a08/win64_24.20.100.6229.zip) Intel 그래픽 드라이버의 드라이버를 수동으로 설치 합니다. 

## <a name="set-up-a-new-device"></a>새 장치 설정

> [!NOTE]
> 대시보드는 Raspberry Pi 3B +를 설치 하는 데 사용할 수 없습니다. 3B + 장치가 있는 경우 사용 해야 합니다 [3B + 기술 미리 보기](https://www.microsoft.com/en-us/software-download/windowsiot)합니다. 참조 하십시오 합니다 [알려진 제한 사항](https://docs.microsoft.com/en-us/windows/iot-core/troubleshooting) 이 개발에 적합 한지 여부를 확인 하려면 기술 미리 보기.

> [!NOTE]
> 현재 OS SD 카드에 파티션을 통해 이동 하 고는 'Format'...' 라는 메시지를 표시 하는 위치의 알려진된 문제 모든 파일 시스템을 포함 하지 않는 특정 데이터 파티션에 대 한 메시지입니다. 취소 눌러이 프롬프트를 해제 하세요. 솔루션에서 작업을 하는 동안에 'Format 이제'를 클릭 하면 있습니다 경감 FFU 이미지를 사용 하 여 SD 카드 다시 업데이트 프로세스 및 장치 업데이트 실패 형식 작업 영향으로는 것이 좋습니다.


IoT 대시보드에 쉽게 새 장치를 설정 합니다. 시작 하는 방법에 대 한 자세한 내용은 참조는 [시작](https://docs.microsoft.com/en-us/windows/iot-core/getstarted) 페이지입니다.

![IoT 대시보드 설정 페이지](../media/IoTDashboard/IoTDashboard_SetupPage.PNG)

### <a name="sd-card"></a>SD 카드
유형, 제조업체 및 모델 SD 카드의 성능 및 IoT Core의 품질에 영향을 크게입니다.
느린 카드 보다 부팅 하는 데 최대 5 배 더 걸릴 수 있습니다 우리의 [카드 권장](../learn-about-hardware/hardwarecompatlist.md)합니다.
오래 되 고 덜 안정적인 SD 카드도 사용할 수 없습니다. 를 계속 설치 하는 문제가 발생 하는 경우에 SD 카드를 대체 하는 것이 좋습니다.

### <a name="device-name"></a>장치 이름
기본 장치 이름은 minwinpc입니다. 이 인해 쉽게 네트워크에 장치를 찾을 수 있도록 고유한 값으로 변경 하는 것이 좋습니다. 장치 이름을 최대 15 자일 수 장기 있으며 문자, 숫자와 기호만 포함할 수: @ # $ % ^ & ') (합니다. -_ {} ~ 자동 다시 부팅을 장치에 전원을 경우 처음으로 현상이 장치를 설정 하는 경우 IoT 대시보드에서 장치 이름을 변경 하면 됩니다.

### <a name="password"></a>암호
암호는 필수 필드 및 설정 해야 합니다. 기본적으로 관리자가 사용자의 암호를 수정 IoT 대시보드에서 암호를 설정 합니다. "p@ssw0rd"입니다.

### <a name="wi-fi-network-connection"></a>Wi-fi 네트워크 연결
IoT 대시보드 사용자 PC에 연결 된 이전에 사용 가능한 모든 네트워크를 보여 줍니다. 목록에서 원하는 Wi-fi 네트워크를 보이지 않으면 PC에 연결을 확인 합니다.
확인란의 선택을 취소 하는 경우 깜박임 후 보드로 이더넷 케이블을 연결 해야 있습니다.

### <a name="first-boot"></a>처음 부팅
첫 번째 부팅 하는 모든 후속 부팅 보다 더 오래 걸립니다 항상. 운영 체제를 설치 하 고 네트워크에 연결 하는 데 시간이 걸립니다.
부팅 시간에 SD 카드에 따라 크게 달라질 수 있습니다. 예를 들어이 권장 되는 SD 카드에서 실행 중인 Raspberry Pi 3 첫 번째 부팅 3-4 분이 걸립니다. 저품질 SD 카드를 사용 하 여 동일한 Pi에서 부팅 시간 15 분 이상에 대해 살펴보았습니다.

### <a name="connecting-to-the-internet"></a>인터넷에 연결
IoT Core 장치를 인터넷에 연결 하는 것이 중요 합니다. 다양 한 최신 보드 수반 빌드된 Wi-fi 어댑터에서. 네트워크에 연결 하는 데 문제가 있으면 다음을 시도 합니다.

* 장치 다시 부팅
* 이더넷 케이블 연결
* 모니터 장치를 연결 합니다. 장치에 대 한 진단 정보가 표시 됩니다이

> [!NOTE]
> 공식 Raspberry Pi 2 Wi-fi 어댑터 Wi-fi에 연결할 때 안정적인 없습니다 수 있습니다.


## <a name="my-devices"></a>내 장치
___
장치는 인터넷에 연결 되 면 IoT 대시보드는 장치를 자동으로 검색 됩니다.
장치를 찾으려면에서로 이동 **내 장치**합니다. 장치가 나열 되지 않으면, 장치 다시 부팅 하십시오. 경우 둘 이상의 장치를 네트워크에 각각 고유한 이름이 있는지 확인 합니다. 확인 프로그램 **windows10iotcoredashboard.exe** 다음 단계를 수행 하 여 Windows 방화벽을 통해 통신 하도록 허용 됩니다.

1. 오픈 **네트워크 및 공유 센터** 을 PC에 연결 된 네트워크 (도메인/사설/공용)의 종류를 찾습니다.
2. 오픈 **Control Panel** 클릭 **시스템 및 보안**합니다.
3. 클릭 **Windows 방화벽을 통해 앱 허용** 아래에서 **Windows 방화벽**합니다.
4. 클릭 **설정을 변경**합니다.
5. 찾을 **windows10iotcoredashboard.exe** 에 **허용 되는 앱 및 기능** 다음 적절 한 네트워크 확인란 (즉, 1 단계에서 찾은 네트워크 형식)를 사용 하도록 설정 합니다.


### <a name="connect-to-your-device"></a>장치에 연결

> [!NOTE]
> 대시보드에서 장치를 찾을 수 없는 경우 [IP 주소]를 입력 해 보세요 및 [: 8080] Windows Device Portal 시작 및 실행 하 여 브라우저에 있습니다. 대시보드에 표시 하기 위해 장치를 가져오려면 장치 다시 부팅을 시도 합니다.


마우스 오른쪽 단추로 클릭 하 고 선택 **장치 포털에서 열기**합니다. 시작 합니다 [Windows Device Portal](../manage-your-device/DevicePortal.md) 페이지와 상호 작용 하 고 장치를 관리 하는 가장 좋은 방법은 합니다.

![장치 IoTDashboard 보기](../media/IoTDashboard/IoTDashboard_RightClickMenu.PNG)

Windows PowerShell을 사용 하 여 장치에 연결할 수 있습니다.

## <a name="connect-to-azure"></a>Azure에 연결
___
IoT 대시보드 사용 하면 Azure IoT Hub를 사용 하 여 IoT Core 장치 프로 비전 합니다. 자세한 내용은이 대 한 [블로그 게시물](https://blogs.windows.com/buildingapps/2016/07/20/building-secure-apps-for-windows-iot-core)합니다.

[Azure IoT 대시보드를 사용 하는 방법 알아보기](https://docs.microsoft.com/windows/iot-core/connect-to-cloud/connectdevicetocloud)

## <a name="quick-run-samples"></a>빠른 실행된 샘플
___

빠른 실행 샘플에는 모든 코드 컴파일, Visual studio 설치 필요 하지 않습니다 또는 SDK를 다운로드 합니다. 신속 하 게 IoT Core에서 수행할 수 있는 작업 확인에 대 한 이러한 탁월 합니다.

### <a name="network-3d-printer"></a>3D 네트워크 프린터
사용 하 여 3D 프린터 보드를 연결할 네트워크 3D 프린터 샘플 수를 찾을 수 있도록 홈 네트워크를 통해. 

![3D IoTDashboard 네트워크 프린터](../media/IoTDashboard/IoTDashboard_3DPrinter.PNG)

### <a name="internet-radio"></a>인터넷 라디오
Windows 10 IoT Core 장치 제어할 수 있는에서 아무 곳 이나 집에는 인터넷 라디오를 바꿔 보세요.

![IoTDashboard 인터넷 라디오](../media/IoTDashboard/IoTDashboard_InternetRadio.PNG)

### <a name="iot-core-blockly"></a>IoT Core Blockly
IoT Core Blockly 샘플 프로그램을 Raspberry Pi2 또는 3 및 브라우저에서 "블록"이 편집기를 사용 하는 Raspberry Pi Sense hat 수 있습니다.

![IoTDashboard Blockly](../media/IoTDashboard/IoTDashboard_Blockly.PNG)
