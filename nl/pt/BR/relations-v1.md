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

# Tipos de relação (Versão 1)

A tabela a seguir lista os tipos de relação retornados pelo sistema de tipos de relação _Versão 1_. O sistema de tipos de entidade usado pelo {{site.data.keyword.nlushort}} difere com base em qual linguagem você usa. Para obter mais detalhes, veja a página [Tipos de relação](relations.html).
{: shortdesc}

| Relação        | Descrição                                                                                                                                                                                                        |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| affectedBy      | Existe entre uma entidade e um evento que tem uma direcionalidade clara e que afeta a entidade.                                                                                                                        |
| affiliatedWith  | Existe entre duas entidades que possuem uma afiliação ou que estejam conectadas de forma semelhante.                                                                                                                                   |
| ageOf           | Relaciona uma idade a uma entidade.                                                                                                                                                                                       |
| agentOf         | Existe entre uma entidade e um evento em que a entidade exerce a função mais ativa de acordo com o texto. Nenhum conhecimento básico é necessário.                                                            |
| authorOf        | Existe entre uma pessoa e um TitleWork que essa pessoa criou.                                                                                                                                                    |
| awardedBy       | Existe entre um Award ou Degree e a pessoa ou a organização pela qual ele foi concedido ou
conferido.                                                                                                             |
| awardedTo       | Existe entre um Award ou Degree e a pessoa ou a organização à qual ele foi concedido ou
conferido.                                                                                                             |
| basedIn         | Existe entre uma Organization e o lugar em que ela está localizada principalmente ou apenas intrinsecamente.                                                                                                                   |
| before          | Significa a relação temporal "antes" entre dois Times ou Events. Marcada apenas quando o texto especifica claramente a relação.                                                                                      |
| bornAt          | Existe entre uma Person ou Animal e o lugar em que essa pessoa ou animal nasceu.                                                                                                                                     |
| bornOn          | Existe entre uma Person ou Animal e a Date ou Time em que essa pessoa ou animal nasceu.                                                                                                                           |
| capitalOf       | Existe entre uma capital e seu país, estado ou município. Marcada apenas quando o texto afirma explicitamente a relação, não baseada no conhecimento mundial.                                                              |
| citizenOf       | Existe entre uma pessoa e a GeopoliticalEntity da qual essa pessoa é cidadã.                                                                                                                                |
| clientOf        | Existe entre duas entidades quando uma é um cliente de negócio direto da outra (ou seja,
paga por determinados serviços ou produtos).                                                                                    |
| colleague       | Existe entre duas pessoas que fazem parte da mesma organização.                                                                                                                                                   |
| competitor      | Existe entre duas GeopoliticalEntities ou Organizations que estão envolvidas em uma concorrência econômica.                                                                                                                  |
| contactOf       | Relaciona informações de contato com uma entidade.                                                                                                                                                                        |
| diedAt          | Existe entre uma Person ou Animal e o lugar em que essa pessoa ou animal morreu.                                                                                                                                      |
| diedOf          | Existe entre uma Person ou Animal e a causa de sua morte.                                                                                                                                         |
| diedOn          | Existe entre uma Pessoa ou Animal e a Date ou Time em que essa pessoa ou animal morreu.                                                                                                                               |
| dissolvedOn     | Existe entre uma entidade, como uma Organization, e a Date ou Time em que ela foi dissolvida.                                                                                                                   |
| educatedAt      | Existe entre uma Person e a Organization em que essa pessoa foi educada.                                                                                                                                |
| employedBy      | Existe entre duas entidades quando uma paga a outra por um determinado trabalho ou
serviços; recompensa monetária deve estar envolvida. Em muitas circunstâncias, a marcação desta relação requer
conhecimento geral.                         |
| foundedOn       | Existe entre uma entidade, como uma Organization, e a Date ou Time em que ela foi fundada.                                                                                                                     |
| founderOf       | Existe entre uma Person ou GeopoliticalEntity e uma entidade, como uma Organization, que a fundou.                                                                                                                          |
| hasDisease      | Indica que uma Person ou um Animal tem ou teve uma Disease.                                                                                                                                                            |
| hasMoney        | Indica que uma entidade, como uma pessoa, tem ou tinha Money.                                                                                                                                                        |
| instrumentOf    | Existe entre uma entidade, como uma Weapon, e um Event que a entidade costuma ou costumava
promover.                                                                                                              |
| locatedAt       | Existe entre uma entidade e seu local físico.                                                                                                                                                                |
| managerOf       | Existe entre uma Person e outra entidade, como uma Person ou Organization, que essa pessoa
gerencia como seu emprego.                                                                                              |
| measureOf       | Indica uma Mesure específica, como a altura ou o peso de uma entidade.                                                                                                                                          |
| memberOf        | Existe entre uma entidade, como uma Person, Organization ou GeopoliticalEntity, e outra
entidade para a qual essa primeira entidade pertence.                                                                                            |
| near            | Existe entre duas entidades que estão localizadas próximas uma da outra fisicamente.                                                                                                                                       |
| overlaps        | Indica que dois Times ou Events se sobrepõem temporariamente. Marcada apenas quando o texto especifica claramente a relação.                                                                                                   |
| ownerOf         | Existe entre uma entidade, como uma Person, Organization ou GeopoliticalEntity, e uma
entidade que essa primeira entidade possui, seja permanentemente ou temporariamente.                                                                     |
| parentOf        | Existe entre uma Person ou Animal e seu filho ou enteado.                                                                                                                                         |
| participantIn   | Existe entre um participante, como uma Person, Animal, Organization ou GeopoliticalEntity, e
um Event no qual ele está participando ou que participou.                                                         |
| partner         | Existe entre duas GeopoliticalEntities ou Organizations que estão envolvidas em uma
cooperação econômica.                                                                                                                  |
| partOf          | Existe entre uma entidade menor e uma maior do mesmo tipo ou de tipos relacionados em que
a segunda entidade inclui a primeira. Se as entidades forem Events, a primeira deverá ocorrer dentro da
amplitude de tempo da segunda. |
| partOfMany      | Existe entre entidades menores e maiores do mesmo tipo ou de tipos relacionados em que a
segunda entidade, que deve ser plural, inclui a primeira, que pode consistir em uma ou mais entidades.                      |
| playsRoleOf     | Existe entre uma Person e uma personagem específica que essa pessoa faz ou fez em um
papel.                                                                                                                  |
| populationOf    | Existe entre um Cardinal e uma entidade, como uma organização ou país, para a qual o número
representa a população inteira.                                                                                  |
| productOf       | Existe entre um Product ou TitleWork e a Organization que o produziu.                                                                                                                                       |
| quantityOf      | Indica um Cardinal que é a quantidade ou a quantia de uma segunda entidade.                                                                                                                                            |
| rateOf          | Existe entre uma Rate e um evento cuja frequência de ocorrência ele especifica.                                                                                                                                     |
| relative        | Existe entre uma Person ou Animal e outra Person ou Animal do qual ele é
parente, quando uma relação mais específica é inapropriada.                                                               |
| residesIn       | Existe entre uma entidade viva e o local no qual essa entidade reside permanentemente.                                                                                                                       |
| shareholdersOf  | Existe entre uma pessoa, Organization ou GeopoliticalEntity e uma Organization da qual a
primeira entidade é um acionista.                                                                                                  |
| siblingOf       | Existe entre uma Person ou Animal e seu irmão ou meio-irmão.                                                                                                                                     |
| spokespersonFor | Existe entre uma Person e uma entidade que essa pessoa representa. Marcada apenas quando o texto afirma explicitamente a relação, não baseada no conhecimento mundial.                                                           |
| spouseOf        | Existe entre duas pessoas que são os cônjuges formais.                                                                                                                                                      |
| subsidiaryOf    | Existe entre duas Organizations quando a primeiro é uma subsidiária da segunda,
significando que a primeira entidade possui uma quantia razoável de autonomia, embora esteja sob o
controle da segunda.                               |
| timeOf          | Indica a Date, Time ou Duration em que ou para a qual um evento ocorreu; um TitleWork foi
publicado, executado ou transmitido ou uma Law foi primeiramente elaborada, criada, aprovada ou abolida.                            |

