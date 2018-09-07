---
title: 管理数据丢失防护 (DLP) 策略 | Microsoft Docs
description: 管理 PowerApps 数据丢失防护策略的演示。
author: manasmams
manager: kvivek
ms.service: powerapps
ms.component: pa-admin
ms.topic: conceptual
ms.date: 03/21/2018
ms.author: manasma
search.audienceType:
- admin
search.app:
- D365CE
- PowerApps
- Powerplatform
ms.openlocfilehash: 4faa8a4cc58b138eec4e7dfe8d35b927faf905b7
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/24/2018
ms.locfileid: "42837153"
---
# <a name="manage-data-loss-prevention-dlp-policies"></a>管理数据丢失防护 (DLP) 策略
组织的数据是取得成功的关键所在。 其数据需要随时可用于决策，但必须受到保护，避免与无权访问这些数据的受众共享。 为了保护此数据，PowerApps 允许创建和强制执行数据丢失防护 (DLP) 策略，该策略定义可以共享特定业务数据的客户连接器。 例如，使用 PowerApps 的组织可能不希望其存储在 SharePoint 中的业务数据自动发布到其 Twitter 源。

若要创建、编辑或删除 DLP 策略，必须有“环境管理员”或“Azure Active Directory 租户管理员”权限。 有关详细信息，请参阅 [PowerApps 中的环境管理](environments-administration.md)。

有关如何创建 DLP 策略的说明，请参阅[创建数据丢失防护 (DLP) 策略](create-dlp-policy.md)。

## <a name="find-a-dlp-policy"></a>查找 DLP 策略
1. 在 [https://admin.powerapps.com]([https://admin.powerapps.com) 上登录到管理中心。
2. 在导航窗格中，单击或点击“数据策略”。 如果有一长串的策略，请使用“搜索”框查找特定的 DLP 策略。

    ![](./media/prevent-data-loss/data-policies.png)

## <a name="edit-a-dlp-policy"></a>编辑 DLP 策略
1. 在数据丢失防护策略列表中，单击或点击想要编辑的策略旁的铅笔图标。

    ![登录](./media/prevent-data-loss/3.png)
2. 进行更改，然后单击或点击“保存策略”。

    > [!NOTE]
    > 环境 DLP 策略无法替代租户范围的 DLP 策略。
    >
    >

    若要查看所做的更改，请找到数据丢失防护策略列表中的 DLP 策略并单击或点击它以查看其属性。

## <a name="delete-a-dlp-policy"></a>删除 DLP 策略
1. 在数据丢失防护策略列表中，单击或点击想要删除的策略旁的垃圾桶图标。

    ![登录](./media/prevent-data-loss/3-delete.png)
4. 在确认对话框中，单击或点击“删除”。

    策略随即删除并且不再显示在数据丢失防护策略列表中。

## <a name="next-steps"></a>后续步骤
* [详细了解环境](environments-administration.md)
* [详细了解 Microsoft PowerApps](../maker/canvas-apps/getting-started.md)
