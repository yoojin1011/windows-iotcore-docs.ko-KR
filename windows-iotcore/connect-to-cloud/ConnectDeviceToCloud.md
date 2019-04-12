---
title: 장치를 클라우드에 연결
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 장치를 클라우드에 연결 하는 방법에 알아봅니다.
keywords: windows iot, Azure, 보안, 신뢰할 수 있는 플랫폼 모듈, SoC
ms.openlocfilehash: ff54bbfa1aaf30d08107fac72ba59ae5a04aa247
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513845"
---
# <a name="connect-your-device-to-the-cloud"></a><span data-ttu-id="01179-104">장치를 클라우드에 연결</span><span class="sxs-lookup"><span data-stu-id="01179-104">Connect your device to the cloud</span></span>

<span data-ttu-id="01179-105">장치에서 암호 또는 인증서와 같은 보안 정보를 저장 장치 노출에 취약 해질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01179-105">Storing secure information such as a password or a certificate on a device could make a device vulnerable to exposure.</span></span> <span data-ttu-id="01179-106">유출 된 암호는 장치 또는 전체 시스템의 보안을 손상 시킬 surefire 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="01179-106">A leaked password is a surefire way to compromise the security of a device or an entire system.</span></span> <span data-ttu-id="01179-107">Windows 제품군의 운영 체제의 보안을 지 원하는 기술은 신뢰할 수 있는 플랫폼 모듈입니다.</span><span class="sxs-lookup"><span data-stu-id="01179-107">In the Windows family, the technology that supports the security of the OS is the Trusted Platform Module.</span></span>

