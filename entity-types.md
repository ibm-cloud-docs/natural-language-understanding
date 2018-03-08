---

copyright:
  years: 2015, 2017
lastupdated: "2018-03-08"

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

# Entity types and subtypes

The entity type system that {{site.data.keyword.nlushort}} uses differs depending on which version date and which language you are using. This page describes, for each version date, which type system is used for each language.
{: shortdesc}

For example, analyzing entities in French text with version date set to `2018-03-08` will use the [v2 entity type system][v2]. Requests that specify a previous version date will use the [v1 entity type system][v1].


## Entity type systems for version 2018-03-08
{: #2018-03-08}

The following entity type systems are used when you set the `version` parameter to `2018-03-08`.

|Language|Entity type system|
| --- | ---|
| English | [v1] |
| French | [v2] |
| German | [v1] |
| Italian | [v1] |
| Korean | [v1] |
| Portuguese | [v1] |
| Russian | [v1] |
| Spanish | [v1] |
| Swedish | [v1] |


## Entity type systems for version 2017-02-27
{: #2017-02-27}

The following entity type systems are used when you set the `version` parameter to `2017-02-27`.

|Language|Entity type system|
| --- | ---|
| English | [v1] |
| French | [v1] |
| German | [v1] |
| Italian | [v1] |
| Korean | [v1] |
| Portuguese | [v1] |
| Russian | [v1] |
| Spanish | [v1] |
| Swedish | [v1] |


[V1]: entity-types-v1.html
[V2]: entity-types-v2.html
