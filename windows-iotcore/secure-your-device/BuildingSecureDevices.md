---
title: Windows 10 IoT Core 사용 하 여 더 안전한 장치 구축
author: TorstenStein
ms.author: torstens
ms.date: 08/28/2017
ms.topic: article
description: 보안 부팅, Tpm, 등을 구현 함으로써 더 안전한 장치를 빌드하는 방법에 알아봅니다.
keywords: windows iot, 보안, 펌웨어, 보안 부팅, TPM, Bitlocker, 암호화
ms.openlocfilehash: b7340ce168f766eb13e00bfca39619e92a931c30
ms.sourcegitcommit: 2e7e9555fe71ca60b5f41dbf06051a50520a368a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66491718"
---
# <a name="building-more-secure-devices-with-windows-10-iot-core"></a>Windows 10 IoT Core 사용 하 여 더 안전한 장치 구축

## <a name="introduction"></a>소개  

Windows 10 IoT Core 강력한 엔터프라이즈급 보안 기능을 제공 활용할 수 있는 IoT 장치의 작은, 리소스가 제한 된 클래스입니다. 실질적인 혜택을 제공 하려면 이러한 보안 기능에 대 한 하드웨어 플랫폼을 고정 하는 방법을 제공 해야 합니다. 이 문서에서는 OEM 장치 작성기 고급 지침을 제공 하 고 보안 인식 결정자 적절 한 하드웨어 및 빌드를 선택 하는 구성 및 고객에 게는 더 안전한 IoT 장치를 제공 합니다.
![데이터 보안](../media/SecurityFlowAndCertificates/DataRestExecutionMotion.png)

## <a name="building-a-more-secure-iot-device"></a>더 안전한 IoT 장치를 만드는  
IoT Core를 사용 하 여 더 안전한 IoT 장치를 빌드하는 프로세스는 프로덕션 IoT 장치의 보안 지원 뿐만 아니라 다양 한 플랫폼 보안 기능을 지원 하기 위해 하드웨어를 포함 합니다.

![장치 빌드 프로세스](../media/SecurityFlowAndCertificates/DeviceBuildProcess.png)


## <a name="choosing-security-enabled-hardware"></a>보안 기능이 설정 된 하드웨어를 선택합니다.
IoT Core에 고객 데이터를 보호 하기 위해 플랫폼에 기본 제공 보안 기능을 완벽 하 게 이러한 기능을 활용 하는 하드웨어 보안 기능이 의존 합니다. 사실, 소프트웨어 메모리를 조작할 수 있습니다 하 고 변경할 수 없는 장치 id만 소프트웨어를 통해 제공 될 수 있는 없거나 트러스트 앵커 있기 때문에 자체적으로 보호할 수 없습니다. 스마트 카드, 신뢰할 수 있는 플랫폼 모듈 (Tpm)를 SoC.에 기본 제공 보안 기능 등의 하드웨어 기반 보안을 제공 하는 방법은 여러 가지가 있습니다. 

