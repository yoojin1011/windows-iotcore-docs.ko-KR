---
title: Fiddler 추적 캡처
ms.date: 08/28/2017
ms.topic: article
description: Fiddler를 사용 하 여 Windows IoT Core에서 Fiddler 추적을 캡처하는 방법에 대해 알아봅니다.
keywords: windows iot, Fiddler, 추적, PuTTY, Fiddler 추적
ms.openlocfilehash: 0539365ed4727866d816ad129cef0e904f22b1df
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918252"
---
# <a name="capturing-fiddler-traces-on-windows-iot-core"></a>Windows IoT Core에서 Fiddler 추적 캡처

Fiddler는 웹 트래픽을 디버깅 하기 위한 도구입니다. 확장 및 추가 기능을 사용 하 여 특정 요구에 맞게 사용자 지정할 수 있으며,이 도구는 웹 트래픽과 관련 된 많은 유용한 정보를 제공 하기 때문에 특히 유용 합니다.

## <a name="assumptions"></a>가정 

* 개발자 상자에 [PuTTY](http://www.putty.org/) 하거나 SSH에 대 한 대안을 사용할 수 있습니다.
* 아래 지침은 IoT Core VM을 가정 하지만 *모든* iot core 장치에서 작동 합니다.

## <a name="initial-setup"></a>초기 설정

1. 아직 없는 경우 개발자 상자에 최신 버전의 [Fiddler](http://www.telerik.com/fiddler/) 를 다운로드 하 여 설치 합니다.
2. Fiddler을 시작 하 고 _도구-> Telerik Fiddler 옵션-> HTTPS_ 탭에서 다음 설정을 업데이트 합니다.
    * _캡처 HTTPS 연결_ 확인
    * _HTTPS 트래픽 암호 해독 확인-모든 프로세스에서 >_
    * '에 의해 생성 된 인증서 ' 링크를 클릭 하 고 _makecert.exe 엔진_ (권장 사항:이 변경 내용을 적용 하려면 Fiddler 다시 시작)을 선택 합니다.
    * 그런 다음 _작업 > 통해 루트 인증서를 바탕 화면으로 내보내기_ FiddlerRoot 파일을 내보냅니다.
3. _도구-> Telerik Fiddler 옵션-> Connections_ 탭에서 다음 설정을 업데이트 합니다.
    * _원격 컴퓨터의 연결 허용_ 을 선택 하 여 시스템 프록시 역할을 하도록 Fiddler를 설정 합니다.
    * _Fiddler 수신 대기 포트_ 를 _8888_ 으로 설정 해야 합니다.
  
참고:이 작업을 수행한 후 Fiddler를 다시 시작 하 고 모든 UAC 프롬프트를 수락 해야 합니다.

## <a name="transfer-and-import-fiddler-root-certificate"></a>Fiddler 루트 인증서 전송 및 가져오기
PC를 통해 https 트래픽 라우팅을 디버깅 하려면 Fiddler 루트 인증서를 IoT 이미지 또는 장치로 가져와야 합니다.  이렇게 하려면 다음을 수행합니다.

1. VHD 파일 탑재 (VHD를 마우스 오른쪽 단추로 클릭 하 고 _탑재_선택) 또는 PuTTY (또는 대체 SSH 클라이언트)를 통해 IoT 장치에 연결
2. MainOS 파티션으로 이동 하 고 루트에 _테스트_ 폴더를 만듭니다 (SSH를 통해 _md c:\test_사용).
3. 위에서 생성 한 FiddlerRoot (기본적으로 데스크톱에 있어야 함)를 테스트 폴더 위치로 복사 합니다.
4. VHD를 사용 하는 경우 탑재 된 드라이브를 모두 꺼내면 탑재를 해제 한 다음 HyperV를 통해 IoT Core VM을 시작 합니다.
5. [SSH 세션](../connect-your-device/ssh.md) 을 시작 하 고 관리자 권한으로 로그인 합니다. 
6. SSH 세션에서 c:\test 디렉터리로 이동 합니다.
7. 명령을 통해 Fiddler 루트 인증서를 가져옵니다.
    * `certmgr -add FiddlerRoot.cer -r localmachine -s root`
8. SSH 세션 닫기


## <a name="setup-proxy-on-vm-or-iot-core-device"></a>VM 또는 IoT Core 장치에서 프록시 설정
아래 단계를 수행 하면 Fiddler에서 분석을 위해 네트워크 트래픽을 캡처할 수 있도록 IoT VM 또는 장치에서 PC를 통해 트래픽을 라우팅할 수 있습니다.

1. _Ipconfig_ 를 통해 CMD 콘솔을 사용 하 여 개발 컴퓨터의 IP 확인
2. 새 SSH 세션을 시작 하 고 이번에는 defaultUser로 로그인 합니다 (Username: _Defaultuser_ Pwd: _[blank]_ ).
3. 다음 명령을 통해 프록시를 설정 합니다.
    * `reg add "hkcu\Software\Microsoft\Windows\CurrentVersion\Internet Settings" /v ProxyEnable /t REG_DWORD /d 1`
    * `reg add "hkcu\Software\Microsoft\Windows\CurrentVersion\Internet Settings" /v ProxyServer /t REG_SZ /d [PC IP address]:8888`

아직 실행 중이 아닌 경우 PC에서 Fiddler를 시작 하 고, VM 또는 IoT Core 장치를 다시 시작 하 고, 이제 Fiddler를 통해 트래픽을 라우팅합니다. 

참고: Fiddler에는 https CONNECT가 있지만 데이터가 없는 경우 인증서가 올바르게 설치 되지 않았을 수 있습니다. 위의 _Fiddler 루트 인증서 전송 및 가져오기_ 단계를 놓치지 않았는지 확인 합니다.

또한 프록시를 다시 사용 하도록 설정 하려는 경우 위의 reg 키는 다른 키의 이진 blob에서 캐시 됩니다. 따라서 위의 3 단계에서 방금 추가한 키를 제거 하는 것 외에도 다음 작업을 수행 해야 합니다.

    reg delete "hkcu\Software\Microsoft\Windows\CurrentVersion\Internet Settings\Connections"
    
    
