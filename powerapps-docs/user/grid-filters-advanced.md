---
title: 使用高级网格筛选器创建个人视图 | Microsoft Docs
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 04/02/2020
ms.author: mkaur
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 0a27f7104b85b8ae45146ea7a3626cd1b0e2157c
ms.sourcegitcommit: 3e6c499a65ada8a9f28022a02f64030b0c069a17
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/04/2020
ms.locfileid: "80661361"
---
# <a name="edit-or-create-personal-views-using-advanced-grid-filters"></a>使用高级网格筛选器编辑或创建个人视图 

使用高级筛选器选项可以创建个人视图，用于查看对你很重要的记录。 借助高级筛选器选项，可以创建从简单到复杂的各种视图。 还可以向筛选器添加分组和嵌套条件。


> [!NOTE]
> 高级筛选器选项只有英语版。

创建并保存的个人视图显示在“我的视图”  下的个人视图列表中。

> [!div class="mx-imgBorder"]
> ![个人视图](media/my_peronsal_view.png "个人视图")


## <a name="see-the-current-view-definition"></a>查看当前视图定义

若要查看哪些筛选器应用于当前视图，请依次选择视图和“筛选器”  ![“筛选器”图标](media/commandbar_filter_icon.png "“筛选器”图标")。 这会打开表达式生成器，并显示默认视图定义。

> [!div class="mx-imgBorder"] 
> ![当前视图定义](media/current_view_def.gif "此图像展示了如何查看视图的筛选器")

## <a name="add-conditions-to-filters"></a>向筛选器添加条件

1. 若要编辑当前视图，并添加更多筛选器，请依次选择视图和“筛选器”  ![“筛选器”图标](media/commandbar_filter_icon.png "“筛选器”图标")。
2. 在“高级筛选器”  屏幕上，使用表达式生成器向筛选器添加条件。 若要详细了解如何添加条件，请参阅[向筛选器添加条件](https://docs.microsoft.com/powerapps/maker/model-driven-apps/create-edit-view-filters#add-conditions-to-a-filter)。
3. 完成后，选择“应用”  。 

   > [!div class="mx-imgBorder"] 
   > ![添加筛选器](media/add_filters.gif "此图像展示了如何使用表达式生成器来添加筛选器")

### <a name="add-grouped-or-nested-conditions"></a>添加分组或嵌套条件

若要进一步向下钻取数据，可以向筛选器添加分组或嵌套条件。 有关详细信息，请参阅[向筛选器添加分组条件](https://docs.microsoft.com/powerapps/maker/model-driven-apps/create-edit-view-filters#add-a-group-condition-to-a-filter)。

   > [!div class="mx-imgBorder"] 
   > ![添加分组或嵌套条件](media/group_condition.gif "此图像展示了如何向筛选器添加分组或嵌套条件")

### <a name="clear-filters"></a>清除筛选器

若要清除已应用的筛选器，并将视图重置回原始定义，请选择“清除筛选器”  ![“清除筛选器”图标](media/clear_filter_icon.png "“清除筛选器”图标")。

### <a name="save-your-personal-view"></a>保存个人视图

视图名称旁边的星号表示视图尚未保存。 

   > [!div class="mx-imgBorder"] 
   > ![未保存的视图](media/unsaved_view.png "未保存的视图")

1. 若要保存个人视图，请选择命令栏上的“更多”  ![“更多”图标](media/commandbar_more_icon.png "“更多”图标")。 
2. 依次选择“创建视图”   > “将筛选器另存为新视图”  。
3. 在“另存为新视图”  对话框中，键入视图的名称和说明，然后选择“保存”  。
4. 此时，保存的视图会显示在“我的视图”  下的个人视图列表中。

   > [!div class="mx-imgBorder"] 
   > ![保存个人视图](media/save_personal_view.gif "此图像展示了如何保存个人视图")


   
