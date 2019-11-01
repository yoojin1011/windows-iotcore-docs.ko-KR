---
title: mDNS 응답기 샘플 소스 시작
ms.date: 02/26/2019
ms.topic: article
description: mDNS 응답기 샘플 소스를 시작하는 방법에 대해 알아봅니다.
keywords: Windows 10 IoT Core, mDNS 응답기 샘플 소스
ms.openlocfilehash: ca99a217ade4c55c6d3050134af8d5663d8d1621
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72917338"
---
# <a name="getting-started-with-mdns-responder-sample-source"></a><span data-ttu-id="2811c-104">mDNS 응답기 샘플 소스 시작</span><span class="sxs-lookup"><span data-stu-id="2811c-104">Getting Started with mDNS Responder Sample Source</span></span>

## <a name="getting-started"></a><span data-ttu-id="2811c-105">시작</span><span class="sxs-lookup"><span data-stu-id="2811c-105">Getting started</span></span>

1.  <span data-ttu-id="2811c-106">프로젝트 *mDNSResponder*를 컴파일하여 서비스인 mDNSResponder.exe를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="2811c-106">Compile the project *mDNSResponder* to get mDNSResponder.exe, which is a service.</span></span> <span data-ttu-id="2811c-107">.exe를 대상 머신에 복사한 다음, 서비스를 등록하고 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="2811c-107">Copy the .exe to the target machine then register the service and run.</span></span>
2. <span data-ttu-id="2811c-108">"mDNSResponder.exe /?" 실행</span><span class="sxs-lookup"><span data-stu-id="2811c-108">Run “mDNSResponder.exe /?”</span></span> <span data-ttu-id="2811c-109">사용법 인쇄하기</span><span class="sxs-lookup"><span data-stu-id="2811c-109">to print the usage</span></span>
3.  <span data-ttu-id="2811c-110">프로젝트 *dnssd*를 컴파일하면 dnssd.dll이 생성됩니다</span><span class="sxs-lookup"><span data-stu-id="2811c-110">Compile the project *dnssd*, it would generate dnssd.dll</span></span>
4.  <span data-ttu-id="2811c-111">*mDNSUWP* 프로젝트를 컴파일합니다.</span><span class="sxs-lookup"><span data-stu-id="2811c-111">Compile the project *mDNSUWP*.</span></span> <span data-ttu-id="2811c-112">dnssd.dll과 대화하고 자체 dll 및 winmd를 생성하는 UWP 브로커</span><span class="sxs-lookup"><span data-stu-id="2811c-112">It’s a UWP broker that talks to dnssd.dll and will generate its own dll and winmd</span></span>
5.  <span data-ttu-id="2811c-113">mDNSUWP를 사용하기 위한 샘플 UWP 앱인 프로젝트 *mDNSTest*를 컴파일하고 종국적으로 mDNSResponder 서비스로 대화합니다.</span><span class="sxs-lookup"><span data-stu-id="2811c-113">Compile the project *mDNSTest*, which is a sample UWP app to consume mDNSUWP and eventually talks into mDNSResponder service.</span></span>
6.  <span data-ttu-id="2811c-114">이 UWP 앱은 dnssd.dll 및 UWP 브로커에 따라 달라집니다(모든 항목을 UWP appx 폴더에 복사하도록 구성된 스크립트가 있음).</span><span class="sxs-lookup"><span data-stu-id="2811c-114">This UWP app depends on both dnssd.dll and the UWP broker (there is script configured to copy everything into the UWP appx folder)</span></span>
7.  <span data-ttu-id="2811c-115">mDNSTest 배포/시작, ID 설정 및 등록을 클릭하면 응답 코드는 0(SUCCESS)이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2811c-115">Deploy/launch mDNSTest, set an ID and click Register, the respond code should be 0 (SUCCESS)</span></span>
8.  <span data-ttu-id="2811c-116">Bonjour 브라우저를 동시에 실행하면 새(가짜) 디바이스가 나열되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2811c-116">If you run any Bonjour Browser at the same time, the new (fake) device should be listed.</span></span>

![mDNS 등록](media/mDNS/mDNS1.png)

## <a name="resources"></a><span data-ttu-id="2811c-118">리소스</span><span class="sxs-lookup"><span data-stu-id="2811c-118">Resources</span></span>

* <span data-ttu-id="2811c-119">[여기에서](https://go.microsoft.com/fwlink/?linkid=2077676) Windows IoT용 Bonjour 호환 mDNS Responder를 다운로드하세요(샘플 소스).</span><span class="sxs-lookup"><span data-stu-id="2811c-119">Download the Bonjour-compatible mDNS Responder for Windows IoT (sample source) [here](https://go.microsoft.com/fwlink/?linkid=2077676).</span></span>

