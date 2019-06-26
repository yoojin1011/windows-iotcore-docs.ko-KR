---
title: 디바이스 설정
ms.author: saclayt
ms.date: 04/10/2018
ms.topic: article
description: SD 카드를 사용하여 Windows 10 IoT Core로 디바이스를 설정하는 방법을 알아보세요.
keywords: Windows 10 IoT Core, SD 카드, Windows 10 IoT Core 대시보드
ms.custom: RS5
ms.openlocfilehash: ece83dcc7f6961a4614db2ee0c6a1331b009bb47
ms.sourcegitcommit: 9ec4716afde25fdc8b94f7c0794448501f451b55
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/17/2019
ms.locfileid: "60167731"
---
# <a name="setting-up-your-device"></a>디바이스 설정

아래에서는 Windows 10 IoT Core로 디바이스를 플래시하는 네 가지 방법을 확인할 수 있습니다. [프로토타입 제작에 추천하는 보드 목록](PrototypeBoards.md)에 포함된 차트에 따라 적절한 지침을 따릅니다. 오른쪽 열을 사용하여 다양한 플래시 방법을 탐색하세요.

> [!IMPORTANT]
> 상용화에 제조사 이미지를 사용하지 마세요. 디바이스를 상용화하려는 경우 최적의 보안을 위해 사용자 지정 FFU를 사용해야 합니다. [여기](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)에서 자세한 내용을 알아보세요.

> [!IMPORTANT]
> "이 디스크 포맷" 팝업이 나타나면 디스크를 포맷하지 _마세요_. 이 이슈를 수정하지 위한 작업을 진행 중입니다.

## <a name="using-the-iot-dashboard-raspberry-pi-minnowboard-nxp"></a>IoT 대시보드(Raspberry Pi, MinnowBoard, NXP) 사용

