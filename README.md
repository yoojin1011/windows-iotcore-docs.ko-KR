## <a name="microsoft-open-source-code-of-conduct"></a>Microsoft 오픈 소스 준수 사항

이 프로젝트에 도입 된 [Microsoft 오픈 소스 준수 사항](https://opensource.microsoft.com/codeofconduct/)합니다.
자세한 내용은 참조는 [준수 사항 FAQ](https://opensource.microsoft.com/codeofconduct/faq/) 에 문의 하거나 [ opencode@microsoft.com ](mailto:opencode@microsoft.com) 추가 질문이 나 의견을 사용 하 여 합니다.

# <a name="how-to-contribute-to-windows-10-iotcore-documentation"></a>Windows 10 IoTCore 설명서에 기여 하는 방법

## <a name="legal-notices"></a>법적 고지 사항
Microsoft와 모든 기여자는 [Creative Commons Attribution 4.0 국제 공개 라이선스](https://creativecommons.org/licenses/by/4.0/legalcode)에 따라 귀하에게 이 리포지토리의 Microsoft 설명서 및 기타 콘텐츠에 대한 라이선스([LICENSE](LICENSE) 파일 참조)를 부여하고, [MIT 라이선스](https://opensource.org/licenses/MIT)에 따라 귀하에게 리포지토리의 모든 코드에 대한 라이선스([LICENSE-CODE](LICENSE-CODE) 파일 참조)를 부여합니다.

Microsoft, Windows, Microsoft Azure 및/또는 기타 이 설명서에 언급된 Microsoft 제품 및 서비스는 미국 및/또는 기타 국가에서 Microsoft의 상표 또는 등록 상표일 수 있습니다.
이 프로젝트에 대한 라이선스는 귀하에게 Microsoft 이름, 로고 또는 상표를 사용할 권한을 부여하지 않습니다.
Microsoft의 일반 상표 지침은에서 찾을 수 있습니다 http://go.microsoft.com/fwlink/?LinkID=254653합니다.

개인 정보 취급 방침에서 찾을 수 있습니다. https://privacy.microsoft.com/en-us/

Microsoft와 모든 기여자는 관련 저작권, 특허 또는 상표에 따라 묵시적, 금반언적 또는 다른 방식으로 다른 모든 권리를 보유합니다.

## <a name="contributing"></a>영향을 주는

이 Windows 10 IoT를 위한 리포지토리입니다 **설명서** 에서 호스트 [ https://docs.microsoft.com/windows/iot-core ](https://docs.microsoft.com/windows/iot-core)합니다.

새 범위를 참조 하세요. 또는 의견이, 보세요 싶다면 [ **영향을 주는**](/CONTRIBUTING.md)합니다.  기존 콘텐츠 편집, 새 콘텐츠를 추가 하거나 단순히 새를 만들 수 있습니다 [문제](https://github.com/MicrosoftDocs/windows-iotcore-docs/issues)합니다. 의견을 확인 하 고 문서를 통합 하 여 하기 위해 함께 작업 합니다.

콘텐츠를 편집 하려면 변경 하려는 문서 편집 클릭 합니다.

![문서를 편집 하는 방법에 대 한 Gif](windows-iotcore/media/edit-doc.gif)


복제 또는 변경 하려면 리포지토리를 다운로드 수도 있습니다.

![다운로드 리포지토리를 복제 하는 방법에 대 한 Gif](windows-iotcore/media/download-repo.gif)

승인를 끌어오기 요청에 검토자 또는 검토를 추가 하려면 해야 합니다.

![끌어오기 요청에 검토자 추가](windows-iotcore/media/reviewers.gif)

# <a name="conventions"></a>규칙
  - 항목을 추가 해야 페이지에 추가할 때는 [toc.md](windows-iotcore/TOC.md) 나타나도록 합니다.
  - 폴더 추가 폴더를 포함할 수 있습니다 또는 `readme.md`s
  - 폴더/디렉터리 이름을 대시로 구분 됩니다 (예를 들어 `f12-tools`) 대 / 소문자입니다. Docs.microsoft.com 사이트의 Url에 사용 됩니다. 밑줄 또는 PascalCase/camelCase를 사용 하지 마세요.


## <a name="other-text-elements"></a>다른 텍스트 요소

이러한 텍스트 요소 스타일 지정에 사용할 수 있습니다.

* 순서가 지정 되지 않은 목록
* 가 일반 글머리 기호
   * 글머리 기호를 중첩할 수도 있습니다.
   * 글머리 기호 목록에 항목이 둘 이상 있어야 합니다.
* 멋진 표준

1. 정렬 된 목록
2. 일반 자리잡은 western 스타일 번호 매기기를 사용 합니다.
3. 목록에는 실제로 순서는 경우에 사용 해야 합니다.

_________________________

수평선 사용할 수 있습니다. 간단 하 게 제한적으로 사용 하는 것이 좋습니다.
제목 태그를 사용 하 여 수평선을 결합 하지 마십시오 일부는 이미 시각적 계층에 대 한 선 스타일을 사용 합니다.
또한 중간 번호 매기기 목록 (아래 참조) 정보를 결합 하지 마십시오. 이 번호 매기기 순서를 사용 하 여 디자인이 바뀝니다.

## <a name="displaying-code"></a>코드 표시

인라인을 사용할 수 있습니다 `code` Markdown 구문 (backtick) 포함 합니다.

코드 블록을 표시할 수 있습니다 또는 다음과 같이 합니다.

```css
body {
    background: #fff;
}
```

## <a name="tables"></a>테이블

| 이 경우     | 헤더 사용 | 테이블에    |
|-------------|-------------|-------------:|
| 왼쪽 맞춤| 경우가 아니면 #  | 456          |
| 텍스트 값  | 자세한 텍스트   | $0.00        |

## <a name="notes"></a>참고

메모를 제한적으로 사용 합니다. 블록 "하지 누락-it" 정보를 강조 표시 하도록 설계 됩니다.

네 개의 서로 다른 버전의 현재 스타일 정보 있습니다.
- 참고
- 경고
- 팁
- 중요


여러 줄 블록 따옴표 정보에 대 한 사용을 > 아래 예에서 볼 수 있듯이 노트의 각 줄 앞에 있습니다.

## <a name="images"></a>이미지

이미지에 저장 되어야 합니다는 `media` 폴더 및 상대 경로 사용 하 여 참조 합니다.

`![Note patterns](media/notes.png)`


## <a name="code-of-conduct"></a>사용 규정
이 프로젝트에 도입 된 [Microsoft 오픈 소스 준수 사항](https://opensource.microsoft.com/codeofconduct/)합니다. 자세한 내용은 참조는 [준수 사항 FAQ](https://opensource.microsoft.com/codeofconduct/faq/) 에 문의 하거나 [ opencode@microsoft.com ](mailto:opencode@microsoft.com) 추가 질문이 나 의견을 사용 하 여 합니다.
