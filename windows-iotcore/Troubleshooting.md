---
author: saraclay
Description: 다양한 개발 관련 문제 해결.
title: 문제 해결
ms.author: saclayt
ms.date: 08/28/18
ms.topic: article
ms.openlocfilehash: 8b93ad987c27e1123d68c4d22148447ccc99e37d
ms.sourcegitcommit: 9ec4716afde25fdc8b94f7c0794448501f451b55
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/17/2019
ms.locfileid: "66491705"
---
# <a name="troubleshooting"></a><span data-ttu-id="c7397-103">문제 해결</span><span class="sxs-lookup"><span data-stu-id="c7397-103">Troubleshooting</span></span>
<span data-ttu-id="c7397-104">이 문서에는 사용자에게 일반적으로 발생하는 문제 해결 이슈가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7397-104">This is an article that contains common troubleshooting issues that people have come across.</span></span> <span data-ttu-id="c7397-105">Ctrl+F를 사용하여 단어 또는 구문을 입력하면 특정 항목을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7397-105">To find something specific, use Ctrl+F to find a word or phrase.</span></span> <span data-ttu-id="c7397-106">추가하려는 인사이트가 있나요?</span><span class="sxs-lookup"><span data-stu-id="c7397-106">Have any insight you want to add?</span></span> <span data-ttu-id="c7397-107">그렇다면 이 설명서 또는 아래 제공된 콘텐츠 피드백에 대한 PR를 생성하세요.</span><span class="sxs-lookup"><span data-stu-id="c7397-107">Create a PR for this documentation or provident content feedback below.</span></span>

> [!TIP]
> <span data-ttu-id="c7397-108">제조와 관련된 문제 해결 이슈의 경우 제조 가이드의 [문제 해결 문서](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/troubleshooting)를 읽어 주세요.</span><span class="sxs-lookup"><span data-stu-id="c7397-108">For troubleshooting issues related to manufacturing, please read the [Troubleshooting doc](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/troubleshooting) in our manufacturing guide.</span></span>

## <a name="asus-tinkerboard-and-rockchip-support"></a><span data-ttu-id="c7397-109">ASUS Tinkerboard 및 Rockchip 지원</span><span class="sxs-lookup"><span data-stu-id="c7397-109">ASUS Tinkerboard and Rockchip support</span></span>

<span data-ttu-id="c7397-110">ASUS Tinkerboard 및 Rockchip은 공식적으로 지원되지 않지만, SoC가 Windows 10 IoT Core에서 작동할 수 있도록 Rockchip이 다른 타사와 협업한 사례가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7397-110">While the ASUS Tinkerboard and Rockchip are not officially supported by us, there are cases where Rockchip has worked with other third parties to get SoC working on Windows 10 IoT Core.</span></span>

## <a name="issue-when-connecting-a-mbm-device-when-roaming"></a><span data-ttu-id="c7397-111">로밍 시 MBM 디바이스를 연결할 때 발생하는 문제</span><span class="sxs-lookup"><span data-stu-id="c7397-111">Issue when connecting a MBM device when roaming</span></span>

<span data-ttu-id="c7397-112">로밍을 사용 설정할 때 고려해야 할 두 가지 사항이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7397-112">There are two things to consider when enabling roaming:</span></span>

