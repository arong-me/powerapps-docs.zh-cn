---
title: 创建和管理网页 |Microsoft Docs
description: 介绍如何在门户中创建和管理网页。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: b62f6a811d2f2e6c5218ef601f18d69357d15ba9
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/11/2019
ms.locfileid: "72977004"
---
# <a name="create-and-manage-webpages"></a>创建和管理网页

网页是由网站中的唯一 URL 标识的文档。 它是网站的核心对象之一，通过与其他网页的父关系和子关系构建网站的层次结构。

> [!NOTE]
> 如果使用 PowerApps portal Studio 自定义门户，则网站用户会注意到性能影响。 建议您在非高峰时段（在实时门户上）进行更改。

## <a name="create-webpage"></a>创建网页

1.  [编辑门户](manage-existing-portals.md#edit)以在 PowerApps portal Studio 中将其打开。  

2.  在命令栏中，选择 "**新建页面**"，然后从 "**布局**" 或 "**固定布局**" 中选择页面。

    > [!div class=mx-imgBorder]
    > 新建![网页](media/create-webpage.png "创建新网页")

    > [!NOTE]
    > - 使用**布局**创建页面使您可以灵活地编辑整个页面。 **固定布局**包含在门户预配过程中安装的页面模板以及使用[门户管理应用](configure/configure-portal.md)创建的自定义页面模板。
    > - 对于要使用 "**布局**" 选项创建的页面，将安装新的 "**默认 studio 模板**" 页面模板。

3.  在屏幕右侧的 "属性" 窗格中，输入以下信息：

    - **Name**：页面的名称。 此值还用作页面的标题。

    - **部分 url**：用于生成此页面的门户 URL 的 url 路径段。

    - **模板**：用于在门户上呈现此页面的页面模板。 如果需要，可以从列表中选择另一个模板。

        > [!div class=mx-imgBorder]
        > ![网页属性](media/webpage-props.png "网页属性")

将添加创建的网页，并在 "**页面**" 窗格中显示其层次结构。 若要查看 "**页面**" 窗格，请从屏幕左侧的 toolbelt 中选择 "**页面**![页面" 图标](media/pages-icon.png "页面图标")。  

假设你已为门户创建了几个网页。 页面层次结构如下所示：

> [!div class=mx-imgBorder]
> ![页面窗格](media/pages-pane.png "页面窗格")  

网站上的主菜单是基于网页的层次结构自动创建的。 它被称为**默认**菜单。 你还可以创建要在网站上显示的自定义菜单。 详细信息：[添加自定义菜单](compose-page.md#add-a-custom-menu)

> [!div class=mx-imgBorder]
> ![网站导航](media/website-navigation.png "网站导航")

如果使用的是使用 Dynamics 365 环境创建的门户，并且希望该菜单与页面层次结构相同，则必须从**导航菜单**列表中选择 "**默认**"。

> [!div class=mx-imgBorder]
> ![默认导航菜单](media/navigation-menu-default.png "默认导航菜单")

## <a name="manage-webpage"></a>管理网页

1.  [编辑门户](manage-existing-portals.md#edit)以在 PowerApps portal Studio 中将其打开。  

2.  在屏幕左侧的 toolbelt 中选择**页面**![页面]图标(media/pages-icon.png "页面图标")。  

3.  将鼠标悬停在要管理的页面上，然后选择要管理的网页的**省略号**按钮（...）。 或者. 你可以右键单击要管理的页面。

4.  从上下文菜单中选择所需的操作：

    - **在默认菜单中隐藏**：隐藏在站点地图中通过默认菜单显示的页面。

    - **在默认菜单中显示**：通过默认菜单显示站点地图中的页面。

    - **添加子页**：向所选页面添加子页。 子页面继承其父页面的页面模板。

    - **设置为主页**：将页面设置为主页。 新主页的 URL 将设置为网站的根目录，并且会相应地更新旧页面的 URL。

    - **上移**：在层次结构中向上移动页面。

    - **向下移动**：在层次结构中向下移动页面。

        > [!NOTE]
        > 同一级别的页支持在页面上上下移动。

    - **提升子页**：减少缩进，使子页面成为层次结构中前一页的级别。

    - **设置子页**：增加缩进，使页面成为层次结构中上一页的子页。

    - **删除**：删除页面。

        > [!div class=mx-imgBorder]
        > ![网页管理选项](media/webpage-manage-options.png "网页管理选项")  





