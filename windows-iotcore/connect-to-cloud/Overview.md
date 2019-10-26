---
title: 클라우드의 IoT 개요
ms.date: 08/28/2017
ms.topic: article
description: Azure IoT를 사용 하 여 클라우드를 통한 메시징, 보안 및 장치 관리에 대해 알아봅니다.
keywords: windows iot, cloud, Azure, Azure IoT Hub, messaging, UWP, 유니버설 Windows 플랫폼
ms.openlocfilehash: 14a8804025cea507574efef6a0512827333faff5
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918380"
---
# <a name="overview-of-iot-on-the-cloud"></a><span data-ttu-id="4416e-104">클라우드의 IoT 개요</span><span class="sxs-lookup"><span data-stu-id="4416e-104">Overview of IoT on the Cloud</span></span>

<span data-ttu-id="4416e-105">사물 인터넷는 클라우드 컴퓨팅을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="4416e-105">The Internet of Things is built on cloud computing.</span></span> <span data-ttu-id="4416e-106">클라우드와 통신 하 고 데이터에서 통찰력을 얻을 수 있는 기능은 모든 IoT 프로젝트의 필수적인 부분입니다.</span><span class="sxs-lookup"><span data-stu-id="4416e-106">The ability to communicate with the cloud and derive insight from the data is an essential part of any IoT project.</span></span>

## <a name="messaging"></a><span data-ttu-id="4416e-107">Messaging</span><span class="sxs-lookup"><span data-stu-id="4416e-107">Messaging</span></span>

<span data-ttu-id="4416e-108">일반적으로 IoT 장치는 메시지를 송수신 하 여 클라우드와 통신 합니다.</span><span class="sxs-lookup"><span data-stu-id="4416e-108">Usually, IoT devices communicate with the cloud or each other by sending and receiving messages.</span></span> <span data-ttu-id="4416e-109">장치에서 클라우드로 전송 되는 메시지의 페이로드는 센서 값 만큼 작고 비디오 파일 만큼 클 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4416e-109">The payload of a message sent from the device to cloud can be as small as a value from a sensor and as big as a video file.</span></span> <span data-ttu-id="4416e-110">클라우드-장치 메시지는 일반적으로 장치에서 작업을 수행 하도록 지시 하는 명령입니다.</span><span class="sxs-lookup"><span data-stu-id="4416e-110">A cloud to device message is typically a command instructing the device to perform an action.</span></span>


<span data-ttu-id="4416e-111">메시지 전달 통신 패턴은 간단한 단방향 메시징에서 요청-응답 또는 2 단계 커밋과 같은 트랜잭션 프로토콜 등의 보다 복잡 한 프로토콜에 이르기까지 복잡성이 다양 합니다.</span><span class="sxs-lookup"><span data-stu-id="4416e-111">Message-passing communication patterns vary in complexity ranging from simple one-way messaging to more complex protocols such as request-response or transactional protocols such as the two-phase commit.</span></span>

## <a name="security"></a><span data-ttu-id="4416e-112">보안</span><span class="sxs-lookup"><span data-stu-id="4416e-112">Security</span></span>

<span data-ttu-id="4416e-113">보안은 IoT의 필수적인 부분입니다.</span><span class="sxs-lookup"><span data-stu-id="4416e-113">Security is an essential part of IoT.</span></span> <span data-ttu-id="4416e-114">각 메시지에 대해 신뢰할 수 있는 장치에서 제공 되 고 변조 되지 않았는지 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4416e-114">For each message, we must ensure that it comes from (or is received by) a trusted device and is not tampered with.</span></span> <span data-ttu-id="4416e-115">데이터에는 암호화 해야 하는 정보가 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4416e-115">The data can contain information that must be encrypted.</span></span>

## <a name="azure-iot-hub"></a><span data-ttu-id="4416e-116">Azure IoT Hub</span><span class="sxs-lookup"><span data-stu-id="4416e-116">Azure IoT Hub</span></span>

<span data-ttu-id="4416e-117">[Azure IoT Hub](https://azure.microsoft.com/services/iot-hub/) 는 수백만 개의 장치로 확장 되는 안정적이 고 안전한 장치-클라우드 및 클라우드-장치 메시징을 제공 하는 Azure 클라우드 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="4416e-117">[Azure IoT Hub](https://azure.microsoft.com/services/iot-hub/) is an Azure cloud service that offers reliable and secure device-to-cloud and cloud-to-device messaging that scales to millions of devices.</span></span> <span data-ttu-id="4416e-118">최소한의 노력으로 시작 하 고 필요에 따라 솔루션을 확장할 수 있는 간소화 된 프로그래밍 모델을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="4416e-118">It offers a streamlined programming model that lets you get started with minimum effort and scale up your solution as its needs grow.</span></span>

