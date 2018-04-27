---

copyright:
  years: 2017, 2018

lastupdated: "2018-01-10"

---


{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Supresión de registros
{: #deleting_logs}

Utilice el mandato [bx cf logging delete](/docs/services/CloudLogAnalysis/reference/logging_cli.html#status) para suprimir los registros de la recopilación de registros.
{:shortdesc}

* Puede suprimir los registros comprendidos en un determinado intervalo de tiempo. 
* Puede suprimir registros por tipo. Tenga en cuenta que cada archivo de registro solo tiene un tipo de entradas de registro.
* Puede suprimir registros correspondientes a un espacio o a un dominio de la cuenta.


## Supresión de registros correspondientes a un determinado periodo de tiempo
{: #time_range}

Siga estos pasos:

1. Inicie la sesión en una región, organización y espacio en {{site.data.keyword.Bluemix_notm}}. 

    Para obtener más información, consulte [Cómo iniciar la sesión en {{site.data.keyword.Bluemix_notm}}](/docs/services/CloudLogAnalysis/qa/cli_qa.html#login).
    
2. Ejecute el mandato *status* para ver los registros disponibles en la recopilación de registros. 

    ```
    bx cf logging status
 ```
    {: codeblock}
    
    Por ejemplo,
    
    ```
    $ bx cf logging status
    +------------+--------+-------+--------------------+------------+
    |    DATE    |  COUNT | SIZE  |       TYPES        | SEARCHABLE |
    +------------+--------+-------+--------------------+------------+
    | 2017-05-24 |    16  | 3020  |        log         |   None     |
    +------------+--------+-------+--------------------+------------+
    | 2017-05-25 |   1224 | 76115 | linux_syslog,log   |    All     |
    +------------+--------+-------+--------------------+------------+
 ```
    {: screen}
	
3. Suprima los registros almacenados en un día específico.

    ```
	bx cf logging delete -s StartDate -e EndDate
	```
	{: codeblock}
	
	donde
	
	* *-s* define la fecha inicial en hora universal coordinada (UTC): AAAA-MM-DD, por ejemplo 2006-01-02.
    * *-e* define la fecha final en hora universal coordinada (UTC): AAAA-MM-DD
Por ejemplo, para suprimir los registros correspondientes al 25 de mayo de 2017, ejecute el mandato siguiente:
	 	```
	bx cf logging delete -s 2017-05-25 -e 2017-05-25
	```
	{: screen}

	
## Supresión de registros por tipo de registro correspondientes a un determinado periodo de tiempo
{: #time_range}

Siga estos pasos:

1. Inicie la sesión en una región, organización y espacio en {{site.data.keyword.Bluemix_notm}}.

  Para obtener más información, consulte [Cómo iniciar la sesión en {{site.data.keyword.Bluemix_notm}}](/docs/services/CloudLogAnalysis/qa/cli_qa.html#login).

 2. Ejecute el mandato *status* para ver los registros disponibles en la recopilación de registros.

    ```
    bx cf logging status
 ```
    {: codeblock}
    
    Por ejemplo,
    
    ```
    $ bx cf logging status
    +------------+--------+-------+--------------------+------------+
    |    DATE      |  COUNT | SIZE  |       TYPES              | SEARCHABLE |
    +------------+--------+-------+--------------------+------------+
    | 2017-05-24 |    16  | 3020  |        log         |   Ninguno        |
    +------------+--------+-------+--------------------+------------+
    | 2017-05-25 |   1224 | 76115 | linux_syslog,log    |    Todos        |
    +------------+--------+-------+--------------------+------------+
    ```
    {: screen}
	
3. Suprima los registros almacenados en un día específico.

    ```
	bx cf logging delete -s StartDate -e EndDate -t LogType
	```
	{: codeblock}
	
	donde
	
	* *-s* define la fecha inicial en hora universal coordinada (UTC): AAAA-MM-DD, por ejemplo 2006-01-02.
    * *-e* define la fecha final en hora universal coordinada (UTC): AAAA-MM-DD
    * *-t* define el tipo de registro.
Por ejemplo, para suprimir los registros de tipo linux_syslog correspondientes al 25 de mayo de 2017, ejecute el mandato siguiente:
	 	```
	bx cf logging delete -s 2017-05-25 -e 2017-05-25 -t linux_syslog
	```
	{: screen}

		
	
## Supresión de registros de la cuenta por tipo de registro correspondientes a un determinado periodo de tiempo
{: #time_range}

Siga estos pasos:

1. Inicie la sesión en una región, organización y espacio en {{site.data.keyword.Bluemix_notm}}.

  Para obtener más información, consulte [Cómo iniciar la sesión en {{site.data.keyword.Bluemix_notm}}](/docs/services/CloudLogAnalysis/qa/cli_qa.html#login).

 2. Ejecute el mandato *status* para ver los registros disponibles en la recopilación de registros a nivel de cuenta.

    ```
    bx cf logging status  -a
 ```
    {: codeblock}
    
    Por ejemplo,
    
    ```
    $ bx cf logging status -a
    +------------+--------+-------+--------------------+------------+
    |    DATE      |  COUNT | SIZE  |       TYPES              | SEARCHABLE |
    +------------+--------+-------+--------------------+------------+
    | 2017-05-24 |    16  | 3020  |        log         |   Ninguno        |
    +------------+--------+-------+--------------------+------------+
    | 2017-05-25 |   1224 | 76115 | linux_syslog,log    |    Todos        |
    +------------+--------+-------+--------------------+------------+
    ```
    {: screen}
	
3. Suprima los registros almacenados en un día específico.

    ```
	bx cf logging delete -s StartDate -e EndDate -t LogType -a
	```
	{: codeblock}
	
	donde
	
	* *-s* define la fecha inicial en hora universal coordinada (UTC): AAAA-MM-DD, por ejemplo 2006-01-02.
    * *-e* define la fecha final en hora universal coordinada (UTC): AAAA-MM-DD
    * *-t* define el tipo de registro.
Por ejemplo, para suprimir los registros de tipo linux_syslog correspondientes al 25 de mayo de 2017 almacenados en la recopilación de registros a nivel de cuenta, ejecute el mandato siguiente:
	 	```
	bx cf logging delete -s 2017-05-25 -e 2017-05-25 -t linux_syslog -a
	```
	{: screen}
	











