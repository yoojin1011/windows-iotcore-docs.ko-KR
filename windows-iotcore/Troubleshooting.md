---
author: saraclay
Description: 다른 개발 관련 문제를 해결 합니다.
title: 문제 해결
ms.author: saclayt
ms.date: 08/28/18
ms.topic: article
ms.openlocfilehash: 00c748e4ce06e960dbc2a4250fb3cb279f4d092a
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513293"
---
# <a name="troubleshooting"></a><span data-ttu-id="d468b-103">문제 해결</span><span class="sxs-lookup"><span data-stu-id="d468b-103">Troubleshooting</span></span>
<span data-ttu-id="d468b-104">사람들이에서 일반적인 문제를 포함 하는 문서입니다.</span><span class="sxs-lookup"><span data-stu-id="d468b-104">This is an article that contains common troubleshooting issues that people have come across.</span></span> <span data-ttu-id="d468b-105">특정 항목을 찾으려면 단어 또는 문구 검색 하려면 Ctrl + F를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d468b-105">To find something specific, use Ctrl+F to find a word or phrase.</span></span> <span data-ttu-id="d468b-106">예정인 추가 하 시겠습니까?</span><span class="sxs-lookup"><span data-stu-id="d468b-106">Have any insight you want to add?</span></span> <span data-ttu-id="d468b-107">이 설명서 또는 아래 provident 콘텐츠 사용자 의견에 대 한 PR을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d468b-107">Create a PR for this documentation or provident content feedback below.</span></span>

> [!TIP]
> <span data-ttu-id="d468b-108">제조와 관련 된 문제 문제 해결을 위해 읽어보세요 합니다 [문제 해결 문서](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/troubleshooting) 있는 제조 지침.</span><span class="sxs-lookup"><span data-stu-id="d468b-108">For troubleshooting issues related to manufacturing, please read the [Troubleshooting doc](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/troubleshooting) in our manufacturing guide.</span></span>

## <a name="asus-tinkerboard-and-rockchip-support"></a><span data-ttu-id="d468b-109">ASU Tinkerboard 및 Rockchip 지원</span><span class="sxs-lookup"><span data-stu-id="d468b-109">ASUS Tinkerboard and Rockchip support</span></span>

<span data-ttu-id="d468b-110">ASU Tinkerboard 및 Rockchip 우리 공식적으로 지원 되지 않으며는 Rockchip SoC Windows 10 IoT Core 작업을 가져올 다른 제 3 자에 협력 하는 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d468b-110">While the ASUS Tinkerboard and Rockchip are not officially supported by us, there are cases where Rockchip has worked with other third parties to get SoC working on Windows 10 IoT Core.</span></span>

## <a name="issue-when-connecting-a-mbm-device-when-roaming"></a><span data-ttu-id="d468b-111">로밍 시 MBM 장치를 연결 하는 문제</span><span class="sxs-lookup"><span data-stu-id="d468b-111">Issue when connecting a MBM device when roaming</span></span>

<span data-ttu-id="d468b-112">두 가지 방법으로 로밍 사용 하도록 설정할 때 고려해 야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d468b-112">There are two things to consider when enabling roaming:</span></span>

