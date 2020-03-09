---
title: 使用 SharePoint 进行协作 | Microsoft Docs
description: 了解如何在模型驱动应用中使用 SharePoint 进行协作
documentationcenter: ''
author: mduelae
manager: kvivek
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: model
ms.date: 03/02/2020
ms.author: matp
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 3491468724662edcac932cf37345730defd6a006
ms.sourcegitcommit: 5b6e6b41a3fc4d7f1aea46ec66c086b784efacac
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/03/2020
ms.locfileid: "78236051"
---
# <a name="collaborate-using-sharepoint"></a>使用 SharePoint 进行协作 

通过 Common Data Service，你可以将文档存储在 SharePoint 上，并在应用中进行管理。 你在应用中创建的文档存储在 SharePoint 上，并自动同步到桌面和移动设备。

系统管理员必须先启用 SharePoint，然后才能使用它来存储文档。 更多信息：

-   [联系你的管理员或支持人员](find-admin.md)  

-   [使用 SharePoint 管理文档](https://docs.microsoft.com/power-platform/admin/manage-documents-using-sharepoint)  

## <a name="where-do-you-access-the-documents-from"></a>从何处访问文档？

1. 对于支持文档管理的记录类型，请打开记录，选择“相关”选项卡，然后选择“文档”   。

   > [!div class="mx-imgBorder"]
   > ![在记录中打开“文档”选项卡 ](media/onedrive_nav.png "在记录中打开“文档”选项卡")

2. 选择“文档位置” > “默认网站 1 上的文档”   。 启用 SharePoint 后，该位置默认设置为“默认站点 1 上的文档”  。

   > [!div class="mx-imgBorder"]
   > ![默认位置](media/sharepoint_defualtsite.png "默认位置")


## <a name="create-a-new-document-and-save-it-to-sharepoint"></a>新建文档并将其保存到 SharePoint

1. 打开记录，然后前往“相关文档网格”视图  。 例如，打开联系人记录。

2. 在打开的记录上，选择“相关”选项卡，然后选择“文档”   。
 
    > [!div class="mx-imgBorder"]
    > ![在记录中打开“文档”选项卡](media/onedrive_nav.png "在记录中打开“文档”选项卡")

2. 选择“文档位置”，然后将位置更改为“默认站点 1 上的文档”   。

3. 选择“新建”，然后选择 Word、Excel 或 PowerPoint 等文档类型  。

    > [!div class="mx-imgBorder"]
    > ![新建文档](media/onedrive_new_doc.png "新建文档")

4. 输入文档名称，然后选择“保存”  。  

## <a name="create-a-new-folder-in-the-default-sharepoint-site-location"></a>在默认 SharePoint 网站位置新建文件夹

1. 打开记录，然后前往“相关文档网格”视图  。 例如，打开联系人记录。

2. 在打开的记录上，选择“相关”选项卡，然后选择“文档”   。
 
    > [!div class="mx-imgBorder"]
    > ![在记录中打开“文档”选项卡](media/onedrive_nav.png "在记录中打开“文档”选项卡")

2. 选择“文档位置”，然后将位置更改为“默认站点 1 上的文档”   。

3. 选择“新建”，然后选择“文件夹”   。

    > [!div class="mx-imgBorder"]
    > ![新建文件夹](media/Sharepoint_new_folder.png "创建新文件夹")
    
 4. 输入文件夹名称，然后选择“保存”  。  
 
 
 ## <a name="upload-an-existing-document-to-sharepoint-from-your-app"></a>将现有文档从应用上传到 SharePoint

1. 前往要为其创建文档的记录，选择“相关”选项卡，然后选择“文档”   。
 
2. 选择“上传”  。

   > [!div class="mx-imgBorder"]
   > ![上传文档](media/upload_doc.png "上传文档")

3. 选择要上传的文件。 一次只能选择一个文件。

   文档是在当前文档位置创建的。

   > [!Note]
   > 最多可以上传 50 MB 的文件。 如果 Internet 连接速度较慢，在上传大型文件时则可能出现错误。

4. 如果 SharePoint 中存在同名文件，请选择是否要覆盖这些文件。

5. 选择“确定”。 

## <a name="manage-sharepoint-locations"></a>管理 SharePoint 位置

可从 Common Data Service 中的应用新建或编辑现有的 SharePoint 位置。

### <a name="edit-a-location"></a>编辑位置

1. 打开记录，选择“相关”选项卡，然后选择“文档”   。

2. 选择“编辑位置”，然后选择 SharePoint 网站位置  。

   显示“编辑筛选器”对话框  。

   > [!div class="mx-imgBorder"]
   > ![编辑位置](media/edit_location.png "编辑位置")

3. 将自动填充显示名称、父网站和文件夹名称。 输入有关新位置的详细信息，然后选择“保存”  。

### <a name="add-a-new-location"></a>添加新位置

1. 打开记录，选择“相关”选项卡，然后选择“文档”   。

2. 选择“添加位置”  。 

   显示“添加位置”对话框  。

   > [!div class="mx-imgBorder"]
   > ![添加位置](media/add_location.png "添加位置")

3. 将自动填充显示名称、父网站和文件夹名称。 如果需要，请更改详细信息，然后选择“保存”  。

## <a name="files-tab-faq"></a>“文件”选项卡常见问题解答

为什么移动了访问文档的位置？  
- 我们移动了此命令，让你能够通过几次单击更轻松地找到文档。

“文档”选项卡是否不存在了？ 
- 是的，它不再存在。 用户仍可以选择“相关”菜单，然后选择“文档”链接，用以前的方式访问与目标记录相关的文档   。

更改后，是否仍会自动创建 SharePoint 中的子文件夹？ 
- 是。 此行为类似于“相关内容”菜单下的“文档”链接行为   。 用户首次选择“文件”选项卡时，系统会创建相应的 SharePoint 子文件夹  。 

是否有办法向其他实体添加“文件”选项卡或删除它？ 
- 是。 要添加或删除“文件”选项卡，请按照本文中的步骤操作  ：[将 SharePoint 文档选项卡添加到实体的主窗体](../maker/model-driven-apps/add-documents-tab-entity-main-form.md)  
