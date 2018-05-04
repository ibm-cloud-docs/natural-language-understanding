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

# Migration depuis AlchemyLanguage

Depuis le **7 avril 2017**, il n'est plus possible de créer une
instance d'AlchemyAPI dans {{site.data.keyword.cloud}}. Les instances de
service existantes seront prises en charge jusqu'au **7 mars 2018**. Pour
pouvoir continuer à utiliser les fonctions
d'{{site.data.keyword.alchemylanguageshort}}, vous devez migrer votre code vers {{site.data.keyword.nlushort}}.
{: shortdesc}

{{site.data.keyword.nlushort}} propose un modèle de tarification plus
économique et une API consolidée beaucoup plus facile à utiliser. Les fonctions
existantes sont rationalisées afin de les rendre plus utiles et profitables selon les
besoins des clients. {{site.data.keyword.nlushort}} facilite la gestion de votre
marque, regroupe des solutions d'aide à la décision ainsi que des correspondances, des
annonces techniques et des recommandations.


## Présentation des principales modifications

- Nouvelle syntaxe de demande d'API : envoyez des demandes au noeud final `/analyze` 
- Nouvelle structure de réponse (le code qui analyse la sortie d'{{site.data.keyword.alchemylanguageshort}} ne fonctionne pas pour la sortie de {{site.data.keyword.nlushort}}) 
- JSON est le seul format de sortie possible 
- Vous pouvez activer l'*extraction de texte* en associant le paramètre `return_analyzed_text` à la valeur `true`
- Les *microformats* ne sont pas pris en charge 
- L'*extraction de date* n'est pas prise en charge (la *date de publication* est toujours prise en charge par la caractéristique *Métadonnées*) 
- Les options entre guillemets pour les entités ne sont pas prises en charge 
- Le graphique des connaissances (knowledgeGraph) n'est pas pris en charge pour les concepts, les mots clés et les entités 
- Les requêtes de contraintes visuelles (utilisées avec le paramètre `cquery`) ne sont pas prises en charge 
- Les rappels JSONP ne sont pas pris en charge 
- *TypedRelations* dans {{site.data.keyword.alchemylanguageshort}} correspond à *Relations* dans {{site.data.keyword.nlushort}}
- *Relations* dans {{site.data.keyword.alchemylanguageshort}} correspond à *Rôles sémantiques* dans {{site.data.keyword.nlushort}}
- Les types d'entité ont changé (prenez connaissance des nouveaux types d'entité [ici](/docs/services/natural-language-understanding/entity-types.html))
- Les mots ci-dessous sont mal orthographiés dans les résultats de taxonomie AlchemyLanguage. Ils ont été corrigés dans les résultats de catégorie dans Natural Language Understanding. 
  - `offence` -> `offense`
  - `civl` -> `civil`
  - `phyiscs` -> `physics`

## Etapes de migration 

