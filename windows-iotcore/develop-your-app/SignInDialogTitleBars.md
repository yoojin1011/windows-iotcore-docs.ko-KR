---
title: 대화 상자에서 로그인에 대 한 제목 막대 높이 구성
author: johntasler
ms.author: jtasler
ms.date: 09/13/2018
ms.topic: article
description: Windows 10 IoT Core, 1809 버전에서에서 대화 상자에서 로그인에 대 한 제목 막대 높이 구성 하는 방법에 알아봅니다.
keywords: Windows 10 IoT Core, msa, aad, 제목 표시줄, 닫기, 취소를 지 향하는 방향, 웹, 계정 WebAccountManagement, 로그인, 로그
ms.custom: RS5
ms.openlocfilehash: 69f59b4416c5db39d119994139eba4907035598e
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513317"
---
# <a name="title-bars-for-sign-in-dialogs"></a><span data-ttu-id="93480-104">대화 상자에 제목 표시줄에 대 한 로그인</span><span class="sxs-lookup"><span data-stu-id="93480-104">Title bars for sign in dialogs</span></span>

<span data-ttu-id="93480-105">기본적으로 Windows 10 IoT Core 응용 프로그램 응용 프로그램의 창 주위 프레임을 표시 하지 않습니다 \- 전체 화면을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="93480-105">By design, Windows 10 IoT Core does not display an application frame around your application's window \- you get the full screen.</span></span> <span data-ttu-id="93480-106">그러나 1809 버전에서는 여러 시스템 대화 상자 지정 되었습니다 제목 표시줄 포함 닫기 단추를 취소 하면 대화 상자의 콘텐츠를 취소 단추가 제공 하는 경우에 가능 합니다.</span><span class="sxs-lookup"><span data-stu-id="93480-106">However, in version 1809, several system dialog boxes have been given a title bar containing close button to allow the user to cancel out of them, even when the content of the dialog box provides no cancel button.</span></span>

## <a name="sign-in-dialog-boxes"></a><span data-ttu-id="93480-107">대화 상자에 로그인</span><span class="sxs-lookup"><span data-stu-id="93480-107">Sign in dialog boxes</span></span>

<span data-ttu-id="93480-108">이 기능을 추가 하는 대화 상자는 identity 대화 상자-Microsoft 계정 (MSA)과 Azure Active Directory (AAD)에 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="93480-108">The dialogs that have this feature added are the identity dialogs - for signing in to Microsoft Accounts (MSA) and Azure Active Directory (AAD).</span></span> <span data-ttu-id="93480-109">에 표시 된 대로 응용 프로그램에서 사용할 수 이러한 합니다 [웹 계정 관리 샘플](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WebAccountManagement) 에 [Microsoft UWP 앱 샘플 리포지토리](https://github.com/Microsoft/Windows-universal-samples)합니다.</span><span class="sxs-lookup"><span data-stu-id="93480-109">These can be used in your application as shown in the [Web Account Management sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WebAccountManagement) in the [Microsoft UWP app samples repo](https://github.com/Microsoft/Windows-universal-samples).</span></span>

## <a name="configuring-the-title-bar-height"></a><span data-ttu-id="93480-110">제목 막대 높이 구성</span><span class="sxs-lookup"><span data-stu-id="93480-110">Configuring the title bar height</span></span>

<span data-ttu-id="93480-111">제목 표시줄에 25 픽셀의 기본 높이 및 50 픽셀까지 큰 값으로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93480-111">The title bar has a default height of 25 pixels, and can be set to any greater value up to 50 pixels.</span></span> <span data-ttu-id="93480-112">50 보다 큰 값 50으로 고정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="93480-112">Any value greater than 50 will be clamped to 50.</span></span> <span data-ttu-id="93480-113">높이 25 보다 작을 수는 있지만 닫기 단추 높이 결정할 때 가능한 부작용을 사용자의 환경에는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="93480-113">The height can be less than 25, but consider the possibly negative effect on the user's experience when deciding the height of the close button.</span></span>

<span data-ttu-id="93480-114">예를 들어, 32 픽셀의 제목 막대 높이 설정 하려면 PowerShell에서 수행할 수 있습니다 다음.</span><span class="sxs-lookup"><span data-stu-id="93480-114">As an example, to set the title bar height to 32 pixels, in PowerShell you could do the following:</span></span>
```powershell
# Note that we're only using the variable to make the sample code more narrow
Set-Variable IoTRootKey "HKLM:\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension"
Set-ItemProperty -Path "$IoTRootKey\Experiences\TitleBar" -Name Height -Type DWord -Value 32
```

> [!NOTE]
> <span data-ttu-id="93480-115">OEM 이미지를 만들기 위해 사용 하 여 레지스트리 값을 설정 하기 위한 기본 메커니즘은는 `OEMInput.xml` 파일에 설명 된 [런타임 사용자 지정](/windows-hardware/manufacture/iot/oscustomizations#runtime-customizations)</span><span class="sxs-lookup"><span data-stu-id="93480-115">For creating an OEM image, the preferred mechanism for setting registry values is with the `OEMInput.xml` file discussed in [Runtime customizations](/windows-hardware/manufacture/iot/oscustomizations#runtime-customizations)</span></span>
