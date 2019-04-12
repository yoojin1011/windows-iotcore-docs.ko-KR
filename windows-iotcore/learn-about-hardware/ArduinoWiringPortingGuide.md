---
title: Arduino 포팅 가이드 연결
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 수정 및 Arduino 연결 하는 프로젝트를 배포할 때 발생 하는 일반적인 문제에 알아봅니다.
keywords: windows iot에 Arduino 연결, Visual Studio에서 이식
ms.openlocfilehash: 9b1d54807c21a54d8186d7f7ddabc31f16d3dab3
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512421"
---
# <a name="arduino-wiring-porting-guide"></a><span data-ttu-id="77df3-104">Arduino 포팅 가이드 연결</span><span class="sxs-lookup"><span data-stu-id="77df3-104">Arduino Wiring Porting Guide</span></span>

<span data-ttu-id="77df3-105">라이브러리 및 배선 Arduino 스케치 Visual Studio 내에서 Arduino 연결 프로젝트로 복사/붙여넣을 하 고 Minnowboard 최대, Raspberry Pi 2 및 Raspberry Pi 3에서 실행 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77df3-105">Arduino Wiring sketches and libraries can be copy/pasted into an Arduino Wiring project inside Visual Studio and run on Raspberry Pi 2, Raspberry Pi 3 or Minnowboard Max.</span></span> <span data-ttu-id="77df3-106">경우에 따라 개 Windows 환경과 더 호환 되도록 하기 위해 이러한 파일에 대해 필요로 하는 약간의 수정을 작업할 보드입니다.</span><span class="sxs-lookup"><span data-stu-id="77df3-106">Sometimes there are slight modifications that need to be made to these files in order to make them more compatible with the Windows environment, or the board you are working with.</span></span> <span data-ttu-id="77df3-107">이 가이드에서는 Arduino 연결 하는 프로젝트를 배포할 때 발생할 수 있는 일반적인 문제 뿐만 아니라 이러한 수정 사항을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="77df3-107">This guide will cover those modifications as well as common issues that you may run into when deploying Arduino Wiring projects.</span></span>

## <a name="porting"></a><span data-ttu-id="77df3-108">포팅</span><span class="sxs-lookup"><span data-stu-id="77df3-108">Porting</span></span>

### <a name="updating-pins"></a><span data-ttu-id="77df3-109">Pin 업데이트</span><span class="sxs-lookup"><span data-stu-id="77df3-109">Updating Pins</span></span>

<span data-ttu-id="77df3-110">언급 하지 않아도 당연 이동 수 있지만 많은 스케치 및 라이브러리 (특히 해당 arduino shields) Arduino 장치에 대 한 특정 커넥터 핀에 대 한 참조를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77df3-110">It might go without saying, but many sketches and libraries (especially those for arduino shields) may contain references to specific connector pins for Arduino devices.</span></span> <span data-ttu-id="77df3-111">작업 중인 장치와 사용 하는 구성에 대 한 적절 한 커넥터 핀을 사용 하 여 스케치를 사용자 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="77df3-111">You'll want to customize your sketches to use the appropriate connector pins for the device you are working on and the configuration you are using.</span></span>

<span data-ttu-id="77df3-112">'Pin'를 참조 하는 모든 함수에 대 한 실제 커넥터 pin 번호를 필요 궁극적으로 Arduino 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="77df3-112">Arduino Wiring ultimately requires a physical connector pin number for any functions that refer to 'pins'.</span></span> <span data-ttu-id="77df3-113">이러한 번호를 직접 사용할 수 있지만 특정 보드에서 커넥터 핀에 해당 하는 몇 가지 미리 정의 된 고정 이름이 제공 했습니다.</span><span class="sxs-lookup"><span data-stu-id="77df3-113">You can use these numbers directly, but we've also provided some pre-defined pin names which correspond to connector pins on specific boards.</span></span>

<span data-ttu-id="77df3-114">예를 들어, Raspberry Pi 2 및 3에 있는 실제 커넥터 핀 29 라고도 `GPIO5`합니다.</span><span class="sxs-lookup"><span data-stu-id="77df3-114">For example, the physical connector pin 29 on a Raspberry Pi 2 and 3 is also known as `GPIO5`.</span></span> <span data-ttu-id="77df3-115">다음 명령 중 하나를 사용 하 여 Raspberry Pi 2 및 3에서 높은 상태를 GPIO pin 5를 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77df3-115">You may set GPIO pin 5 to a HIGH state on a Raspberry Pi 2 and 3 by using either of the following commands:</span></span>
```
pinMode( 29, OUTPUT );
digitalWrite( 29, HIGH );
```

