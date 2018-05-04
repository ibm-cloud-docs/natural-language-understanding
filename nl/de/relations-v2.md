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

# Beziehungstypen (Version 2)

In der folgenden Tabelle sind die Beziehungstypen aufgelistet, die vom Beziehungstypsystem _Version 2_ zurückgegeben werden. Welches Beziehungstypsystem {{site.data.keyword.nlushort}} verwendet, ist von der verwendeten Sprache abhängig. Details hierzu finden Sie auf der Seite [Beziehungstypen](relations.html).
{: shortdesc}

Die von diesem Beziehungstypsystem verwendeten Entitätstypen sind auf der Seite [Entitätstypen und -untertypen (Version 2)](entity-types-v2.html) aufgelistet.

| Beziehung        | Beschreibung |
|-----------------|----------------|
| affiliatedWith  | Besteht zwischen zwei Entitäten mit einer Zugehörigkeit oder ähnlichen Verbindung. | 
| basedIn         | Besteht zwischen einer Organisation und dem Ort, an dem sie hauptsächlich, ausschließlich oder tatsächlich positioniert ist. |
| bornAt          | Besteht zwischen einer Person und ihrem Geburtsort. |
| bornOn          | Besteht zwischen einer Person und dem Zeitpunkt (Datum oder Uhrzeit) ihrer Geburt. |
| clientOf        | Besteht zwischen zwei Entitäten, von denen eine ein direkter Geschäftskunde der anderen ist (d. h., für bestimmte Services oder Produkte zahlt). |
| colleague       | Besteht zwischen zwei Personen, die Teil derselben Organisation sind. |
| competitor      | Besteht zwischen zwei Organisationen, die in wirtschaftlichem Wettbewerb zueinander stehen. |
| contactOf       | Verbindet Kontaktinformationen mit einer Entität. |
| diedAt          | Besteht zwischen einer Person und ihrem Sterbeort. |
| diedOn          | Besteht zwischen einer Person und dem Zeitpunkt (Datum oder Uhrzeit) ihres Ablebens. |
| dissolvedOn     | Besteht zwischen einer Organisation oder URL und dem Zeitpunkt (Datum oder Uhrzeit) ihrer Auflösung. |
| educatedAt      | Besteht zwischen einer Person und der Organisation, an der sie ausgebildet wurde.|
| employedBy      | Besteht zwischen zwei Entitäten, wenn die eine die andere für bestimmte Arbeiten oder Services bezahlt; eine geldwerte Gegenleistung muss einbezogen sein. In vielen Situationen erfordert die Markierung dieser Beziehung Weltwissen. |
| foundedOn       | Besteht zwischen einer Organisation oder URL und dem Zeitpunkt (Datum oder Uhrzeit) ihrer Gründung. |
| founderOf       | Besteht zwischen einer Person und einer Einrichtung, Organisation oder URL, die von der Person gegründet wurde. |
| locatedAt       | Besteht zwischen einer Entität und ihrem Ort. |
| managerOf       | Besteht zwischen einer Person und einer anderen Entität, z. B. einer Person oder Organisation, die von der Person beruflich verwaltet wird. |
| memberOf        | Besteht zwischen einer Entität, z. B. einer Person oder Organisation, und einer anderen Entität, zu der die erste gehört. |
| ownerOf         | Besteht zwischen einer Entität, z. B. einer Person oder Organisation, und einer Entität, die Eigentum der ersten ist. Der Eigner muss kein permanenter Eigner der Entität sein, damit die Beziehung bestehen kann. |
| parentOf        | Besteht zwischen einer Person und ihren Kindern oder Stiefkindern. |
| partner         | Besteht zwischen zwei Organisationen, die auf wirtschaftlicher Ebene zusammenarbeiten. |
| partOf          | Besteht zwischen einer kleineren und einer größeren Entität desselben Typs oder verwandten Typs, wobei die zweite Entität die erste umfasst. Handelt es sich bei beiden Entitäten um Ereignisse, muss das erste innerhalb des Zeitraums des zweiten liegen, damit die Beziehung erkannt wird. |
| partOfMany      | Besteht zwischen einer kleineren und einer größeren Entität desselben Typs oder verwandten Typs, wobei die zweite Entität (die in der Mehrzahl angegeben werden muss) die erste (die in der Einzahl oder der Mehrzahl angegeben werden kann) umfasst. |
| populationOf    | Besteht zwischen einem Ort und der Anzahl der dort befindlichen Personen oder zwischen einer Organisation und der Anzahl der Mitglieder oder Mitarbeiter, die sie besitzt. |
| measureOf       | Diese Beziehung gibt die Menge einer Entität oder eines Maßes (Höhe, Gewicht usw.) einer Entität an. |
| relative        | Besteht zwischen zwei Personen, die miteinander verwandt sind. Zur Angabe von Eltern, Kindern, Geschwistern und Ehegatten verwenden Sie die Beziehungen `parentOf` (Elternteil von), `siblingOf` (Bruder/Schwester von) und `spouseOf` (Ehegatte/-gattin). |
| residesIn       | Besteht zwischen einer Person und dem Ort, an dem sie lebt oder früher gelebt hat. |
| shareholdersOf  | Besteht zwischen einer Person oder Organisation und einer Organisation, an der die erste Entität ein Anteilseigner ist. |
| siblingOf       | Besteht zwischen einer Person und ihrem Bruder/ihrer Schwester oder ihrem Stiefbruder/ihrer Stiefschwester. |
| spokespersonFor | Besteht zwischen einer Person und einer Einrichtung, Organisation oder Person, die von der ersten Person repräsentiert wird. |
| spouseOf        | Besteht zwischen zwei Personen, die miteinander verheiratet sind. |
| subsidiaryOf    | Besteht zwischen zwei Organisationen, wenn die erste der zweiten untergeordnet ist. |
