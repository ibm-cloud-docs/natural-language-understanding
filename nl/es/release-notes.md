---

copyright:
  years: 2015, 2019
lastupdated: "2019-06-21"

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

# Notas del release
{: #release-notes}

Están disponibles las siguientes nuevas características y cambios en el servicio.
{: shortdesc}

## Nuevo proceso de autenticación de API
{: #iam-auth-process }

El 30 de octubre de 2018, las ubicaciones de Dallas (EE. UU. sur) y Frankfurt (Alemania) pasaron a utilizar la autenticación de Identity and Access Management (IAM) basada en señales. (Consulte [Autenticación con señales de IAM ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](/docs/services/watson/getting-started-iam.html) para obtener más información).
{: important}

El servicio {{site.data.keyword.nlushort}} tiene un nuevo proceso de autenticación de API para instancias de servicio que están alojadas en las ubicaciones siguientes:

- Dallas a partir del 30 de octubre de 2018
- Frankfurt a partir del 30 de octubre de 2018
- Londres
- Sídney a partir del 29 de mayo de 2018
- Tokio
- Washington, DC a partir del 12 de junio de 2018

{{site.data.keyword.cloud_notm}} está migrando a la autenticación de IAM (Identity and Access Management) basada en señales. Con algunas instancias de servicio, se autentica en la API mediante IAM.

- Con las *nuevas* instancias de servicio que se creen en las ubicaciones a partir de las fechas indicadas, se autentica en la API mediante IAM. Puede pasar una señal de portadora (bearer) en una cabecera de autorización o una clave de API. Las señales dan soporte a las solicitudes autenticadas sin tener que incluir credenciales de servicio en cada llamada. Las claves de API utilizan la autenticación básica. Aquí encontrará más información acerca de [IAM](/docs/services/watson/getting-started-iam.html).

    Cuando utilice cualquiera de los SDK de Watson, puede pasar la clave de API y dejar que el SDK gestione el ciclo de vida de las señales. Para obtener más información y para ver ejemplos, consulte el apartado sobre [Autenticación ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://{DomainName}/apidocs/natural-language-understanding/#authentication){: new_window} en la consulta de API.
- Para las instancias de servicio _existentes_ que ha creado antes de la fecha indicada, seguirá autenticándose proporcionando el nombre de usuario y la contraseña para la instancia de servicio. Es posible que tenga que migrar estas instancias de servicio a la autenticación de IAM. Se proporcionarán actualizaciones sobre el proceso de migración y las fechas. Para obtener más información sobre la migración, consulte [Migración de instancias de servicio de Cloud Foundry a un grupo de recursos](/docs/resources/instance_migration.html).

Para averiguar qué autenticación debe utilizar, consulte las credenciales de servicio pulsando la instancia de servicio en la [página de recursos de {{site.data.keyword.cloud_notm}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://{DomainName}/resources){: new_window}.


## Versiones de la API del servicio
{: #service-api-versioning}

**Versión de API actual**: 2019-06-04

Las solicitudes de API requieren un parámetro de versión que toma la fecha en el formato `version=AAAA-MM-DD`. Envíe el parámetro version con cada solicitud de API.

Cuando cambiamos la API de forma que sea incompatible con versiones anteriores, ponemos a su disposición una versión inferior. Para aprovechar los cambios de una nueva versión, cambie el valor del parámetro version por la nueva fecha. Si no está listo para actualizar a dicha versión, no cambie la fecha de versión.

### Fechas de versión activas
{: #active-version-dates}

La siguiente tabla muestra los cambios de comportamiento del servicio para cada fecha de versión. Si pasa a una fecha de versión posterior, se activarán todos los cambios incluidos en las versiones anteriores.

|Fecha de versión|Resumen de cambios|
|---|---|
|[`2019-06-04`](#4-june-2019)| <li>Se ha solucionado un problema que hacía que las solicitudes de entidades con modelos personalizados ignoraran la opción `limit`.</li><li>Ahora el valor predeterminado de `limit` para todas las entidades es 50 para todos los modelos.</li><li>Se ha eliminado el valor máximo de `limit` de 250 entidades.</li>|
|[`2018-11-16`](#16-november-2018)| <li>Versión 2 del sistema de tipos de entidad para el italiano.</li>|
|[`2018-09-21`](#21-september-2018)| <li>Versión 2 del sistema de tipos de entidad para el portugués.</li>|
|[`2018-03-16`](#16-march-2018)| <li>Versión 2 del sistema de tipos de entidad para el francés.</li><li>Versión 2 del sistema de tipos de entidad para el alemán.</li>| 
|[`2017-02-27`](#27-february-2017)| Versión base.| 

## Cambios
{: #changes}

### 21 de junio de 2019
{: #21-june-2019}

- Ahora se devuelve la puntuación de confianza de entidades para las solicitudes de entidades que utilizan modelos de aprendizaje automático personalizados.

### 4 de junio de 2019
{: #4-june-2019}

Se han activado los siguientes cambios al utilizar la fecha de versión `2019-06-04` o posterior.

- Se ha solucionado un problema que hacía que las solicitudes de entidades con modelos personalizados ignoraran la opción `limit`.
- Ahora el valor predeterminado de `limit` para todas las entidades es 50 para todos los modelos.
- Se ha eliminado el valor máximo de `limit` de 250 entidades.

### 29 de mayo de 2019
{: #29-may-2019}

- Se ha mejorado la opción de sentimiento en español.
- Se ha solucionado un problema que podría haber afectado a los resultados de sentimiento con destino si el destino contenía caracteres especiales.
- Se han habilitado los siguientes cambios para las instancias de servicio en Washington DC, Tokio, Londres y Sídney:
  - La opción de sentimiento con destino para solicitudes de entidades que utilizan modelos personalizados se ha habilitado para todos los idiomas que admiten la opción de sentimiento, excepto árabe y ruso.


### 24 de mayo de 2019
{: #24-may-2019}

- Se han mejorado las palabras clave en alemán.
- Se han publicado actualizaciones de sentimiento para inglés en las instancias de servicio de todas las ubicaciones de IBM Cloud excepto Dallas.

### 3 de mayo de 2019
{: #3-may-2019}

- Mejoras en la detección del sentimiento a nivel de documentos en alemán.

### 25 de abril de 2019
{: #25-april-2019}

- Se han habilitado las menciones de entidad para los [modelos personalizados](/docs/services/natural-language-understanding?topic=natural-language-understanding-customizing) basados en reglas. Para ver las menciones en los resultados, establezca la opción `mentions` de `entities` en `true`.
- Se han incorporado explicaciones para los resultados de categorías en inglés. Para ver el texto relevante de la fuente que ha contribuido a cada resultados, establezca la opción `explanation` de `categories` en `true`.

### 19 de marzo de 2019
{: #19-march-2019}

- Se ha añadido soporte experimental para modelos de categorías personalizados creados con {{site.data.keyword.knowledgestudioshort}}. Para empezar, consulte [Creación de un modelo de categorías personalizado](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-create-categories-model).
- Se han mejorado las palabras clave y los conceptos en español.

### 10 de enero de 2019
{: #10-january-2019}

- Las solicitudes para **Listar modelos** y **Suprimir modelo** que no incluyan un parámetro de fecha de versión ahora devuelven errores `400` en lugar de respuestas correctas.
- Se ha mejorado el rendimiento de las entidades para idiomas distintos del inglés.

### 14 de diciembre de 2018
{: #14-december-2018}

- Ahora puede crear instancias del servicio {{site.data.keyword.nlushort}} en la ubicación Londres de IBM Cloud.
- Se ha añadido soporte para relaciones en portugués.
- Se ha añadido soporte para las relaciones en italiano.
- Se ha añadido un parámetro `limit` para solicitudes de categorías que controla el número de categorías que se devuelven, con un máximo de 10.
- Se ha mejorado la precisión en el sentimiento en japonés y en alemán.

### 6 de diciembre de 2018
{: #6-december-2018}

- Se ha mejorado la precisión para las categorías en italiano, las palabras clave, las entidades y las categorías.

### 27 de noviembre de 2018
{: #27-november-2018}

- Se ha mejorado la calidad de los resultados de palabras clave para entradas en inglés, francés, japonés y portugués.
- Ahora las palabras clave con diferentes mayúsculas y minúsculas aparecen en los resultados como la misma palabra clave.
- El método **Get models** ahora devuelve campos adicionales que puede utilizar para gestionar modelos personalizados en diversos despliegues.
  - `version`: serie de versión proporcionada por el usuario procedente de {{site.data.keyword.knowledgestudioshort}}
  - `version_description`: descripción proporcionada por el usuario de esta versión procedente de {{site.data.keyword.knowledgestudioshort}} (por ejemplo, lo que ha cambiado desde la versión anterior)
  - `workspace_id`: un ID que proporciona {{site.data.keyword.knowledgestudioshort}} y que permanece constante durante despliegues repetidos procedentes del mismo espacio de trabajo de {{site.data.keyword.knowledgestudioshort}}.
  - `created`: una serie de fecha y hora que indica cuándo se ha desplegado el modelo en NLU.

### 16 de noviembre de 2018
{: #16-november-2018}

- Se han incorporado nuevos algoritmos para el sentimiento y las palabras clave en inglés para mejorar la precisión y el rendimiento.
- Se ha mejorado la precisión y el rendimiento de las palabras clave para entradas en inglés, francés, japonés y portugués.
- Se ha mejorado la precisión y el rendimiento del sentimiento en italiano, así como la precisión de los ejemplos de texto largos.
- Se ha solucionado un problema que hacía que apareciera texto codificado en URL en resultados de eliminación de ambigüedades de entidades en español.
- Se ha incorporado un nuevo modelo de entidades en italiano con el último sistema de tipo de entidad. Encontrará más información sobre el último sistema de tipos en la página [Tipos y subtipos de entidad (Versión 2)](entity-types-v2.html). Si la aplicación es compatible con el nuevo sistema de tipos, cambie el parámetro de fecha de versión de las solicitudes por `2018-11-16` para utilizar el nuevo modelo.

### 9 de noviembre de 2018
{: #9-november-2018}

- Mejora importante en la precisión de las categorías en todos los idiomas a los que se da soporte.

### 8 de noviembre de 2018
{: #8-november-2018}

- Ahora puede crear instancias del servicio {{site.data.keyword.nlushort}} en la ubicación Tokio de IBM Cloud.

### 5 de noviembre de 2018
{: #5-november-2018}

- Se ha añadido soporte para los conceptos en italiano.

### 30 de octubre de 2018	
{: #30-october-2018}	

A partir del 30 de octubre de 2018, las nuevas instancias de servicio creadas en las regiones de Alemania y de EE. UU. sur utilizan la [autenticación de Identity and Access Management (IAM)](#iam-auth-process).	

### 21 de septiembre de 2018
{: #21-september-2018}

- Se ha incorporado soporte para las relaciones en francés y para los conceptos en portugués.
- La opción de sentimiento de destino ahora recibe soporte para palabras clave en francés y en portugués.
- Se han mejorado las palabras clave en francés.
- Se ha mejorado la opción de sentimiento en coreano.
- Se han mejorado las palabras clave y la opción de sentimiento en portugués.
- Se ha incorporado un nuevo modelo de entidades en portugués con el último sistema de tipo de entidad. Encontrará más información sobre el último sistema de tipos en la página [Tipos y subtipos de entidad (Versión 2)](entity-types-v2.html). Si la aplicación es compatible con el nuevo sistema de tipos, cambie el parámetro de fecha de versión de las solicitudes por `2018-09-21` para utilizar el nuevo modelo. 

### 26 de junio de 2018
{: #26-june-2018}

Se ha añadido soporte para entidades y palabras clave en japonés.

- Para entradas en japonés, aún no se da soporte a las entidades siguientes:
  - Number
  - Percent
  - PhoneNumber
  - URL
- Las direcciones IPv6 en entradas en japonés todavía no se detectan como entidades IPAddress.

### 12 de junio de 2018
{: #12-june-2018}

A partir del 12 de junio de 2018, las nuevas instancias de servicio creadas en la región EE. UU. este utilizan la [autenticación de Identity and Access Management (IAM)](#iam-auth-process).

### 6 de junio de 2018
{: #06-june-2018}

- Pequeñas mejoras en resultados de categorías en coreano.

### 29 de mayo de 2018
{: #29-may-2018}

A partir del 29 de mayo de 2018, las nuevas instancias de servicio creadas en la región Sídney utilizan la [autenticación de Identity and Access Management (IAM)](#iam-auth-process).

### 9 de mayo de 2018
{: #9-may-2018}

- Se han mejorado las entidades en alemán.

### 4 de mayo de 2018
{: #4-may-2018}

- Se ha añadido soporte para la opción de sentimiento y los roles semánticos en japonés.
- Se ha mejorado el rendimiento de las solicitudes de metadatos.
- Se ha solucionado un problema que hacía que aparecieran puntuaciones de relevancia `NAN` en los resultados de algunas entidades.
- Se ha solucionado un problema por el que se devolvían códigos de error `400` en solicitudes de palabras clave en alemán y en coreano cuando habrían resultado más adecuados los códigos de error `500`.


### 19 de abril de 2018
{: #19-april-2018}

- Se ha añadido soporte para relaciones en japonés.
- Se han mejorado las palabras clave en alemán.
- Se ha solucionado un problema que hacía que se devolviera texto incorrecto de mención de entidades.
- Se ha solucionado un problema que podría generar resultados poco adecuados para la opción de sentimiento de destino.
- Se ha solucionado un problema que hacía que el valor de `analyzed_text` devuelto incluyera caracteres que no se habían analizado.


### 5 de abril de 2018
{: #05-april-2018}

- Se ha mejorado la captación de contenido de páginas web. Si utiliza el parámetro `url` para analizar páginas web, verá mejores resultados, especialmente en páginas web que utilizan conjuntos de marcos (framesets) y cookies.
- Pequeñas mejoras en conceptos en coreano.

### 16 de marzo de 2018
{: #03-march-2018}

- Se ha añadido soporte para las categorías, las relaciones y los roles semánticos en alemán.
  - Se utiliza un nuevo sistema de tipos de relación para las relaciones en alemán. Para ver los detalles, consulte la página [Tipos de relación (Versión 2)](relations-v2.html).
- Mejoras en las palabras clave y el sentimiento en alemán.
- Se ha añadido soporte para las categorías y los conceptos en japonés.
- Mejoras en la detección de idioma.
- Mejoras en la limpieza de página web.
- Mejoras en los modelos de entidades en francés y alemán. Los modelos utilizan un sistema nuevo de tipos de entidad. Consulte los nuevos tipos y subtipos de entidad en la página [Tipos y subtipos de entidad (Versión 2)](entity-types-v2.html). Si la aplicación es compatible con el nuevo sistema de tipos, cambie el parámetro de fecha de versión de las solicitudes a `2018-03-16` para utilizar el nuevo modelo. Las siguientes son las diferencias entre la _Versión 1_ del sistema de tipos y la _Versión 2_ del sistema de tipos.
  - Nuevos tipos de entidad:
    - Date
    - Duration
    - Measure
    - Money
    - Number&ast;
    - Percent&ast;
    - PhoneNumber&ast;
    - Ordinal
    - Time
    - URL&ast;
  - Tipos de entidad eliminados:
    - Anatomy
    - Award
    - Broadcaster
    - Company
    - Crime
    - Drug
    - HealthCondition
    - Movie
    - MusicGroup
    - NaturalEvent
    - PrintMedia
    - Quantity
    - Sport
    - SportingEvent
    - TelevisionShow
    - Vehicle
  - Nuevo subtipo de entidad:
    - Quantity

&ast;Este tipo de entidad no es detectable todavía en el texto en francés.



### 25 de enero de 2018
{: #25-january-2018}

- Ya se admite el [modelo personalizado](customizing.html) en chino (simplificado) para entidades y relaciones.

### 12 de enero de 2018
{: #12-january-2018}

- Se ha añadido soporte para los conceptos en alemán.

### 15 de diciembre de 2017
{: #15-december-2017}

- Ya se admite el [modelo personalizado](customizing.html) en holandés para entidades y relaciones.
- El [soporte de idioma francés](language-support.html#french) ahora incluye los conceptos.
- El modelo de sentimiento en francés se ha mejorado para ofrecer mejores resultados.
- El modelo de detección de idioma es más rápido y detecta más idiomas en general. Para conocer la lista completa de idiomas, consulte [Idiomas detectables](detectable-languages.html).

  Los siguientes idiomas son nuevas adiciones a la lista:
  - Bielorruso (be)
  - Bihari (bh)
  - Dhivehi (dv)
  - Gallego (gl)
  - Luganda (lg)
  - Inuktitut (iu)
  - Javanés (jv)
  - Canarés (kn)
  - Jemer (km)
  - Ruandés (rw)
  - Laosiano (lo)
  - Malayalam (ml)
  - Maratí (mr)
  - Oriya (or)
  - Panyabí (pa)
  - Gaélico escocés (gd)
  - Cingalés (si)
  - Tamil (ta)
  - Télugu (te)
  - Yídish (yi)

  Los siguientes idiomas ya no son detectables:
  - Bretón (br)
  - Chamorro (ch)
  - Esperanto (eo)
  - Feroés (fo)
  - Hausa (ha)
  - Ndebele (nr)
  - Ojibwa (oj)

### 28 de noviembre de 2017
{: #28-november-2017}

- **Menciones de entidad.** Obtenga las ubicaciones de las menciones de entidad en las solicitudes de `entities` añadiendo la opción `"mentions": true`.
    
    Ejemplo de cuerpo de solicitud `POST /analyze`:
    
    ```json
    {
      "text": "Intel planned to announce Monday a laptop-computer chip that combines an Intel processor and an AMD graphics unit.",
      "features": {
        "entities": {
          "mentions": true
        }
      }
    }
    ```
    {: codeblock}
    
    Respuesta de ejemplo:
    
    ```json
    {
      "usage": {
        "text_units": 1,
        "text_characters": 114,
        "features": 1
      },
      "language": "en",
      "entities": [
        {
          "type": "Company",
          "text": "Intel",
          "relevance": 0.33,
          "mentions": [
            {
              "text": "Intel",
              "location": [
                0,
                5
              ]
            },
            {
              "text": "Intel",
              "location": [
                73,
                78
              ]
            }
          ],
          "disambiguation": {
            "subtype": [
              "OperatingSystemDeveloper",
              "ProcessorManufacturer",
              "SoftwareDeveloper"
            ],
            "name": "Intel",
            "dbpedia_resource": "http://dbpedia.org/resource/Intel"
          },
          "count": 2
        },
        {
          "type": "Company",
          "text": "AMD",
          "relevance": 0.33,
          "mentions": [
            {
              "text": "AMD",
              "location": [
                96,
                99
              ]
            }
          ],
          "disambiguation": {
            "subtype": [
              "ProcessorManufacturer"
            ],
            "name": "Advanced Micro Devices",
            "dbpedia_resource": "http://dbpedia.org/resource/Advanced_Micro_Devices"
          },
          "count": 1
        }
      ]
    }
    ```
    {: codeblock}
    
### 17 de noviembre de 2017
{: #17-november-2017}

- El **[soporte de idioma coreano](language-support.html#korean)** se ha ampliado para incluir las características siguientes:

    - Entidades
    - Palabras clave
    - Roles semánticos


### 30 de julio de 2017
{: #30-july-2017}

- Puede controlar los costes mediante el parámetro opcional `limit_text_characters` para limitar el número de caracteres que se procesan. Por ejemplo:

```
{
  "text": "The United States of America, commonly known as the United States (U.S.) or America, is a federal republic composed of 50 states, a federal district, five major self-governing territories, and various possessions. Forty-eight of the fifty states and the federal district are contiguous and located in North America between Canada and Mexico. The state of Alaska is in the northwest corner of North America, bordered by Canada to the east and across the Bering Strait from Russia to the west.",
  "features": {
    "entities": {}
  },
  "limit_text_characters": 50,
  "return_analyzed_text": true
}
```

- Cada carácter cuenta como un carácter, independientemente de si se trata de un carácter de un solo byte o un carácter de varios bytes.

- Para la medición, un elemento de {{site.data.keyword.nlushort}} sigue siendo una característica (también conocido como un enriquecimiento) por una unidad de texto. Una unidad de texto son 10.000 caracteres o menos.

- Para obtener información detallada sobre precios, [{{site.data.keyword.nlushort}}](https://console.bluemix.net/catalog/services/natural-language-understanding) en el catálogo de {{site.data.keyword.cloud}}.

- Además de añadir el parámetro `limit_text_characters`, se han realizado los siguientes cambios en el truncamiento y los límites de tamaño de texto:

  - Todos los textos de más de 50.000 caracteres se truncarán antes de procesarlos. Anteriormente, el truncamiento se basaba en kilobytes, y un kilobyte equivalía a 1024 bytes.

  - Se devuelve un mensaje informativo en la respuesta cuando se trunca el texto de más de 50.000 caracteres.

  - El tamaño de límite de texto para los modelos personalizados se ha incrementado de 10.000 a 50.000 caracteres.

  - Se ha añadido la información de uso a la respuesta para aclarar el número de elementos de {{site.data.keyword.nlushort}} que se utilizan en cada solicitud. Por ejemplo:

```
{
  "usage": {
    "text_units": 5,
    "text_characters": 41186,
    "features": 1
  },
  ...
}
```


### 8 de mayo de 2017
{: #8-may-2017}

- Se ha actualizado el modelo de puntuación del tono de emoción. El conjunto de datos de entrenamiento se ha ampliado, el diseño de la característica ha cambiado y, como resultado, el modelo tiene una mayor precisión en nuestro conjunto de datos de referencia.

### 27 de marzo de 2017
{: #27-march-2017}

- Se han mejorado los modelos de entidad y sentimiento, lo que significa que cuando se llame a dichas características, se obtendrán mejores resultados.
- Ahora se admiten modelos personalizados de {{site.data.keyword.knowledgestudioshort}} en francés, alemán, italiano y portugués en las relaciones.

### 15 de marzo de 2017
{: #15-march-2017}

Hemos publicado actualizaciones al modelo de puntuación del tono de las emociones. El conjunto de datos de entrenamiento se ha ampliado y, como resultado, el modelo tiene una mayor precisión en nuestro conjunto de datos de referencia.

### 27 de febrero de 2017
{: #27-february-2017}

El servicio Natural Language Understanding ahora está disponible a nivel general (GA).
