---
title: 了解记录引用和多态查找 |Microsoft Docs
description: 使用记录的引用和画布应用中的多态查询
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 05/17/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 80755667a9c7c36eb47999f7f8b2f939eb032c69
ms.sourcegitcommit: 93096dfa1aadba77159db1e5922f3d5528eecb7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/21/2019
ms.locfileid: "65986453"
---
# <a name="understand-record-references-and-polymorphic-lookups-in-canvas-apps"></a>了解记录引用和画布应用中的多态查询

您在学校在编写一篇研究论文，可能会提供结束时您引用的列表。 不包括实际的背景材料，以便在有人无法跟踪原始源使用但而不是 web 链接、 书名和作者或其他信息的副本。 混合不同类型的单个列表中的源音频录制，每个都有其自己的特定详细信息正确引用旁边的报纸文章。 例如，维基百科文章通常包括[引用的长列表](https://en.wikipedia.org/wiki/Microsoft#References)。

在画布应用中，你经常处理的数据源从下载的记录的副本。 您使用[**查找**](functions/function-filter-lookup.md)并[**筛选器**](functions/function-filter-lookup.md)函数和[**库**](controls/control-gallery.md)控件的**选定**属性来标识所需的特定记录。 中的所有记录**筛选器**或**选定**将属于相同的实体类型，因此可以使用一个简单的字段。*字段*表示法。 这些副本通常包含的参考信息，因此，可以使用[**修补**](functions/function-patch.md)函数来更新原始数据源。

画布应用还支持*记录引用*。 更类似于研究论文引用，记录引用所引用的一条记录不包含它的完整副本。 此类引用可以引用中的任何实体的记录。 此外研究论文的引用，如可以混合使用单个列中的不同实体中的记录。

记录引用上的许多操作都是相同处理记录。 您可以比较记录的引用到对方以及完整记录。 可以设置记录的引用值和**修补程序**函数根据需要使用完整记录的查找。

没有重要使用情况的一个区别： 无需先建立它引用的实体不能直接访问记录引用的字段。 这是因为画布应用需要的所有类型都已知当你编写的公式。 因为运行应用之前，您不知道的记录引用的类型，不能使用简单。*字段*直接表示法。 您必须首先动态确定使用的实体类型[ **IsType** ](functions/function-astype-istype.md)函数，然后使用。*字段*的结果的表示法[ **AsType** ](functions/function-astype-istype.md)函数。

*实体类型*指的是实体中的每个记录的架构。 每个实体包含一组唯一的具有不同的名称和数据类型的字段。 每个记录的实体将继承该结构;如果它们来自相同的实体，则两条记录具有相同的实体类型。

## <a name="polymorphic-lookups"></a>多态查询

Common Data Service 支持记录之间的关系。 中的每条**帐户**实体具有**主要联系人**到中的记录的查找字段**联系人**实体。 中的记录只能引用查找**联系人**并不能引用记录中，即**团队**实体。 最后的细节很重要，因为你始终知道什么字段都可用于查找。

Common Data Service 还支持多态的查找，可以从一组中的任何实体引用一条记录。 例如，**所有者**字段中的记录可以引用**用户**实体或**团队**实体。 在不同的记录中的同一个查阅字段可能引用不同的实体中的记录。 在这种情况下，不总是知道字段将可用。

使用多态查找通用数据服务用于画布记录引用。 此外可以使用此上下文中，这是两个概念有何区别之外的记录引用。

在下一部分中，您将开始，以使用了解这些概念**所有者**查找。

## <a name="show-the-fields-of-a-record-owner"></a>显示记录所有者的字段

Common Data Service 中的每个实体包括**所有者**字段。 不能删除此字段，不能添加另一个，它始终需要一个值。

若要显示在该字段**帐户**实体：

1. 打开[此 PowerApps 站点](http://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)。
1. 在左侧的导航栏中，选择**数据** > **实体**。
1. 在实体列表中，选择**帐户**。
1. 在右上角中，打开筛选器列表 (设置为**默认**默认情况下)，然后选择**所有**。
1. 向下滚动直至**所有者**字段显示。

 > [!div class="mx-imgBorder"]
 > ![帐户实体上的所有者字段](media/working-with-references/owner-field.png)

此查找字段可以指从一条记录**团队**实体或**用户**实体。 这些实体中的不是每个记录都有权进行**所有者**; 如果遇到问题，请选中支持的角色。

此图显示了一个简单的库，**帐户**，其中**帐户**实体已添加到作为数据源的应用：

> [!div class="mx-imgBorder"]
> ![库控件中显示的帐户](media/working-with-references/accounts-gallery.png)

> [!IMPORTANT]
> 在本主题中，图形显示一些名称和其他不属于与 Common Data Service 附带的示例数据的值。 准确的步骤演示了如何配置控件的特定结果，但您的体验将因你的组织的数据。

若要在库中显示的每个帐户所有者，您可能想要使用该公式**ThisItem.Owner.Name**。 但是，在名称字段**团队**实体是**团队名称**，和中的名称字段**用户**实体是**全名**。 应用程序不能知道哪种类型的查找您正在使用运行应用程序中，直到和而异中的记录之间**帐户**实体。

需要可以适应这种变化的公式。 您还需要添加数据源的实体类型，**所有者**可能是 (在这种情况下，**用户**并**团队**)。 将以下三个数据源添加到您的应用程序：

> [!div class="mx-imgBorder"]
> ![在数据窗格中的帐户、 团队和用户实体](media/working-with-references/accounts-datasources.png)

使用这些数据中的源，请使用以下公式显示的用户或团队名称：

```powerapps-dot
If( IsType( ThisItem.Owner, [@Teams] ),
    "Team: " & AsType( ThisItem.Owner, [@Teams] ).'Team Name',
    "User: " & AsType( ThisItem.Owner, [@Users] ).'Full Name' )
```

> [!div class="mx-imgBorder"]
> ![使用所有者字段显示在库控件中显示帐户](media/working-with-references/accounts-displayowner.png)

在此公式**IsType**函数测试**所有者**字段对**团队**实体。 如果它是该实体类型， **AsType**函数将转换到**团队**记录。 此时，可以访问的所有字段**团队**实体，包括**团队名称**，通过使用 *。字段*表示法。 如果**IsType**确定**所有者**不是在记录**团队**实体，该字段必须是中的记录**用户**实体因为**所有者**字段是必需的 (不能*空白*)。

要将[全局消除歧义运算符](functions/operators.md#disambiguation-operator)有关 **[@Teams]** 并 **[@Users]** 以确保您正在使用的全局实体类型。 在这种情况下，您不需要它，但它是一个好习惯到窗体。 一个对多关系通常在库的记录范围中冲突，这种做法可以避免混淆。

若要使用的记录引用的任何字段，必须先使用**AsType**函数转换成特定实体类型。 无法访问直接从字段**所有者**字段，因为系统不知道你想要使用哪种实体类型。

**AsType**函数返回一个错误，如果**所有者**字段不匹配所请求的实体类型，因此，可以使用**IfError**函数来简化此公式。 首先，启用的实验性功能**公式级错误管理**:

> [!div class="mx-imgBorder"]
> ![实验性开关来开启公式级错误管理](media/working-with-references/accounts-iferror.png)

然后将此替换为前面的公式：

```powerapps-dot
IfError(
    "Team: " & AsType( ThisItem.Owner, [@Teams] ).'Team Name',
    "User: " & AsType( ThisItem.Owner, [@Users] ).'Full Name' )
```

## <a name="filter-based-on-an-owner"></a>根据所有者进行筛选

恭喜，现已将记录引用所使用的最困难的方面。 其他用例都更简单，因为它们不访问记录的字段。 作为案例，需要筛选，这将在本部分中探讨。

添加**组合框**上方库控件，并设置新控件的这些属性：

- **项**: `Users`
- **SelectMultiple**: `false`

> [!div class="mx-imgBorder"]
> ![项属性设置为用户添加库上方的组合框控件](media/working-with-references/filter-insert-combobox.png)

若要筛选特定用户从此组合框中选择库，请设置库的**项**属性设为此公式：

```powerapps-dot
Filter( Accounts, Owner = ComboBox1.Selected )
```

> [!div class="mx-imgBorder"]
> ![根据在组合框控件中设置的值筛选的库](media/working-with-references/filter-accounts.png)

> [!IMPORTANT]
> 本主题中的说明正确无误如果完全按照步骤操作。 但是，由其名称引用控件的任意公式，无法正常工作，如果控件具有不同的名称。 如果你删除并添加相同类型的控件，控件的名称结尾处号相应更改。 对于任何公式，将显示错误，请确认它包含的所有控件的正确名称。

无需使用**IsType**或**AsType**因为要将记录到记录的其他引用或完整记录的引用进行比较。 应用已知道的实体类型**ComboBox1.Selected**因为它派生自**用户**实体。 为其所有者是一个团队的帐户不匹配的筛选器条件。

您可以通过支持按用户或团队进行筛选以获取那个更复杂。

1. 腾出一些空间，在屏幕顶部附近通过调整库的大小和移动组合框，插入[**单选**控制](controls/control-radio.md)上面库，然后设置新的控制这些属性：

    - **项**: `[ "All", "Users", "Teams" ]`
    - **布局**: `Layout.Horizontal`

1. 有关**组合框**控件，将此属性设置 (如果组合框消失后，选择**用户**单选控件中):

    - **可见**: `Radio1.Selected.Value = "Users"`

1. 复制并粘贴**组合框**控制，直接将副本移原始，然后设置这些属性的副本：

    - **项**: `Teams`
    - **可见**: `Radio1.Selected.Value = "Teams"`

    应用会在某个时间，具体取决于单选控件的状态显示只有一个组合框。 因为它们是另一个的正上方，它们将显示为相同更改其内容的控件。

1. 最后，设置**项**的属性**库**控制为以下公式：

    ```powerapps-dot
    Filter( Accounts,
        Radio1.Selected.Value = "All"
        Or (Radio1.Selected.Value = "Users" And Owner = ComboBox1.Selected)
        Or (Radio1.Selected.Value = "Teams" And Owner = ComboBox1_1.Selected)
    )
    ```

    > [!div class="mx-imgBorder"]
    > ![显示所有记录或特定用户或团队的筛选的库](media/working-with-references/filter-combobox.png)

这些更改，可以显示所有记录，或根据用户或团队对其进行筛选：

> [!div class="mx-imgBorder"]
> ![动画显示不同的筛选的结果基础的单选控件和组合框](media/working-with-references/filter-allthree.gif)

该公式将完全可委托。 比较的单选按钮值的部分是所有记录中的一个常量，并筛选器的其余部分发送到 Common Data Service 之前进行评估。

如果你想要对所有者的类型进行筛选，则可以使用**IsType**函数，但它的不尚可委托。

> [!div class="mx-imgBorder"]
> ![通过使用 IsType 按所有者类型筛选](media/working-with-references/filter-bytype.png)

## <a name="update-the-owner-by-using-patch"></a>使用修补程序更新所有者

可以更新**所有者**字段与任何其他查找相同的方式。 若要将当前所选的帐户的所有者设置为第一个团队：

```powerapps-dot
Patch( Accounts, Gallery1.Selected, { Owner: First( Teams ) } )
```

此方法不会从正常查找不同，因为应用已知道的类型**第一个 （团队）**。 如果改用所需的第一个用户，将替换为与该部分**第一个 （用户）**。 **修补程序**函数知道**所有者**字段可以设置为下列任意一种两个实体。

若要将此功能添加到应用程序：

1. 在中**树视图**窗格中，选择**单选**控件和两个**组合框**相同时控件。

1. 省略号菜单中，选择**复制这些项**。

    > [!div class="mx-imgBorder"]
    > ![使用树视图中的多个控件的副本](media/working-with-references/patch-copy.png)

1. 在相同菜单上，选择**粘贴**。

    > [!div class="mx-imgBorder"]
    > ![使用树视图中的多个控件的粘贴](media/working-with-references/patch-paste.png)

1. 将复制的控件移到库的右侧。

    > [!div class="mx-imgBorder"]
    > ![移动到的库右侧的复制的控件](media/working-with-references/patch-position.png)

1. 选择复制**单选**控件，然后再更改这些属性：

    - 项： `[ "Users", "Teams" ]`
    - 默认值： `If( IsType( Gallery1.Selected.Owner, Users ), "Users", "Teams" )`

    > [!div class="mx-imgBorder"]
    > ![从单选控件中移除所有选择](media/working-with-references/patch-noall.png) 

1. 在中**单选**控件中，选择**用户**以便**组合框**列出了用户的控件是否可见。

1. 选择可见**组合框**控件，并将**DefaultSelectedItems**属性设为此公式：

    ```powerapps-dot
    If( IsType( Gallery1.Selected.Owner, Users ),
        AsType( Gallery1.Selected.Owner, Users ),
        Blank()
    )
    ```

    > [!div class="mx-imgBorder"]
    > ![默认属性设置为用户组合框](media/working-with-references/patch-default-users.png)

1. 在中**单选**控件中，选择**团队**以便**组合框**列出了团队的控件是否可见。

1. 选择**单选**控件，才能取消现在不可见**组合框**控件中的以用户。

1. 选择可见**组合框**控制的团队，并将其**DefaultSelectedItems**属性设为此公式：

    ```powerapps-dot
    If( IsType( Gallery1.Selected.Owner, Teams ),
        AsType( Gallery1.Selected.Owner, Teams ),
        Blank()
    )
    ```

    > [!div class="mx-imgBorder"]
    > ![默认属性设置为团队的组合框](media/working-with-references/patch-default-teams.png)

1. 插入**按钮**控件，将下将其移**组合框**控件，再然后将按钮的**文本**属性设置为`"Patch Owner"`。

1. 设置**OnSelect**为以下公式的按钮的属性：

    ```powerapps-dot
    Patch( Accounts, Gallery1.Selected,
        { Owner: If( Radio1_1.Selected.Value = "Users",
                ComboBox1_2.Selected,
                ComboBox1_3.Selected ) } )
    ```

    > [!div class="mx-imgBorder"]
    > ![按钮控件上设置的公式](media/working-with-references/patch-button.png)

复制**单选**并**组合框**控件显示在库中当前所选帐户的所有者。 与同一个控件，可以对任何团队或用户设置帐户的所有者，通过选择按钮：

> [!div class="mx-imgBorder"]
> ![动画显示修补程序的所有者与用户或团队](media/working-with-references/patch-allthree.gif)

## <a name="show-the-owner-by-using-a-form"></a>通过使用窗体显示所有者

可以显示**所有者**字段内通过添加自定义卡窗体。 在撰写本文时，不能更改与窗体控件字段的值。

1. 插入**编辑窗体**控件，然后重设大小，并将其移动到右下角。

1. 上**属性**选项卡的屏幕上，打开右侧附近**数据源**列表，并选择**帐户**。

    > [!div class="mx-imgBorder"]
    > ![窗体控件显示具有空白值的其他字段](media/working-with-references/form-insert.png)  

1. 设置窗体的**项**属性设置为`Gallery1.Selected`。

    > [!div class="mx-imgBorder"]
    > ![显示其他字段填充从库中的选定项的窗体控件](media/working-with-references/form-item.png)

1. 上**属性**选项卡的屏幕上，选择右侧附近**编辑字段**。

1. 在中**字段**窗格中，选择省略号，然后选择**添加自定义卡**。

    > [!div class="mx-imgBorder"]
    > ![添加自定义卡片](media/working-with-references/form-customcard.png)

    新卡片显示在窗体控件的底部。

1. 调整卡片的大小，以显示所有文本。

    > [!div class="mx-imgBorder"]
    > ![插入自定义的空白卡](media/working-with-references/form-inserted-customcard.png)

1. 插入**标签**控制的自定义卡，然后设置的标签**文本**属性设为在库中使用公式：

    ```powerapps-dot
    If( IsType( ThisItem.Owner, Teams ),
        "Team: " & AsType( ThisItem.Owner, Teams ).'Team Name',
        "User: " & AsType( ThisItem.Owner, Users ).'Full Name' )
    ```

    > [!div class="mx-imgBorder"]
    > ![标签控件中显示所有者字段的自定义卡片](media/working-with-references/form-displayowner.png)

对于库中的每个所选内容，包括记录的所有者的帐户的更多字段出现在窗体。 如果你使用更改所有者**修补程序**按钮，窗体控件还显示了所做的更改。

> [!div class="mx-imgBorder"]
> ![动画显示窗体控件对库中的更改作出响应](media/working-with-references/form-allthree.gif)

## <a name="show-the-fields-of-a-customer"></a>显示客户的字段

在 Common Data Service**客户**查阅字段是另一个非常相似的多态查找**所有者**。

**所有者**限制为每个实体，但实体一个可以包含零个、 一个或多**客户**查阅字段。 **联系人**系统实体包括**公司名称**字段中，即**客户**查找字段。

> [!div class="mx-imgBorder"]
> ![联系人实体公司名称字段显示为不是必需的客户数据类型](media/working-with-references/customer-companyname.png)

您可以添加更多**客户**通过选择实体的查找字段**客户**新字段的数据类型。

![创建一个字段时，客户数据类型从数据类型的列表](media/working-with-references/customer-datatype.png)

一个**客户**查阅字段可以指从一条记录**帐户**实体或**联系人**实体。 将使用**IsType**并**AsType** functions 与这些实体，因此，现在是将其添加为数据源的好时机 (您可以保留**团队**和**用户**就地)。

> [!div class="mx-imgBorder"]
> ![帐户、 数据窗格中的团队、 用户和联系人实体](media/working-with-references/customer-datasources.png)

治疗**客户**并**所有者**字段非常类似，你可以按原义复制应用程序 (**文件** > **另存为**，然后指定一个不同的名称) 并进行以下简单替换：

| Location | **所有者**示例 | **客户**示例 |
|----------|-----------|------------------|
| 在整个 | **Owner** | **Customer Name** |
| 在整个 | **用户** | **Accounts** |
| 在整个 | **团队** | **Contacts** |
| 库的**项**属性 | **Accounts** | **Contacts** |
| 窗体的**项**属性 | **Accounts** | **Contacts** |
| 第一个参数**修补程序**<br>在按钮的**OnSelect**属性 | **Accounts** | **Contacts** |
| 筛选广播电台**项**属性 | **[&nbsp;"All",&nbsp;"Users",&nbsp;"Teams"&nbsp;]** | **[&nbsp;"All",&nbsp;"Accounts",&nbsp;"Contacts"&nbsp;]** |
| 修补广播电台**项**属性 | **[ "Users", "Teams" ]** | **[ "Accounts", "Contacts" ]** |
| 组合框**Visible**属性 | **"用户"** 和 **"团队"** | **"帐户"** 和 **"Contacts"** |

例如，新的库应具有这**项**属性：

```powerapps-dot
Filter( Contacts,
    Radio1.Selected.Value = "All"
    Or (Radio1.Selected.Value = "Accounts" And 'Company Name' = ComboBox1.Selected)
    Or (Radio1.Selected.Value = "Contacts" And 'Company Name' = ComboBox1_1.Selected)
)
```

> [!div class="mx-imgBorder"]
> ![派生自所有者应用程序使用简单的更改应用的客户应用程序](media/working-with-references/customer-simple-update.png)

两个重要区别**客户**并**所有者**要求更新库和窗体中的公式：

1. 一个对多关系之间**帐户**并**联系人**按名称引用这些实体类型时，优先考虑。 而不是**帐户**，使用 **\[\@帐户]**，而不是**联系人**，使用 **\[ \@联系人]**。 通过使用[全局消除歧义运算符](functions/operators.md#disambiguation-operator)，确保你正在引用中的实体类型**IsType**并**AsType**。 仅记录上下文的库和窗体控件中存在此问题。

1. **所有者**字段必须具有一个值，但**客户**字段可以是*空白*。 若要显示的类型名称不正确的结果，测试与这种情况下[ **IsBlank**函数](functions/function-isblank-isempty.md)，并改为显示一个空的文本字符串。

这些更改都在同一个公式，如下所示： 显示在表单中的自定义卡**文本**库的标签控件的属性：

```powerapps-dot
If( IsBlank( ThisItem.'Company Name' ), "",
    IsType( ThisItem.'Company Name', [@Accounts] ),
        "Account: " & AsType( ThisItem.'Company Name', [@Accounts] ).'Account Name',
    "Contact: " & AsType( ThisItem.'Company Name', [@Contacts] ).'Full Name'
)
```

> [!div class="mx-imgBorder"]
> ![更新到库中的副标题标签控件的 Text 属性](media/working-with-references/customer-update.png)

这些更改，您可以查看和更改**公司名称**字段中**联系人**实体。

> [!div class="mx-imgBorder"]
> ![显示如何选择联系人更改其他控件和窗体的动画](media/working-with-references/customer-allthree.gif)

> [!NOTE]
> 撰写本文时，**客户**查找具有以下限制：
>
> - 不能筛选基于中的特定记录的列表**联系人**或**帐户**实体。 上一示例中的筛选器单选按钮控件不起作用。
> - 是否正常工作的唯一客户字段是系统定义**的公司名称**上**联系人**实体，这将使用在前面的示例。 添加自定义客户字段尚不支持。
> - 无法通过清除客户字段**修补程序**以将其设置为*空白*。

## <a name="understand-regarding-lookup-fields"></a>了解有关查找字段

**有关**查找字段稍有不同于那些已使用过本主题中。 将首先应用更早版本，本主题所述的模式，然后你将了解其他一些技巧。

您可以只需使用启动**传真**实体。 该实体具有多态**有关**查阅字段，可以参考**帐户**，**联系人**，和其他实体。 用户可以针对执行应用程序**客户**并修改其用于**传真**。

| Location | **客户**示例 | **传真**示例 |
|----------|-----------|------------------|
| 在整个 | **Customer Name** | **有关** |
| 库的**项**属性 | **Contacts** | **传真** |
| 窗体的**项**属性 | **Contacts** | **传真** |
| 第一个参数**修补程序**<br> 在按钮的**OnSelect**属性 | **Contacts** | **传真** |

同样，您将需要添加数据源： 这次是为了**传真**。 上**视图**选项卡上，选择**数据源**:

> [!div class="mx-imgBorder"]
> ![显示帐户、 团队、 用户、 联系人和传真的实体的数据窗格](media/working-with-references/faxes-datasources.png)

一个重要区别**有关**是它并不限于**帐户**并**联系人**。 实际上，实体的列表是可扩展性，自定义实体。 大部分应用程序可以适应此点而不进行修改，但必须更新库和窗体中的标签的公式：

```powerapps-dot
If( IsBlank( ThisItem.Regarding ), "",
    IsType( ThisItem.Regarding, [@Accounts] ),
        "Account: " & AsType( ThisItem.Regarding, [@Accounts] ).'Account Name',
    IsType( ThisItem.Regarding, [@Contacts] ),
        "Contacts: " & AsType( ThisItem.Regarding, [@Contacts] ).'Full Name',
    ""
)
```

> [!div class="mx-imgBorder"]
> ![有关查找副标题控件的更新后的文本属性](media/working-with-references/regarding-label.png)

进行这些更改后，就使用**有关**一样，只需查找**所有者**并**客户**查找。

> [!div class="mx-imgBorder"]
> ![演示如何在库中选择某一项更改的其他控件和窗体的动画](media/working-with-references/regarding-allthree.gif)

> [!NOTE]
> 撰写本文时，**有关**查找具有以下限制：
>
> - 您不能筛选基于特定记录的列表。 上一示例中的筛选器单选按钮控件不起作用。
> - 您不能使用清除相关字段**修补程序**以将其设置为*空白*。

## <a name="understand-regarding-relationships"></a>了解有关关系

**有关**不同于**所有者**并**客户**因为前者涉及多对一关系。 根据定义，反向，一个对多关系，可编写**第一个 （帐户）。传真**。

让我们来备份并看看实体定义。 在 Common Data Service，如实体**传真**，**任务**，**电子邮件**，**说明**，**电话呼叫**，**字母**，并**聊天**指定为[*活动*](../../developer/common-data-service/activity-entities.md)。 您还可以创建您自己[自定义活动实体](../../developer/common-data-service/custom-activities.md)。 当您查看或创建的活动实体时，其设置会显示在**更多设置**。

![创建实体时的活动实体设置](media/working-with-references/activity-entitytype.png)

其他实体可以与活动实体相关，如果它们作为启用*活动任务*中实体的设置。 **帐户**，**联系人**，并因此指定其他很多标准实体 (同样，在**更多设置**)。

![创建实体时的活动任务设置](media/working-with-references/activity-entityuse.png)

所有活动的实体和活动任务实体都具有隐式的关系。 如果您更改到筛选器**所有**在屏幕的顶部，选择**传真**实体，并选择**关系**选项卡上，可以是目标的所有实体**有关**查找出现。

> [!div class="mx-imgBorder"]
> ![显示有关多对一关系的传真实体的关系](media/working-with-references/activity-manytoone.png)

如果显示的关系**帐户**实体，则可能引发的所有实体**有关**查找字段会显示。

> [!div class="mx-imgBorder"]
> ![显示有关一个对多关系客户实体的关系](media/working-with-references/activity-onetomany.png)

意味着什么？ 它所有

- 在编写公式时，必须考虑到不固定的活动实体的列表，并可以创建你自己。 该公式必须适当地处理活动实体不正常的。
- 活动任务和活动具有一个对多关系。 您可以轻松地请求与帐户相关的所有传真。

若要了解在应用程序这一概念：

1. 添加另一个屏幕。

    > [!div class="mx-imgBorder"]
    > ![插入空白屏幕](media/working-with-references/activitypointer-newscreen.png)

1. 插入的库控件，调整其大小，然后将其移动到屏幕的左侧。

1. 上**属性**屏幕的右侧附近选项卡上，设置库的**项**到**帐户**。

    > [!div class="mx-imgBorder"]
    > ![在属性窗格中将项目设为帐户](media/working-with-references/activitypointer-accounts.png)

1. 将库的布局设置为**标题**，然后将标题字段设置为**帐户名称**。

    > [!div class="mx-imgBorder"]
    > ![对于属性窗格中的库控件设置为标题的布局](media/working-with-references/activitypointer-account-name.png)

1. 添加第二个库，调整其大小，然后将其移动到屏幕的右侧。

1. 设置新的库**项**属性设置为`Gallery2.Selected.Faxes`。

    此步骤中返回筛选的传真对于给定的帐户列表。

    > [!div class="mx-imgBorder"]
    > ![设置显示传真的库的 Items 属性](media/working-with-references/activitypointer-faxes.png)

1. 将库的布局设置为**标题和副标题**，然后设置要显示的标题字段**主题**字段 (这可能是小写**主题**)。

    > [!div class="mx-imgBorder"]
    > ![组标题改为使用者字段](media/working-with-references/activitypointer-subject.png)

在帐户列表中选择项时，传真的列表将显示为该帐户仅传真。

> [!div class="mx-imgBorder"]
> ![在帐户库推动传真列表中显示所选内容的动画](media/working-with-references/activitypointer-allthree.gif)

## <a name="activity-entity"></a>活动实体

如前一部分所述，可以显示的帐户的所有传真。 但是，您还可以显示一个帐户，包括传真、 电子邮件、 电话呼叫和其他交互的所有活动。

对于后一种方案中，你使用**活动**实体。 可以通过打开显示此实体**所有**在右上角登录以从实体列表中删除筛选器。

> [!div class="mx-imgBorder"]
> ![显示活动实体的实体的列表](media/working-with-references/activitypointer-entity.png)

**活动**实体是特殊。 只要您添加一条记录**传真**实体，系统还会创建中的记录**活动**都共用活动的所有实体的字段的实体。 这些字段**使用者**是最有趣的一个。

可以通过更改上一示例中的只有一个行显示所有活动。 替换`Gallery2.Selected.Faxes`与`Gallery2.Selected.Activities`。

> [!div class="mx-imgBorder"]
> ![第二个库中，传真从更改为活动的项属性的更改](media/working-with-references/activitypointer-gallery.png)

记录来自**活动**实体，但你可以不过使用**IsType**函数以确定它们是哪种类型的活动。 同样，使用之前**IsType**实体类型，必须添加数据源。

> [!div class="mx-imgBorder"]
> ![显示 IsType 功能所需的所有实体的数据窗格](media/working-with-references/activity-datasources.png)

通过使用此公式，可以在库中的标签控件中显示的记录类型：

```powerapps-dot
If( IsType( ThisItem, [@Faxes] ), "Fax",
    IsType( ThisItem, [@'Phone Calls'] ), "Phone Call",
    IsType( ThisItem, [@'Email Messages'] ), "Email Message",
    IsType( ThisItem, [@Chats] ), "Chat",
    "Unknown"
)
```

> [!div class="mx-imgBorder"]
> ![将文本属性设置为公式，以显示传真、 电话呼叫和其他活动信息](media/working-with-references/activitypointer-type.png)

此外可以使用**AsType**来访问特定类型的字段。 例如，以下公式确定的每个活动的类型，而且对于电话呼叫，将显示手机号和调用方向从**电话号码**实体：

```powerapps-dot
If( IsType( ThisItem, [@Faxes] ), "Fax",
    IsType( ThisItem, [@'Phone Calls'] ),
       "Phone Call: " &
       AsType( ThisItem, [@'Phone Calls'] ).'Phone Number' &
       " (" & AsType( ThisItem, [@'Phone Calls'] ).Direction & ")",
    IsType( ThisItem, [@'Email Messages'] ), "Email Message",
    IsType( ThisItem, [@Chats] ), "Chat",
    "Unknown"
)
```

> [!div class="mx-imgBorder"]
> ![使用电话呼叫的详细信息的展开的文本属性](media/working-with-references/activitypointer-phonecall.png)

因此，该应用程序显示活动的完整列表。 **使用者**字段是否该公式将它们考虑或不针对所有类型的活动，显示。 对于您已经了解的活动的类型，可以显示其类型名称和有关每个活动的特定于类型的信息。

> [!div class="mx-imgBorder"]
> ![完成显示为不同类型的活动的信息的屏幕](media/working-with-references/activitypointer-complete.png)

## <a name="notes-entity"></a>说明实体

到目前为止，所有**有关**示例具有基于活动，但**说明**实体表示另一种情况。

创建实体时，可以启用附件。

> [!div class="mx-imgBorder"]
> ![创建实体时启用附件和注释](media/working-with-references/notes-entity.png)

如果你选择用于启用附件的复选框，你将创建**有关**与关系**说明**实体，如图所示的**帐户**实体：

> [!div class="mx-imgBorder"]
> ![帐户实体通过一个对多关系说明显示关系](media/working-with-references/notes-relationships.png)

使用这种差异，以外**有关**查找与你在其中使用的活动相同的方式。 启用了附件有一个对多关系的实体**说明**，如下例所示：

`First( Accounts ).Notes`

> [!NOTE]
> 撰写本文时，**有关**查找不适用于**说明**实体。 无法读取或筛选器基于**有关**字段，并且不能通过使用设置该字段**修补程序**。
>
> 但是，反过来**说明**一个对多关系仍然可用，因此可以筛选记录为附件启用便笺的列表。 此外可以使用[ **Relate** ](functions/function-relate-unrelate.md)函数将注释添加到的记录**说明**表，但是请注意，必须先创建，如本例所示：
>
>`Relate( ThisItem.Notes, Patch( Notes, Defaults( Notes ), { Title: "A new note" } ) )`

## <a name="activity-parties"></a>活动的参与方

在撰写本文时，画布应用不支持活动的参与方。