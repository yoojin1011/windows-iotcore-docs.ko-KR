---
title: Localhost와 통신
author: paulmon
ms.author: paulmon
ms.date: 08/28/2017
ms.topic: article
description: Localhost 루프백을 사용 하도록 설정 하 여 두 프로세스로 TCP/IP 연결을 만드는 방법에 대해 알아봅니다.
keywords: windows iot, localhost, 루프백, UWP, visual studio
ms.openlocfilehash: 498db8321babad890606e9e4589c9a6407f3ea6e
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "60170671"
---
# <a name="communicating-with-localhost-loopback"></a><span data-ttu-id="d6f33-104">Localhost (루프백)와 통신</span><span class="sxs-lookup"><span data-stu-id="d6f33-104">Communicating with localhost (loopback)</span></span>

<span data-ttu-id="d6f33-105">Windows IoT Core에서 동일한 장치에서 실행 되는 두 프로세스 사이에 TCP/IP 연결을 만들고 그 중 하나가 UWP 앱 인 경우 localhost 루프백을 사용 하도록 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6f33-105">On Windows IoT Core, if you want to create a TCP/IP connection between 2 processes running on the same device and one of them is a UWP app you must enable localhost loopback.</span></span>

## <a name="loopback-and-the-debugger"></a><span data-ttu-id="d6f33-106">루프백 및 디버거</span><span class="sxs-lookup"><span data-stu-id="d6f33-106">Loopback and the debugger</span></span> 
<span data-ttu-id="d6f33-107">기본적으로 Visual Studio 디버거에서 실행 되는 경우 해당 디버그 세션에 대해서만 자동으로 아웃 바운드 루프백을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6f33-107">By default, running under the Visual Studio debugger enables outbound loopback automatically for that debug session only.</span></span><span data-ttu-id="d6f33-108">  시작 프로젝트에 대 한 디버거 설정에서 루프백 확인란을 선택 하는 동안에는 아무것도 수행할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d6f33-108">  You shouldn’t have to do anything as long as the loopback checkbox is checked in the debugger settings for your startup project.</span></span> <span data-ttu-id="d6f33-109"> 소켓 수신기를 구현 하려면 인바운드 연결에 대해 localhost 루프백을 사용 하도록 설정 해야 합니다 (아래 참조).</span><span class="sxs-lookup"><span data-stu-id="d6f33-109"> If you want to implement a socket listener the you must enable localhost loopback for inbound connections (see below).</span></span>
 
## <a name="enabling-the-inbound-loopback-policy"></a><span data-ttu-id="d6f33-110">인바운드 루프백 정책 사용</span><span class="sxs-lookup"><span data-stu-id="d6f33-110">Enabling the inbound loopback policy</span></span>
<span data-ttu-id="d6f33-111">서버를 구현 하는 UWP 앱에 대해 **Windows IoT Core** 에 대 한 localhost 인바운드 루프백 정책을 사용 하도록 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6f33-111">The localhost inbound loopback policy for **Windows IoT Core** must be enabled for UWP apps that implement servers.</span></span>  <span data-ttu-id="d6f33-112">이 정책은 다음 레지스트리 키를 통해 제어 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d6f33-112">This policy is controlled by the following registry key:</span></span>

        [HKEY_LOCAL_MACHINE\system\currentcontrolset\services\mpssvc\parameters]
            "IoTInboundLoopbackPolicy"=dword:00000001

<span data-ttu-id="d6f33-113">이 IoTInboundLoopbackPolicy 레지스트리 키 값을 dword: 00000001로 설정 해야 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6f33-113">This IoTInboundLoopbackPolicy registry key value must be set to dword:00000001 to enable.</span></span> <span data-ttu-id="d6f33-114">IoTInboundLoopbackPolicy 레지스트리 값을 변경 하는 경우 변경 내용을 적용 하려면 다시 부팅 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6f33-114">If you change the IoTInboundLoopbackPolicy registry value you must reboot for the change to take effect.</span></span><span data-ttu-id="d6f33-115">  Localhost 루프백 정책은 **Windows IoT Core** 에서 기본적으로 사용 하도록 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6f33-115">  The localhost loopback policy should be enabled by default on **Windows IoT Core**</span></span>

<span data-ttu-id="d6f33-116">값이 설정 되어 있는지 확인 하려면 **Windows IoT Core** 장치에서 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6f33-116">To verify that the value is set execute the following command on the **Windows IoT Core** device:</span></span>

        reg query hklm\system\currentcontrolset\services\mpssvc\parameters /v IoTInboundLoopbackPolicy

<span data-ttu-id="d6f33-117">정책을 사용 하도록 설정 하려면 **Windows IoT Core** 장치에서 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6f33-117">To enable the policy execute the following command on the **Windows IoT Core** device:</span></span>

        reg add hklm\system\currentcontrolset\services\mpssvc\parameters /v IoTInboundLoopbackPolicy /t REG_DWORD /d 1
 

