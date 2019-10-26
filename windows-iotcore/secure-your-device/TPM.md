---
title: TPM(신뢰할 수 있는 플랫폼 모듈)
ms.date: 08/28/2017
ms.topic: article
description: 신뢰할 수 있는 플랫폼 모듈를 사용 하 여 암호화 기능을 사용 하 여 장치를 보다 안전 하 게 보호 하는 방법을 알아봅니다.
keywords: windows iot, 보안, 신뢰할 수 있는 플랫폼 모듈, TPM, 암호화, 키
ms.openlocfilehash: 36197c1cea96c964026682da2d05ba1fcd6524a9
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918529"
---
# <a name="trusted-platform-module-tpm-on-windows-10-iot-core"></a>Windows 10 IoT Core의 신뢰할 수 있는 플랫폼 모듈 (TPM)

## <a name="what-is-tpm"></a>TPM 이란?
TPM (신뢰할 수 있는 플랫폼 모듈)은 난수 생성, 암호화 키의 보안 생성 및 사용 제한에 대 한 기능을 포함 하는 암호화 보조 프로세서입니다. 또한 원격 증명 및 봉인 된 저장소와 같은 기능을 포함 합니다.
TPM의 기술 사양은 TCG(신뢰할 수 있는 컴퓨팅 그룹) (TCG)를 기반으로 공개적으로 제공 됩니다. 최신 버전의 TPM 2.0 (10 월 2014 릴리스)는 새로운 기능을 추가 하 고 이전 TPM 1.2의 취약점을 해결 하는 주요 디자인입니다.

## <a name="why-tpm"></a>TPM이 무엇 인가요?  
TPM을 통합 하는 컴퓨터는 암호화 키를 만든 다음 TPM을 통해서만 암호를 해독할 수 있도록 암호화 키를 암호화할 수 있습니다. 주로 **"래핑"** 또는 **"바인딩"** 이라고 하는이 프로세스를 통해 키를 공개 하지 않도록 보호할 수 있습니다. 각 TPM에는 TPM 자체 내에 저장 되는 저장소 루트 키 라는 마스터 "래핑" 키가 있습니다. TPM에서 만든 키의 개인 부분은 다른 구성 요소, 소프트웨어, 프로세스 또는 사용자에 게 노출 되지 않습니다.  

TPM을 통합 하는 컴퓨터는 래핑되지 않은 키를 만들 수도 있지만 특정 플랫폼 측정에도 연결 되어 있습니다. 이러한 키 유형은 해당 플랫폼 측정이 키를 만들 때와 동일한 값을 갖는 경우에만 래핑을 해제할 수 있습니다. 이 프로세스를 TPM에 대 한 키를 **"봉인"** 이라고 합니다. 키 암호를 해독 하는 것을 **"unsealing"** 라고 합니다. Tpm은 TPM 외부에 생성 된 데이터를 봉인 하 고 봉인 수도 있습니다. BitLocker 드라이브 암호화와 같은 봉인 된 키 및 소프트웨어를 사용 하면 특정 하드웨어 또는 소프트웨어 조건이 충족 될 때까지 데이터를 잠글 수 있습니다.  

TPM을 사용 하는 경우 키 쌍의 개인 부분은 운영 체제에서 제어 하는 메모리와 별도로 유지 됩니다. 키는 TPM에 봉인할 수 있으며, 시스템의 상태에 대 한 특정 보증 (시스템의 "신뢰성"을 정의 하는 보장)은 키가 봉인 되어 사용을 위해 해제 되기 전에 수행 될 수 있습니다. TPM은 자체 내부 펌웨어 및 논리 회로를 사용 하 여 명령을 처리 하기 때문에 운영 체제를 사용 하지 않으며 운영 체제 또는 응용 프로그램 소프트웨어에 있을 수 있는 취약점에 노출 되지 않습니다.

## <a name="tpm-architecture"></a>TPM 아키텍처
_TPM 1.2와 TPM 2.0 간의 차이점입니다._  
TPM 사양이 두 번 개발 되었습니다. 처음에는 1.1 b에서 1.2으로 개발 하 여 사양 위원회에서 요청/식별 한 새로운 기능을 통합 했습니다. 이 기능의 크립 형태는 최종 TPM 1.2 사양을 매우 복잡 하 게 만들었습니다. 결국 s h a-1의 암호화 약점 (TPM 1.2의 가장 강력한 상용 알고리즘이 되었음)이 표시 되었으며이로 인해 변경이 필요 했습니다. TPM 아키텍처가 처음부터 새로 디자인 되었으므로 TPM 2.0에 대 한 통합 및 통합 디자인이 훨씬 더 많이 있습니다.  

이전 TPM 1.2에 비해 변경 내용 및 향상 된 기능은 다음과 같습니다.

* 추가 암호화 알고리즘에 대 한 지원
* 응용 프로그램에 대 한 TPM 가용성 향상
* 향상 된 권한 부여 메커니즘
* 간소화 된 TPM 관리
* 플랫폼 서비스의 보안을 강화 하는 추가 기능

> [!NOTE] 
> Windows IoT Core는 TPM 2.0만 지원 하 고 오래 된 TPM 1.2은 지원 하지 않습니다.

