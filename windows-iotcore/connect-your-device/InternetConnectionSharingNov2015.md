---
title: 인터넷 연결 공유 자습서 (2015 년 11 월 릴리스)
author: saraclay
ms.author: saclayt
ms.date: 09/06/17
ms.topic: article
description: 2015 년 11 월 릴리스의 Windows에 인터넷 연결 공유를 구성 하는 방법에 알아봅니다.
keywords: windows iot, Internet Connection Sharing, ICS와 장치 포털
ms.openlocfilehash: c8f27b48197a0ec881a66da5d3e81272b3076100
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513037"
---
# <a name="internet-connection-sharing-tutorial-november-2015-release"></a>인터넷 연결 공유 자습서 (2015 년 11 월 릴리스)

이 문서에서는 Windows 10 IoT Core 실행 하는 장치에서 인터넷 연결 공유 ICS ()를 사용 하도록 설정 하는 단계를 설명 2015 년 11 월 릴리스. 목표는 소프트웨어 Wi-fi 액세스 지점 (SoftAP) 사이의 이더넷 어댑터를 인터넷 연결을 공유 하는 것입니다. Windows 10 IoT Core 1 주년 버전을 사용 하는 경우를 참조 하십시오 합니다 [인터넷 연결 공유 자습서](InternetConnectionSharing.md)합니다.

## <a name="prerequisites"></a>사전 요구 사항

* Windows 10 IoT Core 실행 하는 장치 2015 년 11 월 릴리스.
* Wi-fi USB 장치를 SoftAP 시작 수입니다. 참조 하십시오 합니다 [하드웨어 호환성 목록](../learn-about-hardware/HardwareCompatList.md) 에 대 한 Wi-fi USB 장치를 지원 합니다.
* 인터넷에 연결 된 이더넷 연결 합니다.


## <a name="setup"></a>설치 프로그램

### <a name="step-1-gathering-network-information"></a>1단계: 네트워크 정보 수집

