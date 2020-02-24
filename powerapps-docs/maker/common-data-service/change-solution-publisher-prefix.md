---
title: 解决方案发布商概述 | MicrosoftDocs
ms.custom: ''
ms.date: 02/03/2020
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
author: Mattp123
ms.assetid: ece684h8-ad40-4bfa-975a-3e5bafb854aa
caps.latest.revision: 55
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: b54afabbed9e7dfcc53fe887f600593e77a02a7f
ms.sourcegitcommit: cb533c30252240dc298594e74e3189d7290a4bd7
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/04/2020
ms.locfileid: "3017558"
---
# <a name="solution-publisher-overview"></a>解决方案发布商概述

您创建的每个应用或所做的每个自定义项都是解决方案的一部分。 每个解决方案都有有一个发布商。 发布商是您在创建解决方案时创建的。 

> [!div class="mx-imgBorder"] 
> <img src="media/solution-publisher-select.png" alt="Select solution publisher" height="731" width="416">

解决方案发布商指定应用程序是谁开发的。 可通过前缀快速了解项目是哪些解决方案添加的。 因此，您应该创建解决方案发布商并指定有意义的前缀。 在查看导入的解决方案中的元数据项时，这尤其重要。 例如，其中包含 fundraiser 示例应用的解决方案将 *sample* 用作发布商前缀。 

> [!div class="mx-imgBorder"] 
> ![Fundraiser 解决方案发布商前缀](media/fundraiser-sample-app-prefix.png)

> [!NOTE]
> 若要更改解决方案发布商前缀，您应在创建任何新应用或元数据项目前更改。 您不能更改元数据项目的名称。 

## <a name="common-data-services-default-solution"></a>Common Data Service 的默认解决方案
Power Apps 中的默认解决方案是 Common Data Service 的默认解决方案，其与 Common Data Service 默认发布商关联。 将为发布商随机分配默认发布商前缀，例如，可能是 *cr8a3*。 这意味着默认解决方案中创建的元数据的每个新项目的名称都会将此前缀附加到用于唯一标识项目的名称前面。 如果您创建名为 *Animal* 的新实体，Common Data Service 使用的唯一名称将是 *cr8a3_animal*。 所有新字段（属性）、关系或选项集选项同样如此。 如果要自定义默认解决方案，请考虑更改发布商前缀。 

## <a name="create-a-solution-publisher"></a>创建解决方案发布商
1.  在 Power Apps 门户中，选择**设置**（齿轮），然后选择**高级设置**。 
2.  选择**设置** > **自定义** > **发布商**。 
3.  在 **发布商主视图**命令栏中，选择**新建**。 
4.  输入所需信息： 
   - **显示名称**。 输入发布商的显示名称。 
   - **名称**. 输入发布商的唯一名称。 
   - **前缀**。 输入所需发布商前缀。 
   -    **选项值前缀**。 此字段基于发布商前缀生成一个编号。 在将选项添加到选项集时将使用此编号，并提供一个指示符，指示使用了那个解决方案来添加选项。 
   - **联系人详细信息**。 （可选）可添加联系人和地址信息。
5. 选择**保存并关闭**。

## <a name="change-a-solution-publisher"></a>更改解决方案发布商
可通过以下步骤更改非托管解决方案的解决方案发布商。
1.  在 Power Apps 门户中，选择**解决方案**，选择所需解决方案旁边的 **...**， 然后选择**设置**。 
2.  在**解决方案设置**窗格中，选择**编辑发布商**。 
3.  将**显示名称**和**前缀**字段编辑为所需值。 **选项值前缀**字段基于发布商前缀生成一个编号。 在将选项添加到选项集时将使用此编号，并提供一个指示符，指示使用了那个解决方案来添加选项。 
4.  除了前缀，还可以在**联系人详细信息**部分中更改解决方案发布商显示名称、联系信息和地址。 
5.  选择**保存并关闭**。

### <a name="see-also"></a>另请参阅
[创建解决方案](create-solution.md)