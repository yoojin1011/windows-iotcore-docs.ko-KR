---
title: 2018 10 월 업데이트-빌드 17763
ms.date: 10/02/2018
ms.topic: article
description: Windows 10 월 2018 업데이트의 새로운 기능에 대해 알아봅니다.
keywords: Windows IoT, 2018 년 10 월 업데이트, 릴리스 정보
ms.openlocfilehash: 30292437da20a577a319fe47b3f5c2647df00382
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918702"
---
# <a name="october-2018-update-release-notes-for-windows-10-iot"></a>10 월 2018 Windows 10 IoT의 업데이트 릴리스 정보
빌드 번호 17763. 2018년 10월

> [!IMPORTANT]
> [10 월 2018 업데이트](https://docs.microsoft.com/en-us/windows/iot-core/release-notes/commercial/october2018update)를 사용 하는 경우 대신 [10 월 업데이트 (서비스 팩 1 월, 빌드 17763.253)](https://docs.microsoft.com/en-us/windows/iot-core/release-notes/commercial/17763) 릴리스를 사용 하세요. 10 월 2018 업데이트의 사용자에 게 영향을 주는 알려진 문제가 있음을 발견 했습니다. 

Windows 10 IoT는 임베디드 또는 전용 용도의 장치를 개발할 수 있도록 하며, 스마트 장치용 Windows 솔루션을 구축 하는 Oem 및 개발자에 게 적합 합니다.

이 문서에서는 Windows 10 IoT의이 릴리스에 대 한 다른 내용과 설명서를 보충 하는 정보를 제공 합니다.

## <a name="privacy-statement"></a>개인정보취급방침

이 버전의 Windows 운영 체제에 대 한 개인 정보 취급 방침은 [https://go.microsoft.com/fwlink/?LinkId=521839](https://go.microsoft.com/fwlink/?LinkId=521839)에서 볼 수 있습니다.

## <a name="whats-new-in-october-2018-update"></a>10 월 2018 업데이트의 새로운 기능

_Windows 10 IoT Enterprise & Windows 10 IoT Core_
* Windows 10 IoT 10 월 2018 업데이트는 IoT Core와 IoT Enterprise 모두에 대해 10 년간 지원 됩니다.
* [Azure IoT Edge](https://docs.microsoft.com/azure/iot-edge/quickstart) 은 Windows 10 IoT 장치에서 직접 AI (AI) 작업, Azure 서비스 및 사용자 지정 논리를 배포 하 고 실행 하 여 클라우드 인텔리전스를 로컬로 제공 하는 완전히 관리 되는 서비스입니다.
* 개발자는 [Windows Machine Learning](https://docs.microsoft.com/windows/ai/) 를 사용 하 여 응용 프로그램에서 미리 학습 된 기계 학습 모델을 사용할 수 있습니다. 이러한 모델은 일반적으로에 지에서 평가 하기 위해 클라우드에서 학습 됩니다. Windows 10 IoT를 실행 하는 장치에 대 한 로컬 평가는 연결, 대역폭 및 데이터 개인 정보의 문제를 완화 하는 데 도움이 됩니다.  

_Windows 10 IoT Core_
* [Windows 10 IoT Core Services](https://docs.microsoft.com/windows-hardware/manufacture/iot/iotcoreservicesoverview) 구독이 이제 일반 공급 됩니다. 이 구독에는 10 년간의 OS 지원, [장치 업데이트 센터](https://docs.microsoft.com/windows-hardware/service/iot/using-device-update-center)를 사용 하 여 업데이트 제어 및 디바이스 상태 증명 (dha)와 같은 세 가지 주요 혜택이 제공 됩니다.
* E다양성에 대 한 증가 하는 고객 및 파트너 수요를 충족 하기 위해 NXP와의 가까운 파트너 관계에 있는 Microsoft는 NXP i.MX 6, 7 및 8M 시리즈 프로세서에 대 한 지원을 Windows 10 IoT Core에 추가 했습니다. 
* Qualcomm 및 Microsoft는 Windows 10 IoT Enterprise와 Snapdragon 프로세서를 결합 하 여 더 적게 사용 되는 장치를 구축 하 고, 항상 연결 되어 있으며 즉시 절전 모드를 해제 하는 솔루션을 만들었습니다. 배터리 수명이 긴 경우 모바일 POS 및 lob (기간 업무) 태블릿과 같은 전용 장치를 사용 하 여 마지막으로 전체를 사용할 수 있습니다. 
* [Windows 10 IoT Core 기본 앱](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoredefaultapp) 에는 사용자가 자신의 응용 프로그램을 위해 사용할 수 있는 기능이 더 많이 있습니다. 특히 장치를 시장으로 가져올 때 사용할 수 있습니다. 이러한 기능에는 날씨, 잉크 기능, 오디오 기능 등이 있습니다. 
* 최종 사용자가 최종 구성을 수행 하 고 고객에 게 [WDP에 대 한 인증서를 얻어야 하는 고객을 문서화 하는 "특정/제한 된 설치" (즉, 공장 또는 소매점)에 대해 상용 배포를 위한 오픈 정품 장치를 구축 하는 경우 그리고 WDP에 설치 하 고 브라우저와 암호를 연결 하면 WDP에서](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-ssl)WDP를 사용할 수 있습니다. 이 시나리오에서 소매점 이미지는 여전히 IOT_TOOLKIT를 포함 하지 않지만 IOT_WEBBEXTN 패키지를 사용 하 여 WDP로 가져와야 합니다. 
* Limpet는 이제 [오픈 소스 프로젝트로](https://github.com/ms-iot/azure-dm-client)사용할 수 있습니다. 테스트를 용이 하 게 하기 위해 서명 되지 않은 미리 작성 된 버전의 Limpet를 사용할 수 있으며 WDP에서 바로 다운로드할 수 있습니다. 이 기능에 대 한 자세한 내용은 [Windows 장치 포털 설명서](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal)를 참조 하세요.  
* 이제 개발자는 대시보드를 사용 하 여 장치에 사용자 지정 FFUs를 RS5 수 있습니다. 이 작업은 DragonBoard 410C 또는 NXP 중 하나로 수행할 수 있습니다. 자세히 알아보고 [여기](https://docs.microsoft.com/windows/iot-core/tutorials/quickstarter/devicesetup)에서 시작 하세요.
* 이제 windows 10 IoT Core는 Windows의 데스크톱 버전과 동일한 터치 키보드 구성 요소를 사용 하 여 받아쓰기 모드, 전체 Windows 키보드 언어 레이아웃 집합과 같은 기능을 사용할 수 있도록 합니다. 이 새로운 업데이트에는 이모티콘, 대부분의 입력 "범위" 및 향상 된 다중 언어 지원에 대 한 지원 prt도 포함 됩니다. [여기](https://docs.microsoft.com/windows/iot-core/develop-your-app/onscreenkeyboard)에서 이러한 기능을 활용 하는 방법을 알아보세요.
* 사용 중이 아닌 상태에서 사용자가 화면에 닿을 때 켤 수 있도록 [장치를 구성](https://docs.microsoft.com/windows/iot-core/learn-about-hardware/wakeontouch) 하는 방법에 대해 알아봅니다.
* Bluetooth A2DP는 이제 선택적으로 지원 됩니다 (예: iPhone에서 IoT 장치로의 원격 원본에서 재생 허용). 이제 Bluetooth A2DP가 선택적 패키지 (4 월 2018 릴리스에서 기본적으로 제공 됨)입니다. 두 프로필이 모두 있고 둘 다를 지 원하는 다른 장치와 페어링 하는 경우 Bluetooth A2DP 및 A2DP 프로필 기본 설정을 제어할 수 있습니다. 
* 기본적으로 Windows 10 IoT Core는 응용 프로그램의 창 주위에 응용 프로그램 프레임을 표시 하지 않습니다. 즉, 응용 프로그램은 전체 화면으로 표시 됩니다. 그러나이 릴리스에서는 개발자에 게 [제목 표시줄을 구성할](https://docs.microsoft.com/windows/iot-core/develop-your-app/signindialogtitlebars)수 있는 옵션이 있습니다.
* 이제 Gpio, I2c, Spi 및 UART와 상호 작용할 수 있는 Bus 도구를 [샘플 리포지토리에서](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/BusTools)사용할 수 있습니다. 이러한 도구는 windows 10 IoT Core 및 Windows Enterprise를 비롯 한 모든 Windows 버전에서 실행 됩니다. 
* [Windows To Update 네임 스페이스 API를](https://docs.microsoft.com/uwp/api/windows.system.update) 사용 하면 시스템 업데이트의 대화형 제어를 호출할 수 있습니다. 이 네임스페이스는 Windows 10 IoT Core에서만 사용할 수 있습니다.
* Windows 10 IoT 솔루션의 일부로 IoT Central를 사용 하려는 경우 이제 [windows 10 Iot Core 장치를 준비 하 고 Azure IoT Central 응용 프로그램에 연결할](https://docs.microsoft.com/azure/iot-central/howto-connect-windowsiotcore)수 있습니다. 
* Raspberry Pi 3B +의 릴리스 (다운로드할 수 있는 ISO는 [여기](http://go.microsoft.com/fwlink/?LinkID=708576)에서 찾을 수 있음)는 technical preview 이며 현재 릴리스 버전에 대 한 타임 라인이 없습니다. 더 나은 평가 환경 및 fr 모든 상용 제품은 Raspberry Pi 3B 또는 지원 되는 Intel, Qualcomm 또는 NXP Soc의 기타 장치를 사용 하세요. 

## <a name="iot-enterprise-manufacturing-guide"></a>IoT Enterprise 제조 가이드

* 이제 Windows 10 IoT Enterprise에 대 한 새 제조 가이드를 [사용할 수](https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/iot-ent-overview)있습니다. 

## <a name="improvements-in-assigned-access"></a>할당 된 액세스의 향상 된 기능 

_Windows 10 IoT Enterprise_

* 키오스크 및 디지털 서명은 종종 사용자에 게 문제가 널리 표시 되는 공개 위치에 배치 됩니다. 기본 제공 상태 보고를 사용 하 여 장치 관리 시스템은 자동으로 문제를 인식 하 고 장치 다시 시작 또는 서비스 기술자 디스패치와 같은 수정 작업을 실행할 수 있습니다. 
* 배포 및 관리 비용 절감은 ROI의 핵심 드라이버입니다. Windows 10 IoT Enterprise는 설정 앱에서 새 마법사를 통해 키오스크 환경을 구성 하 고, 다중 앱 키오스크를 관리 하 고, [키오스크 장치에 대 한 Microsoft Edge 브라우저 환경을](https://docs.microsoft.com/microsoft-edge/deploy/microsoft-edge-kiosk-mode-deploy)구성 하기 위한 향상 된 기능을 제공 합니다.
* 장치 빌더는 프로 비전 패키지, 설정 앱 및 모바일 장치 관리 시스템을 사용 하 여 할당 된 액세스를 구성 하는 뛰어난 유연성을 제공 하지만 일부 고객에 게는 더 많은 요구 사항이 있습니다. 이제 개발자는 [할당 된 액세스 api의 새로운 집합을 사용 하 여](https://docs.microsoft.com/uwp/api/windows.system.userprofile.assignedaccesssettings)응용 프로그램 내에서 할당 된 액세스를 프로그래밍 방식으로 구성할 수 있습니다.
* 10 월 2018 릴리스를 사용 하는 경우 고객은 자동 시작 환경을 앱에 할당 된 액세스 구성의 일부로 지정할 수 있으므로, 최종 사용자는 항상 기본 기본 앱 환경을 사용할 수 있습니다.
* 전원이 꺼질 때까지 장치를 켤 때까지 사용자에 게 표시 되는 내용을 제어할 수 있습니다. 시작-부팅 시 Windows 로고 대신 로고를 표시 하거나 앱 충돌 후 오류 메시지 없이 자동으로 앱을 다시 시작 합니다. 
* UWF (통합 쓰기 필터) 기능을 사용 하면 디스크를 디스크에 기록 하는 대신 메모리에 디스크를 변경 하 여 전원 주기 후에 알려진 상태로 반환 되는 "읽기 전용" 장치를 빌드할 수 있습니다. 또한 UWF를 한 번에 최대 절전 모드로 결합 하 고 여러 (HORM) 기능을 다시 시작 하 여 미리 정의 된 세션으로 다시 시작할 수 있습니다. 


## <a name="more-management-support"></a>추가 관리 지원

_Windows 10 IoT Enterprise_
* Azure IoT Hub는 장치 및 클라우드 개발자가 강력한 장치 관리 솔루션을 빌드할 수 있도록 하는 간단한 장치 관리 기능 및 확장성 모델을 제공 합니다. 이제 Windows 10 IoT Core와 Enterprise 모두에서 [Azure Iot 장치 관리](https://docs.microsoft.com/windows/iot-core/manage-your-device/azureiotdm) 와의 통합을 사용할 수 있습니다. 

_Windows 10 IoT Core_
* 장치 관리에 대 한 [Microsoft Intune](https://www.microsoft.com/cloud-platform/microsoft-intune) 를 사용 하는 기업은 이제 Windows 10 iot Enterprise 장치 및 기타 관리 되는 장치와 함께 Windows 10 iot Core 장치를 관리할 수 있습니다. 이를 통해 운영자는 동일한 관리 인터페이스 및 컨트롤을 사용 하 여 Windows 10 IoT 장치를 일관 된 방식으로 관리할 수 있습니다. 


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
* Visual Studio에서 배포하는 F5 드라이버는 Windows 10 IoT Core에서 작동하지 않습니다. 드라이버를 수동으로 복사 하 여 장치에 등록 해야 합니다.
* NOOBS를 통해 설치된 디바이스는 커널 디버거를 사용하도록 설정하는 bcdedit 도구를 실행할 수 없습니다.
* Windows IoT 원격 클라이언트가 Raspberry Pi와 함께 작동하지 않습니다. Minnowboard Max 또는 Dragonboard처럼 가속 그래픽을 사용하는 보드를 사용하거나 로컬 표시용 모니터를 연결하세요.
