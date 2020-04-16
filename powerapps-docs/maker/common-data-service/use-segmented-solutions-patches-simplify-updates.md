---
title: 将细分的解决方案与 Power Apps 结合使用 | MicrosoftDocs
description: 了解如何使用解决方案细分来更新解决方案
ms.custom: ''
ms.date: 02/04/2020
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: 5c05f683-e1bd-4885-be23-b6973128773f
caps.latest.revision: 15
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 16730151eb6d7ec45fad7a6803eed3e76f68f8d4
ms.sourcegitcommit: a1b54333338abbb0bc3ca0d7443a5a06b8945228
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/13/2020
ms.locfileid: "3125473"
---
# <a name="use-segmented-solutions"></a>使用细分解决方案 

使用解决方案细分，以便仅包括在分发解决方案更新时更新的实体组件。 利用解决方案细分，您将导出包含所选实体资产（例如实体字段、窗体和视图）的解决方案更新，而不是包含所有资产的整个实体。 <!-- Depending on the complexity of your app, segmentation of the solution can be as simple as everything in a single solution to segmenting by component type, such as entities in one solution, canvas apps in another, and plugins in a third. --> 若要创建细分解决方案，使用 Power Apps 中的**解决方案**区域。  

当您从以下选项中选择以将现有实体添加到解决方案时，可以细分解决方案： 
- 不包括任何组件。 当您不选择任何组件或元数据时，将向解决方案添加最基本的实体信息。 因此，除了友好名称之外，将不包括实体属性（元数据）或组件。   
- **选择组件**。 您可以通过分别选择与实体关联的每个组件（如字段、关系、业务规则、视图、窗体和图表）来细分解决方案。 使用此选项仅选择已随实体添加或更改的组件，例如新的自定义字段或添加窗体。  
- **包含实体元数据**。 此选项不包括相关实体之类的组件，但包括*所有*与实体关联的元数据。 元数据包括实体属性，如审核、重复项检测或更改跟踪。 
- **包含所有组件**。 此选项包含与实体关联的所有组件*和*元数据。 可以包含其他实体或实体组件，如业务流程、报表、连接和队列。 仅当分发目标环境中不存在的非托管实体时，才应使用此选项。 

    > [!WARNING]
    > 不要在解决方案中添加您不需要的组件。 当您将更新导入目标环境时，包含不需要的组件的解决方案会导致现有组件（现在位于随解决方案更新引入的层之下）出现意外行为。 例如，如果为未更新的实体添加视图，并且现有层中的视图具有自定义项，则现有的自定义项可能会停用。 有关详细信息，请参阅[解决方案层](solution-layers.md)。

<!-- The below was from Per but I don't think it fits in this topic that is only about solution segmentation with entities. 
Similar to the planning that goes into how you model the data that goes into your app, planning for segmentation should be considered before you distribute your solution. Segmenting solutions from a single solution into multiple solutions a month or two years after the initial app has been built can be complex and is prone to cause issues.  -->

## <a name="create-a-segmented-solution-with-entity-assets"></a>创建一个包含实体资产的细分的解决方案 
 若要创建细分的解决方案，首先创建一个非托管解决方案，然后仅添加您已更新的组件。 类似于向导的安装程序会引领您一步一步完成添加实体资产的过程。 

例如，假设您创建了一个新的自定义实体，该实体在名为*自定义实体*的任何其他环境中都不存在，并且您还为客户实体添加了一个名为 *topten* 的新字段。 要创建细分解决方案，请按照下列步骤操作。 
  
1. 转到 Power Apps 门户，然后选择**解决方案**。  
  
2.  选择**新建解决方案**并创建解决方案。 在必填字段中输入相关信息。 选择**创建**。  
  
3.  打开创建的解决方案。 在命令栏上，选择**添加现有**，然后选择**实体**。  
  
4.  在**添加现有实体**窗格中，选择要添加到解决方案中的一个或多个实体。 例如，选择**客户**和**自定义实体**。 选择**下一步**。  

5.  在**选择实体**窗格中，可以从资产中选择要包含的实体： 
    - **包含所有组件**。 此选项包含与实体关联的所有组件*和*元数据。 可以包含其他实体或实体组件，如业务流程、报表、连接和队列。 
    - **包含实体元数据**。 此选项*仅*包含与实体关联的元数据。 元数据包括实体属性，如审核、重复项检测或更改跟踪。 
    - **选择组件**。 此选项让您可以分别选择与实体关联的每个组件，如字段、关系、业务规则、视图、窗体和图表。 
    - 不要包含任何组件。 

      在此示例中，由于从未将*自定义实体*导入到目标环境中，因此在**自定义实体**旁边，选择**包含所有组件**。 在**客户**下，选择**选择组件**。  
      > [!div class="mx-imgBorder"] 
      > ![添加现有实体](media/add-existing-entities1.png)
  
6.  由于只有 *topten* 自定义字段是客户实体的新增字段，因此选择**前十个**，然后选择**添加**。  
     > [!div class="mx-imgBorder"] 
     > ![选择实体组件](media/add-existing-entities2.png)

7. 选择**添加**将组件添加到解决方案中。 

### <a name="create-a-segmented-solution-using-solution-explorer"></a>使用解决方案资源管理器创建细分的解决方案  
以下各图提供了通过从 `Account`、`Case` 和 `Contact` 实体选择实体资产创建细分的解决方案的示例。  

> [!NOTE]
> 某些 Dynamics 365 应用程序（如 Dynamics 365 Customer Service）中随附了案例实体。 
  
首先打开一个创建的非托管解决方案。 选择**实体**组件。  

 > [!div class="mx-imgBorder"] 
 > ![添加现有资源。](media/solution-segmentation-add-existing-resources-admin.png "添加现有资源。")  
  
 然后，选择解决方案组件。  
  
 ![选择解决方案组件。](media/solution-segmentation-select-components-admin.png "选择解决方案组件。")  
  
 按照向导进行操作。 在步骤 1 中，按字母顺序开始，选择第一个实体，即 `Account` 实体的资产，如下所示。  
  
 ![启动向导。](media/solution-segmentation-wizard-starts-admin.png "启动向导。")  
  
 打开**字段**选项卡，选择**客户编号**字段。  
  
 ![选择客户实体资产。](media/solution-segmentation-select-account-assets-admin.png "选择客户实体资产。")  
  
 在步骤 2 中，为**案例**实体添加所有资产。  
  
 ![选择案例实体资产。](media/solution-segmentation-select-case-assets-admin.png "选择案例实体资产。")  
  
 在步骤 3 中，为**联系人**实体添加**纪念日**字段。  
  
 ![选择联系人实体资产。](media/solution-segmentation-select-contact-assets-admin.png "选择联系人实体资产。")  
  
 结果，所创建的细分的解决方案包含三个实体：`Account`、`Case` 和 `Contact`。 每个实体仅包含所选择的资产。  
  
 > [!div class="mx-imgBorder"] 
 > ![带实体的解决方案。](media/solution-segmentation-solution-entities-admin.png "带实体的解决方案。")  
  
  
### <a name="see-also"></a>另请参阅  
 [解决方案概述](solutions-overview.md)


