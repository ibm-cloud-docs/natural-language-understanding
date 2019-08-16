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

# 高可用性と災害復旧
{: #ha-dr}

{{site.data.keyword.nlufull}} は、複数の {{site.data.keyword.cloud_notm}} のロケーション (ダラスやワシントン DC など) で高可用性が確保されています。しかし、ロケーション全体が影響を受ける可能性のある災害から復旧するためには、計画と準備が必要です。
{: shortdesc}

サービスの構成、カスタマイズ、使用法を把握しておく必要があります。新しいロケーションでサービスのインスタンスを再作成し、すべてのロケーションのデータを復元できるように準備しておく必要もあります。詳しくは、[ダウン時間をゼロにする方法 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](/docs/overview?topic=overview-zero-downtime#zero-downtime){: new_window} を参照してください。

## 高可用性
{: #high-availability}

{{site.data.keyword.nlushort}} は高可用性をサポートしており、単一障害点は存在しません。このサービスは、{{site.data.keyword.cloud_notm}} に用意されている複数ゾーン地域 (MZR) 機能を使用して、高可用性を自動的かつ透過的に実現します。

{{site.data.keyword.cloud_notm}} では、1 つのロケーション内で、単一障害点を共有しない複数のゾーンを利用できます。1 つの地域の複数のゾーン間で自動的にロード・バランシングを行うこともできます。

## 災害復旧
{: #disaster-recovery}

ある地域で壊滅的な障害が発生した場合は、以下のステップを実行してください。

- 新しい {{site.data.keyword.nlushort}} サービス・インスタンスを作成します。
- 新しいサービス・インスタンス URL と資格情報を使用するようにアプリケーション・ソフトウェアを調整します。
- {{site.data.keyword.nlushort}} と {{site.data.keyword.knowledgestudioshort}} カスタム・モデルを併用する場合は、カスタム・モデルを新しいサービス・インスタンスに再デプロイする必要があります。{{site.data.keyword.knowledgestudioshort}} データのバックアップとリストアの方法については、[データのバックアップおよびリストア](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-backup-restore#restoremodels)を参照してください。 
