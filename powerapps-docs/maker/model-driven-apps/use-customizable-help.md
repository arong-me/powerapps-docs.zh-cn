---
title: 启用和使用可自定义帮助（模型驱动应用）| MicrosoftDocs
description: ''
keywords: ''
ms.date: 10/22/2019
ms.service: powerapps
ms.topic: article
author: Mattp123
ms.author: matp
manager: kvivek
topic-status: Drafting
search.audienceType:
- customizer
search.app:
- PowerApps
ms.openlocfilehash: 3e6b593a30044c6a2c8cfc3e4867cb18156208f5
ms.sourcegitcommit: 7411b4cf9e30e71052fe932dfd3276e969854af4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/06/2019
ms.locfileid: "2768397"
---
# <a name="enable-and-use-customizable-help"></a>启用和使用可自定义帮助
可自定义帮助使您可以为填写表单的模型驱动应用用户提供您自己的上下文信息。 

> [!NOTE]
> 您可以使用自定义帮助窗格和向导型任务来创作为统一接口应用程序提供针对组织定制的自定义产品内帮助体验的帮助，而不用创建和维护自己的帮助系统。 详细信息：[为您的统一接口应用创建引导式帮助](../common-data-service/create-custom-help-pages.md)

使用模型驱动应用，您可以在全局（环境）级别或实体级别使用您选择的自定义帮助来替换您的默认帮助。 自定义帮助可以使通过帮助链接公开的内容与您的自定义或可自定义实体更相关。 针对所有自定义实体，您可以使用单一、全局的 URL 来替代现成的帮助链接。 针对特定的自定义实体，每个实体的 URL 在网格和窗体上替代现成的帮助链接。 您可以在 URL 中包含其他参数，如语言代码和实体名称。 这些参数允许开发人员添加功能以将用户重定向到页面，该页面与应用程序中其语言或实体上下文相关。 实体级别自定义帮助设置可识别解决方案，因此您可以在解决方案中将他们打包为解决方案的一部分，并在环境之间对其进行传输或在解决方案中进行分发。 

## <a name="set-up-customizable-help"></a>设置自定义帮助
可以在全局和实体级别设置可自定义帮助。 

### <a name="set-customizable-help-at-the-global-level"></a>在全局级别设置可自定义帮助
具有系统管理员安全角色的人员可以使用这些设置来替代全局级别的默认帮助。 
1. 打开模型驱动应用，然后在命令栏上，选择**设置** ![设置](../model-driven-apps/media/powerapps-gear.png) > **高级设置**。
2. 转到**设置** > **管理**。
3. 选择**系统设置**，然后选择**常规**选项卡。 
4. 在**设置自定义帮助 URL** 下，选择并定义以下可自定义帮助的全局设置： 
     - **使用可自定义实体的自定义帮助**。 选择以启用。  
     - **全局自定义帮助 URL**。 输入自定义帮助的 URL。 
     - **将参数追加到 URL**。 选择**是**以允许将语言代码或实体名称等参数追加到您在实体定义中指定的**帮助 URL** 中。 详细信息：[将参数追加到 URL](#append-parameters-to-url)  

    > [!div class="mx-imgBorder"] 
    > ![可自定义帮助的全局设置](media/customizable-help-global-setting.png)

5. 选择**确定**。

### <a name="set-customizable-help-for-a-specific-entity"></a>为特定实体设置可自定义帮助
在全局级别启用自定义帮助后，系统定制员可以在实体定义中替代实体的全局帮助 URL。 

1. 打开解决方案资源管理器。
2. 展开**实体**，然后选择所需的实体。 
3. 在实体定义的**帮助**部分下的**常规**选项卡上，在**帮助 URL** 框中，输入自定义帮助页面的 URL。 

    > [!div class="mx-imgBorder"] 
    > ![可自定义帮助的实体设置](media/customizable-help-entity-setting.png)

#### <a name="append-parameters-to-url"></a>将参数追加到 URL
如前所述，要允许将参数追加到实体定义的**帮助 URL** 中，请在**系统设置** > **常规**选项卡中将**将参数追加到 URL** 设置为**是**。 

可以附加到 URL 的参数的示例：

- 用户语言代码：userlcid
- 实体名称：实体
- 入口点：层次结构图表或窗体
- 窗体 Id：formid

