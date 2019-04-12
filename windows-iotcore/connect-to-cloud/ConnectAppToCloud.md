---
title: 클라우드에 앱 연결
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 클라우드로 앱을 연결 하는 방법에 알아봅니다.
keywords: windows iot, 클라우드, Azure, Azure IoT Hub
ms.openlocfilehash: 3f7f50ba87e269fa8ac958f80affbd2fd0af5c53
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59513350"
---
# <a name="connect-your-app-to-the-cloud"></a>클라우드에 앱 연결

이 단계별 가이드를 사용 하면 Windows 10 IoT Core 사용 하 여 기능을 살펴보고, 장치 설정 및 Azure IoT Hub에 연결 하는 첫 번째 응용 프로그램을 만들 수 있습니다.

## <a name="step-1-prepare-your-device"></a>1단계: 장치를 준비 합니다.

장치를 준비 하는 방법에 지침을 찾을 수 있습니다 합니다 [시작 페이지 가져오기](https://developer.microsoft.com/en-us/windows/iot/getstarted) 했는지 [TPM 장치 프로 비전](../connect-to-cloud/ConnectDeviceToCloud.md)

## <a name="step-2-install-visual-studio-2017-and-tools"></a>2단계: Visual Studio 2017 및 도구 설치

설치할 [Visual Studio 2017](https://go.microsoft.com/fwlink/?linkid=845271)합니다. 무료 Community edition을 비롯해 Visual Studio의 모든 버전을 설치할 수 있습니다.

선택 되어 있는지 확인 합니다 **유니버설 Windows 앱 개발 도구**, Windows 10 앱을 작성 하는 데 필요한 구성 요소:

![유니버설 Windows 앱 개발 도구](../media/ConnectAppToCloud/install_tools_for_windows10.png)

## <a name="step-3-install-the-connected-services-for-azure-iot-hub"></a>3단계: Azure IoT Hub에 대 한 연결 된 서비스를 설치 합니다.

Azure IoT Hub에 대 한 Visual Studio 확장에 대 한 연결 된 서비스에 연결 하 고 1 분 이내에 Azure IoT Hub와 상호 작용을 시작할 수 있습니다.

확장을 설치할 수는 [VS 갤러리](https://aka.ms/azure-iot-hub-vs-2017-cs-vs-gallery)합니다.

## <a name="step-4-create-a-visual-studio-uwp-solution"></a>4단계: Visual Studio UWP 솔루션 만들기

Visual Studio에서 UWP 솔루션 만들기에 **파일** 메뉴에서 클릭 **새로 만들기** 한 다음 **프로젝트**:

![새 프로젝트 만들기](../media/ConnectAppToCloud/new_project_menu.png)

제공 하는 새 프로젝트 대화 상자에서 선택 **비어 있는 앱 (유니버설 Windows) 시각적 개체 C#** 합니다. 프로젝트 (예: 이름 지정 **MyFirstIoTCoreApp**):

![새 솔루션 대화 상자](../media/ConnectAppToCloud/new_solution.png)

## <a name="use-the-connected-services-for-azure-iot-hub-to-connect-to-azure-iot-hub"></a>Azure IoT Hub에 연결 된 서비스를 사용 하 여 Azure IoT Hub에 연결할

지침을 따릅니다 합니다 [연결 된 서비스 도구](https://aka.ms/azure-iot-hub-vs-2017-cs-vs-gallery) 프로젝트를 Azure IoT Hub에 연결 합니다. 두 개의 함수가 생성 됩니다 `SendDeviceToCloudMessageAsync` 및 `ReceiveCloudToDeviceMessageAsync` 는 앱의 어디서 나 호출할 수 있습니다. 하다 면 이러한 함수를 수정할 수 있습니다.  

