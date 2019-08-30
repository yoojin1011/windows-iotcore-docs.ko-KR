---
title: IoT Shell 개요
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: IoT 셸을 활용 하 여 장치에서 탐색을 탐색 하는 방법에 대해 알아봅니다.
keywords: windows iot, IoT core shell, 응용 프로그램, 포그라운드 응용 프로그램, 백그라운드 응용 프로그램
ms.openlocfilehash: 74d8406036aa18dc5f8dcaa871e116eb7f8ec29b
ms.sourcegitcommit: beed912a2266d6dbc06a8a26b85ff49f1feffd69
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/21/2019
ms.locfileid: "67316626"
---
# <a name="iot-shell-overview"></a>IoT Shell 개요

이 문서에서는 IoT Shell, 포그라운드 및 백그라운드 응용 프로그램, 장치에서 이러한 응용 프로그램을 탐색 하는 방법에 대해 설명 합니다.

## <a name="iot-shell-foreground-and-background-apps"></a>IoT Shell, 포그라운드 및 백그라운드 앱

Iot Core 장치는 IoT 셸을 실행 합니다. 많은 책임이 있지만 기본 작업은 등록 된 시작 앱이 시작 되도록 하는 것입니다. 다음과 같은 두 가지 모드가 있습니다. 양방향 및 헤드리스. 또한 IoT Shell은 UI를 전체 화면 (바로 앱이 라고도 함)에 표시 하는 등록 된 단일 시작 앱을 시작 합니다. 화살표는 연결 된 화면이 있고 UI를 표시 하는 것으로 가정 합니다. 헤드리스 모드 ( [여기서](../learn-about-hardware/HeadlessMode.md)자세히 설명)에서는 UI가 없습니다. IoT Shell은 백그라운드 응용 프로그램만 시작 합니다.

다음은 포그라운드 응용 프로그램과 백그라운드 응용 프로그램 간의 주요 차이점입니다.

- **포그라운드 응용 프로그램** 에는 UI가 있습니다. 이러한 항목 중 하나는 장치가 위쪽 모드인 경우 시작 시 시작 됩니다. 모든 포그라운드 앱은 장치에 등록 되며 사용자는 장치 작업 중에 포그라운드 앱 간을 전환할 수 있습니다.

- **백그라운드 응용 프로그램** 은 ui를 포함 하지 않으므로 ui 스택을 해제 하 여 장치 리소스를 저장 합니다. 백그라운드 응용 프로그램은 종종 시작에서 계속 실행 되며 장치를 모니터링 하는 데 종종 사용 됩니다.

## <a name="switching-between-apps-with-a-home-app"></a>홈 앱을 사용 하 여 앱 간 전환

현재 시작 앱을 사용 하면 다른 포그라운드 응용 프로그램 간에 전환할 수 있는 Windows 10 IoT Core 용 홈 앱을 만들 수 있습니다. 

**IoT 시작 앱** ([샘플](https://github.com/microsoft/Windows-iotcore-samples/tree/master/Samples/IoTStartApp) 은 장치에 설치 된 앱을 나열 하는 간단한 시작 앱을 나타내며, PackageManager api를 사용 하 여 하나를 시작 합니다.

## <a name="switching-between-apps-with-hid-injection-keys"></a>HID 삽입 키를 사용 하 여 앱 간 전환

아래 지침에서는 레지스트리 항목을 통해 바로 가기 키 지원을 설정 하는 방법을 보여 줍니다. 사용자 고유의 이미지를 빌드하고 레지스트리에 액세스할 필요 없이 아래 핫키 (홈, 이전 앱 및 다음 앱)를 지원 하려는 경우 이러한 단계를 처리 하는 선택적 기능 패키지를 포함할 수 있습니다.

찾을 기능 패키지를 라고 합니다. **Microsoft-OneCore-IoTUAP-Shell-HotKeys-Feature-Package** 및이 기능을 **IOT_SHELL_HOTKEY_SUPPORT**라고 합니다. 예제는 [설정. 핫키 샘플 패키지](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Common/Packages/Settings.HotKey/Settings.HotKey.pkg.xml) 를 참조 하십시오.

이 문서의 나머지 부분에서는이 기능을 수동으로 구현 하는 방법을 설명 합니다.

### <a name="return-home"></a>홈 반환

IoT Shell은 Windows 10 IoT 기념일 업데이트 (1607)를 사용 하 여 다른 응용 프로그램이 실행 중일 때 키보드의 Windows 단추 릴리스로 설정 된 "이동 홈" 키를 눌러 기본 응용 프로그램 창을 포그라운드로 가져오는 것을 지원 합니다. IoT 장치에 키보드가 없고 [HID 주입](https://developer.microsoft.com/en-us/windows/iot/samples/hidinjection)을 통해 하위 수준 키보드 이벤트를 삽입 해야 하는 경우 또는 "홈 홈" 기능을 앱의 다른 키에 다시 매핑하려는 경우 레지스트리에서 키 값을 조정할 수 있습니다. 예를 들어, 이스케이프 키 (0x1B)를 "이동 홈"으로 누르기를 사용 하도록 설정 하려면 레지스트리에서 다음 명령을 입력 합니다.

``
“HKLM\Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\HotKeys” “HOME” QWORD    0x0000000 0000001B  
``

REG 파일은 다음과 같습니다.

``
[HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\HotKeys]
"Home"=hex(b):1B,00,00,00,00,00,00,00
``

### <a name="switch-between-apps"></a>앱 간 전환

또는 포그라운드 앱 간에 전환 하려는 경우에는 레지스트리에 다음 명령을 입력 하 여 Alt 탭 (다음 앱) 및 Shift + Tab (이전 앱) 기능을 이미지에서 설정할 수 있습니다.

``
“HKLM\Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\HotKeys”
“PREV” QWORD 0x00010000 00010009 
“NEXT” QWORD 0x00020000 00050009 
``

REG 파일은 다음과 같습니다.``
[HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\HotKeys]
"Prev"=hex(b):09,00,01,00,00,00,01,00
"Next"=hex(b):09,00,05,00,00,00,02,00
``

### <a name="bit-translation"></a>비트 변환

위의 REG 파일 항목은 다음과 같이 왼쪽에서 오른쪽으로 디코딩합니다.

- 비트 0-15: 가상 키 코드 (예: 1B, 00 (이스케이프)). 키 코드 값의 전체 목록은 [가상 키 코드](https://msdn.microsoft.com/library/windows/desktop/dd375731(v=vs.85).aspx) 를 참조 하세요.
- 비트 16-19: 한정자 키입니다. 0x0 = No 한정자, 0x1 = ALT, 0x2 = CTRL 및 0x4 = SHIFT입니다. 키를 조합 하면 값이 함께 추가 됩니다 (예: ALT + SHIFT는 0x5).
- 비트 20-47: 나중에 사용 하도록 예약 되어 있습니다. 0 이어야 합니다.
- 비트 48-62:  작업
    - 0 = 홈
    - 1 = 이전 보기 (이후 릴리스에서 작동 하지 않을 수 있음)
    - 2 = 다음 보기 (이후 릴리스에서 작동 하지 않을 수 있음)
- 비트 63: 쓰이는 0 이어야 합니다.

