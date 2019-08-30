---
title: 범용 드라이버 만들기
author: parameshbabu
ms.author: pabab
ms.date: 08/28/2017
ms.topic: article
description: 장치에서 단일 드라이버 패키지를 만들 수 있도록 유니버설 드라이버를 만드는 방법에 대해 알아봅니다.
keywords: windows iot, 범용 드라이버, 드라이버, Windows 10, UWP
ms.openlocfilehash: 839a742598481e3ff70e3a0ccf1ff072bd62e051
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "60169581"
---
# <a name="universal-driver-creation"></a><span data-ttu-id="5da34-104">범용 드라이버 만들기</span><span class="sxs-lookup"><span data-stu-id="5da34-104">Universal Driver Creation</span></span>

<span data-ttu-id="5da34-105">이 문서에서는 IoT Core 장치에 대 한 범용 드라이버를 만드는 과정을 안내 합니다.</span><span class="sxs-lookup"><span data-stu-id="5da34-105">This document will walk you through the creation of Universal Drivers for your IoT Core device.</span></span>

<span data-ttu-id="5da34-106">유니버설 드라이버를 사용 하면 IoT Core를 포함 하 여 UWP 기반 버전의 Windows 10을 실행 하는 여러 장치 유형 간에 실행 되는 단일 드라이버 패키지를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5da34-106">Universal Drivers enable you to create a single driver package that runs across several device types running UWP-based editions of Windows 10, including IoT Core.</span></span>

<span data-ttu-id="5da34-107">이 드라이버 패키지에는 범용 INF 파일과 여러 바이너리가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5da34-107">This driver package contains a Universal INF file and several binaries.</span></span> <span data-ttu-id="5da34-108">각각에 대 한 요구 사항은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="5da34-108">The requirements for each are as follows:</span></span>
- <span data-ttu-id="5da34-109">유니버설 INF 파일은 [Windows의 UWP 기반 버전에서 지원 되는 INF 구문의 하위 집합만](https://docs.microsoft.com/windows-hardware/drivers/install/using-a-universal-inf-file#which-inf-sections-are-invalid-in-a-universal-inf-file)사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5da34-109">Universal INF files can only use [the subset of INF syntax supported on UWP-based editions of Windows](https://docs.microsoft.com/windows-hardware/drivers/install/using-a-universal-inf-file#which-inf-sections-are-invalid-in-a-universal-inf-file).</span></span> <span data-ttu-id="5da34-110">INF 파일을 작성 하는 동안 [InfVerif 도구](https://docs.microsoft.com/windows-hardware/drivers/devtest/infverif) 를 사용 하 여 파일이 해당 구문을 준수 하는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="5da34-110">While writing your INF file, use the [InfVerif tool](https://docs.microsoft.com/windows-hardware/drivers/devtest/infverif) to verify that the file adheres to that syntax.</span></span>

- <span data-ttu-id="5da34-111">이진 파일은 UWP 기반 버전의 Windows 10에서 지원 되는 장치 드라이버 인터페이스만 사용할 수 있습니다 (설명서 참조 페이지에서 유니버설로 표시 됨). [Kmdf](https://docs.microsoft.com/windows-hardware/drivers/wdf/index), [UMDF 2](https://docs.microsoft.com/windows-hardware/drivers/wdf/getting-started-with-umdf-version-2)또는 WDM (WDM(Windows Driver Model)).</span><span class="sxs-lookup"><span data-stu-id="5da34-111">binaries can only use device driver interfaces supported on UWP-based editions of Windows 10 (marked as Universal on the documentation reference pages): [KMDF](https://docs.microsoft.com/windows-hardware/drivers/wdf/index), [UMDF 2](https://docs.microsoft.com/windows-hardware/drivers/wdf/getting-started-with-umdf-version-2), or the Windows Driver Model (WDM).</span></span> <span data-ttu-id="5da34-112">OneCore 하위 집합에 포함 된 Api를 호출할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5da34-112">They can also only call APIs included in the OneCore Subset.</span></span> <span data-ttu-id="5da34-113">[Apivalidator 도구](https://docs.microsoft.com/windows-hardware/drivers/develop/validating-universal-drivers) 를 사용 하 여 이진 파일이 호출 하는 api가 유효한 지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="5da34-113">Use the [ApiValidator tool](https://docs.microsoft.com/windows-hardware/drivers/develop/validating-universal-drivers) to verify that the APIs your binaries call are valid.</span></span>

<span data-ttu-id="5da34-114">**Visual Studio에서 드라이버 패키지를 만드는**방법을 알아보려면 [드라이버 패키지 만들기](https://docs.microsoft.com/windows-hardware/drivers/develop/creating-a-driver-package) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5da34-114">To learn how to **create a driver package in Visual Studio**, please visit [Creating a Driver Package](https://docs.microsoft.com/windows-hardware/drivers/develop/creating-a-driver-package)</span></span>

<span data-ttu-id="5da34-115">**IoT Core에서 범용 드라이버를 만드는 데 도움이 되는 샘플**을 원하는 경우 [universal driver 샘플](https://developer.microsoft.com/en-us/windows/iot/samples/driverlab) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5da34-115">If you would like **a sample to help you create a Universal Driver on IoT Core**, please visit our [Universal Driver sample](https://developer.microsoft.com/en-us/windows/iot/samples/driverlab)</span></span>

## <a name="additional-universal-driver-resources"></a><span data-ttu-id="5da34-116">추가 범용 드라이버 리소스</span><span class="sxs-lookup"><span data-stu-id="5da34-116">Additional Universal Driver Resources</span></span>

1. <span data-ttu-id="5da34-117">범용 드라이버 패키지를 개발할 때 **디자인 원칙** 및 **모범 사례** 에 대 한 자세한 내용은 [범용 드라이버 시작](https://docs.microsoft.com/windows-hardware/drivers/develop/getting-started-with-universal-drivers) 하기를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5da34-117">For additional details on **design principles** and **best practices** when developing a Universal Driver package, please visit [Getting Started with Universal Drivers](https://docs.microsoft.com/windows-hardware/drivers/develop/getting-started-with-universal-drivers)</span></span>

2. <span data-ttu-id="5da34-118">**유니버설 드라이버를 디버깅**하는 데 도움이 필요한 경우 [유니버설 Windows 드라이버 디버그](https://docs.microsoft.com/windows-hardware/drivers/develop/debugging-a-universal-driver)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5da34-118">For help **debugging your Universal Driver**, please visit [Debugging a Universal Windows driver](https://docs.microsoft.com/windows-hardware/drivers/develop/debugging-a-universal-driver).</span></span>

