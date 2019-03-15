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

# 定制
{: #customizing}

借助 [{{site.data.keyword.knowledgestudiofull}} ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://ibm.biz/watsonknowledgestudio)，您可以使用定制模型来扩展 {{site.data.keyword.nlushort}}，这些模型可识别您的域独有的定制实体和关系。
{: shortdesc}

## 定制模型入门
{: #getting-started-with-custom-models}

> {{site.data.keyword.nlushort}} 免费套餐限制了定制模型的大小和性能。要充分测试定制模型，您需要将其与 {{site.data.keyword.nlushort}} 标准套餐配合使用。

1. 如果您尚未执行 {{site.data.keyword.nlushort}} [入门](/docs/services/natural-language-understanding?topic=natural-language-understanding-getting-started)中的操作，请执行这些操作。
2. [{{site.data.keyword.knowledgestudioshort}} 入门](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-wks_tutintro#wks_tutintro)。
3. [使用 {{site.data.keyword.knowledgestudioshort}} 创建机器学习模型](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-wks_tutml_intro#wks_tutml_intro)。
4. [将模型部署到 {{site.data.keyword.nlushort}}](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-publish-ml#wks_manlu)
5. 要使用模型，请在 API 请求的 [entities ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://{DomainName}/apidocs/natural-language-understanding#entities){: new_window} 或 [relations ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://{DomainName}/apidocs/natural-language-understanding#relations){: new_window} 选项中指定部署的 `model`：
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
        curl --user "apikey":"{apikey}" \
        "{url}/v1/analyze?version=2018-09-21" \
        --request POST \
        --header "Content-Type: application/json" \
        --data @parameters.json
        ```
        {: pre}

## 删除定制模型
{: #deleting-a-custom-model}

根据[价格套餐](https://www.ibm.com/cloud/watson-natural-language-understanding/pricing)，您部署到 {{site.data.keyword.nlushort}} 的定制模型的数量会影响 {{site.data.keyword.nlushort}} 帐单。为了避免针对不再使用的模型收费，请[使用 {{site.data.keyword.knowledgestudioshort}} 取消部署模型](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-publish-ml#undeploy-view-model)，或使用**[删除模型](https://{DomainName}/apidocs/natural-language-understanding#delete-model)**方法取消部署模型。

示例 curl 请求：

```bash
curl --user "apikey":"{apikey}" \
"{url}/v1/models/{model_id}?version=2018-10-30" \
--request DELETE
```
{: pre}


## 定制模型的语言支持
{: #language-support-for-custom-models}

检查[语言支持](/docs/services/natural-language-understanding?topic=natural-language-understanding-language-support)页面上的表中的*定制模型支持*列，以查看每种语言支持的定制模型。

### 定制模型实体的目标观点
{: #targeted-sentiment-for-custom-entities}

仅对于英语，可以通过在实体对象中设置 `sentiment: true` 选项来获取服务检测到的每个定制模型实体的观点分数。定制模型实体没有其他语言支持的目标观点。
