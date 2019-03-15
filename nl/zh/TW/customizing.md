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

# 自訂
{: #customizing}

透過 [{{site.data.keyword.knowledgestudiofull}} ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://ibm.biz/watsonknowledgestudio)，您可以使用能夠識別您的網域獨有之自訂實體及關係的自訂模型來擴充 {{site.data.keyword.nlushort}}。
{: shortdesc}

## 開始使用自訂模型
{: #getting-started-with-custom-models}

> {{site.data.keyword.nlushort}} 免費方案會限制自訂模型的大小及效能。若要完整測試自訂模型，您需要將它與 {{site.data.keyword.nlushort}} 標準方案搭配使用。

1. 如果您還沒有這麼做，請[開始使用](/docs/services/natural-language-understanding?topic=natural-language-understanding-getting-started) {{site.data.keyword.nlushort}}。
2. [開始使用 {{site.data.keyword.knowledgestudioshort}}](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-wks_tutintro#wks_tutintro)。
3. [使用 {{site.data.keyword.knowledgestudioshort}} 建立機器學習模型](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-wks_tutml_intro#wks_tutml_intro)。
4. [將模型部署至 {{site.data.keyword.nlushort}}](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-publish-ml#wks_manlu)
5. 若要使用您的模型，請指定 API 要求的[實體 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://{DomainName}/apidocs/natural-language-understanding#entities){: new_window} 或[關係 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://{DomainName}/apidocs/natural-language-understanding#relations){: new_window} 選項中所部署的 `model`：
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
        curl --user "apikey":"{apikey}" \
        "{url}/v1/analyze?version=2018-09-21" \
        --request POST \
        --header "Content-Type: application/json" \
        --data @parameters.json
        ```
        {: pre}

## 刪除自訂模型
{: #deleting-a-custom-model}

您部署至 {{site.data.keyword.nlushort}} 的自訂模型數目會根據[定價方案](https://www.ibm.com/cloud/watson-natural-language-understanding/pricing)影響您的 {{site.data.keyword.nlushort}} 帳單。若要避免為不再使用的模型付費，請[使用 {{site.data.keyword.knowledgestudioshort}} 取消部署模型](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-publish-ml#undeploy-view-model)，或使用**[刪除模型](https://{DomainName}/apidocs/natural-language-understanding#delete-model)**方法來取消部署該模型。

範例 curl 要求：

```bash
curl --user "apikey":"{apikey}" \
"{url}/v1/models/{model_id}?version=2018-10-30" \
--request DELETE
```
{: pre}


## 自訂模型的語言支援
{: #language-support-for-custom-models}

請檢閱[語言支援](/docs/services/natural-language-understanding?topic=natural-language-understanding-language-support)頁面上表格中的*自訂模型支援*直欄，以查看每一種語言支援的自訂模型。

### 自訂模型實體的目標觀感
{: #targeted-sentiment-for-custom-entities}

這僅適用於英文版，您可以在實體物件中設定 `sentiment: true` 選項，藉以取得服務所偵測到之每個自訂模型實體的觀感評分。沒有任何其他語言支援自訂模型實體的目標觀感。
