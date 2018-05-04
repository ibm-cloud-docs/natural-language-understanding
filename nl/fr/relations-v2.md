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

# Types de relation (version 2)

Le tableau ci-dessous répertorie les types de relation renvoyés par le système de types de relation de _version 2_. Le système de types de relation que {{site.data.keyword.nlushort}} utilise varie en fonction de la langue que vous employez. Pour plus de détails, voir la page [Types de relation](relations.html).
{: shortdesc}

Les types d'entité utilisés par ce système de types de relation sont répertoriés dans la page [Types et sous-types d'entité (version 2)](entity-types-v2.html). 

| Relation        | Description |
|-----------------|----------------|
| affiliatedWith  | Existe entre deux entités qui ont une affiliation ou qui sont connectées de façon similaire. | 
| basedIn         | Existe entre une organisation et l'emplacement où elle se trouve principalement, uniquement, ou intrinsèquement. |
| bornAt          | Existe entre une personne et son lieu de naissance. |
| bornOn          | Existe entre une personne et la date ou l'heure de sa naissance. |
| clientOf        | Existe entre deux entités lorsque l'une est un client direct de l'autre (autrement dit, elle paie pour certains services ou produits). |
| colleague       | Existe entre deux personnes qui font partie de la même organisation. |
| competitor      | Existe entre deux organisations engagées dans une concurrence économique. |
| contactOf       | Relie des informations de contact à une entité. |
| diedAt          | Existe entre une personne et le lieu de son décès. |
| diedOn          | Existe entre une personne et la date ou l'heure de son décès.                                                                                                                               |
| dissolvedOn     | Existe entre une organisation ou une URL et la date ou l'heure de sa dissolution. |
| educatedAt      | Existe entre une personne et l'organisation où cette personne fait ou a fait ses études.|
| employedBy      | Existe entre deux entités lorsque l'une d'entre d'elles paie pour certains travaux ou services ; une récompense financière doit être impliquée. Dans de nombreuses circonstances, le marquage de cette relation requiert une certaine connaissance du monde. |
| foundedOn       | Existe entre une organisation ou une URL et la date ou l'heure de sa création. |
| founderOf       | Existe entre une personne et un site, une organisation ou une URL qu'elle a créé. |
| locatedAt       | Existe entre une entité et son emplacement. |
| managerOf       | Existe entre une personne et une autre entité, par exemple une personne ou une organisation, que cette personne gère dans le cadre de son travail. |
| memberOf        | Existe entre une entité, par exemple une personne ou une organisation, et une autre entité à laquelle elle appartient. |
| ownerOf         | Existe entre une entité, par exemple une personne ou une organisation, et une entité qu'elle possède. Il n'est pas nécessaire que le propriétaire ait la propriété permanente de l'entité pour que la relation existe. |
| parentOf        | Existe entre une personne et ses enfants ou ses beaux-fils ou belles-filles. |
| partner         | Existe entre deux organisations engagées dans une coopération économique. |
| partOf          | Existe entre une entité plus petite et une entité plus grande de même type ou de types connexes, la seconde englobant la première. Si les deux entités sont des événements, le premier événement doit survenir dans l'intervalle de temps de la seconde pour que la relation soit reconnue. |
| partOfMany      | Existe entre des entités plus petites et plus grandes de même type ou de types connexes, la seconde (qui doit être multiple) englobant la première (qui peut être unique ou multiple). |
| populationOf    | Existe entre un lieu et le nombre de personnes s'y trouvant, ou une organisation et le nombre de ses membres ou employés. |
| measureOf      | Cette relation indique la quantité ou la mesure (hauteur, poids, etc.) d'une entité. |
| relative        | Existe entre deux personnes d'une même famille. Pour identifier les parents, les enfants, les frères et soeurs et les conjoints, utilisez les relations `parentOf`, `siblingOf` et `spouseOf`. |
| residesIn       | Existe entre une personne et le lieu où elle vit ou a vécu. |
| shareholdersOf  | Existe entre une personne ou une organisation et une organisation dont la première entité est un actionnaire. |
| siblingOf       | Existe entre une personne et son frère et sa soeur ou son beau-fils ou sa belle-fille. |
| spokespersonFor | Existe entre une personne et un site, une organisation ou une personne qu'elle représente. |
| spouseOf        | Existe entre deux personnes qui sont des conjoints. |
| subsidiaryOf    | Existe entre deux organisations lorsque la première est une filiale de la seconde. |
