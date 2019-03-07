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

# 사용자 정의
{: #customizing}

[{{site.data.keyword.knowledgestudiofull}} ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://ibm.biz/watsonknowledgestudio)를 사용하면 도메인에 고유한 사용자 정의 엔티티와 관계를 식별하는 사용자 정의 모델을 사용하여 {{site.data.keyword.nlushort}}을 확장할 수 있습니다.
{: shortdesc}

## 사용자 정의 모델 시작하기
{: #getting-started-with-custom-models}

> {{site.data.keyword.nlushort}} 무료 플랜에서는 사용자 정의 모델의 크기와 성능이 제한됩니다. 사용자 정의 모델 전체를 테스트하려면 {{site.data.keyword.nlushort}} 표준 플랜에서 사용해야 합니다.

1. 이미 수행하지 않은 경우 {{site.data.keyword.nlushort}}으로 [시작하기](/docs/services/natural-language-understanding?topic=natural-language-understanding-getting-started)를 수행하십시오.
2. [{{site.data.keyword.knowledgestudioshort}}](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-wks_tutintro#wks_tutintro)를 시작하십시오.
3. [{{site.data.keyword.knowledgestudioshort}}](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-wks_tutml_intro#wks_tutml_intro)로 기계 학습 모델을 작성하십시오.
4. [모델을 {{site.data.keyword.nlushort}}](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-publish-ml#wks_manlu)에 배치하십시오.
5. 모델을 사용하려면 API 요청의
[엔티티 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://{DomainName}/apidocs/natural-language-understanding#entities){: new_window} 또는
[관계 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://{DomainName}/apidocs/natural-language-understanding#relations){: new_window} 옵션에서 배치한 `모델`을 지정하십시오.
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
        curl --user "apikey":"{apikey}" \
        "{url}/v1/analyze?version=2018-09-21" \
        --request POST \
        --header "Content-Type: application/json" \
        --data @parameters.json
        ```
        {: pre}

## 사용자 정의 모델 삭제
{: #deleting-a-custom-model}

{{site.data.keyword.nlushort}}에 배치하는 사용자 정의 모델 수는 [가격 플랜](https://www.ibm.com/cloud/watson-natural-language-understanding/pricing)에 따라 {{site.data.keyword.nlushort}} 비용 청구에 영향을 미칩니다. 더 이상 사용하지 않는 모델의 변경을 방지하려면 [{{site.data.keyword.knowledgestudioshort}}](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-publish-ml#undeploy-view-model)로 모델 배치 취소 또는 **[모델 삭제](https://{DomainName}/apidocs/natural-language-understanding#delete-model)** 방법으로 모델의 배치를 취소하십시오.

예제 curl 요청:

```bash
curl --user "apikey":"{apikey}" \
"{url}/v1/models/{model_id}?version=2018-10-30" \
--request DELETE
```
{: pre}


## 사용자 정의 모델의 언어 지원
{: #language-support-for-custom-models}

[언어 지원](/docs/services/natural-language-understanding?topic=natural-language-understanding-language-support) 페이지의 표에서 *사용자 정의 모델 지원*을 선택하여 각 언어에 지원되는 사용자 정의 모델을 확인하십시오.

### 사용자 정의 모델 엔티티의 대상 감성
{: #targeted-sentiment-for-custom-entities}

영어에 한해 엔티티 오브젝트에서 `sentiment: true` 옵션을 설정하여 서비스에서 발견한 각 사용자 정의 모델 엔티티의 감성 점수를 얻을 수 있습니다. 다른 언어에서는 사용자 정의 모델 엔티티의 대상 감성을 지원하지 않습니다.
