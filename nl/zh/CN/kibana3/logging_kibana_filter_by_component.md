---

copyright:
  years: 2015, 2018

lastupdated: "2018-01-10"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# 在 Kibana 中按日志类型过滤 Cloud Foundry 应用程序日志
{: #logging_kibana_component_filter}

在 Kibana 仪表板上按组件（日志类型）查看和过滤 {{site.data.keyword.Bluemix_notm}} 应用程序日志。可以从 Cloud Foundry 应用程序的**日志**选项卡访问 Kibana 仪表板。
{:shortdesc}

要在 Kibana 仪表板上按日志类型查看和过滤 Cloud Foundry 应用程序日志，请完成以下任务：

1. 访问 Cloud Foundry 应用程序的**日志**选项卡。 

    1. 单击 {{site.data.keyword.Bluemix_notm}} **应用程序**仪表板上的应用程序名称。
    2. 单击**日志**选项卡。 
    
    这将显示应用程序的日志。

2. 访问应用程序的 Kibana 仪表板。单击**高级视图** ![“高级视图”链接](images/logging_advanced_view.jpg "“高级视图”链接")。这将显示 Kibana 仪表板。

3. 在**所有事件**窗口中，单击向右箭头图标以显示所有字段。 

    ![具有向右箭头图标的“所有事件”窗口](images/logging_all_events_no_fields.jpg "具有向右箭头图标的“所有事件”窗口")

4. 在**字段**窗格中，选择 **source_id** 以显示**所有事件**窗口中生成每个日志条目的组件。

    ![选择了 source_id 字段的“所有事件”窗口](images/logging_component.png "选择了 source_id 字段的“所有事件”窗口")

5. 在**所有事件**窗口中，单击日志事件行以显示该事件的详细信息。选择显示您要过滤的 source_id 的事件。

    ![显示所选日志事件详细信息的“所有事件”窗口](images/logging_component_add_filter.png "显示所选日志事件详细信息的“所有事件”窗口")

6. 添加过滤器以包含或排除组件（日志类型）的信息。 

    * 要添加包含组件值的过滤器，请单击表 source_id 行中的**放大镜** ![“放大镜”图标](images/logging_magnifying_glass.jpg "“放大镜”图标") 图标。 

        ![source_id 字段的过滤条件](images/logging_component_filter.png "source_id 字段的过滤条件") 

    * 要添加排除组件值的过滤器，请单击表 source_id 行中的**排除** ![“排除”图标](images/logging_exclusion_icon.png "“排除”图标") 图标。 
    
         ![排除 source_id 字段的过滤条件](images/logging_component_add_exclusion_filter.png "排除 source_id 字段的过滤条件") 
     
     这将向 Kibana 仪表板添加新过滤条件。

7. 您可以选择性地重复之前的步骤并为每个组件添加过滤器。要查看组件的完整列表，请参阅[日志格式](../logging_view_kibana3.html#kibana_log_format_cf)。

    下图显示具有不同组件的多个过滤器的仪表板：
    
    ![source_id 字段的多个过滤条件](images/logging_component_multiple_filters.png "source_id 字段的多个过滤条件")

8. 保存仪表板。 

    当您完成添加过滤器并定制仪表板后，单击**保存**图标 ![“保存”图标](images/logging_save.jpg "“保存”图标") 并输入仪表板的名称。 
      
    **注：**如果尝试使用包含空格的名称来保存仪表板，那么不会保存该仪表板。请输入不带空格的名称并单击**保存**图标。
    
    ![保存仪表板名称](images/logging_save_dashboard.jpg "保存仪表板名称")

您已创建了按组件（日志类型）过滤日志条目的仪表板。您可以通过单击**文件夹**图标 ![“文件夹”图标](images/logging_folder.jpg "“文件夹”图标") 并按名称选择仪表板，随时装入已保存的仪表板。


