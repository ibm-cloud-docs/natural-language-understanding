---

copyright:
  years: 2015, 2018
lastupdated: "2018-12-19"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:important: .important}
{:note: .note}
{:deprecated: .deprecated}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:javascript: .ph data-hd-programlang='javascript'}
{:go: .ph data-hd-programlang='go'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}
{:download: .download}
{:apikey: data-credential-placeholder='apikey'}
{:url: data-credential-placeholder='url'}
{:hide-dashboard: .hide-dashboard}

# Guía de aprendizaje de iniciación
{: #getting-started}

Esta breve guía de aprendizaje contiene una introducción a la API de {{site.data.keyword.nlushort}} con solicitudes de ejemplo y enlaces con recursos adicionales.
{:shortdesc}

## Antes de empezar
{: #before-you-begin}

- {: hide-dashboard} Cree una instancia del servicio:
    1.  Vaya a la página [{{site.data.keyword.nlushort}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://{DomainName}/catalog/services/natural-language-understanding){: new_window} del catálogo de {{site.data.keyword.Bluemix_notm}}.
    2.  Regístrese para obtener una cuenta de {{site.data.keyword.Bluemix_notm}} gratuita o inicie una sesión.
    3.  Pulse **Crear**.
- Copie las credenciales para autenticarse en la instancia de servicio:
    1.  En la página **Gestionar**, pulse **Mostrar** para ver las credenciales.
    2.  Copie los valores de `Clave de API` y `URL`.
- Asegúrese de que tiene el mandato `curl`:
    - En los ejemplos se utiliza el mandato `curl` para llamar a los métodos de la interfaz HTTP. Instale la versión correspondiente a su sistema operativo desde [curl.haxx.se ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://curl.haxx.se/){: new_window}. Instale la versión que da soporte al protocolo SSL (Secure Sockets Layer). Asegúrese de incluir el archivo binario instalado en la variable de entorno `PATH`.

En esta guía de aprendizaje se muestra cómo utilizar la API de {{site.data.keyword.nlushort}} desde una interfaz de línea de mandatos. Para descargar las bibliotecas de cliente para diversos lenguajes de programación, consulte los [SDK de Watson](/docs/services/natural-language-understanding?topic=watson-using-sdks#using-sdks).
{:tip}

## Paso 1: Analizar una página web
{: #analyze-sample}

Ejecute el mandato siguiente para analizar una página web para obtener el sentimiento, los conceptos, las categorías, las entidades y las palabras clave. <span class="hide-dashboard">Sustituya `{apikey}` y `{url}` por sus credenciales de servicio.</span>

```bash
curl -X POST -u "apikey:{apikey}"{: apikey} \
"{url}/v1/analyze?version=2018-11-16"{: url} \
--header "Content-Type: application/json" \
--data '{
  "url": "http://newsroom.ibm.com/Guerbet-and-IBM-Watson-Health-Announce-Strategic-Partnership-for-Artificial-Intelligence-in-Medical-Imaging-Liver",
  "features": {
    "sentiment": {},
    "categories": {},
    "concepts": {},
    "entities": {},
    "keywords": {}
  }
}'
```
{:pre}

En el siguiente paso se muestra cómo especificar las opciones que personalizan el análisis de cada característica.

## Paso 2: Analizar frases de destino y palabras clave
{: #analyze-phrase}

{{site.data.keyword.nlushort}} puede analizar frases de destino en el contexto del texto circundante para obtener resultados precisos relacionados con sentimientos y emociones. La opción **targets** correspondiente al sentimiento en el ejemplo siguiente indica al servicio que busque los destinos "apples", "oranges" y "broccoli". Puesto que el texto contiene "apples" y "oranges", se devuelven puntuaciones en cuanto a sentimiento para dichos objetivos.

También puede obtener resultados relacionados con sentimientos y emociones para las entidades y palabras clave que se detectan en el texto. En el ejemplo, la opción **emotion** para palabras clave indica al servicio que analice cada palabra clave detectada para obtener resultados relacionados con emociones.

```bash
curl -X POST -u "apikey:{apikey}"{: apikey} \
"{url}/v1/analyze?version=2018-11-16"{: url} \
--request POST \
--header "Content-Type: application/json" \
--data '{
  "text": "I love apples! I do not like oranges.",
  "features": {
    "sentiment": {
      "targets": [
        "apples",
        "oranges",
        "broccoli"
      ]
    },
    "keywords": {
      "emotion": true
    }
  }
}'
```
{:pre}

## Pasos siguientes
{: #next-steps}

- Revise la [Consulta de API ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://{DomainName}/apidocs/natural-language-understanding){: new_window}.
- Aprenda cómo identificar [entidades y relaciones personalizadas](/docs/services/natural-language-understanding?topic=natural-language-understanding-customizing).
