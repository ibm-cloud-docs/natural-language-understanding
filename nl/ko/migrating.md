---

copyright:
  years: 2015, 2017
lastupdated: "2017-11-28"

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

# AlchemyLanguage에서 마이그레이션

**2017년 4월 7일**부터 {{site.data.keyword.cloud}}에서 더 이상 AlchemyAPI의 새 인스턴스를 작성할 수 없습니다. 기존 서비스 인스턴스는 **2018년 3월 7일**까지 지원됩니다. {{site.data.keyword.alchemylanguageshort}} 기능을 계속 사용하려면 {{site.data.keyword.nlushort}}에 코드를 마이그레이션해야 합니다.
{: shortdesc}

{{site.data.keyword.nlushort}}에서는 사용하기 훨씬 쉬워진 통합 API와 더 경제적인 가격 책정 모델을 제공합니다. 고객의 요구 사항에 맞게 유용성과 가치를 높이기 위해 기존 기능은 간소화됩니다. {{site.data.keyword.nlushort}}을 사용하면 브랜드를 관리하고 비즈니스 인텔리전스를 수집하며 일치하는 애드테크(ad-tech) 및 권장사항을 클러스터링하기가 쉬워집니다.

## 주요 변경사항 개요

- 새 API 요청 구문: `/analyze` 엔드포인트에 요청 전송
- 새 응답 구조({{site.data.keyword.alchemylanguageshort}} 출력을 구문 분석하는 코드가 {{site.data.keyword.nlushort}} 출력에 작동하지 않음)
- JSON은 유일한 출력 형식임
- *텍스트 추출*은 `return_analyzed_text` 매개변수를 `true`로 설정하여 사용함
- *마이크로포맷*은 지원되지 않음
- *날짜 추출*은 지원되지 않음(*공개 날짜*가 여전히 *메타데이터* 기능에 지원됨)
- 엔티티에 "quotations" 옵션은 지원되지 않음
- 개념, 키워드 또는 엔티티에 "knowledgeGraph"는 지원되지 않음
- 시각적 제한조건 조회(`cquery` 매개변수와 함께 사용)는 지원되지 않음
- JSONP 콜백은 지원되지 않음
- {{site.data.keyword.alchemylanguageshort}}의 *TypedRelations*은 {{site.data.keyword.nlushort}}의 *관계*임
- {{site.data.keyword.alchemylanguageshort}}의 *관계*는 {{site.data.keyword.nlushort}}의 *시맨틱 역할*임
- 엔티티 유형이 변경됨([여기](/docs/services/natural-language-understanding/entity-types.html)에서 새 엔티티 유형 확인)
- AlchemyLanguage 분류 결과에서 다음 단어의 철자가 틀렸습니다. 해당 철자는 Natural Language Understanding 카테고리 결과에서 정정되었습니다.
  - `offence` -> `offense`
  - `civl` -> `civil`
  - `phyiscs` -> `physics`

## 마이그레이션 단계

