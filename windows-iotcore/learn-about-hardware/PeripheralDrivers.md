---
title: USB 주변 장치 드라이버 설치
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 드라이버 패키지를 만들고 장치에 타사 드라이버를 설치 하는 방법에 대해 알아봅니다.
keywords: windows iot, USB 드라이버, 주변 장치, USB
ms.openlocfilehash: dd7eec9defc676bb84efe988d771794d9bb7c9ef
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "60170931"
---
# <a name="install-usb-peripheral-drivers"></a>USB 주변 장치 드라이버 설치
USB 모바일 광대역 모뎀, 프린터, 스캐너 등의 주변 장치에 대 한 타사 드라이버 (usb)를 추가 하려면 다음 단계를 수행 합니다. 

## <a name="step-1-get-drivers-from-pc"></a>1단계: PC에서 드라이버 가져오기
___
이 단계는 PC에서 x86 버전의 드라이버를 가져오는 것입니다. ARM의 경우 sys/inf 파일을 가져오려면 주변 장치의 공급 업체에 문의 하세요.


1. Windows PC에 장치 연결

2. PC에 장치에 대 한 드라이버를 설치 합니다.

3. Device Manager로 이동 하 고이 장치 (유니버설 직렬 버스 컨트롤러 아래에 나열 됨)를 선택한 후 마우스 오른쪽 단추를 클릭 하 고 속성을 선택 합니다.

4. 속성 창에서 드라이버 탭으로 이동 하 여 드라이버 세부 정보를 클릭 합니다. 여기에는 sys 파일이 나열 되어 있습니다.

5. 에서 sys 파일 `C:\Windows\system32` 을 복사 하 고에서 `C:\Windows\Inf`관련 inf 파일도 복사 합니다. `.inf` 파일에서 sys 파일 참조를 searcing 하 여 inf 파일을 찾을 수 있습니다. Inf에 나열 된 추가 파일을 복사 해야 할 수 있습니다. 이러한 파일은 다음 단계에서를 사용할 `inf2pkg.cmd` 때 생성 되는 inf_filelist 파일에 나열 됩니다.


## <a name="step-2-create-a-driver-package"></a>2단계: 드라이버 패키지 만들기
___

드라이버 패키지에는 드라이버의 Inf 파일에 대 한 참조 (InfSource)가 포함 되며, Inf 파일에서 참조 되는 모든 파일도 나열 됩니다. [새 IoTDriverPackage 패키지](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools/IoTCoreImaging/Docs/Add-IoTDriverPackage.md)를 사용 하 여 드라이버를 제작할 수 있습니다.

[IoTInf2Cab](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools/IoTCoreImaging/Docs/New-IoTInf2Cab.md) 는 패키지 xml 파일을 만들고 cab 파일도 직접 빌드합니다.

> [!NOTE]
> Windows IoT Core는 [범용 INF 및 범용 드라이버만](https://docs.microsoft.com/en-us/windows-hardware/drivers/develop/getting-started-with-universal-drivers)지원 합니다.


참고 항목: [샘플 드라이버 패키지](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/BSP/CustomRpi2/Packages/CustomRPi2.GPIO) 

## <a name="step-3-install-on-device"></a>3단계: 장치에 설치
___

* 장치에 연결 ([SSH 사용](../connect-your-device/ssh.md) 또는 [Powershell 사용](../connect-your-device/powershell.md))
* 폴더에 .cab 파일을 복사 합니다(예:c:\oeminstall).<filename>
* 을 사용 하 여 `applyupdate -stage C:\OemInstall\<filename>.cab`패키지 준비를 시작 합니다. 설치할 패키지가 여러 개 있는 경우이 단계는 각 패키지에 대해 반복 됩니다.
* 를 사용 하 여 `applyupdate -commit`패키지를 커밋합니다.

장치를 업데이트 OS (기어 표시)로 다시 부팅 하 여 패키지를 설치 하 고 다시 주 OS로 다시 부팅 합니다. 이 프로세스는 몇 분 정도 걸릴 수 있습니다.

## <a name="step-4-check-status-of-driver"></a>4단계: 드라이버 상태 확인
___

* [Powershell](../connect-your-device/PowerShell.md) 시작
* 다음 Powershell commandlet을 사용 하 여 설치 된 드라이버의 상태를 가져올 수 있습니다.

    * [Pnp 장치](https://docs.microsoft.com/powershell/module/pnpdevice/get-pnpdevice?view=win10-ps)
    * [PnpDeviceProperty](https://docs.microsoft.com/powershell/module/pnpdevice/get-pnpdeviceproperty?view=win10-ps)
    
