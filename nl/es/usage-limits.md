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

# Límites de utilización
{: #usage-limits}

Se aplican los siguientes límites de uso y restricciones a las instancias de servicio de {{site.data.keyword.nlushort}}.
{: shortdesc}

## Límite de texto analizado
{: #analyzed-text}

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
{: #concurrent-requests}

Cada instancia de servicio de {{site.data.keyword.nlushort}} está limitada a 30 solicitudes simultáneas. Es posible que este límite disminuya en las instancias de servicio en los planes Lite y estándar cuando el sistema soporta un tráfico excepcionalmente intenso. Por ejemplo, una aplicación que realice 35 solicitudes simultáneas desde una sola instancia de servicio, superará el límite de solicitudes simultáneas por cinco solicitudes, en las que se devolverá el error `429: Demasiadas solicitudes`.

Para aumentar el límite de solicitudes simultáneas, [abra una incidencia de soporte](https://ibm.biz/ibmcloudsupport).

## Límite de tamaño del modelo personalizado para los planes de precios Lite
{: #custom-models}

Existe un límite de tamaño para los modelos personalizados de {{site.data.keyword.knowledgestudioshort}} que se despliegan en instancias de servicio de {{site.data.keyword.nlushort}} en planes de precios Lite. Para eliminar el límite de tamaño de modelo personalizado, actualice la instancia de servicio de {{site.data.keyword.nlushort}} a un plan de precios de pago. Encontrará sus instancias de servicio en la {{site.data.keyword.cloud_notm}} [página de recursos](https://{DomainName}/resources).

## Soporte de idioma
{: #language-support}

En función de cómo utilice el servicio, se aplican diferentes restricciones de idioma. Para obtener detalles, consulte la página [Soporte de idioma](/docs/services/natural-language-understanding?topic=natural-language-understanding-language-support).


