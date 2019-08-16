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

# 고가용성 및 재해 복구
{: #ha-dr}

{{site.data.keyword.nlufull}}은 여러 {{site.data.keyword.cloud_notm}} 위치(예: 댈러스 및 워싱턴 DC)에서 가용성이 매우 높습니다. 그러나 전체 위치에 영향을 주는 잠재적 재해로부터 복구하려면 계획과 준비가 필요합니다.
{: shortdesc}

사용자는 서비스의 구성, 사용자 정의 및 사용에 대해 이해하고 있어야 합니다. 또한 새 위치에서 서비스의 인스턴스를 다시 작성하고 어느 위치에서든 데이터를 복원할 준비도 되어 있어야 합니다. 자세한 정보는 [작동 중단이 발생하지 않도록 하는 방법 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](/docs/overview?topic=overview-zero-downtime#zero-downtime){: new_window}을 참조하십시오. 

## 고가용성
{: #high-availability}

{{site.data.keyword.nlushort}}은 단일 실패 지점이 없는 고가용성을 지원합니다. 서비스는 {{site.data.keyword.cloud_notm}}에서 제공하는 다중 구역 지역(MZR) 기능을 사용하여 자동으로 투명하게 고가용성을 달성합니다.

{{site.data.keyword.cloud_notm}}를 사용하면 다중 구역이 단일 위치 내의 단일 실패 지점을 공유하지 않습니다. 또한 지역 내 구역 전체에 대해 자동 로드 밸런싱을 제공합니다. 

## 재해 복구
{: #disaster-recovery}

한 지역에서 치명적인 장애가 발생한 경우 다음 단계를 완료하십시오.

- 새 {{site.data.keyword.nlushort}} 서비스 인스턴스를 작성하십시오. 
- 새 서비스 인스턴스 URL 및 인증 정보를 사용하도록 애플리케이션 소프트웨어를 조정하십시오. 
- {{site.data.keyword.knowledgestudioshort}} 사용자 정의 모델과 함께 {{site.data.keyword.nlushort}}을 사용할 경우, 사용자 정의 모델을 새 서비스 인스턴스에 다시 배치해야 합니다. {{site.data.keyword.knowledgestudioshort}} 데이터 백업 및 복원 방법을 알아보려면 [데이터 백업 및 복원](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-backup-restore#restoremodels)을 참조하십시오. 
