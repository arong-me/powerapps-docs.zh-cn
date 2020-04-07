---
title: Remove 和 RemoveIf 函数 | Microsoft 文档
description: Power Apps 中 Remove 和 RemoveIf 函数的参考信息（包括语法和示例）
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/02/2020
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: bddce14842d111757859b836c0137b35111805d1
ms.sourcegitcommit: 49b69129262a9b530e69508e84c3822b742066df
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/07/2020
ms.locfileid: "80760145"
---
# <a name="remove-and-removeif-functions-in-power-apps"></a>在 Power Apps 中删除和 RemoveIf 函数
从[数据源](../working-with-tables.md#records)删除[记录](../working-with-data-sources.md)。

## <a name="description"></a>说明
### <a name="remove-function"></a>Remove 函数
使用 **Remove** 函数从数据源中删除特定的一个或多个记录。  

对于[集合](../working-with-data-sources.md#collections)来说，整个记录必须匹配。 可以使用 **All** 参数删除某个记录的所有副本；否则只会删除记录的一个副本。

### <a name="removeif-function"></a>RemoveIf 函数
使用 **RemoveIf** 函数根据一个或一组条件删除一个或多个记录。 每个条件都可以是其结果为 **true** 或 **false** 的任意公式，并且可以通过名称引用数据源的[列](../working-with-tables.md#columns)。 将会针对每个记录单独评估每个条件，如果所有条件的评估结果为 **true**，则会删除该记录。

**Remove** 和 **RemoveIf** 都以[表](../working-with-tables.md)的形式返回修改的数据源。 只能在[行为公式](../working-with-formulas-in-depth.md)中使用这两个函数。

还可使用 **[Clear](function-clear-collect-clearcollect.md)** 函数删除数据源中的所有记录。

### <a name="delegation"></a>委派
[!INCLUDE [delegation-no](../../../includes/delegation-no.md)]

## <a name="syntax"></a>语法
**Remove**( *DataSource*, *Record1* [, *Record2*, ... ] [, **All** ] )

* *DataSource* - 必需。 数据源，其中包含要删除的一个或多个记录。
* *Record(s)* - 必需。 要删除的一个或多个记录。
* **All** - 可选。 在集合中，同一记录可能出现多次。  添加 **All** 参数即可删除记录的所有副本。

**Remove**( *DataSource*, *Table* [, **All** ] )

* *DataSource* - 必需。 数据源，其中包含要删除的记录。
* *Table* - 必需。 要删除的记录表。
* **All** - 可选。 在集合中，同一记录可能出现多次。  添加 **All** 参数即可删除记录的所有副本。

**RemoveIf**( *DataSource*, *Condition* [, ... ] )

* *DataSource* - 必需。 数据源，其中包含要删除的一个或多个记录。
* *Condition(s)* - 必需。 一个公式，对于要删除的一个或多个记录，该公式的求值结果为 **true**。  可以在公式中使用 *DataSource* 中的列名。  如果指定多个 Conditions，则所有 Conditions 的求值结果都必须为 **true**，然后才能删除一个或多个记录。

## <a name="examples---single-formulas"></a>示例-单个公式

在以下示例中，你将删除某个数据源中的一个或多个记录。该数据源名为 **IceCream** 且以下表中的数据开头：

![](media/function-remove-removeif/icecream.png)

#### <a name="create-a-collection-with-sample-records"></a>创建包含示例记录的集合

使用以下数据创建集合：

1. 插入[**按钮**](../controls/control-button.md)控件。
1. 将按钮控件的**OnSelect**属性设置为以下公式：

    ```powerapps-dot
    ClearCollect( IceCream,
                  { ID: 1, Flavor: "Chocolate",  Quantity: 100 },
                  { ID: 2, Flavor: "Vanilla",    Quantity: 200 },
                  { ID: 3, Flavor: "Strawberry", Quantity: 300 }
    )
    ```
1. [按住 Alt 键的同时](../keyboard-shortcuts.md#alternate-behavior)选择该按钮：


#### <a name="remove-sample-records-from-collection-using-a-formula"></a>使用公式从集合中删除示例记录

| 公式 | 说明 | 结果 |
| --- | --- | --- |
| **Remove(&nbsp;IceCream,<br>First(&nbsp;Filter(&nbsp;IceCream,&nbsp;Flavor="Chocolate"&nbsp;)&nbsp;) )** |从数据源中删除 **Chocolate** 记录。 |<style>img {最大宽度：无}</style> ![](media/function-remove-removeif/icecream-no-chocolate.png)<br><br>修改了 **IceCream** 数据源。 |
| **Remove(&nbsp;IceCream,<br>First(&nbsp;Filter(&nbsp;IceCream,&nbsp;Flavor="Chocolate"&nbsp;)&nbsp;) First(&nbsp;Filter(&nbsp;IceCream,&nbsp;Flavor="Strawberry"&nbsp;)&nbsp;) )** |从数据源中删除两个记录。 |![](media/function-remove-removeif/icecream-only-vanilla.png)<br><br>修改了 **IceCream** 数据源。 |
| **RemoveIf(&nbsp;IceCream, Quantity&nbsp;>&nbsp;150 )** |删除其 **Quantity** 大于 **150** 的记录。 |![](media/function-remove-removeif/icecream-only-chocolate.png)<br><br>修改了 **IceCream** 数据源。 |
| **RemoveIf(&nbsp;IceCream, Quantity&nbsp;>&nbsp;150, Left(&nbsp;Flavor,&nbsp;1&nbsp;) = "S" )** |删除其 **Quantity** 大于 150 且 **Flavor** 以 **S** 开头的记录。 |![](media/function-remove-removeif/icecream-no-strawberry.png)<br><br><br>修改了 **IceCream** 数据源。 |
| **RemoveIf(&nbsp;IceCream, true )** |从数据源中删除所有记录。 |![](media/function-remove-removeif/icecream-empty.png)<br><br>修改了 **IceCream** 数据源。 |

## <a name="examples---remove-button-outside-a-gallery"></a>示例-删除库外部的按钮

在此示例中，您将使用[**库**控件](../controls/control-gallery.md)列出表中的记录。 然后使用**Remove**函数有选择地删除项。  

### <a name="prepare-for-sample-data"></a>准备示例数据

此示例使用 Common Data Service 中的 "**联系人**" 实体*以及示例应用和数据*。 你可以在[创建环境](https://docs.microsoft.com/power-platform/admin/create-environment#create-an-environment-with-a-database)时部署*示例应用和数据*。 您还可以改用任何其他数据源。

### <a name="remove-button-outside-a-gallery"></a>删除库外的按钮

在此示例中，您将使用库外的*按钮*删除项。

1. 使用手机布局创建[新的空白画布应用](../data-platform-create-app-scratch.md)。

    ![使用手机布局的空白画布应用](media/function-remove-removeif/gallery-new.png)

1. 从左窗格中选择 "**插入**"。

1. 选择 "**垂直库**"。 <br>
    **库**控件将添加到屏幕中。

    ![使用 "插入工具" 窗格添加垂直库控件](media/function-remove-removeif/gallery-add.png)

1. 系统将提示您选择一个数据源，您可以从中选择可用数据源中的数据源。 <br>
    例如，选择 "**联系人**" 实体以使用*示例数据*：  

    ![选择要在库中显示的 "联系人" 实体](media/function-remove-removeif/gallery-datasource.png)

    库将显示此实体中的项： 

    ![添加的库显示联系人实体](media/function-remove-removeif/gallery-data.png)

1. 从左窗格中插入[**按钮**](../controls/control-button.md)控件：
    
    ![使用 "插入工具" 窗格添加按钮控件](media/function-remove-removeif/gallery-addbutton.png)

1. 将添加的按钮移动到库项下面：

    ![移动按钮](media/function-remove-removeif/move-button-down.png)

1. 更新按钮文本属性以*删除记录*。 你还可以使用所选文本：

    ![重命名按钮](media/function-remove-removeif/button-text.png)

1. 将此按钮控件的**OnSelect**属性设置为以下公式：

    ```powerapps-dot
    Remove( Contacts, Gallery1.Selected )
    ```

    ![设置按钮控件的 OnSelect 属性](media/function-remove-removeif/gallery-button-onselect.png)

    库控件使用**所选**属性使当前选定的记录可用。 **删除**函数引用此选定记录以将其删除。

1. 使用右上方的 "*播放*" 按钮预览应用，或按键盘上的*F5* ：

    ![预览应用](media/function-remove-removeif/preview-app.png)

1. 选择要删除的记录，如本示例中的*南希*记录：

    ![选择记录](media/function-remove-removeif/select-nancy-record.png)

1. 选择**删除记录**：

    ![现在没有已删除的张颖记录的联系人库](media/function-remove-removeif/gallery-activatebutton.png)

    选择该按钮将删除所选记录（在本示例中为南希）。

1. 关闭应用预览。

    > [!TIP]
    > 你还可以将备用行为用于[*Alt 键*](../keyboard-shortcuts.md#alternate-behavior)，而不是使用 "*播放*" 按钮或*F5*的应用预览。

## <a name="examples---trash-can-icon-inside-a-gallery"></a>示例-库中的垃圾桶图标

在此示例中，将使用放置在库中的*图标*来删除项。

### <a name="create-a-collection-with-sample-data"></a>使用示例数据创建集合

如果已[准备好示例数据](#prepare-for-sample-data)，请跳过此步骤，并转到[库中的 "垃圾桶" 图标](#trash-can-icon-inside-a-gallery)。

1. 向屏幕中添加一个[**按钮**](../controls/control-button.md)控件。
1. 将 **“OnSelect”** 属性设置为以下公式：

    ```powerapps-dot
    ClearCollect( SampleContacts, 
          { 'Full Name': "Yvonne McKay (sample)",      'Primary Email': "someone_a@example.com" },
          { 'Full Name': "Susanna Stubberod (sample)", 'Primary Email': "someone_b@example.com" },
          { 'Full Name': "Nancy Anderson (sample)",    'Primary Email': "someone_c@example.com" },
          { 'Full Name': "Maria Campbell (sample)",    'Primary Email': "someone_d@example.com" },
          { 'Full Name': "Robert Lyon (sample)",       'Primary Email': "someone_e@example.com" },
          { 'Full Name': "Paul Cannon (sample)",       'Primary Email': "someone_f@example.com" },
          { 'Full Name': "Rene Valdes (sample)",       'Primary Email': "someone_g@example.com" } 
    )
    ```
1. [按住 Alt 键的同时](../keyboard-shortcuts.md#alternate-behavior)选择该按钮。

将创建示例集合，可以在下面的示例中使用该集合。

### <a name="trash-can-icon-inside-a-gallery"></a>库中的垃圾桶图标

1. 使用手机布局创建[新的空白画布应用](../data-platform-create-app-scratch.md)。

    ![使用手机布局的空白画布应用](media/function-remove-removeif/gallery-new.png)

1. 从左窗格中选择 "**插入**"。

1. 选择 "**垂直库**"。 <br>
    **库**控件将添加到屏幕中。

    ![使用 "插入工具" 窗格添加垂直库控件](media/function-remove-removeif/gallery-add.png)

1. 系统将提示您选择一个数据源，您可以从中选择可用数据源中的数据源。 <br>
    例如，选择 "**联系人**" 实体以使用*示例数据*：  

    ![选择要在库中显示的 "联系人" 实体](media/function-remove-removeif/gallery-datasource.png)

    如果已创建[集合](#create-a-collection-with-sample-data)，请改为选择集合：

    ![示例联系人集合](media/function-remove-removeif/sample-contacts.png)

1. 选择库中顶部项内的控件。 <br>
    
    若要确保下一步将项插入库的模板而不是库的外部，请确保在继续下一步之前执行此步骤。
    
    ![选择库中的顶部记录](media/function-remove-removeif/gallery-select-template.png)

1. 从左窗格中选择 "**添加图标**"。 <br>
    
    ![使用 "插入工具" 窗格添加图标控件](media/function-remove-removeif/gallery-addicon.png)

    > [!NOTE]
    > **添加图标**在库的左侧插入 **+** 图标，为库中的每个项复制。 

1. 在顶部项中，将图标移到屏幕的右侧。

    ![“移动”图标](media/function-remove-removeif/move-icon.png)

1. 选择图标的**图标**属性，并将其设置为以下公式，以将图标图像更新为垃圾桶图标：

    ```powerapps-dot 
    Icon.Trash
    ```
    
    > [!NOTE]
    > **图标。** 只有在主动编辑公式时才会显示前缀。

    ![将图标更改为垃圾桶图标](media/function-remove-removeif/gallery-icontrash.png)

1. 将 **“OnSelect”** 属性设置为以下公式：

    ```powerapps-dot
    Remove( [@Contacts], ThisItem )
    ```

    > [!NOTE]
    > 必须使用[全局歧义消除运算符](operators.md#disambiguation-operator) **[@** ... **]** 在本示例中，示例数据使用*Contacts*实体来避免与*一对多关系冲突*。 如果使用数据源（例如 SharePoint 列表或 SQL Server 表），则不需要使用*global disambgulation 运算符*。

    ![垃圾桶图标的 OnSelect](media/function-remove-removeif/gallery-onselect.png)

1. 使用右上方的 "*播放*" 按钮预览应用，或按键盘上的*F5* 。

1. 选择记录旁边的垃圾桶图标，例如*Maria*的：

    ![已删除其中一个联系人的库](media/function-remove-removeif/gallery-activateicon.png)

    记录已删除：

    ![删除的记录](media/function-remove-removeif/deleted-record.png)

1. 关闭应用预览。
