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


# Analisando páginas da web
{: #analyzing-webpages}

O {{site.data.keyword.nlushort}} permite analisar texto das páginas da web programaticamente. Quando você fornece um HTML bruto ou uma URL publicamente acessível em sua solicitação de API, o serviço tenta focar a análise no conteúdo principal da página, como o texto de um artigo de notícias ou postagem do blog.

** Como funciona: **

1. Especifique uma URL publicamente acessível com o parâmetro **url** ou envie o HTML bruto no parâmetro **html**.
2. Por padrão, o serviço [limpa](#webpage-cleaning) a página da web para remover texto geralmente indesejado, como propagandas.
3. Se você especificar uma [consulta XPath](#xpath) com o parâmetro **xpath**, o serviço usará a consulta para selecionar elementos específicos da página para incluir na análise. Se **clean** estiver configurado como `false` quando você usar **xpath**, somente o resultado da consulta XPath será analisado.

## Limpeza da web
{: #webpage-cleaning}

Por padrão, o serviço "limpa" as páginas da web antes de serem analisadas. As tentativas de limpeza de página da web para remover conteúdo geralmente indesejado, como propagandas e outros textos que podem interferir na análise do conteúdo principal da página.

Para desativar a limpeza de página da web, configure o parâmetro **clean** como `false`. O exemplo a seguir desativa a limpeza da página da web.

```bash
curl --user "apikey:{apikey}" \
"{url}/v1/analyze?version=2018-09-21" \
--request POST \
--header "Content-Type: application/json" \
--data '{
  "url": "http://newsroom.ibm.com/Guerbet-and-IBM-Watson-Health-Announce-Strategic-Partnership-for-Artificial-Intelligence-in-Medical-Imaging-Liver" "features": {
    "concepts": {}
  },
  "return_analyzed_text": true,
  "clean": false
}'
```
{: pre}


## Analisando elementos específicos de uma página da web com XPath
{: #xpath}

O parâmetro **xpath** permite que você use uma consulta XPath para analisar partes específicas de uma página da web. Para saber mais sobre o XPath, consulte os recursos a seguir.

  - [ Tutorial do W3Schools XPath ](https://www.w3schools.com/xml/xpath_intro.asp)
  - [ XPath na Wikipédia ](https://wikipedia.org/wiki/XPath)

O comportamento do parâmetro **xpath** depende do valor do parâmetro **clean**: 

  - **clean** = `true` (padrão): os resultados da consulta XPath serão anexados ao texto da página da web limpa antes que o texto combinado seja analisado.
  - **clean** = `false`: somente os resultados da consulta XPath serão analisados.

### Incluindo texto de elementos específicos na análise
{: #analyze-cleaned-and-xpath}

Por padrão, o parâmetro **clean** é configurado como `true` e os resultados de uma consulta XPath são anexados ao texto da página da web limpa após um caractere de nova linha, antes que o texto combinado seja analisado. Isso pode ser útil se você deseja incluir elementos na análise que, de outra forma, seriam removidos pela limpeza de página da web. O exemplo a seguir usa o parâmetro **xpath** para incluir o título e o subtítulo da página da web de exemplo na análise.

**Arquivo *parameters.json* de exemplo**
```json
{
  "url": "http://newsroom.ibm.com/Guerbet-and-IBM-Watson-Health-Announce-Strategic-Partnership-for-Artificial-Intelligence-in-Medical-Imaging-Liver", "features": {
    "concepts": {}
  },
  "return_analyzed_text": true,
  "xpath": "//div[@class='wd_title wd_language_left' or @class='wd_subtitle wd_language_left']"
}
```
{: codeblock}

** Solicitação de exemplo **
```bash
curl --user "apikey:{apikey}" \
"{url}/v1/analyze?version=2018-09-21" \ --request POST \ --header "Content-Type: application/json" \ --data @parameters.json
```
{: pre}


### Analisando texto somente de elementos específicos
{: #analyze-xpath-results-only}

Para analisar somente o resultado de uma consulta XPath, use o parâmetro **xpath** e configure o parâmetro **clean** como `false`. O exemplo a seguir analisa apenas o título e o subtítulo da página da web de exemplo.

**Arquivo *parameters.json* de exemplo**
```json
{
  "url": "http://newsroom.ibm.com/Guerbet-and-IBM-Watson-Health-Announce-Strategic-Partnership-for-Artificial-Intelligence-in-Medical-Imaging-Liver", "features": {
    "concepts": {}
  },
  "return_analyzed_text": true,
  "xpath": "//div[@class='wd_title wd_language_left' or @class='wd_subtitle wd_language_left']",
  "clean": false
}
```
{: codeblock}

** Solicitação de exemplo **
```bash
curl --user "apikey:{apikey}" \
"{url}/v1/analyze?version=2018-09-21" \ --request POST \ --header "Content-Type: application/json" \ --data @parameters.json
```
{: pre}
