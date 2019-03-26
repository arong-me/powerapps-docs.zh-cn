---
title: 通过 PowerApps 使用可编辑网格自定义控件将模型驱动应用程序网格（列表）设置为可编辑 | MicrosoftDocs
description: 了解如何使用可编辑网格自定义控件
ms.custom: ''
ms.date: 06/27/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
ms.assetid: cefbc0c2-769b-4230-ab5a-b28a84630a42
caps.latest.revision: 8
author: Mattp123
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="make-model-driven-app-grids-lists-editable-using-the-editable-grid-custom-control"></a>使用可编辑网格自定义控件将模型驱动应用程序网格（列表）设置为可编辑

在 Dynamics CRM 早期版本中，用户不能直接在窗体上的网格（有时称为列表）或子网格中输入数据。 他们必须选择网格中的记录打开窗体，编辑数据，然后保存，这样就需要多个步骤。 通过可编辑网格，无论用户在使用 Web 应用、平板电脑还是手机，都可以直接从网格和子网格执行丰富的内嵌编辑。  
  
 ![可编辑网格示例](media/editable-grid-examples.png "可编辑网格示例")  
  
 通过“可编辑网格”自定义控件启用了可编辑网格之后，用户可以编辑大多数类型的字段，包括基本的查找字段和选项集。  

**可编辑网格支持：**
  
-   对记录执行实体或子网格级别（包括自定义实体）内嵌编辑  
  
-   系统视图和个人视图  
  
-   Web 和移动客户端  
  
-   通过键盘或鼠标导航  
  
-   分组和排序（可以按当前视图中的任何列分组/排序）  
  
-   筛选  
  
-   移动列和调整列大小  
  
-   分页  
  
-   将更改从一个会话保存到另一个会话以对列执行分组、排序、筛选、分页、移动和调整大小  
  
-   查找配置  
  
-   计算字段和汇总字段  
  
-   业务规则（显示错误消息、设置字段值，设置所需业务，设置默认值、锁定或解锁字段）  
  
-   JavaScript 事件  
  
-   根据安全角色启用或禁用单元格  
  
-   用户可继续使用搜索和图表，还可以将操作栏作为只读网格访问  
  
## <a name="make-main-grids-editable"></a>将主网格设置为可编辑  
  
