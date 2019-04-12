---
title: 클라우드에서 IoT 개요
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 메시징, 보안 및 장치 관리에 대 한 Azure IoT를 사용 하 여 클라우드와 알아봅니다.
keywords: windows iot, 클라우드, Azure, Azure IoT Hub, 메시징, UWP, 유니버설 Windows 플랫폼
ms.openlocfilehash: 4f38a45836e7c474655819988e447137249c2a7f
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513565"
---
# <a name="overview-of-iot-on-the-cloud"></a><span data-ttu-id="9377b-104">클라우드에서 IoT 개요</span><span class="sxs-lookup"><span data-stu-id="9377b-104">Overview of IoT on the Cloud</span></span>

<span data-ttu-id="9377b-105">사물 인터넷은 클라우드 기반 컴퓨팅입니다.</span><span class="sxs-lookup"><span data-stu-id="9377b-105">The Internet of Things is built on cloud computing.</span></span> <span data-ttu-id="9377b-106">클라우드와 통신 하 여 데이터에서 통찰력을 파생 기능은 IoT 프로젝트의 필수적인 부분입니다.</span><span class="sxs-lookup"><span data-stu-id="9377b-106">The ability to communicate with the cloud and derive insight from the data is an essential part of any IoT project.</span></span>

## <a name="messaging"></a><span data-ttu-id="9377b-107">Messaging(메시징)</span><span class="sxs-lookup"><span data-stu-id="9377b-107">Messaging</span></span>

<span data-ttu-id="9377b-108">일반적으로 IoT 장치에서 메시지를 보내고 클라우드 또는 서로 통신 합니다.</span><span class="sxs-lookup"><span data-stu-id="9377b-108">Usually, IoT devices communicate with the cloud or each other by sending and receiving messages.</span></span> <span data-ttu-id="9377b-109">장치에서 클라우드로 보낸 메시지의 페이로드 값 센서에서 비디오 파일을 최대한으로 작게 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9377b-109">The payload of a message sent from the device to cloud can be as small as a value from a sensor and as big as a video file.</span></span> <span data-ttu-id="9377b-110">클라우드 장치 메시지를 일반적으로 작업을 수행 하는 장치를 지시 명령을입니다.</span><span class="sxs-lookup"><span data-stu-id="9377b-110">A cloud to device message is typically a command instructing the device to perform an action.</span></span>


<span data-ttu-id="9377b-111">메시지 전달 통신 패턴에서 요청-응답과 같은 더 복잡 한 프로토콜 또는 2 단계 커밋 같은 트랜잭션 프로토콜 간단한 단방향 메시징 이르기까지 복잡성은 다양 합니다.</span><span class="sxs-lookup"><span data-stu-id="9377b-111">Message-passing communication patterns vary in complexity ranging from simple one-way messaging to more complex protocols such as request-response or transactional protocols such as the two-phase commit.</span></span>

## <a name="security"></a><span data-ttu-id="9377b-112">보안</span><span class="sxs-lookup"><span data-stu-id="9377b-112">Security</span></span>

<span data-ttu-id="9377b-113">보안은 IoT의 필수적인 부분입니다.</span><span class="sxs-lookup"><span data-stu-id="9377b-113">Security is an essential part of IoT.</span></span> <span data-ttu-id="9377b-114">제공 되었음을 확인 해야 합니다 각 메시지에 대 한 (또는 수신한) 신뢰할 수 있는 장치를 변조 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9377b-114">For each message, we must ensure that it comes from (or is received by) a trusted device and is not tampered with.</span></span> <span data-ttu-id="9377b-115">데이터를 암호화 해야 하는 정보를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9377b-115">The data can contain information that must be encrypted.</span></span>

## <a name="azure-iot-hub"></a><span data-ttu-id="9377b-116">Azure IoT Hub</span><span class="sxs-lookup"><span data-stu-id="9377b-116">Azure IoT Hub</span></span>

<span data-ttu-id="9377b-117">[Azure IoT Hub](https://azure.microsoft.com/services/iot-hub/) 해당 제품 안정적이 고 안전한 장치-클라우드 및 클라우드-장치 메시징에 수백만 개의 장치로 확장 하는 Azure 클라우드 서비스 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9377b-117">[Azure IoT Hub](https://azure.microsoft.com/services/iot-hub/) is an Azure cloud service that offers reliable and secure device-to-cloud and cloud-to-device messaging that scales to millions of devices.</span></span> <span data-ttu-id="9377b-118">최소한의 노력으로 시작 하 고 필요에 맞게 증가 함에 따라 솔루션을 확장할 수 있는 간소화 된 프로그래밍 모델을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="9377b-118">It offers a streamlined programming model that lets you get started with minimum effort and scale up your solution as its needs grow.</span></span>
