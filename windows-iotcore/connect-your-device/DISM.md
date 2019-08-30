---
title: DISM을 사용 하 여 Windows 10 IoT Core 플래시
author: bfjelds
ms.author: bfjelds
ms.date: 08/28/2017
ms.topic: article
description: DISM을 사용 하 여 Windows 10 IoT Core를 마이크로 SD 카드에 플래시 하는 방법에 대해 알아봅니다.
keywords: windows iot, DISM, 배포 이미지 서비스 관리, SD 카드, 플래시, OS
ms.openlocfilehash: 1fd075037b97399762aea1b0b844a477337cbc5d
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "60168943"
---
# <a name="use-dism-to-flash-windows-10-iot-core"></a><span data-ttu-id="cb877-104">DISM을 사용 하 여 Windows 10 IoT Core 플래시</span><span class="sxs-lookup"><span data-stu-id="cb877-104">Use DISM to flash Windows 10 IoT Core</span></span>

> [!NOTE]
> <span data-ttu-id="cb877-105">DISM 오프 라인 서비스는 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cb877-105">DISM offline servicing isn't supported.</span></span> <span data-ttu-id="cb877-106">IoT Core 용 FFU를 탑재 하려고 하면 아래 오류가 표시 됩니다. 요청이 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cb877-106">You will receive the error below if you try to mount an FFU for IoT Core: The request is not supported.</span></span>
> <span data-ttu-id="cb877-107">이미지에는 이름이 없고 현재 지원 되지 않는 Mobile/Onecore FFU가 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb877-107">The image doesn't have a name and it's likely to be a Mobile/Onecore FFU, which is currently not supported.</span></span>
> <span data-ttu-id="cb877-108">FfuMountImage # 160이 0 x 80070032로 실패 했습니다.</span><span class="sxs-lookup"><span data-stu-id="cb877-108">FfuMountImage#160 failed with 0x80070032.</span></span>

## <a name="an-alternative-method-to-iot-dashboard-for-flashing-a-ffu"></a><span data-ttu-id="cb877-109">IoT 대시보드가 깜박이는 다른 방법으로 FFU</span><span class="sxs-lookup"><span data-stu-id="cb877-109">An alternative method to IoT Dashboard for Flashing a FFU</span></span>

<span data-ttu-id="cb877-110">배포 이미지 서비스 및 관리 (Dism.exe)를 사용 하 여 SD 카드에서 Windows 10 IoT Core를 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb877-110">You can use Deployment Image Servicing and Management(Dism.exe) to flash Windows 10 IoT Core on your SD card.</span></span> <span data-ttu-id="cb877-111">장치 유형에 해당 하는 FFU 이미지 파일이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb877-111">You will need a FFU image file corresponding to your device type.</span></span> 

* <span data-ttu-id="cb877-112">관리자 명령 프롬프트를 열고 로컬 .ffu 파일이 포함 된 폴더로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb877-112">Open an administrator command prompt and navigate to the folder containing your local flash.ffu file.</span></span>

* <span data-ttu-id="cb877-113">SD 카드를 컴퓨터에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb877-113">Plug-in your SD card to your machine.</span></span> 

* <span data-ttu-id="cb877-114">SD 카드가 컴퓨터에 있는 디스크 번호를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb877-114">Find the disk number that your SD card is on your computer.</span></span>  <span data-ttu-id="cb877-115">이는 다음 단계에서 이미지가 적용 될 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb877-115">This will be used when the image is applied in the next step.</span></span>  <span data-ttu-id="cb877-116">이를 위해 diskpart 유틸리티를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb877-116">To do this, you can use the diskpart utility.</span></span>  <span data-ttu-id="cb877-117">다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb877-117">Run the following commands:</span></span>

        c:\FFUFolder>diskpart

        DISKPART>list disk

    <span data-ttu-id="cb877-118">컴퓨터에 연결 된 모든 저장 장치를 나열 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb877-118">It should list all the storage devices attached to the computer.</span></span> 

    ![DISM 목록 디스크](../media/Dism/DiskpartListDisk.png)

    <span data-ttu-id="cb877-120">디스크 번호를 확인 하 고 exit를 입력 하 여 diskpart를 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb877-120">Note the disk number and type exit to exit diskpart.</span></span> 

        DISKPART>exit

* <span data-ttu-id="cb877-121">관리자 명령 프롬프트를 사용 하 여 다음 명령을 실행 하 여 SD 카드에 이미지를 적용 합니다. 예를 들어, 다음 명령을 실행 하 여 실제 기반을 이전 단계에서 찾은 값으로 바꾸어야 합니다. 예를 들어 SD 카드는 디스크 번호 4 이므로 사용 `/ApplyDrive:\\.\PhysicalDrive4` 합니다. 표에서</span><span class="sxs-lookup"><span data-stu-id="cb877-121">Using the administrator command prompt, apply the image to your SD card by running the following command (be sure to replace PhysicalDriveN with the value you found in the previous step, for example, in this case SD card is disk number 4, so we will use  `/ApplyDrive:\\.\PhysicalDrive4` below)</span></span>

        dism.exe /Apply-Image /ImageFile:"[FULLPATH]\flash.ffu" /ApplyDrive:\\.\PhysicalDriveN /SkipPlatformCheck

* <span data-ttu-id="cb877-122">작업 트레이에서 "하드웨어 안전 제거" 아이콘을 클릭 하 고 USB SD 카드 판독기를 선택 하 여 시스템에서 안전 하 게 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb877-122">Click on the "Safely Remove Hardware" icon in your task tray and select your USB SD card reader to safely remove it from the system.</span></span>  <span data-ttu-id="cb877-123">이 작업을 수행 하지 못하면 이미지를 손상 시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb877-123">Failing to do this can cause corruption of the image.</span></span>
