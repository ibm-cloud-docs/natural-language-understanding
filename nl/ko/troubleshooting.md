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
{:download: .download}

# 문제점 해결
{: #troubleshooting}

{{site.data.keyword.nlushort}}에 문제점이 있으면 다음 문제점 해결 팁이 도움이 될 수 있습니다.
{:shortdesc}

## 엔티티와 관계 엔티티 유형이 일치하지 않음
{: #inconsistent-entity-types}

엔티티와 관계 기능의 엔티티 유형 시스템이 항상 일치하지는 않습니다. 일부 언어와 버전 날짜의 경우 관계 결과에는 엔티티 결과에 표시되는 엔티티 유형과 다른 엔티티 유형이 표시됩니다. 자세한 정보는 [엔티티 유형 및 하위 유형](/docs/services/natural-language-understanding?topic=natural-language-understanding-entity-type-systems)과 [관계 유형](/docs/services/natural-language-understanding?topic=natural-language-understanding-relation-type-systems)을 참조하십시오. 

## 잘못된 언어 감지
{: #incorrect-language-detection}

100자 미만을 포함하는 텍스트의 경우 자동 언어 감지가 정확하지 않을 수 있습니다. 서비스에서 텍스트의 올바른 언어를 감지하지 못하면 [자동 언어 감지를 대체](/docs/services/natural-language-understanding?topic=natural-language-understanding-overriding-language-detection)할 수 있습니다.

## 요청이 너무 많음
{: #too-many requests}

"429: 요청이 너무 많음" 오류가 표시되면 서비스 인스턴스가 동시 요청 한계에 도달했을 가능성이 큽니다. 자세한 정보는 [사용 한계](/docs/services/natural-language-understanding?topic=natural-language-understanding-usage-limits#concurrent-requests) 페이지를 보십시오.

## 웹 페이지 분석에서 예상치 못한 결과
{: #unexpected-webpage-results}

웹 페이지를 분석하면 경우에 따라 예상치 못한 결과를 리턴할 수 있습니다. 이 문제를 조사하려면 **return_analyzed_text** 매개변수를 `true`로 설정하여 요청에서 분석 중인 실제 텍스트를 조사하십시오. [웹 페이지 정리](/docs/services/natural-language-understanding?topic=natural-language-understanding-analyzing-webpages#webpage-cleaning)가 원하지 않는 텍스트를 충분히 제거하지 않는 경우 [**xpath**](/docs/services/natural-language-understanding?topic=natural-language-understanding-analyzing-webpages#xpath) 매개변수를 사용하여 페이지의 특정 요소를 분석하는 데 중점을 두십시오.

## 특정 결과 설명
{: #explanations-for-results}

{{site.data.keyword.nlushort}}에서는 특정 요청에서 특정 결과를 리턴하는 이유를 설명하는 진단 도구를 제공하지 않습니다. 이 서비스는 가능한 많은 텍스트 샘플에 대해 정확한 결과를 제공하도록 디자인되었지만, 사용하는 기계 학습 모델의 특성으로 인해 사용자의 관점에서 특정 결과가 올바르게 표시된다는 보장이 없습니다.






