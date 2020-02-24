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
ms.openlocfilehash: d13eafa6858a6eec86de2db08504575c7fab9acd
ms.sourcegitcommit: 60a721432b3fa2abd14ccb3bd16a6b34e13ada85
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/05/2020
ms.locfileid: "3026357"
---
# <a name="use-segmented-solutions"></a>使用细分解决方案 

若要更紧密地控制您在解决方案或解决方案修补程序中分发的内容，请使用解决方案细分。 根据您的应用程序的复杂程度，细分解决方案可能非常简单，就像在一个解决方案中要按组件类型细分，如按一个解决方案中的实体、另一个中的区域应用和第三个中的插件。 若要创建细分的解决方案，可以使用  Power Apps 用户界面中的解决方案区域，而不必编写代码。  

细分解决方案的方法主要有三种： 
- 在生成应用时细分解决方案。 方法是，添加特定组件以控制要放入解决方案的项。 详细信息：[创建一个包含所需实体资产的细分的解决方案](#create-a-segmented-solution-with-entity-assets)
- 创建细分解决方案以生成和发布解决方案的小更新。 方法是，克隆修补程序。 详细信息：[创建解决方案修补程序](#create-a-solution-patch)
- 创建细分解决方案以生成和发布解决方案的大更新。 方法是，克隆解决方案。 详细信息：[克隆解决方案](#clone-a-solution)

## <a name="when-to-plan-for-segmentation"></a>何时计划细分 
与要进入您的应用的数据的建模方法的规划类似，应该考虑在分发解决方案之前进行细分。 在生成初始应用的一个月或两年后从一个解决方案细分为多个解决方案可能非常复杂，容易导致问题。  

## <a name="solutions-as-patches"></a>解决方案为修补程序形式
利用解决方案细分，您可以导出包含所选实体资产（例如实体字段、窗体和视图）的解决方案修补程序，而不是包含所有资产的整个实体。 

除对解决方案中的内容具有更多控制之外，您还可以控制修补程序中包含什么。 您可以创建父解决方案的修补程序并将其作为次要更新导出到基本解决方案中。 在您克隆解决方案时，系统会将所有相关修补程序汇总到基本解决方案中并创建一个新版本。  
  
 当您使用修补程序和克隆的解决方案时，请牢记以下信息：  
  
-   修补程序表示对父解决方案的增量次要更新。 修补程序在安装到目标系统上后，可以在父解决方案中添加或更新组件和资产，但不能从父解决方案中删除任何组件或资产。  
  
-   修补程序只能有一个父解决方案，但父解决方案可以包含一个或多个修补程序。  
  
-   修补程序是为非托管解决方案创建的。 您无法为托管解决方案创建修补程序。  
  
-   当将修补程序导出到目标系统时，它应被作为托管修补程序导出。 请勿在生产环境中使用非托管修补程序。  
  
-   父解决方案必须位于目标系统中，才能安装修补程序。  
  
-   您可以删除或更新修补程序。  
  
-   如果您删除父解决方案，则所有子修补程序也会被删除。 系统提供了一条警告消息，指明您不能撤销删除操作。 删除操作是在单个事务中执行的。 如果一个修补程序或父解决方案无法删除，则会回滚整个事务。  
  
-   在为父解决方案创建第一个修补程序后，解决方案会被锁定，并且您不能在此解决方案中进行任何更改或将其导出。 但是，如果删除所有子修补程序，父解决方案则会被解锁。  
  
-   在您克隆基本解决方案时，所有子修补程序会汇总到基本解决方案中，并成为一个新版本。 可以在克隆的解决方案中添加、编辑或删除组件和资产。  
  
-   当克隆的解决方案作为托管解决方案安装在目标系统上时，它表示对基本解决方案的替换。 通常，您会使用克隆的解决方案将主要更新传送到之前的解决方案中。  
  
### <a name="understanding-version-numbers-for-cloned-solutions-and-patches"></a>了解克隆的解决方案和修补程序的版本号  
 解决方案的版本具有以下格式：major.minor.build.revision。 修补程序必须具有比父解决方案更高的内部版本号或修订号。 它不能有更高的主要或次要版本。 例如，基本解决方案版本是 3.1.5.7，修补程序可以是 3.1.5.8 版或 3.1.7.0 版，但不能是 3.2.0.0 版。 克隆的解决方案必须具有大于或等于基本解决方案的版本号。 例如，基本解决方案版本是 3.1.5.7，克隆的解决方案可以是 3.2.0.0 版或 3.1.5.7 版。 在 UI 中，您只能为克隆的解决方案设置主要和次要版本值，为修补程序设置内部版本号或修订号值。  
  
## <a name="create-a-segmented-solution-with-entity-assets"></a>创建一个包含实体资产的细分的解决方案 
 若要创建细分的解决方案，请从创建非托管解决方案并添加现有资源开始。 您可以添加多个系统实体或自定义实体，然后对于每个实体，选择要包含在解决方案中的资产。 类似于向导的安装程序会引领您一步一步完成添加实体资产的过程。  
  
1. 转到 Power Apps 门户，然后选择**解决方案**。  
  
2.  选择**新建解决方案**并创建解决方案。 在必填字段中输入相关信息。 选择**创建**。  
  
3.  打开创建的解决方案。 在命令栏上，选择**添加现有**，然后选择**实体**。  
  
4.  在**添加现有**窗格中，选择要向解决方案添加的一个或多个实体，如联系人之类标准实体和自定义实体。 选择**下一步**。  
    > [!div class="mx-imgBorder"] 
    > ![添加现有实体](media/add-existing-entities1.png)

5.  在**选择实体**窗格中，可以从资产中选择要包含的实体。 
    - **包含所有组件**。 此选项包含与实体关联的所有组件*和*元数据。 可以包含其他实体或实体组件，如业务流程、报表、连接和队列。 
    - **包含实体元数据**。 此选项*仅*包含与实体关联的元数据。 元数据包括实体属性，如审核、重复项检测或更改跟踪。 
    - **选择组件**。 此选项让您可以分别选择与实体关联的每个组件，如字段、关系、业务规则、视图、窗体和图表。 
      > [!div class="mx-imgBorder"] 
      > ![选择实体组件](media/add-existing-entities2.png)
  
6.  选择**添加**。  

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
  
## <a name="create-a-solution-patch"></a>创建解决方案修补程序  
 修补程序包含对父解决方案的更改，例如添加或编辑组件和资产。 不必包括父解决方案的组件，除非您计划对其进行编辑。  
  
### <a name="create-a-patch-for-an-unmanaged-solution"></a>为非托管解决方案创建修补程序  
  
1. 转到 Power Apps 门户，然后选择**解决方案**。   
  
2. 在解决方案列表中，选择要为其创建修补程序的非托管解决方案。 在命令栏上，选择**克隆**，然后选择**克隆修补程序**。 打开的右窗格中有基本解决方案的名称和修补程序的版本号。 选择**保存**。  
   > [!div class="mx-imgBorder"] 
   > <img src="media/clone-a-patch.png" alt="Clone a patch" height="735" width="408">
 
3. 在解决方案列表中，查找并打开新建的修补程序。 请注意，已经为解决方案的唯一名称追加了 _Patch_*十六进制编号*。 就像对待基本解决方案一样，添加所需组件和资产。  
  
#### <a name="create-a-patch-using-solution-explorer"></a>使用解决方案资源管理器创建修补程序
 下图提供为现有解决方案创建修补程序的示例。 通过选择**克隆修补程序**开始（在压缩视图中，**克隆修补程序**图标显示为两个小的正方形，如下所示）。  
  
 > [!div class="mx-imgBorder"] 
 > ![克隆修补程序图标。](media/solution-segmentation-click-patch-icon-admin.png "克隆修补程序图标。")  
  
 在**克隆至修补程序**对话框中，您会看到，修补程序的版本号基于父解决方案的版本号，但内部版本号递增 1。 每个后续的修补程序都有比之前的修补程序更高的内部版本号或修订号。  
  
 ![使用“克隆至修补程序”对话框。](media/solution-segmentation-clone-patch-dialog-admin.png "使用“克隆至修补程序”对话框。")  
  
 以下屏幕截图显示基本解决方案 **SegmentedSolutionExample** 版本 **1.0.1.0** 和修补程序 **SegmentedSolutionExample_Patch** 版本 **1.0.2.0**。  
  
 > [!div class="mx-imgBorder"] 
 > ![带解决方案和修补程序的网格。](media/solution-segmentation-solution-patch-grid-admin.png "带解决方案和修补程序的网格。")  
  
 在修补程序中，我们添加了一个名为 `Book` 的新自定义实体，并在修补程序包含了 `Book` 实体的所有资产。  
  
 ![在修补程序中添加自定义实体。](media/solution-segmentation-add-book-patch-admin.png "在修补程序中添加自定义实体。")  
  
## <a name="clone-a-solution"></a>克隆解决方案  
 在克隆非托管解决方案时，原始解决方案和所有与此解决方案相关的修补程序都汇总到原始解决方案的新创建版本中。 克隆后，新解决方案版本中包含原始实体，以及修补程序中添加的任何组件或实体。 

![克隆解决方案](media/cloned-solution.png)

> [!IMPORTANT]
> 克隆解决方案将删除原始解决方案和关联的修补程序。 
  
1. 转到 Power Apps 门户，然后选择**解决方案**。   
  
2.  在解决方案列表中，选择要为其创建克隆的非托管解决方案。 在命令栏上，选择**克隆**，然后选择**克隆解决方案**。 右窗格中将显示基本解决方案的名称和新版本号。 选择**保存**。  
  
  
### <a name="next-steps"></a>后续步骤  
 [解决方案概述](solutions-overview.md)


