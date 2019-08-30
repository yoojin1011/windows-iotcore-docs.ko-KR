---
title: Arduino 배선 포팅 가이드
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Arduino 배선 프로젝트를 배포할 때 발생 하는 수정 사항 및 일반적인 문제에 대해 알아봅니다.
keywords: windows iot, Arduino, 배선, Visual Studio, 포팅
ms.openlocfilehash: 9b1d54807c21a54d8186d7f7ddabc31f16d3dab3
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "60170031"
---
# <a name="arduino-wiring-porting-guide"></a><span data-ttu-id="46b07-104">Arduino 배선 포팅 가이드</span><span class="sxs-lookup"><span data-stu-id="46b07-104">Arduino Wiring Porting Guide</span></span>

<span data-ttu-id="46b07-105">Arduino 배선 스케치와 라이브러리를 Visual Studio 내부의 Arduino 배선 프로젝트에 복사/붙여 넣고 Raspberry Pi 2, Raspberry Pi 3 또는 Minnowboard Max에서 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46b07-105">Arduino Wiring sketches and libraries can be copy/pasted into an Arduino Wiring project inside Visual Studio and run on Raspberry Pi 2, Raspberry Pi 3 or Minnowboard Max.</span></span> <span data-ttu-id="46b07-106">Windows 환경 또는 작업 중인 보드와의 호환성을 위해 이러한 파일을 변경 해야 하는 경우가 가끔 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46b07-106">Sometimes there are slight modifications that need to be made to these files in order to make them more compatible with the Windows environment, or the board you are working with.</span></span> <span data-ttu-id="46b07-107">이 가이드에서는 Arduino 배선 프로젝트를 배포할 때 발생할 수 있는 일반적인 문제 및 이러한 수정 사항을 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="46b07-107">This guide will cover those modifications as well as common issues that you may run into when deploying Arduino Wiring projects.</span></span>

## <a name="porting"></a><span data-ttu-id="46b07-108">포팅</span><span class="sxs-lookup"><span data-stu-id="46b07-108">Porting</span></span>

### <a name="updating-pins"></a><span data-ttu-id="46b07-109">Pin 업데이트</span><span class="sxs-lookup"><span data-stu-id="46b07-109">Updating Pins</span></span>

<span data-ttu-id="46b07-110">이 경우를 몰라도 되지만 많은 스케치와 라이브러리 (특히 arduino 실드의 경우)에는 Arduino 장치에 대 한 특정 커넥터 핀에 대 한 참조가 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46b07-110">It might go without saying, but many sketches and libraries (especially those for arduino shields) may contain references to specific connector pins for Arduino devices.</span></span> <span data-ttu-id="46b07-111">작업 중인 장치와 사용 중인 구성에 적절 한 커넥터 pin을 사용 하도록 스케치를 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46b07-111">You'll want to customize your sketches to use the appropriate connector pins for the device you are working on and the configuration you are using.</span></span>

<span data-ttu-id="46b07-112">Arduino 와이어링은 궁극적으로 ' 핀 '을 참조 하는 모든 함수에 대 한 실제 커넥터 pin 번호가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="46b07-112">Arduino Wiring ultimately requires a physical connector pin number for any functions that refer to 'pins'.</span></span> <span data-ttu-id="46b07-113">이러한 숫자를 직접 사용할 수 있지만 특정 보드의 커넥터 핀에 해당 하는 미리 정의 된 pin 이름을 제공 했습니다.</span><span class="sxs-lookup"><span data-stu-id="46b07-113">You can use these numbers directly, but we've also provided some pre-defined pin names which correspond to connector pins on specific boards.</span></span>

<span data-ttu-id="46b07-114">예를 들어, Raspberry Pi 2 및 3 `GPIO5`에 대 한 실제 커넥터 29는 라고도 합니다.</span><span class="sxs-lookup"><span data-stu-id="46b07-114">For example, the physical connector pin 29 on a Raspberry Pi 2 and 3 is also known as `GPIO5`.</span></span> <span data-ttu-id="46b07-115">다음 명령 중 하나를 사용 하 여 Raspberry Pi 2 및 3에서 GPIO pin 5를 높은 상태로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46b07-115">You may set GPIO pin 5 to a HIGH state on a Raspberry Pi 2 and 3 by using either of the following commands:</span></span>
```
pinMode( 29, OUTPUT );
digitalWrite( 29, HIGH );
```

