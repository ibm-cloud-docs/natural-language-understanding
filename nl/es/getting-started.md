---

copyright:
  years: 2015, 2017
lastupdated: "2017-11-03"

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

# Guía de aprendizaje de iniciación
En esta breve guía de aprendizaje se presenta {{site.data.keyword.nlushort}} analizando el sentimiento de un texto de ejemplo.
{:shortdesc}

## Antes de empezar
{: #before-you-begin}

- Cree una instancia del servicio:
    - {: download} Si ve esto, significa que ha creado la instancia del servicio. Ahora, obtenga las credenciales.
    - Cree un proyecto a partir de un servicio:
        1.  Vaya a la página [Servicios ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.{DomainName}/developer/watson/services){: new_window} de la consola del desarrollador de {{site.data.keyword.watson}}.
        1.  Seleccione {{site.data.keyword.nlushort}}, pulse **Añadir servicios** y regístrese para una cuenta gratuita de {{site.data.keyword.Bluemix_notm}} o inicie una sesión.
        1.  Escriba `sentiment-tutorial` como nombre de proyecto y pulse **Crear proyecto**.
- Copie las credenciales para autenticarse en la instancia de servicio:
    - {: download} Desde el panel de control del servicio (lo que está viendo):
        1.  Pulse el separador **Credenciales de servicio**.
        1.  Pulse **Ver credenciales** bajo **Acciones**.
        1.  Copie los valores de `username`, `password` y `url`.
        {: download}
    - Desde el proyecto **sentiment-tutorial** en la consola del desarrollador, copie los valores de `username`, `password` y `url` de `"natural_language_understanding"` de la sección **Credenciales**.
- Asegúrese de que tiene cURL:
    - En los ejemplos se utiliza cURL para llamar a métodos de la interfaz HTTP. Instale la versión correspondiente a su sistema operativo desde [curl.haxx.se ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://curl.haxx.se/){: new_window}. Instale la versión que da soporte al protocolo SSL (Secure Sockets Layer). Asegúrese de incluir el archivo binario instalado en la variable de entorno `PATH`.

<!-- Remove this text after dedicated instances have the Developer Console: begin -->

Si utiliza {{site.data.keyword.Bluemix_dedicated_notm}}, cree la instancia del servicio desde la página [{{site.data.keyword.nlushort}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.{DomainName}/catalog/services/natural-language-understanding/){: new_window} en el catálogo. Para obtener detalles sobre cómo encontrar las credenciales de servicio, consulte [Credenciales de servicio para servicios de Watson ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](/docs/services/watson/getting-started-credentials.html#getting-credentials-manually){: new_window}.

<!-- Remove this text after dedicated instances have the Developer Console: end -->

## Paso 1: Analizar el sentimiento de un contenido de ejemplo
{: #analyze-sample}

Primero, analice el sentimiento de un texto de ejemplo. Abra una interfaz de línea de mandatos y ejecute el mandato siguiente para llamar al método `GET /v1/analyze`, que analiza el sentimiento y las palabras clave de un texto de ejemplo. Sustituya `{username}` y `{password}` por las credenciales del servicio que ha copiado en el paso anterior:

```bash
curl --user "{username}":"{password}" \
"https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze?version=2017-02-27&text=I%20still%20have%20a%20dream%2C%20a%20dream%20deeply%20rooted%20in%20the%20American%20dream%20%E2%80%93%20one%20day%20this%20nation%20will%20rise%20up%20and%20live%20up%20to%20its%20creed%2C%20%22We%20hold%20these%20truths%20to%20be%20self%20evident%3A%20that%20all%20men%20are%20created%20equal.&features=sentiment,keywords"
```
{:pre}

## Paso 2: Devolver información de palabras clave
{: #analyze-keywords}

La llamada anterior ha devuelto información de sentimiento de todo el texto. Ahora amplíe los resultados para devolver el análisis de sentimiento de cada una de las palabras clave. Incluye el parámetro **keywords.sentiment** y establézcalo en `true`. Sustituya `{username}` y `{password}` por su información.

```bash
curl --user "{username}":"{password}" \
"https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze?version=2017-02-27&text=I%20still%20have%20a%20dream%2C%20a%20dream%20deeply%20rooted%20in%20the%20American%20dream%20%E2%80%93%20one%20day%20this%20nation%20will%20rise%20up%20and%20live%20up%20to%20its%20creed%2C%20%22We%20hold%20these%20truths%20to%20be%20self%20evident%3A%20that%20all%20men%20are%20created%20equal.&features=sentiment,keywords&keywords.sentiment=true"
```
{:pre}

## Paso 3: Definir una frase como objetivo
{: #analyze-phrase}

Ahora defina contenido específico como objetivo para ver un análisis a nivel de oración o a nivel de frase (en lugar del análisis de un documento o de palabras clave) incluyendo la frase `the%20American%20dream%20` en el parámetro **sentiment.targets**. No olvide sustituir `{username}` y `{password}` por su información.

```bash
curl --user "{username}":"{password}" \
"https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze?version=2017-02-27&text=I%20still%20have%20a%20dream%2C%20a%20dream%20deeply%20rooted%20in%20the%20American%20dream%20one%20day%20this%20nation%20will%20rise%20up%20and%20live%20up%20to%20its%20creed%20We%20hold%20these%20truths%20to%20be%20self%20evident%3A%20that%20all%20men%20are%20created%20equal.&features=sentiment,keywords&keywords.sentiment=true&sentiment.targets=the%20American%20dream"
```
{:pre}

## Pasos siguientes
{: #next-steps}

Ya ha acabado. Esta guía de aprendizaje describe de forma muy superficial lo que se puede conseguir con {{site.data.keyword.nlushort}}. Para obtener más información sobre las características de la API, consulte estos recursos:

- Consulte la [Referencia de la API ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/){: new_window} para ver detalles y ejemplos de cada uno de los parámetros.
- Aprenda cómo identificar [entidades y relaciones personalizadas](/docs/services/natural-language-understanding/customizing.html).
