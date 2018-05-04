---

copyright:
  years: 2015, 2017
lastupdated: "2017-11-03"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}
{:download: .download}

# 시작하기 튜토리얼
이 짧은 튜토리얼에서는 감성과 관련된 몇몇 샘플 텍스트를 분석하여 {{site.data.keyword.nlushort}}에 대해 소개합니다.
{:shortdesc}

## 시작하기 전에
{: #before-you-begin}

- 서비스 인스턴스를 작성하십시오.
    - {: download} 이 내용이 표시되면 서비스 인스턴스를 작성한 것입니다. 이제 신임 정보를 가져오십시오.
    - 다음과 같이 서비스에서 프로젝트를 작성하십시오.
        1.  {{site.data.keyword.watson}} 개발자 콘솔 [ 서비스 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://console.{DomainName}/developer/watson/services){: new_window} 페이지로 이동합니다.
        1.  {{site.data.keyword.nlushort}}을 선택하고 **서비스 추가**를 클릭한 다음 무료 {{site.data.keyword.Bluemix_notm}} 계정에 가입하거나 로그인합니다.
        1.  프로젝트 이름으로 `sentiment-tutorial`을 입력하고 **프로젝트 작성**을 클릭합니다.
- 다음과 같이 서비스 인스턴스를 인증할 신임 정보를 복사하십시오.
    - {: download} 서비스 대시보드(현재 표시되는 사항)에서 다음을 수행하십시오.
        1.  **서비스 신임 정보** 탭을 클릭합니다.
        1.  **조치**에서 **신임 정보 보기**를 클릭합니다.
        1.  `username`, `password` 및 `url` 값을 복사합니다.
        {: download}
    - 개발자 콘솔에 있는 **sentiment-tutorial** 프로젝트의 **신임 정보** 섹션에서 `"natural_language_understanding"`의 `username`, `password` 및 `url` 값을 복사하십시오.
- 다음과 같이 cURL이 있는지 확인하십시오.
    - 이 예제에서는 cURL을 사용하여 HTTP 인터페이스의 메소드를 호출합니다. [curl.haxx.se ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://curl.haxx.se/){: new_window}에서 운영 체제의 버전을 설치합니다. SSL(Secure Sockets Layer) 프로토콜을 지원하는 버전을 설치합니다. `PATH` 환경 변수에 설치된 2진 파일을 포함하는지 확인합니다.

<!-- Remove this text after dedicated instances have the Developer Console: begin -->

{{site.data.keyword.Bluemix_dedicated_notm}}를 사용하는 경우 카탈로그의 [{{site.data.keyword.nlushort}} ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://console.{DomainName}/catalog/services/natural-language-understanding/){: new_window} 페이지에서 서비스 인스턴스를 작성하십시오. 서비스 신임 정보를 찾는 방법에 대한 자세한 내용은 Watson 서비스용 [ 서비스 신임 정보 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](/docs/services/watson/getting-started-credentials.html#getting-credentials-manually){: new_window}를 참조하십시오.

<!-- Remove this text after dedicated instances have the Developer Console: end -->

## 1단계: 감성과 관련된 샘플 컨텐츠 분석
{: #analyze-sample}

우선 몇몇 샘플 텍스트의 감성을 분석하십시오. 명령행 인터페이스를 열고 다음 명령을 실행하여 키워드 및 감성과 관련된 샘플 텍스트를 분석하는 `GET /v1/analyze` 메소드를 호출하십시오. `{username}` 및 `{password}`를 이전 단계에서 복사한 서비스 신임 정보로 대체하십시오.

```bash
curl --user "{username}":"{password}" \
"https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze?version=2017-02-27&text=I%20still%20have%20a%20dream%2C%20a%20dream%20deeply%20rooted%20in%20the%20American%20dream%20%E2%80%93%20one%20day%20this%20nation%20will%20rise%20up%20and%20live%20up%20to%20its%20creed%2C%20%22We%20hold%20these%20truths%20to%20be%20self%20evident%3A%20that%20all%20men%20are%20created%20equal.&features=sentiment,keywords"
```
{:pre}

## 2단계: 키워드 정보 리턴
{: #analyze-keywords}

이전 호출에서는 전체 텍스트에 대한 감성 정보를 리턴했습니다. 이제 각 키워드에 대해 명확하게 감성 분석을 리턴할 수 있도록 결과를 확장하십시오. **keywords.sentiment** 매개변수를 포함하고 이를 `true`로 설정하십시오. `{username}` 및 `{password}`를 사용자의 정보로 대체하십시오.

```bash
curl --user "{username}":"{password}" \
"https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze?version=2017-02-27&text=I%20still%20have%20a%20dream%2C%20a%20dream%20deeply%20rooted%20in%20the%20American%20dream%20%E2%80%93%20one%20day%20this%20nation%20will%20rise%20up%20and%20live%20up%20to%20its%20creed%2C%20%22We%20hold%20these%20truths%20to%20be%20self%20evident%3A%20that%20all%20men%20are%20created%20equal.&features=sentiment,keywords&keywords.sentiment=true"
```
{:pre}

## 3단계: 구문 대상 지정
{: #analyze-phrase}

이제 **sentiment.targets** 매개변수에 구문 `the%20American%20dream%20`을 포함하여 (문서나 키워드 분석 대신) 문장 레벨이나 구문 레벨 분석을 볼 수 있도록 특정 컨텐츠를 대상으로 지정하십시오. `{username}` 및 `{password}`를 반드시 사용자의 정보로 대체하십시오.

```bash
curl --user "{username}":"{password}" \
"https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze?version=2017-02-27&text=I%20still%20have%20a%20dream%2C%20a%20dream%20deeply%20rooted%20in%20the%20American%20dream%20one%20day%20this%20nation%20will%20rise%20up%20and%20live%20up%20to%20its%20creed%20We%20hold%20these%20truths%20to%20be%20self%20evident%3A%20that%20all%20men%20are%20created%20equal.&features=sentiment,keywords&keywords.sentiment=true&sentiment.targets=the%20American%20dream"
```
{:pre}

## 다음 단계
{: #next-steps}

완료되었습니다! 이 튜토리얼에서는 {{site.data.keyword.nlushort}}에서 수행할 수 있는 작업을 아주 간략하게만 다루었습니다. API의 기능에 대한 자세한 정보는 다음 리소스를 참조하십시오.

- 각 매개변수의 세부사항과 예제에 대해서는 [API 참조 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/){: new_window}를 보십시오.
- [사용자 정의 엔티티와 관계](/docs/services/natural-language-understanding/customizing.html)를 식별하는 방법을 알아보십시오.
