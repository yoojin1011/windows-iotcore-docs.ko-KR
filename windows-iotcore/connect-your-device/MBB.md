---
title: 모바일 광대역 연결
author: saraclay
ms.author: saclayt
ms.date: 06/12/18
ms.topic: article
description: 모바일 광대역 연결에 대 한 Windows 10 IoT Core 사용 하는 방법에 알아봅니다.
keywords: windows iot, MBB, 모바일 광대역 연결
ms.openlocfilehash: 3afa48e049e38f7e26308434ba6f7349ac0be050
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513574"
---
## <a name="mobile-broadband-connection"></a><span data-ttu-id="b08a4-104">모바일 광대역 연결</span><span class="sxs-lookup"><span data-stu-id="b08a4-104">Mobile Broadband Connection</span></span>

<span data-ttu-id="b08a4-105">모바일 광대역 연결에서 지원 됩니다 [Windows 10 IoT Core](http://windowsondevices.com)합니다.</span><span class="sxs-lookup"><span data-stu-id="b08a4-105">Mobile Broadband Connection is supported on [Windows 10 IoT Core](http://windowsondevices.com).</span></span> <span data-ttu-id="b08a4-106">IoT 게이트웨이 모바일 광대역 모뎀 모듈을 지 원하는 경우 사용할 수는 `MBBConnect` IoT Core의 모바일 광대역 연결에 대 한 설정 구성을 데 유용한 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="b08a4-106">If your IoT gateway supports the mobile broadband modem module, you can use the `MBBConnect` tool to help setup configurations for mobile broadband connection in IoT Core.</span></span>

`MBBConnect` <span data-ttu-id="b08a4-107">구독자 ID, SIM ICC ID, 인터페이스 이름 및 홈 공급자 이름 등의 연결에 대 한 관련 정보를 검색합니다. 그런 다음 연결 프로필을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b08a4-107">retrieves the relevant information for connect, such as subscriber ID, SIM ICC ID, interface name, and home provider name, etc. Then, it creates the connection profile.</span></span> <span data-ttu-id="b08a4-108">수행 해야 하는 작업만 APN을 제공 하기 이며 자동으로 연결을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b08a4-108">The only thing you’ll need to do is to provide APN, and it’ll setup connection automatically.</span></span>

`MBBConnect` <span data-ttu-id="b08a4-109">개발 되 고 사용 하 여 테스트 MinnowBoard 최대 기반 IoT Core를 실행 16299 버전과 모바일 광대역 모뎀 모듈 SIM 카드를 사용 하 여 대만에서 주요 telecom 공급자에서 IoT 게이트웨이.</span><span class="sxs-lookup"><span data-stu-id="b08a4-109">is developed and tested with MinnowBoard Max based IoT gateway running IoT Core version 16299 and the mobile broadband modem module with the SIM card from major telecom provider in Taiwan.</span></span>

### <a name="usage"></a><span data-ttu-id="b08a4-110">사용법</span><span class="sxs-lookup"><span data-stu-id="b08a4-110">Usage</span></span>

1. <span data-ttu-id="b08a4-111">복사 `MBBConnect.exe` IoT 게이트웨이에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b08a4-111">Copy `MBBConnect.exe` to IoT gateway.</span></span>

   * [<span data-ttu-id="b08a4-112">FTP</span><span class="sxs-lookup"><span data-stu-id="b08a4-112">FTP</span></span>](https://docs.microsoft.com/windows/iot-core/connect-your-device/ftp)

2. <span data-ttu-id="b08a4-113">Powershell 또는 SSH에서 게이트웨이 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="b08a4-113">Connect gateway by Powershell or SSH.</span></span>

   * [<span data-ttu-id="b08a4-114">PowerShell</span><span class="sxs-lookup"><span data-stu-id="b08a4-114">PowerShell</span></span>](https://docs.microsoft.com/windows/iot-core/connect-your-device/powershell)

   * [<span data-ttu-id="b08a4-115">SSH</span><span class="sxs-lookup"><span data-stu-id="b08a4-115">SSH</span></span>](https://docs.microsoft.com/windows/iot-core/connect-your-device/SSH)

3. <span data-ttu-id="b08a4-116">폴더로 전환 하 고 있는 `MBBConnect.exe` 위치한 합니다.</span><span class="sxs-lookup"><span data-stu-id="b08a4-116">Switch to the folder where `MBBConnect.exe` is located.</span></span> 
   ```
   Command: MBBConnect.exe <APN name>
   <APN name>: It depends on your SIM card’s provider. 
   ```

### <a name="example"></a><span data-ttu-id="b08a4-117">예제</span><span class="sxs-lookup"><span data-stu-id="b08a4-117">Example</span></span>
<span data-ttu-id="b08a4-118">아래 예제에서는 PowerShell에서 MBBConnect.exe를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b08a4-118">The example below uses MBBConnect.exe in PowerShell.</span></span> <span data-ttu-id="b08a4-119">SIM 카드의 APN "Internet" 인 경우 사용 하는 예를 들어 `MBBConnect.exe Internet` 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="b08a4-119">For example, if the APN of the SIM card is “Internet”, use `MBBConnect.exe Internet` to connect.</span></span>
 
<span data-ttu-id="b08a4-120">출력 메시지 흐름에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b08a4-120">The output message will show the flow:</span></span>

* <span data-ttu-id="b08a4-121">상태는 연결 되지 않은에서 연결 됨으로 변경 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b08a4-121">The state is changed from Not Connected to Connected.</span></span> 

* <span data-ttu-id="b08a4-122">WWAN 네트워크가 성공적으로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b08a4-122">WWAN network is configured successfully.</span></span>

<span data-ttu-id="b08a4-123">모바일 광대역 연결에 대 한 샘플 시도 [여기](https://github.com/ms-iot/iot-utilities/tree/master/MBBConnect)합니다.</span><span class="sxs-lookup"><span data-stu-id="b08a4-123">Try the sample for Mobile Broadband Connection [here](https://github.com/ms-iot/iot-utilities/tree/master/MBBConnect).</span></span>
