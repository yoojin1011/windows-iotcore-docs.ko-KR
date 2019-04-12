---
title: 번개 설치 가이드
author: msalehmsft
ms.author: msaleh
ms.date: 08/28/2017
ms.topic: article
description: 장치에서 매우 DMAP 드라이버를 기본 컨트롤러 드라이버를 변경 하는 방법에 알아봅니다.
keywords: windows iot 번개, 설치, Windows Device Portal 번개 설치
ms.openlocfilehash: 0997638b50f89fd42262df437623bd55380fbb5b
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513198"
---
# <a name="lightning-setup-guide"></a><span data-ttu-id="47c04-104">번개 설치 가이드</span><span class="sxs-lookup"><span data-stu-id="47c04-104">Lightning Setup Guide</span></span>

<span data-ttu-id="47c04-105">이 가이드는 Windows IoT Core 장치에서 매우 직접 메모리 액세스 매핑 (DMAP) 드라이버를 기본 컨트롤러 드라이버를 변경 하는 데 필요한 단계를 안내 합니다.</span><span class="sxs-lookup"><span data-stu-id="47c04-105">This guide will walk you through the steps needed to change the default controller driver to the Lightning direct memory access mapped (DMAP) driver on a Windows IoT Core device.</span></span> <span data-ttu-id="47c04-106">해당 장치에서 매우 사용 응용 프로그램의 사용을 하면이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47c04-106">This will allow the use of Lightning-enabled applications on that device.</span></span>

## <a name="change-the-default-controller-driver"></a><span data-ttu-id="47c04-107">기본 컨트롤러 드라이버 변경</span><span class="sxs-lookup"><span data-stu-id="47c04-107">Change the Default Controller Driver</span></span>

<span data-ttu-id="47c04-108">Windows Device Portal 열고 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="47c04-108">We will want to open the Windows Device Portal.</span></span>

1. <span data-ttu-id="47c04-109">Windows 10 IoT Core 대시보드 응용 프로그램을 사용 하 여 또는 모니터를 보드를 연결 하 여 장치의 IP 주소를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="47c04-109">Locate the IP address of your device, either by using the Windows 10 IoT Core Dashboard application or hooking up your board to a monitor.</span></span>

2. <span data-ttu-id="47c04-110">로컬 컴퓨터에서 웹 브라우저에서이 주소 http://{BoardIPAddress}:8080/를 입력 하 여 Windows 장치 포털 웹 페이지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="47c04-110">From your local machine, open the Windows Devices Portal web page by entering this address http://{BoardIPAddress}:8080/ in your web browser.</span></span>
   ![Windows 장치 포털](../media/LightningSetup/dmap1.png)

3. <span data-ttu-id="47c04-112">Windows 장치 포털 페이지 자격 증명을 요청 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="47c04-112">The Windows Devices Portal Page should ask you for your credentials.</span></span> <span data-ttu-id="47c04-113">기본 사용자 이름은 `Administrator` 이 고 암호는 `p@ssw0rd` 에 사용자 이름과 암호를 포털에 입력 한 후에서 묻는 메시지 암호를 변경 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="47c04-113">The default username is `Administrator` and password is `p@ssw0rd` Note, after entering the username and password, the Portal will ask you if you need to change the password.</span></span> <span data-ttu-id="47c04-114">항상 변경 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="47c04-114">It's always a good practice to change it.</span></span>
   ![Windows 장치 포털 자격 증명](../media/LightningSetup/dmap2.png)

4. <span data-ttu-id="47c04-116">장치 페이지를 열려면 탐색 메뉴에서 장치를 클릭 ![장치 페이지](../media/LightningSetup/dmap3.png)</span><span class="sxs-lookup"><span data-stu-id="47c04-116">Click on Devices in the navigation menu to open the Devices page ![Devices Page](../media/LightningSetup/dmap3.png)</span></span>

5. <span data-ttu-id="47c04-117">장치 페이지는 사용 가능한 컨트롤러 드라이버를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="47c04-117">The Devices page lists the available Controller drivers.</span></span> <span data-ttu-id="47c04-118">기본적으로 드라이버에 현재 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="47c04-118">By default, the Inbox Driver is set to current.</span></span>

6. <span data-ttu-id="47c04-119">드롭다운 메뉴에서에서 직접 메모리 매핑된 드라이버를 선택 하 여 매우 드라이버로 전환 하 고 드라이버 [업데이트] 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="47c04-119">Switch to the Lightning driver by choosing the Direct Memory Mapped Driver from the drop down menu and click the Update Driver Button</span></span><br/>
   ![직접 메모리 매핑된 드라이버 선택](../media/LightningSetup/dmap4.png)

7. <span data-ttu-id="47c04-121">페이지를 사용 하면 드라이버 설치가 완료 되 면 알 때까지 잠시 기다려 주십시오.</span><span class="sxs-lookup"><span data-stu-id="47c04-121">Please wait until the page lets you know when the driver installation is complete.</span></span>
   ![드라이버 설치 완료](../media/LightningSetup/dmap5.png)

8. <span data-ttu-id="47c04-123">다시 부팅이 필요한 경우 에서도 알 페이지 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47c04-123">If a reboot is required, the page will let you know as well.</span></span> <span data-ttu-id="47c04-124">페이지의 맨 위에 있는 단추를 다시 부팅을 사용 하 여 다시 부팅할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47c04-124">You can reboot by using the Reboot button at the top of the page.</span></span>

9. <span data-ttu-id="47c04-125">만들기 및 사용 준비가 이제 응용 프로그램은 번개 직접 메모리 맵핑된 드라이버를 활용 합니다.</span><span class="sxs-lookup"><span data-stu-id="47c04-125">Now you're ready to create and use applications that make use of the Lightning Direct Memory Mapped driver.</span></span>
