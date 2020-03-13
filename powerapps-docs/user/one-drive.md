---
title: 使用 OneDrive for Business| MicrosoftDocs
ms.custom: ''
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 03/02/2020
ms.author: mduelae
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 5cfbed161ca920db3ce474371aa435189dc12543
ms.sourcegitcommit: a1b54333338abbb0bc3ca0d7443a5a06b8945228
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/13/2020
ms.locfileid: "79239996"
---
# <a name="use-onedrive-for-business"></a>使用 OneDrive for Business 

使用 OneDrive for Business 在 Common Data Service 应用中创建和管理私有文档。 更多信息：[什么是 OneDrive for Business？](https://support.office.com/article/What-is-OneDrive-for-Business-187f90af-056f-47c0-9656-cc0ddca7fdc2)


系统管理员必须先启用 OneDrive for Business，然后才能使用。 更多信息：

-   [联系你的管理员或支持人员](find-admin.md)  

-   [启用 OneDrive for Business](https://docs.microsoft.com/power-platform/admin/enable-onedrive-for-business)  


## <a name="the-first-time-you-view-your-documents"></a>首次查看文档时  

1. 打开记录，然后前往“相关文档网格”  。 例如，打开联系人记录。

2.  在打开的记录中，选择“相关”选项卡，然后选择“文档”   。

     > [!div class="mx-imgBorder"]
     > ![在记录中打开“文档”选项卡 ](media/onedrive_nav.png "在记录中打开“文档”选项卡")

3.  选择“文档位置”文档位置 > “OneDrive”   。

     > [!div class="mx-imgBorder"]
     > ![打开“文档”选项卡，然后选择 OneDrive](media/onedrive_menu.png "打开“文档”选项卡，然后选择 OneDrive")

4. 启用 OneDrive for Business 后，当你前往“文档”选项卡查看 Common Data Service 中的文档并将文件上传到 OneDrive，或尝试新建文档或文件夹时，会看到以下对话框  。  

    > [!div class="mx-imgBorder"]
    > ![更改 OneDrive 文件夹](media/setup_onedrive.png "更改 OneDrive 文件夹")  

5. 选择“更改文件夹位置”，选取要存储 OneDrive 文档的新位置，或选择“继续”接受默认文件夹位置   。

  
## <a name="view-existing-onedrive-documents"></a>查看现有 OneDrive 文档 
 
1. 打开记录，然后前往“相关文档网格”视图  。 例如，打开联系人记录。

2. 在打开的记录中，选择“相关”选项卡，然后选择“文档”   。
 
    > [!div class="mx-imgBorder"]
    > ![在记录中打开“文档”选项卡 ](media/onedrive_nav.png "在记录中打开“文档”选项卡")
 
3. 选择“文档位置”，筛选文档列表  。

    > [!div class="mx-imgBorder"]
    > ![打开“文档位置”](media/onedrive_doc_location.png "打开“文档位置”")

4.  选择下表中所述的位置。  

   |    文档位置      |  说明                                   |
   |---------------------------|------------------------------------------------|
   |      OneDrive             | OneDrive for Business 中存储的文档      |
   | 默认网站上的文档 | 默认 SharePoint 网站中存储的文档  |
   | 与我共享的内容            | 其他人分享给你且与此记录相关的文档<!--note from editor: Edit okay? I haven't seen an "app record" defined.-->    |
   |  所有位置            |     与此记录相关的所有文档位置     |

5. 选择位置后，会看到该位置保存的文档。

## <a name="create-a-new-document-and-save-it-to-onedrive"></a>新建文档并将其保存到 OneDrive

1. 打开记录，然后前往“相关文档网格”视图  。 例如，打开联系人记录。

2. 在打开的记录中，选择“相关”选项卡，然后选择“文档”   。
 
    > [!div class="mx-imgBorder"]
    > ![在记录中打开“文档”选项卡 ](media/onedrive_nav.png "在记录中打开“文档”选项卡")

2. 选择“文档位置”，然后将位置更改为 OneDrive   。

3. 选择“新建”，然后选择 PowerPoint 或 Word 等文档类型  。 

    > [!div class="mx-imgBorder"]
    > ![新建文档](media/onedrive_new_doc.png "新建文档")

4. 输入文档名称，然后选择“保存”  。  


## <a name="things-to-consider"></a>注意事项 

关于在 Common Data Service 中使用 OneDrive for Business，请注意以下事项：

- OneDrive 存储文件夹使用用户当前的 Common Data Service 语言创建。 如果语言更改，将使用新语言创建新文件夹。 旧文件夹将保留以前的语言。  

- 在 OneDrive 中共享文档与其他用户可以使用文档之间可能会有延迟。 
