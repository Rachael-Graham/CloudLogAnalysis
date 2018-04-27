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


# Changement de plan
{: #change_plan}

Vous pouvez changer de plan de service {{site.data.keyword.loganalysisshort}} dans l'interface utilisateur {{site.data.keyword.Bluemix_notm}} ou en exécutant la commande `bx cf update-service`. Vous
pouvez choisir un plan de niveau supérieur ou inférieur à tout moment.
{:shortdesc}

## Modification du plan de service via l'interface utilisateur
{: #change_plan_ui}

Pour changer votre plan de service dans l'interface utilisateur {{site.data.keyword.Bluemix_notm}}, procédez comme suit :

1. Connectez-vous à {{site.data.keyword.Bluemix_notm}} : [http://bluemix.net ![Icône de lien externe](../../../icons/launch-glyph.svg "Icône de lien externe")](http://bluemix.net){:new_window}. 

2. Sélectionnez la région, l'organisation et l'espace où le service {{site.data.keyword.loganalysisshort}} est disponible.   

3. Cliquez sur l'instance de service {{site.data.keyword.loganalysisshort}} dans le *tableau de bord* {{site.data.keyword.Bluemix_notm}}.  
    
4. Sélectionnez l'onglet **Plan** dans le tableau de bord {{site.data.keyword.loganalysisshort}}.

    Des informations sur le plan en cours s'affichent.
	
5. Sélectionnez un nouveau plan de niveau supérieur ou inférieur. 

6. Cliquez sur **Sauvegarder**.




## Modification du plan de service via l'interface de ligne de commande
{: #change_plan_cli}

Pour modifier votre plan de service dans Bluemix via l'interface de ligne de commande, procédez comme suit :

1. Connectez-vous à une région, une organisation et un espace dans {{site.data.keyword.Bluemix_notm}}. 

    Pour plus d'informations, voir
[Comment se connecter
à {{site.data.keyword.Bluemix_notm}} ?](/docs/services/CloudLogAnalysis/qa/cli_qa.html#login).
	
2. Exécutez la commande `bx cf services` pour identifier le plan en cours et obtenir le nom du service {{site.data.keyword.loganalysisshort}} depuis la liste des services qui est disponible dans l'espace. 

    La valeur de la zone **name** est celle que vous devez utiliser pour modifier le plan. 

    Exemple :
	
	```
	$ bx cf services
    Getting services in org MyOrg / space dev as xxx@yyy.com...
    OK
    
    name              service          plan      bound apps   last operation
    Log Analysis-a4   ibmLogAnalysis   premium                create succeeded
    ```
	{: screen}
    
3. Choisissez un plan de niveau supérieur ou inférieur. Exécutez la commande `bx cf update-service`.
    
	```
	bx cf update-service service_name [-p new_plan]
	```
	{: codeblock}
	
	où 
	
	* *service_name* est le nom de votre service. Vous pouvez exécuter la commande `bx cf services` pour obtenir la valeur.
	* *new_plan* est le nom du plan.
	
	Le tableau suivant présente les différents plans et les valeurs prises en charge :
	
	<table>
	  <caption>Tableau 1. Liste des plans</caption>
	  <tr>
	    <th>Plan</th>
	    <th>Nom</th>
	  </tr>
	  <tr>
	    <td>Lite</td>
	    <td>standard</td>
	  </tr>
	  <tr>
	    <td>Collecte de journaux</td>
	    <td>premium</td>
	  </tr>
	  <tr>
	    <td>Collecte de journaux avec recherche de 2 Go/jour</td>
	    <td>premiumsearch2</td>
	  </tr>
	  <tr>
	    <td>Collecte de journaux avec recherche de 5 Go/jour</td>
	    <td>premiumsearch5</td>
	  </tr>
	  <tr>
	    <td>Collecte de journaux avec recherche de 10 Go/jour</td>
	    <td>premiumsearch10</td>
	  </tr>
	</table>
	
	Par exemple, pour passer au plan de niveau inférieur *Lite*, exécutez la commande suivante :
	
	```
	bx cf update-service "Log Analysis-a4" -p standard
    Updating service instance Log Analysis-a4 as xxx@yyy.com...
    OK
	```
	{: screen}

4. Vérifiez que le nouveau plan est modifié. Exécutez la commande `cf services`.

    ```
	bx cf services
    Getting services in org MyOrg / space dev as xxx@yyy.com...
    OK

    name              service          plan       bound apps   last operation
    Log Analysis-a4   ibmLogAnalysis   standard                update succeeded
	```
	{: screen}





