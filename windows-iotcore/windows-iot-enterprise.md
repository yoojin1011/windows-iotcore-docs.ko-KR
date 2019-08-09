---
title: Windows 10 IoT Enterprise 개요
author: saraclay
ms.author: saclayt
ms.date: 01/18/2018
ms.topic: article
description: Windows 10 IoT Enterprise가 무엇인지와 이를 통해 수행할 수 있는 작업에 대해 알아봅니다.
keywords: Windows 10 IoT Enterprise, Enterprise, 이진, Windows
ms.openlocfilehash: 0d7347e86e3fd3eb6b5b7ad0eccc0825611a9225
ms.sourcegitcommit: c5552007f5456e57512307f51b146406a23fa723
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/02/2019
ms.locfileid: "68739837"
---
# <a name="an-overview-of-windows-10-iot-enterprise"></a>Windows 10 IoT Enterprise 개요

> [!NOTE]
> Windows 컨테이너는 Windows Server, Windows IoT Server, Windows IoT Enterprise 및 Windows IoT Core에서 상업용으로 배포할 수 있습니다.  Windows 10월 업데이트 2018(빌드 17763)부터 Windows 컨테이너는 Windows Enterprise 및 Professional에서 개발/테스트 용도로만 사용할 수 있습니다.

## <a name="what-is-windows-10-iot-enterprise"></a>Windows 10 IoT Enterprise란?
Windows 10 IoT Enterprise는 IoT 솔루션에 엔터프라이즈 관리 효율성 및 보안을 제공하는 Windows 10의 전체 버전입니다. Windows 10 IoT Enterprise는 전 세계 Windows 에코시스템의 모든 혜택을 공유합니다. Windows 10 IoT Enterprise에 해당하는 이진 파일이기 때문에 클라이언트 PC 및 노트북과 동일한 익숙한 개발 및 관리 도구를 사용할 수 있습니다.  그러나 라이선스 및 배포와 관련하여 데스크톱 버전과 IoT 버전이 다릅니다. Windows 10 IoT Enterprise는 LTSC(장기 서비스 채널) 및 SAC(반기 채널) 옵션을 제공합니다. OEM은 디바이스에 필요한 버전을 선택할 수 있다.

## <a name="getting-started"></a>시작 

