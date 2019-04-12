---
title: 2018 년 10 월 업데이트-17763 빌드
author: saraclay
ms.author: saclayt
ms.date: 10/02/2018
ms.topic: article
description: 2018 년 10 월 업데이트에 대 한 Windows의 새로운 기능에 대해 알아봅니다.
keywords: Windows IoT, 2018 년 10 월 업데이트, 릴리스 정보
ms.openlocfilehash: 886f86a733f53632dee73d0af7b2c172693bc3a5
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59515254"
---
# <a name="october-2018-update-release-notes-for-windows-10-iot"></a>Windows 10 IoT 용 2018 년 10 월 업데이트 릴리스 정보
빌드 번호 17763입니다. 2018년 10월

> [!IMPORTANT]
> 사용 중인 경우는 [2018 년 10 월 업데이트](https://docs.microsoft.com/en-us/windows/iot-core/release-notes/commercial/october2018update)를 사용 하십시오는 [10 월 업데이트 (사용 하 여 서비스 팩, 빌드 17763.253 년 1 월)](https://docs.microsoft.com/en-us/windows/iot-core/release-notes/commercial/17763) 대신 릴리스 합니다. 알려진 문제가 있습니다 년 10 월 2018의 사용자에 영향을 주는 알게 되었지만 업데이트 합니다. 

Windows 10 IoT 장치 포함 또는 전용 용도의 개발 하며 Oem 및 스마트 장치에 대 한 Windows 솔루션을 빌드하는 개발자에 대 한 선택입니다.

이 문서는 다른 콘텐츠 및 Windows 10 IoT의이 릴리스에 대 한 설명서를 보완 하는 정보를 제공 합니다.

## <a name="privacy-statement"></a>개인정보취급방침

이 버전의 Windows 운영 체제에 대 한 개인정보취급방침 볼 수 있습니다 [ https://go.microsoft.com/fwlink/?LinkId=521839 ](https://go.microsoft.com/fwlink/?LinkId=521839)합니다.

## <a name="whats-new-in-october-2018-update"></a>2018 년 10 월의에서 새로운 기능 업데이트

_Windows 10 IoT Enterprise 및 Windows 10 IoT Core_
* Windows 10 IoT 10 월 2018 업데이트 10 년 동안 IoT Core 및 IoT Enterprise 모두 지원 해야 합니다.
* [Azure IoT Edge](https://docs.microsoft.com/azure/iot-edge/quickstart) 는 완전히 관리 되는 서비스는 클라우드 인텔리전스를 제공 로컬로 배포 하 고 Windows 10 IoT 장치에서 직접 인위적인 (인공 지능) 워크 로드, Azure 서비스 및 사용자 지정 논리를 실행 하 여 합니다.
* [Windows Machine Learning](https://docs.microsoft.com/windows/ai/) 개발자는 미리 학습 된 기계 학습 응용 프로그램에서 모델을 사용할 수 있습니다. 이러한 모델은 일반적으로 지에서 평가할 클라우드에서 학습 합니다. Windows 10 IoT를 실행 하는 장치에서 로컬 평가 연결, 대역폭 및 데이터 개인 정보 보호의 문제를 완화 하는 데 도움이 됩니다.  

_Windows 10 IoT Core K_
* [Windows 10 IoT Core Services](https://docs.microsoft.com/windows-hardware/manufacture/iot/iotcoreservicesoverview) 구독 이제 일반 공급 됩니다. 이 구독에는 10 년 동안 OS 포함 하 여 세 가지 주요 이점을 지원, 사용 하 여 컨트롤을 업데이트 합니다 [Device Update Center](https://docs.microsoft.com/windows-hardware/service/iot/using-device-update-center), 및 상태 증명 DHA (장치).
* 증가 하는 고객 및 실리콘 다양성, Microsoft, NXP와 밀접에서 한 파트너 요구에 맞게 Windows 10 IoT Core NXP 6, 7 및 8 i.MX M 시리즈 프로세서에 대 한 지원을 추가 했습니다. 
* Qualcomm 및 Microsoft Snapdragon 적게 소모 하 고 항상 연결 되어 즉시 절전 모드 해제 여부를 지정 하는 장치를 빌드하는 프로세서를 사용 하 여 Windows 10 IoT Enterprise를 결합 하는 솔루션을 만들었습니다. 긴 배터리 수명에는 전용된 장치를 등 모바일 POS-업무 태블릿의 사용량이 종일 지속 될 수 있습니다. 
* [Windows 10 IoT Core 기본 앱](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoredefaultapp) 에 해당 장치를 시장에 제공 하는 경우에 특히 사용자가 자신의 응용 프로그램에 활용할 수 있는 더 많은 기능이 있습니다. 이러한 기능에는 날씨, 잉크 입력 기능, 오디오 기능이 포함 됩니다. 
* "특정/제한 installation"에 상용 배포에 대 한 열기 소매용 장치를 빌드하는 경우 (예:: factory 또는 소매 저장소)는 최종 사용자가 최종 구성을 수행 하 고 시켜야 하는 고객을 문서 [가져올를 WDP 변경 되 WDP 및 연결 브라우저와 암호에 WDP 및 설치에 대 한 인증서](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-ssl), WDP를 사용 하 여 좁은 상용 인스턴스에서이 허용 됩니다. 이 시나리오에서는 일반 정품 이미지 IOT_TOOLKIT, 아직 포함 하지 않아야 하지만 IOT_WEBBEXTN 패키지 WDP에서 끌어오기를 사용 해야 합니다. 
* Limpet.exe은 이제는 [오픈 소스 프로젝트](https://github.com/ms-iot/azure-dm-client)합니다. 테스트를 보다 쉽게 있도록 Limpet.exe 사용 가능한 서명 되지 않은, 미리 작성 된 버전이 고 WDP에서 바로 다운로드할 수 있습니다. 이 기능에 자세히 알아보려면 합니다 [Windows Device Portal 설명서](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal)합니다.  
* RS5, 개발자는 이제 대시보드를 사용 하 여 장치에 사용자 지정 FFUs 플래시 수 있습니다. DragonBoard 410 C 또는 NXP를 사용 하 여이 수행할 수 있습니다. 자세히 알아보고 시작 하세요 [여기](https://docs.microsoft.com/windows/iot-core/tutorials/quickstarter/devicesetup)합니다.
* Windows 10 IoT Core 이제 받아쓰기 모드, Windows 키보드 언어 레이아웃의 전체 집합 등과 같은 기능에 대 한 허용 하는 Windows 데스크톱 버전으로 동일한 터치 키보드 구성 요소를 사용 합니다. 이 새 업데이트에는 또한 supprt 이모티콘, 가장 입력된 "범위" 및 더 나은 다중 언어 지원에 대 한 합니다. 이러한 기능을 활용 하는 방법을 알아봅니다 [여기](https://docs.microsoft.com/windows/iot-core/develop-your-app/onscreenkeyboard)합니다.
* 에 대해 알아봅니다 하는 방법 [해제 될 수 있도록 장치 구성](https://docs.microsoft.com/windows/iot-core/learn-about-hardware/wakeontouch) 사용에서 없고 사용자가 화면을 터치 하면 켜져 있어야 하는 동안.
* Bluetooth A2DP 싱크는 이제 필요에 따라 지원 (예: 허용 재생 iPhone 같은 원격 원본에서 IoT 장치로) 및 Bluetooth A2DP SRC 선택적 패키지 됩니다 (2018 년 4 월에에서 기본적으로 제공 되었습니다 릴리스). 또한 둘 다 지 원하는 다른 장치를 사용 하 여 연결 하는 경우 두 프로필이 있는 경우 및 Bluetooth A2DP SRC 및 A2DP 싱크 프로필 기본 설정을 제어할 수 있습니다. 
* 기본적으로 Windows 10 IoT Core 응용 프로그램 창의 – 주위를 응용 프로그램 프레임 순서 단어 표시 되지 않음, 응용 프로그램 전체 화면으로 표시 됩니다. 이 릴리스를 사용 하 여 개발자는 옵션이 있지만 [제목 표시줄 구성](https://docs.microsoft.com/windows/iot-core/develop-your-app/signindialogtitlebars)합니다.
* Gpio, I2c, Spi 및 UART 상호 작용할 수 있도록 bus 도구를 사용할 수 있습니다 [샘플 리포지토리에서](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/BusTools)합니다. 이러한 도구는 Windows 10 IoT Core 및 Windows Enterprise를 비롯 한 Windows의 모든 버전에서 실행 됩니다. 
* [Windows.System.Update Namespace API](https://docs.microsoft.com/uwp/api/windows.system.update) 시스템 업데이트의 대화형 컨트롤에 대 한 호출을 사용 하도록 설정 합니다. 이 네임 스페이스는 Windows 10 IoT Core 사용할 수만 있습니다.
* Windows 10 IoT 솔루션의 일부로 IoT Central을 사용 하려는 경우 준비할 수 있습니다 하 고 [Windows 10 IoT Core 장치를 Azure IoT Central 응용 프로그램 연결](https://docs.microsoft.com/azure/iot-central/howto-connect-windowsiotcore)합니다. 
* Raspberry Pi 3B + 릴리스 (다운로드 가능한 ISO를 찾을 수 있습니다 [여기](http://go.microsoft.com/fwlink/?LinkID=708576)) 기술 미리 보기 이며는 현재 릴리스 버전에 대 한 타임 라인이 없습니다. 평가 환경 및 fr 향상에 대 한 모든 상용 제품을 사용 하십시오 Raspberry Pi 3B 또는 기타 장치에 지원 되는 Intel, Qualcomm Soc NXP. 

## <a name="iot-enterprise-manufacturing-guide"></a>Iot 제조 가이드

* Windows 10 IoT Enterprise에 대 한 새 제조 지침 됩니다 [출시](https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/iot-ent-overview)합니다. 

## <a name="improvements-in-assigned-access"></a>할당 된 액세스의 향상 된 기능 

_Windows 10 IoT Enterprise_

* 키오스크 및 디지털 간판은 종종 사람이 문제 광범위 하 게 표시 되는 위치는 공공 장소에 배치 됩니다. 기본 제공 상태 보고를 사용 하 여 장치 관리 시스템은 자동으로 문제를 인식 하 고 장치 다시 시작 또는 서비스 기술자를 디스패치하기와 같은 정정 작업을 실행할 수 있습니다. 
* 배포 및 관리 비용 절감는 ROI의 주요 드라이버입니다. Windows 10 IoT Enterprise에 향상 된 기능, 설정 앱에서 새 마법사를 통해 키오스크 경험을 구성 하 고, 다중 앱 키오스크를 관리 하 고, 조정에 대 한 합니다 [키오스크 장치에 대 한 Microsoft Edge 브라우저 환경을](https://docs.microsoft.com/microsoft-edge/deploy/microsoft-edge-kiosk-mode-deploy)합니다.
* 장치 작성기가 매우 융통성 있게 프로 비전 패키지, 설정 앱 및 모바일 장치 관리 시스템을 사용 하 여 할당 된 액세스를 구성 하는 동안 일부 고객은 여전히 해야 더 합니다. [Api 액세스 할당 된 새 집합을 사용 하 여](https://docs.microsoft.com/uwp/api/windows.system.userprofile.assignedaccesssettings), 개발자는 응용 프로그램에 할당 된 액세스에서 프로그래밍 방식으로 구성할 수 있습니다.
* 2018 년 10 월 릴리스를 사용 하 여 고객에 게 지정할 수는 자동으로 시작 환경을 할당 된 다중-앱 액세스 구성의 일부분으로 있으므로 최종 사용자는 항상 기본 기본 앱 환경이 있습니다.
* 장치가 켜져의 전원이 꺼져 될 때까지 순간부터의 사용자에 게 무엇을 제어할 수 있습니다. 앱 충돌, 시스템 문제 또는 전원 중단 후 부팅 또는 오류 메시지 없이 자동 다시 시작 앱에서 Windows 로고 대신 로고를 표시 하 여 시작 합니다. 
* 디스크 변경 내용이 디스크에 작성 하는 대신 메모리에 보관 하 여 전원 주기 후 알려진 상태로 반환 되는 "읽기 전용" 장치를 만들 쓰기 필터 (UWF (통합) 기능을 사용할 수 있습니다. UWF는 Hibernate Once, 미리 정의 된 세션에 다시 시작 하려면 많은 다시 시작 (HORM) 기능을 사용 하 여 결합할 수도 있습니다. 


## <a name="more-management-support"></a>관리 지원 더 보기

_Windows 10 IoT Enterprise_
* Azure IoT Hub에는 간단한 장치 관리 기능 및 장치 및 클라우드 개발자가 강력한 장치 관리 솔루션을 빌드할 수 있는 확장성 모델을 제공 합니다. 와 통합 [Azure IoT 장치 관리](https://docs.microsoft.com/windows/iot-core/manage-your-device/azureiotdm) Enterprise 및 Windows 10 IoT Core 대 한 출시 되었습니다. 

_Windows 10 IoT Core K_
* 사용 하는 기업 [Microsoft Intune](https://www.microsoft.com/cloud-platform/microsoft-intune) management 해당 장치에 대 한 Windows 10 IoT Enterprise 장치 및 기타 관리 되는 장치와 함께 Windows 10 IoT Core 장치를 관리할 이제 수 있습니다. 이렇게 하면 연산자 일관 된 방식으로 동일한 관리 인터페이스 및 컨트롤을 사용 하는 Windows 10 IoT 장치를 관리할 수 있습니다. 


## <a name="windows-10-iot-core-reference-images"></a>Windows 10 IoT Core 참조 이미지
___ 
* Minnowboard 최대
  * 프로세서: Intel Atom E3825
  * X86 아키텍처:

* Raspberry Pi 3 모델 B
  * 프로세서: Broadcom BCM2837
  * 아키텍처: ARM

* DragonBoard 410 c
  * 프로세서: Qualcomm Snapdragon 410
  * 아키텍처: ARM
  * BSP 버전: 2120.0.0.0


## <a name="known-issues"></a>알려진 문제
* Visual Studio에서 F5 드라이버 배포 Windows 10 IoT Core 작동 하지 않습니다. 드라이버 수동으로 복사 하 고 장치에 등록 합니다.
* NOOBS를 통해 설치 된 장치는 커널 디버거를 사용 하도록 설정 하려면 bcdedit 도구를 실행할 수 없습니다.
* Raspberry Pi에 대 한 Windows IoT 원격 클라이언트 작동 하지 않습니다. 보드를 사용 하 여 가속된 그래픽 Minnowboard 최대 Dragonboard 등을 사용 하 여 또는 로컬 표시에 대 한 모니터를 연결 합니다.
