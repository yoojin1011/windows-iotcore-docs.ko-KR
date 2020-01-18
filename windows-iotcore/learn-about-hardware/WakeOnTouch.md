---
title: Wake on Touch
author: jordanrh1
ms.author: jordanrh
ms.date: 09/17/2018
ms.topic: article
description: 장치를 켜 켜 켜 지도록 구성
keywords: windows iot, 화면, 절전 모드, 절전 모드 해제, 터치, 대기, 전원
ms.custom: RS5
ms.openlocfilehash: 11aaaeed721ff3df7d4b78a29ddb3d0f1b4aa732
ms.sourcegitcommit: 0fa10fafb13788496674d13e0ae810a6d93e3483
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76258532"
---
# <a name="configure-your-device-to-wake-on-touch"></a>장치를 켜 켜 켜 지도록 구성

일부 시나리오에서는 사용자가 터치 스크린을 터치 하는 동안 사용 하지 않는 동안 장치의 화면을 끄고 신속 하 게 설정 하는 것이 좋습니다. 이 문서에서는이 시나리오를 달성할 수 있도록 장치를 구성 하는 방법을 설명 합니다.

## <a name="setting-a-video-idle-timeout"></a>비디오 유휴 시간 제한 설정

비디오 유휴 시간 제한을 설정 하 여 비활성 기간 후에 화면을 해제 하도록 구성할 수 있습니다. 사용자가 지정 된 시간 동안 장치와 상호 작용 하지 않으면 화면이 꺼집니다. 이렇게 하면 디스플레이와 관련 된 구성 요소의 전원을 켜는 방식으로 장치에서 절전 모드로 전환 될 수 있습니다.

```powershell
    powercfg.exe /setacvalueindex SCHEME_CURRENT SUB_VIDEO VIDEOIDLE 10
    powercfg.exe /setdcvalueindex SCHEME_CURRENT SUB_VIDEO VIDEOIDLE 10
    powercfg.exe /setactive SCHEME_CURRENT
```

자세한 내용은 [유휴 시간 제한](/windows-hardware/customize/power-settings/display-settings-display-idle-timeout) 및 [디스플레이, 절전 모드 및 최대 절전 모드 타이머](/windows-hardware/design/device-experiences/display--sleep--and-hibernate-idle-timers)표시를 참조 하세요.

## <a name="disabling-modern-standby"></a>최신 대기를 사용 하지 않도록 설정

AoAC 시스템 (모든 ARM 시스템 포함)에서는 디스플레이가 꺼진 경우 시스템이 자동으로 [최신 대기 모드로](/windows-hardware/design/device-experiences/modern-standby) 전환 됩니다. 시스템이 최신 대기 상태 이면 특정 입력에 의해서만 해제 수 있습니다. 이 목록은 완전 한 목록이 아니지만 이러한 입력에는 전원 단추를 누르거나 랩톱에서 덮개를 열거나 마우스를 클릭 하는 작업이 포함 됩니다. 화면 터치는 최신 대기에서 장치를 절전 모드에서 해제 하지 않습니다. 장치를 터치 하 여 절전 모드를 해제 하려면 최신 대기 모드로 들어가지 않도록 장치를 구성 해야 합니다. 최신 대기를 사용 하지 않도록 설정 하려면 다음 레지스트리 키를 설정 하 고 다시 부팅 합니다.

```powershell
    reg add HKLM\System\CurrentControlSet\Control\Power /v PlatformAoAcOverride /t REG_DWORD /d 0
```
    
최신 대기를 사용 하지 않도록 설정 하면 시스템이 유휴 상태일 때 전력 소비에 영향을 줄 수 있습니다. 최신 대기를 사용 하지 않도록 설정 하기 전에 최신 대기를 사용 하도록 설정 하 고 사용 하지 않도록 설정 하 여 시스템의 전력 소비량을 측정 해야 합니다.

최신 대기는 가능한 한 시스템 작업을 자동으로 시도 하 여 하드웨어를 저전력 상태로 전환할 수 있도록 하는 소프트웨어 메커니즘입니다. 이론적으로 최신 대기를 사용 하지 않도록 설정 된 충분 한 자동 장치는 최신 대기 상태의 장치와 동일한 저전력 소비를 달성할 수 있습니다. 최신 대기를 사용 하지 않는 경우 소프트웨어 타이머 및 정기 작업을 포함 하 여 백그라운드 작업을 최소화 하는 것이 중요 합니다.