1. [Initiation](/docs/services/natural-language-understanding/getting-started.html) au service {{site.data.keyword.nlushort}}. 
1. Si vous utilisez des modèles personnalisés provenant de Watson Knowledge Studio, redéployez-les dans l'instance de service {{site.data.keyword.nlushort}}. Procédez comme suit pour déployer des [annotateurs reposant sur des règles](/docs/services/knowledge-studio/rule-annotator-model-use.html#wks_rule_publish) ou des [annotateurs d'apprentissage automatique](/docs/services/knowledge-studio/publish-ml.html#wks_manlu) et sélectionnez le service {{site.data.keyword.nlushort}} comme cible du déploiement. 
1. Migrez votre code.
    Si vous utilisez des logiciels SDK Watson Developer Cloud pour interagir avec {{site.data.keyword.alchemylanguageshort}}, vous devez changer votre code SDK. Cliquez sur les liens suivants pour afficher des exemples de logiciel SDK pour {{site.data.keyword.nlushort}} dans GitHub :
    - [Node.js ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://github.com/watson-developer-cloud/node-sdk#natural-language-understanding){: new_window}
    - [Python ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://github.com/watson-developer-cloud/python-sdk/blob/master/examples/natural_language_understanding_v1.py){: new_window}
    - [Swift ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://github.com/watson-developer-cloud/swift-sdk#natural-language-understanding){: new_window}

De plus, vous devez reconfigurer la logique dans votre application, qui attend la sortie des demandes {{site.data.keyword.alchemylanguageshort}}. Assurez-vous que votre code est adapté au traitement de la nouvelle structure de sortie de {{site.data.keyword.nlushort}}.

### Méthodes AlchemyLanguage et caractéristiques Natural Language Understanding correspondantes 
Les demandes {{site.data.keyword.alchemylanguageshort}} sont mappées aux noeuds finaux `/analyze` de {{site.data.keyword.nlushort}}. Les demandes envoyées à `/analyze` sont similaires aux demandes de type appel combiné d'{{site.data.keyword.alchemylanguageshort}}, mais la syntaxe est différente et vous pouvez spécifier des options telles que `limit` individuellement pour chaque caractéristique. Les demandes POST envoyées à `/analyze` acceptent un corps JSON contenant l'entrée et les paramètres pour la demande, et les demandes GET envoyées à `/analyze` acceptent les paramètres de requête dont la syntaxe est similaire à celle des paramètres JSON. 

| Méthode {{site.data.keyword.alchemylanguageshort}} | Noeud final {{site.data.keyword.alchemylanguageshort}} | Caractéristique {{site.data.keyword.nlushort}} |
|------------------------|--------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------|
| Authors | `/text/TextGetAuthors`<br/>`/url/URLGetAuthors` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#metadata">Métadonnées</a> |
| Concepts | `/html/HTMLGetRankedConcepts`<br/>`/text/TextGetRankedConcepts`<br/>`/url/URLGetRankedConcepts` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#concepts">Concepts</a> |
| Date Extraction | `/html/HTMLExtractDates`<br/>`/text/TextExtractDates`<br/>`/url/URLExtractDates` | Non prise en charge |
| Emotion Analysis | `/html/HTMLGetEmotion`<br/>`/text/TextGetEmotion`<br/>`/url/URLGetEmotion` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#emotion">Emotion</a> |
| Targeted Emotion | `/html/HTMLGetTargetedEmotion`<br/>`/text/TextGetTargetedEmotion`<br/>`/url/URLGetTargetedEmotion` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#emotion">Emotion</a> (utilisez l'option `targets`) |
| Entities | `/html/HTMLGetRankedNamedEntities`<br/>`/text/TextGetRankedNamedEntities`<br/>`/url/URLGetRankedNamedEntities` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#entities">Entités</a> |
| Feed Detection | `/html/HTMLGetFeedLinks`<br/>`/url/URLGetFeedLinks` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#metadata">Métadonnées</a> |
| Keywords | `/html/HTMLGetRankedKeywords`<br/>`/text/TextGetRankedKeywords`<br/>`/url/URLGetRankedKeywords` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#keywords">Mots clés</a> |
| Language Detection | `/html/HTMLGetLanguage`<br/>`/text/TextGetLanguage`<br/>`/url/URLGetLanguage` | La détection de langue basique est libre dans les demandes. Les métadonnées de langue autres que le code ISO ne sont pas renvoyées. |
| Microformats | `/html/HTMLGetMicroformatData`<br/>`/url/URLGetMicroformatData` | Non prise en charge |
| Publication Date | `/html/HTMLGetPubDate`<br/>`/url/URLGetPubDate` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#metadata">Métadonnées</a> |
| Relations | `/html/HTMLGetRelations`<br/>`/text/TextGetRelations`<br/>`/url/URLGetRelations` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#semantic-roles">Rôles sémantique</a> |
| Typed Relations | `/html/HTMLGetTypedRelations`<br/>`/text/TextGetTypedRelations`<br/>`/url/URLGetTypedRelations` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#relations">Relations</a> |
| Sentiment Analysis | `/html/HTMLGetTextSentiment`<br/>`/text/TextGetTextSentiment`<br/>`/url/URLGetTextSentiment` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#sentiment">Sentiment</a> |
| Targeted Sentiment | `/html/HTMLGetTargetedSentiment`<br/>`/text/TextGetTargetedSentiment`<br/>`/url/URLGetTargetedSentiment` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#sentiment">Sentiment</a> (utilisez l'option `targets`) |
| Taxonomy | `/html/HTMLGetRankedTaxonomy`<br/>`/text/TextGetRankedTaxonomy`<br/>`/url/URLGetRankedTaxonomy` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#categories">Catégories</a> |
| Text (cleaned) | `/html/HTMLGetText`<br/>`/url/URLGetText` | Associez `return_analyzed_text` à la valeur `true` dans toute demande valide envoyée à `/analyze` |
| Text (raw) | `/html/HTMLGetRawText`<br/>`/url/URLGetRawText` | Associez `return_analyzed_text` à la valeur `true` et `clean` à la valeur `false` dans toute demande valide envoyée à `/analyze` |
| Title Extraction | `/html/HTMLGetTitle`<br/>`/url/URLGetTitle` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#metadata">Métadonnées</a> |

Ainsi, si vous effectuez l'appel combiné suivant :

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

il se présente sous la forme suivante dans {{site.data.keyword.nlushort}} :

```bash
curl -X POST \
-H "Content-Type: application/json" \
-u "{username}":"{password}" \
-d @parameters.json "https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze?version=2017-02-27"
```
{: pre}

Avec le code parameters.json suivant :

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

## Harmonisation d'entité 

Si vous utilisiez les modèles publiques de la méthode TypedRelations d'{{site.data.keyword.alchemylanguageshort}}, vous devez changer tout code qui attend les types d'entité de ces modèles. Le tableau ci-dessous présente le mappage des types d'entité TypedRelations aux types d'entité de {{site.data.keyword.nlushort}}. 

| Type d'entité TypedRelations | Type d'entité Relations de {{site.data.keyword.nlushort}} |
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
