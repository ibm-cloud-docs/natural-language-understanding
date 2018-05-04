---

copyright:
  years: 2015, 2018
lastupdated: "2018-01-16"

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

# 定制

借助 [{{site.data.keyword.knowledgestudiofull}} ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://ibm.biz/watsonknowledgestudio)，您可以使用定制模型来扩展 {{site.data.keyword.nlushort}}，这些模型可识别您的域独有的定制实体和关系。
{: shortdesc}

## 定制模型入门

> {{site.data.keyword.nlushort}} 免费套餐限制了定制模型的大小和性能。要充分测试定制模型，您需要将其与 {{site.data.keyword.nlushort}} 标准套餐配合使用。

1. 如果您尚未执行 {{site.data.keyword.nlushort}} [入门](/docs/services/natural-language-understanding/getting-started.html)中的操作，请执行这些操作。
1. [获取对 {{site.data.keyword.knowledgestudioshort}} ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/us-en/marketplace/supervised-machine-learning/purchase#product-header-top) 的访问权，然后通过[联机仪表板 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://gateway.watsonplatform.net/knowledge-studio/ui/dashboard/) 登录。
1. 查看 {{site.data.keyword.knowledgestudioshort}} [文档](/docs/services/knowledge-studio/index.html)以了解如何创建定制模型（注释器）并将其部署到 {{site.data.keyword.nlushort}}。
1. 要使用模型，请在 API 请求的 [entities ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/#entities){: new_window} 或 [relations ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/#relations){: new_window} 选项中指定部署的 `model`：
    - 示例 *parameters.json* 文件：

        ```json
        {
          "url": "www.url.example",
          "features": {
            "entities": {
              "model": "your-model-id-here"
            },
            "relations": {
              "model": "your-model-id-here"
            }
          }
        }
        ```
        {: codeblock}
    
    - 示例 curl 请求：

        ```bash
        curl -X POST \
        -H "Content-Type: application/json" \
        -u "{username}":"{password}" \
        -d @parameters.json \
        "https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze?version=2017-02-27"
        ```
        {: pre}

