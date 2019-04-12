---
title: 파일 전송 프로토콜
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 장치에서 파일을 전송할 파일 전송 프로토콜 (FTP)를 사용 하는 방법에 알아봅니다.
keywords: windows iot, FTP, 파일 전송 프로토콜, 파일 전송 장치
ms.openlocfilehash: 43a64e186c2e783624bb47b89e4fa6322c93e04d
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512662"
---
# <a name="file-transfer-protocol"></a><span data-ttu-id="8e2be-104">파일 전송 프로토콜</span><span class="sxs-lookup"><span data-stu-id="8e2be-104">File Transfer Protocol</span></span>
<span data-ttu-id="8e2be-105">(FTP (파일 전송 프로토콜)을 사용 하면 Windows 10 IoT Core 장치에서 파일을 전송할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e2be-105">The File Transfer Protocol (FTP) allows you to transfer files to and from your Windows 10 IoT Core device</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8e2be-106">FTP는 초기 개발 프로세스를 간편 하는 개발자에 일반적으로 권장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8e2be-106">FTP is recommended generally for developers to ease the initial development process.</span></span> <span data-ttu-id="8e2be-107">소매 장치에서 FTP를 사용 하는 것은 좋지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8e2be-107">We do not recommend using FTP in retail devices.</span></span>

## <a name="starting-the-ftp-server-on-your-device"></a><span data-ttu-id="8e2be-108">장치에서 FTP 서버를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="8e2be-108">Starting the FTP server on your device</span></span>
* <span data-ttu-id="8e2be-109">기본적으로 FTP 서버는 IoT Core 장치에서 비활성화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8e2be-109">By default, the FTP server is disabled on your IoT Core device.</span></span>  <span data-ttu-id="8e2be-110">장치에서 FTP 서버를 시작 하려면 먼저 통해 장치에 연결할 [PowerShell](../connect-your-device/PowerShell.md) 하거나 [SSH](../connect-your-device/SSH.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="8e2be-110">In order to start the FTP server on your device, first you need to connect to your device through [PowerShell](../connect-your-device/PowerShell.md) or [SSH](../connect-your-device/SSH.md).</span></span>
* <span data-ttu-id="8e2be-111">형식</span><span class="sxs-lookup"><span data-stu-id="8e2be-111">Type</span></span> `start C:\Windows\System32\ftpd.exe`
* <span data-ttu-id="8e2be-112">서버를 입력 하 여 실행 되 고 있는지 확인할 수 있습니다 `tlist`, 실행 중인 모든 프로세스는 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e2be-112">You can check that the server is running by typing `tlist`, which will list all the running processes.</span></span>  <span data-ttu-id="8e2be-113">FTP 서버를 실행 하는 경우 표시 됩니다 `ftpd.exe` 목록에서입니다.</span><span class="sxs-lookup"><span data-stu-id="8e2be-113">If the FTP server is running, you should see `ftpd.exe` in the list.</span></span>

![FTP 시작](../media/ftp/ftp_start.png)

## <a name="stopping-the-ftp-server-on-your-devicea-namestopftp"></a><span data-ttu-id="8e2be-115">장치에서 FTP 서버를 중지합니다.<a name="stopftp"/></span><span class="sxs-lookup"><span data-stu-id="8e2be-115">Stopping the FTP server on your device<a name="stopftp"/></span></span>
* <span data-ttu-id="8e2be-116">IoT Core 장치에서 FTP 서버를 중지 하려면 먼저 통해 장치에 연결할 [PowerShell](../connect-your-device/PowerShell.md) 하거나 [SSH](../connect-your-device/SSH.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="8e2be-116">In order to stop the FTP server on your IoT Core device, first you need to connect to your device through [PowerShell](../connect-your-device/PowerShell.md) or [SSH](../connect-your-device/SSH.md).</span></span>
* <span data-ttu-id="8e2be-117">PowerShell을 사용 하 여 연결 하는 경우 입력 `kill -processname ftpd*` FTP 프로세스를 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e2be-117">If you connected using PowerShell, type `kill -processname ftpd*` to stop the FTP process.</span></span>

![FTP PowerShell 중지](../media/ftp/ftp_kill_powershell.png)

* <span data-ttu-id="8e2be-119">SSH를 사용 하 여 연결 하는 경우 입력 `kill ftpd*` FTP 프로세스를 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e2be-119">If you connected using SSH, type `kill ftpd*` to stop the FTP process.</span></span>

![FTP SSH 중지](../media/ftp/ftp_kill_ssh.png)

## <a name="accessing-your-files-over-ftp"></a><span data-ttu-id="8e2be-121">FTP를 통한 파일 액세스</span><span class="sxs-lookup"><span data-stu-id="8e2be-121">Accessing your files over FTP</span></span>
* <span data-ttu-id="8e2be-122">FTP 서버의 IoT Core 장치 부팅 시 자동으로 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="8e2be-122">The FTP server on your IoT Core device starts automatically on boot.</span></span>  <span data-ttu-id="8e2be-123">연결 하기 위해 장치의 IP 주소가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e2be-123">In order to connect to it, you need the IP address of your device.</span></span>  <span data-ttu-id="8e2be-124">장치를 시작할 때 부팅 하는 기본 앱에서 IP 주소를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e2be-124">You can find the IP address on the default app that boots when your device starts.</span></span>

![Windows IoT Core에 DefaultApp](../media/ftp/DefaultApp.png)

* <span data-ttu-id="8e2be-126">IP를 만든 후 열어 **파일 탐색기** 에 입력 하 여 PC `ftp://<TARGET_DEVICE>`여기서 `<TARGET_DEVICE>` 는 이름 또는 IP 주소에 장치를 다음 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="8e2be-126">Once you have the IP, open up **File Explorer** on your PC and type `ftp://<TARGET_DEVICE>`, where `<TARGET_DEVICE>` is either the name or the IP address of your device, then hit Enter.</span></span>  <span data-ttu-id="8e2be-127">메시지가 표시 되 면 관리자 사용자 이름 및 암호를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e2be-127">Enter your administrator username and password if prompted.</span></span>

![FTP 탐색기](../media/ftp/ftp_explorer.png)

* <span data-ttu-id="8e2be-129">이제 FTP를 통해 장치에서 파일을 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e2be-129">Now you can access the files on your device through FTP.</span></span>

## <a name="changing-the-root-ftp-directory"></a><span data-ttu-id="8e2be-130">FTP 루트 디렉터리를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="8e2be-130">Changing the root FTP directory</span></span>
* <span data-ttu-id="8e2be-131">기본적으로 FTP 서버에서 장치의 루트 디렉터리 c: 모든 폴더를 표시\\합니다.</span><span class="sxs-lookup"><span data-stu-id="8e2be-131">By default the FTP server displays all the folders in the device's root directory C:\\.</span></span>  <span data-ttu-id="8e2be-132">루트 디렉터리를 변경 하려면 루트 디렉터리를 매개 변수로 전달 해야 할 점을 제외 하 고 FTP 서버를 시작 하려면 동일한 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e2be-132">In order to change the root directory, follow the same steps to start the FTP server, except you need to pass in the root directory as a parameter.</span></span>
* <span data-ttu-id="8e2be-133">변경 하려면 먼저를 통해 장치에 연결 [PowerShell](../connect-your-device/PowerShell.md) 하거나 [SSH](../connect-your-device/SSH.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="8e2be-133">In order to change it, first connect to your device through [PowerShell](../connect-your-device/PowerShell.md) or [SSH](../connect-your-device/SSH.md).</span></span>
* <span data-ttu-id="8e2be-134">[중지](#stopftp) FTP 프로세스가 이미 실행 중인 경우.</span><span class="sxs-lookup"><span data-stu-id="8e2be-134">[Stop](#stopftp) the FTP process if it's already running.</span></span>
* <span data-ttu-id="8e2be-135">형식 `start C:\Windows\System32\ftpd.exe <PATH_TO_DIRECTORY>`, 여기서 `<PATH_TO_DIRECTORY>` 같은 루트 디렉터리로 설정 하려는 디렉터리의 절대 경로 `C:\Users\DefaultAccount`합니다.</span><span class="sxs-lookup"><span data-stu-id="8e2be-135">Type `start C:\Windows\System32\ftpd.exe <PATH_TO_DIRECTORY>`, where `<PATH_TO_DIRECTORY>` is the absolute path to the directory you want to set as the root directory, such as `C:\Users\DefaultAccount`.</span></span>

![매개 변수를 사용 하 여 FTP 시작](../media/ftp/ftp_start_parameter.png)

<span data-ttu-id="8e2be-137">이제 FTP 통해 장치에 연결할 때 설정 하는 루트 디렉터리의 내용을 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="8e2be-137">Now when you connect to your device through FTP, you will see the contents of the root directory you set.</span></span>

![새 루트 디렉터리를 사용 하 여 FTP 탐색기](../media/ftp/ftp_explorer_parameter.png)

<span data-ttu-id="8e2be-139">이와 같이 변경 영구 하려면 호출을 추가 해야 `start ftpd.exe <PATH_TO_DIRECTORY>` 여기서 `<PATH_TO_DIRECTORY>` 같은 루트 디렉터리로 설정 하려는 디렉터리의 절대 경로 `C:\Data\Users\DefaultAccount` OEMCustomization.cmd에에서 배치</span><span class="sxs-lookup"><span data-stu-id="8e2be-139">In order to make this change permanent, you need to add a call to `start ftpd.exe <PATH_TO_DIRECTORY>` where `<PATH_TO_DIRECTORY>` is the absolute path to the directory you want to set as the root directory, such as `C:\Data\Users\DefaultAccount` to OEMCustomization.cmd and place it in</span></span> `C:\Windows\System32`
