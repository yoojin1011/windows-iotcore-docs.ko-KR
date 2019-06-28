---
title: Azure IoT 장치 에이전트
author: rcheeran
ms.author: rcheeran
ms.date: 06/25/2019
ms.topic: article
description: Azure IoT 장치 에이전트를 사용 하 여 Windows iot 장치를 관리 하는 방법에 알아봅니다.
keywords: windows iot, Azure IoT, Azure 장치 에이전트, 장치 관리, 원격 관리
ms.openlocfilehash: 63c51d6281651e8f80fb3a0bdb350f919301fa69
ms.sourcegitcommit: 8932969dc50805113c330bc2ba6ec9003d067b3c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67412307"
---
# <a name="azure-iot-device-agent"></a>Azure IoT 장치 에이전트

연결 된 장치에 있어 원격 장치 관리 시스템 연산자에서 사용 하는 주요 기능 중 하나인 메시지를 표시 합니다. 연산자를를 다시 구성 하 고 소프트웨어 및 장치에 대 한 로컬, 물리적 액세스 권한이 필요 없이 원격으로 장치 매개 변수를 업데이트할 수 있습니다. Windows 10 IoT Core 사용 하 여 Oem 이러한 기능 아웃-기본을 제공 하는 장치를 빌드할 수 있습니다. 다른 Windows 10 버전 뿐만 아니라 Windows 10 IoT Core, 모바일 장치 관리 (MDM)에 기반을 이미 제공 [OMA DM](https://en.wikipedia.org/wiki/OMA_Device_Management)합니다. 이 작업은 주로 SCCM 또는 Intune과 같은 관리 도구를 사용 하 여 엔터프라이즈 솔루션에서 사용 됩니다. 이러한 솔루션은 엔터프라이즈 환경에 배치 하는 장치에 적합 하지만, IoT 솔루션에서 더 다양 한 설정의 과제에 있습니다. 이러한 문제는 간단한 장치 관리를 필요로 하는 IoT 장치에도 표시 됩니다. Microsoft는 이러한 장치의 경우 다음을 제공 합니다. [Azure IoT Hub를 통해 장치 관리](https://docs.microsoft.com/azure/iot-hub/iot-hub-device-management-overview)합니다.

## <a name="scalable-device-management-with-windows-iot"></a>Windows IoT를 사용 하 여 확장 가능한 장치 관리

가전, HVAC 시스템이 등과 같은 장치에서 실행 중인 Windows IoT Core를 사용 하 여 사용자 지정 가능한, 연한 가중치 장치 관리 솔루션에 대 한 요구가 있습니다. Oem은 사용할 수는 [Azure IoT 장치 에이전트](https://github.com/ms-iot/azure-client-tools/blob/master/docs/device-agent/device-agent.md) 해당 Azure IoT Hub에 장치 관리 기능을 추가 하려면 장치를 연결 합니다. 표준 Windows 장치 관리 구성 요소에 액세스 하 여 원격 장치 관리 기능을 사용 하는이 빌드 준비 오픈 소스 패키지 ([구성 서비스 공급자](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference), CSP).  Oem 이제 SCCM, Intune 및 Azure IoT Hub 장치 관리에 대 한 지원 및 최선의 선택 하는 적합 한 장치 관리 솔루션을 고객에 게 최대 유지 하는 장치를 빌드할 수 있습니다. 

![Azure IoT Hub 장치 관리](../media/AzureIoTDM/azureDM.png)


## <a name="how-does-it-work"></a>어떤 방식으로 작동합니까?

![Azure IoT 장치 에이전트](https://github.com/ms-iot/azure-client-tools/blob/master/docs/device-agent/high-level-e2e.png) 는 [Azure IoT 장치 에이전트](https://aka.ms/iot-core-azure-dm-client) 2 핵심 구성 요소로 구성 됩니다. 장치 프로 비전 Client(DPS) 장치 프로 비전을 자동화합니다. 장치의 등록 키와 DPS ScopeID를 사용 하 여 Azure Device Provisioning Service에 연결합니다. Azure DPS 서비스를 구성 된 IoT Hub에 프로 비전 및 장치에 다시 연결 문자열을 반환 합니다. 장치를 식별 합니다. DPS 클라이언트는 다음 올바른 IoT Hub에 장치를 연결할이 연결 문자열을 사용 합니다.  

장치 관리 클라이언트를 통해 사용 가능 기능을 활용 하 여 원격 관리 기능을 사용 합니다 ([구성 서비스 공급자](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference), CSP) Azure 장치 에이전트의 원격 관리 기능 선택적으로 장치에 포함 하려는 기능을 선택할 수 있도록 플러그 인 아키텍처를 기반으로 합니다. 그 외에, 플러그 인 아키텍처는 확장할 수 있습니다. 필요한 Azure 장치 에이전트에 추가 하는 장치 관리 기능에 대 한 사용자 고유의 플러그 인를 작성할 수 있습니다. 장치 관리 기능을 모든 장치 쌍 또는 모듈 쌍 속성 및 배포 된 모든 Windows IoT 장치에 대 한 투명의 단일 창 관리 방법이 있으므로 명령을 사용 하 여 원격으로 액세스할 수 있습니다. 장치 관리의 전체 목록을 사용할 수 있는 기능 참조 [이](https://github.com/ms-iot/azure-client-tools/blob/master/docs/device-agent/reference.md)

이 외에도 Azure 장치 에이전트는 또한 만듭니다 하 고 장치에서 실행 중인 다른 UWP 응용 프로그램에 대 한 SAS 토큰을 관리 합니다. Azure 장치 에이전트는 장치 쌍 또는 모듈 쌍과 다른 UWP 앱을 프로 비전 하 고 해당 TPM 슬롯은 연결 문자열을 추가할 수 있습니다. UWP 앱 활용 [UWP 브리지] (https://github.com/ms-iot/azure-client-tools/blob/master/docs/device-agent/uwp-bridge.md) 해당 연결을 읽을 수 TPM 슬롯에서 문자열 및 IoT Hub에 연결 하는 사용할 수 있습니다. 

## <a name="how-to-get-started"></a>시작 하려면 어떻게 하나요?

Azure IoT 장치 에이전트를 GitHub에서 사용할 수 있습니다. 프로젝트를 빠르게 시작 하는 샘플도 포함 됩니다. 자세한 내용은 아래 링크를 참조 하세요.

### <a name="project-github-page"></a>프로젝트 GitHub 페이지

[Azure IoT 장치 에이전트](https://github.com/ms-iot/azure-client-tools/blob/master/docs/device-agent/device-agent.md) GitHub에서 사용할 수 있습니다.

## <a name="migrating-from-azure-device-agent-v1-to-v2"></a>Azure 장치 에이전트 V1에서 V2로 마이그레이션
V1 버전의 장치 에이전트를 사용 중인 경우는 V2 버전의 Azure 장치 에이전트를 더 이상 공유 연결 UWP 앱을 사용 하 여 V1 및 V2 간의 한 가지 중요 한 변경이 됩니다. IoT Hub에 향상 된 기능을 사용 하 여 이제 UWP 앱 및 독립 연결 문자열이 있고 여전히 동일한 장치에서 IoT Hub에 연결할 Azure 장치 에이전트입니다. 참조할 [여기](https://github.com/ms-iot/azure-client-tools/blob/master/docs/device-agent/migration-from-old-client.md) 대 한 자세한 내용은 합니다.
Azure 장치 에이전트 V1에 대 한 자세한 내용은 참조 하세요. [여기](https://docs.microsoft.com/en-us/windows/iot-core/manage-your-device/azureiotdm)

## <a name="other-useful-tools"></a>기타 유용한 도구 
### <a name="dm-dashboard"></a>DM 대시보드
[DM 대시보드](https://aka.ms/iot-core-azure-dm-client-dashboard) 장치의 DM 함수를 테스트 하는 응용 프로그램입니다. Azure IoT Hub를 통해 장치에 앱 연결합니다. 앱은 유효성을 검사할 장치의 DM 기능도 사용할 수 있습니다. Azure 장치 에이전트에 추가 된 모든 타사 DM 함수를 테스트 하 고 확장할 수 있습니다.

### <a name="tpm-tool---limpetexe"></a>TPM 도구-Limpet.exe
Azure Device Provisioning Service에는 고객이를 자동으로 연결 하 고 프로덕션에 이후 IoT Hub를 사용 하 여 장치를 구성할 수 있습니다. 이 프로세스에 대 한 Device Provisioning Service에 장치 작업에 배치 되는 경우 장치를 안전 하 게 구성할 수 있습니다. 고유 하 고 challengeable 장치 ID를 해야 합니다. Device Provisioning Service는이 목적을 위해 TPM의 공용 인증 키 (EKeyPub)를 사용합니다. DPS에 장치 등록을 EKeyPub 장치에서 수집 될 해야 합니다. 이 단계에 대 한 기본 시간이입니다 (줄의 끝 장치 테스트) 동안 프로덕션 중 그러나 프로세스 에서도 가능 제작 후 필요한 경우.  

Microsoft에서는 Device Provisioning Service 등록 프로세스를 간소화 하기 위해 Limpet 도구를 제공 합니다. 제조 설정에 따라 사용할 수 있는 온라인 연결이 없으면 Limpet를 사용 하 여 Device Provisioning Service를 사용 하 여 직접 장치를 등록할 수 있습니다 또는 Limpet 장치를 사용 하 여 장치의 등록의 뒷부분에 나오는, 오프 라인 EKeyPub을 수집할 수 있습니다. 서비스를 프로 비전 합니다.

Limpet 사용 하 여 Device Provisioning Service 등록 프로세스에 대 한 자세한 내용은 참조 하세요. 합니다 [Device Provisioning Service에서 장치 등록](https://github.com/ms-iot/azure-dm-client/blob/master/docs/limpet.md#setup-azure-cloud-resources) 섹션을 [Limpet 설명서](https://github.com/ms-iot/azure-dm-client/blob/master/docs/limpet.md)합니다. 

프로젝트 리포지토리: [Limpet 프로젝트 리포지토리] (https://github.com/ms-iot/azure-dm-client/) 

라이선스: Limpet은 MIT 오픈 소스 라이선스에 따라 사용이 허가 됩니다. 

## <a name="device-health-attestation"></a>디바이스 상태 증명
IoT 장치의 보안 작업에 대 한 장치 준수 및 신뢰할 수 있는 상태로 부팅 되는 경우 평가 하기 위해 반드시 합니다. 사용 하 여 [Windows IoT 장치 상태 증명 DHA ()](https://github.com/ms-iot/iot-core-azure-dm-client/blob/master/docs/device-health-attestation.md) 장치의 보안 상태를 확인 연산자를 통해 필요한 경우 적절 한 수정 작업을 수행 [Azure IoT Hub 장치 관리](https://github.com/ms-iot/iot-core-azure-dm-client/blob/master/README.md)합니다. DHA는 일부 Windows IoT Core Azure 장치 관리 클라이언트입니다. 솔루션에서 DHA 기능을 사용 하려면 Microsoft DHA 서비스에 대 한 액세스가 필요 합니다. 서비스에 대 한 구독을 통해 제공 되는 [Windows 10 IoT Core Services](https://docs.microsoft.com/windows-hardware/manufacture/iot/iotcoreservicesoverview)합니다.

### <a name="reference"></a>참조
[Azure iot DM 장치 상태 증명](https://github.com/ms-iot/iot-core-azure-dm-client/blob/master/docs/device-health-attestation.md)

[장치 상태 증명에 대 한 Azure 리소스 배포](https://github.com/ms-iot/iot-core-azure-dm-client/blob/master/docs/dha-deploy.md#deploy-azure-resources-for-device-health-attestation)








### <a name="more-about-the-azure-device-provision-service-dps"></a>Azure 장치 프로 비전 서비스 (DPS)에 대 한 자세한 정보 


  
  

