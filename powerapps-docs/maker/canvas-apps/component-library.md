---
title: 创建用于画布应用的组件库 |Microsoft Docs
description: 画布应用的可重用组件库
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
ms.openlocfilehash: ae1b1b7bc7657d513921ddc2513696af9a808299
ms.sourcegitcommit: efb05dbd29c4e4fb31ade1fae340260aeba2e02b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2020
ms.locfileid: "78293123"
---
# <a name="component-library"></a>组件库

> [!IMPORTANT]
> 此功能仍处于公共预览版中。 有关详细信息，请参阅[实验性功能和预览功能](working-with-experimental.md)。

在创建组件的[概述](create-component.md)文章中，会引入 canvas 应用内的组件。 在应用内创建组件时，还可以创建可重用的组件库。 通过创建组件库，应用程序制造商可以轻松地与其他制造商共享和更新一个或多个组件。

组件库是组件定义的容器，便于：

- 发现和搜索组件。
- 跨环境发布更新。
- 通知应用程序提供程序的可用组件更新。 

> [!NOTE]
> 建议使用组件库来跨应用重用组件。 使用组件库时，应用程序会在其所使用的组件上维护依赖关系。 相关组件的更新可用时，将向应用创建者发出警报。 因此，应改为在组件库中创建所有新的可重用组件。 允许将[组件从一个画布应用导入到另一个画布应用](create-component.md?#import-and-export-components)的早期 Power Apps 功能将被弃用。

## <a name="difference-between-an-app-and-a-component-library"></a>应用程序与组件库之间的差异

组件库提供了一个集中式的托管组件存储库，可重用性。 

左侧导航中的 "**插入**" 窗格默认为 "组件" 选项卡（如果创建组件库）。 创建应用时，此视图将显示屏幕而不是组件。 

组件库中的屏幕仅可用于测试。 它为库创建者提供了一种方法，用于快速测试实际屏幕上创建的组件，还可验证更新行为，因为随着时间的推移，组件已增强。 要使用组件库中的组件，你必须创建使用组件库的应用。

可以使用 "播放" 选项在库中预览组件库组件。 选择 "组件" 选项卡时，"播放" 选项处于禁用状态。 使用 Power Apps mobile 时，组件库未显示。

> [!NOTE]
> 本文中讨论的组件库不同于使开发人员和开发人员能够为模型驱动的应用程序和画布应用程序创建代码组件的 Power Apps 组件框架。 有关详细信息，请参阅[Power Apps 组件框架概述](https://docs.microsoft.com/powerapps/developer/component-framework/overview)。

## <a name="working-with-component-library"></a>使用组件库

你可以创建新的组件库或从同一界面编辑现有的组件库。 浏览到[make.powerapps.com](https://make.powerapps.com)，选择 "**应用**"，然后选择 "**组件库**"：

![创建或编辑组件库](./media/component-library/create-edit-component-library.png)

## <a name="create-an-example-component-library"></a>创建示例组件库

在组件库中创建组件的步骤与在应用内创建组件相同。 你将创建组件库。 然后重新使用通过组件创建组件[概述示例](create-component.md#create-an-example-component)中的步骤。 然后，你将使用组件库在新应用程序中提供可重用的组件。

1. 登录到[make.powerapps.com](https://make.powerapps.com)。

1. 选择左侧导航栏中的 "**应用**"，选择 "**组件库**"，然后选择 "**新建组件库**"。

1. 将组件库命名为*菜单组件*;你还可以为你的选择提供不同的名称。

1. 按照以下步骤从组件创建组件[概述示例](create-component.md#create-an-example-component)。 由于你已经创建了一个新的组件库，因此无需打开 Power Apps Studio 或创建新的空白应用。 从步骤2开始。 

    执行以下步骤以创建组件后，请按照下一组步骤，[将组件添加到屏幕](create-component.md#add-component-to-a-screen)，以[创建输出属性](create-component.md#create-and-use-output-property)的步骤。 

1. 完成组件的创建和测试后，通过选择 "**文件**" 菜单，然后选择 "**保存**" 来保存组件库。 

    你还可以选择保存**版本说明**。 版本说明可用于检索组件库的版本。 从此组件库升级应用中使用的组件时。

    ![保存组件库时的版本说明](./media/component-library/save-component-libray-version-note.png)

    > [!TIP]
    > 查看组件库的版本时，版本说明非常有用，并且对于使用组件库的应用制造商而言，查看更改并根据需要更新使用这些组件的应用。 有关更多详细信息，请阅读[更新组件库](component-library.md?#update-a-component-library)。   

1. 保存的组件库可以发布。 仅发布的组件库更新可用于使用组件库的应用。 选择 "**发布**" 以发布组件库版本：

    ![发布组件库版本](./media/component-library/publish-component-library.png)

## <a name="import-from-a-component-library"></a>从组件库导入

创建组件库并进行发布后，应用可通过导入库来使用此组件库中的组件。 你还可以[共享组件库](component-library.md#component-library-permissions)。

若要从组件库导入，请编辑现有应用或创建新的应用。 在画布 app studio 中打开应用后，在左侧导航栏中选择 "**插入**" 或 " **+** "。 然后选择 "**获取更多组件**" 列出当前环境中可用的组件库：

![获取更多组件](./media/component-library/get-more-components.png)

你将看到在屏幕右侧的当前环境中可用的组件库的列表。 从组件库中选择单个组件。 也可以使用 "**全选**" 一次性导入库中的所有组件：

![导入组件](./media/component-library/components.png)

> [!NOTE]
> 如果 "maker" 未显示 "导入" 部分中列出的组件库，请确保组件库与 maker 共享。 有关更多详细信息，请参阅[组件库权限](component-library.md#component-library-permissions)。 

请注意，你可以选择并导入多个组件，并将其导入到不同的组件库。 

应用中可用的组件在 "**插入**" 窗格的 "组件列表" 中的 "**自定义**类别" 下列出。 导入组件库中的可用组件列在 "**库组件**" 类别下面：

![向应用程序插入组件](./media/component-library/insert-components.png)

## <a name="update-a-component-library"></a>更新组件库

您可以修改现有的组件库，并保存包含其他版本说明的任何更改。 但是，必须发布更新的组件库版本，才能在使用组件库的现有应用中使用。 上述[示例组件库](component-library.md#create-an-example-component-library)步骤说明了如何在保存后发布组件库。

其他应用的制造商会收到有关可用更新组件的通知。 当决策者在 canvas app studio 中编辑应用时，将显示通知。 并且可以选择更新组件：

![可用更新](./media/component-library/update-available.png)

选择 "**查看**"，您将看到更新组件的选项：

![更新组件](./media/component-library/update-components.png)

请注意在发布组件库版本时添加的版本说明。 

选择 "**更新**" 以更新组件。

## <a name="component-library-permissions"></a>组件库权限

共享组件库的工作方式与共享画布应用的方式相同。 共享组件库时，允许其他人重复使用组件库。 共享后，其他人可以编辑组件库，并从此共享组件库导入组件，以便创建和编辑应用。 如果共享为共同所有者，用户可以使用、编辑、共享组件库，但不能删除或更改所有者。

## <a name="known-limitations"></a>已知限制

- 适用于组件的[已知限制](create-component.md#known-limitations)还适用于组件库。
- 不能使用组件库从本地保存的组件库文件中导入组件。 如果尝试使用**文件** -> **另存为** -> **此计算机**并将组件库文件下载为应用来导入本地保存的组件库，将显示以下错误消息： 

    ![导入组件库文件](./media/component-library/import-component-library-file.png)

- 不能将现有的组件库添加到[解决方案](add-app-solution.md)中。 但是，可以使用 "添加组件库流" 为解决方案创建新的组件库。

- 如果从组件库中导入组件，则不能在使用的应用程序中对其进行编辑。 如果选择 "**编辑组件**"，则会看到一个选项，可用于在当前应用中创建组件的副本以进行更改： 

    ![编辑库组件](./media/component-library/edit-library-component.png)

    如果选择 "**创建副本**"，则会将组件复制到本地应用。 组件的本地副本显示在 "**插入**" 窗格中的 "**自定义**" 类别下。 如果以后发布了新版本的原始组件库，此组件的本地副本将不会收到更新。
    
- 将组件添加到组件库中的应用程序并更新应用程序的主题后，该组件将成为本地应用程序组件，并且不再与组件库中的主组件相关联。

## <a name="next-steps"></a>后续步骤

了解 canvas 应用的[行为公式](component-behavior.md)。

### <a name="see-also"></a>另请参阅

阅读画布应用[组件概述](create-component.md)和使用应用中的组件。
