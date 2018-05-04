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

# 関係タイプ (バージョン 1)

下表に、_バージョン 1_ 関係タイプ・システムで返される関係タイプを示します。使用している言語によって、{{site.data.keyword.nlushort}} で使用される関係タイプ・システムは異なります。詳しくは、[『関係タイプ』](relations.html)ページを参照してください。
{: shortdesc}

| 関係| 説明|
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| affectedBy      | エンティティーと、明確な方向性を持っていてそのエンティティーに影響するイベントとの間に存在します。|
| affiliatedWith  | 提携関係があるか、それに似た結び付きがある、2 つのエンティティー間に存在します。|
| ageOf           | 年齢をエンティティーに関連付けます。|
| agentOf         | エンティティーと、そのエンティティーがテキストに従って最も積極的な役割を果たすイベントとの間に存在します。背景的知識は不要です。|
| authorOf        | 個人と、その個人が作成したタイトルワーク (TitleWork) との間に存在します。|
| awardedBy       | 賞 (Award) または学位 (Degree) と、それらを授与した個人または組織との間に存在します。|
| awardedTo       | 賞 (Award) または学位 (Degree) と、それらを授与された個人または組織との間に存在します。|
| basedIn         | 組織 (Organization) と、その組織が置かれている主要な場所、唯一の場所、または本来の場所との間に存在します。|
| before          | 2 つの時刻 (Time) またはイベント (Event) 間の「前」という時間関係を表します。テキストがこの関係を明示している場合にのみマーク付けされます。|
| bornAt          | 個人 (Person) または動物 (Animal) と、それらが生まれた場所との間に存在します。|
| bornOn          | 個人 (Person) または動物 (Animal) と、それらが生まれた日付 (Date) または時刻 (Time) との間に存在します。|
| capitalOf       | 首都と、その国、州、または県との間に存在します。テキストがこの関係を明示している場合にのみマーク付けされ、常識的知識には基づきません。|
| citizenOf       | 個人と、その個人が住民である地政学的エンティティー (GeopoliticalEntity) との間に存在します。|
| clientOf        | 一方が他方の直接的なビジネス顧客である (つまり、一方が他方に特定のサービスまたは商品の支払いを行う) 場合に、2 つのエンティティー間に存在します。|
| colleague       | 同じ組織 (Organization) に属する 2 人の個人 (People) 間に存在します。|
| competitor      | 経済競争に参加している 2 つの地政学的エンティティー (GeopoliticalEntity) または組織 (Organization) 間に存在します。|
| contactOf       | 連絡先情報をエンティティーに関連付けます。|
| diedAt          | 個人 (Person) または動物 (Animal) と、それらが死亡した場所との間に存在します。|
| diedOf          | 個人 (Person) または動物 (Animal) と、それらが死亡した原因との間に存在します。|
| diedOn          | 個人 (Person) または動物 (Animal) と、それらが死亡した日付 (Date) または時刻 (Time) との間に存在します。|
| dissolvedOn     | 組織 (Organization) などのエンティティーと、それが解散した日付 (Date) または時刻 (Time) との間に存在します。|
| educatedAt      | 個人 (Person) と、その個人が教育を受けている (受けた) 組織 (Organization) との間に存在します。|
| employedBy      | 一方が他方に特定の仕事またはサービスの支払いを行う場合に、2 つのエンティティー間に存在します。金銭的報酬が関係していなければなりません。多くの場合、この関係をマーク付けするには常識的知識が必要です。|
| foundedOn       | 組織 (Organization) などのエンティティーと、それが設立された日付 (Date) または時刻 (Time) との間に存在します。|
| founderOf       | 個人 (Person) または地政学的エンティティー (GeopoliticalEntity) と、それらが設立した組織 (Organization) などのエンティティーとの間に存在します。|
| hasDisease      | 個人 (Person) または動物 (Animal) が病気 (Disease) である (あった) ことを示します。|
| hasMoney        | 個人 (Person) などのエンティティーが金銭 (Money) を持っている (持っていた) ことを示します。|
| instrumentOf    | 武器 (Weapon) などのエンティティーと、そのエンティティーの使用によって引き起こされる (された) イベント (Event) との間に存在します。|
| locatedAt       | エンティティーと、その物理的な所在地との間に存在します。|
| managerOf       | 個人 (Person) と、その個人が仕事として管理している個人 (Person) や組織 (Organization) などの別のエンティティーとの間に存在します。|
| measureOf       | エンティティーの高さや重量などの特定の尺度 (Measure) を示します。|
| memberOf        | 個人 (Person)、組織 (Organization)、地政学的エンティティー (GeopoliticalEntity) などのエンティティーと、それらが属する別のエンティティーとの間に存在します。|
| near            | 互いに物理的に近い場所にある 2 つのエンティティー間に存在します。|
| overlaps        | 2 つの時刻 (Time) またはイベント (Event) が時間的に重なっていることを示します。テキストがこの関係を明示している場合にのみマーク付けされます。|
| ownerOf         | 個人 (Person)、組織 (Organization)、地政学的エンティティー (GeopoliticalEntity) などのエンティティーと、それらが永続的または一時的に所有しているエンティティーとの間に存在します。|
| parentOf        | 個人 (Person) または動物 (Animal) と、それらの子または継子との間に存在します。|
| participantIn   | 個人 (Person)、組織 (Organization)、地政学的エンティティー (GeopoliticalEntity) などの参加者と、それらが参加している (参加した) イベントとの間に存在します。|
| partner         | 経済協力に関与している 2 つの地政学的エンティティー (GeopoliticalEntity) または組織 (Organization) 間に存在します。|
| partOf          | 2 番目のエンティティーが 1 番目のエンティティーを包含する、同タイプまたは関連タイプで大きさの異なる 2 つのエンティティー間に存在します。これらのエンティティーがイベント (Event) である場合は、1 番目が 2 番目の期間内に発生しなければなりません。|
| partOfMany      | 2 番目のエンティティー (複数でなければならない) が 1 番目のエンティティー (1 つ以上のエンティティーで構成) を包含する、同タイプまたは関連タイプで大きさの異なる 2 つのエンティティー間に存在します。|
| playsRoleOf     | 個人 (Person) と、その個人がパフォーマンスで演じている (演じた) 特定のキャラクターとの間に存在します。|
| populationOf    | 基数 (Cardinal) と、その数が全人口を表す組織や国などのエンティティーとの間に存在します。|
| productOf       | 製品 (Product) またはタイトルワーク (TitleWork) と、それを制作した組織 (Organization) との間に存在します。|
| quantityOf      | 2 番目のエンティティーの数量である基数 (Cardinal) を示します。|
| rateOf          | 率 (Rate) と、その率が指定する発生頻度を持つイベントとの間に存在します。|
| relative        | 個人 (Person) または動物 (Animal) と、それらが親類関係にある別の個人 (Person) または動物 (Animal) との間に、それよりも明確な関係が不適当である場合に存在します。|
| residesIn       | 生きているエンティティーと、その永住場所との間に存在します。|
| shareholdersOf  | 個人 (Person)、組織 (Organization)、および地政学的エンティティー (GeopoliticalEntity) と、1 番目のエンティティーが株主である組織 (Organization) との間に存在します。|
| siblingOf       | 個人 (Person) または動物 (Animal) と、それらの兄弟または義兄弟との間に存在します。|
| spokespersonFor | 個人 (Person) と、その人が代表を務めるエンティティーとの間に存在します。テキストがこの関係を明示している場合にのみマーク付けされ、常識的知識には基づきません。|
| spouseOf        | 正式な配偶者である 2 人の個人 (People) 間に存在します。|
| subsidiaryOf    | 1 番目が 2 番目の子会社である (つまり、1 番目のエンティティーが 2 番目の制御下にあってもかなりの自律性を持っている) 場合に、2 つの組織 (Organization) 間に存在します。|
| timeOf          | タイトルワーク (TitleWork) の発表、実演、配給や、法律 (Law) の草案作成、作成、通過、廃止などのイベントが発生した、日付 (Date)、時刻 (Time)、または期間 (Duration) を示します。|

