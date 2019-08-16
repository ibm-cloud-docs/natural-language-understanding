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

# 製品について
{: #about}

{{site.data.keyword.nlufull}} を使用すれば、開発者は、テキスト入力のセマンティック・フィーチャー (カテゴリー、概念、感情、エンティティー、キーワード、メタデータ、関係、意味役割、評判など) を分析できます。
{: shortdesc}

## フィーチャー
{: #features}

テキスト、HTML、またはパブリック URL を使用して要求を API に送信し、分析する以下の 1 つ以上のフィーチャーを指定します。

### カテゴリー
{: #categories}

5 つのレベルの分類階層を使用してコンテンツをカテゴリー化します。 カテゴリーの全リストについては[こちら](/docs/services/natural-language-understanding?topic=natural-language-understanding-categories-hierarchy)を参照してください。 以下に例を示します。

**入力**
> url: "www.cnn.com"

**応答**
> /news </br>
> /art and entertainment </br>
> /movies and tv/television </br>
> /news </br>
> /international news

### 概念
{: #concepts}

テキスト内で必ずしも直接言及されないおおまかな概念を識別します。 以下に例を示します。

**入力**
> text: "Natural Language Understanding uses natural language processing to analyze text."

**応答**
> Linguistics </br>
> Natural language processing </br>
> Natural language understanding

### 感情
{: #emotion}

特定の対象となる句で、または文書全体で伝えられる感情を分析します。 サービスによって自動的に検出されるエンティティーとキーワードについて感情分析を有効にすることもできます。 以下に例を示します。

**入力**
> text: "I love apples, but I hate oranges." </br>
> targets: "apples", and "oranges"

**応答**
> "apples": joy </br>
> "oranges": anger

### エンティティー
{: #entities}

コンテンツ内で言及されている人、場所、イベント、およびその他のタイプのエンティティーを検出します。 エンティティーのタイプとサブタイプの完全なリストについては、[こちら](/docs/services/natural-language-understanding?topic=natural-language-understanding-entity-type-systems)を参照してください。 以下に例を示します。

**入力**
> text: "IBM is an American multinational technology company headquartered in Armonk, New York, United States, with operations in over 170 countries."

**応答**
> IBM: Company </br>
> Armonk: Location </br>
> New York: Location </br>
> United States: Location

### キーワード
{: #keywords}

コンテンツで関連キーワードを検索します。 以下に例を示します。

**入力**
>url: "[http://www-03.ibm.com/press/us/en/pressrelease/51493.wss](http://www-03.ibm.com/press/us/en/pressrelease/51493.wss)"

**応答**
>Australian Open </br>
>Tennis Australia </br>
>IBM SlamTracker analytics

### メタデータ
{: #metadata}

HTML 入力および URL 入力の場合に、Web ページの作成者、ページ・タイトル、および公開日を取得します。 以下に例を示します。

**入力**
>url: "https://www.ibm.com/blogs/think/2017/01/cognitive-grid/"

**応答**
>Author: Stephen Callahan </br>
>Title: Girding the Grid with Cognitive Computing - THINK Blog </br>
>Publication date: January 31, 2017

### 関係
{: #relations}

2 つのエンティティーが関係している場合にそれを認識し、関係のタイプを識別します。 以下に例を示します。

**入力**
>text: "The Nobel Prize in Physics 1921 was awarded to Albert Einstein."

**応答**
>"awardedTo" relation between "Noble Prize in Physics" and "Albert Einstein" </br>
>"timeOf" relation between "1921" and "awarded"

### 意味役割
{: #semantic-roles}

文を subject-action-object の形式に解析し、アクションの主体または対象であるエンティティーとキーワードを識別します。 以下に例を示します。

**入力**
>text: "In 2011, Watson competed on Jeopardy!"

**応答**
>Subject: Watson </br>
>Action: competed </br>
>Object: on Jeopardy

### 評判
{: #sentiment}

特定の対象となる句についての評判、および文書全体の評判を分析します。 検出されたエンティティーとキーワードの評判情報を取得することもできます。そのためには、これらのフィーチャーの評判オプションを有効にします。 以下に例を示します。

**入力**
>text: "Thank you and have a nice day!"

**応答**
>Positive sentiment (score: 0.91)

## サポート対象言語
{: #supported-languages}

{{site.data.keyword.nlushort}} でサポートされる言語について詳しくは、[言語サポートの資料](/docs/services/natural-language-understanding?topic=natural-language-understanding-language-support)を参照してください。
