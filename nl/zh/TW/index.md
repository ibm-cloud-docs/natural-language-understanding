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

# 關於
{: #about}

使用 {{site.data.keyword.nlufull}}，開發人員可以分析文字輸入的語意特性，包括種類、概念、情緒、實體、關鍵字、meta 資料、關係、語意角色及觀感。
{: shortdesc}

## 特性
{: #features}

使用文字、HTML 或公用 URL 將要求傳送至 API，並指定下列一個以上的特性進行分析：

### 種類
{: #categories}

使用五層分類階層來分類內容。請在[這裡](/docs/services/natural-language-understanding?topic=natural-language-understanding-categories-hierarchy)檢視完整的種類清單。例如：

**輸入**
> url: "www.cnn.com"

**回應**
> /news </br>
> /art and entertainment </br>
> /movies and tv/television </br>
> /news </br>
> /international news

### 概念
{: #concepts}

識別文字中不需要直接參照的高階概念。例如：

**輸入**
> text: "Natural Language Understanding uses natural language processing to analyze text."

**回應**
> Linguistics </br>
> Natural language processing </br>
> Natural language understanding

### 情緒
{: #emotion}

分析特定目標詞組或整個文件所傳達的情緒。您也可以針對服務自動偵測到的實體及關鍵字，啟用情緒分析。例如：

**輸入**
> text: "I love apples, but I hate oranges." </br>
> targets: "apples", and "oranges"

**回應**
> "apples": joy </br>
> "oranges": anger

### 實體
{: #entities}

尋找內容中提及的人員、位置、事件及其他類型的實體。請在[這裡](/docs/services/natural-language-understanding?topic=natural-language-understanding-entity-type-systems)檢視實體類型及子類型的完整清單。例如：

**輸入**
> text: "IBM is an American multinational technology company headquartered in Armonk, New York, United States, with operations in over 170 countries."

**回應**
> IBM: Company </br>
> Armonk: Location </br>
> New York: Location </br>
> United States: Location

### 關鍵字
{: #keywords}

搜尋相關關鍵字的內容。例如：

**輸入**
>url: "[http://www-03.ibm.com/press/us/en/pressrelease/51493.wss](http://www-03.ibm.com/press/us/en/pressrelease/51493.wss)"

**回應**
>Australian Open </br>
>Tennis Australia </br>
>IBM SlamTracker analytics

### meta 資料
{: #metadata}

針對 HTML 及 URL 輸入，取得網頁作者、頁面標題及發佈日期。例如：

**輸入**
>url: "https://www.ibm.com/blogs/think/2017/01/cognitive-grid/"

**回應**
>Author: Stephen Callahan </br>
>Title: Girding the Grid with Cognitive Computing - THINK Blog </br>
>Publication date: January 31, 2017

### 關係
{: #relations}

在兩個實體相關時辨識它們，並識別關係的類型。例如：

**輸入**
>text: "The Nobel Prize in Physics 1921 was awarded to Albert Einstein."

**回應**
>"awardedTo" relation between "Noble Prize in Physics" and "Albert Einstein" </br>
>"timeOf" relation between "1921" and "awarded"

### 語意角色
{: #semantic-roles}

將句子剖析成 subject-action-object 表單，並識別作為動作主題或物件的實體及關鍵字。例如：

**輸入**
>text: "In 2011, Watson competed on Jeopardy!"

**回應**
>Subject: Watson </br>
>Action: competed </br>
>Object: on Jeopardy

### 觀感
{: #sentiment}

分析特定目標詞組的觀感，以及整個文件的觀感。您也可以啟用那些特性的觀感選項，來取得偵測到的實體及關鍵字的觀感資訊。例如：

**輸入**
>text: "Thank you and have a nice day!"

**回應**
>Positive sentiment (score: 0.91)

## 支援的語言
{: #supported-languages}

如需 {{site.data.keyword.nlushort}} 中所支援語言的詳細資料，請參閱[語言支援文件](/docs/services/natural-language-understanding?topic=natural-language-understanding-language-support)。
