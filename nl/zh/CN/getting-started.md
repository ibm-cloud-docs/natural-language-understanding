---

copyright:
  years: 2015, 2017
lastupdated: "2017-06-09"

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

# 入门教程
在此简短的教程中，我们将通过分析一些观点样本文本来介绍 {{site.data.keyword.nlushort}}。
{:shortdesc}

## 第 1 步：登录，创建服务实例并获取凭证
{: #create-service}

如果您已经知道您的 {{site.data.keyword.nlushort}} 服务实例凭证，请跳过此步骤。
{: tip}

1.  转至 [{{site.data.keyword.nlushort}} 服务](https://console.{DomainName}/catalog/services/natural-language-understanding/)，注册一个免费的 {{site.data.keyword.Bluemix_notm}} 帐户或登录。
1.  登录之后，在**服务名称**字段中输入 `sentiment-tutorial`，然后单击**创建**。
1.  复制您的凭证：
    1.  单击**服务凭证**。
    1.  单击**操作**下面的**查看凭证**。
    1.  复制 `username` 和 `password` 值。

## 第 2 步：分析观点的样本内容
{: #analyze-sample}

首先，分析观点的一些样本文本。发出此命令来调用 `GET /v1/analyze` 方法，用于分析观点的样本文本和关键字。使用在上一步中复制的服务凭证来替换 `{username}` 和 `{password}`：

```bash
curl --user "{username}":"{password}" \
"https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze?version=2017-02-27&text=I%20still%20have%20a%20dream%2C%20a%20dream%20deeply%20rooted%20in%20the%20American%20dream%20%E2%80%93%20one%20day%20this%20nation%20will%20rise%20up%20and%20live%20up%20to%20its%20creed%2C%20%22We%20hold%20these%20truths%20to%20be%20self%20evident%3A%20that%20all%20men%20are%20created%20equal.&features=sentiment,keywords"
```
{:pre}

## 第 3 步：返回关键字信息
{: #analyze-keywords}

先前的调用返回了整个文本的观点信息。现在，展开结果以返回专门针对每个关键字的观点分析。包含 **keywords.sentiment** 参数并将其设置为 `true`。使用您的信息替换 `{username}` 和 `{password}`。

```bash
curl --user "{username}":"{password}" \
"https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze?version=2017-02-27&text=I%20still%20have%20a%20dream%2C%20a%20dream%20deeply%20rooted%20in%20the%20American%20dream%20%E2%80%93%20one%20day%20this%20nation%20will%20rise%20up%20and%20live%20up%20to%20its%20creed%2C%20%22We%20hold%20these%20truths%20to%20be%20self%20evident%3A%20that%20all%20men%20are%20created%20equal.&features=sentiment,keywords&keywords.sentiment=true"
```
{:pre}

## 第 4 步：设定目标短语
{: #analyze-phrase}

现在，可通过将短语 `the%20American%20dream%20` 包含到 **sentiment.targets** 参数中，以特定内容为目标来查看句子或短语级别的分析（而不是文档或关键字分析）。请记得用您的信息来替换 `{username}` 和 `{password}`。

```bash
curl --user "{username}":"{password}" \
"https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze?version=2017-02-27&text=I%20still%20have%20a%20dream%2C%20a%20dream%20deeply%20rooted%20in%20the%20American%20dream%20one%20day%20this%20nation%20will%20rise%20up%20and%20live%20up%20to%20its%20creed%20We%20hold%20these%20truths%20to%20be%20self%20evident%3A%20that%20all%20men%20are%20created%20equal.&features=sentiment,keywords&keywords.sentiment=true&sentiment.targets=the%20American%20dream"
```
{:pre}

## 后续步骤
{: #next-steps}

完成了！本教程只是简单演示了 {{site.data.keyword.nlushort}} 的基本功能。有关此 API 功能的更多信息，请参阅以下资源：

- 查看 [API 参考![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/ "外部链接图标"){: new_window}以了解每个参数的详细信息和示例。
- 学习如何识别[定制实体和关系![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/watson/developercloud/doc/natural-language-understanding/customizing.html "外部链接图标"){: new_window}。
