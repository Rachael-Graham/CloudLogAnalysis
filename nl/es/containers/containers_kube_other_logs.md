---

copyright:
  years: 2017, 2018

lastupdated: "2018-01-10"

---


{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}


# Habilitación de la recopilación automática de registros de clúster
{: #containers_kube_other_logs}

Para poder ver y analizar registros del clúster en el servicio {{site.data.keyword.loganalysisshort}}, debe configurar el clúster para que reenvíe estos registros al servicio {{site.data.keyword.loganalysisshort}}. {:shortdesc}

## Paso 1: Comprobar los permisos
{: step1}

Solo los usuarios con una política de IAM para {{site.data.keyword.containershort}} con permisos para gestionar clústeres pueden habilitar esta característica. Se necesita uno de los roles siguientes: *Administrador*, *Operador*

Para comprobar que el ID de usuario tiene una política de IAM asignada para gestionar clústeres, siga estos pasos:

**Nota:** Solo el propietario de la cuenta o los usuarios con permisos para asignar políticas pueden realizar este paso.

1. Inicie sesión en la consola de {{site.data.keyword.Bluemix_notm}}.Abra un navegador web y lance el panel de control de {{site.data.keyword.Bluemix_notm}}: [http://bluemix.net ![Icono de enlace externo](../../../icons/launch-glyph.svg "Icono de enlace externo")](http://bluemix.net){:new_window}
	
	Cuando inicia sesión con su ID de usuario y su contraseña, se abre la interfaz de usuario de {{site.data.keyword.Bluemix_notm}}.

2. En la barra de menús, pulse **Gestionar > Cuenta > Usuarios**.La ventana *Usuarios* muestra una lista de usuarios con sus direcciones de correo electrónico para la cuenta seleccionada actualmente.
	
3. Seleccione el ID de usuario y verifique que el ID de usuario tiene una política con permisos de *visor* para {{site.data.keyword.containershort}}.




## Paso 2: Configurar el contexto de clúster.
{: #step2}

Siga estos pasos:

1. Inicie la sesión en una región, organización y espacio en {{site.data.keyword.Bluemix_notm}}. 

    Para obtener más información, consulte [Cómo iniciar la sesión en {{site.data.keyword.Bluemix_notm}}](/docs/services/CloudLogAnalysis/qa/cli_qa.html#login).
    
2. Inicialice el plug-in del servicio {{site.data.keyword.loganalysisshort}}.

	```
	bx cs init
	```
	{: codeblock}

3. Establezca el contexto de terminal para el clúster.
    
	```
	bx cs cluster-config ClusterName
	```
	{: codeblock}

    El resultado de ejecutar este mandato muestra el mandato que debe ejecutar en el terminal para definir la vía de acceso a su archivo de configuración. Por ejemplo, para un clúster denominado *MyCluster*:

	```
	export KUBECONFIG=/Users/ibm/.bluemix/plugins/container-service/clusters/MyCluster/kube-config-hou02-MyCluster.yml
	```
	{: codeblock}

4. Copie y pegue el mandato para definir la variable de entorno en el terminal y luego pulse **Intro**.



## Paso 3: Configurar el clúster
{: step3}

Puede elegir los registros del clúster que desea reenviar al servicio {{site.data.keyword.loganalysisshort}}. 

* Para habilitar la recopilación automática de registros y el reenvío de stdout y stderr, consulte [Habilitación de la recopilación automática de registros y del reenvío de registros de contenedor](/docs/services/CloudLogAnalysis/containers/containers_kube_other_logs.html#containers).
* Para habilitar la recopilación automática y el reenvío de registros de registros de la aplicación, consulte [Habilitación de la recopilación automática de registros y del reenvío de registro de aplicación](/docs/services/CloudLogAnalysis/containers/containers_kube_other_logs.html#apps).
* Para habilitar la recopilación automática de registros y el reenvío de registro de trabajo, consulte [Habilitación de la recopilación automática de registros y del reenvío de registros de trabajo](/docs/services/CloudLogAnalysis/containers/containers_kube_other_logs.html#workers).
* Para habilitar la recopilación automática de registros y el reenvío de registros de componentes del sistema Kubernetes, consulte [Habilitación de la recopilación automática de registros y del reenvío de registros de componentes del sistema Kubernetes](/docs/services/CloudLogAnalysis/containers/containers_kube_other_logs.html#system).
* Para habilitar la recopilación automática de registros y el reenvío de registros del controlador de Ingress de Kubernetes, consulte [Habilitación de la recopilación automática de registros y del reenvío de registros del controlador de Ingress de Kubernetes](/docs/services/CloudLogAnalysis/containers/containers_kube_other_logs.html#controller).



## Paso 4: Establecer permisos para el propietario de claves de {{site.data.keyword.containershort_notm}}
{: #step4}

Al reenviar registros a un espacio, también debe otorgar permisos de Cloud Foundry (CF) al propietario de claves de {{site.data.keyword.containershort}} en la organización y el espacio. El propietario de claves necesita el rol *orgManager* para la organización, y *SpaceManager* y *Developer* para el espacio.

Siga estos pasos:

1. Identifique el usuario en la cuenta que sea la propietaria de claves de {{site.data.keyword.containershort}}. Desde un terminal, ejecute el mandato siguiente:

    ```
    bx cs api-key-info ClusterName
    ```
    {: codeblock}
    
    donde *ClusterName* es el nombre del clúster.
    
2. Verifique que el usuario que se identifica como el propietario de claves de {{site.data.keyword.containershort}} tenga el rol *orgManager* para la organización, y *SpaceManager* y *Developer* para el espacio.

    Inicie sesión en la consola de {{site.data.keyword.Bluemix_notm}}. Abra un navegador web y lance el panel de control de {{site.data.keyword.Bluemix_notm}}: [http://bluemix.net ![Icono de enlace externo](../../../icons/launch-glyph.svg "Icono de enlace externo")](http://bluemix.net){:new_window} Después de iniciar sesión con su ID de usuario y contraseña, se abrirá la IU de {{site.data.keyword.Bluemix_notm}}.

    En la barra de menús, pulse **Gestionar > Cuenta > Usuarios**.La ventana *Usuarios* muestra una lista de usuarios con sus direcciones de correo electrónico para la cuenta seleccionada actualmente.
	
    Seleccione el ID del usuario, y verifique que el usuario tenga el rol *orgManager* para la organización, y *SpaceManager* y *Developer* para el espacio.
 
3. Si el usuario no tiene los permisos correctos, siga estos pasos:

    1. Otorgue al usuario los permisos siguientes: rol de *orgManager* para la organización, y *SpaceManager* y *Developer* para el espacio. Para obtener más información, consulte [Cómo otorgar permisos a un usuario para ver registros del espacio mediante la IU de IBM Cloud](/docs/services/CloudLogAnalysis/security/grant_permissions.html#grant_permissions_ui_space).
    
    2. Renueve la configuración de registro. Ejecute el mandato siguiente:
    
        ```
        bx cs logging-config-refresh ClusterName
        ```
        {: codeblock}
        
        donde *ClusterName* es el nombre del clúster.
  




## Habilitación de la recopilación automática de registros y del reenvío de registros de contenedor 
{: #containers}

Ejecute el siguiente mandato para enviar los archivos de registro *stdout* y *stderr* al servicio de {{site.data.keyword.loganalysisshort}}:

```
bx cs logging-config-create ClusterName --logsource container --namespace '*' --type ibm --hostname EndPoint --port 9091 --org OrgName --space SpaceName 
```
{: codeblock}

donde 

* *ClusterName* es el nombre del clúster.
* *EndPoint* es el URL para el servicio de registro en la región donde se suministra el servicio de {{site.data.keyword.loganalysisshort}}. Para obtener una lista de puntos finales, consulte [Puntos finales](/docs/services/CloudLogAnalysis/log_ingestion.html#log_ingestion_urls).
* *OrgName* es el nombre de la organización donde está disponible el espacio.
* *SpaceName* es el nombre del espacio donde se suministra el servicio de {{site.data.keyword.loganalysisshort}}.


Por ejemplo, para crear una configuración de registro que reenvíe los registros stdout y stderr al dominio de la cuenta en la región alemana, ejecute el mandato siguiente:

```
bx cs logging-config-create MyCluster --logsource container --type ibm --namespace '*' --type ibm --hostname ingest-eu-fra.logging.bluemix.net --port 9091 
```
{: screen}

Para crear una configuración de registro que reenvíe los registros stdout y stderr al dominio del espacio en la región alemana, ejecute el mandato siguiente:

```
bx cs logging-config-create MyCluster --logsource container --type ibm --namespace '*' --type ibm --hostname ingest-eu-fra.logging.bluemix.net --port 9091 --org MyOrg --space MySpace
```
{: screen}



## Habilitación de la recopilación automática de registros y del reenvío de registros de aplicación 
{: #apps}

Ejecute el siguiente mandato para enviar los archivos de registro */var/log/apps/**/.log* y */var/log/apps/*/.err* al servicio {{site.data.keyword.loganalysisshort}}: 

```
bx cs logging-config-create ClusterName --logsource application --type ibm --hostname EndPoint --port 9091 --org OrgName --space SpaceName 
```
{: codeblock}

donde 

* *ClusterName* es el nombre del clúster.
* *EndPoint* es el URL para el servicio de registro en la región donde se suministra el servicio de {{site.data.keyword.loganalysisshort}}. Para obtener una lista de puntos finales, consulte [Puntos finales](/docs/services/CloudLogAnalysis/log_ingestion.html#log_ingestion_urls).
* *OrgName* es el nombre de la organización donde está disponible el espacio.
* *SpaceName* es el nombre del espacio donde se suministra el servicio de {{site.data.keyword.loganalysisshort}}.


Por ejemplo, para crear una configuración de registro que reenvíe los registros de aplicaciones a un dominio de espacio en la región alemana, ejecute el mandato siguiente:

```
bx cs logging-config-create MyCluster --logsource application --type ibm --hostname ingest-eu-fra.logging.bluemix.net --port 9091 --org MyOrg --space MySpace
```
{: screen}

Por ejemplo, para crear una configuración de registro que reenvíe los registros de aplicaciones al dominio de la cuenta en la región alemana, ejecute el mandato siguiente:

```
bx cs logging-config-create MyCluster --logsource application --type ibm --hostname ingest-eu-fra.logging.bluemix.net --port 9091 
```
{: screen}



## Habilitación de la recopilación automática de registros y del reenvío de registros de trabajo 
{: #workers}


Ejecute el siguiente mandato para enviar los archivos de registro */var/log/syslog* y */var/log/auth.log* al servicio {{site.data.keyword.loganalysisshort}}: 

```
bx cs logging-config-create ClusterName --logsource worker --type ibm --hostname EndPoint --port 9091 --org OrgName --space SpaceName 
```
{: codeblock}

donde 

* *ClusterName* es el nombre del clúster.
* *EndPoint* es el URL para el servicio de registro en la región donde se suministra el servicio de {{site.data.keyword.loganalysisshort}}. Para obtener una lista de puntos finales, consulte [Puntos finales](/docs/services/CloudLogAnalysis/log_ingestion.html#log_ingestion_urls).
* *OrgName* es el nombre de la organización donde está disponible el espacio.
* *SpaceName* es el nombre del espacio donde se suministra el servicio de {{site.data.keyword.loganalysisshort}}.



Por ejemplo, para crear una configuración de registro que reenvíe los registros de trabajo a un dominio de espacio en la región alemana, ejecute el mandato siguiente:

```
bx cs logging-config-create MyCluster --logsource worker  --type ibm --hostname ingest-eu-fra.logging.bluemix.net --port 9091 --org OrgName --space SpaceName 
```
{: screen}

Por ejemplo, para crear una configuración de registro que reenvíe los registros de trabajo al dominio de la cuenta en la región alemana, ejecute el mandato siguiente:

```
bx cs logging-config-create MyCluster --logsource worker  --type ibm --hostname ingest-eu-fra.logging.bluemix.net --port 9091 
```
{: screen}



## Habilitación de la recopilación automática de registros y del reenvío de registros de componentes del sistema Kubernetes
{: #system}

Ejecute el siguiente mandato para enviar los archivos de registro */var/log/kubelet.log* y */var/log/kube-proxy.log* al servicio {{site.data.keyword.loganalysisshort}}: 

```
bx cs logging-config-create ClusterName --logsource kubernetes --type ibm --hostname EndPoint --port 9091 --org OrgName --space SpaceName 
```
{: codeblock}

donde 

* *ClusterName* es el nombre del clúster.
* *EndPoint* es el URL para el servicio de registro en la región donde se suministra el servicio de {{site.data.keyword.loganalysisshort}}. Para obtener una lista de puntos finales, consulte [Puntos finales](/docs/services/CloudLogAnalysis/log_ingestion.html#log_ingestion_urls).
* *OrgName* es el nombre de la organización donde está disponible el espacio.
* *SpaceName* es el nombre del espacio donde se suministra el servicio de {{site.data.keyword.loganalysisshort}}.



Por ejemplo, para crear una configuración de registro que reenvíe los registros de componentes de sistema de Kubernetes a un dominio de espacio en la región alemana, ejecute el mandato siguiente:

```
bx cs logging-config-create MyCluster --logsource kubernetes --type ibm --hostname ingest-eu-fra.logging.bluemix.net --port 9091 --org OrgName --space SpaceName 
```
{: screen}

Por ejemplo, para crear una configuración de registro que reenvíe los registros de componentes de sistema de Kubernetes en el dominio de la cuenta en la región alemana, ejecute el mandato siguiente:

```
bx cs logging-config-create MyCluster --logsource kubernetes --type ibm --hostname ingest-eu-fra.logging.bluemix.net --port 9091 
```
{: screen}



## Habilitación de la recopilación automática de registros y del reenvío de registros del controlador de Ingress de Kubernetes
{: #controller}

Ejecute el siguiente mandato para enviar los archivos de registro */var/log/alb/ids/.log*, */var/log/alb/ids/.err*, */var/log/alb/customerlogs/.log* y /var/log/alb/customerlogs/.err* al servicio {{site.data.keyword.loganalysisshort}}: 

```
bx cs logging-config-create ClusterName --logsource ingress --type ibm --hostname EndPoint --port 9091 --org OrgName --space SpaceName s
```
{: codeblock}

donde 

* *ClusterName* es el nombre del clúster.
* *EndPoint* es el URL para el servicio de registro en la región donde se suministra el servicio de {{site.data.keyword.loganalysisshort}}. Para obtener una lista de puntos finales, consulte [Puntos finales](/docs/services/CloudLogAnalysis/log_ingestion.html#log_ingestion_urls).
* *OrgName* es el nombre de la organización donde está disponible el espacio.
* *SpaceName* es el nombre del espacio donde se suministra el servicio de {{site.data.keyword.loganalysisshort}}.



Por ejemplo, para crear una configuración de registro que reenvíe los registros de controlador de ingress a un dominio de espacio en la región alemana, ejecute el mandato siguiente:

```
bx cs logging-config-create MyLoggingDemoCluster --logsource ingress --type ibm --hostname ingest-eu-fra.logging.bluemix.net --port 9091 --org OrgName --space SpaceName 
```
{: screen}

Por ejemplo, para crear una configuración de registro que reenvíe los registros de controlador de ingress en el dominio de la cuenta en la región alemana, ejecute el mandato siguiente:

```
bx cs logging-config-create MyLoggingDemoCluster --logsource ingress --type ibm --hostname ingest-eu-fra.logging.bluemix.net --port 9091  
```
{: screen}


