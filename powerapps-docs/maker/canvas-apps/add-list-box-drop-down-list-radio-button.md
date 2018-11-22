---
title: 向画布应用添加列表框、下拉列表或单选按钮 | Microsoft Docs
description: 通过 PowerApps，在画布应用中创建或配置多选选项
author: fikaradz
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 10/24/2018
ms.author: fikaradz
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 293c850c5af980a480a56cb9fb3b8c7866950580
ms.sourcegitcommit: c1f58a16f8dcd309a1d5fc4658ca16d82c615994
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2018
ms.locfileid: "49991737"
---
# <a name="add-a-list-box-a-drop-down-list-or-radio-buttons-to-a-canvas-app"></a>向画布应用添加列表框、下拉列表或单选按钮

在画布应用中显示一列数据（例如，包含多列的表中的数据），便于用户选择列表中的一项或多项。

- 添加便于用户选择多个选项的列表框。
- 添加占用较少屏幕空间的下拉列表。
- 添加一组可实现特定设计效果的单选按钮。

虽然本主题以列表框和单选按钮为重点，但相同的原则也适用于下拉列表。

[!INCLUDE [app-customization-requirements](../../includes/app-customization-requirements.md)]

## <a name="create-a-simple-list"></a>创建简单列表

1. 添加“列表框”控件，将它命名为“MyListBox”，并将它的“Items”属性设置为以下表达式：

    ```["circle","triangle","rectangle"]```  <br/>

    设计器的外观与下图类似：

    ![][4]

4. 在“插入”选项卡上，依次选择“图标”和圆形，再将圆形移到“MyListBox”下面：

    ![][5]  

5. 添加三角形和矩形，再将这些形状在“MyListBox”下面排成一行：

    ![][6]  

6. 将以下形状的 **[Visible](controls/properties-core.md)** 属性设置为以下函数：  

   | 形状 | 将 Visible 函数设置为 |
   | --- | --- |
   | 圆形 |```If("circle" in MyListBox.SelectedItems.Value, true)``` |
   | 三角形 |```If("triangle" in MyListBox.SelectedItems.Value, true)``` |
   | 矩形 |```If("rectangle" in MyListBox.SelectedItems.Value, true)``` |

7. 按住 Alt 键的同时，选择“MyListBox”中的一个或多个形状。

    仅显示所选的形状。

上述步骤使用了表达式来创建项列表。 可以将此应用于业务中的其他元素。 例如，可使用“下拉列表”控件来显示产品图像、产品说明等。

## <a name="add-radio-buttons"></a>添加单选按钮
1. 在“主页”选项卡上，依次选择“新建屏幕”和“空白”。

2. 在“插入”选项卡上，选择“控件”，然后选择“单选按钮”。

    ![][10]  

3. 将“单选按钮”控件重命名为“Choices”，并将其 **[Items](controls/properties-core.md)** 属性设置为此公式：  
   ```["red","green","blue"]```  <br/>

    ![][12]  

    如有需要，可将控件大小重设为显示所有选项。

4. 在“插入”选项卡上，选择“图标”，然后选择圆形。

5. 将圆形的 **[Fill](controls/properties-color-border.md)** 属性设置为下面的函数：  
   ```If(Choices.Selected.Value = "red", Red, Choices.Selected.Value = "green", Green, Choices.Selected.Value = "blue", Blue)```  

    在此公式中，圆形根据所选单选按钮更改其颜色。

6. 将圆形移到“单选按钮”控件下面，如此示例所示：

    ![][14]  

7. 按住 Alt 键的同时，选中不同单选按钮，以更改圆形的颜色。

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
