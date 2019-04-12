---
title: Windows IoT Core 장치 관리
author: parameshbabu
ms.author: pabab
ms.date: 08/28/2017
ms.topic: article
description: Windows 10 IoT Core 장치를 관리 하는 다른 방법에 알아봅니다.
keywords: windows iot, windows iot, Azure DM, Azure Hub, Azure IoT 장치 관리
ms.openlocfilehash: dbcc6858ee32ce9eb8b33c3d1831a6581a8fa3c7
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513710"
---
# <a name="managing-windows-iot-core-devices"></a>Windows IoT Core 장치 관리

인증서 기반 등록을 지 원하는 기존의 OMA DM MDM 서버를 사용 하 여 또는 Azure IoT Hub 장치 관리를 사용 하 여 Windows 10 IoT Core 장치를 관리할 수 있습니다.  

 _MDM 및 Windows 10에 대 한 자세한 내용은 곧 [여기](https://msdn.microsoft.com/library/windows/hardware/dn914769(v=vs.85).aspx)합니다._  

OMA DM server를 사용 하 여 관리 되는 장치에 대 한 Windows 10 IoT Core 대 한 MDM 정책을 다른 버전의 Windows 10에서 지원 되는 정책에 맞춰집니다. 뿐만 아니라 정책에 대 한 내용으로 IoT Core 장치에서 관리할 수 있습니다, 참조 구성 서비스 공급자 참조 Windows 10 용 [여기](https://aka.ms/csplist)합니다. MDM을 지 원하는 Windows 10에서 Open Mobile Alliance (OMA) 장치 관리 (DM) 1.2.1 프로토콜 사양을 기반으로 합니다.

## <a name="how-do-i-enroll-an-iot-core-device-into-a-mdm"></a>IoT Core 장치를 MDM에 등록 하려면 어떻게 해야 하나요?
___
MDM 등록을 IoT Core 장치 프로 비전 패키지를 사용 하 여 수행 됩니다. 패키지를 프로 비전 Windows 이미지 구성 및 디자이너 (WICD)를 사용 하 여 만들 수 있습니다. MDM.에 장치 등록을 시도해 보겠습니다

### <a name="creating-a-provisioning-package"></a>프로 비전 패키지 만들기

#### <a name="microsoft-system-center-configuration-manager-standalone-or-sccmintune-hybrid"></a>Microsoft System Center Configuration Manager (독립 실행형 또는 SCCM + Intune 하이브리드)

1. Configuration Manager 관리 콘솔 (ConfigMgr 콘솔) 열기

2. 이동할 _자산 및 준수 > 규정 준수 설정 > 회사 리소스 액세스 > 인증서 프로필_
   ![인증서 프로필](../media/ManagingDevices/ConfigMgr-Certificate-Profiles.PNG)

3. 클릭 **인증서 프로필 만들기**

4. 이름 및 프로필에 대 한 설명을 제공 합니다.
   - 이름: ConfigMgr 예제에서는 신뢰할 수 있는 루트 인증서
     - 인증서 프로필의 유형: 신뢰할 수 있는 CA 인증서  
     ![신뢰할 수 있는 인증](../media/ManagingDevices/ConfigMgr-Certificate-Profiles-Wizard.png)

5. **다음**을 클릭합니다.

6. 인증서 파일을 가져옵니다.

7. 선택 **컴퓨터 인증서 저장소-루트** 에 대 한 합니다 **대상 저장소**합니다.

8. **다음**을 클릭합니다.

9. 선택할 **모두 선택** 지원 되는 플랫폼에 대 한 ![지원 되는 플랫폼](../media/ManagingDevices/ConfigMgr-Certificate-Profiles-Wizard-Supported-Platforms.png)

10. 클릭 **요약, Next 및 닫기** 마법사를 종료 합니다.

11. 방금 만든 프로필을 마우스 오른쪽 단추로 클릭 하 고 클릭 **내보내기**합니다.

12. 클릭 **찾아보기**,.ppkg 파일을 내보내야 할 및 클릭 한 위치를 찾으려면 **저장**합니다.

13. 클릭 **내보내기** 클릭 **확인** 마법사를 종료 합니다.

#### <a name="other-mdm-servers"></a>다른 MDM 서버

1. 다운로드 및 설치 합니다 [Windows 평가 및 배포 키트 (Windows ADK)](https://developer.microsoft.com/windows/hardware/windows-assessment-deployment-kit)합니다.

2. Windows 이미징 및 구성 디자이너 (WICD)를 엽니다.
   ![Windows 이미징 및 구성 디자이너](../media/ManagingDevices/WICD-Start-Page.png)

3. 선택 **고급 프로 비전**

4. 패키지의 이름을 설정 합니다.

5. Windows 10 IoT Core 공통적으로 적용 설정을 선택 합니다.

6. 패키지 가져오기 단계를 건너뜁니다.
   ![WICD-New-Project-Details](../media/ManagingDevices/WICD-Advanced-Provisioning-New-Project-Details.PNG) 
   ![WICD-New-Project-Editions](../media/ManagingDevices/WICD-Advanced-Provisioning-New-Project-Editions.PNG) 
   ![WICD-New-Project-Import](../media/ManagingDevices/WICD-Advanced-Provisioning-New-Project-Import.PNG)

7. 작업 공간으로 이동 등록-> 합니다.

8. UPN 필드에 입력에서 장치를 등록 하려면 계정 (즉 trmck@contoso.co)를 누릅니다 **추가**합니다.

   ![작업 공간 등록 입력](../media/ManagingDevices/WICD-Workplace-Enrollments-UPN-Filled.png)

9. AuthPolicy 중에서 선택에 대 한 사용자 이름 암호 기반 인증 (온-프레미스) 또는 인증서 기반 인증 합니다.

10. MDM 서버에 대 한 검색 서비스 URL을 입력 합니다.

> [!NOTE]
> 등록 서비스 URL 및 정책 서비스 URL은 선택적입니다.

11. 비밀 입력에 대 한  
    - 온-프레미스: 사용 하 여 등록 하는 계정의 암호  
    - 인증서: 인증서의 지문
    
    ![채워진된 온-프레미스](../media/ManagingDevices/WICD-Workplace-Enrollments-UPN-Details-Filled-Premise.png)  

12. WICD 창의 맨 위에 있는 클릭 **내보내기 > 프로 비전 패키지**합니다.

13. 패키지에 대 한 이름 및 버전을 제공 하 고 클릭 **다음**합니다. 

> [!NOTE]
> 업데이트 된 패키지를 실행 되도록 버전 번호가 증가 해야 합니다.

14. 클릭 **다음** 에 **보안 세부 정보 페이지**합니다.

15. 패키지를 로컬 컴퓨터 클릭에서 내보낼 수 있는 위치를 선택 **다음**합니다.

16. 클릭 **빌드** 차례로 **마침** 마법사를 종료 합니다.

### <a name="installing-the-provisioning-package"></a>프로 비전 패키지를 설치합니다.

IoT 장치에 프로 비전 패키지를 배포할 수 있는 몇 가지가 있습니다. 장치에 패키지를 복사 하거나 이미징 프로세스 중 이미지에 패키지를 추가 하 여 패키지를 배포 하는 것이 가능 합니다.

#### <a name="copying-package-to-device"></a>장치에 패키지 복사

SCCM 또는 WICD에서 내보낸 프로 비전 패키지를 가져오고.ppkg 파일을 복사 `C:\Windows\Provisioning\Packages` IoT 장치의 디렉터리입니다. 장치 재부팅 시 패키지 실행 되 고 장치가 등록 프로세스를 시작 합니다.

#### <a name="adding-package-to-image"></a>이미지에 패키지 추가

참조 [이미지에 프로 비전 패키지 추가](https://docs.microsoft.com/windows-hardware/manufacture/iot/add-a-provisioning-package-to-an-image)합니다. 최초 부팅 시 장치 패키지를 실행 하 고 등록 프로세스를 시작 됩니다.
