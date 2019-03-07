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
{:download: .download}

# Resolução de problemas
{: #troubleshooting}

Se você tiver problemas com o {{site.data.keyword.nlushort}}, as dicas de resolução de problemas a seguir poderão ajudar.
{:shortdesc}

## Entidades e tipos de entidade de relações não são consistentes
{: #inconsistent-entity-types}

Os sistemas de tipos de entidade para os recursos de entidades e relações nem sempre são consistentes. Para alguns idiomas e datas da versão, os resultados das relações conterão tipos de entidade diferentes dos tipos de entidade que aparecem nos resultados de entidades. Consulte [Tipos e subtipos de entidade](/docs/services/natural-language-understanding?topic=natural-language-understanding-entity-type-systems) e [Tipos de relação](/docs/services/natural-language-understanding?topic=natural-language-understanding-relation-type-systems) para obter mais detalhes. 

## Detecção de idioma incorreto
{: #incorrect-language-detection}

A detecção automática de idioma poderá não ser exata para texto que contiver menos de 100 caracteres. Se o serviço não detectar o idioma correto de seu texto, será possível [substituir a detecção automática de idioma](/docs/services/natural-language-understanding?topic=natural-language-understanding-overriding-language-detection).

## Muitas solicitações
{: #too-many requests}

Se você estiver vendo um erro "429: excesso de solicitações", a instância de serviço provavelmente atingiu o limite de solicitações simultâneas. Visualize a página [Limites de uso](/docs/services/natural-language-understanding?topic=natural-language-understanding-usage-limits#concurrent-requests) para obter mais informações.

## Resultados inesperados da análise de página da web
{: #unexpected-webpage-results}

A análise de uma página da web pode retornar resultados inesperados em alguns casos. Para investigar, tente configurar o parâmetro **return_analyzed_text** como `true` para inspecionar o texto real que está sendo analisado em sua solicitação. Nos casos em que a [limpeza da página da web](/docs/services/natural-language-understanding?topic=natural-language-understanding-analyzing-webpages#webpage-cleaning) não remover texto indesejado suficiente, considere usar o parâmetro [**xpath**](/docs/services/natural-language-understanding?topic=natural-language-understanding-analyzing-webpages#xpath) para focar a análise em elementos específicos da página.

## Explicações para resultados específicos
{: #explanations-for-results}

O {{site.data.keyword.nlushort}} não fornece nenhuma ferramenta de diagnóstico para explicar por que uma solicitação específica retorna um resultado específico. O serviço foi projetado para fornecer resultados precisos para o máximo de amostras de texto possível, mas, devido à natureza dos modelos de aprendizado de máquina que usamos, não há garantia de que qualquer resultado específico possa parecer correto de uma perspectiva humana.






