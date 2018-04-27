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


# Plan ändern
{: #change_plan}

Sie können den {{site.data.keyword.loganalysisshort}}-Serviceplan über die {{site.data.keyword.Bluemix_notm}}-Benutzerschnittstelle oder durch das Ausführen des Befehls `bx cf update-service` ändern. Sie können Ihren Plan jederzeit aktualisieren oder reduzieren.
{:shortdesc}

## Serviceplan über die Benutzerschnittstelle ändern
{: #change_plan_ui}

Um Ihren Serviceplan über die {{site.data.keyword.Bluemix_notm}}-Benutzerschnittstelle zu ändern, führen Sie die folgenden Schritte aus:

1. Melden Sie sich bei {{site.data.keyword.Bluemix_notm}} an: [http://bluemix.net ![Symbol für externen Link](../../../icons/launch-glyph.svg "Symbol für externen Link")](http://bluemix.net){:new_window}. 

2. Wählen Sie die Region, Organisation und den Bereich aus, in dem der {{site.data.keyword.loganalysisshort}}-Service verfügbar ist.  

3. Klicken Sie im {{site.data.keyword.Bluemix_notm}}-*Dashboard* auf die {{site.data.keyword.loganalysisshort}}-Serviceinstanz. 
    
4. Wählen Sie die Registerkarte **Plan** im {{site.data.keyword.loganalysisshort}}-Dashboard aus.

    Daraufhin werden Informationen zu Ihrem aktuellen Plan angezeigt.
	
5. Wählen Sie einen neuen Plan aus, um Ihren Plan zu aktualisieren oder zu reduzieren. 

6. Klicken Sie auf **Speichern**.




## Serviceplan über die Befehlszeilenschnittstelle ändern
{: #change_plan_cli}

Um Ihren Serviceplan in Bluemix über die Befehlszeilenschnittstelle zu ändern, führen Sie die folgenden Schritte aus:

1. Melden Sie sich bei einer Region, Organisation und bei einem Bereich in {{site.data.keyword.Bluemix_notm}} an. 

    Weitere Informationen finden Sie unter [Wie melde ich mich bei {{site.data.keyword.Bluemix_notm}} an?](/docs/services/CloudLogAnalysis/qa/cli_qa.html#login).
	
2. Führen Sie den Befehl `bx cf services` aus, um Ihren aktuellen Plan zu prüfen und um den {{site.data.keyword.loganalysisshort}}-Servicenamen aus der Liste der Services anzufordern, die in dem Bereich verfügbar sind. 

    Der Wert für das Feld **name** ist der Name, den Sie verwenden müssen, um den Plan zu ändern. 

    Beispiel:
	
	```
	$ bx cf services
    Getting services in org MyOrg / space dev as xxx@yyy.com...
    OK
    
    name              service          plan      bound apps   last operation
    Log Analysis-a4   ibmLogAnalysis   premium                create succeeded
    ```
	{: screen}
    
3. Aktualisieren oder reduzieren Sie Ihren Plan. Führen Sie den Befehl `bx cf update-service` aus.
    
	```
	bx cf update-service Servicename [-p neuer_Plan]
	```
	{: codeblock}
	
	Dabei gilt: 
	
	* *Servicename* ist der Name Ihres Service. Sie können den Befehl `bx cf services` ausführen, um den Wert abzurufen.
	* *neuer_Plan* ist der Name des Plans.
	
	In der folgenden Tabelle werden die verschiedenen Pläne und die unterstützten Werte aufgeführt:
	
	<table>
	  <caption>Tabelle 1. Liste der Pläne.</caption>
	  <tr>
	    <th>Plan</th>
	    <th>Name</th>
	  </tr>
	  <tr>
	    <td>Lite</td>
	    <td>standard</td>
	  </tr>
	  <tr>
	    <td>Log Collection</td>
	    <td>premium</td>
	  </tr>
	  <tr>
	    <td>Log Collection mit Suche bis 2GB/Tag</td>
	    <td>premiumsearch2</td>
	  </tr>
	  <tr>
	    <td>Log Collection mit Suche bis 5GB/Tag</td>
	    <td>premiumsearch5</td>
	  </tr>
	  <tr>
	    <td>Log Collection mit Suche bis 10GB/Tag</td>
	    <td>premiumsearch10</td>
	  </tr>
	</table>
	
	Beispiel: Um Ihren Plan auf den *Lite*-Plan zu reduzieren, führen Sie den folgenden Befehl aus:
	
	```
	bx cf update-service "Log Analysis-a4" -p standard
    Updating service instance Log Analysis-a4 as xxx@yyy.com...
    OK
	```
	{: screen}

4. Überprüfen Sie, ob der neue Plan geändert ist. Führen Sie den Befehl `cf services` aus.

    ```
	bx cf services
    Getting services in org MyOrg / space dev as xxx@yyy.com...
    OK

    name              service          plan       bound apps   last operation
    Log Analysis-a4   ibmLogAnalysis   standard                update succeeded
	```
	{: screen}





