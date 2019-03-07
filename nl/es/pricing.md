---

copyright:
  years: 2015, 2018
lastupdated: "2018-11-08"

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

# Tarifas
{: #pricing}

{{site.data.keyword.nlushort}} tiene tres planes de precios: Lite, Estándar y Premium.

Esta página contiene información de precios en dólares americanos. Para ver información de precios en su divisa, consulte la página [{{site.data.keyword.nlushort}}](https://{DomainName}/catalog/services/natural-language-understanding) del catálogo de {{site.data.keyword.cloud}}.
{: tip}

## Lite
{: #lite}

El plan Lite es gratuito para los usuarios que desea probar el servicio Natural Language Understanding o crear una prueba de concepto.

**Tarifas**
- 30.000 NLU elementos/mes gratuitos

**Modelo personalizado**
- 1 modelo personalizado gratuito

## Estándar
{: #standard}

Un plan de "pago según uso" recomendado cuando esté listo para pasar la aplicación del nivel de prueba de concepto al de producción.

**Precios** (facturación mensual)
- Nivel 1: 0,003 $/elemento NLU para los primeros 1-250.000 elementos NLU
- Nivel 2: 0,001 $/elemento NLU para entre 250.001 y 5.000.000 elemento NLU
- Nivel 3: 0,0002 $/elemento NLU para los elementos NLU adicionales que pasen de los 5.000.000

**Modelo personalizado** ($/modelo personalizado/mes)
- 800 $ para todos los niveles

## Premium
{: #premium}

Un plan que ofrece un mayor nivel de seguridad y aislamiento para ayudar a los clientes con requisitos de datos confidenciales.

_[Póngase en contacto con el equipo de ventas](https://www.ibm.com/account/reg/us-en/signup?formid=MAIL-watson) para obtener más información._

## ¿Qué es un elemento NLU?
{: #nlu-items}

El uso de API se mide en **elementos NLU**. Un elemento NLU es una **unidad de texto** (hasta 10.000 caracteres de texto), que se analiza para una **característica**, como por ejemplo la de sentimiento.

Para realizar un seguimiento del número de elementos NLU de la solicitud, puede examinar el objeto `usage` de la respuesta. Por ejemplo, el análisis de sentimiento, emoción y palabras clave de 15.000 caracteres de texto devolverá la siguiente información de uso.

```json
"usage": {
  "text_units": 2,
  "text_characters": 15000,
  "features": 3
}
```
{: code}
  
Hay **2** unidades de texto y **3** características en la solicitud, de modo que hay **2 × 3 = 6** elementos NLU.

Las unidades de texto se cuentan por separado para cada solicitud. Si una solicitud analiza 15.000 caracteres y otra solicitud analiza 3.000 caracteres, se cuentan como 3 unidades de texto en total. La primera solicitud tiene 2 unidades de texto y la segunda solicitud tiene 1 unidad de texto.

## Preguntas frecuentes
{: #faq}

### Quiero entender el sentimiento de 20.000 tuits. ¿Cómo puedo calcular lo que pagaré en el plan Estándar?

- Paso 1: Calcule el número de unidades de texto por solicitud<br>
A partir de noviembre de 2018, el número máximo de caracteres permitidos en un tuit es de 280.<br>
Esto se traduce en una unidad de texto por solicitud.

- Paso 2: Calcule el número de características por solicitud<br>
Hay una característica, sentimiento, habilitada en cada solicitud.

- Paso 3: Calcule el número de elementos NLU por solicitud<br>
Elementos NLU = (Número de unidades de texto) × (Número de características)<br>
Elementos NLU = 1 unidad de texto × 1 característica = 1 elemento NLU

- Paso 4: Calcule el número total de elementos NLU <br>
Número total de elementos NLU = (Número de solicitudes) × (Número de elementos NLU por solicitud) <br>
Número total de elementos NLU = 20.000 solicitudes × 1 NLU por solicitud = 20.000 elementos NLU en total

- Paso 5: Calcule el precio del número total de elementos NLU<br>
Para el plan de precios Estándar, los primeros 250.000 elementos NLU se facturan a un precio de 0,003 dólares por elemento<br>
Precio estimado = (Número de elementos NLU) × (Precio por elemento NLU) <br>
Precio estimado = 20.000 elementos NLU × 0,003 $ = 60 $

**Coste total = 60 $**

### Deseo extraer las entidades, las palabras Clave y las categorías de 50.000 documentos con un promedio de 12.000 caracteres por documento. ¿Cuál será el precio estimado en el plan Estándar?
- Paso 1: Calcule el número de unidades de texto por solicitud <br>
Unidades de texto = Número de grupos de 10.000 caracteres o menos <br>
12.000 caracteres por solicitud = 2 unidades de texto por solicitud

- Paso 2: Calcule el número de características por solicitud<br>
Entidades, Palabras clave, Categorías = 3 características

- Paso 3: Calcule el número de elementos NLU por solicitud <br>
Elementos NLU = (Número de unidades de texto) × (Número de características) <br>
Elementos NLU = 2 unidades de datos × 3 características = 6 elementos NLU

- Paso 4: Calcule el número total de elementos NLU <br>
Número total de elementos NLU = (Número de solicitudes o documentos) × (Número de elementos NLU) <br>
Número total de elementos NLU = 50.000 solicitudes × 6 elementos NLU = 300.000 elementos NLU

- Paso 5: Calcule el precio del número total de elementos NLU <br>
Los primeros 250.000 elementos NLU se facturan a un precio de 0,003 dólares por elemento<br>
Los elementos NLU adicionales hasta llegar a 5.000.000 de elementos NLU se facturan a 0,001 $ por elemento<br>
Precio estimado = (250.000 elementos NLU × 0,003 $) + (50.000 elementos NLU × 0,001 $) <br>
Precio estimado = 750 $ + 50 $


**Coste total = 800 $**

### ¿Cómo se calcula el precio del plan Estándar de 15.000 elementos NLU?
- Puesto que los primeros 250.000 elementos NLU tienen un precio de 0,003 $/elemento, los 15.000 elementos NLU se facturan a 0,003 $ por elemento (Nivel 1). El precio estimado sería de 45 $. 

### ¿Cómo se calcula el precio del plan Estándar de 6.000.000 de elementos NLU?
- Puesto que tiene más de 5.000.000 de elementos NLU, los primeros 250.000 elementos NLU se facturan a 0,003 $ por elemento (Nivel 1), los siguientes 4.750.000 elementos NLU se facturan a 0,001 $ por elemento (Nivel 2) y los restantes 1.000.000 de elementos NLU se facturan a 0,0002 $ por elemento (Nivel 3). El precio estimado sería de 5.700 $. 



