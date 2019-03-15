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
{:download: .download}

# 故障诊断
{: #troubleshooting}

如果 {{site.data.keyword.nlushort}} 存在问题，那么以下故障诊断技巧可能会有所帮助。
{:shortdesc}

## 实体和关系实体类型不一致
{: #inconsistent-entity-types}

实体和关系特征的实体类型系统并不总是一致的。对于某些语言和版本日期，关系结果将包含与实体结果中显示的实体类型不同的实体类型。有关更多详细信息，请参阅[实体类型和子类型](/docs/services/natural-language-understanding?topic=natural-language-understanding-entity-type-systems)以及[关系类型](/docs/services/natural-language-understanding?topic=natural-language-understanding-relation-type-systems)。 

## 语言检测不正确
{: #incorrect-language-detection}

对于包含的字符数少于 100 个的文本，自动语言检测可能并不准确。如果服务未检测到文本的正确语言，那么可以[覆盖自动语言检测](/docs/services/natural-language-understanding?topic=natural-language-understanding-overriding-language-detection)。

## 请求太多
{: #too-many requests}

如果看到“429: 请求太多”错误，那么服务实例可能达到了并发请求数限制。请查看[使用限制](/docs/services/natural-language-understanding?topic=natural-language-understanding-usage-limits#concurrent-requests)页面以获取更多信息。

## 来自 Web 页面分析的意外结果
{: #unexpected-webpage-results}

在某些情况下，分析 Web 页面可能会返回意外结果。要进行调查，请尝试将 **return_analyzed_text** 参数设置为 `true` 以检查请求中正在分析的实际文本。 在 [Web 页面清理](/docs/services/natural-language-understanding?topic=natural-language-understanding-analyzing-webpages#webpage-cleaning)未除去足够的不需要文本的情况下，请考虑使用 [**xpath**](/docs/services/natural-language-understanding?topic=natural-language-understanding-analyzing-webpages#xpath) 参数来集中分析页面的特定元素。

## 对特定结果的说明
{: #explanations-for-results}

{{site.data.keyword.nlushort}} 不提供任何诊断工具来说明特定请求返回特定结果的原因。该服务旨在为尽可能多的文本样本提供准确的结果，但由于我们使用的机器学习模型的性质，无法保证任何特定结果从人类的角度来看都是正确的。






