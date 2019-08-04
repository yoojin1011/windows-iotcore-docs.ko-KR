---
title: 하드웨어 호환성 목록
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Windows 10 IoT Core에서 가장 잘 지 원하는 주변 장치 인터페이스 및 프로토콜에 대해 알아봅니다.
keywords: windows iot, 주변 장치, 프로토콜, 호환성, 버스, 하드웨어
ms.openlocfilehash: d1d97c3bff2fe843216410d07530f4866136bc63
ms.sourcegitcommit: c5552007f5456e57512307f51b146406a23fa723
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/02/2019
ms.locfileid: "68739825"
---
# <a name="hardware-compatibility-list"></a>하드웨어 호환성 목록

Windows 10 IoT Core는 I2C, UART, USB 등과 같은 일반적인 버스에 대 한 지원을 포함 하 여 다양 한 주변 인터페이스와 프로토콜을 지원 합니다. 이 페이지는 알려진 지원 되는 주변 장치를 나열 하며 최신 RTM 릴리스의 최신 버전입니다. 특정 항목은 참가자 릴리스에 대해서만 작동할 수 있으며 이와 같이 표시 됩니다. GitHub에서이 목록에 참여 하는 것이 좋습니다.

> [!IMPORTANT]
> 이 목록은 완전 하지 않습니다. 이 페이지에는 Windows 10 IoT Core와 호환 되는 다른 여러 장치가 나열 되어 있지 않습니다. 표시 되지 않지만 Windows 10 IoT Core에서 이미 지원 되는 것을 포함 하는 클래스 호환 장치는 작동 합니다. 


