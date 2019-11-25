---
title: 在 Common Data Service 中创建业务规则 | MicrosoftDocs
description: 如何在 Common Data Service 中创建业务规则的分步说明。
author: lancedMicrosoft
manager: kfile
ms.service: powerapps
ms.component: cds
ms.topic: conceptual
ms.date: 03/21/2018
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 45d0d4ce80d1552ace70ae5b25a67e570141d261
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2019
ms.locfileid: "2754727"
---
# <a name="create-a-business-rule-for-an-entity"></a>创建实体的业务规则

无需编写代码或创建插件，即可创建业务规则和建议以应用逻辑和验证。业务规则可以提供一个简单的界面来实施和维护快速更改和常用的规则。

> [!IMPORTANT]
> 如果在应用程序中使用实体，则为该实体定义的业务规则同时应用于*画布应用程序*和*模型驱动的应用程序*。 目前并非所有业务规则操作在画布应用程序上都可用。 详细信息：[画布应用程序与模型驱动的应用程序之间的区别](#differences-between-canvas-and-model-driven-apps)<br/><br/>
> 若要定义应用于模型驱动的应用程序中的窗体的业务规则，请参阅[创建业务规则以在模型驱动的应用程序窗体中应用逻辑](../model-driven-apps/create-business-rules-recommendations-apply-logic-form.md)。

通过组合条件和操作，可以使用业务规则执行下面的任何操作：  
  
* 设置字段值  
* 清除字段值  
* 设置字段要求级别  
* 显示或隐藏字段  
* 启用或禁用字段  
* 验证数据并显示错误消息  
* 根据业务智能创建业务建议。  
  
## <a name="differences-between-canvas-and-model-driven-apps"></a>画布应用程序与模型驱动的应用程序之间的区别

模型驱动应用程序可以使用业务规则中的所有可用操作，但目前并非所有业务规则操作都对画布应用程序可用。 以下操作**不**在画布应用程序上提供：

* 显示或隐藏字段  
* 启用或禁用字段  
* 根据业务智能创建业务建议。  

## <a name="prerequisites"></a>必备条件 
要遵循本主题的做法，您必须切换到可以创建和编辑实体的[环境](../canvas-apps/working-with-environments.md)。

## <a name="create-a-business-rule"></a>创建业务规则
  
1. 登录到 [PowerApps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)，然后单击或点按左边缘附近的**数据**向下键。

2. 在显示的列表中，单击或点按**实体**。
  
3. 打开要为其创建业务规则的实体（如**客户**实体），然后单击**业务规则**选项卡。  

4. 单击**新建**。  
  
    将打开“业务规则”设计器窗口，其中包含一个已经为您创建的条件。 每个规则都从条件开始。 业务规则根据该条件执行一个或多个操作。  

    > [!TIP]
    > 如果要修改现有业务规则，必须先将其停用，然后才能修改。  
  
5. 如果需要，在窗口左上角的说明框中添加说明。
  
6. 根据需要信息设置范围：  
  
    |||  
    |-|-|  
    |**如果选择此项...**|**范围将设置为...**|  
    |**实体**|模型驱动窗体和服务器|  
    |**所有窗体**|模型驱动窗体|  
    |指定窗体（例如，**客户**窗体）|仅该模型驱动窗体|  

    > [!TIP]
    > 如果您生成画布应用程序，您必须使用实体作为范围。
  
7. **添加条件。** 若要向业务规则添加更多条件：  
  
    1. 将**条件**组件从**组件**选项卡拖到设计器中的加号。  
  
        ![在业务规则中添加条件](./media/data-platform-cds-create-business-rule/add-condition-business-rule.png "在业务规则中添加条件")  
  
    2. 若要设置条件的属性，请单击设计器窗口中的**条件**组件，然后在屏幕右侧的**属性**选项卡中设置属性。 设置属性时，Common Data Service 在**属性**选项卡底部创建一个表达式。  
  
    3. 若要向条件添加更多子句（如 AND 或 OR），请单击**属性**选项卡中的**新建**创建新规则，然后为该规则设置属性。 在**规则逻辑**字段中，可以指定将新规则添加为 AND 还是 OR。  
  
        ![为条件添加新规则](./media/data-platform-cds-create-business-rule/add-new-rule-condition.png "为条件添加新规则")  
  
    4. 为条件设置完属性之后，请单击**应用**。  
  
8. **添加操作。** 若要添加操作：  
  
    1. 将一个操作组件从**组件**选项卡拖到**条件**组件旁边的加号。 如果希望满足添加时业务规则采取操作，请将该操作拖到复选标记旁边的加号，如果希望不满足条件时业务规则采取操作，请拖到 x 旁边的加号。
  
        ![将操作拖放到业务规则](./media/data-platform-cds-create-business-rule/drag-an-action-business-rule.png "将操作拖放到业务规则")  
  
    2. 若要设置操作的属性，请单击设计器窗口中的**操作**组件，然后在**属性**选项卡中设置属性。  
  
    3. 设置完属性之后，请单击**应用**。  
  
9. **添加业务建议。（仅模型驱动）** 若要添加业务建议：  
  
    1. 将**建议**组件从**组件**选项卡拖到**条件**组件旁边的加号。 如果希望满足添加时业务规则采取操作，请将**建议**组件拖到复选标记旁边的加号，如果希望不满足条件时业务规则采取操作，请拖到 x 旁边的加号。  
  
    2. 若要设置建议的属性，请单击设计器窗口中的**建议**组件，然后在**属性**选项卡中设置属性。  
  
    3. 若要向建议添加更多操作，请从**组件**选项卡拖动，然后在**属性**选项卡中为每个操作设置属性。  
  
        > [!NOTE]
        >  创建建议时，Common Data Service 默认添加单个操作。 若要查看某个建议中的所有操作，请单击**建议**组件中的**详细信息**。  
  
    4. 设置完属性之后，请单击**应用**。  
  
10. 若要验证业务规则，请单击操作栏中的**验证**。  
  
11. 若要保存业务规则，请单击操作栏中的**保存**。  
12. 若要激活业务规则，请在“解决方案资源管理器”窗口中将其选中，然后单击**激活**。 不能从设计器窗口激活业务规则。  
  
    > [!TIP]
    >  在设计器窗口中处理业务规则时，请记住下面的一些技巧：  
    >   
    > - 若要抓取“业务规则窗口”中所有内容的屏幕截图，请单击操作栏中的**屏幕截图**。 这非常有用，例如，如果要共享和获取团队成员有关业务规则的注释。  
    > - 使用迷你地图快速导航到流程的其他部分。 您有超出屏幕的复杂流程时，这非常有用。  
    > - 向业务规则添加条件、操作和业务建议时，Common Data Service 在设计器窗口底部为业务规则构建代码。 此代码是只读的。  
  
## <a name="localize-error-messages-used-in-business-rules"></a>本地化业务规则中使用的错误消息  
 如果为组织配置了多种语言，则需要将设置的错误消息本地化。 每次设置消息时，系统会生成一个标签。 如果您导出组织中的翻译，就可以添加消息的本地化版本，然后将这些标签重新导入到 Common Data Service 中，从而使使用非基本语言的用户可以查看经过翻译的消息。  
  
