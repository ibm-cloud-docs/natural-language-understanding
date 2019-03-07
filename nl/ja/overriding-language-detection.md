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

# 言語検出のオーバーライド
{: #overriding-language-detection}

`/analyze` 要求内の自動言語検出をオーバーライドするには、`parameters` JSON オブジェクトの `language` 属性で言語コードを指定します。

___parameters.json_ ファイルの例:__

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

__curl 要求の例:__

```bash
curl --user "apikey:{apikey}" \
"{url}/v1/analyze?version=2018-09-21" \
--request POST \
--header "Content-Type: application/json" \
--data @parameters.json

```
{: pre}
