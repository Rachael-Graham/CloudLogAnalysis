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


# Retrieving the key owner for a cluster
{: #containers_key_owner}

Use the command *ibmcloud cs api-key-info* to get the {{site.data.keyword.loganalysisshort}} key owner for a cluster.
{:shortdesc}

Run the following command:

```
 ibmcloud cs api-key-info ClusterName
```
{: codeblock}

where **ClusterName** is the name of the cluster.


For example, the output of running the command is the following:

```
ibmcloud cs api-key-info MyDemoCluster
Getting information about the API key owner for cluster MyDemoCluster...
OK
Name           Email   
Joe Blogg      blogg@ibm.com   
```
{: screen}

The space ID is the value indicated for the **logSpace** field.
The space name is the value indicated for the **logSpaceName** field.
The organization ID is the value indicated for the **logOrg** field.
The organization name is the value indicated for the **logOrgName** field.

If these fields are empty, then, there is no CF organization and space associated to that cluster.



