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

# Hochverfügbarkeit und Disaster-Recovery
{: #ha-dr}

{{site.data.keyword.nlufull}} ist an mehreren {{site.data.keyword.cloud_notm}}-Standorten (z. B. Dallas und Washington, DC) hoch verfügbar. Jedoch sind für eine möglicherweise erforderliche Disaster-Recovery für einen gesamten Standort eine gewisse Planung und Vorbereitung erforderlich.
{: shortdesc}

Sie sind für die Einschätzung Ihrer Konfiguration, Anpassung und Nutzung des Service verantwortlich. Sie sind auch für die Vorbereitung zur Neuerstellung einer Instanz des Service an einem neuen Standort und für die Wiederherstellung der Daten an einem beliebigen Standort zuständig. Weitere Informationen finden Sie im Abschnitt zur [Vorgehensweise zum Sicherstellen von keinerlei Ausfallzeiten ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](/docs/overview?topic=overview-zero-downtime#zero-downtime){: new_window}.

## Hochverfügbarkeit
{: #high-availability}

{{site.data.keyword.nlushort}} unterstützt die Hochverfügbarkeit ohne Single Point of Failure. Durch die Nutzung des MZR-Features (Multi-Zone Region), das {{site.data.keyword.cloud_notm}} bereitstellt, erreicht der Service die Hochverfügbarkeit automatisch und transparent.

{{site.data.keyword.cloud_notm}} ermöglicht mehrere Zonen, die an einem einzigen Standort keinen Single Point of Failure gemeinsam nutzen. Außerdem wird in den Zonen einer Region der automatische Lastausgleich bereitgestellt.

## Disaster-Recovery
{: #disaster-recovery}

Wenn in einer Region ein Fehler aufgrund eines Katastrophenfalls auftritt, müssen Sie die folgenden Schritte ausführen.

- Erstellen Sie eine neue Instanz des Service {{site.data.keyword.nlushort}}.
- Passen Sie Ihre Anwendungssoftware so an, dass die URL und die Berechtigungsnachweise der neuen Serviceinstanz verwendet werden.
- Bei der Verwendung von {{site.data.keyword.nlushort}} mit angepassten {{site.data.keyword.knowledgestudioshort}}-Modellen müssen Sie Ihre angepassten Modelle für die neue Serviceinstanz erneut bereitstellen. Informationen zum Sichern und Wiederherstellen der {{site.data.keyword.knowledgestudioshort}}-Daten finden Sie im Abschnitt zur [Sicherung und Wiederherstellung von Daten](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-backup-restore#restoremodels). 
