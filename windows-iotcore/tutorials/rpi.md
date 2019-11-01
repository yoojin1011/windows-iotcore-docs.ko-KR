---
title: Raspberry Pi 설정
ms.date: 05/22/2019
ms.topic: article
description: Windows 10 IoT Core를 사용하여 Raspberry Pi를 설정하는 방법을 알아봅니다.
keywords: Windows 10 IoT Core, Raspberry Pi
ms.custom: RS5
ms.openlocfilehash: 304ad0ab555ccb32d546220e0b2b5a649e4b7e28
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918624"
---
# <a name="setting-up-a-raspberry-pi"></a>Raspberry Pi 설정

## <a name="overview"></a>개요

> [!NOTE]
> 대시보드는 Raspberry Pi 3B+를 설정하는 데 사용할 수 없습니다. 3B+ 디바이스가 있는 경우 [3B+ 기술 미리 보기](https://www.microsoft.com/en-us/software-download/windowsiot)를 사용해야 합니다. 기술 미리 보기의 [알려진 제한 사항](https://docs.microsoft.com/en-us/windows/iot-core/troubleshooting)을 확인하여 개발 작업에 적합한지 알아보세요.

> [!IMPORTANT]
> "이 디스크 포맷" 팝업이 나타나면 디스크를 포맷하지 _마세요_. 이 이슈를 수정하기 위한 작업을 진행 중입니다.

프로토타입 제작용 Raspberry Pi를 설정할 때 Windows 10 IoT Core 대시보드를 사용하는 것이 좋습니다. 그러나 Raspberry Pi를 사용하여 제작하려는 경우에는 [IoT Core 제작 가이드](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)를 참조하세요. 제조사 이미지는 제작에 사용할 수 없습니다.
<br>
> [!Video https://www.youtube.com/embed/JPRUbGIyODY]

## <a name="using-the-dashboard"></a>대시보드 사용

IoT Core를 Raspberry Pi에 플래시 또는 다운로드하려면 다음이 필요합니다.
* Windows 10을 실행하는 컴퓨터 
* [Windows 10 IoT Core 대시보드](https://docs.microsoft.com/windows/iot-core/downloads)
* SanDisk SD 카드와 같은 고성능 SD 카드
* 외부 디스플레이
* 그 외 주변 기기(예: 마우스, 키보드 등)

### <a name="instructions"></a>지침

1. Windows 10 IoT Core 대시보드를 실행하고, *새 디바이스 설치*를 클릭하고, 컴퓨터에 SD 카드를 삽입합니다.
2. Raspberry Pi를 외부 디스플레이에 연결합니다.
3. 필드를 작성합니다. 디바이스 유형으로 "Broadcomm [Raspberry Pi 2 & 3]"을 선택합니다. 디바이스에 새 이름과 암호를 제공해야 합니다. 그렇지 않으면 기본 자격 증명은 다음과 같이 유지됩니다.

```
Device: minwinpc
Password: p@ssw0rd
```

4. 소프트웨어 사용 조건에 동의하고 *다운로드 및 설치*를 클릭합니다. 정상적으로 작동하는 경우 Windows 10 IoT Core가 SD 카드에 플래시되는 것을 볼 수 있습니다.

![대시보드 스크린샷](../media/DeviceSetup/Dashboard-Screenshot.jpg)

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
