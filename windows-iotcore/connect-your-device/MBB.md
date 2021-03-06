---
title: 모바일 광대역 연결
ms.date: 06/12/2018
ms.topic: article
description: Windows 10 IoT Core에 대해 모바일 광대역 연결을 사용 하는 방법을 알아봅니다.
keywords: windows iot, MBB, 모바일 광대역 연결
ms.openlocfilehash: 2bf9a153fb77ab7f92bad727847cdf581d0b7729
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918340"
---
# <a name="mobile-broadband-connection"></a>모바일 광대역 연결

모바일 광대역 연결은 [Windows 10 IoT Core](http://windowsondevices.com)에서 지원 됩니다. IoT 게이트웨이가 모바일 광대역 모뎀 모듈을 지 원하는 경우 `MBBConnect` 도구를 사용 하 여 IoT Core의 모바일 광대역 연결에 대 한 구성을 설정할 수 있습니다.

`MBBConnect`는 구독자 ID, SIM ICC ID, 인터페이스 이름 및 홈 공급자 이름과 같은 연결 관련 정보를 검색 합니다. 그런 다음 연결 프로필을 만듭니다. APN을 제공 하기만 하면 자동으로 연결을 설정 하 게 됩니다.

`MBBConnect`는 IoT Core 버전 16299을 실행 하는 MinnowBoard Max 기반 IoT gateway와, 주 통신 공급자 (대만)의 SIM 카드가 있는 모바일 광대역 모뎀 모듈을 사용 하 여 개발 및 테스트 됩니다.

### <a name="usage"></a>사용 패턴

1. IoT gateway에 `MBBConnect.exe`를 복사 합니다.

   * [FTP](https://docs.microsoft.com/windows/iot-core/connect-your-device/ftp)

2. Powershell 또는 SSH를 통해 게이트웨이를 연결 합니다.

   * [PowerShell](https://docs.microsoft.com/windows/iot-core/connect-your-device/powershell)

   * [SSH](https://docs.microsoft.com/windows/iot-core/connect-your-device/SSH)

3. `MBBConnect.exe` 있는 폴더로 전환 합니다. 
   ```
   Command: MBBConnect.exe <APN name>
   <APN name>: It depends on your SIM card’s provider. 
   ```

### <a name="example"></a>예
아래 예제에서는 PowerShell에서 MBBConnect .exe를 사용 합니다. 예를 들어 SIM 카드의 APN이 "Internet" 인 경우 `MBBConnect.exe Internet`를 사용 하 여 연결 합니다.
 
출력 메시지에 흐름이 표시 됩니다.

* 상태가 연결 됨에서 연결 됨으로 변경 됩니다. 

* WWAN 네트워크를 구성 했습니다.

[여기](https://github.com/ms-iot/iot-utilities/tree/master/MBBConnect)에서 모바일 광대역 연결에 대 한 샘플을 사용해 보세요.
