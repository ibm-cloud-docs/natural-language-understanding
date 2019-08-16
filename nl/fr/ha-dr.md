---

copyright:
  years: 2019
lastupdated: "2019-03-15"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}

# Haute disponibilité et récupération après sinistre
{: #ha-dr}

{{site.data.keyword.nlufull}} est hautement disponible dans plusieurs emplacements {{site.data.keyword.cloud_notm}} (par exemple, Dallas et Washington, DC). Cependant, la reprise après des incidents potentiels qui affectent un site entier nécessite une planification et une préparation.
{: shortdesc}

Il vous appartient de bien connaître la configuration, la personnalisation et l'utilisation du service. Vous êtes également tenu d'être prêt à recréer une instance du service sur un nouveau site et à restaurer vos données sur n'importe quel site. Voir [Comment garantir une disponibilité permanente ? ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](/docs/overview?topic=overview-zero-downtime#zero-downtime){: new_window} Pour plus d'informations.

## Haute disponibilité
{: #high-availability}

{{site.data.keyword.nlushort}} prend en charge la haute disponibilité sans aucun point de défaillance unique. Ce service assure automatiquement et de manière transparente la haute disponibilité à l'aide de la fonctionnalité MZR (régions multi-zones) fournie par {{site.data.keyword.cloud_notm}}.

{{site.data.keyword.cloud_notm}} active plusieurs zones qui ne partagent pas un point de défaillance unique au sein du même site. Il fournit également un équilibrage automatique de la charge entre les zones d'une région. 

## Reprise après incident
{: #disaster-recovery}

Dans l'éventualité d'un incident grave dans une région, procédez comme suit :

- Créez une instance de service {{site.data.keyword.nlushort}}.
- Ajustez votre logiciel d'application pour qu'il utilise l'URL et les données d'identification de la nouvelle instance de service.
- Si vous utilisez {{site.data.keyword.nlushort}} avec des modèles personnalisés {{site.data.keyword.knowledgestudioshort}}, vous n'avez pas besoin de redéployer vos modèles personnalisés sur la nouvelle instance de service. Voir [Sauvegarde et restauration de données](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-backup-restore#restoremodels) pour savoir comment sauvegarder des données {{site.data.keyword.knowledgestudioshort}}. 
