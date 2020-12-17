---

copyright:
  years: 2019, 2020
lastupdated: "2020-12-17"

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

# Versioning
{: #versioning}

**Current API version**: 2020-12-09

API requests require a version parameter that takes the date in the format `version=YYYY-MM-DD`. Send the version parameter with every API request.

When we change the API in a backwards-incompatible way, we release a new minor version. To take advantage of the changes in a new version, change the value of the version parameter to the new date. If you're not ready to update to that version, don't change your version date.

## Deprecation schedule for version dates
{: #deprecation-schedule-for-version-dates}

When a new version date is released, the previous version date will enter a deprecation period lasting one year. You will have one year to migrate your code to support a version that is not deprecated before API requests that use the retired version are automatically switched over to the latest version available.

The following timeline provides examples of what might happen during the deprecation schedule for the `2019-06-04` version.

- The `2019-07-12` version date is released. This begins a deprecation period for the previous `2019-06-04` version date that lasts one year.
  - The deprecated version date is still available to use during the deprecation period.
- A new version date is released during the deprecation period, such as `2020-05-10`.
- On July 12, 2020, the deprecation period for the `2019-06-04` version date ends and the version date is retired.
  - API requests that still use the `2019-06-04` version date after July 12, 2020 are automatically changed to use the behavior of the latest version date available. For this example, the latest version available is `2020-05-10`.

## Version dates
{: #version-dates}

The following table shows the service behavior changes for each version date. Switching to a later version date will activate all changes introduced in earlier versions.

|Version date|Changes summary|Retirement date|
|---|---|---|
|[`2020-12-09`](/docs/natural-language-understanding?topic=natural-language-understanding-release-notes#9-december-2020)| <li>Version 2 English entity type system.</li>|   |
|[`2020-12-02`](/docs/natural-language-understanding?topic=natural-language-understanding-release-notes#2-december-2020)| <li>Version 2 Korean entity type system.</li><li>Version 2 Spanish entity type system.</li>|   |
|[`2020-08-01`](/docs/natural-language-understanding?topic=natural-language-understanding-release-notes#1-august-2020)| <li>Taxonomy changes aimed towards standardization of the label names in the default taxonomy.</li>|December 2, 2021|
|[`2019-07-12`](/docs/natural-language-understanding?topic=natural-language-understanding-release-notes#7-july-2019)<br><i><strong>Deprecated</strong></i>| <li>New English entities model with improved accuracy and confidence scores.</li>|August 1, 2021|
|[`2019-06-04`](/docs/natural-language-understanding?topic=natural-language-understanding-release-notes#4-june-2019)<br><i><strong>Deprecated</strong></i>|<li>Fixed a bug that caused entities requests with custom models to ignore the `limit` option.</li><li>The default `limit` value for all entities requests is now 50 for all models.</li><li>The maximum `limit` value of 250 entities has been removed.</li>|July 12, 2020|
|[`2018-11-16`](/docs/natural-language-understanding?topic=natural-language-understanding-release-notes#16-november-2018)<br><i><strong>Deprecated</strong></i>| <li>Version 2 Italian entity type system.</li>|July 12, 2020|
|[`2018-09-21`](/docs/natural-language-understanding?topic=natural-language-understanding-release-notes#21-september-2018)<br><i><strong>Deprecated</strong></i>| <li>Version 2 Portuguese entity type system.</li>|July 12, 2020|
|[`2018-03-16`](/docs/natural-language-understanding?topic=natural-language-understanding-release-notes#16-march-2018)<br><i><strong>Deprecated</strong></i>| <li>Version 2 French entity type system.</li><li>Version 2 German entity type system.</li>|July 12, 2020|
|[`2017-02-27`](/docs/natural-language-understanding?topic=natural-language-understanding-release-notes#27-february-2017)<br><i><strong>Deprecated</strong></i>| Base version.|July 12, 2020| 



