---
title: "添加列表框、下拉列表和单选按钮 | Microsoft 文档"
description: "在 PowerApps 中创建或配置多选选项"
services: 
suite: powerapps
documentationcenter: 
author: lonu
manager: anneta
editor: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/23/2016
ms.author: lonu
ms.openlocfilehash: 819443db4359ec30cb1ba5924c93338243b464c2
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2017
---
# <a name="add-a-list-box-a-drop-down-list-or-radio-buttons"></a>添加列表框、下拉列表或单选按钮
PowerApps 提供多选和单选选项，其中包括列表框、下拉列表和单选按钮。 在本主题中，我们会添加这些控件并使用**表**公式来生成列表。 在列表中选定某项时，它会更新其他控件。

&nbsp;

[!INCLUDE [app-customization-requirements](includes/app-customization-requirements.md)]

## <a name="add-a-list-box"></a>添加列表框
1. 在“插入”选项卡上，选择“控件”，然后选择“列表框”：  
   
    ![][2]  
2. 将“列表框”控件重命名为“MyListBox”：  
   
    ![][3]  
3. 将其 **[Items](controls/properties-core.md)** 属性设置为下面的表达式：  
   ```["circle","triangle","rectangle"]```  <br/>
   
    设计器的外观与下图类似：
   
    ![][4]  
4. 在“插入”选项卡上，选择“图标”，选择圆形，然后将其移到“列表框”控件下面：
   
    ![][5]  
5. 添加三角形和矩形，然后将这些形状在“列表框”控件下面排成一行：
   
    ![][6]  
6. 将以下形状的 **[Visible](controls/properties-core.md)** 属性设置为以下函数：  
   
   | 形状 | 将 Visible 函数设置为 |
   | --- | --- |
   | 圆形 |```If("circle" in MyListBox.SelectedItems.Value, true)``` |
   | 三角形 |```If("triangle" in MyListBox.SelectedItems.Value, true)``` |
   | 矩形 |```If("rectangle" in MyListBox.SelectedItems.Value, true)``` |
7. 预览所创建的内容 ![][1]。 在“列表框”控件中选择不同的形状。 仅显示所选的形状。 按 Esc 或选择“X”返回到屏幕。

在这些步骤中使用了表达式在“列表框”控件中创建项列表。 根据在“列表框”控件中所做的选择，将显示不同的形状。 可以将此应用于业务中的其他元素。 例如，可以使用“列表框”控件来显示产品图像、产品说明等等。

## <a name="add-radio-buttons"></a>添加单选按钮
1. 在“主页”选项卡上，选择“新屏幕”。
2. 在“插入”选项卡上，选择“控件”，然后选择“单选按钮”。
   
    ![][10]  
3. 将“单选按钮”控件重命名为“Choices”，并将其 **[Items](controls/properties-core.md)** 属性设置为此公式：  
   ```["red","green","blue"]```  <br/>
   
    ![][12]  
   
    如有需要，可将控件大小重设为显示所有选项。
4. 在“插入”选项卡上，选择“图标”，然后选择圆形。
5. 将圆形的 **[Fill](controls/properties-color-border.md)** 属性设置为下面的函数：  
   ```If(Choices.Selected.Value = "red", RGBA(192, 0, 0, 1), Choices.Selected.Value = "green", RGBA(0, 176, 80, 1), Choices.Selected.Value = "blue", RGBA(0, 32, 96, 1))```  
   
    在此公式中，圆形根据所选单选按钮更改其颜色。
6. 将圆形移到“单选按钮”控件下面，如此示例所示：
   
    ![][14]  
7. 预览所创建的内容：![][1]。 选中不同的单选按钮以更改圆形的颜色。 按 Esc 或选择“X”返回到屏幕。

## <a name="add-a-drop-down-list"></a>添加下拉列表
1. 添加屏幕，然后添加“下拉列表”控件。
   
    ![][15]  
2. 将该控件重命名为“DDChoices”，并将其 **[Items](controls/properties-core.md)** 属性设置为此公式：<br>
   **["red","green","blue"]**
3. 添加一个圆形，将其移到“下拉列表”控件下面，然后将圆形的 **[Fill](controls/properties-color-border.md)** 属性设置为此公式：  
   ```If(DDChoices.Selected.Value = "red", RGBA(192, 0, 0, 1), DDChoices.Selected.Value = "green", RGBA(0, 176, 80, 1), DDChoices.Selected.Value = "blue", RGBA(0, 32, 96, 1))```
4. 预览所创建的内容：![][1]。 选择不同选项以更改圆形的颜色。

[1]: ./media/add-list-box-drop-down-list-radio-button/preview.png
[2]: ./media/add-list-box-drop-down-list-radio-button/listbox.png
[3]: ./media/add-list-box-drop-down-list-radio-button/renamelistbox.png
[4]: ./media/add-list-box-drop-down-list-radio-button/itemslistbox.png
[5]: ./media/add-list-box-drop-down-list-radio-button/circle.png
[6]: ./media/add-list-box-drop-down-list-radio-button/allshapes.png
[10]: ./media/add-list-box-drop-down-list-radio-button/radiobutton.png
[12]: ./media/add-list-box-drop-down-list-radio-button/itemsradio.png
[14]: ./media/add-list-box-drop-down-list-radio-button/radiocircle.png
[15]: ./media/add-list-box-drop-down-list-radio-button/dropdown.png
