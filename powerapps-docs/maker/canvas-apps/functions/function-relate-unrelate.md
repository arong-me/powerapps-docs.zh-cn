---
title: 关联和取消关联时要函数 |Microsoft Docs
description: 引用信息，包括语法和示例，用于建立关系，并取消关联时要在 PowerApps 中的函数
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 01/22/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 4b2c6b9518e987ef17f2ff2b50987568c8a0b69f
ms.sourcegitcommit: 5b2b70c3fc7bcba5647d505a79276bbaad31c610
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/22/2019
ms.locfileid: "58356761"
---
# <a name="relate-and-unrelate-functions-in-powerapps"></a>关联和取消关联时要在 PowerApps 中的函数

关联和取消关联时要通过一个对多或多对多关系的两个实体的记录。

## <a name="description"></a>描述

**Relate**函数链接通过 Common Data Service 中的一个多或多对多关系的两条记录。 **Unrelate**函数可回退该过程并删除该链接。

对于一个对多关系，多个实体具有外键字段指向一条记录的一个实体。 **与相关**设置为指向特定记录的一个实体，此字段时**Unrelate**将此字段设置为*空白*。 如果该字段已设置何时**Relate**是调用，现有的链接是丢失以支持新的链接。 此外可以通过设置此字段[**修补**](function-patch.md)函数或**[编辑窗体](../controls/control-form-detail.md)** 控制; 您无需使用**建立关系**函数。

对于多对多关系，请将这些记录链接的系统维护的隐藏的联接表。 不能直接调用访问此联接表它可以仅通过一个多投影读取数据并通过设置**Relate**并**Unrelate**函数。 都不相关的实体具有外键。

在第一个参数中指定的实体的数据将刷新以反映此更改，但不会在第二个参数中指定的实体的数据。 数据必须进行手动刷新**[刷新](function-refresh.md)** 函数来显示操作的结果。

这些函数永远不会创建或删除一条记录。 它们仅相关或取消键已存在的两条记录。

可以使用这些函数仅在[行为公式](../working-with-formulas-in-depth.md)。

