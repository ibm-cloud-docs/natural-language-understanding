---

copyright:
  years: 2015, 2017
lastupdated: "2018-03-16"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}

# 关系类型 (V2)

下表列出了 _V2_ 关系类型系统返回的关系类型。{{site.data.keyword.nlushort}} 使用的关系类型系统根据使用的语言而有所不同。有关更多详细信息，请参阅[关系类型](relations.html)页面。
{: shortdesc}

此关系类型系统使用的实体类型列在[实体类型和子类型 (V2)](entity-types-v2.html) 页面上。

| 关系| 描述|
|-----------------|----------------|
| affiliatedWith  | 具有亲缘关系或以类似方式连接的两个实体之间存在此关系。| 
| basedIn         | 组织与该组织的主要位置、唯一位置或固有位置之间存在此关系。|
| bornAt          | 个人与出生地之间存在此关系。|
| bornOn          | 个人与出生日期或时间之间存在此关系。|
| clientOf        | 一个实体是另一个实体的直接业务客户（即，付费购买特定服务或产品）时，这两个实体之间存在此关系。|
| colleague       | 属于同一组织的两个人之间存在此关系。|
| competitor      | 参与经济竞争的两个组织之间存在此关系。|
| contactOf       | 将联系人信息与实体相关联。|
| diedAt          | 个人与其死亡地之间存在此关系。|
| diedOn          | 个人与其死亡日期或时间之间存在此关系。|
| dissolvedOn     | 组织或 URL 与其解散日期或时间之间存在此关系。|
| educatedAt      | 个人与其接受教育的组织之间存在此关系。|
| employedBy      | 一个实体向另一个实体付费购买特定工作或服务时，这两个实体之间存在此关系；必须涉及金钱奖励。在很多情况下，标记此关系需要掌握全球情况。|
| foundedOn       | 组织或 URL 与其成立日期或时间之间存在此关系。|
| founderOf       | 个人与其成立的设施、组织或 URL 之间存在此关系。|
| locatedAt       | 实体与其位置之间存在此关系。|
| managerOf       | 个人与其在工作中管理的其他实体（例如，个人或组织）之间存在此关系。|
| memberOf        | 实体（例如，个人或组织）与其所属的另一个实体之间存在此关系。|
| ownerOf         | 实体（例如，个人或组织）与其拥有的另一个实体之间存在此关系。所有者不必具有实体的永久所有权，此关系也能存在。|
| parentOf        | 个人与其子女或继子女之间存在此关系。|
| partner         | 参与经济合作的两个组织之间存在此关系。|
| partOf          | 类型相同或相关的较小实体与较大实体之间存在此关系，其中第二个实体包含第一个实体。如果这两个实体都是事件，那么第一个事件必须在第二个事件的时间范围内发生，才能识别到此关系。|
| partOfMany      | 类型相同或相关的较小实体与较大实体之间存在此关系，其中第二个实体（必须是复数）包含第一个实体（可以是单数或复数）。|
| populationOf    | 场所与其中人数之间存在此关系，或者组织与其拥有的成员数或员工数之间存在此关系。|
| measureOf       | 此关系指示实体的数量或度量（高度、重量等）。|
| relative        | 两个人是亲戚时存在此关系。要识别父母、子女、兄弟姐妹和配偶，请使用 `parentOf`、`siblingOf` 和 `spouseOf` 关系。|
| residesIn       | 个人与其目前或以前居住地之间存在此关系。|
| shareholdersOf  | 个人或组织与另一个组织之间存在此关系，其中第一个实体是第二个实体的股东。|
| siblingOf       | 个人与其兄弟姐妹或继兄弟姐妹之间存在此关系。|
| spokespersonFor | 个人与其代表的设施、组织或个人之间存在此关系。|
| spouseOf        | 两个人是配偶时存在此关系。|
| subsidiaryOf    | 第一个组织是第二个组织的子机构时，这两个组织之间存在此关系。|