## <a name="enabling-loopback-for-a-uwp-application"></a><span data-ttu-id="d6f33-118">UWP 응용 프로그램에 대해 루프백 사용</span><span class="sxs-lookup"><span data-stu-id="d6f33-118">Enabling loopback for a UWP application</span></span>
<span data-ttu-id="d6f33-119">응용 프로그램에 대해 루프백을 사용 하도록 설정 하려면 패키지 제품군 이름이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6f33-119">Before you can enable loopback for an application you will need the package family name.</span></span>  <span data-ttu-id="d6f33-120">**Iotstartup 목록을**실행 하 여 설치 된 응용 프로그램에 대 한 패키지 제품군 이름을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6f33-120">You can find the package family name for an installed application by running **iotstartup list**.</span></span>  <span data-ttu-id="d6f33-121">응용 프로그램에 대 한 **iotstartup 목록** 항목이 IoTCoreDefaultApp\_1w720vyc4ccym! 인 경우 앱에서 패키지 제품군 이름은 IoTCoreDefaultApp\_1w720vyc4ccym입니다.</span><span class="sxs-lookup"><span data-stu-id="d6f33-121">If the **iotstartup list** entry for the application is IoTCoreDefaultApp\_1w720vyc4ccym!App then the package family name is IoTCoreDefaultApp\_1w720vyc4ccym</span></span>

<span data-ttu-id="d6f33-122">클라이언트 연결에 대해 루프백을 사용 `CheckNetIsolation.exe LoopbackExempt -a -n=<AppContainer or Package Family>`하도록 설정 하려면를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6f33-122">To enable loopback for client connections use `CheckNetIsolation.exe LoopbackExempt -a -n=<AppContainer or Package Family>`.</span></span>  <span data-ttu-id="d6f33-123">CheckNetIsolation는 응용 프로그램에 대해 루프백을 구성 하 고 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6f33-123">CheckNetIsolation.exe will configure loopback for the application and exit.</span></span> <span data-ttu-id="d6f33-124">이렇게 하면 응용 프로그램이 서버에 대 한 아웃 바운드 연결을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6f33-124">This will enable the application to make outbound connections to a server.</span></span>

<span data-ttu-id="d6f33-125">예: `CheckNetIsolation.exe LoopbackExempt -a -n=IoTCoreDefaultApp_1w720vyc4ccym`</span><span class="sxs-lookup"><span data-stu-id="d6f33-125">Example: `CheckNetIsolation.exe LoopbackExempt -a -n=IoTCoreDefaultApp_1w720vyc4ccym`</span></span>

<span data-ttu-id="d6f33-126">서버 응용 프로그램에서 인바운드 연결을 받도록 설정 하려면 `CheckNetIsolation.exe LoopbackExempt -is -n=<AppContainer or Package Family>`를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6f33-126">To enable a server application to receive inbound connections use `CheckNetIsolation.exe LoopbackExempt -is -n=<AppContainer or Package Family>`.</span></span> <span data-ttu-id="d6f33-127">아웃 바운드 연결 구성과 달리 인바운드 연결은 서버 응용 프로그램이 연결을 수신 하는 동안 CheckNetIsolation를 계속 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6f33-127">Unlike outbound connection configuration, inbound connections require CheckNetIsolation.exe to run continuously while the server application is receiving connections.</span></span><span data-ttu-id="d6f33-128">  이를 위해서는 10.0.14393 보다 최신 OS 빌드가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6f33-128">  This requires an OS build newer than 10.0.14393.</span></span>

<span data-ttu-id="d6f33-129">예: `CheckNetIsolation.exe LoopbackExempt -is -n=IoTCoreDefaultApp_1w720vyc4ccym`</span><span class="sxs-lookup"><span data-stu-id="d6f33-129">Example: `CheckNetIsolation.exe LoopbackExempt -is -n=IoTCoreDefaultApp_1w720vyc4ccym`</span></span>

<span data-ttu-id="d6f33-130">시작할 때 CheckNetIsolation를 자동으로 실행 하는 가장 좋은 방법은 schtasks.exe를 사용 하는 것입니다.`schtasks /create /tn MyTask /f /sc onstart /ru system /tr "checknetisolation LoopbackExempt -is -n=IoTCoreDefaultApp_1w720vyc4ccym"`</span><span class="sxs-lookup"><span data-stu-id="d6f33-130">The best way to run CheckNetIsolation.exe automatically on startup is to use schtasks.exe: `schtasks /create /tn MyTask /f /sc onstart /ru system /tr "checknetisolation LoopbackExempt -is -n=IoTCoreDefaultApp_1w720vyc4ccym"`</span></span>

<span data-ttu-id="d6f33-131">재부팅 시 tlist.exe 또는 [Windows 장치 포털](https://developer.microsoft.com/en-us/windows/iot/docs/deviceportal) 을 사용 하 여 checknetisolation가 실행 되 고 있는지 확인할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6f33-131">Upon rebooting you should be able to verify that checknetisolation.exe is running by using tlist.exe or [Windows Device Portal](https://developer.microsoft.com/en-us/windows/iot/docs/deviceportal)</span></span>
