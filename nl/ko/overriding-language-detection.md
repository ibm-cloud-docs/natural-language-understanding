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

# 언어 감지 대체

`/analyze` 요청에서 자동 언어 감지를 대체하려면 `parameters` JSON 오브젝트의 `language` 속성에서 언어 코드를 지정하십시오.

__예제 _parameters.json_ 파일__

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

__예제 curl 요청__

```bash
curl -X POST \
-H "Content-Type: application/json" \
-u "{username}":"{password}" \
-d @parameters.json \
"https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze?version=2017-02-27"
```
{: pre}
