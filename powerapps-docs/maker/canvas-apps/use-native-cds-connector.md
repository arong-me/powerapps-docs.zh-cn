---
title: 升级为使用本机 Common Data Service 连接器 |Microsoft Docs
description: ''
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 03/03/2020
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: e77bf1304ac7d1083348dce18d7d78189dfef306
ms.sourcegitcommit: 56c8c7cc64695ccb00e0d021c9f98cf70b69b4a2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78845367"
---
# <a name="common-data-service-and-the-improved-data-source-experience"></a>Common Data Service 和改进的数据源体验

## <a name="overview"></a>概述

如果在2019年11月之前创建了一个带有 Common Data Service 连接器的画布应用，则可能没有 Common Data Service 的最新版本的权益。 

"**改善数据源体验" 和 "Common Data Service 视图**" 选项具有以下优势：

1. 显著提高速度。
2. 提高了可靠性。
3. Common Data Service**视图**和**文件和图像字段属性**的访问权限。

"高级设置" 部分显示了 "**改善数据源体验和 Common Data Service 视图**" 选项：

![改善数据源体验和 Common Data Service 视图](media/use-native-cds-connector/improved-data-source-setting.png)

"已弃用的功能" 部分中将显示**Common Data Service 的关系数据、选项集以及其他新功能**。

## <a name="how-do-i-upgrade"></a>如何实现升级？

通过检查功能的设置，然后按照下面的说明来升级应用程序：

### <a name="improve-data-source-experience-and-common-data-service-views-is-on"></a>*改善数据源体验，并 Common Data Service 视图*：

你已将画布应用转换为使用此功能，或者已*使用的默认设置为此*功能启动了应用。 无需执行其他操作。 

你可能还希望启用**显式列选择**功能：

![显式列选择](media/use-native-cds-connector/explicit-column-selection.png)

