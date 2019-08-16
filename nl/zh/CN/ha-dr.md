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

# 高可用性和灾难恢复
{: #ha-dr}

{{site.data.keyword.nlufull}} 在多个 {{site.data.keyword.cloud_notm}} 位置（例如达拉斯和华盛顿特区）中具有高可用性。但是，从影响整个位置的潜在灾难中恢复需要规划和准备工作。
{: shortdesc}

您负责了解服务的配置、定制和使用情况。您还负责准备好在新位置重新创建服务实例，并在任何位置中复原数据。请参阅[如何确保停机时间为零？![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](/docs/overview?topic=overview-zero-downtime#zero-downtime){: new_window} 以获取更多信息。

## 高可用性
{: #high-availability}

{{site.data.keyword.nlushort}} 支持没有单点故障的高可用性。该服务通过使用 {{site.data.keyword.cloud_notm}} 提供的多专区区域 (MZR) 功能自动且透明地实现高可用性。

{{site.data.keyword.cloud_notm}} 支持多个专区，这些专区不在单个位置中共享单点故障。它还在一个区域中的各个专区之间提供自动负载均衡。

## 灾难恢复
{: #disaster-recovery}

如果区域中发生灾难性故障，请完成以下步骤。

- 创建新 {{site.data.keyword.nlushort}} 服务实例。
- 调整应用软件以使用新服务实例 URL 和凭证。
- 如果将 {{site.data.keyword.nlushort}} 与 {{site.data.keyword.knowledgestudioshort}} 定制模型配合使用，那么需要将定制模型重新部署到新服务实例。请参阅[备份和复原数据](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-backup-restore#restoremodels)，以了解如何备份和复原 {{site.data.keyword.knowledgestudioshort}} 数据。 
