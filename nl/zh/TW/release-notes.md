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

# 版本注意事項
{: #release-notes}

該服務有下列新增特性和變更。
{: shortdesc}

## 新的 API 鑑別處理程序
{: #iam-auth-process }

在 2018 年 10 月 30 日，達拉斯（美國南部）和法蘭克福（德國）位置轉移為使用記號型 Identity and Access Management (IAM) 鑑別。（如需相關資訊，請參閱[使用 IAM 記號鑑別 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](/docs/services/watson/getting-started-iam.html)。）
{: important}

對於在下列位置進行管理的服務實例，{{site.data.keyword.nlushort}} 服務具有新的 API 鑑別處理程序：

- 達拉斯（自 2018 年 10 月 30 日開始）
- 法蘭克福（自 2018 年 10 月 30 日開始）
- 倫敦
- 雪梨（自 2018 年 5 月 29 日開始）
- 東京
- 華盛頓州（自 2018 年 6 月 12 日開始）

{{site.data.keyword.cloud_notm}} 正在移轉至記號型 Identity and Access Management (IAM) 鑑別。對於某些服務實例，您可以使用 IAM 向 API 進行鑑別。

- 對於您於列出日期或該日期之後在上述位置建立的*新* 服務實例，您可以使用 IAM 向 API 進行鑑別。您可以在「授權」標頭或 API 金鑰中傳遞載送記號。記號支援已鑑別要求，而無需在每個呼叫中內嵌服務認證。API 金鑰使用基本鑑別。請進一步瞭解 [IAM](/docs/services/watson/getting-started-iam.html)。

    當您使用任何 Watson SDK 時，您可以傳遞 API 金鑰，並讓 SDK 管理記號的生命週期。如需相關資訊及範例，請參閱 API 參考資料中的[鑑別 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://{DomainName}/apidocs/natural-language-understanding/#authentication){: new_window}。
- 對於在指出日期之前建立的_現有_ 服務實例，您可以提供服務實例的使用者名稱及密碼來繼續進行鑑別。但最終需要將這些服務實例移轉至 IAM 鑑別。將提供有關移轉處理程序和日期的更新項目。如需移轉的相關資訊，請參閱[將 Cloud Foundry 服務實例移轉至資源群組](/docs/resources/instance_migration.html)。

若要找出要使用的鑑別，請按一下[儀表板 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://{DomainName}/dashboard/apps?watson){: new_window} 上的服務實例來檢視服務認證。


## 服務 API 版本化
{: #service-api-versioning}

**現行 API 版本**：2018-11-16

API 要求需要日期格式為 `version=YYYY-MM-DD` 的版本參數。請隨每一個 API 要求傳送版本參數。

以與舊版不相容的方式來變更 API 時，就會發行新的次要版本。若要利用新版本的變更，請將版本參數的值變更為新日期。如果您尚未更新為該版本，請不要變更您的版本日期。

## 變更
{: #changes}

### 2019 年 1 月 10 日
{: #10-january-2019}

- 不包括版本日期參數的**列出模型**及**刪除模型**要求現在會傳回 `400` 錯誤，而非成功回應。
- 改良英文之外語言的實體效能。

### 2018 年 12 月 14 日
{: #14-december-2018}

- 您現在可以在 IBM Cloud 倫敦位置中建立 {{site.data.keyword.nlushort}} 服務實例。
- 新增對葡萄牙文關係的支援。
- 新增對義大利文關係的支援。
- 對於用來控制傳回種類數目上限為 10 的種類要求新增 `limit` 參數。
- 改良日文及德文觀感的正確性。

### 2018 年 12 月 6 日
{: #6-december-2018}

- 改良義大利文種類、關鍵字、實體及種類的正確性。

### 2018 年 11 月 27 日
{: #27-november-2018}

- 改良英文、法文、日文及葡萄牙文輸入的關鍵字結果品質。
- 現在，具有不同大小寫的關鍵字在結果中顯示為相同的關鍵字。
- **取得模型**方法現在會傳回其他欄位，供您用來管理跨數個部署的自訂模型。
  - `version`：{{site.data.keyword.knowledgestudioshort}} 中使用者提供的版本字串
  - `version_description`：{{site.data.keyword.knowledgestudioshort}} 中這個版本的使用者提供說明（例如，自上一版以來的變更項目）
  - `workspace_id`：{{site.data.keyword.knowledgestudioshort}} 所提供的 ID，從相同的 {{site.data.keyword.knowledgestudioshort}} 工作區重複部署時此 ID 保持不變。
  - `created`：指出模型何時部署至 NLU 的日期時間字串。

### 2018 年 11 月 16 日
{: #16-november-2018}

- 為英文關鍵字及觀感發行新的演算法，以改善正確性及效能。
- 改良英文、法文、日文及葡萄牙文輸入的關鍵字正確性及效能。
- 改良義大利文觀感正確性及效能，包括更佳的大型文字範本正確性。
- 修正導致 URL 編碼文字出現在西班牙文實體釐清結果中的錯誤。
- 發行含有最新實體類型系統的新義大利文實體模型。您可以在[實體類型及字類型（第 2 版）](entity-types-v2.html)頁面中瞭解最新的類型系統。當您的應用程式與新的類型系統相容時，請將您要求中的版本日期參數變更為 `2018-11-16`，以使用新模型。

### 2018 年 11 月 9 日
{: #9-november-2018}

- 所有支援語言中對「種類」正確性的主要改進。

### 2018 年 11 月 8 日
{: #8-november-2018}

- 您現在可以在 IBM Cloud 東京位置中建立 {{site.data.keyword.nlushort}} 服務實例。

### 2018 年 11 月 5 日
{: #5-november-2018}

- 新增對義大利文概念的支援。

### 2018 年 10 月 30 日	
{: #30-october-2018}	

從 2018 年 10 月 30 日開始，在德國及美國南部地區建立的新服務實例會使用 [Identity and Access Management (IAM) 鑑別](#iam-auth-process)。	

### 2018 年 9 月 21 日
{: #21-september-2018}

- 新增對法文關係及葡萄牙文概念的支援。
- 法文和葡萄牙文關鍵字現在支援目標觀感選項。
- 改良法文關鍵字。
- 改良韓國觀感。
- 改良葡萄牙文關鍵字及觀感。
- 發行含有最新實體類型系統的新葡萄牙文實體模型。您可以在[實體類型及字類型（第 2 版）](entity-types-v2.html)頁面中瞭解最新的類型系統。當您的應用程式與新的類型系統相容時，請將您要求中的版本日期參數變更為 `2018-09-21`，以使用新模型。 

### 2018 年 6 月 26 日
{: #26-june-2018}

新增對日文實體及關鍵字的支援。

- 對於日文輸入，尚未支援下列實體：
  - Number
  - Percent
  - PhoneNumber
  - URL
- 日文輸入中的 IPv6 位址還無法偵測為 IPAddress 實體。

### 2018 年 6 月 12 日
{: #12-june-2018}

從 2018 年 6 月 12 日開始，在美國東部地區建立的新服務實例會使用 [Identity and Access Management (IAM) 鑑別](#iam-auth-process)。

### 2018 年 6 月 6 日
{: #06-june-2018}

- 對韓文種類結果的次要改進。

### 2018 年 5 月 29 日
{: #29-may-2018}

從 2018 年 5 月 29 日開始，在雪梨地區建立的新服務實例會使用 [Identity and Access Management (IAM) 鑑別](#iam-auth-process)。

### 2018 年 5 月 9 日
{: #9-may-2018}

- 改良德文實體。

### 2018 年 5 月 4 日
{: #4-may-2018}

- 新增對日文觀感及語意角色的支援。
- 改良 meta 資料要求的效能。
- 修正導致 `NAN` 相關性評分出現在部分實體結果中的錯誤。
- 修正當 `500` 錯誤碼更適合時，在德文及韓文關鍵字要求中傳回 `400` 錯誤碼的錯誤。


### 2018 年 4 月 19 日
{: #19-april-2018}

- 新增對日文關係的支援。
- 改良德文關鍵字。
- 修正導致傳回不正確實體提及文字的錯誤。
- 修正可能導致目標觀感產生不良結果的錯誤。
- 修正導致傳回 `analyzed_text` 以包含未分析字元的錯誤。


### 2018 年 4 月 5 日
{: #05-april-2018}

- 改良網頁內容提取。如果您使用 `url` 參數來分析網頁，您會看到更好的結果，尤其是從使用圖文框及 Cookie 的網頁中。
- 韓文概念的次要改進。

### 2018 年 3 月 16 日
{: #03-march-2018}

- 新增對德文種類、關係及語意角色的支援。
  - 將新的關係類型系統用於德文關係。若要檢視詳細資料，請參閱[關係類型（第 2 版）](relations-v2.html)頁面。
- 改良的德文關鍵字及觀感。
- 新增對日文種類及概念的支援。
- 語言偵測改善。
- 改良的網頁清理。
- 改良的法文及德文實體模型。模型會使用新的實體類型系統。請查看[實體類型及子類型（第 2 版）](entity-types-v2.html)頁面上的新實體類型及子類型。當您的應用程式與新的類型系統相容時，請將您要求中的版本日期參數變更為 `2018-03-16`，以使用新模型。以下是_第 1 版_ 類型系統與_第 2 版_ 類型系統之間的差異。
  - 新的實體類型：
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
  - 已移除的實體類型：
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
  - 新的實體子類型：
    - Quantity

&ast; 在法文文字中，偵測不到此實體類型。



### 2018 年 1 月 25 日
{: #25-january-2018}

- 簡體中文[自訂模型](customizing.html)支援現在可用於實體及關係。

### 2018 年 1 月 12 日
{: #12-january-2018}

- 新增對德文概念的支援。

### 2017 年 12 月 15 日
{: #15-december-2017}

- 荷蘭文[自訂模型](customizing.html)支援現在可用於實體及關係。
- [法文語言支援](language-support.html#french)現在包括概念。
- 已改良法文觀感模型來提供較佳的結果。
- 語言偵測模型的速度較快，而且整體上可偵測到更多的語言。如需完整的語言清單，請參閱[可偵測到的語言](detectable-languages.html)。

  下列語言是清單的新增項目：
  - 白俄羅斯文 (be)
  - 比哈爾文 (bh)
  - 迪貝喜文 (dv)
  - 加利西亞文 (gl)
  - 干達文 (lg)
  - 愛斯基摩文 (iu)
  - 爪哇文 (jv)
  - 坎那達文 (kn)
  - 高棉文 (km)
  - 金亞盧安文 (rw)
  - 寮文 (lo)
  - 馬來亞拉姆文 (ml)
  - 馬拉地文 (mr)
  - 奧里亞文 (or)
  - 旁遮普文 (pa)
  - 蘇格蘭蓋爾文 (gd)
  - 錫蘭文 (si)
  - 泰米爾文 (ta)
  - 泰盧固文 (te)
  - 意第緒文 (yi)

  無法再偵測到下列語言：
  - 布列塔尼亞文 (br)
  - 查摩洛文 (ch)
  - 世界語 (eo)
  - 法羅文 (fo)
  - 豪薩文 (ha)
  - 恩德貝萊文 (nr)
  - 奧吉布瓦語 (oj)

### 2017 年 11 月 28 日
{: #28-november-2017}

- **實體提及。**新增選項 `"mentions": true`，以在 `entities` 要求中取得實體提及的位置。
    
    範例 `POST /analyze` 要求內文：
    
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
    
    範例回應：
    
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

- **[韓文語言支援](language-support.html#korean)**已擴充為包括下列特性：

    - 實體
    - 關鍵字
    - 語意角色


### 2017 年 7 月 30 日
{: #30-july-2017}

- 使用選用的 `limit_text_characters` 參數來限制處理的字元數，即可控制成本。例如：

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

- 不論字元是單位元組字元還是多位元組字元，每一個字元都算一個字元。

- 針對計量，一個 {{site.data.keyword.nlushort}} 項目持續為每一個文字單位一個特性（也稱為強化）。一個文字單位是 10,000 個字元以下。

- 如需詳細定價資訊，請參閱「{{site.data.keyword.cloud}} 型錄」中的 [{{site.data.keyword.nlushort}}](https://console.bluemix.net/catalog/services/natural-language-understanding)。

- 除了新增 `limit_text_characters` 參數之外，還會對文字大小限制及截斷進行下列變更：

  - 處理之前，會截斷所有超過 50,000 個字元的文字。先前，截斷是以 KB 為基礎，而一個 KB 等於 1024 個位元組。

  - 截斷超過 50,000 個字元的文字時，會在回應中傳回參考訊息。

  - 自訂模型的文字限制大小已從 10,000 個字元變成 50,000 個字元。

  - 會將使用情形資訊新增至回應，以瞭解每一個要求所使用的 {{site.data.keyword.nlushort}} 項目數。例如：

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

- 已更新情緒語氣評分模型。已擴充訓練資料集，並且已變更特性工程設計，因此，模型對基準性能測試資料集而言具有更高的精準度。

### 2017 年 3 月 27 日
{: #27-march-2017}

- 已改良實體及觀感模型，這表示當您呼叫這些特性時會取得更好的結果。
- 關係現在支援法文、德文、義大利文及葡萄牙文的 {{site.data.keyword.knowledgestudioshort}} 自訂模型。

### 2017 年 3 月 15 日
{: #15-march-2017}

我們已發行情緒語氣評分模型的更新項目。已擴充訓練資料集，因此，模型對基準性能測試資料集而言具有更高的精準度。

### 2017 年 2 月 27 日
{: #27-february-2017}

Natural Language Understanding 服務現在已 GA。
