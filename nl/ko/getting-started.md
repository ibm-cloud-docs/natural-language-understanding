---

copyright:
  years: 2015, 2018
lastupdated: "2018-12-19"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:important: .important}
{:note: .note}
{:deprecated: .deprecated}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:javascript: .ph data-hd-programlang='javascript'}
{:go: .ph data-hd-programlang='go'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}
{:download: .download}
{:apikey: data-credential-placeholder='apikey'}
{:url: data-credential-placeholder='url'}
{:hide-dashboard: .hide-dashboard}

# 시작하기 튜토리얼
{: #getting-started}

이 짧은 튜토리얼에서는 예제 요청이 있는 {{site.data.keyword.nlushort}} API와 추가 리소스에 대한 링크를 소개합니다.
{:shortdesc}

## 시작하기 전에
{: #before-you-begin}

- {: hide-dashboard}서비스 인스턴스를 작성하십시오.
    1.  {{site.data.keyword.Bluemix_notm}} 카탈로그의 [{{site.data.keyword.nlushort}} ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://{DomainName}/catalog/services/natural-language-understanding){: new_window} 페이지로 이동하십시오.
    2.  무료 {{site.data.keyword.Bluemix_notm}} 계정에 가입하거나 로그인하십시오.
    3.  **작성**을 클릭하십시오.
- 다음과 같이 서비스 인스턴스를 인증할 인증 정보를 복사하십시오.
    1.  **관리** 페이지에서 **표시**를 클릭하여 인증 정보를 보십시오.
    2.  `API 키`와 `URL` 값을 복사하십시오.
- `curl` 명령이 있는지 확인하십시오.
    - 이 예제에서는 `curl` 명령을 사용하여 HTTP 인터페이스의 메소드를 호출합니다. [curl.haxx.se ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://curl.haxx.se/){: new_window}에서 운영 체제의 버전을 설치합니다. SSL(Secure Sockets Layer) 프로토콜을 지원하는 버전을 설치합니다. `PATH` 환경 변수에 설치된 2진 파일을 포함하는지 확인합니다.

이 튜토리얼에서는 명령행 인터페이스에서 {{site.data.keyword.nlushort}} API를 사용하는 방법을 보여줍니다. 다양한 프로그래밍 언어의 클라이언트 라이브러리를 다운로드하려면 [Watson SDK](/docs/services/natural-language-understanding?topic=watson-using-sdks#using-sdks)를 확인하십시오.
{:tip}

## 1단계: 웹 페이지 분석
{: #analyze-sample}

웹 페이지를 분석하여 감성, 개념, 카테고리, 엔티티 및 키워드를 얻으려면 다음 명령을 실행하십시오. <span class="hide-dashboard">`{apikey}`와 `{url}`을 서비스 인증 정보로 바꾸십시오.</span>

```bash
curl -X POST -u "apikey:{apikey}"{: apikey} \
"{url}/v1/analyze?version=2018-11-16"{: url} \
--header "Content-Type: application/json" \
--data '{
  "url": "http://newsroom.ibm.com/Guerbet-and-IBM-Watson-Health-Announce-Strategic-Partnership-for-Artificial-Intelligence-in-Medical-Imaging-Liver",
  "features": {
    "sentiment": {},
    "categories": {},
    "concepts": {},
    "entities": {},
    "keywords": {}
  }
}'
```
{:pre}

다음 단계에서는 각 기능의 분석을 사용자 정의하는 데 사용하는 옵션을 지정하는 방법을 보여줍니다.

## 2단계: 대상 문구 및 키워드 분석
{: #analyze-phrase}

{{site.data.keyword.nlushort}}에서는 중점을 둔 감성과 감정 결과를 얻기 위해 주변 텍스트의 컨텍스트에서 대상 문구를 분석할 수 있습니다. 다음 예에서 감성의 **targets** 옵션을 통해 서비스에 "apples", "oranges" 및 "broccoli" 대상을 검색하도록 지시합니다. "apples"와 "oranges"가 텍스트에 있으므로 해당 대상의 감성 점수가 리턴됩니다.

텍스트에서 발견된 엔티티와 키워드의 감성 및 감정 결과도 얻을 수 있습니다. 이 예에서는 키워드의 **emotion** 옵션을 통해 감정 결과를 얻기 위해 발견된 각 키워드를 분석하도록 서비스에 지시합니다.

```bash
curl -X POST -u "apikey:{apikey}"{: apikey} \
"{url}/v1/analyze?version=2018-11-16"{: url} \
--request POST \
--header "Content-Type: application/json" \
--data '{
  "text": "I love apples! I do not like oranges.",
  "features": {
    "sentiment": {
      "targets": [
        "apples",
        "oranges",
        "broccoli"
      ]
    },
    "keywords": {
      "emotion": true
    }
  }
}'
```
{:pre}

## 다음 단계
{: #next-steps}

- [API 참조 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://{DomainName}/apidocs/natural-language-understanding){: new_window}를 보십시오.
- [사용자 정의 엔티티와 관계](/docs/services/natural-language-understanding?topic=natural-language-understanding-customizing)를 식별하는 방법을 알아보십시오.
