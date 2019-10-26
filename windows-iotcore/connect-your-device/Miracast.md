---
title: IoT Core의 Miracast
ms.date: 11/30/2017
ms.topic: article
description: 장치에 Miracast 기능을 포함 하는 방법을 알아봅니다.
keywords: windows iot, miracast, 연결
ms.openlocfilehash: bb997d0ec2899e7a0a988674ae8907e15e87b3c3
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918325"
---
# <a name="miracast-on-iot-core"></a>IoT Core의 Miracast

이 문서에서는 IoT Core 장치에 Miracast 기능을 포함 하는 방법을 보여 줍니다.

> [!IMPORTANT]
> 이 기능은 Insider Build 17093 이상 에서만 사용할 수 있습니다.

## <a name="miracast-overview"></a>Miracast 개요

Miracast 연결은 두 가지 구성 요소인 원본 및 싱크로 구성 됩니다. **Miracast 소스** 는 콘텐츠를 표시 하는 **miracast 싱크로**콘텐츠를 보냅니다. 연결을 만들기 위해 싱크는 연결 된 Wi-fi 네트워크에 자신을 알립니다. 소스는 **장치 선택기** 를 사용 하 여 싱크를 선택 하 고 연결을 요청 합니다. 연결이 요청 되 면 싱크의 사용자는 원본에서 연결을 시도 하 고 있는지 확인 하 고 연결이 발생 해야 하는지 확인 해야 합니다. 이 문제가 발생 하면 소스가 연결을 취소 하거나 싱크가 광고를 중지할 때까지 소스는 싱크로 캐스트를 시작 합니다.

## <a name="hardware-requirements"></a>하드웨어 요구 사항

원본 및 싱크 장치는 모두 제대로 작동 하려면 Miracast 호환 Wi-fi 및 그래픽 드라이버와 칩셋이 필요 합니다. 장치에 Miracast 호환 하드웨어가 있는지 확인 하려면 다음을 실행 합니다. 
```
netsh wlan show driver
```
장치 명령 프롬프트에서.

장치에서 Miracast를 지 원하는 경우 아래 출력이 표시 됩니다.

![호환 되는 장치 출력](../media/Miracast/CompatibleDevice.png)

아래 표에는 IoT Core 참조 플랫폼에 대 한 Miracast 호환성이 나와 있습니다.

| 팀 | SoC | WiFi 드라이버가 있음 | 그래픽 드라이버 있음 | Miracast 호환 |
|-------|-----|----------------------|--------------------------|---------------------|
| Qualcomm Dragonboard 410c | Snapdragon 410 | 예 | 예 | 예 |
| Raspberry Pi 2/3 | Broadcom BCM283x | 예 | 아니요 | 아니요 |
| Minnowboard Max | Intel Atom E3825 | 예 | 아니요 | 아니요 |
| 위쪽 제곱 | Intel 셀러론 N3350 | 예 | 예 | 예 |


### <a name="wi-fi"></a>Wi-Fi

