---
title: Windows 10 IoT Core를 사용 하는 네트워크 3D 프린터
ms.date: 09/05/2017
ms.topic: article
description: Windows 10 IoT Core 장치를 인쇄 서버로 전환 하 고 3D 프린터를 연결 하는 방법에 대해 알아봅니다.
keywords: windows iot, 3D, 3D 프린터, 인쇄 서버, 네트워크 3D 프린터
ms.openlocfilehash: 3c11756f7832952f816978244d401d1d735a8f80
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918193"
---
# <a name="network-3d-printer-with-windows-10-iot-core"></a>Windows 10 IoT Core를 사용 하는 네트워크 3D 프린터

Windows 10 IoT Core 장치를 인쇄 서버로 전환 하 고 3D 프린터를 연결 합니다. 다른 장치에서 무선으로 프린터에 액세스할 수 있습니다.

## <a name="1-install-windows-10-iot-core-on-your-device"></a>1. 장치에 Windows 10 IoT Core를 설치 합니다.
___
시작 하기 전에 다음이 필요 합니다.

* 최신 버전의 Windows 10 IoT Core Insider Preview가 설치 된 보드입니다. [시작 가이드](https://developer.microsoft.com/en-us/windows/iot/getstarted) 에 따라 iot 대시보드 앱을 가져오고 Windows 10 iot Core를 설치 합니다.
* 네트워크 3D 프린터 앱과 호환 되는 3D 프린터:

    * Lulzbot Taz 6
    * Makergear M2
    * Printrbot Play, 더하기 및 단순
    * Prusa i3 Mk2
    * Ultimaker 원본 및 원본 +
    * Ultimaker 2 및 2 +
    * Ultimaker 2 확장 및 확장 +
    * CraftBot 2
    * CraftBot PLUS
    * LulzBot 미니
    * Velleman K8200

## <a name="2-connect-your-3d-printer-to-your-device"></a>2.3D 프린터를 장치에 연결
___
* USB 케이블을 사용 하 여 Windows 10 IoT Core 보드에 3D 프린터를 플러그인 합니다.

    ![3D 프린터를 장치에 연결](../media/3DPrintServer/connect-3d-printer.png)

* IoT 대시보드 앱을 열고 장치가 **내 장치** 탭에 표시 되는지 확인 합니다.

    ![장치가 IoT 대시보드에 표시 되는지 확인 합니다.](../media/3DPrintServer/selectDevice.png)
    
## <a name="3-deploy-the-network-3d-printer-app"></a>3. 네트워크 3D 프린터 앱 배포
___
* IoT 대시보드에서 **샘플 시도** 섹션을 클릭 합니다.
* 네트워크 3D 프린터 샘플 앱을 선택 합니다.

   ![3D 네트워크 프린터 설치](../media/3dprintserver/dashboard-samples.png)

* 3D 프린터 모델을 선택 하 고 **배포 및 실행** 단추를 눌러 앱을 IoT Core 장치에 배포 합니다. 

    ![3D 네트워크 프린터 설치](../media/3dprintserver/dashboard-app.png)

    [Aleph 개체인 i n c.](https://www.alephobjects.com/) 의 [Lulzbot taz 6 이미지](http://devel.lulzbot.com/TAZ/Olive/photos/TAZ_6_Angle_Rock2pus_transparent.png) 는 [CC by-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/)에 따라 사용이 허가 됩니다.
    
    사용자 지정 프린터를 설치 하려는 경우 프린터 목록에서 "사용자 지정" 옵션을 선택 합니다. 사용자 지정 3d 프린터에는 3d 프린터에 올바르게 연결 하 여 인쇄 하기 위해 제공 되는 PrintDeviceCapabilities 파일 이라는 구성 xml이 필요 합니다. 샘플 PrintDeviceCapabilities 파일은 여기에서 찾을 수 있습니다 https://docs.microsoft.com/windows-hardware/drivers/3dprint/sample-configuration-xml
   
   Xml 파일에서 수행 해야 하는 최소 변경 내용은 다음 섹션을 호환 프린터와 관련 된 올바른 값으로 업데이트 하는 것입니다.

이러한 값은 3d 모델을 처리할 때 슬라이서에 대 한 3d 프린터의 인쇄 평판 크기를 지정 합니다.

    <psk3d:Job3DOutputAreaWidth>200000</psk3d:Job3DOutputAreaWidth>
    <psk3d:Job3DOutputAreaDepth>200000</psk3d:Job3DOutputAreaDepth>
    <psk3d:Job3DOutputAreaHeight>200000</psk3d:Job3DOutputAreaHeight>


Psk3dx: 전송 전 xml 태그의 값은 raspberry pi3에서 3d 프린터와 통신 하는 동안 사용할 특정 전송 속도를 제어 합니다. 3d 프린터와 관련 된 적절 한 전송 속도를 설정 합니다. 

```
\<psk3dx:baudrate\>115200</psk3dx:baudrate>
```

PrintDeviceCapabilities xml의 다른 값은 특정 호환 프린터를 사용 하 여 작동 하는 방식을 세밀 하 게 조정 하기 위해 3d 인쇄 드라이버에서 슬라이서에 알리는 데 사용 됩니다.
이러한 모든 값에 대 한 자세한 내용은 [여기](https://docs.microsoft.com/windows-hardware/drivers/3dprint/slicer-settings)에서 제공 됩니다.

    
    
## <a name="4-add-your-3d-printer"></a>4.3D 프린터를 추가 합니다.
___
* Windows 10 PC로 이동 하 고 **설정** -> **장치** -> **프린터 & 스캐너**로 이동 합니다.
* **프린터 또는 스캐너 추가**를 누릅니다.

     ![Windows 설정 장치 추가](../media/3dprintserver/add-printer.png)

* 3D 프린터를 선택 하 고 **장치 추가**를 누릅니다. 프린터가 자동으로 설치 됩니다.

     ![Windows 설정 장치 추가](../media/3dprintserver/add-device.png)

이제 프린터가 설치 되었으며 USB 케이블로 연결 된 것 처럼 동작 합니다.
이제 [3D 작성기](https://msdn.microsoft.com/windows/hardware/mt561568.aspx)를 사용 하 여 인쇄할 수 있습니다.
