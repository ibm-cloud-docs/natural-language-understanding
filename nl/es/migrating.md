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

# Migración desde AlchemyLanguage

A partir del **7 de abril de 2017**, ya no será posible crear una nueva instancia de AlchemyAPI en {{site.data.keyword.cloud}}. Las instancias de servicio existentes se admitirán hasta el **7 de marzo de 2018**. Para continuar utilizando las características de {{site.data.keyword.alchemylanguageshort}}, deberá migrar su código a {{site.data.keyword.nlushort}}.
{: shortdesc}

{{site.data.keyword.nlushort}} ofrece un modelo de precios más económicos y una API unificada que es mucho más fácil de utilizar. Las características existentes se han simplificado para hacerlas más útiles y valiosas para las necesidades de nuestros clientes. {{site.data.keyword.nlushort}} facilita la gestión de la marca, la recopilación de inteligencia empresarial y la agrupación en clúster para las coincidencias, la tecnología publicitaria y las recomendaciones.

## Visión general de los cambios más importantes

- Nueva sintaxis de solicitud de API: enviar solicitudes al punto final `/analyze`
- Nueva estructura de respuesta (el código que analiza la salida de {{site.data.keyword.alchemylanguageshort}} no funciona para la salida de {{site.data.keyword.nlushort}})
- JSON es el único formato de salida
- La *extracción de texto* se habilita definiendo el parámetro `return_analyzed_text` en `true`
- No se admiten los *microformatos*
- No se admite la *extracción de fechas* (la *fecha de publicación* todavía se admite en la característica *Metadatos*)
- No se admiten las opciones de "quotations" para entidades
- "knowledgeGraph" no se admite para conceptos, palabras clave o entidades
- No se admiten las consultas de restricciones visuales (utilizadas con el parámetro `cquery`)
- No se admiten las devoluciones de llamada JSONP
- Las *relaciones con tipos* de {{site.data.keyword.alchemylanguageshort}} son *Relaciones* en {{site.data.keyword.nlushort}}
- Las *relaciones* de {{site.data.keyword.alchemylanguageshort}} son *Roles semánticos* en {{site.data.keyword.nlushort}}
- Los tipos de entidad han cambiado (consulte los nuevos tipos de entidad [aquí](/docs/services/natural-language-understanding/entity-types.html))
- Las siguientes palabras estaban mal escritas en los resultados de taxonomía de AlchemyLanguage. Se han corregido en los resultados de las categorías de Natural Language Understanding.
  - `offence` -> `offense`
  - `civl` -> `civil`
  - `phyiscs` -> `physics`

## Pasos de la migración

