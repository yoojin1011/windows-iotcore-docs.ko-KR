---
title: Intune에서 Windows IoT Core 장치 등록
author: msmimart
ms.author: mimart
ms.date: 05/08/2018
ms.topic: article
description: Microsoft Intune 장치 관리 및 Windows IoT를 사용 하 여 장치를 관리 하는 방법에 알아봅니다.
keywords: windows iot, Azure IoT 장치를 Intune에서 관리 장치 관리
ms.openlocfilehash: 5d75c64813a3e61f60630abd87185949b63e178b
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512358"
---
# <a name="enrolling-windows-iot-core-devices-in-microsoft-intune"></a>Microsoft Intune에서 Windows IoT Core 장치 등록

회사는 다른 관리 되는 장치를 모두 함께 IoT Core 장치를 관리할 수 있습니다. 이렇게 하면 일관 된 방식으로 IoT Core, IoT Enterprise 및 Intune을 사용 하 여 다른 Windows 장치를 관리할 수 있습니다.

## <a name="how-do-i-enroll-an-iot-core-device-into-intune"></a>IoT Core 장치를 Intune에 등록 하려면 어떻게 해야 하나요?

IoT Core 장치를 Intune 등록 Windows IoT Core 대시보드를 사용 하 여 장치를 준비 하 고 프로 비전 패키지를 만드는 Windows 구성 디자이너를 사용 하 여 수행 됩니다.

### <a name="change-the-intune-mdm-user-scope-in-azure-ad"></a>Azure AD에서 Intune MDM 사용자 범위를 변경 합니다.

