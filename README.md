## <a name="microsoft-open-source-code-of-conduct"></a><span data-ttu-id="b3e8b-101">Microsoft 오픈 소스 준수 코드</span><span class="sxs-lookup"><span data-stu-id="b3e8b-101">Microsoft Open Source Code of Conduct</span></span>

<span data-ttu-id="b3e8b-102">이 프로젝트는 [Microsoft 오픈 소스 준수 사항](https://opensource.microsoft.com/codeofconduct/)을 채택했습니다.</span><span class="sxs-lookup"><span data-stu-id="b3e8b-102">This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).</span></span>
<span data-ttu-id="b3e8b-103">자세한 내용은 [준수 사항 FAQ](https://opensource.microsoft.com/codeofconduct/faq/) 를 참조하고, 추가 질문이나 의견이 있는 경우 [opencode@microsoft.com](mailto:opencode@microsoft.com) 에 문의하세요.</span><span class="sxs-lookup"><span data-stu-id="b3e8b-103">For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.</span></span>

# <a name="how-to-contribute-to-windows-10-iotcore-documentation"></a><span data-ttu-id="b3e8b-104">Windows 10 IoTCore 설명서에 기여하는 방법</span><span class="sxs-lookup"><span data-stu-id="b3e8b-104">How to contribute to Windows 10 IoTCore documentation</span></span>

## <a name="legal-notices"></a><span data-ttu-id="b3e8b-105">법적 고지 사항</span><span class="sxs-lookup"><span data-stu-id="b3e8b-105">Legal Notices</span></span>
<span data-ttu-id="b3e8b-106">Microsoft와 모든 기여자는 [Creative Commons Attribution 4.0 국제 공개 라이선스](https://creativecommons.org/licenses/by/4.0/legalcode)에 따라 귀하에게 이 리포지토리의 Microsoft 설명서 및 기타 콘텐츠에 대한 라이선스([LICENSE](LICENSE) 파일 참조)를 부여하고, [MIT 라이선스](https://opensource.org/licenses/MIT)에 따라 귀하에게 리포지토리의 모든 코드에 대한 라이선스([LICENSE-CODE](LICENSE-CODE) 파일 참조)를 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="b3e8b-106">Microsoft and any contributors grant you a license to the Microsoft documentation and other content in this repository under the [Creative Commons Attribution 4.0 International Public License](https://creativecommons.org/licenses/by/4.0/legalcode), see the [LICENSE](LICENSE) file, and grant you a license to any code in the repository under the [MIT License](https://opensource.org/licenses/MIT), see the [LICENSE-CODE](LICENSE-CODE) file.</span></span>

<span data-ttu-id="b3e8b-107">Microsoft, Windows, Microsoft Azure 및/또는 기타 이 설명서에 언급된 Microsoft 제품 및 서비스는 미국 및/또는 기타 국가에서 Microsoft의 상표 또는 등록 상표일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3e8b-107">Microsoft, Windows, Microsoft Azure and/or other Microsoft products and services referenced in the documentation may be either trademarks or registered trademarks of Microsoft in the United States and/or other countries.</span></span>
<span data-ttu-id="b3e8b-108">이 프로젝트에 대한 라이선스는 귀하에게 Microsoft 이름, 로고 또는 상표를 사용할 권한을 부여하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b3e8b-108">The licenses for this project do not grant you rights to use any Microsoft names, logos, or trademarks.</span></span>
<span data-ttu-id="b3e8b-109">Microsoft의 일반 상표 지침은 http://go.microsoft.com/fwlink/?LinkID=254653 에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3e8b-109">Microsoft's general trademark guidelines can be found at http://go.microsoft.com/fwlink/?LinkID=254653.</span></span>

<span data-ttu-id="b3e8b-110">개인 정보는 https://privacy.microsoft.com/en-us/ 에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3e8b-110">Privacy information can be found at https://privacy.microsoft.com/en-us/</span></span>

<span data-ttu-id="b3e8b-111">Microsoft와 모든 기여자는 관련 저작권, 특허 또는 상표에 따라 묵시적, 금반언적 또는 다른 방식으로 다른 모든 권리를 보유합니다.</span><span class="sxs-lookup"><span data-stu-id="b3e8b-111">Microsoft and any contributors reserve all others rights, whether under their respective copyrights, patents, or trademarks, whether by implication, estoppel or otherwise.</span></span>

## <a name="contributing"></a><span data-ttu-id="b3e8b-112">기여</span><span class="sxs-lookup"><span data-stu-id="b3e8b-112">Contributing</span></span>

<span data-ttu-id="b3e8b-113">이는 [https://docs.microsoft.com/windows/iot-core](https://docs.microsoft.com/windows/iot-core)에서 호스팅되는 Windows 10 IoT **설명서**의 리포지토리입니다.</span><span class="sxs-lookup"><span data-stu-id="b3e8b-113">This is the repository for Windows 10 IoT **documentation** hosted at [https://docs.microsoft.com/windows/iot-core](https://docs.microsoft.com/windows/iot-core).</span></span>

<span data-ttu-id="b3e8b-114">새 적용 범위를 보거나 피드백을 받으려면 [**기여**](/CONTRIBUTING.md)하는 것도 고려해보세요.</span><span class="sxs-lookup"><span data-stu-id="b3e8b-114">If you would like to see new coverage or have feedback, please consider [**contributing**](/CONTRIBUTING.md).</span></span>  <span data-ttu-id="b3e8b-115">기존 콘텐츠를 편집하거나, 새 콘텐츠를 추가하거나, 새 [이슈](https://github.com/MicrosoftDocs/windows-iotcore-docs/issues)를 만들면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3e8b-115">You can edit the existing content, add new content, or simply create new [issues](https://github.com/MicrosoftDocs/windows-iotcore-docs/issues).</span></span> <span data-ttu-id="b3e8b-116">제안을 살펴보고 함께 협력하여 문서에 통합할 것입니다.</span><span class="sxs-lookup"><span data-stu-id="b3e8b-116">We’ll take a look at your suggestions and will work together to incorporate them into the docs.</span></span>

<span data-ttu-id="b3e8b-117">콘텐츠를 편집하려면 변경하려는 문서에서 클릭만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3e8b-117">To edit content, just click edit on the article you want to make changes to:</span></span>

![문서 편집 방법에 대한 Gif](windows-iotcore/media/edit-doc.gif)


<span data-ttu-id="b3e8b-119">변경하기 위해 리포지토리를 복제하거나 다운로드할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3e8b-119">You can also clone or download the repo to make changes:</span></span>

![리포지토리를 복제하거나 다운로드하는 방법에 대한 Gif](windows-iotcore/media/download-repo.gif)

<span data-ttu-id="b3e8b-121">또한 끌어오기 요청에 리뷰어 또는 리뷰를 추가하여 승인을 받아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3e8b-121">You will also need to add a reviewer or reviews to your pull requests to get them approved:</span></span>

![끌어오기 요청에 리뷰어 추가](windows-iotcore/media/reviewers.gif)

# <a name="conventions"></a><span data-ttu-id="b3e8b-123">규칙</span><span class="sxs-lookup"><span data-stu-id="b3e8b-123">Conventions</span></span>
  - <span data-ttu-id="b3e8b-124">페이지를 추가할 때 페이지를 표시하려면 [toc.md](windows-iotcore/TOC.md)에 항목을 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3e8b-124">When adding a page, you must add an entry for it in [toc.md](windows-iotcore/TOC.md) for it to appear.</span></span>
  - <span data-ttu-id="b3e8b-125">폴더에는 추가 폴더 또는 `readme.md`가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3e8b-125">A folder can contain more folders or `readme.md`s</span></span>
  - <span data-ttu-id="b3e8b-126">폴더/디렉터리 이름은 대시 구분(예: `f12-tools`) 및 소문자로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3e8b-126">Folder/directory names are dash-separated (e.g., `f12-tools`) and lowercase.</span></span> <span data-ttu-id="b3e8b-127">이는 docs.microsoft.com 사이트의 URL에서 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3e8b-127">They are used in URLs on the docs.microsoft.com site.</span></span> <span data-ttu-id="b3e8b-128">밑줄 또는 PascalCase/camelCase를 사용하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="b3e8b-128">Don't use underscores or PascalCase/camelCase.</span></span>


## <a name="other-text-elements"></a><span data-ttu-id="b3e8b-129">기타 텍스트 요소</span><span class="sxs-lookup"><span data-stu-id="b3e8b-129">Other text elements</span></span>

<span data-ttu-id="b3e8b-130">이러한 기타 텍스트에는 다음과 같은 스타일 지정을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3e8b-130">These other text elements have styling available:</span></span>

* <span data-ttu-id="b3e8b-131">순서가 지정되지 않은 목록</span><span class="sxs-lookup"><span data-stu-id="b3e8b-131">Unordered lists</span></span>
* <span data-ttu-id="b3e8b-132">일반 글머리 기호가 있음</span><span class="sxs-lookup"><span data-stu-id="b3e8b-132">Have regular bullets</span></span>
   * <span data-ttu-id="b3e8b-133">글머리 기호를 중첩할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3e8b-133">You can also nest bullets</span></span>
   * <span data-ttu-id="b3e8b-134">글머리 기호 목록에는 둘 이상의 항목이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3e8b-134">Bullets lists should have more than one entry.</span></span>
* <span data-ttu-id="b3e8b-135">좋은 표준</span><span class="sxs-lookup"><span data-stu-id="b3e8b-135">Pretty standard</span></span>

1. <span data-ttu-id="b3e8b-136">순서가 지정된 목록</span><span class="sxs-lookup"><span data-stu-id="b3e8b-136">Ordered lists</span></span>
2. <span data-ttu-id="b3e8b-137">일반 ol western 스타일 번호 매기기를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b3e8b-137">Use regular ol' western-style numbering.</span></span>
3. <span data-ttu-id="b3e8b-138">목록에 실제로 순서가 있는 경우에만 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3e8b-138">Should be used only when a list truly has order.</span></span>

_________________________

<span data-ttu-id="b3e8b-139">수평 규칙을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3e8b-139">Horizontal rules are available.</span></span> <span data-ttu-id="b3e8b-140">혼란을 줄이기 위해 제한적으로 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="b3e8b-140">We suggest using them sparingly to reduce clutter.</span></span>
<span data-ttu-id="b3e8b-141">수평 규칙을 제목 태그와 결합하지 마세요. 일부는 이미 시각적 계층 구조에 선 스타일을 사용했습니다.</span><span class="sxs-lookup"><span data-stu-id="b3e8b-141">Do not combine horizontal rules with heading tags; some already used line styles for visual hierarchy.</span></span>
<span data-ttu-id="b3e8b-142">또한 번호가 매겨진 목록의 중간에 메모(아래 참조)를 결합하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="b3e8b-142">Also, do not combine notes (see below) in the middle of numbered lists.</span></span> <span data-ttu-id="b3e8b-143">이는 번호 매기기 순서를 엉망으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b3e8b-143">This messes with the numbering order.</span></span>

## <a name="displaying-code"></a><span data-ttu-id="b3e8b-144">코드 표시</span><span class="sxs-lookup"><span data-stu-id="b3e8b-144">Displaying code</span></span>

<span data-ttu-id="b3e8b-145">인라인 `code` Markdown 구문(backtick 포함)을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3e8b-145">You can use inline `code` Markdown syntax (with the backticks).</span></span>

<span data-ttu-id="b3e8b-146">또는 다음과 같은 코드 블록을 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3e8b-146">Or you can display blocks of code like so:</span></span>

```css
body {
    background: #fff;
}
```

## <a name="tables"></a><span data-ttu-id="b3e8b-147">테이블</span><span class="sxs-lookup"><span data-stu-id="b3e8b-147">Tables</span></span>

| <span data-ttu-id="b3e8b-148">이 경우</span><span class="sxs-lookup"><span data-stu-id="b3e8b-148">You can</span></span>     | <span data-ttu-id="b3e8b-149">헤더 사용</span><span class="sxs-lookup"><span data-stu-id="b3e8b-149">use headers</span></span> | <span data-ttu-id="b3e8b-150">테이블에</span><span class="sxs-lookup"><span data-stu-id="b3e8b-150">on tables</span></span>    |
|-------------|-------------|-------------:|
| <span data-ttu-id="b3e8b-151">왼쪽 맞춤</span><span class="sxs-lookup"><span data-stu-id="b3e8b-151">Left-aligned</span></span>| <span data-ttu-id="b3e8b-152">#이 아닌 경우</span><span class="sxs-lookup"><span data-stu-id="b3e8b-152">Unless a #</span></span>  | <span data-ttu-id="b3e8b-153">456</span><span class="sxs-lookup"><span data-stu-id="b3e8b-153">456</span></span>          |
| <span data-ttu-id="b3e8b-154">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="b3e8b-154">Text value</span></span>  | <span data-ttu-id="b3e8b-155">자세한 텍스트</span><span class="sxs-lookup"><span data-stu-id="b3e8b-155">More text</span></span>   | <span data-ttu-id="b3e8b-156">$0.00</span><span class="sxs-lookup"><span data-stu-id="b3e8b-156">$0.00</span></span>        |

## <a name="notes"></a><span data-ttu-id="b3e8b-157">메모</span><span class="sxs-lookup"><span data-stu-id="b3e8b-157">Notes</span></span>

<span data-ttu-id="b3e8b-158">메모를 제한적으로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b3e8b-158">Use notes sparingly.</span></span> <span data-ttu-id="b3e8b-159">"누락하지 마세요" 정보를 강조 표시하도록 설계된 블록입니다.</span><span class="sxs-lookup"><span data-stu-id="b3e8b-159">They are blocks designed to highlight "don't-miss-it" information.</span></span>

<span data-ttu-id="b3e8b-160">현재 스타일이 지정된 네 개의 서로 다른 버전이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3e8b-160">We have four different versions of notes currently styled:</span></span>
- <span data-ttu-id="b3e8b-161">참고</span><span class="sxs-lookup"><span data-stu-id="b3e8b-161">NOTE</span></span>
- <span data-ttu-id="b3e8b-162">경고</span><span class="sxs-lookup"><span data-stu-id="b3e8b-162">WARNING</span></span>
- <span data-ttu-id="b3e8b-163">팁</span><span class="sxs-lookup"><span data-stu-id="b3e8b-163">TIP</span></span>
- <span data-ttu-id="b3e8b-164">중요</span><span class="sxs-lookup"><span data-stu-id="b3e8b-164">IMPORTANT</span></span>


<span data-ttu-id="b3e8b-165">여러 줄 블록 따옴표 메모의 경우 아래 예제와 같이 메모의 각 행 줄 앞에 >를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b3e8b-165">For multi-line blockquote notes, use a > in front of each line of the notes as seen in the example below.</span></span>

## <a name="images"></a><span data-ttu-id="b3e8b-166">이미지</span><span class="sxs-lookup"><span data-stu-id="b3e8b-166">Images</span></span>

<span data-ttu-id="b3e8b-167">이미지는 `media` 폴더에 저장되고 상대 경로로 참조되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3e8b-167">Images should be stored in a `media` folder and referenced with a relative path:</span></span>

`![Note patterns](media/notes.png)`


## <a name="code-of-conduct"></a><span data-ttu-id="b3e8b-168">준수 사항</span><span class="sxs-lookup"><span data-stu-id="b3e8b-168">Code of Conduct</span></span>
<span data-ttu-id="b3e8b-169">이 프로젝트는 [Microsoft 오픈 소스 준수 사항](https://opensource.microsoft.com/codeofconduct/)을 채택했습니다.</span><span class="sxs-lookup"><span data-stu-id="b3e8b-169">This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).</span></span> <span data-ttu-id="b3e8b-170">자세한 내용은 [준수 사항 FAQ](https://opensource.microsoft.com/codeofconduct/faq/) 를 참조하고, 추가 질문이나 의견이 있는 경우 [opencode@microsoft.com](mailto:opencode@microsoft.com) 에 문의하세요.</span><span class="sxs-lookup"><span data-stu-id="b3e8b-170">For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.</span></span>
