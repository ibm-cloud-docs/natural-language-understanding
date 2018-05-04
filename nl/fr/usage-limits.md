---

copyright:
  years: 2015, 2018
lastupdated: "2018-03-16"

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

# Limites d'utilisation

Les limites d'utilisation et les restrictions ci-dessous s'appliquent aux instances du service {{site.data.keyword.nlushort}}.
{: shortdesc}

## Limite relative au texte analysé 

{{site.data.keyword.nlushort}} tronque tout texte analysé contenant plus de 50000 caractères mono-octets ou multi-octets. Pour afficher le texte dont les caractères sont comptabilisés dans vos demandes, associez le paramètre `return_analyzed_text` à la valeur `true`.

Vous pouvez définir un nombre limite de caractères plus petit avec le paramètre `limit_text_characters`. Si vous ne voulez analyser qu'une petite partie du contenu, cette opération peut permettre d'éviter un coût excessif. 

Exemple d'objet de paramètres : 
```json
{
  "url": "ibm.com",
  "limit_text_characters": 10000,
  "return_analyzed_text": true,
  "features": {
    "concepts": {}
  }
}
```

## Nombre maximal de demandes simultanées

Le nombre maximal de demandes simultanées pour chaque instance du service {{site.data.keyword.nlushort}} est de 30. Vous pouvez diminuer ce nombre maximal pour les instances de service dans les plans Lite et Standard si le système doit traiter un trafic exceptionnellement élevé. Par exemple, une application qui envoie 35 demandes simultanées depuis une instance de service unique dépasse le nombre maximal de demandes simultanées de cinq demandes et cinq de ces demandes renverront l'erreur `429: Too many requests` (trop de demandes). 

Pour augmenter le nombre maximal de demandes simultanées, [ouvrez un ticket de demande de service](https://ibm.biz/ibmcloudsupport).


## Support de langue

Des restrictions différentes relatives aux langues s'appliquent selon la façon dont vous utilisez le service. Pour des détails, voir la page [Prise en charge des langues](language-support.html). 


