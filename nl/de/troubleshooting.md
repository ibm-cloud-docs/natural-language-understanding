---

copyright:
  years: 2015, 2019
lastupdated: "2019-02-25"

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
{:download: .download}

# Fehlerbehebung
{: #troubleshooting}

Wenn Sie Probleme mit {{site.data.keyword.nlushort}} haben, sind die folgenden Tipps zur Fehlerbehebung gegebenenfalls hilfreich.
{:shortdesc}

## Entitäten und Beziehungsentitätstypen sind nicht konsistent
{: #inconsistent-entity-types}

Die Entitätstypsysteme für die Features 'Entitäten' und 'Beziehungen' sind nicht immer konsistent. Bei manchen Sprachen und Versionsdaten enthalten die Beziehungsergebnisse andere Entitätstypen als die Entitätsergebnisse. Weitere Informationen finden Sie in [Entitätstypen und -untertypen](/docs/services/natural-language-understanding?topic=natural-language-understanding-entity-type-systems) und in [Beziehungstypen](/docs/services/natural-language-understanding?topic=natural-language-understanding-relation-type-systems). 

## Falsche Spracherkennung
{: #incorrect-language-detection}

Die automatische Spracherkennung ist für Text, der weniger als 100 Zeichen umfasst, unter Umständen nicht korrekt. Wenn der Service nicht die korrekte Sprache Ihres Textes erkennt, können Sie die [automatische Spracherkennung überschreiben](/docs/services/natural-language-understanding?topic=natural-language-understanding-overriding-language-detection).

## Zu viele Anforderungen
{: #too-many requests}

Wenn Sie ein Fehler vom Typ '429: Zu viele Anforderungen' gemeldet wird, bewegt sich Ihre Serviceinstanz wahrscheinlich am Grenzwert für gleichzeitige Anforderungen. Weitere Informationen hierzu finden Sie auf der Seite [Nutzungsbeschränkungen](/docs/services/natural-language-understanding?topic=natural-language-understanding-usage-limits#concurrent-requests).

## Nicht erwartete Ergebnisse der Webseitenanalyse
{: #unexpected-webpage-results}

Die Analyse einer Webseite kann in manchen Fällen zu unerwarteten Ergebnissen führen. Versuchen Sie zur Überprüfung, für den Parameter **return_analyzed_text** den Wert `true` festzulegen, um den eigentlichen Text zu untersuchen, der in Ihrer Anforderung analysiert wird. In Fällen, in denen im Rahmen der [Webseitenbereinigung](/docs/services/natural-language-understanding?topic=natural-language-understanding-analyzing-webpages#webpage-cleaning) nicht genügend unerwünschter Text entfernt wird, sollten Sie die Verwendung des Parameters [**xpath**](/docs/services/natural-language-understanding?topic=natural-language-understanding-analyzing-webpages#xpath) in Betracht ziehen, um den Fokus der Analyse auf bestimmte Elemente der Seite zu lenken.

## Erläuterungen zu bestimmten Ergebnissen
{: #explanations-for-results}

{{site.data.keyword.nlushort}} stellt keine Diagnosetools zur Verfügung, um zu erklären, aus welchem Grund eine bestimmte Anforderung ein bestimmtes Ergebnis zurückgibt. Der Service ist darauf ausgelegt, korrekte Ergebnisse für so viele Textbeispiele wie möglich zu liefern, aber aufgrund der Art der verwendeten Modelle für maschinelles Lernen gibt es keine Garantie dafür, dass ein bestimmtes Ergebnis aus menschlicher Perspektive richtig wirkt.






