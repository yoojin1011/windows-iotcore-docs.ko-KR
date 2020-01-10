---
title: 4 월 2018 업데이트-빌드 17134
ms.date: 05/01/2018
ms.topic: article
description: Windows 10 IoT 용 4 월 2018 업데이트의 새로운 기능에 대해 알아봅니다.
keywords: Windows IoT, 4 월 2018 업데이트, 릴리스 정보
ms.openlocfilehash: b06378db14ba78fc5a3eb60e842e1555e56a66ac
ms.sourcegitcommit: ea060254f9c4c25afcd0245c897b9e1425321859
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75721756"
---
# <a name="april-2018-update-release-notes-for-windows-10-iot"></a>Windows 10 IoT 용 업데이트 릴리스 정보 4 월 2018
빌드 번호 17134. 2018년 5월

Windows 10 IoT는 임베디드 또는 전용 용도의 장치를 개발할 수 있도록 하며, 스마트 장치용 Windows 솔루션을 구축 하는 Oem 및 개발자에 게 적합 합니다.

이 문서에서는 Windows 10 IoT의이 릴리스에 대 한 다른 내용과 설명서를 보충 하는 정보를 제공 합니다.

## <a name="privacy-statement"></a>개인정보취급방침

이 버전의 Windows 운영 체제에 대 한 개인 정보 취급 방침은 [https://go.microsoft.com/fwlink/?LinkId=521839](https://go.microsoft.com/fwlink/?LinkId=521839)에서 볼 수 있습니다.

## <a name="whats-new-in-april-2018-update"></a>4 월 2018 업데이트의 새로운 기능
* [Visual studio 15.6 RTW](https://docs.microsoft.com/visualstudio/releasenotes/vs2017-relnotes#Win10_IoT_Core_Testing_Support) 와 함께 제공 되는 [Visual studio 테스트 플랫폼](https://blogs.msdn.microsoft.com/devops/2017/02/12/evolving-the-visual-studio-test-platform-part-4-together-in-the-open/) 은 이제 Windows 10 IoT Core에서 테스트를 지원 합니다. Windows 10 IoT Core를 대상으로 하는 Visual Studio 2017에서 프로젝트에 대 한 [단위 테스트를 작성할](https://blogs.msdn.microsoft.com/devops/2018/03/07/devops-for-iot-with-win10-iot-core-uwp-and-vsts/) 때 개발자는 이제 장치에 테스트를 배포 하 고 수동으로 실행 하는 대신 visual studio에서 직접 해당 단위 테스트를 장치에서 직접 실행할 수 있습니다.
* 개발자는 Windows 10 IoT에서 [WINDOWS AI 플랫폼](https://blogs.windows.com/buildingapps/2018/03/07/ai-platform-windows-developers/) 의 기능을 활용 하 여 더 지능적인 장치를 만들고 CPU 또는 GPU를 사용 하 여 ML 모델 평가를 가속화 할 수 있습니다.
* 음성 사용 장치를 신속 하 게 출시 하려는 Oem은 [Cortana 장치 SDK의 미리 보기](https://www.aka.ms/cortanadevices)를 사용 하 여 cortana 지원을 장치에 통합할 수 있습니다.
* Oem은 Windows에서 제공 되는 다양 한 Csp를 활용 하 여 [Azure IoT 장치 관리](https://github.com/ms-iot/iot-core-azure-dm-client)를 통해 대규모로 장치의 원격 구성 및 관리를 수행할 수 있습니다. 이 새로운 샘플 구현에서는 로컬 클라이언트, 클라우드 서비스 및 관리 포털을 결합 하 여 IoT 운영자가 클라우드 규모에서 장치 관리를 수행할 수 있도록 합니다.
* 이 릴리스에서는 명령 콘솔, PowerShell 등의 콘솔 호스트에서 실행 되는 [UWP 콘솔 앱](https://docs.microsoft.com/windows/uwp/launch-resume/console-uwp) 을 작성할 수 있습니다. UWP 콘솔 앱은 UWP 앱에 사용할 수 있는 Win32 Api를 사용할 수도 있으며 Microsoft Store를 통해 게시 하 고 업데이트할 수 있습니다.
* 장치를 Miracast 전송기 또는 수신자 역할을 할 수 있도록 하는 [캐스트 api 집합과](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/BasicMediaCasting) 함께 IoT Core에 대 한 새로운 [Miracast 기능 패키지](https://docs.microsoft.com/windows/iot-core/connect-your-device/miracast) 를 추가 했습니다.
* Bluetooth [A2DP](https://docs.microsoft.com/windows/iot-core/connect-your-device/bluetooth) 프로필에 대 한 지원이 추가 되었습니다 .이 프로필을 사용 하면 장치가 AVRCP 프로필을 사용 하 여 bluetooth를 통한 원격 제어 기능을 포함 하 여 bluetooth 스트리밍을 위한 오디오 소스로 작동할 수 있습니다.
* 가장 인기 있는 Qualcomm 보드 중 하나인 DragonBoard 410c는이 릴리스와 함께 훨씬 더 쉽게 사용할 수 있게 되었습니다. 최신 버전의 [Windows 10 IoT Core 대시보드](https://docs.microsoft.com/windows/iot-core/connect-your-device/iotdashboard)를 사용 하 여 보드를 연결 하 고, 플래시 모드로 전환 하 고, 대시보드에서 직접 [장치를 플래시](https://developer.microsoft.com/en-us/windows/iot/getstarted/prototype/setupdevice) 하면 됩니다.
* Wifi 네트워크를 찾고 연결 하는 경우 이전에는 사용 되지 않는 netcmd 명령과 동일 하 게 [Wifi 커넥터 샘플이](https://github.com/Microsoft/Windows-iotcore-samples/blob/develop/Samples/WiFiConnector/CS) 업데이트 되었습니다. 이 샘플에서는 [WiFiAdapter api](https://docs.microsoft.com/uwp/api/Windows.Devices.WiFi.WiFiAdapter) 를 사용 하 여 무선 네트워크 연결 및 어댑터를 관리 합니다.
* 장치 위치에 따라 자동으로 시스템 클럭을 [현지 시간](https://docs.microsoft.com/uwp/api/windows.system.datetimesettings.setsystemdatetime) 및 [표준 시간대](https://docs.microsoft.com/uwp/api/windows.system.timezonesettings.autoupdatetimezoneasync#Windows_System_TimeZoneSettings_AutoUpdateTimeZoneAsync_Windows_Foundation_TimeSpan_) 로 설정 하는 새로운 시간 관련 api를 사용 하 여 oem이 더 효율적인 기본 제공 환경을 만들 수 있습니다.
* 기본 설정 된 사용자 [언어](https://docs.microsoft.com/uwp/api/windows.system.userprofile.globalizationpreferences.trysetlanguages#Windows_System_UserProfile_GlobalizationPreferences_TrySetLanguages_Windows_Foundation_Collections_IIterable_System_String__), [지역](https://docs.microsoft.com/uwp/api/windows.system.userprofile.globalizationpreferences.trysethomegeographicregion#Windows_System_UserProfile_GlobalizationPreferences_TrySetHomeGeographicRegion_System_String_), 기본 [음성](https://docs.microsoft.com/uwp/api/windows.media.speechrecognition.speechrecognizer.trysetsystemspeechlanguageasync) 언어 및 기본 [음성을](https://docs.microsoft.com/uwp/api/windows.media.speechsynthesis.speechsynthesizer.trysetdefaultvoiceasync)설정 하기 위한 새로운 언어 api가 있습니다.
* 새 [mtp 기능 패키지](https://github.com/PawelWMS/windows-iotcore-docs/blob/MTP_Optional_Feature_Instructions/windows-iotcore/connect-your-device/MTP.md)를 사용 하면 Mtp (미디어 전송 프로토콜)를 사용 하 여 Windows 10 IoT Core 장치 간에 파일을 전송할 수 있습니다. 여기에는 장치의 내부 저장소 및 SD 카드 (있는 경우)에 있는 파일이 포함 됩니다.
* Azure IoT Central에 통합 된 Windows 10 IoT 장치를 얼마나 쉽게 가져올 수 있음을 보여 주는 GitHub 및 [Channel 9 비디오](https://channel9.msdn.com/Shows/Internet-of-Things-Show/Connecting-Windows-IoT-Devices-To-IoT-Central) [에 대](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/Azure/IoTHubClients) 한 새 샘플을 게시 했습니다. 또한 Windows 10 IoT Core를 실행 하 [는 장치](https://docs.microsoft.com/azure/iot-central/howto-connect-windowsiotcore) 를 Azure IoT Central에 연결 하는 방법을 설명 하는 설명서를 업데이트 했습니다.

## <a name="improvements-in-assigned-access"></a>할당 된 액세스의 향상 된 기능
* 디지털 signage 사용 사례에 대 한 여러 화면에 대 한 지원이 추가 되었습니다.
* 이제 등록 상태 페이지에는 할당 된 액세스를 입력 하기 전에 장치에 모든 MDM 구성이 적용 되도록 하는 기능이 포함 됩니다.
* 기존 UWP 스토어 앱 외에도 셸 시작 관리자를 구성 하 고 실행 하는 기능을 추가 했습니다.
* 자동 로그온 계정을 만들고 구성 하는 간소화 된 프로세스를 사용 하 여 다시 부팅 한 후에는 할당 된 액세스를 사용 하는 장치를 자동으로 원하는 상태로 전환 하도록 구성할 수 있습니다.
* 다중 사용자 장치의 경우, 이제 모든 사용자를 지정 하는 대신 Azure AD 그룹 또는 Active Directory 그룹에 할당 된 다른 액세스 구성을 할당할 수 있습니다.
* 문제 해결을 돕기 위해 할당된 액세스 구성 앱에 문제가 있는 경우 이제 생성된 오류 보고서를 볼 수 있습니다.

## <a name="features-in-preview-for-dev-and-test-scenarios"></a>개발 및 테스트 시나리오를 위한 미리 보기의 기능
* 장치 업데이트 센터 [Preview]를 통해 Oem은 앱을 전역적으로 관리 하 고, 클라우드에서 운영 체제, 앱, 설정 및 파일에 대 한 업데이트를 장치에 푸시 하 여 최신 상태로 유지 하 고 안전 하 게 유지할 수 있습니다.
* 64 비트 버전의 Windows 10 IoT Core 및 Enterprise에서 [Nano Server 컨테이너](https://docs.microsoft.com/virtualization/windowscontainers/about/index) 호스팅을 지원 하므로 응용 프로그램과 해당 데이터를 서로 격리 하 고 개발에서 프로덕션 또는 클라우드로 신속 하 게 이동할 수 있습니다.
* Windows 디바이스 상태 증명 [Preview] 서비스는 하드웨어 기능 및 클라우드 서비스를 사용 하 여 하드웨어 수준 메트릭과 증명 된 데이터를 기반으로 하는 장치 상태의 변조 교정 및 원격 증명을 제공 합니다.
* Windows IoT [미리 보기]를 [Azure IoT Edge](https://azure.microsoft.com/campaigns/iot-edge/) iot 솔루션은 클라우드 및에 지 장치 간에 인텔리전스를 오케스트레이션 할 수 있으므로 응용 프로그램 및 서비스가 가장 적합 한 위치에서 iot 데이터에 대해 작업을 수행할 수 있습니다.
* Azure IoT Hub [장치 프로 비전 서비스 [미리 보기]](https://blogs.windows.com/buildingapps/2017/10/05/windows-10-iot-enables-complete-iot-lifecycle/) 를 사용 하면 제조 중에 공통 이미지를 사용 하 여 Windows 10 IoT 장치를 만들고, 처음 Azure IoT Hub 부팅 시 자동으로 연결 하 여 장치 관련 프로 비전 정보를 검색할 수 있습니다.

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

## <a name="additional-information"></a>추가 정보
* Intel Joule 플랫폼 생성을 중지 하는 최근 Intel 발표에 기반 하 여 이전 릴리스에서 Intel Joule에 대 한 FFUs가 중단 되었습니다. Intel Joule을 평가 하는 고객은 지원 되는 다른 Soc 중 하나를 사용 하 여 대체 플랫폼을 식별 해야 합니다. 목록은 [제안 된 보드와 soc](https://docs.microsoft.com/windows/iot-core/learn-about-hardware/suggestedboards) 를 참조 하세요.

## <a name="known-issues"></a>알려진 문제
* Visual Studio에서 배포하는 F5 드라이버는 Windows 10 IoT Core에서 작동하지 않습니다. 드라이버를 수동으로 복사 하 여 장치에 등록 해야 합니다.
* NOOBS를 통해 설치된 디바이스는 커널 디버거를 사용하도록 설정하는 bcdedit 도구를 실행할 수 없습니다.
* Windows IoT 원격 클라이언트가 Raspberry Pi와 함께 작동하지 않습니다. Minnowboard Max 또는 Dragonboard처럼 가속 그래픽을 사용하는 보드를 사용하거나 로컬 표시용 모니터를 연결하세요.
