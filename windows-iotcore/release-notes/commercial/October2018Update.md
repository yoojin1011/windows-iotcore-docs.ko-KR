---
title: 2018년 10월 업데이트 - 빌드 17763
ms.date: 10/02/2018
ms.topic: article
description: Windows용 2018년 10월 업데이트의 새로운 기능에 대해 알아봅니다.
keywords: Windows IoT, 2018년 10월 업데이트, 릴리스 정보
ms.openlocfilehash: 5b5b6e45552d099426019626ca52000635e308a5
ms.sourcegitcommit: 34928850d3b1b2fe22a92ebd1d75c01b3d4bf0aa
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/24/2020
ms.locfileid: "75721878"
---
# <a name="october-2018-update-release-notes-for-windows-10-iot"></a>Windows 10 IoT용 2018년 10월 업데이트 릴리스 정보
빌드 번호 17763. 2018년 10월

> [!IMPORTANT]
> [ 2018년 10월 업데이트](https://docs.microsoft.com/windows/iot-core/release-notes/commercial/october2018update)를 사용하는 경우 [10월 업데이트(1월 서비스 팩, 빌드 17763.253 포함)](https://docs.microsoft.com/windows/iot-core/release-notes/commercial/17763) 릴리스를 대신 사용하세요. 2018년 10월 업데이트의 사용자에게 영향을 주는 알려진 문제가 있습니다. 

Windows 10 IoT는 임베디드 또는 전용 디바이스를 개발할 수 있도록 하며, 스마트 디바이스용 Windows 솔루션을 빌드하는 OEM 및 개발자에게 적합합니다.

이 문서에서는 이 Windows 10 IoT 릴리스에 대한 다른 내용과 설명서를 보충하는 정보를 제공합니다.

## <a name="privacy-statement"></a>개인정보취급방침

이 Windows 운영 체제 버전에 대한 개인정보처리방침은 [https://go.microsoft.com/fwlink/?LinkId=521839](https://go.microsoft.com/fwlink/?LinkId=521839)에서 볼 수 있습니다.

## <a name="whats-new-in-october-2018-update"></a>2018년 10월 업데이트의 새로운 기능

_Windows 10 IoT Enterprise 및 Windows 10 IoT Core_
* Windows 10 IoT 2018년 10월 업데이트는 IoT Core 및 IoT Enterprise 모두에 대해 10년간 지원됩니다.
* [Azure IoT Edge](https://docs.microsoft.com/azure/iot-edge/quickstart)는 AI 워크로드, Azure 서비스 및 사용자 지정 논리를 Windows 10 IoT 디바이스에 직접 배포하고 실행하여 클라우드 인텔리전스를 로컬로 제공하는 완전 관리형 서비스입니다.
* [Windows Machine Learning](https://docs.microsoft.com/windows/ai/)을 통해 개발자는 자신의 애플리케이션에서 미리 학습된 기계 학습 모델을 사용할 수 있습니다. 이러한 모델은 일반적으로 클라우드에서 학습되어 에지에서 평가됩니다. Windows 10 IoT를 실행하는 디바이스를 로컬로 평가하면 연결, 대역폭 및 데이터 개인 정보에 대한 문제를 완화할 수 있습니다.  

_Windows 10 IoT Core_
* [Windows 10 IoT Core Services](https://docs.microsoft.com/windows-hardware/manufacture/iot/iotcoreservicesoverview) 구독은 이제 일반 공급됩니다. 이 구독에는 10년간의 OS 지원, [디바이스 업데이트 센터](https://docs.microsoft.com/windows-hardware/service/iot/using-device-update-center)를 통한 업데이트 제어 및 DHA(디바이스 상태 증명)를 포함하여 세 가지 주요 혜택이 제공됩니다.
* 실리콘 다양성에 대해 증가하는 고객 및 파트너의 수요를 충족시키기 위해 Microsoft는 NXP와 긴밀하게 협력하여 NXP i.MX 6, 7 및 8M 시리즈 프로세서에 대한 지원을 Windows 10 IoT Core에 추가했습니다. 
* Qualcomm과 Microsoft는 Windows 10 IoT Enterprise와 Snapdragon 프로세서를 결합하여 전력 소비량이 적은 디바이스를 구축하고 항상 연결되어 있으며, 절전 모드를 즉시 해제하는 솔루션을 만들었습니다. 배터리 수명이 길어 모바일 POS 및 기간 업무 태블릿과 같은 전용 디바이스를 하루 종일 많이 사용할 수 있습니다. 
* [Windows 10 IoT Core 기본 앱](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoredefaultapp)에는 특히 디바이스를 시장에 출시할 때 사용자가 자신의 애플리케이션에 활용할 수 있는 더 많은 기능이 있습니다. 이러한 기능으로 날씨, 수동 입력 기능, 오디오 기능이 있습니다. 
* 상업용 배포를 위해 개방형 소매 디바이스를 최종 사용자가 최종적으로 구성하는 "특정/제한된 설치"(즉, 공장 또는 소매점)에 구축하고 [고객이 WDP에 대한 인증서를 획득하여 WDP에 설치해야 한다는 것을 문서화하고 WDP에서 연결 브라우저와 암호를 변경](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-ssl)하는 경우 이 좁은 상업적 인스턴스에서 WDP를 사용하는 것이 허용됩니다. 이 시나리오의 소매 이미지는 여전히 IOT_TOOLKIT을 포함하지 않고 IOT_WEBBEXTN 패키지를 사용하여 WDP를 가져와야 합니다. 
* Limpet.exe는 이제 [오픈 소스 프로젝트](https://github.com/ms-iot/azure-dm-client)로 사용할 수 있습니다. 더 쉽게 테스트하기 위해 서명되지 않은 미리 빌드된 버전의 Limpet.exe를 사용할 수 있으며 WDP에서 바로 다운로드할 수 있습니다. 이 기능에 대해 [Windows 디바이스 포털 설명서](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal)에서 자세히 알아보세요.  
* RS5를 사용하는 경우 개발자는 이제 대시보드를 사용하여 사용자 지정 FFU를 자신의 디바이스에 플래시할 수 있습니다. 이 작업은 DragonBoard 410C 또는 NXP 중 하나를 사용하여 수행할 수 있습니다. [여기](https://docs.microsoft.com/windows/iot-core/tutorials/quickstarter/devicesetup)서 자세히 알아보고 시작하세요.
* Windows 10 IoT Core는 이제 받아쓰기 모드, Windows 키보드 언어에 대한 전체 레이아웃 세트 등의 기능을 허용하는 Windows 데스크톱 버전과 동일한 터치 키보드 구성 요소를 사용합니다. 또한 이 새로운 업데이트에는 이모티콘, 대부분의 입력 "범위" 및 더 효율적인 다중 언어 지원도 포함됩니다. 이러한 기능을 활용하는 방법에 대해 [여기](https://docs.microsoft.com/windows/iot-core/develop-your-app/onscreenkeyboard)서 알아보세요.
* [사용하지 않을 때는 끄고, 화면을 터치할 때는 켜도록 디바이스를 구성](https://docs.microsoft.com/windows/iot-core/learn-about-hardware/wakeontouch)하는 방법을 알아봅니다.
* Bluetooth A2DP-SINK는 이제 선택적으로 지원되며(예: iPhone과 같은 원격 원본에서 IoT 디바이스로 재생 허용), Bluetooth A2DP-SRC는 이제 선택적 패키지입니다(2018년 4월 릴리스에서 기본적으로 제공되었음). 두 프로필이 모두 있는 경우 및 둘 모두를 지원하는 다른 디바이스와 페어링하는 경우 Bluetooth A2DP-SRC 및 A2DP-SINK 프로필 기본 설정을 제어할 수 있습니다. 
* 의도적으로 Windows 10 IoT Core는 애플리케이션 창 주위에 애플리케이션 프레임을 순서대로 표시하지 않습니다. 즉, 애플리케이션이 전체 화면으로 표시됩니다. 그러나 이 릴리스에서는 개발자가 [제목 표시줄을 구성](https://docs.microsoft.com/windows/iot-core/develop-your-app/signindialogtitlebars)하는 옵션을 사용할 수 있습니다.
* 이제 Gpio, I2c, Spi 및 UART와 상호 작용할 수 있는 버스 도구는 [샘플 리포지토리](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/BusTools)에서 사용할 수 있습니다. 이러한 도구는 Windows 10 IoT Core 및 Windows Enterprise를 포함한 모든 Windows 버전에서 실행됩니다. 
* [Windows.System.Update 네임스페이스 API](https://docs.microsoft.com/uwp/api/windows.system.update)를 사용하면 시스템 업데이트에 대한 대화형 제어를 호출할 수 있습니다. 이 네임스페이스는 Windows 10 IoT Core에서만 사용할 수 있습니다.
* Windows 10 IoT 솔루션의 일부로 IoT Central을 사용하려는 경우 이제 Windows 10 IoT Core 디바이스를 준비하여 [Azure IoT Central 애플리케이션에 연결](https://docs.microsoft.com/azure/iot-central/howto-connect-windowsiotcore)할 수 있습니다. 
* Raspberry Pi 3B+ 릴리스(다운로드 가능한 ISO는 [여기](https://go.microsoft.com/fwlink/?LinkID=708576)서 찾을 수 있음)는 기술 미리 보기이며, 현재 릴리스 버전에 대한 타임라인이 없습니다. 더 나은 평가 환경 및 상용 제품을 위해 Raspberry Pi 3B 또는 지원되는 Intel, Qualcomm 또는 NXP SoC가 있는 다른 디바이스를 사용하세요. 

## <a name="iot-enterprise-manufacturing-guide"></a>IoT Enterprise 제조 가이드

* 이제 Windows 10 IoT Enterprise용 새 제조 가이드를 [사용할 수 있습니다](https://docs.microsoft.com/windows-hardware/manufacture/desktop/iot-ent-overview). 

## <a name="improvements-in-assigned-access"></a>할당된 액세스의 향상된 기능 

_Windows 10 IoT Enterprise_

* 키오스크와 디지털 서명은 사용자에게 문제를 광범위하게 표시하는 퍼블릭 위치에 배치되는 경우가 많습니다. 기본 제공 상태 보고를 사용하면 디바이스 관리 시스템에서 문제를 자동으로 인식하고, 디바이스를 다시 시작하거나 서비스 기술자를 파견하는 것과 같은 수정 작업을 실행할 수 있습니다. 
* 배포 및 관리 비용의 절감은 ROI의 핵심 동인입니다. Windows 10 IoT Enterprise에서는 설정 앱의 새 마법사를 통해 키오스크 환경을 구성하고, 다중 앱 키오스크를 관리하고, [키오스크 디바이스에 대한 Microsoft Edge 브라우저 환경](https://docs.microsoft.com/microsoft-edge/deploy/microsoft-edge-kiosk-mode-deploy)을 조정하는 기능이 향상되었습니다.
* 디바이스 작성기는 프로비저닝 패키지, 설정 앱 및 모바일 디바이스 관리 시스템을 사용하여 할당된 액세스를 구성할 수 있는 유연성을 제공하지만 일부 고객에게는 여전히 더 많은 요구 사항이 있습니다. [새로운 할당된 액세스 API 세트를 사용](https://docs.microsoft.com/uwp/api/windows.system.userprofile.assignedaccesssettings)하는 경우 개발자는 이제 할당된 액세스를 자신의 애플리케이션 내에서 프로그래밍 방식으로 구성할 수 있습니다.
* 2018년 10월 릴리스를 사용하는 경우 고객은 자동 시작 환경을 다중 앱에 할당된 액세스 구성의 일부로 지정할 수 있으므로 최종 사용자는 항상 기본 주 앱 환경을 사용할 수 있습니다.
* 디바이스를 켠 순간부터 전원을 끌 때까지 사용자에게 표시되는 내용을 제어할 수 있습니다. 부팅 시 Windows 로고 대신 사용자 고유의 로고를 표시하여 시작하거나, 앱 작동 중단, 시스템 문제 또는 전력 차단이 발생하면 오류 메시지 없이 앱을 자동으로 다시 시작합니다. 
* 디스크 변경 내용을 디스크에 쓰는 대신 메모리에 유지하여 전원 주기 후에 알려진 상태로 돌아가는 "읽기 전용" 디바이스를 빌드하는 UWF(통합 쓰기 필터) 기능을 사용할 수 있습니다. 또한 UWF를 HORM(Hibernate Once, Resume Many) 기능과 결합하여 미리 정의된 세션으로 다시 시작할 수 있습니다. 


## <a name="more-management-support"></a>추가 관리 지원

_Windows 10 IoT Enterprise_
* Azure IoT Hub는 디바이스 및 클라우드 개발자가 강력한 디바이스 관리 솔루션을 빌드할 수 있도록 지원하는 간단한 디바이스 관리 기능 및 확장성 모델을 제공합니다. [Azure IoT 디바이스 관리](https://docs.microsoft.com/windows/iot-core/manage-your-device/azureiotdm)와의 통합은 이제 Windows 10 IoT Core 및 Enterprise 모두에서 사용할 수 있습니다. 

_Windows 10 IoT Core_
* [Microsoft Intune](https://www.microsoft.com/cloud-platform/microsoft-intune)을 디바이스 관리에 사용하는 기업은 이제 Windows 10 IoT Enterprise 디바이스 및 기타 관리 디바이스와 함께 Windows 10 IoT Core 디바이스를 관리할 수 있습니다. 이를 통해 운영자는 동일한 관리 인터페이스 및 컨트롤을 사용하여 Windows 10 IoT 디바이스를 일관된 방식으로 관리할 수 있습니다. 


## <a name="windows-10-iot-core-reference-images"></a>Windows 10 IoT Core 참조 이미지
___ 
* Minnowboard Max
  * 프로세서: Intel Atom E3825
  * 아키텍처: x86

* Raspberry Pi 3 모델 B
  * 프로세서: Broadcom BCM2837
  * 아키텍처: ARM

* DragonBoard 410c
  * 프로세서: Qualcomm Snapdragon 410
  * 아키텍처: ARM
  * BSP 버전: 2120.0.0.0


## <a name="known-issues"></a>알려진 문제
* Visual Studio에서 배포하는 F5 드라이버는 Windows 10 IoT Core에서 작동하지 않습니다. 드라이버를 수동으로 복사하여 디바이스에 등록해야 합니다.
* NOOBS를 통해 설치된 디바이스는 커널 디버거를 사용하도록 설정하는 bcdedit 도구를 실행할 수 없습니다.
* Windows IoT 원격 클라이언트가 Raspberry Pi와 함께 작동하지 않습니다. Minnowboard Max 또는 Dragonboard처럼 가속 그래픽을 사용하는 보드를 사용하거나 로컬 표시용 모니터를 연결하세요.
