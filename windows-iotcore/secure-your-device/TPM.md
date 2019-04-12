---
title: TPM(신뢰할 수 있는 플랫폼 모듈)
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 암호화 기능을 더 잘 보호 장치로 사용할 수 있도록 신뢰할 수 있는 플랫폼 모듈을 사용 하는 방법에 알아봅니다.
keywords: windows iot, 보안, 키, 암호화, TPM, 신뢰할 수 있는 플랫폼 모듈
ms.openlocfilehash: cf22811cbf45b5c715a19b8e12d7b00c2afaa9b8
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512829"
---
# <a name="trusted-platform-module-tpm-on-windows-10-iot-core"></a><span data-ttu-id="fa550-104">Windows 10 IoT Core 신뢰할 수 있는 플랫폼 모듈 (TPM)</span><span class="sxs-lookup"><span data-stu-id="fa550-104">Trusted Platform Module (TPM) on Windows 10 IoT Core</span></span>

## <a name="what-is-tpm"></a><span data-ttu-id="fa550-105">TPM 이란?</span><span class="sxs-lookup"><span data-stu-id="fa550-105">What is TPM?</span></span>
<span data-ttu-id="fa550-106">신뢰할 수 있는 플랫폼 모듈 (TPM), 난수 생성, 암호화 키의 보안 생성 및 사용의 제한 사항에 대 한 기능을 포함 하는 암호화 프로세서입니다.</span><span class="sxs-lookup"><span data-stu-id="fa550-106">A Trusted Platform Module (TPM), is a cryptographic coprocessor including capabilities for random number generation, secure generation of cryptographic keys and limitation of their use.</span></span> <span data-ttu-id="fa550-107">또한 원격 증명 및 봉인 된 저장소와 같은 기능을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa550-107">It also includes capabilities such as remote attestation and sealed storage.</span></span>
<span data-ttu-id="fa550-108">TPM의 기술 사양은 여는 신뢰할 수 있는 컴퓨팅 그룹 TCG ()를 기반 공개적으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa550-108">TPM's technical specification is publicly available, driven by the Trusted Computing Group (TCG).</span></span> <span data-ttu-id="fa550-109">최신 버전 (2014 년 10 월 출시) TPM 2.0은 다시 디자인 하는 주요 새 기능을 추가 하 고 이전 TPM 1.2의 약점을 수정 하는 사양입니다.</span><span class="sxs-lookup"><span data-stu-id="fa550-109">The latest version TPM 2.0 (released October 2014), is a major redesign of the specification which adds new functionality and fixes weaknesses of the former TPM 1.2.</span></span>

## <a name="why-tpm"></a><span data-ttu-id="fa550-110">왜 TPM?</span><span class="sxs-lookup"><span data-stu-id="fa550-110">Why TPM?</span></span>  
<span data-ttu-id="fa550-111">TPM이 장착 된 컴퓨터 암호화 키를 tpm만 해독할 수 있도록 암호화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa550-111">Computers that incorporate a TPM can create cryptographic keys and encrypt them so that they can only be decrypted by the TPM.</span></span> <span data-ttu-id="fa550-112">이 프로세스를 라고도 **"래핑"** 또는 **"바인딩"** 키를 통해 노출 로부터 키를 보호할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa550-112">This process, often called **"wrapping"** or **"binding"** a key, can help protect the key from disclosure.</span></span> <span data-ttu-id="fa550-113">각 TPM에는 마스터 "래핑" 키를 TPM 자체 내에 저장 된 저장소 루트 키를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa550-113">Each TPM has a master "wrapping" key, called the storage root key, which is stored within the TPM itself.</span></span> <span data-ttu-id="fa550-114">TPM에서 만든 키의 비공개 부분은 다른 구성 요소, 소프트웨어, 프로세스 또는 사용자에 노출 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fa550-114">The private portion of a key created in a TPM is never exposed to any other component, software, process, or person.</span></span>  

