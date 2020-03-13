---

copyright:
  years: 2015, 2020
lastupdated: "2020-02-24"

subcollection: natural-language-understanding

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

# Relation types (Version 1)
{: #relation-types-version-1}

The following table lists the relation types returned by the _Version 1_ relation type system. The relation type system that {{site.data.keyword.nlushort}} uses differs based on which language you are using. For more details, see the [Relation type systems](/docs/natural-language-understanding?topic=natural-language-understanding-relation-type-systems) page.
{: shortdesc}

In the _Version 1_ type system, the entity types in relations results are different than the entity types returned in entities results. To see the list of entity types used in _Version 1_ relations, see the [Entity types (Version 1)](/docs/natural-language-understanding?topic=natural-language-understanding-entity-types-version-1#relations-entity-types) page.
{: note}

| Relation        | Description                                                                                                                                                                                                        |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| affectedBy      | Exists between an entity and an event that has clear directionality and affects the entity.                                                                                                                        |
| affiliatedWith  | Exists between two entities that have an affiliation or are similarly connected.                                                                                                                                   |
| ageOf           | Relates an age to an entity.                                                                                                                                                                                       |
| agentOf         | Exists between an entity and an event in which the entity plays the most active role according to the text. No background knowledge should be required.                                                            |
| authorOf        | Exists between a person and a TitleWork that he or she created.                                                                                                                                                    |
| awardedBy       | Exists between an Award or Degree and the person or organization by which it was awarded or conferred.                                                                                                             |
| awardedTo       | Exists between an Award or Degree and the person or organization to which it was awarded or conferred.                                                                                                             |
| basedIn         | Exists between an Organization and the place where it is mainly, only, or intrinsically located.                                                                                                                   |
| before          | Signifies the temporal relation "before" between two Times or Events. Marked only when the text clearly specifies the relation.                                                                                      |
| bornAt          | Exists between a Person or Animal and the place where she, he, or it was born.                                                                                                                                     |
| bornOn          | Exists between a Person or Animal and the Date or Time on which she, he, or it was born.                                                                                                                           |
| capitalOf       | Exists between a capital and its country, state, or province. Marked only when the text explicitly states the relation, not based on world knowledge.                                                              |
| citizenOf       | Exists between a person and the GeopoliticalEntity of which he or she is a citizen.                                                                                                                                |
| clientOf        | Exists between two entities when one is a direct business client of the other (that is, pays for certain services or products).                                                                                    |
| colleague       | Exists between two People who are part of the same Organization.                                                                                                                                                   |
| competitor      | Exists between two GeopoliticalEntities or Organizations that are engaged in economic competition.                                                                                                                  |
| contactOf       | Relates contact information with an entity.                                                                                                                                                                        |
| diedAt          | Exists between a Person or Animal and the place at which he, she, or it died.                                                                                                                                      |
| diedOf          | Exists between a Person or Animal and the cause of his, her, or its death.                                                                                                                                         |
| diedOn          | Exists between a Person or Animal and the Date or Time on which he, she, or it died.                                                                                                                               |
| dissolvedOn     | Exists between an entity such as an Organization and the Date or Time on which it was dissolved.                                                                                                                   |
| educatedAt      | Exists between a Person and the Organization at which he or she is or was educated.                                                                                                                                |
| employedBy      | Exists between two entities when one pays the other for certain work or services; monetary reward must be involved. In many circumstances, marking this relation requires world knowledge.                         |
| foundedOn       | Exists between an entity such as an Organization and the Date or Time on which it was founded.                                                                                                                     |
| founderOf       | Exists between a Person or GeopoliticalEntity and an entity such as an Organization that it founded.                                                                                                                          |
| hasDisease      | Indicates that a Person or Animal has or had a Disease.                                                                                                                                                            |
| hasMoney        | Indicates that an entity such as a person has or had Money.                                                                                                                                                        |
| instrumentOf    | Exists between an entity such as a Weapon and an Event that the entity is or was used to bring about.                                                                                                              |
| locatedAt       | Exists between an entity and its physical location.                                                                                                                                                                |
| managerOf       | Exists between a Person and another entity such as a Person or Organization that he or she manages as his or her job.                                                                                              |
| measureOf       | Indicates a particular Measure such as the height or weight of an entity.                                                                                                                                          |
| memberOf        | Exists between an entity such as a Person, Organization, or GeopoliticalEntity and another entity to which he, she, or it belongs.                                                                                            |
| near            | Exists between two entities that are located close to each other physically.                                                                                                                                       |
| overlaps        | Indicates that two Times or Events overlap temporally. Marked only when the text clearly specifies the relation.                                                                                                   |
| ownerOf         | Exists between an entity such as a Person, Organization, or GeopoliticalEntity and an entity that he, she, or it owns, either permanently or temporarily.                                                                     |
| parentOf        | Exists between a Person or Animal and his, her, or its child or stepchild.                                                                                                                                         |
| participantIn   | Exists between a participant such as a Person, Animal, Organization, or GeopoliticalEntity and an Event in which he, she, or it is participating or has participated.                                                         |
| partner         | Exists between two GeopoliticalEntities or Organizations that are engaged in economic cooperation.                                                                                                                  |
| partOf          | Exists between a smaller and a larger entity of the same type or related types in which the second entity subsumes the first. If the entities are Events, the first must occur within the time span of the second. |
| partOfMany      | Exists between smaller and larger entities of the same type or related types in which the second entity, which must be plural, subsumes the first, which can consist of one or more entities.                      |
| playsRoleOf     | Exists between a Person and a specific character that he or she plays or played in a performance.                                                                                                                  |
| populationOf    | Exists between a Cardinal and an entity such as an organization or country for which the number represents the entire population.                                                                                  |
| productOf       | Exists between a Product or TitleWork and the Organization that produced it.                                                                                                                                       |
| quantityOf      | Indicates a Cardinal that is the quantity or amount of a second entity.                                                                                                                                            |
| rateOf          | Exists between a Rate and an event whose frequency of occurrence it specifies.                                                                                                                                     |
| relative        | Exists between a Person or Animal and another Person or Animal of which he, she, or it is a relative when a more specific relation is inappropriate.                                                               |
| residesIn       | Exists between a living entity and the location at which he, she, or it permanently resides.                                                                                                                       |
| shareholdersOf  | Exists between a person, Organization, or GeopoliticalEntity and an Organization of which the first entity is a shareholder.                                                                                                  |
| siblingOf       | Exists between a Person or Animal and his, her, or its sibling or stepsibling.                                                                                                                                     |
| spokespersonFor | Exists between a Person and an entity that he or she represents. Marked only when the text explicitly states the relation, not based on world knowledge.                                                           |
| spouseOf        | Exists between two People that are formal spouses.                                                                                                                                                      |
| subsidiaryOf    | Exists between two Organizations when the first is a subsidiary of the second, meaning the first entity has a fair amount of autonomy despite being under the control of the second.                               |
| timeOf          | Indicates the Date, Time, or Duration at or for which an event occurred; a TitleWork was published, performed, or broadcast; or a Law was first drafted, created, passed, or abolished.                            |
