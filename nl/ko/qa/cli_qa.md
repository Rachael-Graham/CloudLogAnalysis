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


# IBM Cloud CLI 사용에 대한 FAQ
{: #cli_qa}

{{site.data.keyword.loganalysisshort}} 서비스에서 {{site.data.keyword.Bluemix}} CLI 사용에 대한 일반적인 질문에 대한 답변입니다.
{:shortdesc}

* [{{site.data.keyword.Bluemix_notm}}에 로그인하는 방법](/docs/services/CloudLogAnalysis/qa/cli_qa.html#login)
* [{{site.data.keyword.Bluemix_notm}} CLI를 설치하는 방법](/docs/services/CloudLogAnalysis/qa/cli_qa.html#install_bmx_cli)
* [계정의 GUID를 가져오는 방법](/docs/services/CloudLogAnalysis/qa/cli_qa.html#account_guid)
* [조직의 GUID를 가져오는 방법](/docs/services/CloudLogAnalysis/qa/cli_qa.html#org_guid)
* [영역의 GUID를 가져오는 방법](/docs/services/CloudLogAnalysis/qa/cli_qa.html#space_guid)

## IBM Cloud에 어떻게 로그인합니까?
{: #login}

다음 명령을 실행하여 {{site.data.keyword.Bluemix_notm}}의 지역, 조직 및 영역에 로그인하십시오. 

```
bx login -a Endpoint
```
{: codeblock}
	
여기서, *Endpoint*는 {{site.data.keyword.Bluemix_notm}}에 로그인할 URL입니다. 이 URL은 지역에 따라 다릅니다. 
	
<table>
    <caption>{{site.data.keyword.Bluemix_notm}}에 액세스하는 엔드포인트 목록</caption>
	<tr>
	  <th>지역</th>
	  <th>URL</th>
	</tr>
	<tr>
	  <td>독일</td>
	  <td>api.eu-de.bluemix.net</td>
	</tr>
	<tr>
	  <td>시드니</td>
	  <td>api.au-syd.bluemix.net</td>
	</tr>
	<tr>
	  <td>미국 남부</td>
	  <td>api.ng.bluemix.net</td>
	</tr>
	<tr>
	  <td>영국</td>
	  <td>api.eu-gb.bluemix.net</td>
	</tr>
</table>

예를 들어, 미국 남부 지역에 로그인하려면 다음 명령을 실행하십시오.
	
```
bx login -a https://api.ng.bluemix.net
```
{: codeblock}

지시사항을 따르십시오.  

그런 다음 조직과 영역을 설정하십시오. 다음 명령을 실행하십시오.

```
bx target -o OrgName -s SpaceName
```
{: codeblock}

여기서

* OrgName은 조직의 이름입니다. 
* SpaceName은 영역의 이름입니다. 

	
	
## IBM Cloud CLI를 어떻게 설치합니까?
{: #install_bmx_cli}

[{{site.data.keyword.Bluemix}} CLI 다운로드 및 설치](/docs/cli/reference/bluemix_cli/download_cli.html#download_install)를 참조하십시오.



## 계정 GUID를 가져오는 방법은 무엇입니까?
{: #account_guid}
	
다음 단계를 완료하여 계정의 GUID를 가져오십시오. 
	
1. {{site.data.keyword.Bluemix_notm}}의 지역, 조직 및 영역에 로그인하십시오. 

    자세한 정보는 [{{site.data.keyword.Bluemix_notm}}에 로그인하는 방법](/docs/services/CloudLogAnalysis/qa/cli_qa.html#login)을 참조하십시오.
	
2. `bx iam accounts` 명령을 실행하여 계정의 GUID를 가져오십시오. 

    ```
	bx iam accounts
	```
	{: codeblock}
	
	예를 들어 사용자 xxx@yyy.com의 해당 GUID가 있는 모든 계정을 검색하려면 다음 명령을 실행하십시오.
	
	```
	bx iam accounts
	Retrieving all accounts of xxx@yyy.com...
    OK
    Account GUID                       Name                               Type    State    Owner User ID
    12345123451234512345123451234512   A Account                          TRIAL   ACTIVE   xxx@yyy.com
    23456234562345622456234561234561   B Account                          TRIAL   ACTIVE   zzz@yyy.com
	```
	{: screen}

	
## 조직의 GUID를 가져오는 방법
{: #org_guid}

다음 단계를 완료하여 조직의 GUID를 가져오십시오.
	
1. {{site.data.keyword.Bluemix_notm}}의 지역, 조직 및 영역에 로그인하십시오.

    자세한 정보는 [{{site.data.keyword.Bluemix_notm}}에 로그인하는 방법](/docs/services/CloudLogAnalysis/qa/cli_qa.html#login)을 참조하십시오.

2. `bx iam org` 명령을 실행하여 조직 GUID를 가져오십시오.

    ```
    bx iam org NAME --guid
    ```
    {: codeblock}
	
    여기서 NAME은 {{site.data.keyword.Bluemix_notm}} 조직의 이름입니다.
		
		
		
## 영역의 GUID를 가져오는 방법
{: #space_guid}
	
다음 단계를 완료하여 영역의 GUID를 가져오십시오.
	
1. {{site.data.keyword.Bluemix_notm}}의 지역, 조직 및 영역에 로그인하십시오.

    자세한 정보는 [{{site.data.keyword.Bluemix_notm}}에 로그인하는 방법](/docs/services/CloudLogAnalysis/qa/cli_qa.html#login)을 참조하십시오.

2. `bx iam space` 명령을 실행하여 영역 GUID를 가져오십시오.

    ```
    bx iam space NAME --guid
    ```
    {: codeblock}
	
    여기서, NAME은 {{site.data.keyword.Bluemix_notm}} 영역의 이름입니다.
	
    예를 들어 영역 *dev*의 GUID를 가져오려면 다음 명령을 실행하십시오.
	
    ```
    bx iam space dev --guid
    e03afff1-3456-4af6-1234-59treg1b0abc
    ```
    {: screen}




		
		