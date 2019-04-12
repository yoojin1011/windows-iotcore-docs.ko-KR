---
title: 2018 년 4 월 업데이트-빌드 17134
author: saraclay
ms.author: saclayt
ms.date: 05/01/2018
ms.topic: article
description: 무엇에 새로운 2018 년 4 월 업데이트 windows 10 IoT에 알아봅니다.
keywords: Windows IoT, 2018 년 4 월 업데이트, 릴리스 정보
ms.openlocfilehash: b61ee94651c2bea0ec0582669b62867d47c85a0c
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512341"
---
# <a name="april-2018-update-release-notes-for-windows-10-iot"></a>Windows 10 IoT 용 2018 년 4 월 업데이트 릴리스 정보
빌드 17134 번호입니다. 2018년 5월

Windows 10 IoT 장치 포함 또는 전용 용도의 개발 하며 Oem 및 스마트 장치에 대 한 Windows 솔루션을 빌드하는 개발자에 대 한 선택입니다.

이 문서는 다른 콘텐츠 및 Windows 10 IoT의이 릴리스에 대 한 설명서를 보완 하는 정보를 제공 합니다.

## <a name="privacy-statement"></a>개인정보취급방침

이 버전의 Windows 운영 체제에 대 한 개인정보취급방침 볼 수 있습니다 [ https://go.microsoft.com/fwlink/?LinkId=521839 ](https://go.microsoft.com/fwlink/?LinkId=521839)합니다.

## <a name="whats-new-in-april-2018-update"></a>2018 년 4 월의에서 새로운 기능 업데이트
* 합니다 [Visual Studio 테스트 플랫폼](https://blogs.msdn.microsoft.com/devops/2017/02/12/evolving-the-visual-studio-test-platform-part-4-together-in-the-open/) 와 함께 제공 되는 [Visual Studio 15.6 RTW](https://docs.microsoft.com/visualstudio/releasenotes/vs2017-relnotes#Win10_IoT_Core_Testing_Support) 이제 Windows 10 IoT Core 대 한 테스트를 지원 합니다. 때 [단위 테스트 작성](https://blogs.msdn.microsoft.com/devops/2018/03/07/devops-for-iot-with-win10-iot-core-uwp-and-vsts/) Windows 10 IoT Core 대상으로 하는 Visual Studio 2017에서 프로젝트의 경우 개발자가 이제 실행할 수 테스트 장치를 배포 하는 대신 Visual Studio에서 직접 장치에 원격으로 해당 단위 테스트 및 수동으로 실행 합니다.
* 개발자의 기능을 활용할 수 있습니다 합니다 [Windows AI 플랫폼](https://blogs.windows.com/buildingapps/2018/03/07/ai-platform-windows-developers/) 더 지능적인 장치 만들기 및 기계 학습을 가속화 하는 Windows 10 IoT 모델 CPU 또는 GPU를 사용 하 여 평가 합니다.
* Oem 음성 기능을 사용할 장치를 빠르게 시장 출시 기간을 사용 하 여 해당 장치에 Cortana 지원을 통합할 수는 [Cortana 디바이스 SDK의 미리 보기](http://www.aka.ms/cortanadevices)합니다.
* Oem 원격 구성을 수행 하는 Windows에서 사용할 수 있는 Csp의 다양 한 및 크기 조정 사용 하 여 장치 관리를 활용할 수 있습니다 [Azure IoT 장치 관리](https://github.com/ms-iot/iot-core-azure-dm-client)합니다. 이 새 샘플 구현을 로컬 클라이언트, 클라우드 서비스 및 관리 포털에서 클라우드 규모의 장치 관리를 수행 하는 IoT 연산자를 사용 하도록 설정 하면 결합 합니다.
* 이 릴리스를 사용 하 여 작성할 수 있습니다 [UWP 콘솔 앱](https://docs.microsoft.com/windows/uwp/launch-resume/console-uwp) 명령 콘솔 또는 PowerShell 콘솔 호스트에서 실행 되는 합니다. UWP 콘솔 앱을 UWP 앱에서 사용할 수 있는 Win32 Api를 사용할 수도 및 게시 하 고 업데이트할 수 Microsoft Store 통해.
* 새로 추가한 [Miracast 특집 패키지](https://docs.microsoft.com/windows/iot-core/connect-your-device/miracast) 와 함께 IoT Core에 대 한를 [캐스팅 Api 집합이](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/BasicMediaCasting) 장치를 Miracast 전송기 또는 수신기로 작동할 수 있도록 합니다.
* 에 대 한 지원이 추가 되었습니다 합니다 [Bluetooth A2DP SRC](https://docs.microsoft.com/windows/iot-core/connect-your-device/bluetooth) AVRCP 프로필을 사용 하 여 Bluetooth를 통한 원격 제어 기능을 포함 하 여 Bluetooth 스트리밍용 오디오 원본으로 작동 하도록 장치를 허용 하는 프로필입니다.
* 우리의 가장 인기 있는 Qualcomm 보드 DragonBoard 410 c 중 하나에이 릴리스를 사용 하 여 플래시를 훨씬 쉬워졌습니다. 최신 버전을 사용 하 여는 [Windows 10 IoT Core 대시보드](https://docs.microsoft.com/windows/iot-core/connect-your-device/iotdashboard)보드를 연결 하기만 하면, 플래시 모드로 설정 하 고 [플래시 장치](https://developer.microsoft.com/en-us/windows/iot/getstarted/prototype/setupdevice) 대시보드에서 직접.
* 찾고 WiFi 네트워크에 연결 하려면 업데이트 했습니다 합니다 [WiFi 커넥터 샘플](https://github.com/Microsoft/Windows-iotcore-samples/blob/develop/Samples/WiFiConnector/CS) netcmd 명령을 이전에 사용 되지 않는 일치 해야 합니다. 이 샘플에서는 합니다 [WiFiAdapter Api](https://docs.microsoft.com/uwp/api/Windows.Devices.WiFi.WiFiAdapter) 무선 네트워크 연결 및 어댑터를 관리 합니다.
* 거기에 맞는 새 시간 관련 Api 시스템 클록을 자동으로 설정 합니다 [현지 시간](https://docs.microsoft.com/uwp/api/windows.system.datetimesettings.setsystemdatetime) 및 [시간대](https://docs.microsoft.com/uwp/api/windows.system.timezonesettings.autoupdatetimezoneasync#Windows_System_TimeZoneSettings_AutoUpdateTimeZoneAsync_Windows_Foundation_TimeSpan_) 경험 부족을 더욱 간소화 된 만들려면 Oem을 사용 하도록 설정 하면 장치 위치에 따라 합니다.
* 새 언어 Api 사용자 기본 설정에 대 한 [언어](https://docs.microsoft.com/uwp/api/windows.system.userprofile.globalizationpreferences.trysetlanguages#Windows_System_UserProfile_GlobalizationPreferences_TrySetLanguages_Windows_Foundation_Collections_IIterable_System_String__)를 [지역](https://docs.microsoft.com/uwp/api/windows.system.userprofile.globalizationpreferences.trysethomegeographicregion#Windows_System_UserProfile_GlobalizationPreferences_TrySetHomeGeographicRegion_System_String_), 기본 [음성](https://docs.microsoft.com/uwp/api/windows.media.speechrecognition.speechrecognizer.trysetsystemspeechlanguageasync) 언어 및 기본값 [음성](https://docs.microsoft.com/uwp/api/windows.media.speechsynthesis.speechsynthesizer.trysetdefaultvoiceasync)합니다.
* 새 [MTP 특집 패키지](https://github.com/PawelWMS/windows-iotcore-docs/blob/MTP_Optional_Feature_Instructions/windows-iotcore/connect-your-device/MTP.md), (MTP (미디어 전송 프로토콜)를 사용 하 여 USB를 통해 Windows 10 IoT Core 장치에서 파일을 전송할 수 있습니다. 이 있으면 장치의 내부 저장소와 SD 카드에 있는 파일을 포함 합니다.
* 새 게시 했습니다 [GitHub의 샘플](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/Azure/IoTHubClients) 하 고 [Channel 9 비디오](https://channel9.msdn.com/Shows/Internet-of-Things-Show/Connecting-Windows-IoT-Devices-To-IoT-Central) 장치를 Windows 10 IoT를 가져오려는 얼마나 쉬운지 보여 주는 Azure IoT Central을 통합 합니다. 설명에 설명서도 업데이트 했습니다 [장치를 연결 하는 방법을](https://docs.microsoft.com/azure/iot-central/howto-connect-windowsiotcore) Azure IoT Central을 Windows 10 IoT Core 실행 합니다.

## <a name="improvements-in-assigned-access"></a>할당 된 액세스의 향상 된 기능
* 디지털 간판 사용 사례에 대 한 여러 화면에 대 한 지원을 추가 했습니다.
* 등록 상태 페이지는 이제 모든 MDM 구성 할당 된 액세스에 진입 하기 전에 장치에 적용 되도록 하는 기능을 포함 합니다.
* 구성 하 고 기존 UWP 스토어 앱 외에도 셸 시작 관리자를 실행 하는 기능을 추가 했습니다.
* 할당 된 액세스를 사용 하 여 장치를 만들고 자동으로 로그온 계정을 구성 하기 위한 간소화 된 프로세스를 사용 하 여 다시 부팅 한 후 원하는 상태가 자동으로 구성할 수 있습니다.
* 모든 사용자를 지정 하는 대신 다중 사용자 장치에 대 한 아니며 이제 Azure AD 그룹 또는 Active Directory 그룹에 다른 할당 된 액세스 구성을 할당할 수 있습니다.
* 문제 해결을 돕기 위해 할당된 액세스 구성 앱에 문제가 있는 경우 이제 생성된 오류 보고서를 볼 수 있습니다.

## <a name="features-in-preview-for-dev-and-test-scenarios"></a>개발 및 테스트 시나리오에 대 한 미리 보기의 기능
* 장치 업데이트 센터 [Preview] Oem을 전역적으로 해당 앱을 관리 하 고 장치 보안 및 최신 상태로 유지 하기 위해 클라우드에서 운영 체제, 앱, 설정 및 파일에 대 한 업데이트를 푸시할 수 있습니다.
* 호스팅에 대 한 지원을 [Nano Server 컨테이너](https://docs.microsoft.com/virtualization/windowscontainers/about/index) Windows 10 IoT Core 및 Enterprise의 64 비트 버전의 응용 프로그램 및 해당 데이터를 사용 하도록 설정 수 서로 격리 하 고 신속 하 게 이동할 수 개발에서 프로덕션 또는 클라우드로는 가장자리입니다.
* [Preview] Windows 장치 상태 증명 서비스는 하드웨어 기능을 사용 하 고 변조 방지 및 원격 장치 상태 증명을 제공 하기 위해 클라우드 서비스 하드웨어 수준 메트릭을 기반으로 데이터 증명 합니다.
* [Azure IoT Edge](https://azure.microsoft.com/campaigns/iot-edge/) Windows iot [미리 보기]는 것이 가장 좋습니다 어디서 나 응용 프로그램 및 서비스 IoT 데이터에서 작동할 수 있도록 클라우드 및에 지 장치 간에 인텔리전스를 오케스트레이션 하기 위해 IoT 솔루션을 허용 합니다.
* Azure IoT Hub [Device Provisioning Service [Preview]](https://blogs.windows.com/buildingapps/2017/10/05/windows-10-iot-enables-complete-iot-lifecycle/) 제조 하는 동안 공용 이미지를 사용 하 여 만든 되어 검색을 위해 Azure IoT Hub에 처음 부팅 시 자동으로 연결 하도록 Windows 10 IoT 장치를 사용 하도록 설정 장치별 프로 비전 정보입니다.

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

## <a name="additional-information"></a>추가 정보
* Intel 줄 플랫폼 생성 중지를 최근 Intel 발표에 따라 FFUs Intel 줄에 대 한 이전 릴리스에서 중단 되었습니다. Intel 줄을 평가 하는 고객은 대신 식별 해야-다른 중 하나를 사용 하 여 플랫폼 지원 Soc [제안 보드 및 Soc](https://docs.microsoft.com/windows/iot-core/learn-about-hardware/suggestedboards) 목록에 대 한 합니다.

## <a name="known-issues"></a>알려진 문제
* Visual Studio에서 F5 드라이버 배포 Windows 10 IoT Core 작동 하지 않습니다. 드라이버 수동으로 복사 하 고 장치에 등록 합니다.
* NOOBS를 통해 설치 된 장치는 커널 디버거를 사용 하도록 설정 하려면 bcdedit 도구를 실행할 수 없습니다.
* Raspberry Pi에 대 한 Windows IoT 원격 클라이언트 작동 하지 않습니다. 보드를 사용 하 여 가속된 그래픽 Minnowboard 최대 Dragonboard 등을 사용 하 여 또는 로컬 표시에 대 한 모니터를 연결 합니다.
