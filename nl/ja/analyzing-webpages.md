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


# Web ページの分析
{: #analyzing-webpages}

{{site.data.keyword.nlushort}} では、Web ページのテキストをプログラムで分析できます。 生の HTML または公開 URL を API リクエストに指定すると、このサービスはそのページのメイン・コンテンツ (ニュース記事やブログ記事のテキストなど) を分析のターゲットにしようとします。

**実行方法:**

1. 公開 URL を **url** パラメーターに指定するか、または生 HTML を **html** パラメーターで送信します。
2. デフォルトでは、サービスは、一般に不要なテキスト (広告など) を取り除くために Web ページを[クリーニング](#webpage-cleaning)します。
3. [XPath クエリー](#xpath)を **xpath** パラメーターに指定すると、サービスは、そのクエリーを使用して、分析に含めるページの特定のエレメントを選択します。 **clean** が `false` に設定されている場合に **xpath** を使用すると、XPath クエリーの結果のみが分析されます。

## Web ページのクリーニング
{: #webpage-cleaning}

デフォルトでは、サービスは Web ページを分析する前にそのページを「クリーニング」します。 Web ページ・クリーニングでは、一般に不要なコンテンツ (広告など) や、ページのメイン・コンテンツの分析の妨げとなる可能性のあるその他のテキストの削除が試行されます。

Web ページ・クリーニングを無効にするには、**clean** パラメーターを `false` に設定します。 次の例では、Web ページ・クリーニングを無効にしています。

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


## XPath を使用した Web ページの特定エレメントの分析
{: #xpath}

**xpath** パラメーターで XPath クエリーを使用することで、Web ページの特定部分を分析できます。 XPath の詳細については、以下の参照資料を参照してください。

  - [W3Schools XPath チュートリアル](https://www.w3schools.com/xml/xpath_intro.asp)
  - [XPath (Wikipedia)](https://wikipedia.org/wiki/XPath)

**xpath** パラメーターの動作は、**clean** パラメーターの値に応じて次のように異なります。 

  - **clean** = `true` (デフォルト): クリーニングされた Web ページ・テキストに XPath クエリーの結果が付加された後に、その結合テキストが分析されます。
  - **clean** = `false`: XPath クエリーの結果のみが分析されます。

### 特定エレメントのテキストを分析対象に含める
{: #analyze-cleaned-and-xpath}

デフォルトでは **clean** パラメーターは `true` に設定されるので、クリーニングされた Web ページ・テキストに改行文字を挟んで XPath クエリーの結果が付加された後に、その結合テキストが分析されます。 これは、Web ページ・クリーニングで削除されるエレメントを分析対象に含めたい場合に便利です。 次の例では、**xpath** パラメーターを使用して Web ページ例のタイトルとサブタイトルを分析対象に含めています。

***parameters.json* ファイルの例**
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

**要求の例**
```bash
curl --user "apikey:{apikey}" \
"{url}/v1/analyze?version=2018-09-21" \
--request POST \
--header "Content-Type: application/json" \
--data @parameters.json
```
{: pre}


### 特定エレメントのテキストのみを分析する
{: #analyze-xpath-results-only}

XPath クエリーの結果のみを分析するには、**xpath** パラメーターを使用し、**clean** パラメーターを `false` に設定します。 次の例では、Web ページ例のタイトルとサブタイトルだけが分析されます。

***parameters.json* ファイルの例**
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

**要求の例**
```bash
curl --user "apikey:{apikey}" \
"{url}/v1/analyze?version=2018-09-21" \
--request POST \
--header "Content-Type: application/json" \
--data @parameters.json
```
{: pre}
