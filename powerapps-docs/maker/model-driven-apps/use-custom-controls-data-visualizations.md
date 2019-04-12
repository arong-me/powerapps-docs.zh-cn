---
title: 在 PowerApps 中使用自定义控件实现模型驱动应用程序的数据可视化 | MicrosoftDocs
description: 了解如何使用字段的自定义控件
ms.custom: ''
ms.date: 06/07/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
ms.assetid: 0d6064cd-4d38-4fc2-a564-735cb453a4b2
caps.latest.revision: 8
author: Mattp123
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="use-custom-controls-for-model-driven-app-data-visualizations"></a>使用自定义控件实现模型驱动应用程序的数据可视化

在本主题中，您将了解如何配置字段的自定义控件。 

自定义控件让您可以将应用程序用户界面组件（如传统上包含文本的字段或视图）转换为可视化项。 自定义控件可以在字段、窗体、仪表板、视图和网格上配置。 例如，滑块控件可以在数字字段上配置。

   > [!div class="mx-imgBorder"] 
   > ![自定义滑块控件](media/slider-control.PNG "字段的滑块控件")

或可编辑网格控件可以在视图上配置。 

   > [!div class="mx-imgBorder"] 
   > ![可编辑网格控件](media/editable-grid-example.png)

可将一种类型的自定义控件设置为在 Web 浏览器客户端中显示，同时让另一个自定义控件在 Dynamics 365 phone or tablet 移动应用程序中显示。 例如，可将数字输入自定义控件用于 Web 浏览器客户端中的字段，将滑块自定义控件用于手机应用程序。 发布自定义效果后，用户可与控件完全交互以更改值，如在使用线性滑块自定义控件时滑动控件。 关闭窗体时自动保存更改，就像用户更改窗体上的传统字段一样。  
  
## <a name="use-a-custom-control-to-add-visualizations-to-a-field"></a>使用自定义控件为字段添加可视化效果  
 执行此过程中的步骤将把“商机”实体中的**预算金额**字段的默认标签和文本框字段更改为滑块自定义控件。 可使用类似步骤将现有字段替换为自定义控件或为自定义字段配置自定义控件。  
  
1.  登录到 [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)。  

     

2.  展开**数据**，选择**实体**，选择所需实体，然后选择**窗体**选项卡。  
  
2.  打开窗体（如商机实体的**主**窗体）。 
  
3.  在窗体编辑器中，单击要在其中添加自定义控件的字段，如商机主窗体上的**预算金额**字段。 或者，您可以创建自定义字段。 
  
4.  在**字段属性**页中，选择**控件**选项卡，然后选择**添加控件**。  
  
5.  在“添加控件”页上，选择所需控件（如此处显示的**线性滑块**控件），然后选择**添加**。  

   > [!div class="mx-imgBorder"] 
   > ![添加线性滑块控件](media/add-slider.PNG "添加线性滑块控件")  
  
6.  选择要在其中显示控件的客户端。  
  
    - **Web**。 要使自定义控件在任何 Web 浏览器中均可用，请选择控件旁边的 **Web** 选项。 请注意，设置 **Web** 选项包括在 PC、Mac 和移动设备上的 Web 浏览器中显示控件。  
  
    - **电话**。 要使自定义控件在运行 Dynamics 365 for phones 的手机中可用，请选择控件旁边的**手机**选项。  
  
    - **平板电脑**。 要使自定义控件在运行 Dynamics 365 for tablets 的平板电脑设备中可用，请选择控件旁边的**平板电脑**选项。  
  
   > [!div class="mx-imgBorder"] 
   > ![选择用于查看自定义控件的客户端应用程序](media/choose-client.png "选择用于查看自定义控件的客户端应用程序")  
  
7.  选择**最小**、**最大**和**步骤**旁边的 ![“编辑自定义控件属性”图标](media/ccf-pencil-icon.png "“编辑自定义控件属性”图标") 铅笔图标，按照下面的说明设置属性选项，然后选择**确定**。  
  
   > [!div class="mx-imgBorder"] 
   > ![添加自定义控件属性](media/ccf-add-properties.png "添加自定义控件属性")
  
   - **最小**。 设置接受的最小值。 可绑定输入的静态值或将值绑定到现有字段。 在此示例中，**绑定到静态值**为**货币**，可输入的最小值为*零*。  
  
       - **绑定到静态值**。 选择数据类型，如整数 (Whole.None)、货币、浮点值 (FP) 或小数。 接下来，输入用于表示字段接受的最小值的数字。  
  
       - **绑定到字段上的值**。 从列表中选择将用作接受的最小值的字段。  
  
   - **最大**。 为字段设置接受的最大值。 和“最小”值一样，可绑定输入的静态值，也可以按照上面的说明将值绑定到现有字段。 在此示例中，**绑定到静态值**为**货币**，可输入的最大值为 **10 亿**。  
  
   - **步骤**。 这表示对当前值增减时的增加或减少单位。 例如，对于预算金额，可选择 100 美元的增量或减量。  
  
   - **隐藏默认控件**。 选择此选项将隐藏控件，从而在不支持自定义控件的任何客户端中不显示控件和数据。 请注意，传统 Dynamics 365 Web 客户端不支持大多数自定义控件。 默认情况下未选中此选项，而传统 Dynamics 365 Web 客户端显示默认控件（通常是基于文本的控件）。  
  
       > [!NOTE]
       >  默认控件带有 **(默认)** 标识和控件名称。  
       >   
       > > [!div class="mx-imgBorder"] 
       > > ![默认控件](media/default-control.png "默认控件")  
  
8.  选择**确定**以关闭**字段属性**页面。  
  
9. 若要激活自定义，请在实体窗体上选择**保存**，然后选择**发布**。  
  
10. 选择**保存并关闭**以关闭窗体编辑器。  
  
### <a name="see-the-custom-control-in-action"></a>查看操作中的自定义控件  
 使用自定义控件打开包含字段的记录（如前面的示例中的“商机”窗体），然后查看字段的变化。  
  
   > [!div class="mx-imgBorder"] 
   > ![窗体中显示的滑块控件](media/slider-control.PNG "窗体中显示的滑块控件")  
  
 字段现在显示为滑块控件，而不是文本字段。 

## <a name="use-the-editable-grid-control-on-a-view-or-sub-grid"></a>在视图或子网格上使用可编辑网格控件

通过可编辑网格，无论用户在使用 Web 应用、平板电脑还是手机，都可以直接从视图和子网格执行丰富的内嵌编辑。 详细信息：[使用可编辑网格自定义控件让网格（列表）可编辑](make-grids-lists-editable-custom-control.md) 
  
## <a name="next-steps"></a>后续步骤  
[创建和编辑字段](../common-data-service/create-edit-fields.md)
