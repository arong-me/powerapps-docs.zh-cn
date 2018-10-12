---
title: 创建模型驱动应用业务规则和建议 | MicrosoftDocs
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
- PowerApps
ms.assetid: 00e62904-2ce9-4730-a113-02b1fedbf22e
caps.latest.revision: 31
author: Mattp123
ms.author: matp
manager: kvivek
tags:
- PowerApps maker portal impact
ms.openlocfilehash: c1a132648a63845c42cde8a80636d0e87e10a328
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39668441"
---
# <a name="tutorial-create-business-rules-and-recommendations-to-apply-logic-in-a-model-driven-app-form"></a>教程：创建业务规则和建议，以在模型驱动应用窗体中应用逻辑

本教程演示如何创建业务规则和建议来应用窗体逻辑，而无需编写 JavaScript 代码或创建插件。业务规则提供简单的界面以实现并维护快速变化且通用的规则。 这些规则可应用于主窗体和快速创建窗体，并且适用于 PowerApps 应用、Dynamics 365 客户参与 Web 应用、适用于平板电脑的 Dynamics 365 和 Dynamics 365 for Outlook（联机或脱机模式）。  
  
 通过组合条件和操作，可以借助业务规则完成下列任何操作：  
  
-   设置字段值  
  
-   清除字段值  
  
-   设置字段要求级别  
  
-   显示或隐藏字段  
  
-   启用或禁用字段  
  
-   验证数据并显示错误信息  
  
-   创建基于商业智能的业务建议。  
  
## <a name="create-a-business-rule-or-business-recommendation"></a>创建业务规则或业务建议
  
1. 打开[解决方案资源管理器](advanced-navigation.md#solution-explorer)。  
  
2.  打开要为其创建业务规则的实体（例如，打开“帐户”实体），然后双击“业务规则”。  
  
 ![在默认解决方案中创建业务规则](media/create-business-rule-the-default-solution.png "Create a business rule in the default solution")  
  
3.  选择“新建”。  
  
     业务规则设计器窗口随即打开，其中有一条已为你创建的条件。 所有规则都是从条件开始的。 基于条件，业务规则采用一个或多个操作。  
  
 ![“业务规则”设计窗口](media/business-rules-design-window.png "Business Rules design window")  
  
   > [!TIP]
> 如果要修改现有业务规则，必须在修改规则之前将其停用。

4.  根据需要，可以在窗口左上角的说明框中添加说明。  
  
5.  根据下表设置范围：  
  
    |||  
    |-|-|  
    |**所选项**|**对应范围**|  
    |**实体**|所有窗体和服务器|  
    |**所有窗体**|所有窗体|  
    |特定窗体（例如“帐户”窗体）|仅该窗体|  
  
6. **添加条件。** 将更多条件添加到业务规则：  
  
    1.  将“条件”组件从“组件”选项卡拖动到设计器中的加号处。  
  
        ![在业务规则中添加条件](media/add-condition-business-rule.png "在业务规则中添加条件")  
  
    2.  要设置条件属性，请在设计器窗口中单击“条件”组件，然后在屏幕右侧的“属性”选项卡上设置属性。 设置属性时，会在“属性”选项卡底部创建一个表达式。  
  
    3.  若要将其他子句（AND 或 OR）添加到条件，请单击“属性”选项卡中的“新建”，创建新规则并为该规则设置属性。 在“规则逻辑”字段中，可以指定是否将新规则添加为 AND 或 OR。  
  
        ![向条件添加新规则](media/add-new-rule-condition.png "向条件添加新规则")  
  
    4.  设置完条件属性后，单击“应用”。  
  
7. **添加操作。** 若要添加操作，请完成以下操作：  
  
    1.  将“组件”选项卡中的一个操作组件拖动到“条件”组件旁边的加号处。 如果希望业务规则在满足条件时执行该操作，请将操作拖动至复选标记旁边的加号处；如果希望规则在不满足条件时执行该操作，请将操作拖动至 x 旁边的加号处。  
  
        ![将操作拖动到业务规则](media/drag-an-action-business-rule.png "")  
  
    2.  要设置操作属性，请在设计器窗口中单击“操作”组件，然后设置“属性”选项卡中的属性。  
  
    3.  设置完属性后，单击“应用”。  
  
8. **添加业务建议**。 添加业务建议：  
  
    1.  将“组件”选项卡中的“建议”组件拖动到“条件”组件旁边的加号处。 如果希望业务规则在满足条件时执行该操作，请将建议组件拖动至复选标记旁边的加号处；如果希望规则在不满足条件时执行该操作，则拖动至 x 旁边的加号处。  
  
    2.  要设置建议属性，请在设计器窗口中单击“建议”组件，然后设置“属性”选项卡中的属性。  
  
    3.  若要向建议添加更多操作，请拖动“组件”选项卡中的操作，并在“属性”选项卡中设置每个操作的属性。  
  
        > [!NOTE]
        >  创建建议时，默认情况下会添加一个操作。 若要查看建议中的所有操作，请单击“建议”组件上的“详细信息”。  
  
    4.  设置完属性后，单击“应用”。  
  
9. 若要验证业务规则，请在操作栏上单击“验证”。  
  
10. 若要保存业务规则，请在操作栏上单击“保存”。  
  
11. 若要激活业务规则，请在“解决方案资源管理器”窗口中选择它，然后单击“激活”。 在设计器窗口中无法激活业务规则。  
  
> [!TIP]
>  在设计器窗口中处理业务规则时，请记住以下提示：  
>   
> - 若要生成业务规则窗口中所有内容的快照，请在操作栏上单击“快照”。 这一点非常有用，例如在你想与团队成员共享业务规则并征求意见时。  
> - 使用 mini-map 快速导航至流程中的不同部分。 这在具备需要滚动屏幕的复杂流程时非常有用。  
> - 在向业务规则添加条件、操作和业务建议时，会生成业务规则的代码，该代码显示在设计器窗口底部。 此代码是只读的。  
  
<a name="BKMK_LocalizingErrorMessages"></a>   
## <a name="localize-error-messages-used-in-business-rules"></a>将业务规则中使用的错误消息本地化  
 如果是多种语言的组织，那么需要将设置的所有错误消息本地化。 每设置一条消息，系统都会生成一个标记。 如果在组织中导出翻译，可以添加消息的本地化版本并将这些标记导回系统，从而让不使用基本语言的人可以查看翻译后的消息。  
  
## <a name="next-steps"></a>后续步骤  
 [通过流程创建业务逻辑](guide-staff-through-common-tasks-processes.md)   
 [创建业务流程](/flow/create-business-process-flow)   

