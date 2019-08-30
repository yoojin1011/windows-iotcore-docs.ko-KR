---
title: 파일 전송 프로토콜
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 파일 전송 프로토콜 (FTP)를 사용 하 여 장치 간에 파일을 전송 하는 방법에 대해 알아봅니다.
keywords: windows iot, FTP, 파일 전송 프로토콜, 파일 전송, 장치
ms.openlocfilehash: 43a64e186c2e783624bb47b89e4fa6322c93e04d
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "60169191"
---
# <a name="file-transfer-protocol"></a><span data-ttu-id="0fefa-104">파일 전송 프로토콜</span><span class="sxs-lookup"><span data-stu-id="0fefa-104">File Transfer Protocol</span></span>
<span data-ttu-id="0fefa-105">FTP (파일 전송 프로토콜)를 사용 하 여 Windows 10 IoT Core 장치 간에 파일을 전송할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0fefa-105">The File Transfer Protocol (FTP) allows you to transfer files to and from your Windows 10 IoT Core device</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0fefa-106">일반적으로 개발자가 초기 개발 프로세스를 쉽게 수행할 수 있도록 FTP를 권장 합니다.</span><span class="sxs-lookup"><span data-stu-id="0fefa-106">FTP is recommended generally for developers to ease the initial development process.</span></span> <span data-ttu-id="0fefa-107">일반 정품 장치에서 FTP를 사용 하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0fefa-107">We do not recommend using FTP in retail devices.</span></span>

## <a name="starting-the-ftp-server-on-your-device"></a><span data-ttu-id="0fefa-108">장치에서 FTP 서버 시작</span><span class="sxs-lookup"><span data-stu-id="0fefa-108">Starting the FTP server on your device</span></span>
* <span data-ttu-id="0fefa-109">기본적으로는 IoT Core 장치에서 FTP 서버를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0fefa-109">By default, the FTP server is disabled on your IoT Core device.</span></span>  <span data-ttu-id="0fefa-110">장치에서 FTP 서버를 시작 하려면 먼저 [PowerShell](../connect-your-device/PowerShell.md) 또는 [SSH](../connect-your-device/SSH.md)를 통해 장치에 연결 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0fefa-110">In order to start the FTP server on your device, first you need to connect to your device through [PowerShell](../connect-your-device/PowerShell.md) or [SSH](../connect-your-device/SSH.md).</span></span>
* <span data-ttu-id="0fefa-111">`start C:\Windows\System32\ftpd.exe`를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="0fefa-111">Type `start C:\Windows\System32\ftpd.exe`</span></span>
* <span data-ttu-id="0fefa-112">실행 중인 모든 프로세스를 나열 하는를 입력 `tlist`하 여 서버가 실행 중인지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0fefa-112">You can check that the server is running by typing `tlist`, which will list all the running processes.</span></span>  <span data-ttu-id="0fefa-113">FTP 서버가를 실행 하는 경우 목록에이 `ftpd.exe` 표시 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0fefa-113">If the FTP server is running, you should see `ftpd.exe` in the list.</span></span>

![FTP 시작](../media/ftp/ftp_start.png)

## <a name="stopping-the-ftp-server-on-your-devicea-namestopftp"></a><span data-ttu-id="0fefa-115">장치에서 FTP 서버를 중지 하는 중<a name="stopftp"/></span><span class="sxs-lookup"><span data-stu-id="0fefa-115">Stopping the FTP server on your device<a name="stopftp"/></span></span>
* <span data-ttu-id="0fefa-116">IoT Core 장치에서 FTP 서버를 중지 하려면 먼저 [PowerShell](../connect-your-device/PowerShell.md) 또는 [SSH](../connect-your-device/SSH.md)를 통해 장치에 연결 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0fefa-116">In order to stop the FTP server on your IoT Core device, first you need to connect to your device through [PowerShell](../connect-your-device/PowerShell.md) or [SSH](../connect-your-device/SSH.md).</span></span>
* <span data-ttu-id="0fefa-117">PowerShell을 사용 하 여 연결한 경우 `kill -processname ftpd*` 를 입력 하 여 FTP 프로세스를 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="0fefa-117">If you connected using PowerShell, type `kill -processname ftpd*` to stop the FTP process.</span></span>

![FTP PowerShell 중지](../media/ftp/ftp_kill_powershell.png)

* <span data-ttu-id="0fefa-119">SSH를 사용 하 여 연결한 경우 `kill ftpd*` 를 입력 하 여 FTP 프로세스를 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="0fefa-119">If you connected using SSH, type `kill ftpd*` to stop the FTP process.</span></span>

![FTP SSH 중지](../media/ftp/ftp_kill_ssh.png)