지원 되는 하드웨어 플랫폼에 대 한 정보를 찾고 있나요? Windows와 호환 되는 개발 보드 목록을 보려면 [여기](https://docs.microsoft.com/windows/iot-core/learn-about-hardware/socsandcustomboards) 를 클릭 하세요.

## <a name="usb-devices"></a>USB 장치

### <a name="wifi-adapters"></a>WiFi 어댑터
> | 파트 이름/아니요입니다. | 호환 아키텍처 | 설명 | 관련 링크 | Microsoft 검증  | 
> |----------------|-------------------|-------------|---------------|------------------------------|
> | 공식 Raspberry Pi WiFi 동글을 | ARM32, x64, x86 | 공식 Raspberry Pi WiFi 동글을 diminutive 크기에 가장 적합 한 WiFi 성능을 제공 합니다. | | &#10004;  |
> | 어 링크 무선 N 150 미니 USB 어댑터 | x64, x86 | WAP 링크 101 AWL5077 골든 150Mbps 무선 미니 USB 어댑터와 WPA2, WPA 및 WEP 강화 무선 보안 | | &#10004;  
> | Panda PAU06 | x64, x86 |  Panda 300Mbps 무선 N USB 어댑터 및 고속 안테나 | |  &#10004;  
> | TP-링크 TL_WN725N |  ARM32, x64, x86 | TP-링크 TL-WN725N Wireless N Nano USB Adapter 150 Mbps`(USB/VID_0BDA&PID_8179)` |  | &#10004;  
> | NET-DYN USB WiFi 어댑터 | MBM | WiFi USB 어댑터 넷-DYN | |  &#10004;  
> | Realtek 8191 USB 무선 WiFi | ARM32, x64, x86 | Realtek 8191 300Mbps 802.11 n/g/b/USB 무선 WiFi LAN 네트워크 카드 어댑터 | | &#10004;  
> | Realtek 8192 USB 무선 WiFi | ARM32, x64, x86 | USB 2.0 인터페이스를 사용 하는 Realtek 단일 칩 IEEE 802.11 b/g/n 2T2R WLAN 컨트롤러 | | &#10004; |
> | Realtek 8188EU USB 무선 WiFi | ARM32, Mx64, x86BM | Realtek RTL8188EU 무선 LAN 802.11 n/g/b USB 2.0 네트워크 어댑터 | | &#10004; |
> | Realtek 8192EU USB 무선 WiFi | ARM32, x64, x86 | Realtek RTL8192EU 무선 LAN 802.11 n/g/b USB 2.0 네트워크 어댑터 | | &#10004; |
> | CanaKit USB 무선 WiFi | x64, x86 | 칩셋 Ralink 5370 | | &#10004;
> | D-Link DWA-172 | ARM32 | 무선 AC600 듀얼 대역 고속 USB 어댑터 | [데이터 시트](ftp://ftp.dlink.de/dwa/dwa-172/documentation/DWA-172_ds_en_Datasheet.pdf) |

### <a name="ethernet-adapters"></a>이더넷 어댑터
> | 파트 이름/아니요입니다. | 호환 아키텍처 | 설명 | 관련 링크 | Microsoft 검증  | 
> |----------------|-------------------|-------------|---------------|------------------------------|
> | ASIX AX88772 USB 2.0 고속 이더넷 어댑터 | ARM32, x64, x86 | 이는 패킷 버퍼링을 위해 포함 된 28KB SRAM 포함 된 고성능 및 높은 통합이 있습니다입니다.  | | &#10004;  |


### <a name="bluetooth-dongles"></a>Bluetooth 동글
> | 파트 이름/아니요입니다. | 호환 아키텍처 | 설명 | 관련 링크 | Microsoft 검증  | 
> |----------------|-------------------|-------------|--------|------------------------------|
> | CSR 미니 USB Bluetooth V 4.0 어댑터 | ARM32, x64, x86 | 클래스 2 Bluetooth 4.0 스마트 준비 어댑터, 낮은 에너지, 이중 전원 |  | &#10004; 
> | ORICO BTA-403 미니 Bluetooth 4.0 USB 동글 | ARM32, x64, x86 | 저 에너지 Bluetooth 4.0 어댑터 USB 마이크로 어댑터 동글 |  | &#10004; 
> | CSR 미니 USB Bluetooth V 4.0 어댑터 | x64, x86 | 클래스 2 Bluetooth 4.0 스마트 준비 어댑터, 낮은 에너지, 이중 전원 |  | &#10004;|

### <a name="cameras"></a>카메라
> | 파트 이름/아니요입니다. | 호환 아키텍처 | 설명 | 관련 링크 | Microsoft 검증  | 
> |----------------|-------------------|-------------|--------|------------------------------|
> | Microsoft Lifecam 3000 USB 카메라 | ARM32, x64, x86 | USB 웹캠 | [Home Security 카메라 프로젝트](https://developer.microsoft.com/en-us/windows/iot/samples/webcamapp)|&#10004;|
> | Microsoft Lifecam HD-5000 | ARM32, x64, x86 | Microsoft LifeCam HD-5000 720p HD 웹캠 | | &#10004; |
> | Microsoft® LifeCam Studio™ | ARM32 | Microsoft® LifeCam Studio™ (모델: 1425) 1080p HD 웹캠 | | |
> | Logitech 웹캠 C210 | ARM32, x64, x86 | USB 웹캠, 1.3 mp 사진 |  |&#10004; |

### <a name="audio"></a>오디오
> | 파트 이름/아니요입니다. | 호환 아키텍처 | 설명 | 관련 링크 | Microsoft 검증 |
> |----------------|-------------------|-------------|--------|------------------------------|
> | Sabrent USB 외부 스테레오 사운드 어댑터, 모델 AU-EMAC1 | ARM32, x64, x86 | USB를 3.5 mm 오디오 및 마이크 신호로 변환 합니다. | | &#10004; 

### <a name="miscellaneous"></a>기타
> | 파트 이름/아니요입니다. | 호환 아키텍처 | 설명 | 관련 링크 | Microsoft 검증  | 
> |----------------|-------------------|-------------|--------|------------------------------|
> | Aeon Labs Z-웨이브 Z-스틱 시리즈 2 USB 동글 DSA02203-ZWUS | ARM32 | 시리즈 2 Z-웨이브 USB Z 스틱 컨트롤러 |  | &#10004; |
> | [Chalkboard 전자식 7 "LCD 용량 터치 스크린 표시](https://www.chalk-elec.com/?page_id=1280#!/7-black-frame-universal-HDMI-LCD-with-capacitive-multi-touch/p/21750201/category=3094861) | ARM32 | | [펌웨어 업데이트](https://www.chalk-elec.com/?p=1826) | &#10004; |
> | Vodafone (Huawei) K5150 | ARM32, x64, x86 | Vodafone (Huawei) K5150 150Mbps 4G LTE FDD USB 모바일 광대역 모뎀 |  | &#10004;  |
> | Vodafone (Huawei) K5160 | ARM32, x64, x86 | Vodafone (Huawei) K5160 150Mbps GSM/EDGE/3G/HSPA +/LTE-CAT4 USB 모바일 광대역 모뎀 |  | |
> | 시에라리온 무선 빔 (AirCard 340U) | x64, x86 |    시에라리온 무선 빔 (AirCard 340U) 4G LTE USB 모바일 광대역 모뎀 |  |&#10004; |
> | Microsoft Xbox 360 컨트롤러 | ARM32 | Microsoft의 Xbox 360에 대 한 HID 규격 USB 게임 패드 | [로봇 키트](https://microsoft.hackster.io/en-US/windowsiot/robot-kit-6dd474) |  &#10004; |
> | [MyTeletouch](http://www.myteletouch.com/) | ARM, x32 | HID 규격 USB 무선 마우스, 키보드 및 게임 패드 |  | &#10004; |

## <a name="other-hardware-peripherals"></a>기타 하드웨어 주변 장치

### <a name="nfcrfidproximity"></a>NFC/RFID/근접
> | 파트 이름/아니요입니다. | 호환 아키텍처 | 설명 | 관련 링크 | Microsoft 검증 |
> |----------------|-------------------|-------------|--------|------------------------------|
> | NXP OM5577 demo 보드 | ARM32 | NXP PN7120 NFC 칩 용 데모 보드입니다. | [ProximityDevice 설명서](https://docs.microsoft.com/uwp/api/Windows.Networking.Proximity.ProximityDevice) | &#10004; |
> | NXP PN547/PN548/PN7120 | ARM32, x64, x86 | NXP NFC 칩이 지원 됩니다. | | &#10004; |

### <a name="pi-hats"></a>Pi 모자
> | 파트 이름/아니요입니다. | 호환 아키텍처 | 설명 | 관련 링크 | Microsoft 검증  | 
> |----------------|-------------------|-------------|--------|------------------------------|
> | [Adafit 16-채널 PWM)](https://www.adafruit.com/product/2327#description-anchor) | ARM32 | 추가 Raspberry Pi 처리 오버 헤드 없이 최대 16 개의 서보를 제어 하는 기능을 추가 합니다. PWM)를 수행할 수 있는 최대 1.6 KHz는 12 비트 전체 자릿수입니다. | [Adafruit 자습서 C# IoT 샘플](https://github.com/golaat/Adafruit.Pwm) | |
> | [Dexter 산업 GrovePi](https://www.dexterindustries.com/shop/grovepi-board/) | ARM32 | Soldering 없이 수백 개의 다른 센서를 연결 하 여 생활에서 장치를 모니터링 하 고 제어 하 고 자동화 하는 데 프로그래밍할 수 있습니다. | [GrovePi 샘플](https://github.com/DexterInd/GrovePi/) | |
> | Dexter 산업 GoPiGo | ARM, x32 | GoPiGo는 Pi를 완전히 작동 하는 로봇으로 전환 하는 Raspberry Pi에 대 한 매력적인 및 complete 로봇입니다. GoPiGo은 Dexter 업계에서 개발한 Raspberry Pi에 대 한 모바일 로보틱 플랫폼입니다. | [GoPiGo 샘플](https://github.com/DexterInd/GoPiGo/tree/master/Software/CSharp) | |
> | [Raspberry PI 용 SeeedStudio Grove Base Hat](https://www.seeedstudio.com/Grove-Base-Hat-for-Raspberry-Pi.html) |ARM| RPI에 대 한 Grove Base Hat는 Raspbery PI 플랫폼의 Seeedstudio Grove 시스템에 대 한 지원을 제공 합니다.| [라이브러리 및 샘플](https://github.com/KiwiBryn/GroveBaseHatWindows10IoTCore) | |
> | [SeeedStudio Grove Base Hat for Raspberry PI 0](https://www.seeedstudio.com/Grove-Base-Hat-for-Raspberry-Pi-Zero-p-3187.html) |ARM| RPI 0 용 Grove Base Hat는 Raspbery PI 플랫폼의 Seeedstudio Grove 시스템에 대 한 지원을 제공 합니다.| [라이브러리 및 샘플](https://github.com/KiwiBryn/GroveBaseHatWindows10IoTCore) | |

### <a name="semtech-sx127x-based-lora-pi-hatshttpswwwsemtechcomproductswireless-rflora-transceivers"></a>[Semtech SX127X based LoRa® Pi 모자](https://www.semtech.com/products/wireless-rf/lora-transceivers)
Semtech 's LoRa® 매우 긴 범위 (100M-10KM)의 분산 스펙트럼 통신 기술은 높은 간섭 면역을가지고 있으며, 배터리/e m p 장치를 기존 네트워크 인프라에 연결 하기 위한 저렴 한 솔루션을 제공 합니다.

> | 파트 이름/아니요입니다. | 호환 아키텍처 | 설명 | 관련 링크 | Microsoft 검증  | 
> |----------------|-------------------|-------------|--------|------------------------------|
> | [Adafruit LoRa 라디오 Bonnet 433MHz](https://www.adafruit.com/product/4075) | ARM32 | 433MHz LoRa connectivity, 3 개의 단추 및 OLED 디스플레이입니다. | [라이브러리 및 샘플](https://github.com/KiwiBryn/RFM9XLoRa-Net) | |
> | [Adafruit LoRa 라디오 Bonnet 868/915MHz](https://www.adafruit.com/product/4074) | ARM32 | 868/915MHz LoRa 연결, 3 개의 단추 및 OLED 디스플레이입니다. | [라이브러리 및 샘플](https://github.com/KiwiBryn/RFM9XLoRa-Net) | |
> | [Dragino LoRa GPS Hat for RaspberryPI 433/868/915MHz](http://www.dragino.com/products/lora/item/106-lora-gps-hat.html) | ARM32 | 433/868/915MHz LoRa 연결 옵션 및 GPS. | [라이브러리 및 샘플](https://github.com/KiwiBryn/RFM9XLoRa-Net) | |
> | [RPI 915MHz 용 elecrow LoRa RFM95 IoT 보드](https://www.elecrow.com/lora-rfm95-iot-board-for-rpi.html) | ARM32 | 915MHz LoRa 연결 및 Grove 소켓입니다. | [라이브러리 및 샘플](https://github.com/KiwiBryn/RFM9XLoRa-Net) | |
> | [Raspberry Pi 0 및 PI3에 대 한 Electronic 트릭 Lora/LoraWan 방패](https://www.tindie.com/products/electronictrik/loralorawan-shield-for-raspberry-pi-zero-and-pi3/) | ARM32 | 868/915MHz LoRa 연결 및 선택적 OLED 디스플레이입니다. | [라이브러리 및 샘플](https://github.com/KiwiBryn/RFM9XLoRa-Net) | |
> | [M2M 1 Channel LoRaWan Gateway 방패 for Raspberry Pi](https://www.tindie.com/products/m2m/1-channel-lorawan-gateway-shield-for-raspberry-pi/) | ARM32 | 868/915/923MHz LoRa 연결 옵션입니다. | [라이브러리 및 샘플](https://github.com/KiwiBryn/RFM9XLoRa-Net) | |
> | [uputronics Raspberry Pi + LoRa (TM) 확장 보드](https://store.uputronics.com/index.php?route=product/product&path=61&product_id=68) | ARM32 | 433/868/915MHz LoRa 연결 옵션입니다. | [라이브러리 및 샘플](https://github.com/KiwiBryn/RFM9XLoRa-Net) | |
> | [uputronics Raspberry PiZero LoRa (TM) 확장 보드](https://store.uputronics.com/index.php?route=product/product&path=61&product_id=99) | ARM32 | 이중 433/868/915MHz LoRa 연결 옵션입니다. | [라이브러리 및 샘플](https://github.com/KiwiBryn/RFM9XLoRa-Net) | |


### <a name="nordic-semiconductor-nrf24l01-wireless-pi-hatshttpswwwnordicsemicomproductslow-power-short-range-wirelessnrf24-series"></a>[북유럽어 반도체 nRF24L01 무선 Pi 모자](https://www.nordicsemi.com/Products/Low-power-short-range-wireless/nRF24-series)
전 세계 2.5 GHz ISM 대역, 250Kbps, 1Mbps 및 2Mbps 데이터 요금. 낮은 파워 모듈 10의 미터 범위, 높은 전원 모듈 1KM

> | 파트 이름/아니요입니다. | 호환 아키텍처 | 설명 | 관련 링크 | Microsoft 검증  | 
> |----------------|-------------------|-------------|--------|------------------------------|
> | [Ceech Raspberry Pi nRF24l01 + 방패](https://www.tindie.com/products/ceech/new-raspberry-pi-to-nrf24l01-shield/) |ARM| Raspberry Pi에 대 한 Raspberry Pi NRF24l01 + 방패 추가 기능에서는 단일 NRF24l01 + 모듈과 버저 및 프로토타입 영역을 지원 합니다.| [라이브러리](https://github.com/techfooninja/Radios.RF24), [샘플 응용 프로그램](https://github.com/KiwiBryn/nRF24L01Windows10IoTCoreDuinoDemo), [필요한 수정](https://blog.devmobile.co.nz/2017/07/31/nrf24-windows-10-iot-core-hardware/) | |
> | [Boros Rf2-이중 nRF24L01 pHat](https://www.tindie.com/products/boros/borosrf2-dual-nrf24l01-phathat-rtc-for-pis/) |ARM| Boros RF2는 최대 2 개의 NRF24L01 + 라디오 및 선택적 RTC를 지원 합니다.| [라이브러리](https://github.com/techfooninja/Radios.RF24), [샘플 응용 프로그램](https://github.com/KiwiBryn/nRF24L01Windows10IoTCoreDuinoDemo) | |


### <a name="port-expanders"></a>포트 확장 기가
> | 파트 이름/아니요입니다. | 호환 아키텍처 | 설명 | 관련 링크 | Microsoft 검증  | 
> |----------------|-------------------|-------------|--------|------------------------------|
> | MCP23008 8 비트 i/o 포트 확장기 | ARM32, x64, x86 | I2C 인터페이스 칩, GPIO 포트 확장기. 8 개 포트, 18-PDIP 패키지 | [SPI 포트 Explander 샘플](https://www.hackster.io/4803/i2c-port-expander-sample-0a6d4f) | &#10004; |
> | MCP23S17 16 비트 i/o 포트 확장기 | ARM32, x64, x86 | I2C 인터페이스 칩, GPIO 포트 확장기. 16 개 포트, 28-SPDIP 패키지 | [대화형 피아노 샘플](https://www.hackster.io/windowsiot/build-2014-piano-3b449c) | &#10004; |

### <a name="storage-media"></a>저장소 미디어
> | 파트 이름/아니요입니다. | 호환 아키텍처 | 설명 | 관련 링크 | Microsoft 검증  | 
> |----------------|-------------------|-------------|--------|------------------------------|
> | [Samsung 32GB EVO 클래스 10 마이크로 SDHC](https://www.amazon.com/gp/product/B00IVPU786) | AARM32, x64, x86 | Windows 10 IoT Core를 사용할 수 있는 장치에 권장 되는 SD 카드입니다. | | &#10004;|
> | [SanDisk Ultra 마이크로 SDHC 16GB](https://www.amazon.com/SanDisk-Ultra-Micro-SDHC-16GB/dp/9966573445) | ARM32, x64, x86 | Windows 10 IoT Core를 사용할 수 있는 장치에 권장 되는 SD 카드입니다. | | &#10004; |

### <a name="sensors"></a>센서
> | 파트 이름/아니요입니다. | 호환 아키텍처 | 설명 | 관련 링크 | Microsoft 검증  | 
> |----------------|-------------------|-------------|--------|------------------------------|
> | DHT11 기본 온도-습도 센서 | ARM32, x64, x86 | 기본, 매우 저렴 한 디지털 온도 및 습도 센서입니다. 이는 용량 습도 센서 및 thermistor를 사용 하 여 주변의 공기를 측정 하 고, 데이터 핀에서 디지털 신호를 산출 합니다 (아날로그 입력 핀 필요 없음).  | [GpioOneWireSample (DHT11)](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/GpioOneWire)| &#10004; |
> | DHT22 온도-습도 센서 | ARM32, x64, x86 | 기본, 매우 저렴 한 디지털 온도 및 습도 센서입니다. 이는 용량 습도 센서 및 thermistor를 사용 하 여 주변의 공기를 측정 하 고, 데이터 핀에서 디지털 신호를 산출 합니다 (아날로그 입력 핀 필요 없음).  | [GpioOneWireSample (DHT11)](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/GpioOneWire) | &#10004; |
> | SparkFun 삼중 축가 속도계 ADXL345 | ARM32, x64, x86 | 최대 ± 16 g에서 고해상도 (13 비트)를 사용 하는 소형, 씬, 낮은 전력, 3 축 MEMS가 속도계. 디지털 출력 데이터는 16 비트 2의 보수 형식으로 지정 되며 SPI (3 또는 4 선) 또는 I2C 디지털 인터페이스를 통해 액세스할 수 있습니다. |[가 속도계 샘플](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/Accelerometer) | &#10004; |
> | AdafBMP280 온도 및 바 Ometric 센서 | ARM32 | 온도, 바 ometric 압력으로 Bosch 환경적 센서 | |   &#10004; |
> | [AdafTCS34725 Color 센서](http://www.adafruit.com/products/1334) | ARM, x32 | IR 필터 및 흰색 LED를 사용 하는 RGB 색 센서-TCS34725 | | &#10004; |
> | Rohm BH1750FVI 주변 광원 센서 | ARM32 | 주변 조명 측정에 대 한 소형 I2C 센서 | [I2C 샘플](https://github.com/mickut/Win10-IoT-Sensors) | |
> | Bosch BMP180 온도 및 바 ometric 센서 | ARM, x32 | Bosch 환경 센서 tempreature, 바 ometric 압력 | [I2C 샘플](https://github.com/mickut/Win10-IoT-Sensors) | |
> | Dorji DSTH01 상대 습도 센서 | ARM32 | I2C 상대 습도 센서 | [I2C 샘플](https://github.com/mickut/Win10-IoT-Sensors)| |
> | Honeywell HMC5883L digital 3 축 나침반/지자기 센터 | ARM32 | 디지털 나침반 사용과 자기 필드 측정을 위한 작은 3 축 지자기 센터 | [I2C 샘플](https://github.com/mickut/Win10-IoT-Sensors) | |

### <a name="touchpanel-solutions"></a>Touchpanel 솔루션
> | 파트 이름/아니요입니다. | 호환 아키텍처 | 설명 | 관련 링크 | Microsoft 검증 | 
> |----------------|-------------------|-------------|--------|------------------------------|
> | Keith & Koep i-PAN M7 CoverLens | ARM32 | 7.0 인치 Touchpanel 컴퓨터 및 Qualcomm Snapdragon 410E CPU, 해결 방법, 밝기 850cd/qm, USB 2.0, SD 카드, POE와 함께 사용 | [M7 정보를 이동 합니다.](https://keith-koep.com/en/products/products-hmi/i-pan-m7-coverlens-arm-touch-panel-computer-technical-data/) | &#10004; |


### <a name="miscellaneous"></a>기타
> | 파트 이름/아니요입니다. | 호환 아키텍처 | 설명 | 관련 링크 | Microsoft 검증 | 
> |----------------|-------------------|-------------|--------|------------------------------|
> | 공식 Pi 표시 | ARM32 | 7 "800x480 touch 디스플레이. | [Raspberry Pi 7 "터치 스크린](https://www.raspberrypi.org/products/raspberry-pi-touch-display/) | &#10004; |
> | 단색 1.3 "128x64 OLED 그래픽 표시 |ARM, x32, x64, x86 | 1.3 "대각선, 고대비 B/W를 표시 합니다. 128x64 개별 흰색 OLED 픽셀은 컨트롤러 칩에 의해 설정 되거나 해제 됩니다. | [SPI 표시 샘플](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/SPIDisplay) | &#10004; |
> | SN74HC595N Shift 등록 IC | ARM32, x64, x86 | IC 8 비트 시프트 레지스터 16 DIP | [Shift Register 샘플](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/ShiftRegister) | &#10004; |
> | 마이크로칩으로 기술 ADC MCP3002-I/P | AARM32, x64, x86 | MCP3002 10 비트 아날로그에서 디지털 컨버터로 변환 합니다. |  [Potentiometer 센서 샘플](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/PotentiometerSensor) | &#10004; |
> | 마이크로칩으로 기술 ADC MCP3208-CI/P | ARM32, x64, x86 | MCP3208 12bit 아날로그에서 디지털 컨버터로 변환 | [Potentiometer 센서 샘플](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/PotentiometerSensor) | &#10004; |
> | ADS1115 | ARM, x32, x64, x86 | 매우 작음, 저전력, 16 비트 ADC | [ADC 버스 공급자](https://github.com/ms-iot/BusProviders/tree/develop/ADC) | &#10004; |
> | CP2102 USB 2.0 to TTL 모듈 직렬 변환기 | ARM32, x64, x86 | CP2102 USB 2.0 to TTL 모듈 직렬 변환기 | [직렬 포트 샘플](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/SerialUART) | &#10004; |
> | PCA9685 | ARM32, x64, x86 | 16 채널, 12 비트 PWM) Fm + I2C 버스 LED 컨트롤러. | [PWM) Bus 공급자](https://github.com/ms-iot/BusProviders/tree/develop/PWM) | &#10004; |


