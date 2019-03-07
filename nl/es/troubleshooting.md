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

# Resolución de problemas
{: #troubleshooting}

Si tiene problemas con {{site.data.keyword.nlushort}}, las siguientes sugerencias sobre resolución de problemas le pueden ayudar.
{:shortdesc}

## Las entidades y los tipos de entidad de relaciones no son coherentes
{: #inconsistent-entity-types}

Los sistemas de tipos de entidad para las características de entidades y de relaciones no siempre son coherentes. En algunos idiomas y fechas de versión, los resultados de relaciones contendrán tipos de entidad distintos de los tipos de entidad que aparecen en los resultados de las entidades. Consulte [Tipos y subtipos de entidad](/docs/services/natural-language-understanding?topic=natural-language-understanding-entity-type-systems) y [Tipos de relación](/docs/services/natural-language-understanding?topic=natural-language-understanding-relation-type-systems) para obtener más información. 

## Detección incorrecta de idioma
{: #incorrect-language-detection}

Es posible que la detección automática de idioma no sea precisa para texto que contenga menos de 100 caracteres. Si el servicio no detecta el idioma correcto del texto, puede [modificar la detección automática de idioma](/docs/services/natural-language-understanding?topic=natural-language-understanding-overriding-language-detection).

## Demasiadas solicitudes
{: #too-many requests}

Si ve el error de "429: Demasiadas solicitudes", es probable que la instancia de servicio haya alcanzado el límite de solicitudes simultáneas. Consulte los [Límites de uso](/docs/services/natural-language-understanding?topic=natural-language-understanding-usage-limits#concurrent-requests) para obtener más información.

## Resultados inesperados del análisis de páginas web
{: #unexpected-webpage-results}

El análisis de una página web puede devolver resultados inesperados en algunos casos. Para investigarlo, intente establecer el parámetro **return_analyzed_text** en `true` para inspeccionar el texto real que se está analizando en la solicitud. Si la operación de [limpieza de la página web](/docs/services/natural-language-understanding?topic=natural-language-understanding-analyzing-webpages#webpage-cleaning) no elimina suficiente texto no deseado, tenga en cuenta la posibilidad de utilizar el parámetro [**xpath**](/docs/services/natural-language-understanding?topic=natural-language-understanding-analyzing-webpages#xpath) para centrar el análisis en elementos específicos de la página.

## Explicaciones de resultados concretos
{: #explanations-for-results}

{{site.data.keyword.nlushort}} no proporciona ninguna herramienta de diagnóstico que explique por qué una solicitud concreta devuelve un resultado determinado. El servicio está diseñado para proporcionar resultados precisos para el mayor número de muestras de texto posible, pero, debido a la naturaleza de los modelos de aprendizaje automático que utilizamos, no hay garantía de que todos los resultados concretos se vean correctamente desde una perspectiva humana.






