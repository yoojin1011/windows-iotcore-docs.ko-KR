---
title: 2018년 4월 업데이트 - 빌드 17134
ms.date: 05/01/2018
ms.topic: article
description: Windows 10 IoT용 2018년 4월 업데이트의 새로운 기능에 대해 알아봅니다.
keywords: Windows IoT, 2018년 4월 업데이트, 릴리스 정보
ms.openlocfilehash: b06378db14ba78fc5a3eb60e842e1555e56a66ac
ms.sourcegitcommit: 34928850d3b1b2fe22a92ebd1d75c01b3d4bf0aa
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/24/2020
ms.locfileid: "75721756"
---
# <a name="april-2018-update-release-notes-for-windows-10-iot"></a>Windows 10 IoT용 2018년 4월 업데이트 릴리스 정보
빌드 번호 17134. 2018년 5월

Windows 10 IoT는 임베디드 또는 전용 디바이스를 개발할 수 있도록 하며, 스마트 디바이스용 Windows 솔루션을 빌드하는 OEM 및 개발자에게 적합합니다.

이 문서에서는 이 Windows 10 IoT 릴리스에 대한 다른 내용과 설명서를 보충하는 정보를 제공합니다.

## <a name="privacy-statement"></a>개인정보취급방침

이 Windows 운영 체제 버전에 대한 개인정보처리방침은 [https://go.microsoft.com/fwlink/?LinkId=521839](https://go.microsoft.com/fwlink/?LinkId=521839)에서 볼 수 있습니다.

## <a name="whats-new-in-april-2018-update"></a>2018년 4월 업데이트의 새로운 기능
* [Visual Studio 15.6 RTW](https://docs.microsoft.com/visualstudio/releasenotes/vs2017-relnotes#Win10_IoT_Core_Testing_Support)와 함께 제공되는 [Visual Studio 테스트 플랫폼](https://blogs.msdn.microsoft.com/devops/2017/02/12/evolving-the-visual-studio-test-platform-part-4-together-in-the-open/)은 이제 Windows 10 IoT Core에서 테스트를 지원합니다. Windows 10 IoT Core를 대상으로 하는 Visual Studio 2017의 프로젝트에 대한 [단위 테스트를 작성](https://blogs.msdn.microsoft.com/devops/2018/03/07/devops-for-iot-with-win10-iot-core-uwp-and-vsts/)하는 경우 개발자는 이제 테스트를 디바이스에 배포하고 수동으로 실행할 필요 없이 Visual Studio에서 직접 디바이스에 대한 단위 테스트를 원격으로 실행할 수 있습니다.
* 개발자는 Windows 10 IoT에서 [Windows AI 플랫폼](https://blogs.windows.com/buildingapps/2018/03/07/ai-platform-windows-developers/)의 기능을 활용하여 인텔리전트 디바이스를 만들고 CPU또는 GPU를 사용하여 ML 모델 평가를 가속화할 수 있습니다.
* 음성 지원 디바이스를 빠르게 출시하려는 OEM은 [Cortana 디바이스 SDK 미리 보기](https://www.aka.ms/cortanadevices)를 사용하여 Cortana 지원을 디바이스에 통합할 수 있습니다.
* OEM은 Windows에서 사용할 수 있는 다양한 CSP 세트를 활용하여 [Azure IoT 디바이스 관리](https://github.com/ms-iot/iot-core-azure-dm-client)에서 규모에 맞게 원격으로 구성하고 관리할 수 있습니다. 이 새로운 샘플 구현은 로컬 클라이언트, 클라우드 서비스 및 관리 포털을 결합하여 IoT 운영자가 클라우드 규모에서 디바이스 관리를 수행할 수 있도록 합니다.
* 이 릴리스를 사용하면 명령 콘솔 또는 PowerShell과 같이 콘솔 호스트에서 실행되는 [UWP 콘솔 앱](https://docs.microsoft.com/windows/uwp/launch-resume/console-uwp)을 작성할 수 있습니다. 또한 UWP 콘솔 앱은 UWP 앱에서 사용할 수 있는 Win32 API를 사용할 수 있으며 Microsoft Store를 통해 게시하고 업데이트할 수 있습니다.
* 디바이스가 Miracast 송신기 또는 수신기로 작동할 수 있도록 [캐스팅 API 세트](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/BasicMediaCasting)와 함께 새로운 IoT Core용 [Miracast 기능 패키지](https://docs.microsoft.com/windows/iot-core/connect-your-device/miracast)가 추가되었습니다.
* [Bluetooth A2DP-SRC](https://docs.microsoft.com/windows/iot-core/connect-your-device/bluetooth) 프로필에 대한 지원이 추가되었습니다. 이에 따라 AVRCP 프로필을 사용하는 Bluetooth를 통한 원격 제어 기능을 포함하여 디바이스가 Bluetooth 스트리밍의 오디오 원본으로 작동할 수 있습니다.
* 가장 인기 있는 Qualcomm 보드 중 하나인 DragonBoard 410c는 이 릴리스에서 훨씬 쉽게 플래시할 수 있게 되었습니다. 최신 버전의 [Windows 10 IoT Core 대시보드](https://docs.microsoft.com/windows/iot-core/connect-your-device/iotdashboard)를 사용하는 경우 보드를 연결하고, 플래시 모드로 전환하고, 대시보드에서 직접 [디바이스를 플래시](https://developer.microsoft.com/en-us/windows/iot/getstarted/prototype/setupdevice)하면 됩니다.
* WiFi 네트워크를 찾아서 연결하기 위해 이전에 더 이상 사용되지 않은 netcmd 명령과 동일하게 [WiFi 커넥터 샘플](https://github.com/Microsoft/Windows-iotcore-samples/blob/develop/Samples/WiFiConnector/CS)이 업데이트되었습니다. 이 샘플에서는 [WiFiAdapter API](https://docs.microsoft.com/uwp/api/Windows.Devices.WiFi.WiFiAdapter)를 사용하여 무선 네트워크 연결 및 어댑터를 관리합니다.
* 디바이스 위치를 기준으로 시스템 시계를 [현지 시간](https://docs.microsoft.com/uwp/api/windows.system.datetimesettings.setsystemdatetime) 및 [표준 시간대](https://docs.microsoft.com/uwp/api/windows.system.timezonesettings.autoupdatetimezoneasync#Windows_System_TimeZoneSettings_AutoUpdateTimeZoneAsync_Windows_Foundation_TimeSpan_)로 자동으로 설정하는 새로운 시간 관련 API를 제공하므로 OEM에서 더 간소화된 기본 제공 환경을 만들 수 있습니다.
* 기본 설정 사용자 [언어](https://docs.microsoft.com/uwp/api/windows.system.userprofile.globalizationpreferences.trysetlanguages#Windows_System_UserProfile_GlobalizationPreferences_TrySetLanguages_Windows_Foundation_Collections_IIterable_System_String__), [지역](https://docs.microsoft.com/uwp/api/windows.system.userprofile.globalizationpreferences.trysethomegeographicregion#Windows_System_UserProfile_GlobalizationPreferences_TrySetHomeGeographicRegion_System_String_), 기본 [음성](https://docs.microsoft.com/uwp/api/windows.media.speechrecognition.speechrecognizer.trysetsystemspeechlanguageasync) 언어 및 기본 [음성](https://docs.microsoft.com/uwp/api/windows.media.speechsynthesis.speechsynthesizer.trysetdefaultvoiceasync)을 설정하는 새로운 언어 API가 있습니다.
* 새 [MTP 기능 패키지](https://github.com/PawelWMS/windows-iotcore-docs/blob/MTP_Optional_Feature_Instructions/windows-iotcore/connect-your-device/MTP.md)를 사용하면 MTP(미디어 전송 프로토콜)를 사용하여 USB를 통해 Windows 10 IoT Core 디바이스 간에 파일을 전송할 수 있습니다. 여기에는 디바이스의 내부 스토리지 및 SD 카드에 있는 파일이 포함됩니다(있는 경우).
* Windows 10 IoT 디바이스를 Azure IoT Central에 쉽게 통합하는 방법을 보여 주는 새로운 샘플이 [GitHub](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/Azure/IoTHubClients) 및 [Channel 9 비디오](https://channel9.msdn.com/Shows/Internet-of-Things-Show/Connecting-Windows-IoT-Devices-To-IoT-Central)에 게시되었습니다. 또한 Windows 10 IoT Core를 실행하는 [디바이스를 Azure IoT Central에 연결하는 방법](https://docs.microsoft.com/azure/iot-central/howto-connect-windowsiotcore) 설명서도 업데이트되었습니다.

## <a name="improvements-in-assigned-access"></a>할당된 액세스의 향상된 기능
* 디지털 서명 사용 사례에 대한 여러 화면 지원이 추가되었습니다.
* 등록 상태 페이지에는 이제 할당된 액세스를 시작하기 전에 모든 MDM 구성이 디바이스에 적용되도록 하는 기능이 포함되어 있습니다.
* 기존 UWP 스토어 앱 외에도 셸 시작 관리자를 구성하고 실행하는 기능이 추가되었습니다.
* 할당된 액세스를 사용하는 디바이스는 자동 로그온 계정을 만들고 구성하는 간소화된 프로세스를 사용하여 다시 부팅 후 자동으로 원하는 상태로 전환되도록 구성할 수 있습니다.
* 다중 사용자 디바이스의 경우 이제 모든 사용자를 지정하는 대신 서로 다른 할당된 액세스 구성을 Azure AD 그룹 또는 Active Directory 그룹에 할당할 수 있습니다.
* 문제 해결에 도움이 되도록 할당된 액세스 구성 앱에 문제가 있는 경우 이제 생성된 오류 보고서를 볼 수 있습니다.

## <a name="features-in-preview-for-dev-and-test-scenarios"></a>개발 및 테스트 시나리오 미리 보기의 기능
* 디바이스 업데이트 센터[미리 보기]를 사용하면 OEM에서 앱을 전역적으로 관리하고 운영 체제, 앱, 설정 및 파일에 대한 업데이트를 클라우드에서 디바이스로 푸시하여 최신 상태로 안전하게 유지할 수 있습니다.
* Windows 10 IoT Core 및 Enterprise 64비트 버전에서 [Nano 서버 컨테이너](https://docs.microsoft.com/virtualization/windowscontainers/about/index)를 호스팅하도록 지원하여 애플리케이션과 해당 데이터를 서로 격리하고 개발에서 프로덕션 또는 클라우드로 빠르게 이동할 수 있습니다.
* Windows 디바이스 상태 증명[미리 보기] 서비스는 하드웨어 기능 및 클라우드 서비스를 사용하여 하드웨어 수준 메트릭과 증명된 데이터에 따라 디바이스 상태에 대한 변조 교정 및 원격 증명을 제공합니다.
* Windows IoT의 [Azure IoT Edge](https://azure.microsoft.com/campaigns/iot-edge/)[미리 보기]를 사용하면 IoT 솔루션에서 클라우드와 에지 디바이스 간의 인텔리전스를 오케스트레이션하여 애플리케이션과 서비스에서 IoT 데이터에 대한 작업을 가장 적합한 위치에서 수행할 수 있습니다.
* Azure IoT Hub [디바이스 프로비저닝 서비스[미리 보기]](https://blogs.windows.com/buildingapps/2017/10/05/windows-10-iot-enables-complete-iot-lifecycle/)를 사용하면 제조 중에 일반적인 이미지를 사용하여 Windows 10 IoT 디바이스를 만들고, 처음 부팅할 때 자동으로 Azure IoT Hub에 연결하여 디바이스 관련 프로비저닝 정보를 검색하도록 구성할 수 있습니다.

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
* Intel Joule 플랫폼 생산을 중단하겠다는 Intel의 최근 발표에 따라 이전 릴리스에서 Intel Joule용 FFU가 중단되었습니다. Intel Joule을 평가하는 고객은 지원되는 다른 SoC 중 하나를 사용하여 대체 플랫폼을 식별해야 합니다. 목록은 [제안된 보드 및 SoC](https://docs.microsoft.com/windows/iot-core/learn-about-hardware/suggestedboards)를 참조하세요.

## <a name="known-issues"></a>알려진 문제
* Visual Studio에서 배포하는 F5 드라이버는 Windows 10 IoT Core에서 작동하지 않습니다. 드라이버를 수동으로 복사하여 디바이스에 등록해야 합니다.
* NOOBS를 통해 설치된 디바이스는 커널 디버거를 사용하도록 설정하는 bcdedit 도구를 실행할 수 없습니다.
* Windows IoT 원격 클라이언트가 Raspberry Pi와 함께 작동하지 않습니다. Minnowboard Max 또는 Dragonboard처럼 가속 그래픽을 사용하는 보드를 사용하거나 로컬 표시용 모니터를 연결하세요.
