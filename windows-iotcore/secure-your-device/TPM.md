---
title: TPM(신뢰할 수 있는 플랫폼 모듈)
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 암호화 기능을 더 잘 보호 장치로 사용할 수 있도록 신뢰할 수 있는 플랫폼 모듈을 사용 하는 방법에 알아봅니다.
keywords: windows iot, 보안, 키, 암호화, TPM, 신뢰할 수 있는 플랫폼 모듈
ms.openlocfilehash: 70552a5f98891281879f1d45cbdbd671b56dd902
ms.sourcegitcommit: 77b86eee2bba3844e87f9d3dbef816761ddf0dd9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/11/2019
ms.locfileid: "65533315"
---
# <a name="trusted-platform-module-tpm-on-windows-10-iot-core"></a>Windows 10 IoT Core 신뢰할 수 있는 플랫폼 모듈 (TPM)

## <a name="what-is-tpm"></a>TPM 이란?
신뢰할 수 있는 플랫폼 모듈 (TPM), 난수 생성, 암호화 키의 보안 생성 및 사용의 제한 사항에 대 한 기능을 포함 하는 암호화 프로세서입니다. 또한 원격 증명 및 봉인 된 저장소와 같은 기능을 포함 합니다.
TPM의 기술 사양은 여는 신뢰할 수 있는 컴퓨팅 그룹 TCG ()를 기반 공개적으로 사용할 수 있습니다. 최신 버전 (2014 년 10 월 출시) TPM 2.0은 다시 디자인 하는 주요 새 기능을 추가 하 고 이전 TPM 1.2의 약점을 수정 하는 사양입니다.

## <a name="why-tpm"></a>왜 TPM?  
TPM이 장착 된 컴퓨터 암호화 키를 tpm만 해독할 수 있도록 암호화할 수 있습니다. 이 프로세스를 라고도 **"래핑"** 또는 **"바인딩"** 키를 통해 노출 로부터 키를 보호할 수 있습니다. 각 TPM에는 마스터 "래핑" 키를 TPM 자체 내에 저장 된 저장소 루트 키를 호출 합니다. TPM에서 만든 키의 비공개 부분은 다른 구성 요소, 소프트웨어, 프로세스 또는 사용자에 노출 되지 않습니다.  

TPM이 장착 된 컴퓨터만 래핑되지에 있지만 특정 플랫폼 측정 값에 연결 하는 키를 만들 수도 있습니다. 이 유형의 키만 수 래핑된 해당 플랫폼 측정 키를 만들 때 동일한 값이 있는 경우. 이 프로세스를 호출할 **"봉인"** tpm 키입니다. 호출 되는 키를 암호 해독 **"봉인 해제"** 합니다. 또한 TPM을 봉인 하 고 TPM 외부에서 생성 된 데이터를 봉인을 해제할 수 있습니다. 이 봉인 된 키와 BitLocker 드라이브 암호화와 같은 소프트웨어를 사용 하 여 특정 하드웨어 또는 소프트웨어 조건이 충족 될 때까지 데이터를 잠글 수 있습니다.  

TPM을 사용 하면 키 쌍의 비공개 부분이 운영 체제에 의해 제어 되는 메모리와에서 별도로 유지 됩니다. 키를 TPM으로 봉인할 수 있습니다 및 키를 봉인 되지 않은 되어 사용에 대 한 출시 전에 (시스템의 "신뢰성"를 정의 하는 보증) 시스템의 상태에 대 한 특정 보증을 수 있습니다. TPM 자체 내부 펌웨어 및 논리 회로 사용 하 여 명령 처리를 위해, 때문에 운영 체제에 의존 하지 않습니다 하 고 운영 체제 또는 응용 프로그램 소프트웨어에 존재 하는 취약성에 노출 되지 않습니다.

## <a name="tpm-architecture"></a>TPM 아키텍처
_TPM 1.2 및 TPM 2.0 간의 차이입니다._  
TPM 사양 두 번 개발 되었습니다. 처음으로이에서 개발 1.1b 1.2, 사양 위원회에서 요청/확인 하는 새로운 기능을 통합 합니다. 이 기능이 점점 형태의 최종 TPM 1.2 사양에 매우 수행 하는 진화 복잡 합니다. 결국 (이었던, 가장 강력한 상용 알고리즘에서 TPM 1.2) sha-1 암호화 약점 변경에 대 한 필요성 때문에 표시 된 합니다. TPM 아키텍처는 TPM 2.0의 훨씬 더 통합 되 고 통합 된 디자인의 결과 처음부터 다시 설계 되었습니다.  

변경 내용과 이전 TPM 1.2에 비해 향상 된 기능 다음과 같습니다.

* 추가 암호화 알고리즘에 대 한 지원
* 응용 프로그램에는 TPM의 가용성 향상
* 향상 된 권한 부여 메커니즘
* 간소화 된 TPM 관리
* 플랫폼 서비스의 보안을 강화 하기 위해 추가 기능

> [!NOTE] 
> Windows IoT Core는 TPM 2.0만 지원 및 오래 된 TPM 1.2를 지원 하지 않습니다.

