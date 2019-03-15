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


# 分析 Web 页面
{: #analyzing-webpages}

利用 {{site.data.keyword.nlushort}} 可以通过编程方式分析 Web 页面中的文本。在 API 请求中提供原始 HTML 或可公开访问的 URL 时，服务会尝试将分析的重点放在页面的主内容上，例如来自新闻文章或博客帖子的文本。

**工作方式：**

1. 使用 **url** 参数指定可公开访问的 URL，或在 **html** 参数中发送原始 HTML。
2. 缺省情况下，该服务会[清除](#webpage-cleaning) Web 页面以移除通常不需要的文本，如广告。
3. 如果使用 **xpath** 参数指定 [XPath 查询](#xpath)，那么服务将使用该查询来选择要包含在分析中的页面的特定元素。如果在使用 **xpath** 时将 **clean** 设置为 `false`，那么将仅分析 XPath 查询的结果。

## Web 页面清理
{: #webpage-cleaning}

缺省情况下，服务会先“清理”Web 页面，然后再对其进行分析。Web 页面清理会尝试除去通常不需要的内容（例如广告），以及可能会影响分析页面主要内容的其他文本。

要禁用 Web 页面清理，请将 **clean** 参数设置为 `false`。以下示例禁用了 Web 页面清理。

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


## 使用 XPath 分析 Web 页面的特定元素
{: #xpath}

利用 **xpath** 参数，您可以使用 XPath 查询来分析 Web 页面的特定部分。要了解有关 XPath 的更多信息，请查看以下资源。

  - [W3Schools XPath 教程](https://www.w3schools.com/xml/xpath_intro.asp)
  - [Wikipedia 上的 XPath](https://wikipedia.org/wiki/XPath)

**xpath** 参数的行为取决于 **clean** 参数的值： 

  - **clean** = `true`（缺省值）：在分析组合文本之前，会将 XPath 查询的结果附加到已清理的 Web 页面文本。
  - **clean** = `false`：仅分析 XPath 查询的结果。

### 在分析中包含特定元素的文本
{: #analyze-cleaned-and-xpath}

缺省情况下，**clean** 参数设置为 `true`，并且在分析合并文本之前，会将 XPath 查询的结果附加到已清理的 Web 页面文本中的换行符之后。如果要在分析中包含本来会被 Web 页面清理除去的元素，这会非常有用。以下示例使用 **xpath** 参数在分析中包含示例 Web 页面的标题和子标题。

**示例 *parameters.json* 文件**
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

**示例请求**
```bash
curl --user "apikey:{apikey}" \
"{url}/v1/analyze?version=2018-09-21" \
--request POST \
--header "Content-Type: application/json" \
--data @parameters.json
```
{: pre}


### 仅分析来自特定元素的文本
{: #analyze-xpath-results-only}

要仅分析 XPath 查询的结果，请使用 **xpath** 参数并将 **clean** 参数设置为 `false`。以下示例仅分析示例 Web 页面的标题和子标题。

**示例 *parameters.json* 文件**
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

**示例请求**
```bash
curl --user "apikey:{apikey}" \
"{url}/v1/analyze?version=2018-09-21" \
--request POST \
--header "Content-Type: application/json" \
--data @parameters.json
```
{: pre}