지원 되는 하드웨어 플랫폼에 대 한 자세한 내용은 참조 하세요. [Soc 및 사용자 지정 보드](https://docs.microsoft.com/en-us/windows/iot-core/learn-about-hardware/socsandcustomboards)합니다. 

### <a name="trusted-platform-module"></a>신뢰할 수 있는 플랫폼 모듈
IoT Core는 하드웨어 보안 플랫폼으로 신뢰할 수 있는 플랫폼 모듈 2.0 (TPM 2.0)를 사용합니다. Oem은 BitLocker, 보안 부팅, Azure 자격 증명 저장소 등과 같은 IoT 핵심 보안 기능을 최대한 활용할 수 있도록 TPM 2.0을 제공 하는 하드웨어 플랫폼을 사용 하는 것이 좋습니다. 프로덕션 장치의 TPM을 구현 하는 방법은 두 가지가: (dTPM) 별도 TPM 또는 TPM (fTPM) 펌웨어. 불연속 Tpm Infineon, NazionZ, 등과 같은 여러 제조업체에서 제공 됩니다. 일부 SoC 제조업체 보드 지원 패키지 (BSP)의 일부로 fTPM 구현을 제공합니다. 

Tpm에 대 한 자세한 내용은 참조 하세요. [TPM 개요](https://docs.microsoft.com/en-us/windows/iot-core/secure-your-device/tpm) 하 고 [TPM을 설정 하는 방법을](https://docs.microsoft.com/en-us/windows/iot-core/secure-your-device/setuptpm)합니다.

### <a name="storage-options"></a>스토리지 옵션
인기 있는 Raspberry Pi 3과 같은 개발 보드, 유연성을 제공 하 고 개발자 이동식 SD 카드를 통해 모든 플랫폼 이미지를 허용 합니다. 대부분의 업계 IoT 장치에 대 한 이러한 유연성 바람직하지 않으며 공격에 대 한 손쉬운 대상이 장치를 만들 수 있습니다. 대신 하드웨어를 디자인할 때에 eMMC 저장소를 사용 하 여 저렴 한 비용을 작고 IoT 장치에 대 한 하는 것이 좋습니다. 포함 된 저장소 크게 더욱 어렵게 장치에서 콘텐츠를 구분 하 고 차례로 데이터 도난 가능성이 또는 장치에 맬웨어 도입을 줄어듭니다.

## <a name="create-a-retail-image"></a>일반 정품 이미지 만들기 
때 [Windows IoT Core 일반 정품 이미지를 만드는](https://docs.microsoft.com/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)원격을 허용 하는 개발자 도구가 없습니다 액세스할 수 있는지 확인 하 고 디버그는 프로덕션 시스템에 있는 이러한 장치의 공격에 노출 시킬 수 있습니다. 와 같은 개발자 도구를 사용 하는 경우 [Windows Device Portal](https://docs.microsoft.com/en-us/windows/iot-core/manage-your-device/remotedisplay)를 [FTP 서버](https://docs.microsoft.com/en-us/windows/iot-core/connect-your-device/ftp)합니다 [SSH](https://docs.microsoft.com/en-us/windows/iot-core/connect-your-device/ssh), 또는 [PowerShell](https://docs.microsoft.com/en-us/windows/iot-core/connect-your-device/powershell) 이미지 중에서 개발, 테스트 하 고 이러한 도구를 포함 하지 않는 시나리오에서는 IoT Core 이미지의 유효성을 검사 해야 합니다.

### <a name="user-accounts"></a>사용자 계정
대부분의 사용자는 관련 개념이 익숙한 *소유권* 휴대폰 및 Pc와 같은 장치의: unboxed에 해당 하는 경우 장치를 개인 설정 및 장치에 액세스 하려면 자격 증명을 설정 하는 것입니다. 소비자 Pc 및 휴대폰와는 달리 IoT 장치 되지 범용 컴퓨팅 장치의 역할도 합니다. 대신 일반적으로 단일 앱, 고정 용도 장치 됩니다. Windows 개발 주기 동안 장치에 원격으로 연결할 수 있는 장치 관리자의 개념을 지 원하는 경우에 산업 IoT 장치의 이러한 지원 약한 암호를 사용 하는 경우에 특히는 위협에 발생할 수 있습니다. 일반적으로 기본 계정 또는 암호 없는 IoT Core 장치에서 만들어야 하는 것이 좋습니다.

## <a name="lockdown-a-retail-image"></a>잠금 정품 이미지
범용 컴퓨팅 장치, Pc 등의 사용자는 응용 프로그램을 설치 하 고 요구에 맞게 가장 적합 한 장치를 확인 하려면 보안 기능을 비롯 한 설정을 변경할 수 있습니다. IoT 장치의 대부분은 고정-함수-장치 장치 수명 주기 동안 용도 변경 되지 것입니다. 이러한 소프트웨어 업데이트를 수신 하거나 향상 된 UI 또는 온도 규정에는 스마트 자동 온도 조절기 같은 운영 해당 경계 내에 기능 업데이트를 사용 하도록 설정 합니다. 이 정보를 수만 알려져 있고 신뢰할 수 있는 코드의 실행을 허용 하 여 IoT 장치를 완벽 하 게 잠금에 사용 합니다. Windows 10 IoT Core device Guard는 잠긴 장치에서 알 수 없거나 신뢰할 수 없는 실행 코드를 실행할 수 없음을 확인 하 여 IoT 장치를 보호할 수 있습니다.

Microsoft는 제공 된 [턴키 보안 패키지](https://github.com/ms-iot/security/tree/master/TurnkeySecurity) IoT Core 장치에 대 한 주요 보안 기능의 사용을 용이 하 게 합니다. 이렇게 하면 장치 작성기를 만들 IoT 장치에 완벽 하 게 잠겨 있습니다. 패키지에 도움이 됩니다.

* 지원 되는 IoT 플랫폼 보안 부팅 키 프로 비전 하 고에서 기능을 사용 하도록 설정
* 설치 및 구성의 BitLocker를 사용 하 여 장치 암호화 합니다. 
* 장치 잠금만 서명 된 응용 프로그램 및 드라이버를 실행할 수 있도록를 시작 합니다.

단계별 지침에 설명 되어는 [를 사용 하도록 설정 하는 보안 부팅, BitLocker, 및 Device Guard](https://docs.microsoft.com/en-us/windows/iot-core/secure-your-device/securebootandbitlocker) 섹션입니다.

## <a name="device-production"></a>장치 프로덕션
잠금 이미지 유효성이 검사 되 면 제조에 사용할 수 있습니다. 자세한 내용은 참조 [제조 IoT Core](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/)합니다.