## Tipos de entidade exclusivos para relações

Os tipos de entidade envolvidos no sistema de tipos de relação _Versão 1_ são
diferentes dos tipos de entidade envolvidos nos sistemas de tipos de entidade padrão. É possível especificar um dos modelos de entidade
de relações a seguir no parâmetro `model` para o recurso `entities` para substituir o modelo de
detecção de entidade padrão.

|ID do modelo|Descrição|
|--------|-----------|
|ar-news|Notícias em árabe|
|en-news|Notícias em inglês|
|es-news|Notícias em espanhol|

As seguintes entidades podem ser identificadas com os modelos `relations`:

|Tipo de entidade|
|---|
|Age |
|Anatomy |
|Animal |
|Award |
|Cardinal |
|Crime |
|Date |
|Degree |
|Duration |
|EmailAddress |
|Event |
|EventBusiness |
|EventCommunication |
|EventCustody |
|EventDemonstration |
|EventEducation |
|EventElection |
|EventGathering |
|EventLegal |
|EventLegislation |
|EventMeeting |
|EventPerformance |
|EventPersonnel |
|EventViolence |
|Facility |
|Food |
|GeographicFeature|
|GeopoliticalEntity |
|HealthCondition |
|Law |
|Location |
|Money |
|Measure |
|NaturalEvent |
|Organization |
|Ordinal |
|Percent |
|Person |
|Phone |
|Plant |
|Product |
|SportingEvent |
|Substance |
|Ticker |
|Time |
|TitleWork |
|Vehicle |
|Weapon |
|Weather |
|Web |

