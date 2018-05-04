---

copyright:
  years: 2015, 2018
lastupdated: "2018-01-16"

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

# Personnalisation 

Avec [{{site.data.keyword.knowledgestudiofull}} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://ibm.biz/watsonknowledgestudio), vous pouvez
étendre {{site.data.keyword.nlushort}} avec des modèles personnalisés qui identifient des entités et des relations
personnalisées propres à votre domaine.
{: shortdesc}

## Initiation aux modèles personnalisés 

> Le plan gratuit de {{site.data.keyword.nlushort}} limite la taille et les performances de votre modèle personnalisé. Pour tester un modèle personnalisé dans toute son ampleur, vous devez l'utiliser avec le plan standard de {{site.data.keyword.nlushort}}. 

1. Si vous ne l'avez pas encore fait, [familiarisez-vous](/docs/services/natural-language-understanding/getting-started.html) avec {{site.data.keyword.nlushort}}.
1. [Obtenez l'accès à {{site.data.keyword.knowledgestudioshort}} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/us-en/marketplace/supervised-machine-learning/purchase#product-header-top) et connectez-vous par le biais du [tableau de bord en ligne ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://gateway.watsonplatform.net/knowledge-studio/ui/dashboard/). 
1. Consultez la [documentation](/docs/services/knowledge-studio/index.html) de {{site.data.keyword.knowledgestudioshort}} pour apprendre à créer un modèle personnalisé (annotateur) et à le déployer dans {{site.data.keyword.nlushort}}. 
1. Pour utiliser votre modèle, spécifiez le `modèle` que vous avez déployé dans l'option [entities ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/#entities){: new_window}
ou [relations ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/#relations){: new_window} de votre demande d'API : 
    - Exemple de fichier *parameters.json* : 

        ```json
        {
          "url": "www.url.example",
          "features": {
            "entities": {
              "model": "your-model-id-here"
            },
            "relations": {
              "model": "your-model-id-here"
            }
          }
        }
        ```
        {: codeblock}
    
    - Exemple de demande curl : 

        ```bash
        curl -X POST \
        -H "Content-Type: application/json" \
        -u "{username}":"{password}" \
        -d @parameters.json \
        "https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze?version=2017-02-27"
        ```
        {: pre}

