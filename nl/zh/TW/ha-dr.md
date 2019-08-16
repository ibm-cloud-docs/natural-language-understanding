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

# 高可用性及災難回復
{: #ha-dr}

{{site.data.keyword.nlufull}} 在多個 {{site.data.keyword.cloud_notm}} 位置內具有高可用性（例如達拉斯和華盛頓特區）。不過，若要從影響整個位置的災難回復，需要規劃與準備。
{: shortdesc}

您要負責瞭解您服務的配置、自訂作業及使用。您也要負責準備好在新的位置重建服務的實例，以及在任何位置還原資料。如需相關資訊，請參閱[如何確保運作零中斷？![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](/docs/overview?topic=overview-zero-downtime#zero-downtime){: new_window}。

## 高可用性
{: #high-availability}

{{site.data.keyword.nlushort}} 支援高可用性，而不會有單一失敗點。服務會藉由使用 {{site.data.keyword.cloud_notm}} 提供的多區域地區 (MZR) 特性而自動且明確地達到高可用性。

{{site.data.keyword.cloud_notm}} 會在單一位置內啟用不會有共同單一失敗點的多個區域。它也在一個地區內的區域之間，提供自動的負載平衡。

## 災難回復
{: #disaster-recovery}

在地區中發生災難性失敗時，請完成下列步驟。

- 建立新的 {{site.data.keyword.nlushort}} 服務實例。
- 調整您的應用軟體，以使用新的服務實例 URL 和認證。
- 如果您使用 {{site.data.keyword.nlushort}} 搭配 {{site.data.keyword.knowledgestudioshort}} 自訂模型，您將需要把自訂模型重新部署到新的服務實例。請參閱[備份及還原資料](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-backup-restore#restoremodels)，以瞭解如何備份及還原 {{site.data.keyword.knowledgestudioshort}} 資料。 