<span data-ttu-id="77df3-116">로 구분하거나 여러</span><span class="sxs-lookup"><span data-stu-id="77df3-116">or</span></span>

```
pinMode( GPIO5, OUTPUT );
digitalWrite( GPIO5, HIGH );
```

<span data-ttu-id="77df3-117">미리 정의 된 pin 이름을 찾을 수 있습니다 [pins_arduino.h](https://github.com/ms-iot/lightning/blob/develop/source/pins_arduino.h) 했습니다 Arduino 연결 모든 프로젝트에 있지만 사용할 수 있는 다른 물리적 커넥터 핀에 대 한 작성 하는 하드웨어 설정에 따라 이후를 포함 하 고 고정 이름은 각 장치에 사용할 수 있는 설명 하기 위해 여기에서 테이블도 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="77df3-117">The pre-defined pin names can be found in [pins_arduino.h](https://github.com/ms-iot/lightning/blob/develop/source/pins_arduino.h) and included in every Arduino Wiring project, but since there will be different physical connector pins available depending on the hardware setup you are building for, we've also included a table here to describe which pin names are available for each device.</span></span>

#### <a name="raspberry-pi-2-and-3"></a><span data-ttu-id="77df3-118">Raspberry Pi 2 및 3</span><span class="sxs-lookup"><span data-stu-id="77df3-118">Raspberry Pi 2 and 3</span></span>

![핀아웃 다이어그램](../media/ArduinoWiringPortingGuide/RP2_Pinout.png)

> [!div class="mx-tdBreakAll"]
> | <span data-ttu-id="77df3-120">Pin 정의</span><span class="sxs-lookup"><span data-stu-id="77df3-120">Pin Define</span></span> | <span data-ttu-id="77df3-121">해당 Pin 번호</span><span class="sxs-lookup"><span data-stu-id="77df3-121">Corresponding Pin Number</span></span>|
> |-------------|----------|
> | <span data-ttu-id="77df3-122">LED_BUILTIN</span><span class="sxs-lookup"><span data-stu-id="77df3-122">LED_BUILTIN</span></span> | *<span data-ttu-id="77df3-123">온보드 LED</span><span class="sxs-lookup"><span data-stu-id="77df3-123">onboard LED</span></span>* |
> | <span data-ttu-id="77df3-124">GPIO \* _여기서 \* 참조 [0, 27]_</span><span class="sxs-lookup"><span data-stu-id="77df3-124">GPIO\* _where \* refers to [0, 27]_</span></span> | *<span data-ttu-id="77df3-125">핀아웃 다이어그램을 참조 하세요</span><span class="sxs-lookup"><span data-stu-id="77df3-125">refer to pinout diagram</span></span>* |
> | <span data-ttu-id="77df3-126">GCLK</span><span class="sxs-lookup"><span data-stu-id="77df3-126">GCLK</span></span> | <span data-ttu-id="77df3-127">7</span><span class="sxs-lookup"><span data-stu-id="77df3-127">7</span></span> |
> | <span data-ttu-id="77df3-128">범용 \* _여기서 \* 참조 [0, 5]_</span><span class="sxs-lookup"><span data-stu-id="77df3-128">GEN\* _where \* refers to [0, 5]_</span></span> | <span data-ttu-id="77df3-129">\* 핀아웃 다이어그램을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="77df3-129">\*refer to pinout diagram</span></span> |
> | <span data-ttu-id="77df3-130">SCL1</span><span class="sxs-lookup"><span data-stu-id="77df3-130">SCL1</span></span> | <span data-ttu-id="77df3-131">5</span><span class="sxs-lookup"><span data-stu-id="77df3-131">5</span></span> |
> | <span data-ttu-id="77df3-132">SDA1</span><span class="sxs-lookup"><span data-stu-id="77df3-132">SDA1</span></span> | <span data-ttu-id="77df3-133">3</span><span class="sxs-lookup"><span data-stu-id="77df3-133">3</span></span> |
> | <span data-ttu-id="77df3-134">CS0 (CE0 또는 SS)</span><span class="sxs-lookup"><span data-stu-id="77df3-134">CS0 (or CE0 or SS)</span></span> | <span data-ttu-id="77df3-135">24</span><span class="sxs-lookup"><span data-stu-id="77df3-135">24</span></span> |
> | <span data-ttu-id="77df3-136">CS1 (또는 CE1)</span><span class="sxs-lookup"><span data-stu-id="77df3-136">CS1 (or CE1)</span></span> | <span data-ttu-id="77df3-137">26</span><span class="sxs-lookup"><span data-stu-id="77df3-137">26</span></span> |
> | <span data-ttu-id="77df3-138">SCLK (또는 SCK)</span><span class="sxs-lookup"><span data-stu-id="77df3-138">SCLK (or SCK)</span></span> | <span data-ttu-id="77df3-139">23</span><span class="sxs-lookup"><span data-stu-id="77df3-139">23</span></span> |
> | <span data-ttu-id="77df3-140">MISO</span><span class="sxs-lookup"><span data-stu-id="77df3-140">MISO</span></span> | <span data-ttu-id="77df3-141">21</span><span class="sxs-lookup"><span data-stu-id="77df3-141">21</span></span> |
> | <span data-ttu-id="77df3-142">MOSI</span><span class="sxs-lookup"><span data-stu-id="77df3-142">MOSI</span></span> | <span data-ttu-id="77df3-143">19</span><span class="sxs-lookup"><span data-stu-id="77df3-143">19</span></span> |
> | <span data-ttu-id="77df3-144">RXD</span><span class="sxs-lookup"><span data-stu-id="77df3-144">RXD</span></span> | <span data-ttu-id="77df3-145">10</span><span class="sxs-lookup"><span data-stu-id="77df3-145">10</span></span> |
> | <span data-ttu-id="77df3-146">TXD</span><span class="sxs-lookup"><span data-stu-id="77df3-146">TXD</span></span> | <span data-ttu-id="77df3-147">8</span><span class="sxs-lookup"><span data-stu-id="77df3-147">8</span></span> |

#### <a name="minnowboard-max"></a><span data-ttu-id="77df3-148">Minnowboard 최대</span><span class="sxs-lookup"><span data-stu-id="77df3-148">Minnowboard Max</span></span>

![핀아웃 다이어그램](../media/ArduinoWiringPortingGuide/MBM_Pinout.png)
> [!div class="mx-tdBreakAll"]
> | <span data-ttu-id="77df3-150">Pin 정의</span><span class="sxs-lookup"><span data-stu-id="77df3-150">Pin Define</span></span> | <span data-ttu-id="77df3-151">해당 Pin 번호</span><span class="sxs-lookup"><span data-stu-id="77df3-151">Corresponding Pin Number</span></span>|
> |-------------|----------|
> | <span data-ttu-id="77df3-152">GPIO \* _여기서 \* 참조 [0, 9]_</span><span class="sxs-lookup"><span data-stu-id="77df3-152">GPIO\* _where \* refers to [0, 9]_</span></span>  | *<span data-ttu-id="77df3-153">핀아웃 다이어그램을 참조 하세요</span><span class="sxs-lookup"><span data-stu-id="77df3-153">refer to pinout diagram</span></span>* |
> | <span data-ttu-id="77df3-154">SCL</span><span class="sxs-lookup"><span data-stu-id="77df3-154">SCL</span></span> | <span data-ttu-id="77df3-155">13</span><span class="sxs-lookup"><span data-stu-id="77df3-155">13</span></span> |
> | <span data-ttu-id="77df3-156">SDA</span><span class="sxs-lookup"><span data-stu-id="77df3-156">SDA</span></span> | <span data-ttu-id="77df3-157">15</span><span class="sxs-lookup"><span data-stu-id="77df3-157">15</span></span> |
> | <span data-ttu-id="77df3-158">CS0 (CE0 또는 SS)</span><span class="sxs-lookup"><span data-stu-id="77df3-158">CS0 (or CE0 or SS)</span></span> | <span data-ttu-id="77df3-159">5</span><span class="sxs-lookup"><span data-stu-id="77df3-159">5</span></span> |
> | <span data-ttu-id="77df3-160">SCLK (또는 SCK)</span><span class="sxs-lookup"><span data-stu-id="77df3-160">SCLK  (or SCK)</span></span>| <span data-ttu-id="77df3-161">11</span><span class="sxs-lookup"><span data-stu-id="77df3-161">11</span></span> |
> | <span data-ttu-id="77df3-162">MISO</span><span class="sxs-lookup"><span data-stu-id="77df3-162">MISO</span></span> |<span data-ttu-id="77df3-163">7</span><span class="sxs-lookup"><span data-stu-id="77df3-163">7</span></span> |
> | <span data-ttu-id="77df3-164">MOSI</span><span class="sxs-lookup"><span data-stu-id="77df3-164">MOSI</span></span> | <span data-ttu-id="77df3-165">9</span><span class="sxs-lookup"><span data-stu-id="77df3-165">9</span></span> |
> | <span data-ttu-id="77df3-166">CTS1</span><span class="sxs-lookup"><span data-stu-id="77df3-166">CTS1</span></span> | <span data-ttu-id="77df3-167">10</span><span class="sxs-lookup"><span data-stu-id="77df3-167">10</span></span> |
> | <span data-ttu-id="77df3-168">RTS1</span><span class="sxs-lookup"><span data-stu-id="77df3-168">RTS1</span></span> | <span data-ttu-id="77df3-169">12</span><span class="sxs-lookup"><span data-stu-id="77df3-169">12</span></span> |
> | <span data-ttu-id="77df3-170">RX1</span><span class="sxs-lookup"><span data-stu-id="77df3-170">RX1</span></span> | <span data-ttu-id="77df3-171">8</span><span class="sxs-lookup"><span data-stu-id="77df3-171">8</span></span> |
> | <span data-ttu-id="77df3-172">TX1</span><span class="sxs-lookup"><span data-stu-id="77df3-172">TX1</span></span> | <span data-ttu-id="77df3-173">6</span><span class="sxs-lookup"><span data-stu-id="77df3-173">6</span></span> |
> | <span data-ttu-id="77df3-174">RX2</span><span class="sxs-lookup"><span data-stu-id="77df3-174">RX2</span></span> | <span data-ttu-id="77df3-175">19</span><span class="sxs-lookup"><span data-stu-id="77df3-175">19</span></span> |
> | <span data-ttu-id="77df3-176">TX2</span><span class="sxs-lookup"><span data-stu-id="77df3-176">TX2</span></span> | <span data-ttu-id="77df3-177">17</span><span class="sxs-lookup"><span data-stu-id="77df3-177">17</span></span> |


## <a name="common-problems"></a><span data-ttu-id="77df3-178">일반적인 문제</span><span class="sxs-lookup"><span data-stu-id="77df3-178">Common Problems</span></span>

### <a name="cant-find-arduino-wiring-application-visual-c-project-template-in-visual-studio"></a><span data-ttu-id="77df3-179">"Arduino 응용 프로그램 연결" 시각적 개체를 찾을 수 없습니다 C++ Visual Studio에서 프로젝트 템플릿</span><span class="sxs-lookup"><span data-stu-id="77df3-179">Can't find "Arduino Wiring Application" Visual C++ project template in Visual Studio</span></span>

<span data-ttu-id="77df3-180">**원인**: Visual Studio 용 Windows IoT 프로젝트 템플릿 확장 설치 되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="77df3-180">**Cause**: The Windows IoT Project Templates extension for Visual Studio is not installed.</span></span>

<span data-ttu-id="77df3-181">**해결 방법**: Visual Studio 확장에 대 한 Windows IoT 프로젝트 템플릿을 설치 해야 Visual Studio에서 프로젝트 Arduino 연결을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77df3-181">**Solution**: You must install the Visual Studio Extension for Windows IoT Project Templates before you can create Arduino Wiring projects in Visual Studio.</span></span> <span data-ttu-id="77df3-182">로 이동 [Windows IoT Core 프로젝트 템플릿에 확장 페이지](https://go.microsoft.com/fwlink/?linkid=847472) Visual Studio 갤러리에서 확장을 다운로드 하려면!</span><span class="sxs-lookup"><span data-stu-id="77df3-182">Head over to [Windows IoT Core Project Templates extension page](https://go.microsoft.com/fwlink/?linkid=847472) to download the extension from the Visual Studio Gallery!</span></span>

### <a name="error-identifier-not-found-when-calling-a-function"></a><span data-ttu-id="77df3-183">오류: 찾을 수 없음 "식별자" 함수를 호출 하는 경우</span><span class="sxs-lookup"><span data-stu-id="77df3-183">ERROR: "identifier not found" when calling a function</span></span>

<span data-ttu-id="77df3-184">**원인**: 이 오류는 문서에 아직 선언 되지 않은 함수 호출 되 면 링커 프로세스 중에 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="77df3-184">**Cause**: This error occurs during the linker process when a function is invoked that has not yet been declared in the document.</span></span>

<span data-ttu-id="77df3-185">**해결 방법**: C++에서 모든 함수 호출 전에 선언 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="77df3-185">**Solution**: In C++, all functions must be declared before they are invoked.</span></span> <span data-ttu-id="77df3-186">스케치 파일에서 새 함수를 정의한 경우 선언 또는 함수의 전체 구현 (일반적으로 문서 위쪽)에서 호출 하려는 모든 시도가 보다 커야 합니다.</span><span class="sxs-lookup"><span data-stu-id="77df3-186">If you have defined a new function in your sketch file, either the declaration or the entire implementation of the function must be above any attempts to invoke it (typically at the top of the document).</span></span>

<span data-ttu-id="77df3-187">**예**:</span><span class="sxs-lookup"><span data-stu-id="77df3-187">**Example**:</span></span>

<span data-ttu-id="77df3-188">다음 코드 블록은 오류 발생 "'myFunction': 식별자를 찾을 수 없습니다"</span><span class="sxs-lookup"><span data-stu-id="77df3-188">The following block of code will raise the error "'myFunction': identifier not found"</span></span>

```
void setup()
{

}

void loop()
{
    myFunction();
}

void myFunction()
{
    //do something
}
```

<span data-ttu-id="77df3-189">두 가지 솔루션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77df3-189">There are two solutions.</span></span> <span data-ttu-id="77df3-190">첫째, 위의 모든 호출 함수를 선언할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77df3-190">First, you may declare the function above any invocations.</span></span> <span data-ttu-id="77df3-191">일반적으로이 선언 파일의 맨 위에 있는 이루어집니다.</span><span class="sxs-lookup"><span data-stu-id="77df3-191">Typically, this declaration is done at the top of the file.</span></span>

```C++
// Declare function here
void myFunction();

void setup()
{

}

void loop()
{
    myFunction();
}

// And, define the function here
void myFunction()
{
    //do something
}
```

<span data-ttu-id="77df3-192">또는 전체 구현의 위의 모든 호출 함수를 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77df3-192">Alternatively, you can move the entire implementation of the function above any invocations.</span></span> <span data-ttu-id="77df3-193">이 선언와 동시에 함수 정의의 효과가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77df3-193">This has the effect of both declaring and defining the function at the same time.</span></span>

```C++
void setup()
{
}

void myFunction()
{
    //do something
}

void loop()
{
    myFunction();
}
```

### <a name="my-solution-hangs-infinitely-when-being-initialized"></a><span data-ttu-id="77df3-194">필자의 솔루션 초기화 되는 경우에 무한 중단 됩니다.</span><span class="sxs-lookup"><span data-stu-id="77df3-194">My solution hangs infinitely when being initialized</span></span>

<span data-ttu-id="77df3-195">알려진 문제가 발생할 수 있습니다는 C++ 무한 중단 솔루션 초기화 되는 (deadlock).</span><span class="sxs-lookup"><span data-stu-id="77df3-195">There is a known issue which can cause a C++ solution to hang infinitely (deadlock) when being initialized.</span></span> <span data-ttu-id="77df3-196">하면 영원히 중단 솔루션이 나타나고 디버거를 사용 하 여 '중단' 문에 Arduino 연결 응용 프로그램의 setup() 또는 loop () 섹션에서 수 없는 경우이 유형의 문제가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77df3-196">You may be experiencing this type of issue if you find that your solution appears to hang forever and you are unable to use the debugger to 'break in' to any statement in the setup() or loop() sections of your Arduino Wiring application.</span></span>

<span data-ttu-id="77df3-197">**원인**: 개체를 만들 되 또는 솔루션 초기화 완료 되기 전에 비동기 작업을 이동 하는 함수 호출 되 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77df3-197">**Cause**: An object is being created or a function is being called which leads to an asyncronous action before the solution has finished initializing.</span></span> <span data-ttu-id="77df3-198">와 같은 API 함수를 호출 하는 개체의 생성자에서 오류로 인 `pinMode`합니다.</span><span class="sxs-lookup"><span data-stu-id="77df3-198">It is likely caused from an object's constructor calling an API function like `pinMode`.</span></span>

<span data-ttu-id="77df3-199">**해결 방법**: 개체 생성자를 이동 하 고 함수 및 코드의 초기화 섹션에서 호출 된 `setup()` 블록입니다.</span><span class="sxs-lookup"><span data-stu-id="77df3-199">**Solution**: Move any object constructors and function calls away from the initialization section of code and into the `setup()` block.</span></span>

<span data-ttu-id="77df3-200">**예 1**:</span><span class="sxs-lookup"><span data-stu-id="77df3-200">**Example 1**:</span></span>

<span data-ttu-id="77df3-201">호출 된 함수를 호출 하는이 스케치 실행 `setPinModes()` 솔루션 자체 초기화 되기 전에 합니다.</span><span class="sxs-lookup"><span data-stu-id="77df3-201">The execution of this sketch calls a function called `setPinModes()` before the solution itself has been initialized.</span></span> <span data-ttu-id="77df3-202">솔루션 실행 되지만를 표시 하는 무한 중단 합니다.</span><span class="sxs-lookup"><span data-stu-id="77df3-202">The solution will appear to execute but will hang infinitely.</span></span>

```C++
bool setPinModes();

int pin = GPIO5;
bool initialized = setPinModes();

void setup()
{

}

void loop()
{
    if( initialized )
    {
        //do something
    }
}

bool setPinModes()
{
    if( pin < 0 ) return false;
    pinMode( pin, OUTPUT );
    return true;
}
```

<span data-ttu-id="77df3-203">아래 솔루션은를 실행 하기만 하면 옮겼습니다 `setPinModes()` 에 `setup()` 함수:</span><span class="sxs-lookup"><span data-stu-id="77df3-203">The solution is below, we've simply moved the execution of `setPinModes()` to the `setup()` function:</span></span>

```C++
bool setPinModes();

int pin = GPIO5;
bool initialized;

void setup()
{
    initialized = setPinModes();
}

void loop()
{
    if( initialized )
    {
        //do something
    }
}

bool setPinModes()
{
    if( pin < 0 ) return false;
    pinMode( pin, OUTPUT );
    return true;
}
```

<span data-ttu-id="77df3-204">**예 2**:</span><span class="sxs-lookup"><span data-stu-id="77df3-204">**Example 2**:</span></span>

<span data-ttu-id="77df3-205">이 스케치를 실행 하기 전에 스택에서 개체를 만듭니다 `setup()` 가 호출 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="77df3-205">The execution of this sketch creates an object on the stack before `setup()` has been called.</span></span> <span data-ttu-id="77df3-206">개체 호출 이후 `pinMode` 생성자를 통해이 또한는 교착 상태가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="77df3-206">Since the object calls `pinMode` in its constructor, this will also cause a deadlock.</span></span> <span data-ttu-id="77df3-207">일반적이 지 않은 문제가 이지만 특정 라이브러리에서 개체를 사용 하 여 발생할 수 있습니다 (에서 Arduino 같은 `LiquidCrystal` 라이브러리)입니다.</span><span class="sxs-lookup"><span data-stu-id="77df3-207">This is an uncommon issue, but may occur with objects from certain libraries (like the Arduino `LiquidCrystal` library).</span></span>

```C++
class MyObject
{
public:
    MyObject()
    {
        pinMode( GPIO5, OUTPUT );
    }

    void doSomething()
    {
        //... 
    }
};

MyObject myObject;

void setup()
{
}

void loop()
{
    myObject.doSomething();
}
```

<span data-ttu-id="77df3-208">솔루션에는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="77df3-208">The solution is below.</span></span> <span data-ttu-id="77df3-209">개체는 개체 포인터에 대 한 변경 되 고 개체를 초기화 하는 이동 되었습니다 `setup()`합니다.</span><span class="sxs-lookup"><span data-stu-id="77df3-209">We've changed the object to an object pointer and moved the initialization of the object to `setup()`.</span></span>

```C++
class MyObject
{
public:
    MyObject()
    {
        pinMode( GPIO5, OUTPUT );
    }

    void doSomething()
    {
        //... 
    }
};

MyObject *myObject;

void setup()
{
    myObject = new MyObject();
}

void loop()
{
    myObject->doSomething();
}
```

### <a name="using-serialprint-and-serialprintln"></a><span data-ttu-id="77df3-210">사용 하 여 `Serial.print()` 및 `Serial.println()`</span><span class="sxs-lookup"><span data-stu-id="77df3-210">Using `Serial.print()` and `Serial.println()`</span></span>

<span data-ttu-id="77df3-211">많은 Arduino 스케치 사용 `Serial` (열) 하는 경우 직렬 콘솔에 데이터를 인쇄 하거나 (USB 또는 tx/rx) 직렬 회선에 쓸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77df3-211">Many Arduino sketches use `Serial` to print data to the serial console (if opened) or to write to the serial lines (USB or tx/rx).</span></span> <span data-ttu-id="77df3-212">하드웨어 번개 SDK의 이전 버전에서 `Serial` 지원의 제공 것 들이 포함 되지 않은 `Log()` 디버거를 인쇄 하는 함수 출력 Visual Studio의 창.</span><span class="sxs-lookup"><span data-stu-id="77df3-212">In prior versions of the Lightning SDK, Hardware `Serial` support wasn't included, so we provided a `Log()` function which will print to the debugger output window in Visual Studio.</span></span> `Serial.print*()` <span data-ttu-id="77df3-213">또는 `Serial.write()` 제거 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="77df3-213">or `Serial.write()` had to be removed.</span></span>

<span data-ttu-id="77df3-214">그러나부터 _번개 SDK v1.1.0_를 추가 했습니다 `Hardware Serial` 지원과 둘 다 `Serial.print*()` 또는 `Serial.write()` 함수 완전히 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="77df3-214">However, starting with _Lightning SDK v1.1.0_, we've added `Hardware Serial` support and both `Serial.print*()` or `Serial.write()` functions are fully supported.</span></span> <span data-ttu-id="77df3-215">따라서 Arduino 용으로 빌드된 스케치를 복사 하는 경우 Windows IoT 버전 스케치에서 직렬 이러한 참조 중 하나를 바꿀 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="77df3-215">So, if you are copying a sketch built for an Arduino, you won't need to replace any of these Serial references in the Windows IoT version of the sketch.</span></span>

<span data-ttu-id="77df3-216">또한의 기능을 확장 한 것 `Serial.print()` 및 `Serial.println()`, 하드웨어 직렬 핀에 작성 하는 것 외에도-는 디버거가 연결 될 때 디버거 창에 출력 합니다.</span><span class="sxs-lookup"><span data-stu-id="77df3-216">Furthermore, we've extended the functionality of `Serial.print()` and `Serial.println()`, to output to the debugger window when a debugger is attached - in addition to writing to the hardware serial pins.</span></span>
<span data-ttu-id="77df3-217">디버그 인쇄 출력 집합 출력 때 사용할 대부분의 사용자는 읽기 이후 기본적으로 실행 중인 해당 스케치 합니다.</span><span class="sxs-lookup"><span data-stu-id="77df3-217">The debug output printing is set as the default since reading that output is what most users would want when running their sketches.</span></span> <span data-ttu-id="77df3-218">그러나 기능을 사용할 수도; 예: 성능 향상을 위해 호출 `Serial.enablePrintDebugOutput(false);` 스케치가 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="77df3-218">However, that functionality can be disabled as well; e.g. to improve performance, simply call `Serial.enablePrintDebugOutput(false);` to disable it in your sketch.</span></span> <span data-ttu-id="77df3-219">다시 사용 하려면 호출 `Serial.enablePrintDebugOutput(true);`합니다.</span><span class="sxs-lookup"><span data-stu-id="77df3-219">To re-enable it, call `Serial.enablePrintDebugOutput(true);`.</span></span> <span data-ttu-id="77df3-220">하드웨어 직렬 핀에 쓰기 호출을 받지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="77df3-220">Writing to the hardware serial pins is not affected by those calls.</span></span>

<span data-ttu-id="77df3-221">Note 출력이 디버거 창에 전송 하는 FTDI 같은 직렬 핀에는 모든 주변 장치를 연결할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="77df3-221">Note, you do NOT need to attach any peripheral to your serial pins such as an FTDI, to get output sent to the debugger window.</span></span> <span data-ttu-id="77df3-222">그러나 응용 프로그램이 디버깅 되 고 하는 동안 디버거 창을 열려 있는지 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="77df3-222">However, you'll need to make sure the debugger window is open while your application is being debugged.</span></span>

![디버거 출력](../media/ArduinoWiringPortingGuide/debugger_output.png)

<span data-ttu-id="77df3-224">업데이트 된 프로젝트 템플릿 합니다 [Windows IoT Core 프로젝트 템플릿에 확장 페이지](https://go.microsoft.com/fwlink/?linkid=847472) 하드웨어를 사용 하도록 설정 하려면 `Serial` 즉시 합니다.</span><span class="sxs-lookup"><span data-stu-id="77df3-224">The project templates have been updated on the [Windows IoT Core Project Templates extension page](https://go.microsoft.com/fwlink/?linkid=847472) to enable using Hardware `Serial` out of the box.</span></span> <span data-ttu-id="77df3-225">그러나 Arduino 연결 응용 프로그램에 이미 생성 된 경우 이전 프로젝트 템플릿 버전을 사용 해야 1) 최신 번개 sdk 프로젝트를 업그레이드 하려면 v1.1.0 이상, 2)에 필요한 하드웨어 직렬 장치 기능이 추가 프로그램 사용할 수 있게 되기를 AppxManifest `Serial`합니다.</span><span class="sxs-lookup"><span data-stu-id="77df3-225">However, if your Arduino Wiring application has already been created using an older project template version, you'll need to 1) Upgrade your project to the latest Lightning SDK, v1.1.0 or later, and 2) add the required Hardware Serial device capability to your AppxManifest to be able to use `Serial`.</span></span>

### <a name="hardware-serial-device-capability-requirements"></a><span data-ttu-id="77df3-226">하드웨어 직렬 장치 기능 요구 사항</span><span class="sxs-lookup"><span data-stu-id="77df3-226">Hardware Serial device capability requirements</span></span>

<span data-ttu-id="77df3-227">Windows 10 IoT Core 하드웨어 직렬 기능 AppX 매니페스트에 추가 하는 장치 기능 선언에 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="77df3-227">Hardware Serial functionality in Windows 10 IoT Core requires device capability declarations added to the AppX manifest.</span></span>

<span data-ttu-id="77df3-228">파일을 찾을 `Package.appxmanifest` 솔루션 탐색기에서 파일 이름을 입력 하 여 프로젝트에서.</span><span class="sxs-lookup"><span data-stu-id="77df3-228">Find the file `Package.appxmanifest` in your project, by typing the file name in the solution explorer.</span></span> <span data-ttu-id="77df3-229">그런 다음, 파일을 마우스 오른쪽 단추로 클릭 하 고 프로그램을 선택 '...'.</span><span class="sxs-lookup"><span data-stu-id="77df3-229">Then, right click the file and choose 'Open With...'.</span></span> <span data-ttu-id="77df3-230">'XML (텍스트) 편집기'를 선택 하 고 [확인]을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="77df3-230">Choose 'XML (Text) Editor' and click 'OK'.</span></span>

![Package.appxmanifest를 업데이트 하는 중](../media/ArduinoWiringPortingGuide/appxmanifest_search.png)

<span data-ttu-id="77df3-232">Appx 매니페스트 파일 편집기에서 추가 된 `serialcommunication` DeviceCapability 다음 XML 조각에서와 같이 프로젝트:</span><span class="sxs-lookup"><span data-stu-id="77df3-232">In the appx manifest file editor, add the `serialcommunication` DeviceCapability to your project as in the following XML snippet:</span></span>

```xml
<Capabilities>
  <Capability Name="internetClient" />

  <!-- General Arduino Wiring required capabilities -->
  <iot:Capability Name="lowLevelDevices" />
  <DeviceCapability Name="109b86ad-f53d-4b76-aa5f-821e2ddf2141"/>

  <!-- The serialcommunication capability is required to access Hardware Serial. --> 
  <DeviceCapability Name="serialcommunication">
    <Device Id="any">
      <Function Type="name:serialPort"/>
    </Device>
  </DeviceCapability>

</Capabilities>
```

### <a name="upgrade-your-project-to-the-latest-lightning-sdk"></a><span data-ttu-id="77df3-233">프로젝트가 최신 번개 SDK로 업그레이드</span><span class="sxs-lookup"><span data-stu-id="77df3-233">Upgrade your project to the latest Lightning SDK</span></span>

<span data-ttu-id="77df3-234">Arduino 연결 프로젝트에 따라 달라 집니다를 [번개 SDK Nuget 패키지](https://www.nuget.org/packages/Microsoft.IoT.Lightning/) 에서는 필요한 Arduino 연결 기능 및 선언으로 번개 드라이버를 사용 하 여 인터페이스를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="77df3-234">The Arduino Wiring projects depend on the [Lightning SDK Nuget package](https://www.nuget.org/packages/Microsoft.IoT.Lightning/) to implement the required Arduino Wiring functions and declarations as well as interface with the Lightning driver.</span></span> <span data-ttu-id="77df3-235">최신 번개 SDK에는 최신 기능 향상 및 버그 수정 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="77df3-235">The latest Lightning SDK will contain the latest improvements and bug fixes.</span></span> <span data-ttu-id="77df3-236">최신 번개 SDK를 업그레이드 하려면 다음이 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="77df3-236">To upgrade to the latest Lightning SDK, follow these steps:</span></span>

- <span data-ttu-id="77df3-237">솔루션 탐색기에서 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 Nuget 패키지 관리 '를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="77df3-237">In the Solution Explorer, right click on your project and click 'Manage Nuget Packages...'</span></span>
- <span data-ttu-id="77df3-238">NuGet 패키지 관리자에서 '설치 됨' 탭으로 이동 합니다. 설치 Microsoft.IoT.Lightning 패키지 표시</span><span class="sxs-lookup"><span data-stu-id="77df3-238">In the NuGet Package Manager, go to the 'Installed' tab. You should see the Microsoft.IoT.Lightning package installed</span></span>
- <span data-ttu-id="77df3-239">'Version' 콤보 상자 내에서 사용 가능한 버전에 나열 됩니다.</span><span class="sxs-lookup"><span data-stu-id="77df3-239">Available versions will be listed inside the 'Version' combobox.</span></span>
- <span data-ttu-id="77df3-240">최신 버전을 선택 하 고 패키지를 업데이트 하려면 ' 업데이트'를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="77df3-240">Choose the latest version, and click 'Update' to update your package.</span></span>
- <span data-ttu-id="77df3-241">시험판 버전으로 업그레이드 하 고 지 확인란 시험판 포함'도 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="77df3-241">Notice, to upgrade to a prerelease version, make sure to check the 'Include prerelease' checkbox as well.</span></span>

![NuGet 패키지 관리자](../media/ArduinoWiringPortingGuide/Nuget_PackageManager.png)
