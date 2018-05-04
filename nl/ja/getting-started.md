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

# チュートリアルの概説
この短いチュートリアルでは、評判についていくつかのサンプル・テキストを分析することにより、{{site.data.keyword.nlushort}} を紹介しています。
{:shortdesc}

## 始めに
{: #before-you-begin}

- サービスのインスタンスを作成します。
    - {: download} これが表示されている場合、サービス・インスタンスは作成済みです。資格情報を入手してください。
    - サービスからプロジェクトを作成します。
        1.  {{site.data.keyword.watson}} Developer Console の[「サービス」![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.{DomainName}/developer/watson/services){: new_window}ページに移動します。
        1.  {{site.data.keyword.nlushort}} を選択し、**「サービスの追加」**をクリックして、無料の {{site.data.keyword.Bluemix_notm}} アカウントに申し込むか、ログインします。
        1.  プロジェクト名として `sentiment-tutorial` を入力し、**「プロジェクトの作成」**をクリックします。
- 認証用の資格情報をサービス・インスタンスにコピーします。
    - {: download} サービス・ダッシュボード (現在表示されている画面) から以下を行います。
        1.  **「サービス資格情報」**タブをクリックします。
        1.  **「アクション」**の下の**「資格情報の表示」**をクリックします。
        1.  `username`、`password`、および `url` の値をコピーします。{: download}
    - Developer Console 内の **sentiment-tutorial** プロジェクトで、**Credentials** セクションから、`"natural_language_understanding"` の `username`、`password`、および `url` の値をコピーします。
- cURL があることを確認します。
    - 例では、cURL を使用して HTTP インターフェースのメソッドを呼び出します。[curl.haxx.se ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://curl.haxx.se/){: new_window} から、ご使用のオペレーティング・システムに対応したバージョンをインストールします。Secure Sockets Layer (SSL) プロトコルをサポートするバージョンをインストールしてください。必ず、インストールしたバイナリー・ファイルを `PATH` 環境変数に含めてください。

<!-- Remove this text after dedicated instances have the Developer Console: begin -->

{{site.data.keyword.Bluemix_dedicated_notm}} を使用する場合は、カタログ内の[「{{site.data.keyword.nlushort}}」![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.{DomainName}/catalog/services/natural-language-understanding/){: new_window}ページからサービス・インスタンスを作成します。サービス資格情報を見つける方法について詳しくは、[「Watson サービスのサービス資格情報」![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](/docs/services/watson/getting-started-credentials.html#getting-credentials-manually){: new_window}を参照してください。

<!-- Remove this text after dedicated instances have the Developer Console: end -->

## ステップ 1: 評判についてサンプル・コンテンツを分析する
{: #analyze-sample}

最初に、サンプル・テキストの評判を分析します。コマンド・ライン・インターフェースを開き、次のコマンドを実行して `GET /v1/analyze` メソッドを呼び出します。このメソッドは評判とキーワードについてサンプル・テキストを分析します。以下の `{username}` と `{password}` を、前のステップでコピーしたサービス資格情報に置き換えてください。

```bash
curl --user "{username}":"{password}" \
"https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze?version=2017-02-27&text=I%20still%20have%20a%20dream%2C%20a%20dream%20deeply%20rooted%20in%20the%20American%20dream%20%E2%80%93%20one%20day%20this%20nation%20will%20rise%20up%20and%20live%20up%20to%20its%20creed%2C%20%22We%20hold%20these%20truths%20to%20be%20self%20evident%3A%20that%20all%20men%20are%20created%20equal.&features=sentiment,keywords"
```
{:pre}

## ステップ 2: キーワード情報を返す
{: #analyze-keywords}

前の呼び出しでは、テキスト全体の評判情報が返されました。次に、結果を拡張して、具体的に個々のキーワードに関する評判分析を返します。**keywords.sentiment** パラメーターを組み込み、それを `true` に設定します。 `{username}` と `{password}` をご自分の情報に置き換えてください。

```bash
curl --user "{username}":"{password}" \
"https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze?version=2017-02-27&text=I%20still%20have%20a%20dream%2C%20a%20dream%20deeply%20rooted%20in%20the%20American%20dream%20%E2%80%93%20one%20day%20this%20nation%20will%20rise%20up%20and%20live%20up%20to%20its%20creed%2C%20%22We%20hold%20these%20truths%20to%20be%20self%20evident%3A%20that%20all%20men%20are%20created%20equal.&features=sentiment,keywords&keywords.sentiment=true"
```
{:pre}

## ステップ 3: 句を分析対象にする
{: #analyze-phrase}

次に、(文書またはキーワードの分析ではなく) 特定のコンテンツを対象として、文レベルまたは句レベルの分析を見るために、**sentiment.targets** パラメーターに `the%20American%20dream%20` という句を含めます。`{username}` と `{password}` をご自分の情報に置き換えることを忘れないでください。

```bash
curl --user "{username}":"{password}" \
"https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze?version=2017-02-27&text=I%20still%20have%20a%20dream%2C%20a%20dream%20deeply%20rooted%20in%20the%20American%20dream%20one%20day%20this%20nation%20will%20rise%20up%20and%20live%20up%20to%20its%20creed%20We%20hold%20these%20truths%20to%20be%20self%20evident%3A%20that%20all%20men%20are%20created%20equal.&features=sentiment,keywords&keywords.sentiment=true&sentiment.targets=the%20American%20dream"
```
{:pre}

## 次のステップ
{: #next-steps}

これで完了です。 このチュートリアルでは、{{site.data.keyword.nlushort}} で実現できる機能のほんの少しを学んだにすぎません。 この API の機能について詳しくは、以下のリソースを参照してください。

- 個々のパラメーターの詳細および例については、[API リファレンス ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/){: new_window}を参照してください。
- [カスタム・エンティティーと関係](/docs/services/natural-language-understanding/customizing.html)の識別方法について学習してください。
