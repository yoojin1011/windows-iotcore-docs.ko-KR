---
title: IoT Core에는 Miracast
author: saraclay
ms.author: saclayt
ms.date: 11/30/2017
ms.topic: article
description: 장치에서 Miracast 기능을 포함 하는 방법 알아보기
keywords: windows iot, miracast, 연결
ms.openlocfilehash: c58def4b218d35c78532f54df4a74fb572c8549e
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59515242"
---
# <a name="miracast-on-iot-core"></a>IoT Core에는 Miracast

이 문서에서는 IoT Core 장치에서 Miracast 기능을 포함 하는 방법을 설명 합니다.

> [!IMPORTANT]
> 이 기능은 에서만 Insider 빌드 17093 이상 사용할 수 있습니다.

## <a name="miracast-overview"></a>Miracast 개요

Miracast 연결을 두 가지 구성 요소로 이루어집니다: 원본과 싱크 합니다. **Miracast 원본** 콘텐츠를 전송 합니다 **Miracast 싱크**, 콘텐츠를 표시 하는 합니다. 연결을 만들려면 싱크 보급 자체 연결 된 Wi-fi 네트워크에 있습니다. 원본을 사용 하는 **장치 선택** 싱크를 선택 하 고 연결 요청을 합니다. 연결 요청 되 면 싱크에 받을지 경고 원본에 연결 하려고 하는 연결 수행 해야 할지 확인 해야 합니다. 이렇게 되 면, 원본 연결을 취소 하는 원본 또는 싱크 광고 중지 될 때까지 싱크로 캐스팅을 시작 합니다.

## <a name="hardware-requirements"></a>하드웨어 요구 사항

둘 다가 원본 및 싱크는 장치도 Miracast-호환 Wi-fi 및 그래픽 드라이버 및 칩셋 제대로 작동 합니다. 장치의 Miracast 호환 하드웨어 있는지를 확인 하려면 다음을 실행 합니다. 
```
netsh wlan show driver
```
장치의 명령 프롬프트입니다.

장치에서 Miracast 지원, 아래 출력이 표시 됩니다.

![호환 장치 출력](../media/Miracast/CompatibleDevice.png)

아래 표에서 IoT Core 참조 플랫폼용 Miracast 호환성을 보여 줍니다.

| 보드 | SoC | WiFi 드라이버 제공 | 그래픽 드라이버 제공 | Miracast 호환 |
|-------|-----|----------------------|--------------------------|---------------------|
| Qualcomm Dragonboard 410 c | Snapdragon 410 | 예 | 예 | 예 |
| Raspberry Pi 2/3 | Broadcom BCM283x | 예 | 아니오 | 아니요 |
| Minnowboard 최대 | Intel Atom E3825 | 예 | 아니오 | 아니요 |
| 최대 제곱 | Intel Celeron N3350 | 예 | 예 | 예 |


### <a name="wi-fi"></a>Wi-Fi

