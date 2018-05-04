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

# Tipi di relazione (versione 2)

La seguente tabella elenca i tipi di relazione restituiti dal sistema di tipi di relazione _versione 2_. Il sistema di tipi di relazione utilizzato da {{site.data.keyword.nlushort}} varia in base alla lingua che stai utilizzando. Per ulteriori dettagli, vedi la pagina [Tipi di relazione](relations.html).
{: shortdesc}

I tipi di entità utilizzati da questo sistema di tipi di relazione sono elencati nella pagina [Tipi e sottotipi di entità (versione 2)](entity-types-v2.html).

| Relazione        | Descrizione |
|-----------------|----------------|
| affiliatedWith  | Esiste tra due entità che hanno un'affiliazione o sono connesse in modo simile. | 
| basedIn         | Esiste tra un'organizzazione e il luogo dove si trova principalmente, esclusivamente o intrinsecamente. |
| bornAt          | Esiste tra persona e il luogo dove sono nati. |
| bornOn          | Esiste tra una persona e la data e l'ora in cui sono nati. |
| clientOf        | Esiste tra due entità quando una è un cliente commerciale diretto dell'altra (ossia, paga per specifici servizi o prodotti). |
| colleague       | Esiste tra due persone che fanno parte della stessa organizzazione. |
| competitor      | Esiste tra due organizzazioni impegnate in una concorrenza economica. |
| contactOf       | Correla le informazioni di contatto con un'entità. |
| diedAt          | Esiste tra una persona e il posto in cui è deceduta. |
| diedOn          | Esiste tra una persona e la data e l'ora in cui è deceduta. |
| dissolvedOn     | Esiste tra un'organizzazione o URL e la data od ora di suo scioglimento. |
| educatedAt      | Esiste tra una persona e l'organizzazione presso la quale ha studiato. |
| employedBy      | Esiste tra due entità quando una paga l'altra per un lavoro o dei servizi specifici: deve essere coinvolta una ricompensa economica. In molte circostanze, contrassegnare questa relazione richiede la conoscenza del mondo. |
| foundedOn       | Esiste tra un'organizzazione o URL e la sua data od ora di istituzione. |
| founderOf       | Esiste tra una persona e una struttura, un'organizzazione o un URL da essa istituiti. |
| locatedAt       | Esiste tra un'entità e la sua posizione. |
| managerOf       | Esiste tra una persona e un'altra entità quali una persona o un'organizzazione che, come suo lavoro, gestisce. |
| memberOf        | Esiste tra un'entità, quali una persona o un'organizzazione, e un'altra entità a cui appartiene. |
| ownerOf         | Esiste tra un'entità, quali una persona o un'organizzazione, e un'altra entità che le appartiene. Il proprietario non deve avere una proprietà permanente dell'entità perché la relazione esista. |
| parentOf        | Esiste tra una persona e i suoi figli o figliastri. |
| partner         | Esiste tra due organizzazioni impegnate in una cooperazione economica. |
| partOf          | Esiste tra un'entità più piccola e una più grande dello stesso tipo o di tipi correlati in cui la seconda entità incorpora la prima. Se le entità sono entrambe degli eventi, il primo si deve verificare entro il lasso di tempo del secondo perché la relazione venga riconosciuta. |
| partOfMany      | Esiste tra entità più piccole e più grandi dello stesso tipo o di tipi correlati in cui la seconda entità, che deve essere plurale, include la prima, che può essere singolare o plurale. |
| populationOf    | Esiste tra un posto e il numero di persone che si trovano lì, o un'organizzazione e il numero di membri o dipendenti che ha. |
| measureOf      | Questa relazione include la quantità di un'entità o misura (altezza, peso ecc.) di un'entità. |
| relative        | Esiste tra due persone che sono parenti. Per identificare genitori, figli, fratelli e coniugi, usa le relazioni `parentOf`, `siblingOf`,e `spouseOf`. |
| residesIn       | Esiste tra una persona e il posto dove vive o dove è vissuta in precedenza. |
| shareholdersOf  | Esiste tra una persona o un'organizzazione e un'organizzazione di cui la prima entità è azionista.|
| siblingOf       | Esiste tra una persona e un suo fratello o fratellastro.     |
| spokespersonFor | Esiste tra una persona e una struttura, un'organizzazione o una persona che rappresenta. |
| spouseOf        | Esiste tra due persone coniugate. |
| subsidiaryOf    | Esiste tra due organizzazioni quando la prima è una filiale della seconda. |
