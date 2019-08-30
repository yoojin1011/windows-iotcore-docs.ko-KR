---
title: IoT Core 장치에 앱 설치
author: parameshbabu
ms.author: pabab
ms.date: 08/28/2017
ms.topic: article
description: Windows 장치 포털을 사용 하거나 IoT core 이미지의 일부로 앱을 설치 하는 방법에 대해 알아봅니다.
keywords: windows iot, 앱 설치, Windows 장치 포털, 장치
ms.openlocfilehash: 23df6bec04395eb31f066eb3befc84a4ff4bbe56
ms.sourcegitcommit: 5a103405cbc5c61101139aff6aaa709bd4ef9582
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66694160"
---
# <a name="install-your-app-on-an-iot-core-device"></a>IoT Core 장치에 앱 설치
아래에 나열 된 두 가지 방법 중 하나를 사용 하 여 앱을 설치할 수 있습니다.

> [!NOTE]
> Windows 장치 포털을 사용 하 여 앱을 설치 하는 것은 개발자 시나리오에만 해당 됩니다.
> 프로덕션 시나리오에 대 한 프로 비전 패키지를 만들거나 Windows IoT Core 이미지에 앱을 추가 하세요.

## <a name="using-windows-device-portal"></a>Windows 장치 포털 사용

> [!NOTE]
> Windows 장치 포털에는 .appx 또는 .appxbundle가 필요 합니다. SDK 및 도구의 버전 17763부터 응용 프로그램 > 프로젝트의 최소 대상 버전이 17763 이상인 경우 도구에서 [. msix 또는. a n x 번들](https://developercommunity.visualstudio.com/content/problem/391934/makeappx-now-creates-msix-files-instead-of-appx.html)을 만듭니다.
> .Appx 또는 .appxbundle를 만들려면 최소 버전을 17763 보다 작은 버전으로 설정 하거나 [makeappx .exe를 직접 실행](https://docs.microsoft.com/en-us/windows/desktop/appxpkg/make-appx-package--makeappx-exe-#command-line-syntax)합니다. 또한. m 6에서 .appx 또는. m x x로 이름을 바꿀 수 있습니다.

이 방법에서는 사용자가 인터넷에 연결 되어 있는지 확인 해야 합니다. 인터넷에 액세스할 수 없는 경우 오픈 인터넷에 액세스 하는 경로를 포함 하지 않는 장치와 클라이언트 컴퓨터 간에 피어 투 피어 이더넷 연결을 사용할 수도 있습니다. 그러나 후자의 방법으로 앱이 설치 되지만 앱이 스토어 서명 된 경우에는 시작 되지 않습니다.

장치에 응용 프로그램을 설치 하려면 다음을 수행 하세요.

1. IoT 장치에 대 한 [Windows 장치 포털](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal) 을 엽니다.

2. 앱 메뉴 에서 응용 프로그램 파일을 선택 하 고 **설치**를 클릭 하 여 앱을 설치 합니다.

3. **파일 선택** 을 클릭 합니다.

4. .Appx 파일을 선택 하 고 **열기** 를 클릭 합니다.

5. **프레임 워크 패키지 선택 허용을 선택 합니다** .

6. **다음**을 클릭합니다.

7. .Appx의 **종속성** 폴더에 있는 각 항목에 대해 7.1 및 7.2 단계를 반복 합니다.

    7.1 **파일 선택** 클릭

    7.2 depenency를 선택 하 고 **열기** 를 클릭 합니다.

8. 모든 종속성이 추가 되 면 **설치** 를 클릭 합니다.

9. 설치가 완료 될 때까지 기다렸다가 **완료** 를 클릭 합니다.

 ![앱 설치](../media/AppInstaller/install-app.gif)

10. 이제 응용 프로그램이 장치의 응용 프로그램 목록에 표시 됩니다.
 ![앱 설치](../media/AppInstaller/install-app.gif)


## <a name="using-provisioning-package-from-wcd"></a>WCD에서 프로 비전 패키지 사용
앱을 사용 하 여 프로 비전 패키지를 만들고 장치에 프로 비전 패키지를 설치할 수 있습니다. 이 방법은 인터넷에 연결 되지 않은 장치 에서도 작동 하며, 스토어 라이선스 파일을 설치 하는 기본 방법입니다. 예를 들어 장치가 인터넷에 연결 되어 있지 않지만 기본 앱이 스토어 서명 된 UWP 앱 인 팩터리 시나리오를 사용할 수 있습니다.

> [!NOTE]
> PFN (패키지 패밀리 이름)은 앱 **관리 > 앱 id** 의 Windows 개발자 센터에서 찾을 수 있습니다.

1. [Windows 구성 디자이너 열기 (WICD)](https://docs.microsoft.com/windows/configuration/provisioning-packages/provisioning-install-icd)

2. **고급 프로 비전**을 선택 하 고 프로젝트 이름 및 설명을 입력 합니다.

3. 프로젝트 설정에 대해 Windows 10 IoT Core를 선택 하 고 프로 비전 패키지 가져오기를 건너뜁니다.

4. 왼쪽에서 **런타임 설정** 을 확장 하 고 **유니버설 앱 설치 > 사용자 컨텍스트 앱** 을 클릭 합니다.

5. 앱의 패키지 패밀리 이름을 입력 하 고 **추가** 를 클릭 합니다.

6. 새로 추가 된 PFN에서
    - Appx 및 해당 종속성 추가
    - DeploymentOptions를 "대상 응용 프로그램 종료 강제 종료"로 설정 합니다.

7. 스토어 서명 된 앱의 경우 라이선스를 지정 해야 합니다. UserContextAppLicense 아래에서
    - LicenseProductID 추가 (라이선스 XML 파일에서 LicenseID로 사용 가능)
    - 라이선스 xml 확장을 *. m s-windows 스토어 라이선스*로 변경 합니다.
    - 왼쪽에서 라이선스 제품 ID를 선택 하 고 라이선스 파일을 검색 하 여 LicenseInstall 필드를 할당 합니다.

8. 비 스토어 서명 된 앱의 경우 **인증서 > RootCertificates** 에 앱 .cer 파일을 추가 해야 합니다. 

9. 패키지 내보내기

10. [SSH](../connect-your-device/SSH.md) 또는 [Powershell](../connect-your-device/powershell.md)을 사용 하 여 내보낸. Ppkg 파일을 IoT 장치의 _C:\Windows\Provisioning\Packages_ 에 복사 하 고 다시 부팅 합니다. 장치를 다시 부팅 하면 프로 비전 패키지가 처리 되 고 앱이 설치 됩니다.


## <a name="add-the-app-to-the-windows-iot-core-imageffu"></a>Windows IoT Core 이미지 (.ffu)에 앱 추가
Windows IoT Core 이미지 자체의 일부가 되도록 앱을 추가할 수 있습니다.
이 방법은 Oem이 장치에 앱을 설치 하는 데 선호 되는 방법입니다.

[이미지에 앱을 추가](https://docs.microsoft.com/windows-hardware/manufacture/iot/deploy-your-app-with-a-standard-board) 하는 방법 및 [샘플 앱 패키지](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Packages/Appx.IoTCoreDefaultApp)를 참조 하세요.
