---
title: Fall Creators Update - 빌드 16299
ms.date: 10/12/2017
ms.topic: article
description: Windows 10 IoT용 Fall Creators Update의 새로운 기능에 대해 알아봅니다.
keywords: Windows IoT, Fall Creators Update, 릴리스 정보
ms.openlocfilehash: 35dbe905cfb25613d1225ab8e6d4b8fd636134d9
ms.sourcegitcommit: 34928850d3b1b2fe22a92ebd1d75c01b3d4bf0aa
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/24/2020
ms.locfileid: "72918700"
---
# <a name="fall-creators-update-release-notes-for-windows-10-iot"></a>Windows 10 IoT용 Fall Creators Update 릴리스 정보
빌드 번호 16299. 2017년 10월

Windows 10 IoT는 임베디드 또는 전용 디바이스를 개발할 수 있도록 하며, 스마트 디바이스용 Windows 솔루션을 빌드하는 OEM 및 개발자에게 적합합니다.

이 문서에서는 이 Windows 10 IoT 릴리스에 대한 다른 내용과 설명서를 보충하는 정보를 제공합니다.

이에 대한 최신 빌드와 패키지를 다운로드하려면 [Windows Insider Preview 다운로드 페이지](https://www.microsoft.com/en-us/software-download/windowsiot)를 방문하세요.

## <a name="privacy-statement"></a>개인정보취급방침

이 Windows 운영 체제 버전에 대한 개인정보처리방침은 [https://go.microsoft.com/fwlink/?LinkId=521839](https://go.microsoft.com/fwlink/?LinkId=521839)에서 볼 수 있습니다.

## <a name="whats-new-in-fall-creators-update"></a>Fall Creators Update의 새로운 기능
* [UWP 앱용 .NET](https://msdn.microsoft.com/library/windows/apps/xaml/mt185501.aspx?f=255&mspperror=-2147217396) - C# 또는 Visual Basic을 사용하여 유니버설 Windows 플랫폼 앱을 빌드하는 데 사용할 수 있는 관리되는 형식 세트가 .NET Standard 2.0을 준수하도록 [수천 개의 새로운 API](https://blogs.msdn.microsoft.com/dotnet/2017/08/25/uwp-net-standard-2-0-preview/)로 확장되었습니다.
* 영어(en-US 및 en-GB), 프랑스어(fr-FR 및 fr-CA), 스페인어(es-ES 및 es-MX) 및 중국어 간체(zh-CN)를 포함하여 Windows 10 IoT Core에서 지원하는 언어가 업데이트되었습니다. 여러 언어를 지원하는 FFU를 만들 수 있습니다. 자세한 내용은 [MultiLangSample](https://github.com/ms-iot/iot-adk-addonkit/tree/16299/Source-arm/Products/MultiLangSample) 및 [SingleLangSample](https://github.com/ms-iot/iot-adk-addonkit/tree/16299/Source-arm/Products/SingleLangSample)을 참조하세요.
* Windows 10 IoT Core에서 [응급 관리 서비스](https://technet.microsoft.com/library/cc736319(v=ws.10).aspx)를 지원합니다.
* Windows 10 IoT Core에서 [잉크 지원](https://docs.microsoft.com/windows/uwp/input-and-devices/pen-and-stylus-interactions)이 향상되었습니다. 호환되는 펜 디지타이저를 사용하면 이제 DirectInk API를 형광펜, 연필 및 벡터 기반 잉크에 사용할 수 있습니다. 또한 InkCanvas 및 InkToolbar를 포함하여 UWP용 XAML 잉크 컨트롤이 추가되었습니다. 이에 따라 스텐실(예: 눈금자, 각도기) 및 다중 모드 상호 작용(예: 호환되는 하드웨어에 대한 동시 펜과 터치)이 가능합니다. 스마트 잉크 기능(예: 잉크 인식 및 잉크 분석)은 지원되지 않습니다.
* 커서 스타일, 밝기, 깜박임 속도 및 문자 세트의 사용자 지정을 포함하여 선 표시를 제어하기 위한 지원이 추가되었습니다. 또한 사용자 지정 문자 모양, 트랜잭션 설명자 및 텍스트 스크롤을 위한 움직이는 텍스트 모드에 대한 지원도 추가되었습니다.
* Windows 10 IoT Enterprise의 경우 [Windows.Devices API](https://docs.microsoft.com/windows/uwp/devices-sensors/enable-usermode-access)를 통해 사용자 모드에서 GPIO, I2C, SPI 및 UART와 같은 업계 표준 버스에 액세스할 수 있습니다.
* Windows 10 IoT Enterprise의 기능인 [할당된 액세스](https://docs.microsoft.com/windows/configuration/lock-down-windows-10-to-specific-apps)는 특정 사용자 계정을 하나의 유니버설 Windows 앱만 사용하도록 제한할 수 있습니다. 잠금 환경에서 여러 UWP 및 Win32 앱을 실행하고 클라우드에서 해당 설정을 관리할 수 있도록 할당된 액세스 지원이 확장되었습니다.
* IoTSettings.exe 또는 새 API를 사용하여 시스템 언어를 변경할 수 있습니다. 자세한 내용은 [명령줄 유틸리티](https://docs.microsoft.com/windows/iot-core/develop-your-app/multilang) 및 [언어 지원](https://docs.microsoft.com/windows/iot-core/develop-your-app/multilang) 설명서의 언어 구성 섹션을 참조하세요.
* 부팅 볼륨 모니터를 사용할 수 있도록 Raspberry Pi UEFI로 업데이트됩니다.
* SMSC 네트워크 드라이버가 모든 Windows 10 IoT Core 아키텍처에 추가되었습니다.
* Windows 10 IoT Core에서 [단독 모드 오디오 스트림](https://msdn.microsoft.com/library/windows/desktop/dd370844(v=vs.85).aspx)을 오디오 엔드포인트 디바이스에 사용하도록 설정하였습니다.
* Windows 10 IoT Core에서 시스템 날짜 및 시간을 설정하는 새 API가 WinRT에 추가되었습니다.
* [유니버설 BSP(wm.xml)](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-packages) 지원이 추가되었습니다. 현재 ADK 버전에서 iot-addk-addonkit v4.0을 사용합니다.
* 언어 선택 및 지역화된 레이아웃이 화상 키보드에 추가되었습니다. 자세한 내용은 [화상 키보드 레이아웃](https://docs.microsoft.com/windows/iot-core/develop-your-app/onscreenkeyboardlayouts)을 참조하세요.

## <a name="features-in-preview-for-dev-and-test-scenarios"></a>개발 및 테스트 시나리오 미리 보기의 기능
* 구성 요소 업데이트 서비스[미리 보기]를 사용하면 OEM에서 앱을 전역적으로 관리하고 운영 체제, 앱, 설정 및 파일에 대한 업데이트를 클라우드에서 디바이스로 푸시하여 최신 상태로 안전하게 유지할 수 있습니다.
* Windows 10 IoT Core 및 Enterprise 64비트 버전에서 [Nano 서버 컨테이너](https://docs.microsoft.com/virtualization/windowscontainers/about/index)를 호스팅하도록 지원하여 애플리케이션과 해당 데이터를 서로 격리하고 개발에서 프로덕션 또는 클라우드로 빠르게 이동할 수 있습니다.
* Windows 디바이스 상태 증명[미리 보기] 서비스는 하드웨어 기능 및 클라우드 서비스를 사용하여 하드웨어 수준 메트릭과 증명된 데이터에 따라 디바이스 상태에 대한 변조 교정 및 원격 증명을 제공합니다.
* Windows IoT의 [Azure IoT Edge](https://azure.microsoft.com/campaigns/iot-edge/)[미리 보기]를 사용하면 IoT 솔루션에서 클라우드와 에지 디바이스 간의 인텔리전스를 오케스트레이션하여 애플리케이션과 서비스에서 IoT 데이터에 대한 작업을 가장 적합한 위치에서 수행할 수 있습니다.
* Azure IoT Hub [디바이스 프로비저닝 서비스[미리 보기]](https://blogs.windows.com/buildingapps/2017/10/05/windows-10-iot-enables-complete-iot-lifecycle/)를 사용하면 제조 중에 일반적인 이미지를 사용하여 Windows 10 IoT 디바이스를 만들고, 처음 부팅할 때 자동으로 Azure IoT Hub에 연결하여 디바이스 관련 프로비저닝 정보를 검색하도록 구성할 수 있습니다.
* [Azure IoT 디바이스 관리[미리 보기]](https://docs.microsoft.com/windows/iot-core/manage-your-device/AzureIoTDM)를 사용하면 IoT 운영자가 설치된 애플리케이션, Windows 업데이트, 인증서 및 네트워크 설정과 같은 디바이스 구성을 클라우드에서 원격으로 관리할 수 있습니다.

## <a name="windows-10-iot-core-reference-images"></a>Windows 10 IoT Core 참조 이미지
___ 
* Minnowboard Max
  * 프로세서: Intel Atom E3825
  * 아키텍처: x86
  * BSP 버전: 10.0.4.0
* Raspberry Pi 3
  * 프로세서: Broadcom BCM2837
  * 아키텍처: ARM
  * BSP 버전: 10.0.16248.1001
* DragonBoard 410c
  * 프로세서: Qualcomm Snapdragon 410
  * 아키텍처: ARM
  * BSP 버전: 2112.0.0.0

## <a name="additional-information"></a>추가 정보
* Intel Joule 플랫폼 생산을 중단하겠다는 Intel의 최근 발표에 따라 이 릴리스에서 Intel Joule용 FFU가 중단되었습니다. Intel Joule을 평가하는 고객은 지원되는 다른 SoC 중 하나를 사용하여 대체 플랫폼을 식별해야 합니다. 목록은 [제안된 보드 및 SoC](https://docs.microsoft.com/windows/iot-core/tutorials/quickstarter/prototypeboards)를 참조하세요.
* 이제 IOT_ONBOARDING_APP로 사용할 수 있는 온보딩 기능을 제거하도록 IOT_WEBB_EXTN 기능이 리팩터링되었습니다. 이 업데이트를 사용하면 온보딩 기능이 제거되며, 이 기능을 다시 사용하려면 이 기능을 사용하는 디바이스를 다시 플래시해야 합니다.

## <a name="known-issues"></a>알려진 문제
* Visual Studio에서 배포하는 F5 드라이버는 Windows 10 IoT Core에서 작동하지 않습니다. 드라이버를 수동으로 복사하여 디바이스에 등록해야 합니다.
* Windows IoT 원격 클라이언트가 Raspberry Pi와 함께 작동하지 않습니다. Minnowboard Max 또는 Dragonboard처럼 가속 그래픽을 사용하는 보드를 사용하거나 로컬 표시용 모니터를 연결하세요.
