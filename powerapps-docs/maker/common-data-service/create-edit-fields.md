---
title: 如何创建和编辑 Common Data Service 的字段 | MicrosoftDocs
ms.custom: ''
ms.date: 02/08/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- PowerApps
ms.assetid: d88677fa-2caf-47b0-aec6-10a25a7ec9c3
caps.latest.revision: 55
ms.author: matp
manager: kvivek
author: Mattp123
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: fd5d17f33490aab049a166fa53ce541bdea2235a
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2019
ms.locfileid: "2757916"
---
# <a name="how-to-create-and-edit-fields"></a>如何创建和编辑字段

在 Common Data Service 中，字段定义可用于存储实体中数据的个别数据项。 开发人员有时也将字段称为*属性*。 
  
在创建自定义字段之前，应评估使用现有字段是否满足您的要求。 详细信息：[新建元数据或使用现有元数据？](create-edit-metadata.md#create-new-metadata-or-use-existing-metadata)

有两个设计器可以用来创建或编辑字段：

|设计器| 说明|
|--|--|
|[PowerApps 门户](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)|提供简单的简化体验，但是有些特殊设置不可用。<br />详细信息：[使用 PowerApps 门户创建和编辑 Common Data Service 的字段](create-edit-field-portal.md)|
|解决方案资源管理器|不那么简单，但提供更多灵活性可减少常见要求。<br />详细信息：[使用 PowerApps 解决方案资源管理器创建和编辑 Common Data Service 的字段](create-edit-field-solution-explorer.md) |

> [!NOTE]
> 您还可以使用以下方法在您的环境中创建字段：
> - 在模型驱动应用程序中，从窗体编辑器中选择**新建字段**。
> - 导入包含字段定义的解决方案。
> - 使用 Power Query 创建新实体并使用数据填充它们。<br />详细信息：[使用 Power Query 将数据添加到 Common Data Service 中的实体](/powerapps/maker/common-data-service/data-platform-cds-newentity-pq)。
> - 开发人员可以使用[元数据服务](/powerapps/developer/common-data-service/use-web-services#metadata-services)编写程序来创建和更新字段。

本主题中的信息将帮助您选择可以使用的设计器。 

您应该使用 PowerApps 门户创建和编辑 Common Data Service 的字段，除非您需要满足下列要求中的任何一个：

- 创建客户查找字段。 
   - 详细信息：[不同的查找类型](types-of-fields.md#different-types-of-lookups)
- 在 Common Data Service 默认解决方案以外的解决方案中创建字段。 
   - 详细信息：[解决方案概述](solutions-overview.md)
- 定义状态描述转换。 
   - 详细信息：[为案例或自定义实体定义状态描述转换](define-status-reason-transitions.md)
- 一次编辑多个字段。
- 启用审核。 
   - 详细信息：[审核概述](../../developer/common-data-service/auditing-overview.md)
- 启用字段级安全性。 
   - 详细信息：[字段安全性实体](../../developer/common-data-service/field-security-entities.md)
- 选择字段是否显示在交互式体验的全局筛选器中。 
   - 详细信息：[配置模型驱动应用交互式体验仪表板](../model-driven-apps/configure-interactive-experience-dashboards.md)
- 选择字段是否可在交互式体验仪表板中排序。 
   - 详细信息：[配置模型驱动应用交互式体验仪表板](../model-driven-apps/configure-interactive-experience-dashboards.md)
- 将字段需求级别设置为“业务建议”。 
   - 详细信息：[创建业务规则和建议以在模型驱动应用程序窗体中应用逻辑](../model-driven-apps/create-business-rules-recommendations-apply-logic-form.md)
- 设置字段的托管属性。 
   - 详细信息：[设置字段的托管属性](set-managed-properties-for-field.md)

> [!NOTE]
> 您可以在 PowerApps 门户或解决方案资源管理器中通过在实体上创建一对多关系来创建“查找”字段。 但是仅解决方案资源管理器在创建字段时提供创建此关系的选项。

## <a name="community-tools"></a>社区工具

**[Attribute Manager](https://www.xrmtoolbox.com/plugins/DLaB.Xrm.AttributeManager/)** 是一款 XrmToolbox 社区为 Common Data Service 开发的工具。 请参阅[开发人员工具](https://docs.microsoft.com/dynamics365/customer-engagement/developer/developer-tools)主题以获取更多社区开发的工具。

> [!NOTE]
> 这些社区工具不是 Microsoft 的产品，因此不能将支持延伸到这些社区工具。 如果有与该工具相关的疑问，请联系发布者。 详细信息：[XrmToolBox](https://www.xrmtoolbox.com)。

### <a name="see-also"></a>另请参阅  
[使用 PowerApps 门户创建和编辑 Common Data Service 的字段](create-edit-field-portal.md)<br />
[使用 PowerApps 解决方案资源管理器创建和编辑 Common Data Service 的字段](create-edit-field-solution-explorer.md)<br />
[字段类型和字段数据类型](types-of-fields.md)<br />
[开发人员文档：使用属性元数据](/dynamics365/customer-engagement/developer/org-service/work-attribute-metadata)
 
