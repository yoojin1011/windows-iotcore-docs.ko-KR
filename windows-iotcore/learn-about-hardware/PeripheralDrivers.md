---
title: USB 주변 장치 드라이버 설치
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 드라이버 패키지 만들기 및 장치에 타사 드라이버를 설치 하는 방법에 알아봅니다.
keywords: windows iot, USB 드라이버, USB 주변 장치
ms.openlocfilehash: dd7eec9defc676bb84efe988d771794d9bb7c9ef
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513582"
---
# <a name="install-usb-peripheral-drivers"></a>USB 주변 장치 드라이버 설치
타사 드라이버 (usb) USB 모바일 광대역 모뎀, 프린터, 스캐너 등과 같은 주변 장치에 대 한 추가 하려면 다음 단계를 수행 합니다. 

## <a name="step-1-get-drivers-from-pc"></a>1단계: PC에서 드라이버를 가져오려면
___
X86을 가져오려는 단계는 PC에서 드라이버의 버전입니다. ARM, sys/inf 파일을 가져올 주변 장치 공급 업체에 문의 하세요.


1. Windows PC에 장치 연결

2. PC에 장치 드라이버를 설치 합니다.

3. 장치 관리자, (범용 직렬 버스 컨트롤러 아래 나열 됨)이이 장치를 선택 하 고 마우스 오른쪽 단추로 클릭를 속성을 선택 합니다.

4. 속성 창에서 드라이버 탭으로 이동한 다음 드라이버 세부 정보 클릭 합니다. 참고 sys 파일을 나열 합니다.

5. Sys 파일을 복사할 `C:\Windows\system32` 및에서 관련된 inf 파일 또한 `C:\Windows\Inf`합니다. 찾을 수 있습니다 inf 파일에서 검색 해 보십시오는 sys 파일 참조는 `.inf` 파일입니다. Inf에 나열 된 추가 파일을 복사 해야 하 고 사용 하는 경우 만든 inf_filelist.txt 파일에 나열 됩니다 `inf2pkg.cmd` 다음 단계에서 합니다.


## <a name="step-2-create-a-driver-package"></a>2단계: 드라이버 패키지 만들기
___

드라이버 패키지는 드라이버의 Inf 파일에 대 한 참조 (InfSource)를 포함 하 고 또한 Inf 파일에서 참조 하는 모든 파일을 나열 합니다. 드라이버를 작성할 수 있습니다. wm.xml를 사용 하 여 [새로 만들기-IoTDriverPackage](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools/IoTCoreImaging/Docs/Add-IoTDriverPackage.md)합니다.

[새 IoTInf2Cab](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools/IoTCoreImaging/Docs/New-IoTInf2Cab.md) 패키지 xml 파일을 만들고 cab 파일을 직접 빌드합니다.

> [!NOTE]
> Windows IoT Core 지원 [범용 INF 및 범용 드라이버](https://docs.microsoft.com/en-us/windows-hardware/drivers/develop/getting-started-with-universal-drivers)합니다.


참고 항목: [샘플 드라이버 패키지](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/BSP/CustomRpi2/Packages/CustomRPi2.GPIO) 

## <a name="step-3-install-on-device"></a>3단계: 장치 설치
___

* 장치에 연결 ([SSH를 사용 하 여](../connect-your-device/ssh.md) 하거나 [Powershell을 사용 하 여](../connect-your-device/powershell.md))
* 복사를 <filename>.cab 파일 디렉터리로 장치로 가정해 C:\OemInstall
* 사용 하 여 패키지 준비 시작 `applyupdate -stage C:\OemInstall\<filename>.cab`합니다. 여러 패키지를 설치 해야 하는 경우이 단계는 각 패키지에 대해 반복 합니다.
* 사용 하 여 패키지를 커밋 `applyupdate -commit`합니다.

장치가는 업데이트 패키지를 설치 하려면 OS (보여 주는 gears)으로 다시 부팅 됩니다 하 고 기본 OS를 다시 부팅 됩니다. 이 프로세스는 몇 분 정도 걸릴 수 있습니다.

## <a name="step-4-check-status-of-driver"></a>4단계: 드라이버의 상태를 확인 합니다.
___

* 시작 된 [Powershell](../connect-your-device/PowerShell.md)
* 다음 Powershell commandlet을 사용 하 여 설치 된 드라이버의 상태를 가져올 수 있습니다.

    * [Get-PnpDevice](https://docs.microsoft.com/powershell/module/pnpdevice/get-pnpdevice?view=win10-ps)
    * [Get-PnpDeviceProperty](https://docs.microsoft.com/powershell/module/pnpdevice/get-pnpdeviceproperty?view=win10-ps)
    
