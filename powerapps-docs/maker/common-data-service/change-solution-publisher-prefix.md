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
ms.openlocfilehash: c8d16a0c8451abc769990dbd88e6ad7f1e7846a5
ms.sourcegitcommit: c9c1c78dadc92913558dab44af0890e90e2adcd0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/27/2020
ms.locfileid: "3088569"
---
# <a name="solution-publisher-overview"></a>解决方案发布商概述

您创建的每个应用或所做的每个自定义项都是解决方案的一部分。 每个解决方案都有有一个发布商。 发布商是您在创建解决方案时创建的。 

> [!div class="mx-imgBorder"] 
> <img src="media/solution-publisher-select.png" alt="Select solution publisher" height="731" width="416">

解决方案发布商指示应用是谁开发的。 因此，您应该创建有所指示的解决方案发布商。 您可以通过从 Power Apps 中的**解决方案**区域选择**设置**来查看解决方案的解决方案发布商。

## <a name="solution-publisher-prefix"></a>解决方案发布商前缀
解决方案发布商包括前缀。 前缀有助于确定哪个发布商负责该组件。 例如，此处显示的 *Contoso 解决方案*包括一个 *contoso* 解决方案发布商前缀。 

> [!div class="mx-imgBorder"] 
> ![Fundraiser 解决方案发布商前缀](media/publisher-prefix.png)

> [!NOTE]
> 若要更改解决方案发布商前缀，您应在创建任何新应用或元数据项目前更改。 您不能更改元数据项目的名称。 

## <a name="common-data-services-default-solution"></a>Common Data Services 默认解决方案
Power Apps 中的默认解决方案是 Common Data Services 默认解决方案，其与 Common Data Service 默认发布商关联。 将为发布商随机分配默认发布商前缀，例如，可能是 *cr8a3*。 这意味着默认解决方案中创建的元数据的每个新项目的名称都会将此前缀附加到用于唯一标识项目的名称前面。 如果您创建名为 *Animal* 的新实体，Common Data Service 使用的唯一名称将是 *cr8a3_animal*。 所有新字段（属性）、关系或选项集选项同样如此。 如果要自定义默认解决方案，请考虑更改发布商前缀。 

## <a name="create-a-solution-publisher"></a>创建解决方案发布商
1.  在 Power Apps 门户中，选择**解决方案**。 
2.  在命令栏上，选择**新建解决方案**，在右窗格中选择**发布商**下拉列表，然后选择 **+ 发布商**。 
    > [!div class="mx-imgBorder"] 
    > <img src="media/create-new-pubisher.png" alt="Create a new publisher" height="738" width="400">
3.  在**新建发布商**窗体中，输入必需和可选信息： 
   - **显示名称**。 输入发布商的显示名称。 
   - **名称**. 输入发布商的唯一名称。 
   - **前缀**。 输入所需发布商前缀。 
   -    **选项值前缀**。 此字段基于发布商前缀生成一个编号。 在将选项添加到选项集时将使用此编号，并提供一个指示符，指示使用了那个解决方案来添加选项。 
   - **联系人详细信息**。 （可选）可添加联系人和地址信息。
4. 选择**保存并关闭**。

## <a name="change-a-solution-publisher"></a>更改解决方案发布商
可通过以下步骤更改非托管解决方案的解决方案发布商。
1.  在 Power Apps 门户中，选择**解决方案**，选择所需解决方案旁边的 **...**， 然后选择**设置**。 
2.  在**解决方案设置**窗格中，选择**编辑发布商**。 
3.  将**显示名称**和**前缀**字段编辑为所需值。 **选项值前缀**字段基于发布商前缀生成一个编号。 在将选项添加到选项集时将使用此编号，并提供一个指示符，指示使用了那个解决方案来添加选项。 
4.  除了前缀，还可以在**联系人详细信息**部分中更改解决方案发布商显示名称、联系信息和地址。 
5.  选择**保存并关闭**。

### <a name="see-also"></a>另请参阅
[创建解决方案](create-solution.md)