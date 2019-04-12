---
title: Windows 10 IoT Core 사용 하 여 프로젝트 로마를 사용 하 여
author: saraclay
ms.author: saclayt
ms.date: 11/14/2017
ms.topic: article
description: 알아보고 출시 Windows IoT 장치를 수행 하는 단계를 이해 합니다.
keywords: windows 10 IoT Core, 프로젝트 로마 원격 장치
ms.openlocfilehash: cc016abad05dd54c7b948bcae8120b6da1724ee0
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59515051"
---
# <a name="using-project-rome-with-windows-10-iot-core"></a>Windows 10 IoT Core 사용 하 여 프로젝트 로마를 사용 하 여 
 
[로마 프로젝트](https://developer.microsoft.com/en-us/windows/project-rome) RemoteSystems 및 AppServiceProvider Api를 사용 하 여 Windows 10 IoT Core 실행 하는 장치를 원격으로 작업할 수 있습니다. 
 
이 문서에서는 컨트롤을 검색 하 고 프로젝트 로마를 사용 하 여 Windows 10 IoT Core 실행 하는 장치에 연결 하는 방법을 살펴봅니다.  
 
## <a name="discovering-iot-core-devices-with-the-remotesystem-apis"></a>RemoteSystem Api를 사용 하 여 IoT Core 장치를 검색합니다. 
 
_설정:_
* Microsoft 계정에 로그인 하는 동안 데스크톱에서 RemoteSystems 샘플을 실행 합니다.  
* IoT Core에서 실행 중인 앱이 없음를 사용 하 여 로그인에 Cortana로 이동 하 여 Microsoft 계정에 로그인 합니다. 
 
_단계:_
1. 바탕 화면에 RemoteSystems 샘플을 실행 합니다. 
2. "1) 검색에"에서 "시스템에 대 한 검색"를 클릭 합니다. 

![시스템에 대 한 검색](../media/ProjectRome/SearchForSystems.gif)
 
## <a name="control-iot-core-devices-with-remotesystemslaunchuri"></a>RemoteSystems.LaunchUri 사용 하 여 IoT Core 장치를 제어 합니다. 
 
_설정:_
* 실행 합니다 [RemoteSystems 샘플](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/RemoteSystems) 데스크톱 잠시에 [Microsoft 계정 로그인](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WebAccountManagement)합니다.
* IoT Core에서 실행 중인 앱이 없음를 사용 하 여 로그인에 Cortana로 이동 하 여 Microsoft 계정에 로그인 합니다. 
 
_단계:_
1. Cortana 및 Cortana에서 Microsoft 계정의 로그인을 사용 하 여 IoT Core 가상 컴퓨터를 켭니다. 
2. 데스크톱에서 RemoteSystems 샘플을 실행 합니다. 
3. "1) 검색", "시스템에 대 한 검색"을 클릭 합니다. 
4. "2) 시작 URI" 아래에서 Cortana를 실행 하는 IoT Core 장치를 선택 합니다. 
5. 이 URI와 실행을 입력 합니다. 

![시작 URI](../media/ProjectRome/LaunchURI.gif)

## <a name="connecting-to-the-remote-app-service-running-on-iot-core"></a>IoT Core에서 실행 중인 원격 App Service에 연결 
_설정:_
* 실행 합니다 [RemoteSystems 샘플](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/RemoteSystems) 데스크톱 잠시에 [Microsoft 계정 로그인](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WebAccountManagement)합니다. 
* 되었는지 확인 합니다 [AppServiceProvider 앱](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/AppServices) 하나 이상의 IoT Core 장치에서 실행 되 고 배포 합니다. 
 
_단계:_
1. Cortana 사용 하 여 IoT 코어 가상 머신에서에서 설정 및 Cortana에서 Microsoft 계정에 로그인 합니다. AppServiceProvider 앱 배포, 한 번 실행 한 다음 종료 합니다. 
2. 데스크톱에서 RemoteSystems 샘플을 실행 합니다. 
3. "1) 검색", "시스템에 대 한 검색"을 클릭 합니다. 
4. "3) 시작 App services 에서" IoT core 장치 AppServiceProvider 앱이 배포 된 이전에 실행을 선택 합니다. 
5. 난수를 생성 합니다.  

![App Services 시작](../media/ProjectRome/LaunchAppServices.gif)
 
## <a name="controlling-other-devices-and-app-services-from-an-iot-core-device"></a>다른 장치 및 IoT Core 장치에서 앱 서비스를 제어합니다. 

_설정:_
* 실행 합니다 [RemoteSystems 샘플](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/RemoteSystems) 하는 동안 IoT Core 장치에 배포 된 [Microsoft 계정 로그인](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WebAccountManagement) Cortana 앱에서. 
* 데스크톱 컴퓨터를 [AppServiceProvider 앱](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/AppServices) 배포 하 고 한 번 이상 실행 되었습니다. 
 
_단계:_
1. RemoteSystems 샘플을 실행 합니다. 
2. "1) 검색", "시스템에 대 한 검색"을 클릭 합니다. 
3. "2) 시작 URI" 아래에서 선택 하 고 데스크톱 컴퓨터 시작 합니다. 
4. "3) 시작 App services"에서 데스크톱 컴퓨터를 선택 합니다.  
 
> [!NOTE] 
> 첫 번째 시도에서 시간이 오래 걸릴 수 있습니다. 다시이 훨씬 더 빠르게 응답 합니다. 
 
### <a name="helpful-links"></a>유용한 링크: 
* [MSDN에 대 한 프로젝트 로마 설명서](https://developer.microsoft.com/en-us/windows/project-rome )
* [Uwp 프로젝트 로마를 사용 하 여](https://docs.microsoft.com/windows/uwp/launch-resume/connected-apps-and-devices )
 
