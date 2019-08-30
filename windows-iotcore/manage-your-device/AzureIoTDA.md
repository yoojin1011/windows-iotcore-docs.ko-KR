---
title: Azure IoT 장치 에이전트
author: rcheeran
ms.author: rcheeran
ms.date: 06/25/2019
ms.topic: article
description: Windows IoT에서 Azure IoT 장치 에이전트를 사용 하 여 장치를 관리 하는 방법에 대해 알아봅니다.
keywords: windows iot, Azure IoT, Azure 장치 에이전트, 장치 관리, 원격 관리
ms.openlocfilehash: 4f7336cd1c4c2af903c0a74254e1b8e73ff077b9
ms.sourcegitcommit: 823ca02f515a577a2bdc469602a228365cb6ebf8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67467684"
---
# <a name="azure-iot-device-agent"></a>Azure IoT 장치 에이전트

연결 된 장치에서 원격 장치 관리는 시스템 운영자가 필요로 하는 주요 기능 중 하나입니다. 장치에 대 한 로컬 또는 물리적 액세스 없이 운영자가 원격으로 장치에서 속성을 구성 하 고 소프트웨어를 업데이트할 수 있습니다. 가정용 어플라이언스, HVAC 시스템 및 기타와 같은 장치에서 실행 되는 Windows IoT Core 및 Windows IoT Enterprise를 사용 하는 경우 사용자 지정 가능한 경량 장치 관리 솔루션이 필요 합니다. Windows 10 버전은 이미 [OMA DM](https://en.wikipedia.org/wiki/OMA_Device_Management)을 기반으로 하는 MDM (모바일 장치 관리)을 제공 하지만이는 주로 SCCM 또는 Intune과 같은 관리 도구를 사용 하 여 엔터프라이즈 솔루션에서 활용 됩니다. 이러한 솔루션은 엔터프라이즈 설정에 배치 된 장치에 적합 하지만 IoT 솔루션에 표시 되는 다양 한 설정에 문제가 있습니다. IoT 장치에는 어려울 수 있는 간단 하 고 작은 공간 장치 관리 솔루션이 필요 합니다. Microsoft는 또한 [Azure IoT Hub](https://docs.microsoft.com/azure/iot-hub/iot-hub-device-management-overview) 및 해당 [SDK](https://docs.microsoft.com/en-us/azure/iot-hub/iot-hub-devguide-sdks)를 사용 하 여 장치 관리 기능을 제공 합니다. [Azure IoT 장치 에이전트](https://github.com/ms-iot/azure-client-tools/blob/master/docs/device-agent/device-agent.md) 는 모바일 장치 관리에서 사용 되는 것과 동일한 표준 [CSP (구성 서비스 공급자)](https://docs.microsoft.com/en-us/windows/client-management/mdm/configuration-service-provider-reference) 에서 작동 하는 IoT Hub를 통해 클라우드의 장치 관리 기능을 함께 제공 합니다. Oem은 Azure 장치 에이전트를 사용 하 여 코드를 작성 하지 않고도 이러한 장치 관리 기능을 제공 하는 장치를 빌드할 수 있습니다. 

Azure 장치 에이전트는 원격 장치 관리 기능을 사용 하도록 설정 하는 빌드 준비 된 오픈 소스 패키지입니다. Azure 장치 에이전트는 Windows 10 IoT Core 및 Windows 10 IoT Enterprise에서 지원 되며 IoT Hub를 통해 연결 된 장치에서 작동 합니다. 이제 Oem은 장치 관리를 위해 SCCM, Intune 또는 Azure IoT Hub를 지 원하는 장치를 빌드하고 고객에 게 가장 적합 한 장치 관리 솔루션을 선택할 수 있도록 남겨 둘 수 있습니다.   

![장치 관리 Azure IoT Hub](../media/AzureIoTDM/azureDM.png)


## <a name="how-does-it-work"></a>어떤 방식으로 작동합니까?

[Azure IoT 장치 에이전트](https://aka.ms/iot-core-azure-dm-client) 는 두 가지 핵심 구성 요소로 구성 됩니다. 

장치 프로 비전 서비스 클라이언트 (DPS 클라이언트)는 장치 프로 비전을 자동화 합니다. 장치의 등록 키 및 DPS ScopeID를 사용 하 여 Azure 장치 프로 비전 서비스에 연결 합니다. Azure DPS 서비스는 장치를 식별 하 여 구성 된 IoT Hub에서 프로 비전 하 고 장치에 대 한 연결 문자열을 다시 반환 합니다. 그러면 DPS 클라이언트는이 연결 문자열을 사용 하 여 장치를 올바른 IoT Hub에 연결 합니다.  

장치 관리 클라이언트는 [구성 서비스 공급자](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference)(CSP)를 사용 하 여 원격 장치 관리 기능을 사용 하도록 설정 합니다. Azure 장치 에이전트의 원격 관리 기능은 플러그 인 모델을 지원 하며, 필요한 기능 뿐만 아니라 플러그 인 아키텍처가 확장 가능 합니다. 필요한 장치 관리 기능에 대 한 플러그 인을 직접 작성 하 여 Azure 장치 에이전트에 추가할 수 있습니다. 모든 장치 관리 기능은 장치 쌍 또는 모듈 쌍 속성 및 명령을 사용 하 여 원격으로 액세스할 수 있으므로 모든 Windows IoT 장치에 대해 단일 창의 투명 한 관리 방법을 사용할 수 있습니다. 사용 가능한 장치 관리 기능의 전체 목록은 [다음](https://github.com/ms-iot/azure-client-tools/blob/master/docs/device-agent/reference.md) 을 참조 하세요.

이 외에도, Azure 장치 에이전트는 장치에서 실행 되는 다른 UWP 응용 프로그램에 대 한 SAS 토큰을 만들고 관리 합니다. Azure 장치 에이전트는 다른 UWP 앱을 장치 쌍으로 프로 비전 하거나 모듈 쌍으로 프로 비전 하 고 해당 하는 각 TPM 슬롯에 연결 문자열을 추가할 수 있습니다. UWP 앱은 [Uwp 브리지](https://github.com/ms-iot/azure-client-tools/blob/master/docs/device-agent/uwp-bridge.md) 를 활용 하 여 TPM 슬롯에서 연결 문자열을 읽고이를 사용 하 여 IoT Hub에 연결할 수 있습니다. 

## <a name="how-to-get-started"></a>시작 하는 방법

Azure IoT 장치 에이전트는 GitHub에서 사용할 수 있습니다. 프로젝트에는 신속 하 게 시작 하기 위한 샘플도 포함 되어 있습니다. 자세한 내용은 GitHub [리포지토리](https://github.com/ms-iot/azure-client-tools/blob/master/docs/device-agent/device-agent.md) 를 참조 하세요.

## <a name="migrating-from-azure-device-agent-v1-to-v2"></a>Azure 장치 에이전트 V1에서 V2로 마이그레이션
현재 v1 버전의 장치 에이전트를 사용 중인 경우 v 1과 v 2의 중요 한 변경 사항은 V2 버전에서 Azure 장치 에이전트가 더 이상 UWP 앱과의 연결을 공유 하지 않기 때문입니다. IoT Hub에 대 한 향상 된 기능을 통해 UWP 앱과 Azure 장치 에이전트는 모두 독립 된 연결 문자열을 포함 하 고 IoT Hub에서 동일한 장치에 연결할 수 있습니다. 자세한 내용은 [여기](https://github.com/ms-iot/azure-client-tools/blob/master/docs/device-agent/migration-from-old-client.md) 를 참조 하세요.

Azure 장치 에이전트 V1에 대 한 자세한 내용은 [여기](https://docs.microsoft.com/en-us/windows/iot-core/manage-your-device/azureiotdm)를 참조 하세요.

## <a name="other-useful-tools"></a>기타 유용한 도구 
### <a name="dm-mock-portal"></a>DM 모의 포털
[DM 모의 포털](https://github.com/ms-iot/azure-client-tools/blob/master/docs/dm-mock-portal/dm-mock-portal.md) 은 IoT Hub의 자동 장치 관리 기능을 사용 하 여 개별 장치 또는 여러 장치에서 장치 쌍 또는 모듈 쌍 속성을 설정 하는 데 사용할 수 있는 응용 프로그램입니다. 

### <a name="tpm-tool---limpetexe"></a>TPM 도구-Limpet
고객은 Azure 장치 프로 비전 서비스를 사용 하 여 장치를 자동으로 연결 하 고 구성 하 여 프로덕션 후에 IoT Hub 수 있습니다. 이 프로세스의 경우 장치 프로 비전 서비스에는 장치가 작동 중일 때 장치를 안전 하 게 구성 하는 데 도움이 되는 고유 하 고 challengeable 장치 ID가 필요 합니다. 장치 프로 비전 서비스는이 목적을 위해 TPM의 EKeyPub (공개 인증 키)를 사용 합니다. DPS에 장치를 등록 하려면 장치에서 EKeyPub을 수집 해야 합니다. 이 단계를 수행 하는 데 소요 되는 시간은 프로덕션 중 (장치에 대 한 종단 간 테스트 중)입니다. 그러나 필요한 경우에도 프로덕션 후에 프로세스를 수행할 수 있습니다.  

Microsoft는 장치 프로 비전 서비스 등록 프로세스를 간소화 하는 Limpet 도구를 제공 합니다. 제조 설정에 따라 온라인 연결을 사용할 수 있는 경우 장치 프로 비전 서비스와 직접 Limpet를 사용 하 여 장치를 등록 하거나, Limpet에서 장치를 사용 하 여 장치를 나중에 오프 라인으로 등록 하기 위해 EKeyPub를 수집할 수 있습니다. 프로 비전 서비스.

Limpet를 사용 하 여 장치 프로 비전 서비스 등록 프로세스에 대 한 자세한 내용은이 [리포지토리](https://github.com/ms-iot/azure-client-tools/blob/master/docs/limpet/limpet.md)를 참조 하세요.

사용권이 Limpet는 MIT 오픈 소스 라이선스에 따라 사용이 허가 됩니다. 
