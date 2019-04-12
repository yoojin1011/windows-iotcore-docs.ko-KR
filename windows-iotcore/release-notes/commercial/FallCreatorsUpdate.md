---
title: Fall Creators Update-빌드 16299
author: saraclay
ms.author: saclayt
ms.date: 10/12/2017
ms.topic: article
description: Fall Creators Update에 대 한 Windows 10 IoT의 새로운 기능에 대해 알아봅니다.
keywords: Windows IoT, Fall Creators Update 릴리스 정보
ms.openlocfilehash: 00daad18d5519eee9be695105332aced81a1133f
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512334"
---
# <a name="fall-creators-update-release-notes-for-windows-10-iot"></a>Windows 10 IoT 용 fall Creators 업데이트 릴리스 정보
빌드 번호 16299입니다. 2017년 10월

Windows 10 IoT 장치 포함 또는 전용 용도의 개발 하며 Oem 및 스마트 장치에 대 한 Windows 솔루션을 빌드하는 개발자에 대 한 선택입니다.

이 문서는 다른 콘텐츠 및 Windows 10 IoT의이 릴리스에 대 한 설명서를 보완 하는 정보를 제공 합니다.

패키지 뿐만 아니라이 최신 빌드를 다운로드 하려면 알아보려면 합니다 [Windows Insider Preview 다운로드 페이지](https://www.microsoft.com/en-us/software-download/windowsiot)합니다.

## <a name="privacy-statement"></a>개인정보취급방침

이 버전의 Windows 운영 체제에 대 한 개인정보취급방침 볼 수 있습니다 [ https://go.microsoft.com/fwlink/?LinkId=521839 ](https://go.microsoft.com/fwlink/?LinkId=521839)합니다.

## <a name="whats-new-in-fall-creators-update"></a>Fall Creators Update의 새로운 기능
* [UWP 앱 용.NET](https://msdn.microsoft.com/library/windows/apps/xaml/mt185501.aspx?f=255&mspperror=-2147217396)를 사용 하 여 유니버설 Windows 플랫폼 앱을 만드는 데 사용할 수 있는 관리 되는 형식의 집합 C# 또는 Visual Basic을 사용 하 여 보강 되었습니다 [수천 개의 새로운 Api](https://blogs.msdn.microsoft.com/dotnet/2017/08/25/uwp-net-standard-2-0-preview/) .NET Standard 호환 되도록 2.0입니다.
* 영어 (EN-US 및 en GB), 프랑스어 (FR 및 FR-CA), 스페인어 (ES-ES 및 ES-MX) 및 중국어 간체 (ZH-CN)를 포함 하 여 Windows 10 IoT Core 지원 언어를 업데이트 합니다. 있습니다 여러 언어를 지 원하는 FFUs를 만들 수 있습니다-참조 [MultiLangSample](https://github.com/ms-iot/iot-adk-addonkit/tree/16299/Source-arm/Products/MultiLangSample) 하 고 [SingleLangSample](https://github.com/ms-iot/iot-adk-addonkit/tree/16299/Source-arm/Products/SingleLangSample) 자세한 내용은 합니다.
* 에 대 한 지원 [응급 관리 서비스](https://technet.microsoft.com/library/cc736319(v=ws.10).aspx) Windows 10 IoT Core 있습니다.
* 개선 [잉크 지원](https://docs.microsoft.com/windows/uwp/input-and-devices/pen-and-stylus-interactions) Windows 10 IoT Core 있습니다. 호환 펜 디지타이저와 형광펜, 연필 및 잉크 벡터 기반 이제 DirectInk Api를 활용할 수 있습니다. UWP, 등 InkCanvas InkToolbar, 스텐실 눈금자 및 protractors, 동시 펜과 같은 다중 모달 상호 작용 등을 사용 하도록 설정 하 고 호환 되는 하드웨어에서 터치에 대 한 XAML 잉크 컨트롤 추가 했습니다. 잉크 인식 및 잉크 분석 등의 스마트 잉크 기능을 사용 하는 것이 없습니다.
* 줄이 표시 됩니다는 커서 스타일, 밝기, 깜박임 속도 및 문자 집합의 사용자 지정을 포함 하 여 제어 하는 것에 대 한 추가 지원 합니다. 또한 사용자 지정 문자 모양을, 트랜잭션 설명자 및 움직이는 텍스트 모드로 움직이는 텍스트에 대 한 지원을 추가 했습니다.
* Windows 10 IoT Enterprise에서 사용할 수 액세스 GPIO, I2C, SPI, 및 UART와 같은 업계 표준 버스를 통해 사용자 모드에서의 [Windows.Devices Api](https://docs.microsoft.com/windows/uwp/devices-sensors/enable-usermode-access)합니다.
* [액세스 할당](https://docs.microsoft.com/windows/configuration/lock-down-windows-10-to-specific-apps) 수 있는 Windows 10 IoT Enterprise의 기능을 하나의 유니버설 Windows 앱을 사용 하 여 특정 사용자 계정 제한 됩니다. 여러 UWP 실행을 허용 하도록 할당 된 액세스 지원이 확장 되었습니다 및 잠금 기능에서 Win32 앱 환경과 클라우드에서 이러한 설정을 관리 합니다.
* IoTSettings.exe 또는 새로운 Api를 사용 하 여 시스템 언어를 변경할 수 있습니다. 자세한 내용은의 언어 구성 섹션을 참조 합니다 [명령줄 유틸리티](https://docs.microsoft.com/windows/iot-core/develop-your-app/multilang) 및 [언어 지원](https://docs.microsoft.com/windows/iot-core/develop-your-app/multilang) 설명서.
* Raspberry Pi UEFI 부팅 볼륨 모니터링을 사용 하도록 설정 하려면로 업데이트 합니다.
* Windows 10 IoT Core 모든 아키텍처에 SMSC 네트워크 드라이버 추가 합니다.
* 사용 하도록 설정 [배타 모드 오디오 스트림](https://msdn.microsoft.com/library/windows/desktop/dd370844(v=vs.85).aspx) Windows 10 IoT Core 오디오 끝점 장치에 대 한 합니다.
* Windows 10 IoT Core 시스템 날짜 및 시간을 설정 하기 위한 WinRT에서 새로운 Api를 추가 합니다.
* 에 대 한 지원이 추가 되었습니다 [유니버설 BSP (wm.xml)](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-packages)합니다. ADK의 현재 버전을 사용 하 여 iot-adk-addonkit v4.0을 사용 합니다.
* 추가 언어 선택 및 화상 키보드에 지역화 된 레이아웃 합니다. 자세한 내용은 참조 하세요. [화상 키보드 레이아웃](https://docs.microsoft.com/windows/iot-core/develop-your-app/onscreenkeyboardlayouts)합니다.

## <a name="features-in-preview-for-dev-and-test-scenarios"></a>개발 및 테스트 시나리오에 대 한 미리 보기의 기능
* 구성 요소 업데이트 서비스 [Preview] Oem이 전역적으로 해당 앱을 관리 하 고 장치 보안 및 최신 상태로 유지 하기 위해 클라우드에서 운영 체제, 앱, 설정 및 파일에 대 한 업데이트를 푸시할 수 있습니다.
* 호스팅에 대 한 지원을 [Nano Server 컨테이너](https://docs.microsoft.com/virtualization/windowscontainers/about/index) Windows 10 IoT Core 및 Enterprise의 64 비트 버전의 응용 프로그램 및 해당 데이터를 사용 하도록 설정 수 서로 격리 하 고 신속 하 게 이동할 수 개발에서 프로덕션 또는 클라우드로는 가장자리입니다.
* [Preview] Windows 장치 상태 증명 서비스는 하드웨어 기능을 사용 하 고 변조 방지 및 원격 장치 상태 증명을 제공 하기 위해 클라우드 서비스 하드웨어 수준 메트릭을 기반으로 데이터 증명 합니다.
* [Azure IoT Edge](https://azure.microsoft.com/campaigns/iot-edge/) Windows iot [미리 보기]는 것이 가장 좋습니다 어디서 나 응용 프로그램 및 서비스 IoT 데이터에서 작동할 수 있도록 클라우드 및에 지 장치 간에 인텔리전스를 오케스트레이션 하기 위해 IoT 솔루션을 허용 합니다.
* Azure IoT Hub [Device Provisioning Service [Preview]](https://blogs.windows.com/buildingapps/2017/10/05/windows-10-iot-enables-complete-iot-lifecycle/) 제조 하는 동안 공용 이미지를 사용 하 여 만든 되어 검색을 위해 Azure IoT Hub에 처음 부팅 시 자동으로 연결 하도록 Windows 10 IoT 장치를 사용 하도록 설정 장치별 프로 비전 정보입니다.
* [Azure IoT 장치 관리 [Preview]](https://docs.microsoft.com/windows/iot-core/manage-your-device/AzureIoTDM) 장치 구성 설치와 같은 응용 프로그램, Windows 업데이트, 인증서 관리 및 네트워크 설정을 원격으로 클라우드에서 IoT 운영자를 사용 하도록 설정 합니다.

## <a name="windows-10-iot-core-reference-images"></a>Windows 10 IoT Core 참조 이미지
___ 
* Minnowboard 최대
  * 프로세서: Intel Atom E3825
  * X86 아키텍처:
  * BSP 버전: 10.0.4.0
* Raspberry Pi 3
  * 프로세서: Broadcom BCM2837
  * 아키텍처: ARM
  * BSP 버전: 10.0.16248.1001
* DragonBoard 410 c
  * 프로세서: Qualcomm Snapdragon 410
  * 아키텍처: ARM
  * BSP 버전: 2112.0.0.0

## <a name="additional-information"></a>추가 정보
* Intel 줄 플랫폼 생성 중지를 최근 Intel 발표에 따라이 릴리스에서 FFUs Intel 줄에 대 한 중단 됩니다. Intel 줄을 평가 하는 고객은 대신 식별 해야-다른 중 하나를 사용 하 여 플랫폼 지원 Soc [제안 보드 및 Soc](https://docs.microsoft.com/windows/iot-core/tutorials/quickstarter/prototypeboards) 목록에 대 한 합니다.
* 이제 IOT_ONBOARDING_APP으로 사용할 수 있는 온 보 딩 기능을 제거 IOT_WEBB_EXTN 기능 리팩터링 되었습니다. 이 업데이트를 사용 하 여 온 보 딩 기능 제거 되 고이 기능을 사용 하 여 장치는이 기능을 다시 가져올 reflashed 수 해야 합니다.

## <a name="known-issues"></a>알려진 문제
* Visual Studio에서 F5 드라이버 배포 Windows 10 IoT Core 작동 하지 않습니다. 드라이버 수동으로 복사 하 고 장치에 등록 합니다.
* Raspberry Pi에 대 한 Windows IoT 원격 클라이언트 작동 하지 않습니다. 보드를 사용 하 여 가속된 그래픽 Minnowboard 최대 Dragonboard 등을 사용 하 여 또는 로컬 표시에 대 한 모니터를 연결 합니다.
