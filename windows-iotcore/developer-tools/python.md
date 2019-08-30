---
title: Python
author: paulmon
ms.author: paulmon
ms.date: 08/13/2019
ms.topic: article
description: Windows 10 IoT Core를 실행하는 디바이스에 Python을 설치하는 방법을 알아봅니다.
keywords: windows iot, python
ms.openlocfilehash: 26063863e5fdf7539e3159d4a4809bab3a38fb71
ms.sourcegitcommit: 4272081b5186dada1e61974193e41fcc1c42a1b9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/20/2019
ms.locfileid: "69629376"
---
# <a name="python"></a>Python
Python은 시스템 자동화 및 ML(기계 학습)에 널리 사용되는 스크립트 언어입니다.
[python.org](https://www.python.org/)에서 Python에 대해 자세히 알아볼 수 있습니다.

## <a name="using-python-on-x64-or-x86"></a>x64 또는 x86에서 Python 사용
Windows IoT Core에 Python을 설치하려면 다음을 수행합니다.
1. Python nuget 패키지를 다운로드한 다음, [PowerShell](../connect-your-device/PowerShell.md)을 사용하여 파일을 설치합니다.

    ```powershell
    $python_zip = "https://globalcdn.nuget.org/packages/python.3.7.4.nupkg"
    if($env:PROCESSOR_ARCHITECTURE -ieq "x86") {
        $python_zip = "https://www.nuget.org/api/v2/package/pythonx86/3.7.4"
    }
    Invoke-WebRequest $python_zip -OutFile c:\data\python.zip
    Expand-Archive C:\data\python.zip -DestinationPath c:\python_temp
    move C:\python_temp\tools c:\python
    rd C:\python_temp -Recurse -Force
    del C:\data\python.zip
    ```

2. 시스템 경로에 Python을 추가합니다.

    ```powershell
    cmd /c 'setx PATH "%PATH%";c:\python;c:\python\scripts /M'
    $env:Path += ";c:\python;c:\python\scripts"
    ```

3. pip의 현재 버전이 설치되어 있는지 확인합니다.

    ```powershell
    python -m pip install --upgrade pip
    ```

## <a name="using-python-on-windows-iot-core-arm32"></a>Windows IoT Core ARM32에서 Python 사용

Windows용 Python을 가져오려면 이진 파일을 직접 작성해야 합니다.

1. ARM32용 Python을 빌드합니다.  분기는 3.8 이상이어야 합니다.

    ```cmd
    git clone https://github.com/python/cpython
    cd cpython
    git checkout 3.8
    pcbuild\build.bat -p ARM --no-tkinter
    ```

2. Windows IoT Core ARM32용 Python .zip 파일을 빌드합니다.  PC/레이아웃을 실행하려면 동일한 버전의 Python을 사용해야 합니다. 이 단계에서는 x86용 Python을 빌드하고 이를 사용하여 .zip 파일을 빌드합니다.  .zip 파일에서 표준 라이브러리 테스트를 원하는 경우 `--include-tests` 매개 변수를 추가합니다.

    ```cmd
    REM Build Python for x86 to use for building the .zip file.
    pcbuild\build.bat
    pcbuild\win32\python.exe PC/layout -vv -s "." -b ".\PCBuild\arm32" -t ".\PCBuild\temp" --preset-iot --include-venv --zip ".\PCBuild\arm32\zip\python.zip"

    net use P: \\[ip address]\c$ /user:administrator

    copy .\PCBuild\arm32\zip\python.zip P:\data
    ```

3. [PowerShell](../connect-your-device/PowerShell.md)을 사용하여 디바이스에서 .zip 파일을 추출하고 시스템 경로에 Python을 추가합니다.

    ```powershell
    Expand-Archive C:\data\python.zip -DestinationPath c:\python
    cmd /c 'setx PATH "%PATH%";c:\python;c:\python\scripts /M'
    $env:Path += ";c:\python;c:\python\scripts"
    ```

4. `print('Hello World')`가 작동하는지 확인합니다.

    ```powershell
    python -c "print('Hello World!');quit()"
    ```

## <a name="using-python-on-windows-iot-core-arm64"></a>Windows IoT Core ARM64에서 Python 사용

Windows용 Python을 가져오려면 이진 파일을 직접 작성해야 합니다.

1. ARM32용 Python을 복제하고 `get_externals`를 실행합니다.  분기는 3.8 이상이어야 합니다.

    ```cmd
    git clone https://github.com/python/cpython
    cd cpython
    git checkout 3.8
    pcbuild\get_externals.bat
    cd ..
    ```

2. libffi를 복제하고 빌드합니다.

    ```cmd
    git clone https://github.com/libffi/libffi
    set LIBFFI_SOURCE=%CD%\libffi

    REM Visual Studio 2015 or greater with ARM64 tools installed is required to build Python
    REM the location of VCVARSALL may differ on your machine
    set VCVARSALL="C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\VC\Auxiliary\Build\vcvarsall.bat"

    cd cpython
    if exist c:\cygwin\bin\sh.exe (
        call pcbuild\prepare_libffi.bat -arm64
    ) else (
        call pcbuild\prepare_libffi.bat -arm64 --install-cygwin
    )
    if not exist externals\libffi\arm64\libffi-7.dll echo ERROR: libffi not built! & exit /b 1
    ```

3. ARM64용 Python을 빌드합니다.

    ```cmd
    pcbuild\build.bat -p ARM64 --no-tkinter
    ```

4. Windows IoT Core ARM64용 Python .zip 파일을 빌드합니다.  PC/레이아웃을 실행하려면 동일한 버전의 Python을 사용해야 합니다. 이 단계에서는 x86용 Python을 빌드하고 이를 사용하여 .zip 파일을 빌드합니다.  .zip 파일에서 표준 라이브러리 테스트를 원하는 경우 `--include-tests` 매개 변수를 추가합니다.

    ```cmd
    REM Build Python for x86 to use for building the .zip file.
    pcbuild\build.bat

    REM Map drive to device and copy files using PC/layout
    net use P: \\[ip address]\c$ /user:administrator
    pcbuild\win32\python.exe PC/layout -vv -s "." -b ".\PCBuild\arm64" -t ".\PCBuild\temp" --preset-iot --include-venv --copy P:\python
    ```

3. 시스템 경로에 Python을 추가합니다.

    ```cmd
    setx PATH "%PATH%";c:\python;c:\python\scripts /M
    set PATH=%PATH%;c:\python;c:\python\scripts
    ```

4. `print('Hello World')`가 작동하는지 확인합니다.

    ```cmd
    python -c "print('Hello World!');quit()"
    ```

## <a name="try-out-azure-iot-hub-python-sdks-v2---previewhttpsgithubcomazureazure-iot-sdk-python-preview"></a>[Azure IoT Hub Python SDK v2 - 미리 보기](https://github.com/Azure/azure-iot-sdk-python-preview)를 사용해 보세요.

1. 먼저 SDK를 설치합니다.

    ```cmd
    python -m pip install azure-iot-device
    ```

`pip install`에 대한 출력에서 `Download error on https://pypi.org/simple/pbr/` 오류가 있을 수 있습니다. 이렇게 표시되면 `Set up an IoT Hub and create a Device Identity`로 건너뜁니다.

2. 자주 사용하는 브라우저에서 `https://pypi.org/simple/pbr/`로 이동합니다. 웹 사이트의 인증서를 검사하고 `DigiCert`에서 발급되었는지 확인합니다.

3. `c:\test`라는 디렉터리를 만듭니다.

4. 데스크톱 Windows 머신의 명령 프롬프트에서 `certmgr.msc`를 실행합니다.  

5. treeview에서 `Trusted Root Certification Authorities`로 이동합니다.  노드를 확장하고 `Certificates`를 선택합니다.

6. 오른쪽 창에서 `DigiCert High Assurance EV Root`를 찾아 마우스 오른쪽 단추로 클릭하고 `All Tasks` > `Export`를 선택합니다.  여러 `DigiCert` 인증서가 있고 한 번에 하나씩 각 인증서를 시도하여 확인했습니다.

7. 열리는 대화 상자에서 `Next`를 클릭합니다.

8. `DER encoded binary X.509 (.CER)`를 선택하고(기본값) `Next`를 클릭합니다.

9. `File name:` 편집 상자에 `c:\test\DigiCert High Assurance EV Root.cer`을 입력합니다.

![인증서 내보내기 마법사](../media/Python/global_sign_cert.png)

10. `Next`을 클릭합니다.

11. `Finish`을 클릭합니다.

12. 데스크톱 머신에서 다음 명령을 실행하여 디바이스에 `c:\test\DigiCert High Assurance EV Root.cer`을 복사합니다.

    ```cmd
    net use X: \\host\c$ /user:host\administrator
    md X:\test
    copy "c:\test\GlobalSign Root CA.cer" X:\test
    ```

13. 디바이스에서 [PowerShell](../connect-your-device/PowerShell.md)을 사용하여 루트 저장소로 인증서를 가져옵니다.

    ```cmd
    certmgr -add "c:\test\DigiCert High Assurance EV Root.cer" -s root -r localMachine -c
    certmgr -add "c:\test\GlobalSign Root CA.cer" -s root -r localMachine -c
    ```

14. `azure-iot-device`를 다시 설치합니다.

    ``` cmd
    python -m pip install azure-iot-device --no-color
    ```

15.  `pip install`에 대한 출력에서 `Download error for https://files.pythonhosted.org/` 오류가 있을 수 있습니다.  표시되지 않는 경우 `Set up an IoT Hub and create a Device Identity`로 건너뜁니다.

16. 자주 사용하는 브라우저에서 `https://files.pythonhosted.org/`로 이동합니다. 웹 사이트의 인증서를 검사하고 `GlobalSign`에서 발급되었는지 확인합니다.

17. 데스크톱 머신에서 `GlobalSign Root CA` 인증서를 내보내고 디바이스에서 가져오는 단계를 반복합니다.

18. `azure-iot-device`를 다시 설치합니다.

### <a name="set-up-an-iot-hub-and-create-a-device-identity"></a>IoT Hub 설정 및 디바이스 ID 만들기

19. [Azure CLI](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli?view=azure-cli-latest)를 설치하고(또는 [Azure Cloud Shell](https://shell.azure.com/) 사용) 이를 사용하여 [Azure IoT Hub를 만듭니다](https://docs.microsoft.com/en-us/cli/azure/iot/hub?view=azure-cli-latest#az-iot-hub-create).

    ```powershell
    az iot hub create --resource-group <your resource group> --name <your IoT Hub name>
    ```
    * 이 작업을 수행하는 데 몇 분 정도 걸립니다.

20. Azure CLI에 IoT 확장을 추가한 다음, [디바이스 ID를 등록합니다](https://docs.microsoft.com/en-us/cli/azure/ext/azure-cli-iot-ext/iot/hub/device-identity?view=azure-cli-latest#ext-azure-cli-iot-ext-az-iot-hub-device-identity-create).

    ```powershell
    az extension add --name azure-cli-iot-ext
    az iot hub device-identity create --hub-name <your IoT Hub name> --device-id <your device id>
    ```

21. Azure CLI를 사용하여 [디바이스 연결 문자열 검색](https://docs.microsoft.com/en-us/cli/azure/ext/azure-cli-iot-ext/iot/hub/device-identity?view=azure-cli-latest#ext-azure-cli-iot-ext-az-iot-hub-device-identity-show-connection-string)

    ```powershell
    az iot hub device-identity show-connection-string --device-id <your device id> --hub-name <your IoT Hub name>
    ```

    다음 형식이어야 합니다.
    ```
    HostName=<your IoT Hub name>.azure-devices.net;DeviceId=<your device id>;SharedAccessKey=<some value>
    ```

### <a name="send-a-simple-telemetry-message"></a>간단한 원격 분석 메시지 보내기

22. Azure CLI를 사용하여 IoT Hub에서 [원격 분석에 대한 모니터링 시작](https://docs.microsoft.com/en-us/cli/azure/ext/azure-cli-iot-ext/iot/hub?view=azure-cli-latest#ext-azure-cli-iot-ext-az-iot-hub-monitor-events)

    ```powershell
    az iot hub monitor-events --hub-name <your IoT Hub name> --output table
    ```

23. 디바이스에서 `IOTHUB_DEVICE_CONNECTION_STRING`이라는 환경 변수로 디바이스 연결 문자열을 설정합니다.

    ```cmd
    REM NOTE: there are no quotes
    set IOTHUB_DEVICE_CONNECTION_STRING=<your connection string here>
    ```

24. simple_send_d2c_message.py를 복사하고 디바이스에서 실행합니다.

    ```cmd
    cmd /c "if not exist c:\test md c:\test"
    REM copy simple_send_d2c_message.py from https://github.com/Azure/azure-iot-sdk-python-preview/blob/master/azure-iot-device/samples/simple_send_d2c_message.py to c:\test on the device
    python c:\test\simple_send_d2c_message.py
    ```

## <a name="using-python-in-an-x64-docker-container-on-windows-iot-core"></a>Windows IoT Core의 x64 docker 컨테이너에서 Python 사용

1. 최신 docker를 다운로드하고, 파일을 설치합니다.

    ```powershell
    Invoke-WebRequest https://master.dockerproject.org/windows/x86_64/docker.zip -OutFile c:\data\docker.zip
    Expand-Archive c:\data\docker.zip -DestinationPath c:\data
    move c:\data\docker\docker*exe c:\windows\system32
    Remove-Item c:\data\docker -Recurse -Force
    dockerd --register-service
    net start docker
    ```

2.  Dockerfile 만들기
    ```
    # escape = `
    FROM mcr.microsoft.com/windows/nanoserver:1809-amd64

    # Get Python
    ADD "https://globalcdn.nuget.org/packages/python.3.7.4.nupkg" .\temp\py.zip

    COPY test test
    COPY certmgr.exe c:\windows\system32

    # need admin for setx and certmgr
    USER ContainerAdministrator

    # Extract Python
    RUN tar -xf c:\temp\py.zip -C c:\temp && `
        move c:\temp\tools c:\ && `
        ren tools python && `
        RD c:\temp /s/q && `
        setx PATH "%PATH%";c:\python;c:\python\scripts /M

    RUN dir c:\test\*.cer /s/b > c:\test\certs.txt && `
        for /f "delims==" %i in (c:\test\certs.txt) do certmgr -add "%i" -s root -r localMachine -c < c:\test\1.txt

    USER ContainerUser

    RUN python -m pip install --upgrade pip && `
        python -m pip install azure-iot-device

    CMD cmd /k c:\test\start.cmd
    ```

3. Dockerfile을 디바이스의 c:\docker에 복사합니다. 또한 P:\docker\test에 인증서를 복사합니다.  1.txt는 번호 1 및 carraige 반환이 있는 파일입니다.

    ```cmd
    net use P: \\[device IP address]\c$ /user:administrator
    md P:\docker\test
    copy Dockerfile P:\docker
    copy AppCertificates\*.cer P:\docker\test
    copy 1.txt P:\docker\test
    ```

4.  SSH를 사용하여 디바이스에 연결합니다.  원격 powershell은 대화형 docker 세션에서 작동하지 않습니다.

    ```powershell
    docker build --isolation==process . -t python
    docker run --isolation==process python
    ```

5. Hello World 인쇄

    ```
    python -c "print('Hello Python in Containers!')"
    ```

6. 클라우드를 디바이스 메시지로 테스트하려면 위의 Azure IoT SDK 지침을 참조하세요.

## <a name="additional-python-developer-resources"></a>추가 Python 개발자 리소스
- [Python 개발자 가이드](https://devguide.python.org/setup/#setup)
- [Windows에서 CPython 빌드](https://cpython-core-tutorial.readthedocs.io/en/latest/build_cpython_windows.html)

