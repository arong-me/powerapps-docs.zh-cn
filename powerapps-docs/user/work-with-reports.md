---
title: 处理报表 | Microsoft Docs
description: 在 Power Apps 中处理报表
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 06/27/2019
ms.author: mkaur
ms.custom: ''
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: c16a589ddcd1e7beb0be1ce28bc9f6df6a8c8b83
ms.sourcegitcommit: a1b54333338abbb0bc3ca0d7443a5a06b8945228
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/13/2020
ms.locfileid: "79239950"
---
# <a name="work-with-reports"></a>处理报表

借助报表，你可以了解工作近况，从而监视业务目标的完成进度。 还可以跟踪趋势，这是你领先对手的一大优势。  

要详细了解如何整理和创建报表，请参阅：[自定义和整理报表](https://docs.microsoft.com/powerapps/maker/model-driven-apps/add-reporting-to-app)。
  
## <a name="run-a-report"></a>运行报表  
  
1. 从左侧导航窗格中，选择报表区域。 
2. 选择目标报表 >“运行报表”  。  
  
   > [!NOTE]
   >  在“报表查看器”对话框中，可以保留原来的搜索条件，或根据需要进行更改  。  
   
   > [!div class="mx-imgBorder"]
   > ![运行报表](media/report-run.png "运行报表")
 
  
## <a name="share-a-report-with-other-users-or-teams"></a>与其他用户或团队共享报表    

1. 从左侧导航窗格中，选择报表区域。  
2. 在报表列表中，选择要共享的报表。  
3. 在命令栏上，选择“共享”  。

   > [!div class="mx-imgBorder"]
   > ![共享报表](media/report-share.png "共享报表")
  
4. 在“共享报表”对话框中，选择“添加用户/团队”   。    
5. 在“查找记录”对话框中，找到要与之共享报表的用户或团队记录，并选中记录旁边的复选框  。

   > [!div class="mx-imgBorder"]
   > ![选择用户以共享报表](media/report-share1.png "选择用户以共享报表")

6. 选择“选择”，将用户或团队记录添加到“已选记录”框中，然后选择“添加”    。

   > [!div class="mx-imgBorder"]
   > ![添加用户以共享报表](media/report-share2.png "添加用户以共享报表")
  
7. 在“共享报表”对话框中，选择所需的共享访问类型  。 可用权限包括：读取、写入、删除、追加、分配或共享。 此操作可将用户或团队记录添加到“所选记录”框  。

   > [!div class="mx-imgBorder"]
   > ![选择共享访问](media/report-share3.png "选择共享访问")
  

## <a name="share-a-report-with-your-organization-for-admins"></a>与组织共享报表（针对管理员）
 如果报表对所有用户都有用，请将其转为组织的公共报表。  

1. 从左侧导航窗格中，选择报表区域。  
2. 在报表列表中，选择要共享的报表。  
3. 在命令栏上，选择“编辑”  。  
4. 在“操作”菜单中，选择“转为组织的公共报表”   。  
  
   > [!div class="mx-imgBorder"]
   > ![与组织共享报表](media/report-share4.png "与组织共享报表")

## <a name="download-a-report"></a>下载报表

1. 从左侧导航窗格中，选择报表区域。 
2. 在报表列表中，选择要共享的报表。  
3. 在命令栏上，选择“编辑”  。  
4. 在“操作”菜单中，选择“下载报表”   。  
RDL 文件包含报表所基于的 fetchXML。
5. 下载完成后，打开报表。





### <a name="see-also"></a>另请参阅

[通过报表向导创建报表](create-report-with-wizard.md)

[添加现有报表](add-existing-report.md)

[编辑报表筛选器](edit-report-filter.md)

[排查报表中不显示数据的问题](troubleshoot-reports.md)


