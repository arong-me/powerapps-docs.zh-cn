---
title: 通过 PowerApps 使用“可编辑网格”自定义控件让模型驱动应用网格（列表）可编辑 | Microsoft Docs
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
ms.openlocfilehash: 704280dbed2177ba9a5467e2897980f78c31b050
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39669295"
---
# <a name="make-model-driven-app-grids-lists-editable-using-the-editable-grid-custom-control"></a>使用“可编辑网格”自定义控件让模型驱动应用网格（列表）可编辑

在旧版 Dynamics CRM 中，用户无法在窗体上的网格（有时也叫列表）或子网格中直接输入数据。 必须选择网格中的记录以打开窗体、编辑并保存数据，步骤繁琐。 无论用户使用的是 Web 应用、平板电脑还是手机，都能利用可编辑网格控件从网格和子网格中直接完成丰富的内联编辑。  
  
 ![可编辑网格示例](media/editable-grid-examples.png "可编辑网格示例")  
  
 通过可编辑网格自定义控件启用可编辑网格后，用户可以编辑大多数类型的字段，包括基本查找字段和选项集。  

**可编辑网格支持以下内容：**
  
-   在实体或子网格级别（包括自定义实体）对记录进行内联编辑  
  
-   系统视图和个人视图  
  
-   Web 和移动客户端  
  
-   使用键盘或鼠标进行导航  
  
-   分组和排序（可以按当前视图中的任何列进行分组/排序）  
  
-   筛选  
  
-   移动列并调整列的尺寸  
  
-   标记页数  
  
-   将更改从一个会话保存至另一个会话，以便对列进行分组、排序、筛选、分页、移动和尺寸调整  
  
-   查找配置  
  
-   计算字段和汇总字段  
  
-   业务规则（显示错误消息、设置字段值、设置必需业务、设置默认值、锁定或解锁字段）  
  
-   JavaScript 事件  
  
-   根据安全角色启用或禁用单元格  
  
-   用户可以继续使用搜索和图表，并能像访问只读网格一样访问操作栏  
  
## <a name="make-main-grids-editable"></a>让主网格可编辑  
  
