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

# Sobre
{: #about}

Com o {{site.data.keyword.nlufull}}, os desenvolvedores podem analisar os recursos de semântica de entrada de texto,
incluindo as categorias, os conceitos, a emoção, as entidades, as palavras-chave, os metadados, as relações, as funções semânticas e a
impressão.
{: shortdesc}

## Recursos
{: #features}

Envie solicitações para a API com texto, HTML ou uma URL pública e especifique um ou mais dos seguintes recursos para
analisar:

### Categorias
{: #categories}

Categorize seu conteúdo usando uma hierarquia de classificação de cinco níveis. Visualize a lista completa de categorias [aqui](/docs/services/natural-language-understanding/categories.html). Por exemplo:

**Entrada**
> URL: "www.cnn.com"

**Resposta**
> /news </br>
> /art and entertainment </br>
> /movies and tv/television </br>
> /news </br>
> /international news

### Conceitos
{: #concepts}

Identifique conceitos de alto nível que não estejam necessariamente referenciados diretamente no texto. Por exemplo:

**Entrada**
> text: "Natural Language Understanding uses natural language processing to analyze text."

**Resposta**
> Linguistics </br>
> Natural language processing </br>
> Natural language understanding

### Emoção
{: #emotion}

Analise a emoção transmitida por frases de destino específicas ou pelo documento como um todo. Também é possível ativar a
análise de emoção para entidades e palavras-chave que são automaticamente detectadas pelo serviço. Por exemplo:

**Entrada**
> text: "I love apples, but I hate oranges." </br>
> targets: "apples", and "oranges"

**Resposta**
> "apples": joy </br>
> "oranges": anger

### Entidades
{: #entities}

Localize pessoas, lugares, eventos e outros tipos de entidades mencionadas no seu conteúdo. Visualize a lista completa de tipos e subtipos de entidade
[aqui](/docs/services/natural-language-understanding/entity-types.html). Por exemplo:

**Entrada**
> text: "IBM is an American multinational technology company headquartered in Armonk, New York, United States, with operations in over 170 countries."

**Resposta**
> IBM: Company </br>
> Armonk: Location </br>
> New York: Location </br>
> United States: Location

### Palavras-chave
{: #keywords}

Procure seu conteúdo para palavras-chave relevantes. Por exemplo:

**Entrada**
>url: "[http://www-03.ibm.com/press/us/en/pressrelease/51493.wss](http://www-03.ibm.com/press/us/en/pressrelease/51493.wss)"

**Resposta**
>Australian Open </br>
>Tennis Australia </br>
>IBM SlamTracker analytics

### Metadados
{: #metadata}

Para entrada HTML e URL, obtenha o autor da página da web, o título da página e a data de publicação. Por exemplo:

**Entrada**
>url: "https://www.ibm.com/blogs/think/2017/01/cognitive-grid/"

**Resposta**
>Author: Stephen Callahan </br>
>Title: Girding the Grid with Cognitive Computing - THINK Blog </br>
>Publication date: January 31, 2017

### Relações
{: #relations}

Reconhecer quando duas entidades estão relacionadas e identificar o tipo de relação. Por exemplo:

**Entrada**
>text: "The Nobel Prize in Physics 1921 was awarded to Albert Einstein."

**Resposta**
>"awardedTo" relation between "Noble Prize in Physics" and "Albert Einstein" </br>
>"timeOf" relation between "1921" and "awarded"

### Funções de semântica
{: #semantic-roles}

Analise sentenças no formato assunto-ação-objeto e identifique entidades e palavras-chave que sejam sujeitos ou
objetos de uma ação. Por exemplo:

**Entrada**
>text: "In 2011, Watson competed on Jeopardy!"

**Resposta**
>Subject: Watson </br>
>Action: competed </br>
>Object: on Jeopardy

### Impressão
{: #sentiment}

Analise a impressão em relação às frases de destino específicas e o sentimento do documento como um todo. Também é possível
obter informações de impressão para entidades e palavras-chave detectadas ativando a opção de impressão para esses recursos. Por exemplo:

**Entrada**
>text: "Thank you and have a nice day!"

**Resposta**
>Positive sentiment (score: 0.91)

## Idiomas suportados
{: #supported-languages}

Consulte a documentação de [Suporte ao idioma](/docs/services/natural-language-understanding/language-support.html) do
para obter detalhes sobre idiomas suportados no {{site.data.keyword.nlushort}}.

## Venda
{: #pricing}

Para obter informações de precificação, consulte o serviço do [{{site.data.keyword.nlushort}}](https://console.bluemix.net/catalog/services/natural-language-understanding) no catálogo {{site.data.keyword.cloud}}.
