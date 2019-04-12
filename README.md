## <a name="microsoft-open-source-code-of-conduct"></a><span data-ttu-id="bb97e-101">Microsoft 오픈 소스 준수 사항</span><span class="sxs-lookup"><span data-stu-id="bb97e-101">Microsoft Open Source Code of Conduct</span></span>

<span data-ttu-id="bb97e-102">이 프로젝트에 도입 된 [Microsoft 오픈 소스 준수 사항](https://opensource.microsoft.com/codeofconduct/)합니다.</span><span class="sxs-lookup"><span data-stu-id="bb97e-102">This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).</span></span>
<span data-ttu-id="bb97e-103">자세한 내용은 참조는 [준수 사항 FAQ](https://opensource.microsoft.com/codeofconduct/faq/) 에 문의 하거나 [ opencode@microsoft.com ](mailto:opencode@microsoft.com) 추가 질문이 나 의견을 사용 하 여 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb97e-103">For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.</span></span>

# <a name="how-to-contribute-to-windows-10-iotcore-documentation"></a><span data-ttu-id="bb97e-104">Windows 10 IoTCore 설명서에 기여 하는 방법</span><span class="sxs-lookup"><span data-stu-id="bb97e-104">How to contribute to Windows 10 IoTCore documentation</span></span>

## <a name="legal-notices"></a><span data-ttu-id="bb97e-105">법적 고지 사항</span><span class="sxs-lookup"><span data-stu-id="bb97e-105">Legal Notices</span></span>
<span data-ttu-id="bb97e-106">Microsoft와 모든 기여자는 [Creative Commons Attribution 4.0 국제 공개 라이선스](https://creativecommons.org/licenses/by/4.0/legalcode)에 따라 귀하에게 이 리포지토리의 Microsoft 설명서 및 기타 콘텐츠에 대한 라이선스([LICENSE](LICENSE) 파일 참조)를 부여하고, [MIT 라이선스](https://opensource.org/licenses/MIT)에 따라 귀하에게 리포지토리의 모든 코드에 대한 라이선스([LICENSE-CODE](LICENSE-CODE) 파일 참조)를 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="bb97e-106">Microsoft and any contributors grant you a license to the Microsoft documentation and other content in this repository under the [Creative Commons Attribution 4.0 International Public License](https://creativecommons.org/licenses/by/4.0/legalcode), see the [LICENSE](LICENSE) file, and grant you a license to any code in the repository under the [MIT License](https://opensource.org/licenses/MIT), see the [LICENSE-CODE](LICENSE-CODE) file.</span></span>

<span data-ttu-id="bb97e-107">Microsoft, Windows, Microsoft Azure 및/또는 기타 이 설명서에 언급된 Microsoft 제품 및 서비스는 미국 및/또는 기타 국가에서 Microsoft의 상표 또는 등록 상표일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb97e-107">Microsoft, Windows, Microsoft Azure and/or other Microsoft products and services referenced in the documentation may be either trademarks or registered trademarks of Microsoft in the United States and/or other countries.</span></span>
<span data-ttu-id="bb97e-108">이 프로젝트에 대한 라이선스는 귀하에게 Microsoft 이름, 로고 또는 상표를 사용할 권한을 부여하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bb97e-108">The licenses for this project do not grant you rights to use any Microsoft names, logos, or trademarks.</span></span>
<span data-ttu-id="bb97e-109">Microsoft의 일반 상표 지침은에서 찾을 수 있습니다 http://go.microsoft.com/fwlink/?LinkID=254653합니다.</span><span class="sxs-lookup"><span data-stu-id="bb97e-109">Microsoft's general trademark guidelines can be found at http://go.microsoft.com/fwlink/?LinkID=254653.</span></span>

<span data-ttu-id="bb97e-110">개인 정보 취급 방침에서 찾을 수 있습니다. https://privacy.microsoft.com/en-us/</span><span class="sxs-lookup"><span data-stu-id="bb97e-110">Privacy information can be found at https://privacy.microsoft.com/en-us/</span></span>

<span data-ttu-id="bb97e-111">Microsoft와 모든 기여자는 관련 저작권, 특허 또는 상표에 따라 묵시적, 금반언적 또는 다른 방식으로 다른 모든 권리를 보유합니다.</span><span class="sxs-lookup"><span data-stu-id="bb97e-111">Microsoft and any contributors reserve all others rights, whether under their respective copyrights, patents, or trademarks, whether by implication, estoppel or otherwise.</span></span>

## <a name="contributing"></a><span data-ttu-id="bb97e-112">영향을 주는</span><span class="sxs-lookup"><span data-stu-id="bb97e-112">Contributing</span></span>

<span data-ttu-id="bb97e-113">이 Windows 10 IoT를 위한 리포지토리입니다 **설명서** 에서 호스트 [ https://docs.microsoft.com/windows/iot-core ](https://docs.microsoft.com/windows/iot-core)합니다.</span><span class="sxs-lookup"><span data-stu-id="bb97e-113">This is the repository for Windows 10 IoT **documentation** hosted at [https://docs.microsoft.com/windows/iot-core](https://docs.microsoft.com/windows/iot-core).</span></span>

<span data-ttu-id="bb97e-114">새 범위를 참조 하세요. 또는 의견이, 보세요 싶다면 [ **영향을 주는**](/CONTRIBUTING.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="bb97e-114">If you would like to see new coverage or have feedback, please consider [**contributing**](/CONTRIBUTING.md).</span></span>  <span data-ttu-id="bb97e-115">기존 콘텐츠 편집, 새 콘텐츠를 추가 하거나 단순히 새를 만들 수 있습니다 [문제](https://github.com/MicrosoftDocs/windows-iotcore-docs/issues)합니다.</span><span class="sxs-lookup"><span data-stu-id="bb97e-115">You can edit the existing content, add new content, or simply create new [issues](https://github.com/MicrosoftDocs/windows-iotcore-docs/issues).</span></span> <span data-ttu-id="bb97e-116">의견을 확인 하 고 문서를 통합 하 여 하기 위해 함께 작업 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb97e-116">We’ll take a look at your suggestions and will work together to incorporate them into the docs.</span></span>

<span data-ttu-id="bb97e-117">콘텐츠를 편집 하려면 변경 하려는 문서 편집 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb97e-117">To edit content, just click edit on the article you want to make changes to:</span></span>

![문서를 편집 하는 방법에 대 한 Gif](windows-iotcore/media/edit-doc.gif)


<span data-ttu-id="bb97e-119">복제 또는 변경 하려면 리포지토리를 다운로드 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb97e-119">You can also clone or download the repo to make changes:</span></span>

![다운로드 리포지토리를 복제 하는 방법에 대 한 Gif](windows-iotcore/media/download-repo.gif)

<span data-ttu-id="bb97e-121">승인를 끌어오기 요청에 검토자 또는 검토를 추가 하려면 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb97e-121">You will also need to add a reviewer or reviews to your pull requests to get them approved:</span></span>

![끌어오기 요청에 검토자 추가](windows-iotcore/media/reviewers.gif)

# <a name="conventions"></a><span data-ttu-id="bb97e-123">규칙</span><span class="sxs-lookup"><span data-stu-id="bb97e-123">Conventions</span></span>
  - <span data-ttu-id="bb97e-124">항목을 추가 해야 페이지에 추가할 때는 [toc.md](windows-iotcore/TOC.md) 나타나도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb97e-124">When adding a page, you must add an entry for it in [toc.md](windows-iotcore/TOC.md) for it to appear.</span></span>
  - <span data-ttu-id="bb97e-125">폴더 추가 폴더를 포함할 수 있습니다 또는 `readme.md`s</span><span class="sxs-lookup"><span data-stu-id="bb97e-125">A folder can contain more folders or `readme.md`s</span></span>
  - <span data-ttu-id="bb97e-126">폴더/디렉터리 이름을 대시로 구분 됩니다 (예를 들어 `f12-tools`) 대 / 소문자입니다.</span><span class="sxs-lookup"><span data-stu-id="bb97e-126">Folder/directory names are dash-separated (e.g., `f12-tools`) and lowercase.</span></span> <span data-ttu-id="bb97e-127">Docs.microsoft.com 사이트의 Url에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bb97e-127">They are used in URLs on the docs.microsoft.com site.</span></span> <span data-ttu-id="bb97e-128">밑줄 또는 PascalCase/camelCase를 사용 하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="bb97e-128">Don't use underscores or PascalCase/camelCase.</span></span>


## <a name="other-text-elements"></a><span data-ttu-id="bb97e-129">다른 텍스트 요소</span><span class="sxs-lookup"><span data-stu-id="bb97e-129">Other text elements</span></span>

<span data-ttu-id="bb97e-130">이러한 텍스트 요소 스타일 지정에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb97e-130">These other text elements have styling available:</span></span>

* <span data-ttu-id="bb97e-131">순서가 지정 되지 않은 목록</span><span class="sxs-lookup"><span data-stu-id="bb97e-131">Unordered lists</span></span>
* <span data-ttu-id="bb97e-132">가 일반 글머리 기호</span><span class="sxs-lookup"><span data-stu-id="bb97e-132">Have regular bullets</span></span>
   * <span data-ttu-id="bb97e-133">글머리 기호를 중첩할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb97e-133">You can also nest bullets</span></span>
   * <span data-ttu-id="bb97e-134">글머리 기호 목록에 항목이 둘 이상 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb97e-134">Bullets lists should have more than one entry.</span></span>
* <span data-ttu-id="bb97e-135">멋진 표준</span><span class="sxs-lookup"><span data-stu-id="bb97e-135">Pretty standard</span></span>

1. <span data-ttu-id="bb97e-136">정렬 된 목록</span><span class="sxs-lookup"><span data-stu-id="bb97e-136">Ordered lists</span></span>
2. <span data-ttu-id="bb97e-137">일반 자리잡은 western 스타일 번호 매기기를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb97e-137">Use regular ol' western-style numbering.</span></span>
3. <span data-ttu-id="bb97e-138">목록에는 실제로 순서는 경우에 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb97e-138">Should be used only when a list truly has order.</span></span>

_________________________

<span data-ttu-id="bb97e-139">수평선 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb97e-139">Horizontal rules are available.</span></span> <span data-ttu-id="bb97e-140">간단 하 게 제한적으로 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="bb97e-140">We suggest using them sparingly to reduce clutter.</span></span>
<span data-ttu-id="bb97e-141">제목 태그를 사용 하 여 수평선을 결합 하지 마십시오 일부는 이미 시각적 계층에 대 한 선 스타일을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb97e-141">Do not combine horizontal rules with heading tags; some already used line styles for visual hierarchy.</span></span>
<span data-ttu-id="bb97e-142">또한 중간 번호 매기기 목록 (아래 참조) 정보를 결합 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="bb97e-142">Also, do not combine notes (see below) in the middle of numbered lists.</span></span> <span data-ttu-id="bb97e-143">이 번호 매기기 순서를 사용 하 여 디자인이 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="bb97e-143">This messes with the numbering order.</span></span>

## <a name="displaying-code"></a><span data-ttu-id="bb97e-144">코드 표시</span><span class="sxs-lookup"><span data-stu-id="bb97e-144">Displaying code</span></span>

<span data-ttu-id="bb97e-145">인라인을 사용할 수 있습니다 `code` Markdown 구문 (backtick) 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb97e-145">You can use inline `code` Markdown syntax (with the backticks).</span></span>

<span data-ttu-id="bb97e-146">코드 블록을 표시할 수 있습니다 또는 다음과 같이 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb97e-146">Or you can display blocks of code like so:</span></span>

```css
body {
    background: #fff;
}
```

## <a name="tables"></a><span data-ttu-id="bb97e-147">테이블</span><span class="sxs-lookup"><span data-stu-id="bb97e-147">Tables</span></span>

| <span data-ttu-id="bb97e-148">이 경우</span><span class="sxs-lookup"><span data-stu-id="bb97e-148">You can</span></span>     | <span data-ttu-id="bb97e-149">헤더 사용</span><span class="sxs-lookup"><span data-stu-id="bb97e-149">use headers</span></span> | <span data-ttu-id="bb97e-150">테이블에</span><span class="sxs-lookup"><span data-stu-id="bb97e-150">on tables</span></span>    |
|-------------|-------------|-------------:|
| <span data-ttu-id="bb97e-151">왼쪽 맞춤</span><span class="sxs-lookup"><span data-stu-id="bb97e-151">Left-aligned</span></span>| <span data-ttu-id="bb97e-152">경우가 아니면 #</span><span class="sxs-lookup"><span data-stu-id="bb97e-152">Unless a #</span></span>  | <span data-ttu-id="bb97e-153">456</span><span class="sxs-lookup"><span data-stu-id="bb97e-153">456</span></span>          |
| <span data-ttu-id="bb97e-154">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="bb97e-154">Text value</span></span>  | <span data-ttu-id="bb97e-155">자세한 텍스트</span><span class="sxs-lookup"><span data-stu-id="bb97e-155">More text</span></span>   | <span data-ttu-id="bb97e-156">$0.00</span><span class="sxs-lookup"><span data-stu-id="bb97e-156">$0.00</span></span>        |

## <a name="notes"></a><span data-ttu-id="bb97e-157">참고</span><span class="sxs-lookup"><span data-stu-id="bb97e-157">Notes</span></span>

<span data-ttu-id="bb97e-158">메모를 제한적으로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb97e-158">Use notes sparingly.</span></span> <span data-ttu-id="bb97e-159">블록 "하지 누락-it" 정보를 강조 표시 하도록 설계 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bb97e-159">They are blocks designed to highlight "don't-miss-it" information.</span></span>

<span data-ttu-id="bb97e-160">네 개의 서로 다른 버전의 현재 스타일 정보 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb97e-160">We have four different versions of notes currently styled:</span></span>
- <span data-ttu-id="bb97e-161">참고</span><span class="sxs-lookup"><span data-stu-id="bb97e-161">NOTE</span></span>
- <span data-ttu-id="bb97e-162">경고</span><span class="sxs-lookup"><span data-stu-id="bb97e-162">WARNING</span></span>
- <span data-ttu-id="bb97e-163">팁</span><span class="sxs-lookup"><span data-stu-id="bb97e-163">TIP</span></span>
- <span data-ttu-id="bb97e-164">중요</span><span class="sxs-lookup"><span data-stu-id="bb97e-164">IMPORTANT</span></span>


<span data-ttu-id="bb97e-165">여러 줄 블록 따옴표 정보에 대 한 사용을 > 아래 예에서 볼 수 있듯이 노트의 각 줄 앞에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb97e-165">For multi-line blockquote notes, use a > in front of each line of the notes as seen in the example below.</span></span>

## <a name="images"></a><span data-ttu-id="bb97e-166">이미지</span><span class="sxs-lookup"><span data-stu-id="bb97e-166">Images</span></span>

<span data-ttu-id="bb97e-167">이미지에 저장 되어야 합니다는 `media` 폴더 및 상대 경로 사용 하 여 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb97e-167">Images should be stored in a `media` folder and referenced with a relative path:</span></span>

`![Note patterns](media/notes.png)`


## <a name="code-of-conduct"></a><span data-ttu-id="bb97e-168">사용 규정</span><span class="sxs-lookup"><span data-stu-id="bb97e-168">Code of Conduct</span></span>
<span data-ttu-id="bb97e-169">이 프로젝트에 도입 된 [Microsoft 오픈 소스 준수 사항](https://opensource.microsoft.com/codeofconduct/)합니다.</span><span class="sxs-lookup"><span data-stu-id="bb97e-169">This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).</span></span> <span data-ttu-id="bb97e-170">자세한 내용은 참조는 [준수 사항 FAQ](https://opensource.microsoft.com/codeofconduct/faq/) 에 문의 하거나 [ opencode@microsoft.com ](mailto:opencode@microsoft.com) 추가 질문이 나 의견을 사용 하 여 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb97e-170">For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.</span></span>
