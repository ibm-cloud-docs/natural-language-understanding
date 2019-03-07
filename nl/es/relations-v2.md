---

copyright:
  years: 2015, 2019
lastupdated: "2019-02-25"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:pre: .pre}
{:note: .note}
{:codeblock: .codeblock}
{:screen: .screen}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}

# Tipos de relación (Versión 2)
{: #relation-types-version-2}

La tabla siguiente lista los tipos de relación que devuelve la _Versión 2_ del sistema de tipos de relación. El sistema de tipos de relación que utiliza {{site.data.keyword.nlushort}} difiere según el idioma utilizado. Para obtener más detalles, consulte la página [Sistemas de tipos de relación](/docs/services/natural-language-understanding?topic=natural-language-understanding-relation-type-systems).
{: shortdesc}

Los tipos de entidad utilizados por este sistema de tipos de relación están listados en la página [Tipos de entidad (Versión 2)](/docs/services/natural-language-understanding?topic=natural-language-understanding-entity-types-version-2).
{: note}

| Relación        | Descripción |
|-----------------|----------------|
| affiliatedWith  | Existe entre dos entidades que tienen una afiliación o están relacionadas de forma similar. | 
| basedIn         | Existe entre una organización y el lugar donde principalmente, únicamente o intrínsecamente se encuentra. |
| bornAt          | Existe entre una Person y el lugar donde nació. |
| bornOn          | Existe entre una Person y la Date o Time en la que nació. |
| clientOf        | Existe entre dos entidades cuando una corresponde a un cliente directo de negocio de la otra (es decir, paga determinados servicios o productos). |
| colleague       | Existe entre dos Persons que son parte de la misma Organization. |
| competitor      | Existe entre dos Organizations involucradas en una competición económica. |
| contactOf       | Indica información de contacto con una entidad. |
| diedAt          | Existe entre una Person y el lugar donde murió. |
| diedOn          | Existe entre una Person y la Date o Time en la que murió. |
| dissolvedOn     | Existe entre una Organization o URL y la Date o Time en la que fue disuelta. |
| educatedAt      | Existe entre una Person y la Organization en la que se formó.|
| employedBy      | Existe entre dos entidades cuando una paga a la otra por determinados servicios o por un trabajo. Debe existir una recompensa económica. En muchos casos, indicar esta relación precisa de un conocimiento exterior. |
| foundedOn       | Existe entre una Organization o URL y la Date o Time en la que fue fundada. |
| founderOf       | Existe entre una Person y la Facility, Organization o URL que fundó. |
| locatedAt       | Existe entre una entidad y su ubicación. |
| managerOf       | Existe entre una Person y otra entidad como, por ejemplo, una Person u Organization que se encarga de gestionar su trabajo. |
| memberOf        | Existe entre una entidad como, por ejemplo, una Person u Organization y otra entidad a la que pertenece. |
| ownerOf         | Existe entre una entidad como, por ejemplo, una Person u Organization y una entidad que posee. El propietario no necesita tener la propiedad permanente de la entidad para que exista la relación. |
| parentOf        | Existe entre una Person y sus hijos o hijastros. |
| partner         | Existe entre dos Organizations involucradas en una cooperación económica. |
| partOf          | Existe entre una entidad pequeña y otra mayor del mismo tipo o de un tipo relacionado en el que la segunda entidad incluye a la primera. Si las entidades son sucesos, el primero debe darse dentro del intervalo de tiempo del segundo para que se reconozca la relación. |
| partOfMany      | Existe entre entidades pequeñas y grandes del mismo tipo o de tipos relacionados en los que la segunda entidad, que debe ser plural, incluye la primera, que puede ser singular o plural. |
| populationOf    | Existe entre un lugar y el número de personas que se encuentra allí, o entre una organización y el número de miembros o empleados que tiene. |
| measureOf      | Esta relación indica la cantidad de una entidad o medida (altura, peso, etc.) de una entidad. |
| relative        | Existe entre dos Persons que son parientes. Para identificar a padres, hijos, hermanos y cónyuges, utilice las relaciones `parentOf`, `siblingOf` y `spouseOf`. |
| residesIn       | Existe entre una Person y un lugar donde vive o vivía anteriormente. |
| shareholdersOf  | Existe entre una Person u Organization y una Organization en la que la primera entidad participa. |
| siblingOf       | Existe entre una Person y sus hermanos o hermanastros.     |
| spokespersonFor | Existe entre una Person y una Facility, Organization o Person a la que representa.  |
| spouseOf        | Existe entre dos Persons que son cónyuges. |
| subsidiaryOf    | Existe entre dos Organizations cuando la primera es una subsidiaria de la segunda. |
