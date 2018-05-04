---

copyright:
  years: 2015, 2018
lastupdated: "2018-03-16"

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

# 사용 한도

다음 사용 한도와 제한사항은 {{site.data.keyword.nlushort}} 서비스 인스턴스에 적용됩니다.
{: shortdesc}

## 분석된 텍스트 한계

{{site.data.keyword.nlushort}}에서는 50,000개의 1바이트 문자 또는 다중 바이트 문자가 넘게 포함된 분석된 텍스트를 자릅니다. 요청에서 이 한계를 계수하는 텍스트를 보려면 `return_analyzed_text` 매개변수를 `true`로 설정하십시오.

`limit_text_characters` 매개변수를 사용하여 적은 수의 문자 한계를 설정할 수 있습니다. 이렇게 하면 컨텐츠의 적은 부분만 분석하려는 경우 과도한 비용을 줄일 수 있습니다.

예제 매개변수 오브젝트:
```json
{
  "url": "ibm.com",
  "limit_text_characters": 10000,
  "return_analyzed_text": true,
  "features": {
    "concepts": {}
  }
}
```

## 동시 요청 한계

각 {{site.data.keyword.nlushort}} 서비스 인스턴스는 30개의 동시 요청으로 제한됩니다. 시스템에서 이례적으로 과도한 트래픽이 발생한 경우 라이트 및 표준 플랜에서는 서비스 인스턴스에 대해 이 한도를 줄여야 할 수도 있습니다. 예를 들어 단일 서비스 인스턴스에서 동시에 35개의 요청을 수행하는 애플리케이션은 5개의 요청으로 설정된 동시 요청 한계를 초과하므로, 5개의 해당 요청에서 `429: Too Many Requests` 오류를 리턴합니다.

동시 요청 한계를 늘리려면 [지원 티켓 열기](https://ibm.biz/ibmcloudsupport)를 수행하십시오.


## 언어 지원

서비스 사용 방법에 따라 다른 언어 제한사항이 적용됩니다. 자세한 내용은 [언어 지원](language-support.html) 페이지를 참조하십시오.


