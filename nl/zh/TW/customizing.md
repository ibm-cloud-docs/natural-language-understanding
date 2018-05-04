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

# 自訂

透過 [{{site.data.keyword.knowledgestudiofull}} ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://ibm.biz/watsonknowledgestudio)，您可以使用能夠識別您的網域獨有之自訂實體及關係的自訂模型來擴充 {{site.data.keyword.nlushort}}。
{: shortdesc}

## 開始使用自訂模型

> {{site.data.keyword.nlushort}} 免費方案會限制自訂模型的大小及效能。若要完整測試自訂模型，您需要將它與 {{site.data.keyword.nlushort}} 標準方案搭配使用。

1. 如果您還沒有這麼做，請[開始使用](/docs/services/natural-language-understanding/getting-started.html) {{site.data.keyword.nlushort}}。
1. [取得 {{site.data.keyword.knowledgestudioshort}} 的存取權 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/us-en/marketplace/supervised-machine-learning/purchase#product-header-top)，並透過[線上儀表板 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://gateway.watsonplatform.net/knowledge-studio/ui/dashboard/) 登入。
1. 檢視 {{site.data.keyword.knowledgestudioshort}} [文件](/docs/services/knowledge-studio/index.html) 以瞭解如何建立自訂模型（註解程式），並將它部署至 {{site.data.keyword.nlushort}}。
1. 若要使用您的模型，請指定 API 要求的[實體 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/#entities){: new_window} 或[關係 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/#relations){: new_window} 選項中所部署的 `model`：
    - 範例 *parameters.json* 檔案：

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
    
    - 範例 curl 要求：

        ```bash
        curl -X POST \
        -H "Content-Type: application/json" \
        -u "{username}":"{password}" \
        -d @parameters.json \
        "https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze?version=2017-02-27"
        ```
        {: pre}

