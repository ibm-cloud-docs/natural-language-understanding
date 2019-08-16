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


# 웹 페이지 분석
{: #analyzing-webpages}

{{site.data.keyword.nlushort}}을 사용하면 프로그래밍 방식으로 웹 페이지의 텍스트를 분석할 수 있습니다. API 요청에서 원시 HTML 또는 공개적으로 액세스 가능한 URL을 제공하면 서비스에서 뉴스 기사나 블로그 게시물의 텍스트와 같은 페이지의 기본 컨텐츠 분석에 초점을 맞춥니다.

**작동 방식:**

1. **url** 매개변수를 사용하여 공개적으로 액세스 가능한 URL을 지정하거나 **html** 매개변수로 원시 HTML을 보내십시오.
2. 기본적으로 서비스에서는 광고와 같이 일반적으로 원하지 않는 텍스트를 제거하기 위해 웹 페이지를 [정리](#webpage-cleaning)합니다.
3. **xpath** 매개변수를 사용하여 [XPath 조회](#xpath)를 지정하는 경우 서비스에서 조회를 사용하여 분석에 포함할 페이지의 특정 요소를 선택합니다. **xpath**를 사용할 때 **clean**을 `false`로 설정하는 경우 XPath 조회 결과만 분석합니다.

## 웹 페이지 정리
{: #webpage-cleaning}

기본적으로 서비스에서 웹 페이지를 분석하기 전에 "정리"합니다. 웹 페이지 정리에서는 페이지의 기본 컨텐츠를 분석하는 데 방해가 될 수 있는 광고나 기타 텍스트 등의 일반적으로 원하지 않는 컨텐츠를 제거합니다.

웹 페이지 정리를 사용 안함으로 설정하려면 **clean** 매개변수를 `false`로 설정하십시오. 다음 예에서는 웹 페이지 정리를 사용 안함으로 설정합니다.

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


## XPath로 웹 페이지의 특정 요소 분석
{: #xpath}

**xpath** 매개변수를 사용하면 XPath 조회를 사용하여 웹 페이지의 특정 경로를 분석할 수 있습니다. XPath에 관해 자세히 알아보려면 다음 리소스를 확인하십시오.

  - [W3Schools XPath 튜토리얼](https://www.w3schools.com/xml/xpath_intro.asp)
  - [위키피디아의 XPath](https://wikipedia.org/wiki/XPath)

**xpath** 매개변수의 동작은 **clean** 매개변수의 값에 따라 달라집니다. 

  - **clean** = `true`(기본값): 결합된 텍스트를 분석하기 전에 XPath 조회 결과를 정리된 웹 페이지 텍스트에 추가합니다.
  - **clean** = `false`: XPath 조회 결과만 분석합니다.

### 분석에 특정 요소의 텍스트 포함
{: #analyze-cleaned-and-xpath}

기본적으로 **clean** 매개변수는 `true`로 설정되며 XPath 조회 결과는 결합된 텍스트를 분석하기 전에 정리된 웹 페이지의 줄 바꾸기 문자 다음에 추가됩니다. 그러면 웹 페이지 정리에서 제거하는 요소를 분석에 포함하려는 경우 유용합니다. 다음 예에서는 **xpath** 매개변수를 사용하여 예제 웹 페이지의 제목과 부제를 분석에 포함시킵니다.

**예제 *parameters.json* 파일**
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

**요청 예제**
```bash
curl --user "apikey:{apikey}" \
"{url}/v1/analyze?version=2018-09-21" \
--request POST \
--header "Content-Type: application/json" \
--data @parameters.json
```
{: pre}


### 특정 요소의 텍스트만 분석
{: #analyze-xpath-results-only}

XPath 조회의 결과만 분석하려면 **xpath** 매개변수를 사용하고 **clean** 매개변수를 `false`로 설정하십시오. 다음 예에서는 예제 웹 페이지의 제목과 부제만 분석합니다.

**예제 *parameters.json* 파일**
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

**요청 예제**
```bash
curl --user "apikey:{apikey}" \
"{url}/v1/analyze?version=2018-09-21" \
--request POST \
--header "Content-Type: application/json" \
--data @parameters.json
```
{: pre}
