---
title: 分配或共享记录 |MicrosoftDocs
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
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/30/2020
ms.locfileid: "76886502"
---
# <a name="assign-or-share-records"></a>分配或共享记录

如果希望组织中的其他人来处理客户记录，可以将记录分配给该人员。 您还可以向团队或您自己分配记录。  

如果要保留记录的所有权，请使用 "**共享**" 选项，并让其他人与你一起工作。 

1. 从左侧导航窗格中，选择 "记录类型"。 例如， **Contacts**。

2. 从记录列表中，选择要重新分配的记录。  
  
3. 在命令栏上，选择 "**分配**"。

   > [!div class="mx-imgBorder"]
   > ![重新分配记录](media/assign1.png "重新分配记录")

   > [!NOTE]
   > 如果要保留记录的所有权，但允许其他人使用该记录，请选择 "**共享**"。 然后，使用工具提示指导您完成**共享**选项。 
   
4. 在 "分配" 对话框中的 "**分配到**" 区域中，选择 "**我**" 或 "**用户或团队**"。

   > [!div class="mx-imgBorder"]
   > ![向我或团队重新分配记录](media/assign2.png "重新分配 a 记录团队")
  
   如果选择 "**用户或团队**"，请在 "**查找记录**" 框中输入用户或团队的名称。 如果需要创建新记录，请选择 " **+ 新建**"。
  
5. 完成后，选择 "**分配**"。

## <a name="use-advanced-find-to-reassign-records"></a>使用高级查找重新分配记录

使用 "高级查找" 搜索记录，然后将其重新分配给其他人。 有关高级查找的详细信息，请参阅[创建、编辑或保存高级查找搜索](advanced-find.md)。


1. 在命令栏上，选择 "**高级查找**"。

   > [!div class="mx-imgBorder"]
   > ![高级查找](media/assign3.png "advacned 查找")
   
2. 从记录列表中，选择要重新分配的记录，然后选择 "分配" 选项。

   > [!div class="mx-imgBorder"]
   > ![使用 "高级查找" 重新分配记录](media/assign4.png "使用 advacned "查找" 重新分配记录")
   
 
 ## <a name="reassign-all-records-for-admins"></a>重新分配所有记录（适用于管理员）
 
 管理员可以从管理设置区域为用户重新分配所有记录。
 
 1. 转到“设置” > “安全”。
 2. 选择 "**用户**" 并选择 "用户名"，以打开用户的配置文件。
 3. 在命令栏上，选择 "**重新分配记录**"。
 
   > [!div class="mx-imgBorder"]
   > ![重新分配所有记录](media/assign5.png "重新分配所有记录")
   
 4. 在 "**重新分配记录**" 对话框中，选择要重新分配所有记录的方法，然后选择 **"确定"** 。
 
  > [!NOTE]
   > "**重新分配记录**" 选项将重新分配所有记录，而不考虑它们的状态。 不活动记录和活动记录将重新分配给其他用户或团队。 当将记录重新分配给另一个用户或团队时，这还将停用所有已激活的进程，包括业务规则和工作流。 新所有者必须激活必须使用的进程。
 
   > [!div class="mx-imgBorder"]
   > ![将所有记录重新分配给用户或团队](media/assign6.png "将所有记录重新分配给用户或团队")
 