1. Wi-fi를 사용 하 여 장치를 부팅할 동글 연결, 이더넷 케이블 연결 합니다.
2. IoT Core 장치에서 SoftAP를 시작 합니다.

   기본적으로 Microsoft는 SoftAP Wi-fi 라디오 수 및 WLAN 프로필이 없습니다. 추가 된 경우 설정 하는 IoT 온 보 딩 응용 프로그램 이미지 시작을 제공 합니다. UWP 응용 프로그램 SoftAP를 시작 하려면 사용 합니다 [Windows.Devices.WiFiDirect.WiFiDirectAdvertisementPublisher API](https://msdn.microsoft.com/library/windows/apps/windows.devices.wifidirect.wifidirectadvertisementpublisher.aspx)합니다. IoT 온 보 딩 응용 프로그램에 대 한 소스 코드를 GitHub에 있을 수 있습니다 [IoTOnboarding](https://github.com/ms-iot/samples/tree/develop/IotOnboarding)합니다.

   SoftAP 네트워크의 SSID를 기록 합니다. Wi-fi를 통해 IoT Core 장치에 연결 하는 나중에 필요 합니다. SSID 시작 IoT 온 보 딩 응용 프로그램에 대 한 "AJ\_SoftAPSsid\_" 응용 프로그램의 구성에서 변경할 수 있습니다 [파일](https://github.com/ms-iot/samples/blob/develop/IotOnboarding/IoTOnboardingTask/Config.xml)합니다.

3. IoT Core 장치에 원격으로 연결할 [ssh를 사용 하 여](ssh.md)입니다.
4. 네트워크 장치 인덱스 및 설명을 검색 하 여 네트워크 장치에 대 한 정보를 수집 합니다. 이 브리지에는 네트워크를 선언 해야 합니다.

   장치에서 실행할 **인쇄 경로** 다음 데이터를 수집 합니다.

   * 이더넷에 대 한 레코드 공용 인터페이스의 네트워크 인덱스입니다.
   * 레코드 개인 인터페이스는 SoftAP에 대 한 (예: 인덱스를 네트워크 "Microsoft Wi-Fi Direct 가상 어댑터 2").

   예를 들어를 SoftAP 인터페이스 인덱스 5 어댑터 설명 "Microsoft Wi-Fi Direct 가상 어댑터 2"를 통해 노출 됩니다.

   ![경로 인쇄](../media/InternetConnectionSharing/internetconnectionsharing_route.png)

   장치에서 실행 **ipconfig /all** 다음 데이터를 수집 합니다.
    
   * 레코드 개인 인터페이스는 SoftAP 네트워크 어댑터 이름

   예를 들어 실행 "ipconfig /all" 라는 특정 어댑터를 찾습니다 "로컬 영역 연결 * 3" 에 "Microsoft Wi-Fi Direct 가상 어댑터 2"에 대 한 설명입니다. 어댑터 이름에 대 한 설명에서 "경로 인쇄" 반환을 수동으로 찾기 위해이 메서드를 사용 합니다.

   ![모든 ipconfig](../media/InternetConnectionSharing/internetconnectionsharing_ipconfig.png)

### <a name="step-2-scripting-internet-connection-sharing-trigger"></a>2단계: 인터넷 연결 공유 트리거 스크립팅

두 네트워크 간의 인터넷 연결 공유를 시작 합니다. 다음 단계를 수행 합니다.

* 연결 (SoftAP) 개인 및 공용 (이더넷) 네트워크 인터페이스를 설정 하려면 레지스트리 키를 설정 합니다.
* 적절 한 방화벽 규칙을 설정 합니다.
* DHCP private 인터페이스를 해제합니다.
* 개인 인터페이스에 고정 IP 주소를 설정합니다.
* SharedAccess 서비스를 시작합니다.
* 명령 코드를 "129" SharedAccess 서비스로 보냅니다.


#### <a name="create-a-script-to-automate-the-ics-settings"></a>ICS 설정을 자동화 하는 스크립트 만들기

아래는 스크립트의 예 이며 장치 시작 순서에는 위에 나열 된 단계를 자동화 하는 코드를 통합할 수 있습니다. 스크립트 파일을 만듭니다 (예: **ConfigureICS.cmd**) 다음과 같은 내용으로:

```
echo off

set START_OR_STOP=%1
set PUBLIC_INDEX=%2
set PRIVATE_INDEX=%3
set PRIVATE_INTERFACE_NAME=%4

if not defined PRIVATE_INTERFACE_NAME (
  goto usage
)

if "%START_OR_STOP%"=="start" (

  REM Set the public and private interface registry keys
  reg add HKEY_LOCAL_MACHINE\System\SA /f /v private /t REG_DWORD /d %PRIVATE_INDEX%
  reg add HKEY_LOCAL_MACHINE\System\SA /f /v public /t REG_DWORD /d %PUBLIC_INDEX%

  REM Set the firewall rules to allow DHCP to work
  netsh advfirewall firewall add rule name=\"AllowPort67In\" protocol=UDP dir=in localport=67 action=allow
  netsh advfirewall firewall add rule name=\"AllowPort68In\" protocol=UDP dir=in localport=68 action=allow
  netsh advfirewall firewall add rule name=\"AllowPort67Out\" protocol=UDP dir=out localport=67 action=allow
  netsh advfirewall firewall add rule name=\"AllowPort68Out\" protocol=UDP dir=out localport=68 action=allow
  netsh advfirewall firewall add rule name=\"AllowPort53Out\" protocol=UDP dir=out localport=53 action=allow
  netsh advfirewall firewall add rule name=\"AllowPort53In\" protocol=UDP dir=in localport=53 action=allow

  REM Turn off DHCP and set static IP for private interface
  netsh interface ip set address %4 static 192.168.137.1

  REM Start sharing
  call SharedAccessUtility.exe start

) else if "%START_OR_STOP%"=="stop" (

  REM Stop sharing
  call SharedAccessUtility.exe stop

  REM Set the public and private interface registry keys
  reg add HKEY_LOCAL_MACHINE\System\SA /f /v private /t REG_DWORD /d 0
  reg add HKEY_LOCAL_MACHINE\System\SA /f /v public /t REG_DWORD /d 0

  REM Clear the firewall rules
  netsh advfirewall firewall delete rule name="AllowPort67In"
  netsh advfirewall firewall delete rule name="AllowPort68In"
  netsh advfirewall firewall delete rule name="AllowPort67Out"
  netsh advfirewall firewall delete rule name="AllowPort68Out"
  netsh advfirewall firewall delete rule name="AllowPort53Out"
  netsh advfirewall firewall delete rule name="AllowPort53In"

  REM Reenable DHCP for private interface
  netsh interface ip set address %4 dhcp

) else (
  goto usage
)

goto eof

:usage
ECHO USAGE: %0 [start ^| stop] [public interface index] [private interface index] [private interface name]
ECHO e.g. %0 start 1 2 "Ethernet"

:eof
```

이 스크립트는 SharedAccess 서비스 시작/중지 하지만 모든 작업을 처리 하 고 서비스 명령 전송 하지 않습니다. 해당 작업용 SharedAccessUtility.exe를 호출 해야 하는 만들 수입니다.

#### <a name="build-the-sharedaccessutility-application"></a>SharedAccessUtility 응용 프로그램 빌드
Visual Studio에서 사용 [Windows IoT Core 프로젝트 템플릿에 확장](https://go.microsoft.com/fwlink/?linkid=847472) 설치를 만듭니다 "빈 Windows IoT Core 콘솔 응용 프로그램" 시각적 개체 C++ 라는 프로젝트 **SharedAccessUtility**합니다.

![VS 새 프로젝트](../media/InternetConnectionSharing/internetconnectionsharing_vs.png)

ConsoleApplication.cpp의 내용을 다음 코드로 바꿉니다.

```C++
#include "pch.h"
#include <ws2tcpip.h>
#include <iphlpapi.h>
#include <mstcpip.h>
#include <stdio.h>

#define SHARED_ACCESS_NAME L"SharedAccess"
#define START_SHARING_CONTROL 129

DWORD StartSharedAccessService(SC_HANDLE *phScm, SC_HANDLE *phSvc)
{
    DWORD dwError = ERROR_SUCCESS;
    SERVICE_STATUS svcStatus = { 0 };

    // open a handle to SCM
    *phScm = OpenSCManager(NULL, NULL, SC_MANAGER_CONNECT);
    if (*phScm == NULL)
    {
        dwError = GetLastError();
        printf("\nOpenSCManager failed; error = %d", dwError);
    }
    else
    {
        // open a handle to the service
        *phSvc = OpenService(*phScm, SHARED_ACCESS_NAME, SERVICE_START | SERVICE_QUERY_STATUS | SERVICE_QUERY_CONFIG | SERVICE_STOP | SERVICE_USER_DEFINED_CONTROL);
        if (*phSvc == NULL)
        {
            dwError = GetLastError();
            printf("\nOpenService failed; error = %d", dwError);
        }
        else
        {
            if (!StartService(*phSvc, 0, NULL))
            {
                dwError = GetLastError();
                if (dwError != ERROR_SERVICE_ALREADY_RUNNING)
                {
                    printf("\nStartService failed; error = %d", dwError);
                }
                else
                {
                    dwError = ERROR_SUCCESS;
                    printf("\nService already running.");
                }
            }

            if (dwError == ERROR_SUCCESS)
            {
                if (QueryServiceStatus(*phSvc, &svcStatus) && svcStatus.dwCurrentState != SERVICE_RUNNING)
                {
                    for (int i = 0; i < 10; i++)
                    {
                        printf("\nWaiting 1 second for service to start.");
                        Sleep(1000);
                        if (QueryServiceStatus(*phSvc, &svcStatus))
                        {
                            if (svcStatus.dwCurrentState == SERVICE_RUNNING)
                            {
                                printf("\nService is running.");
                                // it is, so break out
                                dwError = ERROR_SUCCESS;
                                break;
                            }
                            else
                            {
                                if (svcStatus.dwCurrentState == SERVICE_STOPPED)
                                {
                                    printf("\nService could not run.");
                                    // it is, so break out
                                    dwError = ERROR_SERVICE_NOT_ACTIVE;
                                    break;
                                }
                            }
                        }
                        else
                        {
                            printf("\nWaiting more time.");
                        }
                    }
                }
            }
        }
    }

    if (dwError == ERROR_SUCCESS) //service is running
    {
        if (!ControlService(*phSvc, START_SHARING_CONTROL, &svcStatus))
        {
            dwError = GetLastError();
            printf("\nControl service for start sharing failure, %d", dwError);
        }
        else
        {
            printf("\nSharing started");
        }
    }

    // Service cleanup done at the main.
    return dwError;
}


DWORD StopSharedAccessService(SC_HANDLE *phSvc)
{
    DWORD dwError = ERROR_SUCCESS;
    SERVICE_STATUS svcStatus = { 0 };

    if (!QueryServiceStatus(*phSvc, &svcStatus))
    {
        dwError = GetLastError();
        printf("\nFailed to query sharedaccess, %d", dwError);
    }
    else
    {
        if (svcStatus.dwCurrentState != SERVICE_STOPPED)
        {
            if (ControlService(*phSvc, SERVICE_CONTROL_STOP, &svcStatus))
            {
                if (QueryServiceStatus(*phSvc, &svcStatus) && svcStatus.dwCurrentState != SERVICE_STOPPED)
                {
                    for (int i = 0; i < 10; i++)
                    {
                        printf("\nWaiting 1 second for service to stop.");
                        Sleep(1000);
                        if (QueryServiceStatus(*phSvc, &svcStatus))
                        {
                            if (svcStatus.dwCurrentState == SERVICE_STOPPED)
                            {
                                printf("\nService stopped.");
                                // it is, so break out
                                dwError = ERROR_SUCCESS;
                                break;
                            }
                            else
                            {
                                printf("\nWaiting more time.");
                            }
                        }
                    }
                }
            }
        }
    }
    return dwError;
}

void ShowUsage()
{
    printf("Usage: SharedAccessUtility.exe start | stop\n"
        "Setup: Make sure the public and private interfaces are up and running and that the SharedAccess registry keys are set.");
}

int __cdecl
main(
    __in int argc,
    __in_ecount(argc) LPSTR argv[]
    )
{
    SC_HANDLE hScm = NULL;
    SC_HANDLE hSvc = NULL;
    DWORD dwError = NO_ERROR;
    bool startSharing = true;

    if (argc < 2)
    {
        ShowUsage();
        return -1;
    }
    else
    {
        if (strcmp(argv[1], "start") == 0 || strcmp(argv[1], "/start") == 0)
        {
            startSharing = true;
        }
        else if (strcmp(argv[1], "stop") == 0 || strcmp(argv[1], "/stop") == 0)
        {
            startSharing = false;
        }
        else
        {
            ShowUsage();
            return -1;
        }
    }

    dwError = startSharing ? StartSharedAccessService(&hScm, &hSvc) : StopSharedAccessService(&hSvc);

    // Cleanup
    if (hSvc != NULL)
    {
        CloseServiceHandle(hSvc);
        hSvc = NULL;
    }
    if (hScm != NULL)
    {
        CloseServiceHandle(hScm);
        hScm = NULL;
    }
    return 0;
}
```

출력 대상 아키텍처에 대 한 빌드, x86, 예: 릴리스에서 찾아서 **SharedAccessUtility.exe**

### <a name="step-3-starting-internet-connection-sharing"></a>3단계: 시작 하는 인터넷 연결 공유

1. 복사본 **ConfigICS.cmd** 2 단계에서에서 만든 일부 위치에서 장치에 예를 들어를 스크립트 `C:\test\`
2. 복사본 **SharedAccessUtility.exe** 예: 동일한 위치에서 장치에 2 단계에서에서 만든 `C:\test`\
3. 장치에서 실행 **C:\test\ConfigureICS.cmd 시작 [공용 index] [개인 index] [개인 어댑터 name]** 의미이 예에서 <strong>C:\test\ConfigureICS.cmd 시작 4 5 "로컬 영역 연결 * 3"</strong>

이 시점에서 장치가 사용 하도록 설정한 인터넷 연결 공유 장치 보급 된 SSID에 연결 된 모든 클라이언트에 대 한 합니다.
