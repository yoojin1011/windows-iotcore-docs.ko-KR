---
title: 로그인 대화 상자에 대 한 제목 표시줄 높이 구성
author: johntasler
ms.author: jtasler
ms.date: 09/13/2018
ms.topic: article
description: Windows 10 IoT Core, 버전 1809에서 로그인 대화 상자에 대 한 제목 표시줄 높이를 구성 하는 방법에 대해 알아봅니다.
keywords: Windows 10 IoT Core, msa, aad, titlebar, 닫기, 취소, 양방향, 웹, 계정, WebAccountManagement, 로그인, 서명
ms.custom: RS5
ms.openlocfilehash: 69f59b4416c5db39d119994139eba4907035598e
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "60169111"
---
# <a name="title-bars-for-sign-in-dialogs"></a>로그인 대화 상자에 대 한 제목 표시줄

기본적으로 Windows 10 IoT Core는 전체 화면을 표시 하는 응용 프로그램의 창 \- 주위에 응용 프로그램 프레임을 표시 하지 않습니다. 그러나 버전 1809에서는 대화 상자의 내용이 취소 단추를 제공 하는 경우에도 사용자가 취소할 수 있도록 닫기 단추가 포함 된 제목 표시줄이 여러 시스템 대화 상자에 제공 되었습니다.

## <a name="sign-in-dialog-boxes"></a>로그인 대화 상자

이 기능이 추가 된 대화 상자는 Microsoft 계정 (MSA)에 로그인 하 고 AAD (Azure Active Directory) 하는 데 사용할 수 있는 id 대화 상자입니다. [MICROSOFT UWP 앱 샘플 리포지토리의](https://github.com/Microsoft/Windows-universal-samples) [웹 계정 관리 샘플](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WebAccountManagement) 에 표시 된 것 처럼 응용 프로그램에서 사용할 수 있습니다.

## <a name="configuring-the-title-bar-height"></a>제목 표시줄 높이 구성

제목 표시줄의 기본 높이는 25 픽셀 이며 최대 50 픽셀의 더 큰 값으로 설정할 수 있습니다. 50 보다 큰 값은 50로 고정 됩니다. 높이는 25 미만이 될 수 있지만 닫기 단추의 높이를 결정할 때 사용자 환경에 부정적인 영향을 주는 것이 좋습니다.

예를 들어 제목 표시줄 높이를 32 픽셀로 설정 하려면 PowerShell에서 다음을 수행할 수 있습니다.
```powershell
# Note that we're only using the variable to make the sample code more narrow
Set-Variable IoTRootKey "HKLM:\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension"
Set-ItemProperty -Path "$IoTRootKey\Experiences\TitleBar" -Name Height -Type DWord -Value 32
```

> [!NOTE]
> OEM 이미지를 만드는 경우 레지스트리 값을 설정 하는 기본 메커니즘은 `OEMInput.xml` [런타임 사용자 지정](/windows-hardware/manufacture/iot/oscustomizations#runtime-customizations) 에 설명 된 파일을 사용 하는 것입니다.
