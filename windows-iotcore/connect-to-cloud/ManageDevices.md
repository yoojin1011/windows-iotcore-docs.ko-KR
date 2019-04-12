---
title: Azure IoT Hub를 사용 하 여 Windows 장치를 관리 합니다.
author: saraclay
ms.author: saclayt
ms.date: 01/08/2018
ms.topic: article
description: Azure IoT Hub를 사용 하 여 Windows 장치를 관리 하는 방법에 알아봅니다.
keywords: windows iot, Azure, DM, 장치 관리, Azure IoT Hub, IoT Hub에 장치 상태
ms.openlocfilehash: f3018007c262112374fd39439bf2306675fddafe
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513157"
---
# <a name="manage-your-windows-devices-with-the-azure-iot-hub"></a><span data-ttu-id="56d29-104">Azure IoT Hub를 사용 하 여 Windows 장치를 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="56d29-104">Manage your Windows devices with the Azure IoT Hub</span></span>

## <a name="overview"></a><span data-ttu-id="56d29-105">개요</span><span class="sxs-lookup"><span data-stu-id="56d29-105">Overview</span></span>
<span data-ttu-id="56d29-106">장치 관리 (DM) 연산자를 원격으로 구성 하 고 동시에 매우 많은 양의 IoT 장치를 모니터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56d29-106">Device Management (DM) allows operators to remotely configure and monitor very high volumes of IoT devices simultaneously.</span></span>

<span data-ttu-id="56d29-107">대상 장치는 온라인 또는 오프 라인 여부를 장치에 대 한 구성은 장치에 푸시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56d29-107">Configuration for the devices can be pushed to devices, whether the target devices are online or offline.</span></span> <span data-ttu-id="56d29-108">장치가 오프 라인인 경우 다시 연결 될 때 새 구성이 선택 됩니다.</span><span class="sxs-lookup"><span data-stu-id="56d29-108">If the device is offline it will pick up the new configuration when it reconnects.</span></span> <span data-ttu-id="56d29-109">장치 연산자는 각 장치에 장치 구성 업데이트를 성공적으로 적용 여부 여부 등의 상태를 검색할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56d29-109">Device operators can also retrieve the status of each device, including whether device configuration updates have been successfully applied or not.</span></span>

<span data-ttu-id="56d29-110">IoT 장치에 대 한 이러한 기능을 사용 하도록 설정 하면 중앙, 강력한 및 신뢰할 수 있는 메커니즘을 저장 하 고 대상 장치 및 장치 상태 모니터링-대규모로 구성 데이터를 배포 하려면 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="56d29-110">Enabling these features for IoT devices requires a central, robust, and reliable mechanism to store and to deploy the configuration data to the target devices, and monitor device status - at scale.</span></span>

<span data-ttu-id="56d29-111">완벽 한 솔루션에는 다음이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="56d29-111">A complete solution requires the following:</span></span>

* <span data-ttu-id="56d29-112">다양 한 장치의 desired 및 reported 상태를 저장 하는 강력한/확장 가능 클라우드 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="56d29-112">A Robust/Scalable Cloud Service to store the desired and reported states of the various devices.</span></span>
  * <span data-ttu-id="56d29-113">Azure 장치 관리 및 azure IoT Hub는 수백만 개의 장치를 관리 하기 위한 고도로 확장 가능 하며 효율적인 클라우드 서비스를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="56d29-113">Azure IoT Hub and Azure Device Management offer a highly scalable and efficient cloud service for managing millions of devices.</span></span>

* <span data-ttu-id="56d29-114">클라이언트 장치에서 실행 및 원하는 구성을 적용 하는 장치의 상태를 보고입니다.</span><span class="sxs-lookup"><span data-stu-id="56d29-114">A Client that runs on the device and can apply the desired configuration and report the state of the device.</span></span>
  * <span data-ttu-id="56d29-115">Windows IoT Azure DM 클라이언트 (오픈 소스 SDK + 런타임), Azure IoT Hub와 함께에서 적용 하는 다양 한 일반적인 경우에 따라 중요 한 Windows 구성을 보고 합니다.</span><span class="sxs-lookup"><span data-stu-id="56d29-115">The Windows IoT Azure DM Client (an open source SDK + runtime), in conjunction with Azure IoT Hub, can apply and report on a large set of common, sometimes critical, Windows configurations.</span></span>

* <span data-ttu-id="56d29-116">포털 또는 응용 프로그램을 구성 하 고 장치를 원격으로 쿼리 연산자에서 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="56d29-116">A Portal or an Application that will be used by the operator to configure and query the devices remotely.</span></span>
  * <span data-ttu-id="56d29-117">이 장치 OEM 또는 연산자에서 장치에 대 한 사용자 지정 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="56d29-117">This must be customized for devices by the device OEM or operator.</span></span> <span data-ttu-id="56d29-118">이 솔루션의 일부로 오픈 소스 데이터 모델을 제공 하 고 IoT Hub 저장소와 Windows IoT 클라이언트와 쉽게 상호 작용에 대 한 구현 샘플입니다.</span><span class="sxs-lookup"><span data-stu-id="56d29-118">As part of this solution, we also provide an open source data model and sample implementation for easier interaction with the IoT Hub storage and the Windows IoT client.</span></span>

<span data-ttu-id="56d29-119">Windows 장치에 대 한 장치 관리에 대 한 자세한 내용은 방문 [장치 관리 클라이언트 리포지토리](https://github.com/ms-iot/iot-core-azure-dm-client/tree/master)합니다.</span><span class="sxs-lookup"><span data-stu-id="56d29-119">To learn more about device management for Windows devices, visit the main [Device Management Client repo](https://github.com/ms-iot/iot-core-azure-dm-client/tree/master).</span></span>
