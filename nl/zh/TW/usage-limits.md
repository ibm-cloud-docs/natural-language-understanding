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

# 使用限制

下列使用限制適用於 {{site.data.keyword.nlushort}} 服務實例。
{: shortdesc}

## 已分析的文字限制

{{site.data.keyword.nlushort}} 會截斷已分析的文字，其中包含超過 50,000 個單位元組或多位元組字元。若要檢視計入要求中此限制計數的文字，請將 `return_analyzed_text` 參數設為 `true`。

您可以使用 `limit_text_characters` 參數設定較小的字元限制。如果您想要只分析小部分的內容，則這可協助您避免成本過高。

範例參數物件：
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

## 並行要求限制

每一個 {{site.data.keyword.nlushort}} 服務實例都會限制為 30 個並行要求。系統遇到大量資料流量時，可能會降低精簡及標準方案上服務實例的這個限制。例如，從單一服務實例提出 35 個同時要求的應用程式比並行要求限制多五個要求，而其中的五個要求會傳回 `429: Too Many Requests` 錯誤。

若要增加您的並行要求限制，請[開立支援問題單](https://ibm.biz/ibmcloudsupport)。


## 語言支援

根據您使用服務的方式，會有不同的語言限制。如需詳細資料，請參閱[語言支援](language-support.html)頁面。


