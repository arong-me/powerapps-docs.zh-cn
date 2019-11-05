---
title: 在 Dynamics 365 中包含模型驱动应用的环境中创建门户 |Microsoft Docs
description: 说明如何在 Dynamics 365 中包含模型驱动应用的环境中创建门户。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 50459f3fcd9ebe8894196f934c1b1d2275c490c4
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2019
ms.locfileid: "73542634"
---
# <a name="create-a-portal-in-an-environment-containing-model-driven-apps-in-dynamics-365"></a>在 Dynamics 365 中包含模型驱动应用的环境中创建门户

如果在 Dynamics 365 中选择包含模型驱动应用的环境（如 Dynamics 365 Sales 和 Dynamics 365 Customer Service），则可以创建[门户模板](portal-templates.md)中提到的门户。

1.  登录 [PowerApps](https://make.powerapps.com)。

2.  选择左窗格中的 "**创建**"，然后在 "**搜索模板**" 字段中输入**门户**，以显示所有 Dynamics 365 门户模板。

    > [!div class=mx-imgBorder]
    > ![Dynamics 365 门户模板](media/dynamics-portals.png "Dynamics 365 门户模板")  

3.  选择所需的门户模板。

4.  在 "创建门户" 窗口中，输入门户网站的名称和地址，然后从下拉列表中选择一种语言。 完成后，选择 "**创建**"。 创建过程与[创建 Common Data Service 的入门门户](create-portal.md)部分中所述的过程相同。

> [!NOTE]
> - 如果你购买了较旧的门户外接程序，并且想要使用该外接程序预配门户，则必须使用 " **Dynamics 365 管理中心**" 页。 详细信息：[使用旧门户加载项预配门户](provision-portal-add-on.md)
> - 如果已使用旧版门户外接程序预配了门户，则仍可通过[make.powerapps.com](https://make.powerapps.com)对其进行自定义和管理。
> - 从[make.powerapps.com](https://make.powerapps.com)预配门户不会使用较旧的门户加载项。 此外，这些门户未列在**Dynamics 365 管理中心**页面上的 "**应用程序**" 选项卡下。
> - 无法从**Dynamics 365 管理中心**页面创建 Common Data Service starter 门户。
> - 若要禁用在租户中创建门户，请参阅[禁用在租户中创建门户](create-portal.md#disable-portal-creation-in-a-tenant)。

