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

# Tutorial Introdução
Neste breve tutorial, apresentamos o {{site.data.keyword.nlushort}}, analisando um texto de amostra para obter a impressão.
{:shortdesc}

## Etapa 1: Efetue login, crie a instância de serviço e obtenha suas credenciais
{: #create-service}

Caso já saiba as suas credenciais para a instância de serviço do {{site.data.keyword.nlushort}}, ignore esta etapa.
{: tip}

1.  Acesse o [serviço
do {{site.data.keyword.nlushort}}](https://console.{DomainName}/catalog/services/natural-language-understanding/) e se inscreva para obter uma conta gratuita do {{site.data.keyword.Bluemix_notm}} ou efetue login.
1.  Depois de efetuar login, digite `sentiment-tutorial` no campo **Nome do serviço** e clique em **Criar**.
1.  Copie suas credenciais:
    1.  Clique em **Credenciais de serviço**.
    1.  Clique em **Visualizar credenciais** em **Ações**.
    1.  Copie os valores `username` e `password`.

## Etapa 2: Analise o conteúdo de amostra para obter a impressão
{: #analyze-sample}

Analise, primeiro, a impressão de algum texto de amostra. Emita este comando para chamar o método `GET /v1/analyze`, que analisa o texto de amostra para obter a impressão e as palavras-chave. Substitua `{username}` e `{password}` pelas credenciais de serviço copiadas na etapa anterior:

```bash
curl --user "{username}":"{password}" \
"https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze?version=2017-02-27&text=I%20still%20have%20a%20dream%2C%20a%20dream%20deeply%20rooted%20in%20the%20American%20dream%20%E2%80%93%20one%20day%20this%20nation%20will%20rise%20up%20and%20live%20up%20to%20its%20creed%2C%20%22We%20hold%20these%20truths%20to%20be%20self%20evident%3A%20that%20all%20men%20are%20created%20equal.&features=sentiment,keywords"
```
{:pre}

## Etapa 3: Retorne informações de palavra-chave
{: #analyze-keywords}

A chamada anterior retornou informações de impressão para todo o texto. Agora, expanda os resultados para retornar a análise de sentimentos especificamente em cada uma das palavras-chave. Inclua o parâmetro **keywords.sentiment** e configure-o como `true`. Substitua `{username}` e `{password}` por suas informações.

```bash
curl --user "{username}":"{password}" \
"https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze?version=2017-02-27&text=I%20still%20have%20a%20dream%2C%20a%20dream%20deeply%20rooted%20in%20the%20American%20dream%20%E2%80%93%20one%20day%20this%20nation%20will%20rise%20up%20and%20live%20up%20to%20its%20creed%2C%20%22We%20hold%20these%20truths%20to%20be%20self%20evident%3A%20that%20all%20men%20are%20created%20equal.&features=sentiment,keywords&keywords.sentiment=true"
```
{:pre}

## Etapa 4: Delimite uma frase
{: #analyze-phrase}

Agora, delimite o conteúdo específico para ver uma análise em nível de sentença ou em nível de frase (em vez de uma análise de documento ou de palavra-chave) ao incluir a frase `the%20American%20dream%20` no parâmetro **sentiment.targets**. Não se esqueça de substituir `{username}` e `{password}` por suas informações.

```bash
curl --user "{username}":"{password}" \
"https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze?version=2017-02-27&text=I%20still%20have%20a%20dream%2C%20a%20dream%20deeply%20rooted%20in%20the%20American%20dream%20one%20day%20this%20nation%20will%20rise%20up%20and%20live%20up%20to%20its%20creed%20We%20hold%20these%20truths%20to%20be%20self%20evident%3A%20that%20all%20men%20are%20created%20equal.&features=sentiment,keywords&keywords.sentiment=true&sentiment.targets=the%20American%20dream"
```
{:pre}

## Próximos passos
{: #next-steps}

Pronto! Este tutorial trata apenas superficialmente sobre o que é possível fazer com o {{site.data.keyword.nlushort}}. Para
obter mais informações sobre os recursos da API, consulte estes recursos:

- Visualize a [Referência de API ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/ "Ícone de link externo"){: new_window} para obter detalhes e exemplos de cada um dos parâmetros.
- Saiba como identificar [entidades e relacionamentos customizados ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/watson/developercloud/doc/natural-language-understanding/customizing.html "Ícone de link externo"){: new_window}.
