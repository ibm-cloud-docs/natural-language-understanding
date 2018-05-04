---

copyright:
  years: 2015, 2018
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

# Límites de utilización

Se aplican los siguientes límites de uso y restricciones a las instancias de servicio de {{site.data.keyword.nlushort}}.
{: shortdesc}

## Límite de texto analizado

{{site.data.keyword.nlushort}} trunca el texto analizado que contiene más de 50.000 caracteres de un solo byte o de varios bytes. Para ver el texto que cuenta para este límite en las solicitudes, establezca el parámetro `return_analyzed_text` en `true`.

Puede establecer un límite de caracteres menor con el parámetro `limit_text_characters`. Si le interesa analizar sólo una pequeña parte del contenido, esto puede ayudarle a evitar gastos excesivos.

Ejemplo de objeto de parámetros:
```json
{
  "url": "ibm.com",
  "limit_text_characters": 10000,
  "return_analyzed_text": true,
  "features": {
    "concepts": {}
  }
}
```

## Límite de solicitudes simultáneas

Cada instancia de servicio de {{site.data.keyword.nlushort}} está limitada a 30 solicitudes simultáneas. Es posible que este límite disminuya en las instancias de servicio en los planes Lite y estándar cuando el sistema soporta un tráfico excepcionalmente intenso. Por ejemplo, una aplicación que realice 35 solicitudes simultáneas desde una sola instancia de servicio, superará el límite de solicitudes simultáneas por cinco solicitudes, en las que se devolverá el error `429: Demasiadas solicitudes`.

Para aumentar el límite de solicitudes simultáneas, [abra una incidencia de soporte](https://ibm.biz/ibmcloudsupport).


## Soporte de idioma

En función de cómo utilice el servicio, se aplican diferentes restricciones de idioma. Para obtener detalles, consulte la página [Soporte de idioma](language-support.html).