> [!NOTE]
> [适用于 Windows 的 Power Apps](https://www.microsoft.com/p/power-apps/9nblggh5z8f3)不支持**改善数据源体验和 Common Data Service 视图**。 使用适用于 Windows 的 Power *Apps 时，必须关闭此*功能。

### <a name="relational-data-option-sets-and-other-new-features-for-common-data-service-is-off"></a>*关系数据、选项集和其他 Common Data Service 的新功能*已关闭：

检查 "*高级设置*" 下的 "*弃用的功能*" 部分。  如果设置为*Off*，则继续执行以下说明，作为转换的第一步。 

> [!IMPORTANT]
> 如果在 "*高级设置*" 中看不到 "**关系数据"、"选项集" 和 "其他新 Common Data Service 功能**"，或者如果已*打开*，请跳过以下步骤，转到[下一节](#improve-data-source-experience-and-common-data-service-views-is-off)。

- **步骤 1**：启用 "**使用显示名称** **"** 功能：
    
    1. 启用 "**使用显示名称** *"* 功能。
    1. 等待运行状况监视器完成对应用程序的分析。
    1. 保存、关闭并重新打开应用。
    1. 解决所有公式错误。
    1. 保存、关闭并重新打开应用。
    
    *可能的错误和建议*：
    
    某些新显示的显示名称可能与其他实体、字段或控件的显示名称冲突。 例如，你可能有一个具有相同名称的控件和字段。 可以更改具有唯一值的控件名称以解决问题。
    
    对于任何字段和实体显示名称冲突，你可能会看到一个需要实体但解析为本地作用域内字段名称的公式。

    将方括号与 **@** 符号一起使用，以指示全局范围，使其解析为实体;例如， **[@entityName]** 。
    
    
- **步骤 2**：**为 Common Data Service 打开关系数据、选项集和其他新功能**，并**使用 GUID 数据类型，而不是中的字符串**功能：
    
    1. **为启用 Common Data Service 功能的关系数据、选项集和其他新功能** *。*
    1. 启用**使用 GUID 数据类型而不是字符串***功能。*
    1. 等待运行状况监视器完成对应用程序的分析。
    1. 解决所有公式错误。
    1. 保存、关闭并重新打开应用。  
    
    *可能的错误和建议*：
    
    如果使用的是选项集字段或硬编码 GUID 文本值，则可能会在此阶段出现错误。  <br><br> 
    
    - *选项集值*：如果将选项集字段与选项集值的文本标识符一起使用，请改用点表示法来引用选项集值。 例如，将 `Patch(Accounts, OptionSet1 = “12345”)` 更改为 `Patch(Accounts, OptionSet.Item1)` where `Item1` 对应于 `12345` 值。 <br>
    有关详细信息，请参阅[详细示例](#detailed-examples)部分。
    - *Guid*：如果使用的是静态 guid 字符串（如 `015e45e1044e49f388115be07f2ee116`），请将其转换为返回 GUID 对象的函数;例如 `GUID(“015e45e1044e49f388115be07f2ee116”)`。 
    - *查找*：如果使用查找函数获取第一级查找值（如 `Lookup(Contacts, ‘contactID’ = ThisItem.ContactID”)`），请考虑改用 `ThisItem.PrimaryContacts` （其中 PrimaryContacts 是实体的名称）。

### <a name="improve-data-source-experience-and-common-data-service-views-is-off"></a>*改善数据源体验和 Common Data Service 视图*已关闭：

使用以下指令来打开 "**改善数据源体验" 和 "Common Data Service 视图** *"* 功能：

1. 删除现有 Common Data Service 数据源连接。 
1. 启用 *"* **改善数据源体验和 Common Data Service 视图**" 功能。
1. 使用新的数据源选择体验添加 Common Data Service 连接。
1. 保存应用程序。

> [!NOTE]
> 如果你的应用程序非常大，则添加数据源连接可能需要一段时间。 在此过程中不会关闭应用程序。

## <a name="converting-canvas-apps-with-the-dynamics-365-connector"></a>用 Dynamics 365 连接器转换画布应用

若要转换使用 Dynamics 365 连接器的应用，需要删除与数据源的连接并将其添加到数据源。 使用以下步骤将连接转换为你的数据源。

1. 确保已启用 "**改善数据源体验和 Common Data Service 视图**"*功能。*
2. 删除现有 Dynamics 365 数据源连接。
3. 使用新的数据源选择体验，将到数据源的连接添加到 Common Data Service。 

    > [!NOTE] 
    > 如果您连接到其他环境（"当前" 除外），请选择 "*实体*" 类别，然后选择 "*更多*（...）" 选项来更改环境。 然后，可以从其他环境中选择要添加到应用程序中的实体。 跨租户连接不能与改进的本机连接器一起使用。 你需要使用数据集成来访问跨租户的数据。
4.  保存应用程序。

*可能的错误和建议*：

转换时，可能会出现错误：如果使用的是 GUID 字符串，或者使用的是选项集字段，则可以在转换时使用 "显示名称"。

- 如果控件名称冲突，请将该控件的名称更改为不同并且唯一。 
- 对于字段和实体显示名称冲突，可能会看到一个公式，该公式应为实体，但解析为更本地的作用域内字段名称。 将方括号与 *@* 符号一起使用，以指示全局范围，使其解析为实体;例如， **[@entityName]** 。
- *选项集值*：如果将选项集字段与选项集值的文本标识符一起使用，请改用点表示法来引用选项集值。 例如，将 `Patch(Accounts, OptionSet1 = “12345”)` 更改为 `Patch(Accounts, OptionSet.Item1)` where `Item1` 对应于 `12345` 值。 <br>
有关详细信息，请参阅[详细示例](#detailed-examples)部分。
- *Guid*：如果使用的是静态 guid 字符串（如 `015e45e1044e49f388115be07f2ee116`），请将其转换为返回 GUID 对象的函数;例如 `GUID(“015e45e1044e49f388115be07f2ee116”)`。 
- *查找*：如果使用查找函数获取第一级查找值（如 `Lookup(Contacts, ‘contactID’ = ThisItem.ContactID”)`），请考虑改用 `ThisItem.PrimaryContacts` （其中 PrimaryContacts 是实体的名称）。
- 对于任何多态引用，请参阅下面的详细示例部分。 

## <a name="detailed-examples"></a>详细示例

在升级应用程序时，转换应用程序以使用新的**选项集**和**两个选项**数据类型可能会有挑战性，同时，升级应用以使用新的*改进数据源体验和 Common Data Service 视图*功能。

### <a name="option-sets"></a>选项集

为之前的选项集使用了单独的 `_myfield` 和 `_myfield_label` 字段。 现在，可以使用单个 `myfield` 来实现与区域设置无关的比较和获取特定于区域设置的标签。

#### <a name="removing-and-adding-option-set-data-cards"></a>删除和添加选项集数据卡

建议删除现有数据卡并将其重新添加到选项集。 例如，如果使用 "帐户" 实体和 "类别" 选项集，您将看到数据卡的 " *DataField* " 属性设置为 `_accountcategorycode_label`。 在字段列表中，可以看到数据卡的类型为*字符串*：

![具有旧样式名称的集](./media/use-native-cds-connector/OptionSet-with-old-style-name.png)

利用新的*改进数据源体验和 Common Data Service 视图*功能，你将不再看到 `_accountcategorycode_label`。 它被 `accountcategorycode`替换。 现在，你的卡将标记为 "**自定义**"，你会看到错误。 删除旧的数据卡，并将*选项设置*为 "后退"。 新数据卡是*选项*"感知"。

![具有旧样式名称的集](./media/use-native-cds-connector/OptionSet-with-new-style-name.png)

#### <a name="editing-the-option-set-filter-expressions-to-use-new-syntax"></a>编辑选项 "设置筛选器表达式以使用新语法"

以前，如果想要在筛选器表达式中使用选项集值，则需要使用 "*值*" 字段。 例如：

```powerapps-dot
Filter(Account,'Category Value' = "1")
```

需要编辑此公式。 选项集文本标识符不再用于值。 应更新此表达式以查找以下内容：

```powerapps-dot
Filter(Account, Category= ‘Category (Accounts)’.’Preferred Customer’)
```

"Category （Accounts）" 是 "帐户" 实体的 "类别" 字段中使用的枚举的名称。 这是一个本地选项集。  可在此处阅读有关本地和全局选项集的详细信息：[全局选项集。](https://docs.microsoft.com/powerapps/maker/common-data-service/create-edit-global-option-sets)

#### <a name="editing-option-set-patch-statements-to-use-new-syntax"></a>编辑选项集修补语句以使用新语法

下面是选项集的早期修补语句示例：

```powerapps-dot
Patch( Accounts, First(Accounts), { ‘Category Value’: 1 } ) )
```

你需要更新语句以遵循此形式：

```powerapps-dot
Patch( Accounts, First(Accounts), { Category: ‘Category (Accounts)’.’Preferred Customer’ } )
```

#### <a name="option-set-disambiguation"></a>选项集歧义消除

如果选项集**字段**的显示名称和选项集的名称相同，则需要消除公式的歧义。 若要继续使用帐户类别代码示例， **@** 意味着使用选项集，而不是字段。

```powerapps-dot
Filter(Accounts, 'Category Code' = [@’Category Code’].'Preferred Customer')
```

### <a name="two-options"></a>两个选项

#### <a name="removing-and-adding-two-option-set-data-cards"></a>删除并添加两个选项集数据卡

您应该删除现有的数据卡，并将其重新添加回使用您的两个选项集。 数据类型之前被识别为简单的布尔值（例如 true/on 和 false/off），无标签：

![两个选项集-旧样式](./media/use-native-cds-connector/TwoOptionSet-Old.png)

随着新的*数据源体验和 Common Data Service 视图*功能的改进，你的卡现在将被标记为 "**自定义**"，并且你将看到错误。  删除旧的数据卡，并将选项设置为 "后退"。 添加后，默认情况下，你会看到一个编辑控件，其中包含两个选项。

![TwoOptionSet-新建](./media/use-native-cds-connector/TwoOptionSet-New.png)

如果你更喜欢使用布尔型字段的切换开关，则可以取消锁定数据卡，并改为将数据卡中的控件替换为切换。  还需要在切换上设置这些属性。

```powerapps-dot
Toggle1.Default = ThisItem.’Do not allow Bulk Emails’
Toggle1.TrueText = ‘Do not allow Bulk Emails (Accounts)’.’Do Not Allow’
Toggle1.FalseText = ‘Do not allow Bulk Emails (Accounts)’.Allow
DataCard.Value = If( Toggle1.Value,
    ‘Do not allow Bulk Emails (Accounts)’.’Do Not Allow’,
    ‘Do not allow Bulk Emails (Accounts)’.Allow )
```

![两个选项切换开关](./media/use-native-cds-connector/TwoOption-Toggle.png)

#### <a name="refining-two-option-patch-statements"></a>优化两个选项修补语句

使用带有两个选项的[Patch](./functions/function-patch.md)函数应 "按原样" 运行。 它支持直接使用 true 和 false，这与布尔值类似。 唯一的区别是，如果将值放入前面显示 true 和 false 的 "标签" 控件中，它现在将显示两个选项标签。

### <a name="polymorphic-lookups"></a>多态查找

以下准则有助于在应用程序引用多[态](working-with-references.md)字段时升级应用程序。 来自同一字段的多态查找支持引用多个实体的受限制集。  与其他语言中的引用类似，记录引用是指向特定实体中特定记录的指针。 记录引用与它一起使用实体信息，使其指向多个不同的其他实体中的记录，这不同于只能指向一个实体中的记录的一般查找。  

#### <a name="access-set-and-filter-on-the-owner-field-of-a-record"></a>对记录的 "所有者" 字段进行访问、设置和筛选

例如，实体中的 "所有者" 字段可以引用 "用户" 实体或 "团队" 实体中的记录。 不同记录中的相同查找字段可能引用不同实体中的记录。
 
![多态所有者字段](./media/use-native-cds-connector/Polymorphic1.png)
 
##### <a name="polymorphic-with-filter-and-patch"></a>带筛选器和修补程序的多态

可以像使用完整记录一样使用记录引用：

```powerapps-dot
Filter( Accounts, Owner = First( Teams ) )
Patch( Accounts, First( Accounts ), { Owner: First( Users ) })
```

##### <a name="polymorphic-with-a-gallery-displaying-owner-name"></a>具有显示所有者名称的库的多态

因为引用可指向不同的实体，所以必须是特定的。 不能使用**ThisItem.Owner.Name**，因为**团队**实体中的名称字段是**团队名称**，**用户**实体中的名称字段为**全名**。 在运行应用程序之前，Power Apps 不会知道您引用的是哪种类型的查询。

解决此问题： 

1. 为所有者可以添加的实体类型添加数据源;在当前的示例中，用户和团队）。
2. 使用其他功能，使意向清晰明了。

您可以使用以下两个新函数：

- IsType –检查记录引用是否为特定实体类型。
- AsType –将记录引用强制转换为特定实体类型。

使用这些函数，可以编写一个公式，该公式根据所有者的实体类型显示从两个不同命名字段获取的所有者的名称：

```powerapps-dot
If( IsType( ThisItem.Owner,  [@Teams]), 
    AsType( ThisItem.Owner, [@Teams]).'Team Name', 
    AsType( ThisItem.Owner, [@Users]).'Full Name' )
```

![类型为的库](./media/use-native-cds-connector/Polymorphic-And-AsType-in-Gallery.png)

`[@Teams]` 和 `[@Users]` 的全局歧义消除运算符用于确保引用全局实体类型。 虽然这种情况并不是必需的，但建议始终清楚。 一对多关系通常在库的记录范围内发生冲突，这种做法可以避免这种混乱。
 
#### <a name="access-and-set-the-company-name-field-a-customer-data-type-of-the-contacts-entity"></a>访问和设置联系人实体的 "公司名称" 字段（客户数据类型）

客户查找字段是类似于所有者的另一个多态查询。 对于每个实体，只能有一个所有者字段。 但一个实体可以包含零个、一个或多个客户查找字段。 "联系人系统" 实体包括 "公司名称" 字段，该字段是 "客户查找" 字段。 阅读[显示客户的字段](https://docs.microsoft.com/powerapps/maker/canvas-apps/working-with-references#show-the-fields-of-a-customer)了解更多详细信息。
 
#### <a name="access-and-set-the-regarding-field-of-activity-entities-such-as-faxes-phone-calls-email-messages"></a>访问和设置活动实体（如传真、电话呼叫和电子邮件）的相关字段

多态查找并不限于帐户和联系人。 实体列表可通过自定义实体进行扩展。 例如，"传真" 实体有一个多态相关查找字段，该字段可以引用帐户、联系人和其他实体。 如果有一个将数据源设置为 "传真" 的库，则可以使用以下公式显示与 "相关查找" 字段关联的名称。 
 
 ```powerapps-dot
If( IsBlank( ThisItem.Regarding ), "",
    IsType( ThisItem.Regarding, [@Accounts] ),
        "Account: " & AsType( ThisItem.Regarding, [@Accounts] ).'Account Name',
    IsType( ThisItem.Regarding, [@Contacts] ),
        "Contacts: " & AsType( ThisItem.Regarding, [@Contacts] ).'Full Name',
    "" )
```

![库与相关](./media/use-native-cds-connector/Polymorphic-With-Regarding.png)
 
有关详细信息，请阅读[相关查找字段](https://docs.microsoft.com/powerapps/maker/canvas-apps/working-with-references#understand-regarding-lookup-fields)和[相关关系](https://docs.microsoft.com/powerapps/maker/canvas-apps/working-with-references#understand-regarding-relationships)。

#### <a name="access-the-list-of-all-activities-for-a-record"></a>访问记录的所有活动的列表

在 Common Data Service 中，诸如传真、任务、电子邮件、说明、电话呼叫、信件和聊天等实体都指定为[活动](https://docs.microsoft.com/powerapps/developer/common-data-service/activity-entities)。 您还可以创建自己的[自定义活动实体](https://docs.microsoft.com/powerapps/developer/common-data-service/custom-activities)。

您可以显示特定类型的活动（如传真或税金），也可以显示与某个实体关联的所有活动，如 "帐户"。 添加活动实体和你计划在画布应用中显示其数据的其他单个实体。

每次向添加记录（例如 "任务" 实体）时，都将创建 "活动" 实体中的一条记录，其中包含所有活动实体的公用字段。 阅读[活动实体](https://docs.microsoft.com/powerapps/maker/canvas-apps/working-with-references#activity-entity)了解更多详细信息。

下面的示例显示，当你选择某个帐户时，将显示与该帐户关联的所有活动：
 
![多态活动](./media/use-native-cds-connector/Polymorphic-Activities.png) 
 
将从活动实体显示记录。 但你仍可以使用[IsType](./functions/function-astype-istype.md)函数来标识它们的活动类型。 同样，在将 IsType 与实体类型一起使用之前，必须添加所需的数据源。
 
通过使用此公式，可以在 "标签" 控件中的 "库" 中显示 "记录类型"：

 ```powerapps-dot
If( IsType( ThisItem, [@Faxes] ), "Fax",
    IsType( ThisItem, [@'Phone Calls'] ), "Phone Call",
    IsType( ThisItem, [@'Email Messages'] ), "Email Message",
    IsType( ThisItem, [@Chats] ), "Chat",
    "Unknown")
```

 ![多态-IsType](./media/use-native-cds-connector/Polymorphic-IsType.png)

#### <a name="access-the-list-of-notes-for-a-record"></a>访问记录的便笺列表

创建实体时，可以启用附件。 如果选中 "启用附件" 复选框，则将创建与 "注释" 实体的相关关系，如下图所示为 "帐户" 实体：

![注释-字段](./media/use-native-cds-connector/Notes-Field.png)

##### <a name="filtering"></a>筛选

无法根据相关字段进行读取或筛选。 不过，可以使用反向注释一对多关系。 若要列出与帐户实体相关联的所有注释，可以使用以下公式：

```powerapps-dot
First( Accounts ).Notes
```

##### <a name="patch"></a>修补程序

不能使用 Patch 来设置实体上的 "注释" 字段。 若要向实体的注释表中添加记录，可以使用 "关联函数"。 首先创建注释，如以下示例中所示：

```powerapps-dot
Relate( ThisItem.Notes, Patch( Notes, Defaults( Notes ), { Title: "A new note", isdocument:'Is Document (Notes)'.No } ) )
```

## <a name="next-steps"></a>后续步骤

- [公式参考](https://docs.microsoft.com/powerapps/maker/canvas-apps/formula-reference)
- [控件参考](https://docs.microsoft.com/powerapps/maker/canvas-apps/reference-properties)

### <a name="see-also"></a>另请参阅

[什么是 Common Data Service？](https://docs.microsoft.com/powerapps/maker/common-data-service/data-platform-intro)
