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

# Limites de uso

Os seguintes limites de uso e restrições se aplicam às instâncias de serviço do {{site.data.keyword.nlushort}}.
{: shortdesc}

## Limite de texto analisado

O {{site.data.keyword.nlushort}} trunca texto analisado que contém mais de 50.000 caracteres de byte único ou multibyte. 
Para visualizar o texto que conta para esse limite em suas solicitações, configure o parâmetro
`return_analyzed_text` para `true`.

É possível configurar um limite de caracteres menor com o parâmetro `limit_text_characters`. Se você estiver
interessado em analisar apenas uma pequena parte de seu conteúdo, isso poderá ajudar a evitar custos excessivos.

Objeto de parâmetros de exemplo:
```json
{
  "url": "ibm.com",
  "limit_text_characters": 10000,
  "return_analyzed_text": true,
  "features": {
    "concepts": {}
  }
}
```

## Limite de solicitação simultânea

Cada instância de serviço {{site.data.keyword.nlushort}} é limitada a 30 solicitações simultâneas. É possível que esse
limite possa diminuir para instâncias de serviço nos planos Lite e Standard quando o sistema está enfrentando tráfego
excepcionalmente pesado. Por exemplo, um aplicativo que faz 35 solicitações simultâneas por meio de uma única instância de serviço
excederá o limite de solicitações simultâneas em cinco solicitações e cinco dessas solicitações retornarão um erro `429:
excesso de solicitações`.

Para aumentar seu limite de solicitação simultânea, [abra um chamado de
suporte](https://ibm.biz/ibmcloudsupport).


## Suporte ao idioma

Restrições de idioma diferentes se aplicam, dependendo de como o serviço é usado. Para obter detalhes, consulte a página
[Suporte ao idioma](language-support.html).


