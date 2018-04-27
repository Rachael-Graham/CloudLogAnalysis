---

copyright:
  years: 2017, 2018

lastupdated: "2018-01-10"

---


{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}


# Obtención de la señal de IAM
{: #auth_iam}

Para gestionar los registros disponibles en el dominio de la cuenta mediante la API de {{site.data.keyword.loganalysisshort}}, debe utilizar una señal de autenticación. Utilice la CLI de {{{site.data.keyword.Bluemix_notm}} para obtener la señal de IAM. La señal tiene un tiempo de caducidad.
{:shortdesc}


## Obtención de la señal de IAM
{: #iam_token_cli}

Para obtener la señal de autorización mediante la CLI de {{site.data.keyword.Bluemix_notm}}, siga los pasos siguientes:

1. Instale la CLI de {{site.data.keyword.Bluemix_notm}}.

   Para obtener más información, consulte [Descargue e instale la CLI de {{site.data.keyword.Bluemix}}](/docs/cli/reference/bluemix_cli/download_cli.html#download_install).
   
   Si la CLI está instalada, continúe en el paso siguiente.
    
2. Inicie la sesión en una región, organización y espacio en {{site.data.keyword.Bluemix_notm}}. 

    Para obtener más información, consulte [Cómo iniciar la sesión en {{site.data.keyword.Bluemix_notm}}](/docs/services/CloudLogAnalysis/qa/cli_qa.html#login).
	
3. Ejecute el mandato `bx iam oauth-tokens` para obtener la señal de IAM. 

    ```
	bx iam oauth-tokens
	```
	{: codeblock}
	
	La salida devuelve la señal de IAM que debe utilizar para autenticas su ID de usuario en dicho espacio y organización.
puede exportar la señal de IAM a una variable de shell como por ejemplo `$iam_token`.



**Nota:** Cuando utilice la señal, elimine *Bearer* del valor de la señal que pasa en una llamada de API.
