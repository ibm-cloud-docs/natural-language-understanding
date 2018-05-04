---

copyright:
  years: 2015, 2017
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

# Tipos de relação (versão 2)

A tabela a seguir lista os tipos de relação retornados pelo sistema de tipos de relação _Versão 2_. O sistema de tipos de entidade usado pelo {{site.data.keyword.nlushort}} difere com base em qual linguagem você usa. Para obter mais detalhes, veja a página [Tipos de relação](relations.html).
{: shortdesc}

Os tipos de entidade usados por este sistema de tipos de relação são listados na página
[Tipos e subtipos de entidade (Versão 2)](entity-types-v2.html).

| Relação        | Descrição |
|-----------------|----------------|
| affiliatedWith  | Existe entre duas entidades que possuem uma afiliação ou que estejam conectadas de forma semelhante. | 
| basedIn         | Existe entre uma Organization e o lugar em que ela está localizada principalmente ou apenas intrinsecamente. |
| bornAt          | Existe entre uma Person e o lugar onde nasceu. |
| bornOn          | Existe entre uma Person e a Date ou o Time em que nasceu. |
| clientOf        | Existe entre duas entidades quando uma é um cliente de negócio direto da outra (ou seja,
paga por determinados serviços ou produtos). |
| colleague       | Existe entre duas Persons que fazem parte da mesma Organization. |
| competitor      | Existe entre duas Organizations que estão envolvidas em uma concorrência econômica. |
| contactOf       | Relaciona informações de contato com uma entidade. |
| diedAt          | Existe entre uma Person e o lugar em que ele ou ela morreu. |
| diedOn          | Existe entre uma Person e a Date ou o Time em que ele ou ela morreu. |
| dissolvedOn     | Existe entre uma Organization ou URL e a Date ou o Time em que ela foi dissolvida. |
| educatedAt      | Existe entre uma Person e a Organization em que essa pessoa foi educada.|
| employedBy      | Existe entre duas entidades quando uma paga a outra por um determinado trabalho ou
serviços; recompensa monetária deve estar envolvida. Em muitas circunstâncias, a marcação desta relação requer
conhecimento geral. |
| foundedOn       | Existe entre uma Organization ou URL e a Date ou o Time em que ela foi fundada. |
| founderOf       | Existe entre uma Person e um Facility, Organization ou URL que eles fundaram. |
| locatedAt       | Existe entre uma entidade e sua localização. |
| managerOf       | Existe entre uma Person e outra entidade, como uma Person ou Organization, que essa pessoa
gerencia como seu emprego. |
| memberOf        | Existe entre uma entidade, como uma Person ou Organization, e outra entidade à qual ele ou ela pertence. |
| ownerOf         | Existe entre uma entidade, como uma Person ou Organization, e uma entidade que ele ou ela possui. O proprietário
não precisa ter a propriedade permanente da entidade para a relação existir. |
| parentOf        | Existe entre uma Person e seus filhos ou enteados. |
| partner         | Existe entre duas Organizations que estão envolvidas em uma cooperação econômica. |
| partOf          | Existe entre uma entidade menor e uma maior do mesmo tipo ou de tipos relacionados em que
a segunda entidade inclui a primeira. Se as entidades forem eventos, o primeiro deverá ocorrer dentro da amplitude de
tempo do segundo para que a relação seja reconhecida. |
| partOfMany      | Existe entre entidades menores e maiores do mesmo tipo ou de tipos relacionados em que a segunda entidade, que
deve ser plural, inclui a primeira, que pode ser singular ou plural. |
| populationOf    | Existe entre um lugar e o número de pessoas localizadas lá ou uma organização e o número de membros ou
funcionários que possui. |
| measureOf      | Essa relação indica a quantidade de uma entidade ou medida (altura, peso, etc.) de uma entidade. |
| relative        | Existe entre duas Persons que são parentes. Para identificar pais, filhos, irmãos e cônjuges, use as relações
`parentOf`, `siblingOf` e `spouseOf`. |
| residesIn       | Existe entre uma Person e um lugar onde vive ou viveu anteriormente. |
| shareholdersOf  | Existe entre uma Person ou Organization e uma Organization da qual a primeira entidade é um acionista. |
| siblingOf       | Existe entre uma Person e seu irmão ou meio-irmão. |
| spokespersonFor | Existe entre uma Person e uma Facility, Organization ou Person que ele ou ela representa. |
| spouseOf        | Existe entre duas Persons que são cônjuges. |
| subsidiaryOf    | Existe entre duas Organizations quando a primeira é uma subsidiária da segunda. |
