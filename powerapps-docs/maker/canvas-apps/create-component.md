---
title: 为画布应用创建组件 |Microsoft Docs
description: 画布应用的可重用组件简介
author: yifwang
ms.service: powerapps
ms.topic: article
ms.date: 02/20/2020
ms.author: yifwang
ms.reviewer: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: b86f6c94a7a267fc28a70216c6b89d154cd7b865
ms.sourcegitcommit: efb05dbd29c4e4fb31ade1fae340260aeba2e02b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2020
ms.locfileid: "78293215"
---
# <a name="create-a-component-for-canvas-apps"></a>为画布应用创建组件

> [!IMPORTANT]
> 此功能仍处于公共预览版中。 有关详细信息，请参阅[实验性功能和预览功能](working-with-experimental.md)。

组件是画布应用的可重复使用的构建基块，因此应用程序开发人员可以在应用内部或使用[组件库](component-library.md)跨应用创建要使用的自定义控件。 组件可使用高级功能，如自定义属性和启用复杂的功能。 本文介绍组件概念和一些示例。

组件可用于构建具有类似控件模式的大型应用程序。 如果更新应用内的组件定义，应用中的所有实例都将反映所做的更改。 组件还消除了复制/粘贴控件和提高性能所需的重复工作。 当你使用[组件库](component-library.md)时，组件还可帮助创建协作开发并使组织中的外观标准化。

## <a name="components-in-canvas-app"></a>画布应用中的组件

可以按照本文中所述，或在[组件库](component-library.md)中创建新的组件，从应用内创建组件。 应该使用组件库来要求跨多个应用屏幕使用组件。 你还可以将现有组件复制到现有或新的组件库中。

若要在应用中创建组件，请前往**树视图**，选择 "**组件**" 选项卡，然后选择 "**新建组件**"：

![使用树视图创建新的自定义组件](./media/create-component/insert-new-component-treeview.png)

选择 "**新建组件**" 会打开一个空画布。 您可以在画布上添加控件作为组件定义的一部分。 如果在画布中编辑组件，将更新其他应用程序屏幕中同一组件的实例。 在发布组件更改后，重用已创建组件的应用也可以接收组件更新。

选择屏幕后，可以从左侧导航的现有组件列表中选择一个组件。 选择组件时，会将该组件的实例插入到屏幕上;就像插入控件一样。

在树视图内的组件列表中的 "**自定义**类别" 下列出了应用内可用的组件。 导入组件库列在 "**库组件**" 类别下面：

![向应用程序插入组件](./media/create-component/insert-components.png)

