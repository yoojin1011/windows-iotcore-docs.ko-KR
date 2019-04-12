---
title: 범용 드라이버 만들기
author: parameshbabu
ms.author: pabab
ms.date: 08/28/2017
ms.topic: article
description: 장치에서 단일 드라이버 패키지를 만들 수 있도록 범용 드라이버를 만드는 방법에 알아봅니다.
keywords: windows iot, 범용 드라이버, 드라이버를 Windows 10 UWP
ms.openlocfilehash: 839a742598481e3ff70e3a0ccf1ff072bd62e051
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512326"
---
# <a name="universal-driver-creation"></a><span data-ttu-id="48958-104">범용 드라이버 만들기</span><span class="sxs-lookup"><span data-stu-id="48958-104">Universal Driver Creation</span></span>

<span data-ttu-id="48958-105">이 문서에서는 IoT Core 장치에 대 한 범용 드라이버 만들기 안내 합니다.</span><span class="sxs-lookup"><span data-stu-id="48958-105">This document will walk you through the creation of Universal Drivers for your IoT Core device.</span></span>

<span data-ttu-id="48958-106">범용 드라이버를 통해 Windows 10 IoT Core를 포함 하 여 UWP 기반 버전을 실행 하는 몇 가지 장치 유형에 서 실행 되는 단일 드라이버 패키지를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="48958-106">Universal Drivers enable you to create a single driver package that runs across several device types running UWP-based editions of Windows 10, including IoT Core.</span></span>

<span data-ttu-id="48958-107">이 드라이버 패키지는 범용 INF 파일 및 몇 가지 바이너리를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="48958-107">This driver package contains a Universal INF file and several binaries.</span></span> <span data-ttu-id="48958-108">각각에 대 한 요구 사항은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="48958-108">The requirements for each are as follows:</span></span>
- <span data-ttu-id="48958-109">범용 INF 파일에만 사용할 수 [UWP 기반 Windows 버전에서 지원 되는 INF 구문 하위 집합](https://docs.microsoft.com/windows-hardware/drivers/install/using-a-universal-inf-file#which-inf-sections-are-invalid-in-a-universal-inf-file)합니다.</span><span class="sxs-lookup"><span data-stu-id="48958-109">Universal INF files can only use [the subset of INF syntax supported on UWP-based editions of Windows](https://docs.microsoft.com/windows-hardware/drivers/install/using-a-universal-inf-file#which-inf-sections-are-invalid-in-a-universal-inf-file).</span></span> <span data-ttu-id="48958-110">INF 파일을 작성 하는 동안 사용 합니다 [InfVerif 도구](https://docs.microsoft.com/windows-hardware/drivers/devtest/infverif) 파일 해당 구문에 부합 하는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="48958-110">While writing your INF file, use the [InfVerif tool](https://docs.microsoft.com/windows-hardware/drivers/devtest/infverif) to verify that the file adheres to that syntax.</span></span>

- <span data-ttu-id="48958-111">이진 파일 (설명서 참조 페이지에 보편적으로 표시) 하는 Windows 10의 UWP 기반 버전에서 지원 되는 장치 드라이버 인터페이스 사용할 수 있습니다. [KMDF](https://docs.microsoft.com/windows-hardware/drivers/wdf/index), [UMDF 2](https://docs.microsoft.com/windows-hardware/drivers/wdf/getting-started-with-umdf-version-2), 또는 Windows Driver Model (WDM).</span><span class="sxs-lookup"><span data-stu-id="48958-111">binaries can only use device driver interfaces supported on UWP-based editions of Windows 10 (marked as Universal on the documentation reference pages): [KMDF](https://docs.microsoft.com/windows-hardware/drivers/wdf/index), [UMDF 2](https://docs.microsoft.com/windows-hardware/drivers/wdf/getting-started-with-umdf-version-2), or the Windows Driver Model (WDM).</span></span> <span data-ttu-id="48958-112">OneCore 하위 집합에 포함 된 Api만 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="48958-112">They can also only call APIs included in the OneCore Subset.</span></span> <span data-ttu-id="48958-113">사용 된 [ApiValidator 도구](https://docs.microsoft.com/windows-hardware/drivers/develop/validating-universal-drivers) 이진 파일 Api를 호출 하는 확인 하려면 유효 합니다.</span><span class="sxs-lookup"><span data-stu-id="48958-113">Use the [ApiValidator tool](https://docs.microsoft.com/windows-hardware/drivers/develop/validating-universal-drivers) to verify that the APIs your binaries call are valid.</span></span>

<span data-ttu-id="48958-114">자세한 방법 **Visual Studio에서 드라이버 패키지를 만들**를 방문 하십시오 [드라이버 패키지 만들기](https://docs.microsoft.com/windows-hardware/drivers/develop/creating-a-driver-package)</span><span class="sxs-lookup"><span data-stu-id="48958-114">To learn how to **create a driver package in Visual Studio**, please visit [Creating a Driver Package](https://docs.microsoft.com/windows-hardware/drivers/develop/creating-a-driver-package)</span></span>

<span data-ttu-id="48958-115">싶다면 **IoT Core에는 범용 드라이버를 만들 수 있도록 샘플**를 방문 하십시오 우리의 [범용 드라이버 샘플](https://developer.microsoft.com/en-us/windows/iot/samples/driverlab)</span><span class="sxs-lookup"><span data-stu-id="48958-115">If you would like **a sample to help you create a Universal Driver on IoT Core**, please visit our [Universal Driver sample](https://developer.microsoft.com/en-us/windows/iot/samples/driverlab)</span></span>

## <a name="additional-universal-driver-resources"></a><span data-ttu-id="48958-116">범용 드라이버 추가 리소스</span><span class="sxs-lookup"><span data-stu-id="48958-116">Additional Universal Driver Resources</span></span>

1. <span data-ttu-id="48958-117">에 대 한 자세한 **디자인 원칙** 하 고 **모범 사례** 범용 드라이버 패키지를 개발할 때 방문 하십시오 [범용 드라이버를 사용 하 여 시작](https://docs.microsoft.com/windows-hardware/drivers/develop/getting-started-with-universal-drivers)</span><span class="sxs-lookup"><span data-stu-id="48958-117">For additional details on **design principles** and **best practices** when developing a Universal Driver package, please visit [Getting Started with Universal Drivers](https://docs.microsoft.com/windows-hardware/drivers/develop/getting-started-with-universal-drivers)</span></span>

2. <span data-ttu-id="48958-118">도움말에 대 한 **범용 드라이버 디버깅**를 방문 하십시오 [유니버설 Windows 드라이버 디버깅](https://docs.microsoft.com/windows-hardware/drivers/develop/debugging-a-universal-driver)합니다.</span><span class="sxs-lookup"><span data-stu-id="48958-118">For help **debugging your Universal Driver**, please visit [Debugging a Universal Windows driver](https://docs.microsoft.com/windows-hardware/drivers/develop/debugging-a-universal-driver).</span></span>

