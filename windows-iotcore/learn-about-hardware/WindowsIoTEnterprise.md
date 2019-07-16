---
title: Windows 10 IoT Enterprise 개요
author: saraclay
ms.author: saclayt
ms.date: 01/18/2017
ms.topic: article
description: Windows 10 IoT Enterprise가 무엇인지와 이를 통해 수행할 수 있는 작업에 대해 알아봅니다.
keywords: Windows 10 IoT Enterprise, Enterprise, 이진, Windows
ms.openlocfilehash: 4dd488ece7ae60074de75756272f52f392ebf322
ms.sourcegitcommit: 38de3aad11845248dac393ffc51b18c5596af4c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68155378"
---
# <a name="an-overview-of-windows-10-iot-enterprise"></a>Windows 10 IoT Enterprise 개요

## <a name="what-is-windows-10-iot-enterprise"></a>Windows 10 IoT Enterprise란?
Windows 10 IoT Enterprise는 IoT 솔루션에 엔터프라이즈 관리 효율성 및 보안을 제공하는 Windows 10의 전체 버전입니다. 이 Windows 10 Enterprise 해당 하는 이진 이므로 Windows 10 Enterprise 작동 하는 방법을 이미 알고 있는 경우 해당 지식을 Windows 10 IoT Enterprise에 전송할 수입니다. 그러나 라이선스 및 배포에 있어 데스크톱 버전 및 IoT 버전 달라 집니다. 

## <a name="getting-started"></a>시작하기 
중 하나를 사용 하 여 작업을 포함/i o t 배포자에 연락 하기 전에 권장 [이러한 장치](https://solutionsdirectory.intel.com/solutions-directory/processors/736/processors/766/processors/782/processors/788/processors/869/processors/879/processors/883/processors/888/processors/1053/processors/1058/processors/1103/processors/1107/processors/1110/processors/1117/processors/1133/processors/1135/processors/1139/processors/1141/processors/1175/processors/1192/processors/1344/processors/1348/processors/1349/processors/1371/processors/1392/processors/1729/processors/2284)합니다.  PC 또는 사용 하 여 권장 되는 장치를 로드할 수 있습니다는 [평가판](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-10-enterprise) 프로토타입 제작을 바로 시작 하려면 Windows 10 Enterprise입니다.

를 Windows 10 IoT Enterprise를 사용 하 여 제조에서 과정을 시작 하려면 배포자에서 연락 해야 [이 목록](http://wincom.blob.core.windows.net/documents/Windows_IoT_Distributor_Information.pdf)합니다. 

## <a name="fixed-purpose-devices"></a>고정된 용도 디바이스 

> [!TIP]
> 모든 Windows 10 IoT Enterprise 사용 시나리오에 대한 전체 지침은 사용권 계약을 참조하세요.

Windows 10 IoT Enterprise edition은 씬 클라이언트, ATM 기, 판매 터미널, 산업용 자동화 시스템 등과 같은 고정된 용도 장치를 빌드할 수 있도록 사용이 허가 됩니다.  사용권 계약에 특정와 제한 됩니다. 

일반적 고정된 용도 장치 범용 장치에서 다음과 같이 다릅니다.  
* 디바이스는 할당된 액세스 또는 셸 시작 관리자 기능을 통해 단일 애플리케이션 또는 고정 애플리케이션 세트에 대해 잠겨 있습니다.  
* 장치 전원을에 즉시 최종 고객을 받는 경우 환경이 됩니다. 이는 정상적인 Windows 첫 실행 경험을 건너 뛰도록 디바이스 이미지를 구성하면 수행됩니다.
* 키보드, USB 포트 및 디바이스 정책은 고정된 용도로만 사용하도록 디바이스를 제한하기 위해 잠겨 있습니다.  
* OEM은 하나의 완전한 제품으로서 디바이스에 연결된 소프트웨어와 함께 디바이스의 라이선스를 사용자에게 부여하고 자체 계약의 특정 Windows 사용 약관을 통해 허용됩니다.

## <a name="differences-between-windows-10-iot-core-and-windows-10-iot-enterprise"></a>Windows 10 IoT Core와 Windows 10 IoT Enterprise의 차이점
Windows 10 IoT Core 및 Windows 10 IoT Enterprise는 이름이 유사하지만 제공하는 것과 지원하는 것에 차이점이 있습니다. 다음은 버전 차이를 강조 표시하는 기능 목록입니다.

최소 요구 사항 세부 정보는 [Windows 하드웨어 사이트](https://docs.microsoft.com/windows-hardware/design/minimum/minimum-hardware-requirements-overview)를 방문하세요.

> |             | Windows 10 IoT Core K  |  Windows 10 IoT Enterprise  |
> |-------------|----------|---------|
> | 사용자 환경 | 백그라운드 앱과 서비스 시작 시 실행 중인 단일 UWP 앱. | 고급 잠금 기능이 있는 기존 Windows 셸 |
> | 헤드리스 지원 | 예 | 예 |
> | 앱 아키텍처 지원 | UWP만 | UWP 및 Win32 |
> | Cortana | *Cortana SDK* | 예 |
> | 도메인 가입 | AAD 전용 | AAD 및 기존 도메인 |
> | 관리 | MDM | MDM |
> | 디바이스 보안 기술 | TPM, 보안 부팅, BitLocker, 장치 상태 증명 및 IoT에 대 한 Device Guard | TPM, 보안 부팅, BitLocker, Device Guard, Defender ATP 및 장치 상태 증명 |
> | CPU 아키텍처 지원 | x86, x64, ARM64 및 ARM32 | x86, x64 및 ARM64 |
> | 라이선싱 | 온라인 라이선싱 계약 및 포함된 OEM 계약, 로열티 없음 | 직접 및 간접 포함된 OEM 계약 |
> | 사용 시나리오 | Smart Building, 디지털 간판, IoT 게이트웨이, HMI, 스마트 홈, 착용 식 장치 | 업계 태블릿, POS, 키오스크, 디지털 간판, ATM, 의료 장치, 제조 장치를 씬 클라이언트 |

## <a name="helpful-resources"></a>유용한 리소스
> [!NOTE]
> 추가 리소스는 Windows EPKEA OEM 정품 인증을 설명 하 고 제조 지원 Windows IoT 기업의 생성 지침을 제공 하려면 배포자에서 사용할 수 [WIM](https://msdn.microsoft.com/library/windows/desktop/dd861280.aspx) 장치 이미지입니다.

* [데스크톱 제조](https://docs.microsoft.com/windows-hardware/manufacture/desktop/)
* [Windows 10용 통합 쓰기 필터](https://docs.microsoft.com/windows-hardware/customize/enterprise/unified-write-filter)
* [Enterprise 및 Pro에 대해 할당된 액세스](https://docs.microsoft.com/windows-hardware/customize/enterprise/assigned-access)
* [Enterprise 및 Education 버전용 셸 시작 관리자](https://docs.microsoft.com/windows-hardware/customize/enterprise/shell-launcher)
* [잠금 리소스](https://docs.microsoft.com/windows-hardware/customize/enterprise/create-a-kiosk-image) 
* [Windows IoT Enterprise에서 포함 모드 활성화 및 백그라운드 작업 사용](https://docs.microsoft.com/windows/iot-core/develop-your-app/embeddedmode)
* [조직에서 Windows 원격 분석 구성](https://docs.microsoft.com/windows/configuration/configure-windows-telemetry-in-your-organization )
* [Windows 데스크톱 버전을 실행하는 키오스크 및 공유 디바이스 구성](https://docs.microsoft.com/windows/configuration/kiosk-shared-pc)
