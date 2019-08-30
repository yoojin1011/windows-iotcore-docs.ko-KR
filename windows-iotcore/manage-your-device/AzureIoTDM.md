---
title: Azure IoT 장치 관리
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Azure IoT 장치 관리 및 Windows IoT를 사용 하 여 장치를 관리 하는 방법에 대해 알아봅니다.
keywords: windows iot, Azure IoT, Azure 장치 관리, 장치 관리
ms.openlocfilehash: 51580c2ca4c5bf653428ed83e0d6d53310ae89a3
ms.sourcegitcommit: b00cd20ca22e63b3d0795a1b8fe248963b3c74ed
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67467126"
---
# <a name="azure-iot-device-management"></a>Azure IoT 장치 관리   

연결 된 장치와 함께 제공 되는 경우 원격 장치 관리는 시스템 운영자가 사용 하는 주요 기능 중 하나입니다. 이를 통해 운영자는 장치에 로컬로 액세스할 필요 없이 장치의 소프트웨어와 매개 변수를 원격으로 다시 구성 하 고 업데이트할 수 있습니다. Windows 10 IoT Core를 사용 하면 Oem은 이러한 기능을 제공 하는 장치를 만들 수 있습니다. Windows 10 IoT Core 및 기타 Windows 10 버전은 이미 [OMA DM](https://en.wikipedia.org/wiki/OMA_Device_Management)을 기반으로 하는 MDM (모바일 장치 관리)을 제공 합니다. 주로 SCCM 또는 Intune과 같은 관리 도구를 사용 하 여 엔터프라이즈 솔루션에서 활용 됩니다. 이러한 솔루션은 엔터프라이즈 설정에 배치 된 장치에 적합 하지만 IoT 솔루션에 표시 되는 다양 한 설정에 문제가 있습니다. 이러한 문제는 경량 장치 관리가 필요한 IoT 장치 에서도 볼 수 있습니다. 이러한 장치에 대해 Microsoft는 [Azure IoT Hub을 통해 장치 관리](https://docs.microsoft.com/azure/iot-hub/iot-hub-device-management-overview)를 제공 합니다.    

## <a name="scalable-device-management-with-windows-iot"></a>Windows IoT를 사용 하 여 확장 가능한 장치 관리  

가정용 어플라이언스, HVAC 시스템 및 기타와 같은 장치에서 실행 되는 Windows IoT Core를 사용 하는 경우 사용자 지정 가능한 경량 장치 관리 솔루션이 필요 합니다. Windows Creator Edition에서 Microsoft는 [Azure IoT Hub 장치 관리](https://docs.microsoft.com/azure/iot-hub/iot-hub-device-management-overview)를 사용 하도록 설정 합니다. Oem은 [Windows Iot AZURE DM 클라이언트 라이브러리](https://aka.ms/iot-core-azure-dm-client) 를 사용 하 여 azure iot hub 연결 장치에 장치 관리 기능을 추가할 수 있습니다. 이 라이브러리는 표준 Windows 장치 관리 구성 요소 ([구성 서비스 공급자](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference), CSP)에 액세스 합니다.  이제 Oem은 장치 관리를 위해 SCCM, Intune 및 Azure IoT Hub를 지 원하는 장치를 빌드하고 고객에 게 가장 적합 한 형식 DM 솔루션을 선택할 수 있습니다.   

![장치 관리 Azure IoT Hub](../media/AzureIoTDM/azureDM.png) 

## <a name="how-does-it-work"></a>어떤 방식으로 작동합니까?    

[Windows IoT AZURE DM 클라이언트 라이브러리](https://aka.ms/iot-core-azure-dm-client) 는 호스트 응용 프로그램에서 연결 됩니다. 호스트 앱과 Azure IoT Hub 연결을 공유 합니다. 따라서 장치 관리를 사용 하도록 추가 등록을 수행 하지 않아도 됩니다. 아래 그림은 Windows IoT Azure DM 클라이언트 라이브러리를 사용 하는 Azure IoT Hub DM 솔루션에 대 한 아키텍처를 보여 줍니다.     

![Azure DM 흐름 차트](../media/AzureIoTDM/AzureDM-Architecture.png)    

Microsoft에서는 OEM이 장치 이미지에 포함 해야 하는 두 가지 시스템 구성 요소인 기능을 제공 합니다. 이러한 구성 요소는 Csp에 대 한 액세스를 제공 합니다. IoTDMClientLib는 Azure IoT Hub 장치 관리에서 사용할 수 있는 함수에 CSP 인터페이스를 매핑합니다. 또한 CSP를 사용 하지 않는 DM 함수도 제공 합니다. 예를 들어 표준 시간대를 설정 합니다. IoTDMClientLib는 오픈 소스 구성 요소로 제공 됩니다. Oem은이를 확장 하 여 센서 또는 작동기 구성과 같은 장치와 관련 된 DM 기능을 추가할 수 있습니다.  

## <a name="device-health-attestation"></a>디바이스 상태 증명    
IoT 장치를 안전 하 게 작동 하려면 장치가 신뢰할 수 있는 호환 상태로 부팅 되는지 평가 하는 것이 중요 합니다. [DHA (Windows IoT 디바이스 상태 증명)](https://github.com/ms-iot/iot-core-azure-dm-client/blob/master/docs/device-health-attestation.md) 운영자는 장치의 보안 상태를 확인 하 고, 필요한 경우 [장치 관리를 Azure IoT Hub](https://github.com/ms-iot/iot-core-azure-dm-client/blob/master/README.md)통해 적절 한 수정 작업을 수행할 수 있습니다. DHA는 Windows IoT Core Azure 장치 관리 클라이언트의 일부입니다. 솔루션에서 DHA 기능을 사용 하려면 Microsoft DHA 서비스에 액세스 해야 합니다. [Windows 10 IoT Core Services](https://docs.microsoft.com/windows-hardware/manufacture/iot/iotcoreservicesoverview)를 통해 서비스에 대 한 구독을 사용할 수 있습니다. 

### <a name="reference"></a>참조   
[Azure IoT DM에 대 한 디바이스 상태 증명](https://github.com/ms-iot/iot-core-azure-dm-client/blob/master/docs/device-health-attestation.md)  

[디바이스 상태 증명에 대 한 Azure 리소스 배포](https://github.com/ms-iot/iot-core-azure-dm-client/blob/master/docs/dha-deploy.md#deploy-azure-resources-for-device-health-attestation)  


## <a name="how-to-get-started"></a>시작 하는 방법  

Windows IoT Azure DM 클라이언트 라이브러리는 GitHub에서 사용할 수 있습니다. IoTDMClientLib 프로젝트 옆에는 신속 하 게 시작 하기 위한 샘플도 포함 되어 있습니다. 자세한 내용은 아래 링크를 참조 하세요.    

### <a name="project-github-page"></a>프로젝트 GitHub 페이지 

[Windows IoT AZURE DM 클라이언트 라이브러리](https://aka.ms/iot-core-azure-dm-client) 는 GitHub에서 사용할 수 있습니다.  

### <a name="dm-dashboard"></a>DM 대시보드    

[Dm 대시보드](https://aka.ms/iot-core-azure-dm-client-dashboard) 는 장치에서 dm 함수를 테스트 하는 응용 프로그램입니다. 앱은 Azure IoT Hub를 통해 장치에 연결 됩니다. 앱을 사용 하 여 장치의 DM 기능을 확인할 수 있습니다. IoTDMClientLib에 추가 된 타사 DM 함수를 테스트 하도록 확장할 수 있습니다.    

### <a name="dm-background-application"></a>DM 백그라운드 응용 프로그램   

[DM 백그라운드 응용 프로그램](https://aka.ms/iot-core-azure-dm-client-backgroundapp) 은 Azure IoT Hub 연결 하 고 Windows IoT Core에서 백그라운드 앱으로 실행 해야 하는 응용 프로그램에서 IoTDMClientLib를 사용 하는 방법을 보여 줍니다.    

### <a name="toaster-application"></a>Toaster 응용 프로그램 

[Toaster 응용 프로그램](https://aka.ms/iot-core-azure-dm-client-toasterapp)은 위의 장치 관리 백그라운드 앱에서 장치에 대 한 Azure DM 기능을 사용 하도록 설정 합니다. 이 앱은 포그라운드로 실행 되며 장치 UI를 통해 DM 매개 변수 및 함수에 대 한 액세스를 허용 합니다.   

### <a name="registering-your-device-with-the-azure-device-provision-service-dps"></a>Azure 장치 프로 비전 서비스 (DPS)를 사용 하 여 장치 등록   

고객은 Azure 장치 프로 비전 서비스를 사용 하 여 장치를 자동으로 연결 하 고 구성 하 여 프로덕션 후에 IoT Hub 수 있습니다. 이 프로세스의 경우 장치 프로 비전 서비스에는 장치가 작동 중일 때 장치를 안전 하 게 구성 하는 데 도움이 되는 고유 하 고 challengeable 장치 ID가 필요 합니다. 장치 프로 비전 서비스는이 목적을 위해 TPM의 EKeyPub (공개 인증 키)를 사용 합니다. DPS에 장치를 등록 하려면 장치에서 EKeyPub을 수집 해야 합니다. 이 단계를 수행 하는 데 소요 되는 시간은 프로덕션 중 (장치에 대 한 종단 간 테스트 중)입니다. 그러나 필요한 경우에도 프로덕션 후에 프로세스를 수행할 수 있습니다.   

Microsoft는 장치 프로 비전 서비스 등록 프로세스를 간소화 하는 Limpet 도구를 제공 합니다. 제조 설정에 따라 온라인 연결을 사용할 수 있는 경우 장치 프로 비전 서비스와 직접 Limpet를 사용 하 여 장치를 등록 하거나, Limpet에서 장치를 사용 하 여 장치를 나중에 오프 라인으로 등록 하기 위해 EKeyPub를 수집할 수 있습니다. 프로 비전 서비스.  

Limpet를 사용 하 여 장치 프로 비전 서비스 등록 프로세스에 대 한 자세한 내용은 [Limpet 설명서](https://github.com/ms-iot/azure-dm-client/blob/master/docs/limpet.md)의 장치 [프로 비전 서비스에 장치 등록](https://github.com/ms-iot/azure-dm-client/blob/master/docs/limpet.md#setup-azure-cloud-resources) 섹션을 참조 하세요.    

프로젝트 리포지토리: [Limpet 프로젝트 리포지토리](https://github.com/ms-iot/azure-dm-client/)     


사용권이 Limpet는 MIT 오픈 소스 라이선스에 따라 사용이 허가 됩니다.   

