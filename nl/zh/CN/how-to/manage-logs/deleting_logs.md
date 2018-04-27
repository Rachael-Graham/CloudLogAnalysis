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

# 删除日志
{: #deleting_logs}

使用 [bx cf logging delete](/docs/services/CloudLogAnalysis/reference/logging_cli.html#status) 命令从“日志收集”删除日志。
{:shortdesc}

* 您可以删除特定时间范围内的日志。
* 您可以按类型删除日志。请注意，每个日志文件仅有一种类型的日志条目。
* 您可以删除空间或帐户域中的日志。


## 删除特定时间段的日志
{: #time_range}

请完成以下步骤：

1. 登录到 {{site.data.keyword.Bluemix_notm}} 中的区域、组织和空间。 

    有关更多信息，请参阅[如何登录到 {{site.data.keyword.Bluemix_notm}}](/docs/services/CloudLogAnalysis/qa/cli_qa.html#login)。
    
2. 运行 *status* 命令以查看“日志收集”中可用的日志。

    ```
    bx cf logging status
    ```
    {: codeblock}
    
    例如：
    
    ```
    $ bx cf logging status
    +------------+--------+-------+--------------------+------------+
    |    DATE    |  COUNT | SIZE  |       TYPES        | SEARCHABLE |
    +------------+--------+-------+--------------------+------------+
    | 2017-05-24 |    16  | 3020  |        log         |   None     |
    +------------+--------+-------+--------------------+------------+
    | 2017-05-25 |   1224 | 76115 | linux_syslog,log   |    All     |
    +------------+--------+-------+--------------------+------------+
    ```
    {: screen}
	
3. 删除在特定日期存储的日志。

    ```
	bx cf logging delete -s StartDate -e EndDate
	```
	{: codeblock}
    
    其中
	
	* *-s* 会设置开始日期，格式为全球标准时间 (UTC)：YYYY-MM-DD，例如 2006-01-02。
    * *-e* 会设置结束日期，格式为全球标准时间 (UTC)：YYYY-MM-DD
    	
	例如，要删除 2017 年 5 月 25 日的日志，请运行以下命令：
	
	```
	bx cf logging delete -s 2017-05-25 -e 2017-05-25
	```
	    {: screen}
	
    ## 按日志类型删除特定时间段的日志
{: #time_range}

完成以下步骤：

1. 登录到 {{site.data.keyword.Bluemix_notm}} 中的区域、组织和空间。

    有关更多信息，请参阅[如何登录到 {{site.data.keyword.Bluemix_notm}}](/docs/services/CloudLogAnalysis/qa/cli_qa.html#login)。

2. 运行 *status* 命令以查看“日志收集”中可用的日志。

    ```
    bx cf logging status
    ```
    {: codeblock}

    例如：
```
    $ bx cf logging status
    +------------+--------+-------+--------------------+------------+
    |    DATE    |  COUNT | SIZE  |       TYPES        | SEARCHABLE |
    +------------+--------+-------+--------------------+------------+
    | 2017-05-24 |    16  | 3020  |        log|   None     |
    +------------+--------+-------+--------------------+------------+
    | 2017-05-25 |   1224 | 76115 | linux_syslog,log   |    All     |
    +------------+--------+-------+--------------------+------------+
    ```
    {: screen}
	
3. 删除在特定日期存储的日志。

    ```
	bx cf logging delete -s StartDate -e EndDate -t LogType
	```
	{: codeblock}
    
    其中
	
	* *-s* 会设置开始日期，格式为全球标准时间 (UTC)：YYYY-MM-DD，例如 2006-01-02。
    * *-e* 会设置结束日期，格式为全球标准时间 (UTC)：YYYY-MM-DD
	* *-t* 会设置日志类型。
    	
	例如，要删除 2017 年 5 月 25 日类型为 linux_syslog 的日志，请运行以下命令：
	
	```
	bx cf logging delete -s 2017-05-25 -e 2017-05-25 -t linux_syslog
	```
	{: screen}
    
    ## 按日志类型删除特定时间段的帐户日志
{: #time_range}

完成以下步骤：

1. 登录到 {{site.data.keyword.Bluemix_notm}} 中的区域、组织和空间。

    有关更多信息，请参阅[如何登录到 {{site.data.keyword.Bluemix_notm}}](/docs/services/CloudLogAnalysis/qa/cli_qa.html#login)。

2. 运行 *status* 命令以在帐户级别查看“日志收集”中可用的日志。

    ```
    bx cf logging status  -a
    ```
    {: codeblock}

    例如：
```
    $ bx cf logging status -a
    +------------+--------+-------+--------------------+------------+
    |    DATE    |  COUNT | SIZE  |       TYPES        | SEARCHABLE |
    +------------+--------+-------+--------------------+------------+
    | 2017-05-24 |    16  | 3020  |        log|   None     |
    +------------+--------+-------+--------------------+------------+
    | 2017-05-25 |   1224 | 76115 | linux_syslog,log   |    All     |
    +------------+--------+-------+--------------------+------------+
    ```
    {: screen}
	
3. 删除在特定日期存储的日志。

    ```
	bx cf logging delete -s StartDate -e EndDate -t LogType -a
	```
	{: codeblock}
    
    其中
	
	* *-s* 会设置开始日期，格式为全球标准时间 (UTC)：YYYY-MM-DD，例如 2006-01-02。
    * *-e* 会设置结束日期，格式为全球标准时间 (UTC)：YYYY-MM-DD
	* *-t* 会设置日志类型。
    	
	例如，要删除 2017 年 5 月 25 日在帐户级别存储在“日志收集”中且类型为 linux_syslog 的日志，请运行以下命令：
	
	```
	bx cf logging delete -s 2017-05-25 -e 2017-05-25 -t linux_syslog -a
	```
	    {: screen}
	
    







