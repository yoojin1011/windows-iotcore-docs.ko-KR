---
title: Windows 10 IoT Core 사용 하 여 네트워크 3D 프린터
author: saraclay
ms.author: saclayt
ms.date: 09/05/17
ms.topic: article
description: 인쇄 서버에 Windows 10 IoT Core 장치를 사용 하 여 3D 프린터에 연결 하는 방법을 알아봅니다.
keywords: windows iot, 3D, 3D 프린터, 인쇄 서버, 네트워크 3D 프린터
ms.openlocfilehash: 7a9bcc7871c62be5a73319ca284127ee4abc42f5
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512374"
---
# <a name="network-3d-printer-with-windows-10-iot-core"></a>Windows 10 IoT Core 사용 하 여 네트워크 3D 프린터

인쇄 서버에 Windows 10 IoT Core 장치를 설정 하 고 3D 프린터 연결 합니다. 다른 장치에서 프린터를 무선으로 액세스할 수 없게 됩니다.

## <a name="1-install-windows-10-iot-core-on-your-device"></a>1. Windows 10 IoT Core 장치에 설치
___
시작 하기 전에 해야 합니다.

* 최신 버전의 Windows 10 IoT Core Insider Preview 설치를 사용 하 여 보드입니다. 에 따라 합니다 [시작 가이드](https://developer.microsoft.com/en-us/windows/iot/getstarted) IoT 대시보드 앱 및 Windows 10 IoT Core 설치 합니다.
* 네트워크 3D 프린터 앱 호환 3D 프린터:

    * Lulzbot Taz 6
    * Makergear M2
    * 더하기 및 간단한 Printrbot Play
    * Prusa i3 Mk2
    * Ultimaker 원래 값과 원래 +
    * Ultimaker 2, 2 +
    * Ultimaker 2 확장 및 확장 +
    * CraftBot 2
    * CraftBot 더하기
    * LulzBot 미니
    * Velleman K8200

## <a name="2-connect-your-3d-printer-to-your-device"></a>2. 3D 프린터 장치에 연결
___
* 플러그 인에 Windows 10 IoT Core 3D 프린터 보드는 USB 케이블을 사용 합니다.

    ![3D 프린터 장치에 연결](../media/3DPrintServer/connect-3d-printer.png)

* IoT 대시보드 앱을 열고 장치에 표시 되는지 확인 합니다 **내 장치** 탭 합니다.

    ![장치의 IoT 대시보드에서 표시 되는지 확인 합니다.](../media/3DPrintServer/selectDevice.png)
    
## <a name="3-deploy-the-network-3d-printer-app"></a>3. 네트워크를 배포 3D 프린터 앱
___
* IoT 대시보드에서 다음을 클릭 합니다 **몇 가지 샘플을 시험해 볼** 섹션입니다.
* 네트워크 3D 프린터 샘플 앱을 선택 합니다.

   ![3D 네트워크 프린터를 설치 합니다.](../media/3dprintserver/dashboard-samples.png)

* 3D 프린터 모델 및 키를 눌러 선택 합니다 **배포 및 실행** IoT Core 장치에 앱을 배포 하는 단추입니다. 

    ![3D 네트워크 프린터를 설치 합니다.](../media/3dprintserver/dashboard-app.png)

    [LulzBot TAZ 6 이미지](http://devel.lulzbot.com/TAZ/Olive/photos/TAZ_6_Angle_Rock2pus_transparent.png) 하 여 [Aleph 개체, Inc.](https://www.alephobjects.com/) 사용이 허가 됩니다 [CC BY SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/)합니다.
    
    프린터 목록에서 사용자 지정 프린터 선택 "사용자 지정" 옵션을 설치 하려면. 사용자 지정 3d 프린터 호출 PrintDeviceCapabilities.xml 파일을 올바르게 연결 하 고 3d 프린터에 인쇄를 제공 해야 하는 구성 xml을 해야 합니다. 샘플 PrintDeviceCapabilities.xml 파일을 확인할 수 있습니다. https://docs.microsoft.com/windows-hardware/drivers/3dprint/sample-configuration-xml
   
   Xml 파일에서 해야 할 최소 변경 내용을 다음 섹션에서는 특정 호환 프린터에 올바른 값으로 업데이트 되도록 합니다.

3d 모델을 처리할 때 이러한 값에 슬라이서에 3d 프린터의 인쇄 평판 크기 지정

    <psk3d:Job3DOutputAreaWidth>200000</psk3d:Job3DOutputAreaWidth>
    <psk3d:Job3DOutputAreaDepth>200000</psk3d:Job3DOutputAreaDepth>
    <psk3d:Job3DOutputAreaHeight>200000</psk3d:Job3DOutputAreaHeight>


Psk3dx:baudrate xml 태그에 값 raspberry pi3에서 3d 프린터와 통신 하는 동안 사용할 특정 전송 속도 제어 합니다. 3d 프린터 관련 적절 한 전송 속도 설정 합니다. 

```
\<psk3dx:baudrate\>115200</psk3dx:baudrate>
```

PrintDeviceCapabilities xml에 다른 값은 3d 인쇄 드라이버에서 특정 호환 프린터를 사용 하 여 작동 방법을 미세 조정 하려면 슬라이서를 알리는 데 사용 됩니다.
자세한 내용은 이러한 값을 제공 하는 모든 [여기](https://docs.microsoft.com/windows-hardware/drivers/3dprint/slicer-settings)합니다.

    
    
## <a name="4-add-your-3d-printer"></a>4. 3D 프린터를 추가 합니다.
___
* Windows 10 PC로 이동할 **설정을** -> **장치** -> **프린터 및 스캐너**합니다.
* 키를 눌러 **프린터 또는 스캐너 추가**합니다.

     ![장치를 추가 하는 Windows 설정](../media/3dprintserver/add-printer.png)

* 3D 프린터 및 키를 눌러 선택할 **장치 추가**합니다. 프린터를 자동으로 설치 합니다.

     ![장치를 추가 하는 Windows 설정](../media/3dprintserver/add-device.png)

프린터는 이제 설치 하는 축을 선택 하 고 USB 케이블을 사용 하 여 연결 된 것 처럼 정확 하 게 작동 합니다.
이제 사용 하 여 인쇄할 수 있습니다 [3D 작성기](https://msdn.microsoft.com/windows/hardware/mt561568.aspx)합니다.
