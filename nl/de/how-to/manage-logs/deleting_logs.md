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

# Protokolle löschen
{: #deleting_logs}

Mit dem Befehl [bx cf logging delete](/docs/services/CloudLogAnalysis/reference/logging_cli.html#status) können Sie Protokolle aus 'Log Collection' löschen. 
{:shortdesc}

* Sie können Protokolle für einen bestimmten Zeitraum löschen.
* Sie können Protokolle nach Typ löschen. Beachten Sie, dass jede Protokolldatei nur über einen Typ von Protokolleintrag verfügt.
* Sie können Protokolle für einen Bereich oder in der Kontodomäne löschen.


## Protokolle für einen bestimmten Zeitraum löschen
{: #time_range}

Führen Sie die folgenden Schritte aus:

1. Melden Sie sich bei einer Region, Organisation und bei einem Bereich in {{site.data.keyword.Bluemix_notm}} an. 

    Weitere Informationen finden Sie unter [Wie melde ich mich bei {{site.data.keyword.Bluemix_notm}} an?](/docs/services/CloudLogAnalysis/qa/cli_qa.html#login).
    
2. Führen Sie den Befehl *status* aus, um die in 'Log Collection' verfügbaren Protokolle anzuzeigen.

    ```
    bx cf logging status
    ```
    {: codeblock}
    
    Beispiel:
    
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
	
3. Löschen Sie die Protokolle, die für einen bestimmten Tag gespeichert sind.

    ```
	bx cf logging delete -s StartDate -e EndDate
	```
	{: codeblock}
	
	Dabei gilt:
	
	* *-s* legt das Startdatum in koordinierter Weltzeit (UTC) fest: JJJJ-MM-TT, z. B. 2006-01-02.
    * *-e* legt das Enddatum in koordinierter Weltzeit (UTC) fest: JJJJ-MM-TT
    	
	Führen Sie beispielsweise den folgenden Befehl aus, um die Protokolle für den 25. Mai 2017 zu löschen:
	
	```
	bx cf logging delete -s 2017-05-25 -e 2017-05-25
	```
	{: screen}

	
## Protokolle nach Protokolltyp für einen bestimmten Zeitraum löschen
{: #time_range}

Führen Sie die folgenden Schritte aus:

1. Melden Sie sich an einer Region, einer Organisation und einem Bereich in {{site.data.keyword.Bluemix_notm}} an. 

    Weitere Informationen finden Sie unter [Wie melde ich mich bei {{site.data.keyword.Bluemix_notm}} an?](/docs/services/CloudLogAnalysis/qa/cli_qa.html#login).
    
2. Führen Sie den Befehl *status* aus, um die in 'Log Collection' verfügbaren Protokolle anzuzeigen.

    ```
    bx cf logging status
    ```
    {: codeblock}
    
    Beispiel:
    
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
	
3. Löschen Sie die Protokolle, die für einen bestimmten Tag gespeichert sind.

    ```
	bx cf logging delete -s StartDate -e EndDate -t LogType
	```
	{: codeblock}
	
	Dabei gilt:
	
	* *-s* legt das Startdatum in koordinierter Weltzeit (UTC) fest: JJJJ-MM-TT, z. B. 2006-01-02.
    * *-e* legt das Enddatum in koordinierter Weltzeit (UTC) fest: JJJJ-MM-TT
	* *-t* legt den Protokolltyp fest.
    	
	Führen Sie beispielsweise den folgenden Befehl aus, um die Protokolle des Typs 'linux_syslog' für den 25. Mai 2017 zu löschen:
	
	```
	bx cf logging delete -s 2017-05-25 -e 2017-05-25 -t linux_syslog
	```
	{: screen}

		
	
## Kontoprotokolle nach Protokolltyp für einen bestimmten Zeitraum löschen
{: #time_range}

Führen Sie die folgenden Schritte aus:

1. Melden Sie sich an einer Region, einer Organisation und einem Bereich in {{site.data.keyword.Bluemix_notm}} an. 

    Weitere Informationen finden Sie unter [Wie melde ich mich bei {{site.data.keyword.Bluemix_notm}} an?](/docs/services/CloudLogAnalysis/qa/cli_qa.html#login).
    
2. Führen Sie den Befehl *status* aus, um die in 'Log Collection' verfügbaren Protokolle auf der Kontoebene anzuzeigen.

    ```
    bx cf logging status  -a
    ```
    {: codeblock}
    
    Beispiel:
    
    ```
    $ bx cf logging status -a
    +------------+--------+-------+--------------------+------------+
    |    DATE    |  COUNT | SIZE  |       TYPES        | SEARCHABLE |
    +------------+--------+-------+--------------------+------------+
    | 2017-05-24 |    16  | 3020  |        log         |   None     |
    +------------+--------+-------+--------------------+------------+
    | 2017-05-25 |   1224 | 76115 | linux_syslog,log   |    All     |
    +------------+--------+-------+--------------------+------------+
    ```
    {: screen}
	
3. Löschen Sie die Protokolle, die für einen bestimmten Tag gespeichert sind.

    ```
	bx cf logging delete -s StartDate -e EndDate -t LogType -a
	```
	{: codeblock}
	
	Dabei gilt:
	
	* *-s* legt das Startdatum in koordinierter Weltzeit (UTC) fest: JJJJ-MM-TT, z. B. 2006-01-02.
    * *-e* legt das Enddatum in koordinierter Weltzeit (UTC) fest: JJJJ-MM-TT
	* *-t* legt den Protokolltyp fest.
    	
	Führen Sie beispielsweise den folgenden Befehl aus, um die Protokolle des Typs 'linux_syslog' für den 25. Mai 2017 zu löschen, die in 'Log Collection' auf der Kontoebene gespeichert sind:
	
	```
	bx cf logging delete -s 2017-05-25 -e 2017-05-25 -t linux_syslog -a
	```
	{: screen}
	