> [!NOTE]
> 本文中所述的组件与 Power Apps 组件框架不同，后者使开发人员和开发人员能够为模型驱动的应用程序和画布应用程序创建代码组件。 有关详细信息，请参阅[Power Apps 组件框架概述](https://docs.microsoft.com/powerapps/developer/component-framework/overview)。

## <a name="scope"></a>范围

将组件视为封装的黑色框，其属性为接口。 不能从组件外部访问组件中的控件。 不能从组件内部引用组件以外的任何内容。 异常是指在应用程序及其组件之间共享的数据源。 范围限制会使组件的数据协定保持简单和内聚性，并帮助启用组件定义更新，尤其是跨组件库的应用程序。 可以通过创建一个或多个自定义属性来更新组件的数据协定。

> [!NOTE]
> 您可以将组件的实例插入到组件库中的屏幕上，并预览该屏幕以用于测试目的。 另请注意，当使用[Power Apps mobile](https://powerapps.microsoft.com/downloads/)时，组件库不会显示。

## <a name="custom-properties"></a>自定义属性

如果创建一个或多个自定义属性，组件可以接收输入值和发出数据。 这些方案是高级的，需要你了解[公式](formula-reference.md)和绑定协定。

**输入属性**是组件接收要在组件中使用的数据的方式。 如果选择了组件的实例，则输入属性会显示在右侧窗格的 "**属性**" 选项卡中。 可以通过表达式或公式来配置输入属性，就像在其他控件中配置标准属性一样。 其他控件具有输入属性，如**文本输入**控件的**默认**属性。

**Output 属性**用于发出数据或组件状态。 例如，**库**控件上的**所选**属性是 output 属性。 创建输出属性时，可以确定其他控件可以引用组件状态。

以下演练进一步介绍了这些概念。

## <a name="create-an-example-component"></a>创建示例组件

在此示例中，你将创建一个类似于下图的菜单组件。 稍后，你可以更改文本以在多个屏幕和/或应用程序中使用它：

![最终库](./media/create-component/menu-instance-new.png)

> [!NOTE]
> 建议在创建组件时使用[组件库](component-library.md)以供重用。 更新应用内的组件只会使组件更新在应用内可用。 将组件从一个应用导入到另一个应用时，原始应用中的组件的新更新将不会传播到前面导入这些组件的应用。 使用组件库时，如果更新并发布了库内的组件，系统将提示您更新组件。

### <a name="create-a-new-component"></a>创建新组件

1. 登录到[make.powerapps.com](https://make.powerapps.com)。

1. 选择 "**应用**"，并**从空白选择画布应用**。 

1. 提供应用名称，选择 "任何布局"，然后选择 "**创建**"。

1. 在**树视图**中，选择 "**组件**"，然后选择 "**新建组件**" 以创建新组件。

    ![使用树视图创建新的自定义组件](./media/create-component/insert-new-component-treeview.png)

1. 选择左侧导航窗格中的新组件，然后选择省略号（...），然后选择 "**重命名**"。 键入或粘贴 " **MenuComponent**" 名称。

1. 在右侧窗格中，将组件的宽度设置为**150** ，将其高度设置为**250**，然后选择 "**新建自定义属性**"。 还可以根据需要将 height & width 设置为任何其他值。

    ![新属性](./media/create-component/new-property.png)

1. 在 "**显示名称**"、"**属性名称**" 和 "**说明**" 框中，键入或粘贴文本作为*项*。

    ![显示名称、属性名称、说明框](./media/create-component/property-names.png)

    不要在属性名称中包含空格，因为当你编写公式时，将按此名称引用该组件。 例如， **ComponentName**。

    如果选择组件，显示名称将显示在右侧窗格的 "**属性**" 选项卡上。 描述性显示名称可帮助您和其他制造商了解此属性的用途。 如果将鼠标悬停在 "**属性**" 选项卡上此属性的显示名称上，则**说明**将显示在工具提示中。

1. 在 "**数据类型**" 列表中，选择 "**表**"，然后选择 "**创建**"。

    ![属性的数据类型](./media/create-component/property-data-type.png)

    **Items**属性设置为基于您指定的数据类型的默认值。 您可以将其设置为满足您的需要的值。 如果指定了**表**或**记录**的数据类型，则可能需要更改**Items**属性的值，使其与要输入到组件中的数据架构匹配。 在这种情况下，您需要将其更改为字符串列表。

    如果在右侧窗格的 "**属性**" 选项卡上选择属性的名称，则可以在编辑栏中设置该属性的值。

    !["属性" 选项卡上的自定义输入属性](./media/create-component/properties-tab.png)

    如下图所示，您还可以在右侧窗格的 "**高级**" 选项卡上编辑属性的值。

1. 将组件的**Items**属性设置为以下公式：

    ```powerapps-dot
    Table({Item:"SampleText"})
    ```

    ![公式](./media/create-component/set-component-items.png)

1. 在该组件中，插入一个空白垂直**库**控件，并在 "属性" 窗格上选择 "**布局**" 作为**标题**。

1. 请确保属性列表显示**Items**属性（默认情况下）。 然后，将该属性的值设置为此表达式：

    ```powerapps-dot
    MenuComponent.Items
    ```

    这样一来，**库**控件的**items**属性将读取并依赖于组件的**items** input 属性。

1. 可选-将**库**控件的**BorderThickness**属性设置为**1** ，将其**TemplateSize**属性设置为**50**。 你还可以根据需要将 "边框粗细" 和 "模板大小" 的值更新为任何其他值。

### <a name="add-component-to-a-screen"></a>将组件添加到屏幕

接下来，将该组件添加到屏幕，并为要显示的组件指定一个字符串表。

1. 在左侧导航栏中，选择屏幕列表，然后选择 "默认屏幕"。

    ![默认屏幕](./media/create-component/default-screen.png)

1. 在 "**插入**" 选项卡上，打开 "**组件**" 菜单，然后选择 " **MenuComponent**"。

    ![插入](./media/create-component/insert.png)

    默认情况下，新组件名为**MenuComponent_1** 。

1. 将**MenuComponent_1**的**Items**属性设置为以下公式：

    ```powerapps-dot
    Table({Item:"Home"}, {Item:"Admin"}, {Item:"About"}, {Item:"Help"})
    ```

    此实例与此图形类似，但您可以自定义每个实例的文本和其他属性。

    ![最终库](./media/create-component/menu-instance-new.png)

### <a name="create-and-use-output-property"></a>创建和使用 output 属性

到目前为止，您已经创建了一个组件，并将其添加到了应用程序中。 接下来，您将创建一个输出属性，该属性反映用户在菜单中选择的项。

1. 打开组件列表，然后选择 " **MenuComponent**"。

1. 在右侧窗格中，选择 "**属性**" 选项卡，然后选择 "**新建自定义属性**"。

1. 在 "**显示名称**"、"**属性名称**" 和 "**说明**" 框中，键入或粘贴**所选**的。

1. 在 "**属性类型**" 下，选择 "**输出**"，然后选择 "**创建**"。

    ![作为输出的属性类型](./media/create-component/output-property-type.png)

1. 在 "**高级**" 选项卡上，将**所选**属性的值设置为此表达式，并在必要时调整库名称中的数字：

    ```powerapps-dot
    Gallery1.Selected.Item
    ```

    ![高级窗格](./media/create-component/advance.png)

1. 在应用程序的默认屏幕上，添加一个标签，并将其**Text**属性设置为此表达式，并在必要时调整组件名称中的数字：

    ```powerapps-dot
    MenuComponent_1.Selected
    ```

    **MenuComponent_1**是实例的默认名称，而不是组件定义的名称。 您可以重命名任何实例。

1. 按住 Alt 键的同时，选择菜单中的每一项。

    "**标签**" 控件反映最近选择的菜单项。

## <a name="import-and-export-components"></a>导入和导出组件

> [!NOTE]
> 此功能将被弃用。 建议使用[组件库](component-library.md)在应用中重复使用组件。 使用组件库时，应用程序会在其所使用的组件上维护依赖关系。 相关组件的更新可用时，将向应用创建者发出警报。 因此，应改为在组件库中创建所有新的可重用组件。

### <a name="import-components-from-another-app"></a>从另一个应用导入组件

若要将一个或多个组件从一个应用导入到另一个应用，请选择 "从**插入**菜单**导入组件**"，然后使用 "**自定义**" 下拉。 或使用左侧导航窗格中的 "**组件**"。

对话框会列出所有包含您有权编辑的组件的应用程序。 选择应用，然后选择 "**导**入" 以导入该应用中所有组件的最新发布版本。 导入至少一个组件后，可以编辑副本并删除不需要的任何组件。

!["导入组件" 对话框](./media/create-component/import-component-screen.png)

你可以将具有现有组件的应用保存到本地文件，然后导入该文件以重用它。 您可以使用该文件将组件导入到其他应用程序。

如果应用包含同一组件的修改版本，系统将提示您确定是替换修改后的版本还是取消导入。 

在应用程序中创建组件后，其他应用程序可以通过导入该应用程序中的组件来使用这些组件。

### <a name="export-components-from-your-app"></a>从应用导出组件

可以将组件导出到文件中，并下载这些组件以便导入到另一个应用。

从左侧导航树视图的 "**组件**" 部分中选择 "**导出组件**" 选项：

![导出组件 treeview](./media/create-component/export-components-treeview.png)

你还可以使用 "**插入**" 菜单，然后选择 "**自定义**下拉"。

![导出组件插入菜单](./media/create-component/export-components-insert-menu.png)

选择 "**导出组件**" 会将组件下载到文件：

![下载组件](./media/create-component/download-component.png)

下载的组件文件使用*project-requests-app.msapp*文件扩展名。 

### <a name="import-components-from-exported-components-file"></a>从导出的组件文件导入组件

若要从导出的组件文件中导入组件，请从 "**插入**" 菜单中选择 "**导入组件**"。 然后使用 "**自定义**" 下拉框，或使用左侧导航窗格中的 "**组件**"。 从 "组件" 对话框中，选择 "**导入文件**"，而不是选择任何其他组件或应用：

![导入组件文件](./media/create-component/import-component-file.png)

从 "**打开**" 对话框中，浏览到组件文件的位置，然后选择 "**打开**" 以在应用内导入组件。

### <a name="import-components-from-exported-app"></a>从导出的应用导入组件

你可以使用**文件** -> **另存为**选项本地保存应用：

![保存应用](./media/create-component/save-app-locally.png)

保存应用后，可以使用与从文件导入组件相同的方法重用此应用的组件。 请按照上面的从导出组件文件中导入组件部分中所述的步骤进行操作。

## <a name="known-limitations"></a>已知限制

- 不能将数据源、窗体和数据表与组件一起保存。
- 组件中的集合不受支持。
- 不能将组件插入库或窗体中。
- 组件的主实例为本地主机，作用域为应用。 如果更改主实例，则仅应用程序内的组件副本将反映此更改。 除非再次导入组件库，否则其他应用中的副本将保持不变。 这些应用中的所有主实例将自动检测并更新。
- 导入组件时，不能打包媒体文件。
- 组件不支持[**UpdateContext**](./functions/function-updatecontext.md)函数，但你可以通过使用[**Set**](functions/function-set.md)函数在组件中创建和更新变量。 这些变量的作用域仅限于组件，但你可以通过自定义输出属性从组件外部访问这些变量。

## <a name="next-steps"></a>后续步骤

了解[组件库](component-library.md)以创建可重用组件的存储库。