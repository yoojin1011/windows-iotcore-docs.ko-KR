---
title: Qualcomm 디바이스 설정
ms.author: saclayt
ms.date: 05/22/2019
ms.topic: article
description: Windows 10 IoT Core를 사용하여 Qualcomm 디바이스를 설정하는 방법을 알아봅니다.
keywords: Windows 10 IoT Core, Qualcomm
ms.custom: RS5
ms.openlocfilehash: 02f6c013c428a271d3b3956c88edc1ce8f4fdbf2
ms.sourcegitcommit: 9ec4716afde25fdc8b94f7c0794448501f451b55
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/17/2019
ms.locfileid: "66835608"
---
# <a name="setting-up-a-qualcomm-device"></a>Qualcomm 디바이스 설정

Qualcomm 디바이스로 제작하려는 경우에는 [IoT Core 제작 가이드](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)를 참조하세요. 제조사 이미지는 제작에 사용할 수 없습니다.

> [!NOTE]
> BIOS 설정을 다시 입력하고, USB 드라이브 대신 하드 드라이브에서 로드하도록 부팅 드라이브 순서를 전환하여 디바이스가 eMMC 메모리에서 부팅되도록 설정합니다.

## <a name="using-emmc"></a>eMMC 사용

1. [x86](https://developer.qualcomm.com/download/db410c/windows-10-iot-update-tool-dragonboard-410c-x86.zip) 또는 [x64](https://developer.qualcomm.com/download/db410c/windows-10-iot-update-tool-dragonboard-410c-x64.zip) 머신에 맞는 DragonBoard 업데이트 도구를 다운로드하여 설치합니다.
2. [Windows 10 IoT Core DragonBoard FFU](https://docs.microsoft.com/en-us/windows/iot-core/downloads)를 다운로드합니다.
3. 다운로드한 ISO 파일을 두 번 클릭하고 탑재된 가상 CD 드라이브를 찾습니다. 이 드라이브에 설치 관리자 파일(.msi)이 포함되어 있습니다. 이 파일을 두 번 클릭합니다. 그러면 PC의  `C:\Program Files (x86)\Microsoft IoT\FFU\` 아래에 새 디렉터리가 생성되고 "flash.ffu" 이미지 파일이 보입니다.
4. 아래와 같이 보드의 첫 번째 스위치를 USB 부팅으로 설정하여 DragonBoard를 다운로드 모드로 설정합니다. 그런 다음, microUSB 케이블을 통해 DragonBoard를 호스트 PC에 연결하고, DragonBoard를 12V(>1A) 전원 공급 장치에 연결합니다.
5. 녹색 원을 사용하여 DragonBoard가 PC에 연결되어 있는지 탐지하는 DragonBoard 업데이트 도구를 시작합니다. 다운로드한 DragonBoard의 FFU를 찾은 다음, _프로그램_ 단추를 클릭합니다.
6. "찾아보기"를 다시 클릭하고 5단계에서 생성된 "rawprogram0.xml"을 선택합니다. 그런 다음, "프로그램" 단추를 클릭합니다.
7. 다운로드가 완료되면 보드에서 전원 공급 장치와 microUSB 케이블을 분리하고 USB 부팅 스위치를 다시 _OFF_로 전환합니다. HDMI 디스플레이, 마우스 및 키보드를 DragonBoard에 연결하고 전원 공급 장치를 다시 연결합니다. 몇 분 후 Windows 10 IoT Core 기본 애플리케이션이 보입니다. 

![다운로드 모드인 DragonBoard](../media/DeviceSetup/db1.png)

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



