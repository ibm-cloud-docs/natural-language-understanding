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

# 疑難排解
{: #troubleshooting}

如果 {{site.data.keyword.nlushort}} 發生問題，下列疑難排解提示可能會有幫助。
{:shortdesc}

## 實體與關係實體類型不一致
{: #inconsistent-entity-types}

實體與關係特性的實體類型系統不一定會一致。對於部分語言及版本日期，關係結果將包含與實體結果中出現的實體類型不同的實體類型。如需詳細資料，請參閱[實體類型及子類型](/docs/services/natural-language-understanding?topic=natural-language-understanding-entity-type-systems)和[關係類型](/docs/services/natural-language-understanding?topic=natural-language-understanding-relation-type-systems)。 

## 語言偵測不正確
{: #incorrect-language-detection}

對於內含字元數目少於 100 的文字，自動語言偵測可能不正確。如果服務未偵測到您文字的正確語言，您可以[置換自動語言偵測](/docs/services/natural-language-understanding?topic=natural-language-understanding-overriding-language-detection)。

## 要求太多
{: #too-many requests}

如果您看到的是「429：要求太多」錯誤，即表示您的服務實例可能已達到並行要求限制。如需相關資訊，請檢視[使用限制](/docs/services/natural-language-understanding?topic=natural-language-understanding-usage-limits#concurrent-requests)頁面。

## 網頁分析的非預期結果
{: #unexpected-webpage-results}

在某些情況下，分析網頁可能會傳回非預期的結果。若要調查，請嘗試將 **return_analyzed_text** 參數設為 `true`，以檢查要求中所要分析的實際文字。如果[網頁清理](/docs/services/natural-language-understanding?topic=natural-language-understanding-analyzing-webpages#webpage-cleaning)未移除足夠的不必要文字，請考慮使用 [**xpath**](/docs/services/natural-language-understanding?topic=natural-language-understanding-analyzing-webpages#xpath) 參數，將分析焦點放在頁面的特定元素上。

## 特定結果的說明
{: #explanations-for-results}

{{site.data.keyword.nlushort}} 不會提供任何診斷工具來說明特定要求傳回特定結果的原因。此服務的設計目的是為所需數目的文字範本提供正確的結果，但由於所使用機器學習模型的本質，我們並不保證所有特定結果從人類觀點來看都是正確的。






