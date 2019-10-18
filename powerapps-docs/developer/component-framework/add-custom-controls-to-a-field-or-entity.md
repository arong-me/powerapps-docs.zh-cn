---
title: 向字段或实体添加代码组件 |Microsoft Docs
description: 导入代码组件的过程
keywords: ''
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.openlocfilehash: 63ecdde21328219b70af04b9b65edbb3073f3025
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2019
ms.locfileid: "72347029"
---
# <a name="add-code-components-to-a-field-or-entity-in-model-driven-apps"></a>将代码组件添加到模型驱动应用中的字段或实体

代码组件允许将传统上包含文本的字段转换为可视化对象。 同样，您可以使用代码组件转换数据集（如视图）以更直观的方式显示，而不是记录列表。 代码组件可在窗体、面板、视图和主页网格上显示为可视化对象。 


   > [!div class="mx-imgBorder"] 
   > 字段的![自定义滑块控件](../../maker/model-driven-apps/media/slider-control.PNG "滑块控件")

## <a name="add-a-code-component-to-a-field"></a>向字段添加代码组件

按照此过程中的步骤，将 "**预算金额**" 字段的 "默认标签" 和 "文本框" 字段更改为 "机会" 实体上的 "滑块代码" 组件。 您可以使用类似的步骤将现有字段替换为代码组件或为自定义字段配置代码组件。

1. 打开解决方案资源管理器。

2. 展开 "**实体**"，展开所需的实体（例如 "**机会**" 实体），选择 "**窗体**"，然后打开窗体（如**主**窗体）。

3. 在窗体编辑器中，双击要在其中添加代码组件的字段，例如 "机会" 主窗体上的 "**预算量**" 字段。 或者，您也可以创建自定义字段。

4. 在 "**字段属性**" 页上，选择 "**控件**" 选项卡，然后选择 "**添加控件**"。

5. 在 "添加控件" 页上，选择所需的组件，如**线性滑块**组件，然后选择 "**添加**"。

   > [!div class="mx-imgBorder"] 
   > ![添加线性滑块控件](../../maker/model-driven-apps/media/add-slider.PNG "添加线性滑块控件")

6. 选择要在其中显示组件的客户端。

   - **Web**。 若要从任何 web 浏览器中使用代码组件，请选择该组件旁边的 "Web" 选项。 请注意，设置 "Web" 选项包括在电脑、Mac 和移动设备上的 Web 浏览器中呈现组件。

   - **手机**。 若要使代码组件在运行 Dynamics 365 for 手机的手机上可用，请选择该组件旁边的 "电话" 选项。

   - **Tablet**。 若要使代码组件在运行 Dynamics 365 的平板电脑设备上可用，请选择该组件旁边的 "Tablet" 选项。

   > [!div class="mx-imgBorder"] 
   > ![选择客户端应用以查看自定义控件](../../maker/model-driven-apps/media/choose-client.png "选择客户端应用以查看自定义控件") 

7. 选择 "**最小值**"、"**最大值**" 和 "**步骤**" 旁边的铅笔图标，设置 "属性" 选项，然后选择 **"确定"** 。  
   
   > [!div class="mx-imgBorder"] 
   > ![添加自定义控件属性](../../maker/model-driven-apps/media/ccf-add-properties.png "添加自定义控件属性")

   - **最小值** 设置最小接受值。 可以绑定输入的静态值，也可以将值绑定到现有字段。 在此示例中，**绑定到 static 值**为**Currency** ，可输入的最小值为*零*。  
  
       - **绑定到静态值**。 选择数据类型，例如整数（全值）、货币、浮点（FP）或小数。 接下来，输入一个数字，表示该字段接受的最小值。  
  
       - **绑定到字段的值**。 从列表中选择将用作最小接受值的字段。  
  
   - **最大值**。 为该字段设置最大接受值。 与最小值类似，可以将输入的静态值或绑定到现有字段的值绑定到前面所述的现有字段。 在此示例中，**绑定到静态值**是**货币**，可输入的最大值为**1000000000**。  
  
   - **步骤**。 这表示在添加或减去当前值时要递增或递减的单位。 例如，对于预算金额，可以选择100美元 increments\decrements。  
  
   - **隐藏默认控件**。 选择此选项将隐藏组件，因此不支持代码组件的任何客户端都不会显示组件或数据。   
  
8. 选择 **"确定"** ，关闭 "字段属性" 页。  
  
9. 若要激活自定义项，请在实体窗体上选择 "**保存**"，然后选择 "**发布**"。  
  
10. 选择 "**保存并关闭**" 以关闭窗体编辑器。  
  
## <a name="add-code-component-to-an-entity"></a>向实体添加代码组件

若要将代码组件（如数据集组件或简单表组件）添加到网格或视图，请执行以下步骤：

  - 导航到 "**设置" > "自**定义"，然后单击 "**自定义系统"** 。
  - 单击 "**实体**" 选项卡旁边的箭头，选择要添加代码组件的实体。 
  - 单击 "**控件**" 选项卡，然后单击 "**添加控件**"。
  - 在 "添加控件" 页上，选择所需的组件，如 "简单表组件"，然后选择 "**添加**"。
  - 选择要在其中显示组件的客户端。


## <a name="see-the-code-component-in-action"></a>请参阅操作中的代码组件  

 打开包含包含代码组件的字段的记录，例如上一示例中的商机窗体，并查看如何更改字段。 该字段现在呈现为滑块组件而不是文本字段。  

> [!div class="mx-imgBorder"] 
> 呈现在窗体上的窗体(../../maker/model-driven-apps/media/slider-control.PNG "滑块控件")![上的滑块控件]  

### <a name="see-also"></a>另请参阅

[在 TypeScript 中实现组件](implementing-controls-using-typescript.md)<br/>
[PowerApps 组件框架 API 参考](reference/index.md)<br/>
[PowerApps 组件框架概述](overview.md)