## 関係に固有のエンティティー・タイプ

_バージョン 1_ 関係タイプ・システムに含まれるエンティティー・タイプは、デフォルトのエンティティー・タイプ・システムに含まれるエンティティー・タイプとは異なります。`entities` フィーチャーの `model` パラメーターで以下の関係エンティティー・モジュールのいずれかを指定して、デフォルトのエンティティー検出モデルをオーバーライドすることができます。

|モデル ID|説明|
|--------|-----------|
|ar-news|アラビア語ニュース|
|en-news|英語ニュース|
|es-news|スペイン語ニュース|

以下のエンティティーが `relations` モデルを使用して識別可能です。

|エンティティー・タイプ|
|---|
|Age |
|Anatomy |
|Animal |
|Award |
|Cardinal |
|Crime |
|Date |
|Degree |
|Duration |
|EmailAddress |
|Event |
|EventBusiness |
|EventCommunication |
|EventCustody |
|EventDemonstration |
|EventEducation |
|EventElection |
|EventGathering |
|EventLegal |
|EventLegislation |
|EventMeeting |
|EventPerformance |
|EventPersonnel |
|EventViolence |
|Facility |
|Food |
|GeographicFeature|
|GeopoliticalEntity |
|HealthCondition |
|Law |
|Location |
|Money |
|Measure |
|NaturalEvent |
|Organization |
|Ordinal |
|Percent |
|Person |
|Phone |
|Plant |
|Product |
|SportingEvent |
|Substance |
|Ticker |
|Time |
|TitleWork |
|Vehicle |
|Weapon |
|Weather |
|Web |

