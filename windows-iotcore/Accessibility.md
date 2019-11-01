---
title: Windows 10 IoT의 접근성
ms.date: 03/8/2018
ms.topic: article
description: 접근성에 대해 알아보고 배운 내용을 앞으로 개발할 애플리케이션 또는 디바이스에 적용하는 방법을 살펴보세요.
keywords: Windows 10 IoT Core, Windows 10 IoT Enterprise, 접근성, 색 대비
ms.openlocfilehash: 682541675cf2b59e07bc1596228e169a0f2457c9
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918570"
---
# <a name="an-overview-of-accessibility-for-windows-iot"></a>Windows IoT 접근성의 개요 
 
## <a name="introduction"></a>소개 
접근성은 사람과 애플리케이션 또는 디바이스의 상호 작용에 관계없이 모든 사람들이 애플리케이션 또는 디바이스의 기능을 직관적이고 효율적으로 사용할 수 있게 해줍니다. 
 
접근성과 관련된 여러 버그를 피할 수 있도록 반드시 제품 설계 단계에서 접근성을 고려해야 합니다. 예를 들어 설계 단계에서 사용할 색과 텍스트 크기(및 사용자가 사용자 지정하는 방법)를 고려하면 수많은 고객에게 도움이 될 수 있습니다. 키보드를 사용하는 디바이스의 경우 설계 단계에서 키보드를 사용하여 제품의 모든 기능을 활용하는 방법과 최소한의 키보드 조작으로 가장 자주 사용하는 기능에 액세스하는 방법을 고려해야 합니다.  
 
구현의 관점에서 개발자에게는 다행스럽게도 Windows 플랫폼은 기본적으로 일정 수준의 접근성을 제공하기 위한 수많은 작업을 처리합니다. 예를 들어 표준 컨트롤은 기본적으로 UIA(UI 자동화) API를 통해 프로그래밍 방식으로 액세스할 수 있습니다. 표준 컨트롤을 사용하는 대신 사용자 지정 UI를 빌드하기로 선택하는 경우 UI 접근성을 구현하려면 플랫폼에서 제공하는 표준 컨트롤을 사용하여 앱을 빌드할 때보다 훨씬 많은 시간이 소요될 수 있습니다. 

## <a name="accessibility-testing"></a>접근성 테스트
아래는 애플리케이션을 빌드할 때 사용하면 좋은 도구입니다. 이러한 도구는 사용자 고유의 디자인을 감사할 때 도움이 되지만, 여전히 고대비 및 텍스트 요구 사항 같은 기능을 고려해야 합니다.

### <a name="accscope"></a>AccScope
[AccScope](https://msdn.microsoft.com/library/windows/desktop/Dn433239) 도구를 사용하면 개발자와 테스터가 앱 개발 및 디자인 중 앱 개발 주기의 이후 테스트 단계가 아니라 초기 프로토타입 단계에서 앱의 접근성을 평가할 수 있습니다. 특히 앱에서 내레이터 접근성 시나리오를 테스트하는 데 사용됩니다.

### <a name="inspect"></a>검사
[Inspect](https://msdn.microsoft.com/library/windows/desktop/Dd318521)를 사용하면 원하는 UI 요소를 선택하고 그 접근성 데이터를 볼 수 있습니다. 사용자는 Microsoft UI 자동화 속성 및 컨트롤 패턴을 보고 UI 자동화 트리에서 자동화 요소의 탐색 구조를 테스트할 수 있습니다. UI를 개발할 때 Inspect를 사용하여 접근성 특성이 UI 자동화에 어떻게 표시되는지 확인하세요. 경우에 따라 특성은 기본 XAML 컨트롤에 대해 이미 구현된 UI 자동화 지원에서 제공됩니다. 또 어떤 경우에는 XAML 태그에서 AutomationProperties 연결 속성으로 설정한 특정 값에서 특성이 제공됩니다.

접근성 테스트에 대해 자세히 알아보려면 [접근성 테스트 문서](https://docs.microsoft.com/windows/uwp/design/accessibility/accessibility-testing#inspect)의 전체 목록을 읽어보세요.
 
 
## <a name="accessibility-in-uwp-apps"></a>UWP 앱의 접근성 
Microsoft의 UWP 팀은 UWP 앱을 설계하고 개발할 때 고려할 접근성에 대한 포괄적인 가이드를 만들었습니다. 사용 편의를 위해 아래에 목록을 준비해 두었으며, 보다 자세한 내용은 [접근성 개요](https://docs.microsoft.com/windows/uwp/design/accessibility/accessibility-overview)에서 확인할 수 있습니다. 
 
또한 UI 자동화 API를 소개하는 문서와 프로그래밍 방식 UI 표현에 대해 알아볼 수 있는 도구가 아래에 준비되어 있습니다. 
 
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
 
