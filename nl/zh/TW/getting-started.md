---

copyright:
  years: 2015, 2017
lastupdated: "2017-11-03"

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

# 入門指導教學
在這份簡短的指導教學中，我們會分析一些範例文字的觀感，來介紹 {{site.data.keyword.nlushort}}。
{:shortdesc}

## 開始之前
{: #before-you-begin}

- 建立服務的實例：
    - {: download} 如果您看到此項目，則表示您已建立服務實例。現在請取得您的認證。
    - 從服務中建立專案：
        1.  移至 {{site.data.keyword.watson}} Developer Console [服務 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.{DomainName}/developer/watson/services){: new_window} 頁面。
        1.  選取 {{site.data.keyword.nlushort}}，並按一下**新增服務**，然後註冊免費的 {{site.data.keyword.Bluemix_notm}} 帳戶，或是進行登入。
        1.  鍵入 `sentiment-tutorial` 作為專案名稱，然後按一下**建立專案**。
- 複製用來鑑別服務實例的認證：
    - {: download} 從您正在查看的服務儀表板：
        1.  按一下**服務認證**標籤。
        1.  按一下**動作**底下的**檢視認證**。
        1.  複製 `username`、`password` 及 `url` 值。
        {: download}
    - 從 Developer Console 的 **sentiment-tutorial** 專案中，複製**認證**區段之 `"natural_language_understanding"` 的 `username`、`password` 及 `url` 值。
- 確定您有 cURL：
    - 範例會使用 cURL 來呼叫 HTTP 介面的方法。從 [curl.haxx.se ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://curl.haxx.se/){: new_window} 安裝作業系統的版本。安裝支援 Secure Sockets Layer (SSL) 通訊協定的版本。請務必在 `PATH` 環境變數中包括已安裝的二進位檔。

<!-- Remove this text after dedicated instances have the Developer Console: begin -->

如果您使用 {{site.data.keyword.Bluemix_dedicated_notm}}，請從「型錄」的 [{{site.data.keyword.nlushort}} ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.{DomainName}/catalog/services/natural-language-understanding/){: new_window} 頁面建立服務實例。如需如何尋找服務認證的詳細資料，請參閱 [Watson 服務的服務認證 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](/docs/services/watson/getting-started-credentials.html#getting-credentials-manually){: new_window}。

<!-- Remove this text after dedicated instances have the Developer Console: end -->

## 步驟 1：分析範例內容的觀感
{: #analyze-sample}

首先，分析部分範例文字的觀感。開啟指令行介面，並執行下列指令來呼叫 `GET /v1/analyze` 方法，以分析範例文字的觀感及關鍵字。將 `{username}` 及 `{password}` 取代為您在先前步驟中複製的服務認證：

```bash
curl --user "{username}":"{password}" \
"https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze?version=2017-02-27&text=I%20still%20have%20a%20dream%2C%20a%20dream%20deeply%20rooted%20in%20the%20American%20dream%20%E2%80%93%20one%20day%20this%20nation%20will%20rise%20up%20and%20live%20up%20to%20its%20creed%2C%20%22We%20hold%20these%20truths%20to%20be%20self%20evident%3A%20that%20all%20men%20are%20created%20equal.&features=sentiment,keywords"
```
{:pre}

## 步驟 2：傳回關鍵字資訊
{: #analyze-keywords}

先前的呼叫傳回了整段文字的觀感資訊。現在，請展開結果以傳回特定針對每個關鍵字的觀感分析。請包含 **keywords.sentiment** 參數並將它設為 `true`。將 `{username}` 及 `{password}` 取代為您的資訊。

```bash
curl --user "{username}":"{password}" \
"https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze?version=2017-02-27&text=I%20still%20have%20a%20dream%2C%20a%20dream%20deeply%20rooted%20in%20the%20American%20dream%20%E2%80%93%20one%20day%20this%20nation%20will%20rise%20up%20and%20live%20up%20to%20its%20creed%2C%20%22We%20hold%20these%20truths%20to%20be%20self%20evident%3A%20that%20all%20men%20are%20created%20equal.&features=sentiment,keywords&keywords.sentiment=true"
```
{:pre}

## 步驟 3：以詞組為目標
{: #analyze-phrase}

現在，以特定內容為目標，查看句子層次或片語層次的分析（而非文件或關鍵字分析），方法是在 **sentiment.targets** 參數中包含片語 `the%20American%20dream%20`。別忘了將 `{username}` 及 `{password}` 取代為您的資訊。

```bash
curl --user "{username}":"{password}" \
"https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze?version=2017-02-27&text=I%20still%20have%20a%20dream%2C%20a%20dream%20deeply%20rooted%20in%20the%20American%20dream%20one%20day%20this%20nation%20will%20rise%20up%20and%20live%20up%20to%20its%20creed%20We%20hold%20these%20truths%20to%20be%20self%20evident%3A%20that%20all%20men%20are%20created%20equal.&features=sentiment,keywords&keywords.sentiment=true&sentiment.targets=the%20American%20dream"
```
{:pre}

## 後續步驟
{: #next-steps}

完成了！本指導教學勉強淺談了您可以用 {{site.data.keyword.nlushort}} 達成的事。如需 API 特性的相關資訊，請參閱下列資源：

- 檢視 [API 參考資料 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/){: new_window} 以取得每個參數的詳細資料及範例。
- 瞭解如何識別[自訂實體及關係](/docs/services/natural-language-understanding/customizing.html)。