1. 에 로그인 합니다 [Azure portal](https://portal.azure.com)를 선택한 후 **Azure Active Directory**합니다.
2. 선택 **이동성 (MDM 및 MAM)** 합니다.


~~~
 ![Selecting Mobility and Microsoft Intune](../media/IntuneDeviceEnrollment/iot-ap-mobility-intune.png)
~~~
1. 선택 **Microsoft Intune**합니다. 에 **Microsoft Intune 구성** 페이지 옆에 **MDM 사용자 범위**를 선택 **모든**합니다. 이렇게 하면 프로그램 IoT Core 장치 사용자는 Azure AD에 가입한 후 Intune에 등록할 수 있습니다.

### <a name="create-a-setup-sd-card-for-the-iot-core-device"></a>IoT Core 장치에 대 한 설치 SD 카드 만들기
1. PC에서 카드 판독기에 microSD 카드를 삽입 합니다. 
     > [!NOTE]
     > MicroSD 카드를 카드에 데이터를 삭제할 수는이 과정에서 포맷 됩니다.
2. 로 이동 [Windows IoT Core 대시보드](https://docs.microsoft.com/windows/iot-core/connect-your-device/iotdashboard) 다운로드 하 고 대시보드를 설치 합니다.
3. 대시보드를 설치한 후 열고 선택 **새 장치 설정**합니다.

     ![Windows IoT Core 대시보드](../media/IntuneDeviceEnrollment/IoT-dashboard-my-devices.png)

4. 입력 **장치 이름**합니다.
5. 새 관리자 암호를 입력 합니다. 
6. 장치의 Wi-fi를 사용 하도록 설정 하려는 경우 선택 합니다 **Wi-fi 네트워크 연결** 확인란을 선택 합니다. 장치는 이더넷 네트워크 연결에만 사용 하는 경우이 건너뜁니다.

     ![IoT 대시보드에서 Wi-fi 확인란](../media/IntuneDeviceEnrollment/IoT-dashboard-wifi-connection.png)

7. 선택 된 **소프트웨어 라이선스 조건에 동의** 확인란을 선택한 후 **다운로드 및 설치**합니다.
8. 옵션을 선택 하는 확인 메시지가 나타나면 **형식** SD 카드. 
     > [!NOTE]
     > 감시 합니다 **형식** 설치 하는 동안 확인 메시지입니다. 다른 열린 응용 프로그램에서 메시지를 숨길 수 없습니다 하지만 형식 옵션을 선택 해야 합니다. 드라이브를 포맷 제대로 되지 부팅 실패 합니다.
9. 메시지 **Your SD 카드가 준비** 나타납니다.

     ![SD 카드에 대 한 준비 메시지](../media/IntuneDeviceEnrollment/IoT-dashboard-sd-card-ready.png)

10. 이 페이지를 최소화 합니다.  에서는 다시 뵙 되도록 합니다.

### <a name="create-a-provisioning-package-for-intune-enrollment"></a>Intune 등록에 대 한 프로 비전 패키지 만들기
1. 단계를 수행 하 여 Windows 구성 디자인 앱을 설치할 [Windows 구성 디자이너 설치](https://docs.microsoft.com/windows/configuration/provisioning-packages/provisioning-install-icd)합니다.

2. 엽니다는 **Windows 이미징 및 구성 디자이너**합니다.
3. 선택할 **데스크톱 장치를 프로 비전** 프로젝트를 만들려면 

     ![프로 비전 데스크톱 서비스를 선택합니다.](../media/IntuneDeviceEnrollment/iot-wcd-provision-desktop-devices.png)

4. 입력 된 **프로젝트 세부 정보** 필요에 따라 합니다. 선택한 **완료**합니다.
5. 로 이동 합니다 **계정 관리** 선택한 페이지 **Azure AD에 등록**합니다.
      > [!NOTE]
     > Microsoft Store 또는 Windows 평가 및 배포 키트 (ADK) 중 하나에서 앱을 설치 해도 괜찮습니다.

     ![Azure AD에 등록 선택](../media/IntuneDeviceEnrollment/iot-wcd-enroll-in-azure-ad.png)

6. 옆에 **대량 토큰 만료**, 대량 토큰 만료 날짜를 입력 합니다.
7. 선택 **대량 토큰 가져오기**합니다. Azure AD에 연결 하는 것에 대 한 로그인 메시지가 표시 됩니다.

     ![Azure AD 로그인 페이지](../media/IntuneDeviceEnrollment/iot-wcd-sign-in.png)

8. 테 넌 트 사용자 이름을 입력 (예를 들어 john@mycompany.onmicrosoft.com) 및 암호입니다.   
9. Windows 구성 디자인 응용 프로그램에서 Azure AD 정보에 액세스할 수 있도록 동의 합니다. 
10. 페이지의 메시지를 대량 AAD 토큰을 성공적으로 가져온 보여 줍니다.

     ![대량 토큰 성공 메시지](../media/IntuneDeviceEnrollment/iot-wcd-bulk-token-successful.png)

11. 선택 **고급 편집기로 전환**를 선택한 후 *예*합니다.

     ![고급 편집기 확인 페이지로 전환 합니다.](../media/IntuneDeviceEnrollment/iot-wcd-switch-to-advanced-editor.png)

12. 아래 **사용자 지정 항목을 선택**를 유지 합니다 **계정** 설정에는 있지만 다른 모든 설정을 제거:
13. 선택 **OOBE**를 선택한 후 **제거**합니다.
14. 하는 경우 **SharedPC** 는 표시를 선택한 후 **제거**합니다.

     ![사용자 지정 제거](../media/IntuneDeviceEnrollment/iot-wcd-select-customizations.png)

15. 선택 **내보낼**를 선택한 후 **프로 비전 패키지**합니다.

     ![프로 비전 패키지를 선택합니다.](../media/IntuneDeviceEnrollment/iot-wcd-export-provisioning-package.png)

16. 다음 페이지에서 기본 설정을 적용 하 고 선택 **다음**합니다.
17. 마찬가지로 다음 페이지에서 기본 설정을 적용 하 고 선택 합니다.
18. 변경 된 **프로 비전 패키지** 대상 또는 두고 기본 경로 선택한 후 **다음**합니다.
19. 선택 **빌드**합니다.
20. 선택 된 **출력 위치** 준비가 되 면.ppkg 파일을 찾을 수 있도록 연결 합니다.

     ![출력 위치 링크](../media/IntuneDeviceEnrollment/iot-wcd-all-done.png)

21. 선택 **완료**합니다.
22. 파일 탐색기로 이동 하 고 IoT Core 장치 프로 비전 패키지를 복사 합니다. 아래의 microSD 카드에 저장 합니다 **MainOS** 드라이브에 **c:\windows\provisioning\packages** 폴더입니다.  이 폴더에 파일을 저장 하는 권한을 부여 해야 합니다.

### <a name="provision-and-enroll-the-iot-core-device-in-intune"></a>프로 비전 하 고 Intune에서 IoT Core 장치 등록
1. IoT Core 장치에 microSD 카드를 삽입 합니다.
2. IoT Core 장치를 켜고 시간을 시작 하 고 표준 화면을 표시 하도록 허용 합니다. 
3. Azure portal에서 Microsoft Intune 콘솔에 반환 합니다. 장치는 장치 목록에 표시 됩니다.
     > [!NOTE]
     > 등록을 완료 하는 데 15 분 이상 걸릴 수 있습니다.

     ![Intune 장치 목록](../media/IntuneDeviceEnrollment/iot-ap-devices-after-enrollment.png)

## <a name="next-steps"></a>다음 단계
- [Intune에서 장치 세부 정보를 참조 하세요.](https://docs.microsoft.com/intune/device-inventory)합니다.
- [최신 정책 및 Intune 사용 하 여 작업을 가져오는 장치 동기화](https://docs.microsoft.com/intune/device-sync)합니다.
- [Intune 사용 하 여 장치를 원격으로 다시 시작](https://docs.microsoft.com/intune/device-restart)합니다.
