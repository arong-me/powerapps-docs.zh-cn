---
title: 分配或共享记录 | MicrosoftDocs
ms.custom: ''
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 1/20/2020
ms.author: mduelae
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 81a6513f98351f656fdac3fd0ccc24a10061ca85
ms.sourcegitcommit: d0f02fdaa125feaea884932e1ef31b8fea1bd10c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/30/2020
ms.locfileid: "76886502"
---
# <a name="assign-or-share-records"></a>分配或共享记录

如果希望组织中的其他人能够处理客户记录，你可以将记录分配给该人员。 你还可以向团队或自己分配记录。  

如果希望保留记录的所有权，但又要与其他人合作处理，请使用“共享”选项  。 

1. 从左侧导航窗格，选择记录类型。 例如，“联系人”  。

2. 从记录列表中，选择要重新分配的记录。  
  
3. 在命令栏上，选择“分配”  。

   > [!div class="mx-imgBorder"]
   > ![重新分配记录](media/assign1.png "重新分配记录")

   > [!NOTE]
   > 如果希望保留记录的所有权，但允许其他人处理，请选择“共享”  。 然后，使用工具提示了解“共享”选项  。 
   
4. 在“分配”对话框的“分配对象”区域中，选择“我”或“用户或团队”    。

   > [!div class="mx-imgBorder"]
   > ![将记录重新分配给我或团队](media/assign2.png "向我和团队重新分配记录")
  
   如果选择“用户或团队”，请在“查找记录”框中，输入用户或团队的名称   。 如需新建实体，请选择“+ 新建”  。
  
5. 完成后，选择“分配”  。

## <a name="use-advanced-find-to-reassign-records"></a>使用高级查找重新分配记录

使用高级查找搜索记录，然后将其重新分配给其他人。 有关高级查找的详细信息，请参阅[创建、编辑或保存高级查找搜索](advanced-find.md)。


1. 在命令栏上，选择“高级查找”  。

   > [!div class="mx-imgBorder"]
   > ![高级查找](media/assign3.png "高级查找")
   
2. 从记录列表中，选择要重新分配的记录，然后选择分配选项。

   > [!div class="mx-imgBorder"]
   > ![使用高级查找重新分配记录](media/assign4.png "使用高级查找重新分配记录")
   
 
 ## <a name="reassign-all-records-for-admins"></a>重新分配所有记录（适用于管理员）
 
 管理员可以从管理设置区域为用户重新分配所有记录。
 
 1. 转到“设置” > “安全”   。
 2. 选择“用户”，然后选择用户名以打开用户的配置文件  。
 3. 在命令栏上，选择“重新分配记录”  。
 
   > [!div class="mx-imgBorder"]
   > ![重新分配所有记录](media/assign5.png "重新分配所有记录")
   
 4. 在“重新分配记录”对话框中，选择希望重新分配所有记录的方式，然后选择“确定”   。
 
  > [!NOTE]
   > “重新分配记录”选项将重新分配所有记录，无论其状态如何  。 非活动和活动记录将重新分配给其他用户或团队。 将记录重新分配给其他用户或团队时，这还会停用所有已激活的进程，其中包括业务规则和工作流。 新的所有者必须激活要使用的进程。
 
   > [!div class="mx-imgBorder"]
   > ![将所有记录重新分配给用户或团队](media/assign6.png "将所有记录重新分配给用户或团队")
 

