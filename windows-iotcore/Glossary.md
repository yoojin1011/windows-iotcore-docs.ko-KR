---
title: Windows IoT 용어집
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: 설명서를 통해 다양한 Windows IoT Core 관련 용어에 대해 알아봅니다.
keywords: windows iot, 용어집, 용어, 용어, 정의
ms.openlocfilehash: 155de380459cbb74642352ff2a2ff718ebfe1ed7
ms.sourcegitcommit: 9ec4716afde25fdc8b94f7c0794448501f451b55
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/17/2019
ms.locfileid: "60168911"
---
# <a name="glossary-for-windows-iot"></a><span data-ttu-id="8f212-104">Windows IoT 용어집</span><span class="sxs-lookup"><span data-stu-id="8f212-104">Glossary for Windows IoT</span></span>

<span data-ttu-id="8f212-105">**ACPI(고급 구성 및 전원 인터페이스)** ACPI(고급 구성 및 전원 인터페이스)는 Hewlett-Packard, Intel, Microsoft, Phoenix 및 Toshiba가 공동으로 개발한 공개 산업 규격입니다.</span><span class="sxs-lookup"><span data-stu-id="8f212-105">**Advanced Configuration & Power Interface (ACPI)** ACPI (Advanced Configuration and Power Interface) is an open industry specification co-developed by Hewlett-Packard, Intel, Microsoft, Phoenix, and Toshiba.</span></span>  <span data-ttu-id="8f212-106">ACPI는 모바일, 데스크톱 및 서버 플랫폼의 OS 지향 구성, 전원 관리 및 열 관리를 지원하는 업계 표준 인터페이스를 구축합니다.</span><span class="sxs-lookup"><span data-stu-id="8f212-106">ACPI establishes industry-standard interfaces enabling OS-directed configuration, power management, and thermal management of mobile, desktop, and server platforms.</span></span>

<span data-ttu-id="8f212-107">**BIOS(기본 입출력 시스템)** 시작할 때 하드웨어를 테스트하고, 운영 체제를 시작하고, 하드웨어 디바이스 간의 데이터 전송을 지원하는 필수 소프트웨어 루틴 세트입니다.</span><span class="sxs-lookup"><span data-stu-id="8f212-107">**Basic Input/Output System (BIOS)** The set of essential software routines that test hardware at startup, start the operating system, and support the transfer of data among hardware devices.</span></span>

<span data-ttu-id="8f212-108">**상용화** 디바이스를 상업적으로 일반에 배포할 목적으로 개발 및 제조하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="8f212-108">**Commercialize** Developing and manufacturing a device with the intention of putting it out to the public commercially.</span></span>

<span data-ttu-id="8f212-109">**GPIO(범용 입출력)** GPIO는 입력 핀으로 동작하는 경우와 출력 핀으로 동작하는 경우를 포함하여 런타임 시 사용자가 제어할 수 있는 집적 회로의 일반 핀입니다.</span><span class="sxs-lookup"><span data-stu-id="8f212-109">**General-Purpose Input/Output (GPIO)** GPIO is a generic pin on an integrated circuit whose behavior, including whether it is an input or output pin, can be controlled by the user at run time.</span></span>  <span data-ttu-id="8f212-110">애플리케이션의 Windows.Devices.Gpio 네임스페이스를 사용하여 보드의 GPIO 핀을 조작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f212-110">You can use the Windows.Devices.Gpio namespace in your app to manipulate the GPIO pins on your board.</span></span>

<span data-ttu-id="8f212-111">**헤드** Windows IoT Core는 헤드 또는 헤드리스 모드일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f212-111">**Headed** Windows IoT Core can either be in headed or headless mode.</span></span> <span data-ttu-id="8f212-112">이 두 가지 모드의 차이점은 UI의 형식이 있는지 여부입니다.</span><span class="sxs-lookup"><span data-stu-id="8f212-112">The difference between these two modes is the presence or absence of any form of UI.</span></span> <span data-ttu-id="8f212-113">기본적으로 Windows 10 IoT Core는 헤드 모드에 있으며 컴퓨터 이름 및 IP 주소와 같은 시스템 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8f212-113">By default, Windows 10 IoT Core is in headed mode and displays system information like the computer name and IP address.</span></span>

<span data-ttu-id="8f212-114">**헤드리스** 헤드리스 모드에는 사용할 수 있는 UI 스택이 없으며 앱이 대화형 모드가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="8f212-114">**Headless** In headless mode, there is no UI stack available and apps are not interactive.</span></span> <span data-ttu-id="8f212-115">헤드리스 모드 앱은 서비스라고 간주할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f212-115">Headless mode apps can be thought of as services.</span></span>

<span data-ttu-id="8f212-116">**I2C(회로간 통합 회로)** 회로간 통합 회로 제어를 위한 단순 양방향 2선 직렬 데이터(SDA) 및 시리얼 클럭(SCL) 버스입니다.</span><span class="sxs-lookup"><span data-stu-id="8f212-116">**Inter-Integrated Circuits (I2C)** Simple bidirectional two-wire serial data (SDA) and serial clock (SCL) buses for inter-integrated circuit control.</span></span>  <span data-ttu-id="8f212-117">앱의 Windows.Devices.I2c 네임스페이스를 사용하여 I2C를 통해 디바이스와 통신할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f212-117">You can use the Windows.Devices.I2c namespace in your app to communicate with a device over I2C.</span></span>

