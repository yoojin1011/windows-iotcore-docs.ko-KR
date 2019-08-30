---
title: 드라이버 배포
author: parameshbabu
ms.author: pabab
ms.date: 08/22/2017
ms.topic: article
description: Visual Studio를 사용 하 여 드라이버를 빌드하고 배포 하는 방법을 알아봅니다.
keywords: windows 10 IoT Core, 드라이버 배포
ms.openlocfilehash: aad50718ea44c46d676509fe2c5b408d471afc19
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "60169863"
---
# <a name="driver-deployment"></a>드라이버 배포

Visual Studio를 사용 하 여 Windows 10 IoT Core에 드라이버를 배포 합니다. 

드라이버 개발 단계에서 특정 플랫폼용 드라이버를 컴파일 및 배포할 수 있도록 Visual Studio 드라이버 프로젝트를 구성 합니다. 

이 연습에서는 [gpiokmdfdemo 샘플 드라이버](https://github.com/ms-iot/samples/tree/develop/DriverSamples)를 사용할 수 있습니다.

이미지에 드라이버를 추가 하려는 경우 [IoT 제조 가이드](https://docs.microsoft.com/windows-hardware/manufacture/iot/add-a-driver-to-an-image)의 지침을 참조 하세요.

## <a name="step-1--setup"></a>1 단계: 설정 
___

### <a name="on-the-device"></a>장치에서

* [시작 지침](https://go.microsoft.com/fwlink/?linkid=860461)에 따라 장치에 설치 된 IoTCore 이미지가 있는지 확인 합니다.
* [Powershell](../connect-your-device/PowerShell.md)을 통해 장치에 연결 합니다.

### <a name="on-the-pc"></a>PC에서

* Visual Studio 2017를 설치 했는지 확인 합니다.
* [Windows 드라이버 키트](https://developer.microsoft.com/windows/hardware/windows-driver-kit)를 설치 합니다.  SDK 및 WDK를 설치 해야 합니다.
* 드라이버가 올바르게 서명 되 고 장치에서 실행 될 수 있도록 인증서를 설치 합니다. 관리자 권한 명령 프롬프트에서 아래 나열 된 명령을 실행 합니다.

    1.  `cd c:\Program Files (x86)\Windows Kits\10\Tools\bin\i386` 
    2.  `set WPDKContentRoot=c:\Program Files (x86)\Windows Kits\10`
    3.  `InstallOEMCerts.cmd`
  
* 수정 사항을 적용 하 여 VS에서 F5 배포를 사용 하도록 설정 합니다. 관리자 권한 명령 프롬프트에서 다음 명령을 실행 합니다.

    1.  `cd %TEMP%`(디렉터리를로 `c:\users\<usernsme>\Appdata\Local\Temp`변경 합니다.)
    2.  `md “WdkTempFiles”`"WdkTempFiles" 디렉터리 수동 만들기 도구에서 버그에 대 한 해결 방법 이며 PC에서 *한 번만* 수행 해야 합니다.


## <a name="step-2--provision-device-with-visual-studio"></a>2 단계: Visual Studio를 사용 하 여 장치 프로 비전 
___
* Visual Studio를 열고 **드라이버 > 테스트 > 장치 구성을 선택 하 > 새 장치를 추가** 합니다.
    * 드라이버 메뉴 옵션이 표시 되지 않으면 SDK가 설치 되어 있는지 확인 합니다.

* **장치 구성** 대화 상자에서 
    * 대상 장치의 사용자에 게 친숙 한 표시 이름 입력
    * 장치 유형 = 모바일 선택
    * 표시 된 목록에서 IP 주소를 기준으로 정렬 하 고 IoT 장치의 주소를 찾은 다음 선택 합니다. 두 개의 항목이 있는 경우 0이 아닌 GUID를 가진 항목을 선택 합니다.  행이 선택 되어 있는지 확인 합니다. 파란색을 강조 표시 해야 합니다.
    * 대화 상자 아래쪽에 두 개의 라디오 단추가 있습니다.  장치 프로 비전을 표시 하는 항목을 선택 **하 고 디버거 설정을 선택**합니다.  **다음** 선택

* **디버거 설정 구성**에서 적절 한 설정을 설정 합니다.  다음에 유의하세요.
   * MinnowBoardMax는 디버깅에 네트워크를 사용할 수 있습니다.
       * **네트워크** 연결 유형 사용
       * 포트 선택 – 기본값 사용 가능
       * 일부 키 선택 – 기본값을 사용할 수 있습니다.
       * Visual studio를 실행 하는 컴퓨터의 호스트 IP를 선택 합니다.  Autonet (169.xxx) 주소를 사용 하지 마세요.
       * **다음** 선택
       
  ![디버그 설정 구성](../media/DriverDeployment/confdbgsettings.png)
       
    * Raspberry Pi는 커널 디버깅에 직렬를 사용 합니다.
       *  적절 한 직렬 디버깅 케이블을 PI와 호스트 컴퓨터에 연결 합니다.
       *  연결 형식에 대 한 **직렬** 선택
       *  Raspberry Pi에 적절 한 나머지 매개 변수를 채웁니다.
       *  **다음** 선택

* VS를 통해 WDK가 IoT 장치를 프로 비전 합니다.  TAEF 및 WDTF가 장치에 설치 되 고, 위에 제공 된 설정에 따라 장치가 커널 디버깅에 대해 설정 됩니다.

* 완료 되 면 장치를 다시 부팅할 수 있습니다.  **장치 구성** 의 진행률 화면은 상태를 제공 하 고 IoT 장치에서 설치를 완료 하면 완료 된 것을 보여 줍니다. **마침**을 누릅니다.

![진행률 구성](../media/DriverDeployment/confprogress.png)

* 이제 장치가 프로 비전 되 고 **장치 테스트 구성** 상태에 **드라이버 테스트를 위해 구성** 됨이 표시 됩니다.

![ConfigureDevices](../media/DriverDeployment/ConfigureDevices.png)

## <a name="step-3--configure-visual-studio-driver-project"></a>3 단계: Visual Studio 드라이버 프로젝트 구성
___    
1. 관리자 모드에서 Visual Studio를 시작 하 고 visual studio 드라이버 프로젝트를 엽니다.
2. 대상 플랫폼 버전이 개발 컴퓨터에 설치 된 SDK와 일치 하는지 확인 합니다. 솔루션 탐색기 창에서 프로젝트 속성을 선택 합니다.  일반 구성 속성에서 대상 플랫폼 버전이 개발 컴퓨터에 설치 된 SDK와 일치 하는지 보장 합니다.  제어판의 프로그램 **및 기능 > >** SDK 버전을 확인할 수 있습니다.
3. **Project > Visual C++ > Windows 드라이버 > 새 항목 추가**에서 **패키지 매니페스트** 를 선택 하 고 **추가**를 누릅니다.

![PackageManifest](../media/DriverDeployment/PackageManifest.png)

 `Package.pkg.xml`파일이 프로젝트에 추가 됩니다. 이 파일에서 소유자, 플랫폼, 구성 요소 및 하위 구성 요소 태그를 지정 합니다. 
 
![Pkg-xml](../media/DriverDeployment/Package-pkg-xml.png)
 
4. 프로젝트 속성에서 패키지 버전 번호를 Set **> PackageGen > 버전**으로 설정 합니다. 드라이버의 설치/다시 설치를 수행 해야 할 때마다이 버전 번호를 증가 시켜야 합니다.

![PackageVersion](../media/DriverDeployment/PackageVersion.png)

5. **프로젝트 속성 > 드라이버 서명 > 테스트 인증서**에서 테스트 인증서 (Phone OEM 테스트 인증서)를 선택 합니다.

![DriverSigning](../media/DriverDeployment/DriverTestSigning.png)

6. **드라이버 설치** 로 이동 하 여 **배포** 를 선택 합니다.

![InstallOptions](../media/DriverDeployment/installOptions.png)

* **대상 장치 이름** 드롭다운에서 프로 비전 프로세스에서 위에서 만든 대상을 선택 합니다. **설치/다시** 설치 및 **빠른 다시 설치**에 대 한 두 가지 옵션을 확인 합니다. 옵션을 선택 하 고 **확인**을 클릭 합니다.
* **설치/다시 설치** 는 대상에 드라이버를 처음 설치 하는 데 사용 됩니다.  Windows 업데이트 스택을 사용 하 여 드라이버 패키지를 설치 하 고 몇 분 정도 걸릴 수 있습니다. 이는 INF 파일이 변경 될 때마다 사용 해야 합니다. 
    
> [!TIP]
> 초기 설치 후에이 옵션을 사용 하 여 드라이버를 설치할 때마다 패키지 버전 번호가 증가 해야 합니다.

* **빠른 다시 설치** 는 드라이버를 설치한 후에 사용할 수 있으며 레지스트리에 영향을 주는 드라이버 INF 파일에 대 한 이후 변경 내용이 없습니다.  이 메서드는 설치 프로세스를 건너뛰고, 드라이버와 연결 된 모든 devnodes를 종료 하 고, 드라이버를에 복사 하 고, devnode를 다시 시작 합니다.  몇 초 (< 20 초)가 소요 됩니다.

    
> [!WARNING]
> 이 방법이 반드시 성공 하는 것은 아닙니다. 어떤 이유로 드라이버를 devnode 종료할 수 없는 경우 작업은 실패 합니다.  이는 잘못 된 하드웨어 또는 초기에 잘못 된 드라이버 구현이 원인일 수 있습니다.  이 경우 설치/다시 설치 옵션을 사용 해야 합니다.


이제 Visual Studio 프로젝트가 대상 장치에 드라이버를 빌드하고 배포할 준비가 되었습니다. 샘플 gpiokmdfdemo 드라이버를 사용 하는 경우 ACPI 테이블을 생성 하 고 대상 장치에 복사한 다음 [Visual Studio에서 드라이버 빌드](https://developer.microsoft.com/en-us/windows/iot/samples/driverlab2)의 단계를 수행 해야 합니다.


## <a name="step-4--build-and-deploy-driver"></a>4 단계: 드라이버 빌드 및 배포
___
이 작업은 **F5** 키를 사용 하 고 **배포** 옵션을 사용 하 여 두 가지 방법으로 수행할 수 있습니다. 두 가지 방법으로 드라이버를 빌드하고 배포 (즉, 장치에 설치) 하 고, F5 키를 눌러 Visual Studio 커널 디버거를 설치 되 고 로드 된 드라이버에 연결 합니다. 

일부 사용자는 **배포** 기능을 사용 하 고 다른 커널 디버거 (예: WINDBG 또는 KD)를 연결 하는 것을 선호 합니다.  이를 통해 VS 디버거를 사용 하는 것 보다 더 많은 유연성을 제공할 수 있습니다.

### <a name="deploy"></a>배포
1.  솔루션 탐색기에서 프로젝트를 마우스 오른쪽 단추로 클릭 합니다.
2.  **배포** 선택

![배포](../media/DriverDeployment/deploy.png) 

3.  배포 프로세스를 진행 해야 합니다.  IoT 장치는 배포 후 다시 부팅 되 고 설치가 진행 되는 동안 "기어" 화면을 표시 해야 합니다.

빌드 출력이 출력 창에 표시 됩니다. 배포 상태는 설치가 완료 되 면 장치는 다시 부팅 되 고 VS 출력 화면에는 성공 또는 실패가 표시 됩니다.

### <a name="f5"></a>F5

1.  빌드 창에서 구성이 올바른지 확인 합니다. 현재 빌드 아치는 대상 장치 아치와 동일 합니다.  여기서는 대상 이름의 아치가 중요 합니다.  대상은 메뉴 모음의 보기 상자에 표시 되며, 오른쪽 위를 중심으로 합니다.
2.  **F5**키를 누릅니다.  대상이 빌드, 배포 및 VS Kernel 디버거에 연결 됩니다.

* 다시 부팅 한 후 powershell이 아직 연결 되어 있는지 확인 하 고, 그렇지 않은 경우 powershell `enter-pssession` 명령을 사용 하 여 대상 장치에 다시 연결 합니다.


## <a name="known-issues"></a>알려진 문제
___

### <a name="provisioning-errors"></a>프로 비전 오류
MinnowBoardMax와 상호 작용 하는 동안의 경합 상태는 프로 비전 중에 보고 된 오류가 발생할 수 있습니다.  실제로 프로 비전은 성공 가능성이 높습니다.

**오류 목록:**
 
* 오류: "WDTF를 등록 하는 중" 작업을 완료 하지 못했습니다.
* 오류: "커널 디버거 설정 구성 (다시 부팅 가능)" 작업을 성공적으로 완료 하지 못했습니다.

**해결 방법:** 이러한 오류는 거의 무시 해도 됩니다.

**대해**

**장치 구성 구성 진행률** 대화 상자에 표시 되는 오류는 다음과 같습니다.

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

이 시점에서 **완료** 를 안전 하 게 클릭 한 다음 **적용** 및 **확인**을 수행할 수 있습니다.

이는 결과 로그의 형식이 잘못 되는 경합 상태에서 형성 되는 무해 한 오류입니다. 이는 다음 영역에 있는 로그 파일을 확인 하 여 확인할 수 있습니다.

1. 장치 화면에 표시 된 대로 장치의 IP에 대 한 FTP 연결을 `Data/test/bin/DriverTest/Run` 디렉터리에 엽니다.
예: `ftp://<ip address of device>/Data/test/bin/DriverTest/Run/`

2. 로컬 컴퓨터에 파일을 복사 합니다. `Configuring_computer_settings_(possible_reboot)_identifier.wtl`  로그 파일 이름은 실패 한 작업의 이름과 일치 합니다.
3. 메모장에서 파일을 엽니다.
4. 로그의 아래쪽으로 스크롤합니다.  프로 비전이 성공 했음을 나타내는 다음 텍스트가 표시 됩니다.

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

