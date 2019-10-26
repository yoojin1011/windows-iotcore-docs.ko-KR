---
title: Bluetooth 지원
ms.date: 08/28/2017
ms.topic: article
description: Windows 10 IoT Core를 실행 하는 장치에 대해 Bluetooth를 활용 하는 방법을 알아봅니다.
keywords: windows iot, bluetooth, bluetooth 지원, 장치, 장치 포털
ms.openlocfilehash: e9159e6488ddcd078f5d73b0dafd08082e295cde
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918365"
---
# <a name="bluetooth-support"></a>Bluetooth 지원
Windows 10 IoT Core는 Bluetooth 4.0를 지원 합니다. 지원 되는 Bluetooth 동글 목록은 [하드웨어 호환성 목록](../learn-about-hardware/HardwareCompatList.md)에서 찾을 수 있습니다.

## <a name="about-bluetooth"></a>Bluetooth 정보
앱에서 구현 하도록 선택할 수 있는 두 가지 bluetooth 기술이 있습니다.

* Bluetooth LE 이전의 클래식 Bluetooth (RFCOMM) 장치는 일반적으로이 프로토콜을 사용 하 여 Bluetooth를 사용 하 여 통신 합니다. 이 프로토콜은 에너지 절약이 필요 없이 장치 간 통신하는 데 간단하고 유용합니다. 연결 하려면 페어링이 필요 합니다.

* Bluetooth 저 에너지 (정보/LE) Bluetooth 저 에너지 (LE)는 효율적인 에너지 사용 요구 사항이 있는 장치 간 검색 및 통신을 위한 프로토콜을 정의 하는 사양입니다. 최근 빌드에 대 한 코드 샘플을 포함 한 자세한 내용은 장치를 페어링 하지 않고 가장 많은 장치에 연결할 수 있습니다.

## <a name="supported-bluetooth-profiles"></a>지원 되는 Bluetooth 프로필
Windows 10 IoT Core는 다음 Bluetooth 프로필을 지원 합니다.

1.  **HID (휴먼 인터페이스 장치 프로필 개념)** HID 장치는 사람 으로부터 입력을 받아 인간 consumpation에 대 한 출력을 제공 합니다. 키보드, 마우스, 게임 컨트롤러, 바코드 판독기, LED 및 영숫자 표시의 예가 있습니다. Windows 10 IoT Core 장치는 Bluetooth를 통해 HID 장치에 연결할 수 있습니다. Windows 컨텍스트의 HID에 대 한 일반 항목인 [Hid 개념 소개](https://docs.microsoft.com/windows-hardware/drivers/hid/introduction-to-hid-concepts)를 참조 하세요. 

2.  **라디오 주파수 통신 (RFCOMM)** RFCOMMM는 클래식 Bluetooth의 기본 직렬 통신입니다. UWP 앱에서 지원 되는 RFCOMM 서비스는 다음과 같습니다.

* serialPort
* obexObjectPush
* obexFileTransfer
* phoneBookAccessPce
* phoneBookAccessPse
* genericFileTransfer

3. **일반 특성 프로필 (GATT)** [UWP-Bluetooth 저 에너지](https://docs.microsoft.com/windows/uwp/devices-sensors/bluetooth-low-energy-overview) 항목을 참조 하세요. 

> [!NOTE]
> AppManifest에서 RFCOMM 서비스를 수동으로 지정 해야 합니다.  [UWP-BLUETOOTH RFCOMM](https://docs.microsoft.com/windows/uwp/devices-sensors/send-or-receive-files-with-rfcomm) 항목을 참조 하세요. 또한 [UWP-Bluetooth Rfcomm 채팅 샘플](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/BluetoothRfcommChat) 항목을 참조 하세요.

## <a name="connecting-bluetooth-devices-using-the-device-portal"></a>장치 포털을 사용 하 여 Bluetooth 장치 연결
[Windows 10 IoT Core 릴리스 이미지](https://developer.microsoft.com/en-us/windows/iot/downloads) 중 하나를 사용 하는 경우 Bluetooth 장치는 장치 포털을 사용 하 여 Windows IoT core 장치와 쌍으로 연결할 수 있습니다. Bluetooth 탭으로 이동할 때 장치는 Bluetooth 장치를 검색 하 고 다른 Bluetooth 장치 에서도 검색할 수 있게 됩니다. 아래 그림은 들어오는 페어링 요청을 보여 줍니다. 

![Bluetooth 들어오는 페어링](../media/Bluetooth/Portal_BT_2.png)

장치가 성공적으로 페어링 된 후 페어링된 장치 섹션에 나열 됩니다. 

![Bluetooth 들어오는 페어링](../media/Bluetooth/Portal_BT_3.png)