<span data-ttu-id="fa550-115">TPM이 장착 된 컴퓨터만 래핑되지에 있지만 특정 플랫폼 측정 값에 연결 하는 키를 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa550-115">Computers that incorporate a TPM can also create a key that has not only been wrapped but is also tied to certain platform measurements.</span></span> <span data-ttu-id="fa550-116">이 유형의 키만 수 래핑된 해당 플랫폼 측정 키를 만들 때 동일한 값이 있는 경우.</span><span class="sxs-lookup"><span data-stu-id="fa550-116">This type of key can only be unwrapped when those platform measurements have the same values that they had when the key was created.</span></span> <span data-ttu-id="fa550-117">이 프로세스를 호출할 **"봉인"** tpm 키입니다.</span><span class="sxs-lookup"><span data-stu-id="fa550-117">This process is called **"sealing"** the key to the TPM.</span></span> <span data-ttu-id="fa550-118">호출 되는 키를 암호 해독 **"봉인 해제"** 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa550-118">Decrypting the key is called **"unsealing"**.</span></span> <span data-ttu-id="fa550-119">또한 TPM을 봉인 하 고 TPM 외부에서 생성 된 데이터를 봉인을 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa550-119">The TPM can also seal and unseal data generated outside of the TPM.</span></span> <span data-ttu-id="fa550-120">이 봉인 된 키와 BitLocker 드라이브 암호화와 같은 소프트웨어를 사용 하 여 특정 하드웨어 또는 소프트웨어 조건이 충족 될 때까지 데이터를 잠글 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa550-120">With this sealed key and software such as BitLocker Drive Encryption, you can lock data until specific hardware or software conditions are met.</span></span>  

<span data-ttu-id="fa550-121">TPM을 사용 하면 키 쌍의 비공개 부분이 운영 체제에 의해 제어 되는 메모리와에서 별도로 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa550-121">With a TPM, private portions of key pairs are kept separate from the memory controlled by the operating system.</span></span> <span data-ttu-id="fa550-122">키를 TPM으로 봉인할 수 있습니다 및 키를 봉인 되지 않은 되어 사용에 대 한 출시 전에 (시스템의 "신뢰성"를 정의 하는 보증) 시스템의 상태에 대 한 특정 보증을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa550-122">Keys can be sealed to the TPM, and certain assurances about the state of a system (assurances that define the "trustworthiness" of a system) can be made before the keys are unsealed and released for use.</span></span> <span data-ttu-id="fa550-123">TPM 자체 내부 펌웨어 및 논리 회로 사용 하 여 명령 처리를 위해, 때문에 운영 체제에 의존 하지 않습니다 하 고 운영 체제 또는 응용 프로그램 소프트웨어에 존재 하는 취약성에 노출 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fa550-123">Because the TPM uses its own internal firmware and logic circuits for processing instructions, it does not rely on the operating system and is not exposed to vulnerabilities that might exist in the operating system or application software.</span></span>

## <a name="tpm-architecture"></a><span data-ttu-id="fa550-124">TPM 아키텍처</span><span class="sxs-lookup"><span data-stu-id="fa550-124">TPM Architecture</span></span>
_<span data-ttu-id="fa550-125">TPM 1.2 및 TPM 2.0 간의 차이입니다.</span><span class="sxs-lookup"><span data-stu-id="fa550-125">Difference between TPM 1.2 and TPM 2.0.</span></span>_  
<span data-ttu-id="fa550-126">TPM 사양 두 번 개발 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="fa550-126">The TPM specification has been developed twice.</span></span> <span data-ttu-id="fa550-127">처음으로이에서 개발 1.1b 1.2, 사양 위원회에서 요청/확인 하는 새로운 기능을 통합 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa550-127">The first time, it developed from 1.1b to 1.2, incorporating  new capabilities requested/identified by the specification committee.</span></span> <span data-ttu-id="fa550-128">이 기능이 점점 형태의 최종 TPM 1.2 사양에 매우 수행 하는 진화 복잡 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa550-128">This feature-creep form of evolution made the final TPM 1.2 specification very complicated.</span></span> <span data-ttu-id="fa550-129">결국 (이었던, 가장 강력한 상용 알고리즘에서 TPM 1.2) sha-1 암호화 약점 변경에 대 한 필요성 때문에 표시 된 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa550-129">Eventually, cryptographic weaknesses of SHA-1 (which was the strongest commercial algorithm in TPM 1.2) were revealed which caused the need for a change.</span></span> <span data-ttu-id="fa550-130">TPM 아키텍처는 TPM 2.0의 훨씬 더 통합 되 고 통합 된 디자인의 결과 처음부터 다시 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="fa550-130">The TPM architecture was redesigned from scratch, resulting in the much more integrated and unified design of TPM 2.0.</span></span>  

<span data-ttu-id="fa550-131">변경 내용과 이전 TPM 1.2에 비해 향상 된 기능 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="fa550-131">The changes and enhancements compared to the previous TPM 1.2 include:</span></span>

