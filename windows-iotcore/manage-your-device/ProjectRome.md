---
title: Windows 10 IoT Core에서 Project 로마 사용
ms.date: 11/14/2017
ms.topic: article
description: Windows IoT 장치를 출시 하는 단계를 알아보고 파악 합니다.
keywords: windows 10 IoT Core, 프로젝트 로마, 원격 장치
ms.openlocfilehash: dcf1ba9bec776b2ebde0d374266bb4d7dba3baec
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72917315"
---
# <a name="using-project-rome-with-windows-10-iot-core"></a>Windows 10 IoT Core에서 Project 로마 사용 
 
[프로젝트 로마](https://developer.microsoft.com/en-us/windows/project-rome) 를 사용 하면 RemoteSystems 및 AppServiceProvider api를 사용 하 여 Windows 10 IoT Core를 실행 하는 장치에서 원격으로 작업할 수 있습니다. 
 
이 문서에서는 Project 로마를 사용 하 여 Windows 10 IoT Core를 실행 하는 장치를 검색, 제어 및 연결 하는 방법을 설명 합니다.  
 
## <a name="discovering-iot-core-devices-with-the-remotesystem-apis"></a>RemoteSystem Api를 사용 하 여 IoT Core 장치 검색 
 
_설치_
* Microsoft 계정에 로그인 한 상태에서 바탕 화면에서 RemoteSystems 샘플을 실행 합니다.  
* IoT Core에서 실행 되는 앱이 없는 경우 Cortana로 이동 하 여 로그인으로 이동 하 여 Microsoft 계정에 로그인 합니다. 
 
_위한_
1. 바탕 화면에서 RemoteSystems 샘플 실행 
2. "1" 검색에서 "시스템 검색"을 클릭 합니다. 

![시스템 검색](../media/ProjectRome/SearchForSystems.gif)
 
## <a name="control-iot-core-devices-with-remotesystemslaunchuri"></a>RemoteSystems Uri를 사용 하 여 IoT Core 장치 제어 
 
_설치_
* [Microsoft 계정에 로그인](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WebAccountManagement)한 상태에서 바탕 화면에서 [RemoteSystems 샘플](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/RemoteSystems) 을 실행 합니다.
* IoT Core에서 실행 되는 앱이 없는 경우 Cortana로 이동 하 여 로그인으로 이동 하 여 Microsoft 계정에 로그인 합니다. 
 
_위한_
1. Cortana를 사용 하 여 IoT Core 가상 머신을 켜고 Cortana에서 Microsoft 계정에 로그인 합니다. 
2. 바탕 화면에서 RemoteSystems 샘플을 실행 합니다. 
3. "1) 검색"에서 "시스템 검색"을 클릭 합니다. 
4. "2) 시작 URI"에서 Cortana를 실행 하는 IoT Core 장치를 선택 합니다. 
5. 이 URI를 입력 하 고 시작 합니다. 

![시작 URI](../media/ProjectRome/LaunchURI.gif)

## <a name="connecting-to-the-remote-app-service-running-on-iot-core"></a>IoT Core에서 실행 되는 원격 App Service에 연결 
_설치_
* [Microsoft 계정에 로그인](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WebAccountManagement)한 상태에서 바탕 화면에서 [RemoteSystems 샘플](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/RemoteSystems) 을 실행 합니다. 
* [AppServiceProvider 앱](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/AppServices) 이 하나 이상의 IoT Core 장치에 배포 되 고 실행 중인지 확인 합니다. 
 
_위한_
1. Cortana를 사용 하 여 IoT Core 가상 머신을 켜고 Cortana에서 Microsoft 계정에 로그인 합니다. AppServiceProvider 앱을 배포 하 고 한 번 실행 한 후 종료 합니다. 
2. 바탕 화면에서 RemoteSystems 샘플을 실행 합니다. 
3. "1) 검색"에서 "시스템 검색"을 클릭 합니다. 
4. "3) 시작 App Services에서" AppServiceProvider 앱을 배포 하 고 이전에 실행 한 IoT core 장치를 선택 합니다. 
5. 난수를 생성 합니다.  

![시작 App Services](../media/ProjectRome/LaunchAppServices.gif)
 
## <a name="controlling-other-devices-and-app-services-from-an-iot-core-device"></a>IoT Core 장치에서 기타 장치 및 앱 서비스 제어 

_설치_
* Cortana 앱에서 [Microsoft 계정에 로그인](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WebAccountManagement) 한 상태에서 IoT Core 장치에 배포 된 [RemoteSystems 샘플](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/RemoteSystems) 을 실행 합니다. 
* [AppServiceProvider 앱](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/AppServices) 을 사용 하 여 데스크톱 컴퓨터를 배포 하 고 한 번 이상 실행 했습니다. 
 
_위한_
1. RemoteSystems 샘플을 실행 합니다. 
2. "1) 검색"에서 "시스템 검색"을 클릭 합니다. 
3. "2) 시작 URI"에서 데스크톱 컴퓨터를 선택 하 고를 시작 합니다. 
4. "3) 시작 App Services"에서 데스크톱 컴퓨터를 선택 합니다.  
 
> [!NOTE] 
> 처음 시도 하면 시간이 오래 걸릴 수 있습니다. 훨씬 더 빠른 응답을 위해 다시 시도 하세요. 
 
### <a name="helpful-links"></a>유용한 링크: 
* [MSDN의 Project 로마 설명서](https://developer.microsoft.com/en-us/windows/project-rome )
* [UWP 용 Project 로마 사용](https://docs.microsoft.com/windows/uwp/launch-resume/connected-apps-and-devices )
 
