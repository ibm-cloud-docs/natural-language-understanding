---

copyright:
  years: 2015, 2019
lastupdated: "2019-03-20"

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
{: #customizing}

Con [{{site.data.keyword.knowledgestudiofull}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/watson/services/knowledge-studio/), puede ampliar {{site.data.keyword.nlushort}} con modelos personalizados que identifiquen entidades, relaciones y categorías personalizadas exclusivas de su dominio.
{: shortdesc}

## Iniciación a los modelos personalizados
{: #getting-started-with-custom-models}

> El plan gratuito de {{site.data.keyword.nlushort}} limita el tamaño y el rendimiento del modelo personalizado. Para probar un modelo personalizado en su totalidad, deberá utilizarlo con el plan estándar de {{site.data.keyword.nlushort}}.

1. Si aún no lo ha hecho, [empiece a trabajar](/docs/services/natural-language-understanding?topic=natural-language-understanding-getting-started) con {{site.data.keyword.nlushort}}.
2. [Empiece a trabajar con {{site.data.keyword.knowledgestudioshort}}](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-wks_tutintro#wks_tutintro).
3. Cree un modelo personalizado.
   1. Para crear un modelo personalizado de entidades y relaciones, consulte [Creación de un modelo de aprendizaje automático](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-wks_tutml_intro). 
   2. También puede crear un modelo de entidades personalizado con un modelo basado en reglas. Consulte [Creación de un modelo basado en reglas](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-wks_tutrule_intro) para obtener más información.
   3. Para crear un modelo de categorías personalizado, consulte [Creación de un modelo de categorías personalizado](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-create-categories-model).
4. [Despliegue el modelo en {{site.data.keyword.nlushort}}](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-publish-ml#wks_manlu)
5. Para utilizar el modelo, especifique el `modelo (model)` que ha desplegado en las opciones de [entidades (entities) ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://{DomainName}/apidocs/natural-language-understanding#entities){: new_window}, [relaciones (relations) ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://{DomainName}/apidocs/natural-language-understanding#relations){: new_window} o [categorías (categories) ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://{DomainName}/apidocs/natural-language-understanding#categories){: new_window} de la solicitud de API:
    - Archivo *parameters.json* de ejemplo:

        ```json
        {
          "url": "www.url.example",
          "features": {
            "categories": {
              "model": "your-model-id-here"
            },
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
        curl --user "apikey":"{apikey}" \
        "{url}/v1/analyze?version=2018-11-16" \
        --request POST \
        --header "Content-Type: application/json" \
        --data @parameters.json
        ```
        {: pre}

## Supresión de un modelo personalizado
{: #deleting-a-custom-model}

El número de modelos personalizados que despliega en {{site.data.keyword.nlushort}} afecta a su factura de {{site.data.keyword.nlushort}}, en función de su [plan de precios](https://www.ibm.com/cloud/watson-natural-language-understanding/pricing). Para evitar incurrir en cargos por un modelo que ya no utilice, [elimine el despliegue del modelo con {{site.data.keyword.knowledgestudioshort}}](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-publish-ml#undeploy-view-model) o elimine el despliegue del modelo con el método **[Suprimir modelo](https://{DomainName}/apidocs/natural-language-understanding#delete-model)**.

Ejemplo de solicitud curl:

```bash
curl --user "apikey":"{apikey}" \
"{url}/v1/models/{model_id}?version=2018-10-30" \
--request DELETE
```
{: pre}


## Soporte de idiomas para modelos personalizados
{: #language-support-for-custom-models}

Consulte las columnas *Soporte de modelos personalizados* de las tablas de la página [Soporte de idiomas](/docs/services/natural-language-understanding?topic=natural-language-understanding-language-support) para ver los modelos personalizados que reciben soporte en cada idioma.

### Sentimiento de destino para entidades de modelos personalizados
{: #targeted-sentiment-for-custom-entities}

Solo en la versión en inglés, puede obtener puntuaciones de sentimientos para cada entidad de modelo personalizado que detecte el servicio estableciendo la opción `sentiment: true` en el objeto entities. Ningún otro idioma da soporte al sentimiento de destino para las entidades de modelo personalizado.