1. {{site.data.keyword.nlushort}} 서비스 [시작하기](/docs/services/natural-language-understanding/getting-started.html)를 수행합니다.
1. Watson Knowledge Studio의 사용자 정의 모델을 사용하는 경우 새 {{site.data.keyword.nlushort}} 서비스 인스턴스에 재배포합니다. [규칙 기반 어노테이터](/docs/services/knowledge-studio/rule-annotator-model-use.html#wks_rule_publish) 또는 [기계 학습 어노테이터](/docs/services/knowledge-studio/publish-ml.html#wks_manlu)를 배치하는 단계를 수행하고 {{site.data.keyword.nlushort}} 서비스를 배포 대상으로 선택합니다.
1. 코드를 마이그레이션합니다.
    Watson Developer Cloud SDK를 사용하여 {{site.data.keyword.alchemylanguageshort}}와 상호 작용하는 경우 SDK 코드를 변경해야 합니다. 다음 링크를 클릭하여 GitHub에서 {{site.data.keyword.nlushort}} SDK 예를 봅니다.
    - [Node.js ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://github.com/watson-developer-cloud/node-sdk#natural-language-understanding){: new_window}
    - [Python ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://github.com/watson-developer-cloud/python-sdk/blob/master/examples/natural_language_understanding_v1.py){: new_window}
    - [Swift ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://github.com/watson-developer-cloud/swift-sdk#natural-language-understanding){: new_window}

또한 {{site.data.keyword.alchemylanguageshort}} 요청의 출력을 예상하는 애플리케이션의 로직을 재구성해야 합니다. {{site.data.keyword.nlushort}}의 새 출력 구조를 처리하도록 코드를 조정하십시오.

### AlchemyLanguage 메소드와 해당 Natural Language Understanding 기능
{{site.data.keyword.alchemylanguageshort}} 요청이 {{site.data.keyword.nlushort}} `/analyze` 엔드포인트에 맵핑됩니다. `/analyze`에 대한 요청은 {{site.data.keyword.alchemylanguageshort}}의 결합된 호출 요청과 비슷하지만 구문은 다르므로, 각 기능에 맞게 `limit`와 같은 옵션을 개별적으로 지정할 수 있습니다. `/analyze`에 POST에서는 요청의 매개변수와 입력을 포함하는 JSON 본문을 승인하고 `/analyze`에 GET에서는 JSON 매개변수 구문과 유사한 조회 매개변수를 승인합니다.

| {{site.data.keyword.alchemylanguageshort}} 메소드 | {{site.data.keyword.alchemylanguageshort}} 엔드포인트 | {{site.data.keyword.nlushort}} 기능 |
|------------------------|--------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------|
| 작성자 | `/text/TextGetAuthors`<br/>`/url/URLGetAuthors` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#metadata">메타데이터</a> |
| 개념 | `/html/HTMLGetRankedConcepts`<br/>`/text/TextGetRankedConcepts`<br/>`/url/URLGetRankedConcepts` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#concepts">개념</a> |
| 날짜 추출 | `/html/HTMLExtractDates`<br/>`/text/TextExtractDates`<br/>`/url/URLExtractDates` | 지원되지 않음 |
| 감정 분석 | `/html/HTMLGetEmotion`<br/>`/text/TextGetEmotion`<br/>`/url/URLGetEmotion` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#emotion">감정</a> |
| 대상 감정 | `/html/HTMLGetTargetedEmotion`<br/>`/text/TextGetTargetedEmotion`<br/>`/url/URLGetTargetedEmotion` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#emotion">감정</a>(`targets` 옵션 사용) |
| 엔티티 | `/html/HTMLGetRankedNamedEntities`<br/>`/text/TextGetRankedNamedEntities`<br/>`/url/URLGetRankedNamedEntities` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#entities">엔티티</a> |
| 피드 감지 | `/html/HTMLGetFeedLinks`<br/>`/url/URLGetFeedLinks` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#metadata">메타데이터</a> |
| 키워드 | `/html/HTMLGetRankedKeywords`<br/>`/text/TextGetRankedKeywords`<br/>`/url/URLGetRankedKeywords` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#keywords">키워드</a> |
| 언어 감지 | `/html/HTMLGetLanguage`<br/>`/text/TextGetLanguage`<br/>`/url/URLGetLanguage` | 기본 언어 감지는 모든 요청에서 무료로 수행됩니다. ISO 코드 이외의 언어 메타데이터는 리턴되지 않습니다. |
| 마이크로 포맷 | `/html/HTMLGetMicroformatData`<br/>`/url/URLGetMicroformatData` | 지원되지 않음 |
| 발행 날짜 | `/html/HTMLGetPubDate`<br/>`/url/URLGetPubDate` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#metadata">메타데이터</a> |
| 관계 | `/html/HTMLGetRelations`<br/>`/text/TextGetRelations`<br/>`/url/URLGetRelations` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#semantic-roles">시맨틱 역할</a> |
| 유형이 지정된 관계 | `/html/HTMLGetTypedRelations`<br/>`/text/TextGetTypedRelations`<br/>`/url/URLGetTypedRelations` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#relations">관계</a> |
| 감성 분석 | `/html/HTMLGetTextSentiment`<br/>`/text/TextGetTextSentiment`<br/>`/url/URLGetTextSentiment` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#sentiment">감성</a> |
| 대상이 지정된 감성 | `/html/HTMLGetTargetedSentiment`<br/>`/text/TextGetTargetedSentiment`<br/>`/url/URLGetTargetedSentiment` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#sentiment">감성</a>(`targets` 옵션 사용) |
| 분류 | `/html/HTMLGetRankedTaxonomy`<br/>`/text/TextGetRankedTaxonomy`<br/>`/url/URLGetRankedTaxonomy` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#categories">카테고리</a> |
| 텍스트(정리됨) | `/html/HTMLGetText`<br/>`/url/URLGetText` | 올바른 `/analyze` 요청에서 `return_analyzed_text`를 `true`로 설정 |
| 텍스트(원시) | `/html/HTMLGetRawText`<br/>`/url/URLGetRawText` | 올바른 `/analyze` 요청에서 `return_analyzed_text`를 `true`로 설정하고 `clean`은 `false`로 설정 |
| 제목 추출 | `/html/HTMLGetTitle`<br/>`/url/URLGetTitle` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#metadata">메타데이터</a> |

다음과 같이 결합된 호출을 수행하는 경우,

```bash
curl -X POST \
-d "outputMode=json" \
-d "extract=entities,keywords" \
-d "sentiment=1" \
-d "limit=1" \
-d "url=https://www.ibm.com/us-en/" \
"https://gateway.watsonplatform.net/calls/url/URLGetCombinedData?apikey=$API_KEY"
```
{: pre}

{{site.data.keyword.nlushort}}에서 다음과 같이 표시됩니다.

```bash
curl -X POST \
-H "Content-Type: application/json" \
-u "{username}":"{password}" \
-d @parameters.json "https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze?version=2017-02-27"
```
{: pre}

이 parameters.json을 사용하는 경우,

```json
{
  "url": "https://www.ibm.com/us-en/",
  "features": {
    "entities": {
      "sentiment": true,
      "limit": 1
    },
    "keywords": {
      "sentiment": true,
      "limit": 1
    }
  }
}
```
{: codeblock}

## 엔티티 조화

{{site.data.keyword.alchemylanguageshort}}의 TypedRelations 메소드에서 공용 모델을 사용한 경우 해당 모델에서 엔티티 유형을 기대하는 모든 코드를 변경해야 합니다. 다음 표에서는 TypedRelations 엔티티 유형과 {{site.data.keyword.nlushort}} 엔티티 유형의 맵핑을 보여줍니다.

| TypedRelations 엔티티 유형 | {{site.data.keyword.nlushort}} 관계 엔티티 유형 |
|----------------------------|------------------------------------------------------|
| 수명 | 수명 |
| 동물 | 동물 |
| 상 | 상 |
| 기수 | 기수 |
| 날짜 | 날짜  |
| 학위 | 학위 |
| 질병 | 건강 상태 |
| 지속 시간 | 지속 시간 |
| 이메일 | 이메일 주소 |
| 이벤트 | 이벤트 |
| 설비 | 설비 |
| 음식 | 음식 |
| 지리학적 물체 | 지형지물 |
| GPE | 지정학적 엔티티 |
| 법률 | 법률 |
| 위치 | 위치 |
| 수치 | 수치 |
| 금전 | 금전 |
| 서수 | 서수 |
| 장기 | 해부 |
| 조직 | 조직 |
| 사람 | 개인 |
| 백분율 | 백분율 |
| 사람 | 개인 |
| 개인 | 개인 |
| 전화 | 전화 |
| 공장 | 공장 |
| 제품 | 제품 |
| 물질 | 물질 |
| 티커 | 티커 |
| 시간 | 시간 |
| 물권 보험 작업 | 물권 보험 작업 |
| 차량 | 차량 |
| 무기 | 무기 |
| 날씨 | 날씨 |
| 웹 | 웹 |
| 이벤트_상 | 상 |
| 이벤트_비즈니스 | 이벤트 비즈니스 |
| 이벤트_통신 | 이벤트 통신 |
| 이벤트_범죄 | 범죄 |
| 이벤트_관리 | 이벤트 관리 |
| 이벤트_데모 | 이벤트 데모 |
| 이벤트_재해 | 자연 이벤트 |
| 이벤트_교육 | 이벤트 교육 |
| 이벤트_선거 | 이벤트 선거 |
| 이벤트_법률 | 이벤트 법률 |
| 이벤트_입법 | 이벤트 입법 |
| 이벤트_회의 | 이벤트 회의 |
| 이벤트_모임 | 이벤트 모임 |
| 이벤트_공연 | 이벤트 공연 |
| 이벤트_담당자 | 이벤트 담당자 |
| 이벤트_스포츠 | 스포츠 이벤트 |
| 이벤트_폭력 | 이벤트 폭력 |
| 이벤트 | 이벤트 |
