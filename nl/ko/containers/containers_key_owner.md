---

copyright:
  years: 2017, 2018

lastupdated: "2018-01-16"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}


# 클러스터의 키 소유자 검색
{: #containers_key_owner}

*bx cs api-key-info* 명령을 사용하여 클러스터의 {{site.data.keyword.loganalysisshort}} 키 소유자를 가져오십시오.
{:shortdesc}

다음 명령을 실행하십시오.

```
 bx cs api-key-info ClusterName
```
{: codeblock}

여기서, **ClusterName**은 클러스터의 이름입니다. 


예를 들어 이 명령 실행에 대한 출력은 다음과 같습니다. 

```
bx cs api-key-info MyDemoCluster
Getting information about the API key owner for cluster MyDemoCluster...
OK
Name           Email   
Joe Blogg      blogg@ibm.com   
```
{: screen}

영역 ID는 **logSpace** 필드에 대해 표시되는 값입니다.
영역 이름은 **logSpaceName** 필드에 대해 표시되는 값입니다.
조직 ID는 **logOrg** 필드에 대해 표시되는 값입니다.
조직 이름은 **logOrgName** 필드에 대해 표시되는 값입니다.

이러한 필드가 비어 있는 경우 해당 클러스터와 연관된 CF 조직 및 영역이 없습니다.


