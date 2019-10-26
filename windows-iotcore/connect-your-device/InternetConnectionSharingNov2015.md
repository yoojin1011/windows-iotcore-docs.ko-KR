---
title: 인터넷 연결 공유 자습서 (11 월 2015 릴리스)
ms.date: 09/06/2017
ms.topic: article
description: Windows 11 월 2015 릴리스에 대 한 인터넷 연결 공유를 사용 하도록 설정 하 고 구성 하는 방법을 알아봅니다.
keywords: windows iot, 인터넷 연결 공유, ICS, 장치 포털
ms.openlocfilehash: fa53539128251fd45e47003979a72e5a588b2869
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918361"
---
# <a name="internet-connection-sharing-tutorial-november-2015-release"></a><span data-ttu-id="c3a39-104">인터넷 연결 공유 자습서 (11 월 2015 릴리스)</span><span class="sxs-lookup"><span data-stu-id="c3a39-104">Internet Connection Sharing Tutorial (November 2015 Release)</span></span>

<span data-ttu-id="c3a39-105">이 문서에서는 Windows 10 IoT Core 11 월 2015 릴리스를 실행 하는 장치에서 ICS (인터넷 연결 공유)를 사용 하도록 설정 하는 단계를 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3a39-105">This document describes the steps to enable Internet Connection Sharing (ICS) on a device running Windows 10 IoT Core November 2015 Release.</span></span> <span data-ttu-id="c3a39-106">목표는 소프트웨어 Wi-fi 액세스 지점 (SoftAP)과 이더넷 어댑터 간에 인터넷 연결을 공유 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="c3a39-106">The objective is to share an Internet connection between a software Wi-Fi access point (SoftAP) and an Ethernet adapter.</span></span> <span data-ttu-id="c3a39-107">Windows 10 IoT Core 기념일 릴리스를 사용 하는 경우 [인터넷 연결 공유 자습서](InternetConnectionSharing.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c3a39-107">If you are using the Windows 10 IoT Core Anniversary Release please refer to the [Internet Connection Sharing Tutorial](InternetConnectionSharing.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c3a39-108">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="c3a39-108">Prerequisites</span></span>

* <span data-ttu-id="c3a39-109">Windows 10 IoT Core 11 월 2015 릴리스를 실행 하는 장치입니다.</span><span class="sxs-lookup"><span data-stu-id="c3a39-109">Device running Windows 10 IoT Core November 2015 Release.</span></span>
* <span data-ttu-id="c3a39-110">SoftAP를 시작할 수 있는 wi-fi USB 장치입니다.</span><span class="sxs-lookup"><span data-stu-id="c3a39-110">Wi-Fi USB device capable of starting a SoftAP.</span></span> <span data-ttu-id="c3a39-111">지원 되는 Wi-fi USB 장치는 [하드웨어 호환성 목록](../learn-about-hardware/HardwareCompatList.md) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c3a39-111">Please refer to the [Hardware Compatibility List](../learn-about-hardware/HardwareCompatList.md) for supported Wi-Fi USB devices.</span></span>
* <span data-ttu-id="c3a39-112">인터넷 액세스를 통한 이더넷 연결입니다.</span><span class="sxs-lookup"><span data-stu-id="c3a39-112">Ethernet connection with Internet Access.</span></span>


## <a name="setup"></a><span data-ttu-id="c3a39-113">설정</span><span class="sxs-lookup"><span data-stu-id="c3a39-113">Setup</span></span>

### <a name="step-1-gathering-network-information"></a><span data-ttu-id="c3a39-114">1 단계: 네트워크 정보 수집</span><span class="sxs-lookup"><span data-stu-id="c3a39-114">Step 1: Gathering Network Information</span></span>

1. <span data-ttu-id="c3a39-115">Wi-fi 동글이 연결 된 장치를 부팅 합니다. 이더넷 케이블이 연결 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3a39-115">Boot up device with Wi-Fi dongle plugged in, Ethernet cable plugged in.</span></span>
2. <span data-ttu-id="c3a39-116">IoT Core 장치에서 SoftAP를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3a39-116">Start SoftAP from the IoT Core device.</span></span>

   <span data-ttu-id="c3a39-117">기본적으로 Microsoft에서 제공한 이미지는 Wi-fi 라디오가 가능 하 고 WLAN 프로필이 추가 되지 않은 경우 SoftAP를 설정 하는 IoT 온 보 딩 응용 프로그램을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3a39-117">By default, the Microsoft provided images start an IoT Onboarding application that will setup a SoftAP if Wi-Fi radio is capable and no WLAN profile has been added.</span></span> <span data-ttu-id="c3a39-118">SoftAP를 시작 하기 위해 UWP 응용 프로그램은 [WIFIDIRECTADVERTISEMENTPUBLISHER API](https://msdn.microsoft.com/library/windows/apps/windows.devices.wifidirect.wifidirectadvertisementpublisher.aspx)를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3a39-118">To start SoftAP, UWP applications can use the [Windows.Devices.WiFiDirect.WiFiDirectAdvertisementPublisher API](https://msdn.microsoft.com/library/windows/apps/windows.devices.wifidirect.wifidirectadvertisementpublisher.aspx).</span></span> <span data-ttu-id="c3a39-119">IoT 온 보 딩 응용 프로그램의 소스 코드는 GitHub [i이상](https://github.com/ms-iot/samples/tree/develop/IotOnboarding)등록에 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3a39-119">The source code for the IoT Onboarding application can be on GitHub [IoTOnboarding](https://github.com/ms-iot/samples/tree/develop/IotOnboarding).</span></span>

   <span data-ttu-id="c3a39-120">SoftAP 네트워크의 SSID를 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3a39-120">Record the SSID of the SoftAP network.</span></span> <span data-ttu-id="c3a39-121">나중에 Wi-fi를 통해 IoT Core 장치에 연결 하는 데 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3a39-121">You will need it later to connect to your IoT Core device via Wi-Fi.</span></span> <span data-ttu-id="c3a39-122">IoT 온 보 딩 응용 프로그램의 경우 SSID는 "AJ\_SoftAPSsid\_"로 시작 하 고 응용 프로그램의 구성 [파일](https://github.com/ms-iot/samples/blob/develop/IotOnboarding/IoTOnboardingTask/Config.xml)에서 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3a39-122">For IoT Onboarding application the SSID will start with "AJ\_SoftAPSsid\_" and can be changed in application's configuration [file](https://github.com/ms-iot/samples/blob/develop/IotOnboarding/IoTOnboardingTask/Config.xml).</span></span>

3. <span data-ttu-id="c3a39-123">[Ssh를 사용 하 여](ssh.md)IoT Core 장치에 원격으로 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3a39-123">Remotely connect to the IoT Core device [using ssh](ssh.md).</span></span>
4. <span data-ttu-id="c3a39-124">네트워크 장치 인덱스 및 설명을 찾아 장치 네트워크에 대 한 정보를 수집 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3a39-124">Collect information about device networks by finding network device indexes and descriptions.</span></span> <span data-ttu-id="c3a39-125">연결할 네트워크를 선언 하는 데 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3a39-125">This is needed to declare which networks to bridge.</span></span>

   <span data-ttu-id="c3a39-126">장치에서 **route print** 를 실행 하 고 다음 데이터를 수집 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3a39-126">On device, run **route print** and collect the following data:</span></span>

   * <span data-ttu-id="c3a39-127">이더넷에 대 한 공용 인터페이스 네트워크 인덱스를 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3a39-127">Record PUBLIC Interface network index for the Ethernet.</span></span>
   * <span data-ttu-id="c3a39-128">SoftAP에 대 한 개인 인터페이스 네트워크 인덱스 (예: "Microsoft Wi-fi Direct 가상 어댑터 #2")를 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3a39-128">Record PRIVATE Interface network index for the SoftAP (e.g. “Microsoft Wi-Fi Direct Virtual Adapter #2”).</span></span>

   <span data-ttu-id="c3a39-129">예를 들어 SoftAP는 인터페이스 인덱스 5, 어댑터 설명 "Microsoft Wi-fi Direct 가상 어댑터 #2"를 통해 노출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3a39-129">For example, the SoftAP is exposed through interface index 5, adapter description “Microsoft Wi-Fi Direct Virtual Adapter #2”.</span></span>

   ![경로 인쇄](../media/InternetConnectionSharing/internetconnectionsharing_route.png)

   <span data-ttu-id="c3a39-131">장치에서 **ipconfig/all** 을 실행 하 고 다음 데이터를 수집 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3a39-131">On device, run **ipconfig /all** and collect the following data:</span></span>
    
   * <span data-ttu-id="c3a39-132">SoftAP에 대 한 개인 인터페이스 네트워크 어댑터 이름을 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3a39-132">Record PRIVATE Interface network adapter name for the SoftAP</span></span>

   <span data-ttu-id="c3a39-133">예를 들어 "ipconfig/all"을 실행 하면 "Microsoft Wi-fi Direct 가상 어댑터 #2"에 대 한 설명이 포함 된 "로컬 영역 연결 \* 3" 이라는 특정 어댑터가 검색 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3a39-133">For example, running "ipconfig /all" finds the specific adapter named “Local Area Connection\* 3” that has a description of “Microsoft Wi-Fi Direct Virtual Adapter #2”.</span></span> <span data-ttu-id="c3a39-134">이 메서드를 사용 하 여 "route print"에 반환 된 설명에서 어댑터 이름을 수동으로 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3a39-134">Use this method to manually find Adapter Name from the Description returned in “route print”.</span></span>

   ![모두 ipconfig](../media/InternetConnectionSharing/internetconnectionsharing_ipconfig.png)

### <a name="step-2-scripting-internet-connection-sharing-trigger"></a><span data-ttu-id="c3a39-136">2 단계: 인터넷 연결 공유 트리거 스크립팅</span><span class="sxs-lookup"><span data-stu-id="c3a39-136">Step 2: Scripting Internet Connection Sharing trigger</span></span>

<span data-ttu-id="c3a39-137">두 네트워크 간에 인터넷 연결 공유를 시작 하려면 다음 단계를 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3a39-137">Starting Internet Connection Sharing between two networks requires the following steps:</span></span>

* <span data-ttu-id="c3a39-138">개인 (SoftAP) 및 공용 (이더넷) 네트워크 인터페이스를 브리지로 설정 하도록 레지스트리 키를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3a39-138">Set registry keys to set private (SoftAP) and public (Ethernet) network interfaces to bridge.</span></span>
* <span data-ttu-id="c3a39-139">적절 한 방화벽 규칙을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3a39-139">Set appropriate firewall rules.</span></span>
* <span data-ttu-id="c3a39-140">개인 인터페이스에서 DHCP를 끕니다.</span><span class="sxs-lookup"><span data-stu-id="c3a39-140">Turns off DHCP on private interface.</span></span>
* <span data-ttu-id="c3a39-141">개인 인터페이스의 고정 IP 주소를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3a39-141">Sets static IP address on private interface.</span></span>
* <span data-ttu-id="c3a39-142">SharedAccess 서비스를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3a39-142">Starts SharedAccess service.</span></span>
* <span data-ttu-id="c3a39-143">SharedAccess service에 명령 코드 "129"을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="c3a39-143">Sends command code “129” to SharedAccess service.</span></span>


#### <a name="create-a-script-to-automate-the-ics-settings"></a><span data-ttu-id="c3a39-144">ICS 설정을 자동화 하는 스크립트 만들기</span><span class="sxs-lookup"><span data-stu-id="c3a39-144">Create a script to automate the ICS settings</span></span>

<span data-ttu-id="c3a39-145">다음은 장치 시작 순서에 통합할 수 있는 위에 나열 된 단계를 자동화 하는 스크립트 및 코드의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="c3a39-145">Below is an example of a scripts and code to automate the steps listed above that can be integrated into the device startup sequence.</span></span> <span data-ttu-id="c3a39-146">다음 내용을 사용 하 여 스크립트 파일 (예: **ConfigureICS**)을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c3a39-146">Create a script file (e.g. **ConfigureICS.cmd**) with the following content:</span></span>

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

<span data-ttu-id="c3a39-147">이 스크립트는 모든 작업을 수행 하지만 SharedAccess 서비스를 시작/중지 하 고 서비스 명령을 보내지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c3a39-147">This script will do everything but start/stop SharedAccess service, and does not send service command.</span></span> <span data-ttu-id="c3a39-148">이러한 작업의 경우 생성 해야 하는 SharedAccessUtility .exe를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3a39-148">For those tasks it calls to SharedAccessUtility.exe, which needs to be created.</span></span>

#### <a name="build-the-sharedaccessutility-application"></a><span data-ttu-id="c3a39-149">SharedAccessUtility 응용 프로그램 빌드</span><span class="sxs-lookup"><span data-stu-id="c3a39-149">Build the SharedAccessUtility application</span></span>
<span data-ttu-id="c3a39-150">[Windows Iot Core 프로젝트 템플릿 확장이](https://go.microsoft.com/fwlink/?linkid=847472) 설치 된 visual Studio에서 **sharedaccessutility**라는 새로운 "빈 Windows IoT core 콘솔 응용 프로그램 C++ " Visual 프로젝트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c3a39-150">In Visual Studio with [Windows IoT Core Project Templates extensions](https://go.microsoft.com/fwlink/?linkid=847472) installed, create a new “Blank Windows IoT Core Console Application” Visual C++ project, named **SharedAccessUtility**.</span></span>

![VS 새 프로젝트](../media/InternetConnectionSharing/internetconnectionsharing_vs.png)

<span data-ttu-id="c3a39-152">ConsoleApplication의 내용을 다음 코드로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="c3a39-152">Replace contents of ConsoleApplication.cpp with the following code:</span></span>

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

<span data-ttu-id="c3a39-153">대상 아키텍처 (예: x86 릴리스)를 빌드하고 출력 **Sharedaccessutility .exe** 를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="c3a39-153">Build for target architecture, e.g. Release x86, and locate output **SharedAccessUtility.exe**</span></span>

### <a name="step-3-starting-internet-connection-sharing"></a><span data-ttu-id="c3a39-154">3 단계: 인터넷 연결 공유 시작</span><span class="sxs-lookup"><span data-stu-id="c3a39-154">Step 3: Starting Internet Connection Sharing</span></span>

1. <span data-ttu-id="c3a39-155">2 단계에서 만든 **Configics .cmd** 스크립트를 특정 위치 (예: `C:\test\`)의 장치에 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3a39-155">Copy **ConfigICS.cmd** script created in Step 2 to the device in some location, e.g. to `C:\test\`</span></span>
2. <span data-ttu-id="c3a39-156">2 단계에서 만든 **Sharedaccessutility .exe** 를 같은 위치의 장치 (예: `C:\test`\에 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3a39-156">Copy **SharedAccessUtility.exe** created in Step 2 to the device in the same location, e.g. `C:\test`\</span></span>
3. <span data-ttu-id="c3a39-157">장치에서 **C:\test\ConfigureICS.cmd start [public index] [private index] [private adapter name]** 를 실행 합니다 .이 예제에서는 <strong>C:\test\ConfigureICS.cmd Start 4 5 "Local Area Connection \* 3"</strong> 을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3a39-157">On the device, run **C:\test\ConfigureICS.cmd start [public index] [private index] [private adapter name]** In this example, this would mean <strong>C:\test\ConfigureICS.cmd start 4 5 "Local Area Connection\* 3"</strong></span></span>

<span data-ttu-id="c3a39-158">이 시점에서 장치는 장치의 보급 된 SSID에 연결 된 모든 클라이언트에 대해 인터넷 연결 공유를 사용 하도록 설정 했습니다.</span><span class="sxs-lookup"><span data-stu-id="c3a39-158">At this point the device has enabled Internet Connection Sharing for any client connected to the device’s advertised SSID.</span></span>
