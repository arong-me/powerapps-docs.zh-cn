---
title: 撰写网页 | Microsoft Docs
description: 在门户中撰写网页的说明。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: a6affbb0d13af137ddd044a7ae4b6d2cddbf813c
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/02/2019
ms.locfileid: "2862432"
---
# <a name="compose-a-page"></a>撰写页面

添加所需的网页并在站点地图中管理其层次结构后，您可以添加各种组件。 WYSIWYG 编辑器使您可以轻松地在区域上添加和编辑必需组件。 您可以在区域上添加和编辑以下组件：

- 部分
    - 一列式分区
    - 两列式分区
    - 三列式分区
- 门户组件
    - Text
    - 图像
    - IFrame
    - 表单
    - 列表
    - 痕迹导航

> [!NOTE]
> 如果使用 Power Apps 门户 Studio 自定义门户，则网站用户会注意到性能影响。 我们建议您在非高峰时间在活动门户上进行更改。 

## <a name="use-the-wysiwyg-editor"></a>使用 WYSIWYG 编辑器

1.  [编辑门户](manage-existing-portals.md#edit)以在 Power Apps 门户 Studio 中打开它。  

2.  选择要在其上添加组件的页面。

3.  选择区域上的可编辑元素。

    > [!NOTE]
    > 可编辑元素由边界加以区分。

4.  从屏幕左侧的工具栏中选择**组件** ![组件图标](media/components-icon.png "组件图标")。  

5.  选择要添加的组件。

    > [!div class=mx-imgBorder]
    > ![组件窗格](media/components-pane.png "组件窗格")  

    选定的组件将添加到可编辑元素内的区域中。

6.  要删除组件，请在区域上选择该组件，然后在页面顶部的命令栏上选择**删除**。

    > [!div class=mx-imgBorder]
    > ![删除组件](media/delete-component.png "删除组件")  

## <a name="add-sections"></a>添加分区

分区允许您定义页面的结构并相应地安排门户组件。 将分区添加到页面后，您可以根据需要在分区内添加门户组件。

1.  [编辑门户](manage-existing-portals.md#edit)以在 Power Apps 门户 Studio 中打开它。

2.  选择要在其中添加分区的页面。

3.  选择区域上的可编辑元素。

4.  从屏幕左侧的工具栏中选择**组件** ![组件图标](media/components-icon.png "组件图标")。

5.  在**分区布局**下，选择要插入的分区类型。

6.  在屏幕右侧的属性窗格中，输入或选择以下信息：

    - **最小高度**：输入分区的最小高度。 如果添加的组件所占空间大于指定高度，则该分区将扩展以容纳该组件。 默认情况下，最小高度为 100px。 您还可以输入以点 (pt) 和百分比 (%) 为单位的高度。

        > [!div class=mx-imgBorder]
        > ![部分内的对齐方式](media/section-props-height.png "部分内的对齐方式")  

    - **对齐方式**：选择分区中的组件必须左对齐、居中还是右对齐。

        > [!div class=mx-imgBorder]
        > ![部分内的对齐方式](media/section-props-align.png "部分内的对齐方式")  

    - **背景**：选择是否要使用颜色或图像作为分区背景。

        - **填充**：选择背景颜色。

            > [!div class=mx-imgBorder]
            > ![在部分中填充颜色](media/section-props-fill.png "在部分中填充颜色")  

        - **图像**：从列表中选择图像。 如果您要上载新图像，请选择**上载图像**。

            > [!div class=mx-imgBorder]
            > ![在部分中添加图像](media/section-props-image.png "在部分中添加图像")  

7.  在分区中添加必需的门户组件。


## <a name="add-portal-components"></a>添加门户组件

您可以在网页上添加以下组件：

- [文本](#add-text-box)
- [图像](#add-image)
- [IFrame](#add-iframe)
- [表单](#add-form)
- [列表](#add-list)
- [痕迹导航](#add-breadcrumb)


### <a name="add-text-box"></a>添加文本框

1.  [编辑门户](manage-existing-portals.md#edit)以在 Power Apps 门户 Studio 中打开它。  

2.  选择要在其上添加组件的页面。

3.  选择区域上的可编辑元素。

4.  从屏幕左侧的工具栏中选择**组件** ![组件图标](media/components-icon.png "组件图标")。  

5.  在**门户组件**下，选择**文本**。

6.  在文本框中输入所需文本。

7.  要设置文本格式，选择文本以显示格式选项。 根据需要修改字号和字体样式。

    > [!div class=mx-imgBorder]
    > ![文本组件](media/text-component.png "文本组件")  

8. 在屏幕右侧的属性窗格中，选择以下信息：

    - **对齐方式**：选择文本必须左对齐、居中还是右对齐。

    - **字体颜色**：选择文本的颜色。

        > [!div class=mx-imgBorder]
        > ![选择文本对齐方式和颜色](media/text-props.png "选择文本对齐方式和颜色")  
 

### <a name="add-image"></a>添加图像

1.  [编辑门户](manage-existing-portals.md#edit)以在 Power Apps 门户 Studio 中打开它。  

2.  选择要在其上添加组件的页面。

3.  选择区域上的可编辑元素。

4.  从屏幕左侧的工具栏中选择**组件** ![组件图标](media/components-icon.png "组件图标")。  

5.  在**门户组件**下，选择**图像**。 图像占位符被添加到区域中。

6.  在屏幕右侧的属性窗格中，输入以下信息：

    - **图像**：如果要选择现有图像或上载新图像，请选择此选项。 如果要选择以前上载的图像，请从**选择图像**列表中选择一个图像。 要上载新图像，请选择**上载图像**。 所有上载的图像都包含在图像库中，可以通过**选择图像**列表再次选择。

        > [!div class=mx-imgBorder]
        > ![图像属性](media/image-props.png "图像属性")  

        > [!NOTE]
        > - 只能上载 png、svg、jpg 和 jpeg 类型的图像，最大尺寸为 5 MB。
        > - 不能上载具有相同名称的图像。 您需要修改图像名称才能再次上载。

    - **外部 URL**：如果要从外部 URL 上载图像，请选择此选项。 在**外部 URL** 字段输入 URL。 仅接受安全链接—即 https:// 是强制的。 如果您的内容传送网络中存储有图像，则可以在此字段中提供链接。

        > [!div class=mx-imgBorder]
        > ![图像外部 URL](media/image-ext-url.png "图像外部 URL")  

    -   **格式选项**

        - **宽度**：输入图像的宽度。

        - **高度**：输入图像的高度。

    > [!NOTE]
    > 您还可以选择区域内的图像并拖动手柄来调整其大小。

### <a name="add-iframe"></a>添加 IFrame

1.  [编辑门户](manage-existing-portals.md#edit)以在 Power Apps 门户 Studio 中打开它。  

2.  选择要在其上添加组件的页面。

3.  选择区域上的可编辑元素。

4.  从屏幕左侧的工具栏中选择**组件** ![组件图标](media/components-icon.png "组件图标")。  

5.  在**门户组件**下，选择 **IFrame**。 IFrame 占位符被添加到区域中。

6.  在屏幕右侧的属性窗格中，输入以下信息：

    - **宽度**：输入 IFrame 的宽度。

    - **高度**：输入 IFrame 的高度。

    - **链接**：输入要在 IFrame 中显示的网站的 URL。 仅接受安全链接—即 https:// 是强制的。 默认情况下，<https://www.bing.com> 可以用作值。

        > [!div class=mx-imgBorder]
        > ![iFrame 属性](media/iframe-props.png "iFrame 属性")  

    > [!NOTE]
    > 您还可以选择区域内的 IFrame 并拖动手柄来调整其大小。

### <a name="add-form"></a>添加窗体

窗体是一项数据驱动配置，您可以用它来添加窗体以在门户中收集数据，而无需开发人员在门户中呈现窗体。 [窗体在 Common Data Service 中创建](https://docs.microsoft.com/powerapps/maker/model-driven-apps/form-designer-overview)，您可以在门户的网页中使用它们，或将它们与列表共同用于构建完整的 Web 应用程序。  

1.  [编辑门户](manage-existing-portals.md#edit)以在 Power Apps 门户 Studio 中打开它。  

2.  选择要在其上添加组件的页面。

3.  选择区域上的可编辑元素。

4.  从屏幕左侧的工具栏中选择**组件** ![组件图标](media/components-icon.png "组件图标")。  

5.  在**门户组件**下，选择**窗体**。

6.  在屏幕右侧的属性窗格中，选择以下选项之一：

    - **新建**：新建窗体。
    - **使用现有**：使用现有窗体。

7. 为以下各项输入信息或进行选择：

    - **名称**：窗体的名称。

    - **实体**：窗体将从中加载的实体的名称。

    - **窗体布局**：要呈现的 Common Data Service 中目标实体中的窗体的名称。

    - **模式**：选择以下选项之一：

        - **插入**：指示窗体应在提交后插入新记录。

        - **编辑**：指示窗体应编辑记录。

        - **只读**：指示窗体应显示现有记录的不可编辑窗体。

        > [!NOTE]
        > **编辑**和**只读**模式的默认选项设置为查询字符串参数名称，作为 URL 中的 ID 传递。 要更改这些值，您需要打开门户管理应用并更新窗体属性。

    - **成功时**：选择以下选项之一：

        - **显示成功消息**：要求在成功提交窗体后向用户显示一条消息。 您还可以选择**成功时隐藏窗体**以在成功提交后隐藏窗体。

        - **重定向到网页**：将用户重定向到门户中的所选网页。 您必须从**重定向到网页**列表中选择一个网页。

        - **重定向到 URL**：将用户重定向到指定的 URL。 您必须在**重定向到 URL** 字段中输入一个 URL。

    - **对匿名用户显示 captcha**：向匿名用户显示 captcha。

    - **对已通过身份验证的用户显示 captcha**：向已通过身份验证的用户显示 captcha。

    - **启用实体权限**：要为窗体考虑的实体权限。 默认情况下不选择。 如果选择，访问窗体的所有用户都需要具有显式权限。 详细信息：[实体权限](configure/assign-entity-permissions.md)

        > [!div class=mx-imgBorder]
        > ![窗体属性](media/form-props.png "窗体属性")

### <a name="add-list"></a>添加列表

列表是数据驱动型配置，用于添加呈现记录列表的网页，而无需开发人员在门户中显示网格。 列表使用 [Common Data Service 视图](https://docs.microsoft.com/powerapps/maker/model-driven-apps/create-and-edit-views)在门户上显示记录。  

1.  [编辑门户](manage-existing-portals.md#edit)以在 Power Apps 门户 Studio 中打开它。  

2.  选择要在其上添加组件的页面。

3.  选择区域上的可编辑元素。

4.  从屏幕左侧的工具栏中选择**组件** ![组件图标](media/components-icon.png "组件图标")。  

5.  在**门户组件**下，选择**列表**。

6.  在屏幕右侧的属性窗格中，选择以下选项之一：

    - **新建**：新建列表。
    - **使用现有**：使用现有列表。

7.  为以下各项输入信息或进行选择：

    - **名称**：列表的名称。

    - **实体**：视图将从中加载的实体的名称。

    - **视图**：要呈现的目标实体的视图的列表。 您可以选择多个视图以在列表中显示记录。 第一个选择的视图将是默认视图。

    - **创建新记录**：使用户能够创建记录。 选择一个包含窗体的网页以创建新记录。

    - **查看详细信息**：允许用户查看详细信息。 选择一个包含窗体的网页以显示详细信息。

    - **编辑记录**：使用户能够编辑记录。 选择一个包含窗体的网页以编辑记录。

    - **删除记录**：使用户能够删除记录。

    - **空列表消息**：没有记录可显示时显示的消息。

    - **每页记录数**：一个整数值，用于指定要在页面上显示的记录数。

    - **启用在实体列表中搜索**：允许用户搜索列表中的记录。

    - **启用实体权限**：要为列表考虑的实体权限。 默认情况下不选择。 如果选择，访问窗体的所有用户都需要具有显式权限。 详细信息：[实体权限](configure/assign-entity-permissions.md)  

    > [!div class=mx-imgBorder]
    > ![列表属性](media/list-props.png "列表属性")

### <a name="add-breadcrumb"></a>添加痕迹导航

1.  [编辑门户](manage-existing-portals.md#edit)以在 Power Apps 门户 Studio 中打开它。  

2.  选择要在其上添加组件的页面。

3.  选择区域上的可编辑元素。

4.  从屏幕左侧的工具栏中选择**组件** ![组件图标](media/components-icon.png "组件图标")。  

5.  在**门户组件**下，选择**痕迹导航**。

## <a name="add-a-custom-menu"></a>添加自定义菜单

默认情况下，网站上的菜单是根据网页的层次结构自动创建的。 称为**默认**菜单。 要创建自定义菜单，必须在“门户管理”应用中创建 Web 链接集。 详细信息：[管理 Web 链接](configure/manage-web-links.md)

创建 Web 链接集后：

1.  [编辑门户](manage-existing-portals.md#edit)以在 Power Apps 门户 Studio 中打开它。

2.  选择页眉组件。 

3.  在屏幕右侧的属性中，从**导航菜单**列表中选择 Web 链接集名称。

    > [!div class=mx-imgBorder]
    > ![导航菜单](media/navigation-menu.png "导航菜单")

## <a name="use-code-editor"></a>使用代码编辑器

若要查看区域上组件的源，选择该组件，然后选择页脚内的源代码编辑器图标 **&lt;/&gt;**。

> [!div class=mx-imgBorder]
> ![代码编辑器图标](media/code-editor-icon.png "代码编辑器图标")  

源代码在屏幕底部的**代码编辑器**窗格中显示。 您之前所做的更改将在源代码中更新。 要进行更改，请更新源代码并选择**保存**。 所做的更改将反映在区域上。

> [!div class=mx-imgBorder]
> ![代码编辑器](media/code-editor.png "代码编辑器") 

> [!NOTE]
> 您还可以在源代码编辑器中添加 Liquid 标记以进行高级配置。 详细信息：[使用 Liquid 模板](liquid/liquid-overview.md)