Wi-fi 드라이버 및 장치에 대 한 칩셋 지원 해야 Wi-Fi Direct Miracast 지원 하기 위해 기타 기능이 제공 합니다. 장치에 이러한 기능이 없는 경우에 USB Wi-fi 동글 대신 사용할 수 있습니다. 권장 합니다 [300 M 무선 USB 어댑터](http://a.co/fdhEhV9)합니다.

### <a name="graphics"></a>그래픽

그래픽 드라이버 및 칩셋 h.264 인코딩 및 디코딩 Miracast 지원 하도록 지원 해야 합니다. 장치의 호환 되는 그래픽 드라이버 및/또는 칩셋에 없는 사용 하는 경우에 새 장치를 선택 합니다. Miracast 호환 장치를 선택할 때 위의 매트릭스를 참조 하세요.

## <a name="windows-iot-as-a-miracast-sink"></a>Windows IoT Miracast 싱크로

Miracast 싱크로 장치를 사용 하려면 장치에서 연결 앱을 사용 하도록 설정한 후 레지스트리에서 Miracast를 사용 하도록 설정 해야 합니다.

### <a name="enable-the-connect-app"></a>사용 하도록 설정 된 앱 연결

연결 앱을 사용 하려면 포함 해야 합니다 **IOT_MIRACAST_RX_APP** 이미지에는 기능입니다. 포함 해야 **Microsoft Connect 둘** 하 고 **Microsoft 연결 Package_Lang_XXXX.cab** (여기서 XXXX는 언어, 즉 "enUS") 이미지에서. 

참조 [이 페이지](https://docs.microsoft.com/windows-hardware/manufacture/iot/deploy-your-app-with-a-standard-board#update-the-feature-manifest) 이미지에 기능 및 패키지를 추가 하는 방법에 대 한 자세한 내용은 합니다. 있습니다 수 또한 테스트용으로 로드 패키지 및 기존 이미지에 기능을 수행 하 여 [이러한 지침](https://docs.microsoft.com/windows/iot-core/build-your-image/createinstallpackage)합니다. 이 기능을 테스트용으로 로드를 방지 하는 업데이트 수신을 점을 염두에 두십시오.


### <a name="enable-miracast"></a>Miracast를 사용 하도록 설정

통해 장치에 연결할 [PowerShell](https://docs.microsoft.com/windows/iot-core/connect-your-device/powershell) 또는 [Windows Device Portal](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal) 하 고 다음 명령을 실행 합니다.
```
reg add HKLM\Software\Microsoft\PlayToReceiver /v AutoEnabled /t REG_DWORD /d 1  
reg add HKLM\Software\Microsoft\MiracastReceiver /v  ConsentToast /t REG_DWORD /d 0  
reg add HKLM\Software\Microsoft\MiracastReceiver /v NetworkQualificationEnabled /t REG_DWORD /d 1  
reg add HKLM\Software\Microsoft\MiracastReceiver /v EnabledOnACOnly /t REG_DWORD /d 1  
```
이렇게 하면 보안 네트워크 에서만 및 a/C 전원에 연결 하는 동안에 동의 알림을 없이 Miracast 활성화 됩니다. 이것이 Miracast 수신기 IoT Core에서 실행 하는 권장된 방법입니다.

## <a name="windows-iot-as-a-miracast-source"></a>Windows IoT Miracast 원본으로

> [!IMPORTANT]
> 장치를 Miracast 소스로 사용 하기 전에 해제 하십시오 IoTOnboardingTask 앱 합니다 [Windows Device Portal](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal) 아래와 같이 한 번만 해야 하는: ![IoTOnboardingTask 앱 해제](../media/Miracast/IoTOnboardingOff.gif)
>
> 그런 다음 다시 시작 하십시오 장치

공용 Api 통해 호환 장치에서 Miracast 캐스팅을 설정할 수 있습니다는 `Windows.Media.Casting` 앱에서 네임 스페이스입니다.

작업에서 이러한 Api를 보려면 다운로드 합니다 [BasicMediaCasting UWP 샘플](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/BasicMediaCasting) 및 장치에서 실행 합니다. 이 샘플의 Api를 Miracast 호환 IoT Core 장치에서 실행 하는 모든 다음 시나리오를 다룹니다.
1. Miracast 고 DLNA, Bluetooth 장치에 콘텐츠를 전송 하는 기본 제공 캐스팅을 사용 하는 기본 미디어 캐스팅
2. 장치 선택기를 사용자 지정할 수 있는 캐스팅 선택기를 사용 하는 캐스팅
3. 장치를 선택 하기 위한 사용자 지정 사용자 경험을 구축 하는 방법을 보여 주는 사용자 지정 선택기를 사용 하 여 캐스팅을

> [!NOTE]
> 일부 Miracast 싱크 (무선 디스플레이 어댑터를 사용 하 여 Surface Laptop, Surface Hub, PC) IoT Core 캐스팅 장치와 호환 되지 않습니다. 사용 하는 것이 좋습니다 합니다 [Microsoft 무선 디스플레이 어댑터](https://www.microsoft.com/accessories/en-us/products/adapters/wireless-display-adapter-2/p3q-00001) 프로그램 Miracast 싱크로 호환 모니터를 사용 합니다.