> [!Video https://www.youtube.com/embed/JPRUbGIyODY]


> [!IMPORTANT]
> MinnowBoard Turbot의 최신 64비트 펌웨어는 [MinnowBoard 웹 사이트](https://minnowboard.org/tutorials/updating-the-firmware)에서 찾을 수 있습니다(MinnowBoard 사이트의 지침에서 4단계 생략).

> [!IMPORTANT]
> NXP는 사용자 지정 이미지만 지원합니다. 사용자 지정 이미지를 플래시하려는 경우 OS 빌드 드롭다운 목록에서 "사용자 지정"을 선택하고, [여기](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image)의 지침에 따라 기본 이미지를 만들고, 아래의 나머지 지침에 따라 완료합니다.

> [!NOTE]
> 대시보드는 Raspberry Pi 3B+를 설정하는 데 사용할 수 없습니다. 3B+ 디바이스가 있는 경우 [3B+ 기술 미리 보기](https://www.microsoft.com/en-us/software-download/windowsiot)를 사용해야 합니다. 기술 미리 보기의 [알려진 제한 사항](https://docs.microsoft.com/en-us/windows/iot-core/troubleshooting)을 확인하여 개발 작업에 적합한지 알아보세요.

> [!TIP]
> 안정성을 높이고 디바이스를 외부 디스플레이에 연결하여 기본 애플리케이션이 부팅되는 것을 볼 수 있도록 SanDisk SD 카드 같은 고성능 SD 카드를 사용하는 것이 좋습니다.


1. [여기](https://docs.microsoft.com/windows/iot-core/downloads)서 Windows 10 IoT Core 대시보드를 다운로드하세요.
2. 다운로드한 후에는 대시보드를 열고, _새 디바이스 설치_를 클릭하고, 컴퓨터에 SD 카드를 삽입합니다.
3. 표시된 대로 모든 필드를 작성합니다.
4. 소프트웨어 사용 조건에 동의하고 _다운로드 및 설치_를 클릭합니다. Windows 10 IoT Core가 SD 카드에 플래시되는 것을 볼 수 있습니다.


![대시보드 스크린샷](../../media/DeviceSetup/Dashboard-Screenshot.jpg)
 

## <a name="using-the-iot-dashboard-dragonboard-410c"></a>IoT 대시보드(DragonBoard 410c) 사용

> [!Video https://www.youtube.com/embed/iPm57hGq-Q8]

> [!TIP]
> 기본 애플리케이션이 부팅되는 것을 보려면 디바이스를 외부 디스플레이에 연결하는 것이 좋습니다.

> [!IMPORTANT]
> 사용자 지정 이미지를 플래시하려는 경우 OS 빌드 드롭다운 목록에서 "사용자 지정"을 선택하고, [여기](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image)의 지침에 따라 기본 이미지를 만들고, 아래의 나머지 지침에 따라 완료합니다.

> [!IMPORTANT]
> 새 Dragonboard를 사용하는 경우 Android가 설치된 상태로 제공됩니다. eMMC 플래시 메서드를 사용하여 디바이스의 데이터를 지우고 다시 로드해야 합니다.

> [!NOTE]
> DragonBoard에서 오디오 관련 이슈가 발생하는 경우 [여기서](https://developer.qualcomm.com/download/db410c/stereo-connector-and-audio-routing-application-note.pdf) Qualcomm의 설명서를 읽어보시기를 권장합니다. 

1. [여기](https://docs.microsoft.com/windows/iot-core/downloads)서 Windows 10 IoT Core 대시보드를 다운로드하세요.
2. 다운로드한 후 대시보드를 열고 "Qualcomm DragonBoard 410c"를 선택합니다. 그런 다음, _Windows 참가자로 로그인_합니다. DragonBoard 410c를 플래시하려면 참가자로 로그인해야 합니다. 
3. microUSB 케이블을 사용하여 Qualcomm 보드를 개발자 머신에 연결합니다.
4. 볼륨 크게(+) 단추를 누른 상태에서 12V(>1A) 전원 공급 장치를 사용하여 Dragonboard를 켭니다. 디바이스를 디스플레이에 연결하면 망치, 번개 및 톱니 이미지가 표시됩니다. 
5. 이제 디바이스가 대시보드에 아래와 같이 표시됩니다. 적절한 디바이스를 선택합니다.
6. 소프트웨어 사용 조건에 동의하고 _다운로드 및 설치_를 클릭합니다. Windows 10 IoT Core가 디바이스에 플래시되는 것을 볼 수 있습니다.


![플래시 모드의 DragonBoard](../../media/DeviceSetup/db4.png)


## <a name="flashing-with-emmc-for-dragonboard-410c-other-qualcomm-devices"></a>eMMC로 플래시(DragonBoard 410c의 경우 다른 Qualcomm 디바이스)

1. [x86](https://developer.qualcomm.com/download/db410c/windows-10-iot-update-tool-dragonboard-410c-x86.zip) 또는 [x64](https://developer.qualcomm.com/download/db410c/windows-10-iot-update-tool-dragonboard-410c-x64.zip) 머신에 맞는 DragonBoard 업데이트 도구를 다운로드하여 설치합니다.
2. [Windows 10 IoT Core DragonBoard FFU](https://developer.microsoft.com/en-us/windows/iot/Downloads)를 다운로드합니다.
3. 다운로드한 ISO 파일을 두 번 클릭하고 탑재된 가상 CD 드라이브를 찾습니다. 이 드라이브에 설치 관리자 파일(.msi)이 포함되어 있습니다. 이 파일을 두 번 클릭합니다. 그러면 PC의  `C:\Program Files (x86)\Microsoft IoT\FFU\` 아래에 새 디렉터리가 생성되고 "flash.ffu" 이미지 파일이 보입니다.
4. 아래와 같이 보드의 첫 번째 스위치를 USB 부팅으로 설정하여 DragonBoard를 다운로드 모드로 설정합니다. 그런 다음, microUSB 케이블을 통해 DragonBoard를 호스트 PC에 연결하고, DragonBoard를 12V(>1A) 전원 공급 장치에 연결합니다.
5. 녹색 원을 사용하여 DragonBoard가 PC에 연결되어 있는지 탐지하는 DragonBoard 업데이트 도구를 시작합니다. 다운로드한 DragonBoard의 FFU를 찾은 다음, _프로그램_ 단추를 클릭합니다.
6. "찾아보기"를 다시 클릭하고 5단계에서 생성된 "rawprogram0.xml"을 선택합니다. 그런 다음, "프로그램" 단추를 클릭합니다.
7. 다운로드가 완료되면 보드에서 전원 공급 장치와 microUSB 케이블을 분리하고 USB 부팅 스위치를 다시 _OFF_로 전환합니다. HDMI 디스플레이, 마우스 및 키보드를 DragonBoard에 연결하고 전원 공급 장치를 다시 연결합니다. 몇 분 후 Windows 10 IoT Core 기본 애플리케이션이 보입니다. 

![다운로드 모드인 DragonBoard](../../media/DeviceSetup/db1.png)

> [!NOTE]
> BIOS 설정을 다시 입력하고, USB 드라이브 대신 하드 드라이브에서 로드하도록 부팅 드라이브 순서를 전환하여 디바이스가 eMMC 메모리에서 부팅되도록 설정합니다.


## <a name="flashing-with-emmc-for-up-squared-other-intel-devices"></a>eMMC를 사용하여 플래시(Up Squared의 경우 다른 Intel 디바이스)

1. 실행 중인 Windows 10 버전과 관련된 [Windows 평가 및 배포 키트](https://docs.microsoft.com/windows-hardware/get-started/adk-install)를 다운로드하여 설치합니다.
2. USB 드라이브를 머신에 삽입합니다.
3. 다음과 같이 USB 부팅 가능 WinPE 이미지를 만듭니다.
4. 관리자로 배포 및 이미지 도구 환경 `(C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Deployment Tools)`를 시작합니다.
5. Windows PE 파일의 작업 복사본을 만듭니다. x86, amd64 또는 ARM: `Copype amd64 C:\WINPE_amd64`를 지정합니다.
6. USB 플래시 드라이브에 Windows PE를 설치하고 아래의 WinPE 드라이브 문자를 지정합니다. 자세한 내용은 [여기](https://docs.microsoft.com/windows-hardware/manufacture/desktop/winpe-create-usb-bootable-drive)서 찾을 수 있습니다. `MMakeWinPEMedia /UFD C:\WinPE_amd64 P:`
7. 다운로드한 ISO 파일을 두 번 클릭하고 탑재된 가상 CD 드라이브를 찾아 [Windows 10 IoT Core 이미지](https://downloads.up-community.org/?post_type=wpdmpro&p=204&preview=true)를 다운로드합니다.
8. 이 드라이브에 포함된 설치 관리자 파일(.msi)을 두 번 클릭합니다. 그러면 PC의 C:\Program Files (x86)\Microsoft IoT\FFU\ 아래에 새 디렉터리가 생성됩니다. 이 디렉터리에 "flash.ffu" 이미지가 있습니다.
9. 디바이스의 FFU와 함께 [eMMC 설치 관리자 스크립트](https://github.com/ms-iot/content/blob/develop/Resources/eMMCInstaller.zip)를 USB 디바이스의 루트 디렉터리에 다운로드하여 압축을 풀고 복사합니다.
10. USB 드라이브, 마우스 및 키보드를 USB 허브에 연결합니다. HDMI 디스플레이를 디바이스에 연결하고, 디바이스를 USB 허브에 연결하고, 전원 코드를 디바이스에 연결합니다.
11. 디바이스의 BIOS 설정으로 이동합니다. 운영 체제로 *Windows*를 선택하고, USB 드라이브에서 부팅하도록 디바이스를 설정합니다. 시스템이 다시 부팅되면 WinPE 명령 프롬프트가 표시됩니다. WinPE 프롬프트를 USB 드라이브로 전환합니다. 일반적으로 C: 또는 D:이지만 다른 드라이버 문자를 사용해야 하는 경우도 있습니다.
12. 디바이스의 eMMC 메모리에 Windows 10 IoT Core 이미지를 설치하는 eMMC 설치 관리자 스크립트를 실행합니다. 스크립트가 완료되면 아무 키를 눌러 `wpeutil reboot`를 실행합니다. 시스템이 Windows 10 IoT Core로 부팅되고, 구성 프로세스를 시작하고, 기본 애플리케이션을 로드합니다.

> [!NOTE]
> BIOS 설정을 다시 입력하고, USB 드라이브 대신 하드 드라이브에서 로드하도록 부팅 드라이브 순서를 전환하여 디바이스가 eMMC 메모리에서 부팅되도록 설정합니다.


## <a name="connecting-to-a-network"></a>네트워크에 연결

#### <a name="wired-connection"></a>유선 연결
디바이스에 유선 연결을 지원하는 이더넷 포트 또는 USB 이더넷 어댑터가 있는 경우 이더넷 케이블을 연결하여 네트워크에 연결합니다.

#### <a name="wireless-connection"></a>무선 연결
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

## <a name="connecting-to-windows-device-portal"></a>Windows 디바이스 포털에 연결

[Windows 디바이스 포털](../../manage-your-device/DevicePortal.md)을 사용하여 웹 브라우저를 통해 디바이스를 연결합니다. 디바이스 포털에서는 중요한 구성과 디바이스 관리 기능을 사용할 수 있습니다. 

