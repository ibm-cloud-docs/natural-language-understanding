---

copyright:
  years: 2015, 2018
lastupdated: "2018-12-19"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:important: .important}
{:note: .note}
{:deprecated: .deprecated}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:javascript: .ph data-hd-programlang='javascript'}
{:go: .ph data-hd-programlang='go'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}
{:download: .download}
{:apikey: data-credential-placeholder='apikey'}
{:url: data-credential-placeholder='url'}
{:hide-dashboard: .hide-dashboard}

# Tutoriel d'initiation
{: #getting-started}

Ce bref tutoriel présente l'API {{site.data.keyword.nlushort}} et inclut des demandes exemple ainsi que des liens vers des ressources supplémentaires.
{:shortdesc}

## Avant de commencer
{: #before-you-begin}

- {: hide-dashboard} Créez une instance du service :
    1.  Accédez à la page [{{site.data.keyword.nlushort}} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/catalog/services/natural-language-understanding){: new_window} du catalogue {{site.data.keyword.Bluemix_notm}}.
    2.  Inscrivez-vous pour un compte {{site.data.keyword.Bluemix_notm}} gratuit ou connectez-vous.
    3.  Cliquez sur **Create**.
- Copiez les données d'identification afin de vous authentifier auprès de votre instance de service :
    1.  Sur la page **Manage**, cliquez sur **Show** pour afficher vos données d'identification.
    2.  Copiez la clé d'API`` et les valeurs d'URL``.
- Assurez-vous que la commande `curl` est disponible :
    - Les exemples utilisent la commande `curl` pour appeler les méthodes de l'interface HTTP. Installez la version correspondant à votre système d'exploitation depuis le site [curl.haxx.se ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://curl.haxx.se/){: new_window}. Installez la version qui prend en charge le protocole SSL (Secure Sockets Layer). Veillez à inclure le fichier binaire installé indiqué dans votre variable d'environnement `PATH`.

Ce tutoriel présente comment utiliser l'API {{site.data.keyword.nlushort}} à partir d'une interface de ligne de commande. Pour télécharger des bibliothèques client pour différents langages de programmation, consultez les [kits SDK Watson](/docs/services/natural-language-understanding?topic=watson-using-sdks#using-sdks).
{:tip}

## Etape 1 : Analyse d'une page Web
{: #analyze-sample}

Exécutez la commande suivante pour analyser une page Web afin d'obtenir le sentiment, les concepts, les catégories, les entités et les mots clés. <span class="hide-dashboard">Remplacez `{apikey}` et `{url}` par vos données d'identification de service.</span>

```bash
curl -X POST -u "apikey:{apikey}"{: apikey} \
"{url}/v1/analyze?version=2018-11-16"{: url} \
--header "Content-Type: application/json" \
--data '{
  "url": "http://newsroom.ibm.com/Guerbet-and-IBM-Watson-Health-Announce-Strategic-Partnership-for-Artificial-Intelligence-in-Medical-Imaging-Liver",
  "features": {
    "sentiment": {},
    "categories": {},
    "concepts": {},
    "entities": {},
    "keywords": {}
  }
}'
```
{:pre}

L'étape suivante présente comment spécifier des options qui personnalisent l'analyse de chaque fonction.

## Etape 2 : Analyse des mots clés et des phrases cible
{: #analyze-phrase}

{{site.data.keyword.nlushort}} peut analyser des phrases cible dans le texte environnant et y rechercher des résultats d'émotion et de sentiment. L'option **targets** appliquée à sentiment dans l'exemple suivant indique au service de rechercher les cibles "apples", "oranges" et "broccoli". Etant donné que les éléments "apples" et "oranges" se trouvent dans le texte, des scores de sentiment sont renvoyés pour ces cibles.

Vous pouvez également obtenir des résultats liés aux éléments sentiment et émotion pour les entités et les mots clés détectés dans votre texte. Dans l'exemple, l'option **emotion** pour les mots clés indique au service de rechercher des résultats de type émotion dans chaque mot clé détecté.

```bash
curl -X POST -u "apikey:{apikey}"{: apikey} \
"{url}/v1/analyze?version=2018-11-16"{: url} \
--request POST \
--header "Content-Type: application/json" \
--data '{
  "text": "I love apples! I do not like oranges.",
  "features": {
    "sentiment": {
      "targets": [
        "apples",
        "oranges",
        "broccoli"
      ]
    },
    "keywords": {
      "emotion": true
    }
  }
}'
```
{:pre}

## Etapes suivantes
{: #next-steps}

- Consultez la [référence d'API![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/apidocs/natural-language-understanding){: new_window}.
- Apprenez à identifier les [entités personnalisées et les relations](/docs/services/natural-language-understanding?topic=natural-language-understanding-customizing).