1. <span data-ttu-id="c7397-113">profile.xml은 셀룰러 네트워크에 자동 연결하도록 로밍을 구성하고 동작을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c7397-113">The profile.xml configures roaming and sets the behavior to automatically establish a connection to the cellular network.</span></span>
<span data-ttu-id="c7397-114">로밍에 사용할 프로필을 설정하려면 [이 문서](https://docs.microsoft.com/windows/desktop/mbn/schema-root)를 참조하고</span><span class="sxs-lookup"><span data-stu-id="c7397-114">To set a profile for roaming please refer to [this article](https://docs.microsoft.com/windows/desktop/mbn/schema-root).</span></span>

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

<span data-ttu-id="c7397-115">자동 연결에 사용할 프로필을 설정하려면 "auto"를 선택하세요.</span><span class="sxs-lookup"><span data-stu-id="c7397-115">To set a profile for automatic connection, select "auto":</span></span>

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

2. <span data-ttu-id="c7397-116">다른 요소로는, 인터페이스 특정 로밍 정책을 충족해야 한다는 것이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7397-116">Another factor is that the per-interface roaming policy must be satisfied.</span></span> <span data-ttu-id="c7397-117">기본값으로 이 정책은 FALSE(“홈 통신 회사만")로 설정되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7397-117">By default, that policy is set to FALSE ("home carrier only").</span></span> <span data-ttu-id="c7397-118">이 항목은 `netsh mbn get/set dataroamcontrol.`을 통해 쿼리하여 명령줄에서 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7397-118">This can be queried and changed in command line via `netsh mbn get/set dataroamcontrol.`</span></span>

<span data-ttu-id="c7397-119">예제:</span><span class="sxs-lookup"><span data-stu-id="c7397-119">Example:</span></span>

```
    netsh mbn show dataroamcontrol int=*
    netsh mbn set dataroamcontrol interface=Cellular profileset=all state=all
    netsh mbn set dataroamcontrol help
```

<span data-ttu-id="c7397-120">디바이스가 로밍 중이지만, 로밍 정책에서 데이터 로밍을 허용하지 않는 경우에 **0x139f (ERROR_INVALID_STATE)** 오류가 표시될 수 있습니다. 즉, wwansvc로 전송된 연결 요청에 대한 오류입니다.</span><span class="sxs-lookup"><span data-stu-id="c7397-120">You may get error **0x139f (ERROR_INVALID_STATE)** in the case when the device is roaming but the roaming policy disallows data roaming - error on a connect request sent to wwansvc.</span></span>

## <a name="raspberry-pi-3b-booting-issues"></a><span data-ttu-id="c7397-121">Raspberry Pi 3B + 부팅 문제</span><span class="sxs-lookup"><span data-stu-id="c7397-121">Raspberry Pi 3B+ booting issues</span></span>