Windows 10 IoT Enterprise로 제조 과정을 시작하려면 [이 목록](https://go.microsoft.com/fwlink/?linkid=2094697)의 배포자에게 문의하세요.

또한 [여기](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-10-enterprise)에서 Windows 10 IoT Enterprise 평가판을 사용해 볼 수도 있습니다.

거기에서 [Windows 10 IoT Enterprise 제조 가이드](https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/iot-ent-overview)를 통해 Windows 10 IoT Enterprise로 제조하는 방법을 배울 수 있습니다. 

## <a name="fixed-purpose-devices"></a>고정된 용도 디바이스 

> [!TIP]
> 모든 Windows 10 IoT Enterprise 사용 시나리오에 대한 전체 지침은 사용권 계약을 참조하세요. 이 사용권 계약이 없으면 상용 계약에 대해 작업하는 OEM를 요청합니다. 

Windows는 노트북 및 데스크톱의 운영 체제로 잘 알려져 있으며 전 세계 소비자 및 기업에서 사용됩니다.  잘 알려지지 않은 사실은 수년 동안 Windows가 많은 ATM 머신, POS 터미널, 산업 자동화 시스템, 씬 클라이언트, 의료 기기, 디지털 사이니지, 키오스크 및 기타 고정된 용도 디바이스도 지원해 왔다는 것입니다.  Windows 10 IoT Enterprise를 사용하면 사용권 계약에서 특정 허용 범위와 제한 사항이 있는 고정 용도 디바이스를 빌드할 수 있습니다.  

고정 용도 디바이스는 다음과 같은 점에서 범용 디바이스와 다릅니다.  
* 디바이스는 할당된 액세스 또는 셸 시작 관리자 기능을 통해 단일 애플리케이션 또는 고정 애플리케이션 세트에 대해 잠겨 있습니다.  
* 고객이 전원을 켜면 디바이스 경험이 즉시 제공됩니다. 이는 정상적인 Windows 첫 실행 경험을 건너 뛰도록 디바이스 이미지를 구성하면 수행됩니다. 
* 키보드, USB 포트 및 디바이스 정책은 고정된 용도로만 사용하도록 디바이스를 제한하기 위해 잠겨 있습니다.  
* OEM은 하나의 완전한 제품으로서 디바이스에 연결된 소프트웨어와 함께 디바이스의 라이선스를 사용자에게 부여하고 자체 계약의 특정 Windows 사용 약관을 통해 허용됩니다.
* OEM은 운영 체제에서 수행되는 기능을 포함하여 전체 제품에 대한 고객 지원을 제공합니다.

## <a name="long-term-servicing-channel-ltsc"></a>LTSC(장기 서비스 채널)

의료 장비, POS(Point-Of-Sale) 시스템 및 ATM을 제어하는 PC와 같은 특수 시스템은 해당 용도로 인해 종종 더 긴 서비스 옵션이 필요합니다. 일반적으로 이러한 디바이스는 하나의 중요한 작업을 수행하므로 조직의 다른 디바이스와 같이 자주 기능을 업데이트하지 않아도 됩니다. 이러한 디바이스는 UI 변경 사항으로 최신 상태를 유지하는 것보다 최대한 안정되게 보안을 유지하는 것이 더 중요합니다. LTSC 서비스 모델에서는 Windows 10 IoT Enterprise LTSC 디바이스가 일반 기능 업데이트를 받지 못하며 디바이스 보안이 최신 상태를 유지하도록 품질 업데이트만 제공합니다. 따라서 품질 업데이트는 여전히 Windows 10 IoT Enterprise LTSC 클라이언트에 즉시 사용 가능하지만, 고객은 서비스 도구 섹션에 언급된 서비스 도구 중 하나를 사용하여 해당 업데이트를 지연하도록 선택할 수 있습니다.

* [LTSC에 대해 자세히 알아보기](https://docs.microsoft.com/windows/deployment/update/waas-overview#long-term-servicing-channel)

> [!NOTE]
> 긴 수명의 LTSC 릴리스와 10년 동안 특정 릴리스에 유지되는 이점으로 인해 한 LTSC 릴리스에서 다른 릴리스로 이동할 때 고객에게 업그레이드 요금이 부과됩니다.

## <a name="long-term-support-silicon-details"></a>장기 지원 실리콘 세부 정보

Windows 10 IoT Enterprise 2019 릴리스는 LTSC 릴리스가 됩니다. 아래 목록에는 이 릴리스에서 지원될 것으로 예상되는 모든 프로세서가 포함됩니다. 이전 버전의 Windows 10 IoT Enterprise를 사용하려는 경우 프로세서 지원에 대한 세부 정보는 [여기](https://docs.microsoft.com/windows-hardware/design/minimum/windows-processor-requirements#windows-iot-enterprise--embedded-processor-table)에서 확인할 수 있습니다.

> | Windows 10 IoT Enterprise  |
> |-------------|
> | AMD® 6세대 프로세서 시리즈 Ax-8xxx & E 시리즈 Ex-8xxx & FX-870K | 
> | AMD® 7세대 프로세서 시리즈 Ax-9xxx & E 시리즈 Ex-9xxx & FX-9xxx | 
> | AMD® Ryzen™ 3/5/7 1xxx | 
> | AMD® Ryzen™ 3/5/7 2xxx | 
> | AMD® G 시리즈 | 
> | AMD® R 시리즈 | 
> | AMD® V1xxx | 
> | 4세대 Intel® Core™ 프로세서 | 
> | 5세대 Intel® Core™ 프로세서 |
> | 6세대 Intel® Core™ 프로세서 |
> | 7세대 Intel® Core™ 프로세서 |
> | 8세대 Intel® Core™ 프로세서 |
> | Intel® Atom™ 프로세서 E3900 시리즈 |
> | Intel® Atom™ x5-E8000 프로세서 |
> | Intel® Atom™ x5-Z8350 프로세서 |
> | Intel® Atom™ 프로세서 E3800 제품군 |
> | Intel® Pentium® 및 Celeron® 프로세서 N 및 J 시리즈 |

## <a name="helpful-resources"></a>유용한 리소스
> [!NOTE]
> Windows EPKEA OEM 정품 인증을 설명하고 제조 준비가 완료된 Windows IoT Enterprise [WIM](https://msdn.microsoft.com/library/windows/desktop/dd861280.aspx) 디바이스 이미지 생성 시 지침을 제공하기 위해 배포자의 추가 리소스를 사용할 수 있습니다.

* [엔터프라이즈 데스크톱의 사용자 지정](https://docs.microsoft.com/windows-hardware/customize/enterprise/enterprise-custom-portal)
* [Windows 10용 통합 쓰기 필터](https://docs.microsoft.com/windows-hardware/customize/enterprise/unified-write-filter)
* [Enterprise 및 Pro에 대해 할당된 액세스](https://docs.microsoft.com/windows-hardware/customize/enterprise/assigned-access)
* [Enterprise 및 Education 버전용 셸 시작 관리자](https://docs.microsoft.com/windows-hardware/customize/enterprise/shell-launcher)
* [잠금 리소스](https://docs.microsoft.com/windows-hardware/customize/enterprise/create-a-kiosk-image) 
* [Windows IoT Enterprise에서 포함 모드 활성화 및 백그라운드 작업 사용](https://docs.microsoft.com/windows/iot-core/develop-your-app/embeddedmode)
* [조직에서 Windows 원격 분석 구성](https://docs.microsoft.com/windows/configuration/configure-windows-telemetry-in-your-organization )
* [Windows 데스크톱 버전을 실행하는 키오스크 및 공유 디바이스 구성](https://docs.microsoft.com/windows/configuration/kiosk-shared-pc)
* [데스크톱 제조](https://docs.microsoft.com/windows-hardware/manufacture/desktop/)