1. <span data-ttu-id="d468b-113">profile.xml 로밍 구성 및 셀룰러 네트워크에 대 한 연결을 자동으로 설정 하 고 동작을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d468b-113">The profile.xml configures roaming and sets the behavior to automatically establish a connection to the cellular network.</span></span>
<span data-ttu-id="d468b-114">설정 로밍 프로필을 참조 하세요 [이 문서에서는](https://docs.microsoft.com/windows/desktop/mbn/schema-root)합니다.</span><span class="sxs-lookup"><span data-stu-id="d468b-114">To set a profile for roaming please refer to [this article](https://docs.microsoft.com/windows/desktop/mbn/schema-root).</span></span>

```
  <!-- applicability to any combination of home carrier, partner MOs and non-partner MOs, except for HomeAndNonPartner -->
  <xs:simpleType name="roamApplicabilityType">
    <xs:restriction base="xs:token">
       <xs:enumeration value="NonPartnerOnly"/>
       <xs:enumeration value="PartnerOnly"/>
       <xs:enumeration value="HomeOnly"/>
       <xs:enumeration value="HomeAndPartner"/>
       <xs:enumeration value="PartnerAndNonpartner"/>
       <xs:enumeration value="AllRoaming"/>
    </xs:restriction>
  </xs:simpleType>
  
  <xs:simpleType name="roamControlType">
    <xs:restriction base="xs:token">
       <xs:enumeration value="AllRoamAllowed"/>
       <xs:enumeration value="PartnerRoamAllowed"/>
       <xs:enumeration value="NoRoamAllowed"/>
    </xs:restriction>
  </xs:simpleType>
``` 

<span data-ttu-id="d468b-115">자동 연결에 대 한 프로필을 설정 하려면 "auto"를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="d468b-115">To set a profile for automatic connection, select "auto":</span></span>

```  
<!-- Connection Mode, default is "manual" -->
    <xs:element name="ConnectionMode" minOccurs="0">
      <xs:simpleType>
        <xs:restriction base="xs:string">
          <!-- manual connect always -->
          <xs:enumeration value="manual" />
          <!-- auto connect always -->
          <xs:enumeration value="auto" />
          <!-- auto connect when not roaming -->
          <xs:enumeration value="auto-home"/>
        </xs:restriction>
      </xs:simpleType>
    </xs:element>
```

2. <span data-ttu-id="d468b-116">다른 요소 인터페이스별 로밍 정책을 충족 해야 하는입니다.</span><span class="sxs-lookup"><span data-stu-id="d468b-116">Another factor is that the per-interface roaming policy must be satisfied.</span></span> <span data-ttu-id="d468b-117">기본적으로 해당 정책 ("홈 운송 업체만") FALSE로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d468b-117">By default, that policy is set to FALSE ("home carrier only").</span></span> <span data-ttu-id="d468b-118">쿼리 및 명령줄을 통해 변경할 수 있습니다이</span><span class="sxs-lookup"><span data-stu-id="d468b-118">This can be queried and changed in command line via</span></span> `netsh mbn get/set dataroamcontrol.`

<span data-ttu-id="d468b-119">예:</span><span class="sxs-lookup"><span data-stu-id="d468b-119">Example:</span></span>

```
    netsh mbn show dataroamcontrol int=*
    netsh mbn set dataroamcontrol interface=Cellular profileset=all state=all
    netsh mbn set dataroamcontrol help
```

<span data-ttu-id="d468b-120">오류가 발생할 수 있습니다 **0x139f (ERROR_INVALID_STATE)** 경우에서 장치를 로밍 중일 때 데이터 로밍-로밍 정책에 따라 연결 요청에 대 한 오류 전송 wwansvc 합니다.</span><span class="sxs-lookup"><span data-stu-id="d468b-120">You may get error **0x139f (ERROR_INVALID_STATE)** in the case when the device is roaming but the roaming policy disallows data roaming - error on a connect request sent to wwansvc.</span></span>

## <a name="raspberry-pi-3b-booting-issues"></a><span data-ttu-id="d468b-121">Raspberry Pi 3B + 부팅 문제</span><span class="sxs-lookup"><span data-stu-id="d468b-121">Raspberry Pi 3B+ booting issues</span></span>

> [!NOTE]
> <span data-ttu-id="d468b-122">Raspberry Pi 3B +이 릴리스에서 지원 되지 않는 기술 미리 보기를 합니다.</span><span class="sxs-lookup"><span data-stu-id="d468b-122">This release for the Raspberry Pi 3B+ is an unsupported technical preview.</span></span> <span data-ttu-id="d468b-123">제한 된 유효성 검사 및 활성화가 완료 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="d468b-123">Limited validation and enablement has been completed.</span></span> <span data-ttu-id="d468b-124">더 나은 평가판 환경과 모든 상용 제품을 사용 하세요 Raspberry Pi 3B 또는 기타 장치 지원 되는 Intel, Qualcomm, 또는 NXP Soc를 사용 하 여 합니다.</span><span class="sxs-lookup"><span data-stu-id="d468b-124">For a better evaluation experience and for any commercial products, please use the Raspberry Pi 3B or other devices with supported Intel, Qualcomm, or NXP SoCs.</span></span> <span data-ttu-id="d468b-125">Raspberry Pi 3B +를 사용 하 여 문제를 해결, 문제 해결 가이드를 참조 하세요 [여기](https://docs.microsoft.com/en-us/windows/iot-core/troubleshooting?branch=master#raspberry-pi-3b-booting-issues)합니다.</span><span class="sxs-lookup"><span data-stu-id="d468b-125">For troubleshooting issues with the Raspberry Pi 3B+, please see our Troubleshooting Guide, [here](https://docs.microsoft.com/en-us/windows/iot-core/troubleshooting?branch=master#raspberry-pi-3b-booting-issues).</span></span> 

<span data-ttu-id="d468b-126">Raspberry Pi 3 모델 B +는 최신 제품 Raspberry Pi 3 범위의 1.4 GHz, 이중 밴드 2.4ghz 및 5ghz 무선 LAN, Bluetooth 4.2/BLE 빠르고 이더넷에서 실행 되는 64 비트 쿼드 코어 프로세서를 자랑 하 고는 별도 PoE HA를 통해 PoE 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="d468b-126">The Raspberry Pi 3 Model B+ is the latest product in the Raspberry Pi 3 range, boasting a 64-bit quad core processor running at 1.4GHz, dual-band 2.4GHz and 5GHz wireless LAN, Bluetooth 4.2/BLE, faster Ethernet, and PoE capability via a separate PoE HA.</span></span>

<span data-ttu-id="d468b-127">최근 Windows 10 IoT Core 관심이 많은 고객에는 Windows 10 IoT Core 플러시한 후 장치가 정상적으로 부팅 되지 않습니다 하지만 여 Raspbian에 정상적으로 위치는 문제가 발생 했습니다.</span><span class="sxs-lookup"><span data-stu-id="d468b-127">Recently, many customers who are interested in Windows 10 IoT Core encountered a problem where the device could not boot normally after flushing Windows 10 IoT Core, but the Raspbian works fine on it.</span></span> <span data-ttu-id="d468b-128">다음은 부팅 문제를 해결 하는 방법에 몇 가지 제안 합니다.</span><span class="sxs-lookup"><span data-stu-id="d468b-128">The following are some suggestions on how to troubleshoot the boot problem.</span></span>

<span data-ttu-id="d468b-129">이 Insider Preview 이미지에서 몇 가지 알려진된 문제가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d468b-129">There are some known issues in this Insider Preview image.</span></span> <span data-ttu-id="d468b-130">note 하십시오.</span><span class="sxs-lookup"><span data-stu-id="d468b-130">Please note that:</span></span>
* <span data-ttu-id="d468b-131">이 이미지는 Raspberry Pi 3B + 기능만 및 Raspbierry Pi 2에서 부팅 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d468b-131">This image is only meant for the Raspberry Pi 3B+ and will not boot on the Raspbierry Pi 2.</span></span>
* <span data-ttu-id="d468b-132">Visual Studio에서 F5 드라이버 배포 Windows 10 IoT Core 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d468b-132">F5 driver deployment from Visual Studio does not work on Windows 10 IoT Core.</span></span>
* <span data-ttu-id="d468b-133">온 보 딩 Wi-fi 및 Bluetooth Raspberry Pi 3B 이상에서 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d468b-133">Onboard Wi-Fi and Bluetooth do not work on the Raspberry Pi 3B+.</span></span>
* <span data-ttu-id="d468b-134">Ft5406 터치 화면 드라이버는 Raspberry Pi 3B 이상에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d468b-134">Ft5406 touch screen driver is disabled on the Raspberry Pi 3B+.</span></span>
* <span data-ttu-id="d468b-135">SD 카드 활동 LED 비활성화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d468b-135">SD card activity LED is disabled.</span></span>

<span data-ttu-id="d468b-136">Windows 10 IoT Core 사용 하는 SD 카드를 선택할 때 두 가지 요구 사항이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d468b-136">There are only two requirements when choosing which SD cards to use with Windows 10 IoT Core.</span></span> <span data-ttu-id="d468b-137">클래스 10 SD 카드를 사용 하 여 카드에 충분 한 공간-최소 8GB의 공간이 있는지 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d468b-137">You need to use a class 10 SD card and make sure the card has enough space - at least 8 GB of space.</span></span> <span data-ttu-id="d468b-138">Windows 10 IoT Core 호환 되도록 하기 위해 Microsoft에서 확인 된 SD 카드의 몇 가지 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d468b-138">There are a couple of SD cards that have been verified by Microsoft to be compatible with Windows 10 IoT Core:</span></span>
* <span data-ttu-id="d468b-139">Samsung EVO 32 GB 클래스 10 Micros SDHC 카드</span><span class="sxs-lookup"><span data-stu-id="d468b-139">Samsung EVO 32 GB class 10 Micros SDHC card</span></span>
* <span data-ttu-id="d468b-140">SanDisk Ultra 마이크로 SDHC, 16GB 카드</span><span class="sxs-lookup"><span data-stu-id="d468b-140">SanDisk Ultra Micro SDHC, 16 GB card</span></span>

<span data-ttu-id="d468b-141">일반적으로 SD 카드가 위조 또는 손상 되거나 손상 될 경우를 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d468b-141">Generally, you need to check if the SD card is fake or if it is damaged or corrupt.</span></span> <span data-ttu-id="d468b-142">SD 카드는 동일 하 게 발생 하기 쉬운 다양 한 전원 부족 또는 잘못 된 제거와 같은 요인으로 인해 손상입니다.</span><span class="sxs-lookup"><span data-stu-id="d468b-142">The SD card is equally prone to corruption due to a variety of factors such as power shortage or improper removal.</span></span> <span data-ttu-id="d468b-143">꺼냅니다 카드 손상 으로부터 보호 하는 것이 반드시 합니다.</span><span class="sxs-lookup"><span data-stu-id="d468b-143">It is important to safeguard your memroy card from damage.</span></span>

<span data-ttu-id="d468b-144">SD 카드 이미지 flash를 사용할 수 있습니다 합니다 [Windows 10 IoT Core 대시보드](https://docs.microsoft.com/en-us/windows/iot-core/connect-your-device/iotdashboard)합니다.</span><span class="sxs-lookup"><span data-stu-id="d468b-144">To flash your image to a SD card, you can use the [Windows 10 IoT Core Dashboard](https://docs.microsoft.com/en-us/windows/iot-core/connect-your-device/iotdashboard).</span></span> <span data-ttu-id="d468b-145">OS 빌드 필드에 "Custom"를 선택 하 고 플래시 FFU 파일을 선택 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d468b-145">You will need to choose "Custom" in the OS Build field, then select the FFU file to flash.</span></span> 

<span data-ttu-id="d468b-146">장치에서 모든 하드웨어 오류가 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="d468b-146">Check to see if there are any hardware failure in the device.</span></span> <span data-ttu-id="d468b-147">Raspberry Pi 3B + 보드에는 3B 동일 두 led가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d468b-147">There are two LEDs on the Raspberry Pi 3B+ board, same as the 3B.</span></span> <span data-ttu-id="d468b-148">한 동안 다른 스냅숏이 ACT에 대 한 전원입니다.</span><span class="sxs-lookup"><span data-stu-id="d468b-148">One is for PWR while another is for ACT.</span></span> <span data-ttu-id="d468b-149">밝은 하면 개수는 보드 부팅 되 고 있는지 여부를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d468b-149">The number of blinks the ACT light makes will determine whether or not your board is booting.</span></span> <span data-ttu-id="d468b-150">Raspberry Pi 3B 이상에서 부팅 중 일부는 동안 SD 카드 활동 LED 플래시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d468b-150">The SD card activity LED will not flash during some portions of booting on the Raspberry Pi 3B+.</span></span>

<span data-ttu-id="d468b-151">장치가 부팅 되 고 대기 중인 페이지를 표시 하는 장치를 있으므로 편안 하 게 기다려 주세요.</span><span class="sxs-lookup"><span data-stu-id="d468b-151">When the device is booting and the device shows the waiting page, please wait patiently.</span></span> <span data-ttu-id="d468b-152">일반적으로이 값은 1 분까지 지속 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d468b-152">Generally, this will last up to a minute.</span></span> <span data-ttu-id="d468b-153">하지만 경우에 따라 SD 카드 읽기 / 쓰기 속도, 인해 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d468b-153">But sometimes, due to the SD card read-write speed, it may take longer.</span></span>

<span data-ttu-id="d468b-154">장치는 Windows 10 IoT Core 사용 하 여 정상적으로 부팅할 수 없습니다, 하는 경우 하드웨어에서 문제가 발생 하는지 여부를 줄이기 위해 SD 카드에 (예: Raspbian) Linux OS를 시도할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d468b-154">If the device can't boot normally with Windows 10 IoT Core, you can try to flash a Linux OS (such as Raspbian) to the SD card to narrow down whether the issue is caused by hardware.</span></span> 

<span data-ttu-id="d468b-155">"Rainbow 화면" 보시기를 찾았으면 3B + 릴리스, 사용 가능한 버전을 업데이트 하는 있는지 확인 하십시오 [여기](https://www.microsoft.com/en-us/software-download/windowsiot)합니다.</span><span class="sxs-lookup"><span data-stu-id="d468b-155">If you find that you're getting a "rainbow screen", please check to make sure that you flashed the 3B+ release version, available [here](https://www.microsoft.com/en-us/software-download/windowsiot).</span></span> <span data-ttu-id="d468b-156">자습서를 깜박이 커뮤니티 제공 3B +를 사용 하 여 프로세스를 확인할 수 있습니다 [여기](https://www.hackster.io/JiongShi/windows-10-iot-core-for-raspberry-pi-3-model-b-92b1a3)합니다.</span><span class="sxs-lookup"><span data-stu-id="d468b-156">You can verify your process with a community-submitted 3B+ flashing tutorial [here](https://www.hackster.io/JiongShi/windows-10-iot-core-for-raspberry-pi-3-model-b-92b1a3).</span></span>

## <a name="serial-port-communication-on-windows-10-iot-core-for-raspberry-pi"></a><span data-ttu-id="d468b-157">Raspberry Pi에 대 한 Windows 10 IoT Core 직렬 포트 통신</span><span class="sxs-lookup"><span data-stu-id="d468b-157">Serial Port communication on Windows 10 IoT Core for Raspberry Pi</span></span> 

<span data-ttu-id="d468b-158">Raspberry Pi에서 하드웨어 UART 및 USB UART 어댑터 모두 직렬 communicaiton 사용 하 여 응용 프로그램에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d468b-158">On the Raspberry Pi, hardware UART and USB UART adapters both are usable for your application with serial communicaiton.</span></span> <span data-ttu-id="d468b-159">기본적으로 UART 전송 및 수신 하 여 pin은 pin 8 및 10 GPIO 헤더에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d468b-159">By default, the UART transmit and receive pins are pins 8 and 10 on teh GPIO header.</span></span>

![UART 및 USB UART 어댑터](media/Troubleshooting/adapters.png)

<span data-ttu-id="d468b-161">읽어보세요 [이 문서에서는](https://docs.microsoft.com/en-us/windows/iot-core/learn-about-hardware/pinmappings/pinmappingsrpi#serial-uart) UART0를 초기화 하 고 읽기 뒤 쓰기를 수행 하는 방법에 자세히 알아보려면 합니다.</span><span class="sxs-lookup"><span data-stu-id="d468b-161">You can read [this article](https://docs.microsoft.com/en-us/windows/iot-core/learn-about-hardware/pinmappings/pinmappingsrpi#serial-uart) to learn more about how to initialize UART0 and perform a write followed by a read.</span></span>

<span data-ttu-id="d468b-162">또한 무선 주파수 통신 (RFCOMM)는 클래식 Bluetooth에 대 한 기본 직렬 통신 합니다.</span><span class="sxs-lookup"><span data-stu-id="d468b-162">In addition, Radio Frequency Communication (RFCOMM) is the underlying serial communications for classic Bluetooth.</span></span> <span data-ttu-id="d468b-163">가리킵니다 [이 GitHub 샘플](https://github.com/djaus2/iotbluetoothserial) Bluetooth 일련 번호를 가진 IoT 장치를 통해 연결 된 Windows 10 IoT Core UWP 앱 실행에 대해 자세히 알아보려면 합니다.</span><span class="sxs-lookup"><span data-stu-id="d468b-163">Refer to [this GitHub sample](https://github.com/djaus2/iotbluetoothserial) to learn about running UWP apps on Windows 10 IoT Core to connected over an IoT device with Bluetooth Serial.</span></span>

<span data-ttu-id="d468b-164">장치 수 없습니다. 읽기/쓰기 직렬 포트를 통해 데이터에서 발견 되 면 문제를 해결 하려면 다음 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="d468b-164">If you encounter that the device cannot read/write data through the serial port, follow the steps below to troubleshoot:</span></span>

1. <span data-ttu-id="d468b-165">점퍼-아래-를 사용 하 여 RX에는 TX를 연결한 경우 앱 수 읽기/쓰기 데이터를 확인 하는 샘플 코드를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="d468b-165">Connect the TX to RX with Jumper - shown below - then run the sample code to check if the app can read/write data.</span></span> <span data-ttu-id="d468b-166">작동 하지 않는 경우 보드에서 IC 손상 될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d468b-166">If this does not work, the IC on the board may be broken.</span></span>

![Raspberry Pi에서 RX에는 텍사스](media/Troubleshooting/txrx.png)

2. <span data-ttu-id="d468b-168">BaudRate, 핸드셰이킹 및 StopBits 올바르게 구성 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="d468b-168">Make sure the BaudRate, Handshaking and StopBits are configured correctly.</span></span> <span data-ttu-id="d468b-169">테스트할 직렬 포트에 RS232 인터페이스 (예: DB9)를 완료 하는 경우 일반적인 핸드셰이킹 crossovers 연결할 RxTx 교차 와이어를 사용 하 여 DB 플러그를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d468b-169">If the serial port to be tested has a complete RS232 interface (e.g. DB9), use a DB plug with the RxTx crossover wires connected with the typical handshaking crossovers.</span></span> <span data-ttu-id="d468b-170">일부 RS232 포트 (또는 USB 어댑터)를 제대로 작동 하려면 먼저 평가할 운송 업체 DCD 및 DCE 준비 (DSR)와 같은 신호 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="d468b-170">Some RS232 ports (or USB adapters) require signals such as Carrier Detect (DCD) and DCE Ready (DSR) to be asserted before they function properly.</span></span>

3. <span data-ttu-id="d468b-171">Windows 10 IoT Core USB UART 어댑터를 사용 하려는 경우 다음 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d468b-171">If you want to use USB UART adapters on Windows 10 IoT Core, the following are supported:</span></span>

* <span data-ttu-id="d468b-172">CP2102 USB 2.0</span><span class="sxs-lookup"><span data-stu-id="d468b-172">CP2102 USB 2.0</span></span>
* <span data-ttu-id="d468b-173">TTL 모듈에 대 한 직렬 변환기</span><span class="sxs-lookup"><span data-stu-id="d468b-173">TTL Module Serial Converter</span></span>
* <span data-ttu-id="d468b-174">FTDI</span><span class="sxs-lookup"><span data-stu-id="d468b-174">FTDI</span></span>
* <span data-ttu-id="d468b-175">제네릭 usbser.sys</span><span class="sxs-lookup"><span data-stu-id="d468b-175">Generic usbser.sys</span></span>

<span data-ttu-id="d468b-176">Devcon.exe 스택 이용할 수 있습니다 \* 및 devcon.exe 상태 \* cmdlet에 필요한 드라이버 스택 및 Windows 10 IoT Core 드라이버 상태를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="d468b-176">You can also use the devcon.exe stack \* and devcon.exe status\* cmdlet to check the expected drivers stack and drivers status on Windows 10 IoT Core.</span></span>

```
USB\VID_10C4&PID_EA60\0001
    Name: Silicon Labs CP210x USB to UART Bridge
    Setup Class: {4d36e978-e325-11ce-bfc1-08002be10318} Ports
    Controlling service:
        silabser
```
<span data-ttu-id="d468b-177">[Mincomm](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/BusTools/MinComm) 는 직렬 포트 문제를 해결 하는 또 다른 유용한 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="d468b-177">[Mincomm](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/BusTools/MinComm) is another helpful tool to troubleshoot serial port issues.</span></span> <span data-ttu-id="d468b-178">이 도구 수 포트 열거 장치 ID와 이름을 제공, 포트를 열어 구성 설정 (즉, 전송 속도, 비트의 정지 비트, 등) 및 데이터 전송 및 수신 합니다.</span><span class="sxs-lookup"><span data-stu-id="d468b-178">This tool can enumerate ports, give you their friendly name and Device ID, open ports, configure settings (i.e. baud rate, stop bits, etc.) and send and receive data.</span></span> 

## <a name="sirep-test-service"></a><span data-ttu-id="d468b-179">Sirep 테스트 서비스</span><span class="sxs-lookup"><span data-stu-id="d468b-179">Sirep Test service</span></span>
<span data-ttu-id="d468b-180">Sirep 테스트 서비스를 기본적으로 일반 정품 이미지에서 시작 시 Sirep를 사용 하지 않도록 설정 하려는 경우을 해제 하는 경우에에 로그인 하 고 자동 시작에서 Sirep를 사용 하지 않도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d468b-180">Even though the Sirep Test service is not enabled by default in retail images, in case you still want to disable the Sirep service on startup, you can login and disable Sirep from autostart.</span></span> 

<span data-ttu-id="d468b-181">아래와 같이를 위해 다음 PowerShell 명령을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d468b-181">You can use the following PowerShell commands to do so, as shown below:</span></span>

```
administrator@MINWINPC C:\Data\Users\administrator>sc stop TestSirepSvc

SERVICE_NAME: TestSirepSvc
       TYPE               : 20  WIN32_SHARE_PROCESS
        STATE              : 3  STOP_PENDING
                                (STOPPABLE, NOT_PAUSABLE, ACCEPTS_PRESHUTDOWN)
        WIN32_EXIT_CODE    : 0  (0x0)
        SERVICE_EXIT_CODE  : 0  (0x0)
        CHECKPOINT         : 0x4
        WAIT_HINT          : 0x1770

administrator@MINWINPC C:\Data\Users\administrator>sc query TestSirepSvc

SERVICE_NAME: TestSirepSvc
        TYPE               : 20  WIN32_SHARE_PROCESS
        STATE              : 1  STOPPED
        WIN32_EXIT_CODE    : 0  (0x0)
        SERVICE_EXIT_CODE  : 0  (0x0)
        CHECKPOINT         : 0x0
        WAIT_HINT          : 0x0

administrator@MINWINPC C:\Data\Users\administrator>sc config TestSirepSvc start=disabled
[SC] ChangeServiceConfig SUCCESS
```

## <a name="tablet-mode"></a><span data-ttu-id="d468b-182">태블릿 모드</span><span class="sxs-lookup"><span data-stu-id="d468b-182">Tablet mode</span></span>

<span data-ttu-id="d468b-183">"모드 tablet"는 데스크톱 셸 존재 하는 개념 및 IoT Core에 적용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d468b-183">"Tablet Mode" is a concept that only exist on Desktop shell and doesn’t apply to IoT Core.</span></span> 

<span data-ttu-id="d468b-184">장치 하드웨어 (두 통해 I2C 또는 USB HID touch) 지원 되는, 터치는 받은 편지함 클래스 드라이버를 사용 하 여 자동으로 작동 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d468b-184">If the device have supported hardware (either through I2C or USB HID touch), touch should function automatically using the inbox class drivers.</span></span> <span data-ttu-id="d468b-185">자세한 내용은이 대 한 [여기](https://docs.microsoft.com/en-us/windows-hardware/design/component-guidelines/touchscreen-device-bus-connectivity)합니다.</span><span class="sxs-lookup"><span data-stu-id="d468b-185">You can read more about this [here](https://docs.microsoft.com/en-us/windows-hardware/design/component-guidelines/touchscreen-device-bus-connectivity).</span></span>


## <a name="yubikey-support"></a><span data-ttu-id="d468b-186">Yubikey 지원</span><span class="sxs-lookup"><span data-stu-id="d468b-186">Yubikey support</span></span>

<span data-ttu-id="d468b-187">Windows 10 IoT Core는 스마트 카드 지원은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d468b-187">Windows 10 IoT Core does not have smart card support.</span></span> <span data-ttu-id="d468b-188">그러나 스마트 카드는 장치 Pin을 사용 하 여 고 Yubikey, 단추를 누를 경우 보안이 유지 되는 때문에 사용자 id 및 장치 id 아닌에 사용 되는 일반적으로입니다.</span><span class="sxs-lookup"><span data-stu-id="d468b-188">However, smart cards are usually devices used for user identity and not device identity because they are secured with PINs and, in the case of the Yubikey, a button to press.</span></span> <span data-ttu-id="d468b-189">이 IoT 장치를 사용 하 여는 조화 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d468b-189">This does not harmonize with an IoT device.</span></span> <span data-ttu-id="d468b-190">대안을 찾고 있는 경우 장치에는 TPM 2.0 보다 Yubikey 또는 스마트 카드를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d468b-190">If you're looking for an alternative, a TPM 2.0 on the device may serve better than a Yubikey or smart card.</span></span> <span data-ttu-id="d468b-191">Tpm에 대 한 전체 인증서 지원을 장치 뿐만 아니라 사용자 인증서를 저장 하 고 Azure IoT 액세스 (Limpets) 자격 증명입니다.</span><span class="sxs-lookup"><span data-stu-id="d468b-191">We have full certificate support for TPMs and they are meant to store devices as well as user certificates and Azure IoT access credentials (Limpets).</span></span>
