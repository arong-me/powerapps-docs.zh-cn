---
title: 创建模型驱动应用程序的业务规则和建议 | MicrosoftDocs
ms.custom: ''
ms.date: 03/15/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - PowerApps
ms.assetid: 00e62904-2ce9-4730-a113-02b1fedbf22e
caps.latest.revision: 31
author: Mattp123
ms.author: matp
manager: kvivek
tags:
  - PowerApps maker portal impact
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="create-business-rules-and-recommendations-to-apply-logic-in-a-model-driven-app-form"></a>创建业务规则和建议以在模型驱动应用程序窗体中应用逻辑

本主题向您介绍无需编写 JavaScript 代码或创建插件，如何创建业务规则和建议以在模型驱动的应用程序中应用窗体逻辑。业务规则可以提供一个简单的界面来实施和维护快速更改和常用的规则。 它们可以应用于“主”窗体和“快速创建”窗体，并可以在模型驱动应用、Dynamics 365 customer engagement Web 应用、Dynamics 365 for tablets 和 Dynamics 365 for Outlook（在线或脱机模式）中工作。

> [!NOTE]
> 若要为实体定义业务规则，以使其适用于所有窗体和服务器，请参阅[为实体创建业务规则](/powerapps/maker/common-data-service/data-platform-create-business-rule)。
  
 通过组合条件和操作，可以使用业务规则执行下面的任何操作：  
  
-   设置字段值  
  
-   清除字段值  
  
-   设置字段要求级别  
  
-   显示或隐藏字段  
  
-   启用或禁用字段  
  
-   验证数据并显示错误消息  
  
-   根据业务智能创建业务建议。  
  
## <a name="create-a-business-rule-or-business-recommendation"></a>创建业务规则或业务建议
  
