---
title: 了解记录引用和多态查找 |Microsoft Docs
description: 处理画布应用中的记录引用和多态查找
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 09/14/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: f44d28ab57bb012f1cb4a847920a4cf0597e3b68
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/02/2019
ms.locfileid: "74673509"
---
# <a name="understand-record-references-and-polymorphic-lookups-in-canvas-apps"></a>了解画布应用中的记录引用和多态查找

在学校编写研究论文时，可能会在末尾提供参考列表。 你未包含所使用的实际背景材料的副本，而不包括 web 链接、书籍标题和作者，或其他信息，使用户能够跟踪原始源。 你在单个列表中混合了不同类型的源、音频录制旁边的文章，每个文章都有自己的特定详细信息用于正确的引文。 例如，维基百科文章通常包含一个[较长的引用列表](https://en.wikipedia.org/wiki/Microsoft#References)。

在画布应用中，经常处理从数据源下载的记录副本。 您可以使用[**查找**](functions/function-filter-lookup.md)和[**筛选**](functions/function-filter-lookup.md)函数以及[**库**](controls/control-gallery.md)控件的**所选**属性来识别所需的特定记录。 **筛选器**中的所有记录或**选定**的记录都是相同的实体类型，因此，您可以将字段与简单的一起使用。*字段*表示法。 这些副本通常包含引用信息，因此你可以使用[**Patch**](functions/function-patch.md)函数来更新原始源。

画布应用还支持*记录引用*。 与研究论文引用非常类似，记录引用引用一条记录，而不包含它的完整副本。 此类引用可以引用任何实体中的记录。 同样，您也可以在一列中混合不同实体中的记录。

对记录引用的多个操作与使用记录相同。 您可以将记录引用相互比较，并将其与完整记录进行比较。 您可以使用**Patch**函数设置记录引用的值，就像使用完整记录进行查找一样。

有一种重要的用法差异：你不能直接访问记录引用的字段，而无需首先确定它所引用的实体。 这是因为，在编写公式时，画布应用要求所有类型都是已知的。 由于在应用运行之前不知道记录引用的类型，因此无法使用简单的。直接*字段*符号。 必须首先使用[**IsType**](functions/function-astype-istype.md)函数动态确定实体类型，然后使用。[**AsType**](functions/function-astype-istype.md)函数的结果上的*字段*表示法。

*实体类型*引用实体中每个记录的架构。 每个实体都具有一组具有不同名称和数据类型的唯一字段。 实体的每个记录都继承该结构;如果两个记录来自同一实体，则它们具有相同的实体类型。

## <a name="polymorphic-lookups"></a>多态查找

Common Data Service 支持记录之间的关系。 "**帐户**" 实体中的每个记录都具有 "**联系人**" 实体中的记录的**主 "联系人**查找" 字段。 查找只能引用 "**联系人**" 中的记录，而不能引用 "**团队**" 实体中的记录。 最后一个详细信息非常重要，因为您始终知道哪些字段可用于查找。

Common Data Service 还支持多态查找，多态查找可以引用来自集内任何实体的记录。 例如，"**所有者**" 字段可以引用 "**用户**" 实体或 "**团队**" 实体中的记录。 不同记录中的相同查找字段可能引用不同实体中的记录。 在这种情况下，你并不总是知道哪些字段将可用。

画布记录引用设计用于在 Common Data Service 中处理多态查找。 你还可以在此上下文之外使用记录引用，这就是两个概念的不同之处。

在下一部分中，你将开始通过使用**所有者**查找来了解这些概念。

## <a name="show-the-fields-of-a-record-owner"></a>显示记录所有者的字段

Common Data Service 中的每个实体都包含一个**所有者**字段。 不能删除此字段，不能再添加其他字段，并且它始终需要一个值。

若要在**Account**实体中显示该字段：

1. 打开[此电源应用站点](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)。
1. 在左侧导航栏中，选择 "**数据** > **实体**"。
1. 在实体列表中，选择 "**帐户**"。
1. 在右上角，打开 "筛选器" 列表（默认设置为 "默认**值**"），然后选择 "**全部**"。
1. 向下滚动，直到出现 "**所有者**" 字段。

 > [!div class="mx-imgBorder"]
 > 帐户实体上的 ![所有者字段](media/working-with-references/owner-field.png)

此查找字段可以引用 "**团队**" 实体或 "**用户**" 实体中的记录。 并非这些实体中的每个记录都具有作为**所有者**的权限;如果遇到问题，请检查支持的角色。

此图显示了一个简单的**帐户**库，其中**帐户**实体已作为数据源添加到应用：

> [!div class="mx-imgBorder"]
> ![库控件中显示的帐户](media/working-with-references/accounts-gallery.png)

> [!IMPORTANT]
> 在本主题中，图形会显示一些名称和其他值，这些值不是随 Common Data Service 附带的示例数据的一部分。 这些步骤准确说明了如何为特定结果配置控件，但你的体验因你的组织的数据而异。

若要在库中显示每个帐户的所有者，可能会尝试使用公式**ThisItem.Owner.Name**。 但是，"**团队**" 实体中的 "名称" 字段为 "**团队名称**"，而 "**用户**" 实体中的 "名称" 字段为 "**全名**"。 在运行应用程序之前，应用程序无法知道您正在使用哪种类型的查找，并且它可以在 "**帐户**" 实体中的记录之间变化。

需要一个可适应此方差的公式。 还需要为**所有者**可以为的实体类型（在本例中为**用户**和**团队**）添加数据源。 将以下三个数据源添加到应用：

> [!div class="mx-imgBorder"]
> !["数据" 窗格中的 "帐户"、"团队" 和 "用户" 实体](media/working-with-references/accounts-datasources.png)

准备好这些数据源后，使用此公式显示用户或团队的名称：

```powerapps-dot
If( IsType( ThisItem.Owner, [@Teams] ),
    "Team: " & AsType( ThisItem.Owner, [@Teams] ).'Team Name',
    "User: " & AsType( ThisItem.Owner, [@Users] ).'Full Name' )
```

> [!div class="mx-imgBorder"]
> 库控件中显示的 ![帐户，其中显示了 "所有者" 字段](media/working-with-references/accounts-displayowner.png)

在此公式中， **IsType**函数针对 "**团队**" 实体测试 "**所有者**" 字段。 如果它属于该实体类型，则**AsType**函数会将其转换为**团队**记录。 此时，你可以使用访问 "**团队**" 实体的所有字段（包括**团队名称**） *。字段*表示法。 如果**IsType**确定**所有者**不是 "**团队**" 实体中的记录，则该字段必须是 "**用户**" 实体中的记录，因为 "**所有者**" 字段是必需的（不能为*空*）。

你使用 **[@Teams]** 和 **[@Users]** 的[全局歧义消除运算符](functions/operators.md#disambiguation-operator)来确保你使用的是全局实体类型。 在这种情况下，您不需要它，但最好的方法是进行构建。 一对多关系通常在库的记录范围内发生冲突，这种做法可以避免这种混乱。

若要使用记录引用的任何字段，必须首先使用**AsType**函数将其转换为特定的实体类型。 不能直接从 "**所有者**" 字段访问字段，因为系统不知道要使用的实体类型。

如果**所有者**字段与请求的实体类型不匹配， **AsType**函数将返回错误，因此可以使用**IfError**函数来简化此公式。 首先，打开实验性功能**公式级别错误管理**：

> [!div class="mx-imgBorder"]
> ![试验开关来启用公式级别的错误管理](media/working-with-references/accounts-iferror.png)

然后，将上一个公式替换为此公式：

```powerapps-dot
IfError(
    "Team: " & AsType( ThisItem.Owner, [@Teams] ).'Team Name',
    "User: " & AsType( ThisItem.Owner, [@Users] ).'Full Name' )
```

## <a name="filter-based-on-an-owner"></a>基于所有者进行筛选

恭喜-您已经完成了使用记录引用的最难的方面。 其他用例更简单一些，因为它们不访问记录字段。 例如，在本部分中，我们将对此进行探讨。

将**组合框**控件添加到库上方，并设置新控件的以下属性：

- **项**： `Users`
- **SelectMultiple**： `false`

> [!div class="mx-imgBorder"]
> ![在库上添加了项属性设置为 "用户" 的组合框控件](media/working-with-references/filter-insert-combobox.png)

若要按从此组合框中选择的特定用户筛选库，请将库的**Items**属性设置为以下公式：

```powerapps-dot
Filter( Accounts, Owner = ComboBox1.Selected )
```

> [!div class="mx-imgBorder"]
> ![基于组合框控件中的值集筛选的库](media/working-with-references/filter-accounts.png)

> [!IMPORTANT]
> 如果你严格执行这些步骤，本主题中的说明是准确的。 但是，如果该控件具有不同的名称，则按名称引用该控件的任何公式都将失败。 如果删除并添加了相同类型的控件，则控件名称末尾的数字会发生更改。 对于任何显示错误的公式，确认它包含所有控件的正确名称。

不需要使用**IsType**或**AsType** ，因为您要将记录引用与其他记录引用或完整记录进行比较。 应用知道**combobox1.location**的实体类型，因为它派生自**用户**实体。 所有者为组的帐户不会与筛选条件匹配。

通过支持用户或团队的筛选，你可以获得一点的别致。

1. 通过调整库的大小并移动组合框来使屏幕顶部附近有一些空间，在库上方插入一个[**收音机**控件](controls/control-radio.md)，然后为新控件设置以下属性：

    - **项**： `[ "All", "Users", "Teams" ]`
    - **布局**： `Layout.Horizontal`

1. 对于**组合框**控件，设置此属性（如果组合框消失，请在单选控件中选择 "**用户**"）：

    - **可见**： `Radio1.Selected.Value = "Users"`

1. 复制并粘贴**组合框**控件，直接将副本移到原始副本上，然后为副本设置以下属性：

    - **项**： `Teams`
    - **可见**： `Radio1.Selected.Value = "Teams"`

    应用将一次只显示一个组合框，具体取决于单选控件的状态。 由于它们彼此直接在一起，它们看起来像是更改其内容的相同控件。

1. 最后，将**库**控件的**Items**属性设置为以下公式：

    ```powerapps-dot
    Filter( Accounts,
        Radio1.Selected.Value = "All"
        Or (Radio1.Selected.Value = "Users" And Owner = ComboBox1.Selected)
        Or (Radio1.Selected.Value = "Teams" And Owner = ComboBox1_1.Selected)
    )
    ```

    > [!div class="mx-imgBorder"]
    > 显示所有记录或特定用户或团队的 ![筛选库](media/working-with-references/filter-combobox.png)

进行这些更改后，可以显示所有记录，也可以基于用户或团队筛选它们：

> [!div class="mx-imgBorder"]
> 基于单选控件和组合框显示不同筛选结果的 ![动画](media/working-with-references/filter-allthree.gif)

公式是完全可委派的。 比较单选按钮值的部分是所有记录中的常量，并在筛选器的其余部分发送到 Common Data Service 之前进行计算。

如果要筛选所有者的类型，可以使用**IsType**函数，但尚不可委派。

> [!div class="mx-imgBorder"]
> 使用 IsType 按所有者类型 ![筛选](media/working-with-references/filter-bytype.png)

## <a name="update-the-owner-by-using-patch"></a>使用修补程序更新所有者

您可以用与任何其他查找相同的方式更新 "**所有者**" 字段。 若要将当前所选帐户的所有者设置为第一个团队：

```powerapps-dot
Patch( Accounts, Gallery1.Selected, { Owner: First( Teams ) } )
```

此方法不会与常规查找不同，因为应用知道**第一个（团队）** 的类型。 如果要改为第一个用户，请将该部分替换为**第一个用户（用户）** 。 **Patch**函数知道可以将 "**所有者**" 字段设置为这两种实体类型中的任何一个。

若要将此功能添加到应用：

1. 在 "**树视图**" 窗格中，同时选择**单选**控件和两个**组合框**控件。

1. 在省略号菜单上，选择 "**复制这些项**"。

    > [!div class="mx-imgBorder"]
    > 使用树视图 ![多个控件的副本](media/working-with-references/patch-copy.png)

1. 在同一菜单上，选择 "**粘贴**"。

    > [!div class="mx-imgBorder"]
    > 使用树视图 ![粘贴多个控件](media/working-with-references/patch-paste.png)

1. 将复制的控件移到库的右侧。

    > [!div class="mx-imgBorder"]
    > ![将复制的控件移到库的右侧](media/working-with-references/patch-position.png)

1. 选择已复制的**收音机**控件，然后更改以下属性：

    - 项： `[ "Users", "Teams" ]`
    - 默认值： `If( IsType( Gallery1.Selected.Owner, Users ), "Users", "Teams" )`

    > [!div class="mx-imgBorder"]
    > ![从单选控件中删除了所有选择](media/working-with-references/patch-noall.png) 

1. 在**单选**控件中，选择 "**用户**"，以使列出用户的**组合框**控件可见。

1. 选择可见的**组合框**控件，然后将 " **DefaultSelectedItems** " 属性设置为以下公式：

    ```powerapps-dot
    If( IsType( Gallery1.Selected.Owner, Users ),
        AsType( Gallery1.Selected.Owner, Users ),
        Blank()
    )
    ```

    > [!div class="mx-imgBorder"]
    > !["用户" 组合框的默认属性集](media/working-with-references/patch-default-users.png)

1. 在**单选**控件中，选择 "**团队**" 以便列出团队的**组合框**控件可见。

1. 选择要对用户进行的不可见**组合框**控件选择的**单选**控件。

1. 为团队选择可见的**组合框**控件，然后将其**DefaultSelectedItems**属性设置为以下公式：

    ```powerapps-dot
    If( IsType( Gallery1.Selected.Owner, Teams ),
        AsType( Gallery1.Selected.Owner, Teams ),
        Blank()
    )
    ```

    > [!div class="mx-imgBorder"]
    > 为 "团队" 组合框 ![默认属性集](media/working-with-references/patch-default-teams.png)

1. 插入**按钮**控件，将其移动到**组合框**控件下，然后将该按钮的**Text**属性设置为 `"Patch Owner"`。

1. 将该按钮的**OnSelect**属性设置为以下公式：

    ```powerapps-dot
    Patch( Accounts, Gallery1.Selected,
        { Owner: If( Radio1_1.Selected.Value = "Users",
                ComboBox1_2.Selected,
                ComboBox1_3.Selected ) } )
    ```

    > [!div class="mx-imgBorder"]
    > 在按钮控件上设置 ![公式](media/working-with-references/patch-button.png)

复制的**单选按钮**和**组合框**控件显示库中当前选定帐户的所有者。 使用相同的控件，可以通过选择按钮将帐户的所有者设置为任何团队或用户：

> [!div class="mx-imgBorder"]
> 显示具有用户或团队的所有者修补程序的 ![动画](media/working-with-references/patch-allthree.gif)

## <a name="show-the-owner-by-using-a-form"></a>使用窗体显示所有者

可以通过添加自定义卡片在窗体中显示**所有者**字段。 在撰写本文时，您不能使用窗体控件来更改字段的值。

1. 插入 "**编辑窗体**" 控件，然后调整其大小，并将其移动到右下角。

1. 在屏幕右侧附近的 "**属性**" 选项卡上，打开 "**数据源**" 列表，然后选择 "**帐户**"。

    > [!div class="mx-imgBorder"]
    > 显示具有空白值的其他字段的 ![窗体控件](media/working-with-references/form-insert.png)  

1. 将窗体的**Item**属性设置为 `Gallery1.Selected`。

    > [!div class="mx-imgBorder"]
    > ![窗体控件，显示从库中的选定项填充的其他字段](media/working-with-references/form-item.png)

1. 在屏幕右侧附近的 "**属性**" 选项卡上，选择 "**编辑字段**"。

1. 在 "**字段**" 窗格中，选择省略号，然后选择 "**添加自定义卡片**"。

    > [!div class="mx-imgBorder"]
    > 用于添加自定义卡的 ![命令](media/working-with-references/form-customcard.png)

    新卡将显示在窗体控件的底部。

1. 根据需要调整卡大小以显示所有文本。

    > [!div class="mx-imgBorder"]
    > ![插入的自定义卡，空白](media/working-with-references/form-inserted-customcard.png)

1. 将 "**标签**" 控件插入自定义卡，然后将标签的 " **Text** " 属性设置为在库中使用的公式：

    ```powerapps-dot
    If( IsType( ThisItem.Owner, Teams ),
        "Team: " & AsType( ThisItem.Owner, Teams ).'Team Name',
        "User: " & AsType( ThisItem.Owner, Users ).'Full Name' )
    ```

    > [!div class="mx-imgBorder"]
    > ![自定义卡，其中显示 "标签" 控件中的 "所有者" 字段](media/working-with-references/form-displayowner.png)

对于库中的每个选择，包含记录的所有者的帐户的更多字段将显示在窗体中。 如果使用 "**修补程序**" 按钮更改所有者，窗体控件也会显示该更改。

> [!div class="mx-imgBorder"]
> ![动画显示对库中的更改做出响应的窗体控件](media/working-with-references/form-allthree.gif)

## <a name="show-the-fields-of-a-customer"></a>显示客户的字段

在 Common Data Service 中，**客户**查找字段是另一个多态查找，它非常类似于**所有者**。

**所有者**限制为每个实体一个，但实体可包括零个、一个或多个**客户**查找字段。 "**联系人**系统" 实体包括 "**公司名称**" 字段，该字段是 "**客户**查找" 字段。

> [!div class="mx-imgBorder"]
> ![联系人实体将公司名称字段显示为不需要的客户数据类型](media/working-with-references/customer-companyname.png)

您可以通过为新字段选择**customer**数据类型，将更多**客户**查找字段添加到实体。

![创建字段时数据类型列表中的客户数据类型](media/working-with-references/customer-datatype.png)

**客户**查找字段可以引用**帐户**实体或**联系人**实体中的记录。 对于这些实体，你将使用**IsType**和**AsType**函数，因此现在可以将其添加为数据源（你可以将**团队**和**用户**保持为原位）。

> [!div class="mx-imgBorder"]
> "数据" 窗格中 ![帐户、团队、用户和联系人实体](media/working-with-references/customer-datasources.png)

"**客户**" 和 "**所有者**" 字段的处理与此类似，你可以按字面复制应用（**文件** > "**另存为**"，然后指定其他名称）并进行以下简单替换：

| Location | **所有者**示例 | **客户**示例 |
|----------|-----------|------------------|
| 通用 | **Owner** | **"Customer Name"** |
| 通用 | **那些** | **帐户** |
| 通用 | **协作** | **人** |
| 库的**Items**属性 | **帐户** | **人** |
| 窗体的**Items**属性 | **帐户** | **人** |
| **Patch**的第一个参数<br>在按钮的**OnSelect**属性中 | **帐户** | **人** |
| 筛选广播的**Items**属性 | **[&nbsp;"所有"，&nbsp;"Users"，&nbsp;"团队"&nbsp;]** | **[&nbsp;"所有"，&nbsp;"Accounts"，&nbsp;"Contacts"&nbsp;]** |
| 修补程序广播的**Items**属性 | **["Users"，"团队"]** | **["Accounts"，"Contacts"]** |
| 组合框的**Visible**属性 | **"用户"** 和 **"团队"** | **"帐户"** 和 **"联系人"** |

例如，新库应具有此**Items**属性：

```powerapps-dot
Filter( Contacts,
    Radio1.Selected.Value = "All"
    Or (Radio1.Selected.Value = "Accounts" And 'Company Name' = ComboBox1.Selected)
    Or (Radio1.Selected.Value = "Contacts" And 'Company Name' = ComboBox1_1.Selected)
)
```

> [!div class="mx-imgBorder"]
> 从应用了简单更改的所有者应用派生的 ![客户应用](media/working-with-references/customer-simple-update.png)

**客户**和**所有者**之间的两个重要区别要求更新库中的公式和窗体：

1. 当你按名称引用这些实体类型时，**帐户**与**联系人**之间的一对多关系优先。 使用 **\[\@帐户]** ，而不是使用**帐户**;使用 **\[\@联系人]** ，而不是使用**联系人**。 通过使用[全局歧义消除运算符](functions/operators.md#disambiguation-operator)，可以确保引用**IsType**和**AsType**中的实体类型。 此问题仅存在于库和窗体控件的记录上下文中。

1. "**所有者**" 字段必须具有值，但 "**客户**" 字段可以为*空*。 若要在没有类型名称的情况下显示正确的结果，请使用[ **IsBlank**函数](functions/function-isblank-isempty.md)测试这种情况，并改为显示空的文本字符串。

这两个更改都采用相同的公式，该公式显示在窗体的自定义卡片中，以及库的标签控件的**Text**属性中：

```powerapps-dot
If( IsBlank( ThisItem.'Company Name' ), "",
    IsType( ThisItem.'Company Name', [@Accounts] ),
        "Account: " & AsType( ThisItem.'Company Name', [@Accounts] ).'Account Name',
    "Contact: " & AsType( ThisItem.'Company Name', [@Contacts] ).'Full Name'
)
```

> [!div class="mx-imgBorder"]
> ![更新到库中副标题标签控件的 "文本" 属性](media/working-with-references/customer-update.png)

进行这些更改后，可以在 "**联系人**" 实体中查看和更改 "**公司名称**" 字段。

> [!div class="mx-imgBorder"]
> ![显示选择联系人如何更改其他控件和窗体的动画](media/working-with-references/customer-allthree.gif)

## <a name="understand-regarding-lookup-fields"></a>了解查找字段

"**关于**查找" 字段与你已在本主题中使用过的 "关于查找" 字段有所不同。 首先要应用本主题前面所述的模式，然后学习其他技巧。

您只能开始处理 "**传真**" 实体。 此实体具有多态**相关**的查找字段，可引用**帐户**、**联系人**和其他实体。 你可以将应用程序用于**客户**并对其进行**修改，以**供客户使用。

| Location | **客户**示例 | **传真**示例 |
|----------|-----------|------------------|
| 通用 | **"Customer Name"** | **联系** |
| 库的**Items**属性 | **人** | **传真** |
| 窗体的**Items**属性 | **人** | **传真** |
| **Patch**的第一个参数<br> 在按钮的**OnSelect**属性中 | **人** | **传真** |

同样，您需要添加一个数据源：这次用于**传真**。 在 "**视图**" 选项卡上，选择 "**数据源**"：

> [!div class="mx-imgBorder"]
> 显示帐户、团队、用户、联系人和传真实体 ![数据窗格](media/working-with-references/faxes-datasources.png)

与**相关**的重要区别在于，它并不限于**帐户**和**联系人**。 事实上，实体列表可通过自定义实体进行扩展。 大多数应用程序无需修改即可容纳此点，但必须为库中的标签和窗体更新公式：

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
> 关于查找的副标题控件 ![更新的 Text 属性](media/working-with-references/regarding-label.png)

进行这些更改后，可以像处理**所有者**和**客户**查找一样处理**相关**查找。

> [!div class="mx-imgBorder"]
> ![显示选择库中的项如何更改其他控件和窗体的动画](media/working-with-references/regarding-allthree.gif)

## <a name="understand-regarding-relationships"></a>了解相关关系

**相关**关系不同于**所有者**和**客户**，因为前者涉及多对一关系。 按照定义，反向、一对多关系允许您**首先编写（帐户）。传真**。

让我们备份并查看实体定义。 在 Common Data Service 中，诸如**传真**、**任务**、**电子邮件**、**说明**、**电话呼叫**、**信件**和**聊天**等实体都指定为[*活动*](../../developer/common-data-service/activity-entities.md)。 您还可以创建自己的[自定义活动实体](../../developer/common-data-service/custom-activities.md)。 查看或创建活动实体时，其设置将显示在 "**其他设置**" 下。

![创建实体时的活动实体设置](media/working-with-references/activity-entitytype.png)

如果将其他实体启用为实体设置中的*活动任务*，则可以将这些实体与活动实体相关联。 因此，会在 "**更多设置**" 下指定**帐户**、**联系人**和其他许多标准实体。

![创建实体时的活动任务设置](media/working-with-references/activity-entityuse.png)

所有活动实体和活动-任务实体都具有隐含的关系。 如果将筛选器更改为屏幕顶部的 "**全部**"，请选择 "**传真**" 实体，然后选择 "**关系**" 选项卡，此时将显示可以作为**相关**查找目标的所有实体。

> [!div class="mx-imgBorder"]
> 显示有关多对一关系的 "传真" 实体 ![关系](media/working-with-references/activity-manytoone.png)

如果显示 "**帐户**" 实体的关系，则将显示可以是 "**相关**查找" 字段的源的所有实体。

> [!div class="mx-imgBorder"]
> 显示关于一对多关系的 Account 实体 ![关系](media/working-with-references/activity-onetomany.png)

这是什么意思？

- 编写公式时，必须考虑活动实体列表不是固定的，你可以创建自己的实体。 公式必须适当地处理您不需要的活动实体。
- 活动任务和活动具有一对多关系。 您可以轻松请求与某个帐户相关的所有传真。

若要在应用中浏览此概念：

1. 添加另一个屏幕。

    > [!div class="mx-imgBorder"]
    > ![插入空白屏幕](media/working-with-references/activitypointer-newscreen.png)

1. 插入库控件并调整其大小，然后将其移到屏幕的左侧。

1. 在屏幕右侧附近的 "**属性**" 选项卡上，将库的**项目**设置为 "**帐户**"。

    > [!div class="mx-imgBorder"]
    > ![在 "属性" 窗格中将项目设置为帐户](media/working-with-references/activitypointer-accounts.png)

1. 将库的 "布局" 设置为 "**标题**"，然后将 "标题" 字段设置为 "**帐户名**"。

    > [!div class="mx-imgBorder"]
    > ![在 "属性" 窗格中设置库控件的标题布局](media/working-with-references/activitypointer-account-name.png)

1. 添加第二个库，调整其大小，然后将其移到屏幕的右侧。

1. 将新库的**Items**属性设置为 `Gallery2.Selected.Faxes`。

    此步骤将返回筛选后的给定帐户的传真列表。

    > [!div class="mx-imgBorder"]
    > ![设置显示传真的库的 Items 属性](media/working-with-references/activitypointer-faxes.png)

1. 将库的布局设置为**标题和副标题**，然后将 "标题" 字段设置为显示 "**使用者**" 字段（可能**为小写）** 。

    > [!div class="mx-imgBorder"]
    > ![将标题设置为使用者字段](media/working-with-references/activitypointer-subject.png)

在帐户列表中选择一项时，传真列表仅显示该帐户的传真。

> [!div class="mx-imgBorder"]
> ![动画显示传真列表驱动的帐户库中的选择](media/working-with-references/activitypointer-allthree.gif)

## <a name="activity-entity"></a>活动实体

如前一部分所述，您可以显示一个帐户的所有传真。 但是，还可以显示帐户的所有活动，包括传真、电子邮件、电话呼叫和其他交互。

对于后一种情况，可以使用 "**活动**" 实体。 您可以通过打开右上角的 "**所有**" 来显示此实体，以从实体列表中删除该筛选器。

> [!div class="mx-imgBorder"]
> 显示活动实体的实体 ![列表](media/working-with-references/activitypointer-entity.png)

**活动**实体是特殊的。 每次向 "**传真**" 实体中添加一条记录时，系统还会在 "**活动**" 实体中创建一条记录，其中包含所有活动实体的公用字段。 在这些字段中，"**主题**" 是最有趣的一项。

通过只更改上一示例中的一行，可以显示所有活动。 将 `Gallery2.Selected.Faxes` 替换为 `Gallery2.Selected.Activities`。

> [!div class="mx-imgBorder"]
> ![更改第二个库的 Items 属性，从传真更改为活动](media/working-with-references/activitypointer-gallery.png)

记录来自**活动**实体，但你仍可以使用**IsType**函数来标识它们的活动类型。 同样，在将**IsType**与实体类型一起使用之前，必须添加数据源。

> [!div class="mx-imgBorder"]
> ![数据 "窗格中显示 IsType 函数所需的所有实体](media/working-with-references/activity-datasources.png)

通过使用此公式，可以在 "标签" 控件中的 "库" 中显示 "记录类型"：

```powerapps-dot
If( IsType( ThisItem, [@Faxes] ), "Fax",
    IsType( ThisItem, [@'Phone Calls'] ), "Phone Call",
    IsType( ThisItem, [@'Email Messages'] ), "Email Message",
    IsType( ThisItem, [@Chats] ), "Chat",
    "Unknown"
)
```

> [!div class="mx-imgBorder"]
> ![将 text 属性设置为公式，以显示有关传真、电话呼叫和其他活动的信息](media/working-with-references/activitypointer-type.png)

还可以使用**AsType**访问特定类型的字段。 例如，此公式确定每个活动的类型，对于电话呼叫，将**显示电话号码实体的**电话号码和呼叫方向：

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
> ![扩展的 text 属性，包含电话呼叫的详细信息](media/working-with-references/activitypointer-phonecall.png)

因此，该应用程序会显示活动的完整列表。 对于所有类型的活动都会显示 "**使用者**" 字段，而无论公式是否将其考虑。 对于你知道的活动类型，可以显示有关每个活动的类型名称和特定类型的信息。

> [!div class="mx-imgBorder"]
> 显示不同类型的活动的信息的 ![完成屏幕](media/working-with-references/activitypointer-complete.png)

## <a name="notes-entity"></a>备注实体

到目前为止，所有**相关**示例均基于活动，但**注释**实体表示另一种情况。

创建实体时，可以启用附件。

> [!div class="mx-imgBorder"]
> ![在创建实体时启用附件和备注](media/working-with-references/notes-entity.png)

如果选中 "启用附件" 复选框，则将创建与 "**注释**" 实体的**相关**关系，如下图所示为 "**帐户**" 实体：

> [!div class="mx-imgBorder"]
> 通过一对多关系显示与说明的关系的 ![帐户实体](media/working-with-references/notes-relationships.png)

除这种差异外，还可以使用与使用活动**相同的方式查找。** 为附件启用的实体与**注释**具有一对多关系，如以下示例中所示：

`First( Accounts ).Notes`

> [!NOTE]
> 在撰写本文时，"**相关**查找" 不适用于 "**注释**" 实体。 不能根据**相关**字段进行读取或筛选，也不能使用**Patch**来设置字段。
>
> 不过，可以使用 "反向**注释**一对多" 关系，以便筛选为附件启用的记录的注释列表。 您还可以使用 "[**关联**](functions/function-relate-unrelate.md)函数" 向记录的**注释**表中添加注释，但必须先创建注释，如本示例所示：
>
>`Relate( ThisItem.Notes, Patch( Notes, Defaults( Notes ), { Title: "A new note" } ) )`

## <a name="activity-parties"></a>活动方

在撰写本文时，画布应用不支持活动方。