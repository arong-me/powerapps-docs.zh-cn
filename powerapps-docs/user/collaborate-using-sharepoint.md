---
title: 使用 SharePoint 进行协作 | Microsoft Docs
description: 了解如何在模型驱动应用中使用 SharePoint 进行协作
documentationcenter: ''
author: Mattp123
manager: kvivek
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: model
ms.date: 11/20/2019
ms.author: matp
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 428291712f91e90cea515723a93e1871ec94de2e
ms.sourcegitcommit: 8f32eed48adf4b24b9ca607bbf6db3d19749c46f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/23/2019
ms.locfileid: "74418272"
---
# <a name="collaborate-using-sharepoint"></a>使用 SharePoint 进行协作 

管理常用文档类型（如 Word、Excel 和 PowerPoint），并创建文件夹来保存和管理那些从模型驱动应用中无缝存储在 SharePoint 中的文档。 

> [!NOTE]
> 此功能要求系统管理员启用了 SharePoint 文档管理。 更多信息：[使用 SharePoint 管理文档](/power-platform/admin/manage-documents-using-sharepoint)

对于帐户和联系人记录，首次转到“文件”选项卡时，将自动在 SharePoint 上创建一个默认文档位置文件夹。对于其他标准或自定义实体记录，请转到“相关内容” > 文档”选项卡。文档位置的名称采用以下格式：<record_name>_<record_id>。

默认情况下，该位置设置为默认站点 1 上的“文档”。

## <a name="add-a-document"></a>添加文档
1.  打开帐户或联系人记录，然后选择“文件”选项卡。对于启用了文档管理的其他标准或自定义实体，请选择“相关内容”选项卡，然后选择“文档”。
2.  从以下选项中选择。 
    - 若要创建新文档，请选择“新建”，再选择所需的文档类型（如 Word、Excel 或 OneNote），然后输入名称。 选择“保存”。 将在新选项卡中打开空白文档。 
    - 若要添加现有文档，请选择“上传”，选择“选择文件”，浏览到所需文件，然后选择“打开”。 选择“确定”。 

文档文件将显示在“文档关联的网格”视图中。 

> [!div class="mx-imgBorder"] 
> ![](media/add-doc-sharepoint.png "Add document to SharePoint")

该文档也会显示在 SharePoint 站点文件夹位置。 

> [!div class="mx-imgBorder"] 
> ![](media/doc-on-sharepoint.png "Document on SharePoint")

## <a name="manage-sharepoint-locations"></a>管理 SharePoint 位置
可从模型驱动应用中创建新的 SharePoint 位置或编辑现有的 SharePoint 位置。

1. 在命令栏上的“文件”列表中，选择“打开位置”，然后选择位置。
2. 若要编辑位置，请在命令栏上选择“编辑位置”<location name>。
显示“编辑筛选器”对话框。
3. 将自动填充显示名称、父网站和文件夹名称。 输入有关新位置的详细信息，然后选择“保存”。
4. 若要添加位置，请在命令栏上选择“添加位置”。
5. 显示“添加位置”对话框。

    > [!div class="mx-imgBorder"] 
    > ![](media/add-location-dialog-box.png "Add location dialog box")
6. 将自动填充显示名称、父网站和文件夹名称。 如果需要，请更改详细信息，然后选择“保存”。

## <a name="actions-on-documents"></a>对文档的操作
在“文档”列表中选择一个或多个文档时，可以对文档执行以下其他常见的 SharePoint 操作：
- 编辑
- 删除
- 签入
- 签出
- 放弃签出
- 编辑属性

## <a name="files-tab-faq"></a>“文件”选项卡常见问题解答
为什么移动了访问文档的位置？ 
- 我们移动了此命令，让你能够通过几次单击更轻松地找到文档。

“文档”选项卡是否不存在了？
- 是的，它不再存在。 用户仍可以单击“相关内容”菜单，然后单击“文档”链接，用以前的方式访问与记录相关联的文档。

更改后，是否仍会自动创建 SharePoint 中的子文件夹？
- 是。 此行为类似于“相关内容”菜单下的“文档”链接行为。 用户首次选择“文件”选项卡时，系统会创建相应的 SharePoint 子文件夹。 

是否有办法向其他实体添加“文件”选项卡或删除它？
- 是。 若要添加或删除“文件”选项卡，请按照本文中的步骤进行操作。 [将 SharePoint 文档选项卡添加到实体的主窗体](../maker/model-driven-apps/add-documents-tab-entity-main-form.md)  

我可以将有关此更改的反馈发送到哪里？
- 可以通过此电子邮件地址：d365_ot_crew@microsoft.com 将反馈发送到 Dynamics 365 销售办公室和 Teams 集成团队

### <a name="see-also"></a>另请参阅
[借助 Common Data Service 集成 SharePoint、OneNote 和 OneDrive](../maker/common-data-service/sharepoint-onedrive-onenote-intro.md)