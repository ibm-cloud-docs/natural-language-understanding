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
{:download: .download}

# Traitement des incidents
{: #troubleshooting}

Si vous rencontrez des problèmes lorsque vous utilisez {{site.data.keyword.nlushort}}, les conseils de traitement des incidents suivants peuvent vous être utiles.
{:shortdesc}

## Les types d'entité des fonctions de relations et d'entités ne sont pas cohérents
{: #inconsistent-entity-types}

Les systèmes de types d'entité pour les fonctions d'entités et de relations ne sont pas toujours cohérents. Pour certaines langues et dates de version, les résultats des relations contiennent des types d'entité différents de ceux qui apparaissent dans les résultats des entités. Pour plus d'informations, voir [Types et sous-types d'entité](/docs/services/natural-language-understanding?topic=natural-language-understanding-entity-type-systems) et [Types de relation](/docs/services/natural-language-understanding?topic=natural-language-understanding-relation-type-systems). 

## Détection de langue incorrecte
{: #incorrect-language-detection}

La détection automatique de langue peut ne pas être précise lorsque le texte contient moins de 100 caractères. Si le service ne détecte pas la langue correcte de votre texte, vous pouvez [ignorer la détection automatique de langue](/docs/services/natural-language-understanding?topic=natural-language-understanding-overriding-language-detection).

## Nombre de demandes trop élevé
{: #too-many requests}

Si une erreur "429: Too many requests" s'affiche, il est possible que la limite de demandes simultanées ait été atteinte pour votre instance de service. Pour plus d'informations, consultez la page [Limites d'utilisation](/docs/services/natural-language-understanding?topic=natural-language-understanding-usage-limits#concurrent-requests).

## Résultats inattendus lors de l'analyse de la page Web
{: #unexpected-webpage-results}

Dans certains cas, l'analyse d'une page Web peut renvoyer des résultats inattendus. Pour enquêter, attribuez la valeur `true` au paramètre **return_analyzed_text** afin d'examiner le texte analysé dans votre demande. Lorsque l'opération de [nettoyage de page Web](/docs/services/natural-language-understanding?topic=natural-language-understanding-analyzing-webpages#webpage-cleaning) ne retire pas suffisamment de texte indésirable, utilisez le paramètre [**xpath**](/docs/services/natural-language-understanding?topic=natural-language-understanding-analyzing-webpages#xpath) pour que l'analyse soit effectuée sur des éléments spécifiques de la page.

## Explications de résultats particuliers
{: #explanations-for-results}

{{site.data.keyword.nlushort}} ne fournit aucun outil de diagnostic expliquant pourquoi une demande particulière a renvoyé un résultat spécifique. Le service est conçu afin de fournir des résultats précis pour le plus grand nombre d'exemples de texte, mais en raison de la nature des modèles d'apprentissage automatique que nous utilisons, nous ne pouvons pas garantir qu'un résultat spécifique semblera correct du point de vue humain.






