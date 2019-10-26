---
title: Azure IoT Hub를 사용 하 여 Windows 장치 관리
ms.date: 01/08/2018
ms.topic: article
description: Azure IoT Hub를 사용 하 여 Windows 장치를 관리 하는 방법을 알아봅니다.
keywords: windows iot, Azure, DM, 장치 관리, Azure IoT Hub, IoT Hub, 장치 상태
ms.openlocfilehash: 7eea1a8d3ccfd35bcdb7ebae44803135db05f824
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918384"
---
# <a name="manage-your-windows-devices-with-the-azure-iot-hub"></a><span data-ttu-id="274dd-104">Azure IoT Hub를 사용 하 여 Windows 장치 관리</span><span class="sxs-lookup"><span data-stu-id="274dd-104">Manage your Windows devices with the Azure IoT Hub</span></span>

## <a name="overview"></a><span data-ttu-id="274dd-105">개요</span><span class="sxs-lookup"><span data-stu-id="274dd-105">Overview</span></span>
<span data-ttu-id="274dd-106">DM (장치 관리)을 사용 하면 운영자가 매우 많은 IoT 장치를 원격으로 구성 하 고 모니터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="274dd-106">Device Management (DM) allows operators to remotely configure and monitor very high volumes of IoT devices simultaneously.</span></span>

<span data-ttu-id="274dd-107">대상 장치가 온라인 또는 오프 라인 상태 인지 여부에 관계 없이 장치에 대 한 구성을 장치에 푸시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="274dd-107">Configuration for the devices can be pushed to devices, whether the target devices are online or offline.</span></span> <span data-ttu-id="274dd-108">장치가 오프 라인 상태인 경우 다시 연결할 때 새 구성을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="274dd-108">If the device is offline it will pick up the new configuration when it reconnects.</span></span> <span data-ttu-id="274dd-109">장치 운영자는 장치 구성 업데이트가 성공적으로 적용 되었는지 여부를 포함 하 여 각 장치의 상태를 검색할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="274dd-109">Device operators can also retrieve the status of each device, including whether device configuration updates have been successfully applied or not.</span></span>

<span data-ttu-id="274dd-110">IoT 장치에 이러한 기능을 사용 하도록 설정 하려면 구성 데이터를 저장 하 고 대상 장치에 배포 하 고 장치 상태를 모니터링 하는 중앙의 강력 하 고 신뢰할 수 있는 메커니즘이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="274dd-110">Enabling these features for IoT devices requires a central, robust, and reliable mechanism to store and to deploy the configuration data to the target devices, and monitor device status - at scale.</span></span>

<span data-ttu-id="274dd-111">전체 솔루션에는 다음이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="274dd-111">A complete solution requires the following:</span></span>

* <span data-ttu-id="274dd-112">다양 한 장치의 원하는 상태 및 보고 된 상태를 저장 하는 강력 하 고 확장 가능한 클라우드 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="274dd-112">A Robust/Scalable Cloud Service to store the desired and reported states of the various devices.</span></span>
  * <span data-ttu-id="274dd-113">Azure IoT Hub 및 Azure 장치 관리는 수백만 개의 장치를 관리 하기 위한 확장성과 효율성이 뛰어난 클라우드 서비스를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="274dd-113">Azure IoT Hub and Azure Device Management offer a highly scalable and efficient cloud service for managing millions of devices.</span></span>

* <span data-ttu-id="274dd-114">장치에서 실행 되 고 원하는 구성을 적용 하 고 장치의 상태를 보고할 수 있는 클라이언트입니다.</span><span class="sxs-lookup"><span data-stu-id="274dd-114">A Client that runs on the device and can apply the desired configuration and report the state of the device.</span></span>
  * <span data-ttu-id="274dd-115">Azure IoT Hub와 함께 Windows IoT Azure DM 클라이언트 (오픈 소스 SDK + 런타임)는 광범위 한 공통, 때로는 중요 한 Windows 구성에 적용 하 고 보고할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="274dd-115">The Windows IoT Azure DM Client (an open source SDK + runtime), in conjunction with Azure IoT Hub, can apply and report on a large set of common, sometimes critical, Windows configurations.</span></span>

* <span data-ttu-id="274dd-116">운영자가 원격으로 장치를 구성 하 고 쿼리 하는 데 사용 하는 포털 또는 응용 프로그램입니다.</span><span class="sxs-lookup"><span data-stu-id="274dd-116">A Portal or an Application that will be used by the operator to configure and query the devices remotely.</span></span>
  * <span data-ttu-id="274dd-117">장치 OEM 또는 운영자가 장치에 대해 사용자 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="274dd-117">This must be customized for devices by the device OEM or operator.</span></span> <span data-ttu-id="274dd-118">이 솔루션의 일부로, IoT Hub 저장소 및 Windows IoT 클라이언트와의 상호 작용을 위한 오픈 소스 데이터 모델 및 샘플 구현도 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="274dd-118">As part of this solution, we also provide an open source data model and sample implementation for easier interaction with the IoT Hub storage and the Windows IoT client.</span></span>

<span data-ttu-id="274dd-119">Windows 장치에 대 한 장치 관리에 대해 자세히 알아보려면 기본 [장치 관리 클라이언트 리포지토리](https://github.com/ms-iot/iot-core-azure-dm-client/tree/master)를 방문 하세요.</span><span class="sxs-lookup"><span data-stu-id="274dd-119">To learn more about device management for Windows devices, visit the main [Device Management Client repo](https://github.com/ms-iot/iot-core-azure-dm-client/tree/master).</span></span>
