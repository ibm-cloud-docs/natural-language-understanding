---

copyright:
  years: 2015, 2021
lastupdated: "2021-04-26"

subcollection: natural-language-understanding

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

# Entity type systems
{: #entity-type-systems}

The entity type system that {{site.data.keyword.nlushort}} uses differs depending on which version date and which language you are using. This page describes, for each version date, which type system is used for each language.
{: shortdesc}

For example, analyzing entities in French text with version date set to `2018-09-21` uses the [Version 2 entity type system][v2]. Analyzing entities in French text with a `2017-02-27` version date uses the [Version 1 entity type system][v1].

| Language |   |   |   | Version date |   |   |
| --- | --- | --- | --- | --- | --- | -- |
|     | **2017-07-27** | **2018-03-16** | **2018-09-21** | **2018-11-16** | **2020-12-02** | **2020-12-09** |
| Arabic | [Version 2][v2] | [Version 2][v2] | [Version 2][v2] | [Version 2][v2] | [Version 2][v2] | [Version 2][v2] |
| Chinese | [Version 2][v2] | [Version 2][v2] | [Version 2][v2] | [Version 2][v2] | [Version 2][v2] | [Version 2][v2] |
| Dutch | [Version 2][v2] | [Version 2][v2] | [Version 2][v2] | [Version 2][v2] | [Version 2][v2] | [Version 2][v2] |
| English | [Version 1][v1] | [Version 1][v1] | [Version 1][v1] | [Version 1][v1] | [Version 1][v1] | [Version 2][v2] |
| French | [Version 1][v1] | [Version 2][v2] | [Version 2][v2] | [Version 2][v2] | [Version 2][v2] | [Version 2][v2] |
| German | [Version 1][v1] | [Version 2][v2] | [Version 2][v2] | [Version 2][v2] | [Version 2][v2] | [Version 2][v2] |
| Italian | [Version 1][v1] | [Version 1][v1] | [Version 1][v1] | [Version 2][v2] | [Version 2][v2] | [Version 2][v2] |
| Japanese | [Version 1][v1] | [Version 2][v2] | [Version 2][v2] | [Version 2][v2] | [Version 2][v2] | [Version 2][v2] |
| Korean | [Version 1][v1] | [Version 1][v1] | [Version 1][v1] | [Version 1][v1] | [Version 2][v2] | [Version 2][v2] |
| Portuguese | [Version 1][v1] | [Version 1][v1] | [Version 2][v2] | [Version 2][v2] | [Version 2][v2] | [Version 2][v2] |
| Russian | [Version 1][v1] | [Version 1][v1] | [Version 1][v1] | [Version 1][v1] | [Version 1][v1] | [Version 1][v1] |
| Spanish | [Version 1][v1] | [Version 1][v1] | [Version 1][v1] | [Version 1][v1] | [Version 2][v2] | [Version 2][v2] |
| Swedish | [Version 1][v1] | [Version 1][v1] | [Version 1][v1] | [Version 1][v1] | [Version 1][v1] | [Version 1][v1] |

<!---
 ## Entity type systems for version 2018-11-16
{: #2018-11-16}

The following entity type systems are used when you set the `version` parameter to `2018-11-16`.

|Language|Entity type system|
| --- | ---|
| English | [Version 1][v1] |
| French | [Version 2][v2] |
| German | [Version 2][v2] |
| Italian | [Version 2][v2] |
| Japanese | [Version 2][v2] |
| Korean | [Version 1][v1] |
| Portuguese | [Version 2][v2] |
| Russian | [Version 1][v1] |
| Spanish | [Version 1][v1] |
| Swedish | [Version 1][v1] |

## Entity type systems for version 2018-09-21
{: #2018-09-21}

The following entity type systems are used when you set the `version` parameter to `2018-09-21`.

|Language|Entity type system|
| --- | ---|
| English | [Version 1][v1] |
| French | [Version 2][v2] |
| German | [Version 2][v2] |
| Italian | [Version 1][v1] |
| Japanese | [Version 2][v2] |
| Korean | [Version 1][v1] |
| Portuguese | [Version 2][v2] |
| Russian | [Version 1][v1] |
| Spanish | [Version 1][v1] |
| Swedish | [Version 1][v1] |


## Entity type systems for version 2018-03-16
{: #2018-03-16}

The following entity type systems are used when you set the `version` parameter to `2018-03-16`.

|Language|Entity type system|
| --- | ---|
| English | [Version 1][v1] |
| French | [Version 2][v2] |
| German | [Version 2][v2] |
| Italian | [Version 1][v1] |
| Japanese | [Version 2][v2] |
| Korean | [Version 1][v1] |
| Portuguese | [Version 1][v1] |
| Russian | [Version 1][v1] |
| Spanish | [Version 1][v1] |
| Swedish | [Version 1][v1] |


## Entity type systems for version 2017-02-27
{: #2017-02-27}

The following entity type systems are used when you set the `version` parameter to `2017-02-27`.

|Language|Entity type system|
| --- | ---|
| English | [Version 1][v1] |
| French | [Version 1][v1] |
| German | [Version 1][v1] |
| Italian | [Version 1][v1] |
| Korean | [Version 1][v1] |
| Portuguese | [Version 1][v1] |
| Russian | [Version 1][v1] |
| Spanish | [Version 1][v1] |
| Swedish | [Version 1][v1] |

--->
[v1]: /docs/natural-language-understanding/?topic=natural-language-understanding-entity-types-version-1
[v2]: /docs/natural-language-understanding/?topic=natural-language-understanding-entity-types-version-2
