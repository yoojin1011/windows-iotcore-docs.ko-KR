# <a name="contributing-to-the-windows-10-iot-documentation"></a>Windows 10 IoT 설명서에 기여

당사의 설명서에 관심을 가져 주셔서 감사합니다. 문서 개선을 위해 사용자 의견, 편집, 추가 및 도움을 주셔서 감사 합니다. 이 페이지에는 영향을 주는 기본 단계와 지침이 설명 되어 있습니다.

## <a name="sign-a-cla"></a>CLA 서명

여러 줄을 기여하려 하는데 Microsoft 직원이 아닌 경우 [Microsoft CLA(Contribution Licensing Agreement)에 서명](https://cla.microsoft.com/)해야 합니다. 

## <a name="proposing-a-change"></a>변경 제안

문서 변경을 제안하려면 다음 단계를 수행합니다.

1. Docs.microsoft.com 페이지를 보고 있는 경우 페이지 오른쪽 위에서 **편집** 단추를 클릭합니다.  그러면 [GitHub 리포지토리](https://github.com/MicrosoftDocs/windows-iotcore-docs)의 해당 Markdown 소스 파일로 리디렉션됩니다.  이미 GitHub 리포지토리에 있는 경우 변경하려는 원본 파일로 이동하면 됩니다.
2. 아직 GitHub 계정이 없는 경우 오른쪽 위에서 **가입**을 클릭하고 새 계정을 만듭니다.
3. 변경하려는 GitHub 페이지에서 연필 아이콘을 클릭합니다. 
4. 파일을 수정하고 미리 보기 탭을 사용하여 변경 내용이 올바른지 확인합니다.
5. 모두 마쳤으면 변경 내용을 커밋하고 끌어오기 요청을 엽니다.

끌어오기 요청을 만들면 Windows 10 IoT 팀 구성원이 요청을 검토할 것입니다. 요청이 수락되면 [https://docs.microsoft.com/windows/iot-core](https://docs.microsoft.com/windows/iot-core)에 업데이트가 게시됩니다.

## <a name="making-more-substantial-changes"></a>큰 폭의 변경

기존 문서를 대폭 변경하거나 이미지를 추가 또는 변경하거나 새 문서에 기여하려면 리포지토리를 GitHub 계정으로 분기([GitHub 리포지토리](https://github.com/MicrosoftDocs/windows-iotcore-docs)의 오른쪽 위 모서리에서 "분기" 단추를 클릭)한 다음, 로컬 클론을 만듭니다(녹색 "복제 또는 다운로드" 단추를 클릭하여 클립보드에 복사한 다음, 명령줄에 `git clone <paste your repo clone link>` 입력).

다음 문서에 기여하기 전에 다음 질문에 대답해 보시기 바랍니다.
* 오직 하나의 # 수준 제목만 포함했나요(HTML의 H1과 동등)? 
* 새 문서의 제목에 포함된 동사 시제(해당하는 경우)가 현재형이고 다른 문서와 일치하나요?
* 모든 문법이 올바른가요?
* 새 문서를 기고하는 경우 문서를 적절한 범주에 추가하고 TOC.md를 업데이트했나요?
* URL 형식을 https://github.com/MicrosoftDocs/windows-iotcore-docs/blob/master/CONTRIBUTING.md 가 아닌 [여기처럼](https://github.com/MicrosoftDocs/windows-iotcore-docs/blob/master/CONTRIBUTING.md) 지정했나요?
* 새 문서를 검토할 사람이 두 명 이상 있나요?
* Terry Warwick, twarwick@microsoft.com에 문의

새 문서가 수락되면 다음 단계를 수행하는 것이 좋습니다.
* 문서를 팀과 공유합니다. 성과를 숨기지 말고 동료들에게 알립니다.
* 댓글 상자 아래의 "팔로우" 단추를 클릭하여 문서의 댓글을 팔로우합니다. 이렇게 하면 문서에 달리는 댓글을 확인할 수 있습니다.

자세한 내용은 [리포지토리 분기](https://help.github.com/articles/fork-a-repo/)를 참조하세요. 라이브 분기에 있는 PR은 병합하지 않을 것입니다. PR은 마스터 분기에 제출하세요.

Git 사용 방법에 익숙하지 않은 경우 [Lynda.com Git Essentials 교육](https://www.lynda.com/Git-tutorials/Git-Essential-Training/100222-2.html)을 받아 보세요.

## <a name="authoring-your-contribution"></a>글 작성

리포지토리를 분기하고 로컬 머신에 복제한 후에는 원하는 텍스트 편집기를 사용하여 글 작성을 시작할 수 있습니다.  물론 Microsoft에서 제공하는 가벼운 무료 오픈 소스 편집기인 [Visual Studio Code](https://code.visualstudio.com/)를 사용하는 것이 좋습니다. Markdown 작성에 대 한 도움말 [은이 Markdown 누구나 누구나 즐길 수 있습니다. ](windows-iotcore/media/DocsMarkdownPoster.pdf)알고 있어야 하는 모든 기본 사항을 포함 하는 포스터 이 포스터를 인쇄하여 벽에 걸어 놓고 기여에 대한 미리 알림으로 사용할 수도 있습니다. 

## <a name="submitting-your-contribution-and-filing-a-pull-request-pr"></a>기고문을 제출하고 끌어오기 요청(PR) 작성

게시가 가능하도록 스테이징하기 위해 변경 내용을 원격 리포지토리에 추가할 준비가 되면 명령줄에서 다음 명령을 입력합니다.
- `git status`:이 명령은 변경 된 파일을 보여 주기 위해 변경한 내용을 확인할 수 있습니다. 
- `git add -A`:이 명령은 git에 모든 변경 내용을 추가 하도록 지시 합니다. 특정 파일에서 변경한 내용만 추가하려면 이 명령 대신 `git add <file.md>` 명령을 입력합니다. 여기서 "file.md"는 변경 내용을 포함하고 있는 파일의 이름입니다.
- `git commit -m “Fixed a few typos”`:이 명령은 이전 단계에서 추가한 변경 내용을 커밋하는 git에 지시 하 고 변경한 내용을 설명 하는 짧은 메시지를 표시 합니다.
- `git push origin <yourbranchname>`:이 명령은 GitHub ("원본")에 분기 원격 리포지토리로 변경 내용을 지정 된 분기로 푸시합니다. 리포지토리를 사용자 고유의 GitHub 계정으로 포크했기 때문에 사용자가 **개발** 분기에서 작업을 수행할 수 있습니다. 

변경 내용에 만족하고 PR을 제출할 준비가 완료되면 다음을 수행합니다.
- IoT 리포지토리의 포크 https://github.com/your-github-alias/windows-iotcore-docs 로 이동합니다.
- "새 끌어오기 요청" 단추를 클릭합니다. ("기본 포크:"는 "MicrosoftDocs"로 표시 되 고, "head 포크:"는 사용자가 변경한 리포지토리 및 분기의 포크를 표시 합니다.) 여기 에서도 변경 내용을 검토할 수 있습니다. 
- 녹색 "끌어오기 요청 만들기" 단추를 클릭합니다. 끌어오기 요청의 제목과 설명을 입력한 다음, "끌어오기 요청 만들기" 단추를 한 번 더 클릭합니다.

원격 리포지토리에 기고문을 푸시하면 기고문이 성공적으로 작성되었는지 여부를 알려주고 끊어진 링크 같은 오류 경고에 연결하는 *Open Publishing Build Service*의 이메일이 도착합니다. 링크를 클릭하면 사이트에서 콘텐츠가 스테이징되는 것을 볼 수 있습니다.

[Windows 10 IoT Docs 스테이징 사이트](https://review.docs.microsoft.com/en-us/windows/iot-core/)의 기고문을 검토하여 변경 내용을 실시간으로 게시해도 좋다고 생각되면 PR(끌어오기 요청)을 제출해야 합니다.

PR을 제출하면 Windows 10 IoT 문서 팀의 구성원이 요청을 검토할 것입니다. 요청이 수락되면 [스테이징 사이트](https://review.docs.microsoft.com/en-us/windows/iot-core)에서 변경 내용을 볼 수 있습니다. 이러한 업데이트는 최종적으로 [https://docs.microsoft.com/windows/iot-core](https://docs.microsoft.com/windows/iot-core)에 실시간으로 게시됩니다.

## <a name="working-with-branches"></a>분기 작업

[Windows 10 IoT Docs GitHub 리포지토리](https://github.com/MicrosoftDocs/windows-iotcore-docs) 는 두 개의 기본 부모 분기를 활용 합니다. [개발](https://github.com/MicrosoftDocs/windows-iotcore-docs/tree/develop),이 콘텐츠를 [스테이징 사이트](https://review.docs.microsoft.com/en-us/windows/iot-core)에서 검토 하 [고 라이브](https://github.com/MicrosoftDocs/windows-iotcore-docs/tree/live) [사이트](https://docs.microsoft.com/windows/iot-core)에 표시 되는 콘텐츠를 사용할 수 있습니다. 

기고문을 작성할 때에는 **개발** 분기에 PR(끌어오기 요청)을 제출하세요. 이 분기는 스테이징 사이트에서 볼 수 있으며 실시간으로 게시할 준비가 완료된 기고문만 포함해야 합니다.

## <a name="using-issues-to-provide-feedback-on-iot-documentation"></a>이슈를 사용하여 IoT 설명서에 대한 피드백 제공

실제 설명서 페이지를 직접 수정하지 않고 피드백을 제공하려면 [이슈를 작성](https://github.com/MicrosoftDocs/windows-iotcore-docs/issues)합니다.

토픽 제목과 페이지 URL을 꼭 포함해야 합니다.

## <a name="additional-resources"></a>추가 리소스
- [GitHub에서 작성 및 포맷 시작](https://help.github.com/articles/getting-started-with-writing-and-formatting-on-github/)

## <a name="additional-resources-for-microsoft-employees"></a>Microsoft 직원을 위한 추가 리소스
- [GitHub 계정과 MS 별칭 연결](https://review.docs.microsoft.com/en-us/windows-authoring-guide/github-account#2-connect-your-github-account-and-ms-alias-on-the-microsoft-open-source-portal)
- [Markdown 작성에 대한 리소스](https://review.docs.microsoft.com/en-us/windows-authoring-guide/writing-guidance/writing-markdown)
