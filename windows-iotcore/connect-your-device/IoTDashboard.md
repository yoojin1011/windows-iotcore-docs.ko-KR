---
title: Windows 10 IoT Core 대시보드
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Windows 10 IoT Core 대시보드의 기능 및 시작 하는 방법에 대해 알아봅니다.
keywords: windows iot, windows 10 iot core 대시보드, windows iot 대시보드, 장치
ms.openlocfilehash: af87ff8224cf77b567b1dd96e6de2297b4752530
ms.sourcegitcommit: f447681d9a73ebdec97a3da973bd798a02df975d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65197674"
---
# <a name="windows-10-iot-core-dashboard"></a>Windows 10 IoT Core 대시보드

Windows 10 IoT Core 대시보드는 PC에서 Windows 10 IoT Core 장치를 다운로드 하 고 설정 하 고 연결 하는 가장 좋은 방법입니다.

[IoT Core 대시보드는 여기](http://go.microsoft.com/fwlink/?LinkID=708576)에서 다운로드할 수 있습니다.

> [!NOTE]
> 다운로드 한 후 IoT 대시보드를 열 때 흰색 화면이 표시 되는 경우 드라이버 문제 때문일 수 있습니다. 이 문제를 해결 하려면 Intel Graphics Driver의 [zip 형식을](https://downloadmirror.intel.com/27894/a08/win64_24.20.100.6229.zip) 다운로드 하 고 드라이버를 수동으로 설치 해야 합니다. 

## <a name="set-up-a-new-device"></a>새 장치 설정

> [!NOTE]
> 대시보드는 Raspberry Pi 3B+를 설정하는 데 사용할 수 없습니다. 3B+ 디바이스가 있는 경우 [3B+ 기술 미리 보기](https://www.microsoft.com/en-us/software-download/windowsiot)를 사용해야 합니다. 기술 미리 보기의 [알려진 제한 사항](https://docs.microsoft.com/en-us/windows/iot-core/troubleshooting)을 확인하여 개발 작업에 적합한지 알아보세요.

> [!NOTE]
> 현재 OS가 SD 카드의 파티션을 통해 이동 하 고 ' 형식. '를 요청 하는 알려진 문제가 있습니다. 파일 시스템을 포함 하지 않는 특정 데이터 파티션에 대 한 메시지입니다. [취소]를 눌러이 프롬프트를 해제 하십시오. 솔루션에서 작업 하는 동안 ' 지금 서식 '을 클릭 하면 경감 하기 위해가 업데이트 프로세스에 영향을 주는 형식 작업이 업데이트 프로세스에 영향을 주므로 장치를 업데이트 하지 못하여 SD 카드를 다시 FFU 이미지로 다시 설정 하는 것이 좋습니다.


IoT 대시보드를 사용 하면 새 장치를 쉽게 설정할 수 있습니다. 시작 하는 방법에 대 한 자세한 내용은 [시작](https://docs.microsoft.com/en-us/windows/iot-core/getstarted) 페이지를 참조 하세요.

![IoT 대시보드 설정 페이지](../media/IoTDashboard/IoTDashboard_SetupPage.PNG)

### <a name="sd-card"></a>SD 카드
SD 카드의 유형, 제조업체 및 모델이 IoT Core의 성능 및 품질에 크게 영향을 줍니다.
저속 카드는 [권장 카드](../learn-about-hardware/hardwarecompatlist.md)보다 부팅 하는 데 최대 5 배 더 걸릴 수 있습니다.
이전의 더 안정적인 SD 카드는 작동 하지 않을 수 있습니다. 설치 문제가 계속 되 면 SD 카드를 교체 하는 것이 좋습니다.

### <a name="device-name"></a>장치 이름
기본 장치 이름은 minwinpc입니다. 네트워크에서 장치를 보다 쉽게 찾을 수 있도록 하기 때문에 고유한 항목으로 변경 하는 것이 좋습니다. 장치 이름은 15 자이 하 여야 하 고, 문자, 숫자 및 다음 기호를 포함할 수 있습니다. @ # $% ^ & ') (. -_ {} ~ 장치를 설정할 때 IoT 대시보드에서 장치 이름을 변경 하는 경우 처음으로 장치를 켤 때 자동 다시 부팅이 수행 됩니다.

### <a name="password"></a>암호
암호는 필수 필드 이므로 설정 해야 합니다. IoT 대시보드에서 암호를 설정 하면 관리자 사용자에 대 한 암호를 수정 합니다 .이p@ssw0rd암호는 기본적으로 ""입니다.

### <a name="wi-fi-network-connection"></a>Wi-fi 네트워크 연결
IoT 대시보드에는 PC가 이전에 연결한 모든 사용 가능한 네트워크가 표시 됩니다. 원하는 Wi-fi 네트워크가 목록에 표시 되지 않으면 PC에서 해당 Wi-fi 네트워크에 연결 되어 있는지 확인 합니다.
이 확인란의 선택을 취소 하는 경우 플래시 후에 보드에 이더넷 케이블을 연결 해야 합니다.

### <a name="first-boot"></a>처음 부팅
첫 번째 부팅은 항상 모든 후속 부팅 보다 더 오래 걸립니다. 운영 체제를 설치 하 고 네트워크에 연결 하는 데 약간의 시간이 걸립니다.
부팅 시간은 SD 카드에 따라 크게 다를 수 있습니다. 예를 들어 권장 SD 카드에서 실행 되는 Raspberry Pi 3은 첫 번째 부팅에 대해 3-4 분이 소요 됩니다. 품질이 낮은 SD 카드를 사용 하는 동일한 Pi에서 15 분 보다 긴 부팅 시간이 나타났습니다.

### <a name="connecting-to-the-internet"></a>인터넷에 연결
IoT Core 장치를 인터넷에 연결 하는 것이 필수적입니다. 최신 보드의 대부분은 기본 제공 Wi-fi 어댑터와 함께 제공 됩니다. 네트워크에 연결 하는 데 문제가 있는 경우 다음을 시도 합니다.

* 장치 재부팅
* 이더넷 케이블 연결
* 장치에 모니터를 연결 합니다. 그러면 장치에 대 한 진단 정보가 표시 됩니다.

> [!NOTE]
> Wi-fi에 연결 하는 경우 공식 Raspberry Pi 2 Wi-fi 어댑터를 불안정 하 게 만들 수 있습니다.


## <a name="my-devices"></a>내 장치
___
장치가 인터넷에 연결 되 면 IoT 대시보드가 자동으로 장치를 검색 합니다.
장치를 찾으려면 **내 장치**로 이동 합니다. 장치가 나열 되지 않으면 장치를 다시 부팅 합니다. 네트워크에 장치가 둘 이상 있는지 확인 하 고 각각에 고유한 이름을 지정 합니다. 또한 다음 단계를 수행 하 여 **windows10iotcoredashboard** 가 Windows 방화벽을 통해 통신할 수 있도록 합니다.

1. **네트워크 및 공유 센터** 를 연 다음 PC가 연결 된 네트워크 유형 (도메인/개인/공용)을 찾습니다.
2. **제어판** 을 열고 **시스템 및 보안**을 클릭 합니다.
3. **Windows 방화벽**에서 **windows 방화벽을 통해 앱 허용** 을 클릭 합니다.
4. **설정 변경**을 클릭합니다.
5. **허용 되는 앱 및 기능** 에서 **windows10iotcoredashboard** 을 찾은 다음 적절 한 네트워크 확인란을 사용 하도록 설정 합니다 (예: 1 단계에서 찾은 네트워크 유형).


### <a name="connect-to-your-device"></a>장치에 연결

> [!NOTE]
> 대시보드에서 장치를 찾을 수 없는 경우 [IP 주소] 및 [: 8080]를 브라우저에 입력 하 여 Windows 장치 포털을 시작 하 고 실행 하세요. 대시보드에 장치를 표시 하려면 장치를 다시 부팅 합니다.


마우스 오른쪽 단추를 클릭 하 고 **장치 포털에서 열기**를 선택 합니다. 그러면 [Windows 장치 포털](../manage-your-device/DevicePortal.md) 페이지가 시작 되 고 장치를 조작 하 고 관리 하는 데 가장 적합 한 방법입니다.

![I이상 대시보드 보기 장치](../media/IoTDashboard/IoTDashboard_RightClickMenu.PNG)

Windows PowerShell을 사용 하 여 장치에 연결할 수도 있습니다.

## <a name="connect-to-azure"></a>Azure에 연결
___
IoT 대시보드에서 Azure IoT Hub를 사용 하 여 IoT Core 장치를 프로 비전 할 수 있습니다. 이에 대 한 자세한 내용은이 [블로그 게시물](https://blogs.windows.com/buildingapps/2016/07/20/building-secure-apps-for-windows-iot-core)을 참조 하세요.

[Azure에서 IoT 대시보드를 사용 하는 방법을 알아봅니다.](https://docs.microsoft.com/windows/iot-core/connect-to-cloud/connectdevicetocloud)

## <a name="quick-run-samples"></a>빠른 실행 샘플
___

빠른 실행 샘플에는 코드 컴파일, Visual studio 설치 또는 SDK 다운로드가 필요 하지 않습니다. IoT Core에서 수행할 수 있는 작업을 신속 하 게 확인 하는 데 유용 합니다.

### <a name="network-3d-printer"></a>네트워크 3D 프린터
네트워크 3D 프린터 샘플을 사용 하 여 3D 프린터를 보드에 연결 하면 홈 네트워크를 통해 검색 가능 하 게 만들 수 있습니다. 

![IoTDashboard 네트워크 3D 프린터](../media/IoTDashboard/IoTDashboard_3DPrinter.PNG)

### <a name="internet-radio"></a>인터넷 라디오
Windows 10 IoT Core 장치를 홈의 어디에서 나 제어할 수 있는 인터넷 라디오로 전환 합니다.

![IoTDashboard 인터넷 라디오](../media/IoTDashboard/IoTDashboard_InternetRadio.PNG)

### <a name="iot-core-blockly"></a>IoT Core Blockly
IoT Core Blockly 샘플을 통해 프로그램은 브라우저에서 "블록" 편집기를 사용 하 여 Raspberry Pi2 또는 3 및 Raspberry Pi Sense hat를 사용할 수 있습니다.

![IoTDashboard Blockly](../media/IoTDashboard/IoTDashboard_Blockly.PNG)
