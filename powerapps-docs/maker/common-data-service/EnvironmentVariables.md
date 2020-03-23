---
title: 预览：在解决方案中使用环境变量 | MicrosoftDocs
description: 使用环境变量在解决方案中迁移应用程序配置数据。
Keywords: 环境变量, 变量, 模型驱动应用, 配置数据
author: caburk
ms.author: caburk
manager: kvivek
ms.date: 02/10/2020
ms.service: powerapps
ms.topic: article
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 1426bd729c07387a025965feba5398393d425795
ms.sourcegitcommit: 80120b59d440bb7a3ddca93cd51154607f749f6b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "3036427"
---
# <a name="preview-environment-variables-overview"></a>预览：环境变量概述 

[!INCLUDE[cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

应用和流通常在各个环境中需要不同的配置设置。 与自定义内或使用其他工具的硬编码值相比，作为可配置输入参数的环境变量允许单独管理数据。 由于它们是解决方案组件，因此性能比将配置数据作为记录数据导入要好得多。

使用环境变量的好处：
- 无需在生产环境中手动编辑可配置的值。
- 在一个位置配置一个或多个变量，并像跨多个解决方案组件的参数一样进行引用。
- 更新值而无需更改代码。
- 由 [Common Data Service](https://docs.microsoft.com/powerapps/maker/common-data-service/data-platform-intro)管理的粒度级别安全性。
- 无限制数量的变量（最大解决方案大小为 29 MB）。
- 单独或一起服务处理定义和值。
- 由 [SolutionPackager](/powerapps/developer/common-data-service/compress-extract-solution-file-solutionpackager) 和 [DevOps](/powerapps/developer/common-data-service/build-tools-overview) 工具支持，可实现持续集成和持续交付 (CI/CD)。
- 支持本地化。
- 可用于控制功能标志和其他应用程序设置。

> [!IMPORTANT]
> - 这是一项预览功能。
> - [!INCLUDE[cc_preview_features_definition](../../includes/cc-preview-features-definition.md)] 

## <a name="how-do-they-work"></a>它们如何工作？
环境变量可以通过现代解决方案接口或[使用代码](https://docs.microsoft.com/powerapps/developer/common-data-service/work-with-data-cds)创建和管理。 在解决方案包中将为这些值创建一个单独的 JSON 文件，此文件可以在源代码管理中进行管理，并在生成管道中进行修改。 支持导出到 Excel 和从 Excel 导入。 创建环境变量之后，可以将它们用作插件、流和其他组件中的输入。 

### <a name="create-an-environment-variable-in-power-apps"></a>在 Power Apps 中创建环境变量
1. 登录到 Power Apps，然后在左窗格中选择**解决方案**。 
2. 在命令栏上，选择**新建**，然后选择**环境变量**。 
3. 在左侧窗格中，完成以下字段，然后选择**保存**：  
   - **显示名称**。 输入环境变量的名称。 
   - **名称**. 唯一名称会自动从**显示名称**生成，但您可以更改它。 
   - **数据类型**。 从**十进制数**、**文本**、**JSON** 或**两个选项**字段中进行选择。 
   - **默认值**。 此字段是环境变量定义实体的一部分，不是必需的。 为生产环境或在不同环境下不需要更改值时设置默认值。 
   - **当前值**。 也称为替代值。 此字段是可选的，是环境变量值实体的一部分。 当您想要替代当前环境中的默认值时，请设置该值。 如果您不想在下一个环境中使用它，请从解决方案中删除该值。 这些值也被分隔到导出的 solution.zip 文件中的单独的 JSON 文件中。 

      利用默认值和当前值的分隔，您可以将定义和默认值与当前值分开提供服务。 它还使我们将来可以扩展功能，以支持划定给特定运行时上下文的多个值。

      >[!NOTE]
      > 没有定义值就不会存在。 接口仅允许为每个定义创建一个值。 

## <a name="notifications"></a>通知
当环境变量没有任何值时，将显示一条通知。 目的是提醒您设置值，以使依赖于变量的组件不会失败。 它还允许合作伙伴传送没有值的变量，并提示客户输入值。

>[!NOTE]
> 我们建议合作伙伴建立自己的接口，并要求客户提供值。 如果跳过此步骤，通知将有助于防止失败。 

## <a name="security"></a>安全性
environmentvariabledefinition 和 environmentvariablevalue 实体都是由[用户或团队负责](https://docs.microsoft.com/powerapps/maker/common-data-service/types-of-entities)。 创建使用环境变量的应用程序时，请确保为用户分配适当的权限级别。 详细信息：[Common Data Service 中的安全性](https://docs.microsoft.com/power-platform/admin/wp-security)。 

## <a name="current-limitations"></a>当前限制
- 缓存。 插件将需要运行查询以获取值。 
- 画布应用和流可以使用环境变量，就像实体记录数据一样。 <!-- In the future we plan to build additional actions into canvas app and flow designers. This will simplify authoring and provide better visibility into environment variables being used by a specific app or flow. -->
- 用于密钥管理的 Azure Key Vault 集成。 当前环境变量不应用于存储安全数据，如密码和密钥。
- 数据类型仅在现代解决方案接口中验证，但当前在预览期间不在服务器上验证。 
- 某些组件类型不强制使用依赖项。
- 如果使用 Excel 导入环境变量，请确保将发布者前缀放在 SchemaName 之前。

### <a name="see-also"></a>另请参阅
[Power Apps 博客：环境变量已经提供预览！](https://powerapps.microsoft.com/blog/environment-variables-available-in-preview/)
[使用插件扩展业务流程](https://docs.microsoft.com/powerapps/developer/common-data-service/plug-ins) </BR>
[Web API 示例](https://docs.microsoft.com/powerapps/developer/common-data-service/webapi/web-api-samples) </BR>
[使用 Common Data Service 从头开始创建画布应用。](https://docs.microsoft.com/powerapps/maker/canvas-apps/data-platform-create-app-scratch) </BR>
[使用 Common Data Service 创建流](https://docs.microsoft.com/flow/connection-cds)
