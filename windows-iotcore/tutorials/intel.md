---
title: Intel 디바이스 설정
ms.date: 05/22/2019
ms.topic: article
description: Windows 10 IoT Core를 사용하여 Intel 디바이스를 설정하는 방법을 알아봅니다.
keywords: Windows 10 IoT Core, Intel
ms.custom: RS5
ms.openlocfilehash: 3f92f9af4ddb492b1f465ee00b55e88e16b3a67f
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918505"
---
# <a name="setting-up-an-intel-device"></a>Intel 디바이스 설정

Qualcomm 디바이스로 제작하려는 경우에는 [IoT Core 제작 가이드](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)를 참조하세요. 제조사 이미지는 제작에 사용할 수 없습니다.

> [!NOTE]
> BIOS 설정을 다시 입력하고, USB 드라이브 대신 하드 드라이브에서 로드하도록 부팅 드라이브 순서를 전환하여 디바이스가 eMMC 메모리에서 부팅되도록 설정합니다.

## <a name="using-emmc"></a>eMMC 사용

1. 실행 중인 Windows 10 버전과 관련된 [Windows 평가 및 배포 키트](https://docs.microsoft.com/windows-hardware/get-started/adk-install)를 다운로드하여 설치합니다.
2. USB 드라이브를 머신에 삽입합니다.
3. USB 부팅 가능 WinPE 이미지 만들기:
4. 관리자로 배포 및 이미지 도구 환경 `(C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Deployment Tools)`를 시작합니다.
5. Windows PE 파일의 작업 복사본을 만듭니다. x86, amd64 또는 ARM: `Copype amd64 C:\WINPE_amd64`를 지정합니다.
6. 아래의 WinPE 드라이브 문자를 지정하여 USB 플래시 드라이브에 Windows PE를 설치합니다. 자세한 내용은 [여기](https://docs.microsoft.com/windows-hardware/manufacture/desktop/winpe-create-usb-bootable-drive)서 찾을 수 있습니다. `MMakeWinPEMedia /UFD C:\WinPE_amd64 P:`
7. 다운로드한 ISO 파일을 두 번 클릭하고 탑재된 가상 CD 드라이브를 찾아 [Windows 10 IoT Core 이미지](https://downloads.up-community.org/?post_type=wpdmpro&p=204&preview=true)를 다운로드합니다.
8. 이 드라이브에 포함된 설치 관리자 파일(.msi)을 두 번 클릭합니다. 그러면 PC의 C:\Program Files (x86)\Microsoft IoT\FFU\ 아래에 새 디렉터리가 생성됩니다. 이 디렉터리에 "flash.ffu" 이미지가 있습니다.
9. 디바이스의 FFU와 함께 [eMMC 설치 관리자 스크립트](https://github.com/ms-iot/content/blob/develop/Resources/eMMCInstaller.zip)를 USB 디바이스의 루트 디렉터리에 다운로드하여 압축을 풀고 복사합니다.
10. USB 드라이브, 마우스 및 키보드를 USB 허브에 연결합니다. HDMI 디스플레이를 디바이스에 연결하고, 디바이스를 USB 허브에 연결하고, 전원 코드를 디바이스에 연결합니다.
11. 디바이스의 BIOS 설정으로 이동합니다. 운영 체제로 *Windows*를 선택하고, USB 드라이브에서 부팅하도록 디바이스를 설정합니다. 시스템이 다시 부팅되면 WinPE 명령 프롬프트가 표시됩니다. WinPE 프롬프트를 USB 드라이브로 전환합니다. 일반적으로 C: 또는 D:이지만 다른 드라이버 문자를 사용해야 하는 경우도 있습니다.
12. 디바이스의 eMMC 메모리에 Windows 10 IoT Core 이미지를 설치하는 eMMC 설치 관리자 스크립트를 실행합니다. 스크립트가 완료되면 아무 키를 눌러 `wpeutil reboot`를 실행합니다. 시스템이 Windows 10 IoT Core로 부팅되고, 구성 프로세스를 시작하고, 기본 애플리케이션을 로드합니다.

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


