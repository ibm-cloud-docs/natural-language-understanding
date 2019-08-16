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

# 入門チュートリアル
{: #getting-started}

この短いチュートリアルでは、{{site.data.keyword.nlushort}} API および使用例を紹介し、その他の参照資料へのリンクを記載しています。
{:shortdesc}

## 始めに
{: #before-you-begin}

- {: hide-dashboard} サービスのインスタンスを作成します。
    1.  {{site.data.keyword.Bluemix_notm}} カタログの [{{site.data.keyword.nlushort}} ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://{DomainName}/catalog/services/natural-language-understanding){: new_window} ページに移動します。
    2.  無料の {{site.data.keyword.Bluemix_notm}} アカウントを登録するか、ログインします。
    3.  **「作成」**をクリックします。
- 認証用の資格情報をサービス・インスタンスにコピーします。
    1.  **「管理」**ページで、 **「表示」**をクリックして資格情報を表示します。
    2.  `「API キー」`の値と`「URL」`の値をコピーします。
- `curl` コマンドを使用できることを確認します。
    - 例では `curl` コマンドを使用して HTTP インターフェースのメソッドを呼び出します。 [curl.haxx.se ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://curl.haxx.se/){: new_window} から、ご使用のオペレーティング・システムに対応したバージョンをインストールします。 Secure Sockets Layer (SSL) プロトコルをサポートするバージョンをインストールしてください。 必ず、インストールしたバイナリー・ファイルを `PATH` 環境変数に含めてください。

このチュートリアルでは、コマンド・ライン・インターフェースから {{site.data.keyword.nlushort}} API を使用する方法を説明します。 さまざまなプログラミング言語のクライアント・ライブラリーをダウンロードするには、[Watson SDK](/docs/services/natural-language-understanding?topic=watson-using-sdks#using-sdks)を参照してください。
{:tip}

## ステップ 1: Web ページを分析する
{: #analyze-sample}

Web ページを分析する次のコマンドを実行して、評判、概念、カテゴリー、エンティティー、およびキーワードを取得します。 <span class="hide-dashboard">`{apikey}` と `{url}` はご使用のサービス資格情報に置き換えてください。</span>

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
{: pre}

次のステップでは、各フィーチャーの分析をカスタマイズするオプションを指定する方法を説明します。

## ステップ 2: ターゲットの句およびキーワードを分析する
{: #analyze-phrase}

{{site.data.keyword.nlushort}} では、周囲のテキストを考慮してターゲットの句について分析し、対象を絞った評判と感情の結果を得ることができます。 次の例に示す sentiment の **targets** オプションは、「apples」、「oranges」、および「broccoli」というターゲットを検索するようにサービスに指示しています。 「apples」と「oranges」がテキスト内にあるので、これらのターゲットの評判スコアが返されます。

また、テキスト中に検出されたエンティティーとキーワードについての評判と感情の結果も得ることができます。 この例では、keywords の **emotion** オプションで、検出された各キーワードを分析して感情の結果を得るようにサービスに指示しています。

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
{: pre}

## 次のステップ
{: #next-steps}

- [API リファレンス ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://{DomainName}/apidocs/natural-language-understanding){: new_window} を参照してください。
- [カスタム・エンティティーと関係](/docs/services/natural-language-understanding?topic=natural-language-understanding-customizing)の識別方法について学習してください。
