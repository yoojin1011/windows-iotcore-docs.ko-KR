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
# <a name="getting-started-with-mdns-responder-sample-source"></a>Mdn 응답 자가 샘플 소스 시작

## <a name="getting-started"></a>시작

1.  프로젝트를 컴파일할 *mDNSResponder* 서비스인 get mDNSResponder.exe 하 합니다. .Exe 대상 컴퓨터에 복사 하 고 서비스 등록을 실행 합니다.
2. Run “mDNSResponder.exe /?” 인쇄 사용
3.  프로젝트를 컴파일할 *dnssd*, dnssd.dll 생성 됩니다
4.  프로젝트를 컴파일할 *mDNSUWP*합니다. 이 UWP broker dnssd.dll에 설명 하는 자체 dll 및 winmd 생성
5.  프로젝트를 컴파일할 *mDNSTest*, mDNSUWP를 사용 하는 UWP 앱 샘플은 있으며 결국 mDNSResponder 서비스에 설명 합니다.
6.  UWP 앱이 dnssd.dll와 UWP broker에 따라 달라 집니다 (모든 UWP appx 폴더에 복사 하도록 구성 하는 스크립트는)
7.  MDNSTest 배포/시작, ID를 설정 하 고 등록를 클릭 합니다. 응답 코드에는 0 (성공)를 사용 해야 합니다.
8.  동시에 모든 Bonjour 브라우저를 실행 하는 경우 새 가짜 장치 나열 되어야 합니다.

![Mdn에 대 한 등록](media/mDNS/mDNS1.png)

## <a name="resources"></a>리소스

* Bonjour 호환 Mdn 응답자에 대 한 Windows IoT (샘플 원본)를 다운로드 [여기](https://go.microsoft.com/fwlink/?linkid=2077676)합니다.

