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

# Migration von AlchemyLanguage

Ab dem **7. April 2017** wird es nicht mehr möglich sein, auf {{site.data.keyword.cloud}} eine neue Instanz von AlchemyAPI zu erstellen. Bestehende Serviceinstanzen werden bis zum **7. März 2018** unterstützt. Um {{site.data.keyword.alchemylanguageshort}}-Features weiterhin verwenden zu können, müssen Sie Ihren Code auf {{site.data.keyword.nlushort}} migrieren.
{: shortdesc}

{{site.data.keyword.nlushort}} bietet ein wirtschaftlicheres Preismodell und eine benutzerfreundlichere konsolidierte API. Vorhandene Features werden rationalisiert, um sie für die Anforderungen unserer Kunden brauchbarer und wertvoller zu machen. {{site.data.keyword.nlushort}} erleichtert Ihnen die Verwaltung Ihrer Marke, die Erfassung von Geschäftsdaten und die Clusterbildung zwecks Abgleich, Onlinewerbung und Empfehlungen.

## Übersicht über die wesentlichen Veränderungen

- Neue Syntax für API-Anforderungen: Senden von Anforderungen an den `/analyze`-Endpunkt
- Neue Antwortstruktur (Code, der {{site.data.keyword.alchemylanguageshort}}-Ausgaben analysiert, funktioniert bei {{site.data.keyword.nlushort}}-Ausgaben nicht)
- JSON ist das einzige Ausgabeformat
- *Text extraction* wird aktiviert, indem der Parameter `return_analyzed_text` auf `true` gesetzt wird
- *Microformats* wird nicht unterstützt
- *Date extraction* wird nicht unterstützt (*Publication Date* wird im Feature *Metadata* weiterhin unterstützt)
- Optionen für "quotations" für Entitäten werden nicht unterstützt
- "knowledgeGraph" wird für Konzepte, Schlüsselwörter oder Entitäten nicht unterstützt
- Abfragen mit visueller Beschränkung (verwendet mit dem Parameter `cquery`) werden nicht unterstützt
- JSONP-Rückrufe werden nicht unterstützt
- *TypedRelations* aus {{site.data.keyword.alchemylanguageshort}} wurde in {{site.data.keyword.nlushort}} zu *Relations* geändert
- *Relations* aus {{site.data.keyword.alchemylanguageshort}} wurde in {{site.data.keyword.nlushort}} zu *Semantic Roles* geändert
- Die Entitätstypen wurden geändert (die neuen Entitätstypen finden Sie [hier](/docs/services/natural-language-understanding/entity-types.html))
- Folgende Wörter waren in den Taxonomieergebnissen von AlchemyLanguage falsch geschrieben. Sie wurden in den Kategorieergebnissen von Natural Language Understanding korrigiert.
  - `offence` -> `offense`
  - `civl` -> `civil`
  - `phyiscs` -> `physics`

## Migrationsschritte

