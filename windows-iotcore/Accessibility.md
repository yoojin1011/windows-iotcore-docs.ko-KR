---
title: Windows 10 IoT에 대 한 내게 필요한 옵션
author: saraclay
ms.author: saclayt
ms.date: 03/8/2018
ms.topic: article
description: 내게 필요한 옵션 및 다음 응용 프로그램 또는 장치에 이러한 내용을 적용 하는 방법에 알아봅니다.
keywords: Windows 10 IoT Core, Windows 10 IoT Enterprise, 접근성, 색 대비
ms.openlocfilehash: 149c47fc9cae7fb99eb6aa190055c13284c3e197
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513309"
---
# <a name="an-overview-of-accessibility-for-windows-iot"></a>Windows IoT에 대 한 내게 필요한 옵션의 개요 
 
## <a name="introduction"></a>소개 
내게 필요한 옵션을 사용 하면 사용자가 직관적이 고 효율적으로 사용자에 관계 없이 응용 프로그램 또는 장치 제품, 응용 프로그램 또는 장치를 사용 하 여 상호 작용 하는 모든 기능을 활용 하 여 모든 기능입니다. 
 
반드시 많은 잠재적인 접근성 관련 버그를 방지 하는이 처럼 내게 필요한 옵션 제품의 디자인 단계 동안 간주 됩니다. 예를 들어, 디자인 단계에서 사용 된 색 관련 고려 사항 및 텍스트 (및 해당 수를 사용자 지정는 사용자가)의 크기는 유용한 많은 고객에 게 도움이 됩니다. 및 해결 방법 고려해 설계 단계는 키보드를 사용 하 여 장치 키보드 제품, 그리고 가장 적은 수의 키 입력을 사용 하 여 가장 자주 액세스 하지 않는 기능에 액세스 하는 방법의 모든 기능을 활용 하 여 사용할 수 있습니다.  
 
개발자를 위한 구현 관점에서 좋은 소식은 해당 Windows 플랫폼은 기본적으로 일정 수준의 내게 필요한 옵션을 제공 하는 작업의 많은 이미 수행 하는 대로 합니다. 예를 들어, 표준 컨트롤 기본적으로 UI 자동화 (UIA) API 통해 프로그래밍 방식으로 액세스할 수 있습니다. 표준 컨트롤을 사용 하 고 대신 사용자 지정 UI를 빌드할 필요가 선택 하면 UI 액세스 가능성을 확인 하는 데 필요한 작업 단순히 플랫폼에서 제공 하는 표준 컨트롤을 사용 하 여 앱을 빌드하는 것 보다 훨씬 더 많은 시간이 소요 될 수 있습니다. 

## <a name="accessibility-testing"></a>접근성 테스트
다음은 응용 프로그램을 빌드하는 동안 사용 하도록 권장 하는 도구입니다. 이러한 도구는 자신만 디자인을 감사 하는 데 있어 덕분에, 고대비 텍스트 요구 사항 등의 기능에 대 한 계정 해야 계속 note 하십시오.

