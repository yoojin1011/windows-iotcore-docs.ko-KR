---
author: saraclay
Description: 다른 개발 관련 문제를 해결 합니다.
title: 문제 해결
ms.author: saclayt
ms.date: 08/28/18
ms.topic: article
ms.openlocfilehash: 8b93ad987c27e1123d68c4d22148447ccc99e37d
ms.sourcegitcommit: 2e7e9555fe71ca60b5f41dbf06051a50520a368a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66491705"
---
# <a name="troubleshooting"></a>문제 해결
사람들이에서 일반적인 문제를 포함 하는 문서입니다. 특정 항목을 찾으려면 단어 또는 문구 검색 하려면 Ctrl + F를 사용 합니다. 예정인 추가 하 시겠습니까? 이 설명서 또는 아래 provident 콘텐츠 사용자 의견에 대 한 PR을 만듭니다.

> [!TIP]
> 제조와 관련 된 문제 문제 해결을 위해 읽어보세요 합니다 [문제 해결 문서](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/troubleshooting) 있는 제조 지침.

## <a name="asus-tinkerboard-and-rockchip-support"></a>ASU Tinkerboard 및 Rockchip 지원

ASU Tinkerboard 및 Rockchip 우리 공식적으로 지원 되지 않으며는 Rockchip SoC Windows 10 IoT Core 작업을 가져올 다른 제 3 자에 협력 하는 경우가 있습니다.

## <a name="issue-when-connecting-a-mbm-device-when-roaming"></a>로밍 시 MBM 장치를 연결 하는 문제

두 가지 방법으로 로밍 사용 하도록 설정할 때 고려해 야 할 수 있습니다.

