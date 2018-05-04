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

# Notas sobre a liberação

Os novos recursos e mudanças a seguir para o serviço estão disponíveis.
{: shortdesc}

## Versionamento da API de serviço

**Versão da API atual**: 2018-03-16

Solicitações de API requerem um parâmetro version que obtém a data no formato `version=YYYY-MM-DD`. Envie o parâmetro version com cada solicitação de API.

Quando mudamos a API de uma maneira incompatível com versões anteriores, lançamos uma nova versão secundária. Para aproveitar
as mudanças em uma nova versão, mude o valor do parâmetro da versão para a nova data. Se você não estiver pronto para atualizar para
essa versão, não mude sua data da versão.

## Mudanças

### 16 de março de 2018
{: #03-march-2018}

- Incluído suporte para as categorias, as relações e as funções semânticas em alemão.
  - Um novo sistema de tipos de relação é usado para relações em alemão. Para visualizar detalhes, consulte a página
[Tipos de relação (versão 2)](relations-v2.html).
- Palavras-chave e impressão em alemão melhoradas.
- Incluído suporte para categorias e conceitos em japonês.
- Aprimoramentos de detecção de idioma.
- Limpeza da página da web melhorada.
- Modelos de entidades em alemão e francês melhorados. Os modelos usam um novo sistema de tipos de entidade. Confira os novos
tipos e subtipos de entidade na página [Tipos e subtipos de entidade (versão 2)](entity-types-v2.html). Quando seu
aplicativo for compatível com o novo sistema de tipos, mude o parâmetro de data da versão em suas solicitações para
`2018-03-16` para usar o novo modelo. A seguir estão as diferenças entre o sistema de tipos _Versão 1_
e o sistema de tipos _Versão 2_.
  - Novos tipos de entidade:
    - Data
    - Duração
    - Medida
    - Money
    - Number&ast;
    - Percent&ast;
    - PhoneNumber&ast;
    - Ordinal
    - Tempo
    - URL&ast;
  - Tipos de entidade removidos:
    - Anatomia
    - Award
    - Broadcaster
    - Company
    - Crime
    - Medicamento
    - HealthCondition
    - Movie
    - MusicGroup
    - NaturalEvent
    - PrintMedia
    - Quantidade
    - Sport
    - SportingEvent
    - TelevisionShow
    - Vehicle
  - Novo subtipo de entidade:
    - Quantidade

&ast; Esse tipo de entidade ainda não é detectável no texto francês.



### 25 de janeiro de 2018
{: #25-january-2018}

- O suporte ao [modelo customizado](customizing.html) do chinês (simplificado) agora está disponível para
entidades e relações.

### 12 de janeiro de 2018
{: #12-january-2018}

- Incluído suporte para conceitos em alemão.

### 15 de dezembro de 2017
{: #15-december-2017}

- O suporte ao [modelo customizado](customizing.html) holandês agora está disponível para entidades e
relações.
- O [suporte ao idioma francês](language-support.html#french) agora inclui conceitos.
- O modelo de impressão em francês foi melhorado para entregar melhores resultados.
- O modelo de detecção de idioma é mais rápido e detecta mais idiomas em geral. Para obter a lista completa de idiomas,
consulte [Idiomas detectáveis](detectable-languages.html).

  Os idiomas a seguir são novas adições à lista:
  - Bielorrusso (be)
  - Biari (bh)
  - Divehi (dv)
  - Galego (gl)
  - Ganda (lg)
  - Inuktitut (iu)
  - Javanês (jv)
  - Canarim (kn)
  - Khmer (km)
  - Quiniaruanda (rw)
  - Laosiano (lo)
  - Malaiala (ml)
  - Marata (mr)
  - Oriá (or)
  - Panjabi (pa)
  - Gaélico Escocês (gd)
  - Cingalês (si)
  - Tâmil (ta)
  - Télugo (te)
  - Iídiche (yi)

  Os idiomas a seguir não são mais detectados:
  - Bretã (br)
  - Chamorro (ch)
  - Esperanto (eo)
  - Feroês (fo)
  - Hauçá (ha)
  - Ndebele (nr)
  - Ojíbua (oj)

### 28 de novembro de 2017
{: #28-november-2017}

- **Menções de entidade.** Obter os locais de menções de entidade em suas solicitações de
`entities`, incluindo a opção `"mentions": true`.
    
    Corpo da solicitação `POST /analyze` de exemplo:
    
    ```json
    {
      "text": "Intel planned to announce Monday a laptop-computer chip that combines an Intel processor and an AMD graphics unit.", "recursos": {
        "entities": {
          "mentions": true
        }
      }
    }
    ```
    {: codeblock}
    
    Resposta de exemplo:
    
    ```json
    {
      "uso": {
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
              "text": "Intel", "location": [
                0,
                5
              ]
            },
            {
              "text": "Intel", "location": [
                73,
                78
              ]
            }
          ], "desambiguização": {
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
          ], "desambiguização": {
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
    
### 17 de novembro de 2017
{: #17-november-2017}

- O **[suporte ao idioma coreano](language-support.html#korean)** foi expandido para
incluir os recursos a seguir:

    - Entidades
    - Palavras-chave
    - Funções de semântica


### 30 de julho de 2017
{: #30-july-2017}

- É possível controlar o custo usando o parâmetro opcional `limit_text_characters` para limitar
o número de caracteres que são processados. Por exemplo:

```
{
  "text": "The United States of America, commonly known as the United States (U.S.) or America, is a federal republic composed of 50 states, a federal district, five major self-governing territories, and various possessions. Forty-eight of the fifty states and the federal district are contiguous and located in North America between Canada and Mexico. The state of Alaska is in the northwest corner of North America, bordered by Canada to the east and across the Bering Strait from Russia to the west.", "recursos": {
    "entities": {}
  },
  "limit_text_characters": 50,
  "return_analyzed_text": true
}
```

- Cada caractere conta como um caractere, independentemente se o caractere é um caractere de byte único ou um caractere de
multibyte.

- Para a medição, um {{site.data.keyword.nlushort}} Item continua a ser um recurso (também conhecido como um
enriquecimento) por uma unidade de texto. Uma unidade de texto tem 10.000 caracteres ou menos.

- Para obter informações de precificação detalhadas, consulte
[{{site.data.keyword.nlushort}}](https://console.bluemix.net/catalog/services/natural-language-understanding)
no {{site.data.keyword.cloud}} Catálogo.

- Além de incluir o parâmetro `limit_text_characters`, as mudanças a seguir foram feitas para limites de
tamanho de texto e truncamento:

  - Todo o texto maior que 50.000 caracteres será truncado antes do processamento. Anteriormente, o truncamento se baseava em
kilobytes, em que um kilobyte equivalia a 1.024 bytes.

  - Uma mensagem informativa é retornada na resposta quando o texto com mais de 50.000 caracteres é truncado.

  - O tamanho de limite de texto para modelos customizados foi aumentado de 10.000 caracteres para 50.000 caracteres.

  - Informações de uso são incluídas na resposta para clareza quanto ao número de {{site.data.keyword.nlushort}}
Itens usados para cada solicitação. Por exemplo:

```
{
  "uso": {
    "text_units": 5,
    "text_characters": 41186,
    "features": 1
  },
  ...
}
```


### 8 de maio de 2017
{: #8-may-2017}

- Modelo de pontuação de sinal de emoção atualizado. O conjunto de dados de treinamento foi expandido e a engenharia de
recurso foi alterada e como resultado o modelo tem precisão mais alta em nosso conjunto de dados de avaliação de desempenho.

### 27 de março de 2017
{: #27-march-2017}

- Os modelos de entidade e impressão foram melhorados, o que significa que, quando você chamar esses recursos, obterá melhores resultados.
- As relações agora suportam {{site.data.keyword.knowledgestudioshort}} modelos customizados em francês, alemão,
italiano e português.

### 15 de março de 2017
{: #15-march-2017}

Nós liberamos atualizações para o modelo de pontuação de sinal de emoção. O conjunto de dados de treinamento foi expandido e como
resultado o modelo tem maior precisão em nosso conjunto de dados de avaliação de desempenho.

### 27 de fevereiro de 2017
{: #27-february-2017}

O serviço Natural Language Understanding é agora GA.

