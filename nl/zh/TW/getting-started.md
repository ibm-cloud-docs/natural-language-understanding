---

copyright:
  years: 2015, 2017
lastupdated: "2017-06-09"

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

# 開始使用指導教學
在這份簡短的指導教學中，我們會分析一些範例文字的觀感，來介紹 {{site.data.keyword.nlushort}}。
{:shortdesc}

## 步驟 1：登入、建立服務實例，然後取得認證
{: #create-service}

如果您已知道 {{site.data.keyword.nlushort}} 服務實例的認證，請跳過此步驟。
{: tip}

1.  移至 [{{site.data.keyword.nlushort}} 服務](https://console.{DomainName}/catalog/services/natural-language-understanding/)，註冊免費的 {{site.data.keyword.Bluemix_notm}} 帳戶，或是進行登入。
1.  登入之後，在**服務名稱**欄位鍵入 `sentiment-tutorial`，然後按一下**建立**。
1.  複製您的認證：
    1.  按一下**服務認證**。
    1.  按一下**動作**底下的**檢視認證**。
    1.  複製 `username` 及 `password` 值。

## 步驟 2：分析範例內容裡的觀感
{: #analyze-sample}

首先，分析部分範例文字的觀感。發出這個指令以便呼叫 `GET /v1/analyze` 方法，它會分析範例文字的觀感及關鍵字。將 `{username}` 及 `{password}` 取代為您在先前步驟中複製的服務認證：

```bash
curl --user "{username}":"{password}" \
"https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze?version=2017-02-27&text=I%20still%20have%20a%20dream%2C%20a%20dream%20deeply%20rooted%20in%20the%20American%20dream%20%E2%80%93%20one%20day%20this%20nation%20will%20rise%20up%20and%20live%20up%20to%20its%20creed%2C%20%22We%20hold%20these%20truths%20to%20be%20self%20evident%3A%20that%20all%20men%20are%20created%20equal.&features=sentiment,keywords"
```
{:pre}

## 步驟 3：傳回關鍵字資訊
{: #analyze-keywords}

先前的呼叫傳回了整段文字的觀感資訊。現在，請展開結果以傳回特定針對每個關鍵字的觀感分析。請包含 **keywords.sentiment** 參數並將它設為 `true`。將 `{username}` 及 `{password}` 取代為您的資訊。

```bash
curl --user "{username}":"{password}" \
"https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze?version=2017-02-27&text=I%20still%20have%20a%20dream%2C%20a%20dream%20deeply%20rooted%20in%20the%20American%20dream%20%E2%80%93%20one%20day%20this%20nation%20will%20rise%20up%20and%20live%20up%20to%20its%20creed%2C%20%22We%20hold%20these%20truths%20to%20be%20self%20evident%3A%20that%20all%20men%20are%20created%20equal.&features=sentiment,keywords&keywords.sentiment=true"
```
{:pre}

## 步驟 4：以片語為目標
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

- 檢視 [API 參考資料 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/ "外部鏈結圖示"){: new_window} 以取得每個參數的詳細資料及範例。
- 了解如何識別[自訂實體及關係 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/watson/developercloud/doc/natural-language-understanding/customizing.html "外部鏈結圖示"){: new_window}。