> [!NOTE]
> 这些函数均属于一项预览功能，且其行为时才可用**关系数据、 选项集和其他新功能针对 CDS**启用功能。 这是默认情况下，为新应用程序启用应用程序级设置。 若要查找此功能切换，请打开**文件**菜单中，选择**应用程序设置**，然后选择**高级设置**。 你的反馈对我们非常重要，请通过 [PowerApps 社区论坛](https://powerusers.microsoft.com/t5/Expressions-and-Formulas/bd-p/How-To)提供反馈。

## <a name="syntax"></a>语法

**Relate**( *Entity1RelatedTable*, *Entity2Record* )

* *Entity1RelatedTable* -必需。 记录*Entity1*的表*Entity2*通过一个对多或多对多关系相关的记录。
* *Entity2Record* -必需。 *Entity2*记录将添加到此关系。

**Unrelate**( *Entity1RelatedTable*, *Entity2Record* )

* *Entity1RelatedTable* -必需。 记录*Entity1*的表*Entity2*通过一个对多或多对多关系相关的记录。
* *Entity2Record* -必需。 *Entity2*要从关系中删除记录。

## <a name="examples"></a>示例

请考虑**产品**具有以下关系中所示实体[PowerApps 门户实体查看器](../../common-data-service/create-edit-entities-portal.md):

| 关系显示名称 | 相关的实体 | 关系类型 |
| --- | --- |
| 产品保留项 | 保留项 | 一个对多 |
| 产品&harr;联系人 | 联系人 | 多对多 |

**产品**并**预订**通过一个对多关联关系。  相关联的第一条记录**预订**实体的第一条记录**产品**实体：

`Relate( First( Products ).Reservations, First( Reservations ) )`

若要删除这些记录之间的关系：

`Unrelate( First( Products ).Reservations, First( Reservations ) )`

在没有时未创建或删除或记录，仅记录之间的关系已修改。

**产品**并**联系人**通过多对多关联关系。  若要与相关的第一条记录**联系人**实体的第一条记录**产品**实体：

`Relate( First( Products ).Contacts, First( Contacts ) )`

为多对多关系是对称密钥，我们可能还具有中执行此操作相反的方向：

`Relate( First( Contacts ).Products, First( Products ) )`

若要删除这些记录之间的关系：

`Unrelate( First( Products ).Contacts, First( Contacts ) )`

或：

`Unrelate( First( Contacts ).Products, First( Products ) )`

演练中的全程，如下所示执行完全使用一个应用，这些实体上的这些操作**库**并**组合框**选择涉及的记录的控件。

这些示例取决于你的环境中安装了示例数据。 任一[创建试用环境，包括示例数据](../../model-driven-apps/overview-model-driven-samples.md#get-sample-apps)或[将示例数据添加到现有环境](../../model-driven-apps/overview-model-driven-samples.md#install-or-uninstall-sample-data)。

### <a name="one-to-many"></a>一个对多

#### <a name="relate-function"></a>**相关**函数

你将首先创建一个简单的应用程序，可以查看和重新分配与产品相关联的保留项。

1. 创建[从空白的平板电脑应用](../data-platform-create-app-scratch.md)。

1. 上**视图**选项卡上，选择**数据源**。

1. 在中**数据**窗格中，选择**添加数据源** > **Common Data Service** > **产品** > **连接**。  

    产品实体是加载上面的示例数据的一部分。

     ![将产品实体添加为数据源](media/function-relate-unrelate/products-connect.png)

1. 上**插入**选项卡上，添加空白垂直**[库](../controls/control-gallery.md)** 控件。

1. 请确保您刚添加的控件名为**Gallery1**，然后移动并调整其大小以填充屏幕的左侧。

1. 上**属性**选项卡上，设置**Gallery1**的**项**属性设置为**产品**并将其**布局**到**图像和标题**。

    ![配置 ProductsGallery](media/function-relate-unrelate/products-gallery.png)

1. 在中**Gallery1**，确保**标签**控件被命名为**Title1**，然后设置其**文本**属性设置为**ThisItem.Name**。

    ![在 Gallery1 中配置标签](media/function-relate-unrelate/products-title.png)

1. 选择要避免插入到的下一项在屏幕**Gallery1**。  添加第二个空白垂直**库**控件，并确保它名为**Gallery2**。

    **Gallery2**将显示在用户选择在任何产品的预订**Gallery1**。

1. 移动和调整**Gallery2**以填充屏幕的右上象限。

1. （可选）添加蓝色**标签**控制上述**Gallery2**下, 一步图所示。

1. 在编辑栏中，将**项**的属性**Gallery2**到**Gallery1.Selected.Reservations**。

    ![配置 Gallery2 项](media/function-relate-unrelate/reservations-gallery.png)

1. 在属性窗格中设置**Gallery2**的**布局**到**标题**。

    ![配置 Gallery2 布局](media/function-relate-unrelate/reservations-gallery-right.png)

1. 在中**Gallery2**，添加**[组合框](../controls/control-combo-box.md)** 控件，请确保它名为**ComboBox1**，然后移动并调整其大小以避免阻止中的其他控件**Gallery2**。

1. 上**属性**选项卡上，设置**ComboBox1**的**项**属性设置为**产品**。

    ![将项属性设置为产品](media/function-relate-unrelate/reservations-combo-right.png)

1. 向下滚动**属性**选项卡并设置**ComboBox1**的**允许多个所选内容**属性设置为**关闭**。

    ![组允许为关的多项选择](media/function-relate-unrelate/reservations-singleselect-right.png)

1. 在编辑栏中，将**ComboBox1**的**DefaultSelectedItems**属性设置为**ThisItem.产品保留**。

    ![为 ReserveCombo 设置 DefaultSelectedItems](media/function-relate-unrelate/reservations-combo.png)

1. 在中**Gallery2**，请设置**NextArrow2**的**OnSelect**属性设为此公式：

    ```powerapps-dot
    Relate( ComboBox1.Selected.Reservations, ThisItem )
    ```

    当用户选择此图标时，当前的保留项发生更改中用户选定的产品**ComboBox1**。

    ![配置 NextArrow2](media/function-relate-unrelate/reservations-relate.png)

1. 按 F5 以在预览模式下测试应用程序。

与此应用，用户可以保留在一个产品之间移动。 上一个产品预订，用户可以选择在不同的产品**ComboBox1** ，然后选择**NextArrow2**若要更改该预订。

![演示一个多应用程序中的建立关系函数](media/function-relate-unrelate/reservations-reassign.gif)

#### <a name="unrelate-function"></a>**取消关联时要**函数

此时，可以将一条记录的关系移到另一个，但不能完全删除关系。 可以使用**Unrelate**函数保留记录断开与任何产品。

1. 上**视图**选项卡上，选择**数据源**。

1. 在中**数据**窗格中，选择**添加数据源** > **Common Data Service** > **保留** > **连接**。

1. 在中**Gallery2**，请设置**OnSelect**公式**NextArrow2**为以下公式：

    ```powerapps-dot
    If( IsBlank( ComboBox1.Selected ),
        Unrelate( Gallery1.Selected.Reservations, ThisItem ),
        Relate( ComboBox1.Selected.Reservations, ThisItem )
    );
    Refresh( Reservations )
    ```
    ![配置右侧的图标](media/function-relate-unrelate/reservations-relate-unrelate.png)

1. 复制**Gallery2**到剪贴板上通过选择它，然后按 Ctrl-c。

1. 粘贴的副本**Gallery2**到同一个通过按 Ctrl + V，屏幕上，然后将其移动到屏幕的右下象限。

1. （可选）如果添加上面的标签**Gallery2**，为该标签重复前两个步骤。

1. 确保的重复**Gallery2**名为**Gallery2_1**，然后设置其**项**属性设为此公式：

    ```powerapps-dot
    Filter( Reservations, IsBlank( 'Product Reservation' ) )
    ```

    委派警告出现，但也不会影响此小数量的在此示例中的数据。

    ![Gallery2_1 的项属性设置](media/function-relate-unrelate/reservations-lost.png)

这些更改，用户可以清除中的选定**ComboBox1**联系人如果该用户尚未保留某个产品。 尚未保留某个产品的联系人显示在**Gallery2_1** ，用户可以将每个联系人分配到某个产品。

   ![演示建立关系，并取消关联时要多到应用中的函数](media/function-relate-unrelate/reservations-lostandfound.gif)

### <a name="many-to-many"></a>多对多

#### <a name="create-a-many-to-many-relationship"></a>创建多对多关系

示例数据不包括多对多关系，但你将创建一个产品实体与联系人实体之间。 用户可以与多个联系人和到多个产品的每个联系人的每个产品。

1. 从[本页](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)，选择**数据**左侧导航栏中，然后选择**实体**。

    ![打开的实体列表](media/function-relate-unrelate/entity-list.png)

1. 更改要包括的所有实体的实体筛选器。

    默认情况下，不会显示示例实体。

    ![删除实体筛选器](media/function-relate-unrelate/entity-all.png)

1. 向下的滚动，打开**产品**实体，然后选择**关系**。

    ![对于 Product 实体的关系选项卡](media/function-relate-unrelate/entity-relationships.png)

1. 选择**添加关系** > **多对多**。

    ![添加多对多关系](media/function-relate-unrelate/entity-manytomany.png)

1. 选择**联系人**实体之间的关系。

    ![选择联系人实体](media/function-relate-unrelate/entity-contact.png)

1. 选择**完成** > **保存实体**。

    ![为产品实体的关系的列表](media/function-relate-unrelate/entity-done.png)

#### <a name="relate-and-unrelate-contacts-with-one-or-more-products"></a>关联和取消关联时要与一个或多个产品的联系人

将创建类似于本主题中前面创建的另一个应用，但新的应用将提供的多对多关系。 每个联系人将能够保留而不是仅其中一个的多个产品。

1. 在空白的平板电脑应用中，创建**Gallery1**作为[第一个过程](#one-to-many)本主题中介绍。

1. 添加另一个空白垂直**库**控件，请确保它名为**Gallery2**，然后将其移动到屏幕的右上角。

    稍后在本主题中，你将添加**组合框**控制下**Gallery2**。

1. 在编辑栏中，将**Gallery2**的**项**属性设置为**Gallery1.Selected.Contacts**。

    ![配置 ContactsGallery](media/function-relate-unrelate/contacts-gallery.png)

1. 上**属性**选项卡上，设置**布局**到**图像和标题**。

    ![配置 ContactsGallery](media/function-relate-unrelate/contacts-gallery-right.png)

1. 在**Gallery2**，确保**标签**控件被命名为**Title2**，然后设置其**文本**属性设置为**ThisItem.Full Name**。

    没有文本将显示在该控件中，直到完成此过程并将联系人分配给某个产品。

    ![显示联系人姓名](media/function-relate-unrelate/contacts-title.png)

1. 删除**NextArrow2**，插入**取消**图标，并确保它名为**icon1**。

1. 设置**取消**图标**OnSelect**属性设为此公式： 

    ```powerapps-dot
    Unrelate( Gallery1.Selected.Contacts, ThisItem )
    ```

    ![配置取消按钮图标](media/function-relate-unrelate/contacts-unrelate.png)

1. 上**视图**选项卡上，选择**数据源**。

1. 在中**数据**窗格中，选择**添加数据源** > **Common Data Service** > **联系人** > **连接**。

1. 下**Gallery2**，添加**组合框**控制，请确保它名为**ComboBox1**，然后设置其**项**属性设置为**联系人**。

    ![配置的组合框项属性](media/function-relate-unrelate/contacts-combo.png)

1. 上**属性**选项卡上，设置**允许多个所选内容**到**关闭**。

    ![配置组合框布局属性](media/function-relate-unrelate/contacts-combo-right.png)

1. 插入**外**图标，并设置其**OnSelect**属性设为此公式： 

    ```powerapps-dot
    Relate( Gallery1.Selected.Contacts, ComboBox1.Selected )
    ```

    ![配置添加图标](media/function-relate-unrelate/contacts-relate.png)

与此应用，用户可自由地与相关，并取消对每个产品键为一组联系人。

- 若要向产品添加联系人，在屏幕底部的组合框中选择联系人，然后选择**添加**图标。
- 若要从产品中删除联系人，请选择**取消**该联系人的图标。

    与一个多不同的多对多关系，用户可以将同一联系人与多个产品相关联。

![演示建立关系，并取消关联时要多对多应用程序中的函数](media/function-relate-unrelate/contacts-relate-unrelate.gif)

#### <a name="in-reverse-relate-and-unrelate-products-with-multiple-contacts"></a>按相反的顺序： 相关和取消关联时要使用多个联系人的产品

多对多关系是对称密钥。 您可以扩展此示例以将产品添加到联系人，然后切换，以显示如何将显示关系沿任一方向在两个屏幕之间。

1. 设置**OnVisible**的属性**Screen1**到**刷新 （产品）**。

    更新一个对多或多对多关系中，只有第一个参数实体的数据时**Relate**或**Unrelate**调用刷新。 第二个必须刷新手动如果你想要此应用的屏幕之间切换。

    ![OnVisible 属性设置为刷新函数](media/function-relate-unrelate/contacts-refresh.png)

1. 重复**Screen1**。

    将名为重复**Screen1_1**和窗体从联系人端查看关系的基础。

    ![复制屏幕](media/function-relate-unrelate/contacts-duplicate.png)

1. 若要创建反向视图，更改的控件上这些公式**Screen1_1**:

    - Screen1_1.OnVisible = `Refresh( Contacts )`
    - Gallery1_1.Items = `Contacts`
    - Title1_1.Text = `ThisItem.'Full Name'`
    - Label1_1.Text = `"Selected Contact Products"`
    - Gallery2_1.Items = `Gallery1_1.Selected.Products`
    - Title2_1.Text = `ThisItem.Name`
    - Icon1_1.OnSelect = `Unrelate( Gallery1_1.Selected.Products, ThisItem )`
    - ComboBox1_1.Items = `Products`
    - Icon2_1.OnSelect = `Relate( Gallery1_1.Selected.Products, ComboBox1_1.Selected )`

    结果看起来非常类似于上一屏幕但这是以从关系**联系人**端。

    ![显示多对多关系开头的联系人](media/function-relate-unrelate/reverse-screen.png)

1. 插入**箭头上下**图标并设置其**OnSelect**属性设置为**Navigate (Screen1，None)**。  在执行相同的操作**Screen1**与公式**Navigate (Screen1_1，None)**。

    ![添加屏幕之间导航](media/function-relate-unrelate/reverse-navigate.png)

使用此新屏幕，用户可以向产品添加联系人翻转到联系人的视图并查看关联的产品。 关系是对称和两个屏幕之间共享。

![来自任一方演示多对多关系](media/function-relate-unrelate/contacts-reverse.gif)
