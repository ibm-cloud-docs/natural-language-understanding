---

copyright:
  years: 2015, 2019
lastupdated: "2019-03-20"

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
{: #customizing}

Avec [{{site.data.keyword.knowledgestudiofull}} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/watson/services/knowledge-studio/), vous pouvez
étendre{{site.data.keyword.nlushort}} avec des modèles personnalisés qui identifient des entités,
des relations et des catégories personnalisées propres à votre domaine.
{: shortdesc}

## Initiation aux modèles personnalisés
{: #getting-started-with-custom-models}

> Le plan gratuit de {{site.data.keyword.nlushort}} limite la taille et les performances de votre modèle personnalisé. Pour tester un modèle personnalisé dans toute son ampleur, vous devez l'utiliser avec le plan standard de {{site.data.keyword.nlushort}}.

1. Si vous ne l'avez pas encore fait, [familiarisez-vous](/docs/services/natural-language-understanding?topic=natural-language-understanding-getting-started) avec {{site.data.keyword.nlushort}}.
2. [Découvrez {{site.data.keyword.knowledgestudioshort}}](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-wks_tutintro#wks_tutintro).
3. Créez un modèle personnalisé.
   1. Pour créer un modèle d'entités et de relations personnalisé, voir [Création d'un modèle d'apprentissage automatique](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-wks_tutml_intro) 
   2. Vous pouvez également créer un modèle d'entités personnalisé avec un modèle basé sur des règles. Pour plus d'informations, voir [Création d'un modèle basé sur des règles](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-wks_tutrule_intro).
   3. Pour créer un modèle de catégories personnalisé, voir [Création d'un modèle de catégories personnalisé](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-create-categories-model).
4. [Déployez votre modèle dans {{site.data.keyword.nlushort}}](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-publish-ml#wks_manlu)
5. Pour utiliser votre modèle, spécifiez le `modèle` que vous avez déployé dans l'option
[entities ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/apidocs/natural-language-understanding#entities){: new_window},
[relations ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/apidocs/natural-language-understanding#relations){: new_window} ou [catégories ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/apidocs/natural-language-understanding#categories){: new_window} de votre demande d'API :
    - Exemple de fichier *parameters.json* :

        ```json
        {
          "url": "www.url.example",
          "features": {
            "categories": {
              "model": "your-model-id-here"
            },
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
        curl --user "apikey":"{apikey}" \
        "{url}/v1/analyze?version=2018-11-16" \
        --request POST \
        --header "Content-Type: application/json" \
        --data @parameters.json
        ```
        {: pre}

## Suppression d'un modèle personnalisé
{: #deleting-a-custom-model}

Le nombre de modèles personnalisés que vous déployez dans {{site.data.keyword.nlushort}} a des conséquences sur votre facture {{site.data.keyword.nlushort}} en fonction de votre [plan de tarification](https://www.ibm.com/cloud/watson-natural-language-understanding/pricing). Pour éviter des frais liés à un modèle que vous n'utilisez plus, [annulez le déploiement du modèle avec {{site.data.keyword.knowledgestudioshort}}](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-publish-ml#undeploy-view-model) ou annulez le déploiement du modèle en utilisant la méthode de **[suppression de modèle](https://{DomainName}/apidocs/natural-language-understanding#delete-model)**.

Exemple de demande curl :

```bash
curl --user "apikey":"{apikey}" \
"{url}/v1/models/{model_id}?version=2018-10-30" \
--request DELETE
```
{: pre}


## Prise en charge de langue pour les modèles personnalisés
{: #language-support-for-custom-models}

Consultez les colonnes *Prise en charge de modèle personnalisé* des tableaux [Support de langue](/docs/services/natural-language-understanding?topic=natural-language-understanding-language-support) pour voir les modèles personnalisés pris en charge pour chaque langue.

### Sentiment ciblé pour les entités de modèle personnalisé
{: #targeted-sentiment-for-custom-entities}

Pour l'anglais uniquement, vous pouvez obtenir des scores de sentiment pour chaque entité de modèle personnalisé détectée par le service en indiquant `sentiment: true` dans l'objet d'entités. Aucun autre support de langue ne prend en charge le sentiment ciblé pour les entités de modèle personnalisé.
