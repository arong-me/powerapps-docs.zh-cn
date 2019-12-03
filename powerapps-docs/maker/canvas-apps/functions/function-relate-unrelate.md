---
title: 关联和取消与函数 |Microsoft Docs
description: 有关 Power Apps 中的关联和取消与函数的参考信息（包括语法和示例）
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 01/22/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: e2b1d0e8ab264b9576c18aa7d5803be30c4a45e1
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74730551"
---
# <a name="relate-and-unrelate-functions-in-power-apps"></a>Power Apps 中的关联和取消与函数

通过一对多或多对多关系对两个实体的记录进行关联和取消与。

## <a name="description"></a>描述

**关联**函数通过 Common Data Service 中的一对多或多对多关系来链接两个记录。 **取消与**函数将反转进程并删除链接。

对于一对多关系，多个实体具有一个外键字段，该字段指向一个实体的记录。 **相关**设置此字段，使其指向一个实体的特定记录，而**取消与**将此字段设置为*空*。 如果在调用 "**关联**" 时已设置该字段，则会丢失现有链接，以支持新链接。 还可以通过使用[**Patch**](function-patch.md)函数或 **[编辑窗体](../controls/control-form-detail.md)** 控件来设置此字段;不需要使用 "**关联**函数"。

对于多对多关系，链接记录的系统会维护隐藏的联接表。 不能直接访问此联接表;它只能通过一对多投影进行读取，并通过 "**关系**" 和 "**取消与**" 函数进行设置。 相关实体都没有外键。

将刷新在第一个参数中指定的实体的数据以反映更改，但在第二个参数中指定的实体的数据将不会进行刷新。 必须用 **[Refresh](function-refresh.md)** 函数手动刷新这些数据以显示操作的结果。

这些函数绝不会创建或删除记录。 它们仅关联或取消与已存在的两个记录。

只能在[行为公式](../working-with-formulas-in-depth.md)中使用这些函数。