### <a name="accscope"></a>AccScope
[AccScope](https://msdn.microsoft.com/library/windows/desktop/Dn433239) 도구를 사용하면 개발자와 테스터가 앱 개발 및 디자인 중 앱 개발 주기의 이후 테스트 단계가 아니라 초기 프로토타입 단계에서 앱의 접근성을 평가할 수 있습니다. 특히 앱에서 내레이터 접근성 시나리오를 테스트하는 데 사용됩니다.

### <a name="inspect"></a>검사
[Inspect](https://msdn.microsoft.com/library/windows/desktop/Dd318521)를 사용하면 원하는 UI 요소를 선택하고 그 접근성 데이터를 볼 수 있습니다. 사용자는 Microsoft UI 자동화 속성 및 컨트롤 패턴을 보고 UI 자동화 트리에서 자동화 요소의 탐색 구조를 테스트할 수 있습니다. 내게 필요한 옵션 특성은 UI 자동화에 노출 하는 방법을 확인 하려면 UI를 개발 하는 경우에 검사를 사용 합니다. 경우에 따라 특성은 기본 XAML 컨트롤에 대해 이미 구현된 UI 자동화 지원에서 제공됩니다. 다른 경우에서 AutomationProperties 연결 속성 특성은 XAML 태그에서 설정 된 특정 값에서 가져옵니다.

접근성 테스트에 대해 자세히 알아보려면 하 시겠습니까? 읽기를 [접근성 테스트 문서](https://docs.microsoft.com/windows/uwp/design/accessibility/accessibility-testing#inspect) 전체 목록입니다.
 
 
## <a name="accessibility-in-uwp-apps"></a>UWP 앱의 내게 필요한 옵션 
Microsoft의 UWP 팀에 놓이므로 함께 포괄적인 가이드 UWP 앱 디자인 및 개발을 위한 내게 필요한 옵션. 사용자 편의 위해 아래 목록을 포함 되어 있지만 읽어 자세히도 알아볼 수 있습니다 우리의 [내게 필요한 옵션에 대 한 개요](https://docs.microsoft.com/windows/uwp/design/accessibility/accessibility-overview)합니다. 
 
또한 UI 자동화 API 및 UI 프로그래밍 방식으로 표현 하는 방법에 대 한 설명 하는 데 사용할 수 있는 도구도 소개는 아래에 나와 있습니다. 
 
> [!VIDEO https://www.youtube.com/embed/6b0K2883rXA]

 
| 문서 | 설명 | 
|---------|-------------| 
| [포괄 소프트웨어 디자인](https://docs.microsoft.com/windows/uwp/design/accessibility/designing-inclusive-software) | Windows 10용 UWP 앱을 사용하여 포괄 디자인을 개발하는 방법에 대해 알아보세요.  접근성을 염두에 둔 포괄 소프트웨어를 디자인하고 빌드하세요. | 
| [포괄 Windows 앱 개발](https://docs.microsoft.com/windows/uwp/design/accessibility/developing-inclusive-windows-apps) | 이 문서는 접근성 있는 UWP 앱을 개발하기 위한 로드맵입니다. | 
| [접근성 검사 목록](https://docs.microsoft.com/windows/uwp/design/accessibility/accessibility-checklist) | UWP 앱이 접근 가능한지 확인하는 검사 목록을 제공합니다. | 
| [기본적인 접근성 정보 표시](https://docs.microsoft.com/windows/uwp/design/accessibility/basic-accessibility-information) | 경우에 따라 기본 접근성 정보는 이름, 역할 및 값으로 분류됩니다. 이 항목에서는 보조 기술이 필요로 하는 기본 정보를 앱에 표시하는 데 도움이 되는 코드에 대해 설명합니다. | 
| [키보드 접근성](https://docs.microsoft.com/windows/uwp/design/accessibility/keyboard-accessibility) | 따라서 앱의 키보드 접근성이 좋지 않을 경우 시각 장애나 이동성 문제가 있는 사용자가 앱을 사용하는 데 어려움을 겪거나 아예 사용하지 못할 수 있습니다. | 
| [고대비 테마](https://docs.microsoft.com/windows/uwp/design/accessibility/high-contrast-themes) | 고대비 테마가 활성 상태일 때 UWP 앱을 사용할 수 있도록 하는 데 필요한 단계에 대해 설명합니다. | 
| [접근성 있는 텍스트 요구 사항](https://docs.microsoft.com/windows/uwp/design/accessibility/accessible-text-requirements) | 이 항목에서는 색 및 배경이 필요한 명암비를 충족하도록 하여 앱 텍스트의 접근성에 대한 모범 사례를 설명합니다. 또한 이 항목에서는 UWP 앱의 텍스트 요소에 부여될 수 있는 Microsoft UI 자동화 역할 및 그래픽의 텍스트에 대한 모범 사례를 설명합니다. | 
| [피해야 할 접근성 사례](https://docs.microsoft.com/windows/uwp/design/accessibility/practices-to-avoid) | UWP 앱에 접근성을 구현하려는 경우 피해야 할 사례에 대해 설명합니다. | 
| [사용자 지정 자동화 피어](https://docs.microsoft.com/windows/uwp/design/accessibility/custom-automation-peers) | Microsoft UI 자동화의 자동화 피어 개념과 고유한 사용자 지정 UI 클래스에 대해 자동화 지원을 제공하는 방법을 설명합니다. | 
 
