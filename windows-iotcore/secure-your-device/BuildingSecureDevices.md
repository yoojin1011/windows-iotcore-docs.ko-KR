---
title: Windows 10 IoT Core 사용 하 여 보안 장치 구성
author: TorstenStein
ms.author: torstens
ms.date: 08/28/2017
ms.topic: article
description: 보안 부팅, Tpm, 등을 구현 함으로써 보안 장치를 빌드하는 방법에 알아봅니다.
keywords: windows iot, 보안, 펌웨어, 보안 부팅, TPM, Bitlocker, 암호화
ms.openlocfilehash: 611d82af25d9c4959335aa208e0d06b49daa5f9f
ms.sourcegitcommit: c4232e384e7347f97477e5cd3cc941de492f6a64
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/21/2019
ms.locfileid: "65986480"
---
# <a name="building-secure-devices-with-windows-10-iot-core"></a>Windows 10 IoT Core 사용 하 여 보안 장치 구성

## <a name="introduction"></a>소개  

Windows 10 IoT Core 사용 하 여 Microsoft 가져오는 강력한 엔터프라이즈 활용할 수 있는 엔터프라이즈급 보안 기능 IoT 장치의 작은 리소스가 제한 된 클래스입니다. 실질적인 혜택을 제공 하려면 이러한 보안 기능에 대 한 하드웨어 플랫폼을 고정 하는 방법을 제공 해야 합니다. 이 문서는 인식 '결정권자' 적절 한 하드웨어를 선택 하 고 빌드, 구성 및 고객에 게 안전한 IoT 장치를 제공 하려는 OEM 장치 작성기와 보안에 대 한 자세한 지침을 제공 합니다.
![데이터 보안](../media/SecurityFlowAndCertificates/DataRestExecutionMotion.png)

## <a name="building-a-secure-iot-devices"></a>안전한 IoT 장치를 구축합니다.  
이 섹션에서는 Windows IoT Core를 사용 하 여 안전한 IoT 장치를 빌드하는 프로세스를 통해 개발자와 Oem 도와줍니다. 에서는 생산을 보안이 활성화 된 IoT 장치 뿐만 아니라 다양 한 플랫폼 보안 기능을 지원 하기 위해 하드웨어를 처리할 수 있습니다.

![장치 빌드 프로세스](../media/SecurityFlowAndCertificates/DeviceBuildProcess.png)


## <a name="choosing-security-enabled-hardware"></a>사용 하도록 설정 하는 보안 하드웨어 선택
Windows IoT Core에 고객 데이터를 보호 하기 위해 플랫폼에서 작성 하는 보안 기능을 완벽 하 게 이러한 기능을 활용 하는 하드웨어 보안 기능이 의존 합니다. 사실, 소프트웨어 메모리를 조작할 수 있습니다 하 고 트러스트 앵커 또는 변경할 수 없는 장치 id만 소프트웨어를 통해 제공 될 수 있는 없을 자체적으로 보호할 수 없습니다. 플랫폼 모듈 (TPM)을 신뢰할 수 있는 하드웨어 기반 보안, 예: 스마트 카드 또는 보안 기능을 내장할 SoC.를 제공 하는 방법은 여러 가지가 있습니다. 

