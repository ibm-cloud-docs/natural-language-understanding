---

copyright:
  years: 2015, 2017
lastupdated: "2017-07-21"

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

# Substitution de la détection de langue 

Pour substituer la détection de langue automatique dans les demandes
`/analyze`, spécifiez un code de langue dans l'attribut
`language` de l'objet JSON `parameters`.


__Exemple de fichier _parameters.json___

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

__Exemple de demande curl__

```bash
curl -X POST \
-H "Content-Type: application/json" \
-u "{username}":"{password}" \
-d @parameters.json \
"https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze?version=2017-02-27"
```
{: pre}
