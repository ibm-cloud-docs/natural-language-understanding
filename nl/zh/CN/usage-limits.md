---

copyright:
  years: 2015, 2018
lastupdated: "2018-03-16"

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

# 使用限制

以下使用限制和局限性适用于 {{site.data.keyword.nlushort}} 服务实例。
{: shortdesc}

## 对所分析文本的限制

如果所分析的文本中包含的单字节或多字节字符数超过 50,000 个，那么 {{site.data.keyword.nlushort}} 会截断该文本。要在请求中查看计入此限制的文本，请将 `return_analyzed_text` 参数设置为 `true`。

可以使用 `limit_text_characters` 参数来设置更小的字符限制。如果您只想分析少量内容，那么设置更小的字符限制可帮助您避免产生过高开销。

示例参数对象：
```json
{
  "url": "ibm.com",
  "limit_text_characters": 10000,
  "return_analyzed_text": true,
  "features": {
    "concepts": {}
  }
}
```

## 并发请求限制

每个 {{site.data.keyword.nlushort}} 服务实例的并发请求数限制为 30 个。在系统遇到异常繁忙的流量时，对于轻量套餐和标准套餐上的服务实例，此限制可能会降低。例如，如果一个应用程序从单个服务实例同时发出 35 个请求，这比并发请求限制多出 5 个请求，因此会有 5 个请求返回 `429: 请求太多`错误。

要增大并发请求限制，请[开具支持凭单](https://ibm.biz/ibmcloudsupport)。


## 语言支持

根据您使用服务的方式，不同的语言限制适用。有关详细信息，请参阅[语言支持](language-support.html)页面。


