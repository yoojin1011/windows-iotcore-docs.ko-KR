---
title: Intune에 Windows IoT Core 장치 등록
author: msmimart
ms.author: mimart
ms.date: 05/08/2018
ms.topic: article
description: Microsoft Intune 장치 관리 및 Windows IoT를 사용 하 여 장치를 관리 하는 방법에 대해 알아봅니다.
keywords: windows iot, Azure IoT, Intune 장치 관리, 장치 관리
ms.openlocfilehash: 6a82eab36882e6e2cac830e711b2bba6d4fc95bb
ms.sourcegitcommit: 58f66754eecff826756b686b202c8e21d658bb9d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/20/2019
ms.locfileid: "67277800"
---
# <a name="enrolling-windows-iot-core-devices-in-microsoft-intune"></a>Microsoft Intune에서 Windows IoT Core 장치 등록

회사는 다른 모든 관리 되는 장치와 함께 IoT Core 장치를 관리할 수 있습니다. 이렇게 하면 Intune을 사용 하 여 IoT Core, IoT Enterprise 및 기타 Windows 장치를 관리 하는 일관 된 방법을 제공 합니다.

## <a name="how-do-i-enroll-an-iot-core-device-into-intune"></a>Intune에 IoT Core 장치를 등록 어떻게 할까요? 있나요?

Windows IoT core 대시보드를 사용 하 여 장치를 준비한 다음 Windows 구성 디자이너를 사용 하 여 프로 비전 패키지를 만들면 IoT Core 장치의 Intune 등록을 수행할 수 있습니다.

### <a name="change-the-intune-mdm-user-scope-in-azure-ad"></a>Azure AD에서 Intune MDM 사용자 범위 변경

