---

copyright:
  years: 2015, 2018
lastupdated: "2018-01-16"

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

# 사용자 정의

[{{site.data.keyword.knowledgestudiofull}} ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://ibm.biz/watsonknowledgestudio)를 사용하면 도메인에 고유한 사용자 정의 엔티티와 관계를 식별하는 사용자 정의 모델을 사용하여 {{site.data.keyword.nlushort}}을 확장할 수 있습니다.
{: shortdesc}

## 사용자 정의 모델 시작하기

> {{site.data.keyword.nlushort}} 무료 사용제에서는 사용자 정의 모델의 크기와 성능이 제한됩니다. 사용자 정의 모델 전체를 테스트하려면 {{site.data.keyword.nlushort}} 표준 플랜에서 사용해야 합니다.

1. 이미 수행하지 않은 경우 {{site.data.keyword.nlushort}}으로 [시작하기](/docs/services/natural-language-understanding/getting-started.html)를 수행하십시오.
1. [{{site.data.keyword.knowledgestudioshort}} ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/us-en/marketplace/supervised-machine-learning/purchase#product-header-top)에 액세스하고 [온라인 대시보드 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://gateway.watsonplatform.net/knowledge-studio/ui/dashboard/)를 통해 로그인하십시오.
1. {{site.data.keyword.knowledgestudioshort}} [문서](/docs/services/knowledge-studio/index.html)에서 사용자 정의 모델(어노테이터)을 작성하고 {{site.data.keyword.nlushort}}에 배치하는 방법을 알아봅니다.
1. 모델을 사용하려면 API 요청의
[엔티티 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/#entities){: new_window} 또는
[관계 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/#relations){: new_window} 옵션에서 배치한 `모델`을 지정하십시오.
    - 예제 *parameters.json* 파일:

        ```json
        {
          "url": "www.url.example",
          "features": {
            "entities": {
              "model": "your-model-id-here"
            },
            "relations": {
              "model": "your-model-id-here"
            }
          }
        }
        ```
        {: codeblock}
    
    - 예제 curl 요청:

        ```bash
        curl -X POST \
        -H "Content-Type: application/json" \
        -u "{username}":"{password}" \
        -d @parameters.json \
        "https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze?version=2017-02-27"
        ```
        {: pre}

