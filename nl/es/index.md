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

# Acerca de
{: #about}

Con {{site.data.keyword.nlufull}}, los desarrolladores pueden analizar las características semánticas de entradas de texto, incluidas las categorías, los conceptos, la emoción, las entidades, las palabras clave, los metadatos, las relaciones, los roles semánticos y el sentimiento.
{: shortdesc}

## Características
{: #features}

Envíe solicitudes a la API con texto, HTML o un URL público y especifique uno o varias de las características siguientes para analizar:

### Categorías
{: #categories}

Categorice el contenido utilizando una jerarquía de clasificación de cinco niveles. Consulte [aquí](/docs/services/natural-language-understanding?topic=natural-language-understanding-categories-hierarchy) la lista completa de categorías. Por ejemplo:

**Entrada**
> url: "www.cnn.com"

**Respuesta**
> /news </br>
> /art and entertainment </br>
> /movies and tv/television </br>
> /news </br>
> /international news

### Conceptos
{: #concepts}

Identifique conceptos de alto nivel a los que no necesariamente se hace referencia en el texto. Por ejemplo:

**Entrada**
> text: "Natural Language Understanding uses natural language processing to analyze text."

**Respuesta**
> Linguistics </br>
> Natural language processing </br>
> Natural language understanding

### Emoción
{: #emotion}

Analice la emoción transmitida por frases de destino específicas o por el documento en su conjunto. También puede habilitar el análisis de emociones para entidades y palabras clave que detecta automáticamente el servicio. Por ejemplo:

**Entrada**
> text: "I love apples, but I hate oranges." </br>
> targets: "apples", and "oranges"

**Respuesta**
> "apples": joy </br>
> "oranges": anger

### Entidades
{: #entities}

Busque personas, lugares, sucesos y otros tipos de entidades mencionadas en el contenido. Consulte [aquí](/docs/services/natural-language-understanding?topic=natural-language-understanding-entity-type-systems) la lista completa de tipos y subtipos de entidad. Por ejemplo:

**Entrada**
> text: "IBM is an American multinational technology company headquartered in Armonk, New York, United States, with operations in over 170 countries."

**Respuesta**
> IBM: Company </br>
> Armonk: Location </br>
> New York: Location </br>
> United States: Location

### Palabras clave
{: #keywords}

Busque palabras clave relevantes en el contenido. Por ejemplo:

**Entrada**
>url: "[http://www-03.ibm.com/press/us/en/pressrelease/51493.wss](http://www-03.ibm.com/press/us/en/pressrelease/51493.wss)"

**Respuesta**
>Australian Open </br>
>Tennis Australia </br>
>IBM SlamTracker analytics

### Metadatos
{: #metadata}

Para la entrada de HTML y URL, obtenga el autor de la página web, el título de la página y la fecha de publicación. Por ejemplo:

**Entrada**
>url: "https://www.ibm.com/blogs/think/2017/01/cognitive-grid/"

**Respuesta**
>Author: Stephen Callahan </br>
>Title: Girding the Grid with Cognitive Computing - THINK Blog </br>
>Publication date: January 31, 2017

### Relaciones
{: #relations}

Reconozca cuando están relacionadas dos entidades y determine el tipo de relación. Por ejemplo:

**Entrada**
>text: "The Nobel Prize in Physics 1921 was awarded to Albert Einstein."

**Respuesta**
>"awardedTo" relation between "Noble Prize in Physics" and "Albert Einstein" </br>
>"timeOf" relation between "1921" and "awarded"

### Roles semánticos
{: #semantic-roles}

Analice frases en cuanto a sujeto-acción-objeto e identifique las entidades y las palabras clave que son sujetos u objetos de una acción. Por ejemplo:

**Entrada**
>text: "In 2011, Watson competed on Jeopardy!"

**Respuesta**
>Subject: Watson </br>
>Action: competed </br>
>Object: on Jeopardy

### Sentimiento
{: #sentiment}

Analice el sentimiento de frases de destino específicas y el sentimiento del documento en su conjunto. También puede obtener información de sentimiento de las entidades y las palabras clave detectadas habilitando la opción de sentimiento de dichas características. Por ejemplo:

**Entrada**
>text: "Thank you and have a nice day!"

**Respuesta**
>Positive sentiment (score: 0.91)

## Idiomas soportados
{: #supported-languages}

Consulte la [documentación de soporte de idiomas](/docs/services/natural-language-understanding?topic=natural-language-understanding-language-support) para obtener detalles sobre los idiomas soportados en {{site.data.keyword.nlushort}}.
