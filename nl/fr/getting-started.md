---

copyright:
  years: 2015, 2017
lastupdated: "2017-11-03"

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

# Tutoriel d'initiation
Ce bref tutoriel présente {{site.data.keyword.nlushort}} en analysant un exemple de texte pour révéler le sentiment qu'il recèle.
{:shortdesc}

## Avant de commencer
{: #before-you-begin}

- Créez une instance du service :
    - {: download} Si vous voyez ceci, cela signifie que vous avez créé votre instance de service. A présent, procurez-vous vos données d'identification. 
    - Créez un projet à partir d'un service :
        1.  Accédez à la page {{site.data.keyword.watson}} Developer Console [Services ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://console.{DomainName}/developer/watson/services){: new_window}. 
        1.  Sélectionnez {{site.data.keyword.nlushort}}, cliquez sur **Ajouter un service**, puis inscrivez-vous afin d'obtenir un compte {{site.data.keyword.Bluemix_notm}} gratuit ou connectez-vous. 
        1.  Entrez `sentiment-tutorial` comme nom de projet et cliquez sur **Créer un projet**.
- Copiez les données d'identification afin de vous authentifier auprès de votre instance de service :
    - {: download} Depuis le tableau de bord de service (que vous avez sous les yeux) :
        1.  Sélectionnez l'onglet **Données d'identification pour le service**. 
        1.  Cliquez sur **Afficher les données d'identification** sous **Actions**.
        1.  Copiez les valeurs `username`, `password` et `url`.
        {: download}
    - Depuis le projet **sentiment-tutorial** dans Developer Console, copiez les valeurs `username`, `password`, et `url` pour `"natural_language_understanding"` de la section **Données d'identification**. 
- Vérifiez que cURL est installé : 
    - Les exemples utilisent cURL pour appeler des méthodes de l'interface HTTP. Installez la version correspondant à votre système d'exploitation depuis le site [curl.haxx.se ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://curl.haxx.se/){: new_window}. Installez la version qui prend en charge le protocole SSL (Secure Sockets Layer). Veillez à inclure le fichier binaire installé indiqué dans votre variable d'environnement `PATH`.

<!-- Remove this text after dedicated instances have the Developer Console: begin -->

Si vous utilisez {{site.data.keyword.Bluemix_dedicated_notm}}, créez votre instance de service depuis la page [{{site.data.keyword.nlushort}} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://console.{DomainName}/catalog/services/natural-language-understanding/){: new_window} du catalogue. Pour savoir comment rechercher vos données d'identification pour le service, voir [Données d'identification de service pour des services Watson ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](/docs/services/watson/getting-started-credentials.html#getting-credentials-manually){: new_window}.

<!-- Remove this text after dedicated instances have the Developer Console: end -->

## Etape 1 : Analysez le contenu de l'exemple pour révéler le sentiment qu'il recèle
{: #analyze-sample}

Analysez d'abord le sentiment que recèle l'exemple de texte. Ouvrez une interface de ligne de commande et exécutez la commande suivante pour appeler la méthode `GET /v1/analyze`, qui analyse l'exemple de texte pour identifier le sentiment et des mots clés. Remplacez `{nom_utilisateur}` et `{mot_de_passe}` par les données d'identification du service copiées à l'étape précédente :

```bash
curl --user "{nom_utilisateur}":"{mot_de_passe}" \
"https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze?version=2017-02-27&text=I%20still%20have%20a%20dream%2C%20a%20dream%20deeply%20rooted%20in%20the%20American%20dream%20%E2%80%93%20one%20day%20this%20nation%20will%20rise%20up%20and%20live%20up%20to%20its%20creed%2C%20%22We%20hold%20these%20truths%20to%20be%20self%20evident%3A%20that%20all%20men%20are%20created%20equal.&features=sentiment,keywords"
```
{:pre}

## Etape 2 : Procédez à l'extraction des informations sur les mots clés
{: #analyze-keywords}

L'appel précédent a renvoyé des informations concernant le sentiment pour l'ensemble du texte. A présent, développez les résultats pour extraire une analyse du sentiment spécifique à chaque mot clé. Incluez le paramètre **keywords.sentiment** en lui affectant la valeur `true`. Remplacez `{nom_utilisateur}` et `{mot_de_passe}` par vos informations.

```bash
curl --user "{nom_utilisateur}":"{mot_de_passe}" \
"https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze?version=2017-02-27&text=I%20still%20have%20a%20dream%2C%20a%20dream%20deeply%20rooted%20in%20the%20American%20dream%20%E2%80%93%20one%20day%20this%20nation%20will%20rise%20up%20and%20live%20up%20to%20its%20creed%2C%20%22We%20hold%20these%20truths%20to%20be%20self%20evident%3A%20that%20all%20men%20are%20created%20equal.&features=sentiment,keywords&keywords.sentiment=true"
```
{:pre}

## Etape 3 : Ciblez une phrase
{: #analyze-phrase}

Ciblez à présent un contenu spécifique pour examiner une analyse au niveau d'une phrase ou d'une expression (au lieu d'une analyse au niveau d'un document ou d'un mot clé) en incluant l'expression `the%20American%20dream%20` dans le paramètre **sentiment.targets**. N'oubliez pas de remplacer `{nom_utilisateur}` et `{mot_de_passe}` par vos informations.

```bash
curl --user "{nom_utilisateur}":"{mot_de_passe}" \
"https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze?version=2017-02-27&text=I%20still%20have%20a%20dream%2C%20a%20dream%20deeply%20rooted%20in%20the%20American%20dream%20one%20day%20this%20nation%20will%20rise%20up%20and%20live%20up%20to%20its%20creed%20We%20hold%20these%20truths%20to%20be%20self%20evident%3A%20that%20all%20men%20are%20created%20equal.&features=sentiment,keywords&keywords.sentiment=true&sentiment.targets=the%20American%20dream"
```
{:pre}

## Etapes suivantes
{: #next-steps}

Vous avez terminé ! Ce tutoriel ne fait qu'effleurer l'éventail de vos possibilités avec {{site.data.keyword.nlushort}}. Pour plus d'informations sur les fonctionnalités de l'API, reportez-vous aux ressources suivantes :

- Consultez la rubrique [Référence d'API ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/){: new_window} pour plus de détails et des exemples de chaque paramètre.
- Apprenez à identifier les [entités personnalisées et les relations](/docs/services/natural-language-understanding/customizing.html).
