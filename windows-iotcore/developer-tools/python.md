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
# <a name="python"></a><span data-ttu-id="c1a96-104">Python</span><span class="sxs-lookup"><span data-stu-id="c1a96-104">Python</span></span>
<span data-ttu-id="c1a96-105">Python은 시스템 자동화 및 ML(기계 학습)에 널리 사용되는 스크립트 언어입니다.</span><span class="sxs-lookup"><span data-stu-id="c1a96-105">Python is a scripting language that is popular for system automation and machine learning (ML).</span></span>
<span data-ttu-id="c1a96-106">[python.org](https://www.python.org/)에서 Python에 대해 자세히 알아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1a96-106">You can learn more about Python at [python.org](https://www.python.org/).</span></span>

## <a name="using-python-on-x64-or-x86"></a><span data-ttu-id="c1a96-107">x64 또는 x86에서 Python 사용</span><span class="sxs-lookup"><span data-stu-id="c1a96-107">Using Python on x64 or x86</span></span>
<span data-ttu-id="c1a96-108">Windows IoT Core에 Python을 설치하려면 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="c1a96-108">To install Python on Windows IoT Core:</span></span>
1. <span data-ttu-id="c1a96-109">Python nuget 패키지를 다운로드한 다음, [PowerShell](../connect-your-device/PowerShell.md)을 사용하여 파일을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="c1a96-109">Download the Python nuget package, and then install the files using [PowerShell](../connect-your-device/PowerShell.md).</span></span>

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

2. <span data-ttu-id="c1a96-110">시스템 경로에 Python을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="c1a96-110">Add Python to the system path.</span></span>

    ```powershell
    cmd /c 'setx PATH "%PATH%";c:\python;c:\python\scripts /M'
    $env:Path += ";c:\python;c:\python\scripts"
    ```

3. <span data-ttu-id="c1a96-111">pip의 현재 버전이 설치되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="c1a96-111">Ensure that the current version of pip is installed</span></span>

    ```powershell
    python -m pip install --upgrade pip
    ```

## <a name="using-python-on-windows-iot-core-arm32"></a><span data-ttu-id="c1a96-112">Windows IoT Core ARM32에서 Python 사용</span><span class="sxs-lookup"><span data-stu-id="c1a96-112">Using Python on Windows IoT Core ARM32</span></span>

<span data-ttu-id="c1a96-113">Windows용 Python을 가져오려면 이진 파일을 직접 작성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1a96-113">To get Python for Windows you will need to build the binaries yourself.</span></span>

1. <span data-ttu-id="c1a96-114">ARM32용 Python을 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="c1a96-114">Build Python for ARM32.</span></span>  <span data-ttu-id="c1a96-115">분기는 3.8 이상이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1a96-115">The branch must be 3.8 or greater.</span></span>

    ```cmd
    git clone https://github.com/python/cpython
    cd cpython
    git checkout 3.8
    pcbuild\build.bat -p ARM --no-tkinter
    ```

2. <span data-ttu-id="c1a96-116">Windows IoT Core ARM32용 Python .zip 파일을 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="c1a96-116">Build Python .zip file for for Windows IoT Core ARM32.</span></span>  <span data-ttu-id="c1a96-117">PC/레이아웃을 실행하려면 동일한 버전의 Python을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1a96-117">The same version of Python must be used to run PC/layout.</span></span> <span data-ttu-id="c1a96-118">이 단계에서는 x86용 Python을 빌드하고 이를 사용하여 .zip 파일을 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="c1a96-118">This step builds Python for x86 and uses it to build the .zip file(s).</span></span>  <span data-ttu-id="c1a96-119">.zip 파일에서 표준 라이브러리 테스트를 원하는 경우 `--include-tests` 매개 변수를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="c1a96-119">If you want the standard library tests in your .zip file add the `--include-tests` parameter.</span></span>

    ```cmd
    REM Build Python for x86 to use for building the .zip file.
    pcbuild\build.bat
    pcbuild\win32\python.exe PC/layout -vv -s "." -b ".\PCBuild\arm32" -t ".\PCBuild\temp" --preset-iot --include-venv --zip ".\PCBuild\arm32\zip\python.zip"

    net use P: \\[ip address]\c$ /user:administrator

    copy .\PCBuild\arm32\zip\python.zip P:\data
    ```

3. <span data-ttu-id="c1a96-120">[PowerShell](../connect-your-device/PowerShell.md)을 사용하여 디바이스에서 .zip 파일을 추출하고 시스템 경로에 Python을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="c1a96-120">Use [PowerShell](../connect-your-device/PowerShell.md) to extract the .zip file on the device and add Python to the system path.</span></span>

    ```powershell
    Expand-Archive C:\data\python.zip -DestinationPath c:\python
    cmd /c 'setx PATH "%PATH%";c:\python;c:\python\scripts /M'
    $env:Path += ";c:\python;c:\python\scripts"
    ```

4. <span data-ttu-id="c1a96-121">`print('Hello World')`가 작동하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="c1a96-121">Verify that `print('Hello World')` works.</span></span>

    ```powershell
    python -c "print('Hello World!');quit()"
    ```

## <a name="using-python-on-windows-iot-core-arm64"></a><span data-ttu-id="c1a96-122">Windows IoT Core ARM64에서 Python 사용</span><span class="sxs-lookup"><span data-stu-id="c1a96-122">Using Python on Windows IoT Core ARM64</span></span>

<span data-ttu-id="c1a96-123">Windows용 Python을 가져오려면 이진 파일을 직접 작성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1a96-123">To get Python for Windows you will need to build the binaries yourself.</span></span>

1. <span data-ttu-id="c1a96-124">ARM32용 Python을 복제하고 `get_externals`를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c1a96-124">Clone Python for ARM32 and run `get_externals`.</span></span>  <span data-ttu-id="c1a96-125">분기는 3.8 이상이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1a96-125">The branch must be 3.8 or greater.</span></span>

    ```cmd
    git clone https://github.com/python/cpython
    cd cpython
    git checkout 3.8
    pcbuild\get_externals.bat
    cd ..
    ```

2. <span data-ttu-id="c1a96-126">libffi를 복제하고 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="c1a96-126">Clone and build libffi.</span></span>

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

3. <span data-ttu-id="c1a96-127">ARM64용 Python을 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="c1a96-127">Build Python for ARM64.</span></span>

    ```cmd
    pcbuild\build.bat -p ARM64 --no-tkinter
    ```

4. <span data-ttu-id="c1a96-128">Windows IoT Core ARM64용 Python .zip 파일을 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="c1a96-128">Build Python .zip file for for Windows IoT Core ARM64.</span></span>  <span data-ttu-id="c1a96-129">PC/레이아웃을 실행하려면 동일한 버전의 Python을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1a96-129">The same version of Python must be used to run PC/layout.</span></span> <span data-ttu-id="c1a96-130">이 단계에서는 x86용 Python을 빌드하고 이를 사용하여 .zip 파일을 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="c1a96-130">This step builds Python for x86 and uses it to build the .zip file(s).</span></span>  <span data-ttu-id="c1a96-131">.zip 파일에서 표준 라이브러리 테스트를 원하는 경우 `--include-tests` 매개 변수를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="c1a96-131">If you want the standard library tests in your .zip file add the `--include-tests` parameter.</span></span>

    ```cmd
    REM Build Python for x86 to use for building the .zip file.
    pcbuild\build.bat

    REM Map drive to device and copy files using PC/layout
    net use P: \\[ip address]\c$ /user:administrator
    pcbuild\win32\python.exe PC/layout -vv -s "." -b ".\PCBuild\arm64" -t ".\PCBuild\temp" --preset-iot --include-venv --copy P:\python
    ```

3. <span data-ttu-id="c1a96-132">시스템 경로에 Python을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="c1a96-132">Add Python to the system path.</span></span>

    ```cmd
    setx PATH "%PATH%";c:\python;c:\python\scripts /M
    set PATH=%PATH%;c:\python;c:\python\scripts
    ```

4. <span data-ttu-id="c1a96-133">`print('Hello World')`가 작동하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="c1a96-133">Verify that `print('Hello World')` works.</span></span>

    ```cmd
    python -c "print('Hello World!');quit()"
    ```

## <a name="try-out-azure-iot-hub-python-sdks-v2---previewhttpsgithubcomazureazure-iot-sdk-python-preview"></a><span data-ttu-id="c1a96-134">[Azure IoT Hub Python SDK v2 - 미리 보기](https://github.com/Azure/azure-iot-sdk-python-preview)를 사용해 보세요.</span><span class="sxs-lookup"><span data-stu-id="c1a96-134">Try out [Azure IoT Hub Python SDKs v2 - PREVIEW](https://github.com/Azure/azure-iot-sdk-python-preview)</span></span>

1. <span data-ttu-id="c1a96-135">먼저 SDK를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="c1a96-135">First install the SDK.</span></span>

    ```cmd
    python -m pip install azure-iot-device
    ```

<span data-ttu-id="c1a96-136">`pip install`에 대한 출력에서 `Download error on https://pypi.org/simple/pbr/` 오류가 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1a96-136">In the output for the `pip install` there may be errors: `Download error on https://pypi.org/simple/pbr/`.</span></span> <span data-ttu-id="c1a96-137">이렇게 표시되면 `Set up an IoT Hub and create a Device Identity`로 건너뜁니다.</span><span class="sxs-lookup"><span data-stu-id="c1a96-137">If you see this then, otherwise skip to `Set up an IoT Hub and create a Device Identity`:</span></span>

2. <span data-ttu-id="c1a96-138">자주 사용하는 브라우저에서 `https://pypi.org/simple/pbr/`로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="c1a96-138">Navigate to `https://pypi.org/simple/pbr/` in your favorite browser.</span></span> <span data-ttu-id="c1a96-139">웹 사이트의 인증서를 검사하고 `DigiCert`에서 발급되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="c1a96-139">Inspect the web site's certificate and noticed that it issued by `DigiCert`.</span></span>

3. <span data-ttu-id="c1a96-140">`c:\test`라는 디렉터리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c1a96-140">Create a directory named `c:\test`.</span></span>

4. <span data-ttu-id="c1a96-141">데스크톱 Windows 머신의 명령 프롬프트에서 `certmgr.msc`를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c1a96-141">Run `certmgr.msc` from a command prompt on a desktop Windows machine.</span></span>  

5. <span data-ttu-id="c1a96-142">treeview에서 `Trusted Root Certification Authorities`로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="c1a96-142">Navigate to `Trusted Root Certification Authorities` in the treeview.</span></span>  <span data-ttu-id="c1a96-143">노드를 확장하고 `Certificates`를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c1a96-143">Expand the node and choose `Certificates`.</span></span>

6. <span data-ttu-id="c1a96-144">오른쪽 창에서 `DigiCert High Assurance EV Root`를 찾아 마우스 오른쪽 단추로 클릭하고 `All Tasks` > `Export`를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c1a96-144">In the right pane find the `DigiCert High Assurance EV Root`, right-click and select `All Tasks` > `Export`.</span></span>  <span data-ttu-id="c1a96-145">여러 `DigiCert` 인증서가 있고 한 번에 하나씩 각 인증서를 시도하여 확인했습니다.</span><span class="sxs-lookup"><span data-stu-id="c1a96-145">Note that there are multiple `DigiCert` certs and I identified this one by trying each one, one at a time.</span></span>

7. <span data-ttu-id="c1a96-146">열리는 대화 상자에서 `Next`를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c1a96-146">In the dialog that pops up click `Next`.</span></span>

8. <span data-ttu-id="c1a96-147">`DER encoded binary X.509 (.CER)`를 선택하고(기본값) `Next`를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c1a96-147">Select `DER encoded binary X.509 (.CER)` (this should be the default) and click `Next`.</span></span>

9. <span data-ttu-id="c1a96-148">`File name:` 편집 상자에 `c:\test\DigiCert High Assurance EV Root.cer`을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="c1a96-148">In the `File name:` edit box type `c:\test\DigiCert High Assurance EV Root.cer`</span></span>

![인증서 내보내기 마법사](../media/Python/global_sign_cert.png)

10. <span data-ttu-id="c1a96-150">`Next`을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c1a96-150">Click `Next`.</span></span>

11. <span data-ttu-id="c1a96-151">`Finish`을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c1a96-151">Click `Finish`.</span></span>

12. <span data-ttu-id="c1a96-152">데스크톱 머신에서 다음 명령을 실행하여 디바이스에 `c:\test\DigiCert High Assurance EV Root.cer`을 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="c1a96-152">Copy `c:\test\DigiCert High Assurance EV Root.cer` to the device by running the following command on your desktop machine:</span></span>

    ```cmd
    net use X: \\host\c$ /user:host\administrator
    md X:\test
    copy "c:\test\GlobalSign Root CA.cer" X:\test
    ```

13. <span data-ttu-id="c1a96-153">디바이스에서 [PowerShell](../connect-your-device/PowerShell.md)을 사용하여 루트 저장소로 인증서를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c1a96-153">On the device import the certificate into the root store using [PowerShell](../connect-your-device/PowerShell.md).</span></span>

    ```cmd
    certmgr -add "c:\test\DigiCert High Assurance EV Root.cer" -s root -r localMachine -c
    certmgr -add "c:\test\GlobalSign Root CA.cer" -s root -r localMachine -c
    ```

14. <span data-ttu-id="c1a96-154">`azure-iot-device`를 다시 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="c1a96-154">Try to install the `azure-iot-device` again</span></span>

    ``` cmd
    python -m pip install azure-iot-device --no-color
    ```

15.  <span data-ttu-id="c1a96-155">`pip install`에 대한 출력에서 `Download error for https://files.pythonhosted.org/` 오류가 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1a96-155">In the output for the `pip install` there may be errors: `Download error for https://files.pythonhosted.org/`.</span></span>  <span data-ttu-id="c1a96-156">표시되지 않는 경우 `Set up an IoT Hub and create a Device Identity`로 건너뜁니다.</span><span class="sxs-lookup"><span data-stu-id="c1a96-156">If you don't see this then skip to `Set up an IoT Hub and create a Device Identity`</span></span>

16. <span data-ttu-id="c1a96-157">자주 사용하는 브라우저에서 `https://files.pythonhosted.org/`로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="c1a96-157">Navigate to `https://files.pythonhosted.org/` in your favorite browser.</span></span> <span data-ttu-id="c1a96-158">웹 사이트의 인증서를 검사하고 `GlobalSign`에서 발급되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="c1a96-158">Inspect the web site's certificate and noticed that it issued by `GlobalSign`.</span></span>

17. <span data-ttu-id="c1a96-159">데스크톱 머신에서 `GlobalSign Root CA` 인증서를 내보내고 디바이스에서 가져오는 단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="c1a96-159">Repeat the steps to export the `GlobalSign Root CA` certificate from your desktop machine and import it on the device.</span></span>

18. <span data-ttu-id="c1a96-160">`azure-iot-device`를 다시 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="c1a96-160">Try to install the `azure-iot-device` again.</span></span>

### <a name="set-up-an-iot-hub-and-create-a-device-identity"></a><span data-ttu-id="c1a96-161">IoT Hub 설정 및 디바이스 ID 만들기</span><span class="sxs-lookup"><span data-stu-id="c1a96-161">Set up an IoT Hub and create a Device Identity</span></span>

19. <span data-ttu-id="c1a96-162">[Azure CLI](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli?view=azure-cli-latest)를 설치하고(또는 [Azure Cloud Shell](https://shell.azure.com/) 사용) 이를 사용하여 [Azure IoT Hub를 만듭니다](https://docs.microsoft.com/en-us/cli/azure/iot/hub?view=azure-cli-latest#az-iot-hub-create).</span><span class="sxs-lookup"><span data-stu-id="c1a96-162">Install the [Azure CLI](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli?view=azure-cli-latest) (or use the [Azure Cloud Shell](https://shell.azure.com/)) and use it to [create an Azure IoT Hub](https://docs.microsoft.com/en-us/cli/azure/iot/hub?view=azure-cli-latest#az-iot-hub-create).</span></span>

    ```powershell
    az iot hub create --resource-group <your resource group> --name <your IoT Hub name>
    ```
    * <span data-ttu-id="c1a96-163">이 작업을 수행하는 데 몇 분 정도 걸립니다.</span><span class="sxs-lookup"><span data-stu-id="c1a96-163">Note that this operation make take a few minutes.</span></span>

20. <span data-ttu-id="c1a96-164">Azure CLI에 IoT 확장을 추가한 다음, [디바이스 ID를 등록합니다](https://docs.microsoft.com/en-us/cli/azure/ext/azure-cli-iot-ext/iot/hub/device-identity?view=azure-cli-latest#ext-azure-cli-iot-ext-az-iot-hub-device-identity-create).</span><span class="sxs-lookup"><span data-stu-id="c1a96-164">Add the IoT Extension to the Azure CLI, and then [register a device identity](https://docs.microsoft.com/en-us/cli/azure/ext/azure-cli-iot-ext/iot/hub/device-identity?view=azure-cli-latest#ext-azure-cli-iot-ext-az-iot-hub-device-identity-create)</span></span>

    ```powershell
    az extension add --name azure-cli-iot-ext
    az iot hub device-identity create --hub-name <your IoT Hub name> --device-id <your device id>
    ```

21. <span data-ttu-id="c1a96-165">Azure CLI를 사용하여 [디바이스 연결 문자열 검색](https://docs.microsoft.com/en-us/cli/azure/ext/azure-cli-iot-ext/iot/hub/device-identity?view=azure-cli-latest#ext-azure-cli-iot-ext-az-iot-hub-device-identity-show-connection-string)</span><span class="sxs-lookup"><span data-stu-id="c1a96-165">[Retrieve your Device Connection String](https://docs.microsoft.com/en-us/cli/azure/ext/azure-cli-iot-ext/iot/hub/device-identity?view=azure-cli-latest#ext-azure-cli-iot-ext-az-iot-hub-device-identity-show-connection-string) using the Azure CLI</span></span>

    ```powershell
    az iot hub device-identity show-connection-string --device-id <your device id> --hub-name <your IoT Hub name>
    ```

    <span data-ttu-id="c1a96-166">다음 형식이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1a96-166">It should be in the format:</span></span>
    ```
    HostName=<your IoT Hub name>.azure-devices.net;DeviceId=<your device id>;SharedAccessKey=<some value>
    ```

### <a name="send-a-simple-telemetry-message"></a><span data-ttu-id="c1a96-167">간단한 원격 분석 메시지 보내기</span><span class="sxs-lookup"><span data-stu-id="c1a96-167">Send a simple telemetry message</span></span>

22. <span data-ttu-id="c1a96-168">Azure CLI를 사용하여 IoT Hub에서 [원격 분석에 대한 모니터링 시작](https://docs.microsoft.com/en-us/cli/azure/ext/azure-cli-iot-ext/iot/hub?view=azure-cli-latest#ext-azure-cli-iot-ext-az-iot-hub-monitor-events)</span><span class="sxs-lookup"><span data-stu-id="c1a96-168">[Begin monitoring for telemetry](https://docs.microsoft.com/en-us/cli/azure/ext/azure-cli-iot-ext/iot/hub?view=azure-cli-latest#ext-azure-cli-iot-ext-az-iot-hub-monitor-events) on your IoT Hub using the Azure CLI</span></span>

    ```powershell
    az iot hub monitor-events --hub-name <your IoT Hub name> --output table
    ```

23. <span data-ttu-id="c1a96-169">디바이스에서 `IOTHUB_DEVICE_CONNECTION_STRING`이라는 환경 변수로 디바이스 연결 문자열을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c1a96-169">On your device, set the Device Connection String as an enviornment variable called `IOTHUB_DEVICE_CONNECTION_STRING`.</span></span>

    ```cmd
    REM NOTE: there are no quotes
    set IOTHUB_DEVICE_CONNECTION_STRING=<your connection string here>
    ```

24. <span data-ttu-id="c1a96-170">simple_send_d2c_message.py를 복사하고 디바이스에서 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c1a96-170">Copy simple_send_d2c_message.py and run it on the device.</span></span>

    ```cmd
    cmd /c "if not exist c:\test md c:\test"
    REM copy simple_send_d2c_message.py from https://github.com/Azure/azure-iot-sdk-python-preview/blob/master/azure-iot-device/samples/simple_send_d2c_message.py to c:\test on the device
    python c:\test\simple_send_d2c_message.py
    ```

## <a name="using-python-in-an-x64-docker-container-on-windows-iot-core"></a><span data-ttu-id="c1a96-171">Windows IoT Core의 x64 docker 컨테이너에서 Python 사용</span><span class="sxs-lookup"><span data-stu-id="c1a96-171">Using Python in an x64 docker container on Windows IoT Core</span></span>

1. <span data-ttu-id="c1a96-172">최신 docker를 다운로드하고, 파일을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="c1a96-172">Download the newest docker, and install files.</span></span>

    ```powershell
    Invoke-WebRequest https://master.dockerproject.org/windows/x86_64/docker.zip -OutFile c:\data\docker.zip
    Expand-Archive c:\data\docker.zip -DestinationPath c:\data
    move c:\data\docker\docker*exe c:\windows\system32
    Remove-Item c:\data\docker -Recurse -Force
    dockerd --register-service
    net start docker
    ```

2.  <span data-ttu-id="c1a96-173">Dockerfile 만들기</span><span class="sxs-lookup"><span data-stu-id="c1a96-173">Create Dockerfile</span></span>
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

3. <span data-ttu-id="c1a96-174">Dockerfile을 디바이스의 c:\docker에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="c1a96-174">Copy Dockerfile to c:\docker on device.</span></span> <span data-ttu-id="c1a96-175">또한 P:\docker\test에 인증서를 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="c1a96-175">Also copy any certificates to P:\docker\test.</span></span>  <span data-ttu-id="c1a96-176">1.txt는 번호 1 및 carraige 반환이 있는 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="c1a96-176">1.txt is a file with the number 1 and a carraige return.</span></span>

    ```cmd
    net use P: \\[device IP address]\c$ /user:administrator
    md P:\docker\test
    copy Dockerfile P:\docker
    copy AppCertificates\*.cer P:\docker\test
    copy 1.txt P:\docker\test
    ```

4.  <span data-ttu-id="c1a96-177">SSH를 사용하여 디바이스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="c1a96-177">Connect to the device using SSH.</span></span>  <span data-ttu-id="c1a96-178">원격 powershell은 대화형 docker 세션에서 작동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c1a96-178">Remote powershell will not work for an interactive docker session.</span></span>

    ```powershell
    docker build --isolation==process . -t python
    docker run --isolation==process python
    ```

5. <span data-ttu-id="c1a96-179">Hello World 인쇄</span><span class="sxs-lookup"><span data-stu-id="c1a96-179">Print hello world</span></span>

    ```
    python -c "print('Hello Python in Containers!')"
    ```

6. <span data-ttu-id="c1a96-180">클라우드를 디바이스 메시지로 테스트하려면 위의 Azure IoT SDK 지침을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c1a96-180">See Azure IoT SDK directions above to test cloud to device messages.</span></span>

## <a name="additional-python-developer-resources"></a><span data-ttu-id="c1a96-181">추가 Python 개발자 리소스</span><span class="sxs-lookup"><span data-stu-id="c1a96-181">Additional Python Developer Resources</span></span>
- [<span data-ttu-id="c1a96-182">Python 개발자 가이드</span><span class="sxs-lookup"><span data-stu-id="c1a96-182">Python Developer's Guide</span></span>](https://devguide.python.org/setup/#setup)
- [<span data-ttu-id="c1a96-183">Windows에서 CPython 빌드</span><span class="sxs-lookup"><span data-stu-id="c1a96-183">Build CPython on Windows</span></span>](https://cpython-core-tutorial.readthedocs.io/en/latest/build_cpython_windows.html)