플랫폼 지원 되는 하드웨어에 대 한 자세한 내용은 섹션을 참조 [Soc 및 사용자 지정 보드](https://docs.microsoft.com/en-us/windows/iot-core/learn-about-hardware/socsandcustomboards) 

### <a name="trusted-platform-module"></a>신뢰할 수 있는 플랫폼 모듈
Windows IoT Core는 TPM 2.0 하드웨어 보안 플랫폼으로 사용합니다. TPM 2.0 완벽 하 게 활용 하기 위해 BitLocker, 보안 부팅, Azure 자격 증명 저장소와 같은 Windows IoT Core 보안 기능 등을 제공 하는 하드웨어 플랫폼을 사용 하는 Oem 사용 하는 것이 좋습니다. TPM (fTPM) 펌웨어 또는 개별 TPM (dTPM)으로 프로덕션 구현에 TPM 장치에 대 한 두 가지 옵션이 있습니다. 불연속 Tpm Infineon, NazionZ 등과 같은 여러 제조업체에서 제공 됩니다. 일부 SoC 제조업체에서 BSP의 일부로 fTPM 구현을 제공합니다. 

Tpm에 대 한 자세한 내용은 [TPM 개요](https://docs.microsoft.com/en-us/windows/iot-core/secure-your-device/tpm) 하 고 [TPM을 설정 하는 방법을](https://docs.microsoft.com/en-us/windows/iot-core/secure-your-device/setuptpm)합니다.

### <a name="storage-options"></a>저장소 옵션
인기 있는 Raspberry Pi 3과 같은 개발 보드, 유연성을 제공 하 고 개발자 이동식 SD 카드를 통해 모든 플랫폼 이미지를 허용 합니다. 대부분의 업계 IoT 장치에 대 한 유연성 바람직하지 않으며 공격에 대 한 손쉬운 대상이 이러한 장치를 만들 수 있습니다. 대신 하드웨어를 디자인할 때에 eMMC 저장소를 사용 하 여 저렴 한 비용, 더 작은 IoT 장치에 대 한 하는 것이 좋습니다. 포함 된 저장소 크게 더욱 어렵게 장치에서 콘텐츠를 구분 하 고 차례로 장치나 데이터 도난에 맬웨어 소개의 가능성을 줄입니다.

## <a name="creating-a-retail-image"></a>일반 정품 이미지 만들기 
때 [Windows IoT Core 일반 정품 이미지를 만드는](https://docs.microsoft.com/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)원격을 허용 하는 개발자 도구가 없습니다 액세스할 수 있는지 확인 하 고 디버그는 프로덕션 시스템에 있는 이러한 장치의 공격에 노출 시킬 수 있습니다. 했는지와 같은 개발자 도구를 사용 하는 경우 [Windows Device Portal](https://docs.microsoft.com/en-us/windows/iot-core/manage-your-device/remotedisplay)를 [FTP 서버](https://docs.microsoft.com/en-us/windows/iot-core/connect-your-device/ftp)합니다 [SSH](https://docs.microsoft.com/en-us/windows/iot-core/connect-your-device/ssh), 또는 [PowerShell](https://docs.microsoft.com/en-us/windows/iot-core/connect-your-device/powershell) 이미지에서 개발, 테스트 및 소매 IoT Core 이미지와 이러한 도구를 포함 하지 않는 시나리오의 유효성을 검사 하는 중

### <a name="user-accounts"></a>사용자 계정
대부분의 사용자 "의 소유권을 가져오면" Pc 및 휴대폰-아이디어와 같은 장치 장치를 개인 설정의 unboxed 및 장치에 액세스 하려면 자격 증명을 설정 하는 경우 개념이 익숙합니다. 소비자 Pc 및 휴대폰와는 달리 IoT 장치 되지 범용 컴퓨팅 장치의 역할도 합니다. 대신 일반적으로 단일 앱, 고정 용도 장치 됩니다. Windows 개발 주기 동안 장치에 원격으로 연결할 수 있는 장치 관리자의 개념을 지 원하는 경우에 산업 IoT 장치의 이러한 지원 약한 암호를 사용 하는 경우에 특히는 위협에 발생할 수 있습니다. 일반적으로 Windows 10 IoT Core 장치에 없습니다 "default" 계정 또는 암호를 만들 수는 것이 좋습니다.

## <a name="lockdown-a-retail-image"></a>잠금 정품 이미지
범용 컴퓨팅 장치, Pc 등에서 사용자 응용 프로그램을 설치, 운영 요구에 맞게 함수를 정의 하는 장치 도구 모음에 가장 보안 기능을 비롯 한 설정을 변경할 수 있습니다. 대부분의 IoT 장치는 고정-함수-는 장치 용도 장치 수명 주기 동안 변경 되지 것입니다. 이러한 장치는 계속 소프트웨어 업데이트를 수신 하거나 기능 업데이트를 사용 하도록 해당 operational 경계 내에서 예를 들어 스마트 자동 온도 조절기를에서 사용자 인터페이스 또는 온도 규정 개선 합니다. 이 정보를 수만 알려져 있고 신뢰할 수 있는 코드의 실행을 허용 하 여 IoT 장치를 완벽 하 게 잠금에 사용 합니다. Windows 10 IoT Core device Guard는 잠긴 장치에서 알 수 없거나 신뢰할 수 없는 실행 코드를 실행할 수 없음을 확인 하 여 IoT 장치를 보호할 수 있습니다.

Microsoft는 제공 하는 [턴키 보안 패키지](https://github.com/ms-iot/security/tree/master/TurnkeySecurity) 장치 빌더 빌드를 완벽 하 게 IoT 장치를 잠글 수 있도록 하는 IoT Core 장치에 대 한 주요 보안 기능을 쉽게 사용을 용이 하 게 합니다. 패키지에 도움이 됩니다.

* 보안 부팅 키 프로 비전 하 고 지원 되는 IoT 플랫폼에서이 기능을 사용 하도록 설정
* BitLocker를 사용 하 여 장치 암호화의 설정 및 구성 
* 시작만 서명 된 응용 프로그램 및 드라이버를 실행할 수 있도록 장치 잠금

단계별 지침에 설명 되어는 [를 사용 하도록 설정 하는 보안 부팅, BitLocker, 및 Device Guard](https://docs.microsoft.com/en-us/windows/iot-core/secure-your-device/securebootandbitlocker) 섹션입니다.

## <a name="device-production"></a>장치 프로덕션
잠금 이미지 유효성이 검사 되 면 제조에 사용할 수 있습니다. 자세한 내용은 참조 [제조 IoT Core](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/)합니다.
