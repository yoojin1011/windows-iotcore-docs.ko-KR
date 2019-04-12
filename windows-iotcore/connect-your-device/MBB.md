---
title: 모바일 광대역 연결
author: saraclay
ms.author: saclayt
ms.date: 06/12/18
ms.topic: article
description: 모바일 광대역 연결에 대 한 Windows 10 IoT Core 사용 하는 방법에 알아봅니다.
keywords: windows iot, MBB, 모바일 광대역 연결
ms.openlocfilehash: 3afa48e049e38f7e26308434ba6f7349ac0be050
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513574"
---
## <a name="mobile-broadband-connection"></a>모바일 광대역 연결

모바일 광대역 연결에서 지원 됩니다 [Windows 10 IoT Core](http://windowsondevices.com)합니다. IoT 게이트웨이 모바일 광대역 모뎀 모듈을 지 원하는 경우 사용할 수는 `MBBConnect` IoT Core의 모바일 광대역 연결에 대 한 설정 구성을 데 유용한 도구입니다.

`MBBConnect` 구독자 ID, SIM ICC ID, 인터페이스 이름 및 홈 공급자 이름 등의 연결에 대 한 관련 정보를 검색합니다. 그런 다음 연결 프로필을 만듭니다. 수행 해야 하는 작업만 APN을 제공 하기 이며 자동으로 연결을 설정 합니다.

`MBBConnect` 개발 되 고 사용 하 여 테스트 MinnowBoard 최대 기반 IoT Core를 실행 16299 버전과 모바일 광대역 모뎀 모듈 SIM 카드를 사용 하 여 대만에서 주요 telecom 공급자에서 IoT 게이트웨이.

### <a name="usage"></a>사용법

1. 복사 `MBBConnect.exe` IoT 게이트웨이에 있습니다.

   * [FTP](https://docs.microsoft.com/windows/iot-core/connect-your-device/ftp)

2. Powershell 또는 SSH에서 게이트웨이 연결 합니다.

   * [PowerShell](https://docs.microsoft.com/windows/iot-core/connect-your-device/powershell)

   * [SSH](https://docs.microsoft.com/windows/iot-core/connect-your-device/SSH)

3. 폴더로 전환 하 고 있는 `MBBConnect.exe` 위치한 합니다. 
   ```
   Command: MBBConnect.exe <APN name>
   <APN name>: It depends on your SIM card’s provider. 
   ```

### <a name="example"></a>예제
아래 예제에서는 PowerShell에서 MBBConnect.exe를 사용합니다. SIM 카드의 APN "Internet" 인 경우 사용 하는 예를 들어 `MBBConnect.exe Internet` 연결 합니다.
 
출력 메시지 흐름에 표시 됩니다.

* 상태는 연결 되지 않은에서 연결 됨으로 변경 됩니다. 

* WWAN 네트워크가 성공적으로 구성 됩니다.

모바일 광대역 연결에 대 한 샘플 시도 [여기](https://github.com/ms-iot/iot-utilities/tree/master/MBBConnect)합니다.