1.  打开[解决方案资源管理器](advanced-navigation.md#solution-explorer)。  
  
2.  在“实体”列表中打开合适的实体，选择“控件”选项卡并选择“添加控件”。  
  
     ![添加可编辑网格自定义控件](media/add-editable-grids-custom-control.png "Add Editable Grids custom control")  
  
3.  在“添加控件”对话框中选择“可编辑网格”，然后选择“添加”。  
  
4.  在添加的“可编辑网格”行中选择要应用该网格的窗体要素。 这会将所选窗体要素的默认控件设为可编辑网格控件。  
  
     ![可编辑网格行与窗体要素选择](media/editable-grid-row-wit-factor-selection.png "Editable Grid row with form factor selection")    

   > [!NOTE]
   >  在运行时，用户可以在可编辑网格和只读网格之间切换。  
      
5.  若要添加查找，请在“可编辑网格”选项组中选择“添加查找”，然后在“配置属性‘添加查找’”对话框中执行以下操作：  
  
    1.  在“可用视图”列表中选择要添加查找的视图（例如选择“我的活动帐户”）。  
  
    2.  在“可用列”列表中选择要添加的查阅列（例如选择“主要联系人”）。  
  
    3.  在“默认视图”列表中选择查找字段的数据源。  
  
    4.  若要限制显示的记录，请选择“仅显示此类记录”对话框，然后从列表中选择条件并选择“确定”。  
  
         ![在可编辑网格控件中添加查找](media/add-lookup-in-editable-grid-control.png "Add lookup in Editable Grid control")  
     
6.  若有嵌套网格，请选择“嵌套网格视图”的铅笔按钮，然后选择该嵌套网格的实体和视图。 为“嵌套网格父级 ID”选择实体的关系。 例如，ParentAccountID 字段连接“帐户”和“联系人”实体。  
  
    > [!NOTE]
    >  嵌套网格仅适用于手机和平板电脑，不适用于 Web。  
  
7.  若出于希望节省空间等目的，不想让用户在视图中按任何列对数据分组，请在“按列分组”行选择铅笔按钮，然后在“配置属性‘按列分组’”对话框中选择“禁用”并选择“确定”。  
  
    > [!TIP]
    >  此操作主要用于窗体上的子网格。  
  
8.  若想添加 JavaScript 事件，请选择“事件”选项卡，然后选择适当的实体、字段和事件。 详细信息：[开发人员文档：使用可编辑网格](/dynamics365/customer-engagement/developer/customize-dev/use-editable-grids-dynamics-365.md)  
  
     ![在可编辑网格控件中添加事件](media/add-events-in-editable-grid-control.png "Add events in Editable Grid control")  
  
9. 若要保存所做的设置，请选择操作栏上的“保存”。  
  
10. 若已准备好将更改发布至自己的团队，请选择操作栏上的“发布”。  
  
11. 若要测试所做的更改，请转至在步骤 5 中指定的视图，然后通过内联编辑方式进行一些更改。  
  
## <a name="make-a-sub-grid-on-a-form-editable"></a>让窗体上的子网格可编辑

> [!NOTE] 
> - 要在子网格内保存可编辑网格的更改，用户必须在导航出窗体之前进行显式保存。
> - 若正在使用旧版窗体（Dynamics CRM 2016 之前的版本）且在子网格上启用了可编辑网格，则将不会呈现可编辑子网格。 如有需要，系统管理员可以在系统设置中关闭旧版窗体。
  
1.  打开[解决方案资源管理器](advanced-navigation.md#solution-explorer)。  
  
2.  打开包含子网格的窗体。  
  
3.  选择合适的控件，然后选择功能区上的“更改属性”。  
  
4.  在“设置属性”对话框中选择“控件”，再选择“添加控件”，然后按上面列出的步骤操作。  
  
## <a name="supported-standard-entities"></a>支持的标准实体  
  
||||  
|-|-|-|  
|**Web/平板电脑/手机**|**仅平板电脑/手机**|**仅 Web**|  
|帐户<br /><br /> Appointment<br /><br /> 可预订资源<br /><br /> 可预订资源预订<br /><br /> 可预订资源预订标头<br /><br /> 可预订资源类别<br /><br /> 可预订资源类别分配<br /><br /> 可预订资源特征<br /><br /> 可预订资源组<br /><br /> 预订状态<br /><br /> 用例<br /><br /> 类别<br /><br /> 特征<br /><br /> 竞争对手<br /><br /> 联系人<br /><br /> 电子邮件<br /><br /> 授权<br /><br /> 反馈<br /><br /> 发票<br /><br /> 知识文章<br /><br /> 知识文章阅读数<br /><br /> 知识库记录<br /><br /> 潜在客户<br /><br /> 商机<br /><br /> 订单<br /><br /> 电话呼叫<br /><br /> 价格列表<br /><br /> 产品<br /><br /> 队列<br /><br /> 报价<br /><br /> 评分模型<br /><br /> 评分值<br /><br /> SLA KPI 实例<br /><br /> 社交活动<br /><br /> 社交个人资料<br /><br /> 同步错误<br /><br /> 任务<br /><br /> 团队<br /><br /> 用户|活动<br /><br /> 附件<br /><br /> 渠道访问配置文件规则项<br /><br /> 竞争对手地址<br /><br /> 连接<br /><br /> 连接角色<br /><br /> 电子邮件签名<br /><br /> 电子邮件模板<br /><br /> 已过期流程<br /><br /> 发票产品<br /><br /> 知识文章事件<br /><br /> 潜在顾客转化为商机销售<br /><br /> 流程<br /><br /> 邮箱<br /><br /> 新流程<br /><br /> 说明<br /><br /> 商机产品<br /><br /> 商机销售流程<br /><br /> 订单产品<br /><br /> 组织<br /><br /> 电话转化为案例流程<br /><br /> 价格列表项<br /><br /> 队列项<br /><br /> 报价单产品<br /><br /> Sharepoint 文档<br /><br /> 翻译流程|活动<br /><br /> 市场活动<br /><br /> 市场活动反响<br /><br /> 渠道访问配置文件<br /><br /> 渠道访问配置文件规则<br /><br /> 合同<br /><br /> 权利模板<br /><br /> 外部参与方<br /><br /> Fax<br /><br /> Letter<br /><br /> 市场营销列表<br /><br /> 位置<br /><br /> 快速市场活动<br /><br /> 定期约会<br /><br /> 销售宣传资料<br /><br /> SLA|  
 
##  <a name="data-types-that-arent-editable-in-an-editable-grid"></a>可编辑网格中无法编辑的数据类型
可编辑网格中无法编辑以下数据类型：Customer 和 Partylist 查找字段；Composite（地址）字段；State/Status 字段；查找实体相关字段（例如，“帐户”实体包括联系人查找，其中 Contact 字段可编辑，而 EmailAdress(Contact) 字段无法编辑）。  
 
## <a name="next-steps"></a>后续步骤  
 [在可编辑网格中使用键盘快捷方式](https://docs.microsoft.com/dynamics365/customer-engagement/basics/keyboard-shortcuts#editable-grids-views)

