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

# Migrando do AlchemyLanguage

A partir de **07 de abril de 2017**, não será mais possível criar uma nova instância do AlchemyAPI no {{site.data.keyword.cloud}}. As instâncias de serviço existentes serão suportadas até **7 de março de 2018**. Para continuar usando os recursos do {{site.data.keyword.alchemylanguageshort}}, você precisará migrar seu código para {{site.data.keyword.nlushort}}.
{: shortdesc}

O {{site.data.keyword.nlushort}} oferece um modelo de precificação mais econômico e uma API consolidada que é muito mais fácil de usar. Os recursos existentes são aperfeiçoados para torná-los mais úteis e valiosos para as necessidades de nossos clientes. O {{site.data.keyword.nlushort}} torna mais fácil gerenciar sua marca, reunir inteligência de negócios e cluster para correspondência, ad-tech e recomendações.

## Visão geral das principais mudanças

- Nova sintaxe de solicitação de API: enviar solicitações para o terminal `/analyze`
- Nova estrutura de resposta (código que analisa a saída do {{site.data.keyword.alchemylanguageshort}} não funciona para a saída do {{site.data.keyword.nlushort}})
- JSON é o único formato de saída
- *Extração de texto* é ativada configurando o parâmetro `return_analyzed_text` para `true`
- *Microformatos* não são suportados
- *Extração de data* não é suportada (*Data de publicação* ainda é suportada no recurso *Metadados*)
- Opções de "quotations" para entidades não são suportadas
- "knowledgeGraph" não é suportado para conceitos, palavras-chave ou entidades
- Consultas de restrições visuais (usadas com o parâmetro `cquery`) não são suportadas
- Retornos de chamada de JSONP não são suportados
- *TypedRelations* de {{site.data.keyword.alchemylanguageshort}} são *Relações* em {{site.data.keyword.nlushort}}
- *Relações* de {{site.data.keyword.alchemylanguageshort}} são *Funções semânticas* em {{site.data.keyword.nlushort}}
- Tipos de entidade mudaram (consulte os novos tipos de entidade [aqui](/docs/services/natural-language-understanding/entity-types.html))
- As seguintes palavras foram digitadas incorretamente nos resultados de taxonomia do AlchemyLanguage. Elas foram corrigidas nos resultados das categorias do Natural Language Understanding.
  - `offence` -> `offense`
  - `civl` -> `civil`
  - `phyiscs` -> `physics`

## Etapas da migração

