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

# Relation types (Version 2)
{: #relation-types-version-2}

The following table lists the relation types returned by the _Version 2_ relation type system. The relation type system that {{site.data.keyword.nlushort}} uses differs based on which language you are using. For more details, see the [Relation type systems](/docs/services/natural-language-understanding?topic=natural-language-understanding-relation-type-systems) page.
{: shortdesc}

The entity types used by this relation type system are listed on the [Entity types (Version 2)](/docs/services/natural-language-understanding?topic=natural-language-understanding-entity-types-version-2) page.
{: note}

| Relation        | Description |
|-----------------|----------------|
| affiliatedWith  | Exists between two entities that have an affiliation or are similarly connected. | 
| basedIn         | Exists between an Organization and the place where it is mainly, only, or intrinsically located. |
| bornAt          | Exists between a Person and the place where they were born. |
| bornOn          | Exists between a Person and the Date or Time when they were born. |
| clientOf        | Exists between two entities when one is a direct business client of the other (that is, pays for certain services or products). |
| colleague       | Exists between two Persons who are part of the same Organization. |
| competitor      | Exists between two Organizations that are engaged in economic competition. |
| contactOf       | Relates contact information with an entity. |
| diedAt          | Exists between a Person and the place at which he, she, or it died. |
| diedOn          | Exists between a Person and the Date or Time on which he, she, or it died. |
| dissolvedOn     | Exists between an Organization or URL and the Date or Time when it was dissolved. |
| educatedAt      | Exists between a Person and the Organization at which he or she is or was educated.|
| employedBy      | Exists between two entities when one pays the other for certain work or services; monetary reward must be involved. In many circumstances, marking this relation requires world knowledge. |
| foundedOn       | Exists between an Organization or URL and the Date or Time on which it was founded. |
| founderOf       | Exists between a Person and a Facility, Organization, or URL that they founded. |
| locatedAt       | Exists between an entity and its location. |
| managerOf       | Exists between a Person and another entity such as a Person or Organization that he or she manages as his or her job. |
| memberOf        | Exists between an entity, such as a Person or Organization, and another entity to which he, she, or it belongs. |
| ownerOf         | Exists between an entity, such as a Person or Organization, and an entity that he, she, or it owns. The owner does not need to have permanent ownership of the entity for the relation to exist. |
| parentOf        | Exists between a Person and their children or stepchildren. |
| partner         | Exists between two Organizations that are engaged in economic cooperation. |
| partOf          | Exists between a smaller and a larger entity of the same type or related types in which the second entity subsumes the first. If the entities are both events, the first must occur within the time span of the second for the relation to be recognized. |
| partOfMany      | Exists between smaller and larger entities of the same type or related types in which the second entity, which must be plural, includes the first, which can be singular or plural. |
| populationOf    | Exists between a place and the number of people located there, or an organization and the number of members or employees it has. |
| measureOf      | This relation indicates the quantity of an entity or measure (height, weight, etc) of an entity. |
| relative        | Exists between two Persons who are relatives. To identify parents, children, siblings, and spouses, use the `parentOf`, `siblingOf`, and `spouseOf` relations. |
| residesIn       | Exists between a Person and a place where they live or previously lived. |
| shareholdersOf  | Exists between a Person or Organization, and an Organization of which the first entity is a shareholder. |
| siblingOf       | Exists between a Person and their sibling or stepsibling.     |
| spokespersonFor | Exists between a Person and an Facility, Organization, or Person that he or she represents.  |
| spouseOf        | Exists between two Persons that are spouses. |
| subsidiaryOf    | Exists between two Organizations when the first is a subsidiary of the second. |