<span data-ttu-id="8f212-118">**LED(발광 다이오드)** LED는 2리드 반도체 광원입니다.</span><span class="sxs-lookup"><span data-stu-id="8f212-118">**Light-Emitting Diode (LED)** A LED is a two-lead semiconductor light source.</span></span> <span data-ttu-id="8f212-119">이 다이오드는 활성화되면 빛을 방출하는 pn-junction 다이오드입니다.</span><span class="sxs-lookup"><span data-stu-id="8f212-119">It is a pn-junction diode, which emits light when activated.</span></span>

<span data-ttu-id="8f212-120">**Microsoft Windows KMDF(커널 모드 드라이버 프레임워크)** 드라이버 개발자가 커널 모드에서 드라이버 기능을 노출하여 드라이버가 시스템 메모리 및 하드웨어에 액세스할 수 있도록 하는 Microsoft 개발 프레임워크입니다.</span><span class="sxs-lookup"><span data-stu-id="8f212-120">**Microsoft Windows Kernel Mode Driver Framework (KMDF)** Microsoft development framework which allows driver developers to expose driver functionality in kernel mode, giving the driver access to system memory and hardware.</span></span>

<span data-ttu-id="8f212-121">**프로토타입** 만들려는 디바이스의 최종 버전을 더 원시 버전으로 개발하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="8f212-121">**Prototype** Developing a more raw version of a final version of a device that you're hoping to create.</span></span> <span data-ttu-id="8f212-122">제조 공정의 필수 단계가 아니라면 프로토타입 개발을 적극 권장합니다.</span><span class="sxs-lookup"><span data-stu-id="8f212-122">Prototyping is highly recommended, if not an obligatory step in the manufacturing process.</span></span> <span data-ttu-id="8f212-123">이 단계는 디바이스의 최종 버전에 사용할 모든 기능을 테스트하는 데 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f212-123">This stage should be used for testing any and all features you're hoping to use for the final version of your device.</span></span>

<span data-ttu-id="8f212-124">**SPI(직렬 주변기기 인터페이스) 버스** SPI 버스는 주로 포함된 시스템에서 근거리 통신에 사용되는 동기 직렬 통신 인터페이스 규격입니다.</span><span class="sxs-lookup"><span data-stu-id="8f212-124">**Serial Peripheral Interface Bus (SPI)** The SPI bus is a synchronous serial communication interface specification used for short distance communication, primarily in embedded systems.</span></span>  <span data-ttu-id="8f212-125">앱의 Windows.Devices.Spi 네임스페이스를 사용하여 SPI를 통해 디바이스와 통신할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f212-125">You can use the Windows.Devices.Spi namespace in your app to communicate with a device over SPI.</span></span>

<span data-ttu-id="8f212-126">**UART(유니버셜 비동기 수신기/송신기)** UART는 데이터 바이트를 받아 개별 비트를 순차적으로 전송하는 컴퓨터 하드웨어입니다.</span><span class="sxs-lookup"><span data-stu-id="8f212-126">**Universal Asynchronous Receiver/Transmitter (UART)** UART is a piece of computer hardware that takes bytes of data and transmits the individual bits serially.</span></span>

<span data-ttu-id="8f212-127">**UWP(유니버설 Windows 플랫폼)** 유니버설 Windows 플랫폼은 여러 디바이스에 걸쳐 핵심 API 계층을 보장합니다.</span><span class="sxs-lookup"><span data-stu-id="8f212-127">**Universal Windows Platform (UWP)** The Universal Windows Platform provides a guaranteed core API layer across devices.</span></span>  <span data-ttu-id="8f212-128">광범위한 디바이스에 설치할 수 있는 단일 앱 패키지를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f212-128">You can create a single app package that can be installed onto a wide range of devices.</span></span>

<span data-ttu-id="8f212-129">**VM(가상 머신)**</span><span class="sxs-lookup"><span data-stu-id="8f212-129">**Virtual Machine (VM)**</span></span><br/>
<span data-ttu-id="8f212-130">컴파일러 바이너리 코드와 실제로 프로그램의 명령을 수행하는 마이크로프로세서 사이의 인터페이스 역할을 하는 소프트웨어입니다.</span><span class="sxs-lookup"><span data-stu-id="8f212-130">Software that acts as an interface between compiler binary code and the microprocessor that actually performs the program's instructions.</span></span>  <span data-ttu-id="8f212-131">Windows에서는 Hyper-V 관리자를 사용하여 가상 머신을 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f212-131">In Windows, you can use Hyper-V Manager to manage virtual machines.</span></span>

<span data-ttu-id="8f212-132">**Windows 디바이스 콘솔(Devcon.exe)** 디바이스 콘솔인 DevCon(Devcon.exe)은 Windows를 실행하는 컴퓨터의 디바이스에 대한 자세한 정보를 표시하는 명령줄 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="8f212-132">**Windows Device Console (Devcon.exe)** DevCon (Devcon.exe), the Device Console, is a command-line tool that displays detailed information about devices on computers running Windows.</span></span> <span data-ttu-id="8f212-133">DevCon을 사용하여 디바이스를 활성화, 비활성화, 설치, 구성 및 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f212-133">You can use DevCon to enable, disable, install, configure, and remove devices.</span></span>  <span data-ttu-id="8f212-134">이 도구는 드라이버를 수동으로 설치하고 제거하는 데 주로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8f212-134">This tool is mostly used for manually installing and removing drivers.</span></span>
