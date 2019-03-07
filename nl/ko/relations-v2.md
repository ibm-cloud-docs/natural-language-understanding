---

copyright:
  years: 2015, 2019
lastupdated: "2019-02-25"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:pre: .pre}
{:note: .note}
{:codeblock: .codeblock}
{:screen: .screen}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}

# 관계 유형(버전 2)
{: #relation-types-version-2}

다음 표에서는 _버전 2_ 관계 유형 시스템에서 리턴한 관계 유형을 나열합니다. {{site.data.keyword.nlushort}}에서 사용하는 관계 유형 시스템은 사용하는 언어에 따라 다릅니다. 자세한 내용은 [관계 유형 시스템](/docs/services/natural-language-understanding?topic=natural-language-understanding-relation-type-systems) 페이지를 참조하십시오.
{: shortdesc}

이 관계 유형 시스템에서 사용하는 엔티티 유형은 [엔티티 유형(버전 2)](/docs/services/natural-language-understanding?topic=natural-language-understanding-entity-types-version-2) 페이지에 나열되어 있습니다.
{: note}

|관계        |설명 |
|-----------------|----------------|
|affiliatedWith  |제휴를 맺었거나 유사하게 연결된 두 엔티티 사이에 존재합니다. | 
|basedIn         |조직과 해당 조직이 주로, 유일하게 또는 고유하게 위치하는 장소 사이에 존재합니다. |
|bornAt          |개인과 해당 개인이 태어난 장소 사이에 존재합니다. |
|bornOn          |개인과 해당 개인이 태어난 날짜 또는 시간 사이에 존재합니다. |
|clientOf        |한 엔티티가 다른 엔티티의 직접적인 비즈니스 클라이언트인 경우(즉, 특정 서비스나 제품에 대해 비용 지급) 두 엔티티 사이에 존재합니다. |
|colleague       |동일한 조직에 속한 두 개인 사이에 존재합니다. |
|competitor      |경제적 경쟁에 참여하고 있는 두 조직 사이에 존재합니다. |
|contactOf       |연락처 정보를 엔티티와 관련시킵니다. |
|diedAt          |개인과 해당 개인이 죽은 장소 사이에 존재합니다. |
|diedOn          |개인과 해당 개인이 죽은 날짜 또는 시간 사이에 존재합니다. |
|dissolvedOn     |조직 또는 URL과 해당 조직 또는 URL이 해체된 날짜 또는 시간 사이에 존재합니다. |
|educatedAt      |개인과 해당 개인이 교육을 받고 있거나 받은 조직 사이에 존재합니다.|
|employedBy      |한 엔티티가 다른 엔티티에게 특정 작업 또는 서비스에 대해 비용을 지불할 때 두 엔티티 사이에 존재합니다. 이때 금전적 보상이 있어야 합니다. 대부분의 경우 이 관계를 표시하려면 세계 정세에 관한 지식이 필요합니다. |
|foundedOn       |조직 또는 URL과 해당 조직 또는 URL이 설립된 날짜 또는 시간 사이에 존재합니다. |
|founderOf       |개인과 해당 개인이 설립한 시설, 조직 또는 URL 사이에 존재합니다. |
|locatedAt       |엔티티와 해당 위치 사이에 존재합니다. |
|managerOf       |개인과 해당 개인이 업무상 관리하는 개인 또는 조직과 같은 다른 엔티티 사이에 존재합니다. |
|memberOf        |개인이나 조직과 같은 엔티티와 해당 엔티티가 속한 다른 엔티티 사이에 존재합니다. |
|ownerOf         |개인이나 조직과 같은 엔티티와 해당 엔티티가 소유한 엔티티 사이에 존재합니다. 소유자에게 엔티티의 영구 소유권이 없어도 관계가 존재할 수 있습니다. |
|parentOf        |개인과 해당 개인의 자녀 또는 의붓자녀 사이에 존재합니다. |
|partner         |경제적 협력에 참여하고 있는 두 조직 사이에 존재합니다. |
|partOf          |유형이 같거나 유형이 연관되어 있으며 두 번째 엔티티가 첫 번째 엔티티를 포함하는 상대적으로 소규모이고 대규모인 엔티티 사이에 존재합니다. 엔티티가 둘 다 이벤트이면 첫 번째 엔티티가 두 번째 엔티티의 시간 범위 내에 발생해야 관계가 인식됩니다. |
|partOfMany      |유형이 같거나 유형이 연관되어 있으며 상대적으로 소규모와 대규모인 엔티티 사이에 존재합니다. 이때 두 번째 엔티티는 복수로 구성되어야 하며, 단수이거나 복수로 구성될 수 있는 첫 번째 엔티티를 포함합니다. |
|populationOf    |장소와 해당 장소에 있는 사람의 수 또는 조직과 해당 조직에 있는 구성원 또는 직원의 수 사이에 존재합니다. |
|measureOf      |이 관계는 엔티티의 수량 또는 엔티티의 수치(높이, 중량 등)를 표시합니다. |
|relative        |서로 친척 관계인 두 개인 사이에 존재합니다. 부모, 자녀, 형제자매 및 부부를 식별하려면 `parentOf`, `siblingOf` 및 `spouseOf` 관계를 사용하십시오. |
|residesIn       |개인과 해당 개인이 살고 있거나 이전에 살았던 장소 사이에 존재합니다. |
|shareholdersOf  |개인 또는 조직과 첫 번째 엔티티가 주주인 조직 사이에 존재합니다. |
|siblingOf       |개인과 해당 개인의 형제자매 또는 의붓형제자매 사이에 존재합니다.     |
|spokespersonFor |개인과 해당 개인이 대표하는 시설, 조직 또는 사람 사이에 존재합니다.  |
|spouseOf        |부부인 두 개인 사이에 존재합니다. |
|subsidiaryOf    |첫 번째가 두 번째의 자회사인 두 조직 사이에 존재합니다. |
