---
title: Windows 10 IoT Core를 사용 하 여 더 안전한 장치 빌드
author: TorstenStein
ms.author: torstens
ms.date: 08/28/2017
ms.topic: article
description: 보안 부팅, Tpm 구현 등을 사용 하도록 설정 하 여 더 안전한 장치를 빌드하는 방법을 알아봅니다.
keywords: windows iot, 보안, 펌웨어, 보안 부팅, TPM, Bitlocker, 암호화
ms.openlocfilehash: b7340ce168f766eb13e00bfca39619e92a931c30
ms.sourcegitcommit: 2e7e9555fe71ca60b5f41dbf06051a50520a368a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66491718"
---
# <a name="building-more-secure-devices-with-windows-10-iot-core"></a>Windows 10 IoT Core를 사용 하 여 더 안전한 장치 빌드

## <a name="introduction"></a>소개  

Windows 10 IoT Core는 더 작고 리소스가 제한 된 IoT 장치 클래스에서 활용할 수 있는 강력한 엔터프라이즈급 보안 기능을 제공 합니다. 이러한 보안 기능을 제공 하기 위해 이러한 보안 기능을 제공 하기 위해 하드웨어 플랫폼 에서도 이러한 보안 기능을 제공 해야 합니다. 이 문서에서는 적절 한 하드웨어를 선택 하 고 고객에 게 더 안전한 IoT 장치를 빌드, 구성 및 제공 하려는 OEM 장치 빌더 및 보안 인식 담당자를 위한 개략적인 지침을 제공 합니다.
![데이터 보안](../media/SecurityFlowAndCertificates/DataRestExecutionMotion.png)

## <a name="building-a-more-secure-iot-device"></a>더 안전한 IoT 장치 빌드  
IoT Core를 사용 하 여 더 안전한 IoT 장치를 구축 하는 프로세스에는 플랫폼 보안 기능을 지원 하기 위한 하드웨어 선택 및 보안 사용 IoT 장치의 프로덕션이 포함 됩니다.

![장치 빌드 프로세스](../media/SecurityFlowAndCertificates/DeviceBuildProcess.png)


## <a name="choosing-security-enabled-hardware"></a>보안 사용 하드웨어 선택
IoT Core는 고객 데이터를 보호 하기 위해 플랫폼에 기본 제공 되는 보안 기능을 제공 하지만 하드웨어 보안 기능을 사용 하 여 이러한 기능을 완벽 하 게 활용 합니다. 실제로는 메모리를 조작할 수 있고 소프트웨어를 통해서만 제공할 수 있는 트러스트 앵커 또는 변경할 수 없는 장치 id가 없기 때문에 소프트웨어 자체를 보호할 수 없습니다. 하드웨어 기반 보안 (예: 스마트 카드, Tpm (신뢰할 수 있는 플랫폼 모듈) 또는 SoC에 기본 제공 되는 보안 기능)을 제공 하는 방법에는 여러 가지가 있습니다. 

