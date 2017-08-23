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

# チュートリアルの概説
この短いチュートリアルでは、感情に関するサンプル・テキストを分析することにより、{{site.data.keyword.nlushort}} (自然言語理解) について紹介します。
{:shortdesc}

## ステップ 1: ログインし、サービス・インスタンスを作成して、資格情報を取得します
{: #create-service}

{{site.data.keyword.nlushort}} サービス・インスタンス用の資格情報を既にご存じの場合は、このステップをスキップしてください。
{: tip}

1.  [「{{site.data.keyword.nlushort}} サービス」](https://console.{DomainName}/catalog/services/natural-language-understanding/)に移動し、無料の {{site.data.keyword.Bluemix_notm}} アカウントに申し込むか、あるいはログインします。
1.  ログインした後、**「サービス名」**フィールドに `sentiment-tutorial` と入力し、**「作成」**をクリックします。
1.  以下の手順で、資格情報をコピーします。
    1.  **「サービス資格情報」**をクリックします。
    1.  **「アクション」**の下の**「資格情報の表示」**をクリックします。
    1.  `username` と `password` の値をコピーします。

## ステップ 2: 感情に関するサンプルの内容を分析します
{: #analyze-sample}

最初に、サンプル・テキストの感情を分析します。次のコマンドを発行して、`GET /v1/analyze` メソッドを呼び出します。これにより、感情に関するサンプル・テキストとキーワードを分析します。以下の `{username}` と `{password}` を、前のステップでコピーしたサービス資格情報に置き換えてください。

```bash
curl --user "{username}":"{password}" \
"https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze?version=2017-02-27&text=I%20still%20have%20a%20dream%2C%20a%20dream%20deeply%20rooted%20in%20the%20American%20dream%20%E2%80%93%20one%20day%20this%20nation%20will%20rise%20up%20and%20live%20up%20to%20its%20creed%2C%20%22We%20hold%20these%20truths%20to%20be%20self%20evident%3A%20that%20all%20men%20are%20created%20equal.&features=sentiment,keywords"
```
{:pre}

## ステップ 3: キーワード情報を返します
{: #analyze-keywords}

前の呼び出しでは、テキスト全体の感情情報が返されました。次に、結果を拡張して、具体的に個々のキーワードに関する感情分析を返します。**keywords.sentiment** パラメーターを組み込み、それを `true` に設定します。`{username}` と `{password}` をご自分の情報に置き換えてください。

```bash
curl --user "{username}":"{password}" \
"https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze?version=2017-02-27&text=I%20still%20have%20a%20dream%2C%20a%20dream%20deeply%20rooted%20in%20the%20American%20dream%20%E2%80%93%20one%20day%20this%20nation%20will%20rise%20up%20and%20live%20up%20to%20its%20creed%2C%20%22We%20hold%20these%20truths%20to%20be%20self%20evident%3A%20that%20all%20men%20are%20created%20equal.&features=sentiment,keywords&keywords.sentiment=true"
```
{:pre}

## ステップ 4: 句を分析対象とします
{: #analyze-phrase}

次に、(文書またはキーワードの分析ではなく) 特定の内容を対象として、文レベルまたは句レベルの分析を見るために、**sentiment.targets** パラメーターに `the%20American%20dream%20` という句を含めます。`{username}` と `{password}` をご自分の情報に置き換えることを忘れないでください。

```bash
curl --user "{username}":"{password}" \
"https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze?version=2017-02-27&text=I%20still%20have%20a%20dream%2C%20a%20dream%20deeply%20rooted%20in%20the%20American%20dream%20one%20day%20this%20nation%20will%20rise%20up%20and%20live%20up%20to%20its%20creed%20We%20hold%20these%20truths%20to%20be%20self%20evident%3A%20that%20all%20men%20are%20created%20equal.&features=sentiment,keywords&keywords.sentiment=true&sentiment.targets=the%20American%20dream"
```
{:pre}

## 次のステップ
{: #next-steps}

これで完了です。このチュートリアルでは、{{site.data.keyword.nlushort}} で実現できる機能のほんの少しを学んだにすぎません。この API の機能について詳しくは、以下のリソースを参照してください。

- 個々のパラメーターの詳細および例については、[API リファレンス![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/ "外部リンク・アイコン"){: new_window}を参照してください。
- [カスタム・エンティティーおよび関係![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/watson/developercloud/doc/natural-language-understanding/customizing.html "外部リンク・アイコン"){: new_window}を識別する方法を学習してください。
