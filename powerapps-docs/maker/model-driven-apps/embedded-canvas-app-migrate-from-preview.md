---
title: 迁移使用公共预览版本创建的模型驱动窗体上的嵌入式区域应用 | MicrosoftDocs
ms.custom: ''
ms.date: 06/25/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - PowerApps
author: Aneesmsft
ms.author: matp
manager: kvivek
tags:
  - PowerApps maker portal impact
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="migrate-embedded-canvas-apps-on-model-driven-forms-created-using-the-public-preview-release"></a>迁移使用公共预览版本创建的模型驱动窗体上的嵌入式区域应用
> [!IMPORTANT]
> 通过最新版本，模型驱动窗体上的嵌入式区域应用已公开发布。 使用公共预览版本创建的模型驱动窗体上的任何嵌入式区域应用均应迁移到使用最新版本创建的新嵌入式区域应用。
> 对使用公共预览版本创建的模型驱动窗体上的嵌入式区域应用的支持很快将弃用。 

若要迁移使用最新的公共预览版本创建的模型驱动窗体上的嵌入式区域应用，开发者首先需要使用最新版本创建新的嵌入式区域应用。 然后，开发者可以将控件从现有的嵌入式区域应用复制到新应用，添加所需的数据源，并更新被破坏的引用（如果有）。 下面提供了详细步骤。

1. 登录到 [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)。
2. 打开使用公共预览版本创建的嵌入式区域应用以在 PowerApps Studio 中进行编辑。 有关编辑区域应用的步骤，请参阅：[编辑区域应用](../canvas-apps/edit-app.md)。
3. 在新浏览器标签页中，按照步骤[在模型驱动窗体上添加新的嵌入式区域应用](embedded-canvas-app-add-classic-designer.md)。
4. 使用下方步骤，将控件从使用公共预览版本创建的嵌入式区域应用复制到新的嵌入式区域应用，一次一个屏幕。
    1. 选择步骤 2 中的浏览器标签页，其包含使用公共预览版本创建的嵌入式区域应用，该应用在 PowerApps Studio 中打开。
    2. 选择从其复制控件的屏幕。
    3. 使用 **Ctrl + A** 选择屏幕上的所有控件。
    4. 使用 **Ctrl + C** 复制所有选定控件。
    5. 选择步骤 3 中的浏览器标签页，其包含使用最新版本创建的新嵌入式区域应用。
    6. 选择屏幕或添加新屏幕。
    7. 使用 **Ctrl + V** 在所选屏幕上粘贴控件。
    8. 重复步骤复制每个屏幕。
5. 复制完所有屏幕后，选择步骤 3 中的浏览器标签页，其包含使用最新版本创建的新嵌入式区域应用。
6. 更新在其中访问主机模型驱动窗体中的记录的所有位置。 将 **First(ModelDrivenFormIntegration.Data)** 替换为 **ModelDrivenFormIntegration.Item**。
7. 在新的嵌入式区域应用中添加任何缺少的数据源。
8. 在新的嵌入式区域应用中更新所有被破坏的引用。 
9. 在完成更改时，选择**文件**选项卡，然后选择**保存**。
10. 若要让您的更改对最终用户可用，选择**发布**，然后选择**发布此版本**。

## <a name="migrating-embedded-canvas-apps-on-model-driven-forms-that-use-a-list-of-records-related-to-the-current-main-form-record"></a>迁移使用与当前（主窗体）记录相关的记录列表的模型驱动窗体上的嵌入式区域应用

在预览版本中，要在模型驱动窗体上嵌入区域应用，开发者必须预先决定是否需要作为数据上下文传递当前（主窗体）记录或与当前（主窗体）记录相关的记录列表。 然后，他们必须将区域应用控件添加到字段或子网格控件。

在最新版本中，在模型驱动窗体上添加嵌入式区域应用得到简化，仅简化为字段。 开发者仍然可以使用 Common Data Service 连接器在区域应用中直接访问相关记录的列表。 

要迁移使用与当前（主窗体）记录相关的记录列表的模型驱动窗体上的嵌入式区域应用，请按照正面的步骤操作。

1. 请按照上述部分中的步骤迁移使用最新公共预览版本创建的模型驱动窗体上的嵌入式区域应用。
2. 使用 Common Data Service 连接器，将相关实体的数据源添加到应用。 要了解如何在区域应用中添加数据源，请参阅[在 PowerApps 中向区域应用添加数据连接](../canvas-apps/add-data-connection.md)。
3. 在使用控件（如[库](../canvas-apps/controls/control-gallery.md)或[数据表](../canvas-apps/controls/control-data-table.md)）的相关实体的数据源时，请使用**[筛选器](../canvas-apps/functions/function-filter-lookup.md)** 功能将记录筛选为与当前（主窗体）记录相关的记录。 当前（主窗体）记录通过 **ModelDrivenFormIntegration.Item** 提供。
    > [!NOTE]
    > 嵌入式区域应用具有通过 ModelDrivenFormIntegration.Item 访问主机模型驱动窗体中的记录的完全访问权限。 举例来说，要获取名称为 **accountnumber** 且显示名称为 **Account Number** 的字段的值，您可以使用 **ModelDrivenFormIntegration.Item.accountnumber** 或 **ModelDrivenFormIntegration.Item.'Account Number'**。
4. 通过最近的更新，Common Data Service 现在还提供将实体视图用作筛选器的支持。 请参阅此博客文章了解详细信息：[改进的数据源选择和 Common Data Service 视图](https://powerapps.microsoft.com/blog/improved-data-source-selection-and-common-data-service-views/)。 

## <a name="see-also"></a>另请参阅
[在模型驱动的窗体上嵌入区域应用](embed-canvas-app-in-form.md) <br />
[在模型驱动窗体上添加嵌入式区域应用](embedded-canvas-app-add-classic-designer.md) <br />
[编辑在模型驱动窗体上嵌入的区域应用](embedded-canvas-app-edit-classic-designer.md) <br />
[自定义在模型驱动窗体上嵌入的区域应用的屏幕尺寸和方向](embedded-canvas-app-customize-screen.md) <br />
[从嵌入的区域应用内在主机窗体上执行预定义操作](embedded-canvas-app-actions.md) <br />
[ModelDrivenFormIntegration 控件的属性和操作](embedded-canvas-app-properties-actions.md) <br />
[共享嵌入式区域应用](share-embedded-canvas-app.md) <br />
[嵌入式区域应用使用指南](embedded-canvas-app-guidelines.md) <br />