* <span data-ttu-id="fa550-132">추가 암호화 알고리즘에 대 한 지원</span><span class="sxs-lookup"><span data-stu-id="fa550-132">Support for additional cryptographic algorithms</span></span>
* <span data-ttu-id="fa550-133">응용 프로그램에는 TPM의 가용성 향상</span><span class="sxs-lookup"><span data-stu-id="fa550-133">Enhancements to the availability of the TPM to applications</span></span>
* <span data-ttu-id="fa550-134">향상 된 권한 부여 메커니즘</span><span class="sxs-lookup"><span data-stu-id="fa550-134">Enhanced authorization mechanisms</span></span>
* <span data-ttu-id="fa550-135">간소화 된 TPM 관리</span><span class="sxs-lookup"><span data-stu-id="fa550-135">Simplified TPM management</span></span>
* <span data-ttu-id="fa550-136">플랫폼 서비스의 보안을 강화 하기 위해 추가 기능</span><span class="sxs-lookup"><span data-stu-id="fa550-136">Additional capabilities to enhance the security of platform services</span></span>

<span data-ttu-id="fa550-137">Windows IoT Core는 TPM 2.0만 지원 하 고 오래 된 TPM 1.2를 지원 하지 않습니다 note 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa550-137">Note that Windows IoT Core supports only TPM 2.0 and does not support the outdated TPM 1.2.</span></span>

## <a name="what-is-tbs"></a><span data-ttu-id="fa550-138">TB 란?</span><span class="sxs-lookup"><span data-stu-id="fa550-138">What is TBS?</span></span> 
<span data-ttu-id="fa550-139">TPM 기본 서비스 (TB) 기능은 TPM 리소스의 투명 하 게 공유할 수 있도록 하는 시스템 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="fa550-139">The TPM Base Services (TBS) feature is a system service that allows transparent sharing of the TPM resources.</span></span> <span data-ttu-id="fa550-140">원격 프로시저 호출 (RPC)을 통해 동일한 물리적 컴퓨터에서 여러 응용 프로그램에서 TPM 리소스를 공유 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa550-140">It shares the TPM resources among multiple applications on the same physical machine through remote procedure calls (RPC).</span></span> <span data-ttu-id="fa550-141">이 호출 응용 프로그램에서 지정 된 우선 순위를 사용 하 여 응용 프로그램에서 TPM 액세스를 중앙 집중화 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa550-141">It centralizes TPM access across applications using priorities specified by the calling applications.</span></span>  

<span data-ttu-id="fa550-142">TPM 트러스트 플랫폼에서 제공 하도록 설계 된 암호화 기능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa550-142">The TPM provides cryptographic functions designed to provide trust in the platform.</span></span> <span data-ttu-id="fa550-143">TPM를 하드웨어에 구현 되므로 리소스가 한정 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa550-143">Because the TPM is implemented in hardware, it has finite resources.</span></span> <span data-ttu-id="fa550-144">TCG TPM 소프트웨어 스택을 (TSS)를 사용 하 여 이러한 리소스 응용 프로그램 소프트웨어에 대 한 신뢰할 수 있는 작업을 제공 하기를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa550-144">The TCG defines a TPM Software Stack (TSS) that makes use of these resources to provide trusted operations for application software.</span></span> <span data-ttu-id="fa550-145">그러나 또한 TPM 리소스 사용 중일 수 있는 운영 체제 소프트웨어로 TSS 구현-side-by-side 실행에 대 한 없습니다 프로 비전이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa550-145">However, no provision is made for running a TSS implementation side-by-side with operating system software that may also be using TPM resources.</span></span> <span data-ttu-id="fa550-146">컴퓨터에서 실행 될 수 있는 다른 소프트웨어 스택에 대 한 TPM 리소스 확인을 사용 하는 TB와 통신 하는 각 소프트웨어 스택을 사용 하 여이 문제를 해결 하는 TB 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="fa550-146">The TBS feature solves this problem by enabling each software stack that communicates with TBS to use TPM resources checking for any other software stacks that may be running on the machine.</span></span>

