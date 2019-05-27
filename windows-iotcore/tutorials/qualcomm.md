---
title: Qualcomm 장치 설정
ms.author: saclayt
ms.date: 05/22/2019
ms.topic: article
description: Windows 10 IoT Core 사용 하 여 Qualcomm 장치를 설정 하는 방법에 알아봅니다.
keywords: Windows 10 IoT Core, Qualcomm
ms.custom: RS5
ms.openlocfilehash: 949c5af00f48b4c2049e711d4e18385fe9f3c18e
ms.sourcegitcommit: 8aadc776da7b473159f9023cd555145819e7e952
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66182205"
---
# <a name="setting-up-a-qualcomm-device"></a>Qualcomm 장치 설정

Qualcomm 장치를 사용 하 여 제조 하려는 경우 참조 하는 [IoT Core 제조 가이드](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)합니다. 제조를 위한 작성자 이미지를 사용할 수 없습니다.

> [!NOTE]
> BIOS 설정을 다시 입력 하 고 대신 USB 드라이브에서 하드 드라이브에서 로드 하는 부팅 드라이브 순서를 전환 하 여 eMMC 메모리에서 장치는 이제 부팅 해야 합니다.

## <a name="using-emmc"></a>EMMC를 사용 하 여

1. 에 대 한 DragonBoard 업데이트 도구 다운로드 및 설치 프로그램 [x86](https://developer.qualcomm.com/download/db410c/windows-10-iot-update-tool-dragonboard-410c-x86.zip) 하거나 [x64](https://developer.qualcomm.com/download/db410c/windows-10-iot-update-tool-dragonboard-410c-x64.zip) 컴퓨터.
2. 다운로드 합니다 [Windows 10 IoT Core DragonBoard FFU](https://developer.microsoft.com/en-us/windows/iot/Downloads)합니다.
3. 다운로드 한 ISO 파일을 두 번 누릅니다 하 고 탑재 된 가상 CD 드라이브를 찾습니다. 이 드라이브는 설치 관리자 파일 (.msi);에 포함 됩니다. 두 번 클릭 합니다. 새 디렉터리 아래에 있는 PC에 이렇게 `C:\Program Files (x86)\Microsoft IoT\FFU\` 에서 표시 하는 이미지 파일을 "flash.ffu"입니다.
4. 아래와 같이 프로그램 DragonBoard가 다운로드 모드를 첫 번째 부팅 전환할 보드의 USB 부팅 설정 확인 합니다. 그런 다음 DragonBoard microUSB 케이블을 통해 호스트 PC 연결한 후에 12V DragonBoard 플러그 인 (> 1A) 전원 공급 장치.
5. DragonBoard 녹색 원을 사용 하 여 사용자 PC에 연결 되어 있는지 검색 해야 하는 DragonBoard 업데이트 도구를 시작 합니다. "찾아보기" DragonBoard의를 다운로드 한 FFU 클릭 합니다 _프로그램_ 단추입니다.
6. "찾아보기"를 다시 클릭 하 고 5 단계에서 생성 된 "rawprogram0.xml"를 선택 합니다. "프로그램" 단추를 클릭 합니다.
7. 다운로드가 완료 되 면 전원 공급 장치 및 microUSB 케이블 다시 USB 부팅 스위치 보드 및 설정/해제에서 연결 끊기 _OFF_합니다. HDMI 디스플레이, 마우스 및 키보드 DragonBoard 및 rec-끊기 전원 공급 장치에 연결 합니다. 몇 분 후 Windows 10 IoT Core 기본 응용 프로그램이 표시 됩니다. 

![DragonBoard 다운로드 모드](../media/DeviceSetup/db1.png)

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



