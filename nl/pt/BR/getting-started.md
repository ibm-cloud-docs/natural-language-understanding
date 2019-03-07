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

# Tutorial Introdução
{: #getting-started}

Este curto tutorial introduz a API do {{site.data.keyword.nlushort}} com solicitações de exemplo e links para recursos adicionais.
{:shortdesc}

## Antes de iniciar
{: #before-you-begin}

- {: hide-dashboard} Crie uma instância do serviço:
    1.  Acesse a página [{{site.data.keyword.nlushort}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}/catalog/services/natural-language-understanding){: new_window} no {{site.data.keyword.Bluemix_notm}} Catalog.
    2.  Inscreva-se para obter uma conta gratuita do {{site.data.keyword.Bluemix_notm}} ou efetue login.
    3.  Clique em  ** Criar **.
- Copie as credenciais para autenticação em sua instância de serviço:
    1.  Na página **Gerenciar**, clique em **Mostrar** para visualizar suas credenciais.
    2.  Copie os valores de `API Key` e `URL`.
- Certifique-se de que você tenha o comando `curl`:
    - Os exemplos usam o comando `curl` para chamar métodos da interface HTTP. Instale a versão para seu sistema operacional de [curl.haxx.se ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://curl.haxx.se/){: new_window}. Instale a versão que suporta o protocolo Secure Sockets Layer (SSL). Certifique-se de incluir o arquivo binário instalado em sua variável de ambiente `PATH`.

Este tutorial mostra como usar a API do {{site.data.keyword.nlushort}} por meio de uma interface da linha de comandos. Para fazer download de bibliotecas do cliente para várias linguagens de programação, consulte os [SDKs do Watson](/docs/services/natural-language-understanding?topic=watson-using-sdks#using-sdks).
{:tip}

## Etapa 1: Analisar uma página da web
{: #analyze-sample}

Execute o comando a seguir para analisar uma página da web para obter impressão, conceitos, categorias, entidades e palavras-chave. <span class="hide-dashboard">Substitua `{apikey}` e `{url}` por suas credenciais de serviço.</span>

```bash
curl -X POST -u "apikey:{apikey}"{: apikey} \
"{url}/v1/analyze?version=2018-11-16"{: url} \
--header "Content-Type: application/json" \
--data '{
  "url": "http://newsroom.ibm.com/Guerbet-and-IBM-Watson-Health-Announce-Strategic-Partnership-for-Artificial-Intelligence-in-Medical-Imaging-Liver", "features": {
    "sentiment": {},
    "categories": {},
    "concepts": {},
    "entities": {},
    "keywords": {}
  }
}'
```
{:pre}

A próxima etapa demonstra como especificar as opções que customizam a análise de cada recurso.

## Etapa 2: Analisar frases de destino e palavras-chave
{: #analyze-phrase}

O {{site.data.keyword.nlushort}} pode analisar frases de destino no contexto do texto circundante para resultados focados na impressão e na emoção. A opção **targets** para impressão no exemplo a seguir instrui o serviço a procurar os destinos "apples", "oranges" e "broccoli". Como "apples" e "oranges" estão localizados no texto, as pontuações de impressão são retornadas para esses destinos.

Também é possível obter os resultados de impressão e emoção para entidades e palavras-chave detectadas em seu texto. No exemplo, a opção **emotion** para palavras-chave instrui o serviço a analisar cada palavra-chave detectada para obter resultados de emoção.

```bash
curl -X POST -u "apikey:{apikey}"{: apikey} \
"{url}/v1/analyze?version=2018-11-16"{: url} \
--request POST \
--header "Content-Type: application/json" \
--data '{
  "text": " I love apples! Eu não gosto de laranjas. ", "recursos": {
    "sentimento": {
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
{:pre}

## Próximos passos
{: #next-steps}

- Visualize a [Referência de API ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}/apidocs/natural-language-understanding){: new_window}.
- Saiba como identificar [entidades e relações
customizadas](/docs/services/natural-language-understanding?topic=natural-language-understanding-customizing).
