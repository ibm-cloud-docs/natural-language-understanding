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

# Beziehungstypen (Version 1)

In der folgenden Tabelle sind die Beziehungstypen aufgelistet, die vom Beziehungstypsystem _Version 1_ zurückgegeben werden. Welches Beziehungstypsystem {{site.data.keyword.nlushort}} verwendet, ist von der verwendeten Sprache abhängig. Details hierzu finden Sie auf der Seite [Beziehungstypen](relations.html).
{: shortdesc}

| Beziehung        | Beschreibung                                                                                                                                                                                                        |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| affectedBy      | Besteht zwischen einer Entität und einem Ereignis, das eine klare Ausrichtung hat und sich auf die Entität auswirkt.                                                                                                                        |
| affiliatedWith  | Besteht zwischen zwei Entitäten mit einer Zugehörigkeit oder ähnlichen Verbindung.                                                                                                                                   |
| ageOf           | Verbindet ein Alter mit einer Entität.                                                                                                                                                                                       |
| agentOf         | Besteht zwischen einer Entität und einem Ereignis, bei dem die Entität laut Text die aktivste Rolle spielt. Hierfür sollte kein Hintergrundwissen erforderlich sein.                                                            |
| authorOf        | Besteht zwischen einer Person und einem Titelwerk, das die Person geschaffen hat.                                                                                                                                                    |
| awardedBy       | Besteht zwischen einer Anerkennung (Award) oder einem Ausbildungsgrad (Degree) und der Person oder Organisation, die diese Anerkennung oder diesen Ausbildungsgrad verliehen bzw. zuerkannt hat.                                                                                                             |
| awardedTo       | Besteht zwischen einer Anerkennung (Award) oder einem Ausbildungsgrad (Degree) und der Person oder Organisation, der diese Anerkennung oder den Ausbildungsgrad verliehen bzw. zuerkannt wurde.                                                                                                             |
| basedIn         | Besteht zwischen einer Organisation und dem Ort, an dem sie hauptsächlich, ausschließlich oder tatsächlich positioniert ist. |
| before          | Bezeichnet die zeitliche Beziehung "before" zwischen zwei Zeitpunkten oder Ereignissen. Nur dann markiert, wenn der Text die Beziehung deutlich angibt.                                                                                      |
| bornAt          | Besteht zwischen einer Person oder einem Tier und ihrem/seinem Geburtsort.                                                                                                                                     |
| bornOn          | Besteht zwischen einer Person oder einem Tier und dem Zeitpunkt (Datum oder Uhrzeit) ihres/seines Ablebens. |
| capitalOf       | Besteht zwischen einer Hauptstadt und ihrem Land, ihrem Bundesstaat oder ihrer Provinz. Nur dann markiert, wenn der Text die Beziehung explizit angibt, nicht auf Weltwissen basierend.                                                              |
| citizenOf       | Besteht zwischen einer Person und der geopolitischen Entität, deren Staatsbürger die Person ist.                                                                                                                                |
| clientOf        | Besteht zwischen zwei Entitäten, von denen eine ein direkter Geschäftskunde der anderen ist (d. h., für bestimmte Services oder Produkte zahlt). |
| colleague       | Besteht zwischen zwei Personen, die Teil derselben Organisation sind. |
| competitor      | Besteht zwischen zwei geopolitischen Entitäten oder Organisationen, die in wirtschaftlichem Wettbewerb zueinander stehen. |
| contactOf       | Verbindet Kontaktinformationen mit einer Entität. |
| diedAt          | Besteht zwischen einer Person oder einem Tier und dem Ort ihres/seines Ablebens.                                                                                                                                     |
| diedOf          | Besteht zwischen einer Person oder einem Tier und der Ursache für ihr/sein Ableben.                                                                                                                                     |
| diedOn          | Besteht zwischen einer Person oder einem Tier und dem Zeitpunkt (Datum oder Uhrzeit) ihres Ablebens. |
| dissolvedOn     | Besteht zwischen einer Entität wie z. B. einer Organisation und dem Zeitpunkt (Datum oder Uhrzeit) ihrer Auflösung.                                                                                                                   |
| educatedAt      | Besteht zwischen einer Person und der Organisation, an der sie ausgebildet wurde.|
| employedBy      | Besteht zwischen zwei Entitäten, wenn die eine die andere für bestimmte Arbeiten oder Services bezahlt; eine geldwerte Gegenleistung muss einbezogen sein. In vielen Situationen erfordert die Markierung dieser Beziehung Weltwissen. |
| foundedOn       | Besteht zwischen einer Entität wie z. B. einer Organisation und dem Zeitpunkt (Datum oder Uhrzeit) ihrer Gründung.                                                                                                                   |
| founderOf       | Besteht zwischen einer Person oder geopolitischen Entität und einer Entität wie z. B. einer Organisation, die sie gegründet hat.                                                                                                                          |
| hasDisease      | Gibt an, dass eine Person oder ein Tier eine Krankheit hat oder hatte.                                                                                                                                                            |
| hasMoney        | Gibt an, dass eine Entität wie z. B. eine Person Geld hat oder hatte.                                                                                                                                                        |
| instrumentOf    | Besteht zwischen einer Entität wie z. B. einer Waffe und einem Ereignis, das von der Entität ausgelöst werden wird oder wurde.                                                                                                              |
| locatedAt       | Besteht zwischen einer Entität und ihrem physischen Standort. |
| managerOf       | Besteht zwischen einer Person und einer anderen Entität, z. B. einer Person oder Organisation, die von der Person beruflich verwaltet wird. |
| measureOf      | Gibt ein bestimmtes Maß wie z. B. die Höhe oder das Gewicht einer Entität an.                                                                                                                                          |
| memberOf        | Besteht zwischen einer Entität wie z. B. einer Person, Organisation oder geopolitischen Entität und einer anderen Entität, zu der die erste gehört.                                                                                            |
| near            | Besteht zwischen zwei Entitäten, die sich physisch nahe beieinander befinden.                                                                                                                                       |
| overlaps        | Gibt an, dass sich zwei Zeitpunkte oder Ereignisse zeitlich überschneiden. Nur dann markiert, wenn der Text die Beziehung deutlich angibt.                                                                                      |
| ownerOf         | Besteht zwischen einer Entität wie z. B. einer Person, Organisation oder geopolitischen Entität und einer Entität, der die erste dauerhaft oder vorübergehend angehört.                                                                     |
| parentOf        | Besteht zwischen einer Person oder einem Tier und ihrem/seinem Kind oder Stiefkind.                                                                                                                                     |
| participantIn   | Besteht zwischen einem Teilnehmer wie z. B. einer Person, einem Tier, einer Organisation oder geopolitischen Entität und einem Ereignis, an dem der Teilnehmer teilnimmt oder teilgenommen hat.                                                         |
| partner         | Besteht zwischen zwei geopolitischen Entitäten oder Organisationen, die auf wirtschaftlicher Ebene zusammenarbeiten. |
| partOf          | Besteht zwischen einer kleineren und einer größeren Entität desselben Typs oder verwandten Typs, wobei die zweite Entität die erste umfasst. Handelt es sich bei beiden Entitäten um Ereignisse, muss das erste innerhalb des Zeitraums des zweiten liegen. |
| partOfMany      | Besteht zwischen einer kleineren und einer größeren Entität desselben Typs oder verwandten Typs, wobei die zweite Entität (die in der Mehrzahl angegeben werden muss) die erste (die aus einer oder mehreren Entitäten bestehen kann) umfasst.                      |
| playsRoleOf     | Besteht zwischen einer Person und einem bestimmten Charakter, den die Person in einer Aufführung spielt oder gespielt hat.                                                                                                                  |
| populationOf    | Besteht zwischen einer Kardinalzahl und einer Entität wie z. B. einer Organisation oder einem Land, für die/das die Zahl die Gesamtbevölkerung darstellt.                                                                                  |
| productOf       | Besteht zwischen einem Produkt oder Titelwerk und der Organisation, die es erzeugt hat.                                                                                                                                       |
| quantityOf      | Gibt eine Kardinalzahl an, die die Menge einer zweiten Entität darstellt.                                                                                                                                            |
| rateOf          | Besteht zwischen einem Gebührensatz und einem Ereignis, dessen Vorkommenshäufigkeit er angibt.                                                                                                                                     |
| relative        | Besteht zwischen einer Person oder einem Tier und einer anderen Person oder einem Tier, mit dem sie/es verwandt ist, wenn eine genauere Beziehung ungeeignet ist. |
| residesIn       | Besteht zwischen einer lebenden Entität und ihrem dauerhaften Wohnort.                                                                                                                       |
| shareholdersOf  | Besteht zwischen einer Person, Organisation oder geopolitischen Entität und einer Organisation, an der die erste Entität ein Anteilseigner ist. |
| siblingOf       | Besteht zwischen einer Person oder einem Tier und ihrem/seinem Geschwister oder Stiefgeschwister.                                                                                                                                     |
| spokespersonFor | Besteht zwischen einer Person und einer Entität, die von der ersten dargestellt wird.                                                                                                                                                    Nur dann markiert, wenn der Text die Beziehung explizit angibt, nicht auf Weltwissen basierend.                                                              |
| spouseOf        | Besteht zwischen zwei Personen, die miteinander verheiratet sind. |
| subsidiaryOf    | Besteht zwischen zwei Organisationen, wenn die erste der zweiten untergeordnet ist, d. h., die erste Entität besitzt ausreichende Autonomie, wenngleich sie von der zweiten kontrolliert wird. |
| timeOf          | Gibt Datum, Uhrzeit oder Dauer eines Ereignisses an, das aufgetreten ist, eines Titelwerks, das veröffentlicht, aufgeführt oder ausgestrahlt wurde, oder eines Gesetzes, das entworfen, geschaffen, verabschiedet oder abgeschafft wurde.                            |

## Für Beziehungen eindeutige Entitätstypen

Die am Beziehungstypsystem _Version 1_ beteiligten Entitätstypen unterscheiden sich von den Entitätstypen, die an Standard-Entitätstypsystemen beteiligt sind. Sie können eines der folgenden Beziehungsentitätsmodelle im Parameter `model` für das `entities`-Feature angeben, um das Standard-Entitätserkennungsmodell zu überschreiben.

|Modell-ID|Beschreibung|
|--------|-----------|
|ar-news|Arabische Nachrichten|
|en-news|Englische Nachrichten|
|es-news|Spanische Nachrichten|

Die folgenden Entitäten können mit den `relations`-Modellen identifiziert werden:

|Entitätstyp|
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

