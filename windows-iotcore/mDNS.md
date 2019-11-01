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
# <a name="getting-started-with-mdns-responder-sample-source"></a>mDNS 응답기 샘플 소스 시작

## <a name="getting-started"></a>시작

1.  프로젝트 *mDNSResponder*를 컴파일하여 서비스인 mDNSResponder.exe를 가져옵니다. .exe를 대상 머신에 복사한 다음, 서비스를 등록하고 실행합니다.
2. "mDNSResponder.exe /?" 실행 사용법 인쇄하기
3.  프로젝트 *dnssd*를 컴파일하면 dnssd.dll이 생성됩니다
4.  *mDNSUWP* 프로젝트를 컴파일합니다. dnssd.dll과 대화하고 자체 dll 및 winmd를 생성하는 UWP 브로커
5.  mDNSUWP를 사용하기 위한 샘플 UWP 앱인 프로젝트 *mDNSTest*를 컴파일하고 종국적으로 mDNSResponder 서비스로 대화합니다.
6.  이 UWP 앱은 dnssd.dll 및 UWP 브로커에 따라 달라집니다(모든 항목을 UWP appx 폴더에 복사하도록 구성된 스크립트가 있음).
7.  mDNSTest 배포/시작, ID 설정 및 등록을 클릭하면 응답 코드는 0(SUCCESS)이어야 합니다.
8.  Bonjour 브라우저를 동시에 실행하면 새(가짜) 디바이스가 나열되어야 합니다.

![mDNS 등록](media/mDNS/mDNS1.png)

## <a name="resources"></a>리소스

* [여기에서](https://go.microsoft.com/fwlink/?linkid=2077676) Windows IoT용 Bonjour 호환 mDNS Responder를 다운로드하세요(샘플 소스).

