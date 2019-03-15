---

copyright:
  years: 2015, 2018
lastupdated: "2018-10-30"

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


# 分析網頁
{: #analyzing-webpages}

{{site.data.keyword.nlushort}} 可讓您以程式設計方式分析網頁中的文字。當您在 API 要求中提供原始 HTML 或可公開存取的 URL 時，服務會嘗試將分析重點放在頁面的主要內容，例如新聞文章或部落格文章中的文字。

**如何運作：**

1. 使用 **url** 參數指定可公開存取的 URL，或以 **html** 參數傳送原始的 HTML。
2. 依預設，服務會[清理](#webpage-cleaning)網頁，以移除通常不想要的文字，例如廣告。
3. 如果您使用 **xpath** 參數指定 [XPath 查詢](#xpath)，則服務會使用該查詢來選取要包括在分析中的頁面特定元素。如果使用 **xpath** 時 **clean** 設為 `false`，則只會分析 XPath 查詢的結果。

## 網頁清理
{: #webpage-cleaning}

依預設，服務在進行分析之前，會先「清理」網頁。網頁清理會嘗試移除通常不要的內容，例如廣告及其他可能干擾頁面主要內容分析的文字。

若要停用網頁清理，請將 **clean** 參數設為 `false`。下列範例會停用網頁清理。

```bash
curl --user "apikey:{apikey}" \
"{url}/v1/analyze?version=2018-09-21" \
--request POST \
--header "Content-Type: application/json" \
--data '{
  "url": "http://newsroom.ibm.com/Guerbet-and-IBM-Watson-Health-Announce-Strategic-Partnership-for-Artificial-Intelligence-in-Medical-Imaging-Liver"
  "features": {
    "concepts": {}
  },
  "return_analyzed_text": true,
  "clean": false
}'
```
{: pre}


## 使用 XPath 分析網頁的特定元素
{: #xpath}

**xpath** 參數可讓您使用 XPath 查詢來分析網頁的特定部分。若要進一步瞭解 XPath，請查看下列資源。

  - [W3Schools XPath 指導教學](https://www.w3schools.com/xml/xpath_intro.asp)
  - [維基百科上的 XPath](https://wikipedia.org/wiki/XPath)

**xpath** 參數的行為取決於 **clean** 參數的值： 

  - **clean** = `true`（預設值）：在分析合併的文字之前，XPath 查詢的結果會附加到經清理的網頁文字。
  - **clean** = `false`：只會分析 XPath 查詢的結果。

### 將特定元素中的文字併入分析中
{: #analyze-cleaned-and-xpath}

依預設，**clean** 參數會設為 `true`，因此在分析合併的文字之前，XPath 查詢的結果會附加到換行字元之後經清理的網頁文字。如果您要在分析中併入原本可能因網頁清理而移除的元素，則此功能很有用。下列範例使用 **xpath** 參數，以將範例網頁的標題及子標題併入分析中。

**範例 *parameters.json* 檔案**
```json
{
  "url": "http://newsroom.ibm.com/Guerbet-and-IBM-Watson-Health-Announce-Strategic-Partnership-for-Artificial-Intelligence-in-Medical-Imaging-Liver",
  "features": {
    "concepts": {}
  },
  "return_analyzed_text": true,
  "xpath": "//div[@class='wd_title wd_language_left' or @class='wd_subtitle wd_language_left']"
}
```
{: codeblock}

**範例要求**
```bash
curl --user "apikey:{apikey}" \
"{url}/v1/analyze?version=2018-09-21" \
--request POST \
--header "Content-Type: application/json" \
--data @parameters.json
```
{: pre}


### 只分析特定元素中的文字
{: #analyze-xpath-results-only}

若只要分析 XPath 查詢的結果，請使用 **xpath** 參數，並將 **clean** 參數設為 `false`。下列範例只會分析範例網頁的標題和子標題。

**範例 *parameters.json* 檔案**
```json
{
  "url": "http://newsroom.ibm.com/Guerbet-and-IBM-Watson-Health-Announce-Strategic-Partnership-for-Artificial-Intelligence-in-Medical-Imaging-Liver",
  "features": {
    "concepts": {}
  },
  "return_analyzed_text": true,
  "xpath": "//div[@class='wd_title wd_language_left' or @class='wd_subtitle wd_language_left']",
  "clean": false
}
```
{: codeblock}

**範例要求**
```bash
curl --user "apikey:{apikey}" \
"{url}/v1/analyze?version=2018-09-21" \
--request POST \
--header "Content-Type: application/json" \
--data @parameters.json
```
{: pre}
