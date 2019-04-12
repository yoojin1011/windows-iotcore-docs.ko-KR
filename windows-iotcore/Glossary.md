---
title: Windows IoT에 대 한 용어집
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: 설명서를 통해 다양 한 Windows IoT Core 관련 용어에 알아봅니다.
keywords: windows iot, 용어집, 용어, 용어, 정의
ms.openlocfilehash: 155de380459cbb74642352ff2a2ff718ebfe1ed7
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513709"
---
# <a name="glossary-for-windows-iot"></a><span data-ttu-id="14bd7-104">Windows IoT에 대 한 용어집</span><span class="sxs-lookup"><span data-stu-id="14bd7-104">Glossary for Windows IoT</span></span>

<span data-ttu-id="14bd7-105">**고급 구성 및 전원 인터페이스 (ACPI)** ACPI (고급 구성 및 전원 인터페이스)는 공동 Hewlett-Packard, Intel, Microsoft, Phoenix, 및 Toshiba 개발한 공개 된 업계 사양입니다.</span><span class="sxs-lookup"><span data-stu-id="14bd7-105">**Advanced Configuration & Power Interface (ACPI)** ACPI (Advanced Configuration and Power Interface) is an open industry specification co-developed by Hewlett-Packard, Intel, Microsoft, Phoenix, and Toshiba.</span></span>  <span data-ttu-id="14bd7-106">ACPI OS 지향 구성, 전원 관리 및 모바일, 데스크톱 및 서버 플랫폼의 열 관리를 사용 하도록 설정 하는 업계 표준 인터페이스를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="14bd7-106">ACPI establishes industry-standard interfaces enabling OS-directed configuration, power management, and thermal management of mobile, desktop, and server platforms.</span></span>

<span data-ttu-id="14bd7-107">**기본 입/출력 시스템 (BIOS)** 시작 시 하드웨어 호환성 테스트, 운영 체제를 시작 하 고, 하드웨어 장치 간에 데이터를 전송을 지 원하는 필수 소프트웨어 루틴 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="14bd7-107">**Basic Input/Output System (BIOS)** The set of essential software routines that test hardware at startup, start the operating system, and support the transfer of data among hardware devices.</span></span>

<span data-ttu-id="14bd7-108">**귀하는** 개발 및 유지 공개적으로 상업적으로 배치 하는 장치를 제조 합니다.</span><span class="sxs-lookup"><span data-stu-id="14bd7-108">**Commercialize** Developing and manufacturing a device with the intention of putting it out to the public commercially.</span></span>

<span data-ttu-id="14bd7-109">**범용 입/출력 (GPIO)** GPIO은 런타임 시 사용자가 pin을 입력 또는 출력 인지를 포함 하 여 해당 동작을 제어할 수 있습니다 하는 통합 회로에서 제네릭 pin입니다.</span><span class="sxs-lookup"><span data-stu-id="14bd7-109">**General-Purpose Input/Output (GPIO)** GPIO is a generic pin on an integrated circuit whose behavior, including whether it is an input or output pin, can be controlled by the user at run time.</span></span>  <span data-ttu-id="14bd7-110">GPIO를 조작 하 여 앱에서 네임 스페이스 보드에 고정 Windows.Devices.Gpio를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14bd7-110">You can use the Windows.Devices.Gpio namespace in your app to manipulate the GPIO pins on your board.</span></span>

<span data-ttu-id="14bd7-111">**양방향** 헤드 또는 헤드리스 모드로 Windows IoT Core 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14bd7-111">**Headed** Windows IoT Core can either be in headed or headless mode.</span></span> <span data-ttu-id="14bd7-112">이러한 두 가지 모드 간의 차이점은 UI의 존재 여부</span><span class="sxs-lookup"><span data-stu-id="14bd7-112">The difference between these two modes is the presence or absence of any form of UI.</span></span> <span data-ttu-id="14bd7-113">기본적으로 Windows 10 IoT Core 헤드 모드만 이며 컴퓨터 이름 및 IP 주소와 같은 시스템 정보를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="14bd7-113">By default, Windows 10 IoT Core is in headed mode and displays system information like the computer name and IP address.</span></span>

<span data-ttu-id="14bd7-114">**헤드리스** 헤드리스 모드로 UI 스택 없음 사용할 수 있고 앱은 대화형 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="14bd7-114">**Headless** In headless mode, there is no UI stack available and apps are not interactive.</span></span> <span data-ttu-id="14bd7-115">헤드리스 모드로 앱 서비스로 간주 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14bd7-115">Headless mode apps can be thought of as services.</span></span>

<span data-ttu-id="14bd7-116">**회로 (I2C) 간 통합** 통합 회로 제어 간 단순 양방향 두 실시간 직렬 데이터 (SDA) 및 직렬 클럭 (SCL) 버스에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="14bd7-116">**Inter-Integrated Circuits (I2C)** Simple bidirectional two-wire serial data (SDA) and serial clock (SCL) buses for inter-integrated circuit control.</span></span>  <span data-ttu-id="14bd7-117">Over I2C 장치와 통신 하도록 앱에서 Windows.Devices.I2c 네임 스페이스를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14bd7-117">You can use the Windows.Devices.I2c namespace in your app to communicate with a device over I2C.</span></span>

