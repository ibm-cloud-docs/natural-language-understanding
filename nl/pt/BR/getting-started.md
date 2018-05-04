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

# Tutorial Introdução
Neste breve tutorial, apresentamos o {{site.data.keyword.nlushort}}, analisando um texto de amostra para obter a impressão.
{:shortdesc}

## Antes de iniciar
{: #before-you-begin}

- Crie uma instância do serviço:
    - {: download} Se você estiver vendo isso, você criou sua instância de serviço. Agora, obtenha suas credenciais.
    - Criar um projeto de um serviço:
        1.  Acesse a página {{site.data.keyword.watson}} Developer Console [Services ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.{DomainName}/developer/watson/services){: new_window}.
        1.  Selecione {{site.data.keyword.nlushort}}, clique em **Incluir serviços** e inscreva-se para uma conta grátis do {{site.data.keyword.Bluemix_notm}} ou efetue login.
        1.  Digite `sentiment-tutorial` como o nome do projeto e clique em **Criar
projeto**.
- Copie as credenciais para autenticação em sua instância de serviço:
    - {: download} No painel de serviço (que você está vendo):
        1.  Clique na guia **Credenciais de serviço**.
        1.  Clique em **Visualizar credenciais** em **Ações**.
        1.  Copie os valores de `username`, `password` e `url`.
        {: download}
    - Por meio de seu projeto de **tutorial de impressão** no Console do desenvolvedor, copie os valores
`username`, `password` e `url` para
`"natural_language_understanding"` da seção **Credenciais**.
- Certifique-se de que tenha cURL:
    - Os exemplos usam cURL para chamar métodos da interface HTTP. Instale a versão para seu sistema operacional de [curl.haxx.se ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://curl.haxx.se/){: new_window}. Instale a versão que suporta o protocolo Secure Sockets Layer (SSL). Certifique-se de incluir o arquivo binário instalado em sua variável de ambiente `PATH`.

<!-- Remove this text after dedicated instances have the Developer Console: begin -->

Se você usa o {{site.data.keyword.Bluemix_dedicated_notm}}, crie sua instância de serviço na página [{{site.data.keyword.nlushort}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.{DomainName}/catalog/services/natural-language-understanding/){: new_window} no catálogo. Para obter detalhes sobre como localizar suas credenciais de serviço, consulte [Credenciais de serviço para serviços do Watson ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](/docs/services/watson/getting-started-credentials.html#getting-credentials-manually){: new_window}.

<!-- Remove this text after dedicated instances have the Developer Console: end -->

## Etapa 1: analise o conteúdo de amostra para impressão
{: #analyze-sample}

Analise, primeiro, a impressão de algum texto de amostra. Abra uma interface da linha de comandos e execute o comando a seguir
para chamar o método `GET/v1/analyze`, que analisa o texto de amostra para obter a impressão e as
palavras-chave. Substitua `{username}` e `{password}` pelas credenciais de serviço copiadas na etapa anterior:

```bash
curl --user "{username}":"{password}" \
"https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze?version=2017-02-27&text=I%20still%20have%20a%20dream%2C%20a%20dream%20deeply%20rooted%20in%20the%20American%20dream%20%E2%80%93%20one%20day%20this%20nation%20will%20rise%20up%20and%20live%20up%20to%20its%20creed%2C%20%22We%20hold%20these%20truths%20to%20be%20self%20evident%3A%20that%20all%20men%20are%20created%20equal.&features=sentiment,keywords"
```
{:pre}

## Etapa 2: retorne as informações de palavra-chave
{: #analyze-keywords}

A chamada anterior retornou informações de impressão para todo o texto. Agora, expanda os resultados para retornar a análise de sentimentos especificamente em cada uma das palavras-chave. Inclua o parâmetro **keywords.sentiment** e configure-o como `true`. Substitua `{username}` e `{password}` por suas informações.

```bash
curl --user "{username}":"{password}" \
"https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze?version=2017-02-27&text=I%20still%20have%20a%20dream%2C%20a%20dream%20deeply%20rooted%20in%20the%20American%20dream%20%E2%80%93%20one%20day%20this%20nation%20will%20rise%20up%20and%20live%20up%20to%20its%20creed%2C%20%22We%20hold%20these%20truths%20to%20be%20self%20evident%3A%20that%20all%20men%20are%20created%20equal.&features=sentiment,keywords&keywords.sentiment=true"
```
{:pre}

## Etapa 3: delimite uma frase
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

- Visualize a [Referência de API ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/){: new_window} para obter detalhes e exemplos de cada um dos parâmetros.
- Saiba como identificar [entidades e relações
customizadas](/docs/services/natural-language-understanding/customizing.html).
