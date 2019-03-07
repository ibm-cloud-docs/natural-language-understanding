---

copyright:
  years: 2015, 2018
lastupdated: "2018-11-08"

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

# Tarification
{: #pricing}

{{site.data.keyword.nlushort}} inclut trois plans de tarification (Lite, Standard et Premium).

Les informations de tarification de cette page sont indiquées en dollars américains. Pour accéder à des informations dans votre devise locale, consultez la page [{{site.data.keyword.nlushort}}](https://{DomainName}/catalog/services/natural-language-understanding) dans le catalogue {{site.data.keyword.cloud}}.
{: tip}

## Lite
{: #lite}

Le plan Lite est gratuit pour les utilisateurs qui souhaitent tester Natural Language Understanding ou effectuer une démonstration de faisabilité.

**Tarification**
- 30 000 éléments NLU gratuits/mois

**Modèle personnalisé**
- 1 modèle personnalisé gratuit

## Standard
{: #standard}

Plan de "paiement à la carte" recommandé une fois que vous êtes prêt à faire passer votre application de la démonstration de faisabilité à la production.

**Tarification** (facturation mensuelle)
- Niveau 1 : 0,003 $/élément NLU pour les 250 000 premiers éléments NLU
- Niveau 2 : 0,001 $/élément NLU pour les éléments NLU allant du 250 001e au 5 000 000e  
- Niveau 3 : 0,0002 $/élément NLU pour tout élément NLU supplémentaire

**Modèle personnalisé** ($/modèle personnalisé/mois)
- 800 $ pour tous les niveaux

## Premium
{: #premium}

Plan offrant un niveau de sécurité et d'isolement élevé permettant aux clients de répondre aux exigences en matière de données sensibles.

_Pour plus de détails, [contactez notre équipe de ventes](https://www.ibm.com/account/reg/us-en/signup?formid=MAIL-watson)._

## Qu'est-ce qu'un élément NLU ?
{: #nlu-items}

L'utilisation de l'API est mesurée en **éléments NLU**. Un élément NLU est une **unité de texte** (jusqu'à 10 000 caractères) analysée pour une **fonction**, comme sentiment.

Pour garder le suivi du nombre d'éléments NLU dans votre demande, vous pouvez examiner l'objet `usage` dans la réponse. Par exemple, l'analyse de 15 000 caractères de texte à la recherche de sentiment, d'émotion et de mots clés va renvoyer les informations d'utilisation suivantes. 

```json
"usage": {
  "text_units": 2,
  "text_characters": 15000,
  "features": 3
}
```
{: code}
  
Il existe **2** unités de texte et **3** fonctions dans la demande, donc **2 × 3 = 6** éléments NLU.

Les unités de texte sont comptabilisées séparément pour chaque demande. Si une demande analyse 15 000 caractères et qu'une autre demande analyse 3 000 caractères, 3 unités de texte au total sont comptabilisées. La première demande inclut deux unités de texte et la deuxième une unité de texte.

## FAQ
{: #faq}

### Je souhaite connaître le sentiment se dégageant de 20 000 tweets. Comment puis-je estimer ce que je vais payer dans le plan Standard ?

- Etape 1 : Calculer le nombre d'unités de texte par demande<br>
Depuis novembre 2018, le nombre maximal de caractères autorisés dans un tweet est de 280.<br>
Cela correspond à une unité de texte par demande.

- Etape 2 : Calculer le nombre de fonctions par demande<br>
Une fonction, sentiment, est activée dans chaque demande.

- Etape 3 : Calculer le nombre d'éléments NLU par demande<br>
Eléments NLU = (Nombre d'unités de texte) × (Nombre de fonctions)<br>
Eléments NLU = 1 unité de texte × 1 fonction = 1 élément NLU

- Etape 4 : Calculer le nombre total d'éléments NLU <br>
Nombre total d'éléments NLU = (Nombre de demandes) × (Nombre d'éléments NLU par demande) <br>
Nombre total d'éléments NLU = 20 000 demandes × 1 élément NLU par demande = 20 000 éléments NLU au total

- Etape 5 : Estimer le prix pour le nombre total d'éléments NLU<br>
Pour le plan de tarification Standard, les frais sont de 0,003 $ par élément pour les 250 000 premiers éléments NLU<br>
Prix estimé = (Nombre d'éléments NLU) × (Prix par élément NLU) <br>
Prix estimé = 20 000 éléments NLU × 0,003 $ = 60 $

**Coût total = 60 $**

### Je souhaite extraire les entités, les mots clés et les catégories pour 50 000 documents avec une moyenne de 12 000 caractères par document. Quel sera le prix estimé pour le plan Standard ?
- Etape 1 : Calculer le nombre d'unités de texte par demande <br>
Unités de texte = Nombre de groupes de 10 000 caractères ou moins <br>
12 000 caractères par demande = 2 unités de texte par demande

- Etape 2 : Calculer le nombre de fonctions par demande<br>
Entités, mots clés, catégories = 3 fonctions

- Etape 3 : Calculer le nombre d'éléments NLU par demande <br>
Eléments NLU = (Nombre d'unités de texte) × (Nombre de fonctions) <br>
Eléments NLU = 2 unités de données × 3 enrichissements = 6 éléments NLU

- Etape 4 : Calculer le nombre total d'éléments NLU <br>
Nombre total d'éléments NLU = (Nombre de demandes ou de documents) × (Nombre d'éléments NLU) <br>
Nombre total d'éléments NLU = 50 000 demandes × 6 éléments NLU = 300 000 éléments NLU

- Etape 5 : Estimer le prix pour le nombre total d'éléments NLU <br>
Les frais sont de 0,003 $ par élément pour les 250 000 premiers éléments NLU<br>
Les éléments NLU suivants jusqu'au 5 000 000e sont facturés au prix de 0,001 $ par élément<br>
Prix estimé = (250 000 éléments NLU × 0,003 $) + (50 000 éléments NLU × 0,001 $) <br>
Prix estimé = 750 $ + 50 $


**Coût total = 800 $**

### Comment calculer le prix du plan standard pour 15 000 éléments NLU ?
- Etant donné que les 250 000 premiers éléments NLU sont facturés au prix de 0,003 $/élément, vos 15 000 éléments NLU sont facturés au prix de 0,003 $ par élément (Niveau 1). Votre prix estimé sera de 45 $. 

### Comment calculer le prix du plan Standard pour 6 000 000 éléments NLU ?
- Etant donné que vous avez plus de 5 000 000 éléments NLU, vos 250 000 premiers éléments NLU sont facturés au prix de 0,003 $ par élément (Niveau 1), vos 4 750 000 éléments NLU suivants sont facturés au prix de 0,001 $ par élément (Niveau 2) et les 1 000 000 éléments NLU restants sont facturés au prix de 0,0002 $ par élément (Niveau 3). Votre prix estimé sera de 5 700 $. 



