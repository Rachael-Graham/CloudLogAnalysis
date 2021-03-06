---

copyright:
  years: 2017, 2019

lastupdated: "2019-03-06"

keywords: IBM Cloud, logging

subcollection: cloudloganalysis

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}
{:important: .important}
{:note: .note}


# Externe Protokollhosts konfigurieren
{: #thirdparty_logging}

{{site.data.keyword.Bluemix_notm}} bewahrt eine begrenzte Menge an Protokolldaten im Speicher auf. Bei der Protokollierung von Daten werden die alten Informationen durch die neueren Daten ersetzt. Zur Aufbewahrung aller Protokolldaten können Sie Ihre Cloud Foundry-Anwendungsprotokolle auf einem externen Protokollhost, wie z. B. einem Protokoll-Management-Service eines anderen Anbieters, oder auf einem anderen Host speichern.
{:shortdesc}

Führen Sie die folgenden Schritte aus, um Protokolle aus Ihrer CF-App und dem System an einen externen Protokollhost zu übermitteln:

  1. Bestimmen Sie den Protokollierungsendpunkt.

	 Sie können Protokolle an einen Protokollaggregator eines Drittanbieters wie Papertrail, Splunk oder Sumologic senden. Sie können Protokolle auch an einen Syslog-Host, einen Syslog-Host mit TLS-Verschlüsselung (Transport Layer Security) oder an einen HTTP-POST-Endpunkt senden. Die Methoden zum Anfordern von Protokollierungsendpunkten sind für verschiedene Protokollhosts unterschiedlich.

  2. Erstellen Sie eine vom Benutzer bereitgestellte Serviceinstanz.

	 Verwenden Sie den Befehl `cf create-user-provided-service` (oder die Kurversion des Befehls `cups`, um eine vom Benutzer bereitgestellte Serviceinstanz zu erstellen:
	 
	 ```
	 cf create-user-provided-service <Servicename> -l <Protokollierungsendpunkt>
	 ```
	 {: codeblock}
	 
	 &lt;Servicename&gt;

	 Der Name der vom Benutzer bereitgestellten Serviceinstanz.

	 &lt;Protokollierungsendpunkt&gt;

	 Der Protokollierungsendpunkt, an den {{site.data.keyword.Bluemix_notm}} Protokolle sendet. In der folgenden Tabelle finden Sie Informationen zu den Werten, durch die die Variable *Protokollierungsendpunkt* in Ihrem Fall ersetzt werden kann:

	 <table>
	 <caption>Tabelle 1. Werte für Protokollierungsendpunkte</caption>
     <thead>
     <tr>
     <th>Protokollierungsendpunkt</th>
     <th>Befehl</th>
	 <th>Anmerkungen</th>
     </tr>
     </thead>
     <tbody>
     <tr>
     <td>syslog host</td>
     <td>`cf cups my-logs -l syslog://HOST:PORT`</td>
	 <td>Zum Aktivieren der Protokollierung an Papertrail geben Sie beispielsweise `cf cups my-logs -l syslog: //<papertrail-url>` ein. Ersetzen Sie `<papertrail-url>` durch die URL für Ihren Protokollierungsendpunkt von Papertrail.</td>
     </tr>
	 <tr>
     <td>syslog-tls host</td>
     <td>`cf cups my-logs -l syslog-tls://HOST:PORT`</td>
	 <td>Dem Zertifikat muss von einer Zertifizierungsstelle vertraut werden. Verwenden Sie keine selbst signierten Zertifikate.</td>
     </tr>
	 <tr>
     <td>HTTPS POST</td>
     <td>`cf cups my-logs -l https://HOST:PORT`</td>
	 <td>Dieser Endpunkt muss sich im öffentlichen Internet befinden und für {{site.data.keyword.Bluemix_notm}} zugänglich sein.</td>
     </tr>
     </tbody>
     </table>
  3. Binden Sie die Serviceinstanz an Ihre App.

	 Verwenden Sie den folgenden Befehl, um die Serviceinstanz an Ihre App zu binden:

	 ```
	 cf bind-service <App-Name> <Servicename>
	 ```
	 {: codeblock}
	 
	 &lt;App-Name&gt;

	 Der Name Ihrer App.

	 &lt;Servicename&gt;

	 Der Name der vom Benutzer bereitgestellten Serviceinstanz.

  4. Führen Sie für Ihre App ein erneutes Staging durch.
     Geben Sie `cf restage appname` ein, damit die Änderungen wirksam werden.

