---
title: Select 函数 | Microsoft Docs
description: Power Apps 中 Select 函数的参考信息（包括语法）
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 01/08/2020
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 12e0f7e33487d5a274dea8bf666ed7d539284e92
ms.sourcegitcommit: db62bf0f8210b5ba2d1d5fc2c7d362ab23ec8c63
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/22/2020
ms.locfileid: "76315414"
---
# <a name="select-function-in-power-apps"></a>Power Apps 中的 Select 函数
在控件上模拟选择操作，导致对 OnSelect  公式进行求值。

## <a name="description"></a>说明
Select  函数在控件上模拟选择操作，就像用户已单击或点击控件一样。 结果是，在目标控件上对 OnSelect  公式求值。

使用 Select  将选择操作传播到父控件。 此类型的传播是在库等位置的默认行为。 默认情况下，[库](../controls/control-gallery.md)  控件中的任何控件的 OnSelect  属性设置为 Select( Parent )  。 这样一来，你可以设置库控件本身的 OnSelect  属性的值，并将对该公式求值，无论用户在库中可能单击或点击哪个位置。

如果你希望库中的一个或多个控件从库本身执行不同的操作，请将这些控件的 OnSelect  属性设置为默认值以外的其他值。 如果你希望这些控件从库本身执行同一操作，可保留库中大部分控件的 OnSelect  属性的默认值。

Select  对目标 OnSelect  排队，以便以后进行处理，此操作可能在当前公式完成求值后执行。 Select  不会导致目标 OnSelect  立即求值，Select  也不会等待 OnSelect  完成求值。

不能跨屏幕使用 Select  。

只能对具有 OnSelect  属性的控件使用 Select  。

只能在[行为公式](../working-with-formulas-in-depth.md)中使用 Select  。

控件不能通过其他控件直接或间接使用 Select  。

Select 函数还可在图像库中使用。 例如，它可用来指定要在图像库中选定的行或列，或指定要在图像库的该行或该列中选定的控件。 选择某行或某列时，图像库所选内容将出现变化，并且对计算图像库控件上的 OnSelect 公式进行求值  。 如果提供了行或列中的控件，则对计算子控件的 OnSelect 公式进行求值  。 

## <a name="syntax"></a>语法
Select  （控件  ）

* *Control* – 必需。  代表用户进行选择的控件。

Select（控件、行或列、子控件）  

- *Control* – 必需。 代表用户进行选择的控件。
- 行或列 - 不需要  。 要代表用户在图像库控件中选择的行数或列数（从 1 开始）。
- 子控件 - 不需要  。 在要选择的“control”参数中标识的控件的子控件。 

## <a name="examples"></a>示例

- *按钮*

    ```Select(button1)```

- *库* 

    ```Select(Gallery1, 1)```

    模拟用户在图像库 1 中选择第 1 行或第 1 列的情况。 

- *库* 

    ```Select(Gallery1, 1, ChildControl1)```

    模拟用户在图像库 1 的第 1 行或第 1 列中选择 ChildConttrol1 的情况。

#### <a name="basic-usage"></a>基本用法

1. 添加一个[按钮](../controls/control-button.md)  控件，然后将其重命名为 Button1  （如果它具有不同名称）。

1. 将 Button1  的 OnSelect  属性设置为此公式：

    Notify( "Hello World" ) 

1. 在同一屏幕上添加第二个按钮  控件，并将其 OnSelect  属性设置为此公式：

    Select( Button1 ) 

1. 按住 Alt 键，并选择第二个按钮。

    将在你的应用的顶部出现一条通知。 Button1  的 OnSelect  属性生成了此通知。

    ![当单击第二个按钮时，将出现动画，显示两个按钮和通知的 OnSelect 属性设置](media/function-select/basic-select.gif)

#### <a name="gallery-control"></a>Gallery 控件

1. 添加含有其他控件的垂直 [Gallery](../controls/control-gallery.md)  控件。

    ![选择含有控件的垂直控件](media/function-select/select-gallery.png)

2. 将库的 OnSelect  属性设置为此公式：
 
    Notify( "Gallery Selected" ) 

3. 按住 Alt 键，并单击或点击库的背景或库中的任何控件。

    所有操作都将在应用顶部显示“库项已选”  的通知。

    使用库的 OnSelect  属性指定当用户单击或点击库中的项时要执行的默认操作。

5. 将图像控件的 OnSelect  属性设置为此公式：

    Notify( "Image Selected", Success ) 

6. 按住 Alt 键，并单击或点击库的各种元素。

    单击或点击库中除图像控件以外的任何控件时，将像以前一样显示库项已选  。 单击或点击图像时，将显示“图像已选”  。
 
    使用库中的单独控件执行与库的默认操作不同的操作。

    ![动画显示库控件的 OnSelect 属性的默认值，以及执行不同操作的控件。](media/function-select/gallery-select.gif)

7. 在相同屏幕上添加一个按钮控件，并将其 OnSelect 属性设置为此公式   ：

    **Select( Gallery1,2,Image1 )**

8. 按住 Alt 键，并选择按钮。
   
     你的应用的顶部将显示一则“已选择图像”通知  。 按钮单击模拟了在图像库的第 2 行中选择图像的情况。  