## <a name="accessing-your-files-over-ftp"></a><span data-ttu-id="0fefa-121">FTP를 통해 파일에 액세스</span><span class="sxs-lookup"><span data-stu-id="0fefa-121">Accessing your files over FTP</span></span>
* <span data-ttu-id="0fefa-122">IoT Core 장치의 FTP 서버는 부팅 시 자동으로 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0fefa-122">The FTP server on your IoT Core device starts automatically on boot.</span></span>  <span data-ttu-id="0fefa-123">연결 하려면 장치의 IP 주소가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="0fefa-123">In order to connect to it, you need the IP address of your device.</span></span>  <span data-ttu-id="0fefa-124">장치를 시작할 때 부팅 되는 기본 앱에서 IP 주소를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0fefa-124">You can find the IP address on the default app that boots when your device starts.</span></span>

![Windows IoT Core의 DefaultApp](../media/ftp/DefaultApp.png)

* <span data-ttu-id="0fefa-126">IP가 있으면 PC에서 **파일 탐색기** 를 열고를 입력 `ftp://<TARGET_DEVICE>`합니다. 여기서 `<TARGET_DEVICE>` 은 장치의 이름 또는 IP 주소입니다. enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="0fefa-126">Once you have the IP, open up **File Explorer** on your PC and type `ftp://<TARGET_DEVICE>`, where `<TARGET_DEVICE>` is either the name or the IP address of your device, then hit Enter.</span></span>  <span data-ttu-id="0fefa-127">메시지가 표시 되 면 관리자 사용자 이름과 암호를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="0fefa-127">Enter your administrator username and password if prompted.</span></span>

![FTP 탐색기](../media/ftp/ftp_explorer.png)

* <span data-ttu-id="0fefa-129">이제 FTP를 통해 장치의 파일에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0fefa-129">Now you can access the files on your device through FTP.</span></span>

## <a name="changing-the-root-ftp-directory"></a><span data-ttu-id="0fefa-130">루트 FTP 디렉터리 변경</span><span class="sxs-lookup"><span data-stu-id="0fefa-130">Changing the root FTP directory</span></span>
* <span data-ttu-id="0fefa-131">기본적으로 FTP 서버는 장치의 루트 디렉터리 C:\\에 모든 폴더를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="0fefa-131">By default the FTP server displays all the folders in the device's root directory C:\\.</span></span>  <span data-ttu-id="0fefa-132">루트 디렉터리를 변경 하려면 루트 디렉터리를 매개 변수로 전달 해야 한다는 점을 제외 하 고 동일한 단계를 수행 하 여 FTP 서버를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="0fefa-132">In order to change the root directory, follow the same steps to start the FTP server, except you need to pass in the root directory as a parameter.</span></span>
* <span data-ttu-id="0fefa-133">이를 변경 하려면 먼저 [PowerShell](../connect-your-device/PowerShell.md) 또는 [SSH](../connect-your-device/SSH.md)를 통해 장치에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="0fefa-133">In order to change it, first connect to your device through [PowerShell](../connect-your-device/PowerShell.md) or [SSH](../connect-your-device/SSH.md).</span></span>
* <span data-ttu-id="0fefa-134">FTP 프로세스가 이미 실행 중인 경우이를 [중지](#stopftp) 합니다.</span><span class="sxs-lookup"><span data-stu-id="0fefa-134">[Stop](#stopftp) the FTP process if it's already running.</span></span>
* <span data-ttu-id="0fefa-135">을 `start C:\Windows\System32\ftpd.exe <PATH_TO_DIRECTORY>`입력 `C:\Users\DefaultAccount`합니다 `<PATH_TO_DIRECTORY>` . 여기서은 루트 디렉터리 (예:)로 설정 하려는 디렉터리의 절대 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="0fefa-135">Type `start C:\Windows\System32\ftpd.exe <PATH_TO_DIRECTORY>`, where `<PATH_TO_DIRECTORY>` is the absolute path to the directory you want to set as the root directory, such as `C:\Users\DefaultAccount`.</span></span>

![FTP 시작 매개 변수](../media/ftp/ftp_start_parameter.png)

<span data-ttu-id="0fefa-137">이제 FTP를 통해 장치에 연결할 때 설정 하는 루트 디렉터리의 내용이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0fefa-137">Now when you connect to your device through FTP, you will see the contents of the root directory you set.</span></span>

![새 루트 디렉터리가 있는 FTP 탐색기](../media/ftp/ftp_explorer_parameter.png)

<span data-ttu-id="0fefa-139">이 변경 내용을 영구적으로 적용 하려면에 대 `start ftpd.exe <PATH_TO_DIRECTORY>` 한 호출을 추가 해야 합니다. 여기서은 `C:\Data\Users\DefaultAccount` 루트 디렉터리로 설정할 디렉터리의 절대 경로입니다. 여기 `<PATH_TO_DIRECTORY>` 에는 oemcustomization 지정. cmd를 입력 하 고`C:\Windows\System32`</span><span class="sxs-lookup"><span data-stu-id="0fefa-139">In order to make this change permanent, you need to add a call to `start ftpd.exe <PATH_TO_DIRECTORY>` where `<PATH_TO_DIRECTORY>` is the absolute path to the directory you want to set as the root directory, such as `C:\Data\Users\DefaultAccount` to OEMCustomization.cmd and place it in `C:\Windows\System32`</span></span>
