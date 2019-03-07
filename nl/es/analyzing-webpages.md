---

copyright:
  years: 2015, 2018
lastupdated: "2018-10-30"

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


# Análisis de páginas web
{: #analyzing-webpages}

{{site.data.keyword.nlushort}} le permite analizar texto de páginas web mediante programación. Cuando se proporciona HTML sin especificaciones o un URL de acceso público en la solicitud de API, el servicio intenta centrar el análisis en el contenido principal de la página, como por ejemplo en el texto de un artículo de noticias o de una publicación de un blog.

**Cómo funciona:**

1. Especifique un URL de acceso público con el parámetro **url** o envíe el HTML sin especificaciones en el parámetro **html**.
2. De forma predeterminada, el servicio [limpia](#webpage-cleaning) la página web para eliminar el texto que generalmente no se desea, como por ejemplo los anuncios.
3. Si especifica una [consulta XPath](#xpath) con el parámetro **xpath**, el servicio utiliza la consulta para seleccionar elementos específicos de la página que se deben incluir en el análisis. Si el valor de **clean** es `false`
cuando se utiliza **xpath**, solo se analiza el resultado de la consulta XPath.

## Limpieza de páginas web
{: #webpage-cleaning}

De forma predeterminada, el servicio "limpia" las páginas web antes de que se analicen. La limpieza de páginas web intenta eliminar el contenido que generalmente no se desea, como anuncios y otros textos que pueden interferir con el análisis del contenido principal de la página.

Para inhabilitar la limpieza de la página web, establezca el parámetro **clean** en `false`. En el ejemplo siguiente se inhabilita la limpieza de páginas web.

```bash
curl --user "apikey:{apikey}" \
"{url}/v1/analyze?version=2018-09-21" \
--request POST \
--header "Content-Type: application/json" \
--data '{
  "url": "http://newsroom.ibm.com/Guerbet-and-IBM-Watson-Health-Announce-Strategic-Partnership-for-Artificial-Intelligence-in-Medical-Imaging-Liver"
  "features": {
    "concepts": {}
  },
  "return_analyzed_text": true,
  "clean": false
}'
```
{: pre}


## Análisis de elementos específicos de una página web con XPath
{: #xpath}

El parámetro **xpath** le permite utilizar una consulta XPath para analizar partes específicas de una página web. Para obtener más información acerca de XPath, consulte los recursos siguientes.

  - [Guía de aprendizaje de XPath de W3Schools](https://www.w3schools.com/xml/xpath_intro.asp)
  - [XPath en Wikipedia](https://wikipedia.org/wiki/XPath)

El comportamiento del parámetro **xpath** depende del valor del parámetro **clean**: 

  - **clean** = `true` (valor predeterminado): los resultados de la consulta XPath se añaden al texto de la página web limpia antes de que se analice el texto combinado.
  - **clean** = `false`: solo se analizan los resultados de la consulta XPath.

### Inclusión de texto de elementos específicos en el análisis
{: #analyze-cleaned-and-xpath}

De forma predeterminada, el parámetro **clean** tiene el valor `true` y los resultados de una consulta XPath se añaden al texto de la página web limpia después de un carácter de nueva línea antes de que se analice el texto combinado. Esto puede resultar útil si desea incluir elementos en el análisis que, de lo contrario, se eliminarían mediante la limpieza de páginas web. En el ejemplo siguiente se utiliza el parámetro **xpath** para incluir el título y el subtítulo de la página web de ejemplo en el análisis.

**Archivo *parameters.json* de ejemplo**
```json
{
  "url": "http://newsroom.ibm.com/Guerbet-and-IBM-Watson-Health-Announce-Strategic-Partnership-for-Artificial-Intelligence-in-Medical-Imaging-Liver",
  "features": {
    "concepts": {}
  },
  "return_analyzed_text": true,
  "xpath": "//div[@class='wd_title wd_language_left' or @class='wd_subtitle wd_language_left']"
}
```
{: codeblock}

**Solicitud de ejemplo**
```bash
curl --user "apikey:{apikey}" \
"{url}/v1/analyze?version=2018-09-21" \
--request POST \
--header "Content-Type: application/json" \
--data @parameters.json
```
{: pre}


### Análisis de texto procedente solo de elementos específicos
{: #analyze-xpath-results-only}

Para analizar únicamente el resultado de una consulta XPath, utilice el parámetro **xpath** y establezca el parámetro **clean** en `false`. En el ejemplo solo siguiente se analiza el título y el subtítulo de la página web de ejemplo.

**Archivo *parameters.json* de ejemplo**
```json
{
  "url": "http://newsroom.ibm.com/Guerbet-and-IBM-Watson-Health-Announce-Strategic-Partnership-for-Artificial-Intelligence-in-Medical-Imaging-Liver",
  "features": {
    "concepts": {}
  },
  "return_analyzed_text": true,
  "xpath": "//div[@class='wd_title wd_language_left' or @class='wd_subtitle wd_language_left']",
  "clean": false
}
```
{: codeblock}

**Solicitud de ejemplo**
```bash
curl --user "apikey:{apikey}" \
"{url}/v1/analyze?version=2018-09-21" \
--request POST \
--header "Content-Type: application/json" \
--data @parameters.json
```
{: pre}
