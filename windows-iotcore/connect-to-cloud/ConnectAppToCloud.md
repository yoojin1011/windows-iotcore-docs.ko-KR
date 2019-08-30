---
title: 앱을 클라우드에 연결
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 앱을 클라우드에 연결 하는 방법에 대해 알아봅니다.
keywords: windows iot, 클라우드, Azure, Azure IoT Hub
ms.openlocfilehash: 3f7f50ba87e269fa8ac958f80affbd2fd0af5c53
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "60170221"
---
# <a name="connect-your-app-to-the-cloud"></a>앱을 클라우드에 연결

이 단계별 가이드에서는 Windows 10 IoT Core를 숙지 하 고, 장치를 설정 하 고, Azure IoT Hub에 연결 하는 첫 번째 응용 프로그램을 만들 수 있습니다.

## <a name="step-1-prepare-your-device"></a>1단계: 장치 준비

[시작 페이지](https://developer.microsoft.com/en-us/windows/iot/getstarted) 에서 장치를 준비 하는 방법에 대 한 지침을 확인 하 여 [장치의 TPM을 프로 비전](../connect-to-cloud/ConnectDeviceToCloud.md) 해야 합니다.

## <a name="step-2-install-visual-studio-2017-and-tools"></a>2단계: Visual Studio 2017 및 도구 설치

[Visual Studio 2017](https://go.microsoft.com/fwlink/?linkid=845271)을 설치 합니다. 무료 Community edition을 포함 하 여 모든 버전의 Visual Studio를 설치할 수 있습니다.

Windows 10 앱을 작성 하는 데 필요한 구성 요소인 **유니버설 Windows 앱 개발 도구**를 선택 해야 합니다.

![유니버설 Windows 앱 개발 도구](../media/ConnectAppToCloud/install_tools_for_windows10.png)

## <a name="step-3-install-the-connected-services-for-azure-iot-hub"></a>3단계: Azure IoT Hub에 대 한 연결된 서비스를 설치 합니다.

Visual Studio 확장 Azure IoT Hub에 대 한 연결된 서비스를 사용 하 여 1 분 이내에 Azure IoT Hub와 상호 작용할 수 있습니다.

[VS 갤러리](https://aka.ms/azure-iot-hub-vs-2017-cs-vs-gallery)에서 확장을 설치할 수 있습니다.

## <a name="step-4-create-a-visual-studio-uwp-solution"></a>4단계: Visual Studio UWP 솔루션 만들기

Visual Studio에서 UWP 솔루션을 만들려면 **파일** 메뉴에서 **새로 만들기** , **프로젝트**를 차례로 클릭 합니다.

![새 프로젝트 만들기](../media/ConnectAppToCloud/new_project_menu.png)

새 프로젝트 대화 상자에서 **비어 있는 앱 (유니버설 Windows) 시각적 개체 C#** 를 선택 합니다. 프로젝트에 이름 지정 (예: **MyFirstIoTCoreApp**):

![새 솔루션 대화 상자](../media/ConnectAppToCloud/new_solution.png)

## <a name="use-the-connected-services-for-azure-iot-hub-to-connect-to-azure-iot-hub"></a>Azure IoT Hub에 대 한 연결된 서비스를 사용 하 여 Azure IoT Hub에 연결

[연결된 서비스 도구의](https://aka.ms/azure-iot-hub-vs-2017-cs-vs-gallery) 지침에 따라 프로젝트를 Azure IoT Hub에 연결 합니다. 이 도구는 두 개의 함수를 `SendDeviceToCloudMessageAsync` 생성 `ReceiveCloudToDeviceMessageAsync` 하 고 앱의 아무 곳에서 나 호출할 수 있습니다. 이러한 함수는 적합 한 것 처럼 수정할 수 있습니다.  

