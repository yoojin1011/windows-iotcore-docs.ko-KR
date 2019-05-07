---
title: 하드웨어 호환성 목록
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 주변 인터페이스 및 Windows 10 IoT Core 모범 지 원하는 프로토콜에 알아봅니다.
keywords: windows iot, 주변 장치, 프로토콜, 호환성, 버스, 하드웨어
ms.openlocfilehash: 54ca0f706033a8a3eef0704534805d0d6b379083
ms.sourcegitcommit: 77caab0cfa47c74c66777c3cf5eeaa0ec9ac5784
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/01/2019
ms.locfileid: "64981938"
---
# <a name="hardware-compatibility-list"></a>하드웨어 호환성 목록

Windows 10 IoT Core 다양 한 주변 인터페이스 및 프로토콜, I2C, UART, USB, 등과 같은 일반적인 버스에 대 한 지원을 비롯 하 여 지원 합니다. 이 페이지는 알려진된 지원 되는 주변 장치를 나열 하 고 최신 RTM 버전을 기준으로 현재 합니다. 특정 항목 Insider 릴리스 에서만 작동할 수와 같이 표시 됩니다. GitHub에서이 목록에 기여 하는 것이 좋습니다.

> [!IMPORTANT]
> 이 목록은 완전 하지 않습니다. 많은 기타 주변 장치가이 페이지에 나열 되지 Windows 10 IoT Core 호환 되는 경우 나열 되지만 클래스-호환 이미 Windows 10 IoT Core 지원 되는 표시 되지 않는 장치인 경우 다음이 작동 합니다. 


