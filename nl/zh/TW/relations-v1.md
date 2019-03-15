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

# 關係類型（第 1 版）
{: #relation-types-version-1}

下表列出_第 1 版_ 關係類型系統所傳回的關係類型。根據所使用的語言，{{site.data.keyword.nlushort}} 使用的關係類型系統會有所不同。如需詳細資料，請參閱[關係類型系統](/docs/services/natural-language-understanding?topic=natural-language-understanding-relation-type-systems)頁面。
{: shortdesc}

在_第 1 版_ 類型系統中，關係結果中的實體類型不同於實體結果中傳回的實體類型。若要查看_第 1 版_ 關係中所使用的實體類型清單，請參閱[實體類型（第 1 版）](/docs/services/natural-language-understanding?topic=natural-language-understanding-entity-types-version-1#relations-entity-types)頁面。
{: note}

|關係            |說明|
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|affectedBy      |存在於實體與具有明確方向性且會影響該實體的事件之間。                                                                                                                        |
|affiliatedWith  |存在於具有連結或以類似方式連接的兩個實體之間。                                                                                                                                          |
|ageOf           |讓經歷時間與實體相關。                                                                                                                                                                  |
|agentOf         |存在於實體與該實體在其中根據文字擔任最活躍角色的事件之間。應該不需要背景知識。                                                                                                                  |
|authorOf        |存在於人員與其所建立的 TitleWork 之間。                                                                                                                                                 |
|awardedBy       |存在於 Award 或 Degree 與頒予或授予它的人員或組織之間。                                                                                                                             |
|awardedTo       |存在於 Award 或 Degree 與它頒予或授予的人員或組織之間。                                                                                                                                 |
|basedIn         |存在於 Organization 與其主要、唯一或本質上所在位置之間。                                                                                                                            |
|before          |表示兩個 Time 或 Event 之間的 "before" 時間關係。只有在文字明確指定關係時才加以標示。                                                                                      |
|bornAt          |存在於 Person 或 Animal 與其出生地之間。                                                                                                                                    |
|bornOn          |存在於 Person 或 Animal 與其出生 Date 或 Time 之間。                                                                                                                          |
|capitalOf       |存在於資本與其國家/地區、州/省或縣/市之間。只有在文字明確指出關係時才加以標示，並非以全球知識為基礎。                                                                                       |
|citizenOf       |存在於人員與其為公民的 GeopoliticalEntity 之間。                                                                                                                                        |
|clientOf        |某個實體是另一個實體的直接商業客戶（亦即，支付特定服務或產品的費用）時，存在於這兩個實體之間。                                                                                        |
|colleague       |存在於兩個屬於相同 Organization 的 People 之間。                                                                                                                                        |
|competitor      |存在於經濟競爭中的兩個 GeopoliticalEntity 或 Organization 之間。                                                                                                                        |
|contactOf       |讓聯絡資訊與實體相關。                                                                                                                                                                  |
|diedAt          |存在於 Person 或 Animal 與其死亡地點之間。                                                                                                                                              |
|diedOf          |存在於 Person 或 Animal 與其死亡原因之間。                                                                                                                                              |
|diedOn          |存在於 Person 或 Animal 與其死亡 Date 或 Time 之間。                                                                                                                                    |
|dissolvedOn     |存在於實體（例如 Organization）與其解散 Date 或 Time 之間。                                                                                                                                  |
|educatedAt      |存在於 Person 與其受教育的 Organization 之間。                                                                                                                                    |
|employedBy      |某個實體支付另一個實體的特定工作或服務費用時，存在於這兩個實體之間；必須包含酬金。在許多情況下，標示此關係需要全球知識。                                                                |
|foundedOn       |存在於實體（例如 Organization）與其創辦 Date 或 Time 之間。                                                                                                                             |
|founderOf       |存在於 Person 或 GeopoliticalEntity 與實體（例如，其所創辦的 Organization）之間。                                                                                                           |
|hasDisease      |指出 Person 或 Animal 具有或曾有 Disease。                                                                                                                                              |
|hasMoney        |指出實體（例如人員）具有或曾有 Money。                                                                                                                                                |
|instrumentOf    |存在於實體（例如 Weapon）與使用該實體而引起的 Event 之間。                                                                                                                            |
|locatedAt       |存在於實體與其實際位置之間。                                                                                                                                                            |
|managerOf       |存在於某個 Person 與另一個實體（例如，該人員在工作上管理的 Person 或 Organization）之間。                                                                                             |
|measureOf       |指出特定 Measure，例如實體的高度或重量。                                                                                                                                              |
|memberOf        |存在於某個實體（例如，Person、Organization 或 GeopoliticalEntity）與其所屬的另一個實體之間。                                                                                            |
|near            |存在於實際上彼此位置很接近的兩個實體之間。                                                                                                                                      |
|overlaps        |指出兩個 Time 或 Event 的時間重疊。只有在文字明確指定關係時才加以標示。                                                                                      |
|ownerOf         |存在於實體（例如，Person、Organization 或 GeopoliticalEntity）與其永久或暫時擁有的實體之間。                                                                                            |
|parentOf        |存在於 Person 或 Animal 與其子女或繼子女之間。                                                                                                                                            |
|participantIn   |存在於參與者（例如，Person、Animal、Organization 或 GeopoliticalEntity）與其正參與或已參與的 Event 之間。                                                                               |
|partner         |存在於經濟合作中的兩個 GeopoliticalEntity 或 Organization 之間。                                                                                                                        |
|partOf          |存在於相同類型或相關類型的一個較小實體與一個較大實體之間，其中第二個實體包含第一個實體。如果實體是 Event，則第一個實體必須在第二個實體的時間跨距內發生。                                                |
|partOfMany      |存在於相同類型或相關類型的多個較小實體與較大實體之間，其中第二個實體必須是複數，它包含第一個實體，第一個實體可以由一個以上的實體組成。|
|playsRoleOf     |存在於 Person 與其在績效中扮演的特定角色之間。                                                                                                                                  |
|populationOf    |存在於 Cardinal 與實體（例如，該數字代表其整個人口的組織或國家/地區）之間。                                                                                                                 |
|productOf       |存在於 Product 或 TitleWork 與產生它的 Organization 之間。                                                                                                                              |
|quantityOf      |指出其為第二個實體之數量或金額的 Cardinal。                                                                                                                                               |
|rateOf          |存在於 Rate 與其指定出現頻率的事件之間。                                                                                                                                                |
|relative        |當更具體的關係不適當時，存在於某個 Person 或 Animal 與身為其親屬的另一個 Person 或 Animal 之間。                                                                                            |
|residesIn       |存在於存活實體與其永遠居住位置之間。                                                                                                                                                    |
|shareholdersOf  |存在於 Person、Organization 或 GeopoliticalEntity 與第一個實體為其股東的 Organization 之間。                                                                                              |
|siblingOf       |存在於 Person 或 Animal 與其兄弟姊妹或繼兄弟姊妹之間。                                                                                                                                  |
|spokespersonFor |存在於 Person 與其代表的實體之間。只有在文字明確指出關係時才加以標示，並非以全球知識為基礎。                                                                                       |
|spouseOf        |存在於為正式配偶的兩個 People 之間。                                                                                                                                                    |
|subsidiaryOf    |第一個實體是第二個實體的子公司時，存在於兩個 Organization 之間，表示儘管受到第二個實體的控制，第一個實體還是具有一定的自主權。                                                      |
|timeOf          |指出發生事件的 Date、Time 或 Duration；已發佈、執行或播送 TitleWork；或初次起草、建立、通過或廢除 Law。                                                                               |
