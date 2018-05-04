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

# Notas del release

Están disponibles las siguientes nuevas características y cambios en el servicio.
{: shortdesc}

## Versiones de la API del servicio

**Versión de API actual**: 2018-03-16

Las solicitudes de API requieren un parámetro de versión que toma la fecha en el formato `version=AAAA-MM-DD`. Envíe el parámetro version con cada solicitud de API.

Cuando cambiamos la API de forma que sea incompatible con versiones anteriores, ponemos a su disposición una versión inferior. Para aprovechar los cambios de una nueva versión, cambie el valor del parámetro version por la nueva fecha. Si no está listo para actualizar a dicha versión, no cambie la fecha de versión.

## Cambios

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

