---
title: IoT Core 장치에 앱 설치
author: parameshbabu
ms.author: pabab
ms.date: 08/28/2017
ms.topic: article
description: Windows Device Portal 사용 하 여 앱을 설치 하는 방법을 알아봅니다 또는 IoT의 일환으로 이미지를 핵심입니다.
keywords: windows iot, 앱 설치, Windows Device Portal 장치
ms.openlocfilehash: 23df6bec04395eb31f066eb3befc84a4ff4bbe56
ms.sourcegitcommit: 5a103405cbc5c61101139aff6aaa709bd4ef9582
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66694160"
---
# <a name="install-your-app-on-an-iot-core-device"></a>IoT Core 장치에 앱 설치
아래 나열 된 두 가지 방법 중 하나를 사용 하 여 앱을 설치할 수 있습니다.

> [!NOTE]
> Windows Device Portal 사용 하 여 앱을 설치 하는 것은 개발자 시나리오에 대해서만 합니다.
> 프로 비전 패키지를 만들거나 프로덕션 시나리오에 대 한 Windows IoT Core 이미지에 앱을 추가 합니다.

## <a name="using-windows-device-portal"></a>Windows Device Portal 사용 하 여

> [!NOTE]
> .appx 또는.appxbundle Windows Device Portal 필요 합니다. 최소 버전 응용 프로그램 프로젝트의 대상으로 하는 경우 버전의 SDK 및 도구 17763부터 > 17763 크거나 도구 만듭니다는 [.msix 또는.msixbundle](https://developercommunity.visualstudio.com/content/problem/391934/makeappx-now-creates-msix-files-instead-of-appx.html)합니다.
> .Appx 또는.appxbundle 집합 17763 보다 이전 버전이 최소 버전을 만들려면 또는 [makeappx.exe를 직접 실행](https://docs.microsoft.com/en-us/windows/desktop/appxpkg/make-appx-package--makeappx-exe-#command-line-syntax)합니다. .msix.appx,.appxbundle를.msixbundle에 이름을 바꿀 수도 있습니다.

이 방법에서는 인터넷에 연결 되어 있는지 확인 해야 합니다. 인터넷에 액세스할 수 없는 경우 장치 및 공개 인터넷 액세스에 대 한 경로 포함 하지 않는 클라이언트 컴퓨터 간의 피어-투-피어 이더넷 연결을 수도 있습니다. 두 번째 방법에 대 한 지속적인이 앱을 설치 하지만 앱 스토어 로그인이 시작 되지 것입니다.

설치 하려면 장치에서 응용 프로그램 다음을 수행 하십시오.

1. 엽니다는 [Windows Device Portal](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal) IoT 장치에 대 한 합니다.

2. 에 **앱** 메뉴에서 앱 파일을 선택 하 고 클릭 하 여 앱을 설치할 **설치**합니다.

3. 클릭 **파일 선택**

4. .Appx 파일을 선택 하 고 클릭 **열기**

5. 확인 **나 프레임 워크 패키지를 선택할 수 있음**

6. **다음**을 클릭합니다.

7. 각 항목에는 **종속성** 7.1 및 7.2에.appx 반복 단계에 대 한 폴더

    7.1 클릭 **파일 선택**

    7.2 depenency.appx를 선택 하 고 클릭 **열기**

8. 모든 종속성 클릭 추가 될 때 **설치**

9. 설치가 완료 될 대기 하 고 클릭 **수행**

 ![앱 설치](../media/AppInstaller/install-app.gif)

10. 이제 응용 프로그램 장치에서 응용 프로그램 목록에 표시 됩니다.
 ![앱 설치](../media/AppInstaller/install-app.gif)


## <a name="using-provisioning-package-from-wcd"></a>WCD에서 프로 비전 패키지를 사용 하 여
앱을 사용 하 여 프로 비전 패키지를 만들고 장치의 프로 비전 패키지를 설치할 수 있습니다. 이 메서드는 인터넷에 연결 되지 않은 장치 에서도 작동 하며 저장소 라이선스 파일을 설치 하기 위한 방법이 더 좋습니다. 예를 들어 여기서는 장치가 인터넷에 연결 되어 있지 않지만 기본 앱은 스토어 로그인 UWP 앱 팩터리 시나리오 지원 합니다.

> [!NOTE]
> 패키지 제품군 이름 (PFN) 아래 Windows 개발자 센터에서 찾을 수 있습니다 **앱 관리 > 앱 Id**

1. 열기 [Windows 구성 디자이너 (WICD)](https://docs.microsoft.com/windows/configuration/provisioning-packages/provisioning-install-icd)

2. 선택 **프로 비전 고급**, 프로젝트 이름 및 설명을 입력 합니다.

3. 프로젝트 설정에 대 한 Windows 10 IoT Core 선택 하 고 프로 비전 패키지 가져오기를 건너뛸합니다

4. 왼쪽 창에서 확장 **런타임 설정을** 클릭 하 고 **유니버설 앱 설치 > 사용자 상황에 맞는 앱**

5. 앱의 패키지 패밀리 이름을 입력 **추가**

6. 새로 추가 된 PFN 아래
    - 추가 된 Appx 및 해당 종속성
    - "Force 대상 응용 프로그램 종료" DeploymentOptions 설정

7. 저장소 서명 앱에 대 한 라이선스를 지정 해야 합니다. UserContextAppLicense, 아래
    - LicenseProductID (라이선스 XML 파일에서 LicenseID로 제공)를 추가 합니다.
    - 라이선스 xml 확장을 변경 *.ms-windows-저장소-라이선스*합니다.
    - 왼쪽 창에서 라이선스 제품 ID를 선택 하 고 LicenseInstall 필드에 할당할 라이선스 파일 찾아보기

8. 서명 된 앱의 스토어 이외의 경우 app.cer로 파일을 추가 해야 **인증서 > RootCertificates** 

9. 패키지 내보내기

10. 내보낸된.ppkg 파일을 복사 _C:\Windows\Provisioning\Packages_ 사용 하 여 IoT 장치 [SSH](../connect-your-device/SSH.md) 하거나 [Powershell](../connect-your-device/powershell.md)) 하 고 다시 부팅 합니다. 장치를 다시 부팅 하는 경우 프로 비전 패키지 처리 되 고 앱이 설치 됩니다.


## <a name="add-the-app-to-the-windows-iot-core-imageffu"></a>Windows IoT Core image(.ffu)에 앱 추가
Windows IoT Core 이미지 자체의 일부가 되도록 앱을 추가할 수 있습니다.
이것은 자신의 장치에 앱을 설치 하는 Oem 위한 기본 방법입니다.

참조 하는 방법 [이미지에 앱 추가](https://docs.microsoft.com/windows-hardware/manufacture/iot/deploy-your-app-with-a-standard-board) 와 [샘플 앱 패키지](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Packages/Appx.IoTCoreDefaultApp)합니다.
