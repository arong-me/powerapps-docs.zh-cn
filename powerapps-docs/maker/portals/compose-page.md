---
title: 撰写网页 |Microsoft Docs
description: 在门户中撰写网页的说明。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 0bedeae7952f5ec11394b680064af9016ae2b82e
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2019
ms.locfileid: "73542909"
---
# <a name="compose-a-page"></a>编纂网页

在站点地图中添加所需的网页并管理其层次结构后，可以添加各种组件。 WYSIWYG 编辑器允许您轻松地在画布上添加和编辑所需的组件。 你可以在画布上添加和编辑以下组件：

- 章节
    - 一个列部分
    - 两列部分
    - 三列部分
- 门户组件
    - Text
    - 图像
    - IFrame
    - 窗体
    - 成员列表
    - 导航

> [!NOTE]
> 如果使用 PowerApps portal Studio 自定义门户，则网站用户会注意到性能影响。 建议您在非高峰时段（在实时门户上）进行更改。 

## <a name="use-the-wysiwyg-editor"></a>使用 WYSIWYG 编辑器

1.  [编辑门户](manage-existing-portals.md#edit)以在 PowerApps portal Studio 中将其打开。  

2.  选择要将组件添加到的页面。

3.  选择画布上的可编辑元素。

    > [!NOTE]
    > 可编辑元素由边界 demarcated。

4.  从屏幕左侧的 toolbelt 中选择 "**组件**![组件" 图标](media/components-icon.png "组件图标")。  

5.  选择要添加的组件。

    > [!div class=mx-imgBorder]
    > ![组件窗格](media/components-pane.png "组件窗格")  

    选定的组件将添加到可编辑元素内的画布。

6.  若要删除某个组件，请在画布上选择该组件，然后在页面顶部的命令栏中选择 "**删除**"。

    > [!div class=mx-imgBorder]
    > ![删除组件](media/delete-component.png "删除组件")  

## <a name="add-sections"></a>添加节

使用节可以为页面定义结构并相应地排列门户组件。 将节添加到页面后，可以根据要求在各部分内添加门户组件。

1.  [编辑门户](manage-existing-portals.md#edit)以在 PowerApps portal Studio 中将其打开。

2.  选择要在其上添加节的页面。

3.  选择画布上的可编辑元素。

4.  从屏幕左侧的 toolbelt 中选择 "**组件**![组件" 图标](media/components-icon.png "组件图标")。

5.  在 "**部分布局**" 下，选择要插入的节类型。

6.  在屏幕右侧的 "属性" 窗格中，输入或选择以下信息：

    - **最小高度**：输入部分的最小高度。 如果添加的组件占用的空间超过指定的高度，则该部分将展开以容纳该组件。 默认情况下，最小高度为100px。 还可以按点（pt）和百分比（%）输入高度。

        > [!div class=mx-imgBorder]
        > ![部分中的对齐方式](media/section-props-height.png "部分中的对齐方式")  

    - **对齐方式**：选择部分中的组件是否必须是左对齐、居中或右对齐。

        > [!div class=mx-imgBorder]
        > ![部分中的对齐方式](media/section-props-align.png "部分中的对齐方式")  

    - **背景**：如果想要将颜色或图像作为部分背景，请选择此设置。

        - **填充**：选择背景的颜色。

            > [!div class=mx-imgBorder]
            > ![节中的填充颜色](media/section-props-fill.png "节中的填充颜色")  

        - **映像**：从列表中选择一个映像。 如果要上载新映像，请选择 "**上传映像**"。

            > [!div class=mx-imgBorder]
            > ![在部分中添加图像](media/section-props-image.png "在部分中添加图像")  

7.  在部分中添加所需的门户组件。


## <a name="add-portal-components"></a>添加门户组件

可以在网页上添加以下组件：