> [!NOTE]
> 这些函数是预览功能的一部分，并且仅当启用了 "**关系数据"、"选项集" 和 "适用于 cd 的其他新功能**" 功能时，它们的行为才可用。 这是默认情况下为新应用启用的应用级别设置。 若要查找此功能，请打开 "**文件**" 菜单，选择 "**应用设置**"，然后选择 "**高级设置**"。 你的反馈对我们非常有用-请告诉我们你在[Power Apps 社区论坛](https://powerusers.microsoft.com/t5/Expressions-and-Formulas/bd-p/How-To)中的看法。

## <a name="syntax"></a>语法

**关联**（ *Entity1RelatedTable*， *Entity2Record* ）

* *Entity1RelatedTable* -必需。 对于*Entity1*的记录，则为通过一对多或多对多关系相关的*Entity2*记录表。
* *Entity2Record* -必需。 要添加到关系的*Entity2*记录。

**取消与**（ *Entity1RelatedTable*， *Entity2Record* ）

* *Entity1RelatedTable* -必需。 对于*Entity1*的记录，则为通过一对多或多对多关系相关的*Entity2*记录表。
* *Entity2Record* -必需。 要从关系中移除的*Entity2*记录。

## <a name="examples"></a>示例

请考虑具有以下关系的 "**产品**" 实体，如[Power Apps 门户的实体查看器](../../common-data-service/create-edit-entities-portal.md)中所示：

| 关系显示名称 | 相关实体 | 关系类型 |
| --- | --- |
| 产品预订 | 预约 | 一对多 |
| 产品 &harr; 联系 | 联系人 | 多对多 |

**产品**和**预订**通过一对多关系进行关联。  将**预订**实体的第一条记录与**Products**实体的第一条记录相关联：

`Relate( First( Products ).Reservations, First( Reservations ) )`

删除这些记录之间的关系：

`Unrelate( First( Products ).Reservations, First( Reservations ) )`

无论何时创建或删除记录，都只修改记录之间的关系。

**产品**和**联系人**通过多对多关系进行相关。  将**Contacts**实体的第一条记录与**Products**实体的第一条记录相关联：

`Relate( First( Products ).Contacts, First( Contacts ) )`

因为多对多关系是对称的，所以我们还可以按照相反方向完成此操作：

`Relate( First( Contacts ).Products, First( Products ) )`

删除这些记录之间的关系：

`Unrelate( First( Products ).Contacts, First( Contacts ) )`

或

`Unrelate( First( Contacts ).Products, First( Products ) )`

下面的演练通过使用具有**库**和**组合框**控件的应用程序对这些实体执行这些操作，以选择所涉及的记录。

这些示例取决于在您的环境中安装的示例数据。 [创建包含示例数据的试用环境](../../model-driven-apps/overview-model-driven-samples.md#get-sample-apps)或[向现有环境中添加示例数据](../../model-driven-apps/overview-model-driven-samples.md#install-or-uninstall-sample-data)。

### <a name="one-to-many"></a>一对多

#### <a name="relate-function"></a>**相关**函数

首先，将创建一个简单的应用来查看和重新分配与产品关联的预订。

1. [从空白创建平板电脑应用](../data-platform-create-app-scratch.md)。

1. 在“视图”选项卡上，选择“数据源”。

1. 在 "**数据**" 窗格中，选择 "**添加数据源**" > **Common Data Service** > **产品**" > **连接**"。  

    Products 实体是上面加载的示例数据的一部分。

     ![将 Products 实体添加为数据源](media/function-relate-unrelate/products-connect.png)

1. 在 "**插入**" 选项卡上，添加一个空白垂直 **[库](../controls/control-gallery.md)** 控件。

1. 确保刚刚添加的控件名为**gallery1.selected**，然后移动它并调整其大小，以填充屏幕的左侧。

1. 在 "**属性**" 选项卡上，将 " **Gallery1.selected**" 的**Items**属性设置为 "**产品**"，并将其 "**布局**"**设置为**

    ![配置 ProductsGallery](media/function-relate-unrelate/products-gallery.png)

1. 在**gallery1.selected**中，确保将 "**标签**" 控件命名为 " **Title1**"，然后将 " **Text** " 属性设置为 " **ThisItem.Name**"。

    ![在 Gallery1.selected 中配置标签](media/function-relate-unrelate/products-title.png)

1. 选择屏幕以避免将下一项插入**gallery1.selected**。  添加第二个空白垂直**库**控件，并确保其命名为**Gallery2**。

    **Gallery2**将显示用户在**gallery1.selected**中选择的任何产品的预留。

1. 移动**Gallery2**并调整其大小，以填充屏幕的右上象限。

1. 可有可无按下图所示，在**Gallery2**上方添加蓝色**标签**控件。

1. 在编辑栏中，将 " **Gallery2** " 的 " **Items** " 属性设置为 " **gallery1.selected**"。

    ![配置 Gallery2 项](media/function-relate-unrelate/reservations-gallery.png)

1. 在 "属性" 窗格中，将**Gallery2**的 "**布局**" 设置为 "**标题**"。

    ![配置 Gallery2 布局](media/function-relate-unrelate/reservations-gallery-right.png)

1. 在**Gallery2**中，添加一个 **[组合框](../controls/control-combo-box.md)** 控件，确保它名为**combobox1.location**，然后移动并调整其大小，以避免阻止**Gallery2**中的其他控件。

1. 在 "**属性**" 选项卡上，将 " **Combobox1.location**" 的**Items**属性设置为**Products**。

    ![将 Items 属性设置为 Products](media/function-relate-unrelate/reservations-combo-right.png)

1. 在 "**属性**" 选项卡中向下滚动，并将 " **combobox1.location**"**允许多重选择**属性设置为**Off**。

    ![将 "允许多个选择" 设置为 "关闭"](media/function-relate-unrelate/reservations-singleselect-right.png)

1. 在编辑栏中，将**combobox1.location**的 " **DefaultSelectedItems** " 属性设置为 **"ThisItem**"。

    ![为 ReserveCombo 设置 DefaultSelectedItems](media/function-relate-unrelate/reservations-combo.png)

1. 在**Gallery2**中，将**NextArrow2**的**OnSelect**属性设置为以下公式：

    ```powerapps-dot
    Relate( ComboBox1.Selected.Reservations, ThisItem )
    ```

    当用户选择此图标时，当前预订将更改用户在**combobox1.location**中选择的产品。

    ![配置 NextArrow2](media/function-relate-unrelate/reservations-relate.png)

1. 按 F5 在预览模式下测试应用程序。

使用此应用，用户可以将预订从一个产品移到另一个产品。 对于一个产品的预订，用户可在**combobox1.location**中选择另一产品，然后选择 " **NextArrow2** " 以更改该预订。

![演示一对多应用中的关联函数](media/function-relate-unrelate/reservations-reassign.gif)

#### <a name="unrelate-function"></a>**取消与**函数

此时，您可以将关系从一条记录移动到另一条记录，但无法完全删除该关系。 您可以使用**取消与**函数从任何产品断开预订记录。

1. 在“视图”选项卡上，选择“数据源”。

1. 在 "**数据**" 窗格中，选择 "**添加数据源**" > **Common Data Service** > **保留** > **连接**"。

1. 在**Gallery2**中，将**NextArrow2**的**OnSelect**公式设置为以下公式：

    ```powerapps-dot
    If( IsBlank( ComboBox1.Selected ),
        Unrelate( Gallery1.Selected.Reservations, ThisItem ),
        Relate( ComboBox1.Selected.Reservations, ThisItem )
    );
    Refresh( Reservations )
    ```
    ![配置右侧图标](media/function-relate-unrelate/reservations-relate-unrelate.png)

1. 通过选择并按 Ctrl-c，将**Gallery2**复制到剪贴板。

1. 按下 Ctrl + V，将**Gallery2**的副本粘贴到同一屏幕上，然后将其移动到屏幕右下方。

1. 可有可无如果在**Gallery2**上添加标签，请对该标签重复前面两个步骤。

1. 确保**Gallery2**的副本名为**Gallery2_1**，然后将其**Items**属性设置为以下公式：

    ```powerapps-dot
    Filter( Reservations, IsBlank( 'Product Reservation' ) )
    ```

    此时将显示委托警告，但在此示例中，这并不重要。

    ![设置 Gallery2_1 的 Items 属性](media/function-relate-unrelate/reservations-lost.png)

进行这些更改后，用户可以清除联系人的**combobox1.location**中的选定内容（如果此人未保留产品）。 未预订产品的联系人将显示在**Gallery2_1** ，用户可在其中将每个联系人分配给产品。

   ![演示一对多应用中的关联和取消与函数](media/function-relate-unrelate/reservations-lostandfound.gif)

### <a name="many-to-many"></a>多对多

#### <a name="create-a-many-to-many-relationship"></a>创建多对多关系

示例数据不包含多对多关系，但您将在 Products 实体和 Contacts 实体之间创建一个。 用户可以将每个产品与多个联系人和每个联系人关联到多个产品。

1. 在[此页](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)上，在左侧导航栏中选择 "**数据**"，然后选择 "**实体**"。

    ![打开实体列表](media/function-relate-unrelate/entity-list.png)

1. 更改实体筛选器以包括所有实体。

    默认情况下，不显示示例实体。

    ![删除实体筛选器](media/function-relate-unrelate/entity-all.png)

1. 向下滚动，打开 "**产品**" 实体，然后选择 "**关系**"。

    ![Product 实体的 "关系" 选项卡](media/function-relate-unrelate/entity-relationships.png)

1. 选择 "**添加关系** > **多对多**"。

    ![添加多对多关系](media/function-relate-unrelate/entity-manytomany.png)

1. 选择关系的 "**联系人**" 实体。

    ![选择 "联系人" 实体](media/function-relate-unrelate/entity-contact.png)

1. 选择 "**完成**" > "**保存实体**"。

    !["产品" 实体的列表](media/function-relate-unrelate/entity-done.png)

#### <a name="relate-and-unrelate-contacts-with-one-or-more-products"></a>与一个或多个产品关联和取消与联系人

你将创建一个类似于你之前在本主题中创建的应用，但新的应用将提供多对多的关系。 每个联系人都可以保留多个产品，而不是只保留一个。

1. 在平板电脑的空白应用程序中，创建**gallery1.selected** ，如本主题中的[第一个过程](#one-to-many)所述。

1. 添加另一个空白垂直**库**控件，确保其命名为**Gallery2**，然后将其移到屏幕的右上角。

    稍后在本主题中，你将在**Gallery2**下添加一个**组合框**控件。

1. 在编辑栏中，将 " **Gallery2**" 的**Items**属性设置为 " **gallery1.selected**"。

    ![配置 ContactsGallery](media/function-relate-unrelate/contacts-gallery.png)

1. 在 "**属性**" 选项卡上，将 "**布局**" 设置为 "**图像和标题**"。

    ![配置 ContactsGallery](media/function-relate-unrelate/contacts-gallery-right.png)

1. 在**Gallery2**中，确保将 "**标签**" 控件命名为 " **Title2**"，然后将 " **Text** " 属性设置为 **"ThisItem**"。

    在完成此过程并将联系人分配给产品之前，该控件中将不会显示任何文本。

    ![显示联系人姓名](media/function-relate-unrelate/contacts-title.png)

1. 删除**NextArrow2**，插入 "**取消**" 图标，并确保其命名为 " **icon1**"。

1. 将 "**取消**" 图标的 " **OnSelect** " 属性设置为以下公式： 

    ```powerapps-dot
    Unrelate( Gallery1.Selected.Contacts, ThisItem )
    ```

    ![配置 "取消" 图标](media/function-relate-unrelate/contacts-unrelate.png)

1. 在“视图”选项卡上，选择“数据源”。

1. 在 "**数据**" 窗格中，选择 "**添加数据源**" > **Common Data Service** > **联系人** > **连接**"。

1. 在**Gallery2**下，添加一个**组合框**控件，确保它名为**Combobox1.location**，然后将其**Items**属性设置为**Contacts**。

    ![配置组合框项属性](media/function-relate-unrelate/contacts-combo.png)

1. 在 "**属性**" 选项卡上，将 "**允许多选**" 设置为 "**关闭**"。

    ![配置组合框布局属性](media/function-relate-unrelate/contacts-combo-right.png)

1. 插入 "**添加**" 图标，并将其 " **OnSelect** " 属性设置为以下公式： 

    ```powerapps-dot
    Relate( Gallery1.Selected.Contacts, ComboBox1.Selected )
    ```

    ![配置添加图标](media/function-relate-unrelate/contacts-relate.png)

使用此应用，用户现在可以为每个产品自由关联和取消与一组联系人。

- 若要将联系人添加到产品，请在屏幕底部的组合框中选择 "联系人"，然后选择 "**添加**" 图标。
- 若要从产品中删除联系人，请选择该联系人的 "**取消**" 图标。

    与一对多不同，多对多关系允许用户将同一联系人与多个产品关联。

![演示多对多应用中的关联和取消与函数](media/function-relate-unrelate/contacts-relate-unrelate.gif)

#### <a name="in-reverse-relate-and-unrelate-products-with-multiple-contacts"></a>相反：将产品与多个联系人关联和取消与

多对多关系为对称关系。 您可以扩展该示例以将产品添加到联系人，然后在这两个屏幕之间切换，以显示从任一方向显示该关系的方式。

1. 将**Screen1**的**OnVisible**属性设置为**Refresh （Products）** 。

    更新一对多或多对多关系时，仅刷新**关联**或**取消与**调用的第一个参数实体中的数据。 如果要在此应用程序的屏幕之间切换，则必须手动刷新第二个。

    ![将 OnVisible 属性设置为 Refresh function](media/function-relate-unrelate/contacts-refresh.png)

1. 重复的**Screen1**。

    该副本将命名为 " **Screen1_1** "，并构成从 "联系人" 端查看关系的基础。

    ![复制屏幕](media/function-relate-unrelate/contacts-duplicate.png)

1. 若要创建反向视图，请在**Screen1_1**的控件上更改这些公式：

    - Screen1_1 OnVisible = `Refresh( Contacts )`
    - Gallery1_1 Items = `Contacts`
    - Title1_1。 Text = `ThisItem.'Full Name'`
    - Label1_1。 Text = `"Selected Contact Products"`
    - Gallery2_1 Items = `Gallery1_1.Selected.Products`
    - Title2_1。 Text = `ThisItem.Name`
    - Icon1_1 OnSelect = `Unrelate( Gallery1_1.Selected.Products, ThisItem )`
    - ComboBox1_1 Items = `Products`
    - Icon2_1 OnSelect = `Relate( Gallery1_1.Selected.Products, ComboBox1_1.Selected )`

    结果看起来非常类似于上一个屏幕，但会出现在与**联系人**端的关系上。

    ![显示从联系人开始的多对多关系](media/function-relate-unrelate/reverse-screen.png)

1. **向下插入箭头**图标，并将其**OnSelect**属性设置为 **"导航" （Screen1，"无"）** 。  用公式**导航（Screen1_1、无）** 对**Screen1**执行相同的操作。

    ![在屏幕之间添加导航](media/function-relate-unrelate/reverse-navigate.png)

使用此新屏幕，用户可以将联系人添加到产品，然后翻到联系人视图，并查看关联的产品。 关系是对称的，在这两个屏幕之间共享。

![从任一侧演示多对多关系](media/function-relate-unrelate/contacts-reverse.gif)
