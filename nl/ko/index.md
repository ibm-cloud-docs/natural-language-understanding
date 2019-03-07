---

copyright:
  years: 2015, 2019
lastupdated: "2019-02-25"

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

# 정보
{: #about}

개발자가 {{site.data.keyword.nlufull}}을 사용하여 카테고리, 개념, 감정, 엔티티, 키워드, 메타데이터, 관계, 시맨틱 역할 및 감성을 포함하는 텍스트 입력의 시맨틱 기능을 분석할 수 있습니다.
{: shortdesc}

## 기능
{: #features}

텍스트, HTML 또는 공용 URL을 사용하여 API에 요청을 보내고 다음 기능 중 하나 이상을 지정하여 분석하십시오.

### 카테고리
{: #categories}

5레벨 분류 계층 구조를 사용하여 컨텐츠를 분류하십시오. 전체 카테고리 목록은 [여기](/docs/services/natural-language-understanding?topic=natural-language-understanding-categories-hierarchy)를 보십시오. 예를 들어, 다음과 같습니다.

**입력**
> url: "www.cnn.com"

**응답**
> /news </br>
> /art and entertainment </br>
> /movies and tv/television </br>
> /news </br>
> /international news

### 개념
{: #concepts}

텍스트에서 직접 참조되지 않을 수 있는 상위 레벨 개념을 식별하십시오. 예를 들어, 다음과 같습니다.

**입력**
> 텍스트: "Natural Language Understanding uses natural language processing to analyze text."

**응답**
> Linguistics </br>
> Natural language processing </br>
> Natural language understanding

### 감정
{: #emotion}

특정 대상 문구 또는 문서 전체로 전달되는 감정을 분석하십시오. 서비스에서 자동으로 감지하는 엔티티와 키워드에 대해서도 감정 분석을 사용할 수 있습니다. 예를 들어, 다음과 같습니다.

**입력**
> 텍스트: "I love apples, but I hate oranges." </br>
> 대상: "apples" 및 "oranges"

**응답**
> "apples": 기쁨 </br>
> "oranges": 분노

### 엔티티
{: #entities}

컨텐츠에 언급된 엔티티의 사용자, 위치, 이벤트 및 기타 유형을 찾으십시오. 엔티티 유형과 하위 유형의 전체 목록은 [여기](/docs/services/natural-language-understanding?topic=natural-language-understanding-entity-type-systems)를 보십시오. 예를 들어, 다음과 같습니다.

**입력**
> 텍스트: "IBM is an American multinational technology company headquartered in Armonk, New York, United States, with operations in over 170 countries."

**응답**
> IBM: 회사 </br>
> Armonk: 위치 </br>
> New York: 위치 </br>
> United States: 위치

### 키워드
{: #keywords}

관련 키워드를 컨텐츠를 검색하십시오. 예를 들어, 다음과 같습니다.

**입력**
>url: "[http://www-03.ibm.com/press/us/en/pressrelease/51493.wss](http://www-03.ibm.com/press/us/en/pressrelease/51493.wss)"

**응답**
>Australian Open </br>
>Tennis Australia </br>
>IBM SlamTracker analytics

### 메타데이터
{: #metadata}

HTML와 URL 입력의 경우 웹 페이지의 작성자, 페이지 제목 및 발행 날짜를 가져오십시오. 예를 들어, 다음과 같습니다.

**입력**
>url: "https://www.ibm.com/blogs/think/2017/01/cognitive-grid/"

**응답**
>작성자: Stephen Callahan </br>
>제목: Girding the Grid with Cognitive Computing - THINK Blog </br>
>발행 날짜: January 31, 2017

### 관계
{: #relations}

두 엔티티가 관련된 시기를 인식하고 관계의 유형을 식별합니다. 예를 들어, 다음과 같습니다.

**입력**
>텍스트: "The Nobel Prize in Physics 1921 was awarded to Albert Einstein."

**응답**
>"Noble Prize in Physics"와 "Albert Einstein" 사이에 "awardedTo" 관계 </br>
>"1921"과 "awarded" 사이에 "timeOf" 관계

### 시맨틱 역할
{: #semantic-roles}

주어-동작-목적어 양식으로 문장을 구문 분석하고 조치의 오브젝트이거나 주제인 키워드와 엔티티를 식별합니다. 예를 들어, 다음과 같습니다.

**입력**
>텍스트: "In 2011, Watson competed on Jeopardy!"

**응답**
>주어: Watson </br>
>조치: competed </br>
>목적어: on Jeopardy

### 감성
{: #sentiment}

특정 대상 문구의 감성과 문서 전체의 감성을 분석합니다. 해당 기능에 감성 옵션을 사용하여 감지된 엔티티와 키워드에 대한 감성 정보도 가져올 수 있습니다. 예를 들어, 다음과 같습니다.

**입력**
>텍스트: "Thank you and have a nice day!"

**응답**
>긍정적인 감성(점수: 0.91)

## 지원되는 언어
{: #supported-languages}

{{site.data.keyword.nlushort}}에서 지원되는 언어에 대한 자세한 내용은 [언어 지원 문서](/docs/services/natural-language-understanding?topic=natural-language-understanding-language-support)를 참조하십시오.