<span data-ttu-id="01179-108">A [Trusted Platform Module](https://en.wikipedia.org/wiki/Trusted_Platform_Module) (TPM) 장치 데이터를 저장 하 고 계산을 수행할 수 있는 마이크로컨트롤러 됩니다.</span><span class="sxs-lookup"><span data-stu-id="01179-108">A [Trusted Platform Module](https://en.wikipedia.org/wiki/Trusted_Platform_Module) (TPM) device is a microcontroller that can store data and perform computations.</span></span> <span data-ttu-id="01179-109">컴퓨터의 마더보드에 납땜 불연속 칩 또는 제조업체가 칩 (SoC)의 시스템에 통합 모듈을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01179-109">It can be either a discrete chip soldered to a computer's motherboard or a module integrated into the system on a chip (SoC) by the manufacturer.</span></span> 

## <a name="inside-the-tpm"></a><span data-ttu-id="01179-110">TPM 내부에</span><span class="sxs-lookup"><span data-stu-id="01179-110">Inside the TPM</span></span> 

<span data-ttu-id="01179-111">Tpm을 키 기능은 쓰기 전용 메모리 사용 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="01179-111">A key capability of the TPM is its write-only memory.</span></span> <span data-ttu-id="01179-112">데이터에 따라 TPM 수 또한 계산 암호화 해시 (같은 합니다 [HMAC](https://en.wikipedia.org/wiki/Hash-based_message_authentication_code)), 해당 데이터를 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="01179-112">Based on the data in it, TPM can also compute a cryptographic hash (such as the [HMAC](https://en.wikipedia.org/wiki/Hash-based_message_authentication_code)), based on that data.</span></span>
<span data-ttu-id="01179-113">해시를 지정 된 암호를 파악 하는 것이 불가능 이지만 암호 통신의 양쪽 모두에 알 수 있으면 다른 파티 로부터 받은 해시 된 암호에서 생성 된 여부를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01179-113">It’s impossible to uncover the secret given the hash, but if the secret is known to both parties of communication, it is possible to determine whether the hash received from another party was produced from that secret.</span></span>

<span data-ttu-id="01179-114">암호화 키를 사용 하 여에 대 한 기본 개념: (공유 액세스 키 라고도 함) 암호를 설정 하 고 장치 프로 비전 프로세스 중 IoT 장치와 클라우드 간에 공유 합니다.</span><span class="sxs-lookup"><span data-stu-id="01179-114">The basic idea behind using cryptographic keys: the secret (also called the shared access key) is established and shared between the IoT device and the cloud during the device provisioning process.</span></span> <span data-ttu-id="01179-115">해당 지점에서 암호에서 파생 된 HMAC IoT 장치 인증을 위해 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="01179-115">From that point on, an HMAC derived from the secret will be used to authenticate the IoT device.</span></span>

## <a name="device-provisioning"></a><span data-ttu-id="01179-116">장치 프로 비전</span><span class="sxs-lookup"><span data-stu-id="01179-116">Device Provisioning</span></span> 

<span data-ttu-id="01179-117">Windows 10 IoT Core 장치 프로 비전 하는 도구 IoT Core 대시보드 라고 하며에서 다운로드할 수 있습니다 [다운로드 페이지](http://go.microsoft.com/fwlink/?LinkID=708576)합니다.</span><span class="sxs-lookup"><span data-stu-id="01179-117">The tool that provisions Windows 10 IoT Core devices is called the IoT Core Dashboard and can be downloaded from [the downloads page](http://go.microsoft.com/fwlink/?LinkID=708576).</span></span>

<span data-ttu-id="01179-118">대시보드는 운영 체제의 이미지를 생성 및 안전 하 게 장치를 Azure에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="01179-118">The dashboard produces an image of the OS and securely connects your device to Azure.</span></span> <span data-ttu-id="01179-119">이 Azure IoT Hub에서 장치 ID를 사용 하 여 물리적 장치를 연결 하 고 장치별 공유 액세스 키를 장치의 TPM imprinting 이루어집니다.</span><span class="sxs-lookup"><span data-stu-id="01179-119">This is done by associating the physical device with the device ID in the Azure IoT Hub and imprinting the device-specific shared access key to the device's TPM.</span></span> 

<span data-ttu-id="01179-120">장치의 TPM 칩이 없는 경우 도구는 소프트웨어 에뮬레이트되지 TPM을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01179-120">For devices that don’t have a TPM chip, the tool can install a software-emulated TPM.</span></span> <span data-ttu-id="01179-121">이 보안을 제공 하지 않습니다 하지만 maker 장치 (예: Raspberry Pi 2 또는 3)를 사용 하 여 앱을 개발 하 고 앱을 변경 하지 않고도 "light" 보안 하드웨어 TPM 사용 하 여 장치에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01179-121">This does not provide security but allows you to develop your app using a maker device (such as Raspberry Pi 2 or 3) and have security "light up" on a device with the hardware TPM without having to change the app.</span></span> 

<span data-ttu-id="01179-122">장치를 Azure에 연결 하려면 "Azure에 연결" 탭을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="01179-122">To connect your device to Azure, click on the "Connect to Azure" tab:</span></span>

![오픈 Azure 탭에 연결](../media/ConnectDeviceToCloud/Building_Secure_Apps_for_IoT_Core_Screen01.png)

<span data-ttu-id="01179-124">Azure 계정에 로그인 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="01179-124">You will be asked to log in to your Azure account.</span></span> <span data-ttu-id="01179-125">Azure IoT Hub의 원하는 인스턴스를 선택 하 고 물리적 장치를 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="01179-125">Pick the desired instance of Azure IoT Hub and associate your physical device with it.</span></span> <span data-ttu-id="01179-126">Azure 구독에서 IoT Hub 인스턴스를 모두 없으면이 도구는 사용 가능한 인스턴스를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01179-126">If you don’t have any IoT Hub instances in your Azure subscription, the tool will let you create a free instance.</span></span> 

<span data-ttu-id="01179-127">사용 하 여 장치를 연결할 IoT Hub 및 장치 ID를 선택한 후 TPM에서 장치의 공유 액세스 키를 표시 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01179-127">Once you have selected the IoT Hub and the device ID to associate your device with, you can imprint the shared access key of that device on your TPM:</span></span>

![장치 프로 비전](../media/ConnectDeviceToCloud/Building_Secure_Apps_for_IoT_Core_Screen02.png)

<span data-ttu-id="01179-129">장치의 안전한 방식으로 Azure에 연결할 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="01179-129">Your device is now ready to connect to Azure in a secure way.</span></span> 

<span data-ttu-id="01179-130">또한 먼저 인터넷에 연결 된 프로 비전 후 IoT Hub 연결 문자열을 동적으로 획득 Windows Device Portal 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01179-130">You can also use the Windows Device Portal to dynamically acquire an IoT Hub connection string when it first connects to the internet after being provisioned.</span></span> <span data-ttu-id="01179-131">이 장치 포털에서 "Azure 클라이언트" 탭에서 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01179-131">This can be done from the "Azure Clients" tab in the Device Portal.</span></span>

![Azure 클라이언트 탭](../media/ConnectDeviceToCloud/azure-clients.png)

## <a name="helpful-resources"></a><span data-ttu-id="01179-133">유용한 리소스:</span><span class="sxs-lookup"><span data-stu-id="01179-133">Helpful resources:</span></span>
* [<span data-ttu-id="01179-134">Azure에 앱 연결</span><span class="sxs-lookup"><span data-stu-id="01179-134">Connecting your app to Azure</span></span>](../connect-to-cloud/ConnectAppToCloud.md)
* [<span data-ttu-id="01179-135">IoT Core에 대 한 보안 앱 빌드</span><span class="sxs-lookup"><span data-stu-id="01179-135">Building secure apps for IoT Core</span></span>](https://blogs.windows.com/buildingapps/2016/07/20/building-secure-apps-for-windows-iot-core/#oqFLXiWIL1iCF8j9.97)
