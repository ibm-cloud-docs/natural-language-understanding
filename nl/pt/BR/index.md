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

Categorize seu conteúdo usando uma hierarquia de classificação de cinco níveis. Visualize a lista completa de categorias [aqui](/docs/services/natural-language-understanding?topic=natural-language-understanding-categories-hierarchy). Por exemplo:

**Entrada**
> URL: "www.cnn.com"

**Resposta**
> /notícias </br>
> /arte e entretenimento </br>
> /filmes e tv/televisão </br>
> /notícias </br>
> /notícias internacionais

### Conceitos
{: #concepts}

Identifique conceitos de alto nível que não estejam necessariamente referenciados diretamente no texto. Por exemplo:

**Entrada**
> Texto: "O Natural Language Understanding usará processamento de linguagem natural para analisar texto".

**Resposta**
> Linguística </br>
> Processamento de linguagem natural </br>
> Natural language understanding

### Emoção
{: #emotion}

Analise a emoção transmitida por frases de destino específicas ou pelo documento como um todo. Também é possível ativar a
análise de emoção para entidades e palavras-chave que são automaticamente detectadas pelo serviço. Por exemplo:

**Entrada**
> texto: "Amo maçãs, mas detesto laranja". </br>
> Destinos: "maçãs" e "laranjas"

**Resposta**
> "maças": alegria </br>
> "Laranjas": raiva

### Entidades
{: #entities}

Localize pessoas, lugares, eventos e outros tipos de entidades mencionadas no seu conteúdo. Visualize a lista completa de tipos e subtipos de entidade
[aqui](/docs/services/natural-language-understanding?topic=natural-language-understanding-entity-type-systems). Por exemplo:

**Entrada**
> Texto: "A IBM é uma empresa de tecnologia multinacional americana sediada em Armonk, Nova York, Estados Unidos, com
operações em mais de 170 países".

**Resposta**
> IBM: empresa </br>
> Armonk: local </br>
> Nova Iorque: local </br>
> Estados Unidos: localização

### Palavras-chave
{: #keywords}

Procure seu conteúdo para palavras-chave relevantes. Por exemplo:

**Entrada**
>URL:
"[http://www-03.ibm.com/press/us/en/pressrelease/51493.wss](http://www-03.ibm.com/press/us/en/pressrelease/51493.wss)"

**Resposta**
>Aberto da Austrália </br>
>Equipe de tênis da Austrália </br>
>Analítica do IBM SlamTracker

### Metadados
{: #metadata}

Para entrada HTML e URL, obtenha o autor da página da web, o título da página e a data de publicação. Por exemplo:

**Entrada**
>URL: "https://www.ibm.com/blogs/think/2017/01/cognitive-grid/"

**Resposta**
>Autor: Stephen Callahan </br>
>Título: Girding the Grid with Cognitive Computing - Blog THINK </br>
>Data de publicação: 31 de janeiro de 2017

### Relações
{: #relations}

Reconhecer quando duas entidades estão relacionadas e identificar o tipo de relação. Por exemplo:

**Entrada**
>Texto: "O Prêmio Nobel em Física de 1921 foi concedido a Albert Einstein".

**Resposta**
>Relação "awardedTo" entre "Vencedor do Prêmio Nobel de Física" e "Albert Einstein" </br>
>Relação de "timeOf" entre "1921" e "concedido"

### Funções de semântica
{: #semantic-roles}

Analise sentenças no formato assunto-ação-objeto e identifique entidades e palavras-chave que sejam sujeitos ou
objetos de uma ação. Por exemplo:

**Entrada**
>Texto: "Em 2011, o Watson competiu no Jeopardy!"

**Resposta**
>Sujeito: Watson </br>
>Ação: competiu </br>
>Objeto: no Jeopardy

### Impressão
{: #sentiment}

Analise a impressão em relação às frases de destino específicas e o sentimento do documento como um todo. Também é possível
obter informações de impressão para entidades e palavras-chave detectadas ativando a opção de impressão para esses recursos. Por exemplo:

**Entrada**
>Texto: "Obrigado e tenha um bom dia!"

**Resposta**
>Impressão positiva (pontuação: 0,91)

## Idiomas suportados
{: #supported-languages}

Consulte a [Documentação de suporte a idioma](/docs/services/natural-language-understanding?topic=natural-language-understanding-language-support) para detalhes sobre os idiomas suportados no {{site.data.keyword.nlushort}}.