<span data-ttu-id="14bd7-118">**발광 다이오드 LED** 는 LED가 2-리드 반도체 광원 합니다.</span><span class="sxs-lookup"><span data-stu-id="14bd7-118">**Light-Emitting Diode (LED)** A LED is a two-lead semiconductor light source.</span></span> <span data-ttu-id="14bd7-119">것을 활성화 될 때 빛을 내보내는 pn 접합 다이오드 합니다.</span><span class="sxs-lookup"><span data-stu-id="14bd7-119">It is a pn-junction diode, which emits light when activated.</span></span>

<span data-ttu-id="14bd7-120">**Microsoft Windows 커널 모드 드라이버 프레임 워크 (KMDF)** 시스템 메모리와 하드웨어에 드라이버 액세스할 수 있도록 커널 모드 드라이버 기능을 노출 하는 드라이버 개발자가 Microsoft 개발 프레임 워크입니다.</span><span class="sxs-lookup"><span data-stu-id="14bd7-120">**Microsoft Windows Kernel Mode Driver Framework (KMDF)** Microsoft development framework which allows driver developers to expose driver functionality in kernel mode, giving the driver access to system memory and hardware.</span></span>

<span data-ttu-id="14bd7-121">**프로토타입** 더 원시 버전 만들기 하고자 하는 장치의 최종 버전을 개발 합니다.</span><span class="sxs-lookup"><span data-stu-id="14bd7-121">**Prototype** Developing a more raw version of a final version of a device that you're hoping to create.</span></span> <span data-ttu-id="14bd7-122">프로토타입 것이 좋습니다, 경우 not 제조 프로세스에서 필수 항목 이지만 단계입니다.</span><span class="sxs-lookup"><span data-stu-id="14bd7-122">Prototyping is highly recommended, if not an obligatory step in the manufacturing process.</span></span> <span data-ttu-id="14bd7-123">테스트 장치의 최종 버전을 사용 하고자 하는 모든 기능에 대 한이 단계를 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="14bd7-123">This stage should be used for testing any and all features you're hoping to use for the final version of your device.</span></span>

<span data-ttu-id="14bd7-124">**직렬 주변 Bus SPI (인터페이스)** 는 SPI 버스는 기본적으로 포함 된 시스템에서 근거리 통신을 위해 사용 하는 동기 직렬 통신 인터페이스 사양입니다.</span><span class="sxs-lookup"><span data-stu-id="14bd7-124">**Serial Peripheral Interface Bus (SPI)** The SPI bus is a synchronous serial communication interface specification used for short distance communication, primarily in embedded systems.</span></span>  <span data-ttu-id="14bd7-125">앱에서 SPI 장치와 통신할 수 Windows.Devices.Spi 네임 스페이스를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14bd7-125">You can use the Windows.Devices.Spi namespace in your app to communicate with a device over SPI.</span></span>

<span data-ttu-id="14bd7-126">**범용 비동기 수신기/송신기 (UART)** UART는 데이터의 바이트를 사용 하 고 개별 비트를 순차적으로 전송 하는 컴퓨터 하드웨어입니다.</span><span class="sxs-lookup"><span data-stu-id="14bd7-126">**Universal Asynchronous Receiver/Transmitter (UART)** UART is a piece of computer hardware that takes bytes of data and transmits the individual bits serially.</span></span>

<span data-ttu-id="14bd7-127">**유니버설 Windows 플랫폼 (UWP)** 유니버설 Windows 플랫폼의 장치 간에 보장된 핵심 API 계층을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="14bd7-127">**Universal Windows Platform (UWP)** The Universal Windows Platform provides a guaranteed core API layer across devices.</span></span>  <span data-ttu-id="14bd7-128">광범위 한 장치에 설치할 수 있는 단일 앱 패키지를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14bd7-128">You can create a single app package that can be installed onto a wide range of devices.</span></span>

**<span data-ttu-id="14bd7-129">가상 머신 (VM)</span><span class="sxs-lookup"><span data-stu-id="14bd7-129">Virtual Machine (VM)</span></span>**<br/>
<span data-ttu-id="14bd7-130">실제로 프로그램의 지침을 수행 하는 마이크로프로세서 컴파일러 이진 코드 사이의 인터페이스 역할을 하는 소프트웨어입니다.</span><span class="sxs-lookup"><span data-stu-id="14bd7-130">Software that acts as an interface between compiler binary code and the microprocessor that actually performs the program's instructions.</span></span>  <span data-ttu-id="14bd7-131">Windows, 가상 컴퓨터를 관리 하려면 Hyper-v 관리자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14bd7-131">In Windows, you can use Hyper-V Manager to manage virtual machines.</span></span>

<span data-ttu-id="14bd7-132">**Windows 장치 콘솔 (Devcon.exe)** DevCon (Devcon.exe) 장치 콘솔은 Windows를 실행 하는 컴퓨터에 장치에 대 한 자세한 정보를 표시 하는 명령줄 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="14bd7-132">**Windows Device Console (Devcon.exe)** DevCon (Devcon.exe), the Device Console, is a command-line tool that displays detailed information about devices on computers running Windows.</span></span> <span data-ttu-id="14bd7-133">사용 하도록 설정, 사용 하지 않도록 설정, 설치, 구성 및 장치를 제거 하려면 DevCon를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14bd7-133">You can use DevCon to enable, disable, install, configure, and remove devices.</span></span>  <span data-ttu-id="14bd7-134">이 도구는 수동으로 설치 하 고 드라이버를 제거에 주로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="14bd7-134">This tool is mostly used for manually installing and removing drivers.</span></span>
