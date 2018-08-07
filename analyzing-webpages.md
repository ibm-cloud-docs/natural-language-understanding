---

copyright:
  years: 2015, 2018
lastupdated: "2018-08-07"

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


# Analyzing webpages
{: #analyzing-webpages}

{{site.data.keyword.nlushort}} enables you to analyze text from webpages programmatically. When you provide raw HTML or a publicly accessible URL in your API request, the service attempts to focus the analysis on the main content of the page, such as the text from a news article or blog post.

**How it works:**

1. Specify a publicly accessible URL with the **url** parameter, or send raw HTML in the **html** parameter.
2. By default, the service [cleans](#webpage-cleaning) the webpage to remove generally unwanted text such as advertisements.
3. If you specify an [XPath query](#xpath) with the **xpath** parameter, the service uses the query to select specific elements of the page to include in the analysis. If **clean** is set to `false` when you use **xpath**, only the result of the XPath query will be analyzed.

## Webpage cleaning
{: #webpage-cleaning}

By default, the service "cleans" webpages before they are analyzed. Webpage cleaning attempts to remove generally unwanted content such as advertisements and other text that might interfere with analyzing the main content of the page.

To disable webpage cleaning, set the **clean** parameter to `false`. The following example disables webpage cleaning.

```bash
curl --user "{username}:{password}" \
"{url}/v1/analyze?version=2018-03-16" \
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


## Analyzing specific elements of a webpage with XPath
{: #xpath}

The **xpath** parameter enables you to use an XPath query to analyze specific parts of a webpage. To learn more about XPath, check out the following resources.

  - [W3Schools XPath tutorial](https://www.w3schools.com/xml/xpath_intro.asp)
  - [XPath on Wikipedia](https://wikipedia.org/wiki/XPath)

The behavior of the **xpath** parameter depends on the value of the **clean** parameter: 

  - **clean** = `true` (default): Results of the XPath query will be appended to the cleaned webpage text before the combined text is analyzed.
  - **clean** = `false`: Only the results of the XPath query will be analyzed.

### Including text from specific elements in the analysis
{: #analyze-cleaned-and-xpath}

By default, the **clean** parameter is set to `true`, and results of an XPath query are appended to the cleaned webpage text after a newline character before the combined text is analyzed. This can be useful if you want to include elements in the analysis that would otherwise be removed by webpage cleaning. The following example uses the **xpath** parameter to include the title and subtitle of the example webpage in the analysis.

**Example *parameters.json* file**
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

**Example request**
```bash
curl --user "{username}:{password}" \
"{url}/v1/analyze?version=2018-03-16" \
--request POST \
--header "Content-Type: application/json" \
--data @parameters.json
```
{: pre}


### Analyzing text from specific elements only
{: #analyze-xpath-results-only}

To analyze only the result of an XPath query, use the **xpath** parameter and set the **clean** parameter to `false`. The following example analyzes only the title and subtitle of the example webpage.

**Example *parameters.json* file**
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

**Example request**
```bash
curl --user "{username}:{password}" \
"{url}/v1/analyze?version=2018-03-16" \
--request POST \
--header "Content-Type: application/json" \
--data @parameters.json
```
{: pre}