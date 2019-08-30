---
title: 라이트닝 설정 가이드
author: msalehmsft
ms.author: msaleh
ms.date: 08/28/2017
ms.topic: article
description: 장치에서 기본 컨트롤러 드라이버를 라이트닝 6MAP 드라이버로 변경 하는 방법에 대해 알아봅니다.
keywords: windows iot, 번개, 설정, 번개 설정, Windows 장치 포털
ms.openlocfilehash: 0997638b50f89fd42262df437623bd55380fbb5b
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "60167871"
---
# <a name="lightning-setup-guide"></a><span data-ttu-id="3898b-104">라이트닝 설정 가이드</span><span class="sxs-lookup"><span data-stu-id="3898b-104">Lightning Setup Guide</span></span>

<span data-ttu-id="3898b-105">이 가이드에서는 기본 컨트롤러 드라이버를 Windows IoT Core 장치의 wdirect 메모리 액세스 매핑된 (WMAP) 드라이버로 변경 하는 데 필요한 단계를 안내 합니다.</span><span class="sxs-lookup"><span data-stu-id="3898b-105">This guide will walk you through the steps needed to change the default controller driver to the Lightning direct memory access mapped (DMAP) driver on a Windows IoT Core device.</span></span> <span data-ttu-id="3898b-106">그러면 해당 장치에서 번개 지원 응용 프로그램을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3898b-106">This will allow the use of Lightning-enabled applications on that device.</span></span>

## <a name="change-the-default-controller-driver"></a><span data-ttu-id="3898b-107">기본 컨트롤러 드라이버 변경</span><span class="sxs-lookup"><span data-stu-id="3898b-107">Change the Default Controller Driver</span></span>

<span data-ttu-id="3898b-108">Windows 장치 포털을 열 것입니다.</span><span class="sxs-lookup"><span data-stu-id="3898b-108">We will want to open the Windows Device Portal.</span></span>

1. <span data-ttu-id="3898b-109">Windows 10 IoT Core 대시보드 응용 프로그램을 사용 하거나 보드에 보드를 연결 하 여 장치의 IP 주소를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="3898b-109">Locate the IP address of your device, either by using the Windows 10 IoT Core Dashboard application or hooking up your board to a monitor.</span></span>

2. <span data-ttu-id="3898b-110">로컬 컴퓨터에서 웹 브라우저에 http://{BoardIPAddress}: 8080 주소를 입력 하 여 Windows 장치 포털 웹 페이지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="3898b-110">From your local machine, open the Windows Devices Portal web page by entering this address http://{BoardIPAddress}:8080/ in your web browser.</span></span>
   <span data-ttu-id="3898b-111">![Windows 장치 포털](../media/LightningSetup/dmap1.png)</span><span class="sxs-lookup"><span data-stu-id="3898b-111">![Windows Devices Portal](../media/LightningSetup/dmap1.png)</span></span>

3. <span data-ttu-id="3898b-112">Windows 장치 포털 페이지에서 자격 증명을 요청 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3898b-112">The Windows Devices Portal Page should ask you for your credentials.</span></span> <span data-ttu-id="3898b-113">기본 사용자 이름은 `Administrator` 이며 암호는 `p@ssw0rd` 사용자 이름 및 암호를 입력 한 후 암호를 변경 해야 하는지 여부를 묻는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3898b-113">The default username is `Administrator` and password is `p@ssw0rd` Note, after entering the username and password, the Portal will ask you if you need to change the password.</span></span> <span data-ttu-id="3898b-114">이를 변경 하는 것이 항상 좋은 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="3898b-114">It's always a good practice to change it.</span></span>
   <span data-ttu-id="3898b-115">![Windows 장치 포털 자격 증명](../media/LightningSetup/dmap2.png)</span><span class="sxs-lookup"><span data-stu-id="3898b-115">![Windows Devices Portal Credentials](../media/LightningSetup/dmap2.png)</span></span>

4. <span data-ttu-id="3898b-116">탐색 메뉴에서 장치를 클릭 하 여 장치 페이지 ![장치 페이지를 엽니다.](../media/LightningSetup/dmap3.png)</span><span class="sxs-lookup"><span data-stu-id="3898b-116">Click on Devices in the navigation menu to open the Devices page ![Devices Page](../media/LightningSetup/dmap3.png)</span></span>

5. <span data-ttu-id="3898b-117">장치 페이지에 사용 가능한 컨트롤러 드라이버가 나열 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3898b-117">The Devices page lists the available Controller drivers.</span></span> <span data-ttu-id="3898b-118">기본적으로 수신함 드라이버는 current로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3898b-118">By default, the Inbox Driver is set to current.</span></span>

6. <span data-ttu-id="3898b-119">드롭다운 메뉴에서 직접 메모리 매핑된 드라이버를 선택 하 고 드라이버 업데이트 단추를 클릭 하 여 번개 드라이버로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="3898b-119">Switch to the Lightning driver by choosing the Direct Memory Mapped Driver from the drop down menu and click the Update Driver Button</span></span><br/>
   <span data-ttu-id="3898b-120">![직접 메모리 매핑된 드라이버 선택](../media/LightningSetup/dmap4.png)</span><span class="sxs-lookup"><span data-stu-id="3898b-120">![Select Direct Memory Mapped Driver](../media/LightningSetup/dmap4.png)</span></span>

7. <span data-ttu-id="3898b-121">드라이버 설치가 완료 되 면 페이지에서 페이지를 확인할 수 있을 때까지 기다려 주세요.</span><span class="sxs-lookup"><span data-stu-id="3898b-121">Please wait until the page lets you know when the driver installation is complete.</span></span>
   <span data-ttu-id="3898b-122">![드라이버 설치 완료](../media/LightningSetup/dmap5.png)</span><span class="sxs-lookup"><span data-stu-id="3898b-122">![Driver Installation Complete](../media/LightningSetup/dmap5.png)</span></span>

8. <span data-ttu-id="3898b-123">다시 부팅 해야 하는 경우 페이지에도 알려 주는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="3898b-123">If a reboot is required, the page will let you know as well.</span></span> <span data-ttu-id="3898b-124">페이지 맨 위에 있는 다시 부팅 단추를 사용 하 여 다시 부팅할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3898b-124">You can reboot by using the Reboot button at the top of the page.</span></span>

9. <span data-ttu-id="3898b-125">이제 번개 직접 메모리 매핑된 드라이버를 활용 하는 응용 프로그램을 만들고 사용할 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3898b-125">Now you're ready to create and use applications that make use of the Lightning Direct Memory Mapped driver.</span></span>
