---

copyright:
  years: 2017, 2018

lastupdated: "2018-01-31"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}


# 取得記載記號
{: #logging_token}

取得記載記號以將日誌傳送至 {{site.data.keyword.loganalysisshort}} 服務。
{:shortdesc}


## 取得記載記號，以使用 {{site.data.keyword.loganalysisshort}} CLI 將日誌傳送至空間 
{: #logging_token_la_cloud_cli}

若要取得可用來將日誌傳送至 {{site.data.keyword.loganalysisshort}} 服務的記載記號，請完成下列步驟：

1. 安裝 {{site.data.keyword.Bluemix_notm}} CLI。

   如需相關資訊，請參閱[下載並安裝 {{site.data.keyword.Bluemix_notm}} CLI](/docs/cli/reference/bluemix_cli/download_cli.html#download_install)。
   
   如果已安裝 CLI，請繼續進行下一步。
    
2. 登入 {{site.data.keyword.Bluemix_notm}} 中的地區、組織及空間。 

    如需相關資訊，請參閱[如何登入 {{site.data.keyword.Bluemix_notm}}](/docs/services/CloudLogAnalysis/qa/cli_qa.html#login)。
	
3. 執行下列指令：

	```
	bx logging token-get
	```
	{: codeblock}

此輸出會傳回記載記號。


## 取得記載記號，以使用 {{site.data.keyword.Bluemix_notm}} CLI 將日誌傳送至空間 
{: #logging_token_cloud_cli}

若要取得可用來將日誌傳送至 {{site.data.keyword.loganalysisshort}} 服務的記載記號，請完成下列步驟：

1. 安裝 {{site.data.keyword.Bluemix_notm}} CLI。

   如需相關資訊，請參閱[下載並安裝 {{site.data.keyword.Bluemix_notm}} CLI](/docs/cli/reference/bluemix_cli/download_cli.html#download_install)。
   
   如果已安裝 CLI，請繼續進行下一步。
    
2. 登入 {{site.data.keyword.Bluemix_notm}} 中的地區、組織及空間。 

    如需相關資訊，請參閱[如何登入 {{site.data.keyword.Bluemix_notm}}](/docs/services/CloudLogAnalysis/qa/cli_qa.html#login)。
	
3. 在 {{site.data.keyword.loganalysisshort}} 服務佈建所在的空間中建立服務金鑰。執行下列指令：

    列出服務，以取得空間中的 {{site.data.keyword.loganalysisshort}} 實例名稱：
	
	```
	bx service list
	```
	{: codeblock}
	
	例如：
	
	```
	bx service list
    Invoking 'cf services'...

    Getting services in org lopezdsr_org / space dev as xxx@yyyy...
    OK

    name              service          plan       bound apps   last operation
    Log Analysis-vg   ibmLogAnalysis   standard                create succeeded
    ```
	{: screen}
	
	建立金鑰。使用 **name** 的值作為 servicename，並輸入金鑰名稱。
	
	```
	bx service key-create servicename KeyName 
	```
	{: codeblock}
	
	例如，
	
	```
	bx service key-create "Log Analysis-vg" mykey2
    Invoking 'cf create-service-key Log Analysis-vg mykey2'...

    Creating service key mykey2 for service instance Log Analysis-vg as xxx@yyyy...
    OK
    ```
	{: screen}
	
4. 取得記載記號。執行下列指令：
	
	```
	bx service key-show name Keyname
	```
	{: codeblock}
	
	例如， 
	
	```
	bx service key-show "Log Analysis-vg" "mykey2" 
    Invoking 'cf service-key Log Analysis-vg mykey2'...

    Getting key mykey2 for service instance Log Analysis-vg as xxx@yyyy...

    {
     "LOG_INGESTION_MTLJ_URL": "https://ingest-eu-fra.logging.bluemix.net:9091",
     "logging_token": "sdtghyrtfde4",
     "space_id": "12345678-avfg-erft-b1f2-2efrtgcb1744"
    }
    ```
	{: screen}
	
	若要取得記載記號，您可以執行下列指令：
	
	```
	bx service key-show "Log Analysis-vg" "mykey2" | tail -n +4 | jq -r .logging_token
    sdtghyrtfde4
	```
	{: screen}

## 取得記載記號，以使用 Log Analysis CLI（CF 外掛程式）將日誌傳送至空間
{: #logging_token_cf_plugin}

若要取得可用來將日誌傳送至 {{site.data.keyword.loganalysisshort}} 服務的記載記號，請完成下列步驟：

1. 安裝 {{site.data.keyword.Bluemix_notm}} CLI。

   如需相關資訊，請參閱[下載並安裝 {{site.data.keyword.Bluemix}} CLI](/docs/cli/reference/bluemix_cli/download_cli.html#download_install)。
   
   如果已安裝 CLI，請繼續進行下一步。
    
2. 登入 {{site.data.keyword.Bluemix_notm}} 中的地區、組織及空間。 

    如需相關資訊，請參閱[如何登入 {{site.data.keyword.Bluemix_notm}}](/docs/services/CloudLogAnalysis/qa/cli_qa.html#login)。
	
3. 取得您已取得鑑別記號之空間的 GUID。

   如需相關資訊，請參閱[如何取得空間的 GUID](/docs/services/CloudLogAnalysis/qa/cli_qa.html#space_guid)。  
   
4. 取得記載記號。執行下列指令：

    ```
    bx cf logging auth
    ```
    {: codeblock}

此指令會傳回必要的*記載記號* 及*空間 ID*，以將日誌傳送至具有該 ID 的空間。	
	
## 取得記載記號，以使用 Log Analysis API 將日誌傳送至空間
{: #logging_token_api}


若要取得可用來將日誌傳送至 {{site.data.keyword.loganalysisshort}} 服務的記載記號，請完成下列步驟：

1. 安裝 {{site.data.keyword.Bluemix_notm}} CLI。

   如需相關資訊，請參閱[下載並安裝 {{site.data.keyword.Bluemix_notm}} CLI](/docs/cli/reference/bluemix_cli/download_cli.html#download_install)。
   
   如果已安裝 CLI，請繼續進行下一步。
    
2. 登入 {{site.data.keyword.Bluemix_notm}} 中的地區、組織及空間。 

    如需相關資訊，請參閱[如何登入 {{site.data.keyword.Bluemix_notm}}](/docs/services/CloudLogAnalysis/qa/cli_qa.html#login)。
	
3. 取得 [UAA 記號](/docs/services/CloudLogAnalysis/security/auth_uaa.html#uaa_cli)。

    例如，執行 `bx cf oauth-token` 指令來取得 UAA 記號。

	```
	bx cf oauth-token
	```
	{: codeblock}
	
	此輸出會傳回必要的 UAA 記號，以用來在該空間及組織中鑑別使用者 ID。

4. 取得空間的 GUID。

   如需相關資訊，請參閱[如何取得空間的 GUID](/docs/services/CloudLogAnalysis/qa/cli_qa.html#space_guid)。  
	
5. 匯出下列變數：TOKEN 及 SPACEID。

    * *TOKEN* 是您在前一個步驟中取得的 OAuth 記號，但沒有 Bearer。
	
	* *SPACEID* 是您在前一個步驟中取得之空間的 GUID。 
		
	例如，
	
	```
	export TOKEN="eyJhbGciOiJI....cGFzc3dvcmQiLCJjZiIsInVhYSIsIm9wZW5pZCJdfQ.JaoaVudG4jqjeXz6q3JQL_SJJfoIFvY8m-rGlxryWS8"
	export SPACEID="667fb895-abcd-defg-aaaa-cf4587341095"
	```
	{: screen}
	
6. 取得記載記號。執行下列指令：
 
    ```
	curl -k -X GET  --header "X-Auth-Token: ${TOKEN}"  --header "X-Auth-Project-Id: s-${SPACEID}"  LOGGING_ENDPOINT/token
    ```
    {: codeblock}	
	
	其中
	* SPACEID 是服務執行所在空間的 GUID。
	* TOKEN 是您在前一個步驟中取得的 UAA 記號，但沒有 Bearer 字首。
	* LOGGING_ENDPOINT 是組織及空間所在 {{site.data.keyword.Bluemix_notm}} 地區的 {{site.data.keyword.loganalysisshort}} 端點。每個地區的 LOGGING_ENDPOINT 都不同。若要查看不同端點的 URL，請參閱[端點](/docs/services/CloudLogAnalysis/manage_logs.html#endpoints)。
	
    此指令會傳回必要的記載記號，以用來將日誌傳送至該空間。
	
## 取得記載記號，以使用 Log Analysis API 將日誌傳送至帳戶網域
{: #logging_acc_token_api}


若要取得可用來將日誌傳送至 {{site.data.keyword.loganalysisshort}} 服務的記載記號，請完成下列步驟：

1. 安裝 {{site.data.keyword.Bluemix_notm}} CLI。

   如需相關資訊，請參閱[下載並安裝 {{site.data.keyword.Bluemix_notm}} CLI](/docs/cli/reference/bluemix_cli/download_cli.html#download_install)。
   
   如果已安裝 CLI，請繼續進行下一步。
    
2. 登入 {{site.data.keyword.Bluemix_notm}} 中的地區、組織及空間。 

    如需相關資訊，請參閱[如何登入 {{site.data.keyword.Bluemix_notm}}](/docs/services/CloudLogAnalysis/qa/cli_qa.html#login)。
	
3. 取得 [IAM 記號](/docs/services/CloudLogAnalysis/security/auth_iam.html#iam_token_cli)。

    此輸出會傳回 IAM 記號。

4. 取得帳戶的 GUID。

   如需相關資訊，請參閱[如何取得帳戶的 GUID](/docs/services/CloudLogAnalysis/qa/cli_qa.html#account_guid)。  
	
5. 匯出下列變數：TOKEN 及 AccountID。

    * *TOKEN* 是您在前一個步驟中取得的 OAuth 記號，但沒有 Bearer。
	
	* *AccountID* 是您在前一個步驟中取得之帳戶的 GUID。 
		
	例如，
	
	```
	export TOKEN="eyJhbGciOiJI....cGFzc3dvcmQiLCJjZiIsInVhYSIsIm9wZW5pZCJdfQ.JaoaVudG4jqjeXz6q3JQL_SJJfoIFvY8m-rGlxryWS8"
	export AccountID="667fb8953456fg41095"
	```
	{: screen}
	
6. 取得記載記號。執行下列指令：
 
    ```
	curl -k -X GET  --header "X-Auth-User-Token:iam ${TOKEN}"  --header "X-Auth-Project-Id: a-${AccountID}" -k  LOGGING_ENDPOINT/token
    ```
    {: codeblock}	
	
	其中
	* AccountID 是服務執行所在空間的 GUID。
	* TOKEN 是您在前一個步驟中取得的 IAM 記號，但沒有 Bearer 字首。
	* LOGGING_ENDPOINT 是組織及空間所在 {{site.data.keyword.Bluemix_notm}} 地區的 {{site.data.keyword.loganalysisshort}} 端點。每個地區的 LOGGING_ENDPOINT 都不同。若要查看不同端點的 URL，請參閱[端點](/docs/services/CloudLogAnalysis/manage_logs.html#endpoints)。
	
    此指令會傳回必要的記載記號，以用來將日誌傳送至帳戶網域。
	
