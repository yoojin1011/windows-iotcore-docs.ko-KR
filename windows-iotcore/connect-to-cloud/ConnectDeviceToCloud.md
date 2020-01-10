---
title: 장치를 클라우드에 연결
ms.date: 08/28/2017
ms.topic: article
description: 장치를 클라우드에 연결 하는 방법에 대해 알아봅니다.
keywords: windows iot, Azure, 보안, 신뢰할 수 있는 플랫폼 모듈, SoC
ms.openlocfilehash: 62120695d2209227f938ebd5635380f226dddfc1
ms.sourcegitcommit: ea060254f9c4c25afcd0245c897b9e1425321859
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75721508"
---
# <a name="connect-your-device-to-the-cloud"></a><span data-ttu-id="c37fa-104">장치를 클라우드에 연결</span><span class="sxs-lookup"><span data-stu-id="c37fa-104">Connect your device to the cloud</span></span>

<span data-ttu-id="c37fa-105">암호 또는 인증서와 같은 보안 정보를 장치에 저장 하면 장치가 노출에 취약 해질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c37fa-105">Storing secure information such as a password or a certificate on a device could make a device vulnerable to exposure.</span></span> <span data-ttu-id="c37fa-106">누출 된 암호는 장치 또는 전체 시스템의 보안을 손상 시킬 수 있는 surefire 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="c37fa-106">A leaked password is a surefire way to compromise the security of a device or an entire system.</span></span> <span data-ttu-id="c37fa-107">Windows 제품군에서 OS의 보안을 지 원하는 기술은 신뢰할 수 있는 플랫폼 모듈입니다.</span><span class="sxs-lookup"><span data-stu-id="c37fa-107">In the Windows family, the technology that supports the security of the OS is the Trusted Platform Module.</span></span>

