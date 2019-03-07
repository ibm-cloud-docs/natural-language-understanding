---

copyright:
  years: 2015, 2018
lastupdated: "2018-11-08"

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

# Venda
{: #pricing}

O {{site.data.keyword.nlushort}} tem três planos de precificação: Lite, Standard e Premium.

Esta página contém informações de precificação em dólares americanos. Para visualizar as informações de precificação em sua moeda local, consulte a página [{{site.data.keyword.nlushort}}](https://{DomainName}/catalog/services/natural-language-understanding) no catálogo do {{site.data.keyword.cloud}}.
{: tip}

## Lite
{: #lite}

O plano Lite é grátis para usuários que estão procurando experimentar o Natural Language Understanding ou construir uma prova de conceito.

**Venda**
- 30.000 itens / mês da NLU Grátis

** Modelo Customizado **
- 1 modelo customizado livre

## Padrão
{: #standard}

Um plano "pré-pago" recomendado para quando você estiver pronto para mover seu aplicativo de prova de conceito para produção.

** Precificação **  (faturado mensalmente)
- Camada 1: US$ 0,003/item de NLU para os primeiros 250.000 itens de NLU
- Camada 2: US$ 0,001/item de NLU para 250.001 a 5.000.000 itens de NLU
- Camada 3: US$ 0,0002/item de NLU para itens de NLU adicionais após 5.000.000

** Modelo customizado **  ($/modelo customizado / mês)
- US$ 800 para todas as camadas

## Premium
{: #premium}

Um plano que oferece um nível mais alto de segurança e isolamento para ajudar os clientes com os requisitos de dados sensíveis.

_ [Entre em contado com vendas](https://www.ibm.com/account/reg/us-en/signup?formid=MAIL-watson) para obter detalhes._

## O que é um item NLU?
{: #nlu-items}

O uso da API é medido em **Itens de NLU**. Um item de NLU é uma **unidade de texto** (até 10.000 caracteres de texto) que é analisada para um **recurso**, como a impressão.

Para manter o controle do número de itens de NLU em sua solicitação, é possível examinar o objeto `usage` na resposta. Por exemplo, a análise de 15.000 caracteres de texto para impressão, emoção e palavras-chave retornará as informações de uso a seguir.

```json
"uso": {
  "text_units": 2,
  "text_characters": 15000,
  "features": 3
}
```
{: code}
  
Há **2** unidades de texto e **3** recursos na solicitação, portanto, há **2 × 3 = 6** itens de NLU.

As unidades de texto são contadas separadamente para cada solicitação. Se uma solicitação analisar 15.000 caracteres e outra solicitação analisar 3.000 caracteres, isso contará como um total de 3 unidades de texto. A primeira solicitação tem 2 unidades de texto e a segunda solicitação tem 1 unidade de texto.

## Perguntas mais frequentes
{: #faq}

### Eu quero entender a impressão em 20.000 tweets. Como posso estimar o que pagarei no plano Standard?

- Etapa 1: Calcular o número de unidades de texto por solicitação<br>
A partir de novembro de 2018, o número máximo de caracteres permitidos em um tweet é 280.<br>
Isso se converte em uma unidade de texto por solicitação.

- Etapa 2: Calcular o número de recursos por solicitação<br>
Um recurso, a impressão, é ativado em cada solicitação.

- Etapa 3: Calcular o número de itens de NLU por solicitação<br>
Itens de NLU = (Número de unidades de texto) × (Número de recursos)<br>
Itens da NLU = 1 unidade de texto × 1 recurso = 1 item de NLU

- Etapa 4: Calcular o número total de itens de NLU <br>
Número total de itens de NLU = (Número de solicitações) × (Número de itens de NLU por solicitação) <br>
Número total de itens de NLU = 20.000 solicitações × 1 item de NLU por solicitação = total de 20.000 itens de NLU

- Etapa 5: Estimar o preço para o número total de itens de NLU<br>
Para o plano de precificação Standard, são cobrados US$ 0,003 por item para os primeiros 250.000 itens de NLU<br>
Preço estimado = (Número de itens de NLU) × (Preço por item de NLU) <br>
Preço estimado = 20.000 itens de NLU × $0,003 = US$ 60

** Custo total = US$ 60 **

### Eu desejo extrair entidades, palavras-chave e categorias para 50.000 documentos com uma média de 12.000 caracteres por documento. Qual será o meu preço estimado no plano Standard?
- Etapa 1: Calcular o número de unidades de texto por solicitação <br>
Unidades de texto = Número de grupos de 10.000 caracteres ou menos <br>
12.000 caracteres por solicitação = 2 unidades de texto por solicitação

- Etapa 2: Calcular o número de recursos por solicitação<br>
Entidades, Palavras-chave, Categorias = 3 recursos

- Etapa 3: Calcular o número de itens de NLU por solicitação <br>
Itens de NLU = (Número de unidades de texto) × (Número de recursos) <br>
Itens de NLU = 2 unidades de dados × 3 enriquecimentos = 6 itens de NLU

- Etapa 4: Calcular o número total de itens de NLU <br>
Número total de itens de NLU = (Número de solicitações ou documentos) × (Número de itens de NLU) <br>
Número total de itens de NLU = 50.000 solicitações × 6 itens de NLU = 300.000 itens de NLU

- Etapa 5: Estimar o preço para o número total de itens de NLU <br>
São cobrados US$ 0,003 por item dos primeiros 250.000 itens de NLU<br>
É cobrado US$ 0,001 por item para até 5.000.000 itens de NLU adicionais<br>
Preço estimado = (250.000 itens de NLU × US$ 0,003) + (50.000 itens de NLU × US$ 0,001) <br>
Preço estimado = $750 + $50


** Custo total = US$ 800 **

### Como calculo o preço do Plano Standard para 15.000 itens de NLU?
- Como os primeiros 250.000 itens de NLU são precificados em US$ 0,003/item, são cobrados US$ 0,003 por item dos seus 15.000 itens de NLU (Camada 1). Seu preço estimado seria US$ 45. 

### Como calcular o preço do Plano Standard para 6.000.000 itens de NLU?
- Como você tem mais de 5.000.000 itens de NLU, são cobrados US$ 0,003 por item de seus primeiros 250.000 itens de NLU (Camada 1), US$ 0,001 por item de seus próximos 4.750.000 itens de NLU (Camada 2) e US$ 0,0002 por item de seus 1.000.000 itens de NLU restantes (Camada 3). Seu preço estimado seria US$ 5.700. 



