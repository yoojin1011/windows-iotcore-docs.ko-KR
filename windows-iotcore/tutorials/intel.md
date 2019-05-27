---
title: Intel 장치 설정
ms.author: saclayt
ms.date: 05/22/2019
ms.topic: article
description: Windows 10 IoT Core 사용 하 여 Intel 장치를 설정 하는 방법에 알아봅니다.
keywords: Windows 10 IoT Core, Intel
ms.custom: RS5
ms.openlocfilehash: a42771d82ffbebee9a45a72c5256479f5f611388
ms.sourcegitcommit: 8aadc776da7b473159f9023cd555145819e7e952
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66182185"
---
# <a name="setting-up-an-intel-device"></a>Intel 장치 설정

Qualcomm 장치를 사용 하 여 제조 하려는 경우 참조 하는 [IoT Core 제조 가이드](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)합니다. 제조를 위한 작성자 이미지를 사용할 수 없습니다.

> [!NOTE]
> BIOS 설정을 다시 입력 하 고 대신 USB 드라이브에서 하드 드라이브에서 로드 하는 부팅 드라이브 순서를 전환 하 여 eMMC 메모리에서 장치는 이제 부팅 해야 합니다.

## <a name="using-emmc"></a>EMMC를 사용 하 여

1. 다운로드 및 설치 합니다 [Windows 평가 및 배포 키트](https://docs.microsoft.com/windows-hardware/get-started/adk-install) 실행 중인 Windows 10의 버전과 상관 관계 자동 연결 합니다.
2. 컴퓨터에 USB 드라이브를 삽입 합니다.
3. USB 부팅 가능 WinPE 이미지를 만듭니다.
4. 배포 및 이미징 도구 환경을 시작 `(C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Deployment Tools)` 관리자 권한으로 합니다.
5. Windows PE 파일의 작업 복사본을 만듭니다. X86, amd64 지정 또는 ARM: `Copype amd64 C:\WINPE_amd64`
6. Windows PE 아래 WinPE 드라이브 문자를 지정 하는 USB 플래시 드라이브에 설치 합니다. 자세한 정보를 찾을 수 있습니다 [여기](https://docs.microsoft.com/windows-hardware/manufacture/desktop/winpe-create-usb-bootable-drive)합니다. `MMakeWinPEMedia /UFD C:\WinPE_amd64 P:`
7. 다운로드 합니다 [Windows 10 IoT Core 이미지](https://downloads.up-community.org/?post_type=wpdmpro&p=204&preview=true) 탑재 된 가상 CD 드라이브를 찾아 다운로드 한 ISO 파일을 두 번 클릭 하 여 합니다.
8. 이 드라이브는 설치 파일 (.msi);에 포함 됩니다. 두 번 클릭 합니다. C:\Program Files (x86) \Microsoft IoT\FFU\ shoul d 참조 이미지 파일에는 아래에 있는 PC에이 새 디렉터리를 만듭니다 "flash.ffu"입니다.
9. 다운로드 하 고 압축을 풉니다 복사 합니다 [eMMC 설치 관리자 스크립트](https://github.com/ms-iot/content/blob/develop/Resources/eMMCInstaller.zip) 장치의 FFU 함께 USB 장치의 루트 디렉터리입니다.
10. USB 허브를 USB 드라이브, 마우스 및 키보드를 연결 합니다. USB 허브 및 장치에 전원 코드를 장치에 HDMI 표시, 장치를 연결 합니다.
11. 장치의 BIOS 설정으로 이동 합니다. 선택 *Windows* uSB 드라이브에서 부팅 하려면 운영 체제 하며 장치를 설정 합니다. 시스템이 다시 부팅 하면 WinPE 명령 프롬프트 표시 됩니다. USB 드라이브에 WinPE 프롬프트를 전환 합니다. 일반적으로 C: 또는 D 이지만 다른 드라이버 문자를 시도해 야 할 수 있습니다.
12. EMMC 장치의 eMMC 메모리를 Windows 10 IoT Core 이미지를 설치 하는 설치 관리자 스크립트를 실행 합니다. 완료 되 면 아무 키나 눌러 및 실행 `wpeutil reboot`합니다. 시스템은 Windows 10 IoT Core 부팅 하 고 구성 프로세스를 시작 하 고 기본 응용 프로그램 로드 해야 합니다.

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


