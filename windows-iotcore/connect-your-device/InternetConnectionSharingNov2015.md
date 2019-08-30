---
title: 인터넷 연결 공유 자습서 (11 월 2015 릴리스)
author: saraclay
ms.author: saclayt
ms.date: 09/06/17
ms.topic: article
description: Windows 11 월 2015 릴리스에 대 한 인터넷 연결 공유를 사용 하도록 설정 하 고 구성 하는 방법을 알아봅니다.
keywords: windows iot, 인터넷 연결 공유, ICS, 장치 포털
ms.openlocfilehash: c8f27b48197a0ec881a66da5d3e81272b3076100
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "60169081"
---
# <a name="internet-connection-sharing-tutorial-november-2015-release"></a>인터넷 연결 공유 자습서 (11 월 2015 릴리스)

이 문서에서는 Windows 10 IoT Core 11 월 2015 릴리스를 실행 하는 장치에서 ICS (인터넷 연결 공유)를 사용 하도록 설정 하는 단계를 설명 합니다. 목표는 소프트웨어 Wi-fi 액세스 지점 (SoftAP)과 이더넷 어댑터 간에 인터넷 연결을 공유 하는 것입니다. Windows 10 IoT Core 기념일 릴리스를 사용 하는 경우 [인터넷 연결 공유 자습서](InternetConnectionSharing.md)를 참조 하세요.

## <a name="prerequisites"></a>사전 요구 사항

* Windows 10 IoT Core 11 월 2015 릴리스를 실행 하는 장치입니다.
* SoftAP를 시작할 수 있는 wi-fi USB 장치입니다. 지원 되는 Wi-fi USB 장치는 [하드웨어 호환성 목록](../learn-about-hardware/HardwareCompatList.md) 을 참조 하세요.
* 인터넷 액세스를 통한 이더넷 연결입니다.


## <a name="setup"></a>설정

### <a name="step-1-gathering-network-information"></a>1단계: 네트워크 정보를 모으고 있습니다.

