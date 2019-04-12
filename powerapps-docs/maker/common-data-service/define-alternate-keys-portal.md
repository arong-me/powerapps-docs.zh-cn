---
title: 使用 PowerApps 门户定义备用键 | MicrosoftDocs
description: 了解如何使用 PowerApps 门户定义备用键
ms.custom: ''
ms.date: 05/31/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
author: Mattp123
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="define-alternate-keys-using-powerapps-portal"></a>使用 PowerApps 门户定义备用键

[PowerApps 门户](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)提供通过 Common Data Service 查看和创建实体备用键的简单方法。

此门户支持配置最常见的选项，但是某些选项只能使用解决方案资源管理器设置。 <br />详细信息： 
- [定义引用记录的备用键](define-alternate-keys-reference-records.md)
- [使用解决方案资源管理器定义备用键](define-alternate-keys-solution-explorer.md)

## <a name="view-alternate-keys"></a>查看备用键

1. 从 [PowerApps 门户](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)，选择**模型驱动**或**画布**设计模式。
2. 选择**数据** > **实体**，然后选择您要查看的实体。
3. 选择**键**查看定义的任何备用键的列表。

    ![查看备用键](media/view-alternate-keys-portal.png)

## <a name="create-an-alternate-key"></a>创建备用键

1. 在[查看备用键](#view-alternate-keys)时选择**添加键**。
2. 使用面板设置**显示名称**并选择要用于创建备用键的字段。

    **名称**字段将根据显示名称填充。

    ![示例备用键定义](media/alternate-key-account-number-sic-code.png)

1. 选择**完成**关闭面板。
2. 单击**保存实体**创建备用键。

> [!NOTE]
> 备用键不会立即可用。 当您保存实体以创建支持备用键的数据库索引时系统作业启动。

## <a name="delete-an-alternate-key"></a>删除备用键

在[查看备用键](#view-alternate-keys)时，选择您要删除的键并从命令栏中选择**删除键**。

### <a name="see-also"></a>另请参阅

[定义引用记录的备用键](define-alternate-keys-reference-records.md)<br />
[使用解决方案资源管理器定义备用键](define-alternate-keys-solution-explorer.md)<br />
[开发人员文档：定义实体的备用键](/dynamics365/customer-engagement/developer/define-alternate-keys-entity)
