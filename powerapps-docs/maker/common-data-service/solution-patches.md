---
title: 创建解决方案修补程序 | MicrosoftDocs
description: 了解如何创建解决方案修补程序
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
ms.assetid: ''
caps.latest.revision: 15
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 9bddae4295a891d4c4dd86593b4fa27815b2b03c
ms.sourcegitcommit: 3f89b04359df19f8fa5167e2607509bb97e60fe0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/25/2020
ms.locfileid: "3165251"
---
# <a name="create-solution-patches"></a>创建解决方案修补程序  
您可以创建父解决方案的修补程序并将其作为次要更新导出到基本解决方案中。 在您克隆解决方案时，系统会将所有相关修补程序汇总到基本解决方案中并创建一个新版本。

> [!WARNING]
> 不建议使用克隆修补程序和克隆解决方案来更新解决方案，因为这会限制团队开发并会在将解决方案存储在源代码控制系统中时增加复杂性。 有关如何更新解决方案的信息，请参阅[升级或更新解决方案](update-solutions.md)。


## <a name="creating-updates-using-clone-solution-and-clone-to-patch"></a>使用克隆解决方案和克隆修补程序创建更新
 当您使用修补程序和克隆的解决方案时，请牢记以下信息：  
  
-   修补程序表示对父解决方案的增量次要更新。 修补程序在安装到目标系统上后，可以在父解决方案中添加或更新组件和资产，但不能从父解决方案中删除任何组件或资产。  
  
-   修补程序只能有一个父解决方案，但父解决方案可以包含一个或多个修补程序。  
  
-   修补程序从非托管解决方案创建。 您无法从托管解决方案创建修补程序。  
  
-   当将修补程序导入到目标系统时，它应被作为托管修补程序导出。 请勿在生产环境中使用非托管修补程序。  
  
-   父解决方案必须位于目标系统中，才能安装修补程序。  
  
-   您可以删除或更新修补程序。  
  
-   如果您删除父解决方案，则所有子修补程序也会被删除。 系统提供了一条警告消息，指明您不能撤销删除操作。 删除操作是在单个事务中执行的。 如果一个修补程序或父解决方案无法删除，则会回滚整个事务。  
  
-   在为父解决方案创建第一个修补程序后，解决方案会被锁定，并且您不能在此解决方案中进行任何更改或将其导出。 但是，如果删除所有子修补程序，父解决方案则会被解锁。  
  
-   在您克隆基本解决方案时，所有子修补程序会汇总到基本解决方案中，并成为一个新版本。 可以在克隆的解决方案中添加、编辑或删除组件和资产。  
  
-   当克隆的解决方案作为托管解决方案安装在目标系统上时，它表示对基本解决方案的替换。 通常，您会使用克隆的解决方案将主要更新传送到之前的解决方案中。  

在克隆解决方案时，您指定的版本号包括主要和次要位置。 

   > [!div class="mx-imgBorder"]
   > <img src="media/clone-solution.png" alt="Clone a patch major and minor version" height="560" width="307"> 

 在克隆修补程序时，您指定的版本号包括构内部版本或修订版本位置。 

   > [!div class="mx-imgBorder"] 
   > <img src="media/clone-a-patch2.png" alt="Clone a patch build and revision version" height="560" width="307">

有关版本号的详细信息，请参阅本文中的[克隆解决方案和克隆修补程序版本号](#clone-solution-and-clone-patch-version-numbers)。
  
## <a name="create-a-solution-patch"></a>创建解决方案修补程序  
 修补程序包含对父解决方案的更改，例如添加或编辑组件和资产。 不必包括父解决方案的组件，除非您计划对其进行编辑。  
  
## <a name="create-a-patch-for-an-unmanaged-solution"></a>为非托管解决方案创建修补程序  
  
1. 转到 Power Apps 门户，然后选择**解决方案**。   
  
2. 在解决方案列表中，选择要为其创建修补程序的非托管解决方案。 在命令栏上，选择**克隆**，然后选择**克隆修补程序**。 打开的右窗格中有基本解决方案的名称和修补程序的版本号。 选择**保存**。  
   > [!div class="mx-imgBorder"] 
   > <img src="media/clone-a-patch.png" alt="Clone a patch" height="735" width="408">
 
3. 在解决方案列表中，查找并打开新建的修补程序。 请注意，已经为解决方案的唯一名称追加了 _Patch_*十六进制编号*。 就像对待基本解决方案一样，添加所需组件和资产。  
  
### <a name="create-a-patch-using-solution-explorer"></a>使用解决方案资源管理器创建修补程序
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
> 克隆解决方案会将原始解决方案和关联的修补程序合并到新的基本解决方案中，并删除原始解决方案和修补程序。 
  
1. 转到 Power Apps 门户，然后选择**解决方案**。   
  
2.  在解决方案列表中，选择要为其创建克隆的非托管解决方案。 在命令栏上，选择**克隆**，然后选择**克隆解决方案**。 右窗格中将显示基本解决方案的名称和新版本号。 选择**保存**。  

## <a name="clone-solution-and-clone-patch-version-numbers"></a>克隆解决方案和克隆修补程序版本号
修补程序必须具有比父解决方案更高的内部版本号或修订号。 它不能有更高的主要或次要版本。 例如，对于版本为 3.1.5.7 的基本解决方案，修补程序可以是 3.1.5.8 版或 3.1.7.0 版，但不能是 3.2.0.0 版。 克隆的解决方案必须具有大于或等于基本解决方案的版本号。 例如，基本解决方案版本是 3.1.5.7，克隆的解决方案可以是 3.2.0.0 版或 3.1.5.7 版。 在克隆解决方案或修补程序时，您将为克隆的解决方案设置主要和次要版本值，为修补程序设置内部版本或修订版本值。  
  
### <a name="see-also"></a>另请参阅
[升级或更新解决方案](update-solutions.md)