<span data-ttu-id="46b07-116">로 구분하거나 여러</span><span class="sxs-lookup"><span data-stu-id="46b07-116">or</span></span>

```
pinMode( GPIO5, OUTPUT );
digitalWrite( GPIO5, HIGH );
```

<span data-ttu-id="46b07-117">미리 정의 된 pin 이름은 pins_arduino에서 찾을 수 있으며 모든 Arduino 배선 프로젝트에 포함 될 수 있지만, 빌드 중인 하드웨어 설정에 따라 사용할 수 있는 다른 실제 커넥터 pin이 있으므로 테이블도 포함 되어 있습니다 [.](https://github.com/ms-iot/lightning/blob/develop/source/pins_arduino.h) 각 장치에 사용할 수 있는 pin 이름을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="46b07-117">The pre-defined pin names can be found in [pins_arduino.h](https://github.com/ms-iot/lightning/blob/develop/source/pins_arduino.h) and included in every Arduino Wiring project, but since there will be different physical connector pins available depending on the hardware setup you are building for, we've also included a table here to describe which pin names are available for each device.</span></span>

#### <a name="raspberry-pi-2-and-3"></a><span data-ttu-id="46b07-118">Raspberry Pi 2 및 3</span><span class="sxs-lookup"><span data-stu-id="46b07-118">Raspberry Pi 2 and 3</span></span>

![핀아웃 다이어그램](../media/ArduinoWiringPortingGuide/RP2_Pinout.png)

> [!div class="mx-tdBreakAll"]
> | <span data-ttu-id="46b07-120">Pin 정의</span><span class="sxs-lookup"><span data-stu-id="46b07-120">Pin Define</span></span> | <span data-ttu-id="46b07-121">해당 Pin 번호</span><span class="sxs-lookup"><span data-stu-id="46b07-121">Corresponding Pin Number</span></span>|
> |-------------|----------|
> | <span data-ttu-id="46b07-122">LED_BUILTIN</span><span class="sxs-lookup"><span data-stu-id="46b07-122">LED_BUILTIN</span></span> | <span data-ttu-id="46b07-123">*온보드 LED*</span><span class="sxs-lookup"><span data-stu-id="46b07-123">*onboard LED*</span></span> |
> | <span data-ttu-id="46b07-124">GPIO \* _여기서 \*는 [0, 27]을 참조 합니다_ .</span><span class="sxs-lookup"><span data-stu-id="46b07-124">GPIO\* _where \* refers to [0, 27]_</span></span> | <span data-ttu-id="46b07-125">*핀아웃 다이어그램 참조*</span><span class="sxs-lookup"><span data-stu-id="46b07-125">*refer to pinout diagram*</span></span> |
> | <span data-ttu-id="46b07-126">GCLK</span><span class="sxs-lookup"><span data-stu-id="46b07-126">GCLK</span></span> | <span data-ttu-id="46b07-127">7</span><span class="sxs-lookup"><span data-stu-id="46b07-127">7</span></span> |
> | <span data-ttu-id="46b07-128">GEN \* _여기서 \*는 [0, 5]를 참조 합니다_ .</span><span class="sxs-lookup"><span data-stu-id="46b07-128">GEN\* _where \* refers to [0, 5]_</span></span> | <span data-ttu-id="46b07-129">\* 핀아웃 다이어그램 참조</span><span class="sxs-lookup"><span data-stu-id="46b07-129">\*refer to pinout diagram</span></span> |
> | <span data-ttu-id="46b07-130">SCL1</span><span class="sxs-lookup"><span data-stu-id="46b07-130">SCL1</span></span> | <span data-ttu-id="46b07-131">5</span><span class="sxs-lookup"><span data-stu-id="46b07-131">5</span></span> |
> | <span data-ttu-id="46b07-132">SDA1</span><span class="sxs-lookup"><span data-stu-id="46b07-132">SDA1</span></span> | <span data-ttu-id="46b07-133">3</span><span class="sxs-lookup"><span data-stu-id="46b07-133">3</span></span> |
> | <span data-ttu-id="46b07-134">CS0 (또는 CE0 또는 SS)</span><span class="sxs-lookup"><span data-stu-id="46b07-134">CS0 (or CE0 or SS)</span></span> | <span data-ttu-id="46b07-135">24</span><span class="sxs-lookup"><span data-stu-id="46b07-135">24</span></span> |
> | <span data-ttu-id="46b07-136">CS1 (또는 CE1)</span><span class="sxs-lookup"><span data-stu-id="46b07-136">CS1 (or CE1)</span></span> | <span data-ttu-id="46b07-137">26</span><span class="sxs-lookup"><span data-stu-id="46b07-137">26</span></span> |
> | <span data-ttu-id="46b07-138">SCLK (또는 SCK)</span><span class="sxs-lookup"><span data-stu-id="46b07-138">SCLK (or SCK)</span></span> | <span data-ttu-id="46b07-139">23</span><span class="sxs-lookup"><span data-stu-id="46b07-139">23</span></span> |
> | <span data-ttu-id="46b07-140">MISO</span><span class="sxs-lookup"><span data-stu-id="46b07-140">MISO</span></span> | <span data-ttu-id="46b07-141">21</span><span class="sxs-lookup"><span data-stu-id="46b07-141">21</span></span> |
> | <span data-ttu-id="46b07-142">MOSI</span><span class="sxs-lookup"><span data-stu-id="46b07-142">MOSI</span></span> | <span data-ttu-id="46b07-143">19</span><span class="sxs-lookup"><span data-stu-id="46b07-143">19</span></span> |
> | <span data-ttu-id="46b07-144">RXD</span><span class="sxs-lookup"><span data-stu-id="46b07-144">RXD</span></span> | <span data-ttu-id="46b07-145">10</span><span class="sxs-lookup"><span data-stu-id="46b07-145">10</span></span> |
> | <span data-ttu-id="46b07-146">트랜잭션</span><span class="sxs-lookup"><span data-stu-id="46b07-146">TXD</span></span> | <span data-ttu-id="46b07-147">8</span><span class="sxs-lookup"><span data-stu-id="46b07-147">8</span></span> |

#### <a name="minnowboard-max"></a><span data-ttu-id="46b07-148">Minnowboard Max</span><span class="sxs-lookup"><span data-stu-id="46b07-148">Minnowboard Max</span></span>

![핀아웃 다이어그램](../media/ArduinoWiringPortingGuide/MBM_Pinout.png)
> [!div class="mx-tdBreakAll"]
> | <span data-ttu-id="46b07-150">Pin 정의</span><span class="sxs-lookup"><span data-stu-id="46b07-150">Pin Define</span></span> | <span data-ttu-id="46b07-151">해당 Pin 번호</span><span class="sxs-lookup"><span data-stu-id="46b07-151">Corresponding Pin Number</span></span>|
> |-------------|----------|
> | <span data-ttu-id="46b07-152">GPIO \* _여기서 \*은 [0, 9]를 참조 합니다_ .</span><span class="sxs-lookup"><span data-stu-id="46b07-152">GPIO\* _where \* refers to [0, 9]_</span></span>  | <span data-ttu-id="46b07-153">*핀아웃 다이어그램 참조*</span><span class="sxs-lookup"><span data-stu-id="46b07-153">*refer to pinout diagram*</span></span> |
> | <span data-ttu-id="46b07-154">SCL</span><span class="sxs-lookup"><span data-stu-id="46b07-154">SCL</span></span> | <span data-ttu-id="46b07-155">13</span><span class="sxs-lookup"><span data-stu-id="46b07-155">13</span></span> |
> | <span data-ttu-id="46b07-156">SDA</span><span class="sxs-lookup"><span data-stu-id="46b07-156">SDA</span></span> | <span data-ttu-id="46b07-157">15</span><span class="sxs-lookup"><span data-stu-id="46b07-157">15</span></span> |
> | <span data-ttu-id="46b07-158">CS0 (또는 CE0 또는 SS)</span><span class="sxs-lookup"><span data-stu-id="46b07-158">CS0 (or CE0 or SS)</span></span> | <span data-ttu-id="46b07-159">5</span><span class="sxs-lookup"><span data-stu-id="46b07-159">5</span></span> |
> | <span data-ttu-id="46b07-160">SCLK (또는 SCK)</span><span class="sxs-lookup"><span data-stu-id="46b07-160">SCLK  (or SCK)</span></span>| <span data-ttu-id="46b07-161">11</span><span class="sxs-lookup"><span data-stu-id="46b07-161">11</span></span> |
> | <span data-ttu-id="46b07-162">MISO</span><span class="sxs-lookup"><span data-stu-id="46b07-162">MISO</span></span> |<span data-ttu-id="46b07-163">7</span><span class="sxs-lookup"><span data-stu-id="46b07-163">7</span></span> |
> | <span data-ttu-id="46b07-164">MOSI</span><span class="sxs-lookup"><span data-stu-id="46b07-164">MOSI</span></span> | <span data-ttu-id="46b07-165">9</span><span class="sxs-lookup"><span data-stu-id="46b07-165">9</span></span> |
> | <span data-ttu-id="46b07-166">CTS1</span><span class="sxs-lookup"><span data-stu-id="46b07-166">CTS1</span></span> | <span data-ttu-id="46b07-167">10</span><span class="sxs-lookup"><span data-stu-id="46b07-167">10</span></span> |
> | <span data-ttu-id="46b07-168">RTS1</span><span class="sxs-lookup"><span data-stu-id="46b07-168">RTS1</span></span> | <span data-ttu-id="46b07-169">12</span><span class="sxs-lookup"><span data-stu-id="46b07-169">12</span></span> |
> | <span data-ttu-id="46b07-170">RX1</span><span class="sxs-lookup"><span data-stu-id="46b07-170">RX1</span></span> | <span data-ttu-id="46b07-171">8</span><span class="sxs-lookup"><span data-stu-id="46b07-171">8</span></span> |
> | <span data-ttu-id="46b07-172">TX1</span><span class="sxs-lookup"><span data-stu-id="46b07-172">TX1</span></span> | <span data-ttu-id="46b07-173">6</span><span class="sxs-lookup"><span data-stu-id="46b07-173">6</span></span> |
> | <span data-ttu-id="46b07-174">RX2</span><span class="sxs-lookup"><span data-stu-id="46b07-174">RX2</span></span> | <span data-ttu-id="46b07-175">19</span><span class="sxs-lookup"><span data-stu-id="46b07-175">19</span></span> |
> | <span data-ttu-id="46b07-176">TX2</span><span class="sxs-lookup"><span data-stu-id="46b07-176">TX2</span></span> | <span data-ttu-id="46b07-177">17</span><span class="sxs-lookup"><span data-stu-id="46b07-177">17</span></span> |


## <a name="common-problems"></a><span data-ttu-id="46b07-178">일반적인 문제</span><span class="sxs-lookup"><span data-stu-id="46b07-178">Common Problems</span></span>

### <a name="cant-find-arduino-wiring-application-visual-c-project-template-in-visual-studio"></a><span data-ttu-id="46b07-179">Visual Studio에서 "Arduino 배선 응용 프로그램 C++ " 시각적 프로젝트 템플릿을 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="46b07-179">Can't find "Arduino Wiring Application" Visual C++ project template in Visual Studio</span></span>

<span data-ttu-id="46b07-180">**원인**: Visual Studio 용 Windows IoT 프로젝트 템플릿 확장이 설치 되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="46b07-180">**Cause**: The Windows IoT Project Templates extension for Visual Studio is not installed.</span></span>

<span data-ttu-id="46b07-181">**해결 방법**: Visual Studio에서 Arduino 배선 프로젝트를 만들려면 먼저 Windows IoT 용 Visual Studio 확장 프로젝트 템플릿을 설치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="46b07-181">**Solution**: You must install the Visual Studio Extension for Windows IoT Project Templates before you can create Arduino Wiring projects in Visual Studio.</span></span> <span data-ttu-id="46b07-182">[Windows IoT Core 프로젝트 템플릿 확장 페이지로](https://go.microsoft.com/fwlink/?linkid=847472) 이동 하 여 Visual Studio 갤러리에서 확장을 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="46b07-182">Head over to [Windows IoT Core Project Templates extension page](https://go.microsoft.com/fwlink/?linkid=847472) to download the extension from the Visual Studio Gallery!</span></span>

### <a name="error-identifier-not-found-when-calling-a-function"></a><span data-ttu-id="46b07-183">오류: 함수를 호출 하는 동안 "식별자를 찾을 수 없습니다."</span><span class="sxs-lookup"><span data-stu-id="46b07-183">ERROR: "identifier not found" when calling a function</span></span>

<span data-ttu-id="46b07-184">**원인**: 이 오류는 문서에서 아직 선언 되지 않은 함수를 호출할 때 링커 프로세스 중에 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="46b07-184">**Cause**: This error occurs during the linker process when a function is invoked that has not yet been declared in the document.</span></span>

<span data-ttu-id="46b07-185">**해결 방법**: 에서는 C++모든 함수를 호출 하기 전에 선언 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="46b07-185">**Solution**: In C++, all functions must be declared before they are invoked.</span></span> <span data-ttu-id="46b07-186">스케치 파일에 새 함수를 정의한 경우 함수를 호출 하는 데 필요한 선언 또는 전체 구현에서이 함수를 호출 해야 합니다 (일반적으로 문서 맨 위).</span><span class="sxs-lookup"><span data-stu-id="46b07-186">If you have defined a new function in your sketch file, either the declaration or the entire implementation of the function must be above any attempts to invoke it (typically at the top of the document).</span></span>

<span data-ttu-id="46b07-187">**예**:</span><span class="sxs-lookup"><span data-stu-id="46b07-187">**Example**:</span></span>

<span data-ttu-id="46b07-188">다음 코드 블록은 "' myFunction ': 식별자를 찾을 수 없음" 오류를 발생 시킵니다.</span><span class="sxs-lookup"><span data-stu-id="46b07-188">The following block of code will raise the error "'myFunction': identifier not found"</span></span>

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

<span data-ttu-id="46b07-189">두 가지 솔루션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46b07-189">There are two solutions.</span></span> <span data-ttu-id="46b07-190">먼저 모든 호출 위에 함수를 선언할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46b07-190">First, you may declare the function above any invocations.</span></span> <span data-ttu-id="46b07-191">일반적으로이 선언은 파일 위쪽에서 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="46b07-191">Typically, this declaration is done at the top of the file.</span></span>

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

<span data-ttu-id="46b07-192">또는 함수의 전체 구현을 모든 호출 위로 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46b07-192">Alternatively, you can move the entire implementation of the function above any invocations.</span></span> <span data-ttu-id="46b07-193">이 경우 함수를 동시에 선언 하 고 정의 하는 효과가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46b07-193">This has the effect of both declaring and defining the function at the same time.</span></span>

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

### <a name="my-solution-hangs-infinitely-when-being-initialized"></a><span data-ttu-id="46b07-194">초기화 될 때 내 솔루션이 무한히 중단 됨</span><span class="sxs-lookup"><span data-stu-id="46b07-194">My solution hangs infinitely when being initialized</span></span>

<span data-ttu-id="46b07-195">초기화 될 때 C++ 솔루션이 무한히 중단 (교착 상태)을 일으킬 수 있는 알려진 문제가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46b07-195">There is a known issue which can cause a C++ solution to hang infinitely (deadlock) when being initialized.</span></span> <span data-ttu-id="46b07-196">솔루션이 중단 된 것 처럼 보이고 디버거를 사용 하 여 Arduino 배선 응용 프로그램의 setup () 또는 loop () 섹션에 있는 모든 문에 ' 중단 ' 하는 경우이 문제가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46b07-196">You may be experiencing this type of issue if you find that your solution appears to hang forever and you are unable to use the debugger to 'break in' to any statement in the setup() or loop() sections of your Arduino Wiring application.</span></span>

<span data-ttu-id="46b07-197">**원인**: 솔루션의 초기화가 완료 되기 전에 asyncronous 작업을 수행 하는 함수가 생성 되거나 함수가 호출 되 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46b07-197">**Cause**: An object is being created or a function is being called which leads to an asyncronous action before the solution has finished initializing.</span></span> <span data-ttu-id="46b07-198">개체의 생성자가와 같은 `pinMode`API 함수를 호출 하는 경우에 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46b07-198">It is likely caused from an object's constructor calling an API function like `pinMode`.</span></span>

<span data-ttu-id="46b07-199">**해결 방법**: 모든 개체 생성자 및 함수 호출을 코드의 초기화 섹션과 `setup()` 블록으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="46b07-199">**Solution**: Move any object constructors and function calls away from the initialization section of code and into the `setup()` block.</span></span>

<span data-ttu-id="46b07-200">**예 1**:</span><span class="sxs-lookup"><span data-stu-id="46b07-200">**Example 1**:</span></span>

<span data-ttu-id="46b07-201">이 스케치의 실행은 솔루션 자체가 초기화 되기 `setPinModes()` 전에 호출 되는 함수를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="46b07-201">The execution of this sketch calls a function called `setPinModes()` before the solution itself has been initialized.</span></span> <span data-ttu-id="46b07-202">솔루션이 실행 되는 것 처럼 보이지만 무한히 중단 됩니다.</span><span class="sxs-lookup"><span data-stu-id="46b07-202">The solution will appear to execute but will hang infinitely.</span></span>

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

<span data-ttu-id="46b07-203">이 솔루션은 아래와 같이 단순히 실행 `setPinModes()` `setup()` 을 함수로 이동 했습니다.</span><span class="sxs-lookup"><span data-stu-id="46b07-203">The solution is below, we've simply moved the execution of `setPinModes()` to the `setup()` function:</span></span>

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

<span data-ttu-id="46b07-204">**예 2**:</span><span class="sxs-lookup"><span data-stu-id="46b07-204">**Example 2**:</span></span>

<span data-ttu-id="46b07-205">이 스케치를 실행 하면가 호출 되기 전에 `setup()` 스택에서 개체가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="46b07-205">The execution of this sketch creates an object on the stack before `setup()` has been called.</span></span> <span data-ttu-id="46b07-206">개체는 생성자에서 `pinMode` 를 호출 하므로 교착 상태가 발생 하기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="46b07-206">Since the object calls `pinMode` in its constructor, this will also cause a deadlock.</span></span> <span data-ttu-id="46b07-207">이러한 문제는 드문 경우 지만 특정 라이브러리 (예: Arduino `LiquidCrystal` 라이브러리)의 개체에 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46b07-207">This is an uncommon issue, but may occur with objects from certain libraries (like the Arduino `LiquidCrystal` library).</span></span>

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

<span data-ttu-id="46b07-208">해결 방법은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="46b07-208">The solution is below.</span></span> <span data-ttu-id="46b07-209">개체를 개체 포인터로 변경 하 고 개체 초기화를로 `setup()`이동 했습니다.</span><span class="sxs-lookup"><span data-stu-id="46b07-209">We've changed the object to an object pointer and moved the initialization of the object to `setup()`.</span></span>

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

### <a name="using-serialprint-and-serialprintln"></a><span data-ttu-id="46b07-210">및 `Serial.print()` 사용`Serial.println()`</span><span class="sxs-lookup"><span data-stu-id="46b07-210">Using `Serial.print()` and `Serial.println()`</span></span>

<span data-ttu-id="46b07-211">많은 Arduino 스케치는 `Serial` 데이터를 직렬 콘솔에 인쇄 하거나 (열려 있는 경우) 직렬 회선 (USB 또는 tx/rx)에 쓰는 데 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="46b07-211">Many Arduino sketches use `Serial` to print data to the serial console (if opened) or to write to the serial lines (USB or tx/rx).</span></span> <span data-ttu-id="46b07-212">이전 버전의 라이트닝 SDK에서는 하드웨어 `Serial` 지원이 포함 되지 않았기 때문에 Visual Studio의 디버거 출력 창에 인쇄 되는 `Log()` 함수를 제공 했습니다.</span><span class="sxs-lookup"><span data-stu-id="46b07-212">In prior versions of the Lightning SDK, Hardware `Serial` support wasn't included, so we provided a `Log()` function which will print to the debugger output window in Visual Studio.</span></span> <span data-ttu-id="46b07-213">`Serial.print*()`또는 `Serial.write()` 를 제거 해야 했습니다.</span><span class="sxs-lookup"><span data-stu-id="46b07-213">`Serial.print*()` or `Serial.write()` had to be removed.</span></span>

<span data-ttu-id="46b07-214">그러나 _라이트닝 SDK v 1.1.0_부터 지원을 추가 `Hardware Serial` 하 고 또는 `Serial.write()` 함수를 모두 `Serial.print*()` 완전히 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="46b07-214">However, starting with _Lightning SDK v1.1.0_, we've added `Hardware Serial` support and both `Serial.print*()` or `Serial.write()` functions are fully supported.</span></span> <span data-ttu-id="46b07-215">따라서 Arduino에 대해 빌드된 스케치를 복사 하는 경우에는 Windows IoT 버전의 스케치에서 이러한 직렬 참조를 바꿀 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="46b07-215">So, if you are copying a sketch built for an Arduino, you won't need to replace any of these Serial references in the Windows IoT version of the sketch.</span></span>

<span data-ttu-id="46b07-216">또한 및의 `Serial.print()` 기능을 확장 하 고, `Serial.println()`디버거가 연결 될 때 디버거 창에 출력 하 고, 하드웨어 직렬 핀에 쓰기를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="46b07-216">Furthermore, we've extended the functionality of `Serial.print()` and `Serial.println()`, to output to the debugger window when a debugger is attached - in addition to writing to the hardware serial pins.</span></span>
<span data-ttu-id="46b07-217">디버그 출력은 해당 출력을 읽을 때 대부분의 사용자가 해당 스케치를 실행할 때 사용할 수 있는 것 이므로 기본값으로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="46b07-217">The debug output printing is set as the default since reading that output is what most users would want when running their sketches.</span></span> <span data-ttu-id="46b07-218">그러나이 기능을 사용 하지 않도록 설정할 수도 있습니다. 예를 들어 성능을 향상 시키려면를 호출 `Serial.enablePrintDebugOutput(false);` 하 여 스케치에서 사용 하지 않도록 설정 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="46b07-218">However, that functionality can be disabled as well; e.g. to improve performance, simply call `Serial.enablePrintDebugOutput(false);` to disable it in your sketch.</span></span> <span data-ttu-id="46b07-219">다시 사용 하도록 설정 하려면를 호출 `Serial.enablePrintDebugOutput(true);`합니다.</span><span class="sxs-lookup"><span data-stu-id="46b07-219">To re-enable it, call `Serial.enablePrintDebugOutput(true);`.</span></span> <span data-ttu-id="46b07-220">하드웨어 직렬 pin에 대 한 쓰기는 해당 호출의 영향을 받지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="46b07-220">Writing to the hardware serial pins is not affected by those calls.</span></span>

<span data-ttu-id="46b07-221">디버거 창으로 전송 되는 출력을 가져오기 위해 FTDI와 같은 직렬 핀에는 주변 장치를 연결할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="46b07-221">Note, you do NOT need to attach any peripheral to your serial pins such as an FTDI, to get output sent to the debugger window.</span></span> <span data-ttu-id="46b07-222">그러나 응용 프로그램을 디버깅 하는 동안 디버거 창이 열려 있는지 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="46b07-222">However, you'll need to make sure the debugger window is open while your application is being debugged.</span></span>

![디버거 출력](../media/ArduinoWiringPortingGuide/debugger_output.png)

<span data-ttu-id="46b07-224">기본 하드웨어 `Serial` 를 사용할 수 있도록 [Windows IoT Core 프로젝트 템플릿 확장 페이지](https://go.microsoft.com/fwlink/?linkid=847472) 에서 프로젝트 템플릿이 업데이트 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="46b07-224">The project templates have been updated on the [Windows IoT Core Project Templates extension page](https://go.microsoft.com/fwlink/?linkid=847472) to enable using Hardware `Serial` out of the box.</span></span> <span data-ttu-id="46b07-225">그러나 이전 프로젝트 템플릿 버전을 사용 하 여 Arduino 배선 응용 프로그램을 이미 만든 경우에는 1) 프로젝트를 최신 번개 SDK, v 1.1.0 이상으로 업그레이드 하 고 2) 필요한 하드웨어 직렬 장치 기능을에 추가 해야 합니다. 사용할 `Serial`수 있는 appxmanifest.xml입니다.</span><span class="sxs-lookup"><span data-stu-id="46b07-225">However, if your Arduino Wiring application has already been created using an older project template version, you'll need to 1) Upgrade your project to the latest Lightning SDK, v1.1.0 or later, and 2) add the required Hardware Serial device capability to your AppxManifest to be able to use `Serial`.</span></span>

### <a name="hardware-serial-device-capability-requirements"></a><span data-ttu-id="46b07-226">하드웨어 직렬 장치 기능 요구 사항</span><span class="sxs-lookup"><span data-stu-id="46b07-226">Hardware Serial device capability requirements</span></span>

<span data-ttu-id="46b07-227">Windows 10 IoT Core의 하드웨어 직렬 기능을 사용 하려면 장치 기능 선언이 AppX 매니페스트에 추가 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="46b07-227">Hardware Serial functionality in Windows 10 IoT Core requires device capability declarations added to the AppX manifest.</span></span>

<span data-ttu-id="46b07-228">솔루션 탐색기에서 `Package.appxmanifest` 파일 이름을 입력 하 여 프로젝트에서 파일을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="46b07-228">Find the file `Package.appxmanifest` in your project, by typing the file name in the solution explorer.</span></span> <span data-ttu-id="46b07-229">그런 다음 파일을 마우스 오른쪽 단추로 클릭 하 고 ' 연결 프로그램 ... '을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="46b07-229">Then, right click the file and choose 'Open With...'.</span></span> <span data-ttu-id="46b07-230">' XML (텍스트) 편집기 '를 선택 하 고 ' 확인 '을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="46b07-230">Choose 'XML (Text) Editor' and click 'OK'.</span></span>

![Appxmanifest.xml를 업데이트 하는 중](../media/ArduinoWiringPortingGuide/appxmanifest_search.png)

<span data-ttu-id="46b07-232">Appx 매니페스트 파일 편집기에서 다음 XML 코드 조각과 `serialcommunication` 같이 DeviceCapability를 프로젝트에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="46b07-232">In the appx manifest file editor, add the `serialcommunication` DeviceCapability to your project as in the following XML snippet:</span></span>

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

### <a name="upgrade-your-project-to-the-latest-lightning-sdk"></a><span data-ttu-id="46b07-233">프로젝트를 최신 번개 SDK로 업그레이드</span><span class="sxs-lookup"><span data-stu-id="46b07-233">Upgrade your project to the latest Lightning SDK</span></span>

<span data-ttu-id="46b07-234">Arduino 배선 프로젝트는 라이트닝 [SDK Nuget 패키지](https://www.nuget.org/packages/Microsoft.IoT.Lightning/) 를 사용 하 여 필요한 Arduino 배선 함수 및 선언 뿐만 아니라 번개 드라이버로의 인터페이스를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="46b07-234">The Arduino Wiring projects depend on the [Lightning SDK Nuget package](https://www.nuget.org/packages/Microsoft.IoT.Lightning/) to implement the required Arduino Wiring functions and declarations as well as interface with the Lightning driver.</span></span> <span data-ttu-id="46b07-235">최신 라이트닝 SDK에는 최신 향상 된 기능 및 버그 수정이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="46b07-235">The latest Lightning SDK will contain the latest improvements and bug fixes.</span></span> <span data-ttu-id="46b07-236">최신 라이트닝 SDK로 업그레이드 하려면 다음 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="46b07-236">To upgrade to the latest Lightning SDK, follow these steps:</span></span>

- <span data-ttu-id="46b07-237">솔루션 탐색기에서 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 ' Nuget 패키지 관리 ... '를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="46b07-237">In the Solution Explorer, right click on your project and click 'Manage Nuget Packages...'</span></span>
- <span data-ttu-id="46b07-238">NuGet 패키지 관리자에서 ' 설치 됨 ' 탭으로 이동 합니다. 설치 된 Microsoft. a. a. a.</span><span class="sxs-lookup"><span data-stu-id="46b07-238">In the NuGet Package Manager, go to the 'Installed' tab. You should see the Microsoft.IoT.Lightning package installed</span></span>
- <span data-ttu-id="46b07-239">사용 가능한 버전이 ' 버전 ' combobox 안에 나열 됩니다.</span><span class="sxs-lookup"><span data-stu-id="46b07-239">Available versions will be listed inside the 'Version' combobox.</span></span>
- <span data-ttu-id="46b07-240">최신 버전을 선택 하 고 ' 업데이트 '를 클릭 하 여 패키지를 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="46b07-240">Choose the latest version, and click 'Update' to update your package.</span></span>
- <span data-ttu-id="46b07-241">시험판 버전으로 업그레이드 하려면 ' 시험판 포함 ' 확인란을 선택 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="46b07-241">Notice, to upgrade to a prerelease version, make sure to check the 'Include prerelease' checkbox as well.</span></span>

![NuGet 패키지 관리자](../media/ArduinoWiringPortingGuide/Nuget_PackageManager.png)
