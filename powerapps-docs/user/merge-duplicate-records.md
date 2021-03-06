---
title: 合并重复记录 | MicrosoftDocs
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
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/05/2019
ms.locfileid: "73609884"
---
# <a name="merge-duplicate-records"></a>合并重复记录 

如果你或其他人手动输入数据或批量导入数据，重复的记录可能会混入数据。 通过提供对活动记录（例帐户和联系人）进行重复检测，Common Data Service 可帮助处理可能的重复项。 合并记录时，还会合并任何相关记录或子记录。 管理员还可以为其他情况设置重复项检测规则。  
  
例如，假设输入联系人记录 Jim Glynn 及其手机号码。  重复项检测规则发现已有类似记录，并显示此对话框。  
  
 > [!div class="mx-imgBorder"] 
 > ![检测到的重复联系人记录](media/duplicates-detected.png "检测到的重复联系人记录")  
  
 如果不确定该记录是新记录（恰好与现有联系人同名）还是重复记录，可选择“忽略并保存”  。  
  
 接下来，转到“所有联系人”列表，然后查看目前的两条同名记录  。 查看记录后，确定这些记录是否是需合并的重复项。  
 
 > [!div class="mx-imgBorder"] 
 > ![检测到的重复联系人记录](media/duplicates-detected_1.png "检测到的重复联系人记录")  
 
Common Data Service 包括针对帐户和联系人的重复项检测规则。 这些规则会自动启用，因此无需执行任何操作即可为这些记录类型设置重复项检测。  
  
> [!NOTE]
>  如果系统有提供，你还可以检查除联系人和帐户以外的其他记录类型的重复项。 请与系统管理员联系。 [联系你的管理员或支持人员](find-admin.md)  
  
## <a name="merge-duplicate-records"></a>合并重复记录  
  
1. 选择重复的记录，然后选择“合并”  。  
  
   > [!div class="mx-imgBorder"] 
   > ![检测到的重复联系人记录](media/duplicates-detected_2.png "检测到的重复联系人记录")  
  
2. 在“合并记录”对话框中，选择要保留的主记录，然后选择要合并到主记录的新记录中的任何字段  。 这些字段中的数据可能会覆盖主记录中的现有数据。 选择“确定”。   
  
     
   > [!div class="mx-imgBorder"] 
   > ![用于合并记录的对话框](media/merge-records-dialog.png "用于合并记录的对话框")  
  
> [!NOTE]
>  在下列情况下，可能会发现重复项：  
> 
> - 创建或更新记录时。  
>   - 使用 Dynamics 365 for Outlook 从脱机切换到联机状态时。  
>   - 使用导入数据向导导入数据时。  
> 
>   合并记录、将活动另存为“已完成”或更改记录状态（如激活或重新激活记录）时不会检测到重复项。  
