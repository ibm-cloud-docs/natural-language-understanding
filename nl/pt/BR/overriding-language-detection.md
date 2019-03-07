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

# Substituindo a detecção de idioma
{: #overriding-language-detection}

Para substituir a detecção automática de idioma em solicitações `/analyze`, especifique um código de
idioma no atributo `language` do objeto JSON `parameters`.

__Arquivo _parameters.json_ de exemplo__

```json
{
  "text": "...X, Y, Z, now I know my A, B, Cs",
  "features": {
    "semantic_roles": {}
  },
  "language": "en"
}
```
{: codeblock}

__Solicitação curl de exemplo__

```bash
curl --user "apikey:{apikey}" \ "{url}/v1/analyze?version=2018-09-21" \ --request POST \ --header "Content-Type: application/json" \ --data @parameters.json

```
{: pre}
