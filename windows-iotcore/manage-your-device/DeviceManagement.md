---
title: Windows IoT Core 장치 관리
author: parameshbabu
ms.author: pabab
ms.date: 08/28/2017
ms.topic: article
description: Windows 10 IoT Core 장치를 관리 하는 다양 한 방법에 대해 알아봅니다.
keywords: windows iot, 장치 관리, windows iot, Azure DM, azure 허브, azure IoT
ms.openlocfilehash: dbcc6858ee32ce9eb8b33c3d1831a6581a8fa3c7
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "60170923"
---
# <a name="managing-windows-iot-core-devices"></a>Windows IoT Core 장치 관리

Windows 10 IoT Core 장치는 인증서 기반 등록을 지 원하는 기존 OMA DM MDM 서버를 사용 하거나 Azure IoT Hub의 장치 관리를 사용 하 여 관리할 수 있습니다.  

 _MDM 및 Windows 10에 대 한 자세한 내용은 [여기](https://msdn.microsoft.com/library/windows/hardware/dn914769(v=vs.85).aspx)를 참조 하세요._  

OMA DM 서버를 사용 하 여 관리 되는 장치의 경우 Windows 10 IoT Core 용 MDM 정책은 다른 버전의 Windows 10에서 지원 되는 정책과 일치 합니다. 정책 및 IoT Core 장치에서 관리할 수 있는 항목에 대 한 자세한 내용은 [여기](https://aka.ms/csplist)에서 Windows 10에 대 한 구성 서비스 공급자 참조를 참조 하세요. Windows 10의 MDM 지원은 오픈 Mobile (모바일 동맹) DM (장치 관리) 프로토콜 1.2.1 사양을 기반으로 합니다.

## <a name="how-do-i-enroll-an-iot-core-device-into-a-mdm"></a>IoT Core 장치를 MDM에 등록 어떻게 할까요? 있나요?
___
IoT Core 장치의 MDM 등록은 프로 비전 패키지를 사용 하 여 수행 됩니다. 프로 비전 패키지는 Windows 이미지 구성 및 디자이너 (WICD)를 사용 하 여 만들 수 있습니다. 장치를 MDM에 등록 해 보겠습니다.

### <a name="creating-a-provisioning-package"></a>프로 비전 패키지 만들기

#### <a name="microsoft-system-center-configuration-manager-standalone-or-sccmintune-hybrid"></a>Microsoft System Center Configuration Manager (독립 실행형 또는 SCCM + Intune 하이브리드)

1. Configuration Manager Management Console (ConfigMgr 콘솔)을 엽니다.

2. _자산 및 준수 > 준수 설정 > 회사 리소스 액세스 > 인증서 프로필_
   ![인증서 프로필로 이동 합니다.](../media/ManagingDevices/ConfigMgr-Certificate-Profiles.PNG)

3. **인증서 프로필 만들기** 를 클릭 합니다.

4. 프로필에 대 한 이름 및 설명을 제공 합니다.
   - 이름: ConfigMgr 예제 신뢰할 수 있는 루트 인증서
     - 인증서 프로필의 유형입니다. 신뢰할 수 있는 CA 인증서  
     ![신뢰할 수 있는 인증](../media/ManagingDevices/ConfigMgr-Certificate-Profiles-Wizard.png)

5. **다음**을 클릭합니다.

6. 인증서 파일을 가져옵니다.

7. **대상 저장소**에 대 한 **컴퓨터 인증서 저장소-루트** 를 선택 합니다.

8. **다음**을 클릭합니다.

9. 지원 되는 플랫폼 ![지원 플랫폼에 대해 **모두 선택** 을 선택 합니다.](../media/ManagingDevices/ConfigMgr-Certificate-Profiles-Wizard-Supported-Platforms.png)

10. **요약, 다음, 닫기** 를 차례로 클릭 하 여 마법사를 종료 합니다.

11. 앞서 만든 프로필을 마우스 오른쪽 단추로 클릭 하 고 **내보내기**를 클릭 합니다.

12. **찾아보기**를 클릭 하 고 파일을 내보낼 위치를 찾은 다음 **저장**을 클릭 합니다.

13. **내보내기** 를 클릭 하 고 **확인** 을 클릭 하 여 마법사를 종료 합니다.

#### <a name="other-mdm-servers"></a>기타 MDM 서버

1. Windows [ADK (평가 및 배포 키트)](https://developer.microsoft.com/windows/hardware/windows-assessment-deployment-kit)를 다운로드 하 여 설치 합니다.

2. Windows 이미징 및 구성 디자이너 (WICD)를 엽니다.
   ![Windows 이미징 및 구성 디자이너](../media/ManagingDevices/WICD-Start-Page.png)

3. **고급 프로 비전** 선택

4. 패키지의 이름을 설정 합니다.

5. Windows 10 IoT Core에 공통적인 설정을 선택 합니다.

6. 패키지 가져오기 단계를 건너뜁니다.
   ![WICD-](../media/ManagingDevices/WICD-Advanced-Provisioning-New-Project-Details.PNG) 
   프로젝트-세부 정보![WICD](../media/ManagingDevices/WICD-Advanced-Provisioning-New-Project-Editions.PNG) 
   ![(WICD)-프로젝트-가져오기](../media/ManagingDevices/WICD-Advanced-Provisioning-New-Project-Import.PNG)

7. 작업 공간-> 등록로 이동 합니다.

8. UPN 필드에서 장치를 등록 하려는 계정을 입력 하 고 (예: trmck@contoso.co) **추가**를 클릭 합니다.

   ![작업 공간 등록 채우기](../media/ManagingDevices/WICD-Workplace-Enrollments-UPN-Filled.png)

9. AuthPolicy의 경우 사용자 이름으로 OnPremises (암호 기반 인증) 또는 인증서 기반 인증 중 하나를 선택 합니다.

10. MDM 서버에 대 한 검색 서비스 URL을 입력 합니다.

> [!NOTE]
> 등록 서비스 URL 및 정책 서비스 URL은 선택 사항입니다.

11. 비밀을 입력 합니다.  
    - 온-프레미스 등록 하는 계정의 암호  
    - 인증서 인증서의 지문
    
    ![채워진 온-프레미스](../media/ManagingDevices/WICD-Workplace-Enrollments-UPN-Details-Filled-Premise.png)  

12. WICD 창 맨 위에서 **내보내기 > 프로 비전 패키지**를 클릭 합니다.

13. 패키지의 이름 및 버전을 입력 하 고 **다음**을 클릭 합니다. 

> [!NOTE]
> 업데이트 된 패키지가 실행 되도록 버전 번호를 증분 해야 합니다.

14. **보안 정보 페이지**에서 **다음** 을 클릭 합니다.

15. 로컬 컴퓨터에서 패키지를 내보낼 위치를 선택 하 고 **다음**을 클릭 합니다.

16. **빌드** 를 클릭 한 다음 **마침** 을 클릭 하 여 마법사를 종료 합니다.

### <a name="installing-the-provisioning-package"></a>프로 비전 패키지를 설치 하는 중

프로 비전 패키지를 IoT 장치에 배포 하는 방법에는 몇 가지가 있습니다. 패키지를 장치에 복사 하거나 이미징 프로세스 중에 패키지를 이미지에 추가 하 여 패키지를 배포할 수 있습니다.

#### <a name="copying-package-to-device"></a>장치에 패키지를 복사 하는 중

SCCM 또는 WICD에서 내보낸 프로 비전 패키지를 가져와. n a t kg 파일을 IoT 장치의 `C:\Windows\Provisioning\Packages` 디렉터리에 복사 합니다. 장치를 다시 부팅 하면 패키지가 실행 되 고 장치에서 등록 프로세스가 시작 됩니다.

#### <a name="adding-package-to-image"></a>이미지에 패키지 추가

[이미지에 프로 비전 패키지 추가](https://docs.microsoft.com/windows-hardware/manufacture/iot/add-a-provisioning-package-to-an-image)를 참조 하세요. 처음 부팅 될 때 장치는 패키지를 실행 하 고 등록 프로세스를 시작 합니다.