지원 되는 하드웨어 플랫폼에 대 한 자세한 내용은 [soc and custom 보드](https://docs.microsoft.com/en-us/windows/iot-core/learn-about-hardware/socsandcustomboards)를 참조 하세요. 

### <a name="trusted-platform-module"></a>신뢰할 수 있는 플랫폼 모듈
IoT Core는 하드웨어 보안 플랫폼으로 신뢰할 수 있는 플랫폼 모듈 2.0 (TPM 2.0)을 사용 합니다. Oem은 TPM 2.0를 제공 하는 하드웨어 플랫폼을 사용 하 여 BitLocker, 보안 부팅, Azure 자격 증명 저장소 등과 같은 IoT 핵심 보안 기능을 완벽 하 게 활용 하는 것이 좋습니다. TPM을 구현 하는 두 가지 옵션으로는 TPM (개별 TPM (dTPM) 또는 펌웨어 TPM (fTPM))이 있습니다. Broadcomm, NazionZ 등의 여러 제조업체에서 분리 된 Tpm을 사용할 수 있습니다. 일부 SoC 제조업체는 BSP (보드 지원 패키지)의 일부로 fTPM 구현을 제공 합니다. 

Tpm에 대 한 자세한 내용은 [Tpm 개요](https://docs.microsoft.com/en-us/windows/iot-core/secure-your-device/tpm) 및 [tpm을 설정 하는 방법](https://docs.microsoft.com/en-us/windows/iot-core/secure-your-device/setuptpm)을 참조 하세요.

### <a name="storage-options"></a>스토리지 옵션
인기 있는 Raspberry Pi 3과 같은 개발 보드는 유연성을 제공 하므로 개발자는 이동식 SD 카드를 통해 모든 플랫폼을 쉽게 부팅할 수 있습니다. 대부분의 업계 IoT 장치에서 이러한 유연성은 바람직하지 않으며 장치를 공격 대상으로 쉽게 만들 수 있습니다. 대신 하드웨어를 설계할 때 더 작고 저렴 한 IoT 장치에 eMMC 저장소를 사용 하는 것이 좋습니다. 임베디드 저장소를 사용 하면 장치에서 콘텐츠를 분리 하는 것이 훨씬 더 어려워집니다. 그러면 데이터 도난 또는 장치에 대 한 맬웨어 도입의 가능성이 줄어듭니다.

## <a name="create-a-retail-image"></a>소매점 이미지 만들기 
[Windows IoT Core 상용 이미지를 만들](https://docs.microsoft.com/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)때 원격 액세스 및 디버그를 허용 하는 개발자 도구가 프로덕션 시스템에 있는지 확인 합니다. 이러한 도구는 잠재적으로 장치를 공격에 노출 시킬 수 있습니다. 개발 하는 동안 이미지에 [Windows 장치 포털](https://docs.microsoft.com/en-us/windows/iot-core/manage-your-device/remotedisplay), [FTP 서버](https://docs.microsoft.com/en-us/windows/iot-core/connect-your-device/ftp), [SSH](https://docs.microsoft.com/en-us/windows/iot-core/connect-your-device/ssh)또는 [PowerShell](https://docs.microsoft.com/en-us/windows/iot-core/connect-your-device/powershell) 과 같은 개발자 도구를 사용 하는 경우 포함 하지 않는 소매 IoT 핵심 이미지에서 시나리오를 테스트 하 고 유효성을 검사 해야 합니다. 이러한 도구.

### <a name="user-accounts"></a>사용자 계정
대부분의 사용자는 장치를 unboxing 하 고 장치에 액세스 하기 위한 자격 증명을 설정 하는 것과 같은 장치를 개인 설정 하는 것이 중요 합니다. 고객 Pc와 휴대폰과 달리 IoT 장치는 범용 컴퓨팅 장치로 사용 하기 위한 것이 아닙니다. 대신, 일반적으로 단일 앱의 고정 용도 장치입니다. Windows에서는 개발 주기 중에 장치에 원격으로 연결할 수 있는 장치 관리자의 개념을 지원 하지만, 특히 weak 암호를 사용 하는 경우 업계 IoT 장치에 대 한 지원이 위협에 노출 될 수 있습니다. 일반적으로 IoT Core 장치에는 기본 계정이 나 암호를 만들지 않는 것이 좋습니다.

## <a name="lockdown-a-retail-image"></a>소매점 이미지 잠금
Pc와 같은 범용 컴퓨팅 장치에서 사용자는 응용 프로그램을 설치 하 고 보안 기능을 비롯 한 설정을 변경 하 여 장치가 요구에 가장 적합 하 게 만들 수 있습니다. 대부분의 IoT 장치는 고정 기능 장치로, 장치 수명 동안 용도를 변경 하지 않습니다. 소프트웨어 업데이트를 수신 하거나, 스마트 자동 온도 조절기에 대 한 향상 된 UI 또는 온도 규제와 같은 운영 경계 내에서 기능 업데이트를 사용 하도록 설정 합니다. 이 정보는 알려진 코드와 신뢰할 수 있는 코드의 실행만 허용 하 여 IoT 장치를 완전히 잠그는 데 사용할 수 있습니다. Windows 10 IoT Core의 Device Guard는 잠긴 장치에서 알 수 없거나 신뢰할 수 없는 실행 코드를 실행할 수 없도록 하 여 IoT 장치를 보호 하는 데 도움이 될 수 있습니다.

Microsoft는 IoT Core 장치에서 주요 보안 기능을 쉽게 활용할 수 있도록 [턴키 보안 패키지](https://github.com/ms-iot/security/tree/master/TurnkeySecurity) 를 제공 하 고 있습니다. 이렇게 하면 장치 빌더가 완전히 잠긴 IoT 장치를 만들 수 있습니다. 패키지는 다음에 도움이 됩니다.

* 보안 부팅 키를 프로 비전 하 고 지원 되는 IoT 플랫폼에서이 기능을 사용 하도록 설정 합니다.
* BitLocker를 사용 하 여 장치 암호화를 설정 및 구성 합니다. 
* 서명 된 응용 프로그램 및 드라이버만 실행할 수 있도록 장치 잠금을 시작 하는 중입니다.

단계별 지침은 [보안 부팅, BitLocker 및 Device Guard 사용](https://docs.microsoft.com/en-us/windows/iot-core/secure-your-device/securebootandbitlocker) 섹션에 설명 되어 있습니다.

## <a name="device-production"></a>장치 프로덕션
잠금 이미지의 유효성을 검사 한 후에는 제조에 사용할 수 있습니다. 자세한 내용은 [IoT Core 제조](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/)(영문)를 참조 하세요.
