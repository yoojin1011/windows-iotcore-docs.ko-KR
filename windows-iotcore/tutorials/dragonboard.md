---
title: Dragonboard 설정
ms.author: saclayt
ms.date: 05/22/2019
ms.topic: article
description: Windows 10 IoT Core 사용 하 여 프로그램 Dragonboard를 설정 하는 방법에 알아봅니다.
keywords: Windows 10 IoT Core, Dragonboard
ms.custom: RS5
ms.openlocfilehash: 8e4acc77d902124934e1bdae249f76c7f76306a6
ms.sourcegitcommit: 8aadc776da7b473159f9023cd555145819e7e952
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66182275"
---
# <a name="setting-up-a-dragonboard"></a>Dragonboard 설정

> [!IMPORTANT]
> 새 Dragonboard을 사용 하는 경우 설치 하는 Android를 사용 하 여 제공 됩니다. 초기화 및 eMMC 깜박이 메서드를 사용 하 여 장치를 로드 해야 합니다.

> [!NOTE]
> 프로그램 DragonBoard를 사용 하 여 오디오 관련 문제를 실행 하는 경우 Qualcomm의 수동를 읽는 것이 좋습니다 [여기](https://developer.qualcomm.com/download/db410c/stereo-connector-and-audio-routing-application-note.pdf)합니다. 

프로토타입 제작 Dragonboard를 설정할 때 Windows 10 IoT Core 대시보드를 사용 하는 것이 좋습니다. 그러나는 Dragonboard를 사용 하 여 제조 하려는 경우를 참조 하십시오 합니다 [IoT Core 제조 가이드](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)합니다. 제조를 위한 작성자 이미지를 사용할 수 없습니다.
<br>
> [!Video https://www.youtube.com/embed/iPm57hGq-Q8]

## <a name="using-the-dashboard"></a>대시보드 사용

Flash를 또는 MinnowBoard에 IoT Core를 다운로드 해야 합니다.
* Windows 10을 실행 하는 컴퓨터 
* [Windows 10 IoT Core 대시보드](https://docs.microsoft.com/windows/iot-core/downloads)
* MicroUSB 케이블
* 외부 디스플레이
* 모든 기타 주변 장치 (예: 마우스, 키보드 등)

### <a name="instructions"></a>지침

1. Windows 10 IoT Core 대시보드를 실행 하 고 클릭 *새 장치 설정*합니다.
2. 장치 유형으로 "Qualcomm [DragonBoard 410 c]"를 선택 합니다.
3. DragonBoard microUSB 케이블을 사용 하 여 compuetr에 연결 합니다.
4. 프로그램 DragongBoard 외부 디스플레이에 연결 합니다.
5. 전원 켜기 12V를 사용 하 여 Dragonboard (> 1A) 전원 공급 장치 볼륨 크게 (+)를 누른 채 단추입니다. 장치--디스플레이에 연결 하는 경우 망치, 번개, 및는 코그의 이미지가 표시 됩니다.
6. 이제 장치 대시보드에서 아래와 같이 표시 됩니다. 적절 한 장치를 선택 합니다.
7. 소프트웨어 licnse 조건에 동의 하 고 클릭 **다운로드 및 설치**합니다. Windows 10 IoT Core 이제 장치에 깜박이 볼 수 있습니다.

![플래시 모드로 DragonBoard](../media/DeviceSetup/db4.png)

## <a name="connect-to-a-network"></a>네트워크에 연결
### <a name="wired-connection"></a>유선된으로 연결
이더넷 포트 또는 유선된 연결을 사용 하려면 USB 이더넷 어댑터에서 지 원하는 장치의 상태가 되 면 네트워크에 연결할 이더넷 케이블을 연결 합니다.

### <a name="wireless-connection"></a>무선 연결
장치에서 Wi-fi 연결을 지 원하는 경우 디스플레이에 연결 해야 합니다.

1. 기본 응용 프로그램으로 이동한 다음 클록 옆에 있는 설정 단추를 클릭 합니다.
2. 설정 페이지에서 선택 _네트워크 및 Wi-fi_합니다.
3. 장치의 무선 네트워크에 대 한 검색을 시작 합니다.
4. 이 목록에 표시 되는 네트워크를 선택 하 고 클릭 _Connect_합니다.

디스플레이 연결 하지 않은 하 고 Wi-fi를 통해 연결 하려는 경우을 해야 합니다.

1. IoT 대시보드로 이동 하 고 클릭 _내 장치_합니다.
2. 목록에서 구성 되지 않은 보드를 찾습니다. 이름과 "AJ_"로 시작 됩니다... (예:: AJ_58EA6C68)입니다. 몇 분 정도 지나면 보드 표시 되지 않는 경우 보드를 다시 부팅 하십시오.
3. 클릭할 _장치 구성_ 네트워크 자격 증명을 입력 합니다. 그러면 네트워크에 보드를 연결 됩니다.

> [!NOTE]
> Wifi를 컴퓨터에 다른 네트워크를 찾을 수 있도록 설정 해야 합니다.

## <a name="connect-to-windows-device-portal"></a>Windows Device Portal 연결

사용 합니다 [Windows Device Portal](../manage-your-device/DevicePortal.md) 웹 브라우저를 통해 장치를 연결 합니다. 장치 포털 중요 한 구성 및 장치 관리 기능을 사용할 수 있게 합니다. 