1.  打开[解决方案资源管理器](advanced-navigation.md#solution-explorer)。  
  
2.  在**实体**列表中，打开相应实体，选择**控件**选项卡，然后选择**添加控件**。  
  
     ![添加可编辑网格自定义控件](media/add-editable-grids-custom-control.png "添加可编辑网格自定义控件")  
  
3.  在**添加控件**对话框中，选择**可编辑网格**，然后选择**添加**。  
  
4.  在添加的**可编辑网格**行中，选择要为其应用该网格的外形规格。 这样将把这个可编辑网格控件设置为所选外形规格的默认控件。  
  
     ![带窗体元素选项的可编辑网格行](media/editable-grid-row-wit-factor-selection.png "带窗体元素选项的可编辑网格行")    

   > [!NOTE]
   >  用户可以在运行时，在可编辑网格和只读网格之间切换。  
      
5.  若要添加查找，请在**可编辑网格**选项组中选择**添加查找**，然后在**配置属性‘添加查找’** 对话框中：  
  
    1.  在**可用视图**列表中，选择要为其添加查找的视图（例如，选择**我的有效客户**）。  
  
    2.  在**可用列**列表中，选择要添加的查找列（例如，选择**主要联系人**）。  
  
    3.  在**默认视图**列表中，选择查找字段的数据源。  
  
    4.  如果要限制显示的记录，请选中**仅在以下情况下显示记录**复选框，从列表中选择条件，然后选择**确定**。  
  
         ![在可编辑网格控件中添加查找](media/add-lookup-in-editable-grid-control.png "在可编辑网格控件中添加查找")  
     
6.  如果有嵌套网格，请选择**嵌套网格视图**的铅笔按钮，然后选择嵌套网格的实体和视图。 对于**嵌套网格父 ID**，请选择实体的关系。 例如，ParentAccountID 字段连接**客户**和**联系人**实体。  
  
    > [!NOTE]
    >  嵌套网格仅对手机和平板电脑可用，对 Web 不可用。  
  
7.  如果不希望允许用户按视图中的任何列为数据分组（例如，为了节约空间），请在**按列分组**行中，选择铅笔按钮，然后在**配置属性‘按列分组’** 对话框中，选择**禁用**，然后选择**确定**。  
  
    > [!TIP]
    >  这对窗体中的子网格最有用。  
  
8.  如果要添加 JavaScript 事件，请选择**事件**选项卡，然后选择相应的实体、字段和事件。 详细信息：[开发人员文档：使用可编辑网格](/dynamics365/customer-engagement/developer/customize-dev/use-editable-grids-dynamics-365.md)  
  
     ![在可编辑网格控件中添加事件](media/add-events-in-editable-grid-control.png "在可编辑网格控件中添加事件")  
  
9. 若要保存工作，请选择操作栏中的**保存**。  
  
10. 准备好将更改提供给团队时，请选择操作栏中的**发布**。  
  
11. 若要测试更改，请转到您在步骤 5 中指定的视图，然后执行一些内嵌编辑更改。  
  
## <a name="make-a-sub-grid-on-a-form-editable"></a>将窗体中的子网格设置为可编辑

> [!NOTE] 
> - 若要保存子网格内执行的可编辑网格更改，必须在离开窗体前明确保存。
> - 如果您使用的是旧窗体（Dynamics CRM 2016 之前的版本）并在子网格上启用可编辑网格，将不会呈现可编辑子网格。 如果需要，系统管理员可在系统设置中关闭旧窗体。
  
1.  打开[解决方案资源管理器](advanced-navigation.md#solution-explorer)。  
  
2.  打开包含该子网格的窗体。  
  
3.  选择相应控件，然后选择功能区中的**更改属性**。  
  
4.  在**设置属性**对话框中，选择**控件**，选择**添加控件**，然后执行上面列出的相同步骤。  
  
## <a name="supported-standard-entities"></a>支持的标准实体  
  
||||  
|-|-|-|  
|**Web/平板电脑/手机**|**仅平板电脑/手机**|**仅 Web**|  
|客户<br /><br /> 约会<br /><br /> 可预订的资源<br /><br /> 可预订资源的预订<br /><br /> 可预订资源的预订标题<br /><br /> 可预订资源的类别<br /><br /> 可预订资源的类别 Assn<br /><br /> 可预订资源的特征<br /><br /> 可预订资源组<br /><br /> 预订状态<br /><br /> 案例<br /><br /> 类别<br /><br /> 特征<br /><br /> 竞争对手<br /><br /> 联系人<br /><br /> 电子邮件<br /><br /> 权利<br /><br /> 反馈<br /><br /> 发票<br /><br /> 知识文章<br /><br /> 知识文章视图<br /><br /> 知识库记录<br /><br /> 潜在顾客<br /><br /> 商机<br /><br /> 订单<br /><br /> 电话联络<br /><br /> 价目表<br /><br /> 产品<br /><br /> 队列<br /><br /> 报价单<br /><br /> 评分模型<br /><br /> 评分值<br /><br /> SLA KPI 实例<br /><br /> 社交活动<br /><br /> 社区个人资料<br /><br /> 同步错误<br /><br /> 任务<br /><br /> 团队<br /><br /> 用户|活动<br /><br /> 附件<br /><br /> 渠道访问配置文件规则项<br /><br /> 竞争对手地址<br /><br /> 连接<br /><br /> 连接角色<br /><br /> 电子邮件签名<br /><br /> 电子邮件模板<br /><br /> 已过期流程<br /><br /> 发票产品<br /><br /> 知识文章事件<br /><br /> 潜在顾客转化为商机销售<br /><br /> 进程<br /><br /> 邮箱<br /><br /> 新流程<br /><br /> 注释<br /><br /> 商机产品<br /><br /> 商机销售流程<br /><br /> 订单产品<br /><br /> 组织<br /><br /> 电话转化为案例流程<br /><br /> 价目表项<br /><br /> 队列项<br /><br /> 报价单产品<br /><br /> Sharepoint 文档<br /><br /> 翻译流程|市场活动<br /><br /> 市场活动项目<br /><br /> 市场活动响应<br /><br /> 渠道访问配置文件<br /><br /> 渠道访问配置文件规则<br /><br /> 合同<br /><br /> 权利模板<br /><br /> 外部参与方<br /><br /> 传真<br /><br /> 信件<br /><br /> 市场营销列表<br /><br /> 位置<br /><br /> 快速市场活动<br /><br /> 定期约会<br /><br /> 销售宣传资料<br /><br /> SLA|  
 
##  <a name="data-types-that-arent-editable-in-an-editable-grid"></a>可编辑网格中不可编辑的数据类型
以下数据类型在可编辑网格中不可编辑：客户和 Partylist 查找字段、复合（地址）字段、状态字段、与查找实体有关的字段（如客户实体包含联系人查找，其中的联系人字段可编辑，但是 EmailAddress(Contact) 字段不可编辑）。  
 
## <a name="next-steps"></a>后续步骤  
 [在可编辑网格中使用键盘快捷方式](https://docs.microsoft.com/dynamics365/customer-engagement/basics/keyboard-shortcuts#editable-grids-views)

