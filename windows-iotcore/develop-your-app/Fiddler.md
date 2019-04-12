---
title: Fiddler 추적 캡처
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Fiddler를 사용 하 여 Windows IoT Core에 Fiddler 추적을 캡처하는 방법을 알아봅니다.
keywords: windows iot, Fiddler, 추적, PuTTY, Fiddler 추적
ms.openlocfilehash: b8bf4fa6390aad9640ad9139a8a164a9c83fcff5
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513286"
---
# <a name="capturing-fiddler-traces-on-windows-iot-core"></a>Windows IoT Core에 Fiddler 추적 캡처

Fiddler는 웹 트래픽을 디버깅을 위한 도구입니다. 확장 및 추가 기능을 사용 하 여 특정 요구 사항에 대 한 사용자 지정할 수 있습니다이 도구는 많은 웹 트래픽에 대 한 유용한 정보를 제공 하기 때문에 특히 유용 합니다.

## <a name="assumptions"></a>가정 

* 있다고 [PuTTY](http://www.putty.org/) 개발자 상자 또는 SSH에 대 한 대안
* 아래 지침에 따라 IoT 코어 VM의 가정 하지만 작동 *모든* IoT Core 장치

## <a name="initial-setup"></a>초기 설치

1. 최신 버전 다운로드 및 설치 [Fiddler](http://www.telerik.com/fiddler/) 아직 없는 경우 개발자 상자에서
2. 아래에 다음 설정을 업데이트 하 고 Fiddler를 시작 _도구에는 Telerik Fiddler 옵션-> HTTPS->_ 탭
    * 확인 _HTTPS 연결 캡처_
    * 확인 _모든 프로세스에서 HTTPS 트래픽 해독->_
    * '인증서에서 생성 된' 링크를 클릭 하 고 선택 _MakeCert 엔진_ (권장 사항: 이 변경 내용을 적용 하려면 Fiddler를 다시 시작)
    * 다음으로 통해 FiddlerRoot.cer 파일을 내보내기 _작업 데스크톱에 루트 인증서 내보내기->_
3. 아래에서 다음 설정을 업데이트할 _도구-> Telerik Fiddler 옵션-> 연결_ 탭:
    * Fiddler를 확인 하 여 시스템 프록시 프록시로 설정 _연결할 수 있도록 원격 컴퓨터_
    * _Fiddler는 포트에서 수신 대기_ 로 설정 해야 _8888_
  
참고: 그러면 Fiddler를 다시 시작 하 고 모든 UAC 프롬프트를 수락 해야 합니다.

## <a name="transfer-and-import-fiddler-root-certificate"></a>전송 및 Fiddler 루트 인증서 가져오기
Https 트래픽 라우팅을 통해 PC를 디버그 하기 위해 IoT 이미지 또는 장치에 Fiddler 루트 인증서를 가져올 해야 합니다.  가상 하드 디스크 파일에 대한 중요 정보를 제공하려면

1. VHD 파일을 탑재할 (선택한 VHD를 마우스 오른쪽 단추로 클릭 _탑재_) 또는 PuTTY 통해 IoT 장치에 연결 (또는 다른 SSH 클라이언트)
2. MainOS 파티션을 이동 하 고 만들기를 _테스트_ 루트 폴더 (SSH를 통해 사용 하 여 _md c:\test_)
3. 위에서 생성 된 FiddlerRoot.cer 복사 (기본적으로 바탕 화면에 이어야 함)를 테스트 폴더 위치
4. VHD를 사용 하는 경우 탑재 된 드라이브 꺼내기에서 분리 하 고 HyperV 통해 IoT 코어 VM 시작
5. 시작을 [SSH 세션](../connect-your-device/ssh.md) 및 관리자 권한으로 로그인 
6. SSH 세션에서 c:\test 디렉터리 이동
7. 명령을 통해 Fiddler 루트 인증서를 가져옵니다.
    * `certmgr -add FiddlerRoot.cer -r localmachine -s root`
8. SSH 세션 닫기


## <a name="setup-proxy-on-vm-or-iot-core-device"></a>VM 또는 IoT Core 장치에 대 한 프록시 설정
아래 단계를 사용 하면 IoT VM 또는 PC 통해 트래픽 라우팅하는 데는 장치에 있으므로 해당 Fiddler 분석에 대 한 네트워크 트래픽을 캡처할 수 있습니다.:

1. 통해 CMD 콘솔을 사용 하 여 개발 컴퓨터의 IP 확인 _ipconfig_
2. 새 SSH 세션을 시작 defaultUser 로그인이이 시간 (사용자 이름: _DefaultAccount_ Pwd: _[공백]_ )
3. 다음 명령을 통해 프록시 설정:
    * `reg add "hkcu\Software\Microsoft\Windows\CurrentVersion\Internet Settings" /v ProxyEnable /t REG_DWORD /d 1`
    * `reg add "hkcu\Software\Microsoft\Windows\CurrentVersion\Internet Settings" /v ProxyServer /t REG_SZ /d [PC IP address]:8888`

아직 실행 하는 경우 PC에서 Fiddler를 시작, VM 또는 IoT Core 장치를 다시 시작 하 고 Fiddler를 통해 트래픽을 이제 라우팅해야 합니다. 

참고: Https 연결 데이터를 제외한 Fiddler에 표시 되 면 인증서를 올바르게 설치 되지 않은 가능성이 했습니다. 누르지 않은 있는지 확인 합니다 _전송 하 고 Fiddler 루트 인증서 가져오기_ 위의 단계입니다.

또한 위의 레지스트리 키에서 다른 키 이진 blob의 캐시는 참고 백오프 프록시를 설정 하려는 경우. 따라서 제거 하는 것 외에도 위의 3 단계에서 방금 추가한 키도 수행 해야 합니다.

    reg delete "hkcu\Software\Microsoft\Windows\CurrentVersion\Internet Settings\Connections"
    
    
