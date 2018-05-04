---

copyright:
  years: 2015, 2018
lastupdated: "2018-01-16"

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

# Personalización

Con [{{site.data.keyword.knowledgestudiofull}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://ibm.biz/watsonknowledgestudio), puede ampliar {{site.data.keyword.nlushort}} con modelos personalizados que identifiquen entidades y relaciones personalizadas exclusivas de su dominio.
{: shortdesc}

## Iniciación a los modelos personalizados

> El plan gratuito de {{site.data.keyword.nlushort}} limita el tamaño y el rendimiento del modelo personalizado. Para probar un modelo personalizado en su totalidad, deberá utilizarlo con el plan estándar de {{site.data.keyword.nlushort}}.

1. Si aún no lo han hecho, [empiece a trabajar](/docs/services/natural-language-understanding/getting-started.html) con {{site.data.keyword.nlushort}}.
1. [Obtenga acceso a {{site.data.keyword.knowledgestudioshort}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/us-en/marketplace/supervised-machine-learning/purchase#product-header-top) e inicie sesión en el [panel de control en línea ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://gateway.watsonplatform.net/knowledge-studio/ui/dashboard/).
1. Consulte la [documentación](/docs/services/knowledge-studio/index.html) de {{site.data.keyword.knowledgestudioshort}} para aprender a crear un modelo personalizado (anotador) y desplegarlo en {{site.data.keyword.nlushort}}.
1. Para utilizar el modelo, especifique el `modelo` que ha desplegado en las opciones de [entidades ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/#entities){: new_window} o
[relaciones ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/#relations){: new_window} de la solicitud de API:
    - Archivo *parameters.json* de ejemplo:

        ```json
        {
          "url": "www.url.example",
          "features": {
            "entities": {
              "model": "your-model-id-here"
            },
            "relations": {
              "model": "your-model-id-here"
            }
          }
        }
        ```
        {: codeblock}
    
    - Ejemplo de solicitud curl:

        ```bash
        curl -X POST \
        -H "Content-Type: application/json" \
        -u "{username}":"{password}" \
        -d @parameters.json \
        "https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze?version=2017-02-27"
        ```
        {: pre}