> [!NOTE]
> <span data-ttu-id="c7397-122">이번 Raspberry Pi 3B용 릴리스에서는 기술 미리 보기를 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7397-122">This release for the Raspberry Pi 3B+ is an unsupported technical preview.</span></span> <span data-ttu-id="c7397-123">유효성 검사 및 활성화가 제한적으로 완료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c7397-123">Limited validation and enablement has been completed.</span></span> <span data-ttu-id="c7397-124">보다 나은 평가 환경은 물론, 상용 제품을 위해 Raspberry Pi 3B 또는 Intel, Qualcomm 또는 NXP SoC가 지원되는 기타 디바이스를 사용해 주세요.</span><span class="sxs-lookup"><span data-stu-id="c7397-124">For a better evaluation experience and for any commercial products, please use the Raspberry Pi 3B or other devices with supported Intel, Qualcomm, or NXP SoCs.</span></span> <span data-ttu-id="c7397-125">Raspberry Pi 3B+ 관련 문제 해결의 경우 문제 해결 가이드([여기](https://docs.microsoft.com/en-us/windows/iot-core/troubleshooting?branch=master#raspberry-pi-3b-booting-issues))를 참조해 주세요.</span><span class="sxs-lookup"><span data-stu-id="c7397-125">For troubleshooting issues with the Raspberry Pi 3B+, please see our Troubleshooting Guide, [here](https://docs.microsoft.com/en-us/windows/iot-core/troubleshooting?branch=master#raspberry-pi-3b-booting-issues).</span></span> 

<span data-ttu-id="c7397-126">Raspberry Pi 3 모델 B+는 Raspberry Pi 3 제품군에서 최신 제품으로서, 1.4GHz에서 실행하는 64비트 쿼드 코어 프로세서, 듀얼 밴드 2.4GHz 및 5GHz 무선 LAN, Bluetooth 4.2/BLE, 더 빨라진 이더넷은 물론, 별도의 PoE HA를 통한 PoE 기능을 자랑합니다.</span><span class="sxs-lookup"><span data-stu-id="c7397-126">The Raspberry Pi 3 Model B+ is the latest product in the Raspberry Pi 3 range, boasting a 64-bit quad core processor running at 1.4GHz, dual-band 2.4GHz and 5GHz wireless LAN, Bluetooth 4.2/BLE, faster Ethernet, and PoE capability via a separate PoE HA.</span></span>

<span data-ttu-id="c7397-127">최근 Windows 10 IoT Core에 관심이 있는 많은 고객이 Windows 10 IoT Core를 플래시한 후 디바이스는 제대로 부팅이 안되는데, Raspbian은 정상 작동하는 문제를 경험했습니다.</span><span class="sxs-lookup"><span data-stu-id="c7397-127">Recently, many customers who are interested in Windows 10 IoT Core encountered a problem where the device could not boot normally after flashing Windows 10 IoT Core, but the Raspbian works fine on it.</span></span> <span data-ttu-id="c7397-128">다음은 부팅 문제를 해결하는 방법에 대한 몇 가지 제안 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="c7397-128">The following are some suggestions on how to troubleshoot the boot problem.</span></span>

<span data-ttu-id="c7397-129">이 Insider Preview 이미지에 몇 가지 알려진 문제가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7397-129">There are some known issues in this Insider Preview image.</span></span> <span data-ttu-id="c7397-130">참고:</span><span class="sxs-lookup"><span data-stu-id="c7397-130">Please note that:</span></span>
* <span data-ttu-id="c7397-131">이 이미지는 Raspberry Pi 3B+에만 해당하며 Raspbierry Pi 2에서는 부팅되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7397-131">This image is only meant for the Raspberry Pi 3B+ and will not boot on the Raspbierry Pi 2.</span></span>
* <span data-ttu-id="c7397-132">Visual Studio에서 배포하는 F5 드라이버는 Windows 10 IoT Core에서 작동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7397-132">F5 driver deployment from Visual Studio does not work on Windows 10 IoT Core.</span></span>
* <span data-ttu-id="c7397-133">온보드 Wi-Fi 및 Bluetooth는 Raspberry Pi 3B+에서 작동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7397-133">Onboard Wi-Fi and Bluetooth do not work on the Raspberry Pi 3B+.</span></span>
* <span data-ttu-id="c7397-134">Ft5406 터치 스크린 드라이버를 Raspberry Pi 3B+에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c7397-134">Ft5406 touch screen driver is disabled on the Raspberry Pi 3B+.</span></span>
* <span data-ttu-id="c7397-135">SD 카드 활동 LED를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c7397-135">SD card activity LED is disabled.</span></span>

<span data-ttu-id="c7397-136">Windows 10 IoT Core에 사용할 SD 카드를 선택할 때 단 두 가지 요구 사항이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7397-136">There are only two requirements when choosing which SD cards to use with Windows 10 IoT Core.</span></span> <span data-ttu-id="c7397-137">클래스 10 SD 카드를 사용하고 해당 카드에 충분한 공간(최소 8GB의 공간)이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7397-137">You need to use a class 10 SD card and make sure the card has enough space - at least 8 GB of space.</span></span> <span data-ttu-id="c7397-138">Microsoft에서 Windows 10 IoT Core와 호환되는 것으로 검증한 두 어 개의 SD 카드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7397-138">There are a couple of SD cards that have been verified by Microsoft to be compatible with Windows 10 IoT Core:</span></span>
* <span data-ttu-id="c7397-139">Samsung EVO 32 GB 클래스 10 마이크로 SDHC 카드</span><span class="sxs-lookup"><span data-stu-id="c7397-139">Samsung EVO 32 GB class 10 Micros SDHC card</span></span>
* <span data-ttu-id="c7397-140">SanDisk Ultra 마이크로 SDHC, 16GB 카드</span><span class="sxs-lookup"><span data-stu-id="c7397-140">SanDisk Ultra Micro SDHC, 16 GB card</span></span>

<span data-ttu-id="c7397-141">일반적으로 SD 카드가 위조 또는 손상되거나 훼손되지 않았는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7397-141">Generally, you need to check if the SD card is fake or if it is damaged or corrupt.</span></span> <span data-ttu-id="c7397-142">SD 카드는 정전 또는 부적절한 분리 등, 다양한 요인으로 인해 손상되기 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="c7397-142">The SD card is equally prone to corruption due to a variety of factors such as power shortage or improper removal.</span></span> <span data-ttu-id="c7397-143">메모리 카드가 손상되지 않도록 보호하는 것이 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="c7397-143">It is important to safeguard your memroy card from damage.</span></span>

<span data-ttu-id="c7397-144">이미지를 SD 카드로 플래시하기 위해 [Windows 10 IoT Core 대시보드](https://docs.microsoft.com/en-us/windows/iot-core/connect-your-device/iotdashboard)를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7397-144">To flash your image to a SD card, you can use the [Windows 10 IoT Core Dashboard](https://docs.microsoft.com/en-us/windows/iot-core/connect-your-device/iotdashboard).</span></span> <span data-ttu-id="c7397-145">OS 빌드 필드에서 “사용자 지정"을 선택한 후 플래시할 FFU 파일을 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7397-145">You will need to choose "Custom" in the OS Build field, then select the FFU file to flash.</span></span> 

<span data-ttu-id="c7397-146">디바이스에 하드웨어 오류가 있는지 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="c7397-146">Check to see if there are any hardware failure in the device.</span></span> <span data-ttu-id="c7397-147">Raspberry Pi 3B+ 보드에는 3B와 동일한 두 개의 LED가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7397-147">There are two LEDs on the Raspberry Pi 3B+ board, same as the 3B.</span></span> <span data-ttu-id="c7397-148">하나는 PWR용이고, 다른 하나는 ACT용입니다.</span><span class="sxs-lookup"><span data-stu-id="c7397-148">One is for PWR while another is for ACT.</span></span> <span data-ttu-id="c7397-149">ACT 표시등이 깜박이는 횟수로 보드의 부팅 여부를 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7397-149">The number of blinks the ACT light makes will determine whether or not your board is booting.</span></span> <span data-ttu-id="c7397-150">SD 카드 활동 LED는 Raspberry Pi 3B+가 부팅되는 일부 부분에서는 깜박이지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7397-150">The SD card activity LED will not flash during some portions of booting on the Raspberry Pi 3B+.</span></span>

<span data-ttu-id="c7397-151">디바이스가 부팅 중이고 대기 페이지를 표시하면 잠시 기다려 주세요.</span><span class="sxs-lookup"><span data-stu-id="c7397-151">When the device is booting and the device shows the waiting page, please wait patiently.</span></span> <span data-ttu-id="c7397-152">일반적으로 최대 1분이 걸립니다.</span><span class="sxs-lookup"><span data-stu-id="c7397-152">Generally, this will last up to a minute.</span></span> <span data-ttu-id="c7397-153">하지만 SD 카드 읽기-쓰기 속도로 인해 더 오래 걸리는 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7397-153">But sometimes, due to the SD card read-write speed, it may take longer.</span></span>

<span data-ttu-id="c7397-154">Windows 10 IoT Core에서 디바이스가 정상적으로 부팅되지 않을 경우 Linux OS(Raspbian 등)를 SD 카드로 플래시하여 해당 이슈가 하드웨어에서 발생하는 것인지 한정해 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7397-154">If the device can't boot normally with Windows 10 IoT Core, you can try to flash a Linux OS (such as Raspbian) to the SD card to narrow down whether the issue is caused by hardware.</span></span> 

<span data-ttu-id="c7397-155">"레인보우 화면"이 표시되면 3B+ 릴리스 버전([여기](https://www.microsoft.com/en-us/software-download/windowsiot))을 플래시했는지 확인해 주세요.</span><span class="sxs-lookup"><span data-stu-id="c7397-155">If you find that you're getting a "rainbow screen", please check to make sure that you flashed the 3B+ release version, available [here](https://www.microsoft.com/en-us/software-download/windowsiot).</span></span> <span data-ttu-id="c7397-156">커뮤니티에서 제출한 3B+ 플래싱 자습서([여기](https://www.hackster.io/JiongShi/windows-10-iot-core-for-raspberry-pi-3-model-b-92b1a3))로 프로세스를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7397-156">You can verify your process with a community-submitted 3B+ flashing tutorial [here](https://www.hackster.io/JiongShi/windows-10-iot-core-for-raspberry-pi-3-model-b-92b1a3).</span></span>

## <a name="serial-port-communication-on-windows-10-iot-core-for-raspberry-pi"></a><span data-ttu-id="c7397-157">Raspberry Pi용 Windows 10 IoT Core의 직렬 포트 통신</span><span class="sxs-lookup"><span data-stu-id="c7397-157">Serial Port communication on Windows 10 IoT Core for Raspberry Pi</span></span> 

<span data-ttu-id="c7397-158">Raspberry Pi에서 하드웨어 UART 및 USB UART 어댑터 모두 직렬 통신이 지원되는 애플리케이션에 사용 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="c7397-158">On the Raspberry Pi, hardware UART and USB UART adapters both are usable for your application with serial communicaiton.</span></span> <span data-ttu-id="c7397-159">기본값으로 UART 전송 및 수신 핀은 GPIO 헤더의 8 및 10 핀입니다.</span><span class="sxs-lookup"><span data-stu-id="c7397-159">By default, the UART transmit and receive pins are pins 8 and 10 on teh GPIO header.</span></span>

![UART 및 USB UART 어댑터](media/Troubleshooting/adapters.png)

<span data-ttu-id="c7397-161">UART0을 초기화하고 읽기 후 쓰기를 수행하는 방법에 대해 자세히 알아보려면 [이 문서](https://docs.microsoft.com/en-us/windows/iot-core/learn-about-hardware/pinmappings/pinmappingsrpi#serial-uart)를 읽어 보세요.</span><span class="sxs-lookup"><span data-stu-id="c7397-161">You can read [this article](https://docs.microsoft.com/en-us/windows/iot-core/learn-about-hardware/pinmappings/pinmappingsrpi#serial-uart) to learn more about how to initialize UART0 and perform a write followed by a read.</span></span>

<span data-ttu-id="c7397-162">또한 RFCOMM(무선 주파수 통신)은 클래식 Bluetooth의 기본 직렬 통신입니다.</span><span class="sxs-lookup"><span data-stu-id="c7397-162">In addition, Radio Frequency Communication (RFCOMM) is the underlying serial communications for classic Bluetooth.</span></span> <span data-ttu-id="c7397-163">Bluetooth 직렬이 지원되는 IoT 디바이스를 통해 연결된 Windows 10 IoT Core에서 UWP 앱을 실행하는 방법을 알아 보려면 [이 GitHub 샘플](https://github.com/djaus2/iotbluetoothserial)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c7397-163">Refer to [this GitHub sample](https://github.com/djaus2/iotbluetoothserial) to learn about running UWP apps on Windows 10 IoT Core to connected over an IoT device with Bluetooth Serial.</span></span>

<span data-ttu-id="c7397-164">디바이스가 직렬 포트를 통한 데이터 읽기/쓰기를 수행할 수 없을 경우 아래 단계에 따라 문제를 해결하세요.</span><span class="sxs-lookup"><span data-stu-id="c7397-164">If you encounter that the device cannot read/write data through the serial port, follow the steps below to troubleshoot:</span></span>

1. <span data-ttu-id="c7397-165">점퍼로 TX-RX를 연결(아래 표시)한 다음, 샘플 코드를 사용하여 해당 앱이 데이터 읽기/쓰기를 수행할 수 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="c7397-165">Connect the TX to RX with Jumper - shown below - then run the sample code to check if the app can read/write data.</span></span> <span data-ttu-id="c7397-166">작동하지 않는 경우 보드의 IC가 손상될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7397-166">If this does not work, the IC on the board may be broken.</span></span>

![Raspberry Pi의 TX-RX](media/Troubleshooting/txrx.png)

2. <span data-ttu-id="c7397-168">전송 속도, 핸드셰이킹 및 정지 비트가 올바르게 구성되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="c7397-168">Make sure the BaudRate, Handshaking and StopBits are configured correctly.</span></span> <span data-ttu-id="c7397-169">테스트할 직렬 포트에 RS232 인터페이스(예: DB9)가 온전히 있는 경우 일반적인 핸드셰이킹 크로스오버로 연결된 RxTx 크로스오버 와이어를 사용하여 DB 플러그를 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="c7397-169">If the serial port to be tested has a complete RS232 interface (e.g. DB9), use a DB plug with the RxTx crossover wires connected with the typical handshaking crossovers.</span></span> <span data-ttu-id="c7397-170">일부 RS232 포트(또는 USB 어댑터)는 제대로 작동하려면 DCD(Carrier Detect) 및 DSR(DCE Ready) 등의 신호를 어설션해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7397-170">Some RS232 ports (or USB adapters) require signals such as Carrier Detect (DCD) and DCE Ready (DSR) to be asserted before they function properly.</span></span>

3. <span data-ttu-id="c7397-171">Windows 10 IoT Core에서 USB UART 어댑터를 사용하려는 경우 다음이 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7397-171">If you want to use USB UART adapters on Windows 10 IoT Core, the following are supported:</span></span>

* <span data-ttu-id="c7397-172">CP2102 USB 2.0</span><span class="sxs-lookup"><span data-stu-id="c7397-172">CP2102 USB 2.0</span></span>
* <span data-ttu-id="c7397-173">TTL 모듈 직렬 변환기</span><span class="sxs-lookup"><span data-stu-id="c7397-173">TTL Module Serial Converter</span></span>
* <span data-ttu-id="c7397-174">FTDI</span><span class="sxs-lookup"><span data-stu-id="c7397-174">FTDI</span></span>
* <span data-ttu-id="c7397-175">Generic usbser.sys</span><span class="sxs-lookup"><span data-stu-id="c7397-175">Generic usbser.sys</span></span>

<span data-ttu-id="c7397-176">또한 devcon.exe 스택 \* 및 devcon.exe 상태\* cmdlet을 사용하여 Windows 10 IoT Core의 예상 드라이버 스택 및 드라이버 상태를 확인할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7397-176">You can also use the devcon.exe stack \* and devcon.exe status\* cmdlet to check the expected drivers stack and drivers status on Windows 10 IoT Core.</span></span>

```
USB\VID_10C4&PID_EA60\0001
    Name: Silicon Labs CP210x USB to UART Bridge
    Setup Class: {4d36e978-e325-11ce-bfc1-08002be10318} Ports
    Controlling service:
        silabser
```
<span data-ttu-id="c7397-177">[Mincomm](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/BusTools/MinComm)은 직렬 포트 문제를 해결할 수 있는 또 하나의 유용한 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="c7397-177">[Mincomm](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/BusTools/MinComm) is another helpful tool to troubleshoot serial port issues.</span></span> <span data-ttu-id="c7397-178">이 도구는 포트를 열거하고 식별 이름과 디바이스 ID를 지정하고 포트를 개방하며 설정을 구성(예: 전속 속도, 정지 비트 등)하고 데이터를 전송 및 수신할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7397-178">This tool can enumerate ports, give you their friendly name and Device ID, open ports, configure settings (i.e. baud rate, stop bits, etc.) and send and receive data.</span></span> 

## <a name="sirep-test-service"></a><span data-ttu-id="c7397-179">Sirep 테스트 서비스</span><span class="sxs-lookup"><span data-stu-id="c7397-179">Sirep Test service</span></span>
<span data-ttu-id="c7397-180">Sirep 테스트 서비스가 리테일 이미지에서 기본값으로 활성화되어 있지 않더라도, 시작 시 Sirep 서비스를 비활성화하길 원한다면 로그인하여 Sirep이 자동 시작되지 않도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7397-180">Even though the Sirep Test service is not enabled by default in retail images, in case you still want to disable the Sirep service on startup, you can login and disable Sirep from autostart.</span></span> 

<span data-ttu-id="c7397-181">비활성화하려면 다음 PowerShell 명령을 사용하세요(아래 그림 참조).</span><span class="sxs-lookup"><span data-stu-id="c7397-181">You can use the following PowerShell commands to do so, as shown below:</span></span>

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

## <a name="tablet-mode"></a><span data-ttu-id="c7397-182">태블릿 모드</span><span class="sxs-lookup"><span data-stu-id="c7397-182">Tablet mode</span></span>

<span data-ttu-id="c7397-183">"태블릿 모드”는 데스크톱 셸에만 존재하는 개념으로, IoT Core에는 해당되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7397-183">"Tablet Mode" is a concept that only exist on Desktop shell and doesn’t apply to IoT Core.</span></span> 

<span data-ttu-id="c7397-184">디바이스에 지원되는 하드웨어(I2C 또는 USB HID 터치를 통해)가 있는 경우 터치는 인박스 클래스 드라이버를 사용하여 자동으로 작동해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7397-184">If the device have supported hardware (either through I2C or USB HID touch), touch should function automatically using the inbox class drivers.</span></span> <span data-ttu-id="c7397-185">자세한 내용은 [여기](https://docs.microsoft.com/en-us/windows-hardware/design/component-guidelines/touchscreen-device-bus-connectivity)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c7397-185">You can read more about this [here](https://docs.microsoft.com/en-us/windows-hardware/design/component-guidelines/touchscreen-device-bus-connectivity).</span></span>


## <a name="yubikey-support"></a><span data-ttu-id="c7397-186">Yubikey 지원</span><span class="sxs-lookup"><span data-stu-id="c7397-186">Yubikey support</span></span>

<span data-ttu-id="c7397-187">Windows 10 IoT Core에는 스마트 카드 지원이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c7397-187">Windows 10 IoT Core does not have smart card support.</span></span> <span data-ttu-id="c7397-188">그러나 스마트 카드는 PIN, 그리고 Yubikey의 경우 누르는 버튼으로 보호되어 있으므로 일반적으로 사용자 ID가 아닌 디바이스 ID에 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c7397-188">However, smart cards are usually devices used for user identity and not device identity because they are secured with PINs and, in the case of the Yubikey, a button to press.</span></span> <span data-ttu-id="c7397-189">따라서 IoT 디바이스와 조화를 이루지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7397-189">This does not harmonize with an IoT device.</span></span> <span data-ttu-id="c7397-190">대안을 찾고 있다면 디바이스의 TPM 2.0이 Yubikey 또는 스마트 카드보다 나을 것입니다.</span><span class="sxs-lookup"><span data-stu-id="c7397-190">If you're looking for an alternative, a TPM 2.0 on the device may serve better than a Yubikey or smart card.</span></span> <span data-ttu-id="c7397-191">Microsoft는 TPM 인증서를 빠짐없이 지원합니다. TPM을 이용하면 사용자 인증서나 Azure IoT 액세스 자격 증명(Limpet)뿐만 아니라 디바이스도 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7397-191">We have full certificate support for TPMs and they are meant to store devices as well as user certificates and Azure IoT access credentials (Limpets).</span></span>