## <a name="tpm-solutions-available-on-windows-iot-core"></a><span data-ttu-id="fa550-147">Windows IoT Core에 사용할 수 있는 TPM 솔루션</span><span class="sxs-lookup"><span data-stu-id="fa550-147">TPM solutions available on Windows IoT Core</span></span>  
_<span data-ttu-id="fa550-148">소프트웨어 TPM (sTPM), 펌웨어 TPM (fTPM), 불연속 TPM (dTPM) 하는 방법에 대 한 몇 가지 단어 중...</span><span class="sxs-lookup"><span data-stu-id="fa550-148">A few words about Software TPM (sTPM), Firmware TPM (fTPM), Discrete TPM (dTPM)...</span></span>_

### <a name="firmware-tpm-ftpm"></a><span data-ttu-id="fa550-149">TPM (fTPM) 펌웨어</span><span class="sxs-lookup"><span data-stu-id="fa550-149">Firmware TPM (fTPM)</span></span>  
<span data-ttu-id="fa550-150">TPM (fTPM) 펌웨어에는 Raspberry Pi 2 또는 3의 현재 구현 되지 않은 특수 프로세서/SoC 지원이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa550-150">Firmware TPM (fTPM) requires special Processor/SoC support that is not currently implemented on Raspberry Pi 2 or 3.</span></span> <span data-ttu-id="fa550-151">MinnowBoard 최대 0.80 이상 펌웨어 버전이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="fa550-151">MinnowBoard Max needs firmware version 0.80 or higher.</span></span> <span data-ttu-id="fa550-152">DragonBoard410c는 기본적으로 사용 하도록 설정 하는 즉시 fTPM 기능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa550-152">DragonBoard410c provides fTPM capabilities out of the box enabled by default.</span></span>  

### <a name="discrete-tpm-dtpm"></a><span data-ttu-id="fa550-153">불연속 TPM (dTPM)</span><span class="sxs-lookup"><span data-stu-id="fa550-153">Discrete TPM (dTPM)</span></span>  
<span data-ttu-id="fa550-154">불연속 TPM (dTPM) 가장 신뢰할 수 있는 솔루션을 모든 것으로 간주 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa550-154">Discrete TPM (dTPM) is considered the utmost trustworthy solution by all means.</span></span>  
<span data-ttu-id="fa550-155">DTPM 칩과 Windows IoT Core에서 지원 되는 PCB 모듈의 여러 제조업체 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa550-155">There are several manufacturers of dTPM chips and PCB modules that are supported on Windows IoT Core:</span></span>

