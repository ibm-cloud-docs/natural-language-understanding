---

copyright:
  years: 2015, 2017
lastupdated: "2017-06-09"

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

# Tutoriel Initiation
Ce bref tutoriel présente {{site.data.keyword.nlushort}} en analysant un exemple de texte pour y révéler les opinions qu'il recèle.
{:shortdesc}

## Etape 1 : Connectez-vous, créez l'instance de service et obtenez vos données d'identification
{: #create-service}

Si vous connaissez déjà vos données d'identification pour l'instance de service {{site.data.keyword.nlushort}}, ignorez cette étape.
{: tip}

1.  Accédez au [service {{site.data.keyword.nlushort}}](https://console.{DomainName}/catalog/services/natural-language-understanding/) et inscrivez-vous pour un compte {{site.data.keyword.Bluemix_notm}} gratuit ou connectez-vous.
1.  Après vous être connecté, entrez `sentiment-tutorial` dans la zone **Nom du service** et cliquez sur **Créer**.
1.  Copiez vos données d'identification :
    1.  Cliquez sur **Données d'identification pour le service**.
    1.  Cliquez sur **Afficher les données d'identification** sous **Actions**.
    1.  Copiez les valeurs `username` et `password`.

## Etape 2 : Analysez le contenu de l'exemple pour révéler les opinions qu'il recèle
{: #analyze-sample}

Analysez d'abord les opinions que recèle l'exemple de texte. Lancez la commande suivante pour appeler la méthode `GET /v1/analyze`, laquelle analyse l'exemple de texte pour révéler les opinions qu'il dénote et les mots-clés. Remplacez `{nom_utilisateur}` et `{mot_de_passe}` par les données d'identification du service copiées à l'étape précédente :

```bash
curl --user "{nom_utilisateur}":"{mot_de_passe}" \
"https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze?version=2017-02-27&text=I%20still%20have%20a%20dream%2C%20a%20dream%20deeply%20rooted%20in%20the%20American%20dream%20%E2%80%93%20one%20day%20this%20nation%20will%20rise%20up%20and%20live%20up%20to%20its%20creed%2C%20%22We%20hold%20these%20truths%20to%20be%20self%20evident%3A%20that%20all%20men%20are%20created%20equal.&features=sentiment,keywords"
```
{:pre}

## Etape 3 : Extrayez les informations sur les mots clés
{: #analyze-keywords}

L'appel précédent a renvoyé les informations concernant les opinions sur l'ensemble du texte. Développez à présent les résultats pour extraire une analyse des opinions portant spécifiquement sur chaque mot clé. Incluez le paramètre **keywords.sentiment** en lui affectant la valeur `true`. Remplacez `{nom_utilisateur}` et `{mot_de_passe}` par vos informations.

```bash
curl --user "{nom_utilisateur}":"{mot_de_passe}" \
"https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze?version=2017-02-27&text=I%20still%20have%20a%20dream%2C%20a%20dream%20deeply%20rooted%20in%20the%20American%20dream%20%E2%80%93%20one%20day%20this%20nation%20will%20rise%20up%20and%20live%20up%20to%20its%20creed%2C%20%22We%20hold%20these%20truths%20to%20be%20self%20evident%3A%20that%20all%20men%20are%20created%20equal.&features=sentiment,keywords&keywords.sentiment=true"
```
{:pre}

## Etape 4 : Ciblez une phrase
{: #analyze-phrase}

Ciblez à présent un contenu spécifique pour examiner une analyse au niveau d'une phrase ou d'une expression (au lieu d'une analyse au niveau d'un document ou d'un mot clé) en incluant la phrase `the%20American%20dream%20` dans le paramètre **sentiment.targets**. N'oubliez pas de remplacer `{nom_utilisateur}` et `{mot_de_passe}` par vos informations.

```bash
curl --user "{nom_utilisateur}":"{mot_de_passe}" \
"https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze?version=2017-02-27&text=I%20still%20have%20a%20dream%2C%20a%20dream%20deeply%20rooted%20in%20the%20American%20dream%20one%20day%20this%20nation%20will%20rise%20up%20and%20live%20up%20to%20its%20creed%20We%20hold%20these%20truths%20to%20be%20self%20evident%3A%20that%20all%20men%20are%20created%20equal.&features=sentiment,keywords&keywords.sentiment=true&sentiment.targets=the%20American%20dream"
```
{:pre}

## Etapes suivantes
{: #next-steps}

Vous avez terminé ! Ce tutoriel ne fait qu'effleurer l'éventail de vos possibilités avec {{site.data.keyword.nlushort}}. Pour plus d'informations sur les fonctionnalités de l'API, reportez-vous aux ressources suivantes :

- Cliquez sur l'icône [Référence d'API ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/){: new_window} pour plus de détails et des exemples de chaque paramètre.
- Cliquez sur cette icône pour découvrir les [entités personnalisées et les relations![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/watson/developercloud/doc/natural-language-understanding/customizing.html){: new_window}.
