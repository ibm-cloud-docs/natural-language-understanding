---

copyright:
  years: 2015, 2018
lastupdated: "2018-01-16"

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

# Customizando

Com o [{{site.data.keyword.knowledgestudiofull}}
![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://ibm.biz/watsonknowledgestudio), é possível
estender o {{site.data.keyword.nlushort}} com modelos customizados que identificam entidades customizadas e relações
exclusivas para o seu domínio.
{: shortdesc}

## Introdução aos modelos customizados

> O plano Grátis do {{site.data.keyword.nlushort}} limita o tamanho e o desempenho de seu modelo
customizado. Para testar um modelo customizado para sua extensão integral, você precisará usá-lo com o
plano Standard do {{site.data.keyword.nlushort}}.

1. Se você ainda não tiver feito isso,
veja a [introdução](/docs/services/natural-language-understanding/getting-started.html) ao
{{site.data.keyword.nlushort}}.
1. [Obtenha acesso
ao {{site.data.keyword.knowledgestudioshort}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link
externo")](https://www.ibm.com/us-en/marketplace/supervised-machine-learning/purchase#product-header-top) e efetue login por meio do painel on-line do
[
![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://gateway.watsonplatform.net/knowledge-studio/ui/dashboard/).
1. Visualize a documentação do {{site.data.keyword.knowledgestudioshort}}
[](/docs/services/knowledge-studio/index.html) para saber como criar um modelo customizado (anotador) e implementá-lo no {{site.data.keyword.nlushort}}.
1. Para usar seu modelo, especifique o `modelo` que você implementou nas opções de
[entidades
![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/#entities){: new_window}
ou [relações
![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/#relations){: new_window}
da sua solicitação de API:
    - Arquivo *parameters.json* de exemplo:

        ```json
        {
          "url": "www.url.example",
          "features": {
            "entities": {
              "model": "your-model-id-here"
            },
            "relations": {
              "model": "your-model-id-here"
            }
          }
        }
        ```
        {: codeblock}
    
    - Solicitação curl de exemplo:

        ```bash
        curl -X POST \
        -H "Content-Type: application/json" \
        -u "{username}":"{password}" \
        -d @parameters.json \
        "https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze?version=2017-02-27"
        ```
        {: pre}

