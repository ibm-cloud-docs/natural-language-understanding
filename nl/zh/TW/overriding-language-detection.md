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

# 置換語言偵測

若要置換 `/analyze` 要求中的自動語言偵測，請在 `parameters` JSON 物件的 `language` 屬性中指定語言碼。

__範例 _parameters.json_ 檔案__

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

__範例 curl 要求__

```bash
curl -X POST \
-H "Content-Type: application/json" \
-u "{username}":"{password}" \
-d @parameters.json \
"https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze?version=2017-02-27"
```
{: pre}
