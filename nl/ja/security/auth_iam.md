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


# IAM トークンの取得
{: #auth_iam}

アカウント・ドメイン内にあるログを {{site.data.keyword.loganalysisshort}} API を使用して管理するには、認証トークンを使用する必要があります。 {{{site.data.keyword.Bluemix_notm}} CLI を使用して IAM トークンを取得します。 トークンには有効期限があります。 
{:shortdesc}


## IAM トークンの取得
{: #iam_token_cli}

{{site.data.keyword.Bluemix_notm}} CLI を使用して許可トークンを取得するには、以下の手順を実行します。

1. {{site.data.keyword.Bluemix_notm}} CLI をインストールします。

   詳しくは、『[{{site.data.keyword.Bluemix}} CLI のダウンロードとインストール](/docs/cli/reference/bluemix_cli/download_cli.html#download_install)』を参照してください。
   
   CLI がインストールされている場合は、次のステップに進みます。
    
2. {{site.data.keyword.Bluemix_notm}} で、地域、組織、およびスペースにログインします。 

    詳しくは、『[{{site.data.keyword.Bluemix_notm}} にログインするにはどうすればよいですか](/docs/services/CloudLogAnalysis/qa/cli_qa.html#login)』を参照してください。
	
3. `bx iam oauth-tokens` コマンドを実行して、IAM トークンを取得します。

    ```
	bx iam oauth-tokens
	```
	{: codeblock}
	
	この出力は、そのスペースおよび組織でユーザー ID を認証するために使用する必要がある IAM トークンを返します。 この IAM トークンを「$iam_token」などのシェル変数にエクスポートできます。



**注:** トークンを使用する場合、API 呼び出しで渡すトークンの値から *Bearer* を削除してください。
