---

copyright:
  years: 2015, 2017
lastupdated: "2017-11-28"

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

# 关于
{: #about}

通过 {{site.data.keyword.nlufull}}，开发者可以分析文本输入的语义特征，包括类别、概念、情绪、实体、关键字、元数据、关系、语义角色和观点。
{: shortdesc}

## 特征
{: #features}

向 API 发送包含文本、HTML 或公共 URL 的请求，并指定要分析的以下一个或多个特征：

### 类别
{: #categories}

使用五级分类层次结构对内容进行分类。在[此处](/docs/services/natural-language-understanding/categories.html)查看完整的类别列表。例如：

**输入**
> url: "www.cnn.com"

**响应**
> /news </br>
> /art and entertainment </br>
> /movies and tv/television </br>
> /news </br>
> /international news

### 概念
{: #concepts}

识别文本中不一定直接引用的高级别概念。例如：

**输入**
> text: "Natural Language Understanding uses natural language processing to analyze text."

**响应**
> Linguistics </br>
> Natural language processing </br>
> Natural language understanding

### 情绪
{: #emotion}

分析通过特定目标短语或整个文档来传达的情绪。您还可以对服务自动检测到的实体和关键字启用情绪分析。例如：

**输入**
> text: "I love apples, but I hate oranges." </br>
> targets: "apples", and "oranges"

**响应**
> "apples": joy </br>
> "oranges": anger

### 实体
{: #entities}

查找内容中提及的人员、场所、事件和其他类型的实体。在[此处](/docs/services/natural-language-understanding/entity-types.html)查看实体类型和子类型的完整列表。例如：

**输入**
> text: "IBM is an American multinational technology company headquartered in Armonk, New York, United States, with operations in over 170 countries."

**响应**
> IBM：公司</br>
> Armonk：位置</br>
> New York：位置</br>
> United States：位置

### 关键字
{: #keywords}

在内容中搜索相关关键字。例如：

**输入**
>url: "[http://www-03.ibm.com/press/us/en/pressrelease/51493.wss](http://www-03.ibm.com/press/us/en/pressrelease/51493.wss)"

**响应**
>Australian Open </br>
>Tennis Australia </br>
>IBM SlamTracker analytics

### 元数据
{: #metadata}

对于 HTML 和 URL 输入，获取 Web 页面的作者、页面标题和发布日期。例如：

**输入**
>url: "https://www.ibm.com/blogs/think/2017/01/cognitive-grid/"

**响应**
>作者：Stephen Callahan </br>
>标题：Girding the Grid with Cognitive Computing - THINK Blog </br>
>发布日期：January 31, 2017

### 关系
{: #relations}

识别两个实体何时相关，并确定关系的类型。例如：

**输入**
>text: "The Nobel Prize in Physics 1921 was awarded to Albert Einstein."

**响应**
>“Noble Prize in Physics”和“Albert Einstein”之间有“awardedTo”关系</br>
>“1921”和“awarded”之间有“timeOf”关系

### 语义角色
{: #semantic-roles}

将句子解析为“主语-动作-宾语”形式，并识别作为动作的主语或宾语的实体和关键字。例如：

**输入**
>text: "In 2011, Watson competed on Jeopardy!"

**响应**
>主语：Watson</br>
>动作：competed</br>
>宾语：on Jeopardy

### 观点
{: #sentiment}

针对特定目标短语来分析观点以及分析整个文档的观点。您还可以通过启用这些特征的观点选项来获取检测到的实体和关键字的观点信息。例如：

**输入**
>text: "Thank you and have a nice day!"

**响应**
>正面观点（得分：0.91）

## 支持的语言
{: #supported-languages}

有关 {{site.data.keyword.nlushort}} 中支持的语言的详细信息，请参阅[语言支持文档](/docs/services/natural-language-understanding/language-support.html)。

## 定价
{: #pricing}

有关定价信息，请参阅 {{site.data.keyword.cloud}}“目录”中的 [{{site.data.keyword.nlushort}} 服务](https://console.bluemix.net/catalog/services/natural-language-understanding)。