1. [Introdução](/docs/services/natural-language-understanding/getting-started.html) ao serviço do {{site.data.keyword.nlushort}}.
1. Se você usar modelos customizados do Watson Knowledge Studio, reimplemente-os em sua nova instância de serviço do {{site.data.keyword.nlushort}}. Siga as etapas para implementar os [anotadores baseados em regras](/docs/services/knowledge-studio/rule-annotator-model-use.html#wks_rule_publish) ou os [anotadores de aprendizado de máquina](/docs/services/knowledge-studio/publish-ml.html#wks_manlu)e selecione o serviço do {{site.data.keyword.nlushort}} como o destino para implementação.
1. Migre seu código.
    Se você usar os SDKs do Watson Developer Cloud para interagir com o {{site.data.keyword.alchemylanguageshort}}, você precisará mudar seu código de SDK. Clique nos seguintes links para visualizar exemplos de SDK do {{site.data.keyword.nlushort}} em GitHub:
    - [Node.js ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://github.com/watson-developer-cloud/node-sdk#natural-language-understanding){: new_window}
    - [Python ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://github.com/watson-developer-cloud/python-sdk/blob/master/examples/natural_language_understanding_v1.py){: new_window}
    - [Swift ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://github.com/watson-developer-cloud/swift-sdk#natural-language-understanding){: new_window}

Além disso, você precisa reconfigurar qualquer lógica em seu aplicativo que espere a saída das solicitações do {{site.data.keyword.alchemylanguageshort}}. Certifique-se de que seu código esteja ajustado para processar a nova estrutura de saída do {{site.data.keyword.nlushort}}.

### Os métodos do AlchemyLanguage e os recursos correspondentes do Natural Language Understanding
As solicitações do {{site.data.keyword.alchemylanguageshort}} mapeiam para o terminal `/analyze` do {{site.data.keyword.nlushort}}. As solicitações para `/analyze` são semelhantes às solicitações de Chamada combinada do {{site.data.keyword.alchemylanguageshort}}, mas a sintaxe é diferente e você é capaz de especificar opções como `limit` individualmente para cada recurso. POSTs para `/analyze` aceitam um corpo JSON que contém a entrada e os parâmetros para a solicitação e GETs para `/analyze` aceitam parâmetros de consulta que são análogos à sintaxe de parâmetro JSON.

| Método do {{site.data.keyword.alchemylanguageshort}} | Terminal do {{site.data.keyword.alchemylanguageshort}} | Recurso do {{site.data.keyword.nlushort}} |
|------------------------|--------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------|
| Autores | `/text/TextGetAuthors`<br/>`/url/URLGetAuthors` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#metadata">Metadados</a> |
| Conceitos | `/html/HTMLGetRankedConcepts`<br/>`/text/TextGetRankedConcepts`<br/>`/url/URLGetRankedConcepts` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#concepts">Conceitos</a> |
| Extração de data | `/html/HTMLExtractDates`<br/>`/text/TextExtractDates`<br/>`/url/URLExtractDates` | Não suportado |
| Análise de Emoção | `/html/HTMLGetEmotion`<br/>`/text/TextGetEmotion`<br/>`/url/URLGetEmotion` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#emotion">Emoção</a> |
| Emoção de destino | `/html/HTMLGetTargetedEmotion`<br/>`/text/TextGetTargetedEmotion`<br/>`/url/URLGetTargetedEmotion` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#emotion">Emoção</a> (usar a opção `targets`) |
| Entidades | `/html/HTMLGetRankedNamedEntities`<br/>`/text/TextGetRankedNamedEntities`<br/>`/url/URLGetRankedNamedEntities` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#entities">Entidades</a> |
| Detecção de feed | `/html/HTMLGetFeedLinks`<br/>`/url/URLGetFeedLinks` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#metadata">Metadados</a> |
| Palavras-chave | `/html/HTMLGetRankedKeywords`<br/>`/text/TextGetRankedKeywords`<br/>`/url/URLGetRankedKeywords` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#keywords">Palavras-chave</a> |
| Detecção de idioma | `/html/HTMLGetLanguage`<br/>`/text/TextGetLanguage`<br/>`/url/URLGetLanguage` | A detecção de idioma básico é grátis em cada solicitação. Metadados de idioma diferentes do código ISO não são retornados. |
| Microformatos | `/html/HTMLGetMicroformatData`<br/>`/url/URLGetMicroformatData` | Não suportado |
| Data de publicação | `/html/HTMLGetPubDate`<br/>`/url/URLGetPubDate` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#metadata">Metadados</a>
|
| Relações | `/html/HTMLGetRelations`<br/>`/text/TextGetRelations`<br/>`/url/URLGetRelations` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#semantic-roles">Funções semânticas</a> |
| Relações tipadas | `/html/HTMLGetTypedRelations`<br/>`/text/TextGetTypedRelations`<br/>`/url/URLGetTypedRelations` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#relations">Relações</a> |
| Análise de sentimentos | `/html/HTMLGetTextSentiment`<br/>`/text/TextGetTextSentiment`<br/>`/url/URLGetTextSentiment` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#sentiment">Impressão</a> |
| Impressão com destino | `/html/HTMLGetTargetedSentiment`<br/>`/text/TextGetTargetedSentiment`<br/>`/url/URLGetTargetedSentiment` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#sentiment">Impressão</a> (usar a opção `targets`) |
| Taxonomia | `/html/HTMLGetRankedTaxonomy`<br/>`/text/TextGetRankedTaxonomy`<br/>`/url/URLGetRankedTaxonomy` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#categories">Categorias</a> |
| Texto (limpo) | `/html/HTMLGetText`<br/>`/url/URLGetText` | Configure `return_analyzed_text` para `true` em qualquer solicitação válida para `/analyze` |
| Texto (bruto) | `/html/HTMLGetRawText`<br/>`/url/URLGetRawText` | Configure `return_analyzed_text` para `true` e `clean` para `false` em qualquer solicitação válida para `/analyze` |
| Extração de título | `/html/HTMLGetTitle`<br/>`/url/URLGetTitle` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#metadata">Metadados</a> |

Então, se você estiver fazendo essa chamada combinada:

```bash
curl -X POST \
-d "outputMode=json" \
-d "extract=entities,keywords" \
-d "sentiment=1" \
-d "limit=1" \
-d "url=https://www.ibm.com/us-en/" \
"https://gateway.watsonplatform.net/calls/url/URLGetCombinedData?apikey=$API_KEY"
```
{: pre}

agora seria semelhante a essa no {{site.data.keyword.nlushort}}:

```bash
curl -X POST \
-H "Content-Type: application/json" \
-u "{username}":"{password}" \
-d @parameters.json "https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze?version=2017-02-27"
```
{: pre}

Com esse parameters.json:

```json
{
  "url": "https://www.ibm.com/us-en/",
  "features": {
    "entities": {
      "sentiment": true,
      "limit": 1
    },
    "keywords": {
      "sentiment": true,
      "limit": 1
    }
  }
}
```
{: codeblock}

## Harmonização da entidade

Se você estava usando os modelos públicos do método TypedRelations do {{site.data.keyword.alchemylanguageshort}}, você precisará mudar qualquer código que espera os tipos de entidade desses modelos. A tabela a seguir mostra o mapeamento dos tipos de entidade TypedRelations para os tipos de entidade {{site.data.keyword.nlushort}}.

| Tipo de entidade TypedRelations | {{site.data.keyword.nlushort}} Tipo de entidade Relations |
|----------------------------|------------------------------------------------------|
| AGE | Age |
| ANIMAL | Animal |
| AWARD | Award |
| CARDINAL | Cardinal |
| DATE | Data |
| DEGREE | Degree |
| DISEASE | HealthCondition |
| DURATION | Duração |
| EMAIL | EmailAddress |
| EVENT | Evento |
| FACILITY | Facility |
| FOOD | Food |
| GEOLOGICALOBJ | GeographicFeature |
| GPE | GeopoliticalEntity |
| LAW | Law |
| LOCALIDADE | Local |
| MEASURE | Medida |
| MONEY | Money |
| ORDINAL | Ordinal |
| ORGAN | Anatomia |
| ORGANIZATION | Organização |
| PEOPLE | Pessoa |
| PERCENT | Percentual |
| PERSONPEOPLE | Pessoa |
| PERSON | Pessoa |
| PHONE | Telefone |
| PLANT | Plant |
| PRODUCT | Produto |
| SUBSTANCE | Substance |
| TICKER | Ticker |
| TIME | Horário |
| TITLEWORK | TitleWork |
| VEHICLE | Vehicle |
| WEAPON | Weapon |
| WEATHER | Weather |
| WEB | Web |
| EVENT_AWARD | Award |
| EVENT_BUSINESS | EventBusiness |
| EVENT_COMMUNICATION | EventCommunication |
| EVENT_CRIME | Crime |
| EVENT_CUSTODY | EventCustody |
| EVENT_DEMONSTRATION | EventDemonstration |
| EVENT_DISASTER | NaturalEvent |
| EVENT_EDUCATION | EventEducation |
| EVENT_ELECTION | EventElection |
| EVENT_LEGAL | EventLegal |
| EVENT_LEGISLATION | EventLegislation |
| EVENT_MEETING | EventMeeting |
| EVENT_GATHERING | EventGathering |
| EVENT_PERFORMANCE | EventPerformance |
| EVENT_PERSONNEL | EventPersonnel |
| EVENT_SPORTS | SportingEvent |
| EVENT_VIOLENCE | EventViolence |
| EVENT | Evento |
