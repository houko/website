---
title: 풀 리퀘스트 리뷰
content_type: concept
main_menu: true
weight: 10
---

<!-- overview -->

누구나 문서화에 대한 풀 리퀘스트를 리뷰할 수 있다. 쿠버네티스 website 리포지터리의 [풀 리퀘스트](https://github.com/kubernetes/website/pulls) 섹션을 방문하여 열린(open) 풀 리퀘스트를 확인한다.

문서화에 대한 풀 리퀘스트를 리뷰하는 것은
쿠버네티스 커뮤니티에 자신을 소개하는 훌륭한 방법이다.
아울러, 코드 베이스(code base)를 배우고 다른 기여자와 신뢰를 구축하는 데 도움이 된다.

리뷰하기 전에, 다음을 수행하는 것이 좋다.

- 적합한 코멘트를 남길 수 있도록 [콘텐츠 가이드](/docs/contribute/style/content-guide/)와
  [스타일 가이드](/docs/contribute/style/style-guide/)를 읽는다.
- 쿠버네티스 문서화 커뮤니티의 다양한
  [역할과 책임](/ko/docs/contribute/participate/#역할과-책임)을 
  이해한다.

<!-- body -->

## 시작하기 전에

리뷰를 시작하기 전에 다음을 명심하자.

- [CNCF 행동 강령](https://github.com/cncf/foundation/blob/master/code-of-conduct-languages/ko.md)을 읽고 항상 준수한다.
- 정중하고, 사려 깊고, 도움이 되자.
- PR의 긍정적인 측면과 변화에 대한 의견을 남긴다.
- 당신의 리뷰를 어떻게 받아들일지에 대해 공감하고 주의한다.
- 좋은 의도를 가지고 명확한 질문을 한다.
- 숙련된 기여자인 경우, 작업에 광범위한 변경이 필요한 새 기여자와 쌍을 이루어 리뷰해 본다.

## 리뷰 과정

일반적으로, 영어로 콘텐츠와 스타일에 대한 풀 리퀘스트를 리뷰한다. 그림 1은 리뷰 과정의 단계를 보여 준다. 각 단계에 대한 상세 사항은 아래에 나와 있다.

<!-- See https://github.com/kubernetes/website/issues/28808 for live-editor URL to this figure -->
<!-- You can also cut/paste the mermaid code into the live editor at https://mermaid-js.github.io/mermaid-live-editor to play around with it -->

{{< mermaid >}}
flowchart LR
    subgraph fourth[리뷰 시작]
    direction TB
    S[ ] -.-
    M[코멘트 작성] --> N[변경사항 리뷰]
    N --> O[새 기여자가 어떤 코멘트를<br>반영할지 선택해야 함]
    end
    subgraph third[PR 선택]
    direction TB
    T[ ] -.-
    J[본문과 코멘트 확인]--> K[Netlify 미리보기 빌드로<br>변경사항 미리보기]
    end
 
  A[열려 있는 PR 목록 확인]--> B[레이블을 이용하여<br>PR을 필터링]
  B --> third --> fourth
     

classDef grey fill:#dddddd,stroke:#ffffff,stroke-width:px,color:#000000, font-size:15px;
classDef white fill:#ffffff,stroke:#000,stroke-width:px,color:#000,font-weight:bold
classDef spacewhite fill:#ffffff,stroke:#fff,stroke-width:0px,color:#000
class A,B,J,K,M,N,O grey
class S,T spacewhite
class third,fourth white
{{</ mermaid >}}

그림 1. 리뷰 과정 절차.

1.  [https://github.com/kubernetes/website/pulls](https://github.com/kubernetes/website/pulls)로
    이동한다.
    쿠버네티스 website와 문서에 대한 모든 열린 풀 리퀘스트 목록이
    표시된다.

2.  다음 레이블 중 하나 또는 모두를 사용하여 열린 PR을 필터링한다.
    - `cncf-cla: yes`(권장): CLA에 서명하지 않은 기여자가 제출한 PR은 병합할 수 없다. 자세한 내용은 [CLA 서명](/ko/docs/contribute/new-content/#sign-the-cla)을 참고한다.
    - `language/en`(권장): 영어 문서에 대한 PR 전용 필터이다.
    - `size/<size>`: 특정 크기의 PR을 필터링한다. 새로 시작하는 사람이라면, 더 작은 PR로 시작한다.

    또한, PR이 진행 중인 작업으로 표시되지 않았는지 확인한다. `work in progress` 레이블을 사용하는 PR은 아직 리뷰할 준비가 되지 않은 PR이다.

3.  리뷰할 PR을 선택한 후, 다음을 통해 변경 사항을 이해한다.
    - PR 설명을 통해 변경 사항을 이해하고, 연결된 이슈 읽기
    - 다른 리뷰어의 의견 읽기
    - **Files changed** 탭을 클릭하여 변경된 파일과 행 보기
    - **Conversation** 탭의 맨 아래에 있는 PR의 빌드 확인 섹션으로 스크롤하여 Netlify 미리보기 빌드의 변경 사항을 확인. 
      다음은 스크린샷이다(GitHub 데스크탑 사이트이며, 
      태블릿 또는 스마트폰 장치에서 리뷰하는 경우 GitHub 웹 UI가 약간 다르다).
      {{< figure src="/images/docs/github_netlify_deploy_preview.png" alt="Netlify 미리보기 링크를 포함하는 GitHub PR 상세 사항" >}}
      미리보기를 열려면, 체크 목록의 **deploy/netlify** 행의 **Details** 링크를 클릭한다.

4.  **Files changed** 탭으로 이동하여 리뷰를 시작한다.
    1. 코멘트을 달려는 줄 옆에 있는 `+` 기호를 클릭한다.
    2. 행에 대한 의견을 작성하고 **Add single comments**(작성할 의견이 하나만 있는 경우) 또는 **Start a review**(작성할 의견이 여러 개인 경우)를 클릭한다.
    3. 완료되면, 페이지 상단에서 **Review changes** 를 클릭한다. 여기에서
       리뷰에 대한 요약을 추가하고(기여자에게 긍정적인 의견을 남겨주기 바란다!),
       PR을 승인하거나, 의견을 보내거나 필요에 따라 변경을 요청할 수 있다. 새로운 기여자는
       항상 **Comment** 를 선택해야 한다.

## 리뷰 체크리스트

리뷰할 때, 다음을 시작점으로 사용한다.

### 언어와 문법

- 언어나 문법에 명백한 오류가 있는가? 무언가를 표현하는 더 좋은 방법이 있는가?
- 더 간단한 단어로 대체될 수 있는 복잡하거나 오래된 단어가 있는가?
- 비 차별적 대안으로 대체될 수 있는 단어, 용어 또는 문구가 있는가?
- 단어 선택과 대소문자는 [스타일 가이드](/docs/contribute/style/style-guide/)를 따르는가?
- 더 짧고 간결하게 만들 수 있는 긴 문장이 있는가?
- 목록이나 표로 더 잘 표현할 수 있는 긴 단락이 있는가?

### 콘텐츠

- 쿠버네티스 사이트의 다른 곳에도 비슷한 콘텐츠가 있는가?
- 콘텐츠가 오프-사이트, 개별 업체, 또는 공개되지 않은 소스 문서에 과도하게 링크되는가?

### 웹 사이트

- 이 PR이 페이지 제목, slug/alias 또는 앵커(anchor) 링크를 변경 또는 제거하는가? 그렇다면, 이 PR의 결과로 끊어진 링크가 있는가? slug를 변경 없이 페이지 제목을 변경하는 등의 다른 옵션이 있는가?
- PR이 새로운 페이지를 소개하는가? 그렇다면,
  - 페이지가 올바른 [페이지 콘텐츠 타입](/docs/contribute/style/page-content-types/)과 연관된 Hugo 단축 코드를 사용하는가?
  - 섹션의 측면 탐색에 페이지가 올바르게 나타나는가?
  - 페이지가 [문서 홈](/docs/home/) 목록에 나타나야 하는가?
- 변경 사항이 Netlify 미리보기에 표시되는가? 목록, 코드 블록, 표, 메모 및 이미지에 특히 주의한다.

### 기타

오타나 공백과 같은 작은 이슈의 PR인 경우, 코멘트 앞에 `nit:` 를 추가한다. 이를 통해 문서의 저자는 이슈가 긴급하지 않다는 것을 알 수 있다.