지원 되는 하드웨어 플랫폼에 대 한 정보를 찾으시나요? 클릭 [여기](https://docs.microsoft.com/windows/iot-core/learn-about-hardware/socsandcustomboards) Windows 호환 개발 보드 목록에 대 한 합니다.

## <a name="usb-devices"></a>USB 장치

### <a name="wifi-adapters"></a>WiFi 어댑터
> | 이름 부 / 아니요 | 호환 아키텍처 | 설명 | 관련 링크 | Microsoft Verified  | 
> |----------------|-------------------|-------------|---------------|------------------------------|
> | 공식 Raspberry Pi WiFi 동글 | ARM32, x64, x86 | 공식 Raspberry Pi WiFi 동글을 diminutive 크기에 대 한 최상의 WiFi 성능을 제공합니다. | | &#10004;  |
> | Airlink 무선 N 150 미니 USB 어댑터 | x64, x86 | Airlink 101 Golden AWL5077 150Mbps 무선 미니 USB 어댑터와 WPA2 WPA, WEP 무선 보안 강화 | | &#10004;  
> | Panda PAU06 | x64, x86 |  높은 득점 안테나를 사용 하 여 panda 300Mbps 무선 N USB 어댑터 | |  &#10004;  
> | TP-LINK TL_WN725N |  ARM32, x64, x86 | TP 링크 TL WN725N 무선 N Nano USB 어댑터 150 Mbps `(USB/VID_0BDA&PID_8179)` |  | &#10004;  
> | NET DYN USB WiFi 어댑터 | MBM | WiFi USB 어댑터 NET-DYN | |  &#10004;  
> | Realtek 8191 USB 무선 WiFi | ARM32, x64, x86 | Realtek 8191 300Mbps 802.11n/g/b/ USB WiFi 무선 LAN 네트워크 카드 어댑터 | | &#10004;  
> | 8192 Realtek USB 무선 WiFi | ARM32, x64, x86 | Realtek 단일 칩 IEEE 802.11b/g/n USB 2.0 사용 하 여 2T2R WLAN 컨트롤러 인터페이스 | | &#10004; |
> | Realtek 8188EU USB 무선 WiFi | ARM32, Mx64, x86BM | Realtek RTL8188EU Wireless LAN 802.11n/g/b USB 2.0 Network Adapter | | &#10004; |
> | Realtek 8192EU USB 무선 WiFi | ARM32, x64, x86 | Realtek RTL8192EU 무선 LAN 802.11n/g/b USB 2.0 네트워크 어댑터 | | &#10004; |
> | CanaKit USB 무선 WiFi | x64, x86 | 칩셋 Ralink 5370 | | &#10004;
> | D-Link DWA-172 | ARM32 | 무선 AC600 이중 밴드 높은 향상 USB 어댑터 | [데이터 시트](ftp://ftp.dlink.de/dwa/dwa-172/documentation/DWA-172_ds_en_Datasheet.pdf) |

### <a name="ethernet-adapters"></a>이더넷 어댑터
> | 이름 부 / 아니요 | 호환 아키텍처 | 설명 | 관련 링크 | Microsoft Verified  | 
> |----------------|-------------------|-------------|---------------|------------------------------|
> | ASIX AX88772 USB 2.0 고속 이더넷 어댑터 | ARM32, x64, x86 | 이 고성능 이며 높은 패킷 버퍼링에 대 한 포함 된 28 KB SRAM 사용 하 여이 있습니다를 통합 합니다.  | | &#10004;  |


### <a name="bluetooth-dongles"></a>Bluetooth 동글
> | 이름 부 / 아니요 | 호환 아키텍처 | 설명 | 관련 링크 | Microsoft Verified  | 
> |----------------|-------------------|-------------|--------|------------------------------|
> | CSR Mini USB Bluetooth V 4.0 Adapter | ARM32, x64, x86 | 스마트 준비 2 어댑터 4.0 Bluetooth, 저 에너지, 이중 전원 클래스 |  | &#10004; 
> | ORICO BTA-403 Mini Bluetooth 4.0 USB Dongle | ARM32, x64, x86 | 저 에너지 Bluetooth 4.0 어댑터 USB 마이크로 어댑터 동글 |  | &#10004; 
> | CSR Mini USB Bluetooth V 4.0 Adapter | x64, x86 | 스마트 준비 2 어댑터 4.0 Bluetooth, 저 에너지, 이중 전원 클래스 |  | &#10004;|

### <a name="cameras"></a>카메라
> | 이름 부 / 아니요 | 호환 아키텍처 | 설명 | 관련 링크 | Microsoft Verified  | 
> |----------------|-------------------|-------------|--------|------------------------------|
> | Microsoft Lifecam 3000 USB 카메라 | ARM32, x64, x86 | USB 웹캠 | [홈 보안 카메라 프로젝트](https://developer.microsoft.com/en-us/windows/iot/samples/webcamapp)|&#10004;|
> | Microsoft Lifecam HD-5000 | ARM32, x64, x86 | Microsoft LifeCam HD-5000 720p HD Webcam | | &#10004; |
> | Microsoft® LifeCam Studio™ | ARM32 | Microsoft® LifeCam Studio™ (모델: 1080p HD 웹캠 1425) | | |
> | Logitech 웹캠 C210 | ARM32, x64, x86 | 웹캠 USB 1.3 mp 사진 |  |&#10004; |

### <a name="audio"></a>오디오
> | 이름 부 / 아니요 | 호환 아키텍처 | 설명 | 관련 링크 | Microsoft Verified |
> |----------------|-------------------|-------------|--------|------------------------------|
> | 모델 AU-EMAC1 sabrent USB 외부 스테레오 사운드 어댑터 | ARM32, x64, x86 | USB 3.5 mm 오디오, 마이크 신호를 변환합니다. | | &#10004; 

### <a name="miscellaneous"></a>기타
> | 이름 부 / 아니요 | 호환 아키텍처 | 설명 | 관련 링크 | Microsoft Verified  | 
> |----------------|-------------------|-------------|--------|------------------------------|
> | Aeon Labs Z-wave Z 스틱 시리즈 2 USB 동글 DSA02203-ZWUS | ARM32 | 시리즈 2 Z-wave USB 스틱 Z 컨트롤러 |  | &#10004; |
> | [칠판 Electronics 7 인치 LCD 용량 성 터치 스크린이 표시](https://www.chalk-elec.com/?page_id=1280#!/7-black-frame-universal-HDMI-LCD-with-capacitive-multi-touch/p/21750201/category=3094861) | ARM32 | | [펌웨어 업데이트](https://www.chalk-elec.com/?p=1826) | &#10004; |
> | Vodafone (Huawei) K5150 | ARM32, x64, x86 | Vodafone (Huawei) K5150 150Mbps 4G LTE FDD USB Mobile Broadband Modem |  | &#10004;  |
> | Vodafone (Huawei) K5160 | ARM32, x64, x86 | (Huawei) Vodafone K5160 150Mbps GSM/EDGE/3g/HSPA + LTE CAT4 USB 모바일 광대역 모뎀 |  | |
> | Sierra 무선 보 (340U 항목) | x64, x86 |    Sierra 무선 보 (항목 340U) 4g LTE USB 모바일 광대역 모뎀 |  |&#10004; |
> | Microsoft Xbox 360 Controller | ARM32 | Microsoft의 Xbox 360는 HID 호환 USB gamepad | [Robot Kit](https://microsoft.hackster.io/en-US/windowsiot/robot-kit-6dd474) |  &#10004; |
> | [MyTeletouch](http://www.myteletouch.com/) | ARM, x32 | USB HID 호환 무선 마우스, 키보드 및 gamepad |  | &#10004; |

## <a name="other-hardware-peripherals"></a>다른 하드웨어 주변 장치

### <a name="nfcrfidproximity"></a>NFC/RFID/근접
> | 이름 부 / 아니요 | 호환 아키텍처 | 설명 | 관련 링크 | Microsoft Verified |
> |----------------|-------------------|-------------|--------|------------------------------|
> | NXP OM5577 데모 보드 | ARM32 | NXP PN7120 NFC 칩에 대 한 데모 보드입니다. | [ProximityDevice 설명서](https://docs.microsoft.com/uwp/api/Windows.Networking.Proximity.ProximityDevice) | &#10004; |
> | NXP PN547/PN548/PN7120 | ARM32, x64, x86 | NXP NFC 칩을 지원 합니다. | | &#10004; |

### <a name="pi-hats"></a>Pi Hats
> | 이름 부 / 아니요 | 호환 아키텍처 | 설명 | 관련 링크 | Microsoft Verified  | 
> |----------------|-------------------|-------------|--------|------------------------------|
> | [Adafruit 16 채널 PWM](https://www.adafruit.com/product/2327#description-anchor) | ARM32 | 추가 Raspberry Pi 처리 오버 헤드 없이 최대 16 개의 서보를 제어 하는 기능을 추가 합니다. PWM 수행할 수 있는 12 비트 전체 자릿수를 사용 하 여 최대 1.6 KHz입니다. | [Adafruit 자습서 C# IoT 샘플](https://github.com/golaat/Adafruit.Pwm) | |
> | [Dexter 산업 GrovePi](https://www.dexterindustries.com/shop/grovepi-board/) | ARM32 | 를 모니터링 하려면 프로그래밍할 수 있도록 컨트롤 용접 없이 수백 개의 다양 한 센서를 연결 하 고 업무에 장치를 자동화할 수 있습니다. | [GrovePi 샘플](https://github.com/DexterInd/GrovePi/) | |
> | Dexter 산업 GoPiGo | ARM, x32 | GoPiGo 로봇을 완벽 하 게 운영에 Pi를 설정 하는 Raspberry Pi에 대 한 매력적인 및 전체 로봇입니다. GoPiGo는 Dexter 산업에서 개발한 Raspberry Pi에 대 한 모바일 로봇 플랫폼. | [GoPiGo 샘플](https://github.com/DexterInd/GoPiGo/tree/master/Software/CSharp) | |

### <a name="port-expanders"></a>포트 확장기
> | 이름 부 / 아니요 | 호환 아키텍처 | 설명 | 관련 링크 | Microsoft Verified  | 
> |----------------|-------------------|-------------|--------|------------------------------|
> | MCP23008 8 비트 I/O 포트 확장기 | ARM32, x64, x86 | GPIO 포트 확장기 I2C 인터페이스 칩입니다. 8 개 포트, 18 PDIP 패키지 | [SPI 포트 Explander 샘플](https://www.hackster.io/4803/i2c-port-expander-sample-0a6d4f) | &#10004; |
> | MCP23S17 16 비트 I/O 포트 확장기 | ARM32, x64, x86 | GPIO 포트 확장기 I2C 인터페이스 칩입니다. 16 포트, 28 SPDIP 패키지 | [대화형 피아노 샘플](https://www.hackster.io/windowsiot/build-2014-piano-3b449c) | &#10004; |

### <a name="storage-media"></a>저장소 미디어
> | 이름 부 / 아니요 | 호환 아키텍처 | 설명 | 관련 링크 | Microsoft Verified  | 
> |----------------|-------------------|-------------|--------|------------------------------|
> | [Samsung 32GB EVO 클래스 10 마이크로 SDHC](https://www.amazon.com/gp/product/B00IVPU786) | AARM32, x64, x86 | Windows 10 IoT Core 플래시 됨을 가질 수 있는 장치에 대 한 권장된 SD 카드. | | &#10004;|
> | [SanDisk Ultra Micro SDHC 16GB](https://www.amazon.com/SanDisk-Ultra-Micro-SDHC-16GB/dp/9966573445) | ARM32, x64, x86 | Windows 10 IoT Core 플래시 됨을 가질 수 있는 장치에 대 한 권장된 SD 카드. | | &#10004; |

### <a name="sensors"></a>센서
> | 이름 부 / 아니요 | 호환 아키텍처 | 설명 | 관련 링크 | Microsoft Verified  | 
> |----------------|-------------------|-------------|--------|------------------------------|
> | DHT11 기본 온도 습도 센서 | ARM32, x64, x86 | Basic, 울트라 저렴 한 비용 디지털 온도 및 습도 센서. 및 사용 하 여 용량 습도 센서를 서미스터 주변 공중에 측정 하 고 데이터 pin (아날로그 입력된 핀 없음 필요)에서 디지털 신호를 산출 합니다.  | [GpioOneWireSample (DHT11)](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/GpioOneWire)| &#10004; |
> | DHT22 온도 습도 센서 | ARM32, x64, x86 | Basic, 울트라 저렴 한 비용 디지털 온도 및 습도 센서. 및 사용 하 여 용량 습도 센서를 서미스터 주변 공중에 측정 하 고 데이터 pin (아날로그 입력된 핀 없음 필요)에서 디지털 신호를 산출 합니다.  | [GpioOneWireSample (DHT11)](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/GpioOneWire) | &#10004; |
> | SparkFun Triple 축이 속도계 혁신-ADXL345 | ARM32, x64, x86 | 작고 씬, 전원, 3 축 MEMS가 속도계 ±16 g까지에서 고해상도 (13 비트) 측정으로 부족 합니다. 디지털 출력 데이터 서식이 지정 된 16 비트 두 개씩 짝을 보완 하 고 SPI (3 또는 4-실시간) 또는 I2C 디지털 인터페이스를 통해 액세스할 수 있습니다. |[가 속도계 샘플](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/Accelerometer) | &#10004; |
> | Adafruit BMP280 온도 및 Barometric 센서 | ARM32 | Bosch 환경 압 온도 센서 | |   &#10004; |
> | [Adafruit TCS34725 색 센서](http://www.adafruit.com/products/1334) | ARM, x32 | IR 필터와 흰색 LED-TCS34725 RGB 색 센서 | | &#10004; |
> | Rohm BH1750FVI 주변 광원 센서 | ARM32 | 앰비언트 조명 측정에 대 한 작은 I2C 센서 | [I2C 샘플](https://github.com/mickut/Win10-IoT-Sensors) | |
> | Bosch BMP180 온도 및 barometric 센서 | ARM, x32 | Bosch 환경 tempreature, 압 센서 | [I2C 샘플](https://github.com/mickut/Win10-IoT-Sensors) | |
> | Dorji DSTH01 상대 습도 센서 | ARM32 | I2C 상대 습도 센서 | [I2C 샘플](https://github.com/mickut/Win10-IoT-Sensors)| |
> | Honeywell HMC5883L 디지털 3 축의 나침반/지자기 센터 | ARM32 | 디지털 나침반 사용 및 자기 필드가 측정에는 작은 3 축 지자기 센터 | [I2C 샘플](https://github.com/mickut/Win10-IoT-Sensors) | |

### <a name="touchpanel-solutions"></a>Touchpanel 솔루션
> | 이름 부 / 아니요 | 호환 아키텍처 | 설명 | 관련 링크 | Microsoft Verified | 
> |----------------|-------------------|-------------|--------|------------------------------|
> | Keith & Koep i 팬 M7 CoverLens | ARM32 | 7.0 산업 사용 Qualcomm Snapdragon 410E CPU, 해결 800x480px qm/밝기 850 cd, USB 2.0, SD 카드 POE Touchpanel 컴퓨터 인치 | [i-팬 M7 정보](https://keith-koep.com/en/products/products-hmi/i-pan-m7-coverlens-arm-touch-panel-computer-technical-data/) | &#10004; |

### <a name="miscellaneous"></a>기타
> | 이름 부 / 아니요 | 호환 아키텍처 | 설명 | 관련 링크 | Microsoft Verified | 
> |----------------|-------------------|-------------|--------|------------------------------|
> | 공식 Pi 표시 | ARM32 | 7"800 x 480 디스플레이 터치 합니다. | [Raspberry Pi 7"터치 스크린](https://www.raspberrypi.org/products/raspberry-pi-touch-display/) | &#10004; |
> | 단색 1.3"128 x 64 OLED 그래픽 표시 |ARM, x32, x64, x86 | 1.3"대각선, 높은 대비 회선이 OLED 표시 합니다. 128 x 64 개별 흰색 OLED 픽셀 각각 컨트롤러 칩에서 켜거나 끌 됩니다. | [SPI 표시 샘플](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/SPIDisplay) | &#10004; |
> | SN74HC595N 시프트 레지스터 IC | ARM32, x64, x86 | IC 8 비트가 이동 레지스터 16 DIP | [시프트 레지스터 샘플](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/ShiftRegister) | &#10004; |
> | 마이크로칩 기술 ADC MCP3002-I/P | AARM32, x64, x86 | MCP3002 10 비트 아날로그 디지털 변환기입니다. |  [전위차계 센서 샘플](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/PotentiometerSensor) | &#10004; |
> | 마이크로칩 기술 ADC MCP3208-CI/P | ARM32, x64, x86 | MCP3208 12 비트 아날로그 디지털 변환기입니다. | [전위차계 센서 샘플](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/PotentiometerSensor) | &#10004; |
> | ADS1115 | ARM, x32, x64, x86 | 초소형, 절전, 16 비트 ADC | [ADC Bus 공급자](https://github.com/ms-iot/BusProviders/tree/develop/ADC) | &#10004; |
> | TTL 모듈에 대 한 직렬 변환기에 CP2102 USB 2.0 | ARM32, x64, x86 | TTL 모듈에 대 한 직렬 변환기에 CP2102 USB 2.0 | [직렬 포트 샘플](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/SerialUART) | &#10004; |
> | PCA9685 | ARM32, x64, x86 | 16 채널, 12 비트 PWM Fm + I2C 버스 LED 컨트롤러입니다. | [PWM Bus 공급자](https://github.com/ms-iot/BusProviders/tree/develop/PWM) | &#10004; |


