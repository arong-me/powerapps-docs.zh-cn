---
title: 合并重复记录 |MicrosoftDocs
ms.custom: ''
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 10/31/2019
ms.author: mduelae
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: c0811645429c9f1e7570ceeaf316a5217e440ae4
ms.sourcegitcommit: bee698ca0d11524377b67813a65e1a022d08c05e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/05/2019
ms.locfileid: "73609884"
---
# <a name="merge-duplicate-records"></a>合并重复记录 

当你或其他人手动输入数据或批量导入数据时，重复的记录可能会蔓延到你的数据中。 Common Data Service 通过为活动记录（例如，帐户和联系人）提供重复检测来帮助你解决可能的重复项。 合并记录时，所有相关或子记录也将合并。 管理员还可以为其他情况设置重复检测规则。  
  
例如，假设您输入一个联系人记录 Jim Glynn，以及一个移动电话号码。  重复检测规则发现已有类似的记录，并显示此对话框。  
  
 > [!div class="mx-imgBorder"] 
 > ![重复的联系人记录 detectied](media/duplicates-detected.png "重复的联系人记录 detectied")  
  
 不确定这是一条新记录（碰巧与现有联系人具有相同名称）或重复，因此选择 "**忽略并保存**"。  
  
 接下来，您将访问 "**所有联系人**" 列表，并看到现在有两个同名的记录。 检查记录后，确定这些记录是需要合并的重复项。  
 
 > [!div class="mx-imgBorder"] 
 > ![重复的联系人记录 detectied](media/duplicates-detected_1.png "重复的联系人记录 detectied")  
 
Common Data Service 包括帐户和联系人的重复检测规则。 这些规则会自动打开，因此，无需执行任何操作即可为这些记录类型设置重复检测。  
  
> [!NOTE]
>  如果在您的系统上可用，除了联系人和帐户之外，您还可以检查其他记录类型的重复项。 请与系统管理员联系。 [查找你的管理员或支持人员](find-admin.md)  
  
## <a name="merge-duplicate-records"></a>合并重复记录  
  
1. 选择重复的记录，然后选择 "**合并**"。  
  
   > [!div class="mx-imgBorder"] 
   > ![重复的联系人记录 detectied](media/duplicates-detected_2.png "重复的联系人记录 detectied")  
  
2. 在 "**合并记录**" 对话框中，选择要保留的主记录（要保留的记录），然后选择要合并到主记录的新记录中的任何字段。 这些字段中的数据可能会覆盖主记录中的现有数据。 选择“确定”。  
  
     
   > [!div class="mx-imgBorder"] 
   > ![用于合并记录的对话框](media/merge-records-dialog.png "用于合并记录的对话框")  
  
> [!NOTE]
>  在以下几种情况下，可能会发现重复项：  
> 
> - 创建或更新记录的时间。  
>   - 使用 Dynamics 365 for Outlook 时，从脱机切换到联机状态。  
>   - 使用导入数据向导导入数据时。  
> 
>   合并记录、将活动保存为 "已完成" 或 "更改记录" 状态（如激活或重新激活记录）时不会检测到重复项。  
