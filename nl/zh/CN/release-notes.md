---

copyright:
  years: 2015, 2019
lastupdated: "2019-06-21"

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

# 发行说明
{: #release-notes}

对服务提供了以下新功能和更改。
{: shortdesc}

## 新的 API 认证过程
{: #iam-auth-process }

2018 年 10 月 30 日，达拉斯（美国南部）和法兰克福（德国）位置转为使用基于令牌的 Identity and Access Management (IAM) 认证。（请参阅[使用 IAM 令牌进行认证 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](/docs/services/watson/getting-started-iam.html) 以了解更多信息。）
{: important}

{{site.data.keyword.nlushort}} 服务针对以下位置中托管的服务实例有新的 API 认证过程：

- 达拉斯，2018 年 10 月 30 日起
- 法兰克福，2018 年 10 月 30 日起
- 伦敦
- 悉尼，2018 年 5 月 29 日起
- 东京
- 华盛顿特区，2018 年 6 月 12 日起

{{site.data.keyword.cloud_notm}} 正在迁移到基于令牌的 Identity and Access Management (IAM) 认证。对于某些服务实例，您使用 IAM 向 API 进行认证。

- 对于在列出的日期或这些日期之后在这些位置中创建的*新*服务实例，您使用 IAM 向 API 进行认证。您可以在授权头中传递不记名令牌，也可以传递 API 密钥。令牌支持已认证的请求，而无需在每次调用中嵌入服务凭证。API 密钥使用基本认证。了解有关 [IAM](/docs/services/watson/getting-started-iam.html) 的更多信息。

    使用任何 Watson SDK 时，都可以传递 API 密钥，并让 SDK 管理令牌的生命周期。有关更多信息和示例，请参阅 API 参考中的[认证 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://{DomainName}/apidocs/natural-language-understanding/#authentication){: new_window}。
- 对于在所指示日期之前创建的_现有_服务实例，将继续通过为服务实例提供用户名和密码来进行认证。最终，需要将这些服务实例迁移到 IAM 认证。将提供有关迁移过程和日期的更新。有关迁移的更多信息，请参阅[将 Cloud Foundry 服务实例迁移到资源组](/docs/resources/instance_migration.html)。

要确定需要使用的认证，请通过单击 [{{site.data.keyword.cloud_notm}} 资源页面 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://{DomainName}/resources){: new_window} 上的服务实例来查看服务凭证。


## 服务 API 版本控制
{: #service-api-versioning}

**当前 API 版本**：2019-06-04

API 请求需要 version 参数采用格式为 `version=YYYY-MM-DD` 的日期。请随每个 API 请求一起发送 version 参数。

我们以向后不兼容的方式更改 API 时，会发布一个新的次版本。要利用新版本中的更改，请将 version 参数的值更改为新日期。如果尚未准备好更新到该版本，请勿更改版本日期。

### 活动版本日期
{: #active-version-dates}

下表显示了每个版本日期的服务行为更改。切换到较新版本日期将会激活较早版本中引入的所有更改。

|版本日期|更改汇总|
|---|---|
|[`2019-06-04`](#4-june-2019)| <li>修复了一个错误，该错误导致使用定制模型的实体请求忽略了 `limit` 选项。</li><li>对于所有模型，所有实体请求的缺省 `limit` 值现在为 50。</li><li>已除去最大 `limit` 值 250 个实体。</li>|
|[`2018-11-16`](#16-november-2018)| <li>V2 意大利语实体类型系统。</li>|
|[`2018-09-21`](#21-september-2018)| <li>V2 葡萄牙语实体类型系统。</li>|
|[`2018-03-16`](#16-march-2018)| <li>V2 法语实体类型系统。</li><li>V2 德语实体类型系统。</li>| 
|[`2017-02-27`](#27-february-2017)|基本版本。| 

## 更改
{: #changes}

### 2019 年 6 月 21 日
{: #21-june-2019}

- 针对使用定制机器学习模型的实体请求，现在返回实体置信度分数。

### 2019 年 6 月 4 日
{: #4-june-2019}

使用的版本日期为 `2019-06-04` 或更高版本时，将激活以下更改。

- 修复了一个错误，该错误导致使用定制模型的实体请求忽略了 `limit` 选项。
- 对于所有模型，所有实体请求的缺省 `limit` 值现在为 50。
- 已除去最大 `limit` 值 250 个实体。

### 2019 年 5 月 29 日
{: #29-may-2019}

- 改进了西班牙语观点。
- 修复了一个错误，如果目标包含特殊字符，那么该错误可能会影响目标观点结果。
- 针对位于华盛顿特区、东京、伦敦和悉尼的服务实例，支持以下更改：
  - 针对除了阿拉伯语和俄语之外的所有支持观点的语言，都启用了使用定制模型的实体请求的观点选项。


### 2019 年 5 月 24 日
{: #24-may-2019}

- 改进了德语关键字。
- 英语观点更新发布到除达拉斯之外的所有 IBM Cloud 位置的服务实例。

### 2019 年 5 月 3 日
{: #3-may-2019}

- 改进了德语文档级别的观点检测。

### 2019 年 4 月 25 日
{: #25-april-2019}

- 启用了基于规则的[定制模型](/docs/services/natural-language-understanding?topic=natural-language-understanding-customizing)的实体提及项。要查看结果中的提及项，请将 `mentions` 实体选项设置为 `true`。
- 发布了英语类别结果的说明。要查看产生每个结果的源中的相关文本，请将 `explanation` 类别选项设置为 `true`。

### 2019 年 3 月 19 日
{: #19-march-2019}

- 引入了对使用 {{site.data.keyword.knowledgestudioshort}} 创建的定制类别模型的试验性支持。要开始使用，请参阅[创建定制类别模型](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-create-categories-model)
- 改进了西班牙语关键字和概念。

### 2019 年 1 月 10 日
{: #10-january-2019}

- 不包含版本日期参数的**列出模型**和**删除模型**请求现在会返回 `400` 错误，而不是成功的响应。
- 针对非英语的语言提高了实体性能。

### 2018 年 12 月 14 日
{: #14-december-2018}

- 现在，您可以在 IBM Cloud 伦敦位置创建 {{site.data.keyword.nlushort}} 服务实例。
- 添加了对葡萄牙语关系的支持。
- 添加了对意大利语关系的支持。
- 为类别请求添加了 `limit` 参数，以控制返回的类别数最多不超过 10 个。
- 提高了日语和德语观点的准确性。

### 2018 年 12 月 6 日
{: #6-december-2018}

- 提高了意大利语类别、关键字、实体和类别的准确性。

### 2018 年 11 月 27 日
{: #27-november-2018}

- 提高了英语、法语、日语和葡萄牙语输入的关键字结果的质量。
- 现在，大小写不同的关键字在结果中显示为相同关键字。
- 现在，**获取模型**方法返回其他字段，您可以使用这些字段来管理多个部署中的定制模型。
  - `version`：用户提供的来自 {{site.data.keyword.knowledgestudioshort}} 的版本字符串
  - `version_description`：用户提供的来自 {{site.data.keyword.knowledgestudioshort}} 的此版本描述（例如，在上一版之后有哪些更改）
  - `workspace_id`：{{site.data.keyword.knowledgestudioshort}} 提供的标识，在同一 {{site.data.keyword.knowledgestudioshort}} 工作空间中重复部署时保持不变。
  - `created`：指示模型部署到 NLU 的时间的日期时间字符串。

### 2018 年 11 月 16 日
{: #16-november-2018}

- 发布了针对英语关键字和观点的新算法，提高了准确性和性能。
- 提高了英语、法语、日语和葡萄牙语输入的关键字准确性和性能。
- 提高了意大利语观点的准确性和性能，包括提高了大型文本样本的准确性。
- 修复了导致 URL 编码文本出现在西班牙语实体消岐结果中的错误。
- 发布了使用最新实体类型系统的新的意大利语实体模型。您可以在[实体类型和子类型 (V2)](entity-types-v2.html) 页面上了解最新类型的系统。应用程序与新类型系统兼容时，请将请求中的版本日期参数更改为 `2018-11-16` 以使用新模型。

### 2018 年 11 月 9 日
{: #9-november-2018}

- 所有受支持语言的类别的准确性有重大提高。

### 2018 年 11 月 8 日
{: #8-november-2018}

- 现在，您可以在 IBM Cloud 东京位置创建 {{site.data.keyword.nlushort}} 服务实例。

### 2018 年 11 月 5 日
{: #5-november-2018}

- 添加了对意大利语概念的支持。

### 2018 年 10 月 30 日	
{: #30-october-2018}	

自 2018 年 10 月 30 日起，在德国和美国南部区域创建的新服务实例使用 [Identity and Access Management (IAM) 认证](#iam-auth-process)。	

### 2018 年 9 月 21 日
{: #21-september-2018}

- 添加了对法语关系和葡萄牙语概念的支持。
- 现在，法语和葡萄牙语关键字支持目标观点选项。
- 改进了法语关键字。
- 改进了韩语观点。
- 改进了葡萄牙语关键字和观点。
- 发布了使用最新实体类型系统的新的葡萄牙语实体模型。您可以在[实体类型和子类型 (V2)](entity-types-v2.html) 页面上了解最新类型的系统。应用程序与新类型系统兼容时，请将请求中的版本日期参数更改为 `2018-09-21` 以使用新模型。 

### 2018 年 6 月 26 日
{: #26-june-2018}

添加了对日语实体和关键字的支持。

- 对于日语输入，尚不支持以下实体：
  - Number
  - Percent
  - PhoneNumber
  - URL
- 日语输入中的 IPv6 地址尚无法检测为 IPAddress 实体。

### 2018 年 6 月 12 日
{: #12-june-2018}

自 2018 年 6 月 12 日起，在美国东部区域创建的新服务实例使用 [Identity and Access Management (IAM) 认证](#iam-auth-process)。

### 2018 年 6 月 6 日
{: #06-june-2018}

- 韩语类别结果有小幅改进。

### 2018 年 5 月 29 日
{: #29-may-2018}

自 2018 年 5 月 29 日起，在悉尼区域创建的新服务实例使用 [Identity and Access Management (IAM) 认证](#iam-auth-process)。

### 2018 年 5 月 9 日
{: #9-may-2018}

- 改进了德语实体。

### 2018 年 5 月 4 日
{: #4-may-2018}

- 添加了对日语观点和语义角色的支持。
- 提高了元数据请求的性能。
- 修复了导致 `NAN` 相关性分数出现在某些实体结果中的错误。
- 修复了在德语和韩语关键字请求中返回 `400` 错误代码（返回 `500` 错误代码才更合适）的错误。


### 2018 年 4 月 19 日
{: #19-april-2018}

- 添加了对日语关系的支持。
- 改进了德语关键字。
- 修复了导致返回错误的实体提及文本的错误。
- 修复了可能导致目标观点的结果不佳的错误。
- 修复了导致返回的 `analyzed_text` 中包含未分析字符的错误。


### 2018 年 4 月 5 日
{: #05-april-2018}

- 改进了 Web 页面内容访存。如果使用 `url` 参数来分析 Web 页面，那么您将看到更好的结果，尤其是在使用框架集和 cookie 的 Web 页面中。
- 韩语概念有小幅改进。

### 2018 年 3 月 16 日
{: #03-march-2018}

- 添加了对德语类别、关系和语义角色的支持。
  - 新的关系类型系统用于德语关系。要查看详细信息，请参阅[关系类型 (V2)](relations-v2.html) 页面。
- 改进了德语关键字和观点。
- 添加了对日语类别和概念的支持。
- 改进了语言检测。
- 改进了 Web 页面清理。
- 改进了法语和德语实体模型。模型使用新的实体类型系统。在[实体类型和子类型 (V2)](entity-types-v2.html) 页面上查看新的实体类型和子类型。应用程序与新类型系统兼容时，请将请求中的版本日期参数更改为 `2018-03-16` 以使用新模型。下面是 _V1_ 类型系统与 _V2_ 类型系统之间的差异。
  - 新的实体类型：
    - Date
    - Duration
    - Measure
    - Money
    - Number&ast;
    - Percent&ast;
    - PhoneNumber&ast;
    - Ordinal
    - Time
    - URL&ast;
  - 除去的实体类型：
    - Anatomy
    - Award
    - Broadcaster
    - Company
    - Crime
    - Drug
    - HealthCondition
    - Movie
    - MusicGroup
    - NaturalEvent
    - PrintMedia
    - Quantity
    - Sport
    - SportingEvent
    - TelevisionShow
    - Vehicle
  - 新的实体子类型：
    - Quantity

&ast; 此实体类型在法语文本中还无法检测到。



### 2018 年 1 月 25 日
{: #25-january-2018}

- 简体中文[定制模型](customizing.html)支持现在可用于实体和关系。

### 2018 年 1 月 12 日
{: #12-january-2018}

- 添加了对德语概念的支持。

### 2017 年 12 月 15 日
{: #15-december-2017}

- 荷兰语[定制模型](customizing.html)支持现在可用于实体和关系。
- [法语语言支持](language-support.html#french)现在包含概念。
- 改进了法语观点模型，以交付更好的结果。
- 语言检测模型速度更快，并且总体可检测到更多语言。有关完整的语言列表，请参阅[可检测到的语言](detectable-languages.html)。

  下面是列表中新增的语言：
  - 白俄罗斯语 (be)
  - 比哈尔语 (bh)
  - 迪维西语 (dv)
  - 加利西亚语 (gl)
  - 干达语 (lg)
  - 伊努克提图特语 (iu)
  - 爪哇语 (jv)
  - 卡纳达语 (kn)
  - 高棉语 (km)
  - 卢旺达语 (rw)
  - 老挝语 (lo)
  - 马拉雅拉姆语 (ml)
  - 马拉地语 (mr)
  - 奥利亚语 (or)
  - 旁遮普语 (pa)
  - 苏格兰盖尔语 (gd)
  - 僧伽罗语 (si)
  - 泰米尔语 (ta)
  - 泰卢固语 (te)
  - 意第绪语 (yi)

  无法再检测到以下语言：
  - 布列塔尼语 (br)
  - 查莫罗语 (ch)
  - 世界语 (eo)
  - 法罗语 (fo)
  - 豪萨语 (ha)
  - 恩德贝勒语 (nr)
  - 奥吉布瓦语 (oj)

### 2017 年 11 月 28 日
{: #28-november-2017}

- **实体提及**。通过添加选项 `"mentions":true` 来获取 `entities` 请求中实体提及的位置。
    
    示例 `POST /analyze` 请求主体：
    
    ```json
    {
      "text": "Intel planned to announce Monday a laptop-computer chip that combines an Intel processor and an AMD graphics unit.",
      "features": {
        "entities": {
          "mentions": true
        }
      }
    }
    ```
    {: codeblock}
    
    示例响应：
    
    ```json
    {
      "usage": {
        "text_units": 1,
        "text_characters": 114,
        "features": 1
      },
      "language": "en",
      "entities": [
        {
          "type": "Company",
          "text": "Intel",
          "relevance": 0.33,
          "mentions": [
            {
              "text": "Intel",
              "location": [
                0,
                5
              ]
            },
            {
              "text": "Intel",
              "location": [
                73,
                78
              ]
            }
          ],
          "disambiguation": {
            "subtype": [
              "OperatingSystemDeveloper",
              "ProcessorManufacturer",
              "SoftwareDeveloper"
            ],
            "name": "Intel",
            "dbpedia_resource": "http://dbpedia.org/resource/Intel"
          },
          "count": 2
        },
        {
          "type": "Company",
          "text": "AMD",
          "relevance": 0.33,
          "mentions": [
            {
              "text": "AMD",
              "location": [
                96,
                99
              ]
            }
          ],
          "disambiguation": {
            "subtype": [
              "ProcessorManufacturer"
            ],
            "name": "Advanced Micro Devices",
            "dbpedia_resource": "http://dbpedia.org/resource/Advanced_Micro_Devices"
          },
          "count": 1
        }
      ]
    }
    ```
    {: codeblock}
    
### 2017 年 11 月 17 日
{: #17-november-2017}

- **[韩国语语言支持](language-support.html#korean)**已扩展为包括以下特征：

    - 实体
    - 关键字
    - 语义角色


### 2017 年 7 月 30 日
{: #30-july-2017}

- 可以通过使用可选的 `limit_text_characters` 参数来限制处理的字符数以控制开销。例如：

```
{
  "text": "The United States of America, commonly known as the United States (U.S.) or America, is a federal republic composed of 50 states, a federal district, five major self-governing territories, and various possessions. Forty-eight of the fifty states and the federal district are contiguous and located in North America between Canada and Mexico. The state of Alaska is in the northwest corner of North America, bordered by Canada to the east and across the Bering Strait from Russia to the west.",
  "features": {
    "entities": {}
  },
  "limit_text_characters": 50,
  "return_analyzed_text": true
}
```

- 每个字符计为一个字符，不管该字符是单字节字符还是多字节字符。

- 对于测量，一个 {{site.data.keyword.nlushort}} 项仍然是每个文本单位一个特征（也称为扩充项）。一个文本单位不超过 10,000 个字符。

- 有关详细定价信息，请参阅 {{site.data.keyword.cloud}}“目录”中的 [{{site.data.keyword.nlushort}}](https://console.bluemix.net/catalog/services/natural-language-understanding)。

- 除了添加 `limit_text_characters` 参数外，还对文本大小限制和截断进行了以下更改：

  - 在处理之前，所有超过 50,000 个字符的文本都会进行截断。先前，截断基于千字节执行，其中 1 千字节等于 1024 字节。

  - 截断超过 50,000 个字符的文本后，会在响应中返回一条参考消息。

  - 定制模型的文本限制大小已从 10,000 个字符大幅提升到 50,000 个字符。

  - 向响应添加了使用情况信息，以清楚地表明每个请求使用的 {{site.data.keyword.nlushort}} 项数。例如：

```
{
  "usage": {
    "text_units": 5,
    "text_characters": 41186,
    "features": 1
  },
  ...
}
```


### 2017 年 5 月 8 日
{: #8-may-2017}

- 更新了情绪语气评分模型。扩展了训练数据集并变更了特征工程，因此模型在基准数据集上具有更高精度。

### 2017 年 3 月 27 日
{: #27-march-2017}

- 改进了实体和观点模型，这意味着调用这些特征时，将获得更好的结果。
- 关系现在支持采用法语、德语、意大利语和葡萄牙语的 {{site.data.keyword.knowledgestudioshort}} 定制模型。

### 2017 年 3 月 15 日
{: #15-march-2017}

发布了对情绪语气评分模型的更新。扩展了训练数据集，因此模型在基准数据集上具有更高精度。

### 2017 年 2 月 27 日
{: #27-february-2017}

Natural Language Understanding 服务现在为 GA。
