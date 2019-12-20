---
title: 使用 Power Apps 创建卡窗体 | MicrosoftDocs
description: 了解如何在 Power Apps 中创建和使用卡窗体
keywords: ''
ms.date: 03/05/2019
ms.service: powerapps
ms.custom: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- PowerApps
author: Mattp123
ms.assetid: be93b9d7-f1c2-4ee7-8d7c-0f5c34dfa5f7
ms.author: matp
manager: kvivek
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
topic-status: Drafting
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 2e39935c3373974bd968c93ee0fce2743f39360d
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "2884945"
---
# <a name="create-a-card-form"></a>创建卡片式窗体
卡窗体用于统一接口应用程序的视图。 卡窗体用于以适用于移动设备的紧凑格式呈现信息。 例如，“我的可用客户”视图的默认卡窗体定义为每个客户记录显示的信息。 

> [!div class="mx-imgBorder"] 
> ![](media/account-cardform-for-myactiveaccounts-view.png "Account card form for my active accounts view")

尽管可以通过与其他窗体类型相同的方式创建和编辑卡窗体，但将卡窗体添加到应用程序是不同的。 不是作为应用程序组件添加窗体，而是使用**只读网格**控件将自定义卡窗体添加到视图。 

## <a name="create-a-card-form"></a>创建卡片式窗体
1. 若要创建卡窗体，登录到 [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)。 
2. 展开**数据**，选择**实体**，选择所需实体，然后选择**窗体**选项卡。
3. 在工具栏上，选择**添加窗体**，然后选择**卡窗体**。 或者，您可以打开属于**卡**窗体的现有**窗体类型**来对其进行编辑。
4. 添加所需的字段。 建议您限制字段数，以便窗体在小屏幕上仍能正常显示。 
5. 选择**保存**，然后选择**发布**。 

## <a name="add-a-card-form-to-a-view"></a>将卡窗体添加到视图 
1. 登录到 [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)。
2. 展开**数据**，选择所需实体，然后选择**视图**选项卡。
3. 选择所需的视图，然后在视图设计器工具栏上，选择**切换到经典**。
4. 从**常规任务**窗格中选择**自定义控件**。
5. 选择**添加控件**，从控件列表中选择**只读网格**，然后选择**添加**。

   > [!NOTE]
   > 有两个只读网格控件。 名为**只读网格(默认)** 的默认只读网格控件不支持自定义卡窗体。 

6. 在**只读网格**属性页配置以下属性，然后选择**确定**。 
   - **卡窗体**。 选择铅笔图标 ![编辑控件属性](media/ccf-pencil-icon.png)，然后选择您要在视图中显示的卡窗体。 默认情况下，与视图关联的主要实体已经选择，但是，您也可以更改它。 
   - **回流行为**。 如果您想要更改在调整大小时是否显示卡窗体，请选择铅笔图标 ![编辑控件属性](media/ccf-pencil-icon.png)。 详细信息：[允许网格重排为列表](specify-properties-for-unified-interface-apps.md#allow-grid-to-reflow-into-list)  
   - 选择要显示**只读网格**的客户端类型：**Web**、**手机**或**平板电脑**。

     ![卡窗体的只读网格](media/read-only-grid-for-cardform.png)

7. 选择**确定**以关闭**自定义控件**属性页面。 
8. 在经典视图设计器工具栏中，选择**保存并关闭**。 

## <a name="see-also"></a>另请参阅
[使用自定义控件实现模型驱动应用程序的数据可视化](use-custom-controls-data-visualizations.md)



