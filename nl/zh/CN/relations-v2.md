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

# 关系类型 (V2)
{: #relation-types-version-2}

下表列出了 _V2_ 关系类型系统返回的关系类型。{{site.data.keyword.nlushort}} 使用的关系类型系统根据使用的语言而有所不同。有关更多详细信息，请参阅[关系类型系统](/docs/services/natural-language-understanding?topic=natural-language-understanding-relation-type-systems)页面。
{: shortdesc}

此关系类型系统使用的实体类型列在[实体类型 (V2)](/docs/services/natural-language-understanding?topic=natural-language-understanding-entity-types-version-2) 页面上。
{: note}

|关系             |描述|
|-----------------|----------------|
|affiliatedWith  |存在于具有亲缘关系或类似联系的两个实体之间。| 
|basedIn         |存在于某个组织与该组织的主要位置、唯一位置或固有位置之间。|
|bornAt          |个人与出生地之间存在此关系。|
|bornOn          |个人与出生日期或时间之间存在此关系。|
|clientOf        |存在于两个实体之间，其中一个实体是另一个实体的直接业务客户（即，为特定服务或产品付费）。|
|colleague       |属于同一组织的两个人之间存在此关系。|
|competitor      |参与经济竞争的两个组织之间存在此关系。|
|contactOf       |将联系人信息与某个实体相关联。|
|diedAt          |个人与其死亡地之间存在此关系。|
|diedOn          |个人与其死亡日期或时间之间存在此关系。|
|dissolvedOn     |组织或 URL 与其解散日期或时间之间存在此关系。|
|educatedAt      |个人与其接受教育的组织之间存在此关系。|
|employedBy      |存在于两个实体之间，其中一个实体因获得特定工作或服务而向另一个实体付费；必须涉及金钱上的报酬。在很多情况下，标记此关系需要掌握全球情况。|
|foundedOn       |组织或 URL 与其成立日期或时间之间存在此关系。|
|founderOf       |个人与其成立的设施、组织或 URL 之间存在此关系。|
|locatedAt       |实体与其位置之间存在此关系。|
|managerOf       |存在于某个人员与其作为工作而管理的另一个实体（例如，人员或组织）之间。|
|memberOf        |实体（例如，个人或组织）与其所属的另一个实体之间存在此关系。|
|ownerOf         |实体（例如，个人或组织）与其拥有的另一个实体之间存在此关系。所有者不必具有实体的永久所有权，此关系也能存在。|
|parentOf        |个人与其子女或继子女之间存在此关系。|
|partner         |参与经济合作的两个组织之间存在此关系。|
|partOf          |存在于同一类型或相关类型的某个较小实体与某个较大实体之间，其中第二个实体包含第一个实体。如果这两个实体都是事件，那么第一个事件必须在第二个事件的时间范围内发生，才能识别到此关系。|
|partOfMany      |类型相同或相关的较小实体与较大实体之间存在此关系，其中第二个实体（必须是复数）包含第一个实体（可以是单数或复数）。|
|populationOf    |场所与其中人数之间存在此关系，或者组织与其拥有的成员数或员工数之间存在此关系。|
|measureOf       |此关系指示实体的数量或度量（高度、重量等）。|
|relative        |两个人是亲戚时存在此关系。要识别父母、子女、兄弟姐妹和配偶，请使用 `parentOf`、`siblingOf` 和 `spouseOf` 关系。|
|residesIn       |个人与其目前或以前居住地之间存在此关系。|
|shareholdersOf  |个人或组织与另一个组织之间存在此关系，其中第一个实体是第二个实体的股东。|
|siblingOf       |个人与其兄弟姐妹或继兄弟姐妹之间存在此关系。|
|spokespersonFor |个人与其代表的设施、组织或个人之间存在此关系。|
|spouseOf        |两个人是配偶时存在此关系。|
|subsidiaryOf    |第一个组织是第二个组织的子机构时，这两个组织之间存在此关系。|
