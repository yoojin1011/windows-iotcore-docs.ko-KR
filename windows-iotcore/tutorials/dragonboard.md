---
title: Dragonboard 설정
ms.date: 05/22/2019
ms.topic: article
description: Windows 10 IoT Core를 사용하여 Dragonboard를 설정하는 방법을 알아봅니다.
keywords: Windows 10 IoT Core, Dragonboard
ms.custom: RS5
ms.openlocfilehash: 0233ef4380cfb8f9fadbbd64d8e7e594cf11b0b1
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918667"
---
# <a name="setting-up-a-dragonboard"></a>Dragonboard 설정

> [!IMPORTANT]
> 새 Dragonboard를 사용하는 경우 Android가 설치된 상태로 제공됩니다. [여기](https://docs.microsoft.com/en-us/windows/iot-core/tutorials/qualcomm)서 eMMC 플래시 메서드를 사용하여 디바이스의 데이터를 지우고 다시 로드해야 합니다.

> [!NOTE]
> DragonBoard에서 오디오 관련 이슈가 발생하는 경우 [여기서](https://developer.qualcomm.com/download/db410c/stereo-connector-and-audio-routing-application-note.pdf) Qualcomm의 설명서를 읽어보시기를 권장합니다. 

프로토타입 제작용 Dragonboard를 설정할 때 Windows 10 IoT Core 대시보드를 사용하는 것이 좋습니다. 그러나 Dragonboard를 사용하여 제작하려는 경우에는 [IoT Core 제작 가이드](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)를 참조하세요. 제조사 이미지는 제작에 사용할 수 없습니다.
<br>
> [!Video https://www.youtube.com/embed/iPm57hGq-Q8]

## <a name="using-the-dashboard"></a>대시보드 사용

IoT Core를 MinnowBoard에 플래시 또는 다운로드하려면 다음이 필요합니다.
* Windows 10을 실행하는 컴퓨터 
* [Windows 10 IoT Core 대시보드](https://docs.microsoft.com/windows/iot-core/downloads)
* MicroUSB 케이블
* 외부 디스플레이
* 그 외 주변 기기(예: 마우스, 키보드 등)

### <a name="instructions"></a>지침

1. Windows 10 IoT Core 대시보드를 실행하고 *새 디바이스 설정*을 클릭합니다.
2. 디바이스 유형으로 "Qualcomm [DragonBoard 410c]"를 선택합니다.
3. microUSB 케이블을 사용하여 DragonBoard를 컴퓨터에 연결합니다.
4. DragongBoard를 외부 디스플레이에 연결합니다.
5. 볼륨 크게(+) 단추를 누른 상태에서 12V(>1A) 전원 공급 장치를 사용하여 Dragonboard를 켭니다. 디바이스를 디스플레이에 연결하면 망치, 번개 및 톱니 이미지가 표시됩니다.
6. 이제 디바이스가 대시보드에 아래와 같이 표시됩니다. 적절한 디바이스를 선택합니다.
7. 소프트웨어 사용 조건에 동의하고 **다운로드 및 설치**를 클릭합니다. Windows 10 IoT Core가 디바이스에 플래시되는 것을 볼 수 있습니다.

![플래시 모드의 DragonBoard](../media/DeviceSetup/db4.png)

## <a name="connect-to-a-network"></a>네트워크에 연결
### <a name="wired-connection"></a>유선 연결
디바이스에 유선 연결을 지원하는 이더넷 포트 또는 USB 이더넷 어댑터가 있는 경우 이더넷 케이블을 연결하여 네트워크에 연결합니다.

### <a name="wireless-connection"></a>무선 연결
디바이스에서 Wi-Fi 연결이 지원되고 디바이스를 디스플레이에 연결한 경우 다음 단계를 수행해야 합니다.

1. 기본 애플리케이션으로 이동하여 시계 옆에 있는 설정 단추를 클릭합니다.
2. 설정 페이지에서 _네트워크 및 Wi-Fi_를 선택합니다.
3. 디바이스가 무선 네트워크 검색을 시작합니다.
4. 이 목록에 네트워크가 나타나면 네트워크를 선택하고 _연결_을 클릭합니다.

디스플레이를 연결하지 않았으며 Wi-Fi를 통해 연결하려는 경우에는 다음 단계를 수행해야 합니다.

1. IoT 대시보드로 이동하여 _내 디바이스_를 클릭합니다.
2. 목록에서 구성되지 않은 보드를 찾습니다. 보드 이름은 "AJ_"로 시작합니다(예: AJ_58EA6C68). 몇 분이 지나도 보드가 보이지 않으면 보드를 다시 부팅합니다.
3. _디바이스 구성_을 클릭하고 네트워크 자격 증명을 입력합니다. 그러면 보드가 네트워크에 연결됩니다.

> [!NOTE]
> 다른 네트워크를 찾으려면 컴퓨터의 Wifi를 켜야 합니다.

## <a name="connect-to-windows-device-portal"></a>Windows 디바이스 포털에 연결

[Windows 디바이스 포털](../manage-your-device/DevicePortal.md)을 사용하여 웹 브라우저를 통해 디바이스를 연결합니다. 디바이스 포털에서는 중요한 구성과 디바이스 관리 기능을 사용할 수 있습니다. 

