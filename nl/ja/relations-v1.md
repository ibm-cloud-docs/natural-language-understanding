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

# 関係タイプ (バージョン 1)
{: #relation-types-version-1}

下表に、_バージョン 1_ 関係タイプ・システムで返される関係タイプを示します。 使用している言語によって、{{site.data.keyword.nlushort}} で使用される関係タイプ・システムは異なります。 詳しくは、[関係タイプ・システム](/docs/services/natural-language-understanding?topic=natural-language-understanding-relation-type-systems)ページを参照してください。
{: shortdesc}

_バージョン 1_ タイプ・システムでは、関係の結果に含まれるエンティティー・タイプと、エンティティーの結果で返されるエンティティー・タイプは異なります。 _バージョン 1_ の関係で使用されるエンティティー・タイプのリストについては、[エンティティー・タイプ (バージョン 1)](/docs/services/natural-language-understanding?topic=natural-language-understanding-entity-types-version-1#relations-entity-types)ページを参照してください。
{: note}

| 関係        | 説明                                                                                                                                                                                                        |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| affectedBy      | エンティティーと、明らかな方向性を持っていてそのエンティティーに影響するイベントとの間に存在します。                                                                                                                        |
| affiliatedWith  | 提携関係があるか、または似たような結び付きのある 2 つのエンティティーの間に存在します。                                                                                                                                   |
| ageOf           | 年齢をエンティティーに関連付けます。                                                                                                                                                                                       |
| agentOf         | エンティティーと、そのエンティティーがテキストに照らして最も積極的役割を果たすイベントとの間に存在します。 背景的知識は不要です。                                                            |
| authorOf        | 人と、その人が作成した TitleWork (作品) との間に存在します。                                                                                                                                                    |
| awardedBy       | Award (賞) または Degree (学位) と、その賞または学位を授与した人または組織との間に存在します。                                                                                                             |
| awardedTo       | Award (賞) または Degree (学位) と、その賞または学位を授与された人または組織との間に存在します。                                                                                                             |
| basedIn         | Organization (組織) と、その組織が置かれている主要な場所、唯一の場所、または本質的な場所との間に存在します。                                                                                                                   |
| before          | 2 つの Time (時期) または Event (イベント) の間の、「前」という時間的関係を表します。 テキストがこの関係を明示している場合にのみマーク付けされます。                                                                                      |
| bornAt          | Person (人) または Animal (動物) と、誕生した場所との間に存在します。                                                                                                                                     |
| bornOn          | Person (人) または Animal (動物) と、誕生した Date (日付) または Time (時期) との間に存在します。                                                                                                                           |
| capitalOf       | 首都と、その国や州 (都道府県) の間に存在します。 テキストがこの関係を明示している場合にのみマーク付けされ、常識的知識には基づきません。                                                              |
| citizenOf       | 人と、その人が市民である GeopoliticalEntity (地政学的エンティティー) との間に存在します。                                                                                                                                |
| clientOf        | 一方が他方の直接的なビジネス顧客である (つまり、特定のサービスまたは商品の代金を支払う) 2 つのエンティティーの間に存在します。                                                                                    |
| colleague       | 同じ Organization (組織) に所属する 2 人の人の間に存在します。                                                                                                                                                   |
| competitor      | 経済競争に参加している 2 つの GeopoliticalEntity (地政学的エンティティー) または Organization (組織) の間に存在します。                                                                                                                  |
| contactOf       | 連絡先情報をエンティティーに関連付けます。                                                                                                                                                                        |
| diedAt          | Person (人) または Animal (動物) と、その死亡場所との間に存在します。                                                                                                                                      |
| diedOf          | Person (人) または Animal (動物) と、その死亡原因との間に存在します。                                                                                                                                         |
| diedOn          | Person (人) または Animal (動物) と、その死亡の Date (日付) または Time (時期) との間に存在します。                                                                                                                               |
| dissolvedOn     | Organization (組織) などのエンティティーと、それが解散した Date (日付) または Time (時期) との間に存在します。                                                                                                                   |
| educatedAt      | Person (人) と、その人が教育を受けているかまたは受けた Organization (組織) との間に存在します。                                                                                                                                |
| employedBy      | 一方が特定の仕事またはサービスに対して他方に支払いを行う 2 つのエンティティーの間に存在します。金銭的報酬が存在する必要があります。 多くの場合、この関係をマーク付けするには常識的知識が必要です。                         |
| foundedOn       | Organization (組織) などのエンティティーと、それが設立された Date (日付) または Time (時期) との間に存在します。                                                                                                                     |
| founderOf       | Person (人) または GeopoliticalEntity (地政学的エンティティー) と、それが設立した Organization (組織) などのエンティティーとの間に存在します。                                                                                                                          |
| hasDisease      | Person (人) または Animal (動物) が Disease (病気) であるか、過去にそうだったことを示します。                                                                                                                                                            |
| hasMoney        | 人などのエンティティーが Money (金銭) を持っているか、または持っていたことを示します。                                                                                                                                                        |
| instrumentOf    | Weapon (武器) などのエンティティーと、そのエンティティーの使用によって引き起こされるか、引き起こされた Event (イベント) との間に存在します。                                                                                                              |
| locatedAt       | エンティティーと、そのエンティティーの物理的場所との間に存在します。                                                                                                                                                                |
| managerOf       | Person (人) と、その人が仕事として管理している Person (人) または Organization (組織) などのエンティティーとの間に存在します。                                                                                              |
| measureOf       | エンティティーの高さや重量などの特定の Measure (尺度) を示します。                                                                                                                                          |
| memberOf        | Person (人)、Organization (組織)、または GeopoliticalEntity (地政学的エンティティー) などのエンティティーと、それが所属している別のエンティティーとの間に存在します。                                                                                            |
| near            | 互いに物理的に近い場所にある 2 つのエンティティーの間に存在します。                                                                                                                                       |
| overlaps        | 2 つの Time (時期) または Event (イベント) が時間的に重なっていることを示します。 テキストがこの関係を明示している場合にのみマーク付けされます。                                                                                                   |
| ownerOf         | Person (人)、Organization (組織)、または GeopoliticalEntity (地政学的エンティティー) などのエンティティーと、それが永続的または一時的に所有しているエンティティーとの間に存在します。                                                                     |
| parentOf        | Person (人) または Animal (動物) と、その子または継子との間に存在します。                                                                                                                                         |
| participantIn   | Person (人)、Animal (動物)、Organization (組織)、または GeopoliticalEntity (地政学的エンティティー) と、それが参加しているか、または参加した Event (イベント) との間に存在します。                                                         |
| partner         | 経済的協力関係にある 2 つの GeopoliticalEntity (地政学的エンティティー) または Organization (組織) の間に存在します。                                                                                                                  |
| partOf          | 1 番目のエンティティーを 2 番目のエンティティーが包含する、同じタイプまたは関連するタイプで大きさの違う 2 つのエンティティーの間に存在します。 これらのエンティティーがイベント (Event) である場合は、1 番目が 2 番目の期間内に発生しなければなりません。 |
| partOfMany      | 1 番目のエンティティー (これは 1 つまたは複数のエンティティーからなります) を 2 番目のエンティティー (これは複数でなければなりません) が包含する、同じタイプまたは関連するタイプで大きさの違うエンティティーの間に存在します。                      |
| playsRoleOf     | Person (人) と、その人がパフォーマンスで演じているかまたは演じた特定の役柄との間に存在します。                                                                                                                  |
| populationOf    | Cardinal (カーディナル数) と、その数値が全人口を表している組織または国なとのエンティティーとの間に存在します。                                                                                  |
| productOf       | Product (製品) または TitleWork (作品) と、それを作成した Organization (組織) との間に存在します。                                                                                                                                       |
| quantityOf      | 2 番目のエンティティーの数量または量である Cardinal (カーディナル数) を示します。                                                                                                                                            |
| rateOf          | Rate (率) と、その率で発生頻度が指定されるイベントとの間に存在します。                                                                                                                                     |
| relative        | Person (人) または Animal (動物) と、その人または動物と近縁関係にある別の Person (人) または Animal (動物) との間に、それ以上はっきりした関係が適当ではない場合に存在します。                                                               |
| residesIn       | 生きているエンティティーと、その永住場所との間に存在します。                                                                                                                       |
| shareholdersOf  | Person (人)、Organization (組織)、または GeopoliticalEntity (地政学的エンティティー) と、1 番目のエンティティーが株主である Organization (組織) との間に存在します。                                                                                                  |
| siblingOf       | Person (人) または Animal (動物) と、その兄弟姉妹または義理の兄弟姉妹との間に存在します。                                                                                                                                     |
| spokespersonFor | Person (人) と、その人が代表するエンティティーとの間に存在します。 テキストがこの関係を明示している場合にのみマーク付けされ、常識的知識には基づきません。                                                           |
| spouseOf        | 正式な配偶者である 2 人の人の間に存在します。                                                                                                                                                      |
| subsidiaryOf    | 2 つの Organization (組織) の間に、1 番目が 2 番目の傘下組織である場合、つまり、1 番目のエンティティーが 2 番目の制御下にあるにも関わらずかなりの自律性を持っている場合に存在します。                               |
| timeOf          | TitleWork (作品) の発表、実演、配給や、Law (法律) の草案作成、作成、通過、廃止などのイベントが発生した、Date (日付)、Time (時刻)、または Duration (期間) を示します。                            |
