---

copyright:
  years: 2015, 2018
lastupdated: "2018-12-19"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:important: .important}
{:note: .note}
{:deprecated: .deprecated}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:javascript: .ph data-hd-programlang='javascript'}
{:go: .ph data-hd-programlang='go'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}
{:download: .download}
{:apikey: data-credential-placeholder='apikey'}
{:url: data-credential-placeholder='url'}
{:hide-dashboard: .hide-dashboard}

# 入門指導教學
{: #getting-started}

這個簡短的指導教學簡介了 {{site.data.keyword.nlushort}} API，其中包含範例要求和其他資源的鏈結。
{:shortdesc}

## 開始之前
{: #before-you-begin}

- {: hide-dashboard}建立服務的實例：
    1.  移至「{{site.data.keyword.Bluemix_notm}} 型錄」中的 [{{site.data.keyword.nlushort}} ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://{DomainName}/catalog/services/natural-language-understanding){: new_window} 頁面。
    2.  註冊免費的 {{site.data.keyword.Bluemix_notm}} 帳戶或登入。
    3.  按一下**建立**。
- 複製用來鑑別服務實例的認證：
    1.  在**管理**頁面上，按一下**顯示**以檢視您的認證。
    2.  複製 `API Key` 及 `URL` 值。
- 確定您有 `curl` 指令：
    - 這些範例會使用 `curl` 指令來呼叫 HTTP 介面的方法。從 [curl.haxx.se ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://curl.haxx.se/){: new_window} 安裝作業系統的版本。安裝支援 Secure Sockets Layer (SSL) 通訊協定的版本。請務必在 `PATH` 環境變數中包括已安裝的二進位檔。

本指導教學教您如何從指令行介面使用 {{site.data.keyword.nlushort}} API。若要下載各種程式設計語言的用戶端程式庫，請參閱 [Watson SDK](/docs/services/natural-language-understanding?topic=watson-using-sdks#using-sdks)。
{:tip}

## 步驟 1：分析網頁
{: #analyze-sample}

執行下列指令來分析網頁，以取得觀感、概念、種類、實體及關鍵字。<span class="hide-dashboard">將 `{apikey}` 及 `{url}` 取代為服務認證。</span>

```bash
curl -X POST -u "apikey:{apikey}"{: apikey} \
"{url}/v1/analyze?version=2018-11-16"{: url} \
--header "Content-Type: application/json" \
--data '{
  "url": "http://newsroom.ibm.com/Guerbet-and-IBM-Watson-Health-Announce-Strategic-Partnership-for-Artificial-Intelligence-in-Medical-Imaging-Liver",
  "features": {
    "sentiment": {},
    "categories": {},
    "concepts": {},
    "entities": {},
    "keywords": {}
  }
}'
```
{:pre}

下一步示範如何指定選項，以自訂每個特性的分析。

## 步驟 2：分析目標詞組及關鍵字
{: #analyze-phrase}

{{site.data.keyword.nlushort}} 可以分析周圍文字上下文中的目標詞組，以取得重點觀感及情緒結果。下列範例中觀感的 **targets** 選項會告知服務搜尋 "apples"、"oranges" 及 "broccoli" 目標。因為 "apples" 及 "oranges" 位於文字中，所以會針對這些目標傳回觀感評分。

您也可以針對文字中偵測到的實體和關鍵字，取得觀感及情緒結果。在此範例中，關鍵字的 **emotion** 選項會指示服務分析每個偵測到的關鍵字，以取得情緒結果。

```bash
curl -X POST -u "apikey:{apikey}"{: apikey} \
"{url}/v1/analyze?version=2018-11-16"{: url} \
--request POST \
--header "Content-Type: application/json" \
--data '{
  "text": "I love apples! I do not like oranges.",
  "features": {
    "sentiment": {
      "targets": [
        "apples",
        "oranges",
        "broccoli"
      ]
    },
    "keywords": {
      "emotion": true
    }
  }
}'
```
{:pre}

## 後續步驟
{: #next-steps}

- 檢視 [API 參考資料 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://{DomainName}/apidocs/natural-language-understanding){: new_window}。
- 瞭解如何識別[自訂實體及關係](/docs/services/natural-language-understanding?topic=natural-language-understanding-customizing)。
