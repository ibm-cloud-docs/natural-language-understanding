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

# Alta disponibilidade e recuperação de desastre
{: #ha-dr}

O {{site.data.keyword.nlufull}} é altamente disponível em vários locais do {{site.data.keyword.cloud_notm}} (por exemplo, Dallas e Washington, DC). No entanto, a recuperação de possíveis desastres que afetam todo um local requer planejamento e preparação.
{: shortdesc}

Você é responsável por entender sua configuração, customização e uso do serviço. Você também é responsável por estar pronto para recriar uma instância do serviço em uma nova localização e por restaurar seus dados em qualquer localização. Consulte [Como assegurar tempo de inatividade zero? ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](/docs/overview?topic=overview-zero-downtime#zero-downtime){: new_window} for more information.

## alta disponibilidade
{: #high-availability}

O {{site.data.keyword.nlushort}} suporta alta disponibilidade sem nenhum ponto único de falha. O serviço alcança alta disponibilidade de forma automática e transparente usando o recurso multi-zone region (MZR) fornecido pelo {{site.data.keyword.cloud_notm}}.

O {{site.data.keyword.cloud_notm}} permite diversas zonas que não compartilham um ponto único de falha em um único local. Ele também fornece balanceamento automático de carga
entre as zonas dentro de uma região.

## Recuperação de desastre
{: #disaster-recovery}

No caso de uma falha catastrófica em uma região, conclua as etapas a seguir.

- Crie uma nova instância de serviço do {{site.data.keyword.nlushort}}.
- Ajuste seu software de aplicativo para usar a nova URL da instância de serviço e as credenciais.
- Se você usar o {{site.data.keyword.nlushort}} com os modelos customizados do {{site.data.keyword.knowledgestudioshort}}, será necessário reimplementar seus modelos customizados na nova instância de serviço. Consulte [Fazendo backup e restaurando dados](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-backup-restore#restoremodels) para saber como fazer backup e restaurar dados do {{site.data.keyword.knowledgestudioshort}}. 