1. Wi-fi 동글이 연결 된 장치를 부팅 합니다. 이더넷 케이블이 연결 되어 있습니다.
2. IoT Core 장치에서 SoftAP를 시작 합니다.

   기본적으로 Microsoft에서 제공한 이미지는 Wi-fi 라디오가 가능 하 고 WLAN 프로필이 추가 되지 않은 경우 SoftAP를 설정 하는 IoT 온 보 딩 응용 프로그램을 시작 합니다. SoftAP를 시작 하기 위해 UWP 응용 프로그램은 [WIFIDIRECTADVERTISEMENTPUBLISHER API](https://msdn.microsoft.com/library/windows/apps/windows.devices.wifidirect.wifidirectadvertisementpublisher.aspx)를 사용할 수 있습니다. IoT 온 보 딩 응용 프로그램의 소스 코드는 GitHub [i이상](https://github.com/ms-iot/samples/tree/develop/IotOnboarding)등록에 있을 수 있습니다.

   SoftAP 네트워크의 SSID를 기록 합니다. 나중에 Wi-fi를 통해 IoT Core 장치에 연결 하는 데 필요 합니다. IoT 온 보 딩 응용 프로그램의 경우 SSID는 "\_AJ\_SoftAPSsid"로 시작 하 고 응용 프로그램의 구성 [파일](https://github.com/ms-iot/samples/blob/develop/IotOnboarding/IoTOnboardingTask/Config.xml)에서 변경할 수 있습니다.

3. [Ssh를 사용 하 여](ssh.md)IoT Core 장치에 원격으로 연결 합니다.
4. 네트워크 장치 인덱스 및 설명을 찾아 장치 네트워크에 대 한 정보를 수집 합니다. 연결할 네트워크를 선언 하는 데 필요 합니다.

   장치에서 **route print** 를 실행 하 고 다음 데이터를 수집 합니다.

   * 이더넷에 대 한 공용 인터페이스 네트워크 인덱스를 기록 합니다.
   * SoftAP에 대 한 개인 인터페이스 네트워크 인덱스를 기록 합니다 (예: "Microsoft Wi-fi Direct 가상 어댑터 #2").

   예를 들어 SoftAP는 인터페이스 인덱스 5, 어댑터 설명 "Microsoft Wi-fi Direct 가상 어댑터 #2"를 통해 노출 됩니다.

   ![경로 인쇄](../media/InternetConnectionSharing/internetconnectionsharing_route.png)

   장치에서 **ipconfig/all** 을 실행 하 고 다음 데이터를 수집 합니다.
    
   * SoftAP에 대 한 개인 인터페이스 네트워크 어댑터 이름을 기록 합니다.

   예를 들어 "ipconfig/all"을 실행 하면 "Microsoft Wi-fi Direct 가상 어댑터 #2"에 대 한 설명이 포함 된 "로컬 영역 연결 * 3" 이라는 특정 어댑터가 검색 됩니다. 이 메서드를 사용 하 여 "route print"에 반환 된 설명에서 어댑터 이름을 수동으로 찾을 수 있습니다.

   ![모두 ipconfig](../media/InternetConnectionSharing/internetconnectionsharing_ipconfig.png)

### <a name="step-2-scripting-internet-connection-sharing-trigger"></a>2단계: 인터넷 연결 공유 트리거 스크립팅

두 네트워크 간에 인터넷 연결 공유를 시작 하려면 다음 단계를 수행 해야 합니다.

* 개인 (SoftAP) 및 공용 (이더넷) 네트워크 인터페이스를 브리지로 설정 하도록 레지스트리 키를 설정 합니다.
* 적절 한 방화벽 규칙을 설정 합니다.
* 개인 인터페이스에서 DHCP를 끕니다.
* 개인 인터페이스의 고정 IP 주소를 설정 합니다.
* SharedAccess 서비스를 시작 합니다.
* SharedAccess service에 명령 코드 "129"을 보냅니다.


#### <a name="create-a-script-to-automate-the-ics-settings"></a>ICS 설정을 자동화 하는 스크립트 만들기

다음은 장치 시작 순서에 통합할 수 있는 위에 나열 된 단계를 자동화 하는 스크립트 및 코드의 예입니다. 다음 내용을 사용 하 여 스크립트 파일 (예: **ConfigureICS**)을 만듭니다.

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

이 스크립트는 모든 작업을 수행 하지만 SharedAccess 서비스를 시작/중지 하 고 서비스 명령을 보내지 않습니다. 이러한 작업의 경우 생성 해야 하는 SharedAccessUtility .exe를 호출 합니다.

#### <a name="build-the-sharedaccessutility-application"></a>SharedAccessUtility 응용 프로그램 빌드
[Windows Iot Core 프로젝트 템플릿 확장이](https://go.microsoft.com/fwlink/?linkid=847472) 설치 된 visual Studio에서 **sharedaccessutility**라는 새로운 "빈 Windows IoT core 콘솔 응용 프로그램 C++ " Visual 프로젝트를 만듭니다.

![VS 새 프로젝트](../media/InternetConnectionSharing/internetconnectionsharing_vs.png)

ConsoleApplication의 내용을 다음 코드로 바꿉니다.

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

대상 아키텍처 (예: x86 릴리스)를 빌드하고 출력 **Sharedaccessutility .exe** 를 찾습니다.

### <a name="step-3-starting-internet-connection-sharing"></a>3단계: 인터넷 연결 공유를 시작 하는 중

1. 2 단계에서 만든 **Configics .cmd** 스크립트를 일부 위치의 장치에 복사 합니다. 예를 들면 다음과 같습니다.`C:\test\`
2. 2 단계에서 만든 **Sharedaccessutility .exe** 를 같은 위치의 장치에 복사 합니다 (예:).`C:\test`\
3. 장치에서 **C:\test\ConfigureICS.cmd start [public index] [private index] [private adapter name]** 를 실행 합니다 .이 예제에서는 <strong>C:\test\ConfigureICS.cmd Start 4 5 "Local Area Connection * 3"</strong> 을 의미 합니다.

이 시점에서 장치는 장치의 보급 된 SSID에 연결 된 모든 클라이언트에 대해 인터넷 연결 공유를 사용 하도록 설정 했습니다.
