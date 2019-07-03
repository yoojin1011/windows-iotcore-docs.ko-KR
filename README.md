## <a name="microsoft-open-source-code-of-conduct"></a>Microsoft 오픈 소스 규정

이 프로젝트에서는 [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/)(Microsoft 오픈 소스 규정)를 채택했습니다.
자세한 내용은 [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/)(규정 FAQ)를 참조하세요. 또는 추가 질문이나 의견은 [opencode@microsoft.com](mailto:opencode@microsoft.com)으로 문의하세요.

# <a name="how-to-contribute-to-windows-10-iotcore-documentation"></a>Windows 10 IoTCore 설명서에 기여하는 방법

## <a name="legal-notices"></a>법적 고지 사항
Microsoft와 모든 기여자는 [Creative Commons Attribution 4.0 국제 공개 라이선스](https://creativecommons.org/licenses/by/4.0/legalcode)에 따라 귀하에게 이 리포지토리의 Microsoft 설명서 및 기타 콘텐츠에 대한 라이선스([LICENSE](LICENSE) 파일 참조)를 부여하고, [MIT 라이선스](https://opensource.org/licenses/MIT)에 따라 귀하에게 리포지토리의 모든 코드에 대한 라이선스([LICENSE-CODE](LICENSE-CODE) 파일 참조)를 부여합니다.

Microsoft, Windows, Microsoft Azure 및/또는 기타 이 설명서에 언급된 Microsoft 제품 및 서비스는 미국 및/또는 기타 국가에서 Microsoft의 상표 또는 등록 상표일 수 있습니다.
이 프로젝트에 대한 라이선스는 귀하에게 Microsoft 이름, 로고 또는 상표를 사용할 권한을 부여하지 않습니다.
Microsoft의 일반 상표 지침은 http://go.microsoft.com/fwlink/?LinkID=254653 에 있습니다.

개인 정보는 https://privacy.microsoft.com/en-us/ 에 있습니다.

Microsoft와 모든 기여자는 관련 저작권, 특허 또는 상표에 따라 묵시적, 금반언적 또는 다른 방식으로 다른 모든 권리를 보유합니다.

## <a name="contributing"></a>기여

이는 [https://docs.microsoft.com/windows/iot-core](https://docs.microsoft.com/windows/iot-core)에서 호스팅되는 Windows 10 IoT **설명서**의 리포지토리입니다.

새 적용 범위를 보거나 피드백을 받으려면 [**기여**](/CONTRIBUTING.md)하는 것도 고려해보세요.  기존 콘텐츠를 편집하거나, 새 콘텐츠를 추가하거나, 새 [이슈](https://github.com/MicrosoftDocs/windows-iotcore-docs/issues)를 만들면 됩니다. 제안을 살펴보고 함께 협력하여 문서에 통합할 것입니다.

콘텐츠를 편집하려면 변경하려는 문서에서 클릭만 하면 됩니다.

![문서 편집 방법에 대한 Gif](windows-iotcore/media/edit-doc.gif)


변경하기 위해 리포지토리를 복제하거나 다운로드할 수도 있습니다.

![리포지토리를 복제하거나 다운로드하는 방법에 대한 Gif](windows-iotcore/media/download-repo.gif)

또한 끌어오기 요청에 리뷰어 또는 리뷰를 추가하여 승인을 받아야 합니다.

![끌어오기 요청에 리뷰어 추가](windows-iotcore/media/reviewers.gif)

# <a name="conventions"></a>규칙
  - 페이지를 추가할 때 페이지를 표시하려면 [toc.md](windows-iotcore/TOC.md)에 항목을 추가해야 합니다.
  - 폴더에는 추가 폴더 또는 `readme.md`가 포함될 수 있습니다.
  - 폴더/디렉터리 이름은 대시 구분(예: `f12-tools`) 및 소문자로 구분됩니다. 이는 docs.microsoft.com 사이트의 URL에서 사용됩니다. 밑줄 또는 PascalCase/camelCase를 사용하지 마세요.


## <a name="other-text-elements"></a>기타 텍스트 요소

이러한 기타 텍스트에는 다음과 같은 스타일 지정을 사용할 수 있습니다.

* 순서가 지정되지 않은 목록
* 일반 글머리 기호가 있음
   * 글머리 기호를 중첩할 수도 있습니다.
   * 글머리 기호 목록에는 둘 이상의 항목이 있어야 합니다.
* 좋은 표준

1. 순서가 지정된 목록
2. 일반 ol western 스타일 번호 매기기를 사용합니다.
3. 목록에 실제로 순서가 있는 경우에만 사용해야 합니다.

_________________________

수평 규칙을 사용할 수 있습니다. 혼란을 줄이기 위해 제한적으로 사용하는 것이 좋습니다.
수평 규칙을 제목 태그와 결합하지 마세요. 일부는 이미 시각적 계층 구조에 선 스타일을 사용했습니다.
또한 번호가 매겨진 목록의 중간에 메모(아래 참조)를 결합하지 마세요. 이는 번호 매기기 순서를 엉망으로 만듭니다.

## <a name="displaying-code"></a>코드 표시

인라인 `code` Markdown 구문(backtick 포함)을 사용할 수 있습니다.

또는 다음과 같은 코드 블록을 표시할 수 있습니다.

```css
body {
    background: #fff;
}
```

## <a name="tables"></a>테이블

| 이 경우     | 헤더 사용 | 테이블에    |
|-------------|-------------|-------------:|
| 왼쪽 맞춤| #이 아닌 경우  | 456          |
| 텍스트 값  | 자세한 텍스트   | $0.00        |

## <a name="notes"></a>참고

메모를 제한적으로 사용합니다. "누락하지 마세요" 정보를 강조 표시하도록 설계된 블록입니다.

현재 스타일이 지정된 네 개의 서로 다른 버전이 있습니다.
- 참고
- 경고
- 팁
- 중요


여러 줄 블록 따옴표 메모의 경우 아래 예제와 같이 메모의 각 행 줄 앞에 >를 사용합니다.

## <a name="images"></a>이미지

이미지는 `media` 폴더에 저장되고 상대 경로로 참조되어야 합니다.

`![Note patterns](media/notes.png)`


## <a name="code-of-conduct"></a>준수 사항
이 프로젝트에서는 [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/)(Microsoft 오픈 소스 규정)를 채택했습니다. 자세한 내용은 [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/)(규정 FAQ)를 참조하세요. 또는 추가 질문이나 의견은 [opencode@microsoft.com](mailto:opencode@microsoft.com)으로 문의하세요.
