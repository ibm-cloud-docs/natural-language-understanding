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

# Alta disponibilidad y recuperación tras desastre
{: #ha-dr}

{{site.data.keyword.nlufull}} ofrece alta disponibilidad dentro de múltiples ubicaciones de {{site.data.keyword.cloud_notm}} (por ejemplo, Dallas y Washington, DC). Sin embargo, la recuperación de desastres potenciales que afectan a toda una ubicación requiere planificación y preparación.
{: shortdesc}

Usted es el responsable de comprender su configuración, personalización y uso del servicio. También es responsable de estar preparado para volver a crear una instancia del servicio en una nueva ubicación y de restaurar los datos en cualquier ubicación. Consulte [¿Cómo puedo asegurar un tiempo de inactividad cero? ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](/docs/overview?topic=overview-zero-downtime#zero-downtime){: new_window} para obtener más información.

## Alta disponibilidad
{: #high-availability}

{{site.data.keyword.nlushort}} da soporte a alta disponibilidad sin ningún punto único de anomalía. El servicio consigue una alta disponibilidad de forma automática y transparente utilizando la característica de región multizona (MZR) proporcionada por {{site.data.keyword.cloud_notm}}.

{{site.data.keyword.cloud_notm}} habilita varias zonas que no comparten un único punto de anomalía dentro de una única ubicación. También proporciona equilibrio de carga automático entre las zonas dentro de una región.

## Recuperación tras desastre
{: #disaster-recovery}

En el caso de que se produzca un error catastrófico en una región, siga estos pasos.

- Cree una nueva instancia de servicio de {{site.data.keyword.nlushort}}.
- Ajuste el software de la aplicación para que utilice el nuevo URL y las nuevas credenciales de la instancia de servicio.
- Si utiliza {{site.data.keyword.nlushort}} con modelos personalizados de {{site.data.keyword.knowledgestudioshort}}, deberá volver a desplegar los modelos personalizados en la nueva instancia de servicio. Consulte [Copia de seguridad y restauración de datos](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-backup-restore#restoremodels) para obtener más información sobre la copia de seguridad y restauración de los datos de {{site.data.keyword.knowledgestudioshort}}. 