> | <span data-ttu-id="fa550-156">제조업체</span><span class="sxs-lookup"><span data-stu-id="fa550-156">Manufacturer</span></span> | <span data-ttu-id="fa550-157">웹 페이지</span><span class="sxs-lookup"><span data-stu-id="fa550-157">Web Page</span></span> | <span data-ttu-id="fa550-158">연속 모듈 유형</span><span class="sxs-lookup"><span data-stu-id="fa550-158">Modul Type</span></span> | <span data-ttu-id="fa550-159">TPM 칩</span><span class="sxs-lookup"><span data-stu-id="fa550-159">TPM Chip</span></span> |
> |-------------|----------|----------|----------| 
> | <span data-ttu-id="fa550-160">Infineon</span><span class="sxs-lookup"><span data-stu-id="fa550-160">Infineon</span></span> | [<span data-ttu-id="fa550-161">Infineon TPM</span><span class="sxs-lookup"><span data-stu-id="fa550-161">Infineon TPM</span></span>](https://www.infineon.com/cms/en/product/evaluation-boards/iridium9670-tpm2.0-linux/)| <span data-ttu-id="fa550-162">Evalboard</span><span class="sxs-lookup"><span data-stu-id="fa550-162">Evalboard</span></span> | [<span data-ttu-id="fa550-163">Infineon SLB9670 TPM 2.0</span><span class="sxs-lookup"><span data-stu-id="fa550-163">Infineon SLB9670 TPM 2.0</span></span>](https://www.infineon.com/cms/de/product/security-smart-card-solutions/optiga-embedded-security-solutions/optiga-tpm/slb-9670vq2.0/) |
> | <span data-ttu-id="fa550-164">Pi3g</span><span class="sxs-lookup"><span data-stu-id="fa550-164">Pi3g</span></span> | [<span data-ttu-id="fa550-165">Pi3g.com</span><span class="sxs-lookup"><span data-stu-id="fa550-165">Pi3g.com</span></span>](https://pi3g.com/eigene-produkte/)| <span data-ttu-id="fa550-166">대용량 제품 & Evalboard</span><span class="sxs-lookup"><span data-stu-id="fa550-166">Mass Product & Evalboard</span></span> | [<span data-ttu-id="fa550-167">Infineon SLB9670 TPM 2.0</span><span class="sxs-lookup"><span data-stu-id="fa550-167">Infineon SLB9670 TPM 2.0</span></span>](https://www.infineon.com/cms/de/product/security-smart-card-solutions/optiga-embedded-security-solutions/optiga-tpm/slb-9670vq2.0/) |


### <a name="software-tpm-stpm"></a><span data-ttu-id="fa550-168">소프트웨어 TPM (sTPM)</span><span class="sxs-lookup"><span data-stu-id="fa550-168">Software TPM (sTPM)</span></span>  
<span data-ttu-id="fa550-169">TPM (sTPM) 소프트웨어는 TPM 시뮬레이터 라고도 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa550-169">Software TPM (sTPM) is also referred to as TPM Simulator.</span></span> <span data-ttu-id="fa550-170">Windows IoT Core에 지원 플랫폼에 독립적입니다.</span><span class="sxs-lookup"><span data-stu-id="fa550-170">It is platform-independent, supported on Windows IoT Core.</span></span>  

> [!NOTE]
> <span data-ttu-id="fa550-171">sTPM 개발 목적 으로만 제공 되 고 실제 보안 이점을 제공 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fa550-171">sTPM is intended for development purposes only and does not provide any real security benefits.</span></span>  


## <a name="samples"></a><span data-ttu-id="fa550-172">샘플</span><span class="sxs-lookup"><span data-stu-id="fa550-172">Samples</span></span>  
<!--
* [TBSSample project C++](https://developer.microsoft.com/en-us/windows/iot/samples/tbssample)
  This tutorial demonstrates how to create a basic C++ application that uses TBS to poll the TPM.  -->
* <span data-ttu-id="fa550-173">[Urchin 라이브러리 샘플](https://github.com/ms-iot/security/tree/master/Urchin/Lib) 이 자습서에서는 샘플을 만드는 방법을 보여 줍니다. C++ 사용 하 여 TPM 기능을 연습 하는 응용 프로그램을 [Urchin 라이브러리](https://github.com/ms-iot/security)합니다.</span><span class="sxs-lookup"><span data-stu-id="fa550-173">[Urchin Library Sample](https://github.com/ms-iot/security/tree/master/Urchin/Lib) This tutorial demonstrates how to create a sample C++ application that exercises the TPM functionality using the [Urchin library](https://github.com/ms-iot/security).</span></span> <span data-ttu-id="fa550-174">Urchin에 TPM 2.0 참조 구현에서 파생 된 사양 규격 라이브러리입니다.</span><span class="sxs-lookup"><span data-stu-id="fa550-174">Urchin is a spec-compliant library derived from the TPM 2.0 reference implementation.</span></span> <span data-ttu-id="fa550-175">클라이언트에 모든 데이터 구조 마샬링/역마샬링, 제대로 계산 권한 부여, 매개 변수 암호화를 수행 하 고 감사를 수행 하는 기능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa550-175">It provides to the client the functionality to marshal/unmarshal all data structures, properly calculate authorizations, perform parameter encryption and do auditing.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="fa550-176">추가 리소스</span><span class="sxs-lookup"><span data-stu-id="fa550-176">Additional Resources</span></span>  
* [<span data-ttu-id="fa550-177">신뢰할 수 있는 플랫폼 모듈 (TPM) 사양</span><span class="sxs-lookup"><span data-stu-id="fa550-177">Trusted Platform Module (TPM) Specifications</span></span>](http://www.trustedcomputinggroup.org/developers/trusted_platform_module) 
* [<span data-ttu-id="fa550-178">TCG TPM 2.0 라이브러리 사양</span><span class="sxs-lookup"><span data-stu-id="fa550-178">TCG TPM 2.0 Library Specification</span></span>](http://www.trustedcomputinggroup.org/resources/tpm_library_specification)
* [<span data-ttu-id="fa550-179">TPM 기본 서비스</span><span class="sxs-lookup"><span data-stu-id="fa550-179">TPM Base Services</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa446796(v=vs.85).aspx) 
* [<span data-ttu-id="fa550-180">보안 부팅 및 BitLocker를 사용 하도록 설정</span><span class="sxs-lookup"><span data-stu-id="fa550-180">Enabling Secure Boot and BitLocker</span></span>](SecureBootAndBitLocker.md)
