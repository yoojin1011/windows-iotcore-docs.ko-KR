---
title: Raspberry Pi 설정
ms.author: saclayt
ms.date: 05/22/2019
ms.topic: article
description: Windows 10 IoT Core 사용 하 여 Raspberry Pi를 설정 하는 방법에 알아봅니다.
keywords: Windows 10 IoT Core, Raspberry Pi
ms.custom: RS5
ms.openlocfilehash: 3269aa2ed102b667519baa9212e604083f910783
ms.sourcegitcommit: 8aadc776da7b473159f9023cd555145819e7e952
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66182195"
---
# <a name="setting-up-a-raspberry-pi"></a>Raspberry Pi 설정

## <a name="overview"></a>개요

> [!NOTE]
> 대시보드는 Raspberry Pi 3B +를 설치 하는 데 사용할 수 없습니다. 3B + 장치가 있는 경우 사용 해야 합니다 [3B + 기술 미리 보기](https://www.microsoft.com/en-us/software-download/windowsiot)합니다. 참조 하십시오 합니다 [알려진 제한 사항](https://docs.microsoft.com/en-us/windows/iot-core/troubleshooting) 이 개발에 적합 한지 여부를 확인 하려면 기술 미리 보기.

> [!IMPORTANT]
> "Format이 디스크" 팝업 최대 나타난 경우 수행 _되지_ 디스크를 포맷 합니다. 이 문제에 대 한 수정 노력 합니다.

프로토타입 제작 Raspberry Pi를 설정 하는 경우에 Windows 10 IoT Core 대시보드를 사용 하는 것이 좋습니다. 그러나 Raspberry Pi를 사용 하 여 제조 하려는 경우를 참조 하십시오 합니다 [IoT Core 제조 가이드](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)합니다. 제조를 위한 작성자 이미지를 사용할 수 없습니다.
<br>
> [!Video https://www.youtube.com/embed/JPRUbGIyODY]

## <a name="using-the-dashboard"></a>대시보드 사용

Flash를 또는 Raspberry Pi를 IoT Core를 다운로드 해야 합니다.
* Windows 10을 실행 하는 컴퓨터 
* [Windows 10 IoT Core 대시보드](https://docs.microsoft.com/windows/iot-core/downloads)
* SanDisk SD 카드와 같은 고성능 SD 카드
* 외부 디스플레이
* 모든 기타 주변 장치 (예: 마우스, 키보드 등)

### <a name="instructions"></a>지침

1. Windows 10 IoT Core 대시보드를 실행 하 고 클릭 *새 장치 설정* 컴퓨터에 SD 카드를 삽입 합니다.
2. Raspberry Pi을 외장 디스플레이 연결 합니다.
3. 필드를 채웁니다. 장치 유형으로 "목록의 [Raspberry Pi 2 및 3]"를 선택 합니다. 장치를 새 이름 및 암호를 제공 해야 합니다. 그렇지 않은 경우 기본 자격 증명으로 그대로 유지 됩니다.

```
Device: minwinpc
Password: p@ssw0rd
```

4. 소프트웨어 사용 조건에 동의 하 고 클릭 *다운로드 및 설치*합니다. 정상적으로 작동 하는 경우에 Windows 10 IoT Core 이제 깜박이 SD 카드에 표시 됩니다.

![대시보드 스크린샷](../media/DeviceSetup/Dashboard-Screenshot.jpg)

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