1. [Azure Portal](https://portal.azure.com)에 로그인 한 다음 **Azure Active Directory**를 선택 합니다.
2. **모바일 (MDM 및 MAM)** 을 선택 합니다.

     ![이동성 및 Microsoft Intune 선택](../media/IntuneDeviceEnrollment/iot-ap-mobility-intune.png)

3. **Microsoft Intune**를 선택 합니다. **Microsoft Intune 구성** 페이지에서 **MDM 사용자 범위**옆의 **모두**를 선택 합니다. 이렇게 하면 Azure AD에 가입한 후에 IoT Core 장치 사용자를 Intune에 등록할 수 있습니다.

### <a name="create-a-setup-sd-card-for-the-iot-core-device"></a>IoT Core 장치에 대 한 설치 SD 카드 만들기

1. PC의 카드 판독기에 마이크로 Sd 카드를 삽입 합니다.
     > [!NOTE]
     > 마이크로 Sd 카드는이 프로세스 중에 포맷 되므로 카드의 모든 데이터가 삭제 됩니다.
2. [Windows IoT Core 대시보드](https://docs.microsoft.com/windows/iot-core/connect-your-device/iotdashboard) 로 이동 하 여 대시보드를 다운로드 하 고 설치 합니다.
3. 대시보드를 설치한 후 열고 **새 장치 설정**을 선택 합니다.

     ![Windows IoT Core 대시보드](../media/IntuneDeviceEnrollment/IoT-dashboard-my-devices.png)

4. **장치 이름을**입력 합니다.
5. 새 관리자 암호를 입력 합니다.
6. 장치에 Wi-fi를 사용 하도록 설정 하려면 **Wi-fi 네트워크 연결** 확인란을 선택 합니다. 장치에서 이더넷 네트워크 연결만 사용 하는 경우이를 건너뜁니다.

     ![IoT 대시보드의 wi-fi 확인란](../media/IntuneDeviceEnrollment/IoT-dashboard-wifi-connection.png)

7. **소프트웨어 사용 조건에 동의** 함 확인란을 선택 하 고 **다운로드 및 설치**를 선택 합니다.
8. 확인 메시지가 표시 되 면 SD 카드의 **형식을 지정** 하는 옵션을 선택 합니다.
     > [!NOTE]
     > 설치 중에 **형식** 확인 메시지를 봅니다. 다른 열려 있는 응용 프로그램에서 메시지를 숨길 수 있지만 서식 옵션을 선택 하는 것이 중요 합니다. 드라이브가 올바르게 포맷 되지 않은 경우 부팅이 실패 합니다.
9. **SD 카드가 준비 되었습니다** . 라는 메시지가 나타납니다.

     ![SD 카드 준비 메시지](../media/IntuneDeviceEnrollment/IoT-dashboard-sd-card-ready.png)

10. 이 페이지를 최소화 합니다.  나중에 다시 돌아올 것입니다.

### <a name="create-a-provisioning-package-for-intune-enrollment"></a>Intune 등록을 위한 프로 비전 패키지 만들기

1. Windows [구성 디자이너 설치](https://docs.microsoft.com/windows/configuration/provisioning-packages/provisioning-install-icd)의 단계에 따라 Windows 구성 디자인 앱을 설치 합니다.

2. **Windows 이미징 및 구성 디자이너**를 엽니다.
3. **데스크톱 장치 프로 비전** 을 선택 하 여 프로젝트를 만듭니다.

     ![데스크톱 서비스 프로 비전 선택](../media/IntuneDeviceEnrollment/iot-wcd-provision-desktop-devices.png)

4. **프로젝트 세부 정보** 를 원하는 대로 입력 합니다. 그런 다음 **마침**을 선택 합니다.
5. **계정 관리** 페이지로 이동 하 여 **Azure AD에 등록**을 선택 합니다.
     > [!NOTE]
     > Microsoft Store 또는 Windows ADK (평가 및 배포 키트)에서 앱을 설치 하는 것은 좋은 방법입니다.

     ![Azure AD에서 등록 선택](../media/IntuneDeviceEnrollment/iot-wcd-enroll-in-azure-ad.png)

6. **대량 토큰 만료**옆에 대량 토큰 만료 날짜를 입력 합니다.
7. **대량 토큰 가져오기**를 선택 합니다. Azure AD에 연결 하기 위한 로그인 메시지가 표시 됩니다.

     ![Azure AD 로그인 페이지](../media/IntuneDeviceEnrollment/iot-wcd-sign-in.png)

8. 테 넌 트 사용자 이름 (예: john@mycompany.onmicrosoft.com)과 암호를 입력 합니다.
9. Windows 구성 디자인 앱이 Azure AD 정보에 액세스할 수 있도록 동의 합니다.
10. 페이지의 메시지는 대량 AAD 토큰이 성공적으로 인출 되었음을 보여 줍니다.

     ![대량 토큰 성공 메시지](../media/IntuneDeviceEnrollment/iot-wcd-bulk-token-successful.png)

11. **고급 편집기로 전환**을 선택 하 고 *예*를 선택 합니다.

     ![고급 편집기로 전환 확인 페이지](../media/IntuneDeviceEnrollment/iot-wcd-switch-to-advanced-editor.png)

12. **선택한 사용자 지정**에서 **계정** 설정을 그대로 두고 다른 모든 설정을 제거 합니다.
13. **OOBE**를 선택 하 고 **제거**를 선택 합니다.
14. **Sharedpc** 가 표시 되 면 선택 하 고 **제거**를 선택 합니다.

     ![사용자 지정 제거](../media/IntuneDeviceEnrollment/iot-wcd-select-customizations.png)

15. **내보내기**를 선택한 다음 **프로 비전 패키지**를 선택 합니다.

     ![프로 비전 패키지 선택](../media/IntuneDeviceEnrollment/iot-wcd-export-provisioning-package.png)

16. 다음 페이지에서 기본 설정을 그대로 적용 하 고 **다음**을 선택 합니다.
17. 다시, 다음 페이지에서 기본 설정을 그대로 적용 하 고 다음을 선택 합니다.
18. **프로 비전 패키지** 대상을 변경 하거나 기본 경로를 그대로 두고 **다음**을 선택 합니다.
19. **빌드**를 선택 합니다.
20. 준비가 되 면 파일을 찾을 수 있도록 **출력 위치** 링크를 선택 합니다.

     ![출력 위치 링크](../media/IntuneDeviceEnrollment/iot-wcd-all-done.png)

21. **마침**을 선택 합니다.
22. 파일 탐색기로 이동 하 여 프로 비전 패키지를 IoT Core 장치에 복사 합니다. **C:\windows\provisioning\packages** 폴더의 **mainos** 드라이브 아래 마이크로 sd 카드에 저장 합니다.  이 폴더에 파일을 저장할 수 있는 권한을 부여 해야 합니다.

### <a name="provision-and-enroll-the-iot-core-device-in-intune"></a>Intune에서 IoT Core 장치 프로 비전 및 등록

1. IoT Core 장치에 마이크로 Sd 카드를 삽입 합니다.
2. IoT Core 장치를 켜고 시작 하는 시간을 허용 하 고 표준 화면을 표시 합니다.
3. Azure Portal의 Microsoft Intune 콘솔로 돌아갑니다. 장치가 장치 목록에 표시 됩니다.
     > [!NOTE]
     > 등록을 완료 하는 데 15 분 이상이 걸릴 수 있습니다.

     ![Intune 장치 목록](../media/IntuneDeviceEnrollment/iot-ap-devices-after-enrollment.png)

## <a name="next-steps"></a>다음 단계

- [Intune의 장치 세부 정보를 참조 하세요](https://docs.microsoft.com/intune/device-inventory).
- [장치를 동기화 하 여 Intune에서 최신 정책과 작업을 가져옵니다](https://docs.microsoft.com/intune/device-sync).
- [Intune을 사용 하 여 장치를 원격으로 다시 시작](https://docs.microsoft.com/intune/device-restart)합니다.