## <a name="what-is-tbs"></a>TB 란? 
TPM 기본 서비스 (TB) 기능은 TPM 리소스의 투명 하 게 공유할 수 있도록 하는 시스템 서비스입니다. 원격 프로시저 호출 (RPC)을 통해 동일한 물리적 컴퓨터에서 여러 응용 프로그램에서 TPM 리소스를 공유 합니다. 이 호출 응용 프로그램에서 지정 된 우선 순위를 사용 하 여 응용 프로그램에서 TPM 액세스를 중앙 집중화 합니다.  

TPM 트러스트 플랫폼에서 제공 하도록 설계 된 암호화 기능을 제공 합니다. TPM를 하드웨어에 구현 되므로 리소스가 한정 되어 있습니다. TCG TPM 소프트웨어 스택을 (TSS)를 사용 하 여 이러한 리소스 응용 프로그램 소프트웨어에 대 한 신뢰할 수 있는 작업을 제공 하기를 정의 합니다. 그러나 또한 TPM 리소스 사용 중일 수 있는 운영 체제 소프트웨어로 TSS 구현-side-by-side 실행에 대 한 없습니다 프로 비전이 됩니다. 컴퓨터에서 실행 될 수 있는 다른 소프트웨어 스택에 대 한 TPM 리소스 확인을 사용 하는 TB와 통신 하는 각 소프트웨어 스택을 사용 하 여이 문제를 해결 하는 TB 기능입니다.

## <a name="tpm-solutions-available-on-windows-iot-core"></a>Windows IoT Core에 사용할 수 있는 TPM 솔루션  
_소프트웨어 TPM (sTPM), 펌웨어 TPM (fTPM), 불연속 TPM (dTPM) 하는 방법에 대 한 몇 가지 단어 중..._

### <a name="firmware-tpm-ftpm"></a>TPM (fTPM) 펌웨어  
TPM (fTPM) 펌웨어에는 Raspberry Pi 2 또는 3의 현재 구현 되지 않은 특수 프로세서/SoC 지원이 필요 합니다. MinnowBoard 최대 0.80 이상 펌웨어 버전이 필요합니다. DragonBoard410c는 기본적으로 사용 하도록 설정 하는 즉시 fTPM 기능을 제공 합니다.  

### <a name="discrete-tpm-dtpm"></a>불연속 TPM (dTPM)  
불연속 TPM (dTPM) 가장 신뢰할 수 있는 솔루션을 모든 것으로 간주 됩니다.  
DTPM 칩과 Windows IoT Core에서 지원 되는 PCB 모듈의 여러 제조업체 가지가 있습니다.

> | 제조업체 | 웹 페이지 | 연속 모듈 유형 | TPM 칩 |
> |-------------|----------|----------|----------| 
> | Infineon | [Infineon TPM](https://www.infineon.com/cms/en/product/evaluation-boards/iridium9670-tpm2.0-linux/)| Evalboard | [Infineon SLB9670 TPM 2.0](https://www.infineon.com/cms/de/product/security-smart-card-solutions/optiga-embedded-security-solutions/optiga-tpm/slb-9670vq2.0/) |
> | Pi3g | [Pi3g.com](https://pi3g.com/eigene-produkte/)| 대용량 제품 & Evalboard | [Infineon SLB9670 TPM 2.0](https://www.infineon.com/cms/de/product/security-smart-card-solutions/optiga-embedded-security-solutions/optiga-tpm/slb-9670vq2.0/) |


### <a name="software-tpm-stpm"></a>소프트웨어 TPM (sTPM)  
TPM (sTPM) 소프트웨어는 TPM 시뮬레이터 라고도 합니다. Windows IoT Core에 지원 플랫폼에 독립적입니다.  

> [!NOTE]
> sTPM 개발 목적 으로만 제공 되 고 실제 보안 이점을 제공 하지 않습니다.  


## <a name="samples"></a>샘플  
<!--
* [TBSSample project C++](https://developer.microsoft.com/en-us/windows/iot/samples/tbssample)
  This tutorial demonstrates how to create a basic C++ application that uses TBS to poll the TPM.  -->
* [Urchin 라이브러리 샘플](https://github.com/ms-iot/security/tree/master/Urchin/Lib) 이 자습서에서는 샘플을 만드는 방법을 보여 줍니다. C++ 사용 하 여 TPM 기능을 연습 하는 응용 프로그램을 [Urchin 라이브러리](https://github.com/ms-iot/security)합니다. Urchin에 TPM 2.0 참조 구현에서 파생 된 사양 규격 라이브러리입니다. 클라이언트에 모든 데이터 구조 마샬링/역마샬링, 제대로 계산 권한 부여, 매개 변수 암호화를 수행 하 고 감사를 수행 하는 기능을 제공 합니다.

## <a name="additional-resources"></a>추가 리소스  
* [신뢰할 수 있는 플랫폼 모듈 (TPM) 사양](http://www.trustedcomputinggroup.org/developers/trusted_platform_module) 
* [TCG TPM 2.0 라이브러리 사양](http://www.trustedcomputinggroup.org/resources/tpm_library_specification)
* [TPM 기본 서비스](https://msdn.microsoft.com/library/windows/desktop/aa446796(v=vs.85).aspx) 
* [보안 부팅 및 BitLocker를 사용 하도록 설정](SecureBootAndBitLocker.md)

