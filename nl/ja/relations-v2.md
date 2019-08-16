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

# 関係タイプ (バージョン 2)
{: #relation-types-version-2}

下表に、_バージョン 2_ 関係タイプ・システムで返される関係タイプを示します。 使用している言語によって、{{site.data.keyword.nlushort}} で使用される関係タイプ・システムは異なります。 詳しくは、[関係タイプ・システム](/docs/services/natural-language-understanding?topic=natural-language-understanding-relation-type-systems)ページを参照してください。
{: shortdesc}

この関係タイプ・システムで使用されるエンティティー・タイプは、[エンティティーのタイプ (バージョン 2)](/docs/services/natural-language-understanding?topic=natural-language-understanding-entity-types-version-2)ページに示されています。
{: note}

| 関係        | 説明 |
|-----------------|----------------|
| affiliatedWith  | 提携関係があるか、または似たような結び付きのある 2 つのエンティティーの間に存在します。 | 
| basedIn         | Organization (組織) と、その組織が置かれている主要な場所、唯一の場所、または本質的な場所との間に存在します。 |
| bornAt          | 個人 (Person) と、その個人が生まれた場所との間に存在します。 |
| bornOn          | 個人 (Person) と、その個人が生まれた日付 (Date) または時刻 (Time) との間に存在します。 |
| clientOf        | 一方が他方の直接的なビジネス顧客である (つまり、特定のサービスまたは商品の代金を支払う) 2 つのエンティティーの間に存在します。 |
| colleague       | 同じ組織 (Organization) に属する 2 人の個人 (Person) 間に存在します。 |
| competitor      | 経済競争に参加している 2 つの組織 (Organization) 間に存在します。 |
| contactOf       | 連絡先情報をエンティティーに関連付けます。 |
| diedAt          | 個人 (Person) と、その個人が死亡した場所との間に存在します。 |
| diedOn          | 個人 (Person) と、その個人が死亡した日付 (Date) または時刻 (Time) との間に存在します。 |
| dissolvedOn     | 組織 (Organization) または URL と、それが解散 (消失) した日付 (Date) または時刻 (Time) との間に存在します。 |
| educatedAt      | 個人 (Person) と、その個人が教育を受けているかまたは受けた組織 (Organization) との間に存在します。|
| employedBy      | 一方が特定の仕事またはサービスに対して他方に支払いを行う 2 つのエンティティーの間に存在します。金銭的報酬が存在する必要があります。 多くの場合、この関係をマーク付けするには常識的知識が必要です。 |
| foundedOn       | 組織 (Organization) または URL と、それが設立 (開設) された日付 (Date) または時刻 (Time) との間に存在します。 |
| founderOf       | 個人 (Person) と、その個人が設立 (開設) した機構 (Facility)、組織 (Organization)、または URL との間に存在します。 |
| locatedAt       | エンティティーとその所在地との間に存在します。 |
| managerOf       | Person (人) と、その人が仕事として管理している Person (人) または Organization (組織) などのエンティティーとの間に存在します。 |
| memberOf        | 個人 (Person) や組織 (Organization) などのエンティティーと、それらが属する別のエンティティーとの間に存在します。 |
| ownerOf         | 個人 (Person) や組織 (Organization) などのエンティティーと、それらが所有するエンティティーとの間に存在します。 所有者は、関係を存在させるために、エンティティーの永続的所有権を持つ必要はありません。 |
| parentOf        | 個人 (Person) と、その子または継子との間に存在します。 |
| partner         | 経済協力に関与している 2 つの組織 (Organization) 間に存在します。 |
| partOf          | 1 番目のエンティティーを 2 番目のエンティティーが包含する、同じタイプまたは関連するタイプで大きさの違う 2 つのエンティティーの間に存在します。 エンティティーがいずれもイベントである場合、関係が認識されるためには、1 番目が 2 番目の期間内に発生しなければなりません。 |
| partOfMany      | タイプが同じか関連していて、大きさが異なる 2 つのエンティティー間に存在します。2 番目の大きいエンティティー (複数でなければならない) が 1番目の小さいエンティティー (単数または複数) を包含します。 |
| populationOf    | 場所とそこにいる人数との間、あるいは組織とそのメンバー数または従業員数との間に存在します。 |
| measureOf      | この関係は、エンティティーの数量またはエンティティーの尺度 (高さ、重量など) を示します。 |
| relative        | 親類関係にある 2 人の個人 (Person) 間に存在します。 親、子、兄弟、および配偶者を識別するには、`parentOf`、`siblingOf`、および `spouseOf` の各関係を使用します。 |
| residesIn       | 個人 (Person) と、その生活している (していた) 場所との間に存在します。 |
| shareholdersOf  | 個人 (Person) または組織 (Organization) と、その 1 番目のエンティティーが株主である組織 (Organization) との間に存在します。 |
| siblingOf       | 個人 (Person) と、その兄弟または義兄弟との間に存在します。     |
| spokespersonFor | 個人 (Person) と、その個人が代表を務める機構 (Facility)、組織 (Organization)、または個人 (Person) との間に存在します。  |
| spouseOf        | 配偶者である 2 人の個人 (Person) 間に存在します。 |
| subsidiaryOf    | 1 番目の組織が 2 番目の組織の子会社である 2 つの組織 (Organization) 間に存在します。 |