- [文本](#add-text-box)
- [图像](#add-image)
- [IFrame](#add-iframe)
- [窗体](#add-form)
- [成员列表](#add-list)
- [导航](#add-breadcrumb)


### <a name="add-text-box"></a>添加文本框

1.  [编辑门户](manage-existing-portals.md#edit)以在 PowerApps portal Studio 中将其打开。  

2.  选择要将组件添加到的页面。

3.  选择画布上的可编辑元素。

4.  从屏幕左侧的 toolbelt 中选择 "**组件**![组件" 图标](media/components-icon.png "组件图标")。  

5.  在 "**门户组件**" 下，选择 "**文本**"。

6.  在文本框中输入所需的文本。

7.  若要设置文本格式，请选择文本以显示格式选项。 根据需要修改字号和样式。

    > [!div class=mx-imgBorder]
    > ![文本组件](media/text-component.png "文本组件")  

8. 在屏幕右侧的 "属性" 窗格中，选择以下信息：

    - **对齐方式**：选择文本是必须左对齐、居中还是右对齐。

    - **字体颜色**：选择文本的颜色。

        > [!div class=mx-imgBorder]
        > ![选择文本对齐方式和颜色](media/text-props.png "选择文本对齐方式和颜色")  
 

### <a name="add-image"></a>添加映像

1.  [编辑门户](manage-existing-portals.md#edit)以在 PowerApps portal Studio 中将其打开。  

2.  选择要将组件添加到的页面。

3.  选择画布上的可编辑元素。

4.  从屏幕左侧的 toolbelt 中选择 "**组件**![组件" 图标](media/components-icon.png "组件图标")。  

5.  在 "**门户组件**" 下，选择 "**映像**"。 图像占位符将添加到画布中。

6.  在屏幕右侧的 "属性" 窗格中，输入以下信息：

    - **映像**：如果想要选择现有映像或上传新映像，请选择此选项。 如果要选择以前上传的映像，请从 "**选择映像**" 列表中选择一个映像。 若要上传新映像，请选择 "**上传映像**"。 所有上传的映像都包含在图像库中，可以通过 "**选择图像**" 列表再次选择该图像。

        > [!div class=mx-imgBorder]
        > ![图像属性](media/image-props.png "图像属性")  

        > [!NOTE]
        > - 只能上载类型为 png、svg、jpg 和 jpeg 的图像，其最大大小为 5 MB。
        > - 你无法上传具有相同名称的映像。 你需要修改该映像的名称以重新上传。

    - **外部 url**：如果想要从外部 url 上传图像，请选择此选项。 在 "**外部 url** " 字段中输入 url。 仅接受安全链接，即 https://是必需的。 如果你的图像存储在内容交付网络中，则可以在此字段中提供链接。

        > [!div class=mx-imgBorder]
        > ![图像外部 url](media/image-ext-url.png "图像外部 URL")  

    -   **格式设置选项**

        - **Width**：输入图像的宽度。

        - **高度**：输入图像的高度。

    > [!NOTE]
    > 还可以选择画布上的图像，并拖动控点以调整其大小。

### <a name="add-iframe"></a>添加 IFrame

1.  [编辑门户](manage-existing-portals.md#edit)以在 PowerApps portal Studio 中将其打开。  

2.  选择要将组件添加到的页面。

3.  选择画布上的可编辑元素。

4.  从屏幕左侧的 toolbelt 中选择 "**组件**![组件" 图标](media/components-icon.png "组件图标")。  

5.  在 "**门户组件**" 下，选择 " **IFrame**"。 IFrame 占位符将添加到画布中。

6.  在屏幕右侧的 "属性" 窗格中，输入以下信息：

    - **Width**：输入 IFrame 的宽度。

    - **Height**：输入 IFrame 的高度。

    - **链接**：输入要在 IFrame 中显示的网站的 URL。 仅接受安全链接，即 https://是必需的。 默认情况下，<https://www.bing.com> 可用作为值。

        > [!div class=mx-imgBorder]
        > ![iframe 属性](media/iframe-props.png "IFrame 属性")  

    > [!NOTE]
    > 还可以在画布上选择 IFrame，并拖动控点以调整其大小。

### <a name="add-form"></a>添加窗体

窗体是一种数据驱动的配置，用于在门户中添加用于收集数据的窗体，而无需开发人员在门户中显示窗体。 [表单是在 Common Data Service 中创建的](https://docs.microsoft.com/powerapps/maker/model-driven-apps/form-designer-overview)，你可以在门户中将其用于网页或结合列表来构建完整的 web 应用程序。  

1.  [编辑门户](manage-existing-portals.md#edit)以在 PowerApps portal Studio 中将其打开。  

2.  选择要将组件添加到的页面。

3.  选择画布上的可编辑元素。

4.  从屏幕左侧的 toolbelt 中选择 "**组件**![组件" 图标](media/components-icon.png "组件图标")。  

5.  在 "**门户组件**" 下选择 "**表单**"。

6.  在屏幕右侧的 "属性" 窗格中，选择下列选项之一：

    - **新建**：创建新窗体。
    - **使用现有**窗体：使用现有窗体。

7. 为以下内容输入信息或进行选择：

    - **Name**：格式的名称。

    - **实体**：要从中加载窗体的实体的名称。

    - **窗体布局**：目标实体中要呈现的 Common Data Service 中的窗体的名称。

    - **模式**：选择以下选项之一：

        - **Insert**：指示窗体应该在提交时插入新记录。

        - **编辑**：指示窗体应该编辑现有记录。

        - **只读**：指示窗体应显示现有记录的不可编辑窗体。

        > [!NOTE]
        > "**编辑**" 和 "**只读**" 模式的默认选项设置为 "URL 中作为 ID 传递的查询字符串参数名称"。 若要更改这些值，需要打开门户管理应用并更新窗体属性。

    - **成功时**：选择以下选项之一：

        - **显示成功消息**：要求在成功提交窗体时向用户显示一条消息。 你还可以选择 **"成功时隐藏窗体**" 以在成功提交时隐藏窗体。

        - **重定向到网页**：将用户重定向到门户中的所选网页。 必须从 "**重定向到网页**" 列表中选择一个网页。

        - **重定向到 URL**：将用户重定向到指定的 url。 必须在 "**重定向到 url** " 字段中输入 url。

    - **显示匿名用户的 captcha**：将 captcha 显示给匿名用户。

    - **为经过身份验证的用户显示 captcha**：向经过身份验证的用户显示 captcha。

    - **启用实体权限**：要为窗体考虑的实体权限。 默认情况下，不选择此选项。 如果选择此选项，则所有用户都必须具有显式权限才能访问窗体。 详细信息：[实体权限](configure/assign-entity-permissions.md)

        > [!div class=mx-imgBorder]
        > ![窗体属性](media/form-props.png "窗体属性")

### <a name="add-list"></a>添加列表

"列表" 是一种数据驱动的配置，用于添加一个网页，该网页将呈现一系列记录，而无需开发人员在门户中显示网格。 列表使用[Common Data Service 视图](https://docs.microsoft.com/powerapps/maker/model-driven-apps/create-and-edit-views)在门户上显示记录。  

1.  [编辑门户](manage-existing-portals.md#edit)以在 PowerApps portal Studio 中将其打开。  

2.  选择要将组件添加到的页面。

3.  选择画布上的可编辑元素。

4.  从屏幕左侧的 toolbelt 中选择 "**组件**![组件" 图标](media/components-icon.png "组件图标")。  

5.  在 "**门户组件**" 下，选择 "**列表**"。

6.  在屏幕右侧的 "属性" 窗格中，选择下列选项之一：

    - **新建**：创建新列表。
    - **使用现有**的：使用现有列表。

7.  为以下内容输入信息或进行选择：

    - **名称**：列表的名称。

    - **实体**：从中加载视图的实体的名称。

    - **视图**：要呈现的目标实体的视图列表。 您可以选择多个视图来显示列表中的记录。 首先选择的视图将是默认视图。

    - **创建新记录**：允许用户创建记录。 选择包含用于创建新记录的窗体的网页。

    - **查看详细信息**：允许用户查看详细信息。 选择包含窗体的网页以显示详细信息。

    - **编辑记录**：允许用户编辑记录。 选择包含用于编辑记录的窗体的网页。

    - **删除记录**：允许用户删除记录。

    - **空列表消息**：没有要显示的记录时要显示的消息。

    - **每页的记录数**：一个整数值，用于指定要在页面上显示的记录数。

    - **启用 "在实体列表中搜索"** ：允许用户搜索列表中的记录。

    - **启用实体权限**：要为列表考虑的实体权限。 默认情况下，不选择此选项。 如果选择此选项，则所有用户都必须具有显式权限才能访问窗体。 详细信息：[实体权限](configure/assign-entity-permissions.md)  

    > [!div class=mx-imgBorder]
    > ![列表属性](media/list-props.png "列表属性")

### <a name="add-breadcrumb"></a>添加痕迹

1.  [编辑门户](manage-existing-portals.md#edit)以在 PowerApps portal Studio 中将其打开。  

2.  选择要将组件添加到的页面。

3.  选择画布上的可编辑元素。

4.  从屏幕左侧的 toolbelt 中选择 "**组件**![组件" 图标](media/components-icon.png "组件图标")。  

5.  在 "**门户组件**" 下，选择 "**痕迹导航**"。

## <a name="add-a-custom-menu"></a>添加自定义菜单

默认情况下，将基于网页的层次结构自动创建网站上的菜单。 它被称为**默认**菜单。 若要创建自定义菜单，必须在门户网站管理应用中创建 web 链接集。 详细信息：[管理 web 链接](configure/manage-web-links.md)

创建 web 链接集后：

1.  [编辑门户](manage-existing-portals.md#edit)以在 PowerApps portal Studio 中将其打开。

2.  选择标题组件。 

3.  在屏幕右侧的 "属性" 中，从**导航菜单**列表中选择 "web 链接集名称"。

    > [!div class=mx-imgBorder]
    > ![导航菜单](media/navigation-menu.png "导航菜单")

## <a name="use-code-editor"></a>使用代码编辑器

若要在画布上查看组件的源，请选择该组件，然后选择 "源代码编辑器" 图标&lt;页脚中 **/&gt;** 。

> [!div class=mx-imgBorder]
> !["代码编辑器" 图标](media/code-editor-icon.png ""代码编辑器" 图标")  

源代码显示在屏幕底部的 "**代码编辑器**" 窗格中。 你之前所做的更改会在源代码中更新。 若要进行更改，请更新源代码，然后选择 "**保存**"。 更改将反映在画布上。

> [!div class=mx-imgBorder]
> ![代码编辑器](media/code-editor.png "代码编辑器") 

> [!NOTE]
> 你还可以在源代码编辑器中添加液体标记以进行高级配置。 详细信息：[使用液体模板](liquid/liquid-overview.md)


