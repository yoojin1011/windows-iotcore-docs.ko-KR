---
title: 드라이버 배포
author: parameshbabu
ms.author: pabab
ms.date: 08/22/2017
ms.topic: article
description: 빌드 및 Visual Studio를 사용 하 여 드라이버를 배포 하는 방법에 알아봅니다.
keywords: windows 10 IoT Core, 드라이버 배포
ms.openlocfilehash: aad50718ea44c46d676509fe2c5b408d471afc19
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513750"
---
# <a name="driver-deployment"></a>드라이버 배포

Visual Studio를 사용 하 여 Windows 10 IoT Core 드라이버를 배포 합니다. 

컴파일 및 드라이버 개발 단계는 특정 플랫폼에 대 한 드라이버를 배포할 수 있도록 Visual Studio 드라이버 프로젝트를 구성 합니다. 

이 연습에 사용할 수 있습니다 합니다 [gpiokmdfdemo 샘플 드라이버](https://github.com/ms-iot/samples/tree/develop/DriverSamples)합니다.

이미지에 드라이버를 추가 하려는 경우의 지침을 방문 하십시오 우리의 [IoT 제조 가이드](https://docs.microsoft.com/windows-hardware/manufacture/iot/add-a-driver-to-an-image)합니다.

## <a name="step-1--setup"></a>1 단계: 설치 프로그램 
___

### <a name="on-the-device"></a>장치에서

* 장치에 IoTCore 이미지에 따라 설치 되어 있는지 확인 합니다 [시작 하기 지침이](https://go.microsoft.com/fwlink/?linkid=860461)합니다.
* 통해 장치에 연결할 [Powershell](../connect-your-device/PowerShell.md)합니다.

### <a name="on-the-pc"></a>PC에

* Visual Studio 2017 설치 했는지 확인 합니다.
* 설치 합니다 [Windows 드라이버 키트](https://developer.microsoft.com/windows/hardware/windows-driver-kit)합니다.  SDK 및 WDK를 설치 해야 합니다.
* 드라이버가 올바르게 서명 되 고 장치에서 실행할 수 있도록 인증서를 설치 합니다. 관리자 권한 명령 프롬프트에서 아래 나열 된 명령을 실행 합니다.

    1.  `cd c:\Program Files (x86)\Windows Kits\10\Tools\bin\i386` 
    2.  `set WPDKContentRoot=c:\Program Files (x86)\Windows Kits\10`
    3.  `InstallOEMCerts.cmd`
  
* 적용 VS에서 F5 배포를 사용 하도록 수정 합니다. 관리자 권한 명령 프롬프트에서 다음 명령을 실행 합니다.

    1.  `cd %TEMP%` (디렉터리 변경 됩니다 `c:\users\<usernsme>\Appdata\Local\Temp`)
    2.  `md “WdkTempFiles”` 이 도구에서 버그가 해결 하는 및 수행 하는 데 필요한 "WdkTempFiles" 디렉터리를 수동으로 만듭니다 *한 번만* PC에서.


## <a name="step-2--provision-device-with-visual-studio"></a>2 단계: Visual Studio를 사용 하 여 장치 프로 비전 
___
* Visual Studio를 열고 선택 **드라이버 > 테스트 > 장치 구성 > 새 장치 추가**
    * 드라이버 메뉴 옵션이 표시 되지 않으면 SDK가 설치 되어 있는지 확인 합니다.

* 에 **장치 구성** 대화 상자에서 
    * 사용자를 입력 하면 대상 장치에 대 한 표시 이름
    * 장치 유형 선택 = 모바일
    * 표시 목록에서 IP 주소순으로 정렬 하 고 IoT 장치에 대 한 주소를 찾으려면 선택 합니다. 두 항목의 경우 0이 아닌 GUID 사용 하 여 하나를 선택 합니다.  파란색 강조 표시 해야 하면이 – 행이 선택 되어 있는지 확인
    * 대화 상자의 맨 아래에 두 개의 라디오 단추가 있습니다.  선택 **장치를 프로 비전 하 고 디버거 설정 선택**합니다.  선택 **다음**

* 에 **디버거 설정을 구성**, 설정을 적절 하 게 설정 합니다.  다음에 유의하세요.
   * MinnowBoardMax 디버깅에 대 한 네트워크를 사용할 수 있습니다.
       * 연결 유형을 사용 하 여 **네트워크**
       * 일부 포트를 선택 합니다. – 기본을 사용할 수 있습니다.
       * 일부 키 선택 – 기본을 사용할 수 있습니다.
       * Visual studio를 실행 하는 컴퓨터의 호스트 IP를 선택 합니다.  Autonet (169.xxx) 주소를 사용 하지 마세요.
       * 선택 **다음**
       
  ![디버그 설정 구성](../media/DriverDeployment/confdbgsettings.png)
       
    * Raspberry Pi의 커널 디버깅에 대 한 직렬 사용합니다.
       *  PI 및 호스트 컴퓨터에 적절 한 직렬 디버깅 케이블 연결
       *  선택 **직렬** 연결 형식에 대 한
       *  Raspberry Pi에 대 한 적절 하 게 매개 변수의 나머지를 채웁니다.
       *  선택 **다음**

* VS 통해 WDK 이제 IoT 장치 프로 비전 합니다.  TAEF 고 WDTF은 장치에 설치 하 고 위에 제공 된 설정에 따라 디버깅 커널에 대 한 장치 설정 됩니다.

* 완료 되 면 장치 재부팅 될 수 있습니다.  진행률 화면에는 **장치 구성** 상태를 제공 하 고 IoT 장치 설치 완료 되 면 표시 완료 합니다. 키를 눌러 **완료**합니다.

![구성 진행률](../media/DriverDeployment/confprogress.png)

* 장치는 이제 프로 비전 하며 **장치 테스트 구성을** 상태 표시 **드라이버 테스트를 위해 구성**

![ConfigureDevices](../media/DriverDeployment/ConfigureDevices.png)

## <a name="step-3--configure-visual-studio-driver-project"></a>3 단계: Visual Studio 드라이버 프로젝트 구성
___    
1. 관리자 모드에서 Visual Studio를 시작 하 고 visual studio 드라이버 프로젝트를 엽니다.
2. 대상 플랫폼 버전에는 개발 컴퓨터에 설치 된 SDK와 일치 하는지 확인 합니다. 솔루션 탐색기 창에서 프로젝트 속성을 선택 합니다.  일반 구성 속성에서 개발 컴퓨터에 SDK 설치 대상 플랫폼 버전 일치 항목을 생성 합니다.  SDK의 버전을 확인할 수는 **제어판 > 프로그램 > 프로그램 및 기능**합니다.
3. 아래 **프로젝트 > 새 항목 추가 > Visual C++ > Windows 드라이버**를 선택 **패키지 매니페스트** 누릅니다 **추가**.

![PackageManifest](../media/DriverDeployment/PackageManifest.png)

 `Package.pkg.xml` 파일을 프로젝트에 추가 됩니다. 이 파일의 소유자, 플랫폼, 구성 요소 및 하위 구성 요소 태그를 지정 합니다. 
 
![Package-pkg-xml](../media/DriverDeployment/Package-pkg-xml.png)
 
4. 패키지 버전 번호를 설정 **프로젝트 속성 > PackageGen > 버전**합니다. 드라이버의 설치/다시 설치를 수행 해야 할 때마다이 버전 번호에 증가를 참고 합니다.

![PackageVersion](../media/DriverDeployment/PackageVersion.png)

5. 아래 **프로젝트 속성 > 드라이버 서명 > 테스트 인증서**, 인증서 (Phone OEM 테스트 인증서) 테스트 선택

![DriverSigning](../media/DriverDeployment/DriverTestSigning.png)

6. 로 이동 **드라이버 설치** 선택한 **배포**

![InstallOptions](../media/DriverDeployment/installOptions.png)

* **대상 장치 이름** 드롭다운 대상 프로 비전 프로세스에서 생성 합니다. 에 대 한 두 가지 옵션을 확인할 수 있습니다 **설치 / 다시 설치** 하 고 **빠른 다시 설치**합니다. 선택 옵션 및 클릭 **확인**합니다.
* **설치 / 다시 설치** 대상 하는 드라이버의 초기 설치에 사용 됩니다.  이 Windows 업데이트 스택을 사용 하 여 드라이버 패키지를 설치 하 고 몇 분 정도 걸릴 수 있습니다. INF 파일 변경 될 때마다이 사용 해야 합니다. 
    
> [!TIP]
> 초기 설치 후 드라이버를 설치 하려면이 옵션을 사용 될 때마다 패키지 버전 번호가 증가 해야 합니다.

* **다시 설치 빠른** 드라이버 설치가 시작 된 후 변경 내용이 없습니다 후속 드라이버 INF 파일에 레지스트리를 영향을 줄 수 있습니다.  설치 프로세스를 무시 하 드라이버와 관련 된 모든 devnodes 종료, 드라이버를 복사 및 devnode를 원래 대로 다시 시작 하는이 메서드.  그러면 몇 (< 20) 시간 (초)입니다.

    
> [!WARNING]
> 이 메서드는 devnode 종료 드라이버를 릴리스 하 여야 합니다. 어떤 이유로 작업이 실패 하는 경우 – 되려면 보장 되지 않습니다.  이 하드웨어 오류 또는 잘못 된 드라이버 구현을 초기 발생할 수 있습니다.  설치/다시 설치 옵션은이 경우에 사용 되어야 합니다.


이제 Visual Studio 프로젝트를 빌드하고 대상 장치의 드라이버를 배포할 수 있습니다. ACPI 테이블 및 대상 장치에 복사본을 생성 해야 하는 샘플 gpiokmdfdemo 드라이버를 사용 하는 경우 다음의 단계를 따릅니다 [Visual Studio에서 드라이버를 빌드할](https://developer.microsoft.com/en-us/windows/iot/samples/driverlab2)합니다.


## <a name="step-4--build-and-deploy-driver"></a>4 단계: 빌드 및 드라이버를 배포 합니다.
___
사용 하 여 두 가지 방법으로이 작업을 수행할 수 있습니다 합니다 **F5** 키 및 사용 하 여 합니다 **배포** 옵션입니다. 두 가지 방법으로 드라이버를 빌드 및 배포 (즉, 해당 장치에 설치) F5 설치 및 로드 된 드라이버를 Visual Studio 커널 디버거를 연결 합니다. 

일부 사용자가 선호 하는 **배포** 기능 WinDBG에서 KD 등 다른 커널 디버거를 연결 하 고 있습니다.  이 VS 디버거를 사용 하 여 보다 더 많은 유연성을 제공할 수 있습니다.

### <a name="deploy"></a>배포
1.  솔루션 탐색기에서 프로젝트를 마우스 오른쪽 단추로 클릭
2.  선택 **배포**

![배포](../media/DriverDeployment/deploy.png) 

3.  배포 프로세스를 진행 해야 합니다.  IoT 장치를 배포 후 다시 부팅 됩니다 및 설치가 진행 되는 동안 "기어" 화면을 표시 해야 합니다.

빌드 출력은는 **출력** 상태는 경우 설치 [출력] 창을 창 배포가 완료 되 고 장치 마찬가지로 다시 부팅 됩니다 VS 출력 화면 성공 또는 실패를 표시 합니다.

### <a name="f5"></a>F5

1.  빌드 창에서 있는지 확인 하는 구성이 올바른지 – 현재 빌드 arch 대상 장치 arch 동일 합니다.  이 여기서 아치 대상 이름에는 것이 중요 합니다.  대상 VS에서 위쪽-가운데-오른쪽의 메뉴 모음에서 보기 상자에 표시 됩니다.
2.  키를 눌러 **F5**합니다.  대상 빌드, 배포 및 VS 커널 디버거를 연결 합니다.

* 다시 부팅 하면 확인 되는지 PowerShell을 아직 연결 되어이 고, 그렇지 다시 연결 PowerShell을 사용 하 여 대상 장치로 `enter-pssession` 명령...


## <a name="known-issues"></a>알려진 문제
___

### <a name="provisioning-errors"></a>프로 비전 오류
프로 비전 중 MinnowBoardMax와의 상호 작용 하는 동안 경합 상태가 보고 된 오류가 발생할 수 있습니다.  사실, 프로 비전 가능성이 성공 했습니다.

**오류 목록:**
 
* 오류: 작업 "등록 WDTF" 성공적으로 완료 하지 못했습니다.
* 오류: 작업 "커널 디버거 설정 구성 (재부팅이)"를 성공적으로 완료 하지 못함

**해결 방법:** 이러한 오류는 거의 확실히 무시 됩니다.

**세부 정보:**

에 다음 오류가 표시 됩니다는 **장치 구성 구성 진행률** 대화 상자:

```
Installing necessary components...
Removing TAEF test service
    Task "Removing TAEF test service" completed successfully
Copying required files
    Task "Copying required files" completed successfully
Registering TAEF Test Service
    Task "Registering TAEF Test Service" completed successfully
Starting TAEF Test Service
    Task "Starting TAEF Test Service" completed successfully
Registering WDTF
    Task "Registering WDTF" completed successfully 
Configuring TAEF test service to start automatically
    Task "Configuring TAEF test service to start automatically" completed successfully
Configuring kernel debugger settings (possible reboot)
    ERROR: Task "Configuring kernel debugger settings (possible reboot)" failed to complete successfully. Look at the logs in the driver test group explorer for more details on the failure.
Configuring computer settings (possible reboot)
Waiting for task to complete...
Waiting for task to complete...
    Task "Configuring computer settings (possible reboot)" completed successfully
Computer configuration log file://C:/Users/username/AppData/Roaming/Microsoft/WDKTestInfrastructure/ProvisioningLogs/Driver%20Test%20Computer%20Configuration%log
Failed installing components
```

이 시점에서 클릭할 수 있습니다 안전 하 게 합니다 **완료** 차례로 합니다 **적용** 및 **확인**합니다.

이 형식이 잘못 된 결과 로그를 일으키는 경합 형성 된 심각 하지 않은 오류입니다. 이 다음 영역에서 로그 파일을 보면 확인할 수 있습니다.

1. 장치 화면의 같이 장치의 IP에 대 한 FTP 연결을 엽니다는 `Data/test/bin/DriverTest/Run` 디렉터리입니다.
예:
`ftp://<ip address of device>/Data/test/bin/DriverTest/Run/`

2. 복사를 `Configuring_computer_settings_(possible_reboot)_identifier.wtl` 로컬 컴퓨터에는 파일입니다.  실패 한 작업의 이름과 일치 하는 로그 파일 이름에 있는 참고 합니다.
3. 메모장에서 파일을 엽니다.
4. 로그의 아래쪽으로 스크롤하십시오.  다음 텍스트를 표시 됩니다, 프로 비전 성공적 임을 나타내는입니다.

```
<PFRollup 
    Total="1" 
    Passed="1" 
    Failed="0" 
    Blocked="0" 
    Warned="0" 
    Skipped="0" CA="6191559" LA="6191619" >
    <rti id="2109770915" />
    <ctx id="384048256" />
</PFRollup>
</WTT-Logger>
```

