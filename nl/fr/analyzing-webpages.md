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


# Analyse de pages Web
{: #analyzing-webpages}

{{site.data.keyword.nlushort}} permet d'analyser le texte de pages Web à l'aide d'un programme. Lorsque vous indiquez dans votre demande d'API des éléments HTML bruts ou une URL publiquement accessible, le service tente de cibler l'analyse sur le contenu principal de la page, comme le texte d'un article ou d'une publication de blogue.

**Mode de fonctionnement**

1. Indiquez une URL publiquement accessible avec le paramètre **url** ou envoyez des éléments HTML bruts dans le paramètre **html**.
2. Par défaut, le service [nettoie](#webpage-cleaning) la page Web afin de retirer le texte indésirable, tel que les publicités.
3. Si vous indiquez une [requête XPath](#xpath) avec le paramètre **xpath**, le service utilise la requête pour sélectionner des éléments spécifiques de la page à inclure dans l'analyse. Si l'élément **clean** a la valeur `false` lorsque vous utilisez **xpath**, seul le résultat de la requête XPath sera analysé.

## Nettoyage de page Web
{: #webpage-cleaning}

Par défaut, le service "nettoie" les pages Web avant leur analyse. Cette opération tente de retirer le contenu généralement indésirable, tel que les publicités ou tout autre texte pouvant interférer avec l'analyse du contenu principal de la page.

Pour désactiver le nettoyage de page Web, attribuez la valeur `false` à l'élément **clean**. L'exemple suivant désactive le nettoyage de page Web.

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


## Analyse d'éléments spécifiques d'une page Web avec XPath
{: #xpath}

Le paramètre **xpath** vous permet d'utiliser une requête XPath pour analyser des parties spécifiques d'une page Web. Pour en savoir plus sur XPath, consultez les ressources suivantes.

  - [Tutoriel W3Schools XPath](https://www.w3schools.com/xml/xpath_intro.asp)
  - [Article XPath dans Wikipedia](https://wikipedia.org/wiki/XPath)

Le comportement du paramètre **xpath** dépend de la valeur du paramètre **clean** : 

  - **clean** = `true` (valeur par défaut) : les résultats de la requête XPath seront ajoutés au texte de la page Web nettoyée avant l'analyse du texte combiné.
  - **clean** = `false` : seuls les résultats de la requête XPath seront analysés.

### Inclusion de texte provenant d'éléments spécifiques dans l'analyse
{: #analyze-cleaned-and-xpath}

Par défaut, le paramètre **clean** a la valeur `true` et les résultats d'une requête XPath sont ajoutés au texte de la page Web nettoyée après un caractère de nouvelle ligne et ce avant que le texte combiné ne soit analysé. Cela peut s'avérer utile si vous souhaitez inclure des éléments dans l'analyse qui seraient autrement retirés par le nettoyage de page Web. L'exemple suivant utilise le paramètre **xpath** pour inclure dans l'analyse le titre et le sous-titre de la page Web exemple.

Fichier ***parameters.json* exemple**
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

**Exemple de demande**
```bash
curl --user "apikey:{apikey}" \
"{url}/v1/analyze?version=2018-09-21" \
--request POST \
--header "Content-Type: application/json" \
--data @parameters.json
```
{: pre}


### Analyse du texte provenant d'éléments spécifiques uniquement
{: #analyze-xpath-results-only}

Pour analyser uniquement le résultat d'une requête XPath, utilisez le paramètre **xpath** et attribuez la valeur `false` au paramètre **clean**. L'exemple suivant analyse uniquement le titre et le sous-titre de la page Web exemple.

Fichier ***parameters.json* exemple**
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

**Exemple de demande**
```bash
curl --user "apikey:{apikey}" \
"{url}/v1/analyze?version=2018-09-21" \
--request POST \
--header "Content-Type: application/json" \
--data @parameters.json
```
{: pre}
