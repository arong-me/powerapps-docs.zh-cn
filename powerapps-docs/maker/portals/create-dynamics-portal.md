---
title: 在 Dynamics 365 中在包含模型驱动应用的环境中创建门户 | Microsoft Docs
description: 在 Dynamics 365 中在包含模型驱动应用的环境中创建门户的说明。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 896f6cfe9fabf08606e69b68b9957835a0147aee
ms.sourcegitcommit: 861ba8e719fa16899d14e4a628f9087b47206993
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "2873385"
---
# <a name="create-a-portal-in-an-environment-containing-model-driven-apps-in-dynamics-365"></a>在 Dynamics 365 中在包含模型驱动应用的环境中创建门户

如果您在 Dynamics 365 中选择包含模型驱动应用的环境（例如 Dynamics 365 Sales 和 Dynamics 365 Customer Service），则可以创建[门户模板](portal-templates.md)中提到的门户。

1.  登录到 [Power Apps](https://make.powerapps.com)。

2.  在左侧窗格中选择**创建**，然后在**搜索模板**字段中输入**门户**以显示所有 Dynamics 365 门户模板。

    > [!div class=mx-imgBorder]
    > ![Dynamics 365 门户模板](media/dynamics-portals.png "Dynamics 365 门户模板")  

3.  选择所需的门户模板。

4.  在创建门户窗口中，输入门户的名称和网站的地址，然后从下拉列表中选择一种语言。 完成后，选择**创建**。 创建过程与[创建 Common Data Service 起点门户](create-portal.md)一节中介绍的过程相同。

> [!NOTE]
> - 如果您购买了早期的门户加载项，并且想要使用该加载项来设置门户，则必须转到 **Dynamics 365 管理中心**页面。 详细信息：[使用早期的门户加载项设置门户](provision-portal-add-on.md)
> - 如果您已经使用早期的门户加载项设置了门户，则仍然可以从 [make.powerapps.com](https://make.powerapps.com) 自定义和管理门户。
> - 从 [make.powerapps.com](https://make.powerapps.com) 设置门户不会使用早期的门户加载项。 另外，这些门户未在 **Dynamics 365 管理中心**页面上的**应用程序**选项卡下列出。
> - 无法从 **Dynamics 365 管理中心**页面创建 Common Data Service 起点门户。
> - 要在租户中禁用门户创建，请参阅[在租户中禁用门户创建](create-portal.md#disable-portal-creation-in-a-tenant)。
> - 创建门户时，将安装一些解决方案并导入示例数据。

