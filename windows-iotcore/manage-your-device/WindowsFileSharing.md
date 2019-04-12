---
title: Windows 파일 공유
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 장치에서 파일을 전송 하려면 Windows 파일 공유를 사용 하는 방법에 알아봅니다.
keywords: windows iot, 파일 전송, 파일 공유를 windows 파일 공유
ms.openlocfilehash: 00dc17ded4b9c4fbea05faca794766f965d0632a
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513870"
---
# <a name="windows-file-sharing"></a><span data-ttu-id="fdff9-104">Windows 파일 공유</span><span class="sxs-lookup"><span data-stu-id="fdff9-104">Windows file sharing</span></span>

<span data-ttu-id="fdff9-105">장치에서 파일을 전송 하려면 Windows 파일 공유를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fdff9-105">You can use Windows file sharing to transfer files to and from your device.</span></span>

## <a name="accessing-your-files-using-windows-file-sharing"></a><span data-ttu-id="fdff9-106">Windows 파일 공유를 사용 하 여 파일 액세스</span><span class="sxs-lookup"><span data-stu-id="fdff9-106">Accessing your files using Windows file sharing</span></span>
* <span data-ttu-id="fdff9-107">Windows IoT Core 장치에서 서버를 공유 하는 파일을 부팅 시 자동으로 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="fdff9-107">The file sharing server on your Windows IoT Core device starts automatically on boot.</span></span>  <span data-ttu-id="fdff9-108">연결 하기 위해 장치의 IP 주소가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="fdff9-108">In order to connect to it, you need the IP address of your device.</span></span>  <span data-ttu-id="fdff9-109">장치를 시작할 때 부팅 하는 기본 앱에서 IP 주소를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fdff9-109">You can find the IP address on the default app that boots when your device starts.</span></span>

    ![Windows IoT Core에 DefaultApp](../media/WindowsFileSharing/DefaultApp.png)
    
* <span data-ttu-id="fdff9-111">IP를 만든 후 열어 **파일 탐색기** 입력 하 여 컴퓨터에 `\\<TARGET_DEVICE>\c$`여기서 `<TARGET_DEVICE>` 이름 또는 IP 주소의 Windows IoT Core 장치를 다음 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="fdff9-111">Once you have the IP, open up **File Explorer** on your computer and type `\\<TARGET_DEVICE>\c$`, where `<TARGET_DEVICE>` is either the name or the IP Address of your Windows IoT Core device, then hit Enter.</span></span>  

<span data-ttu-id="fdff9-112">메시지가 표시 되 면 관리자 사용자 이름 및 암호를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="fdff9-112">Enter your administrator username and password if prompted.</span></span> <span data-ttu-id="fdff9-113">사용자 이름이 Windows IoT Core 장치 IP 주소 접두사로 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fdff9-113">The username should be prefixed with the IP Address of your Windows IoT Core device.</span></span> <span data-ttu-id="fdff9-114">예: **사용자 이름:** `192.168.1.118\Administrator`  **암호:** `{your_password}`합니다.</span><span class="sxs-lookup"><span data-stu-id="fdff9-114">Example: **Username:** `192.168.1.118\Administrator`  **Password:** `{your_password}`.</span></span>

![파일 탐색기](../media/WindowsFileSharing/smb_file_explorer.png)

* <span data-ttu-id="fdff9-116">이제 Windows 파일 공유를 사용 하 여 장치에서 파일을 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fdff9-116">Now you can access the files on your device using Windows file sharing.</span></span>

## <a name="starting-and-stopping-the-file-sharing-server"></a><span data-ttu-id="fdff9-117">시작 하 고 파일 서버 공유를 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="fdff9-117">Starting and stopping the file sharing server</span></span>
* <span data-ttu-id="fdff9-118">통해 장치에 연결할 [PowerShell](../connect-your-device/powershell.md) 하거나 [SSH](../connect-your-device/ssh.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="fdff9-118">Connect to your device through [PowerShell](../connect-your-device/powershell.md) or [SSH](../connect-your-device/ssh.md).</span></span>
* <span data-ttu-id="fdff9-119">기본적으로 파일 서버 공유 장치 부팅 될 때 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fdff9-119">By default the file sharing  server is started when the device is booted.</span></span>
* <span data-ttu-id="fdff9-120">파일 서버 공유를 중지 하려면 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="fdff9-120">To stop the file sharing  server, type</span></span> `net stop Server /y`
* <span data-ttu-id="fdff9-121">파일 서버 공유를 시작 하려면 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="fdff9-121">To start the file sharing  server, type</span></span> `net start Server`

    ![서버 시작 및 중지](../media/WindowsFileSharing/smb_start_stop.png)
    
## <a name="disabling-and-enabling-the-file-sharing-server-on-startup"></a><span data-ttu-id="fdff9-123">사용 하지 않도록 설정 하 고 시작 시 서버를 공유 하는 파일을 사용 하도록 설정</span><span class="sxs-lookup"><span data-stu-id="fdff9-123">Disabling and enabling the file sharing server on startup</span></span>
* <span data-ttu-id="fdff9-124">통해 장치에 연결할 [PowerShell](../connect-your-device/powershell.md) 하거나 [SSH](../connect-your-device/ssh.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="fdff9-124">Connect to your device through [PowerShell](../connect-your-device/powershell.md) or [SSH](../connect-your-device/ssh.md).</span></span>
* <span data-ttu-id="fdff9-125">기본적으로 파일 서버 공유 장치 부팅 될 때 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fdff9-125">By default the file sharing  server is started when the device is booted.</span></span>
* <span data-ttu-id="fdff9-126">서버를 공유 하 여 장치를 시작할 때 시작 되지 않도록 파일을 사용 하지 않으려면 입력</span><span class="sxs-lookup"><span data-stu-id="fdff9-126">To disable the file sharing  server so that it does not start when the device starts, type</span></span> `reg add HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\lanmanserver /v Start /t REG_DWORD /d 0x3 /f`
* <span data-ttu-id="fdff9-127">장치가 시작 되 면 작업이 시작 되는 서버를 공유 하는 파일을 사용 하도록 설정 하려면 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="fdff9-127">To enable the file sharing  server so that starts when the device starts, type</span></span> `reg add HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\lanmanserver /v Start /t REG_DWORD /d 0x2 /f`

    ![서버 사용 안 함](../media/WindowsFileSharing/smb_enable_disable.png)