1. [Beginnen Sie ](/docs/services/natural-language-understanding/getting-started.html) mit dem {{site.data.keyword.nlushort}}-Service.
1. Wenn Sie angepasste Modelle aus Watson Knowledge Studio verwenden, stellen Sie sie in Ihrer neuen {{site.data.keyword.nlushort}}-Serviceinstanz erneut bereit. Befolgen Sie die Schritte für die Bereitstellung von [regelbasierten Annotatoren](/docs/services/knowledge-studio/rule-annotator-model-use.html#wks_rule_publish) oder [lernfähigen Annotatoren](/docs/services/knowledge-studio/publish-ml.html#wks_manlu) und wählen Sie den {{site.data.keyword.nlushort}}-Service als Bereitstellungsziel aus.
1. Migrieren Sie Ihren Code.
    Wenn Sie Watson Developer Cloud-SDKs für die Interaktion mit {{site.data.keyword.alchemylanguageshort}} verwenden, müssen Sie Ihren SDK-Code ändern. Klicken Sie auf die folgenden Links, um {{site.data.keyword.nlushort}}-SDK-Beispiele in GitHub zu sehen:
    - [Node.js ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://github.com/watson-developer-cloud/node-sdk#natural-language-understanding){: new_window}
    - [Python ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://github.com/watson-developer-cloud/python-sdk/blob/master/examples/natural_language_understanding_v1.py){: new_window}
    - [Swift ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://github.com/watson-developer-cloud/swift-sdk#natural-language-understanding){: new_window}

Zusätzlich müssen Sie alle Logik in Ihrer Anwendung rekonfigurieren, die eine Ausgabe von {{site.data.keyword.alchemylanguageshort}}-Anforderungen erwartet. Achten Sie darauf, Ihren Code für die Verarbeitung der neuen Ausgabestruktur von {{site.data.keyword.nlushort}} anzupassen.

### Methoden von AlchemyLanguage und entsprechende Features von Natural Language Understanding
{{site.data.keyword.alchemylanguageshort}}-Anforderungen werden dem {{site.data.keyword.nlushort}}-Endpunkt `/analyze` zugeordnet. Anforderungen an `/analyze` ähneln den kombinierten Rufanforderungen ('Combined Call') von {{site.data.keyword.alchemylanguageshort}}, unterscheiden sich aber in der Syntax. Zudem haben Sie die Möglichkeit, Optionen wie `limit` (Begrenzung) für jedes Feature einzeln anzugeben. POSTs an `/analyze` akzeptieren einen JSON-Hauptteil, der die Eingabe und die Parameter für die Anforderung enthält, und GETs an `/analyze` akzeptieren Abfrageparameter, die zur Syntax der JSON-Parameter analog sind.

| {{site.data.keyword.alchemylanguageshort}}-Methode | {{site.data.keyword.alchemylanguageshort}}-Endpunkt | {{site.data.keyword.nlushort}}-Feature |
|------------------------|--------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------|
| Authors | `/text/TextGetAuthors`<br/>`/url/URLGetAuthors` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#metadata">Metadaten</a> |
| Concepts | `/html/HTMLGetRankedConcepts`<br/>`/text/TextGetRankedConcepts`<br/>`/url/URLGetRankedConcepts` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#concepts">Konzepte</a> |
| Date Extraction | `/html/HTMLExtractDates`<br/>`/text/TextExtractDates`<br/>`/url/URLExtractDates` | Nicht unterstützt |
| Emotion Analysis | `/html/HTMLGetEmotion`<br/>`/text/TextGetEmotion`<br/>`/url/URLGetEmotion` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#emotion">Emotion</a> |
| Targeted Emotion | `/html/HTMLGetTargetedEmotion`<br/>`/text/TextGetTargetedEmotion`<br/>`/url/URLGetTargetedEmotion` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#emotion">Emotion</a> (Option `targets` (Ziele) verwenden) |
| Entities | `/html/HTMLGetRankedNamedEntities`<br/>`/text/TextGetRankedNamedEntities`<br/>`/url/URLGetRankedNamedEntities` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#entities">Entitäten</a> |
| Feed Detection | `/html/HTMLGetFeedLinks`<br/>`/url/URLGetFeedLinks` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#metadata">Metadaten</a> |
| Keywords | `/html/HTMLGetRankedKeywords`<br/>`/text/TextGetRankedKeywords`<br/>`/url/URLGetRankedKeywords` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#keywords">Schlüsselwörter</a> |
| Language Detection | `/html/HTMLGetLanguage`<br/>`/text/TextGetLanguage`<br/>`/url/URLGetLanguage` | Die grundlegende Spracherkennung ist in jeder Anforderung frei. Andere Sprachmetadaten als der ISO-Code werden nicht zurückgegeben. |
| Microformats | `/html/HTMLGetMicroformatData`<br/>`/url/URLGetMicroformatData` | Nicht unterstützt |
| Publication Date | `/html/HTMLGetPubDate`<br/>`/url/URLGetPubDate` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#metadata">Metadaten</a> |
| Relations | `/html/HTMLGetRelations`<br/>`/text/TextGetRelations`<br/>`/url/URLGetRelations` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#semantic-roles">Semantische Rollen</a> |
| Typed Relations | `/html/HTMLGetTypedRelations`<br/>`/text/TextGetTypedRelations`<br/>`/url/URLGetTypedRelations` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#relations">Relations</a> |
| Sentiment Analysis | `/html/HTMLGetTextSentiment`<br/>`/text/TextGetTextSentiment`<br/>`/url/URLGetTextSentiment` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#sentiment">Stimmung</a> |
| Targeted Sentiment | `/html/HTMLGetTargetedSentiment`<br/>`/text/TextGetTargetedSentiment`<br/>`/url/URLGetTargetedSentiment` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#sentiment">Stimmung</a> (Option `targets` (Ziele) verwenden) |
| Taxonomy | `/html/HTMLGetRankedTaxonomy`<br/>`/text/TextGetRankedTaxonomy`<br/>`/url/URLGetRankedTaxonomy` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#categories">Kategorien</a> |
| Text (cleaned) | `/html/HTMLGetText`<br/>`/url/URLGetText` | In jeder gültigen Anforderung an `/analyze` den Parameter `return_analyzed_text` auf `true` setzen|
| Text (raw) | `/html/HTMLGetRawText`<br/>`/url/URLGetRawText` | In jeder gültigen Anforderung an `/analyze` den Parameter `return_analyzed_text` auf `true` und den Parameter `clean` auf `false` setzen|
| Title Extraction | `/html/HTMLGetTitle`<br/>`/url/URLGetTitle` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#metadata">Metadaten</a> |

Beispiel: Der kombinierte Ruf ('combined call')...

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

... würde in {{site.data.keyword.nlushort}} jetzt wie folgt aussehen:

```bash
curl -X POST \
-H "Content-Type: application/json" \
-u "{username}":"{password}" \
-d @parameters.json "https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze?version=2017-02-27"
```
{: pre}

Mit dieser parameters.json-Datei:

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

## Entitätenharmonisierung

Wenn Sie die öffentlichen Modelle aus der Methode 'TypedRelations' von {{site.data.keyword.alchemylanguageshort}} verwendet haben, müssen Sie allen Code ändern, der die Entitätstypen aus diesen Modellen erwartet. Die folgende Tabelle zeigt die Zuordnung von Entitätstypen der Methode 'TypedRelations' zu Entitätstypen von {{site.data.keyword.nlushort}}.

| Entitätstyp 'TypedRelations' | {{site.data.keyword.nlushort}}-Entitätstyp 'Relations' |
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