<span data-ttu-id="c37fa-108">TPM ( [신뢰할 수 있는 플랫폼 모듈](https://en.wikipedia.org/wiki/Trusted_Platform_Module) ) 장치는 데이터를 저장 하 고 계산을 수행할 수 있는 마이크로 컨트롤러입니다.</span><span class="sxs-lookup"><span data-stu-id="c37fa-108">A [Trusted Platform Module](https://en.wikipedia.org/wiki/Trusted_Platform_Module) (TPM) device is a microcontroller that can store data and perform computations.</span></span> <span data-ttu-id="c37fa-109">제조업체에서 컴퓨터의 마더보드 또는 칩 (SoC)의 시스템에 통합 된 모듈 중 하나를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c37fa-109">It can be either a discrete chip soldered to a computer's motherboard or a module integrated into the system on a chip (SoC) by the manufacturer.</span></span> 

## <a name="inside-the-tpm"></a><span data-ttu-id="c37fa-110">TPM 내부</span><span class="sxs-lookup"><span data-stu-id="c37fa-110">Inside the TPM</span></span> 

<span data-ttu-id="c37fa-111">TPM의 주요 기능은 쓰기 전용 메모리입니다.</span><span class="sxs-lookup"><span data-stu-id="c37fa-111">A key capability of the TPM is its write-only memory.</span></span> <span data-ttu-id="c37fa-112">TPM은 데이터를 기반으로 해당 데이터를 기반으로 [HMAC](https://en.wikipedia.org/wiki/Hash-based_message_authentication_code)와 같은 암호화 해시를 계산할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c37fa-112">Based on the data in it, TPM can also compute a cryptographic hash (such as the [HMAC](https://en.wikipedia.org/wiki/Hash-based_message_authentication_code)), based on that data.</span></span>
<span data-ttu-id="c37fa-113">해시에 지정 된 암호를 확인 하는 것은 불가능 하지만 비밀이 통신의 양쪽 당사자에 게 알려진 경우 다른 당사자 로부터 받은 해시가 해당 암호에서 생성 되었는지 여부를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c37fa-113">It’s impossible to uncover the secret given the hash, but if the secret is known to both parties of communication, it is possible to determine whether the hash received from another party was produced from that secret.</span></span>

<span data-ttu-id="c37fa-114">암호화 키 사용의 기본 개념은 장치 프로 비전 프로세스 중에 IoT 장치와 클라우드 간에 비밀 (공유 액세스 키 라고도 함)을 설정 하 고 공유 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="c37fa-114">The basic idea behind using cryptographic keys: the secret (also called the shared access key) is established and shared between the IoT device and the cloud during the device provisioning process.</span></span> <span data-ttu-id="c37fa-115">이 시점부터 비밀에서 파생 된 HMAC가 IoT 장치를 인증 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c37fa-115">From that point on, an HMAC derived from the secret will be used to authenticate the IoT device.</span></span>

## <a name="device-provisioning"></a><span data-ttu-id="c37fa-116">디바이스 프로비전</span><span class="sxs-lookup"><span data-stu-id="c37fa-116">Device Provisioning</span></span> 

<span data-ttu-id="c37fa-117">Windows 10 IoT Core 장치를 프로 비전 하는 도구를 IoT Core 대시보드 라고 하며 [다운로드 페이지](https://go.microsoft.com/fwlink/?LinkID=708576)에서 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c37fa-117">The tool that provisions Windows 10 IoT Core devices is called the IoT Core Dashboard and can be downloaded from [the downloads page](https://go.microsoft.com/fwlink/?LinkID=708576).</span></span>

<span data-ttu-id="c37fa-118">대시보드는 OS 이미지를 생성 하 고 장치를 Azure에 안전 하 게 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="c37fa-118">The dashboard produces an image of the OS and securely connects your device to Azure.</span></span> <span data-ttu-id="c37fa-119">이 작업은 물리적 장치를 Azure IoT Hub의 장치 ID와 연결 하 고 장치 전용 공유 액세스 키를 장치의 TPM으로 인쇄 하 여 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="c37fa-119">This is done by associating the physical device with the device ID in the Azure IoT Hub and imprinting the device-specific shared access key to the device's TPM.</span></span> 

<span data-ttu-id="c37fa-120">TPM 칩이 없는 장치의 경우이 도구는 소프트웨어 에뮬레이트된 TPM을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c37fa-120">For devices that don’t have a TPM chip, the tool can install a software-emulated TPM.</span></span> <span data-ttu-id="c37fa-121">이는 보안을 제공 하는 것이 아니라 작성자 장치 (예: Raspberry Pi 2 또는 3)를 사용 하 여 앱을 개발 하 고, 앱을 변경 하지 않고도 하드웨어 TPM을 사용 하 여 장치에 보안 "강화"를 제공 하는 것을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c37fa-121">This does not provide security but allows you to develop your app using a maker device (such as Raspberry Pi 2 or 3) and have security "light up" on a device with the hardware TPM without having to change the app.</span></span> 

<span data-ttu-id="c37fa-122">장치를 Azure에 연결 하려면 "Azure에 연결" 탭을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c37fa-122">To connect your device to Azure, click on the "Connect to Azure" tab:</span></span>

![Azure에 연결 탭 열기](../media/ConnectDeviceToCloud/Building_Secure_Apps_for_IoT_Core_Screen01.png)

<span data-ttu-id="c37fa-124">Azure 계정에 로그인 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c37fa-124">You will be asked to log in to your Azure account.</span></span> <span data-ttu-id="c37fa-125">원하는 Azure IoT Hub 인스턴스를 선택 하 고 실제 장치를 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="c37fa-125">Pick the desired instance of Azure IoT Hub and associate your physical device with it.</span></span> <span data-ttu-id="c37fa-126">Azure 구독에 IoT Hub 인스턴스가 없는 경우이 도구를 사용 하 여 무료 인스턴스를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c37fa-126">If you don’t have any IoT Hub instances in your Azure subscription, the tool will let you create a free instance.</span></span> 

<span data-ttu-id="c37fa-127">장치를 연결 하기 위해 IoT Hub 및 장치 ID를 선택 하면 TPM에서 해당 장치의 공유 액세스 키를 임 프린트가 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c37fa-127">Once you have selected the IoT Hub and the device ID to associate your device with, you can imprint the shared access key of that device on your TPM:</span></span>

![장치 프로 비전](../media/ConnectDeviceToCloud/Building_Secure_Apps_for_IoT_Core_Screen02.png)

<span data-ttu-id="c37fa-129">이제 장치를 안전한 방식으로 Azure에 연결할 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c37fa-129">Your device is now ready to connect to Azure in a secure way.</span></span> 

<span data-ttu-id="c37fa-130">Windows 장치 포털을 사용 하 여 프로 비전 된 후 인터넷에 처음 연결할 때 IoT Hub 연결 문자열을 동적으로 가져올 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c37fa-130">You can also use the Windows Device Portal to dynamically acquire an IoT Hub connection string when it first connects to the internet after being provisioned.</span></span> <span data-ttu-id="c37fa-131">장치 포털의 "Azure 클라이언트" 탭에서이 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c37fa-131">This can be done from the "Azure Clients" tab in the Device Portal.</span></span>

![Azure 클라이언트 탭](../media/ConnectDeviceToCloud/azure-clients.png)

## <a name="helpful-resources"></a><span data-ttu-id="c37fa-133">유용한 리소스:</span><span class="sxs-lookup"><span data-stu-id="c37fa-133">Helpful resources:</span></span>
* [<span data-ttu-id="c37fa-134">Azure에 앱 연결</span><span class="sxs-lookup"><span data-stu-id="c37fa-134">Connecting your app to Azure</span></span>](../connect-to-cloud/ConnectAppToCloud.md)
* [<span data-ttu-id="c37fa-135">IoT Core 용 보안 앱 빌드</span><span class="sxs-lookup"><span data-stu-id="c37fa-135">Building secure apps for IoT Core</span></span>](https://blogs.windows.com/buildingapps/2016/07/20/building-secure-apps-for-windows-iot-core/#oqFLXiWIL1iCF8j9.97)
