---
title: 모바일 광대역 연결
author: saraclay
ms.author: saclayt
ms.date: 06/12/18
ms.topic: article
description: Windows 10 IoT Core에 대해 모바일 광대역 연결을 사용 하는 방법을 알아봅니다.
keywords: windows iot, MBB, 모바일 광대역 연결
ms.openlocfilehash: 3afa48e049e38f7e26308434ba6f7349ac0be050
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "60168051"
---
## <a name="mobile-broadband-connection"></a>모바일 광대역 연결

모바일 광대역 연결은 [Windows 10 IoT Core](http://windowsondevices.com)에서 지원 됩니다. Iot 게이트웨이가 모바일 광대역 모뎀 모듈을 지 원하는 경우이 `MBBConnect` 도구를 사용 하 여 iot Core의 모바일 광대역 연결에 대 한 구성을 설정할 수 있습니다.

`MBBConnect`구독자 ID, SIM ICC ID, 인터페이스 이름 및 홈 공급자 이름과 같은 연결 관련 정보를 검색 합니다. 그런 다음 연결 프로필을 만듭니다. APN을 제공 하기만 하면 자동으로 연결을 설정 하 게 됩니다.

`MBBConnect`은 (는) MinnowBoard Max 기반 IoT gateway를 사용 하 여 IoT Core 버전 16299을 실행 하 고, 주 통신 공급자의 SIM 카드를 사용 하는 모바일 광대역 모뎀 모듈을 사용 하도록 개발 및 테스트 됩니다.

### <a name="usage"></a>사용법

1. IoT `MBBConnect.exe` gateway로 복사 합니다.

   * [FTP](https://docs.microsoft.com/windows/iot-core/connect-your-device/ftp)

2. Powershell 또는 SSH를 통해 게이트웨이를 연결 합니다.

   * [PowerShell](https://docs.microsoft.com/windows/iot-core/connect-your-device/powershell)

   * [SSH](https://docs.microsoft.com/windows/iot-core/connect-your-device/SSH)

3. `MBBConnect.exe` 가 있는 폴더로 전환 합니다. 
   ```
   Command: MBBConnect.exe <APN name>
   <APN name>: It depends on your SIM card’s provider. 
   ```

### <a name="example"></a>예제
아래 예제에서는 PowerShell에서 MBBConnect .exe를 사용 합니다. 예를 들어 SIM 카드의 APN이 "Internet" 인 경우를 사용 `MBBConnect.exe Internet` 하 여 연결 합니다.
 
출력 메시지에 흐름이 표시 됩니다.

* 상태가 연결 됨에서 연결 됨으로 변경 됩니다. 

* WWAN 네트워크를 구성 했습니다.

[여기](https://github.com/ms-iot/iot-utilities/tree/master/MBBConnect)에서 모바일 광대역 연결에 대 한 샘플을 사용해 보세요.
