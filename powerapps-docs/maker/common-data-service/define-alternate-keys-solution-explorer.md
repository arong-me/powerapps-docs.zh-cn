---
title: 使用解决方案资源管理器定义备用键 | MicrosoftDocs
description: 了解如何使用解决方案资源管理器在 Common Data Service 中定义可用于引用记录的备用键
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
ms.openlocfilehash: 8b1b38c94cbd4615ff0ab449944e65089865a823
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2019
ms.locfileid: "2758708"
---
# <a name="define-alternate-keys-using-solution-explorer"></a>使用解决方案资源管理器定义备用键

解决方案资源管理器为查看和创建 Common Data Service 的备用键提供一种方法。

[PowerApps 门户](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)支持配置最常见的选项，但是某些选项只能使用解决方案资源管理器设置。 <br />详细信息： 
- [定义引用记录的备用键](define-alternate-keys-reference-records.md)<br />
- [使用 PowerApps 门户定义备用键](define-alternate-keys-portal.md)

## <a name="open-solution-explorer"></a>打开解决方案资源管理器

您创建的任何备用键的名称中都包含自定义前缀。 这是根据您在其中工作的解决方案的解决方案发布商设置的。 如果您关心自定义前缀，请确保在非托管解决方案中工作，其中的自定义前缀是您需要的此实体的前缀。 详细信息：[更改解决方案发布商前缀](change-solution-publisher-prefix.md) 

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

## <a name="view-alternate-keys"></a>查看备用键

1. 解决方案资源管理器打开后，在**组件**下展开**实体**，然后选择您要查看备用键的实体。
2. 展开实体，选择**键**。

    ![查看备用键](media/view-alternate-keys-solution-explorer.png)

## <a name="create-an-alternate-key"></a>创建备用键

1. 在[查看备用键](#view-alternate-keys)时选择**新建**。
1. 在窗体上，输入**显示名称**。 **名称**字段将根据**显示名称**自动填充。 
2. 从**可用属性**列表，选择每个属性，然后选择**添加 >** 将属性移至**所选属性**列表。
    ![创建备用键](media/create-alternate-key-solution-explorer.png)
1. 选择**确定**关闭窗体。

### <a name="optional-view-the-system-job-tracking-creation-of-indexes"></a>（可选）查看跟踪索引创建的系统作用
1. 在创建了新备用键后[查看备用键](#view-alternate-keys)时，您将看到所创建的键的行。
2. 在**系统作业**列中，您将找到监视索引创建以支持备用键的系统作业的链接。 
    
    此系统作业将有一个这样格式的名称：`Create index for {0} for entity {1}`，其中 `0` 是备用键的**显示名称**，`1` 是实体的名称。

    系统作业的链接不会在系统作业成功完成后显示。 详细信息：[监视和管理系统作业](/dynamics365/customer-engagement/admin/monitor-manage-system-jobs)


## <a name="delete-an-alternate-key"></a>删除备用键

在[查看备用键](#view-alternate-keys)时选择![删除](media/delete.gif)。

### <a name="see-also"></a>另请参阅

[定义引用记录的备用键](define-alternate-keys-reference-records.md)<br />
[使用 PowerApps 门户定义备用键](define-alternate-keys-portal.md)<br />
[开发人员文档：定义实体的备用键](/dynamics365/customer-engagement/developer/define-alternate-keys-entity)
