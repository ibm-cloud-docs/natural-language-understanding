---

copyright:
  years: 2015, 2017
lastupdated: "2017-11-03"

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

# 入门教程
在此简短教程中，我们将以分析一些样本文本来获取观点的方式介绍 {{site.data.keyword.nlushort}}。
{:shortdesc}

## 开始之前
{: #before-you-begin}

- 创建服务的实例：
    - {: download} 如果您看到此信息，说明您已创建服务实例。现在，请获取凭证。
    - 通过服务创建项目：
        1.  转至 {{site.data.keyword.watson}} 开发者控制台[服务 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.{DomainName}/developer/watson/services){: new_window} 页面。
        1.  选择 {{site.data.keyword.nlushort}}，单击**添加服务**，然后注册免费 {{site.data.keyword.Bluemix_notm}} 帐户或登录。
        1.  输入 `sentiment-tutorial` 作为项目名称，然后单击**创建项目**。
- 复制要用于向服务实例进行认证的凭证：
    - {: download} 在服务仪表板（您正在查看的内容）中：
        1.  单击**服务凭证**选项卡。
        1.  单击**操作**下面的**查看凭证**。
        1.  复制 `username`、`password` 和 `url` 值。
        {: download}
    - 在开发者控制台中 **sentiment-tutorial** 项目的**凭证**部分中，复制 `"natural_language_understanding"` 的 `username`、`password` 和 `url` 值。
- 确保您有 cURL：
    - 示例会使用 cURL 来调用 HTTP 接口的方法。通过 [curl.haxx.se ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://curl.haxx.se/){: new_window} 来安装适用于您操作系统的版本。请安装支持安全套接字层 (SSL) 协议的版本。确保在 `PATH` 环境变量上包含安装的二进制文件。

<!-- Remove this text after dedicated instances have the Developer Console: begin -->

如果使用的是 {{site.data.keyword.Bluemix_dedicated_notm}}，请在“目录”的 [{{site.data.keyword.nlushort}} ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.{DomainName}/catalog/services/natural-language-understanding/){: new_window} 页面中创建服务实例。有关如何查找服务凭证的详细信息，请参阅 [Watson 服务的服务凭证 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](/docs/services/watson/getting-started-credentials.html#getting-credentials-manually){: new_window}。

<!-- Remove this text after dedicated instances have the Developer Console: end -->

## 第 1 步：分析样本内容以获取观点
{: #analyze-sample}

首先，分析一些样本文本的观点。打开命令行界面，并运行以下命令来调用 `GET /v1/analyze` 方法，用于分析样本文本以获取观点和关键字。使用在上一步中复制的服务凭证来替换 `{username}` 和 `{password}`：

```bash
curl --user "{username}":"{password}" \
"https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze?version=2017-02-27&text=I%20still%20have%20a%20dream%2C%20a%20dream%20deeply%20rooted%20in%20the%20American%20dream%20%E2%80%93%20one%20day%20this%20nation%20will%20rise%20up%20and%20live%20up%20to%20its%20creed%2C%20%22We%20hold%20these%20truths%20to%20be%20self%20evident%3A%20that%20all%20men%20are%20created%20equal.&features=sentiment,keywords"
```
{:pre}

## 第 2 步：返回关键字信息
{: #analyze-keywords}

先前的调用返回了整个文本的观点信息。现在，展开结果以返回专门针对每个关键字的观点分析。包含 **keywords.sentiment** 参数并将其设置为 `true`。使用您的信息替换 `{username}` 和 `{password}`。

```bash
curl --user "{username}":"{password}" \
"https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze?version=2017-02-27&text=I%20still%20have%20a%20dream%2C%20a%20dream%20deeply%20rooted%20in%20the%20American%20dream%20%E2%80%93%20one%20day%20this%20nation%20will%20rise%20up%20and%20live%20up%20to%20its%20creed%2C%20%22We%20hold%20these%20truths%20to%20be%20self%20evident%3A%20that%20all%20men%20are%20created%20equal.&features=sentiment,keywords&keywords.sentiment=true"
```
{:pre}

## 第 3 步：以短语为目标
{: #analyze-phrase}

现在，可通过将短语 `the%20American%20dream%20` 包含到 **sentiment.targets** 参数中，以特定内容为目标来查看句子或短语级别的分析（而不是文档或关键字分析）。请务必使用您的信息来替换 `{username}` 和 `{password}`。

```bash
curl --user "{username}":"{password}" \
"https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze?version=2017-02-27&text=I%20still%20have%20a%20dream%2C%20a%20dream%20deeply%20rooted%20in%20the%20American%20dream%20one%20day%20this%20nation%20will%20rise%20up%20and%20live%20up%20to%20its%20creed%20We%20hold%20these%20truths%20to%20be%20self%20evident%3A%20that%20all%20men%20are%20created%20equal.&features=sentiment,keywords&keywords.sentiment=true&sentiment.targets=the%20American%20dream"
```
{:pre}

## 后续步骤
{: #next-steps}

完成了！本教程只是简单演示了 {{site.data.keyword.nlushort}} 的基本功能。有关此 API 的功能的更多信息，请参阅以下资源：

- 查看 [API 参考 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/){: new_window} 以了解每个参数的详细信息和示例。
- 了解如何识别[定制实体和关系](/docs/services/natural-language-understanding/customizing.html)。