## <a name="what-is-tbs"></a>TBS 란? 
TBS (TPM Base Services) 기능은 TPM 리소스를 투명 하 게 공유할 수 있는 시스템 서비스입니다. RPC (원격 프로시저 호출)를 통해 동일한 물리적 컴퓨터의 여러 응용 프로그램 간에 TPM 리소스를 공유 합니다. 호출 응용 프로그램에서 지정 된 우선 순위를 사용 하 여 응용 프로그램 간에 TPM 액세스를 중앙 집중화 합니다.  

TPM은 플랫폼에서 트러스트를 제공 하도록 설계 된 암호화 함수를 제공 합니다. TPM은 하드웨어에서 구현 되므로 유한 리소스를 가집니다. TCG는 이러한 리소스를 사용 하 여 응용 프로그램 소프트웨어에 대 한 신뢰할 수 있는 작업을 제공 하는 TSS (TPM 소프트웨어 스택)를 정의 합니다. 그러나 TPM 리소스를 사용 하는 운영 체제 소프트웨어와 함께 TSS 구현을 side-by-side로 실행 하기 위한 프로 비전은 이루어지지 않습니다. TBS 기능은 컴퓨터에서 실행 중일 수 있는 다른 소프트웨어 스택에 대해 확인 하기 위해 TBS와 통신 하는 각 소프트웨어 스택을 사용 하도록 설정 하 여이 문제를 해결 합니다.

## <a name="tpm-solutions-available-on-windows-iot-core"></a>Windows IoT Core에서 사용할 수 있는 TPM 솔루션  
_소프트웨어 TPM (sTPM), 펌웨어 TPM (fTPM), 불연속 TPM (dTPM)에 대 한 몇 가지 단어_

### <a name="firmware-tpm-ftpm"></a>FTPM (펌웨어 TPM)  
펌웨어 TPM (fTPM)에는 Raspberry Pi 2 또는 3에서 현재 구현 되지 않은 특수 한 프로세서/SoC 지원이 필요 합니다. MinnowBoard Max에는 펌웨어 버전 0.80 이상이 필요 합니다. DragonBoard410c은 기본적으로 사용 하도록 설정 된 기본적으로 fTPM 기능을 제공 합니다.  

### <a name="discrete-tpm-dtpm"></a>불연속 TPM (dTPM)  
불연속 TPM (dTPM)은 모든 방법으로 가장 신뢰할 수 있는 솔루션으로 간주 됩니다.  
Windows IoT Core에서 지원 되는 dTPM 칩 및 PCB 모듈의 여러 제조업체는 다음과 같습니다.

> | 제조업체 | 웹 페이지 | Modul 형식 | TPM 칩 |
> |-------------|----------|----------|----------| 
> | Infineon | [Broadcomm TPM](https://www.infineon.com/cms/en/product/evaluation-boards/iridium9670-tpm2.0-linux/)| Evalboard | [Broadcomm SLB9670 TPM 2.0](https://www.infineon.com/cms/de/product/security-smart-card-solutions/optiga-embedded-security-solutions/optiga-tpm/slb-9670vq2.0/) |
> | Pi3g | [Pi3g.com](https://pi3g.com/eigene-produkte/)| 대량 제품 & Evalboard | [Broadcomm SLB9670 TPM 2.0](https://www.infineon.com/cms/de/product/security-smart-card-solutions/optiga-embedded-security-solutions/optiga-tpm/slb-9670vq2.0/) |


### <a name="software-tpm-stpm"></a>소프트웨어 TPM (sTPM)  
소프트웨어 TPM (sTPM)을 TPM 시뮬레이터 라고도 합니다. Windows IoT Core에서 지원 되는 플랫폼 독립적입니다.  

> [!NOTE]
> sTPM은 개발 목적 으로만 제공 되며 실제 보안 이점을 제공 하지 않습니다.  


## <a name="samples"></a>샘플  
<!--
* [TBSSample project C++](https://developer.microsoft.com/en-us/windows/iot/samples/tbssample)
  This tutorial demonstrates how to create a basic C++ application that uses TBS to poll the TPM.  -->
* [Urchin Library 샘플](https://github.com/ms-iot/security/tree/master/Urchin/Lib) 이 자습서에서는 [Urchin 라이브러리](https://github.com/ms-iot/security)를 사용 하 C++ 여 TPM 기능을 사용 하는 샘플 응용 프로그램을 만드는 방법을 보여 줍니다. Urchin는 TPM 2.0 참조 구현에서 파생 된 사양 규격 라이브러리입니다. 모든 데이터 구조를 마샬링/트랜잭션의 역마샬링 위해 하 고, 권한 부여를 올바르게 계산 하 고, 매개 변수 암호화를 수행 하 고, 감사 하는 기능을 클라이언트에 제공 합니다.

## <a name="additional-resources"></a>추가 리소스  
* [TPM (신뢰할 수 있는 플랫폼 모듈) 사양](http://www.trustedcomputinggroup.org/developers/trusted_platform_module) 
* [TCG TPM 2.0 라이브러리 사양](http://www.trustedcomputinggroup.org/resources/tpm_library_specification)
* [TPM 기본 서비스](https://msdn.microsoft.com/library/windows/desktop/aa446796(v=vs.85).aspx) 
* [보안 부팅 및 BitLocker 사용](SecureBootAndBitLocker.md)

