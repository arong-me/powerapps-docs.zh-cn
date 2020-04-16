---
title: 使用 Power Apps 从头构建您的第一个模型驱动应用 | Microsoft Docs
description: 了解如何构建简单的模型驱动应用程序
documentationcenter: ''
author: Mattp123
manager: kvivek
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: model
ms.date: 02/05/2019
ms.author: matp
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 4c404c8aab419fa4b0445a392d7440c2ab3f099b
ms.sourcegitcommit: cf492063eca27fdf73459ff2f9134f2ca04ee766
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "3136132"
---
# <a name="build-your-first-model-driven-app-from-scratch"></a>从头构建您的第一个模型驱动应用程序
模型驱动应用程序的设计是以组件为中心的应用程序开发方法。 在本主题中，您使用 Power Apps 环境中提供的一种标准实体简化模型驱动应用的创建方法。

> [!TIP]
> 若要了解有关构建模型驱动应用程序的所有信息，请从此处开始：[了解模型驱动应用程序的组件](model-driven-app-components.md)。 

## <a name="sign-in-to-power-apps"></a>登录到“Power Apps”
登录到 [Power Apps](https://make.powerapps.com/)。 如果还没有 [!INCLUDE [powerapps](../../includes/powerapps.md)] 帐户，请选择**免费开始**链接。 

## <a name="create-your-model-driven-app"></a>创建您的模型驱动应用程序

1.    选择所需环境，或转到 [Power Apps 管理中心](https://admin.powerapps.com/)创建一个新环境。

2.  在**主页**页面，选择**从头开始制作模型驱动应用**。

    > [!div class="mx-imgBorder"] 
    > <img src="media/build-first-model-driven-app/start-from-blank-model-driven.png" alt="Start from blank model" height="429" width="673">

3.  选择**创建**。

3.    在**创建新应用程序**页面，输入以下详细信息，然后选择**完成**： 
  - **名称**：输入应用的名称，如 *My first app*。 
  - **唯一名称**：默认情况下，唯一名称使用您在**名称**框中指定的名称，无空格，前面加发布商前缀和下划线 (_)。 例如，*crecf_Myfirstapp*。 详细信息：[更改解决方案发布商前缀](../common-data-service/change-solution-publisher-prefix.md)
  - **描述**：键入应用程序是什么或做什么的简短描述，如*这是我的第一个应用程序*。
有关其他应用程序属性的信息，请参阅[创建应用程序](create-edit-app.md#create-an-app)。

  > [!div class="mx-imgBorder"] 
  > ![创新一个新应用](media/create-new-app.png "创新一个新应用")

## <a name="add-components-to-your-app"></a>将组件添加到应用程序
从应用程序设计器，将组件添加到您的应用程序。
1.    选择**打开站点地图设计器**编辑按钮打开站点地图设计器。

      > [!div class="mx-imgBorder"] 
      > ![Create-new-sitemap](media/build-first-model-driven-app/new-sitemap.png "站点地图设计器")

2.    在站点地图设计器上，选择**新建子区域**，在右侧窗格中选择**属性**选项卡，然后选择以下属性。
  - **类型**：实体
  - **实体**：客户

    > [!div class="mx-imgBorder"] 
    > ![向站点地图添加组件](media/build-first-model-driven-app/sitemap.png "新建子区域")

3.    选择**保存并关闭**。
4.    在应用程序设计器区域，选择**窗体**，然后在**主窗体**组下的右窗格上选择**客户**窗体。

      > [!div class="mx-imgBorder"] 
      > ![客户主窗体](media/build-first-model-driven-app/main-form.png "应用窗体")

5.    在应用程序设计器区域，选择**视图**，然后选择**可用客户**、**所有客户**和**我的可用客户**视图。<!-- All checkbox seems to be selected by default -->

      > [!div class="mx-imgBorder"] 
      > ![客户视图](media/build-first-model-driven-app/views.png "应用视图")

6. 在应用程序设计器区域，选择**图表**，然后选择**按行业列出的客户**图表。
7. 在应用程序设计器工具栏中，选择**保存**。

      > [!div class="mx-imgBorder"] 
      > ![应用程序设计器工具栏保存](media/build-first-model-driven-app/app-designer-toolbar.png "保存应用")
 
<!-- ##  Validate your app
This step checks for component dependencies that are required for the app to work, but haven't yet been added to the app. 

1. On the app designer canvas, select the component that indicates a dependency, such as the **Forms** component. Then, on the right-pane select the **Required** tab, expand **Entity Dependencies** and then select all required dependencies. 

    ![Add dependencies](media/build-first-model-driven-app/resolve-dependencies.png)

2. Select **Add Dependencies**.
3. On the app designer toolbar, select **Save**.  -->

## <a name="publish-your-app"></a>发布应用程序
在应用程序设计器工具栏中，选择**发布**。

发布应用程序后，其便可供运行或与其他人共享。

  > [!div class="mx-imgBorder"] 
  > ![简单的客户实体应用程序](media/build-first-model-driven-app/accounts-quickstart-app.png "运行应用")

## <a name="next-steps"></a>后续步骤
在本主题中，您构建简单的模型驱动应用程序。 
- 要查看在您运行时您的应用程序的外观，请参阅[在移动设备上运行模型驱动应用程序](../../user/run-app-client-model-driven.md)。
- 若要了解如何共享您的应用程序，请参阅[共享模型驱动应用程序](share-model-driven-app.md)。
- 若要开始并了解有关构建模型驱动应用程序的所有信息，请参阅[了解模型驱动应用程序的组件](model-driven-app-components.md)。
