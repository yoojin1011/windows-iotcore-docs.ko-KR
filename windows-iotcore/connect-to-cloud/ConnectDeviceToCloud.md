---
title: 장치를 클라우드에 연결
ms.date: 08/28/2017
ms.topic: article
description: 장치를 클라우드에 연결 하는 방법에 대해 알아봅니다.
keywords: windows iot, Azure, 보안, 신뢰할 수 있는 플랫폼 모듈, SoC
ms.openlocfilehash: 6bce16b45175c4c19156f30f35f6d3502f675930
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918394"
---
# <a name="connect-your-device-to-the-cloud"></a>장치를 클라우드에 연결

암호 또는 인증서와 같은 보안 정보를 장치에 저장 하면 장치가 노출에 취약 해질 수 있습니다. 누출 된 암호는 장치 또는 전체 시스템의 보안을 손상 시킬 수 있는 surefire 방법입니다. Windows 제품군에서 OS의 보안을 지 원하는 기술은 신뢰할 수 있는 플랫폼 모듈입니다.

TPM ( [신뢰할 수 있는 플랫폼 모듈](https://en.wikipedia.org/wiki/Trusted_Platform_Module) ) 장치는 데이터를 저장 하 고 계산을 수행할 수 있는 마이크로 컨트롤러입니다. 제조업체에서 컴퓨터의 마더보드 또는 칩 (SoC)의 시스템에 통합 된 모듈 중 하나를 사용할 수 있습니다. 

## <a name="inside-the-tpm"></a>TPM 내부 

TPM의 주요 기능은 쓰기 전용 메모리입니다. TPM은 데이터를 기반으로 해당 데이터를 기반으로 [HMAC](https://en.wikipedia.org/wiki/Hash-based_message_authentication_code)와 같은 암호화 해시를 계산할 수도 있습니다.
해시에 지정 된 암호를 확인 하는 것은 불가능 하지만 비밀이 통신의 양쪽 당사자에 게 알려진 경우 다른 당사자 로부터 받은 해시가 해당 암호에서 생성 되었는지 여부를 확인할 수 있습니다.

암호화 키 사용의 기본 개념은 장치 프로 비전 프로세스 중에 IoT 장치와 클라우드 간에 비밀 (공유 액세스 키 라고도 함)을 설정 하 고 공유 하는 것입니다. 이 시점부터 비밀에서 파생 된 HMAC가 IoT 장치를 인증 하는 데 사용 됩니다.

## <a name="device-provisioning"></a>장치 프로 비전 

Windows 10 IoT Core 장치를 프로 비전 하는 도구를 IoT Core 대시보드 라고 하며 [다운로드 페이지](http://go.microsoft.com/fwlink/?LinkID=708576)에서 다운로드할 수 있습니다.

대시보드는 OS 이미지를 생성 하 고 장치를 Azure에 안전 하 게 연결 합니다. 이 작업은 물리적 장치를 Azure IoT Hub의 장치 ID와 연결 하 고 장치 전용 공유 액세스 키를 장치의 TPM으로 인쇄 하 여 수행 합니다. 

TPM 칩이 없는 장치의 경우이 도구는 소프트웨어 에뮬레이트된 TPM을 설치할 수 있습니다. 이는 보안을 제공 하는 것이 아니라 작성자 장치 (예: Raspberry Pi 2 또는 3)를 사용 하 여 앱을 개발 하 고, 앱을 변경 하지 않고도 하드웨어 TPM을 사용 하 여 장치에 보안 "강화"를 제공 하는 것을 허용 합니다. 

장치를 Azure에 연결 하려면 "Azure에 연결" 탭을 클릭 합니다.

![Azure에 연결 탭 열기](../media/ConnectDeviceToCloud/Building_Secure_Apps_for_IoT_Core_Screen01.png)

Azure 계정에 로그인 하 라는 메시지가 표시 됩니다. 원하는 Azure IoT Hub 인스턴스를 선택 하 고 실제 장치를 연결 합니다. Azure 구독에 IoT Hub 인스턴스가 없는 경우이 도구를 사용 하 여 무료 인스턴스를 만들 수 있습니다. 

장치를 연결 하기 위해 IoT Hub 및 장치 ID를 선택 하면 TPM에서 해당 장치의 공유 액세스 키를 임 프린트가 수 있습니다.

![장치 프로 비전](../media/ConnectDeviceToCloud/Building_Secure_Apps_for_IoT_Core_Screen02.png)

이제 장치를 안전한 방식으로 Azure에 연결할 준비가 되었습니다. 

Windows 장치 포털을 사용 하 여 프로 비전 된 후 인터넷에 처음 연결할 때 IoT Hub 연결 문자열을 동적으로 가져올 수도 있습니다. 장치 포털의 "Azure 클라이언트" 탭에서이 작업을 수행할 수 있습니다.

![Azure 클라이언트 탭](../media/ConnectDeviceToCloud/azure-clients.png)

## <a name="helpful-resources"></a>유용한 리소스:
* [Azure에 앱 연결](../connect-to-cloud/ConnectAppToCloud.md)
* [IoT Core 용 보안 앱 빌드](https://blogs.windows.com/buildingapps/2016/07/20/building-secure-apps-for-windows-iot-core/#oqFLXiWIL1iCF8j9.97)
