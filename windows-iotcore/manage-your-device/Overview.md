---
title: 디버깅 개요
ms.date: 05/10/2019
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: Windows 10 IoT Core를 디버그할 수 있는 여러 가지 방법에 대해 알아봅니다.
keywords: windows iot, 디버깅, PowerShell, SSH
ms.openlocfilehash: 455d8a90fc655b2deda4a09a661c849ff852b65c
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72917244"
---
# <a name="debugging-on-windows-iot-core"></a>Windows IoT Core에서 디버깅
응용 프로그램을 실행 하 여 IoT Core 이미지를 설치한 후에는 필요에 따라 응용 프로그램 또는 시스템을 디버그할 수 있는 것이 중요 합니다. 시스템을 디버깅 하 고 테스트 하는 데 가장 적합 한 시기는 테스트 이미지 상태입니다. IoT 코어 기반 시스템이 야생 경우 디버깅이 challanging 될 수 있습니다. 이는 수행할 수 없으며 테스트 단계와의 비교를 디버그 하기 위해 추가 어려움이 추가 된 것입니다. 테스트 모드에서 다음을 사용 하 여 응용 프로그램 또는 이미지를 디버그할 수 있습니다.

## <a name="device-portal"></a>장치 포털
WDP (Windows 장치 포털)를 사용 하면 로컬 네트워크를 통해 IoT 장치 remoately을 구성 하 고 관리할 수 있습니다. IoT 장치의 로컬 ip를 통해 WDP에 연결할 수 있습니다. IoT의 WDP에 대 한 추가 정보는 [여기](https://docs.microsoft.com/en-us/windows/iot-core/manage-your-device/DevicePortal)에서 찾을 수 있습니다.

### <a name="collecting-etw--wpp-logs"></a>ETW/WPP 로그 수집 
-----

### <a name="file-sharing"></a>파일 공유
앱 파일 탐색기는 앱이 액세스할 수 있는 디렉터리에 대 한 액세스를 허용할 수 있습니다. * vCameraRoll는 모든 앱에서 공유 됩니다.
* 문서는 모든 앱에서 공유 됩니다.
* LocalAppData에는 각 앱에 해당 하는 폴더가 포함 됩니다. 이 폴더는 앱과 이름이 같으며 다른 앱은 액세스할 수 없습니다.
자세한 내용은 위의 링크를 참조 하십시오.

### <a name="kernel-debug"></a>커널 디버그
WDP를 통해 live Kernel 덤프를 다운로드할 수도 있습니다. 모든 시스템 크래시는 자동으로 기록 되 고 다운로드 가능 합니다. 자세한 내용은 위의 링크를 참조 하십시오.

### <a name="enable-crash-dump"></a>크래시 덤프 사용
WDP를 통해 IoT 장치에서 응용 프로그램의 크래시 덤프를 다운로드할 수 있습니다. 자세한 내용은 위의 링크를 참조 하십시오.

## <a name="sshpowershelltshell"></a>SSH/PowerShell/TShell
PowerShell은 시스템 관리를 위해 특별히 설계 된 작업 기반 명령줄 셸 및 스크립트 언어입니다. Powershell 디버깅 및 설정에 대 한 자세한 내용은 [여기](../connect-your-device/powershell.md)를 참조 하세요.

## <a name="debug-through-visual-studio-deployment"></a>Visual Studio 배포를 통해 디버그
Visual Studio를 사용 하면 응용 프로그램을 간편 하 게 배포 하 고 디버그할 수 있습니다. 원격 디버깅 기능을 사용 하 여 로컬에 연결 된 Windows 10 IoT Core 장치에 앱을 배포 하 고 디버그할 수 있습니다. 배포 및 디버깅에 대 한 자세한 내용은 [여기](../develop-your-app/RemoteDebugging.md)를 참조 하세요.

-----
## <a name="live-app-debug"></a>라이브 앱 디버그
Visual Studio (2015 이상)에서는 Azure 애플리케이션 Insights의 원격 분석을 사용 하 여 디버깅 및 프로덕션 환경에서 ASP.NET 웹 앱의 성능을 분석 하 고 문제를 진단할 수 있습니다. 이 기능은 나중에 Visual Studio 2017 및 Azure Portal을 통해 데스크톱 및 UWP 응용 프로그램을 포함 하도록 확장 되었습니다. 프로젝트를 디버그 하는 방법에 대 한 추가 정보는 [여기](https://docs.microsoft.com/en-us/azure/azure-monitor/app/visual-studio) 에서 확인할 수 있으며, 데스크톱 또는 UWP 응용 프로그램의 성능 및 모니터링은 [여기](https://docs.microsoft.com/en-us/azure/azure-monitor/app/windows-desktop)에서 확인할 수 있습니다.
