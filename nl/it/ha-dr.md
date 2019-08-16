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

# Alta disponibilità e ripristino di emergenza 
{: #ha-dr}

{{site.data.keyword.nlufull}} è altamente disponibile con più ubicazioni {{site.data.keyword.cloud_notm}} (ad esempio, Dallas e Washington, DC). Tuttavia, il ripristino da potenziali perdite di dati che interessano un'intera ubicazione richiede pianificazione e preparazione.
{: shortdesc}

Sei responsabile della comprensione della configurazione, della personalizzazione e dell'utilizzo del servizio. Sei anche responsabile di essere pronto a ricreare un'istanza del servizio in una nuova ubicazione e ripristinare i tuoi dati in qualsiasi ubicazione. Per ulteriori informazioni, vedi [Come garantisco nessun tempo di inattività? ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](/docs/overview?topic=overview-zero-downtime#zero-downtime){: new_window}.

## Alta disponibilità (HA) 
{: #high-availability}

{{site.data.keyword.nlushort}} supporta l'alta disponibilità senza un singolo punto di errore. Il servizio ottiene l'alta disponibilità automaticamente e in modo trasparente utilizzando la funzione regione multizona (MZR) fornita da {{site.data.keyword.cloud_notm}}.

{{site.data.keyword.cloud_notm}} abilita più zone che non condividono un singolo punto di errore all'interno di una singola ubicazione. Fornisce anche il bilanciamento del carico automatico tra le zone all'interno di una regione. 

## Ripristino di emergenza 
{: #disaster-recovery}

In caso di un errore catastrofico in una regione, completa la seguente procedura.

- Crea una nuova istanza del servizio {{site.data.keyword.nlushort}}.
- Modifica il tuo software dell'applicazione in modo da utilizzare i nuovi URL e credenziali dell'istanza del servizio. 
- Se utilizzi {{site.data.keyword.nlushort}} con i modelli personalizzati {{site.data.keyword.knowledgestudioshort}}, dovrai ridistribuire i tuoi modelli personalizzati alla nuova istanza del servizio. Vedi [Backup e ripristino di dati](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-backup-restore#restoremodels) per ulteriori informazioni su come eseguire il backup e il ripristino dei dati {{site.data.keyword.knowledgestudioshort}}. 
