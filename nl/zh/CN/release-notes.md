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

# 发行说明

对服务提供了以下新功能和更改。
{: shortdesc}

## 服务 API 版本控制

**当前 API 版本**：2018-03-16

API 请求需要 version 参数采用格式为 `version=YYYY-MM-DD` 的日期。请随每个 API 请求一起发送 version 参数。

我们以向后不兼容的方式更改 API 时，会发布一个新的次版本。要利用新版本中的更改，请将 version 参数的值更改为新日期。如果尚未准备好更新到该版本，请勿更改版本日期。

## 更改

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

&ast; 在法语文本中尚不能检测到此实体类型。



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

- 更新了情绪语气评分模型。扩展了培训数据集并变更了特征工程，因此模型在基准数据集上具有更高精度。

### 2017 年 3 月 27 日
{: #27-march-2017}

- 改进了实体和观点模型，这意味着调用这些特征时，将获得更好的结果。
- 关系现在支持采用法语、德语、意大利语和葡萄牙语的 {{site.data.keyword.knowledgestudioshort}} 定制模型。

### 2017 年 3 月 15 日
{: #15-march-2017}

发布了对情绪语气评分模型的更新。扩展了培训数据集，因此模型在基准数据集上具有更高精度。

### 2017 年 2 月 27 日
{: #27-february-2017}

Natural Language Understanding 服务现在为 GA。

