---
title: 创建和管理网页 | Microsoft Docs
description: 有关如何在门户中创建和管理网页的说明。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: null
ms.date: 09/16/2019
ms.author: shjais
ms.reviewer: null
---

# <a name="create-and-manage-webpages"></a>创建和管理网页

[!include[cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

网页是由网站中的唯一 URL 标识的文档。 它是网站的核心对象之一，通过与其他网页的父子关系建立网站的层次结构。

> [!NOTE]
> 如果使用门户设计器自定义门户，则网站用户会注意到性能影响。 我们建议您在非高峰时间在活动门户上进行更改。

## <a name="create-webpage"></a>新建网页

1.  [编辑门户](manage-existing-portals.md#edit)以在门户设计器中将其打开。  

2.  在命令栏中，选择**新建页面**，然后选择页面模板。

    > [!div class=mx-imgBorder]
    > ![创建新网页](media/create-webpage.png "创建新网页")

3.  在屏幕右侧的属性窗格中，输入以下信息：

    - **名称**：页面的名称。 此值也用作页面标题。

    - **部分 URL**：用于构建此页的门户 URL 的 URL 路径段。

    - **模板**：用于在门户中呈现此页面的页面模板。 如果需要，您可以从列表中选择另一个模板。

        > [!div class=mx-imgBorder]
        > ![网页属性](media/webpage-props.png "网页属性")

您创建的网页已添加，其层次结构显示在**页面**窗格中。 要查看**页面**窗格，请从屏幕左侧的工具栏中选择**页面** ![页面图标](media/pages-icon.png "页面图标")。  

假设您已经为门户创建了一些网页。 页面层次结构如下所示：

> [!div class=mx-imgBorder]
> ![页面窗格](media/pages-pane.png "页面窗格")  

网站上的主要菜单是根据网页的层次结构自动创建的。 称为**默认**菜单。 您还可以创建一个自定义菜单以显示在网站上。 详细信息：[添加自定义菜单](compose-page.md#add-a-custom-menu)

> [!div class=mx-imgBorder]
> ![网站导航](media/website-navigation.png "网站导航")

如果您正在使用 Dynamics 365 门户，并且希望菜单与页面层次结构相同，则必须从**导航菜单**列表中选择**默认**。

> [!div class=mx-imgBorder]
> ![默认导航菜单](media/navigation-menu-default.png "默认导航菜单")

## <a name="manage-webpage"></a>管理网页

1.  [编辑门户](manage-existing-portals.md#edit)以在门户设计器中将其打开。  

2.  从屏幕左侧的工具栏中选择**页面** ![页面图标](media/pages-icon.png "页面图标")。  

3.  将鼠标悬停在要管理的页面上，然后为要管理的网页选择**省略号**按钮 (…)。 或者。 您可以右键单击要管理的页面。

4.  从上下文菜单中选择所需的操作：

    - **在默认菜单中隐藏**：通过默认菜单隐藏页面，使其不显示在站点地图中。

    - **默认菜单中显示**：通过默认菜单在站点地图中显示页面。

    - **添加子页**：将子页面添加到所选页面。 子页面继承其父页面的页面模板。

    - **设置为主页**：将页面设置为主页。 新主页的 URL 设置为网站的根，旧页面的 URL 相应更新。

    - **上移**：将页面在层次结构中向上移动。

    - **下移**：将页面在层次结构中向下移动。

        > [!NOTE]
        > 在同一级别的页面之间支持上下移动页面。

    - **提升子页**：减少缩进量，使子页面位于层次结构中上一页的级别。

    - **创建子页**：增加缩进量，使页面成为位于层次结构中上一页的子页面。

    - **删除**：删除页面。

        > [!div class=mx-imgBorder]
        > ![网页管理选项](media/webpage-manage-options.png "网页管理选项")  





