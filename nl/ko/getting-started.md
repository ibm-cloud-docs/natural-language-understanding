---

copyright:
  years: 2015, 2017
lastupdated: "2017-06-09"

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

# 시작하기 튜토리얼
이 짧은 튜토리얼에서는 감성과 관련된 몇몇 샘플 텍스트를 분석하여 {{site.data.keyword.nlushort}}에 대해 소개합니다.
{:shortdesc}

## 1단계: 로그인, 서비스 인스턴스 작성 및 신임 정보 가져오기
{: #create-service}

{{site.data.keyword.nlushort}} 서비스 인스턴스에 대한 신임 정보를 이미 알고 있는 경우에는 이 단계를 건너뛰십시오.
{: tip}

1.  [{{site.data.keyword.nlushort}} 서비스](https://console.{DomainName}/catalog/services/natural-language-understanding/)로 이동하여 무료 {{site.data.keyword.Bluemix_notm}} 계정에 등록하거나 로그인하십시오. 
1.  로그인 후에는 **서비스 이름** 필드에서 `sentiment-tutorial`을 입력하고 **작성**을 클릭하십시오. 
1.  신임 정보 복사:
    1.  **서비스 신임 정보**를 클릭하십시오. 
    1.  **조치** 아래에서 **신임 정보 보기**를 클릭하십시오. 
    1.  `username` 및 `password` 값을 복사하십시오. 

## 2단계: 감성과 관련된 샘플 컨텐츠 분석
{: #analyze-sample}

우선 몇몇 샘플 텍스트의 감성을 분석하십시오. 다음 명령을 실행하여 키워드 및 감성과 관련된 샘플 텍스트를 분석하는 `GET /v1/analyze` 메소드를 호출하십시오. `{username}` 및 `{password}`를 이전 단계에서 복사한 서비스 신임 정보로 대체하십시오. 

```bash
curl --user "{username}":"{password}" \
"https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze?version=2017-02-27&text=I%20still%20have%20a%20dream%2C%20a%20dream%20deeply%20rooted%20in%20the%20American%20dream%20%E2%80%93%20one%20day%20this%20nation%20will%20rise%20up%20and%20live%20up%20to%20its%20creed%2C%20%22We%20hold%20these%20truths%20to%20be%20self%20evident%3A%20that%20all%20men%20are%20created%20equal.&features=sentiment,keywords"
```
{:pre}

## 3단계: 키워드 정보 리턴
{: #analyze-keywords}

이전 호출에서는 전체 텍스트에 대한 감성 정보를 리턴했습니다. 이제 각 키워드에 대해 명확하게 감성 분석을 리턴할 수 있도록 결과를 확장하십시오. **keywords.sentiment** 매개변수를 포함하고 이를 `true`로 설정하십시오. `{username}` 및 `{password}`를 사용자의 정보로 대체하십시오. 

```bash
curl --user "{username}":"{password}" \
"https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze?version=2017-02-27&text=I%20still%20have%20a%20dream%2C%20a%20dream%20deeply%20rooted%20in%20the%20American%20dream%20%E2%80%93%20one%20day%20this%20nation%20will%20rise%20up%20and%20live%20up%20to%20its%20creed%2C%20%22We%20hold%20these%20truths%20to%20be%20self%20evident%3A%20that%20all%20men%20are%20created%20equal.&features=sentiment,keywords&keywords.sentiment=true"
```
{:pre}

## 4단계: 구문 대상 지정
{: #analyze-phrase}

이제 **sentiment.targets** 매개변수에 구문 `the%20American%20dream%20`을 포함하여 (문서나 키워드 분석 대신) 문장 레벨이나 구문 레벨 분석을 볼 수 있도록 특정 컨텐츠를 대상으로 지정하십시오. `{username}` 및 `{password}`를 반드시 사용자의 정보로 대체하십시오. 

```bash
curl --user "{username}":"{password}" \
"https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze?version=2017-02-27&text=I%20still%20have%20a%20dream%2C%20a%20dream%20deeply%20rooted%20in%20the%20American%20dream%20one%20day%20this%20nation%20will%20rise%20up%20and%20live%20up%20to%20its%20creed%20We%20hold%20these%20truths%20to%20be%20self%20evident%3A%20that%20all%20men%20are%20created%20equal.&features=sentiment,keywords&keywords.sentiment=true&sentiment.targets=the%20American%20dream"
```
{:pre}

## 다음 단계
{: #next-steps}

완료되었습니다! 이 튜토리얼에서는 {{site.data.keyword.nlushort}}에서 수행할 수 있는 작업을 겨우 피상적으로만 다루었습니다. API의 기능에 대한 자세한 정보는 다음 자원을 참조하십시오. 

- 각 매개변수의 세부사항과 예제에 대해서는 [API 참조 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/){: new_window}를 보십시오. 
- [사용자 정의 엔티티 및 관계 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/watson/developercloud/doc/natural-language-understanding/customizing.html){: new_window}를 식별하는 방법을 학습하십시오. 
