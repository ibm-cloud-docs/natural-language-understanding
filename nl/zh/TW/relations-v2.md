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

# 關係類型（第 2 版）

下表列出_第 2 版_ 關係類型系統所傳回的關係類型。根據所使用的語言，{{site.data.keyword.nlushort}} 使用的關係類型系統會有所不同。如需詳細資料，請參閱[關係類型](relations.html)頁面。
{: shortdesc}

此關係類型系統所使用的實體類型列在[實體類型及子類型（第 2 版）](entity-types-v2.html)頁面上。

| 關係            | 說明        |
|-----------------|----------------|
| affiliatedWith  | 存在於具有連結或以類似方式連接的兩個實體之間。                                                                                                                                          | 
| basedIn         | 存在於 Organization 與其主要、唯一或本質上所在位置之間。                                                                                                                            |
| bornAt          | 存在於 Person 與其出生地點之間。|
| bornOn          | 存在於 Person 與其出生 Date 或 Time 之間。|
| clientOf        | 某個實體是另一個實體的直接商業客戶（亦即，支付特定服務或產品的費用）時，存在於這兩個實體之間。|
| colleague       | 存在於兩個屬於相同 Organization 的 Person 之間。|
| competitor      | 存在於經濟競爭中的兩個 Organization 之間。|
| contactOf       | 讓聯絡資訊與實體相關。|
| diedAt          | 存在於 Person 與其死亡地點之間。|
| diedOn          | 存在於 Person 與其死亡 Date 或 Time 之間。|
| dissolvedOn     | 存在於 Organization 或 URL 與其解散 Date 或 Time 之間。|
| educatedAt      | 存在於 Person 與其受教育的 Organization 之間。|
| employedBy      | 某個實體支付另一個實體的特定工作或服務費用時，存在於這兩個實體之間；必須包含酬金。在許多情況下，標示此關係需要全球知識。|
| foundedOn       | 存在於 Organization 或 URL 與其創辦 Date 或 Time 之間。|
| founderOf       | 存在於 Person 與其所創辦的 Facility、Organization 或 URL 之間。|
| locatedAt       | 存在於實體與其位置之間。|
| managerOf       | 存在於某個 Person 與另一個實體（例如，該人員在工作上管理的 Person 或 Organization）之間。|
| memberOf        | 存在於某個實體（例如，Person 或 Organization）與其所屬的另一個實體之間。|
| ownerOf         | 存在於某個實體（例如，Person 或 Organization）與其所擁有的實體之間。擁有者不需要具有實體的永久所有權，關係就能存在。|
| parentOf        | 存在於 Person 與其子女或繼子女之間。|
| partner         | 存在於經濟合作中的兩個 Organization 之間。|
| partOf          | 存在於相同類型或相關類型的一個較小實體與一個較大實體之間，其中第二個實體包含第一個實體。如果實體都是事件，則第一個實體必須在第二個實體的時間跨距內發生，才能辨識關係。|
| partOfMany      | 存在於相同類型或相關類型的多個較小實體與較大實體之間，其中第二個實體必須是複數，它包含第一個實體，第一個實體可以是單數或複數。|
| populationOf    | 存在於位置與該處人數之間，或組織與其成員或員工數目之間。|
| measureOf      | 此關係指出實體的數量或實體的測量（高度、重量等等）。|
| relative        | 存在於為親屬的兩個 Person 之間。若要識別父母、子女、兄弟姊妹及配偶，請使用 `parentOf`、`siblingOf` 及 `spouseOf` 關係。|
| residesIn       | 存在於 Person 與其目前居住地點或先前居住地點之間。|
| shareholdersOf  | 存在於 Person 或 Organization 與第一個實體為其股東的 Organization 之間。|
| siblingOf       | 存在於 Person 與其兄弟姊妹或繼兄弟姊妹之間。|
| spokespersonFor | 存在於 Person 與其代表的 Facility、Organization 或 Person 之間。|
| spouseOf        | 存在於為配偶的兩個 Person 之間。|
| subsidiaryOf    | 第一個實體是第二個實體的子公司時，存在於兩個 Organization 之間。|
