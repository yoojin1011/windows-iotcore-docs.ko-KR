---
title: Mdn 응답 자가 샘플 소스 시작
author: saraclay
ms.author: saclayt
ms.date: 02/26/2019
ms.topic: article
description: Mdn 응답 자가 샘플 소스를 사용 하 여 시작 하는 방법에 알아봅니다.
keywords: Windows 10 IoT Core, Mdn 응답자 샘플 소스
ms.openlocfilehash: eacd22bf4d8a93948706e214fd48262c61c59a08
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512278"
---
# <a name="getting-started-with-mdns-responder-sample-source"></a><span data-ttu-id="53fb5-104">Mdn 응답 자가 샘플 소스 시작</span><span class="sxs-lookup"><span data-stu-id="53fb5-104">Getting Started with mDNS Responder Sample Source</span></span>

## <a name="getting-started"></a><span data-ttu-id="53fb5-105">시작</span><span class="sxs-lookup"><span data-stu-id="53fb5-105">Getting started</span></span>

1.  <span data-ttu-id="53fb5-106">프로젝트를 컴파일할 *mDNSResponder* 서비스인 get mDNSResponder.exe 하 합니다.</span><span class="sxs-lookup"><span data-stu-id="53fb5-106">Compile the project *mDNSResponder* to get mDNSResponder.exe, which is a service.</span></span> <span data-ttu-id="53fb5-107">.Exe 대상 컴퓨터에 복사 하 고 서비스 등록을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="53fb5-107">Copy the .exe to the target machine then register the service and run.</span></span>
2. <span data-ttu-id="53fb5-108">Run “mDNSResponder.exe /?”</span><span class="sxs-lookup"><span data-stu-id="53fb5-108">Run “mDNSResponder.exe /?”</span></span> <span data-ttu-id="53fb5-109">인쇄 사용</span><span class="sxs-lookup"><span data-stu-id="53fb5-109">to print the usage</span></span>
3.  <span data-ttu-id="53fb5-110">프로젝트를 컴파일할 *dnssd*, dnssd.dll 생성 됩니다</span><span class="sxs-lookup"><span data-stu-id="53fb5-110">Compile the project *dnssd*, it would generate dnssd.dll</span></span>
4.  <span data-ttu-id="53fb5-111">프로젝트를 컴파일할 *mDNSUWP*합니다.</span><span class="sxs-lookup"><span data-stu-id="53fb5-111">Compile the project *mDNSUWP*.</span></span> <span data-ttu-id="53fb5-112">이 UWP broker dnssd.dll에 설명 하는 자체 dll 및 winmd 생성</span><span class="sxs-lookup"><span data-stu-id="53fb5-112">It’s a UWP broker that talks to dnssd.dll and will generate its own dll and winmd</span></span>
5.  <span data-ttu-id="53fb5-113">프로젝트를 컴파일할 *mDNSTest*, mDNSUWP를 사용 하는 UWP 앱 샘플은 있으며 결국 mDNSResponder 서비스에 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="53fb5-113">Compile the project *mDNSTest*, which is a sample UWP app to consume mDNSUWP and eventually talks into mDNSResponder service.</span></span>
6.  <span data-ttu-id="53fb5-114">UWP 앱이 dnssd.dll와 UWP broker에 따라 달라 집니다 (모든 UWP appx 폴더에 복사 하도록 구성 하는 스크립트는)</span><span class="sxs-lookup"><span data-stu-id="53fb5-114">This UWP app depends on both dnssd.dll and the UWP broker (there is script configured to copy everything into the UWP appx folder)</span></span>
7.  <span data-ttu-id="53fb5-115">MDNSTest 배포/시작, ID를 설정 하 고 등록를 클릭 합니다. 응답 코드에는 0 (성공)를 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="53fb5-115">Deploy/launch mDNSTest, set an ID and click Register, the respond code should be 0 (SUCCESS)</span></span>
8.  <span data-ttu-id="53fb5-116">동시에 모든 Bonjour 브라우저를 실행 하는 경우 새 가짜 장치 나열 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="53fb5-116">If you run any Bonjour Browser at the same time, the new (fake) device should be listed.</span></span>

![Mdn에 대 한 등록](media/mDNS/mDNS1.png)

## <a name="resources"></a><span data-ttu-id="53fb5-118">리소스</span><span class="sxs-lookup"><span data-stu-id="53fb5-118">Resources</span></span>

* <span data-ttu-id="53fb5-119">Bonjour 호환 Mdn 응답자에 대 한 Windows IoT (샘플 원본)를 다운로드 [여기](https://go.microsoft.com/fwlink/?linkid=2077676)합니다.</span><span class="sxs-lookup"><span data-stu-id="53fb5-119">Download the Bonjour-compatible mDNS Responder for Windows IoT (sample source) [here](https://go.microsoft.com/fwlink/?linkid=2077676).</span></span>