1. 打开[解决方案资源管理器](advanced-navigation.md#solution-explorer)。  
  
2.  打开要为其创建业务规则的实体（如**客户**实体），然后双击**业务规则**。  
  
 ![在默认解决方案中创建业务规则](media/create-business-rule-the-default-solution.png "在默认解决方案中创建业务规则")  
  
3.  选择**新建**。  
  
     将打开“业务规则”设计器窗口，其中包含一个已经为您创建的条件。 每个规则都从条件开始。 业务规则根据该条件执行一个或多个操作。  
  
 ![业务规则设计窗口](media/business-rules-design-window.png "业务规则设计窗口")  
  
   > [!TIP]
> 如果要修改现有业务规则，必须先将其停用，然后才能修改。

4.  如果需要，在窗口左上角的说明框中添加说明。  
  
5.  根据需要信息设置范围：  
  
    |||  
    |-|-|  
    |**如果选择此项...**|**范围将设置为...**|  
    |**实体**|所有窗体和服务器|  
    |**所有窗体**|所有窗体|  
    |指定窗体（例如，**客户**窗体）|仅该表单|  
  
6. **添加条件。** 若要向业务规则添加更多条件：  
  
    1.  将**条件**组件从**组件**选项卡拖到设计器中的加号。  
  
        ![在业务规则中添加条件](media/add-condition-business-rule.png "在业务规则中添加条件")  
  
    2.  若要设置条件的属性，请单击设计器窗口中的**条件**组件，然后在屏幕右侧的**属性**选项卡中设置属性。 设置属性时，在**属性**选项卡底部创建一个表达式。  
  
    3.  若要向条件添加更多子句（如 AND 或 OR），请单击**属性**选项卡中的**新建**创建新规则，然后为该规则设置属性。 在**规则逻辑**字段中，可以指定将新规则添加为 AND 还是 OR。  
  
        ![向条件添加新规则](media/add-new-rule-condition.png "向条件添加新规则")  
  
    4.  为条件设置完属性之后，请单击**应用**。  
  
7. **添加操作。** 若要添加操作：  
  
    1.  将一个操作组件从**组件**选项卡拖到**条件**组件旁边的加号。 如果希望满足添加时业务规则采取操作，请将该操作拖到复选标记旁边的加号，如果希望不满足条件时业务规则采取操作，请拖到 x 旁边的加号。  
  
        ![将操作拖到业务规则](media/drag-an-action-business-rule.png "将操作拖到业务规则")  
  
    2.  若要设置操作的属性，请单击设计器窗口中的**操作**组件，然后在**属性**选项卡中设置属性。  
  
    3.  设置完属性之后，请单击**应用**。  
  
8. **添加业务建议。** 若要添加业务建议：  
  
    1.  将**建议**组件从**组件**选项卡拖到**条件**组件旁边的加号。 如果希望满足添加时业务规则采取操作，请将**建议**组件拖到复选标记旁边的加号，如果希望不满足条件时业务规则采取操作，请拖到 x 旁边的加号。  
  
    2.  若要设置建议的属性，请单击设计器窗口中的**建议**组件，然后在**属性**选项卡中设置属性。  
  
    3.  若要向建议添加更多操作，请从**组件**选项卡拖动，然后在**属性**选项卡中为每个操作设置属性。  
  
        > [!NOTE]
        >  创建建议时，默认添加单个操作。 若要查看某个建议中的所有操作，请单击**建议**组件中的**详细信息**。  
  
    4.  设置完属性之后，请单击**应用**。  
  
9. 若要验证业务规则，请单击操作栏中的**验证**。  
  
10. 若要保存业务规则，请单击操作栏中的**保存**。  
  
11. 若要激活业务规则，请在“解决方案资源管理器”窗口中将其选中，然后单击**激活**。 不能从设计器窗口激活业务规则。  
  
> [!TIP]
>  在设计器窗口中处理业务规则时，请记住下面的一些技巧：  
>   
> - 若要抓取“业务规则窗口”中所有内容的屏幕截图，请单击操作栏中的**屏幕截图**。 这非常有用，例如，如果要共享和获取团队成员有关业务规则的注释。  
> - 使用迷你地图快速导航到流程的其他部分。 您有超出屏幕的复杂流程时，这非常有用。  
> - 向业务规则添加条件、操作和业务建议时，为业务规则构建代码并显示在设计器窗口底部。 该代码为只读代码。  
  
<a name="BKMK_LocalizingErrorMessages"></a>   
## <a name="localize-error-messages-used-in-business-rules"></a>本地化业务规则中使用的错误消息  
 如果为组织配置了多种语言，则需要将设置的错误消息本地化。 每次设置消息时，系统会生成一个标签。 如果您导出组织中的翻译，就可以添加消息的本地化版本，然后将这些标签重新导入到系统中，从而使使用非基本语言的用户可以查看经过翻译的消息。  

## <a name="common-issues"></a>常见问题
本部分介绍了在使用业务规则时可能出现的常见问题。 

### <a name="full-name-field-not-supported-with-unified-interface-apps"></a>统一接口应用程序不支持“全名”字段
使用**全名** (fullname) 字段的操作或条件在基于统一接口的应用程序中不受支持。  或者，可以使用具有**名** (firstname) 和**姓** (lastname) 字段的操作或条件。 

### <a name="is-your-business-rule-not-firing-for-a-form"></a>您的业务规则是否不响应窗体？
由于窗体中不包含业务规则内应用的字段，所以可能不执行业务规则。 
1.  打开解决方案资源管理器。 展开所需实体，然后选择**窗体**。 
2.  打开所需窗体，然后在窗体设计器功能区上选择**业务规则**。 
3.  在窗体设计器中，打开业务规则。 
4.  在业务规则设计器中，选择每个条件和操作以验证每个条件和操作中引用的所有字段。 

     > [!div class="mx-imgBorder"] 
     > ![](media/business-rule-field.png "实体中存在业务规则内引用的字段")

 5. 验证窗体中是否也包含业务规则内引用的每个字段。 如果不包含，则将缺少的字段添加到窗体。

     > [!div class="mx-imgBorder"] 
     > ![](media/account-name-on-form.png "窗体中的客户名称字段")

## <a name="frequently-asked-questions-faq"></a>常见问题 (FAQ)
*业务规则能否解锁只读窗体上的字段？*
- 可以，业务规则可以解锁只读窗体上的字段，并可以编辑只读窗体上的操作。

*如何排查不工作的业务规则的问题？* 
- 请参阅本主题中的[您的业务规则是否不响应窗体？](#is-your-business-rule-not-firing-for-a-form)。

## <a name="see-also"></a>另请参阅  
 [通过流程创建自定义业务逻辑](guide-staff-through-common-tasks-processes.md)   
 [创建业务流程](/flow/create-business-process-flow)   