1. [Empiece a trabajar](/docs/services/natural-language-understanding/getting-started.html) con el servicio {{site.data.keyword.nlushort}}.
1. Si utiliza modelos personalizados de Watson Knowledge Studio, vuelva a desplegarlos en la nueva instancia de servicio de {{site.data.keyword.nlushort}}. Siga los pasos para desplegar [anotadores basados en reglas](/docs/services/knowledge-studio/rule-annotator-model-use.html#wks_rule_publish) o [anotadores de aprendizaje de máquina](/docs/services/knowledge-studio/publish-ml.html#wks_manlu) y seleccione el servicio {{site.data.keyword.nlushort}} como destino para el despliegue.
1. Migre el código.
    Si utiliza los SDK de Watson Developer Cloud para interactuar con {{site.data.keyword.alchemylanguageshort}}, debe cambiar el código del SDK. Pulse los enlaces siguientes para ver ejemplos de SDK de {{site.data.keyword.nlushort}} en GitHub:
    - [Node.js ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://github.com/watson-developer-cloud/node-sdk#natural-language-understanding){: new_window}
    - [Python ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://github.com/watson-developer-cloud/python-sdk/blob/master/examples/natural_language_understanding_v1.py){: new_window}
    - [Swift ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://github.com/watson-developer-cloud/swift-sdk#natural-language-understanding){: new_window}

Además, debe volver a configurar cualquier lógica en la aplicación que espere la salida de las solicitudes de {{site.data.keyword.alchemylanguageshort}}. Asegúrese de que el código esté ajustado para procesar la nueva estructura de salida de {{site.data.keyword.nlushort}}.

### Métodos de AlchemyLanguage y características de Natural Language Understanding correspondientes
Las solicitudes de {{site.data.keyword.alchemylanguageshort}} se correlacionan con el punto final `/analyze` de {{site.data.keyword.nlushort}}. Las solicitudes a `/analyze` son similares a las solicitudes de llamada combinada de {{site.data.keyword.alchemylanguageshort}}, pero la sintaxis es diferente y se pueden especificar opciones como `limit` de forma individual para cada característica. Las solicitudes POST a `/analyze` aceptan un cuerpo JSON que contiene la entrada y los parámetros de la solicitud, y las solicitudes GET a `/analyze` aceptan parámetros de consulta que son análogos a la sintaxis de parámetro JSON.

| Método {{site.data.keyword.alchemylanguageshort}} | Punto final de {{site.data.keyword.alchemylanguageshort}} | Característica de {{site.data.keyword.nlushort}} |
|------------------------|--------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------|
| Autores | `/text/TextGetAuthors`<br/>`/url/URLGetAuthors` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#metadata">Metadatos</a> |
| Conceptos | `/html/HTMLGetRankedConcepts`<br/>`/text/TextGetRankedConcepts`<br/>`/url/URLGetRankedConcepts` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#concepts">Conceptos</a> |
| Extracción de fechas | `/html/HTMLExtractDates`<br/>`/text/TextExtractDates`<br/>`/url/URLExtractDates` | No se da soporte |
| Análisis de emociones | `/html/HTMLGetEmotion`<br/>`/text/TextGetEmotion`<br/>`/url/URLGetEmotion` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#emotion">Emoción</a> |
| Emoción con destino | `/html/HTMLGetTargetedEmotion`<br/>`/text/TextGetTargetedEmotion`<br/>`/url/URLGetTargetedEmotion` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#emotion">Emoción</a> (utilice la opción `targets`) |
| Entidades | `/html/HTMLGetRankedNamedEntities`<br/>`/text/TextGetRankedNamedEntities`<br/>`/url/URLGetRankedNamedEntities` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#entities">Entidades</a> |
| Detección de canales de información | `/html/HTMLGetFeedLinks`<br/>`/url/URLGetFeedLinks` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#metadata">Metadatos</a> |
| Palabras clave | `/html/HTMLGetRankedKeywords`<br/>`/text/TextGetRankedKeywords`<br/>`/url/URLGetRankedKeywords` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#keywords">Palabras clave</a> |
| Detección de idioma | `/html/HTMLGetLanguage`<br/>`/text/TextGetLanguage`<br/>`/url/URLGetLanguage` | La detección de idioma básica es gratuita en todas las solicitudes. No se devuelven metadatos de idioma que no sean el código ISO. |
| Microformatos | `/html/HTMLGetMicroformatData`<br/>`/url/URLGetMicroformatData` | No se da soporte |
| Fecha de publicación | `/html/HTMLGetPubDate`<br/>`/url/URLGetPubDate` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#metadata">Metadatos</a> |
| Relaciones | `/html/HTMLGetRelations`<br/>`/text/TextGetRelations`<br/>`/url/URLGetRelations` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#semantic-roles">Roles semánticos</a> |
| Relaciones con tipos | `/html/HTMLGetTypedRelations`<br/>`/text/TextGetTypedRelations`<br/>`/url/URLGetTypedRelations` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#relations">Relaciones</a> |
| Análisis de sentimiento | `/html/HTMLGetTextSentiment`<br/>`/text/TextGetTextSentiment`<br/>`/url/URLGetTextSentiment` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#sentiment">Sentimiento</a> |
| Sentimiento con destino | `/html/HTMLGetTargetedSentiment`<br/>`/text/TextGetTargetedSentiment`<br/>`/url/URLGetTargetedSentiment` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#sentiment">Sentimiento</a> (utilice la opción `targets`) |
| Taxonomía | `/html/HTMLGetRankedTaxonomy`<br/>`/text/TextGetRankedTaxonomy`<br/>`/url/URLGetRankedTaxonomy` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#categories">Categorías</a> |
| Texto (limpio) | `/html/HTMLGetText`<br/>`/url/URLGetText` | Defina `return_analyzed_text` en `true` en cualquier solicitud válida a `/analyze` |
| Texto (sin procesar) | `/html/HTMLGetRawText`<br/>`/url/URLGetRawText` | Defina `return_analyzed_text` en `true` y `clean` en `false` en cualquier solicitud válida a `/analyze` |
| Extracción de título | `/html/HTMLGetTitle`<br/>`/url/URLGetTitle` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#metadata">Metadatos</a> |

Así, si realiza esta llamada combinada:

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

ahora tendrá este aspecto en {{site.data.keyword.nlushort}}:

```bash
curl -X POST \
-H "Content-Type: application/json" \
-u "{username}":"{password}" \
-d @parameters.json "https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze?version=2017-02-27"
```
{: pre}

Con este parameters.json:

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

## Armonización de entidades

Si ha estado utilizando los modelos públicos del método de relaciones con tipos de {{site.data.keyword.alchemylanguageshort}}, deberá cambiar cualquier código que espere los tipos de entidad de dichos modelos. La tabla siguiente muestra la correlación de los tipos de entidad de relaciones con tipos con los tipos de entidad de {{site.data.keyword.nlushort}}.

| Tipo de entidad de relaciones con tipos | Tipo de entidad de relaciones de {{site.data.keyword.nlushort}} |
|----------------------------|------------------------------------------------------|
| AGE | Age |
| ANIMAL | Animal |
| AWARD | Award |
| CARDINAL | Cardinal |
| DATE | Date |
| DEGREE | Degree |
| DISEASE | HealthCondition |
| DURATION | Duration |
| EMAIL | EmailAddress |
| EVENT | Event |
| FACILITY | Facility |
| FOOD | Food |
| GEOLOGICALOBJ | GeographicFeature |
| GPE | GeopoliticalEntity |
| LAW | Law |
| LOCATION | Location |
| MEASURE | Measure |
| MONEY | Money |
| ORDINAL | Ordinal |
| ORGAN | Anatomy |
| ORGANIZATION | Organization |
| PEOPLE | Person |
| PERCENT | Percent |
| PERSONPEOPLE | Person |
| PERSON | Person |
| PHONE | Phone |
| PLANT | Plant |
| PRODUCT | Product |
| SUBSTANCE | Substance |
| TICKER | Ticker |
| TIME | Time |
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
| EVENT | Event |