장치에 대 한 Wi-fi 드라이버와 칩셋은 Miracast를 지원 하기 위해 다른 기능 중에서 Wi-fi Direct를 지원 해야 합니다. 장치에 이러한 기능이 없는 경우에는 대신 USB Wi-fi 동글을 사용할 수 있습니다. [300M 무선 USB 어댑터](http://a.co/fdhEhV9)를 권장 합니다.

### <a name="graphics"></a>그래픽

그래픽 드라이버와 칩셋은 Miracast 인코딩 및 디코딩을 지원 해야 Miracast를 지원할 수 있습니다. 장치에 호환 되는 그래픽 드라이버 및/또는 칩셋이 없는 경우 새 장치를 선택 해야 합니다. Miracast 호환 장치를 선택 하는 경우 위의 매트릭스를 참조 하세요.

## <a name="windows-iot-as-a-miracast-sink"></a>Windows IoT를 Miracast 싱크로

장치를 Miracast 싱크로 사용 하도록 설정 하려면 장치에서 연결 앱을 사용 하도록 설정한 다음 레지스트리에서 Miracast를 사용 하도록 설정 해야 합니다.

### <a name="enable-the-connect-app"></a>연결 앱 사용

Connect 앱을 사용 하도록 설정 하려면 이미지에 **IOT_MIRACAST_RX_APP** 기능을 포함 해야 합니다. 또한 이미지에 **Microsoft-Connect-Package** 및 **Microsoft-Connect-Package_Lang_XXXX** 를 포함 해야 합니다. 여기서 XXXX는 언어 (예: "enus")입니다. 

이미지에 기능과 패키지를 추가 하는 방법에 대 한 자세한 내용은 [이 페이지](https://docs.microsoft.com/windows-hardware/manufacture/iot/deploy-your-app-with-a-standard-board#update-the-feature-manifest) 를 참조 하세요. 다음 [지침](https://docs.microsoft.com/windows/iot-core/build-your-image/createinstallpackage)에 따라 패키지 및 기능을 기존 이미지에 테스트용으로 로드할 수도 있습니다. 이 기능을 함께 로드 하면 업데이트가 수신 되지 않습니다.


### <a name="enable-miracast"></a>Miracast 사용

[PowerShell](https://docs.microsoft.com/windows/iot-core/connect-your-device/powershell) 또는 [Windows 장치 포털](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal) 을 통해 장치에 연결 하 고 다음 명령을 실행 합니다.
```
reg add HKLM\Software\Microsoft\PlayToReceiver /v AutoEnabled /t REG_DWORD /d 1  
reg add HKLM\Software\Microsoft\MiracastReceiver /v  ConsentToast /t REG_DWORD /d 0  
reg add HKLM\Software\Microsoft\MiracastReceiver /v NetworkQualificationEnabled /t REG_DWORD /d 1  
reg add HKLM\Software\Microsoft\MiracastReceiver /v EnabledOnACOnly /t REG_DWORD /d 1  
```
이렇게 하면 A/C 전원에 연결 되어 있는 동안에만 동의 알림 없이 Miracast를 사용할 수 있습니다. IoT Core에서 Miracast 수신기를 실행 하는 데 권장 되는 방법입니다.

## <a name="windows-iot-as-a-miracast-source"></a>Windows IoT를 Miracast 원본으로

> [!IMPORTANT]
> 장치를 Miracast 원본으로 사용 하기 전에 아래와 같이 [Windows 장치 포털](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal) 에서 Is\on보드 ingtask 앱을 꺼야 합니다 .이 앱은 한 번만 수행 하면 됩니다. ![Is\on보드 ingtask 앱을 해제 하세요](../media/Miracast/IoTOnboardingOff.gif)
>
> 그런 다음 장치를 다시 시작 하세요.

앱에서 `Windows.Media.Casting` 네임 스페이스의 공용 Api를 통해 호환 되는 장치에서 Miracast 캐스트를 설정할 수 있습니다.

이러한 Api의 작동 방식을 확인 하려면 [BASICMEDIACASTING UWP 샘플](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/BasicMediaCasting) 을 다운로드 하 고 장치에서 실행 합니다. 이 샘플의 Api는 다음과 같은 시나리오를 다룹니다. 이러한 시나리오는 모두 Miracast 호환 IoT Core 장치에서 실행 됩니다.
1. 기본 제공 캐스트를 사용 하 여 Miracast, DLNA 및 Bluetooth 장치로 콘텐츠를 전송 하는 기본 미디어 캐스팅
2. 캐스팅 선택기를 사용 하 여 캐스팅 하 여 장치 선택기를 추가로 사용자 지정할 수 있습니다.
3. 사용자 지정 선택기를 사용 하 여 캐스팅-장치를 선택 하기 위한 사용자 지정 UX를 빌드하는 방법을 보여 줍니다.

> [!NOTE]
> 일부 Miracast 싱크 (Surface 노트북, Surface Hub, 무선 디스플레이 어댑터가 있는 PC)는 IoT Core 캐스트 장치와 호환 되지 않습니다. Miracast 싱크와 호환 되는 모니터와 함께 [Microsoft 무선 디스플레이 어댑터](https://www.microsoft.com/accessories/en-us/products/adapters/wireless-display-adapter-2/p3q-00001) 를 사용 하는 것이 좋습니다.
