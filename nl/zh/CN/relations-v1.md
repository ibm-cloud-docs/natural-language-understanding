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

# 关系类型（版本 1）

下表列出了_V1_ 关系类型系统返回的关系类型。{{site.data.keyword.nlushort}} 使用的关系类型系统根据使用的语言不同而有所不同。
有关更多详细信息，请参阅[关系类型](relations.html)页面。
{: shortdesc}

| 关系            | 描述                                                                                                                                                                                                        |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| affectedBy      | 存在于一个实体与具有明确方向性并影响该实体的一个事件之间。                                                                                                             |
| affiliatedWith  | 存在于具有亲缘关系或类似联系的两个实体之间。|
| ageOf           | 将时效关联到一个实体。|
| agentOf         | 存在于一个实体与其中该实体根据文本扮演最活跃角色的一个事件之间。应该无需任何背景知识。|
| authorOf        | 存在于某个人员与其创建的某个 TitleWork 之间。|
| awardedBy       | 存在于某个奖项或学位与授予或颁发它的个人或组织之间。                                                                                                             |
| awardedTo       | 存在于某个奖项或学位与将其授予或颁发给的个人或组织之间。|
| basedIn         | 存在于某个组织与该组织的主要位置、唯一位置或固有位置之间。|
| before          | 表示两个时间或事件之间的时间关系“before”。仅当文本明确指定此关系时才标记。|
| bornAt          | 存在于某个人员或动物与其出生地之间。|
| bornOn          | 存在于某个人员或动物与其出生日期或时间之间。|
| capitalOf       | 存在于某个首都与其国家/地区、州或省之间。仅当文本显式声明此关系时才标记，而不基于全球知识进行标记。|
| citizenOf       | 存在于某个人员与其居住的 GeopoliticalEntity 之间。|
| clientOf        | 存在于两个实体之间，其中一个实体是另一个实体的直接业务客户（即，为特定服务或产品付费）。|
| colleague       | 存在于属于同一组织的两个人员之间。|
| competitor      | 存在于参与经济竞争的两个 GeopoliticalEntities 或组织之间。|
| contactOf       | 将联系人信息与某个实体相关联。|
| diedAt          | 存在于某个人员或动物与其死亡地之间。|
| diedOf          | 存在于某个人员或动物与其死亡原因之间。|
| diedOn          | 存在于某个人员或动物与其死亡日期或时间之间。|
| dissolvedOn     | 存在于某个实体（例如，组织）与其解散日期或时间之间。|
| educatedAt      | 存在于某个人员与其现在或过去接受教育的组织之间。|
| employedBy      | 存在于两个实体之间，其中一个实体因获得特定工作或服务而向另一个实体付费；必须涉及金钱上的报酬。在很多情况下，标记此关系需要世界知识。|
| foundedOn       | 存在于某个实体（例如，组织）与其创立日期或时间之间。|
| founderOf       | 存在于某个人员或 GeopoliticalEntity 与其创立的某个实体（例如，组织）之间。|
| hasDisease      | 指示某个人员或动物现在或过去患有疾病。|
| hasMoney        | 指示某个实体（例如，人员）现在或过去有钱。|
| instrumentOf    | 存在于某个实体（例如，武器）与现在或过去使用该实体而引发的某个事件之间。|
| locatedAt       | 存在于某个实体与其物理位置之间。|
| managerOf       | 存在于某个人员与其作为工作而管理的另一个实体（例如，人员或组织）之间。|
| measureOf       | 指示某个实体的特定度量，例如高度或重量。|
| memberOf        | 存在于某个实体（例如，人员、组织或 GeopoliticalEntity）与其所属的另一个实体之间。|
| near            | 存在于物理上彼此靠近的两个实体之间。|
| overlaps        | 指示两个时间或事件在时间上重叠。仅当文本明确指定此关系时才标记。|
| ownerOf         | 存在于某个实体（例如，人员、组织或 GeopoliticalEntity）与其永久或暂时拥有的某个实体之间。|
| parentOf        | 存在于某个人员或动物与其亲生子或继子之间。|
| participantIn   | 存在于某个参与者（例如，人员、动物、组织或 GeopoliticalEntity）与其正在或已经参与的某个事件之间。 |
| partner         | 存在于参与经济合作的两个 GeopoliticalEntity 或组织之间。|
| partOf          | 存在于同一类型或相关类型的某个较小实体与某个较大实体之间，其中第二个实体包含第一个实体。如果这些实体是事件，那么第一个事件必须在第二个事件的时间范围内发生。|
| partOfMany      | 存在于同一类型或相关类型的较小实体与较大实体之间，其中第二个实体必须为复数且包含第一个实体，而第一个实体可以由一个或多个实体组成。|
| playsRoleOf     | 存在于某个人员与其现在或过去在表演中所扮演的特定人物之间。|
| populationOf    | 存在于某个基数和某个实体（例如，组织或国家/地区）之间，其中数字表示整个人口。|
| productOf       | 存在于某个产品或 TitleWork 与生产它的组织之间。|
| quantityOf      | 指示表示第二个实体的数量的某个基数。|
| rateOf          | 存在于某个速率与该速率指定其发生频率的某个事件之间。|
| relative        | 存在于某个人员或动物与作为其亲属（当更具体的关系不恰当时）的另一个人员或动物之间。|
| residesIn       | 存在于某个生命体与其永久居住地之间。|
| shareholdersOf  | 存在于某个人员、组织或 GeopoliticalEntity 与第一个实体作为其股东的某个组织之间。|
| siblingOf       | 存在于某个人员或动物与其亲兄弟姐妹或继兄弟姐妹之间。|
| spokespersonFor | 存在于某个人员与其代表的某个实体之间。仅当文本显式声明此关系时才标记，而不基于全球知识进行标记。|
| spouseOf        | 存在于作为正式配偶的两个人员之间。|
| subsidiaryOf    | 存在于两个组织之间，其中第一个组织是第二个组织的子机构，这意味着第一个实体虽然受第二个实体的控制，但拥有相当程度的自主权。|
| timeOf          | 指示发生某个事件的日期、时间或持续时间；发布、执行或广播了某个 TitleWork；或者首次起草、创立、通过或废除了某项法律。|

## 对于关系而言唯一的实体类型

_版本 1_ 关系类型系统中涉及的实体类型与缺省实体类型系统中涉及的实体类型不同。您可以在 `entities` 功能部件的 `model` 参数中指定以下某个关系实体模型，以替代缺省实体检测模型。

|模型标识|描述|
|--------|-----------|
|ar-news|阿拉伯语新闻|
|en-news|英语新闻|
|es-news|西班牙语新闻|

使用 `relations` 模型可以识别以下实体：

|实体类型|
|---|
|Age|
|Anatomy|
|Animal|
|Award|
|Cardinal|
|Crime|
|Date|
|Degree|
|Duration|
|EmailAddress|
|Event|
|EventBusiness|
|EventCommunication|
|EventCustody|
|EventDemonstration|
|EventEducation|
|EventElection|
|EventGathering|
|EventLegal|
|EventLegislation|
|EventMeeting|
|EventPerformance|
|EventPersonnel|
|EventViolence|
|Facility|
|Food|
|GeographicFeature|
|GeopoliticalEntity|
|HealthCondition|
|Law|
|Location|
|Money|
|Measure|
|NaturalEvent|
|Organization|
|Ordinal|
|Percent|
|Person|
|Phone|
|Plant|
|Product|
|SportingEvent|
|Substance|
|Ticker|
|Time|
|TitleWork|
|Vehicle|
|Weapon|
|Weather|
|Web|

