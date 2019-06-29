---
title: Azure IoT 장치 관리
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Azure IoT 장치 관리 및 Windows IoT를 사용 하 여 장치를 관리 하는 방법에 알아봅니다.
keywords: windows iot, Azure IoT 장치 관리 Azure 장치 관리
ms.openlocfilehash: 51580c2ca4c5bf653428ed83e0d6d53310ae89a3
ms.sourcegitcommit: b00cd20ca22e63b3d0795a1b8fe248963b3c74ed
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67467126"
---
# <a name="azure-iot-device-management"></a>Azure IoT 장치 관리   

연결 된 장치에 있어 원격 장치 관리 시스템 연산자에서 사용 하는 주요 기능 중 하나인 메시지를 표시 합니다. 연산자를를 다시 구성 하 고 소프트웨어 및 장치에 대 한 로컬, 물리적 액세스 권한이 필요 없이 원격으로 장치 매개 변수를 업데이트할 수 있습니다. Windows 10 IoT Core 사용 하 여 Oem 이러한 기능 아웃-기본을 제공 하는 장치를 빌드할 수 있습니다. 다른 Windows 10 버전 뿐만 아니라 Windows 10 IoT Core, 모바일 장치 관리 (MDM)에 기반을 이미 제공 [OMA DM](https://en.wikipedia.org/wiki/OMA_Device_Management)합니다. 이 작업은 주로 SCCM 또는 Intune과 같은 관리 도구를 사용 하 여 엔터프라이즈 솔루션에서 사용 됩니다. 이러한 솔루션은 엔터프라이즈 환경에 배치 하는 장치에 적합 하지만, IoT 솔루션에서 더 다양 한 설정의 과제에 있습니다. 이러한 문제는 간단한 장치 관리를 필요로 하는 IoT 장치에도 표시 됩니다. Microsoft는 이러한 장치의 경우 다음을 제공 합니다. [Azure IoT Hub를 통해 장치 관리](https://docs.microsoft.com/azure/iot-hub/iot-hub-device-management-overview)합니다.    

## <a name="scalable-device-management-with-windows-iot"></a>Windows IoT를 사용 하 여 확장 가능한 장치 관리  

가전, HVAC 시스템이 등과 같은 장치에서 실행 중인 Windows IoT Core를 사용 하 여 사용자 지정 가능한, 연한 가중치 장치 관리 솔루션에 대 한 요구가 있습니다. Microsoft Windows 작성자 edition에서 사용 하도록 설정 [Azure IoT Hub 장치 관리](https://docs.microsoft.com/azure/iot-hub/iot-hub-device-management-overview)합니다. Oem은 사용할 수는 [Windows IoT Azure DM 클라이언트 라이브러리](https://aka.ms/iot-core-azure-dm-client) 해당 Azure IoT hub로 장치 관리 기능을 추가 하려면 장치를 연결 합니다. 표준 Windows 장치 관리 구성 요소를 액세스 하는이 라이브러리는 ([구성 서비스 공급자](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference), CSP).  Oem 이제 SCCM, Intune 및 Azure IoT Hub 장치 관리에 대 한 지원 및 최상의 DM 솔루션에 적합 한 유형을 선택 하려면 고객에 게 최대 유지 하는 장치를 빌드할 수 있습니다.   

![Azure IoT Hub 장치 관리](../media/AzureIoTDM/azureDM.png) 

## <a name="how-does-it-work"></a>어떤 방식으로 작동합니까?    

합니다 [Windows IoT Azure DM 클라이언트 라이브러리](https://aka.ms/iot-core-azure-dm-client) 호스트 응용 프로그램에 연결 되어 있습니다. 호스트 응용 프로그램을 사용 하 여 Azure IoT Hub 연결을 공유 됩니다. 따라서 불필요 한 장치 관리를 사용 하도록 설정 하려면 추가 등록을 수행 합니다. 아래 그림은 Windows IoT Azure DM 클라이언트 라이브러리를 사용 하 여 Azure IoT Hub DM 솔루션 아키텍처를 보여 줍니다.     

![Azure DM 순서도](../media/AzureIoTDM/AzureDM-Architecture.png)    

Microsoft는 CommProxy.exe 및 장치 이미지를 포함 하는 OEM SystemConfigurator.exe의 두 가지 시스템 구성 요소를 제공 합니다. 이러한 구성 요소는 csp에 대 한 액세스를 제공합니다. IoTDMClientLib CSP 인터페이스를 Azure IoT Hub 장치 관리를 통해 사용할 수 있는 함수에 매핑합니다. 또한 예를 들어 표준 시간대 설정 CSP를 사용 하지 않는 DM 함수를 제공 합니다. IoTDMClientLib 오픈 소스 구성 요소로 제공 됩니다. Oem은 DM 기능도 센서 또는 작동기에 대 한 장치의 구성과 같은 관련 된 추가 되도록 확장할 수 있습니다.  

## <a name="device-health-attestation"></a>디바이스 상태 증명    
IoT 장치의 보안 작업에 대 한 장치 준수 및 신뢰할 수 있는 상태로 부팅 되는 경우 평가 하기 위해 반드시 합니다. 사용 하 여 [Windows IoT 장치 상태 증명 DHA ()](https://github.com/ms-iot/iot-core-azure-dm-client/blob/master/docs/device-health-attestation.md) 장치의 보안 상태를 확인 연산자를 통해 필요한 경우 적절 한 수정 작업을 수행 [Azure IoT Hub 장치 관리](https://github.com/ms-iot/iot-core-azure-dm-client/blob/master/README.md)합니다. DHA는 일부 Windows IoT Core Azure 장치 관리 클라이언트입니다. 솔루션에서 DHA 기능을 사용 하려면 Microsoft DHA 서비스에 대 한 액세스가 필요 합니다. 서비스에 대 한 구독을 통해 제공 되는 [Windows 10 IoT Core Services](https://docs.microsoft.com/windows-hardware/manufacture/iot/iotcoreservicesoverview)합니다. 

### <a name="reference"></a>참조   
[Azure iot DM 장치 상태 증명](https://github.com/ms-iot/iot-core-azure-dm-client/blob/master/docs/device-health-attestation.md)  

[장치 상태 증명에 대 한 Azure 리소스 배포](https://github.com/ms-iot/iot-core-azure-dm-client/blob/master/docs/dha-deploy.md#deploy-azure-resources-for-device-health-attestation)  


## <a name="how-to-get-started"></a>시작 하려면 어떻게 하나요?  

Windows IoT Azure DM 클라이언트 라이브러리는 GitHub에서 사용할 수 있습니다. IoTDMClientLib 프로젝트 옆에 있는 샘플도 신속 하 게 시작 합니다. 자세한 내용은 아래 링크를 참조 하세요.    

### <a name="project-github-page"></a>프로젝트 GitHub 페이지 

[Windows IoT Azure DM 클라이언트 라이브러리](https://aka.ms/iot-core-azure-dm-client) GitHub에서 사용할 수 있습니다.  

### <a name="dm-dashboard"></a>DM 대시보드    

[DM 대시보드](https://aka.ms/iot-core-azure-dm-client-dashboard) 장치의 DM 함수를 테스트 하는 응용 프로그램입니다. Azure IoT Hub를 통해 장치에 앱 연결합니다. 앱은 유효성을 검사할 장치의 DM 기능도 사용할 수 있습니다. 이 IoTDMClientLib에 추가 된 모든 타사 DM 함수를 테스트 하려면 확장할 수 있습니다.    

### <a name="dm-background-application"></a>DM 백그라운드 응용 프로그램   

합니다 [DM 백그라운드 응용 프로그램](https://aka.ms/iot-core-azure-dm-client-backgroundapp) 응용 프로그램에서 Azure IoT Hub에 연결 하 고 Windows IoT Core에 백그라운드 앱으로 실행 해야 하는 IoTDMClientLib를 사용할 수 있는 방법을 보여 줍니다.    

### <a name="toaster-application"></a>토스터 응용 프로그램 

합니다 [토스터 응용 프로그램](https://aka.ms/iot-core-azure-dm-client-toasterapp)처럼 위의 장치 관리 백그라운드 앱을 장치에 대 한 Azure DM 기능도 사용 하도록 설정 됩니다. 이 앱이 포그라운드에서 실행 되 고 DM 매개 변수 및 장치 UI 통해 함수에 대 한 액세스를 허용 합니다.   

### <a name="registering-your-device-with-the-azure-device-provision-service-dps"></a>Azure 장치 프로 비전 서비스 (DPS) 사용 하 여 장치를 등록합니다.   

Azure Device Provisioning Service에는 고객이를 자동으로 연결 하 고 프로덕션에 이후 IoT Hub를 사용 하 여 장치를 구성할 수 있습니다. 이 프로세스에 대 한 Device Provisioning Service에 장치 작업에 배치 되는 경우 장치를 안전 하 게 구성할 수 있습니다. 고유 하 고 challengeable 장치 ID를 해야 합니다. Device Provisioning Service는이 목적을 위해 TPM의 공용 인증 키 (EKeyPub)를 사용합니다. DPS에 장치 등록을 EKeyPub 장치에서 수집 될 해야 합니다. 이 단계에 대 한 기본 시간이입니다 (줄의 끝 장치 테스트) 동안 프로덕션 중 그러나 프로세스 에서도 가능 제작 후 필요한 경우.   

Microsoft에서는 Device Provisioning Service 등록 프로세스를 간소화 하기 위해 Limpet 도구를 제공 합니다. 제조 설정에 따라 사용할 수 있는 온라인 연결이 없으면 Limpet를 사용 하 여 Device Provisioning Service를 사용 하 여 직접 장치를 등록할 수 있습니다 또는 Limpet 장치를 사용 하 여 장치의 등록의 뒷부분에 나오는, 오프 라인 EKeyPub을 수집할 수 있습니다. 서비스를 프로 비전 합니다.  

Limpet 사용 하 여 Device Provisioning Service 등록 프로세스에 대 한 자세한 내용은 참조 하세요. 합니다 [Device Provisioning Service에서 장치 등록](https://github.com/ms-iot/azure-dm-client/blob/master/docs/limpet.md#setup-azure-cloud-resources) 섹션을 [Limpet 설명서](https://github.com/ms-iot/azure-dm-client/blob/master/docs/limpet.md)합니다.    

프로젝트 리포지토리: [Limpet 프로젝트 리포지토리](https://github.com/ms-iot/azure-dm-client/)     


라이선스: Limpet은 MIT 오픈 소스 라이선스에 따라 사용이 허가 됩니다.   

