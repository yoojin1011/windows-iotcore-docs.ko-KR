---
title: DISM을 사용 하 여 Windows 10 IoT Core
author: bfjelds
ms.author: bfjelds
ms.date: 08/28/2017
ms.topic: article
description: Windows 10 IoT Core 마이크로 SD 카드를 DISM을 사용 하는 방법에 알아봅니다.
keywords: windows iot, DISM, SD 카드, flash, 운영 체제 배포 이미지 서비스 관리
ms.openlocfilehash: 1fd075037b97399762aea1b0b844a477337cbc5d
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59515236"
---
# <a name="use-dism-to-flash-windows-10-iot-core"></a>DISM을 사용 하 여 Windows 10 IoT Core

> [!NOTE]
> DISM 오프 라인 지원 되지 않습니다. IoT core는 FFU를 탑재 하려고 하면 아래 오류를 받습니다. 요청이 지원 되지 않습니다.
> 이미지 이름을 없고 현재 지원 되지 않는 모바일/Onecore FFU, 될 가능성이 높습니다.
> FfuMountImage #160 0x80070032 실패 했습니다.

## <a name="an-alternative-method-to-iot-dashboard-for-flashing-a-ffu"></a>깜박이 FFU에 대 한 IoT 대시보드에 대체 메서드

배포 이미지 서비스 및 Management(Dism.exe) SD 카드에 Windows 10 IoT Core 사용할 수 있습니다. 장치 형식에 해당 하는 FFU 이미지 파일을 해야 합니다. 

* 관리자 명령 프롬프트를 열고 로컬 flash.ffu 파일에 포함 된 폴더로 이동 합니다.

* 컴퓨터에 SD 카드를 플러그 인입니다. 

* 컴퓨터에 SD 카드에는 디스크 수를 찾습니다.  다음 단계에서는 이미지를 적용 하는 경우이 사용 됩니다.  이렇게 하려면 diskpart 유틸리티를 사용할 수 있습니다.  다음 명령을 실행 합니다.

        c:\FFUFolder>diskpart

        DISKPART>list disk

    컴퓨터에 연결 하는 모든 저장 장치를 나열 해야 합니다. 

    ![DISM List Disk](../media/Dism/DiskpartListDisk.png)

    디스크 번호를 확인 하 고 종료 하려면 종료 diskpart를 입력 합니다. 

        DISKPART>exit

* 다음 명령을 실행 하 여 SD 카드에 이미지를 적용할 관리자 명령 프롬프트를 사용 하 여 (이 경우에 SD 카드 이므로 디스크 수 4를 사용 하 여, PhysicalDriveN 예를 들어 이전 단계에서 찾은 값으로 대체 해야 `/ApplyDrive:\\.\PhysicalDrive4` 아래)

        dism.exe /Apply-Image /ImageFile:"[FULLPATH]\flash.ffu" /ApplyDrive:\\.\PhysicalDriveN /SkipPlatformCheck

* 작업 트레이에 "안전 하 게 하드웨어 제거" 아이콘을 클릭 하 고 안전 하 게 시스템에서 제거 하려면 USB SD 카드 판독기를 선택 합니다.  이렇게 하면 이미지 손상을 시킬 수 있습니다.
