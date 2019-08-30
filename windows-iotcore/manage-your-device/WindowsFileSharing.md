---
title: Windows 파일 공유
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Windows 파일 공유를 사용 하 여 장치 간에 파일을 전송 하는 방법에 대해 알아봅니다.
keywords: windows iot, 파일 전송, 파일 공유, windows 파일 공유
ms.openlocfilehash: 00dc17ded4b9c4fbea05faca794766f965d0632a
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "60170398"
---
# <a name="windows-file-sharing"></a><span data-ttu-id="75d18-104">Windows 파일 공유</span><span class="sxs-lookup"><span data-stu-id="75d18-104">Windows file sharing</span></span>

<span data-ttu-id="75d18-105">Windows 파일 공유를 사용 하 여 장치 간에 파일을 전송할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75d18-105">You can use Windows file sharing to transfer files to and from your device.</span></span>

## <a name="accessing-your-files-using-windows-file-sharing"></a><span data-ttu-id="75d18-106">Windows 파일 공유를 사용 하 여 파일 액세스</span><span class="sxs-lookup"><span data-stu-id="75d18-106">Accessing your files using Windows file sharing</span></span>
* <span data-ttu-id="75d18-107">Windows IoT Core 장치의 파일 공유 서버는 부팅 시 자동으로 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="75d18-107">The file sharing server on your Windows IoT Core device starts automatically on boot.</span></span>  <span data-ttu-id="75d18-108">연결 하려면 장치의 IP 주소가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="75d18-108">In order to connect to it, you need the IP address of your device.</span></span>  <span data-ttu-id="75d18-109">장치를 시작할 때 부팅 되는 기본 앱에서 IP 주소를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75d18-109">You can find the IP address on the default app that boots when your device starts.</span></span>

    ![Windows IoT Core의 DefaultApp](../media/WindowsFileSharing/DefaultApp.png)
    
* <span data-ttu-id="75d18-111">IP가 있으면 컴퓨터에서 **파일 탐색기** 를 열고를 입력 `\\<TARGET_DEVICE>\c$`합니다. 여기서 `<TARGET_DEVICE>` 은 Windows IoT Core 장치의 이름 또는 IP 주소입니다. enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="75d18-111">Once you have the IP, open up **File Explorer** on your computer and type `\\<TARGET_DEVICE>\c$`, where `<TARGET_DEVICE>` is either the name or the IP Address of your Windows IoT Core device, then hit Enter.</span></span>  

<span data-ttu-id="75d18-112">메시지가 표시 되 면 관리자 사용자 이름과 암호를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="75d18-112">Enter your administrator username and password if prompted.</span></span> <span data-ttu-id="75d18-113">사용자 이름은 Windows IoT Core 장치의 IP 주소 앞에와 야 합니다.</span><span class="sxs-lookup"><span data-stu-id="75d18-113">The username should be prefixed with the IP Address of your Windows IoT Core device.</span></span> <span data-ttu-id="75d18-114">예: **이름** `192.168.1.118\Administrator`  **암호:** `{your_password}`.</span><span class="sxs-lookup"><span data-stu-id="75d18-114">Example: **Username:** `192.168.1.118\Administrator`  **Password:** `{your_password}`.</span></span>

![파일 탐색기](../media/WindowsFileSharing/smb_file_explorer.png)

* <span data-ttu-id="75d18-116">이제 Windows 파일 공유를 사용 하 여 장치에서 파일에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75d18-116">Now you can access the files on your device using Windows file sharing.</span></span>

## <a name="starting-and-stopping-the-file-sharing-server"></a><span data-ttu-id="75d18-117">파일 공유 서버 시작 및 중지</span><span class="sxs-lookup"><span data-stu-id="75d18-117">Starting and stopping the file sharing server</span></span>
* <span data-ttu-id="75d18-118">[PowerShell](../connect-your-device/powershell.md) 또는 [SSH](../connect-your-device/ssh.md)를 통해 장치에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="75d18-118">Connect to your device through [PowerShell](../connect-your-device/powershell.md) or [SSH](../connect-your-device/ssh.md).</span></span>
* <span data-ttu-id="75d18-119">기본적으로 파일 공유 서버는 장치가 부팅 될 때 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="75d18-119">By default the file sharing  server is started when the device is booted.</span></span>
* <span data-ttu-id="75d18-120">파일 공유 서버를 중지 하려면 다음을 입력 합니다.`net stop Server /y`</span><span class="sxs-lookup"><span data-stu-id="75d18-120">To stop the file sharing  server, type `net stop Server /y`</span></span>
* <span data-ttu-id="75d18-121">파일 공유 서버를 시작 하려면 다음을 입력 합니다.`net start Server`</span><span class="sxs-lookup"><span data-stu-id="75d18-121">To start the file sharing  server, type `net start Server`</span></span>

    ![서버 시작 및 중지](../media/WindowsFileSharing/smb_start_stop.png)
    
## <a name="disabling-and-enabling-the-file-sharing-server-on-startup"></a><span data-ttu-id="75d18-123">시작할 때 파일 공유 서버 사용 안 함 및 사용</span><span class="sxs-lookup"><span data-stu-id="75d18-123">Disabling and enabling the file sharing server on startup</span></span>
* <span data-ttu-id="75d18-124">[PowerShell](../connect-your-device/powershell.md) 또는 [SSH](../connect-your-device/ssh.md)를 통해 장치에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="75d18-124">Connect to your device through [PowerShell](../connect-your-device/powershell.md) or [SSH](../connect-your-device/ssh.md).</span></span>
* <span data-ttu-id="75d18-125">기본적으로 파일 공유 서버는 장치가 부팅 될 때 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="75d18-125">By default the file sharing  server is started when the device is booted.</span></span>
* <span data-ttu-id="75d18-126">장치가 시작 될 때 시작 되지 않도록 파일 공유 서버를 사용 하지 않도록 설정 하려면 다음을 입력 합니다.`reg add HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\lanmanserver /v Start /t REG_DWORD /d 0x3 /f`</span><span class="sxs-lookup"><span data-stu-id="75d18-126">To disable the file sharing  server so that it does not start when the device starts, type `reg add HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\lanmanserver /v Start /t REG_DWORD /d 0x3 /f`</span></span>
* <span data-ttu-id="75d18-127">장치가 시작 될 때가 시작 되도록 파일 공유 서버를 사용 하도록 설정 하려면 다음을 입력 합니다.`reg add HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\lanmanserver /v Start /t REG_DWORD /d 0x2 /f`</span><span class="sxs-lookup"><span data-stu-id="75d18-127">To enable the file sharing  server so that starts when the device starts, type `reg add HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\lanmanserver /v Start /t REG_DWORD /d 0x2 /f`</span></span>

    ![서버 사용 안 함](../media/WindowsFileSharing/smb_enable_disable.png)
