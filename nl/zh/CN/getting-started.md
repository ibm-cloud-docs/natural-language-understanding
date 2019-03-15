---

copyright:
  years: 2015, 2018
lastupdated: "2018-12-19"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:important: .important}
{:note: .note}
{:deprecated: .deprecated}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:javascript: .ph data-hd-programlang='javascript'}
{:go: .ph data-hd-programlang='go'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}
{:download: .download}
{:apikey: data-credential-placeholder='apikey'}
{:url: data-credential-placeholder='url'}
{:hide-dashboard: .hide-dashboard}

# 入门教程
{: #getting-started}

此简短教程通过示例请求和指向其他资源的链接介绍了 {{site.data.keyword.nlushort}} API。
{:shortdesc}

## 开始之前
{: #before-you-begin}

- {: hide-dashboard}创建服务的实例：
    1.  转至 {{site.data.keyword.Bluemix_notm}}“目录”中的 [{{site.data.keyword.nlushort}} ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://{DomainName}/catalog/services/natural-language-understanding){: new_window} 页面。
    2.  注册免费的 {{site.data.keyword.Bluemix_notm}} 帐户或登录。
    3.  单击**创建**。
- 复制要用于向服务实例进行认证的凭证：
    1.  在**管理**页面上，单击**显示**以查看凭证。
    2.  复制 `API 密钥`和 `URL` 值。
- 确保您有 `curl` 命令：
    - 示例使用 `curl` 命令来调用 HTTP 接口的方法。通过 [curl.haxx.se ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://curl.haxx.se/){: new_window} 来安装适用于您操作系统的版本。请安装支持安全套接字层 (SSL) 协议的版本。确保在 `PATH` 环境变量上包含安装的二进制文件。

本教程说明了如何通过命令行界面使用 {{site.data.keyword.nlushort}} API。要下载各种编程语言的客户机库，请查阅 [Watson SDK](/docs/services/natural-language-understanding?topic=watson-using-sdks#using-sdks)。
{:tip}

## 第 1 步：分析 Web 页面
{: #analyze-sample}

运行以下命令来分析 Web 页面以获取观点、概念、类别、实体和关键字。<span class="hide-dashboard">将 `{` 和 `{` 替换为您的服务凭证。</span>

```bash
curl -X POST -u "apikey:{apikey}"{: apikey} \
"{url}/v1/analyze?version=2018-11-16"{: url} \
--header "Content-Type: application/json" \
--data '{
  "url": "http://newsroom.ibm.com/Guerbet-and-IBM-Watson-Health-Announce-Strategic-Partnership-for-Artificial-Intelligence-in-Medical-Imaging-Liver",
  "features": {
    "sentiment": {},
    "categories": {},
    "concepts": {},
    "entities": {},
    "keywords": {}
  }
}'
```
{:pre}

下一步演示如何指定用于为每个特征定制分析的选项。

## 第 2 步：分析目标短语和关键字
{: #analyze-phrase}

{{site.data.keyword.nlushort}} 可以在周围文本的上下文中分析目标短语，以获得焦点观点和情绪结果。以下示例中观点的 **targets** 选项指示服务搜索目标“apples”、“oranges”和“brocoli”。由于“apples”和“oranges”位于文本中，因此将为这些目标返回观点分数。

您还可以获取文本中检测到的实体和关键字的观点和情绪结果。在该示例中，关键字的 **emotion** 选项指示服务分析情绪结果中每个检测到的关键字。

```bash
curl -X POST -u "apikey:{apikey}"{: apikey} \
"{url}/v1/analyze?version=2018-11-16"{: url} \
--request POST \
--header "Content-Type: application/json" \
--data '{
  "text": "I love apples! I do not like oranges.",
  "features": {
    "sentiment": {
      "targets": [
        "apples",
        "oranges",
        "broccoli"
      ]
    },
    "keywords": {
      "emotion": true
    }
  }
}'
```
{:pre}

## 后续步骤
{: #next-steps}

- 查看 [API 参考 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://{DomainName}/apidocs/natural-language-understanding){: new_window}。
- 了解如何识别[定制实体和关系](/docs/services/natural-language-understanding?topic=natural-language-understanding-customizing)。
