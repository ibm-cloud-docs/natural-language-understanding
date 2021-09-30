---

copyright:
  years: 2019, 2021
lastupdated: "2021-09-30"

subcollection: natural-language-understanding

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}

# High availability and disaster recovery
{: #ha-dr}

{{site.data.keyword.nlufull}} is highly available within multiple {{site.data.keyword.cloud_notm}} locations (for example, Dallas and Washington, DC). However, recovering from potential disasters that affect an entire location requires planning and preparation.
{: shortdesc}

You are responsible for understanding your configuration, customization, and usage of the service. You are also responsible for being ready to re-create an instance of the service in a new location and to restore your data in any location. See [How do I ensure zero downtime? ![External link icon](../../icons/launch-glyph.svg "External link icon")](/docs/overview?topic=overview-zero-downtime#zero-downtime){: new_window} for more information.

## High availability
{: #high-availability}

{{site.data.keyword.nlushort}} supports high availability with no single point of failure. The service achieves high availability automatically and transparently by using the multi-zone region (MZR) feature provided by {{site.data.keyword.cloud_notm}}.

{{site.data.keyword.cloud_notm}} enables multiple zones that do not share a single point of failure within a single location. It also provides automatic load balancing across the zones within a region.

## Disaster recovery
{: #disaster-recovery}

In the event of a catastrophic failure in a region, complete the following steps.

- Create a new {{site.data.keyword.nlushort}} service instance.
- Adjust your application software to use the new service instance URL and credentials.
- If you use {{site.data.keyword.nlushort}} with {{site.data.keyword.knowledgestudioshort}} custom models, you will need to redeploy your custom models to the new service instance. See [Backing up and restoring data](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-backup-restore#restoremodels) to learn how to backup and restore {{site.data.keyword.knowledgestudioshort}} data. 