1. profile.xml 로밍 구성 및 셀룰러 네트워크에 대 한 연결을 자동으로 설정 하 고 동작을 설정 합니다.
설정 로밍 프로필을 참조 하세요 [이 문서에서는](https://docs.microsoft.com/windows/desktop/mbn/schema-root)합니다.

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

자동 연결에 대 한 프로필을 설정 하려면 "auto"를 선택 합니다.

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

2. 다른 요소 인터페이스별 로밍 정책을 충족 해야 하는입니다. 기본적으로 해당 정책 ("홈 운송 업체만") FALSE로 설정 됩니다. 쿼리 및 명령줄을 통해 변경할 수 있습니다이 `netsh mbn get/set dataroamcontrol.`

예:

```
    netsh mbn show dataroamcontrol int=*
    netsh mbn set dataroamcontrol interface=Cellular profileset=all state=all
    netsh mbn set dataroamcontrol help
```

오류가 발생할 수 있습니다 **0x139f (ERROR_INVALID_STATE)** 경우에서 장치를 로밍 중일 때 데이터 로밍-로밍 정책에 따라 연결 요청에 대 한 오류 전송 wwansvc 합니다.

## <a name="raspberry-pi-3b-booting-issues"></a>Raspberry Pi 3B + 부팅 문제

> [!NOTE]
> Raspberry Pi 3B +이 릴리스에서 지원 되지 않는 기술 미리 보기를 합니다. 제한 된 유효성 검사 및 활성화가 완료 되었습니다. 더 나은 평가판 환경과 모든 상용 제품을 사용 하세요 Raspberry Pi 3B 또는 기타 장치 지원 되는 Intel, Qualcomm, 또는 NXP Soc를 사용 하 여 합니다. Raspberry Pi 3B +를 사용 하 여 문제를 해결, 문제 해결 가이드를 참조 하세요 [여기](https://docs.microsoft.com/en-us/windows/iot-core/troubleshooting?branch=master#raspberry-pi-3b-booting-issues)합니다. 

Raspberry Pi 3 모델 B +는 최신 제품 Raspberry Pi 3 범위의 1.4 GHz, 이중 밴드 2.4ghz 및 5ghz 무선 LAN, Bluetooth 4.2/BLE 빠르고 이더넷에서 실행 되는 64 비트 쿼드 코어 프로세서를 자랑 하 고는 별도 PoE HA를 통해 PoE 기능입니다.

최근 Windows 10 IoT Core 관심이 많은 고객이 여기서 깜박이 Windows 10 IoT Core 후 장치가 정상적으로 부팅 되지 않을 수 있지만 Raspbian에 정상적으로 문제가 발생 했습니다. 다음은 부팅 문제를 해결 하는 방법에 몇 가지 제안 합니다.

이 Insider Preview 이미지에서 몇 가지 알려진된 문제가 있습니다. note 하십시오.
* 이 이미지는 Raspberry Pi 3B + 기능만 및 Raspbierry Pi 2에서 부팅 되지 않습니다.
* Visual Studio에서 F5 드라이버 배포 Windows 10 IoT Core 작동 하지 않습니다.
* 온 보 딩 Wi-fi 및 Bluetooth Raspberry Pi 3B 이상에서 작동 하지 않습니다.
* Ft5406 터치 화면 드라이버는 Raspberry Pi 3B 이상에서 사용할 수 없습니다.
* SD 카드 활동 LED 비활성화 됩니다.

Windows 10 IoT Core 사용 하는 SD 카드를 선택할 때 두 가지 요구 사항이 있습니다. 클래스 10 SD 카드를 사용 하 여 카드에 충분 한 공간-최소 8GB의 공간이 있는지 확인 해야 합니다. Windows 10 IoT Core 호환 되도록 하기 위해 Microsoft에서 확인 된 SD 카드의 몇 가지 있습니다.
* Samsung EVO 32 GB 클래스 10 Micros SDHC 카드
* SanDisk Ultra 마이크로 SDHC, 16GB 카드

일반적으로 SD 카드가 위조 또는 손상 되거나 손상 될 경우를 확인 해야 합니다. SD 카드는 동일 하 게 발생 하기 쉬운 다양 한 전원 부족 또는 잘못 된 제거와 같은 요인으로 인해 손상입니다. 꺼냅니다 카드 손상 으로부터 보호 하는 것이 반드시 합니다.

SD 카드 이미지 flash를 사용할 수 있습니다 합니다 [Windows 10 IoT Core 대시보드](https://docs.microsoft.com/en-us/windows/iot-core/connect-your-device/iotdashboard)합니다. OS 빌드 필드에 "Custom"를 선택 하 고 플래시 FFU 파일을 선택 해야 합니다. 

장치에서 모든 하드웨어 오류가 있는지 확인 합니다. Raspberry Pi 3B + 보드에는 3B 동일 두 led가 있습니다. 한 동안 다른 스냅숏이 ACT에 대 한 전원입니다. 밝은 하면 개수는 보드 부팅 되 고 있는지 여부를 결정 합니다. Raspberry Pi 3B 이상에서 부팅 중 일부는 동안 SD 카드 활동 LED 플래시 되지 않습니다.

장치가 부팅 되 고 대기 중인 페이지를 표시 하는 장치를 있으므로 편안 하 게 기다려 주세요. 일반적으로이 값은 1 분까지 지속 됩니다. 하지만 경우에 따라 SD 카드 읽기 / 쓰기 속도, 인해 걸릴 수 있습니다.

장치는 Windows 10 IoT Core 사용 하 여 정상적으로 부팅할 수 없습니다, 하는 경우 하드웨어에서 문제가 발생 하는지 여부를 줄이기 위해 SD 카드에 (예: Raspbian) Linux OS를 시도할 수 있습니다. 

"Rainbow 화면" 보시기를 찾았으면 3B + 릴리스, 사용 가능한 버전을 업데이트 하는 있는지 확인 하십시오 [여기](https://www.microsoft.com/en-us/software-download/windowsiot)합니다. 자습서를 깜박이 커뮤니티 제공 3B +를 사용 하 여 프로세스를 확인할 수 있습니다 [여기](https://www.hackster.io/JiongShi/windows-10-iot-core-for-raspberry-pi-3-model-b-92b1a3)합니다.

## <a name="serial-port-communication-on-windows-10-iot-core-for-raspberry-pi"></a>Raspberry Pi에 대 한 Windows 10 IoT Core 직렬 포트 통신 

Raspberry Pi에서 하드웨어 UART 및 USB UART 어댑터 모두 직렬 communicaiton 사용 하 여 응용 프로그램에 사용할 수 있습니다. 기본적으로 UART 전송 및 수신 하 여 pin은 pin 8 및 10 GPIO 헤더에 있습니다.

![UART 및 USB UART 어댑터](media/Troubleshooting/adapters.png)

읽어보세요 [이 문서에서는](https://docs.microsoft.com/en-us/windows/iot-core/learn-about-hardware/pinmappings/pinmappingsrpi#serial-uart) UART0를 초기화 하 고 읽기 뒤 쓰기를 수행 하는 방법에 자세히 알아보려면 합니다.

또한 무선 주파수 통신 (RFCOMM)는 클래식 Bluetooth에 대 한 기본 직렬 통신 합니다. 가리킵니다 [이 GitHub 샘플](https://github.com/djaus2/iotbluetoothserial) Bluetooth 일련 번호를 가진 IoT 장치를 통해 연결 된 Windows 10 IoT Core UWP 앱 실행에 대해 자세히 알아보려면 합니다.

장치 수 없습니다. 읽기/쓰기 직렬 포트를 통해 데이터에서 발견 되 면 문제를 해결 하려면 다음 단계를 수행 합니다.

1. 점퍼-아래-를 사용 하 여 RX에는 TX를 연결한 경우 앱 수 읽기/쓰기 데이터를 확인 하는 샘플 코드를 실행 합니다. 작동 하지 않는 경우 보드에서 IC 손상 될 수도 있습니다.

![Raspberry Pi에서 RX에는 텍사스](media/Troubleshooting/txrx.png)

2. BaudRate, 핸드셰이킹 및 StopBits 올바르게 구성 되어 있는지 확인 합니다. 테스트할 직렬 포트에 RS232 인터페이스 (예: DB9)를 완료 하는 경우 일반적인 핸드셰이킹 crossovers 연결할 RxTx 교차 와이어를 사용 하 여 DB 플러그를 사용 합니다. 일부 RS232 포트 (또는 USB 어댑터)를 제대로 작동 하려면 먼저 평가할 운송 업체 DCD 및 DCE 준비 (DSR)와 같은 신호 필요 합니다.

3. Windows 10 IoT Core USB UART 어댑터를 사용 하려는 경우 다음 지원 됩니다.

* CP2102 USB 2.0
* TTL 모듈에 대 한 직렬 변환기
* FTDI
* 제네릭 usbser.sys

Devcon.exe 스택 이용할 수 있습니다 * 및 devcon.exe 상태 * cmdlet에 필요한 드라이버 스택 및 Windows 10 IoT Core 드라이버 상태를 확인 합니다.

```
USB\VID_10C4&PID_EA60\0001
    Name: Silicon Labs CP210x USB to UART Bridge
    Setup Class: {4d36e978-e325-11ce-bfc1-08002be10318} Ports
    Controlling service:
        silabser
```
[Mincomm](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/BusTools/MinComm) 는 직렬 포트 문제를 해결 하는 또 다른 유용한 도구입니다. 이 도구 수 포트 열거 장치 ID와 이름을 제공, 포트를 열어 구성 설정 (즉, 전송 속도, 비트의 정지 비트, 등) 및 데이터 전송 및 수신 합니다. 

## <a name="sirep-test-service"></a>Sirep 테스트 서비스
Sirep 테스트 서비스를 기본적으로 일반 정품 이미지에서 시작 시 Sirep를 사용 하지 않도록 설정 하려는 경우을 해제 하는 경우에에 로그인 하 고 자동 시작에서 Sirep를 사용 하지 않도록 설정할 수 있습니다. 

아래와 같이를 위해 다음 PowerShell 명령을 사용할 수 있습니다.

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

## <a name="tablet-mode"></a>태블릿 모드

"모드 tablet"는 데스크톱 셸 존재 하는 개념 및 IoT Core에 적용 되지 않습니다. 

장치 하드웨어 (두 통해 I2C 또는 USB HID touch) 지원 되는, 터치는 받은 편지함 클래스 드라이버를 사용 하 여 자동으로 작동 해야 합니다. 자세한 내용은이 대 한 [여기](https://docs.microsoft.com/en-us/windows-hardware/design/component-guidelines/touchscreen-device-bus-connectivity)합니다.


## <a name="yubikey-support"></a>Yubikey 지원

Windows 10 IoT Core는 스마트 카드 지원은 없습니다. 그러나 스마트 카드는 장치 Pin을 사용 하 여 고 Yubikey, 단추를 누를 경우 보안이 유지 되는 때문에 사용자 id 및 장치 id 아닌에 사용 되는 일반적으로입니다. 이 IoT 장치를 사용 하 여는 조화 하지 않습니다. 대안을 찾고 있는 경우 장치에는 TPM 2.0 보다 Yubikey 또는 스마트 카드를 제공할 수 있습니다. Tpm에 대 한 전체 인증서 지원을 장치 뿐만 아니라 사용자 인증서를 저장 하 고 Azure IoT 액세스 (Limpets) 자격 증명입니다.
