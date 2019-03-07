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

# Notas sobre a liberação
{: #release-notes}

Os novos recursos e mudanças a seguir para o serviço estão disponíveis.
{: shortdesc}

## Novo processo de autenticação de API
{: #iam-auth-process }

Em 30 de outubro de 2018, as localizações Dallas (Sul dos EUA) e Frankfurt (Alemanha) passaram a usar a autenticação Identity and Access Management (IAM) baseada em token. (Consulte [Autenticando com tokens do IAM ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](/docs/services/watson/getting-started-iam.html) para obter mais informações.)
{: important}

O serviço {{site.data.keyword.nlushort}} possui um novo processo de autenticação de API para instâncias de serviço hospedadas nas localizações a seguir:

- Dallas a partir de 30 de outubro de 2018
- Frankfurt a partir de 30 de outubro de 2018
- Londres
- Sydney, a partir de 29 de maio de 2018
- Tóquio
- Washington, DC, a partir de 12 de junho de 2018

O {{site.data.keyword.cloud_notm}} está migrando para a autenticação Identity and Access Management (IAM) baseada em token. Com algumas instâncias de serviço, você autentica para a API usando o IAM.

- Com as *novas* instâncias de serviço que você cria nas localizações nas datas listadas ou depois delas, você autentica para a API usando o IAM. É possível passar um token de acesso em um cabeçalho de autorização ou uma chave de API. Tokens suportam solicitações autenticadas sem a integração de credenciais de serviço em cada chamada. As chaves API usam autenticação básica. Saiba mais sobre o  [ IAM ](/docs/services/watson/getting-started-iam.html).

    Ao usar qualquer um dos SDKs do Watson, é possível passar a chave de API e deixar que o SDK gerencie o ciclo de vida dos tokens. Para obter mais informações e exemplos, consulte [Autenticação ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}/apidocs/natural-language-understanding/#authentication){: new_window} na referência da API.
- Para instâncias de serviço _existentes_ que você criou antes da data indicada, continue a autenticar fornecendo o nome de usuário e a senha para a instância de serviço. Eventualmente, será necessário migrar essas instâncias de serviço para a autenticação IAM. Atualizações serão fornecidas sobre o processo de migração e as datas. Para obter mais informações sobre migração, consulte [Migrando instâncias de serviço do Cloud Foundry para um grupo de recursos](/docs/resources/instance_migration.html).

Para descobrir qual autenticação deve ser usada, visualize as credenciais de serviço clicando na instância de serviço no [Painel ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}/dashboard/apps?watson){: new_window}.


## Versionamento da API de serviço
{: #service-api-versioning}

** Versão atual da API **: 2018-11-16

Solicitações de API requerem um parâmetro version que obtém a data no formato `version=YYYY-MM-DD`. Envie o parâmetro version com cada solicitação de API.

Quando mudamos a API de uma maneira incompatível com versões anteriores, lançamos uma nova versão secundária. Para aproveitar
as mudanças em uma nova versão, mude o valor do parâmetro da versão para a nova data. Se você não estiver pronto para atualizar para
essa versão, não mude sua data da versão.

## Mudanças
{: #changes}

### 10 de janeiro de 2019
{: #10-january-2019}

- Agora, as solicitações **Listar modelos** e **Excluir modelo** que não incluem um parâmetro de data de versão retornam erros `400` em vez de respostas bem-sucedidas.
- Desempenho melhorado das entidades para idiomas diferentes do inglês.

### 14 de dezembro de 2018
{: #14-december-2018}

- Agora é possível criar instâncias de serviço do {{site.data.keyword.nlushort}} na localização Londres do IBM Cloud.
- Incluído suporte para as relações portuguesas.
- Incluído suporte para as relações italianas.
- Incluído um parâmetro `limit` para as solicitações de categorias que controla o número de categorias retornadas para 10, no máximo.
- Precisão melhorada para impressão em japonês e alemão.

### 6 de dezembro de 2018
{: #6-december-2018}

- Precisão melhorada para as categorias, palavras-chave e entidades em italiano.

### 27 de novembro de 2018
{: #27-november-2018}

- Qualidade melhorada dos resultados das palavras-chave para entrada em inglês, francês, japonês e português.
- Agora, as palavras-chave com capitalizações diferentes aparecem em resultados como a mesma palavra-chave.
- Agora, o método **Obter modelos** retorna campos adicionais que você pode usar para gerenciar modelos customizados em várias implementações.
  - ` version `: sequência de versão fornecida pelo usuário do  {{site.data.keyword.knowledgestudioshort}}
  - `version_description`: a descrição fornecida pelo usuário dessa versão do {{site.data.keyword.knowledgestudioshort}} (por exemplo, o que mudou desde a versão anterior)
  - `workspace_id`: um ID fornecido pelo {{site.data.keyword.knowledgestudioshort}} que permanece constante nas implementações repetidas por meio da mesma área de trabalho do {{site.data.keyword.knowledgestudioshort}}.
  - `created`: uma sequência de data/hora que indica quando o modelo foi implementado para o NLU.

### 16 de novembro de 2018
{: #16-november-2018}

- Liberados novos algoritmos para palavras-chave e impressão em inglês para melhorar a precisão e o desempenho.
- Precisão e desempenho de palavras-chave melhorados para entrada em inglês, francês, japonês e português.
- Precisão e desempenho de impressão em italiano melhorados, incluindo melhor precisão para amostras de texto grandes.
- Corrigido um erro que fazia com que o texto codificado por URL aparecesse nos resultados de desambiguação de entidade em espanhol.
- Liberado um novo modelo de entidades em italiano com o sistema de tipos de entidade mais recente. É possível aprender sobre o sistema de tipos mais recente na página [Tipos e subtipos de entidade (versão 2)](entity-types-v2.html). Quando seu aplicativo for compatível com o novo sistema de tipos, mude o parâmetro de data da versão em suas solicitações para `2018-11-16` para usar o novo modelo.

### 9 de novembro de 2018
{: #9-november-2018}

- Grande melhoria na precisão para categorias em todos os idiomas suportados.

### 8 de novembro de 2018
{: #8-november-2018}

- Agora é possível criar instâncias de serviço do {{site.data.keyword.nlushort}} na localização Tóquio do IBM Cloud.

### 5 de novembro de 2018
{: #5-november-2018}

- Incluído suporte para conceitos italianos.

### 30 de outubro de 2018	
{: #30-october-2018}	

A partir de 30 de outubro de 2018, novas instâncias de serviço criadas nas regiões Alemanha e Sul dos EUA usam a [autenticação Identity and Access Management (IAM)](#iam-auth-process).	

### 21 de setembro de 2018
{: #21-september-2018}

- Incluído suporte para as relações em francês e os conceitos em português.
- Agora, a opção de impressão de destino é suportada para palavras-chave em francês e em português.
- Palavras-chave francesas melhoradas.
- Improvada impressão coreana.
- Palavras-chave e impressão em português melhoradas.
- Liberado um novo modelo de entidades em português com o sistema de tipos de entidade mais recente. É possível aprender sobre o sistema de tipos mais recente na página [Tipos e subtipos de entidade (versão 2)](entity-types-v2.html). Quando seu aplicativo for compatível com o novo sistema de tipos, mude o parâmetro de data da versão em suas solicitações para `2018-09-21` para usar o novo modelo. 

### 26 de junho de 2018
{: #26-june-2018}

Incluído suporte para entidades e palavras-chave em japonês.

- Para entrada em japonês, as entidades a seguir ainda não são suportadas:
  - Number
  - Percentual
  - PhoneNumber
  - URL
- Os endereços IPv6 na entrada em japonês ainda não são detectáveis como entidades IPAddress.

### 12 de junho de 2018
{: #12-june-2018}

A partir de 12 de junho de 2018, novas instâncias de serviço criadas na região Leste dos EUA usam a [autenticação Identity and Access Management (IAM)](#iam-auth-process).

### 6 de junho de 2018
{: #06-june-2018}

- Pequenos aprimoramentos para os resultados das categorias Coreanas.

### 29 de maio de 2018
{: #29-may-2018}

A partir de 29 de maio de 2018, novas instâncias de serviço criadas na região Sydney usam a [autenticação do Identity and Access Management (IAM)](#iam-auth-process).

### 9 de maio de 2018
{: #9-may-2018}

- Entidades alemãs melhoradas.

### 4 de maio de 2018
{: #4-may-2018}

- Incluído suporte para as funções de impressão e semântica em japonês.
- Desempenho aprimorado para solicitações de metadados.
- Corrigido um erro que fazia com que as pontuações de relevância de `NAN` aparecessem em alguns resultados de entidades.
- Corrigido um erro que retornava códigos de erro `400` em solicitações de palavras-chave em alemão e em coreano quando códigos de erro `500` eram mais apropriados.


### 19 de abril de 2018
{: #19-april-2018}

- Incluído suporte para relações Japonesas.
- Palavras-chave alemãs melhoradas.
- Corrigido um erro que causava o retorno do texto de menção de entidade incorreto.
- Corrigido um erro que poderia causar resultados insuficientes para impressão de destino.
- Corrigido um erro que fazia com que o `analyzed_text` retornado incluísse caracteres que não tinham sido analisados.


### 5 de abril de 2018
{: #05-april-2018}

- Busca de conteúdo de página da web melhorada. Se você usar o parâmetro `url` para analisar as páginas da web, verá melhores resultados, especialmente de páginas da web que usam conjuntos de quadros e cookies.
- Pequenos aprimoramentos para conceitos coreanos.

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
    - Measure
    - Money
    - Number&ast;
    - Percent&ast;
    - PhoneNumber&ast;
    - Ordinal
    - Time
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
